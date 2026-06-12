---
title: "Very long boot with Hardy - please help ..."
date: 2008-09-24
forum: Hardware
---

### Post by Houchy on 2008-09-24
Hi,

I'm experiencing unusual long boot time after my new install of Hardy 8.04.

First I have like many other people this message at startup saying :

```
MP-BIOS bug: 8254 timer not connected to IO-APIC
```
I don't really want to use the no-apic option to solve this.

Here after is my full dmesg dump :

```
  1)
[    0.000000] ACPI: MCFG 3FEF7880, 003C (r1 RS480  AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: APIC 3FEF7540, 0068 (r1 RS480  AWRDACPI 42302E31 AWRD        0)
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:7 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3ff00000:a0100000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259827
[    0.000000] Kernel command line: root=UUID=fe298933-90b8-4470-b3e9-be21f2d4a129 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2405.607 MHz processor.
[   17.788918] Console: colour VGA+ 80x25
[   17.788921] console [tty0] enabled
[   17.789367] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   17.789749] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   17.809042] Memory: 1026000k/1047488k available (2157k kernel code, 20828k reserved, 998k data, 364k init, 129984k highmem)
[   17.809048] virtual kernel memory layout:
[   17.809049]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   17.809050]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   17.809051]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   17.809052]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   17.809052]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
[   17.809053]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
[   17.809054]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
[   17.809057] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   17.809085] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   17.888981] Calibrating delay using timer specific routine.. 4815.74 BogoMIPS (lpj=9631492)
[   17.889005] Security Framework initialized
[   17.889011] SELinux:  Disabled at boot.
[   17.889025] AppArmor: AppArmor initialized
[   17.889028] Failure registering capabilities with primary security module.
[   17.889035] Mount-cache hash table entries: 512
[   17.889144] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001 00000000
[   17.889151] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   17.889153] CPU: L2 Cache: 1024K (64 bytes/line)
[   17.889155] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001 00000000
[   17.889164] Compat vDSO mapped to ffffe000.
[   17.889174] Checking 'hlt' instruction... OK.
[   17.905199] SMP alternatives: switching to UP code
[   17.906116] Freeing SMP alternatives: 11k freed
[   17.906207] Early unpacking initramfs... done
[   18.172846] ACPI: Core revision 20070126
[   18.172890] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   18.269828] CPU0: AMD Athlon(tm) 64 Processor 4000+ stepping 01
[   18.269847] Total of 1 processors activated (4815.74 BogoMIPS).
[   18.270222] ENABLING IO-APIC IRQs
[   18.270474] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   18.310147] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   18.310192] ...trying to set up timer (IRQ0) through the 8259A ...  failed.
[   18.310193] ...trying to set up timer as Virtual Wire IRQ... works.
[   18.456130] Brought up 1 CPUs
[   18.456185] CPU0 attaching sched-domain:
[   18.456187]  domain 0: span 01
[   18.456188]   groups: 01
[   18.456312] net_namespace: 64 bytes
[   18.456317] Booting paravirtualized kernel on bare hardware
[   18.456681] Time: 19:43:51  Date: 09/24/08
[   18.456699] NET: Registered protocol family 16
[   18.456818] EISA bus registered
[   18.456845] ACPI: bus type pci registered
[   18.489269] PCI: PCI BIOS revision 3.00 entry at 0xfab70, last bus=4
[   18.489271] PCI: Using configuration type 1
[   18.489272] Setting up standard PCI resources
[   18.492572] ACPI: EC: Look up EC in DSDT
[   18.509109] ACPI: Interpreter enabled
[   18.509114] ACPI: (supports S0 S3 S4 S5)
[   18.509125] ACPI: Using IOAPIC for interrupt routing
[   18.512362] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   18.513991] PCI: Transparent bridge - 0000:00:14.4
[   18.514019] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   18.514151] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   18.530052] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   18.530117] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   18.530181] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   18.530244] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   18.530307] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   18.530370] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 *11)
[   18.530433] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *10 11)
[   18.530496] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11)
[   18.530569] Linux Plug and Play Support v0.97 (c) Adam Belay
[   18.530587] pnp: PnP ACPI init
[   18.530591] ACPI: bus type pnp registered
[   18.532820] pnpacpi: exceeded the max number of mem resources: 12
[   18.532853] pnp: PnP ACPI: found 15 devices
[   18.532855] ACPI: ACPI bus type pnp unregistered
[   18.532857] PnPBIOS: Disabled by ACPI PNP
[   18.532987] PCI: Using ACPI for IRQ routing
[   18.532988] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   18.639827] NET: Registered protocol family 8
[   18.639828] NET: Registered protocol family 20
[   18.639873] AppArmor: AppArmor Filesystem Enabled
[   18.643797] Time: tsc clocksource has been installed.
[   18.651805] system 00:01: ioport range 0x140-0x15f has been reserved
[   18.651807] system 00:01: ioport range 0x228-0x22f has been reserved
[   18.651809] system 00:01: ioport range 0x4d6-0x4d6 has been reserved
[   18.651811] system 00:01: ioport range 0xc00-0xc01 has been reserved
[   18.651813] system 00:01: ioport range 0xc14-0xc14 has been reserved
[   18.651815] system 00:01: ioport range 0xc50-0xc52 has been reserved
[   18.651817] system 00:01: ioport range 0xc6c-0xc6d has been reserved
[   18.651819] system 00:01: ioport range 0xc6f-0xc6f has been reserved
[   18.651821] system 00:01: ioport range 0xcd4-0xcdf has been reserved
[   18.651823] system 00:01: ioport range 0x4000-0x40fe has been reserved
[   18.651825] system 00:01: ioport range 0x4210-0x4217 has been reserved
[   18.651830] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[   18.651834] system 00:06: ioport range 0x220-0x225 has been reserved
[   18.651839] system 00:0d: iomem range 0xe0000000-0xefffffff could not be reserved
[   18.651843] system 00:0e: iomem range 0xd0000-0xd3fff has been reserved
[   18.651846] system 00:0e: iomem range 0xf0000-0xf7fff could not be reserved
[   18.651848] system 00:0e: iomem range 0xf8000-0xfbfff could not be reserved
[   18.651850] system 00:0e: iomem range 0xfc000-0xfffff could not be reserved
[   18.651852] system 00:0e: iomem range 0x3ff00000-0x3fffffff has been reserved
[   18.651854] system 00:0e: iomem range 0x3fef0000-0x3fefffff could not be reserved
[   18.651856] system 00:0e: iomem range 0xffff0000-0xffffffff could not be reserved
[   18.651858] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[   18.651861] system 00:0e: iomem range 0x100000-0x3feeffff could not be reserved
[   18.651863] system 00:0e: iomem range 0x0-0x0 could not be reserved
[   18.651865] system 00:0e: iomem range 0xfec00000-0xfec00fff could not be reserved
[   18.651867] system 00:0e: iomem range 0xfee00000-0xfee00fff could not be reserved
[   18.682080] PCI: Bridge: 0000:00:02.0
[   18.682082]   IO window: e000-efff
[   18.682084]   MEM window: fde00000-fdefffff
[   18.682086]   PREFETCH window: d0000000-dfffffff
[   18.682089] PCI: Bridge: 0000:00:06.0
[   18.682090]   IO window: d000-dfff
[   18.682092]   MEM window: fdd00000-fddfffff
[   18.682094]   PREFETCH window: fda00000-fdafffff
[   18.682096] PCI: Bridge: 0000:00:07.0
[   18.682098]   IO window: c000-cfff
[   18.682100]   MEM window: fd900000-fd9fffff
[   18.682102]   PREFETCH window: fd800000-fd8fffff
[   18.682104] PCI: Bridge: 0000:00:14.4
[   18.682107]   IO window: b000-bfff
[   18.682112]   MEM window: fdc00000-fdcfffff
[   18.682116]   PREFETCH window: fdb00000-fdbfffff
[   18.682127] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   18.682133] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   18.682138] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   18.682152] NET: Registered protocol family 2
[   18.719730] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   18.719948] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   18.720794] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   18.721209] TCP: Hash tables configured (established 131072 bind 65536)
[   18.721211] TCP reno registered
[   18.731772] checking if image is initramfs... it is
[   19.182946] Switched to high resolution mode on CPU 0
[   19.245163] Freeing initrd memory: 7726k freed
[   19.245597] audit: initializing netlink socket (disabled)
[   19.245607] audit(1222285431.192:1): initialized
[   19.245714] highmem bounce pool size: 64 pages
[   19.246903] VFS: Disk quotas dquot_6.5.1
[   19.246952] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   19.247041] io scheduler noop registered
[   19.247042] io scheduler anticipatory registered
[   19.247044] io scheduler deadline registered
[   19.247051] io scheduler cfq registered (default)
[   19.247056] PCI: MSI quirk detected. MSI deactivated.
[   19.302732] Boot video device is 0000:01:00.0
[   19.302802] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   19.302819] assign_interrupt_mode Found MSI capability
[   19.302821] Allocate Port Service[0000:00:02.0:pcie00]
[   19.302865] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   19.302881] assign_interrupt_mode Found MSI capability
[   19.302882] Allocate Port Service[0000:00:06.0:pcie00]
[   19.302926] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   19.302942] assign_interrupt_mode Found MSI capability
[   19.302944] Allocate Port Service[0000:00:07.0:pcie00]
[   19.303075] isapnp: Scanning for PnP cards...
[   19.656986] isapnp: No Plug & Play device found
[   19.674943] Real Time Clock Driver v1.12ac
[   19.675012] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   19.675151] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   19.675293] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   19.675711] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   19.676210] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   19.676262] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   19.676320] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   19.678663] serio: i8042 KBD port at 0x60,0x64 irq 1
[   19.678666] serio: i8042 AUX port at 0x60,0x64 irq 12
[   19.682236] mice: PS/2 mouse device common for all mice
[   19.682310] EISA: Probing bus 0 at eisa.0
[   19.682329] Cannot allocate resource for EISA slot 4
[   19.682347] EISA: Detected 0 cards.
[   19.682349] cpuidle: using governor ladder
[   19.682351] cpuidle: using governor menu
[   19.682416] NET: Registered protocol family 1
[   19.682433] Using IPI No-Shortcut mode
[   19.682458] registered taskstats version 1
[   19.682553]   Magic number: 8:522:749
[   19.682556]   hash matches device ttyS0
[   19.682680] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   19.682682] EDD information not available.
[   19.683006] Freeing unused kernel memory: 364k freed
[   19.714048] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   20.873448] fuse init (API version 7.9)
[   20.885992] ACPI: Fan [FAN] (on)
[   20.890971] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   20.892918] ACPI: Thermal Zone [THRM] (40 C)
[   21.374952] SCSI subsystem initialized
[   21.403276] libata version 3.00 loaded.
[   21.419321] sata_sil24 0000:03:00.0: version 1.1
[   21.419354] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 19 (level, low) -> IRQ 16
[   21.419413] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   21.433949] scsi0 : sata_sil24
[   21.455922] scsi1 : sata_sil24
[   21.455967] ata1: SATA max UDMA/100 host m128@0xfd9ff000 port 0xfd9f8000 irq 16
[   21.455971] ata2: SATA max UDMA/100 host m128@0xfd9ff000 port 0xfd9fa000 irq 16
[   21.480230] usbcore: registered new interface driver usbfs
[   21.480248] usbcore: registered new interface driver hub
[   21.487168] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   21.487172] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   21.496529] usbcore: registered new device driver usb
[   21.511113] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   21.583016] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   21.690678] FDC 0 is a post-1991 82077
[   23.531798] ata1: SATA link down (SStatus 0 SControl 0)
[   25.608395] ata2: SATA link down (SStatus 0 SControl 0)
[   25.608532] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 23 (level, low) -> IRQ 17
[   25.608580] ACPI: PCI interrupt for device 0000:00:11.0 disabled
[   25.608605] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 18
[   25.608627] ACPI: PCI interrupt for device 0000:00:12.0 disabled
[   25.608649] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 19
[   25.608670] ACPI: PCI interrupt for device 0000:00:14.1 disabled
[   25.610584] ATIIXP: IDE controller (0x1002:0x4376 rev 0x80) at  PCI slot 0000:00:14.1
[   25.610596] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 19
[   25.610601] ATIIXP: not 100% native mode: will probe irqs later
[   25.610616]     ide0: BM-DMA at 0xf400-0xf407, BIOS settings: hda:pio, hdb:pio
[   25.610628]     ide1: BM-DMA at 0xf408-0xf40f, BIOS settings: hdc:DMA, hdd:pio
[   25.610636] Probing IDE interface ide0...
[   26.175456] Probing IDE interface ide1...
[   27.581569] hdc: TSSTcorpCD/DVDW SH-S182D, ATAPI CD/DVD-ROM drive
[   27.581595] hdc: host max PIO4 wanted PIO255(auto-tune) selected PIO4
[   27.581893] hdc: UDMA/33 mode selected
[   27.582346] ide1 at 0x170-0x177,0x376 on irq 15
[   27.586952] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 16
[   27.586963] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   27.587165] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   27.587178] ohci_hcd 0000:00:13.0: irq 16, io mem 0xfe02d000
[   27.645110] usb usb1: configuration #1 chosen from 1 choice
[   27.645127] hub 1-0:1.0: USB hub found
[   27.645135] hub 1-0:1.0: 4 ports detected
[   27.748942] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 16
[   27.748952] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   27.748966] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   27.748978] ohci_hcd 0000:00:13.1: irq 16, io mem 0xfe02c000
[   27.808818] usb usb2: configuration #1 chosen from 1 choice
[   27.808835] hub 2-0:1.0: USB hub found
[   27.808842] hub 2-0:1.0: 4 ports detected
[   27.912819] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 16
[   27.912827] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   27.912841] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   27.912890] ehci_hcd 0000:00:13.2: irq 16, io mem 0xfe02b000
[   28.052381] usb 1-4: new full speed USB device using ohci_hcd and address 2
[   28.064360] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   28.064441] usb usb3: configuration #1 chosen from 1 choice
[   28.064458] hub 3-0:1.0: USB hub found
[   28.064462] hub 3-0:1.0: 8 ports detected
[   28.168379] 8139cp 0000:04:05.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   28.168383] 8139cp 0000:04:05.0: Try the "8139too" driver instead.
[   28.170554] ACPI: PCI Interrupt 0000:04:06.0[A] -> GSI 23 (level, low) -> IRQ 17
[   28.223235] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[17]  MMIO=[fdcfe000-fdcfe7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   28.228396] sata_sil 0000:00:11.0: version 2.3
[   28.228427] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 23 (level, low) -> IRQ 17
[   28.229443] 8139too Fast Ethernet driver 0.9.28
[   28.229916] scsi2 : sata_sil
[   28.230280] scsi3 : sata_sil
[   28.230301] ata3: SATA max UDMA/100 mmio m512@0xfe02f000 tf 0xfe02f080 irq 17
[   28.230305] ata4: SATA max UDMA/100 mmio m512@0xfe02f000 tf 0xfe02f0c0 irq 17
[   28.539590] ata3: SATA link down (SStatus 0 SControl 310)
[   28.851099] ata4: SATA link down (SStatus 0 SControl 310)
[   28.851156] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 18
[   28.851226] scsi4 : sata_sil
[   28.851374] scsi5 : sata_sil
[   28.851394] ata5: SATA max UDMA/100 mmio m512@0xfe02e000 tf 0xfe02e080 irq 18
[   28.851398] ata6: SATA max UDMA/100 mmio m512@0xfe02e000 tf 0xfe02e0c0 irq 18
[   29.202493] usb 1-4: new full speed USB device using ohci_hcd and address 3
[   29.318332] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   29.349703] ata5.00: ATA-7: WDC WD5000AAKS-75TMA0, 12.01C01, max UDMA/133
[   29.349706] ata5.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   29.363463] ata5.00: configured for UDMA/100
[   29.417275] usb 1-4: configuration #1 chosen from 1 choice
[   29.510073] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00000ae6ff379538]
[   29.673732] ata6: SATA link down (SStatus 0 SControl 310)
[   29.673819] scsi 4:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-7 12.0 PQ: 0 ANSI: 5
[   29.675131] ACPI: PCI Interrupt 0000:04:05.0[A] -> GSI 22 (level, low) -> IRQ 18
[   29.676207] eth0: RealTek RTL8139 at 0xbc00, 00:14:2a:ac:84:74, IRQ 18
[   29.676209] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   29.688931] hdc: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache
[   29.688937] Uniform CD-ROM driver Revision: 3.20
[   29.689367] Driver 'sd' needs updating - please use bus_type methods
[   29.689429] sd 4:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   29.689438] sd 4:0:0:0: [sda] Write Protect is off
[   29.689440] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   29.689454] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.689488] sd 4:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   29.689494] sd 4:0:0:0: [sda] Write Protect is off
[   29.689496] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   29.689507] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.689509]  sda: sda1 sda3 <<6>usb 2-4: new full speed USB device using ohci_hcd and address 2
[   29.730729]  sda5 sda6 > sda4
[   29.730823] sd 4:0:0:0: [sda] Attached SCSI disk
[   29.735624] sd 4:0:0:0: Attached scsi generic sg0 type 0
[   29.926660] usb 2-4: configuration #1 chosen from 1 choice
[   30.082658] Attempting manual resume
[   30.082661] swsusp: Resume From Partition 8:5
[   30.082663] PM: Checking swsusp image.
[   30.082845] PM: Resume from disk failed.
[   30.127337] kjournald starting.  Commit interval 5 seconds
[   30.127347] EXT3-fs: mounted filesystem with ordered data mode.
[   37.647562] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   37.902033] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   37.951676] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   38.035263] Linux agpgart interface v0.102
[   38.077271] irda_init()
[   38.077287] NET: Registered protocol family 23
[   38.155890] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   38.183143] input: Power Button (FF) as /devices/virtual/input/input3
[   38.223748] ACPI: Power Button (FF) [PWRF]
[   38.223795] input: Power Button (CM) as /devices/virtual/input/input4
[   38.255683] ACPI: Power Button (CM) [PWRB]
[   38.319600] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   38.573042] input: ImExPS/2 Logitech MX Mouse as /devices/platform/i8042/serio1/input/input5
[   38.602952] parport_pc 00:0a: reported by Plug and Play ACPI
[   38.603025] parport0: PC-style at 0x378, irq 7 [PCSPP]
[   38.978705] ndiswrapper: driver wg311v3 (NETGEAR,12/30/2005,3.2.3.2) loaded
[   38.978871] ACPI: PCI Interrupt 0000:04:01.0[A] -> GSI 21 (level, low) -> IRQ 21
[   38.979911] ndiswrapper: using IRQ 21
[   39.254249] wlan0: ethernet device 00:1b:2f:2e:94:54 using NDIS driver: wg311v3, version: 0x3020007, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 11AB:1FAA.5.conf
[   39.254263] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   39.270106] usbcore: registered new interface driver ndiswrapper
[   39.597534] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 20
[   39.597546] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   39.597579] sky2 0000:02:00.0: v1.20 addr 0xfddfc000 irq 20 Yukon-EC (0xb6) rev 2
[   39.597823] sky2 eth1: addr 00:14:2a:a7:69:13
[   39.811879] [fglrx] Maximum main memory to use for locked dma buffers: 928 MBytes.
[   39.811906] [fglrx] ASYNCIO init succeed!
[   39.812087] [fglrx] PAT is enabled successfully!
[   39.812738] [fglrx] module loaded - fglrx 8.47.3 [Mar 29 2008] on minor 0
[   39.854211] usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x03F0 pid 0xC302
[   39.854226] usbcore: registered new interface driver usblp
[   39.894002] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 19
[   39.918661] hda_codec: Unknown model for ALC880, trying auto-probe from BIOS...
[   41.044844] NET: Registered protocol family 17
[   41.184769] lp0: using parport0 (interrupt-driven).
[   41.239821] Adding 1028152k swap on /dev/sda5.  Priority:-1 extents:1 across:1028152k
[   41.773951] EXT3 FS on sda6, internal journal
[   41.874548] device-mapper: uevent: version 1.0.3
[   41.874570] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
[   42.509493] NET: Registered protocol family 10
[   42.509681] lo: Disabled Privacy Extensions
[   42.510121] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   43.819714] ip_tables: (C) 2000-2006 Netfilter Core Team
[   45.352272] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   45.384252] ndiswrapper (NdisMIndicateStatus:2102): unrecognized PMKID ignored
[   46.054541] No dock devices found.
[   46.273075] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 4000+ processors (1 cpu cores) (version 2.20.00)
[   46.273108] powernow-k8:    0 : fid 0x10 (2400 MHz), vid 0x6
[   46.273110] powernow-k8:    1 : fid 0xe (2200 MHz), vid 0x8
[   46.273111] powernow-k8:    2 : fid 0xc (2000 MHz), vid 0xa
[   46.273113] powernow-k8:    3 : fid 0xa (1800 MHz), vid 0xc
[   46.273114] powernow-k8:    4 : fid 0x2 (1000 MHz), vid 0x12
[   46.943876] ppdev: user-space parallel port driver
[   47.093137] audit(1222278259.984:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5335 profile="/usr/sbin/cupsd" namespace="default"
[   47.150361] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   47.150366] apm: overridden by ACPI.
[   64.975316] Marking TSC unstable due to: cpufreq changes.
[   64.980248] Time: acpi_pm clocksource has been installed.
[   65.414740] Clocksource tsc unstable (delta = -110027523 ns)
[   65.450698] Bluetooth: Core ver 2.11
[   65.451409] NET: Registered protocol family 31
[   65.451412] Bluetooth: HCI device and connection manager initialized
[   65.451486] Bluetooth: HCI socket layer initialized
[   65.531698] Bluetooth: L2CAP ver 2.9
[   65.531703] Bluetooth: L2CAP socket layer initialized
[   65.568715] Bluetooth: RFCOMM socket layer initialized
[   65.568731] Bluetooth: RFCOMM TTY layer initialized
[   65.568733] Bluetooth: RFCOMM ver 1.8
[  121.030842] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 18 (level, low) -> IRQ 20
[   51.611699] [fglrx] Reserve Block - 0 offset =  0X7ffb000 length = 0X5000
[   51.611704] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
[   51.611707] [fglrx] Reserve Block - 2 offset =  0Xffff000 length = 0X1000
[   51.611709] [fglrx] Reserve Block - 3 offset =  0Xffbf000 length = 0X40000
[   51.813957] [fglrx] interrupt source 20008000 successfully enabled
[   51.813962] [fglrx] enable ID = 0x00000008
[   51.813970] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
[  127.868969] wlan0: no IPv6 routers present
[  133.738447] hda-intel: Invalid position buffer, using LPIB read method instead.
[  136.666621] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:593: hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x306f000a
[   57.637406] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:600: hda_intel: azx_get_response timeout, switching to single_cmd mode: last cmd=0x306f000a
```

There are 2 clear stops at 64sec and 121sec

Can anybody help me debugging this please ...
Thank you in advance.
Houchy

---

### Post by Houchy on 2008-09-26
Up ...
Thanks for your help.

---

### Post by Houchy on 2008-09-26
one more up.

Ubuntu is driving me nuts, so slow to start up, turn off, suspend/hibernate that doesn't work properly, or when it does, the sound doesn't work anymore, keyboard layout settings not being saved, wifi configuration not beeing saved, and I spent so many hours trying to fix everything else that didn't work to begin with ...

I had better expectations ...

---

### Post by Houchy on 2008-09-27
Up

---

### Post by Houchy on 2008-09-28
UP
last try ...

---

