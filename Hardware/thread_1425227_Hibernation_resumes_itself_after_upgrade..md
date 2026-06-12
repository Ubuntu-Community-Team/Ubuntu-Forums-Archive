---
title: "Hibernation resumes itself after upgrade."
date: 2010-03-08
forum: Hardware
---

### Post by P3t3r on 2010-03-08
I am running Kubuntu 9.10 on a Toshiba Portege R600. I have a strange problem with hibernation. When I hibernate, it locks & turns off the screen, writes the image to disk, but instead of powering off the computer, it just resumes and I end up with the same effect as lock screen. Now I really can't use hibernate at all -- which is desastrous for my battery life.

For your information I am posting my "dmesg" below, before and after the failed hibernation. Thanks in advance for looking into this.

Before failed hibernation, my dmesg looks like this:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-20-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu9) ) #57-Ubuntu SMP Mon Feb 8 09:05:19 UTC 2010 (Ubuntu 2.6.31-20.57-generic)
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
[    0.000000]  BIOS-e820: 00000000000e8000 - 00000000000eee00 (reserved)
[    0.000000]  BIOS-e820: 00000000000eee00 - 00000000000ef000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000000ef000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000b3990000 (usable)
[    0.000000]  BIOS-e820: 00000000b3990000 - 00000000b39a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000b39a0000 - 00000000b39a2000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b39b0000 - 00000000bc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec18000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec28000 - 00000000fec30000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00500 (reserved)
[    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed94000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffa00000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffd00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.5 present.
[    0.000000] last_pfn = 0xb3990 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-D3FFF write-protect
[    0.000000]   D4000-E7FFF uncachable
[    0.000000]   E8000-EFFFF write-back
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0FFE00000 mask FFFE00000 write-protect
[    0.000000]   1 base 000000000 mask F80000000 write-back
[    0.000000]   2 base 080000000 mask FC0000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e8000 - 00000000000eee00 (reserved)
[    0.000000]  modified: 00000000000eee00 - 00000000000ef000 (ACPI NVS)
[    0.000000]  modified: 00000000000ef000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000b3990000 (usable)
[    0.000000]  modified: 00000000b3990000 - 00000000b39a0000 (reserved)
[    0.000000]  modified: 00000000b39a0000 - 00000000b39a2000 (ACPI NVS)
[    0.000000]  modified: 00000000b39b0000 - 00000000bc000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec18000 (reserved)
[    0.000000]  modified: 00000000fec28000 - 00000000fec30000 (reserved)
[    0.000000]  modified: 00000000fed00000 - 00000000fed00500 (reserved)
[    0.000000]  modified: 00000000fed10000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed94000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffa00000 - 00000000ffc00000 (reserved)
[    0.000000]  modified: 00000000ffd00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 37812000 - 37fef89b
[    0.000000] Allocated new RAMDISK: 008b2000 - 0108f89b
[    0.000000] Move RAMDISK from 0000000037812000 - 0000000037fef89a to 008b2000 - 0108f89a
[    0.000000] ACPI: RSDP 000f00b0 00014 (v00 TOSHIB)
[    0.000000] ACPI: RSDT b3990000 0005C (v01 TOSHIB A006A    20090903 TASM 04010000)
[    0.000000] ACPI: FACP b399008c 00084 (v02 TOSHIB A006A    20090903 TASM 04010000)
[    0.000000] ACPI: DSDT b3990110 0692B (v02 TOSHIB A006A    20090903 MSFT 03000000)
[    0.000000] ACPI: FACS 000eee00 00040
[    0.000000] ACPI: SSDT b3996a3b 00506 (v02 TOSHIB A006B    20070720 MSFT 03000000)
[    0.000000] ACPI: BOOT b3990064 00028 (v01 TOSHIB A006A    20090903 TASM 04010000)
[    0.000000] ACPI: APIC b3997515 00068 (v01 TOSHIB A006A    20090903 TASM 04010000)
[    0.000000] ACPI: MCFG b399757d 0003C (v01 TOSHIB A006A    20090903 TASM 04010000)
[    0.000000] ACPI: HPET b39975b9 00038 (v01 TOSHIB A006A    20090903 TASM 04010000)
[    0.000000] ACPI: TCPA b39978be 00032 (v02 TOSHIB A006A    20090903 TASM 04010000)
[    0.000000] ACPI: SLIC b39978f0 00176 (v01 TOSHIB A006A    20090903 TASM 04010000)
[    0.000000] ACPI: ASF! b3997625 00075 (v16 TOSHIB A006A    20090903 TASM 04010000)
[    0.000000] ACPI: SSDT b3998c38 0012C (v02 TOSHIB A006B    20080801 MSFT 03000000)
[    0.000000] ACPI: SSDT b3997a66 00076 (v02 TOSHIB A006B    20061226 MSFT 03000000)
[    0.000000] ACPI: SSDT b3998e69 00046 (v02 TOSHIB A006B    20080929 MSFT 03000000)
[    0.000000] ACPI: SSDT b3998eaf 001E3 (v02 TOSHIB A006B    20090623 MSFT 03000000)
[    0.000000] ACPI: SSDT b3997adc 00A29 (v02 TOSHIB A006B    20080303 MSFT 03000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1985MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008ad060]    TEXT DATA BSS ==> [0000100000 - 00008ad060]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [00008ae000 - 00008b1204]              BRK ==> [00008ae000 - 00008b1204]
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #7 [00008b2000 - 000108f89b]      NEW RAMDISK ==> [00008b2000 - 000108f89b]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x000b3990
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000b3990
[    0.000000] On node 0 totalpages: 735531
[    0.000000] free_area_init_node: node 0, pgdat c0788920, node_mem_map c1090000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 3972 pages used for memmap
[    0.000000]   HighMem zone: 504334 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0xd808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
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
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e8000
[    0.000000] PM: Registered nosave memory: 00000000000e8000 - 00000000000ee000
[    0.000000] PM: Registered nosave memory: 00000000000ee000 - 00000000000ef000
[    0.000000] PM: Registered nosave memory: 00000000000ef000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at bc000000 (gap: bc000000:42c00000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c2712000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 729783
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-20-generic root=UUID=7711e52a-32fd-44fc-9370-9e78f8f372a8 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 14712640 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:000b3990)
[    0.000000] Memory: 2886956k/2942528k available (4579k kernel code, 54284k reserved, 2145k data, 540k init, 2033224k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc0792000 - 0xc0819000   ( 540 kB)
[    0.000000]       .data : 0xc0578c68 - 0xc0791448   (2145 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0578c68   (4579 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Fast TSC calibration failed
[    0.000000] TSC: PIT calibration matches PMTIMER. 2 loops
[    0.000000] Detected 1396.454 MHz processor.
[    0.001512] Console: colour VGA+ 80x25
[    0.001517] console [tty0] enabled
[    0.001741] hpet clockevent registered
[    0.001747] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.001754] Calibrating delay loop (skipped), value calculated using timer frequency.. 2792.90 BogoMIPS (lpj=5585816)
[    0.001776] Security Framework initialized
[    0.001800] AppArmor: AppArmor initialized
[    0.001808] Mount-cache hash table entries: 512
[    0.001956] Initializing cgroup subsys ns
[    0.001962] Initializing cgroup subsys cpuacct
[    0.001967] Initializing cgroup subsys memory
[    0.001975] Initializing cgroup subsys freezer
[    0.001978] Initializing cgroup subsys net_cls
[    0.001996] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.001999] CPU: L2 cache: 3072K
[    0.002003] CPU: Physical Processor ID: 0
[    0.002006] CPU: Processor Core ID: 0
[    0.002010] mce: CPU supports 6 MCE banks
[    0.002020] CPU0: Thermal monitoring handled by SMI
[    0.002024] using mwait in idle threads.
[    0.002032] Performance Counters: Core2 events, Intel PMU driver.
[    0.002042] ... version:                 2
[    0.002044] ... bit width:               40
[    0.002047] ... generic counters:        2
[    0.002049] ... value mask:              000000ffffffffff
[    0.002052] ... max period:              000000007fffffff
[    0.002054] ... fixed-purpose counters:  3
[    0.002056] ... counter mask:            0000000700000003
[    0.002061] Checking 'hlt' instruction... OK.
[    0.019740] ACPI: Core revision 20090521
[    0.032341] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.072036] CPU0: Intel(R) Core(TM)2 Duo CPU     U9400  @ 1.40GHz stepping 06
[    0.076001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 2793.95 BogoMIPS (lpj=5587919)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 3072K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] mce: CPU supports 6 MCE banks
[    0.004000] CPU1: Thermal monitoring handled by SMI
[    0.004000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.162076] CPU1: Intel(R) Core(TM)2 Duo CPU     U9400  @ 1.40GHz stepping 06
[    0.162095] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.164024] Brought up 2 CPUs
[    0.164028] Total of 2 processors activated (5586.86 BogoMIPS).
[    0.164082] CPU0 attaching sched-domain:
[    0.164085]  domain 0: span 0-1 level MC
[    0.164089]   groups: 0 1
[    0.164096] CPU1 attaching sched-domain:
[    0.164099]  domain 0: span 0-1 level MC
[    0.164102]   groups: 1 0
[    0.164195] Booting paravirtualized kernel on bare hardware
[    0.164279] regulator: core version 0.5
[    0.164279] Time:  2:38:24  Date: 03/09/10
[    0.164279] NET: Registered protocol family 16
[    0.164279] EISA bus registered
[    0.164280] ACPI: bus type pci registered
[    0.164368] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
[    0.164372] PCI: Not using MMCONFIG.
[    0.186496] PCI: PCI BIOS revision 2.10 entry at 0xfd42e, last bus=5
[    0.186499] PCI: Using configuration type 1 for base access
[    0.187879] bio: create slab <bio-0> at 0
[    0.189247] ACPI: EC: Look up EC in DSDT
[    0.192601] ACPI Warning: Package List length (C) larger than NumElements count (4), truncated
[    0.192608]  20090521 dsobject-502
[    0.197180] ACPI: Interpreter enabled
[    0.197188] ACPI: (supports S0 S3 S4 S5)
[    0.197213] ACPI: Using IOAPIC for interrupt routing
[    0.197266] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
[    0.202428] PCI: MCFG area at f0000000 reserved in ACPI motherboard resources
[    0.202431] PCI: Using MMCONFIG for extended config space
[    0.211239] ACPI Warning: Incorrect checksum in table [ASF!] - ED, should be 83 20090521 tbutils-246
[    0.213041] ACPI: ACPI Dock Station Driver: 1 docks/bays found
[    0.213220] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.213340] pci 0000:00:02.0: reg 10 64bit mmio: [0xff400000-0xff7fffff]
[    0.213351] pci 0000:00:02.0: reg 18 64bit mmio: [0xe0000000-0xefffffff]
[    0.213358] pci 0000:00:02.0: reg 20 io port: [0xcff8-0xcfff]
[    0.213412] pci 0000:00:02.1: reg 10 64bit mmio: [0x000000-0x0fffff]
[    0.213764] pci 0000:00:03.0: reg 10 64bit mmio: [0xffcff000-0xffcff00f]
[    0.213809] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    0.213814] pci 0000:00:03.0: PME# disabled
[    0.213930] pci 0000:00:19.0: reg 10 32bit mmio: [0xffcc0000-0xffcdffff]
[    0.213941] pci 0000:00:19.0: reg 14 32bit mmio: [0xffcfe000-0xffcfefff]
[    0.213951] pci 0000:00:19.0: reg 18 io port: [0xcf80-0xcf9f]
[    0.214018] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.214023] pci 0000:00:19.0: PME# disabled
[    0.214104] pci 0000:00:1a.0: reg 20 io port: [0xcf60-0xcf7f]
[    0.214215] pci 0000:00:1a.1: reg 20 io port: [0xcf40-0xcf5f]
[    0.214325] pci 0000:00:1a.2: reg 20 io port: [0xcf20-0xcf3f]
[    0.214437] pci 0000:00:1a.7: reg 10 32bit mmio: [0xffcfd000-0xffcfd3ff]
[    0.214518] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.214525] pci 0000:00:1a.7: PME# disabled
[    0.214594] pci 0000:00:1b.0: reg 10 64bit mmio: [0x000000-0x003fff]
[    0.214666] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.214672] pci 0000:00:1b.0: PME# disabled
[    0.214774] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.214780] pci 0000:00:1c.0: PME# disabled
[    0.214890] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.214896] pci 0000:00:1c.3: PME# disabled
[    0.214993] pci 0000:00:1d.0: reg 20 io port: [0x9fe0-0x9fff]
[    0.215105] pci 0000:00:1d.1: reg 20 io port: [0x9f80-0x9f9f]
[    0.215217] pci 0000:00:1d.2: reg 20 io port: [0x9f60-0x9f7f]
[    0.215331] pci 0000:00:1d.7: reg 10 32bit mmio: [0xffcfc000-0xffcfc3ff]
[    0.215655] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.215662] pci 0000:00:1d.7: PME# disabled
[    0.215941] pci 0000:00:1f.2: reg 10 io port: [0x9f58-0x9f5f]
[    0.215951] pci 0000:00:1f.2: reg 14 io port: [0x9f54-0x9f57]
[    0.215961] pci 0000:00:1f.2: reg 18 io port: [0x9f48-0x9f4f]
[    0.215971] pci 0000:00:1f.2: reg 1c io port: [0x9f44-0x9f47]
[    0.215981] pci 0000:00:1f.2: reg 20 io port: [0x9f30-0x9f3f]
[    0.215991] pci 0000:00:1f.2: reg 24 io port: [0x9f20-0x9f2f]
[    0.216101] pci 0000:00:1f.5: reg 10 io port: [0x9f18-0x9f1f]
[    0.216111] pci 0000:00:1f.5: reg 14 io port: [0x9f14-0x9f17]
[    0.216122] pci 0000:00:1f.5: reg 18 io port: [0x9f08-0x9f0f]
[    0.216132] pci 0000:00:1f.5: reg 1c io port: [0x9f04-0x9f07]
[    0.216142] pci 0000:00:1f.5: reg 20 io port: [0x9ef0-0x9eff]
[    0.216152] pci 0000:00:1f.5: reg 24 io port: [0x9ee0-0x9eef]
[    0.216341] pci 0000:01:00.0: reg 10 64bit mmio: [0x000000-0x001fff]
[    0.216494] pci 0000:01:00.0: PME# supported from D0 D3hot D3cold
[    0.216506] pci 0000:01:00.0: PME# disabled
[    0.216623] pci 0000:00:1c.0: bridge io port: [0xb000-0xbfff]
[    0.216630] pci 0000:00:1c.0: bridge 32bit mmio: [0xff900000-0xff9fffff]
[    0.216640] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xff200000-0xff3fffff]
[    0.216714] pci 0000:00:1c.3: bridge io port: [0xa000-0xafff]
[    0.216721] pci 0000:00:1c.3: bridge 32bit mmio: [0xfcc00000-0xfebfffff]
[    0.216731] pci 0000:00:1c.3: bridge 64bit mmio pref: [0xfac00000-0xfcbfffff]
[    0.216809] pci 0000:04:0b.0: reg 10 32bit mmio: [0x000000-0x0000ff]
[    0.216882] pci 0000:04:0b.0: supports D1 D2
[    0.216885] pci 0000:04:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.216891] pci 0000:04:0b.0: PME# disabled
[    0.216958] pci 0000:00:1e.0: transparent bridge
[    0.216996] pci_bus 0000:00: on NUMA node 0
[    0.217002] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.217180] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.217314] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.MPEX._PRT]
[    0.217654] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXCB._PRT]
[    0.222759] ACPI: PCI Interrupt Link [LNKA] (IRQs *10)
[    0.222939] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *11)
[    0.223121] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *11)
[    0.223301] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *11)
[    0.223481] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *11)
[    0.223661] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *11)
[    0.223841] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *11)
[    0.224027] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *11)
[    0.224263] SCSI subsystem initialized
[    0.224288] libata version 3.00 loaded.
[    0.224288] usbcore: registered new interface driver usbfs
[    0.224288] usbcore: registered new interface driver hub
[    0.224288] usbcore: registered new device driver usb
[    0.224288] ACPI: WMI: Mapper loaded
[    0.224288] PCI: Using ACPI for IRQ routing
[    0.236010] Bluetooth: Core ver 2.15
[    0.236029] NET: Registered protocol family 31
[    0.236029] Bluetooth: HCI device and connection manager initialized
[    0.236029] Bluetooth: HCI socket layer initialized
[    0.236029] NetLabel: Initializing
[    0.236029] NetLabel:  domain hash size = 128
[    0.236029] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.236044] NetLabel:  unlabeled traffic allowed by default
[    0.236083] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.236091] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.256016] pnp: PnP ACPI init
[    0.256028] ACPI: bus type pnp registered
[    0.257624] pnp 00:00: mem resource (0x0-0x9ffff) overlaps 0000:00:02.1 BAR 0 (0x0-0xfffff), disabling
[    0.257630] pnp 00:00: mem resource (0xe8000-0xfffff) overlaps 0000:00:02.1 BAR 0 (0x0-0xfffff), disabling
[    0.262836] pnp: PnP ACPI: found 12 devices
[    0.262839] ACPI: ACPI bus type pnp unregistered
[    0.262843] PnPBIOS: Disabled by ACPI PNP
[    0.262857] system 00:00: iomem range 0x100000-0xb398ffff could not be reserved
[    0.262861] system 00:00: iomem range 0xb3990000-0xb399ffff has been reserved
[    0.262865] system 00:00: iomem range 0xb39a0000-0xb39a1fff could not be reserved
[    0.262869] system 00:00: iomem range 0xb39b0000-0xb3cfffff has been reserved
[    0.262873] system 00:00: iomem range 0xb3d00000-0xb3dfffff has been reserved
[    0.262877] system 00:00: iomem range 0xb3e00000-0xbbffffff has been reserved
[    0.262882] system 00:00: iomem range 0xfec00000-0xfec17fff could not be reserved
[    0.262886] system 00:00: iomem range 0xfec28000-0xfec2ffff has been reserved
[    0.262890] system 00:00: iomem range 0xfed00400-0xfed004ff has been reserved
[    0.262894] system 00:00: iomem range 0xfed10000-0xfed19fff has been reserved
[    0.262898] system 00:00: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.262902] system 00:00: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.262906] system 00:00: iomem range 0xfed45000-0xfed8ffff has been reserved
[    0.262910] system 00:00: iomem range 0xfed90000-0xfed93fff has been reserved
[    0.262914] system 00:00: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.262918] system 00:00: iomem range 0xffa00000-0xffbfffff has been reserved
[    0.262922] system 00:00: iomem range 0xffd00000-0xffffffff has been reserved
[    0.262930] system 00:01: iomem range 0xf0000000-0xf3ffffff has been reserved
[    0.262943] system 00:09: ioport range 0x1e0-0x1ef has been reserved
[    0.262947] system 00:09: ioport range 0x480-0x48f has been reserved
[    0.262951] system 00:09: ioport range 0xe000-0xe07f has been reserved
[    0.262955] system 00:09: ioport range 0xe080-0xe0ff has been reserved
[    0.262959] system 00:09: ioport range 0xe400-0xe47f has been reserved
[    0.262963] system 00:09: ioport range 0xe480-0xe4ff has been reserved
[    0.262966] system 00:09: ioport range 0xe800-0xe87f has been reserved
[    0.262971] system 00:09: ioport range 0xe880-0xe8ff has been reserved
[    0.262975] system 00:09: ioport range 0xec00-0xec7f has been reserved
[    0.262979] system 00:09: ioport range 0xec80-0xecff has been reserved
[    0.262982] system 00:09: ioport range 0xd800-0xd87f has been reserved
[    0.262986] system 00:09: ioport range 0xd880-0xd89f has been reserved
[    0.262990] system 00:09: ioport range 0xee80-0xeeff has been reserved
[    0.262994] system 00:09: ioport range 0x690-0x6ff has been reserved
[    0.263001] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[    0.297715] AppArmor: AppArmor Filesystem Enabled
[    0.297821] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
[    0.297826] pci 0000:00:1c.0:   IO window: 0xb000-0xbfff
[    0.297835] pci 0000:00:1c.0:   MEM window: 0xff900000-0xff9fffff
[    0.297842] pci 0000:00:1c.0:   PREFETCH window: 0x000000ff200000-0x000000ff3fffff
[    0.297851] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:02
[    0.297856] pci 0000:00:1c.3:   IO window: 0xa000-0xafff
[    0.297864] pci 0000:00:1c.3:   MEM window: 0xfcc00000-0xfebfffff
[    0.297870] pci 0000:00:1c.3:   PREFETCH window: 0x000000fac00000-0x000000fcbfffff
[    0.297884] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:04
[    0.297887] pci 0000:00:1e.0:   IO window: disabled
[    0.297895] pci 0000:00:1e.0:   MEM window: 0xbc100000-0xbc1fffff
[    0.297900] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.297917]   alloc irq_desc for 17 on node -1
[    0.297919]   alloc kstat_irqs on node -1
[    0.297926] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.297933] pci 0000:00:1c.0: setting latency timer to 64
[    0.297944]   alloc irq_desc for 19 on node -1
[    0.297946]   alloc kstat_irqs on node -1
[    0.297951] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.297958] pci 0000:00:1c.3: setting latency timer to 64
[    0.297968] pci 0000:00:1e.0: setting latency timer to 64
[    0.297974] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.297977] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.297981] pci_bus 0000:01: resource 0 io:  [0xb000-0xbfff]
[    0.297985] pci_bus 0000:01: resource 1 mem: [0xff900000-0xff9fffff]
[    0.297988] pci_bus 0000:01: resource 2 pref mem [0xff200000-0xff3fffff]
[    0.297992] pci_bus 0000:02: resource 0 io:  [0xa000-0xafff]
[    0.297996] pci_bus 0000:02: resource 1 mem: [0xfcc00000-0xfebfffff]
[    0.297999] pci_bus 0000:02: resource 2 pref mem [0xfac00000-0xfcbfffff]
[    0.298003] pci_bus 0000:04: resource 1 mem: [0xbc100000-0xbc1fffff]
[    0.298007] pci_bus 0000:04: resource 3 io:  [0x00-0xffff]
[    0.298010] pci_bus 0000:04: resource 4 mem: [0x000000-0xffffffff]
[    0.298051] NET: Registered protocol family 2
[    0.298170] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.298562] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.299082] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.299302] TCP: Hash tables configured (established 131072 bind 65536)
[    0.299305] TCP reno registered
[    0.299391] NET: Registered protocol family 1
[    0.299458] Trying to unpack rootfs image as initramfs...
[    0.502222] Switched to high resolution mode on CPU 1
[    0.504105] Switched to high resolution mode on CPU 0
[    0.589881] Freeing initrd memory: 8054k freed
[    0.594033] Simple Boot Flag value 0xb read from CMOS RAM was invalid
[    0.594037] Simple Boot Flag at 0x7c set to 0x1
[    0.594272] cpufreq-nforce2: No nForce2 chipset.
[    0.594308] Scanning for low memory corruption every 60 seconds
[    0.594449] audit: initializing netlink socket (disabled)
[    0.594469] type=2000 audit(1268102304.592:1): initialized
[    0.606783] highmem bounce pool size: 64 pages
[    0.606789] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.608861] VFS: Disk quotas dquot_6.5.2
[    0.608941] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.609704] fuse init (API version 7.12)
[    0.609817] msgmni has been set to 1684
[    0.610104] alg: No test for stdrng (krng)
[    0.610123] io scheduler noop registered
[    0.610126] io scheduler anticipatory registered
[    0.610129] io scheduler deadline registered
[    0.610186] io scheduler cfq registered (default)
[    0.610201] pci 0000:00:02.0: Boot video device
[    0.640197]   alloc irq_desc for 24 on node -1
[    0.640200]   alloc kstat_irqs on node -1
[    0.640215] pcieport-driver 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.640229] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.640402]   alloc irq_desc for 25 on node -1
[    0.640405]   alloc kstat_irqs on node -1
[    0.640416] pcieport-driver 0000:00:1c.3: irq 25 for MSI/MSI-X
[    0.640429] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    0.640561] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.640634] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.640815] ACPI: AC Adapter [ADP1] (on-line)
[    0.640891] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.640895] ACPI: Power Button [PWRF]
[    0.640981] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    0.641031] ACPI: Lid Switch [LID]
[    0.641090] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
[    0.641097] ACPI: Power Button [PWRB]
[    0.641672] ACPI: SSDT b3997287 000F3 (v02 TOSHIB A006B    20070720 MSFT 03000000)
[    0.642020] ACPI: SSDT b39973f0 0006C (v02 TOSHIB A006B    20070720 MSFT 03000000)
[    0.642527] Monitor-Mwait will be used to enter C-1 state
[    0.642562] Monitor-Mwait will be used to enter C-2 state
[    0.642593] Monitor-Mwait will be used to enter C-3 state
[    0.642604] Marking TSC unstable due to TSC halts in idle
[    0.642628] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    0.642662] processor LNXCPU:00: registered as cooling_device0
[    0.642987] ACPI: SSDT b399737a 00076 (v02 TOSHIB A006B    20060921 MSFT 03000000)
[    0.643330] ACPI: SSDT b399745c 00079 (v02 TOSHIB A006B    20070720 MSFT 03000000)
[    0.643919] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    0.643945] processor LNXCPU:01: registered as cooling_device1
[    0.647020] thermal LNXTHERM:01: registered as thermal_zone0
[    0.647032] ACPI: Thermal Zone [THRM] (61 C)
[    0.647107] isapnp: Scanning for PnP cards...
[    0.696860] ACPI Warning: \_SB_.BAT1._BIF: Return Package type mismatch at index 12 - found Integer, expected String/Buffer 20090521 nspredef-946
[    0.697437] ACPI: Battery Slot [BAT1] (battery present)
[    1.001215] isapnp: No Plug & Play device found
[    1.002737] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.004544] brd: module loaded
[    1.005151] loop: module loaded
[    1.005242] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.005385] ata_piix 0000:00:1f.2: version 2.13
[    1.005402] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.005410] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[    1.160048] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.160127] scsi0 : ata_piix
[    1.160236] scsi1 : ata_piix
[    1.160323] ata1: SATA max UDMA/133 cmd 0x9f58 ctl 0x9f54 bmdma 0x9f30 irq 19
[    1.160329] ata2: SATA max UDMA/133 cmd 0x9f48 ctl 0x9f44 bmdma 0x9f38 irq 19
[    1.160356]   alloc irq_desc for 21 on node -1
[    1.160359]   alloc kstat_irqs on node -1
[    1.160366] ata_piix 0000:00:1f.5: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.160375] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    1.316081] ata_piix 0000:00:1f.5: setting latency timer to 64
[    1.316147] scsi2 : ata_piix
[    1.316225] scsi3 : ata_piix
[    1.316297] ata3: SATA max UDMA/133 cmd 0x9f18 ctl 0x9f14 bmdma 0x9ef0 irq 21
[    1.316303] ata4: SATA max UDMA/133 cmd 0x9f08 ctl 0x9f04 bmdma 0x9ef8 irq 21
[    1.317489] Fixed MDIO Bus: probed
[    1.317537] PPP generic driver version 2.4.2
[    1.317644] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.317667] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    1.317681] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    1.317686] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    1.317723] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    1.321646] ehci_hcd 0000:00:1a.7: debug port 1
[    1.321655] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    1.321662] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xffcfd000
[    1.336026] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    1.336116] usb usb1: configuration #1 chosen from 1 choice
[    1.336156] hub 1-0:1.0: USB hub found
[    1.336165] hub 1-0:1.0: 6 ports detected
[    1.336237]   alloc irq_desc for 23 on node -1
[    1.336240]   alloc kstat_irqs on node -1
[    1.336247] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.336259] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.336264] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.336302] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    1.340231] ehci_hcd 0000:00:1d.7: debug port 1
[    1.340239] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.340256] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xffcfc000
[    1.356025] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.356116] usb usb2: configuration #1 chosen from 1 choice
[    1.356153] hub 2-0:1.0: USB hub found
[    1.356164] hub 2-0:1.0: 6 ports detected
[    1.356237] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.356261] uhci_hcd: USB Universal Host Controller Interface driver
[    1.356287]   alloc irq_desc for 16 on node -1
[    1.356289]   alloc kstat_irqs on node -1
[    1.356295] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.356304] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.356308] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.356346] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    1.356386] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000cf60
[    1.356488] usb usb3: configuration #1 chosen from 1 choice
[    1.356522] hub 3-0:1.0: USB hub found
[    1.356530] hub 3-0:1.0: 2 ports detected
[    1.356588] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.356597] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    1.356601] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.356644] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    1.356675] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000cf40
[    1.356782] usb usb4: configuration #1 chosen from 1 choice
[    1.356816] hub 4-0:1.0: USB hub found
[    1.356824] hub 4-0:1.0: 2 ports detected
[    1.356880] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    1.356888] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    1.356893] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    1.356932] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    1.356964] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000cf20
[    1.357061] usb usb5: configuration #1 chosen from 1 choice
[    1.357096] hub 5-0:1.0: USB hub found
[    1.357104] hub 5-0:1.0: 2 ports detected
[    1.357161] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.357169] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.357174] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.357214] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    1.357243] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00009fe0
[    1.357342] usb usb6: configuration #1 chosen from 1 choice
[    1.357377] hub 6-0:1.0: USB hub found
[    1.357385] hub 6-0:1.0: 2 ports detected
[    1.357444] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.357453] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.357457] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.357496] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    1.357527] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00009f80
[    1.357627] usb usb7: configuration #1 chosen from 1 choice
[    1.357662] hub 7-0:1.0: USB hub found
[    1.357670] hub 7-0:1.0: 2 ports detected
[    1.357726]   alloc irq_desc for 18 on node -1
[    1.357729]   alloc kstat_irqs on node -1
[    1.357735] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.357743] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.357747] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.357785] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    1.357825] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00009f60
[    1.357925] usb usb8: configuration #1 chosen from 1 choice
[    1.357960] hub 8-0:1.0: USB hub found
[    1.357967] hub 8-0:1.0: 2 ports detected
[    1.358096] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.363665] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.363672] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.363743] mice: PS/2 mouse device common for all mice
[    1.364141] rtc_cmos 00:08: RTC can wake from S4
[    1.364180] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    1.364214] rtc0: alarms up to one year, 114 bytes nvram, hpet irqs
[    1.364344] device-mapper: uevent: version 1.0.3
[    1.364468] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.364570] device-mapper: multipath: version 1.1.0 loaded
[    1.364574] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.364723] EISA: Probing bus 0 at eisa.0
[    1.364763] EISA: Detected 0 cards.
[    1.364965] cpuidle: using governor ladder
[    1.365138] cpuidle: using governor menu
[    1.366050] TCP cubic registered
[    1.366517] NET: Registered protocol family 10
[    1.367118] lo: Disabled Privacy Extensions
[    1.367578] NET: Registered protocol family 17
[    1.367602] Bluetooth: L2CAP ver 2.13
[    1.367604] Bluetooth: L2CAP socket layer initialized
[    1.367608] Bluetooth: SCO (Voice Link) ver 0.6
[    1.367611] Bluetooth: SCO socket layer initialized
[    1.367653] Bluetooth: RFCOMM TTY layer initialized
[    1.367657] Bluetooth: RFCOMM socket layer initialized
[    1.367660] Bluetooth: RFCOMM ver 1.11
[    1.367992] Using IPI No-Shortcut mode
[    1.368068] PM: Resume from disk failed.
[    1.368082] registered taskstats version 1
[    1.368228]   Magic number: 2:446:611
[    1.368305] rtc_cmos 00:08: setting system clock to 2010-03-09 02:38:25 UTC (1268102305)
[    1.368310] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.368312] EDD information not available.
[    1.379120] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.491327] ata2: SATA link down (SStatus 4 SControl 300)
[    1.500088] Clocksource tsc unstable (delta = -109483049 ns)
[    1.637150] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.655306] ata3: SATA link down (SStatus 0 SControl 300)
[    1.666535] ata4: SATA link down (SStatus 4 SControl 300)
[    1.667064] ata1.00: ATA-7: INTEL SSDSA2MH160G1GC, 045C8790, max UDMA/133
[    1.667068] ata1.00: 312581808 sectors, multi 1: LBA48 NCQ (depth 0/31)
[    1.672480] ata1.00: configured for UDMA/133
[    1.672638] scsi 0:0:0:0: Direct-Access     ATA      INTEL SSDSA2MH16 045C PQ: 0 ANSI: 5
[    1.672782] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.672831] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.672893] sd 0:0:0:0: [sda] Write Protect is off
[    1.672897] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.672929] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.673090]  sda: sda1 sda2 < sda5 >
[    1.674066] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.674118] Freeing unused kernel memory: 540k freed
[    1.674487] Write protecting the kernel text: 4580k
[    1.674551] Write protecting the kernel read-only data: 1840k
[    1.720061] usb 1-4: new high speed USB device using ehci_hcd and address 3
[    1.869721] Linux agpgart interface v0.103
[    1.875191] agpgart-intel 0000:00:00.0: Intel Mobile Intel® GM45 Express Chipset
[    1.876718] agpgart-intel 0000:00:00.0: detected 131068K stolen memory
[    1.889651] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k2
[    1.889657] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    1.897719] usb 1-4: configuration #1 chosen from 2 choices
[    1.903865] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[    1.936080]   alloc irq_desc for 20 on node -1
[    1.936087]   alloc kstat_irqs on node -1
[    1.936100] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.936113] e1000e 0000:00:19.0: pci_enable_pcie_error_reporting failed 0xfffffffb
[    1.936121] e1000e 0000:00:19.0: setting latency timer to 64
[    1.936294]   alloc irq_desc for 26 on node -1
[    1.936299]   alloc kstat_irqs on node -1
[    1.936321] e1000e 0000:00:19.0: irq 26 for MSI/MSI-X
[    2.042245] [drm] Initialized drm 1.1.0 20060810
[    2.084064] usb 2-2: new high speed USB device using ehci_hcd and address 2
[    2.090264] 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:1c:7e:db:1c:b2
[    2.090268] 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    2.090309] 0000:00:19.0: eth0: MAC: 7, PHY: 8, PBA No: ffffff-0ff
[    2.091341] i915 0000:00:02.0: power state changed by ACPI to D0
[    2.091357] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.091367] i915 0000:00:02.0: setting latency timer to 64
[    2.095209]   alloc irq_desc for 27 on node -1
[    2.095216]   alloc kstat_irqs on node -1
[    2.095231] i915 0000:00:02.0: irq 27 for MSI/MSI-X
[    2.157052] i2c-adapter i2c-1: unable to read EDID block.
[    2.157058] i915 0000:00:02.0: LVDS-1: no EDID data
[    2.443976] usb 2-2: configuration #1 chosen from 1 choice
[    2.569054] i2c-adapter i2c-1: unable to read EDID block.
[    2.569060] i915 0000:00:02.0: LVDS-1: no EDID data
[    2.591961] [drm] fb0: inteldrmfb frame buffer device
[    2.595311] acpi device:08: registered as cooling_device2
[    2.595602] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:07/input/input5
[    2.595654] ACPI: Video Device [VGA] (multi-head: yes  rom: yes  post: no)
[    2.595692] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    2.596034] usb 2-3: new high speed USB device using ehci_hcd and address 3
[    2.686333] [drm] LVDS-8: set mode 1280x800 f
[    2.752978] usb 2-3: configuration #1 chosen from 1 choice
[    2.766589] Initializing USB Mass Storage driver...
[    3.008232] scsi4 : SCSI emulation for USB Mass Storage devices
[    3.008480] usbcore: registered new interface driver usb-storage
[    3.008483] USB Mass Storage support registered.
[    3.008652] usb-storage: device found at 3
[    3.008656] usb-storage: waiting for device to settle before scanning
[    3.108057] usb 4-1: new low speed USB device using uhci_hcd and address 2
[    3.294856] usb 4-1: configuration #1 chosen from 1 choice
[    3.307560] usbcore: registered new interface driver hiddev
[    3.322112] input: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/input/input6
[    3.322247] generic-usb 0003:045E:0039.0001: input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0000:00:1a.1-1/input0
[    3.322274] usbcore: registered new interface driver usbhid
[    3.322277] usbhid: v2.6:USB HID core driver
[    3.540056] usb 7-2: new full speed USB device using uhci_hcd and address 2
[    3.710668] Console: switching to colour frame buffer device 160x50
[    3.714497] usb 7-2: configuration #1 chosen from 1 choice
[    3.923863] xor: automatically using best checksumming function: pIII_sse
[    3.941036]    pIII_sse  :  4205.000 MB/sec
[    3.941039] xor: using function: pIII_sse (4205.000 MB/sec)
[    3.945313] device-mapper: dm-raid45: initialized v0.2594b
[    4.230544] EXT4-fs (sda5): barriers enabled
[    4.232540] kjournald2 starting: pid 429, dev sda5:8, commit interval 5 seconds
[    4.232704] EXT4-fs (sda5): delayed allocation enabled
[    4.232711] EXT4-fs: file extents enabled
[    4.251384] EXT4-fs: mballoc enabled
[    4.251406] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    4.382045] type=1505 audit(1268102308.512:2): operation="profile_load" pid=458 name=/sbin/dhclient3
[    4.383508] type=1505 audit(1268102308.512:3): operation="profile_load" pid=458 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    4.384299] type=1505 audit(1268102308.512:4): operation="profile_load" pid=458 name=/usr/lib/connman/scripts/dhclient-script
[    4.391684] type=1505 audit(1268102308.520:5): operation="profile_load" pid=460 name=/usr/lib/cups/backend/cups-pdf
[    4.393260] type=1505 audit(1268102308.524:6): operation="profile_load" pid=460 name=/usr/sbin/cupsd
[    4.399938] type=1505 audit(1268102308.528:7): operation="profile_load" pid=461 name=/usr/sbin/mysqld-akonadi
[    4.403530] type=1505 audit(1268102308.532:8): operation="profile_load" pid=462 name=/usr/sbin/tcpdump
[    4.677554] EXT4-fs (sda5): internal journal on sda5:8
[    4.691674] udev: starting version 147
[    4.798697] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.19-dev-acpikeys
[    4.798704] toshiba_acpi:     HCI method: \_SB_.VALZ.GHCI
[    4.799852] toshiba_acpi: Toshiba hotkeys are sent as ACPI events
[    4.799856] toshiba_acpi: ktoshkeyd will check 2 times per second
[    4.827719] heci: module is from the staging directory, the quality is unknown, you have been warned.
[    4.830329] heci: Intel(R) Management Engine Interface - version 5.0.0.31
[    4.830332] heci: Copyright (c) 2003 - 2008 Intel Corporation.
[    4.830387] heci 0000:00:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.830398] heci 0000:00:03.0: setting latency timer to 64
[    4.833521] heci: link layer has been established.
[    4.850735] toshiba_acpi: Dropped 0 keys from the queue on startup
[    4.952871] lp: driver loaded but no devices found
[    4.989320] heci driver initialization successful.
[    5.018303] sdhci: Secure Digital Host Controller Interface driver
[    5.018309] sdhci: Copyright(c) Pierre Ossman
[    5.020854] sdhci-pci 0000:04:0b.0: SDHCI controller found [1180:0822] (rev 22)
[    5.020883] sdhci-pci 0000:04:0b.0: enabling device (0000 -> 0002)
[    5.020897] sdhci-pci 0000:04:0b.0: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    5.021941] sdhci-pci 0000:04:0b.0: Will use DMA mode even though HW doesn't fully claim to support it.
[    5.023158] Registered led device: mmc0::
[    5.024216] mmc0: SDHCI controller on PCI [0000:04:0b.0] using DMA
[    5.032317] cdc_wdm 1-4:1.5: cdc-wdm0: USB WDM device
[    5.032373] cdc_wdm 1-4:1.6: cdc-wdm1: USB WDM device
[    5.032412] usbcore: registered new interface driver cdc_wdm
[    5.038971] cdc_acm 1-4:1.1: ttyACM0: USB ACM device
[    5.097390] cdc_acm 1-4:1.3: ttyACM1: USB ACM device
[    5.098784] cdc_acm 1-4:1.9: ttyACM2: USB ACM device
[    5.099884] usbcore: registered new interface driver cdc_acm
[    5.099891] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
[    5.132848] usb0: register 'cdc_ether' at usb-0000:00:1a.7-4, CDC Ethernet Device, 02:80:37:ec:02:00
[    5.132904] usbcore: registered new interface driver cdc_ether
[    5.133132] cfg80211: Calling CRDA to update world regulatory domain
[    5.133516] tpm_inf_pnp 00:0a: Found TPM with ID IFX0102
[    5.133589] tpm_inf_pnp 00:0a: TPM found: config base 0x4e, data base 0x680, chip version 0x000b, vendor id 0x15d1 (Infineon), product id 0x000b (SLB 9635 TT 1.2)
[    5.184651] Linux video capture interface: v2.00
[    5.191129] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (04f2:b120)
[    5.205851] cfg80211: World regulatory domain updated:
[    5.205857] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    5.205864] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.205867] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    5.205873] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    5.205879] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.205884] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.216470] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb2/2-2/2-2:1.0/input/input7
[    5.216564] usbcore: registered new interface driver uvcvideo
[    5.216570] USB Video Class driver (v0.1.0)
[    5.233320] usbcore: registered new interface driver zaurus
[    5.392043] usb 3-2: new full speed USB device using uhci_hcd and address 2
[    5.477446] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[    5.477454] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[    5.477611] iwlagn 0000:01:00.0: enabling device (0000 -> 0002)
[    5.477652] iwlagn 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.477702] iwlagn 0000:01:00.0: setting latency timer to 64
[    5.477900] iwlagn 0000:01:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[    5.569378] e1000e 0000:00:19.0: irq 26 for MSI/MSI-X
[    5.570314] ip_tables: (C) 2000-2006 Netfilter Core Team
[    5.592247] usb 3-2: configuration #1 chosen from 1 choice
[    5.603222] iwlagn 0000:01:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[    5.603317]   alloc irq_desc for 28 on node -1
[    5.603322]   alloc kstat_irqs on node -1
[    5.603353] iwlagn 0000:01:00.0: irq 28 for MSI/MSI-X
[    5.626290] e1000e 0000:00:19.0: irq 26 for MSI/MSI-X
[    5.626822] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    5.678004] Bluetooth: Generic Bluetooth USB driver ver 0.5
[    5.678251] usbcore: registered new interface driver btusb
[    5.722148] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    5.722154] Bluetooth: BNEP filters: protocol multicast
[    5.737146] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input8
[    5.813569] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input9
[    5.832806] Bridge firewalling registered
[    5.926054] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[    5.926070] HDA Intel 0000:00:1b.0: enabling device (0000 -> 0002)
[    5.926084]   alloc irq_desc for 22 on node -1
[    5.926089]   alloc kstat_irqs on node -1
[    5.926100] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    5.926167] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    5.943967] phy0: Selected rate control algorithm 'iwl-agn-rs'
[    5.976449] iwlagn 0000:01:00.0: firmware: requesting iwlwifi-5000-2.ucode
[    6.044961] iwlagn 0000:01:00.0: loaded firmware version 8.24.2.12
[    6.079087] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input10
[    6.150559] type=1505 audit(1268098710.280:9): operation="profile_replace" pid=1101 name=/sbin/dhclient3
[    6.152180] type=1505 audit(1268098710.280:10): operation="profile_replace" pid=1101 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    6.152983] type=1505 audit(1268098710.280:11): operation="profile_replace" pid=1101 name=/usr/lib/connman/scripts/dhclient-script
[    6.166998] type=1505 audit(1268098710.296:12): operation="profile_replace" pid=1103 name=/usr/lib/cups/backend/cups-pdf
[    6.168960] type=1505 audit(1268098710.296:13): operation="profile_replace" pid=1103 name=/usr/sbin/cupsd
[    6.175687] type=1505 audit(1268098710.304:14): operation="profile_replace" pid=1104 name=/usr/sbin/mysqld-akonadi
[    6.179218] type=1505 audit(1268098710.308:15): operation="profile_replace" pid=1105 name=/usr/sbin/tcpdump
[    6.231242] Registered led device: iwl-phy0::radio
[    6.231280] Registered led device: iwl-phy0::assoc
[    6.231316] Registered led device: iwl-phy0::RX
[    6.231346] Registered led device: iwl-phy0::TX
[    6.248885] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    6.513055] i2c-adapter i2c-1: unable to read EDID block.
[    6.513066] i915 0000:00:02.0: LVDS-1: no EDID data
[    6.649052] i2c-adapter i2c-1: unable to read EDID block.
[    6.649061] i915 0000:00:02.0: LVDS-1: no EDID data
[    7.068380] ppdev: user-space parallel port driver
[    8.010041] usb-storage: device scan complete
[    8.011793] scsi 4:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-844S  1.11 PQ: 0 ANSI: 0
[    8.025740] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    8.025750] Uniform CD-ROM driver Revision: 3.20
[    8.025964] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    8.026089] sr 4:0:0:0: Attached scsi generic sg1 type 5
[   45.824029] i2c-adapter i2c-1: unable to read EDID block.
[   45.824035] i915 0000:00:02.0: LVDS-1: no EDID data
[  205.370353] wlan0: authenticate with AP 00:24:01:f4:70:b0
[  205.372463] wlan0: authenticated
[  205.372469] wlan0: associate with AP 00:24:01:f4:70:b0
[  205.376088] wlan0: RX AssocResp from 00:24:01:f4:70:b0 (capab=0x431 status=0 aid=1)
[  205.376096] wlan0: associated
[  205.378717] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  205.391280] padlock: VIA PadLock not detected.
[  212.340695] tun: Universal TUN/TAP device driver, 1.6
[  212.340700] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[  212.342332] tun0: Disabled Privacy Extensions
[  215.940257] wlan0: no IPv6 routers present
[  268.926892] iwlagn 0000:01:00.0: iwl_tx_agg_start on ra = 00:24:01:f4:70:b0 tid = 0
[  359.829383] tun1: Disabled Privacy Extensions

