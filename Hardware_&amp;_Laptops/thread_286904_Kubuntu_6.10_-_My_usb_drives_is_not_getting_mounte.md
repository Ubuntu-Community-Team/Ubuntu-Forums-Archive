---
title: "Kubuntu 6.10 - My usb drives is not getting mounted!"
date: 2006-10-28
forum: Hardware &amp; Laptops
---

### Post by daller on 2006-10-28
Hi There,

I have a problem after upgrading to Kubuntu 6.10 final.

If I plug in an external drive, I'm asked what the computer should do! (I choose "Open in a new window" - But nothing happens.)

According to "df" the drive is not mounted!

Dmesg:

```
[17183782.116000] usb 4-1: new high speed USB device using ehci_hcd and address 11
[17183782.248000] usb 4-1: configuration #1 chosen from 1 choice
[17183782.248000] scsi7 : SCSI emulation for USB Mass Storage devices
[17183782.248000] usb-storage: device found at 11
[17183782.248000] usb-storage: waiting for device to settle before scanning
[17183787.248000] usb-storage: device scan complete
[17183787.452000]   Vendor: Maxtor    Model: OneTouch          Rev: 0200
[17183787.452000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17183787.456000] SCSI device sda: 490232832 512-byte hdwr sectors (250999 MB)
[17183787.660000] sda: Write Protect is off
[17183787.660000] sda: Mode Sense: 1c 00 00 00
[17183787.660000] sda: assuming drive cache: write through
[17183787.664000] SCSI device sda: 490232832 512-byte hdwr sectors (250999 MB)
[17183787.868000] sda: Write Protect is off
[17183787.868000] sda: Mode Sense: 1c 00 00 00
[17183787.868000] sda: assuming drive cache: write through
[17183787.868000]  sda: sda1
[17183787.900000] sd 7:0:0:0: Attached scsi disk sda
[17183787.900000] sd 7:0:0:0: Attached scsi generic sg0 type 0

```

The same thing happens with all my drives (Onetouch, Onetouch II, Onetouch III and "Argosy Mobile Video HDD")

Help!

---

### Post by John.Michael.Kane on 2006-10-28
Manually add it

[http://ubuntuforums.org/showthread.php?t=283131&highlight=mounting+usb+drives](http://ubuntuforums.org/showthread.php?t=283131&highlight=mounting+usb+drives)

---

