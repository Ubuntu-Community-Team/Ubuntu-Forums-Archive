---
title: "Xampp Start Problems"
date: 2009-06-26
forum: Installation &amp; Upgrades
---

### Post by waloshin on 2009-06-26
Ran in terminal:

server1@serverCluster1:~$ sudo /opt/lampp/lampp start
[sudo] password for server1: 
Starting XAMPP for Linux 1.7.1...
/opt/lampp/share/lampp/phpstatus: line 4: /opt/lampp/bin/php: No such file or directory
XAMPP: Starting Apache with SSL ...
/opt/lampp/bin/httpd: error while loading shared libraries: libaprutil-1.so.0: cannot open shared object file: No such file or directory
XAMPP: Error 127! Couldn't start Apache!
XAMPP: Starting diagnose...
tail: cannot open `/opt/lampp/logs/apachestart.log' for reading: No such file or directory
XAMPP: Sorry, I've no idea what's going wrong.
XAMPP: Please contact our forum [http://www.apachefriends.org/f/](http://www.apachefriends.org/f/)
XAMPP: Starting MySQL...
/opt/lampp/lampp: line 247: /opt/lampp/bin/mysql.server: No such file or directory
XAMPP: Couldn't start MySQL!
XAMPP: Starting ProFTPD...
XAMPP: /opt/lampp/sbin/proftpd: error while loading shared libraries: libmysqlclient.so.16: cannot open shared object file: No such file or directory
XAMPP: Error 127! Couln't start ProFTPD!
XAMPP for Linux started.
server1@serverCluster1:~$ /opt/lampp/lampp start

---

### Post by jimv on 2009-06-26
Meh, Xampp is more trouble than it's worth, IMHO.  You can install the same thing from Synaptic (LAMP) by opening Synaptic, going to the Edit menu, and clicking Mark Packages by Task.  Check LAMP Server, and click Ok, then click Apply.  This will install Apache, Mysql, and PHP.  If you want some simple management tools, install the mysql-admin package.  This will put an excellent GUI, MySQL Administrator, in Applications > Programming > MySQL Administrator.

---

