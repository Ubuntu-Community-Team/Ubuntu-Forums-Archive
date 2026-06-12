---
title: "CPU Frequency Scaling not working for me in Ubuntu 9.10"
date: 2009-10-26
forum: Hardware
---

### Post by Brain_Recall on 2009-10-26
I just upgraded my craptastic Dell Inspiron 5150 with Ubuntu 9.10 RC. The first major issue is CPU Frequency Scaling no longer works, as reported from the CPU Frequency Scaling Monitor. This had worked perfectly under Ubuntu 9.04, so I guess the switch from hal to DeviceKit is to blame.

The 5150 in question uses a [Mobile Pentium 4]("http://en.wikipedia.org/wiki/Pentium_4#Mobile_Pentium_4") @ 2.8GHz. Essentially, it's a battery-powered toaster oven. I need scaling to work, otherwise [the 5150's notoriously crappy hardware]("http://en.wikipedia.org/wiki/Dell_Inspiron#Problems") will catch up to me.

Does anyone have any suggestions?

---

### Post by Dark_Stang on 2009-10-27
Is powernowd installed? If not, install that and see if that helps.

---

### Post by Yellow Pasque on 2009-10-27
More info needed, relevant sections of dmesg, what happpens when you try and modprobe powernowd, etc.

---

### Post by Brain_Recall on 2009-10-27
The output of dmesg (not sure what you're looking for):
```
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000002ffcf800 (usable)
[    0.000000]  BIOS-e820: 000000002ffcf800 - 0000000030000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec20000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] last_pfn = 0x2ffcf max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FE0000000 write-back
[    0.000000]   1 base 020000000 mask FF0000000 write-back
[    0.000000]   2 base 0FEDA0000 mask FFFFE0000 write-combining
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009f000 (usable)
[    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000002ffcf800 (usable)
[    0.000000]  modified: 000000002ffcf800 - 0000000030000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec20000 (reserved)
[    0.000000]  modified: 00000000feda0000 - 00000000fee10000 (reserved)
[    0.000000]  modified: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-000000002ffcf000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 002fc00000 page 2M
[    0.000000]  002fc00000 - 002ffcf000 page 4k
[    0.000000] kernel direct mapping tables up to 2ffcf000 @ 7000-c000
[    0.000000] RAMDISK: 238d2000 - 2401b87f
[    0.000000] ACPI: RSDP 000fdea0 00014 (v00 DELL  )
[    0.000000] ACPI: RSDT 2fff0000 00030 (v01 DELL    CPi R   27D40C0A ASL  00000061)
[    0.000000] ACPI: FACP 2fff0400 00074 (v01 DELL    CPi R   27D40C0A ASL  00000061)
[    0.000000] ACPI: DSDT 2fff1000 0220B (v01 INT430 SYSFexxx 00001001 MSFT 0100000E)
[    0.000000] ACPI: FACS 2ffff800 00040
[    0.000000] ACPI: APIC 2fff0c00 00068 (v01 DELL    CPi R   27D40C0A ASL  00000047)
[    0.000000] ACPI: BOOT 2fff07c0 00028 (v01 DELL    CPi R   27D40C0A ASL  00000061)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 767MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 2ffcf000
[    0.000000]   low ram: 0 - 2ffcf000
[    0.000000]   node 0 low ram: 00000000 - 2ffcf000
[    0.000000]   node 0 bootmap 00008000 - 0000dffc
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 002ffcf000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
[    0.000000]   #4 [00238d2000 - 002401b87f]          RAMDISK ==> [00238d2000 - 002401b87f]
[    0.000000]   #5 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #6 [00008a9000 - 00008ac1a4]              BRK ==> [00008a9000 - 00008ac1a4]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000e000]          BOOTMAP ==> [0000008000 - 000000e000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0002ffcf
[    0.000000]   HighMem  0x0002ffcf -> 0x0002ffcf
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0002ffcf
[    0.000000] On node 0 totalpages: 196458
[    0.000000] free_area_init_node: node 0, pgdat c0784900, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1504 pages used for memmap
[    0.000000]   Normal zone: 190959 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 30000000:cec00000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c1604000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 194922
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=c7d465d9-9fa4-46f4-aa88-b5c073cdbaf8 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 3931180 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 759316k/786236k available (4565k kernel code, 26256k reserved, 2143k data, 540k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf07cf000 - 0xff7fe000   ( 240 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xeffcf000   ( 767 MB)
[    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
[    0.000000]       .data : 0xc0575554 - 0xc078d308   (2143 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0575554   (4565 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2790.836 MHz processor.
[    0.001706] Console: colour VGA+ 80x25
[    0.001711] console [tty0] enabled
[    0.004009] Calibrating delay loop (skipped), value calculated using timer frequency.. 5581.67 BogoMIPS (lpj=11163344)
[    0.004034] Security Framework initialized
[    0.004056] AppArmor: AppArmor initialized
[    0.004066] Mount-cache hash table entries: 512
[    0.004227] Initializing cgroup subsys ns
[    0.004233] Initializing cgroup subsys cpuacct
[    0.004240] Initializing cgroup subsys memory
[    0.004249] Initializing cgroup subsys freezer
[    0.004253] Initializing cgroup subsys net_cls
[    0.004273] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    0.004278] CPU: L2 cache: 512K
[    0.004283] CPU: Physical Processor ID: 0
[    0.004286] CPU: Processor Core ID: 0
[    0.004292] mce: CPU supports 4 MCE banks
[    0.004304] CPU0: Thermal monitoring enabled (TM1)
[    0.004315] Performance Counters: no PMU driver, software counters only.
[    0.004323] Checking 'hlt' instruction... OK.
[    0.023100] ACPI: Core revision 20090521
[    0.030189] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.069876] CPU0: Mobile Intel(R) Pentium(R) 4     CPU 2.80GHz stepping 09
[    0.072001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 5582.38 BogoMIPS (lpj=11164771)
[    0.004000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    0.004000] CPU: L2 cache: 512K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] mce: CPU supports 4 MCE banks
[    0.004000] CPU1: Thermal monitoring enabled (TM1)
[    0.004000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.156874] CPU1: Mobile Intel(R) Pentium(R) 4     CPU 2.80GHz stepping 09
[    0.156898] checking TSC synchronization [CPU#0 -> CPU#1]:
[    0.160001] Measured 31831732 cycles TSC warp between CPUs, turning off TSC clock.
[    0.160001] Marking TSC unstable due to check_tsc_sync_source failed
[    0.160049] Brought up 2 CPUs
[    0.160057] Total of 2 processors activated (11164.05 BogoMIPS).
[    0.160109] CPU0 attaching sched-domain:
[    0.160114]  domain 0: span 0-1 level SIBLING
[    0.160119]   groups: 0 1
[    0.160129] CPU1 attaching sched-domain:
[    0.160133]  domain 0: span 0-1 level SIBLING
[    0.160138]   groups: 1 0
[    0.160255] Booting paravirtualized kernel on bare hardware
[    0.160300] regulator: core version 0.5
[    0.160300] Time:  0:15:58  Date: 10/28/09
[    0.160300] NET: Registered protocol family 16
[    0.160311] EISA bus registered
[    0.160327] ACPI: bus type pci registered
[    0.212688] PCI: PCI BIOS revision 2.10 entry at 0xfcf1e, last bus=2
[    0.212693] PCI: Using configuration type 1 for base access
[    0.214397] bio: create slab <bio-0> at 0
[    0.214397] ACPI: EC: Look up EC in DSDT
[    0.220350] ACPI: Interpreter enabled
[    0.220361] ACPI: (supports S0 S1 S3 S4 S5)
[    0.220398] ACPI: Using IOAPIC for interrupt routing
[    0.228582] ACPI: No dock devices found.
[    0.234651] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.234721] pci 0000:00:00.0: reg 10 32bit mmio: [0xe0000000-0xe7ffffff]
[    0.234950] pci 0000:00:1d.0: reg 20 io port: [0xbf80-0xbf9f]
[    0.235014] pci 0000:00:1d.1: reg 20 io port: [0xbf40-0xbf5f]
[    0.235079] pci 0000:00:1d.2: reg 20 io port: [0xbf20-0xbf3f]
[    0.235152] pci 0000:00:1d.7: reg 10 32bit mmio: [0xf4fffc00-0xf4ffffff]
[    0.235217] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.235224] pci 0000:00:1d.7: PME# disabled
[    0.235326] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[    0.235332] pci 0000:00:1f.0: quirk: region 1080-10bf claimed by ICH4 GPIO
[    0.235362] pci 0000:00:1f.1: reg 10 io port: [0x1f0-0x1f7]
[    0.235371] pci 0000:00:1f.1: reg 14 io port: [0x3f4-0x3f7]
[    0.235381] pci 0000:00:1f.1: reg 18 io port: [0x170-0x177]
[    0.235390] pci 0000:00:1f.1: reg 1c io port: [0x374-0x377]
[    0.235399] pci 0000:00:1f.1: reg 20 io port: [0xbfa0-0xbfaf]
[    0.235409] pci 0000:00:1f.1: reg 24 32bit mmio: [0x000000-0x0003ff]
[    0.235461] pci 0000:00:1f.5: reg 10 io port: [0xb800-0xb8ff]
[    0.235470] pci 0000:00:1f.5: reg 14 io port: [0xbc40-0xbc7f]
[    0.235479] pci 0000:00:1f.5: reg 18 32bit mmio: [0xf4fff800-0xf4fff9ff]
[    0.235489] pci 0000:00:1f.5: reg 1c 32bit mmio: [0xf4fff400-0xf4fff4ff]
[    0.235523] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.235529] pci 0000:00:1f.5: PME# disabled
[    0.235566] pci 0000:00:1f.6: reg 10 io port: [0xb400-0xb4ff]
[    0.235575] pci 0000:00:1f.6: reg 14 io port: [0xb080-0xb0ff]
[    0.235618] pci 0000:00:1f.6: PME# supported from D0 D3hot D3cold
[    0.235624] pci 0000:00:1f.6: PME# disabled
[    0.235671] pci 0000:01:00.0: reg 10 32bit mmio: [0xfc000000-0xfcffffff]
[    0.235679] pci 0000:01:00.0: reg 14 32bit mmio: [0xd0000000-0xdfffffff]
[    0.235703] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.235765] pci 0000:00:01.0: bridge io port: [0xc000-0xcfff]
[    0.235771] pci 0000:00:01.0: bridge 32bit mmio: [0xfc000000-0xfdffffff]
[    0.235777] pci 0000:00:01.0: bridge 32bit mmio pref: [0xd0000000-0xdfffffff]
[    0.235819] pci 0000:02:01.0: reg 10 32bit mmio: [0xfaffe000-0xfaffffff]
[    0.235866] pci 0000:02:01.0: supports D1 D2
[    0.235870] pci 0000:02:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.235876] pci 0000:02:01.0: PME# disabled
[    0.235915] pci 0000:02:02.0: reg 10 32bit mmio: [0xfaffd000-0xfaffdfff]
[    0.235966] pci 0000:02:02.0: PME# supported from D0 D3hot D3cold
[    0.235972] pci 0000:02:02.0: PME# disabled
[    0.236039] pci 0000:02:04.0: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.236061] pci 0000:02:04.0: supports D1 D2
[    0.236065] pci 0000:02:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.236071] pci 0000:02:04.0: PME# disabled
[    0.236110] pci 0000:02:04.1: reg 10 32bit mmio: [0xfaffc800-0xfaffcfff]
[    0.236120] pci 0000:02:04.1: reg 14 32bit mmio: [0xfaff8000-0xfaffbfff]
[    0.236166] pci 0000:02:04.1: supports D1 D2
[    0.236170] pci 0000:02:04.1: PME# supported from D0 D1 D2 D3hot
[    0.236176] pci 0000:02:04.1: PME# disabled
[    0.236227] pci 0000:00:1e.0: transparent bridge
[    0.236234] pci 0000:00:1e.0: bridge io port: [0xd000-0xefff]
[    0.236241] pci 0000:00:1e.0: bridge 32bit mmio: [0xf6000000-0xfbffffff]
[    0.236277] pci_bus 0000:00: on NUMA node 0
[    0.236284] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.236531] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.236606] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.244772] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    0.244916] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *11
[    0.245059] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
[    0.245201] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 *11)
[    0.245346] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.245498] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.245792] SCSI subsystem initialized
[    0.245827] libata version 3.00 loaded.
[    0.245827] usbcore: registered new interface driver usbfs
[    0.245827] usbcore: registered new interface driver hub
[    0.245827] usbcore: registered new device driver usb
[    0.245827] ACPI: WMI: Mapper loaded
[    0.245827] PCI: Using ACPI for IRQ routing
[    0.256014] Bluetooth: Core ver 2.15
[    0.256048] NET: Registered protocol family 31
[    0.256048] Bluetooth: HCI device and connection manager initialized
[    0.256048] Bluetooth: HCI socket layer initialized
[    0.256048] NetLabel: Initializing
[    0.256048] NetLabel:  domain hash size = 128
[    0.256048] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.256058] NetLabel:  unlabeled traffic allowed by default
[    0.268025] pnp: PnP ACPI init
[    0.268058] ACPI: bus type pnp registered
[    0.280617] pnp 00:02: io resource (0x1000-0x1005) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.280623] pnp 00:02: io resource (0x1008-0x100f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.280727] pnp 00:03: io resource (0x1006-0x1007) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.280733] pnp 00:03: io resource (0x1010-0x105f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.280739] pnp 00:03: io resource (0x1060-0x107f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.281754] pnp: PnP ACPI: found 11 devices
[    0.281758] ACPI: ACPI bus type pnp unregistered
[    0.281764] PnPBIOS: Disabled by ACPI PNP
[    0.281780] system 00:00: iomem range 0x0-0x9fbff could not be reserved
[    0.281785] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
[    0.281791] system 00:00: iomem range 0xc0000-0xcffff could not be reserved
[    0.281796] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[    0.281801] system 00:00: iomem range 0x100000-0x2ffeffff could not be reserved
[    0.281806] system 00:00: iomem range 0x2fff0000-0x2fffffff has been reserved
[    0.281812] system 00:00: iomem range 0xfec10000-0xfec1ffff has been reserved
[    0.281817] system 00:00: iomem range 0xfeda0000-0xfedfffff has been reserved
[    0.281822] system 00:00: iomem range 0xffb00000-0xffbfffff has been reserved
[    0.281827] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
[    0.281832] system 00:00: iomem range 0xfee00000-0xfee0ffff has been reserved
[    0.281844] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.281849] system 00:02: ioport range 0x800-0x80f has been reserved
[    0.281859] system 00:03: ioport range 0xf400-0xf4fe has been reserved
[    0.281865] system 00:03: ioport range 0x1080-0x10bf has been reserved
[    0.281870] system 00:03: ioport range 0x10c0-0x10df has been reserved
[    0.281875] system 00:03: ioport range 0x10e0-0x10ff has been reserved
[    0.281887] system 00:08: ioport range 0x900-0x97f has been reserved
[    0.316646] AppArmor: AppArmor Filesystem Enabled
[    0.316697] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.316702] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
[    0.316709] pci 0000:00:01.0:   MEM window: 0xfc000000-0xfdffffff
[    0.316715] pci 0000:00:01.0:   PREFETCH window: 0xd0000000-0xdfffffff
[    0.316728] pci 0000:02:04.0: CardBus bridge, secondary bus 0000:03
[    0.316732] pci 0000:02:04.0:   IO window: 0x00d000-0x00d0ff
[    0.316739] pci 0000:02:04.0:   IO window: 0x00d400-0x00d4ff
[    0.316745] pci 0000:02:04.0:   PREFETCH window: 0x30000000-0x33ffffff
[    0.316752] pci 0000:02:04.0:   MEM window: 0x38000000-0x3bffffff
[    0.316758] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.316764] pci 0000:00:1e.0:   IO window: 0xd000-0xefff
[    0.316772] pci 0000:00:1e.0:   MEM window: 0xf6000000-0xfbffffff
[    0.316778] pci 0000:00:1e.0:   PREFETCH window: 0x30000000-0x33ffffff
[    0.316797] pci 0000:00:1e.0: setting latency timer to 64
[    0.316807] pci 0000:02:04.0: enabling device (0000 -> 0003)
[    0.316816]   alloc irq_desc for 16 on node -1
[    0.316821]   alloc kstat_irqs on node -1
[    0.316830] pci 0000:02:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.316840] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.316845] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.316850] pci_bus 0000:01: resource 0 io:  [0xc000-0xcfff]
[    0.316854] pci_bus 0000:01: resource 1 mem: [0xfc000000-0xfdffffff]
[    0.316859] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.316864] pci_bus 0000:02: resource 0 io:  [0xd000-0xefff]
[    0.316868] pci_bus 0000:02: resource 1 mem: [0xf6000000-0xfbffffff]
[    0.316873] pci_bus 0000:02: resource 2 pref mem [0x30000000-0x33ffffff]
[    0.316878] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.316882] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.316887] pci_bus 0000:03: resource 0 io:  [0xd000-0xd0ff]
[    0.316892] pci_bus 0000:03: resource 1 io:  [0xd400-0xd4ff]
[    0.316896] pci_bus 0000:03: resource 2 pref mem [0x30000000-0x33ffffff]
[    0.316901] pci_bus 0000:03: resource 3 mem: [0x38000000-0x3bffffff]
[    0.316957] NET: Registered protocol family 2
[    0.317103] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.317622] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.318566] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.320089] Switched to high resolution mode on CPU 0
[    0.319186] TCP: Hash tables configured (established 131072 bind 65536)
[    0.319192] TCP reno registered
[    0.319389] NET: Registered protocol family 1
[    0.319495] Trying to unpack rootfs image as initramfs...
[    0.320929] Switched to high resolution mode on CPU 1
[    0.560655] Freeing initrd memory: 7462k freed
[    0.569417] Simple Boot Flag at 0x79 set to 0x1
[    0.569861] cpufreq-nforce2: No nForce2 chipset.
[    0.569905] Scanning for low memory corruption every 60 seconds
[    0.570054] audit: initializing netlink socket (disabled)
[    0.570079] type=2000 audit(1256688958.569:1): initialized
[    0.579588] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.581744] VFS: Disk quotas dquot_6.5.2
[    0.581840] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.582662] fuse init (API version 7.12)
[    0.582790] msgmni has been set to 1498
[    0.583159] alg: No test for stdrng (krng)
[    0.583181] io scheduler noop registered
[    0.583185] io scheduler anticipatory registered
[    0.583188] io scheduler deadline registered
[    0.583256] io scheduler cfq registered (default)
[    0.583367] pci 0000:01:00.0: Boot video device
[    0.583531] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.583569] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.584049] ACPI: AC Adapter [AC] (on-line)
[    0.584158] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.584548] ACPI: Lid Switch [LID]
[    0.584618] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.584624] ACPI: Power Button [PBTN]
[    0.584695] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.584699] ACPI: Sleep Button [SBTN]
[    0.585432] ACPI: SSDT 2fff320b 0066C (v01   DELL CPU0HTCI 00001001 MSFT 0100000E)
[    0.585449] ACPI Error (dswload-0335): [SMIX] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.585457] ACPI Exception: AE_ALREADY_EXISTS, During name lookup/catalog 20090521 psloop-227
[    0.585469] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU0._PDC] (Node ef80d780), AE_ALREADY_EXISTS
[    0.585480] ACPI: Marking method _PDC as Serialized because of AE_ALREADY_EXISTS error
[    0.585548] processor LNXCPU:00: registered as cooling_device0
[    0.585554] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.585692] ACPI: SSDT 2fff3877 000C6 (v01   DELL CPU1HTCI 00001001 MSFT 0100000E)
[    0.585707] ACPI Error (dswload-0335): [GETC] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.585715] ACPI Exception: AE_ALREADY_EXISTS, During name lookup/catalog 20090521 psloop-227
[    0.585726] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU1._PDC] (Node ef80d7b0), AE_ALREADY_EXISTS
[    0.585736] ACPI: Marking method _PDC as Serialized because of AE_ALREADY_EXISTS error
[    0.585833] processor LNXCPU:01: registered as cooling_device1
[    0.585840] ACPI: Processor [CPU1] (supports 8 throttling states)
[    0.590405] thermal LNXTHERM:01: registered as thermal_zone0
[    0.590420] ACPI: Thermal Zone [THM] (57 C)
[    0.590509] isapnp: Scanning for PnP cards...
[    0.878180] ACPI: Battery Slot [BAT0] (battery present)
[    0.944868] isapnp: No Plug & Play device found
[    0.946631] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.947056]   alloc irq_desc for 17 on node -1
[    0.947060]   alloc kstat_irqs on node -1
[    0.947072] serial 0000:00:1f.6: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.947080] serial 0000:00:1f.6: PCI INT B disabled
[    0.948546] brd: module loaded
[    0.949232] loop: module loaded
[    0.949355] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.949538] ata_piix 0000:00:1f.1: version 2.13
[    0.949553] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    0.949563] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.949628] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.949780] scsi0 : ata_piix
[    0.949927] scsi1 : ata_piix
[    0.950152] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    0.950157] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    0.951598] Fixed MDIO Bus: probed
[    0.951657] PPP generic driver version 2.4.2
[    0.951812] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.951844]   alloc irq_desc for 23 on node -1
[    0.951848]   alloc kstat_irqs on node -1
[    0.951862] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.951884] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.951889] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.951972] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.955895] ehci_hcd 0000:00:1d.7: debug port 1
[    0.955904] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    0.955927] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf4fffc00
[    0.968024] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.968145] usb usb1: configuration #1 chosen from 1 choice
[    0.968191] hub 1-0:1.0: USB hub found
[    0.968205] hub 1-0:1.0: 6 ports detected
[    0.968307] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.968339] uhci_hcd: USB Universal Host Controller Interface driver
[    0.968393] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.968404] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.968410] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.968464] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.968503] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000bf80
[    0.968626] usb usb2: configuration #1 chosen from 1 choice
[    0.968667] hub 2-0:1.0: USB hub found
[    0.968679] hub 2-0:1.0: 2 ports detected
[    0.968750]   alloc irq_desc for 19 on node -1
[    0.968754]   alloc kstat_irqs on node -1
[    0.968762] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.968771] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.968776] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.968828] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.968864] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000bf40
[    0.968975] usb usb3: configuration #1 chosen from 1 choice
[    0.969015] hub 3-0:1.0: USB hub found
[    0.969026] hub 3-0:1.0: 2 ports detected
[    0.969092]   alloc irq_desc for 18 on node -1
[    0.969096]   alloc kstat_irqs on node -1
[    0.969103] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.969111] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.969116] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.969167] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.969201] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000bf20
[    0.969316] usb usb4: configuration #1 chosen from 1 choice
[    0.969355] hub 4-0:1.0: USB hub found
[    0.969366] hub 4-0:1.0: 2 ports detected
[    0.969526] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.969673] i8042.c: Warning: Keylock active.
[    0.972116] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.972128] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.972218] mice: PS/2 mouse device common for all mice
[    0.972425] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.972450] rtc0: alarms up to one day, 114 bytes nvram
[    0.972614] device-mapper: uevent: version 1.0.3
[    0.972807] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.972940] device-mapper: multipath: version 1.1.0 loaded
[    0.972950] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.973175] EISA: Probing bus 0 at eisa.0
[    0.973183] Cannot allocate resource for EISA slot 1
[    0.973206] EISA: Detected 0 cards.
[    0.973393] cpuidle: using governor ladder
[    0.973399] cpuidle: using governor menu
[    0.974188] TCP cubic registered
[    0.974373] NET: Registered protocol family 10
[    0.975070] lo: Disabled Privacy Extensions
[    0.975596] NET: Registered protocol family 17
[    0.975627] Bluetooth: L2CAP ver 2.13
[    0.975630] Bluetooth: L2CAP socket layer initialized
[    0.975635] Bluetooth: SCO (Voice Link) ver 0.6
[    0.975638] Bluetooth: SCO socket layer initialized
[    0.975713] Bluetooth: RFCOMM TTY layer initialized
[    0.975721] Bluetooth: RFCOMM socket layer initialized
[    0.975726] Bluetooth: RFCOMM ver 1.11
[    0.975783] Using IPI No-Shortcut mode
[    0.975909] PM: Resume from disk failed.
[    0.975928] registered taskstats version 1
[    0.976132]   Magic number: 13:843:254
[    0.976181] uhci_hcd 0000:00:1d.2: hash matches
[    0.976232] rtc_cmos 00:06: setting system clock to 2009-10-28 00:15:59 UTC (1256688959)
[    0.976237] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.976240] EDD information not available.
[    0.976507] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.112470] ata1.00: ATAPI: SONY CD-RW/DVD-ROM CRX830E, KDK9, max UDMA/33
[    1.120686] ata2.00: ATA-6: HTS721060G9AT00, MC3OA51A, max UDMA/100
[    1.120691] ata2.00: 117210240 sectors, multi 8: LBA48 
[    1.128245] ata1.00: configured for UDMA/33
[    1.136526] ata2.00: configured for UDMA/100
[    1.137410] scsi 0:0:0:0: CD-ROM            SONY     CDRW/DVD CRX830E KDK9 PQ: 0 ANSI: 5
[    1.140267] sr0: scsi3-mmc drive: 0x/24x writer cd/rw xa/form2 cdda tray
[    1.140273] Uniform CD-ROM driver Revision: 3.20
[    1.140410] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.140493] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.140624] scsi 1:0:0:0: Direct-Access     ATA      HTS721060G9AT00  MC3O PQ: 0 ANSI: 5
[    1.140813] sd 1:0:0:0: [sda] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    1.140824] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    1.140909] sd 1:0:0:0: [sda] Write Protect is off
[    1.140914] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.140951] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.141159]  sda: sda1 sda2 < sda5 >
[    1.175114] sd 1:0:0:0: [sda] Attached SCSI disk
[    1.175154] Freeing unused kernel memory: 540k freed
[    1.175904] Write protecting the kernel text: 4568k
[    1.175982] Write protecting the kernel read-only data: 1836k
[    1.395386] Linux agpgart interface v0.103
[    1.401786] agpgart-intel 0000:00:00.0: Intel 855GM Chipset
[    1.457391] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:1b/device:1c/input/input5
[    1.457477] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[    1.528438] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe0000000
[    1.543798] b44 0000:02:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.617112] ssb: Sonics Silicon Backplane found on PCI device 0000:02:01.0
[    1.617165] ohci1394 0000:02:04.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.617171] b44.c:v2.0
[    1.638076] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:0f:1f:1c:74:2a
[    1.676057] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[faffc800-faffcfff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    2.768526] PM: Starting manual resume from disk
[    2.768533] PM: Resume from partition 8:5
[    2.768536] PM: Checking hibernation image.
[    2.768748] PM: Resume from disk failed.
[    2.793925] EXT4-fs (sda1): barriers enabled
[    2.844395] kjournald2 starting: pid 356, dev sda1:8, commit interval 5 seconds
[    2.844417] EXT4-fs (sda1): delayed allocation enabled
[    2.844424] EXT4-fs: file extents enabled
[    2.852496] EXT4-fs: mballoc enabled
[    2.852519] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    2.949208] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[344fc00016c8aca1]
[    3.603207] type=1505 audit(1256688962.125:2): operation="profile_load" pid=379 name=/usr/share/gdm/guest-session/Xsession
[    3.607002] type=1505 audit(1256688962.127:3): operation="profile_load" pid=380 name=/sbin/dhclient3
[    3.607596] type=1505 audit(1256688962.127:4): operation="profile_load" pid=380 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    3.607922] type=1505 audit(1256688962.127:5): operation="profile_load" pid=380 name=/usr/lib/connman/scripts/dhclient-script
[    3.660489] type=1505 audit(1256688962.183:6): operation="profile_load" pid=381 name=/usr/bin/evince
[    3.670229] type=1505 audit(1256688962.191:7): operation="profile_load" pid=381 name=/usr/bin/evince-previewer
[    3.675874] type=1505 audit(1256688962.195:8): operation="profile_load" pid=381 name=/usr/bin/evince-thumbnailer
[    3.693930] type=1505 audit(1256688962.215:9): operation="profile_load" pid=383 name=/usr/lib/cups/backend/cups-pdf
[    3.694630] type=1505 audit(1256688962.215:10): operation="profile_load" pid=383 name=/usr/sbin/cupsd
[    4.450522] Adding 2249060k swap on /dev/sda5.  Priority:-1 extents:1 across:2249060k 
[    4.837511] EXT4-fs (sda1): internal journal on sda1:8
[    4.857037] udev: starting version 147
[    6.178294] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x254ab1, caps: 0x804713/0x0
[    6.181358] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[    6.185183] intel_rng: FWH not detected
[    6.215411] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    6.226099] dell-wmi: No known WMI GUID found
[    6.231467] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[    6.355676] lib80211: common routines for IEEE802.11 drivers
[    6.355682] lib80211_crypt: registered algorithm 'NULL'
[    6.421441] ieee80211: 802.11 data/management/control stack, git-1.1.13
[    6.421448] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[    6.444824] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[    6.444831] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[    6.445030] ipw2200 0000:02:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    6.445545] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[    6.445644] ipw2200 0000:02:02.0: firmware: requesting ipw2200-bss.fw
[    7.211060] nvidia: module license 'NVIDIA' taints kernel.
[    7.211068] Disabling lock debugging due to kernel taint
[    7.467608]   alloc irq_desc for 20 on node -1
[    7.467613]   alloc kstat_irqs on node -1
[    7.467624] nvidia 0000:01:00.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    7.467962] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.20  Thu Jun 25 19:23:24 PDT 2009
[    7.655359] lp: driver loaded but no devices found
[    7.883789] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[    8.160614] ip_tables: (C) 2000-2006 Netfilter Core Team
[    8.417023] yenta_cardbus 0000:02:04.0: CardBus bridge found [1028:015f]
[    8.417051] yenta_cardbus 0000:02:04.0: Using CSCINT to route CSC interrupts to PCI
[    8.417057] yenta_cardbus 0000:02:04.0: Routing CardBus interrupts to PCI
[    8.417067] yenta_cardbus 0000:02:04.0: TI: mfunc 0x00001002, devctl 0x64
[    8.648767] yenta_cardbus 0000:02:04.0: ISA IRQ mask 0x0cf8, PCI irq 16
[    8.648774] yenta_cardbus 0000:02:04.0: Socket status: 30000086
[    8.648780] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #02 to #06
[    8.648792] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge I/O window: 0xd000 - 0xefff
[    8.648798] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xd000-0xefff: clean.
[    8.649397] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge Memory window: 0xf6000000 - 0xfbffffff
[    8.649402] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[    9.095486] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    9.095574] Intel ICH 0000:00:1f.5: setting latency timer to 64
[    9.205719] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[    9.206739] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[    9.207175] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[    9.207544] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[    9.208164] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[    9.525801] __ratelimit: 3 callbacks suppressed
[    9.525807] type=1505 audit(1256688968.048:12): operation="profile_replace" pid=756 name=/usr/share/gdm/guest-session/Xsession
[    9.528788] type=1505 audit(1256688968.048:13): operation="profile_replace" pid=757 name=/sbin/dhclient3
[    9.529467] type=1505 audit(1256688968.052:14): operation="profile_replace" pid=757 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    9.529864] type=1505 audit(1256688968.052:15): operation="profile_replace" pid=757 name=/usr/lib/connman/scripts/dhclient-script
[    9.537819] type=1505 audit(1256688968.060:16): operation="profile_replace" pid=758 name=/usr/bin/evince
[    9.547792] type=1505 audit(1256688968.068:17): operation="profile_replace" pid=758 name=/usr/bin/evince-previewer
[    9.554732] type=1505 audit(1256688968.076:18): operation="profile_replace" pid=758 name=/usr/bin/evince-thumbnailer
[    9.565481] type=1505 audit(1256688968.088:19): operation="profile_replace" pid=762 name=/usr/lib/cups/backend/cups-pdf
[    9.566189] type=1505 audit(1256688968.088:20): operation="profile_replace" pid=762 name=/usr/sbin/cupsd
[    9.571437] type=1505 audit(1256688968.092:21): operation="profile_replace" pid=763 name=/usr/sbin/tcpdump
[    9.920027] intel8x0_measure_ac97_clock: measured 54274 usecs (2615 samples)
[    9.920033] intel8x0: clocking to 48000
[   13.649295] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.274803] ppdev: user-space parallel port driver
[   17.450407] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[   17.450442] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
[   17.450525] nvidia 0000:01:00.0: putting AGP V2 device into 4x mode
[   18.883277] CPU0 attaching NULL sched-domain.
[   18.883291] CPU1 attaching NULL sched-domain.
[   18.900105] CPU0 attaching sched-domain:
[   18.900112]  domain 0: span 0-1 level SIBLING
[   18.900117]   groups: 0 1
[   18.900129] CPU1 attaching sched-domain:
[   18.900133]  domain 0: span 0-1 level SIBLING
[   18.900137]   groups: 1 0
[   22.094398] CPU0 attaching NULL sched-domain.
[   22.094408] CPU1 attaching NULL sched-domain.
[   22.112112] CPU0 attaching sched-domain:
[   22.112119]  domain 0: span 0-1 level SIBLING
[   22.112124]   groups: 0 1
[   22.112136] CPU1 attaching sched-domain:
[   22.112140]  domain 0: span 0-1 level SIBLING
[   22.112144]   groups: 1 0
[   24.708017] eth1: no IPv6 routers present
[   48.678862] lib80211_crypt: registered algorithm 'CCMP'
[   48.754725] padlock: VIA PadLock not detected.
[  841.288037] usb 2-1: new low speed USB device using uhci_hcd and address 2
[  841.464137] usb 2-1: configuration #1 chosen from 1 choice
[  841.534750] usbcore: registered new interface driver hiddev
[  841.547339] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input7
[  841.547481] generic-usb 0003:046D:C016.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.0-1/input0
[  841.547511] usbcore: registered new interface driver usbhid
[  841.547516] usbhid: v2.6:USB HID core driver

```

I think powernowd is having trouble:
```
brainrecall@jason:~$ modprobe powernowd
FATAL: Module powernowd not found.

```
```
brainrecall@jason:/etc/init.d$ sudo /etc/init.d/powernowd start
 * Starting powernowd...                                                        
 * CPU frequency scaling not supported...                                [ OK ] 
```

---

### Post by ecarcole on 2009-10-29
I did a fresh install of Ubuntu 9.10 amd64 in three computers, and only with DELL Latitude D630 (Intel Core Duo) I have a similar problem. Before I used Ubuntu 9.04 and I had no problem. 

I installed powernowd, but is not working. The maximum speed is 2.20GHz, but most of the time works at 1.60 GHz when I choose "Performance". If try to set the speed at 2.20Ghz the CPU Frequency monitor does not allow me to do it.

The output of modprobe: FATAL: Module powernowd not found.

The output of sudo /etc/init.d/powernowd start:  * Starting powernowd...   
Seems to provide no error. If I try modprobe again I get FATAL... again.

I provide output of dmesg in a file.

I need fastest speed since I am running calculations all the time...

---

### Post by MartyBuntu on 2009-10-29
> **Brain_Recall said:**
> I just upgraded my craptastic Dell Inspiron 5150 with Ubuntu 9.10 RC. The first major issue is CPU Frequency Scaling no longer works, as reported from the CPU Frequency Scaling Monitor. This had worked perfectly under Ubuntu 9.04, so I guess the switch from hal to DeviceKit is to blame.

The 5150 in question uses a [Mobile Pentium 4]("http://en.wikipedia.org/wiki/Pentium_4#Mobile_Pentium_4") @ 2.8GHz. Essentially, it's a battery-powered toaster oven. I need scaling to work, otherwise [the 5150's notoriously crappy hardware]("http://en.wikipedia.org/wiki/Dell_Inspiron#Problems") will catch up to me.

