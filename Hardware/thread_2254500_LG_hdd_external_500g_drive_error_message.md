---
title: "LG hdd external 500g drive error message"
date: 2014-11-27
forum: Hardware
---

### Post by anisterra on 2014-11-27
Hello, 

When trying to mount my LG hdd external 500g drive i got this error message
[INDENT]Error mounting: mount: wrong fs type, bad options, bad superblock on /dev/sdb1, missing codepage helper program or other error
In some cases useful info is found in syslog -try demsg|tail or so.
[/INDENT]
 
Reading dmesg.o at dmesg.3.gz   found: 
[INDENT]scsi 6:0:0:0: Direct-Access              LG External HDD  JE3O PQ: 0 ANSI: 5
[    3.001444] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    3.002969] sd 6:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    3.003710] sd 6:0:0:0: [sdb] Write Protect is off
[    3.003713] sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00
[    3.004470] sd 6:0:0:0: [sdb] No Caching mode page found
[    3.004472] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    3.006834] sd 6:0:0:0: [sdb] No Caching mode page found
[    3.006836] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    3.007380]  sdb: sdb1
[    3.010334] sd 6:0:0:0: [sdb] No Caching mode page found
[    3.010336] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    3.010339] sd 6:0:0:0: [sdb] Attached SCSI disk
[    3.359876] sd 6:0:0:0: [sdb] Unhandled sense code
[    3.359880] sd 6:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[    3.359884] sd 6:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[    3.359888] sd 6:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[    3.359893] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 01 00 00 00 08 00
[    3.359902] end_request: critical target error, dev sdb, sector 256
[    3.359904] Buffer I/O error on device sdb, logical block 32
[    3.515355] sd 6:0:0:0: [sdb] Unhandled sense code
[    3.515359] sd 6:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[    3.515362] sd 6:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[    3.515366] sd 6:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[    3.515371] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 01 00 00 00 08 00
[    3.515380] end_request: critical target error, dev sdb, sector 256
[    3.515383] Buffer I/O error on device sdb, logical block 32
[/INDENT]
 
Can anybody tell looking at the log me if the hdd has a  logical or a physical failure ?  
Thanx in advance . ( Just in case, i am spanish speaking user )

---

