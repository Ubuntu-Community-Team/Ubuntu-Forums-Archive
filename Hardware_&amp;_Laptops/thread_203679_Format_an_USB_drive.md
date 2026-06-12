---
title: "Format an USB drive?"
date: 2006-06-25
forum: Hardware &amp; Laptops
---

### Post by nekr0z on 2006-06-25
Hello there!

I would just like to know how do I format an USB drive in Kubuntu. I found that QParted con see this drive, but it doesn't allow to format it in FAT32. I want this drive to be useful in MS Windows too, and FAT16 doesn't seem to be good for 512 Mb drive.

Another question is how to change label on that drive. I tried mtools, but on "mcd f:" I receive:
Total number of sectors not a multiple of sectors per track!

What could that mean?

Thanks in advance for your help.

---

### Post by Jasper Houtman on 2006-06-25
start up the disk utilty (System > Administration > Disks)
Select the usb drive.
Then klick disable, and after that format.
And enable again when it's done.

---

### Post by nekr0z on 2006-06-25
Would not work.

These USB sticks are displayed as optical disks there, with CD icons. They cannot be enabled or disabled, nor can they be formatted.

---

### Post by Turtle.net on 2006-11-05
The only way I found (easier) was with the command line (see [http://ubuntuforums.org/showthread.php?t=236362&highlight=format+usb](http://ubuntuforums.org/showthread.php?t=236362&highlight=format+usb))

---

