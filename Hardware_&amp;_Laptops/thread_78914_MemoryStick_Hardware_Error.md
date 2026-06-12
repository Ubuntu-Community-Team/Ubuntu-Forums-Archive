---
title: "MemoryStick Hardware Error"
date: 2005-10-19
forum: Hardware &amp; Laptops
---

### Post by matthias_k on 2005-10-19
Hi,

my 1GB Sandisk MemoryStick Duo does not work. I can mount it the first time, I can even copy to it, but when I want to unmount it I get strange error messages. I also can't mount it a second time, the whole thing breaks completely, I can't even shutdown my computer properly because it's reporting hardware errors (probably while trying to force-unmount on shutdown). I am using a TEAC multi-card reader to write to the disk. Here is what dmesg says:

> [4294871.115000] SCSI device sdb: 1947648 512-byte hdwr sectors (997 MB)
[4294871.116000] sdb: Write Protect is off
[4294871.116000] sdb: Mode Sense: 6a 10 00 04
[4294871.116000] sdb: assuming drive cache: write through
[4294871.118000] SCSI device sdb: 1947648 512-byte hdwr sectors (997 MB)
[4294871.119000] sdb: Write Protect is off
[4294871.119000] sdb: Mode Sense: 6a 10 00 04
[4294871.119000] sdb: assuming drive cache: write through
[4294871.119000]  /dev/scsi/host0/bus0/target0/lun1: p1
[4294871.212000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4294929.708000] Warning: /proc/ide/hd?/settings interface is obsolete, and will be removed soon!
[4294939.009000] SCSI error : <0 0 0 1> return code = 0x8000002
[4294939.009000] sdb: Current: sense key: Hardware Error
[4294939.009000]     Additional sense: Data phase error
[4294939.009000] end_request: I/O error, dev sdb, sector 608
[4294939.009000] Buffer I/O error on device sdb1, logical block 239
[4294939.009000] lost page write due to I/O error on sdb1
[4294960.429000] SCSI error : <0 0 0 1> return code = 0x8000002
[4294960.429000] sdb: Current: sense key: Hardware Error
[4294960.429000]     Additional sense: Data phase error
[4294960.429000] end_request: I/O error, dev sdb, sector 608
[4294960.429000] FAT: Directory bread(block 239) failed
[4294960.782000] SCSI error : <0 0 0 1> return code = 0x8000002
[4294960.782000] sdb: Current: sense key: Hardware Error
[4294960.782000]     Additional sense: Data phase error
[4294960.782000] end_request: I/O error, dev sdb, sector 608
[4294960.783000] FAT: Directory bread(block 239) failed
[4294961.568000] SCSI error : <0 0 0 1> return code = 0x8000002
[4294961.568000] sdb: Current: sense key: Hardware Error
[4294961.568000]     Additional sense: Data phase error
[4294961.568000] end_request: I/O error, dev sdb, sector 608
[4294961.569000] FAT: Directory bread(block 239) failed
[4294961.570000] SCSI error : <0 0 0 1> return code = 0x8000002
[4294961.570000] sdb: Current: sense key: Hardware Error
[4294961.570000]     Additional sense: Data phase error
[4294961.570000] end_request: I/O error, dev sdb, sector 608
[4294961.570000] FAT: Directory bread(block 239) failed
[4294962.569000] SCSI error : <0 0 0 1> return code = 0x8000002
[4294962.569000] sdb: Current: sense key: Hardware Error
[4294962.569000]     Additional sense: Data phase error
[4294962.569000] end_request: I/O error, dev sdb, sector 608
[4294962.569000] FAT: Directory bread(block 239) failed
[4294963.569000] SCSI error : <0 0 0 1> return code = 0x8000002
[4294963.569000] sdb: Current: sense key: Hardware Error
[4294963.569000]     Additional sense: Data phase error
[4294963.569000] end_request: I/O error, dev sdb, sector 608
[4294963.569000] FAT: Directory bread(block 239) failed
[4294964.570000] SCSI error : <0 0 0 1> return code = 0x8000002
[4294964.570000] sdb: Current: sense key: Hardware Error
[4294964.570000]     Additional sense: Data phase error
[4294964.570000] end_request: I/O error, dev sdb, sector 608
[4294964.570000] FAT: Directory bread(block 239) failed
[4294965.571000] SCSI error : <0 0 0 1> return code = 0x8000002
[4294965.571000] sdb: Current: sense key: Hardware Error
[4294965.571000]     Additional sense: Data phase error
[4294965.571000] end_request: I/O error, dev sdb, sector 608
[4294965.571000] FAT: Directory bread(block 239) failed
[4294966.572000] SCSI error : <0 0 0 1> return code = 0x8000002
[4294966.572000] sdb: Current: sense key: Hardware Error
[4294966.572000]     Additional sense: Data phase error
[4294966.572000] end_request: I/O error, dev sdb, sector 608
[4294966.572000] FAT: Directory bread(block 239) failed
[4294967.573000] SCSI error : <0 0 0 1> return code = 0x8000002
[4294967.573000] sdb: Current: sense key: Hardware Error
[4294967.573000]     Additional sense: Data phase error
[4294967.573000] end_request: I/O error, dev sdb, sector 608
[4294967.573000] FAT: Directory bread(block 239) failed
[4294968.574000] SCSI error : <0 0 0 1> return code = 0x8000002
[4294968.574000] sdb: Current: sense key: Hardware Error
[4294968.574000]     Additional sense: Data phase error
[4294968.574000] end_request: I/O error, dev sdb, sector 608
[4294968.574000] FAT: Directory bread(block 239) failed
[4294975.526000] SCSI error : <0 0 0 1> return code = 0x8000002
[4294975.526000] sdb: Current: sense key: Hardware Error
[4294975.526000]     Additional sense: Data phase error
[4294975.526000] end_request: I/O error, dev sdb, sector 608
[4294975.527000] FAT: Directory bread(block 239) failed
[4294975.529000] SCSI error : <0 0 0 1> return code = 0x8000002
[4294975.529000] sdb: Current: sense key: Hardware Error
[4294975.529000]     Additional sense: Data phase error
[4294975.529000] end_request: I/O error, dev sdb, sector 608
[4294975.530000] FAT: Directory bread(block 239) failed


I have no idea what is causing this. Can someone help, please?

---

