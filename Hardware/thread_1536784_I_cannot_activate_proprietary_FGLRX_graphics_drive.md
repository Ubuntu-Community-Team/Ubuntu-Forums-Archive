---
title: "I cannot activate proprietary FGLRX graphics driver"
date: 2010-07-22
forum: Hardware
---

### Post by MIH1406 on 2010-07-22
Hello,

After an upgrade to Kubuntu 10.10, I couldn't activate the proprietary FGLRX graphics driver. I got this message form Jockey: "SystemError: installArchives() failed". Please if you can help try with me so I can solve this problem.

Here are some information:

Konsole: sudo dpkg --configure -a
```

Setting up fglrx (2:8.723.1-0ubuntu4) ...
update-initramfs: deferring update (trigger activated)
update-initramfs: Generating /boot/initrd.img-2.6.32-23-generic
Removing old fglrx-8.723.1 DKMS files...

------------------------------
Deleting module version: 8.723.1
completely from the DKMS tree.
------------------------------
Done.
Loading new fglrx-8.723.1 DKMS files...
First Installation: checking all kernels...
Building for 2.6.32-23-generic and 2.6.35-9-generic
Building for architecture i686
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
Building initial module for 2.6.35-9-generic

Error! Bad return status for module build on kernel: 2.6.35-9-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.723.1/build/ for more information.
dpkg: error processing fglrx (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-amdcccle (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.35-9-generic
Errors were encountered while processing:
 fglrx
 fglrx-amdcccle

```

Konsole: sudo apt-get install -f
```

Reading package lists... Done
Building dependency tree        
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up fglrx (2:8.723.1-0ubuntu4) ...
update-initramfs: deferring update (trigger activated)
update-initramfs: Generating /boot/initrd.img-2.6.32-23-generic
Removing old fglrx-8.723.1 DKMS files...

------------------------------
Deleting module version: 8.723.1
completely from the DKMS tree.
------------------------------
Done.
Loading new fglrx-8.723.1 DKMS files...
First Installation: checking all kernels...
Building for 2.6.32-23-generic and 2.6.35-9-generic
Building for architecture i686
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
Building initial module for 2.6.35-9-generic

Error! Bad return status for module build on kernel: 2.6.35-9-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.723.1/build/ for more information.
dpkg: error processing fglrx (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-amdcccle (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
No apport report written because the error message indicates its a followup error from a pre
                                                                                            initrd.img-2.6.35-9-generic
Errors were encountered while processing:
 fglrx
 fglrx-amdcccle
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by chillyperson23 on 2010-08-24
Sane problem here. And even with the patches in [http://ubuntuforums.org/showthread.php?t=1476777](http://ubuntuforums.org/showthread.php?t=1476777)  it builds, but the driver doesnt work. "no drivers found" on startup.  The only ray of hope so far, is to add ```
ppa:xorg-edgers/ppa
``` to your sources list.  and try to update

---

### Post by TweFoju on 2010-12-22
Hey, sorry to bump this old post up, but i dont feel like making any new thread just for this question

so i guess that FGLRX ATi driver comes with every 10.10 installed right
what i am wondering is, if this driver is already installed on my system or not

because i haven't activate it, but it's there on the "Additional Driver" List

so by default, is it already in my system? or only when i click on "Activate" then it will install?

because i am planning to use CCC

---