Does anyone have any suggestions?

I'll be following this thread closely as I have the exact same setup as you. I'm currently on 9.04.

I hope this works out for you.

---

### Post by Brain_Recall on 2009-10-29
I did a fresh install of 9.10 final. No difference. powernowd, cpufreqd, and cpudyn don't work.

Are there ways to poke at DeviceKit Power to figure out what it thinks is going on?

---

### Post by MrEgg on 2009-11-01
I am following this thread as well, as I am experiencing the exact same problem with my 5150.

Active cpu governor is userspace by default.

/sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors returns:
conservative ondemand userspace powersave performance

Governor can be changed by doing the following, but it has absolutely no effect on the actual frequency (which stays at 100%) :
sudo echo powersave > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

---

### Post by skalka on 2009-11-01
I have the same problem, everything was fine on Jaunty, no scaling with Karmic. I have a Intel Core Duo 2, if I add the applet on the panel I get "CPU frequency scaling unsupported" e the applet shows me the frequency, actually my proc always works at the maximum (2.4 ghz). I hope we fine a solution, I don't want to come back to Jaunty.

---

### Post by skalka on 2009-11-01
I've solved, last month I've sent my pavilion to Hp, I had problems with the motherboard and they've changed with a new one and they changed bios version too. I've downloaded a new bios firmware from hp site and now I can scale cpu frequency.

