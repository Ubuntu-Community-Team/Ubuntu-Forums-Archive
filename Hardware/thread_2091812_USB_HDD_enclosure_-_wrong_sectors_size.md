---
title: "USB HDD enclosure - wrong sectors size"
date: 2012-12-06
forum: Hardware
---

### Post by Magnes on 2012-12-06
I have two USB HDD enclosures. The newer one apparently works well with my HDD (which has 4096B sectors) but the older one (which is much faster being USB 3.0 and all) shows the disk to have wrong partitions. Probably because it assumes the disk has 512B sectors (so the partitions shown in gparted are 4 times smaller and of course not mountable). Is there a way to force Ubuntu to assume the sectors are 4096B? That would almost certainly solve this problem... Some fdisk setting or sth?

---

