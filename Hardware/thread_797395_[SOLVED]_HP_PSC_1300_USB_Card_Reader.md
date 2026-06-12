---
title: "[SOLVED] HP PSC 1300 USB Card Reader"
date: 2008-05-17
forum: Hardware
---

### Post by toni_uk on 2008-05-17
Tried to read my SD memory card using the inbuild card reader on the my HP PSC 1300. When I try to molunt it I get error message saying there is no media on drive. 

Running dmesg I get the following error messages:

> [ 1016.720000] sd 4:0:0:0: [sdb] 60800 512-byte hardware sectors (31 MB)
[ 1016.728000] sd 4:0:0:0: [sdb] Write Protect is off
[ 1016.728000] sd 4:0:0:0: [sdb] Mode Sense: 17 00 00 08
[ 1016.728000] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1016.740000] sd 4:0:0:0: [sdb] 60800 512-byte hardware sectors (31 MB)
[ 1016.748000] sd 4:0:0:0: [sdb] Write Protect is off
[ 1016.748000] sd 4:0:0:0: [sdb] Mode Sense: 17 00 00 08
[ 1016.748000] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1016.748000]  sdb: sdb1
[ 1017.436000] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1017.436000] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 1017.436000] sd 4:0:0:0: [sdb] Add. Sense: Read error - loss of streaming
[ 1017.436000] end_request: I/O error, dev sdb, sector 60796
[ 1017.436000] printk: 3 messages suppressed.
[ 1017.436000] Buffer I/O error on device sdb1, logical block 60745
[ 1017.436000] Buffer I/O error on device sdb1, logical block 60746
[ 1017.436000] Buffer I/O error on device sdb1, logical block 60747
[ 1017.436000] Buffer I/O error on device sdb1, logical block 60748
[ 1018.448000] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1018.448000] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 1018.448000] sd 4:0:0:0: [sdb] Add. Sense: Read error - loss of streaming
[ 1018.448000] end_request: I/O error, dev sdb, sector 60796
[ 1018.448000] Buffer I/O error on device sdb1, logical block 60745
[ 1018.448000] Buffer I/O error on device sdb1, logical block 60746
[ 1018.448000] Buffer I/O error on device sdb1, logical block 60747
[ 1018.448000] Buffer I/O error on device sdb1, logical block 60748
[ 1019.460000] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1019.460000] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 1019.460000] sd 4:0:0:0: [sdb] Add. Sense: Read error - loss of streaming
[ 1019.460000] end_request: I/O error, dev sdb, sector 60796
[ 1019.460000] Buffer I/O error on device sdb1, logical block 60745
[ 1020.476000] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1020.476000] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 1020.476000] sd 4:0:0:0: [sdb] Add. Sense: Read error - loss of streaming
[ 1020.476000] end_request: I/O error, dev sdb, sector 60797
[ 1020.476000] Buffer I/O error on device sdb1, logical block 60746
[ 1021.488000] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1021.488000] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 1021.488000] sd 4:0:0:0: [sdb] Add. Sense: Read error - loss of streaming
[ 1021.488000] end_request: I/O error, dev sdb, sector 60796
[ 1022.504000] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1022.504000] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 1022.504000] sd 4:0:0:0: [sdb] Add. Sense: Read error - loss of streaming
[ 1022.504000] end_request: I/O error, dev sdb, sector 60796
[ 1022.504000] printk: 6 messages suppressed.
[ 1022.504000] Buffer I/O error on device sdb1, logical block 60745
[ 1023.520000] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1023.520000] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 1023.520000] sd 4:0:0:0: [sdb] Add. Sense: Read error - loss of streaming
[ 1023.520000] end_request: I/O error, dev sdb, sector 60797
[ 1023.536000] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1023.536000] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 1023.536000] sd 4:0:0:0: [sdb] Add. Sense: Read error - loss of streaming
[ 1023.536000] end_request: I/O error, dev sdb, sector 60796
[ 1024.548000] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1024.548000] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 1024.548000] sd 4:0:0:0: [sdb] Add. Sense: Read error - loss of streaming
[ 1024.548000] end_request: I/O error, dev sdb, sector 60796
[ 1025.564000] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1025.564000] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 1025.564000] sd 4:0:0:0: [sdb] Add. Sense: Read error - loss of streaming
[ 1025.564000] end_request: I/O error, dev sdb, sector 60797
[ 1026.580000] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1026.584000] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 1026.584000] sd 4:0:0:0: [sdb] Add. Sense: Read error - loss of streaming
[ 1026.584000] end_request: I/O error, dev sdb, sector 60731
[ 1027.596000] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1027.596000] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 1027.596000] sd 4:0:0:0: [sdb] Add. Sense: Read error - loss of streaming
[ 1027.596000] end_request: I/O error, dev sdb, sector 60787
[ 1027.596000] printk: 19 messages suppressed.
[ 1027.596000] Buffer I/O error on device sdb1, logical block 60736
[ 1028.612000] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1028.612000] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 1028.612000] sd 4:0:0:0: [sdb] Add. Sense: Read error - loss of streaming
[ 1028.612000] end_request: I/O error, dev sdb, sector 60788
[ 1029.624000] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1029.624000] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 1029.624000] sd 4:0:0:0: [sdb] Add. Sense: Read error - loss of streaming
[ 1029.624000] end_request: I/O error, dev sdb, sector 60796
[ 1030.640000] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1030.640000] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 1030.640000] sd 4:0:0:0: [sdb] Add. Sense: Read error - loss of streaming
[ 1030.640000] end_request: I/O error, dev sdb, sector 60796
[ 1031.656000] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1031.656000] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 1031.656000] sd 4:0:0:0: [sdb] Add. Sense: Read error - loss of streaming
[ 1031.656000] end_request: I/O error, dev sdb, sector 60797
[ 1031.676000] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1031.676000] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 1031.676000] sd 4:0:0:0: [sdb] Add. Sense: Read error - loss of streaming
[ 1031.676000] end_request: I/O error, dev sdb, sector 91
[ 1032.700000] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1032.700000] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 1032.700000] sd 4:0:0:0: [sdb] Add. Sense: Read error - loss of streaming
[ 1032.700000] end_request: I/O error, dev sdb, sector 60595
[ 1032.700000] printk: 23 messages suppressed.
[ 1032.700000] Buffer I/O error on device sdb1, logical block 60544
[ 1033.716000] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1033.716000] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 1033.716000] sd 4:0:0:0: [sdb] Add. Sense: Read error - loss of streaming
[ 1033.716000] end_request: I/O error, dev sdb, sector 60595
[ 1034.732000] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1034.732000] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 1034.732000] sd 4:0:0:0: [sdb] Add. Sense: Read error - loss of streaming
[ 1034.732000] end_request: I/O error, dev sdb, sector 60596
[ 1035.752000] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1035.752000] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 1035.752000] sd 4:0:0:0: [sdb] Add. Sense: Read error - loss of streaming
[ 1035.752000] end_request: I/O error, dev sdb, sector 60779
[ 1036.764000] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1036.764000] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 1036.764000] sd 4:0:0:0: [sdb] Add. Sense: Read error - loss of streaming
[ 1036.764000] end_request: I/O error, dev sdb, sector 60779
[ 1037.780000] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1037.780000] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 1037.780000] sd 4:0:0:0: [sdb] Add. Sense: Read error - loss of streaming
[ 1037.780000] end_request: I/O error, dev sdb, sector 60780
[ 1037.780000] printk: 24 messages suppressed.
[ 1037.780000] Buffer I/O error on device sdb1, logical block 60729
[ 1038.796000] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1038.796000] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 1038.796000] sd 4:0:0:0: [sdb] Add. Sense: Read error - loss of streaming
[ 1038.796000] end_request: I/O error, dev sdb, sector 51
[ 1039.812000] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1039.812000] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 1039.812000] sd 4:0:0:0: [sdb] Add. Sense: Read error - loss of streaming
[ 1039.812000] end_request: I/O error, dev sdb, sector 51
[ 1040.824000] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1040.824000] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 1040.824000] sd 4:0:0:0: [sdb] Add. Sense: Read error - loss of streaming
[ 1040.824000] end_request: I/O error, dev sdb, sector 52
[ 1040.848000] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1040.848000] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 1040.848000] sd 4:0:0:0: [sdb] Add. Sense: Read error - loss of streaming
[ 1040.848000] end_request: I/O error, dev sdb, sector 51
[ 1041.860000] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1041.860000] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 1041.860000] sd 4:0:0:0: [sdb] Add. Sense: Read error - loss of streaming
[ 1041.860000] end_request: I/O error, dev sdb, sector 60795
[ 1042.872000] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1042.872000] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 1042.872000] sd 4:0:0:0: [sdb] Add. Sense: Read error - loss of streaming
[ 1042.872000] end_request: I/O error, dev sdb, sector 60796
[ 1042.872000] printk: 31 messages suppressed.
[ 1042.872000] Buffer I/O error on device sdb1, logical block 60745
[ 1710.760000] sd 4:0:0:0: [sdb] 60800 512-byte hardware sectors (31 MB)
[ 1710.768000] sd 4:0:0:0: [sdb] Write Protect is off
[ 1710.768000] sd 4:0:0:0: [sdb] Mode Sense: 17 00 00 08
[ 1710.768000] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1710.780000] sd 4:0:0:0: [sdb] 60800 512-byte hardware sectors (31 MB)
[ 1710.788000] sd 4:0:0:0: [sdb] Write Protect is off
[ 1710.788000] sd 4:0:0:0: [sdb] Mode Sense: 17 00 00 08
[ 1710.788000] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1710.788000]  sdb: sdb1
[ 1711.476000] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1711.476000] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 1711.476000] sd 4:0:0:0: [sdb] Add. Sense: Read error - loss of streaming
[ 1711.476000] end_request: I/O error, dev sdb, sector 60796
[ 1711.476000] printk: 3 messages suppressed.
[ 1711.476000] Buffer I/O error on device sdb1, logical block 60745
[ 1711.476000] Buffer I/O error on device sdb1, logical block 60746
[ 1711.476000] Buffer I/O error on device sdb1, logical block 60747
[ 1711.476000] Buffer I/O error on device sdb1, logical block 60748
[ 1711.976000] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1711.976000] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 1711.976000] sd 4:0:0:0: [sdb] Add. Sense: Read error - loss of streaming
[ 1711.976000] end_request: I/O error, dev sdb, sector 60796
[ 1711.976000] Buffer I/O error on device sdb1, logical block 60745
[ 1711.976000] Buffer I/O error on device sdb1, logical block 60746
[ 1711.976000] Buffer I/O error on device sdb1, logical block 60747
[ 1711.976000] Buffer I/O error on device sdb1, logical block 60748
[ 1712.988000] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1712.988000] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 1712.988000] sd 4:0:0:0: [sdb] Add. Sense: Read error - loss of streaming
[ 1712.988000] end_request: I/O error, dev sdb, sector 60796
[ 1712.988000] Buffer I/O error on device sdb1, logical block 60745
[ 1714.004000] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1714.004000] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 1714.004000] sd 4:0:0:0: [sdb] Add. Sense: Read error - loss of streaming
[ 1714.004000] end_request: I/O error, dev sdb, sector 60797
[ 1714.004000] Buffer I/O error on device sdb1, logical block 60746
[ 1715.020000] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1715.020000] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 1715.020000] sd 4:0:0:0: [sdb] Add. Sense: Read error - loss of streaming
[ 1715.020000] end_request: I/O error, dev sdb, sector 60796


Anyone? Help! Cheers!

---

### Post by toni_uk on 2009-01-06
The problem had to do with the autosuspend of my USB ports - solution on post 7 of this thread:

[http://ubuntuforums.org/showthread.php?t=797789](http://ubuntuforums.org/showthread.php?t=797789)

Hope it helps others with the same problem.

---

