---
title: "Hard drives etc. not mounting"
date: 2011-12-27
forum: Hardware
---

### Post by jimhenry on 2011-12-27
Last night I had one of my external hard drives connected to my laptop -- Dell Inspiron 15n, running Ubuntu 8.10.  It had mounted normally when I plugged it into one of the USB ports.  About fifteen minutes later, it seems to have spontaneously unmounted.  Since then I've unplugged and plugged that and two other external hard drives, and an MP3 player's flash memory -- none of them are mounting either.

These messages were in the syslog at about the time the drive unmounted:

```
Dec 26 18:44:56 dell-desktop kernel: [ 4171.239599] usb 8-3: USB disconnect, address 4
Dec 26 18:44:56 dell-desktop hald[5834]: forcibly attempting to lazy unmount /dev/sdc1 as enclosing drive was disconnected
Dec 26 18:44:57 dell-desktop ntfs-3g[8157]: Unmounting /dev/sdc1 (FreeAgent Drive) 
Dec 26 18:44:57 dell-desktop hald: unmounted /dev/sdc1 from '/media/FreeAgent Drive' on behalf of uid 0
Dec 26 18:45:10 dell-desktop kernel: [ 4185.044059] usb 8-3: new high speed USB device using ehci_hcd and address 5
Dec 26 18:45:10 dell-desktop kernel: [ 4185.181909] usb 8-3: configuration #1 chosen from 1 choice
Dec 26 18:45:10 dell-desktop kernel: [ 4185.183247] scsi8 : SCSI emulation for USB Mass Storage devices
Dec 26 18:45:10 dell-desktop kernel: [ 4185.185689] usb-storage: device found at 5
Dec 26 18:45:10 dell-desktop kernel: [ 4185.185698] usb-storage: waiting for device to settle before scanning
Dec 26 18:45:15 dell-desktop kernel: [ 4190.185286] usb-storage: device scan complete
Dec 26 18:45:15 dell-desktop kernel: [ 4190.185852] scsi 8:0:0:0: Direct-Access     Seagate  FreeAgent        0132 PQ: 0 ANSI: 4
Dec 26 18:45:15 dell-desktop kernel: [ 4190.203943] sd 8:0:0:0: [sdc] 1953525168 512-byte hardware sectors (1000205 MB)
Dec 26 18:45:15 dell-desktop kernel: [ 4190.204579] sd 8:0:0:0: [sdc] Write Protect is off
Dec 26 18:45:15 dell-desktop kernel: [ 4190.204585] sd 8:0:0:0: [sdc] Mode Sense: 2d 08 00 00
Dec 26 18:45:15 dell-desktop kernel: [ 4190.204590] sd 8:0:0:0: [sdc] Assuming drive cache: write through
Dec 26 18:45:15 dell-desktop kernel: [ 4190.216431] sd 8:0:0:0: [sdc] 1953525168 512-byte hardware sectors (1000205 MB)
Dec 26 18:45:15 dell-desktop kernel: [ 4190.217048] sd 8:0:0:0: [sdc] Write Protect is off
Dec 26 18:45:15 dell-desktop kernel: [ 4190.217053] sd 8:0:0:0: [sdc] Mode Sense: 2d 08 00 00
Dec 26 18:45:15 dell-desktop kernel: [ 4190.217057] sd 8:0:0:0: [sdc] Assuming drive cache: write through
Dec 26 18:45:15 dell-desktop kernel: [ 4190.217065]  sdc: sdc1

```Later on, when I plug that or another drive into a USB port, I'm getting messages like these:

```
Dec 27 01:36:28 dell-desktop kernel: [28862.932058] usb 8-1: new high speed USB device using ehci_hcd and address 92
Dec 27 01:36:28 dell-desktop kernel: [28863.066287] usb 8-1: configuration #1 chosen from 1 choice
Dec 27 01:36:28 dell-desktop kernel: [28863.067104] scsi55 : SCSI emulation for USB Mass Storage devices
Dec 27 01:36:28 dell-desktop kernel: [28863.100358] usb-storage: device found at 92
Dec 27 01:36:28 dell-desktop kernel: [28863.100366] usb-storage: waiting for device to settle before scanning
Dec 27 01:36:33 dell-desktop kernel: [28868.100295] usb-storage: device scan complete
Dec 27 01:36:33 dell-desktop kernel: [28868.102501] scsi 55:0:0:0: Direct-Access     WD       Ext HDD 1021     2021 PQ: 0 ANSI: 4
Dec 27 01:36:33 dell-desktop kernel: [28868.105079] sd 55:0:0:0: [sde] 2930272256 512-byte hardware sectors (1500299 MB)
Dec 27 01:36:33 dell-desktop kernel: [28868.106949] sd 55:0:0:0: [sde] Write Protect is off
Dec 27 01:36:33 dell-desktop kernel: [28868.106957] sd 55:0:0:0: [sde] Mode Sense: 17 00 10 08
Dec 27 01:36:33 dell-desktop kernel: [28868.106962] sd 55:0:0:0: [sde] Assuming drive cache: write through
Dec 27 01:36:33 dell-desktop kernel: [28868.107815] sd 55:0:0:0: [sde] 2930272256 512-byte hardware sectors (1500299 MB)
Dec 27 01:36:33 dell-desktop kernel: [28868.109566] sd 55:0:0:0: [sde] Write Protect is off
Dec 27 01:36:33 dell-desktop kernel: [28868.109573] sd 55:0:0:0: [sde] Mode Sense: 17 00 10 08
Dec 27 01:36:33 dell-desktop kernel: [28868.109576] sd 55:0:0:0: [sde] Assuming drive cache: write through
Dec 27 01:36:33 dell-desktop kernel: [28868.109585]  sde: sde1
Dec 27 01:36:33 dell-desktop kernel: [28868.132175] sd 55:0:0:0: [sde] Attached SCSI disk
Dec 27 01:36:33 dell-desktop kernel: [28868.132347] sd 55:0:0:0: Attached scsi generic sg4 type 0

```

---

