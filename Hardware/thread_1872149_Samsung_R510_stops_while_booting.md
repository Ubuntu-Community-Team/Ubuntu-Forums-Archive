---
title: "Samsung R510 stops while booting"
date: 2011-10-30
forum: Hardware
---

### Post by DillerDaller on 2011-10-30
Hi,

I have a Samsung R510 Laptop.
Hardware:
Intel Core 2 Duo Processor T5800, 2GHz, 4096 MB RAM
Chipset: Intel PM45+ICH9M
Graphic: NVIDIA Geforce 9200 GS
Audio: Intel HD Audio Codec, Realtek ALC262-V2GR

I tried to install Ubuntu 11.10 (32bit) on a 32Gb USB Stick, but I had some problems while booting from USB-Stick. When I boot the PC, my Laptop stops while boot process. First, I create a Live-CD then boor from CD and klck "install Ubuntu". The bootloader is installed on the USB-Stick. 3 Partitions are made: The first (10GB, ext4) for Linux, the second about 8GB for SWAP and the third (about 10GB, Fat32) for general use. Installation works fine, I also download the updates while installing. The Live-CD (2bit) works fine....
 
Here the boot.log:
```
fsck from util-linux 2.19.1 
/dev/sdb1: sauber, 155260/625856 Dateien, 824426/2499840 Blöcke 
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox 
 * Starting AppArmor profiles       [80G  [74G[ OK ] 
speech-dispatcher disabled; edit /etc/default/speech-dispatcher 
Checking for running unattended-upgrades:  
 * Starting bluetooth       [80G  [74G[ OK ] 
 [33m*[39;49m PulseAudio configured for per-user sessions 
saned disabled; edit /etc/default/saned
```The dmesg file contains following lines:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-12-generic-pae (buildd@vernadsky) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #20-Ubuntu SMP Fri Oct 7 16:37:17 UTC 2011 (Ubuntu 3.0.0-12.20-generic-pae 3.0.4)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e400 (usable)
[    0.000000]  BIOS-e820: 000000000009e400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf8a1000 (usable)
[    0.000000]  BIOS-e820: 00000000bf8a1000 - 00000000bf8a7000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf8a7000 - 00000000bf9b4000 (usable)
[    0.000000]  BIOS-e820: 00000000bf9b4000 - 00000000bfa0f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfa0f000 - 00000000bfb07000 (usable)
[    0.000000]  BIOS-e820: 00000000bfb07000 - 00000000bfd0f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfd0f000 - 00000000bfd18000 (usable)
[    0.000000]  BIOS-e820: 00000000bfd18000 - 00000000bfd1f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfd1f000 - 00000000bfd65000 (usable)
[    0.000000]  BIOS-e820: 00000000bfd65000 - 00000000bfd9f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfd9f000 - 00000000bfe00000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] DMI: SAMSUNG ELECTRONICS CO., LTD. R510/P510                  /R510/P510                  , BIOS 07LI.MP00.20080926.SCY 09/26/2008
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   1 base 000000000 mask F00000000 write-back
[    0.000000]   2 base 100000000 mask FC0000000 write-back
[    0.000000]   3 base 0BFE00000 mask FFFE00000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 3GB, range: 1GB, type UC
[    0.000000] reg 1, base: 0GB, range: 4GB, type WB
[    0.000000] reg 2, base: 4GB, range: 1GB, type WB
[    0.000000] reg 3, base: 3070MB, range: 2MB, type UC
[    0.000000] total RAM covered: 4094M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 4M     num_reg: 4      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3070MB, range: 2MB, type UC
[    0.000000] reg 3, base: 4GB, range: 1GB, type WB
[    0.000000] e820 update range: 00000000bfe00000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] found SMP MP-table at [c00f7380] f7380
[    0.000000] initial memory mapped : 0 - 02000000
[    0.000000] Base memory trampoline at [c009a000] 9a000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 1ffb000-2000000
[    0.000000] RAMDISK: 365f0000 - 372f0000
[    0.000000] ACPI: RSDP 000f72e0 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT bfdf8657 0006C (v01 SECCSD LH43STAR 06040000  LTP 00000000)
[    0.000000] ACPI: FACP bfde8000 000F4 (v03 INTEL  CRESTLNE 06040000 ALAN 00000001)
[    0.000000] ACPI: DSDT bfde9000 06533 (v02 Intel  CANTIGA  06040000 INTL 20050624)
[    0.000000] ACPI: FACS bfd9efc0 00040
[    0.000000] ACPI: HPET bfdfed86 00038 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG bfdfedbe 0003C (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: APIC bfdfedfa 00068 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT bfdfee62 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SLIC bfdfee8a 00176 (v01 SECCSD LH43STAR 06040000  LTP 00000000)
[    0.000000] ACPI: SSDT bfde7000 005F9 (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT bfde6000 00259 (v01  PmRef  Cpu0Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT bfde5000 0020F (v01  PmRef    ApTst 00003000 INTL 20050624)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 4228MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037bfe
[    0.000000]   HighMem  0x00037bfe -> 0x00140000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[7] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000bf8a1
[    0.000000]     0: 0x000bf8a7 -> 0x000bf9b4
[    0.000000]     0: 0x000bfa0f -> 0x000bfb07
[    0.000000]     0: 0x000bfd0f -> 0x000bfd18
[    0.000000]     0: 0x000bfd1f -> 0x000bfd65
[    0.000000]     0: 0x00100000 -> 0x00140000
[    0.000000] On node 0 totalpages: 1047171
[    0.000000] free_area_init_node: node 0, pgdat c17e9f40, node_mem_map f3df0200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3950 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 8457 pages used for memmap
[    0.000000]   HighMem zone: 810478 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at bfe00000 (gap: bfe00000:40200000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f7800000 s29952 r0 d23296 u1048576
[    0.000000] pcpu-alloc: s29952 r0 d23296 u1048576 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1036930
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic-pae root=UUID=8e7603e0-8b9e-41cd-889b-5e54d0455b59 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 20971264 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:00140000)
[    0.000000] Memory: 4103120k/5242880k available (5494k kernel code, 85564k reserved, 2653k data, 720k init, 3275740k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc17f6000 - 0xc18aa000   ( 720 kB)
[    0.000000]       .data : 0xc155d9b0 - 0xc17f5180   (2653 kB)
[    0.000000]       .text : 0xc1000000 - 0xc155d9b0   (5494 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f7408000 soft=f740a000
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1995.017 MHz processor.
[    0.004003] Calibrating delay loop (skipped), value calculated using timer frequency.. 3990.03 BogoMIPS (lpj=7980068)
[    0.004009] pid_max: default: 32768 minimum: 301
[    0.004031] Security Framework initialized
[    0.004048] AppArmor: AppArmor initialized
[    0.004050] Yama: becoming mindful.
[    0.004107] Mount-cache hash table entries: 512
[    0.004245] Initializing cgroup subsys cpuacct
[    0.004252] Initializing cgroup subsys memory
[    0.004260] Initializing cgroup subsys devices
[    0.004262] Initializing cgroup subsys freezer
[    0.004265] Initializing cgroup subsys net_cls
[    0.004267] Initializing cgroup subsys blkio
[    0.004275] Initializing cgroup subsys perf_event
[    0.004308] CPU: Physical Processor ID: 0
[    0.004310] CPU: Processor Core ID: 0
[    0.004313] mce: CPU supports 6 MCE banks
[    0.004321] CPU0: Thermal monitoring enabled (TM2)
[    0.004325] using mwait in idle threads.
[    0.006471] ACPI: Core revision 20110413
[    0.008831] CPU0: Core temperature above threshold, cpu clock throttled (total events = 1)
[    0.009485] CPU0: Core temperature/speed normal
[    0.016014] ftrace: allocating 25582 entries in 51 pages
[    0.020074] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.020453] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.061408] CPU0: Intel(R) Core(TM)2 Duo CPU     T5800  @ 2.00GHz stepping 0d
[    0.064003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.064003] PEBS disabled due to CPU errata.
[    0.064003] ... version:                2
[    0.064003] ... bit width:              40
[    0.064003] ... generic registers:      2
[    0.064003] ... value mask:             000000ffffffffff
[    0.064003] ... max period:             000000007fffffff
[    0.064003] ... fixed-purpose events:   3
[    0.064003] ... event mask:             0000000700000003
[    0.064003] CPU 1 irqstacks, hard=f74ca000 soft=f74cc000
[    0.064003] Booting Node   0, Processors  #1 Ok.
[    0.064003] smpboot cpu 1: start_ip = 9a000
[    0.008000] Initializing CPU#1
[    0.152023] Brought up 2 CPUs
[    0.152026] Total of 2 processors activated (7981.88 BogoMIPS).
[    0.152993] devtmpfs: initialized
[    0.152993] PM: Registering ACPI NVS region at bfd65000 (237568 bytes)
[    0.154612] print_constraints: dummy: 
[    0.154652] Time: 15:50:46  Date: 10/29/11
[    0.154726] NET: Registered protocol family 16
[    0.156090] Trying to unpack rootfs image as initramfs...
[    0.156246] EISA bus registered
[    0.156271] ACPI: bus type pci registered
[    0.156364] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.156368] PCI: not using MMCONFIG
[    0.156525] PCI : PCI BIOS aera is rw and x. Use pci=nobios if you want it NX.
[    0.156784] PCI: PCI BIOS revision 3.00 entry at 0xfde11, last bus=8
[    0.156786] PCI: Using configuration type 1 for base access
[    0.158000] bio: create slab <bio-0> at 0
[    0.160558] ACPI: EC: Look up EC in DSDT
[    0.166085] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.168237] ACPI: SSDT bfd1ac20 00265 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.168982] ACPI: Dynamic OEM Table Load:
[    0.168989] ACPI: SSDT   (null) 00265 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.169256] ACPI: SSDT bfd18020 00C78 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.169695] ACPI: Dynamic OEM Table Load:
[    0.169698] ACPI: SSDT   (null) 00C78 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.220559] ACPI: SSDT bfd19ca0 001CF (v01  PmRef    ApIst 00003000 INTL 20050624)
[    0.221173] ACPI: Dynamic OEM Table Load:
[    0.221179] ACPI: SSDT   (null) 001CF (v01  PmRef    ApIst 00003000 INTL 20050624)
[    0.252242] ACPI: SSDT bfd19f20 0008D (v01  PmRef    ApCst 00003000 INTL 20050624)
[    0.252801] ACPI: Dynamic OEM Table Load:
[    0.252805] ACPI: SSDT   (null) 0008D (v01  PmRef    ApCst 00003000 INTL 20050624)
[    0.284754] ACPI: Interpreter enabled
[    0.284754] ACPI: (supports S0 S3 S4 S5)
[    0.284754] ACPI: Using IOAPIC for interrupt routing
[    0.284754] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.285441] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.285444] PCI: Using MMCONFIG for extended config space
[    0.286089] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.292490] ACPI: Power Resource [FN00] (off)
[    0.292612] ACPI: Power Resource [FN01] (off)
[    0.293039] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.293316] ACPI: No dock devices found.
[    0.293320] HEST: Table not found.
[    0.293328] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.293900] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.294610] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.294614] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.294617] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.294620] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.294623] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.294627] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xfebfffff]
[    0.294645] pci 0000:00:00.0: [8086:2a40] type 0 class 0x000600
[    0.294675] DMAR: Forcing write-buffer flush capability
[    0.294677] DMAR: Disabling IOMMU for graphics on this chipset
[    0.294705] pci 0000:00:01.0: [8086:2a41] type 1 class 0x000604
[    0.294749] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.294753] pci 0000:00:01.0: PME# disabled
[    0.294829] pci 0000:00:1a.0: [8086:2937] type 0 class 0x000c03
[    0.294920] pci 0000:00:1a.0: reg 20: [io  0x1800-0x181f]
[    0.295011] pci 0000:00:1a.1: [8086:2938] type 0 class 0x000c03
[    0.295081] pci 0000:00:1a.1: reg 20: [io  0x1820-0x183f]
[    0.295157] pci 0000:00:1a.2: [8086:2939] type 0 class 0x000c03
[    0.295236] pci 0000:00:1a.2: reg 20: [io  0x1840-0x185f]
[    0.295325] pci 0000:00:1a.7: [8086:293c] type 0 class 0x000c03
[    0.295363] pci 0000:00:1a.7: reg 10: [mem 0xf6204800-0xf6204bff]
[    0.295491] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.295500] pci 0000:00:1a.7: PME# disabled
[    0.295540] pci 0000:00:1b.0: [8086:293e] type 0 class 0x000403
[    0.295568] pci 0000:00:1b.0: reg 10: [mem 0xf6200000-0xf6203fff 64bit]
[    0.295667] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.295672] pci 0000:00:1b.0: PME# disabled
[    0.295702] pci 0000:00:1c.0: [8086:2940] type 1 class 0x000604
[    0.295796] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.295801] pci 0000:00:1c.0: PME# disabled
[    0.295835] pci 0000:00:1c.2: [8086:2944] type 1 class 0x000604
[    0.296051] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.296057] pci 0000:00:1c.2: PME# disabled
[    0.296090] pci 0000:00:1c.3: [8086:2946] type 1 class 0x000604
[    0.296183] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.296188] pci 0000:00:1c.3: PME# disabled
[    0.296227] pci 0000:00:1d.0: [8086:2934] type 0 class 0x000c03
[    0.296293] pci 0000:00:1d.0: reg 20: [io  0x1860-0x187f]
[    0.296362] pci 0000:00:1d.1: [8086:2935] type 0 class 0x000c03
[    0.296428] pci 0000:00:1d.1: reg 20: [io  0x1880-0x189f]
[    0.296494] pci 0000:00:1d.2: [8086:2936] type 0 class 0x000c03
[    0.296560] pci 0000:00:1d.2: reg 20: [io  0x18a0-0x18bf]
[    0.296652] pci 0000:00:1d.7: [8086:293a] type 0 class 0x000c03
[    0.296690] pci 0000:00:1d.7: reg 10: [mem 0xf6204c00-0xf6204fff]
[    0.296816] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.296824] pci 0000:00:1d.7: PME# disabled
[    0.296859] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.296960] pci 0000:00:1f.0: [8086:2919] type 0 class 0x000601
[    0.297158] pci 0000:00:1f.2: [8086:2929] type 0 class 0x000106
[    0.297193] pci 0000:00:1f.2: reg 10: [io  0x18f0-0x18f7]
[    0.297208] pci 0000:00:1f.2: reg 14: [io  0x18e4-0x18e7]
[    0.297223] pci 0000:00:1f.2: reg 18: [io  0x18e8-0x18ef]
[    0.297238] pci 0000:00:1f.2: reg 1c: [io  0x18e0-0x18e3]
[    0.297253] pci 0000:00:1f.2: reg 20: [io  0x18c0-0x18df]
[    0.297268] pci 0000:00:1f.2: reg 24: [mem 0xf6204000-0xf62047ff]
[    0.297338] pci 0000:00:1f.2: PME# supported from D3hot
[    0.297345] pci 0000:00:1f.2: PME# disabled
[    0.297379] pci 0000:00:1f.3: [8086:2930] type 0 class 0x000c05
[    0.297409] pci 0000:00:1f.3: reg 10: [mem 0x00000000-0x000000ff 64bit]
[    0.297447] pci 0000:00:1f.3: reg 20: [io  0x1c00-0x1c1f]
[    0.297559] pci 0000:01:00.0: [10de:06e8] type 0 class 0x000300
[    0.297581] pci 0000:01:00.0: reg 10: [mem 0xce000000-0xceffffff]
[    0.297604] pci 0000:01:00.0: reg 14: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.297626] pci 0000:01:00.0: reg 1c: [mem 0xcc000000-0xcdffffff 64bit]
[    0.297641] pci 0000:01:00.0: reg 24: [io  0x2000-0x207f]
[    0.297656] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.304043] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.304047] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    0.304051] pci 0000:00:01.0:   bridge window [mem 0xcc000000-0xceffffff]
[    0.304057] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.304149] pci 0000:02:00.0: [168c:001c] type 0 class 0x000200
[    0.304183] pci 0000:02:00.0: reg 10: [mem 0xf3000000-0xf300ffff 64bit]
[    0.304316] pci 0000:02:00.0: PME# supported from D3hot
[    0.304323] pci 0000:02:00.0: PME# disabled
[    0.304357] pci 0000:02:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.304370] pci 0000:00:1c.0: PCI bridge to [bus 02-03]
[    0.304376] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.304382] pci 0000:00:1c.0:   bridge window [mem 0xf3000000-0xf3ffffff]
[    0.304391] pci 0000:00:1c.0:   bridge window [mem 0xf0000000-0xf0ffffff 64bit pref]
[    0.304466] pci 0000:00:1c.2: PCI bridge to [bus 04-05]
[    0.304474] pci 0000:00:1c.2:   bridge window [io  0x4000-0x4fff]
[    0.304482] pci 0000:00:1c.2:   bridge window [mem 0xf4000000-0xf4ffffff]
[    0.304493] pci 0000:00:1c.2:   bridge window [mem 0xf1000000-0xf1ffffff 64bit pref]
[    0.304709] pci 0000:06:00.0: [11ab:4363] type 0 class 0x000200
[    0.304866] pci 0000:06:00.0: reg 10: [mem 0xf5000000-0xf5003fff 64bit]
[    0.304955] pci 0000:06:00.0: reg 18: [io  0x5000-0x50ff]
[    0.305278] pci 0000:06:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.305596] pci 0000:06:00.0: supports D1 D2
[    0.305598] pci 0000:06:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.305623] pci 0000:06:00.0: PME# disabled
[    0.312101] pci 0000:00:1c.3: PCI bridge to [bus 06-07]
[    0.312109] pci 0000:00:1c.3:   bridge window [io  0x5000-0x5fff]
[    0.312117] pci 0000:00:1c.3:   bridge window [mem 0xf5000000-0xf5ffffff]
[    0.312128] pci 0000:00:1c.3:   bridge window [mem 0xf2000000-0xf2ffffff 64bit pref]
[    0.312243] pci 0000:00:1e.0: PCI bridge to [bus 08-08] (subtractive decode)
[    0.312249] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.312254] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.312264] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.312267] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.312270] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.312273] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.312276] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.312279] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.312282] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xfebfffff] (subtractive decode)
[    0.312316] pci_bus 0000:00: on NUMA node 0
[    0.312323] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.312565] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    0.312679] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.312743] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.312799] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.312867]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.312870]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.312873] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.321419] ACPI: PCI Interrupt Link [LNKA] (IRQs *11)
[    0.321477] ACPI: PCI Interrupt Link [LNKB] (IRQs *10)
[    0.321530] ACPI: PCI Interrupt Link [LNKC] (IRQs *5)
[    0.321582] ACPI: PCI Interrupt Link [LNKD] (IRQs *5)
[    0.321633] ACPI: PCI Interrupt Link [LNKE] (IRQs 11) *0, disabled.
[    0.321686] ACPI: PCI Interrupt Link [LNKF] (IRQs *10)
[    0.321738] ACPI: PCI Interrupt Link [LNKG] (IRQs *5)
[    0.321789] ACPI: PCI Interrupt Link [LNKH] (IRQs *5)
[    0.322000] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.322008] vgaarb: loaded
[    0.322010] vgaarb: bridge control possible 0000:01:00.0
[    0.322399] SCSI subsystem initialized
[    0.322505] libata version 3.00 loaded.
[    0.322599] usbcore: registered new interface driver usbfs
[    0.322621] usbcore: registered new interface driver hub
[    0.322665] usbcore: registered new device driver usb
[    0.322764] PCI: Using ACPI for IRQ routing
[    0.323316] PCI: pci_cache_line_size set to 64 bytes
[    0.323514] reserve RAM buffer: 000000000009e400 - 000000000009ffff 
[    0.323519] reserve RAM buffer: 00000000bf8a1000 - 00000000bfffffff 
[    0.323528] reserve RAM buffer: 00000000bf9b4000 - 00000000bfffffff 
[    0.323535] reserve RAM buffer: 00000000bfb07000 - 00000000bfffffff 
[    0.323542] reserve RAM buffer: 00000000bfd18000 - 00000000bfffffff 
[    0.323548] reserve RAM buffer: 00000000bfd65000 - 00000000bfffffff 
[    0.323718] NetLabel: Initializing
[    0.323722] NetLabel:  domain hash size = 128
[    0.323725] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.323743] NetLabel:  unlabeled traffic allowed by default
[    0.323813] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.323823] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.323835] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.328437] Switching to clocksource hpet
[    0.331021] Switched to NOHz mode on CPU #0
[    0.331050] Switched to NOHz mode on CPU #1
[    0.339386] AppArmor: AppArmor Filesystem Enabled
[    0.339421] pnp: PnP ACPI init
[    0.339441] ACPI: bus type pnp registered
[    0.339986] pnp 00:00: [bus 00-ff]
[    0.339991] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.339996] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.340000] pnp 00:00: [io  0x0d00-0xffff window]
[    0.340005] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.340009] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.340014] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.340018] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.340042] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.340047] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.340051] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.340056] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.340060] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.340065] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.340069] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.340074] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.340078] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.340082] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.340087] pnp 00:00: [mem 0xc0000000-0xfebfffff window]
[    0.340092] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    0.340211] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.340469] pnp 00:01: [io  0x0000-0x001f]
[    0.340472] pnp 00:01: [io  0x0081-0x0091]
[    0.340474] pnp 00:01: [io  0x0093-0x009f]
[    0.340477] pnp 00:01: [io  0x00c0-0x00df]
[    0.340479] pnp 00:01: [dma 4]
[    0.340515] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.340526] pnp 00:02: [mem 0xff000000-0xffffffff]
[    0.340559] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    0.340665] pnp 00:03: [mem 0xfed00000-0xfed003ff]
[    0.340771] system 00:03: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.340778] system 00:03: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    0.340802] pnp 00:04: [io  0x00f0]
[    0.340818] pnp 00:04: [irq 13]
[    0.340878] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.340903] pnp 00:05: [io  0x002e-0x002f]
[    0.340907] pnp 00:05: [io  0x004e-0x004f]
[    0.340915] pnp 00:05: [io  0x0061]
[    0.340918] pnp 00:05: [io  0x0063]
[    0.340922] pnp 00:05: [io  0x0065]
[    0.340926] pnp 00:05: [io  0x0067]
[    0.340929] pnp 00:05: [io  0x0070]
[    0.340933] pnp 00:05: [io  0x0080]
[    0.340936] pnp 00:05: [io  0x0092]
[    0.340940] pnp 00:05: [io  0x00b2-0x00b3]
[    0.340944] pnp 00:05: [io  0x0680-0x069f]
[    0.340948] pnp 00:05: [io  0x0480-0x048f]
[    0.340952] pnp 00:05: [io  0xffff]
[    0.340956] pnp 00:05: [io  0xffff]
[    0.340959] pnp 00:05: [io  0x0400-0x047f]
[    0.340963] pnp 00:05: [io  0x0480-0x048f]
[    0.340967] pnp 00:05: [io  0x1180-0x11ff]
[    0.340971] pnp 00:05: [io  0x164e-0x164f]
[    0.340975] pnp 00:05: [io  0x5000-0x500f]
[    0.340979] pnp 00:05: [io  0xfe00]
[    0.341012] pnp 00:05: disabling [io  0x5000-0x500f] because it overlaps 0000:00:1c.3 BAR 13 [io  0x5000-0x5fff]
[    0.341051] pnp 00:05: disabling [io  0x5000-0x500f disabled] because it overlaps 0000:06:00.0 BAR 2 [io  0x5000-0x50ff]
[    0.341118] system 00:05: [io  0x0680-0x069f] has been reserved
[    0.341123] system 00:05: [io  0x0480-0x048f] has been reserved
[    0.341129] system 00:05: [io  0xffff] has been reserved
[    0.341134] system 00:05: [io  0xffff] has been reserved
[    0.341139] system 00:05: [io  0x0400-0x047f] has been reserved
[    0.341144] system 00:05: [io  0x0480-0x048f] has been reserved
[    0.341149] system 00:05: [io  0x1180-0x11ff] has been reserved
[    0.341154] system 00:05: [io  0x164e-0x164f] has been reserved
[    0.341159] system 00:05: [io  0xfe00] has been reserved
[    0.341165] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.341207] pnp 00:06: [io  0x06a0-0x06af]
[    0.341212] pnp 00:06: [io  0x06b0-0x06ff]
[    0.341308] system 00:06: [io  0x06a0-0x06af] has been reserved
[    0.341313] system 00:06: [io  0x06b0-0x06ff] has been reserved
[    0.341320] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.341339] pnp 00:07: [io  0x0070-0x0077]
[    0.341348] pnp 00:07: [irq 8]
[    0.341407] pnp 00:07: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.341430] pnp 00:08: [io  0x0060]
[    0.341434] pnp 00:08: [io  0x0064]
[    0.341443] pnp 00:08: [irq 1]
[    0.341489] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.341503] pnp 00:09: [irq 12]
[    0.341542] pnp 00:09: Plug and Play ACPI device, IDs PNP0f13 (active)
[    0.341670] pnp 00:0a: [mem 0xfed1c000-0xfed1ffff]
[    0.341673] pnp 00:0a: [mem 0xfed10000-0xfed13fff]
[    0.341675] pnp 00:0a: [mem 0xfed18000-0xfed18fff]
[    0.341677] pnp 00:0a: [mem 0xfed19000-0xfed19fff]
[    0.341680] pnp 00:0a: [mem 0xe0000000-0xefffffff]
[    0.341682] pnp 00:0a: [mem 0xfed20000-0xfed3ffff]
[    0.341685] pnp 00:0a: [mem 0xfed40000-0xfed44fff]
[    0.341687] pnp 00:0a: [mem 0xfed45000-0xfed8ffff]
[    0.341760] system 00:0a: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.341764] system 00:0a: [mem 0xfed10000-0xfed13fff] has been reserved
[    0.341767] system 00:0a: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.341770] system 00:0a: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.341774] system 00:0a: [mem 0xe0000000-0xefffffff] has been reserved
[    0.341777] system 00:0a: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.341780] system 00:0a: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.341783] system 00:0a: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.341787] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.342112] pnp: PnP ACPI: found 11 devices
[    0.342114] ACPI: ACPI bus type pnp unregistered
[    0.342119] PnPBIOS: Disabled by ACPI PNP
[    0.379463] PCI: max bus depth: 1 pci_try_num: 2
[    0.379534] pci 0000:00:1f.3: BAR 0: assigned [mem 0xc0000000-0xc00000ff 64bit]
[    0.379544] pci 0000:00:1f.3: BAR 0: set to [mem 0xc0000000-0xc00000ff 64bit] (PCI address [0xc0000000-0xc00000ff])
[    0.379551] pci 0000:01:00.0: BAR 6: can't assign mem pref (size 0x20000)
[    0.379554] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.379557] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    0.379562] pci 0000:00:01.0:   bridge window [mem 0xcc000000-0xceffffff]
[    0.379566] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.379573] pci 0000:00:1c.0: PCI bridge to [bus 02-03]
[    0.379577] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.379584] pci 0000:00:1c.0:   bridge window [mem 0xf3000000-0xf3ffffff]
[    0.379589] pci 0000:00:1c.0:   bridge window [mem 0xf0000000-0xf0ffffff 64bit pref]
[    0.379598] pci 0000:00:1c.2: PCI bridge to [bus 04-05]
[    0.379602] pci 0000:00:1c.2:   bridge window [io  0x4000-0x4fff]
[    0.379609] pci 0000:00:1c.2:   bridge window [mem 0xf4000000-0xf4ffffff]
[    0.379615] pci 0000:00:1c.2:   bridge window [mem 0xf1000000-0xf1ffffff 64bit pref]
[    0.379625] pci 0000:06:00.0: BAR 6: assigned [mem 0xf2000000-0xf201ffff pref]
[    0.379628] pci 0000:00:1c.3: PCI bridge to [bus 06-07]
[    0.379632] pci 0000:00:1c.3:   bridge window [io  0x5000-0x5fff]
[    0.379639] pci 0000:00:1c.3:   bridge window [mem 0xf5000000-0xf5ffffff]
[    0.379645] pci 0000:00:1c.3:   bridge window [mem 0xf2000000-0xf2ffffff 64bit pref]
[    0.379653] pci 0000:00:1e.0: PCI bridge to [bus 08-08]
[    0.379655] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.379662] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.379667] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.379696] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.379701] pci 0000:00:01.0: setting latency timer to 64
[    0.379713] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.379718] pci 0000:00:1c.0: setting latency timer to 64
[    0.379730] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.379736] pci 0000:00:1c.2: setting latency timer to 64
[    0.379750] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.379756] pci 0000:00:1c.3: setting latency timer to 64
[    0.379765] pci 0000:00:1e.0: setting latency timer to 64
[    0.379770] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.379773] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.379776] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.379779] pci_bus 0000:00: resource 7 [mem 0x000d4000-0x000d7fff]
[    0.379782] pci_bus 0000:00: resource 8 [mem 0x000d8000-0x000dbfff]
[    0.379784] pci_bus 0000:00: resource 9 [mem 0xc0000000-0xfebfffff]
[    0.379787] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
[    0.379790] pci_bus 0000:01: resource 1 [mem 0xcc000000-0xceffffff]
[    0.379793] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.379796] pci_bus 0000:02: resource 0 [io  0x3000-0x3fff]
[    0.379798] pci_bus 0000:02: resource 1 [mem 0xf3000000-0xf3ffffff]
[    0.379801] pci_bus 0000:02: resource 2 [mem 0xf0000000-0xf0ffffff 64bit pref]
[    0.379804] pci_bus 0000:04: resource 0 [io  0x4000-0x4fff]
[    0.379807] pci_bus 0000:04: resource 1 [mem 0xf4000000-0xf4ffffff]
[    0.379810] pci_bus 0000:04: resource 2 [mem 0xf1000000-0xf1ffffff 64bit pref]
[    0.379813] pci_bus 0000:06: resource 0 [io  0x5000-0x5fff]
[    0.379816] pci_bus 0000:06: resource 1 [mem 0xf5000000-0xf5ffffff]
[    0.379818] pci_bus 0000:06: resource 2 [mem 0xf2000000-0xf2ffffff 64bit pref]
[    0.379821] pci_bus 0000:08: resource 4 [io  0x0000-0x0cf7]
[    0.379824] pci_bus 0000:08: resource 5 [io  0x0d00-0xffff]
[    0.379827] pci_bus 0000:08: resource 6 [mem 0x000a0000-0x000bffff]
[    0.379830] pci_bus 0000:08: resource 7 [mem 0x000d4000-0x000d7fff]
[    0.379833] pci_bus 0000:08: resource 8 [mem 0x000d8000-0x000dbfff]
[    0.379836] pci_bus 0000:08: resource 9 [mem 0xc0000000-0xfebfffff]
[    0.379884] NET: Registered protocol family 2
[    0.379964] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.380362] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.380953] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.381242] TCP: Hash tables configured (established 131072 bind 65536)
[    0.381246] TCP reno registered
[    0.381252] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.381265] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.381414] NET: Registered protocol family 1
[    0.381704] pci 0000:01:00.0: Boot video device
[    0.381744] PCI: CLS 64 bytes, default 64
[    0.381753] Simple Boot Flag at 0x37 set to 0x1
[    0.382145] audit: initializing netlink socket (disabled)
[    0.382156] type=2000 audit(1319903446.380:1): initialized
[    0.420713] highmem bounce pool size: 64 pages
[    0.420720] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.436764] VFS: Disk quotas dquot_6.5.2
[    0.436845] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.437608] fuse init (API version 7.16)
[    0.437713] msgmni has been set to 1615
[    0.438214] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.438261] io scheduler noop registered
[    0.438265] io scheduler deadline registered
[    0.438291] io scheduler cfq registered (default)
[    0.438496] pcieport 0000:00:01.0: setting latency timer to 64
[    0.438556] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.438646] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.438721] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.438806] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.438867] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    0.438952] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.439012] pcieport 0000:00:1c.3: irq 43 for MSI/MSI-X
[    0.439123] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.439150] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.439233] intel_idle: MWAIT substates: 0x22220
[    0.439235] intel_idle: does not run on family 6 model 15
[    0.439433] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.439693] ACPI: AC Adapter [ADP1] (on-line)
[    0.439823] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.439854] ACPI: Lid Switch [LID0]
[    0.439933] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.439942] ACPI: Power Button [PWRB]
[    0.440037] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.440044] ACPI: Sleep Button [SLPB]
[    0.440126] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.440133] ACPI: Power Button [PWRF]
[    0.440249] ACPI: Fan [FAN0] (off)
[    0.440323] ACPI: Fan [FAN1] (off)
[    0.440337] ACPI: acpi_idle registered with cpuidle
[    0.443428] Monitor-Mwait will be used to enter C-1 state
[    0.443586] Monitor-Mwait will be used to enter C-2 state
[    0.443597] Marking TSC unstable due to TSC halts in idle
[    0.454992] thermal LNXTHERM:00: registered as thermal_zone0
[    0.454998] ACPI: Thermal Zone [TZ00] (81 C)
[    0.455587] thermal LNXTHERM:01: registered as thermal_zone1
[    0.455589] ACPI: Thermal Zone [TZ01] (81 C)
[    0.455612] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.455663] ERST: Table is not found!
[    0.455773] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.460000] ACPI: Battery Slot [BAT1] (battery present)
[    0.460041] isapnp: Scanning for PnP cards...
[    0.589532] Freeing initrd memory: 13312k freed
[    0.816229] isapnp: No Plug & Play device found
[    0.848561] Linux agpgart interface v0.103
[    0.850165] brd: module loaded
[    0.850841] loop: module loaded
[    0.851426] Fixed MDIO Bus: probed
[    0.851456] PPP generic driver version 2.4.2
[    0.851495] tun: Universal TUN/TAP device driver, 1.6
[    0.851497] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.851589] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.851611] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    0.851626] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.851631] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.851670] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.851703] ehci_hcd 0000:00:1a.7: debug port 1
[    0.855587] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    0.855609] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xf6204800
[    0.868019] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.868151] hub 1-0:1.0: USB hub found
[    0.868156] hub 1-0:1.0: 6 ports detected
[    0.868253] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.868266] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.868270] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.868307] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.868339] ehci_hcd 0000:00:1d.7: debug port 1
[    0.872222] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.872238] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf6204c00
[    0.888019] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.888172] hub 2-0:1.0: USB hub found
[    0.888178] hub 2-0:1.0: 6 ports detected
[    0.888287] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.888305] uhci_hcd: USB Universal Host Controller Interface driver
[    0.888333] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.888344] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.888350] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.888401] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.888448] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001800
[    0.888615] hub 3-0:1.0: USB hub found
[    0.888619] hub 3-0:1.0: 2 ports detected
[    0.888713] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.888722] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.888727] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.888772] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.888823] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001820
[    0.888960] hub 4-0:1.0: USB hub found
[    0.888964] hub 4-0:1.0: 2 ports detected
[    0.889038] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    0.889045] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.889049] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.889085] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.889118] uhci_hcd 0000:00:1a.2: irq 19, io base 0x00001840
[    0.889268] hub 5-0:1.0: USB hub found
[    0.889272] hub 5-0:1.0: 2 ports detected
[    0.889350] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.889358] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.889362] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.889398] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.889431] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001860
[    0.889578] hub 6-0:1.0: USB hub found
[    0.889582] hub 6-0:1.0: 2 ports detected
[    0.889654] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.889662] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.889666] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.889707] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.889737] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001880
[    0.889869] hub 7-0:1.0: USB hub found
[    0.889873] hub 7-0:1.0: 2 ports detected
[    0.889944] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.889951] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.889955] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.889993] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.890033] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
[    0.890165] hub 8-0:1.0: USB hub found
[    0.890169] hub 8-0:1.0: 2 ports detected
[    0.890301] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.892708] i8042: Detected active multiplexing controller, rev 1.1
[    0.893671] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.893678] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.893712] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.893743] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.893770] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.893886] mousedev: PS/2 mouse device common for all mice
[    0.894203] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    0.894237] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.894324] device-mapper: uevent: version 1.0.3
[    0.894409] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    0.894447] EISA: Probing bus 0 at eisa.0
[    0.894450] EISA: Cannot allocate resource for mainboard
[    0.894452] Cannot allocate resource for EISA slot 1
[    0.894454] Cannot allocate resource for EISA slot 2
[    0.894457] Cannot allocate resource for EISA slot 3
[    0.894459] Cannot allocate resource for EISA slot 4
[    0.894461] Cannot allocate resource for EISA slot 5
[    0.894463] Cannot allocate resource for EISA slot 6
[    0.894465] Cannot allocate resource for EISA slot 7
[    0.894467] Cannot allocate resource for EISA slot 8
[    0.894469] EISA: Detected 0 cards.
[    0.894480] cpufreq-nforce2: No nForce2 chipset.
[    0.894537] cpuidle: using governor ladder
[    0.894623] cpuidle: using governor menu
[    0.894625] EFI Variables Facility v0.08 2004-May-17
[    0.894981] TCP cubic registered
[    0.895143] NET: Registered protocol family 10
[    0.895844] NET: Registered protocol family 17
[    0.895859] Registering the dns_resolver key type
[    0.895883] Using IPI No-Shortcut mode
[    0.895964] PM: Hibernation image not present or could not be loaded.
[    0.895976] registered taskstats version 1
[    0.910016]   Magic number: 15:582:842
[    0.910115] rtc_cmos 00:07: setting system clock to 2011-10-29 15:50:47 UTC (1319903447)
[    0.910651] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.910653] EDD information not available.
[    0.910849] Freeing unused kernel memory: 720k freed
[    0.911132] Write protecting the kernel text: 5496k
[    0.911211] Write protecting the kernel read-only data: 2232k
[    0.911213] NX-protecting the kernel data: 4744k
[    0.921987] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.930006] udevd[85]: starting version 173
[    1.050088] ahci 0000:00:1f.2: version 3.0
[    1.050105] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.050169] ahci 0000:00:1f.2: irq 44 for MSI/MSI-X
[    1.050235] ahci: SSS flag set, parallel bus scan disabled
[    1.050276] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    1.050281] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ccc ems sxs 
[    1.050287] ahci 0000:00:1f.2: setting latency timer to 64
[    1.071193] scsi0 : ahci
[    1.072831] sky2: driver version 1.28
[    1.072917] sky2 0000:06:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.072954] sky2 0000:06:00.0: setting latency timer to 64
[    1.073049] sky2 0000:06:00.0: Yukon-2 EC Ultra chip revision 3
[    1.073733] sky2 0000:06:00.0: irq 45 for MSI/MSI-X
[    1.074841] scsi1 : ahci
[    1.075068] sky2 0000:06:00.0: eth0: addr 00:13:77:d4:8d:b5
[    1.075284] scsi2 : ahci
[    1.075444] scsi3 : ahci
[    1.075533] scsi4 : ahci
[    1.075620] scsi5 : ahci
[    1.075685] ata1: SATA max UDMA/133 abar m2048@0xf6204000 port 0xf6204100 irq 44
[    1.075689] ata2: SATA max UDMA/133 abar m2048@0xf6204000 port 0xf6204180 irq 44
[    1.075691] ata3: DUMMY
[    1.075693] ata4: DUMMY
[    1.075696] ata5: SATA max UDMA/133 abar m2048@0xf6204000 port 0xf6204300 irq 44
[    1.075700] ata6: SATA max UDMA/133 abar m2048@0xf6204000 port 0xf6204380 irq 44
[    1.240050] usb 1-3: new high speed USB device number 3 using ehci_hcd
[    1.392124] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.576065] usb 2-3: new high speed USB device number 2 using ehci_hcd
[    1.688045] usb 2-3: device descriptor read/64, error -71
[    1.748422] ata1.00: ATA-8: WDC WD3200BEVT-22ZCT0, 11.01A11, max UDMA/133
[    1.748428] ata1.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    1.751020] ata1.00: configured for UDMA/133
[    1.751230] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200BEVT-2 11.0 PQ: 0 ANSI: 5
[    1.751445] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.751479] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.751544] sd 0:0:0:0: [sda] Write Protect is off
[    1.751547] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.751573] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.762251]  sda: sda1 sda2 sda3
[    1.762638] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.928083] usbcore: registered new interface driver uas
[    2.068055] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.071047] ata2.00: ATAPI: TSSTcorp CDDVDW TS-L633A, SC03, max UDMA/100
[    2.071053] ata2.00: applying bridge limits
[    2.113645] ata2.00: configured for UDMA/100
[    2.164058] usb 3-1: new low speed USB device number 2 using uhci_hcd
[    2.219925] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L633A  SC03 PQ: 0 ANSI: 5
[    2.285480] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.285486] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.285670] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.285743] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.604068] ata5: SATA link down (SStatus 0 SControl 300)
[    2.924047] ata6: SATA link down (SStatus 0 SControl 300)
[    2.925226] Initializing USB Mass Storage driver...
[    2.929505] scsi6 : usb-storage 2-3:1.0
[    2.929685] usbcore: registered new interface driver usb-storage
[    2.929688] USB Mass Storage support registered.
[    2.943172] input: Logitech USB Laser Mouse as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/input/input5
[    2.943304] generic-usb 0003:046D:C062.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB Laser Mouse] on usb-0000:00:1a.0-1/input0
[    2.943325] usbcore: registered new interface driver usbhid
[    2.943328] usbhid: USB HID core driver
[    3.928450] scsi 6:0:0:0: Direct-Access     JetFlash Transcend 32GB   1.00 PQ: 0 ANSI: 5
[    3.941149] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    3.941321] sd 6:0:0:0: [sdb] 61767680 512-byte logical blocks: (31.6 GB/29.4 GiB)
[    3.941426] sd 6:0:0:0: [sdb] Write Protect is off
[    3.941430] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[    3.941621] sd 6:0:0:0: [sdb] No Caching mode page present
[    3.941627] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    3.942673] sd 6:0:0:0: [sdb] No Caching mode page present
[    3.942680] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    3.944778]  sdb: sdb1 sdb2 < sdb5 sdb6 >
[    3.945584] sd 6:0:0:0: [sdb] No Caching mode page present
[    3.945588] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    3.945591] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    4.096868] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[    7.199216] udevd[342]: starting version 173
[    7.226112] Adding 1998844k swap on /dev/sdb5.  Priority:-1 extents:1 across:1998844k 
[    7.239721] lp: driver loaded but no devices found
[    7.291733] EXT4-fs (sdb1): re-mounted. Opts: errors=remount-ro
[    7.428329] type=1400 audit(1319896254.017:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=507 comm="apparmor_parser"
[    7.429112] type=1400 audit(1319896254.017:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=507 comm="apparmor_parser"
[    7.439276] type=1400 audit(1319896254.025:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=507 comm="apparmor_parser"
[    7.696505] sky2 0000:06:00.0: eth0: enabling interface
[    7.697008] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    7.745604] cfg80211: Calling CRDA to update world regulatory domain
[    7.805610] ath5k 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.805625] ath5k 0000:02:00.0: setting latency timer to 64
[    7.805679] ath5k 0000:02:00.0: registered as 'phy0'
[    8.225855] Linux video capture interface: v2.00
[    8.231921] uvcvideo: Found UVC 1.00 device Vega USB 2.0 Camera. (0ac8:c302)
[    8.255255] input: Vega USB 2.0 Camera. as /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3:1.0/input/input6
[    8.257499] usbcore: registered new interface driver uvcvideo
[    8.257502] USB Video Class driver (v1.1.0)
[    8.318097] ath: EEPROM regdomain: 0x65
[    8.318101] ath: EEPROM indicates we should expect a direct regpair map
[    8.318107] ath: Country alpha2 being used: 00
[    8.318110] ath: Regpair used: 0x65
[    8.318276] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[    8.318279] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    8.318282] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[    8.318285] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    8.318288] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[    8.318291] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    8.318293] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[    8.318296] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    8.318299] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[    8.318302] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    8.318304] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[    8.318307] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    8.318310] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[    8.318313] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    8.318315] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[    8.318318] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    8.318320] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[    8.318323] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    8.318326] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[    8.318329] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    8.318332] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[    8.318335] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    8.318337] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[    8.318340] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    8.318343] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[    8.318346] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    8.318348] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[    8.318404] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[    8.319117] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[    8.319122] cfg80211: World regulatory domain updated:
[    8.319124] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    8.319127] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.319131] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    8.319134] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    8.319137] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.319140] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.364003] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[    8.376521] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[    8.402177] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    8.406823] type=1400 audit(1319896254.993:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=861 comm="apparmor_parser"
[    8.407524] type=1400 audit(1319896254.993:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=861 comm="apparmor_parser"
[    8.408061] type=1400 audit(1319896254.997:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=861 comm="apparmor_parser"
[    8.409640] type=1400 audit(1319896254.997:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=860 comm="apparmor_parser"
[    8.418528] type=1400 audit(1319896255.005:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=866 comm="apparmor_parser"
[    8.420328] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    8.420402] HDA Intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[    8.420437] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    8.420934] acpi device:03: registered as cooling_device4
[    8.421251] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input7
[    8.421477] ACPI: Video Device [NVID] (multi-head: yes  rom: no  post: no)
[    8.423388] type=1400 audit(1319896255.009:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=866 comm="apparmor_parser"
[    8.428422] type=1400 audit(1319896255.017:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=864 comm="apparmor_parser"
[    8.454398] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    8.485298] hda_codec: ALC262: BIOS auto-probing.
[    8.503006] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[    8.503217] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[    8.683813] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1c0b1, caps: 0xa04711/0xa00000/0x0
[    8.718430] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input10
[    9.912853] init: failsafe main process (803) killed by TERM signal
[    9.918389] init: apport pre-start process (935) terminated with status 1
[    9.946689] init: apport post-stop process (965) terminated with status 1
```I tried to reinstall the gnome-power-manager and also some bootoptions like acpic=off (no better result).

When I start withbootoption vga=771, the system runs a little bit longer...

Here the boot.log with vga=771:
```
fsck from util-linux 2.19.1 
/dev/sdb1: sauber, 155261/625856 Dateien, 824961/2499840 Blöcke (Prüfung nach 4 Einhängevorgängen) 
 * Starting configure network device[74G[ OK ] 
 * Starting configure network device security[74G[ OK ] 
 * Starting configure network device security[74G[ OK ] 
 * Starting Mount network filesystems[74G[ OK ] 
 * Starting Failsafe Boot Delay[74G[ OK ] 
 * Stopping Mount network filesystems[74G[ OK ] 
 * Starting Bridge socket events into upstart[74G[ OK ] 
 * Starting System V initialisation compatibility[74G[ OK ] 
 * Starting configure network device[74G[ OK ] 
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox 
 * Starting AppArmor profiles       [80G  [74G[ OK ] 
 * Starting configure network device[74G[ OK ] 
 * Starting configure network device security[74G[ OK ] 
speech-dispatcher disabled; edit /etc/default/speech-dispatcher 
Checking for running unattended-upgrades:  
 * Stopping Failsafe Boot Delay[74G[ OK ] 
 * Stopping System V initialisation compatibility[74G[ OK ] 
 * Starting System V runlevel compatibility[74G[ OK ] 
 * Stopping automatic crash report generation[74G[[31mfail[39;49m] 
 * Starting deferred execution scheduler[74G[ OK ] 
 * Starting CPU interrupts balancing daemon[74G[ OK ] 
 * Starting regular background program processing daemon[74G[ OK ] 
 * Starting ACPI daemon[74G[ OK ] 
 * Starting anac(h)ronistic cron[74G[ OK ] 
 * Starting save kernel messages[74G[ OK ] 
 * Stopping save kernel messages[74G[ OK ] 
 * Starting bluetooth       [80G  [74G[ OK ] 
 [33m*[39;49m PulseAudio configured for per-user sessions 
saned disabled; edit /etc/default/saned 
 * Stopping cold plug devices[74G[ OK ] 
 * Stopping log initial device creation[74G[ OK ] 
 * Starting configure network device security[74G[ OK ] 
 * Starting save udev log and update rules[74G[ OK ] 
 * Starting LightDM Display Manager[74G[ OK ] 
 * Starting Userspace bootsplash[74G[ OK ] 
 * Stopping Userspace bootsplash[74G[ OK ] 
 * Stopping save udev log and update rules[74G[ OK ]
```and the dmesg with vga=771:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-12-generic-pae (buildd@vernadsky) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #20-Ubuntu SMP Fri Oct 7 16:37:17 UTC 2011 (Ubuntu 3.0.0-12.20-generic-pae 3.0.4)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e400 (usable)
[    0.000000]  BIOS-e820: 000000000009e400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf8a1000 (usable)
[    0.000000]  BIOS-e820: 00000000bf8a1000 - 00000000bf8a7000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf8a7000 - 00000000bf9b4000 (usable)
[    0.000000]  BIOS-e820: 00000000bf9b4000 - 00000000bfa0f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfa0f000 - 00000000bfb07000 (usable)
[    0.000000]  BIOS-e820: 00000000bfb07000 - 00000000bfd0f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfd0f000 - 00000000bfd18000 (usable)
[    0.000000]  BIOS-e820: 00000000bfd18000 - 00000000bfd1f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfd1f000 - 00000000bfd65000 (usable)
[    0.000000]  BIOS-e820: 00000000bfd65000 - 00000000bfd9f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfd9f000 - 00000000bfe00000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] DMI: SAMSUNG ELECTRONICS CO., LTD. R510/P510                  /R510/P510                  , BIOS 07LI.MP00.20080926.SCY 09/26/2008
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   1 base 000000000 mask F00000000 write-back
[    0.000000]   2 base 100000000 mask FC0000000 write-back
[    0.000000]   3 base 0BFE00000 mask FFFE00000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 3GB, range: 1GB, type UC
[    0.000000] reg 1, base: 0GB, range: 4GB, type WB
[    0.000000] reg 2, base: 4GB, range: 1GB, type WB
[    0.000000] reg 3, base: 3070MB, range: 2MB, type UC
[    0.000000] total RAM covered: 4094M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 4M     num_reg: 4      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3070MB, range: 2MB, type UC
[    0.000000] reg 3, base: 4GB, range: 1GB, type WB
[    0.000000] e820 update range: 00000000bfe00000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] found SMP MP-table at [c00f7380] f7380
[    0.000000] initial memory mapped : 0 - 02000000
[    0.000000] Base memory trampoline at [c009a000] 9a000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 1ffb000-2000000
[    0.000000] RAMDISK: 365f0000 - 372f0000
[    0.000000] ACPI: RSDP 000f72e0 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT bfdf8657 0006C (v01 SECCSD LH43STAR 06040000  LTP 00000000)
[    0.000000] ACPI: FACP bfde8000 000F4 (v03 INTEL  CRESTLNE 06040000 ALAN 00000001)
[    0.000000] ACPI: DSDT bfde9000 06533 (v02 Intel  CANTIGA  06040000 INTL 20050624)
[    0.000000] ACPI: FACS bfd9efc0 00040
[    0.000000] ACPI: HPET bfdfed86 00038 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG bfdfedbe 0003C (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: APIC bfdfedfa 00068 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT bfdfee62 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SLIC bfdfee8a 00176 (v01 SECCSD LH43STAR 06040000  LTP 00000000)
[    0.000000] ACPI: SSDT bfde7000 005F9 (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT bfde6000 00259 (v01  PmRef  Cpu0Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT bfde5000 0020F (v01  PmRef    ApTst 00003000 INTL 20050624)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 4228MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037bfe
[    0.000000]   HighMem  0x00037bfe -> 0x00140000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[7] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000bf8a1
[    0.000000]     0: 0x000bf8a7 -> 0x000bf9b4
[    0.000000]     0: 0x000bfa0f -> 0x000bfb07
[    0.000000]     0: 0x000bfd0f -> 0x000bfd18
[    0.000000]     0: 0x000bfd1f -> 0x000bfd65
[    0.000000]     0: 0x00100000 -> 0x00140000
[    0.000000] On node 0 totalpages: 1047171
[    0.000000] free_area_init_node: node 0, pgdat c17e9f40, node_mem_map f3df0200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3950 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 8457 pages used for memmap
[    0.000000]   HighMem zone: 810478 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at bfe00000 (gap: bfe00000:40200000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f7800000 s29952 r0 d23296 u1048576
[    0.000000] pcpu-alloc: s29952 r0 d23296 u1048576 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1036930
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic-pae root=UUID=8e7603e0-8b9e-41cd-889b-5e54d0455b59 ro quiet splash vt.handoff=7 vga=771
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 20971264 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:00140000)
[    0.000000] Memory: 4103120k/5242880k available (5494k kernel code, 85564k reserved, 2653k data, 720k init, 3275740k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc17f6000 - 0xc18aa000   ( 720 kB)
[    0.000000]       .data : 0xc155d9b0 - 0xc17f5180   (2653 kB)
[    0.000000]       .text : 0xc1000000 - 0xc155d9b0   (5494 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f7408000 soft=f740a000
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1994.800 MHz processor.
[    0.004003] Calibrating delay loop (skipped), value calculated using timer frequency.. 3989.60 BogoMIPS (lpj=7979200)
[    0.004009] pid_max: default: 32768 minimum: 301
[    0.004031] Security Framework initialized
[    0.004048] AppArmor: AppArmor initialized
[    0.004050] Yama: becoming mindful.
[    0.004108] Mount-cache hash table entries: 512
[    0.004247] Initializing cgroup subsys cpuacct
[    0.004253] Initializing cgroup subsys memory
[    0.004262] Initializing cgroup subsys devices
[    0.004264] Initializing cgroup subsys freezer
[    0.004267] Initializing cgroup subsys net_cls
[    0.004269] Initializing cgroup subsys blkio
[    0.004277] Initializing cgroup subsys perf_event
[    0.004310] CPU: Physical Processor ID: 0
[    0.004312] CPU: Processor Core ID: 0
[    0.004315] mce: CPU supports 6 MCE banks
[    0.004324] CPU0: Thermal monitoring enabled (TM2)
[    0.004328] using mwait in idle threads.
[    0.005381] CPU0: Core temperature above threshold, cpu clock throttled (total events = 1)
[    0.006036] CPU0: Core temperature/speed normal
[    0.008149] ACPI: Core revision 20110413
[    0.018469] ftrace: allocating 25582 entries in 51 pages
[    0.020074] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.020441] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.060987] CPU0: Intel(R) Core(TM)2 Duo CPU     T5800  @ 2.00GHz stepping 0d
[    0.064003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.064003] PEBS disabled due to CPU errata.
[    0.064003] ... version:                2
[    0.064003] ... bit width:              40
[    0.064003] ... generic registers:      2
[    0.064003] ... value mask:             000000ffffffffff
[    0.064003] ... max period:             000000007fffffff
[    0.064003] ... fixed-purpose events:   3
[    0.064003] ... event mask:             0000000700000003
[    0.064003] CPU 1 irqstacks, hard=f74ca000 soft=f74cc000
[    0.064003] Booting Node   0, Processors  #1 Ok.
[    0.064003] smpboot cpu 1: start_ip = 9a000
[    0.008000] Initializing CPU#1
[    0.152023] Brought up 2 CPUs
[    0.152027] Total of 2 processors activated (7980.10 BogoMIPS).
[    0.152991] devtmpfs: initialized
[    0.152991] PM: Registering ACPI NVS region at bfd65000 (237568 bytes)
[    0.154420] print_constraints: dummy: 
[    0.154452] Time:  9:45:07  Date: 10/30/11
[    0.154499] NET: Registered protocol family 16
[    0.154529] Trying to unpack rootfs image as initramfs...
[    0.156106] EISA bus registered
[    0.156124] ACPI: bus type pci registered
[    0.156200] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.156204] PCI: not using MMCONFIG
[    0.156412] PCI : PCI BIOS aera is rw and x. Use pci=nobios if you want it NX.
[    0.156734] PCI: PCI BIOS revision 3.00 entry at 0xfde11, last bus=8
[    0.156738] PCI: Using configuration type 1 for base access
[    0.158550] bio: create slab <bio-0> at 0
[    0.161594] ACPI: EC: Look up EC in DSDT
[    0.168431] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.171116] ACPI: SSDT bfd1ac20 00265 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.171896] ACPI: Dynamic OEM Table Load:
[    0.171902] ACPI: SSDT   (null) 00265 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.172238] ACPI: SSDT bfd18020 00C78 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.172981] ACPI: Dynamic OEM Table Load:
[    0.172987] ACPI: SSDT   (null) 00C78 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.232567] ACPI: SSDT bfd19ca0 001CF (v01  PmRef    ApIst 00003000 INTL 20050624)
[    0.233386] ACPI: Dynamic OEM Table Load:
[    0.233393] ACPI: SSDT   (null) 001CF (v01  PmRef    ApIst 00003000 INTL 20050624)
[    0.264240] ACPI: SSDT bfd19f20 0008D (v01  PmRef    ApCst 00003000 INTL 20050624)
[    0.265014] ACPI: Dynamic OEM Table Load:
[    0.265020] ACPI: SSDT   (null) 0008D (v01  PmRef    ApCst 00003000 INTL 20050624)
[    0.296829] ACPI: Interpreter enabled
[    0.296829] ACPI: (supports S0 S3 S4 S5)
[    0.296829] ACPI: Using IOAPIC for interrupt routing
[    0.296829] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.297809] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.297814] PCI: Using MMCONFIG for extended config space
[    0.298491] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.305940] ACPI: Power Resource [FN00] (off)
[    0.305940] ACPI: Power Resource [FN01] (off)
[    0.305940] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.305940] ACPI: No dock devices found.
[    0.305940] HEST: Table not found.
[    0.305940] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.308404] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.309553] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.309559] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.309564] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.309570] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.309575] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.309581] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xfebfffff]
[    0.309606] pci 0000:00:00.0: [8086:2a40] type 0 class 0x000600
[    0.309649] DMAR: Forcing write-buffer flush capability
[    0.309652] DMAR: Disabling IOMMU for graphics on this chipset
[    0.309691] pci 0000:00:01.0: [8086:2a41] type 1 class 0x000604
[    0.309756] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.309763] pci 0000:00:01.0: PME# disabled
[    0.309845] pci 0000:00:1a.0: [8086:2937] type 0 class 0x000c03
[    0.309933] pci 0000:00:1a.0: reg 20: [io  0x1800-0x181f]
[    0.310025] pci 0000:00:1a.1: [8086:2938] type 0 class 0x000c03
[    0.310095] pci 0000:00:1a.1: reg 20: [io  0x1820-0x183f]
[    0.310170] pci 0000:00:1a.2: [8086:2939] type 0 class 0x000c03
[    0.310246] pci 0000:00:1a.2: reg 20: [io  0x1840-0x185f]
[    0.310340] pci 0000:00:1a.7: [8086:293c] type 0 class 0x000c03
[    0.310377] pci 0000:00:1a.7: reg 10: [mem 0xf6204800-0xf6204bff]
[    0.310502] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.310510] pci 0000:00:1a.7: PME# disabled
[    0.310550] pci 0000:00:1b.0: [8086:293e] type 0 class 0x000403
[    0.310578] pci 0000:00:1b.0: reg 10: [mem 0xf6200000-0xf6203fff 64bit]
[    0.310672] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.310680] pci 0000:00:1b.0: PME# disabled
[    0.310715] pci 0000:00:1c.0: [8086:2940] type 1 class 0x000604
[    0.310813] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.310821] pci 0000:00:1c.0: PME# disabled
[    0.310864] pci 0000:00:1c.2: [8086:2944] type 1 class 0x000604
[    0.310972] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.310980] pci 0000:00:1c.2: PME# disabled
[    0.311018] pci 0000:00:1c.3: [8086:2946] type 1 class 0x000604
[    0.311126] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.311134] pci 0000:00:1c.3: PME# disabled
[    0.311181] pci 0000:00:1d.0: [8086:2934] type 0 class 0x000c03
[    0.311251] pci 0000:00:1d.0: reg 20: [io  0x1860-0x187f]
[    0.311329] pci 0000:00:1d.1: [8086:2935] type 0 class 0x000c03
[    0.311400] pci 0000:00:1d.1: reg 20: [io  0x1880-0x189f]
[    0.311476] pci 0000:00:1d.2: [8086:2936] type 0 class 0x000c03
[    0.311550] pci 0000:00:1d.2: reg 20: [io  0x18a0-0x18bf]
[    0.311642] pci 0000:00:1d.7: [8086:293a] type 0 class 0x000c03
[    0.311680] pci 0000:00:1d.7: reg 10: [mem 0xf6204c00-0xf6204fff]
[    0.311816] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.311824] pci 0000:00:1d.7: PME# disabled
[    0.311858] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.311968] pci 0000:00:1f.0: [8086:2919] type 0 class 0x000601
[    0.312151] pci 0000:00:1f.2: [8086:2929] type 0 class 0x000106
[    0.312186] pci 0000:00:1f.2: reg 10: [io  0x18f0-0x18f7]
[    0.312202] pci 0000:00:1f.2: reg 14: [io  0x18e4-0x18e7]
[    0.312218] pci 0000:00:1f.2: reg 18: [io  0x18e8-0x18ef]
[    0.312232] pci 0000:00:1f.2: reg 1c: [io  0x18e0-0x18e3]
[    0.312248] pci 0000:00:1f.2: reg 20: [io  0x18c0-0x18df]
[    0.312264] pci 0000:00:1f.2: reg 24: [mem 0xf6204000-0xf62047ff]
[    0.312325] pci 0000:00:1f.2: PME# supported from D3hot
[    0.312332] pci 0000:00:1f.2: PME# disabled
[    0.312362] pci 0000:00:1f.3: [8086:2930] type 0 class 0x000c05
[    0.312394] pci 0000:00:1f.3: reg 10: [mem 0x00000000-0x000000ff 64bit]
[    0.312436] pci 0000:00:1f.3: reg 20: [io  0x1c00-0x1c1f]
[    0.312568] pci 0000:01:00.0: [10de:06e8] type 0 class 0x000300
[    0.312601] pci 0000:01:00.0: reg 10: [mem 0xce000000-0xceffffff]
[    0.312635] pci 0000:01:00.0: reg 14: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.312669] pci 0000:01:00.0: reg 1c: [mem 0xcc000000-0xcdffffff 64bit]
[    0.312694] pci 0000:01:00.0: reg 24: [io  0x2000-0x207f]
[    0.312718] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.320051] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.320058] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    0.320065] pci 0000:00:01.0:   bridge window [mem 0xcc000000-0xceffffff]
[    0.320074] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.320175] pci 0000:02:00.0: [168c:001c] type 0 class 0x000200
[    0.320212] pci 0000:02:00.0: reg 10: [mem 0xf3000000-0xf300ffff 64bit]
[    0.320364] pci 0000:02:00.0: PME# supported from D3hot
[    0.320373] pci 0000:02:00.0: PME# disabled
[    0.320411] pci 0000:02:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.320427] pci 0000:00:1c.0: PCI bridge to [bus 02-03]
[    0.320435] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.320442] pci 0000:00:1c.0:   bridge window [mem 0xf3000000-0xf3ffffff]
[    0.320454] pci 0000:00:1c.0:   bridge window [mem 0xf0000000-0xf0ffffff 64bit pref]
[    0.320526] pci 0000:00:1c.2: PCI bridge to [bus 04-05]
[    0.320533] pci 0000:00:1c.2:   bridge window [io  0x4000-0x4fff]
[    0.320540] pci 0000:00:1c.2:   bridge window [mem 0xf4000000-0xf4ffffff]
[    0.320551] pci 0000:00:1c.2:   bridge window [mem 0xf1000000-0xf1ffffff 64bit pref]
[    0.320799] pci 0000:06:00.0: [11ab:4363] type 0 class 0x000200
[    0.320962] pci 0000:06:00.0: reg 10: [mem 0xf5000000-0xf5003fff 64bit]
[    0.321050] pci 0000:06:00.0: reg 18: [io  0x5000-0x50ff]
[    0.321381] pci 0000:06:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.321679] pci 0000:06:00.0: supports D1 D2
[    0.321683] pci 0000:06:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.321704] pci 0000:06:00.0: PME# disabled
[    0.321916] pci 0000:00:1c.3: PCI bridge to [bus 06-07]
[    0.321922] pci 0000:00:1c.3:   bridge window [io  0x5000-0x5fff]
[    0.321928] pci 0000:00:1c.3:   bridge window [mem 0xf5000000-0xf5ffffff]
[    0.321937] pci 0000:00:1c.3:   bridge window [mem 0xf2000000-0xf2ffffff 64bit pref]
[    0.322045] pci 0000:00:1e.0: PCI bridge to [bus 08-08] (subtractive decode)
[    0.322053] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.322062] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.322073] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.322078] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.322083] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.322088] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.322093] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.322098] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.322103] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xfebfffff] (subtractive decode)
[    0.322141] pci_bus 0000:00: on NUMA node 0
[    0.322150] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.322530] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    0.322713] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.322820] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.322888] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.322955]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.322959]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.322961] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.333791] ACPI: PCI Interrupt Link [LNKA] (IRQs *11)
[    0.333887] ACPI: PCI Interrupt Link [LNKB] (IRQs *10)
[    0.333972] ACPI: PCI Interrupt Link [LNKC] (IRQs *5)
[    0.334066] ACPI: PCI Interrupt Link [LNKD] (IRQs *5)
[    0.334150] ACPI: PCI Interrupt Link [LNKE] (IRQs 11) *0, disabled.
[    0.334236] ACPI: PCI Interrupt Link [LNKF] (IRQs *10)
[    0.334320] ACPI: PCI Interrupt Link [LNKG] (IRQs *5)
[    0.334405] ACPI: PCI Interrupt Link [LNKH] (IRQs *5)
[    0.334612] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.334619] vgaarb: loaded
[    0.334622] vgaarb: bridge control possible 0000:01:00.0
[    0.335024] SCSI subsystem initialized
[    0.335124] libata version 3.00 loaded.
[    0.335217] usbcore: registered new interface driver usbfs
[    0.335239] usbcore: registered new interface driver hub
[    0.335290] usbcore: registered new device driver usb
[    0.335454] PCI: Using ACPI for IRQ routing
[    0.335986] PCI: pci_cache_line_size set to 64 bytes
[    0.336180] reserve RAM buffer: 000000000009e400 - 000000000009ffff 
[    0.336185] reserve RAM buffer: 00000000bf8a1000 - 00000000bfffffff 
[    0.336193] reserve RAM buffer: 00000000bf9b4000 - 00000000bfffffff 
[    0.336201] reserve RAM buffer: 00000000bfb07000 - 00000000bfffffff 
[    0.336207] reserve RAM buffer: 00000000bfd18000 - 00000000bfffffff 
[    0.336213] reserve RAM buffer: 00000000bfd65000 - 00000000bfffffff 
[    0.336386] NetLabel: Initializing
[    0.336390] NetLabel:  domain hash size = 128
[    0.336393] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.336411] NetLabel:  unlabeled traffic allowed by default
[    0.336480] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.336490] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.336500] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.340402] Switching to clocksource hpet
[    0.343520] Switched to NOHz mode on CPU #0
[    0.343627] Switched to NOHz mode on CPU #1
[    0.354031] AppArmor: AppArmor Filesystem Enabled
[    0.354076] pnp: PnP ACPI init
[    0.354102] ACPI: bus type pnp registered
[    0.354723] pnp 00:00: [bus 00-ff]
[    0.354728] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.354733] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.354737] pnp 00:00: [io  0x0d00-0xffff window]
[    0.354742] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.354747] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.354751] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.354756] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.354760] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.354764] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.354769] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.354773] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.354777] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.354782] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.354787] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.354791] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.354795] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.354800] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.354804] pnp 00:00: [mem 0xc0000000-0xfebfffff window]
[    0.354809] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    0.354928] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.355207] pnp 00:01: [io  0x0000-0x001f]
[    0.355211] pnp 00:01: [io  0x0081-0x0091]
[    0.355215] pnp 00:01: [io  0x0093-0x009f]
[    0.355219] pnp 00:01: [io  0x00c0-0x00df]
[    0.355223] pnp 00:01: [dma 4]
[    0.355290] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.355309] pnp 00:02: [mem 0xff000000-0xffffffff]
[    0.355363] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    0.355492] pnp 00:03: [mem 0xfed00000-0xfed003ff]
[    0.355598] system 00:03: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.355606] system 00:03: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    0.355629] pnp 00:04: [io  0x00f0]
[    0.355645] pnp 00:04: [irq 13]
[    0.355704] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.355730] pnp 00:05: [io  0x002e-0x002f]
[    0.355736] pnp 00:05: [io  0x004e-0x004f]
[    0.355743] pnp 00:05: [io  0x0061]
[    0.355747] pnp 00:05: [io  0x0063]
[    0.355750] pnp 00:05: [io  0x0065]
[    0.355754] pnp 00:05: [io  0x0067]
[    0.355758] pnp 00:05: [io  0x0070]
[    0.355761] pnp 00:05: [io  0x0080]
[    0.355765] pnp 00:05: [io  0x0092]
[    0.355769] pnp 00:05: [io  0x00b2-0x00b3]
[    0.355773] pnp 00:05: [io  0x0680-0x069f]
[    0.355776] pnp 00:05: [io  0x0480-0x048f]
[    0.355781] pnp 00:05: [io  0xffff]
[    0.355785] pnp 00:05: [io  0xffff]
[    0.355789] pnp 00:05: [io  0x0400-0x047f]
[    0.355793] pnp 00:05: [io  0x0480-0x048f]
[    0.355797] pnp 00:05: [io  0x1180-0x11ff]
[    0.355801] pnp 00:05: [io  0x164e-0x164f]
[    0.355805] pnp 00:05: [io  0x5000-0x500f]
[    0.355808] pnp 00:05: [io  0xfe00]
[    0.355841] pnp 00:05: disabling [io  0x5000-0x500f] because it overlaps 0000:00:1c.3 BAR 13 [io  0x5000-0x5fff]
[    0.355880] pnp 00:05: disabling [io  0x5000-0x500f disabled] because it overlaps 0000:06:00.0 BAR 2 [io  0x5000-0x50ff]
[    0.355956] system 00:05: [io  0x0680-0x069f] has been reserved
[    0.355962] system 00:05: [io  0x0480-0x048f] has been reserved
[    0.355968] system 00:05: [io  0xffff] has been reserved
[    0.355973] system 00:05: [io  0xffff] has been reserved
[    0.355978] system 00:05: [io  0x0400-0x047f] has been reserved
[    0.355983] system 00:05: [io  0x0480-0x048f] has been reserved
[    0.355988] system 00:05: [io  0x1180-0x11ff] has been reserved
[    0.355993] system 00:05: [io  0x164e-0x164f] has been reserved
[    0.355998] system 00:05: [io  0xfe00] has been reserved
[    0.356004] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.356063] pnp 00:06: [io  0x06a0-0x06af]
[    0.356067] pnp 00:06: [io  0x06b0-0x06ff]
[    0.356163] system 00:06: [io  0x06a0-0x06af] has been reserved
[    0.356168] system 00:06: [io  0x06b0-0x06ff] has been reserved
[    0.356174] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.356194] pnp 00:07: [io  0x0070-0x0077]
[    0.356203] pnp 00:07: [irq 8]
[    0.356263] pnp 00:07: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.356286] pnp 00:08: [io  0x0060]
[    0.356290] pnp 00:08: [io  0x0064]
[    0.356300] pnp 00:08: [irq 1]
[    0.356361] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.356383] pnp 00:09: [irq 12]
[    0.356450] pnp 00:09: Plug and Play ACPI device, IDs PNP0f13 (active)
[    0.356668] pnp 00:0a: [mem 0xfed1c000-0xfed1ffff]
[    0.356673] pnp 00:0a: [mem 0xfed10000-0xfed13fff]
[    0.356677] pnp 00:0a: [mem 0xfed18000-0xfed18fff]
[    0.356681] pnp 00:0a: [mem 0xfed19000-0xfed19fff]
[    0.356685] pnp 00:0a: [mem 0xe0000000-0xefffffff]
[    0.356689] pnp 00:0a: [mem 0xfed20000-0xfed3ffff]
[    0.356694] pnp 00:0a: [mem 0xfed40000-0xfed44fff]
[    0.356698] pnp 00:0a: [mem 0xfed45000-0xfed8ffff]
[    0.356818] system 00:0a: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.356824] system 00:0a: [mem 0xfed10000-0xfed13fff] has been reserved
[    0.356829] system 00:0a: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.356835] system 00:0a: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.356841] system 00:0a: [mem 0xe0000000-0xefffffff] has been reserved
[    0.356846] system 00:0a: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.356851] system 00:0a: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.356857] system 00:0a: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.356863] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.357348] pnp: PnP ACPI: found 11 devices
[    0.357352] ACPI: ACPI bus type pnp unregistered
[    0.357362] PnPBIOS: Disabled by ACPI PNP
[    0.394944] PCI: max bus depth: 1 pci_try_num: 2
[    0.395021] pci 0000:00:1f.3: BAR 0: assigned [mem 0xc0000000-0xc00000ff 64bit]
[    0.395034] pci 0000:00:1f.3: BAR 0: set to [mem 0xc0000000-0xc00000ff 64bit] (PCI address [0xc0000000-0xc00000ff])
[    0.395043] pci 0000:01:00.0: BAR 6: can't assign mem pref (size 0x20000)
[    0.395048] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.395054] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    0.395062] pci 0000:00:01.0:   bridge window [mem 0xcc000000-0xceffffff]
[    0.395068] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.395077] pci 0000:00:1c.0: PCI bridge to [bus 02-03]
[    0.395083] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.395092] pci 0000:00:1c.0:   bridge window [mem 0xf3000000-0xf3ffffff]
[    0.395100] pci 0000:00:1c.0:   bridge window [mem 0xf0000000-0xf0ffffff 64bit pref]
[    0.395113] pci 0000:00:1c.2: PCI bridge to [bus 04-05]
[    0.395118] pci 0000:00:1c.2:   bridge window [io  0x4000-0x4fff]
[    0.395128] pci 0000:00:1c.2:   bridge window [mem 0xf4000000-0xf4ffffff]
[    0.395136] pci 0000:00:1c.2:   bridge window [mem 0xf1000000-0xf1ffffff 64bit pref]
[    0.395150] pci 0000:06:00.0: BAR 6: assigned [mem 0xf2000000-0xf201ffff pref]
[    0.395154] pci 0000:00:1c.3: PCI bridge to [bus 06-07]
[    0.395160] pci 0000:00:1c.3:   bridge window [io  0x5000-0x5fff]
[    0.395169] pci 0000:00:1c.3:   bridge window [mem 0xf5000000-0xf5ffffff]
[    0.395177] pci 0000:00:1c.3:   bridge window [mem 0xf2000000-0xf2ffffff 64bit pref]
[    0.395188] pci 0000:00:1e.0: PCI bridge to [bus 08-08]
[    0.395192] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.395202] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.395209] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.395246] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.395254] pci 0000:00:01.0: setting latency timer to 64
[    0.395273] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.395280] pci 0000:00:1c.0: setting latency timer to 64
[    0.395298] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.395306] pci 0000:00:1c.2: setting latency timer to 64
[    0.395327] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.395334] pci 0000:00:1c.3: setting latency timer to 64
[    0.395346] pci 0000:00:1e.0: setting latency timer to 64
[    0.395353] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.395358] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.395363] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.395367] pci_bus 0000:00: resource 7 [mem 0x000d4000-0x000d7fff]
[    0.395372] pci_bus 0000:00: resource 8 [mem 0x000d8000-0x000dbfff]
[    0.395381] pci_bus 0000:00: resource 9 [mem 0xc0000000-0xfebfffff]
[    0.395384] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
[    0.395394] pci_bus 0000:01: resource 1 [mem 0xcc000000-0xceffffff]
[    0.395399] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.395404] pci_bus 0000:02: resource 0 [io  0x3000-0x3fff]
[    0.395409] pci_bus 0000:02: resource 1 [mem 0xf3000000-0xf3ffffff]
[    0.395413] pci_bus 0000:02: resource 2 [mem 0xf0000000-0xf0ffffff 64bit pref]
[    0.395418] pci_bus 0000:04: resource 0 [io  0x4000-0x4fff]
[    0.395423] pci_bus 0000:04: resource 1 [mem 0xf4000000-0xf4ffffff]
[    0.395428] pci_bus 0000:04: resource 2 [mem 0xf1000000-0xf1ffffff 64bit pref]
[    0.395432] pci_bus 0000:06: resource 0 [io  0x5000-0x5fff]
[    0.395437] pci_bus 0000:06: resource 1 [mem 0xf5000000-0xf5ffffff]
[    0.395442] pci_bus 0000:06: resource 2 [mem 0xf2000000-0xf2ffffff 64bit pref]
[    0.395447] pci_bus 0000:08: resource 4 [io  0x0000-0x0cf7]
[    0.395451] pci_bus 0000:08: resource 5 [io  0x0d00-0xffff]
[    0.395456] pci_bus 0000:08: resource 6 [mem 0x000a0000-0x000bffff]
[    0.395460] pci_bus 0000:08: resource 7 [mem 0x000d4000-0x000d7fff]
[    0.395465] pci_bus 0000:08: resource 8 [mem 0x000d8000-0x000dbfff]
[    0.395470] pci_bus 0000:08: resource 9 [mem 0xc0000000-0xfebfffff]
[    0.395541] NET: Registered protocol family 2
[    0.395662] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.396115] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.396698] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.396972] TCP: Hash tables configured (established 131072 bind 65536)
[    0.396976] TCP reno registered
[    0.396981] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.396993] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.397151] NET: Registered protocol family 1
[    0.397454] pci 0000:01:00.0: Boot video device
[    0.397495] PCI: CLS 64 bytes, default 64
[    0.397505] Simple Boot Flag at 0x37 set to 0x1
[    0.398048] audit: initializing netlink socket (disabled)
[    0.398064] type=2000 audit(1319967906.396:1): initialized
[    0.445677] highmem bounce pool size: 64 pages
[    0.445687] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.463692] VFS: Disk quotas dquot_6.5.2
[    0.463819] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.465103] fuse init (API version 7.16)
[    0.465277] msgmni has been set to 1615
[    0.465866] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.465912] io scheduler noop registered
[    0.465916] io scheduler deadline registered
[    0.465942] io scheduler cfq registered (default)
[    0.466148] pcieport 0000:00:01.0: setting latency timer to 64
[    0.466208] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.466309] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.466384] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.466497] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.466572] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    0.466686] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.466761] pcieport 0000:00:1c.3: irq 43 for MSI/MSI-X
[    0.466922] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.466967] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.467067] intel_idle: MWAIT substates: 0x22220
[    0.467069] intel_idle: does not run on family 6 model 15
[    0.467287] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.467525] ACPI: AC Adapter [ADP1] (on-line)
[    0.467655] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.467687] ACPI: Lid Switch [LID0]
[    0.467767] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.467776] ACPI: Power Button [PWRB]
[    0.467853] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.467860] ACPI: Sleep Button [SLPB]
[    0.467941] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.467947] ACPI: Power Button [PWRF]
[    0.468080] ACPI: Fan [FAN0] (off)
[    0.468154] ACPI: Fan [FAN1] (off)
[    0.468169] ACPI: acpi_idle registered with cpuidle
[    0.471988] Monitor-Mwait will be used to enter C-1 state
[    0.472171] Monitor-Mwait will be used to enter C-2 state
[    0.472181] Marking TSC unstable due to TSC halts in idle
[    0.483002] thermal LNXTHERM:00: registered as thermal_zone0
[    0.483005] ACPI: Thermal Zone [TZ00] (81 C)
[    0.483653] thermal LNXTHERM:01: registered as thermal_zone1
[    0.483657] ACPI: Thermal Zone [TZ01] (81 C)
[    0.483693] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.483738] ERST: Table is not found!
[    0.483875] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.484059] isapnp: Scanning for PnP cards...
[    0.500676] ACPI: Battery Slot [BAT1] (battery present)
[    0.671669] Freeing initrd memory: 13312k freed
[    0.840636] isapnp: No Plug & Play device found
[    0.872509] Linux agpgart interface v0.103
[    0.874115] brd: module loaded
[    0.874793] loop: module loaded
[    0.875372] Fixed MDIO Bus: probed
[    0.875399] PPP generic driver version 2.4.2
[    0.875437] tun: Universal TUN/TAP device driver, 1.6
[    0.875439] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.875533] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.875555] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    0.875570] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.875575] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.875616] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.875651] ehci_hcd 0000:00:1a.7: debug port 1
[    0.879537] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    0.879559] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xf6204800
[    0.892018] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.892152] hub 1-0:1.0: USB hub found
[    0.892157] hub 1-0:1.0: 6 ports detected
[    0.892254] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.892267] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.892271] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.892308] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.892339] ehci_hcd 0000:00:1d.7: debug port 1
[    0.896234] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.896251] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf6204c00
[    0.912018] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.912170] hub 2-0:1.0: USB hub found
[    0.912177] hub 2-0:1.0: 6 ports detected
[    0.912279] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.912298] uhci_hcd: USB Universal Host Controller Interface driver
[    0.912324] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.912335] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.912341] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.912399] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.912454] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001800
[    0.912623] hub 3-0:1.0: USB hub found
[    0.912628] hub 3-0:1.0: 2 ports detected
[    0.912724] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.912732] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.912736] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.912772] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.912822] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001820
[    0.912959] hub 4-0:1.0: USB hub found
[    0.912963] hub 4-0:1.0: 2 ports detected
[    0.913042] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    0.913049] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.913053] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.913090] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.913122] uhci_hcd 0000:00:1a.2: irq 19, io base 0x00001840
[    0.913266] hub 5-0:1.0: USB hub found
[    0.913270] hub 5-0:1.0: 2 ports detected
[    0.913347] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.913354] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.913358] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.913396] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.913428] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001860
[    0.913573] hub 6-0:1.0: USB hub found
[    0.913577] hub 6-0:1.0: 2 ports detected
[    0.913655] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.913662] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.913666] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.913704] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.913735] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001880
[    0.913869] hub 7-0:1.0: USB hub found
[    0.913873] hub 7-0:1.0: 2 ports detected
[    0.913946] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.913953] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.913957] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.913993] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.914033] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
[    0.914166] hub 8-0:1.0: USB hub found
[    0.914171] hub 8-0:1.0: 2 ports detected
[    0.914301] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.916863] i8042: Detected active multiplexing controller, rev 1.1
[    0.917981] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.917989] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.918022] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.918050] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.918077] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.918193] mousedev: PS/2 mouse device common for all mice
[    0.918518] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    0.918551] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.918633] device-mapper: uevent: version 1.0.3
[    0.918723] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    0.918759] EISA: Probing bus 0 at eisa.0
[    0.918763] EISA: Cannot allocate resource for mainboard
[    0.918766] Cannot allocate resource for EISA slot 1
[    0.918768] Cannot allocate resource for EISA slot 2
[    0.918770] Cannot allocate resource for EISA slot 3
[    0.918772] Cannot allocate resource for EISA slot 4
[    0.918774] Cannot allocate resource for EISA slot 5
[    0.918776] Cannot allocate resource for EISA slot 6
[    0.918778] Cannot allocate resource for EISA slot 7
[    0.918780] Cannot allocate resource for EISA slot 8
[    0.918782] EISA: Detected 0 cards.
[    0.918793] cpufreq-nforce2: No nForce2 chipset.
[    0.918848] cpuidle: using governor ladder
[    0.918935] cpuidle: using governor menu
[    0.918937] EFI Variables Facility v0.08 2004-May-17
[    0.919293] TCP cubic registered
[    0.919453] NET: Registered protocol family 10
[    0.920168] NET: Registered protocol family 17
[    0.920184] Registering the dns_resolver key type
[    0.920203] Using IPI No-Shortcut mode
[    0.920289] PM: Hibernation image not present or could not be loaded.
[    0.920307] registered taskstats version 1
[    0.936118]   Magic number: 15:468:779
[    0.936229] rtc_cmos 00:07: setting system clock to 2011-10-30 09:45:07 UTC (1319967907)
[    0.936986] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.936990] EDD information not available.
[    0.937203] Freeing unused kernel memory: 720k freed
[    0.937499] Write protecting the kernel text: 5496k
[    0.937578] Write protecting the kernel read-only data: 2232k
[    0.937580] NX-protecting the kernel data: 4744k
[    0.946160] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.960323] udevd[85]: starting version 173
[    1.108257] ahci 0000:00:1f.2: version 3.0
[    1.108279] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.108363] ahci 0000:00:1f.2: irq 44 for MSI/MSI-X
[    1.108438] ahci: SSS flag set, parallel bus scan disabled
[    1.108490] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    1.108497] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ccc ems sxs 
[    1.108506] ahci 0000:00:1f.2: setting latency timer to 64
[    1.108617] sky2: driver version 1.28
[    1.108689] sky2 0000:06:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.108729] sky2 0000:06:00.0: setting latency timer to 64
[    1.108856] sky2 0000:06:00.0: Yukon-2 EC Ultra chip revision 3
[    1.109560] sky2 0000:06:00.0: irq 45 for MSI/MSI-X
[    1.126519] sky2 0000:06:00.0: eth0: addr 00:13:77:d4:8d:b5
[    1.134478] scsi0 : ahci
[    1.134696] scsi1 : ahci
[    1.134829] scsi2 : ahci
[    1.134966] scsi3 : ahci
[    1.135100] scsi4 : ahci
[    1.135211] scsi5 : ahci
[    1.135286] ata1: SATA max UDMA/133 abar m2048@0xf6204000 port 0xf6204100 irq 44
[    1.135293] ata2: SATA max UDMA/133 abar m2048@0xf6204000 port 0xf6204180 irq 44
[    1.135297] ata3: DUMMY
[    1.135300] ata4: DUMMY
[    1.135305] ata5: SATA max UDMA/133 abar m2048@0xf6204000 port 0xf6204300 irq 44
[    1.135311] ata6: SATA max UDMA/133 abar m2048@0xf6204000 port 0xf6204380 irq 44
[    1.260053] usb 1-3: new high speed USB device number 3 using ehci_hcd
[    1.452050] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.596045] usb 2-3: new high speed USB device number 2 using ehci_hcd
[    1.708038] usb 2-3: device descriptor read/64, error -71
[    1.793922] ata1.00: ATA-8: WDC WD3200BEVT-22ZCT0, 11.01A11, max UDMA/133
[    1.793929] ata1.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    1.796477] ata1.00: configured for UDMA/133
[    1.796657] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200BEVT-2 11.0 PQ: 0 ANSI: 5
[    1.796833] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.796869] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.796954] sd 0:0:0:0: [sda] Write Protect is off
[    1.796958] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.797009] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.807765]  sda: sda1 sda2 sda3
[    1.808145] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.947963] usbcore: registered new interface driver uas
[    2.116055] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.122858] ata2.00: ATAPI: TSSTcorp CDDVDW TS-L633A, SC03, max UDMA/100
[    2.122865] ata2.00: applying bridge limits
[    2.165444] ata2.00: configured for UDMA/100
[    2.184039] usb 3-1: new low speed USB device number 2 using uhci_hcd
[    2.271727] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L633A  SC03 PQ: 0 ANSI: 5
[    2.337283] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.337288] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.337469] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.337548] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.656069] ata5: SATA link down (SStatus 0 SControl 300)
[    2.976047] ata6: SATA link down (SStatus 0 SControl 300)
[    2.977231] Initializing USB Mass Storage driver...
[    2.980123] scsi6 : usb-storage 2-3:1.0
[    2.980234] usbcore: registered new interface driver usb-storage
[    2.980236] USB Mass Storage support registered.
[    2.994179] input: Logitech USB Laser Mouse as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/input/input5
[    2.994310] generic-usb 0003:046D:C062.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB Laser Mouse] on usb-0000:00:1a.0-1/input0
[    2.994331] usbcore: registered new interface driver usbhid
[    2.994333] usbhid: USB HID core driver
[    3.980461] scsi 6:0:0:0: Direct-Access     JetFlash Transcend 32GB   1.00 PQ: 0 ANSI: 5
[    4.012296] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    4.012906] sd 6:0:0:0: [sdb] 61767680 512-byte logical blocks: (31.6 GB/29.4 GiB)
[    4.013587] sd 6:0:0:0: [sdb] Write Protect is off
[    4.013595] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[    4.013718] sd 6:0:0:0: [sdb] No Caching mode page present
[    4.013725] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    4.014576] sd 6:0:0:0: [sdb] No Caching mode page present
[    4.014579] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    4.018191]  sdb: sdb1 sdb2 < sdb5 sdb6 >
[    4.019195] sd 6:0:0:0: [sdb] No Caching mode page present
[    4.019198] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    4.019204] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    4.173660] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[    7.269570] udevd[325]: starting version 173
[    7.300729] lp: driver loaded but no devices found
[    7.305213] Adding 1998844k swap on /dev/sdb5.  Priority:-1 extents:1 across:1998844k 
[    7.386747] EXT4-fs (sdb1): re-mounted. Opts: errors=remount-ro
[    7.550205] type=1400 audit(1319964314.110:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=494 comm="apparmor_parser"
[    7.558642] type=1400 audit(1319964314.118:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=494 comm="apparmor_parser"
[    7.559136] type=1400 audit(1319964314.118:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=494 comm="apparmor_parser"
[    7.998593] cfg80211: Calling CRDA to update world regulatory domain
[    8.023900] ath5k 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.023920] ath5k 0000:02:00.0: setting latency timer to 64
[    8.024001] ath5k 0000:02:00.0: registered as 'phy0'
[    8.107831] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    8.107901] HDA Intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[    8.107936] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    8.263568] hda_codec: ALC262: BIOS auto-probing.
[    8.345365] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[    8.349894] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[    8.611376] ath: EEPROM regdomain: 0x65
[    8.611379] ath: EEPROM indicates we should expect a direct regpair map
[    8.611383] ath: Country alpha2 being used: 00
[    8.611385] ath: Regpair used: 0x65
[    8.611390] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[    8.611393] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    8.611396] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[    8.611399] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    8.611401] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[    8.611404] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    8.611406] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[    8.611409] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    8.611411] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[    8.611413] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    8.611415] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[    8.611418] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    8.611420] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[    8.611423] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    8.611425] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[    8.611427] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    8.611429] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[    8.611432] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    8.611434] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[    8.611436] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    8.611439] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[    8.611441] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    8.611443] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[    8.611446] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    8.611448] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[    8.611451] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[    8.611453] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[    8.619375] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[    8.619665] Linux video capture interface: v2.00
[    8.621271] uvcvideo: Found UVC 1.00 device Vega USB 2.0 Camera. (0ac8:c302)
[    8.649388] input: Vega USB 2.0 Camera. as /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3:1.0/input/input8
[    8.649518] usbcore: registered new interface driver uvcvideo
[    8.649520] USB Video Class driver (v1.1.0)
[    8.662498] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[    8.664422] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[    8.701273] type=1400 audit(1319964315.262:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=791 comm="apparmor_parser"
[    8.702645] type=1400 audit(1319964315.262:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=792 comm="apparmor_parser"
[    8.705445] type=1400 audit(1319964315.266:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=792 comm="apparmor_parser"
[    8.705947] type=1400 audit(1319964315.266:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=792 comm="apparmor_parser"
[    8.718727] type=1400 audit(1319964315.278:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=795 comm="apparmor_parser"
[    8.723157] type=1400 audit(1319964315.282:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=793 comm="apparmor_parser"
[    8.731475] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1c0b1, caps: 0xa04711/0xa00000/0x0
[    8.731823] type=1400 audit(1319964315.290:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=795 comm="apparmor_parser"
[    8.766148] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input9
[    8.779922] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    8.780827] acpi device:03: registered as cooling_device4
[    8.780977] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input10
[    8.781071] ACPI: Video Device [NVID] (multi-head: yes  rom: no  post: no)
[    8.862413] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[    8.862418] cfg80211: World regulatory domain updated:
[    8.862420] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    8.862423] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.862426] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    8.862430] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    8.862432] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.862435] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.908068] init: failsafe main process (716) killed by TERM signal
[    9.910062] init: apport pre-start process (889) terminated with status 1
[    9.943317] init: apport post-stop process (927) terminated with status 1
```Any ideas what could be my problem(s) (execept myself? ;) )
I read about some problems with more than 3 GB of RAM and my system has 4GB. But I have found no solutions. I tried to install Lubuntu 11.10 (32bit) with the same effects and Ubuntu 11.10 (64bit) but then the PC restarts continiously...

Thanks!!! :)

---

### Post by JohanoFiera on 2012-06-26
I had the same/similar problems with the Samsung R510, model: NP-R510-FS0ANL. (The last 2 letters of the model only identify the country you bought it in, like DE/NL/etc. so it is actually a NP-R510-FS0A)

I tried all the option under F6, (ACPI = off, etc), I tried different versions like Ubuntu 11.10/12.04 CD and DVD versions, both amd64 and i386... but every time the laptop would reboot right after selecting "Install Ubuntu", or trying to boot the live CD of Ubuntu.

Here the fix:

Simply download the BIOS Update from the samsung website and install it via a windows live CD, after that everything works with no more unexpected reboots. :)

I ended up installing Ubuntu 12.04 DVD for 64bit, so not sure if this will work for older/other versions.

Hope this helps someone ;)

---

