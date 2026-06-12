---
title: "uninstalling mysql problems"
date: 2009-07-06
forum: Installation &amp; Upgrades
---

### Post by johnh10000 on 2009-07-06
What the heck am I doing wrong?

--
johnh10000@tux:~$ sudo aptitude --purge remove mysql-server-5.0 mysql-server
[sudo] password for johnh10000: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initialising package states... Done
Writing extended state information... Done
The following packages will be REMOVED:
  libmhash2{pu} libt1-5{pu} mysql-server-5.0{u} 
0 packages upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 80.1MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 165053 files and directories currently installed.)
Removing libmhash2 ...
Purging configuration files for libmhash2 ...
Removing libt1-5 ...
Purging configuration files for libt1-5 ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
(Reading database ... 165032 files and directories currently installed.)
Removing mysql-server-5.0 ...
 * Stopping MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "stop" failed.
dpkg: error processing mysql-server-5.0 (--remove):
 subprocess pre-removal script returned error exit status 1
 * Stopping MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "stop" failed.
 * Starting MySQL database server mysqld                                 [ OK ] 
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'
Errors were encountered while processing:
 mysql-server-5.0
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Writing extended state information... Done

johnh10000@tux:~$ mysql
ERROR 1045 (28000): Access denied for user 'johnh10000'@'localhost' (using password: NO)
johnh10000@tux:~$ apt-get remove mysql-server mysql-server-5.0
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
johnh10000@tux:~$ sudo apt-get remove mysql-server mysql-server-5.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mysql-server is not installed, so not removed
The following packages will be REMOVED
  mysql-server-5.0
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 79.4MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 165032 files and directories currently installed.)
Removing mysql-server-5.0 ...
 * Stopping MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "stop" failed.
dpkg: error processing mysql-server-5.0 (--remove):
 subprocess pre-removal script returned error exit status 1
 * Stopping MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "stop" failed.
 * Starting MySQL database server mysqld                                 [ OK ] 
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'
Errors were encountered while processing:
 mysql-server-5.0
E: Sub-process /usr/bin/dpkg returned an error code (1)
johnh10000@tux:~$ sudo apt-get remove mysql-server mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mysql-server is not installed, so not removed
Package mysql-server is not installed, so not removed
The following packages were automatically installed and are no longer required:
  mysql-server-5.0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
johnh10000@tux:~$ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
johnh10000@tux:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  mysql-server-5.0
The following packages will be REMOVED
  mysql-server-5.0
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 79.4MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 165032 files and directories currently installed.)
Removing mysql-server-5.0 ...
 * Stopping MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "stop" failed.
dpkg: error processing mysql-server-5.0 (--remove):
 subprocess pre-removal script returned error exit status 1
 * Stopping MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "stop" failed.
 * Starting MySQL database server mysqld                                 [ OK ] 
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'
Errors were encountered while processing:
 mysql-server-5.0
E: Sub-process /usr/bin/dpkg returned an error code (1)
johnh10000@tux:~$

---

### Post by wojox on 2009-07-06
Maybe try stopping the service before uninstalling

```
sudo /etc/init.d/mysql stop
```

---

### Post by johnh10000 on 2009-07-06
> **wojox said:**
> Maybe try stopping the service before uninstalling

```
sudo /etc/init.d/mysql stop
```

Nope won't let me:(

johnh10000@tux:~$ sudo /etc/init.d/mysql stop
[sudo] password for johnh10000: 
 * Stopping MySQL database server mysqld                                 [fail] 
johnh10000@tux:~$

---

