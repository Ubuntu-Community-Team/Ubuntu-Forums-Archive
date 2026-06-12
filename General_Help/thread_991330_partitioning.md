---
title: "partitioning"
date: 2008-11-23
forum: General Help
---

### Post by _Corsair_ on 2008-11-23
I'm planning to partition my ubuntu only HD to make room for another OS (red hat) and I've been doing a little reading, but I want to be sure I'm doing it right.

I've already backed up all my data on an external HD.  My current "fdisk p" stats are:
```

The number of cylinders for this disk is set to 24321.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

...

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000974e8
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23580   189406318+  83  Linux
/dev/sda2           23581       24321     5952082+   5  Extended
/dev/sda5           23581       24321     5952051   82  Linux swap / Solaris
```
Ignoring that warining at the beginning (I hope this will not cause problems?)  I plan to follow the steps [_here_]("http://tldp.org/HOWTO/Partition/fdisk_partitioning.html") (section 5.2) to downsize sda1, then create a new partition with the room created.  Then I'll install Red Hat from its live CD, choosing sda4, or sda2 if I rename the Extended and Swap to 3 and 4 respectively.

Good plan, or have I missed anything?

---

### Post by Partyboi2 on 2008-11-25
You can only have 4 primary partitions so you could resize sda1 and add to your extended partition and create the partitions for the other os under the extended partition. You can use the same swap for both os but I think I read somewhere that if you want to use hibernation/suspend you would need seperate swap.

---