```
After failed hibernation, the following part is added:
```
[  428.773205] wlan0: deauthenticating by local choice (reason=3)
[  428.848801] wlan0: disassociating by local choice (reason=3)
[  428.963841] PM: Marking nosave pages: 0000000000002000 - 0000000000006000
[  428.963846] PM: Marking nosave pages: 000000000009f000 - 0000000000100000
[  428.963852] PM: Basic memory bitmaps created
[  428.963854] PM: Syncing filesystems ... done.
[  428.967541] Freezing user space processes ... (elapsed 0.00 seconds) done.
[  428.968533] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[  428.968602] PM: Shrinking memory...  -
[  429.321926] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[  429.588705] \|/-\|done (59024 pages freed)
[  434.130270] PM: Freed 236096 kbytes in 5.16 seconds (45.75 MB/s)
[  434.130273] Suspending console(s) (use no_console_suspend to debug)
[  434.154145] btusb_bulk_complete: hci0 urb f6955b80 failed to resubmit (1)
[  434.155137] btusb_bulk_complete: hci0 urb f6955b00 failed to resubmit (1)
[  434.156132] btusb_intr_complete: hci0 urb f6955a80 failed to resubmit (1)
[  434.157884] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[  434.161608] sdhci-pci 0000:04:0b.0: PME# disabled
[  434.161618] sdhci-pci 0000:04:0b.0: PCI INT B disabled
[  434.192288] ata_piix 0000:00:1f.5: PCI INT A disabled
[  434.192558] ata_piix 0000:00:1f.2: PCI INT B disabled
[  434.296232] HDA Intel 0000:00:1b.0: PCI INT A disabled
[  434.312206] HDA Intel 0000:00:1b.0: power state changed by ACPI to D3
[  434.312416] e1000e 0000:00:19.0: PCI INT A disabled
[  434.312422] e1000e 0000:00:19.0: PME# enabled
[  434.312466] e1000e 0000:00:19.0: wake-up capability enabled by ACPI
[  434.329079] heci 0000:00:03.0: PCI INT A disabled
[  434.387728] ACPI: Preparing to enter system sleep state S4
[  434.388248] PM: Saving platform NVS memory
[  434.388581] Disabling non-boot CPUs ...
[  434.390793] CPU 1 is now offline
[  434.390796] SMP alternatives: switching to UP code
[  434.399886] CPU0 attaching NULL sched-domain.
[  434.399892] CPU1 attaching NULL sched-domain.
[  434.399899] CPU0 attaching NULL sched-domain.
[  434.400142] CPU1 is down
[  434.400281] PM: Creating hibernation image: 
[  434.404007] PM: Need to copy 126154 pages
[  434.404007] PM: Normal pages needed: 18863 + 1024 + 54, available pages: 208361
[  434.404007] PM: Hibernation image created (126154 pages copied)
[  434.404007] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[  434.404007] CPU0: Thermal monitoring handled by SMI
[  434.404007] Enabling non-boot CPUs ...
[  434.404007] SMP alternatives: switching to SMP code
[  434.409199] Booting processor 1 APIC 0x1 ip 0x6000
[  434.399720] Initializing CPU#1
[  434.464911] Calibrating delay using timer specific routine.. 2468.37 BogoMIPS (lpj=4936740)
[  434.464911] CPU: L1 I cache: 32K, L1 D cache: 32K
[  434.464911] CPU: L2 cache: 3072K
[  434.464911] CPU: Physical Processor ID: 0
[  434.464911] CPU: Processor Core ID: 1
[  434.464911] mce: CPU supports 6 MCE banks
[  434.464911] CPU1: Thermal monitoring handled by SMI
[  434.464911] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[  434.502140] CPU1: Intel(R) Core(TM)2 Duo CPU     U9400  @ 1.40GHz stepping 06
[  434.502231] CPU0 attaching NULL sched-domain.
[  434.504021] Switched to high resolution mode on CPU 1
[  434.516028] CPU0 attaching sched-domain:
[  434.516031]  domain 0: span 0-1 level MC
[  434.516034]   groups: 0 1
[  434.516040] CPU1 attaching sched-domain:
[  434.516042]  domain 0: span 0-1 level MC
[  434.516045]   groups: 1 0
[  434.517021] CPU1 is up
[  434.517038] ACPI: Waking up from system sleep state S4
[  434.526414] i915 0000:00:02.0: setting latency timer to 64
[  434.605023] [drm] LVDS-8: set mode 1280x800 f
[  435.608143] heci 0000:00:03.0: restoring config space at offset 0x1 (was 0x180002, writing 0x100006)
[  435.624144] e1000e 0000:00:19.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[  435.624179] e1000e 0000:00:19.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[  435.624219] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[  435.624225] e1000e 0000:00:19.0: setting latency timer to 64
[  435.624230] e1000e 0000:00:19.0: wake-up capability disabled by ACPI
[  435.624236] e1000e 0000:00:19.0: PME# disabled
[  435.624238] e1000e 0000:00:19.0: wake-up capability disabled by ACPI
[  435.624244] e1000e 0000:00:19.0: PME# disabled
[  435.624290] e1000e 0000:00:19.0: irq 26 for MSI/MSI-X
[  435.675132] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[  435.688180] HDA Intel 0000:00:1b.0: restoring config space at offset 0xf (was 0x100, writing 0x1ff)
[  435.688204] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x8)
[  435.688212] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100002)
[  435.688234] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[  435.688242] HDA Intel 0000:00:1b.0: setting latency timer to 64
[  435.790578] pci 0000:00:1e.0: setting latency timer to 64
[  435.790633] ata_piix 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00003, writing 0x2b00007)
[  435.790658] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[  435.790669] ata_piix 0000:00:1f.2: setting latency timer to 64
[  435.790733] ata_piix 0000:00:1f.5: restoring config space at offset 0x1 (was 0x2b00003, writing 0x2b00007)
[  435.790757] ata_piix 0000:00:1f.5: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[  435.790765] ata_piix 0000:00:1f.5: setting latency timer to 64
[  435.804160] iwlagn 0000:01:00.0: enabling device (0000 -> 0002)
[  435.804246] iwlagn 0000:01:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[  435.804312] iwlagn 0000:01:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100006)
[  435.820150] sdhci-pci 0000:04:0b.0: restoring config space at offset 0x3 (was 0x800000, writing 0x804008)
[  435.820160] sdhci-pci 0000:04:0b.0: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100006)
[  435.820184] sdhci-pci 0000:04:0b.0: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[  435.820187] sdhci-pci 0000:04:0b.0: Will use DMA mode even though HW doesn't fully claim to support it.
[  436.093833] sd 0:0:0:0: [sda] Starting disk
[  436.120403] ata2: SATA link down (SStatus 4 SControl 300)
[  436.131630] ata3: SATA link down (SStatus 0 SControl 300)
[  436.142927] ata4: SATA link down (SStatus 4 SControl 300)
[  436.285249] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  436.300505] ata1.00: configured for UDMA/133
[  436.309537] PM: writing image.
[  436.309540] PM: Cannot find swap device, try swapon -a.
[  436.358857] Restarting tasks ... done.
[  436.368324] PM: Basic memory bitmaps freed
[  437.100347] e1000e 0000:00:19.0: irq 26 for MSI/MSI-X
[  437.156212] e1000e 0000:00:19.0: irq 26 for MSI/MSI-X
[  437.157623] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  437.196495] Registered led device: iwl-phy0::radio
[  437.196521] Registered led device: iwl-phy0::assoc
[  437.196545] Registered led device: iwl-phy0::RX
[  437.196569] Registered led device: iwl-phy0::TX
[  437.237898] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  437.343465] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input11
[  437.370599] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input12

