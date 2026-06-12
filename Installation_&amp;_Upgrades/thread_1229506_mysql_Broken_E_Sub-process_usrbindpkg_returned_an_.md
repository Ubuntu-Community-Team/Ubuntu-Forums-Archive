---
title: "mysql Broken: E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2009-08-02
forum: Installation &amp; Upgrades
---

### Post by rungss on 2009-08-02
Here is what I did to Screw up things

I had a running version of all Components of LAMP Server.

One fine Day I saw that I have mysql-server-5.0 and mysql-client-5.0 installed in my System and in Syneptic I saw two other Packages named  

mysql-server and 
mysql-client 

The Description said they are for te latest version of available at any point and so  I thought instead of the 5.0 version that I have I should install this version independent ones.

I did that through Syneptic.

They did not any other packages and the dependencies solved properly.

But when I was done I saw that my mysql Server was no more usable.

I then upgraded to mysql-server-5.1 and mysql-client-5.1. 

This time everything did work but i thought I must switch back to the stable version and I (as far as I can remember) tried to remove these and install mysql-server-5.0 and mysql-client-5.0

Since then I have been getting the following errors.

```

E: Sub-process /usr/bin/dpkg returned an error code (1)

```
I tried to resolve y following various Solutions for the above message..

I also tried to remove/install/reinstall a combination of these packages but nothing seems to work.

Please help...

MySQL is a must for me...

Also How hould i backup my Data just in case....

Is Copy pasting every directory under /var/lib/mysql good enough??

The Trace of the latest try follows:

```

bijay@bijay:$ mysql -uXXXXXX -pXXXXXX
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

bijay@bijay:$ archive/index.php/t-1102402.html                                                          
bijay@bijay:$ ls /var/run/mysqld/mysqld.sock                                                            
ls: cannot access /var/run/mysqld/mysqld.sock: No such file or directory                                

bijay@bijay:$ ls /var/run/mysqld/mysqld.sock                                                            


bijay@bijay:$ sudo apt-get -f dist-upgrade
Reading package lists... Done             
Building dependency tree                  
Reading state information... Done         
Calculating upgrade... Done               
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up libdbd-mysql-perl (4.008-1) ...
Setting up libhtml-template-perl (2.9-1) ...
Setting up mysql-client-5.0 (5.1.30really5.0.75-0ubuntu10.2) ...
Setting up mysql-server-core-5.0 (5.1.30really5.0.75-0ubuntu10.2) ...


bijay@bijay:$ bjmysql
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

bijay@bijay:$ sudo apt-get -f dist-upgrade
[sudo] password for bijay:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


bijay@bijay:$ sudo apt-get -f install mysql-server-5.0
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  tinyca
The following NEW packages will be installed:
  mysql-server-5.0
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/23.6MB of archives.
After this operation, 79.4MB of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 214722 files and directories currently installed.)
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.2_i386.deb) ...
Aborting downgrade from (at least) 5.1 to 5.0.
dpkg: error processing /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.2_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
bijay@bijay:$


```

---

### Post by rungss on 2009-08-22
Someone Please help on this...

I still haven't managed to fix this...

Error when I try to install from Command line...

```

bijay@bijay:$ sudo apt-get install mysql-server
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  libhtml-template-perl mysql-server-5.0
Suggested packages:
  libipc-sharedcache-perl tinyca
The following NEW packages will be installed:
  libhtml-template-perl mysql-server mysql-server-5.0
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 123kB/23.7MB of archives.
After this operation, 79.7MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://in.archive.ubuntu.com jaunty/main libhtml-template-perl 2.9-1 [65.8kB]
Get:2 http://in.archive.ubuntu.com jaunty-updates/main mysql-server 5.1.30really5.0.75-0ubuntu10.2 [57.2kB]
Fetched 123kB in 2s (44.3kB/s)
Preconfiguring packages ...
(Reading database ... 246863 files and directories currently installed.)
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.2_i386.deb) ...
Aborting downgrade from (at least) 5.1 to 5.0.
dpkg: error processing /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.2_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Selecting previously deselected package libhtml-template-perl.
Unpacking libhtml-template-perl (from .../libhtml-template-perl_2.9-1_all.deb) ...
Selecting previously deselected package mysql-server.
Unpacking mysql-server (from .../mysql-server_5.1.30really5.0.75-0ubuntu10.2_all.deb) ...
 * Stopping MySQL database server mysqld                                                                                                                         [ OK ]
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Related Pages/information 

[http://www.mail-archive.com/ubuntu-server-bugs@lists.ubuntu.com/msg13209.html](http://www.mail-archive.com/ubuntu-server-bugs@lists.ubuntu.com/msg13209.html)
[http://www.linuxquestions.org/questions/linux-software-2/mysql-installation-problem-741902/](http://www.linuxquestions.org/questions/linux-software-2/mysql-installation-problem-741902/)

But none of them solved the Problem for me...

More error messages...

```

                                       
bijay@bijay:$ sudo apt-get install mysql-server-5.1
Reading package lists... Done                      
Building dependency tree                           
Reading state information... Done                  
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:             
  mysql-server: Depends: mysql-server-5.0 but it is not going to be installed
  mysql-server-5.1: Depends: mysql-client-5.1 (>= 5.1.31-1ubuntu2) but it is not going to be installed
                    Depends: libmysqlclient16 (>= 5.1.21-1) but it is not going to be installed       
                    Conflicts: mysql-server (< 5.1.31-1ubuntu2)                                       
                    Conflicts: mysql-server-core-5.0 but 5.1.30really5.0.75-0ubuntu10.2 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).                 
