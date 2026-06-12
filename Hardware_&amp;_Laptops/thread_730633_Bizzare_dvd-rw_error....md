---
title: "Bizzare dvd-rw error..."
date: 2008-03-21
forum: Hardware &amp; Laptops
---

### Post by yrufset on 2008-03-21
Hello all helpers, and answers seekers :)

my nec ND-3550A dvd-rw worked just fine on my xubuntu PC, until i moved my /home folder to it's own partition.
since then, it's giving me an error failed to mount "Blank DVD/RW". even on not-empty cds.

tried to mess with fstab. nada.
here it is:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=9330a687-a4d1-4d57-8b75-ee706771dc79 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=e80ed1a2-df1b-4517-ac03-c1f0232a2be8 none            swap    sw              0       0
/dev/hda        /media/cdrom0   rw,udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    user,noauto,exec 0       0
/dev/sda1 	/home ext3 	nodev,nosuid 		0 	2


H-E-L-P?

---

