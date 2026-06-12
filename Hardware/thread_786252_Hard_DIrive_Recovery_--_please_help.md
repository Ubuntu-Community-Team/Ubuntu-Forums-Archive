---
title: "Hard DIrive Recovery -- please help"
date: 2008-05-08
forum: Hardware
---

### Post by baudelaire on 2008-05-08
Alrighty, guys.  I need your help here.  I just dropped my ide hard drive about 18 inches off the coffee table while it was reading.  It was connected via a ide-to-usb cable directly to my laptop.

I can see the partition table on the drive.  I can see the partitions via the drive mounter applet in gnome as well as gparted.  There were ext2, ext3 and ntfs partitions on the disk.  I cannot currently mount any of the partitions.

Are there any solutions out there in ubuntu to copy the drive in read only or take some sort of disk level image off the raw device?  Thank you in advance for your help -- I need it.

---

### Post by ilrudie on 2008-05-08
fsck can scan partitions and attempt to fix the file system.  I think it works even if you can't currently mount the drive but you have to figure out which raw device it is.  dd can be used to copy raw bits from one device to another.  Check the man pages for more info on how these work or post back with more questions.  I will try to keep an eye on this thread and help you out if I can.

---

