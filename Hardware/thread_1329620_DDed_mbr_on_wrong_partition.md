---
title: "DDed mbr on wrong partition"
date: 2009-11-17
forum: Hardware
---

### Post by marlonbr on 2009-11-17
Hello guys,

I was recovering MBR from a USB Hard Disk (NTFS) and by my insanity instead of "of=/dev/sda" I used "of=/dev/sdb1" (sdb1 is the partition inside the usb disk), resulting on not being able to mount the partition from anywhere.

Tried WinXP with "chkdsk d: /F" and it says it can't detect the type of ntfs (something like that), and tried mouting with ntfs-3g and gparted.

This USB HDD is for backup and have important data on it. So I need any solution that recovers anything.

Important: How I was trying to recover the MBR, only the first 512 bytes of the partition sdb1 where replaced. So I created another partion on sda, sda2 (clean ntfs), and DDed the first 512 bytes of it to sdb1. But the results where the same.

Well, I really need some light from you guys. Any help is appreciated.

---

