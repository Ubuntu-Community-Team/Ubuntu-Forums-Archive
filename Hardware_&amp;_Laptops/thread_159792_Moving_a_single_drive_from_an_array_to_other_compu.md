---
title: "Moving a single drive from an array to other computer"
date: 2006-04-13
forum: Hardware &amp; Laptops
---

### Post by aamukahvi on 2006-04-13
I have a single disk drive, configured as a JBOD array. It's a SATA drive and my motherboard (Asus A7V8X) doesn't support native SATA. The controller doesn't support single disks, so I was forced to make an array with just one disk.

lspci:
RAID bus controller: Promise Technology, Inc. PDC20376 (FastTrak 376) (rev 02)

Now, is it possible to move that single disk from the array to another system with native SATA? (without repartitioning/formatting)

Could trying to do that corrupt the "array"?

---

