---
title: "CDROM won't recognize cds/dvds on ubuntu 9.10"
date: 2009-11-04
forum: Hardware
---

### Post by frojnd on 2009-11-04
Hello there.

I am having problem with cdrom on acer aspire 5410 with ubuntu 9.10.
When I insert a cd or dvd ubuntu won't recognize it. Also when I try to eject it it won't eject it the first time I press the eject buttong. I have to press a couple of times before it actually eject it.

I have no idea how to solve this problem since before I hadn't had any hardware problems at all :S

I heard dmesg tells what's wrong so here is the dmesg output when I put in DVD and then try to eject it:

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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e000 (usable)
[    0.000000]  BIOS-e820: 000000000009e000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007b9f0000 (usable)
[    0.000000]  BIOS-e820: 000000007b9f0000 - 000000007ba3f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007ba3f000 - 000000007ba57000 (usable)
[    0.000000]  BIOS-e820: 000000007ba57000 - 000000007babf000 (reserved)
[    0.000000]  BIOS-e820: 000000007babf000 - 000000007bade000 (usable)
[    0.000000]  BIOS-e820: 000000007bade000 - 000000007baf7000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007baf7000 - 000000007bb00000 (usable)
[    0.000000]  BIOS-e820: 000000007bb00000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.6 present.
[    0.000000] last_pfn = 0x7bb00 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-through
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FC0000000 write-back
[    0.000000]   1 base 0FFE00000 mask FFFE00000 write-protect
[    0.000000]   2 base 040000000 mask FC0000000 write-back
[    0.000000]   3 base 07C000000 mask FFC000000 uncachable
[    0.000000]   4 base 07BC00000 mask FFFC00000 uncachable
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009e000 (usable)
[    0.000000]  modified: 000000000009e000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007b9f0000 (usable)
[    0.000000]  modified: 000000007b9f0000 - 000000007ba3f000 (ACPI NVS)
[    0.000000]  modified: 000000007ba3f000 - 000000007ba57000 (usable)
[    0.000000]  modified: 000000007ba57000 - 000000007babf000 (reserved)
[    0.000000]  modified: 000000007babf000 - 000000007bade000 (usable)
[    0.000000]  modified: 000000007bade000 - 000000007baf7000 (ACPI data)
[    0.000000]  modified: 000000007baf7000 - 000000007bb00000 (usable)
[    0.000000]  modified: 000000007bb00000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  modified: 00000000fed18000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 378a6000 - 37fef91b
[    0.000000] Allocated new RAMDISK: 008ad000 - 00ff691b
[    0.000000] Move RAMDISK from 00000000378a6000 - 0000000037fef91a to 008ad000 - 00ff691a
[    0.000000] ACPI: RSDP 000fe020 00024 (v02 ACRSYS)
[    0.000000] ACPI: XSDT 7baf6120 0007C (v01 ACRSYS ACRPRDCT 00000001      01000013)
[    0.000000] ACPI: FACP 7baf4000 000F4 (v04 ACRSYS ACRPRDCT 00000001 1025 000F4240)
[    0.000000] ACPI: DSDT 7bae5000 0A592 (v01 ACER   ACER     00000001 1025 20051117)
[    0.000000] ACPI: FACS 7b9fd000 00040
[    0.000000] ACPI: DMAR 7baf5000 00060 (v01                00000001      00000000)
[    0.000000] ACPI: HPET 7baf3000 00038 (v01 ACER   ACER     00000001 1025 000F4240)
[    0.000000] ACPI: APIC 7baf2000 0006C (v02 ACER   ACER     00000001 1025 000F4240)
[    0.000000] ACPI: MCFG 7baf1000 0003C (v01 ACER   ACER     00000001 1025 000F4240)
[    0.000000] ACPI: ASF! 7baf0000 000A5 (v32 ACER   ACER     00000001 1025 000F4240)
[    0.000000] ACPI: SLIC 7bae4000 00176 (v01 ACRSYS ACRPRDCT 00000001 1025 000F4240)
[    0.000000] ACPI: BOOT 7bae3000 00028 (v01 ACER   ACER     00000001 1025 00000001)
[    0.000000] ACPI: SSDT 7bae2000 0031A (v01 ACER   ACER     00001000 1025 20051117)
[    0.000000] ACPI: SSDT 7badf000 00537 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.000000] ACPI: SSDT 7bade000 00655 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1091MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
[    0.000000]   #4 [000009e000 - 0000100000]    BIOS reserved ==> [000009e000 - 0000100000]
[    0.000000]   #5 [00008a9000 - 00008ac258]              BRK ==> [00008a9000 - 00008ac258]
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #7 [00008ad000 - 0000ff691b]      NEW RAMDISK ==> [00008ad000 - 0000ff691b]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007bb00
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[6] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x0007b9f0
[    0.000000]     0: 0x0007ba3f -> 0x0007ba57
[    0.000000]     0: 0x0007babf -> 0x0007bade
[    0.000000]     0: 0x0007baf7 -> 0x0007bb00
[    0.000000] On node 0 totalpages: 506314
[    0.000000] free_area_init_node: node 0, pgdat c0784900, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3962 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2183 pages used for memmap
[    0.000000]   HighMem zone: 276907 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x00] disabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 3 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:78000000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c1f82000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 502355
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=a808f8e3-9fca-4328-ac37-bae2d9ed0268 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] allocated 10132480 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007bb00)
[    0.000000] Memory: 1982164k/2026496k available (4565k kernel code, 42148k reserved, 2143k data, 540k init, 1116360k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
[    0.000000]       .data : 0xc0575554 - 0xc078d308   (2143 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0575554   (4565 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:440
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1196.751 MHz processor.
[    0.001491] Console: colour VGA+ 80x25
[    0.001496] console [tty0] enabled
[    0.001751] hpet clockevent registered
[    0.001756] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.001764] Calibrating delay loop (skipped), value calculated using timer frequency.. 2393.50 BogoMIPS (lpj=4787004)
[    0.001788] Security Framework initialized
[    0.001814] AppArmor: AppArmor initialized
[    0.001824] Mount-cache hash table entries: 512
[    0.001994] Initializing cgroup subsys ns
[    0.002001] Initializing cgroup subsys cpuacct
[    0.002008] Initializing cgroup subsys memory
[    0.002017] Initializing cgroup subsys freezer
[    0.002020] Initializing cgroup subsys net_cls
[    0.002041] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.002045] CPU: L2 cache: 1024K
[    0.002052] mce: CPU supports 6 MCE banks
[    0.002061] CPU0: Thermal monitoring handled by SMI
[    0.002067] using mwait in idle threads.
[    0.002075] Performance Counters: Core2 events, Intel PMU driver.
[    0.002087] ... version:                 2
[    0.002090] ... bit width:               40
[    0.002093] ... generic counters:        2
[    0.002095] ... value mask:              000000ffffffffff
[    0.002099] ... max period:              000000007fffffff
[    0.002102] ... fixed-purpose counters:  3
[    0.002104] ... counter mask:            0000000700000003
[    0.002113] Checking 'hlt' instruction... OK.
[    0.017279] SMP alternatives: switching to UP code
[    0.028007] ACPI: Core revision 20090521
[    0.056425] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.097104] CPU0: Intel(R) Celeron(R) CPU          723  @ 1.20GHz stepping 0a
[    0.100001] Brought up 1 CPUs
[    0.100001] Total of 1 processors activated (2393.50 BogoMIPS).
[    0.100001] CPU0 attaching NULL sched-domain.
[    0.100001] Booting paravirtualized kernel on bare hardware
[    0.100001] regulator: core version 0.5
[    0.100001] Time: 17:14:12  Date: 11/04/09
[    0.100001] NET: Registered protocol family 16
[    0.100001] EISA bus registered
[    0.100001] ACPI: bus type pci registered
[    0.100001] PCI: MCFG configuration 0: base f8000000 segment 0 buses 0 - 63
[    0.100001] PCI: MCFG area at f8000000 reserved in E820
[    0.100001] PCI: Using MMCONFIG for extended config space
[    0.100001] PCI: Using configuration type 1 for base access
[    0.100001] bio: create slab <bio-0> at 0
[    0.100302] ACPI: EC: Look up EC in DSDT
[    0.109177] ACPI: BIOS _OSI(Linux) query ignored
[    0.110254] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.148059] ACPI: Interpreter enabled
[    0.148065] ACPI: (supports S0 S3 S4 S5)
[    0.148112] ACPI: Using IOAPIC for interrupt routing
[    0.189619] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.189623] ACPI: EC: driver started in interrupt mode
[    0.190151] ACPI: No dock devices found.
[    0.190914] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.191037] pci 0000:00:02.0: reg 10 64bit mmio: [0x90000000-0x903fffff]
[    0.191049] pci 0000:00:02.0: reg 18 64bit mmio: [0x80000000-0x8fffffff]
[    0.191056] pci 0000:00:02.0: reg 20 io port: [0x4110-0x4117]
[    0.191112] pci 0000:00:02.1: reg 10 64bit mmio: [0x000000-0x0fffff]
[    0.191275] pci 0000:00:1a.0: reg 20 io port: [0x40e0-0x40ff]
[    0.191413] pci 0000:00:1a.1: reg 20 io port: [0x40c0-0x40df]
[    0.191531] pci 0000:00:1a.7: reg 10 32bit mmio: [0x94405c00-0x94405fff]
[    0.191611] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.191617] pci 0000:00:1a.7: PME# disabled
[    0.191680] pci 0000:00:1b.0: reg 10 64bit mmio: [0x94400000-0x94403fff]
[    0.191750] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.191756] pci 0000:00:1b.0: PME# disabled
[    0.191852] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.191859] pci 0000:00:1c.0: PME# disabled
[    0.191955] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.192007] pci 0000:00:1c.1: PME# disabled
[    0.192119] pci 0000:00:1d.0: reg 20 io port: [0x40a0-0x40bf]
[    0.192256] pci 0000:00:1d.1: reg 20 io port: [0x4080-0x409f]
[    0.192395] pci 0000:00:1d.2: reg 20 io port: [0x4060-0x407f]
[    0.192513] pci 0000:00:1d.3: reg 20 io port: [0x4040-0x405f]
[    0.192632] pci 0000:00:1d.7: reg 10 32bit mmio: [0x94405800-0x94405bff]
[    0.192712] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.192718] pci 0000:00:1d.7: PME# disabled
[    0.192979] pci 0000:00:1f.2: reg 10 io port: [0x4108-0x410f]
[    0.192989] pci 0000:00:1f.2: reg 14 io port: [0x411c-0x411f]
[    0.192998] pci 0000:00:1f.2: reg 18 io port: [0x4100-0x4107]
[    0.193008] pci 0000:00:1f.2: reg 1c io port: [0x4118-0x411b]
[    0.193018] pci 0000:00:1f.2: reg 20 io port: [0x4020-0x403f]
[    0.193028] pci 0000:00:1f.2: reg 24 32bit mmio: [0x94405000-0x944057ff]
[    0.193079] pci 0000:00:1f.2: PME# supported from D3hot
[    0.193085] pci 0000:00:1f.2: PME# disabled
[    0.193131] pci 0000:00:1f.3: reg 10 64bit mmio: [0x94406000-0x944060ff]
[    0.193154] pci 0000:00:1f.3: reg 20 io port: [0x4000-0x401f]
[    0.193231] pci 0000:00:1f.6: reg 10 64bit mmio: [0x94404000-0x94404fff]
[    0.193371] pci 0000:01:00.0: reg 10 64bit mmio: [0x93400000-0x9343ffff]
[    0.193384] pci 0000:01:00.0: reg 18 io port: [0x3000-0x307f]
[    0.193469] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.193476] pci 0000:01:00.0: PME# disabled
[    0.193555] pci 0000:00:1c.0: bridge io port: [0x3000-0x3fff]
[    0.193562] pci 0000:00:1c.0: bridge 32bit mmio: [0x93400000-0x943fffff]
[    0.193572] pci 0000:00:1c.0: bridge 64bit mmio pref: [0x90400000-0x913fffff]
[    0.193649] pci 0000:02:00.0: reg 10 64bit mmio: [0x92400000-0x9240ffff]
[    0.193741] pci 0000:02:00.0: supports D1
[    0.193745] pci 0000:02:00.0: PME# supported from D0 D1 D3hot
[    0.193752] pci 0000:02:00.0: PME# disabled
[    0.193838] pci 0000:00:1c.1: bridge io port: [0x2000-0x2fff]
[    0.193845] pci 0000:00:1c.1: bridge 32bit mmio: [0x92400000-0x933fffff]
[    0.193854] pci 0000:00:1c.1: bridge 64bit mmio pref: [0x91400000-0x923fffff]
[    0.193924] pci 0000:00:1e.0: transparent bridge
[    0.193959] pci_bus 0000:00: on NUMA node 0
[    0.193971] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.194409] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[    0.194501] ACPI Warning: \_SB_.PCI0.P32_._PRT: Return Package has no elements (empty) 20090521 nspredef-434
[    0.194611] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.194778] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    0.222673] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    0.222898] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 *11 12)
[    0.223120] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[    0.223339] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[    0.223560] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.223781] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 *10 11 12)
[    0.224013] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 *11 12)
[    0.224234] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 *11 12)
[    0.224541] SCSI subsystem initialized
[    0.224605] libata version 3.00 loaded.
[    0.224705] usbcore: registered new interface driver usbfs
[    0.224727] usbcore: registered new interface driver hub
[    0.224760] usbcore: registered new device driver usb
[    0.225056] ACPI: WMI: Mapper loaded
[    0.225059] PCI: Using ACPI for IRQ routing
[    0.225274] Bluetooth: Core ver 2.15
[    0.225313] NET: Registered protocol family 31
[    0.225316] Bluetooth: HCI device and connection manager initialized
[    0.225319] Bluetooth: HCI socket layer initialized
[    0.225322] NetLabel: Initializing
[    0.225324] NetLabel:  domain hash size = 128
[    0.225326] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.225343] NetLabel:  unlabeled traffic allowed by default
[    0.225381] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.225389] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.229904] pnp: PnP ACPI init
[    0.229929] ACPI: bus type pnp registered
[    0.233090] pnp: PnP ACPI: found 9 devices
[    0.233094] ACPI: ACPI bus type pnp unregistered
[    0.233098] PnPBIOS: Disabled by ACPI PNP
[    0.233114] system 00:01: ioport range 0x164e-0x164f has been reserved
[    0.233120] system 00:01: ioport range 0x600-0x60f has been reserved
[    0.233124] system 00:01: ioport range 0x610-0x610 has been reserved
[    0.233128] system 00:01: ioport range 0x800-0x80f has been reserved
[    0.233132] system 00:01: ioport range 0x810-0x817 has been reserved
[    0.233137] system 00:01: ioport range 0x820-0x823 has been reserved
[    0.233141] system 00:01: ioport range 0x400-0x47f has been reserved
[    0.233145] system 00:01: ioport range 0x500-0x53f has been reserved
[    0.233150] system 00:01: iomem range 0xf8000000-0xfbffffff has been reserved
[    0.233155] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.233159] system 00:01: iomem range 0xfed10000-0xfed13fff has been reserved
[    0.233164] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.233168] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.233173] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.233177] system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.233182] system 00:01: iomem range 0xfed40000-0xfed44fff has been reserved
[    0.233186] system 00:01: iomem range 0xfed45000-0xfed8ffff has been reserved
[    0.233191] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.233195] system 00:01: iomem range 0xff800000-0xff800fff has been reserved
[    0.267927] AppArmor: AppArmor Filesystem Enabled
[    0.267985] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
[    0.267990] pci 0000:00:1c.0:   IO window: 0x3000-0x3fff
[    0.267999] pci 0000:00:1c.0:   MEM window: 0x93400000-0x943fffff
[    0.268012] pci 0000:00:1c.0:   PREFETCH window: 0x00000090400000-0x000000913fffff
[    0.268022] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02
[    0.268028] pci 0000:00:1c.1:   IO window: 0x2000-0x2fff
[    0.268036] pci 0000:00:1c.1:   MEM window: 0x92400000-0x933fffff
[    0.268042] pci 0000:00:1c.1:   PREFETCH window: 0x00000091400000-0x000000923fffff
[    0.268051] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.268054] pci 0000:00:1e.0:   IO window: disabled
[    0.268062] pci 0000:00:1e.0:   MEM window: disabled
[    0.268067] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.268084]   alloc irq_desc for 16 on node -1
[    0.268087]   alloc kstat_irqs on node -1
[    0.268095] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.268103] pci 0000:00:1c.0: setting latency timer to 64
[    0.268113]   alloc irq_desc for 17 on node -1
[    0.268116]   alloc kstat_irqs on node -1
[    0.268121] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.268127] pci 0000:00:1c.1: setting latency timer to 64
[    0.268136] pci 0000:00:1e.0: setting latency timer to 64
[    0.268143] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.268147] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.268151] pci_bus 0000:01: resource 0 io:  [0x3000-0x3fff]
[    0.268155] pci_bus 0000:01: resource 1 mem: [0x93400000-0x943fffff]
[    0.268160] pci_bus 0000:01: resource 2 pref mem [0x90400000-0x913fffff]
[    0.268164] pci_bus 0000:02: resource 0 io:  [0x2000-0x2fff]
[    0.268167] pci_bus 0000:02: resource 1 mem: [0x92400000-0x933fffff]
[    0.268171] pci_bus 0000:02: resource 2 pref mem [0x91400000-0x923fffff]
[    0.268176] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.268179] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffff]
[    0.268225] NET: Registered protocol family 2
[    0.268352] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.268759] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.269362] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.269706] TCP: Hash tables configured (established 131072 bind 65536)
[    0.269710] TCP reno registered
[    0.269850] NET: Registered protocol family 1
[    0.269933] Trying to unpack rootfs image as initramfs...
[    0.504070] Switched to high resolution mode on CPU 0
[    0.575191] Freeing initrd memory: 7462k freed
[    0.579269] Simple Boot Flag value 0x5 read from CMOS RAM was invalid
[    0.579274] Simple Boot Flag at 0x44 set to 0x1
[    0.579438] cpufreq-nforce2: No nForce2 chipset.
[    0.579476] Scanning for low memory corruption every 60 seconds
[    0.579617] audit: initializing netlink socket (disabled)
[    0.579638] type=2000 audit(1257354851.576:1): initialized
[    0.593792] highmem bounce pool size: 64 pages
[    0.593800] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.595815] VFS: Disk quotas dquot_6.5.2
[    0.595893] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.596694] fuse init (API version 7.12)
[    0.596813] msgmni has been set to 1707
[    0.597057] alg: No test for stdrng (krng)
[    0.597073] io scheduler noop registered
[    0.597076] io scheduler anticipatory registered
[    0.597079] io scheduler deadline registered
[    0.597142] io scheduler cfq registered (default)
[    0.597157] pci 0000:00:02.0: Boot video device
[    2.196012] pci 0000:00:1a.7: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[    3.796012] pci 0000:00:1d.7: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[    3.796290]   alloc irq_desc for 24 on node -1
[    3.796294]   alloc kstat_irqs on node -1
[    3.796308] pcieport-driver 0000:00:1c.0: irq 24 for MSI/MSI-X
[    3.796322] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    3.796511]   alloc irq_desc for 25 on node -1
[    3.796514]   alloc kstat_irqs on node -1
[    3.796526] pcieport-driver 0000:00:1c.1: irq 25 for MSI/MSI-X
[    3.796539] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    3.796668] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    3.796845] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    3.801187] ACPI: AC Adapter [ADP1] (on-line)
[    3.801275] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    3.801280] ACPI: Power Button [PWRF]
[    3.801347] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    3.803295] ACPI: Lid Switch [LID0]
[    3.803361] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    3.803370] ACPI: Sleep Button [SLPB]
[    3.804879] Monitor-Mwait will be used to enter C-1 state
[    3.804913] Monitor-Mwait will be used to enter C-2 state
[    3.804924] Marking TSC unstable due to TSC halts in idle
[    3.804943] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    3.804975] processor LNXCPU:00: registered as cooling_device0
[    3.836583] thermal LNXTHERM:01: registered as thermal_zone0
[    3.836595] ACPI: Thermal Zone [TZS0] (37 C)
[    3.846687] thermal LNXTHERM:02: registered as thermal_zone1
[    3.846698] ACPI: Thermal Zone [TZS1] (37 C)
[    3.846764] isapnp: Scanning for PnP cards...
[    3.852430] ACPI: Battery Slot [BAT0] (battery absent)
[    4.200971] isapnp: No Plug & Play device found
[    4.202642] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    4.204426] brd: module loaded
[    4.205025] loop: module loaded
[    4.205125] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    4.205220] ahci 0000:00:1f.2: version 3.0
[    4.205238]   alloc irq_desc for 19 on node -1
[    4.205241]   alloc kstat_irqs on node -1
[    4.205251] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.205291]   alloc irq_desc for 26 on node -1
[    4.205294]   alloc kstat_irqs on node -1
[    4.205306] ahci 0000:00:1f.2: irq 26 for MSI/MSI-X
[    4.205361] ahci: SSS flag set, parallel bus scan disabled
[    4.205409] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    4.205414] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck stag pm led clo pmp pio slum part ems 
[    4.205422] ahci 0000:00:1f.2: setting latency timer to 64
[    4.228089] scsi0 : ahci
[    4.228219] scsi1 : ahci
[    4.228287] scsi2 : ahci
[    4.228357] scsi3 : ahci
[    4.228435] scsi4 : ahci
[    4.228504] scsi5 : ahci
[    4.228872] ata1: SATA max UDMA/133 abar m2048@0x94405000 port 0x94405100 irq 26
[    4.228878] ata2: SATA max UDMA/133 abar m2048@0x94405000 port 0x94405180 irq 26
[    4.228881] ata3: DUMMY
[    4.228884] ata4: DUMMY
[    4.228888] ata5: SATA max UDMA/133 abar m2048@0x94405000 port 0x94405300 irq 26
[    4.228893] ata6: SATA max UDMA/133 abar m2048@0x94405000 port 0x94405380 irq 26
[    4.230022] Fixed MDIO Bus: probed
[    4.230070] PPP generic driver version 2.4.2
[    4.230202] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.230230] ehci_hcd 0000:00:1a.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    4.230251] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    4.230256] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    4.230323] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    4.234256] ehci_hcd 0000:00:1a.7: debug port 1
[    4.234265] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    4.234409] ehci_hcd 0000:00:1a.7: irq 19, io mem 0x94405c00
[    4.248020] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    4.248115] usb usb1: configuration #1 chosen from 1 choice
[    4.248155] hub 1-0:1.0: USB hub found
[    4.248165] hub 1-0:1.0: 4 ports detected
[    4.248233]   alloc irq_desc for 23 on node -1
[    4.248237]   alloc kstat_irqs on node -1
[    4.248244] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    4.248258] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    4.248263] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.248304] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    4.252232] ehci_hcd 0000:00:1d.7: debug port 1
[    4.252241] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    4.252258] ehci_hcd 0000:00:1d.7: irq 23, io mem 0x94405800
[    4.268021] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    4.268119] usb usb2: configuration #1 chosen from 1 choice
[    4.268157] hub 2-0:1.0: USB hub found
[    4.268166] hub 2-0:1.0: 8 ports detected
[    4.268246] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.268270] uhci_hcd: USB Universal Host Controller Interface driver
[    4.268306] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.268316] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    4.268321] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    4.268364] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    4.268406] uhci_hcd 0000:00:1a.0: irq 16, io base 0x000040e0
[    4.268508] usb usb3: configuration #1 chosen from 1 choice
[    4.268543] hub 3-0:1.0: USB hub found
[    4.268552] hub 3-0:1.0: 2 ports detected
[    4.268613]   alloc irq_desc for 21 on node -1
[    4.268616]   alloc kstat_irqs on node -1
[    4.268623] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    4.268632] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    4.268636] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    4.268675] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    4.268714] uhci_hcd 0000:00:1a.1: irq 21, io base 0x000040c0
[    4.268814] usb usb4: configuration #1 chosen from 1 choice
[    4.268851] hub 4-0:1.0: USB hub found
[    4.268860] hub 4-0:1.0: 2 ports detected
[    4.268923] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    4.268932] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    4.268937] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    4.268982] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    4.269014] uhci_hcd 0000:00:1d.0: irq 23, io base 0x000040a0
[    4.269117] usb usb5: configuration #1 chosen from 1 choice
[    4.269158] hub 5-0:1.0: USB hub found
[    4.269166] hub 5-0:1.0: 2 ports detected
[    4.269222] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.269231] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    4.269236] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    4.269274] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    4.269305] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00004080
[    4.269405] usb usb6: configuration #1 chosen from 1 choice
[    4.269446] hub 6-0:1.0: USB hub found
[    4.269455] hub 6-0:1.0: 2 ports detected
[    4.269514] uhci_hcd 0000:00:1d.2: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    4.269523] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    4.269527] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    4.269568] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    4.269600] uhci_hcd 0000:00:1d.2: irq 16, io base 0x00004060
[    4.269702] usb usb7: configuration #1 chosen from 1 choice
[    4.269739] hub 7-0:1.0: USB hub found
[    4.269751] hub 7-0:1.0: 2 ports detected
[    4.269807]   alloc irq_desc for 18 on node -1
[    4.269810]   alloc kstat_irqs on node -1
[    4.269817] uhci_hcd 0000:00:1d.3: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.269827] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    4.269832] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    4.269872] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 8
[    4.269912] uhci_hcd 0000:00:1d.3: irq 18, io base 0x00004040
[    4.270018] usb usb8: configuration #1 chosen from 1 choice
[    4.270054] hub 8-0:1.0: USB hub found
[    4.270062] hub 8-0:1.0: 2 ports detected
[    4.270188] PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    4.284571] i8042.c: Detected active multiplexing controller, rev 1.1.
[    4.291660] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.291668] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    4.291672] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    4.291676] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    4.291680] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    4.291755] mice: PS/2 mouse device common for all mice
[    4.291894] rtc_cmos 00:03: RTC can wake from S4
[    4.291943] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    4.291977] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    4.292171] device-mapper: uevent: version 1.0.3
[    4.292298] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    4.292359] device-mapper: multipath: version 1.1.0 loaded
[    4.292363] device-mapper: multipath round-robin: version 1.0.0 loaded
[    4.292512] EISA: Probing bus 0 at eisa.0
[    4.292523] Cannot allocate resource for EISA slot 2
[    4.292526] Cannot allocate resource for EISA slot 3
[    4.292529] Cannot allocate resource for EISA slot 4
[    4.292551] EISA: Detected 0 cards.
[    4.292644] cpuidle: using governor ladder
[    4.292706] cpuidle: using governor menu
[    4.293342] TCP cubic registered
[    4.293560] NET: Registered protocol family 10
[    4.294131] lo: Disabled Privacy Extensions
[    4.294533] NET: Registered protocol family 17
[    4.294556] Bluetooth: L2CAP ver 2.13
[    4.294559] Bluetooth: L2CAP socket layer initialized
[    4.294563] Bluetooth: SCO (Voice Link) ver 0.6
[    4.294565] Bluetooth: SCO socket layer initialized
[    4.294600] Bluetooth: RFCOMM TTY layer initialized
[    4.294604] Bluetooth: RFCOMM socket layer initialized
[    4.294607] Bluetooth: RFCOMM ver 1.11
[    4.294641] Using IPI No-Shortcut mode
[    4.294728] PM: Resume from disk failed.
[    4.294742] registered taskstats version 1
[    4.294895]   Magic number: 1:302:238
[    4.294984] rtc_cmos 00:03: setting system clock to 2009-11-04 17:14:16 UTC (1257354856)
[    4.294989] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.294991] EDD information not available.
[    4.313645] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    4.568214] ata1: SATA link down (SStatus 0 SControl 300)
[    4.624029] usb 2-5: new high speed USB device using ehci_hcd and address 2
[    5.017160] usb 2-5: configuration #1 chosen from 1 choice
[    5.112105] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.113531] ata2.00: ACPI cmd 00/00:00:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[    5.113677] ata2.00: ATA-8: Hitachi HTS545025B9A300, PB2OC60F, max UDMA/133
[    5.113682] ata2.00: 488397168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    5.115241] ata2.00: ACPI cmd 00/00:00:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[    5.115418] ata2.00: configured for UDMA/133
[    5.128176] scsi 1:0:0:0: Direct-Access     ATA      Hitachi HTS54502 PB2O PQ: 0 ANSI: 5
[    5.128336] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    5.128390] sd 1:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    5.128453] sd 1:0:0:0: [sda] Write Protect is off
[    5.128457] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.128491] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.128656]  sda: sda1 sda2 sda3
[    5.156333] sd 1:0:0:0: [sda] Attached SCSI disk
[    6.016033] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    6.019920] ata5.00: ACPI cmd 00/00:00:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    6.019928] ata5.00: ATAPI: MATSHITADVD-RAM UJ862AS, 1.00, max UDMA/33
[    6.027862] ata5.00: ACPI cmd 00/00:00:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    6.027906] ata5.00: configured for UDMA/33
[    6.051454] scsi 4:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ862AS  1.00 PQ: 0 ANSI: 5
[    6.066416] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    6.066420] Uniform CD-ROM driver Revision: 3.20
[    6.066525] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    6.066583] sr 4:0:0:0: Attached scsi generic sg1 type 5
[    6.384036] ata6: SATA link down (SStatus 0 SControl 300)
[    6.400042] Freeing unused kernel memory: 540k freed
[    6.400324] Write protecting the kernel text: 4568k
[    6.400368] Write protecting the kernel read-only data: 1836k
[    6.603295] Linux agpgart interface v0.103
[    6.677605] agpgart-intel 0000:00:00.0: Intel Mobile Intel® GM45 Express Chipset
[    6.678015] agpgart-intel 0000:00:00.0: detected 65532K stolen memory
[    6.681088] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x80000000
[    6.836152] [drm] Initialized drm 1.1.0 20060810
[    6.855730] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.855738] i915 0000:00:02.0: setting latency timer to 64
[    6.858015]   alloc irq_desc for 27 on node -1
[    6.858020]   alloc kstat_irqs on node -1
[    6.858031] i915 0000:00:02.0: irq 27 for MSI/MSI-X
[    6.966283] [drm] i2c_init DPDDC-B
[    6.977472] [drm] i2c_init DPDDC-D
[    7.110277] i2c-adapter i2c-2: unable to read EDID block.
[    7.110283] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[    7.120292] [drm] fb0: inteldrmfb frame buffer device
[    7.146693] acpi device:03: registered as cooling_device1
[    7.147206] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/input/input5
[    7.147260] ACPI: Video Device [OVGA] (multi-head: yes  rom: no  post: no)
[    7.147325] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    7.528682] [drm] LVDS-8: set mode 1366x768 14
[    8.089152] Console: switching to colour frame buffer device 170x48
[    8.541577] PM: Starting manual resume from disk
[    8.541584] PM: Resume from partition 8:1
[    8.541588] PM: Checking hibernation image.
[    8.541709] PM: Resume from disk failed.
[    8.553918] EXT4-fs (sda2): barriers enabled
[    8.567122] kjournald2 starting: pid 382, dev sda2:8, commit interval 5 seconds
[    8.567135] EXT4-fs (sda2): delayed allocation enabled
[    8.567140] EXT4-fs: file extents enabled
[    8.568516] EXT4-fs: mballoc enabled
[    8.568534] EXT4-fs (sda2): mounted filesystem with ordered data mode
[    9.115910] type=1505 audit(1257354861.317:2): operation="profile_load" pid=405 name=/usr/share/gdm/guest-session/Xsession
[    9.119015] type=1505 audit(1257354861.321:3): operation="profile_load" pid=406 name=/sbin/dhclient3
[    9.120252] type=1505 audit(1257354861.325:4): operation="profile_load" pid=406 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    9.120909] type=1505 audit(1257354861.325:5): operation="profile_load" pid=406 name=/usr/lib/connman/scripts/dhclient-script
[    9.169721] type=1505 audit(1257354861.373:6): operation="profile_load" pid=407 name=/usr/bin/evince
[    9.188396] type=1505 audit(1257354861.393:7): operation="profile_load" pid=407 name=/usr/bin/evince-previewer
[    9.199444] type=1505 audit(1257354861.401:8): operation="profile_load" pid=407 name=/usr/bin/evince-thumbnailer
[    9.223552] type=1505 audit(1257354861.425:9): operation="profile_load" pid=409 name=/usr/lib/cups/backend/cups-pdf
[    9.224979] type=1505 audit(1257354861.429:10): operation="profile_load" pid=409 name=/usr/sbin/cupsd
[    9.257425] type=1505 audit(1257354861.461:11): operation="profile_load" pid=410 name=/usr/sbin/ntpd
[    9.902639] Adding 4104568k swap on /dev/sda1.  Priority:-1 extents:1 across:4104568k 
[   10.276734] udev: starting version 147
[   10.498714] EXT4-fs (sda2): internal journal on sda2:8
[   11.090925] atl1c 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.090940] atl1c 0000:01:00.0: setting latency timer to 64
[   11.090986] atl1c 0000:01:00.0: PME# disabled
[   11.090994] atl1c 0000:01:00.0: PME# disabled
[   11.196970] atl1c 0000:01:00.0: version 1.0.0.1-NAPI
[   11.237327] cfg80211: Calling CRDA to update world regulatory domain
[   11.295165] Linux video capture interface: v2.00
[   11.360256] lp: driver loaded but no devices found
[   11.517518] acer-wmi: Acer Laptop ACPI-WMI Extras
[   11.534335] acer-wmi: Brightness must be controlled by generic video driver
[   11.682804] uvcvideo: Found UVC 1.00 device CNF9113 (04f2:b160)
[   11.693342] input: CNF9113 as /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/input/input6
[   11.693405] usbcore: registered new interface driver uvcvideo
[   11.693409] USB Video Class driver (v0.1.0)
[   12.218456] EXT4-fs (sda3): barriers enabled
[   12.218820] kjournald2 starting: pid 694, dev sda3:8, commit interval 5 seconds
[   12.249395] EXT4-fs (sda3): internal journal on sda3:8
[   12.249402] EXT4-fs (sda3): delayed allocation enabled
[   12.249406] EXT4-fs: file extents enabled
[   12.284986] EXT4-fs: mballoc enabled
[   12.285009] EXT4-fs (sda3): mounted filesystem with ordered data mode
[   12.286150] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04731/0xa40000
[   12.340058] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input7
[   12.428038] usb 3-2: new full speed USB device using uhci_hcd and address 2
[   12.604169] usb 3-2: configuration #1 chosen from 1 choice
[   12.823971] ip_tables: (C) 2000-2006 Netfilter Core Team
[   13.233436] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.233453] ath9k 0000:02:00.0: setting latency timer to 64
[   13.668703] ath: EEPROM regdomain: 0x65
[   13.668706] ath: EEPROM indicates we should expect a direct regpair map
[   13.668711] ath: Country alpha2 being used: 00
[   13.668714] ath: Regpair used: 0x65
[   13.796031] Bluetooth: Generic Bluetooth USB driver ver 0.5
[   13.796178] usbcore: registered new interface driver btusb
[   13.962620] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   13.963529] Registered led device: ath9k-phy0::radio
[   13.963556] Registered led device: ath9k-phy0::assoc
[   13.963580] Registered led device: ath9k-phy0::tx
[   13.963602] Registered led device: ath9k-phy0::rx
[   13.963629] phy0: Atheros AR9280 MAC/BB Rev:2 AR5133 RF Rev:d0: mem=0xf95c0000, irq=17
[   14.458695] cfg80211: World regulatory domain updated:
[   14.458702] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   14.458707] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.458711] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.458715] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.458719] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.458723] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.068100]   alloc irq_desc for 22 on node -1
[   15.068105]   alloc kstat_irqs on node -1
[   15.068114] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   15.068158] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   15.428961] hda_codec: Unknown model for ALC269, trying auto-probe from BIOS...
[   15.429069] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input8
[   15.447461] __ratelimit: 3 callbacks suppressed
[   15.447466] type=1505 audit(1257354867.649:13): operation="profile_replace" pid=828 name=/usr/share/gdm/guest-session/Xsession
[   15.450690] type=1505 audit(1257354867.653:14): operation="profile_replace" pid=829 name=/sbin/dhclient3
[   15.451895] type=1505 audit(1257354867.653:15): operation="profile_replace" pid=829 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   15.452599] type=1505 audit(1257354867.657:16): operation="profile_replace" pid=829 name=/usr/lib/connman/scripts/dhclient-script
[   15.459452] type=1505 audit(1257354867.661:17): operation="profile_replace" pid=830 name=/usr/bin/evince
[   15.490156] type=1505 audit(1257354867.693:18): operation="profile_replace" pid=830 name=/usr/bin/evince-previewer
[   15.501671] type=1505 audit(1257354867.705:19): operation="profile_replace" pid=830 name=/usr/bin/evince-thumbnailer
[   15.516942] type=1505 audit(1257354867.721:20): operation="profile_replace" pid=836 name=/usr/lib/cups/backend/cups-pdf
[   15.518365] type=1505 audit(1257354867.721:21): operation="profile_replace" pid=836 name=/usr/sbin/cupsd
[   15.616090] type=1505 audit(1257354867.821:22): operation="profile_replace" pid=840 name=/usr/sbin/ntpd
[   21.959722]   alloc irq_desc for 28 on node -1
[   21.959728]   alloc kstat_irqs on node -1
[   21.959749] atl1c 0000:01:00.0: irq 28 for MSI/MSI-X
[   21.959876] atl1c 0000:01:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   22.175143] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.037620] ppdev: user-space parallel port driver
[   25.299444] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   25.299449] Bluetooth: BNEP filters: protocol multicast
[   25.568425] Bridge firewalling registered
[   27.140562] i2c-adapter i2c-2: unable to read EDID block.
[   27.140569] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   27.145001] i2c-adapter i2c-2: unable to read EDID block.
[   27.145005] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   27.334145] i2c-adapter i2c-2: unable to read EDID block.
[   27.334151] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   27.339458] i2c-adapter i2c-2: unable to read EDID block.
[   27.339465] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   28.349500] __ratelimit: 3 callbacks suppressed
[   28.349505] type=1503 audit(1257354880.553:24): operation="capable" pid=1302 parent=1 profile="/usr/sbin/ntpd" name="dac_override"
[   32.776018] eth0: no IPv6 routers present
[   37.459725] i2c-adapter i2c-2: unable to read EDID block.
[   37.459733] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   37.464709] i2c-adapter i2c-2: unable to read EDID block.
[   37.464714] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   37.611665] i2c-adapter i2c-2: unable to read EDID block.
[   37.611671] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   37.616635] i2c-adapter i2c-2: unable to read EDID block.
[   37.616640] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   37.775757] i2c-adapter i2c-2: unable to read EDID block.
[   37.775764] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   37.780713] i2c-adapter i2c-2: unable to read EDID block.
[   37.780717] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   54.331638] i2c-adapter i2c-2: unable to read EDID block.
[   54.331644] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   54.336609] i2c-adapter i2c-2: unable to read EDID block.
[   54.336614] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   54.487656] i2c-adapter i2c-2: unable to read EDID block.
[   54.487662] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   54.492613] i2c-adapter i2c-2: unable to read EDID block.
[   54.492617] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   54.639737] i2c-adapter i2c-2: unable to read EDID block.
[   54.639743] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   54.644696] i2c-adapter i2c-2: unable to read EDID block.
[   54.644701] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   56.744072] i2c-adapter i2c-2: unable to read EDID block.
[   56.744078] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   56.748508] i2c-adapter i2c-2: unable to read EDID block.
[   56.748512] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   62.313398] wlan0: direct probe to AP 00:1d:7e:60:fd:fd try 1
[   62.316220] wlan0 direct probe responded
[   62.316226] wlan0: authenticate with AP 00:1d:7e:60:fd:fd
[   62.318269] wlan0: authenticated
[   62.318276] wlan0: associate with AP 00:1d:7e:60:fd:fd
[   62.328154] wlan0: RX AssocResp from 00:1d:7e:60:fd:fd (capab=0x411 status=0 aid=2)
[   62.328159] wlan0: associated
[   62.328670] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   63.445035] padlock: VIA PadLock not detected.
[   72.876024] wlan0: no IPv6 routers present
[   79.677326] wlan0: disassociating by local choice (reason=3)
[  431.072757] ata5: exception Emask 0x1 SAct 0x0 SErr 0x0 action 0x0
[  431.072763] ata5: irq_stat 0x40000001
[  462.000182] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[  462.000198] ata5.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[  462.000200]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[  462.000202]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[  462.000206] ata5.00: status: { DRDY }
[  462.000213] ata5: hard resetting link
[  467.864035] ata5: failed to reset engine (errno=-5)
[  470.647411] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  470.758159] ata5.00: failed to IDENTIFY (I/O error, err_mask=0x1)
[  470.758165] ata5.00: revalidation failed (errno=-5)
[  475.644050] ata5: hard resetting link
[  477.092046] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  482.092035] ata5.00: qc timeout (cmd 0xa1)
[  482.092048] ata5.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[  482.092052] ata5.00: revalidation failed (errno=-5)
[  482.092060] ata5: limiting SATA link speed to 1.5 Gbps
[  482.092066] ata5: hard resetting link
[  488.756026] ata5: link is slow to respond, please be patient (ready=0)
[  490.548041] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  490.550958] ata5.00: ACPI cmd 00/00:00:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[  490.554696] ata5.00: ACPI cmd 00/00:00:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[  490.554741] ata5.00: configured for UDMA/33
[  490.555013] ata5: EH complete
[  491.648092] ata5: exception Emask 0x1 SAct 0x0 SErr 0x0 action 0x0
[  491.648099] ata5: irq_stat 0x40000001
```

If I search for a word "error" or "failed" there are some errors and fails but I don't understand them quite... Any ideas why this is happening?

---

### Post by spetey on 2009-11-05
I'm having a similar problem; Ubuntu 9.10 won't recognize my CDROM drive at all.  The CD ripper Grip is gone suddenly in 9.10, though it used to work fine in 9.04, and Sound Juicer says I don't have any CDROM drives.  What gives?!  Thanks in advance ...

---

### Post by saechen on 2009-11-07
Bump. Simular problems with 9.10 and Compaq 6510b.

---

### Post by frojnd on 2009-11-07
I found this [http://ubuntuforums.org/showpost.php?p=7759469&postcount=3](http://ubuntuforums.org/showpost.php?p=7759469&postcount=3) BUT this only fix the eject way. Now it would eject immediately but the cd drive still won't recognize any cds dvds!!! Any ideas?

---

### Post by brundles on 2009-11-07
Similar one here - 9.10 doesn't recognise the DVD drive at all:
```
mark@E8200:~/Downloads$ sudo mount /media/cdrom
mount: special device /dev/scd0 does not exist
```

Trawling through lshw, lsmod etc all show the same thing - as far as Ubuntu is concerned, the DVD drive doesn't exit :(.

The drive is a Pioneer installed a couple of years back so nothing new or fancy.

Any suggestions appreciated!

---

### Post by frojnd on 2009-11-19
For all of those ethat hadn't find a solution.... hiemanshu from freenode.org suggested me to change AHCI mode to IDE since I have sata drives... and look at this now cd/DVD rom works :)

---

### Post by Lrpbpb on 2010-03-29
> **frojnd said:**
> For all of those ethat hadn't find a solution.... hiemanshu from freenode.org suggested me to change AHCI mode to IDE since I have sata drives... and look at this now cd/DVD rom works :)

How exactly do you do that??

---

### Post by frojnd on 2010-05-13
As I said in BIOS under (I don't remember what settings) I've changed AHCI mode into IDE mode.

If you don't know how to get into bios: When you power on Acer, you press F12 or Delete and you come into BIOS. Then you search for the AHCI mode under settings (don't know which ones since I don't have this computer with me) and when you find it you change it into IDE mode.

---

