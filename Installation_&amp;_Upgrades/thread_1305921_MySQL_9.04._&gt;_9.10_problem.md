---
title: "MySQL 9.04. &gt; 9.10 problem"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by pnmoslo on 2009-10-30
Functioning, fully updated 9.04 server running MySQL out of the box (presumably MySQL 5.0).

Apparently painless upgrade to 9.10. Everything I've tested so far works perfectly, except for MySQL, which refuses to start. This seems to be because of a failed script during the conversion process -- see below for output from manual attempt to install MySQL 5.1. 

I've tried everything I can think of (back to 5.0 and back again, tweaking permissions on the socket directory, etc. Same result, and 5.0 doesn't work now either, so something important has been changed.

Any ideas or suggestions? Inasmuch as this was a plain vanilla setup that was working perfectly, I assume this might be a problem I'm not alone in experiencing.

------------------

$ sudo aptitude install mysql-server-5.1
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
The following NEW packages will be installed:
  libdbd-mysql-perl{a} libdbi-perl{a} libhtml-template-perl{a}
  libnet-daemon-perl{a} libplrpc-perl{a} mysql-client-5.1{a}
  mysql-server-5.1 mysql-server-core-5.1{a}
0 packages upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/20,3MB of archives. After unpacking 48,7MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Preconfiguring packages ...
Selecting previously deselected package libnet-daemon-perl.
(Reading database ... 50271 files and directories currently installed.)
Unpacking libnet-daemon-perl (from .../libnet-daemon-perl_0.43-1_all.deb) ...
Selecting previously deselected package libplrpc-perl.
Unpacking libplrpc-perl (from .../libplrpc-perl_0.2020-2_all.deb) ...
Selecting previously deselected package libdbi-perl.
Unpacking libdbi-perl (from .../libdbi-perl_1.609-1_i386.deb) ...
Selecting previously deselected package libdbd-mysql-perl.
Unpacking libdbd-mysql-perl (from .../libdbd-mysql-perl_4.011-1ubuntu1_i386.deb)                                                                              ...
Selecting previously deselected package mysql-client-5.1.
Unpacking mysql-client-5.1 (from .../mysql-client-5.1_5.1.37-1ubuntu5_i386.deb)                                                                              ...
Selecting previously deselected package mysql-server-core-5.1.
Unpacking mysql-server-core-5.1 (from .../mysql-server-core-5.1_5.1.37-1ubuntu5_                                                                             i386.deb) ...
Selecting previously deselected package mysql-server-5.1.
Unpacking mysql-server-5.1 (from .../mysql-server-5.1_5.1.37-1ubuntu5_i386.deb)                                                                              ...
 * Stopping MySQL database server mysqld                                 [ OK ]
Selecting previously deselected package libhtml-template-perl.
Unpacking libhtml-template-perl (from .../libhtml-template-perl_2.9-1_all.deb) .                                                                             ..
Processing triggers for man-db ...
Setting up libnet-daemon-perl (0.43-1) ...
Setting up libplrpc-perl (0.2020-2) ...
Setting up libdbi-perl (1.609-1) ...
Setting up libdbd-mysql-perl (4.011-1ubuntu1) ...
Setting up mysql-client-5.1 (5.1.37-1ubuntu5) ...

Setting up mysql-server-core-5.1 (5.1.37-1ubuntu5) ...
Setting up mysql-server-5.1 (5.1.37-1ubuntu5) ...
 * Stopping MySQL database server mysqld                                 [ OK ]
091030 11:37:05 [Note] Plugin 'FEDERATED' is disabled.
091030 11:37:05  InnoDB: Started; log sequence number 0 43655
091030 11:37:05 [ERROR] /usr/sbin/mysqld: unknown option '--skip-bdb'
091030 11:37:05 [ERROR] Aborting

091030 11:37:05  InnoDB: Starting shutdown...
091030 11:37:06  InnoDB: Shutdown completed; log sequence number 0 43655
091030 11:37:06 [Warning] Forcing shutdown of 1 plugins
091030 11:37:06 [Note] /usr/sbin/mysqld: Shutdown complete

