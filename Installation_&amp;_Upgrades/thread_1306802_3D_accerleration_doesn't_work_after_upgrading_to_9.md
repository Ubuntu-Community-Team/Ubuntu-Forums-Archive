---
title: "3D accerleration doesn't work after upgrading to 9.10 (using ATI radeon 9200)"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by trldp on 2009-10-30
After I upgraded to ubuntu 9.10 the 3D acceleration doesn't work anymore. I have an ATI radeon 9200 card (so, free drivers are available). Before my upgrade everything went fine. Now I'm using the 2.6.31-14 kernel, but also with the old kernel it doesn't work.

Here is the dmesg output:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-14-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 (Ubuntu 2.6.31-14.48-generic)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ffc0000 (usable)
[    0.000000]  BIOS-e820: 000000001ffc0000 - 000000001ffd0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001ffd0000 - 0000000020000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x1ffc0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FFE0000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000001ffc0000 (usable)
[    0.000000]  modified: 000000001ffc0000 - 000000001ffd0000 (ACPI data)
[    0.000000]  modified: 000000001ffd0000 - 0000000020000000 (ACPI NVS)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-000000001ffc0000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 001fc00000 page 2M
[    0.000000]  001fc00000 - 001ffc0000 page 4k
[    0.000000] kernel direct mapping tables up to 1ffc0000 @ 10000-15000
[    0.000000] RAMDISK: 1f80e000 - 1ffaf9f5
[    0.000000] ACPI: RSDP 000f9ed0 00021 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 1ffc0100 0003C (v01 A M I  OEMXSDT  02000616 MSFT 00000097)
[    0.000000] ACPI: FACP 1ffc0290 000F4 (v03 A M I  OEMFACP  02000616 MSFT 00000097)
[    0.000000] ACPI Warning: 32/64X length mismatch in Gpe1Block: 0/32 20090521 tbfadt-527
[    0.000000] ACPI Warning: Optional field Gpe1Block has zero address or length: 00000000000044A0/0 20090521 tbfadt-558
[    0.000000] ACPI: DSDT 1ffc0400 04D76 (v01  A0342 A0342003 00000003 INTL 02002026)
[    0.000000] ACPI: FACS 1ffd0000 00040
[    0.000000] ACPI: APIC 1ffc0390 00068 (v01 A M I  OEMAPIC  02000616 MSFT 00000097)
[    0.000000] ACPI: OEMB 1ffd0040 00041 (v01 A M I  OEMBIOS  02000616 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 1ffc0000
[    0.000000]   low ram: 0 - 1ffc0000
[    0.000000]   node 0 low ram: 00000000 - 1ffc0000
[    0.000000]   node 0 bootmap 00011000 - 00014ff8
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 001ffc0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
[    0.000000]   #4 [001f80e000 - 001ffaf9f5]          RAMDISK ==> [001f80e000 - 001ffaf9f5]
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #6 [00008a9000 - 00008ac174]              BRK ==> [00008a9000 - 00008ac174]
[    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #8 [0000011000 - 0000015000]          BOOTMAP ==> [0000011000 - 0000015000]
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] Reserving 64MB of memory at 16MB for crashkernel (System RAM: 511MB)
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0001ffc0
[    0.000000]   HighMem  0x0001ffc0 -> 0x0001ffc0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0001ffc0
[    0.000000] On node 0 totalpages: 130895
[    0.000000] free_area_init_node: node 0, pgdat c0784900, node_mem_map c5000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 992 pages used for memmap
[    0.000000]   Normal zone: 125920 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 20000000:dec00000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c5402000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 129871
[    0.000000] Kernel command line: root=UUID=659c1eb0-a9fc-4ad9-a209-4624af1b05af ro quiet splash  crashkernel=384M-2G:64M,2G-:128M
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 2619840 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 435056k/524032k available (4565k kernel code, 88352k reserved, 2143k data, 540k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xe07c0000 - 0xff7fe000   ( 496 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xdffc0000   ( 511 MB)
[    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
[    0.000000]       .data : 0xc0575554 - 0xc078d308   (2143 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0575554   (4565 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Extended CMOS year: 2000
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1808.755 MHz processor.
[    0.000008] spurious 8259A interrupt: IRQ7.
[    0.001306] Console: colour VGA+ 80x25
[    0.001309] console [tty0] enabled
[    0.001364] Calibrating delay loop (skipped), value calculated using timer frequency.. 3617.51 BogoMIPS (lpj=7235020)
[    0.001384] Security Framework initialized
[    0.001405] AppArmor: AppArmor initialized
[    0.001412] Mount-cache hash table entries: 512
[    0.001530] Initializing cgroup subsys ns
[    0.001534] Initializing cgroup subsys cpuacct
[    0.001539] Initializing cgroup subsys memory
[    0.001547] Initializing cgroup subsys freezer
[    0.001549] Initializing cgroup subsys net_cls
[    0.001561] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.001564] CPU: L2 Cache: 128K (64 bytes/line)
[    0.001568] mce: CPU supports 5 MCE banks
[    0.001583] Performance Counters: AMD PMU driver.
[    0.001595] ... version:                 0
[    0.001597] ... bit width:               48
[    0.001599] ... generic counters:        4
[    0.001601] ... value mask:              0000ffffffffffff
[    0.001604] ... max period:              00007fffffffffff
[    0.001606] ... fixed-purpose counters:  0
[    0.001608] ... counter mask:            000000000000000f
[    0.001612] Checking 'hlt' instruction... OK.
[    0.016622] SMP alternatives: switching to UP code
[    0.022360] Freeing SMP alternatives: 19k freed
[    0.022381] ACPI: Core revision 20090521
[    0.028958] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.068649] CPU0: AMD Sempron(tm) Processor 3000+ stepping 02
[    0.072001] Brought up 1 CPUs
[    0.072001] Total of 1 processors activated (3617.51 BogoMIPS).
[    0.072001] CPU0 attaching NULL sched-domain.
[    0.072001] Booting paravirtualized kernel on bare hardware
[    0.072001] regulator: core version 0.5
[    0.072001] Time: 21:13:31  Date: 10/30/09
[    0.072001] NET: Registered protocol family 16
[    0.072001] EISA bus registered
[    0.072001] ACPI: bus type pci registered
[    0.072001] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=2
[    0.072001] PCI: Using configuration type 1 for base access
[    0.072001] bio: create slab <bio-0> at 0
[    0.072001] ACPI: EC: Look up EC in DSDT
[    0.074292] ACPI Warning: Package List length (10A) larger than NumElements count (2), truncated
[    0.074298]  20090521 dsobject-502
[    0.076965] ACPI: Interpreter enabled
[    0.076972] ACPI: (supports S0 S1 S3 S4 S5)
[    0.076997] ACPI: Using IOAPIC for interrupt routing
[    0.084840] ACPI: Power Resource [ISAV] (on)
[    0.084904] ACPI Warning: Incorrect checksum in table [OEMB] - AE, should be 80 20090521 tbutils-246
[    0.085021] ACPI: No dock devices found.
[    0.085132] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.085179] pci 0000:00:00.0: reg 10 32bit mmio: [0xf0000000-0xf7ffffff]
[    0.085255] pci 0000:00:01.1: reg 10 io port: [0x5080-0x509f]
[    0.085264] pci 0000:00:01.1: reg 20 io port: [0x5000-0x503f]
[    0.085269] pci 0000:00:01.1: reg 24 io port: [0x5040-0x507f]
[    0.085280] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.085284] pci 0000:00:01.1: PME# disabled
[    0.085305] pci 0000:00:02.0: reg 10 32bit mmio: [0xff6fd000-0xff6fdfff]
[    0.085324] pci 0000:00:02.0: supports D1 D2
[    0.085326] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.085330] pci 0000:00:02.0: PME# disabled
[    0.085346] pci 0000:00:02.1: reg 10 32bit mmio: [0xff6fe000-0xff6fefff]
[    0.085365] pci 0000:00:02.1: supports D1 D2
[    0.085368] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.085371] pci 0000:00:02.1: PME# disabled
[    0.085391] pci 0000:00:02.2: reg 10 32bit mmio: [0xff6ffc00-0xff6ffcff]
[    0.085414] pci 0000:00:02.2: supports D1 D2
[    0.085416] pci 0000:00:02.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.085420] pci 0000:00:02.2: PME# disabled
[    0.085445] pci 0000:00:05.0: reg 10 32bit mmio: [0xff6fc000-0xff6fcfff]
[    0.085450] pci 0000:00:05.0: reg 14 io port: [0xec00-0xec07]
[    0.085467] pci 0000:00:05.0: supports D1 D2
[    0.085469] pci 0000:00:05.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.085473] pci 0000:00:05.0: PME# disabled
[    0.085489] pci 0000:00:06.0: reg 10 io port: [0xe800-0xe8ff]
[    0.085494] pci 0000:00:06.0: reg 14 io port: [0xe400-0xe47f]
[    0.085498] pci 0000:00:06.0: reg 18 32bit mmio: [0xff6fb000-0xff6fbfff]
[    0.085514] pci 0000:00:06.0: supports D1 D2
[    0.085537] pci 0000:00:08.0: reg 20 io port: [0xffa0-0xffaf]
[    0.085564] pci 0000:00:0a.0: reg 10 io port: [0x9f0-0x9f7]
[    0.085569] pci 0000:00:0a.0: reg 14 io port: [0xbf0-0xbf3]
[    0.085573] pci 0000:00:0a.0: reg 18 io port: [0x970-0x977]
[    0.085577] pci 0000:00:0a.0: reg 1c io port: [0xb70-0xb73]
[    0.085582] pci 0000:00:0a.0: reg 20 io port: [0xc800-0xc80f]
[    0.085586] pci 0000:00:0a.0: reg 24 io port: [0xc400-0xc47f]
[    0.085733] pci 0000:01:00.0: reg 10 32bit mmio: [0xe0000000-0xe7ffffff]
[    0.085740] pci 0000:01:00.0: reg 14 io port: [0xb800-0xb8ff]
[    0.085746] pci 0000:01:00.0: reg 18 32bit mmio: [0xff5f0000-0xff5fffff]
[    0.085762] pci 0000:01:00.0: reg 30 32bit mmio: [0xff5c0000-0xff5dffff]
[    0.085782] pci 0000:01:00.0: supports D1 D2
[    0.085809] pci 0000:01:00.1: reg 10 32bit mmio: [0xd8000000-0xdfffffff]
[    0.085816] pci 0000:01:00.1: reg 14 32bit mmio: [0xff5e0000-0xff5effff]
[    0.085847] pci 0000:01:00.1: supports D1 D2
[    0.085887] pci 0000:00:0b.0: bridge io port: [0xb000-0xbfff]
[    0.085891] pci 0000:00:0b.0: bridge 32bit mmio: [0xff500000-0xff5fffff]
[    0.085895] pci 0000:00:0b.0: bridge 32bit mmio pref: [0xceb00000-0xeeafffff]
[    0.085934] pci_bus 0000:00: on NUMA node 0
[    0.085938] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.086089] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.091348] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
[    0.091518] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.
[    0.091685] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[    0.091853] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
[    0.092032] ACPI: PCI Interrupt Link [LNKE] (IRQs 16 17 18 19) *11
[    0.092196] ACPI: PCI Interrupt Link [LUS0] (IRQs 20 21 22) *3
[    0.092363] ACPI: PCI Interrupt Link [LUS1] (IRQs 20 21 22) *9
[    0.092526] ACPI: PCI Interrupt Link [LUS2] (IRQs 20 21 22) *10
[    0.092688] ACPI: PCI Interrupt Link [LKLN] (IRQs 20 21 22) *10
[    0.092851] ACPI: PCI Interrupt Link [LAUI] (IRQs 20 21 22) *11
[    0.093017] ACPI: PCI Interrupt Link [LKMO] (IRQs 20 21 22) *0, disabled.
[    0.093180] ACPI: PCI Interrupt Link [LKSM] (IRQs 20 21 22) *0, disabled.
[    0.093343] ACPI: PCI Interrupt Link [LTID] (IRQs 20 21 22) *0
[    0.093515] ACPI: PCI Interrupt Link [LTIE] (IRQs 20 21 22) *0, disabled.
[    0.093717] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22) *14
[    0.093910] SCSI subsystem initialized
[    0.093978] libata version 3.00 loaded.
[    0.094058] usbcore: registered new interface driver usbfs
[    0.094075] usbcore: registered new interface driver hub
[    0.094098] usbcore: registered new device driver usb
[    0.094229] ACPI: WMI: Mapper loaded
[    0.094231] PCI: Using ACPI for IRQ routing
[    0.094373] Bluetooth: Core ver 2.15
[    0.094407] NET: Registered protocol family 31
[    0.094409] Bluetooth: HCI device and connection manager initialized
[    0.094413] Bluetooth: HCI socket layer initialized
[    0.094415] NetLabel: Initializing
[    0.094416] NetLabel:  domain hash size = 128
[    0.094418] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.094432] NetLabel:  unlabeled traffic allowed by default
[    0.096116] pnp: PnP ACPI init
[    0.096135] ACPI: bus type pnp registered
[    0.101101] pnp: PnP ACPI: found 15 devices
[    0.101104] ACPI: ACPI bus type pnp unregistered
[    0.101109] PnPBIOS: Disabled by ACPI PNP
[    0.101124] system 00:08: ioport range 0x190-0x193 has been reserved
[    0.101127] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.101134] system 00:09: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.101138] system 00:09: iomem range 0xfee00000-0xfeefffff could not be reserved
[    0.101142] system 00:09: iomem range 0xff780000-0xff7bffff has been reserved
[    0.101149] system 00:0b: ioport range 0x480-0x487 has been reserved
[    0.101152] system 00:0b: ioport range 0xd00-0xd07 has been reserved
[    0.101159] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[    0.101162] system 00:0e: iomem range 0xc0000-0xdffff could not be reserved
[    0.101166] system 00:0e: iomem range 0xe0000-0xfffff could not be reserved
[    0.101169] system 00:0e: iomem range 0x100000-0x1fffffff could not be reserved
[    0.101173] system 00:0e: iomem range 0xff7c0000-0xffffffff has been reserved
[    0.135855] AppArmor: AppArmor Filesystem Enabled
[    0.135879] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:01
[    0.135883] pci 0000:00:0b.0:   IO window: 0xb000-0xbfff
[    0.135888] pci 0000:00:0b.0:   MEM window: 0xff500000-0xff5fffff
[    0.135893] pci 0000:00:0b.0:   PREFETCH window: 0xceb00000-0xeeafffff
[    0.135898] pci 0000:00:0e.0: PCI bridge, secondary bus 0000:02
[    0.135900] pci 0000:00:0e.0:   IO window: disabled
[    0.135903] pci 0000:00:0e.0:   MEM window: disabled
[    0.135906] pci 0000:00:0e.0:   PREFETCH window: disabled
[    0.135917] pci 0000:00:0e.0: setting latency timer to 64
[    0.135922] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.135925] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.135928] pci_bus 0000:01: resource 0 io:  [0xb000-0xbfff]
[    0.135931] pci_bus 0000:01: resource 1 mem: [0xff500000-0xff5fffff]
[    0.135934] pci_bus 0000:01: resource 2 pref mem [0xceb00000-0xeeafffff]
[    0.135972] NET: Registered protocol family 2
[    0.136072] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.136353] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.136444] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.136554] TCP: Hash tables configured (established 16384 bind 16384)
[    0.136556] TCP reno registered
[    0.136651] NET: Registered protocol family 1
[    0.136721] Trying to unpack rootfs image as initramfs...
[    0.377363] Freeing initrd memory: 7814k freed
[    0.384292] cpufreq-nforce2: No nForce2 chipset.
[    0.384319] Scanning for low memory corruption every 60 seconds
[    0.384431] audit: initializing netlink socket (disabled)
[    0.384455] type=2000 audit(1256937211.384:1): initialized
[    0.394415] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.395890] VFS: Disk quotas dquot_6.5.2
[    0.395954] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.396570] fuse init (API version 7.12)
[    0.396658] msgmni has been set to 865
[    0.396878] alg: No test for stdrng (krng)
[    0.396890] io scheduler noop registered
[    0.396893] io scheduler anticipatory registered
[    0.396895] io scheduler deadline registered
[    0.396953] io scheduler cfq registered (default)
[    0.397025] pci 0000:01:00.0: Boot video device
[    0.397108] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.397132] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.397262] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.397267] ACPI: Power Button [PWRF]
[    0.397324] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.397328] ACPI: Power Button [PWRB]
[    0.397772] processor LNXCPU:00: registered as cooling_device0
[    0.400914] isapnp: Scanning for PnP cards...
[    0.636047] Switched to high resolution mode on CPU 0
[    0.754582] isapnp: No Plug & Play device found
[    0.755877] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.755975] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.756332] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.757372] brd: module loaded
[    0.757856] loop: module loaded
[    0.757950] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.758154] sata_nv 0000:00:0a.0: version 3.5
[    0.758517] ACPI: PCI Interrupt Link [LTID] BIOS reported IRQ 0, using IRQ 22
[    0.758520] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 22
[    0.758525]   alloc irq_desc for 22 on node -1
[    0.758527]   alloc kstat_irqs on node -1
[    0.758537] sata_nv 0000:00:0a.0: PCI INT A -> Link[LTID] -> GSI 22 (level, low) -> IRQ 22
[    0.758576] sata_nv 0000:00:0a.0: setting latency timer to 64
[    0.758655] scsi0 : sata_nv
[    0.758756] scsi1 : sata_nv
[    0.759529] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xc800 irq 22
[    0.759533] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xc808 irq 22
[    0.759628] pata_amd 0000:00:08.0: version 0.4.1
[    0.759662] pata_amd 0000:00:08.0: power state changed by ACPI to D0
[    0.759701] pata_amd 0000:00:08.0: setting latency timer to 64
[    0.759779] ata1: SATA link down (SStatus 0 SControl 300)
[    0.759806] ata2: SATA link down (SStatus 0 SControl 300)
[    0.759848] scsi2 : pata_amd
[    0.759920] scsi3 : pata_amd
[    0.760757] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.760761] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.761495] Fixed MDIO Bus: probed
[    0.761533] PPP generic driver version 2.4.2
[    0.761643] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.761933] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 21
[    0.761939]   alloc irq_desc for 21 on node -1
[    0.761941]   alloc kstat_irqs on node -1
[    0.761951] ehci_hcd 0000:00:02.2: PCI INT C -> Link[LUS2] -> GSI 21 (level, low) -> IRQ 21
[    0.761967] ehci_hcd 0000:00:02.2: setting latency timer to 64
[    0.761970] ehci_hcd 0000:00:02.2: EHCI Host Controller
[    0.762035] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 1
[    0.762063] ehci_hcd 0000:00:02.2: debug port 1
[    0.762067] ehci_hcd 0000:00:02.2: cache line size of 64 is not supported
[    0.762085] ehci_hcd 0000:00:02.2: irq 21, io mem 0xff6ffc00
[    0.772007] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00
[    0.772102] usb usb1: configuration #1 chosen from 1 choice
[    0.772141] hub 1-0:1.0: USB hub found
[    0.772151] hub 1-0:1.0: 8 ports detected
[    0.772220] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.772522] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 20
[    0.772527]   alloc irq_desc for 20 on node -1
[    0.772529]   alloc kstat_irqs on node -1
[    0.772539] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUS0] -> GSI 20 (level, low) -> IRQ 20
[    0.772554] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    0.772558] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    0.772613] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    0.772641] ohci_hcd 0000:00:02.0: irq 20, io mem 0xff6fd000
[    0.830081] usb usb2: configuration #1 chosen from 1 choice
[    0.830121] hub 2-0:1.0: USB hub found
[    0.830131] hub 2-0:1.0: 4 ports detected
[    0.830448] ACPI: PCI Interrupt Link [LUS1] enabled at IRQ 22
[    0.830453] ohci_hcd 0000:00:02.1: PCI INT B -> Link[LUS1] -> GSI 22 (level, low) -> IRQ 22
[    0.830466] ohci_hcd 0000:00:02.1: setting latency timer to 64
[    0.830469] ohci_hcd 0000:00:02.1: OHCI Host Controller
[    0.830516] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 3
[    0.830533] ohci_hcd 0000:00:02.1: irq 22, io mem 0xff6fe000
[    0.886070] usb usb3: configuration #1 chosen from 1 choice
[    0.886104] hub 3-0:1.0: USB hub found
[    0.886114] hub 3-0:1.0: 4 ports detected
[    0.886174] uhci_hcd: USB Universal Host Controller Interface driver
[    0.886261] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.886264] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.886606] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.886671] mice: PS/2 mouse device common for all mice
[    0.886769] rtc_cmos 00:02: RTC can wake from S4
[    0.886804] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.886827] rtc0: alarms up to one year, y3k, 114 bytes nvram
[    0.886956] device-mapper: uevent: version 1.0.3
[    0.887071] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.887156] device-mapper: multipath: version 1.1.0 loaded
[    0.887160] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.887309] EISA: Probing bus 0 at eisa.0
[    0.887323] Cannot allocate resource for EISA slot 4
[    0.887325] Cannot allocate resource for EISA slot 5
[    0.887334] EISA: Detected 0 cards.
[    0.887380] cpuidle: using governor ladder
[    0.887383] cpuidle: using governor menu
[    0.887927] TCP cubic registered
[    0.888130] NET: Registered protocol family 10
[    0.888588] lo: Disabled Privacy Extensions
[    0.888912] NET: Registered protocol family 17
[    0.888935] Bluetooth: L2CAP ver 2.13
[    0.888936] Bluetooth: L2CAP socket layer initialized
[    0.888939] Bluetooth: SCO (Voice Link) ver 0.6
[    0.888941] Bluetooth: SCO socket layer initialized
[    0.888993] Bluetooth: RFCOMM TTY layer initialized
[    0.888996] Bluetooth: RFCOMM socket layer initialized
[    0.888998] Bluetooth: RFCOMM ver 1.11
[    0.889013] powernow-k8: Found 1 AMD Sempron(tm) Processor 3000+ processors (1 cpu cores) (version 2.20.00)
[    0.889049] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x6
[    0.889052] powernow-k8:    1 : fid 0x2 (1000 MHz), vid 0x12
[    0.889306] Using IPI No-Shortcut mode
[    0.889390] PM: Resume from disk failed.
[    0.889405] registered taskstats version 1
[    0.889516]   Magic number: 13:675:248
[    0.889597] rtc_cmos 00:02: setting system clock to 2009-10-30 21:13:32 UTC (1256937212)
[    0.889600] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.889602] EDD information not available.
[    0.907207] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.948379] ata3.00: ATA-5: ST340016A, 3.05, max UDMA/100
[    0.948382] ata3.00: 78165360 sectors, multi 16: LBA 
[    0.952931] ata3.01: ATA-6: FUJITSU MHS2060AT, 3005, max UDMA/100
[    0.952934] ata3.01: 117210240 sectors, multi 16: LBA 
[    0.952960] ata3: nv_mode_filter: 0x3f39f&0x739f->0x739f, BIOS=0x7000 (0xc0c6c000) ACPI=0x701f (60:20:0x1f)
[    0.952966] ata3: nv_mode_filter: 0x3f39f&0x3f39f->0x3f39f, BIOS=0x3f000 (0xc0c6c000) ACPI=0x3f01f (60:20:0x1f)
[    0.968327] ata3.00: configured for UDMA/33
[    1.046689] ata3.01: configured for UDMA/100
[    1.046800] scsi 2:0:0:0: Direct-Access     ATA      ST340016A        3.05 PQ: 0 ANSI: 5
[    1.046932] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    1.047005] scsi 2:0:1:0: Direct-Access     ATA      FUJITSU MHS2060A 3005 PQ: 0 ANSI: 5
[    1.047102] sd 2:0:1:0: Attached scsi generic sg1 type 0
[    1.047141] sd 2:0:0:0: [sda] 78165360 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    1.047186] sd 2:0:0:0: [sda] Write Protect is off
[    1.047189] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.047212] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.047340]  sda: sda1 sda2 sda3 sda4 < sda5
[    1.074285] sd 2:0:1:0: [sdb] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    1.089688] sd 2:0:1:0: [sdb] Write Protect is off
[    1.089691] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    1.089715] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.089846]  sdb: sda6 >
[    1.147076]  sdb1 sdb2
[    1.162654] sd 2:0:1:0: [sdb] Attached SCSI disk
[    1.162734] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.216247] ata4.00: ATAPI: HL-DT-STDVD-ROM GDR8164B, 0L06, max UDMA/33
[    1.216279] ata4.01: ATAPI: HL-DT-ST GCE-8160B, 2.01, max MWDMA2
[    1.216305] ata4: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc0c6c000) ACPI=0x701f (60:120:0x1b)
[    1.216311] ata4: nv_mode_filter: 0x39f&0x739f->0x39f, BIOS=0x0 (0xc0c6c000) ACPI=0x39f (60:120:0x1b)
[    1.232198] ata4.00: configured for UDMA/33
[    1.248196] ata4.01: configured for MWDMA2
[    1.252494] scsi 3:0:0:0: CD-ROM            HL-DT-ST DVD-ROM GDR8164B 0L06 PQ: 0 ANSI: 5
[    1.260238] sr0: scsi3-mmc drive: 52x/52x cd/rw xa/form2 cdda tray
[    1.260242] Uniform CD-ROM driver Revision: 3.20
[    1.260352] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    1.260415] sr 3:0:0:0: Attached scsi generic sg2 type 5
[    1.260673] scsi 3:0:1:0: CD-ROM            HL-DT-ST CD-RW GCE-8160B  2.01 PQ: 0 ANSI: 5
[    1.262177] sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    1.262281] sr 3:0:1:0: Attached scsi CD-ROM sr1
[    1.262332] sr 3:0:1:0: Attached scsi generic sg3 type 5
[    1.262358] Freeing unused kernel memory: 540k freed
[    1.262881] Write protecting the kernel text: 4568k
[    1.262916] Write protecting the kernel read-only data: 1836k
[    1.406233] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.406513] ACPI: PCI Interrupt Link [LKLN] enabled at IRQ 21
[    1.406519] forcedeth 0000:00:05.0: PCI INT A -> Link[LKLN] -> GSI 21 (level, low) -> IRQ 21
[    1.406524] forcedeth 0000:00:05.0: setting latency timer to 64
[    1.406558] nv_probe: set workaround bit for reversed mac addr
[    1.415931] Linux agpgart interface v0.103
[    1.460203] Floppy drive(s): fd0 is 1.44M
[    1.480292] FDC 0 is a post-1991 82077
[    1.616548] [drm] Initialized drm 1.1.0 20060810
[    1.647573] [drm] radeon default to kernel modesetting DISABLED.
[    1.648060] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 19
[    1.648067]   alloc irq_desc for 19 on node -1
[    1.648069]   alloc kstat_irqs on node -1
[    1.648079] pci 0000:01:00.0: PCI INT A -> Link[LNKE] -> GSI 19 (level, low) -> IRQ 19
[    1.648222] [drm] Initialized radeon 1.31.0 20080528 for 0000:01:00.0 on minor 0
[    1.876059] ata3.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[    1.876064] ata3.01: BMDMA stat 0x64
[    1.876073] ata3.01: cmd c8/00:20:78:7b:fc/00:00:00:00:00/f6 tag 0 dma 16384 in
[    1.876075]          res 51/84:00:97:7b:fc/00:00:00:00:00/f6 Emask 0x10 (ATA bus error)
[    1.876078] ata3.01: status: { DRDY ERR }
[    1.876081] ata3.01: error: { ICRC ABRT }
[    1.876102] ata3: soft resetting link
[    1.924813] forcedeth 0000:00:05.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:15:f2:0c:8c:2e
[    1.924818] forcedeth 0000:00:05.0: csum timirq gbit lnktim desc-v2
[    1.925226] agpgart-amd64 0000:00:00.0: AGP bridge [10de/00e1]
[    1.925254] agpgart-amd64 0000:00:00.0: aperture size 4096 MB is not right, using settings from NB
[    1.925259] agpgart-amd64 0000:00:00.0: setting up Nforce3 AGP
[    1.929421] agpgart-amd64 0000:00:00.0: AGP aperture is 128M @ 0xf0000000
[    2.048405] ata3: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc0c6c000) ACPI=0x701f (60:20:0x1f)
[    2.048412] ata3: nv_mode_filter: 0x3f39f&0x3f39f->0x3f39f, BIOS=0x3f000 (0xc0c6c000) ACPI=0x3f01f (60:20:0x1f)
[    2.064306] ata3.00: configured for UDMA/33
[    2.080316] ata3.01: configured for UDMA/100
[    2.080326] ata3: EH complete
[    2.560594] ata3.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[    2.560598] ata3.01: BMDMA stat 0x64
[    2.560607] ata3.01: cmd c8/00:20:78:7b:fc/00:00:00:00:00/f6 tag 0 dma 16384 in
[    2.560608]          res 51/84:00:97:7b:fc/00:00:00:00:00/f6 Emask 0x10 (ATA bus error)
[    2.560612] ata3.01: status: { DRDY ERR }
[    2.560614] ata3.01: error: { ICRC ABRT }
[    2.560633] ata3: soft resetting link
[    2.732390] ata3: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc0c6c000) ACPI=0x701f (60:20:0x1f)
[    2.732397] ata3: nv_mode_filter: 0x3f39f&0x3f39f->0x3f39f, BIOS=0x3f000 (0xc0c6c000) ACPI=0x3f01f (60:20:0x1f)
[    2.740325] ata3.00: configured for UDMA/33
[    2.756303] ata3.01: configured for UDMA/100
[    2.756312] ata3: EH complete
[    3.002685] ata3.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[    3.002688] ata3.01: BMDMA stat 0x64
[    3.002697] ata3.01: cmd c8/00:20:78:7b:fc/00:00:00:00:00/f6 tag 0 dma 16384 in
[    3.002699]          res 51/84:00:97:7b:fc/00:00:00:00:00/f6 Emask 0x10 (ATA bus error)
[    3.002702] ata3.01: status: { DRDY ERR }
[    3.002704] ata3.01: error: { ICRC ABRT }
[    3.002723] ata3: soft resetting link
[    3.172398] ata3: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc0c6c000) ACPI=0x701f (60:20:0x1f)
[    3.172404] ata3: nv_mode_filter: 0x3f39f&0x3f39f->0x3f39f, BIOS=0x3f000 (0xc0c6c000) ACPI=0x3f01f (60:20:0x1f)
[    3.180301] ata3.00: configured for UDMA/33
[    3.196339] ata3.01: configured for UDMA/100
[    3.196348] ata3: EH complete
[    3.444780] ata3.01: limiting speed to UDMA/66:PIO4
[    3.444785] ata3.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[    3.444787] ata3.01: BMDMA stat 0x64
[    3.444796] ata3.01: cmd c8/00:20:78:7b:fc/00:00:00:00:00/f6 tag 0 dma 16384 in
[    3.444797]          res 51/84:00:97:7b:fc/00:00:00:00:00/f6 Emask 0x10 (ATA bus error)
[    3.444801] ata3.01: status: { DRDY ERR }
[    3.444803] ata3.01: error: { ICRC ABRT }
[    3.444822] ata3: soft resetting link
[    3.616396] ata3: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc0c6c000) ACPI=0x701f (60:20:0x1f)
[    3.616401] ata3: nv_mode_filter: 0x1f39f&0x3f39f->0x1f39f, BIOS=0x3f000 (0xc0c6c000) ACPI=0x3f01f (60:20:0x1f)
[    3.624325] ata3.00: configured for UDMA/33
[    3.640339] ata3.01: configured for UDMA/66
[    3.640347] ata3: EH complete
[    3.886878] ata3.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[    3.886882] ata3.01: BMDMA stat 0x64
[    3.886891] ata3.01: cmd c8/00:20:78:7b:fc/00:00:00:00:00/f6 tag 0 dma 16384 in
[    3.886892]          res 51/84:00:97:7b:fc/00:00:00:00:00/f6 Emask 0x10 (ATA bus error)
[    3.886895] ata3.01: status: { DRDY ERR }
[    3.886898] ata3.01: error: { ICRC ABRT }
[    3.886917] ata3: soft resetting link
[    4.056403] ata3: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc0c6c000) ACPI=0x701f (60:20:0x1f)
[    4.056410] ata3: nv_mode_filter: 0x1f39f&0x3f39f->0x1f39f, BIOS=0x3f000 (0xc0c6c000) ACPI=0x3f01f (60:20:0x1f)
[    4.072303] ata3.00: configured for UDMA/33
[    4.088339] ata3.01: configured for UDMA/66
[    4.088347] ata3: EH complete
[    4.343234] ata3.01: limiting speed to UDMA/33:PIO4
[    4.343239] ata3.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[    4.343242] ata3.01: BMDMA stat 0x64
[    4.343250] ata3.01: cmd c8/00:20:78:7b:fc/00:00:00:00:00/f6 tag 0 dma 16384 in
[    4.343252]          res 51/84:00:97:7b:fc/00:00:00:00:00/f6 Emask 0x10 (ATA bus error)
[    4.343255] ata3.01: status: { DRDY ERR }
[    4.343258] ata3.01: error: { ICRC ABRT }
[    4.343276] ata3: soft resetting link
[    4.512386] ata3: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc0c6c000) ACPI=0x701f (60:20:0x1f)
[    4.512392] ata3: nv_mode_filter: 0x739f&0x3f39f->0x739f, BIOS=0x3f000 (0xc0c6c000) ACPI=0x3f01f (60:20:0x1f)
[    4.520325] ata3.00: configured for UDMA/33
[    4.536339] ata3.01: configured for UDMA/33
[    4.536350] sd 2:0:1:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    4.536354] sd 2:0:1:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
[    4.536359] Descriptor sense data with sense descriptors (in hex):
[    4.536361]         72 0b 47 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[    4.536370]         06 fc 7b 97 
[    4.536374] sd 2:0:1:0: [sdb] Add. Sense: Scsi parity error
[    4.536380] end_request: I/O error, dev sdb, sector 117209976
[    4.536384] Buffer I/O error on device sdb, logical block 14651247
[    4.536390] Buffer I/O error on device sdb, logical block 14651248
[    4.536393] Buffer I/O error on device sdb, logical block 14651249
[    4.536396] Buffer I/O error on device sdb, logical block 14651250
[    4.536406] ata3: EH complete
[    5.925131] PM: Starting manual resume from disk
[    5.925137] PM: Resume from partition 8:17
[    5.925139] PM: Checking hibernation image.
[    5.925424] PM: Resume from disk failed.
[    5.934998] REISERFS (device sda5): found reiserfs format "3.6" with standard journal
[    5.935011] REISERFS (device sda5): using ordered data mode
[    5.941534] REISERFS (device sda5): journal params: device sda5, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[    5.942448] REISERFS (device sda5): checking transaction log (sda5)
[    5.972588] REISERFS (device sda5): Using r5 hash to sort names
[    6.989988] type=1505 audit(1256937218.599:2): operation="profile_load" pid=392 name=/usr/share/gdm/guest-session/Xsession
[    7.020784] type=1505 audit(1256937218.630:3): operation="profile_load" pid=393 name=/sbin/dhclient3
[    7.021114] type=1505 audit(1256937218.630:4): operation="profile_load" pid=393 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    7.021301] type=1505 audit(1256937218.630:5): operation="profile_load" pid=393 name=/usr/lib/connman/scripts/dhclient-script
[    7.109472] type=1505 audit(1256937218.718:6): operation="profile_load" pid=394 name=/usr/bin/evince
[    7.114792] type=1505 audit(1256937218.722:7): operation="profile_load" pid=394 name=/usr/bin/evince-previewer
[    7.118041] type=1505 audit(1256937218.726:8): operation="profile_load" pid=394 name=/usr/bin/evince-thumbnailer
[    7.138503] type=1505 audit(1256937218.746:9): operation="profile_load" pid=396 name=/usr/lib/cups/backend/cups-pdf
[    7.138931] type=1505 audit(1256937218.746:10): operation="profile_load" pid=396 name=/usr/sbin/cupsd
[    7.151501] type=1505 audit(1256937218.758:11): operation="profile_load" pid=397 name=/usr/sbin/mysqld-akonadi
[    9.722798] Adding 979956k swap on /dev/sda3.  Priority:-1 extents:1 across:979956k 
[    9.747777] Adding 1052216k swap on /dev/sdb1.  Priority:-2 extents:1 across:1052216k 
[   10.467155] udev: starting version 147
[   11.790969] REISERFS (device sda6): found reiserfs format "3.6" with standard journal
[   11.790986] REISERFS (device sda6): using ordered data mode
[   11.800564] REISERFS (device sda6): journal params: device sda6, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   11.801489] REISERFS (device sda6): checking transaction log (sda6)
[   12.242309] REISERFS (device sda6): Using r5 hash to sort names
[   12.548760] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.555913] ACPI: I/O resource nForce2_smbus [0x5000-0x503f] conflicts with ACPI region SMRG [0x5000-0x5004]
[   12.555918] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   12.555922] nForce2_smbus 0000:00:01.1: Error probing SMB1.
[   12.555957] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x5040
[   12.625480] lp: driver loaded but no devices found
[   12.787865] parport_pc 00:06: reported by Plug and Play ACPI
[   12.787918] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   12.863341] ip_tables: (C) 2000-2006 Netfilter Core Team
[   12.870948] ppdev: user-space parallel port driver
[   12.884183] lp0: using parport0 (interrupt-driven).
[   12.922497] gameport: NS558 PnP Gameport is pnp00:0c/gameport0, io 0x200, speed 59659kHz
[   13.376769] ACPI: PCI Interrupt Link [LAUI] enabled at IRQ 20
[   13.376776] Intel ICH 0000:00:06.0: PCI INT A -> Link[LAUI] -> GSI 20 (level, low) -> IRQ 20
[   13.376810] Intel ICH 0000:00:06.0: setting latency timer to 64
[   13.477106] REISERFS (device sda2): found reiserfs format "3.6" with standard journal
[   13.477131] REISERFS (device sda2): using ordered data mode
[   13.485384] REISERFS (device sda2): journal params: device sda2, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   13.486350] REISERFS (device sda2): checking transaction log (sda2)
[   13.645459] REISERFS (device sda2): Using r5 hash to sort names
[   13.700023] intel8x0_measure_ac97_clock: measured 54632 usecs (2680 samples)
[   13.700028] intel8x0: clocking to 46967
[   13.901014] REISERFS (device sda1): found reiserfs format "3.6" with standard journal
[   13.901043] REISERFS (device sda1): using ordered data mode
[   13.907626] REISERFS (device sda1): journal params: device sda1, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   13.908591] REISERFS (device sda1): checking transaction log (sda1)
[   14.039939] REISERFS (device sda1): Using r5 hash to sort names
[   14.218245] REISERFS (device sdb2): found reiserfs format "3.6" with standard journal
[   14.218274] REISERFS (device sdb2): using ordered data mode
[   14.228639] REISERFS (device sdb2): journal params: device sdb2, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   14.229625] REISERFS (device sdb2): checking transaction log (sdb2)
[   14.315272] REISERFS (device sdb2): Using r5 hash to sort names
[   16.104458] __ratelimit: 6 callbacks suppressed
[   16.104463] type=1505 audit(1256937227.714:14): operation="profile_replace" pid=810 name=/usr/share/gdm/guest-session/Xsession
[   16.106419] type=1505 audit(1256937227.714:15): operation="profile_replace" pid=811 name=/sbin/dhclient3
[   16.106766] type=1505 audit(1256937227.714:16): operation="profile_replace" pid=811 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   16.106957] type=1505 audit(1256937227.714:17): operation="profile_replace" pid=811 name=/usr/lib/connman/scripts/dhclient-script
[   16.113715] type=1505 audit(1256937227.722:18): operation="profile_replace" pid=812 name=/usr/bin/evince
[   16.119169] type=1505 audit(1256937227.726:19): operation="profile_replace" pid=812 name=/usr/bin/evince-previewer
[   16.122780] type=1505 audit(1256937227.730:20): operation="profile_replace" pid=812 name=/usr/bin/evince-thumbnailer
[   16.129029] type=1505 audit(1256937227.738:21): operation="profile_replace" pid=815 name=/usr/lib/cups/backend/cups-pdf
[   16.129476] type=1505 audit(1256937227.738:22): operation="profile_replace" pid=815 name=/usr/sbin/cupsd
[   16.131676] type=1505 audit(1256937227.738:23): operation="profile_replace" pid=816 name=/usr/sbin/mysqld-akonadi
[   33.074645] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   33.074650] vboxdrv: Warning: 2.6.31+ kernel detected. Most likely the hwardware performance
[   33.074652] vboxdrv: counter framework which can generate NMIs is active. You have to prevent
[   33.074654] vboxdrv: the usage of hardware performance counters by
[   33.074655] vboxdrv:   echo 2 > /proc/sys/kernel/perf_counter_paranoid
[   33.074660] vboxdrv: Found 1 processor cores.
[   33.074761] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   33.074764] vboxdrv: Successfully loaded version 3.0.8_OSE (interface 0x000e0000).
[   36.848018] eth0: no IPv6 routers present
[   97.500164] Marking TSC unstable due to cpufreq changes
[   98.132034] Clocksource tsc unstable (delta = -222077805 ns)
```

---

### Post by trldp on 2009-10-31
I did some research myself, and I found that I should load the radeon module before the agpgart module. (Which isn't the case). So I can solve the problem by unloading and reloading the radeon module and then restarting GDM.

Is there a way to force ubuntu to load the agpgart module before the radeon module?

---

