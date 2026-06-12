---
title: "Help Fstab and a second partition"
date: 2005-02-13
forum: Hardware &amp; Laptops
---

### Post by DeathX on 2005-02-13
Saved the usage of my computer with Ubuntu and my dads blessing and I even had the data on my windows partition read and writable but suddenly it doesn't want to work. Something's wrong in fstab which I don't know, the cd rom and the floppy drive weren't working to begin with either, but that's not a big deal but getting something off of the first hd is. So does anyone see a problem with this - 
,# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/hda1     vfat    rw,user,umask=000

any help is appreciated

---

### Post by Xian on 2005-02-13
Not a definitive answer, so be sure to backup your current config.
Try and substitute this line in place of what you have:

/dev/hda1 /media/hda1 vfat rw,user,umask=0002

---

### Post by hajo on 2005-02-14
Hallo,

go to "www.ubuntu.com" and search for "fstab vfat"
for a quite detailed description, how (an why) to configure a vfat partition in fstab.

It worked on my system.

---

