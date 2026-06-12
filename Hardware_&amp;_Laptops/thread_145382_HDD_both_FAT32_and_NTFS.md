---
title: "HDD both FAT32 and NTFS"
date: 2006-03-16
forum: Hardware &amp; Laptops
---

### Post by Xecuter on 2006-03-16
I've quickformated a hdd in Windows to NTFS. So Windows says it's NTFS.
But when I boot Ubuntu, it's says the hdd is formated in FAT32.

The problem is when I try to mount it. I can't mount it as NTFS, because Ubuntu thinks it's FAT32, but I can't mount it as FAT32 either, cause I guess it's not looking like a FAT32 filesystem, and then Ubuntu gets comfused. I can't reformat the hdd either cause I have a lot on it.

Need some help!

---

### Post by Ensnared on 2006-03-16
Does the drive mountpoint have an entry in /etc/fstab? If so, it's probably set up as being a FAT32 drive (as that's what it was when you first set it up). Try mounting it with "mount -t ntfs", or try to edit fstab and change the vfat-entry for the drive to ntfs.

---

