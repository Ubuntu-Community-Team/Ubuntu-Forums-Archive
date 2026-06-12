---
title: "Hard Drive Error"
date: 2009-07-13
forum: Hardware
---

### Post by kornyam on 2009-07-13
I'm using a Toshiba Satellite A100 running Jaunty, and this morning I started getting some odd error messages on boot. They appear right after the Ubuntu splash screen and seem to relate to a hard drive issue. However, after displaying, the login screen comes up and there are no apparent problems with anything. Still, I'd like to know what they mean and if it's a sign of approaching doom.

Relevant section of dmseg:
```
[   30.465507] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   30.465515] ata1.00: BMDMA stat 0x24
[   30.465528] ata1.00: cmd 25/00:08:31:aa:18/00:00:14:00:00/e0 tag 0 dma 4096 in
[   30.465531]          res 51/40:05:34:aa:18/40:00:14:00:00/e0 Emask 0x9 (media error)
[   30.465538] ata1.00: status: { DRDY ERR }
[   30.465543] ata1.00: error: { UNC }
[   30.528871] ata1.00: configured for UDMA/100
[   30.528887] ata1: EH complete
[   36.380209] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   36.380215] ata1.00: BMDMA stat 0x24
[   36.380227] ata1.00: cmd 25/00:08:31:aa:18/00:00:14:00:00/e0 tag 0 dma 4096 in
[   36.380229]          res 51/40:05:34:aa:18/40:00:14:00:00/e0 Emask 0x9 (media error)
[   36.380236] ata1.00: status: { DRDY ERR }
[   36.380241] ata1.00: error: { UNC }
[   36.404837] ata1.00: configured for UDMA/100
[   36.404851] ata1: EH complete
[   42.094955] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   42.095030] ata1.00: BMDMA stat 0x24
[   42.095100] ata1.00: cmd 25/00:08:31:aa:18/00:00:14:00:00/e0 tag 0 dma 4096 in
[   42.095103]          res 51/40:05:34:aa:18/40:00:14:00:00/e0 Emask 0x9 (media error)
[   42.095268] ata1.00: status: { DRDY ERR }
[   42.095320] ata1.00: error: { UNC }
[   42.116836] ata1.00: configured for UDMA/100
[   42.116856] ata1: EH complete
[   47.809676] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   47.809746] ata1.00: BMDMA stat 0x24
[   47.809814] ata1.00: cmd 25/00:08:31:aa:18/00:00:14:00:00/e0 tag 0 dma 4096 in
[   47.809817]          res 51/40:05:34:aa:18/40:00:14:00:00/e0 Emask 0x9 (media error)
[   47.809984] ata1.00: status: { DRDY ERR }
[   47.810035] ata1.00: error: { UNC }
[   47.832874] ata1.00: configured for UDMA/100
[   47.832887] ata1: EH complete
[   53.524423] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   53.524494] ata1.00: BMDMA stat 0x24
[   53.524562] ata1.00: cmd 25/00:08:31:aa:18/00:00:14:00:00/e0 tag 0 dma 4096 in
[   53.524565]          res 51/40:05:34:aa:18/40:00:14:00:00/e0 Emask 0x9 (media error)
[   53.524732] ata1.00: status: { DRDY ERR }
[   53.524785] ata1.00: error: { UNC }
[   53.548865] ata1.00: configured for UDMA/100
[   53.548879] ata1: EH complete
[   59.239156] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   59.239225] ata1.00: BMDMA stat 0x24
[   59.239292] ata1.00: cmd 25/00:08:31:aa:18/00:00:14:00:00/e0 tag 0 dma 4096 in
[   59.239295]          res 51/40:05:34:aa:18/40:00:14:00:00/e0 Emask 0x9 (media error)
[   59.239463] ata1.00: status: { DRDY ERR }
[   59.239517] ata1.00: error: { UNC }
[   59.260866] ata1.00: configured for UDMA/100
[   59.260885] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   59.260894] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[   59.260906] Descriptor sense data with sense descriptors (in hex):
[   59.260911]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   59.260937]         14 18 aa 34 
[   59.260947] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[   59.260962] end_request: I/O error, dev sda, sector 337160756
[   59.261056] ata1: EH complete
[   59.286863] sd 0:0:0:0: [sda] 390721968 512-byte hardware sectors: (200 GB/186 GiB)
[   59.286922] sd 0:0:0:0: [sda] Write Protect is off
[   59.286928] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   59.304099] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   59.304180] sd 0:0:0:0: [sda] 390721968 512-byte hardware sectors: (200 GB/186 GiB)
[   59.304218] sd 0:0:0:0: [sda] Write Protect is off
[   59.304224] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   59.304285] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   65.153915] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   65.154004] ata1.00: BMDMA stat 0x24
[   65.154073] ata1.00: cmd 25/00:08:31:aa:18/00:00:14:00:00/e0 tag 0 dma 4096 in
[   65.154076]          res 51/40:05:34:aa:18/40:00:14:00:00/e0 Emask 0x9 (media error)
[   65.154236] ata1.00: status: { DRDY ERR }
[   65.154289] ata1.00: error: { UNC }
[   65.176842] ata1.00: configured for UDMA/100
[   65.176859] ata1: EH complete
[   70.868638] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   70.868708] ata1.00: BMDMA stat 0x24
[   70.868776] ata1.00: cmd 25/00:08:31:aa:18/00:00:14:00:00/e0 tag 0 dma 4096 in
[   70.868780]          res 51/40:05:34:aa:18/40:00:14:00:00/e0 Emask 0x9 (media error)
[   70.868948] ata1.00: status: { DRDY ERR }
[   70.869001] ata1.00: error: { UNC }
[   70.892837] ata1.00: configured for UDMA/100
[   70.892851] ata1: EH complete
[   76.583374] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   76.583442] ata1.00: BMDMA stat 0x24
[   76.583512] ata1.00: cmd 25/00:08:31:aa:18/00:00:14:00:00/e0 tag 0 dma 4096 in
[   76.583515]          res 51/40:05:34:aa:18/40:00:14:00:00/e0 Emask 0x9 (media error)
[   76.583683] ata1.00: status: { DRDY ERR }
[   76.583735] ata1.00: error: { UNC }
[   76.604838] ata1.00: configured for UDMA/100
[   76.604852] ata1: EH complete
[   82.298112] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   82.298182] ata1.00: BMDMA stat 0x24
[   82.298250] ata1.00: cmd 25/00:08:31:aa:18/00:00:14:00:00/e0 tag 0 dma 4096 in
[   82.298253]          res 51/40:05:34:aa:18/40:00:14:00:00/e0 Emask 0x9 (media error)
[   82.298420] ata1.00: status: { DRDY ERR }
[   82.298472] ata1.00: error: { UNC }
[   82.320868] ata1.00: configured for UDMA/100
[   82.320882] ata1: EH complete
[   88.012848] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   88.012917] ata1.00: BMDMA stat 0x24
[   88.012986] ata1.00: cmd 25/00:08:31:aa:18/00:00:14:00:00/e0 tag 0 dma 4096 in
[   88.012989]          res 51/40:05:34:aa:18/40:00:14:00:00/e0 Emask 0x9 (media error)
[   88.013156] ata1.00: status: { DRDY ERR }
[   88.013208] ata1.00: error: { UNC }
[   88.036851] ata1.00: configured for UDMA/100
[   88.036864] ata1: EH complete
[   93.899030] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   93.899099] ata1.00: BMDMA stat 0x24
[   93.899168] ata1.00: cmd 25/00:08:31:aa:18/00:00:14:00:00/e0 tag 0 dma 4096 in
[   93.899171]          res 51/40:05:34:aa:18/40:00:14:00:00/e0 Emask 0x9 (media error)
[   93.899337] ata1.00: status: { DRDY ERR }
[   93.899389] ata1.00: error: { UNC }
[   93.920836] ata1.00: configured for UDMA/100
[   93.920855] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   93.920864] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[   93.920875] Descriptor sense data with sense descriptors (in hex):
[   93.920881]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   93.920907]         14 18 aa 34 
[   93.920917] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[   93.920932] end_request: I/O error, dev sda, sector 337160756
[   93.921023] ata1: EH complete
[   93.921528] sd 0:0:0:0: [sda] 390721968 512-byte hardware sectors: (200 GB/186 GiB)
[   93.921550] sd 0:0:0:0: [sda] Write Protect is off
[   93.921553] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   93.921582] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   93.921615] sd 0:0:0:0: [sda] 390721968 512-byte hardware sectors: (200 GB/186 GiB)
[   93.921632] sd 0:0:0:0: [sda] Write Protect is off
[   93.921634] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   93.921662] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
```

Also, I have a suspicion this may be a problem on my Window's partition, as gparted told me there were bad sectors on it when I resized it a month or so ago. 

Thanks in advance

---

### Post by kornyam on 2009-07-14
Well, I'm pretty sure I was right about the problem being on my Vista partition. It hasn't been bootable since I shrunk it with gparted a month or so ago. I repaired the installation today (which led to me also having to repair GRUB2) and now the error no longer appears on boot.
I'm not really convinced that anything has been fixed, but as long as there aren't any errors coming up I'm just gonna ignore it and keep backing up the hard drive.

---

### Post by Zeedok on 2009-07-16
I've been dealing with some hard drive "bad sector" issues over the last few days as well.

For me, the problems with my drive only came to light after I tried to get rsync going for backup.

On other forums I have been told that finding "bad sectors" on your drive indicates poor drive health and that complete drive failure is a likely outcome, ie GET YOUR DATA SAFE, ASAP.

That's the approach I'm taking anyway.

---

