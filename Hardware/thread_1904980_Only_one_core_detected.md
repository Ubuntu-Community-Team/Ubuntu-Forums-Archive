---
title: "Only one core detected"
date: 2012-01-05
forum: Hardware
---

### Post by daniel_victoria on 2012-01-05
I have an old laptop with Intel Core Duo and looking at /proc/cpuinfo it only lists one processor (attached)! 

I tried using the acpi=off boot parameter, as explained on some other threads, but that did not help. One thing to note is that my laptop will only boot if I use the nolapic boot option.

I'm using Lubuntu 11.10.
Any hints as to what is going on?
Thanks

---

### Post by jerrrys on 2012-01-07
I take this to mean that acpi options were changed in ubuntu.  You may also have acpi options in BIOS.

---

### Post by daniel_victoria on 2012-01-09
Unfortunatelly, my laptop BIOS does not give me the option to change ACPI settings. So I tried booting with or without the boot parameter acpi=off and no changes. Still only one core detected. 
I'm attaching the output of dmesg. Initially, both cores are detected but then, I get a SMP dissabled message.
I have no Idea what to do.

Thanks for the attention
Daniel

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-14-generic (buildd@palmer) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 (Ubuntu 3.0.0-14.23-generic 3.0.9)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000b7d90000 (usable)
[    0.000000]  BIOS-e820: 00000000b7d90000 - 00000000b7d9c000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000b7d9c000 - 00000000b7d9d000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b7d9d000 - 00000000b8000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI present.
[    0.000000] DMI: Phoenix/SiS M720S/M720S, BIOS 6.00 07/17/0792
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0xb7d90 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FE0000000 write-back
[    0.000000]   2 base 0A0000000 mask FF0000000 write-back
[    0.000000]   3 base 0B0000000 mask FF8000000 write-back
[    0.000000]   4 base 0B7E00000 mask FFFE00000 uncachable
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT not supported by CPU.
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 512MB, type WB
[    0.000000] reg 2, base: 2560MB, range: 256MB, type WB
[    0.000000] reg 3, base: 2816MB, range: 128MB, type WB
[    0.000000] reg 4, base: 2942MB, range: 2MB, type UC
[    0.000000] total RAM covered: 2942M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 256M 	num_reg: 4  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 2942MB, range: 2MB, type UC
[    0.000000] reg 3, base: 2944MB, range: 128MB, type UC
[    0.000000] found SMP MP-table at [c00f8190] f8190
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] Base memory trampoline at [c0099000] 99000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 365ee000 - 372ef000
[    0.000000] 2053MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x000b7d90
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x000b7d90
[    0.000000] On node 0 totalpages: 752925
[    0.000000] free_area_init_node: node 0, pgdat c17b3400, node_mem_map f4eee200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3949 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4108 pages used for memmap
[    0.000000]   HighMem zone: 521606 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] SFI: Simple Firmware Interface v0.81 [http://simplefirmware.org](http://simplefirmware.org)
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000]     Virtual Wire compatibility mode.
[    0.000000] MPTABLE: OEM ID: SiS     
[    0.000000] MPTABLE: Product ID: 671MX       
[    0.000000] MPTABLE: APIC at: 0xFEE00000
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] Processor #1
[    0.000000] IOAPIC[0]: apic_id 2, version 20, address 0xfec00000, GSI 0-23
[    0.000000] Processors: 2
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at b8000000 (gap: b8000000:28000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 12 pages/cpu @f4800000 s26240 r0 d22912 u2097152
[    0.000000] pcpu-alloc: s26240 r0 d22912 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 747041
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-14-generic root=UUID=bdaf0301-4a8b-4410-b24c-aa121eba035e ro quiet splash vt.handoff=7 nolapic acpi=off
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 12048384 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:000b7d90)
[    0.000000] Memory: 2952548k/3012160k available (5335k kernel code, 59152k reserved, 2592k data, 696k init, 2102856k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc17bf000 - 0xc186d000   ( 696 kB)
[    0.000000]       .data : 0xc1535d84 - 0xc17be080   (2592 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1535d84   (5335 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f3808000 soft=f380a000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1732.815 MHz processor.
[    0.004016] Calibrating delay loop (skipped), value calculated using timer frequency.. 3465.63 BogoMIPS (lpj=6931260)
[    0.004031] pid_max: default: 32768 minimum: 301
[    0.004112] Security Framework initialized
[    0.004211] AppArmor: AppArmor initialized
[    0.004216] Yama: becoming mindful.
[    0.004426] Mount-cache hash table entries: 512
[    0.004999] Initializing cgroup subsys cpuacct
[    0.005020] Initializing cgroup subsys memory
[    0.005047] Initializing cgroup subsys devices
[    0.005055] Initializing cgroup subsys freezer
[    0.005061] Initializing cgroup subsys net_cls
[    0.005067] Initializing cgroup subsys blkio
[    0.005095] Initializing cgroup subsys perf_event
[    0.008055] Disabled fast string operations
[    0.008073] CPU: Physical Processor ID: 0
[    0.008078] CPU: Processor Core ID: 0
[    0.008090] mce: CPU supports 6 MCE banks
[    0.008130] using mwait in idle threads.
[    0.014555] ftrace: allocating 24878 entries in 49 pages
[    0.016295] SMP disabled
[    0.016316] Performance Events: Core events, 
[    0.016330] no APIC, boot with the "lapic" boot parameter to force-enable it.
[    0.016335] no hardware sampling interrupt available.
[    0.016346] core PMU driver.
[    0.016362] ... version:                1
[    0.016366] ... bit width:              40
[    0.016371] ... generic registers:      2
[    0.016376] ... value mask:             000000ffffffffff
[    0.016382] ... max period:             000000007fffffff
[    0.016387] ... fixed-purpose events:   0
[    0.016392] ... event mask:             0000000000000003
[    0.020168] Brought up 1 CPUs
[    0.020175] Total of 1 processors activated (3465.63 BogoMIPS).
[    0.020556] devtmpfs: initialized
[    0.021108] PM: Registering ACPI NVS region at b7d9c000 (4096 bytes)
[    0.027390] print_constraints: dummy: 
[    0.027437] Time:  0:03:11  Date: 01/10/12
[    0.027597] NET: Registered protocol family 16
[    0.028039] EISA bus registered
[    0.043734] PCI: PCI BIOS revision 3.00 entry at 0xfde54, last bus=4
[    0.043750] PCI: Using configuration type 1 for base access
[    0.047109] bio: create slab <bio-0> at 0
[    0.047427] ACPI: Interpreter disabled.
[    0.047622] vgaarb: loaded
[    0.048366] SCSI subsystem initialized
[    0.048500] libata version 3.00 loaded.
[    0.048630] usbcore: registered new interface driver usbfs
[    0.048663] usbcore: registered new interface driver hub
[    0.048750] usbcore: registered new device driver usb
[    0.049021] PCI: Probing PCI hardware
[    0.049030] PCI: Probing PCI hardware (bus 00)
[    0.049141] pci 0000:00:00.0: [1039:0671] type 0 class 0x000600
[    0.049169] pci 0000:00:00.0: reg 10: [mem 0xd0000000-0xd3ffffff]
[    0.049278] pci 0000:00:01.0: [1039:0003] type 1 class 0x000604
[    0.049350] pci 0000:00:02.0: [1039:0968] type 0 class 0x000601
[    0.049489] pci 0000:00:02.5: [1039:5513] type 0 class 0x000101
[    0.049521] pci 0000:00:02.5: reg 10: [io  0x01f0-0x01f7]
[    0.049540] pci 0000:00:02.5: reg 14: [io  0x03f4-0x03f7]
[    0.049561] pci 0000:00:02.5: reg 18: [io  0x0170-0x0177]
[    0.049580] pci 0000:00:02.5: reg 1c: [io  0x0374-0x0377]
[    0.049600] pci 0000:00:02.5: reg 20: [io  0x1000-0x100f]
[    0.049663] pci 0000:00:02.5: PME# supported from D3cold
[    0.049675] pci 0000:00:02.5: PME# disabled
[    0.049707] pci 0000:00:03.0: [1039:7001] type 0 class 0x000c03
[    0.049733] pci 0000:00:03.0: reg 10: [mem 0xd4104000-0xd4104fff]
[    0.049839] pci 0000:00:03.1: [1039:7001] type 0 class 0x000c03
[    0.049865] pci 0000:00:03.1: reg 10: [mem 0xd4105000-0xd4105fff]
[    0.049978] pci 0000:00:03.3: [1039:7002] type 0 class 0x000c03
[    0.050008] pci 0000:00:03.3: reg 10: [mem 0xd4106000-0xd4106fff]
[    0.050115] pci 0000:00:03.3: PME# supported from D0 D3hot D3cold
[    0.050125] pci 0000:00:03.3: PME# disabled
[    0.050166] pci 0000:00:04.0: [1039:0191] type 0 class 0x000200
[    0.050197] pci 0000:00:04.0: reg 10: [mem 0xd4307000-0xd430707f]
[    0.050217] pci 0000:00:04.0: reg 14: [io  0x1080-0x10ff]
[    0.050310] pci 0000:00:04.0: supports D1 D2
[    0.050317] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.050328] pci 0000:00:04.0: PME# disabled
[    0.050361] pci 0000:00:05.0: [1039:1183] type 0 class 0x000101
[    0.050393] pci 0000:00:05.0: reg 10: [io  0x1058-0x105f]
[    0.050412] pci 0000:00:05.0: reg 14: [io  0x104c-0x104f]
[    0.050431] pci 0000:00:05.0: reg 18: [io  0x1050-0x1057]
[    0.050450] pci 0000:00:05.0: reg 1c: [io  0x1048-0x104b]
[    0.050469] pci 0000:00:05.0: reg 20: [io  0x1020-0x102f]
[    0.050529] pci 0000:00:05.0: PME# supported from D3cold
[    0.050539] pci 0000:00:05.0: PME# disabled
[    0.050581] pci 0000:00:06.0: [1039:000a] type 1 class 0x000604
[    0.050693] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.050703] pci 0000:00:06.0: PME# disabled
[    0.050755] pci 0000:00:07.0: [1039:000a] type 1 class 0x000604
[    0.050867] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.050877] pci 0000:00:07.0: PME# disabled
[    0.050924] pci 0000:00:09.0: [1524:0730] type 0 class 0x000501
[    0.050956] pci 0000:00:09.0: reg 10: [mem 0x00007400-0x0000747f]
[    0.051066] pci 0000:00:09.0: supports D1 D2
[    0.051072] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot
[    0.051082] pci 0000:00:09.0: PME# disabled
[    0.051126] pci 0000:00:09.1: [1524:0750] type 0 class 0x000805
[    0.051159] pci 0000:00:09.1: reg 10: [mem 0x00000000-0x000000ff]
[    0.051272] pci 0000:00:09.1: supports D1 D2
[    0.051278] pci 0000:00:09.1: PME# supported from D0 D1 D2 D3hot
[    0.051288] pci 0000:00:09.1: PME# disabled
[    0.051325] pci 0000:00:09.3: [1524:0751] type 0 class 0x000501
[    0.051357] pci 0000:00:09.3: reg 10: [mem 0x00000000-0x000000ff]
[    0.051467] pci 0000:00:09.3: supports D1 D2
[    0.051473] pci 0000:00:09.3: PME# supported from D0 D1 D2 D3hot
[    0.051483] pci 0000:00:09.3: PME# disabled
[    0.051537] pci 0000:00:0f.0: [1039:7502] type 0 class 0x000403
[    0.051570] pci 0000:00:0f.0: reg 10: [mem 0xd4100000-0xd4103fff]
[    0.051678] pci 0000:00:0f.0: PME# supported from D0 D3hot D3cold
[    0.051688] pci 0000:00:0f.0: PME# disabled
[    0.051757] pci 0000:00:1f.0: [1039:0004] type 1 class 0x000604
[    0.051874] pci 0000:00:1f.0: PME# supported from D0 D3hot D3cold
[    0.051884] pci 0000:00:1f.0: PME# disabled
[    0.051952] pci 0000:01:00.0: [1039:6351] type 0 class 0x000300
[    0.051982] pci 0000:01:00.0: reg 10: [mem 0xc0000000-0xcfffffff pref]
[    0.052025] pci 0000:01:00.0: reg 14: [mem 0xd4000000-0xd401ffff]
[    0.052042] pci 0000:01:00.0: reg 18: [io  0x9000-0x907f]
[    0.052118] pci 0000:01:00.0: supports D1 D2
[    0.052196] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.052207] pci 0000:00:01.0:   bridge window [io  0x9000-0x9fff]
[    0.052219] pci 0000:00:01.0:   bridge window [mem 0xd4000000-0xd40fffff]
[    0.052231] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff pref]
[    0.052324] pci 0000:00:06.0: PCI bridge to [bus 02-02]
[    0.052339] pci 0000:00:06.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.052350] pci 0000:00:06.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.052365] pci 0000:00:06.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.052458] pci 0000:00:07.0: PCI bridge to [bus 03-03]
[    0.052472] pci 0000:00:07.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.052483] pci 0000:00:07.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.052498] pci 0000:00:07.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.052589] pci 0000:00:1f.0: PCI bridge to [bus 04-04]
[    0.052603] pci 0000:00:1f.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.052615] pci 0000:00:1f.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.052630] pci 0000:00:1f.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.054049] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.054602] PCI: pci_cache_line_size set to 64 bytes
[    0.054674] pci 0000:00:09.0: address space collision: [mem 0x00007400-0x0000747f] conflicts with reserved [mem 0x00000000-0x0000ffff]
[    0.054768] reserve RAM buffer: 000000000009dc00 - 000000000009ffff 
[    0.054776] reserve RAM buffer: 00000000b7d90000 - 00000000b7ffffff 
[    0.055141] NetLabel: Initializing
[    0.055147] NetLabel:  domain hash size = 128
[    0.055151] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.055188] NetLabel:  unlabeled traffic allowed by default
[    0.055373] Switching to clocksource pit
[    0.078981] AppArmor: AppArmor Filesystem Enabled
[    0.079118] pnp: PnP ACPI: disabled
[    0.079137] PnPBIOS: Scanning system for PnP BIOS support...
[    0.079288] PnPBIOS: Found PnP BIOS installation structure at 0xc00f81b0
[    0.079296] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xbec4, dseg 0x400
[    0.081593] PNPBIOS fault.. attempting recovery.
[    0.081607] PnPBIOS: Warning! Your PnP BIOS caused a fatal error. Attempting to continue
[    0.081613] PnPBIOS: You may need to reboot with the "pnpbios=off" option to operate stably
[    0.081619] PnPBIOS: Check with your vendor for an updated BIOS
[    0.081626] PnPBIOS: get_dev_node: unexpected status 0x3a
[    0.081633] PnPBIOS: 0 nodes reported by PnP BIOS; 0 recorded by driver
[    0.086859] PCI: max bus depth: 1 pci_try_num: 2
[    0.086983] pci 0000:00:09.1: BAR 0: assigned [mem 0xb8000000-0xb80000ff]
[    0.086998] pci 0000:00:09.1: BAR 0: set to [mem 0xb8000000-0xb80000ff] (PCI address [0xb8000000-0xb80000ff])
[    0.087011] pci 0000:00:09.3: BAR 0: assigned [mem 0xb8000100-0xb80001ff]
[    0.087024] pci 0000:00:09.3: BAR 0: set to [mem 0xb8000100-0xb80001ff] (PCI address [0xb8000100-0xb80001ff])
[    0.087037] pci 0000:00:09.0: BAR 0: assigned [mem 0xb8000200-0xb800027f]
[    0.087050] pci 0000:00:09.0: BAR 0: set to [mem 0xb8000200-0xb800027f] (PCI address [0xb8000200-0xb800027f])
[    0.087064] pci 0000:00:07.0: BAR 14: assigned [mem 0xb8100000-0xb82fffff]
[    0.087077] pci 0000:00:07.0: BAR 15: assigned [mem 0xb8300000-0xb84fffff 64bit pref]
[    0.087088] pci 0000:00:07.0: BAR 13: assigned [io  0x2000-0x2fff]
[    0.087100] pci 0000:00:06.0: BAR 14: assigned [mem 0xb8500000-0xb86fffff]
[    0.087113] pci 0000:00:06.0: BAR 15: assigned [mem 0xb8700000-0xb88fffff 64bit pref]
[    0.087124] pci 0000:00:06.0: BAR 13: assigned [io  0x3000-0x3fff]
[    0.087136] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.087145] pci 0000:00:01.0:   bridge window [io  0x9000-0x9fff]
[    0.087158] pci 0000:00:01.0:   bridge window [mem 0xd4000000-0xd40fffff]
[    0.087169] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff pref]
[    0.087183] pci 0000:00:06.0: PCI bridge to [bus 02-02]
[    0.087192] pci 0000:00:06.0:   bridge window [io  0x3000-0x3fff]
[    0.087204] pci 0000:00:06.0:   bridge window [mem 0xb8500000-0xb86fffff]
[    0.087216] pci 0000:00:06.0:   bridge window [mem 0xb8700000-0xb88fffff 64bit pref]
[    0.087230] pci 0000:00:07.0: PCI bridge to [bus 03-03]
[    0.087239] pci 0000:00:07.0:   bridge window [io  0x2000-0x2fff]
[    0.087251] pci 0000:00:07.0:   bridge window [mem 0xb8100000-0xb82fffff]
[    0.087262] pci 0000:00:07.0:   bridge window [mem 0xb8300000-0xb84fffff 64bit pref]
[    0.087277] pci 0000:00:1f.0: PCI bridge to [bus 04-04]
[    0.087283] pci 0000:00:1f.0:   bridge window [io  disabled]
[    0.087294] pci 0000:00:1f.0:   bridge window [mem disabled]
[    0.087304] pci 0000:00:1f.0:   bridge window [mem pref disabled]
[    0.087338] pci 0000:00:01.0: setting latency timer to 64
[    0.087360] pci 0000:00:06.0: setting latency timer to 64
[    0.087380] pci 0000:00:07.0: setting latency timer to 64
[    0.087398] pci 0000:00:1f.0: setting latency timer to 64
[    0.087409] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.087416] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.087424] pci_bus 0000:01: resource 0 [io  0x9000-0x9fff]
[    0.087432] pci_bus 0000:01: resource 1 [mem 0xd4000000-0xd40fffff]
[    0.087440] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff pref]
[    0.087448] pci_bus 0000:02: resource 0 [io  0x3000-0x3fff]
[    0.087455] pci_bus 0000:02: resource 1 [mem 0xb8500000-0xb86fffff]
[    0.087463] pci_bus 0000:02: resource 2 [mem 0xb8700000-0xb88fffff 64bit pref]
[    0.087471] pci_bus 0000:03: resource 0 [io  0x2000-0x2fff]
[    0.087478] pci_bus 0000:03: resource 1 [mem 0xb8100000-0xb82fffff]
[    0.087487] pci_bus 0000:03: resource 2 [mem 0xb8300000-0xb84fffff 64bit pref]
[    0.087657] NET: Registered protocol family 2
[    0.087883] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.088765] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.092521] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.094958] TCP: Hash tables configured (established 131072 bind 65536)
[    0.094978] TCP reno registered
```

---

### Post by daniel_victoria on 2012-01-09
FIXED IT! Instead of using the nolapic boot parameter I used the noapic boot parameter and now both cores are detected! Yea!!!

---

