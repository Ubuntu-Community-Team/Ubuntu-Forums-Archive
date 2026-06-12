---
title: "usb devies are not detected on an LG XNOTE notebook"
date: 2008-01-21
forum: Hardware &amp; Laptops
---

### Post by gobucks747 on 2008-01-21
I just installed kubuntu, and my usb drives are not being detected. When I livecd'ed it before the install, they worked, but after the install they do not work. 

lsusb yields
steveny@steveny-laptop:~$ lsusb
Bus 002 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
steveny@steveny-laptop:~$
 
and dmesg yields

steveny@steveny-laptop:~$ dmesg
[17179569.184000] Linux version 2.6.15-51-386 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Dec 6 20:20:49 UTC 2007
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000dc000 - 00000000000e0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 0000000037e90000 (usable)
[17179569.184000]  BIOS-e820: 0000000037e90000 - 0000000037e9e000 (ACPI data)
[17179569.184000]  BIOS-e820: 0000000037e9e000 - 0000000037f00000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 0000000037f00000 - 0000000038000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 894MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f7fb0
[17179569.184000] On node 0 totalpages: 229008
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 224912 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI present.
[17179569.184000] ATI board detected. Disabling timer routing over 8254.
[17179569.184000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f7f80
[17179569.184000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x37e972b5
[17179569.184000] ACPI: FADT (v001 LGE    DEBORAHR 0x06040000 LGE  0x000f4240) @ 0x37e9def2
[17179569.184000] ACPI: MADT (v001 PTLTD         APIC   0x06040000  LTP 0x00000000) @ 0x37e9df66
[17179569.184000] ACPI: MCFG (v001 PTLTD    MCFG   0x06040000  LTP 0x00000000) @ 0x37e9dfc4
[17179569.184000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20050228) @ 0x37e972e9
[17179569.184000] ACPI: DSDT (v001    LGE DEBORAHR 0x06040000 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x8008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:14 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[17179569.184000] Processor #1 6:14 APIC version 20
[17179569.184000] WARNING: NR_CPUS limit of 1 reached.  Processor ignored.
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 40000000 (gap: 38000000:a8000000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/sda1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[17179569.184000] Detected 1666.892 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.948000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179569.948000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.980000] Memory: 897452k/916032k available (1977k kernel code, 17948k reserved, 605k data, 288k init, 0k highmem)
[17179569.980000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179570.060000] Calibrating delay using timer specific routine.. 3340.63 BogoMIPS (lpj=6681272)
[17179570.060000] Security Framework v1.0.0 initialized
[17179570.060000] SELinux:  Disabled at boot.
[17179570.060000] Mount-cache hash table entries: 512
[17179570.060000] CPU: After generic identify, caps: bfe9fbff 00000000 00000000 00000000 0000c189 00000000 00000000
[17179570.060000] CPU: After vendor identify, caps: bfe9fbff 00000000 00000000 00000000 0000c189 00000000 00000000
[17179570.060000] monitor/mwait feature present.
[17179570.060000] using mwait in idle threads.
[17179570.060000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179570.060000] CPU: L2 cache: 2048K
[17179570.060000] CPU: After all inits, caps: bfe9fbff 00000000 00000000 00000040 0000c189 00000000 00000000
[17179570.060000] mtrr: v2.0 (20020519)
[17179570.060000] CPU: Intel Genuine Intel(R) CPU           T2300  @ 1.66GHz stepping 08
[17179570.060000] Enabling fast FPU save and restore... done.
[17179570.060000] Enabling unmasked SIMD FPU exception support... done.
[17179570.060000] Checking 'hlt' instruction... OK.
[17179570.076000] checking if image is initramfs... it is
[17179571.136000] Freeing initrd memory: 6666k freed
[17179571.160000] ACPI: Looking for DSDT ... not found!
[17179571.172000] ENABLING IO-APIC IRQs
[17179571.172000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[17179571.316000] NET: Registered protocol family 16
[17179571.316000] EISA bus registered
[17179571.316000] ACPI: bus type pci registered
[17179571.316000] PCI: PCI BIOS revision 2.10 entry at 0xfd644, last bus=8
[17179571.316000] PCI: Using MMCONFIG
[17179571.316000] ACPI: Subsystem revision 20051216
[17179571.320000] ACPI: Interpreter enabled
[17179571.320000] ACPI: Using IOAPIC for interrupt routing
[17179571.320000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179571.320000] PCI: Probing PCI hardware (bus 00)
[17179571.324000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:14.1
[17179571.324000] Boot video device is 0000:01:05.0
[17179571.324000] PCI: Transparent bridge - 0000:00:14.4
[17179571.324000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179571.328000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB7_._PRT]
[17179571.332000] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[17179571.332000] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[17179571.332000] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[17179571.332000] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[17179571.332000] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[17179571.332000] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[17179571.332000] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[17179571.332000] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[17179571.332000] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 5 7) *0, disabled.
[17179571.336000] ACPI: Embedded Controller [EC] (gpe 29) interrupt mode.
[17179571.336000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[17179571.336000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[17179571.336000] ACPI: Power Resource [CTHT] (off)
[17179571.340000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179571.340000] pnp: PnP ACPI init
[17179571.340000] pnp: PnP ACPI: found 10 devices
[17179571.340000] PnPBIOS: Disabled by ACPI PNP
[17179571.340000] PCI: Using ACPI for IRQ routing
[17179571.340000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179571.340000] PCI: Cannot allocate resource region 2 of device 0000:00:12.0
[17179571.340000] PCI: Cannot allocate resource region 3 of device 0000:00:12.0
[17179571.368000] pnp: 00:08: ioport range 0x1080-0x1080 has been reserved
[17179571.368000] pnp: 00:08: ioport range 0x220-0x22f has been reserved
[17179571.368000] pnp: 00:08: ioport range 0x40b-0x40b has been reserved
[17179571.368000] pnp: 00:08: ioport range 0x4d0-0x4d1 has been reserved
[17179571.368000] PCI: Bridge: 0000:00:01.0
[17179571.368000]   IO window: 9000-9fff
[17179571.368000]   MEM window: c0000000-c00fffff
[17179571.368000]   PREFETCH window: d0000000-dfffffff
[17179571.368000] PCI: Bridge: 0000:00:07.0
[17179571.368000]   IO window: a000-afff
[17179571.368000]   MEM window: c0100000-c01fffff
[17179571.368000]   PREFETCH window: disabled.
[17179571.368000] PCI: Bus 6, cardbus bridge: 0000:05:00.0
[17179571.368000]   IO window: 00002000-000020ff
[17179571.368000]   IO window: 00002400-000024ff
[17179571.368000]   PREFETCH window: 42000000-43ffffff
[17179571.368000]   MEM window: 44000000-45ffffff
[17179571.368000] PCI: Bridge: 0000:00:14.4
[17179571.368000]   IO window: 2000-2fff
[17179571.368000]   MEM window: f0200000-f02fffff
[17179571.368000]   PREFETCH window: f0300000-f03fffff
[17179571.368000] PCI: Setting latency timer of device 0000:00:07.0 to 64
[17179571.368000] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 20 (level, low) -> IRQ 185
[17179571.368000] audit: initializing netlink socket (disabled)
[17179571.368000] audit(1200976427.368:1): initialized
[17179571.372000] VFS: Disk quotas dquot_6.5.1
[17179571.372000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179571.372000] Initializing Cryptographic API
[17179571.372000] io scheduler noop registered
[17179571.372000] io scheduler anticipatory registered
[17179571.372000] io scheduler deadline registered
[17179571.372000] io scheduler cfq registered
[17179571.372000] PCI: Setting latency timer of device 0000:00:07.0 to 64
[17179571.372000] pcie_portdrv_probe->Dev[5a39:1002] has invalid IRQ. Check vendor BIOS
[17179571.372000] assign_interrupt_mode Found MSI capability
[17179571.372000] Allocate Port Service[pcie00]
[17179571.372000] Allocate Port Service[pcie01]
[17179571.372000] Allocate Port Service[pcie03]
[17179571.372000] isapnp: Scanning for PnP cards...
[17179571.728000] isapnp: No Plug & Play device found
[17179571.752000] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[17179571.772000] i8042.c: Detected active multiplexing controller, rev 1.1.
[17179571.784000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[17179571.784000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[17179571.788000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[17179571.788000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[17179571.788000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179571.788000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179571.792000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179571.792000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179571.792000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179571.792000] mice: PS/2 mouse device common for all mice
[17179571.804000] EISA: Probing bus 0 at eisa.0
[17179571.808000] Cannot allocate resource for EISA slot 1
[17179571.808000] Cannot allocate resource for EISA slot 2
[17179571.808000] Cannot allocate resource for EISA slot 8
[17179571.808000] EISA: Detected 0 cards.
[17179571.808000] NET: Registered protocol family 2
[17179571.844000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179571.844000] TCP established hash table entries: 131072 (order: 7, 524288 bytes)
[17179571.844000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[17179571.844000] TCP: Hash tables configured (established 131072 bind 65536)
[17179571.844000] TCP reno registered
[17179571.844000] TCP bic registered
[17179571.844000] NET: Registered protocol family 1
[17179571.844000] NET: Registered protocol family 8
[17179571.844000] NET: Registered protocol family 20
[17179571.844000] Using IPI Shortcut mode
[17179571.844000] ACPI wakeup devices:
[17179571.844000] LID0 PWRB  PB7 LANC OHC1 OHC2 EHCI KBC0  P2P AZLA
[17179571.844000] ACPI: (supports S0 S3 S4 S5)
[17179571.844000] Freeing unused kernel memory: 288k freed
[17179571.912000] vga16fb: initializing
[17179571.912000] vga16fb: mapped to 0xc00a0000
[17179572.032000] Console: switching to colour frame buffer device 80x25
[17179572.032000] fb0: VGA16 VGA frame buffer device
[17179572.056000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179573.076000] Capability LSM initialized
[17179573.216000] ACPI: Fan [FAN0] (off)
[17179573.224000] ACPI: CPU0 (power states: C1[C1] C3[C3])
[17179573.224000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179573.228000] ACPI: Thermal Zone [TZ1] (40 C)
[17179573.800000] SCSI subsystem initialized
[17179573.804000] ACPI: bus type scsi registered
[17179573.804000] libata version 1.20 loaded.
[17179573.804000] sata_sil 0000:00:12.0: version 0.9
[17179573.804000] PCI: Enabling device 0000:00:12.0 (0005 -> 0007)
[17179573.804000] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 209
[17179573.804000] ata1: SATA max UDMA/100 cmd 0xF8880080 ctl 0xF888008A bmdma 0xF8880000 irq 209
[17179573.804000] ata2: SATA max UDMA/100 cmd 0xF88800C0 ctl 0xF88800CA bmdma 0xF8880008 irq 209
[17179574.172000] ata1: dev 0 cfg 00:045a 49:0f00 82:746b 83:7f69 84:4063 85:f468 86:3d49 87:4063 88:203f 93:0000
[17179574.172000] ata1: dev 0 ATA-7, max UDMA/100, 117210240 sectors: LBA48
[17179574.172000] sata_get_dev_handle: SATA dev addr=0x120000, handle=0xdffea500
[17179574.176000] ata1: dev 0 configured for UDMA/100
[17179574.176000] sata_get_dev_handle: SATA dev addr=0x120000, handle=0xdffea500
[17179574.176000] scsi0 : sata_sil
[17179574.384000] ata2: no device found (phy stat 00000000)
[17179574.384000] scsi1 : sata_sil
[17179574.384000]   Vendor: ATA       Model: HTS541060G9SA00   Rev: MB3O
[17179574.384000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179574.392000] Driver 'sd' needs updating - please use bus_type methods
[17179574.392000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[17179574.392000] SCSI device sda: drive cache: write back
[17179574.396000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[17179574.396000] SCSI device sda: drive cache: write back
[17179574.396000]  sda: sda1 sda2 < sda5 >
[17179574.436000] sd 0:0:0:0: Attached scsi disk sda
[17179574.588000] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[17179574.588000] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 217
[17179574.588000] ATIIXP: chipset revision 128
[17179574.588000] ATIIXP: not 100% native mode: will probe irqs later
[17179574.588000]     ide1: BM-DMA at 0x8468-0x846f, BIOS settings: hdc:DMA, hdd:pio
[17179574.588000] Probing IDE interface ide1...
[17179575.328000] hdc: HL-DT-STCD-RW/DVD DRIVE GCC-4244N, ATAPI CD/DVD-ROM drive
[17179575.664000] ide1 at 0x170-0x177,0x376 on irq 15
[17179575.676000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179575.676000] Uniform CD-ROM driver Revision: 3.20
[17179575.812000] usbcore: registered new driver usbfs
[17179575.812000] usbcore: registered new driver hub
[17179575.812000] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 225
[17179575.812000] ehci_hcd 0000:00:13.2: EHCI Host Controller
[17179575.812000] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
[17179575.812000] ehci_hcd 0000:00:13.2: irq 225, io mem 0xc0506000
[17179575.812000] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179575.812000] hub 1-0:1.0: USB hub found
[17179575.812000] hub 1-0:1.0: 8 ports detected
[17179575.884000] ieee1394: Initialized config rom entry `ip1394'
[17179575.908000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179575.908000] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 225
[17179575.908000] ohci_hcd 0000:00:13.0: OHCI Host Controller
[17179576.112000] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[17179576.112000] ACPI: PCI Interrupt 0000:05:00.2[A] -> GSI 20 (level, low) -> IRQ 185
[17179576.164000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[185]  MMIO=[c0209000-c02097ff]  Max Packet=[2048]
[17179576.208000] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[17179576.208000] ohci_hcd 0000:00:13.0: irq 225, io mem 0xc0504000
[17179576.268000] hub 2-0:1.0: USB hub found
[17179576.268000] hub 2-0:1.0: 4 ports detected
[17179576.372000] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 225
[17179576.372000] ohci_hcd 0000:00:13.1: OHCI Host Controller
[17179576.588000] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[17179576.588000] ohci_hcd 0000:00:13.1: irq 225, io mem 0xc0505000
[17179576.648000] hub 3-0:1.0: USB hub found
[17179576.648000] hub 3-0:1.0: 4 ports detected
[17179576.800000] Probing IDE interface ide0...
[17179577.380000] Attempting manual resume
[17179577.392000] EXT3-fs: INFO: recovery required on readonly filesystem.
[17179577.392000] EXT3-fs: write access will be enabled during recovery.
[17179583.344000] EXT3-fs: sda1: orphan cleanup on readonly fs
[17179583.344000] ext3_orphan_cleanup: deleting unreferenced inode 4653065
[17179583.344000] EXT3-fs: sda1: 1 orphan inode deleted
[17179583.344000] EXT3-fs: recovery complete.
[17179583.344000] kjournald starting.  Commit interval 5 seconds
[17179583.392000] EXT3-fs: mounted filesystem with ordered data mode.
[17179593.288000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179594.828000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179594.832000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179595.268000] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 217
[17179595.468000] Linux agpgart interface v0.101 (c) Dave Jones
[17179596.172000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 19 (level, low) -> IRQ 225
[17179596.172000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[17179596.172000] sky2 v1.4 addr 0xc0100000 irq 225 Yukon-FE (0xb7) rev 1
[17179596.172000] sky2 eth0: addr 00:e0:91:11:3a:98
[17179596.496000] Real Time Clock Driver v1.12
[17179596.496000] input: PC Speaker as /class/input/input1
[17179596.500000] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 20 (level, low) -> IRQ 185
[17179596.500000] Yenta: CardBus bridge found at 0000:05:00.0 [1854:0024]
[17179596.500000] Yenta: Using INTVAL to route CSC interrupts to PCI
[17179596.500000] Yenta: Routing CardBus interrupts to PCI
[17179596.500000] Yenta TI: socket 0000:05:00.0, mfunc 0x01d01002, devctl 0x64
[17179596.520000] sdhci: Secure Digital Host Controller Interface driver, 0.10
[17179596.520000] sdhci: Copyright(c) Pierre Ossman
[17179596.520000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x23aeb3, caps: 0xa04713/0x10008
[17179596.564000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[17179596.732000] Yenta: ISA IRQ mask 0x0ef8, PCI irq 185
[17179596.732000] Socket status: 30000006
[17179596.732000] Yenta: Raising subordinate bus# of parent bus (#05) from #08 to #09
[17179596.732000] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[17179596.732000] cs: IO port probe 0x2000-0x2fff: clean.
[17179596.732000] pcmcia: parent PCI bridge Memory window: 0xf0200000 - 0xf02fffff
[17179596.732000] pcmcia: parent PCI bridge Memory window: 0xf0300000 - 0xf03fffff
[17179596.744000] ACPI: PCI Interrupt 0000:05:00.4[A] -> GSI 20 (level, low) -> IRQ 185
[17179596.792000] sdhci: ============== REGISTER DUMP ==============
[17179596.792000] sdhci: Sys addr: 0x00000000 | Version:  0x00008400
[17179596.792000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
[17179596.792000] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
[17179596.792000] sdhci: Present:  0x00020000 | Host ctl: 0x00000000
[17179596.792000] sdhci: Power:    0x00000000 | Blk gap:  0x00000000
[17179596.792000] sdhci: Walk up:  0x00000000 | Clock:    0x00000002
[17179596.792000] sdhci: Timeout:  0x0000000e | Int stat: 0x00000000
[17179596.792000] sdhci: Int enab: 0x11ff00cf | Sig enab: 0x11ff00cf
[17179596.792000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[17179596.792000] sdhci: Caps:     0x01821090 | Max curr: 0x00000000
[17179596.792000] sdhci: ===========================================
[17179596.844000] mmc0: SDHCI at 0xc020a000 irq 185 DMA
[17179596.940000] sdhci: ============== REGISTER DUMP ==============
[17179596.940000] sdhci: Sys addr: 0x00000000 | Version:  0x00008400
[17179596.940000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
[17179596.940000] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
[17179596.940000] sdhci: Present:  0x00020000 | Host ctl: 0x00000000
[17179596.940000] sdhci: Power:    0x00000000 | Blk gap:  0x00000000
[17179596.940000] sdhci: Walk up:  0x00000000 | Clock:    0x00000002
[17179596.940000] sdhci: Timeout:  0x0000000e | Int stat: 0x00000000
[17179596.940000] sdhci: Int enab: 0x11ff00cf | Sig enab: 0x11ff00cf
[17179596.940000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[17179596.940000] sdhci: Caps:     0x01821090 | Max curr: 0x00000000
[17179596.940000] sdhci: ===========================================
[17179596.992000] mmc1: SDHCI at 0xc0209c00 irq 185 DMA
[17179597.092000] sdhci: ============== REGISTER DUMP ==============
[17179597.092000] sdhci: Sys addr: 0x00000000 | Version:  0x00008400
[17179597.092000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
[17179597.092000] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
[17179597.092000] sdhci: Present:  0x000f0000 | Host ctl: 0x00000000
[17179597.092000] sdhci: Power:    0x00000000 | Blk gap:  0x00000000
[17179597.092000] sdhci: Walk up:  0x00000000 | Clock:    0x00000002
[17179597.092000] sdhci: Timeout:  0x0000000e | Int stat: 0x00000000
[17179597.092000] sdhci: Int enab: 0x11ff00cf | Sig enab: 0x11ff00cf
[17179597.092000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[17179597.092000] sdhci: Caps:     0x01821898 | Max curr: 0x00000000
[17179597.092000] sdhci: ===========================================
[17179597.140000] mmc2: SDHCI at 0xc0209800 irq 185 DMA
[17179597.448000] sky2 eth0: enabling interface
[17179597.824000] ts: Compaq touchscreen protocol output
[17179597.844000] ACPI: PCI Interrupt 0000:05:02.0[A] -> GSI 22 (level, low) -> IRQ 209
[17179597.844000] rt2500 1.1.0 CVS 2005/07/10 [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
[17179597.908000] cs: IO port probe 0x100-0x3af: clean.
[17179597.928000] cs: IO port probe 0x3e0-0x4ff: clean.
[17179597.928000] cs: IO port probe 0x820-0x8ff: excluding 0x878-0x87f
[17179597.928000] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
[17179597.932000] cs: IO port probe 0xa00-0xaff: clean.
[17179598.504000] NET: Registered protocol family 17
[17179599.240000] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control none
[17179599.252000] lp: driver loaded but no devices found
[17179599.304000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[17179599.304000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179599.304000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179599.380000] Adding 2409708k swap on /dev/sda5.  Priority:-1 extents:1 across:2409708k
[17179599.532000] EXT3 FS on sda1, internal journal
[17179599.720000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179599.720000] md: bitmap version 4.39
[17179600.268000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[17179600.908000] cdrom: open failed.
[17179604.728000] NET: Registered protocol family 10
[17179604.728000] lo: Disabled Privacy Extensions
[17179604.728000] IPv6 over IPv4 tunneling driver
[17179608.536000] ACPI: AC Adapter [AC] (on-line)
[17179608.548000] ACPI: Battery Slot [CMB0] (battery present)
[17179608.660000] ACPI: Power Button (FF) [PWRF]
[17179608.660000] ACPI: Sleep Button (CM) [SLPB]
[17179608.660000] ACPI: Lid Switch [LID0]
[17179608.660000] ACPI: Power Button (CM) [PWRB]
[17179608.788000] ibm_acpi: ec object not found
[17179608.824000] pcc_acpi: loading...
[17179608.880000] wmi_add device=dff6c400
[17179608.880000] calling WQBA
[17179608.948000] ACPI: Video Device [VGA] (multi-head: yes  rom: yes  post: no)
[17179612.800000] ppdev: user-space parallel port driver
[17179613.120000] apm: BIOS not found.
[17179613.644000] Bluetooth: Core ver 2.8
[17179613.644000] NET: Registered protocol family 31
[17179613.644000] Bluetooth: HCI device and connection manager initialized
[17179613.644000] Bluetooth: HCI socket layer initialized
[17179613.660000] Bluetooth: L2CAP ver 2.8
[17179613.660000] Bluetooth: L2CAP socket layer initialized
[17179613.684000] Bluetooth: RFCOMM socket layer initialized
[17179613.684000] Bluetooth: RFCOMM TTY layer initialized
[17179613.684000] Bluetooth: RFCOMM ver 1.7
[17179614.736000] eth0: no IPv6 routers present
[17179641.336000] hda-intel: Invalid position buffer, using LPIB read method instead.

Other than these two commands, I am a completely new to this.:(
any help would be appreciated

thank you for your time

---

### Post by gobucks747 on 2008-01-22
someone on IRC got it for me

dmesg | grep usb

then

cat /proc/interrupts

lsusb

then rebooted:)

---

### Post by Yellow Pasque on 2008-01-22
Can you run **cat /proc/cpuinfo** for me? I want to make sure it's recognizing both of your cores.
> [17179569.184000] WARNING: NR_CPUS limit of 1 reached. Processor ignored.

Edit: looks like you need to install the generic kernel.

---

