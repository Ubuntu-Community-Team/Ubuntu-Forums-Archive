---
title: "SigmaTel MSCNMMC 0100 chip , mp3 player"
date: 2007-11-01
forum: Hardware &amp; Laptops
---

### Post by zwastik on 2007-11-01
hello,  I have a mp3 player it has a sigmatel chip and I can't get it work right. It does not get mount.

[ 9613.916000] usb 2-1: new high speed USB device using ehci_hcd and address 3
[ 9614.064000] usb 2-1: configuration #1 chosen from 1 choice
[ 9614.196000] usbcore: registered new interface driver libusual
[ 9614.240000] Initializing USB Mass Storage driver...
[ 9614.240000] scsi2 : SCSI emulation for USB Mass Storage devices
[ 9614.240000] usb-storage: device found at 3
[ 9614.240000] usb-storage: waiting for device to settle before scanning
[ 9614.240000] usbcore: registered new interface driver usb-storage
[ 9614.240000] USB Mass Storage support registered.
[ 9619.240000] usb-storage: device scan complete
[ 9619.244000] scsi 2:0:0:0: Direct-Access     Generic- SD/MMC           1.00 PQ: 0 ANSI: 0 CCS
[ 9619.972000] sd 2:0:0:0: [sdb] 4022272 512-byte hardware sectors (2059 MB)
[ 9619.972000] sd 2:0:0:0: [sdb] Write Protect is off
[ 9619.972000] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 9619.972000] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 9619.976000] sd 2:0:0:0: [sdb] 4022272 512-byte hardware sectors (2059 MB)
[ 9619.976000] sd 2:0:0:0: [sdb] Write Protect is off
[ 9619.976000] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 9619.976000] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 9619.976000]  sdb: sdb1 sdb2 < sdb5 >
[ 9619.976000] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[ 9619.976000] sd 2:0:0:0: Attached scsi generic sg1 type 0
[ 9643.228000] usb 2-1: USB disconnect, address 3
[ 9694.060000] usb 1-1: new full speed USB device using ohci_hcd and address 3
[ 9695.660000] usb 1-1: configuration #1 chosen from 1 choice
[ 9695.724000] scsi3 : SCSI emulation for USB Mass Storage devices
[ 9695.724000] usb-storage: device found at 3
[ 9695.724000] usb-storage: waiting for device to settle before scanning
[ 9700.724000] usb-storage: device scan complete
[ 9700.732000] scsi 3:0:0:0: Direct-Access     SigmaTel MSCNMMC          0100 PQ: 0 ANSI: 4
[ 9706.408000] usb 1-1: reset full speed USB device using ohci_hcd and address 3
[ 9716.800000] usb 1-1: reset full speed USB device using ohci_hcd and address 3
[ 9722.180000] usb 1-1: reset full speed USB device using ohci_hcd and address 3
[ 9727.360000] usb 1-1: device descriptor read/64, error -62
[ 9732.644000] usb 1-1: device descriptor read/64, error -62
[ 9732.924000] usb 1-1: reset full speed USB device using ohci_hcd and address 3
[ 9738.104000] usb 1-1: device descriptor read/64, error -62
[ 9743.388000] usb 1-1: device descriptor read/64, error -62
[ 9743.668000] usb 1-1: reset full speed USB device using ohci_hcd and address 3
[ 9749.076000] usb 1-1: device not accepting address 3, error -62
[ 9749.252000] usb 1-1: reset full speed USB device using ohci_hcd and address 3
[ 9754.660000] usb 1-1: device not accepting address 3, error -62
[ 9754.660000] scsi 3:0:0:1: scsi: Device offlined - not ready after error recovery
[ 9754.660000] usb 1-1: USB disconnect, address 3
[ 9754.660000] scsi 3:0:0:1: rejecting I/O to offline device
[ 9754.668000] sd 3:0:0:0: [sdb] READ CAPACITY failed
[ 9754.668000] sd 3:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 9754.668000] sd 3:0:0:0: [sdb] Sense not available.
[ 9754.668000] sd 3:0:0:0: [sdb] Write Protect is off
[ 9754.668000] sd 3:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 9754.668000] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 9754.668000] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[ 9754.668000] sd 3:0:0:0: Attached scsi generic sg1 type 0
[ 9754.844000] usb 1-1: new full speed USB device using ohci_hcd and address 4
[ 9760.024000] usb 1-1: device descriptor read/64, error -62
[ 9765.308000] usb 1-1: device descriptor read/64, error -62
[ 9765.588000] usb 1-1: new full speed USB device using ohci_hcd and address 5
[ 9770.768000] usb 1-1: device descriptor read/64, error -62
[ 9776.052000] usb 1-1: device descriptor read/64, error -62
[ 9776.332000] usb 1-1: new full speed USB device using ohci_hcd and address 6
[ 9781.740000] usb 1-1: device not accepting address 6, error -62
[ 9781.916000] usb 1-1: new full speed USB device using ohci_hcd and address 7
[ 9787.324000] usb 1-1: device not accepting address 7, error -62
[ 9914.196000] ehci_hcd 0000:00:02.1: remove, state 4
[ 9914.196000] usb usb2: USB disconnect, address 1
[ 9914.204000] ehci_hcd 0000:00:02.1: USB bus 2 deregistered
[ 9914.204000] ACPI: PCI interrupt for device 0000:00:02.1 disabled
[ 9961.860000] usb 1-1: new full speed USB device using ohci_hcd and address 8
[ 9962.072000] usb 1-1: configuration #1 chosen from 1 choice

---

