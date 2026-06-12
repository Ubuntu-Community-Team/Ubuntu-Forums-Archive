---
title: "100% CPU after resume from suspend"
date: 2009-11-23
forum: Hardware
---

### Post by darkrv on 2009-11-23
Hello i have a laptop packard bell SB 87.  When my laptop suspend or go hibernate, i have a strange behavior from one of my cpu. One of the  cpu is using 100% ( i have a dual core) and is used by ksoftirqd/0. I updated to kernel 2.6.31-15 ( ubuntu karmic koala) today and still the same problem. Is there a fix?? Thx in advance!

my dsmeg output is > 
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-15-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #50-Ubuntu SMP Tue Nov 10 14:54:29 UTC 2009 (Ubuntu 2.6.31-15.50-generic)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007f6d0000 (usable)
[    0.000000]  BIOS-e820: 000000007f6d0000 - 000000007f6e3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007f6e3000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x7f6d0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 07F700000 mask FFFF00000 uncachable
[    0.000000]   2 base 07F800000 mask FFF800000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007f6d0000 (usable)
[    0.000000]  modified: 000000007f6d0000 - 000000007f6e3000 (ACPI NVS)
[    0.000000]  modified: 000000007f6e3000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
[    0.000000] RAMDISK: 3786a000 - 37feff9a
[    0.000000] Allocated new RAMDISK: 008ad000 - 01032f9a
[    0.000000] Move RAMDISK from 000000003786a000 - 0000000037feff99 to 008ad000 - 01032f99
[    0.000000] ACPI: RSDP 000f7e10 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT 7f6d9e3a 00094 (v01 PacBel PBNB0017 06040000  LTP 00000000)
[    0.000000] ACPI: FACP 7f6e1bd2 000F4 (v03 INTEL  CRESTLNE 06040000 ALAN 00000001)
[    0.000000] ACPI: DSDT 7f6dbd90 05DCE (v02 INTEL  CRESTLNE 06040000 MSFT 0100000E)
[    0.000000] ACPI: FACS 7f6e2fc0 00040
[    0.000000] ACPI: APIC 7f6e1cc6 00068 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: HPET 7f6e1d2e 00038 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG 7f6e1d66 0003C (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: TCPA 7f6e1da2 00032 (v01 Intel   CRESTLN 06040000      00005A52)
[    0.000000] ACPI: TMOR 7f6e1dd4 00026 (v01 PTLTD           06040000 PTL  00000003)
[    0.000000] ACPI: APIC 7f6e1dfa 00068 (v01 PTLTD       APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT 7f6e1e62 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SLIC 7f6e1e8a 00176 (v01 PacBel PBNB0017 06040000  LTP 00000000)
[    0.000000] ACPI: SSDT 7f6db741 0064F (v01 SataRe  SataPri 00001000 INTL 20050624)
[    0.000000] ACPI: SSDT 7f6db0af 00692 (v01 SataRe  SataSec 00001000 INTL 20050624)
[    0.000000] ACPI: SSDT 7f6da45a 0025F (v01  PmRef  Cpu0Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 7f6da3b4 000A6 (v01  PmRef  Cpu1Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 7f6d9ece 004E6 (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify [EMAIL="linux-acpi@vger.kernel.org"]linux-acpi@vger.kernel.org[/EMAIL]
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1150MB HIGHMEM available.
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
[    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #5 [00008a9000 - 00008ac1c4]              BRK ==> [00008a9000 - 00008ac1c4]
[    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #7 [00008ad000 - 0001032f9a]      NEW RAMDISK ==> [00008ad000 - 0001032f9a]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00f7e40] f7e40
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007f6d0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007f6d0
[    0.000000] On node 0 totalpages: 521823
[    0.000000] free_area_init_node: node 0, pgdat c0784940, node_mem_map c1033200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2302 pages used for memmap
[    0.000000]   HighMem zone: 292308 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
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
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:60000000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c202d000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517745
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-15-generic root=UUID=466fb2c0-6da0-4f6c-bda3-704f7c2f8292 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10438400 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007f6d0)
[    0.000000] Memory: 2043324k/2087744k available (4566k kernel code, 43044k reserved, 2142k data, 540k init, 1178440k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
[    0.000000]       .data : 0xc0575b44 - 0xc078d3c8   (2142 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0575b44   (4566 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Extended CMOS year: 2000
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1994.736 MHz processor.
[    0.002728] Console: colour VGA+ 80x25
[    0.002736] console [tty0] enabled
[    0.002966] hpet clockevent registered
[    0.002973] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.002984] Calibrating delay loop (skipped), value calculated using timer frequency.. 3989.47 BogoMIPS (lpj=7978944)
[    0.003023] Security Framework initialized
[    0.003065] AppArmor: AppArmor initialized
[    0.003080] Mount-cache hash table entries: 512
[    0.003355] Initializing cgroup subsys ns
[    0.003366] Initializing cgroup subsys cpuacct
[    0.003376] Initializing cgroup subsys memory
[    0.003391] Initializing cgroup subsys freezer
[    0.003396] Initializing cgroup subsys net_cls
[    0.003424] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.003431] CPU: L2 cache: 4096K
[    0.003437] CPU: Physical Processor ID: 0
[    0.003441] CPU: Processor Core ID: 0
[    0.003452] mce: CPU supports 6 MCE banks
[    0.003470] CPU0: Thermal monitoring enabled (TM2)
[    0.003477] using mwait in idle threads.
[    0.003491] Performance Counters: Core2 events, Intel PMU driver.
[    0.003511] ... version:                 2
[    0.003515] ... bit width:               40
[    0.003519] ... generic counters:        2
[    0.003523] ... value mask:              000000ffffffffff
[    0.003528] ... max period:              000000007fffffff
[    0.003533] ... fixed-purpose counters:  3
[    0.003537] ... counter mask:            0000000700000003
[    0.003546] Checking 'hlt' instruction... OK.
[    0.020007] ACPI: Core revision 20090521
[    0.040530] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.081248] CPU0: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz stepping 0a
[    0.084001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3990.05 BogoMIPS (lpj=7980110)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] mce: CPU supports 6 MCE banks
[    0.004000] CPU1: Thermal monitoring enabled (TM2)
[    0.004000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.175212] CPU1: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz stepping 0a
[    0.175242] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.176039] Brought up 2 CPUs
[    0.176045] Total of 2 processors activated (7979.52 BogoMIPS).
[    0.176117] CPU0 attaching sched-domain:
[    0.176124]  domain 0: span 0-1 level MC
[    0.176130]   groups: 0 1
[    0.176143] CPU1 attaching sched-domain:
[    0.176149]  domain 0: span 0-1 level MC
[    0.176155]   groups: 1 0
[    0.180024] Booting paravirtualized kernel on bare hardware
[    0.180470] regulator: core version 0.5
[    0.180470] Time: 14:11:23  Date: 11/23/09
[    0.180470] NET: Registered protocol family 16
[    0.180470] EISA bus registered
[    0.180488] ACPI: bus type pci registered
[    0.180644] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.180651] PCI: MCFG area at e0000000 reserved in E820
[    0.180656] PCI: Using MMCONFIG for extended config space
[    0.180661] PCI: Using configuration type 1 for base access
[    0.183199] bio: create slab <bio-0> at 0
[    0.185896] ACPI: EC: Look up EC in DSDT
[    0.191371] ACPI: BIOS _OSI(Linux) query ignored
[    0.192869] ACPI: Interpreter enabled
[    0.192886] ACPI: (supports S0 S3 S4 S5)
[    0.192935] ACPI: Using IOAPIC for interrupt routing
[    0.192026] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.207886] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.207893] ACPI: EC: driver started in interrupt mode
[    0.208047] ACPI: Power Resource [QFAN] (off)
[    0.208924] ACPI: No dock devices found.
[    0.210185] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.210452] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.210462] pci 0000:00:01.0: PME# disabled
[    0.210620] pci 0000:00:1a.0: reg 20 io port: [0x1800-0x181f]
[    0.210732] pci 0000:00:1a.1: reg 20 io port: [0x1820-0x183f]
[    0.210860] pci 0000:00:1a.7: reg 10 32bit mmio: [0xf4704000-0xf47043ff]
[    0.210973] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.210984] pci 0000:00:1a.7: PME# disabled
[    0.211079] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf4700000-0xf4703fff]
[    0.211189] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.211199] pci 0000:00:1b.0: PME# disabled
[    0.211350] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.211361] pci 0000:00:1c.0: PME# disabled
[    0.211516] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.211526] pci 0000:00:1c.1: PME# disabled
[    0.211682] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.211692] pci 0000:00:1c.2: PME# disabled
[    0.211846] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.211856] pci 0000:00:1c.3: PME# disabled
[    0.212021] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.212031] pci 0000:00:1c.5: PME# disabled
[    0.212147] pci 0000:00:1d.0: reg 20 io port: [0x1840-0x185f]
[    0.212267] pci 0000:00:1d.1: reg 20 io port: [0x1860-0x187f]
[    0.212385] pci 0000:00:1d.2: reg 20 io port: [0x1880-0x189f]
[    0.212506] pci 0000:00:1d.7: reg 10 32bit mmio: [0xf4704400-0xf47047ff]
[    0.212615] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.212625] pci 0000:00:1d.7: PME# disabled
[    0.212900] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.212910] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH6 GPIO
[    0.212919] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0680 (mask 007f)
[    0.212929] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 1640 (mask 000f)
[    0.212938] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0260 (mask 00ff)
[    0.213027] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.213043] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.213058] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.213074] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.213090] pci 0000:00:1f.1: reg 20 io port: [0x18a0-0x18af]
[    0.213190] pci 0000:00:1f.2: reg 10 io port: [0x18f8-0x18ff]
[    0.213205] pci 0000:00:1f.2: reg 14 io port: [0x18cc-0x18cf]
[    0.213221] pci 0000:00:1f.2: reg 18 io port: [0x18f0-0x18f7]
[    0.213237] pci 0000:00:1f.2: reg 1c io port: [0x18c8-0x18cb]
[    0.213253] pci 0000:00:1f.2: reg 20 io port: [0x18e0-0x18ef]
[    0.213269] pci 0000:00:1f.2: reg 24 io port: [0x18d0-0x18df]
[    0.213323] pci 0000:00:1f.2: PME# supported from D3hot
[    0.213333] pci 0000:00:1f.2: PME# disabled
[    0.213381] pci 0000:00:1f.3: reg 10 32bit mmio: [0x000000-0x0000ff]
[    0.213424] pci 0000:00:1f.3: reg 20 io port: [0x1c00-0x1c1f]
[    0.213563] pci 0000:01:00.0: reg 10 32bit mmio: [0xce000000-0xceffffff]
[    0.213591] pci 0000:01:00.0: reg 14 64bit mmio: [0xd0000000-0xdfffffff]
[    0.213619] pci 0000:01:00.0: reg 1c 64bit mmio: [0xcc000000-0xcdffffff]
[    0.213636] pci 0000:01:00.0: reg 24 io port: [0x2000-0x207f]
[    0.213654] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.213838] pci 0000:00:01.0: bridge io port: [0x2000-0x2fff]
[    0.213847] pci 0000:00:01.0: bridge 32bit mmio: [0xcc000000-0xceffffff]
[    0.213859] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.214169] pci 0000:02:00.0: reg 10 64bit mmio: [0xf4100000-0xf4101fff]
[    0.214551] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    0.214588] pci 0000:02:00.0: PME# disabled
[    0.214763] pci 0000:00:1c.0: bridge 32bit mmio: [0xf4100000-0xf41fffff]
[    0.214880] pci 0000:00:1c.1: bridge io port: [0x3000-0x3fff]
[    0.214890] pci 0000:00:1c.1: bridge 32bit mmio: [0xf2000000-0xf3ffffff]
[    0.214907] pci 0000:00:1c.1: bridge 64bit mmio pref: [0xf0000000-0xf1ffffff]
[    0.215015] pci 0000:06:00.0: reg 10 32bit mmio: [0xf4300000-0xf43003ff]
[    0.215048] pci 0000:06:00.0: reg 18 io port: [0x4000-0x407f]
[    0.215108] pci 0000:06:00.0: reg 30 32bit mmio: [0x000000-0x00ffff]
[    0.215304] pci 0000:00:1c.2: bridge io port: [0x4000-0x4fff]
[    0.215314] pci 0000:00:1c.2: bridge 32bit mmio: [0xf4300000-0xf43fffff]
[    0.215434] pci 0000:07:00.0: reg 10 io port: [0x5020-0x5027]
[    0.215453] pci 0000:07:00.0: reg 14 io port: [0x5014-0x5017]
[    0.215471] pci 0000:07:00.0: reg 18 io port: [0x5018-0x501f]
[    0.215489] pci 0000:07:00.0: reg 1c io port: [0x5010-0x5013]
[    0.215508] pci 0000:07:00.0: reg 20 io port: [0x5000-0x500f]
[    0.215527] pci 0000:07:00.0: reg 24 32bit mmio: [0xf4200000-0xf4201fff]
[    0.215601] pci 0000:07:00.0: PME# supported from D3hot
[    0.215612] pci 0000:07:00.0: PME# disabled
[    0.215726] pci 0000:00:1c.3: bridge io port: [0x5000-0x5fff]
[    0.215737] pci 0000:00:1c.3: bridge 32bit mmio: [0xf4200000-0xf42fffff]
[    0.215867] pci 0000:08:00.0: reg 10 64bit mmio: [0xf4000000-0xf4003fff]
[    0.215884] pci 0000:08:00.0: reg 18 io port: [0x6000-0x60ff]
[    0.216017] pci 0000:08:00.0: supports D1 D2
[    0.216023] pci 0000:08:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.216034] pci 0000:08:00.0: PME# disabled
[    0.216145] pci 0000:00:1c.5: bridge io port: [0x6000-0x6fff]
[    0.216155] pci 0000:00:1c.5: bridge 32bit mmio: [0xf4000000-0xf40fffff]
[    0.216245] pci 0000:09:01.0: reg 10 32bit mmio: [0xf4400000-0xf44007ff]
[    0.216347] pci 0000:09:01.0: supports D1 D2
[    0.216352] pci 0000:09:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.216363] pci 0000:09:01.0: PME# disabled
[    0.216437] pci 0000:09:01.1: reg 10 32bit mmio: [0xf4400800-0xf44008ff]
[    0.216534] pci 0000:09:01.1: supports D1 D2
[    0.216539] pci 0000:09:01.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.216550] pci 0000:09:01.1: PME# disabled
[    0.216623] pci 0000:09:01.2: reg 10 32bit mmio: [0xf4400c00-0xf4400cff]
[    0.216725] pci 0000:09:01.2: supports D1 D2
[    0.216730] pci 0000:09:01.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.216740] pci 0000:09:01.2: PME# disabled
[    0.216813] pci 0000:09:01.3: reg 10 32bit mmio: [0xf4401000-0xf44010ff]
[    0.216912] pci 0000:09:01.3: supports D1 D2
[    0.216917] pci 0000:09:01.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.216927] pci 0000:09:01.3: PME# disabled
[    0.217038] pci 0000:00:1e.0: transparent bridge
[    0.217054] pci 0000:00:1e.0: bridge 32bit mmio: [0xf4400000-0xf44fffff]
[    0.217139] pci_bus 0000:00: on NUMA node 0
[    0.217151] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.217613] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    0.217809] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.217988] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.218164] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.218342] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.218528] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    0.218785] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.228986] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 12 14 15) *11
[    0.229212] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.229434] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 *5 6 7 12 14 15)
[    0.229658] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    0.229877] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 12 14 15) *0, disabled.
[    0.230096] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 *7 11 12 14 15)
[    0.230313] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 *5 6 7 12 14 15)
[    0.230531] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.230949] SCSI subsystem initialized
[    0.232034] libata version 3.00 loaded.
[    0.232100] usbcore: registered new interface driver usbfs
[    0.232108] usbcore: registered new interface driver hub
[    0.232120] usbcore: registered new device driver usb
[    0.232120] ACPI: WMI: Mapper loaded
[    0.232123] PCI: Using ACPI for IRQ routing
[    0.244017] Bluetooth: Core ver 2.15
[    0.244030] NET: Registered protocol family 31
[    0.244033] Bluetooth: HCI device and connection manager initialized
[    0.244038] Bluetooth: HCI socket layer initialized
[    0.244043] NetLabel: Initializing
[    0.244047] NetLabel:  domain hash size = 128
[    0.244051] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.244084] NetLabel:  unlabeled traffic allowed by default
[    0.244155] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.244169] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.267293] pnp: PnP ACPI init
[    0.267314] ACPI: bus type pnp registered
[    0.273594] pnp: PnP ACPI: found 11 devices
[    0.273600] ACPI: ACPI bus type pnp unregistered
[    0.273610] PnPBIOS: Disabled by ACPI PNP
[    0.273633] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.273641] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.273648] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.273656] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.273663] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    0.273670] system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.273677] system 00:01: iomem range 0xfed40000-0xfed44fff has been reserved
[    0.273684] system 00:01: iomem range 0xfed45000-0xfed8ffff has been reserved
[    0.273703] system 00:05: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.273719] system 00:07: ioport range 0x680-0x69f has been reserved
[    0.273727] system 00:07: ioport range 0x800-0x80f has been reserved
[    0.273734] system 00:07: ioport range 0x1000-0x107f has been reserved
[    0.273741] system 00:07: ioport range 0x1180-0x11bf has been reserved
[    0.273748] system 00:07: ioport range 0x1640-0x164f has been reserved
[    0.273755] system 00:07: ioport range 0xfe00-0xfe00 has been reserved
[    0.308635] AppArmor: AppArmor Filesystem Enabled
[    0.308816] pci 0000:01:00.0: BAR 6: can't allocate mem resource [0xe0000000-0xdfffffff]
[    0.308824] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.308832] pci 0000:00:01.0:   IO window: 0x2000-0x2fff
[    0.308842] pci 0000:00:01.0:   MEM window: 0xcc000000-0xceffffff
[    0.308852] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.308864] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.308869] pci 0000:00:1c.0:   IO window: disabled
[    0.308882] pci 0000:00:1c.0:   MEM window: 0xf4100000-0xf41fffff
[    0.308891] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.308901] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:04
[    0.308909] pci 0000:00:1c.1:   IO window: 0x3000-0x3fff
[    0.308922] pci 0000:00:1c.1:   MEM window: 0xf2000000-0xf3ffffff
[    0.308933] pci 0000:00:1c.1:   PREFETCH window: 0x000000f0000000-0x000000f1ffffff
[    0.308950] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:06
[    0.308958] pci 0000:00:1c.2:   IO window: 0x4000-0x4fff
[    0.308970] pci 0000:00:1c.2:   MEM window: 0xf4300000-0xf43fffff
[    0.308980] pci 0000:00:1c.2:   PREFETCH window: 0x80000000-0x800fffff
[    0.308991] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:07
[    0.308998] pci 0000:00:1c.3:   IO window: 0x5000-0x5fff
[    0.309011] pci 0000:00:1c.3:   MEM window: 0xf4200000-0xf42fffff
[    0.309020] pci 0000:00:1c.3:   PREFETCH window: disabled
[    0.309031] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:08
[    0.309038] pci 0000:00:1c.5:   IO window: 0x6000-0x6fff
[    0.309051] pci 0000:00:1c.5:   MEM window: 0xf4000000-0xf40fffff
[    0.309061] pci 0000:00:1c.5:   PREFETCH window: disabled
[    0.309072] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:09
[    0.309077] pci 0000:00:1e.0:   IO window: disabled
[    0.309089] pci 0000:00:1e.0:   MEM window: 0xf4400000-0xf44fffff
[    0.309099] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.309121]   alloc irq_desc for 16 on node -1
[    0.309126]   alloc kstat_irqs on node -1
[    0.309137] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.309147] pci 0000:00:01.0: setting latency timer to 64
[    0.309163]   alloc irq_desc for 17 on node -1
[    0.309168]   alloc kstat_irqs on node -1
[    0.309176] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.309187] pci 0000:00:1c.0: setting latency timer to 64
[    0.309205] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.309215] pci 0000:00:1c.1: setting latency timer to 64
[    0.309232]   alloc irq_desc for 18 on node -1
[    0.309236]   alloc kstat_irqs on node -1
[    0.309249] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.309260] pci 0000:00:1c.2: setting latency timer to 64
[    0.309276]   alloc irq_desc for 19 on node -1
[    0.309281]   alloc kstat_irqs on node -1
[    0.309289] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.309299] pci 0000:00:1c.3: setting latency timer to 64
[    0.309316] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.309326] pci 0000:00:1c.5: setting latency timer to 64
[    0.309342] pci 0000:00:1e.0: setting latency timer to 64
[    0.309351] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.309358] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.309365] pci_bus 0000:01: resource 0 io:  [0x2000-0x2fff]
[    0.309371] pci_bus 0000:01: resource 1 mem: [0xcc000000-0xceffffff]
[    0.309378] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.309385] pci_bus 0000:02: resource 1 mem: [0xf4100000-0xf41fffff]
[    0.309391] pci_bus 0000:04: resource 0 io:  [0x3000-0x3fff]
[    0.309397] pci_bus 0000:04: resource 1 mem: [0xf2000000-0xf3ffffff]
[    0.309403] pci_bus 0000:04: resource 2 pref mem [0xf0000000-0xf1ffffff]
[    0.309410] pci_bus 0000:06: resource 0 io:  [0x4000-0x4fff]
[    0.309416] pci_bus 0000:06: resource 1 mem: [0xf4300000-0xf43fffff]
[    0.309423] pci_bus 0000:06: resource 2 pref mem [0x80000000-0x800fffff]
[    0.309429] pci_bus 0000:07: resource 0 io:  [0x5000-0x5fff]
[    0.309435] pci_bus 0000:07: resource 1 mem: [0xf4200000-0xf42fffff]
[    0.309441] pci_bus 0000:08: resource 0 io:  [0x6000-0x6fff]
[    0.309447] pci_bus 0000:08: resource 1 mem: [0xf4000000-0xf40fffff]
[    0.309454] pci_bus 0000:09: resource 1 mem: [0xf4400000-0xf44fffff]
[    0.309460] pci_bus 0000:09: resource 3 io:  [0x00-0xffff]
[    0.309466] pci_bus 0000:09: resource 4 mem: [0x000000-0xffffffff]
[    0.309544] NET: Registered protocol family 2
[    0.309760] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.310476] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.311299] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.311719] TCP: Hash tables configured (established 131072 bind 65536)
[    0.311724] TCP reno registered
[    0.311876] NET: Registered protocol family 1
[    0.311996] Trying to unpack rootfs image as initramfs...
[    0.503326] Switched to high resolution mode on CPU 1
[    0.504039] Switched to high resolution mode on CPU 0
[    0.789115] Freeing initrd memory: 7703k freed
[    0.797153] Simple Boot Flag at 0x36 set to 0x1
[    0.797579] cpufreq-nforce2: No nForce2 chipset.
[    0.797643] Scanning for low memory corruption every 60 seconds
[    0.797878] audit: initializing netlink socket (disabled)
[    0.797913] type=2000 audit(1258985482.796:1): initialized
[    0.819192] highmem bounce pool size: 64 pages
[    0.819204] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.822917] VFS: Disk quotas dquot_6.5.2
[    0.823084] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.824432] fuse init (API version 7.12)
[    0.824638] msgmni has been set to 1706
[    0.825123] alg: No test for stdrng (krng)
[    0.825159] io scheduler noop registered
[    0.825164] io scheduler anticipatory registered
[    0.825169] io scheduler deadline registered
[    0.825269] io scheduler cfq registered (default)
[    0.825532] pci 0000:01:00.0: Boot video device
[    0.825868]   alloc irq_desc for 24 on node -1
[    0.825874]   alloc kstat_irqs on node -1
[    0.825893] pcieport-driver 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.825910] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    0.826184]   alloc irq_desc for 25 on node -1
[    0.826189]   alloc kstat_irqs on node -1
[    0.826206] pcieport-driver 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.826227] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.826525]   alloc irq_desc for 26 on node -1
[    0.826529]   alloc kstat_irqs on node -1
[    0.826546] pcieport-driver 0000:00:1c.1: irq 26 for MSI/MSI-X
[    0.826567] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    0.826851]   alloc irq_desc for 27 on node -1
[    0.826855]   alloc kstat_irqs on node -1
[    0.826873] pcieport-driver 0000:00:1c.2: irq 27 for MSI/MSI-X
[    0.826893] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    0.827185]   alloc irq_desc for 28 on node -1
[    0.827189]   alloc kstat_irqs on node -1
[    0.827206] pcieport-driver 0000:00:1c.3: irq 28 for MSI/MSI-X
[    0.827227] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    0.827521]   alloc irq_desc for 29 on node -1
[    0.827525]   alloc kstat_irqs on node -1
[    0.827542] pcieport-driver 0000:00:1c.5: irq 29 for MSI/MSI-X
[    0.827562] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    0.827787] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.828229] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.828626] ACPI: AC Adapter [ACAD] (off-line)
[    0.828807] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.828815] ACPI: Power Button [PWRF]
[    0.828936] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    0.833753] ACPI: Lid Switch [LID]
[    0.833863] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
[    0.833870] ACPI: Power Button [PWRB]
[    0.834148] fan PNP0C0B:00: registered as cooling_device0
[    0.834162] ACPI: Fan [FAN] (off)
[    0.835627] ACPI: SSDT 7f6dad6d 0027A (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.836752] ACPI: SSDT 7f6da6b9 0062F (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.841926] Monitor-Mwait will be used to enter C-1 state
[    0.841988] Monitor-Mwait will be used to enter C-2 state
[    0.842043] Monitor-Mwait will be used to enter C-3 state
[    0.842062] Marking TSC unstable due to TSC halts in idle
[    0.842101] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    0.842150] processor LNXCPU:00: registered as cooling_device1
[    0.842160] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.842940] ACPI: SSDT 7f6dafe7 000C8 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.843700] ACPI: SSDT 7f6dace8 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.845668] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    0.845717] processor LNXCPU:01: registered as cooling_device2
[    0.845727] ACPI: Processor [CPU1] (supports 8 throttling states)
[    0.852287] thermal LNXTHERM:01: registered as thermal_zone0
[    0.852308] ACPI: Thermal Zone [THRM] (63 C)
[    0.852456] isapnp: Scanning for PnP cards...
[    1.048024] ACPI: Battery Slot [BAT1] (battery present)
[    1.210923] isapnp: No Plug & Play device found
[    1.213741] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.216989] brd: module loaded
[    1.218103] loop: module loaded
[    1.218265] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.218460] ahci 0000:07:00.0: version 3.0
[    1.218490] ahci 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.232064] ahci 0000:07:00.0: AHCI 0001.0000 32 slots 1 ports 3 Gbps 0x1 impl SATA mode
[    1.232073] ahci 0000:07:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    1.232086] ahci 0000:07:00.0: setting latency timer to 64
[    1.232303] scsi0 : ahci
[    1.232446] ata1: SATA max UDMA/133 abar m8192@0xf4200000 port 0xf4200100 irq 19
[    1.232568] ata_piix 0000:00:1f.1: version 2.13
[    1.232587] ata_piix 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.232660] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.232785] scsi1 : ata_piix
[    1.232928] scsi2 : ata_piix
[    1.234207] ata2: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x18a0 irq 14
[    1.234215] ata3: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18a8 irq 15
[    1.234259] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.234271] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    1.388085] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.388231] scsi3 : ata_piix
[    1.388359] scsi4 : ata_piix
[    1.390669] ata4: SATA max UDMA/133 cmd 0x18f8 ctl 0x18cc bmdma 0x18e0 irq 19
[    1.390682] ata5: SATA max UDMA/133 cmd 0x18f0 ctl 0x18c8 bmdma 0x18e8 irq 19
[    1.393031] Fixed MDIO Bus: probed
[    1.393117] PPP generic driver version 2.4.2
[    1.393315] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.393352] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.393377] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    1.393386] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    1.393485] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    1.397410] ehci_hcd 0000:00:1a.7: debug port 1
[    1.397424] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    1.400105] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf4704000
[    1.400694] ata2.00: ATAPI: Optiarc DVD RW AD-7530A, EX33, max UDMA/33
[    1.412052] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    1.412219] usb usb1: configuration #1 chosen from 1 choice
[    1.412289] hub 1-0:1.0: USB hub found
[    1.412306] hub 1-0:1.0: 4 ports detected
[    1.412438]   alloc irq_desc for 23 on node -1
[    1.412444]   alloc kstat_irqs on node -1
[    1.412456] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.412478] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.412486] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.412558] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    1.416486] ehci_hcd 0000:00:1d.7: debug port 1
[    1.416499] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.416530] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf4704400
[    1.416560] ata2.00: configured for UDMA/33
[    1.432030] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.432182] usb usb2: configuration #1 chosen from 1 choice
[    1.432248] hub 2-0:1.0: USB hub found
[    1.432262] hub 2-0:1.0: 6 ports detected
[    1.432399] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.432442] uhci_hcd: USB Universal Host Controller Interface driver
[    1.432486] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.432499] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.432507] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.432577] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    1.432633] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001800
[    1.432813] usb usb3: configuration #1 chosen from 1 choice
[    1.432877] hub 3-0:1.0: USB hub found
[    1.432897] hub 3-0:1.0: 2 ports detected
[    1.432998]   alloc irq_desc for 21 on node -1
[    1.433004]   alloc kstat_irqs on node -1
[    1.433014] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.433028] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    1.433035] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.433111] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    1.433166] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001820
[    1.433340] usb usb4: configuration #1 chosen from 1 choice
[    1.433404] hub 4-0:1.0: USB hub found
[    1.433419] hub 4-0:1.0: 2 ports detected
[    1.433529] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.433543] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.433551] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.433622] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    1.433664] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001840
[    1.433841] usb usb5: configuration #1 chosen from 1 choice
[    1.433906] hub 5-0:1.0: USB hub found
[    1.433928] hub 5-0:1.0: 2 ports detected
[    1.434037] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.434051] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.434058] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.434142] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    1.434184] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001860
[    1.434373] usb usb6: configuration #1 chosen from 1 choice
[    1.434437] hub 6-0:1.0: USB hub found
[    1.434452] hub 6-0:1.0: 2 ports detected
[    1.434560] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.434574] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.434581] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.434652] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    1.434693] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001880
[    1.434870] usb usb7: configuration #1 chosen from 1 choice
[    1.434933] hub 7-0:1.0: USB hub found
[    1.434948] hub 7-0:1.0: 2 ports detected
[    1.435189] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.438168] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.439389] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.439401] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.439408] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.439415] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.439422] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.439540] mice: PS/2 mouse device common for all mice
[    1.439794] rtc_cmos 00:08: RTC can wake from S4
[    1.439862] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    1.439908] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.440159] device-mapper: uevent: version 1.0.3
[    1.440399] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    1.440561] device-mapper: multipath: version 1.1.0 loaded
[    1.440568] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.440835] EISA: Probing bus 0 at eisa.0
[    1.440846] Cannot allocate resource for EISA slot 1
[    1.440852] Cannot allocate resource for EISA slot 2
[    1.440857] Cannot allocate resource for EISA slot 3
[    1.440862] Cannot allocate resource for EISA slot 4
[    1.440868] Cannot allocate resource for EISA slot 5
[    1.440873] Cannot allocate resource for EISA slot 6
[    1.440891] EISA: Detected 0 cards.
[    1.441245] cpuidle: using governor ladder
[    1.441543] cpuidle: using governor menu
[    1.442721] TCP cubic registered
[    1.443099] NET: Registered protocol family 10
[    1.444217] lo: Disabled Privacy Extensions
[    1.445063] NET: Registered protocol family 17
[    1.445102] Bluetooth: L2CAP ver 2.13
[    1.445106] Bluetooth: L2CAP socket layer initialized
[    1.445113] Bluetooth: SCO (Voice Link) ver 0.6
[    1.445117] Bluetooth: SCO socket layer initialized
[    1.445186] Bluetooth: RFCOMM TTY layer initialized
[    1.445193] Bluetooth: RFCOMM socket layer initialized
[    1.445198] Bluetooth: RFCOMM ver 1.11
[    1.446277] Using IPI No-Shortcut mode
[    1.446375] PM: Resume from disk failed.
[    1.446385] registered taskstats version 1
[    1.446510]   Magic number: 1:859:182
[    1.446605] rtc_cmos 00:08: setting system clock to 2009-11-23 14:11:24 UTC (1258985484)
[    1.446608] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.446610] EDD information not available.
[    1.476647] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.552133] ata1: SATA link down (SStatus 0 SControl 300)
[    1.569505] scsi 1:0:0:0: CD-ROM            Optiarc  DVD RW AD-7530A  EX33 PQ: 0 ANSI: 5
[    1.579742] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.579747] Uniform CD-ROM driver Revision: 3.20
[    1.579868] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.579934] sr 1:0:0:0: Attached scsi generic sg0 type 5
[    1.724115] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.869630] usb 1-1: configuration #1 chosen from 1 choice
[    2.000111] Clocksource tsc unstable (delta = -314663702 ns)
[    2.092122] usb 2-4: new high speed USB device using ehci_hcd and address 4
[    2.200204] ata5.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.200225] ata5.01: SATA link down (SStatus 0 SControl 0)
[    2.200453] ata4.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.200471] ata4.01: SATA link down (SStatus 0 SControl 300)
[    2.208688] ata4.00: ATA-7: ST9160821AS, 3.ALC, max UDMA/133
[    2.208691] ata4.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.208807] ata5.00: ATA-7: ST9160821AS, 3.ALC, max UDMA/133
[    2.208810] ata5.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.224725] ata5.00: configured for UDMA/133
[    2.224756] ata4.00: configured for UDMA/133
[    2.224833] scsi 3:0:0:0: Direct-Access     ATA      ST9160821AS      3.AL PQ: 0 ANSI: 5
[    2.224953] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    2.224966] sd 3:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    2.225012] sd 3:0:0:0: [sda] Write Protect is off
[    2.225015] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.225039] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.225052] scsi 4:0:0:0: Direct-Access     ATA      ST9160821AS      3.AL PQ: 0 ANSI: 5
[    2.225153] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    2.225155]  sda:
[    2.225186] sd 4:0:0:0: [sdb] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    2.225282] sd 4:0:0:0: [sdb] Write Protect is off
[    2.225285] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.225308] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.225424]  sdb:
[    2.226920] usb 2-4: configuration #1 chosen from 1 choice
[    2.238401]  sdb1 < sdb5 sdb6 > sdb2 sdb3 sdb4
[    2.245673] sd 4:0:0:0: [sdb] Attached SCSI disk
[    2.246363]  sda1 sda2
[    2.246668] sd 3:0:0:0: [sda] Attached SCSI disk
[    2.246726] Freeing unused kernel memory: 540k freed
[    2.247080] Write protecting the kernel text: 4568k
[    2.247142] Write protecting the kernel read-only data: 1836k
[    2.369593] acpi device:04: registered as cooling_device3
[    2.369742] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/device:03/input/input5
[    2.369776] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    2.375728] Linux agpgart interface v0.103
[    2.444925] sky2 driver version 1.23
[    2.444971] sky2 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.444987] sky2 0000:08:00.0: setting latency timer to 64
[    2.445018] sky2 0000:08:00.0: Yukon-2 FE chip revision 3
[    2.445129]   alloc irq_desc for 30 on node -1
[    2.445132]   alloc kstat_irqs on node -1
[    2.445149] sky2 0000:08:00.0: irq 30 for MSI/MSI-X
[    2.445786] sky2 eth0: addr 00:1e:68:11:58:29
[    2.448639] ohci1394 0000:09:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.460155] Initializing USB Mass Storage driver...
[    2.460287] scsi5 : SCSI emulation for USB Mass Storage devices
[    2.460373] usbcore: registered new interface driver usb-storage
[    2.460377] USB Mass Storage support registered.
[    2.460450] usb-storage: device found at 4
[    2.460451] usb-storage: waiting for device to settle before scanning
[    2.464425] usb 5-2: new low speed USB device using uhci_hcd and address 2
[    2.507093] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[f4400000-f44007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    2.630855] usb 5-2: configuration #1 chosen from 1 choice
[    2.638663] usbcore: registered new interface driver hiddev
[    2.652071] input: USB Mouse as /devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.0/input/input6
[    2.652144] generic-usb 0003:15D9:0A33.0001: input,hidraw0: USB HID v1.10 Mouse [USB Mouse] on usb-0000:00:1d.0-2/input0
[    2.652158] usbcore: registered new interface driver usbhid
[    2.652160] usbhid: v2.6:USB HID core driver
[    2.873114] usb 6-1: new low speed USB device using uhci_hcd and address 2
[    3.052336] usb 6-1: configuration #1 chosen from 1 choice
[    3.070523] input: LITEON Technology USB Multimedia Keyboard as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0/input/input7
[    3.070579] generic-usb 0003:046D:C312.0002: input,hidraw1: USB HID v1.10 Keyboard [LITEON Technology USB Multimedia Keyboard] on usb-0000:00:1d.1-1/input0
[    3.820660] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00004ce056681e00]
[    3.921620] xor: automatically using best checksumming function: pIII_sse
[    3.941019]    pIII_sse  :  7986.000 MB/sec
[    3.941021] xor: using function: pIII_sse (7986.000 MB/sec)
[    3.943197] device-mapper: dm-raid45: initialized v0.2594b
[    4.469496] PM: Starting manual resume from disk
[    4.469500] PM: Resume from partition 8:21
[    4.469502] PM: Checking hibernation image.
[    4.469694] PM: Resume from disk failed.
[    4.482406] EXT4-fs (sdb6): barriers enabled
[    4.494570] kjournald2 starting: pid 438, dev sdb6:8, commit interval 5 seconds
[    4.494600] EXT4-fs (sdb6): delayed allocation enabled
[    4.494607] EXT4-fs: file extents enabled
[    4.494781] EXT4-fs: mballoc enabled
[    4.494792] EXT4-fs (sdb6): mounted filesystem with ordered data mode
[    5.202756] type=1505 audit(1258985488.255:2): operation="profile_load" pid=461 name=/usr/share/gdm/guest-session/Xsession
[    5.205480] type=1505 audit(1258985488.257:3): operation="profile_load" pid=462 name=/sbin/dhclient3
[    5.206145] type=1505 audit(1258985488.257:4): operation="profile_load" pid=462 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    5.206507] type=1505 audit(1258985488.257:5): operation="profile_load" pid=462 name=/usr/lib/connman/scripts/dhclient-script
[    5.285414] type=1505 audit(1258985488.337:6): operation="profile_load" pid=463 name=/usr/bin/evince
[    5.296203] type=1505 audit(1258985488.349:7): operation="profile_load" pid=463 name=/usr/bin/evince-previewer
[    5.302562] type=1505 audit(1258985488.353:8): operation="profile_load" pid=463 name=/usr/bin/evince-thumbnailer
[    5.325556] type=1505 audit(1258985488.377:9): operation="profile_load" pid=465 name=/usr/bin/freshclam
[    5.336099] type=1505 audit(1258985488.389:10): operation="profile_load" pid=466 name=/usr/lib/cups/backend/cups-pdf
[    5.336913] type=1505 audit(1258985488.389:11): operation="profile_load" pid=466 name=/usr/sbin/cupsd
[    6.416546] Adding 2000020k swap on /dev/sdb5.  Priority:-1 extents:1 across:2000020k 
[    6.695155] EXT4-fs (sdb6): internal journal on sdb6:8
[    7.460422] usb-storage: device scan complete
[    7.461232] scsi 5:0:0:0: Direct-Access     ST       8GB              0000 PQ: 0 ANSI: 0 CCS
[    7.461621] sd 5:0:0:0: Attached scsi generic sg3 type 0
[    7.462365] sd 5:0:0:0: [sdc] 15663104 512-byte logical blocks: (8.01 GB/7.46 GiB)
[    7.463100] sd 5:0:0:0: [sdc] Write Protect is off
[    7.463104] sd 5:0:0:0: [sdc] Mode Sense: 43 00 00 00
[    7.463108] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[    7.466514] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[    7.466520]  sdc: sdc1
[    7.468608] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[    7.468613] sd 5:0:0:0: [sdc] Attached SCSI removable disk
[    9.181063] sky2 eth0: enabling interface
[    9.181261] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    9.415363] udev: starting version 147
[    9.987737] ip_tables: (C) 2000-2006 Netfilter Core Team
[   10.082515] lirc_dev: IR Remote Control driver registered, major 61 
[   10.084382] lirc_dev: lirc_register_driver: sample_rate: 0
[   10.086560] lirc_ite8709: device found : irq=10 io=0x260
[   10.137431] ricoh-mmc: Ricoh MMC Controller disabling driver
[   10.137433] ricoh-mmc: Copyright(c) Philip Langdale
[   10.137468] ricoh-mmc: Ricoh MMC controller found at 0000:09:01.2 [1180:0843] (rev 1)
[   10.137490] ricoh-mmc: Controller is now disabled.
[   10.440101] cfg80211: Calling CRDA to update world regulatory domain
[   10.467420] Linux video capture interface: v2.00
[   10.494457] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (04f2:b024)
[   10.497941] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1:1.0/input/input8
[   10.498016] usbcore: registered new interface driver uvcvideo
[   10.498021] USB Video Class driver (v0.1.0)
[   10.836664] cfg80211: World regulatory domain updated:
[   10.836667]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.836670]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.836672]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.836674]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.836677]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.836679]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.022132] nvidia: module license 'NVIDIA' taints kernel.
[   11.022138] Disabling lock debugging due to kernel taint
[   11.275179] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.275189] nvidia 0000:01:00.0: setting latency timer to 64
[   11.275340] NVRM: loading NVIDIA UNIX x86 Kernel Module  185.18.36  Fri Aug 14 17:18:04 PDT 2009
[   11.384290] sdhci: Secure Digital Host Controller Interface driver
[   11.384293] sdhci: Copyright(c) Pierre Ossman
[   11.521365] sdhci-pci 0000:09:01.1: SDHCI controller found [1180:0822] (rev 19)
[   11.521383] sdhci-pci 0000:09:01.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   11.523440] Registered led device: mmc0::
[   11.524479] mmc0: SDHCI controller on PCI [0000:09:01.1] using PIO
[   11.802133] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   11.802137] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   11.802239] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.802270] iwlagn 0000:02:00.0: setting latency timer to 64
[   11.802327] iwlagn 0000:02:00.0: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[   11.851691] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 19 802.11a channels
[   11.851760]   alloc irq_desc for 31 on node -1
[   11.851762]   alloc kstat_irqs on node -1
[   11.851783] iwlagn 0000:02:00.0: irq 31 for MSI/MSI-X
[   12.041847] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   12.173631] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-4965-2.ucode
[   12.264680] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x81a0b2, caps: 0xa04713/0x200000
[   12.309569] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input9
[   12.318994] iwlagn 0000:02:00.0: loaded firmware version 228.61.2.24
[   12.538369] Registered led device: iwl-phy0::radio
[   12.538402] Registered led device: iwl-phy0::assoc
[   12.538430] Registered led device: iwl-phy0::RX
[   12.538458] Registered led device: iwl-phy0::TX
[   12.574721] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   13.878352] lp: driver loaded but no devices found
[   14.375663]   alloc irq_desc for 22 on node -1
[   14.375667]   alloc kstat_irqs on node -1
[   14.375674] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   14.375708] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   14.729173] __ratelimit: 6 callbacks suppressed
[   14.729177] type=1505 audit(1259021497.782:14): operation="profile_replace" pid=1154 name=/usr/share/gdm/guest-session/Xsession
[   14.730819] type=1505 audit(1259021497.782:15): operation="profile_replace" pid=1155 name=/sbin/dhclient3
[   14.731487] type=1505 audit(1259021497.782:16): operation="profile_replace" pid=1155 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   14.731849] type=1505 audit(1259021497.782:17): operation="profile_replace" pid=1155 name=/usr/lib/connman/scripts/dhclient-script
[   14.735333] type=1505 audit(1259021497.786:18): operation="profile_replace" pid=1156 name=/usr/bin/evince
[   14.746529] type=1505 audit(1259021497.798:19): operation="profile_replace" pid=1156 name=/usr/bin/evince-previewer
[   14.752947] type=1505 audit(1259021497.802:20): operation="profile_replace" pid=1156 name=/usr/bin/evince-thumbnailer
[   14.761727] type=1505 audit(1259021497.814:21): operation="profile_replace" pid=1158 name=/usr/bin/freshclam
[   14.763456] type=1505 audit(1259021497.814:22): operation="profile_replace" pid=1159 name=/usr/lib/cups/backend/cups-pdf
[   14.764265] type=1505 audit(1259021497.814:23): operation="profile_replace" pid=1159 name=/usr/sbin/cupsd
[   20.537529] __ratelimit: 18 callbacks suppressed
[   20.537533] type=1503 audit(1259021503.589:30): operation="open" pid=1502 parent=1501 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   22.067335] type=1503 audit(1259021505.118:31): operation="open" pid=1516 parent=1515 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   22.200550] type=1503 audit(1259021505.250:32): operation="open" pid=1527 parent=1526 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   26.508131] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   26.508135] vboxdrv: Warning: 2.6.31+ kernel detected. Most likely the hwardware performance
[   26.508136] vboxdrv: counter framework which can generate NMIs is active. You have to prevent
[   26.508137] vboxdrv: the usage of hardware performance counters by
[   26.508138] vboxdrv:   echo 2 > /proc/sys/kernel/perf_counter_paranoid
[   26.508142] vboxdrv: Found 2 processor cores.
[   26.508212] vboxdrv: fAsync=0 offMin=0x1c2 offMax=0xcda
[   26.508256] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   26.508258] vboxdrv: Successfully loaded version 3.0.12 (interface 0x00110000).
[   28.137891] ppdev: user-space parallel port driver
[   99.797149] sky2 eth0: disabling interface
[  102.164601] PM: Syncing filesystems ... done.
[  102.166595] PM: Preparing system for mem sleep
[  102.166598] Freezing user space processes ... (elapsed 0.01 seconds) done.
[  102.183925] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[  102.183976] PM: Entering mem sleep
[  102.183986] Suspending console(s) (use no_console_suspend to debug)
[  102.264113] sd 4:0:0:0: [sdb] Synchronizing SCSI cache
[  102.294036] sd 4:0:0:0: [sdb] Stopping disk
[  104.651769] sd 3:0:0:0: [sda] Synchronizing SCSI cache
[  104.651897] sd 3:0:0:0: [sda] Stopping disk
[  107.497734] ACPI handle has no context!
[  107.497800] lirc_ite8709 00:02: disabled
[  107.498862] ACPI handle has no context!
[  107.498868] sdhci-pci 0000:09:01.1: PME# disabled
[  107.498874] sdhci-pci 0000:09:01.1: PCI INT B disabled
[  107.498880] ACPI handle has no context!
[  107.517168] ACPI handle has no context!
[  107.532226] sky2 0000:08:00.0: PME# disabled
[  107.564305] ahci 0000:07:00.0: PCI INT A disabled
[  107.665162] ata_piix 0000:00:1f.2: PCI INT B disabled
[  107.680331] ata_piix 0000:00:1f.1: PCI INT A disabled
[  107.680343] ehci_hcd 0000:00:1d.7: PCI INT A disabled
[  107.680351] uhci_hcd 0000:00:1d.2: PCI INT C disabled
[  107.680359] uhci_hcd 0000:00:1d.1: PCI INT B disabled
[  107.680367] uhci_hcd 0000:00:1d.0: PCI INT A disabled
[  107.784434] HDA Intel 0000:00:1b.0: PCI INT A disabled
[  107.800118] ehci_hcd 0000:00:1a.7: PCI INT C disabled
[  107.800129] uhci_hcd 0000:00:1a.1: PCI INT B disabled
[  107.800139] uhci_hcd 0000:00:1a.0: PCI INT A disabled
[  107.800295] PM: suspend devices took 5.620 seconds
[  107.800382] ricoh-mmc: Suspending.
[  107.800392] ricoh-mmc: Controller is now re-enabled.
[  107.800751] ehci_hcd 0000:00:1d.7: PME# disabled
[  107.816416] ehci_hcd 0000:00:1a.7: PME# disabled
[  107.832487] ACPI: Preparing to enter system sleep state S3
[  107.920377] Disabling non-boot CPUs ...
[  108.024019] CPU 1 is now offline
[  108.024022] SMP alternatives: switching to UP code
[  108.030014] CPU0 attaching NULL sched-domain.
[  108.030016] CPU1 attaching NULL sched-domain.
[  108.030022] CPU0 attaching NULL sched-domain.
[  108.030186] CPU1 is down
[  108.030231] Extended CMOS year: 2000
[  108.030231] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[  108.030231] Back to C!
[  108.030231] CPU0: Thermal LVT vector (0xfa) already installed
[  108.030231] Extended CMOS year: 2000
[  108.030231] Enabling non-boot CPUs ...
[  108.030231] SMP alternatives: switching to SMP code
[  108.035945] Booting processor 1 APIC 0x1 ip 0x6000
[  108.029909] Initializing CPU#1
[  108.029909] Calibrating delay using timer specific routine.. 3990.05 BogoMIPS (lpj=7980117)
[  108.029909] CPU: L1 I cache: 32K, L1 D cache: 32K
[  108.029909] CPU: L2 cache: 4096K
[  108.029909] CPU: Physical Processor ID: 0
[  108.029909] CPU: Processor Core ID: 1
[  108.029909] mce: CPU supports 6 MCE banks
[  108.029909] CPU1: Thermal monitoring enabled (TM2)
[  108.029909] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[  108.125706] CPU1: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz stepping 0a
[  108.125776] CPU0 attaching NULL sched-domain.
[  108.129014] Switched to high resolution mode on CPU 1
[  108.140018] CPU0 attaching sched-domain:
[  108.140021]  domain 0: span 0-1 level MC
[  108.140023]   groups: 0 1
[  108.140027] CPU1 attaching sched-domain:
[  108.140029]  domain 0: span 0-1 level MC
[  108.140031]   groups: 1 0
[  108.141018] CPU1 is up
[  108.141020] ACPI: Waking up from system sleep state S3
[  108.141628] pcieport-driver 0000:00:01.0: restoring config space at offset 0x6 (was 0x0, writing 0x10100)
[  108.141633] pcieport-driver 0000:00:01.0: restoring config space at offset 0x3 (was 0x10000, writing 0x10010)
[  108.141638] pcieport-driver 0000:00:01.0: restoring config space at offset 0x1 (was 0x100107, writing 0x100507)
[  108.141682] uhci_hcd 0000:00:1a.0: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[  108.141716] uhci_hcd 0000:00:1a.1: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[  108.141760] ehci_hcd 0000:00:1a.7: restoring config space at offset 0x1 (was 0x2900106, writing 0x2900102)
[  108.141780] ehci_hcd 0000:00:1a.7: PME# disabled
[  108.141820] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[  108.141827] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100106, writing 0x100102)
[  108.141861] pcieport-driver 0000:00:1c.0: restoring config space at offset 0xf (was 0x40100, writing 0x4010b)
[  108.141878] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x7 (was 0x200000f0, writing 0x600000f0)
[  108.141889] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[  108.141896] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[  108.141947] pcieport-driver 0000:00:1c.1: restoring config space at offset 0xf (was 0x40200, writing 0x4020b)
[  108.141961] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x9 (was 0x10001, writing 0xf1f1f001)
[  108.141967] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x8 (was 0x0, writing 0xf3f0f200)
[  108.141972] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x7 (was 0x0, writing 0x3030)
[  108.141983] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[  108.141990] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100507)
[  108.142042] pcieport-driver 0000:00:1c.2: restoring config space at offset 0xf (was 0x40300, writing 0x40305)
[  108.142055] pcieport-driver 0000:00:1c.2: restoring config space at offset 0x9 (was 0x10001, writing 0x80018001)
[  108.142061] pcieport-driver 0000:00:1c.2: restoring config space at offset 0x8 (was 0x0, writing 0xf430f430)
[  108.142067] pcieport-driver 0000:00:1c.2: restoring config space at offset 0x7 (was 0x20000000, writing 0x4040)
[  108.142077] pcieport-driver 0000:00:1c.2: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[  108.142084] pcieport-driver 0000:00:1c.2: restoring config space at offset 0x1 (was 0x100000, writing 0x100507)
[  108.142136] pcieport-driver 0000:00:1c.3: restoring config space at offset 0xf (was 0x40400, writing 0x40405)
[  108.142149] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
[  108.142155] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x8 (was 0x0, writing 0xf420f420)
[  108.142161] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x7 (was 0x20000000, writing 0x5050)
[  108.142171] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[  108.142178] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x1 (was 0x100000, writing 0x100507)
[  108.142230] pcieport-driver 0000:00:1c.5: restoring config space at offset 0xf (was 0x40200, writing 0x4020b)
[  108.142243] pcieport-driver 0000:00:1c.5: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
[  108.142249] pcieport-driver 0000:00:1c.5: restoring config space at offset 0x8 (was 0x0, writing 0xf400f400)
[  108.142254] pcieport-driver 0000:00:1c.5: restoring config space at offset 0x7 (was 0x20000000, writing 0x6060)
[  108.142264] pcieport-driver 0000:00:1c.5: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[  108.142272] pcieport-driver 0000:00:1c.5: restoring config space at offset 0x1 (was 0x100000, writing 0x100507)
[  108.142333] uhci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[  108.142367] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[  108.142401] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[  108.142445] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x1 (was 0x2900106, writing 0x2900102)
[  108.142465] ehci_hcd 0000:00:1d.7: PME# disabled
[  108.142485] pci 0000:00:1e.0: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
[  108.142490] pci 0000:00:1e.0: restoring config space at offset 0x8 (was 0x0, writing 0xf440f440)
[  108.142496] pci 0000:00:1e.0: restoring config space at offset 0x7 (was 0x22800000, writing 0x228000f0)
[  108.142509] pci 0000:00:1e.0: restoring config space at offset 0x1 (was 0x100004, writing 0x100107)
[  108.142561] pci 0000:00:1f.0: restoring config space at offset 0x1 (was 0x2100007, writing 0x2100107)
[  108.142580] ata_piix 0000:00:1f.1: restoring config space at offset 0xf (was 0x100, writing 0x1ff)
[  108.142619] ata_piix 0000:00:1f.2: restoring config space at offset 0xf (was 0x200, writing 0x205)
[  108.142675] pci 0000:00:1f.3: restoring config space at offset 0x4 (was 0x0, writing 0x80100000)
[  108.142740] nvidia 0000:01:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[  108.142754] nvidia 0000:01:00.0: restoring config space at offset 0x9 (was 0x1, writing 0x2001)
[  108.142762] nvidia 0000:01:00.0: restoring config space at offset 0x7 (was 0x4, writing 0xcc000004)
[  108.142769] nvidia 0000:01:00.0: restoring config space at offset 0x5 (was 0xc, writing 0xd000000c)
[  108.142775] nvidia 0000:01:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xce000000)
[  108.142784] nvidia 0000:01:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[  108.142877] iwlagn 0000:02:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[  108.142930] iwlagn 0000:02:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf4100004)
[  108.142943] iwlagn 0000:02:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[  108.142960] iwlagn 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x40100106)
[  108.143064] pci 0000:06:00.0: restoring config space at offset 0xf (was 0x100, writing 0x105)
[  108.143077] pci 0000:06:00.0: restoring config space at offset 0xc (was 0x1, writing 0x0)
[  108.143097] pci 0000:06:00.0: restoring config space at offset 0x6 (was 0x1, writing 0x4001)
[  108.143108] pci 0000:06:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xf4300000)
[  108.143115] pci 0000:06:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[  108.143125] pci 0000:06:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100107)
[  108.143180] ahci 0000:07:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[  108.143200] ahci 0000:07:00.0: restoring config space at offset 0x9 (was 0x0, writing 0xf4200000)
[  108.143207] ahci 0000:07:00.0: restoring config space at offset 0x8 (was 0x1, writing 0x5001)
[  108.143214] ahci 0000:07:00.0: restoring config space at offset 0x7 (was 0x1, writing 0x5011)
[  108.143221] ahci 0000:07:00.0: restoring config space at offset 0x6 (was 0x1, writing 0x5019)
[  108.143228] ahci 0000:07:00.0: restoring config space at offset 0x5 (was 0x1, writing 0x5015)
[  108.143236] ahci 0000:07:00.0: restoring config space at offset 0x4 (was 0x1, writing 0x5021)
[  108.143243] ahci 0000:07:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[  108.143252] ahci 0000:07:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100107)
[  108.143322] sky2 0000:08:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[  108.143347] sky2 0000:08:00.0: restoring config space at offset 0x6 (was 0x1, writing 0x6001)
[  108.143355] sky2 0000:08:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf4000004)
[  108.143362] sky2 0000:08:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[  108.143371] sky2 0000:08:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100507)
[  108.143454] ohci1394 0000:09:01.0: restoring config space at offset 0x4 (was 0x0, writing 0xf4400000)
[  108.143459] ohci1394 0000:09:01.0: restoring config space at offset 0x3 (was 0x800000, writing 0x802000)
[  108.143467] ohci1394 0000:09:01.0: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
[  108.143510] sdhci-pci 0000:09:01.1: restoring config space at offset 0x4 (was 0x0, writing 0xf4400800)
[  108.143515] sdhci-pci 0000:09:01.1: restoring config space at offset 0x3 (was 0x800000, writing 0x802000)
[  108.143523] sdhci-pci 0000:09:01.1: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
[  108.143566] ricoh-mmc 0000:09:01.2: restoring config space at offset 0x4 (was 0x0, writing 0xf4400c00)
[  108.143575] ricoh-mmc 0000:09:01.2: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
[  108.143587] ricoh-mmc: Resuming.
[  108.143597] ricoh-mmc: Controller is now disabled.
[  115.086359] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  115.086370] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[  115.086401] usb usb3: root hub lost power or was reset
[  115.086450] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[  115.086459] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[  115.086488] usb usb4: root hub lost power or was reset
[  115.086512] ehci_hcd 0000:00:1a.7: PME# disabled
[  115.086518] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[  115.086527] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[  115.086534] usb usb1: root hub lost power or was reset
[  115.090437] ehci_hcd 0000:00:1a.7: debug port 1
[  115.090443] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[  115.090452] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[  115.090459] HDA Intel 0000:00:1b.0: setting latency timer to 64
[  115.090488] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[  115.090494] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[  115.090518] usb usb5: root hub lost power or was reset
[  115.090548] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[  115.090554] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[  115.090578] usb usb6: root hub lost power or was reset
[  115.090610] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[  115.090616] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[  115.090639] usb usb7: root hub lost power or was reset
[  115.090659] ehci_hcd 0000:00:1d.7: PME# disabled
[  115.090663] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[  115.090669] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[  115.090674] usb usb2: root hub lost power or was reset
[  115.094556] ehci_hcd 0000:00:1d.7: debug port 1
[  115.094562] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[  115.094573] pci 0000:00:1e.0: setting latency timer to 64
[  115.094581] ata_piix 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[  115.094586] ata_piix 0000:00:1f.1: setting latency timer to 64
[  115.095613] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[  115.095618] ata_piix 0000:00:1f.2: setting latency timer to 64
[  115.862607] pci 0000:06:00.0: PME# disabled
[  115.862625] ahci 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[  115.862641] ahci 0000:07:00.0: setting latency timer to 64
[  115.862771] sky2 0000:08:00.0: PME# disabled
[  115.863015] ata2.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[  115.863018] ata2.00: ACPI cmd ef/03:42:00:00:00:a0 filtered out
[  115.893120] ata4.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  115.893138] ata4.01: SATA link down (SStatus 4 SControl 300)
[  115.901286] ata4.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[  115.901289] ata4.00: ACPI cmd ef/03:22:00:00:00:a0 filtered out
[  115.908263] ata2.00: configured for UDMA/33
[  115.913118] ata5.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  115.913136] ata5.01: SATA link down (SStatus 0 SControl 0)
[  115.919051] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[f4400000-f44007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[  115.925521] ata5.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[  115.925524] ata5.00: ACPI cmd ef/03:41:00:00:00:a0 filtered out
[  115.925656] sdhci-pci 0000:09:01.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[  115.926671] pci 0000:09:01.3: PME# disabled
[  115.926815] lirc_ite8709 00:02: activated
[  115.926928] ata4.00: configured for UDMA/133
[  115.941456] ata5.00: configured for UDMA/133
[  116.181062] ata1: SATA link down (SStatus 0 SControl 300)
[  117.125043] usb 1-1: reset high speed USB device using ehci_hcd and address 2
[  117.268135] sd 3:0:0:0: [sda] Starting disk
[  117.287623] sd 4:0:0:0: [sdb] Starting disk
[  117.417041] usb 2-4: reset high speed USB device using ehci_hcd and address 4
[  117.809040] usb 5-2: reset low speed USB device using uhci_hcd and address 2
[  118.377039] usb 6-1: reset low speed USB device using uhci_hcd and address 2
[  118.684322] PM: resume devices took 10.528 seconds
[  118.684323] ------------[ cut here ]------------
[  118.684330] WARNING: at /build/buildd/linux-2.6.31/kernel/power/suspend_test.c:53 suspend_test_finish+0x84/0x90()
[  118.684332] Hardware name: EasyNote SB87                   
[  118.684334] Component: resume devices, time: 10528
[  118.684335] Modules linked in: binfmt_misc ppdev vboxnetadp vboxnetflt vboxdrv snd_hda_codec_conexant snd_hda_intel snd_hda_codec snd_hwdep lp parport snd_pcm_oss snd_mixer_oss joydev snd_pcm snd_seq_dummy snd_seq_oss arc4 snd_seq_midi snd_rawmidi ecb snd_seq_midi_event snd_seq snd_timer snd_seq_device iwlagn iwlcore snd soundcore sdhci_pci psmouse mac80211 snd_page_alloc sdhci nvidia(P) uvcvideo videodev v4l1_compat cfg80211 serio_raw led_class ricoh_mmc iptable_filter lirc_ite8709 lirc_dev ip_tables x_tables dm_raid45 xor usbhid usb_storage ohci1394 sky2 ieee1394 intel_agp agpgart video output
[  118.684376] Pid: 3009, comm: pm-suspend Tainted: P           2.6.31-15-generic #50-Ubuntu
[  118.684378] Call Trace:
[  118.684384]  [<c014518d>] warn_slowpath_common+0x6d/0xa0
[  118.684387]  [<c0174e74>] ? suspend_test_finish+0x84/0x90
[  118.684391]  [<c0174e74>] ? suspend_test_finish+0x84/0x90
[  118.684394]  [<c0145206>] warn_slowpath_fmt+0x26/0x30
[  118.684397]  [<c0174e74>] suspend_test_finish+0x84/0x90
[  118.684401]  [<c0174c5f>] suspend_devices_and_enter+0x9f/0xd0
[  118.684404]  [<c056ea0c>] ? printk+0x18/0x1c
[  118.684407]  [<c0174d49>] enter_state+0xb9/0xf0
[  118.684411]  [<c017443d>] state_store+0x6d/0xb0
[  118.684414]  [<c01743d0>] ? state_store+0x0/0xb0
[  118.684418]  [<c0311f30>] kobj_attr_store+0x20/0x30
[  118.684422]  [<c0239750>] sysfs_write_file+0x90/0x100
[  118.684427]  [<c01e791a>] vfs_write+0x9a/0x190
[  118.684430]  [<c02396c0>] ? sysfs_write_file+0x0/0x100
[  118.684433]  [<c057333b>] ? do_page_fault+0x19b/0x380
[  118.684437]  [<c01e83dd>] sys_write+0x3d/0x70
[  118.684440]  [<c010336c>] syscall_call+0x7/0xb
[  118.684442] ---[ end trace aa59b8b20e733372 ]---
[  118.684485] PM: Finishing wakeup.
[  118.684486] Restarting tasks ... done.
[  118.750351] sky2 eth0: enabling interface
[  118.750543] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  119.016164] Registered led device: iwl-phy0::radio
[  119.016185] Registered led device: iwl-phy0::assoc
[  119.016204] Registered led device: iwl-phy0::RX
[  119.016223] Registered led device: iwl-phy0::TX
[  119.217198] ADDRCONF(NETDEV_UP): wlan0: link is not ready


---

