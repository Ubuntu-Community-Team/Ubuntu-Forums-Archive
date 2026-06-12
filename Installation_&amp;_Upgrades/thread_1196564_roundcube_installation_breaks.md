---
title: "roundcube installation breaks"
date: 2009-06-25
forum: Installation &amp; Upgrades
---

### Post by tomjoad on 2009-06-25
I'm trying to install roundcube on 8.04 LTS but get lots of errors during apt-get install...

There may be an issue with perl but I'm not able to track it down, not very well aquainted with the dpkg-tool so thankful for any help here.


ATB
//

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dbconfig-common php-auth php-db php-mail-mime php-net-smtp php-net-socket
  roundcube-core roundcube-mysql tinymce
The following NEW packages will be installed:
  dbconfig-common php-auth php-db php-mail-mime php-net-smtp php-net-socket
  roundcube roundcube-core roundcube-mysql tinymce
0 upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Need to get 494kB/1646kB of archives.
After this operation, 9867kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe roundcube-mysql 0.1~rc2-6ubuntu0.1 [5532B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe roundcube-core 0.1~rc2-6ubuntu0.1 [486kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe roundcube 0.1~rc2-6ubuntu0.1 [2290B]
Fetched 494kB in 0s (1567kB/s)  
Preconfiguring packages ...
Can't exec "/tmp/dbconfig-common.config.201411": Permission denied at /usr/share/perl/5.8/IPC/Open3.pm line 168.
open2: exec of /tmp/dbconfig-common.config.201411 configure  failed at /usr/share/perl5/Debconf/ConfModule.pm line 59
dbconfig-common failed to preconfigure, with exit status 9
Can't exec "/tmp/roundcube-core.config.201413": Permission denied at /usr/share/perl/5.8/IPC/Open3.pm line 168.
open2: exec of /tmp/roundcube-core.config.201413 configure  failed at /usr/share/perl5/Debconf/ConfModule.pm line 59
roundcube-core failed to preconfigure, with exit status 9
Selecting previously deselected package dbconfig-common.
(Reading database ... 39829 files and directories currently installed.)
Unpacking dbconfig-common (from .../dbconfig-common_1.8.38ubuntu1_all.deb) ...
Selecting previously deselected package php-auth.
Unpacking php-auth (from .../php-auth_1.5.4-1_all.deb) ...
Selecting previously deselected package php-db.
Unpacking php-db (from .../php-db_1.7.13-2_all.deb) ...
Selecting previously deselected package php-net-socket.
Unpacking php-net-socket (from .../php-net-socket_1.0.6-2_all.deb) ...
Selecting previously deselected package php-net-smtp.
Unpacking php-net-smtp (from .../php-net-smtp_1.2.6-2ubuntu1_all.deb) ...
Selecting previously deselected package tinymce.
Unpacking tinymce (from .../tinymce_2.1.1.1-1_all.deb) ...
Selecting previously deselected package php-mail-mime.
Unpacking php-mail-mime (from .../php-mail-mime_1.3.1-1.1_all.deb) ...
Selecting previously deselected package roundcube-mysql.
Unpacking roundcube-mysql (from .../roundcube-mysql_0.1~rc2-6ubuntu0.1_all.deb) ...
Selecting previously deselected package roundcube-core.
Unpacking roundcube-core (from .../roundcube-core_0.1~rc2-6ubuntu0.1_all.deb) ...
Selecting previously deselected package roundcube.
Unpacking roundcube (from .../roundcube_0.1~rc2-6ubuntu0.1_all.deb) ...
Setting up dbconfig-common (1.8.38ubuntu1) ...

Setting up php-auth (1.5.4-1) ...
Setting up php-db (1.7.13-2) ...
Setting up php-net-socket (1.0.6-2) ...
Setting up php-net-smtp (1.2.6-2ubuntu1) ...
Setting up tinymce (2.1.1.1-1) ...
Setting up php-mail-mime (1.3.1-1.1) ...
Setting up roundcube-mysql (0.1~rc2-6ubuntu0.1) ...
Setting up roundcube-core (0.1~rc2-6ubuntu0.1) ...
dbconfig-common: writing config to /etc/dbconfig-common/roundcube.conf
Not replacing deleted config file /etc/dbconfig-common/roundcube.conf
unable to read input file /etc/dbconfig-common/roundcube.conf
dpkg: error processing roundcube-core (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of roundcube:
 roundcube depends on roundcube-core; however:
  Package roundcube-core is not configured yet.
dpkg: error processing roundcube (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 roundcube-core
 roundcube
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by tomjoad on 2009-06-25
all packages removed except roundcube-core,
initial problem probably due to (manually) removed config files in the /etc/dbconfig-common/

problem with roundcube-core 
apt-get --purge -f remove roundcube-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  roundcube-core*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 2879kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 40247 files and directories currently installed.)
Removing roundcube-core ...
/var/lib/dpkg/info/roundcube-core.prerm: 10: dbc_go: not found
dpkg: error processing roundcube-core (--purge):
 subprocess pre-removal script returned error exit status 127
/var/lib/dpkg/info/roundcube-core.postinst: 18: dbc_go: not found
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 roundcube-core
E: Sub-process /usr/bin/dpkg returned an error code (1)


manully #:ed dbc_go commands in both scripts above.
purge success.. 

finally removed non-autoremoved dirs:

dpkg - warning: while removing roundcube-core, directory `/etc/roundcube' not empty so not removed.
dpkg - warning: while removing roundcube-core, directory `/usr/share/dbconfig-common' not empty so not removed.


All ends well.

---

