---
title: "Kernel USB stack?"
date: 2009-10-13
forum: Hardware
---

### Post by DReeves922 on 2009-10-13
Just bought a [Rosewill external HHD case]("http://www.newegg.com/Product/Product.aspx?Item=N82E16817182142") to load some pics onto an old drive.
The manual says I need to download a kernel USB stack in order to use it, but I'm not really sure what to do.

I found [this site]("http://www.linux-usb.org/") but I don't know what I'm looking for.

Can someone help me out?

---

### Post by falconindy on 2009-10-13
Does the OS not discover the drive when its plugged in? You should already have a USB stack installed by default.

---

### Post by DReeves922 on 2009-10-13
Nope, got everything plugged in, Ubuntu 9.04 doesn't show it

---

### Post by falconindy on 2009-10-14
> **DReeves922 said:**
> Nope, got everything plugged in, Ubuntu 9.04 doesn't show it
From the terminal, post the output of `lsusb` and `sudo fdisk -l`.

---

### Post by DReeves922 on 2009-10-14
:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c404 Logitech, Inc. TrackMan Wheel
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 13fd:1040 Initio Corporation 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 059b:0370 Iomega Corp. 

:~$ sudo fdisk -l
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000066cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005ac5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4865    39078081   83  Linux

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcb4a53fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdc: 13.6 GB, 13613064192 bytes
64 heads, 32 sectors/track, 12982 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table    <~~~~~~~~
-----------------------

Heh, think I just found the problem!  Thanks :)

---

