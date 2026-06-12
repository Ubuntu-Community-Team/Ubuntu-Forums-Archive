---
title: "Ubuntu + Hard Drive sounds"
date: 2006-02-20
forum: Hardware &amp; Laptops
---

### Post by straylight on 2006-02-20
Ok heres the deal, i dual boot win xp pro and breezy on a dell inspiron 9300.  When i'm booted into Ubuntu i notice a lot more disk activity (HD sounds, no not the bad grinding sounds...just little read ticks).  I have checked the system monitor and it doesnt show anything out of the ordinary so i'm wondering what it could be?  Also when i shutdown from ubuntu everything comes up [ok] but the sound the hard drive makes reminds me of the sound heard when holding the power button in to force a shutdown...its like the drive doesnt even spin down at all.

I dont notice any of these issues when booted into windows so i'm wondering if i need to tweak the hard drive settings w/ hdparam?  

Anyone have ideas?

Thanks,
Straylight

---

### Post by Lord Illidan on 2006-02-20
Is DMA enabled? Check it with ```
sudo hdparm /dev/hdd
``` (or whatever your drive name is)

Also, give us your /etc/fstab

---

### Post by straylight on 2006-02-20
here are the results of "hdparm /dev/sda5"

```
/dev/sda5:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 7296/255/63, sectors = 42700707, start = 65545263
```

and here is my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda6       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```

Let me know if anything else is needed.

-straylight

---

### Post by straylight on 2006-02-22
any ideas??

---

### Post by darrenrxm on 2006-02-22
l

---

### Post by Offthedeepend on 2006-04-08
I've noticed the same on my i9300 (hard drive ticks and odd shutdown noise), but I'm not at all techy and very new to linux, so interested if anyone has ideas about this.

---

### Post by 1.21 on 2006-05-03
I would also like to find out as I am about to install this distro on my i9300 as well

---

### Post by paritybit on 2006-05-03
[http://www.ubuntuforums.org/showthread.php?t=79055](http://www.ubuntuforums.org/showthread.php?t=79055)
[http://www.ubuntuforums.org/showpost.php?p=947815&postcount=55](http://www.ubuntuforums.org/showpost.php?p=947815&postcount=55)
Search is your friend. This seems to be going around... the ticking noise that is..

---

