---
title: "All 3D apps quits."
date: 2010-04-30
forum: Hardware
---

### Post by meciu on 2010-04-30
Hi
I have problem with all 3d apps for example 
Quake III Arena
Installed by IOQUAKE3
all working fine, but after loading game quits and in terminal i can see error
```

drmRadeonCmdBuffer: -22. Kernel failed to parse or rejected command stream. See dmesg for more info.

```

and here is dmesg
```

meciu@ubuntu:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-21-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 (Ubuntu 2.6.32-21.32-generic 2.6.32.11+drm33.2)
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
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ffd0000 (usable)
[    0.000000]  BIOS-e820: 000000003ffd0000 - 000000003fff0c00 (reserved)
[    0.000000]  BIOS-e820: 000000003fff0c00 - 000000003fffc000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fffc000 - 0000000040000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] last_pfn = 0x3ffd0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FC0000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT not supported by CPU.
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003ffd0000 (usable)
[    0.000000]  modified: 000000003ffd0000 - 000000003fff0c00 (reserved)
[    0.000000]  modified: 000000003fff0c00 - 000000003fffc000 (ACPI NVS)
[    0.000000]  modified: 000000003fffc000 - 0000000040000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 2f882000 - 3001b212
[    0.000000] ACPI: RSDP 000f9970 00014 (v00 COMPAQ)
[    0.000000] ACPI: RSDT 3fff0c84 00030 (v01 COMPAQ CPQ0030  18110220 CPQ  00000001)
[    0.000000] ACPI: FACP 3fff0c00 00084 (v02 COMPAQ CPQ0030  00000002 CPQ  00000001)
[    0.000000] ACPI: DSDT 3fff0cb4 06FBB (v01 COMPAQ EVON600C 00010000 MSFT 0100000E)
[    0.000000] ACPI: FACS 3fffbe80 00040
[    0.000000] ACPI: SSDT 3fff7c6f 0004B (v01 COMPAQ   CPQCPU 00001001 MSFT 0100000E)
[    0.000000] ACPI: SSDT 3fff7cba 0010E (v01 COMPAQ  CPQGysr 00001001 MSFT 0100000E)
[    0.000000] 135MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008d9e98]    TEXT DATA BSS ==> [0000100000 - 00008d9e98]
[    0.000000]   #4 [002f882000 - 003001b212]          RAMDISK ==> [002f882000 - 003001b212]
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #6 [00008da000 - 00008dd108]              BRK ==> [00008da000 - 00008dd108]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003ffd0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003ffd0
[    0.000000] On node 0 totalpages: 261995
[    0.000000] free_area_init_node: node 0, pgdat c0798720, node_mem_map c1001000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 272 pages used for memmap
[    0.000000]   HighMem zone: 34498 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] APIC: disable apic facility
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:c0000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1c00000 s36024 r0 d21320 u4194304
[    0.000000] pcpu-alloc: s36024 r0 d21320 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259947
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic root=UUID=41ef7624-e8df-4a33-b01f-804b0637c4ec ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 5241920 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0003ffd0)
[    0.000000] Memory: 1017484k/1048384k available (4673k kernel code, 30056k reserved, 2122k data, 656k init, 139080k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a3000 - 0xc0847000   ( 656 kB)
[    0.000000]       .data : 0xc0590613 - 0xc07a2e48   (2122 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0590613   (4673 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 797.423 MHz processor.
[    0.008014] Calibrating delay loop (skipped), value calculated using timer frequency.. 1594.84 BogoMIPS (lpj=3189692)
[    0.008073] Security Framework initialized
[    0.008172] AppArmor: AppArmor initialized
[    0.008198] Mount-cache hash table entries: 512
[    0.008597] Initializing cgroup subsys ns
[    0.008614] Initializing cgroup subsys cpuacct
[    0.008627] Initializing cgroup subsys memory
[    0.008655] Initializing cgroup subsys devices
[    0.008664] Initializing cgroup subsys freezer
[    0.008672] Initializing cgroup subsys net_cls
[    0.008737] CPU: L1 I cache: 16K, L1 D cache: 16K
[    0.008747] CPU: L2 cache: 512K
[    0.008762] mce: CPU supports 5 MCE banks
[    0.008805] Performance Events: 
[    0.008813] no APIC, boot with the "lapic" boot parameter to force-enable it.
[    0.008820] no hardware sampling interrupt available.
[    0.008827] p6 PMU driver.
[    0.008843] ... version:                0
[    0.008849] ... bit width:              32
[    0.008855] ... generic registers:      2
[    0.008862] ... value mask:             00000000ffffffff
[    0.008869] ... max period:             000000007fffffff
[    0.008875] ... fixed-purpose events:   0
[    0.008882] ... event mask:             0000000000000003
[    0.008896] Checking 'hlt' instruction... OK.
[    0.025543] SMP alternatives: switching to UP code
[    0.041062] Freeing SMP alternatives: 19k freed
[    0.041092] ACPI: Core revision 20090903
[    0.058733] ACPI: setting ELCR to 0200 (from 0800)
[    0.060017] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.060032] ftrace: allocating 21771 entries in 43 pages
[    0.064250] Enabling APIC mode:  Flat.  Using 0 I/O APICs
[    0.064266] weird, boot CPU (#0) not listed by the BIOS.
[    0.064273] SMP motherboard not detected.
[    0.064280] Local APIC not detected. Using dummy APIC emulation.
[    0.064287] SMP disabled
[    0.064731] Brought up 1 CPUs
[    0.064744] Total of 1 processors activated (1594.84 BogoMIPS).
[    0.066282] CPU0 attaching NULL sched-domain.
[    0.068250] devtmpfs: initialized
[    0.069379] regulator: core version 0.5
[    0.069415] Time: 18:40:51  Date: 04/30/10
[    0.069553] NET: Registered protocol family 16
[    0.069890] EISA bus registered
[    0.069922] ACPI: bus type pci registered
[    0.071443] PCI: PCI BIOS revision 2.10 entry at 0xf04dd, last bus=4
[    0.071451] PCI: Using configuration type 1 for base access
[    0.074477] bio: create slab <bio-0> at 0
[    0.076523] ACPI: EC: Look up EC in DSDT
[    0.113761] ACPI: Interpreter enabled
[    0.113779] ACPI: (supports S0 S1 S3 S4 S5)
[    0.113845] ACPI: Using PIC for interrupt routing
[    0.142257] ACPI: Power Resource [C14E] (on)
[    0.142479] ACPI: Power Resource [C162] (on)
[    0.142707] ACPI: Power Resource [C167] (on)
[    0.142929] ACPI: Power Resource [C16B] (on)
[    0.143036] ACPI: Power Resource [C174] (on)
[    0.143244] ACPI: Power Resource [C1F3] (off)
[    0.143441] ACPI: Power Resource [C1F4] (off)
[    0.143638] ACPI: Power Resource [C1F5] (off)
[    0.145918] ACPI: ACPI Dock Station Driver: 1 docks/bays found
[    0.157186] ACPI: PCI Root Bridge [C03E] (0000:00)
[    0.157298] pci 0000:00:00.0: reg 10 32bit mmio pref: [0x60000000-0x6fffffff]
[    0.157458] pci 0000:00:1d.0: reg 20 io port: [0x4000-0x401f]
[    0.157528] pci 0000:00:1d.1: reg 20 io port: [0x4020-0x403f]
[    0.157597] pci 0000:00:1d.2: reg 20 io port: [0x4040-0x405f]
[    0.157734] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[    0.157745] pci 0000:00:1f.0: quirk: region 1100-113f claimed by ICH4 GPIO
[    0.157785] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.157798] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.157811] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.157824] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.157837] pci 0000:00:1f.1: reg 20 io port: [0x4060-0x406f]
[    0.157850] pci 0000:00:1f.1: reg 24 32bit mmio: [0x000000-0x0003ff]
[    0.157924] pci 0000:01:00.0: reg 10 32bit mmio pref: [0x48000000-0x4fffffff]
[    0.157937] pci 0000:01:00.0: reg 14 io port: [0x3000-0x30ff]
[    0.157949] pci 0000:01:00.0: reg 18 32bit mmio: [0x40200000-0x4020ffff]
[    0.157971] pci 0000:01:00.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.157998] pci 0000:01:00.0: supports D1 D2
[    0.158045] pci 0000:00:01.0: bridge io port: [0x3000-0x3fff]
[    0.158055] pci 0000:00:01.0: bridge 32bit mmio: [0x40200000-0x402fffff]
[    0.158065] pci 0000:00:01.0: bridge 32bit mmio pref: [0x48000000-0x4fffffff]
[    0.158121] pci 0000:02:03.0: reg 10 32bit mmio: [0x40000000-0x40000fff]
[    0.158147] pci 0000:02:03.0: supports D1 D2
[    0.158155] pci 0000:02:03.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.158166] pci 0000:02:03.0: PME# disabled
[    0.158211] pci 0000:02:03.1: reg 10 32bit mmio: [0x40080000-0x40080fff]
[    0.158238] pci 0000:02:03.1: supports D1 D2
[    0.158245] pci 0000:02:03.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.158255] pci 0000:02:03.1: PME# disabled
[    0.158307] pci 0000:02:04.0: reg 10 32bit mmio: [0x40180000-0x401800ff]
[    0.158321] pci 0000:02:04.0: reg 14 io port: [0x2840-0x2847]
[    0.158334] pci 0000:02:04.0: reg 18 io port: [0x2000-0x20ff]
[    0.158377] pci 0000:02:04.0: supports D2
[    0.158384] pci 0000:02:04.0: PME# supported from D2 D3hot D3cold
[    0.158393] pci 0000:02:04.0: PME# disabled
[    0.158440] pci 0000:02:08.0: reg 10 32bit mmio: [0x40100000-0x40100fff]
[    0.158454] pci 0000:02:08.0: reg 14 io port: [0x2800-0x283f]
[    0.158499] pci 0000:02:08.0: supports D1 D2
[    0.158506] pci 0000:02:08.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.158516] pci 0000:02:08.0: PME# disabled
[    0.158572] pci 0000:02:09.0: reg 10 io port: [0x2400-0x24ff]
[    0.158628] pci 0000:02:09.0: supports D1 D2
[    0.158635] pci 0000:02:09.0: PME# supported from D1 D2 D3hot
[    0.158645] pci 0000:02:09.0: PME# disabled
[    0.158686] pci 0000:00:1e.0: transparent bridge
[    0.158696] pci 0000:00:1e.0: bridge io port: [0x2000-0x2fff]
[    0.158706] pci 0000:00:1e.0: bridge 32bit mmio: [0x40000000-0x401fffff]
[    0.158766] pci_bus 0000:00: on NUMA node 0
[    0.158778] ACPI: PCI Interrupt Routing Table [\_SB_.C03E._PRT]
[    0.158906] ACPI: PCI Interrupt Routing Table [\_SB_.C03E.C03F._PRT]
[    0.158983] ACPI: PCI Interrupt Routing Table [\_SB_.C03E.C052._PRT]
[    0.184605] ACPI: PCI Interrupt Link [C0BA] (IRQs 5 10 *11)
[    0.185091] ACPI: PCI Interrupt Link [C0BB] (IRQs 5 10 *11)
[    0.185576] ACPI: PCI Interrupt Link [C0BC] (IRQs 5 10 *11)
[    0.186060] ACPI: PCI Interrupt Link [C0BD] (IRQs 5 10 *11)
[    0.186545] ACPI: PCI Interrupt Link [C0BE] (IRQs 5 10 *11)
[    0.187029] ACPI: PCI Interrupt Link [C0BF] (IRQs 5 10 *11)
[    0.187514] ACPI: PCI Interrupt Link [C0C0] (IRQs 5 10 *11)
[    0.187973] ACPI: PCI Interrupt Link [C0C1] (IRQs 5 10 11) *0, disabled.
[    0.188419] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.188434] vgaarb: loaded
[    0.188792] SCSI subsystem initialized
[    0.189011] libata version 3.00 loaded.
[    0.189237] usbcore: registered new interface driver usbfs
[    0.189279] usbcore: registered new interface driver hub
[    0.189371] usbcore: registered new device driver usb
[    0.189801] ACPI: WMI: Mapper loaded
[    0.189808] PCI: Using ACPI for IRQ routing
[    0.190149] NetLabel: Initializing
[    0.190156] NetLabel:  domain hash size = 128
[    0.190161] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.190198] NetLabel:  unlabeled traffic allowed by default
[    0.190301] Switching to clocksource tsc
[    0.193668] AppArmor: AppArmor Filesystem Enabled
[    0.193735] pnp: PnP ACPI init
[    0.193793] ACPI: bus type pnp registered
[    0.231896] pnp: PnP ACPI: found 15 devices
[    0.231905] ACPI: ACPI bus type pnp unregistered
[    0.231915] PnPBIOS: Disabled by ACPI PNP
[    0.231956] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.231968] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[    0.231978] system 00:00: iomem range 0x100000-0x3fffffff could not be reserved
[    0.232007] system 00:0c: ioport range 0x140-0x14f has been reserved
[    0.232017] system 00:0c: iomem range 0xffb00000-0xffbfffff has been reserved
[    0.232028] system 00:0c: iomem range 0xfff00000-0xffffffff has been reserved
[    0.232047] system 00:0d: ioport range 0x4d0-0x4d1 has been reserved
[    0.232057] system 00:0d: ioport range 0x1000-0x1087 could not be reserved
[    0.232067] system 00:0d: ioport range 0x1100-0x113f has been reserved
[    0.232077] system 00:0d: ioport range 0x1200-0x121f has been reserved
[    0.232087] system 00:0d: iomem range 0xffc00000-0xffc003ff has been reserved
[    0.232105] system 00:0e: iomem range 0xcf000-0xcffff has been reserved
[    0.267230] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.267240] pci 0000:00:01.0:   IO window: 0x3000-0x3fff
[    0.267250] pci 0000:00:01.0:   MEM window: 0x40200000-0x402fffff
[    0.267260] pci 0000:00:01.0:   PREFETCH window: 0x48000000-0x4fffffff
[    0.267288] pci 0000:02:03.0: CardBus bridge, secondary bus 0000:03
[    0.267296] pci 0000:02:03.0:   IO window: 0x002c00-0x002cff
[    0.267306] pci 0000:02:03.0:   IO window: 0x001400-0x0014ff
[    0.267316] pci 0000:02:03.0:   PREFETCH window: 0x50000000-0x53ffffff
[    0.267327] pci 0000:02:03.0:   MEM window: 0x44000000-0x47ffffff
[    0.267337] pci 0000:02:03.1: CardBus bridge, secondary bus 0000:04
[    0.267345] pci 0000:02:03.1:   IO window: 0x001800-0x0018ff
[    0.267355] pci 0000:02:03.1:   IO window: 0x001c00-0x001cff
[    0.267365] pci 0000:02:03.1:   PREFETCH window: 0x54000000-0x57ffffff
[    0.267375] pci 0000:02:03.1:   MEM window: 0x58000000-0x5bffffff
[    0.267385] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.267394] pci 0000:00:1e.0:   IO window: 0x2000-0x2fff
[    0.267405] pci 0000:00:1e.0:   MEM window: 0x40000000-0x401fffff
[    0.267416] pci 0000:00:1e.0:   PREFETCH window: 0x50000000-0x57ffffff
[    0.267445] pci 0000:00:1e.0: setting latency timer to 64
[    0.268160] ACPI: PCI Interrupt Link [C0C0] enabled at IRQ 11
[    0.268168] PCI: setting IRQ 11 as level-triggered
[    0.268180] pci 0000:02:03.0: PCI INT A -> Link[C0C0] -> GSI 11 (level, low) -> IRQ 11
[    0.268204] pci 0000:02:03.1: PCI INT A -> Link[C0C0] -> GSI 11 (level, low) -> IRQ 11
[    0.268220] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.268229] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.268238] pci_bus 0000:01: resource 0 io:  [0x3000-0x3fff]
[    0.268247] pci_bus 0000:01: resource 1 mem: [0x40200000-0x402fffff]
[    0.268256] pci_bus 0000:01: resource 2 pref mem [0x48000000-0x4fffffff]
[    0.268265] pci_bus 0000:02: resource 0 io:  [0x2000-0x2fff]
[    0.268273] pci_bus 0000:02: resource 1 mem: [0x40000000-0x401fffff]
[    0.268282] pci_bus 0000:02: resource 2 pref mem [0x50000000-0x57ffffff]
[    0.268291] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.268299] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.268308] pci_bus 0000:03: resource 0 io:  [0x2c00-0x2cff]
[    0.268316] pci_bus 0000:03: resource 1 io:  [0x1400-0x14ff]
[    0.268325] pci_bus 0000:03: resource 2 pref mem [0x50000000-0x53ffffff]
[    0.268334] pci_bus 0000:03: resource 3 mem: [0x44000000-0x47ffffff]
[    0.268342] pci_bus 0000:04: resource 0 io:  [0x1800-0x18ff]
[    0.268351] pci_bus 0000:04: resource 1 io:  [0x1c00-0x1cff]
[    0.268359] pci_bus 0000:04: resource 2 pref mem [0x54000000-0x57ffffff]
[    0.268368] pci_bus 0000:04: resource 3 mem: [0x58000000-0x5bffffff]
[    0.268483] NET: Registered protocol family 2
[    0.268793] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.269937] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.274442] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.276934] TCP: Hash tables configured (established 131072 bind 65536)
[    0.276945] TCP reno registered
[    0.277384] NET: Registered protocol family 1
[    0.277533] pci 0000:01:00.0: Boot video device
[    0.277663] pci 0000:02:08.0: Firmware left e100 interrupts enabled; disabling
[    0.278244] speedstep-lib: frequency transition measured seems out of range (7200 nSec), falling back to a safe one of500000 nSec.
[    0.278307] Marking TSC unstable due to cpufreq changes
[    0.278435] cpufreq-nforce2: No nForce2 chipset.
[    0.278494] Scanning for low memory corruption every 60 seconds
[    0.278735] audit: initializing netlink socket (disabled)
[    0.278766] type=2000 audit(1272652851.277:1): initialized
[    0.303108] Trying to unpack rootfs image as initramfs...
[    0.306602] Switching to clocksource acpi_pm
[    0.328850] highmem bounce pool size: 64 pages
[    0.328867] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.335940] VFS: Disk quotas dquot_6.5.2
[    0.336162] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.340288] fuse init (API version 7.13)
[    0.340556] msgmni has been set to 1716
[    0.344469] alg: No test for stdrng (krng)
[    0.344635] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.344643] io scheduler noop registered
[    0.344647] io scheduler anticipatory registered
[    0.344652] io scheduler deadline registered
[    0.344770] io scheduler cfq registered (default)
[    0.345034] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.345087] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.345572] ACPI: AC Adapter [C1A2] (off-line)
[    0.345784] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
[    0.345800] ACPI: Sleep Button [C1A3]
[    0.345896] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    0.346026] ACPI: Lid Switch [C1A4]
[    0.346123] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.346129] ACPI: Power Button [PWRF]
[    0.346464] fan PNP0C0B:00: registered as cooling_device0
[    0.346477] ACPI: Fan [C1F6] (off)
[    0.346744] fan PNP0C0B:01: registered as cooling_device1
[    0.346756] ACPI: Fan [C1F7] (off)
[    0.347027] fan PNP0C0B:02: registered as cooling_device2
[    0.347039] ACPI: Fan [C1F8] (off)
[    0.347689] processor LNXCPU:00: registered as cooling_device3
[    0.381642] thermal LNXTHERM:01: registered as thermal_zone0
[    0.381670] ACPI: Thermal Zone [TZ1] (52 C)
[    0.392949] ACPI: Battery Slot [C1A0] (battery absent)
[    0.393008] isapnp: Scanning for PnP cards...
[    0.399569] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.399697] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.399868] serial8250: ttyS2 at I/O 0x3e8 (irq = 4) is a 16550A
[    0.400297] 00:02: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.402854] brd: module loaded
[    0.403928] loop: module loaded
[    0.456282] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.456589] ata_piix 0000:00:1f.1: version 2.13
[    0.456616] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    0.462131] ACPI: PCI Interrupt Link [C0BC] enabled at IRQ 11
[    0.462147] ata_piix 0000:00:1f.1: PCI INT A -> Link[C0BC] -> GSI 11 (level, low) -> IRQ 11
[    0.462254] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.462468] scsi0 : ata_piix
[    0.464556] scsi1 : ata_piix
[    0.465977] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x4060 irq 14
[    0.465984] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x4068 irq 15
[    0.466892] Fixed MDIO Bus: probed
[    0.466975] PPP generic driver version 2.4.2
[    0.467134] tun: Universal TUN/TAP device driver, 1.6
[    0.467139] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.467356] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.467394] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.467424] uhci_hcd: USB Universal Host Controller Interface driver
[    0.473442] ACPI: PCI Interrupt Link [C0BA] enabled at IRQ 11
[    0.473457] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[C0BA] -> GSI 11 (level, low) -> IRQ 11
[    0.473481] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.473488] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.473670] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    0.473715] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00004000
[    0.473974] usb usb1: configuration #1 chosen from 1 choice
[    0.474041] hub 1-0:1.0: USB hub found
[    0.474061] hub 1-0:1.0: 2 ports detected
[    0.474682] ACPI: PCI Interrupt Link [C0BD] enabled at IRQ 11
[    0.474691] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[C0BD] -> GSI 11 (level, low) -> IRQ 11
[    0.474704] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.474710] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.474800] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    0.474830] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00004020
[    0.475020] usb usb2: configuration #1 chosen from 1 choice
[    0.475075] hub 2-0:1.0: USB hub found
[    0.475094] hub 2-0:1.0: 2 ports detected
[    0.475178] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[C0BC] -> GSI 11 (level, low) -> IRQ 11
[    0.475190] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.475196] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.475270] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    0.475298] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00004040
[    0.475482] usb usb3: configuration #1 chosen from 1 choice
[    0.475538] hub 3-0:1.0: USB hub found
[    0.475554] hub 3-0:1.0: 2 ports detected
[    0.475763] PNP: PS/2 Controller [PNP0303:C171,PNP0f0e:C172] at 0x60,0x64 irq 1,12
[    0.477311] i8042.c: Detected active multiplexing controller, rev 1.0.
[    0.480843] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.480872] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.480970] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.481040] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.481091] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.481430] mice: PS/2 mouse device common for all mice
[    0.481744] rtc_cmos 00:09: RTC can wake from S4
[    0.481843] rtc_cmos 00:09: rtc core: registered rtc_cmos as rtc0
[    0.481871] rtc0: alarms up to one month, y3k, 114 bytes nvram
[    0.482154] device-mapper: uevent: version 1.0.3
[    0.484742] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.488451] device-mapper: multipath: version 1.1.0 loaded
[    0.488462] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.488948] EISA: Probing bus 0 at eisa.0
[    0.488962] Cannot allocate resource for EISA slot 1
[    0.488968] Cannot allocate resource for EISA slot 2
[    0.488973] Cannot allocate resource for EISA slot 3
[    0.488977] Cannot allocate resource for EISA slot 4
[    0.488994] EISA: Detected 0 cards.
[    0.489242] cpuidle: using governor ladder
[    0.489364] cpuidle: using governor menu
[    0.490443] TCP cubic registered
[    0.490820] NET: Registered protocol family 10
[    0.491925] lo: Disabled Privacy Extensions
[    0.492743] NET: Registered protocol family 17
[    0.492861] Using IPI No-Shortcut mode
[    0.493085] PM: Resume from disk failed.
[    0.493122] registered taskstats version 1
[    0.493455]   Magic number: 6:285:697
[    0.493643] rtc_cmos 00:09: setting system clock to 2010-04-30 18:40:51 UTC (1272652851)
[    0.493650] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.493654] EDD information not available.
[    0.503325] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.672676] ata1.00: ATA-5: IC25N030ATCS04-0, CA3OA71A, max UDMA/100
[    0.672685] ata1.00: 58605120 sectors, multi 16: LBA 
[    0.688567] ata1.00: configured for UDMA/100
[    0.727287] ACPI: Battery Slot [C19F] (battery present)
[    0.784359] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    0.793034] ata2.00: ATAPI: Compaq  DVD-ROM DRN-8080B, 2.18, max MWDMA2
[    0.808541] ata2.00: configured for MWDMA2
[    1.004429] usb 2-1: configuration #1 chosen from 1 choice
[    1.139752] isapnp: No Plug & Play device found
[    1.140188] scsi 0:0:0:0: Direct-Access     ATA      IC25N030ATCS04-0 CA3O PQ: 0 ANSI: 5
[    1.140587] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.140973] sd 0:0:0:0: [sda] 58605120 512-byte logical blocks: (30.0 GB/27.9 GiB)
[    1.141094] sd 0:0:0:0: [sda] Write Protect is off
[    1.141101] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.141162] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.141507]  sda:
[    1.145850] scsi 1:0:0:0: CD-ROM            COMPAQ   DVD-ROM DRN8080B 2.18 PQ: 0 ANSI: 5
[    1.149042] sr0: scsi3-mmc drive: 0x/24x cd/rw xa/form2 cdda tray
[    1.149051] Uniform CD-ROM driver Revision: 3.20
[    1.149302] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.149464] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.171983]  sda1 sda2 < sda5 >
[    1.193157] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.196719] Freeing initrd memory: 7780k freed
[    1.216838] Freeing unused kernel memory: 656k freed
[    1.218654] Write protecting the kernel text: 4676k
[    1.218732] Write protecting the kernel read-only data: 1840k
[    1.257842] udev: starting version 151
[    1.806832] Floppy drive(s): fd0 is 1.44M
[    1.829241] FDC 0 is a post-1991 82077
[    1.845148] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
[    1.845155] e100: Copyright(c) 1999-2006 Intel Corporation
[    1.845834] ACPI: PCI Interrupt Link [C0BE] enabled at IRQ 11
[    1.845844] e100 0000:02:08.0: PCI INT A -> Link[C0BE] -> GSI 11 (level, low) -> IRQ 11
[    1.933597] e100 0000:02:08.0: PME# disabled
[    1.935313] e100: eth0: e100_probe: addr 0x40100000, irq 11, MAC addr 00:02:a5:b8:88:7b
[    2.150629] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    2.150641] EXT4-fs (sda1): write access will be enabled during recovery
[    3.747322] EXT4-fs (sda1): recovery complete
[    3.748599] EXT4-fs (sda1): mounted filesystem with ordered data mode
[   25.954827] Adding 1253368k swap on /dev/sda5.  Priority:-1 extents:1 across:1253368k 
[   25.998189] udev: starting version 151
[   26.033466] Disabling lock debugging due to kernel taint
[   26.518857] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   26.529633] EXT4-fs (sda1): warning: maximal mount count reached, running e2fsck is recommended
[   27.176623] irda_init()
[   27.176665] NET: Registered protocol family 23
[   27.238390] Linux agpgart interface v0.103
[   27.259439] parport_pc 00:05: reported by Plug and Play ACPI
[   27.259480] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   27.285837] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   27.293353] intel_rng: FWH not detected
[   27.338965] found SMC SuperIO Chip (devid=0x0e rev=01 base=0x002e): LPC47N252
[   27.338991] smsc_ircc_present: can't get sir_base of 0x3e8
[   27.371989] agpgart-intel 0000:00:00.0: Intel 830M Chipset
[   27.400882] usb 2-1: reset full speed USB device using uhci_hcd and address 2
[   27.467564] ppdev: user-space parallel port driver
[   27.541336] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x60000000
[   27.646208] type=1505 audit(1272645678.650:2):  operation="profile_load" pid=621 name="/sbin/dhclient3"
[   27.647126] type=1505 audit(1272645678.650:3):  operation="profile_load" pid=621 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   27.647625] type=1505 audit(1272645678.650:4):  operation="profile_load" pid=621 name="/usr/lib/connman/scripts/dhclient-script"
[   27.685560] ndiswrapper: driver netwg11t (NETGEAR,01/07/2005,1.0.1.1007) loaded
[   27.732096] [drm] Initialized drm 1.1.0 20060810
[   27.921164] yenta_cardbus 0000:02:03.0: CardBus bridge found [0e11:004e]
[   27.921190] yenta_cardbus 0000:02:03.0: Enabling burst memory read transactions
[   27.921198] yenta_cardbus 0000:02:03.0: Using CSCINT to route CSC interrupts to PCI
[   27.921204] yenta_cardbus 0000:02:03.0: Routing CardBus interrupts to PCI
[   27.921212] yenta_cardbus 0000:02:03.0: TI: mfunc 0x01001002, devctl 0x64
[   28.155093] wlan0: ethernet device 00:14:6c:ec:12:48 using NDIS driver: netwg11t, version: 0x10000, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 1385:4250.F.conf
[   28.155136] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
[   28.155592] usbcore: registered new interface driver ndiswrapper
[   28.160516] yenta_cardbus 0000:02:03.0: ISA IRQ mask 0x0438, PCI irq 11
[   28.160526] yenta_cardbus 0000:02:03.0: Socket status: 30000006
[   28.160544] yenta_cardbus 0000:02:03.0: pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   28.160554] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x2000-0x2fff: clean.
[   28.160933] yenta_cardbus 0000:02:03.0: pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x401fffff
[   28.160941] yenta_cardbus 0000:02:03.0: pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x57ffffff
[   28.160965] Synaptics Touchpad, model: 1, fw: 5.8, id: 0x9b48b1, caps: 0x884793/0x0
[   28.160974] serio: Synaptics pass-through port at isa0060/serio4/input0
[   28.171463] yenta_cardbus 0000:02:03.1: CardBus bridge found [0e11:004e]
[   28.171488] yenta_cardbus 0000:02:03.1: Using CSCINT to route CSC interrupts to PCI
[   28.171493] yenta_cardbus 0000:02:03.1: Routing CardBus interrupts to PCI
[   28.171501] yenta_cardbus 0000:02:03.1: TI: mfunc 0x01001002, devctl 0x64
[   28.255156] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input5
[   28.360557] [drm] radeon defaulting to kernel modesetting.
[   28.360570] [drm] radeon kernel modesetting enabled.
[   28.361314] ACPI: PCI Interrupt Link [C0BB] enabled at IRQ 11
[   28.361324] radeon 0000:01:00.0: PCI INT A -> Link[C0BB] -> GSI 11 (level, low) -> IRQ 11
[   28.400553] yenta_cardbus 0000:02:03.1: ISA IRQ mask 0x0438, PCI irq 11
[   28.400562] yenta_cardbus 0000:02:03.1: Socket status: 30000006
[   28.400570] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #04 to #07
[   28.400590] yenta_cardbus 0000:02:03.1: pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   28.400599] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x2000-0x2fff: clean.
[   28.400978] yenta_cardbus 0000:02:03.1: pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x401fffff
[   28.400986] yenta_cardbus 0000:02:03.1: pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x57ffffff
[   28.417391] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.426585] [drm] radeon: Initializing kernel modesetting.
[   28.429603] [drm] register mmio base: 0x40200000
[   28.429611] [drm] register mmio size: 65536
[   28.430079] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
[   28.430119] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[   28.430144] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
[   28.430170] radeon 0000:01:00.0: putting AGP V2 device into 4x mode
[   28.430204] [drm] radeon: VRAM 64M
[   28.430209] [drm] radeon: VRAM from 0x00000000 to 0x03FFFFFF
[   28.430213] [drm] radeon: GTT 256M
[   28.430217] [drm] radeon: GTT from 0x60000000 to 0x6FFFFFFF
[   28.430264] [drm] radeon: irq initialized.
[   28.430632] [drm] Detected VRAM RAM=64M, BAR=128M
[   28.430642] [drm] RAM width 64bits DDR
[   28.447789] lp0: using parport0 (interrupt-driven).
[   28.463210] [TTM] Zone  kernel: Available graphics memory: 443650 kiB.
[   28.463218] [TTM] Zone highmem: Available graphics memory: 513190 kiB.
[   28.463266] [drm] radeon: 32M of VRAM memory ready
[   28.463271] [drm] radeon: 256M of GTT memory ready.
[   28.504626] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.547136] [drm] radeon: cp idle (0x00008080)
[   28.547299] [drm] Loading R100 Microcode
[   28.547891] platform radeon_cp.0: firmware: requesting radeon/R100_cp.bin
[   28.643842] type=1505 audit(1272645679.646:5):  operation="profile_load" pid=734 name="/usr/share/gdm/guest-session/Xsession"
[   28.674205] type=1505 audit(1272645679.678:6):  operation="profile_replace" pid=740 name="/sbin/dhclient3"
[   28.675117] type=1505 audit(1272645679.678:7):  operation="profile_replace" pid=740 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   28.675823] type=1505 audit(1272645679.678:8):  operation="profile_replace" pid=740 name="/usr/lib/connman/scripts/dhclient-script"
[   28.713425] [drm] radeon: ring at 0x0000000060000000
[   28.713453] [drm] ring test succeeded in 1 usecs
[   28.765999] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x100-0x3af: excluding 0x100-0x107
[   28.766892] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3e0-0x4ff: clean.
[   28.767301] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x820-0x8ff: clean.
[   28.767669] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7: clean.
[   28.769494] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff: clean.
[   28.780699] type=1505 audit(1272645679.786:9):  operation="profile_load" pid=741 name="/usr/bin/evince"
[   28.815216] type=1505 audit(1272645679.818:10):  operation="profile_load" pid=741 name="/usr/bin/evince-previewer"
[   28.826871] [drm] radeon: ib pool ready.
[   28.827064] [drm] ib test succeeded in 0 usecs
[   28.832356] [drm] Panel ID String: Samsung LTN150P1-L02    
[   28.832366] [drm] Panel Size 1400x1050
[   28.832681] [drm] Default TV standard: NTSC
[   28.832685] [drm] 27.000000000 MHz TV ref clk
[   28.832693] [drm] Default TV standard: NTSC
[   28.832696] [drm] 27.000000000 MHz TV ref clk
[   28.832958] [drm] Radeon Display Connectors
[   28.832964] [drm] Connector 0:
[   28.832968] [drm]   VGA
[   28.832974] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   28.832978] [drm]   Encoders:
[   28.832981] [drm]     CRT1: INTERNAL_DAC1
[   28.832985] [drm] Connector 1:
[   28.832989] [drm]   LVDS
[   28.832991] [drm]   Encoders:
[   28.832995] [drm]     LCD1: INTERNAL_LVDS
[   28.832998] [drm] Connector 2:
[   28.833002] [drm]   S-video
[   28.833004] [drm]   Encoders:
[   28.833008] [drm]     TV1: INTERNAL_DAC2
[   28.880142] type=1505 audit(1272645679.886:11):  operation="profile_load" pid=741 name="/usr/bin/evince-thumbnailer"
[   29.007455] [drm] fb mappable at 0x48040000
[   29.007462] [drm] vram apper at 0x48000000
[   29.007467] [drm] size 1478400
[   29.007470] [drm] fb depth is 8
[   29.007473] [drm]    pitch is 1408
[   29.012890] fb0: radeondrmfb frame buffer device
[   29.012897] registered panic notifier
[   29.012912] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:00.0 on minor 0
[   29.035209] vga16fb: initializing
[   29.035221] vga16fb: mapped to 0xc00a0000
[   29.035235] vga16fb: not registering due to another framebuffer present
[   29.241326] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x100-0x107
[   29.242219] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   29.258767] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   29.259150] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   29.259777] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   29.318291] Maestro3 0000:02:09.0: PCI INT A -> Link[C0BA] -> GSI 11 (level, low) -> IRQ 11
[   29.318309] Maestro3 0000:02:09.0: firmware: requesting ess/maestro3_assp_kernel.fw
[   29.326940] Maestro3 0000:02:09.0: firmware: requesting ess/maestro3_assp_minisrc.fw
[   29.383249] Console: switching to colour frame buffer device 175x65
[   31.998952] psmouse serio5: ID: 10 00 64
[   36.587036] IBM TrackPoint firmware: 0x0b, buttons: 2/3
[   36.869585] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio4/serio5/input/input6
[   43.783295] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[   43.828268] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   53.844036] wlan0: no IPv6 routers present
[   72.571764] end_request: I/O error, dev fd0, sector 0
[  106.519031] end_request: I/O error, dev fd0, sector 0
[  135.023250] [drm:r100_cs_track_texture_check] *ERROR* No texture bound to unit 1
[  135.023262] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[  140.466871] end_request: I/O error, dev fd0, sector 0
[  140.466891] __ratelimit: 9 callbacks suppressed
[  140.466899] Buffer I/O error on device fd0, logical block 0
[  174.543799] end_request: I/O error, dev fd0, sector 0
[  174.543820] Buffer I/O error on device fd0, logical block 0
[  208.531279] end_request: I/O error, dev fd0, sector 0
[  208.531297] Buffer I/O error on device fd0, logical block 0
[  242.844343] end_request: I/O error, dev fd0, sector 0
[  242.844364] Buffer I/O error on device fd0, logical block 0
[  277.698305] end_request: I/O error, dev fd0, sector 0
[  277.698325] Buffer I/O error on device fd0, logical block 0
[  311.991222] end_request: I/O error, dev fd0, sector 0
[  311.991242] Buffer I/O error on device fd0, logical block 0
[  346.189356] end_request: I/O error, dev fd0, sector 0
[  346.189376] Buffer I/O error on device fd0, logical block 0
[  380.432184] end_request: I/O error, dev fd0, sector 0
[  380.432206] Buffer I/O error on device fd0, logical block 0
[  414.791392] end_request: I/O error, dev fd0, sector 0
[  414.791412] Buffer I/O error on device fd0, logical block 0
[  448.886348] end_request: I/O error, dev fd0, sector 0
[  448.886369] Buffer I/O error on device fd0, logical block 0
[  483.109190] end_request: I/O error, dev fd0, sector 0
[  483.109206] Buffer I/O error on device fd0, logical block 0
[  517.026382] end_request: I/O error, dev fd0, sector 0
[  517.026399] Buffer I/O error on device fd0, logical block 0
[  551.018126] end_request: I/O error, dev fd0, sector 0
[  551.018146] Buffer I/O error on device fd0, logical block 0
[  585.086823] end_request: I/O error, dev fd0, sector 0
[  585.086842] Buffer I/O error on device fd0, logical block 0
[  619.425779] end_request: I/O error, dev fd0, sector 0
[  619.425796] Buffer I/O error on device fd0, logical block 0
[  653.554299] end_request: I/O error, dev fd0, sector 0
[  653.554327] Buffer I/O error on device fd0, logical block 0
[  687.806164] end_request: I/O error, dev fd0, sector 0
[  687.806184] Buffer I/O error on device fd0, logical block 0
[  716.583297] [drm:r100_cs_track_texture_check] *ERROR* No texture bound to unit 1
[  716.583312] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[  721.765927] end_request: I/O error, dev fd0, sector 0
[  721.765948] Buffer I/O error on device fd0, logical block 0
[  755.916583] end_request: I/O error, dev fd0, sector 0
[  755.916600] Buffer I/O error on device fd0, logical block 0
[  790.397778] end_request: I/O error, dev fd0, sector 0
[  790.397799] Buffer I/O error on device fd0, logical block 0
[  824.441064] end_request: I/O error, dev fd0, sector 0
[  824.441080] Buffer I/O error on device fd0, logical block 0
[  858.806100] end_request: I/O error, dev fd0, sector 0
[  858.806120] Buffer I/O error on device fd0, logical block 0
[  892.727617] end_request: I/O error, dev fd0, sector 0
[  892.727644] Buffer I/O error on device fd0, logical block 0
[  926.892041] end_request: I/O error, dev fd0, sector 0
[  926.892041] Buffer I/O error on device fd0, logical block 0
[  960.940545] end_request: I/O error, dev fd0, sector 0
[  960.940577] Buffer I/O error on device fd0, logical block 0
[  995.182086] end_request: I/O error, dev fd0, sector 0
[  995.182113] Buffer I/O error on device fd0, logical block 0
[ 1029.194438] end_request: I/O error, dev fd0, sector 0
[ 1029.194466] Buffer I/O error on device fd0, logical block 0
[ 1063.189837] end_request: I/O error, dev fd0, sector 0
[ 1063.189863] Buffer I/O error on device fd0, logical block 0
[ 1097.166533] end_request: I/O error, dev fd0, sector 0
[ 1097.166562] Buffer I/O error on device fd0, logical block 0
[ 1131.264852] end_request: I/O error, dev fd0, sector 0
[ 1131.264892] Buffer I/O error on device fd0, logical block 0
[ 1165.378405] end_request: I/O error, dev fd0, sector 0
[ 1165.378430] Buffer I/O error on device fd0, logical block 0
[ 1199.434677] end_request: I/O error, dev fd0, sector 0
[ 1199.434708] Buffer I/O error on device fd0, logical block 0
[ 1233.475902] end_request: I/O error, dev fd0, sector 0
[ 1233.475932] Buffer I/O error on device fd0, logical block 0
[ 1267.564028] end_request: I/O error, dev fd0, sector 0
[ 1267.564028] Buffer I/O error on device fd0, logical block 0
[ 1301.493847] end_request: I/O error, dev fd0, sector 0
[ 1301.493875] Buffer I/O error on device fd0, logical block 0
[ 1335.530650] end_request: I/O error, dev fd0, sector 0
[ 1335.530676] Buffer I/O error on device fd0, logical block 0
[ 1369.462339] end_request: I/O error, dev fd0, sector 0
[ 1369.462364] Buffer I/O error on device fd0, logical block 0
[ 1403.386715] end_request: I/O error, dev fd0, sector 0
[ 1403.386741] Buffer I/O error on device fd0, logical block 0
[ 1437.306585] end_request: I/O error, dev fd0, sector 0
[ 1437.306611] Buffer I/O error on device fd0, logical block 0
[ 1471.236005] end_request: I/O error, dev fd0, sector 0
[ 1471.236026] Buffer I/O error on device fd0, logical block 0
[ 1474.456446] [drm:r100_cs_track_texture_check] *ERROR* No texture bound to unit 1
[ 1474.456468] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 1505.186708] end_request: I/O error, dev fd0, sector 0
[ 1539.221811] end_request: I/O error, dev fd0, sector 0
[ 1573.241837] end_request: I/O error, dev fd0, sector 0
[ 1607.306618] end_request: I/O error, dev fd0, sector 0
[ 1607.306645] Buffer I/O error on device fd0, logical block 0
[ 1628.060092] [drm:r100_cs_track_texture_check] *ERROR* No texture bound to unit 1
[ 1628.060107] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
meciu@ubuntu:~$ 

```

My X11
```

Section "Device"
Identifier	"ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
Driver	 "radeon"
BusID	 "PCI:1:0:0"
# Acceleration
Option	 "AGPMode" "4"
Option	 "AGPSize" "64" # default: 8
Option	 "RingSize" "8"
Option	 "BufferSize" "2"
#	Option	 "SWcursor" "off"
#	Option	 "EnablePageFlip" "true"
#	Option	 "ColorTiling" "on"
#	Option	 "EnableDepthMoves" "true"
# Enable (partial) PowerPlay features
Option	 "DynamicClocks" "on"
# Use bios hot keys on ThinkPad (aka fn+f7)
Option "BIOSHotkeys" "on"
# Enable AIGLX
Option	 "XAANoOffscreenPixmaps" "true"
Option	 "DRI" "true"
EndSection
```

Its Laptop Compaq Evo N600c 
Intel Pentium III 1,2 GHz
1024MB SDRAM 133 MHz
Radeon M6 LY

Ubuntu 10.04

sorry for my bad english

---

### Post by razy8 on 2010-06-27
same here

anybody out there ?

---

