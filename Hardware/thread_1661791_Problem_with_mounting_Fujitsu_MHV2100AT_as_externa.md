---
title: "Problem with mounting Fujitsu MHV2100AT as external hard drive"
date: 2011-01-07
forum: Hardware
---

### Post by saemull on 2011-01-07
[prologue]
My old windows based laptop died through motherboard failure. According to service hard drive (**MHV2100AT**) was ok and i wanted to use it as external hard drive.

So on the second day with linux i connected the case with computer and faced with problems:

```
[ 3303.204081] usb 1-3: new high speed USB device using ehci_hcd and address 5 
[ 3303.533897] Initializing USB Mass Storage driver... 
[ 3303.534276] scsi2 : usb-storage 1-3:1.0 
[ 3303.534819] usbcore: registered new interface driver usb-storage 
[ 3303.534829] USB Mass Storage support registered. 
[ 3304.592505] scsi 2:0:0:0: Direct-Access     fUjIvSw  oHv2302Av " " "       PQ: 0 ANSI: 2 CCS 
[ 3304.599936] sd 2:0:0:0: Attached scsi generic sg1 type 0 
[ 3304.612463] sd 2:0:0:0: [sdb] 732242480 512-byte logical blocks: (374 GB/349 GiB) 
[ 3304.613334] sd 2:0:0:0: [sdb] Write Protect is off 
[ 3304.613346] sd 2:0:0:0: [sdb] Mode Sense: 28 00 00 00 
[ 3304.613353] sd 2:0:0:0: [sdb] Assuming drive cache: write through 
[ 3304.615189] sd 2:0:0:0: [sdb] Assuming drive cache: write through 
[ 3304.615206]  sdb: 
[ 3308.039050] sd 2:0:0:0: [sdb] Unhandled sense code 
[ 3308.039060] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE 
[ 3308.039070] sd 2:0:0:0: [sdb] Sense Key : Hardware Error [current] 
[ 3308.039081] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information 
[ 3308.039093] sd 2:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00 
[ 3308.039116] end_request: I/O error, dev sdb, sector 0 
[ 3308.039125] quiet_error: 9 callbacks suppressed 
[ 3308.039132] Buffer I/O error on device sdb, logical block 0 
[ 3308.048224] ldm_validate_partition_table(): Disk read failed. 
[ 3308.048249] Dev sdb: unable to read RDB block 0 
[ 3308.048934]  unable to read partition table 
[ 3308.055946] sd 2:0:0:0: [sdb] Assuming drive cache: write through 
[ 3308.055960] sd 2:0:0:0: [sdb] Attached SCSI disk 
```

As the external hard drive didn't show up i thought i should connect it with a computer with windows (bad idea). Didn't give any errors but won't let use the hard drive either.

So i went back to linux, this time it was somewhat different:

```
[20695.765074] usb 1-3: new high speed USB device using ehci_hcd and address 9 
[20695.900195] scsi3 : usb-storage 1-3:1.0 
[20696.955545] scsi 3:0:0:0: Direct-Access     nUnI~S   oH~2 0~A~ n n n       PQ: 0 ANSI: 2 CCS 
[20696.957273] sd 3:0:0:0: Attached scsi generic sg1 type 0 
[20696.967518] sd 3:0:0:0: [sdb] 1845521920 512-byte logical blocks: (944 GB/880 GiB) 
[20696.968779] sd 3:0:0:0: [sdb] Write Protect is off 
[20696.968792] sd 3:0:0:0: [sdb] Mode Sense: 28 00 00 00 
[20696.968800] sd 3:0:0:0: [sdb] Assuming drive cache: write through 
[20696.970374] sd 3:0:0:0: [sdb] Assuming drive cache: write through 
[20696.970391]  sdb: 
[20697.369490] sd 3:0:0:0: [sdb] Unhandled sense code 
[20697.369501] sd 3:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE 
[20697.369512] sd 3:0:0:0: [sdb] Sense Key : Hardware Error [current] 
[20697.369524] sd 3:0:0:0: [sdb] Add. Sense: No additional sense information 
[20697.369537] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00 
[20697.369562] end_request: I/O error, dev sdb, sector 0 
[20697.369575] Buffer I/O error on device sdb, logical block 0 
```

Any suggestion, what to do next?

---

