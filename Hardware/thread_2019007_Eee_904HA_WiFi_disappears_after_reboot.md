---
title: "Eee 904HA WiFi disappears after reboot"
date: 2012-07-06
forum: Hardware
---

### Post by Yoshamano on 2012-07-06
This is mostly a shot in the dark since its not an OS problem (I had the same issue with WinXP and FreeBSD). I've had this netbook for going about 3 1/2 years, and this is a minor annoyance that appeared about a year into owning it. No matter what OS I'm running or what WiFi card I use, if I reboot my Eee the WiFi will not work. If I shut the Eee down, leave it unplugged, and take the battery out for about 10 minutes, then the WiFi works on next boot.  If I just shut it off for a longer length of time the WiFi will work on next boot as well.

So my question is, is there some way around this issue under Xubuntu? I'm currently using an Intel 3945ABG WiFi card. Let me know what logs I should post. Included is my dmesg output from when its borked.

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-26-generic (buildd@lamiak) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #41-Ubuntu SMP Thu Jun 14 16:26:01 UTC 2012 (Ubuntu 3.2.0-26.41-generic 3.2.19)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] Disabled fast string operations
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007f7a0000 (usable)
[    0.000000]  BIOS-e820: 000000007f7a0000 - 000000007f7ae000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007f7ae000 - 000000007f7f0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007f7f0000 - 000000007f800000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI present.
[    0.000000] DMI: ASUSTeK Computer INC. 1000H/1000H, BIOS 2204    10/21/2009
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x7f7a0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask 080000000 write-back
[    0.000000]   1 base 07F800000 mask 0FF800000 uncachable
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2040MB, range: 8MB, type UC
[    0.000000] total RAM covered: 2040M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 16M     num_reg: 2      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2040MB, range: 8MB, type UC
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 3575c000 - 36ba6000
[    0.000000] ACPI: RSDP 000fb9e0 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 7f7a0000 0003C (v01 A_M_I_ OEMRSDT  10000921 MSFT 00000097)
[    0.000000] ACPI: FACP 7f7a0200 00084 (v02 A_M_I_ OEMFACP  10000921 MSFT 00000097)
[    0.000000] ACPI: DSDT 7f7a0430 06FFF (v01  A1028 A1028000 00000000 INTL 20051117)
[    0.000000] ACPI: FACS 7f7ae000 00040
[    0.000000] ACPI: APIC 7f7a0390 0005C (v01 A_M_I_ OEMAPIC  10000921 MSFT 00000097)
[    0.000000] ACPI: MCFG 7f7a03f0 0003C (v01 A_M_I_ OEMMCFG  10000921 MSFT 00000097)
[    0.000000] ACPI: OEMB 7f7ae040 00061 (v01 A_M_I_ AMI_OEM  10000921 MSFT 00000097)
[    0.000000] ACPI: HPET 7f7a7430 00038 (v01 A_M_I_ OEMHPET  10000921 MSFT 00000097)
[    0.000000] ACPI: SSDT 7f7aeb80 004F0 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1151MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007f7a0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007f7a0
[    0.000000] On node 0 totalpages: 522031
[    0.000000] free_area_init_node: node 0, pgdat c1822dc0, node_mem_map f476c200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2304 pages used for memmap
[    0.000000]   HighMem zone: 292514 pages, LIFO batch:31
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
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e2000
[    0.000000] PM: Registered nosave memory: 00000000000e2000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 7f800000 (gap: 7f800000:7f600000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f77d7000 s31616 r0 d21632 u53248
[    0.000000] pcpu-alloc: s31616 r0 d21632 u53248 alloc=13*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517951
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.2.0-26-generic root=/dev/mapper/eee-root ro splash quiet pciehp.pciehp_force=1 pciehp.pciehp_poll=1 vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 8354048 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007f7a0)
[    0.000000] Memory: 2031896k/2088576k available (5615k kernel code, 56228k reserved, 2765k data, 712k init, 1179272k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc1830000 - 0xc18e2000   ( 712 kB)
[    0.000000]       .data : 0xc157be04 - 0xc182f4c0   (2765 kB)
[    0.000000]       .text : 0xc1000000 - 0xc157be04   (5615 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f4008000 soft=f400a000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1596.008 MHz processor.
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 3192.01 BogoMIPS (lpj=6384032)
[    0.004016] pid_max: default: 32768 minimum: 301
[    0.004073] Security Framework initialized
[    0.004116] AppArmor: AppArmor initialized
[    0.004121] Yama: becoming mindful.
[    0.004251] Mount-cache hash table entries: 512
[    0.004538] Initializing cgroup subsys cpuacct
[    0.004553] Initializing cgroup subsys memory
[    0.004573] Initializing cgroup subsys devices
[    0.004579] Initializing cgroup subsys freezer
[    0.004585] Initializing cgroup subsys blkio
[    0.004601] Initializing cgroup subsys perf_event
[    0.004649] Disabled fast string operations
[    0.004659] CPU: Physical Processor ID: 0
[    0.004664] CPU: Processor Core ID: 0
[    0.004670] mce: CPU supports 5 MCE banks
[    0.004685] CPU0: Thermal monitoring enabled (TM2)
[    0.004694] using mwait in idle threads.
[    0.010825] ACPI: Core revision 20110623
[    0.020026] ftrace: allocating 25884 entries in 51 pages
[    0.024107] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.028206] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.067908] CPU0: Intel(R) Atom(TM) CPU N270   @ 1.60GHz stepping 02
[    0.068003] Performance Events: PEBS fmt0+, Atom events, Intel PMU driver.
[    0.068003] ... version:                3
[    0.068003] ... bit width:              40
[    0.068003] ... generic registers:      2
[    0.068003] ... value mask:             000000ffffffffff
[    0.068003] ... max period:             000000007fffffff
[    0.068003] ... fixed-purpose events:   3
[    0.068003] ... event mask:             0000000700000003
[    0.068003] NMI watchdog enabled, takes one hw-pmu counter.
[    0.068003] CPU 1 irqstacks, hard=f40ea000 soft=f40ec000
[    0.068003] Booting Node   0, Processors  #1 Ok.
[    0.068003] smpboot cpu 1: start_ip = 9b000
[    0.008000] Initializing CPU#1
[    0.008000] Disabled fast string operations
[    0.156077] NMI watchdog enabled, takes one hw-pmu counter.
[    0.156170] Brought up 2 CPUs
[    0.156179] Total of 2 processors activated (6383.95 BogoMIPS).
[    0.156777] devtmpfs: initialized
[    0.156777] EVM: security.selinux
[    0.156777] EVM: security.SMACK64
[    0.156777] EVM: security.capability
[    0.156777] PM: Registering ACPI NVS region at 7f7ae000 (270336 bytes)
[    0.160731] print_constraints: dummy: 
[    0.160792] RTC time: 22:00:04, date: 07/06/12
[    0.160887] NET: Registered protocol family 16
[    0.161038] Trying to unpack rootfs image as initramfs...
[    0.161443] EISA bus registered
[    0.161563] ACPI: bus type pci registered
[    0.161782] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xe0000000-0xe3ffffff] (base 0xe0000000)
[    0.161793] PCI: not using MMCONFIG
[    0.162137] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
[    0.162147] PCI: Using configuration type 1 for base access
[    0.176369] bio: create slab <bio-0> at 0
[    0.176658] ACPI: Added _OSI(Module Device)
[    0.176668] ACPI: Added _OSI(Processor Device)
[    0.176676] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.176684] ACPI: Added _OSI(Processor Aggregator Device)
[    0.180938] ACPI: EC: Look up EC in DSDT
[    0.185198] ACPI: Executed 1 blocks of module-level executable AML code
[    0.193105] ACPI: SSDT 7f7ae180 0023C (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.196650] ACPI: Dynamic OEM Table Load:
[    0.196663] ACPI: SSDT   (null) 0023C (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.197216] ACPI: SSDT 7f7ae450 00724 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.198210] ACPI: Dynamic OEM Table Load:
[    0.198222] ACPI: SSDT   (null) 00724 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.199101] ACPI: SSDT 7f7ae0b0 000CC (v01  PmRef  Cpu1Ist 00003000 INTL 20051117)
[    0.200135] ACPI: Dynamic OEM Table Load:
[    0.200147] ACPI: SSDT   (null) 000CC (v01  PmRef  Cpu1Ist 00003000 INTL 20051117)
[    0.200502] ACPI: SSDT 7f7ae3c0 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20051117)
[    0.201503] ACPI: Dynamic OEM Table Load:
[    0.201515] ACPI: SSDT   (null) 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20051117)
[    0.202519] ACPI: Interpreter enabled
[    0.202548] ACPI: (supports S0 S3 S4 S5)
[    0.202617] ACPI: Using IOAPIC for interrupt routing
[    0.202711] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xe0000000-0xe3ffffff] (base 0xe0000000)
[    0.204362] PCI: MMCONFIG at [mem 0xe0000000-0xe3ffffff] reserved in ACPI motherboard resources
[    0.204373] PCI: Using MMCONFIG for extended config space
[    0.216696] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.221852] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    0.222335] ACPI: No dock devices found.
[    0.222344] HEST: Table not found.
[    0.222358] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.222651] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.223212] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.223223] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.223233] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.223243] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.223253] pci_root PNP0A08:00: host bridge window [mem 0x7f800000-0xffffffff]
[    0.223295] pci 0000:00:00.0: [8086:27ac] type 0 class 0x000600
[    0.223391] pci 0000:00:02.0: [8086:27ae] type 0 class 0x000300
[    0.223415] pci 0000:00:02.0: reg 10: [mem 0xf7f00000-0xf7f7ffff]
[    0.223431] pci 0000:00:02.0: reg 14: [io  0xdc00-0xdc07]
[    0.223446] pci 0000:00:02.0: reg 18: [mem 0xd0000000-0xdfffffff pref]
[    0.223462] pci 0000:00:02.0: reg 1c: [mem 0xf7ec0000-0xf7efffff]
[    0.223543] pci 0000:00:02.1: [8086:27a6] type 0 class 0x000380
[    0.223565] pci 0000:00:02.1: reg 10: [mem 0xf7f80000-0xf7ffffff]
[    0.223740] pci 0000:00:1b.0: [8086:27d8] type 0 class 0x000403
[    0.223782] pci 0000:00:1b.0: reg 10: [mem 0xf7eb8000-0xf7ebbfff 64bit]
[    0.223939] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.223953] pci 0000:00:1b.0: PME# disabled
[    0.224025] pci 0000:00:1c.0: [8086:27d0] type 1 class 0x000604
[    0.224180] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.224192] pci 0000:00:1c.0: PME# disabled
[    0.224250] pci 0000:00:1c.1: [8086:27d2] type 1 class 0x000604
[    0.224402] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.224414] pci 0000:00:1c.1: PME# disabled
[    0.224472] pci 0000:00:1c.3: [8086:27d6] type 1 class 0x000604
[    0.224624] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.224637] pci 0000:00:1c.3: PME# disabled
[    0.224699] pci 0000:00:1d.0: [8086:27c8] type 0 class 0x000c03
[    0.224789] pci 0000:00:1d.0: reg 20: [io  0xd400-0xd41f]
[    0.224865] pci 0000:00:1d.1: [8086:27c9] type 0 class 0x000c03
[    0.224946] pci 0000:00:1d.1: reg 20: [io  0xd480-0xd49f]
[    0.225019] pci 0000:00:1d.2: [8086:27ca] type 0 class 0x000c03
[    0.225100] pci 0000:00:1d.2: reg 20: [io  0xd800-0xd81f]
[    0.225173] pci 0000:00:1d.3: [8086:27cb] type 0 class 0x000c03
[    0.225254] pci 0000:00:1d.3: reg 20: [io  0xd880-0xd89f]
[    0.225343] pci 0000:00:1d.7: [8086:27cc] type 0 class 0x000c03
[    0.225382] pci 0000:00:1d.7: reg 10: [mem 0xf7eb7c00-0xf7eb7fff]
[    0.225534] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.225548] pci 0000:00:1d.7: PME# disabled
[    0.225596] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.225749] pci 0000:00:1f.0: [8086:27b9] type 0 class 0x000601
[    0.225890] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0380 (mask 0003)
[    0.225902] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0290 (mask 0007)
[    0.225914] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0068 (mask 0003)
[    0.226003] pci 0000:00:1f.2: [8086:27c4] type 0 class 0x000101
[    0.226037] pci 0000:00:1f.2: reg 10: [io  0x0000-0x0007]
[    0.226059] pci 0000:00:1f.2: reg 14: [io  0x0000-0x0003]
[    0.226080] pci 0000:00:1f.2: reg 18: [io  0x0000-0x0007]
[    0.226102] pci 0000:00:1f.2: reg 1c: [io  0x0000-0x0003]
[    0.226123] pci 0000:00:1f.2: reg 20: [io  0xffa0-0xffaf]
[    0.226203] pci 0000:00:1f.2: PME# supported from D3hot
[    0.226215] pci 0000:00:1f.2: PME# disabled
[    0.226326] pci 0000:00:1c.0: PCI bridge to [bus 04-04]
[    0.226474] pci 0000:03:00.0: [1969:1026] type 0 class 0x000200
[    0.226522] pci 0000:03:00.0: reg 10: [mem 0xfbfc0000-0xfbffffff 64bit]
[    0.226549] pci 0000:03:00.0: reg 18: [io  0xec00-0xec7f]
[    0.226726] pci 0000:03:00.0: PME# supported from D3hot D3cold
[    0.226739] pci 0000:03:00.0: PME# disabled
[    0.226782] pci 0000:03:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.226809] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.226822] pci 0000:00:1c.1:   bridge window [io  0xe000-0xefff]
[    0.226834] pci 0000:00:1c.1:   bridge window [mem 0xfbf00000-0xfbffffff]
[    0.226933] pci 0000:00:1c.3: PCI bridge to [bus 01-02]
[    0.226950] pci 0000:00:1c.3:   bridge window [mem 0xf8000000-0xfbefffff]
[    0.226968] pci 0000:00:1c.3:   bridge window [mem 0xf0000000-0xf6ffffff 64bit pref]
[    0.227088] pci 0000:00:1e.0: PCI bridge to [bus 05-05] (subtractive decode)
[    0.227114] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.227124] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.227135] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.227146] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.227157] pci 0000:00:1e.0:   bridge window [mem 0x7f800000-0xffffffff] (subtractive decode)
[    0.227202] pci_bus 0000:00: on NUMA node 0
[    0.227217] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.227713] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[    0.227798] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[    0.227969]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.227982]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.227990] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.250688] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.250877] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.251059] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.251250] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.251436] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.251628] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.251814] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.252003] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.252458] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.252487] vgaarb: loaded
[    0.252493] vgaarb: bridge control possible 0000:00:02.0
[    0.253074] i2c-core: driver [aat2870] using legacy suspend method
[    0.253082] i2c-core: driver [aat2870] using legacy resume method
[    0.253369] SCSI subsystem initialized
[    0.253575] libata version 3.00 loaded.
[    0.253799] usbcore: registered new interface driver usbfs
[    0.253851] usbcore: registered new interface driver hub
[    0.253977] usbcore: registered new device driver usb
[    0.254386] PCI: Using ACPI for IRQ routing
[    0.254454] PCI: pci_cache_line_size set to 64 bytes
[    0.254604] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.254614] reserve RAM buffer: 000000007f7a0000 - 000000007fffffff 
[    0.254994] NetLabel: Initializing
[    0.255001] NetLabel:  domain hash size = 128
[    0.255007] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.255042] NetLabel:  unlabeled traffic allowed by default
[    0.255256] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.255283] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.255299] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.260174] Switching to clocksource hpet
[    0.285709] AppArmor: AppArmor Filesystem Enabled
[    0.285793] pnp: PnP ACPI init
[    0.285846] ACPI: bus type pnp registered
[    0.286163] pnp 00:00: [bus 00-ff]
[    0.286174] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.286183] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.286191] pnp 00:00: [io  0x0d00-0xffff window]
[    0.286200] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.286210] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.286219] pnp 00:00: [mem 0x7f800000-0xffffffff window]
[    0.286409] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.286451] pnp 00:01: [mem 0xfed13000-0xfed19fff]
[    0.286607] system 00:01: [mem 0xfed13000-0xfed19fff] has been reserved
[    0.286620] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.286688] pnp 00:02: [dma 4]
[    0.286697] pnp 00:02: [io  0x0000-0x000f]
[    0.286710] pnp 00:02: [io  0x0081-0x0083]
[    0.286718] pnp 00:02: [io  0x0087]
[    0.286725] pnp 00:02: [io  0x0089-0x008b]
[    0.286732] pnp 00:02: [io  0x008f]
[    0.286740] pnp 00:02: [io  0x00c0-0x00df]
[    0.286841] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.286892] pnp 00:03: [io  0x0070-0x0071]
[    0.286920] pnp 00:03: [irq 8]
[    0.287030] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.287154] pnp 00:04: [io  0x0060]
[    0.287162] pnp 00:04: [io  0x0064]
[    0.287179] pnp 00:04: [irq 1]
[    0.287284] pnp 00:04: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.287395] pnp 00:05: [irq 12]
[    0.287513] pnp 00:05: Plug and Play ACPI device, IDs SYN0a04 SYN0a00 SYN0002 PNP0f13 (active)
[    0.287553] pnp 00:06: [io  0x0061]
[    0.287660] pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.287698] pnp 00:07: [io  0x00f0-0x00ff]
[    0.287715] pnp 00:07: [irq 13]
[    0.287818] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.288295] pnp 00:08: [io  0x0010-0x001f]
[    0.288304] pnp 00:08: [io  0x0022-0x003f]
[    0.288312] pnp 00:08: [io  0x0044-0x004d]
[    0.288320] pnp 00:08: [io  0x0050-0x005e]
[    0.288327] pnp 00:08: [io  0x0063]
[    0.288335] pnp 00:08: [io  0x0065]
[    0.288342] pnp 00:08: [io  0x0067-0x006f]
[    0.288350] pnp 00:08: [io  0x0072-0x007f]
[    0.288358] pnp 00:08: [io  0x0080]
[    0.288366] pnp 00:08: [io  0x0084-0x0086]
[    0.288374] pnp 00:08: [io  0x0088]
[    0.288381] pnp 00:08: [io  0x008c-0x008e]
[    0.288388] pnp 00:08: [io  0x0090-0x009f]
[    0.288397] pnp 00:08: [io  0x00a2-0x00bf]
[    0.288405] pnp 00:08: [io  0x00e0-0x00ef]
[    0.288413] pnp 00:08: [io  0x025c-0x025f]
[    0.288422] pnp 00:08: [io  0x0380-0x0383]
[    0.288431] pnp 00:08: [io  0x0400-0x041f]
[    0.288439] pnp 00:08: [io  0x04d0-0x04d1]
[    0.288446] pnp 00:08: [io  0x0800-0x087f]
[    0.288454] pnp 00:08: [io  0x0400-0x03ff disabled]
[    0.288461] pnp 00:08: [io  0x0480-0x04bf]
[    0.288469] pnp 00:08: [mem 0x8c000000-0x8c01ffff]
[    0.288478] pnp 00:08: [mem 0xfed1c000-0xfed1ffff]
[    0.288486] pnp 00:08: [mem 0xfed20000-0xfed3ffff]
[    0.288494] pnp 00:08: [mem 0xfed50000-0xfed8ffff]
[    0.288504] pnp 00:08: [mem 0xffb00000-0xffbfffff]
[    0.288512] pnp 00:08: [mem 0xfff00000-0xffffffff]
[    0.288763] system 00:08: [io  0x025c-0x025f] has been reserved
[    0.288775] system 00:08: [io  0x0380-0x0383] has been reserved
[    0.288785] system 00:08: [io  0x0400-0x041f] has been reserved
[    0.288795] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.288805] system 00:08: [io  0x0800-0x087f] has been reserved
[    0.288816] system 00:08: [io  0x0480-0x04bf] has been reserved
[    0.288828] system 00:08: [mem 0x8c000000-0x8c01ffff] has been reserved
[    0.288839] system 00:08: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.288850] system 00:08: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.288861] system 00:08: [mem 0xfed50000-0xfed8ffff] has been reserved
[    0.288872] system 00:08: [mem 0xffb00000-0xffbfffff] has been reserved
[    0.288883] system 00:08: [mem 0xfff00000-0xffffffff] could not be reserved
[    0.288896] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.289132] pnp 00:09: [mem 0xfed00000-0xfed003ff]
[    0.289248] pnp 00:09: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.289445] pnp 00:0a: [mem 0xfec00000-0xfec00fff]
[    0.289455] pnp 00:0a: [mem 0xfee00000-0xfee00fff]
[    0.289636] system 00:0a: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.289648] system 00:0a: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.289662] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.289800] pnp 00:0b: [mem 0xe0000000-0xe3ffffff]
[    0.289963] system 00:0b: [mem 0xe0000000-0xe3ffffff] has been reserved
[    0.289977] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.290632] pnp 00:0c: [mem 0x00000000-0x0009ffff]
[    0.290643] pnp 00:0c: [mem 0x000c0000-0x000cffff]
[    0.290652] pnp 00:0c: [mem 0x000e0000-0x000fffff]
[    0.290660] pnp 00:0c: [mem 0x00100000-0x7f7fffff]
[    0.290669] pnp 00:0c: [mem 0x00000000-0xffffffff disabled]
[    0.290868] system 00:0c: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.290880] system 00:0c: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.290891] system 00:0c: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.290902] system 00:0c: [mem 0x00100000-0x7f7fffff] could not be reserved
[    0.290915] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.291540] pnp: PnP ACPI: found 13 devices
[    0.291548] ACPI: ACPI bus type pnp unregistered
[    0.291558] PnPBIOS: Disabled by ACPI PNP
[    0.334234] PCI: max bus depth: 1 pci_try_num: 2
[    0.334332] pci 0000:00:1c.3: BAR 13: assigned [io  0x1000-0x1fff]
[    0.334347] pci 0000:00:1c.1: BAR 15: assigned [mem 0x7f800000-0x7f9fffff 64bit pref]
[    0.334361] pci 0000:00:1c.0: BAR 14: assigned [mem 0x7fa00000-0x7fbfffff]
[    0.334375] pci 0000:00:1c.0: BAR 15: assigned [mem 0x7fc00000-0x7fdfffff 64bit pref]
[    0.334389] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
[    0.334401] pci 0000:00:1c.0: PCI bridge to [bus 04-04]
[    0.334413] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.334427] pci 0000:00:1c.0:   bridge window [mem 0x7fa00000-0x7fbfffff]
[    0.334441] pci 0000:00:1c.0:   bridge window [mem 0x7fc00000-0x7fdfffff 64bit pref]
[    0.334458] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.334468] pci 0000:00:1c.1:   bridge window [io  0xe000-0xefff]
[    0.334483] pci 0000:00:1c.1:   bridge window [mem 0xfbf00000-0xfbffffff]
[    0.334496] pci 0000:00:1c.1:   bridge window [mem 0x7f800000-0x7f9fffff 64bit pref]
[    0.334513] pci 0000:00:1c.3: PCI bridge to [bus 01-02]
[    0.334523] pci 0000:00:1c.3:   bridge window [io  0x1000-0x1fff]
[    0.334537] pci 0000:00:1c.3:   bridge window [mem 0xf8000000-0xfbefffff]
[    0.334551] pci 0000:00:1c.3:   bridge window [mem 0xf0000000-0xf6ffffff 64bit pref]
[    0.334568] pci 0000:00:1e.0: PCI bridge to [bus 05-05]
[    0.334605] pci 0000:00:1c.0: enabling device (0104 -> 0107)
[    0.334645] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.334660] pci 0000:00:1c.0: setting latency timer to 64
[    0.334692] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.334705] pci 0000:00:1c.1: setting latency timer to 64
[    0.334722] pci 0000:00:1c.3: enabling device (0106 -> 0107)
[    0.334746] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.334759] pci 0000:00:1c.3: setting latency timer to 64
[    0.334778] pci 0000:00:1e.0: setting latency timer to 64
[    0.334790] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.334799] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.334809] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.334818] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.334827] pci_bus 0000:00: resource 8 [mem 0x7f800000-0xffffffff]
[    0.334837] pci_bus 0000:04: resource 0 [io  0x2000-0x2fff]
[    0.334846] pci_bus 0000:04: resource 1 [mem 0x7fa00000-0x7fbfffff]
[    0.334856] pci_bus 0000:04: resource 2 [mem 0x7fc00000-0x7fdfffff 64bit pref]
[    0.334866] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
[    0.334875] pci_bus 0000:03: resource 1 [mem 0xfbf00000-0xfbffffff]
[    0.334885] pci_bus 0000:03: resource 2 [mem 0x7f800000-0x7f9fffff 64bit pref]
[    0.334895] pci_bus 0000:01: resource 0 [io  0x1000-0x1fff]
[    0.334904] pci_bus 0000:01: resource 1 [mem 0xf8000000-0xfbefffff]
[    0.334913] pci_bus 0000:01: resource 2 [mem 0xf0000000-0xf6ffffff 64bit pref]
[    0.334924] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7]
[    0.334932] pci_bus 0000:05: resource 5 [io  0x0d00-0xffff]
[    0.334941] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff]
[    0.334951] pci_bus 0000:05: resource 7 [mem 0x000d0000-0x000dffff]
[    0.334960] pci_bus 0000:05: resource 8 [mem 0x7f800000-0xffffffff]
[    0.335094] NET: Registered protocol family 2
[    0.335305] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.336273] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.337417] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.338012] TCP: Hash tables configured (established 131072 bind 65536)
[    0.338024] TCP reno registered
[    0.338040] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.338066] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.338349] NET: Registered protocol family 1
[    0.338401] pci 0000:00:02.0: Boot video device
[    0.338495] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.338529] pci 0000:00:1d.0: PCI INT A disabled
[    0.338553] pci 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.338583] pci 0000:00:1d.1: PCI INT B disabled
[    0.338618] pci 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.338648] pci 0000:00:1d.2: PCI INT C disabled
[    0.338671] pci 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.338701] pci 0000:00:1d.3: PCI INT D disabled
[    0.338726] pci 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.338799] pci 0000:00:1d.7: PCI INT A disabled
[    0.338839] PCI: CLS 32 bytes, default 64
[    0.340169] audit: initializing netlink socket (disabled)
[    0.340200] type=2000 audit(1341612004.336:1): initialized
[    0.406497] highmem bounce pool size: 64 pages
[    0.406518] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.424812] VFS: Disk quotas dquot_6.5.2
[    0.425050] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.427171] fuse init (API version 7.17)
[    0.427567] msgmni has been set to 1665
[    0.428872] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.428985] io scheduler noop registered
[    0.428993] io scheduler deadline registered
[    0.429020] io scheduler cfq registered (default)
[    0.429417] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.429520] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.429691] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.429779] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.429941] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.430036] pcieport 0000:00:1c.3: irq 42 for MSI/MSI-X
[    0.430321] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.430431] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.430690] intel_idle: MWAIT substates: 0x20220
[    0.430710] intel_idle: v0.4 model 0x1C
[    0.430716] intel_idle: lapic_timer_reliable_states 0x2
[    0.430724] Marking TSC unstable due to TSC halts in idle states deeper than C2
[    0.430920] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.431106] ACPI: AC Adapter [AC0] (on-line)
[    0.431501] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.436497] ACPI: Lid Switch [LID]
[    0.436743] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    0.436759] ACPI: Sleep Button [SLPB]
[    0.436930] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
[    0.436943] ACPI: Power Button [PWRB]
[    0.437125] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.437137] ACPI: Power Button [PWRF]
[    0.453351] thermal LNXTHERM:00: registered as thermal_zone0
[    0.453363] ACPI: Thermal Zone [TZ00] (49 C)
[    0.453476] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.453508] ACPI: Battery Slot [BAT0] (battery present)
[    0.453623] ERST: Table is not found!
[    0.453629] GHES: HEST is not enabled!
[    0.453904] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.454771] isapnp: Scanning for PnP cards...
[    0.811252] isapnp: No Plug & Play device found
[    0.819273] ACPI: Battery Slot [BAT0] (battery present)
[    1.276083] Freeing initrd memory: 20776k freed
[    1.317310] Linux agpgart interface v0.103
[    1.317487] agpgart-intel 0000:00:00.0: Intel 945GME Chipset
[    1.317652] agpgart-intel 0000:00:00.0: detected gtt size: 262144K total, 262144K mappable
[    1.317840] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    1.318123] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    1.322519] brd: module loaded
[    1.324872] loop: module loaded
[    1.325277] ata_piix 0000:00:1f.2: version 2.13
[    1.325311] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.325323] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    1.325396] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.326212] scsi0 : ata_piix
[    1.326439] scsi1 : ata_piix
[    1.329221] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    1.329230] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    1.330462] Fixed MDIO Bus: probed
[    1.330528] tun: Universal TUN/TAP device driver, 1.6
[    1.330533] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.330709] PPP generic driver version 2.4.2
[    1.331018] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.331066] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.331105] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.331114] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.331246] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.331287] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    1.331307] ehci_hcd 0000:00:1d.7: debug port 1
[    1.335211] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.335252] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf7eb7c00
[    1.348039] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.348383] hub 1-0:1.0: USB hub found
[    1.348396] hub 1-0:1.0: 8 ports detected
[    1.348590] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.348628] uhci_hcd: USB Universal Host Controller Interface driver
[    1.348693] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.348712] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.348720] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.348867] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.348912] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d400
[    1.349274] hub 2-0:1.0: USB hub found
[    1.349286] hub 2-0:1.0: 2 ports detected
[    1.349437] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.349454] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.349461] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.349600] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.349665] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d480
[    1.350029] hub 3-0:1.0: USB hub found
[    1.350043] hub 3-0:1.0: 2 ports detected
[    1.350189] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.350211] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.350219] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.350349] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.350411] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d800
[    1.350773] hub 4-0:1.0: USB hub found
[    1.350785] hub 4-0:1.0: 2 ports detected
[    1.350925] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    1.350942] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.350950] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.351086] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.351150] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d880
[    1.351495] hub 5-0:1.0: USB hub found
[    1.351506] hub 5-0:1.0: 2 ports detected
[    1.351803] usbcore: registered new interface driver libusual
[    1.351932] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.378142] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.378162] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.378571] mousedev: PS/2 mouse device common for all mice
[    1.380786] rtc_cmos 00:03: RTC can wake from S4
[    1.381017] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.381067] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    1.381262] device-mapper: uevent: version 1.0.3
[    1.381476] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.381575] EISA: Probing bus 0 at eisa.0
[    1.381582] EISA: Cannot allocate resource for mainboard
[    1.381589] Cannot allocate resource for EISA slot 1
[    1.381595] Cannot allocate resource for EISA slot 2
[    1.381600] Cannot allocate resource for EISA slot 3
[    1.381606] Cannot allocate resource for EISA slot 4
[    1.381612] Cannot allocate resource for EISA slot 5
[    1.381617] Cannot allocate resource for EISA slot 6
[    1.381623] Cannot allocate resource for EISA slot 7
[    1.381628] Cannot allocate resource for EISA slot 8
[    1.381633] EISA: Detected 0 cards.
[    1.381653] cpufreq-nforce2: No nForce2 chipset.
[    1.381834] cpuidle: using governor ladder
[    1.382135] cpuidle: using governor menu
[    1.382141] EFI Variables Facility v0.08 2004-May-17
[    1.382761] TCP cubic registered
[    1.383073] NET: Registered protocol family 10
[    1.384521] NET: Registered protocol family 17
[    1.384534] Registering the dns_resolver key type
[    1.384602] Using IPI No-Shortcut mode
[    1.385021] PM: Hibernation image not present or could not be loaded.
[    1.385050] registered taskstats version 1
[    1.406314] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.409137]   Magic number: 4:751:46
[    1.409300] rtc_cmos 00:03: setting system clock to 2012-07-06 22:00:06 UTC (1341612006)
[    1.410020] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.410025] EDD information not available.
[    1.492568] ata1.00: ATA-8: OCZ-ONYX, 1.7, max UDMA/133
[    1.492577] ata1.00: 62533296 sectors, multi 1: LBA48 NCQ (depth 0/32)
[    1.508534] ata1.00: configured for UDMA/133
[    1.508913] scsi 0:0:0:0: Direct-Access     ATA      OCZ-ONYX         1.7  PQ: 0 ANSI: 5
[    1.509310] sd 0:0:0:0: [sda] 62533296 512-byte logical blocks: (32.0 GB/29.8 GiB)
[    1.509473] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.509677] sd 0:0:0:0: [sda] Write Protect is off
[    1.509687] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.509801] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.511545]  sda: sda1 sda2 < sda5 >
[    1.512754] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.512824] Freeing unused kernel memory: 712k freed
[    1.513411] Write protecting the kernel text: 5616k
[    1.513504] Write protecting the kernel read-only data: 2324k
[    1.562126] udevd[90]: starting version 175
[    1.740190] wmi: Mapper loaded
[    1.758738] acpi device:1b: registered as cooling_device2
[    1.759000] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5
[    1.763385] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    1.783598] usb 1-8: new high-speed USB device number 3 using ehci_hcd
[    1.825640] [drm] Initialized drm 1.1.0 20060810
[    1.858157] ATL1E 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.858188] ATL1E 0000:03:00.0: setting latency timer to 64
[    1.903360] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.903376] i915 0000:00:02.0: setting latency timer to 64
[    1.956797] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    1.956807] [drm] Driver supports precise vblank timestamp query.
[    1.957478] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    2.252229] usb 3-1: new full-speed USB device number 2 using uhci_hcd
[    2.291871] [drm] initialized overlay support
[    2.309965] fbcon: inteldrmfb (fb0) is primary device
[    2.311021] Console: switching to colour frame buffer device 128x37
[    2.311074] fb0: inteldrmfb frame buffer device
[    2.311079] drm: registered panic notifier
[    2.311115] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   15.187401] EXT4-fs (dm-1): mounted filesystem with ordered data mode. Opts: (null)
[   16.949988] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.024760] udevd[402]: starting version 175
[   17.283029] lp: driver loaded but no devices found
[   17.301835] Adding 2088956k swap on /dev/mapper/eee-swap_1.  Priority:-1 extents:1 across:2088956k SS
[   17.317901] EXT4-fs (dm-1): re-mounted. Opts: discard,errors=remount-ro
[   18.396282] intel_rng: FWH not detected
[   18.556811] leds_ss4200: no LED devices found
[   18.564327] type=1400 audit(1341626423.653:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=598 comm="apparmor_parser"
[   18.565928] type=1400 audit(1341626423.653:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=598 comm="apparmor_parser"
[   18.566790] type=1400 audit(1341626423.653:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=598 comm="apparmor_parser"
[   18.595115] Bluetooth: Core ver 2.16
[   18.598895] NET: Registered protocol family 31
[   18.598906] Bluetooth: HCI device and connection manager initialized
[   18.598917] Bluetooth: HCI socket layer initialized
[   18.598924] Bluetooth: L2CAP socket layer initialized
[   18.598950] Bluetooth: SCO socket layer initialized
[   18.610481] Bluetooth: Atheros AR30xx firmware driver ver 1.0
[   19.009905] psmouse serio1: hgpk: ID: 10 00 64
[   19.012397] Linux video capture interface: v2.00
[   19.193888] Bluetooth: RFCOMM TTY layer initialized
[   19.193908] Bluetooth: RFCOMM socket layer initialized
[   19.193916] Bluetooth: RFCOMM ver 1.11
[   19.216067] psmouse serio1: elantech: assuming hardware version 2 (with firmware version 0x020030)
[   19.290278] psmouse serio1: elantech: Synaptics capabilities query result 0x00, 0x02, 0x64.
[   19.502204] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio1/input/input6
[   19.617921] uvcvideo: Found UVC 1.00 device CNF7129 (04f2:b071)
[   19.654175] input: CNF7129 as /devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/input/input7
[   19.660412] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.660422] Bluetooth: BNEP filters: protocol multicast
[   19.660629] usbcore: registered new interface driver uvcvideo
[   19.660638] USB Video Class driver (1.1.1)
[   19.773721] ppdev: user-space parallel port driver
[   19.931453] type=1400 audit(1341626425.017:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=797 comm="apparmor_parser"
[   19.933829] type=1400 audit(1341626425.021:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=797 comm="apparmor_parser"
[   20.095965] init: failsafe main process (737) killed by TERM signal
[   20.506422] asus_wmi: ASUS WMI generic driver loaded
[   20.508255] asus_wmi: Initialization: 0x0
[   20.508385] asus_wmi: BIOS WMI version: 0.8
[   20.508618] asus_wmi: SFUN value: 0x0
[   20.511785] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.512349] snd_hda_intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[   20.512573] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   20.527883] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input8
[   20.647896] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   20.649162] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   21.089075] type=1400 audit(1341626426.177:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=928 comm="apparmor_parser"
[   21.096819] type=1400 audit(1341626426.185:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=927 comm="apparmor_parser"
[   21.101810] type=1400 audit(1341626426.189:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=928 comm="apparmor_parser"
[   21.102685] type=1400 audit(1341626426.189:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=928 comm="apparmor_parser"
[   21.135949] type=1400 audit(1341626426.221:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=931 comm="apparmor_parser"
[   21.324915] usbcore: registered new interface driver ath3k
[   21.480126] usb 3-1: USB disconnect, device number 2
[   21.861226] asus_wmi: BIOS says wireless lan is unblocked, but the pci device is absent
[   21.861238] asus_wmi: skipped wireless hotplug as probably inappropriate for this model
[   21.861246] asus_wmi: Backlight controlled by ACPI video driver
[   22.142536] NET: Registered protocol family 15
[   22.727375] ATL1E 0000:03:00.0: irq 44 for MSI/MSI-X
[   22.728592] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.729779] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.960232] usb 3-1: new full-speed USB device number 3 using uhci_hcd
[   23.147323] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   23.152561] usbcore: registered new interface driver btusb
[   24.440079] init: plymouth-stop pre-start process (1441) terminated with status 1

```

---

