---
title: "mounting ufs over ide to usb converter"
date: 2009-01-22
forum: Hardware
---

### Post by Ofloo on 2009-01-22
Hi, i was wondering how to mount an ufs system i've tried, ..

mount -r -t ufs -o ufstype=ufs2 /dev/sdb1 /mnt/ufs

which didn't work, linux was not able to find the partition well it was but it's kindoff strange, .. it shows in /dev it doesn't show in fdisk -l it shows in my computer, but the usb converter doesn't show in lsusb, .. to me that's really strange.. because how can something not show in lsusb but still tries to mount in my computer it even shows the disk as USB-disk, but i'm not able to browse anything, when i do try it says it's not able to mount it.

and it shows in dmesg ..?

```
[421138.304595] usb 7-2: USB disconnect, address 35
[421144.124113] usb 7-2: new high speed USB device using ehci_hcd and address 36
[421144.258924] usb 7-2: configuration #1 chosen from 1 choice
[421144.259763] scsi23 : SCSI emulation for USB Mass Storage devices
[421144.261305] usb-storage: device found at 36
[421144.261313] usb-storage: waiting for device to settle before scanning
[421149.260434] usb-storage: device scan complete
[421149.261380] scsi 23:0:0:0: Direct-Access     USB TO I DE/SATA Device   0041 PQ: 0 ANSI: 0
[421149.265349] sd 23:0:0:0: [sdb] Attached SCSI disk
[421149.266286] sd 23:0:0:0: Attached scsi generic sg2 type 0
```

---

