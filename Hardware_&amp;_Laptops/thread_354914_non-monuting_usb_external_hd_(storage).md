---
title: "non-monuting usb external hd (storage)"
date: 2007-02-06
forum: Hardware &amp; Laptops
---

### Post by vierranet on 2007-02-06
any idea on how an external usb hd (wd 40gig) was working under dapper with no problems, then after applying updates, poof, it its not mounting.

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

no /dev/hdb??????

any help will be appreciated......

---

### Post by allwin on 2007-02-06
> **vierranet said:**
> any idea on how an external usb hd (wd 40gig) was working under dapper with no problems, then after applying updates, poof, it its not mounting.

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

no /dev/hdb??????

any help will be appreciated......

I've run the gamut of problems here connecting external hd's.  I assume you have a wd40 in an enclosure?  If so, the jumpers on the back of the drive need to be set correctly.  On WD drives, I found out that the MASTER jumper really means "Master plus slave" and this confuses things.  NO jumpers at all=MASTER.  However, you do need to check CAREFULLY the wording on the drive.  It's only WD that has this strange scheme, btw.

If you do not have an HD in a can, then...never mind!  Although I will put my two cents in to say I have more trouble with USB 2.0 than with 1394 if that's available.  Sometimes I have to have it plugged in while booting.

Check your system log for errors referring to the device.  Might be a clue there, too.

---

