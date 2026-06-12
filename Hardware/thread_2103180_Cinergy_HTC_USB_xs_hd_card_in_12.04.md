---
title: "Cinergy HTC USB xs hd card in 12.04"
date: 2013-01-09
forum: Hardware
---

### Post by mercury1981 on 2013-01-09
Hi!

I have a Cinergy HTC USB xs hd card in my PC and I installed Ubuntu 12.04.

And now I'm trying to install it - I found the entry on [http://wiki.ubuntuusers.de/em28xx](http://wiki.ubuntuusers.de/em28xx) but there it states that the driver is no longer developed?

Could somebody please guide me through the installation process or has experience with this kind of hardware?

Thanks a lot!

---

### Post by mercury1981 on 2013-01-11
Nobody?

---

### Post by mercury1981 on 2013-01-14
I found [http://git.linuxtv.org/media_build.git](http://git.linuxtv.org/media_build.git) now and will try if this helps - will update this thread in case it works.

---

### Post by mercury1981 on 2013-01-15
Ok - I was able to compile the em28xx module but I'm having the problem, that /dev/video is not available.

Can anybody please help?

dmesg output:
> 
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-35-generic-pae (buildd@aatxe) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #55-Ubuntu SMP Wed Dec 5 18:04:39 UTC 2012 (Ubuntu 3.2.0-35.55-generic-pae 3.2.34)
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
[    0.000000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ff2fc00 (usable)
[    0.000000]  BIOS-e820: 000000003ff2fc00 - 000000003ff30000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003ff30000 - 000000003ff40000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ff40000 - 000000003fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fff0000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed13000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000feda0000 (reserved)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.3 present.
[    0.000000] DMI: MAXDATA                                 /D915GEV                        , BIOS EV91510A.86A.0332.2004.1201.0225 12/01/2004
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x3ff2f max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 040000000 mask FC0000000 uncachable
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 1GB, range: 1GB, type UC
[    0.000000] total RAM covered: 1024M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 64K     num_reg: 1      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 1GB, type WB
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] initial memory mapped : 0 - 02000000
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 1ffb000-2000000
[    0.000000] RAMDISK: 364ec000 - 3726e000
[    0.000000] ACPI: RSDP 000f4eb0 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 3ff30000 0003C (v01 INTEL  D915GEV  20041201 MSFT 00000097)
[    0.000000] ACPI: FACP 3ff30200 00081 (v02 INTEL  D915GEV  20041201 MSFT 00000097)
[    0.000000] ACPI: DSDT 3ff30440 05BDF (v01 INTEL  D915GEV  00000001 INTL 02002026)
[    0.000000] ACPI: FACS 3ff40000 00040
[    0.000000] ACPI: APIC 3ff30390 00068 (v01 INTEL  D915GEV  20041201 MSFT 00000097)
[    0.000000] ACPI: MCFG 3ff30400 0003C (v01 INTEL  D915GEV  20041201 MSFT 00000097)
[    0.000000] ACPI: ASF! 3ff36020 00099 (v16 LEGEND I865PASF 00000001 INTL 02002026)
[    0.000000] ACPI: TCPA 3ff360c0 00034 (v01 INTEL  TBLOEMID 00000001 MSFT 00000097)
[    0.000000] ACPI: WDDT 3ff360f4 00040 (v01 INTEL  OEMWDDT  00000001 INTL 02002026)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 131MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037bfe
[    0.000000]   HighMem  0x00037bfe -> 0x0003ff2f
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003ff2f
[    0.000000] On node 0 totalpages: 261822
[    0.000000] free_area_init_node: node 0, pgdat c186b1c0, node_mem_map f73fd200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 263 pages used for memmap
[    0.000000]   HighMem zone: 33322 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e6000
[    0.000000] PM: Registered nosave memory: 00000000000e6000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:a0000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f73da000 s34240 r0 d23104 u57344
[    0.000000] pcpu-alloc: s34240 r0 d23104 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259775
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-35-generic-pae root=UUID=dd81ea70-aeb5-4514-b19b-dfce063d5a3d ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 4190704 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:0003ff2f)
[    0.000000] Memory: 1009844k/1047740k available (5825k kernel code, 37444k reserved, 2849k data, 744k init, 134340k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc1879000 - 0xc1933000   ( 744 kB)
[    0.000000]       .data : 0xc15b05bc - 0xc1878a00   (2849 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15b05bc   (5825 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=128, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f5c08000 soft=f5c0a000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2999.784 MHz processor.
[    0.004002] Calibrating delay loop (skipped), value calculated using timer frequency.. 5999.56 BogoMIPS (lpj=11999136)
[    0.004009] pid_max: default: 32768 minimum: 301
[    0.004037] Security Framework initialized
[    0.004064] AppArmor: AppArmor initialized
[    0.004067] Yama: becoming mindful.
[    0.004146] Mount-cache hash table entries: 512
[    0.004323] Initializing cgroup subsys cpuacct
[    0.004332] Initializing cgroup subsys memory
[    0.004344] Initializing cgroup subsys devices
[    0.004348] Initializing cgroup subsys freezer
[    0.004351] Initializing cgroup subsys blkio
[    0.004362] Initializing cgroup subsys perf_event
[    0.004404] CPU: Physical Processor ID: 0
[    0.004407] CPU: Processor Core ID: 0
[    0.004411] mce: CPU supports 4 MCE banks
[    0.004425] CPU0: Thermal monitoring enabled (TM1)
[    0.004430] using mwait in idle threads.
[    0.009072] ACPI: Core revision 20110623
[    0.013191] ftrace: allocating 26576 entries in 53 pages
[    0.016066] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.016450] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.059695] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 01
[    0.060003] Performance Events: Netburst events, Netburst P4/Xeon PMU driver.
[    0.060003] ... version:                0
[    0.060003] ... bit width:              40
[    0.060003] ... generic registers:      18
[    0.060003] ... value mask:             000000ffffffffff
[    0.060003] ... max period:             0000007fffffffff
[    0.060003] ... fixed-purpose events:   0
[    0.060003] ... event mask:             000000000003ffff
[    0.060003] NMI watchdog enabled, takes one hw-pmu counter.
[    0.060003] CPU 1 irqstacks, hard=f5cc6000 soft=f5cd0000
[    0.060003] Booting Node   0, Processors  #1 Ok.
[    0.060003] smpboot cpu 1: start_ip = 9b000
[    0.008000] Initializing CPU#1
[    0.148046] NMI watchdog enabled, takes one hw-pmu counter.
[    0.148103] Brought up 2 CPUs
[    0.148109] Total of 2 processors activated (11999.89 BogoMIPS).
[    0.149111] devtmpfs: initialized
[    0.149111] EVM: security.selinux
[    0.149111] EVM: security.SMACK64
[    0.149111] EVM: security.capability
[    0.149111] PM: Registering ACPI NVS region at 3ff2fc00 (1024 bytes)
[    0.149111] PM: Registering ACPI NVS region at 3ff40000 (720896 bytes)
[    0.149772] print_constraints: dummy: 
[    0.149810] RTC time: 22:13:36, date: 01/14/13
[    0.149865] NET: Registered protocol family 16
[    0.149915] Trying to unpack rootfs image as initramfs...
[    0.150163] EISA bus registered
[    0.150194] ACPI: bus type pci registered
[    0.150326] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.150334] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.150338] PCI: Using MMCONFIG for extended config space
[    0.150343] PCI: Using configuration type 1 for base access
[    0.155081] bio: create slab <bio-0> at 0
[    0.155260] ACPI: Added _OSI(Module Device)
[    0.155266] ACPI: Added _OSI(Processor Device)
[    0.155271] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.155276] ACPI: Added _OSI(Processor Aggregator Device)
[    0.157797] ACPI: EC: Look up EC in DSDT
[    0.160814] ACPI: Executed 4 blocks of module-level executable AML code
[    0.167548] ACPI: Interpreter enabled
[    0.167578] ACPI: (supports S0 S1 S4 S5)
[    0.167622] ACPI: Using IOAPIC for interrupt routing
[    0.173788] ACPI: Power Resource [URP1] (off)
[    0.173881] ACPI: Power Resource [FDDP] (off)
[    0.173976] ACPI: Power Resource [LPTP] (off)
[    0.174103] ACPI: Power Resource [URP2] (off)
[    0.179179] ACPI: No dock devices found.
[    0.179186] HEST: Table not found.
[    0.179197] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.180426] ACPI Warning: For \_SB_.PCI0._OSC: Parameter count mismatch - ASL declared 5, ACPI requires 4 (20110623/nspredef-359)
[    0.180443] \_SB_.PCI0:_OSC evaluation returned wrong type
[    0.180447] _OSC request data:1 8 1f 
[    0.180459] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.180768] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.180775] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.180781] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.180788] pci_root PNP0A08:00: host bridge window [mem 0x40000000-0xffffffff] (ignored)
[    0.180808] pci 0000:00:00.0: [8086:2580] type 0 class 0x000600
[    0.180890] pci 0000:00:01.0: [8086:2581] type 1 class 0x000604
[    0.180966] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.180974] pci 0000:00:01.0: PME# disabled
[    0.181048] pci 0000:00:1b.0: [8086:2668] type 0 class 0x000403
[    0.181073] pci 0000:00:1b.0: reg 10: [mem 0xb8500000-0xb8503fff 64bit]
[    0.181170] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.181178] pci 0000:00:1b.0: PME# disabled
[    0.181210] pci 0000:00:1c.0: [8086:2660] type 1 class 0x000604
[    0.181311] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.181318] pci 0000:00:1c.0: PME# disabled
[    0.181356] pci 0000:00:1c.1: [8086:2662] type 1 class 0x000604
[    0.181460] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.181468] pci 0000:00:1c.1: PME# disabled
[    0.181502] pci 0000:00:1c.2: [8086:2664] type 1 class 0x000604
[    0.181602] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.181610] pci 0000:00:1c.2: PME# disabled
[    0.181644] pci 0000:00:1c.3: [8086:2666] type 1 class 0x000604
[    0.181749] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.181758] pci 0000:00:1c.3: PME# disabled
[    0.181793] pci 0000:00:1d.0: [8086:2658] type 0 class 0x000c03
[    0.181850] pci 0000:00:1d.0: reg 20: [io  0xcc00-0xcc1f]
[    0.181897] pci 0000:00:1d.1: [8086:2659] type 0 class 0x000c03
[    0.181954] pci 0000:00:1d.1: reg 20: [io  0xd000-0xd01f]
[    0.182000] pci 0000:00:1d.2: [8086:265a] type 0 class 0x000c03
[    0.182056] pci 0000:00:1d.2: reg 20: [io  0xd400-0xd41f]
[    0.182102] pci 0000:00:1d.3: [8086:265b] type 0 class 0x000c03
[    0.182158] pci 0000:00:1d.3: reg 20: [io  0xd800-0xd81f]
[    0.182217] pci 0000:00:1d.7: [8086:265c] type 0 class 0x000c03
[    0.182248] pci 0000:00:1d.7: reg 10: [mem 0xb8504000-0xb85043ff]
[    0.182362] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.182371] pci 0000:00:1d.7: PME# disabled
[    0.182398] pci 0000:00:1e.0: [8086:244e] type 1 class 0x000604
[    0.182485] pci 0000:00:1f.0: [8086:2640] type 0 class 0x000601
[    0.182596] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.182612] pci 0000:00:1f.0: LPC Generic IO decode 1 PIO at 0680-06ff
[    0.182619] pci 0000:00:1f.0: LPC Generic IO decode 2 PIO at 4700-470f
[    0.182650] pci 0000:00:1f.1: [8086:266f] type 0 class 0x000101
[    0.182671] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
[    0.182686] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
[    0.182700] pci 0000:00:1f.1: reg 18: [io  0x0000-0x0007]
[    0.182715] pci 0000:00:1f.1: reg 1c: [io  0x0000-0x0003]
[    0.182730] pci 0000:00:1f.1: reg 20: [io  0xffa0-0xffaf]
[    0.182787] pci 0000:00:1f.2: [8086:2651] type 0 class 0x000101
[    0.182810] pci 0000:00:1f.2: reg 10: [io  0xec00-0xec07]
[    0.182824] pci 0000:00:1f.2: reg 14: [io  0xe800-0xe803]
[    0.182837] pci 0000:00:1f.2: reg 18: [io  0xe400-0xe407]
[    0.182850] pci 0000:00:1f.2: reg 1c: [io  0xe000-0xe003]
[    0.182863] pci 0000:00:1f.2: reg 20: [io  0xdc00-0xdc0f]
[    0.182915] pci 0000:00:1f.2: PME# supported from D3hot
[    0.182922] pci 0000:00:1f.2: PME# disabled
[    0.182943] pci 0000:00:1f.3: [8086:266a] type 0 class 0x000c05
[    0.183010] pci 0000:00:1f.3: reg 20: [io  0xc800-0xc81f]
[    0.183121] pci 0000:01:00.0: [1002:3e50] type 0 class 0x000300
[    0.183143] pci 0000:01:00.0: reg 10: [mem 0xc0000000-0xcfffffff pref]
[    0.183158] pci 0000:01:00.0: reg 14: [io  0xa800-0xa8ff]
[    0.183171] pci 0000:01:00.0: reg 18: [mem 0xa8000000-0xa800ffff]
[    0.183210] pci 0000:01:00.0: reg 30: [mem 0xb0000000-0xb001ffff pref]
[    0.183259] pci 0000:01:00.0: supports D1 D2
[    0.183292] pci 0000:01:00.1: [1002:3e70] type 0 class 0x000380
[    0.183309] pci 0000:01:00.1: reg 10: [mem 0xb0020000-0xb002ffff]
[    0.183398] pci 0000:01:00.1: supports D1 D2
[    0.183420] pci 0000:01:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.183437] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.183444] pci 0000:00:01.0:   bridge window [io  0xa000-0xafff]
[    0.183452] pci 0000:00:01.0:   bridge window [mem 0xa8000000-0xb7ffffff]
[    0.183459] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff pref]
[    0.183524] pci 0000:00:1c.0: PCI bridge to [bus 05-05]
[    0.183535] pci 0000:00:1c.0:   bridge window [mem 0xb8300000-0xb83fffff]
[    0.183547] pci 0000:00:1c.0:   bridge window [mem 0xd0300000-0xd03fffff 64bit pref]
[    0.183636] pci 0000:04:00.0: [11ab:4361] type 0 class 0x000200
[    0.183669] pci 0000:04:00.0: reg 10: [mem 0xb8220000-0xb8223fff 64bit]
[    0.183688] pci 0000:04:00.0: reg 18: [io  0xb800-0xb8ff]
[    0.183745] pci 0000:04:00.0: reg 30: [mem 0xb8200000-0xb821ffff pref]
[    0.183833] pci 0000:04:00.0: supports D1 D2
[    0.183838] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.183846] pci 0000:04:00.0: PME# disabled
[    0.183866] pci 0000:04:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.183881] pci 0000:00:1c.1: PCI bridge to [bus 04-04]
[    0.183889] pci 0000:00:1c.1:   bridge window [io  0xb000-0xbfff]
[    0.183897] pci 0000:00:1c.1:   bridge window [mem 0xb8200000-0xb82fffff]
[    0.183908] pci 0000:00:1c.1:   bridge window [mem 0xd0200000-0xd02fffff 64bit pref]
[    0.183968] pci 0000:00:1c.2: PCI bridge to [bus 03-03]
[    0.183978] pci 0000:00:1c.2:   bridge window [mem 0xb8100000-0xb81fffff]
[    0.183989] pci 0000:00:1c.2:   bridge window [mem 0xd0100000-0xd01fffff 64bit pref]
[    0.184068] pci 0000:00:1c.3: PCI bridge to [bus 02-02]
[    0.184079] pci 0000:00:1c.3:   bridge window [mem 0xb8000000-0xb80fffff]
[    0.184091] pci 0000:00:1c.3:   bridge window [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.184146] pci 0000:06:01.0: [1814:0201] type 0 class 0x000280
[    0.184173] pci 0000:06:01.0: reg 10: [mem 0xb8400000-0xb8401fff]
[    0.184334] pci 0000:00:1e.0: PCI bridge to [bus 06-06] (subtractive decode)
[    0.184345] pci 0000:00:1e.0:   bridge window [mem 0xb8400000-0xb84fffff]
[    0.184356] pci 0000:00:1e.0:   bridge window [mem 0xd0400000-0xd04fffff 64bit pref]
[    0.184362] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.184368] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xfffffffff] (subtractive decode)
[    0.184405] pci_bus 0000:00: on NUMA node 0
[    0.184414] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.184660] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    0.184751] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    0.185071] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[    0.185158] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
[    0.185245] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
[    0.185334] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
[    0.186305] ACPI Warning: For \_SB_.PCI0._OSC: Parameter count mismatch - ASL declared 5, ACPI requires 4 (20110623/nspredef-359)
[    0.186322] \_SB_.PCI0:_OSC evaluation returned wrong type
[    0.186326] _OSC request data:1 1f 1f 
[    0.186337]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.187209] ACPI Warning: For \_SB_.PCI0._OSC: Parameter count mismatch - ASL declared 5, ACPI requires 4 (20110623/nspredef-359)
[    0.187224] \_SB_.PCI0:_OSC evaluation returned wrong type
[    0.187228] _OSC request data:1 0 1d 
[    0.187239]  pci0000:00: ACPI _OSC request failed (AE_TYPE), returned control mask: 0x1d
[    0.187243] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.195253] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.195391] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[    0.195524] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.195660] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.195793] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.195928] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.196091] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.196235] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.196548] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.196559] vgaarb: loaded
[    0.196563] vgaarb: bridge control possible 0000:01:00.0
[    0.196846] i2c-core: driver [aat2870] using legacy suspend method
[    0.196850] i2c-core: driver [aat2870] using legacy resume method
[    0.197011] SCSI subsystem initialized
[    0.197111] libata version 3.00 loaded.
[    0.197229] usbcore: registered new interface driver usbfs
[    0.197261] usbcore: registered new interface driver hub
[    0.197322] usbcore: registered new device driver usb
[    0.197522] PCI: Using ACPI for IRQ routing
[    0.205655] PCI: pci_cache_line_size set to 64 bytes
[    0.205801] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.205807] reserve RAM buffer: 000000003ff2fc00 - 000000003fffffff 
[    0.206044] NetLabel: Initializing
[    0.206049] NetLabel:  domain hash size = 128
[    0.206053] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.206075] NetLabel:  unlabeled traffic allowed by default
[    0.206277] hpet clockevent registered
[    0.206284] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.206292] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.206303] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.212182] Switching to clocksource hpet
[    0.230677] AppArmor: AppArmor Filesystem Enabled
[    0.230725] pnp: PnP ACPI init
[    0.230758] ACPI: bus type pnp registered
[    0.230935] pnp 00:00: [bus 00-ff]
[    0.230941] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.230947] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.230953] pnp 00:00: [io  0x0d00-0xffff window]
[    0.230958] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.230964] pnp 00:00: [mem 0x00000000 window]
[    0.230969] pnp 00:00: [mem 0x40000000-0xffffffff window]
[    0.231082] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.231179] pnp 00:01: [dma 4]
[    0.231185] pnp 00:01: [io  0x0000-0x000f]
[    0.231190] pnp 00:01: [io  0x0081-0x0083]
[    0.231194] pnp 00:01: [io  0x0087]
[    0.231199] pnp 00:01: [io  0x0089-0x008b]
[    0.231203] pnp 00:01: [io  0x008f]
[    0.231208] pnp 00:01: [io  0x00c0-0x00df]
[    0.231277] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.231304] pnp 00:02: [io  0x0070-0x0071]
[    0.231321] pnp 00:02: [irq 8]
[    0.231389] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.231454] pnp 00:03: [io  0x0060]
[    0.231460] pnp 00:03: [io  0x0064]
[    0.231470] pnp 00:03: [irq 1]
[    0.231544] pnp 00:03: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.231833] pnp 00:04: [io  0x0061]
[    0.231908] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.231931] pnp 00:05: [io  0x00f0-0x00ff]
[    0.231942] pnp 00:05: [irq 13]
[    0.232048] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.232200] pnp 00:06: [io  0x03f0-0x03f1]
[    0.232206] pnp 00:06: [io  0x03f2-0x03f3]
[    0.232211] pnp 00:06: [io  0x03f4-0x03f5]
[    0.232216] pnp 00:06: [io  0x03f7]
[    0.232226] pnp 00:06: [irq 6]
[    0.232231] pnp 00:06: [dma 2]
[    0.232353] pnp 00:06: Plug and Play ACPI device, IDs PNP0700 (active)
[    0.232715] pnp 00:07: [io  0x03f8-0x03ff]
[    0.232727] pnp 00:07: [irq 4]
[    0.232884] pnp 00:07: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.233500] pnp 00:08: [io  0x0378-0x037f]
[    0.233506] pnp 00:08: [io  0x0778-0x077f]
[    0.233517] pnp 00:08: [irq 7]
[    0.233523] pnp 00:08: [dma 3]
[    0.233725] pnp 00:08: Plug and Play ACPI device, IDs PNP0401 (active)
[    0.233919] pnp 00:09: [io  0x0010-0x001f]
[    0.233925] pnp 00:09: [io  0x0022-0x003f]
[    0.233930] pnp 00:09: [io  0x0044-0x004d]
[    0.233935] pnp 00:09: [io  0x0050-0x005f]
[    0.233939] pnp 00:09: [io  0x0063]
[    0.233944] pnp 00:09: [io  0x0065]
[    0.233948] pnp 00:09: [io  0x0067-0x006f]
[    0.233953] pnp 00:09: [io  0x0072-0x007f]
[    0.233958] pnp 00:09: [io  0x0080]
[    0.233962] pnp 00:09: [io  0x0084-0x0086]
[    0.233967] pnp 00:09: [io  0x0088]
[    0.233971] pnp 00:09: [io  0x008c-0x008e]
[    0.233976] pnp 00:09: [io  0x0090-0x009f]
[    0.233981] pnp 00:09: [io  0x00a2-0x00bf]
[    0.233985] pnp 00:09: [io  0x00e0-0x00ef]
[    0.233990] pnp 00:09: [io  0x04d0-0x04d1]
[    0.233995] pnp 00:09: [io  0x0400-0x047f]
[    0.234000] pnp 00:09: [io  0x0500-0x053f]
[    0.234160] system 00:09: [io  0x04d0-0x04d1] has been reserved
[    0.234167] system 00:09: [io  0x0400-0x047f] has been reserved
[    0.234174] system 00:09: [io  0x0500-0x053f] has been reserved
[    0.234182] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.234334] pnp 00:0a: [mem 0xffb80000-0xffbfffff]
[    0.234340] pnp 00:0a: [mem 0xfff80000-0xffffffff]
[    0.234418] pnp 00:0a: Plug and Play ACPI device, IDs INT0800 (active)
[    0.234514] pnp 00:0b: [mem 0xffc00000-0xfff7ffff]
[    0.234647] system 00:0b: [mem 0xffc00000-0xfff7ffff] has been reserved
[    0.234656] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.235018] pnp 00:0c: [io  0x0400-0x047f]
[    0.235025] pnp 00:0c: [io  0x0000-0xffffffffffffffff disabled]
[    0.235030] pnp 00:0c: [io  0x0680-0x06ff]
[    0.235035] pnp 00:0c: [io  0x0500-0x053f]
[    0.235040] pnp 00:0c: [mem 0xeec00000-0xeec03fff]
[    0.235045] pnp 00:0c: [mem 0xfec00000-0xfec00fff]
[    0.235051] pnp 00:0c: [mem 0xfee00000-0xfee00fff]
[    0.235056] pnp 00:0c: [mem 0xe0000000-0xefffffff]
[    0.235061] pnp 00:0c: [mem 0xfed13000-0xfed13fff]
[    0.235066] pnp 00:0c: [mem 0xfed14000-0xfed17fff]
[    0.235071] pnp 00:0c: [mem 0xfed18000-0xfed18fff]
[    0.235077] pnp 00:0c: [mem 0xfed19000-0xfed19fff]
[    0.235083] pnp 00:0c: [mem 0xfed1c000-0xfed1ffff]
[    0.235089] pnp 00:0c: [mem 0xfed20000-0xfed9ffff]
[    0.235244] system 00:0c: [io  0x0400-0x047f] has been reserved
[    0.235251] system 00:0c: [io  0x0680-0x06ff] has been reserved
[    0.235259] system 00:0c: [io  0x0500-0x053f] has been reserved
[    0.235266] system 00:0c: [mem 0xeec00000-0xeec03fff] has been reserved
[    0.235273] system 00:0c: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.235280] system 00:0c: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.235287] system 00:0c: [mem 0xe0000000-0xefffffff] could not be reserved
[    0.235294] system 00:0c: [mem 0xfed13000-0xfed13fff] has been reserved
[    0.235300] system 00:0c: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.235307] system 00:0c: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.235314] system 00:0c: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.235321] system 00:0c: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.235327] system 00:0c: [mem 0xfed20000-0xfed9ffff] has been reserved
[    0.235335] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.235821] pnp 00:0d: [mem 0x00000000-0x0009ffff]
[    0.235827] pnp 00:0d: [mem 0x000c0000-0x000dffff]
[    0.235832] pnp 00:0d: [mem 0x000e0000-0x000fffff]
[    0.235837] pnp 00:0d: [mem 0x00100000-0x3fffffff]
[    0.235843] pnp 00:0d: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.235985] system 00:0d: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.235993] system 00:0d: [mem 0x000c0000-0x000dffff] could not be reserved
[    0.236025] system 00:0d: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.236032] system 00:0d: [mem 0x00100000-0x3fffffff] could not be reserved
[    0.236041] system 00:0d: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.236428] pnp: PnP ACPI: found 14 devices
[    0.236432] ACPI: ACPI bus type pnp unregistered
[    0.236440] PnPBIOS: Disabled by ACPI PNP
[    0.275449] PCI: max bus depth: 1 pci_try_num: 2
[    0.275518] pci 0000:00:1c.3: BAR 13: assigned [io  0x1000-0x1fff]
[    0.275527] pci 0000:00:1c.2: BAR 13: assigned [io  0x2000-0x2fff]
[    0.275536] pci 0000:00:1c.0: BAR 13: assigned [io  0x3000-0x3fff]
[    0.275543] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.275550] pci 0000:00:01.0:   bridge window [io  0xa000-0xafff]
[    0.275559] pci 0000:00:01.0:   bridge window [mem 0xa8000000-0xb7ffffff]
[    0.275566] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff pref]
[    0.275575] pci 0000:00:1c.0: PCI bridge to [bus 05-05]
[    0.275582] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.275591] pci 0000:00:1c.0:   bridge window [mem 0xb8300000-0xb83fffff]
[    0.275599] pci 0000:00:1c.0:   bridge window [mem 0xd0300000-0xd03fffff 64bit pref]
[    0.275610] pci 0000:00:1c.1: PCI bridge to [bus 04-04]
[    0.275617] pci 0000:00:1c.1:   bridge window [io  0xb000-0xbfff]
[    0.275626] pci 0000:00:1c.1:   bridge window [mem 0xb8200000-0xb82fffff]
[    0.275634] pci 0000:00:1c.1:   bridge window [mem 0xd0200000-0xd02fffff 64bit pref]
[    0.275646] pci 0000:00:1c.2: PCI bridge to [bus 03-03]
[    0.275653] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff]
[    0.275663] pci 0000:00:1c.2:   bridge window [mem 0xb8100000-0xb81fffff]
[    0.275671] pci 0000:00:1c.2:   bridge window [mem 0xd0100000-0xd01fffff 64bit pref]
[    0.275682] pci 0000:00:1c.3: PCI bridge to [bus 02-02]
[    0.275689] pci 0000:00:1c.3:   bridge window [io  0x1000-0x1fff]
[    0.275699] pci 0000:00:1c.3:   bridge window [mem 0xb8000000-0xb80fffff]
[    0.275707] pci 0000:00:1c.3:   bridge window [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.275719] pci 0000:00:1e.0: PCI bridge to [bus 06-06]
[    0.275728] pci 0000:00:1e.0:   bridge window [mem 0xb8400000-0xb84fffff]
[    0.275736] pci 0000:00:1e.0:   bridge window [mem 0xd0400000-0xd04fffff 64bit pref]
[    0.275773] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.275781] pci 0000:00:01.0: setting latency timer to 64
[    0.275793] pci 0000:00:1c.0: enabling device (0106 -> 0107)
[    0.275808] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.275816] pci 0000:00:1c.0: setting latency timer to 64
[    0.275829] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.275836] pci 0000:00:1c.1: setting latency timer to 64
[    0.275847] pci 0000:00:1c.2: enabling device (0106 -> 0107)
[    0.275861] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.275869] pci 0000:00:1c.2: setting latency timer to 64
[    0.275880] pci 0000:00:1c.3: enabling device (0106 -> 0107)
[    0.275894] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.275902] pci 0000:00:1c.3: setting latency timer to 64
[    0.275914] pci 0000:00:1e.0: setting latency timer to 64
[    0.275921] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.275927] pci_bus 0000:00: resource 1 [mem 0x00000000-0xfffffffff]
[    0.275933] pci_bus 0000:01: resource 0 [io  0xa000-0xafff]
[    0.275938] pci_bus 0000:01: resource 1 [mem 0xa8000000-0xb7ffffff]
[    0.275943] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff pref]
[    0.275948] pci_bus 0000:05: resource 0 [io  0x3000-0x3fff]
[    0.275953] pci_bus 0000:05: resource 1 [mem 0xb8300000-0xb83fffff]
[    0.275959] pci_bus 0000:05: resource 2 [mem 0xd0300000-0xd03fffff 64bit pref]
[    0.275965] pci_bus 0000:04: resource 0 [io  0xb000-0xbfff]
[    0.275970] pci_bus 0000:04: resource 1 [mem 0xb8200000-0xb82fffff]
[    0.275975] pci_bus 0000:04: resource 2 [mem 0xd0200000-0xd02fffff 64bit pref]
[    0.275981] pci_bus 0000:03: resource 0 [io  0x2000-0x2fff]
[    0.275986] pci_bus 0000:03: resource 1 [mem 0xb8100000-0xb81fffff]
[    0.275991] pci_bus 0000:03: resource 2 [mem 0xd0100000-0xd01fffff 64bit pref]
[    0.275997] pci_bus 0000:02: resource 0 [io  0x1000-0x1fff]
[    0.276023] pci_bus 0000:02: resource 1 [mem 0xb8000000-0xb80fffff]
[    0.276029] pci_bus 0000:02: resource 2 [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.276035] pci_bus 0000:06: resource 1 [mem 0xb8400000-0xb84fffff]
[    0.276040] pci_bus 0000:06: resource 2 [mem 0xd0400000-0xd04fffff 64bit pref]
[    0.276046] pci_bus 0000:06: resource 4 [io  0x0000-0xffff]
[    0.276051] pci_bus 0000:06: resource 5 [mem 0x00000000-0xfffffffff]
[    0.276120] NET: Registered protocol family 2
[    0.276257] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.276705] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.277345] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.277680] TCP: Hash tables configured (established 131072 bind 65536)
[    0.277686] TCP reno registered
[    0.277693] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.277706] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.277856] NET: Registered protocol family 1
[    0.277936] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.277961] pci 0000:00:1d.0: PCI INT A disabled
[    0.277978] pci 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.278000] pci 0000:00:1d.1: PCI INT B disabled
[    0.278019] pci 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.278041] pci 0000:00:1d.2: PCI INT C disabled
[    0.278057] pci 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.278079] pci 0000:00:1d.3: PCI INT D disabled
[    0.278095] pci 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.598881] Freeing initrd memory: 13832k freed
[    1.876033] pci 0000:00:1d.7: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[    1.876159] pci 0000:00:1d.7: PCI INT A disabled
[    1.876188] pci 0000:01:00.0: Boot video device
[    1.876202] PCI: CLS 64 bytes, default 64
[    1.876722] audit: initializing netlink socket (disabled)
[    1.876738] type=2000 audit(1358201617.872:1): initialized
[    1.903741] highmem bounce pool size: 64 pages
[    1.903749] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.906881] VFS: Disk quotas dquot_6.5.2
[    1.906974] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.907873] fuse init (API version 7.17)
[    1.908058] msgmni has been set to 1736
[    1.908667] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.908712] io scheduler noop registered
[    1.908718] io scheduler deadline registered
[    1.908732] io scheduler cfq registered (default)
[    1.908910] pcieport 0000:00:01.0: setting latency timer to 64
[    1.908958] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    1.909036] pcieport 0000:00:1c.0: setting latency timer to 64
[    1.909083] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    1.909171] pcieport 0000:00:1c.1: setting latency timer to 64
[    1.909219] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    1.909300] pcieport 0000:00:1c.2: setting latency timer to 64
[    1.909348] pcieport 0000:00:1c.2: irq 43 for MSI/MSI-X
[    1.909429] pcieport 0000:00:1c.3: setting latency timer to 64
[    1.909477] pcieport 0000:00:1c.3: irq 44 for MSI/MSI-X
[    1.909605] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.909646] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.909885] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.909895] ACPI: Power Button [PWRB]
[    1.909976] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.909982] ACPI: Power Button [PWRF]
[    1.912140] ERST: Table is not found!
[    1.912144] GHES: HEST is not enabled!
[    1.912193] isapnp: Scanning for PnP cards...
[    1.912296] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.932729] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.265326] isapnp: No Plug & Play device found
[    2.312734] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.324356] Linux agpgart interface v0.103
[    2.327178] brd: module loaded
[    2.328537] loop: module loaded
[    2.328807] ata_piix 0000:00:1f.1: version 2.13
[    2.328828] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.328882] ata_piix 0000:00:1f.1: setting latency timer to 64
[    2.329410] scsi0 : ata_piix
[    2.329551] scsi1 : ata_piix
[    2.331165] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    2.331170] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    2.331210] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.331220] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    2.331285] ata_piix 0000:00:1f.2: setting latency timer to 64
[    2.331848] scsi2 : ata_piix
[    2.331979] scsi3 : ata_piix
[    2.333149] ata3: SATA max UDMA/133 cmd 0xec00 ctl 0xe800 bmdma 0xdc00 irq 19
[    2.333154] ata4: SATA max UDMA/133 cmd 0xe400 ctl 0xe000 bmdma 0xdc08 irq 19
[    2.333883] Fixed MDIO Bus: probed
[    2.333921] tun: Universal TUN/TAP device driver, 1.6
[    2.333924] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    2.334029] PPP generic driver version 2.4.2
[    2.334226] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.334254] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.334281] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.334286] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.334379] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    2.334414] ehci_hcd 0000:00:1d.7: debug port 1
[    2.338312] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    2.338335] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xb8504000
[    2.352041] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.352278] hub 1-0:1.0: USB hub found
[    2.352286] hub 1-0:1.0: 8 ports detected
[    2.352414] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.352438] uhci_hcd: USB Universal Host Controller Interface driver
[    2.352467] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.352477] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.352482] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.352559] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.352589] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000cc00
[    2.352804] hub 2-0:1.0: USB hub found
[    2.352811] hub 2-0:1.0: 2 ports detected
[    2.352914] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.352924] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.352928] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.353004] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    2.353031] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d000
[    2.353249] hub 3-0:1.0: USB hub found
[    2.353256] hub 3-0:1.0: 2 ports detected
[    2.353360] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.353369] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.353374] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.353457] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    2.353498] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d400
[    2.353707] hub 4-0:1.0: USB hub found
[    2.353714] hub 4-0:1.0: 2 ports detected
[    2.353818] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    2.353828] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    2.353832] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    2.353910] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    2.353949] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d800
[    2.354161] hub 5-0:1.0: USB hub found
[    2.354168] hub 5-0:1.0: 2 ports detected
[    2.354348] usbcore: registered new interface driver libusual
[    2.354423] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    2.354427] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    2.355211] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.355411] mousedev: PS/2 mouse device common for all mice
[    2.355668] rtc_cmos 00:02: RTC can wake from S4
[    2.355815] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    2.355845] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    2.355939] device-mapper: uevent: version 1.0.3
[    2.356093] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [email]dm-devel@redhat.com[/email]
[    2.356149] EISA: Probing bus 0 at eisa.0
[    2.356157] Cannot allocate resource for EISA slot 1
[    2.356160] Cannot allocate resource for EISA slot 2
[    2.356163] Cannot allocate resource for EISA slot 3
[    2.356182] EISA: Detected 0 cards.
[    2.356195] cpufreq-nforce2: No nForce2 chipset.
[    2.356199] cpuidle: using governor ladder
[    2.356202] cpuidle: using governor menu
[    2.356205] EFI Variables Facility v0.08 2004-May-17
[    2.356602] TCP cubic registered
[    2.356795] NET: Registered protocol family 10
[    2.357683] NET: Registered protocol family 17
[    2.357690] Registering the dns_resolver key type
[    2.357716] Using IPI No-Shortcut mode
[    2.357910] PM: Hibernation image not present or could not be loaded.
[    2.357931] registered taskstats version 1
[    2.368369]   Magic number: 13:522:249
[    2.368470] rtc_cmos 00:02: setting system clock to 2013-01-14 22:13:39 UTC (1358201619)
[    2.368498] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.368501] EDD information not available.
[    2.512571] ata3.00: ATA-7: Maxtor 6Y080M0, YAR511W0, max UDMA/133
[    2.512576] ata3.00: 160086528 sectors, multi 16: LBA 
[    2.513942] ata1.00: ATA-7: Maxtor 6B080P0, BAH41E00, max UDMA/133
[    2.513946] ata1.00: 160086528 sectors, multi 16: LBA 
[    2.513954] ata1.01: ATAPI: TSSTcorpCD/DVDW TS-H552B, TS04, max UDMA/33
[    2.528458] ata3.00: configured for UDMA/133
[    2.529803] ata1.00: configured for UDMA/100
[    2.544206] ata1.01: configured for UDMA/33
[    2.545084] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6B080P0   BAH4 PQ: 0 ANSI: 5
[    2.545313] sd 0:0:0:0: [sda] 160086528 512-byte logical blocks: (81.9 GB/76.3 GiB)
[    2.545396] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.545440] sd 0:0:0:0: [sda] Write Protect is off
[    2.545448] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.545503] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.546172] scsi 0:0:1:0: CD-ROM            TSSTcorp CD/DVDW TS-H552B TS04 PQ: 0 ANSI: 5
[    2.571545] sr0: scsi3-mmc drive: 1x/48x writer cd/rw xa/form2 cdda tray
[    2.571550] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.571742] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    2.571859] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    2.572097] scsi 2:0:0:0: Direct-Access     ATA      Maxtor 6Y080M0   YAR5 PQ: 0 ANSI: 5
[    2.572304] sd 2:0:0:0: [sdb] 160086528 512-byte logical blocks: (81.9 GB/76.3 GiB)
[    2.572376] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    2.572431] sd 2:0:0:0: [sdb] Write Protect is off
[    2.572438] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.572494] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.594354]  sda: sda1 sda2 < sda5 >
[    2.594995] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.607445]  sdb: sdb1 sdb2 < sdb5 >
[    2.607992] sd 2:0:0:0: [sdb] Attached SCSI disk
[    2.608136] Freeing unused kernel memory: 744k freed
[    2.608607] Write protecting the kernel text: 5828k
[    2.608637] Write protecting the kernel read-only data: 2380k
[    2.608640] NX-protecting the kernel data: 4412k
[    2.637376] udevd[93]: starting version 175
[    2.720062] usb 1-6: new high-speed USB device number 3 using ehci_hcd
[    2.760801] sky2: driver version 1.30
[    2.760862] sky2 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.760885] sky2 0000:04:00.0: setting latency timer to 64
[    2.760931] sky2 0000:04:00.0: Yukon-2 EC chip revision 1
[    2.761045] sky2 0000:04:00.0: irq 45 for MSI/MSI-X
[    2.765275] sky2 0000:04:00.0: eth0: addr 00:11:11:75:88:08
[    2.795991] Floppy drive(s): fd0 is 1.44M
[    2.815705] FDC 0 is a post-1991 82077
[    2.870477] Initializing USB Mass Storage driver...
[    2.876095] Refined TSC clocksource calibration: 2999.980 MHz.
[    2.876105] Switching to clocksource tsc
[    2.876153] scsi4 : usb-storage 1-6:1.0
[    2.876339] usbcore: registered new interface driver usb-storage
[    2.876345] USB Mass Storage support registered.
[    2.968061] usb 1-7: new high-speed USB device number 4 using ehci_hcd
[    3.091822] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[    3.396035] usb 3-2: new low-speed USB device number 2 using uhci_hcd
[    3.816179] usb 5-2: new low-speed USB device number 2 using uhci_hcd
[    3.877046] scsi 4:0:0:0: Direct-Access     Generic  USB Storage-CFC  I20A PQ: 0 ANSI: 0 CCS
[    3.877663] scsi 4:0:0:1: Direct-Access     Generic  USB Storage-SDC  I20A PQ: 0 ANSI: 0 CCS
[    3.878281] scsi 4:0:0:2: Direct-Access     Generic  USB Storage-SMC  I20A PQ: 0 ANSI: 0 CCS
[    3.878910] scsi 4:0:0:3: Direct-Access     Generic  USB Storage-MSC  I20A PQ: 0 ANSI: 0 CCS
[    3.879732] sd 4:0:0:0: Attached scsi generic sg3 type 0
[    3.880027] sd 4:0:0:1: Attached scsi generic sg4 type 0
[    3.880306] sd 4:0:0:2: Attached scsi generic sg5 type 0
[    3.880676] sd 4:0:0:3: Attached scsi generic sg6 type 0
[    3.885898] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[    3.887397] sd 4:0:0:1: [sdd] Attached SCSI removable disk
[    3.888146] sd 4:0:0:2: [sde] Attached SCSI removable disk
[    3.888898] sd 4:0:0:3: [sdf] Attached SCSI removable disk
[   18.658754] Adding 1012732k swap on /dev/sdb5.  Priority:-1 extents:1 across:1012732k 
[   18.672516] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.722599] udevd[335]: starting version 175
[   18.729553] EXT4-fs (sdb1): re-mounted. Opts: errors=remount-ro
[   18.798237] lp: driver loaded but no devices found
[   18.919545] [drm] Initialized drm 1.1.0 20060810
[   19.118402] type=1400 audit(1358198036.245:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=510 comm="apparmor_parser"
[   19.119347] type=1400 audit(1358198036.245:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=510 comm="apparmor_parser"
[   19.119884] type=1400 audit(1358198036.245:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=510 comm="apparmor_parser"
[   19.214039] ppdev: user-space parallel port driver
[   19.242603] Bluetooth: Core ver 2.16
[   19.242651] NET: Registered protocol family 31
[   19.242656] Bluetooth: HCI device and connection manager initialized
[   19.242661] Bluetooth: HCI socket layer initialized
[   19.242666] Bluetooth: L2CAP socket layer initialized
[   19.242678] Bluetooth: SCO socket layer initialized
[   19.243661] parport_pc 00:08: reported by Plug and Play ACPI
[   19.243734] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   19.249146] [drm] radeon defaulting to kernel modesetting.
[   19.249153] [drm] radeon kernel modesetting enabled.
[   19.249257] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.249268] radeon 0000:01:00.0: setting latency timer to 64
[   19.249806] [drm] initializing kernel modesetting (RV380 0x1002:0x3E50 0x174B:0x0450).
[   19.249856] [drm] register mmio base: 0xA8000000
[   19.249861] [drm] register mmio size: 65536
[   19.252158] [drm] Generation 2 PCI interface, using max accessible memory
[   19.252170] radeon 0000:01:00.0: VRAM: 256M 0x00000000C0000000 - 0x00000000CFFFFFFF (256M used)
[   19.252178] radeon 0000:01:00.0: GTT: 512M 0x00000000A0000000 - 0x00000000BFFFFFFF
[   19.255558] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.255565] Bluetooth: BNEP filters: protocol multicast
[   19.256653] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   19.256660] [drm] Driver supports precise vblank timestamp query.
[   19.256724] radeon 0000:01:00.0: irq 46 for MSI/MSI-X
[   19.256735] radeon 0000:01:00.0: radeon: using MSI.
[   19.256772] [drm] radeon: irq initialized.
[   19.257534] [drm] Detected VRAM RAM=256M, BAR=256M
[   19.257541] [drm] RAM width 128bits DDR
[   19.264546] [TTM] Zone  kernel: Available graphics memory: 445040 kiB.
[   19.264553] [TTM] Zone highmem: Available graphics memory: 512210 kiB.
[   19.264558] [TTM] Initializing pool allocator.
[   19.264599] [drm] radeon: 256M of VRAM memory ready
[   19.264604] [drm] radeon: 512M of GTT memory ready.
[   19.264650] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   19.265945] [drm] radeon: 1 quad pipes, 1 Z pipes initialized.
[   19.270084] [drm] PCIE GART of 512M enabled (table at 0x00000000C0040000).
[   19.303326] radeon 0000:01:00.0: WB enabled
[   19.303523] [drm] Loading R300 Microcode
[   19.338879] intel_rng: FWH not detected
[   19.340749] lp0: using parport0 (interrupt-driven).
[   19.347642] cfg80211: Calling CRDA to update world regulatory domain
[   19.366096] type=1400 audit(1358198036.493:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=588 comm="apparmor_parser"
[   19.371606] type=1400 audit(1358198036.497:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=588 comm="apparmor_parser"
[   19.475718] input: Microsoft Microsoft Wireless Optical Mouse\xffffffc2\xffffffae\xffffffae 1.00 as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input2
[   19.476752] generic-usb 0003:045E:00E1.0001: input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse\xffffffc2\xffffffae\xffffffae 1.00] on usb-0000:00:1d.1-2/input0
[   19.492794] input: Device USB Device as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/input/input3
[   19.493239] generic-usb 0003:05FE:2001.0002: input,hidraw1: USB HID v1.00 Keyboard [Device USB Device] on usb-0000:00:1d.3-2/input0
[   19.526374] input: Device USB Device as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.1/input/input4
[   19.527187] generic-usb 0003:05FE:2001.0003: input,hidraw2: USB HID v1.00 Mouse [Device USB Device] on usb-0000:00:1d.3-2/input1
[   19.527293] usbcore: registered new interface driver usbhid
[   19.527299] usbhid: USB HID core driver
[   19.565351] rt2500pci 0000:06:01.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   19.581162] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   19.581170] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   19.581176] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   19.581182] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   19.581187] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   19.581193] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   19.581198] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   19.581204] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   19.581210] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   19.581216] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   19.581221] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   19.581228] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   19.581232] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   19.581238] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   19.581243] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   19.581250] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   19.581255] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   19.581261] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   19.581266] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   19.581272] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   19.581277] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   19.581283] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   19.581288] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   19.581294] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (600 mBi, 2000 mBm)
[   19.581299] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   19.581305] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (600 mBi, 2000 mBm)
[   19.581310] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   19.581317] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (600 mBi, 2000 mBm)
[   19.607710] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   19.612249] Registered led device: rt2500pci-phy0::radio
[   19.612362] Registered led device: rt2500pci-phy0::quality
[   19.776990] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.777080] snd_hda_intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[   19.777126] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   19.947796] init: failsafe main process (708) killed by TERM signal
[   20.172993] type=1400 audit(1358198037.301:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=839 comm="apparmor_parser"
[   20.204588] sky2 0000:04:00.0: eth0: enabling interface
[   20.205426] type=1400 audit(1358198037.333:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=841 comm="apparmor_parser"
[   20.208551] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.210584] type=1400 audit(1358198037.337:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=841 comm="apparmor_parser"
[   20.211139] type=1400 audit(1358198037.337:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=841 comm="apparmor_parser"
[   20.212369] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.241631] type=1400 audit(1358198037.369:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=844 comm="apparmor_parser"
[   20.256881] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.258149] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.295452] [drm] radeon: ring at 0x00000000A0001000
[   20.295474] [drm] ring test succeeded in 0 usecs
[   20.295770] [drm] radeon: ib pool ready.
[   20.295906] [drm] ib test succeeded in 0 usecs
[   20.297180] [drm] Radeon Display Connectors
[   20.297185] [drm] Connector 0:
[   20.297189] [drm]   VGA
[   20.297194] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   20.297198] [drm]   Encoders:
[   20.297201] [drm]     CRT1: INTERNAL_DAC1
[   20.297205] [drm] Connector 1:
[   20.297208] [drm]   DVI-I
[   20.297211] [drm]   HPD1
[   20.297216] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
[   20.297219] [drm]   Encoders:
[   20.297222] [drm]     CRT2: INTERNAL_DAC2
[   20.297226] [drm]     DFP1: INTERNAL_TMDS1
[   20.297230] [drm] Connector 2:
[   20.297234] [drm]   S-video
[   20.297236] [drm]   Encoders:
[   20.297240] [drm]     TV1: INTERNAL_DAC2
[   20.432958] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   20.432967] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.432972] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   20.432978] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.432982] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   20.432988] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.432993] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   20.432998] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.433003] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   20.433009] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.433014] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   20.433019] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.433024] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   20.433030] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.433034] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   20.433040] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.433045] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   20.433051] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.433055] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   20.433061] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.433066] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   20.433071] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.433076] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   20.433082] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.433087] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   20.433092] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.433097] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   20.433103] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.433109] cfg80211: World regulatory domain updated:
[   20.433113] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   20.433118] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.433123] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.433128] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.433134] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.433139] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.558415] [drm] fb mappable at 0xC00C0000
[   20.558424] [drm] vram apper at 0xC0000000
[   20.558428] [drm] size 3145728
[   20.558431] [drm] fb depth is 24
[   20.558435] [drm]    pitch is 4096
[   20.563637] fbcon: radeondrmfb (fb0) is primary device
[   20.564388] Console: switching to colour frame buffer device 128x48
[   20.564443] fb0: radeondrmfb frame buffer device
[   20.564448] drm: registered panic notifier
[   20.564466] [drm] Initialized radeon 2.12.0 20080528 for 0000:01:00.0 on minor 0
[   23.380458] wlan0: authenticate with 00:25:86:bb:46:32 (try 1)
[   23.381917] wlan0: authenticated
[   23.396459] wlan0: associate with 00:25:86:bb:46:32 (try 1)
[   23.398473] wlan0: RX AssocResp from 00:25:86:bb:46:32 (capab=0x431 status=0 aid=1)
[   23.398481] wlan0: associated
[   23.400484] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   34.960025] wlan0: no IPv6 routers present
[   62.611007] Linux video capture interface: v2.00
[   62.640574] usbcore: registered new interface driver em28xx
[   62.640579] em28xx driver loaded
[   62.641789] IR NEC protocol handler initialized
[   62.643765] em28xx_alsa: Unknown parameter `card'
[   62.664918] IR RC5(x) protocol handler initialized
[   62.667659] IR RC6 protocol handler initialized
[   62.670579] IR JVC protocol handler initialized
[   62.675015] IR Sony protocol handler initialized
[   62.686271] IR MCE Keyboard/mouse protocol handler initialized
[   62.699187] lirc_dev: IR Remote Control driver registered, major 250 
[   62.701008] IR LIRC bridge handler initialized



lsmod output:
> 
Module                  Size  Used by
ir_lirc_codec          12739  0 
lirc_dev               18700  1 ir_lirc_codec
ir_mce_kbd_decoder     12681  0 
ir_sony_decoder        12462  0 
ir_jvc_decoder         12459  0 
ir_rc6_decoder         12459  0 
ir_rc5_decoder         12459  0 
ir_nec_decoder         12459  0 
em28xx                 94221  0 
v4l2_common            15793  1 em28xx
videodev               86588  2 em28xx,v4l2_common
videobuf_vmalloc       13336  1 em28xx
videobuf_core          25409  2 em28xx,videobuf_vmalloc
rc_core                21263  8 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,em28xx
tveeprom               17009  1 em28xx
snd_hda_codec_realtek   174313  1 
snd_hda_intel          32765  5 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  3 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
arc4                   12473  2 
snd_seq_midi_event     14475  1 snd_seq_midi
rt2500pci              22948  0 
rt2x00pci              14202  1 rt2500pci
rt2x00lib              48875  2 rt2500pci,rt2x00pci
mac80211              436493  2 rt2x00pci,rt2x00lib
serio_raw              13027  0 
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
usbhid                 41937  0 
hid                    77428  1 usbhid
snd_timer              28931  2 snd_pcm,snd_seq
cfg80211              178877  2 rt2x00lib,mac80211
eeprom_93cx6           12687  1 rt2500pci
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
bnep                   17830  2 
parport_pc             32114  1 
radeon                737926  2 
bluetooth             158479  7 bnep
snd                    62218  18 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ppdev                  12849  0 
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
mac_hid                13077  0 
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
drm                   197641  4 radeon,ttm,drm_kms_helper
i2c_algo_bit           13199  1 radeon
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usb_storage            39646  0 
floppy                 60184  0 
sky2                   53628  0 


---

### Post by mercury1981 on 2013-01-18
Nobody an idea what the problem is why i have no /dev/video ?

---

### Post by mercury1981 on 2013-03-03
> **mercury1981 said:**
> Nobody an idea what the problem is why i have no /dev/video ?

Push!

---