---

### Post by zim2dive on 2009-11-01
Same problem here... cannot reach my max CPU fgrequency under 9.10


G31M-ES2L mobo, Intel E5200. I can only get `1.2 and 19.GHz, not 2.5.
```
>dmesg
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bfee0000 (usable)
[    0.000000]  BIOS-e820: 00000000bfee0000 - 00000000bfee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfee3000 - 00000000bfef0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bfef0000 - 00000000bff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000c0000000 - 00000000d0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0xbfee0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CDFFF write-protect
[    0.000000]   CE000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-through
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F00000000 write-back
[    0.000000]   1 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   2 base 100000000 mask FC0000000 write-back
[    0.000000]   3 base 0BFF00000 mask FFFF00000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000bff00000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bfee0000 (usable)
[    0.000000]  modified: 00000000bfee0000 - 00000000bfee3000 (ACPI NVS)
[    0.000000]  modified: 00000000bfee3000 - 00000000bfef0000 (ACPI data)
[    0.000000]  modified: 00000000bfef0000 - 00000000bff00000 (reserved)
[    0.000000]  modified: 00000000c0000000 - 00000000d0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 37868000 - 37fef34a
[    0.000000] Allocated new RAMDISK: 008ad000 - 0103434a
[    0.000000] Move RAMDISK from 0000000037868000 - 0000000037fef349 to 008ad000 - 01034349
[    0.000000] ACPI: RSDP 000f6bf0 00014 (v00 GBT   )
[    0.000000] ACPI: RSDT bfee3040 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: FACP bfee30c0 00074 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: DSDT bfee3180 040E8 (v01 GBT    GBTUACPI 00001000 MSFT 0100000C)
[    0.000000] ACPI: FACS bfee0000 00040
[    0.000000] ACPI: HPET bfee73c0 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 00000098)
[    0.000000] ACPI: MCFG bfee7440 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: APIC bfee72c0 00084 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: SSDT bfee7ae0 003AB (v01  PmRef    CpuPm 00003000 INTL 20040311)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2182MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
[    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #5 [00008a9000 - 00008ac0f6]              BRK ==> [00008a9000 - 00008ac0f6]
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #7 [00008ad000 - 000103434a]      NEW RAMDISK ==> [00008ad000 - 000103434a]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00f5200] f5200
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x000bfee0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000bfee0
[    0.000000] On node 0 totalpages: 786043
[    0.000000] free_area_init_node: node 0, pgdat c0784900, node_mem_map c1035000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4366 pages used for memmap
[    0.000000]   HighMem zone: 554452 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
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
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at d0000000 (gap: d0000000:2ec00000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c2845000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 779901
[    0.000000] Kernel command line: root=UUID=4aa5b8ac-44a3-4673-ba51-fcf6c8a8e43e ro quiet splash 
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] allocated 15722880 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:000bfee0)
[    0.000000] Memory: 3086644k/3144576k available (4565k kernel code, 56616k reserved, 2143k data, 540k init, 2235272k highmem)
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
[    0.000000] Detected 2499.519 MHz processor.
[    0.001391] Console: colour VGA+ 80x25
[    0.001395] console [tty0] enabled
[    0.001533] hpet clockevent registered
[    0.001536] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.001542] Calibrating delay loop (skipped), value calculated using timer frequency.. 4999.03 BogoMIPS (lpj=9998076)
[    0.001559] Security Framework initialized
[    0.001579] AppArmor: AppArmor initialized
[    0.001587] Mount-cache hash table entries: 512
[    0.001712] Initializing cgroup subsys ns
[    0.001717] Initializing cgroup subsys cpuacct
[    0.001722] Initializing cgroup subsys memory
[    0.001729] Initializing cgroup subsys freezer
[    0.001731] Initializing cgroup subsys net_cls
[    0.001746] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.001749] CPU: L2 cache: 2048K
[    0.001752] CPU: Physical Processor ID: 0
[    0.001753] CPU: Processor Core ID: 0
[    0.001757] mce: CPU supports 6 MCE banks
[    0.001765] CPU0: Thermal monitoring enabled (TM2)
[    0.001769] using mwait in idle threads.
[    0.001775] Performance Counters: Core2 events, Intel PMU driver.
[    0.001783] ... version:                 2
[    0.001785] ... bit width:               40
[    0.001787] ... generic counters:        2
[    0.001789] ... value mask:              000000ffffffffff
[    0.001791] ... max period:              000000007fffffff
[    0.001793] ... fixed-purpose counters:  3
[    0.001795] ... counter mask:            0000000700000003
[    0.001801] Checking 'hlt' instruction... OK.
[    0.019030] ACPI: Core revision 20090521
[    0.026123] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.065806] CPU0: Intel Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz stepping 0a
[    0.068001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 4999.95 BogoMIPS (lpj=9999908)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] mce: CPU supports 6 MCE banks
[    0.004000] CPU1: Thermal monitoring enabled (TM2)
[    0.004000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.153672] CPU1: Intel Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz stepping 0a
[    0.153688] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.156021] Brought up 2 CPUs
[    0.156024] Total of 2 processors activated (9998.99 BogoMIPS).
[    0.156069] CPU0 attaching sched-domain:
[    0.156072]  domain 0: span 0-1 level MC
[    0.156075]   groups: 0 1
[    0.156080] CPU1 attaching sched-domain:
[    0.156083]  domain 0: span 0-1 level MC
[    0.156085]   groups: 1 0
[    0.156163] Booting paravirtualized kernel on bare hardware
[    0.156232] regulator: core version 0.5
[    0.156232] Time: 20:50:57  Date: 11/01/09
[    0.156232] NET: Registered protocol family 16
[    0.156232] EISA bus registered
[    0.156232] ACPI: bus type pci registered
[    0.156293] PCI: MCFG configuration 0: base c0000000 segment 0 buses 0 - 255
[    0.156296] PCI: MCFG area at c0000000 reserved in E820
[    0.156298] PCI: Using MMCONFIG for extended config space
[    0.156300] PCI: Using configuration type 1 for base access
[    0.157394] bio: create slab <bio-0> at 0
[    0.160374] ACPI: EC: Look up EC in DSDT
[    0.165607] ACPI: Interpreter enabled
[    0.165621] ACPI: (supports S0 S3 S4 S5)
[    0.165645] ACPI: Using IOAPIC for interrupt routing
[    0.170071] ACPI: No dock devices found.
[    0.170166] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.170280] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.170283] pci 0000:00:01.0: PME# disabled
[    0.170350] pci 0000:00:1b.0: reg 10 64bit mmio: [0xe5100000-0xe5103fff]
[    0.170394] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.170399] pci 0000:00:1b.0: PME# disabled
[    0.170460] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.170464] pci 0000:00:1c.0: PME# disabled
[    0.170526] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.170531] pci 0000:00:1c.1: PME# disabled
[    0.170582] pci 0000:00:1d.0: reg 20 io port: [0xe000-0xe01f]
[    0.170632] pci 0000:00:1d.1: reg 20 io port: [0xe100-0xe11f]
[    0.170683] pci 0000:00:1d.2: reg 20 io port: [0xe200-0xe21f]
[    0.170733] pci 0000:00:1d.3: reg 20 io port: [0xe300-0xe31f]
[    0.170782] pci 0000:00:1d.7: reg 10 32bit mmio: [0xe5104000-0xe51043ff]
[    0.170948] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[    0.170952] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.170956] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0800 (mask 000f)
[    0.170960] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0290 (mask 000f)
[    0.171011] pci 0000:00:1f.2: reg 10 io port: [0x00-0x07]
[    0.171018] pci 0000:00:1f.2: reg 14 io port: [0x00-0x03]
[    0.171024] pci 0000:00:1f.2: reg 18 io port: [0x00-0x07]
[    0.171031] pci 0000:00:1f.2: reg 1c io port: [0x00-0x03]
[    0.171037] pci 0000:00:1f.2: reg 20 io port: [0xf000-0xf00f]
[    0.171062] pci 0000:00:1f.2: PME# supported from D3hot
[    0.171066] pci 0000:00:1f.2: PME# disabled
[    0.171114] pci 0000:00:1f.3: reg 20 io port: [0x500-0x51f]
[    0.171169] pci 0000:01:00.0: reg 10 32bit mmio: [0xe2000000-0xe2ffffff]
[    0.171179] pci 0000:01:00.0: reg 14 64bit mmio: [0xd0000000-0xdfffffff]
[    0.171188] pci 0000:01:00.0: reg 1c 64bit mmio: [0xe0000000-0xe1ffffff]
[    0.171195] pci 0000:01:00.0: reg 24 io port: [0xc000-0xc07f]
[    0.171201] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x07ffff]
[    0.171269] pci 0000:00:01.0: bridge io port: [0xc000-0xcfff]
[    0.171273] pci 0000:00:01.0: bridge 32bit mmio: [0xe0000000-0xe3ffffff]
[    0.171278] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.171320] pci 0000:00:1c.0: bridge io port: [0xb000-0xbfff]
[    0.171374] pci 0000:03:00.0: reg 10 io port: [0xd000-0xd0ff]
[    0.171395] pci 0000:03:00.0: reg 18 64bit mmio: [0xe5010000-0xe5010fff]
[    0.171410] pci 0000:03:00.0: reg 20 64bit mmio: [0xe5000000-0xe500ffff]
[    0.171419] pci 0000:03:00.0: reg 30 32bit mmio: [0x000000-0x00ffff]
[    0.171461] pci 0000:03:00.0: supports D1 D2
[    0.171463] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.171468] pci 0000:03:00.0: PME# disabled
[    0.171528] pci 0000:00:1c.1: bridge io port: [0xd000-0xdfff]
[    0.171533] pci 0000:00:1c.1: bridge 32bit mmio: [0xe4000000-0xe4ffffff]
[    0.171539] pci 0000:00:1c.1: bridge 64bit mmio pref: [0xe5000000-0xe50fffff]
[    0.171589] pci 0000:00:1e.0: transparent bridge
[    0.171593] pci 0000:00:1e.0: bridge io port: [0xa000-0xafff]
[    0.171618] pci_bus 0000:00: on NUMA node 0
[    0.171622] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.171810] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.171872] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[    0.171946] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.182258] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.182358] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.182457] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.182556] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.182654] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.182753] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.182852] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.182953] ACPI: PCI Interrupt Link [LNK1] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[    0.183143] SCSI subsystem initialized
[    0.183177] libata version 3.00 loaded.
[    0.183177] usbcore: registered new interface driver usbfs
[    0.183177] usbcore: registered new interface driver hub
[    0.183177] usbcore: registered new device driver usb
[    0.183177] ACPI: WMI: Mapper loaded
[    0.183177] PCI: Using ACPI for IRQ routing
[    0.192011] Bluetooth: Core ver 2.15
[    0.192032] NET: Registered protocol family 31
[    0.192032] Bluetooth: HCI device and connection manager initialized
[    0.192032] Bluetooth: HCI socket layer initialized
[    0.192032] NetLabel: Initializing
[    0.192032] NetLabel:  domain hash size = 128
[    0.192032] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.192051] NetLabel:  unlabeled traffic allowed by default
[    0.192092] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.192100] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.208014] pnp: PnP ACPI init
[    0.208028] ACPI: bus type pnp registered
[    0.210728] pnp: PnP ACPI: found 14 devices
[    0.210730] ACPI: ACPI bus type pnp unregistered
[    0.210735] PnPBIOS: Disabled by ACPI PNP
[    0.210746] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.210749] system 00:01: ioport range 0x290-0x29f has been reserved
[    0.210752] system 00:01: ioport range 0x800-0x87f has been reserved
[    0.210755] system 00:01: ioport range 0x290-0x294 has been reserved
[    0.210758] system 00:01: ioport range 0x880-0x88f has been reserved
[    0.210768] system 00:0a: ioport range 0x400-0x4cf could not be reserved
[    0.210774] system 00:0b: iomem range 0xc0000000-0xcfffffff has been reserved
[    0.210780] system 00:0c: iomem range 0xce000-0xcffff has been reserved
[    0.210783] system 00:0c: iomem range 0xf0000-0xf7fff could not be reserved
[    0.210787] system 00:0c: iomem range 0xf8000-0xfbfff could not be reserved
[    0.210790] system 00:0c: iomem range 0xfc000-0xfffff could not be reserved
[    0.210793] system 00:0c: iomem range 0xbfee0000-0xbfefffff could not be reserved
[    0.210796] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    0.210799] system 00:0c: iomem range 0x100000-0xbfedffff could not be reserved
[    0.210803] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.210806] system 00:0c: iomem range 0xfed13000-0xfed1dfff has been reserved
[    0.210809] system 00:0c: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.210812] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.210815] system 00:0c: iomem range 0xffb00000-0xffb7ffff has been reserved
[    0.210818] system 00:0c: iomem range 0xfff00000-0xffffffff has been reserved
[    0.210822] system 00:0c: iomem range 0xe0000-0xeffff has been reserved
[    0.245485] AppArmor: AppArmor Filesystem Enabled
[    0.245527] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.245530] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
[    0.245535] pci 0000:00:01.0:   MEM window: 0xe0000000-0xe3ffffff
[    0.245539] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.245544] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.245548] pci 0000:00:1c.0:   IO window: 0xb000-0xbfff
[    0.245553] pci 0000:00:1c.0:   MEM window: disabled
[    0.245556] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.245561] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    0.245564] pci 0000:00:1c.1:   IO window: 0xd000-0xdfff
[    0.245570] pci 0000:00:1c.1:   MEM window: 0xe4000000-0xe4ffffff
[    0.245574] pci 0000:00:1c.1:   PREFETCH window: 0x000000e5000000-0x000000e50fffff
[    0.245581] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:04
[    0.245584] pci 0000:00:1e.0:   IO window: 0xa000-0xafff
[    0.245589] pci 0000:00:1e.0:   MEM window: disabled
[    0.245593] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.245603]   alloc irq_desc for 16 on node -1
[    0.245605]   alloc kstat_irqs on node -1
[    0.245610] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.245614] pci 0000:00:01.0: setting latency timer to 64
[    0.245622] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.245626] pci 0000:00:1c.0: setting latency timer to 64
[    0.245633]   alloc irq_desc for 17 on node -1
[    0.245635]   alloc kstat_irqs on node -1
[    0.245639] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.245643] pci 0000:00:1c.1: setting latency timer to 64
[    0.245649] pci 0000:00:1e.0: setting latency timer to 64
[    0.245654] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.245657] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.245659] pci_bus 0000:01: resource 0 io:  [0xc000-0xcfff]
[    0.245662] pci_bus 0000:01: resource 1 mem: [0xe0000000-0xe3ffffff]
[    0.245665] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.245668] pci_bus 0000:02: resource 0 io:  [0xb000-0xbfff]
[    0.245671] pci_bus 0000:03: resource 0 io:  [0xd000-0xdfff]
[    0.245674] pci_bus 0000:03: resource 1 mem: [0xe4000000-0xe4ffffff]
[    0.245676] pci_bus 0000:03: resource 2 pref mem [0xe5000000-0xe50fffff]
[    0.245679] pci_bus 0000:04: resource 0 io:  [0xa000-0xafff]
[    0.245682] pci_bus 0000:04: resource 3 io:  [0x00-0xffff]
[    0.245685] pci_bus 0000:04: resource 4 mem: [0x000000-0xffffffff]
[    0.245718] NET: Registered protocol family 2
[    0.245818] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.246134] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.246575] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.246801] TCP: Hash tables configured (established 131072 bind 65536)
[    0.246804] TCP reno registered
[    0.246879] NET: Registered protocol family 1
[    0.246939] Trying to unpack rootfs image as initramfs...
[    0.460947] Freeing initrd memory: 7708k freed
[    0.464823] cpufreq-nforce2: No nForce2 chipset.
[    0.464853] Scanning for low memory corruption every 60 seconds
[    0.464956] audit: initializing netlink socket (disabled)
[    0.464972] type=2000 audit(1257108657.464:1): initialized
[    0.474488] highmem bounce pool size: 64 pages
[    0.474493] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.476086] VFS: Disk quotas dquot_6.5.2
[    0.476152] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.476746] fuse init (API version 7.12)
[    0.476837] msgmni has been set to 1679
[    0.477053] alg: No test for stdrng (krng)
[    0.477068] io scheduler noop registered
[    0.477070] io scheduler anticipatory registered
[    0.477072] io scheduler deadline registered
[    0.477124] io scheduler cfq registered (default)
[    0.477227] pci 0000:01:00.0: Boot video device
[    0.477335]   alloc irq_desc for 24 on node -1
[    0.477338]   alloc kstat_irqs on node -1
[    0.477347] pcieport-driver 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.477354] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    0.477454]   alloc irq_desc for 25 on node -1
[    0.477456]   alloc kstat_irqs on node -1
[    0.477463] pcieport-driver 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.477472] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.477589]   alloc irq_desc for 26 on node -1
[    0.477591]   alloc kstat_irqs on node -1
[    0.477598] pcieport-driver 0000:00:1c.1: irq 26 for MSI/MSI-X
[    0.477607] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    0.477697] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.477776] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.477920] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.477924] ACPI: Power Button [PWRF]
[    0.477978] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.477981] ACPI: Power Button [PWRB]
[    0.478462] ACPI: SSDT bfee74c0 0022A (v01  PmRef  Cpu0Ist 00003000 INTL 20040311)
[    0.478666] processor LNXCPU:00: registered as cooling_device0
[    0.478670] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.478869] ACPI: SSDT bfee7980 00152 (v01  PmRef  Cpu1Ist 00003000 INTL 20040311)
[    0.479094] processor LNXCPU:01: registered as cooling_device1
[    0.479098] ACPI: Processor [CPU1] (supports 8 throttling states)
[    0.480786] isapnp: Scanning for PnP cards...
[    0.501765] Switched to high resolution mode on CPU 1
[    0.504057] Switched to high resolution mode on CPU 0
[    0.833761] isapnp: No Plug & Play device found
[    0.834944] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.835044] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.835421] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.836556] brd: module loaded
[    0.837039] loop: module loaded
[    0.837108] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.837213] ata_piix 0000:00:1f.2: version 2.13
[    0.837228]   alloc irq_desc for 19 on node -1
[    0.837230]   alloc kstat_irqs on node -1
[    0.837236] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.837241] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.837276] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.837332] scsi0 : ata_piix
[    0.837408] scsi1 : ata_piix
[    0.838047] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    0.838051] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    0.838928] Fixed MDIO Bus: probed
[    0.838964] PPP generic driver version 2.4.2
[    0.839048] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.839067]   alloc irq_desc for 23 on node -1
[    0.839069]   alloc kstat_irqs on node -1
[    0.839074] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.839084] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.839087] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.839137] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.843049] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.843062] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xe5104000
[    0.856015] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.856117] usb usb1: configuration #1 chosen from 1 choice
[    0.856169] hub 1-0:1.0: USB hub found
[    0.856183] hub 1-0:1.0: 8 ports detected
[    0.856247] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.856263] uhci_hcd: USB Universal Host Controller Interface driver
[    0.856284] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.856290] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.856293] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.856324] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.856347] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000e000
[    0.856425] usb usb2: configuration #1 chosen from 1 choice
[    0.856453] hub 2-0:1.0: USB hub found
[    0.856459] hub 2-0:1.0: 2 ports detected
[    0.856509] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.856515] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.856519] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.856554] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.856583] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e100
[    0.856661] usb usb3: configuration #1 chosen from 1 choice
[    0.856694] hub 3-0:1.0: USB hub found
[    0.856700] hub 3-0:1.0: 2 ports detected
[    0.856746]   alloc irq_desc for 18 on node -1
[    0.856748]   alloc kstat_irqs on node -1
[    0.856753] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.856759] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.856762] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.856796] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.856824] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e200
[    0.856902] usb usb4: configuration #1 chosen from 1 choice
[    0.856929] hub 4-0:1.0: USB hub found
[    0.856935] hub 4-0:1.0: 2 ports detected
[    0.856979] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.856985] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.856988] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.857019] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.857047] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000e300
[    0.857124] usb usb5: configuration #1 chosen from 1 choice
[    0.857151] hub 5-0:1.0: USB hub found
[    0.857157] hub 5-0:1.0: 2 ports detected
[    0.857264] PNP: No PS/2 controller found. Probing ports directly.
[    0.857619] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.857628] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.857704] mice: PS/2 mouse device common for all mice
[    0.857847] rtc_cmos 00:04: RTC can wake from S4
[    0.857889] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.857912] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.858014] device-mapper: uevent: version 1.0.3
[    0.858109] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.858172] device-mapper: multipath: version 1.1.0 loaded
[    0.858174] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.858283] EISA: Probing bus 0 at eisa.0
[    0.858310] EISA: Detected 0 cards.
[    0.858385] cpuidle: using governor ladder
[    0.858388] cpuidle: using governor menu
[    0.858912] TCP cubic registered
[    0.859076] NET: Registered protocol family 10
[    0.859556] lo: Disabled Privacy Extensions
[    0.859911] NET: Registered protocol family 17
[    0.859930] Bluetooth: L2CAP ver 2.13
[    0.859932] Bluetooth: L2CAP socket layer initialized
[    0.859935] Bluetooth: SCO (Voice Link) ver 0.6
[    0.859937] Bluetooth: SCO socket layer initialized
[    0.859960] Bluetooth: RFCOMM TTY layer initialized
[    0.859963] Bluetooth: RFCOMM socket layer initialized
[    0.859965] Bluetooth: RFCOMM ver 1.11
[    0.861703] Using IPI No-Shortcut mode
[    0.861796] PM: Resume from disk failed.
[    0.861810] registered taskstats version 1
[    0.861926]   Magic number: 1:16:851
[    0.861998] rtc_cmos 00:04: setting system clock to 2009-11-01 20:50:58 UTC (1257108658)
[    0.862002] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.862004] EDD information not available.
[    1.020333] ata1.01: HPA unlocked: 1953523055 -> 1953525168, native 1953525168
[    1.020338] ata1.01: ATA-8: WDC WD10EADS-00L5B1, 01.01A01, max UDMA/133
[    1.020342] ata1.01: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.020458] ata2.01: ATA-7: SAMSUNG HD103SI, 1AG01118, max UDMA7
[    1.020462] ata2.01: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.028361] ata2.01: configured for UDMA/133
[    1.036734] ata1.01: configured for UDMA/133
[    1.036878] scsi 0:0:1:0: Direct-Access     ATA      WDC WD10EADS-00L 01.0 PQ: 0 ANSI: 5
[    1.037005] sd 0:0:1:0: Attached scsi generic sg0 type 0
[    1.037043] sd 0:0:1:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.037091] sd 0:0:1:0: [sda] Write Protect is off
[    1.037094] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
[    1.037119] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.037247]  sda:
[    1.037399] scsi 1:0:1:0: Direct-Access     ATA      SAMSUNG HD103SI  1AG0 PQ: 0 ANSI: 5
[    1.037502] sd 1:0:1:0: Attached scsi generic sg1 type 0
[    1.037536] sd 1:0:1:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.037584] sd 1:0:1:0: [sdb] Write Protect is off
[    1.037587] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    1.037611] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.037731]  sdb: sdb1
[    1.042781] sd 1:0:1:0: [sdb] Attached SCSI disk
[    1.059999]  sda1 sda2 < sda5 >
[    1.082251] sd 0:0:1:0: [sda] Attached SCSI disk
[    1.082267] Freeing unused kernel memory: 540k freed
[    1.082532] Write protecting the kernel text: 4568k
[    1.082578] Write protecting the kernel read-only data: 1836k
[    1.198888] Linux agpgart interface v0.103
[    1.213005] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.213023] r8169 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.213060] r8169 0000:03:00.0: setting latency timer to 64
[    1.213104]   alloc irq_desc for 27 on node -1
[    1.213106]   alloc kstat_irqs on node -1
[    1.213120] r8169 0000:03:00.0: irq 27 for MSI/MSI-X
[    1.213803] eth0: RTL8168c/8111c at 0xf80c0000, 00:24:1d:1d:b6:ea, XID 3c4000c0 IRQ 27
[    1.243592] Floppy drive(s): fd0 is 1.44M
[    1.263126] FDC 0 is a post-1991 82077
[    1.468523] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    1.680599] usb 2-1: configuration #1 chosen from 1 choice
[    1.764521] usbcore: registered new interface driver hiddev
[    1.767806] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input3
[    1.767870] generic-usb 0003:046D:C529.0001: input,hidraw0: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.0-1/input0
[    1.772149] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1/input/input4
[    1.772255] generic-usb 0003:046D:C529.0002: input,hiddev96,hidraw1: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-1/input1
[    1.772269] usbcore: registered new interface driver usbhid
[    1.772272] usbhid: v2.6:USB HID core driver
[    2.036010] usb 2-2: new low speed USB device using uhci_hcd and address 3
[    2.211576] xor: automatically using best checksumming function: pIII_sse
[    2.228504]    pIII_sse  :  6884.000 MB/sec
[    2.228506] xor: using function: pIII_sse (6884.000 MB/sec)
[    2.228591] usb 2-2: configuration #1 chosen from 1 choice
[    2.231148] device-mapper: dm-raid45: initialized v0.2594b
[    2.252916] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input5
[    2.253013] generic-usb 0003:046D:C521.0003: input,hidraw2: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-2/input0
[    2.280750] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.1/input/input6
[    2.280839] generic-usb 0003:046D:C521.0004: input,hiddev97,hidraw3: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.0-2/input1
[    7.495504] kjournald starting.  Commit interval 5 seconds
[    7.495517] EXT3-fs: mounted filesystem with writeback data mode.
[    8.108135] type=1505 audit(1257108665.746:2): operation="profile_load" pid=471 name=/usr/share/gdm/guest-session/Xsession
[    8.119312] type=1505 audit(1257108665.754:3): operation="profile_load" pid=472 name=/sbin/dhclient3
[    8.120168] type=1505 audit(1257108665.758:4): operation="profile_load" pid=472 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    8.120604] type=1505 audit(1257108665.758:5): operation="profile_load" pid=472 name=/usr/lib/connman/scripts/dhclient-script
[    8.146313] type=1505 audit(1257108665.782:6): operation="profile_load" pid=473 name=/usr/bin/evince
[    8.158673] type=1505 audit(1257108665.794:7): operation="profile_load" pid=473 name=/usr/bin/evince-previewer
[    8.165982] type=1505 audit(1257108665.802:8): operation="profile_load" pid=473 name=/usr/bin/evince-thumbnailer
[    8.180757] type=1505 audit(1257108665.818:9): operation="profile_load" pid=475 name=/usr/lib/cups/backend/cups-pdf
[    8.181741] type=1505 audit(1257108665.818:10): operation="profile_load" pid=475 name=/usr/sbin/cupsd
[    8.195547] type=1505 audit(1257108665.830:11): operation="profile_load" pid=476 name=/usr/sbin/mysqld
[    9.077056] Adding 9068652k swap on /dev/sda5.  Priority:-1 extents:1 across:9068652k 
[    9.253770] EXT3 FS on sda1, internal journal
[    9.692039] kjournald starting.  Commit interval 5 seconds
[    9.692569] EXT3 FS on sdb1, internal journal
[    9.692577] EXT3-fs: mounted filesystem with writeback data mode.
[   10.588589] udev: starting version 147
[   11.991066] lp: driver loaded but no devices found
[   12.313417] parport_pc 00:09: reported by Plug and Play ACPI
[   12.313461] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   12.320108] ppdev: user-space parallel port driver
[   12.412249] lp0: using parport0 (interrupt-driven).
[   13.051285] intel_rng: FWH not detected
[   13.121290] it87: Found IT8718F chip at 0x290, revision 5
[   13.121299] it87: in3 is VCC (+5V)
[   13.830096] coretemp coretemp.0: Using relative temperature scale!
[   13.830142] coretemp coretemp.1: Using relative temperature scale!
[   13.855255] ip_tables: (C) 2000-2006 Netfilter Core Team
[   14.838914] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.838939] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   15.046517] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input7
[   17.652869] r8169: eth0: link up
[   17.652876] r8169: eth0: link up
[   19.523753] __ratelimit: 36 callbacks suppressed
[   19.523758] type=1503 audit(1257108677.158:24): operation="open" pid=1322 parent=1321 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   20.595097] type=1503 audit(1257108678.230:25): operation="open" pid=1459 parent=1458 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   21.305866] type=1503 audit(1257108678.942:26): operation="open" pid=1581 parent=1469 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   21.835537] type=1503 audit(1257108679.470:27): operation="open" pid=1588 parent=1587 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   22.853002] type=1503 audit(1257108680.490:28): operation="open" pid=1641 parent=1640 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   23.872281] type=1503 audit(1257108680.353:29): operation="open" pid=1652 parent=1651 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   24.893232] type=1503 audit(1257108681.373:30): operation="open" pid=1662 parent=1661 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   25.912555] type=1503 audit(1257108682.393:31): operation="open" pid=1672 parent=1671 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   27.105864] type=1503 audit(1257108683.585:32): operation="open" pid=1689 parent=1688 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   27.248337] type=1503 audit(1257108683.725:33): operation="open" pid=1700 parent=1699 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   27.868009] eth0: no IPv6 routers present
[   28.982411] nvidia: module license 'NVIDIA' taints kernel.
[   28.982417] Disabling lock debugging due to kernel taint
[   29.238830] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   29.238842] nvidia 0000:01:00.0: setting latency timer to 64
[   29.239004] NVRM: loading NVIDIA UNIX x86 Kernel Module  185.18.36  Fri Aug 14 17:18:04 PDT 2009
[   36.613611] NET: Registered protocol family 5
[   42.004516] CPU0 attaching NULL sched-domain.
[   42.004524] CPU1 attaching NULL sched-domain.
[   42.020595] CPU0 attaching sched-domain:
[   42.020601]  domain 0: span 0-1 level MC
[   42.020606]   groups: 0 1
[   42.020614] CPU1 attaching sched-domain:
[   42.020617]  domain 0: span 0-1 level MC
[   42.020621]   groups: 1 0

