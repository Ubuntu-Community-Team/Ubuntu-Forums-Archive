---
title: "Is it time to replace this disk?"
date: 2016-06-03
forum: Hardware
---

### Post by Harpz on 2016-06-03
Received an email from my server the other day saying 
```

Device: /dev/sdc [SAT], ATA error count increased from 12682 to 14958

Device info:
WDC WD30EZRX-00DC0B0, S/N:WD-WMC1T2102007, WWN:5-0014ee-0ae2ebd98, FW:80.00A80, 3.00 TB

```

This isn't the first time this has happened, the disk was remounted in read only mode by the server and after a reboot appeared to be operating fine, checked the system log and i have a load of the following:
```

May 31 23:16:07 Altair kernel: [29387.093097] ata3.00: status: { DRDY DF ERR }
May 31 23:16:07 Altair kernel: [29387.095487] ata3.00: error: { ABRT }
May 31 23:16:07 Altair kernel: [29387.098472] ata3.00: failed to enable AA (error_mask=0x1)
May 31 23:16:07 Altair kernel: [29387.101661] ata3.00: failed to enable AA (error_mask=0x1)
May 31 23:16:07 Altair kernel: [29387.103986] ata3.00: configured for UDMA/133 (device error ignored)
May 31 23:16:07 Altair kernel: [29387.104000] ata3: EH complete
May 31 23:16:07 Altair kernel: [29387.109165] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
May 31 23:16:07 Altair kernel: [29387.111552] ata3.00: irq_stat 0x40000001
May 31 23:16:07 Altair kernel: [29387.113935] ata3.00: failed command: WRITE DMA EXT
May 31 23:16:07 Altair kernel: [29387.116293] ata3.00: cmd 35/00:00:00:88:be/00:08:df:00:00/e0 tag 11 dma 1048576 out
May 31 23:16:07 Altair kernel: [29387.116293]          res 61/04:00:00:88:be/00:08:df:00:00/e0 Emask 0x1 (device error)
May 31 23:16:07 Altair kernel: [29387.121116] ata3.00: status: { DRDY DF ERR }
May 31 23:16:07 Altair kernel: [29387.123508] ata3.00: error: { ABRT }
May 31 23:16:08 Altair kernel: [29387.126480] ata3.00: failed to enable AA (error_mask=0x1)
May 31 23:16:08 Altair kernel: [29387.129672] ata3.00: failed to enable AA (error_mask=0x1)
May 31 23:16:08 Altair kernel: [29387.132003] ata3.00: configured for UDMA/133 (device error ignored)
May 31 23:16:08 Altair kernel: [29387.132017] ata3: EH complete
May 31 23:16:08 Altair kernel: [29387.137165] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
May 31 23:16:08 Altair kernel: [29387.139571] ata3.00: irq_stat 0x40000001
May 31 23:16:08 Altair kernel: [29387.141966] ata3.00: failed command: WRITE DMA EXT
May 31 23:16:08 Altair kernel: [29387.144342] ata3.00: cmd 35/00:00:00:88:be/00:08:df:00:00/e0 tag 15 dma 1048576 out
May 31 23:16:08 Altair kernel: [29387.144342]          res 61/04:00:00:88:be/00:08:df:00:00/e0 Emask 0x1 (device error)
May 31 23:16:08 Altair kernel: [29387.149193] ata3.00: status: { DRDY DF ERR }
May 31 23:16:08 Altair kernel: [29387.151603] ata3.00: error: { ABRT }
May 31 23:16:08 Altair kernel: [29387.154594] ata3.00: failed to enable AA (error_mask=0x1)
May 31 23:16:08 Altair kernel: [29387.157762] ata3.00: failed to enable AA (error_mask=0x1)
May 31 23:16:08 Altair kernel: [29387.160079] ata3.00: configured for UDMA/133 (device error ignored)
May 31 23:16:08 Altair kernel: [29387.160092] ata3: EH complete
May 31 23:16:08 Altair kernel: [29387.165104] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
May 31 23:16:08 Altair kernel: [29387.167505] ata3.00: irq_stat 0x40000001
May 31 23:16:08 Altair kernel: [29387.169869] ata3.00: failed command: WRITE DMA EXT
May 31 23:16:08 Altair kernel: [29387.172206] ata3.00: cmd 35/00:00:00:88:be/00:08:df:00:00/e0 tag 19 dma 1048576 out
May 31 23:16:08 Altair kernel: [29387.172206]          res 61/04:00:00:88:be/00:08:df:00:00/e0 Emask 0x1 (device error)
May 31 23:16:08 Altair kernel: [29387.176981] ata3.00: status: { DRDY DF ERR }
May 31 23:16:08 Altair kernel: [29387.179340] ata3.00: error: { ABRT }
May 31 23:16:08 Altair kernel: [29387.182318] ata3.00: failed to enable AA (error_mask=0x1)
May 31 23:16:08 Altair kernel: [29387.185464] ata3.00: failed to enable AA (error_mask=0x1)
May 31 23:16:08 Altair kernel: [29387.187760] ata3.00: configured for UDMA/133 (device error ignored)
May 31 23:16:08 Altair kernel: [29387.187779] sd 2:0:0:0: [sdc] tag#19 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May 31 23:16:08 Altair kernel: [29387.187782] sd 2:0:0:0: [sdc] tag#19 Sense Key : Illegal Request [current] [descriptor] 
May 31 23:16:08 Altair kernel: [29387.187785] sd 2:0:0:0: [sdc] tag#19 Add. Sense: Unaligned write command
May 31 23:16:08 Altair kernel: [29387.187788] sd 2:0:0:0: [sdc] tag#19 CDB: Write(16) 8a 00 00 00 00 00 df be 88 00 00 00 08 00 00 00
May 31 23:16:08 Altair kernel: [29387.187790] blk_update_request: I/O error, dev sdc, sector 3753805824
May 31 23:16:08 Altair kernel: [29387.190145] EXT4-fs warning (device sdc1): ext4_end_bio:329: I/O error -5 writing to inode 177995778 (offset 150994944 size 1347584 starting block 469225984)
May 31 23:16:08 Altair kernel: [29387.190250] ata3: EH complete
May 31 23:16:08 Altair kernel: [29387.197175] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
May 31 23:16:08 Altair kernel: [29387.199564] ata3.00: irq_stat 0x40000001
May 31 23:16:08 Altair kernel: [29387.201947] ata3.00: failed command: WRITE DMA EXT
May 31 23:16:08 Altair kernel: [29387.204307] ata3.00: cmd 35/00:80:00:90:be/00:02:df:00:00/e0 tag 25 dma 327680 out
May 31 23:16:08 Altair kernel: [29387.204307]          res 61/04:80:00:90:be/00:02:df:00:00/e0 Emask 0x1 (device error)
May 31 23:16:08 Altair kernel: [29387.209124] ata3.00: status: { DRDY DF ERR }
May 31 23:16:08 Altair kernel: [29387.211515] ata3.00: error: { ABRT }
May 31 23:16:08 Altair kernel: [29387.214488] ata3.00: failed to enable AA (error_mask=0x1)
May 31 23:16:08 Altair kernel: [29387.217668] ata3.00: failed to enable AA (error_mask=0x1)
May 31 23:16:08 Altair kernel: [29387.219994] ata3.00: configured for UDMA/133 (device error ignored)
May 31 23:16:08 Altair kernel: [29387.220008] ata3: EH complete
May 31 23:16:08 Altair kernel: [29387.225011] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
May 31 23:16:08 Altair kernel: [29387.227411] ata3.00: irq_stat 0x40000001
May 31 23:16:08 Altair kernel: [29387.229797] ata3.00: failed command: WRITE DMA EXT
May 31 23:16:08 Altair kernel: [29387.232168] ata3.00: cmd 35/00:80:00:90:be/00:02:df:00:00/e0 tag 28 dma 327680 out
May 31 23:16:08 Altair kernel: [29387.232168]          res 61/04:80:00:90:be/00:02:df:00:00/e0 Emask 0x1 (device error)
May 31 23:16:08 Altair kernel: [29387.237010] ata3.00: status: { DRDY DF ERR }
May 31 23:16:08 Altair kernel: [29387.239413] ata3.00: error: { ABRT }
May 31 23:16:08 Altair kernel: [29387.242390] ata3.00: failed to enable AA (error_mask=0x1)
May 31 23:16:08 Altair kernel: [29387.245627] ata3.00: failed to enable AA (error_mask=0x1)
May 31 23:16:08 Altair kernel: [29387.247954] ata3.00: configured for UDMA/133 (device error ignored)
May 31 23:16:08 Altair kernel: [29387.247968] ata3: EH complete
May 31 23:16:08 Altair kernel: [29387.253008] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
May 31 23:16:08 Altair kernel: [29387.255390] ata3.00: irq_stat 0x40000001
May 31 23:16:08 Altair kernel: [29387.257761] ata3.00: failed command: WRITE DMA EXT
May 31 23:16:08 Altair kernel: [29387.260116] ata3.00: cmd 35/00:80:00:90:be/00:02:df:00:00/e0 tag 1 dma 327680 out
May 31 23:16:08 Altair kernel: [29387.260116]          res 61/04:80:00:90:be/00:02:df:00:00/e0 Emask 0x1 (device error)
May 31 23:16:08 Altair kernel: [29387.264915] ata3.00: status: { DRDY DF ERR }
May 31 23:16:08 Altair kernel: [29387.267317] ata3.00: error: { ABRT }
May 31 23:16:08 Altair kernel: [29387.270287] ata3.00: failed to enable AA (error_mask=0x1)
May 31 23:16:08 Altair kernel: [29387.273451] ata3.00: failed to enable AA (error_mask=0x1)
May 31 23:16:08 Altair kernel: [29387.275771] ata3.00: configured for UDMA/133 (device error ignored)
May 31 23:16:08 Altair kernel: [29387.275785] ata3: EH complete
May 31 23:16:08 Altair kernel: [29387.281174] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
May 31 23:16:08 Altair kernel: [29387.283748] ata3.00: irq_stat 0x40000001
May 31 23:16:08 Altair kernel: [29387.286338] ata3.00: failed command: WRITE DMA EXT
May 31 23:16:08 Altair kernel: [29387.288874] ata3.00: cmd 35/00:80:00:90:be/00:02:df:00:00/e0 tag 5 dma 327680 out
May 31 23:16:08 Altair kernel: [29387.288874]          res 61/04:80:00:90:be/00:02:df:00:00/e0 Emask 0x1 (device error)
May 31 23:16:08 Altair kernel: [29387.294055] ata3.00: status: { DRDY DF ERR }
May 31 23:16:08 Altair kernel: [29387.296626] ata3.00: error: { ABRT }
May 31 23:16:08 Altair kernel: [29387.299806] ata3.00: failed to enable AA (error_mask=0x1)
May 31 23:16:08 Altair kernel: [29387.303231] ata3.00: failed to enable AA (error_mask=0x1)
May 31 23:16:08 Altair kernel: [29387.305776] ata3.00: configured for UDMA/133 (device error ignored)
May 31 23:16:08 Altair kernel: [29387.305798] ata3: EH complete
May 31 23:16:08 Altair kernel: [29387.313177] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
May 31 23:16:08 Altair kernel: [29387.315568] ata3.00: irq_stat 0x40000001
May 31 23:16:08 Altair kernel: [29387.317941] ata3.00: failed command: WRITE DMA EXT
May 31 23:16:08 Altair kernel: [29387.320287] ata3.00: cmd 35/00:80:00:90:be/00:02:df:00:00/e0 tag 9 dma 327680 out
May 31 23:16:08 Altair kernel: [29387.320287]          res 61/04:80:00:90:be/00:02:df:00:00/e0 Emask 0x1 (device error)
May 31 23:16:08 Altair kernel: [29387.325085] ata3.00: status: { DRDY DF ERR }
May 31 23:16:08 Altair kernel: [29387.327464] ata3.00: error: { ABRT }
May 31 23:16:08 Altair kernel: [29387.330433] ata3.00: failed to enable AA (error_mask=0x1)
May 31 23:16:08 Altair kernel: [29387.333709] ata3.00: failed to enable AA (error_mask=0x1)
May 31 23:16:08 Altair kernel: [29387.336023] ata3.00: configured for UDMA/133 (device error ignored)
May 31 23:16:08 Altair kernel: [29387.336037] ata3: EH complete
May 31 23:16:08 Altair kernel: [29387.341178] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
May 31 23:16:08 Altair kernel: [29387.343574] ata3.00: irq_stat 0x40000001
May 31 23:16:08 Altair kernel: [29387.345932] ata3.00: failed command: WRITE DMA EXT
May 31 23:16:08 Altair kernel: [29387.348254] ata3.00: cmd 35/00:80:00:90:be/00:02:df:00:00/e0 tag 13 dma 327680 out
May 31 23:16:08 Altair kernel: [29387.348254]          res 61/04:80:00:90:be/00:02:df:00:00/e0 Emask 0x1 (device error)
May 31 23:16:08 Altair kernel: [29387.353006] ata3.00: status: { DRDY DF ERR }
May 31 23:16:08 Altair kernel: [29387.355354] ata3.00: error: { ABRT }
May 31 23:16:08 Altair kernel: [29387.358341] ata3.00: failed to enable AA (error_mask=0x1)
May 31 23:16:08 Altair kernel: [29387.361568] ata3.00: failed to enable AA (error_mask=0x1)
May 31 23:16:08 Altair kernel: [29387.363850] ata3.00: configured for UDMA/133 (device error ignored)
May 31 23:16:08 Altair kernel: [29387.363867] sd 2:0:0:0: [sdc] tag#13 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May 31 23:16:08 Altair kernel: [29387.363870] sd 2:0:0:0: [sdc] tag#13 Sense Key : Illegal Request [current] [descriptor] 
May 31 23:16:08 Altair kernel: [29387.363873] sd 2:0:0:0: [sdc] tag#13 Add. Sense: Unaligned write command
May 31 23:16:08 Altair kernel: [29387.363876] sd 2:0:0:0: [sdc] tag#13 CDB: Write(16) 8a 00 00 00 00 00 df be 90 00 00 00 02 80 00 00
May 31 23:16:08 Altair kernel: [29387.363878] blk_update_request: I/O error, dev sdc, sector 3753807872
May 31 23:16:08 Altair kernel: [29387.366213] EXT4-fs warning (device sdc1): ext4_end_bio:329: I/O error -5 writing to inode 177995778 (offset 150994944 size 1347584 starting block 469226057)
May 31 23:16:08 Altair kernel: [29387.366269] EXT4-fs warning (device sdc1): ext4_end_bio:329: I/O error -5 writing to inode 177995778 (offset 152342528 size 28672 starting block 469226064)
May 31 23:16:08 Altair kernel: [29387.366279] ata3: EH complete
May 31 23:16:08 Altair kernel: [29387.373123] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
May 31 23:16:08 Altair kernel: [29387.375515] ata3.00: irq_stat 0x40000001
May 31 23:16:08 Altair kernel: [29387.377895] ata3.00: failed command: WRITE DMA EXT
May 31 23:16:08 Altair kernel: [29387.380245] ata3.00: cmd 35/00:00:80:92:be/00:08:df:00:00/e0 tag 19 dma 1048576 out
May 31 23:16:08 Altair kernel: [29387.380245]          res 61/04:00:80:92:be/00:08:df:00:00/e0 Emask 0x1 (device error)

```
And more:
```

May 31 23:16:08 Altair kernel: [29387.469982] ata3.00: status: { DRDY DF ERR }
May 31 23:16:08 Altair kernel: [29387.472563] ata3.00: error: { ABRT }
May 31 23:16:08 Altair kernel: [29387.475701] ata3.00: failed to enable AA (error_mask=0x1)
May 31 23:16:08 Altair kernel: [29387.478898] ata3.00: failed to enable AA (error_mask=0x1)
May 31 23:16:08 Altair kernel: [29387.481236] ata3.00: configured for UDMA/133 (device error ignored)
May 31 23:16:08 Altair kernel: [29387.481251] ata3: EH complete
May 31 23:16:08 Altair kernel: [29387.489181] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
May 31 23:16:08 Altair kernel: [29387.491594] ata3.00: irq_stat 0x40000001
May 31 23:16:08 Altair kernel: [29387.493984] ata3.00: failed command: WRITE DMA EXT
May 31 23:16:08 Altair kernel: [29387.496355] ata3.00: cmd 35/00:00:80:92:be/00:08:df:00:00/e0 tag 3 dma 1048576 out
May 31 23:16:08 Altair kernel: [29387.496355]          res 61/04:00:80:92:be/00:08:df:00:00/e0 Emask 0x1 (device error)
May 31 23:16:08 Altair kernel: [29387.501189] ata3.00: status: { DRDY DF ERR }
May 31 23:16:08 Altair kernel: [29387.503597] ata3.00: error: { ABRT }
May 31 23:16:08 Altair kernel: [29387.506569] ata3.00: failed to enable AA (error_mask=0x1)
May 31 23:16:08 Altair kernel: [29387.509777] ata3.00: failed to enable AA (error_mask=0x1)
May 31 23:16:08 Altair kernel: [29387.512095] ata3.00: configured for UDMA/133 (device error ignored)
May 31 23:16:08 Altair kernel: [29387.512110] ata3: EH complete
May 31 23:16:08 Altair kernel: [29387.517110] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
May 31 23:16:08 Altair kernel: [29387.519506] ata3.00: irq_stat 0x40000001
May 31 23:16:08 Altair kernel: [29387.521864] ata3.00: failed command: WRITE DMA EXT
May 31 23:16:08 Altair kernel: [29387.524193] ata3.00: cmd 35/00:00:80:92:be/00:08:df:00:00/e0 tag 7 dma 1048576 out
May 31 23:16:08 Altair kernel: [29387.524193]          res 61/04:00:80:92:be/00:08:df:00:00/e0 Emask 0x1 (device error)
May 31 23:16:08 Altair kernel: [29387.528946] ata3.00: status: { DRDY DF ERR }
May 31 23:16:08 Altair kernel: [29387.531332] ata3.00: error: { ABRT }
May 31 23:16:08 Altair kernel: [29387.535013] ata3.00: failed to enable AA (error_mask=0x1)
May 31 23:16:08 Altair kernel: [29387.538164] ata3.00: failed to enable AA (error_mask=0x1)
May 31 23:16:08 Altair kernel: [29387.540455] ata3.00: configured for UDMA/133 (device error ignored)
May 31 23:16:08 Altair kernel: [29387.540476] sd 2:0:0:0: [sdc] tag#7 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May 31 23:16:08 Altair kernel: [29387.540479] sd 2:0:0:0: [sdc] tag#7 Sense Key : Illegal Request [current] [descriptor] 
May 31 23:16:08 Altair kernel: [29387.540481] sd 2:0:0:0: [sdc] tag#7 Add. Sense: Unaligned write command
May 31 23:16:08 Altair kernel: [29387.540484] sd 2:0:0:0: [sdc] tag#7 CDB: Write(16) 8a 00 00 00 00 00 df be 92 80 00 00 08 00 00 00
May 31 23:16:08 Altair kernel: [29387.540486] blk_update_request: I/O error, dev sdc, sector 3753808512
May 31 23:16:08 Altair kernel: [29387.542827] EXT4-fs warning (device sdc1): ext4_end_bio:329: I/O error -5 writing to inode 177995778 (offset 152371200 size 4128768 starting block 469226320)
May 31 23:16:08 Altair kernel: [29387.542935] ata3: EH complete
May 31 23:16:08 Altair kernel: [29387.549168] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
May 31 23:16:08 Altair kernel: [29387.551594] ata3.00: irq_stat 0x40000001
May 31 23:16:08 Altair kernel: [29387.553998] ata3.00: failed command: WRITE DMA EXT
May 31 23:16:08 Altair kernel: [29387.556378] ata3.00: cmd 35/00:00:80:9a:be/00:08:df:00:00/e0 tag 13 dma 1048576 out
May 31 23:16:08 Altair kernel: [29387.556378]          res 61/04:00:80:9a:be/00:08:df:00:00/e0 Emask 0x1 (device error)
May 31 23:16:08 Altair kernel: [29387.561267] ata3.00: status: { DRDY DF ERR }
May 31 23:16:08 Altair kernel: [29387.563847] ata3.00: error: { ABRT }
May 31 23:16:08 Altair kernel: [29387.567027] ata3.00: failed to enable AA (error_mask=0x1)
May 31 23:16:08 Altair kernel: [29387.570458] ata3.00: failed to enable AA (error_mask=0x1)
May 31 23:16:08 Altair kernel: [29387.572862] ata3.00: configured for UDMA/133 (device error ignored)
May 31 23:16:08 Altair kernel: [29387.572882] ata3: EH complete
May 31 23:16:08 Altair kernel: [29387.577100] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
May 31 23:16:08 Altair kernel: [29387.579572] ata3.00: irq_stat 0x40000001
May 31 23:16:08 Altair kernel: [29387.582031] ata3.00: failed command: WRITE DMA EXT
May 31 23:16:08 Altair kernel: [29387.584471] ata3.00: cmd 35/00:00:80:9a:be/00:08:df:00:00/e0 tag 16 dma 1048576 out
May 31 23:16:08 Altair kernel: [29387.584471]          res 61/04:00:80:9a:be/00:08:df:00:00/e0 Emask 0x1 (device error)
May 31 23:16:08 Altair kernel: [29387.589454] ata3.00: status: { DRDY DF ERR }
May 31 23:16:08 Altair kernel: [29387.591928] ata3.00: error: { ABRT }
May 31 23:16:08 Altair kernel: [29387.594987] ata3.00: failed to enable AA (error_mask=0x1)
May 31 23:16:08 Altair kernel: [29387.598272] ata3.00: failed to enable AA (error_mask=0x1)
May 31 23:16:08 Altair kernel: [29387.600680] ata3.00: configured for UDMA/133 (device error ignored)
May 31 23:16:08 Altair kernel: [29387.600698] ata3: EH complete
May 31 23:16:08 Altair kernel: [29387.605102] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
May 31 23:16:08 Altair kernel: [29387.607502] ata3.00: irq_stat 0x40000001
May 31 23:16:08 Altair kernel: [29387.609890] ata3.00: failed command: WRITE DMA EXT
May 31 23:16:08 Altair kernel: [29387.612260] ata3.00: cmd 35/00:00:80:9a:be/00:08:df:00:00/e0 tag 20 dma 1048576 out
May 31 23:16:08 Altair kernel: [29387.612260]          res 61/04:00:80:9a:be/00:08:df:00:00/e0 Emask 0x1 (device error)
May 31 23:16:08 Altair kernel: [29387.617096] ata3.00: status: { DRDY DF ERR }
May 31 23:16:08 Altair kernel: [29387.619498] ata3.00: error: { ABRT }
May 31 23:16:08 Altair kernel: [29387.622463] ata3.00: failed to enable AA (error_mask=0x1)
May 31 23:16:08 Altair kernel: [29387.625639] ata3.00: failed to enable AA (error_mask=0x1)
May 31 23:16:08 Altair kernel: [29387.627947] ata3.00: configured for UDMA/133 (device error ignored)
May 31 23:16:08 Altair kernel: [29387.627959] ata3: EH complete
May 31 23:16:08 Altair kernel: [29387.633098] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
May 31 23:16:08 Altair kernel: [29387.635498] ata3.00: irq_stat 0x40000001
May 31 23:16:08 Altair kernel: [29387.637883] ata3.00: failed command: WRITE DMA EXT
May 31 23:16:08 Altair kernel: [29387.640256] ata3.00: cmd 35/00:00:80:9a:be/00:08:df:00:00/e0 tag 24 dma 1048576 out
May 31 23:16:08 Altair kernel: [29387.640256]          res 61/04:00:80:9a:be/00:08:df:00:00/e0 Emask 0x1 (device error)

```

