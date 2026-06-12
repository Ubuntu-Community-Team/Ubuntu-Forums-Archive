---
title: "Cardreader not working"
date: 2010-08-21
forum: Hardware
---

### Post by HeinzVoerbakje on 2010-08-21
Hi all,

I've bought a Compaq CQ10-400 netbook. With a little bit of tweaking I've got most things, like sound and wireless working using 10.04. The only thing that's still not working is the internal cardreader. Who can help me trying to get it to work?

Some output:

sudo fdisk -l
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5ef35ef3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3522    28281888    7  HPFS/NTFS
/dev/sda2            3522       19458   128006145    5  Extended
/dev/sda5            3522       19088   125036544   83  Linux
/dev/sda6           19088       19458     2968576   82  Linux swap / Solaris

```

dmesg
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-24-generic (buildd@vernadsky) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #41-Ubuntu SMP Thu Aug 19 01:12:52 UTC 2010 (Ubuntu 2.6.32-24.41-generic 2.6.32.15+drm33.5)
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
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f43f000 (usable)
[    0.000000]  BIOS-e820: 000000003f43f000 - 000000003f4bf000 (reserved)
[    0.000000]  BIOS-e820: 000000003f4bf000 - 000000003f5bf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f5bf000 - 000000003f5f7000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003f5f7000 - 000000003f600000 (usable)
[    0.000000]  BIOS-e820: 000000003f600000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.6 present.
[    0.000000] last_pfn = 0x3f600 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0FFE00000 mask 0FFE00000 write-protect
[    0.000000]   1 base 000000000 mask 0E0000000 write-back
[    0.000000]   2 base 020000000 mask 0E0000000 write-back
[    0.000000]   3 base 03F800000 mask 0FF800000 uncachable
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
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003f43f000 (usable)
[    0.000000]  modified: 000000003f43f000 - 000000003f4bf000 (reserved)
[    0.000000]  modified: 000000003f4bf000 - 000000003f5bf000 (ACPI NVS)
[    0.000000]  modified: 000000003f5bf000 - 000000003f5f7000 (ACPI data)
[    0.000000]  modified: 000000003f5f7000 - 000000003f600000 (usable)
[    0.000000]  modified: 000000003f600000 - 0000000040000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 2efd8000 - 2f76e9ac
[    0.000000] ACPI: RSDP 000fe020 00024 (v02 HP    )
[    0.000000] ACPI: XSDT 3f5f6120 00074 (v01 HPQOEM SLIC-MPC 00000001      01000013)
[    0.000000] ACPI: FACP 3f5f5000 000F4 (v04 HP     SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: DSDT 3f5e6000 0B13E (v01 HP     SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: FACS 3f589000 00040
[    0.000000] ACPI: HPET 3f5f4000 00038 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: APIC 3f5f3000 00078 (v02 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: MCFG 3f5f2000 0003C (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: SLIC 3f5e5000 00176 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: BOOT 3f5e4000 00028 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: SSDT 3f5e3000 004C4 (v02  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: SSDT 3f5e2000 001F7 (v02  PmRef  Cpu0Tst 00003000 INTL 20051117)
[    0.000000] ACPI: SSDT 3f5e1000 00064 (v02  PmRef  Cpu1Tst 00003000 INTL 20051117)
[    0.000000] ACPI: WDAT 3f5e0000 00194 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 126MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008ddeb8]    TEXT DATA BSS ==> [0000100000 - 00008ddeb8]
[    0.000000]   #4 [002efd8000 - 002f76e9ac]          RAMDISK ==> [002efd8000 - 002f76e9ac]
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #6 [00008de000 - 00008e129b]              BRK ==> [00008de000 - 00008e129b]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003f600
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003f43f
[    0.000000]     0: 0x0003f5f7 -> 0x0003f600
[    0.000000] On node 0 totalpages: 259043
[    0.000000] free_area_init_node: node 0, pgdat c079a780, node_mem_map c1001000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 253 pages used for memmap
[    0.000000]   HighMem zone: 31565 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:a0000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1800000 s36056 r0 d21288 u1048576
[    0.000000] pcpu-alloc: s36056 r0 d21288 u1048576 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257014
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=1ad34f77-ea8d-48f5-a6b6-df680bd8443a ro pciehp.pciehp_force=1 elevator=noop quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 5191680 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0003f600)
[    0.000000] Memory: 1005268k/1038336k available (4679k kernel code, 30112k reserved, 2124k data, 660k init, 127272k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a5000 - 0xc084a000   ( 660 kB)
[    0.000000]       .data : 0xc0591e33 - 0xc07a4e88   (2124 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0591e33   (4679 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:440
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1662.625 MHz processor.
[    0.004009] Calibrating delay loop (skipped), value calculated using timer frequency.. 3325.25 BogoMIPS (lpj=6650500)
[    0.004045] Security Framework initialized
[    0.004084] AppArmor: AppArmor initialized
[    0.004100] Mount-cache hash table entries: 512
[    0.008080] Initializing cgroup subsys ns
[    0.008090] Initializing cgroup subsys cpuacct
[    0.008100] Initializing cgroup subsys memory
[    0.008113] Initializing cgroup subsys devices
[    0.008119] Initializing cgroup subsys freezer
[    0.008125] Initializing cgroup subsys net_cls
[    0.008160] CPU: L1 I cache: 32K, L1 D cache: 24K
[    0.008167] CPU: L2 cache: 512K
[    0.008172] CPU: Physical Processor ID: 0
[    0.008176] CPU: Processor Core ID: 0
[    0.008183] mce: CPU supports 5 MCE banks
[    0.008195] CPU0: Thermal monitoring handled by SMI
[    0.008202] using mwait in idle threads.
[    0.008214] Performance Events: Atom events, Intel PMU driver.
[    0.008231] ... version:                3
[    0.008235] ... bit width:              40
[    0.008240] ... generic registers:      2
[    0.008244] ... value mask:             000000ffffffffff
[    0.008250] ... max period:             000000007fffffff
[    0.008254] ... fixed-purpose events:   3
[    0.008259] ... event mask:             0000000700000003
[    0.008267] Checking 'hlt' instruction... OK.
[    0.024009] Disabling 4MB page tables to avoid TLB bug
[    0.028293] ACPI: Core revision 20090903
[    0.056017] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.056029] ftrace: allocating 21780 entries in 43 pages
[    0.060100] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.060520] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.102306] CPU0: Intel(R) Atom(TM) CPU N450   @ 1.66GHz stepping 0a
[    0.104001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.008000] Initializing CPU#1
[    0.008000] CPU: L1 I cache: 32K, L1 D cache: 24K
[    0.008000] CPU: L2 cache: 512K
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 0
[    0.008000] CPU1: Thermal monitoring handled by SMI
[    0.188128] CPU1: Intel(R) Atom(TM) CPU N450   @ 1.66GHz stepping 0a
[    0.188156] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.192033] Brought up 2 CPUs
[    0.192041] Total of 2 processors activated (6650.57 BogoMIPS).
[    0.192275] CPU0 attaching sched-domain:
[    0.192284]  domain 0: span 0-1 level SIBLING
[    0.192290]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[    0.192302]   domain 1: span 0-1 level MC
[    0.192307]    groups: 0-1 (cpu_power = 1178)
[    0.192320] CPU1 attaching sched-domain:
[    0.192325]  domain 0: span 0-1 level SIBLING
[    0.192330]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[    0.192341]   domain 1: span 0-1 level MC
[    0.192346]    groups: 0-1 (cpu_power = 1178)
[    0.192571] devtmpfs: initialized
[    0.192571] regulator: core version 0.5
[    0.192571] Time: 18:56:14  Date: 08/21/10
[    0.192571] NET: Registered protocol family 16
[    0.192571] Trying to unpack rootfs image as initramfs...
[    0.192571] EISA bus registered
[    0.192577] ACPI: bus type pci registered
[    0.192743] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.192752] PCI: MCFG area at e0000000 reserved in E820
[    0.192758] PCI: Using MMCONFIG for extended config space
[    0.192764] PCI: Using configuration type 1 for base access
[    0.197594] bio: create slab <bio-0> at 0
[    0.200954] ACPI: EC: Look up EC in DSDT
[    0.206420] ACPI: Executed 1 blocks of module-level executable AML code
[    0.212106] ACPI: BIOS _OSI(Linux) query ignored
[    0.516841] ACPI: Interpreter enabled
[    0.516871] ACPI: (supports S0 S3 S4 S5)
[    0.516965] ACPI: Using IOAPIC for interrupt routing
[    0.537092] ACPI: EC: GPE = 0x11, I/O: command/status = 0x66, data = 0x62
[    0.537316] ACPI: Power Resource [FN00] (on)
[    0.537999] ACPI: No dock devices found.
[    0.539736] ACPI Warning for \_SB_.PCI0._OSC: Parameter count mismatch - ASL declared 5, ACPI requires 4 (20090903/nspredef-336)
[    0.539762] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.539954] pci 0000:00:02.0: reg 10 32bit mmio: [0x54180000-0x541fffff]
[    0.539966] pci 0000:00:02.0: reg 14 io port: [0x30c0-0x30c7]
[    0.539977] pci 0000:00:02.0: reg 18 32bit mmio pref: [0x40000000-0x4fffffff]
[    0.540022] pci 0000:00:02.0: reg 1c 32bit mmio: [0x54000000-0x540fffff]
[    0.540085] pci 0000:00:02.1: reg 10 32bit mmio: [0x54100000-0x5417ffff]
[    0.540252] pci 0000:00:1b.0: reg 10 64bit mmio: [0x54200000-0x54203fff]
[    0.540340] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.540351] pci 0000:00:1b.0: PME# disabled
[    0.540485] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.540495] pci 0000:00:1c.0: PME# disabled
[    0.540631] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.540641] pci 0000:00:1c.1: PME# disabled
[    0.540746] pci 0000:00:1d.0: reg 20 io port: [0x3080-0x309f]
[    0.540850] pci 0000:00:1d.1: reg 20 io port: [0x3060-0x307f]
[    0.540949] pci 0000:00:1d.2: reg 20 io port: [0x3040-0x305f]
[    0.541044] pci 0000:00:1d.3: reg 20 io port: [0x3020-0x303f]
[    0.541146] pci 0000:00:1d.7: reg 10 32bit mmio: [0x54204400-0x542047ff]
[    0.541238] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.541249] pci 0000:00:1d.7: PME# disabled
[    0.541563] pci 0000:00:1f.2: reg 10 io port: [0x30b8-0x30bf]
[    0.541579] pci 0000:00:1f.2: reg 14 io port: [0x30cc-0x30cf]
[    0.541594] pci 0000:00:1f.2: reg 18 io port: [0x30b0-0x30b7]
[    0.541609] pci 0000:00:1f.2: reg 1c io port: [0x30c8-0x30cb]
[    0.541624] pci 0000:00:1f.2: reg 20 io port: [0x30a0-0x30af]
[    0.541639] pci 0000:00:1f.2: reg 24 32bit mmio: [0x54204000-0x542043ff]
[    0.541695] pci 0000:00:1f.2: PME# supported from D3hot
[    0.541706] pci 0000:00:1f.2: PME# disabled
[    0.541793] pci 0000:00:1f.3: reg 20 io port: [0x3000-0x301f]
[    0.542022] pci 0000:01:00.0: reg 10 io port: [0x2000-0x20ff]
[    0.542102] pci 0000:01:00.0: reg 18 64bit mmio pref: [0x50004000-0x50004fff]
[    0.542161] pci 0000:01:00.0: reg 20 64bit mmio pref: [0x50000000-0x50003fff]
[    0.542353] pci 0000:01:00.0: supports D1 D2
[    0.542360] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.542380] pci 0000:01:00.0: PME# disabled
[    0.542659] pci 0000:01:00.1: reg 10 32bit mmio: [0x53000000-0x5300ffff]
[    0.542971] pci 0000:01:00.1: supports D1 D2
[    0.542978] pci 0000:01:00.1: PME# supported from D1 D2 D3hot D3cold
[    0.542997] pci 0000:01:00.1: PME# disabled
[    0.543188] pci 0000:00:1c.0: bridge io port: [0x2000-0x2fff]
[    0.543199] pci 0000:00:1c.0: bridge 32bit mmio: [0x53000000-0x53ffffff]
[    0.543215] pci 0000:00:1c.0: bridge 64bit mmio pref: [0x50000000-0x50ffffff]
[    0.543332] pci 0000:02:00.0: reg 10 32bit mmio: [0x52000000-0x5200ffff]
[    0.543588] pci 0000:00:1c.1: bridge io port: [0x1000-0x1fff]
[    0.543599] pci 0000:00:1c.1: bridge 32bit mmio: [0x52000000-0x52ffffff]
[    0.543614] pci 0000:00:1c.1: bridge 64bit mmio pref: [0x51000000-0x51ffffff]
[    0.543701] pci 0000:00:1e.0: transparent bridge
[    0.543749] pci_bus 0000:00: on NUMA node 0
[    0.543775] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.544345] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[    0.544736] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.545034] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    0.545690] ACPI Warning for \_SB_.PCI0._OSC: Parameter count mismatch - ASL declared 5, ACPI requires 4 (20090903/nspredef-336)
[    0.555803] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    0.556200] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 *10 11 12)
[    0.556567] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[    0.556923] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[    0.557270] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.557639] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.557991] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.558356] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.558717] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.558749] vgaarb: loaded
[    0.559118] SCSI subsystem initialized
[    0.559347] libata version 3.00 loaded.
[    0.559580] usbcore: registered new interface driver usbfs
[    0.559622] usbcore: registered new interface driver hub
[    0.559706] usbcore: registered new device driver usb
[    0.560291] ACPI: WMI: Mapper loaded
[    0.560297] PCI: Using ACPI for IRQ routing
[    0.560742] NetLabel: Initializing
[    0.560749] NetLabel:  domain hash size = 128
[    0.560754] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.560789] NetLabel:  unlabeled traffic allowed by default
[    0.560899] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.560914] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.564049] Switching to clocksource tsc
[    0.568784] AppArmor: AppArmor Filesystem Enabled
[    0.568822] pnp: PnP ACPI init
[    0.568859] ACPI: bus type pnp registered
[    0.574489] pnp: PnP ACPI: found 9 devices
[    0.574499] ACPI: ACPI bus type pnp unregistered
[    0.574510] PnPBIOS: Disabled by ACPI PNP
[    0.574546] system 00:01: ioport range 0x600-0x60f has been reserved
[    0.574558] system 00:01: ioport range 0x610-0x610 has been reserved
[    0.574568] system 00:01: ioport range 0x800-0x80f has been reserved
[    0.574577] system 00:01: ioport range 0x810-0x817 has been reserved
[    0.574586] system 00:01: ioport range 0x400-0x47f has been reserved
[    0.574595] system 00:01: ioport range 0x500-0x53f has been reserved
[    0.574607] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    0.574618] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.574628] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.574637] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.574647] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.574659] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.574669] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.578823] Freeing initrd memory: 7770k freed
[    0.609844] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
[    0.609853] pci 0000:00:1c.0:   IO window: 0x2000-0x2fff
[    0.609863] pci 0000:00:1c.0:   MEM window: 0x53000000-0x53ffffff
[    0.609872] pci 0000:00:1c.0:   PREFETCH window: 0x00000050000000-0x00000050ffffff
[    0.609885] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02
[    0.609892] pci 0000:00:1c.1:   IO window: 0x1000-0x1fff
[    0.609902] pci 0000:00:1c.1:   MEM window: 0x52000000-0x52ffffff
[    0.609910] pci 0000:00:1c.1:   PREFETCH window: 0x00000051000000-0x00000051ffffff
[    0.609923] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.609927] pci 0000:00:1e.0:   IO window: disabled
[    0.609936] pci 0000:00:1e.0:   MEM window: disabled
[    0.609942] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.609976]   alloc irq_desc for 16 on node -1
[    0.609981]   alloc kstat_irqs on node -1
[    0.609996] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.610007] pci 0000:00:1c.0: setting latency timer to 64
[    0.610032]   alloc irq_desc for 17 on node -1
[    0.610036]   alloc kstat_irqs on node -1
[    0.610045] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.610054] pci 0000:00:1c.1: setting latency timer to 64
[    0.610067] pci 0000:00:1e.0: setting latency timer to 64
[    0.610076] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.610082] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.610089] pci_bus 0000:01: resource 0 io:  [0x2000-0x2fff]
[    0.610095] pci_bus 0000:01: resource 1 mem: [0x53000000-0x53ffffff]
[    0.610101] pci_bus 0000:01: resource 2 pref mem [0x50000000-0x50ffffff]
[    0.610107] pci_bus 0000:02: resource 0 io:  [0x1000-0x1fff]
[    0.610113] pci_bus 0000:02: resource 1 mem: [0x52000000-0x52ffffff]
[    0.610119] pci_bus 0000:02: resource 2 pref mem [0x51000000-0x51ffffff]
[    0.610125] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.610131] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffff]
[    0.610206] NET: Registered protocol family 2
[    0.610423] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.611131] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.612076] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.612509] TCP: Hash tables configured (established 131072 bind 65536)
[    0.612515] TCP reno registered
[    0.612732] NET: Registered protocol family 1
[    0.612775] pci 0000:00:02.0: Boot video device
[    0.627147] Simple Boot Flag at 0x44 set to 0x1
[    0.627511] cpufreq-nforce2: No nForce2 chipset.
[    0.627569] Scanning for low memory corruption every 60 seconds
[    0.627798] audit: initializing netlink socket (disabled)
[    0.627820] type=2000 audit(1282416974.627:1): initialized
[    0.644358] highmem bounce pool size: 64 pages
[    0.644370] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.647816] VFS: Disk quotas dquot_6.5.2
[    0.647947] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.649309] fuse init (API version 7.13)
[    0.649510] msgmni has been set to 1731
[    0.649993] alg: No test for stdrng (krng)
[    0.650133] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.650140] io scheduler noop registered (default)
[    0.650145] io scheduler anticipatory registered
[    0.650149] io scheduler deadline registered
[    0.650243] io scheduler cfq registered
[    0.650503]   alloc irq_desc for 24 on node -1
[    0.650509]   alloc kstat_irqs on node -1
[    0.650527] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.650544] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.650778]   alloc irq_desc for 25 on node -1
[    0.650783]   alloc kstat_irqs on node -1
[    0.650798] pcieport 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.650813] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.650993] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.651024] Firmware did not grant requested _OSC control
[    0.651097] Firmware did not grant requested _OSC control
[    0.651168] pciehp 0000:00:1c.0:pcie04: Bypassing BIOS check for pciehp use on 0000:00:1c.0
[    0.651267] pciehp 0000:00:1c.0:pcie04: HPC vendor_id 8086 device_id 27d0 ss_vid 0 ss_did 0
[    0.755074] pciehp 0000:00:1c.0:pcie04: Device 0000:01:00.0 already exists at 0000:01:00, cannot hot-add
[    0.755081] pciehp 0000:00:1c.0:pcie04: Cannot add device at 0000:01:00
[    0.755096] pciehp 0000:00:1c.0:pcie04: service driver pciehp loaded
[    0.755110] pciehp 0000:00:1c.1:pcie04: Bypassing BIOS check for pciehp use on 0000:00:1c.1
[    0.755134] pciehp 0000:00:1c.1:pcie04: HPC vendor_id 8086 device_id 27d2 ss_vid 0 ss_did 0
[    0.859073] pciehp 0000:00:1c.1:pcie04: Device 0000:02:00.0 already exists at 0000:02:00, cannot hot-add
[    0.859080] pciehp 0000:00:1c.1:pcie04: Cannot add device at 0000:02:00
[    0.859095] pciehp 0000:00:1c.1:pcie04: service driver pciehp loaded
[    0.859116] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.860610] ACPI: AC Adapter [AC] (off-line)
[    0.860791] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.860804] ACPI: Power Button [PWRB]
[    0.860897] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    0.861913] ACPI: Lid Switch [LID0]
[    0.862040] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.862047] ACPI: Power Button [PWRF]
[    0.863452] ACPI: SSDT 3f494c98 001F7 (v02  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.864346] ACPI: SSDT 3f493e18 001C7 (v02  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.868961] Marking TSC unstable due to TSC halts in idle
[    0.869093] Switching to clocksource hpet
[    0.869285] processor LNXCPU:00: registered as cooling_device0
[    0.870108] ACPI: SSDT 3f494f18 000D0 (v02  PmRef  Cpu1Ist 00003000 INTL 20051117)
[    0.870934] ACPI: SSDT 3f492f18 00083 (v02  PmRef  Cpu1Cst 00003000 INTL 20051117)
[    0.872621] processor LNXCPU:01: registered as cooling_device1
[    0.882050] ACPI Warning for \_TZ_.THRM._AL0: Return Package has no elements (empty) (20090903/nspredef-433)
[    0.882066] ACPI: [Package] has zero elements (f73b15a0)
[    0.882071] ACPI: Invalid active0 threshold
[    0.885339] thermal LNXTHERM:01: registered as thermal_zone0
[    0.885356] ACPI: Thermal Zone [THRM] (50 C)
[    0.885771] isapnp: Scanning for PnP cards...
[    0.891614] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.896629] brd: module loaded
[    0.898303] loop: module loaded
[    0.898664] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.900330] Fixed MDIO Bus: probed
[    0.900435] PPP generic driver version 2.4.2
[    0.900591] tun: Universal TUN/TAP device driver, 1.6
[    0.900597] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.900827] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.900877] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.900911] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.900920] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.901009] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.901052] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.901072] ehci_hcd 0000:00:1d.7: debug port 1
[    0.904971] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.905028] ehci_hcd 0000:00:1d.7: irq 16, io mem 0x54204400
[    0.920544] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.920872] usb usb1: configuration #1 chosen from 1 choice
[    0.920998] hub 1-0:1.0: USB hub found
[    0.921019] hub 1-0:1.0: 8 ports detected
[    0.921250] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.921294] uhci_hcd: USB Universal Host Controller Interface driver
[    0.921366] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.921385] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.921419] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.921928] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.921973] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00003080
[    0.922228] usb usb2: configuration #1 chosen from 1 choice
[    0.922309] hub 2-0:1.0: USB hub found
[    0.922327] hub 2-0:1.0: 2 ports detected
[    0.922487]   alloc irq_desc for 18 on node -1
[    0.922494]   alloc kstat_irqs on node -1
[    0.922510] uhci_hcd 0000:00:1d.1: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.922525] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.922534] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.922623] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.922679] uhci_hcd 0000:00:1d.1: irq 18, io base 0x00003060
[    0.923415] usb usb3: configuration #1 chosen from 1 choice
[    0.923493] hub 3-0:1.0: USB hub found
[    0.923513] hub 3-0:1.0: 2 ports detected
[    0.923623] uhci_hcd 0000:00:1d.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.923641] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.923650] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.923841] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.923899] uhci_hcd 0000:00:1d.2: irq 17, io base 0x00003040
[    0.924195] usb usb4: configuration #1 chosen from 1 choice
[    0.924342] hub 4-0:1.0: USB hub found
[    0.924362] hub 4-0:1.0: 2 ports detected
[    0.924554]   alloc irq_desc for 19 on node -1
[    0.924561]   alloc kstat_irqs on node -1
[    0.924573] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.924599] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.924607] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.924753] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.924829] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00003020
[    0.925232] usb usb5: configuration #1 chosen from 1 choice
[    0.925310] hub 5-0:1.0: USB hub found
[    0.925330] hub 5-0:1.0: 2 ports detected
[    0.925564] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUE] at 0x60,0x64 irq 1,12
[    0.932637] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.932664] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.932894] mice: PS/2 mouse device common for all mice
[    0.933256] rtc_cmos 00:03: RTC can wake from S4
[    0.933353] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.933397] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.933758] device-mapper: uevent: version 1.0.3
[    0.934093] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.934276] device-mapper: multipath: version 1.1.0 loaded
[    0.934284] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.934757] EISA: Probing bus 0 at eisa.0
[    0.934771] Cannot allocate resource for EISA slot 1
[    0.934777] Cannot allocate resource for EISA slot 2
[    0.934783] Cannot allocate resource for EISA slot 3
[    0.934815] EISA: Detected 0 cards.
[    0.935227] cpuidle: using governor ladder
[    0.935613] cpuidle: using governor menu
[    0.936918] TCP cubic registered
[    0.937393] NET: Registered protocol family 10
[    0.938626] lo: Disabled Privacy Extensions
[    0.939513] NET: Registered protocol family 17
[    0.940868] Using IPI No-Shortcut mode
[    0.941107] PM: Resume from disk failed.
[    0.941134] registered taskstats version 1
[    0.942030]   Magic number: 6:391:949
[    0.942072] tty tty6: hash matches
[    0.942163] rtc_cmos 00:03: setting system clock to 2010-08-21 18:56:15 UTC (1282416975)
[    0.942171] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.942176] EDD information not available.
[    1.067624] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.074001] ACPI: Battery Slot [BAT0] (battery present)
[    1.240340] isapnp: No Plug & Play device found
[    1.240402] Freeing unused kernel memory: 660k freed
[    1.240969] Write protecting the kernel text: 4680k
[    1.241042] Write protecting the kernel read-only data: 1844k
[    1.277135] udev: starting version 151
[    1.356645] usb 1-8: new high speed USB device using ehci_hcd and address 3
[    1.546718] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.546780] r8169 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.546897] r8169 0000:01:00.0: setting latency timer to 64
[    1.546919] r8169 0000:01:00.0: unknown MAC, using family default
[    1.547086]   alloc irq_desc for 26 on node -1
[    1.547093]   alloc kstat_irqs on node -1
[    1.547138] r8169 0000:01:00.0: irq 26 for MSI/MSI-X
[    1.549095] eth0: RTL8101e at 0xf8034000, 00:21:cc:4d:bd:aa, XID 04000000 IRQ 26
[    1.558101] ahci 0000:00:1f.2: version 3.0
[    1.558138] ahci 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.558224]   alloc irq_desc for 27 on node -1
[    1.558232]   alloc kstat_irqs on node -1
[    1.558256] ahci 0000:00:1f.2: irq 27 for MSI/MSI-X
[    1.558344] ahci: SSS flag set, parallel bus scan disabled
[    1.558402] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0x3 impl SATA mode
[    1.558413] ahci 0000:00:1f.2: flags: 64bit ncq ilck stag pm led clo pmp pio slum part 
[    1.558426] ahci 0000:00:1f.2: setting latency timer to 64
[    1.558882] scsi0 : ahci
[    1.559224] scsi1 : ahci
[    1.559450] scsi2 : ahci
[    1.559656] scsi3 : ahci
[    1.560424] ata1: SATA max UDMA/133 abar m1024@0x54204000 port 0x54204100 irq 27
[    1.560437] ata2: SATA max UDMA/133 abar m1024@0x54204000 port 0x54204180 irq 27
[    1.560445] ata3: DUMMY
[    1.560450] ata4: DUMMY
[    1.566882] usb 1-8: configuration #1 chosen from 1 choice
[    1.824092] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    2.014991] usb 3-1: configuration #1 chosen from 1 choice
[    2.044644] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.045234] ACPI Warning for \_SB_.PCI0.SATA.PRT0._GTF: Return type mismatch - found Integer, expected Buffer (20090903/nspredef-1006)
[    2.045251] ata1.00: _GTF unexpected object type 0x1
[    2.090187] ata1.00: ATA-8: TOSHIBA MK1665GSX, GJ003A, max UDMA/100
[    2.090194] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.091104] ata1.00: _GTF unexpected object type 0x1
[    2.091373] ata1.00: configured for UDMA/100
[    2.104310] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK1665GS GJ00 PQ: 0 ANSI: 5
[    2.104657] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.104920] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    2.105112] sd 0:0:0:0: [sda] Write Protect is off
[    2.105123] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.105224] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.105609]  sda: sda1 sda2 < sda5 sda6 >
[    2.193812] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.424153] ata2: SATA link down (SStatus 0 SControl 300)
[    2.456059] usbcore: registered new interface driver hiddev
[    2.489383] input: HID 1241:1177 as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input5
[    2.489854] generic-usb 0003:1241:1177.0001: input,hidraw0: USB HID v1.00 Mouse [HID 1241:1177] on usb-0000:00:1d.1-1/input0
[    2.489914] usbcore: registered new interface driver usbhid
[    2.490003] usbhid: v2.6:USB HID core driver
[    2.969502] EXT4-fs (sda5): mounted filesystem with ordered data mode
[   12.987315] Adding 2968568k swap on /dev/sda6.  Priority:-1 extents:1 across:2968568k 
[   13.017833] udev: starting version 151
[   13.326890] lp: driver loaded but no devices found
[   13.486526] Linux agpgart interface v0.103
[   13.580346] agpgart-intel 0000:00:00.0: Intel IGD Chipset
[   13.580679] agpgart-intel 0000:00:00.0: detected 8188K stolen memory
[   13.597662] rt3090sta: module is from the staging directory, the quality is unknown, you have been warned.
[   13.644231] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x40000000
[   13.736646] rt3090 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.736716] rt3090 0000:02:00.0: setting latency timer to 64
[   13.737110] 
[   13.737115] 
[   13.737117] === pAd = f8482000, size = 483224 ===
[   13.737120] 
[   13.737127] <-- RTMPAllocAdapterBlock, Status=0
[   13.737134] pAd->CSRBaseAddress =0xf8100000, csr_addr=0xf8100000!
[   13.804101] Linux video capture interface: v2.00
[   13.844636] type=1505 audit(1282409788.402:2):  operation="profile_load" pid=553 name="/sbin/dhclient3"
[   13.845380] type=1505 audit(1282409788.402:3):  operation="profile_load" pid=553 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   13.845804] type=1505 audit(1282409788.402:4):  operation="profile_load" pid=553 name="/usr/lib/connman/scripts/dhclient-script"
[   13.852141] rt2860sta: module is from the staging directory, the quality is unknown, you have been warned.
[   13.852493] [drm] Initialized drm 1.1.0 20060810
[   13.959062] uvcvideo: Found UVC 1.00 device HP Webcam (174f:1124)
[   13.971943] input: HP Webcam as /devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/input/input6
[   13.972112] usbcore: registered new interface driver uvcvideo
[   13.972128] USB Video Class driver (v0.1.0)
[   14.097904] i915 0000:00:02.0: power state changed by ACPI to D0
[   14.097934] i915 0000:00:02.0: power state changed by ACPI to D0
[   14.097949] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.097959] i915 0000:00:02.0: setting latency timer to 64
[   14.162797]   alloc irq_desc for 28 on node -1
[   14.162807]   alloc kstat_irqs on node -1
[   14.162827] i915 0000:00:02.0: irq 28 for MSI/MSI-X
[   14.162843] [drm] set up 7M of stolen space
[   14.270080] [drm] initialized overlay support
[   14.756725] r8169: eth0: link down
[   14.763533] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.763995] fb0: inteldrmfb frame buffer device
[   14.764002] registered panic notifier
[   14.764847] type=1505 audit(1282409789.322:5):  operation="profile_load" pid=704 name="/usr/share/gdm/guest-session/Xsession"
[   14.783029] RX DESC f1948000  size = 2048
[   14.783526] <-- RTMPAllocTxRxRingMemory, Status=0
[   14.790575] acpi device:20: registered as cooling_device2
[   14.795548] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input7
[   14.795992] ACPI: Video Device [OVGA] (multi-head: yes  rom: no  post: no)
[   14.797986] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   14.798098] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.798190]   alloc irq_desc for 29 on node -1
[   14.798198]   alloc kstat_irqs on node -1
[   14.798224] HDA Intel 0000:00:1b.0: irq 29 for MSI/MSI-X
[   14.798285] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   14.803788] Synaptics Touchpad, model: 1, fw: 7.4, id: 0x1e0b1, caps: 0xd04771/0xa40000
[   14.804751] type=1505 audit(1282409789.362:6):  operation="profile_replace" pid=705 name="/sbin/dhclient3"
[   14.805504] type=1505 audit(1282409789.362:7):  operation="profile_replace" pid=705 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   14.805930] type=1505 audit(1282409789.362:8):  operation="profile_replace" pid=705 name="/usr/lib/connman/scripts/dhclient-script"
[   14.815620] vga16fb: initializing
[   14.815630] vga16fb: mapped to 0xc00a0000
[   14.815641] vga16fb: not registering due to another framebuffer present
[   14.843806] type=1505 audit(1282409789.398:9):  operation="profile_load" pid=707 name="/usr/bin/evince"
[   14.850518] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   14.871567] Key1Str is Invalid key length(0) or Type(0)
[   14.871626] Key2Str is Invalid key length(0) or Type(0)
[   14.871686] Key3Str is Invalid key length(0) or Type(0)
[   14.871746] Key4Str is Invalid key length(0) or Type(0)
[   14.872782] AntDiversity=0
[   14.872795] 1. Phy Mode = 5
[   14.872799] 2. Phy Mode = 5
[   14.872806] NVM is Efuse and its size =2d[2d0-2fc] 
[   14.874471] 3. Phy Mode = 9
[   14.876537] type=1505 audit(1282409789.430:10):  operation="profile_load" pid=707 name="/usr/bin/evince-previewer"
[   14.877015] RTMPSetPhyMode: channel is out of range, use first channel=1 
[   14.877104] MCS Set = ff 00 00 00 01
[   14.885464] <==== rt28xx_init, Status=0
[   14.885573] 0x1300 = 00064300
[   14.885617]  AUX_CTRL = 0x                            1d42
[   14.885626]  Read AUX_CTRL = 0x1d42
[   14.885633]  Write AUX_CTRL = 0x1d42
[   14.885639]  OSC_CTRL = 0x3ff11
[   14.893827] [drm] Big FIFO is enabled
[   14.894522] type=1505 audit(1282409789.450:11):  operation="profile_load" pid=707 name="/usr/bin/evince-thumbnailer"
[   14.939086] ====> rt30xx Read PowerLevelMode =  0x3.
[   14.939094] ====> rt30xx F Write 0x83 Command = 0x3.
[   14.973008] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   14.973289] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   14.976670] [drm] Big FIFO is enabled
[   14.976690] [drm] Big FIFO is enabled
[   15.000968] [drm] Big FIFO is enabled
[   15.037190] [drm] Big FIFO is enabled
[   15.041027] Console: switching to colour frame buffer device 128x37
[   15.064330] [drm] Big FIFO is enabled
[   15.642444] ppdev: user-space parallel port driver
[   16.289144] CPU0 attaching NULL sched-domain.
[   16.289159] CPU1 attaching NULL sched-domain.
[   16.312212] CPU0 attaching sched-domain:
[   16.312223]  domain 0: span 0-1 level SIBLING
[   16.312231]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[   16.312248]   domain 1: span 0-1 level MC
[   16.312255]    groups: 0-1 (cpu_power = 1178)
[   16.312270] CPU1 attaching sched-domain:
[   16.312277]  domain 0: span 0-1 level SIBLING
[   16.312284]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[   16.312299]   domain 1: span 0-1 level MC
[   16.312306]    groups: 0-1 (cpu_power = 1178)
[   18.910664] CPU0 attaching NULL sched-domain.
[   18.910676] CPU1 attaching NULL sched-domain.
[   18.940206] CPU0 attaching sched-domain:
[   18.940218]  domain 0: span 0-1 level SIBLING
[   18.940226]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[   18.940243]   domain 1: span 0-1 level MC
[   18.940251]    groups: 0-1 (cpu_power = 1178)
[   18.940266] CPU1 attaching sched-domain:
[   18.940273]  domain 0: span 0-1 level SIBLING
[   18.940280]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[   18.940296]   domain 1: span 0-1 level MC
[   18.940303]    groups: 0-1 (cpu_power = 1178)
[   20.112104] ===>rt_ioctl_giwscan. 13(13) BSS returned, data->length = 1721
[   25.444051] wlan0: no IPv6 routers present
[   40.450042] ===>rt_ioctl_giwscan. 15(15) BSS returned, data->length = 2026
[   66.572642] ===>rt_ioctl_giwscan. 14(14) BSS returned, data->length = 1887
[   66.573726] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
[   70.101912] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[  110.461673] ===>rt_ioctl_giwscan. 12(12) BSS returned, data->length = 1648
[  150.456110] ===>rt_ioctl_giwscan. 15(15) BSS returned, data->length = 1994
[  210.456175] ===>rt_ioctl_giwscan. 14(14) BSS returned, data->length = 1855
[  290.462297] ===>rt_ioctl_giwscan. 13(13) BSS returned, data->length = 1752
[  301.748682] ===>rt_ioctl_giwscan. 16(16) BSS returned, data->length = 2128
[  301.749438] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
[  390.457783] ===>rt_ioctl_giwscan. 15(15) BSS returned, data->length = 1993
[  510.456650] ===>rt_ioctl_giwscan. 11(11) BSS returned, data->length = 1473
[  630.459701] ===>rt_ioctl_giwscan. 11(11) BSS returned, data->length = 1505
[  641.606491] sdhci: Secure Digital Host Controller Interface driver
[  641.606506] sdhci: Copyright(c) Pierre Ossman
[  750.457360] ===>rt_ioctl_giwscan. 14(14) BSS returned, data->length = 1912
[  870.456153] ===>rt_ioctl_giwscan. 13(13) BSS returned, data->length = 1814
[  990.460202] ===>rt_ioctl_giwscan. 12(12) BSS returned, data->length = 1674
[ 1110.458456] ===>rt_ioctl_giwscan. 12(12) BSS returned, data->length = 1585
[ 1230.457995] ===>rt_ioctl_giwscan. 11(11) BSS returned, data->length = 1541
[ 1350.456578] ===>rt_ioctl_giwscan. 13(13) BSS returned, data->length = 1766
[ 1470.459574] ===>rt_ioctl_giwscan. 13(13) BSS returned, data->length = 1741

```

lsusb
```

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 1241:1177 Belkin F8E842-DL Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 174f:1124 Syntek 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Thanks!

---

### Post by frenkel on 2010-10-30
I have the same problem (same netbook). Weird thing is, it's not listed in lspci either.

---

