---
title: "vaio pgc-fr215e - can't mount dvds"
date: 2005-05-10
forum: Hardware &amp; Laptops
---

### Post by therealanselm on 2005-05-10
Hi all,

Just intalled (k)ubuntu 5.0.4 on a Sony Vaio PCG-FR215E. All works fine, exept one thing : I can't mount DVDs.

I can, however mount CDs in the same drive. If I put a CD in the drive I get the following :

stephane@Stef:/$ ide_info /dev/dvd
MODEL="QSI CD-RW/DVD-ROM SBW-241"
FW_REV="VS03"
SERIAL_NO=""

If I put a DVD in the drive (which I know to work on the same machine in winxp), I get this :
stephane@Stef:/$ ide_info /dev/dvd
open() failed: No medium found

I didn't find anything relevant on these forums. Can someone help me ?

Cheers,
Anselm

---

### Post by emlprime on 2005-05-18
I'm having the same problem.  I have a DVD burner and it tries to mount twice and then fails.

here's my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               reiserfs defaults        0       1
/dev/hda2       /boot           ext3    defaults        0       2
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Peter

---