```

EDIT: Updated the BIOS on my mobo.. no effect.  CPU freq still wrong.

EDIT: embarrassingly I was finally able to fix this via BIOS... how/when my BIOS decided to dial back my max Freq (I had to go in to the pages that I considered only relevant to OCing), I have no idea..

---

### Post by TheKorn2 on 2009-11-03
I am having an identical problem with my Toshiba L305 laptop.  The CPU frequency monitor complains that frequency scaling is unsupported.

Not sure what logs would be helpful, but happy to provide whatever is asked for!  (Here's some ACPI stuff from dmesg, but not really sure if it's useful or not.)

```

Nov  3 09:50:57 Toshtop kernel: [    4.531129] ACPI: AC Adapter [ADP0] (on-line)
Nov  3 09:50:57 Toshtop kernel: [    4.531199] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
Nov  3 09:50:57 Toshtop kernel: [    4.531202] ACPI: Power Button [PWRF]
Nov  3 09:50:57 Toshtop kernel: [    4.531248] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
Nov  3 09:50:57 Toshtop kernel: [    4.531250] ACPI: Power Button [PWRB]
Nov  3 09:50:57 Toshtop kernel: [    4.531292] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
Nov  3 09:50:57 Toshtop kernel: [    4.533131] ACPI: Lid Switch [LID0]
Nov  3 09:50:57 Toshtop kernel: [    4.533295] fan PNP0C0B:00: registered as cooling_device0
Nov  3 09:50:57 Toshtop kernel: [    4.533300] ACPI: Fan [FAN] (on)
Nov  3 09:50:57 Toshtop kernel: [    4.534358] Monitor-Mwait will be used to enter C-1 state
Nov  3 09:50:57 Toshtop kernel: [    4.534380] Monitor-Mwait will be used to enter C-2 state
Nov  3 09:50:57 Toshtop kernel: [    4.534387] Marking TSC unstable due to TSC halts in idle
Nov  3 09:50:57 Toshtop kernel: [    4.534400] ACPI: CPU0 (power states: C1[C1] C2[C2])
Nov  3 09:50:57 Toshtop kernel: [    4.534419] processor LNXCPU:00: registered as cooling_device1
Nov  3 09:50:57 Toshtop kernel: [    4.534422] ACPI: Processor [CPU0] (supports 8 throttling states)
Nov  3 09:50:57 Toshtop kernel: [    4.542299] thermal LNXTHERM:01: registered as thermal_zone0
Nov  3 09:50:57 Toshtop kernel: [    4.542307] ACPI: Thermal Zone [THRM] (55 C)
Nov  3 09:50:57 Toshtop kernel: [    4.543352] Linux agpgart interface v0.103

