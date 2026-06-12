---
title: "Cannot install Nvidia Driver on Ubuntu 18.04"
date: 2018-06-30
forum: Hardware
---

### Post by asder2 on 2018-06-30
&#8203;Hello I am trying to install the official nvidia driver for my Ubuntu 18.04.The error I get is :

```
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 libnvidia-ifr1-390 : Depends: libnvidia-gl-390 but it is not going to be installed
 libnvidia-ifr1-390:i386 : Depends: libnvidia-gl-390:i386 but it is not going to be installed
 nvidia-390 : Depends: nvidia-driver-390 but it is not going to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
```
After I run apt --fix-broken install as said , and gives me:
```
(Reading database ... 194729 files and directories currently installed.)
Preparing to unpack .../libnvidia-gl-390_390.67-0ubuntu0~gpu18.04.1_i386.deb ...
diversion of /usr/lib/i386-linux-gnu/libGL.so to /usr/lib/i386-linux-gnu/libGL.so.distrib by nvidia-340
dpkg-divert: error: mismatch on package
  when removing 'diversion of /usr/lib/i386-linux-gnu/libGL.so by libnvidia-gl-390'
  found 'diversion of /usr/lib/i386-linux-gnu/libGL.so to /usr/lib/i386-linux-gnu/libGL.so.distrib by nvidia-340'
dpkg: error processing archive /var/cache/apt/archives/libnvidia-gl-390_390.67-0ubuntu0~gpu18.04.1_i386.deb (--unpack):
 new libnvidia-gl-390:i386 package pre-installation script subprocess returned error exit status 2
Preparing to unpack .../libnvidia-gl-390_390.67-0ubuntu0~gpu18.04.1_amd64.deb ...
diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 to /usr/lib/x86_64-linux-gnu/libGL.so.1.distrib by nvidia-340
dpkg-divert: error: mismatch on package
  when removing 'diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 by libnvidia-gl-390'
  found 'diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 to /usr/lib/x86_64-linux-gnu/libGL.so.1.distrib by nvidia-340'
dpkg: error processing archive /var/cache/apt/archives/libnvidia-gl-390_390.67-0ubuntu0~gpu18.04.1_amd64.deb (--unpack):
 new libnvidia-gl-390:amd64 package pre-installation script subprocess returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/libnvidia-gl-390_390.67-0ubuntu0~gpu18.04.1_i386.deb
 /var/cache/apt/archives/libnvidia-gl-390_390.67-0ubuntu0
```

I have tried purge, clean install and none of these work.

---

### Post by Autodave on 2018-06-30
Did you do a clean install of 18.04 or did you upgrade? Is this a laptop or desktop?  Model of computer and Nvidia card? Are you installing the driver from the repositories?

---

### Post by takha on 2018-07-01
I have the similar issue. I tried to fix through package manager and have got an error:

> E: /var/cache/apt/archives/libnvidia-gl-390_390.67-0ubuntu0~gpu18.04.1_i386.deb: new libnvidia-gl-390:i386 package pre-installation script subprocess returned error exit status 2
E: /var/cache/apt/archives/libnvidia-gl-390_390.67-0ubuntu0~gpu18.04.1_amd64.deb: new libnvidia-gl-390:amd64 package pre-installation script subprocess returned error exit status 2

---

