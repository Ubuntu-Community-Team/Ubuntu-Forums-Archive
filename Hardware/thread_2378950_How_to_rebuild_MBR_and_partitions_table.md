---
title: "How to rebuild MBR and partitions table"
date: 2017-11-29
forum: Hardware
---

### Post by johnluk on 2017-11-29
Hello everyone, 
I have a problem of my 3TB hard disk. I tried the "boot repair" .
boot repair show me this:
                                     Invalid MBR Signature found. Unknown MBR on /dev/sdb

And I also tried the "testdisk":
                but show me the incorrect size of my 3TB on sdb, only see 4142 MB / 3950 MiB. So I can't move to next step.

Please help me!

```
dmesg | grep sdb
[   84.193165] sd 6:0:0:0: [sdb] 8089950 512-byte logical blocks: (4.14 GB/3.86 GiB)
[   84.193530] sd 6:0:0:0: [sdb] Write Protect is off
[   84.193534] sd 6:0:0:0: [sdb] Mode Sense: 43 00 00 00
[   84.194283] sd 6:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   84.198150] sd 6:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   84.198153] sd 6:0:0:0: [sdb] tag#0 Sense Key : Illegal Request [current] 
[   84.198155] sd 6:0:0:0: [sdb] tag#0 Add. Sense: Invalid field in cdb
[   84.198157] sd 6:0:0:0: [sdb] tag#0 CDB: Read(10) 28 00 00 00 00 00 00 00 02 00
[   84.198159] print_req_error: critical target error, dev sdb, sector 0
[   84.198162] Buffer I/O error on dev sdb, logical block 0, async page read
[   84.198168] sd 6:0:0:0: [sdb] tag#1 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   84.198169] sd 6:0:0:0: [sdb] tag#1 Sense Key : Illegal Request [current] 
[   84.198171] sd 6:0:0:0: [sdb] tag#1 Add. Sense: Invalid field in cdb
[   84.198172] sd 6:0:0:0: [sdb] tag#1 CDB: Read(10) 28 00 00 00 00 02 00 00 02 00
[   84.198173] print_req_error: critical target error, dev sdb, sector 2
[   84.198175] Buffer I/O error on dev sdb, logical block 1, async page read
[   84.198179] sd 6:0:0:0: [sdb] tag#2 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   84.198180] sd 6:0:0:0: [sdb] tag#2 Sense Key : Illegal Request [current] 
[   84.198181] sd 6:0:0:0: [sdb] tag#2 Add. Sense: Invalid field in cdb
[   84.198183] sd 6:0:0:0: [sdb] tag#2 CDB: Read(10) 28 00 00 00 00 04 00 00 02 00
[   84.198184] print_req_error: critical target error, dev sdb, sector 4
[   84.198185] Buffer I/O error on dev sdb, logical block 2, async page read
[   84.198268] sd 6:0:0:0: [sdb] tag#3 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   84.198269] sd 6:0:0:0: [sdb] tag#3 Sense Key : Illegal Request [current] 
[   84.198271] sd 6:0:0:0: [sdb] tag#3 Add. Sense: Invalid field in cdb
[   84.198272] sd 6:0:0:0: [sdb] tag#3 CDB: Read(10) 28 00 00 00 00 06 00 00 02 00
[   84.198273] print_req_error: critical target error, dev sdb, sector 6
[   84.198274] Buffer I/O error on dev sdb, logical block 3, async page read
[   84.198770] sd 6:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   84.198772] sd 6:0:0:0: [sdb] tag#0 Sense Key : Illegal Request [current] 
[   84.198773] sd 6:0:0:0: [sdb] tag#0 Add. Sense: Invalid field in cdb
[   84.198775] sd 6:0:0:0: [sdb] tag#0 CDB: Read(10) 28 00 00 00 00 00 00 00 02 00
[   84.198776] print_req_error: critical target error, dev sdb, sector 0
[   84.198777] Buffer I/O error on dev sdb, logical block 0, async page read
[   84.198781] sd 6:0:0:0: [sdb] tag#1 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   84.198783] sd 6:0:0:0: [sdb] tag#1 Sense Key : Illegal Request [current] 
[   84.198784] sd 6:0:0:0: [sdb] tag#1 Add. Sense: Invalid field in cdb
[   84.198786] sd 6:0:0:0: [sdb] tag#1 CDB: Read(10) 28 00 00 00 00 02 00 00 02 00
[   84.198787] print_req_error: critical target error, dev sdb, sector 2
[   84.198788] Buffer I/O error on dev sdb, logical block 1, async page read
[   84.198897] sd 6:0:0:0: [sdb] tag#2 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   84.198899] sd 6:0:0:0: [sdb] tag#2 Sense Key : Illegal Request [current] 
[   84.198901] sd 6:0:0:0: [sdb] tag#2 Add. Sense: Invalid field in cdb
[   84.198903] sd 6:0:0:0: [sdb] tag#2 CDB: Read(10) 28 00 00 00 00 04 00 00 02 00
[   84.198905] print_req_error: critical target error, dev sdb, sector 4
[   84.198907] Buffer I/O error on dev sdb, logical block 2, async page read
[   84.198912] sd 6:0:0:0: [sdb] tag#3 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   84.198914] sd 6:0:0:0: [sdb] tag#3 Sense Key : Illegal Request [current] 
[   84.198916] sd 6:0:0:0: [sdb] tag#3 Add. Sense: Invalid field in cdb
[   84.198918] sd 6:0:0:0: [sdb] tag#3 CDB: Read(10) 28 00 00 00 00 06 00 00 02 00
[   84.198919] print_req_error: critical target error, dev sdb, sector 6
[   84.198921] Buffer I/O error on dev sdb, logical block 3, async page read
[   84.199400] sd 6:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   84.199403] sd 6:0:0:0: [sdb] tag#0 Sense Key : Illegal Request [current] 
[   84.199405] sd 6:0:0:0: [sdb] tag#0 Add. Sense: Invalid field in cdb
[   84.199407] sd 6:0:0:0: [sdb] tag#0 CDB: Read(10) 28 00 00 00 00 00 00 00 02 00
[   84.199409] print_req_error: critical target error, dev sdb, sector 0
[   84.199412] Buffer I/O error on dev sdb, logical block 0, async page read
[   84.199524] sd 6:0:0:0: [sdb] tag#1 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   84.199526] sd 6:0:0:0: [sdb] tag#1 Sense Key : Illegal Request [current] 
[   84.199528] sd 6:0:0:0: [sdb] tag#1 Add. Sense: Invalid field in cdb
[   84.199530] sd 6:0:0:0: [sdb] tag#1 CDB: Read(10) 28 00 00 00 00 02 00 00 02 00
[   84.199531] print_req_error: critical target error, dev sdb, sector 2
[   84.199534] Buffer I/O error on dev sdb, logical block 1, async page read
[   84.202157] Dev sdb: unable to read RDB block 0
[   84.205281]  sdb: unable to read partition table
[   84.208651] sd 6:0:0:0: [sdb] Attached SCSI disk
[  175.603684] sd 6:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  175.603690] sd 6:0:0:0: [sdb] tag#0 Sense Key : Illegal Request [current] 
[  175.603694] sd 6:0:0:0: [sdb] tag#0 Add. Sense: Invalid field in cdb
[  175.603699] sd 6:0:0:0: [sdb] tag#0 CDB: Read(10) 28 00 00 7b 70 80 00 00 08 00
[  175.603703] print_req_error: critical target error, dev sdb, sector 8089728
[  175.604173] sd 6:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  175.604177] sd 6:0:0:0: [sdb] tag#0 Sense Key : Illegal Request [current] 
[  175.604181] sd 6:0:0:0: [sdb] tag#0 Add. Sense: Invalid field in cdb
[  175.604185] sd 6:0:0:0: [sdb] tag#0 CDB: Read(10) 28 00 00 7b 70 80 00 00 02 00
[  175.604187] print_req_error: critical target error, dev sdb, sector 8089728
[  175.604193] Buffer I/O error on dev sdb, logical block 4044864, async page read
[  175.604297] sd 6:0:0:0: [sdb] tag#1 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  175.604300] sd 6:0:0:0: [sdb] tag#1 Sense Key : Illegal Request [current] 
[  175.604304] sd 6:0:0:0: [sdb] tag#1 Add. Sense: Invalid field in cdb
[  175.604307] sd 6:0:0:0: [sdb] tag#1 CDB: Read(10) 28 00 00 7b 70 82 00 00 02 00
[  175.604309] print_req_error: critical target error, dev sdb, sector 8089730
[  175.604313] Buffer I/O error on dev sdb, logical block 4044865, async page read
[  175.604324] sd 6:0:0:0: [sdb] tag#2 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  175.604327] sd 6:0:0:0: [sdb] tag#2 Sense Key : Illegal Request [current] 
[  175.604331] sd 6:0:0:0: [sdb] tag#2 Add. Sense: Invalid field in cdb
[  175.604334] sd 6:0:0:0: [sdb] tag#2 CDB: Read(10) 28 00 00 7b 70 84 00 00 02 00
[  175.604336] print_req_error: critical target error, dev sdb, sector 8089732
[  175.604339] Buffer I/O error on dev sdb, logical block 4044866, async page read
[  175.604420] sd 6:0:0:0: [sdb] tag#3 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  175.604423] sd 6:0:0:0: [sdb] tag#3 Sense Key : Illegal Request [current] 
[  175.604426] sd 6:0:0:0: [sdb] tag#3 Add. Sense: Invalid field in cdb
[  175.604430] sd 6:0:0:0: [sdb] tag#3 CDB: Read(10) 28 00 00 7b 70 86 00 00 02 00
[  175.604432] print_req_error: critical target error, dev sdb, sector 8089734
[  175.604435] Buffer I/O error on dev sdb, logical block 4044867, async page read
[  176.682625] sd 6:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  176.682628] sd 6:0:0:0: [sdb] tag#0 Sense Key : Illegal Request [current] 
[  176.682630] sd 6:0:0:0: [sdb] tag#0 Add. Sense: Invalid field in cdb
[  176.682633] sd 6:0:0:0: [sdb] tag#0 CDB: Read(10) 28 00 00 7b 70 80 00 00 08 00
[  176.682634] print_req_error: critical target error, dev sdb, sector 8089728
[  176.683621] sd 6:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  176.683623] sd 6:0:0:0: [sdb] tag#0 Sense Key : Medium Error [current] 
[  176.683624] sd 6:0:0:0: [sdb] tag#0 Add. Sense: Unrecovered read error
[  176.683626] sd 6:0:0:0: [sdb] tag#0 CDB: Read(10) 28 00 00 7b 70 80 00 00 02 00
[  176.683627] print_req_error: critical medium error, dev sdb, sector 8089728
[  176.683630] Buffer I/O error on dev sdb, logical block 4044864, async page read
[  176.683870] sd 6:0:0:0: [sdb] tag#1 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  176.683872] sd 6:0:0:0: [sdb] tag#1 Sense Key : Illegal Request [current] 
[  176.683873] sd 6:0:0:0: [sdb] tag#1 Add. Sense: Invalid field in cdb
[  176.683875] sd 6:0:0:0: [sdb] tag#1 CDB: Read(10) 28 00 00 7b 70 82 00 00 02 00
[  176.683876] print_req_error: critical target error, dev sdb, sector 8089730
[  176.683877] Buffer I/O error on dev sdb, logical block 4044865, async page read
[  176.683883] sd 6:0:0:0: [sdb] tag#2 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  176.683884] sd 6:0:0:0: [sdb] tag#2 Sense Key : Illegal Request [current] 
[  176.683886] sd 6:0:0:0: [sdb] tag#2 Add. Sense: Invalid field in cdb
[  176.683887] sd 6:0:0:0: [sdb] tag#2 CDB: Read(10) 28 00 00 7b 70 84 00 00 02 00
[  176.683888] print_req_error: critical target error, dev sdb, sector 8089732
[  176.683889] Buffer I/O error on dev sdb, logical block 4044866, async page read
[  176.683994] sd 6:0:0:0: [sdb] tag#3 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  176.683995] sd 6:0:0:0: [sdb] tag#3 Sense Key : Illegal Request [current] 
[  176.683997] sd 6:0:0:0: [sdb] tag#3 Add. Sense: Invalid field in cdb
[  176.683998] sd 6:0:0:0: [sdb] tag#3 CDB: Read(10) 28 00 00 7b 70 86 00 00 02 00
[  176.683999] print_req_error: critical target error, dev sdb, sector 8089734
[  176.684001] Buffer I/O error on dev sdb, logical block 4044867, async page read
[  176.697873] Buffer I/O error on dev sdb, logical block 1, async page read
[  176.697884] Buffer I/O error on dev sdb, logical block 0, async page read
[  207.958538] sd 6:0:0:0: [sdb] tag#3 uas_eh_abort_handler 0 uas-tag 4 inflight: CMD 
[  207.958547] sd 6:0:0:0: [sdb] tag#3 CDB: Read(10) 28 00 00 00 00 06 00 00 02 00
[  207.958557] sd 6:0:0:0: [sdb] tag#2 uas_eh_abort_handler 0 uas-tag 3 inflight: CMD 
[  207.958561] sd 6:0:0:0: [sdb] tag#2 CDB: Read(10) 28 00 00 00 00 04 00 00 02 00
[  207.958568] sd 6:0:0:0: [sdb] tag#1 uas_eh_abort_handler 0 uas-tag 2 inflight: CMD 
[  207.958572] sd 6:0:0:0: [sdb] tag#1 CDB: Read(10) 28 00 00 00 00 02 00 00 02 00
[  207.958579] sd 6:0:0:0: [sdb] tag#0 uas_eh_abort_handler 0 uas-tag 1 inflight: CMD 
[  207.958583] sd 6:0:0:0: [sdb] tag#0 CDB: Read(10) 28 00 00 00 00 00 00 00 02 00
[  208.258938] sd 6:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  208.258944] sd 6:0:0:0: [sdb] tag#0 Sense Key : Medium Error [current] 
[  208.258949] sd 6:0:0:0: [sdb] tag#0 Add. Sense: Unrecovered read error
[  208.258955] sd 6:0:0:0: [sdb] tag#0 CDB: Read(10) 28 00 00 00 00 06 00 00 02 00
[  208.258964] print_req_error: critical medium error, dev sdb, sector 6
[  208.258976] Buffer I/O error on dev sdb, logical block 3, async page read
[  208.259040] sd 6:0:0:0: [sdb] tag#1 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  208.259043] sd 6:0:0:0: [sdb] tag#1 Sense Key : Illegal Request [current] 
[  208.259046] sd 6:0:0:0: [sdb] tag#1 Add. Sense: Invalid field in cdb
[  208.259049] sd 6:0:0:0: [sdb] tag#1 CDB: Read(10) 28 00 00 00 00 04 00 00 02 00
[  208.259051] print_req_error: critical target error, dev sdb, sector 4
[  208.259054] Buffer I/O error on dev sdb, logical block 2, async page read
[  208.259166] sd 6:0:0:0: [sdb] tag#2 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  208.259169] sd 6:0:0:0: [sdb] tag#2 Sense Key : Illegal Request [current] 
[  208.259172] sd 6:0:0:0: [sdb] tag#2 Add. Sense: Invalid field in cdb
[  208.259174] sd 6:0:0:0: [sdb] tag#2 CDB: Read(10) 28 00 00 00 00 02 00 00 02 00
[  208.259176] print_req_error: critical target error, dev sdb, sector 2
[  208.259179] Buffer I/O error on dev sdb, logical block 1, async page read
[  208.259289] sd 6:0:0:0: [sdb] tag#3 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  208.259292] sd 6:0:0:0: [sdb] tag#3 Sense Key : Illegal Request [current] 
[  208.259295] sd 6:0:0:0: [sdb] tag#3 Add. Sense: Invalid field in cdb
[  208.259297] sd 6:0:0:0: [sdb] tag#3 CDB: Read(10) 28 00 00 00 00 00 00 00 02 00
[  208.259299] print_req_error: critical target error, dev sdb, sector 0
[  208.259301] Buffer I/O error on dev sdb, logical block 0, async page read
[  208.259792] sd 6:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  208.259795] sd 6:0:0:0: [sdb] tag#0 Sense Key : Illegal Request [current] 
[  208.259798] sd 6:0:0:0: [sdb] tag#0 Add. Sense: Invalid field in cdb
[  208.259801] sd 6:0:0:0: [sdb] tag#0 CDB: Read(10) 28 00 00 00 00 00 00 00 02 00
[  208.259802] print_req_error: critical target error, dev sdb, sector 0
[  208.259805] Buffer I/O error on dev sdb, logical block 0, async page read
[  208.259924] sd 6:0:0:0: [sdb] tag#1 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  208.259928] sd 6:0:0:0: [sdb] tag#1 Sense Key : Illegal Request [current] 
[  208.259932] sd 6:0:0:0: [sdb] tag#1 Add. Sense: Invalid field in cdb
[  208.259935] sd 6:0:0:0: [sdb] tag#1 CDB: Read(10) 28 00 00 00 00 02 00 00 02 00
[  208.259937] print_req_error: critical target error, dev sdb, sector 2
[  208.259941] Buffer I/O error on dev sdb, logical block 1, async page read
[  208.259952] sd 6:0:0:0: [sdb] tag#2 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  208.259955] sd 6:0:0:0: [sdb] tag#2 Sense Key : Illegal Request [current] 
[  208.259960] sd 6:0:0:0: [sdb] tag#2 Add. Sense: Invalid field in cdb
[  208.259964] sd 6:0:0:0: [sdb] tag#2 CDB: Read(10) 28 00 00 00 00 04 00 00 02 00
[  208.259966] print_req_error: critical target error, dev sdb, sector 4
[  208.259969] Buffer I/O error on dev sdb, logical block 2, async page read
[  208.259980] sd 6:0:0:0: [sdb] tag#3 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  208.259984] sd 6:0:0:0: [sdb] tag#3 Sense Key : Illegal Request [current] 
[  208.259987] sd 6:0:0:0: [sdb] tag#3 Add. Sense: Invalid field in cdb
[  208.259991] sd 6:0:0:0: [sdb] tag#3 CDB: Read(10) 28 00 00 00 00 06 00 00 02 00
[  208.259993] print_req_error: critical target error, dev sdb, sector 6
[  208.259996] Buffer I/O error on dev sdb, logical block 3, async page read
[  208.260543] sd 6:0:0:0: [sdb] tag#1 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  208.260546] sd 6:0:0:0: [sdb] tag#1 Sense Key : Illegal Request [current] 
[  208.260549] sd 6:0:0:0: [sdb] tag#1 Add. Sense: Invalid field in cdb
[  208.260552] sd 6:0:0:0: [sdb] tag#1 CDB: Read(10) 28 00 00 00 00 02 00 00 02 00
[  208.260554] print_req_error: critical target error, dev sdb, sector 2
[  208.260557] Buffer I/O error on dev sdb, logical block 1, async page read
[  208.260567] sd 6:0:0:0: [sdb] tag#2 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  208.260570] sd 6:0:0:0: [sdb] tag#2 Sense Key : Illegal Request [current] 
[  208.260573] sd 6:0:0:0: [sdb] tag#2 Add. Sense: Invalid field in cdb
[  208.260575] sd 6:0:0:0: [sdb] tag#2 CDB: Read(10) 28 00 00 00 00 04 00 00 02 00
[  208.260576] print_req_error: critical target error, dev sdb, sector 4
[  208.260579] Buffer I/O error on dev sdb, logical block 2, async page read
[  208.267459] Dev sdb: unable to read RDB block 0
[  208.270807]  sdb: unable to read partition table
[  240.727268] sd 6:0:0:0: [sdb] tag#3 uas_eh_abort_handler 0 uas-tag 4 inflight: CMD 
[  240.727275] sd 6:0:0:0: [sdb] tag#3 CDB: Read(10) 28 00 00 00 00 06 00 00 02 00
[  240.727285] sd 6:0:0:0: [sdb] tag#2 uas_eh_abort_handler 0 uas-tag 3 inflight: CMD 
[  240.727290] sd 6:0:0:0: [sdb] tag#2 CDB: Read(10) 28 00 00 00 00 04 00 00 02 00
[  240.727296] sd 6:0:0:0: [sdb] tag#1 uas_eh_abort_handler 0 uas-tag 2 inflight: CMD 
[  240.727300] sd 6:0:0:0: [sdb] tag#1 CDB: Read(10) 28 00 00 00 00 02 00 00 02 00
[  241.020290] sd 6:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  241.020295] sd 6:0:0:0: [sdb] tag#0 Sense Key : Illegal Request [current] 
[  241.020301] sd 6:0:0:0: [sdb] tag#0 Add. Sense: Invalid field in cdb
[  241.020306] sd 6:0:0:0: [sdb] tag#0 CDB: Read(10) 28 00 00 00 00 06 00 00 02 00
[  241.020312] print_req_error: critical target error, dev sdb, sector 6
[  241.020321] Buffer I/O error on dev sdb, logical block 3, async page read
[  241.020394] sd 6:0:0:0: [sdb] tag#1 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  241.020396] sd 6:0:0:0: [sdb] tag#1 Sense Key : Illegal Request [current] 
[  241.020398] sd 6:0:0:0: [sdb] tag#1 Add. Sense: Invalid field in cdb
[  241.020400] sd 6:0:0:0: [sdb] tag#1 CDB: Read(10) 28 00 00 00 00 04 00 00 02 00
[  241.020402] print_req_error: critical target error, dev sdb, sector 4
[  241.020404] Buffer I/O error on dev sdb, logical block 2, async page read
[  241.020411] sd 6:0:0:0: [sdb] tag#2 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  241.020413] sd 6:0:0:0: [sdb] tag#2 Sense Key : Illegal Request [current] 
[  241.020415] sd 6:0:0:0: [sdb] tag#2 Add. Sense: Invalid field in cdb
[  241.020417] sd 6:0:0:0: [sdb] tag#2 CDB: Read(10) 28 00 00 00 00 02 00 00 02 00
[  241.020418] print_req_error: critical target error, dev sdb, sector 2
[  241.020420] Buffer I/O error on dev sdb, logical block 1, async page read
[  241.020896] sd 6:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  241.020898] sd 6:0:0:0: [sdb] tag#0 Sense Key : Medium Error [current] 
[  241.020900] sd 6:0:0:0: [sdb] tag#0 Add. Sense: Unrecovered read error
[  241.020902] sd 6:0:0:0: [sdb] tag#0 CDB: Read(10) 28 00 00 00 00 00 00 00 02 00
[  241.020903] print_req_error: critical medium error, dev sdb, sector 0
[  241.020906] Buffer I/O error on dev sdb, logical block 0, async page read
[  241.021019] sd 6:0:0:0: [sdb] tag#1 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  241.021021] sd 6:0:0:0: [sdb] tag#1 Sense Key : Illegal Request [current] 
[  241.021023] sd 6:0:0:0: [sdb] tag#1 Add. Sense: Invalid field in cdb
[  241.021025] sd 6:0:0:0: [sdb] tag#1 CDB: Read(10) 28 00 00 00 00 02 00 00 02 00
[  241.021026] print_req_error: critical target error, dev sdb, sector 2
[  241.021028] Buffer I/O error on dev sdb, logical block 1, async page read
[  241.021142] sd 6:0:0:0: [sdb] tag#2 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  241.021144] sd 6:0:0:0: [sdb] tag#2 Sense Key : Illegal Request [current] 
[  241.021146] sd 6:0:0:0: [sdb] tag#2 Add. Sense: Invalid field in cdb
[  241.021148] sd 6:0:0:0: [sdb] tag#2 CDB: Read(10) 28 00 00 00 00 04 00 00 02 00
[  241.021149] print_req_error: critical target error, dev sdb, sector 4
[  241.021151] Buffer I/O error on dev sdb, logical block 2, async page read
[  241.021267] sd 6:0:0:0: [sdb] tag#3 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  241.021269] sd 6:0:0:0: [sdb] tag#3 Sense Key : Illegal Request [current] 
[  241.021271] sd 6:0:0:0: [sdb] tag#3 Add. Sense: Invalid field in cdb
[  241.021273] sd 6:0:0:0: [sdb] tag#3 CDB: Read(10) 28 00 00 00 00 06 00 00 02 00
[  241.021274] print_req_error: critical target error, dev sdb, sector 6
[  241.021275] Buffer I/O error on dev sdb, logical block 3, async page read
[  241.021770] sd 6:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  241.021772] sd 6:0:0:0: [sdb] tag#0 Sense Key : Illegal Request [current] 
[  241.021775] sd 6:0:0:0: [sdb] tag#0 Add. Sense: Invalid field in cdb
[  241.021777] sd 6:0:0:0: [sdb] tag#0 CDB: Read(10) 28 00 00 00 00 00 00 00 02 00
[  241.021778] print_req_error: critical target error, dev sdb, sector 0
[  241.021780] Buffer I/O error on dev sdb, logical block 0, async page read
[  241.021788] sd 6:0:0:0: [sdb] tag#1 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  241.021790] sd 6:0:0:0: [sdb] tag#1 Sense Key : Illegal Request [current] 
[  241.021792] sd 6:0:0:0: [sdb] tag#1 Add. Sense: Invalid field in cdb
[  241.021793] sd 6:0:0:0: [sdb] tag#1 CDB: Read(10) 28 00 00 00 00 02 00 00 02 00
[  241.021794] print_req_error: critical target error, dev sdb, sector 2
[  241.021796] Buffer I/O error on dev sdb, logical block 1, async page read
[  241.021893] sd 6:0:0:0: [sdb] tag#2 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  241.021895] sd 6:0:0:0: [sdb] tag#2 Sense Key : Illegal Request [current] 
[  241.021897] sd 6:0:0:0: [sdb] tag#2 Add. Sense: Invalid field in cdb
[  241.021899] sd 6:0:0:0: [sdb] tag#2 CDB: Read(10) 28 00 00 00 00 04 00 00 02 00
[  241.021900] print_req_error: critical target error, dev sdb, sector 4
[  241.021902] Buffer I/O error on dev sdb, logical block 2, async page read
[  251.485028] sd 6:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  251.485033] sd 6:0:0:0: [sdb] tag#0 Sense Key : Illegal Request [current] 
[  251.485038] sd 6:0:0:0: [sdb] tag#0 Add. Sense: Invalid field in cdb
[  251.485043] sd 6:0:0:0: [sdb] tag#0 CDB: Read(10) 28 00 00 7b 70 80 00 00 08 00
[  251.485047] print_req_error: critical target error, dev sdb, sector 8089728
[  251.486010] sd 6:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  251.486014] sd 6:0:0:0: [sdb] tag#0 Sense Key : Medium Error [current] 
[  251.486018] sd 6:0:0:0: [sdb] tag#0 Add. Sense: Unrecovered read error
[  251.486022] sd 6:0:0:0: [sdb] tag#0 CDB: Read(10) 28 00 00 7b 70 80 00 00 02 00
[  251.486025] print_req_error: critical medium error, dev sdb, sector 8089728
[  251.486032] Buffer I/O error on dev sdb, logical block 4044864, async page read
[  251.486256] sd 6:0:0:0: [sdb] tag#1 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  251.486259] sd 6:0:0:0: [sdb] tag#1 Sense Key : Illegal Request [current] 
[  251.486262] sd 6:0:0:0: [sdb] tag#1 Add. Sense: Invalid field in cdb
[  251.486266] sd 6:0:0:0: [sdb] tag#1 CDB: Read(10) 28 00 00 7b 70 82 00 00 02 00
[  251.486268] print_req_error: critical target error, dev sdb, sector 8089730
[  251.486272] Buffer I/O error on dev sdb, logical block 4044865, async page read
[  251.486283] sd 6:0:0:0: [sdb] tag#2 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  251.486286] sd 6:0:0:0: [sdb] tag#2 Sense Key : Illegal Request [current] 
[  251.486290] sd 6:0:0:0: [sdb] tag#2 Add. Sense: Invalid field in cdb
[  251.486293] sd 6:0:0:0: [sdb] tag#2 CDB: Read(10) 28 00 00 7b 70 84 00 00 02 00
[  251.486295] print_req_error: critical target error, dev sdb, sector 8089732
[  251.486298] Buffer I/O error on dev sdb, logical block 4044866, async page read
[  251.486379] sd 6:0:0:0: [sdb] tag#3 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  251.486382] sd 6:0:0:0: [sdb] tag#3 Sense Key : Illegal Request [current] 
[  251.486385] sd 6:0:0:0: [sdb] tag#3 Add. Sense: Invalid field in cdb
[  251.486389] sd 6:0:0:0: [sdb] tag#3 CDB: Read(10) 28 00 00 7b 70 86 00 00 02 00
[  251.486391] print_req_error: critical target error, dev sdb, sector 8089734
[  251.486394] Buffer I/O error on dev sdb, logical block 4044867, async page read
[  251.502881] sd 6:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  251.502885] sd 6:0:0:0: [sdb] tag#0 Sense Key : Illegal Request [current] 
[  251.502887] sd 6:0:0:0: [sdb] tag#0 Add. Sense: Invalid field in cdb
[  251.502891] sd 6:0:0:0: [sdb] tag#0 CDB: Read(10) 28 00 00 7b 70 80 00 00 08 00
[  251.502893] print_req_error: critical target error, dev sdb, sector 8089728
[  251.503375] sd 6:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  251.503377] sd 6:0:0:0: [sdb] tag#0 Sense Key : Illegal Request [current] 
[  251.503380] sd 6:0:0:0: [sdb] tag#0 Add. Sense: Invalid field in cdb
[  251.503382] sd 6:0:0:0: [sdb] tag#0 CDB: Read(10) 28 00 00 7b 70 80 00 00 02 00
[  251.503383] print_req_error: critical target error, dev sdb, sector 8089728
[  251.503387] Buffer I/O error on dev sdb, logical block 4044864, async page read
[  251.503395] sd 6:0:0:0: [sdb] tag#1 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  251.503397] sd 6:0:0:0: [sdb] tag#1 Sense Key : Illegal Request [current] 
[  251.503400] sd 6:0:0:0: [sdb] tag#1 Add. Sense: Invalid field in cdb
[  251.503402] sd 6:0:0:0: [sdb] tag#1 CDB: Read(10) 28 00 00 7b 70 82 00 00 02 00
[  251.503403] print_req_error: critical target error, dev sdb, sector 8089730
[  251.503405] Buffer I/O error on dev sdb, logical block 4044865, async page read
[  251.503570] sd 6:0:0:0: [sdb] tag#2 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  251.503573] sd 6:0:0:0: [sdb] tag#2 Sense Key : Illegal Request [current] 
[  251.503575] sd 6:0:0:0: [sdb] tag#2 Add. Sense: Invalid field in cdb
[  251.503578] sd 6:0:0:0: [sdb] tag#2 CDB: Read(10) 28 00 00 7b 70 84 00 00 02 00
[  251.503579] print_req_error: critical target error, dev sdb, sector 8089732
[  251.503582] Buffer I/O error on dev sdb, logical block 4044866, async page read
[  251.503592] sd 6:0:0:0: [sdb] tag#3 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  251.503594] sd 6:0:0:0: [sdb] tag#3 Sense Key : Illegal Request [current] 
[  251.503597] sd 6:0:0:0: [sdb] tag#3 Add. Sense: Invalid field in cdb
[  251.503600] sd 6:0:0:0: [sdb] tag#3 CDB: Read(10) 28 00 00 7b 70 86 00 00 02 00
[  251.503601] print_req_error: critical target error, dev sdb, sector 8089734
[  251.503604] Buffer I/O error on dev sdb, logical block 4044867, async page read
[  251.507255] Buffer I/O error on dev sdb, logical block 4044864, async page read
[  251.507269] Buffer I/O error on dev sdb, logical block 4044865, async page read
[ 2420.584000] sd 6:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2420.584006] sd 6:0:0:0: [sdb] tag#0 Sense Key : Illegal Request [current] 
[ 2420.584010] sd 6:0:0:0: [sdb] tag#0 Add. Sense: Invalid field in cdb
[ 2420.584014] sd 6:0:0:0: [sdb] tag#0 CDB: Read(10) 28 00 00 00 00 00 00 00 02 00
[ 2420.584018] print_req_error: critical target error, dev sdb, sector 0
[ 2420.584026] Buffer I/O error on dev sdb, logical block 0, async page read
[ 2420.584042] sd 6:0:0:0: [sdb] tag#1 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2420.584046] sd 6:0:0:0: [sdb] tag#1 Sense Key : Illegal Request [current] 
[ 2420.584049] sd 6:0:0:0: [sdb] tag#1 Add. Sense: Invalid field in cdb
[ 2420.584052] sd 6:0:0:0: [sdb] tag#1 CDB: Read(10) 28 00 00 00 00 02 00 00 02 00
[ 2420.584055] print_req_error: critical target error, dev sdb, sector 2
[ 2420.584059] Buffer I/O error on dev sdb, logical block 1, async page read
[ 2420.584113] sd 6:0:0:0: [sdb] tag#2 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2420.584116] sd 6:0:0:0: [sdb] tag#2 Sense Key : Illegal Request [current] 
[ 2420.584119] sd 6:0:0:0: [sdb] tag#2 Add. Sense: Invalid field in cdb
[ 2420.584121] sd 6:0:0:0: [sdb] tag#2 CDB: Read(10) 28 00 00 00 00 04 00 00 02 00
[ 2420.584123] print_req_error: critical target error, dev sdb, sector 4
[ 2420.584126] Buffer I/O error on dev sdb, logical block 2, async page read
[ 2420.584236] sd 6:0:0:0: [sdb] tag#3 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2420.584239] sd 6:0:0:0: [sdb] tag#3 Sense Key : Illegal Request [current] 
[ 2420.584241] sd 6:0:0:0: [sdb] tag#3 Add. Sense: Invalid field in cdb
[ 2420.584244] sd 6:0:0:0: [sdb] tag#3 CDB: Read(10) 28 00 00 00 00 06 00 00 02 00
[ 2420.584245] print_req_error: critical target error, dev sdb, sector 6
[ 2420.584248] Buffer I/O error on dev sdb, logical block 3, async page read
[ 2464.855392] sd 6:0:0:0: [sdb] tag#3 uas_eh_abort_handler 0 uas-tag 4 inflight: CMD 
[ 2464.855398] sd 6:0:0:0: [sdb] tag#3 CDB: Read(10) 28 00 00 00 00 06 00 00 02 00
[ 2464.855404] sd 6:0:0:0: [sdb] tag#2 uas_eh_abort_handler 0 uas-tag 3 inflight: CMD 
[ 2464.855407] sd 6:0:0:0: [sdb] tag#2 CDB: Read(10) 28 00 00 00 00 04 00 00 02 00
[ 2464.855411] sd 6:0:0:0: [sdb] tag#1 uas_eh_abort_handler 0 uas-tag 2 inflight: CMD 
[ 2464.855414] sd 6:0:0:0: [sdb] tag#1 CDB: Read(10) 28 00 00 00 00 02 00 00 02 00
[ 2464.855418] sd 6:0:0:0: [sdb] tag#0 uas_eh_abort_handler 0 uas-tag 1 inflight: CMD 
[ 2464.855421] sd 6:0:0:0: [sdb] tag#0 CDB: Read(10) 28 00 00 00 00 00 00 00 02 00
[ 2465.156634] sd 6:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2465.156659] sd 6:0:0:0: [sdb] tag#0 Sense Key : Illegal Request [current] 
[ 2465.156668] sd 6:0:0:0: [sdb] tag#0 Add. Sense: Invalid field in cdb
[ 2465.156676] sd 6:0:0:0: [sdb] tag#0 CDB: Read(10) 28 00 00 00 00 06 00 00 02 00
[ 2465.156682] print_req_error: critical target error, dev sdb, sector 6
[ 2465.156698] Buffer I/O error on dev sdb, logical block 3, async page read
[ 2465.156738] sd 6:0:0:0: [sdb] tag#1 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2465.156745] sd 6:0:0:0: [sdb] tag#1 Sense Key : Illegal Request [current] 
[ 2465.156751] sd 6:0:0:0: [sdb] tag#1 Add. Sense: Invalid field in cdb
[ 2465.156758] sd 6:0:0:0: [sdb] tag#1 CDB: Read(10) 28 00 00 00 00 04 00 00 02 00
[ 2465.156763] print_req_error: critical target error, dev sdb, sector 4
[ 2465.156769] Buffer I/O error on dev sdb, logical block 2, async page read
[ 2465.156883] sd 6:0:0:0: [sdb] tag#2 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2465.156887] sd 6:0:0:0: [sdb] tag#2 Sense Key : Illegal Request [current] 
[ 2465.156892] sd 6:0:0:0: [sdb] tag#2 Add. Sense: Invalid field in cdb
[ 2465.156896] sd 6:0:0:0: [sdb] tag#2 CDB: Read(10) 28 00 00 00 00 02 00 00 02 00
[ 2465.156899] print_req_error: critical target error, dev sdb, sector 2
[ 2465.156904] Buffer I/O error on dev sdb, logical block 1, async page read
[ 2465.156918] sd 6:0:0:0: [sdb] tag#3 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2465.156923] sd 6:0:0:0: [sdb] tag#3 Sense Key : Illegal Request [current] 
[ 2465.156927] sd 6:0:0:0: [sdb] tag#3 Add. Sense: Invalid field in cdb
[ 2465.156931] sd 6:0:0:0: [sdb] tag#3 CDB: Read(10) 28 00 00 00 00 00 00 00 02 00
[ 2465.156934] print_req_error: critical target error, dev sdb, sector 0
[ 2465.156938] Buffer I/O error on dev sdb, logical block 0, async page read
[ 2465.157498] sd 6:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2465.157502] sd 6:0:0:0: [sdb] tag#0 Sense Key : Illegal Request [current] 
[ 2465.157507] sd 6:0:0:0: [sdb] tag#0 Add. Sense: Invalid field in cdb
[ 2465.157512] sd 6:0:0:0: [sdb] tag#0 CDB: Read(10) 28 00 00 00 00 00 00 00 02 00
[ 2465.157514] print_req_error: critical target error, dev sdb, sector 0
[ 2465.157520] Buffer I/O error on dev sdb, logical block 0, async page read
[ 2465.157538] sd 6:0:0:0: [sdb] tag#1 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2465.157542] sd 6:0:0:0: [sdb] tag#1 Sense Key : Illegal Request [current] 
[ 2465.157546] sd 6:0:0:0: [sdb] tag#1 Add. Sense: Invalid field in cdb
[ 2465.157550] sd 6:0:0:0: [sdb] tag#1 CDB: Read(10) 28 00 00 00 00 02 00 00 02 00
[ 2465.157553] print_req_error: critical target error, dev sdb, sector 2
[ 2465.157557] Buffer I/O error on dev sdb, logical block 1, async page read
[ 2465.157628] sd 6:0:0:0: [sdb] tag#2 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2465.157633] sd 6:0:0:0: [sdb] tag#2 Sense Key : Illegal Request [current] 
[ 2465.157637] sd 6:0:0:0: [sdb] tag#2 Add. Sense: Invalid field in cdb
[ 2465.157642] sd 6:0:0:0: [sdb] tag#2 CDB: Read(10) 28 00 00 00 00 04 00 00 02 00
[ 2465.157644] print_req_error: critical target error, dev sdb, sector 4
[ 2465.157649] Buffer I/O error on dev sdb, logical block 2, async page read
[ 2465.157663] sd 6:0:0:0: [sdb] tag#3 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2465.157667] sd 6:0:0:0: [sdb] tag#3 Sense Key : Illegal Request [current] 
[ 2465.157672] sd 6:0:0:0: [sdb] tag#3 Add. Sense: Invalid field in cdb
[ 2465.157676] sd 6:0:0:0: [sdb] tag#3 CDB: Read(10) 28 00 00 00 00 06 00 00 02 00
[ 2465.157678] print_req_error: critical target error, dev sdb, sector 6
[ 2465.157682] Buffer I/O error on dev sdb, logical block 3, async page read
[ 2465.158252] sd 6:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2465.158256] sd 6:0:0:0: [sdb] tag#0 Sense Key : Illegal Request [current] 
[ 2465.158261] sd 6:0:0:0: [sdb] tag#0 Add. Sense: Invalid field in cdb
[ 2465.158265] sd 6:0:0:0: [sdb] tag#0 CDB: Read(10) 28 00 00 00 00 00 00 00 02 00
[ 2465.158267] print_req_error: critical target error, dev sdb, sector 0
[ 2465.158273] Buffer I/O error on dev sdb, logical block 0, async page read
[ 2465.158291] sd 6:0:0:0: [sdb] tag#1 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2465.158296] sd 6:0:0:0: [sdb] tag#1 Sense Key : Illegal Request [current] 
[ 2465.158300] sd 6:0:0:0: [sdb] tag#1 Add. Sense: Invalid field in cdb
[ 2465.158304] sd 6:0:0:0: [sdb] tag#1 CDB: Read(10) 28 00 00 00 00 02 00 00 02 00
[ 2465.158306] print_req_error: critical target error, dev sdb, sector 2
[ 2465.158311] Buffer I/O error on dev sdb, logical block 1, async page read
[ 2465.161050] Dev sdb: unable to read RDB block 0
[ 2465.164744]  sdb: unable to read partition table
[ 2465.261107] sd 6:0:0:0: [sdb] tag#0 response iu 10 uas-tag 1 inflight: 
[ 2465.261112] sd 6:0:0:0: [sdb] tag#0 CDB: ATA command pass through(16) 85 08 2e 00 00 00 01 00 00 00 00 00 00 00 ec 00
[ 4511.975186] sd 6:0:0:0: [sdb] tag#0 response iu 10 uas-tag 1 inflight: 
[ 4511.975195] sd 6:0:0:0: [sdb] tag#0 CDB: Read(10) 28 00 00 00 00 00 00 00 02 00
[ 4517.762555] sd 6:0:0:0: [sdb] tag#1 uas_zap_pending 0 uas-tag 2 inflight: CMD 
[ 4517.762562] sd 6:0:0:0: [sdb] tag#1 CDB: Read(10) 28 00 00 00 00 02 00 00 02 00
[ 4517.762570] sd 6:0:0:0: [sdb] tag#2 uas_zap_pending 0 uas-tag 3 inflight: CMD 
[ 4517.762574] sd 6:0:0:0: [sdb] tag#2 CDB: Read(10) 28 00 00 00 00 04 00 00 02 00
[ 4517.762579] sd 6:0:0:0: [sdb] tag#3 uas_zap_pending 0 uas-tag 4 inflight: CMD 
[ 4517.762583] sd 6:0:0:0: [sdb] tag#3 CDB: Read(10) 28 00 00 00 00 06 00 00 02 00
[ 4517.762637] sd 6:0:0:0: [sdb] tag#1 FAILED Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 4517.762641] sd 6:0:0:0: [sdb] tag#1 CDB: Read(10) 28 00 00 00 00 02 00 00 02 00
[ 4517.762645] print_req_error: I/O error, dev sdb, sector 2
[ 4517.762654] Buffer I/O error on dev sdb, logical block 1, async page read
[ 4517.762683] sd 6:0:0:0: [sdb] tag#2 FAILED Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 4517.762687] sd 6:0:0:0: [sdb] tag#2 CDB: Read(10) 28 00 00 00 00 04 00 00 02 00
[ 4517.762689] print_req_error: I/O error, dev sdb, sector 4
[ 4517.762692] Buffer I/O error on dev sdb, logical block 2, async page read
[ 4517.762704] sd 6:0:0:0: [sdb] tag#3 FAILED Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 4517.762708] sd 6:0:0:0: [sdb] tag#3 CDB: Read(10) 28 00 00 00 00 06 00 00 02 00
[ 4517.762710] print_req_error: I/O error, dev sdb, sector 6
[ 4517.762713] Buffer I/O error on dev sdb, logical block 3, async page read
[ 4517.781658] sd 6:0:0:0: [sdb] Synchronizing SCSI cache
[ 4517.821443] sd 6:0:0:0: [sdb] tag#1 FAILED Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 4517.821451] sd 6:0:0:0: [sdb] tag#1 CDB: Read(10) 28 00 00 00 00 00 00 00 02 00
[ 4517.821453] print_req_error: I/O error, dev sdb, sector 0
[ 4517.821461] Buffer I/O error on dev sdb, logical block 0, async page read
[ 4518.001442] sd 6:0:0:0: [sdb] Synchronize Cache(10) failed: Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 4537.019747] Buffer I/O error on dev sdb, logical block 4044864, async page read
[ 4537.019756] Buffer I/O error on dev sdb, logical block 4044865, async page read
[ 4537.019761] Buffer I/O error on dev sdb, logical block 4044866, async page read
[ 4537.019765] Buffer I/O error on dev sdb, logical block 4044867, async page read
[ 4537.020029] Buffer I/O error on dev sdb, logical block 4044864, async page read
[ 4537.020034] Buffer I/O error on dev sdb, logical block 4044865, async page read
[ 4537.020038] Buffer I/O error on dev sdb, logical block 4044866, async page read
[ 4537.020042] Buffer I/O error on dev sdb, logical block 4044867, async page read
[ 4537.020101] Buffer I/O error on dev sdb, logical block 4044964, async page read
[ 4537.020105] Buffer I/O error on dev sdb, logical block 4044965, async page read
[ 4548.513342] sd 7:0:0:0: [sdb] 8089950 512-byte logical blocks: (4.14 GB/3.86 GiB)
[ 4548.513704] sd 7:0:0:0: [sdb] Write Protect is off
[ 4548.513708] sd 7:0:0:0: [sdb] Mode Sense: 43 00 00 00
[ 4548.514456] sd 7:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 4548.519203] sd 7:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4548.519221] sd 7:0:0:0: [sdb] tag#0 Sense Key : Illegal Request [current] 
[ 4548.519230] sd 7:0:0:0: [sdb] tag#0 Add. Sense: Invalid field in cdb
[ 4548.519238] sd 7:0:0:0: [sdb] tag#0 CDB: Read(10) 28 00 00 00 00 00 00 00 02 00
[ 4548.519247] print_req_error: critical target error, dev sdb, sector 0
[ 4548.519264] Buffer I/O error on dev sdb, logical block 0, async page read
[ 4548.519282] sd 7:0:0:0: [sdb] tag#1 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4548.519289] sd 7:0:0:0: [sdb] tag#1 Sense Key : Illegal Request [current] 
[ 4548.519296] sd 7:0:0:0: [sdb] tag#1 Add. Sense: Invalid field in cdb
[ 4548.519311] sd 7:0:0:0: [sdb] tag#1 CDB: Read(10) 28 00 00 00 00 02 00 00 02 00
[ 4548.519316] print_req_error: critical target error, dev sdb, sector 2
[ 4548.519324] Buffer I/O error on dev sdb, logical block 1, async page read
[ 4548.519489] sd 7:0:0:0: [sdb] tag#2 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4548.519494] sd 7:0:0:0: [sdb] tag#2 Sense Key : Illegal Request [current] 
[ 4548.519498] sd 7:0:0:0: [sdb] tag#2 Add. Sense: Invalid field in cdb
[ 4548.519503] sd 7:0:0:0: [sdb] tag#2 CDB: Read(10) 28 00 00 00 00 04 00 00 02 00
[ 4548.519505] print_req_error: critical target error, dev sdb, sector 4
[ 4548.519510] Buffer I/O error on dev sdb, logical block 2, async page read
[ 4548.519521] sd 7:0:0:0: [sdb] tag#3 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4548.519525] sd 7:0:0:0: [sdb] tag#3 Sense Key : Illegal Request [current] 
[ 4548.519530] sd 7:0:0:0: [sdb] tag#3 Add. Sense: Invalid field in cdb
[ 4548.519534] sd 7:0:0:0: [sdb] tag#3 CDB: Read(10) 28 00 00 00 00 06 00 00 02 00
[ 4548.519537] print_req_error: critical target error, dev sdb, sector 6
[ 4548.519541] Buffer I/O error on dev sdb, logical block 3, async page read
[ 4548.520067] sd 7:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4548.520070] sd 7:0:0:0: [sdb] tag#0 Sense Key : Illegal Request [current] 
[ 4548.520073] sd 7:0:0:0: [sdb] tag#0 Add. Sense: Invalid field in cdb
[ 4548.520076] sd 7:0:0:0: [sdb] tag#0 CDB: Read(10) 28 00 00 00 00 00 00 00 02 00
[ 4548.520078] print_req_error: critical target error, dev sdb, sector 0
[ 4548.520082] Buffer I/O error on dev sdb, logical block 0, async page read
[ 4548.520091] sd 7:0:0:0: [sdb] tag#1 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4548.520093] sd 7:0:0:0: [sdb] tag#1 Sense Key : Illegal Request [current] 
[ 4548.520096] sd 7:0:0:0: [sdb] tag#1 Add. Sense: Invalid field in cdb
[ 4548.520098] sd 7:0:0:0: [sdb] tag#1 CDB: Read(10) 28 00 00 00 00 02 00 00 02 00
[ 4548.520100] print_req_error: critical target error, dev sdb, sector 2
[ 4548.520103] Buffer I/O error on dev sdb, logical block 1, async page read
[ 4548.520188] sd 7:0:0:0: [sdb] tag#2 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4548.520190] sd 7:0:0:0: [sdb] tag#2 Sense Key : Illegal Request [current] 
[ 4548.520193] sd 7:0:0:0: [sdb] tag#2 Add. Sense: Invalid field in cdb
[ 4548.520195] sd 7:0:0:0: [sdb] tag#2 CDB: Read(10) 28 00 00 00 00 04 00 00 02 00
[ 4548.520196] print_req_error: critical target error, dev sdb, sector 4
[ 4548.520201] Buffer I/O error on dev sdb, logical block 2, async page read
[ 4548.520209] sd 7:0:0:0: [sdb] tag#3 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4548.520211] sd 7:0:0:0: [sdb] tag#3 Sense Key : Illegal Request [current] 
[ 4548.520213] sd 7:0:0:0: [sdb] tag#3 Add. Sense: Invalid field in cdb
[ 4548.520216] sd 7:0:0:0: [sdb] tag#3 CDB: Read(10) 28 00 00 00 00 06 00 00 02 00
[ 4548.520217] print_req_error: critical target error, dev sdb, sector 6
[ 4548.520220] Buffer I/O error on dev sdb, logical block 3, async page read
[ 4548.520690] sd 7:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4548.520694] sd 7:0:0:0: [sdb] tag#0 Sense Key : Illegal Request [current] 
[ 4548.520696] sd 7:0:0:0: [sdb] tag#0 Add. Sense: Invalid field in cdb
[ 4548.520699] sd 7:0:0:0: [sdb] tag#0 CDB: Read(10) 28 00 00 00 00 00 00 00 02 00
[ 4548.520701] print_req_error: critical target error, dev sdb, sector 0
[ 4548.520704] Buffer I/O error on dev sdb, logical block 0, async page read
[ 4548.520713] sd 7:0:0:0: [sdb] tag#1 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4548.520716] sd 7:0:0:0: [sdb] tag#1 Sense Key : Illegal Request [current] 
[ 4548.520719] sd 7:0:0:0: [sdb] tag#1 Add. Sense: Invalid field in cdb
[ 4548.520723] sd 7:0:0:0: [sdb] tag#1 CDB: Read(10) 28 00 00 00 00 02 00 00 02 00
[ 4548.520725] print_req_error: critical target error, dev sdb, sector 2
[ 4548.520727] Buffer I/O error on dev sdb, logical block 1, async page read
[ 4548.527688] Dev sdb: unable to read RDB block 0
[ 4548.530818]  sdb: unable to read partition table
[ 4548.534194] sd 7:0:0:0: [sdb] Attached SCSI disk
[ 4552.063209] sd 7:0:0:0: [sdb] Synchronizing SCSI cache
[ 4552.310920] sd 7:0:0:0: [sdb] Synchronize Cache(10) failed: Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
```

