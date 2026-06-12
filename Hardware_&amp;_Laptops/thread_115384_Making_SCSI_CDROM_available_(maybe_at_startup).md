---
title: "Making SCSI CDROM available (maybe at startup)?"
date: 2006-01-10
forum: Hardware &amp; Laptops
---

### Post by Franko30 on 2006-01-10
Hi,

I'm using an older Yamaha CD-Writer on an Adaptec 2940 SCSI adapter.

After installing Ubuntu I couldn't find the CDROM anymore.

The module aic7xxx is loaded. The directory **/proc/scsi/aic7xxx** is there and **cat /proc/scsi/aic7xxx/0** shows me the SCSI adapter.
But I saw no entries like scd0 etc. in **/dev** so mounting the CDROM manually was beyond my means.

This thread

[http://www.ubuntuforums.org/showthread.php?t=59915](http://www.ubuntuforums.org/showthread.php?t=59915)

led me to two ways of making the drive available manually:

[list]**sudo scsiadd** -> using this to remove/then add my drive again made the automount jump in.[/list]
[list]Using **sudo modprobe -r aic7xxx** and then **sudo modprobe aic7xxx** did the same thing[/list]

Apparently the SCSI bus needs to be re-scanned to make the CDROM available. That's why making the CDROM available in **fstab** as **/dev/scd0** doesn't work...


My question now is:

How do I make the SCSI CDROM avaible automatically during/at startup?

Thanks in advance. :-)

Franko30

---

