---
title: "Pentagram EON Cineo not connecting throught USB"
date: 2008-08-10
forum: Hardware
---

### Post by Chainz on 2008-08-10
Hello,
I just bought Pentagram EON Cineo player - nice toy, but just can't connect to any of my computers. :(

lsusb command shows nothing:
```
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
``` 

dmesg gives some feedback:
```
[ 1015.829213] usb 3-7: new high speed USB device using ehci_hcd and address 3
[ 1015.962084] usb 3-7: configuration #1 chosen from 1 choice
[ 1016.070290] usbcore: registered new interface driver libusual
[ 1016.119526] Initializing USB Mass Storage driver...
[ 1016.119718] scsi2 : SCSI emulation for USB Mass Storage devices
[ 1016.119875] usb-storage: device found at 3
[ 1016.119878] usb-storage: waiting for device to settle before scanning
[ 1016.120038] usbcore: registered new interface driver usb-storage
[ 1016.120125] USB Mass Storage support registered.
[ 1021.110739] usb-storage: device scan complete
[ 1021.111319] scsi 2:0:0:0: Direct-Access     Cineo    USBDISK  User    1.00 PQ: 0 ANSI: 0
[ 1021.111970] scsi 2:0:0:1: Direct-Access     Cineo    USBDISK    SD    1.00 PQ: 0 ANSI: 0 CCS
[ 1021.113707] sd 2:0:0:0: [sdc] Attached SCSI removable disk
[ 1021.113774] sd 2:0:0:0: Attached scsi generic sg2 type 0
[ 1021.115585] sd 2:0:0:1: [sdd] Attached SCSI removable disk
[ 1021.115644] sd 2:0:0:1: Attached scsi generic sg3 type 0
[ 1021.466666] sd 2:0:0:0: [sdc] 16013312 512-byte hardware sectors (8199 MB)
[ 1021.577928] usb 3-7: reset high speed USB device using ehci_hcd and address 3
[ 1021.801697] usb 3-7: USB disconnect, address 3
[ 1021.807636] scsi 2:0:0:1: rejecting I/O to dead device
[ 1021.807745] scsi 2:0:0:1: rejecting I/O to dead device
[ 1021.807828] scsi 2:0:0:1: rejecting I/O to dead device
[ 1021.807910] scsi 2:0:0:1: rejecting I/O to dead device
[ 1021.807990] scsi 2:0:0:1: [sdd] READ CAPACITY failed
[ 1021.807993] scsi 2:0:0:1: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 1021.807998] scsi 2:0:0:1: [sdd] Sense not available.
[ 1021.808264] scsi 2:0:0:1: rejecting I/O to dead device
[ 1021.808343] scsi 2:0:0:1: [sdd] Write Protect is off
[ 1021.808347] scsi 2:0:0:1: [sdd] Mode Sense: 00 00 00 00
[ 1021.808350] scsi 2:0:0:1: [sdd] Assuming drive cache: write through
[ 1021.808584] scsi 2:0:0:1: rejecting I/O to dead device
[ 1021.808669] scsi 2:0:0:1: rejecting I/O to dead device
[ 1021.808751] scsi 2:0:0:1: rejecting I/O to dead device
[ 1021.808832] scsi 2:0:0:1: rejecting I/O to dead device
[ 1021.808913] scsi 2:0:0:1: rejecting I/O to dead device
[ 1021.808991] scsi 2:0:0:1: [sdd] READ CAPACITY failed
[ 1021.808994] scsi 2:0:0:1: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 1021.808998] scsi 2:0:0:1: [sdd] Sense not available.
[ 1021.809259] scsi 2:0:0:1: rejecting I/O to dead device
[ 1021.809337] scsi 2:0:0:1: [sdd] Write Protect is off
[ 1021.809341] scsi 2:0:0:1: [sdd] Mode Sense: 00 00 00 00
[ 1021.809343] scsi 2:0:0:1: [sdd] Assuming drive cache: write through
[ 1021.811780] scsi 2:0:0:1: rejecting I/O to dead device
[ 1021.817694] scsi 2:0:0:0: [sdc] Write Protect is off
[ 1021.817703] scsi 2:0:0:0: [sdc] Mode Sense: 03 00 00 00
[ 1021.817707] scsi 2:0:0:0: [sdc] Assuming drive cache: write through
[ 1021.818274] scsi 2:0:0:0: rejecting I/O to dead device
[ 1021.818464] scsi 2:0:0:0: rejecting I/O to dead device
[ 1021.818647] scsi 2:0:0:0: rejecting I/O to dead device
[ 1021.818826] scsi 2:0:0:0: rejecting I/O to dead device
[ 1021.819085] scsi 2:0:0:0: rejecting I/O to dead device
[ 1021.819259] scsi 2:0:0:0: [sdc] READ CAPACITY failed
[ 1021.819263] scsi 2:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 1021.819269] scsi 2:0:0:0: [sdc] Sense not available.
[ 1021.819899] scsi 2:0:0:0: rejecting I/O to dead device
[ 1021.820073] scsi 2:0:0:0: [sdc] Write Protect is off
[ 1021.820078] scsi 2:0:0:0: [sdc] Mode Sense: 00 00 00 00
[ 1021.820081] scsi 2:0:0:0: [sdc] Assuming drive cache: write through
[ 1021.821573] scsi 2:0:0:0: rejecting I/O to dead device
[ 1021.821584] Buffer I/O error on device sdc, logical block 2001648
[ 1021.822492] scsi 2:0:0:0: rejecting I/O to dead device
[ 1021.822499] Buffer I/O error on device sdc, logical block 2001648
[ 1021.822911] scsi 2:0:0:0: rejecting I/O to dead device
[ 1021.822917] Buffer I/O error on device sdc, logical block 2001662
[ 1021.823277] scsi 2:0:0:0: rejecting I/O to dead device
[ 1021.823283] Buffer I/O error on device sdc, logical block 2001662
[ 1021.823668] scsi 2:0:0:0: rejecting I/O to dead device
[ 1021.823673] Buffer I/O error on device sdc, logical block 0
[ 1021.824020] scsi 2:0:0:0: rejecting I/O to dead device
[ 1021.824025] Buffer I/O error on device sdc, logical block 0
[ 1021.824407] scsi 2:0:0:0: rejecting I/O to dead device
[ 1021.824413] Buffer I/O error on device sdc, logical block 0
[ 1021.824774] scsi 2:0:0:0: rejecting I/O to dead device
[ 1021.824780] Buffer I/O error on device sdc, logical block 2001663
[ 1021.825441] scsi 2:0:0:0: rejecting I/O to dead device
[ 1021.825447] Buffer I/O error on device sdc, logical block 2001663
[ 1021.825826] scsi 2:0:0:0: rejecting I/O to dead device
[ 1021.825832] Buffer I/O error on device sdc, logical block 2001663
[ 1021.826198] scsi 2:0:0:0: rejecting I/O to dead device
[ 1021.826409] scsi 2:0:0:0: rejecting I/O to dead device
[ 1021.826636] scsi 2:0:0:0: rejecting I/O to dead device

```

But that just doesn't tell me much :(

Anybody any ideas?
Have tested it under Gutsy and Hardy - same results

---

