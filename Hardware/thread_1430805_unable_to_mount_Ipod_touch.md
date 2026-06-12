---
title: "unable to mount Ipod touch"
date: 2010-03-15
forum: Hardware
---

### Post by surajpkn on 2010-03-15
Hello,

I think there have been a number of posts regarding problems related to mounting ipod touch. I have another unique problem. When I insert my ipod touch into the usb slot, nothing happens!

Here is the result of 
$lsusb

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0c45:63ea Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 007: ID 05ac:1281 Apple, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 413c:8156 Dell Computer Corp. 
Bus 003 Device 004: ID 413c:8158 Dell Computer Corp. 
Bus 003 Device 003: ID 413c:8157 Dell Computer Corp. 
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


Well, my system does find it in bus 002 device 007.
But $ sudo fdisk -l 
returns the following

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1229     9871911   83  Linux
/dev/sda2            1230       60801   478512090    5  Extended
/dev/sda5            1230        1836     4875696   82  Linux swap / Solaris
/dev/sda6            1837       60801   473636331   83  Linux


And finally, when i tried to mount sdb1 to some location, this is what i get
$ sudo mount -t vfat /dev/sdb1 /media/ipod
mount: special device /dev/sdb1 does not exist

Please, can someone tell me what is wrong here?
Thanks
Suraj

---

