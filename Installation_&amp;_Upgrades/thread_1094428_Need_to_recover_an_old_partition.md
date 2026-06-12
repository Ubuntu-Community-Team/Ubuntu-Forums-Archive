---
title: "Need to recover an old partition"
date: 2009-03-12
forum: Installation &amp; Upgrades
---

### Post by adznet on 2009-03-12
Basically this is what happened

Previous set up:
NO RAID
4 750 GB Disks
1 Disk used with ext3 partition

Setup Later:
RAID 0 on all 4 disks (partition tables destroyed)
Installed Linux on 1 partition...but can't get to it

Setup Now:
Deleted the RAID

The problem: I REALLY need to get my old ext3 partition back, as it has some EXTREMELY important files. 

How can I recover it? Any help would be GREATLY appreciated.

---

### Post by adznet on 2009-03-12
This is what I have done so far:

GRUB Disk: Can't find ANYTHING

---

### Post by upchucky on 2009-03-12
if you did not follow instructions and back up important files, then proceeded to overwrite the partitions, you are outta luck.

if you did not follow instructions when partitioning, and the partitioner failed, you are in luck

what does the partitioner show you when you start it?

if there are some ext3 partitions there, it is possible the files are intact.

post the partition tables here.

if you do not understand how the partitioner works and how to back up files, do yourself a favor and read a few of the many hundreds of posts here on how to do this, it will help us help you, and there is a good chance you will solve it yourself just by understanding how it works.

---

