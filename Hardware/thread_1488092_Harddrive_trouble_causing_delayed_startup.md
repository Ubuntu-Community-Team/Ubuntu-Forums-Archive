---
title: "Harddrive trouble causing delayed startup"
date: 2010-05-19
forum: Hardware
---

### Post by nixpix on 2010-05-19
I've recently converted back to Ubuntu after crashing my BackTrack 4. It has however not solved the problem causing BackTrack to crash, and the problem is also affecting Ubuntu, both when run from a live USB and when running from a complete installation on a USB.

Basically, the problem consists in a delayed startup. The messages printed during a non-quiet boot looks like this according to the gmesg log. I have highlighted the line where the errors seem to start.

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-22-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 (Ubuntu 2.6.32-22.33-generic 2.6.32.11+drm33.2)
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
[    0.000000]  BIOS-e820: 00000000000e2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f7a0000 (usable)
[    0.000000]  BIOS-e820: 000000003f7a0000 - 000000003f7ae000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003f7ae000 - 000000003f7f0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f7f0000 - 000000003f800000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x3f7a0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask 0C0000000 write-back
[    0.000000]   1 base 03F800000 mask 0FF800000 uncachable
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
[    0.000000]  modified: 00000000000e2000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003f7a0000 (usable)
[    0.000000]  modified: 000000003f7a0000 - 000000003f7ae000 (ACPI data)
[    0.000000]  modified: 000000003f7ae000 - 000000003f7f0000 (ACPI NVS)
[    0.000000]  modified: 000000003f7f0000 - 000000003f800000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
[    0.000000] RAMDISK: 2ed6a000 - 2f9f742e
[    0.000000] ACPI: RSDP 000fb9d0 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 3f7a0000 0003C (v01 A_M_I_ OEMRSDT  03000905 MSFT 00000097)
[    0.000000] ACPI: FACP 3f7a0200 00084 (v02 A_M_I_ OEMFACP  03000905 MSFT 00000097)
[    0.000000] ACPI: DSDT 3f7a05b0 05E21 (v01  A1192 A1192000 00000000 INTL 20060113)
[    0.000000] ACPI: FACS 3f7ae000 00040
[    0.000000] ACPI: APIC 3f7a0390 0005C (v01 A_M_I_ OEMAPIC  03000905 MSFT 00000097)
[    0.000000] ACPI: MCFG 3f7a03f0 0003C (v01 A_M_I_ OEMMCFG  03000905 MSFT 00000097)
[    0.000000] ACPI: OEMB 3f7ae040 00061 (v01 A_M_I_ AMI_OEM  03000905 MSFT 00000097)
[    0.000000] ACPI: HPET 3f7a63e0 00038 (v01 A_M_I_ OEMHPET  03000905 MSFT 00000097)
[    0.000000] ACPI: SSDT 3f7aeb40 004F0 (v01  PmRef    CpuPm 00003000 INTL 20060113)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00011000 - 00017f00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008d9e98]    TEXT DATA BSS ==> [0000100000 - 00008d9e98]
[    0.000000]   #4 [002ed6a000 - 002f9f742e]          RAMDISK ==> [002ed6a000 - 002f9f742e]
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #6 [00008da000 - 00008dd1f8]              BRK ==> [00008da000 - 00008dd1f8]
[    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003f7a0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003f7a0
[    0.000000] On node 0 totalpages: 259887
[    0.000000] free_area_init_node: node 0, pgdat c0798720, node_mem_map c1001200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 256 pages used for memmap
[    0.000000]   HighMem zone: 32418 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e2000
[    0.000000] PM: Registered nosave memory: 00000000000e2000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 3f800000 (gap: 3f800000:bf600000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1800000 s36024 r0 d21320 u2097152
[    0.000000] pcpu-alloc: s36024 r0 d21320 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257855
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=837c0cc7-0c25-45e4-99c6-8a8c464d6f9d ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 5199680 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0003f7a0)
[    0.000000] Memory: 1003928k/1040000k available (4673k kernel code, 35068k reserved, 2121k data, 656k init, 130696k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a3000 - 0xc0847000   ( 656 kB)
[    0.000000]       .data : 0xc0590653 - 0xc07a2e48   (2121 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0590653   (4673 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1662.615 MHz processor.
[    0.004010] Calibrating delay loop (skipped), value calculated using timer frequency.. 3325.23 BogoMIPS (lpj=6650460)
[    0.004046] Security Framework initialized
[    0.004086] AppArmor: AppArmor initialized
[    0.004102] Mount-cache hash table entries: 512
[    0.004331] Initializing cgroup subsys ns
[    0.004341] Initializing cgroup subsys cpuacct
[    0.004351] Initializing cgroup subsys memory
[    0.004364] Initializing cgroup subsys devices
[    0.004370] Initializing cgroup subsys freezer
[    0.004376] Initializing cgroup subsys net_cls
[    0.004413] CPU: L1 I cache: 32K, L1 D cache: 24K
[    0.004420] CPU: L2 cache: 512K
[    0.004425] CPU: Physical Processor ID: 0
[    0.004430] CPU: Processor Core ID: 0
[    0.004437] mce: CPU supports 5 MCE banks
[    0.004453] CPU0: Thermal monitoring enabled (TM2)
[    0.004463] using mwait in idle threads.
[    0.004474] Performance Events: Atom events, Intel PMU driver.
[    0.004490] ... version:                3
[    0.004494] ... bit width:              40
[    0.004499] ... generic registers:      2
[    0.004503] ... value mask:             000000ffffffffff
[    0.004508] ... max period:             000000007fffffff
[    0.004513] ... fixed-purpose events:   3
[    0.004518] ... event mask:             0000000700000003
[    0.004526] Checking 'hlt' instruction... OK.
[    0.020009] Disabling 4MB page tables to avoid TLB bug
[    0.024237] ACPI: Core revision 20090903
[    0.040017] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.040028] ftrace: allocating 21771 entries in 43 pages
[    0.044106] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.044505] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.084322] CPU0: Intel(R) Atom(TM) CPU N280   @ 1.66GHz stepping 02
[    0.088001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.008000] Initializing CPU#1
[    0.008000] CPU: L1 I cache: 32K, L1 D cache: 24K
[    0.008000] CPU: L2 cache: 512K
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 0
[    0.008000] CPU1: Thermal monitoring enabled (TM2)
[    0.172151] CPU1: Intel(R) Atom(TM) CPU N280   @ 1.66GHz stepping 02
[    0.172178] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.176036] Brought up 2 CPUs
[    0.176043] Total of 2 processors activated (6650.20 BogoMIPS).
[    0.176283] CPU0 attaching sched-domain:
[    0.176292]  domain 0: span 0-1 level SIBLING
[    0.176298]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[    0.176310]   domain 1: span 0-1 level MC
[    0.176315]    groups: 0-1 (cpu_power = 1178)
[    0.176327] CPU1 attaching sched-domain:
[    0.176331]  domain 0: span 0-1 level SIBLING
[    0.176336]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[    0.176348]   domain 1: span 0-1 level MC
[    0.176352]    groups: 0-1 (cpu_power = 1178)
[    0.176576] devtmpfs: initialized
[    0.176576] regulator: core version 0.5
[    0.176576] Time: 20:44:18  Date: 05/19/10
[    0.176576] NET: Registered protocol family 16
[    0.176576] Trying to unpack rootfs image as initramfs...
[    0.176576] EISA bus registered
[    0.176576] ACPI: bus type pci registered
[    0.176742] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 63
[    0.176750] PCI: Not using MMCONFIG.
[    0.177070] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
[    0.177077] PCI: Using configuration type 1 for base access
[    0.181997] bio: create slab <bio-0> at 0
[    0.184588] ACPI: EC: Look up EC in DSDT
[    0.187485] ACPI: Executed 1 blocks of module-level executable AML code
[    0.201026] ACPI: Interpreter enabled
[    0.201050] ACPI: (supports S0 S3 S4 S5)
[    0.201119] ACPI: Using IOAPIC for interrupt routing
[    0.201248] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 63
[    0.206195] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.206206] PCI: Using MMCONFIG for extended config space
[    0.222373] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    0.222899] ACPI: No dock devices found.
[    0.223266] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.223450] pci 0000:00:02.0: reg 10 32bit mmio: [0xf7f00000-0xf7f7ffff]
[    0.223464] pci 0000:00:02.0: reg 14 io port: [0xdc00-0xdc07]
[    0.223477] pci 0000:00:02.0: reg 18 32bit mmio pref: [0xd0000000-0xdfffffff]
[    0.223491] pci 0000:00:02.0: reg 1c 32bit mmio: [0xf7ec0000-0xf7efffff]
[    0.223559] pci 0000:00:02.1: reg 10 32bit mmio: [0xf7f80000-0xf7ffffff]
[    0.223721] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf7eb8000-0xf7ebbfff]
[    0.223805] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.223816] pci 0000:00:1b.0: PME# disabled
[    0.223942] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.223953] pci 0000:00:1c.0: PME# disabled
[    0.224118] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.224129] pci 0000:00:1c.1: PME# disabled
[    0.224263] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.224275] pci 0000:00:1c.3: PME# disabled
[    0.224377] pci 0000:00:1d.0: reg 20 io port: [0xd400-0xd41f]
[    0.224471] pci 0000:00:1d.1: reg 20 io port: [0xd480-0xd49f]
[    0.224564] pci 0000:00:1d.2: reg 20 io port: [0xd800-0xd81f]
[    0.224657] pci 0000:00:1d.3: reg 20 io port: [0xd880-0xd89f]
[    0.224756] pci 0000:00:1d.7: reg 10 32bit mmio: [0xf7eb7c00-0xf7eb7fff]
[    0.224842] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.224852] pci 0000:00:1d.7: PME# disabled
[    0.225080] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    0.225091] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.225102] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0380 (mask 0003)
[    0.225113] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0290 (mask 0007)
[    0.225123] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0068 (mask 0003)
[    0.225215] pci 0000:00:1f.2: reg 10 io port: [0x00-0x07]
[    0.225230] pci 0000:00:1f.2: reg 14 io port: [0x00-0x03]
[    0.225245] pci 0000:00:1f.2: reg 18 io port: [0x00-0x07]
[    0.225259] pci 0000:00:1f.2: reg 1c io port: [0x00-0x03]
[    0.225274] pci 0000:00:1f.2: reg 20 io port: [0xffa0-0xffaf]
[    0.225324] pci 0000:00:1f.2: PME# supported from D3hot
[    0.225334] pci 0000:00:1f.2: PME# disabled
[    0.225533] pci 0000:03:00.0: reg 10 64bit mmio: [0xfbfc0000-0xfbffffff]
[    0.225551] pci 0000:03:00.0: reg 18 io port: [0xec00-0xec7f]
[    0.225652] pci 0000:03:00.0: PME# supported from D3hot D3cold
[    0.225663] pci 0000:03:00.0: PME# disabled
[    0.225763] pci 0000:00:1c.1: bridge io port: [0xe000-0xefff]
[    0.225774] pci 0000:00:1c.1: bridge 32bit mmio: [0xfbf00000-0xfbffffff]
[    0.225877] pci 0000:01:00.0: reg 10 64bit mmio: [0xfbef0000-0xfbefffff]
[    0.225990] pci 0000:01:00.0: supports D1
[    0.225997] pci 0000:01:00.0: PME# supported from D0 D1 D3hot
[    0.226009] pci 0000:01:00.0: PME# disabled
[    0.226118] pci 0000:00:1c.3: bridge 32bit mmio: [0xf8000000-0xfbefffff]
[    0.226133] pci 0000:00:1c.3: bridge 64bit mmio pref: [0xf0000000-0xf6ffffff]
[    0.226216] pci 0000:00:1e.0: transparent bridge
[    0.226268] pci_bus 0000:00: on NUMA node 0
[    0.226289] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.227330] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[    0.227462] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[    0.258965] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.259294] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.259608] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.259922] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.260291] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.260611] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.260931] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.261257] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.261589] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.261619] vgaarb: loaded
[    0.261981] SCSI subsystem initialized
[    0.262224] libata version 3.00 loaded.
[    0.262458] usbcore: registered new interface driver usbfs
[    0.262500] usbcore: registered new interface driver hub
[    0.262579] usbcore: registered new device driver usb
[    0.263021] ACPI: WMI: Mapper loaded
[    0.263028] PCI: Using ACPI for IRQ routing
[    0.263466] NetLabel: Initializing
[    0.263473] NetLabel:  domain hash size = 128
[    0.263478] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.263511] NetLabel:  unlabeled traffic allowed by default
[    0.263632] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.263648] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.268552] Switching to clocksource tsc
[    0.272740] AppArmor: AppArmor Filesystem Enabled
[    0.272782] pnp: PnP ACPI init
[    0.272822] ACPI: bus type pnp registered
[    0.278035] pnp: PnP ACPI: found 13 devices
[    0.278046] ACPI: ACPI bus type pnp unregistered
[    0.278056] PnPBIOS: Disabled by ACPI PNP
[    0.278095] system 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
[    0.278124] system 00:08: ioport range 0x25c-0x25f has been reserved
[    0.278133] system 00:08: ioport range 0x380-0x383 has been reserved
[    0.278143] system 00:08: ioport range 0x400-0x41f has been reserved
[    0.278152] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.278161] system 00:08: ioport range 0x800-0x87f has been reserved
[    0.278171] system 00:08: ioport range 0x480-0x4bf has been reserved
[    0.278181] system 00:08: iomem range 0x8c000000-0x8c01ffff has been reserved
[    0.278191] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.278201] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.278211] system 00:08: iomem range 0xfed50000-0xfed8ffff has been reserved
[    0.278221] system 00:08: iomem range 0xffb00000-0xffbfffff has been reserved
[    0.278231] system 00:08: iomem range 0xfff00000-0xffffffff could not be reserved
[    0.278252] system 00:0a: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.278262] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.278282] system 00:0b: iomem range 0xe0000000-0xe3ffffff has been reserved
[    0.278302] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    0.278313] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
[    0.278323] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[    0.278335] system 00:0c: iomem range 0x100000-0x3f7fffff could not be reserved
[    0.313552] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:04
[    0.313564] pci 0000:00:1c.0:   IO window: 0x1000-0x1fff
[    0.313577] pci 0000:00:1c.0:   MEM window: 0x40000000-0x401fffff
[    0.313589] pci 0000:00:1c.0:   PREFETCH window: 0x00000040200000-0x000000403fffff
[    0.313605] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    0.313614] pci 0000:00:1c.1:   IO window: 0xe000-0xefff
[    0.313626] pci 0000:00:1c.1:   MEM window: 0xfbf00000-0xfbffffff
[    0.313638] pci 0000:00:1c.1:   PREFETCH window: 0x00000040400000-0x000000405fffff
[    0.313653] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:01
[    0.313662] pci 0000:00:1c.3:   IO window: 0x2000-0x2fff
[    0.313675] pci 0000:00:1c.3:   MEM window: 0xf8000000-0xfbefffff
[    0.313686] pci 0000:00:1c.3:   PREFETCH window: 0x000000f0000000-0x000000f6ffffff
[    0.313701] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    0.313708] pci 0000:00:1e.0:   IO window: disabled
[    0.313719] pci 0000:00:1e.0:   MEM window: disabled
[    0.313728] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.313757] pci 0000:00:1c.0: enabling device (0104 -> 0107)
[    0.313774]   alloc irq_desc for 16 on node -1
[    0.313781]   alloc kstat_irqs on node -1
[    0.313798] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.313811] pci 0000:00:1c.0: setting latency timer to 64
[    0.313846]   alloc irq_desc for 17 on node -1
[    0.313852]   alloc kstat_irqs on node -1
[    0.313863] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.313875] pci 0000:00:1c.1: setting latency timer to 64
[    0.313893] pci 0000:00:1c.3: enabling device (0106 -> 0107)
[    0.313903]   alloc irq_desc for 19 on node -1
[    0.313909]   alloc kstat_irqs on node -1
[    0.313920] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.313931] pci 0000:00:1c.3: setting latency timer to 64
[    0.313947] pci 0000:00:1e.0: setting latency timer to 64
[    0.313958] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.313967] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.313976] pci_bus 0000:04: resource 0 io:  [0x1000-0x1fff]
[    0.313984] pci_bus 0000:04: resource 1 mem: [0x40000000-0x401fffff]
[    0.313993] pci_bus 0000:04: resource 2 pref mem [0x40200000-0x403fffff]
[    0.314001] pci_bus 0000:03: resource 0 io:  [0xe000-0xefff]
[    0.314010] pci_bus 0000:03: resource 1 mem: [0xfbf00000-0xfbffffff]
[    0.314018] pci_bus 0000:03: resource 2 pref mem [0x40400000-0x405fffff]
[    0.314027] pci_bus 0000:01: resource 0 io:  [0x2000-0x2fff]
[    0.314035] pci_bus 0000:01: resource 1 mem: [0xf8000000-0xfbefffff]
[    0.314043] pci_bus 0000:01: resource 2 pref mem [0xf0000000-0xf6ffffff]
[    0.314052] pci_bus 0000:05: resource 3 io:  [0x00-0xffff]
[    0.314060] pci_bus 0000:05: resource 4 mem: [0x000000-0xffffffff]
[    0.314153] NET: Registered protocol family 2
[    0.314466] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.315376] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.316528] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.317068] TCP: Hash tables configured (established 131072 bind 65536)
[    0.317077] TCP reno registered
[    0.317378] NET: Registered protocol family 1
[    0.317433] pci 0000:00:02.0: Boot video device
[    0.318158] cpufreq-nforce2: No nForce2 chipset.
[    0.318253] Scanning for low memory corruption every 60 seconds
[    0.318609] audit: initializing netlink socket (disabled)
[    0.318635] type=2000 audit(1274301857.318:1): initialized
[    0.339265] highmem bounce pool size: 64 pages
[    0.339284] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.344332] VFS: Disk quotas dquot_6.5.2
[    0.344529] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.346511] fuse init (API version 7.13)
[    0.346791] msgmni has been set to 1706
[    0.347448] alg: No test for stdrng (krng)
[    0.347637] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.347646] io scheduler noop registered
[    0.347652] io scheduler anticipatory registered
[    0.347658] io scheduler deadline registered
[    0.347805] io scheduler cfq registered (default)
[    0.348127]   alloc irq_desc for 24 on node -1
[    0.348135]   alloc kstat_irqs on node -1
[    0.348157] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.348176] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.348451]   alloc irq_desc for 25 on node -1
[    0.348458]   alloc kstat_irqs on node -1
[    0.348476] pcieport 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.348494] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.348775]   alloc irq_desc for 26 on node -1
[    0.348782]   alloc kstat_irqs on node -1
[    0.348800] pcieport 0000:00:1c.3: irq 26 for MSI/MSI-X
[    0.348819] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.349053] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.349353] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.349639] ACPI: AC Adapter [AC0] (off-line)
[    0.349897] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.401781] ACPI: Lid Switch [LID]
[    0.401960] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.401971] ACPI: Sleep Button [SLPB]
[    0.402106] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input2
[    0.402115] ACPI: Power Button [PWRB]
[    0.402247] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.402256] ACPI: Power Button [PWRF]
[    0.404137] ACPI: SSDT 3f7ae180 001FA (v01  PmRef  Cpu0Ist 00003000 INTL 20060113)
[    0.405516] ACPI: SSDT 3f7ae410 00724 (v01  PmRef  Cpu0Cst 00003001 INTL 20060113)
[    0.406685] Monitor-Mwait will be used to enter C-1 state
[    0.406787] Monitor-Mwait will be used to enter C-2 state
[    0.406877] Monitor-Mwait will be used to enter C-3 state
[    0.406901] Marking TSC unstable due to TSC halts in idle
[    0.407067] processor LNXCPU:00: registered as cooling_device0
[    0.408071] ACPI: SSDT 3f7ae0b0 000CC (v01  PmRef  Cpu1Ist 00003000 INTL 20060113)
[    0.409029] ACPI: SSDT 3f7ae380 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20060113)
[    0.409857] Switching to clocksource hpet
[    0.417370] processor LNXCPU:01: registered as cooling_device1
[    0.434781] thermal LNXTHERM:01: registered as thermal_zone0
[    0.434810] ACPI: Thermal Zone [TZ00] (46 C)
[    0.439943] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.444243] brd: module loaded
[    0.445767] loop: module loaded
[    0.446074] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.446348] ata_piix 0000:00:1f.2: version 2.13
[    0.446385] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.446397] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    0.446479] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.446699] scsi0 : ata_piix
[    0.446934] isapnp: Scanning for PnP cards...
[    0.496631] scsi1 : ata_piix
[    0.500930] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.500941] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.502338] Fixed MDIO Bus: probed
[    0.502453] PPP generic driver version 2.4.2
[    0.502602] tun: Universal TUN/TAP device driver, 1.6
[    0.502608] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.502862] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.502920]   alloc irq_desc for 23 on node -1
[    0.502927]   alloc kstat_irqs on node -1
[    0.502945] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.502979] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.502988] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.503109] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.503160] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.503182] ehci_hcd 0000:00:1d.7: debug port 1
[    0.507096] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.507140] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf7eb7c00
[    0.555422] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.555757] usb usb1: configuration #1 chosen from 1 choice
[    0.555850] hub 1-0:1.0: USB hub found
[    0.555874] hub 1-0:1.0: 8 ports detected
[    0.556096] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.556150] uhci_hcd: USB Universal Host Controller Interface driver
[    0.556311] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.556333] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.556343] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.556490] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.556539] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d400
[    0.556812] usb usb2: configuration #1 chosen from 1 choice
[    0.556899] hub 2-0:1.0: USB hub found
[    0.556920] hub 2-0:1.0: 2 ports detected
[    0.557064] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.557081] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.557090] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.557202] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.557273] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d480
[    0.557554] usb usb3: configuration #1 chosen from 1 choice
[    0.557641] hub 3-0:1.0: USB hub found
[    0.557662] hub 3-0:1.0: 2 ports detected
[    0.557794]   alloc irq_desc for 18 on node -1
[    0.557801]   alloc kstat_irqs on node -1
[    0.557817] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.557834] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.557902] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.558009] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.558074] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d800
[    0.558361] usb usb4: configuration #1 chosen from 1 choice
[    0.558444] hub 4-0:1.0: USB hub found
[    0.558464] hub 4-0:1.0: 2 ports detected
[    0.558591] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.558608] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.558617] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.558715] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.558775] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d880
[    0.559057] usb usb5: configuration #1 chosen from 1 choice
[    0.559150] hub 5-0:1.0: USB hub found
[    0.559172] hub 5-0:1.0: 2 ports detected
[    0.559452] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.588814] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.588859] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.589294] mice: PS/2 mouse device common for all mice
[    0.590256] rtc_cmos 00:03: RTC can wake from S4
[    0.590390] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.590443] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    0.590881] device-mapper: uevent: version 1.0.3
[    0.625485] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.645818] device-mapper: multipath: version 1.1.0 loaded
[    0.645828] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.649400] EISA: Probing bus 0 at eisa.0
[    0.649414] Cannot allocate resource for EISA slot 1
[    0.649422] Cannot allocate resource for EISA slot 2
[    0.649456] EISA: Detected 0 cards.
[    0.665690] cpuidle: using governor ladder
[    0.666014] cpuidle: using governor menu
[    0.667272] TCP cubic registered
[    0.667742] NET: Registered protocol family 10
[    0.668965] lo: Disabled Privacy Extensions
[    0.669901] NET: Registered protocol family 17
[    0.670900] Using IPI No-Shortcut mode
[    0.671131] PM: Resume from disk failed.
[    0.671164] registered taskstats version 1
[    0.672164]   Magic number: 10:228:751
[    0.672196] tty ttyS2: hash matches
[    0.672311] rtc_cmos 00:03: setting system clock to 2010-05-19 20:44:18 UTC (1274301858)
[    0.672320] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.672325] EDD information not available.
[    0.705382] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    0.829861] ACPI: Battery Slot [BAT0] (battery present)
[    0.855514] isapnp: No Plug & Play device found
[    0.913810] Freeing initrd memory: 12853k freed
[    0.924228] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    1.001690] ata1.00: ATA-8: ST9160310AS, 0303, max UDMA/133
[    1.001703] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.017094] ata1.00: configured for UDMA/133
[    1.017405] scsi 0:0:0:0: Direct-Access     ATA      ST9160310AS      0303 PQ: 0 ANSI: 5
[    1.017740] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.017763] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.017936] sd 0:0:0:0: [sda] Write Protect is off
[    1.017945] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.018023] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.018388]  sda:
[    1.054873] usb 1-2: configuration #1 chosen from 1 choice
[    1.079235]  sda1 sda2 < sda5
[    1.164123] usb 1-8: new high speed USB device using ehci_hcd and address 3
[    1.176073]  sda6 sda7 > sda3 sda4
[    1.211951] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.211983] Freeing unused kernel memory: 656k freed
[    1.212574] Write protecting the kernel text: 4676k
[    1.212646] Write protecting the kernel read-only data: 1840k
[    1.253340] udev: starting version 151
[    1.344961] usb 1-8: configuration #1 chosen from 1 choice
[    1.501627] ATL1E 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.501655] ATL1E 0000:03:00.0: setting latency timer to 64
[    1.541697] Linux agpgart interface v0.103
[    1.542845] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input6
[    1.542970] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    1.601423] Initializing USB Mass Storage driver...
[    1.605857] scsi2 : SCSI emulation for USB Mass Storage devices
[    1.606352] usbcore: registered new interface driver usb-storage
[    1.606363] USB Mass Storage support registered.
[    1.613321] usb-storage: device found at 2
[    1.613328] usb-storage: waiting for device to settle before scanning
[    1.646060] [drm] Initialized drm 1.1.0 20060810
[    1.655421] agpgart-intel 0000:00:00.0: Intel 945GME Chipset
[    1.655992] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[    1.659113] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    1.722068] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.722080] i915 0000:00:02.0: setting latency timer to 64
[    1.729814] [drm] set up 7M of stolen space
[    1.832321] composite sync not supported
[    1.832683] [drm] initialized overlay support
[    2.249455] [drm:edid_is_valid] *ERROR* EDID checksum is invalid, remainder is 158
[    2.249462] [drm:edid_is_valid] *ERROR* Raw EDID:
[    2.249470] <3>00 ff ff ff ff ff ff 00 22 64 e9 03 a8 b8 03 00  ........"d......
[    2.249476] <3>0c 13 01 03 80 16 0d 78 0a 86 26 94 57 51 90 27  .......x..&.WQ.'
[    2.249482] <3>21 4f 54 00 00 00 01 01 01 01 01 01 01 01 01 01  !OT.............
[    2.249488] <3>01 01 01 01 01 01 94 11 00 b0 40 58 19 20 35 23  ..........@X. 5#
[    2.249493] <3>45 00 dc 81 00 00 00 19 16 14 00 d8 40 58 26 20  E...........@X&
[    2.249499] <3>7f 23 ff 04 ff 81 ff ff ff ff ff ff ff ff ff ff  .#..............
[    2.249504] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[    2.249510] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[    2.249514]
[    2.258897] fb0: inteldrmfb frame buffer device
[    2.258902] registered panic notifier
[    2.258917] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    2.264673] vga16fb: initializing
[    2.264686] vga16fb: mapped to 0xc00a0000
[    2.264696] vga16fb: not registering due to another framebuffer present
[    2.527678] Console: switching to colour frame buffer device 128x37
[COLOR=Red] [    3.633046] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0[/COLOR]
[    3.633058] ata1.00: BMDMA stat 0x24
[    3.633071] ata1.00: failed command: READ DMA EXT
[    3.633093] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[    3.633099]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[    3.633109] ata1.00: status: { DRDY ERR }
[    3.633117] ata1.00: error: { UNC }
[    3.781146] ata1.00: configured for UDMA/133
[    3.781184] ata1: EH complete
[    6.053484] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[    6.053496] ata1.00: BMDMA stat 0x24
[    6.053508] ata1.00: failed command: READ DMA EXT
[    6.053531] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[    6.053536]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[    6.053547] ata1.00: status: { DRDY ERR }
[    6.053555] ata1.00: error: { UNC }
[    6.189118] ata1.00: configured for UDMA/133
[    6.189155] ata1: EH complete
[    6.612564] usb-storage: device scan complete
[    6.613360] scsi 2:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
[    6.616105] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    6.617293] sd 2:0:0:0: [sdb] 31252024 512-byte logical blocks: (16.0 GB/14.9 GiB)
[    6.617915] sd 2:0:0:0: [sdb] Write Protect is off
[    6.617929] sd 2:0:0:0: [sdb] Mode Sense: 16 07 09 51
[    6.617938] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    6.621297] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    6.621315]  sdb: sdb1 sdb2 < sdb5 >
[    6.626750] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    6.626763] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[    8.485325] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[    8.485337] ata1.00: BMDMA stat 0x24
[    8.485349] ata1.00: failed command: READ DMA EXT
[    8.485381] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[    8.485384]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[    8.485391] ata1.00: status: { DRDY ERR }
[    8.485396] ata1.00: error: { UNC }
[    8.628987] ata1.00: configured for UDMA/133
[    8.629036] ata1: EH complete
[   10.917215] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   10.917227] ata1.00: BMDMA stat 0x24
[   10.917239] ata1.00: failed command: READ DMA EXT
[   10.917262] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[   10.917267]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[   10.917278] ata1.00: status: { DRDY ERR }
[   10.917286] ata1.00: error: { UNC }
[   11.061151] ata1.00: configured for UDMA/133
[   11.061189] ata1: EH complete
[   13.337908] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   13.337920] ata1.00: BMDMA stat 0x24
[   13.337933] ata1.00: failed command: READ DMA EXT
[   13.337955] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[   13.337960]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[   13.337971] ata1.00: status: { DRDY ERR }
[   13.337979] ata1.00: error: { UNC }
[   13.493112] ata1.00: configured for UDMA/133
[   13.493150] ata1: EH complete
[   15.780764] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   15.780776] ata1.00: BMDMA stat 0x24
[   15.780789] ata1.00: failed command: READ DMA EXT
[   15.780811] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[   15.780816]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[   15.780827] ata1.00: status: { DRDY ERR }
[   15.780835] ata1.00: error: { UNC }
[   15.925152] ata1.00: configured for UDMA/133
[   15.925192] sd 0:0:0:0: [sda] Unhandled sense code
[   15.925200] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   15.925213] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[   15.925229] Descriptor sense data with sense descriptors (in hex):
[   15.925237]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00
[   15.925271]         12 a1 9e af
[   15.925285] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[   15.925307] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 12 a1 9e a8 00 00 08 00
[   15.925326] end_request: I/O error, dev sda, sector 312581807
[   15.925334] Buffer I/O error on device sda, logical block 39072725
[   15.925371] ata1: EH complete
[   18.201427] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   18.201439] ata1.00: BMDMA stat 0x24
[   18.201452] ata1.00: failed command: READ DMA EXT
[   18.201475] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[   18.201480]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[   18.201491] ata1.00: status: { DRDY ERR }
[   18.201499] ata1.00: error: { UNC }
[   18.348955] ata1.00: configured for UDMA/133
[   18.348988] ata1: EH complete
[   20.633222] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   20.633233] ata1.00: BMDMA stat 0x24
[   20.633245] ata1.00: failed command: READ DMA EXT
[   20.633267] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[   20.633272]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[   20.633283] ata1.00: status: { DRDY ERR }
[   20.633291] ata1.00: error: { UNC }
[   20.804951] ata1.00: configured for UDMA/133
[   20.804980] ata1: EH complete
[   23.109433] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   23.109444] ata1.00: BMDMA stat 0x24
[   23.109456] ata1.00: failed command: READ DMA EXT
[   23.109478] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[   23.109483]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[   23.109494] ata1.00: status: { DRDY ERR }
[   23.109502] ata1.00: error: { UNC }
[   23.264960] ata1.00: configured for UDMA/133
[   23.264987] ata1: EH complete
[   25.552349] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   25.552361] ata1.00: BMDMA stat 0x24
[   25.552372] ata1.00: failed command: READ DMA EXT
[   25.552394] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[   25.552399]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[   25.552410] ata1.00: status: { DRDY ERR }
[   25.552418] ata1.00: error: { UNC }
[   25.700940] ata1.00: configured for UDMA/133
[   25.700969] ata1: EH complete
[   27.973059] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   27.973071] ata1.00: BMDMA stat 0x24
[   27.973082] ata1.00: failed command: READ DMA EXT
[   27.973104] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[   27.973109]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[   27.973120] ata1.00: status: { DRDY ERR }
[   27.973128] ata1.00: error: { UNC }
[   28.116961] ata1.00: configured for UDMA/133
[   28.116988] ata1: EH complete
[   30.393749] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   30.393760] ata1.00: BMDMA stat 0x24
[   30.393772] ata1.00: failed command: READ DMA EXT
[   30.393794] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[   30.393799]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[   30.393810] ata1.00: status: { DRDY ERR }
[   30.393818] ata1.00: error: { UNC }
[   30.536939] ata1.00: configured for UDMA/133
[   30.536972] sd 0:0:0:0: [sda] Unhandled sense code
[   30.536981] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.536993] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[   30.537009] Descriptor sense data with sense descriptors (in hex):
[   30.537017]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00
[   30.537051]         12 a1 9e af
[   30.537075] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[   30.537086] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 12 a1 9e a8 00 00 08 00
[   30.537105] end_request: I/O error, dev sda, sector 312581807
[   30.537113] Buffer I/O error on device sda, logical block 39072725
[   30.537148] ata1: EH complete
[   32.825553] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   32.825564] ata1.00: BMDMA stat 0x24
[   32.825577] ata1.00: failed command: READ DMA EXT
[   32.825599] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[   32.825604]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[   32.825615] ata1.00: status: { DRDY ERR }
[   32.825623] ata1.00: error: { UNC }
[   32.968939] ata1.00: configured for UDMA/133
[   32.968967] ata1: EH complete
[   33.452076] usb 3-1: new low speed USB device using uhci_hcd and address 2
[   33.629387] usb 3-1: configuration #1 chosen from 1 choice
[   33.676294] usbcore: registered new interface driver hiddev
[   33.692202] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input7
[   33.692879] generic-usb 0003:046D:C521.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-1/input0
[   33.723439] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.1/input/input8
[   33.723719] generic-usb 0003:046D:C521.0002: input,hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.1-1/input1
[   33.723773] usbcore: registered new interface driver usbhid
[   33.723780] usbhid: v2.6:USB HID core driver
[   35.246263] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   35.246275] ata1.00: BMDMA stat 0x24
[   35.246288] ata1.00: failed command: READ DMA EXT
[   35.246310] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[   35.246316]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[   35.246326] ata1.00: status: { DRDY ERR }
[   35.246335] ata1.00: error: { UNC }
[   35.380952] ata1.00: configured for UDMA/133
[   35.380986] ata1: EH complete
[   37.666946] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   37.666957] ata1.00: BMDMA stat 0x24
[   37.666969] ata1.00: failed command: READ DMA EXT
[   37.666991] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[   37.666996]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[   37.667007] ata1.00: status: { DRDY ERR }
[   37.667015] ata1.00: error: { UNC }
[   37.788958] ata1.00: configured for UDMA/133
[   37.788985] ata1: EH complete
[   40.076544] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   40.076555] ata1.00: BMDMA stat 0x24
[   40.076567] ata1.00: failed command: READ DMA EXT
[   40.076589] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[   40.076594]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[   40.076604] ata1.00: status: { DRDY ERR }
[   40.076612] ata1.00: error: { UNC }
[   40.220961] ata1.00: configured for UDMA/133
[   40.220990] ata1: EH complete
[   42.497244] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   42.497255] ata1.00: BMDMA stat 0x24
[   42.497267] ata1.00: failed command: READ DMA EXT
[   42.497289] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[   42.497294]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[   42.497305] ata1.00: status: { DRDY ERR }
[   42.497313] ata1.00: error: { UNC }
[   42.644941] ata1.00: configured for UDMA/133
[   42.644969] ata1: EH complete
[   44.929044] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   44.929056] ata1.00: BMDMA stat 0x24
[   44.929067] ata1.00: failed command: READ DMA EXT
[   44.929090] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[   44.929095]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[   44.929106] ata1.00: status: { DRDY ERR }
[   44.929114] ata1.00: error: { UNC }
[   45.072933] ata1.00: configured for UDMA/133
[   45.072966] sd 0:0:0:0: [sda] Unhandled sense code
[   45.072975] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   45.072987] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[   45.073003] Descriptor sense data with sense descriptors (in hex):
[   45.073011]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00
[   45.073044]         12 a1 9e af
[   45.073069] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[   45.073079] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 12 a1 9e a8 00 00 08 00
[   45.073098] end_request: I/O error, dev sda, sector 312581807
[   45.073106] Buffer I/O error on device sda, logical block 39072725
[   45.073138] ata1: EH complete
[   47.360857] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   47.360869] ata1.00: BMDMA stat 0x24
[   47.360881] ata1.00: failed command: READ DMA EXT
[   47.360903] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[   47.360908]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[   47.360919] ata1.00: status: { DRDY ERR }
[   47.360927] ata1.00: error: { UNC }
[   47.492940] ata1.00: configured for UDMA/133
[   47.492969] ata1: EH complete
[   49.770445] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   49.770456] ata1.00: BMDMA stat 0x24
[   49.770468] ata1.00: failed command: READ DMA EXT
[   49.770490] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[   49.770495]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[   49.770506] ata1.00: status: { DRDY ERR }
[   49.770514] ata1.00: error: { UNC }
[   49.916947] ata1.00: configured for UDMA/133
[   49.916974] ata1: EH complete
[   52.191147] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   52.191158] ata1.00: BMDMA stat 0x24
[   52.191169] ata1.00: failed command: READ DMA EXT
[   52.191192] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[   52.191197]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[   52.191208] ata1.00: status: { DRDY ERR }
[   52.191216] ata1.00: error: { UNC }
[   52.364931] ata1.00: configured for UDMA/133
[   52.364959] ata1: EH complete
[   54.645106] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   54.645117] ata1.00: BMDMA stat 0x24
[   54.645129] ata1.00: failed command: READ DMA EXT
[   54.645151] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[   54.645156]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[   54.645167] ata1.00: status: { DRDY ERR }
[   54.645175] ata1.00: error: { UNC }
[   54.788941] ata1.00: configured for UDMA/133
[   54.788967] ata1: EH complete
[   57.065808] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   57.065819] ata1.00: BMDMA stat 0x24
[   57.065831] ata1.00: failed command: READ DMA EXT
[   57.065853] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[   57.065858]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[   57.065868] ata1.00: status: { DRDY ERR }
[   57.065876] ata1.00: error: { UNC }
[   57.208941] ata1.00: configured for UDMA/133
[   57.208969] ata1: EH complete
[   59.497658] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   59.497669] ata1.00: BMDMA stat 0x24
[   59.497681] ata1.00: failed command: READ DMA EXT
[   59.497703] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[   59.497708]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[   59.497719] ata1.00: status: { DRDY ERR }
[   59.497727] ata1.00: error: { UNC }
[   59.632953] ata1.00: configured for UDMA/133
[   59.632983] sd 0:0:0:0: [sda] Unhandled sense code
[   59.632992] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   59.633003] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[   59.633019] Descriptor sense data with sense descriptors (in hex):
[   59.633027]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00
[   59.633061]         12 a1 9e af
[   59.633086] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[   59.633097] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 12 a1 9e a8 00 00 08 00
[   59.633116] end_request: I/O error, dev sda, sector 312581807
[   59.633123] Buffer I/O error on device sda, logical block 39072725
[   59.633155] ata1: EH complete
[   61.907246] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   61.907258] ata1.00: BMDMA stat 0x24
[   61.907270] ata1.00: failed command: READ DMA EXT
[   61.907292] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[   61.907297]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[   61.907308] ata1.00: status: { DRDY ERR }
[   61.907316] ata1.00: error: { UNC }
[   62.052960] ata1.00: configured for UDMA/133
[   62.052990] ata1: EH complete
[   64.327955] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   64.327966] ata1.00: BMDMA stat 0x24
[   64.327978] ata1.00: failed command: READ DMA EXT
[   64.328000] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[   64.328005]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[   64.328048] ata1.00: status: { DRDY ERR }
[   64.328060] ata1.00: error: { UNC }
[   64.448939] ata1.00: configured for UDMA/133
[   64.448967] ata1: EH complete
[   66.726444] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   66.726455] ata1.00: BMDMA stat 0x24
[   66.726466] ata1.00: failed command: READ DMA EXT
[   66.726489] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[   66.726494]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[   66.726505] ata1.00: status: { DRDY ERR }
[   66.726513] ata1.00: error: { UNC }
[   66.872943] ata1.00: configured for UDMA/133
[   66.872972] ata1: EH complete
[   69.158244] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   69.158255] ata1.00: BMDMA stat 0x24
[   69.158267] ata1.00: failed command: READ DMA EXT
[   69.158289] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[   69.158294]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[   69.158305] ata1.00: status: { DRDY ERR }
[   69.158313] ata1.00: error: { UNC }
[   69.300938] ata1.00: configured for UDMA/133
[   69.300965] ata1: EH complete
[   71.578944] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   71.578955] ata1.00: BMDMA stat 0x24
[   71.578967] ata1.00: failed command: READ DMA EXT
[   71.578989] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[   71.578994]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[   71.579005] ata1.00: status: { DRDY ERR }
[   71.579013] ata1.00: error: { UNC }
[   71.756928] ata1.00: configured for UDMA/133
[   71.756958] ata1: EH complete
[   74.055164] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   74.055175] ata1.00: BMDMA stat 0x24
[   74.055186] ata1.00: failed command: READ DMA EXT
[   74.055208] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[   74.055213]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[   74.055224] ata1.00: status: { DRDY ERR }
[   74.055232] ata1.00: error: { UNC }
[   74.224961] ata1.00: configured for UDMA/133
[   74.224992] sd 0:0:0:0: [sda] Unhandled sense code
[   74.225001] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   74.225013] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[   74.225028] Descriptor sense data with sense descriptors (in hex):
[   74.225036]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00
[   74.225070]         12 a1 9e af
[   74.225095] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[   74.225106] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 12 a1 9e a8 00 00 08 00
[   74.225124] end_request: I/O error, dev sda, sector 312581807
[   74.225132] Buffer I/O error on device sda, logical block 39072725
[   74.225162] ata1: EH complete
[   76.509181] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   76.509193] ata1.00: BMDMA stat 0x24
[   76.509205] ata1.00: failed command: READ DMA EXT
[   76.509227] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[   76.509232]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[   76.509243] ata1.00: status: { DRDY ERR }
[   76.509251] ata1.00: error: { UNC }
[   76.652949] ata1.00: configured for UDMA/133
[   76.652979] ata1: EH complete
[   78.940977] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   78.940989] ata1.00: BMDMA stat 0x24
[   78.941000] ata1.00: failed command: READ DMA EXT
[   78.941022] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[   78.941028]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[   78.941038] ata1.00: status: { DRDY ERR }
[   78.941046] ata1.00: error: { UNC }
[   79.084943] ata1.00: configured for UDMA/133
[   79.084969] ata1: EH complete
[   81.361679] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   81.361690] ata1.00: BMDMA stat 0x24
[   81.361701] ata1.00: failed command: READ DMA EXT
[   81.361724] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[   81.361729]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[   81.361740] ata1.00: status: { DRDY ERR }
[   81.361748] ata1.00: error: { UNC }
[   81.524945] ata1.00: configured for UDMA/133
[   81.524974] ata1: EH complete
[   83.804533] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   83.804545] ata1.00: BMDMA stat 0x24
[   83.804556] ata1.00: failed command: READ DMA EXT
[   83.804579] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[   83.804584]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[   83.804594] ata1.00: status: { DRDY ERR }
[   83.804603] ata1.00: error: { UNC }
[   83.956945] ata1.00: configured for UDMA/133
[   83.956972] ata1: EH complete
[   86.258601] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   86.258612] ata1.00: BMDMA stat 0x24
[   86.258624] ata1.00: failed command: READ DMA EXT
[   86.258646] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[   86.258651]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[   86.258662] ata1.00: status: { DRDY ERR }
[   86.258670] ata1.00: error: { UNC }
[   86.404947] ata1.00: configured for UDMA/133
[   86.404975] ata1: EH complete
[   88.701489] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   88.701500] ata1.00: BMDMA stat 0x24
[   88.701512] ata1.00: failed command: READ DMA EXT
[   88.701534] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[   88.701539]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[   88.701550] ata1.00: status: { DRDY ERR }
[   88.701558] ata1.00: error: { UNC }
[   88.832944] ata1.00: configured for UDMA/133
[   88.832974] sd 0:0:0:0: [sda] Unhandled sense code
[   88.832983] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   88.832995] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[   88.833010] Descriptor sense data with sense descriptors (in hex):
[   88.833018]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00
[   88.833052]         12 a1 9e af
[   88.833077] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[   88.833088] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 12 a1 9e a8 00 00 08 00
[   88.833107] end_request: I/O error, dev sda, sector 312581807
[   88.833114] Buffer I/O error on device sda, logical block 39072725
[   88.833145] ata1: EH complete
[   91.122205] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   91.122216] ata1.00: BMDMA stat 0x24
[   91.122228] ata1.00: failed command: READ DMA EXT
[   91.122251] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[   91.122256]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[   91.122267] ata1.00: status: { DRDY ERR }
[   91.122275] ata1.00: error: { UNC }
[   91.264938] ata1.00: configured for UDMA/133
[   91.264969] ata1: EH complete
[   93.542850] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   93.542861] ata1.00: BMDMA stat 0x24
[   93.542872] ata1.00: failed command: READ DMA EXT
[   93.542895] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[   93.542900]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[   93.542910] ata1.00: status: { DRDY ERR }
[   93.542918] ata1.00: error: { UNC }
[   93.716959] ata1.00: configured for UDMA/133
[   93.716986] ata1: EH complete
[   96.008033] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   96.008045] ata1.00: BMDMA stat 0x24
[   96.008056] ata1.00: failed command: READ DMA EXT
[   96.008078] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[   96.008083]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[   96.008094] ata1.00: status: { DRDY ERR }
[   96.008102] ata1.00: error: { UNC }
[   96.152941] ata1.00: configured for UDMA/133
[   96.152969] ata1: EH complete
[   98.439817] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   98.439828] ata1.00: BMDMA stat 0x24
[   98.439840] ata1.00: failed command: READ DMA EXT
[   98.439862] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[   98.439867]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[   98.439878] ata1.00: status: { DRDY ERR }
[   98.439886] ata1.00: error: { UNC }
[   98.572940] ata1.00: configured for UDMA/133
[   98.572967] ata1: EH complete
[  100.871623] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  100.871635] ata1.00: BMDMA stat 0x24
[  100.871646] ata1.00: failed command: READ DMA EXT
[  100.871669] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[  100.871674]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[  100.871684] ata1.00: status: { DRDY ERR }
[  100.871692] ata1.00: error: { UNC }
[  101.004944] ata1.00: configured for UDMA/133
[  101.004972] ata1: EH complete
[  103.281218] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  103.281229] ata1.00: BMDMA stat 0x24
[  103.281240] ata1.00: failed command: READ DMA EXT
[  103.281262] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[  103.281267]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[  103.281278] ata1.00: status: { DRDY ERR }
[  103.281286] ata1.00: error: { UNC }
[  103.424939] ata1.00: configured for UDMA/133
[  103.424969] sd 0:0:0:0: [sda] Unhandled sense code
[  103.424977] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  103.424989] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  103.425004] Descriptor sense data with sense descriptors (in hex):
[  103.425012]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00
[  103.425046]         12 a1 9e af
[  103.425071] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  103.425082] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 12 a1 9e a8 00 00 08 00
[  103.425100] end_request: I/O error, dev sda, sector 312581807
[  103.425108] Buffer I/O error on device sda, logical block 39072725
[  103.425138] ata1: EH complete
[  105.746337] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  105.746348] ata1.00: BMDMA stat 0x24
[  105.746360] ata1.00: failed command: READ DMA EXT
[  105.746382] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[  105.746387]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[  105.746398] ata1.00: status: { DRDY ERR }
[  105.746406] ata1.00: error: { UNC }
[  105.888967] ata1.00: configured for UDMA/133
[  105.888996] ata1: EH complete
[  108.178133] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  108.178144] ata1.00: BMDMA stat 0x24
[  108.178155] ata1.00: failed command: READ DMA EXT
[  108.178177] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[  108.178182]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[  108.178193] ata1.00: status: { DRDY ERR }
[  108.178201] ata1.00: error: { UNC }
[  108.320964] ata1.00: configured for UDMA/133
[  108.320991] ata1: EH complete
[  110.598834] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  110.598845] ata1.00: BMDMA stat 0x24
[  110.598856] ata1.00: failed command: READ DMA EXT
[  110.598878] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[  110.598883]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[  110.598894] ata1.00: status: { DRDY ERR }
[  110.598902] ata1.00: error: { UNC }
[  110.744943] ata1.00: configured for UDMA/133
[  110.744971] ata1: EH complete
[  113.041740] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  113.041751] ata1.00: BMDMA stat 0x24
[  113.041762] ata1.00: failed command: READ DMA EXT
[  113.041784] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[  113.041789]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[  113.041800] ata1.00: status: { DRDY ERR }
[  113.041808] ata1.00: error: { UNC }
[  113.196963] ata1.00: configured for UDMA/133
[  113.196989] ata1: EH complete
[  115.473544] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  115.473555] ata1.00: BMDMA stat 0x24
[  115.473566] ata1.00: failed command: READ DMA EXT
[  115.473589] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[  115.473594]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[  115.473604] ata1.00: status: { DRDY ERR }
[  115.473612] ata1.00: error: { UNC }
[  115.620943] ata1.00: configured for UDMA/133
[  115.620971] ata1: EH complete
[  117.905344] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  117.905355] ata1.00: BMDMA stat 0x24
[  117.905366] ata1.00: failed command: READ DMA EXT
[  117.905389] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[  117.905394]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[  117.905404] ata1.00: status: { DRDY ERR }
[  117.905412] ata1.00: error: { UNC }
[  118.048942] ata1.00: configured for UDMA/133
[  118.048973] sd 0:0:0:0: [sda] Unhandled sense code
[  118.048981] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  118.048993] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  118.049008] Descriptor sense data with sense descriptors (in hex):
[  118.049015]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00
[  118.049049]         12 a1 9e af
[  118.049063] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  118.049085] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 12 a1 9e a8 00 00 08 00
[  118.049104] end_request: I/O error, dev sda, sector 312581807
[  118.049111] Buffer I/O error on device sda, logical block 39072725
[  118.049139] ata1: EH complete
[  120.337153] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  120.337164] ata1.00: BMDMA stat 0x24
[  120.337176] ata1.00: failed command: READ DMA EXT
[  120.337198] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[  120.337203]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[  120.337214] ata1.00: status: { DRDY ERR }
[  120.337222] ata1.00: error: { UNC }
[  120.480940] ata1.00: configured for UDMA/133
[  120.480970] ata1: EH complete
[  122.757842] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  122.757853] ata1.00: BMDMA stat 0x24
[  122.757865] ata1.00: failed command: READ DMA EXT
[  122.757887] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[  122.757892]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[  122.757903] ata1.00: status: { DRDY ERR }
[  122.757911] ata1.00: error: { UNC }
[  122.892943] ata1.00: configured for UDMA/133
[  122.892971] ata1: EH complete
[  125.178546] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  125.178557] ata1.00: BMDMA stat 0x24
[  125.178569] ata1.00: failed command: READ DMA EXT
[  125.178591] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[  125.178596]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[  125.178607] ata1.00: status: { DRDY ERR }
[  125.178615] ata1.00: error: { UNC }
[  125.324947] ata1.00: configured for UDMA/133
[  125.324977] ata1: EH complete
[  127.599195] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  127.599206] ata1.00: BMDMA stat 0x24
[  127.599217] ata1.00: failed command: READ DMA EXT
[  127.599239] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[  127.599244]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[  127.599255] ata1.00: status: { DRDY ERR }
[  127.599263] ata1.00: error: { UNC }
[  127.744951] ata1.00: configured for UDMA/133
[  127.744978] ata1: EH complete
[  130.019990] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  130.020001] ata1.00: BMDMA stat 0x24
[  130.020050] ata1.00: failed command: READ DMA EXT
[  130.020076] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[  130.020081]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[  130.020092] ata1.00: status: { DRDY ERR }
[  130.020100] ata1.00: error: { UNC }
[  130.140964] ata1.00: configured for UDMA/133
[  130.140991] ata1: EH complete
[  132.440645] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  132.440656] ata1.00: BMDMA stat 0x24
[  132.440667] ata1.00: failed command: READ DMA EXT
[  132.440689] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[  132.440694]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[  132.440705] ata1.00: status: { DRDY ERR }
[  132.440713] ata1.00: error: { UNC }
[  132.584961] ata1.00: configured for UDMA/133
[  132.584992] sd 0:0:0:0: [sda] Unhandled sense code
[  132.585000] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  132.585012] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  132.585028] Descriptor sense data with sense descriptors (in hex):
[  132.585036]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00
[  132.585070]         12 a1 9e af
[  132.585095] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  132.585106] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 12 a1 9e a8 00 00 08 00
[  132.585124] end_request: I/O error, dev sda, sector 312581807
[  132.585132] Buffer I/O error on device sda, logical block 39072725
[  132.585161] ata1: EH complete
[  134.872499] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  134.872510] ata1.00: BMDMA stat 0x24
[  134.872522] ata1.00: failed command: READ DMA EXT
[  134.872544] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[  134.872549]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[  134.872560] ata1.00: status: { DRDY ERR }
[  134.872568] ata1.00: error: { UNC }
[  135.004964] ata1.00: configured for UDMA/133
[  135.004991] ata1: EH complete
[  137.293133] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  137.293144] ata1.00: BMDMA stat 0x24
[  137.293156] ata1.00: failed command: READ DMA EXT
[  137.293178] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[  137.293183]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[  137.293194] ata1.00: status: { DRDY ERR }
[  137.293202] ata1.00: error: { UNC }
[  137.436967] ata1.00: configured for UDMA/133
[  137.436996] ata1: EH complete
[  139.724997] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  139.725008] ata1.00: BMDMA stat 0x24
[  139.725020] ata1.00: failed command: READ DMA EXT
[  139.725042] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[  139.725047]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[  139.725058] ata1.00: status: { DRDY ERR }
[  139.725066] ata1.00: error: { UNC }
[  139.868966] ata1.00: configured for UDMA/133
[  139.868993] ata1: EH complete
[  142.156703] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  142.156714] ata1.00: BMDMA stat 0x24
[  142.156726] ata1.00: failed command: READ DMA EXT
[  142.156748] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[  142.156753]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[  142.156764] ata1.00: status: { DRDY ERR }
[  142.156772] ata1.00: error: { UNC }
[  142.332941] ata1.00: configured for UDMA/133
[  142.332969] ata1: EH complete
[  144.610761] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  144.610772] ata1.00: BMDMA stat 0x24
[  144.610783] ata1.00: failed command: READ DMA EXT
[  144.610805] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[  144.610811]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[  144.610821] ata1.00: status: { DRDY ERR }
[  144.610829] ata1.00: error: { UNC }
[  144.752950] ata1.00: configured for UDMA/133
[  144.752976] ata1: EH complete
[  147.042567] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  147.042579] ata1.00: BMDMA stat 0x24
[  147.042590] ata1.00: failed command: READ DMA EXT
[  147.042612] ata1.00: cmd 25/00:08:a8:9e:a1/00:00:12:00:00/e0 tag 0 dma 4096 in
[  147.042617]          res 51/40:00:af:9e:a1/40:00:12:00:00/00 Emask 0x9 (media error)
[  147.042628] ata1.00: status: { DRDY ERR }
[  147.042636] ata1.00: error: { UNC }
[  147.188964] ata1.00: configured for UDMA/133
[  147.188996] sd 0:0:0:0: [sda] Unhandled sense code
[  147.189004] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  147.189016] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  147.189031] Descriptor sense data with sense descriptors (in hex):
[  147.189039]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00
[  147.189073]         12 a1 9e af
[  147.189098] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  147.189109] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 12 a1 9e a8 00 00 08 00
[  147.189127] end_request: I/O error, dev sda, sector 312581807
[  147.189134] Buffer I/O error on device sda, logical block 39072725
[  147.189162] ata1: EH complete
[  149.017409] composite sync not supported
[  149.239258] EXT4-fs (sdb1): mounted filesystem with ordered data mode
[  155.092594] Adding 1952760k swap on /dev/sdb5.  Priority:-1 extents:1 across:1952760k
[  155.166806] udev: starting version 151
[  155.278765] lp: driver loaded but no devices found
[  155.562437] eeepc_laptop: Eee PC Hotkey Driver
[  155.563768] eeepc_laptop: Hotkey init flags 0x41
[  155.564082] eeepc_laptop: TYPE (2000000) not reported by BIOS, enabling anyway
[  155.580323] eeepc_laptop: PANELPOWER (4000000) not reported by BIOS, enabling anyway
[  155.580341] eeepc_laptop: Get control methods supported: 0x6301713
[  155.583858] input: Asus EeePC extra buttons as /devices/platform/eeepc/input/input9
[  155.942821] Linux video capture interface: v2.00
[  155.945409] cfg80211: Calling CRDA to update world regulatory domain
[  155.976184] intel_rng: FWH not detected
[  156.010982] uvcvideo: Found UVC 1.00 device CNF7129 (04f2:b071)
[  156.036065] input: CNF7129 as /devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/input/input10
[  156.036234] usbcore: registered new interface driver uvcvideo
[  156.036244] USB Video Class driver (v0.1.0)
[  156.065450] cfg80211: World regulatory domain updated:
[  156.065460]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  156.065470]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  156.065479]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  156.065489]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  156.065498]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  156.065507]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  156.214502] ath9k 0000:01:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[  156.214525] ath9k 0000:01:00.0: setting latency timer to 64
[  156.404412] psmouse serio1: ID: 10 00 64
[  156.598517] elantech.c: assuming hardware version 2, firmware version 2.48
[  156.653402] ath: EEPROM regdomain: 0x60
[  156.653411] ath: EEPROM indicates we should expect a direct regpair map
[  156.653423] ath: Country alpha2 being used: 00
[  156.653429] ath: Regpair used: 0x60
[  156.684443] elantech.c: Synaptics capabilities query result 0x00, 0x02, 0x64.
[  156.693221] type=1505 audit(1274291214.520:2):  operation="profile_load" pid=691 name="/sbin/dhclient3"
[  156.693988] type=1505 audit(1274291214.520:3):  operation="profile_load" pid=691 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[  156.694425] type=1505 audit(1274291214.520:4):  operation="profile_load" pid=691 name="/usr/lib/connman/scripts/dhclient-script"
[  156.898987] phy0: Selected rate control algorithm 'ath9k_rate_control'
[  156.901344] Registered led device: ath9k-phy0::radio
[  156.901404] Registered led device: ath9k-phy0::assoc
[  156.901462] Registered led device: ath9k-phy0::tx
[  156.901522] Registered led device: ath9k-phy0::rx
[  156.901560] phy0: Atheros AR9280 MAC/BB Rev:2 AR5133 RF Rev:d0: mem=0xf81a0000, irq=19
[  156.935505] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio1/input/input11
[  157.042426]   alloc irq_desc for 27 on node -1
[  157.042437]   alloc kstat_irqs on node -1
[  157.042468] ATL1E 0000:03:00.0: irq 27 for MSI/MSI-X
[  157.043236] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  157.101207] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  157.101279] HDA Intel 0000:00:1b.0: setting latency timer to 64
[  157.133865] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  157.262365] type=1505 audit(1274291215.087:5):  operation="profile_replace" pid=862 name="/sbin/dhclient3"
[  157.263127] type=1505 audit(1274291215.087:6):  operation="profile_replace" pid=862 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[  157.263561] type=1505 audit(1274291215.087:7):  operation="profile_replace" pid=862 name="/usr/lib/connman/scripts/dhclient-script"
[  157.279433] type=1505 audit(1274291215.103:8):  operation="profile_load" pid=863 name="/usr/bin/evince"
[  157.301674] type=1505 audit(1274291215.127:9):  operation="profile_load" pid=863 name="/usr/bin/evince-previewer"
[  157.310391] type=1505 audit(1274291215.135:10):  operation="profile_load" pid=863 name="/usr/bin/evince-thumbnailer"
[  157.347971] type=1505 audit(1274291215.171:11):  operation="profile_load" pid=868 name="/usr/bin/freshclam"
[  157.752144] composite sync not supported
[  157.890705] composite sync not supported
[  158.230977] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
[  158.249058] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x020c0000
[  158.249458] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input12

