---
title: "VERY slow boot with hot-plug SATAs"
date: 2013-05-14
forum: Hardware
---

### Post by gamez on 2013-05-14
Dear community,

whenever I boot with one or two of my Samsung HD204UI inserted in my hot-swap bays, boot-up is seriously delayed.

dmesg reports
```

[   12.542694] ...some message here...
[   12.959071] ata8: link is slow to respond, please be patient (ready=-19)
[   17.494686] ata8: SRST failed (errno=-16)
[   17.494785] ata6: exception Emask 0x10 SAct 0x0 SErr 0x10000 action 0xe frozen
[   17.494787] ata6: irq_stat 0x00400000, PHY RDY changed
[   17.494789] ata6: SError: { PHYRdyChg }
[   17.494791] ata6: hard resetting link
[   18.216995] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)

```
and then again
```

[   18.229503] ata6.00: configured for UDMA/133
[   18.229508] ata6: EH complete
[   22.994348] ata8: link is slow to respond, please be patient (ready=-19)
[   27.528947] ata8: SRST failed (errno=-16)
[   27.529050] ata6: exception Emask 0x10 SAct 0x0 SErr 0x10000 action 0xe frozen
[   27.529054] ata6: irq_stat 0x00400000, PHY RDY changed
[   27.529057] ata6: SError: { PHYRdyChg }
[   27.529062] ata6: hard resetting link
[   28.252251] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   28.258338] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20121018/psargs-359)
[   28.258353] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT5._GTF] (Node ffff88040c4821b8), AE_NOT_FOUND (20121018/psparse-537)
[   28.264671] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20121018/psargs-359)
[   28.264687] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT5._GTF] (Node ffff88040c4821b8), AE_NOT_FOUND (20121018/psparse-537)
[   28.264801] ata6.00: configured for UDMA/133
[   28.264806] ata6: EH complete
[   33.028607] ata8: link is slow to respond, please be patient (ready=-19)
[   38.384308] device-mapper: uevent: version 1.0.3

```

So some 25 secs are passing by while recognizing and setting up the SATA HDD(s).

W/o the disk(s), boot is performed significantly faster.

I have a MSI P67A-C43 (B3) motherboard, and upgraded the BIOS recently to v1.J (2012-08-01), and I'm not sure if this was happening before. The BIOS configuration for SATA devices has AHCI activated, with the bays in question being set to hot swappable. Changing to hot-swappable disabled doesn't improve the behaviour.

Is this some kind of known kernel error, and is there a fix, or is something wrong with the disk? I do not notice anything abnormal when using the disks later on after the slow boot.

Thanks in advance for any advice you may have.

Best regards,

g.

---

### Post by gamez on 2013-06-02
Resolved; was a cabling / connectivity / power supply problem.

g.

---

