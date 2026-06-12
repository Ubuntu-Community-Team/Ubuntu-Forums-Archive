---
title: "Rewriting Partition Table"
date: 2008-01-13
forum: Hardware &amp; Laptops
---

### Post by teh_howch on 2008-01-13
Hello everyone, This post is asking for how-to's and advice for restoring my dead external drive.  Last March I bought a WD MyBook Essential Edition (500GB) and experienced no problems until this past October, when the drive stopped mounting in XP and current versions of Linux.  When I plug the HDD into a USB port, the drive spins up and does the 'whir whir click' routine, indicating that the partition table is gone/unreadable, etc.  Recently I decided I would try to resurrect the drive (no harm in trying, right?) to recover data.  I plugged it into the computer and in syslog (dmesg) i got the following:
```

 [  292.500000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
 [  292.500000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
 [  292.504000] Initializing USB Mass Storage driver...
 [  292.504000] scsi2 : SCSI emulation for USB Mass Storage devices
 [  292.504000] usb-storage: device found at 4
 [  292.504000] usb-storage: waiting for device to settle before scanning
 [  292.504000] usbcore: registered new interface driver usb-storage
 [  292.504000] USB Mass Storage support registered.
 [  297.504000] usb-storage: device scan complete
 [  297.504000] scsi 2:0:0:0: Direct-Access     WD        External        101a PQ: 0 ANSI: 4
 [  297.524000] sd 2:0:0:0: [sdb] Unit Not Ready
 [  297.524000] sd 2:0:0:0: [sdb] Sense Key : Aborted Command [current] 
 [  297.524000] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information
 [  297.524000] sd 2:0:0:0: [sdb] Very big device. Trying to use READ CAPACITY(16).
 [  297.524000] sd 2:0:0:0: [sdb] READ CAPACITY(16) failed
 [  297.524000] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
 [  297.524000] sd 2:0:0:0: [sdb] Use 0xffffffff as device size
 [  297.524000] sd 2:0:0:0: [sdb] 4294967296 512-byte hardware sectors (2199023 MB)
 [  297.524000] sd 2:0:0:0: [sdb] Write Protect is off
 [  297.524000] sd 2:0:0:0: [sdb] Mode Sense: 11 00 00 00
 [  297.524000] sd 2:0:0:0: [sdb] Assuming drive cache: write through

```
At which point the 'Unit Not Ready' to 'write through' block repeats again, and then is followed by
```

 [  297.548000]  sdb:<6>sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
 [  297.556000] sd 2:0:0:0: [sdb] Sense Key : Aborted Command [current] 
 [  297.556000] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information
 [  297.556000] end_request: I/O error, dev sdb, sector 0
 [  297.556000] Buffer I/O error on device sdb, logical block 0

```
At this point, the following block repeats 4 times
```

 [  297.564000] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
 [  297.564000] sd 2:0:0:0: [sdb] Sense Key : Aborted Command [current] 
 [  297.564000] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information
 [  297.564000] end_request: I/O error, dev sdb, sector 0
 [  297.564000] Buffer I/O error on device sdb, logical block 0

```
And is followed by
```

 [  297.592000] ldm_validate_partition_table(): Disk read failed.

```
After which the I/O error block repeats 4 more times, this time followed by
```

 [  297.628000] Dev sdb: unable to read RDB block 0

```
Then continues that block, without the 'Buffer I/O error' line, 6 more times, finally ending with
```

 [  297.684000]  unable to read partition table
 [  297.684000] sd 2:0:0:0: [sdb] Attached SCSI disk
 [  297.684000] sd 2:0:0:0: Attached scsi generic sg2 type 0

```
After this, the commonly repeated block continues repeating, 84 more times.  The sectors listed as having I/O errors are 0, 24,  and 4294967XXX, where XXX is either 168, 232, 280, or 288.  Sector 0 is most common by far.

I wasn't sure where to go from here, so i ran gparted and it tells me that sdb has size '-2872832.00 B', DiskLabelType 'unrecognized', Heads '255', Sectors/Track '63', Cylinders '267349', and Total Secotrs '-5611'

People have mentioned that gparted has a restore functionality, but I can't seem to find it in the menus anywhere.

All help is appreciated greatly

---

