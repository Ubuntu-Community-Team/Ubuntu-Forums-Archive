---
title: "Troubles formatting partitions larger than 2TB"
date: 2009-07-29
forum: Installation &amp; Upgrades
---

### Post by buee on 2009-07-29
I recently rebuilt my NAS and have put in a total of 8TB of hard drives.  3 2TB drives and 2 1TB drives.  I have the 2 1TB mirrored and that's where Ubuntu 9.04 Desktop 64-bit resides.  The 3 2TB drives are in a RAID5.  That's hardware RAID with a 3ware 9650SE.  When installing, I kept running in to issues when attempting to format the 4TB RAID5 partition, it would only format 2TB volumes at a time.  I searched the forums and found that with 3ware cards and Ubuntu, you have to install, then format under GParted.  I did that and still same issue.  Back to the forums...

I found something that said it may be the filesystem I'm trying to format in to and try a different one.  I have now tried Ext4, Ext3, XFS, and reiserfs, all with the same outcome.  Back to the forums...

I found a thread that said the array has to be marked as GPT which supports partitions much higher than 2TB.  I checked and it was set as GPT already, but I set it as GPT again anyway in fdisk.  However, it is still not working, I still end up with a 2TB partition and 2TB of free space.  Does anyone have any insight as to why this might be?

I will be wiping the machine later today anyway to put the OS filesystem back to Ext3 from Ext4, and there's no crucial data on there now anyway as the data partition can't be the size I need it to be so I have no reservations about starting over if that is necessary.

---

### Post by stlsaint on 2009-07-29
try third party software...maybe partition magic(use at own risk)!

---

### Post by buee on 2009-07-29
> **stlsaint said:**
> try third party software...maybe partition magic(use at own risk)!

Is there any reason Ubuntu wouldn't be able to take care of it?

---

### Post by bkortleven on 2009-11-26
Did you eventually get to resolve this?
We're planning on installing a backup/file server on a 3ware 9650SE with 4x 1TB disks in Raid5 (3TB volume) and I don't want to run into similar issues...

---

### Post by khelben1979 on 2009-11-26
If there's a limitation of the software and not the filesystem, you can check out this page for some alternatives: [list of partitioning software]("http://en.wikipedia.org/wiki/List_of_disk_partitioning_software").

I think the Paragon partition manager is pretty good.

---

