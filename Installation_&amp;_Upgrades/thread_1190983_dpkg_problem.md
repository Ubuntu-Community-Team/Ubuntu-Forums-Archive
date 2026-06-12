---
title: "dpkg problem"
date: 2009-06-18
forum: Installation &amp; Upgrades
---

### Post by camper365 on 2009-06-18
Whenever I try to install something using aptitude, apt-get, synaptic, etc. it tells me:
```
aaron@truman:~$ sudo aptitude install hello
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
The following packages will be REMOVED:
  python-qt4-common{u} 
The following partially installed packages will be configured:
  hello ubuntustudio-desktop 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B/6548B of archives. After unpacking 139kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 206365 files and directories currently installed.)
Preparing to replace ubuntustudio-default-settings 0.26 (using .../ubuntustudio-default-settings_0.26_all.deb) ...
Unpacking replacement ubuntustudio-default-settings ...
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
dpkg: error processing /var/cache/apt/archives/ubuntustudio-default-settings_0.26_all.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/ubuntustudio-default-settings_0.26_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of ubuntustudio-desktop:
 ubuntustudio-desktop depends on ubuntustudio-default-settings; however:
  Package ubuntustudio-default-settings is not installed.
dpkg: error processing ubuntustudio-desktop (--configure):
 dependency problems - leaving unconfigured
Setting up hello (2.2-3) ...
Errors were encountered while processing:
 ubuntustudio-desktop
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

aaron@truman:~$ 


```

I think that I tried to uninstall the ubuntustudio-default-settings package but something happened, and now apt tries to fix it, but it can't configure it.

---

### Post by jerrrys on 2009-06-18
try

SynapticPackageManager>Edit>Fix broken packages

you can also try changing download source

---

### Post by camper365 on 2009-06-18
I'm not sure the package is broken, I think it's just a bug in Karmic (I'm running Karmic).

EDIT: I am sure that it is a bug in Karmic. I have downloaded the .deb from the Ubuntu package search and it doesn't install properly.

---

