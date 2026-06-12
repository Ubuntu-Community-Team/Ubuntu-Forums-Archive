---
title: "ExpressCard GigE doesn't detect when hotplugged"
date: 2009-09-25
forum: Hardware
---

### Post by SJrX on 2009-09-25
When I boot my machine up with a [http://catalog.belkin.com/IWCatProductPage.process?Product_Id=277569](http://catalog.belkin.com/IWCatProductPage.process?Product_Id=277569) in it, it works fine. However if the card is not inserted before my system boots I can't seem to get it working. It uses the sky2 module, and yes I've tried loading that module manually, but no luck. sky2 doesn't seem to depend on any other modules. I also don't have any other express cards to check with. 

Finally it seems that I can in fact Suspend to Disk and back and the card will still work, so long as it's inserted before I boot up, otherwise there is simply a ghost eth1, and when I unload and reload the sky2 module, it's gone.

I didn't see anything in dmesg or message when I try to insert it at all:

[html]<pre>
dmesg:
 EBDA/lowmem at: 0009f000/0009f000
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-15-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 (Ubuntu 2.6.28-15.49-generic)
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
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bfe93400 (usable)
[    0.000000]  BIOS-e820: 00000000bfe93400 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4007000 (reserved)
[    0.000000]  BIOS-e820: 00000000f4008000 - 00000000f400c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0xbfe93 max_arch_pfn = 0x100000
[    0.000000] Scanning 2 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)
[    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000092000 (usable)
[    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bfe93400 (usable)
[    0.000000]  modified: 00000000bfe93400 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000f0000000 - 00000000f4007000 (reserved)
[    0.000000]  modified: 00000000f4008000 - 00000000f400c000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed20000 - 00000000feda0000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  modified: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.000000] RAMDISK: 37875000 - 37fefbf9
[    0.000000] Allocated new RAMDISK: 0087d000 - 00ff7bf9
[    0.000000] Move RAMDISK from 0000000037875000 - 0000000037fefbf8 to 0087d000 - 00ff7bf8
[    0.000000] ACPI: RSDP 000FC1D0, 0014 (r0 DELL  )
[    0.000000] ACPI: RSDT BFE93A0F, 0040 (r1 DELL    M07     27D70402 ASL        61)
[    0.000000] ACPI: FACP BFE94800, 0074 (r1 DELL    M07     27D70402 ASL        61)
[    0.000000] ACPI: DSDT BFE95400, 4766 (r1 INT430 SYSFexxx     1001 INTL 20050624)
[    0.000000] ACPI: FACS BFEA3C00, 0040
[    0.000000] ACPI: HPET BFE94F00, 0038 (r1 DELL    M07            1 ASL        61)
[    0.000000] ACPI: APIC BFE95000, 0068 (r1 DELL    M07     27D70402 ASL        47)
[    0.000000] ACPI: MCFG BFE94FC0, 003E (r16 DELL    M07     27D70402 ASL        61)
[    0.000000] ACPI: SLIC BFE9509C, 0176 (r1 DELL    M07     27D70402 ASL        61)
[    0.000000] ACPI: BOOT BFE94BC0, 0028 (r1 DELL    M07     27D70402 ASL        61)
[    0.000000] ACPI: SSDT BFE93A4F, 04DC (r1  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2186MB HIGHMEM available.
[    0.000000] 883MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 373fe000
[    0.000000]   low ram: 00000000 - 373fe000
[    0.000000]   bootmap 00012000 - 00018e80
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008780ac]    TEXT DATA BSS ==> [0000100000 - 00008780ac]
[    0.000000]   #4 [0000879000 - 000087d000]    INIT_PG_TABLE ==> [0000879000 - 000087d000]
[    0.000000]   #5 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [000087d000 - 0000ff7bf9]      NEW RAMDISK ==> [000087d000 - 0000ff7bf9]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x000bfe93
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x00000007
[    0.000000]     0: 0x00000010 -> 0x00000092
[    0.000000]     0: 0x00000100 -> 0x000bfe93
[    0.000000] On node 0 totalpages: 785944
[    0.000000] free_area_init_node: node 0, pgdat c06cb500, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3941 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4374 pages used for memmap
[    0.000000]   HighMem zone: 555391 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
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
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 0000000000092000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c4000000 (gap: c0000000:30000000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 779802
[    0.000000] Kernel command line: root=UUID=2812c64b-6b3f-4f58-bafb-59310733deeb ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1830.737 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 15721340 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 3086592k/3144268k available (4115k kernel code, 56240k reserved, 2199k data, 532k init, 2239060k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0733000 - 0xc07b8000   ( 532 kB)
[    0.004000]       .data : 0xc0504f5f - 0xc072ae60   (2199 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0504f5f   (4115 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3661.47 BogoMIPS (lpj=7322948)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] Initializing cgroup subsys freezer
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.018573] ACPI: Core revision 20080926
[    0.020409] ACPI: Checking initramfs for custom DSDT
[    0.352343] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.392270] CPU0: Intel(R) Core(TM)2 CPU         T5600  @ 1.83GHz stepping 06
[    0.396001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3661.75 BogoMIPS (lpj=7323514)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.480475] CPU1: Intel(R) Core(TM)2 CPU         T5600  @ 1.83GHz stepping 06
[    0.480491] checking TSC synchronization [CPU#0 -> CPU#1]:
[    0.484001] Measured 3887629977 cycles TSC warp between CPUs, turning off TSC clock.
[    0.484001] Marking TSC unstable due to check_tsc_sync_source failed
[    0.484046] Brought up 2 CPUs
[    0.484050] Total of 2 processors activated (7323.23 BogoMIPS).
[    0.484106] CPU0 attaching sched-domain:
[    0.484109]  domain 0: span 0-1 level MC
[    0.484111]   groups: 0 1
[    0.484118] CPU1 attaching sched-domain:
[    0.484121]  domain 0: span 0-1 level MC
[    0.484123]   groups: 1 0
[    0.484197] net_namespace: 776 bytes
[    0.484197] Booting paravirtualized kernel on bare hardware
[    0.484350] Time: 16:41:57  Date: 09/25/09
[    0.484350] regulator: core version 0.5
[    0.484350] NET: Registered protocol family 16
[    0.484350] EISA bus registered
[    0.484350] ACPI: bus type pci registered
[    0.484350] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
[    0.484350] PCI: MCFG area at f0000000 reserved in E820
[    0.484350] PCI: Using MMCONFIG for extended config space
[    0.484350] PCI: Using configuration type 1 for base access
[    0.485224] ACPI: EC: Look up EC in DSDT
[    0.502998] ACPI: Interpreter enabled
[    0.503003] ACPI: (supports S0 S3 S4 S5)
[    0.503011] ACPI: Using IOAPIC for interrupt routing
[    0.533080] ACPI: No dock devices found.
[    0.533092] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.533195] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.533199] pci 0000:00:01.0: PME# disabled
[    0.533294] pci 0000:00:1b.0: reg 10 64bit mmio: [0xefffc000-0xefffffff]
[    0.533337] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.533342] pci 0000:00:1b.0: PME# disabled
[    0.533412] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.533417] pci 0000:00:1c.0: PME# disabled
[    0.533490] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.533495] pci 0000:00:1c.1: PME# disabled
[    0.533569] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.533574] pci 0000:00:1c.3: PME# disabled
[    0.533641] pci 0000:00:1d.0: reg 20 io port: [0xbf80-0xbf9f]
[    0.533706] pci 0000:00:1d.1: reg 20 io port: [0xbf60-0xbf7f]
[    0.533771] pci 0000:00:1d.2: reg 20 io port: [0xbf40-0xbf5f]
[    0.533836] pci 0000:00:1d.3: reg 20 io port: [0xbf20-0xbf3f]
[    0.533906] pci 0000:00:1d.7: reg 10 32bit mmio: [0xffa80000-0xffa803ff]
[    0.533955] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.533961] pci 0000:00:1d.7: PME# disabled
[    0.534127] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.534132] pci 0000:00:1f.0: quirk: region 1080-10bf claimed by ICH6 GPIO
[    0.534185] pci 0000:00:1f.2: reg 10 io port: [0x1f0-0x1f7]
[    0.534194] pci 0000:00:1f.2: reg 14 io port: [0x3f4-0x3f7]
[    0.534202] pci 0000:00:1f.2: reg 18 io port: [0x170-0x177]
[    0.534210] pci 0000:00:1f.2: reg 1c io port: [0x374-0x377]
[    0.534218] pci 0000:00:1f.2: reg 20 io port: [0xbfa0-0xbfaf]
[    0.534244] pci 0000:00:1f.2: PME# supported from D3hot
[    0.534249] pci 0000:00:1f.2: PME# disabled
[    0.534314] pci 0000:00:1f.3: reg 20 io port: [0x10c0-0x10df]
[    0.534378] pci 0000:01:00.0: reg 10 32bit mmio: [0xed000000-0xedffffff]
[    0.534388] pci 0000:01:00.0: reg 14 64bit mmio: [0xd0000000-0xdfffffff]
[    0.534399] pci 0000:01:00.0: reg 1c 64bit mmio: [0xee000000-0xeeffffff]
[    0.534409] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.534479] pci 0000:00:01.0: bridge 32bit mmio: [0xed000000-0xefefffff]
[    0.534485] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.534741] pci 0000:0c:00.0: reg 10 32bit mmio: [0xecfff000-0xecffffff]
[    0.534907] pci 0000:0c:00.0: PME# supported from D0 D3hot D3cold
[    0.534920] pci 0000:0c:00.0: PME# disabled
[    0.535031] pci 0000:00:1c.1: bridge 32bit mmio: [0xecf00000-0xecffffff]
[    0.535133] pci 0000:0d:00.0: reg 10 64bit mmio: [0xecdfc000-0xecdfffff]
[    0.535146] pci 0000:0d:00.0: reg 18 io port: [0xee00-0xeeff]
[    0.535189] pci 0000:0d:00.0: reg 30 32bit mmio: [0xece00000-0xece1ffff]
[    0.535207] pci 0000:0d:00.0: supports D1 D2
[    0.535209] pci 0000:0d:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.535216] pci 0000:0d:00.0: PME# disabled
[    0.535286] pci 0000:00:1c.3: bridge io port: [0xe000-0xefff]
[    0.535292] pci 0000:00:1c.3: bridge 32bit mmio: [0xecd00000-0xecefffff]
[    0.535300] pci 0000:00:1c.3: bridge 64bit mmio pref: [0xe0000000-0xe01fffff]
[    0.535344] pci 0000:03:00.0: reg 10 32bit mmio: [0xeccfe000-0xeccfffff]
[    0.535392] pci 0000:03:00.0: supports D1 D2
[    0.535395] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.535400] pci 0000:03:00.0: PME# disabled
[    0.535444] pci 0000:03:01.0: reg 10 32bit mmio: [0xeccfd800-0xeccfdfff]
[    0.535494] pci 0000:03:01.0: supports D1 D2
[    0.535497] pci 0000:03:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.535502] pci 0000:03:01.0: PME# disabled
[    0.535547] pci 0000:03:01.1: reg 10 32bit mmio: [0xeccfd400-0xeccfd4ff]
[    0.535596] pci 0000:03:01.1: supports D1 D2
[    0.535599] pci 0000:03:01.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.535604] pci 0000:03:01.1: PME# disabled
[    0.535649] pci 0000:03:01.2: reg 10 32bit mmio: [0xeccfd500-0xeccfd5ff]
[    0.535699] pci 0000:03:01.2: supports D1 D2
[    0.535701] pci 0000:03:01.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.535706] pci 0000:03:01.2: PME# disabled
[    0.535750] pci 0000:03:01.3: reg 10 32bit mmio: [0xeccfd600-0xeccfd6ff]
[    0.535800] pci 0000:03:01.3: supports D1 D2
[    0.535803] pci 0000:03:01.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.535808] pci 0000:03:01.3: PME# disabled
[    0.535854] pci 0000:03:01.4: reg 10 32bit mmio: [0xeccfd700-0xeccfd7ff]
[    0.535905] pci 0000:03:01.4: supports D1 D2
[    0.535907] pci 0000:03:01.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.535912] pci 0000:03:01.4: PME# disabled
[    0.535982] pci 0000:00:1e.0: transparent bridge
[    0.535990] pci 0000:00:1e.0: bridge 32bit mmio: [0xecc00000-0xeccfffff]
[    0.536035] bus 00 -> node 0
[    0.536041] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.536468] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.536574] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.536713] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.536845] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.536977] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.545766] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 11) *4
[    0.545901] ACPI: PCI Interrupt Link [LNKB] (IRQs *5 7)
[    0.546032] ACPI: PCI Interrupt Link [LNKC] (IRQs *9 10 11)
[    0.546163] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 11) *3
[    0.546296] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.546431] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.546567] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.546702] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
[    0.546936] ACPI: WMI: Mapper loaded
[    0.546977] SCSI subsystem initialized
[    0.546977] libata version 3.00 loaded.
[    0.546977] usbcore: registered new interface driver usbfs
[    0.546977] usbcore: registered new interface driver hub
[    0.546977] usbcore: registered new device driver usb
[    0.546977] PCI: Using ACPI for IRQ routing
[    0.552010] Bluetooth: Core ver 2.13
[    0.552025] NET: Registered protocol family 31
[    0.552025] Bluetooth: HCI device and connection manager initialized
[    0.552025] Bluetooth: HCI socket layer initialized
[    0.552025] NET: Registered protocol family 8
[    0.552025] NET: Registered protocol family 20
[    0.552037] NetLabel: Initializing
[    0.552039] NetLabel:  domain hash size = 128
[    0.552041] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.552054] NetLabel:  unlabeled traffic allowed by default
[    0.552070] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.552075] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.556066] AppArmor: AppArmor Filesystem Enabled
[    0.560015] Switched to high resolution mode on CPU 0
[    0.560539] Switched to high resolution mode on CPU 1
[    0.564018] pnp: PnP ACPI init
[    0.564026] ACPI: bus type pnp registered
[    0.597701] pnp 00:02: io resource (0x1000-0x1005) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.597704] pnp 00:02: io resource (0x1008-0x100f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.597795] pnp 00:03: io resource (0x1006-0x1007) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.597799] pnp 00:03: io resource (0x100a-0x1059) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.597802] pnp 00:03: io resource (0x1060-0x107f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.597805] pnp 00:03: io resource (0x1010-0x102f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.598996] pnp: PnP ACPI: found 12 devices
[    0.598999] ACPI: ACPI bus type pnp unregistered
[    0.599002] PnPBIOS: Disabled by ACPI PNP
[    0.599012] system 00:00: iomem range 0x0-0x9fbff could not be reserved
[    0.599015] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
[    0.599018] system 00:00: iomem range 0xc0000-0xcffff could not be reserved
[    0.599021] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[    0.599024] system 00:00: iomem range 0x100000-0xbfe933ff could not be reserved
[    0.599027] system 00:00: iomem range 0xbfe93400-0xbfefffff has been reserved
[    0.599030] system 00:00: iomem range 0xbff00000-0xbfffffff has been reserved
[    0.599033] system 00:00: iomem range 0xffb00000-0xffffffff has been reserved
[    0.599036] system 00:00: iomem range 0xfec00000-0xfec0ffff has been reserved
[    0.599039] system 00:00: iomem range 0xfee00000-0xfee0ffff has been reserved
[    0.599042] system 00:00: iomem range 0xfed20000-0xfed9ffff has been reserved
[    0.599045] system 00:00: iomem range 0xffa80000-0xffa83fff could not be reserved
[    0.599048] system 00:00: iomem range 0xf4000000-0xf4003fff has been reserved
[    0.599051] system 00:00: iomem range 0xf4004000-0xf4004fff has been reserved
[    0.599053] system 00:00: iomem range 0xf4005000-0xf4005fff has been reserved
[    0.599056] system 00:00: iomem range 0xf4006000-0xf4006fff has been reserved
[    0.599059] system 00:00: iomem range 0xf4008000-0xf400bfff has been reserved
[    0.599062] system 00:00: iomem range 0xf0000000-0xf3ffffff has been reserved
[    0.599069] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.599076] system 00:03: ioport range 0xf400-0xf4fe has been reserved
[    0.599079] system 00:03: ioport range 0x1080-0x10bf has been reserved
[    0.599082] system 00:03: ioport range 0x10c0-0x10df has been reserved
[    0.599085] system 00:03: ioport range 0x809-0x809 has been reserved
[    0.599093] system 00:08: ioport range 0xc80-0xcff could not be reserved
[    0.599095] system 00:08: ioport range 0x910-0x91f has been reserved
[    0.599098] system 00:08: ioport range 0x920-0x92f has been reserved
[    0.599101] system 00:08: ioport range 0xcb0-0xcbf has been reserved
[    0.599103] system 00:08: ioport range 0x930-0x97f has been reserved
[    0.599111] system 00:0b: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.633848] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.633850] pci 0000:00:01.0:   IO window: disabled
[    0.633855] pci 0000:00:01.0:   MEM window: 0xed000000-0xefefffff
[    0.633859] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.633865] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:0b
[    0.633866] pci 0000:00:1c.0:   IO window: disabled
[    0.633873] pci 0000:00:1c.0:   MEM window: disabled
[    0.633878] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.633886] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:0c
[    0.633888] pci 0000:00:1c.1:   IO window: disabled
[    0.633894] pci 0000:00:1c.1:   MEM window: 0xecf00000-0xecffffff
[    0.633899] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.633908] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:0d
[    0.633911] pci 0000:00:1c.3:   IO window: 0xe000-0xefff
[    0.633918] pci 0000:00:1c.3:   MEM window: 0xecd00000-0xecefffff
[    0.633923] pci 0000:00:1c.3:   PREFETCH window: 0x000000e0000000-0x000000e01fffff
[    0.633932] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.633934] pci 0000:00:1e.0:   IO window: disabled
[    0.633941] pci 0000:00:1e.0:   MEM window: 0xecc00000-0xeccfffff
[    0.633946] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.633962] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.633966] pci 0000:00:01.0: setting latency timer to 64
[    0.633975] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.633980] pci 0000:00:1c.0: setting latency timer to 64
[    0.633990] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.633996] pci 0000:00:1c.1: setting latency timer to 64
[    0.634006] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.634011] pci 0000:00:1c.3: setting latency timer to 64
[    0.634020] pci 0000:00:1e.0: setting latency timer to 64
[    0.634025] bus: 00 index 0 io port: [0x00-0xffff]
[    0.634027] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.634030] bus: 01 index 0 mmio: [0x0-0x0]
[    0.634032] bus: 01 index 1 mmio: [0xed000000-0xefefffff]
[    0.634034] bus: 01 index 2 mmio: [0xd0000000-0xdfffffff]
[    0.634036] bus: 01 index 3 mmio: [0x0-0x0]
[    0.634038] bus: 0b index 0 mmio: [0x0-0x0]
[    0.634040] bus: 0b index 1 mmio: [0x0-0x0]
[    0.634042] bus: 0b index 2 mmio: [0x0-0x0]
[    0.634044] bus: 0b index 3 mmio: [0x0-0x0]
[    0.634046] bus: 0c index 0 mmio: [0x0-0x0]
[    0.634048] bus: 0c index 1 mmio: [0xecf00000-0xecffffff]
[    0.634050] bus: 0c index 2 mmio: [0x0-0x0]
[    0.634052] bus: 0c index 3 mmio: [0x0-0x0]
[    0.634054] bus: 0d index 0 io port: [0xe000-0xefff]
[    0.634056] bus: 0d index 1 mmio: [0xecd00000-0xecefffff]
[    0.634059] bus: 0d index 2 mmio: [0xe0000000-0xe01fffff]
[    0.634061] bus: 0d index 3 mmio: [0x0-0x0]
[    0.634063] bus: 03 index 0 mmio: [0x0-0x0]
[    0.634065] bus: 03 index 1 mmio: [0xecc00000-0xeccfffff]
[    0.634067] bus: 03 index 2 mmio: [0x0-0x0]
[    0.634069] bus: 03 index 3 io port: [0x00-0xffff]
[    0.634071] bus: 03 index 4 mmio: [0x000000-0xffffffff]
[    0.634079] NET: Registered protocol family 2
[    0.648060] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.648317] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.648712] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.648917] TCP: Hash tables configured (established 131072 bind 65536)
[    0.648920] TCP reno registered
[    0.652081] NET: Registered protocol family 1
[    0.652202] checking if image is initramfs... it is
[    1.001012] Clocksource tsc unstable (delta = 2123572752 ns)
[    1.332990] Freeing initrd memory: 7658k freed
[    1.333034] Simple Boot Flag at 0x79 set to 0x1
[    1.333224] cpufreq: No nForce2 chipset.
[    1.333374] audit: initializing netlink socket (disabled)
[    1.333403] type=2000 audit(1253896917.332:1): initialized
[    1.341244] highmem bounce pool size: 64 pages
[    1.341249] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.342724] VFS: Disk quotas dquot_6.5.1
[    1.342790] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.343458] fuse init (API version 7.10)
[    1.343552] msgmni has been set to 1672
[    1.343781] alg: No test for stdrng (krng)
[    1.343797] io scheduler noop registered
[    1.343799] io scheduler anticipatory registered
[    1.343801] io scheduler deadline registered
[    1.343815] io scheduler cfq registered (default)
[    1.343951] pci 0000:01:00.0: Boot video device
[    1.345640] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.345682] pcieport-driver 0000:00:01.0: found MSI capability
[    1.345709] pcieport-driver 0000:00:01.0: irq 2303 for MSI/MSI-X
[    1.345720] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.345735] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.345790] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.345841] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.345876] pcieport-driver 0000:00:1c.0: irq 2302 for MSI/MSI-X
[    1.345892] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.345905] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.345918] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.345996] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.346047] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.346081] pcieport-driver 0000:00:1c.1: irq 2301 for MSI/MSI-X
[    1.346099] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.346113] pci_express 0000:00:1c.1:pcie02: allocate port service
[    1.346126] pci_express 0000:00:1c.1:pcie03: allocate port service
[    1.346203] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    1.346254] pcieport-driver 0000:00:1c.3: found MSI capability
[    1.346288] pcieport-driver 0000:00:1c.3: irq 2300 for MSI/MSI-X
[    1.346304] pci_express 0000:00:1c.3:pcie00: allocate port service
[    1.346318] pci_express 0000:00:1c.3:pcie02: allocate port service
[    1.346331] pci_express 0000:00:1c.3:pcie03: allocate port service
[    1.346426] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.346512] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.346981] ACPI: AC Adapter [AC] (off-line)
[    1.374860] ACPI: Battery Slot [BAT0] (battery present)
[    1.374942] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    1.375382] ACPI: Lid Switch [LID]
[    1.375429] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.375435] ACPI: Power Button (CM) [PBTN]
[    1.375478] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.375480] ACPI: Sleep Button (CM) [SBTN]
[    1.376073] ACPI: SSDT BFE94176, 0202 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[    1.376406] ACPI: SSDT BFE93F2B, 01C6 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[    1.376762] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.376789] processor ACPI_CPU:00: registered as cooling_device0
[    1.376793] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.377153] ACPI: SSDT BFE94378, 00C4 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[    1.377469] ACPI: SSDT BFE940F1, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[    1.377845] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.377865] processor ACPI_CPU:01: registered as cooling_device1
[    1.377869] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.382643] thermal LNXTHERM:01: registered as thermal_zone0
[    1.386894] ACPI: Thermal Zone [THM] (53 C)
[    1.386957] isapnp: Scanning for PnP cards...
[    1.741334] isapnp: No Plug & Play device found
[    1.749195] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.750298] brd: module loaded
[    1.750623] loop: module loaded
[    1.750690] Fixed MDIO Bus: probed
[    1.750695] PPP generic driver version 2.4.2
[    1.750755] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.750785] Driver 'sd' needs updating - please use bus_type methods
[    1.750795] Driver 'sr' needs updating - please use bus_type methods
[    1.750876] ata_piix 0000:00:1f.2: version 2.12
[    1.750889] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.750893] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    1.750935] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.751025] scsi0 : ata_piix
[    1.751115] scsi1 : ata_piix
[    1.752014] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    1.752017] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    1.989312] ata1.00: ATA-8: ST9320421ASG, SD13, max UDMA/133
[    1.989316] ata1.00: 625142448 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    2.050109] ata1.00: configured for UDMA/133
[    2.228494] ata2.00: ATAPI: TSSTcorp DVD+/-RW TS-L632D, DE04, max UDMA/33
[    2.268461] ata2.00: configured for UDMA/33
[    2.292527] scsi 0:0:0:0: Direct-Access     ATA      ST9320421ASG     SD13 PQ: 0 ANSI: 5
[    2.292624] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    2.292641] sd 0:0:0:0: [sda] Write Protect is off
[    2.292644] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.292671] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.292733] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    2.292749] sd 0:0:0:0: [sda] Write Protect is off
[    2.292752] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.292778] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.292781]  sda: sda2 sda3 < sda5 sda6 > sda4
[    2.340316] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.340358] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.356384] scsi 1:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-L632D DE04 PQ: 0 ANSI: 5
[    2.420515] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    2.420518] Uniform CD-ROM driver Revision: 3.20
[    2.420608] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.420645] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.421354] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.421378] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.421401] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.421405] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.421467] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    2.425380] ehci_hcd 0000:00:1d.7: debug port 1
[    2.425387] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.425401] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xffa80000
[    2.440018] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.440101] usb usb1: configuration #1 chosen from 1 choice
[    2.440131] hub 1-0:1.0: USB hub found
[    2.440138] hub 1-0:1.0: 8 ports detected
[    2.440265] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.440283] uhci_hcd: USB Universal Host Controller Interface driver
[    2.440304] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.440311] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.440314] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.440359] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.440386] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000bf80
[    2.440461] usb usb2: configuration #1 chosen from 1 choice
[    2.440487] hub 2-0:1.0: USB hub found
[    2.440494] hub 2-0:1.0: 2 ports detected
[    2.440581] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.440588] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.440591] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.440632] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    2.440667] uhci_hcd 0000:00:1d.1: irq 21, io base 0x0000bf60
[    2.440742] usb usb3: configuration #1 chosen from 1 choice
[    2.440772] hub 3-0:1.0: USB hub found
[    2.440779] hub 3-0:1.0: 2 ports detected
[    2.440866] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    2.440873] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.440876] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.440919] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    2.440953] uhci_hcd 0000:00:1d.2: irq 22, io base 0x0000bf40
[    2.441030] usb usb4: configuration #1 chosen from 1 choice
[    2.441056] hub 4-0:1.0: USB hub found
[    2.441062] hub 4-0:1.0: 2 ports detected
[    2.441148] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    2.441154] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    2.441158] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    2.441205] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    2.441239] uhci_hcd 0000:00:1d.3: irq 23, io base 0x0000bf20
[    2.441312] usb usb5: configuration #1 chosen from 1 choice
[    2.441340] hub 5-0:1.0: USB hub found
[    2.441346] hub 5-0:1.0: 2 ports detected
[    2.441494] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.444551] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.444558] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.448050] mice: PS/2 mouse device common for all mice
[    2.464086] rtc_cmos 00:06: RTC can wake from S4
[    2.464119] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    2.464151] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    2.464211] device-mapper: uevent: version 1.0.3
[    2.464322] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    2.464439] device-mapper: multipath: version 1.0.5 loaded
[    2.464442] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.464534] EISA: Probing bus 0 at eisa.0
[    2.464541] Cannot allocate resource for EISA slot 1
[    2.464572] EISA: Detected 0 cards.
[    2.464715] cpuidle: using governor ladder
[    2.464855] cpuidle: using governor menu
[    2.465387] TCP cubic registered
[    2.465486] NET: Registered protocol family 10
[    2.465944] lo: Disabled Privacy Extensions
[    2.466310] NET: Registered protocol family 17
[    2.466327] Bluetooth: L2CAP ver 2.11
[    2.466329] Bluetooth: L2CAP socket layer initialized
[    2.466332] Bluetooth: SCO (Voice Link) ver 0.6
[    2.466334] Bluetooth: SCO socket layer initialized
[    2.466396] Bluetooth: RFCOMM socket layer initialized
[    2.466402] Bluetooth: RFCOMM TTY layer initialized
[    2.466404] Bluetooth: RFCOMM ver 1.10
[    2.466732] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    2.466916] Using IPI No-Shortcut mode
[    2.466988] registered taskstats version 1
[    2.467109]   Magic number: 9:726:692
[    2.467197] rtc_cmos 00:06: setting system clock to 2009-09-25 16:41:59 UTC (1253896919)
[    2.467200] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.467202] EDD information not available.
[    2.467465] Freeing unused kernel memory: 532k freed
[    2.467627] Write protecting the kernel text: 4116k
[    2.467689] Write protecting the kernel read-only data: 1528k
[    2.686038] sky2 driver version 1.22
[    2.686088] sky2 0000:0d:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.686101] sky2 0000:0d:00.0: setting latency timer to 64
[    2.686146] sky2 0000:0d:00.0: Yukon-2 EC Ultra chip revision 3
[    2.718193] sky2 0000:0d:00.0: Marvell Yukon 88E8053 Gigabit Ethernet Controller
[    2.718196]  Part Number: Yukon 88E8053
[    2.718198]  Engineering Level: Rev. 2.0
[    2.718200]  Manufacturer: Marvell
[    2.718302] sky2 0000:0d:00.0: irq 2299 for MSI/MSI-X
[    2.719717] sky2 eth0: addr 00:00:5a:11:29:73
[    2.885046] usb 1-5: new high speed USB device using ehci_hcd and address 4
[    2.886335] b44 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.945088] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[    2.945131] b44.c:v2.0
[    2.945136] ohci1394 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.965851] eth1: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:18:8b:b7:0b:11
[    2.998120] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[eccfd800-eccfdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    3.200197] usb 1-5: configuration #1 chosen from 1 choice
[    3.243336] PM: Starting manual resume from disk
[    3.243340] PM: Resume from partition 8:6
[    3.243342] PM: Checking hibernation image.
[    3.243753] PM: Resume from disk failed.
[    3.276303] kjournald starting.  Commit interval 5 seconds
[    3.276332] EXT3-fs: mounted filesystem with ordered data mode.
[    3.440051] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    3.616573] usb 2-1: configuration #1 chosen from 1 choice
[    3.856075] usb 2-2: new low speed USB device using uhci_hcd and address 3
[    4.038579] usb 2-2: configuration #1 chosen from 1 choice
[    4.272163] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[344fc000204bb561]
[    8.811565] udev: starting version 141
[    9.000711] input: PC Speaker as /devices/platform/pcspkr/input/input5
[    9.084560] acpi device:25: registered as cooling_device2
[    9.085301] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:21/device:22/input/input6
[    9.099561] Linux agpgart interface v0.103
[    9.101077] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[    9.115654] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[    9.243267] udev: renamed network interface eth1 to eth0
[    9.266461] udev: renamed network interface eth0_rename to eth1
[    9.503540] nvidia: module license 'NVIDIA' taints kernel.
[    9.757241] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.757252] nvidia 0000:01:00.0: setting latency timer to 64
[    9.758492] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
[    9.798331] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   10.027426] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x81a0b1, caps: 0xa04713/0x200000
[   10.063330] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   10.085274] cfg80211: Calling CRDA to update world regulatory domain
[   10.098618] usbcore: registered new interface driver hiddev
[   10.115047] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input8
[   10.117170] generic-usb 0003:046D:C051.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-1/input0
[   10.117426] usbcore: registered new interface driver usbhid
[   10.117452] usbhid: v2.6:USB HID core driver
[   10.146124] cfg80211: World regulatory domain updated:
[   10.146129]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.146131]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.146134]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.146136]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.146138]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.146141]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.161275] sdhci: Secure Digital Host Controller Interface driver
[   10.161278] sdhci: Copyright(c) Pierre Ossman
[   10.187920] ricoh-mmc: Ricoh MMC Controller disabling driver
[   10.187923] ricoh-mmc: Copyright(c) Philip Langdale
[   10.187945] ricoh-mmc: Ricoh MMC controller found at 0000:03:01.2 [1180:0843] (rev 1)
[   10.187964] ricoh-mmc: Controller is now disabled.
[   10.189731] intel_rng: FWH not detected
[   10.234228] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 19)
[   10.234249] sdhci-pci 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   10.237356] mmc0: SDHCI controller on PCI [0000:03:01.1] using DMA
[   10.243589] Linux video capture interface: v2.00
[   10.253038] input: Microsoft Natural&#65533; Ergonomic Keyboard 4000 as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input9
[   10.272167] microsoft 0003:045E:00DB.0002: input,hidraw1: USB HID v1.11 Keyboard [Microsoft Natural&#65533; Ergonomic Keyboard 4000] on usb-0000:00:1d.0-2/input0
[   10.293111] input: Microsoft Natural&#65533; Ergonomic Keyboard 4000 as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.1/input/input10
[   10.296208] microsoft 0003:045E:00DB.0003: input,hidraw2: USB HID v1.11 Device [Microsoft Natural&#65533; Ergonomic Keyboard 4000] on usb-0000:00:1d.0-2/input1
[   10.304388] iTCO_vendor_support: vendor-support=0
[   10.306343] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   10.306527] iTCO_wdt: Found a ICH7-M or ICH7-U TCO device (Version=2, TCOBASE=0x1060)
[   10.306785] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   10.352248] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08c6)
[   10.359347] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   10.359351] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   10.359463] iwl3945 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.359478] iwl3945 0000:0c:00.0: setting latency timer to 64
[   10.359529] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   10.359931] iwl3945 0000:0c:00.0: irq 2298 for MSI/MSI-X
[   10.398920] input: UVC Camera (046d:08c6) as /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/input/input11
[   10.414765] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   10.415016] usbcore: registered new interface driver uvcvideo
[   10.415042] USB Video Class driver (v0.1.0)
[   10.416741] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   10.566642] lp: driver loaded but no devices found
[   10.686516] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   10.686627] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   10.928382] Adding 2931820k swap on /dev/sda6.  Priority:-1 extents:1 across:2931820k
[   10.947445] EXT3 FS on sda2, internal journal
[   11.369798] kjournald starting.  Commit interval 5 seconds
[   11.370330] EXT3 FS on sda5, internal journal
[   11.370335] EXT3-fs: mounted filesystem with ordered data mode.
[   12.000237] type=1505 audit(1253922129.032:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2196
[   12.048468] type=1505 audit(1253922129.080:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2200
[   12.048582] type=1505 audit(1253922129.080:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2200
[   12.048624] type=1505 audit(1253922129.080:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2200
[   12.048662] type=1505 audit(1253922129.080:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2200
[   12.182751] type=1505 audit(1253922129.212:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2205
[   12.182940] type=1505 audit(1253922129.212:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2205
[   12.224361] type=1505 audit(1253922129.256:9): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=2209
[   12.253996] type=1505 audit(1253922129.285:10): operation="profile_load" name="/usr/sbin/mysqld-akonadi" name2="default" pid=2213
[   12.281584] type=1505 audit(1253922129.313:11): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2217
[   28.923162] ppdev: user-space parallel port driver
[   32.812455] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   32.812459] Bluetooth: BNEP filters: protocol multicast
[   32.859255] Bridge firewalling registered



Here is output with the card inserted:




lspci:
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)                                             
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)                                              
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)                                                              
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)                                                                              
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)                                                                              
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)                                                                              
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)                                                                      
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)                                                                      
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)                                                                      
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)                                                                      
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)                                                                        
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)            
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G72M [GeForce Go 7400] (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
0d:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 20)


