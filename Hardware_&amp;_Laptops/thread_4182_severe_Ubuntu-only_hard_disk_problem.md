---
title: "severe Ubuntu-only hard disk problem"
date: 2004-11-12
forum: Hardware &amp; Laptops
---

### Post by mrv on 2004-11-12
(or so it seems)

I've the following drive configuration:

/dev/hda: 123.5 GB, 123522416640 bytes (IBM Deskstar 180GXP)
(3 partitions, 2 x reiserfs + swap)
/dev/hdc: DVD-ROM (Acer 16x)
/dev/hdd: 80.0 GB, 80026361856 bytes (Seagate Barracuda 7200.7)
(1 reiserfs partition)

When having this, booting Ubuntu results in several hundreds of error messages of the following type:

Nov 12 17:00:08 localhost kernel: end_request: I/O error, dev hdd, sector 156296255
Nov 12 17:00:08 localhost kernel: hdd: status error: status=0x7f { DriveReady DeviceFault SeekComplete DataRequest CorrectedError Index Error }
Nov 12 17:00:08 localhost kernel: hdd: status error: error=0x7f { DriveStatusError UncorrectableError SectorIdNotFound TrackZeroNotFound AddrMarkNotFound }, LBAsect=150630937100159, high=8978303, low=8355711, sector=156296257
Nov 12 17:00:08 localhost kernel: ide1: reset: success
Nov 12 17:00:08 localhost kernel: hdd: status error: status=0x7f { DriveReady DeviceFault SeekComplete DataRequest CorrectedError Index Error }
Nov 12 17:00:08 localhost kernel: hdd: status error: error=0x7f { DriveStatusError UncorrectableError SectorIdNotFound TrackZeroNotFound AddrMarkNotFound }, LBAsect=150630937100159, high=8978303, low=8355711, sector=156296257
Nov 12 17:00:08 localhost kernel: ide1: reset: success
Nov 12 17:00:08 localhost kernel: hdd: status error: status=0x7f { DriveReady DeviceFault SeekComplete DataRequest CorrectedError Index Error }

Trying to mount /dev/hdd1 results in mount hanging. The point in this is that the drive worked without problems in SUSE 9.1, over which I installed Ubuntu (formatting the /dev/hda1 first). The drive also works perfectly, if I boot from a SUSE installation CD now. And, finally, it works (now) if I disconnect the DVD-ROM drive and set the 80GB hd drive as master.

This is a bit frightening as it's my backup hard disk, and the first thing noticing after installing Ubuntu is that my backup hard drive is failing. Hopefully, this is not severe data-integrity wise, but I wonder if this is a know problem (probably with the Ubuntu's kernel)?

Other specs include:
Clean install Ubuntu 4.10
Athlon XP 1600+
Via KT266A
512MB RAM

---

### Post by scoon on 2004-11-18
Hey there, 

First thing that has been known to work for some (check cdrecord's page for the explanation) is to put your cdrom as a master on its own ide channel.  Move the other drive to be the secondary to your primary on the first channel and see if that helps.


scoon

---

