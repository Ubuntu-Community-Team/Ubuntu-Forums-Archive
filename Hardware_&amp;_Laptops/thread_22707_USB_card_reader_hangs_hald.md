---
title: "USB card reader hangs hald"
date: 2005-03-29
forum: Hardware &amp; Laptops
---

### Post by jeremy on 2005-03-29
My Verbatim USB2 card reader/writer (model UISDMC2W)  causes hald to crash/hang when I plug it in (with or without card inserted). I then have to reinstall hald and reboot for the volume manager to work.

I am using linux-image-2.6.10-5-686-smp, and my thumb drive and USB hard drive both work perfectly when plugged in.

The card reader worked correctly in warty, and I have just tried it on a windows xp setup, works fine.

---

### Post by jeremy on 2005-03-29
Well, I just downloaded and installed todays hal updates, and thought, great, but, no change :-(

---

### Post by jeremy on 2005-04-03
[QUOTE=jeremy]Well, I just downloaded and installed todays hal updates, and thought, great, but, no change :-([/QUOTE]
 Here are the last few lines of dmesg after plugging the device in, can anybody help? 

eth0: no IPv6 routers present
cdrom: dropping to single frame dma
program eject is using a deprecated SCSI ioctl, please convert it to SG_IO
usb 5-5: new high speed USB device using ehci_hcd and address 3
Initializing USB Mass Storage driver...
scsi2 : SCSI emulation for USB Mass Storage devices
usbcore: registered new driver usb-storage
USB Mass Storage support registered.
usb-storage: device found at 3
usb-storage: waiting for device to settle before scanning
  Vendor: USB2.0    Model: CardReader CF RW  Rev: 0.0>
  Type:   Direct-Access                      ANSI SCSI revision: 00
SCSI device sdc: 15744 512-byte hdwr sectors (8 MB)
sdc: Write Protect is off
sdc: Mode Sense: 02 00 00 00
sdc: assuming drive cache: write through
SCSI device sdc: 15744 512-byte hdwr sectors (8 MB)
sdc: Write Protect is off
sdc: Mode Sense: 02 00 00 00
sdc: assuming drive cache: write through
 /dev/scsi/host2/bus0/target0/lun0: p1
Attached scsi removable disk sdc at scsi2, channel 0, id 0, lun 0
  Vendor: USB2.0    Model: CardReader SD RW  Rev: 0.0>
  Type:   Direct-Access                      ANSI SCSI revision: 00
Attached scsi removable disk sdd at scsi2, channel 0, id 0, lun 1
  Vendor: USB2.0    Model: CardReader SM RW  Rev: 0.0>
  Type:   Direct-Access                      ANSI SCSI revision: 00
Attached scsi removable disk sde at scsi2, channel 0, id 0, lun 2
  Vendor: USB2.0    Model: CardReader MS RW  Rev: 0.0>
  Type:   Direct-Access                      ANSI SCSI revision: 00
Attached scsi removable disk sdf at scsi2, channel 0, id 0, lun 3
usb-storage: device scan complete
jeremy@ubuntu1:~$

should I post this at bugzilla?

[edit] I have filed a bug report nº 8585 [/edit]

---

