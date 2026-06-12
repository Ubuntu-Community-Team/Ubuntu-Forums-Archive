---
title: "External usb disk not mounted/recognized"
date: 2009-05-28
forum: Hardware
---

### Post by henriquemaia on 2009-05-28
I'm having trouble in accessing an external usb disk I have. Last week the disk was working nicely, I plugged it in and it was automatically mounted. However, some days ago, I plug it in and the disk was not mounted. I tried to mount it manually, but it's like the disk isn't there. If I try a 

fdisk -l

I only get the information on the internal drives. 

But dmesg shows the kernel recognizes the external drive, at least it seems to have:

```
[44995.372418] usb 1-3: new high speed USB device using ehci_hcd and address 6
[44995.508356] usb 1-3: configuration #1 chosen from 1 choice
[44995.509565] scsi4 : SCSI emulation for USB Mass Storage devices
[44995.510030] usb-storage: device found at 6
[44995.510034] usb-storage: waiting for device to settle before scanning
[45000.508403] usb-storage: device scan complete
[45000.509201] scsi 4:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2 CCS
[45000.519064] sd 4:0:0:0: [sdc] Attached SCSI disk
[45000.519181] sd 4:0:0:0: Attached scsi generic sg3 type 0

```Does anyone have an idea on how to solve this?

---

### Post by henriquemaia on 2009-05-28
Bump!

---

