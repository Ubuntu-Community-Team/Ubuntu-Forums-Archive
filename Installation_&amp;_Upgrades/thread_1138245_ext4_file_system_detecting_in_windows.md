---
title: "ext4 file system detecting in windows"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by nims_420 on 2009-04-26
hi,

I recently installed ubuntu 9.04. i am using dual boot with windows xp. Previously, with ubuntu 8.04 (ext3 file system) I was able to access linux drive in windows using a software called ext2fs. But now I cant open linux drive in windows, it says do u winat to format the drive now.
Also, whenever i try to mount windows ntfs drive in linux, it says drive busy, mount failed.
can ne1 help me here..
thanx

---

### Post by Triptol on 2009-04-26
You are probably using the extended features of ext4. In that case ext4 cannot be mounted with an ext3 nor an ext2 drivers, so you are basically out of luck.

Option: backup, reformat with ext3 and restore.

---

### Post by nims_420 on 2009-04-26
i m sorry nut wat do u mean by extended features of ext4 file system and can I expect a driver for windows to detect ext4 file system in some time ?

---

### Post by johnhenry on 2009-04-26
You might find it more effective to have a separate partition (most people use ntfs for this) to share data between Windows and Linux. Like that both can read and write fuly to the partition.

---

### Post by drawkcab on 2009-04-27
> **johnhenry said:**
> You might find it more effective to have a separate partition (most people use ntfs for this) to share data between Windows and Linux. Like that both can read and write fuly to the partition.

Ya, I think this is what I might have to do until fs-driver is updated.

---

### Post by briandotcom0 on 2009-08-03
Ext2 uses by default 128 inodes, and that is what ext2fs is designed to read.  Ext4 uses by default 256 (Some newer distributions will use 256 in Ext3 also in anticipation of upgrading to Ext4, but apparently not yours).  I would suggest the shared ntfs or FAT32 drive until something comes out to read Ext4 on windows.

---

### Post by Sef on 2009-08-04
>   I would suggest the shared ntfs or FAT32 drive

NTFS would be the best way to go.

---

### Post by opticyclic on 2009-09-01
Try Virtual Volumes [http://www.chrysocome.net/virtualvolumes](http://www.chrysocome.net/virtualvolumes)
Although not specifically mentioned, ext4 is visible for me.

You could also try contacting the developer to check if he is doing anything specific with ext4

---