Warning: found usr.sbin.mysqld in /etc/apparmor.d/force-complain, forcing compla                                                                             in mode
 * Starting MySQL database server mysqld                                 [fail]
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.1 (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up libhtml-template-perl (2.9-1) ...
Errors were encountered while processing:
 mysql-server-5.1
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up mysql-server-5.1 (5.1.37-1ubuntu5) ...
 * Stopping MySQL database server mysqld                                 [ OK ]
Warning: found usr.sbin.mysqld in /etc/apparmor.d/force-complain, forcing compla                                                                             in mode
 * Starting MySQL database server mysqld                                 [fail]
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.1 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.1
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done

>>> Syslog:

Oct 30 11:41:09 nlhserver kernel: [ 6617.956712] __ratelimit: 6 callbacks suppressed
Oct 30 11:41:09 nlhserver kernel: [ 6617.956716] type=1502 audit(1256899269.707:664): operation="open" pid=8494 parent=8493 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Oct 30 11:41:09 nlhserver kernel: [ 6617.956737] type=1502 audit(1256899269.707:665): operation="file_perm" pid=8494 parent=8493 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Oct 30 11:41:09 nlhserver kernel: [ 6617.956758] type=1502 audit(1256899269.707:666): operation="file_perm" pid=8494 parent=8493 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Oct 30 11:41:09 nlhserver kernel: [ 6617.986200] type=1502 audit(1256899269.735:667): operation="open" pid=8514 parent=8513 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Oct 30 11:41:09 nlhserver kernel: [ 6617.986222] type=1502 audit(1256899269.735:668): operation="file_perm" pid=8514 parent=8513 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Oct 30 11:41:09 nlhserver kernel: [ 6617.986243] type=1502 audit(1256899269.735:669): operation="file_perm" pid=8514 parent=8513 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Oct 30 11:41:09 nlhserver mysqld_safe: Starting mysqld daemon with databases from /var/lib/mysql
Oct 30 11:41:09 nlhserver kernel: [ 6618.090559] type=1502 audit(1256899269.839:670): operation="open" pid=8634 parent=8520 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Oct 30 11:41:09 nlhserver kernel: [ 6618.090581] type=1502 audit(1256899269.839:671): operation="file_perm" pid=8634 parent=8520 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Oct 30 11:41:09 nlhserver kernel: [ 6618.090603] type=1502 audit(1256899269.839:672): operation="file_perm" pid=8634 parent=8520 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Oct 30 11:41:09 nlhserver mysqld: 091030 11:41:09 [Note] Plugin 'FEDERATED' is disabled.
Oct 30 11:41:09 nlhserver mysqld: /usr/sbin/mysqld: Table 'mysql.plugin' doesn't exist
Oct 30 11:41:09 nlhserver mysqld: 091030 11:41:09 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it.
Oct 30 11:41:09 nlhserver mysqld: 091030 11:41:09  InnoDB: Started; log sequence number 0 43655
Oct 30 11:41:09 nlhserver mysqld: 091030 11:41:09 [ERROR] /usr/sbin/mysqld: unknown option '--skip-bdb'
Oct 30 11:41:09 nlhserver mysqld: 091030 11:41:09 [ERROR] Aborting
Oct 30 11:41:09 nlhserver mysqld:
Oct 30 11:41:09 nlhserver mysqld: 091030 11:41:09  InnoDB: Starting shutdown...
Oct 30 11:41:10 nlhserver kernel: [ 6619.002058] type=1502 audit(1256899270.751:673): operation="open" pid=8648 parent=8647 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Oct 30 11:41:11 nlhserver mysqld: 091030 11:41:11  InnoDB: Shutdown completed; log sequence number 0 43655
Oct 30 11:41:11 nlhserver mysqld: 091030 11:41:11 [Warning] Forcing shutdown of 1 plugins
Oct 30 11:41:11 nlhserver mysqld: 091030 11:41:11 [Note] /usr/sbin/mysqld: Shutdown complete
Oct 30 11:41:11 nlhserver mysqld:
Oct 30 11:41:11 nlhserver mysqld_safe: mysqld from pid file /var/run/mysqld/mysqld.pid ended
Oct 30 11:41:14 nlhserver kernel: [ 6623.064383] __ratelimit: 33 callbacks suppressed
Oct 30 11:41:14 nlhserver kernel: [ 6623.064386] type=1502 audit(1256899274.815:685): operation="open" pid=8690 parent=8689 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Oct 30 11:41:14 nlhserver kernel: [ 6623.064408] type=1502 audit(1256899274.815:686): operation="file_perm" pid=8690 parent=8689 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Oct 30 11:41:14 nlhserver kernel: [ 6623.064430] type=1502 audit(1256899274.815:687): operation="file_perm" pid=8690 parent=8689 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Oct 30 11:41:15 nlhserver kernel: [ 6624.081069] type=1502 audit(1256899275.831:688): operation="open" pid=8700 parent=8699 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Oct 30 11:41:15 nlhserver kernel: [ 6624.081092] type=1502 audit(1256899275.831:689): operation="file_perm" pid=8700 parent=8699 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Oct 30 11:41:15 nlhserver kernel: [ 6624.081114] type=1502 audit(1256899275.831:690): operation="file_perm" pid=8700 parent=8699 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Oct 30 11:41:16 nlhserver kernel: [ 6625.096187] type=1502 audit(1256899276.847:691): operation="open" pid=8710 parent=8709 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Oct 30 11:41:16 nlhserver kernel: [ 6625.096208] type=1502 audit(1256899276.847:692): operation="file_perm" pid=8710 parent=8709 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Oct 30 11:41:16 nlhserver kernel: [ 6625.096228] type=1502 audit(1256899276.847:693): operation="file_perm" pid=8710 parent=8709 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Oct 30 11:41:17 nlhserver kernel: [ 6626.110232] type=1502 audit(1256899277.859:694): operation="open" pid=8720 parent=8719 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Oct 30 11:41:19 nlhserver kernel: [ 6628.140422] __ratelimit: 15 callbacks suppressed
Oct 30 11:41:19 nlhserver kernel: [ 6628.140426] type=1502 audit(1256899279.891:700): operation="open" pid=8740 parent=8739 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Oct 30 11:41:19 nlhserver kernel: [ 6628.140444] type=1502 audit(1256899279.891:701): operation="file_perm" pid=8740 parent=8739 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Oct 30 11:41:19 nlhserver kernel: [ 6628.140464] type=1502 audit(1256899279.891:702): operation="file_perm" pid=8740 parent=8739 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Oct 30 11:41:20 nlhserver kernel: [ 6629.154392] type=1502 audit(1256899280.903:703): operation="open" pid=8750 parent=8749 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Oct 30 11:41:20 nlhserver kernel: [ 6629.154414] type=1502 audit(1256899280.903:704): operation="file_perm" pid=8750 parent=8749 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Oct 30 11:41:20 nlhserver kernel: [ 6629.154436] type=1502 audit(1256899280.903:705): operation="file_perm" pid=8750 parent=8749 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Oct 30 11:41:21 nlhserver kernel: [ 6630.169725] type=1502 audit(1256899281.919:706): operation="open" pid=8760 parent=8759 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Oct 30 11:41:21 nlhserver kernel: [ 6630.169746] type=1502 audit(1256899281.919:707): operation="file_perm" pid=8760 parent=8759 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Oct 30 11:41:21 nlhserver kernel: [ 6630.169767] type=1502 audit(1256899281.919:708): operation="file_perm" pid=8760 parent=8759 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Oct 30 11:41:22 nlhserver kernel: [ 6631.185737] type=1502 audit(1256899282.935:709): operation="open" pid=8770 parent=8769 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Oct 30 11:41:23 nlhserver /etc/init.d/mysql[8796]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Oct 30 11:41:23 nlhserver /etc/init.d/mysql[8796]: #007/usr/bin/mysqladmin: connect to server at 'localhost' failed
Oct 30 11:41:23 nlhserver /etc/init.d/mysql[8796]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Oct 30 11:41:23 nlhserver /etc/init.d/mysql[8796]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Oct 30 11:41:23 nlhserver /etc/init.d/mysql[8796]:

---

### Post by mehaga on 2009-10-30
I am trying to upgrade from CD, and I also have mysql related upgrade issue (see attachment).
Now, I don't mind restarting the upgrade if it can be done safely and if I don't have to download the packages again. I thought new packages are downloaded to /var/cache/apt, but they're not. Where are they?

EDIT: I killed mysql process and upgrade continued...

---

### Post by pnmoslo on 2009-10-30
Fixed this by moving the database files (happily only one database that really mattered, and I had a good backup), removing all traces of MySQL (including mysql-common) and installing mysql again with aptitude. Then slowly and painfully reconstructing users and moving the database back in etc. 

It seems to have worked -- but whatever happened remains unsolved: the 9.04 to 9.10 upgrade zilched a functioning plain vanilla MySQL setup.

Ah well -- back to what I should have been doing for the last 6 hours.

---

### Post by lstilo on 2009-11-01
My existing MySQL installation was also effected after I upgraded to 9.10 :(

So far I think that was the only that effected.  I did notice during the upgrade process that seemed to hang a while why trying to restart MySQL, although I did not see how it resolved itself, apparently it didn't.

When I try to log into MySQL I get the following:

ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (111)

Is there any way to fix this (without having to reinstall MySQL???

Thanks.

---

### Post by pnmoslo on 2009-11-02
My conclusion after a lot of trial and error is that either there was something in my.cnf that the new version didn't like, or that the update process did something to my.cnf and didn't complete the process.

I found that moving my.cnf to eg. my.cnf.back and restarting MySQL worked (with an error message that my.cnf was missing, but the database came up, presumably in some sort of generic configuration). I then found a minimal my.cnf on the net and tried again - it worked. Next step should have been to systematically compare the new my.cnf and my.cnf.back, but time had run out. 

I also had to do an "aptitude reinstall mysql-server" several times before the installation scripts accepted that the programme was correctly installed.

---

### Post by tsh on 2009-11-04
The error message is not reflecting the primary problem for me.

```
grep mysqld /var/log/daemon.log
Nov  4 13:42:16 desktop mysqld: 091104 13:42:16 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it.
Nov  4 13:42:16 desktop mysqld: 091104 13:42:16  InnoDB: Started; log sequence number 0 209835
Nov  4 13:42:16 desktop mysqld: 091104 13:42:16 [ERROR] /usr/sbin/mysqld: unknown option '--skip-bdb'
Nov  4 13:42:16 desktop mysqld: 091104 13:42:16 [ERROR] Aborting

```

So I remove the skip-bdb option in the config file
```
sudo sed -i 's/dkip-bdb/#skip-bdb/' /etc/mysqld/my.cnf
```

It seems there is now some corrupted files,
```
sudo apt-get install mysql-server
```
seems to allow me to get mysql up and running. Myth still won't connect at this point...
If I use a host name of 'localhost' for myth, it works, 192.168.0.1 doesn't (despite me thinking thats what I set mysql for,) and 127.0.0.1 doesn't.

---

### Post by pwaltman_1972 on 2009-11-05
I got the same behavior reported by **tsh**.  Commenting out the skip-bdb caused the same message about corrupt tables.

Following the suggestion of others, I:
[LIST]
[*]made backup copies of all my databases and renamed the /etc/mysql/my.cnf file I'd been using to /etc/mysql/my.cnf.9.04.modified
[*]removed all mysql packages, including mysql-common (as an aside, the Synaptic Package Manager kept crashing on me, but I was able to remove the server using the new Ubuntu Software center, and then 'completely removed' the mysql-common using the Synaptic Package Manager)
[*] used the package manager to re-install the mysql-server package (**and** OpenOffice as this will be removed as well when you remove the mysql-common)
[/LIST]

Luckily, once I did this, mysqld started and I did **not** have to copy back my back-up, nor re-make the users.

Finally, I also tried replacing the new /etc/mysql/my.cnf with my original (**make sure to save a backup of the default version before you do this!**), and this worked as well.  I'm not sure what is causing the corrupt tables message we got at the beginning.



> **tsh said:**
> The error message is not reflecting the primary problem for me.

```
grep mysqld /var/log/daemon.log
Nov  4 13:42:16 desktop mysqld: 091104 13:42:16 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it.
Nov  4 13:42:16 desktop mysqld: 091104 13:42:16  InnoDB: Started; log sequence number 0 209835
Nov  4 13:42:16 desktop mysqld: 091104 13:42:16 [ERROR] /usr/sbin/mysqld: unknown option '--skip-bdb'
Nov  4 13:42:16 desktop mysqld: 091104 13:42:16 [ERROR] Aborting

```

So I remove the skip-bdb option in the config file
```
sudo sed -i 's/dkip-bdb/#skip-bdb/' /etc/mysqld/my.cnf
```

It seems there is now some corrupted files,
```
sudo apt-get install mysql-server
```
seems to allow me to get mysql up and running. Myth still won't connect at this point...
If I use a host name of 'localhost' for myth, it works, 192.168.0.1 doesn't (despite me thinking thats what I set mysql for,) and 127.0.0.1 doesn't.

---

### Post by skskarda on 2009-11-08
> **pwaltman_1972 said:**
> 
[LIST]
[*]made backup copies of all my databases and renamed the /etc/mysql/my.cnf file I'd been using to /etc/mysql/my.cnf.9.04.modified
[*]removed all mysql packages, including mysql-common (as an aside, the Synaptic Package Manager kept crashing on me, but I was able to remove the server using the new Ubuntu Software center, and then 'completely removed' the mysql-common using the Synaptic Package Manager)
[*] used the package manager to re-install the mysql-server package (**and** OpenOffice as this will be removed as well when you remove the mysql-common)
[/LIST]


This worked for me also.  I backed up my.cnf file.  Deleted the existing my.cnf file.  Went into package manager and did complete removal of everything mysql.   That caused applications like Office and Mythtv to uninstall also.  In my case, I just wanted Mythtv to work. After having Mythtv uninstalled during the mysql uninstall, I went back into package installer and installed mythtv.   That installed the newer version of mysql.  Everything is happy.:p   My mythtv database was still intact as well.

---

### Post by Phobos Gekko on 2009-11-09
> **pnmoslo said:**
> My conclusion after a lot of trial and error is that either there was something in my.cnf that the new version didn't like, or that the update process did something to my.cnf and didn't complete the process.

I found that moving my.cnf to eg. my.cnf.back and restarting MySQL worked (with an error message that my.cnf was missing, but the database came up, presumably in some sort of generic configuration). I then found a minimal my.cnf on the net and tried again - it worked. Next step should have been to systematically compare the new my.cnf and my.cnf.back, but time had run out. 

I also had to do an "aptitude reinstall mysql-server" several times before the installation scripts accepted that the programme was correctly installed.

First Google post, this must be my lucky day! :D

Thanks to pnmoslo, I was able to fix the problem without having to reinstall anything at all. My solution is below:

```

cd /etc/mysql
sudo mv my.cnf my.cnf.9.04
sudo cp my.cnf.dpkg-dist my.cnf
```

After this MySQL should start alright as it did for me. I /think/ the culprit might be this:

```

# * Federated
#
# The FEDERATED storage engine is disabled since 5.0.67 by default in the .cnf files
# shipped with MySQL distributions (my-huge.cnf, my-medium.cnf, and so forth).
#
skip-federated
```

---

### Post by cabez0n on 2009-11-13
I simply started removing option from my.cnf until it came up. 
I found out that skip-bdb is not a valid option anymore, and it was there by default on previous mysqls so you might want to delete that one.

---

### Post by jdsampayo on 2010-02-10
I also have the same problem,

For me, it solved:

1.- renaming my.cnf
2.- #aptitude reinstall mysql
3.- restoring my.cnf
4.- removing 'bind-address' option of my.cnf
5.- #service mysql restart

:KS

---

### Post by vikonen on 2010-03-22
After struggling with it for a LONG time, playing with apparmor setting etc., I had to go all the way; removing mysql-server & mysql-common with purge option (+OpenOffice etc. dependencies).

Also had to rm -r /etc/mysql , /var/lib/mysql , /var/log/mysql
and after all this, reinstall all. Finally, Ubuntu managed to create a new my.cnf under /etc/mysql .
Database started up nicely, and I noticed the weirdest thing:
after seeing the error at mysql startup
*"/etc/init.d/mysql: line 123: /etc/mysql/debian-start: No such file or directory"*
I realised that the complete reinstall made the /etc/mysql/debian-start disappear, and suddenly everything works.
I suppose that file had not been properly updated in the upgrade from 9.04 -> 9.10 .
Next time: fresh install to 10.04 ... :popcorn:

---

### Post by phillw on 2010-03-22
> **vikonen said:**
> After struggling with it for a LONG time, playing with apparmor setting etc., I had to go all the way; removing mysql-server & mysql-common with purge option (+OpenOffice etc. dependencies).

Also had to rm -r /etc/mysql , /var/lib/mysql , /var/log/mysql
and after all this, reinstall all. Finally, Ubuntu managed to create a new my.cnf under /etc/mysql .
Database started up nicely, and I noticed the weirdest thing:
after seeing the error at mysql startup
*"/etc/init.d/mysql: line 123: /etc/mysql/debian-start: No such file or directory"*
I realised that the complete reinstall made the /etc/mysql/debian-start disappear, and suddenly everything works.
I suppose that file had not been properly updated in the upgrade from 9.04 -> 9.10 .
Next time: fresh install to 10.04 ... :popcorn:

Next Time, tasksel :D

[http://forum.phillw.net/viewtopic.php?f=4&t=4](http://forum.phillw.net/viewtopic.php?f=4&t=4)

Although, my LAMP from 9.04 --> 9.10 went sweet.

You know it makes sense :popcorn:

Regards,

Phill.

---

### Post by kpm on 2010-04-10
> **cabez0n said:**
> I simply started removing option from my.cnf until it came up. 
I found out that skip-bdb is not a valid option anymore, and it was there by default on previous mysqls so you might want to delete that one.

Thank you!  This did it for me!

---

### Post by Socawarrior on 2010-04-28
> **cabez0n said:**
> I simply started removing option from my.cnf until it came up. 
I found out that skip-bdb is not a valid option anymore, and it was there by default on previous mysqls so you might want to delete that one.

I followed the recommendation above, but it still didn't work for me.  I ended up with a different message along the lines of:

--------------------------------------------------------------------------
ERROR 1577 (HY000) at line 1: Cannot proceed because system tables used by Event Scheduler were found damaged at server start
--------------------------------------------------------------------------

I saved a copy of my functioning my.cnf file prior to the update, and I DIFFed it with the new one from Karmic.  My findings proved that commenting out:

--------------------------
#myusam-recover         = BACKUP
--------------------------

 was ALSO necessary.

---

### Post by MunksterMan2 on 2010-06-17
> **Socawarrior said:**
> I followed the recommendation above, but it still didn't work for me.  I ended up with a different message along the lines of:

--------------------------------------------------------------------------
ERROR 1577 (HY000) at line 1: Cannot proceed because system tables used by Event Scheduler were found damaged at server start
--------------------------------------------------------------------------

I saved a copy of my functioning my.cnf file prior to the update, and I DIFFed it with the new one from Karmic.  My findings proved that commenting out:

--------------------------
#myusam-recover         = BACKUP
--------------------------

 was ALSO necessary.

This worked for me, but I should note you have it mis-spelled.

So, for the newcomers... to fix this, comment off these 2 lines in /etc/mysql/mysql.cnf then reboot:
> skip-bdb
> myisam-recover         = BACKUP

---

### Post by Leo_Luz on 2010-07-20
I tried the recommendations about "my.cnf" and didn't work. I not tried to remove mysql-common because of all dependencies that needs to be removed too.

So, I opened the Synaptic Package Manager and saw that was installed "mysql-server-core-5.1", but not the "mysql-server-5.1".
I marked "mysql-server-5.1" for installation and that was an advice that "mysql-server-5.0" should be removed before install the 5.1

Well, I installed mysql-server-5.1, removed mysql-server-5.0 and mysql worked fine after reboot.

---

