---
title: "External HD, remounting, powersaving"
date: 2007-11-19
forum: Hardware &amp; Laptops
---

### Post by dhaus111 on 2007-11-19
Hello all, gonna try to make this short and sweet.  I've got an external drive (Seagate Freeagent Pro hooked up using usb2) that I recently formatted as ext3 and loaded all my crap onto. after an undetermined period of inactivity (nothing ridiculous, probably 15-30 min) then a request for data from the drive, the drive remounts as readonly.  I'm not surprised by this, and I'm pretty sure it has to do with the fact that the drive spins down.  However, exactly what to do about this I'm also not too sure about.  I've experimented with hdparm etc, but to no avail.  I've also unmounted the drive and run an ext3 filesystem check on it, the errors are fixed without any problems, but there are more created as the cycle continues.  I really don't want to outright disable any powersaving features, as thats one of the main reasons I bought this drive, just didn't think linux would have such a problem with it.  After a filesystem fix, i remounted then let the drive idle for about 40 min, then accessed it, the drive spins up in a respectable amount of time (4-5 secs) then i see what i'm looking for, but the drive is mounted as readonly and my dmesg says this....


```
[ 2713.084996] synaptics: using relaxed packet validation
[ 2939.985788] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current] 
[ 2939.985801] : Add. Sense: Logical unit not ready, initializing command required
[ 2939.985819] end_request: I/O error, dev sdb, sector 12423
[ 2939.985826] Buffer I/O error on device sdb1, logical block 1545
[ 2939.985832] lost page write due to I/O error on sdb1
[ 2939.993394] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current] 
[ 2939.993414] : Add. Sense: Logical unit not ready, initializing command required
[ 2939.993424] end_request: I/O error, dev sdb, sector 543424591
[ 2939.993470] EXT3-fs error (device sdb1): ext3_get_inode_loc: unable to read inode block - inode=33964033, block=67928066
[ 2940.007268] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current] 
[ 2940.007292] : Add. Sense: Logical unit not ready, initializing command required
[ 2940.007301] end_request: I/O error, dev sdb, sector 63
[ 2940.007308] Buffer I/O error on device sdb1, logical block 0
[ 2940.007322] lost page write due to I/O error on sdb1
[ 4087.867197] usb 1-4: USB disconnect, address 4
[ 4100.570505] usb 1-4: new high speed USB device using ehci_hcd and address 6
[ 4100.815851] usb 1-4: configuration #1 chosen from 1 choice
[ 4100.846202] scsi3 : SCSI emulation for USB Mass Storage devices
[ 4100.852626] usb-storage: device found at 6
[ 4100.852635] usb-storage: waiting for device to settle before scanning
[ 4105.855932] usb-storage: device scan complete
[ 4105.858679] scsi 3:0:0:0: Direct-Access     Seagate  FreeAgent Pro    400A PQ: 0 ANSI: 4
[ 4105.863025] sd 3:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[ 4105.865784] sd 3:0:0:0: [sdb] Write Protect is off
[ 4105.865792] sd 3:0:0:0: [sdb] Mode Sense: 1c 00 00 00
[ 4105.865795] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 4105.869655] sd 3:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[ 4105.872394] sd 3:0:0:0: [sdb] Write Protect is off
[ 4105.872400] sd 3:0:0:0: [sdb] Mode Sense: 1c 00 00 00
[ 4105.872403] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 4105.872409]  sdb: sdb1
[ 4105.901019] sd 3:0:0:0: [sdb] Attached SCSI disk
[ 4105.901090] sd 3:0:0:0: Attached scsi generic sg2 type 0
[ 4107.368704] kjournald starting.  Commit interval 5 seconds
[ 4107.375918] EXT3 FS on sdb1, internal journal
[ 4107.375932] EXT3-fs: mounted filesystem with ordered data mode.
[ 7865.381534] sd 3:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current] 
[ 7865.381570] : Add. Sense: Logical unit not ready, initializing command required
[ 7865.381591] end_request: I/O error, dev sdb, sector 15351
[ 7865.389651] sd 3:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current] 
[ 7865.389691] : Add. Sense: Logical unit not ready, initializing command required
[ 7865.389716] end_request: I/O error, dev sdb, sector 15383
[ 7865.389730] Buffer I/O error on device sdb1, logical block 1915
[ 7865.389744] lost page write due to I/O error on sdb1
[ 7865.389826] Aborting journal on device sdb1.
[ 7865.676286] sd 3:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current] 
[ 7865.676297] : Add. Sense: Logical unit not ready, initializing command required
[ 7865.676305] end_request: I/O error, dev sdb, sector 543555647
[ 7865.679059] ext3_abort called.
[ 7865.679071] EXT3-fs error (device sdb1): ext3_journal_start_sb: Detected aborted journal
[ 7865.679077] Remounting filesystem read-only
```


I'm not sure how to interpret the syntax of [ 7865.679077]. does it have to do with time/date?

any help would be rewarded with good karma, as my unfortunate position currently entitles me to being a dealer
dustin

---

### Post by dhaus111 on 2007-11-20
anyzbodyz? whozez gotz some repliesz!  I reaaaaly need some help with this...

---

### Post by bdanilko on 2007-11-22
This looks like the drive powering down.
Check out this forum entry for the solution:
[http://ubuntuforums.org/showthread.php?t=494673](http://ubuntuforums.org/showthread.php?t=494673)

Brian

---

### Post by dhaus111 on 2007-12-03
sure enough, that did it for me, thanks bdanilko.  I did look around I promise...

---

