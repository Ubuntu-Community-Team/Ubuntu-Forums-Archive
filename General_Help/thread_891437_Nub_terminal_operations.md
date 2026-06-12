---
title: "Nub terminal operations"
date: 2008-08-16
forum: General Help
---

### Post by Garratt on 2008-08-16
yea so ive been noticing for the last week or so my terminal asking me to autoremove some packages and so i finally did so, it did just remove the packages yea? and not the actual programs

```
garratt@ubuntu:~/myscripts/chapter2$ sudo apt-get autoremove
[sudo] password for garratt: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libswing-layout-java libfreemarker-java javahelp2 xserver-xorg-video-psb
  subversion libaccess-bridge-java liblucene2-java tzdata-java
  libnb-platform7-devel-java libdb4.5-java libjtidy-java libnb-platform7-java
  libxml-commons-resolver1.1-java
The following packages will be REMOVED:
  javahelp2 libaccess-bridge-java libdb4.5-java libfreemarker-java
  libjtidy-java liblucene2-java libnb-platform7-devel-java
  libnb-platform7-java libswing-layout-java libxml-commons-resolver1.1-java
  subversion tzdata-java xserver-xorg-video-psb
0 upgraded, 0 newly installed, 13 to remove and 1 not upgraded.
After this operation, 31.7MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 211392 files and directories currently installed.)
Removing libnb-platform7-java ...
Removing libnb-platform7-devel-java ...
Removing javahelp2 ...
Removing libaccess-bridge-java ...
Removing liblucene2-java ...
Removing libdb4.5-java ...
Removing libfreemarker-java ...
Removing libjtidy-java ...
Removing libswing-layout-java ...
Removing libxml-commons-resolver1.1-java ...
Removing subversion ...
Removing tzdata-java ...
Removing xserver-xorg-video-psb ...
garratt@ubuntu:~/myscripts/chapter2$ 


```

Thanks.

---

### Post by p_quarles on 2008-08-16
The packages contain the "programs," so yes, everything was removed. 

The reason for this is because these applications were installed as dependencies for a meta-package. Because you presumably removed another dependency for this meta-package at some point, these things were added to the "installed automatically, no longer needed" list. 

It's a mild nuisance for those who are new to APT, but it's easy enough to fix. Just run 
```
sudo apt-get install *package_name*
```
to reinstall whichever package(s) you need to.

---

