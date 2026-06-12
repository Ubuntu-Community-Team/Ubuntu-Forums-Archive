---
title: "Problems with the new 4k sector size HDs?"
date: 2011-05-09
forum: Hardware
---

### Post by Seeb on 2011-05-09
Hey,

I'm about to get a new HD for my lappy. I'll prolly get myself a Samsung M7 which is available in the old/standard 512 sector size version and the new 4k sector size. 
I've read that there aren't problems with win7 but that u have to somehow partition ur drive for Linux in some special way.

Is that still the case or can I just simply install it?

(I'm using win7 and ubuntu in dualboot)

---

### Post by Seeb on 2011-05-09
bump

---

### Post by oldfred on 2011-05-09
I do not think it is a windows or Linux issue, but a how your partitions are set up.

First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of RAID arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
srs's to show 8 sector alignment
$ sudo parted /dev/sda unit s print

---

