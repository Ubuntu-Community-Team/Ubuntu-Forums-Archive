---
title: "External Drive not detected"
date: 2014-06-06
forum: Hardware
---

### Post by asearle on 2014-06-06
Dear all.

I have an Intenso "Memory Center" (usb3 external hard drive, 1TB) which is detected by Windows but not by Linux.

In the Spec the Intenso drive is apparently Linux compatible and all other of my drives (usb sticks and external disks) are detected under Linux.

I have tried with Ubuntu, Lubuntu (14.04) and with Knoppix both in usb2 and ubs3 ports but the drive is simply not detected.

Can someone maybe point me to a "HowTo" explaining diagnostic steps that I can take to find out what is happening here?

Any tips would be most gratefully received.

Regards and thanks,
Alan Searle
Cologne, Germany

Link to product spec (in German but probably clear anyway) ... [http://www.intenso.de/multimedia/produktblatt/1318595418.pdf](http://www.intenso.de/multimedia/produktblatt/1318595418.pdf)

---

### Post by rahul4557 on 2014-06-06
try typing " lsusb " in terminal and check whether USB drive is getting detected.

also i guess you must be having NTFS partitions on your external HDD and Lubuntu doesnt have NTFS support presinstalled.

try installing NTFS Support by typing in terminal

> sudo apt-get update
> sudo apt-get install ntfs-3g

also install EXFAT support (you might need it)

> sudo apt-get install fuse-exfat exfat-utils

---

### Post by asearle on 2014-06-06
Yes, lsusb does see the drive.

Here is the relevant entry ...

```
Bus 001 Device 019: ID 174c:55aa ASMedia Technology Inc. ASMedia 2105 SATA bridge
```

Can you give me any tips on how to get the drive to mount?

Many thanks,
Alan Searle

---

### Post by rahul4557 on 2014-06-07
Did you install NTFS and EXFAT support?
After you Install Try connecting the External Disk.

If its not automounting then..

the simplest way would be install an utility called "Disks" from Software Center.
Goto terminal and type > gnome-disks
that should open a Disks Utility which we installed, where you can see all the disks with their partitions and mount any partition that you want very easily.

---

### Post by asearle on 2014-06-07
Many thanks, yes, with gnome-disks the drive is visible.

I am testing with Ubuntu and support for NTFS is installed (Fuse).

I think I see what the problem might be:  The disk is formatted as W95 FAT32.  Isn't FAT32 limited to the size of disk that it can handle (the disk is 1TB)?

I probably need to reformat as NTFS, don't I?

What do you recommend?

Many, many thanks for getting me moving on this point.

Yours,
Alan Searle

---

### Post by rahul4557 on 2014-06-07
NTFS it supports files larger than 4GB(even EXFAT does)... ;)

---

### Post by asearle on 2014-06-07
Fantastic.  I'll re-format.  That should fix it.

Many thanks,
Alan

---

