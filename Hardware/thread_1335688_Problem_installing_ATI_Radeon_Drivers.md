---
title: "Problem installing ATI Radeon Drivers"
date: 2009-11-23
forum: Hardware
---

### Post by cmmckoy on 2009-11-23
I'm trying to install drivers for my ATI card, and I'm trying to follow this website:
[http://technowizah.com/2006/10/debian-how-to-ati-drivers.html](http://technowizah.com/2006/10/debian-how-to-ati-drivers.html)

When I get to the bit about 'At this point you must build the fglrx module with module-assistant' I enter the four lines into terminal, and I get the error:

Build of the package fglrx-kernel-source failed! How do you wish to proceed?

I click 'View Log' and it displays:

Build log starting, file:                                               
/var/cache/modass/fglrx-kernel-source.buildlog.2.6.28-16-generic.12590196
73                                                                       
Date: Mon, 23 Nov 2009 18:41:13 -0500   

Can someone tell me what I'm doing wrong? I'm using Ubuntu 9.04, if that helps at all.

---

### Post by cmmckoy on 2009-11-23
I forgot, after the module-assistant closes, this the following is in the terminal:

ghost@G7:~$ sudo m-a a-i fglrx

Updated infos about 1 packages
Getting source for kernel version: 2.6.28-16-generic
Kernel headers available in /usr/src/linux-headers-2.6.28-16-generic
Creating symlink...
apt-get install build-essential 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

Done!
unpack 
The source tarball could not be found!
Package fglrx-kernel-source not installed?
Running "m-a -f get fglrx-kernel-source" may help.
"/usr/share/modass/packages/default.sh" build KVERS=2.6.28-16-generic KSRC=/usr/src/linux KDREV=2.6.28-16.55 kdist_image
find: `/usr/src/modules/fglrx*': No such file or directory
ghost@G7:~$

---

