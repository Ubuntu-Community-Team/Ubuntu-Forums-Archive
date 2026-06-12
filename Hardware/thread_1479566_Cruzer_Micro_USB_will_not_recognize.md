---
title: "Cruzer Micro USB will not recognize"
date: 2010-05-10
forum: Hardware
---

### Post by kcghost on 2010-05-10
Im using an Asus UX50V laptop Ubuntu Karmic. Some USB drives recognize and mount automatically but others do not.

One im testing now is a Cruzer Micro 4GB. The end of dmesg is:

[ 1129.371364] usb 2-2: new high speed USB device using ehci_hcd and address 5
[ 1129.561612] usb 2-2: configuration #1 chosen from 1 choice
[ 1129.569047] scsi6 : SCSI emulation for USB Mass Storage devices
[ 1129.569193] usb-storage: device found at 5
[ 1129.569196] usb-storage: waiting for device to settle before scanning
[ 1134.564227] usb-storage: device scan complete
[ 1134.570357] scsi 6:0:0:0: Direct-Access     SanDisk  Cruzer           7.01 PQ: 0 ANSI: 0 CCS
[ 1134.570993] scsi 6:0:0:1: CD-ROM            SanDisk  Cruzer           7.01 PQ: 0 ANSI: 0
[ 1134.571709] sd 6:0:0:0: Attached scsi generic sg2 type 0
[ 1134.584635] sd 6:0:0:0: [sdb] 7856127 512-byte logical blocks: (4.02 GB/3.74 GiB)
[ 1134.592019] sd 6:0:0:0: [sdb] Write Protect is off
[ 1134.592024] sd 6:0:0:0: [sdb] Mode Sense: 45 00 00 08
[ 1134.592031] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1134.605509] sr1: scsi3-mmc drive: 48x/48x tray
[ 1134.605680] sr 6:0:0:1: Attached scsi CD-ROM sr1
[ 1134.605779] sr 6:0:0:1: Attached scsi generic sg3 type 5
[ 1134.620367] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1134.620378]  sdb: sdb1
[ 1134.640269] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1134.640278] sd 6:0:0:0: [sdb] Attached SCSI removable disk


However the window does not come up nor can I mount it in the terminal. I looked in /dev, but there is no sdb. lsusb shows no difference between plugged in and not. blkid does not show it either. udevd runs in the 70% CPU usage range on this laptop, I never figured out how exactly to fix that and it is likely related.

---

### Post by wilee-nilee on 2010-05-10
The cruzer has firmware on it like all usb thumbs basically it is called U3. I would just reformat it in gparted or remove that U3 altogether, I think the cruzer web site has a program to remove the firmware. I used to have a 4 gig cruzer and had no problems if I reformatted the thumb before using for install. There are links on the forum about removing theU3 you will have to look for them, a Google search with remove U3 ubuntu forums will probably get you there or are a variation depending on what you want.

---

