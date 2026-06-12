---
title: "Ubuntu doesn't see my second hard drive"
date: 2013-01-29
forum: Hardware
---

### Post by Jason Spaceman on 2013-01-29
Hello:

I built a new system (Gigabyte GA-Z77X UP5 TH board, Intel 3770k CPU, Intel 520 SSD drive 240GB, Western Digital Caviar Black 2TB mechanical drive, etc.).

I am dual booting between OS X Mountain Lion and Ubuntu 12.10 (both 64-bit).  Both operating systems are on the Intel SSD drive.

I am unable to access or format my mechanical drive (the Western Digital one listed above).  It doesn't show up at all in Ubuntu, while in OS X is shows up in the Disk Utility but it won't let me format it, it just says "This disk is too small to contain partitions."  Which is strange since it is 2TB in size and unformatted.

Is there something I'm doing wrong?  Is there a way to mount this disk in Ubuntu and format it?  Perhaps something in the BIOS needs to be set?  Both the SSD and mechanical drives are connected to SATA3 ports on the motherboard. 

Ultimately I want to have a triple boot system with Ubuntu, Mountain Lion, and Win7 on the SSD drive, while the mechanical drive is formatted as FAT32 and used for music, movies, pics, etc.

Thanks.

---

### Post by gnush on 2013-01-29
Have you tried to list all the available disks with fdisk?

```
# fdisk -l
```

If you can't find it there, check if there are any loose cables or anything.

---

### Post by Bucky Ball on 2013-01-29
> **gnush said:**
> Have you tried to list all the available disks with fdisk?

```
# fdisk -l
```If you can't find it there, check if there are any loose cables or anything.

+1. FAT32 has limitations. You are better with NTFS, if Mac can read that, for data storage.

---

### Post by Jason Spaceman on 2013-01-29
I'm beginning to think the WD drive might be dead.  Tonight I went into the BIOS and it lists the drive as having 0.0GB of space available.

I tried swapping out the SATA cable, still the same.  Tried a different SATA port, still nothing.

---

### Post by Bucky Ball on 2013-01-29
Just out of curiousity; when booted in Ubuntu, launch Gparted with that disk connected. What does that show?

---

### Post by Jason Spaceman on 2013-01-29
> **Bucky Ball said:**
> Just out of curiousity; when booted in Ubuntu, launch Gparted with that disk connected. What does that show?

Gparted just shows my SSD drive.  There is no listing for the WD drive.

---

### Post by neowiz73 on 2013-02-07
is the 2TB drive SATA 3.0 capatible? try it in a SATA 2.0 slot and reboot and see if either of the systems see it?  

Could be drivers are incompatible for the SATA 3.0, but that seems unlikely with Ubuntu with Gparted.  

If it is compatible with 3.0, double check to make sure the SATA is ON in bios.

---

### Post by jsmayne on 2014-02-05
i have the same problem

gparted does see the second drive

---

