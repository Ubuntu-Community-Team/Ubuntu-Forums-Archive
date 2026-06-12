---
title: "usb hard drive problems: &quot;reset high speed USB device using ehci_hcd&quot;"
date: 2009-11-26
forum: Hardware
---

### Post by jon.reeve on 2009-11-26
Every time I try to transfer a file from my USB hard drive, it crashes nautilus, the transfer hangs, and I get this message: 

usb 1-8: reset high speed USB device using ehci_hcd and address 7

Does anyone know what might be going on here?

---

### Post by lavinog on 2009-11-27
I am getting this too.
It looks like a ehci bug.
You should post your dmesg output.

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-15-generic (buildd@yellow) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #50-Ubuntu SMP Tue Nov 10 14:53:52 UTC 2009 (Ubuntu 2.6.31-15.50-generic)
[    0.000000] Command line: root=UUID=84cadf52-515e-47d7-a0c7-a12bb53ea9a3 ro verbose vga=791 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfde0000 (usable)
[    0.000000]  BIOS-e820: 00000000cfde0000 - 00000000cfde3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cfde3000 - 00000000cfdf0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cfdf0000 - 00000000cfe00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0x130000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 base 0080000000 mask FFC0000000 write-back
[    0.000000]   2 base 00C0000000 mask FFF0000000 write-back
[    0.000000]   3 base 00CFE00000 mask FFFFE00000 uncachable
[    0.000000]   4 base 0100000000 mask FFE0000000 write-back
[    0.000000]   5 base 0120000000 mask FFF0000000 write-back
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000130000000 aka 4864M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000cfe00000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xcfde0 max_arch_pfn = 0x400000000
[    0.000000] e820 update range: 0000000000001000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
[    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000cfde0000 (usable)
[    0.000000]  modified: 00000000cfde0000 - 00000000cfde3000 (ACPI NVS)
[    0.000000]  modified: 00000000cfde3000 - 00000000cfdf0000 (ACPI data)
[    0.000000]  modified: 00000000cfdf0000 - 00000000cfe00000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-00000000cfde0000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 00cfc00000 page 2M
[    0.000000]  00cfc00000 - 00cfde0000 page 4k
[    0.000000] kernel direct mapping tables up to cfde0000 @ 8000-e000
[    0.000000] init_memory_mapping: 0000000100000000-0000000130000000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0100000000 - 0130000000 page 2M
[    0.000000] kernel direct mapping tables up to 130000000 @ c000-12000
[    0.000000] RAMDISK: 377f1000 - 37fef728
[    0.000000] ACPI: RSDP 00000000000f7140 00014 (v00 GBT   )
[    0.000000] ACPI: RSDT 00000000cfde3000 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: FACP 00000000cfde3040 00074 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: DSDT 00000000cfde30c0 06515 (v01 GBT    GBTUACPI 00001000 MSFT 03000000)
[    0.000000] ACPI: FACS 00000000cfde0000 00040
[    0.000000] ACPI: SSDT 00000000cfde96c0 0028A (v01 PTLTD  POWERNOW 00000001  LTP 00000001)
[    0.000000] ACPI: HPET 00000000cfde9980 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 00000098)
[    0.000000] ACPI: MCFG 00000000cfde99c0 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: APIC 00000000cfde9600 00084 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000130000000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000130000000
[    0.000000]   NODE_DATA [000000000000d000 - 0000000000011fff]
[    0.000000]   bootmap [0000000000012000 -  0000000000037fff] pages 26
[    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0130000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 00019e4ccc]    TEXT DATA BSS ==> [0001000000 - 00019e4ccc]
[    0.000000]   #3 [00377f1000 - 0037fef728]          RAMDISK ==> [00377f1000 - 0037fef728]
[    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #5 [00019e5000 - 00019e50ce]              BRK ==> [00019e5000 - 00019e50ce]
[    0.000000]   #6 [0000008000 - 000000c000]          PGTABLE ==> [0000008000 - 000000c000]
[    0.000000]   #7 [000000c000 - 000000d000]          PGTABLE ==> [000000c000 - 000000d000]
[    0.000000] found SMP MP-table at [ffff8800000f57f0] f57f0
[    0.000000]  [ffffea0000000000-ffffea00043fffff] PMD -> [ffff880028600000-ffff88002bffffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00130000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000001
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000cfde0
[    0.000000]     0: 0x00100000 -> 0x00130000
[    0.000000] On node 0 totalpages: 1047930
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 104 pages reserved
[    0.000000]   DMA zone: 3834 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 833048 pages, LIFO batch:31
[    0.000000]   Normal zone: 2688 pages used for memmap
[    0.000000]   Normal zone: 193920 pages, LIFO batch:31
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cfde0000 - 00000000cfde3000
[    0.000000] PM: Registered nosave memory: 00000000cfde3000 - 00000000cfdf0000
[    0.000000] PM: Registered nosave memory: 00000000cfdf0000 - 00000000cfe00000
[    0.000000] PM: Registered nosave memory: 00000000cfe00000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at cfe00000 (gap: cfe00000:10200000)
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages at ffff880028022000, static data 90720 bytes
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1030802
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: root=UUID=84cadf52-515e-47d7-a0c7-a12bb53ea9a3 ro verbose vga=791 
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ 204e000000 size 32 MB
[    0.000000] Aperture beyond 4GB. Ignoring.
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ 20000000
[    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000024000000
[    0.000000] Memory: 4047732k/4980736k available (5315k kernel code, 789016k absent, 143988k reserved, 3018k data, 660k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] NR_IRQS:4352 nr_irqs:440
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2505.262 MHz processor.
[    0.000019] Console: colour dummy device 80x25
[    0.000021] console [tty0] enabled
[    0.010000] allocated 41943040 bytes of page_cgroup
[    0.010000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.010000] hpet clockevent registered
[    0.010000]   alloc irq_desc for 24 on node 0
[    0.010000]   alloc kstat_irqs on node 0
[    0.010000] HPET: 4 timers in total, 1 timers will be used for per-cpu timer
[    0.010007] Calibrating delay loop (skipped), value calculated using timer frequency.. 5010.52 BogoMIPS (lpj=25052620)
[    0.010034] Security Framework initialized
[    0.010055] AppArmor: AppArmor initialized
[    0.010371] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.012716] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.013875] Mount-cache hash table entries: 256
[    0.014014] Initializing cgroup subsys ns
[    0.014019] Initializing cgroup subsys cpuacct
[    0.014024] Initializing cgroup subsys memory
[    0.014032] Initializing cgroup subsys freezer
[    0.014036] Initializing cgroup subsys net_cls
[    0.014049] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.014053] CPU: L2 Cache: 512K (64 bytes/line)
[    0.014057] CPU 0/0x0 -> Node 0
[    0.014060] tseg: 00cfe00000
[    0.014062] CPU: Physical Processor ID: 0
[    0.014064] CPU: Processor Core ID: 0
[    0.014068] mce: CPU supports 5 MCE banks
[    0.014078] using C1E aware idle routine
[    0.014081] Performance Counters: AMD PMU driver.
[    0.014087] ... version:                 0
[    0.014090] ... bit width:               48
[    0.014092] ... generic counters:        4
[    0.014095] ... value mask:              0000ffffffffffff
[    0.014099] ... max period:              00007fffffffffff
[    0.014102] ... fixed-purpose counters:  0
[    0.014104] ... counter mask:            000000000000000f
[    0.015399] ACPI: Core revision 20090521
[    0.030040] Setting APIC routing to flat
[    0.030575] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.130383] CPU0: AMD Athlon(tm) Dual Core Processor 4850e stepping 02
[    0.140000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.010000] Initializing CPU#1
[    0.010000] Calibrating delay using timer specific routine.. 5010.70 BogoMIPS (lpj=25053527)
[    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.010000] CPU 1/0x1 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 1
[    0.010000] mce: CPU supports 5 MCE banks
[    0.010000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.290360] CPU1: AMD Athlon(tm) Dual Core Processor 4850e stepping 02
[    0.290387] Brought up 2 CPUs
[    0.290390] Total of 2 processors activated (10021.22 BogoMIPS).
[    0.290499] CPU0 attaching sched-domain:
[    0.290501]  domain 0: span 0-1 level MC
[    0.290503]   groups: 0 1
[    0.290508] CPU1 attaching sched-domain:
[    0.290509]  domain 0: span 0-1 level MC
[    0.290511]   groups: 1 0
[    0.290567] Booting paravirtualized kernel on bare hardware
[    0.290567] regulator: core version 0.5
[    0.290567] Time: 23:12:20  Date: 11/26/09
[    0.290567] NET: Registered protocol family 16
[    0.290567] node 0 link 0: io port [c000, ffff]
[    0.290567] TOM: 00000000d0000000 aka 3328M
[    0.290567] node 0 link 0: mmio [a0000, bffff]
[    0.290567] node 0 link 0: mmio [d0000000, dfffffff]
[    0.290567] node 0 link 0: mmio [f0000000, fe02ffff]
[    0.290567] node 0 link 0: mmio [e0000000, e03fffff]
[    0.290567] TOM2: 0000000130000000 aka 4864M
[    0.290567] bus: [00,03] on node 0 link 0
[    0.290567] bus: 00 index 0 io port: [0, ffff]
[    0.290567] bus: 00 index 1 mmio: [a0000, bffff]
[    0.290567] bus: 00 index 2 mmio: [d0000000, efffffff]
[    0.290567] bus: 00 index 3 mmio: [f0000000, ffffffff]
[    0.290567] bus: 00 index 4 mmio: [130000000, fcffffffff]
[    0.290567] ACPI: bus type pci registered
[    0.290567] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.290567] PCI: MCFG area at e0000000 reserved in E820
[    0.300633] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.300639] PCI: Using configuration type 1 for base access
[    0.301339] bio: create slab <bio-0> at 0
[    0.301339] ACPI: EC: Look up EC in DSDT
[    0.306850] ACPI: Interpreter enabled
[    0.306860] ACPI: (supports S0 S3 S4 S5)
[    0.306883] ACPI: Using IOAPIC for interrupt routing
[    0.312817] ACPI: No dock devices found.
[    0.312927] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.312984] pci 0000:00:00.0: reg 1c 64bit mmio: [0xe0000000-0xffffffff]
[    0.313045] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.313050] pci 0000:00:02.0: PME# disabled
[    0.313105] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
[    0.313110] pci 0000:00:0a.0: PME# disabled
[    0.313162] pci 0000:00:11.0: reg 10 io port: [0xff00-0xff07]
[    0.313169] pci 0000:00:11.0: reg 14 io port: [0xfe00-0xfe03]
[    0.313176] pci 0000:00:11.0: reg 18 io port: [0xfd00-0xfd07]
[    0.313183] pci 0000:00:11.0: reg 1c io port: [0xfc00-0xfc03]
[    0.313190] pci 0000:00:11.0: reg 20 io port: [0xfb00-0xfb0f]
[    0.313197] pci 0000:00:11.0: reg 24 32bit mmio: [0xfe02f000-0xfe02f3ff]
[    0.313250] pci 0000:00:12.0: reg 10 32bit mmio: [0xfe02e000-0xfe02efff]
[    0.313305] pci 0000:00:12.1: reg 10 32bit mmio: [0xfe02d000-0xfe02dfff]
[    0.313378] pci 0000:00:12.2: reg 10 32bit mmio: [0xfe02c000-0xfe02c0ff]
[    0.313431] pci 0000:00:12.2: supports D1 D2
[    0.313433] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.313439] pci 0000:00:12.2: PME# disabled
[    0.313474] pci 0000:00:13.0: reg 10 32bit mmio: [0xfe02b000-0xfe02bfff]
[    0.313530] pci 0000:00:13.1: reg 10 32bit mmio: [0xfe02a000-0xfe02afff]
[    0.313603] pci 0000:00:13.2: reg 10 32bit mmio: [0xfe029000-0xfe0290ff]
[    0.313656] pci 0000:00:13.2: supports D1 D2
[    0.313658] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.313663] pci 0000:00:13.2: PME# disabled
[    0.313784] pci 0000:00:14.1: reg 10 io port: [0x00-0x07]
[    0.313790] pci 0000:00:14.1: reg 14 io port: [0x00-0x03]
[    0.313797] pci 0000:00:14.1: reg 18 io port: [0x00-0x07]
[    0.313804] pci 0000:00:14.1: reg 1c io port: [0x00-0x03]
[    0.313811] pci 0000:00:14.1: reg 20 io port: [0xfa00-0xfa0f]
[    0.313878] pci 0000:00:14.2: reg 10 64bit mmio: [0xfe024000-0xfe027fff]
[    0.313921] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.313927] pci 0000:00:14.2: PME# disabled
[    0.314034] pci 0000:00:14.5: reg 10 32bit mmio: [0xfe028000-0xfe028fff]
[    0.314162] pci 0000:01:00.0: reg 10 64bit mmio: [0xd0000000-0xdfffffff]
[    0.314171] pci 0000:01:00.0: reg 18 64bit mmio: [0xfdfe0000-0xfdfeffff]
[    0.314176] pci 0000:01:00.0: reg 20 io port: [0xee00-0xeeff]
[    0.314185] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.314203] pci 0000:01:00.0: supports D1 D2
[    0.314235] pci 0000:01:00.1: reg 10 64bit mmio: [0xfdffc000-0xfdffffff]
[    0.314269] pci 0000:01:00.1: supports D1 D2
[    0.314327] pci 0000:00:02.0: bridge io port: [0xe000-0xefff]
[    0.314329] pci 0000:00:02.0: bridge 32bit mmio: [0xfdf00000-0xfdffffff]
[    0.314334] pci 0000:00:02.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.314368] pci 0000:02:00.0: reg 10 io port: [0xde00-0xdeff]
[    0.314383] pci 0000:02:00.0: reg 18 64bit mmio: [0xfdbff000-0xfdbfffff]
[    0.314394] pci 0000:02:00.0: reg 20 64bit mmio: [0xfdbe0000-0xfdbeffff]
[    0.314401] pci 0000:02:00.0: reg 30 32bit mmio: [0x000000-0x00ffff]
[    0.314430] pci 0000:02:00.0: supports D1 D2
[    0.314432] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.314438] pci 0000:02:00.0: PME# disabled
[    0.314505] pci 0000:00:0a.0: bridge io port: [0xd000-0xdfff]
[    0.314508] pci 0000:00:0a.0: bridge 32bit mmio: [0xfde00000-0xfdefffff]
[    0.314512] pci 0000:00:0a.0: bridge 64bit mmio pref: [0xfdb00000-0xfdbfffff]
[    0.314581] pci 0000:03:0e.0: reg 10 32bit mmio: [0xfddff000-0xfddff7ff]
[    0.314590] pci 0000:03:0e.0: reg 14 32bit mmio: [0xfddf8000-0xfddfbfff]
[    0.314649] pci 0000:03:0e.0: supports D1 D2
[    0.314651] pci 0000:03:0e.0: PME# supported from D0 D1 D2 D3hot
[    0.314658] pci 0000:03:0e.0: PME# disabled
[    0.314695] pci 0000:00:14.4: transparent bridge
[    0.314701] pci 0000:00:14.4: bridge io port: [0xc000-0xcfff]
[    0.314705] pci 0000:00:14.4: bridge 32bit mmio: [0xfdd00000-0xfddfffff]
[    0.314710] pci 0000:00:14.4: bridge 32bit mmio pref: [0xfdc00000-0xfdcfffff]
[    0.314725] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.314970] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.315042] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[    0.315105] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCEA._PRT]
[    0.334618] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.334710] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.334801] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.334895] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.334989] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.335083] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.335177] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.335274] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.335434] SCSI subsystem initialized
[    0.335481] libata version 3.00 loaded.
[    0.335481] usbcore: registered new interface driver usbfs
[    0.335481] usbcore: registered new interface driver hub
[    0.335481] usbcore: registered new device driver usb
[    0.335481] ACPI: WMI: Mapper loaded
[    0.335481] PCI: Using ACPI for IRQ routing
[    0.335481] pci 0000:00:00.0: BAR 3: address space collision on of device [0xe0000000-0xffffffff]
[    0.335481] pci 0000:00:00.0: BAR 3: can't allocate resource
[    0.380006] Bluetooth: Core ver 2.15
[    0.380022] NET: Registered protocol family 31
[    0.380022] Bluetooth: HCI device and connection manager initialized
[    0.380022] Bluetooth: HCI socket layer initialized
[    0.380024] NetLabel: Initializing
[    0.380027] NetLabel:  domain hash size = 128
[    0.380030] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.380045] NetLabel:  unlabeled traffic allowed by default
[    0.380220] PCI-DMA: Disabling AGP.
[    0.380302] PCI-DMA: aperture base @ 20000000 size 65536 KB
[    0.380307] PCI-DMA: using GART IOMMU.
[    0.380312] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    0.380760] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 24, 0
[    0.380772] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.390043] hpet: hpet2 irq 24 for MSI
[    0.400030] Switched to high resolution mode on CPU 0
[    0.400294] Switched to high resolution mode on CPU 1
[    0.420029] pnp: PnP ACPI init
[    0.420051] ACPI: bus type pnp registered
[    0.422595] pnp 00:0b: mem resource (0xd1c00-0xd3fff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.422603] pnp 00:0b: mem resource (0xf0000-0xf7fff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.422608] pnp 00:0b: mem resource (0xf8000-0xfbfff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.422614] pnp 00:0b: mem resource (0xfc000-0xfffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.422620] pnp 00:0b: mem resource (0x0-0x9ffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.422626] pnp 00:0b: mem resource (0x100000-0xcfddffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.422707] pnp: PnP ACPI: found 12 devices
[    0.422710] ACPI: ACPI bus type pnp unregistered
[    0.422722] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.422726] system 00:01: ioport range 0x220-0x225 has been reserved
[    0.422730] system 00:01: ioport range 0x290-0x294 has been reserved
[    0.422736] system 00:02: ioport range 0x4100-0x411f has been reserved
[    0.422740] system 00:02: ioport range 0x228-0x22f has been reserved
[    0.422744] system 00:02: ioport range 0x238-0x23f has been reserved
[    0.422748] system 00:02: ioport range 0x40b-0x40b has been reserved
[    0.422752] system 00:02: ioport range 0x4d6-0x4d6 has been reserved
[    0.422757] system 00:02: ioport range 0xc00-0xc01 has been reserved
[    0.422761] system 00:02: ioport range 0xc14-0xc14 has been reserved
[    0.422765] system 00:02: ioport range 0xc50-0xc52 has been reserved
[    0.422769] system 00:02: ioport range 0xc6c-0xc6d has been reserved
[    0.422773] system 00:02: ioport range 0xc6f-0xc6f has been reserved
[    0.422777] system 00:02: ioport range 0xcd0-0xcd1 has been reserved
[    0.422781] system 00:02: ioport range 0xcd2-0xcd3 has been reserved
[    0.422785] system 00:02: ioport range 0xcd4-0xcdf has been reserved
[    0.422790] system 00:02: ioport range 0x4000-0x40fe has been reserved
[    0.422794] system 00:02: ioport range 0x4210-0x4217 has been reserved
[    0.422798] system 00:02: ioport range 0xb00-0xb0f has been reserved
[    0.422802] system 00:02: ioport range 0xb10-0xb1f has been reserved
[    0.422807] system 00:02: ioport range 0xb20-0xb3f has been reserved
[    0.422814] system 00:0a: iomem range 0xe0000000-0xefffffff has been reserved
[    0.422821] system 00:0b: iomem range 0xcfde0000-0xcfdfffff could not be reserved
[    0.422826] system 00:0b: iomem range 0xffff0000-0xffffffff has been reserved
[    0.422831] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.422836] system 00:0b: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.422844] system 00:0b: iomem range 0xfff80000-0xfffeffff has been reserved
[    0.427539] AppArmor: AppArmor Filesystem Enabled
[    0.427578] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
[    0.427583] pci 0000:00:02.0:   IO window: 0xe000-0xefff
[    0.427589] pci 0000:00:02.0:   MEM window: 0xfdf00000-0xfdffffff
[    0.427595] pci 0000:00:02.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.427603] pci 0000:00:0a.0: PCI bridge, secondary bus 0000:02
[    0.427608] pci 0000:00:0a.0:   IO window: 0xd000-0xdfff
[    0.427613] pci 0000:00:0a.0:   MEM window: 0xfde00000-0xfdefffff
[    0.427618] pci 0000:00:0a.0:   PREFETCH window: 0x000000fdb00000-0x000000fdbfffff
[    0.427626] pci 0000:00:14.4: PCI bridge, secondary bus 0000:03
[    0.427642] pci 0000:00:14.4:   IO window: 0xc000-0xcfff
[    0.427650] pci 0000:00:14.4:   MEM window: 0xfdd00000-0xfddfffff
[    0.427656] pci 0000:00:14.4:   PREFETCH window: 0xfdc00000-0xfdcfffff
[    0.427669]   alloc irq_desc for 18 on node 0
[    0.427671]   alloc kstat_irqs on node 0
[    0.427679] pci 0000:00:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.427686] pci 0000:00:02.0: setting latency timer to 64
[    0.427691] pci 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.427697] pci 0000:00:0a.0: setting latency timer to 64
[    0.427705] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.427707] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.427709] pci_bus 0000:01: resource 0 io:  [0xe000-0xefff]
[    0.427711] pci_bus 0000:01: resource 1 mem: [0xfdf00000-0xfdffffff]
[    0.427714] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.427716] pci_bus 0000:02: resource 0 io:  [0xd000-0xdfff]
[    0.427718] pci_bus 0000:02: resource 1 mem: [0xfde00000-0xfdefffff]
[    0.427721] pci_bus 0000:02: resource 2 pref mem [0xfdb00000-0xfdbfffff]
[    0.427723] pci_bus 0000:03: resource 0 io:  [0xc000-0xcfff]
[    0.427725] pci_bus 0000:03: resource 1 mem: [0xfdd00000-0xfddfffff]
[    0.427727] pci_bus 0000:03: resource 2 pref mem [0xfdc00000-0xfdcfffff]
[    0.427730] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.427732] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.427767] NET: Registered protocol family 2
[    0.427925] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.429269] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.433133] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.433631] TCP: Hash tables configured (established 524288 bind 65536)
[    0.433638] TCP reno registered
[    0.433742] NET: Registered protocol family 1
[    0.433803] Trying to unpack rootfs image as initramfs...
[    0.602307] Freeing initrd memory: 8185k freed
[    0.606147] Scanning for low memory corruption every 60 seconds
[    0.606268] audit: initializing netlink socket (disabled)
[    0.606283] type=2000 audit(1259277139.600:1): initialized
[    0.614017] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.615221] VFS: Disk quotas dquot_6.5.2
[    0.615275] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.615816] fuse init (API version 7.12)
[    0.615888] msgmni has been set to 7921
[    0.616119] alg: No test for stdrng (krng)
[    0.616143] io scheduler noop registered
[    0.616146] io scheduler anticipatory registered
[    0.616149] io scheduler deadline registered
[    0.616187] io scheduler cfq registered (default)
[    1.640031] pci 0000:00:12.1: OHCI: BIOS handoff failed (BIOS bug?) 00000184
[    1.730049] pci 0000:01:00.0: Boot video device
[    1.730237]   alloc irq_desc for 25 on node 0
[    1.730239]   alloc kstat_irqs on node 0
[    1.730246] pcieport-driver 0000:00:02.0: irq 25 for MSI/MSI-X
[    1.730252] pcieport-driver 0000:00:02.0: setting latency timer to 64
[    1.730374]   alloc irq_desc for 26 on node 0
[    1.730376]   alloc kstat_irqs on node 0
[    1.730380] pcieport-driver 0000:00:0a.0: irq 26 for MSI/MSI-X
[    1.730385] pcieport-driver 0000:00:0a.0: setting latency timer to 64
[    1.730449] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.730477] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.730579] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.730584] ACPI: Power Button [PWRF]
[    1.730629] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.730636] ACPI: Power Button [PWRB]
[    1.730927] processor LNXCPU:00: registered as cooling_device0
[    1.730969] processor LNXCPU:01: registered as cooling_device1
[    1.733865] Linux agpgart interface v0.103
[    1.733879] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.733998] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.734262] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.735041] brd: module loaded
[    1.735393] loop: module loaded
[    1.735466] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.735599] ahci 0000:00:11.0: version 3.0
[    1.735617]   alloc irq_desc for 22 on node 0
[    1.735618]   alloc kstat_irqs on node 0
[    1.735629] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.735757] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.735765] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    1.736169] scsi0 : ahci
[    1.736293] scsi1 : ahci
[    1.736354] scsi2 : ahci
[    1.736414] scsi3 : ahci
[    1.736518] ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 22
[    1.736526] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 22
[    1.736533] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 22
[    1.736540] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 22
[    1.736822]   alloc irq_desc for 16 on node 0
[    1.736824]   alloc kstat_irqs on node 0
[    1.736833] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.736957] scsi4 : pata_atiixp
[    1.737019] scsi5 : pata_atiixp
[    1.738039] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfa00 irq 14
[    1.738045] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfa08 irq 15
[    1.738559] Fixed MDIO Bus: probed
[    1.738588] PPP generic driver version 2.4.2
[    1.738681] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.738743]   alloc irq_desc for 17 on node 0
[    1.738745]   alloc kstat_irqs on node 0
[    1.738753] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.738778] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    1.738827] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.738860] ehci_hcd 0000:00:12.2: applying AMD SB600/SB700 USB freeze workaround
[    1.738882] ehci_hcd 0000:00:12.2: debug port 1
[    1.738913] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe02c000
[    1.750024] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.750085] usb usb1: configuration #1 chosen from 1 choice
[    1.750112] hub 1-0:1.0: USB hub found
[    1.750121] hub 1-0:1.0: 6 ports detected
[    1.750231]   alloc irq_desc for 19 on node 0
[    1.750232]   alloc kstat_irqs on node 0
[    1.750240] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.750257] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.750295] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.750327] ehci_hcd 0000:00:13.2: applying AMD SB600/SB700 USB freeze workaround
[    1.750348] ehci_hcd 0000:00:13.2: debug port 1
[    1.750373] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe029000
[    1.770022] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.770067] usb usb2: configuration #1 chosen from 1 choice
[    1.770093] hub 2-0:1.0: USB hub found
[    1.770100] hub 2-0:1.0: 6 ports detected
[    1.770166] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.770219] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.770240] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.770272] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.770318] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfe02e000
[    1.834073] usb usb3: configuration #1 chosen from 1 choice
[    1.834098] hub 3-0:1.0: USB hub found
[    1.834113] hub 3-0:1.0: 3 ports detected
[    1.834197] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.834210] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    1.834250] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    1.834273] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfe02d000
[    1.905861] usb usb4: configuration #1 chosen from 1 choice
[    1.905887] hub 4-0:1.0: USB hub found
[    1.905900] hub 4-0:1.0: 3 ports detected
[    1.905983] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.905997] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.906026] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.906059] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe02b000
[    1.964075] usb usb5: configuration #1 chosen from 1 choice
[    1.964097] hub 5-0:1.0: USB hub found
[    1.964111] hub 5-0:1.0: 3 ports detected
[    1.964198] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.964210] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    1.964239] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    1.964261] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfe02a000
[    2.024075] usb usb6: configuration #1 chosen from 1 choice
[    2.024098] hub 6-0:1.0: USB hub found
[    2.024112] hub 6-0:1.0: 3 ports detected
[    2.024200] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.024215] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    2.024258] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    2.024283] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfe028000
[    2.081323] ata4: SATA link down (SStatus 0 SControl 300)
[    2.084075] usb usb7: configuration #1 chosen from 1 choice
[    2.084099] hub 7-0:1.0: USB hub found
[    2.084113] hub 7-0:1.0: 2 ports detected
[    2.084167] uhci_hcd: USB Universal Host Controller Interface driver
[    2.084276] PNP: No PS/2 controller found. Probing ports directly.
[    2.084641] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.084649] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.084720] mice: PS/2 mouse device common for all mice
[    2.084802] rtc_cmos 00:05: RTC can wake from S4
[    2.084836] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    2.084873] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    2.084973] device-mapper: uevent: version 1.0.3
[    2.085058] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    2.085145] device-mapper: multipath: version 1.1.0 loaded
[    2.085150] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.085340] cpuidle: using governor ladder
[    2.085344] cpuidle: using governor menu
[    2.085706] TCP cubic registered
[    2.085818] NET: Registered protocol family 10
[    2.086193] lo: Disabled Privacy Extensions
[    2.086423] NET: Registered protocol family 17
[    2.086444] Bluetooth: L2CAP ver 2.13
[    2.086447] Bluetooth: L2CAP socket layer initialized
[    2.086451] Bluetooth: SCO (Voice Link) ver 0.6
[    2.086454] Bluetooth: SCO socket layer initialized
[    2.086494] Bluetooth: RFCOMM TTY layer initialized
[    2.086499] Bluetooth: RFCOMM socket layer initialized
[    2.086502] Bluetooth: RFCOMM ver 1.11
[    2.086529] powernow-k8: Found 1 AMD Athlon(tm) Dual Core Processor 4850e processors (2 cpu cores) (version 2.20.00)
[    2.086588] powernow-k8:    0 : fid 0x11 (2500 MHz), vid 0xc
[    2.086592] powernow-k8:    1 : fid 0x10 (2400 MHz), vid 0xd
[    2.086596] powernow-k8:    2 : fid 0xe (2200 MHz), vid 0xf
[    2.086599] powernow-k8:    3 : fid 0xc (2000 MHz), vid 0x11
[    2.086603] powernow-k8:    4 : fid 0xa (1800 MHz), vid 0x13
[    2.086606] powernow-k8:    5 : fid 0x2 (1000 MHz), vid 0x16
[    2.086728] PM: Resume from disk failed.
[    2.086739] registered taskstats version 1
[    2.086869]   Magic number: 1:594:252
[    2.086962] rtc_cmos 00:05: setting system clock to 2009-11-26 23:12:22 UTC (1259277142)
[    2.086968] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.086971] EDD information not available.
[    2.131276] usb 1-4: new high speed USB device using ehci_hcd and address 3
[    2.261270] ata1: softreset failed (device not ready)
[    2.261275] ata1: applying SB600 PMP SRST workaround and retrying
[    2.261292] ata2: softreset failed (device not ready)
[    2.261297] ata2: applying SB600 PMP SRST workaround and retrying
[    2.261314] ata3: softreset failed (device not ready)
[    2.261319] ata3: applying SB600 PMP SRST workaround and retrying
[    2.282445] usb 1-4: configuration #1 chosen from 1 choice
[    2.282536] hub 1-4:1.0: USB hub found
[    2.282640] hub 1-4:1.0: 7 ports detected
[    2.440034] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.440061] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.440083] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.441232] ata2.00: ATAPI: HL-DT-STDVD-RAM GH22NS30, 1.01, max UDMA/100
[    2.441608] ata3.00: ATA-8: ST3500320AS, SD1A, max UDMA/133
[    2.441613] ata3.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    2.442679] ata2.00: configured for UDMA/100
[    2.443590] ata3.00: configured for UDMA/133
[    2.469844] ata1.00: ATA-8: ST3640323AS, CC1F, max UDMA/133
[    2.469848] ata1.00: 1250263728 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    2.518618] ata1.00: configured for UDMA/133
[    2.530111] scsi 0:0:0:0: Direct-Access     ATA      ST3640323AS      CC1F PQ: 0 ANSI: 5
[    2.530215] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.530251] sd 0:0:0:0: [sda] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
[    2.530292] sd 0:0:0:0: [sda] Write Protect is off
[    2.530297] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.530316] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.530427]  sda:
[    2.531548] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GH22NS30 1.01 PQ: 0 ANSI: 5
[    2.534826] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.534831] Uniform CD-ROM driver Revision: 3.20
[    2.534907] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.534940] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.535004] scsi 2:0:0:0: Direct-Access     ATA      ST3500320AS      SD1A PQ: 0 ANSI: 5
[    2.535087] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    2.535119] sd 2:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    2.535158] sd 2:0:0:0: [sdb] Write Protect is off
[    2.535163] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.535182] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.535270]  sdb: sda1 sda2 < sda5 sda6 sdb2 < sdb5 sdb6 >
[    2.558712] sd 2:0:0:0: [sdb] Attached SCSI disk
[    2.572967]  sda7 sda8 sda9 > sda4
[    2.600194] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.601270] usb 3-2: new low speed USB device using ohci_hcd and address 2
[    2.701327] Freeing unused kernel memory: 660k freed
[    2.701619] Write protecting the kernel read-only data: 7584k
[    2.807245] usb 3-2: configuration #1 chosen from 1 choice
[    2.837970] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.838002] r8169 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.838057] r8169 0000:02:00.0: setting latency timer to 64
[    2.838094]   alloc irq_desc for 27 on node 0
[    2.838096]   alloc kstat_irqs on node 0
[    2.838109] r8169 0000:02:00.0: irq 27 for MSI/MSI-X
[    2.838630] eth0: RTL8168c/8111c at 0xffffc9000066c000, 00:1f:d0:56:b1:0b, XID 3c4000c0 IRQ 27
[    2.889820] ohci1394 0000:03:0e.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    2.896138] usbcore: registered new interface driver hiddev
[    2.896228] usbcore: registered new interface driver usbhid
[    2.896233] usbhid: v2.6:USB HID core driver
[    2.902385] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2:1.0/input/input3
[    2.902461] logitech 0003:046D:C517.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:12.0-2/input0
[    2.910103] logitech 0003:046D:C517.0002: fixing up Logitech keyboard report descriptor
[    2.910938] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2:1.1/input/input4
[    2.911053] logitech 0003:046D:C517.0002: input,hiddev96,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:12.0-2/input1
[    2.911718] usb 1-4.5: new high speed USB device using ehci_hcd and address 4
[    2.950087] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[fddff000-fddff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.023910] usb 1-4.5: configuration #1 chosen from 1 choice
[    3.032597] Initializing USB Mass Storage driver...
[    3.032732] scsi6 : SCSI emulation for USB Mass Storage devices
[    3.032839] usbcore: registered new interface driver usb-storage
[    3.032844] USB Mass Storage support registered.
[    3.032975] usb-storage: device found at 4
[    3.032976] usb-storage: waiting for device to settle before scanning
[    3.155711] vesafb: framebuffer at 0xd0000000, mapped to 0xffffc90011180000, using 3072k, total 16384k
[    3.155722] vesafb: mode is 1024x768x16, linelength=2048, pages=9
[    3.155726] vesafb: scrolling: redraw
[    3.155730] vesafb: Truecolor: size=0:5:6:5, shift=0:11:5:0
[    3.155776] fb0: VESA VGA frame buffer device
[    3.160482] Console: switching to colour frame buffer device 128x48
[    3.409874] PM: Starting manual resume from disk
[    3.409956] PM: Resume from partition 8:8
[    3.409957] PM: Checking hibernation image.
[    3.410206] PM: Resume from disk failed.
[    3.422430] EXT4-fs (sda5): barriers enabled
[    3.443511] kjournald2 starting: pid 433, dev sda5:8, commit interval 5 seconds
[    3.443636] EXT4-fs (sda5): delayed allocation enabled
[    3.443724] EXT4-fs: file extents enabled
[    3.443883] EXT4-fs: mballoc enabled
[    3.443953] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    3.959763] type=1505 audit(1259277144.364:2): operation="profile_load" pid=459 name=/usr/share/gdm/guest-session/Xsession
[    3.972252] type=1505 audit(1259277144.384:3): operation="profile_load" pid=460 name=/sbin/dhclient3
[    3.974177] type=1505 audit(1259277144.384:4): operation="profile_load" pid=460 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    3.977836] type=1505 audit(1259277144.384:5): operation="profile_load" pid=460 name=/usr/lib/connman/scripts/dhclient-script
[    3.999533] type=1505 audit(1259277144.404:6): operation="profile_load" pid=461 name=/usr/bin/evince
[    4.005663] type=1505 audit(1259277144.414:7): operation="profile_load" pid=461 name=/usr/bin/evince-previewer
[    4.010204] type=1505 audit(1259277144.414:8): operation="profile_load" pid=461 name=/usr/bin/evince-thumbnailer
[    4.032042] type=1505 audit(1259277144.444:9): operation="profile_load" pid=463 name=/usr/lib/cups/backend/cups-pdf
[    4.034820] type=1505 audit(1259277144.444:10): operation="profile_load" pid=463 name=/usr/sbin/cupsd
[    4.261463] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0070cd5b00001fd0]
[    8.030235] usb-storage: device scan complete
[    8.030843] scsi 6:0:0:0: Direct-Access     Multi    Flash Reader     1.00 PQ: 0 ANSI: 0
[    8.033916] sd 6:0:0:0: Attached scsi generic sg3 type 0
[    8.450794] sd 6:0:0:0: [sdc] 15523840 512-byte logical blocks: (7.94 GB/7.40 GiB)
[    8.454911] sd 6:0:0:0: [sdc] Write Protect is off
[    8.457873] sd 6:0:0:0: [sdc] Mode Sense: 03 00 00 00
[    8.457876] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[    8.463659] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[    8.466683]  sdc: sdc1
[    8.485154] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[    8.488289] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[   10.499817] udev: starting version 147
[   10.532165] ACPI: I/O resource piix4_smbus [0xb00-0xb07] conflicts with ACPI region SOR1 [0xb00-0xb0f]
[   10.535722] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   10.535745] piix4_smbus: probe of 0000:00:14.0 failed with error -16
[   10.536872] EDAC MC: Ver: 2.1.0 Nov 10 2009
[   10.538518] EDAC amd64_edac:  Ver: 3.2.0 Nov 10 2009
[   10.538607] EDAC amd64: This node reports that Memory ECC is currently disabled.
[   10.538612] EDAC amd64: bit 0x400000 in register F3x44 of the MISC_CONTROL device (0000:00:18.3) should be enabled
[   10.538614] EDAC amd64: WARNING: ECC is NOT currently enabled by the BIOS. Module will NOT be loaded.
[   10.538616]     Either Enable ECC in the BIOS, or use the 'ecc_enable_override' parameter.
[   10.538617]     Might be a BIOS bug, if BIOS says ECC is enabled
[   10.538618]     Use of the override can cause unknown side effects.
[   10.538798] amd64_edac: probe of 0000:00:18.2 failed with error -22
[   10.550183] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   10.560465] Adding 1020088k swap on /dev/sda8.  Priority:-1 extents:1 across:1020088k 
[   10.635330] parport_pc 00:09: reported by Plug and Play ACPI
[   10.635388] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   10.663585] lp: driver loaded but no devices found
[   10.671414] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   10.671419] Disabling lock debugging due to kernel taint
[   10.712289] lp0: using parport0 (interrupt-driven).
[   10.745254] ppdev: user-space parallel port driver
[   10.756923] ip_tables: (C) 2000-2006 Netfilter Core Team
[   10.761433] [fglrx] Maximum main memory to use for locked dma buffers: 3799 MBytes.
[   10.761542] [fglrx]   vendor: 1002 device: 9598 count: 1
[   10.761794] [fglrx] ioport: bar 4, base 0xee00, size: 0x100
[   10.761809] pci 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   10.761814] pci 0000:01:00.0: setting latency timer to 64
[   10.761996] [fglrx] Kernel PAT support is enabled
[   10.762024] [fglrx] module loaded - fglrx 8.67.4 [Nov  4 2009] with 1 minors
[   10.793466] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.917967] hda_codec: Unknown model for ALC889A, trying auto-probe from BIOS...
[   10.918158] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input5
[   10.922500] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   10.922550] HDA Intel 0000:01:00.1: setting latency timer to 64
[   11.110330] EXT4-fs (sda5): internal journal on sda5:8
[   11.413357] EXT4-fs (sda6): barriers enabled
[   11.414174] kjournald2 starting: pid 919, dev sda6:8, commit interval 5 seconds
[   11.415354] EXT4-fs (sda6): internal journal on sda6:8
[   11.415357] EXT4-fs (sda6): delayed allocation enabled
[   11.415360] EXT4-fs: file extents enabled
[   11.416263] EXT4-fs: mballoc enabled
[   11.416280] EXT4-fs (sda6): mounted filesystem with ordered data mode
[   11.691346] EXT4-fs (sda7): barriers enabled
[   11.747837] r8169: eth0: link up
[   11.747846] r8169: eth0: link up
[   11.794386] __ratelimit: 3 callbacks suppressed
[   11.794390] type=1505 audit(1259298752.204:12): operation="profile_replace" pid=1092 name=/usr/share/gdm/guest-session/Xsession
[   11.796090] type=1505 audit(1259298752.204:13): operation="profile_replace" pid=1093 name=/sbin/dhclient3
[   11.796336] type=1505 audit(1259298752.204:14): operation="profile_replace" pid=1093 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   11.796474] type=1505 audit(1259298752.204:15): operation="profile_replace" pid=1093 name=/usr/lib/connman/scripts/dhclient-script
[   11.799859] kjournald2 starting: pid 1095, dev sda7:8, commit interval 5 seconds
[   11.800424] type=1505 audit(1259298752.204:16): operation="profile_replace" pid=1094 name=/usr/bin/evince
[   11.804401] type=1505 audit(1259298752.214:17): operation="profile_replace" pid=1094 name=/usr/bin/evince-previewer
[   11.806797] type=1505 audit(1259298752.214:18): operation="profile_replace" pid=1094 name=/usr/bin/evince-thumbnailer
[   11.809993] EXT4-fs (sda7): internal journal on sda7:8
[   11.809998] EXT4-fs (sda7): delayed allocation enabled
[   11.810002] EXT4-fs: file extents enabled
[   11.810346] EXT4-fs: mballoc enabled
[   11.810367] EXT4-fs (sda7): mounted filesystem with ordered data mode
[   11.814095] type=1505 audit(1259298752.224:19): operation="profile_replace" pid=1097 name=/usr/lib/cups/backend/cups-pdf
[   11.814395] type=1505 audit(1259298752.224:20): operation="profile_replace" pid=1097 name=/usr/sbin/cupsd
[   11.816516] type=1505 audit(1259298752.224:21): operation="profile_replace" pid=1099 name=/usr/sbin/tcpdump
[   12.779008]   alloc irq_desc for 28 on node 0
[   12.779012]   alloc kstat_irqs on node 0
[   12.779023] fglrx_pci 0000:01:00.0: irq 28 for MSI/MSI-X
[   12.779672] [fglrx] Firegl kernel thread PID: 1414
[   13.504688] CPU0 attaching NULL sched-domain.
[   13.504695] CPU1 attaching NULL sched-domain.
[   13.540119] CPU0 attaching sched-domain:
[   13.540122]  domain 0: span 0-1 level MC
[   13.540125]   groups: 0 1
[   13.540128]   domain 1: span 0-1 level CPU
[   13.540130]    groups: 0-1 (__cpu_power = 2048)
[   13.540134] CPU1 attaching sched-domain:
[   13.540136]  domain 0: span 0-1 level MC
[   13.540137]   groups: 1 0
[   13.540140]   domain 1: span 0-1 level CPU
[   13.540142]    groups: 0-1 (__cpu_power = 2048)
[   13.751234] kjournald starting.  Commit interval 5 seconds
[   13.751962] EXT3 FS on sda9, internal journal
[   13.751967] EXT3-fs: mounted filesystem with writeback data mode.
[   13.858616] [fglrx] Gart USWC size:1236 M.
[   13.858620] [fglrx] Gart cacheable size:491 M.
[   13.858626] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   13.858628] [fglrx] Reserved FB block: Unshared offset:fc1f000, size:3e1000 
[   13.858631] [fglrx] Reserved FB block: Unshared offset:1fffb000, size:5000 
[   15.547510] CPU0 attaching NULL sched-domain.
[   15.547517] CPU1 attaching NULL sched-domain.
[   15.601251] CPU0 attaching sched-domain:
[   15.601255]  domain 0: span 0-1 level MC
[   15.601258]   groups: 0 1
[   15.601263] CPU1 attaching sched-domain:
[   15.601265]  domain 0: span 0-1 level MC
[   15.601267]   groups: 1 0
[   18.620767] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   22.310013] eth0: no IPv6 routers present
[   74.001301] Clocksource tsc unstable (delta = -100487947 ns)
[  104.386442] usb 1-4.5: USB disconnect, address 4
[  109.801324] usb 1-4: reset high speed USB device using ehci_hcd and address 3
[  110.251756] usb 1-4.5: new high speed USB device using ehci_hcd and address 5
[  110.363909] usb 1-4.5: configuration #1 chosen from 1 choice
[  110.365264] scsi7 : SCSI emulation for USB Mass Storage devices
[  110.365599] usb-storage: device found at 5
[  110.365603] usb-storage: waiting for device to settle before scanning
[  115.363191] usb-storage: device scan complete
[  115.364028] scsi 7:0:0:0: Direct-Access     Multi    Flash Reader     1.00 PQ: 0 ANSI: 0
[  115.365031] sd 7:0:0:0: Attached scsi generic sg3 type 0
[  116.046962] sd 7:0:0:0: [sdc] 2012160 512-byte logical blocks: (1.03 GB/982 MiB)
[  116.047791] sd 7:0:0:0: [sdc] Write Protect is off
[  116.047798] sd 7:0:0:0: [sdc] Mode Sense: 03 00 00 00
[  116.047803] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  116.050164] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  116.050171]  sdc: sdc1
[  116.065667] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  116.065678] sd 7:0:0:0: [sdc] Attached SCSI removable disk
[  203.120207] usb 1-4.5: reset high speed USB device using ehci_hcd and address 5
[  203.899900] sd 7:0:0:0: [sdc] 2012160 512-byte logical blocks: (1.03 GB/982 MiB)
[  203.900753] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  203.902118] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  203.902125]  sdc: sdc1
[  254.092059] usb 1-4.5: reset high speed USB device using ehci_hcd and address 5
[  302.092450] usb 1-4.5: reset high speed USB device using ehci_hcd and address 5
[  334.092893] usb 1-4.5: reset high speed USB device using ehci_hcd and address 5
[  386.090882] usb 1-4.5: reset high speed USB device using ehci_hcd and address 5
[  423.112081] usb 1-4.5: reset high speed USB device using ehci_hcd and address 5

