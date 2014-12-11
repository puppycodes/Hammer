What's Hammer?
===================================  
A web vulnerability scanner framework

Basic usage
===================================  

```
   ██░ ██  ▄▄▄       ███▄ ▄███▓ ███▄ ▄███▓▓█████  ██▀███  
  ▓██░ ██▒▒████▄    ▓██▒▀█▀ ██▒▓██▒▀█▀ ██▒▓█   ▀ ▓██ ▒ ██▒
  ▒██▀▀██░▒██  ▀█▄  ▓██    ▓██░▓██    ▓██░▒███   ▓██ ░▄█ ▒
  ░▓█ ░██ ░██▄▄▄▄██ ▒██    ▒██ ▒██    ▒██ ▒▓█  ▄ ▒██▀▀█▄  
  ░▓█▒░██▓ ▓█   ▓██▒▒██▒   ░██▒▒██▒   ░██▒░▒████▒░██▓ ▒██▒
   ▒ ░░▒░▒ ▒▒   ▓▒█░░ ▒░   ░  ░░ ▒░   ░  ░░░ ▒░ ░░ ▒▓ ░▒▓░
   ▒ ░▒░ ░  ▒   ▒▒ ░░  ░      ░░  ░      ░ ░ ░  ░  ░▒ ░ ▒░
   ░  ░░ ░  ░   ▒   ░      ░   ░      ░      ░     ░░   ░ 
   ░  ░  ░      ░  ░       ░          ░      ░  ░   ░     
	
Usage: hammer.py [Auth] [Options] [Targets]

[Auth]
	-s --server: your hammer web server host address, like www.hammer.org
	-t --token: token, find it in http://www.hammer.org/user.php
[Options]
	-u --update-plugins: update new added plugins to web
	-v --verbose: increase verbosity level
	   --threads: max number of process, default cpu number
[Targets]
	-T --target: target, can be an ip address, an url or an iprange
	-p --plugin: run a plugin type scan
	   --plugin-arg: plugin argus
	   --no-gather: do not use information gather module
	-h: help
[Examples]
	hammer.py -s www.hammer.org -t 3r75... -u plugins/Info_Collect/
	hammer.py -s www.hammer.org -t 3r75... -T 192.168.1.1/24
	hammer.py -s www.hammer.org -t 3r75... -p plugins/System/iisshort.py -T vulnweb.com
```

Install
=================================== 

```
目前建议在kali上运行：
```
```
1. 数据库导入sql文件，地址在temp/hammer.sql
2. 配置web，修改web目录下config配置文件
3. 将plugins目录下所有插件内容导入web数据库
	1)登录web，在user.php中获取token，执行更新插件:
	python hammer.py -s www.hammer.org -t yourtokenhere -u plugins/
	2) 以后若添加插件，可以-U指定单独.py插件，也可以指定目录
	python hammer.py -s www.hammer.org -t yourtokenhere -u yourpluginfilepath
4. 运行hammer.py进行扫描
	python hammer.py -s www.hammer.org -t yourtokenhere -T yourtargethere
```
 Require
----------------------------------- 
Required software:
```
python2.7
ruby
dig
whatweb
```

Required python plugins:
```
# framework basic
futures		# for Parallel Processing
argparse 	# for input handling
sqlite3		# for local database
MySQLdb
beautifulsoup4	# for crawler
ipaddress	# for handling input ip
＃ used in plugins
python-nmap	# for nmap scanning
httplib		# for http request
urllib
urllib2
requests
paramiko	# for ssh cracker
pymongo		# for mongodb
easywebdav	# for webdav
json		# others
pyquery
```