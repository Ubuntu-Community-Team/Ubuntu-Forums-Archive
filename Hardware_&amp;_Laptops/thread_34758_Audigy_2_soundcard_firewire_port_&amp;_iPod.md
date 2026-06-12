---
title: "Audigy 2 soundcard firewire port &amp; iPod"
date: 2005-05-16
forum: Hardware &amp; Laptops
---

### Post by providencia on 2005-05-16
I'm trying to connect my iPod via my only FireWire port on my soundcard.
Any help is appreciated.

Here's my fstab:

##begin
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/sda2       /mnt/ipod       auto   auto,rw,user     0       0
##end

---

