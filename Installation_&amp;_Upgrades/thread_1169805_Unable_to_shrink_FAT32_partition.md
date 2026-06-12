---
title: "Unable to shrink FAT32 partition"
date: 2009-05-25
forum: Installation &amp; Upgrades
---

### Post by jersoncito on 2009-05-25
I have an external 500GB USB drive which I want to use to install Ubuntu on it. I already used 232 GB of 465 GB. I tried to shrink the FAT32 partition and create what I need to install ubuntu. The problem is that Gparted never finishes the process. I used ubuntu 9.04 live cd and Gparted Live CD. Both with the same result. There is not error or anything that indicates that something is wrong. I already tried to find errors using Gparted and the Windows utility. Everything seam to be fine. The de-fragmentation in Windows would take days.
I don't have any other drive to move the data and delete the FAT32 partition...
Is it a normal behaviour with Gparted and big FAT32 partitions?

Any suggestion?

---

### Post by kiridude on 2009-05-25
gparted will not let you cut windows too close. In other words, try leaving a little extra space in the windows partition and see if that works.

And make sure you defrag

---

### Post by Mark Phelps on 2009-05-25
Just so you know ... GParted is not fast, in fact, with a multi-hundred GB drive, expect it to take HOURS to do its work.  So, if it's finishing quickly, it's most probably failing.

---

