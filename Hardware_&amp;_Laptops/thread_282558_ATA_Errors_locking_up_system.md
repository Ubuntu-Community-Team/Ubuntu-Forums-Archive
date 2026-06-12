---
title: "ATA Errors locking up system"
date: 2006-10-22
forum: Hardware &amp; Laptops
---

### Post by Nicolae on 2006-10-22
When I try to copy files between my 2 SATA drives (This ONLY occurs when copying/moving between the 2-- copying/moving from the IDE drive to one of them or vice-versa still works fine. It actually worked fine when one of them (sda) was still NTFS and was mounted read-only.)

kern.log output when this occurs:
```
Oct 22 22:24:17 lesser****up kernel: [17181225.292000] ata2: translated ATA stat/err 0x51/84 to SCSI SK/ASC/ASCQ 0xb/47/00
Oct 22 22:24:17 lesser****up kernel: [17181225.292000] ata2: status=0x51 { DriveReady SeekComplete Error }
Oct 22 22:24:17 lesser****up kernel: [17181225.292000] ata2: error=0x84 { DriveStatusError BadCRC }
Oct 22 22:24:32 lesser****up kernel: [17181240.368000] ata2: translated ATA stat/err 0x51/84 to SCSI SK/ASC/ASCQ 0xb/47/00
Oct 22 22:24:32 lesser****up kernel: [17181240.368000] ata2: status=0x51 { DriveReady SeekComplete Error }
Oct 22 22:24:32 lesser****up kernel: [17181240.368000] ata2: error=0x84 { DriveStatusError BadCRC }
Oct 22 22:25:02 lesser****up kernel: [17181270.368000] ata2: command 0x25 timeout, stat 0xd1 host_stat 0x1
Oct 22 22:25:02 lesser****up kernel: [17181270.368000] ata2: translated ATA stat/err 0xd1/00 to SCSI SK/ASC/ASCQ 0xb/47/00
Oct 22 22:25:02 lesser****up kernel: [17181270.368000] ata2: status=0xd1 { Busy }
Oct 22 22:25:02 lesser****up kernel: [17181270.368000] sd 1:0:0:0: SCSI error: return code = 0x8000002
Oct 22 22:25:02 lesser****up kernel: [17181270.368000] sdb: Current: sense key: Aborted Command
Oct 22 22:25:02 lesser****up kernel: [17181270.368000]     Additional sense: Scsi parity error
Oct 22 22:25:02 lesser****up kernel: [17181270.368000] end_request: I/O error, dev sdb, sector 347982967
Oct 22 22:25:32 lesser****up kernel: [17181300.368000] ata2: command 0x25 timeout, stat 0xd1 host_stat 0x1
Oct 22 22:25:32 lesser****up kernel: [17181300.368000] ata2: translated ATA stat/err 0xd1/00 to SCSI SK/ASC/ASCQ 0xb/47/00
Oct 22 22:25:32 lesser****up kernel: [17181300.368000] ata2: status=0xd1 { Busy }
Oct 22 22:25:32 lesser****up kernel: [17181300.368000] sd 1:0:0:0: SCSI error: return code = 0x8000002
Oct 22 22:25:32 lesser****up kernel: [17181300.368000] sdb: Current: sense key: Aborted Command
Oct 22 22:25:32 lesser****up kernel: [17181300.368000]     Additional sense: Scsi parity error
Oct 22 22:25:32 lesser****up kernel: [17181300.368000] end_request: I/O error, dev sdb, sector 347982975
Oct 22 22:26:02 lesser****up kernel: [17181330.368000] ata2: command 0x25 timeout, stat 0xd1 host_stat 0x1
Oct 22 22:26:02 lesser****up kernel: [17181330.368000] ata2: translated ATA stat/err 0xd1/00 to SCSI SK/ASC/ASCQ 0xb/47/00
Oct 22 22:26:02 lesser****up kernel: [17181330.368000] ata2: status=0xd1 { Busy }
Oct 22 22:26:02 lesser****up kernel: [17181330.368000] sd 1:0:0:0: SCSI error: return code = 0x8000002
Oct 22 22:26:02 lesser****up kernel: [17181330.368000] sdb: Current: sense key: Aborted Command
Oct 22 22:26:02 lesser****up kernel: [17181330.368000]     Additional sense: Scsi parity error
Oct 22 22:26:02 lesser****up kernel: [17181330.368000] end_request: I/O error, dev sdb, sector 347982983
Oct 22 22:26:32 lesser****up kernel: [17181360.372000] ata2: command 0x25 timeout, stat 0xd1 host_stat 0x1
Oct 22 22:26:32 lesser****up kernel: [17181360.372000] ata2: translated ATA stat/err 0xd1/00 to SCSI SK/ASC/ASCQ 0xb/47/00
Oct 22 22:26:32 lesser****up kernel: [17181360.372000] ata2: status=0xd1 { Busy }
Oct 22 22:26:32 lesser****up kernel: [17181360.372000] sd 1:0:0:0: SCSI error: return code = 0x8000002
Oct 22 22:26:32 lesser****up kernel: [17181360.372000] sdb: Current: sense key: Aborted Command
Oct 22 22:26:32 lesser****up kernel: [17181360.372000]     Additional sense: Scsi parity error
Oct 22 22:26:32 lesser****up kernel: [17181360.372000] end_request: I/O error, dev sdb, sector 347982991
Oct 22 22:27:02 lesser****up kernel: [17181390.372000] ata2: command 0x25 timeout, stat 0xd1 host_stat 0x1
Oct 22 22:27:02 lesser****up kernel: [17181390.372000] ata2: translated ATA stat/err 0xd1/00 to SCSI SK/ASC/ASCQ 0xb/47/00
Oct 22 22:27:02 lesser****up kernel: [17181390.372000] ata2: status=0xd1 { Busy }
Oct 22 22:27:02 lesser****up kernel: [17181390.372000] sd 1:0:0:0: SCSI error: return code = 0x8000002
Oct 22 22:27:02 lesser****up kernel: [17181390.372000] sdb: Current: sense key: Aborted Command
Oct 22 22:27:02 lesser****up kernel: [17181390.372000]     Additional sense: Scsi parity error
Oct 22 22:27:02 lesser****up kernel: [17181390.372000] end_request: I/O error, dev sdb, sector 347982999
Oct 22 22:27:32 lesser****up kernel: [17181420.372000] ata2: command 0x25 timeout, stat 0xd1 host_stat 0x1
Oct 22 22:27:32 lesser****up kernel: [17181420.372000] ata2: translated ATA stat/err 0xd1/00 to SCSI SK/ASC/ASCQ 0xb/47/00
Oct 22 22:27:32 lesser****up kernel: [17181420.372000] ata2: status=0xd1 { Busy }
Oct 22 22:27:32 lesser****up kernel: [17181420.372000] sd 1:0:0:0: SCSI error: return code = 0x8000002
Oct 22 22:27:32 lesser****up kernel: [17181420.372000] sdb: Current: sense key: Aborted Command
Oct 22 22:27:32 lesser****up kernel: [17181420.372000]     Additional sense: Scsi parity error
Oct 22 22:27:32 lesser****up kernel: [17181420.372000] end_request: I/O error, dev sdb, sector 347983007
Oct 22 22:28:02 lesser****up kernel: [17181450.372000] ata2: command 0x25 timeout, stat 0xd1 host_stat 0x1
Oct 22 22:28:02 lesser****up kernel: [17181450.372000] ata2: translated ATA stat/err 0xd1/00 to SCSI SK/ASC/ASCQ 0xb/47/00
Oct 22 22:28:02 lesser****up kernel: [17181450.372000] ata2: status=0xd1 { Busy }
Oct 22 22:28:02 lesser****up kernel: [17181450.372000] sd 1:0:0:0: SCSI error: return code = 0x8000002
Oct 22 22:28:02 lesser****up kernel: [17181450.372000] sdb: Current: sense key: Aborted Command
Oct 22 22:28:02 lesser****up kernel: [17181450.372000]     Additional sense: Scsi parity error
Oct 22 22:28:02 lesser****up kernel: [17181450.372000] end_request: I/O error, dev sdb, sector 347983015
Oct 22 22:28:32 lesser****up kernel: [17181480.372000] ata2: command 0x25 timeout, stat 0xd1 host_stat 0x1
Oct 22 22:28:32 lesser****up kernel: [17181480.372000] ata2: translated ATA stat/err 0xd1/00 to SCSI SK/ASC/ASCQ 0xb/47/00
Oct 22 22:28:32 lesser****up kernel: [17181480.372000] ata2: status=0xd1 { Busy }
Oct 22 22:28:32 lesser****up kernel: [17181480.372000] sd 1:0:0:0: SCSI error: return code = 0x8000002
Oct 22 22:28:32 lesser****up kernel: [17181480.372000] sdb: Current: sense key: Aborted Command
Oct 22 22:28:32 lesser****up kernel: [17181480.372000]     Additional sense: Scsi parity error
Oct 22 22:28:32 lesser****up kernel: [17181480.372000] end_request: I/O error, dev sdb, sector 347983023
```

