---
title: "portable hard drive"
date: 2006-11-16
forum: Hardware &amp; Laptops
---

### Post by moondogie on 2006-11-16
Smile  help with portable hard drive
The portable hd is coneccted via usb .
I am running Ububtu 6.10
I am not able to drag files to the portable hd .
the error message i get is :error while copying to /media/usbdisk.
you do not have permission .
Question : How do I get permission ?
The drive is recognized and I can drag files from it to my hd but I can't put anything on it .
Thanks, Moondogie
Reply With Quote

---

### Post by sethmahoney on 2006-11-16
How is the drive formatted?  FAT32?  NTFS?  EXT3?

---

### Post by moondogie on 2006-11-17
Probably NTFS but it could be FAT32 . I can drag and drop from winxp no problem but not with Ubuntu or actually any flavor of Linux .

---

### Post by sethmahoney on 2006-11-17
> **moondogie said:**
> Probably NTFS but it could be FAT32 . I can drag and drop from winxp no problem but not with Ubuntu or actually any flavor of Linux .

If its NTFS, that's probably the problem - most linux distros can't write to NTFS filesystems.  There's software out there to let you do it, but its beta, so there may be problems.  I'd recommend copying all your stuff on that drive to your main drive, and reformatting the portable to FAT32, which can be read from and written to in both Windows and Linux.

---

### Post by moondogie on 2006-11-17
Thank you . I will do that and let you know how it works out .

---

