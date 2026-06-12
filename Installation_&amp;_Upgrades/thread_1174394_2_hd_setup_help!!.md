---
title: "2 hd setup help!!"
date: 2009-05-30
forum: Installation &amp; Upgrades
---

### Post by lucifuge on 2009-05-30
I have physically got two 120Gb hard disks and want a Ubuntu 9.04 over the entire system.

I take it I need to use advanced partitioning and I also want to make use of EXT3. Can someone supply some example(s) combination??

 All i want to do is have a 2Gb swap file (easy step), but I think i want maybe 10Gb  allocated for '/'  (ie system stuff) and I really want the remainder of the 2 HDs  (120+ 108Gb) ie 228Gb in /HOME   ...ie seen as one large usable data space. This doesn't seem to work as when I allocate a mount point of /HOME on both Hard disks, you can't have the same mount point twice.  

 Is there some applcation of logical or extended partioning that I am missing?  This should be simple but I cant see it.

---

### Post by kidders on 2009-05-31
Hi there,

Spreading filesystems over two disks with no redundancy is very high risk, because it doubles the probability of data loss. In any case, it sounds like you want RAID 0.

---

