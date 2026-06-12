---
title: "external usb iomega hard drive just doesn't work anymore"
date: 2008-11-09
forum: Hardware
---

### Post by stitchmysmile93 on 2008-11-09
Hello everyone I was wondering if anyone can help me with my issue with my hard drive.  Last night I unmounted my drive turned off my laptop and this morning I booted up my laptop and tried to mount my hard drive and I get nothing.  I have no idea what happened to it why it isn't working anymore.  I tried taking it apart to see if I could hook it to another machine but can't bacause it is sata and I have no hardware to try it out on.  If anyone can help that would be cool... Not a hardware guy lol.

---

### Post by cariboo on 2008-11-09
WHat is the out putof demsg when you turn the drive on. In a terminal type:

```
dmesg
```

you should get an output something like this:

```
usb 2-5: new high speed USB device using ehci_hcd and address 6
[11056.242955] usb 2-5: configuration #1 chosen from 1 choice
[11056.301915] usbcore: registered new interface driver libusual
[11056.316371] Initializing USB Mass Storage driver...
[11056.317390] scsi6 : SCSI emulation for USB Mass Storage devices
[11056.317659] usb-storage: device found at 6
[11056.317667] usb-storage: waiting for device to settle before scanning
[11056.317673] usbcore: registered new interface driver usb-storage
[11056.317678] USB Mass Storage support registered.
[11061.316417] usb-storage: device scan complete
[11061.319243] scsi 6:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  2.15 PQ: 0 ANSI: 2
[11061.321107] scsi 6:0:0:1: CD-ROM            SanDisk  U3 Cruzer Micro  2.15 PQ: 0 ANSI: 2
[11061.344409] sd 6:0:0:0: [sdc] 1994385 512-byte hardware sectors (1021 MB)
[11061.350192] sd 6:0:0:0: [sdc] Write Protect is off
[11061.350203] sd 6:0:0:0: [sdc] Mode Sense: 03 00 00 00
[11061.350206] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[11061.366280] sd 6:0:0:0: [sdc] 1994385 512-byte hardware sectors (1021 MB)
[11061.372117] sd 6:0:0:0: [sdc] Write Protect is off
[11061.372128] sd 6:0:0:0: [sdc] Mode Sense: 03 00 00 00
[11061.372131] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[11061.375077]  sdc: sdc1
```

Your device number will be different.

Jim

---

### Post by stitchmysmile93 on 2008-11-09
I'm not sure exactly what you wanted but it printed a lot of info.



