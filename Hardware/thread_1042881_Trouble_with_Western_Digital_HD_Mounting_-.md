---
title: "Trouble with Western Digital HD Mounting -"
date: 2009-01-18
forum: Hardware
---

### Post by rgm1231 on 2009-01-18
Trying to get a western digital 250gb external hd to mount (me2500) with no luck. Im new to ubuntu. I've searched all of the forums and can't find a solution.

i get the following from sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x40000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5c74ae42

lsusb gets me

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 04e8:3419 Samsung Electronics Co., Ltd Composite Device
Bus 002 Device 004: ID 045e:0024 Microsoft Corp. Trackball Explorer
Bus 002 Device 003: ID 413c:2010 Dell Computer Corp. 
Bus 002 Device 002: ID 413c:1003 Dell Computer Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 1058:0704 Western Digital Technologies, Inc. 
Bus 001 Device 002: ID 05ac:1292 Apple, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
rgm071000@rgm071000-laptop:~$ 


Can someone help me??

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS

Does anyone have a solution to this issue? Any help would be greatly appreciated.

---

