---
title: "usb hard drive problem"
date: 2007-07-04
forum: Hardware &amp; Laptops
---

### Post by jdeng@mtoliveboe.org on 2007-07-04
Hi all, I plug in an external usb 200g hard disk. read, no problem. but I can't write to it. any suggestion?

---

### Post by Arrdee on 2007-07-04
What file system is it partitioned with? (NTFS, FAT32...)

If it's NTFS, you may need to specifically enable write support for it. If you have ntfs-3g installed, go to System Tools > NTFS Configuration Tool, enter your password, and make sure the box for write support are checked for external drives.

---

### Post by nigelt on 2007-07-05
Marvelous! Thank you! I have been running into this problem as well for ages.

---

