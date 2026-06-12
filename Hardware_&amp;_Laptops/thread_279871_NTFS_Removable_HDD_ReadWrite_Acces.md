---
title: "NTFS Removable HDD Read/Write Acces"
date: 2006-10-18
forum: Hardware &amp; Laptops
---

### Post by gRoberts on 2006-10-18
Hi all,

I'm running XP and Ubuntu (Dapper) on seperate partitions, as well as I have 2 seperate USB Hard Drives (NTFS).

I've just installed Crossover Office 5.0.3 and installed Office 2003, and I need to open my PST File. When I do it complains about read/write access.

My PST file is stored on a USB Hard drive for backup reasons, and in windows it automatically runs from this drive (if plugged in).

I've installed the NTFS-G3 but previous posts suggest that USB Removable Hard Drives are automatically dealt with, which it does automatically install and display the contents in a new window, but I am still unable to write to the drive (I presume Outlook 2003 does a write check or actually writes to the PST file on opening).

Anyone have any idea's?

TIA

Gav

---

### Post by wislon on 2006-10-18
gRoberts,

I had a similar problem with my NTFS USB drive. I had installed ntfs-3g as well, and it could read from the drive just fine, but not write to it. It turned out that if I just double clicked on the drive to mount it, Dapper would mount it using its own, internal NTFS driver, which only does read only stuff.

As part of the ntfs-3g install, there should be a couple of nautilus scripts that get put in for you as well. If you right click on the drive, you should see (among others) two menu items, one for mounting with ntfs-3g and one for unmounting it, the same way. 

Doing it this way solved the problem for me, I can now read AND write to the disk.

My removable drives are NOT automatically mounted (I had to take entries out of the fstab that I had put in earlier to automatically mount them). Now, when I plug one of the devices in, it shows up in the 'Computer' window, but shows a sort of 'ejected' looking icon. Mounting it (whichever way) places an icon for the drive on my desktop.

Hope that helps you ;)

---

