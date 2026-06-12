---
title: "Why no dual boot with GRUB (mythbuntu + ubuntu)"
date: 2009-09-27
forum: Installation &amp; Upgrades
---

### Post by cat2005 on 2009-09-27
I recently installed mythbuntu on sda.  This is the sda setup:

- sda1 (root and mbr)
- sda2 (swap)
- sda3 (home)

I recently installed ubuntu on sdb.  This is the sdb setup:

- sdb1 (root)
- sdb2 (swap)
- sdb3 (home)

I can not make GRUB dual boot.  I have tried the following and each yielded the same result:  GRUB took me directly to mythbuntu (sda1):

- install GRUB only on sda1
- install GRUB only on sdb1
- install GRUB on both sda1 and sdb1

What gives?  How do make GRUB give me a menu, like it did when I had Windows on sda and Ubuntu on sdb?

Thank you.

---

