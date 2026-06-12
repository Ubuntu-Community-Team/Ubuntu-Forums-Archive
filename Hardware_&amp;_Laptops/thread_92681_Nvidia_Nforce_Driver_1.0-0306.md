---
title: "Nvidia Nforce Driver 1.0-0306"
date: 2005-11-20
forum: Hardware &amp; Laptops
---

### Post by Tobias_at_ch on 2005-11-20
i can not install the Nvidia Nforce Driver 1.0-0306

i have done:
sudo sh NFORCE-Linux-x86-1.0-0306-pkg1.run --kernel-source-path /usr/src/linux-headers-2.6.12-9
but not sure if this is correct.

kernel-sources, kernel-headers are installed

nforce-installer log file '/var/log/nvidia-nforce-installer.log'
creation time: Sun Nov 20 12:54:37 2005
option status:
  license pre-accepted       : false
  expert                     : false
  uninstall                  : false
  driver info                : false
  no precompiled interface   : true
  no ncurses color           : false
  no questions               : false
  silent                     : false
  Installer install prefix   : /usr
  kernel source path         : /usr/src/linux-headers-2.6.12-9
  net kernel install path    : (not specified)
  audio kernel install path  : (not specified)
  proc mount point           : /proc
  ui                         : (not specified)
  tmpdir                     : /tmp
Using: nvidia-installer ncurses user interface
-> Found package NVIDIA network driver for Linux-x86
-> Found package NVIDIA audio driver for Linux-x86
-> Please select packages for installation:
   Selections:
   NVIDIA network driver for Linux-x86 (1.0-12)
   NVIDIA audio driver for Linux-x86 (1.0-6)
-> Starting install of NVIDIA network driver for Linux-x86
-> Checking for loaded module nvnet
-> Checking for loaded module forcedeth
-> License accepted.
-> Skipping check for conflicting rpms.
-> Not probing for precompiled kernel interfaces.
-> Using the kernel source path '/usr/src/linux-headers-2.6.12-9' as specified
   by the '--kernel-source-path' commandline option.
-> Kernel source path: '/usr/src/linux-headers-2.6.12-9'
-> Kernel output path: '/lib/modules/2.6.12-9-386/build'
-> Performing cc_version_check with CC="gcc-3.3".
-> running command /bin/grep "^PATCHLEVEL ="
   /usr/src/linux-headers-2.6.12-9/Makefile | /usr/bin/cut -d " " -f 3
-> Kernel module filename is nvnet.ko
   Cleaning kernel module build directory.
   executing: 'cd ./nvnet; make clean'...
   rm -f *.ko *mod.* *.cmd nvenet.o nvenetif.o nvnet.o *~ core
-> Building kernel module:
   executing: 'cd ./nvnet; make module SYSSRC=/usr/src/linux-headers-2.6.12-9 S
   YSOUT=/lib/modules/2.6.12-9-386/build'...
   make -C /lib/modules/2.6.12-9-386/build            \
   KBUILD_SRC=/usr/src/linux-headers-2.6.12-9        KBUILD_VERBOSE=1  \
   KBUILD_CHECK= KBUILD_EXTMOD="/tmp/selfgz17173/NFORCE-Linux-x86-1.0-0306-pkg1
   /nvnet" \
            -f /usr/src/linux-headers-2.6.12-9/Makefile modules
   /bin/sh: /usr/src/linux-headers-2.6.12-9/scripts/gcc-version.sh: file or
   directory not found
   mkdir -p /tmp/selfgz17173/NFORCE-Linux-x86-1.0-0306-pkg1/nvnet/.tmp_versions
   make -f /usr/src/linux-headers-2.6.12-9/scripts/Makefile.build obj=/tmp/self
   gz17173/NFORCE-Linux-x86-1.0-0306-pkg1/nvnet
   make[4]: /usr/src/linux-headers-2.6.12-9/scripts/Makefile.build: file or
   directory not found
   make[4]: *** no rule, to make »/usr/src/linux-headers-2.6.12-9/scripts/Makef
   ile.build« finish.
   make[3]: *** [_module_/tmp/selfgz17173/NFORCE-Linux-x86-1.0-0306-pkg1/nvnet]
   Error 2
   make[2]: *** [modules] error 2
-> Error.
ERROR: The NVIDIA kernel module was not created.
ERROR: Installation of the network driver has failed. Please see the file
       '/var/log/nvidia-nforce-installer.log' for details. You may find
       suggestions on fixing installation problems in the README available on
       the Linux driver download page at [www.nvidia.com](www.nvidia.com).
-> Starting install of NVIDIA audio driver for Linux-x86
-> Checking for loaded module nvsound
-> Checking for loaded module nvaudio
-> License not accepted, aborting installation of audio driver.


 lspci
0000:00:00.0 Host bridge: nVidia Corporation nForce3 Host Bridge (rev a4)
0000:00:01.0 ISA bridge: nVidia Corporation nForce3 LPC Bridge (rev f6)
0000:00:01.1 SMBus: nVidia Corporation nForce3 SMBus (rev a4)
0000:00:02.0 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
0000:00:02.1 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
0000:00:02.2 USB Controller: nVidia Corporation nForce3 USB 2.0 (rev a2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)
0000:00:08.0 IDE interface: nVidia Corporation nForce3 IDE (rev a5)
0000:00:0a.0 PCI bridge: nVidia Corporation nForce3 PCI Bridge (rev a2)
0000:00:0b.0 PCI bridge: nVidia Corporation nForce3 AGP Bridge (rev a4)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 031b (rev a1)
0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd. Yukon Gigabit Ethernet 10/100/1000Base-T Adapter (rev 13)
0000:02:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ab)
0000:02:01.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ab)
0000:02:01.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 03)
0000:02:01.3 System peripheral: Ricoh Co Ltd: Unknown device 0576 (rev 01)
0000:02:01.4 System peripheral: Ricoh Co Ltd: Unknown device 0592
0000:02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

---

### Post by Tobias_at_ch on 2005-11-21
i have installed the kernel-headers

 ERROR: Unable to load the kernel module 'nvnet.ko'.  This is most likely
         because the kernel module was built using the wrong kernel source
         files.  Please make sure you have installed the kernel source files
         for your kernel; on Red Hat Linux systems, for example, be sure you
         have the 'kernel-source' rpm installed.  If you know the correct
         kernel source files are installed, you may specify the kernel source
         path with the '--kernel-source-path' commandline option.

---

### Post by nuclearfly on 2006-01-31
Found one more... This is the same problem I am having.

Anyone with a solution?

---

### Post by linixo on 2006-03-20
Hello,

I had the same problem. This is due to gcc version used to compile the kernel (3.4). The default gcc version delivered with Breezy Badger is 4.0 and that's why the nvidia program doesn't work.
As shown in the howto located at [http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074)
you should use the following commands before lanching nvidia installer :

$ cd “directory where you have the nvidia installer”
$ su
$ CC=gcc-3.4
$ export CC
$ exit
$ CC=gcc-3.4
$ export CC

---

### Post by Big-Wayne on 2006-04-03
oops

---

