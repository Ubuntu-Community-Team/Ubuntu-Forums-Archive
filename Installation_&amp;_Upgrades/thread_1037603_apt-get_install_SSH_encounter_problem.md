---
title: "apt-get install SSH encounter problem"
date: 2009-01-11
forum: Installation &amp; Upgrades
---

### Post by hmchzb19 on 2009-01-11
dpkg --configure -a  

Setting up openssh-server (1:5.1p1-3ubuntu1) ...
invoke-rc.d: initscript ssh, action "restart" failed.
dpkg: error processing openssh-server (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ssh:
 ssh depends on openssh-server; however:
  Package openssh-server is not configured yet.
dpkg: error processing ssh (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 openssh-server
 ssh


wut can I do to solve this problem ?

---

### Post by roflnoob on 2009-01-12
Try booting up with recovery mode (I do this by hitting 'esc' while ubuntu is booting and choosing "recovery mode" or something to that effect, this may be different for you) and use the "fix packages" option that pops up after a bit and following the prompts afterwards. This should help something, as it looks to newbie me that you have a problem with packages.

whatever the case may be, good luck.

---

### Post by kranny on 2009-01-12
```
sudo apt-get install --fix-missing ssh
```

---

### Post by hmchzb19 on 2009-01-12
#apt-get install --fix-missing ssh
Reading package lists... Done
Building dependency tree... Done
ssh is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 18 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up openssh-server (1:5.1p1-3ubuntu1) ...
invoke-rc.d: initscript ssh, action "restart" failed.
dpkg: error processing openssh-server (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ssh:
 ssh depends on openssh-server; however:
  Package openssh-server is not configured yet.
dpkg: error processing ssh (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
Errors were encountered while processing:
 openssh-server
 ssh
E: Sub-process /usr/bin/dpkg returned an error code (1)

It looks weird get these information

---

### Post by kranny on 2009-01-12
I wud have done a 
```
sudo apt-get --purge remove openssh-server
sudo apt-get install openssh-server 
```
If that dint solve your problem try to get rid of the /etc/sshd_config file

---

