---
title: "[SOLVED] mysql-server configuration problem"
date: 2008-12-02
forum: General Help
---

### Post by taecha on 2008-12-02
I have been tinkering with this problem ever since the last mysql update. MySQL was not working initially. After a reboot(?!) it was. After every update or software installation, the below error keeps popping up and MySQL is unavailable until after the next reboot :mad:

I have read numerous threads ([this]("http://ubuntuforums.org/showthread.php?t=955096&highlight=mysql+dependency+problem"), [this]("http://ubuntuforums.org/showthread.php?t=873171&highlight=mysql+dependency+problem"), and [this]("http://ubuntuforums.org/showthread.php?t=981832&highlight=mysql+dependency+problem")) and their "solutions", non of which worked for me. I get the following error over and over again:

```
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up mysql-server-5.0 (5.0.51a-3ubuntu5.4) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
Reloading AppArmor profiles  Skipping profile /etc/apparmor.d/usr.sbin.mysqld~
: Warning.
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
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I am thankful for any ideas on how to solve this nagging problem.

---

### Post by hyper_ch on 2008-12-02
you could try to remove apparmor, upgrade and then reinstall apparmor. It looks like that is the point of failure.

---

### Post by taecha on 2008-12-03
Great tip hyper_ch! Thanks very much. This one worked for me!

It seems that apparmor is causing a lot of troubles with mysql as I have seen from many other threads and experienced myself first hand.

Hopefully, these issues will be addressed by the developers.

---

### Post by hyper_ch on 2008-12-03
I removed apparmor... don't see any real benefit.

---

