---
title: "Cannot access vfat partition in windows"
date: 2007-01-13
forum: Hardware &amp; Laptops
---

### Post by jonttu on 2007-01-13
I created vfat partition in linux (fdisk and mkfs.vfat). In Windows Computer Manager says that it's FAT32 but Unknown Partition and I cannot do anything else than delete it. ](*,)

---

### Post by pay on 2007-01-13
You could partition it as fat32 in Windows and mount it in Linux as vfat

---

### Post by jonttu on 2007-01-13
There is a problem i only can partition it as ntfs :(

---

### Post by pay on 2007-01-13
Ohh ok. That's because Windows XP can't make a fat32 partition larger than 32gb for some reason. You could use an old Windows 98 disc if you have on or use partition magic to make it larger than 32gb.

---

