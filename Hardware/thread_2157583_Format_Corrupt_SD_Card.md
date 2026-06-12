---
title: "Format Corrupt SD Card"
date: 2013-06-25
forum: Hardware
---

### Post by Joon Lee on 2013-06-25
I have a 4GB microSDHC card that I have connected to my computer via a USB adapter. I think it's dead or corrupted or something because while it shows up in "My Computer" on Windows except an error pops up saying, "Please insert a disk in Drive [blah]". On Lubuntu, lsusb lists my USB adapter but Disk Utility says there is no filesystem available. dmesg, however, recognizes a 4GBish capacity but says that it dropped to zero. Here is the result of dmesg:

xxxxx@xxxxx:~$ dmesg | tail -n 20
[  412.507798] sd 6:0:0:0: [sdb]  
[  412.507802] Add. Sense: Medium not present
[  412.507808] sd 6:0:0:0: [sdb] CDB: 
[  412.507810] Read(10): 28 00 00 00 00 80 00 00 08 00
[  412.510027] sd 6:0:0:0: [sdb] Device not ready
[  412.510032] sd 6:0:0:0: [sdb]  
[  412.510036] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  412.510041] sd 6:0:0:0: [sdb]  
[  412.510044] Sense Key : Not Ready [current] 
[  412.510050] sd 6:0:0:0: [sdb]  
[  412.510055] Add. Sense: Medium not present
[  412.510060] sd 6:0:0:0: [sdb] CDB: 
[  412.510063] Read(10): 28 00 00 00 10 00 00 00 08 00
[  412.521984] sdb: detected capacity change from 3965190144 to 0
[  433.383116] sd 6:0:0:0: [sdb] 7744512 512-byte logical blocks: (3.96 GB/3.69 GiB)
[  433.385827] sd 6:0:0:0: [sdb] No Caching mode page present
[  433.385835] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  433.388950] sd 6:0:0:0: [sdb] No Caching mode page present
[  433.388962] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  433.390215]  sdb: sdb1

I don't need to recover any data but it would be nice if I could format this card so I can use it again. Right now, I can't even format this card so somebody please tell me what's going on with my microSD card. Also, if this card is actually dead somebody please tell me that too so I can stop concerning myself with it.

---

### Post by trevm999 on 2013-06-25
I would try it in another adapter, or try another card in that adapter. If the adapter seems fine, I'd say you have a bad card.

---