```

(I've updated my bios to the 10-31-2009 bios, but that didn't help.  And there are no CPU frequency options in my bios.)

powernowd is installed, and says that frequency scaling is unsupported.

```

:/var/log$ sudo modprobe powernowd
[sudo] password for vince: 
FATAL: Module powernowd not found.

```

---

### Post by TheKorn2 on 2009-11-03
Update:  Solved, *almost*.

I don't have any idea why it's not a default, but I had to add p4-clockmod to my modules as detailed in [this post from three years ago.](http://ubuntuforums.org/showthread.php?t=190921&highlight=karmic+cpu+scaling)


Well, I'm halfway there.  Now when I come up, I no longer get a complaint that CPU frequency scaling is unsupported.  I saw the CPU frequency monitor drop from 2.17GHZ all the way down to 250MHz.  

Then something odd happened...  gnome's top bar started futzing with itself, and the CPU speed jumped back up to 2.17GHz and has stayed there ever since.

My hunch is that I have to go tune the thresholds at which the CPU scales up/down, but at least I think I'm on the right path now.  

Hopefully this info helps others.


Edit:  OK looks like this doesn't add real power savings (what I was after) but some hoakey clockspeed trickery.  Don't do this; these aren't the droids we're looking for.  (Guess that's not why it's a default.)

---

### Post by Brain_Recall on 2009-11-03
I've rolled back to 9.04 on my laptop. I guess this is one I'm going to have to skip.

On a plus side, [my desktop]("http://brain.recall.googlepages.com/monolith") has no issues with 9.10. Even CPU Scaling works.

---

### Post by crackbaby on 2009-11-04
Same problem here. Dell GX280 desktop, old P4-HT. All, of course, worked fine before Karmic.

```
$ cpufreq-info
CPU 0:
(...)
current policy: frequency should be within 400 MHz and 3.20 GHz.
The governor "performance" may decide which speed to use
within this range.
(...)
CPU 1:
current policy: frequency should be within 400 MHz and 3.20 GHz.
The governor "performance" may decide which speed to use
within this range.
(...)

