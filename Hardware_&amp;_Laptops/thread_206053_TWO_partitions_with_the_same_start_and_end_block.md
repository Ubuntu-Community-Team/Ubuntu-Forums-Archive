---
title: "TWO partitions with the same start and end block?"
date: 2006-06-29
forum: Hardware &amp; Laptops
---

### Post by phibxr on 2006-06-29
I managed to interrupt an install of Windows XP, which in some horrible way left me with one /dev/hda1 beginning at block 1 and ending at block 1019 (I think), and ANOTHER partition, /dev/hda5, with the same start and ending values. How sn earth did this occur?

This prevented even the Ubuntu LiveCD (Dapper) from booting, by the way. It was solved by booting Novell SLED installation and abort it after deleting /dev/hda1 and /dev/hda5 while partitioning the drive.

---

