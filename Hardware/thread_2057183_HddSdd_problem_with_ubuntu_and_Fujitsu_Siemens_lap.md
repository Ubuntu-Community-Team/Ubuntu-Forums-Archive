---
title: "Hdd/Sdd problem with ubuntu and Fujitsu Siemens laptop"
date: 2012-09-13
forum: Hardware
---

### Post by Jens.L on 2012-09-13
Hi

I bought a new ssd drive to my laptop. OCZ Vertex 3 90gb. But i got weird stuff posting in dmesg. I have tried with another Ocz Agility 3 ssd and with a standard 500gb hdd but it's the same fault. Computer feels real slow. 

DMESG
```
[    0.599234] ata3: SATA max UDMA/133 abar m1024@0xfe9ffc00 port 0xfe9ffe00 irq 22
[    0.920046] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    0.931796] ata3.00: ATA-8: OCZ-VERTEX3, 2.22, max UDMA/133
[    0.931799] ata3.00: 175836528 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    0.941969] ata3.00: configured for UDMA/133
[  144.688982] ata3: exception Emask 0x10 SAct 0x0 SErr 0x90202 action 0xe frozen
[  144.688988] ata3: irq_stat 0x00400000, PHY RDY changed
[  144.688993] ata3: SError: { RecovComm Persist PHYRdyChg 10B8B }
[  144.689002] ata3: hard resetting link
[  145.412095] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  145.433835] ata3.00: configured for UDMA/133
[  145.434265] ata3: EH complete
[  193.665764] ata3: exception Emask 0x10 SAct 0x0 SErr 0x90202 action 0xe frozen
[  193.665774] ata3: irq_stat 0x00400000, PHY RDY changed
[  193.665783] ata3: SError: { RecovComm Persist PHYRdyChg 10B8B }
[  193.665795] ata3: hard resetting link
[  194.388088] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  194.410173] ata3.00: configured for UDMA/133
[  194.410609] ata3: EH complete
[  293.747432] ata3: exception Emask 0x10 SAct 0x0 SErr 0x90202 action 0xe frozen
[  293.747439] ata3: irq_stat 0x00400000, PHY RDY changed
[  293.747444] ata3: SError: { RecovComm Persist PHYRdyChg 10B8B }
[  293.747452] ata3: hard resetting link
[  294.468153] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  294.490188] ata3.00: configured for UDMA/133
[  294.490593] ata3: EH complete
[  653.538349] ata3: limiting SATA link speed to 1.5 Gbps
[  653.538361] ata3: exception Emask 0x10 SAct 0x0 SErr 0x90202 action 0xe frozen
[  653.538369] ata3: irq_stat 0x00400000, PHY RDY changed
[  653.538377] ata3: SError: { RecovComm Persist PHYRdyChg 10B8B }
[  653.538389] ata3: hard resetting link
[  654.260126] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  654.282233] ata3.00: configured for UDMA/133
[  654.282664] ata3: EH complete
[  680.878723] ata3: exception Emask 0x10 SAct 0x0 SErr 0x90200 action 0xe frozen
[  680.878730] ata3: irq_stat 0x00400000, PHY RDY changed
[  680.878735] ata3: SError: { Persist PHYRdyChg 10B8B }
[  680.878742] ata3: hard resetting link
[  681.600095] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  681.621857] ata3.00: configured for UDMA/133
[  681.622291] ata3: EH complete
[  743.343037] ata3: exception Emask 0x10 SAct 0x0 SErr 0x90200 action 0xe frozen
[  743.343047] ata3: irq_stat 0x00400000, PHY RDY changed
[  743.343055] ata3: SError: { Persist PHYRdyChg 10B8B }
[  743.343066] ata3: hard resetting link
[  744.064073] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  744.085705] ata3.00: configured for UDMA/133
[  744.086143] ata3: EH complete
[  748.430403] ata3: exception Emask 0x10 SAct 0x0 SErr 0x90200 action 0xe frozen
[  748.430413] ata3: irq_stat 0x00400000, PHY RDY changed
[  748.430422] ata3: SError: { Persist PHYRdyChg 10B8B }
[  748.430433] ata3: hard resetting link
[  749.152093] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  749.173933] ata3.00: configured for UDMA/133
[  749.174374] ata3: EH complete
[ 1147.236789] ata3.00: limiting speed to UDMA/100:PIO4
[ 1147.236800] ata3: exception Emask 0x10 SAct 0x0 SErr 0x90200 action 0xe frozen
[ 1147.236808] ata3: irq_stat 0x00400000, PHY RDY changed
[ 1147.236817] ata3: SError: { Persist PHYRdyChg 10B8B }
[ 1147.236828] ata3: hard resetting link
[ 1147.960093] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 1147.982052] ata3.00: configured for UDMA/100
[ 1147.982486] ata3: EH complete
[ 1166.919298] ata3: exception Emask 0x10 SAct 0x0 SErr 0x90200 action 0xe frozen
[ 1166.919309] ata3: irq_stat 0x00400000, PHY RDY changed
[ 1166.919318] ata3: SError: { Persist PHYRdyChg 10B8B }
[ 1166.919329] ata3: hard resetting link
[ 1167.640052] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 1167.662016] ata3.00: configured for UDMA/100
[ 1167.662449] ata3: EH complete
[ 1269.499928] ata3: exception Emask 0x10 SAct 0x0 SErr 0x90200 action 0xe frozen
[ 1269.499938] ata3: irq_stat 0x00400000, PHY RDY changed
[ 1269.499946] ata3: SError: { Persist PHYRdyChg 10B8B }
[ 1269.499958] ata3: hard resetting link
[ 1270.220105] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 1270.241747] ata3.00: configured for UDMA/100
[ 1270.242179] ata3: EH complete
[ 1272.575197] ata3: exception Emask 0x10 SAct 0x0 SErr 0x90200 action 0xe frozen
[ 1272.575203] ata3: irq_stat 0x00400000, PHY RDY changed
[ 1272.575208] ata3: SError: { Persist PHYRdyChg 10B8B }
[ 1272.575216] ata3: hard resetting link
[ 1273.296138] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 1273.318233] ata3.00: configured for UDMA/100
[ 1273.318726] ata3: EH complete
[ 1308.479456] ata3.00: limiting speed to UDMA/33:PIO4
[ 1308.479468] ata3: exception Emask 0x10 SAct 0x0 SErr 0x90200 action 0xe frozen
[ 1308.479475] ata3: irq_stat 0x00400000, PHY RDY changed
[ 1308.479484] ata3: SError: { Persist PHYRdyChg 10B8B }
[ 1308.479495] ata3: hard resetting link
[ 1309.200088] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 1309.221792] ata3.00: configured for UDMA/33
[ 1309.222214] ata3: EH complete
[ 1347.714271] ata3: exception Emask 0x10 SAct 0x0 SErr 0x90200 action 0xe frozen
[ 1347.714276] ata3: irq_stat 0x00400000, PHY RDY changed
[ 1347.714282] ata3: SError: { Persist PHYRdyChg 10B8B }
[ 1347.714289] ata3: hard resetting link
[ 1348.436091] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 1348.458113] ata3.00: configured for UDMA/33
[ 1348.458550] ata3: EH complete
[ 1426.865719] ata3: exception Emask 0x10 SAct 0x0 SErr 0x90200 action 0xe frozen
[ 1426.865725] ata3: irq_stat 0x00400000, PHY RDY changed
[ 1426.865730] ata3: SError: { Persist PHYRdyChg 10B8B }
[ 1426.865737] ata3: hard resetting link
[ 1427.588090] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 1427.609842] ata3.00: configured for UDMA/33
[ 1427.610276] ata3: EH complete
[ 1508.291712] ata3: exception Emask 0x10 SAct 0x0 SErr 0x90200 action 0xe frozen
[ 1508.291723] ata3: irq_stat 0x00400000, PHY RDY changed
[ 1508.291733] ata3: SError: { Persist PHYRdyChg 10B8B }
[ 1508.291744] ata3: hard resetting link
[ 1509.012098] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 1509.033952] ata3.00: configured for UDMA/33
[ 1509.034389] ata3: EH complete
```

Somebody who knows what i can do?. Running Ubuntu 12.04 64bit

Fujitsu Siemens XA3530
4gb ram
Athlon64 cpu
Ati Radeon 3200

---

### Post by kimberlite on 2012-09-13
As it is written in this [page]("https://ata.wiki.kernel.org/index.php/Libata_error_messages"):

"SATA SError expansion

If any bits in the SATA SError register are set, the SError register contents will be expanded into its component bits, for example:
SError: { PHYRdyChg CommWake }
These bits are set by the SATA host interface in response to error conditions on the SATA link. Unless a drive hotplug or unplug operation occurred, it is generally not normal to see any of these bits set. If they are, it usually points strongly toward a hardware problem (often a bad SATA cable or a bad or inadequate power supply)."

So check cables and power supply.
HTH

---

### Post by Jens.L on 2012-09-13
It's a laptop so i can't change sata cable. I can try with a another power supply but i don't think that will help.

Edit: It was a bad mainboard. I had a spare mainboard to my laptop so i replaced it.

---

