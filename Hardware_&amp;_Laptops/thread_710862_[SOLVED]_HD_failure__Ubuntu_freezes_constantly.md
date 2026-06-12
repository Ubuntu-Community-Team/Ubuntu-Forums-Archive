---
title: "[SOLVED] HD failure ?? Ubuntu freezes constantly"
date: 2008-02-28
forum: Hardware &amp; Laptops
---

### Post by tango_ninja on 2008-02-28
Hi all,

I'm having some problems recently with Ubuntu in the OS and individual applications. Every now and then, Ubuntu takes a LONG time to load on boot (I'm talking 3 min+).

Sometimes loading programs (Firefox, Picasa, OpenOffice writer, Terminal etc.) will take 60+ seconds to load, and sometimes I'm in the middle of a program and the screen gets greyed out and the computer freezes for about a minute or so. Geez it just did it now, I had to wait a minute to finish this post....

Everytime this happens my HD indicator light is on, and I suspect problems with my HD. I hope its not something to do with Ubuntu, because honestly my winXP system ran more efficiently than this....

here is output of dmesg, it keeps throwing exceptions:

```
[  873.876000] ata1.00: configured for UDMA/133
[  873.876000] ata1: EH complete
[  876.708000] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  876.708000] ata1.00: (irq_stat 0x40000008)
[  876.708000] ata1.00: cmd 60/20:00:d7:dc:05/00:00:00:00:00/40 tag 0 cdb 0x0 data 16384 in
[  876.708000]          res 41/40:00:dd:dc:05/81:00:00:00:00/40 Emask 0x9 (media error)
[  876.736000] ata1.00: configured for UDMA/133
[  876.736000] ata1: EH complete
[  876.736000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[  876.736000] sd 0:0:0:0: [sda] Write Protect is off
[  876.736000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  876.736000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  876.736000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[  876.736000] sd 0:0:0:0: [sda] Write Protect is off
[  876.736000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  876.736000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  908.600000] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  908.600000] ata1.00: (irq_stat 0x40000008)
[  908.600000] ata1.00: cmd 60/20:00:77:0f:39/00:00:00:00:00/40 tag 0 cdb 0x0 data 16384 in
[  908.600000]          res 41/40:00:79:0f:39/81:00:00:00:00/40 Emask 0x9 (media error)
[  908.636000] ata1.00: configured for UDMA/133
[  908.636000] ata1: EH complete
[  909.088000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[  909.088000] sd 0:0:0:0: [sda] Write Protect is off
[  909.088000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  909.092000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  912.200000] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  912.200000] ata1.00: (irq_stat 0x40000008)
[  912.200000] ata1.00: cmd 60/f0:00:3f:cf:05/00:00:00:00:00/40 tag 0 cdb 0x0 data 122880 in
[  912.200000]          res 41/40:00:1e:d0:05/81:00:00:00:00/40 Emask 0x9 (media error)
[  912.240000] ata1.00: configured for UDMA/133
[  912.240000] ata1: EH complete
[  914.712000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[  914.720000] sd 0:0:0:0: [sda] Write Protect is off
[  914.720000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  914.724000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  918.484000] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  918.484000] ata1.00: (irq_stat 0x40000008)
[  918.484000] ata1.00: cmd 60/20:00:9f:d9:05/00:00:00:00:00/40 tag 0 cdb 0x0 data 16384 in
[  918.484000]          res 41/40:00:ad:d9:05/81:00:00:00:00/40 Emask 0x9 (media error)
[  918.524000] ata1.00: configured for UDMA/133
[  918.524000] ata1: EH complete
[  921.568000] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  921.568000] ata1.00: (irq_stat 0x40000008)
[  921.568000] ata1.00: cmd 60/20:00:9f:d9:05/00:00:00:00:00/40 tag 0 cdb 0x0 data 16384 in
[  921.568000]          res 41/40:00:ad:d9:05/81:00:00:00:00/40 Emask 0x9 (media error)
[  921.596000] ata1.00: configured for UDMA/133
[  921.596000] ata1: EH complete
[  924.428000] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  924.428000] ata1.00: (irq_stat 0x40000008)
[  924.428000] ata1.00: cmd 60/20:00:9f:d9:05/00:00:00:00:00/40 tag 0 cdb 0x0 data 16384 in
[  924.428000]          res 41/40:00:ad:d9:05/81:00:00:00:00/40 Emask 0x9 (media error)
[  924.456000] ata1.00: configured for UDMA/133
[  924.456000] ata1: EH complete
[  927.288000] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  927.288000] ata1.00: (irq_stat 0x40000008)
[  927.288000] ata1.00: cmd 60/20:00:9f:d9:05/00:00:00:00:00/40 tag 0 cdb 0x0 data 16384 in
[  927.288000]          res 41/40:00:ad:d9:05/81:00:00:00:00/40 Emask 0x9 (media error)
[  927.316000] ata1.00: configured for UDMA/133
[  927.316000] ata1: EH complete
[  930.356000] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  930.356000] ata1.00: (irq_stat 0x40000008)
[  930.356000] ata1.00: cmd 60/20:00:9f:d9:05/00:00:00:00:00/40 tag 0 cdb 0x0 data 16384 in
[  930.356000]          res 41/40:00:ad:d9:05/81:00:00:00:00/40 Emask 0x9 (media error)
[  930.396000] ata1.00: configured for UDMA/133
[  930.396000] ata1: EH complete
[  933.028000] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  933.028000] ata1.00: (irq_stat 0x40000008)
[  933.028000] ata1.00: cmd 60/20:00:9f:d9:05/00:00:00:00:00/40 tag 0 cdb 0x0 data 16384 in
[  933.028000]          res 41/40:00:ad:d9:05/81:00:00:00:00/40 Emask 0x9 (media error)
[  933.056000] ata1.00: configured for UDMA/133
[  933.056000] ata1: EH complete
[  933.076000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[  933.076000] sd 0:0:0:0: [sda] Write Protect is off
[  933.076000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  933.076000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  933.076000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[  933.076000] sd 0:0:0:0: [sda] Write Protect is off
[  933.076000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  933.080000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1245.480000] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1245.480000] ata1.00: (irq_stat 0x40000008)
[ 1245.480000] ata1.00: cmd 60/08:00:97:33:39/00:00:00:00:00/40 tag 0 cdb 0x0 data 4096 in
[ 1245.480000]          res 41/40:00:97:33:39/81:00:00:00:00/40 Emask 0x9 (media error)
[ 1245.516000] ata1.00: configured for UDMA/133
[ 1245.516000] ata1: EH complete
[ 1248.152000] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1248.152000] ata1.00: (irq_stat 0x40000008)
[ 1248.152000] ata1.00: cmd 60/08:00:97:33:39/00:00:00:00:00/40 tag 0 cdb 0x0 data 4096 in
[ 1248.152000]          res 41/40:00:97:33:39/81:00:00:00:00/40 Emask 0x9 (media error)
[ 1248.188000] ata1.00: configured for UDMA/133
[ 1248.188000] ata1: EH complete
[ 1250.700000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[ 1250.700000] sd 0:0:0:0: [sda] Write Protect is off
[ 1250.700000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1250.700000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1250.700000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[ 1250.700000] sd 0:0:0:0: [sda] Write Protect is off
[ 1250.700000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1250.704000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1518.348000] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1518.348000] ata1.00: (irq_stat 0x40000008)
[ 1518.348000] ata1.00: cmd 60/00:00:bf:7a:11/04:00:00:00:00/40 tag 0 cdb 0x0 data 524288 in
[ 1518.348000]          res 41/40:00:d9:7d:11/81:00:00:00:00/40 Emask 0x9 (media error)
[ 1518.384000] ata1.00: configured for UDMA/133
[ 1518.384000] ata1: EH complete
[ 1521.252000] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1521.252000] ata1.00: (irq_stat 0x40000008)
[ 1521.252000] ata1.00: cmd 60/00:00:bf:7a:11/04:00:00:00:00/40 tag 0 cdb 0x0 data 524288 in
[ 1521.252000]          res 41/40:00:d9:7d:11/81:00:00:00:00/40 Emask 0x9 (media error)
[ 1521.280000] ata1.00: configured for UDMA/133
[ 1521.280000] ata1: EH complete
[ 1524.344000] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1524.344000] ata1.00: (irq_stat 0x40000008)
[ 1524.344000] ata1.00: cmd 60/00:00:bf:7a:11/04:00:00:00:00/40 tag 0 cdb 0x0 data 524288 in
[ 1524.344000]          res 41/40:00:d9:7d:11/81:00:00:00:00/40 Emask 0x9 (media error)
[ 1524.384000] ata1.00: configured for UDMA/133
[ 1524.384000] ata1: EH complete
[ 1527.236000] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1527.236000] ata1.00: (irq_stat 0x40000008)
[ 1527.236000] ata1.00: cmd 60/00:00:bf:7a:11/04:00:00:00:00/40 tag 0 cdb 0x0 data 524288 in
[ 1527.236000]          res 41/40:00:d9:7d:11/81:00:00:00:00/40 Emask 0x9 (media error)
[ 1527.276000] ata1.00: configured for UDMA/133
[ 1527.276000] ata1: EH complete
[ 1529.932000] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1529.932000] ata1.00: (irq_stat 0x40000008)
[ 1529.932000] ata1.00: cmd 60/00:00:bf:7a:11/04:00:00:00:00/40 tag 0 cdb 0x0 data 524288 in
[ 1529.932000]          res 41/40:00:d9:7d:11/81:00:00:00:00/40 Emask 0x9 (media error)
[ 1529.968000] ata1.00: configured for UDMA/133
[ 1529.968000] ata1: EH complete
[ 1532.836000] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1532.836000] ata1.00: (irq_stat 0x40000008)
[ 1532.836000] ata1.00: cmd 60/00:00:bf:7a:11/04:00:00:00:00/40 tag 0 cdb 0x0 data 524288 in
[ 1532.836000]          res 41/40:00:d9:7d:11/81:00:00:00:00/40 Emask 0x9 (media error)
[ 1532.872000] ata1.00: configured for UDMA/133
[ 1532.872000] ata1: EH complete
[ 1532.896000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[ 1535.728000] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1535.728000] ata1.00: (irq_stat 0x40000008)
[ 1535.728000] ata1.00: cmd 60/00:00:bf:82:11/04:00:00:00:00/40 tag 0 cdb 0x0 data 524288 in
[ 1535.728000]          res 41/40:00:c1:84:11/81:00:00:00:00/40 Emask 0x9 (media error)
[ 1535.764000] ata1.00: configured for UDMA/133
[ 1535.768000] ata1: EH complete
[ 1538.620000] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1538.620000] ata1.00: (irq_stat 0x40000008)
[ 1538.620000] ata1.00: cmd 60/00:00:bf:82:11/04:00:00:00:00/40 tag 0 cdb 0x0 data 524288 in
[ 1538.620000]          res 41/40:00:c1:84:11/81:00:00:00:00/40 Emask 0x9 (media error)
[ 1538.648000] ata1.00: configured for UDMA/133
[ 1538.648000] ata1: EH complete
[ 1541.492000] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1541.492000] ata1.00: (irq_stat 0x40000008)
[ 1541.492000] ata1.00: cmd 60/00:00:bf:82:11/04:00:00:00:00/40 tag 0 cdb 0x0 data 524288 in
[ 1541.492000]          res 41/40:00:c1:84:11/81:00:00:00:00/40 Emask 0x9 (media error)
[ 1541.532000] ata1.00: configured for UDMA/133
[ 1541.532000] ata1: EH complete
[ 1544.584000] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1544.584000] ata1.00: (irq_stat 0x40000008)
[ 1544.584000] ata1.00: cmd 60/00:00:bf:82:11/04:00:00:00:00/40 tag 0 cdb 0x0 data 524288 in
[ 1544.584000]          res 41/40:00:c1:84:11/81:00:00:00:00/40 Emask 0x9 (media error)
[ 1544.612000] ata1.00: configured for UDMA/133
[ 1544.612000] ata1: EH complete
[ 1547.256000] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1547.256000] ata1.00: (irq_stat 0x40000008)
[ 1547.256000] ata1.00: cmd 60/00:00:bf:82:11/04:00:00:00:00/40 tag 0 cdb 0x0 data 524288 in
[ 1547.256000]          res 41/40:00:c1:84:11/81:00:00:00:00/40 Emask 0x9 (media error)
[ 1547.296000] ata1.00: configured for UDMA/133
[ 1547.296000] ata1: EH complete
[ 1549.936000] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1549.936000] ata1.00: (irq_stat 0x40000008)
[ 1549.936000] ata1.00: cmd 60/00:00:bf:82:11/04:00:00:00:00/40 tag 0 cdb 0x0 data 524288 in
[ 1549.936000]          res 41/40:00:c1:84:11/81:00:00:00:00/40 Emask 0x9 (media error)
[ 1549.976000] ata1.00: configured for UDMA/133
[ 1549.976000] ata1: EH complete
[ 1549.976000] sd 0:0:0:0: [sda] Write Protect is off
[ 1549.976000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1553.032000] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1553.032000] ata1.00: (irq_stat 0x40000008)
[ 1553.032000] ata1.00: cmd 60/a0:00:bf:86:11/03:00:00:00:00/40 tag 0 cdb 0x0 data 475136 in
[ 1553.032000]          res 41/40:00:f1:87:11/81:00:00:00:00/40 Emask 0x9 (media error)
[ 1553.056000] ata1.00: configured for UDMA/133
[ 1553.056000] ata1: EH complete
[ 1555.912000] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1555.912000] ata1.00: (irq_stat 0x40000008)
[ 1555.912000] ata1.00: cmd 60/a0:00:bf:86:11/03:00:00:00:00/40 tag 0 cdb 0x0 data 475136 in
[ 1555.912000]          res 41/40:00:f1:87:11/81:00:00:00:00/40 Emask 0x9 (media error)
[ 1555.940000] ata1.00: configured for UDMA/133
[ 1555.940000] ata1: EH complete
[ 1557.652000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1557.652000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[ 1557.656000] sd 0:0:0:0: [sda] Write Protect is off
[ 1557.656000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1557.656000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1561.156000] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1561.156000] ata1.00: (irq_stat 0x40000008)
[ 1561.156000] ata1.00: cmd 60/00:00:5f:8a:11/04:00:00:00:00/40 tag 0 cdb 0x0 data 524288 in
[ 1561.156000]          res 41/40:00:50:8e:11/81:00:00:00:00/40 Emask 0x9 (media error)
[ 1561.192000] ata1.00: configured for UDMA/133
[ 1561.192000] ata1: EH complete
[ 1563.848000] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1563.848000] ata1.00: (irq_stat 0x40000008)
[ 1563.848000] ata1.00: cmd 60/00:00:5f:8a:11/04:00:00:00:00/40 tag 0 cdb 0x0 data 524288 in
[ 1563.848000]          res 41/40:00:50:8e:11/81:00:00:00:00/40 Emask 0x9 (media error)
[ 1563.888000] ata1.00: configured for UDMA/133
[ 1563.888000] ata1: EH complete
[ 1566.544000] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1566.544000] ata1.00: (irq_stat 0x40000008)
[ 1566.544000] ata1.00: cmd 60/00:00:5f:8a:11/04:00:00:00:00/40 tag 0 cdb 0x0 data 524288 in
[ 1566.544000]          res 41/40:00:50:8e:11/81:00:00:00:00/40 Emask 0x9 (media error)
[ 1566.568000] ata1.00: configured for UDMA/133
[ 1566.572000] ata1: EH complete
[ 1569.212000] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1569.212000] ata1.00: (irq_stat 0x40000008)
[ 1569.212000] ata1.00: cmd 60/00:00:5f:8a:11/04:00:00:00:00/40 tag 0 cdb 0x0 data 524288 in
[ 1569.212000]          res 41/40:00:50:8e:11/81:00:00:00:00/40 Emask 0x9 (media error)
[ 1569.252000] ata1.00: configured for UDMA/133
[ 1569.252000] ata1: EH complete
[ 1572.096000] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1572.096000] ata1.00: (irq_stat 0x40000008)
[ 1572.096000] ata1.00: cmd 60/00:00:5f:8a:11/04:00:00:00:00/40 tag 0 cdb 0x0 data 524288 in
[ 1572.096000]          res 41/40:00:50:8e:11/81:00:00:00:00/40 Emask 0x9 (media error)
[ 1572.136000] ata1.00: configured for UDMA/133
[ 1572.136000] ata1: EH complete
[ 1574.988000] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1574.988000] ata1.00: (irq_stat 0x40000008)
[ 1574.988000] ata1.00: cmd 60/00:00:5f:8a:11/04:00:00:00:00/40 tag 0 cdb 0x0 data 524288 in
[ 1574.988000]          res 41/40:00:50:8e:11/81:00:00:00:00/40 Emask 0x9 (media error)
[ 1575.016000] ata1.00: configured for UDMA/133
[ 1575.016000] ata1: EH complete
[ 1578.080000] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1578.080000] ata1.00: (irq_stat 0x40000008)
[ 1578.080000] ata1.00: cmd 60/00:00:5f:8e:11/04:00:00:00:00/40 tag 0 cdb 0x0 data 524288 in
[ 1578.080000]          res 41/40:00:80:91:11/81:00:00:00:00/40 Emask 0x9 (media error)
[ 1578.108000] ata1.00: configured for UDMA/133
[ 1578.108000] ata1: EH complete
[ 1580.764000] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1580.764000] ata1.00: (irq_stat 0x40000008)
[ 1580.764000] ata1.00: cmd 60/00:00:5f:8e:11/04:00:00:00:00/40 tag 0 cdb 0x0 data 524288 in
[ 1580.764000]          res 41/40:00:80:91:11/81:00:00:00:00/40 Emask 0x9 (media error)
[ 1580.804000] ata1.00: configured for UDMA/133
[ 1580.804000] ata1: EH complete
[ 1583.456000] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1583.456000] ata1.00: (irq_stat 0x40000008)
[ 1583.456000] ata1.00: cmd 60/00:00:5f:8e:11/04:00:00:00:00/40 tag 0 cdb 0x0 data 524288 in
[ 1583.456000]          res 41/40:00:80:91:11/81:00:00:00:00/40 Emask 0x9 (media error)
[ 1583.484000] ata1.00: configured for UDMA/133
[ 1583.484000] ata1: EH complete
[ 1586.352000] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1586.352000] ata1.00: (irq_stat 0x40000008)
[ 1586.352000] ata1.00: cmd 60/00:00:5f:8e:11/04:00:00:00:00/40 tag 0 cdb 0x0 data 524288 in
[ 1586.352000]          res 41/40:00:80:91:11/81:00:00:00:00/40 Emask 0x9 (media error)
[ 1586.388000] ata1.00: configured for UDMA/133
[ 1586.388000] ata1: EH complete
[ 1589.044000] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1589.044000] ata1.00: (irq_stat 0x40000008)
[ 1589.044000] ata1.00: cmd 60/00:00:5f:8e:11/04:00:00:00:00/40 tag 0 cdb 0x0 data 524288 in
[ 1589.044000]          res 41/40:00:80:91:11/81:00:00:00:00/40 Emask 0x9 (media error)
[ 1589.084000] ata1.00: configured for UDMA/133
[ 1589.084000] ata1: EH complete
[ 1591.948000] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1591.948000] ata1.00: (irq_stat 0x40000008)
[ 1591.948000] ata1.00: cmd 60/00:00:5f:8e:11/04:00:00:00:00/40 tag 0 cdb 0x0 data 524288 in
[ 1591.948000]          res 41/40:00:80:91:11/81:00:00:00:00/40 Emask 0x9 (media error)
[ 1591.988000] ata1.00: configured for UDMA/133
[ 1591.988000] ata1: EH complete
[ 1591.988000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[ 1595.040000] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1595.040000] ata1.00: (irq_stat 0x40000008)
[ 1595.040000] ata1.00: cmd 60/00:00:5f:92:11/04:00:00:00:00/40 tag 0 cdb 0x0 data 524288 in
[ 1595.040000]          res 41/40:00:b0:94:11/81:00:00:00:00/40 Emask 0x9 (media error)
[ 1595.080000] ata1.00: configured for UDMA/133
[ 1595.080000] ata1: EH complete
[ 1597.576000] sd 0:0:0:0: [sda] Write Protect is off
[ 1597.576000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1600.208000] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1600.208000] ata1.00: (irq_stat 0x40000008)
[ 1600.208000] ata1.00: cmd 60/00:00:5f:96:11/04:00:00:00:00/40 tag 0 cdb 0x0 data 524288 in
[ 1600.208000]          res 41/40:00:df:97:11/81:00:00:00:00/40 Emask 0x9 (media error)
[ 1600.244000] ata1.00: configured for UDMA/133
[ 1600.244000] ata1: EH complete
[ 1603.088000] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1603.088000] ata1.00: (irq_stat 0x40000008)
[ 1603.088000] ata1.00: cmd 60/00:00:5f:96:11/04:00:00:00:00/40 tag 0 cdb 0x0 data 524288 in
[ 1603.088000]          res 41/40:00:df:97:11/81:00:00:00:00/40 Emask 0x9 (media error)
[ 1603.128000] ata1.00: configured for UDMA/133
[ 1603.128000] ata1: EH complete
[ 1605.672000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1605.684000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[ 1605.684000] sd 0:0:0:0: [sda] Write Protect is off
[ 1605.684000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1605.708000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1608.376000] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1608.376000] ata1.00: (irq_stat 0x40000008)
[ 1608.376000] ata1.00: cmd 60/a0:00:cf:a6:11/03:00:00:00:00/40 tag 0 cdb 0x0 data 475136 in
[ 1608.376000]          res 41/40:00:56:a8:11/81:00:00:00:00/40 Emask 0x9 (media error)
[ 1608.416000] ata1.00: configured for UDMA/133
[ 1608.416000] ata1: EH complete
[ 1611.680000] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1611.680000] ata1.00: (irq_stat 0x40000008)
[ 1611.680000] ata1.00: cmd 60/a0:00:cf:a6:11/03:00:00:00:00/40 tag 0 cdb 0x0 data 475136 in
[ 1611.680000]          res 41/40:00:56:a8:11/81:00:00:00:00/40 Emask 0x9 (media error)
[ 1611.716000] ata1.00: configured for UDMA/133
[ 1611.716000] ata1: EH complete
[ 1614.360000] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1614.360000] ata1.00: (irq_stat 0x40000008)
[ 1614.360000] ata1.00: cmd 60/a0:00:cf:a6:11/03:00:00:00:00/40 tag 0 cdb 0x0 data 475136 in
[ 1614.360000]          res 41/40:00:56:a8:11/81:00:00:00:00/40 Emask 0x9 (media error)
[ 1614.388000] ata1.00: configured for UDMA/133
[ 1614.388000] ata1: EH complete
[ 1617.244000] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1617.244000] ata1.00: (irq_stat 0x40000008)
[ 1617.244000] ata1.00: cmd 60/a0:00:cf:a6:11/03:00:00:00:00/40 tag 0 cdb 0x0 data 475136 in
[ 1617.244000]          res 41/40:00:56:a8:11/81:00:00:00:00/40 Emask 0x9 (media error)
[ 1617.280000] ata1.00: configured for UDMA/133
[ 1617.280000] ata1: EH complete
[ 1620.536000] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1620.536000] ata1.00: (irq_stat 0x40000008)
[ 1620.536000] ata1.00: cmd 60/a0:00:cf:a6:11/03:00:00:00:00/40 tag 0 cdb 0x0 data 475136 in
[ 1620.536000]          res 41/40:00:56:a8:11/81:00:00:00:00/40 Emask 0x9 (media error)
[ 1620.564000] ata1.00: configured for UDMA/133
[ 1620.564000] ata1: EH complete
[ 1623.196000] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1623.196000] ata1.00: (irq_stat 0x40000008)
[ 1623.196000] ata1.00: cmd 60/a0:00:cf:a6:11/03:00:00:00:00/40 tag 0 cdb 0x0 data 475136 in
[ 1623.196000]          res 41/40:00:56:a8:11/81:00:00:00:00/40 Emask 0x9 (media error)
[ 1623.224000] ata1.00: configured for UDMA/133
[ 1623.224000] ata1: EH complete
[ 1623.240000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[ 1623.244000] sd 0:0:0:0: [sda] Write Protect is off
[ 1623.244000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1623.244000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1623.248000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[ 1623.248000] sd 0:0:0:0: [sda] Write Protect is off
[ 1623.248000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1623.248000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1627.076000] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1627.076000] ata1.00: (irq_stat 0x40000008)
[ 1627.076000] ata1.00: cmd 60/00:00:6f:ae:11/04:00:00:00:00/40 tag 0 cdb 0x0 data 524288 in
[ 1627.076000]          res 41/40:00:e6:b1:11/81:00:00:00:00/40 Emask 0x9 (media error)
[ 1627.112000] ata1.00: configured for UDMA/133
[ 1627.112000] ata1: EH complete
[ 1630.820000] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1630.820000] ata1.00: (irq_stat 0x40000008)
[ 1630.820000] ata1.00: cmd 60/00:00:6f:ae:11/04:00:00:00:00/40 tag 0 cdb 0x0 data 524288 in
[ 1630.820000]          res 41/40:00:e6:b1:11/81:00:00:00:00/40 Emask 0x9 (media error)
[ 1630.860000] ata1.00: configured for UDMA/133
[ 1630.860000] ata1: EH complete
[ 1634.160000] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1634.160000] ata1.00: (irq_stat 0x40000008)
[ 1634.160000] ata1.00: cmd 60/00:00:6f:ae:11/04:00:00:00:00/40 tag 0 cdb 0x0 data 524288 in
[ 1634.160000]          res 41/40:00:e6:b1:11/81:00:00:00:00/40 Emask 0x9 (media error)
[ 1634.196000] ata1.00: configured for UDMA/133
[ 1634.196000] ata1: EH complete
[ 1637.040000] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1637.040000] ata1.00: (irq_stat 0x40000008)
[ 1637.040000] ata1.00: cmd 60/00:00:6f:ae:11/04:00:00:00:00/40 tag 0 cdb 0x0 data 524288 in
[ 1637.040000]          res 41/40:00:b6:ae:11/81:00:00:00:00/40 Emask 0x9 (media error)
[ 1637.080000] ata1.00: configured for UDMA/133
[ 1637.080000] ata1: EH complete
[ 1640.168000] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1640.168000] ata1.00: (irq_stat 0x40000008)
[ 1640.168000] ata1.00: cmd 60/00:00:6f:ae:11/04:00:00:00:00/40 tag 0 cdb 0x0 data 524288 in
[ 1640.168000]          res 41/40:00:e6:b1:11/81:00:00:00:00/40 Emask 0x9 (media error)
[ 1640.204000] ata1.00: configured for UDMA/133
[ 1640.204000] ata1: EH complete
[ 1643.836000] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[ 1643.836000] ata1.00: (irq_stat 0x40000008)
[ 1643.836000] ata1.00: cmd 60/00:00:6f:ae:11/04:00:00:00:00/40 tag 0 cdb 0x0 data 524288 in
[ 1643.836000]          res 41/40:00:e6:b1:11/81:00:00:00:00/40 Emask 0x9 (media error)
[ 1643.864000] ata1.00: configured for UDMA/133
[ 1643.864000] ata1: EH complete
[ 1643.884000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[ 1643.888000] sd 0:0:0:0: [sda] Write Protect is off
[ 1643.888000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1643.928000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1643.952000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[ 1643.960000] sd 0:0:0:0: [sda] Write Protect is off
[ 1643.960000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1643.976000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

```

---

### Post by Eggbanjo on 2008-02-29
after weeks/months of having this issue i think (hasnt happened again sine) i found the issue.

I was leaving my pc on over night to download, coming back to find it frozen, also found that if i left it for more than 20mins it would freeze to.

What i did was go into bios and change Upnp Os from NO to YES

no more log error messages, no more freezing!!!!

---

### Post by tango_ninja on 2008-02-29
I don't think that this is the cause... my system freezes all the time....while loading, while surfing, while doing unbelievably trivial tasks....
i think i'm going to bite the bullet, get a new HD for my laptop and hope that works :O

---

### Post by tango_ninja on 2008-03-19
Just in case any of you were biting your nails on this one.... I've purchased a new HD and everything is tickity-boo.

---

