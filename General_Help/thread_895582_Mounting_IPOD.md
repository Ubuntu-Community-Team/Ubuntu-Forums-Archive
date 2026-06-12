---
title: "Mounting IPOD"
date: 2008-08-20
forum: General Help
---

### Post by sprucio on 2008-08-20
I'm currently trying to mount an IPOD on my ubuntu box (in VMWARE fusion) and I'm not having much success. My other USB devices work perfectly at this time.


Here's a snippet of dmesg right after I plug it in:
```
[ 1440.830933] usb 2-1: new high speed USB device using ehci_hcd and address 6
[ 1441.002636] usb 2-1: configuration #1 chosen from 2 choices
[ 1441.014236] scsi7 : SCSI emulation for USB Mass Storage devices
[ 1441.015045] usb-storage: device found at 6
[ 1441.015084] usb-storage: waiting for device to settle before scanning
[ 1446.014053] usb-storage: device scan complete
[ 1446.020066] scsi 7:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 1446.030941] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[ 1446.031111] sd 7:0:0:0: Attached scsi generic sg2 type 0
```


When I look at /etc/mtab, I see no references to my IPOD whatsoever.

Any help is greatly appreciated.

---

