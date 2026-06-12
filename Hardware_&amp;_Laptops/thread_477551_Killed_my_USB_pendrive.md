---
title: "Killed my USB pendrive"
date: 2007-06-18
forum: Hardware &amp; Laptops
---

### Post by [h2o] on 2007-06-18
I was going to put the Live CD on a USB stick for installation on a machine that has no CD-drive. But it seems like I managed to bork it quite heavily in the process so right now it is not being mounted in neither Ubuntu or Windows XP.

dmesg says this when I plug it in:
```

usb 1-1: new full speed USB device using ohci_hcd and address 5
usb 1-1: configuration #1 chosen from 1 choice
scsi2 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 5
usb-storage: waiting for device to settle before scanning
usb-storage: device scan complete
scsi 2:0:0:0: Direct-Access     Generic  USB Flash Drive  1.04 PQ: 0 ANSI: 2
sd 2:0:0:0: Attached scsi removable disk sda
sd 2:0:0:0: Attached scsi generic sg0 type 0

```

But if I try to run fdisk on /dev/sda I get a "Could not open /dev/sda" error, and if I try to mount it I get a "no medium found" error.

Any ideas?

---