$ sudo cpufreq-set -c0 -g ondemand
$ sudo cpufreq-set -c1 -g ondemand

cpufreq-info still lists performance as the gov in charge...
No errors, no warnings, just no apparent change of governor.

$ cpufreq-info |grep "available cpu"
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance

$ lsmod |grep p4_
p4_clockmod 4164 1
```

---

### Post by MrEgg on 2009-11-05
I too rolled back to Jaunty... for now. IMHO, this issue should be solved with some kernel update, as I've never seen Ubuntu developers let us users down so far. Can anybody let us know when 2.6.32 is out, so we can give it a try?

TIA

---

### Post by ego1 on 2009-11-12
The issue with 9.10 is because "The Linux kernel now provides all the necessary tools to properly manage CPU frequency : no need to use a daemon (like cpufreqd or powernowd) to take care of your CPU." I found a very complete howto in 
[http://technowizah.com/2007/01/debian-how-to-cpu-frequency-management.html]("http://technowizah.com/2007/01/debian-how-to-cpu-frequency-management.html")

But following that howto I am having trouble because 9.10 is missing the policy governor. You can follow my tread in 
[http://ubuntuforums.org/showthread.php?t=1323245]("http://ubuntuforums.org/showthread.php?t=1323245")

Good look

---

### Post by riban on 2009-11-13
Same for me on Dell Inspiron 5150. Fine under Jaunty. Stopped working after upgrade to Karmic. It seems the drivers have been removed. Is this a kernel issue? Very frustrating to upgrade and for things to stop working. (One expects the opposite.)

---

### Post by osced on 2009-11-13
I tried that guide, but I get some errors : > $ sudo modprobe powernow_k8
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Module powernow_k8 not found.
$ sudo modprobe acpi_cpufreq
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Module acpi_cpufreq not found.


I have a AMD Athlon 64 and according to the guide I should use that module.

---

### Post by xyepblra on 2009-11-19
I used to set up my cpu frequency governor the way it is described [here]("http://maketecheasier.com/how-to-control-your-cpu-frequency-in-ubuntu/2009/04/10?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+MakeTechEasier+%28Make+Tech+Easier%29"). It worked remarkably well untill I upgraded to KK. It still does work in KK, but now it prompts for the root password, instead of just changing CPU frequency or policy without remembering the fat that I am the administrator of my computer. I think the main reason of my difficulties with the applet is performance of the
```
sudo dpkg-reconfigure gnome-applets
```
which simply does not work.
Could somebody please tell me how to launch cpufreq applet as a root user all the time?

---

### Post by purduepilot on 2009-11-22
My problem was that it required root authentication every time I tried to change the cpu speed, and even when I did authenticate the change would not always go into effect.  This seems to have fixed it:

> **azerty88 said:**
> Here is what you need to do:

sudo gedit /var/lib/polkit-1/localauthority/50-local.d/01-cpufreq.pkla

and paste this:
```

