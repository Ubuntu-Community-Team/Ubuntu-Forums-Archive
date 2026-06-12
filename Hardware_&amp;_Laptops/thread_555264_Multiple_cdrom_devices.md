---
title: "Multiple cdrom devices?"
date: 2007-09-19
forum: Hardware &amp; Laptops
---

### Post by blackaardvark on 2007-09-19
Hi everybody, I'm a bit of an eejit so forgive me if im talking nonsense.  I seem to have far too many cd/dvd drives.  Which ones should I keep and which ones do I discard? I've been editing fstab to the point where it looks like this (I've omitted hd partitions etc..):

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

/dev/scd0      /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1      /media/cdrom1   udf,iso9660 user,noauto     0       0

```

Is this right or do I have these symbolic links wrong? it's causing me all sorts of hassle with cedega and it's also downright irritating.

A bit of help and patience would be amazing and no doubt there's something I'm not telling you but please help?

Thanks

---

### Post by yabbadabbadont on 2007-09-19
If you have two cdrom drives, or two dvd drives, or one of each, then that looks correct.  Assuming that they are both SCSI devices of course.  If they are ATAPI, then they are usually referenced by /dev/hd? devices.  You can check this by looking for your drives in your dmesg output.  Here is an example from my system: ```
/home/daffy $ dmesg | grep -i rom
[   25.166201] ieee1394: Initialized config rom entry `ip1394'
[   25.253374] sata_promise 0000:00:08.0: version 2.01
[   25.253415] sata_promise PATA port found
[   25.319051] scsi0 : sata_promise
[   25.815262] scsi1 : sata_promise
[   26.130108] scsi2 : sata_promise
[   26.338105] usb usb1: configuration #1 chosen from 1 choice
[   26.445955] usb usb2: configuration #1 chosen from 1 choice
[   26.553629] usb usb3: configuration #1 chosen from 1 choice
[   26.894866] usb 1-1: configuration #1 chosen from 1 choice
[   27.346847] usb 1-2: configuration #1 chosen from 1 choice
[b][   27.543346] hdb: CD-RW 48X16, ATAPI CD/DVD-ROM drive
[   28.485453] hdc: PLEXTOR DVDR PX-708A, ATAPI CD/DVD-ROM drive[/b]
[   28.830670] usb usb4: configuration #1 chosen from 1 choice
[   28.877662] hdb: ATAPI 48X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   28.877673] Uniform CD-ROM driver Revision: 3.20
[   28.879032] hdc: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[   29.137274] swsusp: Resume From Partition 8:10
[   29.137610] PM: Resume from disk failed.
[   29.745540] usb 1-1: configuration #1 chosen from 1 choice
[   30.208517] usb 1-2: configuration #1 chosen from 1 choice

```

---

