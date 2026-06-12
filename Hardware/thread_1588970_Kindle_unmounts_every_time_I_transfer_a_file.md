---
title: "Kindle unmounts every time I transfer a file"
date: 2010-10-05
forum: Hardware
---

### Post by last1 on 2010-10-05
When I plug in my Kindle it asks me if I want it to mount, which it does successfully, then I transfer a file to it. The file does not transfer though I get a message that it did, then the device unmounts. The Kindle doesn't show the new file. In my system log I see lots of errors about I/O, which I have included below. Last I checked I had no problems transferring files from WinXP. 

```

2010-10-05 14:06:49	kaadoke	kernel	[   69.992075] usb 1-6: new high speed USB device using ehci_hcd and address 6
2010-10-05 14:06:50	kaadoke	kernel	[   70.136271] usb 1-6: configuration #1 chosen from 1 choice
2010-10-05 14:06:50	kaadoke	kernel	[   70.144183] scsi5 : SCSI emulation for USB Mass Storage devices
2010-10-05 14:06:50	kaadoke	kernel	[   70.144299] usb-storage: device found at 6
2010-10-05 14:06:50	kaadoke	kernel	[   70.144301] usb-storage: waiting for device to settle before scanning
2010-10-05 14:06:55	kaadoke	kernel	[   75.145127] usb-storage: device scan complete
2010-10-05 14:06:55	kaadoke	kernel	[   75.146365] scsi 5:0:0:0: Direct-Access     Kindle   Internal Storage 0100 PQ: 0 ANSI: 2
2010-10-05 14:06:55	kaadoke	kernel	[   75.146842] sd 5:0:0:0: Attached scsi generic sg7 type 0
2010-10-05 14:06:55	kaadoke	kernel	[   75.154664] sd 5:0:0:0: [sdg] 7143360 512-byte logical blocks: (3.65 GB/3.40 GiB)
2010-10-05 14:06:55	kaadoke	kernel	[   75.256112] sd 5:0:0:0: [sdg] Write Protect is off
2010-10-05 14:06:55	kaadoke	kernel	[   75.256117] sd 5:0:0:0: [sdg] Mode Sense: 0f 00 00 00
2010-10-05 14:06:55	kaadoke	kernel	[   75.256119] sd 5:0:0:0: [sdg] Assuming drive cache: write through
2010-10-05 14:06:55	kaadoke	kernel	[   75.362745] sd 5:0:0:0: [sdg] Assuming drive cache: write through
2010-10-05 14:06:55	kaadoke	kernel	[   75.362751]  sdg: sdg1
2010-10-05 14:06:55	kaadoke	kernel	[   75.472758] sd 5:0:0:0: [sdg] Assuming drive cache: write through
2010-10-05 14:06:55	kaadoke	kernel	[   75.472763] sd 5:0:0:0: [sdg] Attached SCSI removable disk
2010-10-05 14:06:55	kaadoke	hald	mounted /dev/sdg1 on behalf of uid 1000
2010-10-05 14:07:25	kaadoke	kernel	[  105.105527] usb 1-6: USB disconnect, address 6
2010-10-05 14:07:25	kaadoke	kernel	[  105.105666] sd 5:0:0:0: [sdg] Unhandled error code
2010-10-05 14:07:25	kaadoke	kernel	[  105.105669] sd 5:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 14:07:25	kaadoke	kernel	[  105.105672] sd 5:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 c3 fe 00 00 f0 00
2010-10-05 14:07:25	kaadoke	kernel	[  105.105681] end_request: I/O error, dev sdg, sector 3326974
2010-10-05 14:07:25	kaadoke	kernel	[  105.105730] sd 5:0:0:0: [sdg] Unhandled error code
2010-10-05 14:07:25	kaadoke	kernel	[  105.105732] sd 5:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 14:07:25	kaadoke	kernel	[  105.105735] sd 5:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 c4 ee 00 00 f0 00
2010-10-05 14:07:25	kaadoke	kernel	[  105.105743] end_request: I/O error, dev sdg, sector 3327214
2010-10-05 14:07:25	kaadoke	kernel	[  105.105791] sd 5:0:0:0: [sdg] Unhandled error code
2010-10-05 14:07:25	kaadoke	kernel	[  105.105793] sd 5:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 14:07:25	kaadoke	kernel	[  105.105795] sd 5:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 c5 de 00 00 f0 00
2010-10-05 14:07:25	kaadoke	kernel	[  105.105803] end_request: I/O error, dev sdg, sector 3327454
2010-10-05 14:07:25	kaadoke	kernel	[  105.105845] sd 5:0:0:0: [sdg] Unhandled error code
2010-10-05 14:07:25	kaadoke	kernel	[  105.105847] sd 5:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 14:07:25	kaadoke	kernel	[  105.105850] sd 5:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 c6 ce 00 00 f0 00
2010-10-05 14:07:25	kaadoke	kernel	[  105.105858] end_request: I/O error, dev sdg, sector 3327694
2010-10-05 14:07:25	kaadoke	kernel	[  105.105901] sd 5:0:0:0: [sdg] Unhandled error code
2010-10-05 14:07:25	kaadoke	kernel	[  105.105903] sd 5:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 14:07:25	kaadoke	kernel	[  105.105905] sd 5:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 c7 be 00 00 f0 00
2010-10-05 14:07:25	kaadoke	kernel	[  105.105913] end_request: I/O error, dev sdg, sector 3327934
2010-10-05 14:07:25	kaadoke	kernel	[  105.105956] sd 5:0:0:0: [sdg] Unhandled error code
2010-10-05 14:07:25	kaadoke	kernel	[  105.105958] sd 5:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 14:07:25	kaadoke	kernel	[  105.105961] sd 5:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 c8 ae 00 00 f0 00
2010-10-05 14:07:25	kaadoke	kernel	[  105.105969] end_request: I/O error, dev sdg, sector 3328174
2010-10-05 14:07:25	kaadoke	kernel	[  105.106012] sd 5:0:0:0: [sdg] Unhandled error code
2010-10-05 14:07:25	kaadoke	kernel	[  105.106014] sd 5:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 14:07:25	kaadoke	kernel	[  105.106016] sd 5:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 c9 9e 00 00 f0 00
2010-10-05 14:07:25	kaadoke	kernel	[  105.106024] end_request: I/O error, dev sdg, sector 3328414
2010-10-05 14:07:25	kaadoke	kernel	[  105.106066] sd 5:0:0:0: [sdg] Unhandled error code
2010-10-05 14:07:25	kaadoke	kernel	[  105.106068] sd 5:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 14:07:25	kaadoke	kernel	[  105.106071] sd 5:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 ca 8e 00 00 f0 00
2010-10-05 14:07:25	kaadoke	kernel	[  105.106078] end_request: I/O error, dev sdg, sector 3328654
2010-10-05 14:07:25	kaadoke	kernel	[  105.106121] sd 5:0:0:0: [sdg] Unhandled error code
2010-10-05 14:07:25	kaadoke	kernel	[  105.106123] sd 5:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 14:07:25	kaadoke	kernel	[  105.106125] sd 5:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 cb 7e 00 00 f0 00
2010-10-05 14:07:25	kaadoke	kernel	[  105.106133] end_request: I/O error, dev sdg, sector 3328894
2010-10-05 14:07:25	kaadoke	kernel	[  105.106175] sd 5:0:0:0: [sdg] Unhandled error code
2010-10-05 14:07:25	kaadoke	kernel	[  105.106177] sd 5:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 14:07:25	kaadoke	kernel	[  105.106180] sd 5:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 cc 6e 00 00 f0 00
2010-10-05 14:07:25	kaadoke	kernel	[  105.106188] end_request: I/O error, dev sdg, sector 3329134
2010-10-05 14:07:25	kaadoke	kernel	[  105.106229] sd 5:0:0:0: [sdg] Unhandled error code
2010-10-05 14:07:25	kaadoke	kernel	[  105.106231] sd 5:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 14:07:25	kaadoke	kernel	[  105.106234] sd 5:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 cd 5e 00 00 f0 00
2010-10-05 14:07:25	kaadoke	kernel	[  105.106242] end_request: I/O error, dev sdg, sector 3329374
2010-10-05 14:07:25	kaadoke	kernel	[  105.106284] sd 5:0:0:0: [sdg] Unhandled error code
2010-10-05 14:07:25	kaadoke	kernel	[  105.106285] sd 5:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 14:07:25	kaadoke	kernel	[  105.106288] sd 5:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 ce 4e 00 00 f0 00
2010-10-05 14:07:25	kaadoke	kernel	[  105.106296] end_request: I/O error, dev sdg, sector 3329614
2010-10-05 14:07:25	kaadoke	kernel	[  105.106337] sd 5:0:0:0: [sdg] Unhandled error code
2010-10-05 14:07:25	kaadoke	kernel	[  105.106339] sd 5:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 14:07:25	kaadoke	kernel	[  105.106342] sd 5:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 cf 3e 00 00 f0 00
2010-10-05 14:07:25	kaadoke	kernel	[  105.106349] end_request: I/O error, dev sdg, sector 3329854
2010-10-05 14:07:25	kaadoke	kernel	[  105.106392] sd 5:0:0:0: [sdg] Unhandled error code
2010-10-05 14:07:25	kaadoke	kernel	[  105.106394] sd 5:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 14:07:25	kaadoke	kernel	[  105.106397] sd 5:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 d0 2e 00 00 f0 00
2010-10-05 14:07:25	kaadoke	kernel	[  105.106404] end_request: I/O error, dev sdg, sector 3330094
2010-10-05 14:07:25	kaadoke	kernel	[  105.106446] sd 5:0:0:0: [sdg] Unhandled error code
2010-10-05 14:07:25	kaadoke	kernel	[  105.106448] sd 5:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 14:07:25	kaadoke	kernel	[  105.106451] sd 5:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 d1 1e 00 00 f0 00
2010-10-05 14:07:25	kaadoke	kernel	[  105.106458] end_request: I/O error, dev sdg, sector 3330334
2010-10-05 14:07:25	kaadoke	kernel	[  105.106501] sd 5:0:0:0: [sdg] Unhandled error code
2010-10-05 14:07:25	kaadoke	kernel	[  105.106502] sd 5:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 14:07:25	kaadoke	kernel	[  105.106505] sd 5:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 d2 0e 00 00 f0 00
2010-10-05 14:07:25	kaadoke	kernel	[  105.106513] end_request: I/O error, dev sdg, sector 3330574
2010-10-05 14:07:25	kaadoke	kernel	[  105.106556] sd 5:0:0:0: [sdg] Unhandled error code
2010-10-05 14:07:25	kaadoke	kernel	[  105.106558] sd 5:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 14:07:25	kaadoke	kernel	[  105.106560] sd 5:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 d2 fe 00 00 f0 00
2010-10-05 14:07:25	kaadoke	kernel	[  105.106568] end_request: I/O error, dev sdg, sector 3330814
2010-10-05 14:07:25	kaadoke	kernel	[  105.106610] sd 5:0:0:0: [sdg] Unhandled error code
2010-10-05 14:07:25	kaadoke	kernel	[  105.106612] sd 5:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 14:07:25	kaadoke	kernel	[  105.106615] sd 5:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 d3 ee 00 00 f0 00
2010-10-05 14:07:25	kaadoke	kernel	[  105.106623] end_request: I/O error, dev sdg, sector 3331054
2010-10-05 14:07:25	kaadoke	kernel	[  105.106665] sd 5:0:0:0: [sdg] Unhandled error code
2010-10-05 14:07:25	kaadoke	kernel	[  105.106667] sd 5:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 14:07:25	kaadoke	kernel	[  105.106669] sd 5:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 d4 de 00 00 f0 00
2010-10-05 14:07:25	kaadoke	kernel	[  105.106677] end_request: I/O error, dev sdg, sector 3331294
2010-10-05 14:07:25	kaadoke	kernel	[  105.106719] sd 5:0:0:0: [sdg] Unhandled error code
2010-10-05 14:07:25	kaadoke	kernel	[  105.106721] sd 5:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 14:07:25	kaadoke	kernel	[  105.106724] sd 5:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 d5 ce 00 00 f0 00
2010-10-05 14:07:25	kaadoke	kernel	[  105.106732] end_request: I/O error, dev sdg, sector 3331534
2010-10-05 14:07:25	kaadoke	kernel	[  105.106773] sd 5:0:0:0: [sdg] Unhandled error code
2010-10-05 14:07:25	kaadoke	kernel	[  105.106775] sd 5:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 14:07:25	kaadoke	kernel	[  105.106778] sd 5:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 d6 be 00 00 f0 00
2010-10-05 14:07:25	kaadoke	kernel	[  105.106786] end_request: I/O error, dev sdg, sector 3331774
2010-10-05 14:07:25	kaadoke	kernel	[  105.106828] sd 5:0:0:0: [sdg] Unhandled error code
2010-10-05 14:07:25	kaadoke	kernel	[  105.106830] sd 5:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 14:07:25	kaadoke	kernel	[  105.106832] sd 5:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 d7 ae 00 00 f0 00
2010-10-05 14:07:25	kaadoke	kernel	[  105.106840] end_request: I/O error, dev sdg, sector 3332014
2010-10-05 14:07:25	kaadoke	kernel	[  105.106882] sd 5:0:0:0: [sdg] Unhandled error code
2010-10-05 14:07:25	kaadoke	kernel	[  105.106883] sd 5:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 14:07:25	kaadoke	kernel	[  105.106886] sd 5:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 d8 9e 00 00 f0 00
2010-10-05 14:07:25	kaadoke	kernel	[  105.106894] end_request: I/O error, dev sdg, sector 3332254
2010-10-05 14:07:25	kaadoke	kernel	[  105.106936] sd 5:0:0:0: [sdg] Unhandled error code
2010-10-05 14:07:25	kaadoke	kernel	[  105.106938] sd 5:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 14:07:25	kaadoke	kernel	[  105.106941] sd 5:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 d9 8e 00 00 f0 00
2010-10-05 14:07:25	kaadoke	kernel	[  105.106949] end_request: I/O error, dev sdg, sector 3332494
2010-10-05 14:07:25	kaadoke	kernel	[  105.106990] sd 5:0:0:0: [sdg] Unhandled error code
2010-10-05 14:07:25	kaadoke	kernel	[  105.106992] sd 5:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 14:07:25	kaadoke	kernel	[  105.106995] sd 5:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 da 7e 00 00 f0 00
2010-10-05 14:07:25	kaadoke	kernel	[  105.107003] end_request: I/O error, dev sdg, sector 3332734
2010-10-05 14:07:25	kaadoke	kernel	[  105.107044] sd 5:0:0:0: [sdg] Unhandled error code
2010-10-05 14:07:25	kaadoke	kernel	[  105.107046] sd 5:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 14:07:25	kaadoke	kernel	[  105.107049] sd 5:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 db 6e 00 00 f0 00
2010-10-05 14:07:25	kaadoke	kernel	[  105.107057] end_request: I/O error, dev sdg, sector 3332974
2010-10-05 14:07:25	kaadoke	kernel	[  105.107099] sd 5:0:0:0: [sdg] Unhandled error code
2010-10-05 14:07:25	kaadoke	kernel	[  105.107100] sd 5:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 14:07:25	kaadoke	kernel	[  105.107103] sd 5:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 dc 5e 00 00 f0 00
2010-10-05 14:07:25	kaadoke	kernel	[  105.107111] end_request: I/O error, dev sdg, sector 3333214
2010-10-05 14:07:25	kaadoke	kernel	[  105.107153] sd 5:0:0:0: [sdg] Unhandled error code
2010-10-05 14:07:25	kaadoke	kernel	[  105.107154] sd 5:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 14:07:25	kaadoke	kernel	[  105.107157] sd 5:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 dd 4e 00 00 f0 00
2010-10-05 14:07:25	kaadoke	kernel	[  105.107165] end_request: I/O error, dev sdg, sector 3333454
2010-10-05 14:07:25	kaadoke	kernel	[  105.107207] sd 5:0:0:0: [sdg] Unhandled error code
2010-10-05 14:07:25	kaadoke	kernel	[  105.107209] sd 5:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 14:07:25	kaadoke	kernel	[  105.107211] sd 5:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 de 3e 00 00 f0 00
2010-10-05 14:07:25	kaadoke	kernel	[  105.107219] end_request: I/O error, dev sdg, sector 3333694
2010-10-05 14:07:25	kaadoke	kernel	[  105.107261] sd 5:0:0:0: [sdg] Unhandled error code
2010-10-05 14:07:25	kaadoke	kernel	[  105.107263] sd 5:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 14:07:25	kaadoke	kernel	[  105.107265] sd 5:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 df 2e 00 00 f0 00
2010-10-05 14:07:25	kaadoke	kernel	[  105.107273] end_request: I/O error, dev sdg, sector 3333934
2010-10-05 14:07:25	kaadoke	kernel	[  105.107316] sd 5:0:0:0: [sdg] Unhandled error code
2010-10-05 14:07:25	kaadoke	kernel	[  105.107318] sd 5:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 14:07:25	kaadoke	kernel	[  105.107320] sd 5:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 e0 1e 00 00 f0 00
2010-10-05 14:07:25	kaadoke	kernel	[  105.107328] end_request: I/O error, dev sdg, sector 3334174
2010-10-05 14:07:25	kaadoke	kernel	[  105.107370] sd 5:0:0:0: [sdg] Unhandled error code
2010-10-05 14:07:25	kaadoke	kernel	[  105.107371] sd 5:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 14:07:25	kaadoke	kernel	[  105.107374] sd 5:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 e1 0e 00 00 f0 00
2010-10-05 14:07:25	kaadoke	kernel	[  105.107382] end_request: I/O error, dev sdg, sector 3334414
2010-10-05 14:07:25	kaadoke	kernel	[  105.107424] sd 5:0:0:0: [sdg] Unhandled error code
2010-10-05 14:07:25	kaadoke	kernel	[  105.107426] sd 5:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 14:07:25	kaadoke	kernel	[  105.107428] sd 5:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 e1 fe 00 00 f0 00
2010-10-05 14:07:25	kaadoke	kernel	[  105.107436] end_request: I/O error, dev sdg, sector 3334654
2010-10-05 14:07:25	kaadoke	kernel	[  105.107479] sd 5:0:0:0: [sdg] Unhandled error code
2010-10-05 14:07:25	kaadoke	kernel	[  105.107481] sd 5:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 14:07:25	kaadoke	kernel	[  105.107484] sd 5:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 e2 ee 00 00 f0 00
2010-10-05 14:07:25	kaadoke	kernel	[  105.107491] end_request: I/O error, dev sdg, sector 3334894
2010-10-05 14:07:25	kaadoke	kernel	[  105.107535] sd 5:0:0:0: [sdg] Unhandled error code
2010-10-05 14:07:25	kaadoke	kernel	[  105.107536] sd 5:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 14:07:25	kaadoke	kernel	[  105.107539] sd 5:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 e3 de 00 00 f0 00
2010-10-05 14:07:25	kaadoke	kernel	[  105.107547] end_request: I/O error, dev sdg, sector 3335134
2010-10-05 14:07:25	kaadoke	kernel	[  105.107589] sd 5:0:0:0: [sdg] Unhandled error code
2010-10-05 14:07:25	kaadoke	kernel	[  105.107590] sd 5:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 14:07:25	kaadoke	kernel	[  105.107593] sd 5:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 e4 ce 00 00 f0 00
2010-10-05 14:07:25	kaadoke	kernel	[  105.107601] end_request: I/O error, dev sdg, sector 3335374
2010-10-05 14:07:25	kaadoke	kernel	[  105.107647] sd 5:0:0:0: [sdg] Unhandled error code
2010-10-05 14:07:25	kaadoke	kernel	[  105.107649] sd 5:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 14:07:25	kaadoke	kernel	[  105.107652] sd 5:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 e5 be 00 00 f0 00
2010-10-05 14:07:25	kaadoke	kernel	[  105.107660] end_request: I/O error, dev sdg, sector 3335614
2010-10-05 14:07:25	kaadoke	kernel	[  105.107702] sd 5:0:0:0: [sdg] Unhandled error code
2010-10-05 14:07:25	kaadoke	kernel	[  105.107704] sd 5:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 14:07:25	kaadoke	kernel	[  105.107706] sd 5:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 e6 ae 00 00 f0 00
2010-10-05 14:07:25	kaadoke	kernel	[  105.107714] end_request: I/O error, dev sdg, sector 3335854
2010-10-05 14:07:25	kaadoke	kernel	[  105.107757] sd 5:0:0:0: [sdg] Unhandled error code
2010-10-05 14:07:25	kaadoke	kernel	[  105.107759] sd 5:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 14:07:25	kaadoke	kernel	[  105.107761] sd 5:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 e7 9e 00 00 f0 00
2010-10-05 14:07:25	kaadoke	kernel	[  105.107769] end_request: I/O error, dev sdg, sector 3336094
2010-10-05 14:07:25	kaadoke	kernel	[  105.107812] sd 5:0:0:0: [sdg] Unhandled error code
2010-10-05 14:07:25	kaadoke	kernel	[  105.107813] sd 5:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 14:07:25	kaadoke	kernel	[  105.107816] sd 5:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 e8 8e 00 00 f0 00
2010-10-05 14:07:25	kaadoke	kernel	[  105.107824] end_request: I/O error, dev sdg, sector 3336334
2010-10-05 14:07:25	kaadoke	kernel	[  105.107866] sd 5:0:0:0: [sdg] Unhandled error code
2010-10-05 14:07:25	kaadoke	kernel	[  105.107868] sd 5:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 14:07:25	kaadoke	kernel	[  105.107870] sd 5:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 e9 7e 00 00 f0 00
2010-10-05 14:07:25	kaadoke	kernel	[  105.107879] end_request: I/O error, dev sdg, sector 3336574
2010-10-05 14:07:25	kaadoke	kernel	[  105.107920] sd 5:0:0:0: [sdg] Unhandled error code
2010-10-05 14:07:25	kaadoke	kernel	[  105.107922] sd 5:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 14:07:25	kaadoke	kernel	[  105.107925] sd 5:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 ea 6e 00 00 f0 00
2010-10-05 14:07:25	kaadoke	kernel	[  105.107933] end_request: I/O error, dev sdg, sector 3336814
2010-10-05 14:07:25	kaadoke	kernel	[  105.107976] sd 5:0:0:0: [sdg] Unhandled error code
2010-10-05 14:07:25	kaadoke	kernel	[  105.107978] sd 5:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 14:07:25	kaadoke	kernel	[  105.107981] sd 5:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 eb 5e 00 00 f0 00
2010-10-05 14:07:25	kaadoke	kernel	[  105.107988] end_request: I/O error, dev sdg, sector 3337054
2010-10-05 14:07:25	kaadoke	kernel	[  105.108032] sd 5:0:0:0: [sdg] Unhandled error code
2010-10-05 14:07:25	kaadoke	kernel	[  105.108034] sd 5:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 14:07:25	kaadoke	kernel	[  105.108036] sd 5:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 ec 4e 00 00 f0 00
2010-10-05 14:07:25	kaadoke	kernel	[  105.108044] end_request: I/O error, dev sdg, sector 3337294
2010-10-05 14:07:25	kaadoke	kernel	[  105.108085] sd 5:0:0:0: [sdg] Unhandled error code
2010-10-05 14:07:25	kaadoke	kernel	[  105.108088] sd 5:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 14:07:25	kaadoke	kernel	[  105.108092] sd 5:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 ed 3e 00 00 f0 00
2010-10-05 14:07:25	kaadoke	kernel	[  105.108115] end_request: I/O error, dev sdg, sector 3337534
2010-10-05 14:07:25	kaadoke	kernel	[  105.108155] sd 5:0:0:0: [sdg] Unhandled error code
2010-10-05 14:07:25	kaadoke	kernel	[  105.108158] sd 5:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 14:07:25	kaadoke	kernel	[  105.108163] sd 5:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 ee 2e 00 00 23 00
2010-10-05 14:07:25	kaadoke	kernel	[  105.108185] end_request: I/O error, dev sdg, sector 3337774
2010-10-05 14:07:25	kaadoke	kernel	[  105.108228] sd 5:0:0:0: [sdg] Unhandled error code
2010-10-05 14:07:25	kaadoke	kernel	[  105.108231] sd 5:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 14:07:25	kaadoke	kernel	[  105.108235] sd 5:0:0:0: [sdg] CDB: Write(10): 2a 00 00 00 00 11 00 00 01 00
2010-10-05 14:07:25	kaadoke	kernel	[  105.108258] end_request: I/O error, dev sdg, sector 17
2010-10-05 14:07:25	kaadoke	kernel	[  105.108262] Buffer I/O error on device sdg1, logical block 1
2010-10-05 14:07:25	kaadoke	kernel	[  105.108265] lost page write due to I/O error on sdg1
2010-10-05 14:07:25	kaadoke	kernel	[  105.108309] sd 5:0:0:0: [sdg] Unhandled error code
2010-10-05 14:07:25	kaadoke	kernel	[  105.108312] sd 5:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 14:07:25	kaadoke	kernel	[  105.108316] sd 5:0:0:0: [sdg] CDB: Write(10): 2a 00 00 00 0c 9d 00 00 41 00
2010-10-05 14:07:25	kaadoke	kernel	[  105.108339] end_request: I/O error, dev sdg, sector 3229
2010-10-05 14:07:25	kaadoke	kernel	[  105.108342] Buffer I/O error on device sdg1, logical block 3213
2010-10-05 14:07:25	kaadoke	kernel	[  105.108345] lost page write due to I/O error on sdg1
2010-10-05 14:07:25	kaadoke	kernel	[  105.108348] Buffer I/O error on device sdg1, logical block 3214
2010-10-05 14:07:25	kaadoke	kernel	[  105.108351] lost page write due to I/O error on sdg1
2010-10-05 14:07:25	kaadoke	kernel	[  105.108355] Buffer I/O error on device sdg1, logical block 3215
2010-10-05 14:07:25	kaadoke	kernel	[  105.108358] lost page write due to I/O error on sdg1
2010-10-05 14:07:25	kaadoke	kernel	[  105.108362] Buffer I/O error on device sdg1, logical block 3216
2010-10-05 14:07:25	kaadoke	kernel	[  105.108364] lost page write due to I/O error on sdg1
2010-10-05 14:07:25	kaadoke	kernel	[  105.108368] Buffer I/O error on device sdg1, logical block 3217
2010-10-05 14:07:25	kaadoke	kernel	[  105.108370] lost page write due to I/O error on sdg1
2010-10-05 14:07:25	kaadoke	kernel	[  105.108374] Buffer I/O error on device sdg1, logical block 3218
2010-10-05 14:07:25	kaadoke	kernel	[  105.108376] lost page write due to I/O error on sdg1
2010-10-05 14:07:25	kaadoke	kernel	[  105.108379] Buffer I/O error on device sdg1, logical block 3219
2010-10-05 14:07:25	kaadoke	kernel	[  105.108382] lost page write due to I/O error on sdg1
2010-10-05 14:07:25	kaadoke	kernel	[  105.108385] Buffer I/O error on device sdg1, logical block 3220
2010-10-05 14:07:25	kaadoke	kernel	[  105.108388] lost page write due to I/O error on sdg1
2010-10-05 14:07:25	kaadoke	kernel	[  105.108391] Buffer I/O error on device sdg1, logical block 3221
2010-10-05 14:07:25	kaadoke	kernel	[  105.108394] lost page write due to I/O error on sdg1
2010-10-05 14:07:25	kaadoke	kernel	[  105.108456] sd 5:0:0:0: [sdg] Unhandled error code
2010-10-05 14:07:25	kaadoke	kernel	[  105.108458] sd 5:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 14:07:25	kaadoke	kernel	[  105.108463] sd 5:0:0:0: [sdg] CDB: Write(10): 2a 00 00 00 27 d0 00 00 41 00
2010-10-05 14:07:25	kaadoke	kernel	[  105.108486] end_request: I/O error, dev sdg, sector 10192
2010-10-05 14:07:25	kaadoke	kernel	[  105.108563] sd 5:0:0:0: [sdg] Unhandled error code
2010-10-05 14:07:25	kaadoke	kernel	[  105.108565] sd 5:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 14:07:25	kaadoke	kernel	[  105.108568] sd 5:0:0:0: [sdg] CDB: Write(10): 2a 00 00 00 36 a6 00 00 01 00
2010-10-05 14:07:25	kaadoke	kernel	[  105.108576] end_request: I/O error, dev sdg, sector 13990
2010-10-05 14:07:25	kaadoke	kernel	[  105.109170] FAT: unable to read inode block for updating (i_pos 223591)
2010-10-05 14:07:25	kaadoke	hald[2464]	forcibly attempting to lazy unmount /dev/sdg1 as enclosing drive was disconnected
2010-10-05 14:07:25	kaadoke	kernel	[  105.161391] FAT: Directory bread(block 13958) failed
2010-10-05 14:07:25	kaadoke	kernel	[  105.161400] FAT: Directory bread(block 13959) failed
2010-10-05 14:07:25	kaadoke	kernel	[  105.161407] FAT: Directory bread(block 13960) failed
2010-10-05 14:07:25	kaadoke	kernel	[  105.161414] FAT: Directory bread(block 13961) failed
2010-10-05 14:07:25	kaadoke	kernel	[  105.161420] FAT: Directory bread(block 13962) failed
2010-10-05 14:07:25	kaadoke	kernel	[  105.161426] FAT: Directory bread(block 13963) failed
2010-10-05 14:07:25	kaadoke	kernel	[  105.161432] FAT: Directory bread(block 13964) failed
2010-10-05 14:07:25	kaadoke	kernel	[  105.161439] FAT: Directory bread(block 13965) failed
2010-10-05 14:07:25	kaadoke	hald	unmounted /dev/sdg1 from '/media/Kindle' on behalf of uid 0
2010-10-05 14:07:25	kaadoke	kernel	[  105.380039] usb 1-6: new high speed USB device using ehci_hcd and address 7
2010-10-05 14:07:25	kaadoke	kernel	[  105.522314] usb 1-6: configuration #1 chosen from 1 choice
2010-10-05 14:07:30	kaadoke	kernel	[  110.520109] usb 1-6: can't set config #1, error -110
2010-10-05 14:07:55	kaadoke	kernel	[  135.216228] usb 1-6: USB disconnect, address 7

```

