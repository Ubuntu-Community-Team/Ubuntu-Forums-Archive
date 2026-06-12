---
title: "Windows tool for creating large FAT32 partition"
date: 2008-02-07
forum: Hardware &amp; Laptops
---

### Post by jonathanku on 2008-02-07
This was a god-send for me, but only because both Windows and Ubuntu made it pretty difficult for me to create a large (well 120 GB) partition on a new external (USB) hard drive that could be used on both Windoze and Linux.

Sorted this in Win XP Pro 

(a) Creating a new partition without formatting it:
- run compmgmt.msc
- go to "disk management"
- identify the disk and create a new primary partition
- choose **not** to format it

(b) Run fat32format.exe (49kb, runs in 3 sec)
Download [fat32format]("http://www.ridgecrop.demon.co.uk/fat32format.htm") from Ridge Crop
Then run "fat32format.exe x:" from a command prompt where x is the drive.

*As always, be careful when formatting drives!!*

**So - anyone know of an equivalent method in Ubuntu? The community needs it (in my opinion)!**

---

### Post by chrisdeckard on 2008-02-07
I did this on a 160GB disk a few weeks ago:

```
# mkfs.vfat -F 32 /dev/sda1
```

Supports the whole disk, also lets me create large files.

-Chris

---

