---
title: "[SOLVED] UltraSPARC Server Software RAID Problems"
date: 2008-07-29
forum: General Help
---

### Post by prince_of_hackers on 2008-07-29
OK, I've searched all over the internet and many different forums, and haven't heard of anything remotely like this, so hopefully somebody has seen this before and can help me figure out what's causing it.

First, some background: I set up an old Ultra 5 workstation as a Samba file server. I used the 8.4GB IDE or whatever drive came with it to install Ubuntu 6.06 LTS SPARC server edition on it. I then added an 80GB IDE hard drive, partitioned and mounted it, and shared it to the Windows machines using Samba. No problems so far, the system works great, and the UltraSPARC never crashes, unlike my Pentium II based PC file server, with has a kernel panic about twice a year.

Now, what I tried next: At this point, 63 of the 80GB hard drive is used up, so I started looking to increase the storage capacity. I decided to try a software RAID array, using an external SCSI multipack hard drive bay purchased from Ebay. Read the following thread to see more about how I learned about this solution:

[http://ubuntuforums.org/showthread.php?t=450711]("http://ubuntuforums.org/showthread.php?t=450711")

OK, at the end of all that, I have an Ultra 5 with 6 external 73GB SCSI drives, sda through sdf. No problems there. I partitioned each drive with a single Linux raid autodetect partition the size of the whole drive. I then used mdadm to create a RAID 5 array with 5 active disks and 1 spare, on the partitions previously created. After some fumbling about with the options to mdadm to get it to create the array the way I wanted it to, (it kept wanting to create it with two spares instead of one) and about 5 hours later I had a functioning multi-disk device, /dev/md0. I created an ext3 partition on it, mounted it, and copied some files to it. I tried unmounting it, shutting down the array and starting it back up, adding and removing disks from the array to make sure I could fix it later if anything went wrong. No problems, everything seemed to be working great.

OK, now for the problem: I thought everything was working as it should be, but for the final test - to make sure the array was properly detected on a reboot. (The power goes out for several hours with every storm here, so reboots happen quite often, and battery backups only last so long) OK, on reboot, the whole system hung. BTW, did I mention this was a remote server I was administering via ssh? Anyhow, when I was able to go to the site and look at the system, it turned out the system had hung trying to fsck the RAID partition, because the RAID partition hadn't started properly.

Now for the part that has me perplexed: The reason the RAID array didn't start properly on reboot was because the partitions with the RAID superblocks were sda1,sdb1,sdc1,sdd1,sde1,&sdf1. However, after the reboot, only sda1 and sdf1 exist. The rest report an invalid partition table. I can recreate the partition tables, and the RAID array will work properly again until another reboot, and the exact same thing happens - the partition tables apparently get scrambled every time, but only on disks sdb through sde.

At one point, I did discover that on an out-of-the box installation, Ubuntu 6.06 starts the evms Enterprise Volume Management System on each boot, which will attempt to take over arrays created with mdadm - however, I modified it's configuration file to exclude all SCSI disks from it's search for software RAID partitions.

If anyone has any ideas on what is causing these problems, or anything I might try, that would be great!

---

### Post by prince_of_hackers on 2008-08-06
OK, I think I've got this one figured out - apparently, the problem is due to the way the partitioning programs I used (parted and fdisk) handled the sun disklabels on the disks. On an msdos disklabel, the partitioning programs prevent you from creating a partition that begins before the end of the disklabel itself, which is stored at the beginning of the disk. However, on a sun disklabel, the partitioning programs will allow (even default to!) starting the first partition on the disk at cylinder zero, which is also the start of the disklabel. Apparently, they expect the filesystem placed in the partition to know better than to use the area used by the disklabel. Ext and ufs filesystems seem to have no problem doing this, but from what I have read reiserfs, lvm, and software raid use all the space made available to them by the partition boundaries. It does appear that raid level 5 does avoid the disklabel area on the first disk in the array, which explains why only the first disk in the array and the hot spare did not have their disklabels overwritten.

---

