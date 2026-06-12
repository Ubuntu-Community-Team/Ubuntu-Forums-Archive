---
title: "Screen flickering a lot after resume from suspend XPS m1330"
date: 2009-06-22
forum: Hardware
---

### Post by sinnadyr on 2009-06-22
Got the Dell XPS m1330, using the nVidia driver version 180, and after rebooting from suspend the screen is flickering alot, for like a minute before it stops and everything is fine. 

Anyone know what could be done?

dmesg:

```
[    0.000000] BIOS EBDA/lowmem at: 0009f000/0009f000
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-13-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #44-Ubuntu SMP Tue Jun 2 07:57:31 UTC 2009 (Ubuntu 2.6.28-13.44-generic)
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
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bfe6d800 (usable)
[    0.000000]  BIOS-e820: 00000000bfe6d800 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000feda6000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0xbfe6d max_arch_pfn = 0x100000
[    0.000000] Scanning 2 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)
[    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000092000 (usable)
[    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bfe6d800 (usable)
[    0.000000]  modified: 00000000bfe6d800 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed18000 - 00000000fed1c000 (reserved)
[    0.000000]  modified: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000feda0000 - 00000000feda6000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  modified: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.000000] RAMDISK: 378bd000 - 37fef854
[    0.000000] Allocated new RAMDISK: 0087b000 - 00fad854
[    0.000000] Move RAMDISK from 00000000378bd000 - 0000000037fef853 to 0087b000 - 00fad853
[    0.000000] ACPI: RSDP 000FBC00, 0024 (r2 DELL  )
[    0.000000] ACPI: XSDT BFE6F200, 005C (r1 DELL    M08     27D80C1A ASL        61)
[    0.000000] ACPI: FACP BFE6F09C, 00F4 (r4 DELL    M08     27D80C1A ASL        61)
[    0.000000] ACPI: DSDT BFE6F800, 5733 (r2 INT430 SYSFexxx     1001 INTL 20050624)
[    0.000000] ACPI: FACS BFE7E000, 0040
[    0.000000] ACPI: HPET BFE6F300, 0038 (r1 DELL    M08            1 ASL        61)
[    0.000000] ACPI: APIC BFE6F400, 0068 (r1 DELL    M08     27D80C1A ASL        47)
[    0.000000] ACPI: MCFG BFE6F3C0, 003E (r16 DELL    M08     27D80C1A ASL        61)
[    0.000000] ACPI: SLIC BFE6F49C, 0176 (r1 DELL    M08     27D80C1A ASL        61)
[    0.000000] ACPI: BOOT BFE6EFC0, 0028 (r1 DELL    M08     27D80C1A ASL        61)
[    0.000000] ACPI: SSDT BFE6D9FE, 04CC (r1  PmRef    CpuPm     3000 INTL 20050624)
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
[    0.000000]   #3 [0000100000 - 00008760ac]    TEXT DATA BSS ==> [0000100000 - 00008760ac]
[    0.000000]   #4 [0000877000 - 000087b000]    INIT_PG_TABLE ==> [0000877000 - 000087b000]
[    0.000000]   #5 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [000087b000 - 0000fad854]      NEW RAMDISK ==> [000087b000 - 0000fad854]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x000bfe6d
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x00000007
[    0.000000]     0: 0x00000010 -> 0x00000092
[    0.000000]     0: 0x00000100 -> 0x000bfe6d
[    0.000000] On node 0 totalpages: 785906
[    0.000000] free_area_init_node: node 0, pgdat c06c9500, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3941 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4373 pages used for memmap
[    0.000000]   HighMem zone: 555354 pages, LIFO batch:31
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
[    0.000000] Allocating PCI resources starting at c4000000 (gap: c0000000:38000000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 779765
[    0.000000] Kernel command line: root=UUID=e47437c8-a4fa-4415-8b4f-7f5a99a4c6ed ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2161.137 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 15720580 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 3086764k/3144116k available (4110k kernel code, 55944k reserved, 2197k data, 532k init, 2238908k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0731000 - 0xc07b6000   ( 532 kB)
[    0.004000]       .data : 0xc05039df - 0xc0728e60   (2197 kB)
[    0.004000]       .text : 0xc0100000 - 0xc05039df   (4110 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4322.27 BogoMIPS (lpj=8644548)
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
[    0.018192] ACPI: Core revision 20080926
[    0.020194] ACPI: Checking initramfs for custom DSDT
[    0.294353] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.334049] CPU0: Intel(R) Core(TM)2 Duo CPU     T5850  @ 2.16GHz stepping 0d
[    0.336001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 4322.49 BogoMIPS (lpj=8644990)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.420402] CPU1: Intel(R) Core(TM)2 Duo CPU     T5850  @ 2.16GHz stepping 0d
[    0.420418] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.424036] Brought up 2 CPUs
[    0.424038] Total of 2 processors activated (8644.76 BogoMIPS).
[    0.424094] CPU0 attaching sched-domain:
[    0.424096]  domain 0: span 0-1 level MC
[    0.424099]   groups: 0 1
[    0.424104] CPU1 attaching sched-domain:
[    0.424106]  domain 0: span 0-1 level MC
[    0.424108]   groups: 1 0
[    0.424172] net_namespace: 776 bytes
[    0.424172] Booting paravirtualized kernel on bare hardware
[    0.424296] Time: 11:57:00  Date: 06/21/09
[    0.424296] regulator: core version 0.5
[    0.424296] NET: Registered protocol family 16
[    0.424296] EISA bus registered
[    0.424296] ACPI: bus type pci registered
[    0.424296] PCI: MCFG configuration 0: base f8000000 segment 0 buses 0 - 63
[    0.424296] PCI: MCFG area at f8000000 reserved in E820
[    0.424296] PCI: Using MMCONFIG for extended config space
[    0.424296] PCI: Using configuration type 1 for base access
[    0.425031] ACPI: EC: Look up EC in DSDT
[    0.438960] ACPI: SSDT BFE7E080, 0043 (r1  LMPWR  DELLLOM     1001 INTL 20050624)
[    0.455111] ACPI: Interpreter enabled
[    0.455116] ACPI: (supports S0 S3 S4 S5)
[    0.457030] ACPI: Using IOAPIC for interrupt routing
[    0.500193] ACPI: No dock devices found.
[    0.500202] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.500297] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.500300] pci 0000:00:01.0: PME# disabled
[    0.500395] pci 0000:00:1a.0: reg 20 io port: [0x6f20-0x6f3f]
[    0.500462] pci 0000:00:1a.1: reg 20 io port: [0x6f00-0x6f1f]
[    0.500537] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfed1c400-0xfed1c7ff]
[    0.500587] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.500593] pci 0000:00:1a.7: PME# disabled
[    0.500652] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf6ffc000-0xf6ffffff]
[    0.500696] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.500701] pci 0000:00:1b.0: PME# disabled
[    0.500773] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.500777] pci 0000:00:1c.0: PME# disabled
[    0.500852] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.500857] pci 0000:00:1c.1: PME# disabled
[    0.500934] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.500939] pci 0000:00:1c.3: PME# disabled
[    0.501015] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.501020] pci 0000:00:1c.5: PME# disabled
[    0.501087] pci 0000:00:1d.0: reg 20 io port: [0x6f80-0x6f9f]
[    0.501154] pci 0000:00:1d.1: reg 20 io port: [0x6f60-0x6f7f]
[    0.501221] pci 0000:00:1d.2: reg 20 io port: [0x6f40-0x6f5f]
[    0.501293] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfed1c000-0xfed1c3ff]
[    0.501344] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.501349] pci 0000:00:1d.7: PME# disabled
[    0.501518] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.501522] pci 0000:00:1f.0: quirk: region 1080-10bf claimed by ICH6 GPIO
[    0.501561] pci 0000:00:1f.1: reg 10 io port: [0x1f0-0x1f7]
[    0.501569] pci 0000:00:1f.1: reg 14 io port: [0x3f4-0x3f7]
[    0.501578] pci 0000:00:1f.1: reg 18 io port: [0x170-0x177]
[    0.501586] pci 0000:00:1f.1: reg 1c io port: [0x374-0x377]
[    0.501594] pci 0000:00:1f.1: reg 20 io port: [0x6fa0-0x6faf]
[    0.501671] pci 0000:00:1f.2: reg 10 io port: [0x6eb0-0x6eb7]
[    0.501680] pci 0000:00:1f.2: reg 14 io port: [0x6eb8-0x6ebb]
[    0.501688] pci 0000:00:1f.2: reg 18 io port: [0x6ec0-0x6ec7]
[    0.501696] pci 0000:00:1f.2: reg 1c io port: [0x6ec8-0x6ecb]
[    0.501705] pci 0000:00:1f.2: reg 20 io port: [0x6ee0-0x6eff]
[    0.501713] pci 0000:00:1f.2: reg 24 32bit mmio: [0xf6ffb800-0xf6ffbfff]
[    0.501735] pci 0000:00:1f.2: PME# supported from D3hot
[    0.501740] pci 0000:00:1f.2: PME# disabled
[    0.501775] pci 0000:00:1f.3: reg 10 32bit mmio: [0xf6ffb700-0xf6ffb7ff]
[    0.501803] pci 0000:00:1f.3: reg 20 io port: [0x10c0-0x10df]
[    0.501882] pci 0000:01:00.0: reg 10 32bit mmio: [0xf5000000-0xf5ffffff]
[    0.501899] pci 0000:01:00.0: reg 14 64bit mmio: [0xe0000000-0xefffffff]
[    0.501915] pci 0000:01:00.0: reg 1c 64bit mmio: [0xf2000000-0xf3ffffff]
[    0.501925] pci 0000:01:00.0: reg 24 io port: [0xef00-0xef7f]
[    0.501934] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.502019] pci 0000:00:01.0: bridge io port: [0xe000-0xefff]
[    0.502023] pci 0000:00:01.0: bridge 32bit mmio: [0xf2000000-0xf6efffff]
[    0.502028] pci 0000:00:01.0: bridge 64bit mmio pref: [0xe0000000-0xefffffff]
[    0.502225] pci 0000:0c:00.0: reg 10 64bit mmio: [0xf1ffe000-0xf1ffffff]
[    0.502315] pci 0000:0c:00.0: PME# supported from D0 D3hot D3cold
[    0.502328] pci 0000:0c:00.0: PME# disabled
[    0.502421] pci 0000:00:1c.1: bridge 32bit mmio: [0xf1f00000-0xf1ffffff]
[    0.502492] pci 0000:00:1c.3: bridge io port: [0xd000-0xdfff]
[    0.502497] pci 0000:00:1c.3: bridge 32bit mmio: [0xf1c00000-0xf1efffff]
[    0.502505] pci 0000:00:1c.3: bridge 64bit mmio pref: [0xf0000000-0xf01fffff]
[    0.502700] pci 0000:09:00.0: reg 10 64bit mmio: [0xf1bf0000-0xf1bfffff]
[    0.502831] pci 0000:09:00.0: PME# supported from D3hot D3cold
[    0.502843] pci 0000:09:00.0: PME# disabled
[    0.502941] pci 0000:00:1c.5: bridge 32bit mmio: [0xf1b00000-0xf1bfffff]
[    0.502996] pci 0000:03:01.0: reg 10 32bit mmio: [0xf1aff800-0xf1afffff]
[    0.503049] pci 0000:03:01.0: supports D1 D2
[    0.503051] pci 0000:03:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.503057] pci 0000:03:01.0: PME# disabled
[    0.503102] pci 0000:03:01.1: reg 10 32bit mmio: [0xf1aff400-0xf1aff4ff]
[    0.503156] pci 0000:03:01.1: supports D1 D2
[    0.503158] pci 0000:03:01.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.503163] pci 0000:03:01.1: PME# disabled
[    0.503209] pci 0000:03:01.2: reg 10 32bit mmio: [0xf1aff500-0xf1aff5ff]
[    0.503262] pci 0000:03:01.2: supports D1 D2
[    0.503263] pci 0000:03:01.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.503269] pci 0000:03:01.2: PME# disabled
[    0.503314] pci 0000:03:01.3: reg 10 32bit mmio: [0xf1aff600-0xf1aff6ff]
[    0.503365] pci 0000:03:01.3: supports D1 D2
[    0.503367] pci 0000:03:01.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.503372] pci 0000:03:01.3: PME# disabled
[    0.503417] pci 0000:03:01.4: reg 10 32bit mmio: [0xf1aff700-0xf1aff7ff]
[    0.503469] pci 0000:03:01.4: supports D1 D2
[    0.503470] pci 0000:03:01.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.503475] pci 0000:03:01.4: PME# disabled
[    0.503548] pci 0000:00:1e.0: transparent bridge
[    0.503556] pci 0000:00:1e.0: bridge 32bit mmio: [0xf1a00000-0xf1afffff]
[    0.503601] bus 00 -> node 0
[    0.503607] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.504048] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.504198] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.504300] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.504425] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.504548] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.504670] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    0.515824] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 11) *7
[    0.515951] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
[    0.516086] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *4
[    0.516210] ACPI: PCI Interrupt Link [LNKD] (IRQs *5 7 9 10 11)
[    0.516333] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.516460] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.516587] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.516700] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.516838] ACPI: WMI: Mapper loaded
[    0.516873] SCSI subsystem initialized
[    0.516873] libata version 3.00 loaded.
[    0.516873] usbcore: registered new interface driver usbfs
[    0.516873] usbcore: registered new interface driver hub
[    0.516873] usbcore: registered new device driver usb
[    0.516873] PCI: Using ACPI for IRQ routing
[    0.524009] Bluetooth: Core ver 2.13
[    0.524020] NET: Registered protocol family 31
[    0.524020] Bluetooth: HCI device and connection manager initialized
[    0.524020] Bluetooth: HCI socket layer initialized
[    0.524020] NET: Registered protocol family 8
[    0.524020] NET: Registered protocol family 20
[    0.524030] NetLabel: Initializing
[    0.524032] NetLabel:  domain hash size = 128
[    0.524033] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.524045] NetLabel:  unlabeled traffic allowed by default
[    0.524059] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.524064] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.528053] AppArmor: AppArmor Filesystem Enabled
[    0.532010] Switched to high resolution mode on CPU 0
[    0.532451] Switched to high resolution mode on CPU 1
[    0.536009] pnp: PnP ACPI init
[    0.536016] ACPI: bus type pnp registered
[    0.556064] pnp 00:09: io resource (0x1000-0x1005) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.556067] pnp 00:09: io resource (0x1008-0x100f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.556159] pnp 00:0a: io resource (0x1006-0x1007) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.556161] pnp 00:0a: io resource (0x100a-0x1059) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.556164] pnp 00:0a: io resource (0x1060-0x107f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.556167] pnp 00:0a: io resource (0x1010-0x102f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.578470] pnp: PnP ACPI: found 12 devices
[    0.578472] ACPI: ACPI bus type pnp unregistered
[    0.578475] PnPBIOS: Disabled by ACPI PNP
[    0.578485] system 00:05: ioport range 0xc80-0xcff could not be reserved
[    0.578491] system 00:08: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.578496] system 00:09: ioport range 0x900-0x97f has been reserved
[    0.578499] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[    0.578504] system 00:0a: ioport range 0xf400-0xf4fe has been reserved
[    0.578507] system 00:0a: ioport range 0x1080-0x10bf has been reserved
[    0.578509] system 00:0a: ioport range 0x10c0-0x10df has been reserved
[    0.578512] system 00:0a: ioport range 0x809-0x809 has been reserved
[    0.578517] system 00:0b: iomem range 0x0-0x9efff could not be reserved
[    0.578520] system 00:0b: iomem range 0x9f000-0x9ffff could not be reserved
[    0.578522] system 00:0b: iomem range 0xc0000-0xcffff could not be reserved
[    0.578525] system 00:0b: iomem range 0xe0000-0xfffff could not be reserved
[    0.578527] system 00:0b: iomem range 0x100000-0xbfe6d7ff could not be reserved
[    0.578529] system 00:0b: iomem range 0xbfe6d800-0xbfefffff has been reserved
[    0.578532] system 00:0b: iomem range 0xbff00000-0xbfffffff has been reserved
[    0.578534] system 00:0b: iomem range 0xbff00000-0xc06fffff could not be reserved
[    0.578537] system 00:0b: iomem range 0xffe00000-0xffffffff has been reserved
[    0.578540] system 00:0b: iomem range 0xffa00000-0xffbfffff has been reserved
[    0.578542] system 00:0b: iomem range 0xfec00000-0xfec0ffff has been reserved
[    0.578544] system 00:0b: iomem range 0xfee00000-0xfee0ffff has been reserved
[    0.578547] system 00:0b: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.578549] system 00:0b: iomem range 0xfeda0000-0xfeda3fff has been reserved
[    0.578552] system 00:0b: iomem range 0xfeda4000-0xfeda4fff has been reserved
[    0.578554] system 00:0b: iomem range 0xfeda5000-0xfeda5fff has been reserved
[    0.578557] system 00:0b: iomem range 0xfeda6000-0xfeda6fff has been reserved
[    0.578559] system 00:0b: iomem range 0xfed18000-0xfed1bfff has been reserved
[    0.578564] system 00:0b: iomem range 0xf8000000-0xfbffffff has been reserved
[    0.613269] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.613272] pci 0000:00:01.0:   IO window: 0xe000-0xefff
[    0.613276] pci 0000:00:01.0:   MEM window: 0xf2000000-0xf6efffff
[    0.613280] pci 0000:00:01.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
[    0.613285] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:0b
[    0.613287] pci 0000:00:1c.0:   IO window: disabled
[    0.613293] pci 0000:00:1c.0:   MEM window: disabled
[    0.613298] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.613306] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:0c
[    0.613308] pci 0000:00:1c.1:   IO window: disabled
[    0.613314] pci 0000:00:1c.1:   MEM window: 0xf1f00000-0xf1ffffff
[    0.613319] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.613327] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:0d
[    0.613331] pci 0000:00:1c.3:   IO window: 0xd000-0xdfff
[    0.613337] pci 0000:00:1c.3:   MEM window: 0xf1c00000-0xf1efffff
[    0.613342] pci 0000:00:1c.3:   PREFETCH window: 0x000000f0000000-0x000000f01fffff
[    0.613351] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:09
[    0.613353] pci 0000:00:1c.5:   IO window: disabled
[    0.613359] pci 0000:00:1c.5:   MEM window: 0xf1b00000-0xf1bfffff
[    0.613364] pci 0000:00:1c.5:   PREFETCH window: disabled
[    0.613372] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.613374] pci 0000:00:1e.0:   IO window: disabled
[    0.613380] pci 0000:00:1e.0:   MEM window: 0xf1a00000-0xf1afffff
[    0.613385] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.613400] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.613404] pci 0000:00:01.0: setting latency timer to 64
[    0.613412] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.613418] pci 0000:00:1c.0: setting latency timer to 64
[    0.613427] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.613433] pci 0000:00:1c.1: setting latency timer to 64
[    0.613443] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.613448] pci 0000:00:1c.3: setting latency timer to 64
[    0.613457] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.613462] pci 0000:00:1c.5: setting latency timer to 64
[    0.613470] pci 0000:00:1e.0: setting latency timer to 64
[    0.613475] bus: 00 index 0 io port: [0x00-0xffff]
[    0.613477] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.613479] bus: 01 index 0 io port: [0xe000-0xefff]
[    0.613481] bus: 01 index 1 mmio: [0xf2000000-0xf6efffff]
[    0.613483] bus: 01 index 2 mmio: [0xe0000000-0xefffffff]
[    0.613485] bus: 01 index 3 mmio: [0x0-0x0]
[    0.613486] bus: 0b index 0 mmio: [0x0-0x0]
[    0.613488] bus: 0b index 1 mmio: [0x0-0x0]
[    0.613490] bus: 0b index 2 mmio: [0x0-0x0]
[    0.613491] bus: 0b index 3 mmio: [0x0-0x0]
[    0.613493] bus: 0c index 0 mmio: [0x0-0x0]
[    0.613495] bus: 0c index 1 mmio: [0xf1f00000-0xf1ffffff]
[    0.613496] bus: 0c index 2 mmio: [0x0-0x0]
[    0.613498] bus: 0c index 3 mmio: [0x0-0x0]
[    0.613500] bus: 0d index 0 io port: [0xd000-0xdfff]
[    0.613502] bus: 0d index 1 mmio: [0xf1c00000-0xf1efffff]
[    0.613504] bus: 0d index 2 mmio: [0xf0000000-0xf01fffff]
[    0.613505] bus: 0d index 3 mmio: [0x0-0x0]
[    0.613507] bus: 09 index 0 mmio: [0x0-0x0]
[    0.613509] bus: 09 index 1 mmio: [0xf1b00000-0xf1bfffff]
[    0.613511] bus: 09 index 2 mmio: [0x0-0x0]
[    0.613512] bus: 09 index 3 mmio: [0x0-0x0]
[    0.613514] bus: 03 index 0 mmio: [0x0-0x0]
[    0.613516] bus: 03 index 1 mmio: [0xf1a00000-0xf1afffff]
[    0.613517] bus: 03 index 2 mmio: [0x0-0x0]
[    0.613519] bus: 03 index 3 io port: [0x00-0xffff]
[    0.613521] bus: 03 index 4 mmio: [0x000000-0xffffffff]
[    0.613528] NET: Registered protocol family 2
[    0.628046] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.628275] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.628616] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.628799] TCP: Hash tables configured (established 131072 bind 65536)
[    0.628801] TCP reno registered
[    0.632061] NET: Registered protocol family 1
[    0.632162] checking if image is initramfs... it is
[    1.187849] Freeing initrd memory: 7370k freed
[    1.187888] Simple Boot Flag at 0x79 set to 0x1
[    1.188059] cpufreq: No nForce2 chipset.
[    1.188186] audit: initializing netlink socket (disabled)
[    1.188210] type=2000 audit(1245585420.188:1): initialized
[    1.194742] highmem bounce pool size: 64 pages
[    1.194746] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.195933] VFS: Disk quotas dquot_6.5.1
[    1.195989] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.196531] fuse init (API version 7.10)
[    1.196603] msgmni has been set to 1672
[    1.196761] alg: No test for stdrng (krng)
[    1.196770] io scheduler noop registered
[    1.196772] io scheduler anticipatory registered
[    1.196774] io scheduler deadline registered
[    1.196785] io scheduler cfq registered (default)
[    1.196961] pci 0000:01:00.0: Boot video device
[    1.198750] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.198788] pcieport-driver 0000:00:01.0: found MSI capability
[    1.198813] pcieport-driver 0000:00:01.0: irq 2303 for MSI/MSI-X
[    1.198823] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.198835] pci_express 0000:00:01.0:pcie02: allocate port service
[    1.198846] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.198897] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.198950] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.198985] pcieport-driver 0000:00:1c.0: irq 2302 for MSI/MSI-X
[    1.199002] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.199014] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.199024] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.199101] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.199153] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.199188] pcieport-driver 0000:00:1c.1: irq 2301 for MSI/MSI-X
[    1.199205] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.199216] pci_express 0000:00:1c.1:pcie02: allocate port service
[    1.199226] pci_express 0000:00:1c.1:pcie03: allocate port service
[    1.199302] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    1.199355] pcieport-driver 0000:00:1c.3: found MSI capability
[    1.199390] pcieport-driver 0000:00:1c.3: irq 2300 for MSI/MSI-X
[    1.199406] pci_express 0000:00:1c.3:pcie00: allocate port service
[    1.199417] pci_express 0000:00:1c.3:pcie02: allocate port service
[    1.199428] pci_express 0000:00:1c.3:pcie03: allocate port service
[    1.199507] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    1.199559] pcieport-driver 0000:00:1c.5: found MSI capability
[    1.199594] pcieport-driver 0000:00:1c.5: irq 2299 for MSI/MSI-X
[    1.199611] pci_express 0000:00:1c.5:pcie00: allocate port service
[    1.199622] pci_express 0000:00:1c.5:pcie02: allocate port service
[    1.199632] pci_express 0000:00:1c.5:pcie03: allocate port service
[    1.199717] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.199831] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.199958] ACPI: AC Adapter [AC] (on-line)
[    1.229859] ACPI: Battery Slot [BAT0] (battery present)
[    1.229926] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    1.230990] ACPI: Lid Switch [LID]
[    1.231029] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.231034] ACPI: Power Button (CM) [PBTN]
[    1.231073] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.231076] ACPI: Sleep Button (CM) [SBTN]
[    1.231585] ACPI: SSDT BFE6E534, 0244 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[    1.231931] ACPI: SSDT BFE6DECA, 05E5 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[    1.234542] Monitor-Mwait will be used to enter C-1 state
[    1.234545] Monitor-Mwait will be used to enter C-2 state
[    1.234548] Monitor-Mwait will be used to enter C-3 state
[    1.234561] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.234584] processor ACPI_CPU:00: registered as cooling_device0
[    1.234587] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.234885] ACPI: SSDT BFE6E778, 00C4 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[    1.235188] ACPI: SSDT BFE6E4AF, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[    1.235583] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.235600] processor ACPI_CPU:01: registered as cooling_device1
[    1.235604] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.241097] thermal LNXTHERM:01: registered as thermal_zone0
[    1.244679] ACPI: Thermal Zone [THM] (33 C)
[    1.244734] isapnp: Scanning for PnP cards...
[    1.598839] isapnp: No Plug & Play device found
[    1.605161] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.606081] brd: module loaded
[    1.606352] loop: module loaded
[    1.606410] Fixed MDIO Bus: probed
[    1.606414] PPP generic driver version 2.4.2
[    1.606464] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.606489] Driver 'sd' needs updating - please use bus_type methods
[    1.606497] Driver 'sr' needs updating - please use bus_type methods
[    1.606537] ahci 0000:00:1f.2: version 3.0
[    1.606549] ahci 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.606588] ahci 0000:00:1f.2: irq 2298 for MSI/MSI-X
[    1.606660] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x5 impl SATA mode
[    1.606663] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems 
[    1.606668] ahci 0000:00:1f.2: setting latency timer to 64
[    1.606844] scsi0 : ahci
[    1.606919] scsi1 : ahci
[    1.606970] scsi2 : ahci
[    1.607195] ata1: SATA max UDMA/133 abar m2048@0xf6ffb800 port 0xf6ffb900 irq 2298
[    1.607197] ata2: DUMMY
[    1.607200] ata3: SATA max UDMA/133 abar m2048@0xf6ffb800 port 0xf6ffba00 irq 2298
[    1.924023] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.960646] ata1.00: ATA-8: WDC WD2500BEVS-75UST0, 01.01A01, max UDMA/133
[    1.960648] ata1.00: 488397168 sectors, multi 8: LBA48 NCQ (depth 31/32)
[    1.961461] ata1.00: configured for UDMA/133
[    2.296019] ata3: SATA link down (SStatus 0 SControl 300)
[    2.312097] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500BEVS-7 01.0 PQ: 0 ANSI: 5
[    2.312179] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[    2.312194] sd 0:0:0:0: [sda] Write Protect is off
[    2.312196] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.312218] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.312271] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[    2.312284] sd 0:0:0:0: [sda] Write Protect is off
[    2.312286] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.312307] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.312310]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 >
[    2.400785] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.400820] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.400864] ata_piix 0000:00:1f.1: version 2.12
[    2.400870] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.400904] ata_piix 0000:00:1f.1: setting latency timer to 64
[    2.400975] scsi3 : ata_piix
[    2.401028] scsi4 : ata_piix
[    2.401654] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6fa0 irq 14
[    2.401657] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6fa8 irq 15
[    2.564588] ata4.00: ATAPI: MATSHITA DVD+/-RW UJ-857G, Z111, max UDMA/33
[    2.580530] ata4.00: configured for UDMA/33
[    2.582989] ata5: port disabled. ignoring.
[    2.585182] scsi 3:0:0:0: CD-ROM            MATSHITA DVD+-RW UJ-857G  Z111 PQ: 0 ANSI: 5
[    2.589328] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda caddy
[    2.589331] Uniform CD-ROM driver Revision: 3.20
[    2.589404] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    2.589435] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    2.590049] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.590069] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    2.590082] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    2.590085] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    2.590137] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    2.594039] ehci_hcd 0000:00:1a.7: debug port 1
[    2.594046] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    2.594059] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfed1c400
[    2.608009] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    2.608068] usb usb1: configuration #1 chosen from 1 choice
[    2.608091] hub 1-0:1.0: USB hub found
[    2.608098] hub 1-0:1.0: 4 ports detected
[    2.608196] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.608206] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.608210] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.608246] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    2.612164] ehci_hcd 0000:00:1d.7: debug port 1
[    2.612170] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.612182] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfed1c000
[    2.624008] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.624069] usb usb2: configuration #1 chosen from 1 choice
[    2.624095] hub 2-0:1.0: USB hub found
[    2.624101] hub 2-0:1.0: 6 ports detected
[    2.624187] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.624202] uhci_hcd: USB Universal Host Controller Interface driver
[    2.624219] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.624226] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.624229] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    2.624269] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    2.624296] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f20
[    2.624368] usb usb3: configuration #1 chosen from 1 choice
[    2.624389] hub 3-0:1.0: USB hub found
[    2.624395] hub 3-0:1.0: 2 ports detected
[    2.624471] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.624477] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    2.624481] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    2.624515] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    2.624549] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f00
[    2.624614] usb usb4: configuration #1 chosen from 1 choice
[    2.624637] hub 4-0:1.0: USB hub found
[    2.624642] hub 4-0:1.0: 2 ports detected
[    2.624720] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.624726] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.624729] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.624763] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    2.624789] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f80
[    2.624855] usb usb5: configuration #1 chosen from 1 choice
[    2.624876] hub 5-0:1.0: USB hub found
[    2.624882] hub 5-0:1.0: 2 ports detected
[    2.624954] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.624960] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.624964] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.624998] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    2.625031] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f60
[    2.625096] usb usb6: configuration #1 chosen from 1 choice
[    2.625119] hub 6-0:1.0: USB hub found
[    2.625124] hub 6-0:1.0: 2 ports detected
[    2.625200] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    2.625206] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.625209] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.625247] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    2.625273] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40
[    2.625341] usb usb7: configuration #1 chosen from 1 choice
[    2.625362] hub 7-0:1.0: USB hub found
[    2.625368] hub 7-0:1.0: 2 ports detected
[    2.625495] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.628638] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.628642] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.633082] mice: PS/2 mouse device common for all mice
[    2.653060] rtc_cmos 00:03: RTC can wake from S4
[    2.653088] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    2.653121] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    2.653172] device-mapper: uevent: version 1.0.3
[    2.653246] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    2.653311] device-mapper: multipath: version 1.0.5 loaded
[    2.653313] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.653376] EISA: Probing bus 0 at eisa.0
[    2.653436] EISA: Mainboard WG_FFFF detected.
[    2.653450] Cannot allocate resource for EISA slot 1
[    2.653480] EISA: Detected 0 cards.
[    2.653581] cpuidle: using governor ladder
[    2.653685] cpuidle: using governor menu
[    2.654140] TCP cubic registered
[    2.654226] NET: Registered protocol family 10
[    2.654608] lo: Disabled Privacy Extensions
[    2.654912] NET: Registered protocol family 17
[    2.654926] Bluetooth: L2CAP ver 2.11
[    2.654928] Bluetooth: L2CAP socket layer initialized
[    2.654930] Bluetooth: SCO (Voice Link) ver 0.6
[    2.654932] Bluetooth: SCO socket layer initialized
[    2.654972] Marking TSC unstable due to TSC halts in idle
[    2.654986] Bluetooth: RFCOMM socket layer initialized
[    2.654992] Bluetooth: RFCOMM TTY layer initialized
[    2.654993] Bluetooth: RFCOMM ver 1.10
[    2.655591] Using IPI No-Shortcut mode
[    2.655657] registered taskstats version 1
[    2.655775]   Magic number: 13:186:985
[    2.655863] rtc_cmos 00:03: setting system clock to 2009-06-21 11:57:02 UTC (1245585422)
[    2.655866] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.655867] EDD information not available.
[    2.656124] Freeing unused kernel memory: 532k freed
[    2.656258] Write protecting the kernel text: 4112k
[    2.656283] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    2.656303] Write protecting the kernel read-only data: 1524k
[    2.889814] tg3.c:v3.94 (August 14, 2008)
[    2.889848] tg3 0000:09:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.889866] tg3 0000:09:00.0: setting latency timer to 64
[    3.011333] ohci1394 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    3.062090] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[f1aff800-f1afffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    3.249043] usb 2-6: new high speed USB device using ehci_hcd and address 3
[    3.313518] eth0: Tigon3 [partno(BCM95906) rev c002 PHY(5906)] (PCI Express) 10/100Base-TX Ethernet 00:21:9b:cf:eb:a4
[    3.313521] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[0] TSOcap[0]
[    3.313523] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    3.456455] usb 2-6: configuration #1 chosen from 1 choice
[    3.700041] usb 3-2: new full speed USB device using uhci_hcd and address 2
[    3.721376] PM: Starting manual resume from disk
[    3.721379] PM: Resume from partition 8:5
[    3.721380] PM: Checking hibernation image.
[    3.721593] PM: Resume from disk failed.
[    3.724066] EXT4-fs: INFO: recovery required on readonly filesystem.
[    3.724069] EXT4-fs: write access will be enabled during recovery.
[    3.755420] EXT4-fs: barriers enabled
[    3.873316] usb 3-2: configuration #1 chosen from 1 choice
[    3.875439] hub 3-2:1.0: USB hub found
[    3.877374] hub 3-2:1.0: 3 ports detected
[    4.120066] usb 7-1: new full speed USB device using uhci_hcd and address 2
[    4.292465] usb 7-1: configuration #1 chosen from 1 choice
[    4.333224] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[464fc00005297070]
[    4.370379] usb 3-2.1: new full speed USB device using uhci_hcd and address 3
[    4.493490] usb 3-2.1: configuration #1 chosen from 1 choice
[    4.569388] usb 3-2.2: new full speed USB device using uhci_hcd and address 4
[    4.703506] usb 3-2.2: configuration #1 chosen from 1 choice
[    4.710485] usbcore: registered new interface driver hiddev
[    4.713707] input: Broadcom Corp as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2.2/3-2.2:1.0/input/input5
[    4.713883] generic-usb 0003:0A5C:4502.0001: input,hidraw0: USB HID v1.11 Keyboard [Broadcom Corp] on usb-0000:00:1a.0-2.2/input0
[    4.713898] usbcore: registered new interface driver usbhid
[    4.713901] usbhid: v2.6:USB HID core driver
[    4.781384] usb 3-2.3: new full speed USB device using uhci_hcd and address 5
[    4.912508] usb 3-2.3: configuration #1 chosen from 1 choice
[    4.919768] input: Broadcom Corp as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2.3/3-2.3:1.0/input/input6
[    4.923245] generic-usb 0003:0A5C:4503.0002: input,hidraw1: USB HID v1.11 Mouse [Broadcom Corp] on usb-0000:00:1a.0-2.3/input0
[    5.610739] kjournald2 starting.  Commit interval 5 seconds
[    5.610765] EXT4-fs: delayed allocation enabled
[    5.610769] EXT4-fs: file extents enabled
[    5.610863] EXT4-fs: mballoc enabled
[    5.610866] EXT4-fs: sda6: orphan cleanup on readonly fs
[    5.610871] ext4_orphan_cleanup: deleting unreferenced inode 5888
[    5.610939] ext4_orphan_cleanup: deleting unreferenced inode 5832
[    5.610954] ext4_orphan_cleanup: deleting unreferenced inode 5877
[    5.610961] ext4_orphan_cleanup: deleting unreferenced inode 5655
[    5.610968] EXT4-fs: sda6: 4 orphan inodes deleted
[    5.610970] EXT4-fs: recovery complete.
[    6.038641] EXT4-fs: mounted filesystem with ordered data mode.
[   11.077074] udev: starting version 141
[   11.293106] cfg80211: Calling CRDA to update world regulatory domain
[   11.568077] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   11.568198] usbcore: registered new interface driver btusb
[   11.573790] Linux agpgart interface v0.103
[   11.619920] cfg80211: World regulatory domain updated:
[   11.619924] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   11.619926] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.619928] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.619930] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.619932] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.619934] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.832345] iTCO_vendor_support: vendor-support=0
[   12.124494] nvidia: module license 'NVIDIA' taints kernel.
[   12.177923] Linux video capture interface: v2.00
[   12.204693] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   12.330779] sdhci: Secure Digital Host Controller Interface driver
[   12.330781] sdhci: Copyright(c) Pierre Ossman
[   12.352193] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 22)
[   12.352213] sdhci-pci 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   12.355482] mmc0: SDHCI controller on PCI [0000:03:01.1] using DMA
[   12.377384] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.377401] nvidia 0000:01:00.0: setting latency timer to 64
[   12.377848] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
[   12.399092] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   12.428869] ricoh-mmc: Ricoh MMC Controller disabling driver
[   12.428872] ricoh-mmc: Copyright(c) Philip Langdale
[   12.428908] ricoh-mmc: Ricoh MMC controller found at 0000:03:01.2 [1180:0843] (rev 12)
[   12.428927] ricoh-mmc: Controller is now disabled.
[   12.581112] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   12.590235] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   12.590376] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
[   12.590465] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   12.706491] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:7670)
[   12.706876] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
[   12.707525] input: Laptop Integrated Webcam as /devices/pci0000:00/0000:00:1d.7/usb2/2-6/2-6:1.0/input/input8
[   12.729189] usbcore: registered new interface driver uvcvideo
[   12.729212] USB Video Class driver (v0.1.0)
[   12.777971] acpi device:32: registered as cooling_device2
[   12.779191] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2e/device:2f/input/input9
[   12.789663] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   12.832171] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[   12.832175] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[   12.832288] iwlagn 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.832318] iwlagn 0000:0c:00.0: setting latency timer to 64
[   12.832399] iwlagn: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[   12.875483] iwlagn: Tunable channels: 13 802.11bg, 19 802.11a channels
[   12.875566] iwlagn 0000:0c:00.0: irq 2297 for MSI/MSI-X
[   12.876578] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   13.120826] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   13.120883] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   13.339915] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1c0b1, caps: 0xa04751/0xa00000
[   13.377265] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input10
[   13.596171] lp: driver loaded but no devices found
[   13.688410] Adding 2931820k swap on /dev/sda5.  Priority:-1 extents:1 across:2931820k
[   14.222132] EXT4 FS on sda6, internal journal on sda6:8
[   16.138142] kjournald starting.  Commit interval 5 seconds
[   16.138440] EXT3 FS on sda7, internal journal
[   16.138449] EXT3-fs: mounted filesystem with ordered data mode.
[   16.371674] type=1505 audit(1245578236.212:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2477
[   16.413356] type=1505 audit(1245578236.256:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2481
[   16.413448] type=1505 audit(1245578236.256:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2481
[   16.413487] type=1505 audit(1245578236.256:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2481
[   16.413522] type=1505 audit(1245578236.256:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2481
[   16.528077] type=1505 audit(1245578236.372:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2486
[   16.528249] type=1505 audit(1245578236.372:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2486
[   16.552929] type=1505 audit(1245578236.396:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2490
[   20.232402] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   20.232406] vboxdrv: Successfully done.
[   20.232408] vboxdrv: Found 2 processor cores.
[   20.232482] vboxdrv: fAsync=0 offMin=0x1ad offMax=0x8d6
[   20.232522] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   20.232523] vboxdrv: Successfully loaded version 2.2.4 (interface 0x000a0009).
[   21.281829] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   21.281832] Bluetooth: BNEP filters: protocol multicast
[   21.363960] Bridge firewalling registered
[   23.294766] ppdev: user-space parallel port driver
[   26.157607] tg3 0000:09:00.0: irq 2296 for MSI/MSI-X
[   26.233178] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.389626] iwlagn 0000:0c:00.0: firmware: requesting iwlwifi-4965-2.ucode
[   26.689160] Registered led device: iwl-phy0:radio
[   26.689193] Registered led device: iwl-phy0:assoc
[   26.689222] Registered led device: iwl-phy0:RX
[   26.689252] Registered led device: iwl-phy0:TX
[   26.716756] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   27.818026] wlan0: direct probe to AP 00:19:5b:df:83:cc try 1
[   27.820180] wlan0 direct probe responded
[   27.820183] wlan0: authenticate with AP 00:19:5b:df:83:cc
[   28.020063] wlan0: authenticate with AP 00:19:5b:df:83:cc
[   28.022107] wlan0: authenticated
[   28.022114] wlan0: associate with AP 00:19:5b:df:83:cc
[   28.220055] wlan0: associate with AP 00:19:5b:df:83:cc
[   28.226567] wlan0: RX AssocResp from 00:19:5b:df:83:cc (capab=0x421 status=0 aid=3)
[   28.226572] wlan0: associated
[   28.247560] wlan0: disassociating by local choice (reason=3)
[   61.908561] wlan0: direct probe to AP 00:19:5b:df:83:cc try 1
[   61.919968] wlan0: direct probe to AP 00:19:5b:df:83:cc try 1
[   61.919988] wlan0 direct probe responded
[   61.919994] wlan0: authenticate with AP 00:19:5b:df:83:cc
[   61.922645] wlan0: authenticated
[   61.922651] wlan0: associate with AP 00:19:5b:df:83:cc
[   62.120075] wlan0: associate with AP 00:19:5b:df:83:cc
[   62.122234] wlan0: RX ReassocResp from 00:19:5b:df:83:cc (capab=0x421 status=0 aid=4)
[   62.122239] wlan0: associated
[   62.141226] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   72.144076] wlan0: no IPv6 routers present
[  394.372629] kjournald starting.  Commit interval 5 seconds
[  394.373041] EXT3 FS on sda1, internal journal
[  394.373049] EXT3-fs: mounted filesystem with ordered data mode.
[  891.498478] wlan0: deauthenticated
[  892.496079] wlan0: direct probe to AP 00:19:5b:df:83:cc try 1
[  892.696076] wlan0: direct probe to AP 00:19:5b:df:83:cc try 2
[  892.896076] wlan0: direct probe to AP 00:19:5b:df:83:cc try 3
[  893.097357] wlan0: direct probe to AP 00:19:5b:df:83:cc timed out
[  894.833561] wlan0: direct probe to AP 00:19:5b:df:83:cc try 1
[  894.847653] wlan0: direct probe to AP 00:19:5b:df:83:cc try 1
[  895.044076] wlan0: direct probe to AP 00:19:5b:df:83:cc try 2
[  895.244074] wlan0: direct probe to AP 00:19:5b:df:83:cc try 3
[  895.446719] wlan0: direct probe to AP 00:19:5b:df:83:cc timed out
[  905.912817] wlan0: direct probe to AP 00:19:5b:df:83:cc try 1
[  905.920118] wlan0: direct probe to AP 00:19:5b:df:83:cc try 1
[  906.120077] wlan0: direct probe to AP 00:19:5b:df:83:cc try 2
[  906.320077] wlan0: direct probe to AP 00:19:5b:df:83:cc try 3
[  906.520073] wlan0: direct probe to AP 00:19:5b:df:83:cc timed out
[  906.780050] wlan0: direct probe to AP 00:19:5b:df:83:cc try 1
[  906.980083] wlan0: direct probe to AP 00:19:5b:df:83:cc try 2
[  907.184071] wlan0: direct probe to AP 00:19:5b:df:83:cc try 3
[  907.380101] wlan0: direct probe to AP 00:19:5b:df:83:cc timed out
[  908.465716] wlan0: direct probe to AP 00:19:5b:df:83:cc try 1
[  908.473055] wlan0: direct probe to AP 00:19:5b:df:83:cc try 1
[  908.672129] wlan0: direct probe to AP 00:19:5b:df:83:cc try 2
[  908.872129] wlan0: direct probe to AP 00:19:5b:df:83:cc try 3
[  909.072122] wlan0: direct probe to AP 00:19:5b:df:83:cc timed out
[  919.487811] wlan0: direct probe to AP 00:19:5b:df:83:cc try 1
[  919.495187] wlan0: direct probe to AP 00:19:5b:df:83:cc try 1
[  919.692077] wlan0: direct probe to AP 00:19:5b:df:83:cc try 2
[  919.892078] wlan0: direct probe to AP 00:19:5b:df:83:cc try 3
[  920.092103] wlan0: direct probe to AP 00:19:5b:df:83:cc timed out
[  930.511186] wlan0: direct probe to AP 00:19:5b:df:83:cc try 1
[  930.518185] wlan0: direct probe to AP 00:19:5b:df:83:cc try 1
[  930.716081] wlan0: direct probe to AP 00:19:5b:df:83:cc try 2
[  930.917070] wlan0: direct probe to AP 00:19:5b:df:83:cc try 3
[  931.116079] wlan0: direct probe to AP 00:19:5b:df:83:cc timed out
[  941.541201] wlan0: direct probe to AP 00:19:5b:df:83:cc try 1
[  941.548532] wlan0: direct probe to AP 00:19:5b:df:83:cc try 1
[  941.749061] wlan0: direct probe to AP 00:19:5b:df:83:cc try 2
[  941.949021] wlan0: direct probe to AP 00:19:5b:df:83:cc try 3
[  942.149073] wlan0: direct probe to AP 00:19:5b:df:83:cc timed out
[  952.562692] wlan0: direct probe to AP 00:19:5b:df:83:cc try 1
[  952.569971] wlan0: direct probe to AP 00:19:5b:df:83:cc try 1
[  952.768080] wlan0: direct probe to AP 00:19:5b:df:83:cc try 2
[  952.969077] wlan0: direct probe to AP 00:19:5b:df:83:cc try 3
[  953.169045] wlan0: direct probe to AP 00:19:5b:df:83:cc timed out
[  963.610742] wlan0: direct probe to AP 00:19:5b:df:83:cc try 1
[  963.617475] wlan0: direct probe to AP 00:19:5b:df:83:cc try 1
[  963.817082] wlan0: direct probe to AP 00:19:5b:df:83:cc try 2
[  964.016306] wlan0: direct probe to AP 00:19:5b:df:83:cc try 3
[  964.216054] wlan0: direct probe to AP 00:19:5b:df:83:cc timed out
[  966.585912] wlan0: direct probe to AP 00:19:5b:df:83:cc try 1
[  966.797109] wlan0: direct probe to AP 00:19:5b:df:83:cc try 2
[  966.997051] wlan0: direct probe to AP 00:19:5b:df:83:cc try 3
[  967.197050] wlan0: direct probe to AP 00:19:5b:df:83:cc timed out
[  976.534645] wlan0: authenticate with AP 00:11:50:94:37:64
[  976.536516] wlan0: authenticated
[  976.536519] wlan0: associate with AP 00:11:50:94:37:64
[  976.550159] wlan0: RX AssocResp from 00:11:50:94:37:64 (capab=0x411 status=0 aid=6)
[  976.550165] wlan0: associated
[ 1025.122139] wlan0: disassociating by local choice (reason=3)
[ 1025.145017] iwlagn: index 0 not used in uCode key table.
[ 1047.767913] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[ 1050.591053] CE: hpet increasing min_delta_ns to 15000 nsec
[ 1065.148350] wlan0: direct probe to AP 00:14:78:b6:1e:10 try 1
[ 1065.162519] wlan0: direct probe to AP 00:14:78:b6:1e:10 try 1
[ 1065.360070] wlan0: direct probe to AP 00:14:78:b6:1e:10 try 2
[ 1065.560041] wlan0: direct probe to AP 00:14:78:b6:1e:10 try 3
[ 1065.761073] wlan0: direct probe to AP 00:14:78:b6:1e:10 timed out
[ 1076.208702] wlan0: direct probe to AP 00:14:78:b6:1e:10 try 1
[ 1076.216147] wlan0: direct probe to AP 00:14:78:b6:1e:10 try 1
[ 1076.416048] wlan0: direct probe to AP 00:14:78:b6:1e:10 try 2
[ 1076.616194] wlan0: direct probe to AP 00:14:78:b6:1e:10 try 3
[ 1076.816087] wlan0: direct probe to AP 00:14:78:b6:1e:10 timed out
[ 1085.578683] wlan0: direct probe to AP 00:14:78:b6:1e:10 try 1
[ 1085.776204] wlan0: direct probe to AP 00:14:78:b6:1e:10 try 2
[ 1085.976095] wlan0: direct probe to AP 00:14:78:b6:1e:10 try 3
[ 1086.176098] wlan0: direct probe to AP 00:14:78:b6:1e:10 timed out
[ 4931.831233] wlan0: authenticate with AP 00:11:50:94:37:64
[ 4932.028073] wlan0: authenticate with AP 00:11:50:94:37:64
[ 4932.035113] wlan0: authenticated
[ 4932.035118] wlan0: associate with AP 00:11:50:94:37:64
[ 4932.232099] wlan0: associate with AP 00:11:50:94:37:64
[ 4932.237398] wlan0: RX AssocResp from 00:11:50:94:37:64 (capab=0x411 status=0 aid=6)
[ 4932.237404] wlan0: associated
[ 4932.962235] CE: hpet increasing min_delta_ns to 22500 nsec
[ 4981.991159] wlan0: disassociating by local choice (reason=3)
[ 4982.016825] wlan0: direct probe to AP 00:11:50:94:37:64 try 1
[ 4982.019744] iwlagn: index 0 not used in uCode key table.
[ 4982.213729] wlan0: direct probe to AP 00:11:50:94:37:64 try 2
[ 4982.412069] wlan0: direct probe to AP 00:11:50:94:37:64 try 3
[ 4982.612185] wlan0: direct probe to AP 00:11:50:94:37:64 timed out
[ 4992.036109] wlan0: direct probe to AP 00:11:50:94:37:64 try 1
[ 4992.036139] iwlagn: index 0 not used in uCode key table.
[ 4992.044250] wlan0: direct probe to AP 00:11:50:94:37:64 try 1
[ 4992.047496] wlan0 direct probe responded
[ 4992.047502] wlan0: authenticate with AP 00:11:50:94:37:64
[ 4992.050127] wlan0: authenticated
[ 4992.050134] wlan0: associate with AP 00:11:50:94:37:64
[ 4992.059006] wlan0: RX ReassocResp from 00:11:50:94:37:64 (capab=0x411 status=0 aid=6)
[ 4992.059011] wlan0: associated
[ 5033.618066] wlan0: deauthenticated
[ 5034.617075] wlan0: direct probe to AP 00:11:50:94:37:64 try 1
[ 5034.816164] wlan0: direct probe to AP 00:11:50:94:37:64 try 2
[ 5035.017073] wlan0: direct probe to AP 00:11:50:94:37:64 try 3
[ 5035.216081] wlan0: direct probe to AP 00:11:50:94:37:64 timed out
[ 5036.636684] wlan0: direct probe to AP 00:11:50:94:37:64 try 1
[ 5036.650825] wlan0: direct probe to AP 00:11:50:94:37:64 try 1
[ 5036.650859] iwlagn: index 0 not used in uCode key table.
[ 5036.848079] wlan0: direct probe to AP 00:11:50:94:37:64 try 2
[ 5036.850128] wlan0 direct probe responded
[ 5036.850135] wlan0: authenticate with AP 00:11:50:94:37:64
[ 5036.868069] wlan0: authenticated
[ 5036.868075] wlan0: associate with AP 00:11:50:94:37:64
[ 5036.871301] wlan0: RX ReassocResp from 00:11:50:94:37:64 (capab=0x411 status=0 aid=6)
[ 5036.871304] wlan0: associated
[ 5054.039664] wlan0: disassociating by local choice (reason=3)
[ 5054.048044] iwlagn: index 0 not used in uCode key table.
[ 5055.680264] wlan0: direct probe to AP 00:11:50:94:37:64 try 1
[ 5055.694445] wlan0: direct probe to AP 00:11:50:94:37:64 try 1
[ 5055.892102] wlan0: direct probe to AP 00:11:50:94:37:64 try 2
[ 5056.092071] wlan0: direct probe to AP 00:11:50:94:37:64 try 3
[ 5056.094126] wlan0 direct probe responded
[ 5056.094133] wlan0: authenticate with AP 00:11:50:94:37:64
[ 5056.096184] wlan0: authenticated
[ 5056.096190] wlan0: associate with AP 00:11:50:94:37:64
[ 5056.101802] wlan0: RX ReassocResp from 00:11:50:94:37:64 (capab=0x411 status=0 aid=6)
[ 5056.101807] wlan0: associated
[ 5112.752990] wlan0: disassociating by local choice (reason=3)
[ 5112.775266] wlan0: direct probe to AP 00:11:50:94:37:64 try 1
[ 5112.775385] iwlagn: index 0 not used in uCode key table.
[ 5112.790659] wlan0: direct probe to AP 00:11:50:94:37:64 try 1
[ 5112.988041] wlan0: direct probe to AP 00:11:50:94:37:64 try 2
[ 5113.189068] wlan0: direct probe to AP 00:11:50:94:37:64 try 3
[ 5113.389791] wlan0: direct probe to AP 00:11:50:94:37:64 timed out
[ 5122.789290] wlan0: direct probe to AP 00:11:50:94:37:64 try 1
[ 5122.796264] wlan0: direct probe to AP 00:11:50:94:37:64 try 1
[ 5122.796287] wlan0 direct probe responded
[ 5122.796292] iwlagn: index 0 not used in uCode key table.
[ 5122.796301] wlan0: authenticate with AP 00:11:50:94:37:64
[ 5122.821101] wlan0: authenticated
[ 5122.821111] wlan0: associate with AP 00:11:50:94:37:64
[ 5122.827922] wlan0: RX ReassocResp from 00:11:50:94:37:64 (capab=0x411 status=0 aid=6)
[ 5122.827928] wlan0: associated
[ 5168.759148] wlan0: disassociating by local choice (reason=3)
[ 5168.793706] iwlagn: index 0 not used in uCode key table.
[ 6039.894740] iwlagn: MAC is in deep sleep!
[ 6041.956805] PM: Syncing filesystems ... done.
[ 6041.969592] PM: Preparing system for mem sleep
[ 6041.969597] Freezing user space processes ... (elapsed 0.00 seconds) done.
[ 6041.972033] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[ 6041.975137] PM: Entering mem sleep
[ 6041.975147] Suspending console(s) (use no_console_suspend to debug)
[ 6042.014133] btusb_intr_complete: hci0 urb f6604100 failed to resubmit (1)
[ 6042.015133] btusb_bulk_complete: hci0 urb f6604580 failed to resubmit (2)
[ 6042.015144] btusb_bulk_complete: hci0 urb f6604c00 failed to resubmit (1)
[ 6042.500105] Clocksource tsc unstable (delta = -179801843 ns)
[ 6042.840324] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[ 6042.840534] sd 0:0:0:0: [sda] Stopping disk
[ 6043.267750] ricoh-mmc: Suspending.
[ 6043.267760] ricoh-mmc: Controller is now re-enabled.
[ 6043.268841] ACPI handle has no context!
[ 6043.268848] sdhci-pci 0000:03:01.1: PCI INT B disabled
[ 6043.268854] ACPI handle has no context!
[ 6043.320301] NVRM: RmPowerManagement: 4
[ 6043.448425] ata5: port disabled. ignoring.
[ 6043.448514] ata_piix 0000:00:1f.1: PCI INT A disabled
[ 6043.448668] ehci_hcd 0000:00:1d.7: PCI INT A disabled
[ 6043.464287] uhci_hcd 0000:00:1d.2: PCI INT C disabled
[ 6043.464341] uhci_hcd 0000:00:1d.1: PCI INT B disabled
[ 6043.464395] uhci_hcd 0000:00:1d.0: PCI INT A disabled
[ 6043.496258] HDA Intel 0000:00:1b.0: PCI INT A disabled
[ 6043.512334] ehci_hcd 0000:00:1a.7: PCI INT C disabled
[ 6043.528287] uhci_hcd 0000:00:1a.1: PCI INT B disabled
[ 6043.528341] uhci_hcd 0000:00:1a.0: PCI INT A disabled
[ 6043.528493] PM: suspend devices took 1.556 seconds
[ 6043.532900] ACPI: Preparing to enter system sleep state S3
[ 6043.534726] Disabling non-boot CPUs ...
[ 6043.640018] CPU 1 is now offline
[ 6043.640021] SMP alternatives: switching to UP code
[ 6043.764830] CPU0 attaching NULL sched-domain.
[ 6043.764833] CPU1 attaching NULL sched-domain.
[ 6043.765047] CPU0 attaching NULL sched-domain.
[ 6043.765192] CPU1 is down
[ 6043.765283] Extended CMOS year: 2000
[ 6043.765283] Back to C!
[ 6043.765283] Extended CMOS year: 2000
[ 6043.765283] Enabling non-boot CPUs ...
[ 6043.765283] SMP alternatives: switching to SMP code
[ 6043.889406] Booting processor 1 APIC 0x1 ip 0x6000
[ 6043.764694] Initializing CPU#1
[ 6043.764694] Calibrating delay using timer specific routine.. 4322.56 BogoMIPS (lpj=8645123)
[ 6043.764694] CPU: L1 I cache: 32K, L1 D cache: 32K
[ 6043.764694] CPU: L2 cache: 2048K
[ 6043.764694] CPU: Physical Processor ID: 0
[ 6043.764694] CPU: Processor Core ID: 1
[ 6043.980433] CPU1: Intel(R) Core(TM)2 Duo CPU     T5850  @ 2.16GHz stepping 0d
[ 6043.980488] CPU0 attaching NULL sched-domain.
[ 6043.981016] Switched to high resolution mode on CPU 1
[ 6043.981018] CPU0 attaching sched-domain:
[ 6043.981021]  domain 0: span 0-1 level MC
[ 6043.981022]   groups: 0 1
[ 6043.981026] CPU1 attaching sched-domain:
[ 6043.981028]  domain 0: span 0-1 level MC
[ 6043.981029]   groups: 1 0
[ 6043.984022] CPU1 is up
[ 6043.984025] ACPI: Waking up from system sleep state S3
[ 6044.009573] pcieport-driver 0000:00:01.0: restoring config space at offset 0xf (was 0x100, writing 0x1a0100)
[ 6044.009579] pcieport-driver 0000:00:01.0: restoring config space at offset 0xa (was 0xf, writing 0x0)
[ 6044.009583] pcieport-driver 0000:00:01.0: restoring config space at offset 0x9 (was 0x1fff1, writing 0xeff1e001)
[ 6044.009587] pcieport-driver 0000:00:01.0: restoring config space at offset 0x8 (was 0xfea0fa00, writing 0xf6e0f200)
[ 6044.009590] pcieport-driver 0000:00:01.0: restoring config space at offset 0x7 (was 0xf0, writing 0xe0e0)
[ 6044.009594] pcieport-driver 0000:00:01.0: restoring config space at offset 0x6 (was 0x0, writing 0x10100)
[ 6044.009599] pcieport-driver 0000:00:01.0: restoring config space at offset 0x3 (was 0x10000, writing 0x10010)
[ 6044.009603] pcieport-driver 0000:00:01.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100507)
[ 6044.009625] pcieport-driver 0000:00:01.0: setting latency timer to 64
[ 6044.009635] uhci_hcd 0000:00:1a.0: enabling device (0000 -> 0001)
[ 6044.009641] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[ 6044.009647] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[ 6044.009654] uhci_hcd 0000:00:1a.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 6044.009668] uhci_hcd 0000:00:1a.0: restoring config space at offset 0x8 (was 0x1, writing 0x6f21)
[ 6044.009709] usb usb3: root hub lost power or was reset
[ 6044.009731] uhci_hcd 0000:00:1a.1: enabling device (0000 -> 0001)
[ 6044.009735] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[ 6044.009745] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[ 6044.009754] uhci_hcd 0000:00:1a.1: restoring config space at offset 0xf (was 0x200, writing 0x20a)
[ 6044.009770] uhci_hcd 0000:00:1a.1: restoring config space at offset 0x8 (was 0x1, writing 0x6f01)
[ 6044.009810] usb usb4: root hub lost power or was reset
[ 6044.024242] ehci_hcd 0000:00:1a.7: enabling device (0000 -> 0002)
[ 6044.024249] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[ 6044.024259] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[ 6044.024281] ehci_hcd 0000:00:1a.7: restoring config space at offset 0xf (was 0x300, writing 0x309)
[ 6044.024310] ehci_hcd 0000:00:1a.7: restoring config space at offset 0x4 (was 0x0, writing 0xfed1c400)
[ 6044.024324] ehci_hcd 0000:00:1a.7: restoring config space at offset 0x1 (was 0x2900006, writing 0x2900106)
[ 6044.040265] HDA Intel 0000:00:1b.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[ 6044.040295] HDA Intel 0000:00:1b.0: restoring config space at offset 0x4 (was 0xfebfc004, writing 0xf6ffc004)
[ 6044.040303] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 6044.040314] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100102)
[ 6044.040344] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[ 6044.040354] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 6044.040396] pcieport-driver 0000:00:1c.0: restoring config space at offset 0xf (was 0x100, writing 0x20100)
[ 6044.040416] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
[ 6044.040425] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x8 (was 0x0, writing 0xfff0)
[ 6044.040434] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x7 (was 0x0, writing 0x200000f0)
[ 6044.040449] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x6 (was 0x0, writing 0xb0b00)
[ 6044.040457] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 6044.040464] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[ 6044.040509] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[ 6044.040527] pcieport-driver 0000:00:1c.1: restoring config space at offset 0xf (was 0x200, writing 0x20200)
[ 6044.040541] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
[ 6044.040546] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x8 (was 0x0, writing 0xf1f0f1f0)
[ 6044.040551] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x7 (was 0x0, writing 0xf0)
[ 6044.040556] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x6 (was 0x0, writing 0xc0c00)
[ 6044.040565] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 6044.040572] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100507)
[ 6044.040616] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[ 6044.040635] pcieport-driver 0000:00:1c.3: restoring config space at offset 0xf (was 0x400, writing 0x20400)
[ 6044.040649] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x9 (was 0x10001, writing 0xf011f001)
[ 6044.040655] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x8 (was 0x0, writing 0xf1e0f1c0)
[ 6044.040660] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x7 (was 0x0, writing 0xd0d0)
[ 6044.040665] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x6 (was 0x0, writing 0xe0d00)
[ 6044.040674] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 6044.040681] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[ 6044.040726] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[ 6044.040744] pcieport-driver 0000:00:1c.5: restoring config space at offset 0xf (was 0x200, writing 0x20200)
[ 6044.040757] pcieport-driver 0000:00:1c.5: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
[ 6044.040762] pcieport-driver 0000:00:1c.5: restoring config space at offset 0x8 (was 0x0, writing 0xf1b0f1b0)
[ 6044.040768] pcieport-driver 0000:00:1c.5: restoring config space at offset 0x7 (was 0x0, writing 0xf0)
[ 6044.040773] pcieport-driver 0000:00:1c.5: restoring config space at offset 0x6 (was 0x0, writing 0x90900)
[ 6044.040781] pcieport-driver 0000:00:1c.5: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 6044.040788] pcieport-driver 0000:00:1c.5: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[ 6044.040832] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[ 6044.040841] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[ 6044.040846] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[ 6044.040901] usb usb5: root hub lost power or was reset
[ 6044.040919] uhci_hcd 0000:00:1d.1: enabling device (0000 -> 0001)
[ 6044.040922] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[ 6044.040929] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[ 6044.040935] uhci_hcd 0000:00:1d.1: restoring config space at offset 0xf (was 0x200, writing 0x20a)
[ 6044.040950] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x8 (was 0x1, writing 0x6f61)
[ 6044.040989] usb usb6: root hub lost power or was reset
[ 6044.041015] uhci_hcd 0000:00:1d.2: enabling device (0000 -> 0001)
[ 6044.041021] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[ 6044.041031] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[ 6044.041041] uhci_hcd 0000:00:1d.2: restoring config space at offset 0xf (was 0x300, writing 0x309)
[ 6044.041062] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x8 (was 0x1, writing 0x6f41)
[ 6044.041101] usb usb7: root hub lost power or was reset
[ 6044.056241] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[ 6044.056249] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[ 6044.056352] pci 0000:00:1e.0: restoring config space at offset 0x9 (was 0x100f1, writing 0x1fff1)
[ 6044.056364] pci 0000:00:1e.0: restoring config space at offset 0x8 (was 0xa0, writing 0xf1a0f1a0)
[ 6044.056373] pci 0000:00:1e.0: restoring config space at offset 0x7 (was 0x2280e0f0, writing 0x228000f0)
[ 6044.056394] pci 0000:00:1e.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100107)
[ 6044.056419] pci 0000:00:1e.0: setting latency timer to 64
[ 6044.056474] pci 0000:00:1f.0: restoring config space at offset 0x1 (was 0x2100007, writing 0x2100107)
[ 6044.056494] ata_piix 0000:00:1f.1: restoring config space at offset 0xf (was 0x100, writing 0x107)
[ 6044.056520] ata_piix 0000:00:1f.1: restoring config space at offset 0x1 (was 0x2800005, writing 0x2880005)
[ 6044.056530] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 6044.056535] ata_piix 0000:00:1f.1: setting latency timer to 64
[ 6044.056583] ata4.00: _GTF evaluation failed (AE 0x1001)
[ 6044.056747] ata5: port disabled. ignoring.
[ 6044.072257] ahci 0000:00:1f.2: restoring config space at offset 0xf (was 0x200, writing 0x20a)
[ 6044.072276] ahci 0000:00:1f.2: restoring config space at offset 0x9 (was 0x0, writing 0xf6ffb800)
[ 6044.072300] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00000, writing 0x2b00407)
[ 6044.072356] ahci 0000:00:1f.2: setting latency timer to 64
[ 6044.072414] pci 0000:00:1f.3: restoring config space at offset 0xf (was 0x200, writing 0x20a)
[ 6044.072456] pci 0000:00:1f.3: restoring config space at offset 0x4 (was 0x0, writing 0xf6ffb700)
[ 6044.072466] pci 0000:00:1f.3: restoring config space at offset 0x1 (was 0x2800001, writing 0x2800103)
[ 6044.072572] NVRM: RmPowerManagement: 5
[ 6044.238479] ata4.00: configured for UDMA/33
[ 6044.396104] ata3: SATA link down (SStatus 0 SControl 300)
[ 6044.936268] iwlagn 0000:0c:00.0: enabling device (0000 -> 0002)
[ 6044.936415] iwlagn 0000:0c:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[ 6044.936490] iwlagn 0000:0c:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf1ffe004)
[ 6044.936515] iwlagn 0000:0c:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 6044.936530] iwlagn 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100106)
[ 6044.936721] tg3 0000:09:00.0: restoring config space at offset 0xc (was 0x0, writing 0xffb90000)
[ 6044.936774] tg3 0000:09:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 6044.936791] tg3 0000:09:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100106)
[ 6044.952251] ohci1394 0000:03:01.0: restoring config space at offset 0xf (was 0x4020100, writing 0x4020105)
[ 6044.952284] ohci1394 0000:03:01.0: restoring config space at offset 0x3 (was 0x800000, writing 0x804010)
[ 6044.952294] ohci1394 0000:03:01.0: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
[ 6045.004913] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[f1aff800-f1afffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[ 6045.024243] sdhci-pci 0000:03:01.1: restoring config space at offset 0xf (was 0x200, writing 0x204)
[ 6045.024274] sdhci-pci 0000:03:01.1: restoring config space at offset 0x4 (was 0x0, writing 0xf1aff400)
[ 6045.024283] sdhci-pci 0000:03:01.1: restoring config space at offset 0x3 (was 0x800000, writing 0x804010)
[ 6045.024294] sdhci-pci 0000:03:01.1: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
[ 6045.024319] sdhci-pci 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[ 6045.025342] ricoh-mmc: Resuming.
[ 6045.025351] ricoh-mmc: Controller is now disabled.
[ 6045.025363] pci 0000:03:01.3: restoring config space at offset 0xf (was 0x200, writing 0x204)
[ 6045.025385] pci 0000:03:01.3: restoring config space at offset 0x4 (was 0x0, writing 0xf1aff700)
[ 6045.025390] pci 0000:03:01.3: restoring config space at offset 0x3 (was 0x800000, writing 0x804010)
[ 6045.025397] pci 0000:03:01.3: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
[ 6045.025550] sd 0:0:0:0: [sda] Starting disk
[ 6046.804249] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 6046.856295] ata1.00: configured for UDMA/133
[ 6046.872305] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[ 6046.872336] sd 0:0:0:0: [sda] Write Protect is off
[ 6046.872340] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 6046.872384] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 6048.020249] usb 2-6: reset high speed USB device using ehci_hcd and address 3
[ 6048.324067] usb 3-2: reset full speed USB device using uhci_hcd and address 2
[ 6048.800067] usb 7-1: reset full speed USB device using uhci_hcd and address 2
[ 6049.025298] usb 3-2.1: reset full speed USB device using uhci_hcd and address 3
[ 6049.209298] usb 3-2.2: reset full speed USB device using uhci_hcd and address 4
[ 6049.397297] usb 3-2.3: reset full speed USB device using uhci_hcd and address 5
[ 6049.510678] PM: resume devices took 5.516 seconds
[ 6049.510683] ------------[ cut here ]------------
[ 6049.510685] WARNING: at /build/buildd/linux-2.6.28/kernel/power/main.c:177 suspend_test_finish+0x80/0x90()
[ 6049.510687] Component: resume devices
[ 6049.510688] Modules linked in: binfmt_misc ppdev bridge stp bnep vboxnetflt vboxdrv input_polldev lp parport joydev snd_hda_intel arc4 snd_pcm_oss ecb snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss iwlagn iwlcore snd_seq_midi snd_rawmidi uvcvideo video iTCO_wdt dcdbas led_class ricoh_mmc sdhci_pci sdhci psmouse serio_raw snd_seq_midi_event snd_seq snd_timer snd_seq_device pcspkr compat_ioctl32 videodev v4l1_compat nvidia(P) output iTCO_vendor_support mac80211 snd intel_agp agpgart btusb soundcore snd_page_alloc cfg80211 usbhid ohci1394 ieee1394 tg3 fbcon tileblit font bitblit softcursor
[ 6049.510723] Pid: 17890, comm: pm-suspend Tainted: P           2.6.28-13-generic #44-Ubuntu
[ 6049.510724] Call Trace:
[ 6049.510729]  [<c0139ab0>] warn_slowpath+0x60/0x80
[ 6049.510732]  [<c015381a>] ? down_trylock+0x2a/0x40
[ 6049.510734]  [<c013a10d>] ? try_acquire_console_sem+0xd/0x30
[ 6049.510738]  [<c02c72e0>] ? kobject_put+0x20/0x50
[ 6049.510742]  [<c04fca36>] ? printk+0x18/0x1a
[ 6049.510744]  [<c0164ff0>] suspend_test_finish+0x80/0x90
[ 6049.510747]  [<c01650c6>] suspend_devices_and_enter+0xc6/0x160
[ 6049.510749]  [<c04fca36>] ? printk+0x18/0x1a
[ 6049.510752]  [<c0165349>] enter_state+0xc9/0x100
[ 6049.510754]  [<c01653fd>] state_store+0x7d/0xc0
[ 6049.510756]  [<c0165380>] ? state_store+0x0/0xc0
[ 6049.510759]  [<c02c71a4>] kobj_attr_store+0x24/0x30
[ 6049.510762]  [<c020ab22>] sysfs_write_file+0x92/0xf0
[ 6049.510765]  [<c01bdad8>] vfs_write+0x98/0x110
[ 6049.510767]  [<c020aa90>] ? sysfs_write_file+0x0/0xf0
[ 6049.510770]  [<c01bdc0d>] sys_write+0x3d/0x70
[ 6049.510772]  [<c0103f6b>] sysenter_do_call+0x12/0x2f
[ 6049.510774] ---[ end trace b8b3a742e36dafec ]---
[ 6049.511020] PM: Finishing wakeup.
[ 6049.511021] Restarting tasks ... <6>synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[ 6049.620596] done.
[ 6050.413713] tg3 0000:09:00.0: irq 2296 for MSI/MSI-X
[ 6050.467442] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 6050.686097] Registered led device: iwl-phy0:radio
[ 6050.686121] Registered led device: iwl-phy0:assoc
[ 6050.686135] Registered led device: iwl-phy0:RX
[ 6050.686152] Registered led device: iwl-phy0:TX
[ 6050.722905] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6050.750282] wlan0: direct probe to AP 00:19:5b:df:83:cc try 1
[ 6050.752695] wlan0 direct probe responded
[ 6050.752698] wlan0: authenticate with AP 00:19:5b:df:83:cc
[ 6050.755568] wlan0: authenticated
[ 6050.755571] wlan0: associate with AP 00:19:5b:df:83:cc
[ 6050.757600] wlan0: RX AssocResp from 00:19:5b:df:83:cc (capab=0x421 status=0 aid=3)
[ 6050.757603] wlan0: associated
[ 6050.777863] phy0: failed to restore operational channel after scan
[ 6050.778028] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 6050.778407] wlan0: disassociating by local choice (reason=3)
[ 6051.206628] phy0: failed to restore operational channel after scan
[ 6061.736048] wlan0: no IPv6 routers present
[ 6064.911410] wlan0: deauthenticated
[ 6064.920544] wlan0: authenticate with AP 00:19:5b:df:83:cc
[ 6064.936311] wlan0: authenticate with AP 00:19:5b:df:83:cc
[ 6064.938657] wlan0: authenticated
[ 6064.938665] wlan0: associate with AP 00:19:5b:df:83:cc
[ 6064.940841] wlan0: RX ReassocResp from 00:19:5b:df:83:cc (capab=0x421 status=0 aid=3)
[ 6064.940846] wlan0: associated
[ 7120.972010] CE: hpet increasing min_delta_ns to 33750 nsec
[ 9248.820088] CE: hpet increasing min_delta_ns to 50624 nsec
[33086.011979] wlan0: disassociating by local choice (reason=3)
[33086.072586] iwlagn: MAC is in deep sleep!
[33088.735112] PM: Syncing filesystems ... done.
[33088.747286] PM: Preparing system for mem sleep
[33088.747291] Freezing user space processes ... (elapsed 0.00 seconds) done.
[33088.753046] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
[33088.764240] PM: Entering mem sleep
[33088.764250] Suspending console(s) (use no_console_suspend to debug)
[33088.801277] btusb_intr_complete: hci0 urb f0564b00 failed to resubmit (1)
[33088.802269] btusb_bulk_complete: hci0 urb f0564c00 failed to resubmit (2)
[33088.802280] btusb_bulk_complete: hci0 urb f0564a80 failed to resubmit (1)
[33089.628462] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[33089.628669] sd 0:0:0:0: [sda] Stopping disk
[33089.987522] ricoh-mmc: Suspending.
[33089.987533] ricoh-mmc: Controller is now re-enabled.
[33089.988615] ACPI handle has no context!
[33089.988622] sdhci-pci 0000:03:01.1: PCI INT B disabled
[33089.988628] ACPI handle has no context!
[33090.040301] NVRM: RmPowerManagement: 4
[33090.188321] ata5: port disabled. ignoring.
[33090.188399] ata_piix 0000:00:1f.1: PCI INT A disabled
[33090.188569] ehci_hcd 0000:00:1d.7: PCI INT A disabled
[33090.204287] uhci_hcd 0000:00:1d.2: PCI INT C disabled
[33090.204341] uhci_hcd 0000:00:1d.1: PCI INT B disabled
[33090.204394] uhci_hcd 0000:00:1d.0: PCI INT A disabled
[33090.236258] HDA Intel 0000:00:1b.0: PCI INT A disabled
[33090.252308] ehci_hcd 0000:00:1a.7: PCI INT C disabled
[33090.268285] uhci_hcd 0000:00:1a.1: PCI INT B disabled
[33090.268338] uhci_hcd 0000:00:1a.0: PCI INT A disabled
[33090.268491] PM: suspend devices took 1.504 seconds
[33090.272939] ACPI: Preparing to enter system sleep state S3
[33090.274569] Disabling non-boot CPUs ...
[33090.380018] CPU 1 is now offline
[33090.380021] SMP alternatives: switching to UP code
[33090.505023] CPU0 attaching NULL sched-domain.
[33090.505026] CPU1 attaching NULL sched-domain.
[33090.505238] CPU0 attaching NULL sched-domain.
[33090.505385] CPU1 is down
[33090.505475] Extended CMOS year: 2000
[33090.505475] Back to C!
[33090.505475] Extended CMOS year: 2000
[33090.505475] Enabling non-boot CPUs ...
[33090.505475] SMP alternatives: switching to SMP code
[33090.629294] Booting processor 1 APIC 0x1 ip 0x6000
[33090.504902] Initializing CPU#1
[33090.504902] Calibrating delay using timer specific routine.. 4322.61 BogoMIPS (lpj=8645238)
[33090.504902] CPU: L1 I cache: 32K, L1 D cache: 32K
[33090.504902] CPU: L2 cache: 2048K
[33090.504902] CPU: Physical Processor ID: 0
[33090.504902] CPU: Processor Core ID: 1
[33090.720413] CPU1: Intel(R) Core(TM)2 Duo CPU     T5850  @ 2.16GHz stepping 0d
[33090.720468] CPU0 attaching NULL sched-domain.
[33090.721010] CPU0 attaching sched-domain:
[33090.721013]  domain 0: span 0-1 level MC
[33090.721016] Switched to high resolution mode on CPU 1
[33090.721018]   groups: 0 1
[33090.721022] CPU1 attaching sched-domain:
[33090.721023]  domain 0: span 0-1 level MC
[33090.721025]   groups: 1 0
[33090.724022] CPU1 is up
[33090.724024] ACPI: Waking up from system sleep state S3
[33090.748780] pcieport-driver 0000:00:01.0: restoring config space at offset 0xf (was 0x100, writing 0x1a0100)
[33090.748786] pcieport-driver 0000:00:01.0: restoring config space at offset 0xa (was 0xf, writing 0x0)
[33090.748790] pcieport-driver 0000:00:01.0: restoring config space at offset 0x9 (was 0x1fff1, writing 0xeff1e001)
[33090.748793] pcieport-driver 0000:00:01.0: restoring config space at offset 0x8 (was 0xfea0fa00, writing 0xf6e0f200)
[33090.748797] pcieport-driver 0000:00:01.0: restoring config space at offset 0x7 (was 0xf0, writing 0x2000e0e0)
[33090.748800] pcieport-driver 0000:00:01.0: restoring config space at offset 0x6 (was 0x0, writing 0x10100)
[33090.748805] pcieport-driver 0000:00:01.0: restoring config space at offset 0x3 (was 0x10000, writing 0x10010)
[33090.748809] pcieport-driver 0000:00:01.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100507)
[33090.748831] pcieport-driver 0000:00:01.0: setting latency timer to 64
[33090.748841] uhci_hcd 0000:00:1a.0: enabling device (0000 -> 0001)
[33090.748847] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[33090.748853] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[33090.748860] uhci_hcd 0000:00:1a.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[33090.748875] uhci_hcd 0000:00:1a.0: restoring config space at offset 0x8 (was 0x1, writing 0x6f21)
[33090.748916] usb usb3: root hub lost power or was reset
[33090.748937] uhci_hcd 0000:00:1a.1: enabling device (0000 -> 0001)
[33090.748942] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[33090.748953] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[33090.748962] uhci_hcd 0000:00:1a.1: restoring config space at offset 0xf (was 0x200, writing 0x20a)
[33090.748978] uhci_hcd 0000:00:1a.1: restoring config space at offset 0x8 (was 0x1, writing 0x6f01)
[33090.749017] usb usb4: root hub lost power or was reset
[33090.764240] ehci_hcd 0000:00:1a.7: enabling device (0000 -> 0002)
[33090.764247] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[33090.764258] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[33090.764279] ehci_hcd 0000:00:1a.7: restoring config space at offset 0xf (was 0x300, writing 0x309)
[33090.764309] ehci_hcd 0000:00:1a.7: restoring config space at offset 0x4 (was 0x0, writing 0xfed1c400)
[33090.764322] ehci_hcd 0000:00:1a.7: restoring config space at offset 0x1 (was 0x2900006, writing 0x2900106)
[33090.780264] HDA Intel 0000:00:1b.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[33090.780294] HDA Intel 0000:00:1b.0: restoring config space at offset 0x4 (was 0xfebfc004, writing 0xf6ffc004)
[33090.780302] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[33090.780313] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100102)
[33090.780343] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[33090.780353] HDA Intel 0000:00:1b.0: setting latency timer to 64
[33090.780396] pcieport-driver 0000:00:1c.0: restoring config space at offset 0xf (was 0x100, writing 0x20100)
[33090.780416] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
[33090.780424] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x8 (was 0x0, writing 0xfff0)
[33090.780433] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x7 (was 0x0, writing 0xf0)
[33090.780441] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x6 (was 0x0, writing 0xb0b00)
[33090.780457] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[33090.780464] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[33090.780508] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[33090.780527] pcieport-driver 0000:00:1c.1: restoring config space at offset 0xf (was 0x200, writing 0x20200)
[33090.780540] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
[33090.780546] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x8 (was 0x0, writing 0xf1f0f1f0)
[33090.780551] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x7 (was 0x0, writing 0xf0)
[33090.780557] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x6 (was 0x0, writing 0xc0c00)
[33090.780566] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[33090.780573] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100507)
[33090.780617] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[33090.780637] pcieport-driver 0000:00:1c.3: restoring config space at offset 0xf (was 0x400, writing 0x20400)
[33090.780650] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x9 (was 0x10001, writing 0xf011f001)
[33090.780656] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x8 (was 0x0, writing 0xf1e0f1c0)
[33090.780661] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x7 (was 0x0, writing 0xd0d0)
[33090.780666] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x6 (was 0x0, writing 0xe0d00)
[33090.780675] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[33090.780682] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[33090.780727] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[33090.780745] pcieport-driver 0000:00:1c.5: restoring config space at offset 0xf (was 0x200, writing 0x20200)
[33090.780759] pcieport-driver 0000:00:1c.5: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
[33090.780764] pcieport-driver 0000:00:1c.5: restoring config space at offset 0x8 (was 0x0, writing 0xf1b0f1b0)
[33090.780769] pcieport-driver 0000:00:1c.5: restoring config space at offset 0x7 (was 0x0, writing 0xf0)
[33090.780775] pcieport-driver 0000:00:1c.5: restoring config space at offset 0x6 (was 0x0, writing 0x90900)
[33090.780783] pcieport-driver 0000:00:1c.5: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[33090.780791] pcieport-driver 0000:00:1c.5: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[33090.780835] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[33090.780843] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[33090.780848] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[33090.780904] usb usb5: root hub lost power or was reset
[33090.780921] uhci_hcd 0000:00:1d.1: enabling device (0000 -> 0001)
[33090.780925] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[33090.780932] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[33090.780938] uhci_hcd 0000:00:1d.1: restoring config space at offset 0xf (was 0x200, writing 0x20a)
[33090.780953] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x8 (was 0x1, writing 0x6f61)
[33090.780993] usb usb6: root hub lost power or was reset
[33090.781019] uhci_hcd 0000:00:1d.2: enabling device (0000 -> 0001)
[33090.781026] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[33090.781037] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[33090.781047] uhci_hcd 0000:00:1d.2: restoring config space at offset 0xf (was 0x300, writing 0x309)
[33090.781065] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x8 (was 0x1, writing 0x6f41)
[33090.781104] usb usb7: root hub lost power or was reset
[33090.796241] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[33090.796249] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[33090.796352] pci 0000:00:1e.0: restoring config space at offset 0x9 (was 0x100f1, writing 0x1fff1)
[33090.796363] pci 0000:00:1e.0: restoring config space at offset 0x8 (was 0xa0, writing 0xf1a0f1a0)
[33090.796373] pci 0000:00:1e.0: restoring config space at offset 0x7 (was 0x2280e0f0, writing 0x228000f0)
[33090.796392] pci 0000:00:1e.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100107)
[33090.796416] pci 0000:00:1e.0: setting latency timer to 64
[33090.796472] pci 0000:00:1f.0: restoring config space at offset 0x1 (was 0x2100007, writing 0x2100107)
[33090.796492] ata_piix 0000:00:1f.1: restoring config space at offset 0xf (was 0x100, writing 0x107)
[33090.796518] ata_piix 0000:00:1f.1: restoring config space at offset 0x1 (was 0x2800005, writing 0x2880005)
[33090.796528] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[33090.796533] ata_piix 0000:00:1f.1: setting latency timer to 64
[33090.796579] ata4.00: _GTF evaluation failed (AE 0x1001)
[33090.796743] ata5: port disabled. ignoring.
[33090.812258] ahci 0000:00:1f.2: restoring config space at offset 0xf (was 0x200, writing 0x20a)
[33090.812277] ahci 0000:00:1f.2: restoring config space at offset 0x9 (was 0x0, writing 0xf6ffb800)
[33090.812301] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00000, writing 0x2b00407)
[33090.812358] ahci 0000:00:1f.2: setting latency timer to 64
[33090.812414] pci 0000:00:1f.3: restoring config space at offset 0xf (was 0x200, writing 0x20a)
[33090.812457] pci 0000:00:1f.3: restoring config space at offset 0x4 (was 0x0, writing 0xf6ffb700)
[33090.812468] pci 0000:00:1f.3: restoring config space at offset 0x1 (was 0x2800001, writing 0x2800103)
[33090.812571] NVRM: RmPowerManagement: 5
[33090.977845] ata4.00: configured for UDMA/33
[33091.136052] ata3: SATA link down (SStatus 0 SControl 300)
[33091.736268] iwlagn 0000:0c:00.0: enabling device (0000 -> 0002)
[33091.736416] iwlagn 0000:0c:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[33091.736485] iwlagn 0000:0c:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf1ffe004)
[33091.736512] iwlagn 0000:0c:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[33091.736530] iwlagn 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100506)
[33091.736724] tg3 0000:09:00.0: restoring config space at offset 0xc (was 0x0, writing 0xffb90000)
[33091.736776] tg3 0000:09:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[33091.736793] tg3 0000:09:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100106)
[33091.752253] ohci1394 0000:03:01.0: restoring config space at offset 0xf (was 0x4020100, writing 0x4020105)
[33091.752285] ohci1394 0000:03:01.0: restoring config space at offset 0x3 (was 0x800000, writing 0x804010)
[33091.752296] ohci1394 0000:03:01.0: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
[33091.804915] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[f1aff800-f1afffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[33091.824251] sdhci-pci 0000:03:01.1: restoring config space at offset 0xf (was 0x200, writing 0x204)
[33091.824282] sdhci-pci 0000:03:01.1: restoring config space at offset 0x4 (was 0x0, writing 0xf1aff400)
[33091.824291] sdhci-pci 0000:03:01.1: restoring config space at offset 0x3 (was 0x800000, writing 0x804010)
[33091.824302] sdhci-pci 0000:03:01.1: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
[33091.824327] sdhci-pci 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[33091.825351] ricoh-mmc: Resuming.
[33091.825361] ricoh-mmc: Controller is now disabled.
[33091.825373] pci 0000:03:01.3: restoring config space at offset 0xf (was 0x200, writing 0x204)
[33091.825395] pci 0000:03:01.3: restoring config space at offset 0x4 (was 0x0, writing 0xf1aff700)
[33091.825400] pci 0000:03:01.3: restoring config space at offset 0x3 (was 0x800000, writing 0x804010)
[33091.825407] pci 0000:03:01.3: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
[33091.825565] sd 0:0:0:0: [sda] Starting disk
[33093.600241] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[33093.665135] ata1.00: configured for UDMA/133
[33093.680300] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[33093.680333] sd 0:0:0:0: [sda] Write Protect is off
[33093.680337] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[33093.680384] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[33094.828244] usb 2-6: reset high speed USB device using ehci_hcd and address 3
[33095.132069] usb 3-2: reset full speed USB device using uhci_hcd and address 2
[33095.608069] usb 7-1: reset full speed USB device using uhci_hcd and address 2
[33095.833300] usb 3-2.1: reset full speed USB device using uhci_hcd and address 3
[33096.017300] usb 3-2.2: reset full speed USB device using uhci_hcd and address 4
[33096.205300] usb 3-2.3: reset full speed USB device using uhci_hcd and address 5
[33096.319681] PM: resume devices took 5.584 seconds
[33096.319686] ------------[ cut here ]------------
[33096.319688] WARNING: at /build/buildd/linux-2.6.28/kernel/power/main.c:177 suspend_test_finish+0x80/0x90()
[33096.319689] Component: resume devices
[33096.319691] Modules linked in: binfmt_misc ppdev bridge stp bnep vboxnetflt vboxdrv input_polldev lp parport joydev snd_hda_intel arc4 snd_pcm_oss ecb snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss iwlagn iwlcore snd_seq_midi snd_rawmidi uvcvideo video iTCO_wdt dcdbas led_class ricoh_mmc sdhci_pci sdhci psmouse serio_raw snd_seq_midi_event snd_seq snd_timer snd_seq_device pcspkr compat_ioctl32 videodev v4l1_compat nvidia(P) output iTCO_vendor_support mac80211 snd intel_agp agpgart btusb soundcore snd_page_alloc cfg80211 usbhid ohci1394 ieee1394 tg3 fbcon tileblit font bitblit softcursor
[33096.319724] Pid: 31824, comm: pm-suspend Tainted: P        W  2.6.28-13-generic #44-Ubuntu
[33096.319726] Call Trace:
[33096.319731]  [<c0139ab0>] warn_slowpath+0x60/0x80
[33096.319734]  [<c015381a>] ? down_trylock+0x2a/0x40
[33096.319736]  [<c013a10d>] ? try_acquire_console_sem+0xd/0x30
[33096.319740]  [<c02c72e0>] ? kobject_put+0x20/0x50
[33096.319744]  [<c04fca36>] ? printk+0x18/0x1a
[33096.319746]  [<c0164ff0>] suspend_test_finish+0x80/0x90
[33096.319749]  [<c01650c6>] suspend_devices_and_enter+0xc6/0x160
[33096.319751]  [<c04fca36>] ? printk+0x18/0x1a
[33096.319754]  [<c0165349>] enter_state+0xc9/0x100
[33096.319756]  [<c01653fd>] state_store+0x7d/0xc0
[33096.319758]  [<c0165380>] ? state_store+0x0/0xc0
[33096.319761]  [<c02c71a4>] kobj_attr_store+0x24/0x30
[33096.319764]  [<c020ab22>] sysfs_write_file+0x92/0xf0
[33096.319767]  [<c01bdad8>] vfs_write+0x98/0x110
[33096.319769]  [<c020aa90>] ? sysfs_write_file+0x0/0xf0
[33096.319772]  [<c01bdc0d>] sys_write+0x3d/0x70
[33096.319774]  [<c0103f6b>] sysenter_do_call+0x12/0x2f
[33096.319776] ---[ end trace b8b3a742e36dafec ]---
[33096.320059] PM: Finishing wakeup.
[33096.320061] Restarting tasks ... done.
[33096.397998] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[33097.708273] tg3 0000:09:00.0: irq 2296 for MSI/MSI-X
[33097.762315] ADDRCONF(NETDEV_UP): eth0: link is not ready
[33097.985592] Registered led device: iwl-phy0:radio
[33097.985622] Registered led device: iwl-phy0:assoc
[33097.985637] Registered led device: iwl-phy0:RX
[33097.985651] Registered led device: iwl-phy0:TX
[33098.055042] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[33098.069657] wlan0: direct probe to AP 00:19:5b:df:83:cc try 1
[33098.071619] wlan0 direct probe responded
[33098.071622] wlan0: authenticate with AP 00:19:5b:df:83:cc
[33098.073376] wlan0: authenticated
[33098.073380] wlan0: associate with AP 00:19:5b:df:83:cc
[33098.272014] wlan0: associate with AP 00:19:5b:df:83:cc
[33098.472041] wlan0: associate with AP 00:19:5b:df:83:cc
[33098.673045] wlan0: association with AP 00:19:5b:df:83:cc timed out
[33099.702707] wlan0: authenticate with AP 00:19:5b:df:83:cc
[33099.708487] wlan0: authenticate with AP 00:19:5b:df:83:cc
[33099.708507] wlan0: authenticated
[33099.708510] wlan0: associate with AP 00:19:5b:df:83:cc
[33099.715177] wlan0: RX AssocResp from 00:19:5b:df:83:cc (capab=0x421 status=0 aid=4)
[33099.715180] wlan0: associated
[33099.745451] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[33109.956064] wlan0: no IPv6 routers present
```

---

### Post by sinnadyr on 2009-06-23
bump

---

