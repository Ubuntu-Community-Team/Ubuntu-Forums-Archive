---
title: "thinkpad sl510 boot time"
date: 2010-05-22
forum: Hardware
---

### Post by AlexKpow on 2010-05-22
When my laptop boots it sits at the "_" blinking for a long time. What do you think?

[http://www.youtube.com/watch?v=y_0ChHoCHnk](http://www.youtube.com/watch?v=y_0ChHoCHnk)

my dmesg:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-22-generic (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 (Ubuntu 2.6.32-22.33-generic 2.6.32.11+drm33.2)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=537355ce-4761-48f8-be03-98e46cdeacba ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000b76b1000 (usable)
[    0.000000]  BIOS-e820: 00000000b76b1000 - 00000000b76b7000 (reserved)
[    0.000000]  BIOS-e820: 00000000b76b7000 - 00000000b77ba000 (usable)
[    0.000000]  BIOS-e820: 00000000b77ba000 - 00000000b780f000 (reserved)
[    0.000000]  BIOS-e820: 00000000b780f000 - 00000000b7908000 (usable)
[    0.000000]  BIOS-e820: 00000000b7908000 - 00000000b7b0f000 (reserved)
[    0.000000]  BIOS-e820: 00000000b7b0f000 - 00000000b7b18000 (usable)
[    0.000000]  BIOS-e820: 00000000b7b18000 - 00000000b7b1f000 (reserved)
[    0.000000]  BIOS-e820: 00000000b7b1f000 - 00000000b7b63000 (usable)
[    0.000000]  BIOS-e820: 00000000b7b63000 - 00000000b7b9f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b7b9f000 - 00000000b7be0000 (usable)
[    0.000000]  BIOS-e820: 00000000b7be0000 - 00000000b7bfd000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000b7bfd000 - 00000000b7c00000 (usable)
[    0.000000]  BIOS-e820: 00000000b7c00000 - 00000000b7e00000 (reserved)
[    0.000000]  BIOS-e820: 00000000b8000000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff800000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0xb7c00 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-D3FFF write-protect
[    0.000000]   D4000-DBFFF uncachable
[    0.000000]   DC000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0FFE00000 mask FFFE00000 write-protect
[    0.000000]   1 base 0B8000000 mask FF8000000 uncachable
[    0.000000]   2 base 000000000 mask F80000000 write-back
[    0.000000]   3 base 080000000 mask FC0000000 write-back
[    0.000000]   4 base 0B7E00000 mask FFFE00000 uncachable
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000001000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
[    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009f400 (usable)
[    0.000000]  modified: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000b76b1000 (usable)
[    0.000000]  modified: 00000000b76b1000 - 00000000b76b7000 (reserved)
[    0.000000]  modified: 00000000b76b7000 - 00000000b77ba000 (usable)
[    0.000000]  modified: 00000000b77ba000 - 00000000b780f000 (reserved)
[    0.000000]  modified: 00000000b780f000 - 00000000b7908000 (usable)
[    0.000000]  modified: 00000000b7908000 - 00000000b7b0f000 (reserved)
[    0.000000]  modified: 00000000b7b0f000 - 00000000b7b18000 (usable)
[    0.000000]  modified: 00000000b7b18000 - 00000000b7b1f000 (reserved)
[    0.000000]  modified: 00000000b7b1f000 - 00000000b7b63000 (usable)
[    0.000000]  modified: 00000000b7b63000 - 00000000b7b9f000 (ACPI NVS)
[    0.000000]  modified: 00000000b7b9f000 - 00000000b7be0000 (usable)
[    0.000000]  modified: 00000000b7be0000 - 00000000b7bfd000 (ACPI data)
[    0.000000]  modified: 00000000b7bfd000 - 00000000b7c00000 (usable)
[    0.000000]  modified: 00000000b7c00000 - 00000000b7e00000 (reserved)
[    0.000000]  modified: 00000000b8000000 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  modified: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  modified: 00000000fed18000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff800000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-00000000b7c00000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 00b7c00000 page 2M
[    0.000000] kernel direct mapping tables up to b7c00000 @ 8000-c000
[    0.000000] RAMDISK: 377fe000 - 37fefab3
[    0.000000] ACPI: RSDP 00000000000f71b0 00024 (v04 PTLTD )
[    0.000000] ACPI: XSDT 00000000b7bf2a0a 0006C (v01 LENOVO TP-6J    00001310  LTP 00000000)
[    0.000000] ACPI: FACP 00000000b7be4000 000F4 (v03 LENOVO TP-6J    00001310 ALAN 00000001)
[    0.000000] ACPI: DSDT 00000000b7be5000 0A180 (v02 LENOVO TP-6J    00001310 INTL 20050624)
[    0.000000] ACPI: FACS 00000000b7b9efc0 00040
[    0.000000] ACPI: HPET 00000000b7bfcd86 00038 (v01 LENOVO TP-6J    00001310 LOHR 0000005A)
[    0.000000] ACPI: MCFG 00000000b7bfcdbe 0003C (v01 LENOVO TP-6J    00001310 LOHR 0000005A)
[    0.000000] ACPI: APIC 00000000b7bfcdfa 00068 (v01 LENOVO TP-6J    00001310  LTP 00000000)
[    0.000000] ACPI: BOOT 00000000b7bfce62 00028 (v01 LENOVO TP-6J    00001310  LTP 00000001)
[    0.000000] ACPI: SLIC 00000000b7bfce8a 00176 (v01 LENOVO TP-6J    00001310  LTP 00000000)
[    0.000000] ACPI: SSDT 00000000b7be3000 00655 (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 00000000b7be2000 00259 (v01  PmRef  Cpu0Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 00000000b7be1000 0020F (v01  PmRef    ApTst 00003000 INTL 20050624)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-00000000b7c00000
[    0.000000] Bootmem setup node 0 0000000000000000-00000000b7c00000
[    0.000000]   NODE_DATA [000000000000a000 - 000000000000efff]
[    0.000000]   bootmap [000000000000f000 -  0000000000025f7f] pages 17
[    0.000000] (7 early reservations) ==> bootmem [0000000000 - 00b7c00000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 0001a29e64]    TEXT DATA BSS ==> [0001000000 - 0001a29e64]
[    0.000000]   #3 [00377fe000 - 0037fefab3]          RAMDISK ==> [00377fe000 - 0037fefab3]
[    0.000000]   #4 [000009f400 - 0000100000]    BIOS reserved ==> [000009f400 - 0000100000]
[    0.000000]   #5 [0001a2a000 - 0001a2a14c]              BRK ==> [0001a2a000 - 0001a2a14c]
[    0.000000]   #6 [0000008000 - 000000a000]          PGTABLE ==> [0000008000 - 000000a000]
[    0.000000] found SMP MP-table at [ffff8800000f74e0] f74e0
[    0.000000]  [ffffea0000000000-ffffea00029fffff] PMD -> [ffff880002000000-ffff8800049fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[9] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000001
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000b76b1
[    0.000000]     0: 0x000b76b7 -> 0x000b77ba
[    0.000000]     0: 0x000b780f -> 0x000b7908
[    0.000000]     0: 0x000b7b0f -> 0x000b7b18
[    0.000000]     0: 0x000b7b1f -> 0x000b7b63
[    0.000000]     0: 0x000b7b9f -> 0x000b7be0
[    0.000000]     0: 0x000b7bfd -> 0x000b7c00
[    0.000000] On node 0 totalpages: 751832
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 101 pages reserved
[    0.000000]   DMA zone: 3837 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 10234 pages used for memmap
[    0.000000]   DMA32 zone: 737604 pages, LIFO batch:31
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
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000b76b1000 - 00000000b76b7000
[    0.000000] PM: Registered nosave memory: 00000000b77ba000 - 00000000b780f000
[    0.000000] PM: Registered nosave memory: 00000000b7908000 - 00000000b7b0f000
[    0.000000] PM: Registered nosave memory: 00000000b7b18000 - 00000000b7b1f000
[    0.000000] PM: Registered nosave memory: 00000000b7b63000 - 00000000b7b9f000
[    0.000000] PM: Registered nosave memory: 00000000b7be0000 - 00000000b7bfd000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:20000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001c00000 s91544 r8192 d23144 u1048576
[    0.000000] pcpu-alloc: s91544 r8192 d23144 u1048576 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 741441
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=537355ce-4761-48f8-be03-98e46cdeacba ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 2945300k/3010560k available (5409k kernel code, 3232k absent, 62028k reserved, 2976k data, 876k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:4352 nr_irqs:424
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 30146560 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2094.790 MHz processor.
[    0.010007] Calibrating delay loop (skipped), value calculated using timer frequency.. 4189.58 BogoMIPS (lpj=20947900)
[    0.010037] Security Framework initialized
[    0.010059] AppArmor: AppArmor initialized
[    0.010439] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.013218] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.014640] Mount-cache hash table entries: 256
[    0.014808] Initializing cgroup subsys ns
[    0.014814] Initializing cgroup subsys cpuacct
[    0.014818] Initializing cgroup subsys memory
[    0.014826] Initializing cgroup subsys devices
[    0.014829] Initializing cgroup subsys freezer
[    0.014831] Initializing cgroup subsys net_cls
[    0.014853] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.014855] CPU: L2 cache: 2048K
[    0.014859] CPU 0/0x0 -> Node 0
[    0.014861] CPU: Physical Processor ID: 0
[    0.014863] CPU: Processor Core ID: 0
[    0.014866] mce: CPU supports 6 MCE banks
[    0.014875] CPU0: Thermal monitoring enabled (TM2)
[    0.014879] using mwait in idle threads.
[    0.014881] Performance Events: Core2 events, Intel PMU driver.
[    0.014887] ... version:                2
[    0.014889] ... bit width:              40
[    0.014890] ... generic registers:      2
[    0.014892] ... value mask:             000000ffffffffff
[    0.014894] ... max period:             000000007fffffff
[    0.014895] ... fixed-purpose events:   3
[    0.014897] ... event mask:             0000000700000003
[    0.023282] ACPI: Core revision 20090903
[    0.040029] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.040037] ftrace: allocating 22518 entries in 89 pages
[    0.050061] Setting APIC routing to flat
[    0.050422] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.158794] CPU0: Intel(R) Core(TM)2 Duo CPU     T6570  @ 2.10GHz stepping 0a
[    0.160000] APIC calibration not consistent with PM-Timer: 90ms instead of 100ms
[    0.160000] APIC delta adjusted to PM-Timer: 1246875 (1126108)
[    0.160000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.020000] Initializing CPU#1
[    0.020000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.020000] CPU: L2 cache: 2048K
[    0.020000] CPU 1/0x1 -> Node 0
[    0.020000] CPU: Physical Processor ID: 0
[    0.020000] CPU: Processor Core ID: 1
[    0.020000] CPU1: Thermal monitoring enabled (TM2)
[    0.310122] CPU1: Intel(R) Core(TM)2 Duo CPU     T6570  @ 2.10GHz stepping 0a
[    0.310130] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.320018] Brought up 2 CPUs
[    0.320021] Total of 2 processors activated (8379.15 BogoMIPS).
[    0.320521] CPU0 attaching sched-domain:
[    0.320525]  domain 0: span 0-1 level MC
[    0.320527]   groups: 0 1
[    0.320533] CPU1 attaching sched-domain:
[    0.320535]  domain 0: span 0-1 level MC
[    0.320537]   groups: 1 0
[    0.320626] devtmpfs: initialized
[    0.320626] regulator: core version 0.5
[    0.320626] Time: 22:10:49  Date: 05/22/10
[    0.320626] NET: Registered protocol family 16
[    0.320626] Trying to unpack rootfs image as initramfs...
[    0.320626] ACPI: bus type pci registered
[    0.320626] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.320626] PCI: MCFG area at e0000000 reserved in E820
[    0.332403] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.332407] PCI: Using configuration type 1 for base access
[    0.332455] mtrr: your CPUs had inconsistent variable MTRR settings
[    0.332456] mtrr: probably your BIOS does not setup all CPUs.
[    0.332458] mtrr: corrected configuration.
[    0.340238] bio: create slab <bio-0> at 0
[    0.341575] ACPI: EC: Look up EC in DSDT
[    0.346098] ACPI: BIOS _OSI(Linux) query ignored
[    0.350218] ACPI: Interpreter enabled
[    0.350223] ACPI: (supports S0 S3 S4 S5)
[    0.350252] ACPI: Using IOAPIC for interrupt routing
[    0.364104] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.364104] ACPI: No dock devices found.
[    0.364104] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.364104] pci 0000:00:02.0: reg 10 64bit mmio: [0xf2400000-0xf27fffff]
[    0.364104] pci 0000:00:02.0: reg 18 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.364104] pci 0000:00:02.0: reg 20 io port: [0x1800-0x1807]
[    0.364104] pci 0000:00:02.1: reg 10 64bit mmio: [0xf2100000-0xf21fffff]
[    0.364104] pci 0000:00:1a.0: reg 20 io port: [0x1820-0x183f]
[    0.364104] pci 0000:00:1a.1: reg 20 io port: [0x1840-0x185f]
[    0.364104] pci 0000:00:1a.2: reg 20 io port: [0x1860-0x187f]
[    0.364104] pci 0000:00:1a.7: reg 10 32bit mmio: [0xf2a04800-0xf2a04bff]
[    0.364104] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.364104] pci 0000:00:1a.7: PME# disabled
[    0.364104] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf2a00000-0xf2a03fff]
[    0.364104] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.364104] pci 0000:00:1b.0: PME# disabled
[    0.364104] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.364104] pci 0000:00:1c.0: PME# disabled
[    0.364104] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.364104] pci 0000:00:1c.1: PME# disabled
[    0.364104] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.364104] pci 0000:00:1c.2: PME# disabled
[    0.364104] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.364104] pci 0000:00:1c.3: PME# disabled
[    0.364104] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.364104] pci 0000:00:1c.4: PME# disabled
[    0.364104] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.364104] pci 0000:00:1c.5: PME# disabled
[    0.364104] pci 0000:00:1d.0: reg 20 io port: [0x1880-0x189f]
[    0.364104] pci 0000:00:1d.1: reg 20 io port: [0x18a0-0x18bf]
[    0.364104] pci 0000:00:1d.2: reg 20 io port: [0x18c0-0x18df]
[    0.364104] pci 0000:00:1d.7: reg 10 32bit mmio: [0xf2a04c00-0xf2a04fff]
[    0.364104] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.364104] pci 0000:00:1d.7: PME# disabled
[    0.364104] pci 0000:00:1f.2: reg 10 io port: [0x1818-0x181f]
[    0.364104] pci 0000:00:1f.2: reg 14 io port: [0x180c-0x180f]
[    0.364104] pci 0000:00:1f.2: reg 18 io port: [0x1810-0x1817]
[    0.364104] pci 0000:00:1f.2: reg 1c io port: [0x1808-0x180b]
[    0.364104] pci 0000:00:1f.2: reg 20 io port: [0x18e0-0x18ff]
[    0.364104] pci 0000:00:1f.2: reg 24 32bit mmio: [0xf2a04000-0xf2a047ff]
[    0.364104] pci 0000:00:1f.2: PME# supported from D3hot
[    0.364104] pci 0000:00:1f.2: PME# disabled
[    0.364104] pci 0000:00:1f.3: reg 10 64bit mmio: [0x000000-0x0000ff]
[    0.364104] pci 0000:00:1f.3: reg 20 io port: [0x1c00-0x1c1f]
[    0.364171] pci 0000:02:00.0: reg 10 32bit mmio: [0xf2300000-0xf23000ff]
[    0.364352] pci 0000:02:00.2: reg 10 32bit mmio: [0xf2300400-0xf23004ff]
[    0.364532] pci 0000:02:00.3: reg 10 32bit mmio: [0xf2300800-0xf23008ff]
[    0.364709] pci 0000:02:00.4: reg 10 32bit mmio: [0xf2300c00-0xf2300cff]
[    0.364904] pci 0000:00:1c.0: bridge 32bit mmio: [0xf2300000-0xf23fffff]
[    0.365161] pci 0000:05:00.0: reg 10 64bit mmio: [0xf2200000-0xf2201fff]
[    0.365284] pci 0000:05:00.0: PME# supported from D0 D3hot D3cold
[    0.365291] pci 0000:05:00.0: PME# disabled
[    0.370032] pci 0000:00:1c.3: bridge 32bit mmio: [0xf2200000-0xf22fffff]
[    0.370109] pci 0000:00:1c.4: bridge io port: [0x2000-0x2fff]
[    0.370114] pci 0000:00:1c.4: bridge 32bit mmio: [0xf4000000-0xf5ffffff]
[    0.370123] pci 0000:00:1c.4: bridge 64bit mmio pref: [0xf0000000-0xf1ffffff]
[    0.370292] pci 0000:08:00.0: reg 10 io port: [0x3000-0x30ff]
[    0.370369] pci 0000:08:00.0: reg 18 64bit mmio pref: [0xf2004000-0xf2004fff]
[    0.370421] pci 0000:08:00.0: reg 20 64bit mmio pref: [0xf2000000-0xf2003fff]
[    0.370449] pci 0000:08:00.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.370608] pci 0000:08:00.0: supports D1 D2
[    0.370610] pci 0000:08:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.370624] pci 0000:08:00.0: PME# disabled
[    0.370789] pci 0000:00:1c.5: bridge io port: [0x3000-0x3fff]
[    0.370801] pci 0000:00:1c.5: bridge 64bit mmio pref: [0xf2000000-0xf20fffff]
[    0.370875] pci 0000:00:1e.0: transparent bridge
[    0.370946] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.371117] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.371257] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.371344] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.371430] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.371514] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.371600] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    0.371685] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    0.392862] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.392994] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.393125] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.393253] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.393382] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.393512] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.393642] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.393770] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.393897] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.393916] vgaarb: loaded
[    0.394027] SCSI subsystem initialized
[    0.394133] libata version 3.00 loaded.
[    0.394203] usbcore: registered new interface driver usbfs
[    0.394215] usbcore: registered new interface driver hub
[    0.394239] usbcore: registered new device driver usb
[    0.394394] ACPI: WMI: Mapper loaded
[    0.394396] PCI: Using ACPI for IRQ routing
[    0.394645] NetLabel: Initializing
[    0.394647] NetLabel:  domain hash size = 128
[    0.394648] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.394662] NetLabel:  unlabeled traffic allowed by default
[    0.394700] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.394706] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.400117] Switching to clocksource tsc
[    0.401811] AppArmor: AppArmor Filesystem Enabled
[    0.401829] pnp: PnP ACPI init
[    0.401847] ACPI: bus type pnp registered
[    0.405221] pnp: PnP ACPI: found 10 devices
[    0.405224] ACPI: ACPI bus type pnp unregistered
[    0.405239] system 00:03: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.405246] system 00:05: ioport range 0x680-0x69f has been reserved
[    0.405249] system 00:05: ioport range 0x480-0x48f has been reserved
[    0.405252] system 00:05: ioport range 0xffff-0xffff has been reserved
[    0.405254] system 00:05: ioport range 0xffff-0xffff has been reserved
[    0.405257] system 00:05: ioport range 0x400-0x47f has been reserved
[    0.405260] system 00:05: ioport range 0x1180-0x11ff has been reserved
[    0.405263] system 00:05: ioport range 0x1600-0x16fe has been reserved
[    0.405265] system 00:05: ioport range 0xfe00-0xfe00 has been reserved
[    0.405268] system 00:05: ioport range 0x700-0x70f has been reserved
[    0.405275] system 00:09: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.405278] system 00:09: iomem range 0xfed10000-0xfed13fff has been reserved
[    0.405281] system 00:09: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.405284] system 00:09: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.405287] system 00:09: iomem range 0xe0000000-0xefffffff has been reserved
[    0.405290] system 00:09: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.405293] system 00:09: iomem range 0xfed40000-0xfed44fff has been reserved
[    0.410118] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.410122] pci 0000:00:1c.0:   IO window: 0x4000-0x4fff
[    0.410129] pci 0000:00:1c.0:   MEM window: 0xf2300000-0xf23fffff
[    0.410135] pci 0000:00:1c.0:   PREFETCH window: 0x000000c0000000-0x000000c01fffff
[    0.410143] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    0.410147] pci 0000:00:1c.1:   IO window: 0x5000-0x5fff
[    0.410153] pci 0000:00:1c.1:   MEM window: 0xc0200000-0xc03fffff
[    0.410159] pci 0000:00:1c.1:   PREFETCH window: 0x000000c0400000-0x000000c05fffff
[    0.410167] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:04
[    0.410171] pci 0000:00:1c.2:   IO window: 0x6000-0x6fff
[    0.410177] pci 0000:00:1c.2:   MEM window: 0xc0600000-0xc07fffff
[    0.410183] pci 0000:00:1c.2:   PREFETCH window: 0x000000c0800000-0x000000c09fffff
[    0.410191] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:05
[    0.410195] pci 0000:00:1c.3:   IO window: 0x7000-0x7fff
[    0.410202] pci 0000:00:1c.3:   MEM window: 0xf2200000-0xf22fffff
[    0.410207] pci 0000:00:1c.3:   PREFETCH window: 0x000000c0a00000-0x000000c0bfffff
[    0.410216] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:06
[    0.410219] pci 0000:00:1c.4:   IO window: 0x2000-0x2fff
[    0.410226] pci 0000:00:1c.4:   MEM window: 0xf4000000-0xf5ffffff
[    0.410231] pci 0000:00:1c.4:   PREFETCH window: 0x000000f0000000-0x000000f1ffffff
[    0.410240] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:08
[    0.410244] pci 0000:00:1c.5:   IO window: 0x3000-0x3fff
[    0.410251] pci 0000:00:1c.5:   MEM window: 0xc0c00000-0xc0ffffff
[    0.410256] pci 0000:00:1c.5:   PREFETCH window: 0x000000f2000000-0x000000f20fffff
[    0.410265] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:09
[    0.410266] pci 0000:00:1e.0:   IO window: disabled
[    0.410273] pci 0000:00:1e.0:   MEM window: disabled
[    0.410277] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.410299]   alloc irq_desc for 17 on node -1
[    0.410301]   alloc kstat_irqs on node -1
[    0.410307] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.410313] pci 0000:00:1c.0: setting latency timer to 64
[    0.410324]   alloc irq_desc for 16 on node -1
[    0.410326]   alloc kstat_irqs on node -1
[    0.410329] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.410334] pci 0000:00:1c.1: setting latency timer to 64
[    0.410344]   alloc irq_desc for 18 on node -1
[    0.410346]   alloc kstat_irqs on node -1
[    0.410349] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.410354] pci 0000:00:1c.2: setting latency timer to 64
[    0.410364]   alloc irq_desc for 19 on node -1
[    0.410366]   alloc kstat_irqs on node -1
[    0.410369] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.410374] pci 0000:00:1c.3: setting latency timer to 64
[    0.410386] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.410391] pci 0000:00:1c.4: setting latency timer to 64
[    0.410402] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.410407] pci 0000:00:1c.5: setting latency timer to 64
[    0.410416] pci 0000:00:1e.0: setting latency timer to 64
[    0.410420] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.410423] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.410425] pci_bus 0000:02: resource 0 io:  [0x4000-0x4fff]
[    0.410428] pci_bus 0000:02: resource 1 mem: [0xf2300000-0xf23fffff]
[    0.410430] pci_bus 0000:02: resource 2 pref mem [0xc0000000-0xc01fffff]
[    0.410432] pci_bus 0000:03: resource 0 io:  [0x5000-0x5fff]
[    0.410435] pci_bus 0000:03: resource 1 mem: [0xc0200000-0xc03fffff]
[    0.410437] pci_bus 0000:03: resource 2 pref mem [0xc0400000-0xc05fffff]
[    0.410439] pci_bus 0000:04: resource 0 io:  [0x6000-0x6fff]
[    0.410441] pci_bus 0000:04: resource 1 mem: [0xc0600000-0xc07fffff]
[    0.410444] pci_bus 0000:04: resource 2 pref mem [0xc0800000-0xc09fffff]
[    0.410446] pci_bus 0000:05: resource 0 io:  [0x7000-0x7fff]
[    0.410448] pci_bus 0000:05: resource 1 mem: [0xf2200000-0xf22fffff]
[    0.410450] pci_bus 0000:05: resource 2 pref mem [0xc0a00000-0xc0bfffff]
[    0.410453] pci_bus 0000:06: resource 0 io:  [0x2000-0x2fff]
[    0.410455] pci_bus 0000:06: resource 1 mem: [0xf4000000-0xf5ffffff]
[    0.410457] pci_bus 0000:06: resource 2 pref mem [0xf0000000-0xf1ffffff]
[    0.410460] pci_bus 0000:08: resource 0 io:  [0x3000-0x3fff]
[    0.410462] pci_bus 0000:08: resource 1 mem: [0xc0c00000-0xc0ffffff]
[    0.410464] pci_bus 0000:08: resource 2 pref mem [0xf2000000-0xf20fffff]
[    0.410467] pci_bus 0000:09: resource 3 io:  [0x00-0xffff]
[    0.410469] pci_bus 0000:09: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.410506] NET: Registered protocol family 2
[    0.410682] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.412012] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.417385] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.418089] TCP: Hash tables configured (established 524288 bind 65536)
[    0.418092] TCP reno registered
[    0.418207] NET: Registered protocol family 1
[    0.418229] pci 0000:00:02.0: Boot video device
[    0.418457] Simple Boot Flag at 0x36 set to 0x1
[    0.418650] Scanning for low memory corruption every 60 seconds
[    0.418799] audit: initializing netlink socket (disabled)
[    0.418811] type=2000 audit(1274566248.409:1): initialized
[    0.428184] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.429581] VFS: Disk quotas dquot_6.5.2
[    0.429636] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.430206] fuse init (API version 7.13)
[    0.430285] msgmni has been set to 5752
[    0.430494] alg: No test for stdrng (krng)
[    0.430553] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.430556] io scheduler noop registered
[    0.430558] io scheduler anticipatory registered
[    0.430560] io scheduler deadline registered
[    0.430594] io scheduler cfq registered (default)
[    0.430781]   alloc irq_desc for 24 on node -1
[    0.430783]   alloc kstat_irqs on node -1
[    0.430797] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.430811] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.430976]   alloc irq_desc for 25 on node -1
[    0.430977]   alloc kstat_irqs on node -1
[    0.430987] pcieport 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.430998] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.431165]   alloc irq_desc for 26 on node -1
[    0.431167]   alloc kstat_irqs on node -1
[    0.431176] pcieport 0000:00:1c.2: irq 26 for MSI/MSI-X
[    0.431188] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.431350]   alloc irq_desc for 27 on node -1
[    0.431352]   alloc kstat_irqs on node -1
[    0.431361] pcieport 0000:00:1c.3: irq 27 for MSI/MSI-X
[    0.431373] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.431539]   alloc irq_desc for 28 on node -1
[    0.431541]   alloc kstat_irqs on node -1
[    0.431550] pcieport 0000:00:1c.4: irq 28 for MSI/MSI-X
[    0.431562] pcieport 0000:00:1c.4: setting latency timer to 64
[    0.431732]   alloc irq_desc for 29 on node -1
[    0.431733]   alloc kstat_irqs on node -1
[    0.431742] pcieport 0000:00:1c.5: irq 29 for MSI/MSI-X
[    0.431754] pcieport 0000:00:1c.5: setting latency timer to 64
[    0.431858] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.432137] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.508240] Freeing initrd memory: 8134k freed
[    0.530022] ACPI: AC Adapter [ACAD] (on-line)
[    0.530144] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.530594] ACPI: Lid Switch [LID]
[    0.530636] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.530639] ACPI: Power Button [PWRB]
[    0.530681] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.530687] ACPI: Sleep Button [SLPB]
[    0.530725] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.530727] ACPI: Power Button [PWRF]
[    0.531767] ACPI: SSDT 00000000b7b1ac20 00265 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.532348] ACPI: SSDT 00000000b7b18620 00549 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.534854] Monitor-Mwait will be used to enter C-1 state
[    0.534892] Monitor-Mwait will be used to enter C-2 state
[    0.534899] Marking TSC unstable due to TSC halts in idle
[    0.534943] Switching to clocksource hpet
[    0.535018] processor LNXCPU:00: registered as cooling_device0
[    0.535515] ACPI: SSDT 00000000b7b19ca0 001CF (v01  PmRef    ApIst 00003000 INTL 20050624)
[    0.536005] ACPI: SSDT 00000000b7b19f20 0008D (v01  PmRef    ApCst 00003000 INTL 20050624)
[    0.537251] processor LNXCPU:01: registered as cooling_device1
[    0.543162] thermal LNXTHERM:01: registered as thermal_zone0
[    0.543170] ACPI: Thermal Zone [TZ00] (43 C)
[    0.544705] Linux agpgart interface v0.103
[    0.544739] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.545972] brd: module loaded
[    0.546488] loop: module loaded
[    0.546615] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.547074] Fixed MDIO Bus: probed
[    0.547107] PPP generic driver version 2.4.2
[    0.547136] tun: Universal TUN/TAP device driver, 1.6
[    0.547138] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.547214] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.547237] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    0.547254] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.547258] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.547326] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.547372] ehci_hcd 0000:00:1a.7: debug port 1
[    0.551275] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.551291] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xf2a04800
[    0.580017] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.580090] usb usb1: configuration #1 chosen from 1 choice
[    0.580119] hub 1-0:1.0: USB hub found
[    0.580126] hub 1-0:1.0: 6 ports detected
[    0.580185]   alloc irq_desc for 23 on node -1
[    0.580188]   alloc kstat_irqs on node -1
[    0.580194] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.580204] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.580208] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.580236] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.580265] ehci_hcd 0000:00:1d.7: debug port 1
[    0.584137] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.584149] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf2a04c00
[    0.610014] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.610086] usb usb2: configuration #1 chosen from 1 choice
[    0.610113] hub 2-0:1.0: USB hub found
[    0.610118] hub 2-0:1.0: 6 ports detected
[    0.610172] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.610185] uhci_hcd: USB Universal Host Controller Interface driver
[    0.610205] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.610212] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.610216] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.610249] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.610283] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001820
[    0.610364] usb usb3: configuration #1 chosen from 1 choice
[    0.610394] hub 3-0:1.0: USB hub found
[    0.610400] hub 3-0:1.0: 2 ports detected
[    0.610444]   alloc irq_desc for 21 on node -1
[    0.610445]   alloc kstat_irqs on node -1
[    0.610450] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.610456] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.610460] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.610491] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.610527] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001840
[    0.610613] usb usb4: configuration #1 chosen from 1 choice
[    0.610638] hub 4-0:1.0: USB hub found
[    0.610644] hub 4-0:1.0: 2 ports detected
[    0.610686] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    0.610693] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.610696] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.610723] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.610750] uhci_hcd 0000:00:1a.2: irq 19, io base 0x00001860
[    0.610831] usb usb5: configuration #1 chosen from 1 choice
[    0.610853] hub 5-0:1.0: USB hub found
[    0.610859] hub 5-0:1.0: 2 ports detected
[    0.610904] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.610911] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.610914] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.610950] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.610976] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001880
[    0.611057] usb usb6: configuration #1 chosen from 1 choice
[    0.611080] hub 6-0:1.0: USB hub found
[    0.611085] hub 6-0:1.0: 2 ports detected
[    0.611136] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.611143] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.611146] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.611175] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.611201] uhci_hcd 0000:00:1d.1: irq 19, io base 0x000018a0
[    0.611282] usb usb7: configuration #1 chosen from 1 choice
[    0.611305] hub 7-0:1.0: USB hub found
[    0.611311] hub 7-0:1.0: 2 ports detected
[    0.611355] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.611362] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.611365] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.611399] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.611432] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018c0
[    0.611511] usb usb8: configuration #1 chosen from 1 choice
[    0.611536] hub 8-0:1.0: USB hub found
[    0.611542] hub 8-0:1.0: 2 ports detected
[    0.611629] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.615756] i8042.c: Detected active multiplexing controller, rev 1.1.
[    0.617115] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.617121] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.617147] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.617167] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.617189] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.617291] mice: PS/2 mouse device common for all mice
[    0.617437] rtc_cmos 00:06: RTC can wake from S4
[    0.617472] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.617503] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.617615] device-mapper: uevent: version 1.0.3
[    0.617735] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.617810] device-mapper: multipath: version 1.1.0 loaded
[    0.617813] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.618024] cpuidle: using governor ladder
[    0.618104] cpuidle: using governor menu
[    0.618417] TCP cubic registered
[    0.618537] NET: Registered protocol family 10
[    0.618948] lo: Disabled Privacy Extensions
[    0.619214] NET: Registered protocol family 17
[    0.620069] PM: Resume from disk failed.
[    0.620080] registered taskstats version 1
[    0.620903]   Magic number: 10:597:199
[    0.621015] rtc_cmos 00:06: setting system clock to 2010-05-22 22:10:49 UTC (1274566249)
[    0.621018] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.621019] EDD information not available.
[    0.621135] Freeing unused kernel memory: 876k freed
[    0.621437] Write protecting the kernel read-only data: 7680k
[    0.636812] udev: starting version 151
[    0.673043] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    0.733766] ahci 0000:00:1f.2: version 3.0
[    0.733791] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.733843]   alloc irq_desc for 30 on node -1
[    0.733845]   alloc kstat_irqs on node -1
[    0.733857] ahci 0000:00:1f.2: irq 30 for MSI/MSI-X
[    0.733909] ahci: SSS flag set, parallel bus scan disabled
[    0.733952] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    0.733956] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ccc ems sxs 
[    0.733962] ahci 0000:00:1f.2: setting latency timer to 64
[    0.736651] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.736697] r8169 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.736823] r8169 0000:08:00.0: setting latency timer to 64
[    0.736989]   alloc irq_desc for 31 on node -1
[    0.736991]   alloc kstat_irqs on node -1
[    0.737042] r8169 0000:08:00.0: irq 31 for MSI/MSI-X
[    0.737622] eth0: RTL8168d/8111d at 0xffffc9000067c000, c8:0a:a9:3d:0d:79, XID 081000c0 IRQ 31
[    0.800349] scsi0 : ahci
[    0.800475] scsi1 : ahci
[    0.800534] scsi2 : ahci
[    0.800588] scsi3 : ahci
[    0.800659] scsi4 : ahci
[    0.800714] scsi5 : ahci
[    0.801002] ata1: SATA max UDMA/133 abar m2048@0xf2a04000 port 0xf2a04100 irq 30
[    0.801006] ata2: SATA max UDMA/133 abar m2048@0xf2a04000 port 0xf2a04180 irq 30
[    0.801008] ata3: DUMMY
[    0.801009] ata4: DUMMY
[    0.801012] ata5: SATA max UDMA/133 abar m2048@0xf2a04000 port 0xf2a04300 irq 30
[    0.801016] ata6: SATA max UDMA/133 abar m2048@0xf2a04000 port 0xf2a04380 irq 30
[    0.930057] usb 2-6: new high speed USB device using ehci_hcd and address 2
[    1.085990] usb 2-6: configuration #1 chosen from 1 choice
[    1.140066] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.141174] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.141178] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.180497] ata1.00: ATA-8: ST9320423AS, 0003LVM1, max UDMA/100
[    1.180502] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.182402] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.182405] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.182740] ata1.00: configured for UDMA/100
[    1.200201] scsi 0:0:0:0: Direct-Access     ATA      ST9320423AS      0003 PQ: 0 ANSI: 5
[    1.200390] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.200425] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.200477] sd 0:0:0:0: [sda] Write Protect is off
[    1.200480] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.200502] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.200691]  sda: sda1 sda2 < sda5 >
[    1.229256] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.314499] ACPI: Battery Slot [BAT1] (battery present)
[    1.950132] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.952045] ACPI Warning for \_SB_.PCI0.SAT0.PRT1._GTF: Return type mismatch - found Integer, expected Buffer (20090903/nspredef-1006)
[    1.952052] ata2.00: _GTF unexpected object type 0x1
[    1.952656] ata2.00: ATAPI: MATSHITADVD-RAM UJ890, SB31, max UDMA/100, ATAPI AN
[    1.954940] ata2.00: _GTF unexpected object type 0x1
[    1.955564] ata2.00: configured for UDMA/100
[    1.972799] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ890    SB31 PQ: 0 ANSI: 5
[    1.978406] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.978410] Uniform CD-ROM driver Revision: 3.20
[    1.978546] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.978627] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.320113] ata5: SATA link down (SStatus 0 SControl 300)
[    2.690115] ata6: SATA link down (SStatus 0 SControl 300)
[    3.079564] EXT4-fs (sda1): mounted filesystem with ordered data mode
[   11.700447] udev: starting version 151
[   11.733002] Adding 8653816k swap on /dev/sda5.  Priority:-1 extents:1 across:8653816k 
[   11.738192] lp: driver loaded but no devices found
[   11.803552] Non-volatile memory driver v1.3
[   11.879003] agpgart-intel 0000:00:00.0: Intel Mobile Intel® GM45 Express Chipset
[   11.879715] agpgart-intel 0000:00:00.0: detected 131068K stolen memory
[   12.009165] cfg80211: Calling CRDA to update world regulatory domain
[   12.014794] sdhci: Secure Digital Host Controller Interface driver
[   12.014797] sdhci: Copyright(c) Pierre Ossman
[   12.016010] sdhci-pci 0000:02:00.0: SDHCI controller found [197b:2382] (rev 0)
[   12.016036] sdhci-pci 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.016087] sdhci-pci 0000:02:00.0: setting latency timer to 64
[   12.016129] Registered led device: mmc0::
[   12.016168] mmc0: SDHCI controller on PCI [0000:02:00.0] using DMA
[   12.016182] sdhci-pci 0000:02:00.2: SDHCI controller found [197b:2381] (rev 0)
[   12.016201] sdhci-pci 0000:02:00.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.016208] sdhci-pci 0000:02:00.2: Refusing to bind to secondary interface.
[   12.016215] sdhci-pci 0000:02:00.2: PCI INT A disabled
[   12.037007] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[   12.038213] type=1505 audit(1274580660.909:2):  operation="profile_load" pid=689 name="/sbin/dhclient3"
[   12.038849] type=1505 audit(1274580660.909:3):  operation="profile_load" pid=689 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   12.039191] type=1505 audit(1274580660.909:4):  operation="profile_load" pid=689 name="/usr/lib/connman/scripts/dhclient-script"
[   12.051891] [drm] Initialized drm 1.1.0 20060810
[   12.060549] Linux video capture interface: v2.00
[   12.063395] uvcvideo: Found UVC 1.00 device Integrated Camera (17ef:4811)
[   12.067108] input: Integrated Camera as /devices/pci0000:00/0000:00:1d.7/usb2/2-6/2-6:1.0/input/input6
[   12.067233] usbcore: registered new interface driver uvcvideo
[   12.067732] USB Video Class driver (v0.1.0)
[   12.083922] jmb38x_ms 0000:02:00.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.083930] jmb38x_ms 0000:02:00.3: setting latency timer to 64
[   12.104162] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.104169] i915 0000:00:02.0: setting latency timer to 64
[   12.122289]   alloc irq_desc for 32 on node -1
[   12.122292]   alloc kstat_irqs on node -1
[   12.122308] i915 0000:00:02.0: irq 32 for MSI/MSI-X
[   12.122309] [drm] set up 127M of stolen space
[   12.135450] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   12.135453] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   12.135529] iwlagn 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   12.135539] iwlagn 0000:05:00.0: setting latency timer to 64
[   12.135576] iwlagn 0000:05:00.0: Detected Intel Wireless WiFi Link 1000 Series BGN REV=0x6C
[   12.138540] cfg80211: World regulatory domain updated:
[   12.138543] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   12.138546] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.138548] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.138551] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.138553] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.138555] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.171537] iwlagn 0000:05:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   12.171603]   alloc irq_desc for 33 on node -1
[   12.171606]   alloc kstat_irqs on node -1
[   12.171626] iwlagn 0000:05:00.0: irq 33 for MSI/MSI-X
[   12.273796] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   12.285208] thinkpad_acpi: Not yet supported ThinkPad detected!
[   12.387325] type=1505 audit(1274580661.259:5):  operation="profile_load" pid=837 name="/usr/share/gdm/guest-session/Xsession"
[   12.388855] type=1505 audit(1274580661.259:6):  operation="profile_replace" pid=838 name="/sbin/dhclient3"
[   12.389499] type=1505 audit(1274580661.259:7):  operation="profile_replace" pid=838 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   12.389846] type=1505 audit(1274580661.259:8):  operation="profile_replace" pid=838 name="/usr/lib/connman/scripts/dhclient-script"
[   12.392763] type=1505 audit(1274580661.269:9):  operation="profile_load" pid=839 name="/usr/bin/evince"
[   12.400898] type=1505 audit(1274580661.279:10):  operation="profile_load" pid=839 name="/usr/bin/evince-previewer"
[   12.406140] type=1505 audit(1274580661.279:11):  operation="profile_load" pid=839 name="/usr/bin/evince-thumbnailer"
[   12.641749] iwlagn 0000:05:00.0: firmware: requesting iwlwifi-1000-3.ucode
[   12.695025] iwlagn 0000:05:00.0: loaded firmware version 128.50.3.1
[   12.798872] Registered led device: iwl-phy0::radio
[   12.799269] Registered led device: iwl-phy0::assoc
[   12.799657] Registered led device: iwl-phy0::RX
[   12.800043] Registered led device: iwl-phy0::TX
[   12.816810] fb0: inteldrmfb frame buffer device
[   12.816812] registered panic notifier
[   12.822644] acpi device:06: registered as cooling_device2
[   12.822950] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input7
[   12.823031] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   12.823083] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   12.823132]   alloc irq_desc for 22 on node -1
[   12.823134]   alloc kstat_irqs on node -1
[   12.823140] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   12.823176] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   12.825606] vga16fb: initializing
[   12.825610] vga16fb: mapped to 0xffff8800000a0000
[   12.825614] vga16fb: not registering due to another framebuffer present
[   12.844810] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   12.846159] r8169: eth0: link down
[   12.846653] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.925413] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd047b1/0xb40000
[   12.925417] serio: Synaptics pass-through port at isa0060/serio4/input0
[   12.972246] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
[   13.023553] hda_codec: ALC269: BIOS auto-probing.
[   13.024032] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input9
[   13.215603] Console: switching to colour frame buffer device 170x48
[   20.062952] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   20.369819] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio4/serio5/input/input10
[   26.542179] wlan0: deauthenticating from 00:21:29:8e:5b:5e by local choice (reason=3)
[   26.542357] wlan0: direct probe to AP 00:21:29:8e:5b:5e (try 1)
[   26.545540] wlan0: direct probe responded
[   26.545547] wlan0: authenticate with AP 00:21:29:8e:5b:5e (try 1)
[   26.547442] wlan0: authenticated
[   26.547470] wlan0: associate with AP 00:21:29:8e:5b:5e (try 1)
[   26.549682] wlan0: RX AssocResp from 00:21:29:8e:5b:5e (capab=0x401 status=0 aid=4)
[   26.549687] wlan0: associated
[   26.553467] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   37.352537] wlan0: no IPv6 routers present
```

---