bijay@bijay:$ sudo apt-get -f install 
Reading package lists... Done         
Building dependency tree              
Reading state information... Done     
Correcting dependencies... Done       
The following extra packages will be installed:
  mysql-server-5.0                             
Suggested packages:                            
  tinyca                                       
The following NEW packages will be installed:  
  mysql-server-5.0                             
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.                             
Need to get 0B/23.6MB of archives.                            
After this operation, 79.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y                                   
Preconfiguring packages ...                                        
(Reading database ... 246874 files and directories currently installed.)
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.2_i386.deb) ...
Aborting downgrade from (at least) 5.1 to 5.0.
dpkg: error processing /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.2_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
bijay@bijay:$ man dpkg
bijay@bijay:$ sudo dpkg -i --simulate /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.2_i386.deb
(Reading database ... 246874 files and directories currently installed.)
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.2_i386.deb) ...
bijay@bijay:$ sudo dpkg -i /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.2_i386.deb
(Reading database ... 246874 files and directories currently installed.)
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.2_i386.deb) ...
Aborting downgrade from (at least) 5.1 to 5.0.
dpkg: error processing /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.2_i386.deb (--install):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.2_i386.deb
bijay@bijay:$ sudo dpkg -i --ignore-depends  /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.2_i386.deb
dpkg: --ignore-depends requires a legal package name. `/var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.2_i386.deb' is not; must start with an alphanumeric: No such file or directory
bijay@bijay:$ sudo dpkg -i --force-all  /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.2_i386.deb
(Reading database ... 246874 files and directories currently installed.)
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.2_i386.deb) ...
Aborting downgrade from (at least) 5.1 to 5.0.
dpkg: error processing /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.2_i386.deb (--install):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.2_i386.deb
bijay@bijay:$ sudo dpkg -i --force-downgrade  /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.2_i386.deb
(Reading database ... 246874 files and directories currently installed.)
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.2_i386.deb) ...
Aborting downgrade from (at least) 5.1 to 5.0.
dpkg: error processing /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.2_i386.deb (--install):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.2_i386.deb
bijay@bijay:$


```


Please Help..

---

### Post by Jor_727 on 2009-08-23
I have the same error and can't figure out how to solve it either.. >.>

---

### Post by rungss on 2009-08-23
A lot of People seem to be having this issue...

I haven't found a solution yet..

> **Jor_727 said:**
> I have the same error and can't figure out how to solve it either.. >.>

---

### Post by Pitel on 2009-08-24
I also have the same problem...
```
$ sudo dpkg --purge mysql-server-5.1
(&#268;tu databázi ... nyní je nainstalováno 185338 soubor&#367; a adresá&#345;&#367;.)
Odinstalování balíku mysql-server-5.1 ...
 * Stopping MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "stop" failed.
dpkg: chyba p&#345;i zpracovávání mysql-server-5.1 (--purge):
 podproces pre-removal script vrátil chybový status 1
 * Stopping MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "stop" failed.
 * Starting MySQL database server mysqld                                 [ OK ] 
P&#345;i zpracování nastaly chyby:
 mysql-server-5.1
```

---

### Post by VirtualEntity on 2009-08-24
Hi, gang!  Here's a possible fix for this one--it worked for me.


Fairly dangerous procedure described below--but if you've come this far as to dig up this 
Howto, you're probably up you-know-which creek without a you-know-what....

