---
title: "Pesky Cd Rom Drive"
date: 2008-07-07
forum: Hardware
---

### Post by NNNNNNNNNN1515 on 2008-07-07
I'm running ubuntu on my computer. I have four drives: one hard drive, a floppy drive, and two cd drives. One is a cd/dvd rom drive. The other is a cd-RW drive. Whenever I try to access a cd in either drive, file browser displayes the message **"Unable to mount location - no media in the drive"**. Problem is, there IS media in the drive. I ought know. I put it there! :mad:

I tried searching this forum for similar posts, and I found a few, but since I'm new to linux, they weren't much help. In all of them, however, I noticed that problems were diagnosed with information from fstab, and after reading up on the subject, I figured out how to read it in terminal. :) 

So here is what my fstab says:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a5716e71-cff2-4a12-be80-0ae76a3d2e49 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=33da9863-d8de-4021-a18c-c6ad9fe267b6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


I'm guessing scd0 and scd1 are my cd drives. fd0 is clearly my floppy drive. By process of elimination, I deduce sda5 to be my hard drive. Is this correct? 

That's pretty much all I understand so far. Does anyone see anything wrong with this fstab report that could be preventing me from mounting my cd drives? Or has anyone had this error before? What should I do to get my cd drives to work? And don't spare on the lengthy technical discussions! I love learning new things about linux. :)

---

### Post by NNNNNNNNNN1515 on 2008-07-08
And incase you were confused by my nickname, I'm not some spam bot.

Anybody there? This post's getting no views!

---

