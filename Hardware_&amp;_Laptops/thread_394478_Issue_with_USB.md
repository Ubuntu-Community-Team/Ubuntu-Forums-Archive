---
title: "Issue with USB"
date: 2007-03-27
forum: Hardware &amp; Laptops
---

### Post by nick_karstedt on 2007-03-27
Well it all started when I was trying to connect my ipod.  Tried using disk mode and it always said ok to disconnect (Sounds like a usb host issue....).  Ran lsusb... nothing as expected.  Then ran a Dmesg and found something.... interesting.  Here's the whole thing:

```
[   18.918719] nv_sata: Primary device added
[   18.918720] nv_sata: Primary device removed
[   18.918721] nv_sata: Secondary device added
[   18.918722] nv_sata: Secondary device removed
[   18.922718] nv_sata: Primary device added
[   18.922719] nv_sata: Primary device removed
[   18.922721] nv_sata: Secondary device added
[   18.922722] nv_sata: Secondary device removed
[   18.926718] nv_sata: Primary device added
[   18.926719] nv_sata: Primary device removed
[   18.926720] nv_sata: Secondary device added
[   18.926721] nv_sata: Secondary device removed
[   18.930717] nv_sata: Primary device added
[   18.930719] nv_sata: Primary device removed
[   18.930720] nv_sata: Secondary device added
[   18.930721] nv_sata: Secondary device removed
[   18.934717] nv_sata: Primary device added
[   18.934718] nv_sata: Primary device removed
[   18.934720] nv_sata: Secondary device added
[   18.934721] nv_sata: Secondary device removed
[   18.938717] nv_sata: Primary device added
[   18.938718] nv_sata: Primary device removed
[   18.938719] nv_sata: Secondary device added
[   18.938720] nv_sata: Secondary device removed
[   18.942716] nv_sata: Primary device added
[   18.942718] nv_sata: Primary device removed
[   18.942719] nv_sata: Secondary device added
[   18.942720] nv_sata: Secondary device removed
[   18.946716] nv_sata: Primary device added
[   18.946717] nv_sata: Primary device removed
[   18.946718] nv_sata: Secondary device added
[   18.946720] nv_sata: Secondary device removed
[   18.950716] nv_sata: Primary device added
[   18.950717] nv_sata: Primary device removed
[   18.950718] nv_sata: Secondary device added
[   18.950719] nv_sata: Secondary device removed
[   18.954715] nv_sata: Primary device added
[   18.954716] nv_sata: Primary device removed
[   18.954718] nv_sata: Secondary device added
[   18.954719] nv_sata: Secondary device removed
[   18.958715] nv_sata: Primary device added
[   18.958716] nv_sata: Primary device removed
[   18.958717] nv_sata: Secondary device added
[   18.958719] nv_sata: Secondary device removed
[   18.962714] nv_sata: Primary device added
[   18.962716] nv_sata: Primary device removed
[   18.962717] nv_sata: Secondary device added
[   18.962718] nv_sata: Secondary device removed
[   18.966714] nv_sata: Primary device added
[   18.966715] nv_sata: Primary device removed
[   18.966716] nv_sata: Secondary device added
[   18.966718] nv_sata: Secondary device removed
[   18.970714] nv_sata: Primary device added
[   18.970715] nv_sata: Primary device removed
[   18.970716] nv_sata: Secondary device added
[   18.970717] nv_sata: Secondary device removed
[   18.974713] nv_sata: Primary device added
[   18.974715] nv_sata: Primary device removed
[   18.974716] nv_sata: Secondary device added
[   18.974717] nv_sata: Secondary device removed
[   18.978713] nv_sata: Primary device added
[   18.978714] nv_sata: Primary device removed
[   18.978715] nv_sata: Secondary device added
[   18.978717] nv_sata: Secondary device removed
[   18.982713] nv_sata: Primary device added
[   18.982714] nv_sata: Primary device removed
[   18.982715] nv_sata: Secondary device added
[   18.982716] nv_sata: Secondary device removed
[   18.986712] nv_sata: Primary device added
[   18.986713] nv_sata: Primary device removed
[   18.986715] nv_sata: Secondary device added
[   18.986716] nv_sata: Secondary device removed
[   18.990712] nv_sata: Primary device added
[   18.990713] nv_sata: Primary device removed
[   18.990714] nv_sata: Secondary device added
[   18.990716] nv_sata: Secondary device removed
[   18.994712] nv_sata: Primary device added
[   18.994713] nv_sata: Primary device removed
[   18.994714] nv_sata: Secondary device added
[   18.994715] nv_sata: Secondary device removed
[   18.998711] nv_sata: Primary device added
[   18.998713] nv_sata: Primary device removed
[   18.998714] nv_sata: Secondary device added
[   18.998715] nv_sata: Secondary device removed
[   19.002711] nv_sata: Primary device added
[   19.002712] nv_sata: Primary device removed
[   19.002713] nv_sata: Secondary device added
[   19.002715] nv_sata: Secondary device removed
[   19.006710] nv_sata: Primary device added
[   19.006712] nv_sata: Primary device removed
[   19.006713] nv_sata: Secondary device added
[   19.006714] nv_sata: Secondary device removed
[   19.010710] nv_sata: Primary device added
[   19.010711] nv_sata: Primary device removed
[   19.010712] nv_sata: Secondary device added
[   19.010714] nv_sata: Secondary device removed
[   19.014710] nv_sata: Primary device added
[   19.014711] nv_sata: Primary device removed
[   19.014712] nv_sata: Secondary device added
[   19.014713] nv_sata: Secondary device removed
[   19.018709] nv_sata: Primary device added
[   19.018711] nv_sata: Primary device removed
[   19.018712] nv_sata: Secondary device added
[   19.018713] nv_sata: Secondary device removed
[   19.022709] nv_sata: Primary device added
[   19.022710] nv_sata: Primary device removed
[   19.022711] nv_sata: Secondary device added
[   19.022713] nv_sata: Secondary device removed
[   19.026709] nv_sata: Primary device added
[   19.026710] nv_sata: Primary device removed
[   19.026711] nv_sata: Secondary device added
[   19.026712] nv_sata: Secondary device removed
[   19.030708] nv_sata: Primary device added
[   19.030709] nv_sata: Primary device removed
[   19.030711] nv_sata: Secondary device added
[   19.030712] nv_sata: Secondary device removed
[   19.034708] nv_sata: Primary device added
[   19.034709] nv_sata: Primary device removed
[   19.034710] nv_sata: Secondary device added
[   19.034711] nv_sata: Secondary device removed
[   19.038707] nv_sata: Primary device added
[   19.038709] nv_sata: Primary device removed
[   19.038710] nv_sata: Secondary device added
[   19.038711] nv_sata: Secondary device removed
[   19.042707] nv_sata: Primary device added
[   19.042708] nv_sata: Primary device removed
[   19.042709] nv_sata: Secondary device added
[   19.042711] nv_sata: Secondary device removed
[   19.046707] nv_sata: Primary device added
[   19.046708] nv_sata: Primary device removed
[   19.046709] nv_sata: Secondary device added
[   19.046710] nv_sata: Secondary device removed
[   19.050706] nv_sata: Primary device added
[   19.050707] nv_sata: Primary device removed
[   19.050709] nv_sata: Secondary device added
[   19.050710] nv_sata: Secondary device removed
[   19.054706] nv_sata: Primary device added
[   19.054707] nv_sata: Primary device removed
[   19.054709] nv_sata: Secondary device added
[   19.054710] nv_sata: Secondary device removed
[   19.058706] nv_sata: Primary device added
[   19.058707] nv_sata: Primary device removed
[   19.058708] nv_sata: Secondary device added
[   19.058709] nv_sata: Secondary device removed
[   19.062705] nv_sata: Primary device added
[   19.062707] nv_sata: Primary device removed
[   19.062708] nv_sata: Secondary device added
[   19.062709] nv_sata: Secondary device removed
[   19.066705] nv_sata: Primary device added
[   19.066706] nv_sata: Primary device removed
[   19.066707] nv_sata: Secondary device added
[   19.066709] nv_sata: Secondary device removed
[   19.070705] nv_sata: Primary device added
[   19.070706] nv_sata: Primary device removed
[   19.070707] nv_sata: Secondary device added
[   19.070708] nv_sata: Secondary device removed
[   19.074704] nv_sata: Primary device added
[   19.074705] nv_sata: Primary device removed
[   19.074706] nv_sata: Secondary device added
[   19.074708] nv_sata: Secondary device removed
[   19.078704] nv_sata: Primary device added
[   19.078705] nv_sata: Primary device removed
[   19.078706] nv_sata: Secondary device added
[   19.078707] nv_sata: Secondary device removed
[   19.082703] nv_sata: Primary device added
[   19.082705] nv_sata: Primary device removed
[   19.082706] nv_sata: Secondary device added
[   19.082707] nv_sata: Secondary device removed
[   19.086703] nv_sata: Primary device added
[   19.086704] nv_sata: Primary device removed
[   19.086705] nv_sata: Secondary device added
[   19.086707] nv_sata: Secondary device removed
[   19.090703] nv_sata: Primary device added
[   19.090704] nv_sata: Primary device removed
[   19.090705] nv_sata: Secondary device added
[   19.090706] nv_sata: Secondary device removed
[   19.094702] nv_sata: Primary device added
[   19.094703] nv_sata: Primary device removed
[   19.094705] nv_sata: Secondary device added
[   19.094706] nv_sata: Secondary device removed
[   19.098702] nv_sata: Primary device added
[   19.098703] nv_sata: Primary device removed
[   19.098704] nv_sata: Secondary device added
[   19.098705] nv_sata: Secondary device removed
[   19.102683] ata4: SATA link up 1.5 Gbps (SStatus 113)
[   19.102702] nv_sata: Primary device added
[   19.102703] nv_sata: Primary device removed
[   19.102704] nv_sata: Secondary device added
[   19.102705] nv_sata: Secondary device removed
[   19.106701] nv_sata: Primary device added
[   19.106702] nv_sata: Primary device removed
[   19.106704] nv_sata: Secondary device added
[   19.106705] nv_sata: Secondary device removed
[   19.110701] nv_sata: Primary device added
[   19.110702] nv_sata: Primary device removed
[   19.110703] nv_sata: Secondary device added
[   19.110705] nv_sata: Secondary device removed
[   19.114700] nv_sata: Primary device added
[   19.114702] nv_sata: Primary device removed
[   19.114703] nv_sata: Secondary device added
[   19.114704] nv_sata: Secondary device removed
[   19.118700] nv_sata: Primary device added
[   19.118701] nv_sata: Primary device removed
[   19.118703] nv_sata: Secondary device added
[   19.118704] nv_sata: Secondary device removed
[   19.122700] nv_sata: Primary device added
[   19.122701] nv_sata: Primary device removed
[   19.122702] nv_sata: Secondary device added
[   19.122703] nv_sata: Secondary device removed
[   19.126699] nv_sata: Primary device added
[   19.126701] nv_sata: Primary device removed
[   19.126702] nv_sata: Secondary device added
[   19.126703] nv_sata: Secondary device removed
[   19.130699] nv_sata: Primary device added
[   19.130700] nv_sata: Primary device removed
[   19.130701] nv_sata: Secondary device added
[   19.130703] nv_sata: Secondary device removed
[   19.134699] nv_sata: Primary device added
[   19.134700] nv_sata: Primary device removed
[   19.134701] nv_sata: Secondary device added
[   19.134702] nv_sata: Secondary device removed
[   19.138698] nv_sata: Primary device added
[   19.138700] nv_sata: Primary device removed
[   19.138701] nv_sata: Secondary device added
[   19.138702] nv_sata: Secondary device removed
[   19.142698] nv_sata: Primary device added
[   19.142699] nv_sata: Primary device removed
[   19.142700] nv_sata: Secondary device added
[   19.142702] nv_sata: Secondary device removed
[   19.146698] nv_sata: Primary device added
[   19.146699] nv_sata: Primary device removed
[   19.146700] nv_sata: Secondary device added
[   19.146701] nv_sata: Secondary device removed
[   19.150697] nv_sata: Primary device added
[   19.150698] nv_sata: Primary device removed
[   19.150700] nv_sata: Secondary device added
[   19.150701] nv_sata: Secondary device removed
[   19.154697] nv_sata: Primary device added
[   19.154698] nv_sata: Primary device removed
[   19.154699] nv_sata: Secondary device added
[   19.154700] nv_sata: Secondary device removed
[   19.158696] nv_sata: Primary device added
[   19.158698] nv_sata: Primary device removed
[   19.158699] nv_sata: Secondary device added
[   19.158700] nv_sata: Secondary device removed
[   19.162696] nv_sata: Primary device added
[   19.162697] nv_sata: Primary device removed
[   19.162698] nv_sata: Secondary device added
[   19.162700] nv_sata: Secondary device removed
[   19.166696] nv_sata: Primary device added
[   19.166697] nv_sata: Primary device removed
[   19.166698] nv_sata: Secondary device added
[   19.166699] nv_sata: Secondary device removed
[   19.170695] nv_sata: Primary device added
[   19.170697] nv_sata: Primary device removed
[   19.170698] nv_sata: Secondary device added
[   19.170699] nv_sata: Secondary device removed
[   19.174695] nv_sata: Primary device added
[   19.174696] nv_sata: Primary device removed
[   19.174697] nv_sata: Secondary device added
[   19.174699] nv_sata: Secondary device removed
[   19.178694] nv_sata: Primary device added
[   19.178696] nv_sata: Primary device removed
[   19.178697] nv_sata: Secondary device added
[   19.178698] nv_sata: Secondary device removed
[   19.182694] nv_sata: Primary device added
[   19.182695] nv_sata: Primary device removed
[   19.182697] nv_sata: Secondary device added
[   19.182698] nv_sata: Secondary device removed
[   19.186694] nv_sata: Primary device added
[   19.186695] nv_sata: Primary device removed
[   19.186696] nv_sata: Secondary device added
[   19.186697] nv_sata: Secondary device removed
[   19.190693] nv_sata: Primary device added
[   19.190695] nv_sata: Primary device removed
[   19.190696] nv_sata: Secondary device added
[   19.190697] nv_sata: Secondary device removed
[   19.194693] nv_sata: Primary device added
[   19.194694] nv_sata: Primary device removed
[   19.194695] nv_sata: Secondary device added
[   19.194697] nv_sata: Secondary device removed
[   19.198693] nv_sata: Primary device added
[   19.198694] nv_sata: Primary device removed
[   19.198695] nv_sata: Secondary device added
[   19.198696] nv_sata: Secondary device removed
[   19.202692] nv_sata: Primary device added
[   19.202694] nv_sata: Primary device removed
[   19.202695] nv_sata: Secondary device added
[   19.202696] nv_sata: Secondary device removed
[   19.206692] nv_sata: Primary device added
[   19.206693] nv_sata: Primary device removed
[   19.206694] nv_sata: Secondary device added
[   19.206696] nv_sata: Secondary device removed
[   19.210692] nv_sata: Primary device added
[   19.210693] nv_sata: Primary device removed
[   19.210694] nv_sata: Secondary device added
[   19.210695] nv_sata: Secondary device removed
[   19.214691] nv_sata: Primary device added
[   19.214692] nv_sata: Primary device removed
[   19.214694] nv_sata: Secondary device added
[   19.214695] nv_sata: Secondary device removed
[   19.218691] nv_sata: Primary device added
[   19.218692] nv_sata: Primary device removed
[   19.218693] nv_sata: Secondary device added
[   19.218695] nv_sata: Secondary device removed
[   19.222691] nv_sata: Primary device added
[   19.222692] nv_sata: Primary device removed
[   19.222693] nv_sata: Secondary device added
[   19.222695] nv_sata: Secondary device removed
[   19.226690] nv_sata: Primary device added
[   19.226691] nv_sata: Primary device removed
[   19.226692] nv_sata: Secondary device added
[   19.226694] nv_sata: Secondary device removed
[   19.230690] nv_sata: Primary device added
[   19.230691] nv_sata: Primary device removed
[   19.230692] nv_sata: Secondary device added
[   19.230693] nv_sata: Secondary device removed
[   19.234689] nv_sata: Primary device added
[   19.234691] nv_sata: Primary device removed
[   19.234692] nv_sata: Secondary device added
[   19.234693] nv_sata: Secondary device removed
[   19.238689] nv_sata: Primary device added
[   19.238690] nv_sata: Primary device removed
[   19.238691] nv_sata: Secondary device added
[   19.238693] nv_sata: Secondary device removed
[   19.242689] nv_sata: Primary device added
[   19.242690] nv_sata: Primary device removed
[   19.242691] nv_sata: Secondary device added
[   19.242692] nv_sata: Secondary device removed
[   19.246688] nv_sata: Primary device added
[   19.246689] nv_sata: Primary device removed
[   19.246691] nv_sata: Secondary device added
[   19.246692] nv_sata: Secondary device removed
[   19.250688] nv_sata: Primary device added
[   19.250689] nv_sata: Primary device removed
[   19.250690] nv_sata: Secondary device added
[   19.250691] nv_sata: Secondary device removed
[   19.254688] nv_sata: Primary device added
[   19.254689] nv_sata: Primary device removed
[   19.254690] nv_sata: Secondary device added
[   19.254691] nv_sata: Secondary device removed
[   19.258687] nv_sata: Primary device added
[   19.258688] nv_sata: Primary device removed
[   19.258690] nv_sata: Secondary device added
[   19.258691] nv_sata: Secondary device removed
[   19.262687] nv_sata: Primary device added
[   19.262688] nv_sata: Primary device removed
[   19.262689] nv_sata: Secondary device added
[   19.262690] nv_sata: Secondary device removed
[   19.266686] nv_sata: Primary device added
[   19.266688] nv_sata: Primary device removed
[   19.266689] nv_sata: Secondary device added
[   19.266690] nv_sata: Secondary device removed
[   19.270686] nv_sata: Primary device added
[   19.270687] nv_sata: Primary device removed
[   19.270689] nv_sata: Secondary device added
[   19.270690] nv_sata: Secondary device removed
[   19.274686] nv_sata: Primary device added
[   19.274687] nv_sata: Primary device removed
[   19.274688] nv_sata: Secondary device added
[   19.274690] nv_sata: Secondary device removed
[   19.274786] ata4: dev 0 cfg 49:2f00 82:346b 83:7f61 84:4003 85:3468 86:3c41 87:4003 88:407f
[   19.274790] ata4: dev 0 ATA-6, max UDMA/133, 312581808 sectors: LBA48
[   19.276076] nv_sata: Primary device added
[   19.276077] nv_sata: Primary device removed
[   19.276078] nv_sata: Secondary device added
[   19.276079] nv_sata: Secondary device removed
[   19.278685] nv_sata: Primary device added
[   19.278687] nv_sata: Primary device removed
[   19.278688] nv_sata: Secondary device added
[   19.278689] nv_sata: Secondary device removed
[   19.282685] nv_sata: Primary device added
[   19.282686] nv_sata: Primary device removed
[   19.282687] nv_sata: Secondary device added
[   19.282689] nv_sata: Secondary device removed
[   19.286685] nv_sata: Primary device added
[   19.286686] nv_sata: Primary device removed
[   19.286687] nv_sata: Secondary device added
[   19.286688] nv_sata: Secondary device removed
[   19.286781] ata4: dev 0 configured for UDMA/133
[   19.286783] scsi3 : sata_nv
[   19.287352]   Vendor: ATA       Model: WDC WD1600JD-00H  Rev: 08.0
[   19.287360]   Type:   Direct-Access                      ANSI SCSI revision: 05
[   19.289019] NFORCE-CK804: IDE controller at PCI slot 0000:00:06.0
[   19.289040] NFORCE-CK804: chipset revision 162
[   19.289043] NFORCE-CK804: not 100% native mode: will probe irqs later
[   19.289047] NFORCE-CK804: BIOS didn't set cable bits correctly. Enabling workaround.
[   19.289051] NFORCE-CK804: 0000:00:06.0 (rev a2) UDMA133 controller
[   19.289062]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[   19.289074]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
[   19.289083] Probing IDE interface ide0...
[   19.304206] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[   19.304220] sda: Write Protect is off
[   19.304222] sda: Mode Sense: 00 3a 00 00
[   19.304233] SCSI device sda: drive cache: write back
[   19.304282] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[   19.304288] sda: Write Protect is off
[   19.304290] sda: Mode Sense: 00 3a 00 00
[   19.304299] SCSI device sda: drive cache: write back
[   19.304301]  sda: sda1 sda2 < sda5 sda6 >
[   19.354570] sd 3:0:0:0: Attached scsi disk sda
[   19.518507] spurious 8259A interrupt: IRQ7.
[   19.862616] Probing IDE interface ide1...
[   20.602628] hdc: LITE-ON DVDRW SHM-165H6S, ATAPI CD/DVD-ROM drive
[   21.390549] hdd: PLEXTOR CD-R PX-W1210A, ATAPI CD/DVD-ROM drive
[   21.451173] ide1 at 0x170-0x177,0x376 on irq 15
[   21.465380] hdc: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(66)
[   21.465393] Uniform CD-ROM driver Revision: 3.20
[   21.468796] hdd: ATAPI 32X CD-ROM CD-R/RW drive, 2048kB Cache, DMA
[   21.635335] Probing IDE interface ide0...
[   21.666385] usbcore: registered new driver usbfs
[   21.666409] usbcore: registered new driver hub
[   21.667066] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[   21.667096] PCI: No IRQ known for interrupt pin A of device 0000:00:02.0. Please try using pci=biosirq.
[   21.667100] ohci_hcd 0000:00:02.0: Found HC with no IRQ.  Check BIOS/PCI 0000:00:02.0 setup!
[   21.667105] ohci_hcd 0000:00:02.0: init 0000:00:02.0 fail, -19
[   21.673601] PCI: No IRQ known for interrupt pin B of device 0000:00:02.1. Please try using pci=biosirq.
[   21.673607] ehci_hcd 0000:00:02.1: Found HC with no IRQ.  Check BIOS/PCI 0000:00:02.1 setup!
[   21.673613] ehci_hcd 0000:00:02.1: init 0000:00:02.1 fail, -19
[   21.732762] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.54.
[   21.733203] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   21.733213] forcedeth: using HIGHDMA
[   22.254767] eth0: forcedeth.c: subsystem: 01043:8141 bound to 0000:00:0a.0
[   22.328273] kjournald starting.  Commit interval 5 seconds
[   22.328288] EXT3-fs: mounted filesystem with ordered data mode.
[   30.041466] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x4c00
[   30.041487] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x4c40
[   30.061974] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   30.073089] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   30.396884] parport: PnPBIOS parport detected.
[   30.396937] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   30.638946] eth0: no link during initialization.
[   30.666085] input: PC Speaker as /class/input/input1
[   30.703141] sd 3:0:0:0: Attached scsi generic sg0 type 0
[   30.755954] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   30.783405] Linux agpgart interface v0.101 (c) Dave Jones
[   30.823686] Linux Tulip driver version 1.1.14 (May 6, 2006)
[   30.936208] input: ImExPS/2 Generic Explorer Mouse as /class/input/input2
[   31.081495] intel8x0_measure_ac97_clock: measured 58376 usecs
[   31.081501] intel8x0: clocking to 46961
[   31.082532] tulip0:  MII transceiver #1 config 1000 status 786d advertising 01e1.
[   31.086753] eth1: ADMtek Comet rev 17 at Port 0xa000, 00:03:6D:1F:F6:94, IRQ 3.
[   31.373747] nvidia: module license 'NVIDIA' taints kernel.
[   31.412966] ts: Compaq touchscreen protocol output
[   31.720599] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   31.720933] NVRM: loading NVIDIA UNIX x86 Kernel Module  1.0-9755  Mon Feb 26 23:21:15 PST 2007
[   31.738794] NET: Registered protocol family 17
[   31.897170] lp0: using parport0 (interrupt-driven).
[   31.928104] fuse init (API version 7.6)
[   32.062797] EXT3 FS on sda6, internal journal
[   34.830894] 0000:05:07.0: tulip_stop_rxtx() failed (CSR5 0xfc664010 CSR6 0xff972117)
[   34.830907] eth1: Setting full-duplex based on MII#1 link partner capability of 45e1.
[   35.932535] NET: Registered protocol family 10
[   35.932637] lo: Disabled Privacy Extensions
[   35.932702] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   35.932788] IPv6 over IPv4 tunneling driver
[   37.708134] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.60.2)
[   37.712882] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
[   40.246100] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   45.067095] /dev/vmmon[4252]: Module vmmon: registered with major=10 minor=165
[   45.067485] /dev/vmmon[4252]: Module vmmon: initialized
[   45.160485] Bluetooth: Core ver 2.8
[   45.160492] NET: Registered protocol family 31
[   45.160494] Bluetooth: HCI device and connection manager initialized
[   45.160510] Bluetooth: HCI socket layer initialized
[   45.189054] Bluetooth: L2CAP ver 2.8
[   45.189059] Bluetooth: L2CAP socket layer initialized
[   45.191378] Bluetooth: RFCOMM socket layer initialized
[   45.191398] Bluetooth: RFCOMM TTY layer initialized
[   45.191400] Bluetooth: RFCOMM ver 1.7
[   46.127989] eth1: no IPv6 routers present
[  781.696230] hdd: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[ 1140.855051] hdd: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[ 1464.373134] hdd: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[ 1900.080862] hdd: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[ 1960.339295] hdd: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
```

What the heck is going on!?

Anyways, just as another test, I put in my usb flash drive and ran lsusb, again nothing.

This is MADNESS

(Madness?  This.. IS... SPAAAAAARTAAAAAAAAAA)

---

### Post by nick_karstedt on 2007-03-27
bump

---

### Post by trjnhrse44 on 2007-05-23
this is an apic/acpi issue.  I believe that command in your code snipet may be a grub option you can pass at boot to compensate.  So at boot time enter the grub menu and hit e to edit your boot command then append this code to the end of the string
```
pci=biosirq
```

My laptop has a similar problem but I use noapic in my grub to work around.  Unfortunately it is only temporary and I still lose irq 7 after a random amount of uptime, which essentially disables my usb.

I will try to use this pci=bios code myself and see what happens and if i have better luck.

---

