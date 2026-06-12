---
title: "Ext3 problems"
date: 2017-03-23
forum: Hardware
---

### Post by mchatzikos on 2017-03-23
Hi,

I am having some trouble with a bunch of ext3 partitions I've created, and I need some input for guidance.

A few months ago I bought a number of WD hard drives to store some data (8 TB in total).  I wiped out the NTFS filesystem that came with them, and installed ext3.  I did so with gparted on an old version of Ubuntu (10.04).

At some point, I had trouble with one of the disks, and I ended up borrowing a friend's 16.04 system to install ext3.  I had created a GPT partition table with my 10.04 on it.  At the end of the process, gparted complained that there was a misalignment (or something like that) with the ext3 system, which could impede performance.

The data I downloaded were in tar archives.  Each file varies in size from 30 to 60 GB.  Recently, I tried to unpack the contents of all the archives on one of those drives.  When the process started out, each file was taking about 2 hours to unpack.  By the end of the process, each file was taking 6-10 hours to unpack.

Even though I can't be sure the problem occurred on the disk 16.04 complained about, it seems to me that what is biting me is the misalignment problems the newer version of gparted was referring to.  In saying this, I am assuming that they were generated in all disks processed by my 10.04 system.  One way to check that would be to unpack the files on another disk, but that'd take about 10 days.

It also seems to me that the best way forward would be to (patiently) back up the data and reinstall both the partition table and the file system.  And that ought to be done with a new version of Ubuntu.

So, questions:

First of all, I would like to know if that's what other people would do, as well.  I know it's almost a no-brainer, but given it can easily take a few weeks to complete the process, I need to be sure that I have to bite that bullet.

Second, if I am to do this, is it a good idea to use GPT instead of the good old MS-DOS partition table?  It seemed so at the time (and still does), but I'd like to know if anyone had any bad experience with GPT, and if there are any things to look out for.

Finally, is ext3 the best choice for a filesystem?  I haven't kept up with the times, so maybe ext4 ought to be preferred.

That's all.

Thanks for your time,

-m

---

### Post by oldfred on 2017-03-23
Use ext4, Ubuntu converted to that, I think with about 10.10 or maybe 9.10?

With newer hardware you have to use newer tools that are updated to work with that hardware.
Windows 7 started using correct alignment for new 4K drives when partitioning and soon after, gparted did also, but that was well after 10.04 which is now long obsolete.

 First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). 
[https://www.ibm.com/developerworks/linux/library/l-linux-on-4kb-sector-disks/](https://www.ibm.com/developerworks/linux/library/l-linux-on-4kb-sector-disks/)
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/) 

        srs5694's to show 8 sector alignment post #9
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
sudo parted /dev/sda unit s print 

I have only used gpt for all new drives or reformatted drives including larger flash drives since about 2010. I do not have any drives over 2GiB though.
But with drives over 2 TiB, you have to use gpt or one of the major work arounds that does not really work with Linux.

      
 GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

---

