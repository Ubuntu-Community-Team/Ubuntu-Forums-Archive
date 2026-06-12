---
title: "fsck died with exit status 8"
date: 2009-01-21
forum: Installation &amp; Upgrades
---

### Post by love fingers on 2009-01-21
Hi there,

Hoping someone can help me out <fingers crossed> and that I'm in the right area...

I have installed ubuntu 8.10 (upgraded from 8.04) I don't know what I've done but now I randomly get this exit status 8 error when I boot up.
Normally, I boot up, get the error, press ctrl+d, continue booting, then reboot once I reach the desktop (this isn't the right desktop and the home folder doesn't have any of my stuff in it) and most of the time it'll boot up without error and I'll get my correct /home folder and all will be ok.

My SATA drive is partitioned with a / (sdc1 54 gig) and /home (sdc2 590gig) and some unpartitioned space...

I have my swap partition on another drive.

My fstab file is messy but I don't really know how it works and suspect the problem lies in there somewhere.

So odd that it boots up sometimes without a hitch...

My fstab file (with the wrong /home folder)
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=45cec373-33b8-411f-91e9-a1261bb37026 /               ext3    relatime,errors=remount-ro 0       1
/dev/sda2 /home	ext3    relatime        0       2
# /dev/sdc2
UUID=31ea3386-a929-43c4-b87f-62c0950710c2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

Any advice or solutions will be muchly appreciated.
Thanks.

---

### Post by love fingers on 2009-01-21
OK, head slap time...
I took a punt and tidied up the fs tab file and used the UUID details from the cmd "blkid" to look like this

proc            /proc           proc    defaults        0       0
UUID=45cec373-33b8-411f-91e9-a1261bb37026 /             ext3    relatime,errors=remount-ro 	0       1
UUID=3b5b214a-1a59-4826-b4c4-f1e89adf2e6f /home		ext3    nodev,nosuid,relatime        	0       2
UUID=31ea3386-a929-43c4-b87f-62c0950710c2 none          swap    sw              		0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

...And it's working like a charm.

---

