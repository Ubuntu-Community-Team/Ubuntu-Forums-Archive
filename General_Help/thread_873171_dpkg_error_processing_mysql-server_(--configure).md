---
title: "dpkg: error processing mysql-server (--configure)"
date: 2008-07-28
forum: General Help
---

### Post by clarkburbidge on 2008-07-28
I have been unable to get mysql to install on my new hardy install. I have been through the google grinder and tried a few searches here but with no luck.

These posts seem to relate but are not resolved:
[https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.0/+bug/153868](https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.0/+bug/153868)
[http://osdir.com/ml/linux.debian.devel.live/2007-12/msg00021.html](http://osdir.com/ml/linux.debian.devel.live/2007-12/msg00021.html)

These didn't work for me:
[http://ubuntuforums.org/archive/index.php/t-607482.html](http://ubuntuforums.org/archive/index.php/t-607482.html)
[http://www.techienuggets.com/Comments?tx=40708](http://www.techienuggets.com/Comments?tx=40708)


Here is my terminal output for the install attempt:
```
clark@dev3:~$ sudo aptitude install mysql-server mysql-client libmysqlclient15-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following NEW packages will be automatically installed:
  libdbd-mysql-perl libdbi-perl libhtml-template-perl libnet-daemon-perl 
  libplrpc-perl mysql-client-5.0 mysql-server-5.0 
The following NEW packages will be installed:
  libdbd-mysql-perl libdbi-perl libhtml-template-perl libnet-daemon-perl 
  libplrpc-perl mysql-client mysql-client-5.0 mysql-server mysql-server-5.0 
0 packages upgraded, 9 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/36.4MB of archives. After unpacking 108MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Preconfiguring packages ...
Selecting previously deselected package libnet-daemon-perl.
(Reading database ... 115894 files and directories currently installed.)
Unpacking libnet-daemon-perl (from .../libnet-daemon-perl_0.38-1.1_all.deb) ...
Selecting previously deselected package libplrpc-perl.
Unpacking libplrpc-perl (from .../libplrpc-perl_0.2017-1.1_all.deb) ...
Selecting previously deselected package libdbi-perl.
Unpacking libdbi-perl (from .../libdbi-perl_1.601-1_i386.deb) ...
Selecting previously deselected package libdbd-mysql-perl.
Unpacking libdbd-mysql-perl (from .../libdbd-mysql-perl_4.005-1_i386.deb) ...
Selecting previously deselected package mysql-client-5.0.
Unpacking mysql-client-5.0 (from .../mysql-client-5.0_5.0.51a-3ubuntu5.1_i386.deb) ...
Selecting previously deselected package mysql-server-5.0.
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.0.51a-3ubuntu5.1_i386.deb) ...
Selecting previously deselected package libhtml-template-perl.
Unpacking libhtml-template-perl (from .../libhtml-template-perl_2.9-1_all.deb) ...
Selecting previously deselected package mysql-client.
Unpacking mysql-client (from .../mysql-client_5.0.51a-3ubuntu5.1_all.deb) ...
Selecting previously deselected package mysql-server.
Unpacking mysql-server (from .../mysql-server_5.0.51a-3ubuntu5.1_all.deb) ...
Setting up libnet-daemon-perl (0.38-1.1) ...
Setting up libplrpc-perl (0.2017-1.1) ...
Setting up libdbi-perl (1.601-1) ...
Setting up libdbd-mysql-perl (4.005-1) ...
Setting up mysql-client-5.0 (5.0.51a-3ubuntu5.1) ...
Setting up mysql-server-5.0 (5.0.51a-3ubuntu5.1) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
Reloading AppArmor profiles : done.
 * Starting MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
Setting up libhtml-template-perl (2.9-1) ...
Setting up mysql-client (5.0.51a-3ubuntu5.1) ...
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.0
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up mysql-server-5.0 (5.0.51a-3ubuntu5.1) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
Reloading AppArmor profiles : done.
 * Starting MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.0
 mysql-server
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done  
```

---

### Post by clarkburbidge on 2008-07-28
This helped! 

[http://www.linux-archive.org/debian-user/108744-mysql-fails-install-after-aptitude-purge-mysql-server-purge-unused.html](http://www.linux-archive.org/debian-user/108744-mysql-fails-install-after-aptitude-purge-mysql-server-purge-unused.html)

I had to get rid of the mysql-common package via purge also and then I was able to install mysql-server

---

### Post by run1206 on 2008-08-07
> **clarkburbidge said:**
> This helped! 

[http://www.linux-archive.org/debian-user/108744-mysql-fails-install-after-aptitude-purge-mysql-server-purge-unused.html](http://www.linux-archive.org/debian-user/108744-mysql-fails-install-after-aptitude-purge-mysql-server-purge-unused.html)

I had to get rid of the mysql-common package via purge also and then I was able to install mysql-server

kool that it worked!  i had a similar problem a few weeks ago but i reinstalled it and it runs fine now.  make sure you mark the thread as solved btw. :D

edit: pretty sure it's already out there in the HOWTOs but just wanted to post the link for installing MySQL here as well...
[https://help.ubuntu.com/Community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")
after getting past getting MySQL installed and with the root password set, i'm currently using the help files from Ubuntu to setup a MySQL database for Amarok, hope this helps...

---

### Post by marreka on 2008-09-13
Hey,

I'm having a similar problem to the first post of this thread.
I would like to install mysql-server but I'm getting an error message similar to the one above. 

I tried googling for an answer but none of the existing solutions seemed to have worked.
(and hence purging mysql-common also didn't help).

I'm currently running Ubuntu 8.04.1 on a virtual machine. 

Here is the output from the terminal
```
root@marreka:~# uname -a
Linux servername 2.6.18-12-fza-686-bigmem #1 SMP Sun May 18 13:01:05 CEST 2008 i686 GNU/Linux

root@server:~# apt-get install mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libdbd-mysql-perl libmysqlclient15off mysql-client-5.0 mysql-common
  mysql-server-5.0
Suggested packages:
  mysql-doc-5.0 tinyca
Recommended packages:
  libterm-readkey-perl apparmor libhtml-template-perl mailx
The following NEW packages will be installed:
  libdbd-mysql-perl libmysqlclient15off mysql-client-5.0 mysql-common
  mysql-server mysql-server-5.0
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/37.3MB of archives.
After this operation, 109MB of additional disk space will be used.
Do you want to continue [Y/n]? 
Preconfiguring packages ...

Package configuration

### MySQL root password entry###

Selecting previously deselected package mysql-common.
(Reading database ... 17146 files and directories currently installed.)
Unpacking mysql-common (from .../mysql-common_5.0.51a-3ubuntu5.1_all.deb) ...
Selecting previously deselected package libmysqlclient15off.
Unpacking libmysqlclient15off (from .../libmysqlclient15off_5.0.51a-3ubuntu5.1_i386.deb) ...
Selecting previously deselected package libdbd-mysql-perl.
Unpacking libdbd-mysql-perl (from .../libdbd-mysql-perl_4.005-1_i386.deb) ...
Selecting previously deselected package mysql-client-5.0.
Unpacking mysql-client-5.0 (from .../mysql-client-5.0_5.0.51a-3ubuntu5.1_i386.deb) ...
Setting up mysql-common (5.0.51a-3ubuntu5.1) ...
Selecting previously deselected package mysql-server-5.0.
(Reading database ... 17247 files and directories currently installed.)
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.0.51a-3ubuntu5.1_i386.deb) ...
Selecting previously deselected package mysql-server.
Unpacking mysql-server (from .../mysql-server_5.0.51a-3ubuntu5.1_all.deb) ...
Setting up libmysqlclient15off (5.0.51a-3ubuntu5.1) ...

Setting up libdbd-mysql-perl (4.005-1) ...
Setting up mysql-client-5.0 (5.0.51a-3ubuntu5.1) ...
Setting up mysql-server-5.0 (5.0.51a-3ubuntu5.1) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
 * Starting MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 mysql-server-5.0
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any help would be greatly appreciated!

Thanks,
Matt

---

### Post by idr3 on 2008-11-18
> **clarkburbidge said:**
> This helped! 

[http://www.linux-archive.org/debian-user/108744-mysql-fails-install-after-aptitude-purge-mysql-server-purge-unused.html](http://www.linux-archive.org/debian-user/108744-mysql-fails-install-after-aptitude-purge-mysql-server-purge-unused.html)

I had to get rid of the mysql-common package via purge also and then I was able to install mysql-server


Worked for me - thanks!

---

### Post by Sam Rose on 2008-11-21
This is the one that worked for me:

[http://ubuntuforums.org/archive/index.php/t-607482.html](http://ubuntuforums.org/archive/index.php/t-607482.html)

---

