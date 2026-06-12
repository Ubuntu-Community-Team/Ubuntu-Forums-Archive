---
title: "Usb Pen Drive not automounting"
date: 2005-07-29
forum: Hardware &amp; Laptops
---

### Post by hal8000 on 2005-07-29
For some reason my  USB 2.0 pen drive no longer automounts. Using Hoary5.04 and gnome, I use to plug into an empty USB slot and a drive icon appeared on gnome desktop. This no longer happens.

Output of dmesg:
usb 1-2: new full speed USB device using uhci_hcd and address 4
drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 4 if 0 alt 1 proto 2 vid 0x03F0 pid 0x1004
usb 5-5: USB disconnect, address 3
usb 5-5: new high speed USB device using ehci_hcd and address 5
scsi1 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 5
usb-storage: waiting for device to settle before scanning
  Vendor:           Model: USB DISK Pro      Rev: PMAP
  Type:   Direct-Access                      ANSI SCSI revision: 00
SCSI device sda: 489472 512-byte hdwr sectors (251 MB)
sda: assuming Write Enabled
sda: assuming drive cache: write through
SCSI device sda: 489472 512-byte hdwr sectors (251 MB)
sda: assuming Write Enabled
sda: assuming drive cache: write through
 sda: sda1
Attached scsi removable disk sda at scsi1, channel 0, id 0, lun 0
usb-storage: device scan complete

The device is recognised, I don not have any entries in /etc/fstab (never did for this
drive) so what mechanism does Ubuntu use to autodetect and automount usb
hard drives ?
Thanks in advance for any help.

---