```

---

### Post by lavinog on 2009-11-27
It looks like a hardware issue with either my usb cable or my hub.
I was able to transfer 1g of data without problems when connected to the back of my computer.

---

### Post by jon.reeve on 2009-11-29
I've tried using different sockets, like the ones on the back of the computer, but no luck so far. 

```
Nov 29 19:49:32 albert kernel: [22752.780032] usb 1-8: new high speed USB device using ehci_hcd and address 5
Nov 29 19:49:35 albert kernel: [22756.321977] usb 1-8: configuration #1 chosen from 1 choice
Nov 29 19:49:37 albert kernel: [22758.178761] Initializing USB Mass Storage driver...
Nov 29 19:49:37 albert kernel: [22758.179273] scsi6 : SCSI emulation for USB Mass Storage devices
Nov 29 19:49:37 albert kernel: [22758.179444] usbcore: registered new interface driver usb-storage
Nov 29 19:49:37 albert kernel: [22758.179449] USB Mass Storage support registered.
Nov 29 19:49:42 albert kernel: [22763.181002] scsi 6:0:0:0: Direct-Access     Generic  USB Disk         9.02 PQ: 0 ANSI: 2
Nov 29 19:49:42 albert kernel: [22763.181542] sd 6:0:0:0: Attached scsi generic sg3 type 0
Nov 29 19:49:42 albert kernel: [22763.191611] sd 6:0:0:0: [sdc] 156368016 512-byte logical blocks: (80.0 GB/74.5 GiB)
Nov 29 19:49:42 albert kernel: [22763.192349] sd 6:0:0:0: [sdc] Write Protect is off
Nov 29 19:49:43 albert kernel: [22763.193852]  sdc: sdc1 < sdc5 sdc6 sdc7 >
Nov 29 19:49:43 albert kernel: [22763.729682] sd 6:0:0:0: [sdc] Attached SCSI disk
Nov 29 19:49:46 albert kernel: [22767.026653] hfs: Filesystem was not cleanly unmounted, running fsck.hfsplus is recommended.  mounting read-only.
Nov 29 19:49:46 albert kernel: [22767.081372] kjournald starting.  Commit interval 5 seconds
Nov 29 19:49:46 albert kernel: [22767.081397] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
Nov 29 19:49:46 albert kernel: [22767.091086] EXT3 FS on sdc6, internal journal
Nov 29 19:49:46 albert kernel: [22767.091098] EXT3-fs: mounted filesystem with writeback data mode.
Nov 29 19:50:23 albert kernel: [22804.160038] usb 1-8: reset high speed USB device using ehci_hcd and address 5
Nov 29 19:51:06 albert kernel: [22847.160126] usb 1-8: reset high speed USB device using ehci_hcd and address 5
Nov 29 19:51:37 albert kernel: [22878.160086] usb 1-8: reset high speed USB device using ehci_hcd and address 5
Nov 29 19:52:08 albert kernel: [22909.160041] usb 1-8: reset high speed USB device using ehci_hcd and address 5
Nov 29 19:52:39 albert kernel: [22940.161116] usb 1-8: reset high speed USB device using ehci_hcd and address 5
```

---

### Post by Aposp on 2009-12-05
i am dealing with the exact same problem when i try to write data to a usb flash disk

```

