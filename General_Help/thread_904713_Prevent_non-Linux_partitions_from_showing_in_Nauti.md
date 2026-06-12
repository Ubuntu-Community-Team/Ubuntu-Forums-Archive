---
title: "Prevent non-Linux partitions from showing in Nautilus"
date: 2008-08-29
forum: General Help
---

### Post by mfeltman on 2008-08-29
Hey folks, I have a dual boot setup on my laptop with Ubuntu for productivity and Vista for the occasional gaming fix.

Right now Nautilus shows the Vista partition as "17.2GB Media", which isn't really causing a PROBLEM but it's not really pleasing aesthetically.  :-)

Can I make it go away without serious modification to my system?  Is there a hidden option somewhere to avoid displaying it in Nautilus?

Thanks!

---

### Post by Sycron on 2008-08-29
Post the output of the file **/etc/fstab** .

---

### Post by mfeltman on 2008-08-29
You mean contents?  fstab doesn't appear to be executable..

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=7065b47d-5fb3-4425-8032-d5f9337d3766 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=2729ee02-5159-4cc9-8ffa-dc5466d3a1f4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by mfeltman on 2008-08-30
Anyone?  Sorry to bump but I just can't figure this out.  Is there a way to hide unmounted drive space in Nautilus?

---

### Post by mb_webguy on 2008-08-30
Are you talking about unmounted partitions?  If so, look [here]("http://ubuntuforums.org/showthread.php?t=428196&page=4").

---

### Post by drs305 on 2008-08-30
> **mb_webguy said:**
> Are you talking about unmounted partitions?  If so, look [here]("http://ubuntuforums.org/showthread.php?t=428196&page=4").

Now that's funny. I just dug out my notes and posted the same solution on another thread within the past 10 minutes. And I haven't used this solution in years. ;-)

[http://ubuntuforums.org/showthread.php?t=905859]("http://ubuntuforums.org/showthread.php?t=905859")

---

### Post by retrovertigo on 2008-08-30
> **mfeltman said:**
> You mean contents?  fstab doesn't appear to be executable..

Is that the complete contents of /etc/fstab?  Also, can you post the contents of /etc/mtab?

---

### Post by mfeltman on 2008-08-30
mb_webguy: Thanks!!  Perfect.  A little intimidating, but I'll try it out eventually.  :)  I dislike messing with low-level stuff as I invariably end up having to reinstall eventually, it's like Russian roulette. :)  I'm a programmer and comfortable messing with source files and adding scripts but I'll always break something irretrievably in the end.

---

