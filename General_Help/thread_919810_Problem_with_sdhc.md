---
title: "Problem with sdhc"
date: 2008-09-14
forum: General Help
---

### Post by elect on 2008-09-14
I dont know what happened, but i can "see" my sdhc-icon in "Computer", neither in Gparted

dmegs

279.985638] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 279.985706] end_request: I/O error, dev sdb, sector 0
[ 279.995145] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 279.995219] sd 2:0:0:0: [sdb] Sense Key : Hardware Error [current]
[ 279.995277] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 279.995350] end_request: I/O error, dev sdb, sector 0
[ 279.995493] unable to read partition table
[ 280.148599] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 280.148696] sd 2:0:0:0: [sdb] Sense Key : Hardware Error [current]
[ 280.148759] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 280.148834] end_request: I/O error, dev sdb, sector 0
[ 280.157893] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 280.157967] sd 2:0:0:0: [sdb] Sense Key : Hardware Error [current]
[ 280.158029] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 280.158093] end_request: I/O error, dev sdb, sector 8
[ 280.166022] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 280.166036] sd 2:0:0:0: [sdb] Sense Key : Hardware Error [current]
[ 280.166047] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 280.166058] end_request: I/O error, dev sdb, sector 16
[ 280.173770] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 280.173786] sd 2:0:0:0: [sdb] Sense Key : Hardware Error [current]
[ 280.173797] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 280.173808] end_request: I/O error, dev sdb, sector 0

Ubuntu-eee, sdhc 16GB, eeepc 4G

---

### Post by bornagainpenguin on 2008-09-19
Just a thought, but did you already remove the cd-drive from fstab?

--bornagainpenguin

---