[  879.160054] usb 1-8: reset high speed USB device using ehci_hcd and address 6
[  971.162532] usb 1-8: reset high speed USB device using ehci_hcd and address 6

```

---

### Post by dasbooter on 2009-12-15
```
kernel: [33806.100696] usb 1-4: reset high speed USB device using ehci_hcd and address 9
```

Many versions of ubuntu have had this problem... I have been around since edgy... for me the problem seems related to whether or not I have an actuall hi-speed device connected or not. Ex 720p webcam or any other webcam or maybe even my usb hard drive connected at the same time as my ipod or psp will cause this when I am trying to transfer a file to the ipod or psp. Disconnecting the camera(even if it isnt being used by a program) allows me to transfer files to the psp or ipod without the above warning with no problems or corruption. Ubuntu doesnt seem to be able to manage the resources of the usb for me.I wish I new a way to disable one usb device from the cli so I wouldnt have to manually unplug it... maybe this helps some of you. Built in webcams(laptops) maybe a problem. I wish the devs would fix this but I guess it is a complicated problem ... different hardware and all :(   <---  I am sad about this

---

### Post by lavinog on 2009-12-16
I have noticed that if I use a microsoft keyboard with a logitech mouse, i have to move my mouse in order for my keyboard to work in bios/grub menu.  I got a new logitech keyboard and the keyboard works fine in bios.  I should try the microsoft keyboard with a microsoft mouse to see what happens...I am mentioning this to point out that usb devices are not always "universal"

---

### Post by Filippo on 2009-12-22
I have the same problem with another device:
```

