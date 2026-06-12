---
title: "New hard disk"
date: 2007-12-11
forum: Hardware &amp; Laptops
---

### Post by pan69 on 2007-12-11
Hi guys,

I just got my new hard drive and now I want this drive to serve as my home folder. I've been reading how to do this from posts on this forum. However, in order to complete this transition I need to edit my fstab. All the examples I see are pretty straight forward but my fstab has instead of 'normal' drive id's like hd1, hda, sda1 etc. it lists UUID's like this:
```

proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=2996efb2-6f4d-4966-9ce9-713e3d5a23cb /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=A6DC1FD2DC1F9C1D /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=2fe9935b-84b0-4b75-926e-947e0c1a198f none            swap    sw              0       0

```

As you can see, it list /dev/sda5 as 2fe9935b-84b0-4b75-926e-947e0c1a198f. Now, my new drive is indentified by GParted as sdb1. Now, what would be the best way to add it to fstab mounted as /home?

Thanks!

---

### Post by c0mp13371331337 on 2007-12-12
Those UUIDs are replaceable with the path commented out above each one.  So for example, my fstab looks like this:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=18613405-b87b-479a-b8d5-800bbc8e4984 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=9420325f-8c79-4857-9dd7-1f70329274a5 /home     ext3    defaults        0       2
# /dev/sdb1
UUID=108c77b4-9bfd-4d61-86e1-b1a3a4d4fc3b /home/me/Videos     ext3    defaults        0       2
# /dev/sda3
UUID=1316aabc-23cb-4915-bdc8-a722513d24d4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

It could also look like this and would mean the exact same thing:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1   /               ext3    defaults,errors=remount-ro 0       1
/dev/sda2   /home     ext3    defaults        0       2
/dev/sdb1   /home/me/Videos     ext3    defaults        0       2
/dev/sda3   none            swap    sw              0       0
/dev/scd0   /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1   /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0      /media/floppy0  auto    rw,user,noauto,exec 0       0
```

So for your new drive, add a new line to your fstab (uncommented) beginning with '/dev/sdb1     /mounted/directory/of/newdisk'   then whatever options you need after that.

---

### Post by pan69 on 2007-12-12
Thanks for that! It all works now :)

---

### Post by c0mp13371331337 on 2007-12-13
No problem, glad to help!  That's a good call too, putting your /home directory on a separate HD.  I've helped a few friends install Ubuntu on their systems, and I always advocate the use of at least a separate partition for /home, if not a different HD altogether.  

I can't tell you how many times I've played with the wrong file as root and not noticed the effects til the next reboot (or at least restarting the xserver) long after I would remember what changes were made.  Sometimes it's fixable, but in most cases, with /home on a separate partition, it's much easier to just re-install Ubuntu.  Then your worst headache is reinstalling your programs, rather than reinstalling AND reconfiguring.

---

