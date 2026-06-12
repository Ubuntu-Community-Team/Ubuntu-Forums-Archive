---
title: "External hard drive case"
date: 2010-08-25
forum: Hardware
---

### Post by John Long on 2010-08-25
So I had an old laptop that stopped working. I extracted the hard drive and put it in a NexStar SX case. My new laptop can read the new external via USB but what mounts is a 255 MB Filesystem, not the data that was on the 40 GB drive. I'm assuming because the filesystem was bootable the mount is only reading the bootable portion. Maybe? I don't really know.

What do you all think? I'm using Ubuntu 10.4. Thank you all!

---

### Post by ajgreeny on 2010-08-25
Attach the drive in the case and then run```
sudo fdisk -l
```(that's a lower case L at the end) and report back here the output.

---

### Post by John Long on 2010-08-25
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b982a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29649   238155561   83  Linux
/dev/sda2           29650       30401     6040440    5  Extended
/dev/sda5           29650       30401     6040408+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94e494e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          31      248976   83  Linux
/dev/sdb2              32        4864    38821072+   5  Extended
/dev/sdb5              32        4864    38821041   8e  Linux LVM
john@john-laptop:~$

---

### Post by ajgreeny on 2010-08-25
I see there is an LVM partition on sdb, which may be the problem
> Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          31      248976   83  Linux
/dev/sdb2              32        4864    38821072+   5  Extended
[COLOR=Red]/dev/sdb5              32        4864    38821041   8e  Linux LVM[/COLOR]
but unfortunately I can not tell you how to mount it.  Do a forum or google search to see if "LVM mount" will give you an answer.

---

### Post by John Long on 2010-08-25
So I installed gparted and LVM and now I can mount my real drive. Thank you very much! Easy fix.

---

