---
title: "how to share and allocate disk space"
date: 2009-10-21
forum: Installation &amp; Upgrades
---

### Post by husayn on 2009-10-21
Hello everyone, i would like to know if it's possible to hard disk space to existing one from free available ones

---

### Post by gareththegeek on 2009-10-21
Do you mean you want to make one hard disk partition smaller then add that space to a different partition?

In the System Menu there is a Partition Manager (gparted) which allows you to resize your hard disk partitions.

Please make sure you backup any data you wouldn't want to lose first though and if you are resizing a windows partition, make sure you defrag it first.

---

### Post by Mark Phelps on 2009-10-21
> **husayn said:**
> Hello everyone, i would like to know if it's possible to hard disk space to existing one from free available ones

Don't quite understand your question, so I'm going to make a guess at two different responses ...

If you're asking about combining the free space across several partitions, all on the same physical drive, into one shared space, the answer is basically, no.  You would have to first, shrink the partitions that have free space available. You would then have to move them on the drive so they are adjacent to each other.  You would then have to create a new partition to fill the consolidated free space.

If you're asking about combining free space across several physical hard drives, the answer is yes -- providing you use something that spans drives, like RAID.

---

