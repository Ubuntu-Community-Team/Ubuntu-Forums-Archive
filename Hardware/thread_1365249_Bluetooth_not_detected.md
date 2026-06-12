---
title: "Bluetooth not detected"
date: 2009-12-27
forum: Hardware
---

### Post by sccrstvn93 on 2009-12-27
My bluetooth is not detected on my Studio XPS 16 running ubuntu 9.10 64 bit. 

Here is the output of dmesg:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-16-generic (buildd@crested) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #53-Ubuntu SMP Tue Dec 8 04:02:15 UTC 2009 (Ubuntu 2.6.31-16.53-generic)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-16-generic root=UUID=e7395c96-4d12-45bb-bb4e-6bf3b3cddc12 ro
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009c400 (usable)
[    0.000000]  BIOS-e820: 000000000009c400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf8a1000 (usable)
[    0.000000]  BIOS-e820: 00000000bf8a1000 - 00000000bf8a7000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf8a7000 - 00000000bf9bb000 (usable)
[    0.000000]  BIOS-e820: 00000000bf9bb000 - 00000000bfa0f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfa0f000 - 00000000bfb08000 (usable)
[    0.000000]  BIOS-e820: 00000000bfb08000 - 00000000bfd0f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfd0f000 - 00000000bfd18000 (usable)
[    0.000000]  BIOS-e820: 00000000bfd18000 - 00000000bfd1f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfd1f000 - 00000000bfd63000 (usable)
[    0.000000]  BIOS-e820: 00000000bfd63000 - 00000000bfd9f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfd9f000 - 00000000bfde4000 (usable)
[    0.000000]  BIOS-e820: 00000000bfde4000 - 00000000bfdff000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bfdff000 - 00000000bfe00000 (usable)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-D7FFF write-protect
[    0.000000]   D8000-DBFFF uncachable
[    0.000000]   DC000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 100000000 mask FC0000000 write-back
[    0.000000]   3 base 0FFE00000 mask FFFE00000 write-protect
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] last_pfn = 0xbfe00 max_arch_pfn = 0x400000000
[    0.000000] e820 update range: 0000000000001000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
[    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009c400 (usable)
[    0.000000]  modified: 000000000009c400 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bf8a1000 (usable)
[    0.000000]  modified: 00000000bf8a1000 - 00000000bf8a7000 (reserved)
[    0.000000]  modified: 00000000bf8a7000 - 00000000bf9bb000 (usable)
[    0.000000]  modified: 00000000bf9bb000 - 00000000bfa0f000 (reserved)
[    0.000000]  modified: 00000000bfa0f000 - 00000000bfb08000 (usable)
[    0.000000]  modified: 00000000bfb08000 - 00000000bfd0f000 (reserved)
[    0.000000]  modified: 00000000bfd0f000 - 00000000bfd18000 (usable)
[    0.000000]  modified: 00000000bfd18000 - 00000000bfd1f000 (reserved)
[    0.000000]  modified: 00000000bfd1f000 - 00000000bfd63000 (usable)
[    0.000000]  modified: 00000000bfd63000 - 00000000bfd9f000 (ACPI NVS)
[    0.000000]  modified: 00000000bfd9f000 - 00000000bfde4000 (usable)
[    0.000000]  modified: 00000000bfde4000 - 00000000bfdff000 (ACPI data)
[    0.000000]  modified: 00000000bfdff000 - 00000000bfe00000 (usable)
[    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-00000000bfe00000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 00bfe00000 page 2M
[    0.000000] kernel direct mapping tables up to bfe00000 @ 8000-c000
[    0.000000] init_memory_mapping: 0000000100000000-0000000140000000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0100000000 - 0140000000 page 2M
[    0.000000] kernel direct mapping tables up to 140000000 @ a000-10000
[    0.000000] RAMDISK: 377ac000 - 37fef92f
[    0.000000] ACPI: RSDP 00000000000f7910 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT 00000000bfdf7cd6 00074 (v01 DELL    QA09    06040000  LTP 00000000)
[    0.000000] ACPI: FACP 00000000bfde8000 000F4 (v03 INTEL  CRESTLNE 06040000 ALAN 00000001)
[    0.000000] ACPI: DSDT 00000000bfde9000 06E3C (v02 Intel  CANTIGA  06040000 INTL 20050624)
[    0.000000] ACPI: FACS 00000000bfd9efc0 00040
[    0.000000] ACPI: HPET 00000000bfdfed16 00038 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG 00000000bfdfed4e 0003C (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: APIC 00000000bfdfed8a 00068 (v01 PTLTD  	 APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT 00000000bfdfedf2 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SLIC 00000000bfdfee1a 00176 (v01 DELL    QA09    06040000  LTP 00000000)
[    0.000000] ACPI: OSFR 00000000bfdfef90 00070 (v01 DELL   DELL     06040000 ASL  00000061)
[    0.000000] ACPI: SSDT 00000000bfde7000 00655 (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 00000000bfde6000 00259 (v01  PmRef  Cpu0Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 00000000bfde5000 0020F (v01  PmRef    ApTst 00003000 INTL 20050624)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000140000000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000140000000
[    0.000000]   NODE_DATA [000000000000b000 - 000000000000ffff]
[    0.000000]   bootmap [0000000000010000 -  0000000000037fff] pages 28
[    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0140000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 00019e4ccc]    TEXT DATA BSS ==> [0001000000 - 00019e4ccc]
[    0.000000]   #3 [00377ac000 - 0037fef92f]          RAMDISK ==> [00377ac000 - 0037fef92f]
[    0.000000]   #4 [000009c400 - 0000100000]    BIOS reserved ==> [000009c400 - 0000100000]
[    0.000000]   #5 [00019e5000 - 00019e51d4]              BRK ==> [00019e5000 - 00019e51d4]
[    0.000000]   #6 [0000008000 - 000000a000]          PGTABLE ==> [0000008000 - 000000a000]
[    0.000000]   #7 [000000a000 - 000000b000]          PGTABLE ==> [000000a000 - 000000b000]
[    0.000000] found SMP MP-table at [ffff8800000f79c0] f79c0
[    0.000000]  [ffffea0000000000-ffffea00045fffff] PMD -> [ffff880028600000-ffff88002bdfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00140000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[10] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000001
[    0.000000]     0: 0x00000006 -> 0x0000009c
[    0.000000]     0: 0x00000100 -> 0x000bf8a1
[    0.000000]     0: 0x000bf8a7 -> 0x000bf9bb
[    0.000000]     0: 0x000bfa0f -> 0x000bfb08
[    0.000000]     0: 0x000bfd0f -> 0x000bfd18
[    0.000000]     0: 0x000bfd1f -> 0x000bfd63
[    0.000000]     0: 0x000bfd9f -> 0x000bfde4
[    0.000000]     0: 0x000bfdff -> 0x000bfe00
[    0.000000]     0: 0x00100000 -> 0x00140000
[    0.000000] On node 0 totalpages: 1047256
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 105 pages reserved
[    0.000000]   DMA zone: 3830 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 766841 pages, LIFO batch:31
[    0.000000]   Normal zone: 3584 pages used for memmap
[    0.000000]   Normal zone: 258560 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009c000 - 000000000009d000
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000bf8a1000 - 00000000bf8a7000
[    0.000000] PM: Registered nosave memory: 00000000bf9bb000 - 00000000bfa0f000
[    0.000000] PM: Registered nosave memory: 00000000bfb08000 - 00000000bfd0f000
[    0.000000] PM: Registered nosave memory: 00000000bfd18000 - 00000000bfd1f000
[    0.000000] PM: Registered nosave memory: 00000000bfd63000 - 00000000bfd9f000
[    0.000000] PM: Registered nosave memory: 00000000bfde4000 - 00000000bfdff000
[    0.000000] PM: Registered nosave memory: 00000000bfe00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at bfe00000 (gap: bfe00000:40200000)
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages at ffff880028023000, static data 90720 bytes
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1029231
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-16-generic root=UUID=e7395c96-4d12-45bb-bb4e-6bf3b3cddc12 ro
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.000000] Placing 64MB software IO TLB between ffff880020000000 - ffff880024000000
[    0.000000] software IO TLB at phys 0x20000000 - 0x24000000
[    0.000000] Memory: 4046640k/5242880k available (5315k kernel code, 1053856k absent, 142384k reserved, 3018k data, 660k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] NR_IRQS:4352 nr_irqs:424
[    0.000000] Extended CMOS year: 2000
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2659.446 MHz processor.
[    0.000936] Console: colour VGA+ 80x25
[    0.000939] console [tty0] enabled
[    0.010000] allocated 41943040 bytes of page_cgroup
[    0.010000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.010000] hpet clockevent registered
[    0.010000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.010000] Calibrating delay loop (skipped), value calculated using timer frequency.. 5318.89 BogoMIPS (lpj=26594460)
[    0.010000] Security Framework initialized
[    0.010000] AppArmor: AppArmor initialized
[    0.010000] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.010000] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.010000] Mount-cache hash table entries: 256
[    0.010000] Initializing cgroup subsys ns
[    0.010000] Initializing cgroup subsys cpuacct
[    0.010000] Initializing cgroup subsys memory
[    0.010000] Initializing cgroup subsys freezer
[    0.010000] Initializing cgroup subsys net_cls
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 6144K
[    0.010000] CPU 0/0x0 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 0
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] CPU0: Thermal monitoring enabled (TM2)
[    0.010000] using mwait in idle threads.
[    0.010000] Performance Counters: Core2 events, Intel PMU driver.
[    0.010000] ... version:                 2
[    0.010000] ... bit width:               40
[    0.010000] ... generic counters:        2
[    0.010000] ... value mask:              000000ffffffffff
[    0.010000] ... max period:              000000007fffffff
[    0.010000] ... fixed-purpose counters:  3
[    0.010000] ... counter mask:            0000000700000003
[    0.010000] ACPI: Core revision 20090521
[    0.020055] Setting APIC routing to flat
[    0.020407] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.130536] CPU0: Intel(R) Core(TM)2 Duo CPU     T9550  @ 2.66GHz stepping 0a
[    0.140000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.010000] Initializing CPU#1
[    0.010000] Calibrating delay using timer specific routine.. 5320.08 BogoMIPS (lpj=26600416)
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 6144K
[    0.010000] CPU 1/0x1 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 1
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] CPU1: Thermal monitoring enabled (TM2)
[    0.010000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.291705] CPU1: Intel(R) Core(TM)2 Duo CPU     T9550  @ 2.66GHz stepping 0a
[    0.292175] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.300019] Brought up 2 CPUs
[    0.300056] Total of 2 processors activated (10638.97 BogoMIPS).
[    0.300141] CPU0 attaching sched-domain:
[    0.300143]  domain 0: span 0-1 level MC
[    0.300145]   groups: 0 1
[    0.300149] CPU1 attaching sched-domain:
[    0.300151]  domain 0: span 0-1 level MC
[    0.300152]   groups: 1 0
[    0.300211] Booting paravirtualized kernel on bare hardware
[    0.300211] regulator: core version 0.5
[    0.300211] Time:  5:43:49  Date: 12/27/09
[    0.300211] NET: Registered protocol family 16
[    0.300277] ACPI: bus type pci registered
[    0.300374] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.300414] PCI: Not using MMCONFIG.
[    0.300452] PCI: Using configuration type 1 for base access
[    0.301125] bio: create slab <bio-0> at 0
[    0.301125] ACPI: EC: Look up EC in DSDT
[    0.303806] ACPI: BIOS _OSI(Linux) query ignored
[    0.304745] ACPI: Interpreter enabled
[    0.304783] ACPI: (supports S0 S3 S4 S5)
[    0.304949] ACPI: Using IOAPIC for interrupt routing
[    0.305025] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.310016] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.320461] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.330882] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.333684] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    0.333684] ACPI: EC: driver started in interrupt mode
[    0.333684] ACPI: No dock devices found.
[    0.333684] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.333684] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.333684] pci 0000:00:01.0: PME# disabled
[    0.333684] pci 0000:00:1a.0: reg 20 io port: [0x1800-0x181f]
[    0.333684] pci 0000:00:1a.1: reg 20 io port: [0x1820-0x183f]
[    0.333684] pci 0000:00:1a.2: reg 20 io port: [0x1840-0x185f]
[    0.333684] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfc404800-0xfc404bff]
[    0.333684] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.333684] pci 0000:00:1a.7: PME# disabled
[    0.333684] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfc400000-0xfc403fff]
[    0.333684] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.333684] pci 0000:00:1b.0: PME# disabled
[    0.333684] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.333684] pci 0000:00:1c.0: PME# disabled
[    0.333684] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.333684] pci 0000:00:1c.1: PME# disabled
[    0.333684] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.333684] pci 0000:00:1c.3: PME# disabled
[    0.333684] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.333684] pci 0000:00:1c.5: PME# disabled
[    0.333684] pci 0000:00:1d.0: reg 20 io port: [0x1860-0x187f]
[    0.333684] pci 0000:00:1d.1: reg 20 io port: [0x1880-0x189f]
[    0.333684] pci 0000:00:1d.2: reg 20 io port: [0x18a0-0x18bf]
[    0.333684] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfc404c00-0xfc404fff]
[    0.333684] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.333684] pci 0000:00:1d.7: PME# disabled
[    0.333684] pci 0000:00:1f.2: reg 10 io port: [0x18f0-0x18f7]
[    0.333684] pci 0000:00:1f.2: reg 14 io port: [0x18e4-0x18e7]
[    0.333684] pci 0000:00:1f.2: reg 18 io port: [0x18e8-0x18ef]
[    0.333684] pci 0000:00:1f.2: reg 1c io port: [0x18e0-0x18e3]
[    0.333684] pci 0000:00:1f.2: reg 20 io port: [0x18c0-0x18df]
[    0.333684] pci 0000:00:1f.2: reg 24 32bit mmio: [0xfc404000-0xfc4047ff]
[    0.333684] pci 0000:00:1f.2: PME# supported from D3hot
[    0.333684] pci 0000:00:1f.2: PME# disabled
[    0.333684] pci 0000:00:1f.3: reg 10 64bit mmio: [0x000000-0x0000ff]
[    0.333684] pci 0000:00:1f.3: reg 20 io port: [0x1c00-0x1c1f]
[    0.333684] pci 0000:01:00.0: reg 10 32bit mmio: [0xd0000000-0xdfffffff]
[    0.333684] pci 0000:01:00.0: reg 14 io port: [0x2000-0x20ff]
[    0.333684] pci 0000:01:00.0: reg 18 32bit mmio: [0xcfef0000-0xcfefffff]
[    0.333684] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.333684] pci 0000:01:00.0: supports D1 D2
[    0.333684] pci 0000:01:00.1: reg 10 32bit mmio: [0xcfeec000-0xcfeeffff]
[    0.333684] pci 0000:01:00.1: supports D1 D2
[    0.333684] pci 0000:00:01.0: bridge io port: [0x2000-0x2fff]
[    0.333684] pci 0000:00:01.0: bridge 32bit mmio: [0xcfe00000-0xcfefffff]
[    0.333684] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.333684] pci 0000:00:1c.0: bridge io port: [0x3000-0x3fff]
[    0.333684] pci 0000:00:1c.0: bridge 32bit mmio: [0xf6000000-0xf7ffffff]
[    0.333684] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xf0000000-0xf1ffffff]
[    0.333684] pci 0000:04:00.0: reg 10 64bit mmio: [0xf8000000-0xf8001fff]
[    0.333684] pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
[    0.333684] pci 0000:04:00.0: PME# disabled
[    0.333700] pci 0000:00:1c.1: bridge io port: [0x4000-0x4fff]
[    0.333703] pci 0000:00:1c.1: bridge 32bit mmio: [0xf8000000-0xf9ffffff]
[    0.333709] pci 0000:00:1c.1: bridge 64bit mmio pref: [0xf2000000-0xf3ffffff]
[    0.333752] pci 0000:00:1c.3: bridge io port: [0x5000-0x5fff]
[    0.333756] pci 0000:00:1c.3: bridge 32bit mmio: [0xfa000000-0xfbffffff]
[    0.333761] pci 0000:00:1c.3: bridge 64bit mmio pref: [0xf4000000-0xf5ffffff]
[    0.333986] pci 0000:08:00.0: reg 10 64bit mmio: [0xfc000000-0xfc00ffff]
[    0.334077] pci 0000:08:00.0: PME# supported from D3hot D3cold
[    0.334120] pci 0000:08:00.0: PME# disabled
[    0.334213] pci 0000:00:1c.5: bridge 32bit mmio: [0xfc000000-0xfc0fffff]
[    0.334251] pci 0000:09:01.0: reg 10 32bit mmio: [0xfc100000-0xfc1007ff]
[    0.334297] pci 0000:09:01.0: supports D1 D2
[    0.334299] pci 0000:09:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.334340] pci 0000:09:01.0: PME# disabled
[    0.334407] pci 0000:09:01.1: reg 10 32bit mmio: [0xfc100800-0xfc1008ff]
[    0.334454] pci 0000:09:01.1: supports D1 D2
[    0.334455] pci 0000:09:01.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.334498] pci 0000:09:01.1: PME# disabled
[    0.334568] pci 0000:09:01.2: reg 10 32bit mmio: [0xfc100c00-0xfc100cff]
[    0.334618] pci 0000:09:01.2: supports D1 D2
[    0.334620] pci 0000:09:01.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.334661] pci 0000:09:01.2: PME# disabled
[    0.334731] pci 0000:09:01.3: reg 10 32bit mmio: [0xfc101000-0xfc1010ff]
[    0.334782] pci 0000:09:01.3: supports D1 D2
[    0.334783] pci 0000:09:01.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.334824] pci 0000:09:01.3: PME# disabled
[    0.334892] pci 0000:09:01.4: reg 10 32bit mmio: [0xfc101400-0xfc1014ff]
[    0.334939] pci 0000:09:01.4: supports D1 D2
[    0.334940] pci 0000:09:01.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.334981] pci 0000:09:01.4: PME# disabled
[    0.335067] pci 0000:00:1e.0: transparent bridge
[    0.335108] pci 0000:00:1e.0: bridge 32bit mmio: [0xfc100000-0xfc1fffff]
[    0.335137] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.335232] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    0.335285] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.335361] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.335417] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.335472] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.335518] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    0.349255] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    0.349718] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.350208] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.350670] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.351170] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.351697] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.352162] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.352659] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 *7 11 12 14 15)
[    0.353168] SCSI subsystem initialized
[    0.353210] libata version 3.00 loaded.
[    0.353210] usbcore: registered new interface driver usbfs
[    0.353210] usbcore: registered new interface driver hub
[    0.353210] usbcore: registered new device driver usb
[    0.353210] ACPI: WMI: Mapper loaded
[    0.353210] PCI: Using ACPI for IRQ routing
[    0.380005] Bluetooth: Core ver 2.15
[    0.380045] NET: Registered protocol family 31
[    0.380046] Bluetooth: HCI device and connection manager initialized
[    0.380086] Bluetooth: HCI socket layer initialized
[    0.380124] NetLabel: Initializing
[    0.380160] NetLabel:  domain hash size = 128
[    0.380197] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.380243] NetLabel:  unlabeled traffic allowed by default
[    0.380317] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.380499] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.422260] pnp: PnP ACPI init
[    0.422301] ACPI: bus type pnp registered
[    0.424335] pnp: PnP ACPI: found 10 devices
[    0.424374] ACPI: ACPI bus type pnp unregistered
[    0.424417] system 00:02: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.424460] system 00:04: ioport range 0x400-0x47f has been reserved
[    0.424501] system 00:04: ioport range 0x680-0x69f has been reserved
[    0.424540] system 00:04: ioport range 0x480-0x48f has been reserved
[    0.424579] system 00:04: ioport range 0xffff-0xffff has been reserved
[    0.424618] system 00:04: ioport range 0xffff-0xffff has been reserved
[    0.424657] system 00:04: ioport range 0x1000-0x107f has been reserved
[    0.424696] system 00:04: ioport range 0x1180-0x11ff has been reserved
[    0.424735] system 00:04: ioport range 0x164e-0x164f has been reserved
[    0.424774] system 00:04: ioport range 0xfe00-0xfe00 has been reserved
[    0.424813] system 00:04: ioport range 0x900-0x97f has been reserved
[    0.424855] system 00:09: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.424895] system 00:09: iomem range 0xfed10000-0xfed13fff has been reserved
[    0.424934] system 00:09: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.424974] system 00:09: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.425013] system 00:09: iomem range 0xe0000000-0xefffffff has been reserved
[    0.425052] system 00:09: iomem range 0xfeb00000-0xfeb03fff has been reserved
[    0.425092] system 00:09: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.425131] system 00:09: iomem range 0xfed40000-0xfed44fff has been reserved
[    0.425171] system 00:09: iomem range 0xfed45000-0xfed8ffff has been reserved
[    0.429843] AppArmor: AppArmor Filesystem Enabled
[    0.429934] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.429973] pci 0000:00:01.0:   IO window: 0x2000-0x2fff
[    0.430013] pci 0000:00:01.0:   MEM window: 0xcfe00000-0xcfefffff
[    0.430055] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.430102] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.430145] pci 0000:00:1c.0:   IO window: 0x3000-0x3fff
[    0.430188] pci 0000:00:1c.0:   MEM window: 0xf6000000-0xf7ffffff
[    0.430229] pci 0000:00:1c.0:   PREFETCH window: 0x000000f0000000-0x000000f1ffffff
[    0.430279] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:04
[    0.430317] pci 0000:00:1c.1:   IO window: 0x4000-0x4fff
[    0.430359] pci 0000:00:1c.1:   MEM window: 0xf8000000-0xf9ffffff
[    0.430399] pci 0000:00:1c.1:   PREFETCH window: 0x000000f2000000-0x000000f3ffffff
[    0.430448] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:06
[    0.430488] pci 0000:00:1c.3:   IO window: 0x5000-0x5fff
[    0.430529] pci 0000:00:1c.3:   MEM window: 0xfa000000-0xfbffffff
[    0.430569] pci 0000:00:1c.3:   PREFETCH window: 0x000000f4000000-0x000000f5ffffff
[    0.430617] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:08
[    0.430655] pci 0000:00:1c.5:   IO window: disabled
[    0.430696] pci 0000:00:1c.5:   MEM window: 0xfc000000-0xfc0fffff
[    0.430736] pci 0000:00:1c.5:   PREFETCH window: disabled
[    0.430776] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:09
[    0.430814] pci 0000:00:1e.0:   IO window: disabled
[    0.430854] pci 0000:00:1e.0:   MEM window: 0xfc100000-0xfc1fffff
[    0.430894] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.430938]   alloc irq_desc for 16 on node 0
[    0.430940]   alloc kstat_irqs on node 0
[    0.430943] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.430983] pci 0000:00:01.0: setting latency timer to 64
[    0.430989]   alloc irq_desc for 17 on node 0
[    0.430990]   alloc kstat_irqs on node 0
[    0.430992] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.431033] pci 0000:00:1c.0: setting latency timer to 64
[    0.431038] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.431079] pci 0000:00:1c.1: setting latency timer to 64
[    0.431085]   alloc irq_desc for 19 on node 0
[    0.431086]   alloc kstat_irqs on node 0
[    0.431088] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.431129] pci 0000:00:1c.3: setting latency timer to 64
[    0.431134] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.431175] pci 0000:00:1c.5: setting latency timer to 64
[    0.431180] pci 0000:00:1e.0: setting latency timer to 64
[    0.431183] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.431185] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.431187] pci_bus 0000:01: resource 0 io:  [0x2000-0x2fff]
[    0.431188] pci_bus 0000:01: resource 1 mem: [0xcfe00000-0xcfefffff]
[    0.431190] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.431192] pci_bus 0000:02: resource 0 io:  [0x3000-0x3fff]
[    0.431194] pci_bus 0000:02: resource 1 mem: [0xf6000000-0xf7ffffff]
[    0.431195] pci_bus 0000:02: resource 2 pref mem [0xf0000000-0xf1ffffff]
[    0.431197] pci_bus 0000:04: resource 0 io:  [0x4000-0x4fff]
[    0.431199] pci_bus 0000:04: resource 1 mem: [0xf8000000-0xf9ffffff]
[    0.431201] pci_bus 0000:04: resource 2 pref mem [0xf2000000-0xf3ffffff]
[    0.431202] pci_bus 0000:06: resource 0 io:  [0x5000-0x5fff]
[    0.431204] pci_bus 0000:06: resource 1 mem: [0xfa000000-0xfbffffff]
[    0.431206] pci_bus 0000:06: resource 2 pref mem [0xf4000000-0xf5ffffff]
[    0.431208] pci_bus 0000:08: resource 1 mem: [0xfc000000-0xfc0fffff]
[    0.431209] pci_bus 0000:09: resource 1 mem: [0xfc100000-0xfc1fffff]
[    0.431211] pci_bus 0000:09: resource 3 io:  [0x00-0xffff]
[    0.431213] pci_bus 0000:09: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.431235] NET: Registered protocol family 2
[    0.431397] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.432300] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.435501] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.436019] TCP: Hash tables configured (established 524288 bind 65536)
[    0.436058] TCP reno registered
[    0.436190] NET: Registered protocol family 1
[    0.436975] Trying to unpack rootfs image as initramfs...
[    0.502284] Switched to high resolution mode on CPU 1
[    0.510024] Switched to high resolution mode on CPU 0
[    0.589566] Freeing initrd memory: 8462k freed
[    0.592631] Simple Boot Flag at 0x36 set to 0x1
[    0.592824] Scanning for low memory corruption every 60 seconds
[    0.592980] audit: initializing netlink socket (disabled)
[    0.593031] type=2000 audit(1261892629.592:1): initialized
[    0.600664] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.601784] VFS: Disk quotas dquot_6.5.2
[    0.601863] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.602325] fuse init (API version 7.12)
[    0.602426] msgmni has been set to 7920
[    0.602624] alg: No test for stdrng (krng)
[    0.602667] io scheduler noop registered
[    0.602704] io scheduler anticipatory registered
[    0.602742] io scheduler deadline registered
[    0.602806] io scheduler cfq registered (default)
[    0.602988] pci 0000:01:00.0: Boot video device
[    0.603104]   alloc irq_desc for 24 on node 0
[    0.603106]   alloc kstat_irqs on node 0
[    0.603114] pcieport-driver 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.603119] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    0.603233]   alloc irq_desc for 25 on node 0
[    0.603234]   alloc kstat_irqs on node 0
[    0.603241] pcieport-driver 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.603250] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.603382]   alloc irq_desc for 26 on node 0
[    0.603383]   alloc kstat_irqs on node 0
[    0.603390] pcieport-driver 0000:00:1c.1: irq 26 for MSI/MSI-X
[    0.603398] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    0.603529]   alloc irq_desc for 27 on node 0
[    0.603530]   alloc kstat_irqs on node 0
[    0.603537] pcieport-driver 0000:00:1c.3: irq 27 for MSI/MSI-X
[    0.603545] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    0.603674]   alloc irq_desc for 28 on node 0
[    0.603676]   alloc kstat_irqs on node 0
[    0.603682] pcieport-driver 0000:00:1c.5: irq 28 for MSI/MSI-X
[    0.603691] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    0.603776] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.603953] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.700057] ACPI: AC Adapter [ADP1] (on-line)
[    0.700140] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.700188] ACPI: Power Button [PWRF]
[    0.700272] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.700319] ACPI: Power Button [PWRB]
[    0.700389] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.700436] ACPI: Sleep Button [SLPB]
[    0.700506] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[    0.701277] ACPI: Lid Switch [LID0]
[    0.702038] ACPI: SSDT 00000000bfd1ac20 002A7 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.702552] ACPI: SSDT 00000000bfd18620 00575 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.704539] Monitor-Mwait will be used to enter C-1 state
[    0.704557] Monitor-Mwait will be used to enter C-2 state
[    0.704573] Monitor-Mwait will be used to enter C-3 state
[    0.704579] Marking TSC unstable due to TSC halts in idle
[    0.704640] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    0.704821] processor LNXCPU:00: registered as cooling_device0
[    0.704862] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.705340] ACPI: SSDT 00000000bfd19ca0 001CF (v01  PmRef    ApIst 00003000 INTL 20050624)
[    0.705752] ACPI: SSDT 00000000bfd19f20 0008D (v01  PmRef    ApCst 00003000 INTL 20050624)
[    0.706670] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    0.706844] processor LNXCPU:01: registered as cooling_device1
[    0.706886] ACPI: Processor [CPU1] (supports 8 throttling states)
[    0.710743] thermal LNXTHERM:01: registered as thermal_zone0
[    0.710840] ACPI: Thermal Zone [TZ00] (62 C)
[    0.712742] thermal LNXTHERM:02: registered as thermal_zone1
[    0.712788] ACPI: Thermal Zone [TZ01] (42 C)
[    0.714803] thermal LNXTHERM:03: registered as thermal_zone2
[    0.714847] ACPI: Thermal Zone [TZ02] (50 C)
[    0.715758] Linux agpgart interface v0.103
[    0.715802] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.716741] brd: module loaded
[    0.717106] loop: module loaded
[    0.717194] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.717320] ahci 0000:00:1f.2: version 3.0
[    0.717330] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.717399]   alloc irq_desc for 29 on node 0
[    0.717400]   alloc kstat_irqs on node 0
[    0.717407] ahci 0000:00:1f.2: irq 29 for MSI/MSI-X
[    0.717474] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    0.717522] ahci 0000:00:1f.2: flags: 64bit ncq sntf led clo pmp pio slum part 
[    0.717570] ahci 0000:00:1f.2: setting latency timer to 64
[    0.717849] scsi0 : ahci
[    0.717938] scsi1 : ahci
[    0.718014] scsi2 : ahci
[    0.718088] scsi3 : ahci
[    0.718166] scsi4 : ahci
[    0.718242] scsi5 : ahci
[    0.718307] ata1: SATA max UDMA/133 abar m2048@0xfc404000 port 0xfc404100 irq 29
[    0.718409] ata2: SATA max UDMA/133 abar m2048@0xfc404000 port 0xfc404180 irq 29
[    0.718455] ata3: DUMMY
[    0.718493] ata4: DUMMY
[    0.718531] ata5: SATA max UDMA/133 abar m2048@0xfc404000 port 0xfc404300 irq 29
[    0.718578] ata6: SATA max UDMA/133 abar m2048@0xfc404000 port 0xfc404380 irq 29
[    0.719260] Fixed MDIO Bus: probed
[    0.719353] PPP generic driver version 2.4.2
[    0.719449] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.719530] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    0.719578] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.719581] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.719658] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.723613] ehci_hcd 0000:00:1a.7: debug port 1
[    0.723656] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.723667] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xfc404800
[    0.740024] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.740169] usb usb1: configuration #1 chosen from 1 choice
[    0.740229] hub 1-0:1.0: USB hub found
[    0.740273] hub 1-0:1.0: 6 ports detected
[    0.740378]   alloc irq_desc for 23 on node 0
[    0.740380]   alloc kstat_irqs on node 0
[    0.740383] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.740431] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.740434] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.740494] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.744457] ehci_hcd 0000:00:1d.7: debug port 1
[    0.744500] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.744510] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfc404c00
[    0.751300] ACPI: Battery Slot [BAT0] (battery present)
[    0.760010] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.760094] usb usb2: configuration #1 chosen from 1 choice
[    0.760183] hub 2-0:1.0: USB hub found
[    0.760246] hub 2-0:1.0: 6 ports detected
[    0.760341] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.760392] uhci_hcd: USB Universal Host Controller Interface driver
[    0.760483] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.760528] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.760531] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.760623] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.760749] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001800
[    0.760843] usb usb3: configuration #1 chosen from 1 choice
[    0.760903] hub 3-0:1.0: USB hub found
[    0.760946] hub 3-0:1.0: 2 ports detected
[    0.761041]   alloc irq_desc for 21 on node 0
[    0.761043]   alloc kstat_irqs on node 0
[    0.761046] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.761090] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.761093] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.761157] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.761250] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001820
[    0.761348] usb usb4: configuration #1 chosen from 1 choice
[    0.761406] hub 4-0:1.0: USB hub found
[    0.761448] hub 4-0:1.0: 2 ports detected
[    0.761594] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    0.761639] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.761642] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.761702] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.761768] uhci_hcd 0000:00:1a.2: irq 19, io base 0x00001840
[    0.761899] usb usb5: configuration #1 chosen from 1 choice
[    0.761956] hub 5-0:1.0: USB hub found
[    0.761998] hub 5-0:1.0: 2 ports detected
[    0.762095] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.762140] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.762142] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.762231] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.762316] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001860
[    0.762411] usb usb6: configuration #1 chosen from 1 choice
[    0.762468] hub 6-0:1.0: USB hub found
[    0.762512] hub 6-0:1.0: 2 ports detected
[    0.762613] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.762657] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.762660] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.762748] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.762829] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001880
[    0.762925] usb usb7: configuration #1 chosen from 1 choice
[    0.762983] hub 7-0:1.0: USB hub found
[    0.763026] hub 7-0:1.0: 2 ports detected
[    0.763117]   alloc irq_desc for 18 on node 0
[    0.763118]   alloc kstat_irqs on node 0
[    0.763121] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.763166] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.763169] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.763231] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.763302] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
[    0.763396] usb usb8: configuration #1 chosen from 1 choice
[    0.763486] hub 8-0:1.0: USB hub found
[    0.763530] hub 8-0:1.0: 2 ports detected
[    0.763639] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.778337] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.778380] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.778459] mice: PS/2 mouse device common for all mice
[    0.778586] rtc_cmos 00:06: RTC can wake from S4
[    0.778646] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.778709] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.778817] device-mapper: uevent: version 1.0.3
[    0.778938] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.779035] device-mapper: multipath: version 1.1.0 loaded
[    0.779077] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.779290] cpuidle: using governor ladder
[    0.779419] cpuidle: using governor menu
[    0.779738] TCP cubic registered
[    0.779865] NET: Registered protocol family 10
[    0.780214] lo: Disabled Privacy Extensions
[    0.780457] NET: Registered protocol family 17
[    0.780516] Bluetooth: L2CAP ver 2.13
[    0.780555] Bluetooth: L2CAP socket layer initialized
[    0.780596] Bluetooth: SCO (Voice Link) ver 0.6
[    0.780635] Bluetooth: SCO socket layer initialized
[    0.780714] Bluetooth: RFCOMM TTY layer initialized
[    0.780757] Bluetooth: RFCOMM socket layer initialized
[    0.780796] Bluetooth: RFCOMM ver 1.11
[    0.781398] PM: Resume from disk failed.
[    0.781407] registered taskstats version 1
[    0.782193]   Magic number: 5:279:720
[    0.782242] block loop0: hash matches
[    0.782350] rtc_cmos 00:06: setting system clock to 2009-12-27 05:43:50 UTC (1261892630)
[    0.782403] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.782443] EDD information not available.
[    0.783588] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    1.000085] Clocksource tsc unstable (delta = -204629187 ns)
[    1.070095] ata6: SATA link down (SStatus 0 SControl 300)
[    1.070160] ata5: SATA link down (SStatus 0 SControl 300)
[    1.250149] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.250210] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.264847] ata2.00: ATAPI: TSSTcorp DVD+/-RW TS-T633A, D600, max UDMA/100
[    1.264903] ata2.00: applying bridge limits
[    1.278445] ata2.00: configured for UDMA/100
[    1.289156] ata1.00: ATA-8: ST9500420ASG, 0003SDM1, max UDMA/133
[    1.289202] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.291874] ata1.00: configured for UDMA/133
[    1.292053] scsi 0:0:0:0: Direct-Access     ATA      ST9500420ASG     0003 PQ: 0 ANSI: 5
[    1.292192] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.292204] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.292235] sd 0:0:0:0: [sda] Write Protect is off
[    1.292237] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.292254] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.292345]  sda:
[    1.294869] scsi 1:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-T633A D600 PQ: 0 ANSI: 5
[    1.298107]  sda1 sda2 <
[    1.300043] usb 1-6: new high speed USB device using ehci_hcd and address 4
[    1.303679] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.303733] Uniform CD-ROM driver Revision: 3.20
[    1.303855] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.303895] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.313859]  sda5 sda6 sda7 >
[    1.335703] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.335805] Freeing unused kernel memory: 660k freed
[    1.336027] Write protecting the kernel read-only data: 7584k
[    1.389665] ramzswap: disk size set to 1013940 kB
[    1.411782] tg3.c:v3.99 (April 20, 2009)
[    1.411996] tg3 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.412048] tg3 0000:08:00.0: setting latency timer to 64
[    1.444019] tg3 0000:08:00.0: PME# disabled
[    1.455423] Adding 1013936k swap on /dev/ramzswap0.  Priority:100 extents:1 across:1013936k SSD
[    1.475536] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/device:02/input/input6
[    1.475615] ACPI: Video Device [M86] (multi-head: yes  rom: no  post: no)
[    1.477688] ohci1394 0000:09:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.532071] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[fc100000-fc1007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    1.546206] usb 1-6: configuration #1 chosen from 1 choice
[    1.822589] usb 3-1: new full speed USB device using uhci_hcd and address 2
[    2.000900] usb 3-1: configuration #1 chosen from 1 choice
[    2.002875] hub 3-1:1.0: USB hub found
[    2.004840] hub 3-1:1.0: 3 ports detected
[    2.290108] usb 4-1: new full speed USB device using uhci_hcd and address 2
[    2.468396] usb 4-1: configuration #1 chosen from 1 choice
[    2.476794] usbcore: registered new interface driver hiddev
[    2.478613] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/input/input7
[    2.478707] generic-usb 0003:046D:C526.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1a.1-1/input0
[    2.484436] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.1/input/input8
[    2.484575] generic-usb 0003:046D:C526.0002: input,hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1a.1-1/input1
[    2.484631] usbcore: registered new interface driver usbhid
[    2.484671] usbhid: v2.6:USB HID core driver
[    2.553841] usb 3-1.1: new full speed USB device using uhci_hcd and address 3
[    2.674895] usb 3-1.1: configuration #1 chosen from 1 choice
[    2.681108] input: HID 413c:8157 as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.1/3-1.1:1.0/input/input9
[    2.681187] generic-usb 0003:413C:8157.0003: input,hidraw2: USB HID v1.11 Keyboard [HID 413c:8157] on usb-0000:00:1a.0-1.1/input0
[    2.763841] usb 3-1.2: new full speed USB device using uhci_hcd and address 4
[    2.781413] eth0: Tigon3 [partno(BCM95784M) rev 5784100] (PCI Express) MAC address 00:22:19:f5:9d:b5
[    2.781461] eth0: attached PHY is 5784 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    2.781508] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    2.781548] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    2.855327] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0000000000000000]
[    2.860295] xor: automatically using best checksumming function: generic_sse
[    2.902525]    generic_sse: 10640.800 MB/sec
[    2.902569] xor: using function: generic_sse (10640.800 MB/sec)
[    2.904103] device-mapper: dm-raid45: initialized v0.2594b
[    2.931914] usb 3-1.2: configuration #1 chosen from 1 choice
[    2.939187] input: HID 413c:8158 as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2/3-1.2:1.0/input/input10
[    2.939282] generic-usb 0003:413C:8158.0004: input,hidraw3: USB HID v1.11 Mouse [HID 413c:8158] on usb-0000:00:1a.0-1.2/input0
[    3.095421] PM: Starting manual resume from disk
[    3.095467] PM: Resume from partition 8:5
[    3.095468] PM: Checking hibernation image.
[    3.095772] PM: Resume from disk failed.
[    3.112608] EXT4-fs (sda1): barriers enabled
[    3.126274] kjournald2 starting: pid 488, dev sda1:8, commit interval 5 seconds
[    3.126341] EXT4-fs (sda1): delayed allocation enabled
[    3.126453] EXT4-fs: file extents enabled
[    3.127847] EXT4-fs: mballoc enabled
[    3.127893] EXT4-fs (sda1): mounted filesystem with ordered data mode
[   19.913572] udev: starting version 147
[   19.927167] lp: driver loaded but no devices found
[   19.928743] Adding 5855652k swap on /dev/sda5.  Priority:-1 extents:1 across:5855652k 
[   19.987846] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   19.987851] Disabling lock debugging due to kernel taint
[   19.999091] [fglrx] Maximum main memory to use for locked dma buffers: 3798 MBytes.
[   19.999311] ricoh-mmc: Ricoh MMC Controller disabling driver
[   19.999313] ricoh-mmc: Copyright(c) Philip Langdale
[   19.999320] [fglrx]   vendor: 1002 device: 9593 count: 1
[   19.999663] [fglrx] ioport: bar 1, base 0x2000, size: 0x100
[   19.999676] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.999680] pci 0000:01:00.0: setting latency timer to 64
[   19.999814] [fglrx] Kernel PAT support is enabled
[   19.999830] [fglrx] module loaded - fglrx 8.66.10 [Sep  3 2009] with 1 minors
[   20.042664] sdhci: Secure Digital Host Controller Interface driver
[   20.042667] sdhci: Copyright(c) Pierre Ossman
[   20.043507] ricoh-mmc: Ricoh MMC controller found at 0000:09:01.2 [1180:0843] (rev 12)
[   20.043523] ricoh-mmc: Controller is now disabled.
[   20.065247] sdhci-pci 0000:09:01.1: SDHCI controller found [1180:0822] (rev 22)
[   20.065262] sdhci-pci 0000:09:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   20.067379] Registered led device: mmc0::
[   20.068411] mmc0: SDHCI controller on PCI [0000:09:01.1] using DMA
[   20.079225]   alloc irq_desc for 22 on node 0
[   20.079228]   alloc kstat_irqs on node 0
[   20.079233] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   20.079269] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   20.080932] ip_tables: (C) 2000-2006 Netfilter Core Team
[   20.081775] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   20.096851] Linux video capture interface: v2.00
[   20.098795] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_2M (0c45:63fa)
[   20.122405] input: Dell WMI hotkeys as /devices/virtual/input/input11
[   20.135084] input: Laptop_Integrated_Webcam_2M as /devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0/input/input12
[   20.135128] usbcore: registered new interface driver uvcvideo
[   20.135130] USB Video Class driver (v0.1.0)
[   20.140074] cfg80211: Calling CRDA to update world regulatory domain
[   20.169969] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   20.169972] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   20.171533] iwlagn 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   20.171541] iwlagn 0000:04:00.0: setting latency timer to 64
[   20.171573] iwlagn 0000:04:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
[   20.195746] cfg80211: World regulatory domain updated:
[   20.195749] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   20.195751] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.195753] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.195755] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.195757] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.195759] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.196883] EXT4-fs (sda1): internal journal on sda1:8
[   20.209832] iwlagn 0000:04:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   20.209887]   alloc irq_desc for 30 on node 0
[   20.209889]   alloc kstat_irqs on node 0
[   20.209905] iwlagn 0000:04:00.0: irq 30 for MSI/MSI-X
[   20.226505] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input13
[   20.228624] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   20.241153] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[   20.241210] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[   20.241254] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input16
[   20.241930] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   20.241969] HDA Intel 0000:01:00.1: setting latency timer to 64
[   20.747886] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04731/0xa40000
[   20.799481] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input17
[   21.137881] EXT4-fs (sda6): barriers enabled
[   21.146231] kjournald2 starting: pid 1015, dev sda6:8, commit interval 5 seconds
[   21.146718] EXT4-fs (sda6): internal journal on sda6:8
[   21.146723] EXT4-fs (sda6): delayed allocation enabled
[   21.146727] EXT4-fs: file extents enabled
[   21.147496] EXT4-fs: mballoc enabled
[   21.147507] EXT4-fs (sda6): mounted filesystem with ordered data mode
[   21.289227] iwlagn 0000:04:00.0: firmware: requesting iwlwifi-5000-2.ucode
[   21.303405] type=1505 audit(1261892651.020:2): operation="profile_load" pid=1200 name=/usr/share/gdm/guest-session/Xsession
[   21.304675] type=1505 audit(1261892651.020:3): operation="profile_load" pid=1207 name=/sbin/dhclient3
[   21.305189] type=1505 audit(1261892651.020:4): operation="profile_load" pid=1207 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   21.305466] type=1505 audit(1261892651.020:5): operation="profile_load" pid=1207 name=/usr/lib/connman/scripts/dhclient-script
[   21.307697] type=1505 audit(1261892651.020:6): operation="profile_load" pid=1208 name=/usr/bin/evince
[   21.316044] type=1505 audit(1261892651.030:7): operation="profile_load" pid=1208 name=/usr/bin/evince-previewer
[   21.321019] type=1505 audit(1261892651.030:8): operation="profile_load" pid=1208 name=/usr/bin/evince-thumbnailer
[   21.325995] iwlagn 0000:04:00.0: loaded firmware version 8.24.2.12
[   21.327458] type=1505 audit(1261892651.040:9): operation="profile_load" pid=1211 name=/usr/lib/cups/backend/cups-pdf
[   21.328079] type=1505 audit(1261892651.040:10): operation="profile_load" pid=1211 name=/usr/sbin/cupsd
[   21.330076] type=1505 audit(1261892651.040:11): operation="profile_load" pid=1213 name=/usr/sbin/tcpdump
[   21.541289] EXT4-fs (sda7): barriers enabled
[   21.542692] kjournald2 starting: pid 1336, dev sda7:8, commit interval 5 seconds
[   21.552892] Registered led device: iwl-phy0::radio
[   21.552905] Registered led device: iwl-phy0::assoc
[   21.552931] Registered led device: iwl-phy0::RX
[   21.552943] Registered led device: iwl-phy0::TX
[   21.561275] EXT4-fs (sda7): internal journal on sda7:8
[   21.561278] EXT4-fs (sda7): delayed allocation enabled
[   21.561281] EXT4-fs: file extents enabled
[   21.565142] EXT4-fs: mballoc enabled
[   21.565151] EXT4-fs (sda7): mounted filesystem with ordered data mode
[   21.593231] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.594285] tg3 0000:08:00.0: PME# disabled
[   21.594590]   alloc irq_desc for 31 on node 0
[   21.594592]   alloc kstat_irqs on node 0
[   21.594607] tg3 0000:08:00.0: irq 31 for MSI/MSI-X
[   21.741327] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.004672]   alloc irq_desc for 32 on node 0
[   22.004675]   alloc kstat_irqs on node 0
[   22.004684] fglrx_pci 0000:01:00.0: irq 32 for MSI/MSI-X
[   22.005941] [fglrx] Firegl kernel thread PID: 1545
[   22.426023] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   22.426026] vboxdrv: Successfully done.
[   22.426027] vboxdrv: Found 2 processor cores.
[   22.426073] VBoxDrv: dbg - g_abExecMemory=ffffffffa04f7480
[   22.426093] vboxdrv: fAsync=0 offMin=0x1a4 offMax=0x1284
[   22.426126] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   22.426128] vboxdrv: Successfully loaded version 3.0.12 (interface 0x00110000).
[   22.481655] [fglrx] Gart USWC size:1236 M.
[   22.481658] [fglrx] Gart cacheable size:491 M.
[   22.481662] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   22.481664] [fglrx] Reserved FB block: Unshared offset:fc21000, size:3df000 
[   22.481666] [fglrx] Reserved FB block: Unshared offset:1fffb000, size:5000 
[   22.630507] VBoxNetFlt: dbg - g_abExecMemory=ffffffffa0696220
[   22.632472] VBoxNetAdp: dbg - g_abExecMemory=ffffffffa06afb20
[   22.742346] ppdev: user-space parallel port driver
[   25.220753] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   54.928373] Registered led device: iwl-phy0::radio
[   54.928419] Registered led device: iwl-phy0::assoc
[   54.928470] Registered led device: iwl-phy0::RX
[   54.928507] Registered led device: iwl-phy0::TX
[   54.974444] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   58.487490] Registered led device: iwl-phy0::radio
[   58.487537] Registered led device: iwl-phy0::assoc
[   58.487581] Registered led device: iwl-phy0::RX
[   58.487634] Registered led device: iwl-phy0::TX
[   58.533755] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   69.975128] wlan0: authenticate with AP 00:1e:e5:50:d1:5f
[   69.977237] wlan0: authenticated
[   69.977244] wlan0: associate with AP 00:1e:e5:50:d1:5f
[   69.980882] wlan0: RX AssocResp from 00:1e:e5:50:d1:5f (capab=0x401 status=0 aid=2)
[   69.980891] wlan0: associated
[   69.985558] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   78.032459] iwlagn 0000:04:00.0: iwl_tx_agg_start on ra = 00:1e:e5:50:d1:5f tid = 0
[   80.512517] wlan0: no IPv6 routers present
[  502.840923] iwlagn 0000:04:00.0: iwl_tx_agg_start on ra = 00:1e:e5:50:d1:5f tid = 1
[ 1104.676248] [fglrx] ACPI output device 110 to be enabled
[ 1106.458090] [fglrx] ACPI output device 110 to be enabled
```

and lspci:

```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility HD 3670
01:00.1 Audio device: ATI Technologies Inc RV635 Audio device [Radeon HD 3600 Series]
04:00.0 Network controller: Intel Corporation PRO/Wireless 5300 AGN [Shiloh] Network Connection
08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
09:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
09:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
09:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
09:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
```

Thanks for the help.

---

### Post by efflandt on 2009-12-27
Do you have the Bluetooth "option" on your laptop?  Just because you have an LED for it does not necessarily mean it is installed.

Do your wireless keyboard and mouse work?  If not then check alternate USB settings in CMOS setup (BIOS).

If you are thinking that you can use the Logitech Bluetooth for other things, the Logitech USB Bluetooth is not pci (would not show up in lspci) and it is specific to the keyboard and mouse (for security reasons), so it will not work for other things.  However, Bluetooth keyboard and mouse can work with standard Bluetooth.

I have a Logitech Bluetooth combo keyboard/mousepad and it automatically worked in Ubuntu 9.10 on various computers without doing anything.  But I learned long ago that its Bluetooth USB dongle will not communicate with my Bluetooth headset or mobile phone or anything.  I do have a Motorola USB Bluetooth dongle that does work for other things.

---

### Post by sccrstvn93 on 2009-12-27
Yes, I have bluetooth; it worked in windows.

Yes, my wireless mouse works, but it has a dongle.

---

### Post by sccrstvn93 on 2009-12-28
bump

---

### Post by sccrstvn93 on 2010-01-01
anyone?

---

### Post by ReMG on 2010-01-03
I've just installed Ubuntu 9.10 (Karmic Koala) in my ThinkPad SL400, and have the same problem... The system just doesn't recognize my bluetooth hardware..
When I go to Bluetooth Preferences, this message is shown: ***"No Bluetooth adapters present. Your computer does not have any Bluetooth adapters plugged in."***

In Windows XP it works without doing anything special, and connects with other ThinPad, and phones very well.

Thanks for help!

---

### Post by Harutyun Dr. on 2010-01-24
Hello

Running Ubuntu 9.10 (karmic) Kernel Linux 2.6.31-17-generic on HP 6730s and having the same issue. Bluetooth worked fine under windows vista. Googled a lot but nothing helped... :confused: :confused: :confused:

---

### Post by Harutyun Dr. on 2010-01-25
I have fixed it! Just remembered that on my vista I could enable/disable wifi/bluetooth in Wireless Assistant separately and thought that enabling bluetooth under vista may somehow activate bluetooth device. And that worked! After rebooting to Ubuntu I saw bluetooth icon with all functions enabled. Haven't used it yet but I think it should work now.

---