[26499.526882] usb 2-5: reset high speed USB device using ehci_hcd and address 18
[26639.435976] usb 2-5: reset high speed USB device using ehci_hcd and address 18
[26679.014676] usb 2-5: reset high speed USB device using ehci_hcd and address 18
[26691.167783] usb 2-5: USB disconnect, address 18
[26699.208170] usb 2-5: new high speed USB device using ehci_hcd and address 19
[26699.281072] usb 2-5: configuration #1 chosen from 1 choice
[26699.281387] scsi19 : SCSI emulation for USB Mass Storage devices
[26699.306689] usb-storage: device found at 19
[26699.306696] usb-storage: waiting for device to settle before scanning
[26701.780118] usb-storage: device scan complete
[26701.806413] scsi 19:0:0:0: Direct-Access     ST350082 0AS                   PQ: 0 ANSI: 2 CCS
[26701.809398] sd 19:0:0:0: [sdb] Very big device. Trying to use READ CAPACITY(16).
[26701.813882] sd 19:0:0:0: [sdb] READ CAPACITY(16) failed
[26701.813888] sd 19:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[26701.813894] sd 19:0:0:0: [sdb] Use 0xffffffff as device size
[26701.813900] sd 19:0:0:0: [sdb] 4294967296 512-byte hardware sectors (2199023 MB)
[26701.816389] sd 19:0:0:0: [sdb] Write Protect is off
[26701.816395] sd 19:0:0:0: [sdb] Mode Sense: 34 00 00 00
[26701.816400] sd 19:0:0:0: [sdb] Assuming drive cache: write through
[26701.818381] sd 19:0:0:0: [sdb] Very big device. Trying to use READ CAPACITY(16).
[26701.822880] sd 19:0:0:0: [sdb] READ CAPACITY(16) failed
[26701.822884] sd 19:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[26701.822891] sd 19:0:0:0: [sdb] Use 0xffffffff as device size
[26701.822894] sd 19:0:0:0: [sdb] 4294967296 512-byte hardware sectors (2199023 MB)
[26701.824943] sd 19:0:0:0: [sdb] Write Protect is off
[26701.824949] sd 19:0:0:0: [sdb] Mode Sense: 34 00 00 00
[26701.824954] sd 19:0:0:0: [sdb] Assuming drive cache: write through
[26701.824958]  sdb:<6>sd 19:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[26701.825776] sd 19:0:0:0: [sdb] Sense Key : Medium Error [current] 
[26701.825783] sd 19:0:0:0: [sdb] Add. Sense: Unrecovered read error
[26701.825788] end_request: I/O error, dev sdb, sector 0
[26701.825791] printk: 15 messages suppressed.
[26701.825794] Buffer I/O error on device sdb, logical block 0
[26701.835267] sd 19:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[26701.835275] sd 19:0:0:0: [sdb] Sense Key : Medium Error [current] 
[26701.835279] sd 19:0:0:0: [sdb] Add. Sense: Unrecovered read error
[26701.835283] end_request: I/O error, dev sdb, sector 0
[26701.835287] Buffer I/O error on device sdb, logical block 0
[26701.844765] sd 19:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[26701.844771] sd 19:0:0:0: [sdb] Sense Key : Medium Error [current] 
[26701.844775] sd 19:0:0:0: [sdb] Add. Sense: Unrecovered read error
[26701.844780] end_request: I/O error, dev sdb, sector 0
[26701.844784] Buffer I/O error on device sdb, logical block 0
[26701.854261] sd 19:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[26701.854265] sd 19:0:0:0: [sdb] Sense Key : Medium Error [current] 
[26701.854269] sd 19:0:0:0: [sdb] Add. Sense: Unrecovered read error
[26701.854272] end_request: I/O error, dev sdb, sector 0
[26701.854275] Buffer I/O error on device sdb, logical block 0
[26701.863765] sd 19:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[26701.863772] sd 19:0:0:0: [sdb] Sense Key : Medium Error [current] 
[26701.863775] sd 19:0:0:0: [sdb] Add. Sense: Unrecovered read error
[26701.863780] end_request: I/O error, dev sdb, sector 0
[26701.863784] Buffer I/O error on device sdb, logical block 0
[26701.888904] ldm_validate_partition_table(): Disk read failed.
[26701.873267] sd 19:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[26701.873274] sd 19:0:0:0: [sdb] Sense Key : Medium Error [current] 
[26701.873278] sd 19:0:0:0: [sdb] Add. Sense: Unrecovered read error
[26701.873282] end_request: I/O error, dev sdb, sector 0
[26701.873286] Buffer I/O error on device sdb, logical block 0
[26701.882767] sd 19:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[26701.882774] sd 19:0:0:0: [sdb] Sense Key : Medium Error [current] 
[26701.882778] sd 19:0:0:0: [sdb] Add. Sense: Unrecovered read error
[26701.882782] end_request: I/O error, dev sdb, sector 0
[26701.882786] Buffer I/O error on device sdb, logical block 0
[26701.923880] sd 19:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[26701.923889] sd 19:0:0:0: [sdb] Sense Key : Medium Error [current] 
[26701.923894] sd 19:0:0:0: [sdb] Add. Sense: Unrecovered read error
[26701.923900] end_request: I/O error, dev sdb, sector 0
[26701.923904] Buffer I/O error on device sdb, logical block 0
[26701.932877] sd 19:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[26701.932887] sd 19:0:0:0: [sdb] Sense Key : Medium Error [current] 
[26701.932892] sd 19:0:0:0: [sdb] Add. Sense: Unrecovered read error
[26701.932897] end_request: I/O error, dev sdb, sector 0
[26701.932901] Buffer I/O error on device sdb, logical block 0
[26701.932918] Dev sdb: unable to read RDB block 0
[26701.941875] sd 19:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[26701.941882] sd 19:0:0:0: [sdb] Sense Key : Medium Error [current] 
[26701.941886] sd 19:0:0:0: [sdb] Add. Sense: Unrecovered read error
[26701.941891] end_request: I/O error, dev sdb, sector 0
[26701.941895] Buffer I/O error on device sdb, logical block 0
[26701.925769] sd 19:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[26701.925783] sd 19:0:0:0: [sdb] Sense Key : Medium Error [current] 
[26701.925788] sd 19:0:0:0: [sdb] Add. Sense: Unrecovered read error
[26701.925795] end_request: I/O error, dev sdb, sector 0
[26701.935266] sd 19:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[26701.935275] sd 19:0:0:0: [sdb] Sense Key : Medium Error [current] 
[26701.935282] sd 19:0:0:0: [sdb] Add. Sense: Unrecovered read error
[26701.935287] end_request: I/O error, dev sdb, sector 24
[26701.944264] sd 19:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[26701.944271] sd 19:0:0:0: [sdb] Sense Key : Medium Error [current] 
[26701.944277] sd 19:0:0:0: [sdb] Add. Sense: Unrecovered read error
[26701.944283] end_request: I/O error, dev sdb, sector 24
[26701.953264] sd 19:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[26701.953272] sd 19:0:0:0: [sdb] Sense Key : Medium Error [current] 
[26701.953276] sd 19:0:0:0: [sdb] Add. Sense: Unrecovered read error
[26701.953283] end_request: I/O error, dev sdb, sector 0
[26701.962267] sd 19:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[26701.962276] sd 19:0:0:0: [sdb] Sense Key : Medium Error [current] 
[26701.962281] sd 19:0:0:0: [sdb] Add. Sense: Unrecovered read error
[26701.962286] end_request: I/O error, dev sdb, sector 0
[26701.962299]  unable to read partition table
[26701.962367] sd 19:0:0:0: [sdb] Attached SCSI disk
[26701.962414] sd 19:0:0:0: Attached scsi generic sg2 type 0
[26701.985269] sd 19:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[26701.985280] sd 19:0:0:0: [sdb] Sense Key : Medium Error [current] 
[26701.985287] sd 19:0:0:0: [sdb] Add. Sense: Unrecovered read error
[26701.985292] end_request: I/O error, dev sdb, sector 0
[26701.994262] sd 19:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[26701.994270] sd 19:0:0:0: [sdb] Sense Key : Medium Error [current] 
[26701.994274] sd 19:0:0:0: [sdb] Add. Sense: Unrecovered read error
[26701.994279] end_request: I/O error, dev sdb, sector 0
[26702.016262] sd 19:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[26702.016275] sd 19:0:0:0: [sdb] Sense Key : Medium Error [current] 
[26702.016280] sd 19:0:0:0: [sdb] Add. Sense: Unrecovered read error
[26702.016285] end_request: I/O error, dev sdb, sector 0
[26702.024758] sd 19:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[26702.024768] sd 19:0:0:0: [sdb] Sense Key : Medium Error [current] 
[26702.024774] sd 19:0:0:0: [sdb] Add. Sense: Unrecovered read error
[26702.024782] end_request: I/O error, dev sdb, sector 0
[26713.999361] usb 2-5: USB disconnect, address 19
[26740.895105] usb 2-5: new high speed USB device using ehci_hcd and address 20
[26740.968062] usb 2-5: configuration #1 chosen from 1 choice
[26740.985244] scsi20 : SCSI emulation for USB Mass Storage devices
[26740.989670] usb-storage: device found at 20
[26740.989676] usb-storage: waiting for device to settle before scanning
[26743.489038] usb-storage: device scan complete
[26743.490350] scsi 20:0:0:0: Direct-Access     ST350082 0AS                   PQ: 0 ANSI: 2 CCS
[26743.492821] sd 20:0:0:0: [sdb] Very big device. Trying to use READ CAPACITY(16).
[26743.497818] sd 20:0:0:0: [sdb] READ CAPACITY(16) failed
[26743.497824] sd 20:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[26743.497830] sd 20:0:0:0: [sdb] Use 0xffffffff as device size
[26743.497835] sd 20:0:0:0: [sdb] 4294967296 512-byte hardware sectors (2199023 MB)
[26743.499381] sd 20:0:0:0: [sdb] Write Protect is off
[26743.499387] sd 20:0:0:0: [sdb] Mode Sense: 34 00 00 00
[26743.499392] sd 20:0:0:0: [sdb] Assuming drive cache: write through
[26743.501317] sd 20:0:0:0: [sdb] Very big device. Trying to use READ CAPACITY(16).
[26743.505816] sd 20:0:0:0: [sdb] READ CAPACITY(16) failed
[26743.505822] sd 20:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[26743.505827] sd 20:0:0:0: [sdb] Use 0xffffffff as device size
[26743.505830] sd 20:0:0:0: [sdb] 4294967296 512-byte hardware sectors (2199023 MB)
[26743.507379] sd 20:0:0:0: [sdb] Write Protect is off
[26743.507385] sd 20:0:0:0: [sdb] Mode Sense: 34 00 00 00
[26743.507389] sd 20:0:0:0: [sdb] Assuming drive cache: write through
[26743.507394]  sdb:<6>sd 20:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[26743.534833] sd 20:0:0:0: [sdb] Sense Key : Medium Error [current] 
[26743.534841] sd 20:0:0:0: [sdb] Add. Sense: Unrecovered read error
[26743.534847] end_request: I/O error, dev sdb, sector 0
[26743.534851] printk: 15 messages suppressed.
[26743.534855] Buffer I/O error on device sdb, logical block 0
[26743.543313] sd 20:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[26743.543322] sd 20:0:0:0: [sdb] Sense Key : Medium Error [current] 
[26743.543326] sd 20:0:0:0: [sdb] Add. Sense: Unrecovered read error
[26743.543333] end_request: I/O error, dev sdb, sector 0
[26743.543336] Buffer I/O error on device sdb, logical block 0
[26743.552312] sd 20:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[26743.552322] sd 20:0:0:0: [sdb] Sense Key : Medium Error [current] 
[26743.552327] sd 20:0:0:0: [sdb] Add. Sense: Unrecovered read error
[26743.552335] end_request: I/O error, dev sdb, sector 0
[26743.552339] Buffer I/O error on device sdb, logical block 0
[26743.561310] sd 20:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[26743.561317] sd 20:0:0:0: [sdb] Sense Key : Medium Error [current] 
[26743.561322] sd 20:0:0:0: [sdb] Add. Sense: Unrecovered read error
[26743.561328] end_request: I/O error, dev sdb, sector 0
[26743.561332] Buffer I/O error on device sdb, logical block 0
[26743.569809] sd 20:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[26743.569817] sd 20:0:0:0: [sdb] Sense Key : Medium Error [current] 
[26743.569821] sd 20:0:0:0: [sdb] Add. Sense: Unrecovered read error
[26743.569827] end_request: I/O error, dev sdb, sector 0
[26743.569831] Buffer I/O error on device sdb, logical block 0
[26743.569840] ldm_validate_partition_table(): Disk read failed.
[26743.578808] sd 20:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[26743.578817] sd 20:0:0:0: [sdb] Sense Key : Medium Error [current] 
[26743.578822] sd 20:0:0:0: [sdb] Add. Sense: Unrecovered read error
[26743.578828] end_request: I/O error, dev sdb, sector 0
[26743.578832] Buffer I/O error on device sdb, logical block 0
[26743.587307] sd 20:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[26743.587316] sd 20:0:0:0: [sdb] Sense Key : Medium Error [current] 
[26743.587320] sd 20:0:0:0: [sdb] Add. Sense: Unrecovered read error
[26743.587327] end_request: I/O error, dev sdb, sector 0
[26743.587331] Buffer I/O error on device sdb, logical block 0
[26743.597315] sd 20:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[26743.597325] sd 20:0:0:0: [sdb] Sense Key : Medium Error [current] 
[26743.597329] sd 20:0:0:0: [sdb] Add. Sense: Unrecovered read error
[26743.597334] end_request: I/O error, dev sdb, sector 0
[26743.597338] Buffer I/O error on device sdb, logical block 0
[26743.608316] sd 20:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[26743.608326] sd 20:0:0:0: [sdb] Sense Key : Medium Error [current] 
[26743.608331] sd 20:0:0:0: [sdb] Add. Sense: Unrecovered read error
[26743.608336] end_request: I/O error, dev sdb, sector 0
[26743.608340] Buffer I/O error on device sdb, logical block 0
[26743.608356] Dev sdb: unable to read RDB block 0
[26743.617305] sd 20:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[26743.617311] sd 20:0:0:0: [sdb] Sense Key : Medium Error [current] 
[26743.617314] sd 20:0:0:0: [sdb] Add. Sense: Unrecovered read error
[26743.617318] end_request: I/O error, dev sdb, sector 0
[26743.617320] Buffer I/O error on device sdb, logical block 0
[26743.626309] sd 20:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[26743.626313] sd 20:0:0:0: [sdb] Sense Key : Medium Error [current] 
[26743.626317] sd 20:0:0:0: [sdb] Add. Sense: Unrecovered read error
[26743.626321] end_request: I/O error, dev sdb, sector 0
[26743.634811] sd 20:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[26743.634815] sd 20:0:0:0: [sdb] Sense Key : Medium Error [current] 
[26743.634819] sd 20:0:0:0: [sdb] Add. Sense: Unrecovered read error
[26743.634823] end_request: I/O error, dev sdb, sector 24
[26743.643306] sd 20:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[26743.643311] sd 20:0:0:0: [sdb] Sense Key : Medium Error [current] 
[26743.643314] sd 20:0:0:0: [sdb] Add. Sense: Unrecovered read error
[26743.643318] end_request: I/O error, dev sdb, sector 24
[26743.652311] sd 20:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[26743.652316] sd 20:0:0:0: [sdb] Sense Key : Medium Error [current] 
[26743.652320] sd 20:0:0:0: [sdb] Add. Sense: Unrecovered read error
[26743.652323] end_request: I/O error, dev sdb, sector 0
[26743.660806] sd 20:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[26743.660811] sd 20:0:0:0: [sdb] Sense Key : Medium Error [current] 
[26743.660814] sd 20:0:0:0: [sdb] Add. Sense: Unrecovered read error
[26743.660818] end_request: I/O error, dev sdb, sector 0
[26743.660825]  unable to read partition table
[26743.660892] sd 20:0:0:0: [sdb] Attached SCSI disk
[26743.660943] sd 20:0:0:0: Attached scsi generic sg2 type 0
[26743.686311] sd 20:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[26743.686320] sd 20:0:0:0: [sdb] Sense Key : Medium Error [current] 
[26743.686325] sd 20:0:0:0: [sdb] Add. Sense: Unrecovered read error
[26743.686330] end_request: I/O error, dev sdb, sector 0
[26743.695808] sd 20:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[26743.695812] sd 20:0:0:0: [sdb] Sense Key : Medium Error [current] 
[26743.695816] sd 20:0:0:0: [sdb] Add. Sense: Unrecovered read error
[26743.695820] end_request: I/O error, dev sdb, sector 0
[26743.718319] sd 20:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[26743.718327] sd 20:0:0:0: [sdb] Sense Key : Medium Error [current] 
[26743.718332] sd 20:0:0:0: [sdb] Add. Sense: Unrecovered read error
[26743.718337] end_request: I/O error, dev sdb, sector 0
[26743.727302] sd 20:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[26743.727307] sd 20:0:0:0: [sdb] Sense Key : Medium Error [current] 
[26743.727311] sd 20:0:0:0: [sdb] Add. Sense: Unrecovered read error
[26743.727315] end_request: I/O error, dev sdb, sector 0
[27373.087788] usb 2-5: USB disconnect, address 20
[27436.336190] wlan0: No ProbeResp from current AP 00:1e:2a:54:b5:b8 - assume out of range
[27446.869723] b43-phy0 debug: Disabling hardware based encryption for keyidx: 0, mac: ff:ff:ff:ff:ff:ff
[27449.407753] b43-phy0 debug: Using hardware based encryption for keyidx: 0, mac: ff:ff:ff:ff:ff:ff
[27449.381749] wlan0: Initial auth_alg=0
[27449.381758] wlan0: authenticate with AP 00:1e:2a:54:b5:b8
[27449.381775] wlan0: Initial auth_alg=0
[27449.381778] wlan0: authenticate with AP 00:1e:2a:54:b5:b8
[27449.382862] wlan0: RX authentication from 00:1e:2a:54:b5:b8 (alg=0 transaction=2 status=0)
[27449.382868] wlan0: authenticated
[27449.382872] wlan0: associate with AP 00:1e:2a:54:b5:b8
[27449.386921] wlan0: authentication frame received from 00:1e:2a:54:b5:b8, but not in authenticate state - ignored
[27449.388090] wlan0: RX AssocResp from 00:1e:2a:54:b5:b8 (capab=0x411 status=0 aid=1)
[27449.388097] wlan0: associated
[27449.388102] printk: 15 messages suppressed.
[27449.388106] wlan0: switched to short barker preamble (BSSID=00:1e:2a:54:b5:b8)
[27449.388141] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[27449.388146] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[27449.388150] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[27449.388155] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[27449.389594] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[27458.455950] wlan0: no IPv6 routers present
[27458.699937] usb 1-3: new full speed USB device using ohci_hcd and address 3
[27458.812340] usb 1-3: configuration #1 chosen from 1 choice
[27458.923752] usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x03F0 pid 0x1D04
[27458.923987] usbcore: registered new interface driver usblp
[27475.965951] usblp0: removed
[27476.715443] audit(1226260142.107:3): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=10372 profile="/usr/sbin/cupsd" namespace="default"
[28945.877892] usb 1-3: USB disconnect, address 3
[29003.286130] usb 2-3: new high speed USB device using ehci_hcd and address 22
[29003.352833] usb 2-3: configuration #1 chosen from 1 choice
[29003.384911] scsi21 : SCSI emulation for USB Mass Storage devices
[29003.384983] usb-storage: device found at 22
[29003.384987] usb-storage: waiting for device to settle before scanning
[29006.206166] usb-storage: device scan complete
[29006.207279] scsi 21:0:0:0: Direct-Access     ST350082 0AS                   PQ: 0 ANSI: 2 CCS
[29006.218142] sd 21:0:0:0: [sdb] Very big device. Trying to use READ CAPACITY(16).
[29006.222690] sd 21:0:0:0: [sdb] READ CAPACITY(16) failed
[29006.222696] sd 21:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[29006.222702] sd 21:0:0:0: [sdb] Use 0xffffffff as device size
[29006.222708] sd 21:0:0:0: [sdb] 4294967296 512-byte hardware sectors (2199023 MB)
[29006.224753] sd 21:0:0:0: [sdb] Write Protect is off
[29006.224759] sd 21:0:0:0: [sdb] Mode Sense: 34 00 00 00
[29006.224763] sd 21:0:0:0: [sdb] Assuming drive cache: write through
[29006.226690] sd 21:0:0:0: [sdb] Very big device. Trying to use READ CAPACITY(16).
[29006.232694] sd 21:0:0:0: [sdb] READ CAPACITY(16) failed
[29006.232700] sd 21:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[29006.232706] sd 21:0:0:0: [sdb] Use 0xffffffff as device size
[29006.232710] sd 21:0:0:0: [sdb] 4294967296 512-byte hardware sectors (2199023 MB)
[29006.234753] sd 21:0:0:0: [sdb] Write Protect is off
[29006.234759] sd 21:0:0:0: [sdb] Mode Sense: 34 00 00 00
[29006.234762] sd 21:0:0:0: [sdb] Assuming drive cache: write through
[29006.234767]  sdb:<6>sd 21:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[29006.233535] sd 21:0:0:0: [sdb] Sense Key : Medium Error [current] 
[29006.233541] sd 21:0:0:0: [sdb] Add. Sense: Unrecovered read error
[29006.233546] end_request: I/O error, dev sdb, sector 0
[29006.233550] Buffer I/O error on device sdb, logical block 0
[29006.243021] sd 21:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[29006.243026] sd 21:0:0:0: [sdb] Sense Key : Medium Error [current] 
[29006.243029] sd 21:0:0:0: [sdb] Add. Sense: Unrecovered read error
[29006.243033] end_request: I/O error, dev sdb, sector 0
[29006.243036] Buffer I/O error on device sdb, logical block 0
[29006.253529] sd 21:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[29006.253538] sd 21:0:0:0: [sdb] Sense Key : Medium Error [current] 
[29006.253542] sd 21:0:0:0: [sdb] Add. Sense: Unrecovered read error
[29006.253547] end_request: I/O error, dev sdb, sector 0
[29006.253551] Buffer I/O error on device sdb, logical block 0
[29006.263028] sd 21:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[29006.263035] sd 21:0:0:0: [sdb] Sense Key : Medium Error [current] 
[29006.263039] sd 21:0:0:0: [sdb] Add. Sense: Unrecovered read error
[29006.263044] end_request: I/O error, dev sdb, sector 0
[29006.263048] Buffer I/O error on device sdb, logical block 0
[29006.273528] sd 21:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[29006.273536] sd 21:0:0:0: [sdb] Sense Key : Medium Error [current] 
[29006.273540] sd 21:0:0:0: [sdb] Add. Sense: Unrecovered read error
[29006.273544] end_request: I/O error, dev sdb, sector 0
[29006.273548] Buffer I/O error on device sdb, logical block 0
[29006.302217] ldm_validate_partition_table(): Disk read failed.
[29006.283028] sd 21:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[29006.283036] sd 21:0:0:0: [sdb] Sense Key : Medium Error [current] 
[29006.283040] sd 21:0:0:0: [sdb] Add. Sense: Unrecovered read error
[29006.283045] end_request: I/O error, dev sdb, sector 0
[29006.283049] Buffer I/O error on device sdb, logical block 0
[29006.323800] sd 21:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[29006.323810] sd 21:0:0:0: [sdb] Sense Key : Medium Error [current] 
[29006.323815] sd 21:0:0:0: [sdb] Add. Sense: Unrecovered read error
[29006.323820] end_request: I/O error, dev sdb, sector 0
[29006.323825] Buffer I/O error on device sdb, logical block 0
[29006.310083] sd 21:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[29006.310093] sd 21:0:0:0: [sdb] Sense Key : Medium Error [current] 
[29006.310097] sd 21:0:0:0: [sdb] Add. Sense: Unrecovered read error
[29006.310102] end_request: I/O error, dev sdb, sector 0
[29006.310106] Buffer I/O error on device sdb, logical block 0
[29006.327938] sd 21:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[29006.327948] sd 21:0:0:0: [sdb] Sense Key : Medium Error [current] 
[29006.327953] sd 21:0:0:0: [sdb] Add. Sense: Unrecovered read error
[29006.327958] end_request: I/O error, dev sdb, sector 0
[29006.327962] Buffer I/O error on device sdb, logical block 0
[29006.356629] Dev sdb: unable to read RDB block 0
[29006.345943] sd 21:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[29006.345950] sd 21:0:0:0: [sdb] Sense Key : Medium Error [current] 
[29006.345953] sd 21:0:0:0: [sdb] Add. Sense: Unrecovered read error
[29006.345959] end_request: I/O error, dev sdb, sector 0
[29006.345962] Buffer I/O error on device sdb, logical block 0
[29006.363938] sd 21:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[29006.363944] sd 21:0:0:0: [sdb] Sense Key : Medium Error [current] 
[29006.363947] sd 21:0:0:0: [sdb] Add. Sense: Unrecovered read error
[29006.363955] end_request: I/O error, dev sdb, sector 0
[29006.381938] sd 21:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[29006.381944] sd 21:0:0:0: [sdb] Sense Key : Medium Error [current] 
[29006.381948] sd 21:0:0:0: [sdb] Add. Sense: Unrecovered read error
[29006.381952] end_request: I/O error, dev sdb, sector 24
[29006.398932] sd 21:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[29006.398938] sd 21:0:0:0: [sdb] Sense Key : Medium Error [current] 
[29006.398941] sd 21:0:0:0: [sdb] Add. Sense: Unrecovered read error
[29006.398946] end_request: I/O error, dev sdb, sector 24
[29006.415932] sd 21:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[29006.415939] sd 21:0:0:0: [sdb] Sense Key : Medium Error [current] 
[29006.415942] sd 21:0:0:0: [sdb] Add. Sense: Unrecovered read error
[29006.415947] end_request: I/O error, dev sdb, sector 0
[29006.433925] sd 21:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[29006.433930] sd 21:0:0:0: [sdb] Sense Key : Medium Error [current] 
[29006.433934] sd 21:0:0:0: [sdb] Add. Sense: Unrecovered read error
[29006.433938] end_request: I/O error, dev sdb, sector 0
[29006.462601]  unable to read partition table
[29006.462673] sd 21:0:0:0: [sdb] Attached SCSI disk
[29006.462722] sd 21:0:0:0: Attached scsi generic sg2 type 0
[29006.466929] sd 21:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[29006.466937] sd 21:0:0:0: [sdb] Sense Key : Medium Error [current] 
[29006.466942] sd 21:0:0:0: [sdb] Add. Sense: Unrecovered read error
[29006.466947] end_request: I/O error, dev sdb, sector 0
[29006.483917] sd 21:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[29006.483922] sd 21:0:0:0: [sdb] Sense Key : Medium Error [current] 
[29006.483926] sd 21:0:0:0: [sdb] Add. Sense: Unrecovered read error
[29006.483930] end_request: I/O error, dev sdb, sector 0
[29006.523914] sd 21:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[29006.523924] sd 21:0:0:0: [sdb] Sense Key : Medium Error [current] 
[29006.523928] sd 21:0:0:0: [sdb] Add. Sense: Unrecovered read error
[29006.523933] end_request: I/O error, dev sdb, sector 0
[29006.540914] sd 21:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[29006.540919] sd 21:0:0:0: [sdb] Sense Key : Medium Error [current] 
[29006.540923] sd 21:0:0:0: [sdb] Add. Sense: Unrecovered read error
[29006.540926] end_request: I/O error, dev sdb, sector 0

