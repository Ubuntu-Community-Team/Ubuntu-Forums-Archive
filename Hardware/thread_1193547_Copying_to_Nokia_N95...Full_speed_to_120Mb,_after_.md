---
title: "Copying to Nokia N95...Full speed to 120Mb, after it 100KB..."
date: 2009-06-21
forum: Hardware
---

### Post by starfly on 2009-06-21
Hello

Again my Usb System is Sucking, and iam very angry...its always the same...Usb Slots are much to slow in Ubuntu...


After Pushing my sticks to 5MB/s by setting them to async, i havent got a chance with the Memory of my Nokia N95 8GB!

Its copying very fast to 120 MB, after it i get 120Kb/s, and cant unmount it because the 1,5GB are still Pending after 4hours !

Whats the Problem ?!

---

### Post by starfly on 2009-06-21
The Output of dmesg

[  127.236115] usb 6-1: new full speed USB device using uhci_hcd and address 2
[  127.402485] usb 6-1: configuration #1 chosen from 1 choice
[  127.468078] Initializing USB Mass Storage driver...
[  127.468351] scsi4 : SCSI emulation for USB Mass Storage devices
[  127.468515] usb-storage: device found at 2
[  127.468520] usb-storage: waiting for device to settle before scanning
[  127.468525] usbcore: registered new interface driver usb-storage
[  127.468532] USB Mass Storage support registered.
[  132.471065] usb-storage: device scan complete
[  132.473948] scsi 4:0:0:0: Direct-Access     Nokia    N95 8GB          1.0  PQ: 0 ANSI: 0
[  132.474636] sd 4:0:0:0: Attached scsi generic sg2 type 0
[  132.494927] sd 4:0:0:0: [sdb] 15857664 512-byte hardware sectors: (8.11 GB/7.56 GiB)
[  132.497914] sd 4:0:0:0: [sdb] Write Protect is off
[  132.497924] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  132.497929] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  132.518917] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  132.518929]  sdb: sdb1
[  132.622639] sd 4:0:0:0: [sdb] Attached SCSI removable disk
root@LinuxOS:~#

---

### Post by starfly on 2009-06-22
no one

---

