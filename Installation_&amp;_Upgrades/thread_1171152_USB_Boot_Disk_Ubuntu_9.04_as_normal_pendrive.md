---
title: "USB Boot Disk Ubuntu 9.04 as normal pendrive"
date: 2009-05-27
forum: Installation &amp; Upgrades
---

### Post by bu2bu on 2009-05-27
Hello
I have a small question. Can we create and divide Ubu 9.04 Usb boot disk to 2 parts (maybe partitions?) on a 8 gb pendrive:

1. First part contains the whole bootable system with its internal file system visible only from within ubuntu. (For example 5 GB space)

2. Second part is a normal storage space for all type of files in Windows/Mac/Linux systems (ie. ordinary pendrive).

Is it even possible with 1 or 2 partitions?

Best regards

---

### Post by Kevbert on 2009-05-27
You can do this, but first you need to set up a partition for Windows/Linux which is formatted FAT32 (you can use Gparted for this. Windows may not recognise the partition if this shared space is the second partition.
The second partition you can install 9.04 on, if you have Ubuntu installed on a PC with the System-Administration-Create a USB startup disk tool. You need to make sure the USB is persistent so that files are saved to the USB in one go (otherwise your USB drive will have a short life - maybe 2-3 years).

---

