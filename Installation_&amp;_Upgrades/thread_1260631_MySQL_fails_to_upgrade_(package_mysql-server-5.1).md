---
title: "MySQL fails to upgrade (package: mysql-server-5.1)"
date: 2009-09-07
forum: Installation &amp; Upgrades
---

### Post by MTGap on 2009-09-07
I recently had troubles with my MySQL database, but was able to resolve those. Unfortunately now I can't upgrade it, here is the result of trying to upgrade mysql-server-5.1:

> The following packages will be upgraded:                                                                                                     
  mysql-server-5.1                                                                                                                           
1 upgraded, 0 newly installed, 0 to remove and 17 not upgraded.                                                                              
Need to get 0B/7187kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 217091 files and directories currently installed.)
Preparing to replace mysql-server-5.1 5.1.37-1ubuntu2 (using .../mysql-server-5.1_5.1.37-1ubuntu3_i386.deb) ...
 * Stopping MySQL database server mysqld                                                                                                                [fail]
invoke-rc.d: initscript mysql, action "stop" failed.
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
 * Stopping MySQL database server mysqld                                                                                                                [fail]
invoke-rc.d: initscript mysql, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/mysql-server-5.1_5.1.37-1ubuntu3_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
 * Stopping MySQL database server mysqld                                                                                                                [fail]
invoke-rc.d: initscript mysql, action "stop" failed.
 * Starting MySQL database server mysqld                                                                                                                [ OK ]
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.1_5.1.37-1ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


What exactly could be causing it to fail at stopping the Database? Is it a problem in my.cnf?

---

### Post by fendora on 2009-09-25
im also having the same problem/error while reinstalling mysql-server-5.1_5.1.37-1ubuntu4_i386.deb. :(

---

### Post by weits on 2009-10-09
I had also problem with upgrading and I found the solution.

Type in the terminal:

```
sudo nano /etc/mysql/my.cnf
```Find the line, which starts:

```
skip-bdb
```and comment it out:

```
#skip-bdb
```Save the file and try to upgrade again. This solution worked for me. Hope it helps you.

---

### Post by alphakaya on 2009-11-01
This worked for me.

Thanks weits!!

---

