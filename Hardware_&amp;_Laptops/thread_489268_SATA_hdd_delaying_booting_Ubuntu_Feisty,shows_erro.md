---
title: "SATA hdd delaying booting Ubuntu Feisty,shows errors too"
date: 2007-07-01
forum: Hardware &amp; Laptops
---

### Post by deepclutch on 2007-07-01
I got ubuntu feisty installed on an asus via based board.now the board went kaput and i am using a gigabyte intel 915GV board.I know that some differences exists.
i chrooted into feisty installation from livecd and dpkg-reconfigure linux-image-2.6.20.xx .it went fine and i can boot into Ubuntu Feisty.
but it takes around 5-6 minutes to boot in as some sata errors are shown.after these error exercise, though ubuntu boots.
below is the specific error parts from /var/log/messages
> 
un 24 12:53:48 ubuntu kernel: [   19.938386] SCSI subsystem initialized
Jun 24 12:53:48 ubuntu kernel: [   19.945742] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 19
Jun 24 12:53:48 ubuntu kernel: [   19.945910] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001f000 irq 14
Jun 24 12:53:48 ubuntu kernel: [   19.946011] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001f008 irq 15
Jun 24 12:53:48 ubuntu kernel: [   19.946099] scsi0 : ata_piix
Jun 24 12:53:48 ubuntu kernel: [   20.596613] ata1.00: ATAPI, max UDMA/33
Jun 24 12:53:48 ubuntu kernel: [   20.596672] ata1.01: ATAPI, max UDMA/33
Jun 24 12:53:48 ubuntu kernel: [   20.760350] ata1.00: configured for UDMA/33
Jun 24 12:53:48 ubuntu kernel: [   50.712163] ata1.01: qc timeout (cmd 0xef)
Jun 24 12:53:48 ubuntu kernel: [   50.712283] ata1: failed to recover some devices, retrying in 5 secs
Jun 24 12:53:48 ubuntu kernel: [   56.523082] ata1.00: configured for UDMA/33
Jun 24 12:53:48 ubuntu kernel: [   86.474891] ata1.01: qc timeout (cmd 0xef)
Jun 24 12:53:48 ubuntu kernel: [   86.475011] ata1.01: limiting speed to UDMA/33:PIO3
Jun 24 12:53:48 ubuntu kernel: [   86.475066] ata1: failed to recover some devices, retrying in 5 secs
Jun 24 12:53:48 ubuntu kernel: [   92.285815] ata1.00: configured for UDMA/33
Jun 24 12:53:48 ubuntu kernel: [  122.237623] ata1.01: qc timeout (cmd 0xef)
Jun 24 12:53:48 ubuntu kernel: [  122.237742] ata1.01: disabled
Jun 24 12:53:48 ubuntu kernel: [  122.237795] ata1: failed to recover some devices, retrying in 5 secs
Jun 24 12:53:48 ubuntu kernel: [  127.233683] ata1: failed to recover some devices, retrying in 5 secs
Jun 24 12:53:48 ubuntu kernel: [  132.880809] ata1.00: configured for UDMA/33
Jun 24 12:53:48 ubuntu kernel: [  132.880874] scsi1 : ata_piix
Jun 24 12:53:48 ubuntu kernel: [  133.046483] ATA: abnormal status 0x7F on port 0x00010177
Jun 24 12:53:48 ubuntu kernel: [  133.047422] scsi 0:0:0:0: CD-ROM            TSSTcorp CD/DVDW SH-S182F SB02 PQ: 0 ANSI: 5
Jun 24 12:53:48 ubuntu kernel: [  133.048018] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
Jun 24 12:53:48 ubuntu kernel: [  133.048275] ACPI: PCI Interrupt 0000:00:1f.2[b] -> GSI 19 (level, low) -> IRQ 18
Jun 24 12:53:48 ubuntu kernel: [  133.048439] ata3: SATA max UDMA/133 cmd 0x0001d000 ctl 0x0001d402 bmdma 0x0001e000 irq 18
Jun 24 12:53:48 ubuntu kernel: [  133.048533] ata4: SATA max UDMA/133 cmd 0x0001d800 ctl 0x0001dc02 bmdma 0x0001e008 irq 18
Jun 24 12:53:48 ubuntu kernel: [  133.048613] scsi2 : ata_piix
Jun 24 12:53:48 ubuntu kernel: [  133.324256] ata3.00: ata_hpa_resize 1: sectors = 156299375, hpa_sectors = 156301488
Jun 24 12:53:48 ubuntu kernel: [  133.324331] ata3.00: Host Protected Area detected.
Jun 24 12:53:48 ubuntu kernel: [  133.324332]      current size : 156299375 sectors (80025 MB)
Jun 24 12:53:48 ubuntu kernel: [  133.324334]      native  size : 156301488 sectors (80026 MB)
Jun 24 12:53:48 ubuntu kernel: [  133.332018] ata3.00: Native size increased to 156301488 sectors
Jun 24 12:53:48 ubuntu kernel: [  133.332077] ata3.00: ATA-6: ST380013AS, 3.18, max UDMA/133
Jun 24 12:53:48 ubuntu kernel: [  133.332134] ata3.00: 156301488 sectors, multi 16: LBA48 
Jun 24 12:53:48 ubuntu kernel: [  133.340223] ata3.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
Jun 24 12:53:48 ubuntu kernel: [  133.340295] ata3.00: configured for UDMA/133
Jun 24 12:53:48 ubuntu kernel: [  133.340354] scsi3 : ata_piix
Jun 24 12:53:48 ubuntu kernel: [  133.505728] ATA: abnormal status 0x7F on port 0x0001d807
Jun 24 12:53:48 ubuntu kernel: [  133.505883] scsi 2:0:0:0: Direct-Access     ATA      ST380013AS       3.18 PQ: 0 ANSI: 5
Jun 24 12:53:48 ubuntu kernel: [  133.532247] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Jun 24 12:53:48 ubuntu kernel: [  133.532326] Uniform CD-ROM driver Revision: 3.20
Jun 24 12:53:48 ubuntu kernel: [  133.535999] sr 0:0:0:0: Attached scsi generic sg0 type 5
Jun 24 12:53:48 ubuntu kernel: [  133.536077] scsi 2:0:0:0: Attached scsi generic sg1 type 0
Jun 24 12:53:48 ubuntu kernel: [  133.541694] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
Jun 24 12:53:48 ubuntu kernel: [  133.541769] sda: Write Protect is off
Jun 24 12:53:48 ubuntu kernel: [  133.541840] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 24 12:53:48 ubuntu kernel: [  133.541967] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
Jun 24 12:53:48 ubuntu kernel: [  133.542033] sda: Write Protect is off
Jun 24 12:53:48 ubuntu kernel: [  133.542102] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 24 12:53:48 ubuntu kernel: [  133.542176]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 sda10 sda11 sda12 sda13 sda14 >
Jun 24 12:53:48 ubuntu kernel: [  133.651593] sd 2:0:0:0: Attached scsi disk sda
Mine is a sata seagate ST380013AS 80GB hdd.
also i got a debian Sid install which works OK.though debian sid logs show:
> 
Jun 30 23:04:56 jaguar kernel: PCI: Setting latency timer of device 0000:00:1f.2 to 64
Jun 30 23:04:56 jaguar kernel: ata1: SATA max UDMA/133 cmd 0x0001d000 ctl 0x0001d402 bmdma 0x0001e000 irq 18
Jun 30 23:04:56 jaguar kernel: ata2: SATA max UDMA/133 cmd 0x0001d800 ctl 0x0001dc02 bmdma 0x0001e008 irq 18
Jun 30 23:04:56 jaguar kernel: scsi0 : ata_piix
Jun 30 23:04:56 jaguar kernel: ata1.00: ATA-6: ST380013AS, 3.18, max UDMA/133
Jun 30 23:04:56 jaguar kernel: ata1.00: 156299375 sectors, multi 16: LBA48 
Jun 30 23:04:56 jaguar kernel: ata1.00: configured for UDMA/133
Jun 30 23:04:56 jaguar kernel: scsi1 : ata_piix
Jun 30 23:04:56 jaguar kernel: ATA: abnormal status 0x7F on port 0x0001d807
Jun 30 23:04:56 jaguar kernel: scsi 0:0:0:0: Direct-Access     ATA      ST380013AS       3.18 PQ: 0 ANSI: 5
Jun 30 23:04:56 jaguar kernel: ICH6: IDE controller at PCI slot 0000:00:1f.1
Jun 30 23:04:56 jaguar kernel: ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 19
Jun 30 23:04:56 jaguar kernel: ICH6: chipset revision 4
Jun 30 23:04:56 jaguar kernel: ICH6: not 100%% native mode: will probe irqs later
Jun 30 23:04:56 jaguar kernel:     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
Jun 30 23:04:56 jaguar kernel:     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:pio, hdd:pio
Jun 30 23:04:56 jaguar kernel: Probing IDE interface ide0...
Jun 30 23:04:56 jaguar kernel: SCSI device sda: 156299375 512-byte hdwr sectors (80025 MB)
Jun 30 23:04:56 jaguar kernel: sda: Write Protect is off
Jun 30 23:04:56 jaguar kernel: sda: Mode Sense: 00 3a 00 00
Jun 30 23:04:56 jaguar kernel: SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 30 23:04:56 jaguar kernel: SCSI device sda: 156299375 512-byte hdwr sectors (80025 MB)
Jun 30 23:04:56 jaguar kernel: sda: Write Protect is off
Jun 30 23:04:56 jaguar kernel: sda: Mode Sense: 00 3a 00 00
Jun 30 23:04:56 jaguar kernel: SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 30 23:04:56 jaguar kernel:  sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 sda10 sda11 sda12 sda13 sda14 >
Jun 30 23:04:56 jaguar kernel: sd 0:0:0:0: Attached scsi disk sda
although debian does not delay while booting.

