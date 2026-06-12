---
title: "Kworld PVR-Plus PVR-TV 7133 TC878 PCI TV Card"
date: 2007-11-25
forum: Hardware &amp; Laptops
---

### Post by tcgood on 2007-11-25
Okay, so I have a kworld tv tuner expert, and mythbuntu won't recognize the card.  Here is the dmesg:
[    0.000000] Linux version 2.6.22-14-generic (buildd@crested) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 21:45:15 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] Command line: root=UUID=4640ab30-9cc3-4236-be60-2c631542183f ro quiet splash
[   14.425793] AMD Athlon(tm) 64 X2 Dual Core Processor 3600+ stepping 01
[   14.429214] Brought up 2 CPUs
[   15.441173] migration_cost=232
[   15.440899] NET: Registered protocol family 16
[   15.440991] ACPI: bus type pci registered
[   15.440996] PCI: Using configuration type 1
[   15.442301] ACPI: EC: Look up EC in DSDT
[   15.448666] ACPI: Interpreter enabled
[   15.448669] ACPI: (supports S0 S1 S3 S4 S5)
[   15.448687] ACPI: Using IOAPIC for interrupt routing
[   15.459553] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   15.459560] PCI: Probing PCI hardware (bus 00)
[   15.460073] PCI: Transparent bridge - 0000:00:04.0
[   15.460341] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   15.460593] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   15.502281] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   15.502464] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   15.502644] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   15.502824] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   15.503003] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   15.503182] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   15.503361] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   15.503542] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 *10 11 14 15)
[   15.503721] ACPI: PCI Interrupt Link [LIGP] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   15.503900] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   15.504085] ACPI: PCI Interrupt Link [LUBA] (IRQs *5 7 9 10 11 14 15)
[   15.504266] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 *11 14 15)
[   15.504454] ACPI: PCI Interrupt Link [LAZA] (IRQs *5 7 9 10 11 14 15)
[   15.504634] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   15.504815] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 *11 14 15)
[   15.504996] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 *10 11 14 15)
[   15.505176] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   15.505357] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[   15.505537] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   15.505757] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[   15.505966] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[   15.506176] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[   15.506385] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[   15.506592] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[   15.506800] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[   15.507009] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[   15.507219] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0
[   15.507428] ACPI: PCI Interrupt Link [AIGP] (IRQs 20 21 22 23) *0, disabled.
[   15.507638] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[   15.507848] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[   15.508058] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[   15.508269] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
[   15.508482] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[   15.508695] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[   15.508905] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[   15.509116] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[   15.509327] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[   15.509538] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
[   15.509650] Linux Plug and Play Support v0.97 (c) Adam Belay
[   15.509665] pnp: PnP ACPI init
[   15.509676] ACPI: bus type pnp registered
[   15.515469] pnp: PnP ACPI: found 13 devices
[   15.515472] ACPI: ACPI bus type pnp unregistered
[   15.515535] PCI: Using ACPI for IRQ routing
[   15.515539] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   15.515619] NET: Registered protocol family 8
[   15.515621] NET: Registered protocol family 20
[   15.515740] pnp: 00:01: ioport range 0x1000-0x107f has been reserved
[   15.515744] pnp: 00:01: ioport range 0x1080-0x10ff has been reserved
[   15.515747] pnp: 00:01: ioport range 0x1400-0x147f has been reserved
[   15.515750] pnp: 00:01: ioport range 0x1480-0x14ff has been reserved
[   15.515753] pnp: 00:01: ioport range 0x1800-0x187f has been reserved
[   15.515756] pnp: 00:01: ioport range 0x1880-0x18ff has been reserved
[   15.515759] pnp: 00:01: ioport range 0x2000-0x207f has been reserved
[   15.515762] pnp: 00:01: ioport range 0x2080-0x20ff has been reserved
[   15.515765] pnp: 00:01: iomem range 0x0-0x0 could not be reserved
[   15.515769] pnp: 00:01: iomem range 0xfefe0000-0xfefe01ff has been reserved
[   15.515772] pnp: 00:01: iomem range 0xfefe1000-0xfefe10ff has been reserved
[   15.515775] pnp: 00:01: iomem range 0x0-0x0 could not be reserved
[   15.515786] pnp: 00:0b: iomem range 0xf0000000-0xf3ffffff could not be reserved
[   15.515791] pnp: 00:0c: iomem range 0xf0000-0xfffff could not be reserved
[   15.515795] pnp: 00:0c: iomem range 0xfeff0000-0xfeff00ff has been reserved
[   15.515798] pnp: 00:0c: iomem range 0x3fee0000-0x3fefffff could not be reserved
[   15.515801] pnp: 00:0c: iomem range 0xffff0000-0xffffffff has been reserved
[   15.516096] PCI: Bridge: 0000:00:04.0
[   15.516099]   IO window: c000-cfff
[   15.516103]   MEM window: fde00000-fdefffff
[   15.516106]   PREFETCH window: fdf00000-fdffffff
[   15.516112] PCI: Bridge: 0000:00:09.0
[   15.516114]   IO window: b000-bfff
[   15.516117]   MEM window: fdd00000-fddfffff
[   15.516120]   PREFETCH window: e0000000-efffffff
[   15.516123] PCI: Bridge: 0000:00:0b.0
[   15.516125]   IO window: a000-afff
[   15.516128]   MEM window: fdc00000-fdcfffff
[   15.516131]   PREFETCH window: fdb00000-fdbfffff
[   15.516133] PCI: Bridge: 0000:00:0c.0
[   15.516135]   IO window: 9000-9fff
[   15.516138]   MEM window: fda00000-fdafffff
[   15.516141]   PREFETCH window: fd900000-fd9fffff
[   15.516151] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   15.516159] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   15.516165] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   15.516170] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   15.516184] NET: Registered protocol family 2
[   15.516796] Time: acpi_pm clocksource has been installed.
[   15.548302] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   15.548709] TCP established hash table entries: 131072 (order: 9, 3145728 bytes)
[   15.551115] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   15.551899] TCP: Hash tables configured (established 131072 bind 65536)
[   15.551903] TCP reno registered
[   15.560367] checking if image is initramfs... it is
[   16.208243] Freeing initrd memory: 7964k freed
[   16.215135] audit: initializing netlink socket (disabled)
[   16.215151] audit(1196020178.364:1): initialized
[   16.217360] VFS: Disk quotas dquot_6.5.1
[   16.217415] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   16.217505] io scheduler noop registered
[   16.217507] io scheduler anticipatory registered
[   16.217509] io scheduler deadline registered
[   16.217609] io scheduler cfq registered (default)
[   16.244622] Boot video device is 0000:02:00.0
[   16.244780] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   16.244800] assign_interrupt_mode Found MSI capability
[   16.244804] Allocate Port Service[0000:00:09.0:pcie00]
[   16.244871] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   16.244891] assign_interrupt_mode Found MSI capability
[   16.244893] Allocate Port Service[0000:00:0b.0:pcie00]
[   16.244950] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   16.244969] assign_interrupt_mode Found MSI capability
[   16.244972] Allocate Port Service[0000:00:0c.0:pcie00]
[   16.272875] Real Time Clock Driver v1.12ac
[   16.272985] Linux agpgart interface v0.102 (c) Dave Jones
[   16.272988] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   16.273087] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   16.273740] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   16.274541] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   16.274681] input: Macintosh mouse button emulation as /class/input/input0
[   16.274759] PNP: PS/2 Controller [PNP0f13:PS2M] at 0x60,0x64 irq 12
[   16.274762] PNP: PS/2 controller doesn't have KBD irq; using default 1
[   16.275095] serio: i8042 KBD port at 0x60,0x64 irq 1
[   16.275100] serio: i8042 AUX port at 0x60,0x64 irq 12
[   16.275267] mice: PS/2 mouse device common for all mice
[   16.275405] TCP cubic registered
[   16.275467] NET: Registered protocol family 1
[   16.275673] /build/buildd/linux-source-2.6.22-2.6.22/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   16.275684] Freeing unused kernel memory: 296k freed
[   17.442135] AppArmor: AppArmor initialized<5>audit(1196020179.592:2):  type=1505 info="AppArmor initialized" pid=1199
[   17.449052] fuse init (API version 7.8)
[   17.453577] Failure registering capabilities with primary security module.
[   17.474271] ACPI: Fan [FAN] (on)
[   17.480114] ACPI: Thermal Zone [THRM] (40 C)
[   18.000456] usbcore: registered new interface driver usbfs
[   18.000484] usbcore: registered new interface driver hub
[   18.000513] usbcore: registered new device driver usb
[   18.001988] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 23
[   18.002000] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCL] -> GSI 23 (level, low) -> IRQ 23
[   18.002251] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   18.002259] ehci_hcd 0000:00:02.1: EHCI Host Controller
[   18.002444] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[   18.002475] ehci_hcd 0000:00:02.1: debug port 1
[   18.002479] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[   18.002491] ehci_hcd 0000:00:02.1: irq 23, io mem 0xfe02e000
[   18.002498] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   18.002610] usb usb1: configuration #1 chosen from 1 choice
[   18.002636] hub 1-0:1.0: USB hub found
[   18.002643] hub 1-0:1.0: 8 ports detected
[   18.007323] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
[   18.042682] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   18.052042] Floppy drive(s): fd0 is 1.44M
[   18.064933] SCSI subsystem initialized
[   18.071001] libata version 2.21 loaded.
[   18.098713] FDC 0 is a post-1991 82077
[   18.110738] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
[   18.110751] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [APCH] -> GSI 22 (level, low) -> IRQ 22
[   18.110757] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   18.110767] forcedeth: using HIGHDMA
[   18.633950] eth0: forcedeth.c: subsystem: 01019:2602 bound to 0000:00:07.0
[   18.635020] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
[   18.635033] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 21 (level, low) -> IRQ 21
[   18.635631] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   18.635638] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   18.635975] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[   18.635994] ohci_hcd 0000:00:02.0: irq 21, io mem 0xfe02f000
[   18.696512] usb usb2: configuration #1 chosen from 1 choice
[   18.696688] hub 2-0:1.0: USB hub found
[   18.696698] hub 2-0:1.0: 8 ports detected
[   18.801961] sata_nv 0000:00:08.0: version 3.4
[   18.802335] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 20
[   18.802346] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSI] -> GSI 20 (level, low) -> IRQ 20
[   18.802578] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   18.802724] scsi0 : sata_nv
[   18.802782] scsi1 : sata_nv
[   18.802855] ata1: SATA max UDMA/133 cmd 0x00000000000109f0 ctl 0x0000000000010bf2 bmdma 0x000000000001d800 irq 20
[   18.802859] ata2: SATA max UDMA/133 cmd 0x0000000000010970 ctl 0x0000000000010b72 bmdma 0x000000000001d808 irq 20
[   19.109218] usb 2-1: new low speed USB device using ohci_hcd and address 2
[   19.117210] ata1: SATA link down (SStatus 0 SControl 300)
[   19.332604] usb 2-1: configuration #1 chosen from 1 choice
[   19.596807] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   19.606403] ata2.00: ATA-7: Maxtor 7H500F0, HA431DN0, max UDMA/133
[   19.606408] ata2.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   19.626379] ata2.00: configured for UDMA/133
[   19.626004] scsi 1:0:0:0: Direct-Access     ATA      Maxtor 7H500F0   HA43 PQ: 0 ANSI: 5
[   19.631313] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   19.631320] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   19.632009] NFORCE-MCP61: IDE controller at PCI slot 0000:00:06.0
[   19.632034] NFORCE-MCP61: chipset revision 162
[   19.632036] NFORCE-MCP61: not 100% native mode: will probe irqs later
[   19.632043] NFORCE-MCP61: 0000:00:06.0 (rev a2) UDMA133 controller
[   19.632051]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[   19.632062] Probing IDE interface ide0...
[   19.647940] usbcore: registered new interface driver hiddev
[   19.653998] input: Logitech USB Receiver as /class/input/input1
[   19.654014] input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:02.0-1
[   19.660136] sd 1:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   19.660150] sd 1:0:0:0: [sda] Write Protect is off
[   19.660153] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   19.660165] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   19.660225] sd 1:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   19.660233] sd 1:0:0:0: [sda] Write Protect is off
[   19.660235] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   19.660246] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   19.660251]  sda:<6>input: Logitech USB Receiver as /class/input/input2
[   19.665640] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:02.0-1
[   19.665655] usbcore: registered new interface driver usbhid
[   19.665658] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   19.679522]  sda1 sda2 < sda5 >
[   19.699464] sd 1:0:0:0: [sda] Attached SCSI disk
[   19.702791] sd 1:0:0:0: Attached scsi generic sg0 type 0
[   19.865906] Attempting manual resume
[   19.865910] swsusp: Resume From Partition 8:5
[   19.865912] PM: Checking swsusp image.
[   19.866068] PM: Resume from disk failed.
[   19.883643] EXT3-fs: INFO: recovery required on readonly filesystem.
[   19.883648] EXT3-fs: write access will be enabled during recovery.
[   20.310329] kjournald starting.  Commit interval 5 seconds
[   20.310816] EXT3-fs: sda1: orphan cleanup on readonly fs
[   20.310826] ext3_orphan_cleanup: deleting unreferenced inode 1982472
[   20.310856] ext3_orphan_cleanup: deleting unreferenced inode 1982471
[   20.310865] ext3_orphan_cleanup: deleting unreferenced inode 1982470
[   20.310874] ext3_orphan_cleanup: deleting unreferenced inode 1982469
[   20.310881] ext3_orphan_cleanup: deleting unreferenced inode 1982468
[   20.310889] EXT3-fs: sda1: 5 orphan inodes deleted
[   20.310891] EXT3-fs: recovery complete.
[   20.312404] EXT3-fs: mounted filesystem with ordered data mode.
[   20.372242] hda: _NEC DVD_RW ND-3550A, ATAPI CD/DVD-ROM drive
[   21.043950] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   26.358460] input: PC Speaker as /class/input/input3
[   26.369983] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   26.376599] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   26.382078] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   26.382281] i2c-adapter i2c-1: nForce2 SMBus adapter at 0xf400
[   26.524539] hda: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[   26.524550] Uniform CD-ROM driver Revision: 3.20
[   26.726351] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 23
[   26.726357] ACPI: PCI Interrupt 0000:00:05.0[B] -> Link [AAZA] -> GSI 23 (level, low) -> IRQ 23
[   26.726577] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   27.064133] input: ImPS/2 Logitech Wheel Mouse as /class/input/input4
[   27.067037] parport_pc 00:09: reported by Plug and Play ACPI
[   27.067103] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   27.503840] lp0: using parport0 (interrupt-driven).
[   27.703288] Adding 3012148k swap on /dev/sda5.  Priority:-1 extents:1 across:3012148k
[   28.134250] EXT3 FS on sda1, internal journal
[   29.477028] No dock devices found.
[   29.485201] input: Power Button (FF) as /class/input/input5
[   29.485223] ACPI: Power Button (FF) [PWRF]
[   29.485271] input: Power Button (CM) as /class/input/input6
[   29.485285] ACPI: Power Button (CM) [PWRB]
[   32.249509] NET: Registered protocol family 10
[   32.249619] lo: Disabled Privacy Extensions
[   41.255617] [drm] Initialized drm 1.1.0 20060810
[   41.261979] ACPI: PCI Interrupt Link [APC8] enabled at IRQ 16
[   41.261995] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [APC8] -> GSI 16 (level, low) -> IRQ 16
[   41.262733] [drm] Initialized radeon 1.27.0 20060524 on minor 0
[   43.105544] NET: Registered protocol family 17
[   43.784926] [drm] Setting GART location based on new memory map
[   43.785307] [drm] Loading R300 Microcode
[   43.785332] [drm] writeback test succeeded in 1 usecs
[   54.623455] eth0: no IPv6 routers present

I am more than new at this, but I can use the command line very basic.  Please any help would be great.  I tried doing it myself, but I can't seem to get it to work.

---

