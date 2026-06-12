---
title: "Terratec Cinergy HT PCI remote control not detected"
date: 2010-05-23
forum: Hardware
---

### Post by calande on 2010-05-23
Hello,

I have a Terratec Cinergy HT PCI remote control IR sensor that doesn't seem to be detected by my system. I can't find on the web a driver for this remote control sensor. Other than that, the DVB-T board works great. Only the remote control sensor doesn't work. Could you help me please? Here's the dmesg output. Thanks.

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
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000009ffb0000 (usable)
[    0.000000]  BIOS-e820: 000000009ffb0000 - 000000009ffc0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000009ffc0000 - 000000009fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000009fff0000 - 00000000a0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x9ffb0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 base 0080000000 mask FFE0000000 write-back
[    0.000000]   2 base 00E4000000 mask FFFC000000 write-combining
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
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000009ffb0000 (usable)
[    0.000000]  modified: 000000009ffb0000 - 000000009ffc0000 (ACPI data)
[    0.000000]  modified: 000000009ffc0000 - 000000009fff0000 (ACPI NVS)
[    0.000000]  modified: 000000009fff0000 - 00000000a0000000 (reserved)
[    0.000000]  modified: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
[    0.000000] RAMDISK: 37859000 - 37fefc3c
[    0.000000] Allocated new RAMDISK: 008de000 - 01074c3c
[    0.000000] Move RAMDISK from 0000000037859000 - 0000000037fefc3b to 008de000 - 01074c3b
[    0.000000] ACPI: RSDP 000fa7c0 00021 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 9ffb0100 0003C (v01 A M I  OEMXSDT  05000519 MSFT 00000097)
[    0.000000] ACPI: FACP 9ffb0290 000F4 (v03 A M I  OEMFACP  05000519 MSFT 00000097)
[    0.000000] ACPI: DSDT 9ffb03f0 03A3E (v01  A0036 A0036001 00000001 MSFT 0100000D)
[    0.000000] ACPI: FACS 9ffc0000 00040
[    0.000000] ACPI: APIC 9ffb0390 00052 (v01 A M I  OEMAPIC  05000519 MSFT 00000097)
[    0.000000] ACPI: OEMB 9ffc0040 0003F (v01 A M I  OEMBIOS  05000519 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1671MB HIGHMEM available.
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
[    0.000000]   #4 [000009d800 - 0000100000]    BIOS reserved ==> [000009d800 - 0000100000]
[    0.000000]   #5 [00008da000 - 00008dd234]              BRK ==> [00008da000 - 00008dd234]
[    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #7 [00008de000 - 0001074c3c]      NEW RAMDISK ==> [00008de000 - 0001074c3c]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0009ffb0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0009ffb0
[    0.000000] On node 0 totalpages: 655167
[    0.000000] free_area_init_node: node 0, pgdat c0798720, node_mem_map c1076200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 3344 pages used for memmap
[    0.000000]   HighMem zone: 424610 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at a0000000 (gap: a0000000:5f780000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2800000 s36024 r0 d21320 u2097152
[    0.000000] pcpu-alloc: s36024 r0 d21320 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 650047
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=b86eb121-0104-4329-a9bc-6aad1d0004ed ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 13105280 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0009ffb0)
[    0.000000] Memory: 2569476k/2621120k available (4673k kernel code, 50088k reserved, 2121k data, 656k init, 1711816k highmem)
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
[    0.000000] Extended CMOS year: 2000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2002.569 MHz processor.
[    0.004006] Calibrating delay loop (skipped), value calculated using timer frequency.. 4005.13 BogoMIPS (lpj=8010276)
[    0.004030] Security Framework initialized
[    0.004058] AppArmor: AppArmor initialized
[    0.004066] Mount-cache hash table entries: 512
[    0.004230] Initializing cgroup subsys ns
[    0.004234] Initializing cgroup subsys cpuacct
[    0.004239] Initializing cgroup subsys memory
[    0.004247] Initializing cgroup subsys devices
[    0.004250] Initializing cgroup subsys freezer
[    0.004253] Initializing cgroup subsys net_cls
[    0.004274] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004277] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004282] mce: CPU supports 5 MCE banks
[    0.004305] Performance Events: AMD PMU driver.
[    0.004312] ... version:                0
[    0.004314] ... bit width:              48
[    0.004316] ... generic registers:      4
[    0.004318] ... value mask:             0000ffffffffffff
[    0.004320] ... max period:             00007fffffffffff
[    0.004322] ... fixed-purpose events:   0
[    0.004324] ... event mask:             000000000000000f
[    0.004330] Checking 'hlt' instruction... OK.
[    0.020725] SMP alternatives: switching to UP code
[    0.026749] ACPI: Core revision 20090903
[    0.032644] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.032651] ftrace: allocating 21771 entries in 43 pages
[    0.036125] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.036937] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
[    0.079262] CPU0: AMD Athlon(tm) 64 Processor 3200+ stepping 00
[    0.080001] Brought up 1 CPUs
[    0.080001] Total of 1 processors activated (4005.13 BogoMIPS).
[    0.080001] CPU0 attaching NULL sched-domain.
[    0.080001] devtmpfs: initialized
[    0.080001] regulator: core version 0.5
[    0.080001] Time: 12:05:26  Date: 05/23/10
[    0.080001] NET: Registered protocol family 16
[    0.080001] EISA bus registered
[    0.080001] ACPI: bus type pci registered
[    0.080001] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[    0.080001] PCI: Using configuration type 1 for base access
[    0.080001] bio: create slab <bio-0> at 0
[    0.080001] ACPI: EC: Look up EC in DSDT
[    0.081422] ACPI: Executed 1 blocks of module-level executable AML code
[    0.084810] ACPI: Interpreter enabled
[    0.084817] ACPI: (supports S0 S1 S3 S4 S5)
[    0.084840] ACPI: Using IOAPIC for interrupt routing
[    0.089803] ACPI: No dock devices found.
[    0.089923] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.089969] pci 0000:00:00.0: reg 10 32bit mmio pref: [0xe4000000-0xe7ffffff]
[    0.090221] pci 0000:00:01.0: supports D1
[    0.090259] pci 0000:00:09.0: reg 10 32bit mmio: [0xf7000000-0xf7ffffff]
[    0.090322] pci 0000:00:09.1: reg 10 32bit mmio: [0xf8000000-0xf8ffffff]
[    0.090381] pci 0000:00:09.2: reg 10 32bit mmio: [0xf9000000-0xf9ffffff]
[    0.090451] pci 0000:00:0a.0: reg 10 32bit mmio: [0xfaa00000-0xfaa03fff]
[    0.090457] pci 0000:00:0a.0: reg 14 io port: [0xa400-0xa4ff]
[    0.090477] pci 0000:00:0a.0: reg 30 32bit mmio pref: [0xfa900000-0xfa91ffff]
[    0.090497] pci 0000:00:0a.0: supports D1 D2
[    0.090500] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.090504] pci 0000:00:0a.0: PME# disabled
[    0.090538] pci 0000:00:0d.0: reg 10 32bit mmio: [0xfab00000-0xfab00fff]
[    0.090544] pci 0000:00:0d.0: reg 14 io port: [0xa800-0xa8ff]
[    0.090580] pci 0000:00:0d.0: PME# supported from D0 D3hot D3cold
[    0.090584] pci 0000:00:0d.0: PME# disabled
[    0.090613] pci 0000:00:0e.0: reg 10 io port: [0xb000-0xb0ff]
[    0.090619] pci 0000:00:0e.0: reg 14 32bit mmio: [0xfac00000-0xfac001ff]
[    0.090653] pci 0000:00:0e.0: supports D1 D2
[    0.090655] pci 0000:00:0e.0: PME# supported from D1 D2 D3hot D3cold
[    0.090659] pci 0000:00:0e.0: PME# disabled
[    0.090690] pci 0000:00:0f.0: reg 10 io port: [0xd000-0xd007]
[    0.090697] pci 0000:00:0f.0: reg 14 io port: [0xc800-0xc803]
[    0.090703] pci 0000:00:0f.0: reg 18 io port: [0xc400-0xc407]
[    0.090709] pci 0000:00:0f.0: reg 1c io port: [0xc000-0xc003]
[    0.090715] pci 0000:00:0f.0: reg 20 io port: [0xb800-0xb80f]
[    0.090721] pci 0000:00:0f.0: reg 24 io port: [0xb400-0xb4ff]
[    0.090782] pci 0000:00:0f.1: reg 20 io port: [0xfc00-0xfc0f]
[    0.090852] pci 0000:00:10.0: reg 20 io port: [0xd400-0xd41f]
[    0.090874] pci 0000:00:10.0: supports D1 D2
[    0.090877] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.090880] pci 0000:00:10.0: PME# disabled
[    0.090922] pci 0000:00:10.1: reg 20 io port: [0xd800-0xd81f]
[    0.090944] pci 0000:00:10.1: supports D1 D2
[    0.090946] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.090950] pci 0000:00:10.1: PME# disabled
[    0.090991] pci 0000:00:10.2: reg 20 io port: [0xe000-0xe01f]
[    0.091014] pci 0000:00:10.2: supports D1 D2
[    0.091016] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.091020] pci 0000:00:10.2: PME# disabled
[    0.091062] pci 0000:00:10.3: reg 20 io port: [0xe400-0xe41f]
[    0.091084] pci 0000:00:10.3: supports D1 D2
[    0.091086] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.091090] pci 0000:00:10.3: PME# disabled
[    0.091118] pci 0000:00:10.4: reg 10 32bit mmio: [0xfae00000-0xfae000ff]
[    0.091155] pci 0000:00:10.4: supports D1 D2
[    0.091157] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.091161] pci 0000:00:10.4: PME# disabled
[    0.091215] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.091221] pci 0000:00:11.0: Enabled onboard AC97/MC97 devices
[    0.091268] pci 0000:00:11.5: reg 10 io port: [0xe800-0xe8ff]
[    0.091306] pci 0000:00:11.5: supports D1 D2
[    0.091335] pci 0000:00:11.6: reg 10 io port: [0x00-0xff]
[    0.091471] pci 0000:01:00.0: reg 10 32bit mmio: [0xfb000000-0xfbffffff]
[    0.091475] pci 0000:01:00.0: reg 14 32bit mmio pref: [0xe8000000-0xefffffff]
[    0.091489] pci 0000:01:00.0: reg 30 32bit mmio pref: [0xfaf00000-0xfaf1ffff]
[    0.091532] pci 0000:00:01.0: bridge 32bit mmio: [0xfaf00000-0xfbffffff]
[    0.091536] pci 0000:00:01.0: bridge 32bit mmio pref: [0xe8000000-0xf6ffffff]
[    0.091543] pci_bus 0000:00: on NUMA node 0
[    0.091547] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.100286] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 14 15)
[    0.100372] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *10 11 14 15)
[    0.100456] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 10 11 14 15)
[    0.100539] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 7 10 11 14 15)
[    0.100623] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.100708] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.100792] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.100877] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.100988] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.100991] vgaarb: loaded
[    0.101115] SCSI subsystem initialized
[    0.101196] libata version 3.00 loaded.
[    0.101266] usbcore: registered new interface driver usbfs
[    0.101279] usbcore: registered new interface driver hub
[    0.101303] usbcore: registered new device driver usb
[    0.101419] ACPI: WMI: Mapper loaded
[    0.101421] PCI: Using ACPI for IRQ routing
[    0.101595] NetLabel: Initializing
[    0.101597] NetLabel:  domain hash size = 128
[    0.101599] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.101614] NetLabel:  unlabeled traffic allowed by default
[    0.103498] AppArmor: AppArmor Filesystem Enabled
[    0.103521] pnp: PnP ACPI init
[    0.103540] ACPI: bus type pnp registered
[    0.104696] pnp 00:06: io resource (0x10-0x1f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.104700] pnp 00:06: io resource (0x22-0x3f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.104703] pnp 00:06: io resource (0x44-0x5f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.104707] pnp 00:06: io resource (0x62-0x63) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.104710] pnp 00:06: io resource (0x65-0x6f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.104714] pnp 00:06: io resource (0x72-0x7f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.104718] pnp 00:06: io resource (0x80-0x80) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.104721] pnp 00:06: io resource (0x84-0x86) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.104725] pnp 00:06: io resource (0x88-0x88) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.104728] pnp 00:06: io resource (0x8c-0x8e) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.104732] pnp 00:06: io resource (0x90-0x9f) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.104735] pnp 00:06: io resource (0xa2-0xbf) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.104739] pnp 00:06: io resource (0xe0-0xef) overlaps 0000:00:11.6 BAR 0 (0x0-0xff), disabling
[    0.106096] pnp: PnP ACPI: found 9 devices
[    0.106098] ACPI: ACPI bus type pnp unregistered
[    0.106102] PnPBIOS: Disabled by ACPI PNP
[    0.106116] system 00:05: ioport range 0x680-0x6ff has been reserved
[    0.106119] system 00:05: ioport range 0x290-0x297 has been reserved
[    0.106125] system 00:06: ioport range 0x3e1-0x3e7 has been reserved
[    0.106128] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[    0.106131] system 00:06: ioport range 0x800-0x87f has been reserved
[    0.106134] system 00:06: ioport range 0x400-0x41f has been reserved
[    0.106141] system 00:07: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.106144] system 00:07: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.106148] system 00:07: iomem range 0xfff80000-0xffffffff has been reserved
[    0.106153] system 00:08: iomem range 0x0-0x9ffff could not be reserved
[    0.106157] system 00:08: iomem range 0xc0000-0xdffff could not be reserved
[    0.106160] system 00:08: iomem range 0xe0000-0xfffff could not be reserved
[    0.106164] system 00:08: iomem range 0x100000-0x9ffeffff could not be reserved
[    0.140836] Switching to clocksource acpi_pm
[    0.140965] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.140967] pci 0000:00:01.0:   IO window: disabled
[    0.140972] pci 0000:00:01.0:   MEM window: 0xfaf00000-0xfbffffff
[    0.140976] pci 0000:00:01.0:   PREFETCH window: 0xe8000000-0xf6ffffff
[    0.140991] pci 0000:00:01.0: setting latency timer to 64
[    0.140996] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.140999] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.141002] pci_bus 0000:01: resource 1 mem: [0xfaf00000-0xfbffffff]
[    0.141005] pci_bus 0000:01: resource 2 pref mem [0xe8000000-0xf6ffffff]
[    0.141045] NET: Registered protocol family 2
[    0.141143] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.141536] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.142627] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.143245] TCP: Hash tables configured (established 131072 bind 65536)
[    0.143248] TCP reno registered
[    0.143366] NET: Registered protocol family 1
[    0.143390] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
[    1.740013] pci 0000:00:10.4: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[    1.740137] pci 0000:01:00.0: Boot video device
[    1.740349] cpufreq-nforce2: No nForce2 chipset.
[    1.740377] Scanning for low memory corruption every 60 seconds
[    1.740488] audit: initializing netlink socket (disabled)
[    1.740500] type=2000 audit(1274616327.740:1): initialized
[    1.750612] Trying to unpack rootfs image as initramfs...
[    1.764372] highmem bounce pool size: 64 pages
[    1.764379] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.765830] VFS: Disk quotas dquot_6.5.2
[    1.765899] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.766488] fuse init (API version 7.13)
[    1.766570] msgmni has been set to 1677
[    1.772239] alg: No test for stdrng (krng)
[    1.772346] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.772350] io scheduler noop registered
[    1.772352] io scheduler anticipatory registered
[    1.772354] io scheduler deadline registered
[    1.772392] io scheduler cfq registered (default)
[    1.772523] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.772544] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.772650] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    1.772660] ACPI: Power Button [PWRB]
[    1.772707] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    1.772712] ACPI: Sleep Button [SLPB]
[    1.772756] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    1.772759] ACPI: Power Button [PWRF]
[    1.773117] processor LNXCPU:00: registered as cooling_device0
[    1.776795] isapnp: Scanning for PnP cards...
[    1.782463] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.782734]   alloc irq_desc for 18 on node -1
[    1.782736]   alloc kstat_irqs on node -1
[    1.782744] serial 0000:00:0d.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.782862] 0000:00:0d.0: ttyS0 at I/O 0xa808 (irq = 18) is a 16450
[    1.782927] 0000:00:0d.0: ttyS1 at I/O 0xa810 (irq = 18) is a 8250
[    1.782989] 0000:00:0d.0: ttyS2 at I/O 0xa818 (irq = 18) is a 16450
[    1.783051] 0000:00:0d.0: ttyS3 at I/O 0xa820 (irq = 18) is a 8250
[    1.783072] Couldn't register serial port 0000:00:0d.0: -28
[    1.788293] brd: module loaded
[    1.788785] loop: module loaded
[    1.788899] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.789076]   alloc irq_desc for 20 on node -1
[    1.789079]   alloc kstat_irqs on node -1
[    1.789087] pata_acpi 0000:00:0f.1: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.789159] pata_acpi 0000:00:0f.1: PCI INT A disabled
[    1.789450] Fixed MDIO Bus: probed
[    1.789483] PPP generic driver version 2.4.2
[    1.789529] tun: Universal TUN/TAP device driver, 1.6
[    1.789531] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.789608] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.789624]   alloc irq_desc for 21 on node -1
[    1.789626]   alloc kstat_irqs on node -1
[    1.789631] ehci_hcd 0000:00:10.4: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    1.789651] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    1.789681] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 1
[    1.789751] ehci_hcd 0000:00:10.4: irq 21, io mem 0xfae00000
[    1.839846] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00
[    1.839993] usb usb1: configuration #1 chosen from 1 choice
[    1.840041] hub 1-0:1.0: USB hub found
[    1.840053] hub 1-0:1.0: 8 ports detected
[    1.840118] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.840138] uhci_hcd: USB Universal Host Controller Interface driver
[    1.840202] uhci_hcd 0000:00:10.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.840212] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    1.840248] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[    1.840272] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000d400
[    1.840371] usb usb2: configuration #1 chosen from 1 choice
[    1.840395] hub 2-0:1.0: USB hub found
[    1.840404] hub 2-0:1.0: 2 ports detected
[    1.840443] uhci_hcd 0000:00:10.1: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.840451] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    1.840479] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[    1.840498] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000d800
[    1.840589] usb usb3: configuration #1 chosen from 1 choice
[    1.840612] hub 3-0:1.0: USB hub found
[    1.840620] hub 3-0:1.0: 2 ports detected
[    1.840660] uhci_hcd 0000:00:10.2: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.840666] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    1.840704] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[    1.840722] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000e000
[    1.840824] usb usb4: configuration #1 chosen from 1 choice
[    1.840848] hub 4-0:1.0: USB hub found
[    1.840856] hub 4-0:1.0: 2 ports detected
[    1.840893] uhci_hcd 0000:00:10.3: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.840898] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    1.840926] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
[    1.840944] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000e400
[    1.841041] usb usb5: configuration #1 chosen from 1 choice
[    1.841065] hub 5-0:1.0: USB hub found
[    1.841074] hub 5-0:1.0: 2 ports detected
[    1.841165] PNP: No PS/2 controller found. Probing ports directly.
[    1.841653] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.841659] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.841733] mice: PS/2 mouse device common for all mice
[    1.841846] rtc_cmos 00:02: RTC can wake from S4
[    1.841889] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.841940] rtc0: alarms up to one year, y3k, 114 bytes nvram
[    1.842046] device-mapper: uevent: version 1.0.3
[    1.844242] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.848158] device-mapper: multipath: version 1.1.0 loaded
[    1.848163] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.848358] EISA: Probing bus 0 at eisa.0
[    1.848367] Cannot allocate resource for EISA slot 1
[    1.848379] Cannot allocate resource for EISA slot 5
[    1.848392] EISA: Detected 0 cards.
[    1.852321] cpuidle: using governor ladder
[    1.852324] cpuidle: using governor menu
[    1.852808] TCP cubic registered
[    1.852966] NET: Registered protocol family 10
[    1.853420] lo: Disabled Privacy Extensions
[    1.853719] NET: Registered protocol family 17
[    1.853758] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3200+ processors (1 cpu cores) (version 2.20.00)
[    1.854940] [Firmware Bug]: powernow-k8: No PSB or ACPI _PSS objects
[    1.854959] Using IPI No-Shortcut mode
[    1.855067] PM: Resume from disk failed.
[    1.855080] registered taskstats version 1
[    1.855433]   Magic number: 10:506:77
[    1.855556] rtc_cmos 00:02: setting system clock to 2010-05-23 12:05:28 UTC (1274616328)
[    1.855560] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.855562] EDD information not available.
[    2.218324] Freeing initrd memory: 7771k freed
[    2.358066] isapnp: No Plug & Play device found
[    2.358101] Freeing unused kernel memory: 656k freed
[    2.358952] Write protecting the kernel text: 4676k
[    2.358986] Write protecting the kernel read-only data: 1840k
[    2.379548] udev: starting version 151
[    2.468078] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    2.594518] pata_via 0000:00:0f.1: version 0.3.4
[    2.594533] pata_via 0000:00:0f.1: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.594789] scsi0 : pata_via
[    2.594959] scsi1 : pata_via
[    2.596226] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[    2.596229] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[    2.596365] sata_via 0000:00:0f.0: version 2.4
[    2.596376] sata_via 0000:00:0f.0: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    2.596414] sata_via 0000:00:0f.0: routed to hard irq line 10
[    2.596619] scsi2 : sata_via
[    2.596710] scsi3 : sata_via
[    2.596745] ata3: SATA max UDMA/133 cmd 0xd000 ctl 0xc800 bmdma 0xb800 irq 20
[    2.596748] ata4: SATA max UDMA/133 cmd 0xc400 ctl 0xc000 bmdma 0xb808 irq 20
[    2.596842]   alloc irq_desc for 17 on node -1
[    2.596845]   alloc kstat_irqs on node -1
[    2.596852] skge 0000:00:0a.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.596862] skge 0000:00:0a.0: PCI: Disallowing DAC for device
[    2.596892] skge 1.13 addr 0xfaa00000 irq 17 chip Yukon-Lite rev 9
[    2.597534] skge eth0: addr 00:13:d4:78:a3:e0
[    2.625507] usb 3-1: configuration #1 chosen from 1 choice
[    2.642743] usbcore: registered new interface driver hiddev
[    2.643123] usbcore: registered new interface driver usbhid
[    2.643201] usbhid: v2.6:USB HID core driver
[    2.800017] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.872015] usb 3-2: new low speed USB device using uhci_hcd and address 3
[    3.020196] ata3.00: ATA-7: Kingston SSDNow V Series 64GB, B090522a, max UDMA/133
[    3.020200] ata3.00: 125045424 sectors, multi 1: LBA 
[    3.028207] ata3.00: configured for UDMA/133
[    3.028327] scsi 2:0:0:0: Direct-Access     ATA      Kingston SSDNow  B090 PQ: 0 ANSI: 5
[    3.028492] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    3.028733] sd 2:0:0:0: [sda] 125045424 512-byte logical blocks: (64.0 GB/59.6 GiB)
[    3.028776] sd 2:0:0:0: [sda] Write Protect is off
[    3.028779] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.028802] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.028929]  sda: sda1 < sda5 sda6 > sda2
[    3.030156] sd 2:0:0:0: [sda] Attached SCSI disk
[    3.048412] usb 3-2: configuration #1 chosen from 1 choice
[    3.067651] input: Kensington USB/PS2 Wheel Mouse  as /devices/pci0000:00/0000:00:10.1/usb3/3-2/3-2:1.0/input/input4
[    3.067745] generic-usb 0003:047D:1002.0003: input,hidraw0: USB HID v1.00 Mouse [Kensington USB/PS2 Wheel Mouse ] on usb-0000:00:10.1-2/input0
[    3.232021] ata4: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    3.263683] input: HID 046a:0023 as /devices/pci0000:00/0000:00:10.1/usb3/3-1/3-1:1.0/input/input5
[    3.263775] cherry 0003:046A:0023.0001: input,hidraw1: USB HID v1.11 Keyboard [HID 046a:0023] on usb-0000:00:10.1-1/input0
[    3.287935] input: HID 046a:0023 as /devices/pci0000:00/0000:00:10.1/usb3/3-1/3-1:1.1/input/input6
[    3.288044] cherry 0003:046A:0023.0002: input,hidraw2: USB HID v1.11 Device [HID 046a:0023] on usb-0000:00:10.1-1/input1
[    3.304859] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    3.601918] Adding 1317288k swap on /dev/sda6.  Priority:-1 extents:1 across:1317288k SS
[    3.678381] udev: starting version 151
[    4.025462] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    4.040940] Linux agpgart interface v0.103
[    4.246673] agpgart-amd64 0000:00:00.0: AGP bridge [1106/0282]
[    4.260232] Linux video capture interface: v2.00
[    4.263709] cfg80211: Calling CRDA to update world regulatory domain
[    4.281596] agpgart-amd64 0000:00:00.0: AGP aperture is 64M @ 0xe4000000
[    4.309637] lp: driver loaded but no devices found
[    4.330978] type=1505 audit(1274609130.972:2):  operation="profile_load" pid=530 name="/sbin/dhclient3"
[    4.331259] type=1505 audit(1274609130.972:3):  operation="profile_load" pid=530 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    4.331420] type=1505 audit(1274609130.972:4):  operation="profile_load" pid=530 name="/usr/lib/connman/scripts/dhclient-script"
[    4.357775] cfg80211: World regulatory domain updated:
[    4.357780] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    4.357783] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    4.357787] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    4.357790] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    4.357792] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    4.357795] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    4.433505] vga16fb: initializing
[    4.433510] vga16fb: mapped to 0xc00a0000
[    4.433756] fb0: VGA16 VGA frame buffer device
[    4.460895] cx88/0: cx2388x v4l2 driver version 0.0.7 loaded
[    4.460941]   alloc irq_desc for 16 on node -1
[    4.460943]   alloc kstat_irqs on node -1
[    4.460952] cx8800 0000:00:09.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.461309] cx88[0]: subsystem: 153b:1177, board: Terratec Cinergy HT PCI MKII [card=79,autodetected], frontend(s): 1
[    4.461312] cx88[0]: TV tuner type 71, Radio tuner type 71
[    4.628446] nvidia: module license 'NVIDIA' taints kernel.
[    4.628452] Disabling lock debugging due to kernel taint
[    5.388842] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.7 loaded
[    5.498204] tuner 1-0061: chip found @ 0xc2 (cx88[0])
[    5.601538] cx2388x alsa driver version 0.0.7 loaded
[    5.622107] ip_tables: (C) 2000-2006 Netfilter Core Team
[    5.748511] xc2028 1-0061: creating new instance
[    5.748516] xc2028 1-0061: type set to XCeive xc2028/xc3028 tuner
[    5.748522] xc2028 1-0061: destroying instance
[    5.748609] xc2028 1-0061: creating new instance
[    5.748611] xc2028 1-0061: type set to XCeive xc2028/xc3028 tuner
[    5.748614] cx88[0]: Asking xc2028/3028 to load firmware xc3028-v27.fw
[    5.764227] cx88[0]/0: found at 0000:00:09.0, rev: 5, irq: 16, latency: 64, mmio: 0xf7000000
[    5.764243] IRQ 16/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[    5.764361] cx88[0]/0: registered device video0 [v4l2]
[    5.764386] cx88[0]/0: registered device vbi0
[    5.764410] cx88[0]/0: registered device radio0
[    5.764469] cx8800 0000:00:09.0: firmware: requesting xc3028-v27.fw
[    5.783967] xc2028 1-0061: Loading 80 firmware images from xc3028-v27.fw, type: xc2028 firmware, ver 2.7
[    5.784131] cx88[0]: Calling XC2028/3028 callback
[    5.784133] cx88[0]: setting GPIO to TV!
[    6.528184] xc2028 1-0061: Loading firmware for type=BASE MTS (5), id 0000000000000000.
[    6.528189] cx88[0]: Calling XC2028/3028 callback
[    6.528191] cx88[0]: setting GPIO to TV!
[    7.381598] Console: switching to colour frame buffer device 80x30
[    7.404632] skge eth0: enabling interface
[    7.432615] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    7.579412] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.581990] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.22  Sun Nov  8 20:26:31 PST 2009
[    7.705516] type=1505 audit(1274609134.348:5):  operation="profile_load" pid=744 name="/usr/share/gdm/guest-session/Xsession"
[    7.707966] type=1505 audit(1274609134.348:6):  operation="profile_replace" pid=746 name="/sbin/dhclient3"
[    7.722413] type=1505 audit(1274609134.364:7):  operation="profile_replace" pid=746 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    7.722588] type=1505 audit(1274609134.364:8):  operation="profile_replace" pid=746 name="/usr/lib/connman/scripts/dhclient-script"
[    7.763309] type=1505 audit(1274609134.404:9):  operation="profile_load" pid=748 name="/usr/bin/evince"
[    7.776341] type=1505 audit(1274609134.420:10):  operation="profile_load" pid=748 name="/usr/bin/evince-previewer"
[    7.804052] type=1505 audit(1274609134.448:11):  operation="profile_load" pid=748 name="/usr/bin/evince-thumbnailer"
[    7.853470] type=1505 audit(1274609134.496:12):  operation="profile_load" pid=816 name="/usr/lib/cups/backend/cups-pdf"
[    7.853840] type=1505 audit(1274609134.496:13):  operation="profile_load" pid=816 name="/usr/sbin/cupsd"
[    7.868542] type=1505 audit(1274609134.512:14):  operation="profile_load" pid=817 name="/usr/sbin/mysqld-akonadi"
[    9.133567] skge eth0: Link is up at 100 Mbps, full duplex, flow control none
[    9.133789] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[    9.600722] xc2028 1-0061: Loading firmware for type=MTS (4), id 000000000000b700.
[    9.628964] xc2028 1-0061: Loading SCODE for type=MTS LCD NOGD MONO IF SCODE HAS_IF_4500 (6002b004), id 000000000000b700.
[    9.692065] cx88[0]: Calling XC2028/3028 callback
[    9.813349]   alloc irq_desc for 19 on node -1
[    9.813353]   alloc kstat_irqs on node -1
[    9.813362] rtl8180 0000:00:0e.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    9.837334] cx88[0]: Calling XC2028/3028 callback
[    9.837340] cx88[0]: setting GPIO to TV!
[   10.581396] xc2028 1-0061: Loading firmware for type=BASE FM (401), id 0000000000000000.
[   10.581402] cx88[0]: Calling XC2028/3028 callback
[   10.581405] cx88[0]: setting GPIO to TV!
[   11.421555] agpgart-amd64 0000:00:00.0: AGP 3.0 bridge
[   11.421569] agpgart-amd64 0000:00:00.0: putting AGP V3 device into 8x mode
[   11.421666] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
[   11.572166] phy0: Selected rate control algorithm 'minstrel'
[   11.572864] phy0: hwaddr 00:17:3f:2e:ef:0b, RTL8185vD + rtl8225z2
[   11.573461] cx88[0]/2: cx2388x 8802 Driver Manager
[   11.573480] cx88-mpeg driver manager 0000:00:09.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.573489] cx88[0]/2: found at 0000:00:09.2, rev: 5, irq: 16, latency: 64, mmio: 0xf9000000
[   11.573497] IRQ 16/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   11.573913] cx88_audio 0000:00:09.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.573920] IRQ 16/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   11.573941] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[   11.574938] VIA 82xx Modem 0000:00:11.6: enabling device (0000 -> 0001)
[   11.574945]   alloc irq_desc for 22 on node -1
[   11.574947]   alloc kstat_irqs on node -1
[   11.574955] VIA 82xx Modem 0000:00:11.6: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[   11.709972] usb 1-1: new high speed USB device using ehci_hcd and address 4
[   11.814180] cx88/2: cx2388x dvb driver version 0.0.7 loaded
[   11.814184] cx88/2: registering cx8802 driver, type: dvb access: shared
[   11.814189] cx88[0]/2: subsystem: 153b:1177, board: Terratec Cinergy HT PCI MKII [card=79]
[   11.814193] cx88[0]/2: cx2388x based DVB/ATSC card
[   11.814195] cx8802_alloc_frontends() allocating 1 frontend(s)
[   11.894544] usb 1-1: configuration #1 chosen from 1 choice
[   11.914482] xc2028 1-0061: attaching existing instance
[   11.914486] xc2028 1-0061: type set to XCeive xc2028/xc3028 tuner
[   11.941043] Initializing USB Mass Storage driver...
[   11.956605] scsi4 : SCSI emulation for USB Mass Storage devices
[   11.956972] usbcore: registered new interface driver usb-storage
[   11.956975] USB Mass Storage support registered.
[   11.959816] usb-storage: device found at 4
[   11.959819] usb-storage: waiting for device to settle before scanning
[   12.357450] VIA 82xx Modem 0000:00:11.6: setting latency timer to 64
[   12.427138] ppdev: user-space parallel port driver
[   14.909443] xc2028 1-0061: Loading firmware for type=FM (400), id 0000000000000000.
[   14.968026] cx88[0]: Calling XC2028/3028 callback
[   15.104165] cx88[0]/2: xc3028 attached
[   15.104173] DVB: registering new adapter (cx88[0])
[   15.104178] DVB: registering adapter 0 frontend 0 (Zarlink ZL10353 DVB-T)...
[   15.107294] VIA 82xx Modem 0000:00:11.6: PCI INT C disabled
[   15.107313] VIA 82xx Modem: probe of 0000:00:11.6 failed with error -13
[   15.107522] VIA 82xx Audio 0000:00:11.5: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[   15.107676] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   15.940243] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.697175] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697186] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697196] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697203] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697210] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697217] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697235] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697241] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697258] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697265] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697272] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697278] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697284] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697290] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697296] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697303] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697309] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697315] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697321] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697327] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697334] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697340] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697357] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697363] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697370] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697376] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697383] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697389] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697406] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697413] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697419] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697426] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697432] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697438] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697444] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697450] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697457] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697463] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697480] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697487] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697493] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697500] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697506] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697512] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697529] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697535] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697542] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697549] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697555] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697561] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697579] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697585] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697592] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697598] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697615] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697622] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697629] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697635] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697652] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697658] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697665] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697672] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697678] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697684] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697701] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697707] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697714] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697721] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697727] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697733] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697750] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697757] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697764] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697770] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697776] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697782] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697799] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697806] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697813] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697819] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697825] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697831] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697849] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697856] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697875] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697885] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697891] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697899] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697905] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697922] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697929] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697935] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697953] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697959] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697976] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.697986] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.707758] cx88[0]: irq aud [0x1101] dn_risci1* dnf_of dn_sync*
[   16.707769] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.707778] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.707785] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.707803] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.707810] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.707827] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.707833] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.707840] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.707846] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.707853] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.707859] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.707876] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.707882] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.707890] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.707896] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.707903] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.707909] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.707926] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.707932] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.707939] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.707946] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.707952] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.707958] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.707964] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.707970] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.707988] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.707994] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708002] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708008] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708046] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708055] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708062] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708081] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708090] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708097] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708105] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708111] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708128] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708135] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708142] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708148] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708154] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708161] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708178] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708184] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708191] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708198] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708204] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708210] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708227] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708234] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708241] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708247] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708264] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708271] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708278] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708284] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708302] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708308] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708315] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708321] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708328] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708334] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708351] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708358] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708365] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708371] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708389] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708395] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708402] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708408] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708426] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708432] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708439] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708446] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708452] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708458] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708464] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708471] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708489] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708495] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708505] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708512] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708519] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708525] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708542] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708549] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708556] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708562] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708579] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708585] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708593] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708599] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708616] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708623] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708630] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708636] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708654] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708660] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708667] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708673] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708680] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708686] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708703] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708710] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708717] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708723] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708741] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708747] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708754] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708760] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708766] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708773] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708790] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708796] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708803] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708810] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708827] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708833] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708840] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708846] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708864] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708870] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708877] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708884] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708901] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708907] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708914] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708921] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708927] cx88[0]: irq aud [0x1000] dn_sync*
[   16.708933] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708950] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708957] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708964] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708970] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708987] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.708993] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709001] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709007] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709025] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709031] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709038] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709044] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709051] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709057] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709074] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709080] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709088] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709094] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709112] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709118] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709125] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709131] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709149] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709155] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709162] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709168] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709185] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709192] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709199] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709205] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709222] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709228] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709236] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709242] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709259] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709266] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709273] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709279] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709295] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709302] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709308] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709325] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709332] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709339] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709346] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709352] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709358] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709376] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709382] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709389] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709395] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709412] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709419] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709426] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709432] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709439] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709445] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709462] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709469] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709476] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709482] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709500] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709506] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709513] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709519] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709537] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709543] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709550] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709556] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709574] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709580] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709587] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709594] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709611] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709617] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709624] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709631] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709648] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709655] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709661] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709668] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709685] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709691] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709699] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709705] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709711] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709718] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709735] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709742] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709748] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709755] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709773] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709779] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709786] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709792] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709798] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709805] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709822] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709829] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709836] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709846] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709852] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709860] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709867] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709884] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709891] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709898] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709904] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709910] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709917] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709923] cx88[0]: irq aud [0x1000] dn_sync*
[   16.709929] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709946] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709953] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709960] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709966] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709984] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709990] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.709997] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.710003] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.710010] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.710020] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.710026] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.710034] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.710040] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.710047] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.710053] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.710059] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.710066] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.710083] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.710090] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.710099] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[   16.960734] usb-storage: device scan complete
[   16.964718] scsi 4:0:0:0: Direct-Access     WD       2500BEV External 1.04 PQ: 0 ANSI: 4
[   16.966884] sd 4:0:0:0: Attached scsi generic sg1 type 0
[   16.976876] sd 4:0:0:0: [sdb] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[   16.978007] sd 4:0:0:0: [sdb] Write Protect is off
[   16.978012] sd 4:0:0:0: [sdb] Mode Sense: 21 00 00 00
[   16.978015] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   16.979752] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   16.979762]  sdb: sdb1
[   17.034641] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   17.034665] sd 4:0:0:0: [sdb] Attached SCSI disk
[   17.087051] cfg80211: Found new beacon on frequency: 2467 MHz (Ch 12) on phy0
[   19.908026] eth0: no IPv6 routers present
[  222.676030] usb 1-1: USB disconnect, address 4
[45507.364535] __ratelimit: 3 callbacks suppressed
[45507.364541] operapluginwrap[26487]: segfault at 0 ip (null) sp bf9906bc error 4 in libXext.so.6.4.0[110000+e000]
[45507.391097] operapluginwrap[26498]: segfault at 0 ip (null) sp bfc0a90c error 4 in libX11.so.6.3.0[110000+119000]
[45507.490360] operapluginwrap[26521]: segfault at 0 ip (null) sp bfab34bc error 4 in libXt.so.6.0.0[110000+4f000]
[45507.541853] operapluginwrap[26543]: segfault at 0 ip (null) sp bfab449c error 4 in libc-2.11.1.so[110000+153000]
[46029.168937] type=1505 audit(1274655158.430:16):  operation="profile_replace" pid=26978 name="/usr/share/gdm/guest-session/Xsession"
[46029.386502] type=1505 audit(1274655158.646:17):  operation="profile_replace" pid=26979 name="/sbin/dhclient3"
[46029.386696] type=1505 audit(1274655158.646:18):  operation="profile_replace" pid=26979 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[46029.386801] type=1505 audit(1274655158.646:19):  operation="profile_replace" pid=26979 name="/usr/lib/connman/scripts/dhclient-script"
[46041.441901] type=1505 audit(1274655170.702:20):  operation="profile_replace" pid=26980 name="/usr/bin/evince"
[46041.444138] type=1505 audit(1274655170.706:21):  operation="profile_replace" pid=26980 name="/usr/bin/evince-previewer"
[46041.453260] type=1505 audit(1274655170.714:22):  operation="profile_replace" pid=26980 name="/usr/bin/evince-thumbnailer"
[46042.450038] type=1505 audit(1274655171.710:23):  operation="profile_replace" pid=26999 name="/usr/lib/cups/backend/cups-pdf"
[46042.451077] type=1505 audit(1274655171.710:24):  operation="profile_replace" pid=26999 name="/usr/sbin/cupsd"
[46042.767225] type=1505 audit(1274655172.026:25):  operation="profile_replace" pid=27001 name="/usr/sbin/mysqld-akonadi"
[46043.044213] type=1505 audit(1274655172.306:26):  operation="profile_replace" pid=27002 name="/usr/sbin/tcpdump"
```

---

### Post by calande on 2010-05-24
Any idea? :)

---

### Post by DOM81 on 2011-09-19
I concur with the request

---

### Post by calande on 2012-02-24
Does someone know from the above dmesg the name of my radio module, and which driver I should use? Thanks.

---

