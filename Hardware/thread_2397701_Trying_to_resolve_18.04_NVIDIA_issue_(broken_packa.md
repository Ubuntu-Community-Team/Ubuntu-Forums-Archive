---
title: "Trying to resolve 18.04 NVIDIA issue (broken package manager)"
date: 2018-08-02
forum: Hardware
---

### Post by Daniel_Rosehill on 2018-08-02
Hi folks,

I recently did a clean install of 18.04 and used the GUI to switch from Noveau to nvidia-driver-390. After a couple of weeks, the PC began booting only one monitor (I have three), and when I checked under 'Additional Drivers' I saw that the system had automatically fallen back to Noveau. I put it back to Nvidia, but when I tried to install my next package, it said that the package management system is broken. I have since spent almost an entire day going in circles (I'll forcibly uninstall the broken packages but then be without my screens, and if I manage to reinstall it, it eventually breaks the package manager). I've tried many commands and adding 32-bit architecture -- nothing seems to lead to a permanent solution.

Here's the current runaround if I try to install, say, Wireshark.

```
**sudo apt-get install wireshark**Reading package lists... Done
Building dependency tree       
Reading state information... Done
wireshark is already the newest version (2.4.5-1).
wireshark set to manually installed.
You might want to run 'apt --fix-broken install' to correct these.
**The following packages have unmet dependencies:**
** libnvidia-ifr1-390 : Depends: libnvidia-gl-390 but it is not going to be installed**
**                      Breaks: libnvidia-ifr1-390:i386 (!= 390.48-0ubuntu3) but 390.77-0ubuntu0~gpu18.04.1 is to be installed**
 libnvidia-ifr1-390:i386 : Depends: libnvidia-gl-390:i386 but it is not going to be installed
                           Breaks: libnvidia-ifr1-390 (!= 390.77-0ubuntu0~gpu18.04.1) but 390.48-0ubuntu3 is to be installed
 nvidia-driver-390 : Depends: libnvidia-gl-390 (= 390.77-0ubuntu0~gpu18.04.1) but it is not going to be installed
                     Depends: libnvidia-ifr1-390 (= 390.77-0ubuntu0~gpu18.04.1) but 390.48-0ubuntu3 is to be installed
                     Recommends: libnvidia-gl-390:i386 (= 390.77-0ubuntu0~gpu18.04.1)
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).



```

```

**sudo apt --fix-broken install**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  lib32gcc1 libc6-i386 xserver-xorg-legacy
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libnvidia-gl-390 libnvidia-gl-390:i386 libnvidia-ifr1-390
The following NEW packages will be installed:
  libnvidia-gl-390 libnvidia-gl-390:i386
The following packages will be upgraded:
  libnvidia-ifr1-390
1 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
15 not fully installed or removed.
Need to get 0 B/29.3 MB of archives.
After this operation, 147 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
(Reading database ... 254949 files and directories currently installed.)
Preparing to unpack .../libnvidia-gl-390_390.77-0ubuntu0~gpu18.04.1_i386.deb ...
diversion of /usr/lib/i386-linux-gnu/libGL.so.1 to /usr/lib/i386-linux-gnu/libGL.so.1.distrib by nvidia-340
**dpkg-divert: error: mismatch on package**
  when removing 'diversion of /usr/lib/i386-linux-gnu/libGL.so.1 by libnvidia-gl-390'
  found 'diversion of /usr/lib/i386-linux-gnu/libGL.so.1 to /usr/lib/i386-linux-gnu/libGL.so.1.distrib by nvidia-340'
dpkg: error processing archive /var/cache/apt/archives/libnvidia-gl-390_390.77-0ubuntu0~gpu18.04.1_i386.deb (--unpack):
 new libnvidia-gl-390:i386 package pre-installation script subprocess returned error exit status 2
Preparing to unpack .../libnvidia-ifr1-390_390.77-0ubuntu0~gpu18.04.1_amd64.deb ...
Unpacking libnvidia-ifr1-390:amd64 (390.77-0ubuntu0~gpu18.04.1) over (390.48-0ubuntu3) ...
dpkg: error processing archive /var/cache/apt/archives/libnvidia-ifr1-390_390.77-0ubuntu0~gpu18.04.1_amd64.deb (--unpack):
 trying to overwrite shared '/usr/share/doc/libnvidia-ifr1-390/changelog.Debian.gz', which is different from other instances of package libnvidia-ifr1-390:amd64
Preparing to unpack .../libnvidia-gl-390_390.77-0ubuntu0~gpu18.04.1_amd64.deb ...
diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 to /usr/lib/x86_64-linux-gnu/libGL.so.1.distrib by nvidia-340
dpkg-divert: error: mismatch on package
  when removing 'diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 by libnvidia-gl-390'
  found 'diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 to /usr/lib/x86_64-linux-gnu/libGL.so.1.distrib by nvidia-340'
dpkg: error processing archive /var/cache/apt/archives/libnvidia-gl-390_390.77-0ubuntu0~gpu18.04.1_amd64.deb (--unpack):
 new libnvidia-gl-390:amd64 package pre-installation script subprocess returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/libnvidia-gl-390_390.77-0ubuntu0~gpu18.04.1_i386.deb
 /var/cache/apt/archives/libnvidia-ifr1-390_390.77-0ubuntu0~gpu18.04.1_amd64.deb
 /var/cache/apt/archives/libnvidia-gl-390_390.77-0ubuntu0~gpu18.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Synaptic will flag the broken packages, but if I manage to remove them, I simply fall back to Noveau on my next restart. I tried to upgrade one and got this output

```

E: /var/cache/apt/archives/libnvidia-gl-390_390.77-0ubuntu0~gpu18.04.1_amd64.deb: new libnvidia-gl-390:amd64 package pre-installation script subprocess returned error exit status 2

```

[IMG]https://ibb.co/gKmJyz[/IMG]
[IMG]https://image.ibb.co/dy9Gke/Selection_012.png[/IMG]
Any ideas? I'm trying really hard to not install a previous distro from scratch as I feel as I've done that too many times: but cannot live without either a proper display driver or package manager!

Any help appreciated!

---

### Post by Autodave on 2018-08-02
Did you originally install the driver from the repositories or from the Nvidia site?

---

### Post by Daniel_Rosehill on 2018-08-02
Over CLI. I added the Nvidia repo but used the one that Ubuntu finds (nvidia-driver-390 rather than nvidia-driver-396).

I finally manged to remove the broken packages through Synaptic and Software & Updates now shows that I'm "using a manually installed driver"

---

### Post by jakobadamgrabowski on 2018-09-02
Answer.
1. you have old dependencies you want to remove
2. you want to clean mess
3. you want to install new driver

I assume you have cr*p from 340 driver installed - which was my problem

1. remove old dependencies
```
for FILE in $(dpkg-divert --list | grep nvidia-340 | awk '{print $3}'); do sudo dpkg-divert --remove $FILE; done
```

2. clean mess - depended on mess you have installed find it out if not work out of the box ;)```
sudo dpkg --force-all -P nvidia-390 nvidia-compute-utils-390 nvidia-dkms-390 nvidia-prime nvidia-settings nvidia-opencl-icd-340 nvidia-opencl-icd-384 nvidia-kernel-source-390 nvidia-kernel-common-390

```

```
sudo dpkg --force-all -P libnvidia-cfg1-390 libnvidia-common-390 libnvidia-compute-390 libnvidia-decode-390 libnvidia-encode-390  libnvidia-fbc1-390 libnvidia-ifr1-390

```

```
sudo apt purge *nvidia*
```
```
sudo apt autoremove
```

```
sudo apt-get upgrade update
```

3. install new recommended drivers

```
ubuntu-drivers devices
```

```
nvidia-settings
``` - advice do not play with settings in this cr*ppy drivers just for checking if installed :)

---

### Post by marco68 on 2018-12-10
Thank you!!!

---

### Post by william-s2 on 2019-03-07
Thank you. Worked.

---

### Post by arek.kucmann on 2019-03-20
Hello Jakob,
I have the same problem like Daniell with my nvidia drivers. My code is below. Can you write instruction for me like for Daniel to solve this problem? I try so many things, that I'm scary to do next... :/

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  lib32gcc1 libc6-i386 libnvidia-common-390 libnvidia-common-415
  libwayland-client0:i386 libwayland-server0:i386 libwxbase3.0-0v5
  libwxgtk3.0-0v5
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libnvidia-gl-418 libnvidia-gl-418:i386
The following NEW packages will be installed:
  libnvidia-gl-418 libnvidia-gl-418:i386
0 upgraded, 2 newly installed, 0 to remove and 16 not upgraded.
3 not fully installed or removed.
Need to get 0 B/49,1 MB of archives.
After this operation, 236 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 175896 files and directories currently installed.)
Preparing to unpack .../libnvidia-gl-418_418.43-0ubuntu0~gpu18.04.1_i386.deb ...
diversion of /usr/lib/i386-linux-gnu/libGL.so.1 to /usr/lib/i386-linux-gnu/libGL.so.1.distrib by nvidia-340
dpkg-divert: error: mismatch on package
  when removing 'diversion of /usr/lib/i386-linux-gnu/libGL.so.1 by libnvidia-gl-418'
  found 'diversion of /usr/lib/i386-linux-gnu/libGL.so.1 to /usr/lib/i386-linux-gnu/libGL.so.1.distrib by nvidia-340'
dpkg: error processing archive /var/cache/apt/archives/libnvidia-gl-418_418.43-0ubuntu0~gpu18.04.1_i386.deb (--unpack):
 new libnvidia-gl-418:i386 package pre-installation script subprocess returned error exit status 2
Preparing to unpack .../libnvidia-gl-418_418.43-0ubuntu0~gpu18.04.1_amd64.deb ...
diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 to /usr/lib/x86_64-linux-gnu/libGL.so.1.distrib by nvidia-340
dpkg-divert: error: mismatch on package
  when removing 'diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 by libnvidia-gl-418'
  found 'diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 to /usr/lib/x86_64-linux-gnu/libGL.so.1.distrib by nvidia-340'
dpkg: error processing archive /var/cache/apt/archives/libnvidia-gl-418_418.43-0ubuntu0~gpu18.04.1_amd64.deb (--unpack):
 new libnvidia-gl-418:amd64 package pre-installation script subprocess returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/libnvidia-gl-418_418.43-0ubuntu0~gpu18.04.1_i386.deb
 /var/cache/apt/archives/libnvidia-gl-418_418.43-0ubuntu0~gpu18.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by ununseptium2 on 2019-05-28
Thanks, worked for me too!

---

