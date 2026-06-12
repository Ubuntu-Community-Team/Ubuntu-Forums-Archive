---
title: "Usb ports doesn't works"
date: 2010-08-17
forum: Hardware
---

### Post by djcasti on 2010-08-17
Goodnight

I have an Acer Aspire 5100 laptop which I have just installed Ubuntu 10.04 from the day it was released in April.

Everything worked perfectly until the usb ports stopped working altogether.

Looking back, I remember that the last thing I installed was Adobe Air and then installed TweetDeck. I'm not sure what were the last automatic updates installed.

Then proceeded to uninstall the programs above but everything remained the same.

When you run the command lsusb I get the following:

```

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

When i run the command dmesg I get the following output:

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-24-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 (Ubuntu 2.6.32-24.39-generic 2.6.32.15+drm33.5)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000077e90000 (usable)
[    0.000000]  BIOS-e820: 0000000077e90000 - 0000000077e9a000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000077e9a000 - 0000000077f00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000077f00000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0x77e90 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-E3FFF uncachable
[    0.000000]   E4000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 base 0078000000 mask FFF8000000 uncachable
[    0.000000]   2 disabled
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
[    0.000000]  modified: 0000000000006000 - 000000000009dc00 (usable)
[    0.000000]  modified: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 0000000077e90000 (usable)
[    0.000000]  modified: 0000000077e90000 - 0000000077e9a000 (ACPI data)
[    0.000000]  modified: 0000000077e9a000 - 0000000077f00000 (ACPI NVS)
[    0.000000]  modified: 0000000077f00000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 37857000 - 37fef207
[    0.000000] Allocated new RAMDISK: 008e0000 - 01078207
[    0.000000] Move RAMDISK from 0000000037857000 - 0000000037fef206 to 008e0000 - 01078206
[    0.000000] ACPI: RSDP 000f80e0 00014 (v00 PTLTD )
[    0.000000] ACPI: RSDT 77e91f82 00034 (v01 PTLTD    RSDT   06040000  LTP 00000000)
[    0.000000] ACPI: FACP 77e99d7a 00074 (v01 ATI    Bowfin   06040000 ATI  000F4240)
[    0.000000] ACPI: DSDT 77e91fb6 07DC4 (v01   Acer  Navarro 06040000 MSFT 0100000E)
[    0.000000] ACPI: FACS 77e9afc0 00040
[    0.000000] ACPI: SSDT 77e99dee 00182 (v01 PTLTD  POWERNOW 06040000  LTP 00000001)
[    0.000000] ACPI: APIC 77e99f70 00054 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: MCFG 77e99fc4 0003C (v01 PTLTD    MCFG   06040000  LTP 00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1030MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008dbeb8]    TEXT DATA BSS ==> [0000100000 - 00008dbeb8]
[    0.000000]   #4 [000009dc00 - 0000100000]    BIOS reserved ==> [000009dc00 - 0000100000]
[    0.000000]   #5 [00008dc000 - 00008df111]              BRK ==> [00008dc000 - 00008df111]
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #7 [00008e0000 - 0001078207]      NEW RAMDISK ==> [00008e0000 - 0001078207]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00f8110] f8110
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x00077e90
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x00077e90
[    0.000000] On node 0 totalpages: 491049
[    0.000000] free_area_init_node: node 0, pgdat c0798780, node_mem_map c107a000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3961 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2062 pages used for memmap
[    0.000000]   HighMem zone: 261764 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] SB4X0 revision 0x83
[    0.000000] Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d0000
[    0.000000] PM: Registered nosave memory: 00000000000d0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:60000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2000000 s36056 r0 d21288 u2097152
[    0.000000] pcpu-alloc: s36056 r0 d21288 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 487211
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=f0cb8699-e132-4ddf-9d61-5e443598d668 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 9823040 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:00077e90)
[    0.000000] Memory: 1921376k/1964608k available (4679k kernel code, 41780k reserved, 2116k data, 660k init, 1055304k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a3000 - 0xc0848000   ( 660 kB)
[    0.000000]       .data : 0xc0591d43 - 0xc07a2e88   (2116 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0591d43   (4679 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1596.070 MHz processor.
[    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 3192.14 BogoMIPS (lpj=6384280)
[    0.004027] Security Framework initialized
[    0.004049] AppArmor: AppArmor initialized
[    0.004058] Mount-cache hash table entries: 512
[    0.004196] Initializing cgroup subsys ns
[    0.004200] Initializing cgroup subsys cpuacct
[    0.004206] Initializing cgroup subsys memory
[    0.004214] Initializing cgroup subsys devices
[    0.004217] Initializing cgroup subsys freezer
[    0.004220] Initializing cgroup subsys net_cls
[    0.004240] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004244] CPU: L2 Cache: 256K (64 bytes/line)
[    0.004247] CPU: Physical Processor ID: 0
[    0.004249] CPU: Processor Core ID: 0
[    0.004254] mce: CPU supports 5 MCE banks
[    0.004266] using C1E aware idle routine
[    0.004273] Performance Events: AMD PMU driver.
[    0.004281] ... version:                0
[    0.004283] ... bit width:              48
[    0.004286] ... generic registers:      4
[    0.004289] ... value mask:             0000ffffffffffff
[    0.004292] ... max period:             00007fffffffffff
[    0.004294] ... fixed-purpose events:   0
[    0.004297] ... event mask:             000000000000000f
[    0.004302] Checking 'hlt' instruction... OK.
[    0.022733] ACPI: Core revision 20090903
[    0.036012] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.036019] ftrace: allocating 21780 entries in 43 pages
[    0.040089] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.040440] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.081782] CPU0: AMD Turion(tm) 64 X2 Mobile Technology TL-50 stepping 02
[    0.084001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.008000] Initializing CPU#1
[    0.008000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.008000] CPU: L2 Cache: 256K (64 bytes/line)
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 1
[    0.168120] CPU1: AMD Turion(tm) 64 X2 Mobile Technology TL-50 stepping 02
[    0.168156] Brought up 2 CPUs
[    0.168159] Total of 2 processors activated (6384.33 BogoMIPS).
[    0.168154] System has AMD C1E enabled
[    0.168154] Switch to broadcast mode on CPU1
[    0.168326] CPU0 attaching sched-domain:
[    0.168330]  domain 0: span 0-1 level MC
[    0.168334]   groups: 0 1
[    0.168340] CPU1 attaching sched-domain:
[    0.168343]  domain 0: span 0-1 level MC
[    0.168346]   groups: 1 0
[    0.168443] Switch to broadcast mode on CPU0
[    0.168443] devtmpfs: initialized
[    0.168443] regulator: core version 0.5
[    0.168443] Time:  2:00:06  Date: 08/17/10
[    0.168443] NET: Registered protocol family 16
[    0.168443] Trying to unpack rootfs image as initramfs...
[    0.168443] EISA bus registered
[    0.168443] ACPI: bus type pci registered
[    0.168443] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 7
[    0.168443] PCI: MCFG area at e0000000 reserved in E820
[    0.168443] PCI: Using MMCONFIG for extended config space
[    0.168443] PCI: Using configuration type 1 for base access
[    0.172138] bio: create slab <bio-0> at 0
[    0.173198] ACPI: EC: Look up EC in DSDT
[    0.175864] ACPI Warning: Package List length (0x1) larger than NumElements count (0x0), truncated
[    0.175872]  (20090903/dsobject-515)
[    0.175941] ACPI Warning: Package List length (0x1) larger than NumElements count (0x0), truncated
[    0.175948]  (20090903/dsobject-515)
[    0.196646] ACPI: Interpreter enabled
[    0.196657] ACPI: (supports S0 S3 S4 S5)
[    0.196680] ACPI: Using IOAPIC for interrupt routing
[    0.249489] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[    0.249729] ACPI: No dock devices found.
[    0.250807] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.250943] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    0.250948] pci 0000:00:04.0: PME# disabled
[    0.250990] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.250994] pci 0000:00:05.0: PME# disabled
[    0.251065] pci 0000:00:13.0: reg 10 32bit mmio: [0xc0004000-0xc0004fff]
[    0.251178] pci 0000:00:13.1: reg 10 32bit mmio: [0xc0005000-0xc0005fff]
[    0.251299] pci 0000:00:13.2: reg 10 32bit mmio: [0xc0006000-0xc0006fff]
[    0.251373] pci 0000:00:13.2: supports D1 D2
[    0.251376] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.251383] pci 0000:00:13.2: PME# disabled
[    0.251440] pci 0000:00:14.0: reg 10 io port: [0x8400-0x840f]
[    0.251450] pci 0000:00:14.0: reg 14 32bit mmio: [0xfed00000-0xfed003ff]
[    0.251489] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.251557] pci 0000:00:14.1: reg 10 io port: [0x8430-0x8437]
[    0.251567] pci 0000:00:14.1: reg 14 io port: [0x8424-0x8427]
[    0.251578] pci 0000:00:14.1: reg 18 io port: [0x8428-0x842f]
[    0.251588] pci 0000:00:14.1: reg 1c io port: [0x8420-0x8423]
[    0.251599] pci 0000:00:14.1: reg 20 io port: [0x8410-0x841f]
[    0.251702] pci 0000:00:14.2: reg 10 64bit mmio: [0xc0000000-0xc0003fff]
[    0.251769] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.251776] pci 0000:00:14.2: PME# disabled
[    0.252041] pci 0000:01:05.0: reg 10 32bit mmio pref: [0xc8000000-0xcfffffff]
[    0.252048] pci 0000:01:05.0: reg 14 io port: [0x9000-0x90ff]
[    0.252054] pci 0000:01:05.0: reg 18 32bit mmio: [0xc0100000-0xc010ffff]
[    0.252066] pci 0000:01:05.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.252077] pci 0000:01:05.0: supports D1 D2
[    0.252097] pci 0000:00:01.0: bridge io port: [0x9000-0x9fff]
[    0.252102] pci 0000:00:01.0: bridge 32bit mmio: [0xc0100000-0xc01fffff]
[    0.252108] pci 0000:00:01.0: bridge 64bit mmio pref: [0xc8000000-0xcfffffff]
[    0.252170] pci 0000:00:04.0: bridge io port: [0x00-0xfff]
[    0.252175] pci 0000:00:04.0: bridge 32bit mmio: [0x000000-0x0fffff]
[    0.252181] pci 0000:00:04.0: bridge 64bit mmio pref: [0x000000-0x0fffff]
[    0.252242] pci 0000:00:05.0: bridge io port: [0x00-0xfff]
[    0.252247] pci 0000:00:05.0: bridge 32bit mmio: [0x000000-0x0fffff]
[    0.252309] pci 0000:06:01.0: reg 10 io port: [0xa000-0xa0ff]
[    0.252321] pci 0000:06:01.0: reg 14 32bit mmio: [0xc0202000-0xc02020ff]
[    0.252394] pci 0000:06:01.0: supports D1 D2
[    0.252397] pci 0000:06:01.0: PME# supported from D1 D2 D3hot D3cold
[    0.252405] pci 0000:06:01.0: PME# disabled
[    0.252444] pci 0000:06:02.0: reg 10 32bit mmio: [0xc0200000-0xc0201fff]
[    0.252556] pci 0000:06:04.0: reg 10 32bit mmio: [0xc0203000-0xc0203fff]
[    0.252591] pci 0000:06:04.0: supports D1 D2
[    0.252594] pci 0000:06:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.252602] pci 0000:06:04.0: PME# disabled
[    0.252661] pci 0000:06:04.1: reg 10 32bit mmio: [0xc0202400-0xc020247f]
[    0.252744] pci 0000:06:04.1: supports D1 D2
[    0.252747] pci 0000:06:04.1: PME# supported from D0 D1 D2 D3hot
[    0.252755] pci 0000:06:04.1: PME# disabled
[    0.252813] pci 0000:06:04.2: reg 10 32bit mmio: [0xc0202800-0xc02028ff]
[    0.252897] pci 0000:06:04.2: supports D1 D2
[    0.252900] pci 0000:06:04.2: PME# supported from D0 D1 D2 D3hot
[    0.252908] pci 0000:06:04.2: PME# disabled
[    0.252966] pci 0000:06:04.3: reg 10 32bit mmio: [0xc0202c00-0xc0202c7f]
[    0.253049] pci 0000:06:04.3: supports D1 D2
[    0.253053] pci 0000:06:04.3: PME# supported from D0 D1 D2 D3hot
[    0.253060] pci 0000:06:04.3: PME# disabled
[    0.253119] pci 0000:06:04.4: reg 10 32bit mmio: [0x000000-0x0000ff]
[    0.253202] pci 0000:06:04.4: supports D1 D2
[    0.253205] pci 0000:06:04.4: PME# supported from D0 D1 D2 D3hot
[    0.253213] pci 0000:06:04.4: PME# disabled
[    0.253286] pci 0000:00:14.4: transparent bridge
[    0.253297] pci 0000:00:14.4: bridge io port: [0xa000-0xafff]
[    0.253304] pci 0000:00:14.4: bridge 32bit mmio: [0xc0200000-0xc02fffff]
[    0.253351] pci_bus 0000:00: on NUMA node 0
[    0.253356] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.253475] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[    0.253552] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]
[    0.253635] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BB4_._PRT]
[    0.253711] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BB5_._PRT]
[    0.253821] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.253936] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.260028] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[    0.260166] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[    0.260296] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[    0.260423] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[    0.260549] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[    0.260680] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[    0.260807] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[    0.260934] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[    0.261062] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 5 7) *0, disabled.
[    0.261199] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.261210] vgaarb: loaded
[    0.261345] SCSI subsystem initialized
[    0.261460] libata version 3.00 loaded.
[    0.261545] usbcore: registered new interface driver usbfs
[    0.261561] usbcore: registered new interface driver hub
[    0.261593] usbcore: registered new device driver usb
[    0.261836] ACPI: WMI: Mapper loaded
[    0.261839] PCI: Using ACPI for IRQ routing
[    0.261847] pci 0000:00:04.0: BAR 13: can't allocate resource
[    0.261851] pci 0000:00:04.0: BAR 14: can't allocate resource
[    0.261854] pci 0000:00:04.0: BAR 15: can't allocate resource
[    0.261858] pci 0000:00:05.0: BAR 13: can't allocate resource
[    0.261862] pci 0000:00:05.0: BAR 14: can't allocate resource
[    0.262085] NetLabel: Initializing
[    0.262088] NetLabel:  domain hash size = 128
[    0.262090] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.262107] NetLabel:  unlabeled traffic allowed by default
[    0.264350] AppArmor: AppArmor Filesystem Enabled
[    0.264370] pnp: PnP ACPI init
[    0.264388] ACPI: bus type pnp registered
[    0.267373] pnp 00:09: mem resource (0x0-0xfff) overlaps 0000:01:05.0 BAR 6 (0x0-0x1ffff), disabling
[    0.288206] pnp: PnP ACPI: found 10 devices
[    0.288209] ACPI: ACPI bus type pnp unregistered
[    0.288214] PnPBIOS: Disabled by ACPI PNP
[    0.288229] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    0.288235] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.288240] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.288252] system 00:08: ioport range 0x1080-0x1080 has been reserved
[    0.288257] system 00:08: ioport range 0x40b-0x40b has been reserved
[    0.288261] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.288266] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
[    0.288271] system 00:08: ioport range 0xc00-0xc01 has been reserved
[    0.288275] system 00:08: ioport range 0xc14-0xc14 has been reserved
[    0.288280] system 00:08: ioport range 0xc50-0xc52 has been reserved
[    0.288284] system 00:08: ioport range 0xc6c-0xc6c has been reserved
[    0.288289] system 00:08: ioport range 0xc6f-0xc6f has been reserved
[    0.288294] system 00:08: ioport range 0xcd4-0xcd5 has been reserved
[    0.288298] system 00:08: ioport range 0xcd6-0xcd7 has been reserved
[    0.288303] system 00:08: ioport range 0xcd8-0xcdf has been reserved
[    0.288308] system 00:08: ioport range 0x8000-0x805f has been reserved
[    0.288313] system 00:08: ioport range 0xf40-0xf47 has been reserved
[    0.288317] system 00:08: ioport range 0x280-0x293 has been reserved
[    0.288322] system 00:08: ioport range 0x87f-0x87f has been reserved
[    0.288330] system 00:09: iomem range 0xe0000-0xfffff could not be reserved
[    0.288336] system 00:09: iomem range 0xfff00000-0xffffffff could not be reserved
[    0.323059] Switching to clocksource acpi_pm
[    0.323193] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.323193] pci 0000:00:01.0:   IO window: 0x9000-0x9fff
[    0.323193] pci 0000:00:01.0:   MEM window: 0xc0100000-0xc01fffff
[    0.323193] pci 0000:00:01.0:   PREFETCH window: 0x000000c8000000-0x000000cfffffff
[    0.323193] pci 0000:00:04.0: PCI bridge, secondary bus 0000:02
[    0.323193] pci 0000:00:04.0:   IO window: disabled
[    0.323193] pci 0000:00:04.0:   MEM window: disabled
[    0.323193] pci 0000:00:04.0:   PREFETCH window: disabled
[    0.323193] pci 0000:00:05.0: PCI bridge, secondary bus 0000:04
[    0.323193] pci 0000:00:05.0:   IO window: disabled
[    0.323193] pci 0000:00:05.0:   MEM window: disabled
[    0.323193] pci 0000:00:05.0:   PREFETCH window: disabled
[    0.323193] pci 0000:06:04.0: CardBus bridge, secondary bus 0000:07
[    0.323193] pci 0000:06:04.0:   IO window: 0x00a400-0x00a4ff
[    0.323193] pci 0000:06:04.0:   IO window: 0x00a800-0x00a8ff
[    0.323193] pci 0000:06:04.0:   PREFETCH window: 0x80000000-0x83ffffff
[    0.323193] pci 0000:06:04.0:   MEM window: 0x84000000-0x87ffffff
[    0.323193] pci 0000:00:14.4: PCI bridge, secondary bus 0000:06
[    0.323193] pci 0000:00:14.4:   IO window: 0xa000-0xafff
[    0.323193] pci 0000:00:14.4:   MEM window: 0xc0200000-0xc02fffff
[    0.323193] pci 0000:00:14.4:   PREFETCH window: 0x80000000-0x83ffffff
[    0.323193] pci 0000:00:04.0: setting latency timer to 64
[    0.323193] pci 0000:00:05.0: setting latency timer to 64
[    0.323193]   alloc irq_desc for 20 on node -1
[    0.323193]   alloc kstat_irqs on node -1
[    0.323193] pci 0000:06:04.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.323193] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.323193] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.323193] pci_bus 0000:01: resource 0 io:  [0x9000-0x9fff]
[    0.323193] pci_bus 0000:01: resource 1 mem: [0xc0100000-0xc01fffff]
[    0.323193] pci_bus 0000:01: resource 2 pref mem [0xc8000000-0xcfffffff]
[    0.323193] pci_bus 0000:02: resource 0 mem: [0x0-0xfff]
[    0.323193] pci_bus 0000:02: resource 1 mem: [0x0-0xfffff]
[    0.323193] pci_bus 0000:02: resource 2 mem: [0x0-0xfffff]
[    0.323193] pci_bus 0000:04: resource 0 mem: [0x0-0xfff]
[    0.323193] pci_bus 0000:04: resource 1 mem: [0x0-0xfffff]
[    0.323193] pci_bus 0000:06: resource 0 io:  [0xa000-0xafff]
[    0.323193] pci_bus 0000:06: resource 1 mem: [0xc0200000-0xc02fffff]
[    0.323193] pci_bus 0000:06: resource 2 pref mem [0x80000000-0x83ffffff]
[    0.323193] pci_bus 0000:06: resource 3 io:  [0x00-0xffff]
[    0.323193] pci_bus 0000:06: resource 4 mem: [0x000000-0xffffffff]
[    0.323193] pci_bus 0000:07: resource 0 io:  [0xa400-0xa4ff]
[    0.323193] pci_bus 0000:07: resource 1 io:  [0xa800-0xa8ff]
[    0.323193] pci_bus 0000:07: resource 2 pref mem [0x80000000-0x83ffffff]
[    0.323193] pci_bus 0000:07: resource 3 mem: [0x84000000-0x87ffffff]
[    0.323193] NET: Registered protocol family 2
[    0.323193] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.323193] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.323193] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.323193] TCP: Hash tables configured (established 131072 bind 65536)
[    0.323193] TCP reno registered
[    0.323193] NET: Registered protocol family 1
[    0.323193] pci 0000:00:00.0: MSI quirk detected; MSI disabled
[    0.323193] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
[    0.323193] pci 0000:01:05.0: Boot video device
[    0.323193] cpufreq-nforce2: No nForce2 chipset.
[    0.323193] Scanning for low memory corruption every 60 seconds
[    0.323193] audit: initializing netlink socket (disabled)
[    0.323193] type=2000 audit(1282010405.320:1): initialized
[    0.335956] highmem bounce pool size: 64 pages
[    0.335963] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.337900] VFS: Disk quotas dquot_6.5.2
[    0.337974] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.338694] fuse init (API version 7.13)
[    0.338798] msgmni has been set to 1693
[    0.339083] alg: No test for stdrng (krng)
[    0.339152] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.339157] io scheduler noop registered
[    0.339160] io scheduler anticipatory registered
[    0.339162] io scheduler deadline registered
[    0.339211] io scheduler cfq registered (default)
[    0.339379] pcieport 0000:00:04.0: setting latency timer to 64
[    0.339445] pcieport 0000:00:05.0: setting latency timer to 64
[    0.339493] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.339521] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.341539] ACPI: AC Adapter [ACAD] (on-line)
[    0.341615] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.341679] ACPI: Lid Switch [LID]
[    0.341733] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.341738] ACPI: Power Button [PWRB]
[    0.341792] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.341796] ACPI: Sleep Button [SLPB]
[    0.341868] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.341873] ACPI: Power Button [PWRF]
[    0.342153] ACPI: processor limited to max C-state 1
[    0.342185] processor LNXCPU:00: registered as cooling_device0
[    0.342224] processor LNXCPU:01: registered as cooling_device1
[    0.382753] ACPI: Invalid active0 threshold
[    0.388886] thermal LNXTHERM:01: registered as thermal_zone0
[    0.388896] ACPI: Thermal Zone [THRM] (59 C)
[    0.390765] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.392429] brd: module loaded
[    0.393036] loop: module loaded
[    0.393165] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.393352]   alloc irq_desc for 16 on node -1
[    0.393356]   alloc kstat_irqs on node -1
[    0.393364] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.393414] pata_acpi 0000:00:14.1: setting latency timer to 64
[    0.393808] Fixed MDIO Bus: probed
[    0.393851] PPP generic driver version 2.4.2
[    0.393904] tun: Universal TUN/TAP device driver, 1.6
[    0.393907] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.394012] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.394034]   alloc irq_desc for 19 on node -1
[    0.394037]   alloc kstat_irqs on node -1
[    0.394044] ehci_hcd 0000:00:13.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.394065] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    0.394106] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
[    0.394174] ehci_hcd 0000:00:13.2: irq 19, io mem 0xc0006000
[    0.394418] isapnp: Scanning for PnP cards...
[    0.434588] Freeing initrd memory: 7776k freed
[    0.443639] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    0.443763] usb usb1: configuration #1 chosen from 1 choice
[    0.443803] hub 1-0:1.0: USB hub found
[    0.443814] hub 1-0:1.0: 8 ports detected
[    0.443923] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.443944] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.443964] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    0.444032] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    0.444054] ohci_hcd 0000:00:13.0: irq 19, io mem 0xc0004000
[    0.497235] usb usb2: configuration #1 chosen from 1 choice
[    0.497273] hub 2-0:1.0: USB hub found
[    0.497289] hub 2-0:1.0: 4 ports detected
[    0.497394] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.497417] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    0.497464] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    0.497489] ohci_hcd 0000:00:13.1: irq 19, io mem 0xc0005000
[    0.553157] usb usb3: configuration #1 chosen from 1 choice
[    0.553189] hub 3-0:1.0: USB hub found
[    0.553204] hub 3-0:1.0: 4 ports detected
[    0.553281] uhci_hcd: USB Universal Host Controller Interface driver
[    0.553377] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSS0] at 0x60,0x64 irq 1,12
[    0.553736] i8042.c: Detected active multiplexing controller, rev 1.1.
[    0.553824] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.553835] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.553839] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.553844] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.553849] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.553947] mice: PS/2 mouse device common for all mice
[    0.554110] rtc_cmos 00:04: RTC can wake from S4
[    0.554155] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.554185] rtc0: alarms up to one month, 114 bytes nvram
[    0.554312] device-mapper: uevent: version 1.0.3
[    0.554499] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.554583] device-mapper: multipath: version 1.1.0 loaded
[    0.554587] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.554733] EISA: Probing bus 0 at eisa.0
[    0.554755] Cannot allocate resource for EISA slot 1
[    0.554787] Cannot allocate resource for EISA slot 8
[    0.554790] EISA: Detected 0 cards.
[    0.554897] cpuidle: using governor ladder
[    0.554900] cpuidle: using governor menu
[    0.555500] TCP cubic registered
[    0.555690] NET: Registered protocol family 10
[    0.556250] lo: Disabled Privacy Extensions
[    0.556657] NET: Registered protocol family 17
[    0.556700] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-50 processors (2 cpu cores) (version 2.20.00)
[    0.556741] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x13
[    0.556745] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x1e
[    0.558756] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    0.575318] Using IPI No-Shortcut mode
[    0.575422] PM: Resume from disk failed.
[    0.575437] registered taskstats version 1
[    0.575859]   Magic number: 6:459:5
[    0.575958] rtc_cmos 00:04: setting system clock to 2010-08-17 02:00:06 UTC (1282010406)
[    0.575964] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.575967] EDD information not available.
[    0.749558] isapnp: No Plug & Play device found
[    0.749586] Freeing unused kernel memory: 660k freed
[    0.750142] Write protecting the kernel text: 4680k
[    0.750193] Write protecting the kernel read-only data: 1840k
[    0.775175] udev: starting version 151
[    0.783182] ACPI: Battery Slot [BAT1] (battery present)
[    0.930582] scsi0 : pata_atiixp
[    0.936183] scsi1 : pata_atiixp
[    0.937220] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8410 irq 14
[    0.937225] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8418 irq 15
[    0.938330] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    0.938364] 8139cp 0000:06:01.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    0.944991]   alloc irq_desc for 22 on node -1
[    0.944995]   alloc kstat_irqs on node -1
[    0.945027] b43-pci-bridge 0000:06:02.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.004126] ssb: Sonics Silicon Backplane found on PCI device 0000:06:02.0
[    1.110475] ata1.00: ATA-8: SAMSUNG HM160HC, LQ100-10, max UDMA/100
[    1.110480] ata1.00: 312581808 sectors, multi 16: LBA48 
[    1.110520] ata1.01: ATAPI: PHILIPS DVD-RAM SDVD8821, EY01, max UDMA/33
[    1.126424] ata1.00: configured for UDMA/100
[    1.140587] ata1.01: configured for UDMA/33
[    1.141372] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HM160HC  LQ10 PQ: 0 ANSI: 5
[    1.141578] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.141625] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.142330] sd 0:0:0:0: [sda] Write Protect is off
[    1.142335] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.142982] scsi 0:0:1:0: CD-ROM            PHILIPS  DVD-RAM SDVD8821 EY01 PQ: 0 ANSI: 5
[    1.142989] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.156665] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.156670] Uniform CD-ROM driver Revision: 3.20
[    1.156689]  sda:
[    1.156833] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    1.156914] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    1.205741]  sda1 sda2 < sda5 >
[    1.230984] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.244052] usb 2-1: new low speed USB device using ohci_hcd and address 2
[    1.316581] 8139too Fast Ethernet driver 0.9.28
[    1.316684]   alloc irq_desc for 21 on node -1
[    1.316687]   alloc kstat_irqs on node -1
[    1.316697] 8139too 0000:06:01.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.318478] eth0: RealTek RTL8139 at 0xa000, 00:16:d4:19:b2:ca, IRQ 21
[    1.424063] usb 2-1: device descriptor read/64, error -62
[    1.592548] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    1.708059] usb 2-1: device descriptor read/64, error -62
[    1.988069] usb 2-1: new low speed USB device using ohci_hcd and address 3
[    2.168056] usb 2-1: device descriptor read/64, error -62
[    2.452061] usb 2-1: device descriptor read/64, error -62
[    2.732076] usb 2-1: new low speed USB device using ohci_hcd and address 4
[    3.140068] usb 2-1: device not accepting address 4, error -62
[    3.316086] usb 2-1: new low speed USB device using ohci_hcd and address 5
[    3.724062] usb 2-1: device not accepting address 5, error -62
[    3.724081] hub 2-0:1.0: unable to enumerate USB device on port 1
[   26.055067] udev: starting version 151
[   26.157158] Adding 5653496k swap on /dev/sda5.  Priority:-1 extents:1 across:5653496k 
[   26.423211] lp: driver loaded but no devices found
[   26.535489] acer-wmi: Acer Laptop ACPI-WMI Extras
[   26.542484] Registered led device: acer-wmi::mail
[   26.571764] type=1505 audit(1282010432.492:2):  operation="profile_load" pid=501 name="/sbin/dhclient3"
[   26.572145] type=1505 audit(1282010432.496:3):  operation="profile_load" pid=501 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   26.572343] type=1505 audit(1282010432.496:4):  operation="profile_load" pid=501 name="/usr/lib/connman/scripts/dhclient-script"
[   26.738276] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:1f/LNXVIDEO:00/input/input6
[   26.738452] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   26.891400] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   26.905359] Linux agpgart interface v0.103
[   26.943955] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   27.054491] [drm] Initialized drm 1.1.0 20060810
[   27.147752] cfg80211: Calling CRDA to update world regulatory domain
[   27.199996] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x12a0b1, caps: 0xa04713/0x204000
[   27.229190] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
[   57.804114] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   57.804161] ata1.00: failed command: READ DMA
[   57.804206] ata1.00: cmd c8/00:08:80:08:80/00:00:00:00:00/e2 tag 0 dma 4096 in
[   57.804208]          res 40/00:fe:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)
[   57.804291] ata1.00: status: { DRDY }
[   62.844061] ata1: link is slow to respond, please be patient (ready=0)
[   67.828051] ata1: device not ready (errno=-16), forcing hardreset
[   67.828064] ata1: soft resetting link
[   68.018499] ata1.00: configured for UDMA/100
[   68.032586] ata1.01: configured for UDMA/33
[   68.033222] ata1.00: device reported invalid CHS sector 0
[   68.033234] ata1: EH complete
[   68.044818] cfg80211: World regulatory domain updated:
[   68.044823] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   68.044828] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   68.044832] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   68.044836] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   68.044839] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   68.044843] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   68.090266] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x8400, revision 0
[   68.101456] sdhci: Secure Digital Host Controller Interface driver
[   68.101460] sdhci: Copyright(c) Pierre Ossman
[   68.273386] sdhci-pci 0000:06:04.2: SDHCI controller found [1524:0550] (rev 1)
[   68.273412]   alloc irq_desc for 23 on node -1
[   68.273416]   alloc kstat_irqs on node -1
[   68.273424] sdhci-pci 0000:06:04.2: PCI INT B -> GSI 23 (level, low) -> IRQ 23
[   68.275060] Registered led device: mmc0::
[   68.275214] mmc0: SDHCI controller on PCI [0000:06:04.2] using PIO
[   68.275236] sdhci-pci 0000:06:04.4: SDHCI controller found [1524:0551] (rev 1)
[   68.275255] sdhci-pci 0000:06:04.4: enabling device (0000 -> 0002)
[   68.275266] sdhci-pci 0000:06:04.4: PCI INT B -> GSI 23 (level, low) -> IRQ 23
[   68.276998] Registered led device: mmc1::
[   68.277959] mmc1: SDHCI controller on PCI [0000:06:04.4] using PIO
[   68.287362] yenta_cardbus 0000:06:04.0: CardBus bridge found [1025:009f]
[   68.287395] yenta_cardbus 0000:06:04.0: Using CSCINT to route CSC interrupts to PCI
[   68.287399] yenta_cardbus 0000:06:04.0: Routing CardBus interrupts to PCI
[   68.287407] yenta_cardbus 0000:06:04.0: TI: mfunc 0x90501212, devctl 0x44
[   68.462440] [drm] radeon defaulting to kernel modesetting.
[   68.462445] [drm] radeon kernel modesetting enabled.
[   68.462535] radeon 0000:01:05.0: power state changed by ACPI to D0
[   68.462544] radeon 0000:01:05.0: power state changed by ACPI to D0
[   68.462554]   alloc irq_desc for 17 on node -1
[   68.462557]   alloc kstat_irqs on node -1
[   68.462565] radeon 0000:01:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   68.464689] [drm] radeon: Initializing kernel modesetting.
[   68.464922] [drm] register mmio base: 0xC0100000
[   68.464926] [drm] register mmio size: 65536
[   68.465286] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
[   68.465311] [drm:rs400_gart_adjust_size] *ERROR* Forcing to 32M GART size (because of ASIC bug ?)
[   68.465359] [drm] Generation 2 PCI interface, using max accessible memory
[   68.465363] [drm] radeon: VRAM 128M
[   68.465366] [drm] radeon: VRAM from 0x78000000 to 0x7FFFFFFF
[   68.465369] [drm] radeon: GTT 32M
[   68.465372] [drm] radeon: GTT from 0x80000000 to 0x81FFFFFF
[   68.465411] [drm] radeon: irq initialized.
[   68.465560] [drm] Detected VRAM RAM=128M, BAR=128M
[   68.465566] [drm] RAM width 128bits DDR
[   68.465705] [TTM] Zone  kernel: Available graphics memory: 437774 kiB.
[   68.465710] [TTM] Zone highmem: Available graphics memory: 965426 kiB.
[   68.465732] [drm] radeon: 128M of VRAM memory ready
[   68.465735] [drm] radeon: 32M of GTT memory ready.
[   68.465756] [drm] GART: num cpu pages 8192, num gpu pages 8192
[   68.466243] [drm] radeon: 1 quad pipes, 1 z pipes initialized.
[   68.466260] [drm] radeon: cp idle (0x10000C03)
[   68.466314] [drm] Loading R300 Microcode
[   68.466320] platform radeon_cp.0: firmware: requesting radeon/R300_cp.bin
[   68.520851] yenta_cardbus 0000:06:04.0: ISA IRQ mask 0x0cf8, PCI irq 20
[   68.520858] yenta_cardbus 0000:06:04.0: Socket status: 30000006
[   68.520867] yenta_cardbus 0000:06:04.0: pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[   68.520872] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa000-0xafff: clean.
[   68.521103] yenta_cardbus 0000:06:04.0: pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xc02fffff
[   68.521108] yenta_cardbus 0000:06:04.0: pcmcia: parent PCI bridge Memory window: 0x80000000 - 0x83ffffff
[   68.616039] eth0: link down
[   68.616375] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   68.626140] type=1505 audit(1282010474.548:5):  operation="profile_load" pid=735 name="/usr/share/gdm/guest-session/Xsession"
[   68.628368] type=1505 audit(1282010474.552:6):  operation="profile_replace" pid=736 name="/sbin/dhclient3"
[   68.628740] type=1505 audit(1282010474.552:7):  operation="profile_replace" pid=736 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   68.628948] type=1505 audit(1282010474.552:8):  operation="profile_replace" pid=736 name="/usr/lib/connman/scripts/dhclient-script"
[   68.633573] type=1505 audit(1282010474.556:9):  operation="profile_load" pid=737 name="/usr/bin/evince"
[   68.638188] type=1505 audit(1282010474.560:10):  operation="profile_load" pid=737 name="/usr/bin/evince-previewer"
[   68.641163] type=1505 audit(1282010474.564:11):  operation="profile_load" pid=737 name="/usr/bin/evince-thumbnailer"
[   68.644230] [drm] radeon: ring at 0x0000000080000000
[   68.644250] [drm] ring test succeeded in 1 usecs
[   68.644419] [drm] radeon: ib pool ready.
[   68.644499] [drm] ib test succeeded in 0 usecs
[   68.644543] [drm] Default TV standard: NTSC
[   68.644545] [drm] 14.318180000 MHz TV ref clk
[   68.644632] [drm] Panel ID String: AUO                     
[   68.644635] [drm] Panel Size 1280x800
[   68.644697] [drm] Radeon Display Connectors
[   68.644699] [drm] Connector 0:
[   68.644701] [drm]   VGA
[   68.644705] [drm]   DDC: 0x68 0x68 0x68 0x68 0x68 0x68 0x68 0x68
[   68.644707] [drm]   Encoders:
[   68.644709] [drm]     CRT1: INTERNAL_DAC2
[   68.644712] [drm] Connector 1:
[   68.644713] [drm]   LVDS
[   68.644717] [drm]   DDC: 0x198 0x198 0x19c 0x19c 0x1a0 0x1a0 0x1a4 0x1a4
[   68.644719] [drm]   Encoders:
[   68.644721] [drm]     LCD1: INTERNAL_LVDS
[   68.653672] type=1505 audit(1282010474.576:12):  operation="profile_load" pid=743 name="/usr/lib/cups/backend/cups-pdf"
[   68.654125] type=1505 audit(1282010474.576:13):  operation="profile_load" pid=743 name="/usr/sbin/cupsd"
[   68.656710] type=1505 audit(1282010474.580:14):  operation="profile_load" pid=744 name="/usr/sbin/tcpdump"
[   68.777587] [drm] fb mappable at 0xC8040000
[   68.777591] [drm] vram apper at 0xC8000000
[   68.777593] [drm] size 4096000
[   68.777596] [drm] fb depth is 24
[   68.777598] [drm]    pitch is 5120
[   68.777779] fb0: radeondrmfb frame buffer device
[   68.777782] registered panic notifier
[   68.777788] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:05.0 on minor 0
[   68.859412] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   68.943335] vga16fb: initializing
[   68.943342] vga16fb: mapped to 0xc00a0000
[   68.943348] vga16fb: not registering due to another framebuffer present
[   69.154999] Console: switching to colour frame buffer device 160x50
[   69.175988] phy0: Selected rate control algorithm 'minstrel'
[   69.177024] Registered led device: b43-phy0::tx
[   69.177051] Registered led device: b43-phy0::rx
[   69.177074] Registered led device: b43-phy0::radio
[   69.177163] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
[   69.218200] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   69.220561] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   69.221612] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   69.222422] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   69.223317] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   69.229101] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   69.235124] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   69.240448] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   69.244209] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   69.373111] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   69.465994] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   69.647442] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   69.786144] hda_codec: ALC883: BIOS auto-probing.
[   69.788141] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input8
[   72.721050] usb 2-1: new low speed USB device using ohci_hcd and address 6
[   72.905070] usb 2-1: device descriptor read/64, error -62
[   73.189187] usb 2-1: device descriptor read/64, error -62
[   73.469051] usb 2-1: new low speed USB device using ohci_hcd and address 7
[   73.649059] usb 2-1: device descriptor read/64, error -62
[   73.933056] usb 2-1: device descriptor read/64, error -62
[   74.213046] usb 2-1: new low speed USB device using ohci_hcd and address 8
[   74.621042] usb 2-1: device not accepting address 8, error -62
[   74.797058] usb 2-1: new low speed USB device using ohci_hcd and address 9
[   75.037713] ppdev: user-space parallel port driver
[   75.206047] usb 2-1: device not accepting address 9, error -62
[   75.206106] hub 2-0:1.0: unable to enumerate USB device on port 1
[  137.169031] Clocksource tsc unstable (delta = -107445321 ns)
[  231.990238] wlan0: deauthenticating from 00:27:19:dc:b7:04 by local choice (reason=3)
[  231.990416] wlan0: direct probe to AP 00:27:19:dc:b7:04 (try 1)
[  231.998675] wlan0: direct probe responded
[  231.998689] wlan0: authenticate with AP 00:27:19:dc:b7:04 (try 1)
[  232.000285] wlan0: authenticated
[  232.000342] wlan0: associate with AP 00:27:19:dc:b7:04 (try 1)
[  232.003909] wlan0: RX AssocResp from 00:27:19:dc:b7:04 (capab=0x431 status=0 aid=2)
[  232.003920] wlan0: associated
[  232.008451] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  233.087866] padlock: VIA PadLock not detected.
[  240.876098] usb 2-3: new low speed USB device using ohci_hcd and address 10
[  241.056157] usb 2-3: device descriptor read/64, error -62
[  241.340086] usb 2-3: device descriptor read/64, error -62
[  241.620091] usb 2-3: new low speed USB device using ohci_hcd and address 11
[  241.800088] usb 2-3: device descriptor read/64, error -62
[  242.084106] usb 2-3: device descriptor read/64, error -62
[  242.364127] usb 2-3: new low speed USB device using ohci_hcd and address 12
[  242.600051] wlan0: no IPv6 routers present
[  242.772085] usb 2-3: device not accepting address 12, error -62
[  242.948093] usb 2-3: new low speed USB device using ohci_hcd and address 13
[  243.356078] usb 2-3: device not accepting address 13, error -62
[  243.356117] hub 2-0:1.0: unable to enumerate USB device on port 3
[  257.225935] dropbox[1162]: segfault at 0 ip 00469dc9 sp bffa1764 error 4 in libpango-1.0.so.0.2800.0[459000+40000]
[  650.984090] usb 2-1: new low speed USB device using ohci_hcd and address 14
[  651.148096] usb 2-1: device descriptor read/64, error -62
[  651.432122] usb 2-1: device descriptor read/64, error -62
[  651.712098] usb 2-1: new low speed USB device using ohci_hcd and address 15
[  651.892110] usb 2-1: device descriptor read/64, error -62
[  652.160120] usb 2-1: device descriptor read/64, error -62
[  652.440097] usb 2-1: new low speed USB device using ohci_hcd and address 16
[  652.848110] usb 2-1: device not accepting address 16, error -62
[  653.024109] usb 2-1: new low speed USB device using ohci_hcd and address 17
[  653.432101] usb 2-1: device not accepting address 17, error -62
[  653.432181] hub 2-0:1.0: unable to enumerate USB device on port 1
[  663.432107] usb 1-5: new high speed USB device using ehci_hcd and address 5
[  663.538260] ehci_hcd 0000:00:13.2: port 5 reset error -110
[  663.538277] hub 1-0:1.0: hub_port_status failed (err = -32)
[  663.742267] ehci_hcd 0000:00:13.2: port 5 reset error -110
[  663.742285] hub 1-0:1.0: hub_port_status failed (err = -32)
[  663.946267] ehci_hcd 0000:00:13.2: port 5 reset error -110
[  663.946285] hub 1-0:1.0: hub_port_status failed (err = -32)
[  664.150270] ehci_hcd 0000:00:13.2: port 5 reset error -110
[  664.150287] hub 1-0:1.0: hub_port_status failed (err = -32)
[  664.354266] ehci_hcd 0000:00:13.2: port 5 reset error -110
[  664.354284] hub 1-0:1.0: hub_port_status failed (err = -32)
[  664.354291] hub 1-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[  664.410278] ehci_hcd 0000:00:13.2: port 5 reset error -110
[  664.410295] hub 1-0:1.0: hub_port_status failed (err = -32)
[  664.614269] ehci_hcd 0000:00:13.2: port 5 reset error -110
[  664.614286] hub 1-0:1.0: hub_port_status failed (err = -32)
[  664.818269] ehci_hcd 0000:00:13.2: port 5 reset error -110
[  664.818303] hub 1-0:1.0: hub_port_status failed (err = -32)
[  665.022258] ehci_hcd 0000:00:13.2: port 5 reset error -110
[  665.022275] hub 1-0:1.0: hub_port_status failed (err = -32)
[  665.226252] ehci_hcd 0000:00:13.2: port 5 reset error -110
[  665.226269] hub 1-0:1.0: hub_port_status failed (err = -32)
[  665.226277] hub 1-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[  665.282260] ehci_hcd 0000:00:13.2: port 5 reset error -110
[  665.282278] hub 1-0:1.0: hub_port_status failed (err = -32)
[  665.486295] ehci_hcd 0000:00:13.2: port 5 reset error -110
[  665.486313] hub 1-0:1.0: hub_port_status failed (err = -32)
[  665.690272] ehci_hcd 0000:00:13.2: port 5 reset error -110
[  665.690290] hub 1-0:1.0: hub_port_status failed (err = -32)
[  665.894276] ehci_hcd 0000:00:13.2: port 5 reset error -110
[  665.894295] hub 1-0:1.0: hub_port_status failed (err = -32)
[  666.098263] ehci_hcd 0000:00:13.2: port 5 reset error -110
[  666.098280] hub 1-0:1.0: hub_port_status failed (err = -32)
[  666.098287] hub 1-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[  666.154296] ehci_hcd 0000:00:13.2: port 5 reset error -110
[  666.154308] hub 1-0:1.0: hub_port_status failed (err = -32)
[  666.358283] ehci_hcd 0000:00:13.2: port 5 reset error -110
[  666.358299] hub 1-0:1.0: hub_port_status failed (err = -32)
[  666.562294] ehci_hcd 0000:00:13.2: port 5 reset error -110
[  666.562311] hub 1-0:1.0: hub_port_status failed (err = -32)
[  666.766290] ehci_hcd 0000:00:13.2: port 5 reset error -110
[  666.766307] hub 1-0:1.0: hub_port_status failed (err = -32)
[  666.970295] ehci_hcd 0000:00:13.2: port 5 reset error -110
[  666.970312] hub 1-0:1.0: hub_port_status failed (err = -32)
[  666.970319] hub 1-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[  666.970346] hub 1-0:1.0: unable to enumerate USB device on port 5
[  974.112090] usb 2-1: new low speed USB device using ohci_hcd and address 18
[  974.292106] usb 2-1: device descriptor read/64, error -62
[  974.576090] usb 2-1: device descriptor read/64, error -62
[  974.856095] usb 2-1: new low speed USB device using ohci_hcd and address 19
[  975.040320] usb 2-1: device descriptor read/64, error -62
[  975.320086] usb 2-1: device descriptor read/64, error -62
[  975.600108] usb 2-1: new low speed USB device using ohci_hcd and address 20
[  976.008076] usb 2-1: device not accepting address 20, error -62
[  976.184096] usb 2-1: new low speed USB device using ohci_hcd and address 21
[  976.592097] usb 2-1: device not accepting address 21, error -62
[  976.592181] hub 2-0:1.0: unable to enumerate USB device on port 1
[  976.646275] ehci_hcd 0000:00:13.2: port 5 reset error -110
[  976.646289] hub 1-0:1.0: hub_port_status failed (err = -32)

```

The last thing I tried was to install a newer version of the kernel to rule that it was a bug in the same but neither worked.

When i ran the command uname-a i get the following:

```

Linux matrix 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 i686 GNU/Linux

```

If anyone has any idea what could be happening would appreciate it a lot because I want to avoid having to reformat the computer since I'm currently working on a project and do not want to have to reinstall everything.

Regards

---

