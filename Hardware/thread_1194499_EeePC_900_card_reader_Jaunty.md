---
title: "EeePC 900 card reader Jaunty"
date: 2009-06-22
forum: Hardware
---

### Post by markyb86 on 2009-06-22
Is there a fix to get the sd card reader to work in jaunty on the EeePC, or EeePC 900's? Since I have owned the machine it has not worked in any OS except the included and outdated Xandros install.

---

### Post by aim on 2009-09-08
Have the same problem....


```
[  659.223495] sd 2:0:0:0: [sdb] 31388672 512-byte hardware sectors: (16.0 GB/14.9 GiB)
[  659.226497] sd 2:0:0:0: [sdb] Write Protect is off
[  659.226504] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  659.226509] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  659.231489] sd 2:0:0:0: [sdb] 31388672 512-byte hardware sectors: (16.0 GB/14.9 GiB)
[  659.234495] sd 2:0:0:0: [sdb] Write Protect is off
[  659.234502] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  659.234507] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  659.234517]  sdb: sdb1
[  839.330506] sd 2:0:0:0: timing out command, waited 180s
[  839.330525] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  839.330533] sd 2:0:0:0: [sdb] Sense Key : Hardware Error [current] 
[  839.330541] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  839.330551] end_request: I/O error, dev sdb, sector 31388656
[  839.330558] __ratelimit: 27 callbacks suppressed
[  839.330564] Buffer I/O error on device sdb, logical block 3923582

```

---