---

### Post by S.R on 2010-10-05
Try mounting it manually.

---

### Post by last1 on 2010-10-05
The transfer completes more than it does otherwise since the file shows up on the Kindle, but cannot be read so it still failed. It also still disconnects afterward, but then it automatically mounts again. The log is basically the same. 
```

2010-10-05 17:25:55	kaadoke	kernel	[ 9629.768635] usb 1-6: USB disconnect, address 7
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.768776] sd 6:0:0:0: [sdg] Unhandled error code
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.768779] sd 6:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.768785] sd 6:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 1b fe 00 00 f0 00
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.768798] end_request: I/O error, dev sdg, sector 3283966
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.768865] sd 6:0:0:0: [sdg] Unhandled error code
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.768868] sd 6:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.768872] sd 6:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 1c ee 00 00 f0 00
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.768884] end_request: I/O error, dev sdg, sector 3284206
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.768949] sd 6:0:0:0: [sdg] Unhandled error code
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.768952] sd 6:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.768956] sd 6:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 1d de 00 00 f0 00
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.768967] end_request: I/O error, dev sdg, sector 3284446
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.769031] sd 6:0:0:0: [sdg] Unhandled error code
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.769034] sd 6:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.769040] sd 6:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 1e ce 00 00 f0 00
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.769052] end_request: I/O error, dev sdg, sector 3284686
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.769200] sd 6:0:0:0: [sdg] Unhandled error code
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.769203] sd 6:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.769207] sd 6:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 1f be 00 00 f0 00
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.769219] end_request: I/O error, dev sdg, sector 3284926
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.769283] sd 6:0:0:0: [sdg] Unhandled error code
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.769286] sd 6:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.769290] sd 6:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 20 ae 00 00 f0 00
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.769301] end_request: I/O error, dev sdg, sector 3285166
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.769364] sd 6:0:0:0: [sdg] Unhandled error code
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.769366] sd 6:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.769370] sd 6:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 21 9e 00 00 f0 00
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.769382] end_request: I/O error, dev sdg, sector 3285406
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.769444] sd 6:0:0:0: [sdg] Unhandled error code
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.769447] sd 6:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.769451] sd 6:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 22 8e 00 00 f0 00
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.769463] end_request: I/O error, dev sdg, sector 3285646
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.769525] sd 6:0:0:0: [sdg] Unhandled error code
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.769528] sd 6:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.769532] sd 6:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 23 7e 00 00 f0 00
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.769544] end_request: I/O error, dev sdg, sector 3285886
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.770912] sd 6:0:0:0: [sdg] Unhandled error code
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.770915] sd 6:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.770919] sd 6:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 24 6e 00 00 f0 00
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.770931] end_request: I/O error, dev sdg, sector 3286126
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.770995] sd 6:0:0:0: [sdg] Unhandled error code
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.770997] sd 6:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.771002] sd 6:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 25 5e 00 00 f0 00
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.771013] end_request: I/O error, dev sdg, sector 3286366
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.771077] sd 6:0:0:0: [sdg] Unhandled error code
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.771080] sd 6:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.771084] sd 6:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 26 4e 00 00 f0 00
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.771096] end_request: I/O error, dev sdg, sector 3286606
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.771158] sd 6:0:0:0: [sdg] Unhandled error code
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.771161] sd 6:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.771165] sd 6:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 27 3e 00 00 f0 00
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.771177] end_request: I/O error, dev sdg, sector 3286846
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.771253] sd 6:0:0:0: [sdg] Unhandled error code
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.771256] sd 6:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.771260] sd 6:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 28 2e 00 00 f0 00
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.771272] end_request: I/O error, dev sdg, sector 3287086
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.771334] sd 6:0:0:0: [sdg] Unhandled error code
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.771337] sd 6:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.771341] sd 6:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 29 1e 00 00 f0 00
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.771353] end_request: I/O error, dev sdg, sector 3287326
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.771414] sd 6:0:0:0: [sdg] Unhandled error code
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.771416] sd 6:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.771420] sd 6:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 2a 0e 00 00 f0 00
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.771432] end_request: I/O error, dev sdg, sector 3287566
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.771493] sd 6:0:0:0: [sdg] Unhandled error code
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.771496] sd 6:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.771534] sd 6:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 2a fe 00 00 20 00
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.771546] end_request: I/O error, dev sdg, sector 3287806
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.771617] sd 6:0:0:0: [sdg] Unhandled error code
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.771620] sd 6:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.771624] sd 6:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 2b 1e 00 00 f0 00
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.771636] end_request: I/O error, dev sdg, sector 3287838
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.771698] sd 6:0:0:0: [sdg] Unhandled error code
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.771701] sd 6:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.771705] sd 6:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 2c 0e 00 00 f0 00
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.771717] end_request: I/O error, dev sdg, sector 3288078
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.771778] sd 6:0:0:0: [sdg] Unhandled error code
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.771781] sd 6:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.771785] sd 6:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 2c fe 00 00 f0 00
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.771797] end_request: I/O error, dev sdg, sector 3288318
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.771858] sd 6:0:0:0: [sdg] Unhandled error code
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.771860] sd 6:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.771864] sd 6:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 2d ee 00 00 f0 00
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.771876] end_request: I/O error, dev sdg, sector 3288558
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.771937] sd 6:0:0:0: [sdg] Unhandled error code
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.771940] sd 6:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.771944] sd 6:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 2e de 00 00 f0 00
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.771956] end_request: I/O error, dev sdg, sector 3288798
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.772032] sd 6:0:0:0: [sdg] Unhandled error code
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.772035] sd 6:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.772041] sd 6:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 2f ce 00 00 f0 00
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.772066] end_request: I/O error, dev sdg, sector 3289038
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.772129] sd 6:0:0:0: [sdg] Unhandled error code
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.772132] sd 6:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.772138] sd 6:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 30 be 00 00 f0 00
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.772163] end_request: I/O error, dev sdg, sector 3289278
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.772228] sd 6:0:0:0: [sdg] Unhandled error code
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.772231] sd 6:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.772237] sd 6:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 31 ae 00 00 f0 00
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.772263] end_request: I/O error, dev sdg, sector 3289518
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.772328] sd 6:0:0:0: [sdg] Unhandled error code
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.772331] sd 6:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.772337] sd 6:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 32 9e 00 00 f0 00
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.772362] end_request: I/O error, dev sdg, sector 3289758
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.772424] sd 6:0:0:0: [sdg] Unhandled error code
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.772428] sd 6:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.772434] sd 6:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 33 8e 00 00 f0 00
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.772459] end_request: I/O error, dev sdg, sector 3289998
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.772523] sd 6:0:0:0: [sdg] Unhandled error code
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.772525] sd 6:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.772529] sd 6:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 34 7e 00 00 f0 00
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.772551] end_request: I/O error, dev sdg, sector 3290238
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.772614] sd 6:0:0:0: [sdg] Unhandled error code
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.772617] sd 6:0:0:0: [sdg] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.772621] sd 6:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 35 6e 00 00 f0 00
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.772633] end_request: I/O error, dev sdg, sector 3290478
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.772927] sd 6:0:0:0: [sdg] Unhandled error code
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.772930] sd 6:0:0:0: [sdg] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.772935] sd 6:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 36 5e 00 00 f0 00
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.772947] end_request: I/O error, dev sdg, sector 3290718
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.775079] sd 6:0:0:0: [sdg] Unhandled error code
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.775083] sd 6:0:0:0: [sdg] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.775087] sd 6:0:0:0: [sdg] CDB: Write(10): 2a 00 00 32 37 4e 00 00 f0 00
2010-10-05 17:25:55	kaadoke	kernel	[ 9629.775100] end_request: I/O error, dev sdg, sector 3290958
2010-10-05 17:26:11	kaadoke	kernel	[ 9645.064025] usb 1-6: new high speed USB device using ehci_hcd and address 8
2010-10-05 17:26:11	kaadoke	kernel	[ 9645.209181] usb 1-6: configuration #1 chosen from 1 choice
2010-10-05 17:26:11	kaadoke	kernel	[ 9645.221671] scsi7 : SCSI emulation for USB Mass Storage devices
2010-10-05 17:26:11	kaadoke	kernel	[ 9645.222821] usb-storage: device found at 8
2010-10-05 17:26:11	kaadoke	kernel	[ 9645.222824] usb-storage: waiting for device to settle before scanning
2010-10-05 17:26:16	kaadoke	kernel	[ 9650.221113] usb-storage: device scan complete
2010-10-05 17:26:16	kaadoke	kernel	[ 9650.222226] scsi 7:0:0:0: Direct-Access     Kindle   Internal Storage 0100 PQ: 0 ANSI: 2
2010-10-05 17:26:16	kaadoke	kernel	[ 9650.222748] sd 7:0:0:0: Attached scsi generic sg7 type 0
2010-10-05 17:26:16	kaadoke	kernel	[ 9650.232050] sd 7:0:0:0: [sdh] 7143360 512-byte logical blocks: (3.65 GB/3.40 GiB)
2010-10-05 17:26:16	kaadoke	kernel	[ 9650.333850] sd 7:0:0:0: [sdh] Write Protect is off
2010-10-05 17:26:16	kaadoke	kernel	[ 9650.333856] sd 7:0:0:0: [sdh] Mode Sense: 0f 00 00 00
2010-10-05 17:26:16	kaadoke	kernel	[ 9650.333859] sd 7:0:0:0: [sdh] Assuming drive cache: write through
2010-10-05 17:26:16	kaadoke	kernel	[ 9650.441133] sd 7:0:0:0: [sdh] Assuming drive cache: write through
2010-10-05 17:26:16	kaadoke	kernel	[ 9650.441141]  sdh: sdh1
2010-10-05 17:26:17	kaadoke	kernel	[ 9651.564456] sd 7:0:0:0: [sdh] Assuming drive cache: write through
2010-10-05 17:26:17	kaadoke	kernel	[ 9651.564465] sd 7:0:0:0: [sdh] Attached SCSI removable disk
2010-10-05 17:26:17	kaadoke	hald	mounted /dev/sdh1 on behalf of uid 1000
2010-10-05 17:26:18	kaadoke	kernel	[ 9652.319967] FAT: Directory bread(block 13958) failed
2010-10-05 17:26:18	kaadoke	kernel	[ 9652.319981] FAT: Directory bread(block 13959) failed
2010-10-05 17:26:18	kaadoke	kernel	[ 9652.319990] FAT: Directory bread(block 13960) failed
2010-10-05 17:26:18	kaadoke	kernel	[ 9652.320000] FAT: Directory bread(block 13961) failed
2010-10-05 17:26:18	kaadoke	kernel	[ 9652.320009] FAT: Directory bread(block 13962) failed
2010-10-05 17:26:18	kaadoke	kernel	[ 9652.320019] FAT: Directory bread(block 13963) failed
2010-10-05 17:26:18	kaadoke	kernel	[ 9652.320028] FAT: Directory bread(block 13964) failed
2010-10-05 17:26:18	kaadoke	kernel	[ 9652.320037] FAT: Directory bread(block 13965) failed

```

---

### Post by S.R on 2010-10-05
Looks like it is trying to read a FAT formatted file system on your Kindle. Linux will work with a NTFS file system but not FAT.

I would suggest trying WINE.

*After doing a little research Kindle does not support Linux so your only option when using Linux is to use WINE.*

---

### Post by last1 on 2010-10-05
I don't understand, every flash drive I've ever used has been FAT, and they all work in Linux.

---

### Post by S.R on 2010-10-05
Welcome to the brick wall. Many ways around but no one way over.

---