[cpufreq policy for admin group]
Identity=unix-group:admin
Action=org.gnome.cpufreqselector
ResultAny=no
ResultInactive=no
ResultActive=yes

```

---

### Post by priyadarshan.hari on 2009-11-25
I have also been trying to enable cpu frequency scaling for the past few days in VAIN with my ubuntu 9.04 jaunty.  I have searched the forms and tried most of the suggestions. 

I have tried the following modules acpi_cpufreq, powernowd, cpudyn, cpufreqd. Nothing works for me. I always get the error message of the form

FATAL : Module acpi_cpufreq not found.

My processor is always operating in full speed . 

I am using Xeon E5420 x 2 quad core on S5000vSA motherboard.

I will be grateful for any help in this direction.

====
priyadarshan

---

### Post by DaMad-Man on 2009-11-30
When I load up 9.10 I can't even get the thing past the white Ubuntu logo before it goes to the "FREQUENCY PROBLEM"... I am new to Linux but maybe cli @ boot might work? Provided U get that far... The only way I can get around it is. 1.) Install "9.04"  2.) Then FULLY UPDATE" 9.04  3.) Then Upgrade... I thought grub 2 waz the problem... My Rig - (_AMD Athlon XP - Barton 1.86GHZ Overclocked to 2.02GHZ. 1.5GiB Ram. FIC mobo AU-13. Nvidia Geforce 7 512MB. Stock Air Cooling. B43 Legacy wireless Desktop_)

---

### Post by TheKorn2 on 2009-11-30
> **DaMad-Man said:**
> When I load up 9.10 I can't even get the thing past the white Ubuntu logo before it goes to the "FREQUENCY PROBLEM"... I am new to Linux but maybe cli @ boot might work? Provided U get that far... The only way I can get around it is. 1.) Install "9.04"  2.) Then FULLY UPDATE" 9.04  3.) Then Upgrade... I thought grub 2 waz the problem... 

I can't even **start** to make heads or tails of this reply.  What frequency problem?  We can't read your mind, nor your computer's mind.  cli?  Don't shorten things, write them out.  (Again with the mind reading.)  You thought grub2 was the problem.... why?  Did you see it on a poster in the subway and said to yourself, "ah HA!  **That** must be the source of my woes!"?

---

### Post by DaMad-Man on 2009-11-30
My fault wrong frequency problem. My Karmic Koala 9.10 won't load. The screen goes blank with frequency window error? I worked around it by upgrading  Jaunty to Koala keeping Jaunty's GRUB. _Freqency out of range_. I have a old monitor, so I hooked up a lcd monitor to that machine, same problem. Install perfectly on other machine, no problem. See my problem?

---

### Post by TheKorn2 on 2009-12-01
> **DaMad-Man said:**
> My fault wrong frequency problem. My Karmic Koala 9.10 won't load. The screen goes blank with frequency window error? I worked around it by upgrading  Jaunty to Koala keeping Jaunty's GRUB. _Freqency out of range_. I have a old monitor, so I hooked up a lcd monitor to that machine, same problem. Install perfectly on other machine, no problem. See my problem?

Ahhhhh, now that makes a lot more sense.

Sounds like X (-windows) is selecting a video mode that your monitor isn't happy with, or just can't configure your video card correctly for whatever reason.

Sorry, I don't know enough about those to really be of much help, outside of...  if you can boot the machine and know its IP address, you could SSH in and see what the logs say.  (I think ubuntu has a 'safe graphics' boot option also; I'd look into that to at least get you sorta running.)

---

### Post by Felliph3 on 2009-12-07
This crap pisses me off. Seems to have fixed it. Thanks a lottt! :p

---

### Post by bornagainpenguin on 2010-04-09
> **purduepilot said:**
> My problem was that it required root authentication every time I tried to change the cpu speed, and even when I did authenticate the change would not always go into effect.  This seems to have fixed it:

Thanks, this also allowed me to change the cpu frequency without requiring me to sign in as root.

--bornagainpenguin

---

