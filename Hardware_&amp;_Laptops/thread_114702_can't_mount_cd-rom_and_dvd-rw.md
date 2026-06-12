---
title: "can't mount cd-rom and dvd-rw"
date: 2006-01-09
forum: Hardware &amp; Laptops
---

### Post by gosh on 2006-01-09
Hi,

I have a cd-rom and dvd-player, but both can't be mounted.

This is fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

If I try to mount hdd of hdc  it says:
mount: special device /dev/hdd does not exist

---

### Post by taurus on 2006-01-09
Look at the dmesg to see if the kernel even sees your two CD drives!  Also, make sure you have a data CD in the drive before you attempt to mount it...

dmesg | more

---

### Post by dcstar on 2006-01-09
[QUOTE=gosh]Hi,

I have a cd-rom and dvd-player, but both can't be mounted.

This is fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

If I try to mount hdd of hdc  it says:
mount: special device /dev/hdd does not exist[/QUOTE]
Does /dev/hdd exist?, look in the /dev directory and tell us what you can see.

---

### Post by gosh on 2006-01-10
[QUOTE=dcstar]Does /dev/hdd exist?, look in the /dev directory and tell us what you can see.[/QUOTE]
No,

When I do dir /dev/hd*  I get: 
/dev/hda  /dev/hda1  /dev/hda2  /dev/hda5
which are my harddisk partitions

---

### Post by Tuf on 2006-01-10
how about /dev/cd*

---

### Post by gosh on 2006-01-10
Nothing there with /dev/cd*

---

### Post by gosh on 2006-01-16
I've fixed it.
I changed /dev/hdc to mount cdrom0 and /dev/hdd to mount cdrom1 in fstab and rebooted.
Now they both work.

Strange, not?

[QUOTE=gosh]Hi,

I have a cd-rom and dvd-player, but both can't be mounted.

This is fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

If I try to mount hdd of hdc  it says:
mount: special device /dev/hdd does not exist[/QUOTE]

---

