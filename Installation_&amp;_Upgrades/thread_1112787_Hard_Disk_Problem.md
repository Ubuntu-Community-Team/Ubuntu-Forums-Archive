---
title: "Hard Disk Problem"
date: 2009-04-01
forum: Installation &amp; Upgrades
---

### Post by leonoel on 2009-04-01
Hello

I am tryign to repair a computer that seems to have a problem with the Hard Disk.

It does not allow the ubuntu installation directly from the CD, do you have any ideas to solve it. 

Thank You

Leon

---

### Post by Mark Phelps on 2009-04-01
> **leonoel said:**
> Hello
It does not allow the ubuntu installation directly from the CD ...


This could mean practically anything -- dead drive, drive full, drive already formatted, SATA drive without proper drivers, etc.

Boot to a liveCD and enter the following at a terminal: "sudo fdisk -lu" (That's a lower-case L, not a one).  That will determine if Ubuntu can even "see" the drive, and if do, what partitions are already on the drive.

---

