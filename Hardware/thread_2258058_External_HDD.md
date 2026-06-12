---
title: "External HDD"
date: 2014-12-24
forum: Hardware
---

### Post by Shamik_Biswas on 2014-12-24
Hello,

I am having a 1 TB External Seagate HDD which is full of important data. Few days ago...the HDD filesystem got corrupted to RAW format. As RAW is Un-readable by Windows... I cannot get my data back. In this situation, I can't Re-format the HDD also as this would delete all the existing data.

I tried PartitionRecovery but with no help. Now...I am trying to connect the HDD in linux system (Lubuntu). In here also, the HDD does not get recognized at all.

I tried EaseUs data recovery...but all the data item found are shown as 0 bytes data :O

**_Question:_**
[B]
Is there any way to recover the data in Lubuntu ???[/B]

---

### Post by yancek on 2014-12-24
What exactly happened to get it into this state?  Which version of windows are you using?  Is this a windows filesystem partition?  Is the drive recognized in the BIOS?  I don't know anything about 'RAW' format but the link below gives some advice about trying to repair.  Worth reading at least.  Another possible option is to download and try using testdisk from the second link below.  Be sure to read their Step-by-Step guide before starting.  

[http://html5.litten.com/updated-how-to-fix-external-disk-drive-suddenly-became-raw/](http://html5.litten.com/updated-how-to-fix-external-disk-drive-suddenly-became-raw/)

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by oldfred on 2014-12-24
With NTFS both the partition table must have code 07, and the partition's boot sector must have NTFS configuration in it with the same start & size in sectors as the partition table. 
RAW in Windows means it is not formatted, but it is that the other data is missing.

NTFS does have a backup of the partition boot sector, which testdisk can show. If it is a valid NTFS type you may be able to restore it. Or if partition table is not 07, you can just reset that without totally formatting it.
But that is not a sure thing if other issues apply.

Did you remove drive without properly shutting down, or have abnormal shutdown, power failure etc?

In Testdisk you want to get to this screen and see if Testdisk says backup is valid.
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

And does this show NTFS with code 07?
sudo fdisk -lu

---

### Post by Mark Phelps on 2014-12-24
> all the data item found are shown as 0 bytes data :O

Very bad news!!  I had much the same problem this last year with two different hard drives -- BOTH of which were Seagate drives.

That information, coupled with the reporting of a "raw" format are pretty good indications that you have had what I did -- head crashes.

IN which case, NOTHING can be recovered without first rebuilding the drive in a "clean room" facility -- which, last time I checked, was very expensive, starting at $1000 USD.

---

