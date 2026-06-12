---
title: "Slow DVD Burning with Intrepid/Jaunty"
date: 2009-05-26
forum: Hardware
---

### Post by IAmZim on 2009-05-26
hi,
maybe you can help me with this:
my DVD-Drive (Sony and LG with several disks tested) burns with a maximum of 1.2x.
I had no problems in gentoo or XP in dualboot.

this is my dmesg:
```
 dmesg | grep ata
[    0.000000]  BIOS-e820: 000000007fff3000 - 0000000080000000 (ACPI data)
[    0.000000]  modified: 000000007fff3000 - 0000000080000000 (ACPI data)
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 -
 0000001000]
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.004000] Memory: 2052852k/2097088k available (4110k kernel code, 42864k re
served, 2197k data, 532k init, 1191880k highmem)
[    0.004000]       .data : 0xc05039df - 0xc0728e60   (2197 kB)
[    0.571959] libata version 3.00 loaded.
[    1.697483] sata_uli 0000:00:0e.1: version 1.3
[    1.697502] sata_uli 0000:00:0e.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.697662] scsi0 : sata_uli
[    1.697770] scsi1 : sata_uli
[    1.697814] ata1: SATA max UDMA/133 cmd 0xd400 ctl 0xd800 bmdma 0xe400 irq 19
[    1.697817] ata2: SATA max UDMA/133 cmd 0xdc00 ctl 0xe000 bmdma 0xe408 irq 19
[    2.164032] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.192120] ata1.00: HPA unlocked: 312579695 -> 312581808, native 312581808
[    2.192125] ata1.00: ATA-7: Maxtor 6V160E0, VA111630, max UDMA/133
[    2.192128] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.209306] ata1.00: configured for UDMA/133
[    2.676029] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.684207] ata2.00: ATA-7: SAMSUNG HD250HJ, FH100-06, max UDMA7
[    2.684209] ata2.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.692229] ata2.00: configured for UDMA/133
[    2.733086] pata_ali 0000:00:0e.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.733246] scsi2 : pata_ali
[    2.733307] scsi3 : pata_ali
[    2.733851] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    2.733854] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    2.896274] ata3.00: ATAPI: HL-DT-ST DVDRAM GSA-H42N, RL00, max UDMA/66
[    2.896296] ata3.00: WARNING: ATAPI DMA disabled for reliablity issues.  It c
an be enabled
[    2.896298] ata3.00: WARNING: via pata_ali.atapi_dma modparam or correspondin
g sysfs node.
[    2.912219] ata3.00: configured for UDMA/66
[    3.286169] Write protecting the kernel read-only data: 1524k

```

i tried to change the  /sys/module/pata_ali/parameters/atapi_dma to 1 but this didn't work.every reboot it's changed back to 0. i tried some grub options too but again no luck.
How can i use my drive with an acceptable speed?

sincerely,
IAmZim

---

