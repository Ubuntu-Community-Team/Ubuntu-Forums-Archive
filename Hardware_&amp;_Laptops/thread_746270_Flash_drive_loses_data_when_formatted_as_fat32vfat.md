---
title: "Flash drive loses data when formatted as fat32/vfat"
date: 2008-04-05
forum: Hardware &amp; Laptops
---

### Post by runemaste644 on 2008-04-05
I got a kingston 8gb flash drive but it wont keep data for very long at all. When plugged in to a windows system, files appear in found.000 and in linux files suddenly are 0 bytes. I played with it in gparted and as ext3 it works fine, however i need to use this drive on windows systems, too. i tried to make a 7.7GB ext3 partition and a 300MB fat partition (to put ext2fsd on) and the fat partition never formatted correctly. Is there any file system that can 1. be read natively on linux and windows  2. will go without problems on a flash drive and  3. not make my flash drive lose data spontaneously.

---

### Post by luisromangz on 2008-04-05
You can use ext2/3 in Windows, using a driver which can be found on the net. Linux is also able to read/write NTFS with no problems nowadays.

---

### Post by runemaste644 on 2008-04-07
> **luisromangz said:**
> You can use ext2/3 in Windows, using a driver which can be found on the net.
It would be inconvenient to have to install it on every computer i have to use my flash drive on, thats what the fat partition was for.
 > **luisromangz said:**
> Linux is also able to read/write NTFS with no problems nowadays.
NTFS is for hard disks,  for flash drives fat32 must be used.

---

