---
title: "External dvd+/-rw not working properly"
date: 2010-06-27
forum: Hardware
---

### Post by Dopey-Robot on 2010-06-27
I'm having trouble with my external optical drive. Here's the output of DMESG:

```
 00
root@DAW:/home/jesse# dmesg | tail
[  763.316418] sr 5:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  763.316421] sr 5:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  763.316425] sr 5:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00 00 00
[  763.316432] end_request: I/O error, dev sr0, sector 0
[ 1916.218518] sr 5:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1916.218524] sr 5:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 1916.218529] sr 5:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 1916.218535] sr 5:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 10 00 00 01 00 00 00
[ 1916.218543] end_request: I/O error, dev sr0, sector 64
[ 1916.218557] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
root@DAW:/home/jesse# dmesg | tail
[ 2018.773822] sr 5:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 76 e4 00 00 01 00 00 00
[ 2018.773830] end_request: I/O error, dev sr0, sector 1432464
[ 2018.773835] Buffer I/O error on device sr0, logical block 358116
[ 2019.459830] sr 5:0:0:0: [sr0] Unhandled sense code
[ 2019.459836] sr 5:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2019.459840] sr 5:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 2019.459844] sr 5:0:0:0: [sr0] Add. Sense: Unrecovered read error
[ 2019.459848] sr 5:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 76 e4 00 00 01 00 00 00
[ 2019.459857] end_request: I/O error, dev sr0, sector 1432464
[ 2019.459862] Buffer I/O error on device sr0, logical block 35811

```There's no entry in fstab, and no auto mount is happening at all...yet through audacious I can listen to an audio cd. If there's anything else I can post to help I'd be happy to do so.

---