So, here goes--this worked for me more than once.  I figure it should work for you--for any
failed install, not just mysql-server or vmware-server....


SECTION 1.  Cleaning Up with Apt-Get 
=======================
sudo apt-get clean all
sudo apt-get update (perhaps 2 times)
sudo apt-get upgrade


SECTION 2.  Cleaning out /var/lib/dpkg/info
=========================
In the case of some packages, it may be necessary delete the 
/var/lib/dpkg/info/<unwanted-package-name>.postrm and 
/var/lib/dpkg/info/<unwanted-package-name>.list files and then 
do your sudo apt-get clean all, sudo apt-get update, etc as detailed
above in Section 1.

BEFORE DOING ANY TYPE OF CLEANING ACTION, PLEASE BACK UP /var/lib/dpkg/info 
BY USING AN APPROPRIATE UTILITY, E.G. 

       rsync -av /var/lib/dpkg/info/ /var/lib/dpkg/info-original

You never know when you might delete something you shouldn't have, and it is always
good to have a backup....

There may be other files associated with /var/lib/dpkg/info<unwanted-package-name> 
in /var/lib/dpkg/info.  These should probably be removed as well.

The first time these are run (especially if you've deleted all files 
pertaining to </var/lib/dpkg/info/<unwanted-package-name.*>), you will get
a 'serious warning' when running apt-get upgrade, as illustrated below:

root@ombostrsx105:/var/lib/dpkg/info# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  mysql-server
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 726MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 
dpkg: serious warning: files list file for package `mysql-server' missing, assuming package has no files currently installed. <---
114644 files and directories currently installed.)
Removing mysql-server ...

This IS a warning, and implies that you may have to go and clean up the leftover files 
from the aborted install out of /var/lib/dpkg/info. 

SECTION 3:  When /var/lib/dpkg/info is missing....
=============================
--->   NOTE:  In certain cases, /var/lib/dpkg/info may be missing.  <---

This is easily recognized if you see lots of this kind of stuff on your screen when running 
apt-get (e.g. "apt-get update" or "apt-get check"):

dpkg: serious warning: files list file for package `libmysqlclient15off' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `mysql-query-browser' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `mysql-common' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libdbd-mysql-perl' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `mysql-admin' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `mysql-gui-tools-common' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `mysql-server-core-5.0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `mysql-server' missing, assuming package has no files currently installed.


This will clue you in to the possibility that an installation screwed up somewhere between renaming /var/lib/dpkg/info 
to /var/lib/dpkg/info-old and creating a new /var/lib/dpkg/info.  

That means that there may be a backup of /var/lib/dpkg/info, namely /var/lib/dpkg/info-old.  

Assuming that the /var/lib/dpkg/info-old directory exists:
Make a copy of this, (e.g. rsync -av /var/lib/dpkg/info-old /var/lib/dpkg/info-old-original) and then 
rename /var/lib/dpkg/info-old to /var/lib/dpkg/info. 

(Yes, I know you can rename the info-old/ directory, but I want you to copy it and to have the copy 
not be a name used by dpkg, so that it is preserved should we need it later.)

Now, proceed with the steps detailed above in Section 2, then the apt-get cleaning operation specified
in Section 1.

This _should_ get you sorted right nicely....


Once you get the apt-get package database back in order, it should be a simple matter to install packages.  For example, doing "apt-get install mysql-server-5.1" would be good, where installing "mysql-server" or "mysql-server-5.0" seems to be what has led a number of people to this mess in the first place.  

Might be a good idea to practice gentle package management--use the command-line and the -s(imulate) switch before doing the actual install--just to make sure you aren't heading full throttle for a briar-patch!

Have fun!

---

### Post by rungss on 2009-08-25
I resolved this Finally..

I don't really remember what exactly worked as I did similar things quite a few times and it seems to have clicked once.

Here is what I think worked for me..

I searched for all packages that was installed from syneptic for mysql

there were a few including 
php5-mysql, mysql-client-5.0, phpmyadmin, mysql-common, mysql-server-5.0, mysql-server-core-5.0 and a few library files with the name something like libmysql*

# Barring, php5-mysql and phpmyadmin, I clicked on removed completely for each of them one at a time.
# If the Dependency check warned that this will also remove other packages outside of these mysql packages, I canceled.
After leaving off two or three among them I clicked on Apply, again making sure no other packages are removed.

Once done I selected mysql-server-5.1 for installation, it worked just fine..

