---
title: "Ubuntu lock up with noika phone connected"
date: 2010-10-20
forum: Hardware
---

### Post by ksadil on 2010-10-20
Has anyone else notices that if you use a Nokia 6720, connected to Ubuntu(Lucid) by usb (tethered modem or just mass storage is the same), Ubuntu locks up after about 20 minutes?

Here is the relevant /var/log/messages around the time of the incident:

Oct 20 20:34:15 ubuntu kernel: [ 3774.789964] usb 1-1: USB disconnect, address 2
Oct 20 20:34:16 ubuntu kernel: [ 3775.190075] usb 1-1: new high speed USB device using ehci_hcd and address 3
Oct 20 20:34:16 ubuntu kernel: [ 3775.341766] usb 1-1: configuration #1 chosen from 1 choice
Oct 20 20:34:16 ubuntu kernel: [ 3775.376259] Initializing USB Mass Storage driver...
Oct 20 20:34:16 ubuntu kernel: [ 3775.376474] scsi8 : SCSI emulation for USB Mass Storage devices
Oct 20 20:34:16 ubuntu kernel: [ 3775.376648] usbcore: registered new interface driver usb-storage
Oct 20 20:34:16 ubuntu kernel: [ 3775.376653] USB Mass Storage support registered.
Oct 20 20:34:21 ubuntu kernel: [ 3780.382291] scsi 8:0:0:0: Direct-Access     Nokia    S60              1.0  PQ: 0 ANSI: 0
Oct 20 20:34:21 ubuntu kernel: [ 3780.385377] sd 8:0:0:0: Attached scsi generic sg1 type 0
Oct 20 20:34:21 ubuntu kernel: [ 3780.410514] sd 8:0:0:0: [sdb] 1930240 512-byte logical blocks: (988 MB/942 MiB)
Oct 20 20:34:21 ubuntu kernel: [ 3780.411410] sd 8:0:0:0: [sdb] Write Protect is off
Oct 20 20:34:21 ubuntu kernel: [ 3780.416853]  sdb: sdb1
Oct 20 20:34:21 ubuntu kernel: [ 3780.699073] sd 8:0:0:0: [sdb] Attached SCSI removable disk
Oct 20 21:38:16 ubuntu kernel: [ 7615.027111] lo: Disabled Privacy Extensions

Apart from this lockup, everything else about the integration works very well, using the phone to get on the internet is a breeze, as is actually using the device as mass storage.

Any ideas?

---

