---
title: "Install MySQL Error Message 2002 (HY000)"
date: 2009-04-09
forum: Installation &amp; Upgrades
---

### Post by hbradshaw on 2009-04-09
Hello:

I'm trying to install MySQL with Ubuntu.  I received an error message.  Below is the steps I took and the final is the error message.

I typed the following command:
sudo apt-get install libapache2-mod-auth-mysql php5-mysql

The results was the following:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libapache2-mod-auth-mysql is already the newest version.
The following NEW packages will be installed:
  php5-mysql
0 upgraded, 1 newly installed, 0 to remove and 270 not upgraded.
Need to get 74.2kB of archives.
After this operation, 287kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main php5-mysql 5.2.6-2ubuntu4.1 [74.2kB]
Fetched 74.2kB in 1s (67.7kB/s)    
Selecting previously deselected package php5-mysql.
(Reading database ... 101585 files and directories currently installed.)
Unpacking php5-mysql (from .../php5-mysql_5.2.6-2ubuntu4.1_amd64.deb) ...
Setting up php5-mysql (5.2.6-2ubuntu4.1) ...

I typed the following statement and this is the error message I received:
 mysql -u root

Error message:
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

Can someone help?
Thanks

---

### Post by knattlhuber on 2009-04-09
This thread discusses a similar problem:
[http://ubuntuforums.org/showthread.php?t=276470]("http://ubuntuforums.org/showthread.php?t=276470")
I hope it's helpful for you.

---

