---
title: "mysql issues"
date: 2009-06-29
forum: Installation &amp; Upgrades
---

### Post by magh-87 on 2009-06-29
Hello,

Whenever I attempt to run updates on my system, I get the following error.

```
desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up mysql-server-5.0 (5.1.30really5.0.75-0ubuntu10.2) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
 * Reloading AppArmor profiles ...                                       [ OK ] 
 * Starting MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 mysql-server-5.0
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I can't seem to find a fix to this so I was looking for either some guidance on this, or a way to remove mysql so I can try this all over again.

Thanks

---

### Post by magh-87 on 2009-06-29
Still haven't come up with any fixes to this issue

---

### Post by cariboo on 2009-06-30
Try in a terminal:

```
sudo apt-get -f install
```

the above command will install any missing dependencies.

---

