---
title: "RAID 0 question"
date: 2009-02-17
forum: Hardware
---

### Post by davidself1001 on 2009-02-17
I have a RAID 0 setup using the ASUS Drive Xpert SW on my P5Q-E MB.  I have two 1TB drives.  Both in Windows and in Linux it shows up as a single drive but the capacity of the drive is 2TB.  Is that they way it should be?  Or should it show only 1TB in the stripe mode?

---

### Post by davidself1001 on 2009-02-18
After a reboot on my XP machine now I have to different drives but both of them are 2TB (even though I have 2 1TB drives configured in RAID 0).  Any ideas?

---

### Post by alanwalterthomas on 2009-03-18
As far as I know that's the way it should be.

RAID 0 will put like-sized disks together to make a big disk, (so the 2 1TBs become 1 2TB) & also divide up the read/write operations to boost performance. Note that if one drive fails the data on the other one is unusable.

RAID 1 would make your multiple drives appear as a single drive but instead of dividing the reads & writes, they're doubled & each disk gets a copy. No change in performance, but now if one disk fails the data on the other remains in good shape.

I hope that helps,

---

