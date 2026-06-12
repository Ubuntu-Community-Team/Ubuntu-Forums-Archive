---
title: "Free space.. how to combine?"
date: 2005-10-27
forum: Hardware &amp; Laptops
---

### Post by Sherkas on 2005-10-27
I have some free space (5 gigs) of unallocated space on my hard drive.

How do I combine it with the Linux part?

---

### Post by heimo on 2005-10-27
Rough overview.

There exists couple different strategies with pros and cons. You could try to merge this space to existing partitions (risky, may be tricky, extends existing partition, probably most useful), or just format as a new partition to some convenient mount point (easiest, not much risks).

First backup your personal data. It never hurts to do this.
Understand your current partitions. Use *sudo fdisk -l /dev/hda *(where hda is your hard disk) to list partitions. Check mount points using *mount*. Make notes.

Use Live CD, like Knoppix. Use gparted or qtparted, check what you can do with those (these are used to repartition), do *not* proceed to do any actual changes before backing up, even though it's perfectly possible to repartition without losing data. Difficulty depends on the current setup.

OR. Create new partition using fdisk or another partitioner, format as ext3 (or reiserfs, xfs, jfs, ext2, fat32... what-ever suits you). Add mount point (mkdir), edit /etc/fstab (man fstab), mount the partition and start using.

Sorry for scarce instructions. For all of these steps there are lots of instructions on these forums and wiki, but of course, feel free to ask if you have any questions. :)

>  How do I combine it with the Linux part?
Maybe next time I'll be patient enough to read the question. ;) Use Live CD with gparted or qtparted (Knoppix should have one of these and I believe at least Breezy Live DVD has gparted), but be sure to backup your personal files (and what ever is important for you on the hard disk[s]) before doing this.

---

