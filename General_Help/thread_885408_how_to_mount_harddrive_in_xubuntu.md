---
title: "how to mount harddrive in xubuntu?"
date: 2008-08-10
forum: General Help
---

### Post by yenson on 2008-08-10
hello every1 i am running xubuntu 8.04 on my pc.1 and i wanted to know how to access to other harddrive in xubuntu?i can only access to the "file system"diski got another 2 partitions which are ext3 and ntfs that i couldnt access,pls enlight me,and heres my fdisk - l fyi,thanks

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x28002800

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686   83  Linux
/dev/sda2            5100        9729    37190475    f  W95 Ext'd (LBA)
/dev/sda5            5100        9729    37190443+   7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd8487d2e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4863    39062016   83  Linux
/dev/sdb2            4864        4870       56227+   5  Extended
/dev/sdb5            4864        4870       56196   82  Linux swap / Solaris

---

### Post by yenson on 2008-08-11
pls help me thx

---

### Post by tuxerman on 2008-08-11
Open a terminal

Let's say you want to mount all those partitions under /mnt.
Create two directories - one for the linux partition(called "lindisk") and the other for the ntfs one(called "ntdisk"). We'll mount the partitions onto them.

```

sudo mkdir /mnt/lindisk
sudo mkdir /mnt/ntdisk

sudo mount /dev/sdb1 /mnt/lindisk
sudo mount /dev/sda5 /mnt/ntdisk

```

---