---

### Post by oldfred on 2017-11-29
Post this:
sudo parted -l
sudo gdisk -l /dev/sdb  #if 3TB drive is sdb

Is drive internal or external.
Some older USB drive caddies do not work with gpt or larger drives.

You should only have gpt, not MBR with any drive over 2TiB.

 MBR tech details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table) 

        GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by johnluk on 2017-11-29
I am a new user of ubuntu, not so family about the MBR. 
This 3TB hard disk not for bootup, 
Only for stored some data. So am I need the MBR?

"sudo parted -l" only find my sda, not find the sdb, no display.

sudo gdisk -l /dev/sdb
GPT fdisk (gdisk) version 1.0.1

Problem opening /dev/sdb for reading! Error is 2.
The specified file does not exist!

The drive is 3.5" internal and using the usb put in. And used it on ubuntu 17.4 is good.
So you mean that, I need the GPT, not the MBR. And how to rebuild the GPT?

Thanks!

sudo parted -l         
Model: ATA FSX-120GB (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  120GB  120GB  primary  ext4         boot


Error: /dev/sdb: unrecognised disk label
Model: ST3000DM 001 (scsi)                                                
Disk /dev/sdb: 4142MB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags:

---

### Post by oldfred on 2017-11-29
Did you just format drive, not partition it and then format partitions?

Both MBR and gpt are where partition table info is stored. Size, how many, and formats.
But MBR was designed 35 or so years ago and then KB was large, MB unheard of, so they designed it with a max of 2TiB which was more than super computers of the day.

Do you have data on this drive, or can we just start over?

Often if random data in location where partition table info is, then all partition & system tools fail as the random data does not look like a partition table.

So we may be able to erase location for partition table.

You could use dd, but I hesitate to use dd as its nickname is Data Destroyer. It is easy to do a typo and then you totally destroy data.

While this tools is for creating & then recovering a flash drive installer, it uses dd under the hood, but adds some protection. You can try this on your drive.:
[https://help.ubuntu.com/community/mkusb#Re-use_the_pendrive](https://help.ubuntu.com/community/mkusb#Re-use_the_pendrive)

---

### Post by johnluk on 2017-11-29
I did not format drive, few day ago. The drive just disappear for no reason. And I have many files on this drive be keeping. You teach me so much.

I just input below:
sudo gdisk /dev/sdb
GPT fdisk (gdisk) version 1.0.1

Warning! Read error 5; strange behavior now likely!
Warning! Read error 5; strange behavior now likely!
Partition table scan:
  MBR: not present
  BSD: not present
  APM: not present
  GPT: not present

Creating new GPT entries.

Command (? for help): GPT      
b    back up GPT data to a file
c    change a partition's name
d    delete a partition
i    show detailed information on a partition
l    list known partition types
n    add a new partition
o    create a new empty GUID partition table (GPT)
p    print the partition table
q    quit without saving changes
r    recovery and transformation options (experts only)
s    sort partitions
t    change a partition's type code
v    verify disk
w    write table to disk and exit
x    extra functionality (experts only)
?    print this menu

Command (? for help):

---

### Post by johnluk on 2017-11-29
When I use gparted , it always show me the "Input/output error during read on /dev/sdb" box

---

### Post by oldfred on 2017-11-29
If drive has data, we need to check if drive has major issues.

In Disks (gnome-disks) and icon in upper right corner is Smart Status.
That can run many tests, but all I know if good/bad which it will tell you. Is drive shown as good?

Gdisk is not seeing anything in the way of partitions.
I still think you may have just formatted drive, not partitioned drive.

Do you know what format drive was? NTFS, FAT32, ext4, or something else?

---

### Post by johnluk on 2017-11-29
I find some information about dd rescue. It said Never try to repair a file system on a drive with I/O errors; you will probably lose even more data.
[https://www.gnu.org/software/ddrescue/manual/ddrescue_manual.html](https://www.gnu.org/software/ddrescue/manual/ddrescue_manual.html)
So, I do not make the dd rescue before. I need to fix the I/O errors first.
I do not remember what format of the drive before, just a big 3TB space, no divide it. I guess it maybe NTFS or ext4.

---

### Post by oldfred on 2017-11-29
If you used NTFS, you may do better in a Windows forum.
But it sounds like you formatted drive, then no partition tools will work.
It then looks like a superfloppy drive.
If ext4 this might mount it.

sudo mkdir /media/disk
 sudo mount -t ext4 /dev/sdb /media/disk/ 

Or:
[https://linux.die.net/man/8/mount.ntfs-3g](https://linux.die.net/man/8/mount.ntfs-3g)
sudo mount -t ntfs-3g /dev/sdb /media/disk/ 


Note:
Normally we mount a partition like sdb1, but if you just formatted drive the it will be sdb.

---

### Post by johnluk on 2017-11-30
sudo mkdir /media/disk

sudo mount -t ext4 /dev/sdb /media/disk/ 
mount: /media/disk: wrong fs type, bad option, bad superblock on /dev/sdb, missing codepage or helper program, or other error.

sudo mount -t ntfs-3g /dev/sdb /media/disk/ 
Error reading bootsector: Input/output error
Failed to mount '/dev/sdb': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

---

### Post by johnluk on 2017-11-30
sudo mount -t ext4 /dev/sdb1 /media/disk/ 
mount: /media/disk: special device /dev/sdb1 does not exist.

sudo mount -t ntfs-3g /dev/sdb1 /media/disk/ 
ntfs-3g: Failed to access volume '/dev/sdb1': No such file or directory

---

### Post by oldfred on 2017-11-30
I wanted you to try to mount sdb, not sdb1 as I do not think you have a partition, just a formatted drive.

---

### Post by johnluk on 2017-12-21
I did it at post #10

---

### Post by oldfred on 2017-12-21
In post 10 you used NTFS and post 11 ext4, which is it?

---

### Post by LostFarmer on 2017-12-21
on post #7 'oldfred' asked about - smart-Status', what is the results ?   If it shows failure then it is a hardware problem and that must be fix first if possible.

on post #3 you wrote "The drive is 3.5" internal and using the usb put in."  ?? are you saying the hdd is in a case of some type and connected via the USB port ?
 if so, have you replace the USB cable and tried a different USB port, tried different computer ?

---