```

---

### Post by rogue_0111 on 2010-03-08
Sounds like a bug. Revert back to the old kernel and try again in a week:)

---

### Post by P3t3r on 2010-03-09
> **rogue_0111 said:**
> Sounds like a bug.Should I report the bug, and if so, where should I do that? Not through the KDE Crash Handler, I assume?

> **rogue_0111 said:**
> Revert back to the old kernelIs there any better way than just reinstalling everything (takes *much* time)? Just booting the old kernel does not change anything, it also autoresumes.

> **rogue_0111 said:**
> and try again in a weekUmm... now I'm not following. How will this help?

---

### Post by rogue_0111 on 2010-03-09
To report the issue:[I]

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)
[/I]
also read[I], [http://www.ubuntu.com/community/ReportProblem](http://www.ubuntu.com/community/ReportProblem)


[/I]Or hit up someone on the Laptop test team, they may be of further assistance:

[https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaPortegeR600](https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaPortegeR600)

---

### Post by rogue_0111 on 2010-03-09
This link may also be related???

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/501752](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/501752)

---

### Post by rogue_0111 on 2010-03-09
Just found this:

[http://webapps.ubuntu.com/certification/hardware/200810-884/](http://webapps.ubuntu.com/certification/hardware/200810-884/)

---

### Post by P3t3r on 2010-03-12
> **rogue_0111 said:**
> hit up someone on the Laptop test team, they may be of further assistance:

[https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaPortegeR600](https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaPortegeR600)I get "This page does not exist yet. You can create a new empty page, or use one of the page templates."... there is an old page though, but it seems quite outdated.

> **rogue_0111 said:**
> This link may also be related???

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/501752](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/501752)That is my page. :)
I thought the problem was caused by my unrecognized harddisk, but now with my working disk it's the same, so now I'm very certain it's a software problem.

> **rogue_0111 said:**
> Just found this:
[http://webapps.ubuntu.com/certification/hardware/200810-884/](http://webapps.ubuntu.com/certification/hardware/200810-884/)That is very useful! Now my pm-suspend works. But pm-hibernate doesn't work either: it auto-resumes now even faster and without locking the screen.

---

### Post by P3t3r on 2010-03-13
> **rogue_0111 said:**
> To report the issue:[I]

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)
[/I]
also read[I], [http://www.ubuntu.com/community/ReportProblem](http://www.ubuntu.com/community/ReportProblem)

Reporting the bug also fails, I keep getting "Cannot connect to crash database, please check your Internet connection". My internet connection works perfect though.

Don't know if it could indicate something related, but I now reported it manually through LaunchPad.

---

### Post by P3t3r on 2010-03-24
> **P3t3r said:**
> That is very useful! Now my pm-suspend works. But pm-hibernate doesn't work either: it auto-resumes now even faster and without locking the screen.I don't know how or why but apparently my pm-suspend doesn't always work either. 

So far also not a single reply on the bug report, but I wait patiently.

---

