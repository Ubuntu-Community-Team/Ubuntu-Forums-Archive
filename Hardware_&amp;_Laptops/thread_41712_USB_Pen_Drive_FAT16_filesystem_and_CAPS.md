---
title: "USB Pen Drive FAT16 filesystem and CAPS"
date: 2005-06-14
forum: Hardware &amp; Laptops
---

### Post by hal8000 on 2005-06-14
Recently bought a 256M USB pen drive. It is recognised and appeared on Gnome 2.10 desktop straight from the box.

However the pen drive arrives pre-formatted and is a FAT16 filesystem not FAT32. One
immediate problem is that part of my web site has 2 folders that are named in capital letters, these are reproduced in lower case on the pen drive.

Output of dmesg:
--snip--
SCSI device sda: 489472 512-byte hdwr sectors (251 MB)
sda: assuming Write Enabled
sda: assuming drive cache: write through
SCSI device sda: 489472 512-byte hdwr sectors (251 MB)
sda: assuming Write Enabled
sda: assuming drive cache: write through
 sda: sda1
Attached scsi removable disk sda at scsi1, channel 0, id 0, lun 0
usb-storage: device scan complete
FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will b e case sensitive!


I guess this is the limitation of FAT16 no all CAPS filenames.  If I move all the files
can I recreate a FAT32 (type 0C) filesystem on dev/sda1 with linux fdisk?
I need to read files in both OS's.
Thanks in advance.

---

