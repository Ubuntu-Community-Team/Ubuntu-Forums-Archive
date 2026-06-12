---
title: "Cant see SATA drive (Edgy)"
date: 2007-11-11
forum: Hardware &amp; Laptops
---

### Post by narcan on 2007-11-11
I've got the following setup:

GA-G33-DS3R Motherboard
Intel Q6600 Processors

3 x IDE drives (2 via onboard IDE, 1 via PCI IDE Card)
1 x 500 Gig Samsung SATA drive

Ubuntu (Edgy) is installed on one of the IDE drives.

All drives can be seen apart from my new SATA drive.

I've tried changing the BIOS settings for SATA to both IDE mode for SATA and AHCI.

In both cases I can't see to see the drive under /dev , or /dev/disk.

This is what I see in /var/log/messages

Nov 11 17:26:30 tvbox kernel: [17179572.348000] SCSI subsystem initialized
Nov 11 17:26:30 tvbox kernel: [17179572.352000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 19 (level, low) -> IRQ 177
Nov 11 17:26:30 tvbox kernel: [17179576.556000] ahci 0000:02:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
Nov 11 17:26:30 tvbox kernel: [17179576.556000] ahci 0000:02:00.0: flags: 64bit ncq pm led clo pmp pio slum part
Nov 11 17:26:30 tvbox kernel: [17179576.556000] ata1: SATA max UDMA/133 cmd 0xF883C100 ctl 0x0 bmdma 0x0 irq 177
Nov 11 17:26:30 tvbox kernel: [17179576.556000] ata2: SATA max UDMA/133 cmd 0xF883C180 ctl 0x0 bmdma 0x0 irq 177
Nov 11 17:26:30 tvbox kernel: [17179577.476000] ata1: SATA link down (SStatus 0)
Nov 11 17:26:30 tvbox kernel: [17179577.476000] scsi0 : ahci
Nov 11 17:26:30 tvbox kernel: [17179578.396000] ata2: SATA link down (SStatus 0) 
Nov 11 17:26:30 tvbox kernel: [17179578.396000] scsi1 : ahci

I was able to see and format the drive under windows using an external encolsure so the drive looks to be working fine (and it's recognised correctly in the BIOS).

Any ideas on where to start trying to solve this issue ?

---