how can i resolve this.is there anything wrong with hdd?
help is appreciated thank you.

---

### Post by deepclutch on 2007-07-01
I forgot to tell that i didnt reinstalled Debian and Ubuntu but just reconfigured hoping for the best after changing the mobo from VIA to intel one.thx

---

### Post by deepclutch on 2007-07-01
I have already tried "irqpoll" "irqfixup" etc.it works fine then.
but then my CD writer and DVD writers are detected as scsi(i know with new kernel,libata) and dma is not working with them :(
> Jul  1 15:49:40 ubuntu kernel: [   22.125601] SCSI subsystem initialized
Jul  1 15:49:40 ubuntu kernel: [   22.131477] libata version 2.20 loaded.
Jul  1 15:49:40 ubuntu kernel: [   22.133092] ata_piix 0000:00:1f.1: version 2.10ac1
Jul  1 15:49:40 ubuntu kernel: [   22.133109] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 19
Jul  1 15:49:40 ubuntu kernel: [   22.133233] PCI: Setting latency timer of device 0000:00:1f.1 to 64
Jul  1 15:49:40 ubuntu kernel: [   22.133275] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001f000 irq 14
Jul  1 15:49:40 ubuntu kernel: [   22.133377] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001f008 irq 15
Jul  1 15:49:40 ubuntu kernel: [   22.133465] scsi0 : ata_piix
Jul  1 15:49:40 ubuntu kernel: [   22.782185] ata1.00: ATAPI, max UDMA/33
Jul  1 15:49:40 ubuntu kernel: [   22.782245] ata1.01: ATAPI, max UDMA/33
Jul  1 15:49:40 ubuntu kernel: [   22.945922] ata1.00: configured for UDMA/33
Jul  1 15:49:40 ubuntu kernel: [   23.109660] ata1.01: configured for UDMA/33
Jul  1 15:49:40 ubuntu kernel: [   23.109725] scsi1 : ata_piix
Jul  1 15:49:40 ubuntu kernel: [   23.275335] ATA: abnormal status 0x7F on port 0x00010177
Jul  1 15:49:40 ubuntu kernel: [   23.276321] scsi 0:0:0:0: CD-ROM            TSSTcorp CD/DVDW SH-S182F SB02 PQ: 0 ANSI: 5
Jul  1 15:49:40 ubuntu kernel: [   23.281261] scsi 0:0:1:0: CD-ROM            SONY     CD-RW  CRX210E1  2YS2 PQ: 0 ANSI: 5
Jul  1 15:49:40 ubuntu kernel: [   23.281820] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
Jul  1 15:49:40 ubuntu kernel: [   23.282075] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 18
Jul  1 15:49:40 ubuntu kernel: [   23.282198] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Jul  1 15:49:40 ubuntu kernel: [   23.282229] ata3: SATA max UDMA/133 cmd 0x0001d000 ctl 0x0001d402 bmdma 0x0001e000 irq 18
Jul  1 15:49:40 ubuntu kernel: [   23.282323] ata4: SATA max UDMA/133 cmd 0x0001d800 ctl 0x0001dc02 bmdma 0x0001e008 irq 18
Jul  1 15:49:40 ubuntu kernel: [   23.282402] scsi2 : ata_piix
Jul  1 15:49:40 ubuntu kernel: [   23.557098] ata3.00: ata_hpa_resize 1: sectors = 156299375, hpa_sectors = 156301488
Jul  1 15:49:40 ubuntu kernel: [   23.557173] ata3.00: Host Protected Area detected.
Jul  1 15:49:40 ubuntu kernel: [   23.557175]      current size : 156299375 sectors (80025 MB)
Jul  1 15:49:40 ubuntu kernel: [   23.557176]      native  size : 156301488 sectors (80026 MB)
Jul  1 15:49:40 ubuntu kernel: [   23.564860] ata3.00: Native size increased to 156301488 sectors
Jul  1 15:49:40 ubuntu kernel: [   23.564919] ata3.00: ATA-6: ST380013AS, 3.18, max UDMA/133
Jul  1 15:49:40 ubuntu kernel: [   23.564976] ata3.00: 156301488 sectors, multi 16: LBA48 
Jul  1 15:49:40 ubuntu kernel: [   23.573083] ata3.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
Jul  1 15:49:40 ubuntu kernel: [   23.573155] ata3.00: configured for UDMA/133
Jul  1 15:49:40 ubuntu kernel: [   23.573214] scsi3 : ata_piix
Jul  1 15:49:40 ubuntu kernel: [   23.738571] ATA: abnormal status 0x7F on port 0x0001d807
Jul  1 15:49:40 ubuntu kernel: [   23.738747] scsi 2:0:0:0: Direct-Access     ATA      ST380013AS       3.18 PQ: 0 ANSI: 5
Jul  1 15:49:40 ubuntu kernel: [   23.743215] 8139cp 0000:02:05.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
Jul  1 15:49:40 ubuntu kernel: [   23.743292] 8139cp 0000:02:05.0: Try the "8139too" driver instead.
Jul  1 15:49:40 ubuntu kernel: [   23.745116] 8139too Fast Ethernet driver 0.9.28
Jul  1 15:49:40 ubuntu kernel: [   23.745403] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 21 (level, low) -> IRQ 20
Jul  1 15:49:40 ubuntu kernel: [   23.745963] eth0: RealTek RTL8139 at 0xd0830000, 00:14:85:98:be:a2, IRQ 20
Jul  1 15:49:40 ubuntu kernel: [   23.746023] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
Jul  1 15:49:40 ubuntu kernel: [   23.771082] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Jul  1 15:49:40 ubuntu kernel: [   23.771161] Uniform CD-ROM driver Revision: 3.20
Jul  1 15:49:40 ubuntu kernel: [   23.771265] sr 0:0:0:0: Attached scsi CD-ROM sr0
Jul  1 15:49:40 ubuntu kernel: [   23.844453] sr1: scsi3-mmc drive: 152x/52x writer cd/rw xa/form2 cdda tray
Jul  1 15:49:40 ubuntu kernel: [   23.844552] sr 0:0:1:0: Attached scsi CD-ROM sr1
Jul  1 15:49:40 ubuntu kernel: [   23.848099] sr 0:0:0:0: Attached scsi generic sg0 type 5
Jul  1 15:49:40 ubuntu kernel: [   23.848178] sr 0:0:1:0: Attached scsi generic sg1 type 5
Jul  1 15:49:40 ubuntu kernel: [   23.848302] scsi 2:0:0:0: Attached scsi generic sg2 type 0
Jul  1 15:49:40 ubuntu kernel: [   23.858787] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
Jul  1 15:49:40 ubuntu kernel: [   23.858861] sda: Write Protect is off
Jul  1 15:49:40 ubuntu kernel: [   23.858916] sda: Mode Sense: 00 3a 00 00
Jul  1 15:49:40 ubuntu kernel: [   23.858932] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul  1 15:49:40 ubuntu kernel: [   23.859052] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
Jul  1 15:49:40 ubuntu kernel: [   23.859118] sda: Write Protect is off
Jul  1 15:49:40 ubuntu kernel: [   23.859172] sda: Mode Sense: 00 3a 00 00
Jul  1 15:49:40 ubuntu kernel: [   23.859187] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul  1 15:49:40 ubuntu kernel: [   23.859262]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 sda10 sda11 sda12 sda13 sda14 >
Jul  1 15:49:40 ubuntu kernel: [   23.960416] sd 2:0:0:0: Attached scsi disk sda
so the error is there i think :( any other ways!

---

### Post by deepclutch on 2007-07-01
Bum**pp**

---

### Post by deepclutch on 2007-07-01
so what shud i try?do i  need to modprobe piix and rmmod ata-piix :?

---

