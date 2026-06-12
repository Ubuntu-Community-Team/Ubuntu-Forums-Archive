---
title: "Mounting an external hard drive"
date: 2009-04-05
forum: Hardware
---

### Post by jdelasalas on 2009-04-05
I have a 2.5" enclosure that's powered off the USB ports.  I'm unable to get it to mount, however I can get it to appear in the lsusb:

Bus 002 Device 005: ID 04fc:0c25 Sunplus Technology Co., Ltd 

Occasionally I can get it to appear, but it just quits after a few moments.  Any ideas?

---

### Post by zigga15 on 2009-04-05
> **jdelasalas said:**
> I have a 2.5" enclosure that's powered off the USB ports.  I'm unable to get it to mount, however I can get it to appear in the lsusb:

Bus 002 Device 005: ID 04fc:0c25 Sunplus Technology Co., Ltd 

Occasionally I can get it to appear, but it just quits after a few moments.  Any ideas?

ls /dev/disk/by-label
(scope out one that looks like sunplus or something)
mount sunplus

---

### Post by jdelasalas on 2009-04-05
scsi 4:0:0:0: Direct-Access     ST916082 1AS                   PQ: 0 ANSI: 2
sd 4:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
sd 4:0:0:0: [sdb] Write Protect is off
sd 4:0:0:0: [sdb] Mode Sense: 38 00 00 00
sd 4:0:0:0: [sdb] Assuming drive cache: write through
sd 4:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
sd 4:0:0:0: [sdb] Write Protect is off
sd 4:0:0:0: [sdb] Mode Sense: 38 00 00 00
sd 4:0:0:0: [sdb] Assuming drive cache: write through
 sdb: sdb1
sd 4:0:0:0: [sdb] Attached SCSI disk
sd 4:0:0:0: Attached scsi generic sg2 type 0
usb-storage: device scan complete
usb 2-1: reset high speed USB device using ehci_hcd and address 2
kjournald starting.  Commit interval 5 seconds
EXT3 FS on sdb1, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
usb 2-1: reset high speed USB device using ehci_hcd and address 2
usb 2-1: reset high speed USB device using ehci_hcd and address 2
usb 2-1: reset high speed USB device using ehci_hcd and address 2


Then when I try to write, I usually get an error saying the destination drive doesn't exist.

---

