---
title: "Bus powered external hard drive"
date: 2009-04-11
forum: Hardware
---

### Post by jdelasalas on 2009-04-11
I bought an external harddrive powered off the bus recently.  It works alright when I transfer small files, like a PDF or a folder full of 20 or so PDFs.  However when I let it idle or try to move a huge file onto it, I get an error: "This is a read only file system"

Dmesg output:
usb-storage: device found at 4
usb-storage: waiting for device to settle before scanning
usb 2-1: New USB device found, idVendor=04fc, idProduct=0c25
usb 2-1: New USB device strings: Mfr=2, Product=3, SerialNumber=1
usb 2-1: Product: USB to Serial-ATA bridge
usb 2-1: Manufacturer: Sunplus Technology Inc.
usb 2-1: SerialNumber: ST9160821A5MA3LZVC            
scsi 6:0:0:0: Direct-Access     ST916082 1AS                   PQ: 0 ANSI: 2
sd 6:0:0:0: [sdc] 312581808 512-byte hardware sectors (160042 MB)
sd 6:0:0:0: [sdc] Write Protect is off
sd 6:0:0:0: [sdc] Mode Sense: 38 00 00 00
sd 6:0:0:0: [sdc] Assuming drive cache: write through
sd 6:0:0:0: [sdc] 312581808 512-byte hardware sectors (160042 MB)
sd 6:0:0:0: [sdc] Write Protect is off
sd 6:0:0:0: [sdc] Mode Sense: 38 00 00 00
sd 6:0:0:0: [sdc] Assuming drive cache: write through
 sdc: sdc1
