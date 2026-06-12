---
title: "Dell removable CD-ROM"
date: 2006-07-04
forum: Hardware &amp; Laptops
---

### Post by TMC on 2006-07-04
Under XP, I could hot swap the CD-ROM and battery on my Dell Latitude laptop without problem but with Ubuntu, if I want to use my CD-ROM, I need to reboot.  Is there any way I can get Ubuntu to recognise my CD-ROM when I plug it in without having to reboot every time?  I've gone through the manpage for mount and pmount and tried various options, but can't sort this out.  The CD-ROM is listed in my /etc/fstab file as

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

I'm assuming the noauto option refers to auto-running any CD that's inserted.

I don't mind having to do this manually every time I insert the drive - although automatic would be nice  :) - after all, having to type a command is still quicker than rebooting!

Many thanks in advance,

David Shaw

---

### Post by linedpaper on 2006-11-15
Did you ever find a solution for this?  I'm having the same problem.

---

### Post by linedpaper on 2007-01-03
there has got to be some sort of solution to this problem...anyone!

---

