---
title: "Unable to Install or Remove Anything at All"
date: 2009-02-13
forum: Installation &amp; Upgrades
---

### Post by ALIENDUDE5300 on 2009-02-13
I'm not really sure what caused this to happen, but after trying to remove some packages on my system that I no longer need, which failed, I get the following message everytime I try to install or remove anything, or even use dselect or aptitude as root to update my list of available packages:
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```
That error message came from the Add/Remove GUI, but I get similar ones from just about all package management systems, such as this one from dpkg --configure -a (as root):
```
dpkg: parse error, in file `/var/lib/dpkg/updates/0032' near line 1:
 newline in field name `#padding'
```
Here are the contents of the file "/var/lib/dpkg/updates/0032":
```
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#paddi
```
To be honest, I have no idea how to fix this, and it is rather annoying to be unable to install or uninstall *anything*. I would really appreciate it if anyone could help me fix this problem. The attached file is a list of software that was being removed at the time.

---

### Post by ALIENDUDE5300 on 2009-02-13
Removing the file /var/lib/dpkg/updates/0032 then re-running dpkg --configure -a as root seems to have fixed the problem.

---

