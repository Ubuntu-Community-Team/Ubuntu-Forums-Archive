---
title: "Unmountable usb"
date: 2009-01-25
forum: Hardware
---

### Post by ibbill on 2009-01-25
I have windows xp on one partition and ubuntu 8.10 on another partition.

Am trying to install ubuntu 8.10 on a usb stick says unmountable and I do not have permission.You are not privileged to mount this drive,

Using the System>Administration>create a USB start up disk. That all being said I want to give this to my daughter who can run it on her computer with out installing linux 8.10 on her computer.

ibbill@ibbill-desktop:~$ sudo fdisk -l 

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4073    32716341    7  HPFS/NTFS
/dev/sda2            4074        6623    20482875    5  Extended
/dev/sda3            6624        8918    18434587+   7  HPFS/NTFS
/dev/sda4            8919        9725     6482227+  82  Linux swap / Solaris
/dev/sda5            4074        6623    20482843+  83  Linux

Disk /dev/sdb: 8127 MB, 8127512576 bytes
5 heads, 32 sectors/track, 99212 cylinders
Units = cylinders of 160 * 512 = 81920 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          51       99213     7932992    b  W95 FAT32
ibbill@ibbill-desktop:~$

---

### Post by utnubuuser on 2009-01-26
Has this USB been "uncleanly removed", meaning removed from Ubuntu without "unmounting" first, or without "ejecting" in Windows?

That would cause that sort of issue.  - Try plugin it into a Windows machine and "ejecting" it.

You can always do a sudo chmod 777 /dev/sdb1 (assuming your USB is the sdb1 listed above)

---

### Post by ibbill on 2009-01-26
Thanks no luck. Darn. any other suggestions please.

---