(Yes, I named my computer lesser****up (uncensored))

My chipset is via 8237, I'm running edgy 32bit.
The hard drives are a Maxtor DiamondMAx10 (250 GB, sda) and a WD Caviar(?) SE 400 GB (sdb)

---

### Post by Nicolae on 2006-10-24
I've compiled a new kernel (2.6.18 with the 2.6.18-mm3 patch) and I'm getting different errors copying files now: 

```
Oct 24 15:49:19 lesser****up kernel: [ 1761.554067] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Oct 24 15:49:19 lesser****up kernel: [ 1761.554082] ata2: soft resetting port
Oct 24 15:49:19 lesser****up kernel: [ 1761.719638] ata2.00: configured for PIO0
Oct 24 15:49:19 lesser****up kernel: [ 1761.719651] ata2: EH complete
Oct 24 15:49:19 lesser****up kernel: [ 1761.741805] ata2.00: speed down requested but no transfer mode left
Oct 24 15:49:19 lesser****up kernel: [ 1761.741809] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
Oct 24 15:49:19 lesser****up kernel: [ 1761.741812] ata2.00: tag 0 cmd 0x29 Emask 0x10 stat 0x51 err 0x84 (ATA bus error)
```

According to the log it started with "configured for UDMA/133" and began stepping down after subsequent errors. It's not locking up the system, though, and the errors go away after I unmount the disk. I still need to fix this, though.

---

