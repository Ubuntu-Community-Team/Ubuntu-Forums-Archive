---
title: "DKMS won't build fglrx for the official installer... annoying"
date: 2008-07-15
forum: Hardware
---

### Post by Cerberus108 on 2008-07-15
Hi there, I'm searching for a little help for my umpteenth problem on Ubuntu... 

I was trying to install the official ati driver on my Intrepid Ibex, but both in package mode and in non-package mode it failed, with a problem relating to DKMS: 

```
lorenzo@lorenzo-desktop:~$ sudo dpkg -i fglrx-kernel-source_8.501-0ubuntu1_i386.deb 
(Lettura del database ... 127391 file e directory attualmente installati.)
Mi preparo a sostituire fglrx-kernel-source 2:8.501-0ubuntu1 (con fglrx-kernel-source_8.501-0ubuntu1_i386.deb) ...
Removing all DKMS Modules

Error! There are no instances of module: fglrx
8.501 located in the DKMS tree.
Done.
Spacchetto il sostituto di fglrx-kernel-source ...
Configuro fglrx-kernel-source (2:8.501-0ubuntu1) ...
Adding Module to DKMS build system
Doing initial module build

Error!  Build of fglrx.ko failed for: 2.6.26-3-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.501/build/ for more information.
Installing initial module

Error! Could not locate fglrx.ko for module fglrx in the DKMS tree.
You must run a dkms build for kernel 2.6.26-3-generic (i686) first.
Done.
```

This is what I get by trying to install the generated packages; by trying to install the driver directly, I get this:

```
lorenzo@lorenzo-desktop:~/Driver/ATI$ sudo ./ati-installer.sh 8.501 --install
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Detected configuration:
Architecture: i686 (32-bit)
X Server: X.Org 7.1 and later releases
DKMS part of installation failed.  Please refer to /usr/share/ati/fglrx-install.log for details
```

and this is /usr/share/ati/fglrx-install.log: 

```
/usr/share/ati/fglrx-install.log
```

A last note: searching on the net, I found out that this problem is not strictly related to the xorg version, some people had problems even in 7.3..
I'm hoping that someone (please) will help me... I'm starting to believe at this point that Windows $Vista is better in any camp...

---

### Post by markbuntu on 2008-07-15
There is a Intrepid build for the fglrx driver in Launchpad somewhere. I saw it.

Besides that, why are you using Intrepid and expecting stability?
It is still in alpha!!

---

### Post by duru on 2009-04-01
> **markbuntu said:**
> 
Besides that, why are you using Intrepid and expecting stability?
It is still in alpha!!

Had I known this, I would definitely install something like Ubuntu 1.0.

---

