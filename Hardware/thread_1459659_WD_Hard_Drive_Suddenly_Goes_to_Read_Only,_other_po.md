---
title: "WD Hard Drive Suddenly Goes to Read Only, other posts dont seem to help"
date: 2010-04-21
forum: Hardware
---

### Post by Atticus8631 on 2010-04-21
Hi guys,
today my WD external hard drive just set everything to read only so I can't add/delete anything.  I'm not sure exactly what caused it and other posts online don't really seem to work for me.  I'm on Ubuntu 9.10

blake@Ruiner:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x14c3e5a5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6992    56163208+  83  Linux
/dev/sda2            6993        7296     2441880    5  Extended
/dev/sda5            6993        7296     2441848+  82  Linux swap / Solaris

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xacdd9b22

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       77825   625129281    c  W95 FAT32 (LBA)
blake@Ruiner:~$ df -h

I've had the hard drive in Fat32 so I can watch movies on my PS3.  Everyone is saying that my hard drive must have gone to ntsf.  I never had a partition or anything like that on the hard drive.  I just really want to be able to put things on and off my hd again!  Any help would be greatly appreciated.

---

### Post by Cracauer on 2010-04-21
`dmesg`?

---

### Post by Atticus8631 on 2010-04-23
Hey thanks for trying!  I just plugged it into my PS3 and deleted a few things and now it works fine (knock on wood)!

---

