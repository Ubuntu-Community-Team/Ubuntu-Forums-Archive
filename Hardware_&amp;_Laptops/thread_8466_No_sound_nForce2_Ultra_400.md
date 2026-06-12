---
title: "No sound nForce2 Ultra 400"
date: 2004-12-17
forum: Hardware &amp; Laptops
---

### Post by Dmitry100 on 2004-12-17
Help me :
Mather Board MS K7N2 Delta2-LSR Chipset NVIDIA nForce2 Ultra 400  ,
sound Realtek AC'97 ALC650 , 
lspci :
0000:00:06.0 Multimedia audio controller: nVidia Corporation: Unknown device 008a (rev a1)

Is not instaling driver NFORCE-Linux-x86-1.0-0292-pkg1.run , log :

Using: nvidia-installer ncurses user interface
-> Found package NVIDIA network driver for Linux-x86
-> Found package NVIDIA audio driver for Linux-x86
-> Please select packages for installation:
   Selections:
   NVIDIA network driver for Linux-x86 (1.0-10)
   NVIDIA audio driver for Linux-x86 (1.0-1)
-> Starting install of NVIDIA network driver for Linux-x86
-> Checking for loaded module nvnet
-> Checking for loaded module forcedeth
-> License accepted.
-> Skipping check for conflicting rpms.
-> /proc/version is Linux version 2.6.8.1-3-386 (buildd@terranova) (gcc version
   3.3.4 (Debian 1:3.3.4-9ubuntu5)) #1 Tue Oct 12 12:41:57 BST 2004
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
-> Kernel source path: '/usr/src/linux'
-> Kernel output path: '/usr/src/linux'
-> Performing cc_version_check with CC="cc".
ERROR: 
       If you are using a Linux 2.4 kernel, please make sure
       you either have configured kernel sources matching your
       kernel or the correct set of kernel headers installed
       on your system.
       
       If you are using a Linux 2.6 kernel, please make sure
       you have configured kernel sources matching your kernel
       installed on your system. If you specified a separate
       output directory using either the "KBUILD_OUTPUT" or
       the "O" KBUILD parameter, make sure to specify this
       directory with the SYSOUT environment variable or with
       the appropriate nvidia-installer command line option.
ERROR: Installation of the network driver has failed.  Please see the file
       '/var/log/nvidia-nforce-installer.log' for details.  You may find
       suggestions on  fixing installation problems in the README available on
       the Linux driver download page at [www.nvidia.com](www.nvidia.com).
 
P.S. Bad englich  :(

---

### Post by alphster on 2004-12-26
Press ESC during Grub to see what your linux version is. Write it down.

Then, get the headers for that version.

Example:

sudo apt-get install linux-headers-2.6.8.1-4-386

Now try to try the install again.

---

### Post by NeoEcoS on 2005-03-14
[QUOTE=alphster]Press ESC during Grub to see what your linux version is. Write it down.

Then, get the headers for that version.

Example:

sudo apt-get install linux-headers-2.6.8.1-4-386

Now try to try the install again.[/QUOTE]
 Thanks Alpsther , I was having the same problem, and i 
# 
sudo apt-get install linux-headers-2.6.8.1-3-386
and after run the nvidia drivers and i'm listening so good.

thanks

---

