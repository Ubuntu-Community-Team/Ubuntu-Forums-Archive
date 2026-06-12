---
title: "Ironkey USB non responsive"
date: 2010-11-03
forum: Hardware
---

### Post by dakkar9999 on 2010-11-03
Well, the latest update of my Ironkey secure USB stick just went bad.  Now the key is no longer detected.  I've contacted their tech support and they'll just send me a new one, but if possible I'd like to get my files back.  Anybody can interpret this log file?  If you have any suggestion it would be greatly appreciated.



Nov  3 09:35:23 ontherun kernel: [ 5146.102706] scsi 49:0:0:0: CD-ROM            IronKey  CD-ROM           2.08 PQ: 0 ANSI: 0
Nov  3 09:35:23 ontherun kernel: [ 5146.104058] scsi 49:0:0:1: Direct-Access     IronKey  Secure Drive     2.08 PQ: 0 ANSI: 0
Nov  3 09:35:24 ontherun kernel: [ 5146.958902] VFS: busy inodes on changed media or resized disk sr0
Nov  3 09:35:26 ontherun kernel: [ 5148.957622] VFS: busy inodes on changed media or resized disk sr0
Nov  3 09:35:28 ontherun kernel: [ 5150.957746] VFS: busy inodes on changed media or resized disk sr0
Nov  3 09:35:30 ontherun kernel: [ 5152.959221] VFS: busy inodes on changed media or resized disk sr0
Nov  3 09:35:31 ontherun kernel: [ 5154.287699] usb 2-5: USB disconnect, address 54
Nov  3 09:35:31 ontherun kernel: [ 5154.287878] sr1: scsi3-mmc drive: 372x/94x caddy
Nov  3 09:35:31 ontherun kernel: [ 5154.288117] sr 49:0:0:0: Attached scsi generic sg3 type 5
Nov  3 09:35:31 ontherun kernel: [ 5154.288279] sd 49:0:0:1: Attached scsi generic sg4 type 0
Nov  3 09:35:31 ontherun kernel: [ 5154.296565] sd 49:0:0:1: [sdc] READ CAPACITY failed
Nov  3 09:35:31 ontherun kernel: [ 5154.296569] sd 49:0:0:1: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Nov  3 09:35:31 ontherun kernel: [ 5154.296573] sd 49:0:0:1: [sdc] Sense not available.
Nov  3 09:35:31 ontherun kernel: [ 5154.296586] sd 49:0:0:1: [sdc] Write Protect is off
Nov  3 09:35:31 ontherun kernel: [ 5154.297837] sd 49:0:0:1: [sdc] READ CAPACITY failed
Nov  3 09:35:31 ontherun kernel: [ 5154.297840] sd 49:0:0:1: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Nov  3 09:35:31 ontherun kernel: [ 5154.297844] sd 49:0:0:1: [sdc] Sense not available.
Nov  3 09:35:31 ontherun kernel: [ 5154.297860] sd 49:0:0:1: [sdc] Attached SCSI removable disk
Nov  3 09:35:31 ontherun kernel: [ 5154.682789] usb 2-5: new high speed USB device using ehci_hcd and address 55
Nov  3 09:35:31 ontherun kernel: [ 5154.852565] scsi50 : usb-storage 2-5:1.0
Nov  3 09:35:32 ontherun kernel: [ 5154.957936] VFS: busy inodes on changed media or resized disk sr0
Nov  3 09:35:34 ontherun kernel: [ 5156.957976] VFS: busy inodes on changed media or resized disk sr0
Nov  3 09:35:35 ontherun kernel: [ 5158.048806] scsi 50:0:0:0: CD-ROM            IronKey  CD-ROM           2.08 PQ: 0 ANSI: 0
Nov  3 09:35:35 ontherun kernel: [ 5158.050293] scsi 50:0:0:1: Direct-Access     IronKey  Secure Drive     2.08 PQ: 0 ANSI: 0
Nov  3 09:35:36 ontherun kernel: [ 5158.958394] VFS: busy inodes on changed media or resized disk sr0
Nov  3 09:35:38 ontherun kernel: [ 5160.958145] VFS: busy inodes on changed media or resized disk sr0

---

