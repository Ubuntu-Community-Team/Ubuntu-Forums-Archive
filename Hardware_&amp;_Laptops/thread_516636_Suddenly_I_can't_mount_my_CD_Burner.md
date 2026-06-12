---
title: "Suddenly I can't mount my CD Burner"
date: 2007-08-03
forum: Hardware &amp; Laptops
---

### Post by saxophobe on 2007-08-03
Hey everyone!

I have been reading posts on this, but it doesn't sound like anyone has come up with a workable solution, and that there may have been an update that came out that is responsible for this.

In any case, when I try to browse to my CD Burner, I get the following error:

> 
Unable to mount the selected volume
mount: special device /dev/cdrom does not exist


When looking in my /etc/fstab, it looks like it does exist:

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=b3df8116-6fd1-469c-9048-b685734e1852 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=3d5a8091-5557-47ac-b353-6c9bfd4ac986 none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0


I have tried inserting ide_cd and cdrom into lsmod using modprobe, but this didn't resolve the issue.  

Anyone have any other ideas?

Thanks in advance for your help!

sax

---

### Post by saxophobe on 2007-08-03
I should add that this DID work until recently.

Thanks!

sax

---

### Post by Arjent on 2007-08-05
I had exactly the same problem and after a lot of forum scouring I found a solution that worked.
Try going into your boot sequence and altering the order so your cdrom boots after your hard drive.  It worked for me and a few others.

Good luck

---

### Post by saxophobe on 2007-08-06
Thanks Arjent!

That worked!

Have a good one!

---

