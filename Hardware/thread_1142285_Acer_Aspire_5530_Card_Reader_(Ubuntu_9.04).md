---
title: "Acer Aspire 5530 Card Reader (Ubuntu 9.04)"
date: 2009-04-29
forum: Hardware
---

### Post by mr.tapac on 2009-04-29
Hi.

How to make it work? Card Reader (5-in-1) doesn't work after install, and I have no idea, how to make it work.

Can anybody help me?

```
[~]$ dmesg
[    0.000000] BIOS EBDA/lowmem at: 0009dc00/0009dc00
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 (Ubuntu 2.6.28-11.42-generic)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000006fed0000 (usable)
[    0.000000]  BIOS-e820: 000000006fed0000 - 000000006fedc000 (ACPI data)
[    0.000000]  BIOS-e820: 000000006fedc000 - 000000006fede000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000006fede000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0x6fed0 max_arch_pfn = 0x100000
[    0.000000] Scanning 2 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)
[    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000090c00 (usable)
[    0.000000]  modified: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000006fed0000 (usable)
[    0.000000]  modified: 000000006fed0000 - 000000006fedc000 (ACPI data)
[    0.000000]  modified: 000000006fedc000 - 000000006fede000 (ACPI NVS)
[    0.000000]  modified: 000000006fede000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.000000] RAMDISK: 378bd000 - 37feffb8
[    0.000000] Allocated new RAMDISK: 00881000 - 00fb3fb8
[    0.000000] Move RAMDISK from 00000000378bd000 - 0000000037feffb7 to 00881000 - 00fb3fb7
[    0.000000] ACPI: RSDP 000F7700, 0024 (r2 ACRSYS)
[    0.000000] ACPI: XSDT 6FED1795, 005C (r1 ACRSYS ACRPRDCT  6040000  LTP        0)
[    0.000000] ACPI: FACP 6FEDB871, 00F4 (r3 AMD    ANT       6040000 ATI     F4240)
[    0.000000] ACPI: DSDT 6FED17F1, A080 (r1   Acer    SB700  6040000 MSFT  3000000)
[    0.000000] ACPI: FACS 6FEDDFC0, 0040
[    0.000000] ACPI: SLIC 6FEDB9D9, 0176 (r1 ACRSYS ACRPRDCT  6040000 LOHR        0)
[    0.000000] ACPI: SSDT 6FEDBB4F, 02B4 (r1 PTLTD  POWERNOW  6040000  LTP        1)
[    0.000000] ACPI: APIC 6FEDBE03, 005E (r1 PTLTD       APIC    6040000  LTP        0)
[    0.000000] ACPI: MCFG 6FEDBE61, 003C (r1 PTLTD    MCFG    6040000  LTP        0)
[    0.000000] ACPI: HPET 6FEDBE9D, 0038 (r1 PTLTD  HPETTBL   6040000  LTP        1)
[    0.000000] ACPI: ASF! 6FEDBED5, 012B (r32    DMA AMDTBL    6040000 PTL         1)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 906MB HIGHMEM available.
[    0.000000] 883MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 373fe000
[    0.000000]   low ram: 00000000 - 373fe000
[    0.000000]   bootmap 00012000 - 00018e80
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 000087c52c]    TEXT DATA BSS ==> [0000100000 - 000087c52c]
[    0.000000]   #4 [000087d000 - 0000881000]    INIT_PG_TABLE ==> [000087d000 - 0000881000]
[    0.000000]   #5 [000009dc00 - 0000100000]    BIOS reserved ==> [000009dc00 - 0000100000]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [0000881000 - 0000fb3fb8]      NEW RAMDISK ==> [0000881000 - 0000fb3fb8]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] found SMP MP-table at [c00f77c0] 000f77c0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x0006fed0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x00000007
[    0.000000]     0: 0x00000010 -> 0x00000090
[    0.000000]     0: 0x00000100 -> 0x0006fed0
[    0.000000] On node 0 totalpages: 458323
[    0.000000] free_area_init_node: node 0, pgdat c06d0f80, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3939 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 1814 pages used for memmap
[    0.000000]   HighMem zone: 230332 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x43538301 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 0000000000090000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d0000
[    0.000000] PM: Registered nosave memory: 00000000000d0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 454741
[    0.000000] Kernel command line: root=UUID=339a2467-59ce-42ce-8f8c-01b85ec00d5e ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1900.175 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 9168960 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 1793064k/1833792k available (4126k kernel code, 39292k reserved, 2208k data, 532k init, 928584k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0737000 - 0xc07bc000   ( 532 kB)
[    0.004000]       .data : 0xc0507a6f - 0xc072fe60   (2208 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0507a6f   (4126 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] HPET: 4 timers in total, 1 timers will be used for per-cpu timer
[    0.004011] Calibrating delay loop (skipped), value calculated using timer frequency.. 3800.35 BogoMIPS (lpj=7600700)
[    0.004029] Security Framework initialized
[    0.004035] SELinux:  Disabled at boot.
[    0.004050] AppArmor: AppArmor initialized
[    0.004058] Mount-cache hash table entries: 512
[    0.004191] Initializing cgroup subsys ns
[    0.004194] Initializing cgroup subsys cpuacct
[    0.004197] Initializing cgroup subsys memory
[    0.004202] Initializing cgroup subsys freezer
[    0.004215] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004218] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004220] CPU: Physical Processor ID: 0
[    0.004222] CPU: Processor Core ID: 0
[    0.004226] using C1E aware idle routine
[    0.004236] Checking 'hlt' instruction... OK.
[    0.022968] ACPI: Core revision 20080926
[    0.026032] ACPI: Checking initramfs for custom DSDT
[    0.328486] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
[    0.369921] CPU0: AMD Athlon(tm) X2 Dual-Core QL-60 stepping 01
[    0.372001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3790.74 BogoMIPS (lpj=7581491)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.456253] CPU1: AMD Athlon(tm) X2 Dual-Core QL-60 stepping 01
[    0.456304] checking TSC synchronization [CPU#0 -> CPU#1]:
[    0.460001] Measured 22073759 cycles TSC warp between CPUs, turning off TSC clock.
[    0.460001] Marking TSC unstable due to check_tsc_sync_source failed
[    0.460044] Brought up 2 CPUs
[    0.460047] Total of 2 processors activated (7591.09 BogoMIPS).
[    0.460128] CPU0 attaching sched-domain:
[    0.460130]  domain 0: span 0-1 level CPU
[    0.460133]   groups: 0 1
[    0.460140] CPU1 attaching sched-domain:
[    0.460142]  domain 0: span 0-1 level CPU
[    0.460144]   groups: 1 0
[    0.460209] net_namespace: 776 bytes
[    0.460209] Booting paravirtualized kernel on bare hardware
[    0.460358] Time:  1:10:12  Date: 04/29/09
[    0.460358] regulator: core version 0.5
[    0.460358] NET: Registered protocol family 16
[    0.460358] EISA bus registered
[    0.460358] ACPI: bus type pci registered
[    0.460358] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 9
[    0.460358] PCI: MCFG area at e0000000 reserved in E820
[    0.460358] PCI: Using MMCONFIG for extended config space
[    0.460358] PCI: Using configuration type 1 for base access
[    0.461100] ACPI: EC: Look up EC in DSDT
[    0.469956] ACPI: BIOS _OSI(Linux) query ignored
[    0.493091] ACPI: Interpreter enabled
[    0.493095] ACPI: (supports S0 S3 S4 S5)
[    0.493113] ACPI: Using IOAPIC for interrupt routing
[    0.500017] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.576721] ACPI: EC: GPE = 0x3, I/O: command/status = 0x66, data = 0x62
[    0.576724] ACPI: EC: driver started in interrupt mode
[    0.576898] ACPI: No dock devices found.
[    0.576910] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.577104] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    0.577109] pci 0000:00:04.0: PME# disabled
[    0.577185] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.577189] pci 0000:00:06.0: PME# disabled
[    0.577224] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.577228] pci 0000:00:07.0: PME# disabled
[    0.577299] pci 0000:00:09.0: PME# supported from D0 D3hot D3cold
[    0.577302] pci 0000:00:09.0: PME# disabled
[    0.577366] pci 0000:00:11.0: reg 10 io port: [0x8420-0x8427]
[    0.577375] pci 0000:00:11.0: reg 14 io port: [0x8414-0x8417]
[    0.577383] pci 0000:00:11.0: reg 18 io port: [0x8418-0x841f]
[    0.577391] pci 0000:00:11.0: reg 1c io port: [0x8410-0x8413]
[    0.577399] pci 0000:00:11.0: reg 20 io port: [0x8400-0x840f]
[    0.577408] pci 0000:00:11.0: reg 24 32bit mmio: [0xf0508000-0xf05083ff]
[    0.577430] pci 0000:00:11.0: set SATA to AHCI mode
[    0.577466] pci 0000:00:12.0: reg 10 32bit mmio: [0xf0504000-0xf0504fff]
[    0.577528] pci 0000:00:12.1: reg 10 32bit mmio: [0xf0505000-0xf0505fff]
[    0.577612] pci 0000:00:12.2: reg 10 32bit mmio: [0xf0508400-0xf05084ff]
[    0.577658] pci 0000:00:12.2: supports D1 D2
[    0.577661] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.577666] pci 0000:00:12.2: PME# disabled
[    0.577702] pci 0000:00:13.0: reg 10 32bit mmio: [0xf0506000-0xf0506fff]
[    0.577765] pci 0000:00:13.1: reg 10 32bit mmio: [0xf0507000-0xf0507fff]
[    0.577849] pci 0000:00:13.2: reg 10 32bit mmio: [0xf0508800-0xf05088ff]
[    0.577895] pci 0000:00:13.2: supports D1 D2
[    0.577897] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.577902] pci 0000:00:13.2: PME# disabled
[    0.578039] pci 0000:00:14.2: reg 10 64bit mmio: [0xf0500000-0xf0503fff]
[    0.578080] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.578085] pci 0000:00:14.2: PME# disabled
[    0.578373] pci 0000:01:05.0: reg 10 32bit mmio: [0xd0000000-0xdfffffff]
[    0.578379] pci 0000:01:05.0: reg 14 io port: [0x9000-0x90ff]
[    0.578384] pci 0000:01:05.0: reg 18 32bit mmio: [0xcfdf0000-0xcfdfffff]
[    0.578395] pci 0000:01:05.0: reg 24 32bit mmio: [0xcfe00000-0xcfefffff]
[    0.578405] pci 0000:01:05.0: supports D1 D2
[    0.578432] pci 0000:01:05.1: reg 10 32bit mmio: [0xcfdec000-0xcfdeffff]
[    0.578456] pci 0000:01:05.1: supports D1 D2
[    0.578541] pci 0000:00:01.0: bridge io port: [0x9000-0x9fff]
[    0.578545] pci 0000:00:01.0: bridge 32bit mmio: [0xcfd00000-0xcfefffff]
[    0.578551] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.578606] pci 0000:00:04.0: bridge io port: [0x00-0xfff]
[    0.578610] pci 0000:00:04.0: bridge 32bit mmio: [0x000000-0x0fffff]
[    0.578615] pci 0000:00:04.0: bridge 64bit mmio pref: [0x000000-0x0fffff]
[    0.578664] pci 0000:05:00.0: reg 10 64bit mmio: [0xf0200000-0xf020ffff]
[    0.578802] pci 0000:00:06.0: bridge 32bit mmio: [0xf0200000-0xf02fffff]
[    0.578866] pci 0000:06:00.0: reg 10 64bit mmio: [0xf0300000-0xf030ffff]
[    0.578907] pci 0000:06:00.0: PME# supported from D3hot D3cold
[    0.578912] pci 0000:06:00.0: PME# disabled
[    0.578984] pci 0000:00:07.0: bridge 32bit mmio: [0xf0300000-0xf03fffff]
[    0.579043] pci 0000:00:09.0: bridge 32bit mmio: [0xf0400000-0xf04fffff]
[    0.579112] pci 0000:00:14.4: transparent bridge
[    0.579144] bus 00 -> node 0
[    0.579150] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.579578] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[    0.579737] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[    0.579892] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB7_._PRT]
[    0.580095] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.580210] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.583971] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[    0.584196] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[    0.584432] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[    0.584666] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[    0.584902] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[    0.585087] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[    0.585322] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[    0.585558] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[    0.585906] ACPI: WMI: Mapper loaded
[    0.585954] SCSI subsystem initialized
[    0.585954] libata version 3.00 loaded.
[    0.585954] usbcore: registered new interface driver usbfs
[    0.585954] usbcore: registered new interface driver hub
[    0.585954] usbcore: registered new device driver usb
[    0.585954] PCI: Using ACPI for IRQ routing
[    0.585954] pci 0000:00:04.0: BAR 7: can't allocate resource
[    0.585954] pci 0000:00:04.0: BAR 8: can't allocate resource
[    0.585954] pci 0000:00:04.0: BAR 9: can't allocate resource
[    0.588016] Bluetooth: Core ver 2.13
[    0.588023] NET: Registered protocol family 31
[    0.588023] Bluetooth: HCI device and connection manager initialized
[    0.588023] Bluetooth: HCI socket layer initialized
[    0.588023] NET: Registered protocol family 8
[    0.588024] NET: Registered protocol family 20
[    0.588035] NetLabel: Initializing
[    0.588037] NetLabel:  domain hash size = 128
[    0.588039] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.588053] NetLabel:  unlabeled traffic allowed by default
[    0.588103] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 2303, 0
[    0.588109] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.592048] hpet: hpet2 irq 2303 for MSI
[    0.592089] AppArmor: AppArmor Filesystem Enabled
[    0.596024] Switched to high resolution mode on CPU 0
[    0.596371] Switched to high resolution mode on CPU 1
[    0.596381] pnp: PnP ACPI init
[    0.596390] ACPI: bus type pnp registered
[    0.636189] pnp: PnP ACPI: found 12 devices
[    0.636191] ACPI: ACPI bus type pnp unregistered
[    0.636194] PnPBIOS: Disabled by ACPI PNP
[    0.636205] system 00:01: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.636208] system 00:01: iomem range 0xfec10000-0xfec10fff has been reserved
[    0.636211] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.636220] system 00:08: ioport range 0x220-0x22f has been reserved
[    0.636223] system 00:08: ioport range 0x40b-0x40b has been reserved
[    0.636226] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.636228] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
[    0.636231] system 00:08: ioport range 0x530-0x537 has been reserved
[    0.636234] system 00:08: ioport range 0xc00-0xc01 has been reserved
[    0.636237] system 00:08: ioport range 0xc14-0xc14 has been reserved
[    0.636239] system 00:08: ioport range 0xc50-0xc52 has been reserved
[    0.636242] system 00:08: ioport range 0xc6c-0xc6c has been reserved
[    0.636245] system 00:08: ioport range 0xc6f-0xc6f has been reserved
[    0.636248] system 00:08: ioport range 0xcd0-0xcd1 has been reserved
[    0.636251] system 00:08: ioport range 0xcd2-0xcd3 has been reserved
[    0.636254] system 00:08: ioport range 0xcd4-0xcd5 has been reserved
[    0.636257] system 00:08: ioport range 0xcd6-0xcd7 has been reserved
[    0.636259] system 00:08: ioport range 0xcd8-0xcdf has been reserved
[    0.636262] system 00:08: ioport range 0x8000-0x805f has been reserved
[    0.636265] system 00:08: ioport range 0xf40-0xf47 has been reserved
[    0.636268] system 00:08: ioport range 0x87f-0x87f has been reserved
[    0.636275] system 00:09: iomem range 0xe0000-0xfffff could not be reserved
[    0.636278] system 00:09: iomem range 0xfff00000-0xffffffff has been reserved
[    0.671387] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.671390] pci 0000:00:01.0:   IO window: 0x9000-0x9fff
[    0.671395] pci 0000:00:01.0:   MEM window: 0xcfd00000-0xcfefffff
[    0.671399] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.671404] pci 0000:00:04.0: PCI bridge, secondary bus 0000:02
[    0.671406] pci 0000:00:04.0:   IO window: disabled
[    0.671410] pci 0000:00:04.0:   MEM window: disabled
[    0.671414] pci 0000:00:04.0:   PREFETCH window: disabled
[    0.671419] pci 0000:00:06.0: PCI bridge, secondary bus 0000:05
[    0.671421] pci 0000:00:06.0:   IO window: disabled
[    0.671425] pci 0000:00:06.0:   MEM window: 0xf0200000-0xf02fffff
[    0.671428] pci 0000:00:06.0:   PREFETCH window: disabled
[    0.671433] pci 0000:00:07.0: PCI bridge, secondary bus 0000:06
[    0.671435] pci 0000:00:07.0:   IO window: disabled
[    0.671440] pci 0000:00:07.0:   MEM window: 0xf0300000-0xf03fffff
[    0.671443] pci 0000:00:07.0:   PREFETCH window: disabled
[    0.671448] pci 0000:00:09.0: PCI bridge, secondary bus 0000:07
[    0.671450] pci 0000:00:09.0:   IO window: disabled
[    0.671454] pci 0000:00:09.0:   MEM window: 0xf0400000-0xf04fffff
[    0.671458] pci 0000:00:09.0:   PREFETCH window: disabled
[    0.671463] pci 0000:00:14.4: PCI bridge, secondary bus 0000:08
[    0.671465] pci 0000:00:14.4:   IO window: disabled
[    0.671504] pci 0000:00:14.4:   MEM window: disabled
[    0.671509] pci 0000:00:14.4:   PREFETCH window: disabled
[    0.671530] pci 0000:00:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.671535] pci 0000:00:04.0: setting latency timer to 64
[    0.671542] pci 0000:00:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.671546] pci 0000:00:06.0: setting latency timer to 64
[    0.671553] pci 0000:00:07.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.671557] pci 0000:00:07.0: setting latency timer to 64
[    0.671563] pci 0000:00:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.671567] pci 0000:00:09.0: setting latency timer to 64
[    0.671576] bus: 00 index 0 io port: [0x00-0xffff]
[    0.671579] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.671581] bus: 01 index 0 io port: [0x9000-0x9fff]
[    0.671583] bus: 01 index 1 mmio: [0xcfd00000-0xcfefffff]
[    0.671586] bus: 01 index 2 mmio: [0xd0000000-0xdfffffff]
[    0.671588] bus: 01 index 3 mmio: [0x0-0x0]
[    0.671590] bus: 02 index 0 mmio: [0x0-0xfff]
[    0.671592] bus: 02 index 1 mmio: [0x0-0xfffff]
[    0.671594] bus: 02 index 2 mmio: [0x0-0xfffff]
[    0.671596] bus: 02 index 3 mmio: [0x0-0x0]
[    0.671598] bus: 05 index 0 mmio: [0x0-0x0]
[    0.671600] bus: 05 index 1 mmio: [0xf0200000-0xf02fffff]
[    0.671602] bus: 05 index 2 mmio: [0x0-0x0]
[    0.671604] bus: 05 index 3 mmio: [0x0-0x0]
[    0.671606] bus: 06 index 0 mmio: [0x0-0x0]
[    0.671608] bus: 06 index 1 mmio: [0xf0300000-0xf03fffff]
[    0.671610] bus: 06 index 2 mmio: [0x0-0x0]
[    0.671612] bus: 06 index 3 mmio: [0x0-0x0]
[    0.671614] bus: 07 index 0 mmio: [0x0-0x0]
[    0.671616] bus: 07 index 1 mmio: [0xf0400000-0xf04fffff]
[    0.671618] bus: 07 index 2 mmio: [0x0-0x0]
[    0.671620] bus: 07 index 3 mmio: [0x0-0x0]
[    0.671622] bus: 08 index 0 mmio: [0x0-0x0]
[    0.671624] bus: 08 index 1 mmio: [0x0-0x0]
[    0.671626] bus: 08 index 2 mmio: [0x0-0x0]
[    0.671628] bus: 08 index 3 io port: [0x00-0xffff]
[    0.671630] bus: 08 index 4 mmio: [0x000000-0xffffffff]
[    0.671642] NET: Registered protocol family 2
[    0.681102] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.681399] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.682063] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.682373] TCP: Hash tables configured (established 131072 bind 65536)
[    0.682376] TCP reno registered
[    0.685136] NET: Registered protocol family 1
[    0.685268] checking if image is initramfs... it is
[    1.302388] Freeing initrd memory: 7371k freed
[    1.302626] cpufreq: No nForce2 chipset.
[    1.302753] audit: initializing netlink socket (disabled)
[    1.302771] type=2000 audit(1240967412.301:1): initialized
[    1.311348] highmem bounce pool size: 64 pages
[    1.311355] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.312622] VFS: Disk quotas dquot_6.5.1
[    1.312681] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.313395] fuse init (API version 7.10)
[    1.313484] msgmni has been set to 1704
[    1.313782] alg: No test for stdrng (krng)
[    1.313798] io scheduler noop registered
[    1.313800] io scheduler anticipatory registered
[    1.313802] io scheduler deadline registered
[    1.313820] io scheduler cfq registered (default)
[    1.314052] pci 0000:01:05.0: Boot video device
[    1.392291] pcieport-driver 0000:00:04.0: setting latency timer to 64
[    1.392327] pcieport-driver 0000:00:04.0: found MSI capability
[    1.392354] pcieport-driver 0000:00:04.0: irq 2302 for MSI/MSI-X
[    1.392365] pci_express 0000:00:04.0:pcie00: allocate port service
[    1.392380] pci_express 0000:00:04.0:pcie02: allocate port service
[    1.392391] pci_express 0000:00:04.0:pcie03: allocate port service
[    1.392440] pcieport-driver 0000:00:06.0: setting latency timer to 64
[    1.392472] pcieport-driver 0000:00:06.0: found MSI capability
[    1.392494] pcieport-driver 0000:00:06.0: irq 2301 for MSI/MSI-X
[    1.392508] pci_express 0000:00:06.0:pcie00: allocate port service
[    1.392519] pci_express 0000:00:06.0:pcie03: allocate port service
[    1.392567] pcieport-driver 0000:00:07.0: setting latency timer to 64
[    1.392600] pcieport-driver 0000:00:07.0: found MSI capability
[    1.392622] pcieport-driver 0000:00:07.0: irq 2300 for MSI/MSI-X
[    1.392632] pci_express 0000:00:07.0:pcie00: allocate port service
[    1.392644] pci_express 0000:00:07.0:pcie02: allocate port service
[    1.392656] pci_express 0000:00:07.0:pcie03: allocate port service
[    1.392703] pcieport-driver 0000:00:09.0: setting latency timer to 64
[    1.392736] pcieport-driver 0000:00:09.0: found MSI capability
[    1.392758] pcieport-driver 0000:00:09.0: irq 2299 for MSI/MSI-X
[    1.392768] pci_express 0000:00:09.0:pcie00: allocate port service
[    1.392780] pci_express 0000:00:09.0:pcie03: allocate port service
[    1.392843] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.392899] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.411767] ACPI: AC Adapter [ACAD] (on-line)
[    1.827348] ACPI: Battery Slot [BAT1] (battery present)
[    1.827422] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.827425] ACPI: Power Button (FF) [PWRF]
[    1.827468] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.827470] ACPI: Power Button (CM) [PWRB]
[    1.827512] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.827515] ACPI: Sleep Button (CM) [SLPB]
[    1.827560] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[    1.827657] ACPI: Lid Switch [LID]
[    1.827967] processor ACPI_CPU:00: registered as cooling_device0
[    1.827972] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.828019] processor ACPI_CPU:01: registered as cooling_device1
[    1.902456] thermal LNXTHERM:01: registered as thermal_zone0
[    1.969169] ACPI: Thermal Zone [THRM] (36 C)
[    2.001808] thermal LNXTHERM:02: registered as thermal_zone1
[    2.042921] ACPI: Thermal Zone [Z014] (0 C)
[    2.042971] isapnp: Scanning for PnP cards...
[    2.423653] isapnp: No Plug & Play device found
[    2.437392] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.438357] brd: module loaded
[    2.438672] loop: module loaded
[    2.438742] Fixed MDIO Bus: probed
[    2.438748] PPP generic driver version 2.4.2
[    2.438811] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    2.438841] Driver 'sd' needs updating - please use bus_type methods
[    2.438850] Driver 'sr' needs updating - please use bus_type methods
[    2.438885] ahci 0000:00:11.0: version 3.0
[    2.438941] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    2.439134] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    2.439138] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    2.439863] scsi0 : ahci
[    2.440067] scsi1 : ahci
[    2.440154] scsi2 : ahci
[    2.440248] scsi3 : ahci
[    2.440357] ata1: SATA max UDMA/133 abar m1024@0xf0508000 port 0xf0508100 irq 22
[    2.440362] ata2: SATA max UDMA/133 abar m1024@0xf0508000 port 0xf0508180 irq 22
[    2.440366] ata3: SATA max UDMA/133 abar m1024@0xf0508000 port 0xf0508200 irq 22
[    2.440370] ata4: SATA max UDMA/133 abar m1024@0xf0508000 port 0xf0508280 irq 22
[    2.924081] ata1: softreset failed (device not ready)
[    2.924124] ata1: failed due to HW bug, retry pmp=0
[    3.088073] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.089010] ata1.00: ATA-8: Hitachi HTS543216L9A300, FB2OC40C, max UDMA/133
[    3.089013] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    3.090154] ata1.00: configured for UDMA/133
[    3.588048] ata2: softreset failed (device not ready)
[    3.588090] ata2: failed due to HW bug, retry pmp=0
[    3.752052] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.765740] ata2.00: ATAPI: Optiarc DVD RW AD-7560S, SX07, max UDMA/100, ATAPI AN
[    3.779340] ata2.00: configured for UDMA/100 (device error ignored)
[    4.112090] ata3: SATA link down (SStatus 0 SControl 300)
[    4.448067] ata4: SATA link down (SStatus 0 SControl 300)
[    4.464159] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54321 FB2O PQ: 0 ANSI: 5
[    4.464262] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[    4.464280] sd 0:0:0:0: [sda] Write Protect is off
[    4.464282] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.464308] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.464386] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[    4.464401] sd 0:0:0:0: [sda] Write Protect is off
[    4.464403] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.464428] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.464432]  sda: sda1 sda2 sda3
[    4.506103] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.506155] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.507223] scsi 1:0:0:0: CD-ROM            Optiarc  DVD RW AD-7560S  SX07 PQ: 0 ANSI: 5
[    4.513097] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.513101] Uniform CD-ROM driver Revision: 3.20
[    4.513191] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.513226] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    4.513957] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.514015] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    4.514040] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    4.514107] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    4.514169] ehci_hcd 0000:00:12.2: applying AMD SB600/SB700 USB freeze workaround
[    4.514190] ehci_hcd 0000:00:12.2: debug port 1
[    4.514214] ehci_hcd 0000:00:12.2: irq 17, io mem 0xf0508400
[    4.524055] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    4.524136] usb usb1: configuration #1 chosen from 1 choice
[    4.524165] hub 1-0:1.0: USB hub found
[    4.524177] hub 1-0:1.0: 6 ports detected
[    4.524311] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.524323] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    4.524371] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    4.524427] ehci_hcd 0000:00:13.2: applying AMD SB600/SB700 USB freeze workaround
[    4.524447] ehci_hcd 0000:00:13.2: debug port 1
[    4.524463] ehci_hcd 0000:00:13.2: irq 19, io mem 0xf0508800
[    4.536052] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    4.536102] usb usb2: configuration #1 chosen from 1 choice
[    4.536125] hub 2-0:1.0: USB hub found
[    4.536132] hub 2-0:1.0: 6 ports detected
[    4.536261] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.536307] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.536319] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    4.536358] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    4.536421] ohci_hcd 0000:00:12.0: irq 16, io mem 0xf0504000
[    4.596074] usb usb3: configuration #1 chosen from 1 choice
[    4.596101] hub 3-0:1.0: USB hub found
[    4.596147] hub 3-0:1.0: 3 ports detected
[    4.596260] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.596272] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    4.596319] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    4.596368] ohci_hcd 0000:00:12.1: irq 16, io mem 0xf0505000
[    4.652082] usb usb4: configuration #1 chosen from 1 choice
[    4.652105] hub 4-0:1.0: USB hub found
[    4.652148] hub 4-0:1.0: 3 ports detected
[    4.652269] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    4.652280] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    4.652320] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    4.652381] ohci_hcd 0000:00:13.0: irq 18, io mem 0xf0506000
[    4.708074] usb usb5: configuration #1 chosen from 1 choice
[    4.708097] hub 5-0:1.0: USB hub found
[    4.708146] hub 5-0:1.0: 3 ports detected
[    4.708265] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    4.708277] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    4.708322] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    4.708371] ohci_hcd 0000:00:13.1: irq 18, io mem 0xf0507000
[    4.764076] usb usb6: configuration #1 chosen from 1 choice
[    4.764103] hub 6-0:1.0: USB hub found
[    4.764146] hub 6-0:1.0: 3 ports detected
[    4.764263] uhci_hcd: USB Universal Host Controller Interface driver
[    4.764341] usbcore: registered new interface driver libusual
[    4.764378] usbcore: registered new interface driver usbserial
[    4.764389] USB Serial support registered for generic
[    4.892066] usb 1-6: new high speed USB device using ehci_hcd and address 3
[    5.065195] usb 1-6: configuration #1 chosen from 1 choice
[    5.068149] usbcore: registered new interface driver usbserial_generic
[    5.068152] usbserial: USB Serial Driver core
[    5.068196] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    5.104854] serio: i8042 KBD port at 0x60,0x64 irq 1
[    5.104862] serio: i8042 AUX port at 0x60,0x64 irq 12
[    5.109077] mice: PS/2 mouse device common for all mice
[    5.129106] rtc_cmos 00:04: RTC can wake from S4
[    5.129143] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    5.129171] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    5.129236] device-mapper: uevent: version 1.0.3
[    5.129390] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    5.129531] device-mapper: multipath: version 1.0.5 loaded
[    5.129534] device-mapper: multipath round-robin: version 1.0.0 loaded
[    5.129651] EISA: Probing bus 0 at eisa.0
[    5.129686] Cannot allocate resource for EISA slot 8
[    5.129688] EISA: Detected 0 cards.
[    5.129782] cpuidle: using governor ladder
[    5.129784] cpuidle: using governor menu
[    5.130296] TCP cubic registered
[    5.130397] NET: Registered protocol family 10
[    5.130805] lo: Disabled Privacy Extensions
[    5.131121] NET: Registered protocol family 17
[    5.131142] Bluetooth: L2CAP ver 2.11
[    5.131144] Bluetooth: L2CAP socket layer initialized
[    5.131147] Bluetooth: SCO (Voice Link) ver 0.6
[    5.131149] Bluetooth: SCO socket layer initialized
[    5.131230] Bluetooth: RFCOMM socket layer initialized
[    5.131238] Bluetooth: RFCOMM TTY layer initialized
[    5.131240] Bluetooth: RFCOMM ver 1.10
[    5.131396] powernow-k8: Found 1 AMD Athlon(tm) X2 Dual-Core QL-60 processors (2 cpu cores) (version 2.20.00)
[    5.131437] powernow-k8:    0 : pstate 0 (1900 MHz)
[    5.131439] powernow-k8:    1 : pstate 1 (1000 MHz)
[    5.131857] Using IPI No-Shortcut mode
[    5.131936] registered taskstats version 1
[    5.132068]   Magic number: 5:884:155
[    5.132095] bdi 1:7: hash matches
[    5.132137] acpi device:22: hash matches
[    5.132199] rtc_cmos 00:04: setting system clock to 2009-04-29 01:10:17 UTC (1240967417)
[    5.132202] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    5.132205] EDD information not available.
[    5.132587] Freeing unused kernel memory: 532k freed
[    5.132781] Write protecting the kernel text: 4128k
[    5.132871] Write protecting the kernel read-only data: 1532k
[    5.167107] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    5.216055] usb 4-2: new low speed USB device using ohci_hcd and address 2
[    5.387203] usb 4-2: configuration #1 chosen from 1 choice
[    5.394726] usbcore: registered new interface driver hiddev
[    5.402836] input: Microsoft Microsoft Notebook Optical Mouse with Tilt Wheel as /devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.0/input/input6
[    5.436167] generic-usb 0003:045E:00D2.0001: input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Notebook Optical Mouse with Tilt Wheel] on usb-0000:00:12.1-2/input0
[    5.436192] usbcore: registered new interface driver usbhid
[    5.436196] usbhid: v2.6:USB HID core driver
[    5.490230] tg3.c:v3.94 (August 14, 2008)
[    5.490248] tg3 0000:06:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    5.490257] tg3 0000:06:00.0: setting latency timer to 64
[    6.029241] eth0: Tigon3 [partno(BCM95764M) rev 5784100 PHY(5784)] (PCI Express) 10/100/1000Base-T Ethernet 00:1e:ec:5d:8c:80
[    6.029246] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[    6.029249] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    6.187962] PM: Starting manual resume from disk
[    6.187967] PM: Resume from partition 8:2
[    6.187969] PM: Checking hibernation image.
[    6.188162] PM: Resume from disk failed.
[    6.212751] EXT4-fs: barriers enabled
[    6.226990] kjournald2 starting.  Commit interval 5 seconds
[    6.227003] EXT4-fs: delayed allocation enabled
[    6.227006] EXT4-fs: file extents enabled
[    6.227941] EXT4-fs: mballoc enabled
[    6.227946] EXT4-fs: mounted filesystem with ordered data mode.
[   10.245046] udev: starting version 141
[   10.446810] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.493154] cfg80211: Calling CRDA to update world regulatory domain
[   10.527158] acpi device:30: registered as cooling_device2
[   10.527408] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2d/device:2e/input/input7
[   10.553220] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   10.634298] Linux agpgart interface v0.103
[   10.762200] ACPI: I/O resource piix4_smbus [0x8040-0x8047] conflicts with ACPI region SMB2 [0x8040-0x8045]
[   10.762204] ACPI: Device needs an ACPI driver
[   10.762213] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x8040, revision 0
[   10.819287] input: PC Speaker as /devices/platform/pcspkr/input/input8
[   10.889849] acer-wmi: Acer Laptop ACPI-WMI Extras
[   10.900638] acer-wmi: Unable to detect available WMID devices
[   10.931056] cfg80211: World regulatory domain updated:
[   10.931060]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.931064]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.931067]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.931070]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.931072]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.931075]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.972948] ath5k_pci 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   10.972962] ath5k_pci 0000:05:00.0: setting latency timer to 64
[   10.973253] ath5k_pci 0000:05:00.0: registered as 'phy0'
[   11.014044] phy0: Selected rate control algorithm 'pid'
[   11.098267] Linux video capture interface: v2.00
[   11.246537] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   11.500206] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   11.533990] [fglrx] Maximum main memory to use for locked dma buffers: 1643 MBytes.
[   11.534021] [fglrx]   vendor: 1002 device: 9612 count: 1
[   11.534321] [fglrx] ioport: bar 1, base 0x9000, size: 0x100
[   11.534341] pci 0000:01:05.0: power state changed by ACPI to D0
[   11.534352] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   11.534357] pci 0000:01:05.0: setting latency timer to 64
[   11.534988] [fglrx] Driver built-in PAT support is enabled successfully
[   11.535029] [fglrx] module loaded - fglrx 8.60.40 [Mar 14 2009] with 1 minors
[   11.574232] uvcvideo: Found UVC 1.00 device Acer Crystal Eye webcam (064e:a103)
[   11.575815] input: Acer Crystal Eye webcam as /devices/pci0000:00/0000:00:12.2/usb1/1-6/1-6:1.0/input/input9
[   11.577141] usbcore: registered new interface driver uvcvideo
[   11.577166] USB Video Class driver (v0.1.0)
[   11.629842] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   11.702964] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.806473] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   11.806555] HDA Intel 0000:01:05.1: setting latency timer to 64
[   12.054044] lp: driver loaded but no devices found
[   12.106626] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input10
[   12.155739] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input11
[   12.158183] Adding 3903784k swap on /dev/sda2.  Priority:-1 extents:1 across:3903784k
[   12.705189] EXT4 FS on sda1, internal journal on sda1:8
[   13.577271] EXT4-fs: barriers enabled
[   13.577610] kjournald2 starting.  Commit interval 5 seconds
[   13.577996] EXT4 FS on sda3, internal journal on sda3:8
[   13.577999] EXT4-fs: delayed allocation enabled
[   13.578001] EXT4-fs: file extents enabled
[   13.591634] EXT4-fs: mballoc enabled
[   13.591639] EXT4-fs: mounted filesystem with ordered data mode.
[   13.860488] type=1505 audit(1240967426.227:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2153
[   13.917318] type=1505 audit(1240967426.283:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2157
[   13.917468] type=1505 audit(1240967426.283:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2157
[   13.917526] type=1505 audit(1240967426.283:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2157
[   13.917578] type=1505 audit(1240967426.283:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2157
[   14.082050] type=1505 audit(1240967426.447:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2162
[   14.082270] type=1505 audit(1240967426.447:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2162
[   14.146001] type=1505 audit(1240967426.511:9): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=2166
[   14.178379] type=1505 audit(1240967426.543:10): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2170
[   18.678059] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   18.678064] vboxdrv: Successfully done.
[   18.678066] vboxdrv: Found 2 processor cores.
[   18.679270] vboxdrv: fAsync=1 offMin=0x150ccfc offMax=0x150ccfc
[   18.679354] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
[   18.679357] vboxdrv: Successfully loaded version 2.1.4_OSE (interface 0x000a0009).
[   19.725202] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.725207] Bluetooth: BNEP filters: protocol multicast
[   19.744105] Bridge firewalling registered
[   21.158721] ppdev: user-space parallel port driver
[   22.525630] [fglrx] GART Table is not in FRAME_BUFFER range 
[   22.566159] fglrx_pci 0000:01:05.0: irq 2298 for MSI/MSI-X
[   22.579356] [fglrx] Firegl kernel thread PID: 3476
[   22.586070] APIC error on CPU0: 00(08)
[   22.586077] APIC error on CPU1: 00(08)
[   22.655191] [fglrx] Gart USWC size:815 M.
[   22.655196] [fglrx] Gart cacheable size:60 M.
[   22.655204] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   22.655208] [fglrx] Reserved FB block: Unshared offset:fffb000, size:5000 
[   24.636533] tg3 0000:06:00.0: irq 2297 for MSI/MSI-X
[   24.785637] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.665581] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.386850] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   26.386854] tg3: eth0: Flow control is off for TX and off for RX.
[   26.387072] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   27.591400] wlan0: authenticate with AP 00:21:91:86:47:b7
[   27.789061] wlan0: authenticate with AP 00:21:91:86:47:b7
[   27.989068] wlan0: authenticate with AP 00:21:91:86:47:b7
[   28.189064] wlan0: authentication with AP 00:21:91:86:47:b7 timed out
[   36.700061] eth0: no IPv6 routers present

```lspci:```
[~]$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Acer Incorporated [ALI] Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:09.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 4)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
06:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe (rev 10)
```lsusb:```
[~]$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 064e:a103 Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 004: ID 045e:00d2 Microsoft Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```lshw:```
[~]$ sudo lshw
gil-laptop                
    description: Notebook
    product: Aspire 5530
    vendor: Acer
    version: V1.11
    serial: LXAPV0X024834069771601
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: boot=normal chassis=notebook cpus=2 uuid=66393437-3232-6235-6261-001EEC5D8C80
  *-core
       description: Motherboard
       product: Cinder Cone
       vendor: Acer
       physical id: 0
       version: N/A
       serial: LXAPV0X0xxxxxxxxxxxxxx
       slot: ATI RS780MN
     *-firmware
          description: BIOS
          vendor: Acer
          physical id: 0
          version: V1.11 (08/06/2008)
          size: 115KiB
          capacity: 960KiB
          capabilities: pci pnp upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: AMD Athlon(tm) X2 Dual-Core QL-60
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.3.1
          slot: Socket S1G2
          size: 1GHz
          capacity: 1900MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow constant_tsc pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch osvw skinit cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 128KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: H0 L2 Cache
             size: 512KiB
             capacity: 2MiB
             capabilities: synchronous internal write-through unified
     *-memory
          description: System Memory
          physical id: 18
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM Synchronous
             physical id: 0
             slot: S1
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: DIMM Synchronous
             physical id: 1
             slot: S2
             size: 1GiB
             width: 64 bits
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 15.3.1
          size: 1GHz
          capacity: 1GHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-pci:0
          description: Host bridge
          product: RS780 Host Bridge
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: Acer Incorporated [ALI]
             vendor: Acer Incorporated [ALI]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht bus_master cap_list
           *-display
                description: VGA compatible controller
                product: RS780M/RS780MN [Radeon HD 3200 Graphics]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi bus_master cap_list
                configuration: driver=fglrx_pci latency=0 module=fglrx
           *-multimedia
                description: Audio device
                product: RS780 Azalia controller
                vendor: ATI Technologies Inc
                physical id: 5.1
                bus info: pci@0000:01:05.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi bus_master cap_list
                configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:1
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 0)
             vendor: Advanced Micro Devices [AMD]
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 2)
             vendor: Advanced Micro Devices [AMD]
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: AR242x 802.11abg Wireless PCI Express Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: wmaster0
                version: 01
                serial: 00:22:69:6a:a3:59
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list logical wireless
                configuration: broadcast=yes driver=ath5k_pci latency=0 module=ath5k multicast=yes promiscuous=yes wireless=IEEE 802.11bg
        *-pci:3
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 3)
             vendor: Advanced Micro Devices [AMD]
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: NetXtreme BCM5764M Gigabit Ethernet PCIe
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:06:00.0
                logical name: eth0
                version: 10
                serial: 00:1e:ec:5d:8c:80
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full ip=10.2.51.160 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
        *-pci:4
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 4)
             vendor: Advanced Micro Devices [AMD]
             physical id: 9
             bus info: pci@0000:00:09.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport-driver
        *-storage
             description: SATA controller
             product: SB700/SB800 SATA Controller [IDE mode]
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi0
             logical name: scsi1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm bus_master cap_list emulated
             configuration: driver=ahci latency=64 module=ahci
           *-disk
                description: ATA Disk
                product: Hitachi HTS54321
                vendor: Hitachi
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: FB2O
                serial: 080805FB2200LCCDKPUA
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0f8000b1
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 339a2467-59ce-42ce-8f8c-01b85ec00d5e
                   size: 9538MiB
                   capacity: 9538MiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2009-04-26 16:48:01 filesystem=ext4 modified=2009-04-29 01:11:26 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2009-04-28 18:38:07 state=mounted
              *-volume:1
                   description: Linux swap volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 1
                   serial: 1552bf1e-3666-4443-87c5-bcc9b3fe2df3
                   size: 3812MiB
                   capacity: 3812MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
              *-volume:2
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /home
                   version: 1.0
                   serial: 2576e4b8-7502-4e89-a813-b97da3e3595a
                   size: 136GiB
                   capacity: 136GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2009-04-14 19:20:02 filesystem=ext4 modified=2009-04-29 08:10:25 mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered mounted=2009-04-29 08:10:25 state=mounted
           *-cdrom
                description: DVD-RAM writer
                product: DVD RW AD-7560S
                vendor: Optiarc
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: SX07
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-usb:0
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
        *-usb:1
             description: USB Controller
             product: SB700 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 12.1
             bus info: pci@0000:00:12.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
        *-usb:2
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd
        *-usb:3
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
        *-usb:4
             description: USB Controller
             product: SB700 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
        *-usb:5
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 3a
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=64 module=snd_hda_intel
        *-isa
             description: ISA bridge
             product: SB700/SB800 LPC host controller
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:5
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
     *-pci:1
          description: Host bridge
          product: Family 11h HyperTransport Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 40
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 11h Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 11h DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 11h Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Family 11h Link Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 46:fe:98:22:1d:4b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

---

### Post by mr.tapac on 2009-04-29
Suddenly, I can't found our Card Reader in list (lspci and lshw).

Acer (via hotline) says:
> It's [FONT=sans-serif][SIZE=2]JMB38X   (JMB385 [/SIZE][/FONT][SIZE=3]Card Reader[/SIZE][FONT=sans-serif][SIZE=2])[/SIZE][/FONT] 
[FONT=sans-serif][SIZE=2] JMicron Technology Corp.[/SIZE][/FONT] 
see  [FONT=sans-serif][SIZE=2][http://www.jmicron.com/Product_JMB38X.htm](http://www.jmicron.com/Product_JMB38X.htm)[/SIZE][/FONT]


Thanks. I'm going to google it! :)

---

### Post by mr.tapac on 2009-04-29
Hmm..

I try to boot with SD card inserted. And... it's mounted correctly!
lspci have more 4 lines "JMicron bla-bla-bla",
lsmod contains sdhci_pci..

How to make it works without boot with SD card inserted? :)

---

