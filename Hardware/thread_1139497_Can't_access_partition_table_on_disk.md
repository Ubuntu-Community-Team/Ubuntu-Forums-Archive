---
title: "Can't access partition table on disk"
date: 2009-04-27
forum: Hardware
---

### Post by musther on 2009-04-27
I was having some issues with my netbook, so I booted using a bootable image on a USB drive.  I opened GParted, selected the internal disk's partition and hit 'check', then apply.  Fsck began to run so I walked away.  When I came back it said something about an error while trying to resize the partition - something I didn't ask it to do...  Anyway, I then rebooted, and got a GRUB error 10.  I booted with the USB drive again, and could no longer see the internal drive in ubuntu.  I tried a few things, tried fdisk and cfdisk, got "Unable to read sda" from fdisk.  

So I took out the drive, plugged it into an external SATA enclosure, and plugged it into my desktop - it showed up in cfdisk, with no partitions, so I tried to create one, it seemed to work.  But now I can't access the drive with any partitioning tool, still get "Unable to read" from fdisk.  

So, I'm quite stuck, don't know what to try.
Dmesg output:
```
[  471.295940] Initializing USB Mass Storage driver...
[  471.296829] scsi2 : SCSI emulation for USB Mass Storage devices
[  471.297713] usbcore: registered new interface driver usb-storage
[  471.297730] USB Mass Storage support registered.
[  471.298968] usb-storage: device found at 5
[  471.298981] usb-storage: waiting for device to settle before scanning
[  476.296295] usb-storage: device scan complete
[  476.297116] scsi 2:0:0:0: Direct-Access     STT_FTM3 2GL25H                PQ: 0 ANSI: 2 CCS
[  476.300238] sd 2:0:0:0: [sdc] 62586880 512-byte hardware sectors (32044 MB)
[  476.301098] sd 2:0:0:0: [sdc] Write Protect is off
[  476.301107] sd 2:0:0:0: [sdc] Mode Sense: 34 00 00 00
[  476.301112] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[  476.301837] sd 2:0:0:0: [sdc] 62586880 512-byte hardware sectors (32044 MB)
[  476.311894] sd 2:0:0:0: [sdc] Write Protect is off
[  476.311919] sd 2:0:0:0: [sdc] Mode Sense: 34 00 00 00
[  476.311930] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[  476.311954]  sdc:<6>usb 5-4.3: reset high speed USB device using ehci_hcd and address 5
[  506.405163] sd 2:0:0:0: Device offlined - not ready after error recovery
[  506.405185] sd 2:0:0:0: [sdc] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
[  506.405194] end_request: I/O error, dev sdc, sector 0
[  506.405205] Buffer I/O error on device sdc, logical block 0
[  506.405263] sd 2:0:0:0: rejecting I/O to offline device
[  506.405271] Buffer I/O error on device sdc, logical block 0
[  506.405295] sd 2:0:0:0: rejecting I/O to offline device
[  506.405301] Buffer I/O error on device sdc, logical block 0
[  506.405323] sd 2:0:0:0: rejecting I/O to offline device
[  506.405330] Buffer I/O error on device sdc, logical block 0
[  506.405350] sd 2:0:0:0: rejecting I/O to offline device
[  506.405356] Buffer I/O error on device sdc, logical block 0
[  506.405368] ldm_validate_partition_table(): Disk read failed.
[  506.405386] sd 2:0:0:0: rejecting I/O to offline device
[  506.405393] Buffer I/O error on device sdc, logical block 0
[  506.405411] sd 2:0:0:0: rejecting I/O to offline device
[  506.405418] Buffer I/O error on device sdc, logical block 0
[  506.405436] sd 2:0:0:0: rejecting I/O to offline device
[  506.405442] Buffer I/O error on device sdc, logical block 0
[  506.405460] sd 2:0:0:0: rejecting I/O to offline device
[  506.405468] Buffer I/O error on device sdc, logical block 0
[  506.405480] Dev sdc: unable to read RDB block 0
[  506.405495] sd 2:0:0:0: rejecting I/O to offline device
[  506.405501] Buffer I/O error on device sdc, logical block 0
[  506.405521] sd 2:0:0:0: rejecting I/O to offline device
[  506.405553] sd 2:0:0:0: rejecting I/O to offline device
[  506.405570] sd 2:0:0:0: rejecting I/O to offline device
[  506.405590] sd 2:0:0:0: rejecting I/O to offline device
[  506.405610] sd 2:0:0:0: rejecting I/O to offline device
[  506.405621]  unable to read partition table
[  506.405806] sd 2:0:0:0: [sdc] Attached SCSI disk
[  506.406068] sd 2:0:0:0: Attached scsi generic sg4 type 0
[  506.416979] usb 5-4.3: USB disconnect, address 5
[  506.628324] usb 5-4.3: new high speed USB device using ehci_hcd and address 6
[  506.721127] usb 5-4.3: configuration #1 chosen from 1 choice
[  506.722234] scsi3 : SCSI emulation for USB Mass Storage devices
[  506.725261] usb-storage: device found at 6
[  506.725278] usb-storage: waiting for device to settle before scanning
[  511.724292] usb-storage: device scan complete
[  513.101849] scsi 3:0:0:0: Direct-Access     STT_FTM3 2GL25H                PQ: 0 ANSI: 2 CCS
[  531.612033] not responding...
[  539.864017] sd 3:0:0:0: [sdc] READ CAPACITY failed
[  539.864031] sd 3:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  539.864040] sd 3:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[  539.864050] sd 3:0:0:0: [sdc] Add. Sense: Not ready to ready change, medium may have changed
[  542.616183] sd 3:0:0:0: [sdc] Test WP failed, assume Write Enabled
[  542.616196] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[  542.617833] sd 3:0:0:0: [sdc] Attached SCSI disk
[  542.620090] sd 3:0:0:0: Attached scsi generic sg4 type 0
[ 1028.196390] usb 5-4.3: reset high speed USB device using ehci_hcd and address 6
[ 1028.288420] usb 5-4.3: device firmware changed
[ 1028.289168] usb 5-4.3: USB disconnect, address 6
[ 1028.364304] usb 5-4.3: new high speed USB device using ehci_hcd and address 7
[ 1028.458225] usb 5-4.3: configuration #1 chosen from 1 choice
[ 1028.459885] scsi4 : SCSI emulation for USB Mass Storage devices
[ 1028.460719] usb-storage: device found at 7
[ 1028.460725] usb-storage: waiting for device to settle before scanning
[ 1033.461525] usb-storage: device scan complete
[ 1035.450733] scsi 4:0:0:0: Direct-Access     STT_FTM3 2GL25H                PQ: 0 ANSI: 2 CCS
[ 1053.965017] not responding...
[ 1062.212864] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 1062.212878] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1062.212889] sd 4:0:0:0: [sdc] Sense Key : Unit Attention [current] 
[ 1062.212898] sd 4:0:0:0: [sdc] Add. Sense: Not ready to ready change, medium may have changed
[ 1064.968396] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 1064.968419] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 1064.968654] sd 4:0:0:0: [sdc] Attached SCSI disk
[ 1064.968976] sd 4:0:0:0: Attached scsi generic sg4 type 0

```

---

### Post by dusan.saiko on 2009-04-27
I had this only once and the case was the disk was really damaged.

---

