---
title: "SD Card reader problem"
date: 2024-06-26
forum: Hardware
---

### Post by juanero2 on 2024-06-26
1.706 / 5.000
Hello,


I was hearing a sound that repeated every x number of minutes. In a forum they proposed executing the command "sudo dmesg | tail -50" as soon as I heard the sound and that's how I realized that the card reader is being permanently connected and disconnected:


This is the output that repeats every time I hear the sound:
[3419.238650] usb 4-3: new SuperSpeed &#8203;&#8203;USB device number 12 using xhci_hcd
[ 3419.291089] usb 4-3: New USB device found, idVendor=0bda, idProduct=0321, bcdDevice=11.21
[ 3419.291099] usb 4-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 3419.291104] usb 4-3: Product: USB Card Reader
[3419.291107] usb 4-3: Manufacturer: Realtek
[3419.291111] usb 4-3: SerialNumber: 201312261010
[ 3419.298839] usb-storage 4-3:1.0: USB Mass Storage device detected
[3419.299173] scsi host9: usb-storage 4-3:1.0
[ 3420.329756] scsi 9:0:0:0: Direct-Access Generic- USB CRW-CF/MD 1.00 PQ: 0 ANSI: 6
[ 3420.347209] scsi 9:0:0:1: Direct-Access Generic - USB CRW-SD 1.00 PQ: 0 ANSI: 6
[ 3420.364681] scsi 9:0:0:2: Direct-Access Generic - USB CRW-MS 1.00 PQ: 0 ANSI: 6
[ 3420.365254] sd 9:0:0:0: Attached scsi generic sg3 type 0
[ 3420.365519] sd 9:0:0:1: Attached scsi generic sg4 type 0
[ 3420.365856] sd 9:0:0:2: Attached scsi generic sg5 type 0
[ 3420.368569] sd 9:0:0:0: [sdc] Media removed, stopped polling
[ 3420.369376] sd 9:0:0:0: [sdc] Attached SCSI removable disk
[ 3420.371033] sd 9:0:0:1: [sdd] Media removed, stopped polling
[ 3420.373027] sd 9:0:0:1: [sdd] Attached SCSI removable disk
[ 3420.376390] sd 9:0:0:2: [sde] Media removed, stopped polling
[ 3420.378572] sd 9:0:0:2: [sde] Attached SCSI removable disk


How can I solve it?

---

### Post by currentshaft on 2024-06-26
Disconnect the card reader? Perhaps it has a failing USB cable from use?

---

