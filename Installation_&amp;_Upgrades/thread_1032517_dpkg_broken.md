---
title: "dpkg broken"
date: 2009-01-06
forum: Installation &amp; Upgrades
---

### Post by nerdpride on 2009-01-06
I want to install gftp but DPkg is broken. Look at this:```
pete@pete-linux:~$ sudo apt-get install gftp
[sudo] password for pete: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gftp-common gftp-gtk gftp-text
The following NEW packages will be installed:
  gftp gftp-common gftp-gtk gftp-text
0 upgraded, 4 newly installed, 0 to remove and 94 not upgraded.
3 not fully installed or removed.
Need to get 0B/525kB of archives.
After this operation, 3785kB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: syntax error in triggers deferred file `/var/lib/dpkg/triggers/Unincorp' at character `U' midline
E: Sub-process /usr/bin/dpkg returned an error code (2)
pete@pete-linux:~$ 

```
Can anybody help

---

### Post by lemming465 on 2009-01-19
Does ```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade --fix-broken
```
improve things any?

---

