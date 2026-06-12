---
title: "Difficulty Mounting Volumes on a Partitioned External HD"
date: 2011-06-30
forum: Hardware
---

### Post by hunternsf on 2011-06-30
I'm having a great deal of difficulty with an external hard drive.  I'm currently running a dual boot system (XP Service Pack 3 and Ubuntu 11.04 Natty Narwahl) on a Dell Inspiron B120.  I'm trying to set up a new 80 GB Hitachi external HD.  Using GParted, I formatted the drive and set up the partitions.  The partitioning scheme is as follows 10GB NTFS Primary, 2GB Linux-Swap Primary, 50GB FAT32 Primary, 12GB Unallocated.  After applying those changes, I went into Disk Utility and the HD appears along with the correct partitions.  When I try to mount the volumes for partitions 1 and 3, I get a pop-up stating:

> Error Mounting Volume
An error occurred while performing an operation on "Home"
(Partition 3 of HTS548080m9AT00): The daemon is being inhibited.


When I try to to check the filesystem I get a pop-up stating:

> Error Checking filesystem on volume
An error occurred while performing an operation on "Home"
(Partition 3 of HTS548080m9AT00): The daemon is being inhibited.


Throughout the time that I'm attempting to troubleshoot the problem, the external drive light is on and blinking. With my frustration hitting a boiling point, I try to shut down the drive and remove it so that I can plug in a different external HD that works PERFECTLY.

However, when I try to shut down and safely remove the drive, I get a pop-up stating:

> Error Detaching Drive
An error occurred while performing an operation on "80GB Hard Disk"
(HTS548080m9AT00): The daemon is being inhibited.

Can anyone tell me what I'm doing wrong?  I'm a newbie and not that skilled with Terminal commands, so please dumb it down for me if you request specific command output.

Thanks

---

