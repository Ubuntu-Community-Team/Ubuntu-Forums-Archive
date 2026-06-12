---
title: "Problems with external floppy drive"
date: 2005-01-12
forum: Hardware &amp; Laptops
---

### Post by arkz on 2005-01-12
Hi!
I have an external floppy drive which connects to the USB port. The problem is that I can't get it to mount properly. When i insert a disc into the drive it works for a while and then "sda" shows up on the desktop, a few seconds later "sdb" shows up, then "sdc", "sdd" and so on. The only way to make it stop mounting more and more drives is to eject the floppy.
I tried add a line to fstab but without any result.

---

### Post by benjou on 2006-02-27
got the very same problem.

It will try to mount from sdb to sdi

will eventually get mounted but takes a LOT of time...

---

### Post by josh2112 on 2006-04-09
Anyone found a solution to this yet?  Kubuntu Breezy Badger on my Dell Latitude D510 does the same thing when I plug in the external floppy drive into the bay.  Here is the relevant output from dmesg:

> 
[4294682.705000]   Vendor: NEC       Model: USB UF000x        Rev: 1.50
[4294682.705000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294683.410000] Attached scsi removable disk sdb at scsi2, channel 0, id 0, lun 0
[4294683.473000]   Vendor: NEC       Model: USB UF000x        Rev: 1.50
[4294683.473000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294683.858000] Attached scsi removable disk sdc at scsi2, channel 0, id 0, lun 1
[4294683.922000]   Vendor: NEC       Model: USB UF000x        Rev: 1.50
[4294683.922000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294684.307000] Attached scsi removable disk sdd at scsi2, channel 0, id 0, lun 2
[4294684.369000]   Vendor: NEC       Model: USB UF000x        Rev: 1.50
[4294684.369000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294684.754000] Attached scsi removable disk sde at scsi2, channel 0, id 0, lun 3
[4294684.817000]   Vendor: NEC       Model: USB UF000x        Rev: 1.50
[4294684.817000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294685.628000] Attached scsi removable disk sdf at scsi2, channel 0, id 0, lun 4
[4294685.649000]   Vendor: NEC       Model: USB UF000x        Rev: 1.50
[4294685.649000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294686.034000] Attached scsi removable disk sdg at scsi2, channel 0, id 0, lun 5
[4294686.097000]   Vendor: NEC       Model: USB UF000x        Rev: 1.50
[4294686.097000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294686.482000] Attached scsi removable disk sdh at scsi2, channel 0, id 0, lun 6
[4294686.548000]   Vendor: NEC       Model: USB UF000x        Rev: 1.50
[4294686.548000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294686.930000] Attached scsi removable disk sdi at scsi2, channel 0, id 0, lun 7
[4294686.931000] usb-storage: device scan complete


This causes 8 "External Floppy Drive" devices to show up under system:/media.  The last one, /dev/sdi, does eventually get mounted as /media/sdi and is usable, but why all this mess?

Josh

---

### Post by tksownz on 2006-04-25
Hey josh2112, I am having the same problem, however I have no attached external floppy drive, if anyone could find a solution to this it was help a great deal.

---

