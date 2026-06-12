---
title: "Edgy boot time issue ~ SATA2 related?"
date: 2006-12-17
forum: Hardware &amp; Laptops
---

### Post by Ecthelion on 2006-12-17
Hi,

This is a follow-up of [this thread]("http://ubuntuforums.org/showthread.php?t=291525").
Since I discovered there that this issue was probably hardware related I tough I would have more help here.

Short summary of the problem:

I get boot times from up to 3 minutes due to a (I think) driver/hardware problem.
When my pc starts up it needs 2/2.5 minutes to mount my root file system (which is a SATA2).
I didn't had that problem when I used Dapper.

I tracked the problem in my logs and found this:
> Dec 17 08:10:20 ElvenLounge kernel: [17179576.152000] SCSI subsystem initialized
Dec 17 08:10:20 ElvenLounge kernel: [17179576.156000] PCI: Enabling device 0000:00:16.1 (0105 -> 0107)
Dec 17 08:10:20 ElvenLounge kernel: [17179576.156000] ACPI: PCI Interrupt 0000:00:16.1[A] -> GSI 21 (level, low) -> IRQ 66
Dec 17 08:10:20 ElvenLounge kernel: [17179581.976000] ahci 0000:00:16.1: AHCI 0001.0000 32 slots 4 ports 3 Gbps 0xf impl RAID mode
Dec 17 08:10:20 ElvenLounge kernel: [17179581.976000] ahci 0000:00:16.1: flags: ncq ilck pm led clo pmp pio slum part 
Dec 17 08:10:20 ElvenLounge kernel: [17179581.976000] ata1: SATA max UDMA/133 cmd 0xF882E900 ctl 0x0 bmdma 0x0 irq 66
Dec 17 08:10:20 ElvenLounge kernel: [17179581.976000] ata2: SATA max UDMA/133 cmd 0xF882E980 ctl 0x0 bmdma 0x0 irq 66
Dec 17 08:10:20 ElvenLounge kernel: [17179581.976000] ata3: SATA max UDMA/133 cmd 0xF882EA00 ctl 0x0 bmdma 0x0 irq 66
Dec 17 08:10:20 ElvenLounge kernel: [17179581.976000] ata4: SATA max UDMA/133 cmd 0xF882EA80 ctl 0x0 bmdma 0x0 irq 66
Dec 17 08:10:20 ElvenLounge kernel: [17179582.896000] ata1: SATA link down (SStatus 0)
Dec 17 08:10:20 ElvenLounge kernel: [17179612.916000] ata1: qc timeout (cmd 0xec)
Dec 17 08:10:20 ElvenLounge kernel: [17179612.916000] ata1: dev 0 failed to IDENTIFY (I/O error)
Dec 17 08:10:20 ElvenLounge kernel: [17179612.916000] scsi0 : ahci
Dec 17 08:10:20 ElvenLounge kernel: [17179613.836000] ata2: SATA link down (SStatus 0)
Dec 17 08:10:20 ElvenLounge kernel: [17179643.856000] ata2: qc timeout (cmd 0xec)
Dec 17 08:10:20 ElvenLounge kernel: [17179643.856000] ata2: dev 0 failed to IDENTIFY (I/O error)
Dec 17 08:10:20 ElvenLounge kernel: [17179643.856000] scsi1 : ahci
Dec 17 08:10:20 ElvenLounge kernel: [17179644.776000] ata3: SATA link down (SStatus 0)
Dec 17 08:10:20 ElvenLounge kernel: [17179674.796000] ata3: qc timeout (cmd 0xec)
Dec 17 08:10:20 ElvenLounge kernel: [17179674.796000] ata3: dev 0 failed to IDENTIFY (I/O error)
Dec 17 08:10:20 ElvenLounge kernel: [17179674.796000] scsi2 : ahci
Dec 17 08:10:20 ElvenLounge kernel: [17179675.172000] ata4: SATA link up 3.0 Gbps (SStatus 123)
Dec 17 08:10:20 ElvenLounge kernel: [17179675.172000] ata4: dev 0 ATA-7, max UDMA/133, 488397168 sectors: LBA48
Dec 17 08:10:20 ElvenLounge kernel: [17179675.172000] ata4: dev 0 configured for UDMA/133

I think it are those "SATA link down" and their timeouts that make a boot take so much time.

Is there anyone who knows of this problem, or anyone that has any advice?
A better SATA2 driver maybe?

Any suggestion is welcome

---

### Post by Ecthelion on 2006-12-20
Nevermind, there has been a kernel update and since then the problem is gone.

Good work developers!

---

