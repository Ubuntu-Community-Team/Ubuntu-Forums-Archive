---
title: "apt-get upgrade bug"
date: 2009-01-21
forum: Installation &amp; Upgrades
---

### Post by alpharesearch on 2009-01-21
markus@markus-desktop-work:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
Setting up nano (2.0.7-4) ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing nano (--configure):
 subprocess post-installation script returned error exit status 1
Setting up libmikmod2-dev (3.1.11-a-6ubuntu3) ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing libmikmod2-dev (--configure):
 subprocess post-installation script returned error exit status 1
Processing triggers for menu ...
Errors were encountered while processing:
 nano
 libmikmod2-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)


see also:
[http://ubuntuforums.org/showthread.php?t=1039631](http://ubuntuforums.org/showthread.php?t=1039631)

---

### Post by alpharesearch on 2009-01-23
see:
[https://bugs.launchpad.net/bugs/305505](https://bugs.launchpad.net/bugs/305505)

---

