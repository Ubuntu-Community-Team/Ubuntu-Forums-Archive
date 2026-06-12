---
title: "CD Burning to USB CDRW"
date: 2005-05-21
forum: Hardware &amp; Laptops
---

### Post by Eric the Grey on 2005-05-21
I'm trying to burn files to a Cyberdrive CW058D CD-R/RW drive but GnomeBaker does not seem to be able to write to the drive.

I get the following error when I try:

> The mount point (e.g. /mnt/cdrom) for the writing device could not be obtained. Please check that the writing device has an entry in /etc/fstab and then go to preferences and rescan for devices. 

My FSTAB looks like this:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/scd0       /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdc1	/usr/music	ext2	defaults	0	0
```


I have changed each cdrom from ro to rw (as shown below, but only one at a time) but neither seems to do any good.  I did reboot between each change to ensure that the changes have taken place.

```

dev/hdd        /media/cdrom0   udf,iso9660 rw,user,noauto  0       0
/dev/scd0       /media/cdrom1   udf,iso9660 rw,user,noauto  0       0
```

Anybody have any idea what I'm doing wrong here?  I figure there's something simple that I'm missing, but I'll be dammed if I can figure it out.


:cool: Eric the Grey

---

### Post by poofyhairguy on 2005-05-21
See if Graveman will work:


sudo apt-get graveman

I personally use K3B in gnome. I don't think Gnomebaker is "there" yet. But its pretty good.

---

### Post by Eric the Grey on 2005-05-22
You can also burn by opening up the "blank CDR" icon on the desktop and dragging files into it, the same way you do under XP.  That failed as well, but without any reason why.

I'll give that a try though.  Haven't installed KDE on this system yet, although I'd like to.


:cool: Eric the Grey

---