```As you might notice it seems to get stuck with that EMASK exception that seems to be caused by a bad sector. When I used BackTrack 4 this lead me to the initramfs, and made it impossible to start. Ubuntu installed to a USB-stick starts, but with a delay.

When trying to identify in which partition the problem is, fdisk -l gives me this for the disk sda:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
214 heads, 54 sectors/track, 27049 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9358c633

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          54   151129367    75564657    7  HPFS/NTFS
/dev/sda2       151129368   302247179    75558906    f  W95 Ext'd (LBA)
/dev/sda3       302247180   312497351     5125086   1c  Hidden W95 FAT32 (LBA)
/dev/sda4       312497352   312578243       40446   ef  EFI (FAT-12/16/32)
/dev/sda5       151129422   224856647    36863613   17  Hidden HPFS/NTFS
/dev/sda6       224856702   297127871    36135585   83  Linux
/dev/sda7       297127926   302247179     2559627   82  Linux swap / Solaris

```So, seemingly, the sector the gmesg is complaining about, 312581807, is not in any of the partitions, and it is the second last sector of the disk.

To try to figure out more about this I also ran smartctl -a /dev/sda, advice which I found in another thread, in hope of getting more info about the issue. The result:

```
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     ST9160310AS
Serial Number:    5SV5DNVD
Firmware Version: 0303
User Capacity:    160 041 885 696 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Thu May 20 00:08:27 2010 EEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.

General SMART Values:
Offline data collection status:  (0x82)    Offline data collection activity
                    was completed without error.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:          ( 712) seconds.
Offline data collection
capabilities:              (0x7b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   1) minutes.
Extended self-test routine
recommended polling time:      (  62) minutes.
Conveyance self-test routine
recommended polling time:      (   2) minutes.
SCT capabilities:            (0x103f)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   087   077   006    Pre-fail  Always       -       156461629
  3 Spin_Up_Time            0x0003   099   099   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       713
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   076   060   030    Pre-fail  Always       -       42553784
  9 Power_On_Hours          0x0032   097   097   000    Old_age   Always       -       2688
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       692
184 Unknown_Attribute       0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   001   001   000    Old_age   Always       -       14244
188 Unknown_Attribute       0x0032   099   074   000    Old_age   Always       -       236
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   056   043   045    Old_age   Always   In_the_past 44 (0 13 44 29)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       287
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       31
193 Load_Cycle_Count        0x0032   085   085   000    Old_age   Always       -       31734
194 Temperature_Celsius     0x0022   044   057   000    Old_age   Always       -       44 (0 15 0 0)
195 Hardware_ECC_Recovered  0x001a   058   050   000    Old_age   Always       -       156461629
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       6
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       6
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 14279 (device log contains only the most recent five errors)
    CR = Command Register [HEX]
    FR = Features Register [HEX]
    SC = Sector Count Register [HEX]
    SN = Sector Number Register [HEX]
    CL = Cylinder Low Register [HEX]
    CH = Cylinder High Register [HEX]
    DH = Device/Head Register [HEX]
    DC = Device Command Register [HEX]
    ER = Error register [HEX]
    ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

Error 14279 occurred at disk power-on lifetime: 2688 hours (112 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 ff ff ff ef 00      03:22:41.556  READ DMA EXT
  27 00 00 00 00 00 e0 00      03:22:41.556  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 00      03:22:41.547  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00      03:22:41.540  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00      03:22:41.509  READ NATIVE MAX ADDRESS EXT

Error 14278 occurred at disk power-on lifetime: 2688 hours (112 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 ff ff ff ef 00      03:22:39.136  READ DMA EXT
  27 00 00 00 00 00 e0 00      03:22:39.136  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 00      03:22:39.127  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00      03:22:39.119  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00      03:22:39.084  READ NATIVE MAX ADDRESS EXT

Error 14277 occurred at disk power-on lifetime: 2688 hours (112 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 ff ff ff ef 00      03:22:36.712  READ DMA EXT
  27 00 00 00 00 00 e0 00      03:22:36.711  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 00      03:22:36.703  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00      03:22:36.698  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00      03:22:36.663  READ NATIVE MAX ADDRESS EXT

Error 14276 occurred at disk power-on lifetime: 2688 hours (112 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 ff ff ff ef 00      03:22:34.280  READ DMA EXT
  27 00 00 00 00 00 e0 00      03:22:34.279  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 00      03:22:34.271  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00      03:22:34.267  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00      03:22:34.231  READ NATIVE MAX ADDRESS EXT

Error 14275 occurred at disk power-on lifetime: 2688 hours (112 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 ff ff ff ef 00      03:22:31.852  READ DMA EXT
  27 00 00 00 00 00 e0 00      03:22:31.851  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 00      03:22:31.843  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00      03:22:31.835  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00      03:22:31.799  READ NATIVE MAX ADDRESS EXT

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       90%      2669         312581807
# 2  Extended offline    Completed: read failure       90%      2653         312581807
# 3  Short offline       Completed: read failure       90%      2652         260604486
# 4  Extended offline    Completed: read failure       90%      2651         312581807
# 5  Short offline       Completed: read failure       90%      2644         312581807
# 6  Short offline       Completed: read failure       90%      2643         312581807
# 7  Conveyance offline  Completed: read failure       90%      2643         312581807
# 8  Short offline       Completed: read failure       90%      2643         312581807
# 9  Short offline       Aborted by host               90%      2643         -
#10  Short offline       Completed: read failure       90%      2641         312581807
#11  Short offline       Completed: read failure       90%      2641         312581807
#12  Short offline       Completed: read failure       90%      2641         312581807
#13  Short offline       Completed: read failure       90%      2641         312581807
#14  Short offline       Completed: read failure       90%      2641         312581807
#15  Short offline       Completed: read failure       90%      2641         312581807
#16  Extended offline    Completed: read failure       90%      2641         312581807
#17  Extended offline    Completed: read failure       90%      2641         312581807

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

```This should give a fairly good overview of the problem. I might mention that I'm running Ubuntu 10.04, Netbook Edition, on an Asus EEE 1000HE. The problem is, as earlier stated, not unique to Ubuntu, but problematic in BackTrack 4 as well. Windows seems to have no issues with it. So far I have reformatted the former BackTrack partition (sda6) as well as the swap (sda7) in an early desperate attempt to fix the issue. It probably solved some issues, but the main problem is still there.