Smart report for the drive:
```
smartctl 6.5 2016-01-24 r4214 [x86_64-linux-4.4.0-22-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Green
Device Model:     WDC WD30EZRX-00DC0B0
Serial Number:    WD-WMC1T2102007
LU WWN Device Id: 5 0014ee 0ae2ebd98
Firmware Version: 80.00A80
User Capacity:    3,000,592,982,016 bytes [3.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ACS-2 (minor revision not indicated)
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Fri Jun  3 19:57:47 2016 BST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		(40980) seconds.
Offline data collection
capabilities: 			 (0x7b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 ( 411) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.
SCT capabilities: 	       (0x70b5)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   180   178   021    Pre-fail  Always       -       5983
  4 Start_Stop_Count        0x0032   095   095   000    Old_age   Always       -       5303
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   074   074   000    Old_age   Always       -       19117
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       913
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       73
193 Load_Cycle_Count        0x0032   196   196   000    Old_age   Always       -       14489
194 Temperature_Celsius     0x0022   124   107   000    Old_age   Always       -       26
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       1
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

SMART Error Log Version: 1
ATA Error Count: 14970 (device log contains only the most recent five errors)
	CR = Command Register [HEX]
	FR = Features Register [HEX]
	SC = Sector Count Register [HEX]
	SN = Sector Number Register [HEX]
	CL = Cylinder Low Register [HEX]
	CH = Cylinder High Register [HEX]
	DH = Device/Head Register [HEX]
	DC = Device Command Register [HEX]
	ER = Error register [HEX]
	ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

Error 14970 occurred at disk power-on lifetime: 19117 hours (796 days + 13 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 61 00 00 00 00 40

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  94 00 00 00 00 00 40 08      16:29:52.148  STANDBY IMMEDIATE [RET-4]
  e0 00 00 00 00 00 40 08      16:29:52.141  STANDBY IMMEDIATE
  b0 d5 01 09 4f c2 00 08      16:29:52.129  SMART READ LOG
  b0 d5 01 06 4f c2 00 08      16:29:52.129  SMART READ LOG
  b0 d5 01 01 4f c2 00 08      16:29:52.128  SMART READ LOG

Error 14969 occurred at disk power-on lifetime: 19117 hours (796 days + 13 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 61 00 00 00 00 40

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  e0 00 00 00 00 00 40 08      16:29:52.141  STANDBY IMMEDIATE
  b0 d5 01 09 4f c2 00 08      16:29:52.129  SMART READ LOG
  b0 d5 01 06 4f c2 00 08      16:29:52.129  SMART READ LOG
  b0 d5 01 01 4f c2 00 08      16:29:52.128  SMART READ LOG
  b0 d5 01 00 4f c2 00 08      16:29:52.128  SMART READ LOG

Error 14968 occurred at disk power-on lifetime: 19117 hours (796 days + 13 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 61 00 00 00 00 40

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  94 00 00 00 00 00 40 08      16:28:56.282  STANDBY IMMEDIATE [RET-4]
  e0 00 00 00 00 00 40 08      16:28:56.276  STANDBY IMMEDIATE
  b0 d5 01 09 4f c2 00 08      16:28:56.262  SMART READ LOG
  b0 d5 01 06 4f c2 00 08      16:28:56.262  SMART READ LOG
  b0 d5 01 01 4f c2 00 08      16:28:56.261  SMART READ LOG

Error 14967 occurred at disk power-on lifetime: 19117 hours (796 days + 13 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 61 00 00 00 00 40

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  e0 00 00 00 00 00 40 08      16:28:56.276  STANDBY IMMEDIATE
  b0 d5 01 09 4f c2 00 08      16:28:56.262  SMART READ LOG
  b0 d5 01 06 4f c2 00 08      16:28:56.262  SMART READ LOG
  b0 d5 01 01 4f c2 00 08      16:28:56.261  SMART READ LOG
  b0 d5 01 00 4f c2 00 08      16:28:56.261  SMART READ LOG

Error 14966 occurred at disk power-on lifetime: 19116 hours (796 days + 12 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 61 00 00 00 00 40

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  94 00 00 00 00 00 40 08      15:29:55.338  STANDBY IMMEDIATE [RET-4]
  e0 00 00 00 00 00 40 08      15:29:55.327  STANDBY IMMEDIATE
  b0 d5 01 09 4f c2 00 08      15:29:55.315  SMART READ LOG
  b0 d5 01 06 4f c2 00 08      15:29:55.315  SMART READ LOG
  b0 d5 01 01 4f c2 00 08      15:29:55.314  SMART READ LOG

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%     18917         -
# 2  Extended offline    Completed without error       00%     18915         -
# 3  Short offline       Completed without error       00%     18886         -
# 4  Short offline       Completed without error       00%     18879         -
# 5  Short offline       Completed without error       00%     18852         -
# 6  Short offline       Completed without error       00%     18845         -
# 7  Short offline       Completed without error       00%     18824         -
# 8  Extended offline    Completed without error       00%     18807         -
# 9  Short offline       Completed without error       00%     18772         -
#10  Short offline       Completed without error       00%     18760         -
#11  Short offline       Completed without error       00%     18757         -
#12  Extended offline    Completed without error       00%     18735         -
#13  Short offline       Completed without error       00%     18721         -
#14  Short offline       Completed without error       00%     18715         -
#15  Short offline       Completed without error       00%     18711         -
#16  Short offline       Completed without error       00%     18695         -
#17  Extended offline    Completed without error       00%     18673         -
#18  Short offline       Completed without error       00%     18618         -
#19  Short offline       Completed without error       00%     18592         -
#20  Short offline       Completed without error       00%     18570         -
#21  Short offline       Completed without error       00%     18535         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

```

The drive appears to be playing nice at the moment but i would like to know if its time to replace it, is it worth running long and short tests on the drive and are there any other tests i should run?

---

### Post by TheFu on 2016-06-03
Seems odd that ```

  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
```
there aren´t any relocated sectors.  Bad drive electronics is my guess, but it could be a bad disk controller on the system or bad cable (unlikely).  I´d try a different cable first - see if the errors go away. Then try a different SATA port - see if the errors go away.

[http://arstechnica.com/civis/viewtopic.php?t=1155702](http://arstechnica.com/civis/viewtopic.php?t=1155702) 

If it were mine, I´d have already ordered a replacement. 
Also, I´d have my backups to 100% positive, know-I-can-restore, status.

---

