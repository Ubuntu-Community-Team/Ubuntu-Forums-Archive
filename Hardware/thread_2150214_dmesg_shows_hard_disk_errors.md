---
title: "dmesg shows hard disk errors?"
date: 2013-05-31
forum: Hardware
---

### Post by deri on 2013-05-31
[  295.588876] ata1.00: status: { DRDY }
[  295.588885] ata1: hard resetting link
[  305.604546] ata1: softreset failed (1st FIS failed)
[  305.604563] ata1: hard resetting link
[  306.097081] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  306.098518] ata1.00: configured for UDMA/100
[  306.145223] ata1: EH complete

[ 2283.716273] ata1.00: exception Emask 0x10 SAct 0x0 SErr 0x400001 action 0x6 frozen
[ 2283.716286] ata1.00: irq_stat 0x08000000, interface fatal error
[ 2283.716295] ata1: SError: { RecovData Handshk }
[ 2283.716305] sr 0:0:0:0: CDB: 
[ 2283.716309] Get event status notification: 4a 01 00 00 10 00 00 00 08 00
[ 2283.716350] ata1.00: cmd a0/00:00:00:08:00/00:00:00:00:00/a0 tag 0 pio 16392 in
[ 2283.716350]          res 50/00:03:00:08:00/00:00:00:00:00/a0 Emask 0x10 (ATA bus error)
[ 2283.716358] ata1.00: status: { DRDY }
[ 2283.716368] ata1: hard resetting link
[ 2293.731891] ata1: softreset failed (1st FIS failed)
[ 2293.731906] ata1: hard resetting link
[ 2294.224645] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 2294.225671] ata1.00: configured for UDMA/100
[ 2294.272735] ata1: EH complete

[ 2600.114185] ata1.00: exception Emask 0x10 SAct 0x0 SErr 0x400000 action 0x6 frozen
[ 2600.114193] ata1.00: irq_stat 0x08000000, interface fatal error
[ 2600.114196] ata1: SError: { Handshk }
[ 2600.114202] sr 0:0:0:0: CDB: 
[ 2600.114204] Get event status notification: 4a 01 00 00 10 00 00 00 08 00
[ 2600.114214] ata1.00: cmd a0/00:00:00:08:00/00:00:00:00:00/a0 tag 0 pio 16392 in
[ 2600.114214]          res 50/00:03:00:08:00/00:00:00:00:00/a0 Emask 0x10 (ATA bus error)
[ 2600.114217] ata1.00: status: { DRDY }
[ 2600.114222] ata1: hard resetting link
[ 2610.129764] ata1: softreset failed (1st FIS failed)
[ 2610.129779] ata1: hard resetting link
[ 2610.622565] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 2610.623546] ata1.00: configured for UDMA/100
[ 2610.670666] ata1: EH complete
[ 2623.190275] ata1.00: exception Emask 0x10 SAct 0x0 SErr 0x400000 action 0x6 frozen
[ 2623.190288] ata1.00: irq_stat 0x08000000, interface fatal error
[ 2623.190296] ata1: SError: { Handshk }
[ 2623.190314] sr 0:0:0:0: CDB: 
[ 2623.190318] Get event status notification: 4a 01 00 00 10 00 00 00 08 00
[ 2623.190346] ata1.00: cmd a0/00:00:00:08:00/00:00:00:00:00/a0 tag 0 pio 16392 in
[ 2623.190346]          res 50/00:03:00:08:00/00:00:00:00:00/a0 Emask 0x10 (ATA bus error)
[ 2623.190354] ata1.00: status: { DRDY }
[ 2623.190364] ata1: hard resetting link
[ 2623.257195] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:74:ea:3a:a7:c9:10:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 2633.209775] ata1: softreset failed (1st FIS failed)
[ 2633.209783] ata1: hard resetting link
[ 2633.702567] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 2633.703930] ata1.00: configured for UDMA/100
[ 2633.718631] ata1: EH complete
[ 2748.455774] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:74:ea:3a:a7:c9:10:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 2873.654373] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:74:ea:3a:a7:c9:10:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 2994.970710] ata1.00: exception Emask 0x10 SAct 0x0 SErr 0x400001 action 0x6 frozen
[ 2994.970728] ata1.00: irq_stat 0x08000000, interface fatal error
[ 2994.970738] ata1: SError: { RecovData Handshk }
[ 2994.970751] sr 0:0:0:0: CDB: 
[ 2994.970756] Get event status notification: 4a 01 00 00 10 00 00 00 08 00
[ 2994.970785] ata1.00: cmd a0/00:00:00:08:00/00:00:00:00:00/a0 tag 0 pio 16392 in
[ 2994.970785]          res 50/00:03:00:08:00/00:00:00:00:00/a0 Emask 0x10 (ATA bus error)
[ 2994.970793] ata1.00: status: { DRDY }
[ 2994.970804] ata1: hard resetting link
[ 2998.852892] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:74:ea:3a:a7:c9:10:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 3004.986176] ata1: softreset failed (1st FIS failed)
[ 3004.986183] ata1: hard resetting link
[ 3005.478963] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 3005.483912] ata1.00: configured for UDMA/100
[ 3005.515050] ata1: EH complete
[ 3091.889926] ata1: limiting SATA link speed to 1.5 Gbps
[ 3091.889933] ata1.00: exception Emask 0x10 SAct 0x0 SErr 0x400001 action 0x6 frozen
[ 3091.889937] ata1.00: irq_stat 0x08000000, interface fatal error
[ 3091.889940] ata1: SError: { RecovData Handshk }
[ 3091.889944] sr 0:0:0:0: CDB: 
[ 3091.889946] Get event status notification: 4a 01 00 00 10 00 00 00 08 00
[ 3091.889957] ata1.00: cmd a0/00:00:00:08:00/00:00:00:00:00/a0 tag 0 pio 16392 in
[ 3091.889957]          res 50/00:03:00:08:00/00:00:00:00:00/a0 Emask 0x10 (ATA bus error)
[ 3091.889959] ata1.00: status: { DRDY }
[ 3091.889964] ata1: hard resetting link
[ 3101.905457] ata1: softreset failed (1st FIS failed)
[ 3101.905473] ata1: hard resetting link
[ 3102.398243] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 3102.403705] ata1.00: configured for UDMA/100
[ 3102.418279] ata1: EH complete
[ 3124.051482] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:74:ea:3a:a7:c9:10:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 3192.911630] ata1.00: exception Emask 0x10 SAct 0x0 SErr 0x400001 action 0x6 frozen
[ 3192.911643] ata1.00: irq_stat 0x08000000, interface fatal error
[ 3192.911652] ata1: SError: { RecovData Handshk }
[ 3192.911663] sr 0:0:0:0: CDB: 
[ 3192.911667] Get event status notification: 4a 01 00 00 10 00 00 00 08 00
[ 3192.911694] ata1.00: cmd a0/00:00:00:08:00/00:00:00:00:00/a0 tag 0 pio 16392 in
[ 3192.911694]          res 50/00:03:00:08:00/00:00:00:00:00/a0 Emask 0x10 (ATA bus error)

---

### Post by tgalati4 on 2013-05-31
Could be a loose cable, dirty connection, interference within the cable or a pinched cable, or a failing SATA controller chip either on the motherboard or on the hard disk.  Try switching the cable first.

---

