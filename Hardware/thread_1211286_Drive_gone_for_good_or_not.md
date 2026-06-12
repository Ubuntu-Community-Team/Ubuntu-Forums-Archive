---
title: "Drive gone for good or not ?"
date: 2009-07-12
forum: Hardware
---

### Post by xMbx on 2009-07-12
The logs are attached. How would you rate this ? Thanks.

messages.log

```

Jul 12 18:59:28 ubuntu kernel: [ 1076.784105] ata1: EH complete
Jul 12 18:59:28 ubuntu kernel: [ 1080.057765]          res 51/40:08:a0:0c:07/40:04:04:00:00/e4 Emask 0x9 (media error)
Jul 12 18:59:28 ubuntu kernel: [ 1080.109476] ata1.00: configured for UDMA/133
Jul 12 18:59:28 ubuntu kernel: [ 1080.308530] ata1.01: configured for UDMA/100
Jul 12 18:59:28 ubuntu kernel: [ 1080.308541] ata1: EH complete
Jul 12 18:59:28 ubuntu kernel: [ 1083.143029]          res 51/40:08:9f:0c:07/40:04:04:00:00/e4 Emask 0x9 (media error)
Jul 12 18:59:28 ubuntu kernel: [ 1083.204591] ata1.00: configured for UDMA/133
Jul 12 18:59:28 ubuntu kernel: [ 1083.403640] ata1.01: configured for UDMA/100
Jul 12 18:59:28 ubuntu kernel: [ 1083.403651] ata1: EH complete
Jul 12 18:59:28 ubuntu kernel: [ 1086.255481]          res 51/40:08:9f:0c:07/40:04:04:00:00/e4 Emask 0x9 (media error)
Jul 12 18:59:28 ubuntu kernel: [ 1086.309704] ata1.00: configured for UDMA/133
Jul 12 18:59:28 ubuntu kernel: [ 1086.508735] ata1.01: configured for UDMA/100
Jul 12 18:59:28 ubuntu kernel: [ 1086.508745] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Jul 12 18:59:28 ubuntu kernel: [ 1086.508749] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Jul 12 18:59:28 ubuntu kernel: [ 1086.508755] Descriptor sense data with sense descriptors (in hex):
Jul 12 18:59:28 ubuntu kernel: [ 1086.508758]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00
Jul 12 18:59:28 ubuntu kernel: [ 1086.508768]         04 07 0c 9f
Jul 12 18:59:28 ubuntu kernel: [ 1086.508772] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Jul 12 18:59:28 ubuntu kernel: [ 1086.508779] end_request: I/O error, dev sda, sector 67570847
Jul 12 18:59:28 ubuntu kernel: [ 1086.508786] ata1: EH complete
Jul 12 18:59:28 ubuntu kernel: [ 1086.508873] sd 0:0:0:0: [sda] 145226112 512-byte hardware sectors (74356 MB)
Jul 12 18:59:28 ubuntu kernel: [ 1086.508886] sd 0:0:0:0: [sda] Write Protect is off
Jul 12 18:59:28 ubuntu kernel: [ 1086.508910] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 12 18:59:28 ubuntu kernel: [ 1086.508931] sd 0:0:0:0: [sda] 145226112 512-byte hardware sectors (74356 MB)
Jul 12 18:59:28 ubuntu kernel: [ 1086.508943] sd 0:0:0:0: [sda] Write Protect is off
Jul 12 18:59:28 ubuntu kernel: [ 1086.508965] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 12 18:59:39 ubuntu kernel: [ 1097.720832]          res 51/40:00:87:59:16/40:04:04:00:00/e0 Emask 0x9 (media error)
Jul 12 18:59:39 ubuntu kernel: [ 1097.781585] ata1.00: configured for UDMA/133
Jul 12 18:59:39 ubuntu kernel: [ 1097.980613] ata1.01: configured for UDMA/100
Jul 12 18:59:39 ubuntu kernel: [ 1097.980880] ata1: EH complete
Jul 12 18:59:42 ubuntu kernel: [ 1100.866425]          res 51/40:00:87:59:16/40:04:04:00:00/e0 Emask 0x9 (media error)
Jul 12 18:59:42 ubuntu kernel: [ 1100.926617] ata1.00: configured for UDMA/133
Jul 12 18:59:42 ubuntu kernel: [ 1101.125646] ata1.01: configured for UDMA/100
Jul 12 18:59:42 ubuntu kernel: [ 1101.125834] ata1: EH complete
Jul 12 18:59:45 ubuntu kernel: [ 1104.012208]          res 51/40:00:87:59:16/40:04:04:00:00/e0 Emask 0x9 (media error)
Jul 12 18:59:45 ubuntu kernel: [ 1104.071659] ata1.00: configured for UDMA/133
Jul 12 18:59:46 ubuntu kernel: [ 1104.270677] ata1.01: configured for UDMA/100
Jul 12 18:59:46 ubuntu kernel: [ 1104.270865] ata1: EH complete
Jul 12 18:59:48 ubuntu kernel: [ 1107.107887]          res 51/40:00:87:59:16/40:04:04:00:00/e0 Emask 0x9 (media error)
Jul 12 18:59:49 ubuntu kernel: [ 1107.166774] ata1.00: configured for UDMA/133
Jul 12 18:59:49 ubuntu kernel: [ 1107.365788] ata1.01: configured for UDMA/100
Jul 12 18:59:49 ubuntu kernel: [ 1107.365980] ata1: EH complete
Jul 12 18:59:52 ubuntu kernel: [ 1110.203568]          res 51/40:00:87:59:16/40:04:04:00:00/e0 Emask 0x9 (media error)
Jul 12 18:59:52 ubuntu kernel: [ 1110.261875] ata1.00: configured for UDMA/133
Jul 12 18:59:52 ubuntu kernel: [ 1110.460899] ata1.01: configured for UDMA/100
Jul 12 18:59:52 ubuntu kernel: [ 1110.461084] ata1: EH complete
Jul 12 18:59:55 ubuntu kernel: [ 1113.299250]          res 51/40:00:87:59:16/40:04:04:00:00/e0 Emask 0x9 (media error)
Jul 12 18:59:55 ubuntu kernel: [ 1113.357000] ata1.00: configured for UDMA/133
Jul 12 18:59:55 ubuntu kernel: [ 1113.556010] ata1.01: configured for UDMA/100
Jul 12 18:59:55 ubuntu kernel: [ 1113.556442] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Jul 12 18:59:55 ubuntu kernel: [ 1113.556448] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Jul 12 18:59:55 ubuntu kernel: [ 1113.556453] Descriptor sense data with sense descriptors (in hex):
Jul 12 18:59:55 ubuntu kernel: [ 1113.556459]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00
Jul 12 18:59:55 ubuntu kernel: [ 1113.556483]         04 16 59 87
Jul 12 18:59:55 ubuntu kernel: [ 1113.556491] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Jul 12 18:59:55 ubuntu kernel: [ 1113.556500] end_request: I/O error, dev sda, sector 68573575
Jul 12 18:59:55 ubuntu kernel: [ 1113.556532] ata1: EH complete
Jul 12 18:59:55 ubuntu kernel: [ 1113.573913] sd 0:0:0:0: [sda] 145226112 512-byte hardware sectors (74356 MB)
Jul 12 18:59:55 ubuntu kernel: [ 1113.580295] sd 0:0:0:0: [sda] Write Protect is off
Jul 12 18:59:55 ubuntu kernel: [ 1113.593570] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 12 18:59:55 ubuntu kernel: [ 1113.593706] sd 0:0:0:0: [sda] 145226112 512-byte hardware sectors (74356 MB)
Jul 12 18:59:55 ubuntu kernel: [ 1113.593718] sd 0:0:0:0: [sda] Write Protect is off
Jul 12 18:59:55 ubuntu kernel: [ 1113.593738] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 12 18:59:58 ubuntu kernel: [ 1116.327796]          res 51/40:08:87:59:16/40:04:04:00:00/e4 Emask 0x9 (media error)
Jul 12 18:59:58 ubuntu kernel: [ 1116.382212] ata1.00: configured for UDMA/133
Jul 12 18:59:58 ubuntu kernel: [ 1116.581235] ata1.01: configured for UDMA/100
Jul 12 18:59:58 ubuntu kernel: [ 1116.581249] ata1: EH complete

```

