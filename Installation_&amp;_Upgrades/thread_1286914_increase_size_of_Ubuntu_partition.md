---
title: "increase size of Ubuntu partition"
date: 2009-10-09
forum: Installation &amp; Upgrades
---

### Post by chrisrico69 on 2009-10-09
Need to increase the size of my Ubuntu partition, any ideas how to do this? Does the partitioning tool on the install CD I received allow me to do this? I have about 30 gig available, unpartitioned. Windows Vista on the other partition.

---

### Post by dannyboy79 on 2009-10-09
i use a livecd, then issue sudo apt-get install gparted, ensure that your partitions didn't get mounted anywhere before running gparted by issuing the "mount" command, if you don't see your hard drive mounted then it's safe to run gparted. then just run gparted and stretch the partition that you want to enlarge and your good to go. it's always smart to backup important data before messing with enlarging partitions. i can say that I have done this twice since installing 9.04, i even shrunk my home partition and enlarged my root partition and no data loss occurred but it's always better to be safe than sorry. good luck.

---

### Post by jeremyswalker on 2009-10-09
Yes, the partitioning tool on the LiveCD will let you do this.
Of course, the usual jargon... Backup important data first!

---

### Post by jeremyswalker on 2009-10-09
> ...it's always better to be safe than sorry.
Absolutely! I have rendered filesystems unusable in the past performing such tasks. (Of course, this was only when I lost my patience waiting for something taking hours to complete.)

---