Dec 22 23:13:50 bdesk kernel: [ 3980.490018] usb 1-1: new high speed USB device using ehci_hcd and address 5
Dec 22 23:13:50 bdesk kernel: [ 3980.640928] usb 1-1: configuration #1 chosen from 1 choice
Dec 22 23:13:51 bdesk kernel: [ 3980.789116] scsi8 : SCSI emulation for USB Mass Storage devices
Dec 22 23:13:56 bdesk kernel: [ 3985.780816] scsi scan: INQUIRY result too short (35), using 36
Dec 22 23:13:56 bdesk kernel: [ 3985.780823] scsi 8:0:0:0: Direct-Access     veecam                         PQ: 0 ANSI: 2
Dec 22 23:13:56 bdesk kernel: [ 3985.781357] sd 8:0:0:0: Attached scsi generic sg6 type 0
Dec 22 23:13:56 bdesk kernel: [ 3985.782387] sd 8:0:0:0: [sdf] 16777216 512-byte logical blocks: (8.58 GB/8.00 GiB)
Dec 22 23:13:56 bdesk kernel: [ 3985.782934] sd 8:0:0:0: [sdf] Write Protect is off
Dec 22 23:13:56 bdesk kernel: [ 3985.784750]  sdf: sdf1
Dec 22 23:13:56 bdesk kernel: [ 3985.790859] sd 8:0:0:0: [sdf] Attached SCSI disk
Dec 22 23:14:03 bdesk kernel: [ 3993.070017] usb 1-1: reset high speed USB device using ehci_hcd and address 5
Dec 22 23:14:09 bdesk kernel: [ 3999.227692] usb 1-1: USB disconnect, address 5

