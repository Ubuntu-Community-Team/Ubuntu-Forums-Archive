---
title: "usb drive can't be found"
date: 2009-06-02
forum: Hardware
---

### Post by yawnmoth on 2009-06-02
When I plug in a hard drive via a USB<->ATA adapter, I get the following:
```
[  406.676042] usb 1-5: new high speed USB device using ehci_hcd and address 5
[  406.835870] usb 1-5: configuration #1 chosen from 1 choice
[  406.838514] scsi8 : SCSI emulation for USB Mass Storage devices
[  406.869524] usb-storage: device found at 5
[  406.869529] usb-storage: waiting for device to settle before scanning
[  411.868271] usb-storage: device scan complete
[  411.869100] scsi 8:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2 CCS
[  411.872683] sd 8:0:0:0: [sdc] Attached SCSI disk
[  411.872791] sd 8:0:0:0: Attached scsi generic sg3 type 0
```
The drive, however, is not mentioned in the System menu.  Not only is it not mentioned there but I don't even see it when doing "sudo fdisk -l" or in GParted.

Any ideas?  There's no more dmesg output after that...

---

