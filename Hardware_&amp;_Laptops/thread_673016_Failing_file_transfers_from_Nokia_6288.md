---
title: "Failing file transfers from Nokia 6288"
date: 2008-01-20
forum: Hardware &amp; Laptops
---

### Post by yaztromo on 2008-01-20
I cannot copy files from a Nokia 6288 in data transfer mode using the Nokia USB cable. The transfer will work for a few seconds then stall.

I tried echo 32, 64 and 128 to max_sectors_kb in as suggested in another thread to no avail.

Does anyone know a solution to this?

Dmesg output:
> 
[ 2744.768828] usb 1-1: new full speed USB device using ohci_hcd and address 15
[ 2744.993654] usb 1-1: configuration #1 chosen from 1 choice
[ 2744.996716] scsi7 : SCSI emulation for USB Mass Storage devices
[ 2744.997048] usb-storage: device found at 15
[ 2744.997052] usb-storage: waiting for device to settle before scanning
[ 2749.997415] usb-storage: device scan complete
[ 2750.004443] scsi 7:0:0:0: Direct-Access Nokia Nokia 6288 0000 PQ: 0 ANSI: 4
[ 2750.015382] sd 7:0:0:0: [sdb] 1000449 512-byte hardware sectors (512 MB)
[ 2750.032379] sd 7:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2750.032395] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 2750.051368] sd 7:0:0:0: [sdb] 1000449 512-byte hardware sectors (512 MB)
[ 2750.069353] sd 7:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2750.069369] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 2750.069379] sdb:
[ 2750.258377] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[ 2750.258491] sd 7:0:0:0: Attached scsi generic sg2 type 0
[ 2750.503385] sd 7:0:0:0: [sdb] Sense Key : No Sense [current]
[ 2750.503403] sd 7:0:0:0: [sdb] Add. Sense: No additional sense information
[ 2750.726061] sd 7:0:0:0: [sdb] Sense Key : No Sense [current]
[ 2750.726079] sd 7:0:0:0: [sdb] Add. Sense: No additional sense information
[ 2750.958966] sd 7:0:0:0: [sdb] Sense Key : No Sense [current]
[ 2750.958984] sd 7:0:0:0: [sdb] Add. Sense: No additional sense information
[ 2765.495649] usb 1-1: reset full speed USB device using ohci_hcd and address 15
[ 2795.868037] usb 1-1: reset full speed USB device using ohci_hcd and address 15
[ 2806.261414] usb 1-1: reset full speed USB device using ohci_hcd and address 15
[ 2812.883788] usb 1-1: reset full speed USB device using ohci_hcd and address 15
[ 2843.260159] usb 1-1: reset full speed USB device using ohci_hcd and address 15
[ 2853.637549] usb 1-1: reset full speed USB device using ohci_hcd and address 15
[ 2860.259899] usb 1-1: reset full speed USB device using ohci_hcd and address 15
[ 2890.632276] usb 1-1: reset full speed USB device using ohci_hcd and address 15
[ 2901.009671] usb 1-1: reset full speed USB device using ohci_hcd and address 15
[ 2907.225003] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
[ 2907.225023] end_request: I/O error, dev sdb, sector 31931
[ 3032.992603] usb 1-1: reset full speed USB device using ohci_hcd and address 15
[ 3063.364987] usb 1-1: reset full speed USB device using ohci_hcd and address 15
[ 3073.742403] usb 1-1: reset full speed USB device using ohci_hcd and address 15
[ 3080.364735] usb 1-1: reset full speed USB device using ohci_hcd and address 15
[ 3110.737116] usb 1-1: reset full speed USB device using ohci_hcd and address 15
[ 3121.114526] usb 1-1: reset full speed USB device using ohci_hcd and address 15
[ 3127.732848] usb 1-1: reset full speed USB device using ohci_hcd and address 15
[ 3127.912805] usb 1-1: device descriptor read/64, error -62
[ 3128.196752] usb 1-1: device descriptor read/64, error -62
[ 3128.476665] usb 1-1: reset full speed USB device using ohci_hcd and address 15
[ 3128.656616] usb 1-1: device descriptor read/64, error -62
[ 3128.996607] usb 1-1: USB disconnect, address 15
[ 3129.000567] sd 7:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3129.000587] end_request: I/O error, dev sdb, sector 32491
[ 3129.000657] sd 7:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3129.000664] end_request: I/O error, dev sdb, sector 32731
[ 3129.000685] Buffer I/O error on device sdb, logical block 523
[ 3129.000692] lost page write due to I/O error on sdb
[ 3129.009334] Buffer I/O error on device sdb, logical block 523
[ 3129.009347] lost page write due to I/O error on sdb
[ 3129.016854] VFS: busy inodes on changed media.
[ 3129.016990] scsi 7:0:0:0: rejecting I/O to dead device
[ 3129.017137] scsi 7:0:0:0: rejecting I/O to dead device
[ 3129.017259] scsi 7:0:0:0: rejecting I/O to dead device
[ 3129.017379] scsi 7:0:0:0: rejecting I/O to dead device
[ 3129.017506] scsi 7:0:0:0: [sdb] READ CAPACITY failed
[ 3129.017511] scsi 7:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3129.017518] scsi 7:0:0:0: [sdb] Sense not available.
[ 3129.017529] scsi 7:0:0:0: rejecting I/O to dead device
[ 3129.017537] scsi 7:0:0:0: [sdb] Write Protect is off
[ 3129.017542] scsi 7:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 3129.017546] scsi 7:0:0:0: [sdb] Assuming drive cache: write through
[ 3129.028588] scsi 7:0:0:0: rejecting I/O to dead device
[ 3129.028791] scsi 7:0:0:0: rejecting I/O to dead device
[ 3129.052361] scsi 7:0:0:0: rejecting I/O to dead device
[ 3129.125739] scsi 7:0:0:0: rejecting I/O to dead device
[ 3129.126209] FAT: unable to read inode block for updating (i_pos 8375)
[ 3129.126527] scsi 7:0:0:0: rejecting I/O to dead device
[ 3129.126797] FAT: unable to read inode block for updating (i_pos 8373)
[ 3129.127219] scsi 7:0:0:0: rejecting I/O to dead device


---

### Post by yaztromo on 2008-01-20
Solved it. I was referencing the wrong drive. I was doing:

echo 32 > /sys/block/sda/queue/max_sectors_kb 

Typing this fixes everything:

echo 32 > /sys/block/sdb/queue/max_sectors_kb

---

