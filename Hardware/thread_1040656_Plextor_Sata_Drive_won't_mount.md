---
title: "Plextor Sata Drive won't mount"
date: 2009-01-15
forum: Hardware
---

### Post by thewooster on 2009-01-15
Hi!

So I am running Ubuntu 8.10 (Intrepid), and I can' get my SATA DVD drive to work. It is a Plextor Px-755SA.

Whenever I put a dvd or cd in, and try to mount it, it says "Unable to mount location: no media in drive."

It seems to not even recognize that the drive is there. What do I need to do? What info do I need to post?

Here is my fstab:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=0b41f443-5425-4787-8181-f99172937c0d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=e54ddab0-473e-4275-8d89-fb56e211989e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0






Thanks Everyone!

---

### Post by thewooster on 2009-01-19
Bump.

---