I am not sure if installing mysql-server-5.0 would have worked..

Also, as pointed out by VirtualEntity below, it seems to be safer to give the version i.e, "mysql-server-5.1" instead of "mysql-server"

> **VirtualEntity said:**
> For example, doing "apt-get install mysql-server-5.1" would be good, where installing "mysql-server" or "mysql-server-5.0" seems to be what has led a number of people to this mess in the first place. 


You are right...

Thanks to VirtualEntity for taking the time to Post his Solution here.

---

### Post by whitenight639 on 2009-09-06
> **VirtualEntity said:**
> Hi, gang!  Here's a possible fix for this one--it worked for me.


Fairly dangerous procedure described below--but if you've come this far as to dig up this 
Howto, you're probably up you-know-which creek without a you-know-what....

So, here goes--this worked for me more than once.  I figure it should work for you--for any
failed install, not just mysql-server or vmware-server....


SECTION 1.  Cleaning Up with Apt-Get 
=======================
sudo apt-get clean all
sudo apt-get update (perhaps 2 times)
sudo apt-get upgrade


SECTION 2.  Cleaning out /var/lib/dpkg/info
=========================
In the case of some packages, it may be necessary delete the 
/var/lib/dpkg/info/<unwanted-package-name>.postrm and 
/var/lib/dpkg/info/<unwanted-package-name>.list files and then 
do your sudo apt-get clean all, sudo apt-get update, etc as detailed
above in Section 1.

BEFORE DOING ANY TYPE OF CLEANING ACTION, PLEASE BACK UP /var/lib/dpkg/info 
BY USING AN APPROPRIATE UTILITY, E.G. 

       rsync -av /var/lib/dpkg/info/ /var/lib/dpkg/info-original

You never know when you might delete something you shouldn't have, and it is always
good to have a backup....

There may be other files associated with /var/lib/dpkg/info<unwanted-package-name> 
in /var/lib/dpkg/info.  These should probably be removed as well.

The first time these are run (especially if you've deleted all files 
pertaining to </var/lib/dpkg/info/<unwanted-package-name.*>), you will get
a 'serious warning' when running apt-get upgrade, as illustrated below:

root@ombostrsx105:/var/lib/dpkg/info# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  mysql-server
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 726MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 
dpkg: serious warning: files list file for package `mysql-server' missing, assuming package has no files currently installed. <---
114644 files and directories currently installed.)
Removing mysql-server ...

This IS a warning, and implies that you may have to go and clean up the leftover files 
from the aborted install out of /var/lib/dpkg/info. 

SECTION 3:  When /var/lib/dpkg/info is missing....
=============================
--->   NOTE:  In certain cases, /var/lib/dpkg/info may be missing.  <---

This is easily recognized if you see lots of this kind of stuff on your screen when running 
apt-get (e.g. "apt-get update" or "apt-get check"):

dpkg: serious warning: files list file for package `libmysqlclient15off' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `mysql-query-browser' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `mysql-common' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libdbd-mysql-perl' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `mysql-admin' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `mysql-gui-tools-common' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `mysql-server-core-5.0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `mysql-server' missing, assuming package has no files currently installed.


This will clue you in to the possibility that an installation screwed up somewhere between renaming /var/lib/dpkg/info 
to /var/lib/dpkg/info-old and creating a new /var/lib/dpkg/info.  

That means that there may be a backup of /var/lib/dpkg/info, namely /var/lib/dpkg/info-old.  

Assuming that the /var/lib/dpkg/info-old directory exists:
Make a copy of this, (e.g. rsync -av /var/lib/dpkg/info-old /var/lib/dpkg/info-old-original) and then 
rename /var/lib/dpkg/info-old to /var/lib/dpkg/info. 

(Yes, I know you can rename the info-old/ directory, but I want you to copy it and to have the copy 
not be a name used by dpkg, so that it is preserved should we need it later.)

Now, proceed with the steps detailed above in Section 2, then the apt-get cleaning operation specified
in Section 1.

This _should_ get you sorted right nicely....


Once you get the apt-get package database back in order, it should be a simple matter to install packages.  For example, doing "apt-get install mysql-server-5.1" would be good, where installing "mysql-server" or "mysql-server-5.0" seems to be what has led a number of people to this mess in the first place.  

Might be a good idea to practice gentle package management--use the command-line and the -s(imulate) switch before doing the actual install--just to make sure you aren't heading full throttle for a briar-patch!

Have fun!

THANK YOU! :D sorted out my issues

---

