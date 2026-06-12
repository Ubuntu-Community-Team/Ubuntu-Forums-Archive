---
title: "ububtu on already partitioned harddrive"
date: 2009-01-15
forum: Installation &amp; Upgrades
---

### Post by cool-vibes on 2009-01-15
Hi i'm running xp and i have a free partion on my harddrive that i would like to put ubuntu on, it is a NTFC partition  could someone give a hand how to direct the installation of ubuntu to that specific partition. Thanks

---

### Post by 2hot6ft2 on 2009-01-15
You mean it's NTFS.

FIRST CAN YOU TAKE A SCREENSHOT OF THE PARTITIONS AND POST IT?


You'll want to create 2 partitions where that one currently is.

When going thru the install steps choose manual partitioning,
and select that partition and delete it,
Choose create NEW and make a partition about 2GB should be plenty since you've given no system specs.
For type choose linux swap

For the rest of the space that's now empty create a NEW partition choose ext3 for the type,
mark it to be formated,
and the mount point as /
That's really all there is to it.

Continue thru the installer.

---

### Post by cool-vibes on 2009-01-15
Here is a pic of the partitions.

---

### Post by 2hot6ft2 on 2009-01-15
That's not showing me what I was looking for. How many actual drives are in the pc and whether or not any of them were inside an extended partition or not. Looking at it again I see there are no extended partitions.

The instructions above should work in either case. Like I said you'll want to make 2 partitions though one for swap and one for the OS.

Just be very sure when selecting the partition you're going to make the changes to.

---