system.log

```

ul 12 18:53:23 ubuntu kernel: [  722.492322] ata1.00: status: { DRDY ERR }
Jul 12 18:53:23 ubuntu kernel: [  722.492369] ata1.00: error: { UNC }
Jul 12 18:53:23 ubuntu kernel: [  722.544342] ata1.00: configured for UDMA/133
Jul 12 18:53:24 ubuntu kernel: [  722.743367] ata1.01: configured for UDMA/100
Jul 12 18:53:24 ubuntu kernel: [  722.743542] ata1: EH complete
Jul 12 18:53:26 ubuntu kernel: [  725.687697] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jul 12 18:53:26 ubuntu kernel: [  725.687748] ata1.00: BMDMA stat 0x65
Jul 12 18:53:26 ubuntu kernel: [  725.687797] ata1.00: cmd 25/00:00:3f:4e:91/00:04:02:00:00/e0 tag 0 dma 524288 in
Jul 12 18:53:26 ubuntu kernel: [  725.687798]          res 51/40:00:ef:50:91/40:04:02:00:00/e0 Emask 0x9 (media error)
Jul 12 18:53:26 ubuntu kernel: [  725.687858] ata1.00: status: { DRDY ERR }
Jul 12 18:53:26 ubuntu kernel: [  725.687903] ata1.00: error: { UNC }
Jul 12 18:53:27 ubuntu kernel: [  725.739290] ata1.00: configured for UDMA/133
Jul 12 18:53:27 ubuntu kernel: [  725.938318] ata1.01: configured for UDMA/100
Jul 12 18:53:27 ubuntu kernel: [  725.938702] ata1: EH complete
Jul 12 18:53:30 ubuntu kernel: [  728.833309] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jul 12 18:53:30 ubuntu kernel: [  728.833360] ata1.00: BMDMA stat 0x65
Jul 12 18:53:30 ubuntu kernel: [  728.833407] ata1.00: cmd 25/00:00:3f:4e:91/00:04:02:00:00/e0 tag 0 dma 524288 in
Jul 12 18:53:30 ubuntu kernel: [  728.833409]          res 51/40:00:ef:50:91/40:04:02:00:00/e0 Emask 0x9 (media error)
Jul 12 18:53:30 ubuntu kernel: [  728.833468] ata1.00: status: { DRDY ERR }
Jul 12 18:53:30 ubuntu kernel: [  728.833513] ata1.00: error: { UNC }
Jul 12 18:53:30 ubuntu kernel: [  728.894306] ata1.00: configured for UDMA/133
Jul 12 18:53:30 ubuntu kernel: [  729.093335] ata1.01: configured for UDMA/100
Jul 12 18:53:30 ubuntu kernel: [  729.093567] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Jul 12 18:53:30 ubuntu kernel: [  729.093573] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Jul 12 18:53:30 ubuntu kernel: [  729.093578] Descriptor sense data with sense descriptors (in hex):
Jul 12 18:53:30 ubuntu kernel: [  729.093579]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00
Jul 12 18:53:30 ubuntu kernel: [  729.093593]         02 91 50 ef
Jul 12 18:53:30 ubuntu kernel: [  729.093603] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Jul 12 18:53:30 ubuntu kernel: [  729.093611] end_request: I/O error, dev sda, sector 43077871
Jul 12 18:53:30 ubuntu kernel: [  729.093647] ata1: EH complete
Jul 12 18:53:30 ubuntu kernel: [  729.105160] sd 0:0:0:0: [sda] 145226112 512-byte hardware sectors (74356 MB)
Jul 12 18:53:30 ubuntu kernel: [  729.111306] sd 0:0:0:0: [sda] Write Protect is off
Jul 12 18:53:30 ubuntu kernel: [  729.111320] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jul 12 18:53:30 ubuntu kernel: [  729.120758] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 12 18:53:30 ubuntu kernel: [  729.121011] sd 0:0:0:0: [sda] 145226112 512-byte hardware sectors (74356 MB)
Jul 12 18:53:30 ubuntu kernel: [  729.121022] sd 0:0:0:0: [sda] Write Protect is off
Jul 12 18:53:30 ubuntu kernel: [  729.121026] sd 0:0:0:0: [sda] Mode 

```

---