lsusb:
Bus 001 Device 004: ID 046d:08c6 Logitech, Inc. QuickCam for DELL Notebooks
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 046d:c051 Logitech, Inc. G3 (MX518) Optical Mouse
Bus 002 Device 003: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

lshw:
pascal-ubuntu
    description: Portable Computer
    product: MXC062
    vendor: Dell Inc.
    serial: 4J4RFC1
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=portable uuid=44454C4C-4A00-1034-8052-B4C04F464331
  *-core
       description: Motherboard
       product: 0FP985
       vendor: Dell Inc.
       physical id: 0
       serial: .4J4RFC1.CN1296171G3685.
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A07 (04/02/2007)
          size: 64KiB
          capacity: 512KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 CPU         T5600  @ 1.83GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 6.15.6
          serial: 0000-06F6-0000-0000-0000-0000
          slot: Microprocessor
          size: 1833MHz
          capacity: 1833MHz
          width: 64 bits
          clock: 166MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow cpufreq
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 2MiB
             capacity: 2MiB
             clock: 66MHz (15.0ns)
             capabilities: pipeline-burst internal varies unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 3GiB
        *-bank:0
             description: DIMM DDR Synchronous 667 MHz (1.5 ns)
             vendor: 7F7F7F7F7F020000
             physical id: 0
             serial: 00000000
             slot: DIMM_A
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR Synchronous
             vendor: FFFFFFFFFFFFFFFF
             physical id: 1
             serial: FFFFFFFF
             slot: DIMM_B
             size: 1GiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: G72M [GeForce Go 7400]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=nvidia latency=0 module=nvidia
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG [Golan] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                logical name: wmaster0
                version: 02
                serial: 00:19:d2:4d:c7:17
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
        *-pci:3
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: 88E8053 PCI-E Gigabit Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:0d:00.0
                logical name: eth1
                version: 20
                serial: 00:00:5a:11:29:73
                size: 1GB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=192.168.1.109 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=1GB/s
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
           *-network
                description: Ethernet interface
                product: BCM4401-B0 100Base-TX
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 02
                serial: 00:18:8b:b7:0b:11
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 1
                bus info: pci@0000:03:01.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2 module=ohci1394
           *-system:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.1
                bus info: pci@0000:03:01.1
                version: 19
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64 module=sdhci_pci
           *-system:1
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.2
                bus info: pci@0000:03:01.2
                version: 0a
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: driver=ricoh-mmc latency=0 module=ricoh_mmc
           *-system:2 UNCLAIMED
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 1.3
                bus info: pci@0000:03:01.3
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: latency=0
           *-generic UNCLAIMED
                product: Illegal Vendor ID
                vendor: Illegal Vendor ID
                physical id: 1.4
                bus info: pci@0000:03:01.4
                version: ff
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master vga_palette cap_list
                configuration: latency=255 maxlatency=255 mingnt=255
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801GBM/GHM (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
           *-disk
                description: ATA Disk
                product: ST9320421ASG
                vendor: Seagate
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: SD13
                serial: 5TJ0AJWG
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=e686f016
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /
                   version: 1.0
                   serial: 2812c64b-6b3f-4f58-bafb-59310733deeb
                   size: 59GiB
                   capacity: 59GiB
                   capabilities: primary bootable journaled extended_attributes large_files recover ext3 ext2 initialized
                   configuration: created=2008-11-05 09:09:26 filesystem=ext3 modified=2009-09-25 16:42:07 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2009-09-25 16:42:07 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   size: 200GiB
                   capacity: 200GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /home
                      capacity: 197GiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=continue,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 2863MiB
                      capabilities: nofs
              *-volume:2
                   description: Windows NTFS volume
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   version: 3.1
                   serial: fa598757-5150-734c-97c7-521c5b70052e
                   size: 37GiB
                   capacity: 37GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2008-12-29 21:54:57 filesystem=ntfs state=clean
           *-cdrom
                description: DVD writer
                product: DVD+-RW TS-L632D
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: DE04
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
  *-battery
       product: DELL YF0916B
       vendor: SMP
       physical id: 1
       slot: Sys. Battery Bay
       capacity: 78000mWh
       configuration: voltage=11.1V
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 4e:9b:df:31:79:1a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


lsmod:
Module                  Size  Used by            
binfmt_misc            16776  1                  
bridge                 56212  0                  
stp                    10500  1 bridge           
bnep                   20224  2                  
ppdev                  15620  0                  
parport_pc             40100  0                  
input_polldev          11912  0                  
dm_crypt               20996  0                  
snd_hda_intel         434100  3                  
snd_pcm                83076  1 snd_hda_intel    
snd_timer              29704  1 snd_pcm          
snd                    62756  9 snd_hda_intel,snd_pcm,snd_timer
soundcore              15200  1 snd                            
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm          
sbp2                   30476  0                                
lp                     17156  0                                
parport                42220  3 ppdev,parport_pc,lp            
arc4                    9856  2                                
ecb                    10752  2                                
iwl3945                97912  0                                
uvcvideo               63368  0                                
mac80211              217592  1 iwl3945                        
iTCO_wdt               19108  0                                
iTCO_vendor_support    11652  1 iTCO_wdt                       
compat_ioctl32          9344  1 uvcvideo                       
led_class              12036  1 iwl3945                        
videodev               41600  1 uvcvideo                       
hid_microsoft          11780  0                                
sdhci_pci              15232  0                                
joydev                 18496  0                                
v4l1_compat            21764  2 uvcvideo,videodev              
ricoh_mmc              11904  0                                
intel_agp              34108  0                                
sdhci                  23940  1 sdhci_pci                      
usbhid                 42336  0                                
cfg80211               38288  2 iwl3945,mac80211               
dcdbas                 15264  0
nvidia               7233756  42
agpgart                42696  2 intel_agp,nvidia
video                  25360  6
output                 11008  1 video
psmouse                61972  0
serio_raw              13444  0
pcspkr                 10496  0
ohci1394               38576  0
ieee1394               94660  2 sbp2,ohci1394
b44                    35984  0
ssb                    41220  1 b44
mii                    13312  1 b44
sky2                   54916  0
fbcon                  46112  0
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
</pre>
[/html]

---

