---
title: "ATI Radeon Driver Issue - Lucid"
date: 2012-01-31
forum: Hardware
---

### Post by w0rlds on 2012-01-31
Hey everyone, 

I am having a heck of a time installing a working driver for my ATI Mobility Radeon 3650 card for my Lucid O/S with a 2.6.39.4 Kernel.    

I have tried both the restricted driver through the Hardware Drivers utility AND the manual install process, outlined here:  
[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide)  

The error I get either way is:    
(Reading database ... 247803 files and directories currently installed.)
Unpacking fglrx (from .../fglrx_2%3a8.801-0ubuntu1~xup~lucid_i386.deb) ...
Selecting previously deselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from .../fglrx-amdcccle_2%3a8.801-0ubuntu1~xup~lucid_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Setting up fglrx (2:8.801-0ubuntu1~xup~lucid) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/GL.conf (gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-8.801 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.39.4
Building for architecture i686
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
update-initramfs: deferring update (trigger activated)

Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.POSIX.cache...
Setting up fglrx-amdcccle (2:8.801-0ubuntu1~xup~lucid) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.39.4
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...

2012-01-31 09:50:50,914 ERROR: update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group gl_conf) doesn't exist.

2012-01-31 09:50:51,070 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx



The part that stands out to me (I am still a bit of a newb at this) is the:  
Module build for the currently running kernel was skipped since the kernel source for this kernel does not seem to be installed.    

How do I fix this? Am I missing a kernel module?  Any help is appreciated...

---

