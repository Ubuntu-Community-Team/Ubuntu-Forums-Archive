---
title: "Problem with large hard drive"
date: 2006-07-07
forum: Hardware &amp; Laptops
---

### Post by kfb on 2006-07-07
I have a 250gig hard drive formatted to vfat.  It works just fine and XP and used to work in Gentoo.  I just installed Ubuntu last night and now it sees it, but thinks that it's unformatted.  However, my other disks that are vfat work, so it isn't the formatting.

I remember having to enable a kernel option to support large hard drives in Gentoo.  Is it possible that I have to do this in Ubuntu?  If so, I have no idea how.

I don't know what else to post for support info, so here's my dmesg:

```
[17179569.184000] Linux version 2.6.15-25-386 (buildd@terranova) (gcc version 4. 0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Wed Jun 14 11:25:49 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009e800 (usable)
[17179569.184000]  BIOS-e820: 000000000009e800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000007fff0000 (usable)
[17179569.184000]  BIOS-e820: 000000007fff0000 - 000000007fff3000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000007fff3000 - 0000000080000000 (ACPI data)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[17179569.184000] 1151MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f5d50
[17179569.184000] On node 0 totalpages: 524272
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 294896 pages, LIFO batch:31
[17179569.184000] DMI 2.2 present.
[17179569.184000] ACPI: RSDP (v000 IntelR                                ) @ 0x0 00f77e0
[17179569.184000] ACPI: RSDT (v001 IntelR AWRDACPI 0x42302e31 AWRD 0x00000000) @  0x7fff3000
[17179569.184000] ACPI: FADT (v001 IntelR AWRDACPI 0x42302e31 AWRD 0x00000000) @  0x7fff3040
[17179569.184000] ACPI: MADT (v001 IntelR AWRDACPI 0x42302e31 AWRD 0x00000000) @  0x7fff7a40
[17179569.184000] ACPI: DSDT (v001 INTELR AWRDACPI 0x00001000 MSFT 0x0100000e) @  0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x408
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:2 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[17179569.184000] Processor #1 15:2 APIC version 20
[17179569.184000] WARNING: NR_CPUS limit of 1 reached.  Processor ignored.
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 88000000 (gap: 80000000:7 ec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/sda2 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[17179569.184000] Detected 3007.280 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179572.180000] Dentry cache hash table entries: 131072 (order: 7, 524288 byte s)
[17179572.180000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179572.260000] Memory: 2068644k/2097088k available (1976k kernel code, 27140k  reserved, 606k data, 288k init, 1179584k highmem)
[17179572.260000] Checking if this processor honours the WP bit even in supervis or mode... Ok.
[17179572.340000] Calibrating delay using timer specific routine.. 6019.18 BogoM IPS (lpj=12038364)
[17179572.340000] Security Framework v1.0.0 initialized
[17179572.340000] SELinux:  Disabled at boot.
[17179572.340000] Mount-cache hash table entries: 512
[17179572.340000] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[17179572.340000] CPU: After vendor identify, caps: bfebfbff 00000000 00000000 0 0000000 00004400 00000000 00000000
[17179572.340000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[17179572.340000] CPU: L2 cache: 512K
[17179572.340000] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000008 0 00004400 00000000 00000000
[17179572.340000] mtrr: v2.0 (20020519)
[17179572.340000] CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 09
[17179572.340000] Enabling fast FPU save and restore... done.
[17179572.340000] Enabling unmasked SIMD FPU exception support... done.
[17179572.340000] Checking 'hlt' instruction... OK.
[17179572.356000] checking if image is initramfs... it is
[17179572.800000] Freeing initrd memory: 6614k freed
[17179572.812000] ACPI: Looking for DSDT ... not found!
[17179573.008000] ENABLING IO-APIC IRQs
[17179573.008000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179573.152000] NET: Registered protocol family 16
[17179573.152000] EISA bus registered
[17179573.152000] ACPI: bus type pci registered
[17179573.164000] PCI: PCI BIOS revision 2.10 entry at 0xfba10, last bus=3
[17179573.164000] PCI: Using configuration type 1
[17179573.164000] ACPI: Subsystem revision 20051216
[17179573.172000] ACPI: Interpreter enabled
[17179573.172000] ACPI: Using IOAPIC for interrupt routing
[17179573.172000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179573.172000] PCI: Probing PCI hardware (bus 00)
[17179573.176000] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[17179573.176000] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
[17179573.176000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179573.176000] Boot video device is 0000:01:00.0
[17179573.176000] PCI: Transparent bridge - 0000:00:1e.0
[17179573.176000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179573.184000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[17179573.188000] ACPI: PCI Interrupt Link [LNKA] (IRQs *3 4 5 7 9 10 11 12 14 1 5)
[17179573.188000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 *11 12 14 1 5)
[17179573.188000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12 14 1 5)
[17179573.188000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 *10 11 12 14 1 5)
[17179573.188000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12 14 15 ) *0, disabled.
[17179573.188000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15 ) *0, disabled.
[17179573.188000] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 *9 10 11 12 14 1 5)
[17179573.188000] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 *5 7 9 10 11 12 14 1 5)
[17179573.288000] ACPI: Power Resource [PFAN] (off)
[17179573.288000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179573.288000] pnp: PnP ACPI init
[17179573.288000] pnp: PnP ACPI: found 13 devices
[17179573.288000] PnPBIOS: Disabled by ACPI PNP
[17179573.288000] PCI: Using ACPI for IRQ routing
[17179573.288000] PCI: If a device doesn't work, try "pci=routeirq".  If it help s, post a report
[17179573.320000] pnp: 00:0a: ioport range 0x400-0x4bf could not be reserved
[17179573.320000] PCI: Bridge: 0000:00:01.0
[17179573.320000]   IO window: disabled.
[17179573.320000]   MEM window: f0000000-f2ffffff
[17179573.320000]   PREFETCH window: e0000000-efffffff
[17179573.320000] PCI: Bridge: 0000:00:03.0
[17179573.320000]   IO window: a000-afff
[17179573.320000]   MEM window: f5000000-f50fffff
[17179573.320000]   PREFETCH window: disabled.
[17179573.320000] PCI: Bridge: 0000:00:1e.0
[17179573.320000]   IO window: 7000-9fff
[17179573.320000]   MEM window: f3000000-f4ffffff
[17179573.320000]   PREFETCH window: 88000000-880fffff
[17179573.320000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179573.320000] audit: initializing netlink socket (disabled)
[17179573.320000] audit(1152280438.320:1): initialized
[17179573.320000] highmem bounce pool size: 64 pages
[17179573.320000] VFS: Disk quotas dquot_6.5.1
[17179573.320000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179573.320000] Initializing Cryptographic API
[17179573.320000] io scheduler noop registered
[17179573.320000] io scheduler anticipatory registered
[17179573.320000] io scheduler deadline registered
[17179573.320000] io scheduler cfq registered
[17179573.320000] isapnp: Scanning for PnP cards...
[17179573.672000] isapnp: No Plug & Play device found
[17179573.684000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179573.688000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179573.688000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179573.688000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ shar ing enabled
[17179573.688000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179573.688000] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179573.688000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 b locksize
[17179573.688000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179573.688000] ide: Assuming 33MHz system bus speed for PIO modes; override w ith idebus=xx
[17179573.688000] mice: PS/2 mouse device common for all mice
[17179573.692000] EISA: Probing bus 0 at eisa.0
[17179573.692000] Cannot allocate resource for EISA slot 7
[17179573.692000] Cannot allocate resource for EISA slot 8
[17179573.692000] EISA: Detected 0 cards.
[17179573.692000] NET: Registered protocol family 2
[17179573.720000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179573.732000] IP route cache hash table entries: 131072 (order: 7, 524288 by tes)
[17179573.732000] TCP established hash table entries: 524288 (order: 9, 2097152 bytes)
[17179573.732000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[17179573.732000] TCP: Hash tables configured (established 524288 bind 65536)
[17179573.732000] TCP reno registered
[17179573.732000] TCP bic registered
[17179573.732000] NET: Registered protocol family 1
[17179573.732000] NET: Registered protocol family 8
[17179573.732000] NET: Registered protocol family 20
[17179573.732000] Using IPI Shortcut mode
[17179573.732000] ACPI wakeup devices:
[17179573.732000] PCI0 CSAD HUB0 UAR1 USB0 USB1 USB2 USB3 USBE MODM
[17179573.732000] ACPI: (supports S0 S1 S4 S5)
[17179573.732000] Freeing unused kernel memory: 288k freed
[17179573.772000] vga16fb: initializing
[17179573.772000] vga16fb: mapped to 0xc00a0000
[17179573.936000] Console: switching to colour frame buffer device 80x25
[17179573.936000] fb0: VGA16 VGA frame buffer device
[17179574.960000] Capability LSM initialized
[17179575.204000] ACPI: Fan [FAN] (off)
[17179575.408000] ACPI: Thermal Zone [THRM] (44 C)
[17179575.928000] SCSI subsystem initialized
[17179575.928000] ACPI: bus type scsi registered
[17179575.928000] libata version 1.20 loaded.
[17179575.932000] sata_sil 0000:03:03.0: version 0.9
[17179575.932000] ACPI: PCI Interrupt 0000:03:03.0[A] -> GSI 19 (level, low) -> IRQ 169
[17179575.932000] ata1: SATA max UDMA/100 cmd 0xF8860080 ctl 0xF886008A bmdma 0x F8860000 irq 169
[17179575.932000] ata2: SATA max UDMA/100 cmd 0xF88600C0 ctl 0xF88600CA bmdma 0x F8860008 irq 169
[17179576.136000] ata1: no device found (phy stat 00000000)
[17179576.136000] scsi0 : sata_sil
[17179576.340000] ata2: no device found (phy stat 00000000)
[17179576.340000] scsi1 : sata_sil
[17179576.372000] PDC20269: IDE controller at PCI slot 0000:03:07.0
[17179576.372000] ACPI: PCI Interrupt 0000:03:07.0[A] -> GSI 23 (level, low) -> IRQ 177
[17179576.372000] PDC20269: chipset revision 2
[17179576.372000] PDC20269: ROM enabled at 0x88080000
[17179576.372000] PDC20269: 100% native mode on irq 177
[17179576.372000]     ide2: BM-DMA at 0x9c00-0x9c07, BIOS settings: hde:pio, hdf :pio
[17179576.372000]     ide3: BM-DMA at 0x9c08-0x9c0f, BIOS settings: hdg:pio, hdh :pio
[17179576.372000] Probing IDE interface ide2...
[17179576.660000] hde: WDC WD2500LB-55EDA0, ATA DISK drive
[17179577.332000] ide2 at 0x8c00-0x8c07,0x9002 on irq 177
[17179577.332000] Probing IDE interface ide3...
[17179577.904000] hde: max request size: 1024KiB
[17179577.932000] hde: 488397168 sectors (250059 MB) w/2048KiB Cache, CHS=30401/ 255/63, UDMA(100)
[17179577.936000] hde: cache flushes supported
[17179577.936000]  hde: hde1
[17179578.612000] ICH5: IDE controller at PCI slot 0000:00:1f.1
[17179578.612000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 185
[17179578.612000] ICH5: chipset revision 2
[17179578.612000] ICH5: not 100% native mode: will probe irqs later
[17179578.612000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb :pio
[17179578.612000]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd :pio
[17179578.612000] Probing IDE interface ide0...
[17179578.900000] hda: Maxtor 54610H6, ATA DISK drive
[17179579.180000] hdb: MAXTOR 6L080J4, ATA DISK drive
[17179579.236000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179579.264000] hda: max request size: 128KiB
[17179579.264000] hda: 90045648 sectors (46103 MB) w/2048KiB Cache, CHS=65535/16 /63, UDMA(100)
[17179579.264000] hda: cache flushes not supported
[17179579.264000]  hda: hda1
[17179579.268000] hdb: max request size: 128KiB
[17179579.268000] hdb: 156355584 sectors (80054 MB) w/1819KiB Cache, CHS=65535/1 6/63, UDMA(100)
[17179579.268000] hdb: cache flushes supported
[17179579.268000]  hdb: hdb1
[17179579.272000] Probing IDE interface ide1...
[17179579.676000] hdc: LITEON DVD-ROM LTD163, ATAPI CD/DVD-ROM drive
[17179580.460000] hdd: _NEC DVD+RW ND-1100A, ATAPI CD/DVD-ROM drive
[17179580.516000] ide1 at 0x170-0x177,0x376 on irq 15
[17179580.548000] hdc: ATAPI 48X DVD-ROM drive, 512kB Cache, UDMA(33)
[17179580.548000] Uniform CD-ROM driver Revision: 3.20
[17179580.552000] hdd: ATAPI 40X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179582.532000] ata_piix 0000:00:1f.2: version 1.05
[17179582.532000] ata_pci_init_one: pci_dev class+intf: 0x1018f
[17179582.532000] ata_pci_init_one: NO_LEGACY == 0
[17179582.532000] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 185
[17179582.532000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179582.532000] ata3: PATA max UDMA/133 cmd 0xC000 ctl 0xC402 bmdma 0xD000 irq  185
[17179582.532000] ata4: PATA max UDMA/133 cmd 0xC800 ctl 0xCC02 bmdma 0xD008 irq  185
[17179582.752000] ata3: dev 0 cfg 00:0c5a 49:2f00 82:346b 83:7f01 84:4003 85:346 9 86:3c01 87:4003 88:207f 93:0000
[17179582.752000] ata3: dev 0 ATA-6, max UDMA/133, 234375000 sectors: LBA48
[17179582.752000] sata_get_dev_handle: SATA dev addr=0x1f0002, handle=0xdffe7320
[17179582.756000] ata3: dev 0 configured for UDMA/133
[17179582.756000] sata_get_dev_handle: SATA dev addr=0x1f0002, handle=0xdffe7320
[17179582.756000] scsi2 : ata_piix
[17179582.920000] ata4: dev 0 cfg 00:045a 49:2f00 82:346b 83:7f01 84:4003 85:3c6 9 86:3c01 87:4003 88:203f 93:400b
[17179582.920000] ata4: dev 0 ATA-7, max UDMA/100, 156368016 sectors: LBA48
[17179582.920000] ata4(0): applying bridge limits
[17179582.920000] ata4: dev 0 configured for UDMA/100
[17179582.920000] sata_get_dev_handle: SATA dev addr=0x1f0002, handle=0xdffe7320
[17179582.920000] scsi3 : ata_piix
[17179582.920000]   Vendor: ATA       Model: ST3120026AS       Rev: 8.05
[17179582.920000]   Type:   Direct-Access                      ANSI SCSI revisio n: 05
[17179582.924000]   Vendor: ATA       Model: SAMSUNG SP0802N   Rev: TK10
[17179582.924000]   Type:   Direct-Access                      ANSI SCSI revisio n: 05
[17179582.928000] Driver 'sd' needs updating - please use bus_type methods
[17179582.932000] SCSI device sda: 234375000 512-byte hdwr sectors (120000 MB)
[17179582.932000] SCSI device sda: drive cache: write back
[17179582.936000] SCSI device sda: 234375000 512-byte hdwr sectors (120000 MB)
[17179582.936000] SCSI device sda: drive cache: write back
[17179582.936000]  sda: sda1 sda2 sda3
[17179582.976000] sd 2:0:0:0: Attached scsi disk sda
[17179582.976000] SCSI device sdb: 156368016 512-byte hdwr sectors (80060 MB)
[17179582.984000] SCSI device sdb: drive cache: write back
[17179582.984000] SCSI device sdb: 156368016 512-byte hdwr sectors (80060 MB)
[17179582.984000] SCSI device sdb: drive cache: write back
[17179582.984000]  sdb: sdb1
[17179582.992000] sd 3:0:0:0: Attached scsi disk sdb
[17179583.392000] usbcore: registered new driver usbfs
[17179583.392000] usbcore: registered new driver hub
[17179583.392000] USB Universal Host Controller Interface driver v2.3
[17179583.392000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 193
[17179583.392000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179583.392000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179583.396000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus nu mber 1
[17179583.396000] uhci_hcd 0000:00:1d.0: irq 193, io base 0x0000bc00
[17179583.396000] hub 1-0:1.0: USB hub found
[17179583.396000] hub 1-0:1.0: 2 ports detected
[17179583.456000] ieee1394: Initialized config rom entry `ip1394'
[17179583.500000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 169
[17179583.500000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179583.500000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179583.500000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus nu mber 2
[17179583.500000] uhci_hcd 0000:00:1d.1: irq 169, io base 0x0000b000
[17179583.500000] hub 2-0:1.0: USB hub found
[17179583.500000] hub 2-0:1.0: 2 ports detected
[17179583.604000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 185
[17179583.604000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179583.604000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179583.604000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus nu mber 3
[17179583.604000] uhci_hcd 0000:00:1d.2: irq 185, io base 0x0000b400
[17179583.604000] hub 3-0:1.0: USB hub found
[17179583.604000] hub 3-0:1.0: 2 ports detected
[17179583.708000] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 193
[17179583.708000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17179583.708000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[17179583.708000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus nu mber 4
[17179583.708000] uhci_hcd 0000:00:1d.3: irq 193, io base 0x0000b800
[17179583.708000] hub 4-0:1.0: USB hub found
[17179583.708000] hub 4-0:1.0: 2 ports detected
[17179583.812000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 177
[17179583.812000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179583.812000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179583.812000] PCI: cache line size of 128 is not supported by device 0000:00 :1d.7
[17179583.812000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus nu mber 5
[17179583.812000] ehci_hcd 0000:00:1d.7: irq 177, io mem 0xf5100000
[17179583.816000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 D ec 2004
[17179583.816000] hub 5-0:1.0: USB hub found
[17179583.816000] hub 5-0:1.0: 8 ports detected
[17179583.920000] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[17179583.920000] ACPI: PCI Interrupt 0000:03:02.0[A] -> GSI 18 (level, low) -> IRQ 185
[17179583.968000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[185]  MMIO=[f400 e000-f400e7ff]  Max Packet=[2048]
[17179583.968000] ACPI: PCI Interrupt 0000:03:06.2[B] -> GSI 23 (level, low) -> IRQ 177
[17179584.020000] ohci1394: fw-host1: OHCI-1394 1.1 (PCI): IRQ=[177]  MMIO=[f400 c000-f400c7ff]  Max Packet=[2048]
[17179584.052000] Probing IDE interface ide3...
[17179584.772000] Attempting manual resume
[17179584.796000] EXT3-fs: mounted filesystem with ordered data mode.
[17179584.816000] kjournald starting.  Commit interval 5 seconds
[17179585.240000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00508d0000d077cb ]
[17179585.512000] ieee1394: Host added: ID:BUS[1-00:1023]  GUID[00023c015103cfbd ]
[17179593.696000] sd 2:0:0:0: Attached scsi generic sg0 type 0
[17179593.696000] sd 3:0:0:0: Attached scsi generic sg1 type 0
[17179594.968000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179594.972000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179595.084000] hw_random: RNG not detected
[17179595.092000] Linux agpgart interface v0.101 (c) Dave Jones
[17179595.092000] agpgart: Detected an Intel i875 Chipset.
[17179595.100000] agpgart: AGP aperture is 256M @ 0xd0000000
[17179595.200000] nvidia: module license 'NVIDIA' taints kernel.
[17179595.200000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 193
[17179595.200000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8762  Mon Ma y 15 13:06:38 PDT 2006
[17179595.884000] Intel(R) PRO/1000 Network Driver - version 7.0.33-k2
[17179595.884000] Copyright (c) 1999-2005 Intel Corporation.
[17179595.884000] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 18 (level, low) -> IRQ 185
[17179595.884000] PCI: Setting latency timer of device 0000:02:01.0 to 64
[17179596.152000] e1000: 0000:02:01.0: e1000_probe: (PCI:33MHz:32-bit) 00:50:8d: d1:77:cb
[17179596.228000] input: PC Speaker as /class/input/input1
[17179596.300000] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[17179596.316000] gameport: EMU10K1 is pci0000:03:06.1/gameport0, io 0x8800, spe ed 1193kHz
[17179596.592000] Real Time Clock Driver v1.12
[17179596.768000] ACPI: PCI Interrupt 0000:03:06.0[A] -> GSI 22 (level, low) -> IRQ 201
[17179596.772000] Installing spdif_bug patch: Audigy 2 ZS [SB0350]
[17179596.812000] Floppy drive(s): fd0 is 1.44M
[17179596.824000] parport: PnPBIOS parport detected.
[17179596.824000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[17179596.828000] FDC 0 is a post-1991 82077
[17179596.840000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 209
[17179596.840000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[17179597.156000] intel8x0_measure_ac97_clock: measured 1511993770 usecs
[17179597.156000] intel8x0: measured clock 1 rejected
[17179597.156000] intel8x0: clocking to 48000
[17179597.604000] lp0: using parport0 (interrupt-driven).
[17179597.632000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[17179597.632000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1 )
[17179597.632000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179597.688000] Adding 4192956k swap on /dev/sda3.  Priority:-1 extents:1 acro ss:4192956k
[17179597.844000] e1000: eth0: e1000_watchdog_task: NIC Link is Up 100 Mbps Full  Duplex
[17179597.844000] EXT3 FS on sda2, internal journal
[17179597.868000] input: ImExPS/2 Generic Explorer Mouse as /class/input/input2
[17179597.880000] ts: Compaq touchscreen protocol output
[17179598.072000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179598.072000] md: bitmap version 4.39
[17179598.432000] NET: Registered protocol family 17
[17179598.664000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@ redhat.com
[17179600.192000] cdrom: open failed.
[17179604.904000] NET: Registered protocol family 10
[17179604.904000] lo: Disabled Privacy Extensions
[17179604.904000] IPv6 over IPv4 tunneling driver
[17179607.552000] NTFS driver 2.1.25 [Flags: R/O MODULE].
[17179607.604000] NTFS volume version 3.1.
[17179612.988000] ACPI: Power Button (FF) [PWRF]
[17179612.988000] ACPI: Power Button (CM) [PWRB]
[17179613.072000] ibm_acpi: ec object not found
[17179613.100000] pcc_acpi: loading...
[17179614.968000] eth0: no IPv6 routers present
[17179617.504000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[17179617.504000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[17179617.504000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[17179618.040000] ppdev: user-space parallel port driver
[17179618.548000] apm: BIOS not found.
[17179624.372000] Bluetooth: Core ver 2.8
[17179624.372000] NET: Registered protocol family 31
[17179624.372000] Bluetooth: HCI device and connection manager initialized
[17179624.372000] Bluetooth: HCI socket layer initialized
[17179624.400000] Bluetooth: L2CAP ver 2.8
[17179624.400000] Bluetooth: L2CAP socket layer initialized
[17179624.412000] Bluetooth: RFCOMM socket layer initialized
[17179624.412000] Bluetooth: RFCOMM TTY layer initialized
[17179624.412000] Bluetooth: RFCOMM ver 1.7
[17179631.328000] ISO 9660 Extensions: Microsoft Joliet Level 1
[17179631.328000] ISOFS: changing to secondary root

```

Thanks,

--keith.

---

### Post by kfb on 2006-07-09
*bump*

Seriously, this can't be that hard.  Even if someone would point me to the right page, but searching for 'large hard drive support' has gotten me nothing.  Please.  I just need some quick help.  I don't even know how to edit the kernel config in ubuntu.  Could someone at least tell me that?

---

