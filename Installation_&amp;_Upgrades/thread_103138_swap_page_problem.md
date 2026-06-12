---
title: "swap page problem"
date: 2005-12-13
forum: Installation &amp; Upgrades
---

### Post by HosBosCos on 2005-12-13
first of all, hello to everyone
i just installed ubuntu to my second partition but while installing i could not define any swap pages to use as memory so now my system works only with real memory.
i tried to find a way to do it but i could not. i tried the command swapon but could not figure out cos' i'm a real newbie.
i'd really appreciate help for that problem thanx in advance:)

---

### Post by taurus on 2005-12-13
Did you create a swap space, a partition, when you installed it?  If you haven't, you can either use gparted to resize your current partition to make room for swap space or you can create a swap file for it.

What does your /etc/fstab say anyway?

more /etc/fstab

---

### Post by psusi on 2005-12-13
By default, the installer creates a swap partition for you.  What makes you think it did not do this?

---

### Post by HosBosCos on 2005-12-13
the command you said says
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc1       /media/hdc1     vfat    defaults        0       0
/dev/hdc2       /media/hdc2     ntfs    defaults        0       0
/dev/sda1       /media/sda1     vfat    defaults        0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

i did an expert install cos' i did not want to lose windows.
and in system monitor it shows swap space as 0.
i'm a newbie so really appreciate your help :D

---

### Post by HosBosCos on 2005-12-13
while installing it said you did not choose a swap partition but i could not figure out how to do that so there is no swap partition now i think.
please help me because my computer is beginning to get slower and slower. i have 256mb ram and with no swap space it is really being very slow.

---

### Post by psusi on 2005-12-13
Well, you can boot off the livecd and use gparted to resize some partitions and make a swap partition, then add it to your fstab.  

Or you can use a swap file.  Start with man swapon.  IIRC, you can run swapon and give it a file to use.

---

