---
title: "&quot;(folder) is not a block device&quot; when mounting reiserfs SCSI disk"
date: 2007-05-13
forum: Hardware &amp; Laptops
---

### Post by kundalinikat on 2007-05-13
Reinstalled Edgy, now it won't mount my reiserfs SCSI disk.

My fstab:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=84ebcf75-7f3e-46dc-84e3-3790834cccea /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=1b17c194-c076-4deb-b779-67a3984ba46c none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

#added by rob
/rob	/dev/sda1	reiserfs	defaults	0	0


When I run "sudo mount -a" I get the message "/rob is not a block device."

All my personal stuffs are on that disk! at this point my hardware is so crapped I just want to get it all on a USB key before it's too late...

---

### Post by Spartan.II.117 on 2007-05-13
I think you have your /rob and /dev/sda1 backwards...

---

### Post by kundalinikat on 2007-05-13
Laughing at myself

Indeed "/rob" and "/dev/sda1" were backwards.

---

