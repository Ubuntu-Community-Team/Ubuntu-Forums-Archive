---
title: "Ubuntu on Compaq/Vista Laptp"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by th1bill on 2009-11-07
I have an elderly gentleman that wants me to set him up with a dual boot.  I understand that Vista has a Restore Partition that must remain in place for the warranty to be valid.  I also have seen some say to use the Windows Disk Management Tool to resize the partition after defragging the HDD.  Is it possible to put Hardy on his lap top and leave that pesky Restore Partition there?  And if so, how please.

---

### Post by mick55 on 2009-11-07
Hi th1bill 


Yes, it's possible and quite easy.
Follow these instructions to the letter and you will be 
dual booting in no time at all.

First you should defrag Vista to move all the files closer together 
before you shrink the partition.
Ignore the restore partition, it will be on it's own
Primary Partition at the very end of the drive.
Leave it be, it doesn't figure into the plan.

OK, lets shrink the Vista partition

1) Click on the Start menu
2) Right click on Computer and click on Manage
3) You may get a User Account Control dialog here; just click Continue
4) In the left pane, open up the Storage category and click on Disk Management
5) Here, you will find your partitions for your disks. Right click on the partition you&#8217;d like to modify.
6) Click on Extend Volume or Shrink Volume to extend or shrink the selected partition.

After you have shrunk your partition, boot up the Ubuntu Cd.

When you arrive at the partitioning section
select to use all unpartitioned/unused space for Ubuntu.

Caveats
..................
It is essential to shrink the partition with Vista's built in tool
or the Vista loader will not boot.
Make sure Ubuntu has at least 20GB of free space to install to.
Do not create any new partitions manually prior to installing Ubuntu.
Ubuntu will create its own partition and swap partition and format 
them without user intervention.

From when you boot the Ubuntu Cd until it completes the install
will be about 20-30 minutes.

good luck
mick

---

