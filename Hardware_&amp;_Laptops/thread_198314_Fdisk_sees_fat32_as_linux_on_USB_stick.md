---
title: "Fdisk sees fat32 as linux on USB stick"
date: 2006-06-17
forum: Hardware &amp; Laptops
---

### Post by cotcot on 2006-06-17
After formatting a partition with a fat32 filesystem on a USB stick with 'fdisk' I checked it with 'sudo fdisk -l' and it showed a linux partition. Gparted and Qtparted show 'fat32'.
Then I deleted the partition and remade it using Qtparted (Gparted did not work). Again 'fdisk -l' sees it as 'linux' instead of 'fat32'.
Is this a bug ? (I could not find bug reports on this)

---

