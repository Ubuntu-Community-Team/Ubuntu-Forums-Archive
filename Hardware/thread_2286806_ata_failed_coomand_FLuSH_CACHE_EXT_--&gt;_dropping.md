---
title: "ata failed coomand FLuSH CACHE EXT --&gt; dropping from 6.0Gb/s to 3.0Gb/s"
date: 2015-07-14
forum: Hardware
---

### Post by alex351 on 2015-07-14
hi there,

I have a very strange problem that I could not find a solution for on the web and came again to the awesome forums in hopes of a solution.

I have 2x ASM1062 PCIe SATA III Controller in my ubuntu server. Each card has 2 SATA III drives connected to it (1 controller has 2x WD30EFRX drives and 1 controller has 2x 8TB Seagate Archive v2 drives connected).

I get from one of the Seagate drives failed command FLUSH CACHE EXT errors until the sata link drops to 3.0Gb/s then the errors stop. this happens under load:

```
[  181.743476] ata10.00: exception Emask 0x10 SAct 0x0 SErr 0x4050002 action 0x6 frozen[  181.743502] ata10.00: irq_stat 0x08000000, interface fatal error
[  181.743518] ata10: SError: { RecovComm PHYRdyChg CommWake DevExch }
[  181.743534] ata10.00: failed command: FLUSH CACHE EXT
[  181.743549] ata10.00: cmd ea/00:00:00:00:00/00:00:00:00:00/a0 tag 19
         res 40/00:98:c0:ec:67/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[  181.743582] ata10.00: status: { DRDY }
[  181.743593] ata10: hard resetting link
[  182.235851] ata10: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[  182.238604] ata10.00: configured for UDMA/133
[  182.238607] ata10.00: retrying FLUSH 0xea Emask 0x10
[  182.238816] ata10: EH complete
[  196.384727] ata10.00: exception Emask 0x10 SAct 0x0 SErr 0x4050002 action 0x6 frozen
[  196.384752] ata10.00: irq_stat 0x08000000, interface fatal error
[  196.384769] ata10: SError: { RecovComm PHYRdyChg CommWake DevExch }
[  196.384785] ata10.00: failed command: FLUSH CACHE EXT
[  196.384799] ata10.00: cmd ea/00:00:00:00:00/00:00:00:00:00/a0 tag 24
         res 40/00:c0:c0:17:b0/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[  196.384832] ata10.00: status: { DRDY }
[  196.384844] ata10: hard resetting link
[  196.877056] ata10: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[  196.879700] ata10.00: configured for UDMA/133
[  196.879703] ata10.00: retrying FLUSH 0xea Emask 0x10
[  196.879899] ata10: EH complete
[  216.916517] ata10.00: exception Emask 0x10 SAct 0x0 SErr 0x4050000 action 0x6 frozen
[  216.916542] ata10.00: irq_stat 0x08000000, interface fatal error
[  216.916558] ata10: SError: { PHYRdyChg CommWake DevExch }
[  216.916572] ata10.00: failed command: FLUSH CACHE EXT
[  216.916587] ata10.00: cmd ea/00:00:00:00:00/00:00:00:00:00/a0 tag 24
         res 40/00:c0:40:62:1c/00:00:01:00:00/40 Emask 0x10 (ATA bus error)
[  216.916620] ata10.00: status: { DRDY }
[  216.916632] ata10: hard resetting link
[  217.408782] ata10: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[  217.411446] ata10.00: configured for UDMA/133
[  217.411448] ata10.00: retrying FLUSH 0xea Emask 0x10
[  217.411717] ata10: EH complete
[  226.653814] ata10: limiting SATA link speed to 3.0 Gbps
[  226.653818] ata10.00: exception Emask 0x10 SAct 0x0 SErr 0x4050000 action 0x6 frozen
[  226.653840] ata10.00: irq_stat 0x08000000, interface fatal error
[  226.653856] ata10: SError: { PHYRdyChg CommWake DevExch }
[  226.653871] ata10.00: failed command: FLUSH CACHE EXT
[  226.653885] ata10.00: cmd ea/00:00:00:00:00/00:00:00:00:00/a0 tag 12
         res 40/00:60:80:67:39/00:00:01:00:00/40 Emask 0x10 (ATA bus error)
[  226.653918] ata10.00: status: { DRDY }
[  226.653930] ata10: hard resetting link
[  227.146070] ata10: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
[  227.148833] ata10.00: configured for UDMA/133
[  227.148835] ata10.00: retrying FLUSH 0xea Emask 0x10
[  227.149049] ata10: EH complete



```

What I have done so far:
- Switched the SATA-Power-cable
- Switched the SATA-Data-Cable
- Repartitoned the drive using gparted (GPT partition table with one partition - just like the other drive)
- Switched SATA ports on the same controller
- Switched drive to a different controller

As mentioned earlier the two drives connected to the SATA controller are exactly the same (same model, firmware, partition table and partition) - one works smoothly the other one fires of the errors...

Help is much appreciated

Alex

EDIT: I connected the drive to one of the SATA 3 ports on the mainboard directly (Intel c226 chipset) - so far no errors. there seems to be a driver / incompatibility issue with the asmedia 1062 driver or hardware and two 8tb drives I guess...however this seems to be linux specific (no issues in win7)

---