```

This device is working with Ubuntu 8.04 and Windows XP.

Any help would be greatly appreciated.
Thanks, Filippo

---

### Post by HunkTB on 2010-03-19
I think it is related with [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88746](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88746), with no solution yet

---

### Post by Elwro on 2010-06-16
I also have this problem, with a 1 TB Western Digital disk. Am I reading something wrong, or does the bug linked to above have the status "Won't fix"? Why? For me this is a serious problem, since I rely on this external disk for archiving my data.

---

### Post by lavinog on 2010-06-17
> **Elwro said:**
> I also have this problem, with a 1 TB Western Digital disk. Am I reading something wrong, or does the bug linked to above have the status "Won't fix"? Why? For me this is a serious problem, since I rely on this external disk for archiving my data.

I believe it is "Won't fix" because ehci_hcd is no longer a module, but compiled into the kernel.

Do you have any messages in dmesg that is giving you any clues as to what the problem is?
It would be better to create a new bug report for your situation.  That bug report seems to have too much garbage, but no clear indication as to what the problem is.

Many times it is a hardware issue and not a driver issue.
For instance: I have a couple of usb cables that if I boot with a device attached to them, I will have issues. If I boot without a device attached, and wait until ubuntu loads to attach the device, everything works fine.  I cannot blame Ubuntu for the problem though because if I boot with the device attached, I cannot enter bios.  I also suspect my keyboard to be a cause of some of the issues, because I experience less issues when I use a generic keyboard.  I have 3 of the same keyboards and each one does something weird on different machines.

---

