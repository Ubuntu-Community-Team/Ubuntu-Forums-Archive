---
title: "External Hard Drive No Longer Auto Mounts"
date: 2007-05-03
forum: Hardware &amp; Laptops
---

### Post by halberd25 on 2007-05-03
I recently reformatted my external hard drive.  I tried to format it to ext3, but I'm not sure if that's what file system it is actually using; when I look at the properties of it, it says file system unknown.  Anyway, it works, but doesn't automatically mount anymore.  I have to use sudo to mount it everytime I restart my computer.  Here's what my fstab looks like: 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,unhide,noauto     0       0
/dev/sda        /media/disk     auto    defaults        1       1

With /dev/sda being the external hard drive.  Any suggestions?

---

### Post by psusi on 2007-05-03
Your fstab entry is messed up.  Auto and defaults are options.  Options need to be separated by commas, not space.  Also auto is default, so you don't need to mention it.  You are missing the filesystem field.  Change it to:

/dev/sda /media/disk ext3 defaults 1 1

---

