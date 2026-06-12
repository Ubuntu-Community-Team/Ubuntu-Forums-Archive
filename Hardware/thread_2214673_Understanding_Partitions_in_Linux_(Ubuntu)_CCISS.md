---
title: "Understanding Partitions in Linux (Ubuntu) CCISS"
date: 2014-04-02
forum: Hardware
---

### Post by CasperJames on 2014-04-02
[LIST]
[*][COLOR=#660066]Device | [/COLOR][COLOR=#660066]Boot | [/COLOR][COLOR=#660066]Start | [/COLOR][COLOR=#660066]End | [/COLOR][COLOR=#660066]Blocks | [/COLOR][COLOR=#660066]Id | [/COLOR][COLOR=#660066]System[/COLOR]
[*][COLOR=#666600]/[/COLOR][COLOR=#000000]dev[/COLOR][COLOR=#666600]/[/COLOR][COLOR=#000000]cciss[/COLOR][COLOR=#666600]/[/COLOR][COLOR=#000000]c0d0p1 | [/COLOR][COLOR=#666600]* | [/COLOR][COLOR=#006666]2048 | [/COLOR][COLOR=#006666]499711 | [/COLOR][COLOR=#006666]248832 | [/COLOR][COLOR=#006666]83 | [/COLOR][COLOR=#660066]Linux[/COLOR]
[*][COLOR=#666600]/[/COLOR][COLOR=#000000]dev[/COLOR][COLOR=#666600]/[/COLOR][COLOR=#000000]cciss[/COLOR][COLOR=#666600]/[/COLOR][COLOR=#000000]c0d0p2 | [/COLOR][COLOR=#006666]501758 | [/COLOR][COLOR=#006666]573366271 | [/COLOR][COLOR=#006666]286432257 | [/COLOR][COLOR=#006666]5 | [/COLOR][COLOR=#660066]Extended[/COLOR]
[*][COLOR=#666600]/[/COLOR][COLOR=#000000]dev[/COLOR][COLOR=#666600]/[/COLOR][COLOR=#000000]cciss[/COLOR][COLOR=#666600]/[/COLOR][COLOR=#000000]c0d0p5 | [/COLOR][COLOR=#006666]501760 | [/COLOR][COLOR=#006666]573366271 | [/COLOR][COLOR=#006666]286432256 | [/COLOR][COLOR=#006666]83 | [/COLOR][COLOR=#660066]Linux[/COLOR]
[/LIST]


[COLOR=#434343][FONT=helvetica]Okay, we are building a new data server that has 6 disks - we partitioned the first 4 as a RAID 1 and the last 2 as a RAID 0. Our RAID 1 will house the main data server and the RAID 0 we want to use as a NAS/file storage device. My question is which partition is the RAID 0? Is the Extended partition the RAID 0? I want to mount 0 on the 1 as a NAS but I don't want to write the files to the wrong device.[/FONT][/COLOR]
[COLOR=#434343][FONT=helvetica]Thanks[/FONT][/COLOR]

---