---

### Post by stitchmysmile93 on 2008-11-09
Actually now that I look at it it just says the same stuff over and over...

---

### Post by stitchmysmile93 on 2008-11-09
Well I'm not sure what to do it is  probably a problem with the hardware that cases the hard drive because it sounds fine when I power it up and does nothing when I connect the usb to the laptop...

---

### Post by stitchmysmile93 on 2008-11-09
bump...

---

### Post by cariboo on 2008-11-09
It looks like you got a defective drive:

> [26701.824958] sdb:<6>sd 19:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[26701.825776] sd 19:0:0:0: [sdb] Sense Key : Medium Error [current]
[26701.825783] sd 19:0:0:0: [sdb] Add. Sense: **Unrecovered read error**

note the bolded part.

Which files system is it using? If it is ntfs you may want to hook it up to a windows computer and chkdsk on it. If it is ext3 run fsck on it.

```
sudo fsck -a /dev/sdb
```

Jim

---

### Post by stitchmysmile93 on 2008-11-09
It's ntfs and it doesn't show on a windows machine either....

---

### Post by cariboo on 2008-11-10
Depending on how old it is, the hard driver may still be under warranty. If you can take it out of the case and go to the manufcturesr web site and check the model and serial number you may be able to get an RMA to return if for warranty repair/replacement.

Jim

---