All and any help would be greatly appreciated.

---

### Post by nixpix on 2010-05-21
Update: Just realized that /dev/sda5 was not hidden a few days ago. That's the partition to which I back-uped my home-folder from BackTrack. Someone mentioned a broken MBR to me. Is the MBR located in the last few sectors of the disk? Any other ideas would be greatly appriciated.

---

### Post by nixpix on 2010-05-24
Okay, the MBR seems to not be located there. Helpful people in #ubuntu suggested that I comment out different file-systems in my boot file. It seems, however, that the only partitons mentioned in my fstab is the root-partition and the swap. Are there other boot-files that I am unaware of? What other solutions could there be?

---

### Post by dino99 on 2010-05-24
some checkings:

sudo apt-get install -f
sudo dpkg --configure -a

need to only have grub-pc and grub-common installed (remove menu.lst)
sudo grub-mkconfig
sudo update-grub

to easily manage your devices and partitions, install mountmanager and set your prefs

force a fsck at next boot:
sudo shutdown -F -r now

---

### Post by nixpix on 2010-05-24
Did the first two, seemed to not be any problems there.

Do I need to remove menu.lst manually, or did the two grub-commands do that automatically? If so, where is it located?

Was there a need for any further action on my part for the fsck to take place? The dmesg-log doesn't seem to have changed after I rebooted using the -F flag, as far as I can tell.

---

