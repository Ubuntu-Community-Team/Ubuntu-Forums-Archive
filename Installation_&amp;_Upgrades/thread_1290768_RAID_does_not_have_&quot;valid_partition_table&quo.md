---
title: "RAID does not have &quot;valid partition table&quot;"
date: 2009-10-13
forum: Installation &amp; Upgrades
---

### Post by wesg on 2009-10-13
I've been experimenting with RAIDs over the last few days, and have settled on XFS/RAID 6 for my mega server build I will start in a few months. 

To do that, I used a USB drive with 6 partitions and just played around. Currently all 6 partitions are used in the /dev/md0 device. 

However, when I issue fdisk -l, the bottom element pertaining to the USB drive says "Disk /dev/md0 does not contain a valid partition table". Ay suggestions/comments?

---

