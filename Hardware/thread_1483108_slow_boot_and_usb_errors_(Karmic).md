---
title: "slow boot and usb errors (Karmic)"
date: 2010-05-14
forum: Hardware
---

### Post by WDYSUN on 2010-05-14
Dear Users

from time to time I experienced very slow boot processes on my Karmic (64bit). 

Today I had a check and form the dmesg output I noticed there are several erros on usb devices. Could somebody explains 

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-21-generic (buildd@yellow) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu9) ) #59-Ubuntu SMP Wed Mar 24 07:28:27 UTC 2010 (Ubuntu 2.6.31-21.59-generic)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-21-generic root=UUID=1e2405d2-d183-4723-9e92-650d1d597c11 ro splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e800 (usable)
[    0.000000]  BIOS-e820: 000000000009e800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfe90000 (usable)
[    0.000000]  BIOS-e820: 00000000cfe90000 - 00000000cfee0000 (reserved)
[    0.000000]  BIOS-e820: 00000000cfee0000 - 00000000cfee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cfee3000 - 00000000cfef0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cfef0000 - 00000000cff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] DMI 2.5 present.
[    0.000000] last_pfn = 0x130000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CEFFF write-protect
[    0.000000]   CF000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-through
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 100000000 mask FE0000000 write-back
[    0.000000]   1 base 120000000 mask FF0000000 write-back
[    0.000000]   2 base 000000000 mask F80000000 write-back
[    0.000000]   3 base 080000000 mask FC0000000 write-back
[    0.000000]   4 base 0C0000000 mask FF0000000 write-back
[    0.000000]   5 base 0CFF00000 mask FFFF00000 uncachable
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000cff00000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xcfe90 max_arch_pfn = 0x400000000
[    0.000000] e820 update range: 0000000000001000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
[    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009e800 (usable)
[    0.000000]  modified: 000000000009e800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000cfe90000 (usable)
[    0.000000]  modified: 00000000cfe90000 - 00000000cfee0000 (reserved)
[    0.000000]  modified: 00000000cfee0000 - 00000000cfee3000 (ACPI NVS)
[    0.000000]  modified: 00000000cfee3000 - 00000000cfef0000 (ACPI data)
[    0.000000]  modified: 00000000cfef0000 - 00000000cff00000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-00000000cfe90000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 00cfe00000 page 2M
[    0.000000]  00cfe00000 - 00cfe90000 page 4k
[    0.000000] kernel direct mapping tables up to cfe90000 @ 8000-e000
[    0.000000] init_memory_mapping: 0000000100000000-0000000130000000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0100000000 - 0130000000 page 2M
[    0.000000] kernel direct mapping tables up to 130000000 @ c000-12000
[    0.000000] RAMDISK: 37832000 - 37fef993
[    0.000000] ACPI: RSDP 00000000000f99c0 00014 (v00 DELL  )
[    0.000000] ACPI: RSDT 00000000cfee3000 00040 (v01 DELL    FX09    42302E31 AWRD 00000000)
[    0.000000] ACPI: FACP 00000000cfee3080 00074 (v01 DELL    FX09    42302E31 AWRD 00000000)
[    0.000000] ACPI: DSDT 00000000cfee3100 03F8D (v01 DELL   AWRDACPI 00001000 MSFT 03000000)
[    0.000000] ACPI: FACS 00000000cfee0000 00040
[    0.000000] ACPI: HPET 00000000cfee7180 00038 (v01 DELL    FX09    42302E31 AWRD 00000098)
[    0.000000] ACPI: MCFG 00000000cfee71c0 0003C (v01 DELL    FX09    42302E31 AWRD 00000000)
[    0.000000] ACPI: SLIC 00000000cfee7200 00176 (v01 DELL    FX09    42302E31 AWRD 00000000)
[    0.000000] ACPI: DMY2 00000000cfee7380 00080 (v01 DELL    FX09    42302E31 AWRD 00000000)
[    0.000000] ACPI: APIC 00000000cfee70c0 00084 (v01 DELL    FX09    42302E31 AWRD 00000000)
[    0.000000] ACPI: SSDT 00000000cfee7d20 00380 (v01  PmRef    CpuPm 00003000 INTL 20041203)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000130000000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000130000000
[    0.000000]   NODE_DATA [000000000000d000 - 0000000000011fff]
[    0.000000]   bootmap [0000000000012000 -  0000000000037fff] pages 26
[    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0130000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 00019ebe8c]    TEXT DATA BSS ==> [0001000000 - 00019ebe8c]
[    0.000000]   #3 [0037832000 - 0037fef993]          RAMDISK ==> [0037832000 - 0037fef993]
[    0.000000]   #4 [000009e800 - 0000100000]    BIOS reserved ==> [000009e800 - 0000100000]
[    0.000000]   #5 [00019ec000 - 00019ec0f4]              BRK ==> [00019ec000 - 00019ec0f4]
[    0.000000]   #6 [0000008000 - 000000c000]          PGTABLE ==> [0000008000 - 000000c000]
[    0.000000]   #7 [000000c000 - 000000d000]          PGTABLE ==> [000000c000 - 000000d000]
[    0.000000] found SMP MP-table at [ffff8800000f4120] f4120
[    0.000000]  [ffffea0000000000-ffffea00043fffff] PMD -> [ffff880028600000-ffff88002bffffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00130000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000001
[    0.000000]     0: 0x00000006 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000cfe90
[    0.000000]     0: 0x00100000 -> 0x00130000
[    0.000000] On node 0 totalpages: 1048105
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 105 pages reserved
[    0.000000]   DMA zone: 3832 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 833224 pages, LIFO batch:31
[    0.000000]   Normal zone: 2688 pages used for memmap
[    0.000000]   Normal zone: 193920 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cfe90000 - 00000000cfee0000
[    0.000000] PM: Registered nosave memory: 00000000cfee0000 - 00000000cfee3000
[    0.000000] PM: Registered nosave memory: 00000000cfee3000 - 00000000cfef0000
[    0.000000] PM: Registered nosave memory: 00000000cfef0000 - 00000000cff00000
[    0.000000] PM: Registered nosave memory: 00000000cff00000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at cff00000 (gap: cff00000:10100000)
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages at ffff880028022000, static data 90720 bytes
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1030976
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-21-generic root=UUID=1e2405d2-d183-4723-9e92-650d1d597c11 ro splash
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
[    0.000000] Memory: 4048252k/4980736k available (5332k kernel code, 788316k absent, 144168k reserved, 3018k data, 668k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] NR_IRQS:4352 nr_irqs:440
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2493.868 MHz processor.
[    0.000740] Console: colour VGA+ 80x25
[    0.000742] console [tty0] enabled
[    0.010000] allocated 41943040 bytes of page_cgroup
[    0.010000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.010000] hpet clockevent registered
[    0.010000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.010000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4987.73 BogoMIPS (lpj=24938680)
[    0.010000] Security Framework initialized
[    0.010000] AppArmor: AppArmor initialized
[    0.010000] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.010000] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.010000] Mount-cache hash table entries: 256
[    0.010000] Initializing cgroup subsys ns
[    0.010000] Initializing cgroup subsys cpuacct
[    0.010000] Initializing cgroup subsys memory
[    0.010000] Initializing cgroup subsys devices
[    0.010000] Initializing cgroup subsys freezer
[    0.010000] Initializing cgroup subsys net_cls
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 2048K
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
[    0.020048] Setting APIC routing to flat
[    0.020376] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.121960] CPU0: Intel(R) Core(TM)2 Quad CPU    Q8300  @ 2.50GHz stepping 0a
[    0.130000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.010000] Initializing CPU#1
[    0.010000] Calibrating delay using timer specific routine.. 4987.49 BogoMIPS (lpj=24937467)
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 2048K
[    0.010000] CPU 1/0x1 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 1
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] CPU1: Thermal monitoring enabled (TM2)
[    0.010000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.281266] CPU1: Intel(R) Core(TM)2 Quad CPU    Q8300  @ 2.50GHz stepping 0a
[    0.282193] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.290095] Booting processor 2 APIC 0x3 ip 0x6000
[    0.010000] Initializing CPU#2
[    0.010000] Calibrating delay using timer specific routine.. 4987.51 BogoMIPS (lpj=24937582)
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 2048K
[    0.010000] CPU 2/0x3 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 3
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] CPU2: Thermal monitoring enabled (TM2)
[    0.010000] x86 PAT enabled: cpu 2, old 0x7040600070406, new 0x7010600070106
[    0.451282] CPU2: Intel(R) Core(TM)2 Quad CPU    Q8300  @ 2.50GHz stepping 0a
[    0.451640] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.460069] Booting processor 3 APIC 0x2 ip 0x6000
[    0.010000] Initializing CPU#3
[    0.010000] Calibrating delay using timer specific routine.. 4987.51 BogoMIPS (lpj=24937574)
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 2048K
[    0.010000] CPU 3/0x2 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 2
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] CPU3: Thermal monitoring enabled (TM2)
[    0.010000] x86 PAT enabled: cpu 3, old 0x7040600070406, new 0x7010600070106
[    0.621300] CPU3: Intel(R) Core(TM)2 Quad CPU    Q8300  @ 2.50GHz stepping 0a
[    0.621660] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[    0.630009] Brought up 4 CPUs
[    0.630048] Total of 4 processors activated (19950.26 BogoMIPS).
[    0.630122] CPU0 attaching sched-domain:
[    0.630125]  domain 0: span 0-1 level MC
[    0.630127]   groups: 0 1
[    0.630130]   domain 1: span 0-3 level CPU
[    0.630132]    groups: 0-1 2-3
[    0.630136] CPU1 attaching sched-domain:
[    0.630137]  domain 0: span 0-1 level MC
[    0.630139]   groups: 1 0
[    0.630142]   domain 1: span 0-3 level CPU
[    0.630143]    groups: 0-1 2-3
[    0.630147] CPU2 attaching sched-domain:
[    0.630148]  domain 0: span 2-3 level MC
[    0.630150]   groups: 2 3
[    0.630152]   domain 1: span 0-3 level CPU
[    0.630154]    groups: 2-3 0-1
[    0.630158] CPU3 attaching sched-domain:
[    0.630159]  domain 0: span 2-3 level MC
[    0.630161]   groups: 3 2
[    0.630163]   domain 1: span 0-3 level CPU
[    0.630165]    groups: 2-3 0-1
[    0.630269] Booting paravirtualized kernel on bare hardware
[    0.630269] regulator: core version 0.5
[    0.630269] Time: 15:21:08  Date: 05/14/10
[    0.630269] NET: Registered protocol family 16
[    0.630276] ACPI: bus type pci registered
[    0.630360] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.630391] PCI: MCFG area at e0000000 reserved in E820
[    0.637044] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.637073] PCI: Using configuration type 1 for base access
[    0.640313] bio: create slab <bio-0> at 0
[    0.640495] ACPI: EC: Look up EC in DSDT
[    0.644600] ACPI: Interpreter enabled
[    0.644634] ACPI: (supports S0 S3 S4 S5)
[    0.644769] ACPI: Using IOAPIC for interrupt routing
[    0.647999] ACPI: No dock devices found.
[    0.648112] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.648218] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.648249] pci 0000:00:01.0: PME# disabled
[    0.648335] pci 0000:00:1a.0: reg 20 io port: [0xff00-0xff1f]
[    0.648392] pci 0000:00:1a.1: reg 20 io port: [0xfe00-0xfe1f]
[    0.648448] pci 0000:00:1a.2: reg 20 io port: [0xfd00-0xfd1f]
[    0.648497] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfdfff000-0xfdfff3ff]
[    0.648535] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.648566] pci 0000:00:1a.7: PME# disabled
[    0.648623] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfdff8000-0xfdffbfff]
[    0.648656] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.648687] pci 0000:00:1b.0: PME# disabled
[    0.648760] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.648791] pci 0000:00:1c.0: PME# disabled
[    0.648869] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.648900] pci 0000:00:1c.5: PME# disabled
[    0.648971] pci 0000:00:1d.0: reg 20 io port: [0xfc00-0xfc1f]
[    0.649029] pci 0000:00:1d.1: reg 20 io port: [0xfb00-0xfb1f]
[    0.649085] pci 0000:00:1d.2: reg 20 io port: [0xfa00-0xfa1f]
[    0.649134] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfdffe000-0xfdffe3ff]
[    0.649172] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.650004] pci 0000:00:1d.7: PME# disabled
[    0.650130] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[    0.650165] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.650196] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0800 (mask 003f)
[    0.650230] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0290 (mask 003f)
[    0.650306] pci 0000:00:1f.2: reg 10 io port: [0xf900-0xf907]
[    0.650310] pci 0000:00:1f.2: reg 14 io port: [0xf800-0xf803]
[    0.650315] pci 0000:00:1f.2: reg 18 io port: [0xf700-0xf707]
[    0.650320] pci 0000:00:1f.2: reg 1c io port: [0xf600-0xf603]
[    0.650324] pci 0000:00:1f.2: reg 20 io port: [0xf500-0xf50f]
[    0.650329] pci 0000:00:1f.2: reg 24 io port: [0xf400-0xf40f]
[    0.650366] pci 0000:00:1f.3: reg 10 64bit mmio: [0xfdffd000-0xfdffd0ff]
[    0.650377] pci 0000:00:1f.3: reg 20 io port: [0x500-0x51f]
[    0.650412] pci 0000:00:1f.5: reg 10 io port: [0xf200-0xf207]
[    0.650417] pci 0000:00:1f.5: reg 14 io port: [0xf100-0xf103]
[    0.650421] pci 0000:00:1f.5: reg 18 io port: [0xf000-0xf007]
[    0.650426] pci 0000:00:1f.5: reg 1c io port: [0xef00-0xef03]
[    0.650431] pci 0000:00:1f.5: reg 20 io port: [0xee00-0xee0f]
[    0.650435] pci 0000:00:1f.5: reg 24 io port: [0xed00-0xed0f]
[    0.650482] pci 0000:01:00.0: reg 10 64bit mmio: [0xd0000000-0xdfffffff]
[    0.650489] pci 0000:01:00.0: reg 18 64bit mmio: [0xfdce0000-0xfdceffff]
[    0.650494] pci 0000:01:00.0: reg 20 io port: [0xae00-0xaeff]
[    0.650501] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.650516] pci 0000:01:00.0: supports D1 D2
[    0.650543] pci 0000:01:00.1: reg 10 64bit mmio: [0xfdcfc000-0xfdcfffff]
[    0.650571] pci 0000:01:00.1: supports D1 D2
[    0.650610] pci 0000:00:01.0: bridge io port: [0xa000-0xafff]
[    0.650612] pci 0000:00:01.0: bridge 32bit mmio: [0xfdc00000-0xfdcfffff]
[    0.650615] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.650649] pci 0000:00:1c.0: bridge io port: [0xd000-0xdfff]
[    0.650652] pci 0000:00:1c.0: bridge 32bit mmio: [0xfd900000-0xfd9fffff]
[    0.650657] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xfd800000-0xfd8fffff]
[    0.650696] pci 0000:03:00.0: reg 10 io port: [0xce00-0xceff]
[    0.650714] pci 0000:03:00.0: reg 18 64bit mmio: [0xfddff000-0xfddfffff]
[    0.650726] pci 0000:03:00.0: reg 20 64bit mmio: [0xfdde0000-0xfddeffff]
[    0.650733] pci 0000:03:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.650768] pci 0000:03:00.0: supports D1 D2
[    0.650769] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.650802] pci 0000:03:00.0: PME# disabled
[    0.650878] pci 0000:00:1c.5: bridge io port: [0xc000-0xcfff]
[    0.650881] pci 0000:00:1c.5: bridge 32bit mmio: [0xfde00000-0xfdefffff]
[    0.650886] pci 0000:00:1c.5: bridge 64bit mmio pref: [0xfdd00000-0xfddfffff]
[    0.650928] pci 0000:00:1e.0: transparent bridge
[    0.650958] pci 0000:00:1e.0: bridge io port: [0xb000-0xbfff]
[    0.650961] pci 0000:00:1e.0: bridge 32bit mmio: [0xfdb00000-0xfdbfffff]
[    0.650966] pci 0000:00:1e.0: bridge 64bit mmio pref: [0xfda00000-0xfdafffff]
[    0.650982] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.651096] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.651150] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX5._PRT]
[    0.651193] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.663981] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[    0.664367] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[    0.664751] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.665134] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.665519] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.665952] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 *7 9 10 11 12 14 15)
[    0.666335] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.666769] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[    0.667203] SCSI subsystem initialized
[    0.667254] libata version 3.00 loaded.
[    0.667254] usbcore: registered new interface driver usbfs
[    0.667254] usbcore: registered new interface driver hub
[    0.667254] usbcore: registered new device driver usb
[    0.667254] ACPI: WMI: Mapper loaded
[    0.667254] PCI: Using ACPI for IRQ routing
[    0.690006] Bluetooth: Core ver 2.15
[    0.690050] NET: Registered protocol family 31
[    0.690050] Bluetooth: HCI device and connection manager initialized
[    0.690074] Bluetooth: HCI socket layer initialized
[    0.690104] NetLabel: Initializing
[    0.690133] NetLabel:  domain hash size = 128
[    0.690178] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.690215] NetLabel:  unlabeled traffic allowed by default
[    0.690286] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.690434] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.730008] Switched to high resolution mode on CPU 0
[    0.731723] Switched to high resolution mode on CPU 2
[    0.731739] Switched to high resolution mode on CPU 3
[    0.732266] Switched to high resolution mode on CPU 1
[    0.750010] pnp: PnP ACPI init
[    0.750050] ACPI: bus type pnp registered
[    0.751338] pnp: PnP ACPI: found 11 devices
[    0.751367] ACPI: ACPI bus type pnp unregistered
[    0.751403] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.751434] system 00:01: ioport range 0x800-0x87f has been reserved
[    0.751464] system 00:01: ioport range 0x290-0x297 has been reserved
[    0.751494] system 00:01: ioport range 0x880-0x88f has been reserved
[    0.751527] system 00:07: ioport range 0x400-0x4bf could not be reserved
[    0.751560] system 00:09: iomem range 0xe0000000-0xefffffff has been reserved
[    0.751592] system 00:0a: iomem range 0xf0000-0xfffff could not be reserved
[    0.751623] system 00:0a: iomem range 0xcff00000-0xcfffffff could not be reserved
[    0.751656] system 00:0a: iomem range 0xfed00000-0xfed000ff has been reserved
[    0.751687] system 00:0a: iomem range 0xcfee0000-0xcfefffff could not be reserved
[    0.751720] system 00:0a: iomem range 0x0-0x9ffff could not be reserved
[    0.751751] system 00:0a: iomem range 0x100000-0xcfedffff could not be reserved
[    0.751784] system 00:0a: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.751818] system 00:0a: iomem range 0xfed14000-0xfed1dfff has been reserved
[    0.751848] system 00:0a: iomem range 0xfed20000-0xfed9ffff has been reserved
[    0.751878] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.751909] system 00:0a: iomem range 0xffb00000-0xffb7ffff has been reserved
[    0.751939] system 00:0a: iomem range 0xfff00000-0xffffffff has been reserved
[    0.751970] system 00:0a: iomem range 0xe0000-0xeffff has been reserved
[    0.756637] AppArmor: AppArmor Filesystem Enabled
[    0.756700] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.756731] pci 0000:00:01.0:   IO window: 0xa000-0xafff
[    0.756762] pci 0000:00:01.0:   MEM window: 0xfdc00000-0xfdcfffff
[    0.756793] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.756829] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.756860] pci 0000:00:1c.0:   IO window: 0xd000-0xdfff
[    0.756892] pci 0000:00:1c.0:   MEM window: 0xfd900000-0xfd9fffff
[    0.756924] pci 0000:00:1c.0:   PREFETCH window: 0x000000fd800000-0x000000fd8fffff
[    0.756961] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:03
[    0.756991] pci 0000:00:1c.5:   IO window: 0xc000-0xcfff
[    0.757023] pci 0000:00:1c.5:   MEM window: 0xfde00000-0xfdefffff
[    0.757055] pci 0000:00:1c.5:   PREFETCH window: 0x000000fdd00000-0x000000fddfffff
[    0.757092] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:04
[    0.757122] pci 0000:00:1e.0:   IO window: 0xb000-0xbfff
[    0.757154] pci 0000:00:1e.0:   MEM window: 0xfdb00000-0xfdbfffff
[    0.757186] pci 0000:00:1e.0:   PREFETCH window: 0x000000fda00000-0x000000fdafffff
[    0.757227]   alloc irq_desc for 16 on node 0
[    0.757229]   alloc kstat_irqs on node 0
[    0.757233] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.757264] pci 0000:00:01.0: setting latency timer to 64
[    0.757270] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.757301] pci 0000:00:1c.0: setting latency timer to 64
[    0.757306]   alloc irq_desc for 17 on node 0
[    0.757307]   alloc kstat_irqs on node 0
[    0.757309] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.757341] pci 0000:00:1c.5: setting latency timer to 64
[    0.757345] pci 0000:00:1e.0: setting latency timer to 64
[    0.757349] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.757351] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.757353] pci_bus 0000:01: resource 0 io:  [0xa000-0xafff]
[    0.757355] pci_bus 0000:01: resource 1 mem: [0xfdc00000-0xfdcfffff]
[    0.757357] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.757359] pci_bus 0000:02: resource 0 io:  [0xd000-0xdfff]
[    0.757361] pci_bus 0000:02: resource 1 mem: [0xfd900000-0xfd9fffff]
[    0.757362] pci_bus 0000:02: resource 2 pref mem [0xfd800000-0xfd8fffff]
[    0.757364] pci_bus 0000:03: resource 0 io:  [0xc000-0xcfff]
[    0.757366] pci_bus 0000:03: resource 1 mem: [0xfde00000-0xfdefffff]
[    0.757368] pci_bus 0000:03: resource 2 pref mem [0xfdd00000-0xfddfffff]
[    0.757370] pci_bus 0000:04: resource 0 io:  [0xb000-0xbfff]
[    0.757372] pci_bus 0000:04: resource 1 mem: [0xfdb00000-0xfdbfffff]
[    0.757373] pci_bus 0000:04: resource 2 pref mem [0xfda00000-0xfdafffff]
[    0.757375] pci_bus 0000:04: resource 3 io:  [0x00-0xffff]
[    0.757377] pci_bus 0000:04: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.757405] NET: Registered protocol family 2
[    0.757573] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.758552] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.761661] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.762074] TCP: Hash tables configured (established 524288 bind 65536)
[    0.762104] TCP reno registered
[    0.762236] NET: Registered protocol family 1
[    0.762321] Trying to unpack rootfs image as initramfs...
[    0.912659] Freeing initrd memory: 7926k freed
[    0.915265] Scanning for low memory corruption every 60 seconds
[    0.915419] audit: initializing netlink socket (disabled)
[    0.915460] type=2000 audit(1273850467.910:1): initialized
[    0.923665] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.924968] VFS: Disk quotas dquot_6.5.2
[    0.925040] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.925555] fuse init (API version 7.12)
[    0.925646] msgmni has been set to 7922
[    0.926025] alg: No test for stdrng (krng)
[    0.926060] io scheduler noop registered
[    0.926090] io scheduler anticipatory registered
[    0.926119] io scheduler deadline registered
[    0.926179] io scheduler cfq registered (default)
[    0.926339] pci 0000:01:00.0: Boot video device
[    0.926466]   alloc irq_desc for 24 on node 0
[    0.926467]   alloc kstat_irqs on node 0
[    0.926475] pcieport-driver 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.926480] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    0.926597]   alloc irq_desc for 25 on node 0
[    0.926599]   alloc kstat_irqs on node 0
[    0.926604] pcieport-driver 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.926611] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.926746]   alloc irq_desc for 26 on node 0
[    0.926747]   alloc kstat_irqs on node 0
[    0.926753] pcieport-driver 0000:00:1c.5: irq 26 for MSI/MSI-X
[    0.926759] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    0.926834] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.926930] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.927056] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.927091] ACPI: Power Button [PWRF]
[    0.927158] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.927759] ACPI: Power Button [PWRB]
[    0.927826] fan PNP0C0B:00: registered as cooling_device0
[    0.927860] ACPI: Fan [FAN] (on)
[    0.928313] ACPI: SSDT 00000000cfee7440 0022A (v01  PmRef  Cpu0Ist 00003000 INTL 20041203)
[    0.928540] processor LNXCPU:00: registered as cooling_device1
[    0.928764] ACPI: SSDT 00000000cfee7900 00152 (v01  PmRef  Cpu1Ist 00003000 INTL 20041203)
[    0.928980] processor LNXCPU:01: registered as cooling_device2
[    0.929200] ACPI: SSDT 00000000cfee7a60 00152 (v01  PmRef  Cpu2Ist 00003000 INTL 20041203)
[    0.929416] processor LNXCPU:02: registered as cooling_device3
[    0.929643] ACPI: SSDT 00000000cfee7bc0 00152 (v01  PmRef  Cpu3Ist 00003000 INTL 20041203)
[    0.929858] processor LNXCPU:03: registered as cooling_device4
[    0.931352] thermal LNXTHERM:01: registered as thermal_zone0
[    0.931386] ACPI: Thermal Zone [THRM] (40 C)
[    0.932314] Linux agpgart interface v0.103
[    0.932349] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.932464] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.932582] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.933496] brd: module loaded
[    0.933864] loop: module loaded
[    0.933945] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.934103] ata_piix 0000:00:1f.2: version 2.13
[    0.934116]   alloc irq_desc for 19 on node 0
[    0.934118]   alloc kstat_irqs on node 0
[    0.934122] ata_piix 0000:00:1f.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.934163] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.934334] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.934414] scsi0 : ata_piix
[    0.934538] scsi1 : ata_piix
[    0.935108] ata1: SATA max UDMA/133 cmd 0xf900 ctl 0xf800 bmdma 0xf500 irq 19
[    0.935140] ata2: SATA max UDMA/133 cmd 0xf700 ctl 0xf600 bmdma 0xf508 irq 19
[    0.935223] ata_piix 0000:00:1f.5: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.935255] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    0.935420] ata_piix 0000:00:1f.5: setting latency timer to 64
[    0.935458] scsi2 : ata_piix
[    0.935560] scsi3 : ata_piix
[    0.935824] ata3: SATA max UDMA/133 cmd 0xf200 ctl 0xf100 bmdma 0xee00 irq 19
[    0.935856] ata4: SATA max UDMA/133 cmd 0xf000 ctl 0xef00 bmdma 0xee08 irq 19
[    0.936512] Fixed MDIO Bus: probed
[    0.936564] PPP generic driver version 2.4.2
[    0.936658] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.936750]   alloc irq_desc for 18 on node 0
[    0.936751]   alloc kstat_irqs on node 0
[    0.936755] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.936822] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.936825] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.936884] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.940822] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.940832] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfdfff000
[    0.960023] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.960115] usb usb1: configuration #1 chosen from 1 choice
[    0.960177] hub 1-0:1.0: USB hub found
[    0.960228] hub 1-0:1.0: 6 ports detected
[    0.960434]   alloc irq_desc for 23 on node 0
[    0.960436]   alloc kstat_irqs on node 0
[    0.960439] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.960475] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.960478] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.960528] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.964467] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.964477] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfdffe000
[    0.980007] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.980088] usb usb2: configuration #1 chosen from 1 choice
[    0.980143] hub 2-0:1.0: USB hub found
[    0.980176] hub 2-0:1.0: 6 ports detected
[    0.980267] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.980307] uhci_hcd: USB Universal Host Controller Interface driver
[    0.980419] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.980453] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.980456] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.980505] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.980563] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000ff00
[    0.980649] usb usb3: configuration #1 chosen from 1 choice
[    0.980696] hub 3-0:1.0: USB hub found
[    0.980729] hub 3-0:1.0: 2 ports detected
[    0.980834]   alloc irq_desc for 21 on node 0
[    0.980835]   alloc kstat_irqs on node 0
[    0.980839] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.980872] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.980874] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.980925] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.980983] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000fe00
[    0.981068] usb usb4: configuration #1 chosen from 1 choice
[    0.981114] hub 4-0:1.0: USB hub found
[    0.981146] hub 4-0:1.0: 2 ports detected
[    0.981252] uhci_hcd 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.981285] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.981288] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.981336] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.981388] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000fd00
[    0.981477] usb usb5: configuration #1 chosen from 1 choice
[    0.981523] hub 5-0:1.0: USB hub found
[    0.981555] hub 5-0:1.0: 2 ports detected
[    0.981661] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.981694] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.981696] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.981745] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.981797] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000fc00
[    0.981880] usb usb6: configuration #1 chosen from 1 choice
[    0.981927] hub 6-0:1.0: USB hub found
[    0.981958] hub 6-0:1.0: 2 ports detected
[    0.982061] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.982094] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.982097] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.982148] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.982199] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000fb00
[    0.982281] usb usb7: configuration #1 chosen from 1 choice
[    0.982330] hub 7-0:1.0: USB hub found
[    0.982365] hub 7-0:1.0: 2 ports detected
[    0.982468] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.982501] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.982508] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.982562] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.982613] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000fa00
[    0.982700] usb usb8: configuration #1 chosen from 1 choice
[    0.982747] hub 8-0:1.0: USB hub found
[    0.982778] hub 8-0:1.0: 2 ports detected
[    0.982882] PNP: No PS/2 controller found. Probing ports directly.
[    0.983181] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.983215] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.983332] mice: PS/2 mouse device common for all mice
[    0.983445] rtc_cmos 00:04: RTC can wake from S4
[    0.983500] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.983549] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.983673] device-mapper: uevent: version 1.0.3
[    0.983797] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.983915] device-mapper: multipath: version 1.1.0 loaded
[    0.983947] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.984159] cpuidle: using governor ladder
[    0.984192] cpuidle: using governor menu
[    0.984534] TCP cubic registered
[    0.984659] NET: Registered protocol family 10
[    0.985028] lo: Disabled Privacy Extensions
[    0.985283] NET: Registered protocol family 17
[    0.985323] Bluetooth: L2CAP ver 2.13
[    0.985352] Bluetooth: L2CAP socket layer initialized
[    0.985382] Bluetooth: SCO (Voice Link) ver 0.6
[    0.985411] Bluetooth: SCO socket layer initialized
[    0.985457] Bluetooth: RFCOMM TTY layer initialized
[    0.985487] Bluetooth: RFCOMM socket layer initialized
[    0.985516] Bluetooth: RFCOMM ver 1.11
[    0.986134] PM: Resume from disk failed.
[    0.986145] registered taskstats version 1
[    0.986275]   Magic number: 10:458:386
[    0.986308] usb usb4: hash matches
[    0.986359] thermal cooling_device1: hash matches
[    0.986439] rtc_cmos 00:04: setting system clock to 2010-05-14 15:21:10 UTC (1273850470)
[    0.986477] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.986506] EDD information not available.
[    1.290658] ata3: SATA link down (SStatus 0 SControl 300)
[    1.301279] ata4: SATA link down (SStatus 0 SControl 300)
[    1.400008] usb 1-4: new high speed USB device using ehci_hcd and address 3
[    1.790072] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.790112] ata1.01: SATA link down (SStatus 0 SControl 300)
[    1.810050] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.810092] ata2.01: SATA link down (SStatus 0 SControl 300)
[    1.810130] ata2.01: link offline, clearing class 3 to NONE
[    1.810608] ata1.00: ATA-8: ST31000528AS, CC45, max UDMA/133
[    1.810641] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.830197] ata2.00: ATAPI: TSSTcorp DVD+/-RW TS-H653G, DW10, max UDMA/100
[    1.830239] ata2.00: applying bridge limits
[    1.850397] ata1.00: configured for UDMA/133
[    1.850526] scsi 0:0:0:0: Direct-Access     ATA      ST31000528AS     CC45 PQ: 0 ANSI: 5
[    1.850682] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.850750] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.850818] sd 0:0:0:0: [sda] Write Protect is off
[    1.850848] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.850867] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.851004]  sda: sda1 < sda5
[    1.873948] ata2.00: configured for UDMA/100
[    1.875626] scsi 1:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-H653G DW10 PQ: 0 ANSI: 5
[    1.879098] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.879135] Uniform CD-ROM driver Revision: 3.20
[    1.879251] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.879297] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.891086]  sda6 > sda2 sda3 sda4
[    1.891535] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.891591] Freeing unused kernel memory: 668k freed
[    1.891766] Write protecting the kernel read-only data: 7600k
[    1.972642] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.972698] r8169 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.972778] r8169 0000:03:00.0: setting latency timer to 64
[    1.972818]   alloc irq_desc for 27 on node 0
[    1.972820]   alloc kstat_irqs on node 0
[    1.972832] r8169 0000:03:00.0: irq 27 for MSI/MSI-X
[    1.973295] eth0: RTL8102e at 0xffffc90000670000, 00:25:64:e9:69:fa, XID 24a00000 IRQ 27
[    2.737578] xor: automatically using best checksumming function: generic_sse
[    2.781244]    generic_sse:  9502.800 MB/sec
[    2.781245] xor: using function: generic_sse (9502.800 MB/sec)
[    2.782934] device-mapper: dm-raid45: initialized v0.2594b
[    2.940893] PM: Starting manual resume from disk
[    2.940896] PM: Resume from partition 8:6
[    2.940898] PM: Checking hibernation image.
[    2.941073] PM: Resume from disk failed.
[    2.973636] EXT4-fs (sda5): barriers enabled
[    2.998600] kjournald2 starting: pid 401, dev sda5:8, commit interval 5 seconds
[    2.998689] EXT4-fs (sda5): delayed allocation enabled
[    2.998694] EXT4-fs: file extents enabled
[    3.037028] EXT4-fs: mballoc enabled
[    3.037042] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    3.477085] type=1505 audit(1273850472.984:2): operation="profile_load" pid=431 name=/usr/share/gdm/guest-session/Xsession
[    3.479027] type=1505 audit(1273850472.984:3): operation="profile_load" pid=432 name=/sbin/dhclient3
[    3.479594] type=1505 audit(1273850472.984:4): operation="profile_load" pid=432 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    3.479905] type=1505 audit(1273850472.984:5): operation="profile_load" pid=432 name=/usr/lib/connman/scripts/dhclient-script
[    3.519139] type=1505 audit(1273850473.024:6): operation="profile_load" pid=433 name=/usr/bin/evince
[    3.528441] type=1505 audit(1273850473.034:7): operation="profile_load" pid=433 name=/usr/bin/evince-previewer
[    3.533829] type=1505 audit(1273850473.044:8): operation="profile_load" pid=433 name=/usr/bin/evince-thumbnailer
[    3.545381] type=1505 audit(1273850473.054:9): operation="profile_load" pid=435 name=/usr/lib/cups/backend/cups-pdf
[    3.546064] type=1505 audit(1273850473.054:10): operation="profile_load" pid=435 name=/usr/sbin/cupsd
[   14.461078] udev: starting version 147
[   14.486088] Adding 11880028k swap on /dev/sda6.  Priority:-1 extents:1 across:11880028k 
[   14.492851] lp: driver loaded but no devices found
[   14.541617] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   14.541621] Disabling lock debugging due to kernel taint
[   14.554522] [fglrx] Maximum main memory to use for locked dma buffers: 3799 MBytes.
[   14.554656] [fglrx]   vendor: 1002 device: 954f count: 1
[   14.554941] [fglrx] ioport: bar 4, base 0xae00, size: 0x100
[   14.554954] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.554958] pci 0000:01:00.0: setting latency timer to 64
[   14.555137] [fglrx] Kernel PAT support is enabled
[   14.555161] [fglrx] module loaded - fglrx 8.66.10 [Sep  3 2009] with 1 minors
[   14.564916] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   14.565390] dell-wmi: No known WMI GUID found
[   14.565516] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   14.565628] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   14.575915] ip_tables: (C) 2000-2006 Netfilter Core Team
[   14.654114] EXT4-fs (sda5): internal journal on sda5:8
[   14.718221] hda_codec: Unknown model for ALC888, trying auto-probe from BIOS...
[   14.718301] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input3
[   14.721819] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   14.721870] HDA Intel 0000:01:00.1: setting latency timer to 64
[   14.950059] __ratelimit: 6 callbacks suppressed
[   14.950062] type=1505 audit(1273843284.454:13): operation="profile_replace" pid=960 name=/usr/share/gdm/guest-session/Xsession
[   14.951380] type=1505 audit(1273843284.464:14): operation="profile_replace" pid=961 name=/sbin/dhclient3
[   14.951947] type=1505 audit(1273843284.464:15): operation="profile_replace" pid=961 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   14.952256] type=1505 audit(1273843284.464:16): operation="profile_replace" pid=961 name=/usr/lib/connman/scripts/dhclient-script
[   14.955002] type=1505 audit(1273843284.464:17): operation="profile_replace" pid=962 name=/usr/bin/evince
[   14.964296] type=1505 audit(1273843284.474:18): operation="profile_replace" pid=962 name=/usr/bin/evince-previewer
[   14.969659] type=1505 audit(1273843284.474:19): operation="profile_replace" pid=962 name=/usr/bin/evince-thumbnailer
[   14.977167] type=1505 audit(1273843284.484:20): operation="profile_replace" pid=964 name=/usr/lib/cups/backend/cups-pdf
[   14.977832] type=1505 audit(1273843284.484:21): operation="profile_replace" pid=964 name=/usr/sbin/cupsd
[   14.979757] type=1505 audit(1273843284.484:22): operation="profile_replace" pid=965 name=/usr/sbin/mysqld-akonadi
[   15.115955] r8169: eth0: link up
[   15.115968] r8169: eth0: link up
[   15.657878] ppdev: user-space parallel port driver
[   15.941590] usplash:347 freeing invalid memtype ffffffffd0000000-ffffffffd1000000
[   16.251502]   alloc irq_desc for 28 on node 0
[   16.251505]   alloc kstat_irqs on node 0
[   16.251514] fglrx_pci 0000:01:00.0: irq 28 for MSI/MSI-X
[   16.251967] [fglrx] Firegl kernel thread PID: 1577
[   16.531266] usb 1-4: device descriptor read/64, error -110
[   17.367341] [fglrx] Gart USWC size:1236 M.
[   17.367344] [fglrx] Gart cacheable size:491 M.
[   17.367349] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   17.367351] [fglrx] Reserved FB block: Unshared offset:fc1f000, size:3e1000 
[   17.367353] [fglrx] Reserved FB block: Unshared offset:1fffb000, size:5000 
[   17.683559] [fglrx:fireglAsyncioIntEnableMsgHandler] *ERROR* interrupt source ff000066 is not supported on this hardware (return code = 1)
[   25.320005] eth0: no IPv6 routers present
[   31.750010] usb 1-4: device descriptor read/64, error -110
[   31.980016] usb 1-4: new high speed USB device using ehci_hcd and address 4
[   46.933843] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   47.103766] usb 1-4: device descriptor read/64, error -110
[   62.333766] usb 1-4: device descriptor read/64, error -110
[   62.560011] usb 1-4: new high speed USB device using ehci_hcd and address 5
[   67.590152] usb 1-4: device descriptor read/8, error -110
[   72.720157] usb 1-4: device descriptor read/8, error -110
[   72.950009] usb 1-4: new high speed USB device using ehci_hcd and address 6
[   77.980155] usb 1-4: device descriptor read/8, error -110
[   83.110040] usb 1-4: device descriptor read/8, error -110
[   83.220017] hub 1-0:1.0: unable to enumerate USB device on port 4
[   83.501262] usb 2-5: new high speed USB device using ehci_hcd and address 2
[   83.654489] usb 2-5: configuration #1 chosen from 1 choice
[   83.684319] Initializing USB Mass Storage driver...
[   83.684447] scsi4 : SCSI emulation for USB Mass Storage devices
[   83.684807] usb-storage: device found at 2
[   83.684810] usb-storage: waiting for device to settle before scanning
[   83.684820] usbcore: registered new interface driver usb-storage
[   83.684824] USB Mass Storage support registered.
[   83.930011] usb 4-1: new full speed USB device using uhci_hcd and address 2
[   84.107187] usb 4-1: configuration #1 chosen from 1 choice
[   84.110170] hub 4-1:1.0: USB hub found
[   84.112113] hub 4-1:1.0: 4 ports detected
[   84.400010] usb 4-2: new full speed USB device using uhci_hcd and address 3
[   88.680204] usb-storage: device scan complete
[   88.680691] scsi 4:0:0:0: Direct-Access     Generic- SD/MMC           1.00 PQ: 0 ANSI: 0
[   88.681188] scsi 4:0:0:1: Direct-Access     Generic- Compact Flash    1.01 PQ: 0 ANSI: 0
[   88.681690] scsi 4:0:0:2: Direct-Access     Generic- SM/xD Picture    1.02 PQ: 0 ANSI: 0
[   88.682185] scsi 4:0:0:3: Direct-Access     Generic- MS/MS-Pro        1.03 PQ: 0 ANSI: 0
[   88.682575] sd 4:0:0:0: Attached scsi generic sg2 type 0
[   88.682656] sd 4:0:0:1: Attached scsi generic sg3 type 0
[   88.682740] sd 4:0:0:2: Attached scsi generic sg4 type 0
[   88.682822] sd 4:0:0:3: Attached scsi generic sg5 type 0
[   88.684800] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[   88.686676] sd 4:0:0:1: [sdc] Attached SCSI removable disk
[   88.688055] sd 4:0:0:3: [sde] Attached SCSI removable disk
[   88.690691] sd 4:0:0:2: [sdd] Attached SCSI removable disk
[   99.523760] usb 4-2: device descriptor read/64, error -110
[  114.750011] usb 4-2: device descriptor read/64, error -110
[  114.980015] usb 4-2: new full speed USB device using uhci_hcd and address 4
[  130.100013] usb 4-2: device descriptor read/64, error -110
[  145.330012] usb 4-2: device descriptor read/64, error -110
[  145.561260] usb 4-2: new full speed USB device using uhci_hcd and address 5
[  150.581980] usb 4-2: device descriptor read/8, error -110
[  155.711737] usb 4-2: device descriptor read/8, error -110
[  155.940010] usb 4-2: new full speed USB device using uhci_hcd and address 6
[  160.961486] usb 4-2: device descriptor read/8, error -110
[  166.091248] usb 4-2: device descriptor read/8, error -110
[  166.200019] hub 4-0:1.0: unable to enumerate USB device on port 2
[  166.480010] usb 5-1: new low speed USB device using uhci_hcd and address 2
[  166.660190] usb 5-1: configuration #1 chosen from 1 choice
[  166.698491] usbcore: registered new interface driver hiddev
[  166.713395] input: Dell Dell USB Entry Keyboard as /devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1:1.0/input/input4
[  166.713463] generic-usb 0003:413C:2107.0001: input,hidraw0: USB HID v1.10 Keyboard [Dell Dell USB Entry Keyboard] on usb-0000:00:1a.2-1/input0
[  166.713479] usbcore: registered new interface driver usbhid
[  166.713482] usbhid: v2.6:USB HID core driver
[  166.940012] usb 5-2: new low speed USB device using uhci_hcd and address 3
[  167.112173] usb 5-2: configuration #1 chosen from 1 choice
[  167.128339] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.0/input/input5
[  167.128424] generic-usb 0003:0461:4D22.0002: input,hidraw1: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:1a.2-2/input0
[  201.283759] usb 4-2: new full speed USB device using uhci_hcd and address 7
[  216.402515] usb 4-2: device descriptor read/64, error -110
[  231.630015] usb 4-2: device descriptor read/64, error -110
[  231.860015] usb 4-2: new full speed USB device using uhci_hcd and address 8
[  246.992515] usb 4-2: device descriptor read/64, error -110
[  262.220012] usb 4-2: device descriptor read/64, error -110
[  262.450010] usb 4-2: new full speed USB device using uhci_hcd and address 9
[  267.471404] usb 4-2: device descriptor read/8, error -110
[  272.601162] usb 4-2: device descriptor read/8, error -110
[  272.830011] usb 4-2: new full speed USB device using uhci_hcd and address 10
[  277.851914] usb 4-2: device descriptor read/8, error -110
[  282.981670] usb 4-2: device descriptor read/8, error -110
[  283.090019] hub 4-0:1.0: unable to enumerate USB device on port 2
[  283.091428] usb 4-1: USB disconnect, address 2
[  283.210015] usb 4-1: new full speed USB device using uhci_hcd and address 11
[  283.387727] usb 4-1: configuration #1 chosen from 1 choice
[  283.390708] hub 4-1:1.0: USB hub found
[  283.392648] hub 4-1:1.0: 4 ports detected
[  477.760012] usb 4-2: new full speed USB device using uhci_hcd and address 12
[  492.880013] usb 4-2: device descriptor read/64, error -110
[  508.113506] usb 4-2: device descriptor read/64, error -110
[  508.343769] usb 4-2: new full speed USB device using uhci_hcd and address 13
[  523.470025] usb 4-2: device descriptor read/64, error -110
[  538.700012] usb 4-2: device descriptor read/64, error -110
[  538.930010] usb 4-2: new full speed USB device using uhci_hcd and address 14
[  543.951149] usb 4-2: device descriptor read/8, error -110
[  549.081914] usb 4-2: device descriptor read/8, error -110
[  549.310012] usb 4-2: new full speed USB device using uhci_hcd and address 15
[  554.331663] usb 4-2: device descriptor read/8, error -110
[  559.461421] usb 4-2: device descriptor read/8, error -110
[  559.570021] hub 4-0:1.0: unable to enumerate USB device on port 2
[  559.570048] usb 4-1: USB disconnect, address 11
[  559.690013] usb 4-1: new full speed USB device using uhci_hcd and address 16
[  559.867480] usb 4-1: configuration #1 chosen from 1 choice
[  559.870442] hub 4-1:1.0: USB hub found
[  559.872400] hub 4-1:1.0: 4 ports detected

```

Thanks very much
Pietro

---