sd 6:0:0:0: [sdc] Attached SCSI disk
sd 6:0:0:0: Attached scsi generic sg2 type 0
usb-storage: device scan complete
usb 2-1: reset high speed USB device using ehci_hcd and address 4
usb 2-1: reset high speed USB device using ehci_hcd and address 4
kjournald starting.  Commit interval 5 seconds
EXT3 FS on sdc1, internal journal
EXT3-fs: recovery complete.
EXT3-fs: mounted filesystem with ordered data mode.
usb 2-1: reset high speed USB device using ehci_hcd and address 4
EXT3-fs error (device sdb1): ext3_find_entry: reading directory #2 offset 0
usb 2-1: reset high speed USB device using ehci_hcd and address 4
usb 2-1: reset high speed USB device using ehci_hcd and address 4
usb 2-1: reset high speed USB device using ehci_hcd and address 4
usb 2-1: reset high speed USB device using ehci_hcd and address 4
usb 2-1: reset high speed USB device using ehci_hcd and address 4
usb 2-1: reset high speed USB device using ehci_hcd and address 4
usb 2-1: reset high speed USB device using ehci_hcd and address 4
usb 2-1: reset high speed USB device using ehci_hcd and address 4
usb 2-1: reset high speed USB device using ehci_hcd and address 4
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102604647
__ratelimit: 50915 callbacks suppressed
Buffer I/O error on device sdc1, logical block 12825573
lost page write due to I/O error on sdc1
Buffer I/O error on device sdc1, logical block 12825574
lost page write due to I/O error on sdc1
Buffer I/O error on device sdc1, logical block 12825575
lost page write due to I/O error on sdc1
Buffer I/O error on device sdc1, logical block 12825576
lost page write due to I/O error on sdc1
Buffer I/O error on device sdc1, logical block 12825577
lost page write due to I/O error on sdc1
Buffer I/O error on device sdc1, logical block 12825578
lost page write due to I/O error on sdc1
Buffer I/O error on device sdc1, logical block 12825579
lost page write due to I/O error on sdc1
Buffer I/O error on device sdc1, logical block 12825580
lost page write due to I/O error on sdc1
usb 2-1: reset high speed USB device using ehci_hcd and address 4
usb 2-1: reset high speed USB device using ehci_hcd and address 4
usb 2-1: reset high speed USB device using ehci_hcd and address 4
usb 2-1: reset high speed USB device using ehci_hcd and address 4
usb 2-1: reset high speed USB device using ehci_hcd and address 4
usb 2-1: reset high speed USB device using ehci_hcd and address 4
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102604711
Buffer I/O error on device sdc1, logical block 12825581
lost page write due to I/O error on sdc1
Buffer I/O error on device sdc1, logical block 12825582
lost page write due to I/O error on sdc1
Buffer I/O error on device sdc1, logical block 12825583
lost page write due to I/O error on sdc1
Buffer I/O error on device sdc1, logical block 12825584
lost page write due to I/O error on sdc1
Buffer I/O error on device sdc1, logical block 12825585
lost page write due to I/O error on sdc1
Buffer I/O error on device sdc1, logical block 12825586
lost page write due to I/O error on sdc1
Buffer I/O error on device sdc1, logical block 12825587
lost page write due to I/O error on sdc1
Buffer I/O error on device sdc1, logical block 12825588
lost page write due to I/O error on sdc1
usb 2-1: reset high speed USB device using ehci_hcd and address 4
usb 2-1: reset high speed USB device using ehci_hcd and address 4
usb 2-1: reset high speed USB device using ehci_hcd and address 4
usb 2-1: reset high speed USB device using ehci_hcd and address 4
usb 2-1: reset high speed USB device using ehci_hcd and address 4
usb 2-1: reset high speed USB device using ehci_hcd and address 4
usb 2-1: device descriptor read/all, error 8
usb 2-1: reset high speed USB device using ehci_hcd and address 4
usb 2-1: device descriptor read/8, error -75
usb 2-1: device descriptor read/8, error -75
usb 2-1: reset high speed USB device using ehci_hcd and address 4
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102604775
Buffer I/O error on device sdc1, logical block 12825589
lost page write due to I/O error on sdc1
Buffer I/O error on device sdc1, logical block 12825590
lost page write due to I/O error on sdc1
usb 2-1: reset high speed USB device using ehci_hcd and address 4
usb 2-1: reset high speed USB device using ehci_hcd and address 4
usb 2-1: reset high speed USB device using ehci_hcd and address 4
usb 2-1: reset high speed USB device using ehci_hcd and address 4
usb 2-1: reset high speed USB device using ehci_hcd and address 4
usb 2-1: reset high speed USB device using ehci_hcd and address 4
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102604839
__ratelimit: 6 callbacks suppressed
Buffer I/O error on device sdc1, logical block 12825597
lost page write due to I/O error on sdc1
Buffer I/O error on device sdc1, logical block 12825598
lost page write due to I/O error on sdc1
Buffer I/O error on device sdc1, logical block 12825599
lost page write due to I/O error on sdc1
Buffer I/O error on device sdc1, logical block 12825600
lost page write due to I/O error on sdc1
Buffer I/O error on device sdc1, logical block 12825601
lost page write due to I/O error on sdc1
Buffer I/O error on device sdc1, logical block 12825602
lost page write due to I/O error on sdc1
Buffer I/O error on device sdc1, logical block 12825603
lost page write due to I/O error on sdc1
Buffer I/O error on device sdc1, logical block 12825604
lost page write due to I/O error on sdc1
usb 2-1: reset high speed USB device using ehci_hcd and address 4
usb 2-1: reset high speed USB device using ehci_hcd and address 4
usb 2-1: reset high speed USB device using ehci_hcd and address 4
usb 2-1: reset high speed USB device using ehci_hcd and address 4
usb 2-1: reset high speed USB device using ehci_hcd and address 4
usb 2-1: reset high speed USB device using ehci_hcd and address 4
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102604903
Buffer I/O error on device sdc1, logical block 12825605
lost page write due to I/O error on sdc1
Buffer I/O error on device sdc1, logical block 12825606
lost page write due to I/O error on sdc1
Buffer I/O error on device sdc1, logical block 12825607
lost page write due to I/O error on sdc1
Buffer I/O error on device sdc1, logical block 12825608
lost page write due to I/O error on sdc1
Buffer I/O error on device sdc1, logical block 12825609
lost page write due to I/O error on sdc1
Buffer I/O error on device sdc1, logical block 12825610
lost page write due to I/O error on sdc1
Buffer I/O error on device sdc1, logical block 12825611
lost page write due to I/O error on sdc1
Buffer I/O error on device sdc1, logical block 12825612
lost page write due to I/O error on sdc1
usb 2-1: reset high speed USB device using ehci_hcd and address 4
usb 2-1: reset high speed USB device using ehci_hcd and address 4
usb 2-1: reset high speed USB device using ehci_hcd and address 4
usb 2-1: reset high speed USB device using ehci_hcd and address 4
usb 2-1: reset high speed USB device using ehci_hcd and address 4
usb 2-1: reset high speed USB device using ehci_hcd and address 4
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102604967
Buffer I/O error on device sdc1, logical block 12825613
lost page write due to I/O error on sdc1
Buffer I/O error on device sdc1, logical block 12825614
lost page write due to I/O error on sdc1
Buffer I/O error on device sdc1, logical block 12825615
lost page write due to I/O error on sdc1
Buffer I/O error on device sdc1, logical block 12825616
lost page write due to I/O error on sdc1
Buffer I/O error on device sdc1, logical block 12825617
lost page write due to I/O error on sdc1
Buffer I/O error on device sdc1, logical block 12825618
lost page write due to I/O error on sdc1
Buffer I/O error on device sdc1, logical block 12825619
lost page write due to I/O error on sdc1
Buffer I/O error on device sdc1, logical block 12825620
lost page write due to I/O error on sdc1
usb 2-1: reset high speed USB device using ehci_hcd and address 4
usb 2-1: reset high speed USB device using ehci_hcd and address 4
usb 2-1: reset high speed USB device using ehci_hcd and address 4
usb 2-1: reset high speed USB device using ehci_hcd and address 4
usb 2-1: reset high speed USB device using ehci_hcd and address 4
usb 2-1: reset high speed USB device using ehci_hcd and address 4
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102605031
Buffer I/O error on device sdc1, logical block 12825621
lost page write due to I/O error on sdc1
Buffer I/O error on device sdc1, logical block 12825622
lost page write due to I/O error on sdc1
Buffer I/O error on device sdc1, logical block 12825623
lost page write due to I/O error on sdc1
Buffer I/O error on device sdc1, logical block 12825624
lost page write due to I/O error on sdc1
Buffer I/O error on device sdc1, logical block 12825625
lost page write due to I/O error on sdc1
Buffer I/O error on device sdc1, logical block 12825626
lost page write due to I/O error on sdc1
Buffer I/O error on device sdc1, logical block 12825627
lost page write due to I/O error on sdc1
Buffer I/O error on device sdc1, logical block 12825628
lost page write due to I/O error on sdc1
usb 2-1: reset high speed USB device using ehci_hcd and address 4
usb 2-1: reset high speed USB device using ehci_hcd and address 4
usb 2-1: device firmware changed
usb 2-1: USB disconnect, address 4
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102605095
Buffer I/O error on device sdc1, logical block 12825629
lost page write due to I/O error on sdc1
Buffer I/O error on device sdc1, logical block 12825630
lost page write due to I/O error on sdc1
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102605159
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102605223
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102605287
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102789503
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102789567
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102605351
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102605415
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102605479
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102605543
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102605607
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102605671
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102605735
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102605799
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102605863
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102605927
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102605991
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102606055
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102606119
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102606183
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102606247
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102606311
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102606375
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102606439
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102606503
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102606567
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102606631
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102606695
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102606759
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102606823
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102606887
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102606951
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102607015
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102607079
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102607143
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102607207
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102607271
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102607335
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102607399
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102607463
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102607527
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102607591
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102607655
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102607719
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102607783
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102607847
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102607911
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102607975
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102608039
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102608111
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102608175
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102608239
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102608303
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102608367
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102608431
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102608495
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102608559
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102608623
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102608687
sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102608751
sd 6:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102608815
sd 6:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdc, sector 102608879
ext3_journal_dirty_data: aborting transaction: IO failure in ext3_journal_dirty_data
EXT3-fs error (device sdc1) in ext3_ordered_writepage: IO failure
ext3_journal_dirty_data: aborting transaction: IO failure in ext3_journal_dirty_data
EXT3-fs error (device sdc1) in ext3_ordered_writepage: IO failure
JBD: Detected IO errors while flushing file data on sdc1
Aborting journal on device sdc1.
EXT3-fs error (device sdc1) in ext3_ordered_writepage: IO failure
ext3_abort called.
EXT3-fs error (device sdc1): ext3_journal_start_sb: Detected aborted journal
Remounting filesystem read-only
JBD: Detected IO errors while flushing file data on sdc1
__journal_remove_journal_head: freeing b_committed_data
usb 2-1: new high speed USB device using ehci_hcd and address 5
usb 2-1: device descriptor read/8, error -75
usb 2-1: device descriptor read/8, error -75
usb 2-1: new high speed USB device using ehci_hcd and address 6
usb 2-1: device descriptor read/8, error -75
usb 2-1: device descriptor read/8, error -75
usb 2-1: new high speed USB device using ehci_hcd and address 7
usb 2-1: configuration #1 chosen from 1 choice
scsi7 : SCSI emulation for USB Mass Storage devices
usb 2-1: New USB device found, idVendor=04fc, idProduct=0c25
usb 2-1: New USB device strings: Mfr=2, Product=3, SerialNumber=1
usb 2-1: Product: USB to Serial-ATA bridge
usb 2-1: Manufacturer: Sunplus Technology Inc.
usb 2-1: SerialNumber: ST9160821A5MA3LZVC            
usb-storage: device found at 7
usb-storage: waiting for device to settle before scanning
EXT3-fs error (device sdc1): ext3_find_entry: reading directory #2 offset 0
usb 2-1: reset high speed USB device using ehci_hcd and address 7
usb 2-1: reset high speed USB device using ehci_hcd and address 7
usb 2-1: device firmware changed
usb 2-1: USB disconnect, address 7
usb-storage: device scan complete
usb 2-1: new high speed USB device using ehci_hcd and address 8
usb 2-1: device descriptor read/8, error -75
usb 2-1: device descriptor read/8, error -75
usb 2-1: new high speed USB device using ehci_hcd and address 9
usb 2-1: device descriptor read/8, error -75
usb 2-1: device descriptor read/8, error -75
usb 2-1: new high speed USB device using ehci_hcd and address 10
usb 2-1: configuration #1 chosen from 1 choice
scsi8 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 10
usb-storage: waiting for device to settle before scanning
usb 2-1: New USB device found, idVendor=04fc, idProduct=0c25
usb 2-1: New USB device strings: Mfr=2, Product=3, SerialNumber=1
usb 2-1: Product: USB to Serial-ATA bridge
usb 2-1: Manufacturer: Sunplus Technology Inc.
usb 2-1: SerialNumber: ST9160821A5MA3LZVC            
usb 2-1: reset high speed USB device using ehci_hcd and address 10
usb 2-1: reset high speed USB device using ehci_hcd and address 10
usb 2-1: reset high speed USB device using ehci_hcd and address 10
EXT3-fs error (device sdc1): ext3_find_entry: reading directory #2 offset 0
EXT3-fs error (device sdc1): ext3_find_entry: reading directory #2 offset 0
EXT3-fs error (device sdc1): ext3_find_entry: reading directory #2 offset 0
usb 2-1: reset high speed USB device using ehci_hcd and address 10
usb-storage: device scan complete
__ratelimit: 25471 callbacks suppressed
Buffer I/O error on device sdc1, logical block 12746753
lost page write due to I/O error on sdc1
Buffer I/O error on device sdc1, logical block 12746754
lost page write due to I/O error on sdc1
Buffer I/O error on device sdc1, logical block 12746755
lost page write due to I/O error on sdc1
Buffer I/O error on device sdc1, logical block 12767638
lost page write due to I/O error on sdc1
Buffer I/O error on device sdc1, logical block 12812288
lost page write due to I/O error on sdc1
Buffer I/O error on device sdc1, logical block 4
lost page write due to I/O error on sdc1
Buffer I/O error on device sdc1, logical block 12831448
lost page write due to I/O error on sdc1
Buffer I/O error on device sdc1, logical block 12839649
lost page write due to I/O error on sdc1
Buffer I/O error on device sdc1, logical block 12840674
lost page write due to I/O error on sdc1
Buffer I/O error on device sdc1, logical block 12841699
lost page write due to I/O error on sdc1
usb 2-1: USB disconnect, address 10

---

