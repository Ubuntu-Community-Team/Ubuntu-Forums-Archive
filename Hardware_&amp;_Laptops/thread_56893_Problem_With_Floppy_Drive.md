---
title: "Problem With Floppy Drive"
date: 2005-08-14
forum: Hardware &amp; Laptops
---

### Post by alec on 2005-08-14
Hi, I cannot get my floppy drive to mount. I keep getting the following error message:

'No final newline at the end of /etc/fstab'.

My fstab reads as follows:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdc        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


Any suggestions as to how to sort this would be appreciated

Cheers Alec.

---

### Post by jasmuz on 2005-08-14
Hi!
Open your /etc/fstab
at the end of the file, hit enter and save (hope that works because everything seems to be in order, unless you are mounting a defective floppy, hav you tried mounting manually the floppy?)

---

### Post by alec on 2005-08-14
Yep that cured the newline problem, but I now have another one. Now the error message reads: 

'Mount: I could not determine the filesystem type, and non was specified'.

I am using standard floppys, and have tried three and get the same message.

Anybody got any ideas about this one???

Cheers Alec

---

### Post by jasmuz on 2005-08-16
try this sudo mount -t vfat /dev/fd0 /media/floppy0
and open your floppy disk, check around to see if you see any files.

You might be getting this problem is they arent formatted properly.

---

