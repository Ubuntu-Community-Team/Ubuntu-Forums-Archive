---
title: "USB External CD Enclosure not working"
date: 2010-05-16
forum: Hardware
---

### Post by jawahar on 2010-05-16
I have an old USB 1.1 enclosure for IDE CD drives. It works with windows 7 but not with Ubuntu 10.04 Lucid Lynx 32bit. 

At times it will, detect the drive but then drop off without ever actually being able to browse files on the CD. Any help will be much appreciated!

dmesg outputs are as follows:

[  695.345170] usb 1-1: new high speed USB device using ehci_hcd and address 12
[  695.478881] usb 1-1: configuration #1 chosen from 1 choice
[  695.480470] scsi10 : SCSI emulation for USB Mass Storage devices
[  695.481261] usb-storage: device found at 12
[  695.481268] usb-storage: waiting for device to settle before scanning


[  706.671306] sr 10:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  706.671328] sr 10:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  706.671349] sr 10:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  706.671375] sr 10:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[  706.671418] end_request: I/O error, dev sr0, sector 0

---

