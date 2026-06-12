---
title: "Problem when uninstalling mysql-server"
date: 2009-10-14
forum: Installation &amp; Upgrades
---

### Post by Wouter N on 2009-10-14
Hi,

I installed mysql server a while ago, through apt-get. As I wanted to give a manual install of the latest mysql server version a try, I did something stupid. I deleted the mysql folders which where installed when apt-get installed mysql-server on my system. I did so because I thought it just were the precompiled binaries I already downloaded from mysql.com once.
So, later on, i tried to remove mysql-server trough apt-get... Somehow apt-get tries to shutdown the mysql server, while it isn't even running, it searches for my.cnf in some of the folders I deleted. So I can't delete the mysql-server package anymore...
What should I do?

P.S.: Here's the complete output of apt-get when I try to remove mysq-server via 'autoremove'. There also pops up a mysql config window that is only to be seen when installing mysql, not when uninstalling. It asks to set up a root password, I press enter, and the process continues(No, it doesn't ask for my mysql root password, it really asks me to set one up!)
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  mysql-server-5.0
The following packages will be REMOVED:
  mysql-server-5.0
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 79.4MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 124973 files and directories currently installed.)
Removing mysql-server-5.0 ...
 * Stopping MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "stop" failed.
dpkg: error processing mysql-server-5.0 (--remove):
 subprocess pre-removal script returned error exit status 1
 * Stopping MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "stop" failed.
 * /etc/init.d/mysql: WARNING: /etc/mysql/my.cnf cannot be read. See README.Debian.gz
 * Starting MySQL database server mysqld                                 [ OK ] 
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'
Errors were encountered while processing:
 mysql-server-5.0
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

