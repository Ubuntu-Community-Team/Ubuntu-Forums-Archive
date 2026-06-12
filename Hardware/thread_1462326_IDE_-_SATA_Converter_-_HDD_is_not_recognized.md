---
title: "IDE - SATA Converter - HDD is not recognized"
date: 2010-04-25
forum: Hardware
---

### Post by wal3 on 2010-04-25
Hello,

I want to connect my IDE HDD where ubuntu 9.10 is installed to my pc . My pc supports only SATA, so I bought this adapter: [http://www.delock.de/produkte/suche/Delock_Konverter_SATA_zu_IDE_61317.html](http://www.delock.de/produkte/suche/Delock_Konverter_SATA_zu_IDE_61317.html)


The HDD is found by BIOS. I cannot boot ubuntu from the harddisk because it gets stuck at the ubuntu image (after grub), works fine on my older pc though.

When I boot from ubuntu live cd (9.10), it does not see the HDD at all. I tried various jumper settings.
When I boot from another HDD where Windows 7 is installed, it finds the ubuntu ide harddisk and all its partitions!

So whats wrong? Isnt the adapter os independend?

Thanks in advance.

dmesg output from livecd:


> 
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
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000dffb0000 (usable)
[    0.000000]  BIOS-e820: 00000000dffb0000 - 00000000dffbe000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000dffbe000 - 00000000dfff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000dfff0000 - 00000000e0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000120000000 (usable)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xdffb0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 base 0000C0000000 mask FFFFE0000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000120000000 aka 4608M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000e0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000dffb0000 (usable)
[    0.000000]  modified: 00000000dffb0000 - 00000000dffbe000 (ACPI data)
[    0.000000]  modified: 00000000dffbe000 - 00000000dfff0000 (ACPI NVS)
[    0.000000]  modified: 00000000dfff0000 - 00000000e0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000120000000 (usable)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
[    0.000000] RAMDISK: 7fa82000 - 7ffff098
[    0.000000] Allocated new RAMDISK: 008ad000 - 00e2a098
[    0.000000] Move RAMDISK from 000000007fa82000 - 000000007ffff097 to 008ad000 - 00e2a097
[    0.000000] ACPI: RSDP 000fb220 00014 (v00 HPQOEM)
[    0.000000] ACPI: RSDT dffb0000 00040 (v01 HPQOEM SLIC-CPC 20100107 MSFT 00000097)
[    0.000000] ACPI: FACP dffb0200 00084 (v01 HPQOEM SLIC-CPC 20100107 MSFT 00000097)
[    0.000000] ACPI: DSDT dffb0450 043AF (v01 HPQOEM SLIC-CPC 00000001 INTL 20051117)
[    0.000000] ACPI: FACS dffbe000 00040
[    0.000000] ACPI: APIC dffb0390 00080 (v01 HPQOEM SLIC-CPC 20100107 MSFT 00000097)
[    0.000000] ACPI: MCFG dffb0410 0003C (v01 HPQOEM SLIC-CPC 20100107 MSFT 00000097)
[    0.000000] ACPI: OEMB dffbe040 00072 (v01 HPQOEM SLIC-CPC 20100107 MSFT 00000097)
[    0.000000] ACPI: HPET dffb4800 00038 (v01 HPQOEM SLIC-CPC 20100107 MSFT 00000097)
[    0.000000] ACPI: SLIC dffbe0c0 00176 (v01 HPQOEM SLIC-CPC 00000001 MSFT 00000001)
[    0.000000] ACPI: SSDT dffb4840 00458 (v01 HPQOEM SLIC-CPC 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2695MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00011000 - 00017f00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [00008a9000 - 00008ac5d4]              BRK ==> [00008a9000 - 00008ac5d4]
[    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #7 [00008ad000 - 0000e2a098]      NEW RAMDISK ==> [00008ad000 - 0000e2a098]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x000dffb0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000dffb0
[    0.000000] On node 0 totalpages: 917311
[    0.000000] free_area_init_node: node 0, pgdat c0784900, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 5392 pages used for memmap
[    0.000000]   HighMem zone: 684706 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at e0000000 (gap: e0000000:1ec00000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c2c10000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 910143
[    0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- debian-installer/language=de console-setup/layoutcode?=de
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 18348160 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:000dffb0)
[    0.000000] Memory: 3607224k/3669696k available (4565k kernel code, 61176k reserved, 2143k data, 540k init, 2760392k highmem)
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
[    0.000000] Detected 2712.283 MHz processor.
[    0.000010] spurious 8259A interrupt: IRQ7.
[    0.001984] Console: colour VGA+ 80x25
[    0.001986] console [tty0] enabled
[    0.002115] hpet clockevent registered
[    0.002118] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.002122] Calibrating delay loop (skipped), value calculated using timer frequency.. 5424.56 BogoMIPS (lpj=10849132)
[    0.002134] Security Framework initialized
[    0.002146] AppArmor: AppArmor initialized
[    0.002152] Mount-cache hash table entries: 512
[    0.002225] Initializing cgroup subsys ns
[    0.002228] Initializing cgroup subsys cpuacct
[    0.002230] Initializing cgroup subsys memory
[    0.002234] Initializing cgroup subsys freezer
[    0.002236] Initializing cgroup subsys net_cls
[    0.002244] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.002246] CPU: L2 Cache: 512K (64 bytes/line)
[    0.002247] CPU: Physical Processor ID: 0
[    0.002249] CPU: Processor Core ID: 0
[    0.002251] mce: CPU supports 6 MCE banks
[    0.002257] using C1E aware idle routine
[    0.002261] Performance Counters: AMD PMU driver.
[    0.002266] ... version:                 0
[    0.002267] ... bit width:               48
[    0.002268] ... generic counters:        4
[    0.002269] ... value mask:              0000ffffffffffff
[    0.002271] ... max period:              00007fffffffffff
[    0.002272] ... fixed-purpose counters:  0
[    0.002273] ... counter mask:            000000000000000f
[    0.002276] Checking 'hlt' instruction... OK.
[    0.017514] ACPI: Core revision 20090521
[    0.023452] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.063145] CPU0: AMD Athlon(tm) II X2 215 Processor stepping 02
[    0.064001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 5424.63 BogoMIPS (lpj=10849275)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] mce: CPU supports 6 MCE banks
[    0.004000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.148377] CPU1: AMD Athlon(tm) II X2 215 Processor stepping 02
[    0.148387] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.152009] Brought up 2 CPUs
[    0.152011] Total of 2 processors activated (10849.20 BogoMIPS).
[    0.152089] CPU0 attaching sched-domain:
[    0.152091]  domain 0: span 0-1 level MC
[    0.152093]   groups: 0 1
[    0.152097] CPU1 attaching sched-domain:
[    0.152098]  domain 0: span 0-1 level MC
[    0.152100]   groups: 1 0
[    0.152153] Booting paravirtualized kernel on bare hardware
[    0.152153] regulator: core version 0.5
[    0.152153] Time: 17:19:20  Date: 04/25/10
[    0.152153] NET: Registered protocol family 16
[    0.152153] EISA bus registered
[    0.152164] ACPI: bus type pci registered
[    0.152213] PCI: MCFG configuration 0: base fc000000 segment 0 buses 0 - 31
[    0.152215] PCI: Not using MMCONFIG.
[    0.152820] PCI: Using configuration type 1 for base access
[    0.152821] PCI: Using configuration type 1 for extended access
[    0.153396] bio: create slab <bio-0> at 0
[    0.153396] ACPI: EC: Look up EC in DSDT
[    0.159466] ACPI: Interpreter enabled
[    0.159469] ACPI: (supports S0 S1 S3 S4 S5)
[    0.159485] ACPI: Using IOAPIC for interrupt routing
[    0.159519] PCI: MCFG configuration 0: base fc000000 segment 0 buses 0 - 31
[    0.161338] PCI: MCFG area at fc000000 reserved in ACPI motherboard resources
[    0.161340] PCI: Using MMCONFIG for extended config space
[    0.164916] ACPI: No dock devices found.
[    0.165142] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.165305] pci 0000:00:01.0: reg 10 io port: [0x4f00-0x4fff]
[    0.165339] pci 0000:00:01.1: reg 10 io port: [0x4900-0x493f]
[    0.165348] pci 0000:00:01.1: reg 20 io port: [0x4d00-0x4d3f]
[    0.165352] pci 0000:00:01.1: reg 24 io port: [0x4e00-0x4e3f]
[    0.165369] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.165374] pci 0000:00:01.1: PME# disabled
[    0.165416] pci 0000:00:02.0: reg 10 32bit mmio: [0xfaeff000-0xfaefffff]
[    0.165435] pci 0000:00:02.0: supports D1 D2
[    0.165437] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.165439] pci 0000:00:02.0: PME# disabled
[    0.165458] pci 0000:00:02.1: reg 10 32bit mmio: [0xfaefec00-0xfaefecff]
[    0.165482] pci 0000:00:02.1: supports D1 D2
[    0.165484] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.165486] pci 0000:00:02.1: PME# disabled
[    0.165539] pci 0000:00:05.0: reg 10 32bit mmio: [0xfaef8000-0xfaefbfff]
[    0.165562] pci 0000:00:05.0: PME# supported from D3hot D3cold
[    0.165564] pci 0000:00:05.0: PME# disabled
[    0.165593] pci 0000:00:07.0: reg 10 32bit mmio: [0xfaefd000-0xfaefdfff]
[    0.165596] pci 0000:00:07.0: reg 14 io port: [0xd480-0xd487]
[    0.165615] pci 0000:00:07.0: supports D1 D2
[    0.165617] pci 0000:00:07.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.165621] pci 0000:00:07.0: PME# disabled
[    0.165638] pci 0000:00:08.0: reg 10 io port: [0xd400-0xd407]
[    0.165641] pci 0000:00:08.0: reg 14 io port: [0xd080-0xd083]
[    0.165644] pci 0000:00:08.0: reg 18 io port: [0xd000-0xd007]
[    0.165647] pci 0000:00:08.0: reg 1c io port: [0xcc00-0xcc03]
[    0.165650] pci 0000:00:08.0: reg 20 io port: [0xc880-0xc88f]
[    0.165653] pci 0000:00:08.0: reg 24 32bit mmio: [0xfaefc000-0xfaefcfff]
[    0.165679] pci 0000:00:08.1: reg 10 io port: [0xc800-0xc807]
[    0.165682] pci 0000:00:08.1: reg 14 io port: [0xc480-0xc483]
[    0.165685] pci 0000:00:08.1: reg 18 io port: [0xc400-0xc407]
[    0.165688] pci 0000:00:08.1: reg 1c io port: [0xc080-0xc083]
[    0.165691] pci 0000:00:08.1: reg 20 io port: [0xc000-0xc00f]
[    0.165694] pci 0000:00:08.1: reg 24 32bit mmio: [0xfaef7000-0xfaef7fff]
[    0.165734] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.165736] pci 0000:00:09.0: PME# disabled
[    0.165762] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.165764] pci 0000:00:0b.0: PME# disabled
[    0.165790] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.165792] pci 0000:00:0c.0: PME# disabled
[    0.165894] pci 0000:00:04.0: transparent bridge
[    0.165916] pci 0000:02:00.0: reg 10 32bit mmio: [0xfb000000-0xfbffffff]
[    0.165923] pci 0000:02:00.0: reg 14 64bit mmio: [0xe0000000-0xefffffff]
[    0.165929] pci 0000:02:00.0: reg 1c 64bit mmio: [0xf8000000-0xf9ffffff]
[    0.165933] pci 0000:02:00.0: reg 24 io port: [0xec00-0xec7f]
[    0.165937] pci 0000:02:00.0: reg 30 32bit mmio: [0xfaf80000-0xfaffffff]
[    0.165976] pci 0000:02:00.1: reg 10 32bit mmio: [0xfaf7c000-0xfaf7ffff]
[    0.166037] pci 0000:00:09.0: bridge io port: [0xe000-0xefff]
[    0.166039] pci 0000:00:09.0: bridge 32bit mmio: [0xfaf00000-0xfbffffff]
[    0.166043] pci 0000:00:09.0: bridge 64bit mmio pref: [0xe0000000-0xf9ffffff]
[    0.166111] pci_bus 0000:00: on NUMA node 0
[    0.166114] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.166230] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.166282] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR10._PRT]
[    0.166322] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR11._PRT]
[    0.166361] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR12._PRT]
[    0.170980] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
[    0.171128] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.
[    0.171271] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[    0.171414] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
[    0.171558] ACPI: PCI Interrupt Link [LNEA] (IRQs 16 17 18 19) *0, disabled.
[    0.171701] ACPI: PCI Interrupt Link [LNEB] (IRQs 16 17 18 19) *0, disabled.
[    0.171844] ACPI: PCI Interrupt Link [LNEC] (IRQs 16 17 18 19) *0, disabled.
[    0.171990] ACPI: PCI Interrupt Link [LNED] (IRQs 16 17 18 19) *10
[    0.172145] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *14
[    0.172291] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *7
[    0.172443] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *11
[    0.172589] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *10
[    0.172732] ACPI: PCI Interrupt Link [LMC9] (IRQs 20 21 22 23) *0, disabled.
[    0.172879] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *11
[    0.173022] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *0, disabled.
[    0.173169] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *5
[    0.173315] ACPI: PCI Interrupt Link [LSA1] (IRQs 20 21 22 23) *5
[    0.173481] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[    0.173596] SCSI subsystem initialized
[    0.173626] libata version 3.00 loaded.
[    0.173626] usbcore: registered new interface driver usbfs
[    0.173626] usbcore: registered new interface driver hub
[    0.173626] usbcore: registered new device driver usb
[    0.173626] ACPI: WMI: Mapper loaded
[    0.173626] PCI: Using ACPI for IRQ routing
[    0.184019] Bluetooth: Core ver 2.15
[    0.184050] NET: Registered protocol family 31
[    0.184050] Bluetooth: HCI device and connection manager initialized
[    0.184050] Bluetooth: HCI socket layer initialized
[    0.184050] NetLabel: Initializing
[    0.184050] NetLabel:  domain hash size = 128
[    0.184050] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.184050] NetLabel:  unlabeled traffic allowed by default
[    0.184067] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
[    0.184071] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.200022] pnp: PnP ACPI init
[    0.200036] ACPI: bus type pnp registered
[    0.202083] pnp: PnP ACPI: found 11 devices
[    0.202085] ACPI: ACPI bus type pnp unregistered
[    0.202087] PnPBIOS: Disabled by ACPI PNP
[    0.202095] system 00:05: ioport range 0xa00-0xadf has been reserved
[    0.202099] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[    0.202101] system 00:06: ioport range 0x800-0x80f has been reserved
[    0.202104] system 00:06: ioport range 0x4000-0x407f has been reserved
[    0.202106] system 00:06: ioport range 0x4080-0x40ff has been reserved
[    0.202108] system 00:06: ioport range 0x4400-0x447f has been reserved
[    0.202110] system 00:06: ioport range 0x4480-0x44ff has been reserved
[    0.202111] system 00:06: ioport range 0x4800-0x487f has been reserved
[    0.202114] system 00:06: ioport range 0x4880-0x48ff has been reserved
[    0.202116] system 00:06: ioport range 0x4c00-0x4c7f has been reserved
[    0.202118] system 00:06: ioport range 0x4c80-0x4cff has been reserved
[    0.202120] system 00:06: iomem range 0xfec80000-0xfd93ffff could not be reserved
[    0.202123] system 00:06: iomem range 0xfefe0000-0xfefe01ff has been reserved
[    0.202125] system 00:06: iomem range 0xfefe1000-0xfefe1fff has been reserved
[    0.202127] system 00:06: iomem range 0xfee01000-0xfeefffff has been reserved
[    0.202129] system 00:06: iomem range 0xffb80000-0xffffffff could not be reserved
[    0.202133] system 00:08: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.202136] system 00:08: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.202139] system 00:09: iomem range 0xfc000000-0xfdffffff has been reserved
[    0.202143] system 00:0a: iomem range 0x0-0x9ffff could not be reserved
[    0.202145] system 00:0a: iomem range 0xc0000-0xcffff could not be reserved
[    0.202147] system 00:0a: iomem range 0xe0000-0xfffff could not be reserved
[    0.202149] system 00:0a: iomem range 0x100000-0xdfffffff could not be reserved
[    0.202152] system 00:0a: iomem range 0xfec00000-0xffffffff could not be reserved
[    0.236767] AppArmor: AppArmor Filesystem Enabled
[    0.236786] pci 0000:00:04.0: PCI bridge, secondary bus 0000:01
[    0.236788] pci 0000:00:04.0:   IO window: disabled
[    0.236790] pci 0000:00:04.0:   MEM window: disabled
[    0.236793] pci 0000:00:04.0:   PREFETCH window: disabled
[    0.236795] pci 0000:00:09.0: PCI bridge, secondary bus 0000:02
[    0.236797] pci 0000:00:09.0:   IO window: 0xe000-0xefff
[    0.236800] pci 0000:00:09.0:   MEM window: 0xfaf00000-0xfbffffff
[    0.236802] pci 0000:00:09.0:   PREFETCH window: 0x000000e0000000-0x000000f9ffffff
[    0.236805] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:03
[    0.236807] pci 0000:00:0b.0:   IO window: disabled
[    0.236809] pci 0000:00:0b.0:   MEM window: disabled
[    0.236810] pci 0000:00:0b.0:   PREFETCH window: disabled
[    0.236813] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:04
[    0.236814] pci 0000:00:0c.0:   IO window: disabled
[    0.236816] pci 0000:00:0c.0:   MEM window: disabled
[    0.236818] pci 0000:00:0c.0:   PREFETCH window: disabled
[    0.236823] pci 0000:00:04.0: setting latency timer to 64
[    0.236827] pci 0000:00:09.0: setting latency timer to 64
[    0.236831] pci 0000:00:0b.0: setting latency timer to 64
[    0.236834] pci 0000:00:0c.0: setting latency timer to 64
[    0.236837] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.236839] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.236841] pci_bus 0000:01: resource 3 io:  [0x00-0xffff]
[    0.236842] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffff]
[    0.236844] pci_bus 0000:02: resource 0 io:  [0xe000-0xefff]
[    0.236846] pci_bus 0000:02: resource 1 mem: [0xfaf00000-0xfbffffff]
[    0.236848] pci_bus 0000:02: resource 2 pref mem [0xe0000000-0xf9ffffff]
[    0.236874] NET: Registered protocol family 2
[    0.236938] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.237139] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.237540] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.237736] TCP: Hash tables configured (established 131072 bind 65536)
[    0.237738] TCP reno registered
[    0.237801] NET: Registered protocol family 1
[    0.237844] Trying to unpack rootfs image as initramfs...
[    0.500413] Switched to high resolution mode on CPU 1
[    0.503999] Switched to high resolution mode on CPU 0
[    1.203442] Freeing initrd memory: 5620k freed
[    1.205147] cpufreq-nforce2: No nForce2 chipset.
[    1.205169] Scanning for low memory corruption every 60 seconds
[    1.205233] audit: initializing netlink socket (disabled)
[    1.205243] type=2000 audit(1272215961.204:1): initialized
[    1.211456] highmem bounce pool size: 64 pages
[    1.211460] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.212381] VFS: Disk quotas dquot_6.5.2
[    1.212419] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.212794] fuse init (API version 7.12)
[    1.212845] msgmni has been set to 1666
[    1.213001] alg: No test for stdrng (krng)
[    1.213016] io scheduler noop registered
[    1.213018] io scheduler anticipatory registered
[    1.213019] io scheduler deadline registered
[    1.213047] io scheduler cfq registered (default)
[    1.234864] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    1.234910] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    1.234959] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    1.235010] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    1.235061] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    1.235115] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    1.235174] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    1.235236] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    1.235249] pci 0000:02:00.0: Boot video device
[    1.235317]   alloc irq_desc for 24 on node -1
[    1.235319]   alloc kstat_irqs on node -1
[    1.235325] pcieport-driver 0000:00:09.0: irq 24 for MSI/MSI-X
[    1.235329] pcieport-driver 0000:00:09.0: setting latency timer to 64
[    1.235380]   alloc irq_desc for 25 on node -1
[    1.235382]   alloc kstat_irqs on node -1
[    1.235385] pcieport-driver 0000:00:0b.0: irq 25 for MSI/MSI-X
[    1.235388] pcieport-driver 0000:00:0b.0: setting latency timer to 64
[    1.235438]   alloc irq_desc for 26 on node -1
[    1.235439]   alloc kstat_irqs on node -1
[    1.235443] pcieport-driver 0000:00:0c.0: irq 26 for MSI/MSI-X
[    1.235446] pcieport-driver 0000:00:0c.0: setting latency timer to 64
[    1.235486] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.235502] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.235579] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.235582] ACPI: Power Button [PWRF]
[    1.235621] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.235623] ACPI: Power Button [PWRB]
[    1.235793] processor LNXCPU:00: registered as cooling_device0
[    1.235814] processor LNXCPU:01: registered as cooling_device1
[    1.237162] isapnp: Scanning for PnP cards...
[    1.590258] isapnp: No Plug & Play device found
[    1.591031] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.591780] brd: module loaded
[    1.592052] loop: module loaded
[    1.592098] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.592225] sata_nv 0000:00:08.0: version 3.5
[    1.592465] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 23
[    1.592469]   alloc irq_desc for 23 on node -1
[    1.592470]   alloc kstat_irqs on node -1
[    1.592478] sata_nv 0000:00:08.0: PCI INT A -> Link[LSA0] -> GSI 23 (level, low) -> IRQ 23
[    1.592517] sata_nv 0000:00:08.0: setting latency timer to 64
[    1.592587] scsi0 : sata_nv
[    1.592656] scsi1 : sata_nv
[    1.592745] ata1: SATA max UDMA/133 cmd 0xd400 ctl 0xd080 bmdma 0xc880 irq 23
[    1.592747] ata2: SATA max UDMA/133 cmd 0xd000 ctl 0xcc00 bmdma 0xc888 irq 23
[    1.592971] ACPI: PCI Interrupt Link [LSA1] enabled at IRQ 22
[    1.592972]   alloc irq_desc for 22 on node -1
[    1.592974]   alloc kstat_irqs on node -1
[    1.592980] sata_nv 0000:00:08.1: PCI INT B -> Link[LSA1] -> GSI 22 (level, low) -> IRQ 22
[    1.592998] sata_nv 0000:00:08.1: setting latency timer to 64
[    1.593122] scsi2 : sata_nv
[    1.593188] scsi3 : sata_nv
[    1.593281] ata3: SATA max UDMA/133 cmd 0xc800 ctl 0xc480 bmdma 0xc000 irq 22
[    1.593283] ata4: SATA max UDMA/133 cmd 0xc400 ctl 0xc080 bmdma 0xc008 irq 22
[    1.593764] Fixed MDIO Bus: probed
[    1.593786] PPP generic driver version 2.4.2
[    1.593850] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.594084] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 21
[    1.594086]   alloc irq_desc for 21 on node -1
[    1.594088]   alloc kstat_irqs on node -1
[    1.594095] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUB2] -> GSI 21 (level, low) -> IRQ 21
[    1.594104] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    1.594106] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    1.594138] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    1.594158] ehci_hcd 0000:00:02.1: debug port 1
[    1.594161] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    1.594177] ehci_hcd 0000:00:02.1: irq 21, io mem 0xfaefec00
[    1.604528] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    1.604610] usb usb1: configuration #1 chosen from 1 choice
[    1.604630] hub 1-0:1.0: USB hub found
[    1.604636] hub 1-0:1.0: 10 ports detected
[    1.604686] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.604939] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 20
[    1.604942]   alloc irq_desc for 20 on node -1
[    1.604943]   alloc kstat_irqs on node -1
[    1.604951] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUB0] -> GSI 20 (level, low) -> IRQ 20
[    1.604961] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    1.604964] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    1.604987] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    1.605007] ohci_hcd 0000:00:02.0: irq 20, io mem 0xfaeff000
[    1.662077] usb usb2: configuration #1 chosen from 1 choice
[    1.662097] hub 2-0:1.0: USB hub found
[    1.662104] hub 2-0:1.0: 10 ports detected
[    1.662150] uhci_hcd: USB Universal Host Controller Interface driver
[    1.662209] PNP: No PS/2 controller found. Probing ports directly.
[    1.664126] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.664133] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.664184] mice: PS/2 mouse device common for all mice
[    1.664246] rtc_cmos 00:02: RTC can wake from S4
[    1.664271] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.664306] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    1.664380] device-mapper: uevent: version 1.0.3
[    1.664469] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    1.664535] device-mapper: multipath: version 1.1.0 loaded
[    1.664537] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.664619] EISA: Probing bus 0 at eisa.0
[    1.664628] Cannot allocate resource for EISA slot 4
[    1.664639] EISA: Detected 0 cards.
[    1.664709] cpuidle: using governor ladder
[    1.664711] cpuidle: using governor menu
[    1.665039] TCP cubic registered
[    1.665137] NET: Registered protocol family 10
[    1.665434] lo: Disabled Privacy Extensions
[    1.665653] NET: Registered protocol family 17
[    1.665664] Bluetooth: L2CAP ver 2.13
[    1.665665] Bluetooth: L2CAP socket layer initialized
[    1.665667] Bluetooth: SCO (Voice Link) ver 0.6
[    1.665668] Bluetooth: SCO socket layer initialized
[    1.665704] Bluetooth: RFCOMM TTY layer initialized
[    1.665706] Bluetooth: RFCOMM socket layer initialized
[    1.665708] Bluetooth: RFCOMM ver 1.11
[    1.665720] powernow-k8: Found 1 AMD Athlon(tm) II X2 215 Processor processors (2 cpu cores) (version 2.20.00)
[    1.665747] powernow-k8:    0 : pstate 0 (2700 MHz)
[    1.665749] powernow-k8:    1 : pstate 1 (2100 MHz)
[    1.665750] powernow-k8:    2 : pstate 2 (1500 MHz)
[    1.665752] powernow-k8:    3 : pstate 3 (800 MHz)
[    1.665854] Using IPI No-Shortcut mode
[    1.665898] PM: Resume from disk failed.
[    1.665905] registered taskstats version 1
[    1.665986]   Magic number: 6:939:340
[    1.666064] rtc_cmos 00:02: setting system clock to 2010-04-25 17:19:22 UTC (1272215962)
[    1.666067] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.666068] EDD information not available.
[    1.748046] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.748175] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.756226] ata3.00: ATAPI: hp        DDVDW TS-H653R, 0E00, max UDMA/100
[    1.756353] ata1.00: ATA-8: WDC WD5000AAKB-00H8A0, 05.04E05, max UDMA/100
[    1.756355] ata1.00: 268435455 sectors, multi 16: LBA 
[    1.756363] ata1.00: applying bridge limits
[    1.772161] ata3.00: configured for UDMA/100
[    1.772216] ata1.00: NODEV after polling detection
[    1.772218] ata1.00: revalidation failed (errno=-2)
[    2.028032] usb 1-8: new high speed USB device using ehci_hcd and address 4
[    2.162782] usb 1-8: configuration #1 chosen from 1 choice
[    2.464029] usb 2-3: new low speed USB device using ohci_hcd and address 2
[    2.673128] usb 2-3: configuration #1 chosen from 1 choice
[    2.980030] usb 2-4: new low speed USB device using ohci_hcd and address 3
[    3.193145] usb 2-4: configuration #1 chosen from 1 choice
[    6.904040] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    6.928050] ata1.00: NODEV after polling detection
[    6.928053] ata1.00: revalidation failed (errno=-2)
[   12.060045] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   17.068037] ata1.00: qc timeout (cmd 0x27)
[   17.068041] ata1.00: failed to read native max address (err_mask=0x4)
[   17.068044] ata1.00: revalidation failed (errno=-5)
[   17.068046] ata1.00: disabled
[   17.068056] ata1: hard resetting link
[   17.068058] ata1: nv: skipping hardreset on occupied port
[   17.224040] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   17.224048] ata1: EH complete
[   17.234344] ata2: SATA link down (SStatus 0 SControl 300)
[   17.234965] scsi 2:0:0:0: CD-ROM            hp       CDDVDW TS-H653R  0E00 PQ: 0 ANSI: 5
[   17.239275] sr0: scsi3-mmc drive: 125x/125x writer dvd-ram cd/rw xa/form2 cdda tray
[   17.239279] Uniform CD-ROM driver Revision: 3.20
[   17.239348] sr 2:0:0:0: Attached scsi CD-ROM sr0
[   17.239387] sr 2:0:0:0: Attached scsi generic sg0 type 5
[   17.249689] ata4: SATA link down (SStatus 0 SControl 300)
[   17.249724] Freeing unused kernel memory: 540k freed
[   17.249907] Write protecting the kernel text: 4568k
[   17.249933] Write protecting the kernel read-only data: 1836k
[   17.349347] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[   17.349608] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 23
[   17.349612] forcedeth 0000:00:07.0: PCI INT A -> Link[LMAC] -> GSI 23 (level, low) -> IRQ 23
[   17.349616] forcedeth 0000:00:07.0: setting latency timer to 64
[   17.383491] usbcore: registered new interface driver hiddev
[   17.388807] Initializing USB Mass Storage driver...
[   17.388895] scsi4 : SCSI emulation for USB Mass Storage devices
[   17.388969] usbcore: registered new interface driver usb-storage
[   17.388971] USB Mass Storage support registered.
[   17.389041] usb-storage: device found at 4
[   17.389043] usb-storage: waiting for device to settle before scanning
[   17.389506] input: USB Optical Mouse as /devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.0/input/input3
[   17.389560] generic-usb 0003:0461:4D20.0001: input,hidraw0: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:02.0-3/input0
[   17.395072] input: NOVATEK USB Keyboard as /devices/pci0000:00/0000:00:02.0/usb2/2-4/2-4:1.0/input/input4
[   17.395118] generic-usb 0003:0461:0010.0002: input,hidraw1: USB HID v1.10 Keyboard [NOVATEK USB Keyboard] on usb-0000:00:02.0-4/input0
[   17.407415] input: NOVATEK USB Keyboard as /devices/pci0000:00/0000:00:02.0/usb2/2-4/2-4:1.1/input/input5
[   17.407459] generic-usb 0003:0461:0010.0003: input,hidraw2: USB HID v1.10 Device [NOVATEK USB Keyboard] on usb-0000:00:02.0-4/input1
[   17.407472] usbcore: registered new interface driver usbhid
[   17.407474] usbhid: v2.6:USB HID core driver
[   17.868867] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x732 @ 1, addr f4:ce:46:ef:69:0e
[   17.868871] forcedeth 0000:00:07.0: highdma pwrctl mgmt lnktim msi desc-v3
[   18.463917] xor: automatically using best checksumming function: pIII_sse
[   18.480510]    pIII_sse  : 10878.000 MB/sec
[   18.480512] xor: using function: pIII_sse (10878.000 MB/sec)
[   18.482181] device-mapper: dm-raid45: initialized v0.2594b
[   19.273654] ISO 9660 Extensions: Microsoft Joliet Level 3
[   19.297576] ISO 9660 Extensions: RRIP_1991A
[   19.430898] aufs 2-standalone.tree-30-20090727
[   19.541392] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[   22.388162] usb-storage: device scan complete
[   22.388903] scsi 4:0:0:0: Direct-Access     Multi    Flash Reader     1.00 PQ: 0 ANSI: 0
[   22.389263] sd 4:0:0:0: Attached scsi generic sg1 type 0
[   22.392279] sd 4:0:0:0: [sda] Attached SCSI removable disk
[   54.243235] udev: starting version 147
[   54.649236] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x4d00
[   54.649249] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x4e00
[   57.107147] ip_tables: (C) 2000-2006 Netfilter Core Team
[   58.297650] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 22
[   58.297655] HDA Intel 0000:00:05.0: PCI INT B -> Link[LAZA] -> GSI 22 (level, low) -> IRQ 22
[   58.297673] HDA Intel 0000:00:05.0: setting latency timer to 64
[   58.778302]   alloc irq_desc for 27 on node -1
[   58.778305]   alloc kstat_irqs on node -1
[   58.778312] forcedeth 0000:00:07.0: irq 27 for MSI/MSI-X
[   58.984029] hda_codec: Unknown model for ALC662 rev1, trying auto-probe from BIOS...
[   59.232080] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:05.0/input/input6
[   64.539898] lp: driver loaded but no devices found
[   64.720032] ppdev: user-space parallel port driver
[   68.952018] eth0: no IPv6 routers present
[   71.065333] CPU0 attaching NULL sched-domain.
[   71.065338] CPU1 attaching NULL sched-domain.
[   71.080318] CPU0 attaching sched-domain:
[   71.080321]  domain 0: span 0-1 level MC
[   71.080324]   groups: 0 1
[   71.080327]   domain 1: span 0-1 level CPU
[   71.080329]    groups: 0-1 (__cpu_power = 2048)
[   71.080333] CPU1 attaching sched-domain:
[   71.080334]  domain 0: span 0-1 level MC
[   71.080336]   groups: 1 0
[   71.080338]   domain 1: span 0-1 level CPU
[   71.080340]    groups: 0-1 (__cpu_power = 2048)
[   75.252576] CPU0 attaching NULL sched-domain.
[   75.252581] CPU1 attaching NULL sched-domain.
[   75.272059] CPU0 attaching sched-domain:
[   75.272062]  domain 0: span 0-1 level MC
[   75.272065]   groups: 0 1
[   75.272069] CPU1 attaching sched-domain:
[   75.272071]  domain 0: span 0-1 level MC
[   75.272072]   groups: 1 0

---

### Post by wal3 on 2010-04-25
> 
[ 1.756353] ata1.00: ATA-8: WDC WD5000AAKB-00H8A0, 05.04E05, max UDMA/100
[ 1.756355] ata1.00: 268435455 sectors, multi 16: LBA
[ 1.756363] ata1.00: applying bridge limits
[ 1.772161] ata3.00: configured for UDMA/100
[ 1.772216] ata1.00: NODEV after polling detection
[ 1.772218] ata1.00: revalidation failed (errno=-2)
..
[ 17.068037] ata1.00: qc timeout (cmd 0x27)
[ 17.068041] ata1.00: failed to read native max address (err_mask=0x4)
[ 17.068044] ata1.00: revalidation failed (errno=-5)
[ 17.068046] ata1.00: disabled


Any ideas?

---

### Post by wallymann on 2011-11-21
did you ever figure this out?

ive tried a couple different IDE->SATA adapters, none work with 10.10 on my workstation.

ive also tried them on my linux-based tivo unit, also no joy.

---

