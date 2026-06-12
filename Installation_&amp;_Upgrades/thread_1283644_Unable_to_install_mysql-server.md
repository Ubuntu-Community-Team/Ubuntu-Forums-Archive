---
title: "Unable to install mysql-server"
date: 2009-10-05
forum: Installation &amp; Upgrades
---

### Post by Krishna Prasad on 2009-10-05
Hi,

Yesterday I installed 'wubi' and installed ISO image of 9.04.  I was installing mysql-server-5.0 and it got interrupted(manually).  

Then when I was trying to reinstall mysql-server-5.0, I am getting the following error.

root@ubuntu:/home/mkrishna# apt-get install mysql-server-5.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  postfix linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic libmysqlclient16 bsd-mailx mailx
Use 'apt-get autoremove' to remove them.
Suggested packages:
  tinyca
The following NEW packages will be installed:
  mysql-server-5.0
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
Need to get 0B/23.6MB of archives.
After this operation, 79.4MB of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 122985 files and directories currently installed.)
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.2_i386.deb) ...
Aborting downgrade from (at least) 5.1 to 5.0.
dpkg: error processing /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.2_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
"


If i try, apt-get remove mysql-server-5.0, I get the following message,
"root@ubuntu:/home/mkrishna# apt-get remove mysql-server-5.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mysql-server-5.0 is not installed, so not removed
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  mysql-server: Depends: mysql-server-5.0 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
"


If I do, apt-get -f install

"root@ubuntu:/home/mkrishna# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  postfix linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic libmysqlclient16 bsd-mailx mailx
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  mysql-server-5.0
Suggested packages:
  tinyca
The following NEW packages will be installed:
  mysql-server-5.0
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
Need to get 0B/23.6MB of archives.
After this operation, 79.4MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
(Reading database ... 122985 files and directories currently installed.)
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.2_i386.deb) ...
Aborting downgrade from (at least) 5.1 to 5.0.
dpkg: error processing /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.2_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
"



I did different combinations of installing mysql-server-5.1 , uninstalling them, restarting the system etc.    Now my package info looks like this,

root@ubuntu:/home/mkrishna# ls -l /var/lib/dpkg/info/mysql-server*
-rw-r--r-- 1 root root  376 2009-10-05 05:23 /var/lib/dpkg/info/mysql-server-5.1.list
-rwxr-xr-x 1 root root 2437 2009-10-06 04:10 /var/lib/dpkg/info/mysql-server-5.1.postrm
-rw-r--r-- 1 root root 2673 2009-10-05 05:45 /var/lib/dpkg/info/mysql-server-core-5.0.list
-rw-r--r-- 1 root root 3683 2009-05-14 16:11 /var/lib/dpkg/info/mysql-server-core-5.0.md5sums
-rw-r--r-- 1 root root  148 2009-10-06 03:49 /var/lib/dpkg/info/mysql-server.list
-rw-r--r-- 1 root root  152 2009-05-14 16:09 /var/lib/dpkg/info/mysql-server.md5sums
-rwxr-xr-x 1 root root 5353 2009-05-14 16:09 /var/lib/dpkg/info/mysql-server.preinst


Please advice how to fix this problem.

---

### Post by Denisiuk on 2009-10-23
> [COLOR=#ff0000][COLOR=#000000]Its a serious downgrade problem:

After running the above command:

sudo rm -rf /var/lib/mysql

sudo apt-get install mysql-server-5.0

sudo apt-get install libapache2-mod-auth-mysql

sudo apt-get install php5-mysql

sudo apt-get install phpmyadmin[/COLOR][/COLOR][http://fossarchives.blogspot.com/2009/07/to-install-lamp-in-your-jaunty-or.html](http://fossarchives.blogspot.com/2009/07/to-install-lamp-in-your-jaunty-or.html)

---

