---
title: "BIOS bug, local APIC #0 not detected!... BUT works with Windows Vista"
date: 2009-05-22
forum: Hardware
---

### Post by thomas_a55 on 2009-05-22
Ubuntu 9.04 (32 bits) on Advent 5544 (yes - I know about the Advent model no's.... please, check lshw output) - get:" BIOS bug, local APIC #0 not detected!..." during startup, must use nolapic to start at all. After installation only one cpu core is started (Intel T1500 dual core cpu). Windows Vista has no problems to bring up both cores - also no messages about local apic problems.......

Would appreciate any advice on how to get Ubuntu to bring up both cores. Here is the dmseg (and after it the lshw output):
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
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000077d90000 (usable)
[    0.000000]  BIOS-e820: 0000000077d90000 - 0000000077d9b000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000077d9b000 - 0000000077d9c000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000077d9c000 - 0000000078000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0x77d90 max_arch_pfn = 0x100000
[    0.000000] Scanning 2 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)
[    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000090c00 (usable)
[    0.000000]  modified: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 0000000077d90000 (usable)
[    0.000000]  modified: 0000000077d90000 - 0000000077d9b000 (ACPI data)
[    0.000000]  modified: 0000000077d9b000 - 0000000077d9c000 (ACPI NVS)
[    0.000000]  modified: 0000000077d9c000 - 0000000078000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.000000] RAMDISK: 378c2000 - 37fef170
[    0.000000] Allocated new RAMDISK: 00881000 - 00fae170
[    0.000000] Move RAMDISK from 00000000378c2000 - 0000000037fef16f to 00881000 - 00fae16f
[    0.000000] ACPI: RSDP 000F8580, 0024 (r2 PTLTD )
[    0.000000] ACPI: XSDT 77D91CB2, 0094 (r1 DSGLTD DSGVISTA  6040000  LTP        0)
[    0.000000] ACPI: FACP 77D9AB86, 00F4 (r3 SiS    671MX     6040000 PTL     F4240)
[    0.000000] ACPI: DSDT 77D95CCC, 4E46 (r1 PTLTD       671  6040000 MSFT  3000000)
[    0.000000] ACPI: FACS 77D9BFC0, 0040
[    0.000000] ACPI: APIC 77D9AC7A, 005E (r1 PTLTD       APIC    6040000  LTP        0)
[    0.000000] ACPI: SLIC 77D9ACD8, 0176 (r1 DSGLTD DSGVISTA  6040000  LTP        0)
[    0.000000] ACPI: MCFG 77D9AE4E, 003C (r1 PTLTD    MCFG    6040000  LTP        0)
[    0.000000] ACPI: SLIC 77D9AE8A, 0176 (r1 DSGLTD DSGVISTA  6040000  LTP        0)
[    0.000000] ACPI: SSDT 77D935F1, 025F (r1  PmRef  Cpu0Tst     3000 INTL 2005022
[    0.000000] ACPI: SSDT 77D9354B, 00A6 (r1  PmRef  Cpu7Tst     3000 INTL 2005022
[    0.000000] ACPI: SSDT 77D934A5, 00A6 (r1  PmRef  Cpu6Tst     3000 INTL 2005022
[    0.000000] ACPI: SSDT 77D933FF, 00A6 (r1  PmRef  Cpu5Tst     3000 INTL 2005022
[    0.000000] ACPI: SSDT 77D93359, 00A6 (r1  PmRef  Cpu4Tst     3000 INTL 2005022
[    0.000000] ACPI: SSDT 77D932B3, 00A6 (r1  PmRef  Cpu3Tst     3000 INTL 2005022
[    0.000000] ACPI: SSDT 77D9320D, 00A6 (r1  PmRef  Cpu2Tst     3000 INTL 2005022
[    0.000000] ACPI: SSDT 77D93167, 00A6 (r1  PmRef  Cpu1Tst     3000 INTL 2005022
[    0.000000] ACPI: SSDT 77D91D46, 1421 (r1  PmRef    CpuPm     3000 INTL 2005022
[    0.000000] 1033MB HIGHMEM available.
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
[    0.000000]   #7 [0000881000 - 0000fae170]      NEW RAMDISK ==> [0000881000 - 0000fae170]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] found SMP MP-table at [c00f85b0] 000f85b0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x00077d90
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x00000007
[    0.000000]     0: 0x00000010 -> 0x00000090
[    0.000000]     0: 0x00000100 -> 0x00077d90
[    0.000000] On node 0 totalpages: 490771
[    0.000000] free_area_init_node: node 0, pgdat c06d0f80, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3939 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2068 pages used for memmap
[    0.000000]   HighMem zone: 262526 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000]     Virtual Wire compatibility mode.
[    0.000000] MPTABLE: OEM ID: SiS     
[    0.000000] MPTABLE: Product ID: 671MX       
[    0.000000] MPTABLE: APIC at: 0xFEE00000
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] Processor #1
[    0.000000] I/O APIC #2 Version 20 at 0xFEC00000.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Processors: 2
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 0000000000090000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 78000000:68000000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 486935
[    0.000000] Kernel command line: root=UUID=4069bebc-8c45-40c5-938c-567f7587c05e ro nolapic quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1866.690 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 9817920 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 1921248k/1963584k available (4126k kernel code, 40940k reserved, 2208k data, 532k init, 1058376k highmem)
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
[    0.004018] Calibrating delay loop (skipped), value calculated using timer frequency.. 3733.38 BogoMIPS (lpj=7466760)
[    0.004044] Security Framework initialized
[    0.004057] SELinux:  Disabled at boot.
[    0.004086] AppArmor: AppArmor initialized
[    0.004096] Mount-cache hash table entries: 512
[    0.004274] Initializing cgroup subsys ns
[    0.004281] Initializing cgroup subsys cpuacct
[    0.004285] Initializing cgroup subsys memory
[    0.004289] Initializing cgroup subsys freezer
[    0.004307] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004310] CPU: L2 cache: 512K
[    0.004314] CPU: Physical Processor ID: 0
[    0.004316] CPU: Processor Core ID: 0
[    0.004321] using mwait in idle threads.
[    0.004336] Checking 'hlt' instruction... OK.
[    0.022777] ACPI: Core revision 20080926
[    0.025776] ACPI: Checking initramfs for custom DSDT
[    0.342187] ACPI: setting ELCR to 0800 (from 0eb
[    0.344081] BIOS bug, local APIC #0 not detected!...
[    0.344124] ... forcing use of dummy APIC emulation.(tell your hw vendor)
[    0.344165] SMP disabled
[    0.344411] Brought up 1 CPUs
[    0.344415] Total of 1 processors activated (3733.38 BogoMIPS).
[    0.344430] CPU0 attaching NULL sched-domain.
[    0.344769] net_namespace: 776 bytes
[    0.344794] Booting paravirtualized kernel on bare hardware
[    0.345050] Time: 15:36:16  Date: 05/22/09
[    0.345057] regulator: core version 0.5
[    0.345099] NET: Registered protocol family 16
[    0.345244] EISA bus registered
[    0.345266] ACPI: bus type pci registered
[    0.345349] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 0
[    0.345354] PCI: MCFG area at e0000000 reserved in E820
[    0.345356] PCI: Using MMCONFIG for extended config space
[    0.345358] PCI: Using configuration type 1 for base access
[    0.347237] ACPI: EC: Look up EC in DSDT
[    0.353027] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.353148] ACPI: Interpreter enabled
[    0.353148] ACPI: (supports S0 S3 S4 S5)
[    0.353148] ACPI: Using PIC for interrupt routing
[    0.359213] ACPI: EC: GPE = 0x13, I/O: command/status = 0x66, data = 0x62
[    0.359217] ACPI: EC: driver started in interrupt mode
[    0.359341] ACPI: No dock devices found.
[    0.359355] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.359416] pci 0000:00:00.0: reg 10 32bit mmio: [0xa0000000-0xafffffff]
[    0.359576] pci 0000:00:02.5: reg 10 io port: [0x1f0-0x1f7]
[    0.359583] pci 0000:00:02.5: reg 14 io port: [0x3f4-0x3f7]
[    0.359591] pci 0000:00:02.5: reg 18 io port: [0x170-0x177]
[    0.359598] pci 0000:00:02.5: reg 1c io port: [0x374-0x377]
[    0.359605] pci 0000:00:02.5: reg 20 io port: [0x1080-0x108f]
[    0.359628] pci 0000:00:02.5: PME# supported from D3cold
[    0.359633] pci 0000:00:02.5: PME# disabled
[    0.359660] pci 0000:00:03.0: reg 10 32bit mmio: [0xb0104000-0xb0104fff]
[    0.359715] pci 0000:00:03.1: reg 10 32bit mmio: [0xb0105000-0xb0105fff]
[    0.359782] pci 0000:00:03.3: reg 10 32bit mmio: [0xb0106000-0xb0106fff]
[    0.359823] pci 0000:00:03.3: PME# supported from D0 D3hot D3cold
[    0.359828] pci 0000:00:03.3: PME# disabled
[    0.359868] pci 0000:00:04.0: reg 10 32bit mmio: [0xb0307000-0xb030707f]
[    0.359876] pci 0000:00:04.0: reg 14 io port: [0x1000-0x107f]
[    0.359912] pci 0000:00:04.0: supports D1 D2
[    0.359914] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.359918] pci 0000:00:04.0: PME# disabled
[    0.359959] pci 0000:00:05.0: reg 10 io port: [0x10c8-0x10cf]
[    0.359966] pci 0000:00:05.0: reg 14 io port: [0x10bc-0x10bf]
[    0.359973] pci 0000:00:05.0: reg 18 io port: [0x10c0-0x10c7]
[    0.359981] pci 0000:00:05.0: reg 1c io port: [0x10b8-0x10bb]
[    0.359988] pci 0000:00:05.0: reg 20 io port: [0x10a0-0x10af]
[    0.360027] pci 0000:00:05.0: PME# supported from D3cold
[    0.360031] pci 0000:00:05.0: PME# disabled
[    0.360080] pci 0000:00:0f.0: reg 10 32bit mmio: [0xb0100000-0xb0103fff]
[    0.360122] pci 0000:00:0f.0: PME# supported from D0 D3hot D3cold
[    0.360126] pci 0000:00:0f.0: PME# disabled
[    0.360191] pci 0000:01:00.0: reg 10 32bit mmio: [0xc0000000-0xcfffffff]
[    0.360197] pci 0000:01:00.0: reg 14 32bit mmio: [0xb0000000-0xb001ffff]
[    0.360204] pci 0000:01:00.0: reg 18 io port: [0x9000-0x907f]
[    0.360228] pci 0000:01:00.0: supports D1 D2
[    0.360271] pci 0000:00:01.0: bridge io port: [0x9000-0x9fff]
[    0.360276] pci 0000:00:01.0: bridge 32bit mmio: [0xb0000000-0xb00fffff]
[    0.360281] pci 0000:00:01.0: bridge 32bit mmio pref: [0xc0000000-0xcfffffff]
[    0.360290] bus 00 -> node 0
[    0.360299] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.367197] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 *9 10 11)
[    0.367324] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 7 9 10 11)
[    0.367445] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 *4 5 7 9 10 11)
[    0.367566] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 7 9 10 11)
[    0.367713] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 *11)
[    0.367834] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 *10 11)
[    0.367955] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 *7 9 10 11)
[    0.368097] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11) *0, disabled.
[    0.368467] ACPI: WMI: Mapper loaded
[    0.368694] SCSI subsystem initialized
[    0.368755] libata version 3.00 loaded.
[    0.368816] usbcore: registered new interface driver usbfs
[    0.368836] usbcore: registered new interface driver hub
[    0.368874] usbcore: registered new device driver usb
[    0.369014] PCI: Using ACPI for IRQ routing
[    0.369117] Bluetooth: Core ver 2.13
[    0.369117] NET: Registered protocol family 31
[    0.369117] Bluetooth: HCI device and connection manager initialized
[    0.369117] Bluetooth: HCI socket layer initialized
[    0.369117] NET: Registered protocol family 8
[    0.369117] NET: Registered protocol family 20
[    0.369117] NetLabel: Initializing
[    0.369117] NetLabel:  domain hash size = 128
[    0.369117] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.369117] NetLabel:  unlabeled traffic allowed by default
[    0.369117] AppArmor: AppArmor Filesystem Enabled
[    0.369117] pnp: PnP ACPI init
[    0.369117] ACPI: bus type pnp registered
[    0.369581] pnp 00:05: IRQ 13 override to level, low
[    0.369585] PCI: setting IRQ 13 as level-triggered
[    0.369717] pnp 00:07: IRQ 12 override to level, low
[    0.369720] PCI: setting IRQ 12 as level-triggered
[    0.372128] pnp: PnP ACPI: found 10 devices
[    0.372131] ACPI: ACPI bus type pnp unregistered
[    0.372137] PnPBIOS: Disabled by ACPI PNP
[    0.372154] system 00:04: ioport range 0x8000-0x80be has been reserved
[    0.372157] system 00:04: ioport range 0x8100-0x812f has been reserved
[    0.372160] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[    0.372162] system 00:04: ioport range 0xfe00-0xfe00 has been reserved
[    0.372165] system 00:04: ioport range 0x200-0x20f has been reserved
[    0.372168] system 00:04: ioport range 0x290-0x297 has been reserved
[    0.372172] system 00:04: iomem range 0xe0000000-0xefffffff has been reserved
[    0.372175] system 00:04: iomem range 0xfec00000-0xfecfffff could not be reserved
[    0.372178] system 00:04: iomem range 0xfee00000-0xfeefffff could not be reserved
[    0.372181] system 00:04: iomem range 0xffb80000-0xffbfffff has been reserved
[    0.372183] system 00:04: iomem range 0xffc00000-0xffc00fff has been reserved
[    0.372186] system 00:04: iomem range 0xffe00000-0xffe00fff has been reserved
[    0.372189] system 00:04: iomem range 0xffe80000-0xffefffff has been reserved
[    0.406902] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.406906] pci 0000:00:01.0:   IO window: 0x9000-0x9fff
[    0.406912] pci 0000:00:01.0:   MEM window: 0xb0000000-0xb00fffff
[    0.406917] pci 0000:00:01.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff
[    0.406934] pci 0000:00:01.0: setting latency timer to 64
[    0.406938] bus: 00 index 0 io port: [0x00-0xffff]
[    0.406940] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.406943] bus: 01 index 0 io port: [0x9000-0x9fff]
[    0.406945] bus: 01 index 1 mmio: [0xb0000000-0xb00fffff]
[    0.406947] bus: 01 index 2 mmio: [0xc0000000-0xcfffffff]
[    0.406949] bus: 01 index 3 mmio: [0x0-0x0]
[    0.406962] NET: Registered protocol family 2
[    0.407104] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.407400] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.408448] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.409026] TCP: Hash tables configured (established 131072 bind 65536)
[    0.409032] TCP reno registered
[    0.409230] NET: Registered protocol family 1
[    0.409405] checking if image is initramfs... it is
[    0.908047] Switched to high resolution mode on CPU 0
[    1.059061] Freeing initrd memory: 7348k freed
[    1.059214] cpufreq: No nForce2 chipset.
[    1.059380] audit: initializing netlink socket (disabled)
[    1.059409] type=2000 audit(1243006576.056:1): initialized
[    1.066881] highmem bounce pool size: 64 pages
[    1.066888] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.068335] VFS: Disk quotas dquot_6.5.1
[    1.068422] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.069102] fuse init (API version 7.10)
[    1.069206] msgmni has been set to 1701
[    1.069436] alg: No test for stdrng (krng)
[    1.069455] io scheduler noop registered
[    1.069457] io scheduler anticipatory registered
[    1.069459] io scheduler deadline registered
[    1.069486] io scheduler cfq registered (default)
[    1.069558] pci 0000:01:00.0: Boot video device
[    1.073028] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.073039] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.073510] ACPI: AC Adapter [AC0] (on-line)
[    1.084556] ACPI: Battery Slot [BAT0] (battery present)
[    1.084656] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.084660] ACPI: Power Button (FF) [PWRF]
[    1.084720] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.084722] ACPI: Power Button (CM) [PWRB]
[    1.084768] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.084774] ACPI: Sleep Button (CM) [SLPB]
[    1.084823] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[    1.085197] ACPI: Lid Switch [LID0]
[    1.086579] ACPI: SSDT 77D93850, 0518 (r1  PmRef  Cpu0Cst     3001 INTL 2005022
[    1.087178] Monitor-Mwait will be used to enter C-1 state
[    1.087182] Monitor-Mwait will be used to enter C-2 state
[    1.087184] Monitor-Mwait will be used to enter C-3 state
[    1.087214] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.087256] processor ACPI_CPU:00: registered as cooling_device0
[    1.087261] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.092740] thermal LNXTHERM:01: registered as thermal_zone0
[    1.095050] ACPI: Thermal Zone [TZ01] (48 C)
[    1.095127] isapnp: Scanning for PnP cards...
[    1.448591] isapnp: No Plug & Play device found
[    1.449903] hpet_acpi_add: no address or irqs in _CRS
[    1.449944] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.451092] brd: module loaded
[    1.451463] loop: module loaded
[    1.451567] Fixed MDIO Bus: probed
[    1.451574] PPP generic driver version 2.4.2
[    1.451642] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    1.451687] Driver 'sd' needs updating - please use bus_type methods
[    1.451698] Driver 'sr' needs updating - please use bus_type methods
[    1.451861] sata_sis 0000:00:05.0: version 1.0
[    1.452151] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[    1.452154] PCI: setting IRQ 5 as level-triggered
[    1.452159] sata_sis 0000:00:05.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[    1.452165] sata_sis 0000:00:05.0: Detected SiS 1183/966/966L/968/680 controller in PATA mode
[    1.452294] scsi0 : sata_sis
[    1.452423] scsi1 : sata_sis
[    1.452941] ata1: PATA max UDMA/133 cmd 0x10c8 ctl 0x10bc bmdma 0x10a0 irq 5
[    1.452944] ata2: PATA max UDMA/133 cmd 0x10c0 ctl 0x10b8 bmdma 0x10a8 irq 5
[    1.660427] ata1.00: ATA-8: WDC WD1600BEVT-75ZCT2, 11.01A11, max UDMA/133
[    1.660430] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.677386] ata1.00: configured for UDMA/133
[    1.842907] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600BEVT-7 11.0 PQ: 0 ANSI: 5
[    1.843045] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[    1.843063] sd 0:0:0:0: [sda] Write Protect is off
[    1.843065] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.843091] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.843177] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[    1.843191] sd 0:0:0:0: [sda] Write Protect is off
[    1.843194] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.843218] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.843222]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    1.877232] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.877295] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.877733] pata_sis 0000:00:02.5: version 0.5.2
[    1.877996] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 9
[    1.878000] PCI: setting IRQ 9 as level-triggered
[    1.878005] pata_sis 0000:00:02.5: PCI INT A -> Link[LNKA] -> GSI 9 (level, low) -> IRQ 9
[    1.878147] scsi2 : pata_sis
[    1.878236] scsi3 : pata_sis
[    1.878599] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x1080 irq 14
[    1.878602] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x1088 irq 15
[    2.056263] ata3.00: ATAPI: TSSTcorp CDDVDW TS-L632H, TMC0, max UDMA/33
[    2.088280] ata3.00: configured for UDMA/33
[    2.088731] ata4: port disabled. ignoring.
[    2.091155] scsi 2:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L632H  TMC0 PQ: 0 ANSI: 5
[    2.101921] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.101926] Uniform CD-ROM driver Revision: 3.20
[    2.102077] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    2.102136] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    2.102279] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.102523] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 7
[    2.102526] PCI: setting IRQ 7 as level-triggered
[    2.102531] ehci_hcd 0000:00:03.3: PCI INT C -> Link[LNKG] -> GSI 7 (level, low) -> IRQ 7
[    2.102560] ehci_hcd 0000:00:03.3: EHCI Host Controller
[    2.102662] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 1
[    2.102707] ehci_hcd 0000:00:03.3: irq 7, io mem 0xb0106000
[    2.112037] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00
[    2.112133] usb usb1: configuration #1 chosen from 1 choice
[    2.112165] hub 1-0:1.0: USB hub found
[    2.112174] hub 1-0:1.0: 8 ports detected
[    2.112319] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.112580] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[    2.112582] PCI: setting IRQ 11 as level-triggered
[    2.112587] ohci_hcd 0000:00:03.0: PCI INT A -> Link[LNKE] -> GSI 11 (level, low) -> IRQ 11
[    2.112607] ohci_hcd 0000:00:03.0: OHCI Host Controller
[    2.112679] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 2
[    2.112697] ohci_hcd 0000:00:03.0: irq 11, io mem 0xb0104000
[    2.168118] usb usb2: configuration #1 chosen from 1 choice
[    2.168148] hub 2-0:1.0: USB hub found
[    2.168157] hub 2-0:1.0: 4 ports detected
[    2.168458] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 10
[    2.168462] PCI: setting IRQ 10 as level-triggered
[    2.168467] ohci_hcd 0000:00:03.1: PCI INT B -> Link[LNKF] -> GSI 10 (level, low) -> IRQ 10
[    2.168485] ohci_hcd 0000:00:03.1: OHCI Host Controller
[    2.168560] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 3
[    2.168578] ohci_hcd 0000:00:03.1: irq 10, io mem 0xb0105000
[    2.226089] usb usb3: configuration #1 chosen from 1 choice
[    2.226126] hub 3-0:1.0: USB hub found
[    2.226134] hub 3-0:1.0: 4 ports detected
[    2.226247] uhci_hcd: USB Universal Host Controller Interface driver
[    2.226332] usbcore: registered new interface driver libusual
[    2.226371] usbcore: registered new interface driver usbserial
[    2.226382] USB Serial support registered for generic
[    2.226396] usbcore: registered new interface driver usbserial_generic
[    2.226399] usbserial: USB Serial Driver core
[    2.226455] PNP: PS/2 Controller [PNP0303S2K,PNP0f13S2M] at 0x60,0x64 irq 1,12
[    2.231229] i8042.c: Detected active multiplexing controller, rev 1.1.
[    2.232164] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.232171] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    2.232173] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    2.232176] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    2.232178] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    2.232375] mice: PS/2 mouse device cmmon for all mice
[    2.232638] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    2.232659] rtc0: alarms up to one year, y3k, 114 bytes nvram
[    2.232744] device-mapper: uevent: version 1.0.3
[    2.232892] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    2.232956] device-mapper: multipath: version 1.0.5 loaded
[    2.232959] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.233080] EISA: Probing bus 0 at eisa.0
[    2.233088] Cannot allocate resource for EISA slot 1
[    2.233113] Cannot allocate resource for EISA slot 8
[    2.233115] EISA: Detected 0 cards.
[    2.233202] cpuidle: using governor ladder
[    2.233268] cpuidle: using governor menu
[    2.233835] TCP cubic registered
[    2.233954] NET: Registered protocol family 10
[    2.234419] lo: Disabled Privacy Extensions
[    2.234773] NET: Registered protocol family 17
[    2.234802] Bluetooth: L2CAP ver 2.11
[    2.234804] Bluetooth: L2CAP socket layer initialized
[    2.234807] Bluetooth: SCO (Voice Link) ver 0.6
[    2.234808] Bluetooth: SCO socket layer initialized
[    2.234856] Bluetooth: RFCOMM socket layer initialized
[    2.234867] Bluetooth: RFCOMM TTY layer initialized
[    2.234869] Bluetooth: RFCOMM ver 1.10
[    2.234933] Using IPI No-Shortcut mode
[    2.235045] registered taskstats version 1
[    2.235139]   Magic number: 9:817:639
[    2.235228] rtc_cmos 00:02: setting system clock to 2009-05-22 15:36:18 UTC (124300657
[    2.235231] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.235233] EDD information not available.
[    2.235556] Freeing unused kernel memory: 532k freed
[    2.235747] Write protecting the kernel text: 4128k
[    2.235793] Write protecting the kernel read-only data: 1532k
[    2.424048] usb 1-6: new high speed USB device using ehci_hcd and address 2
[    2.463303] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    3.115682] usb 1-6: configuration #1 chosen from 1 choice
[    3.149798] Initializing USB Mass Storage driver...
[    3.170344] scsi4 : SCSI emulation for USB Mass Storage devices
[    3.173120] usbcore: registered new interface driver usb-storage
[    3.173126] USB Mass Storage support registered.
[    3.173281] usb-storage: device found at 2
[    3.173283] usb-storage: waiting for device to settle before scanning
[    3.260078] usb 1-7: new high speed USB device using ehci_hcd and address 3
[    3.429555] Marking TSC unstable due to TSC halts in idle
[    3.699986] usb 1-7: configuration #1 chosen from 1 choice
[    3.799634] PM: Starting manual resume from disk
[    3.799640] PM: Resume from partition 8:6
[    3.799641] PM: Checking hibernation image.
[    3.799930] PM: Resume from disk failed.
[    3.823374] kjournald starting.  Commit interval 5 seconds
[    3.823391] EXT3-fs: mounted filesystem with ordered data mode.
[    8.172416] usb-storage: device scan complete
[    8.178782] scsi 4:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[    8.180139] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[    8.180214] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    9.444085] udev: starting version 141
[    9.603397] acpi device:0f: registered as cooling_device1
[    9.603639] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:0c/device:0d/input/input6
[    9.636247] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    9.641170] Linux agpgart interface v0.103
[    9.667596] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    9.684326] agpgart-sis 0000:00:00.0: SiS chipset [1039/0671]
[    9.701132] agpgart-sis 0000:00:00.0: AGP aperture is 256M @ 0xa0000000
[    9.870566] Linux video capture interface: v2.00
[   10.045703] sis190 Gigabit Ethernet driver 1.2 loaded.
[   10.045963] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 3
[   10.045968] PCI: setting IRQ 3 as level-triggered
[   10.045972] sis190 0000:00:04.0: PCI INT A -> Link[LNKD] -> GSI 3 (level, low) -> IRQ 3
[   10.045986] sis190 0000:00:04.0: setting latency timer to 64
[   10.046057] 0000:00:04.0: Read MAC address from EEPROM
[   10.101480] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   10.132060] 0000:00:04.0: Realtek PHY RTL8201 transceiver at address 1.
[   10.136384] uvcvideo: Found UVC 1.00 device USB2.0 Camera (5986:0200)
[   10.139622] input: USB2.0 Camera as /devices/pci0000:00/0000:00:03.3/usb1/1-7/1-7:1.0/input/input8
[   10.152336] usbcore: registered new interface driver uvcvideo
[   10.152378] USB Video Class driver (v0.1.0)
[   10.239097] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   10.640065] 0000:00:04.0: Using transceiver at address 1 as default.
[   10.672887] 0000:00:04.0: SiS 191 PCI Gigabit Ethernet adapter at f7cd0000 (IRQ: 3), 00:03:0d:b3:9f:09
[   10.672891] eth0: GMII mode.
[   10.672899] eth0: Enabling Auto-negotiation.
[   10.747413] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 4
[   10.747418] PCI: setting IRQ 4 as level-triggered
[   10.747423] HDA Intel 0000:00:0f.0: PCI INT A -> Link[LNKC] -> GSI 4 (level, low) -> IRQ 4
[   10.747548] HDA Intel 0000:00:0f.0: setting latency timer to 64
[   10.777987] hda_codec: Unknown model for ALC662, trying auto-probe from BIOS...
[   10.996407] lp: driver loaded but no devices found
[   11.112988] Adding 1638588k swap on /dev/sda6.  Priority:-1 extents:1 across:1638588k
[   11.154603] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04711/0x200000
[   11.200504] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input9
[   11.676434] EXT3 FS on sda5, internal journal
[   12.876320] type=1505 audit(1242999389.140:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1942
[   12.931721] type=1505 audit(1242999389.192:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1946
[   12.931948] type=1505 audit(1242999389.192:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1946
[   12.932073] type=1505 audit(1242999389.196:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1946
[   12.932155] type=1505 audit(1242999389.196:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1946
[   13.082999] type=1505 audit(1242999389.344:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1951
[   13.083312] type=1505 audit(1242999389.344:: operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1951
[   13.118710] type=1505 audit(1242999389.380:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1955
[   14.591640] ip_tables: (C) 2000-2006 Netfilter Core Team
[   14.618474] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   14.618726] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   14.618729] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
[   14.618731] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   20.023169] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.023173] Bluetooth: BNEP filters: protocol multicast
[   20.050337] Bridge firewalling registered
[   21.821559] ppdev: user-space parallel port driver
[   25.736636] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   35.768054] eth0: mii ext = 0000.
[   35.784055] eth0: mii lpa = cde1 adv = 01e1.
[   35.784060] eth0: link on 100 Mbps Full Duplex mode.
[   35.784351] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   38.356114] R3#2 - IN= OUT=eth0 SRC=192.168.166.108 DST=224.0.0.22 LEN=40 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[   39.337326] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
***********************************************************************************
lshw output:


advent5544                
    description: Notebook
    product: DIXONSXP
    vendor: DIXONSXP
    serial: **************************
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: administrator_password=enabled boot=oem-specific chassis=notebook cpus=2 frontpanel_password=unknown keyboard_password=unknown power-on_password=enabled uuid=802C2561-5E65-0010-A062-8E2C25690007
  *-core
       description: Motherboard
       product: N/A
       vendor: DIXONSXP
       physical id: 0
       version: N/A
       serial: 1234AA782E
     *-firmware
          description: BIOS
          vendor: OEM
          physical id: 0
          version: 1.14 (11/05/200
          size: 107KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppynec int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Genuine Intel(R) CPU           T1500  @ 1.86GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          slot: uPGA 479M
          size: 1860MHz
          capacity: 3600MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm lahf_lm
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 16KiB
             capacity: 16KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 512KiB
             capacity: 1MiB
             capabilities: burst internal write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-cache
          description: L3 cache
          physical id: 7
          slot: L3 Cache
          size: 512KiB
          capacity: 512KiB
          capabilities: burst internal write-back
     *-memory
          description: System Memory
          physical id: e
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: DIMM1
             size: 2GiB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM [empty]
             physical id: 1
             slot: DIMM2
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          size: 1900MHz
          capabilities: ht
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: 671MX
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-sis latency=32 module=sis_agp
        *-pci
             description: PCI bridge
             product: SiS AGP Port (virtual PCI-to-PCI bridge)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
           *-display UNCLAIMED
                description: VGA compatible controller
                product: 771/671 PCIE VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 10
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 cap_list
                configuration: latency=0
        *-isa
             description: ISA bridge
             product: SiS968 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             logical name: scsi2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_sis latency=128
           *-cdrom
                description: DVD-RAM writer
                product: CDDVDW TS-L632H
                vendor: TSSTcorp
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: TMC0
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-usb:0
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80
        *-usb:1
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80
        *-usb:2
             description: USB Controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=32 maxlatency=80 module=ehci_hcd
        *-network
             description: Ethernet interface
             product: 191 Gigabit Ethernet Adapter
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: 02
             serial: 00:03:0d:b3:9f:09
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=sis190 driverversion=1.2 duplex=full ip=192.168.166.108 latency=0 link=yes module=sis190 multicast=yes port=MII speed=100MB/s
        *-ide:1
             description: IDE interface
             product: SATA Controller / IDE mode
             vendor: Silicon Integrated Systems [SiS]
             physical id: 5
             bus info: pci@0000:00:05.0
             logical name: scsi0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=sata_sis latency=32
           *-disk
                description: ATA Disk
                product: WDC WD1600BEVT-7
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 11.0
                serial: WD-WXC708945724
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=ae20f311
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 0c55a04d-a008-124d-ae9c-914065074172
                   size: 5498MiB
                   capacity: 5500MiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2009-04-21 19:06:17 filesystem=ntfs label=Recovery state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: cca51e68-398a-4641-b903-d84fd2e5fa29
                   size: 1470MiB
                   capacity: 1500MiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2009-04-21 19:06:22 filesystem=ntfs label=System state=clean
              *-volume:2
                   description: Windows NTFS volume
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   version: 3.1
                   serial: 6c87673a-0159-9b48-90e3-d2e992e5692f
                   size: 55GiB
                   capacity: 55GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2009-04-25 00:49:19 filesystem=ntfs label=Vista modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   size: 86GiB
                   capacity: 86GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 84GiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 1600MiB
                      capabilities: nofs
        *-multimedia
             description: Audio device
             product: Azalia Audio Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=0 maxlatency=11 mingnt=52 module=snd_hda_intel
     *-scsi
          physical id: 2
          bus info: usb@1:6
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
  *-battery
       physical id: 1
       slot: MAIN
       capacity: 32560mWh
       configuration: voltage=14.8V
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 5e:87:ef:ee:66:ec
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

