---
title: "Partitioning External HDD for Virtualbox"
date: 2011-06-03
forum: Hardware
---

### Post by LiteDrive on 2011-06-03
Hello all,

I just had a quick question regarding disk partitioning, and am hoping to find out whether or not this will work. 

You see, I have a 500gb WD Passport with plenty of space on it left, and I was hoping to see if I could create a FAT32 partition (with 100gb or so) on it without having to format the entire drive. It has plenty of space left, and there is no reason why 100GB should by any means overwrite what is already on there. I just don't know if this is even possible. 

I was also hoping to know specifically, if this is possible, what option I should select when using the disk utility "Edit Partition" option. There's a lot, and admittedly I feel somewhat confused. 

Anyway, the idea is to basically just create a separate partition for Win XP which I can use for a VirtualBox install. 

Thanks in advance.

---

### Post by mikewhatever on 2011-06-03
I don't quite see why you want a separate partition for VirtualBox. When you install an OS in VirtualBox, you don't use the existing hdd partitions, but create virtual hard disks instead. A virtual hard disk is basically a file (for example, WinXP.vdi) that can be anywhere, even on an external hdd, but you don't need a dedicated partition for it. Just create a folder, VboxDisks, or similar to hold all your virtual disks.
Fat32 is not the best file system for large files, because it has the max file size limit of 4GB.

---

