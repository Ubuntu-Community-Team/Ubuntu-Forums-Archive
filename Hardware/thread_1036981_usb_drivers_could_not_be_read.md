---
title: "usb drivers could not be read"
date: 2009-01-11
forum: Hardware
---

### Post by Kelen.Chang on 2009-01-11
it's nothing happened when i put on usb driver, 
checked last dmesg, it's said 
```
[ 1617.266844] usb 5-2: new full speed USB device using uhci_hcd and address 2
[ 1617.425082] usb 5-2: configuration #1 chosen from 1 choice
[ 1617.599399] usbcore: registered new interface driver libusual
[ 1617.726426] Initializing USB Mass Storage driver...
[ 1617.727654] scsi5 : SCSI emulation for USB Mass Storage devices
[ 1617.729470] usbcore: registered new interface driver usb-storage
[ 1617.729477] USB Mass Storage support registered.
[ 1617.729564] usb-storage: device found at 2
[ 1617.729566] usb-storage: waiting for device to settle before scanning
[ 1622.726219] usb-storage: device scan complete
[ 1622.729147] scsi 5:0:0:0: Direct-Access                                    PQ: 0 ANSI: 0
[ 1622.734925] sd 5:0:0:0: [sdb] Very big device. Trying to use READ CAPACITY(16).
[ 1622.755923] sd 5:0:0:0: [sdb] READ CAPACITY(16) failed
[ 1622.755934] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1622.755943] sd 5:0:0:0: [sdb] Use 0xffffffff as device size
[ 1622.755950] sd 5:0:0:0: [sdb] 4294967296 512-byte hardware sectors (2199023 MB)
[ 1622.758916] sd 5:0:0:0: [sdb] Write Protect is off
[ 1622.758925] sd 5:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 1622.758930] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1622.763887] sd 5:0:0:0: [sdb] Very big device. Trying to use READ CAPACITY(16).
[ 1622.784861] sd 5:0:0:0: [sdb] READ CAPACITY(16) failed
[ 1622.784867] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1622.784871] sd 5:0:0:0: [sdb] Use 0xffffffff as device size
[ 1622.784873] sd 5:0:0:0: [sdb] 4294967296 512-byte hardware sectors (2199023 MB)
[ 1622.787856] sd 5:0:0:0: [sdb] Write Protect is off
[ 1622.787859] sd 5:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 1622.787861] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1622.787866]  sdb:<6>usb 5-2: reset full speed USB device using uhci_hcd and address 2
[ 1663.126950] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[ 1668.383655] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[ 1678.638651] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[ 1678.781034] sd 5:0:0:0: Device offlined - not ready after error recovery
[ 1678.781056] sd 5:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
[ 1678.781065] end_request: I/O error, dev sdb, sector 0
[ 1678.781072] Buffer I/O error on device sdb, logical block 0
[ 1678.781131] sd 5:0:0:0: rejecting I/O to offline device
[ 1678.781138] Buffer I/O error on device sdb, logical block 0
[ 1678.781160] sd 5:0:0:0: rejecting I/O to offline device
[ 1678.781166] Buffer I/O error on device sdb, logical block 0
[ 1678.781182] sd 5:0:0:0: rejecting I/O to offline device
[ 1678.781187] Buffer I/O error on device sdb, logical block 0
[ 1678.781201] sd 5:0:0:0: rejecting I/O to offline device
[ 1678.781207] Buffer I/O error on device sdb, logical block 0
[ 1678.781216] ldm_validate_partition_table(): Disk read failed.
[ 1678.781227] sd 5:0:0:0: rejecting I/O to offline device
[ 1678.781233] Buffer I/O error on device sdb, logical block 0
[ 1678.781246] sd 5:0:0:0: rejecting I/O to offline device
[ 1678.781252] Buffer I/O error on device sdb, logical block 0
[ 1678.781266] sd 5:0:0:0: rejecting I/O to offline device
[ 1678.781271] Buffer I/O error on device sdb, logical block 0
[ 1678.781284] sd 5:0:0:0: rejecting I/O to offline device
[ 1678.781290] Buffer I/O error on device sdb, logical block 0
[ 1678.781299] Dev sdb: unable to read RDB block 0
[ 1678.781324] sd 5:0:0:0: rejecting I/O to offline device
[ 1678.781330] Buffer I/O error on device sdb, logical block 0
[ 1678.781345] sd 5:0:0:0: rejecting I/O to offline device
[ 1678.781368] sd 5:0:0:0: rejecting I/O to offline device
[ 1678.781381] sd 5:0:0:0: rejecting I/O to offline device
[ 1678.781394] sd 5:0:0:0: rejecting I/O to offline device
[ 1678.781408] sd 5:0:0:0: rejecting I/O to offline device
[ 1678.781417]  unable to read partition table
[ 1678.781523] sd 5:0:0:0: [sdb] Attached SCSI disk
[ 1678.781609] sd 5:0:0:0: Attached scsi generic sg2 type 0
[ 1684.426311] usb 5-2: USB disconnect, address 2
[ 1684.697778] usb 5-2: new full speed USB device using uhci_hcd and address 3
[ 1684.864899] usb 5-2: configuration #1 chosen from 1 choice
[ 1684.868663] scsi6 : SCSI emulation for USB Mass Storage devices
[ 1684.869360] usb-storage: device found at 3
[ 1684.869364] usb-storage: waiting for device to settle before scanning
[ 1689.863978] usb-storage: device scan complete
[ 1695.473097] usb 5-2: reset full speed USB device using uhci_hcd and address 3

```

---

### Post by Kelen.Chang on 2009-01-12
it's could not be found even i using command <sudo fdisk -l>, 
Is there any idea for this Problem? plz!

---

### Post by Neural oD on 2009-02-17
I have the same problem - I'm using an external harddrive with firewire 
wonder if this is a bug in the kernel

---

