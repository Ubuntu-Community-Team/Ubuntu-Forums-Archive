---
title: "Problem with linux on USB memory stick"
date: 2006-09-15
forum: Hardware &amp; Laptops
---

### Post by emil.s on 2006-09-15
GRUB starts fine. But when the kernel loads it stop.
Dmesg says:
```

[17179572.272000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[17179572.288000] eth0: Tigon3 [partno(BCM95751) rev 4001 PHY(5750)] (PCI Express) 10/100/1000BaseT Ethernet 00:11:11:2a:31:a2
[17179572.288000] eth0: RXcsums[1] LinkChgREG[1] MIirq[1] ASF[0] Split[0] WireSpeed[1] TSOcap[1]
[17179572.288000] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[17179572.288000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[17179572.288000] ACPI: PCI Interrupt 0000:04:01.0[A] -> GSI 17 (level, low) -> IRQ 177
[17179572.292000] eth1: VIA Rhine III at 0x1cc00, 00:0f:3d:cd:9e:b3, IRQ 177.
[17179572.292000] eth1: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[17179572.296000] PPP generic driver version 2.4.2
[17179572.296000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179572.296000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179572.296000] GDT-HA: Storage RAID Controller Driver. Version: 3.04
[17179572.296000] GDT-HA: Found 0 PCI Storage RAID Controllers
[17179572.296000] libata version 1.20 loaded.
[17179572.296000] ata_piix 0000:00:1f.2: version 1.05
[17179572.296000] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[17179572.296000] ACPI: PCI Interrupt 0000:00:1f.2[C] -> GSI 20 (level, low) -> IRQ 217
[17179572.296000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179572.296000] ata1: SATA max UDMA/133 cmd 0x1F0 ctl 0x3F6 bmdma 0xFFA0 irq 14
[17179572.636000] ata1: dev 0 cfg 49:2f00 82:346b 83:7f01 84:4003 85:3469 86:3c01 87:4003 88:207f
[17179572.636000] ata1: dev 0 ATA-6, max UDMA/133, 312581808 sectors: LBA48
[17179572.648000] ata1: dev 0 configured for UDMA/133
[17179572.648000] scsi0 : ata_piix
[17179572.648000]   Vendor: ATA       Model: ST3160023AS       Rev: 8.05
[17179572.648000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179572.648000] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xFFA8 irq 15
[17179572.980000] ata2: dev 0 cfg 49:0b00 82:0000 83:0000 84:0000 85:0000 86:0000 87:0000 88:0407
[17179572.980000] ata2: dev 0 ATAPI, max UDMA/33
[17179573.152000] ata2: dev 1 cfg 49:0f00 82:0000 83:0000 84:4000 85:0000 86:0000 87:4000 88:0407
[17179573.152000] ata2: dev 1 ATAPI, max UDMA/33
[17179573.340000] ata2: dev 0 configured for UDMA/33
[17179573.512000] ata2: dev 1 configured for UDMA/33
[17179573.512000] scsi1 : ata_piix
[17179573.512000]   Vendor: _NEC      Model: DVD_RW ND-3500AG  Rev: 2.18
[17179573.512000]   Type:   CD-ROM                             ANSI SCSI revision: 05
[17179573.512000]   Vendor: HL-DT-ST  Model: RW/DVD GCC-4481B  Rev: E108
[17179573.516000]   Type:   CD-ROM                             ANSI SCSI revision: 05
[17179573.516000] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[17179573.516000] sda: Write Protect is off
[17179573.516000] sda: Mode Sense: 00 3a 00 00
[17179573.516000] SCSI device sda: drive cache: write back
[17179573.516000] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[17179573.516000] sda: Write Protect is off
[17179573.516000] sda: Mode Sense: 00 3a 00 00
[17179573.516000] SCSI device sda: drive cache: write back
[17179573.516000]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[17179573.536000] sd 0:0:0:0: Attached scsi disk sda
```

What will i have to do to get it work?

---

