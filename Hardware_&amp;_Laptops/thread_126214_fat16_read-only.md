---
title: "fat16 read-only"
date: 2006-02-06
forum: Hardware &amp; Laptops
---

### Post by Nickoladze on 2006-02-06
my usb drive is fat16 and when i plug it in, it says that its a read-only system.

why cant i write? i cant format it either...

---

### Post by Nickoladze on 2006-02-06
well i have a new problem, i plugged it into windows so i could format it to FAT32, but it gave errors and now its completely corrupted with an unknown filesystem and i cant get it to format to anything.

---

### Post by awi on 2006-02-06
Do you have a CD from your usb-drive manufacturer? Maybe some security feature was enabled on it, preventing the write.
Either way I think that with fdisk and mkfs.vfat  (or maybe with gparted GUI), you should not have any problem making a new partition on the drive.

---

### Post by Nickoladze on 2006-02-07
no i dont have a cd, and how can i format it?

---

