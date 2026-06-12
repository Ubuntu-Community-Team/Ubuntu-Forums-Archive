---
title: "dvd player help"
date: 2005-07-03
forum: Hardware &amp; Laptops
---

### Post by sgbridges on 2005-07-03
I need some help getting my dvd player to work.


I have just installed 5.04 today.  
I have a cd drive and a dvd drive.  The cd drive works.
I was previously using fedora, and the dvd player works under fedora.
If I boot into Windows, the dvd player works.

I can see the dvd player on Places->Computer, where I see "CD-ROM/DVD-ROM Drive"
I can eject the dvd drive by right clicking on the icon in Places->Computer.
When I put a cd into the dvd player, I can't open the dvd by double clicking on the icon in Place->Computer.  I get a message "mount: No medium found", but there is a cd in there, and the cd works in the cd drive.


Any ideas what might be the problem?

Thanks for the help,




---------------------------------
Sean
triplea.sourceforge.net

---

### Post by sgbridges on 2005-07-03
My /etc/fstab is

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdc        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

