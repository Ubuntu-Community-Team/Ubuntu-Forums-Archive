---
title: "Partitioning questions"
date: 2009-10-08
forum: Hardware
---

### Post by Houchy on 2009-10-08
Hello all!

looking at my disk configuration, I'm seeing some weird things I'd like to understand.

**1-** On sda, I installed Windows XP on a 20GB partition and I created a 60GB NTFS partition. However fdisk shows 3 partitions? Why? Is there an extended partition? Can I make it a primary partition without destroying everything?

**2-** I want to create an image on my XP partition (sda5), with this configuration, will the restoration work?

Here is the description of my file system :

```
Disk /dev/sda: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xac68976f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7413    59544891    7  HPFS/NTFS
/dev/sda2            7414        9963    20482875    f  W95 Ext'd (LBA)
/dev/sda5            7414        9963    20482843+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x51195119

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       31871   256003776    7  HPFS/NTFS
/dev/sdb2           58252       60673    19454683+   f  W95 Ext'd (LBA)
/dev/sdb3           60674       60801     1028160   82  Linux swap / Solaris
/dev/sdb5           58252       60673    19454652   83  Linux

```

**3-** My 500GB Hard drive (sdb), on which Ubuntu is installed has an Extended partition. Is it possible to switch back to have only 3 _Primary_ partitions?

Thanks a lot for your help!
Houchy

---

### Post by louieb on 2009-10-08
What did you use to create that partition structure in the 1st place?  
An extended partition is a container for logical partitions. sda5 is a logical partition - so it must be in an extended partition (in this case sda2).

> will the restoration work
maybe depends on where the boot loader was installed - my guess is sda1. So you would need to image the whole drive. Not just sda5.
[HowTo: Partitioning Basics - Ubuntu Forums]("http://www.ubuntuforums.org/showthread.php?&t=282018") 
> Can I make it a primary partition 
sfdisk can do it - but be warned - its a hackers tool - do it wrong and  your not going to like the results. [sfdisk to fix partition table problems]("http://ubuntuforums.org/showthread.php?t=1192598") 
> My 500GB ... switch back to have only 3 _Primary_ partitions?

sfdisk - see above 

Seriously if its not broke - don't fix it.

---

### Post by Houchy on 2009-10-09
Thank you for your answer.

The extended partition were created with GParted. However, the last time I installed XP, I partitioned the disk with XP installer and it was only showing 2 partitions, which I though were Primary partitions!

I think I will reinstall Ubuntu on my 500GB HD to get rid of this useless extended partition.

For my 80GB HD, I'll leave it as is. I wish it was cleaner since I want to use this install as a clone for a quick reinstall when necessary ...
I found a [_nice tutorial_]("http://www.partimage.org/Partimage-manual_Backup-partition-table") that explain how to deal with extended partition, and save their partition table with sfdisk.
I will try that.

I'm closing this post, thanks again.
Houchy

---

