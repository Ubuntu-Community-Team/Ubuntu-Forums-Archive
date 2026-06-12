---
title: "USB Memory Drive is automounted with msdos filesystem"
date: 2005-10-20
forum: Hardware &amp; Laptops
---

### Post by christianbrahms on 2005-10-20
Hi,

when I plug in my USB Memory drive, KDE displays the icon in the devices app. When I click on it, it's mounted. But with msdos filesystem, disabling long file names.
This is really annoying! It is not entered in fstab, it's working without that. But I don't know where to change that filesystem type!

Thanks for any hints!
Christian

---

### Post by christianbrahms on 2005-10-21
Solved it myself... For others with the same problem:
The partition table had the FAT16 entry, I changed that to FAT32 (b) and it worked...

It worked correctly with my old mandrake system though, that's why I didn't realise the problem at the first spot.

Thanks anyway,
Christian

---

