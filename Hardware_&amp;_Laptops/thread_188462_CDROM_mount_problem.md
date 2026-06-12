---
title: "CDROM mount problem"
date: 2006-06-04
forum: Hardware &amp; Laptops
---

### Post by Tosa on 2006-06-04
I'm trying to upgrade to Dapper using iso image, but when I run
> sudo apt-cdrom add
I get
> E: Failed to mount the cdrom.
But it's already mounted and I can browse its content in Konqueror... On the other hand, in media folder there are **cdrom,** **cdrom0,** and **hdc** folders and the disk content is in **hdc!**
I suppose that's the problem, but i dont know what to do about it...
This is my fstab:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  vfat    rw,user,noauto  0       0
/dev/hda1 /media/windows vfat umask=000 0 0
/dev/hda5 /media/D: vfat umask=000 0 0
I'd appreciate some help.
Regards

---

### Post by Tosa on 2006-06-06
Anybody, please?

---

