---
title: "Visual effect can't be reseted."
date: 2008-10-01
forum: General Help
---

### Post by Ideuss on 2008-10-01
Hi there, i've searched about my problem for 2 days. 

In the visual effect choice (None,Normal,Extra) I've changed the normal for the none to see if my batterie will live longer (not worked by the way)

And now I can't go back to normal effects. Got that problem : Visual effects can't be set (sorry for my bad english)

So someone tell me to try Dmseg in the Terminal and to copy my result here. So i'm trying it. 
```


[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Aug 20 22:56:21 UTC 2008 (Ubuntu 2.6.24-19.41-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007f670000 (usable)
[    0.000000]  BIOS-e820: 000000007f670000 - 000000007f700000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007f700000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 1142MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f6a10
[    0.000000] Entering add_active_range(0, 0, 521840) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   521840
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   521840
[    0.000000] On node 0 totalpages: 521840
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2284 pages used for memmap
[    0.000000]   HighMem zone: 290180 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6960 checksum 0
[    0.000000] ACPI: RSDP 000F6960, 0024 (r2 TOSINV)
[    0.000000] ACPI: XSDT 7F678718, 008C (r1 TOSINV TOSINV00  6040000  INV        0)
[    0.000000] ACPI: FACP 7F681BF8, 00F4 (r3 TOSINV TOSINV00  6040000 ALAN        1)
[    0.000000] ACPI: DSDT 7F67A4B1, 76D3 (r2 TOSINV CALISTGA  6040000 INTL 20050624)
[    0.000000] ACPI: FACS 7F682FC0, 0040
[    0.000000] ACPI: APIC 7F681CEC, 0068 (r1 INTEL  CALISTGA  6040000 LOHR       5A)
[    0.000000] ACPI: HPET 7F681D54, 0038 (r1 INTEL  CALISTGA  6040000 LOHR       5A)
[    0.000000] ACPI: MCFG 7F681D8C, 003C (r1 INTEL  CALISTGA  6040000 LOHR       5A)
[    0.000000] ACPI: TCPA 7F681DC8, 0032 (r1 PTLTD  CALISTGA  6040000  PTL        1)
[    0.000000] ACPI: APIC 7F681DFA, 0068 (r1 TOSINV   APIC    6040000  INV        0)
[    0.000000] ACPI: SLIC 7F681E62, 0176 (r1 TOSINV TOSINV00  6040000  INV        0)
[    0.000000] ACPI: BOOT 7F681FD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SSDT 7F679E62, 064F (r1 SataRe  SataPri     1000 INTL 20050624)
[    0.000000] ACPI: SSDT 7F6797D0, 0692 (r1 SataRe  SataSec     1000 INTL 20050624)
[    0.000000] ACPI: SSDT 7F678D30, 025F (r1  PmRef  Cpu0Tst     3000 INTL 20050624)
[    0.000000] ACPI: SSDT 7F678C8A, 00A6 (r1  PmRef  Cpu1Tst     3000 INTL 20050624)
[    0.000000] ACPI: SSDT 7F6787A4, 04E6 (r1  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: DMI detected: Toshiba
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ec00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000dc000
[    0.000000] swsusp: Registered nosave memory region: 00000000000dc000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517764
[    0.000000] Kernel command line: root=UUID=5975a4e4-c7f0-4b03-8e7a-84f85cee1a6b ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1596.031 MHz processor.
[   13.784301] Console: colour VGA+ 80x25
[   13.784308] console [tty0] enabled
[   13.784698] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   13.785218] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   13.981752] Memory: 2056368k/2087360k available (2177k kernel code, 29828k reserved, 1006k data, 368k init, 1169856k highmem)
[   13.981767] virtual kernel memory layout:
[   13.981769]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   13.981771]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   13.981773]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   13.981775]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   13.981777]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   13.981780]       .data : 0xc03204c4 - 0xc041bdc4   (1006 kB)
[   13.981782]       .text : 0xc0100000 - 0xc03204c4   (2177 kB)
[   13.981788] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   13.981854] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   13.982024] hpet clockevent registered
[   14.061959] Calibrating delay using timer specific routine.. 3197.00 BogoMIPS (lpj=6394015)
[   14.061997] Security Framework initialized
[   14.062007] SELinux:  Disabled at boot.
[   14.062032] AppArmor: AppArmor initialized
[   14.062040] Failure registering capabilities with primary security module.
[   14.062056] Mount-cache hash table entries: 512
[   14.062278] Initializing cgroup subsys ns
[   14.062286] Initializing cgroup subsys cpuacct
[   14.062307] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e39d 00000000 00000001 00000000
[   14.062323] monitor/mwait feature present.
[   14.062326] using mwait in idle threads.
[   14.062333] CPU: L1 I cache: 32K, L1 D cache: 32K
[   14.062338] CPU: L2 cache: 2048K
[   14.062343] CPU: Physical Processor ID: 0
[   14.062346] CPU: Processor Core ID: 0
[   14.062350] CPU: After all inits, caps: bfebfbff 20000000 00000000 00003940 0000e39d 00000000 00000001 00000000
[   14.062367] Compat vDSO mapped to ffffe000.
[   14.062392] Checking 'hlt' instruction... OK.
[   14.078717] SMP alternatives: switching to UP code
[   14.082025] Early unpacking initramfs... done
[   14.867343] ACPI: Core revision 20070126
[   14.867437] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   14.924982] CPU0: Intel(R) Core(TM)2 CPU         T5200  @ 1.60GHz stepping 06
[   14.925011] SMP alternatives: switching to SMP code
[   14.926406] Booting processor 1/1 eip 3000
[   14.936891] Initializing CPU#1
[   15.017042] Calibrating delay using timer specific routine.. 3192.13 BogoMIPS (lpj=6384261)
[   15.017056] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e39d 00000000 00000001 00000000
[   15.017066] monitor/mwait feature present.
[   15.017071] CPU: L1 I cache: 32K, L1 D cache: 32K
[   15.017075] CPU: L2 cache: 2048K
[   15.017079] CPU: Physical Processor ID: 0
[   15.017081] CPU: Processor Core ID: 1
[   15.017084] CPU: After all inits, caps: bfebfbff 20000000 00000000 00003940 0000e39d 00000000 00000001 00000000
[   15.018123] CPU1: Intel(R) Core(TM)2 CPU         T5200  @ 1.60GHz stepping 06
[   15.018161] Total of 2 processors activated (6389.13 BogoMIPS).
[   15.018379] ENABLING IO-APIC IRQs
[   15.018605] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   15.165102] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   15.185113] Brought up 2 CPUs
[   15.185155] CPU0 attaching sched-domain:
[   15.185159]  domain 0: span 03
[   15.185163]   groups: 01 02
[   15.185170] CPU1 attaching sched-domain:
[   15.185173]  domain 0: span 03
[   15.185177]   groups: 02 01
[   15.185643] net_namespace: 64 bytes
[   15.185657] Booting paravirtualized kernel on bare hardware
[   15.186585] Time: 12:48:39  Date: 10/01/08
[   15.186638] NET: Registered protocol family 16
[   15.187056] EISA bus registered
[   15.187065] ACPI: bus type pci registered
[   15.187388] PCI: PCI BIOS revision 2.10 entry at 0xfd604, last bus=7
[   15.187393] PCI: Using configuration type 1
[   15.187412] Setting up standard PCI resources
[   15.193462] ACPI: EC: Look up EC in DSDT
[   15.221547] ACPI: BIOS _OSI(Linux) query ignored via DMI
[   15.222671] ACPI: Interpreter enabled
[   15.222677] ACPI: (supports S0 S3 S4 S5)
[   15.222707] ACPI: Using IOAPIC for interrupt routing
[   15.223273] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   15.313818] ACPI: EC: GPE = 0x16, I/O: command/status = 0x66, data = 0x62
[   15.313823] ACPI: EC: driver started in interrupt mode
[   15.313927] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   15.315206] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   15.315214] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   15.316882] PCI: Transparent bridge - 0000:00:1e.0
[   15.317039] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   15.317703] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   15.317991] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   15.318277] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[   15.318588] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   15.445325] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[   15.445554] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   15.445777] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   15.445998] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   15.446218] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[   15.446437] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[   15.446659] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[   15.446879] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   15.447214] ACPI: Power Resource [FN00] (off)
[   15.447331] Linux Plug and Play Support v0.97 (c) Adam Belay
[   15.447398] pnp: PnP ACPI init
[   15.447413] ACPI: bus type pnp registered
[   15.520958] pnp: PnP ACPI: found 10 devices
[   15.520964] ACPI: ACPI bus type pnp unregistered
[   15.520972] PnPBIOS: Disabled by ACPI PNP
[   15.521464] PCI: Using ACPI for IRQ routing
[   15.521470] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   15.592720] NET: Registered protocol family 8
[   15.592725] NET: Registered protocol family 20
[   15.592793] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   15.592802] hpet0: 3 64-bit timers, 14318180 Hz
[   15.593865] AppArmor: AppArmor Filesystem Enabled
[   15.596496] Time: tsc clocksource has been installed.
[   15.596518] Switched to high resolution mode on CPU 0
[   15.596711] Switched to high resolution mode on CPU 1
[   15.609484] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[   15.609491] system 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[   15.609498] system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[   15.609504] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[   15.609510] system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[   15.609516] system 00:01: iomem range 0xfed20000-0xfed3ffff could not be reserved
[   15.609522] system 00:01: iomem range 0xfed40000-0xfed44fff could not be reserved
[   15.609528] system 00:01: iomem range 0xfed45000-0xfed8ffff could not be reserved
[   15.609544] system 00:04: iomem range 0xfed00000-0xfed003ff could not be reserved
[   15.609558] system 00:06: ioport range 0x3e8-0x3ef has been reserved
[   15.609564] system 00:06: ioport range 0x400-0x401 has been reserved
[   15.609569] system 00:06: ioport range 0x680-0x69f has been reserved
[   15.609574] system 00:06: ioport range 0x800-0x80f has been reserved
[   15.609580] system 00:06: ioport range 0x1000-0x107f has been reserved
[   15.609585] system 00:06: ioport range 0x1180-0x11bf has been reserved
[   15.609591] system 00:06: ioport range 0x1640-0x164f has been reserved
[   15.609596] system 00:06: ioport range 0xfe00-0xfe01 has been reserved
[   15.640509] PCI: Bridge: 0000:00:1c.0
[   15.640513]   IO window: disabled.
[   15.640523]   MEM window: disabled.
[   15.640529]   PREFETCH window: disabled.
[   15.640539] PCI: Bridge: 0000:00:1c.1
[   15.640544]   IO window: 2000-2fff
[   15.640554]   MEM window: f0700000-f07fffff
[   15.640561]   PREFETCH window: f0200000-f03fffff
[   15.640571] PCI: Bridge: 0000:00:1c.2
[   15.640577]   IO window: 3000-3fff
[   15.640586]   MEM window: f0800000-f08fffff
[   15.640593]   PREFETCH window: f0400000-f05fffff
[   15.640616] PCI: Bus 8, cardbus bridge: 0000:07:06.0
[   15.640620]   IO window: 00004400-000044ff
[   15.640627]   IO window: 00004800-000048ff
[   15.640636]   PREFETCH window: 88000000-8bffffff
[   15.640643]   MEM window: 8c000000-8fffffff
[   15.640651] PCI: Bridge: 0000:00:1e.0
[   15.640656]   IO window: 4000-4fff
[   15.640666]   MEM window: f0900000-f09fffff
[   15.640673]   PREFETCH window: disabled.
[   15.640720] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
[   15.640732] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   15.640770] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 17
[   15.640780] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   15.640817] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   15.640828] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   15.640850] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   15.640874] PCI: Enabling device 0000:07:06.0 (0000 -> 0003)
[   15.640881] ACPI: PCI Interrupt 0000:07:06.0[A] -> GSI 18 (level, low) -> IRQ 18
[   15.640910] NET: Registered protocol family 2
[   15.677448] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   15.677879] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   15.678741] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   15.679135] TCP: Hash tables configured (established 131072 bind 65536)
[   15.679140] TCP reno registered
[   15.689581] checking if image is initramfs... it is
[   17.234956] Freeing initrd memory: 8508k freed
[   17.235213] Simple Boot Flag at 0x36 set to 0x1
[   17.236618] audit: initializing netlink socket (disabled)
[   17.236646] audit(1222865320.080:1): initialized
[   17.237044] highmem bounce pool size: 64 pages
[   17.241373] VFS: Disk quotas dquot_6.5.1
[   17.241545] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   17.241825] io scheduler noop registered
[   17.241830] io scheduler anticipatory registered
[   17.241834] io scheduler deadline registered
[   17.241857] io scheduler cfq registered (default)
[   17.241874] Boot video device is 0000:00:02.0
[   17.242009] PCI: Firmware left 0000:07:08.0 e100 interrupts enabled, disabling
[   17.242234] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   17.242321] assign_interrupt_mode Found MSI capability
[   17.242396] Allocate Port Service[0000:00:1c.0:pcie00]
[   17.242470] Allocate Port Service[0000:00:1c.0:pcie02]
[   17.242642] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   17.242729] assign_interrupt_mode Found MSI capability
[   17.242798] Allocate Port Service[0000:00:1c.1:pcie00]
[   17.242880] Allocate Port Service[0000:00:1c.1:pcie02]
[   17.243055] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   17.243141] assign_interrupt_mode Found MSI capability
[   17.243211] Allocate Port Service[0000:00:1c.2:pcie00]
[   17.243283] Allocate Port Service[0000:00:1c.2:pcie02]
[   17.243798] isapnp: Scanning for PnP cards...
[   17.598272] isapnp: No Plug & Play device found
[   17.653346] Real Time Clock Driver v1.12ac
[   17.653791] hpet_resources: 0xfed00000 is busy
[   17.653844] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   17.656364] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   17.656501] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   17.656708] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   17.659620] i8042.c: Detected active multiplexing controller, rev 1.1.
[   17.661122] serio: i8042 KBD port at 0x60,0x64 irq 1
[   17.661131] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   17.661136] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   17.661141] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   17.661146] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   17.679567] mice: PS/2 mouse device common for all mice
[   17.679805] EISA: Probing bus 0 at eisa.0
[   17.679815] Cannot allocate resource for EISA slot 1
[   17.679820] Cannot allocate resource for EISA slot 2
[   17.679824] Cannot allocate resource for EISA slot 3
[   17.679828] Cannot allocate resource for EISA slot 4
[   17.679855] EISA: Detected 0 cards.
[   17.679861] cpuidle: using governor ladder
[   17.679864] cpuidle: using governor menu
[   17.680012] NET: Registered protocol family 1
[   17.680064] Using IPI No-Shortcut mode
[   17.680117] registered taskstats version 1
[   17.680313]   Magic number: 12:158:834
[   17.680369]   hash matches device ptyu0
[   17.680415] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   17.680419] EDD information not available.
[   17.680696] Freeing unused kernel memory: 368k freed
[   17.713099] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   19.128415] fuse init (API version 7.9)
[   19.162015] ACPI: Transitioning device [FAN0] to D3
[   19.162022] ACPI: Transitioning device [FAN0] to D3
[   19.162029] ACPI: Fan [FAN0] (off)
[   19.174105] ACPI: SSDT 7F6794D6, 023D (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[   19.174605] ACPI: SSDT 7F678F8F, 04C2 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[   19.178698] Monitor-Mwait will be used to enter C-1 state
[   19.178704] Monitor-Mwait will be used to enter C-2 state
[   19.178709] Monitor-Mwait will be used to enter C-3 state
[   19.178975] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   19.178985] ACPI: Processor [CPU0] (supports 8 throttling states)
[   19.179492] ACPI: SSDT 7F679713, 00BD (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[   19.179961] ACPI: SSDT 7F679451, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[   19.182042] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   19.182053] ACPI: Processor [CPU1] (supports 8 throttling states)
[   19.184565] ACPI: Thermal Zone [TZ00] (45 C)
[   19.185505] ACPI: Invalid passive threshold
[   19.186560] ACPI: Transitioning device [FAN0] to D0
[   19.186565] ACPI: Transitioning device [FAN0] to D0
[   19.186569] ACPI: Unable to turn cooling device [f7c49b40] 'on'
[   19.186575] ACPI: Thermal Zone [TZ01] (45 C)
[   19.971969] usbcore: registered new interface driver usbfs
[   19.972015] usbcore: registered new interface driver hub
[   19.972069] usbcore: registered new device driver usb
[   19.974350] USB Universal Host Controller Interface driver v3.0
[   19.974432] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[   19.974449] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   19.974457] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   19.974807] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   19.974850] uhci_hcd 0000:00:1d.0: irq 19, io base 0x00001820
[   19.975101] usb usb1: configuration #1 chosen from 1 choice
[   19.975150] hub 1-0:1.0: USB hub found
[   19.975160] hub 1-0:1.0: 2 ports detected
[   20.076297] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
[   20.076318] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   20.076327] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   20.076374] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   20.076416] uhci_hcd 0000:00:1d.1: irq 20, io base 0x00001840
[   20.076637] usb usb2: configuration #1 chosen from 1 choice
[   20.076685] hub 2-0:1.0: USB hub found
[   20.076695] hub 2-0:1.0: 2 ports detected
[   20.180115] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   20.180134] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   20.180142] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   20.180188] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   20.180231] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[   20.180456] usb usb3: configuration #1 chosen from 1 choice
[   20.180506] hub 3-0:1.0: USB hub found
[   20.180515] hub 3-0:1.0: 2 ports detected
[   20.191233] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[   20.191239] e100: Copyright(c) 1999-2006 Intel Corporation
[   20.250515] SCSI subsystem initialized
[   20.278900] libata version 3.00 loaded.
[   20.284047] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 17
[   20.284066] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   20.284074] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   20.284122] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   20.284165] uhci_hcd 0000:00:1d.3: irq 17, io base 0x00001880
[   20.284397] usb usb4: configuration #1 chosen from 1 choice
[   20.284447] hub 4-0:1.0: USB hub found
[   20.284457] hub 4-0:1.0: 2 ports detected
[   20.388253] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[   20.388278] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   20.388286] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   20.388339] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   20.392271] ehci_hcd 0000:00:1d.7: debug port 1
[   20.392282] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   20.392294] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xf0d44000
[   20.407743] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   20.407966] usb usb5: configuration #1 chosen from 1 choice
[   20.408019] hub 5-0:1.0: USB hub found
[   20.408030] hub 5-0:1.0: 8 ports detected
[   20.512080] ACPI: PCI Interrupt 0000:07:08.0[A] -> GSI 20 (level, low) -> IRQ 21
[   20.541894] e100: eth0: e100_probe: addr 0xf0905000, irq 21, MAC addr 00:a0:d1:68:93:9f
[   20.541952] ACPI: PCI Interrupt 0000:07:06.1[B] -> GSI 17 (level, low) -> IRQ 16
[   20.591819] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[f0906000-f09067ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   20.598791] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
[   20.598847] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   20.598871] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[   20.605355] ata_piix 0000:00:1f.2: version 2.12
[   20.605366] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[   20.759451] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
[   20.759509] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   20.760429] scsi0 : ata_piix
[   20.760562] scsi1 : ata_piix
[   20.762398] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x18b0 irq 14
[   20.762405] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18b8 irq 15
[   20.923797] ata1.00: ATA-7: TOSHIBA MK1637GSX, DL020M, max UDMA/100
[   20.923807] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   20.931810] ata1.00: configured for UDMA/100
[   21.252535] ata2.00: ATAPI: MATSHITADVD-RAM UJ-850S, 1.10, max UDMA/33
[   21.423280] ata2.00: configured for UDMA/33
[   21.423579] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK1637GS DL02 PQ: 0 ANSI: 5
[   21.425446] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-850S  1.10 PQ: 0 ANSI: 5
[   21.443757] Driver 'sd' needs updating - please use bus_type methods
[   21.444363] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   21.444392] sd 0:0:0:0: [sda] Write Protect is off
[   21.444397] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   21.444433] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.445021] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   21.445046] sd 0:0:0:0: [sda] Write Protect is off
[   21.445051] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   21.445086] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.445093]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   21.475977]  sda1 sda2 < sda5 >
[   21.506403] sd 0:0:0:0: [sda] Attached SCSI disk
[   21.515033] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   21.515041] Uniform CD-ROM driver Revision: 3.20
[   21.515137] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   21.516294] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   21.516334] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   21.650550] Clocksource tsc unstable (delta = -8061449460 ns)
[   21.654559] Time: hpet clocksource has been installed.
[   21.762526] Attempting manual resume
[   21.762533] swsusp: Resume From Partition 8:5
[   21.762536] PM: Checking swsusp image.
[   21.762799] PM: Resume from disk failed.
[   21.810090] kjournald starting.  Commit interval 5 seconds
[   21.810135] EXT3-fs: mounted filesystem with ordered data mode.
[   33.082056] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   33.165963] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   33.249746] Linux agpgart interface v0.102
[   33.331842] agpgart: Detected an Intel 945GM Chipset.
[   33.334007] agpgart: Detected 7932K stolen memory.
[   33.355008] agpgart: AGP aperture is 256M @ 0xd0000000
[   33.605393] iTCO_vendor_support: vendor-support=0
[   33.653389] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   33.653609] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   33.653699] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   33.929474] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   34.084832] intel_rng: FWH not detected
[   34.324775] input: Power Button (FF) as /devices/virtual/input/input3
[   34.335524] ACPI: Power Button (FF) [PWRF]
[   34.335639] input: Lid Switch as /devices/virtual/input/input4
[   34.335782] ACPI: Lid Switch [LID]
[   34.335889] input: Power Button (CM) as /devices/virtual/input/input5
[   34.351548] ACPI: Power Button (CM) [PWRB]
[   34.417736] ACPI: AC Adapter [ADP0] (off-line)
[   34.453863] ACPI: Battery Slot [BAT0] (battery present)
[   34.673296] Yenta: CardBus bridge found at 0000:07:06.0 [1179:ff10]
[   34.673328] Yenta: Enabling burst memory read transactions
[   34.673337] Yenta: Using CSCINT to route CSC interrupts to PCI
[   34.673341] Yenta: Routing CardBus interrupts to PCI
[   34.673351] Yenta TI: socket 0000:07:06.0, mfunc 0x01a01b22, devctl 0x66
[   34.676105] sdhci: Secure Digital Host Controller Interface driver
[   34.676111] sdhci: Copyright(c) Pierre Ossman
[   34.911848] Yenta: ISA IRQ mask 0x0cf8, PCI irq 18
[   34.911856] Socket status: 30000006
[   34.911861] Yenta: Raising subordinate bus# of parent bus (#07) from #07 to #0b
[   34.911870] pcmcia: parent PCI bridge I/O window: 0x4000 - 0x4fff
[   34.911876] cs: IO port probe 0x4000-0x4fff: clean.
[   34.912437] pcmcia: parent PCI bridge Memory window: 0xf0900000 - 0xf09fffff
[   34.958927] sdhci: SDHCI controller found at 0000:07:06.3 [104c:803c] (rev 0)
[   34.958959] ACPI: PCI Interrupt 0000:07:06.3[A] -> GSI 18 (level, low) -> IRQ 18
[   34.959068] mmc0: SDHCI at 0xf0906800 irq 18 DMA
[   34.962098] ACPI: PCI Interrupt 0000:07:06.2[A] -> GSI 18 (level, low) -> IRQ 18
[   35.919380] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input6
[   35.956090] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   35.963829] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input7
[   36.005947] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   36.103460] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   36.103505] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   36.139592] hda_codec: Unknown model for ALC660VD/ALC861VD, trying auto-probe from BIOS...
[   36.681245] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   36.681253] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   36.681481] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   36.681502] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   36.681537] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   37.686805] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04713/0x0
[   37.686819] synaptics: Toshiba Satellite A100 detected, limiting rate to 40pps.
[   37.719783] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
[   38.378773] NET: Registered protocol family 17
[   39.190616] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   39.223137] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[   39.309318] cs: IO port probe 0x100-0x3af: clean.
[   39.311688] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   39.312640] cs: IO port probe 0x820-0x8ff: clean.
[   39.313477] cs: IO port probe 0xc00-0xcf7: clean.
[   39.314627] cs: IO port probe 0xa00-0xaff: clean.
[   39.605814] lp: driver loaded but no devices found
[   39.849041] Adding 6048432k swap on /dev/sda5.  Priority:-1 extents:1 across:6048432k
[   39.912137] EXT3 FS on sda1, internal journal
[   41.055495] ip_tables: (C) 2000-2006 Netfilter Core Team
[   41.790533] ACPI: Error installing notify handler
[   41.790655] No dock devices found.
[   43.356900] apm: BIOS not found.
[   44.311801] ppdev: user-space parallel port driver
[   44.532772] audit(1222865356.202:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5172 profile="/usr/sbin/cupsd" namespace="default"
[   46.300703] Bluetooth: Core ver 2.11
[   46.301271] NET: Registered protocol family 31
[   46.301277] Bluetooth: HCI device and connection manager initialized
[   46.301284] Bluetooth: HCI socket layer initialized
[   46.372732] Bluetooth: L2CAP ver 2.9
[   46.372741] Bluetooth: L2CAP socket layer initialized
[   46.456686] Bluetooth: RFCOMM socket layer initialized
[   46.456706] Bluetooth: RFCOMM TTY layer initialized
[   46.456710] Bluetooth: RFCOMM ver 1.8
[   49.097660] [drm] Initialized drm 1.1.0 20060810
[   49.103593] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[   49.103606] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   49.103672] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   67.005834] NET: Registered protocol family 10
[   67.006352] lo: Disabled Privacy Extensions
[   67.007395] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   67.008642] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   83.607430] CPU0 attaching NULL sched-domain.
[   83.607441] CPU1 attaching NULL sched-domain.
[   83.623380] CPU0 attaching sched-domain:
[   83.623390]  domain 0: span 03
[   83.623394]   groups: 01 02
[   83.623401]   domain 1: span 03
[   83.623405]    groups: 03
[   83.623412] CPU1 attaching sched-domain:
[   83.623416]  domain 0: span 03
[   83.623419]   groups: 02 01
[   83.623426]   domain 1: span 03
[   83.623430]    groups: 03
[   87.936410] wlan0: Initial auth_alg=0
[   87.936422] wlan0: authenticate with AP 00:16:ca:3a:e2:80
[   87.939275] wlan0: RX authentication from 00:16:ca:3a:e2:80 (alg=0 transaction=2 status=0)
[   87.939286] wlan0: authenticated
[   87.939290] wlan0: associate with AP 00:16:ca:3a:e2:80
[   87.942508] wlan0: RX AssocResp from 00:16:ca:3a:e2:80 (capab=0x431 status=0 aid=2)
[   87.942516] wlan0: associated
[   87.942676] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[   87.947040] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   87.949562] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[   87.949666] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[   87.949764] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[  104.233932] wlan0: no IPv6 routers present
[  689.877623] wlan0: CTS protection enabled (BSSID=00:16:ca:3a:e2:80)
[  709.713096] wlan0: CTS protection disabled (BSSID=00:16:ca:3a:e2:80)


```

Thanks a lot in advance

Ideuss

---

