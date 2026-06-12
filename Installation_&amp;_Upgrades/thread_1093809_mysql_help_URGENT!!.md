---
title: "mysql help URGENT!!"
date: 2009-03-11
forum: Installation &amp; Upgrades
---

### Post by ironic1122 on 2009-03-11
```
root@purevoltage:/# sudo apt-get install mysql-server
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  mysql-server-5.0
Suggested packages:
  mysql-doc-5.0 tinyca
Recommended packages:
  libhtml-template-perl
The following NEW packages will be installed:
  mysql-server mysql-server-5.0
0 upgraded, 2 newly installed, 0 to remove and 12 not upgraded.
Need to get 0B/27.5MB of archives.
After this operation, 86.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Can't exec "/tmp/mysql-server-5.0.config.215521": Permission denied at /usr/share/perl/5.8/IPC/Open3.pm line 168.
open2: exec of /tmp/mysql-server-5.0.config.215521 configure  failed at /usr/share/perl5/Debconf/ConfModule.pm line 59
mysql-server-5.0 failed to preconfigure, with exit status 9
Selecting previously deselected package mysql-server-5.0.
(Reading database ... 43451 files and directories currently installed.)
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.0.51a-3ubuntu5.4_i386.deb) ...
Selecting previously deselected package mysql-server.
Unpacking mysql-server (from .../mysql-server_5.0.51a-3ubuntu5.4_all.deb) ...
Setting up mysql-server-5.0 (5.0.51a-3ubuntu5.4) ...
 * Stopping MySQL database server mysqld                                                                                                                                                                [ OK ]
/var/lib/dpkg/info/mysql-server-5.0.postinst: line 143: /etc/mysql/conf.d/old_passwords.cnf: No such file or directory
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
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


this is starting to make me mad i have removed this so many times and still not working i've looked all over the net and tried all the commands about removing and auto remove now im stuch how to hell do i fix this ?

---

### Post by ironic1122 on 2009-03-12
this is starting to make me very mad it wont fix at all

this is the new update now

> root@purevoltage:/# sudo apt-get install mysql-server
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  mysql-server-5.0
Suggested packages:
  mysql-doc-5.0 tinyca
Recommended packages:
  libhtml-template-perl
The following NEW packages will be installed:
  mysql-server mysql-server-5.0
0 upgraded, 2 newly installed, 0 to remove and 12 not upgraded.
Need to get 0B/27.5MB of archives.
After this operation, 86.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Can't exec "/tmp/mysql-server-5.0.config.289051": Permission denied at /usr/share/perl/5.8/IPC/Open3.pm line 168.
open2: exec of /tmp/mysql-server-5.0.config.289051 configure  failed at /usr/share/perl5/Debconf/ConfModule.pm line 59
mysql-server-5.0 failed to preconfigure, with exit status 9
Selecting previously deselected package mysql-server-5.0.
(Reading database ... 43451 files and directories currently installed.)
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.0.51a-3ubuntu5.4_i386.deb) ...
Selecting previously deselected package mysql-server.
Unpacking mysql-server (from .../mysql-server_5.0.51a-3ubuntu5.4_all.deb) ...
Setting up mysql-server-5.0 (5.0.51a-3ubuntu5.4) ...
 * Stopping MySQL database server mysqld                                                                                                                                                                [ OK ]
/var/lib/dpkg/info/mysql-server-5.0.postinst: line 143: /etc/mysql/conf.d/old_passwords.cnf: No such file or directory
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
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by TheLions on 2009-03-12
you could try download it from here:
[http://dev.mysql.com/downloads/mysql/5.1.html](http://dev.mysql.com/downloads/mysql/5.1.html)

---

### Post by yoshic on 2009-03-12
try using first:
```

$ sudo -i

``` i'll take you to a root term, and then try to reinstall mysql from there, of course you have to ommit the "sudo" command. 

```

# apt-get install mysql

```

---

### Post by ironic1122 on 2009-03-13
still no luck :(

---

### Post by upchucky on 2009-03-13
i just did the mysql server install, it worked.
is this the first attempt at an install? if yes did you set up a password?
I saw the permission denied in the temp file it created. an apt get purge remove may be in order and a second attempt but make sure you choose and remember a password.

---

### Post by KayakJim on 2009-03-13
Try the following and you should be up and going in no time.
```

sudo apt-get purge mysql-server mysql-client libmysqlclient15-dev

```
The above will ensure that everything has been removed and there are no left over files on your system.

```

sudo apt-get update

```
This will ensure that your repositories have the latest information.

```

sudo apt-get install mysql-server mysql-client libmysqlclient15-dev

```
This will do the install and then you should be ready to go.

---

