---
title: "16 GiB SDHC not working"
date: 2009-06-13
forum: Hardware
---

### Post by ongun.kanat on 2009-06-13
I've bought a new sdhc card for my camera.I've tried to plug.But it's not working.Also my 8gb sdhc memory is not working.

That's the output of lsusb:
> 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
**Bus 001 Device 035: ID 05e3:0711 Genesys Logic, Inc. Card Reader**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


dmesg:
> [ 2052.582436] usb-storage: device found at 37
[ 2052.582443] usb-storage: waiting for device to settle before scanning
[ 2057.580600] usb-storage: device scan complete
[ 2057.696054] usb 1-2: reset high speed USB device using ehci_hcd and address 37
[ 2057.834863] scsi 37:0:0:0: Direct-Access     Generic  STORAGE DEVICE   9144 PQ: 0 ANSI: 0
[ 2057.836568] sd 37:0:0:0: Attached scsi generic sg2 type 0
[ 2073.170209] usb 1-2: USB disconnect, address 37
[ 2073.170611] sd 37:0:0:0: [sdb] READ CAPACITY failed
[ 2073.170617] sd 37:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 2073.170626] sd 37:0:0:0: [sdb] Sense not available.
[ 2073.170709] sd 37:0:0:0: [sdb] Write Protect is off
[ 2073.170716] sd 37:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 2073.170722] sd 37:0:0:0: [sdb] Assuming drive cache: write through
[ 2073.170932] sd 37:0:0:0: [sdb] Attached SCSI removable disk
[ 2091.036062] usb 1-2: new high speed USB device using ehci_hcd and address 38
[ 2091.179904] usb 1-2: configuration #1 chosen from 1 choice
[ 2091.214267] scsi38 : SCSI emulation for USB Mass Storage devices
[ 2091.249181] usb-storage: device found at 38
[ 2091.249188] usb-storage: waiting for device to settle before scanning
[ 2096.248586] usb-storage: device scan complete
[ 2096.249959] scsi 38:0:0:0: Direct-Access     Generic  STORAGE DEVICE   9144 PQ: 0 ANSI: 0
[ 2096.252700] sd 38:0:0:0: Attached scsi generic sg2 type 0


---

### Post by harry7 on 2009-12-20
[COLOR=DarkRed]I am having the same problem in Ubuntu 9.10.

2GB SD card put into multi-card reader and plugged into USB port
----------------------------------------------------------------[/COLOR] 

usb 1-5: new high speed USB device using ehci_hcd and address 44
usb 1-5: configuration #1 chosen from 1 choice
scsi47 : SCSI emulation for USB Mass Storage devices
scsi 47:0:0:0: Direct-Access     Generic  STORAGE DEVICE   0125 PQ: 0 ANSI: 0
scsi 47:0:0:1: Direct-Access     Generic  STORAGE DEVICE   0125 PQ: 0 ANSI: 0
scsi 47:0:0:2: Direct-Access     Generic  STORAGE DEVICE   0125 PQ: 0 ANSI: 0
scsi 47:0:0:3: Direct-Access     Generic  STORAGE DEVICE   0125 PQ: 0 ANSI: 0
sd 47:0:0:0: Attached scsi generic sg2 type 0
sd 47:0:0:1: Attached scsi generic sg3 type 0
sd 47:0:0:2: Attached scsi generic sg4 type 0
sd 47:0:0:3: Attached scsi generic sg5 type 0
sd 47:0:0:1: [sdc] Attached SCSI removable disk
sd 47:0:0:2: [sdd] 3962880 512-byte logical blocks: (2.02 GB/1.88 GiB)
sd 47:0:0:0: [sdb] Attached SCSI removable disk
sd 47:0:0:2: [sdd] Write Protect is off
sd 47:0:0:3: [sde] Attached SCSI removable disk
 sdd: sdd1
sd 47:0:0:2: [sdd] Attached SCSI removable disk

[COLOR=DarkRed]works fine
unmounted 2GB SD card
unplugged card reader
---------------------[/COLOR]

usb 1-5: USB disconnect, address 44

[COLOR=DarkRed]put in 8GB SD card and plugged back in
--------------------------------------[/COLOR]

usb 1-5: new high speed USB device using ehci_hcd and address 45
usb 1-5: configuration #1 chosen from 1 choice
scsi48 : SCSI emulation for USB Mass Storage devices
scsi 48:0:0:0: Direct-Access     Generic  STORAGE DEVICE   0125 PQ: 0 ANSI: 0
usb 1-5: reset high speed USB device using ehci_hcd and address 45
usb 1-5: reset high speed USB device using ehci_hcd and address 45
usb 1-5: reset high speed USB device using ehci_hcd and address 45
usb 1-5: reset high speed USB device using ehci_hcd and address 45
usb 1-5: reset high speed USB device using ehci_hcd and address 45
scsi 48:0:0:1: Device offlined - not ready after error recovery
sd 48:0:0:0: Attached scsi generic sg2 type 0
usb 1-5: reset high speed USB device using ehci_hcd and address 45
usb 1-5: reset high speed USB device using ehci_hcd and address 45
usb 1-5: reset high speed USB device using ehci_hcd and address 45
usb 1-5: reset high speed USB device using ehci_hcd and address 45
usb 1-5: reset high speed USB device using ehci_hcd and address 45
sd 48:0:0:0: Device offlined - not ready after error recovery
sd 48:0:0:0: [sdb] READ CAPACITY failed
sd 48:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
sd 48:0:0:0: [sdb] Sense not available.
sd 48:0:0:0: [sdb] Write Protect is off
sd 48:0:0:0: [sdb] Attached SCSI removable disk

[COLOR=DarkRed]and there it stops[/COLOR]

---

