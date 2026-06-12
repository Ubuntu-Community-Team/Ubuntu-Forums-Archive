---
title: "Western Digital 160G usb drive not working"
date: 2006-11-10
forum: Hardware &amp; Laptops
---

### Post by Snocrash on 2006-11-10
When I plug my Wester Digital Passport USB drive into my desktop, it does not get mounted.

dmesg gives:

[17180140.896000] usb 7-5: new high speed USB device using ehci_hcd and address 2
[17180162.552000] usb 7-5: new high speed USB device using ehci_hcd and address 3
[17180184.204000] usb 7-5: new high speed USB device using ehci_hcd and address 4
[17180184.740000] usb 7-5: device not accepting address 4, error -71
[17180248.600000] usb 7-5: new high speed USB device using ehci_hcd and address 6
[17180270.248000] usb 7-5: new high speed USB device using ehci_hcd and address 7


and lsusb gives:

Bus 007 Device 001: ID 0000:0000
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 03f0:6204 Hewlett-Packard DeskJet 5150c
Bus 001 Device 001: ID 0000:0000


It is not there. I have tried different ports, no good.

Oddly enough, It works fine on my laptop.

Just for the fun of it, I compiled a new kernel from 2.6.18.2 vanilla source and added the sd_mod module to my rc.local file, pluged in the drive and rebooted.

It saw the drive and added it:

[ 54.336000] usb-storage: device found at 5
[ 54.336000] usb-storage: waiting for device to settle before scanning
[ 59.336000] Vendor: WD Model: 1600BEVExternal Rev: 1.02
[ 59.336000] Type: Direct-Access ANSI SCSI revision: 00
[ 59.336000] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[ 59.336000] sda: Write Protect is off
[ 59.336000] sda: Mode Sense: 00 00 00 00
[ 59.336000] sda: assuming drive cache: write through
[ 59.336000] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[ 59.336000] sda: Write Protect is off
[ 59.336000] sda: Mode Sense: 00 00 00 00
[ 59.336000] sda: assuming drive cache: write through
[ 59.336000] sda: sda1
[ 59.388000] sd 2:0:0:0: Attached scsi disk sda
[ 59.388000] sd 2:0:0:0: Attached scsi generic sg1 type 0
[ 59.392000] usb-storage: device scan complete



But then it dropped it:

[ 59.500000] usb 6-2: USB disconnect, address 5
[ 102.200000] usb 6-2: new high speed USB device using ehci_hcd and address 6
[ 102.340000] usb 6-2: configuration #1 chosen from 1 choice
[ 102.340000] scsi3 : SCSI emulation for USB Mass Storage devices
[ 102.340000] usb-storage: device found at 6
[ 102.340000] usb-storage: waiting for device to settle before scanning
[ 102.704000] usb 6-2: USB disconnect, address 6
[ 124.620000] usb 6-2: new high speed USB device using ehci_hcd and address 7
[ 124.760000] usb 6-2: configuration #1 chosen from 1 choice
[ 124.760000] scsi4 : SCSI emulation for USB Mass Storage devices
[ 124.760000] usb-storage: device found at 7
[ 124.760000] usb-storage: waiting for device to settle before scanning
[ 125.132000] usb 6-2: USB disconnect, address 7
[ 147.168000] usb 6-2: new high speed USB device using ehci_hcd and address 8


Can't figure out why......

Any ideas???

Thanks,

Sno

---

### Post by wislon on 2006-11-10
I had a similar problem with a 40GB external USB drive. It turned out that there wasn't quite enough power getting to it (it takes power from two USB ports simultaneously, one of those ports it used to connect the device too).

At that point I had the device plugged into the two USB slots on the front of my box, and had similar experience to yours. As soon as I plugged them into slots on the BACK of the PC, directly into the motherboard, it all worked without a hitch.

HTH :)

---

### Post by Snocrash on 2006-11-13
Yep.....Power problem.

Had to go get a powered USB hub. Now it works fine.

Thanks,

-Sno

---

