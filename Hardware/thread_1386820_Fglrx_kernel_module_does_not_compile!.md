---
title: "Fglrx kernel module does not compile!"
date: 2010-01-21
forum: Hardware
---

### Post by carbolymer on 2010-01-21
Hai.
I've got toshiba satellite a300-20w notebook. Damn toshiba's support for linux does not exist. >.>
Ok. I'm trying to install fglrx (i tried with 9.12 and 9.8 ) drivers on ATI Mobility Radeon HD 3470, but kernel module fails to compile. I tried to do this manually but... there's no makefile nor ./configure, just make.sh which produces this output:
```
[root@nucleon]:/var/lib/dkms/fglrx/8.681/build# ./make.sh 
AMD kernel module generator version 2.1
doing Makefile based build for kernel 2.6.x and higher
rm -rf *.c *.h *.o *.ko *.GCC* .??* *.symvers
make -C /lib/modules/2.6.31-17-generic/build SUBDIRS=/var/lib/dkms/fglrx/8.681/build/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-17-generic'
make[1]: Makefile: No such file or directory
make[1]: *** No rule to make target `Makefile'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-17-generic'
make: *** [kmod_build] Error 2
build failed with return value 2
```

Also when i'm installing drivers from self-made .deb package or downloading from repo, i see:
```
Loading new fglrx-8.681 DKMS files...
Building initial module for 2.6.31-17-generic, architecture -a x86_64
 
Error! Bad return status for module build on kernel: 2.6.31-17-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.681/build/ for more information.
Done.
 
Error! Could not locate fglrx.ko for module fglrx in the DKMS tree.
You must run a dkms build for kernel 2.6.31-17-generic (x86_64) first.
 
Setting up fglrx-modaliases (2:8.681-0ubuntu1) ...
Setting up libamdxvba1 (2:8.681-0ubuntu1) ...
 
Setting up xorg-driver-fglrx (2:8.681-0ubuntu1) ...
```

Any ideas how can i compile and add this kernel module? ;O
Strange, on ubuntu 9.04 x86 fglrx was installing wothout any problems. After upgrade from 9.04 -> 9.10 x86 that problem also appeared. ;S

Karmic Koala amd64, kernel version: 2.6.31-17-generic.

---

### Post by carbolymer on 2010-01-23
*bump*

---

### Post by Ayuthia on 2010-01-23
Have you tried:
```
sudo dkms --build -m fglrx -v 8.681
```
Then if that works:
```
sudo dkms --install -m fglrx -v 8.681
```

Generally if there are folders in /var/lib/dkms, it means that the system can patch and compile the source using dkms.  If I remember correctly, the folder name is the module (the -m portion) and then the version number (the -v portion) is found inside the module folder.

Hope that helps.

---

### Post by kaspien on 2010-01-23
*bump -- I'm having the exact same issue. 

> (Reading database ... 160356 files and directories currently installed.)
Preparing to replace fglrx-kernel-source 2:8.593-0ubuntu1 (using fglrx-kernel-source_8.593-0ubuntu1_amd64.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement fglrx-kernel-source ...
Setting up fglrx-kernel-source (2:8.593-0ubuntu1) ...
Adding Module to DKMS build system
Doing initial module build

Error! Bad return status for module build on kernel: 2.6.31-17-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.593/build/ for more information.
Installing initial module

Error! Could not locate fglrx.ko for module fglrx in the DKMS tree.
You must run a dkms build for kernel 2.6.31-17-generic (x86_64) first.
Done.


Running Ubuntu 9.10 64bit.

---

### Post by Ayuthia on 2010-01-24
> **kaspien said:**
> *bump -- I'm having the exact same issue. 

> Error! Bad return status for module build on kernel: 2.6.31-17-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.593/build/ for more information.
Installing initial module



Running Ubuntu 9.10 64bit.

What does /var/lib/dkms/fglrx/8.593/build/make.log have in it?

---

### Post by Silent Warrior on 2010-01-24
I hate to be a stick in the mud, but do you have the 2.6.31-**17**-headers installed?

[sudo apt-get install linux-headers-2.6.31-17-generic]

---

### Post by carbolymer on 2010-01-26
I've fixed it! I don't know exactly how i did it, maybe it's because of new fglrxs in repo. I've used these comands to make drivers working:
1. Kernel headers reinstallation.
```
apt-get remove --purge linux-headers-2.6.31-17
apt-get remove --purge linux-headers-2.6.31-17-generic
apt-get install linux-headers-2.6.31-17-generic linux-headers-2.6.31-17

```
2. Old drivers removal (in my case: radeonhd)
```
apt-get remove --purge xserver-xorg-video-radeonhd
```
3. Fglrx reinstallation.
```
apt-get remove --purge xorg-driver-fglrx
apt-get install xorg-driver-fglrx
```
4. New xorg.conf generation
```
rm /etc/X11/xorg.conf
/usr/bin/aticonfig --initial -f
```

Exactly, a try to run X -configure causes segmentation fault, but that way makes them working.

---

### Post by elange2 on 2010-06-28
I had this problem too.  The above solution did not work for me.  The problem is with the loader, not fglrx.  The gold loader has a bug, so switch to the bfd loader for this driver and then switch back.  To fix in 10.04:

```

sudo rm /usr/bin/ld
sudo ln -s /usr/bin/ld.bfd /usr/bin/ld
sudo apt-get install xorg-driver-fglrx
sudo ln -s /usr/bin/ld.gold /usr/bin/ld

```

This worked for me.

---

### Post by kamshi on 2010-09-21
As far as I know, fglrx doesn't build because of a security update of the kernel (2.6.33 and higher). The function compat_alloc_user_space has been removed from asm/compat.h, but is still used by fglrx.

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/573748](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/573748)

I think they are already working on a solution. I have the same problem under lucid. Well, seems like I have to wait a little longer for hardware accelerated 3D :popcorn:

---

