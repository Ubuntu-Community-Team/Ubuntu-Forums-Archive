---
title: "Ubuntu 9.10 problems with net"
date: 2010-03-10
forum: Hardware
---

### Post by playcat on 2010-03-10
Hello everyone,

I'm unable to go online using laptop with ubuntu 9.10.

It doesn't matter if I try over wlan or ethernet, it's always the same. I think it started when I upgraded from 9.04 to 9.10 recently, but I can't be sure because I didn't use it for a while.

I need to add here that I had problems (long time to connect) via wless on 9.04, but it still worked.

My laptopt model is HP 6735s.

Here is the output of my dmesg:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-16-generic-pae (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #53-Ubuntu SMP Tue Dec 8 05:20:21 UTC 2009 (Ubuntu 2.6.31-16.53-generic-pae)
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
[    0.000000]  BIOS-e820: 00000000000ef000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000acb70000 (usable)
[    0.000000]  BIOS-e820: 00000000acb70000 - 00000000acb80000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000acb80000 - 00000000afd4f000 (usable)
[    0.000000]  BIOS-e820: 00000000afd4f000 - 00000000afdcf000 (reserved)
[    0.000000]  BIOS-e820: 00000000afdcf000 - 00000000afecf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000afecf000 - 00000000afeff000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000afeff000 - 00000000aff00000 (usable)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000feb00000 - 00000000feb01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 base 0080000000 mask FFE0000000 write-back
[    0.000000]   2 base 00A0000000 mask FFF0000000 write-back
[    0.000000]   3 base 0100000000 mask FFC0000000 write-back
[    0.000000]   4 base 00FFE00000 mask FFFFE00000 write-protect
[    0.000000]   5 base 00FFF40000 mask FFFFFF0000 write-protect
[    0.000000]   6 base 00ACB70000 mask FFFFFF0000 uncachable
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000140000000 aka 5120M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000ef000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000acb70000 (usable)
[    0.000000]  modified: 00000000acb70000 - 00000000acb80000 (ACPI NVS)
[    0.000000]  modified: 00000000acb80000 - 00000000afd4f000 (usable)
[    0.000000]  modified: 00000000afd4f000 - 00000000afdcf000 (reserved)
[    0.000000]  modified: 00000000afdcf000 - 00000000afecf000 (ACPI NVS)
[    0.000000]  modified: 00000000afecf000 - 00000000afeff000 (ACPI data)
[    0.000000]  modified: 00000000afeff000 - 00000000aff00000 (usable)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000feb00000 - 00000000feb01000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000379fe000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037800000 page 2M
[    0.000000]  0037800000 - 00379fe000 page 4k
[    0.000000] kernel direct mapping tables up to 379fe000 @ 7000-d000
[    0.000000] RAMDISK: 3789f000 - 37fef1c4
[    0.000000] Allocated new RAMDISK: 008b5000 - 010051c4
[    0.000000] Move RAMDISK from 000000003789f000 - 0000000037fef1c3 to 008b5000 - 010051c3
[    0.000000] ACPI: RSDP 000f68c0 00014 (v00 HP    )
[    0.000000] ACPI: RSDT afefe038 00038 (v01 HPQOEM SLIC-MPC 00000003      01000013)
[    0.000000] ACPI: FACP afefd000 00074 (v01 HP     0944     00000003 HP   00000001)
[    0.000000] ACPI: DSDT afee3000 164D6 (v01 HP     0944     00000001 HP   00000001)
[    0.000000] ACPI: FACS afea1000 00040
[    0.000000] ACPI: APIC afefc000 00084 (v01 HP     0944     00000001 HP   00000001)
[    0.000000] ACPI: MCFG afefb000 0003C (v01 HP     0944     00000001 HP   00000001)
[    0.000000] ACPI: HPET afee1000 00038 (v01 HP     0944     00000001 HP   00000001)
[    0.000000] ACPI: SSDT afee0000 00386 (v01 AMD    PowerNow 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 4230MB HIGHMEM available.
[    0.000000] 889MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 379fe000
[    0.000000]   low ram: 0 - 379fe000
[    0.000000]   node 0 low ram: 00000000 - 379fe000
[    0.000000]   node 0 bootmap 00009000 - 0000ff40
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00379fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008ad9a0]    TEXT DATA BSS ==> [0000100000 - 00008ad9a0]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [00008ae000 - 00008b418c]              BRK ==> [00008ae000 - 00008b418c]
[    0.000000]   #6 [0000007000 - 0000009000]          PGTABLE ==> [0000007000 - 0000009000]
[    0.000000]   #7 [00008b5000 - 00010051c4]      NEW RAMDISK ==> [00008b5000 - 00010051c4]
[    0.000000]   #8 [0000009000 - 0000010000]          BOOTMAP ==> [0000009000 - 0000010000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000379fe
[    0.000000]   HighMem  0x000379fe -> 0x00140000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[6] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000acb70
[    0.000000]     0: 0x000acb80 -> 0x000afd4f
[    0.000000]     0: 0x000afeff -> 0x000aff00
[    0.000000]     0: 0x00100000 -> 0x00140000
[    0.000000] On node 0 totalpages: 982235
[    0.000000] free_area_init_node: node 0, pgdat c078bd20, node_mem_map c1006000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1748 pages used for memmap
[    0.000000]   Normal zone: 221994 pages, LIFO batch:31
[    0.000000]   HighMem zone: 8461 pages used for memmap
[    0.000000]   HighMem zone: 746037 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x43538301 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000ef000
[    0.000000] PM: Registered nosave memory: 00000000000ef000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at aff00000 (gap: aff00000:30100000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c3816000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 971994
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-16-generic-pae root=UUID=7c65c223-4b32-418b-a1ab-0a5968acd41b ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 26214400 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000379fe:00140000)
[    0.000000] Memory: 3845008k/5242880k available (4590k kernel code, 83056k reserved, 2147k data, 544k init, 3017992k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xffa00000 - 0xffc00000   (2048 kB)
[    0.000000]     vmalloc : 0xf81fe000 - 0xff9fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf79fe000   ( 889 MB)
[    0.000000]       .init : 0xc0795000 - 0xc081d000   ( 544 kB)
[    0.000000]       .data : 0xc057b994 - 0xc07947a8   (2147 kB)
[    0.000000]       .text : 0xc0100000 - 0xc057b994   (4590 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:440
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1999.921 MHz processor.
[    0.000011] spurious 8259A interrupt: IRQ7.
[    0.001089] Console: colour VGA+ 80x25
[    0.001092] console [tty0] enabled
[    0.001941] hpet clockevent registered
[    0.001959]   alloc irq_desc for 24 on node 0
[    0.001962]   alloc kstat_irqs on node 0
[    0.001970] HPET: 4 timers in total, 1 timers will be used for per-cpu timer
[    0.004009] Calibrating delay loop (skipped), value calculated using timer frequency.. 3999.84 BogoMIPS (lpj=7999684)
[    0.004034] Security Framework initialized
[    0.004052] AppArmor: AppArmor initialized
[    0.004061] Mount-cache hash table entries: 512
[    0.004190] Initializing cgroup subsys ns
[    0.004194] Initializing cgroup subsys cpuacct
[    0.004198] Initializing cgroup subsys memory
[    0.004205] Initializing cgroup subsys freezer
[    0.004207] Initializing cgroup subsys net_cls
[    0.004221] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004224] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004226] CPU: Physical Processor ID: 0
[    0.004228] CPU: Processor Core ID: 0
[    0.004232] mce: CPU supports 5 MCE banks
[    0.004242] using C1E aware idle routine
[    0.004249] Performance Counters: AMD PMU driver.
[    0.004253] ... version:                 0
[    0.004255] ... bit width:               48
[    0.004257] ... generic counters:        4
[    0.004259] ... value mask:              0000ffffffffffff
[    0.004261] ... max period:              00007fffffffffff
[    0.004263] ... fixed-purpose counters:  0
[    0.004265] ... counter mask:            000000000000000f
[    0.004269] Checking 'hlt' instruction... OK.
[    0.023054] ACPI: Core revision 20090521
[    0.044475] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.086791] CPU0: AMD Turion(tm)X2 Dual Core Mobile RM-70 stepping 01
[    0.088001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3990.08 BogoMIPS (lpj=7980163)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] mce: CPU supports 5 MCE banks
[    0.004000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.172600] CPU1: AMD Turion(tm)X2 Dual Core Mobile RM-70 stepping 01
[    0.172644] checking TSC synchronization [CPU#0 -> CPU#1]:
[    0.176001] Measured 16883800 cycles TSC warp between CPUs, turning off TSC clock.
[    0.176001] Marking TSC unstable due to check_tsc_sync_source failed
[    0.176015] Brought up 2 CPUs
[    0.176018] Total of 2 processors activated (7989.92 BogoMIPS).
[    0.176094] CPU0 attaching sched-domain:
[    0.176098]  domain 0: span 0-1 level MC
[    0.176101]   groups: 0 1
[    0.176107] CPU1 attaching sched-domain:
[    0.176109]  domain 0: span 0-1 level MC
[    0.176111]   groups: 1 0
[    0.176183] HP Compaq Laptop series board detected. Selecting BIOS-method for reboots.
[    0.176183] Booting paravirtualized kernel on bare hardware
[    0.176272] regulator: core version 0.5
[    0.176272] Time: 15:38:42  Date: 03/10/10
[    0.176272] NET: Registered protocol family 16
[    0.176272] EISA bus registered
[    0.176272] ACPI: bus type pci registered
[    0.176304] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.176308] PCI: MCFG area at e0000000 reserved in E820
[    0.176310] PCI: Using MMCONFIG for extended config space
[    0.176313] PCI: Using configuration type 1 for base access
[    0.177221] bio: create slab <bio-0> at 0
[    0.180478] ACPI: EC: Look up EC in DSDT
[    0.828022] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.880201] ACPI: Interpreter enabled
[    0.880207] ACPI: (supports S0 S3 S4 S5)
[    0.880235] ACPI: Using IOAPIC for interrupt routing
[    0.897698] ACPI: EC: GPE = 0x11, I/O: command/status = 0x66, data = 0x62
[    0.897702] ACPI: EC: driver started in interrupt mode
[    0.897773] ACPI: Power Resource [APPR] (off)
[    0.897859] ACPI: Power Resource [PFN0] (off)
[    0.897936] ACPI: Power Resource [PFN1] (off)
[    0.898014] ACPI: Power Resource [PFN2] (off)
[    0.898094] ACPI: Power Resource [PFN3] (off)
[    0.898419] ACPI: No dock devices found.
[    0.898614] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.898829] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    0.898834] pci 0000:00:04.0: PME# disabled
[    0.898918] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.898922] pci 0000:00:07.0: PME# disabled
[    0.899008] pci 0000:00:09.0: PME# supported from D0 D3hot D3cold
[    0.899011] pci 0000:00:09.0: PME# disabled
[    0.899110] pci 0000:00:11.0: reg 10 io port: [0x6018-0x601f]
[    0.899119] pci 0000:00:11.0: reg 14 io port: [0x6024-0x6027]
[    0.899128] pci 0000:00:11.0: reg 18 io port: [0x6010-0x6017]
[    0.899136] pci 0000:00:11.0: reg 1c io port: [0x6020-0x6023]
[    0.899145] pci 0000:00:11.0: reg 20 io port: [0x6000-0x600f]
[    0.899154] pci 0000:00:11.0: reg 24 32bit mmio: [0xd4409000-0xd44093ff]
[    0.899176] pci 0000:00:11.0: set SATA to AHCI mode
[    0.899230] pci 0000:00:12.0: reg 10 32bit mmio: [0xd4408000-0xd4408fff]
[    0.899297] pci 0000:00:12.1: reg 10 32bit mmio: [0xd4407000-0xd4407fff]
[    0.899385] pci 0000:00:12.2: reg 10 32bit mmio: [0xd4409500-0xd44095ff]
[    0.899447] pci 0000:00:12.2: supports D1 D2
[    0.899450] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.899455] pci 0000:00:12.2: PME# disabled
[    0.899493] pci 0000:00:13.0: reg 10 32bit mmio: [0xd4406000-0xd4406fff]
[    0.899559] pci 0000:00:13.1: reg 10 32bit mmio: [0xd4405000-0xd4405fff]
[    0.899646] pci 0000:00:13.2: reg 10 32bit mmio: [0xd4409400-0xd44094ff]
[    0.899708] pci 0000:00:13.2: supports D1 D2
[    0.899711] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.899716] pci 0000:00:13.2: PME# disabled
[    0.899864] pci 0000:00:14.2: reg 10 64bit mmio: [0xd4400000-0xd4403fff]
[    0.899916] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.899921] pci 0000:00:14.2: PME# disabled
[    0.900065] pci 0000:00:14.5: reg 10 32bit mmio: [0xd4404000-0xd4404fff]
[    0.900329] pci 0000:01:05.0: reg 10 32bit mmio: [0xc0000000-0xcfffffff]
[    0.900335] pci 0000:01:05.0: reg 14 io port: [0x5000-0x50ff]
[    0.900340] pci 0000:01:05.0: reg 18 32bit mmio: [0xd4300000-0xd430ffff]
[    0.900351] pci 0000:01:05.0: reg 24 32bit mmio: [0xd4200000-0xd42fffff]
[    0.900369] pci 0000:01:05.0: supports D1 D2
[    0.900455] pci 0000:00:01.0: bridge io port: [0x5000-0x5fff]
[    0.900459] pci 0000:00:01.0: bridge 32bit mmio: [0xd4200000-0xd43fffff]
[    0.900464] pci 0000:00:01.0: bridge 64bit mmio pref: [0xc0000000-0xcfffffff]
[    0.900538] pci 0000:02:00.0: reg 10 64bit mmio: [0xd3100000-0xd3103fff]
[    0.900566] pci 0000:02:00.0: reg 18 io port: [0x3000-0x30ff]
[    0.900652] pci 0000:02:00.0: supports D1 D2
[    0.900654] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.900660] pci 0000:02:00.0: PME# disabled
[    0.900782] pci 0000:00:04.0: bridge io port: [0x3000-0x4fff]
[    0.900786] pci 0000:00:04.0: bridge 32bit mmio: [0xd3100000-0xd41fffff]
[    0.900791] pci 0000:00:04.0: bridge 64bit mmio pref: [0xd0000000-0xd0ffffff]
[    0.900847] pci 0000:00:07.0: bridge io port: [0x2000-0x2fff]
[    0.900851] pci 0000:00:07.0: bridge 32bit mmio: [0xd2100000-0xd30fffff]
[    0.900856] pci 0000:00:07.0: bridge 64bit mmio pref: [0xd1000000-0xd1ffffff]
[    0.900946] pci 0000:06:00.0: reg 10 64bit mmio: [0xd2000000-0xd2003fff]
[    0.901011] pci 0000:06:00.0: supports D1 D2
[    0.901119] pci 0000:00:09.0: bridge 32bit mmio: [0xd2000000-0xd20fffff]
[    0.901188] pci 0000:00:14.4: transparent bridge
[    0.901193] pci 0000:00:14.4: bridge io port: [0x1000-0x1fff]
[    0.901220] pci_bus 0000:00: on NUMA node 0
[    0.901227] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.901336] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    0.901423] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[    0.901526] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB9_._PRT]
[    0.901622] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB7_._PRT]
[    0.901807] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.915863] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.916079] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.916281] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.916482] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.916686] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.916888] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.917089] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.917290] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.917521] SCSI subsystem initialized
[    0.917544] libata version 3.00 loaded.
[    0.917544] usbcore: registered new interface driver usbfs
[    0.917544] usbcore: registered new interface driver hub
[    0.917544] usbcore: registered new device driver usb
[    0.917544] ACPI: WMI: Mapper loaded
[    0.917544] PCI: Using ACPI for IRQ routing
[    0.928010] Bluetooth: Core ver 2.15
[    0.928017] NET: Registered protocol family 31
[    0.928019] Bluetooth: HCI device and connection manager initialized
[    0.928022] Bluetooth: HCI socket layer initialized
[    0.928025] NetLabel: Initializing
[    0.928027] NetLabel:  domain hash size = 128
[    0.928029] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.928043] NetLabel:  unlabeled traffic allowed by default
[    0.928148] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 24, 0
[    0.928154] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.936056] hpet: hpet2 irq 24 for MSI
[    0.940024] Switched to high resolution mode on CPU 0
[    0.940677] Switched to high resolution mode on CPU 1
[    0.948553] pnp: PnP ACPI init
[    0.948571] ACPI: bus type pnp registered
[    0.950657]   alloc irq_desc for 23 on node -1
[    0.950660]   alloc kstat_irqs on node -1
[    0.951670] pnp: PnP ACPI: found 11 devices
[    0.951672] ACPI: ACPI bus type pnp unregistered
[    0.951676] PnPBIOS: Disabled by ACPI PNP
[    0.951689] system 00:04: ioport range 0x400-0x4cf has been reserved
[    0.951693] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[    0.951696] system 00:04: ioport range 0x4d6-0x4d6 has been reserved
[    0.951699] system 00:04: ioport range 0x680-0x6ff has been reserved
[    0.951702] system 00:04: ioport range 0x77a-0x77a has been reserved
[    0.951706] system 00:04: ioport range 0xc00-0xc01 has been reserved
[    0.951709] system 00:04: ioport range 0xc14-0xc14 has been reserved
[    0.951712] system 00:04: ioport range 0xc50-0xc52 has been reserved
[    0.951715] system 00:04: ioport range 0xc6c-0xc6c has been reserved
[    0.951719] system 00:04: ioport range 0xc6f-0xc6f has been reserved
[    0.951722] system 00:04: ioport range 0xcd0-0xcdb has been reserved
[    0.951725] system 00:04: ioport range 0x220-0x227 has been reserved
[    0.951728] system 00:04: ioport range 0x260-0x273 has been reserved
[    0.951731] system 00:04: ioport range 0x800-0x800 has been reserved
[    0.951735] system 00:04: ioport range 0x804-0x804 has been reserved
[    0.951738] system 00:04: ioport range 0x87f-0x87f has been reserved
[    0.951741] system 00:04: ioport range 0xcdc-0xcdf has been reserved
[    0.951745] system 00:04: ioport range 0xb00-0xb0f has been reserved
[    0.951748] system 00:04: ioport range 0xb20-0xb3f has been reserved
[    0.951751] system 00:04: ioport range 0x200-0x27f could not be reserved
[    0.951758] system 00:05: iomem range 0x0-0x9ffff could not be reserved
[    0.951761] system 00:05: iomem range 0xec000-0xfffff could not be reserved
[    0.951765] system 00:05: iomem range 0x100000-0xbfffffff could not be reserved
[    0.951769] system 00:05: iomem range 0xe0000000-0xefffffff has been reserved
[    0.951772] system 00:05: iomem range 0xfeb00000-0xfeb00fff has been reserved
[    0.951776] system 00:05: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.951779] system 00:05: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.951783] system 00:05: iomem range 0xffe00000-0xffffffff has been reserved
[    0.986829] AppArmor: AppArmor Filesystem Enabled
[    0.986907] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.986911] pci 0000:00:01.0:   IO window: 0x5000-0x5fff
[    0.986916] pci 0000:00:01.0:   MEM window: 0xd4200000-0xd43fffff
[    0.986920] pci 0000:00:01.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff
[    0.986927] pci 0000:00:04.0: PCI bridge, secondary bus 0000:02
[    0.986930] pci 0000:00:04.0:   IO window: 0x3000-0x4fff
[    0.986935] pci 0000:00:04.0:   MEM window: 0xd3100000-0xd41fffff
[    0.986940] pci 0000:00:04.0:   PREFETCH window: 0x000000d0000000-0x000000d0ffffff
[    0.986945] pci 0000:00:07.0: PCI bridge, secondary bus 0000:03
[    0.986949] pci 0000:00:07.0:   IO window: 0x2000-0x2fff
[    0.986954] pci 0000:00:07.0:   MEM window: 0xd2100000-0xd30fffff
[    0.986958] pci 0000:00:07.0:   PREFETCH window: 0x000000d1000000-0x000000d1ffffff
[    0.986964] pci 0000:00:09.0: PCI bridge, secondary bus 0000:06
[    0.986966] pci 0000:00:09.0:   IO window: disabled
[    0.986971] pci 0000:00:09.0:   MEM window: 0xd2000000-0xd20fffff
[    0.986975] pci 0000:00:09.0:   PREFETCH window: disabled
[    0.986979] pci 0000:00:14.4: PCI bridge, secondary bus 0000:80
[    0.987017] pci 0000:00:14.4:   IO window: 0x1000-0x1fff
[    0.987023] pci 0000:00:14.4:   MEM window: disabled
[    0.987028] pci 0000:00:14.4:   PREFETCH window: disabled
[    0.987040] pci 0000:00:01.0: setting latency timer to 64
[    0.987048] pci 0000:00:04.0: setting latency timer to 64
[    0.987055] pci 0000:00:07.0: setting latency timer to 64
[    0.987062] pci 0000:00:09.0: setting latency timer to 64
[    0.987072] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.987075] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.987079] pci_bus 0000:01: resource 0 io:  [0x5000-0x5fff]
[    0.987082] pci_bus 0000:01: resource 1 mem: [0xd4200000-0xd43fffff]
[    0.987085] pci_bus 0000:01: resource 2 pref mem [0xc0000000-0xcfffffff]
[    0.987088] pci_bus 0000:02: resource 0 io:  [0x3000-0x4fff]
[    0.987091] pci_bus 0000:02: resource 1 mem: [0xd3100000-0xd41fffff]
[    0.987094] pci_bus 0000:02: resource 2 pref mem [0xd0000000-0xd0ffffff]
[    0.987097] pci_bus 0000:03: resource 0 io:  [0x2000-0x2fff]
[    0.987100] pci_bus 0000:03: resource 1 mem: [0xd2100000-0xd30fffff]
[    0.987103] pci_bus 0000:03: resource 2 pref mem [0xd1000000-0xd1ffffff]
[    0.987106] pci_bus 0000:06: resource 1 mem: [0xd2000000-0xd20fffff]
[    0.987109] pci_bus 0000:80: resource 0 io:  [0x1000-0x1fff]
[    0.987112] pci_bus 0000:80: resource 3 io:  [0x00-0xffff]
[    0.987115] pci_bus 0000:80: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.987152] NET: Registered protocol family 2
[    0.987253] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.987594] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.988230] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.988598] TCP: Hash tables configured (established 131072 bind 65536)
[    0.988601] TCP reno registered
[    0.988699] NET: Registered protocol family 1
[    0.988769] Trying to unpack rootfs image as initramfs...
[    1.201148] Freeing initrd memory: 7488k freed
[    1.206201] cpufreq-nforce2: No nForce2 chipset.
[    1.206232] Scanning for low memory corruption every 60 seconds
[    1.206334] audit: initializing netlink socket (disabled)
[    1.206350] type=2000 audit(1268235523.204:1): initialized
[    1.216018] highmem bounce pool size: 64 pages
[    1.216025] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.217559] VFS: Disk quotas dquot_6.5.2
[    1.217618] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.218188] fuse init (API version 7.12)
[    1.218266] msgmni has been set to 1631
[    1.219003] alg: No test for stdrng (krng)
[    1.219017] io scheduler noop registered
[    1.219020] io scheduler anticipatory registered
[    1.219023] io scheduler deadline registered
[    1.219065] io scheduler cfq registered (default)
[    1.219200] pci 0000:01:05.0: Boot video device
[    1.219331]   alloc irq_desc for 25 on node -1
[    1.219333]   alloc kstat_irqs on node -1
[    1.219344] pcieport-driver 0000:00:04.0: irq 25 for MSI/MSI-X
[    1.219352] pcieport-driver 0000:00:04.0: setting latency timer to 64
[    1.219455]   alloc irq_desc for 26 on node -1
[    1.219457]   alloc kstat_irqs on node -1
[    1.219463] pcieport-driver 0000:00:07.0: irq 26 for MSI/MSI-X
[    1.219470] pcieport-driver 0000:00:07.0: setting latency timer to 64
[    1.219580]   alloc irq_desc for 27 on node -1
[    1.219582]   alloc kstat_irqs on node -1
[    1.219588] pcieport-driver 0000:00:09.0: irq 27 for MSI/MSI-X
[    1.219595] pcieport-driver 0000:00:09.0: setting latency timer to 64
[    1.219671] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.219738] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.226424] ACPI: AC Adapter [AC] (on-line)
[    1.226489] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.226493] ACPI: Power Button [PWRF]
[    1.226588] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    1.226591] ACPI: Sleep Button [SLPB]
[    1.226631] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    1.226742] ACPI: Lid Switch [LID]
[    1.226943] fan PNP0C0B:00: registered as cooling_device0
[    1.226949] ACPI: Fan [FAN0] (off)
[    1.227111] fan PNP0C0B:01: registered as cooling_device1
[    1.227116] ACPI: Fan [FAN1] (off)
[    1.227278] fan PNP0C0B:02: registered as cooling_device2
[    1.227283] ACPI: Fan [FAN2] (off)
[    1.227445] fan PNP0C0B:03: registered as cooling_device3
[    1.227453] ACPI: Fan [FAN3] (off)
[    1.227887] processor LNXCPU:00: registered as cooling_device4
[    1.227893] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.227946] processor LNXCPU:01: registered as cooling_device5
[    1.242644] thermal LNXTHERM:01: registered as thermal_zone0
[    1.242654] ACPI: Thermal Zone [CPUZ] (68 C)
[    1.242735] isapnp: Scanning for PnP cards...
[    1.399813] ACPI: Battery Slot [BAT0] (battery present)
[    1.625853] isapnp: No Plug & Play device found
[    1.627187] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.628441] brd: module loaded
[    1.628946] loop: module loaded
[    1.629027] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.629098] ahci 0000:00:11.0: version 3.0
[    1.629148]   alloc irq_desc for 20 on node -1
[    1.629155]   alloc kstat_irqs on node -1
[    1.629163] ahci 0000:00:11.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.629325] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.629329] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pio 
[    1.629918] scsi0 : ahci
[    1.630061] scsi1 : ahci
[    1.630136] scsi2 : ahci
[    1.630379] scsi3 : ahci
[    1.630534] ata1: SATA max UDMA/133 abar m1024@0xd4409000 port 0xd4409100 irq 20
[    1.630539] ata2: SATA max UDMA/133 abar m1024@0xd4409000 port 0xd4409180 irq 20
[    1.630543] ata3: SATA max UDMA/133 abar m1024@0xd4409000 port 0xd4409200 irq 20
[    1.630547] ata4: SATA max UDMA/133 abar m1024@0xd4409000 port 0xd4409280 irq 20
[    1.631462] Fixed MDIO Bus: probed
[    1.631497] PPP generic driver version 2.4.2
[    1.631614] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.631670]   alloc irq_desc for 17 on node -1
[    1.631673]   alloc kstat_irqs on node -1
[    1.631679] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.631699] ehci_hcd 0000:00:12.2: setting latency timer to 64
[    1.631704] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    1.631766] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.631832] ehci_hcd 0000:00:12.2: applying AMD SB600/SB700 USB freeze workaround
[    1.631854] ehci_hcd 0000:00:12.2: debug port 1
[    1.631871] ehci_hcd 0000:00:12.2: irq 17, io mem 0xd4409500
[    1.640548] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.640636] usb usb1: configuration #1 chosen from 1 choice
[    1.640666] hub 1-0:1.0: USB hub found
[    1.640676] hub 1-0:1.0: 6 ports detected
[    1.640771]   alloc irq_desc for 19 on node -1
[    1.640774]   alloc kstat_irqs on node -1
[    1.640778] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.640789] ehci_hcd 0000:00:13.2: setting latency timer to 64
[    1.640793] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.640825] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.640847] ehci_hcd 0000:00:13.2: applying AMD SB600/SB700 USB freeze workaround
[    1.640866] ehci_hcd 0000:00:13.2: debug port 1
[    1.640881] ehci_hcd 0000:00:13.2: irq 19, io mem 0xd4409400
[    1.652055] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.652125] usb usb2: configuration #1 chosen from 1 choice
[    1.652151] hub 2-0:1.0: USB hub found
[    1.652158] hub 2-0:1.0: 6 ports detected
[    1.652254] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.652302]   alloc irq_desc for 16 on node -1
[    1.652304]   alloc kstat_irqs on node -1
[    1.652309] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.652319] ohci_hcd 0000:00:12.0: setting latency timer to 64
[    1.652323] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.652356] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.652426] ohci_hcd 0000:00:12.0: irq 16, io mem 0xd4408000
[    1.712087] usb usb3: configuration #1 chosen from 1 choice
[    1.712113] hub 3-0:1.0: USB hub found
[    1.712157] hub 3-0:1.0: 3 ports detected
[    1.712206] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.712216] ohci_hcd 0000:00:12.1: setting latency timer to 64
[    1.712220] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    1.712252] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    1.712268] ohci_hcd 0000:00:12.1: irq 16, io mem 0xd4407000
[    1.768088] usb usb4: configuration #1 chosen from 1 choice
[    1.768114] hub 4-0:1.0: USB hub found
[    1.768157] hub 4-0:1.0: 3 ports detected
[    1.768208] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.768218] ohci_hcd 0000:00:13.0: setting latency timer to 64
[    1.768222] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.768257] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.768316] ohci_hcd 0000:00:13.0: irq 17, io mem 0xd4406000
[    1.824088] usb usb5: configuration #1 chosen from 1 choice
[    1.824114] hub 5-0:1.0: USB hub found
[    1.824158] hub 5-0:1.0: 3 ports detected
[    1.824208] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.824218] ohci_hcd 0000:00:13.1: setting latency timer to 64
[    1.824222] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    1.824252] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    1.824268] ohci_hcd 0000:00:13.1: irq 17, io mem 0xd4405000
[    1.880105] usb usb6: configuration #1 chosen from 1 choice
[    1.880132] hub 6-0:1.0: USB hub found
[    1.880172] hub 6-0:1.0: 3 ports detected
[    1.880232]   alloc irq_desc for 18 on node -1
[    1.880234]   alloc kstat_irqs on node -1
[    1.880239] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.880249] ohci_hcd 0000:00:14.5: setting latency timer to 64
[    1.880253] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    1.880284] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    1.880306] ohci_hcd 0000:00:14.5: irq 18, io mem 0xd4404000
[    1.936595] usb usb7: configuration #1 chosen from 1 choice
[    1.936626] hub 7-0:1.0: USB hub found
[    1.936670] hub 7-0:1.0: 2 ports detected
[    1.936722] uhci_hcd: USB Universal Host Controller Interface driver
[    1.936805] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.939074] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.940151] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.940158] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.940162] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.940166] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.940169] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.940235] mice: PS/2 mouse device common for all mice
[    1.940350] rtc_cmos 00:06: RTC can wake from S4
[    1.940385] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.940412] rtc0: alarms up to one day, 114 bytes nvram, hpet irqs
[    1.940563] device-mapper: uevent: version 1.0.3
[    1.940660] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.941050] device-mapper: multipath: version 1.1.0 loaded
[    1.941053] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.941360] EISA: Probing bus 0 at eisa.0
[    1.941402] Cannot allocate resource for EISA slot 1
[    1.941405] Cannot allocate resource for EISA slot 2
[    1.941407] Cannot allocate resource for EISA slot 3
[    1.941410] Cannot allocate resource for EISA slot 4
[    1.941412] Cannot allocate resource for EISA slot 5
[    1.941415] Cannot allocate resource for EISA slot 6
[    1.941426] EISA: Detected 0 cards.
[    1.941916] cpuidle: using governor ladder
[    1.941919] cpuidle: using governor menu
[    1.942424] TCP cubic registered
[    1.942574] NET: Registered protocol family 10
[    1.943028] lo: Disabled Privacy Extensions
[    1.943346] NET: Registered protocol family 17
[    1.943364] Bluetooth: L2CAP ver 2.13
[    1.943366] Bluetooth: L2CAP socket layer initialized
[    1.943369] Bluetooth: SCO (Voice Link) ver 0.6
[    1.943371] Bluetooth: SCO socket layer initialized
[    1.943449] Bluetooth: RFCOMM TTY layer initialized
[    1.943452] Bluetooth: RFCOMM socket layer initialized
[    1.943454] Bluetooth: RFCOMM ver 1.11
[    1.943528] powernow-k8: Found 1 AMD Turion(tm)X2 Dual Core Mobile RM-70 processors (2 cpu cores) (version 2.20.00)
[    1.943573] powernow-k8:    0 : pstate 0 (2000 MHz)
[    1.943575] powernow-k8:    1 : pstate 1 (1000 MHz)
[    1.943578] powernow-k8:    2 : pstate 2 (500 MHz)
[    1.945001] Using IPI No-Shortcut mode
[    1.945065] PM: Resume from disk failed.
[    1.945078] registered taskstats version 1
[    1.945213]   Magic number: 2:902:638
[    1.945363] rtc_cmos 00:06: setting system clock to 2010-03-10 15:38:44 UTC (1268235524)
[    1.945367] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.945369] EDD information not available.
[    1.948076] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.949369] ata1.00: ATA-8: WDC WD2500BEVT-60ZCT1, 13.01A13, max UDMA/100
[    1.949373] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.950811] ata1.00: configured for UDMA/100
[    1.956086] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.956114] ata3: SATA link down (SStatus 0 SControl 300)
[    1.956143] ata4: SATA link down (SStatus 0 SControl 300)
[    1.962467] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.964682] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500BEVT-6 13.0 PQ: 0 ANSI: 5
[    1.964818] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.964870] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.964921] sd 0:0:0:0: [sda] Write Protect is off
[    1.964924] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.964950] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.965083]  sda:
[    2.003353] ata2.00: ATAPI: HL-DT-ST DVDRAM GSA-T50L, SC04, max UDMA/100
[    2.008148] ata2.00: configured for UDMA/100
[    2.017048]  sda1 sda2 < sda5 sda6 sda7 sda8 >
[    2.076573] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.139118] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T50L  SC04 PQ: 0 ANSI: 5
[    2.160065] usb 3-1: new low speed USB device using ohci_hcd and address 2
[    2.329166] usb 3-1: configuration #1 chosen from 1 choice
[    2.440051] usb 2-2: new high speed USB device using ehci_hcd and address 2
[    2.463985] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.463989] Uniform CD-ROM driver Revision: 3.20
[    2.464065] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.464108] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.464276] Freeing unused kernel memory: 544k freed
[    2.464740] Write protecting the kernel text: 4592k
[    2.464915] Write protecting the kernel read-only data: 1836k
[    2.620000] usb 2-2: configuration #1 chosen from 1 choice
[    2.628911] sky2 driver version 1.23
[    2.629029] sky2 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.629080] sky2 0000:02:00.0: setting latency timer to 64
[    2.629150] sky2 0000:02:00.0: Yukon-2 FE+ chip revision 0
[    2.629864]   alloc irq_desc for 28 on node -1
[    2.629870]   alloc kstat_irqs on node -1
[    2.629906] sky2 0000:02:00.0: irq 28 for MSI/MSI-X
[    2.646855] sky2 eth0: addr 00:24:81:3a:11:7a
[    2.682116] acpi device:03: registered as cooling_device6
[    2.682653] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/device:02/input/input5
[    2.682696] ACPI: Video Device [IGFX] (multi-head: yes  rom: no  post: no)
[    2.715353] usbcore: registered new interface driver hiddev
[    2.722086] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1:1.0/input/input6
[    2.722179] generic-usb 0003:046D:C03E.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:12.0-1/input0
[    2.722203] usbcore: registered new interface driver usbhid
[    2.722207] usbhid: v2.6:USB HID core driver
[    2.996573] usb 6-3: new full speed USB device using ohci_hcd and address 2
[    3.178193] usb 6-3: configuration #1 chosen from 1 choice
[    3.961459] PM: Starting manual resume from disk
[    3.961464] PM: Resume from partition 8:6
[    3.961467] PM: Checking hibernation image.
[    3.961719] PM: Resume from disk failed.
[    3.971302] EXT4-fs (sda8): barriers enabled
[    3.999482] kjournald2 starting: pid 425, dev sda8:8, commit interval 5 seconds
[    3.999492] EXT4-fs (sda8): delayed allocation enabled
[    3.999496] EXT4-fs: file extents enabled
[    4.000025] EXT4-fs: mballoc enabled
[    4.000041] EXT4-fs (sda8): mounted filesystem with ordered data mode
[    4.576134] type=1505 audit(1268235527.127:2): operation="profile_load" pid=448 name=/usr/share/gdm/guest-session/Xsession
[    4.579213] type=1505 audit(1268235527.131:3): operation="profile_load" pid=449 name=/sbin/dhclient3
[    4.579523] type=1505 audit(1268235527.131:4): operation="profile_load" pid=449 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    4.579695] type=1505 audit(1268235527.131:5): operation="profile_load" pid=449 name=/usr/lib/connman/scripts/dhclient-script
[    4.631987] type=1505 audit(1268235527.185:6): operation="profile_load" pid=450 name=/usr/bin/evince
[    4.636977] type=1505 audit(1268235527.191:7): operation="profile_load" pid=450 name=/usr/bin/evince-previewer
[    4.639908] type=1505 audit(1268235527.191:8): operation="profile_load" pid=450 name=/usr/bin/evince-thumbnailer
[    4.661564] type=1505 audit(1268235527.215:9): operation="profile_load" pid=452 name=/usr/lib/cups/backend/cups-pdf
[   15.000086] Adding 1951856k swap on /dev/sda6.  Priority:-1 extents:1 across:1951856k 
[   15.009589] udev: starting version 147
[   15.124861] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   15.140294] shpchp 0000:00:01.0: HPC vendor_id 1022 device_id 9602 ss_vid 0 ss_did 0
[   15.140300] shpchp 0000:00:01.0: Cannot reserve MMIO region
[   15.140333] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.170334] lp: driver loaded but no devices found
[   15.186868] lib80211: common routines for IEEE802.11 drivers
[   15.186873] lib80211_crypt: registered algorithm 'NULL'
[   15.199720] Linux agpgart interface v0.103
[   15.201542] Bluetooth: Generic Bluetooth USB driver ver 0.5
[   15.201734] usbcore: registered new interface driver btusb
[   15.275678] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   15.275685] Disabling lock debugging due to kernel taint
[   15.317610] [fglrx] Maximum main memory to use for locked dma buffers: 3604 MBytes.
[   15.317641] [fglrx]   vendor: 1002 device: 9612 count: 1
[   15.317976] [fglrx] ioport: bar 1, base 0x5000, size: 0x100
[   15.317995] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   15.318001] pci 0000:01:05.0: setting latency timer to 64
[   15.318342] [fglrx] Kernel PAT support is enabled
[   15.318370] [fglrx] module loaded - fglrx 8.66.10 [Sep  3 2009] with 1 minors
[   15.330820] Linux video capture interface: v2.00
[   15.334190] uvcvideo: Found UVC 1.00 device CKF7063 (04f2:b083)
[   15.340246] ip_tables: (C) 2000-2006 Netfilter Core Team
[   15.370451] input: CKF7063 as /devices/pci0000:00/0000:00:13.2/usb2/2-2/2-2:1.0/input/input7
[   15.370511] usbcore: registered new interface driver uvcvideo
[   15.370515] USB Video Class driver (v0.1.0)
[   15.478295] wl 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.478306] wl 0000:06:00.0: setting latency timer to 64
[   15.493335] lis3lv02d: hardware type NC673x found.
[   15.494137] lis3lv02d: 1-byte sensor found
[   15.513814] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input8
[   15.513916] Registered led device: hp::hddprotect
[   15.513937] lis3lv02d driver loaded.
[   15.593413] HDA Intel 0000:00:14.2: power state changed by ACPI to D0
[   15.593441] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.701478] lib80211_crypt: registered algorithm 'TKIP'
[   15.701712] eth1: Broadcom BCM432b 802.11 Wireless Controller 5.10.91.9
[   15.858931] EXT4-fs (sda8): internal journal on sda8:8
[   15.923851] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04711/0x200000
[   15.964145] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input9
[   16.008835] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input10
[   16.192364] EXT4-fs (sda7): barriers enabled
[   16.203106] kjournald2 starting: pid 909, dev sda7:8, commit interval 5 seconds
[   16.203435] EXT4-fs (sda7): internal journal on sda7:8
[   16.203439] EXT4-fs (sda7): delayed allocation enabled
[   16.203442] EXT4-fs: file extents enabled
[   16.203700] EXT4-fs: mballoc enabled
[   16.203718] EXT4-fs (sda7): mounted filesystem with ordered data mode
[   16.215570] sky2 eth0: enabling interface
[   16.215838] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.325572] __ratelimit: 6 callbacks suppressed
[   16.325578] type=1505 audit(1268231938.879:12): operation="profile_replace" pid=981 name=/usr/share/gdm/guest-session/Xsession
[   16.345705] type=1505 audit(1268231938.899:13): operation="profile_replace" pid=982 name=/sbin/dhclient3
[   16.346059] type=1505 audit(1268231938.899:14): operation="profile_replace" pid=982 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   16.346231] type=1505 audit(1268231938.899:15): operation="profile_replace" pid=982 name=/usr/lib/connman/scripts/dhclient-script
[   16.351056] type=1505 audit(1268231938.903:16): operation="profile_replace" pid=983 name=/usr/bin/evince
[   16.356006] type=1505 audit(1268231938.907:17): operation="profile_replace" pid=983 name=/usr/bin/evince-previewer
[   16.361038] type=1505 audit(1268231938.915:18): operation="profile_replace" pid=983 name=/usr/bin/evince-thumbnailer
[   16.367330] type=1505 audit(1268231938.919:19): operation="profile_replace" pid=990 name=/usr/lib/cups/backend/cups-pdf
[   16.367706] type=1505 audit(1268231938.919:20): operation="profile_replace" pid=990 name=/usr/sbin/cupsd
[   16.370908] type=1505 audit(1268231938.923:21): operation="profile_replace" pid=994 name=/usr/sbin/tcpdump
[   18.616564] [fglrx] GART Table is not in FRAME_BUFFER range 
[   18.617030]   alloc irq_desc for 29 on node -1
[   18.617034]   alloc kstat_irqs on node -1
[   18.617046] fglrx_pci 0000:01:05.0: irq 29 for MSI/MSI-X
[   18.619272] [fglrx] Firegl kernel thread PID: 1374
[   18.805768] [fglrx] Gart USWC size:1174 M.
[   18.805773] [fglrx] Gart cacheable size:466 M.
[   18.805780] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   18.805784] [fglrx] Reserved FB block: Unshared offset:fffb000, size:5000 
[   18.976795] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.976800] Bluetooth: BNEP filters: protocol multicast
[   18.985633] Bridge firewalling registered
[   19.066891] ppdev: user-space parallel port driver
[   19.293119] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[   19.296971] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   19.612923] CPU0 attaching NULL sched-domain.
[   19.612931] CPU1 attaching NULL sched-domain.
[   19.644210] CPU0 attaching sched-domain:
[   19.644216]  domain 0: span 0-1 level MC
[   19.644220]   groups: 0 1
[   19.644227] CPU1 attaching sched-domain:
[   19.644229]  domain 0: span 0-1 level MC
[   19.644232]   groups: 1 0
[   21.261801] CPU0 attaching NULL sched-domain.
[   21.261810] CPU1 attaching NULL sched-domain.
[   21.276112] CPU0 attaching sched-domain:
[   21.276118]  domain 0: span 0-1 level MC
[   21.276121]   groups: 0 1
[   21.276129] CPU1 attaching sched-domain:
[   21.276131]  domain 0: span 0-1 level MC
[   21.276134]   groups: 1 0
[   27.240019] eth1: no IPv6 routers present
[   29.552516] eth0: no IPv6 routers present
[   75.131590] [fglrx:fireglAsyncioIntDisableMsgHandler] *ERROR* IRQMGR returned error 1 when trying to disable interrupt source ff000034
[   75.665435] [fglrx:fireglAsyncioIntEnableMsgHandler] *ERROR* IRQMGR returned error 1 when trying to enable interrupt source ff000034

```
Thanks,
Dan

---

### Post by playcat on 2010-05-12
10.04 fixed the thing :)

Thx for reading guys
Dan

---

