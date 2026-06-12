---
title: "USB Device does not appear in /dev/, appears in /proc/partitions with 0 blocks..."
date: 2008-10-12
forum: General Help
---

### Post by gausie on 2008-10-12
Hi all!

I've plugged in my iRiver H10 in usb storage mode and I see the following in dmesg

> [10232.761922] usb 7-4: new high speed USB device using ehci_hcd and address 2
[10232.800947] usb 7-4: configuration #1 chosen from 1 choice
[10233.175907] usbcore: registered new interface driver libusual
[10233.252047] Initializing USB Mass Storage driver...
[10233.252267] scsi5 : SCSI emulation for USB Mass Storage devices
[10233.252422] usbcore: registered new interface driver usb-storage
[10233.252425] USB Mass Storage support registered.
[10233.252713] usb-storage: device found at 2
[10233.252715] usb-storage: waiting for device to settle before scanning
[10234.131996] usb-storage: device scan complete
[10234.132643] scsi 5:0:0:0: Direct-Access     iriver   iriver H10            PQ: 0 ANSI: 0
[10234.134581] sd 5:0:0:0: [sdb] Sector size 0 reported, assuming 512.
[10234.134590] sd 5:0:0:0: [sdb] 1 512-byte hardware sectors (0 MB)
[10234.135360] sd 5:0:0:0: [sdb] Write Protect is off
[10234.135367] sd 5:0:0:0: [sdb] Mode Sense: 45 00 00 00
[10234.135372] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[10234.194197] sd 5:0:0:0: [sdb] Sector size 0 reported, assuming 512.
[10234.194208] sd 5:0:0:0: [sdb] 1 512-byte hardware sectors (0 MB)
[10234.195198] sd 5:0:0:0: [sdb] Write Protect is off
[10234.195205] sd 5:0:0:0: [sdb] Mode Sense: 45 00 00 00
[10234.195209] sd 5:0:0:0: [sdb] Assuming drive cache: write through


But no sdb appears in /dev/

When I run cat /proc/partitions I get the following

>    8     0  244198584 sda
   8     1  238179658 sda1
   8     2          1 sda2
   8     5    6016311 sda5
   8    16          0 sdb


It looks bad to me, and I realise that it may be that the data has gone - but is there any way to fix the device?

Gausie

---

