---
title: "No USB Support for Any Devices"
date: 2012-05-10
forum: Hardware
---

### Post by Nightreaver1986 on 2012-05-10
Hello. Forgive me if this has been covered/solved already in a previous post, but I've been searching for two hours with no solid resolution, and without a mouse that gets rather time-consuming. (I've had to tab and alt-tab to run everything, opening firefox from the terminal).

Recently I upgraded to ubuntu 12.04, and everything was working fine, or so I assumed. The other day I restarted my computer, the ubuntu login screen came up, but I had no keyboard or mouse input available. 

I am using a Toshiba Satellite L505D-S5965. The touchpad hasn't worked since I got it (ribbon cables have a short), so I use a usb laser mouse instead. After several restarts the keyboard finally started to respond again, but I still cannot get any USB device to respond. I have tried plugging in my external hard drive, and it gets power but the device will not show up on the system even when I try to manually mount it, and the usb mouse simply does not function at all. (It doesn't seem to be getting power most of the time, and when it does get power it flashes periodically).

I've tried using another mouse with the same result, also flash drives, a usb keyboard, anything usb at all refuses to respond.

Running dmesg yields:

> 

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-24-generic (buildd@vernadsky) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #37-Ubuntu SMP Wed Apr 25 08:43:52 UTC 2012 (Ubuntu 3.2.0-24.37-generic 3.2.14)
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
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000afdd7000 (usable)
[    0.000000]  BIOS-e820: 00000000afdd7000 - 00000000afe3f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000afe3f000 - 00000000afe70000 (usable)
[    0.000000]  BIOS-e820: 00000000afe70000 - 00000000afebf000 (reserved)
[    0.000000]  BIOS-e820: 00000000afebf000 - 00000000afeef000 (usable)
[    0.000000]  BIOS-e820: 00000000afeef000 - 00000000afeff000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000afeff000 - 00000000aff00000 (usable)
[    0.000000]  BIOS-e820: 00000000f7000000 - 00000000f8000000 (reserved)
[    0.000000]  BIOS-e820: 00000000feb00000 - 00000000feb01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI 2.4 present.
[    0.000000] DMI: TOSHIBA Satellite L505D/Portable PC, BIOS 1.20 06/18/2009
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0xaff00 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 base 0080000000 mask FFE0000000 write-back
[    0.000000]   2 base 00A0000000 mask FFF0000000 write-back
[    0.000000]   3 base 00FFF00000 mask FFFFF00000 write-protect
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 36504000 - 3727a000
[    0.000000] ACPI: RSDP 000fe020 00024 (v02 TOSINV)
[    0.000000] ACPI: XSDT afefe120 0005C (v01 TOSINV TOSINV00 00000003      01000013)
[    0.000000] ACPI: FACP afefd000 000F4 (v04 TOSINV TOSINV00 00000003 MSFT 01000013)
[    0.000000] ACPI: DSDT afef2000 07EAA (v01 TOSINV TOSINV00 F0000000 MSFT 01000013)
[    0.000000] ACPI: FACS afde0000 00040
[    0.000000] ACPI: HPET afefc000 00038 (v01 TOSINV TOSINV00 00000001 MSFT 01000013)
[    0.000000] ACPI: APIC afefb000 00084 (v02 TOSINV TOSINV00 00000001 MSFT 01000013)
[    0.000000] ACPI: MCFG afefa000 0003C (v01 TOSINV TOSINV00 00000001 MSFT 01000013)
[    0.000000] ACPI: SLIC afef1000 00176 (v01 TOSINV TOSINV00 00000001 MSFT 01000013)
[    0.000000] ACPI: BOOT afef0000 00028 (v01 TOSINV TOSINV00 00000001 MSFT 01000013)
[    0.000000] ACPI: SSDT afeef000 002BE (v01 AMD    PowerNow 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1927MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x000aff00
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[5] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000afdd7
[    0.000000]     0: 0x000afe3f -> 0x000afe70
[    0.000000]     0: 0x000afebf -> 0x000afeef
[    0.000000]     0: 0x000afeff -> 0x000aff00
[    0.000000] On node 0 totalpages: 720328
[    0.000000] free_area_init_node: node 0, pgdat c18258c0, node_mem_map f4f04200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 3855 pages used for memmap
[    0.000000]   HighMem zone: 489260 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x1002a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at aff00000 (gap: aff00000:47100000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f4800000 s31616 r0 d21632 u1048576
[    0.000000] pcpu-alloc: s31616 r0 d21632 u1048576 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 714697
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic root=UUID=561ff062-aaf2-405f-86f3-a9b189532adf ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 11529984 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:000aff00)
[    0.000000] Memory: 2822652k/2882560k available (5627k kernel code, 58660k reserved, 2764k data, 712k init, 1972460k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc1833000 - 0xc18e5000   ( 712 kB)
[    0.000000]       .data : 0xc157ef84 - 0xc1832080   (2764 kB)
[    0.000000]       .text : 0xc1000000 - 0xc157ef84   (5627 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712 16
[    0.000000] CPU 0 irqstacks, hard=f380a000 soft=f380c000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2099.279 MHz processor.
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 4198.55 BogoMIPS (lpj=8397116)
[    0.004011] pid_max: default: 32768 minimum: 301
[    0.004043] Security Framework initialized
[    0.004067] AppArmor: AppArmor initialized
[    0.004070] Yama: becoming mindful.
[    0.004146] Mount-cache hash table entries: 512
[    0.004330] Initializing cgroup subsys cpuacct
[    0.004338] Initializing cgroup subsys memory
[    0.004350] Initializing cgroup subsys devices
[    0.004353] Initializing cgroup subsys freezer
[    0.004357] Initializing cgroup subsys blkio
[    0.004366] Initializing cgroup subsys perf_event
[    0.004397] CPU: Physical Processor ID: 0
[    0.004400] CPU: Processor Core ID: 0
[    0.004405] mce: CPU supports 5 MCE banks
[    0.010656] ACPI: Core revision 20110623
[    0.010662] TOSHIBA Satellite detected - force copy of DSDT to local memory
[    0.010814] ACPI: Forced DSDT copy: length 0x07EAA copied locally, original unmapped
[    0.020015] ftrace: allocating 25954 entries in 51 pages
[    0.024105] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.024487] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.064660] CPU0: AMD Athlon(tm) X2 Dual-Core QL-65 stepping 01
[    0.068003] Performance Events: AMD PMU driver.
[    0.068003] ... version:                0
[    0.068003] ... bit width:              48
[    0.068003] ... generic registers:      4
[    0.068003] ... value mask:             0000ffffffffffff
[    0.068003] ... max period:             00007fffffffffff
[    0.068003] ... fixed-purpose events:   0
[    0.068003] ... event mask:             000000000000000f
[    0.068003] NMI watchdog enabled, takes one hw-pmu counter.
[    0.068003] CPU 1 irqstacks, hard=f38da000 soft=f38dc000
[    0.068003] Booting Node   0, Processors  #1
[    0.068003] smpboot cpu 1: start_ip = 9b000
[    0.008000] Initializing CPU#1
[    0.156009] TSC synchronization [CPU#0 -> CPU#1]:
[    0.156009] Measured 74196835 cycles TSC warp between CPUs, turning off TSC clock.
[    0.156009] Marking TSC unstable due to check_tsc_sync_source failed
[    0.156033] NMI watchdog enabled, takes one hw-pmu counter.
[    0.156065] Brought up 2 CPUs
[    0.156068] Total of 2 processors activated (8388.24 BogoMIPS).
[    0.156671] devtmpfs: initialized
[    0.156671] EVM: security.selinux
[    0.156671] EVM: security.SMACK64
[    0.156671] EVM: security.capability
[    0.156671] PM: Registering ACPI NVS region at afdd7000 (425984 bytes)
[    0.157308] print_constraints: dummy: 
[    0.157342] RTC time:  4:14:17, date: 05/10/12
[    0.157395] NET: Registered protocol family 16
[    0.157439] Trying to unpack rootfs image as initramfs...
[    0.157568] EISA bus registered
[    0.157580] TOM: 00000000c0000000 aka 3072M
[    0.157585] Fam 10h mmconf [mem 0xf7000000-0xf7ffffff]
[    0.157686] Extended Config Space enabled on 0 nodes
[    0.157724] ACPI: bus type pci registered
[    0.157812] PCI: MMCONFIG for domain 0000 [bus 00-0f] at [mem 0xf7000000-0xf7ffffff] (base 0xf7000000)
[    0.157816] PCI: MMCONFIG at [mem 0xf7000000-0xf7ffffff] reserved in E820
[    0.157819] PCI: Using MMCONFIG for extended config space
[    0.157821] PCI: Using configuration type 1 for base access
[    0.160511] bio: create slab <bio-0> at 0
[    0.160622] ACPI: Added _OSI(Module Device)
[    0.160625] ACPI: Added _OSI(Processor Device)
[    0.160628] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.160630] ACPI: Added _OSI(Processor Aggregator Device)
[    0.161770] ACPI: EC: Look up EC in DSDT
[    0.162973] ACPI: Executed 1 blocks of module-level executable AML code
[    0.165227] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.522897] Freeing initrd memory: 13784k freed
[    0.604061] ACPI: Interpreter enabled
[    0.604068] ACPI: (supports S0 S3 S4 S5)
[    0.604093] ACPI: Using IOAPIC for interrupt routing
[    0.609159] ACPI: Power Resource [PFA1] (off)
[    0.609459] ACPI: EC: GPE = 0x7, I/O: command/status = 0x66, data = 0x62
[    0.609640] ACPI: No dock devices found.
[    0.609643] HEST: Table not found.
[    0.609647] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.610132] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.611072] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.611075] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.611079] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.611082] pci_root PNP0A08:00: host bridge window [mem 0x000c0000-0x000c3fff]
[    0.611085] pci_root PNP0A08:00: host bridge window [mem 0x000c4000-0x000c7fff]
[    0.611088] pci_root PNP0A08:00: host bridge window [mem 0x000c8000-0x000cbfff]
[    0.611092] pci_root PNP0A08:00: host bridge window [mem 0x000cc000-0x000cffff]
[    0.611095] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
[    0.611098] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.611101] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.611104] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
[    0.611107] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff]
[    0.611110] pci_root PNP0A08:00: host bridge window [mem 0x000e4000-0x000e7fff]
[    0.611114] pci_root PNP0A08:00: host bridge window [mem 0x000e8000-0x000ebfff]
[    0.611117] pci_root PNP0A08:00: host bridge window [mem 0x000ec000-0x000effff]
[    0.611120] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xf6ffffff]
[    0.611123] pci_root PNP0A08:00: host bridge window [mem 0xf8000000-0xffffffff]
[    0.611132] pci_root PNP0A08:00: ignoring host bridge window [mem 0x000cc000-0x000cffff] (conflicts with Video ROM [mem 0x000c0000-0x000cebff])
[    0.611155] pci 0000:00:00.0: [1022:9600] type 0 class 0x000600
[    0.611243] pci 0000:00:01.0: [1022:9602] type 1 class 0x000604
[    0.611306] pci 0000:00:04.0: [1022:9604] type 1 class 0x000604
[    0.611364] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    0.611369] pci 0000:00:04.0: PME# disabled
[    0.611391] pci 0000:00:05.0: [1022:9605] type 1 class 0x000604
[    0.611447] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.611451] pci 0000:00:05.0: PME# disabled
[    0.611472] pci 0000:00:06.0: [1022:9606] type 1 class 0x000604
[    0.611528] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.611532] pci 0000:00:06.0: PME# disabled
[    0.611578] pci 0000:00:11.0: [1002:4391] type 0 class 0x000106
[    0.611602] pci 0000:00:11.0: reg 10: [io  0x8038-0x803f]
[    0.611615] pci 0000:00:11.0: reg 14: [io  0x804c-0x804f]
[    0.611628] pci 0000:00:11.0: reg 18: [io  0x8030-0x8037]
[    0.611640] pci 0000:00:11.0: reg 1c: [io  0x8048-0x804b]
[    0.611653] pci 0000:00:11.0: reg 20: [io  0x8010-0x801f]
[    0.611666] pci 0000:00:11.0: reg 24: [mem 0xd6408000-0xd64083ff]
[    0.611740] pci 0000:00:12.0: [1002:4397] type 0 class 0x000c03
[    0.611757] pci 0000:00:12.0: reg 10: [mem 0xd6407000-0xd6407fff]
[    0.611840] pci 0000:00:12.1: [1002:4398] type 0 class 0x000c03
[    0.611858] pci 0000:00:12.1: reg 10: [mem 0xd6406000-0xd6406fff]
[    0.611948] pci 0000:00:12.2: [1002:4396] type 0 class 0x000c03
[    0.611973] pci 0000:00:12.2: reg 10: [mem 0xd6408500-0xd64085ff]
[    0.612097] pci 0000:00:12.2: supports D1 D2
[    0.612099] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.612105] pci 0000:00:12.2: PME# disabled
[    0.612132] pci 0000:00:13.0: [1002:4397] type 0 class 0x000c03
[    0.612150] pci 0000:00:13.0: reg 10: [mem 0xd6405000-0xd6405fff]
[    0.612232] pci 0000:00:13.1: [1002:4398] type 0 class 0x000c03
[    0.612250] pci 0000:00:13.1: reg 10: [mem 0xd6404000-0xd6404fff]
[    0.612340] pci 0000:00:13.2: [1002:4396] type 0 class 0x000c03
[    0.612364] pci 0000:00:13.2: reg 10: [mem 0xd6408400-0xd64084ff]
[    0.612469] pci 0000:00:13.2: supports D1 D2
[    0.612471] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.612477] pci 0000:00:13.2: PME# disabled
[    0.612508] pci 0000:00:14.0: [1002:4385] type 0 class 0x000c05
[    0.612636] pci 0000:00:14.1: [1002:439c] type 0 class 0x000101
[    0.612657] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
[    0.612670] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
[    0.612682] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
[    0.612695] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
[    0.612707] pci 0000:00:14.1: reg 20: [io  0x8000-0x800f]
[    0.612785] pci 0000:00:14.2: [1002:4383] type 0 class 0x000403
[    0.612812] pci 0000:00:14.2: reg 10: [mem 0xd6400000-0xd6403fff 64bit]
[    0.612897] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.612902] pci 0000:00:14.2: PME# disabled
[    0.612919] pci 0000:00:14.3: [1002:439d] type 0 class 0x000601
[    0.613016] pci 0000:00:14.4: [1002:4384] type 1 class 0x000604
[    0.613077] pci 0000:00:18.0: [1022:1300] type 0 class 0x000600
[    0.613117] pci 0000:00:18.1: [1022:1301] type 0 class 0x000600
[    0.613146] pci 0000:00:18.2: [1022:1302] type 0 class 0x000600
[    0.613177] pci 0000:00:18.3: [1022:1303] type 0 class 0x000600
[    0.613216] pci 0000:00:18.4: [1022:1304] type 0 class 0x000600
[    0.613292] pci 0000:01:05.0: [1002:9613] type 0 class 0x000300
[    0.613306] pci 0000:01:05.0: reg 10: [mem 0xc0000000-0xcfffffff pref]
[    0.613314] pci 0000:01:05.0: reg 14: [io  0x7000-0x70ff]
[    0.613322] pci 0000:01:05.0: reg 18: [mem 0xd6300000-0xd630ffff]
[    0.613339] pci 0000:01:05.0: reg 24: [mem 0xd6200000-0xd62fffff]
[    0.613369] pci 0000:01:05.0: supports D1 D2
[    0.613417] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.613423] pci 0000:00:01.0:   bridge window [io  0x7000-0x7fff]
[    0.613428] pci 0000:00:01.0:   bridge window [mem 0xd6200000-0xd63fffff]
[    0.613433] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.613488] pci 0000:02:00.0: [10ec:8199] type 0 class 0x000280
[    0.613505] pci 0000:02:00.0: reg 10: [io  0x5000-0x50ff]
[    0.613517] pci 0000:02:00.0: reg 14: [mem 0xd5100000-0xd5103fff]
[    0.613613] pci 0000:02:00.0: supports D1 D2
[    0.613616] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot
[    0.613621] pci 0000:02:00.0: PME# disabled
[    0.620061] pci 0000:00:04.0: PCI bridge to [bus 02-02]
[    0.620067] pci 0000:00:04.0:   bridge window [io  0x5000-0x6fff]
[    0.620071] pci 0000:00:04.0:   bridge window [mem 0xd5100000-0xd61fffff]
[    0.620077] pci 0000:00:04.0:   bridge window [mem 0xd0000000-0xd0ffffff 64bit pref]
[    0.620154] pci 0000:03:00.0: [10ec:8136] type 0 class 0x000200
[    0.620171] pci 0000:03:00.0: reg 10: [io  0x3000-0x30ff]
[    0.620198] pci 0000:03:00.0: reg 18: [mem 0xd1010000-0xd1010fff 64bit pref]
[    0.620215] pci 0000:03:00.0: reg 20: [mem 0xd1000000-0xd100ffff 64bit pref]
[    0.620228] pci 0000:03:00.0: reg 30: [mem 0xfffe0000-0xffffffff pref]
[    0.620287] pci 0000:03:00.0: supports D1 D2
[    0.620290] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.620299] pci 0000:03:00.0: PME# disabled
[    0.628074] pci 0000:00:05.0: PCI bridge to [bus 03-03]
[    0.628080] pci 0000:00:05.0:   bridge window [io  0x3000-0x4fff]
[    0.628084] pci 0000:00:05.0:   bridge window [mem 0xd4100000-0xd50fffff]
[    0.628090] pci 0000:00:05.0:   bridge window [mem 0xd1000000-0xd20fffff 64bit pref]
[    0.628128] pci 0000:00:06.0: PCI bridge to [bus 04-05]
[    0.628133] pci 0000:00:06.0:   bridge window [io  0x2000-0x2fff]
[    0.628137] pci 0000:00:06.0:   bridge window [mem 0xd3100000-0xd40fffff]
[    0.628143] pci 0000:00:06.0:   bridge window [mem 0xd2100000-0xd30fffff 64bit pref]
[    0.628219] pci 0000:00:14.4: PCI bridge to [bus 80-8f]
[    0.628225] pci 0000:00:14.4:   bridge window [io  0x1000-0x1fff]
[    0.628251] pci_bus 0000:00: on NUMA node 0
[    0.628256] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.628371] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.628418] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[    0.628464] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]
[    0.628513] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[    0.628598] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.628645]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.628649]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.628652] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.635599] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.635654] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.635704] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.635753] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.635802] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.635852] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.635901] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.635950] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.636215] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.636215] vgaarb: loaded
[    0.636215] vgaarb: bridge control possible 0000:01:05.0
[    0.636237] i2c-core: driver [aat2870] using legacy suspend method
[    0.636240] i2c-core: driver [aat2870] using legacy resume method
[    0.636349] SCSI subsystem initialized
[    0.636401] libata version 3.00 loaded.
[    0.636401] core: registered new interface driver usbfs
[    0.636401] usbcore: registered new interface driver hub
[    0.636401] usbcore: registered new device driver usb
[    0.636401] PCI: Using ACPI for IRQ routing
[    0.636585] PCI: pci_cache_line_size set to 64 bytes
[    0.636764] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.636767] reserve RAM buffer: 00000000afdd7000 - 00000000afffffff 
[    0.636771] reserve RAM buffer: 00000000afe70000 - 00000000afffffff 
[    0.636774] reserve RAM buffer: 00000000afeef000 - 00000000afffffff 
[    0.636777] reserve RAM buffer: 00000000aff00000 - 00000000afffffff 
[    0.636930] NetLabel: Initializing
[    0.636933] NetLabel:  domain hash size = 128
[    0.636935] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.636952] NetLabel:  unlabeled traffic allowed by default
[    0.637000] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.637000] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.638116] Switching to clocksource hpet
[    0.645559] AppArmor: AppArmor Filesystem Enabled
[    0.645603] pnp: PnP ACPI init
[    0.645631] ACPI: bus type pnp registered
[    0.646293] pnp 00:00: [bus 00-ff]
[    0.646297] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.646300] pnp 00:00: [io  0x0d00-0xffff window]
[    0.646303] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.646306] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.646309] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.646312] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.646315] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.646318] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.646321] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.646324] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.646327] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.646330] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.646333] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.646336] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.646339] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.646342] pnp 00:00: [mem 0xc0000000-0xf6ffffff window]
[    0.646345] pnp 00:00: [mem 0xf8000000-0xffffffff window]
[    0.646348] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.646443] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.646497] pnp 00:01: [mem 0xfec00000-0xfec00fff]
[    0.646500] pnp 00:01: [mem 0xfee00000-0xfee00fff]
[    0.646575] system 00:01: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.646579] system 00:01: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.646583] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.646714] pnp 00:02: [irq 0 disabled]
[    0.646728] pnp 00:02: [irq 8]
[    0.646730] pnp 00:02: [mem 0xfed00000-0xfed003ff]
[    0.646769] pnp 00:02: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.646798] pnp 00:03: [io  0x0000-0x000f]
[    0.646801] pnp 00:03: [io  0x0081-0x008f]
[    0.646803] pnp 00:03: [io  0x00c0-0x00df]
[    0.646806] pnp 00:03: [dma 4]
[    0.646841] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.646851] pnp 00:04: [io  0x00f0-0x00fe]
[    0.646861] pnp 00:04: [irq 13]
[    0.646896] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.646927] pnp 00:05: [io  0x0070-0x0071]
[    0.646968] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.646978] pnp 00:06: [io  0x0061]
[    0.647014] pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.647026] pnp 00:07: [io  0x0060]
[    0.647029] pnp 00:07: [io  0x0064]
[    0.647047] pnp 00:07: [irq 1]
[    0.647088] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.647108] pnp 00:08: [irq 12]
[    0.647151] pnp 00:08: Plug and Play ACPI device, IDs SYN191b SYN1900 SYN0002 PNP0f13 (active)
[    0.647169] pnp 00:09: [io  0x0010-0x001f]
[    0.647172] pnp 00:09: [io  0x002e-0x002f]
[    0.647175] pnp 00:09: [io  0x0068]
[    0.647177] pnp 00:09: [io  0x006c]
[    0.647180] pnp 00:09: [io  0x0072-0x0073]
[    0.647182] pnp 00:09: [io  0x0080]
[    0.647185] pnp 00:09: [io  0x00b0-0x00b1]
[    0.647187] pnp 00:09: [io  0x0092]
[    0.647190] pnp 00:09: [io  0x0400-0x04cf]
[    0.647192] pnp 00:09: [io  0x04d0-0x04d1]
[    0.647195] pnp 00:09: [io  0x04d6]
[    0.647197] pnp 00:09: [io  0x0680-0x06ff]
[    0.647200] pnp 00:09: [io  0x077a]
[    0.647202] pnp 00:09: [io  0x0c00-0x0c01]
[    0.647205] pnp 00:09: [io  0x0c14]
[    0.647207] pnp 00:09: [io  0x0c50-0x0c52]
[    0.647209] pnp 00:09: [io  0x0c6c]
[    0.647212] pnp 00:09: [io  0x0c6f]
[    0.647214] pnp 00:09: [io  0x0cd0-0x0cdb]
[    0.647217] pnp 00:09: [io  0x0022-0x0023]
[    0.647219] pnp 00:09: [io  0x00b8]
[    0.647222] pnp 00:09: [io  0x0800-0x0804]
[    0.647224] pnp 00:09: [io  0x0b00-0x0b3f]
[    0.647227] pnp 00:09: [io  0x0cdc-0x0cdf]
[    0.647312] system 00:09: [io  0x0400-0x04cf] has been reserved
[    0.647315] system 00:09: [io  0x04d0-0x04d1] has been reserved
[    0.647318] system 00:09: [io  0x04d6] has been reserved
[    0.647321] system 00:09: [io  0x0680-0x06ff] has been reserved
[    0.647325] system 00:09: [io  0x077a] has been reserved
[    0.647328] system 00:09: [io  0x0c00-0x0c01] has been reserved
[    0.647331] system 00:09: [io  0x0c14] has been reserved
[    0.647334] system 00:09: [io  0x0c50-0x0c52] has been reserved
[    0.647337] system 00:09: [io  0x0c6c] has been reserved
[    0.647340] system 00:09: [io  0x0c6f] has been reserved
[    0.647343] system 00:09: [io  0x0cd0-0x0cdb] has been reserved
[    0.647347] system 00:09: [io  0x0800-0x0804] has been reserved
[    0.647350] system 00:09: [io  0x0b00-0x0b3f] has been reserved
[    0.647354] system 00:09: [io  0x0cdc-0x0cdf] has been reserved
[    0.647357] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.647404] pnp 00:0a: [mem 0xff800000-0xff80ffff]
[    0.647407] pnp 00:0a: [mem 0x000e0000-0x000fffff]
[    0.647410] pnp 00:0a: [mem 0xfeb00000-0xfeb00fff]
[    0.647413] pnp 00:0a: [mem 0xfff00000-0xffffffff]
[    0.647480] system 00:0a: [mem 0xff800000-0xff80ffff] has been reserved
[    0.647484] system 00:0a: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.647487] system 00:0a: [mem 0xfeb00000-0xfeb00fff] has been reserved
[    0.647491] system 00:0a: [mem 0xfff00000-0xffffffff] has been reserved
[    0.647494] system 00:0a: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.647667] pnp: PnP ACPI: found 11 devices
[    0.647669] ACPI: ACPI bus type pnp unregistered
[    0.647673] PnPBIOS: Disabled by ACPI PNP
[    0.686168] pci 0000:03:00.0: no compatible bridge window for [mem 0xfffe0000-0xffffffff pref]
[    0.686174] PCI: max bus depth: 1 pci_try_num: 2
[    0.686209] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.686213] pci 0000:00:01.0:   bridge window [io  0x7000-0x7fff]
[    0.686218] pci 0000:00:01.0:   bridge window [mem 0xd6200000-0xd63fffff]
[    0.686222] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.686228] pci 0000:00:04.0: PCI bridge to [bus 02-02]
[    0.686232] pci 0000:00:04.0:   bridge window [io  0x5000-0x6fff]
[    0.686237] pci 0000:00:04.0:   bridge window [mem 0xd5100000-0xd61fffff]
[    0.686241] pci 0000:00:04.0:   bridge window [mem 0xd0000000-0xd0ffffff 64bit pref]
[    0.686250] pci 0000:03:00.0: BAR 6: assigned [mem 0xd1020000-0xd103ffff pref]
[    0.686254] pci 0000:00:05.0: PCI bridge to [bus 03-03]
[    0.686258] pci 0000:00:05.0:   bridge window [io  0x3000-0x4fff]
[    0.686262] pci 0000:00:05.0:   bridge window [mem 0xd4100000-0xd50fffff]
[    0.686267] pci 0000:00:05.0:   bridge window [mem 0xd1000000-0xd20fffff 64bit pref]
[    0.686272] pci 0000:00:06.0: PCI bridge to [bus 04-05]
[    0.686276] pci 0000:00:06.0:   bridge window [io  0x2000-0x2fff]
[    0.686281] pci 0000:00:06.0:   bridge window [mem 0xd3100000-0xd40fffff]
[    0.686285] pci 0000:00:06.0:   bridge window [mem 0xd2100000-0xd30fffff 64bit pref]
[    0.686291] pci 0000:00:14.4: PCI bridge to [bus 80-8f]
[    0.686298] pci 0000:00:14.4:   bridge window [io  0x1000-0x1fff]
[    0.686321] pci 0000:00:01.0: setting latency timer to 64
[    0.686338] pci 0000:00:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.686342] pci 0000:00:04.0: setting latency timer to 64
[    0.686353] pci 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.686357] pci 0000:00:05.0: setting latency timer to 64
[    0.686367] pci 0000:00:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.686372] pci 0000:00:06.0: setting latency timer to 64
[    0.686381] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.686384] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.686387] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.686391] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.686394] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.686397] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.686400] pci_bus 0000:00: resource 10 [mem 0x000d0000-0x000d3fff]
[    0.686403] pci_bus 0000:00: resource 11 [mem 0x000d4000-0x000d7fff]
[    0.686406] pci_bus 0000:00: resource 12 [mem 0x000d8000-0x000dbfff]
[    0.686409] pci_bus 0000:00: resource 13 [mem 0x000dc000-0x000dffff]
[    0.686412] pci_bus 0000:00: resource 14 [mem 0x000e0000-0x000e3fff]
[    0.686415] pci_bus 0000:00: resource 15 [mem 0x000e4000-0x000e7fff]
[    0.686418] pci_bus 0000:00: resource 16 [mem 0x000e8000-0x000ebfff]
[    0.686421] pci_bus 0000:00: resource 17 [mem 0x000ec000-0x000effff]
[    0.686424] pci_bus 0000:00: resource 18 [mem 0xc0000000-0xf6ffffff]
[    0.686427] pci_bus 0000:00: resource 19 [mem 0xf8000000-0xffffffff]
[    0.686430] pci_bus 0000:01: resource 0 [io  0x7000-0x7fff]
[    0.686433] pci_bus 0000:01: resource 1 [mem 0xd6200000-0xd63fffff]
[    0.686436] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.686440] pci_bus 0000:02: resource 0 [io  0x5000-0x6fff]
[    0.686443] pci_bus 0000:02: resource 1 [mem 0xd5100000-0xd61fffff]
[    0.686446] pci_bus 0000:02: resource 2 [mem 0xd0000000-0xd0ffffff 64bit pref]
[    0.686449] pci_bus 0000:03: resource 0 [io  0x3000-0x4fff]
[    0.686452] pci_bus 0000:03: resource 1 [mem 0xd4100000-0xd50fffff]
[    0.686455] pci_bus 0000:03: resource 2 [mem 0xd1000000-0xd20fffff 64bit pref]
[    0.686458] pci_bus 0000:04: resource 0 [io  0x2000-0x2fff]
[    0.686461] pci_bus 0000:04: resource 1 [mem 0xd3100000-0xd40fffff]
[    0.686464] pci_bus 0000:04: resource 2 [mem 0xd2100000-0xd30fffff 64bit pref]
[    0.686468] pci_bus 0000:80: resource 0 [io  0x1000-0x1fff]
[    0.686518] NET: Registered protocol family 2
[    0.686600] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.686898] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.687604] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.687934] TCP: Hash tables configured (established 131072 bind 65536)
[    0.687937] TCP reno registered
[    0.687941] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.687954] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.688110] NET: Registered protocol family 1
[    0.688126] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
[    0.688158] pci 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.780030] pci 0000:00:12.0: PCI INT A disabled
[    0.780041] pci 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.860046] pci 0000:00:12.1: PCI INT A disabled
[    0.860064] pci 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.860236] pci 0000:00:12.2: EHCI: unrecognized capability 00
[    0.860245] pci 0000:00:12.2: PCI INT B disabled
[    0.860255] pci 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.952026] pci 0000:00:13.0: PCI INT A disabled
[    0.952036] pci 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.032037] pci 0000:00:13.1: PCI INT A disabled
[    1.032112] pci 0000:00:13.2: power state changed by ACPI to D0
[    1.032122] pci 0000:00:13.2: power state changed by ACPI to D0
[    1.032138] pci 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.032304] pci 0000:00:13.2: EHCI: unrecognized capability 00
[    1.032686] pci 0000:00:13.2: PCI INT B disabled
[    1.032717] pci 0000:01:05.0: Boot video device
[    1.032748] PCI: CLS 64 bytes, default 64
[    1.032759] Simple Boot Flag at 0x44 set to 0x1
[    1.033268] audit: initializing netlink socket (disabled)
[    1.033279] type=2000 audit(1336623257.028:1): initialized
[    1.067063] highmem bounce pool size: 64 pages
[    1.067071] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.088352] VFS: Disk quotas dquot_6.5.2
[    1.088434] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.089209] fuse init (API version 7.17)
[    1.089354] msgmni has been set to 1687
[    1.089953] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.090001] io scheduler noop registered
[    1.090006] io scheduler deadline registered
[    1.090019] io scheduler cfq registered (default)
[    1.090215] pcieport 0000:00:04.0: setting latency timer to 64
[    1.090265] pcieport 0000:00:04.0: irq 40 for MSI/MSI-X
[    1.090331] pcieport 0000:00:05.0: setting latency timer to 64
[    1.090365] pcieport 0000:00:05.0: irq 41 for MSI/MSI-X
[    1.090424] pcieport 0000:00:06.0: setting latency timer to 64
[    1.090459] pcieport 0000:00:06.0: irq 42 for MSI/MSI-X
[    1.090554] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.090589] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.090760] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.090837] ACPI: AC Adapter [ADP0] (on-line)
[    1.090929] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.090936] ACPI: Power Button [PWRB]
[    1.090997] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    1.096386] ACPI: Lid Switch [LID]
[    1.096449] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    1.096453] ACPI: Power Button [PWRF]
[    1.096533] ACPI: Fan [FAN1] (off)
[    1.098063] thermal LNXTHERM:00: registered as thermal_zone0
[    1.098066] ACPI: Thermal Zone [THZN] (70 C)
[    1.098087] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.098098] ACPI: Battery Slot [BAT0] (battery present)
[    1.098138] ERST: Table is not found!
[    1.098140] GHES: HEST is not enabled!
[    1.098289] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.099202] ACPI: Battery Slot [BAT0] (battery present)
[    1.099224] isapnp: Scanning for PnP cards...
[    1.457044] isapnp: No Plug & Play device found
[    1.496556] Linux agpgart interface v0.103
[    1.498838] brd: module loaded
[    1.500023] loop: module loaded
[    1.500186] ahci 0000:00:11.0: version 3.0
[    1.500219] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.500367] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.500372] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck led clo pmp pio ccc 
[    1.501443] scsi0 : ahci
[    1.501620] scsi1 : ahci
[    1.501752] scsi2 : ahci
[    1.501876] scsi3 : ahci
[    1.502168] ata1: SATA max UDMA/133 abar m1024@0xd6408000 port 0xd6408100 irq 22
[    1.502173] ata2: SATA max UDMA/133 abar m1024@0xd6408000 port 0xd6408180 irq 22
[    1.502178] ata3: SATA max UDMA/133 abar m1024@0xd6408000 port 0xd6408200 irq 22
[    1.502182] ata4: SATA max UDMA/133 abar m1024@0xd6408000 port 0xd6408280 irq 22
[    1.502381] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.502436] pata_acpi 0000:00:14.1: setting latency timer to 64
[    1.502955] Fixed MDIO Bus: probed
[    1.502987] tun: Universal TUN/TAP device driver, 1.6
[    1.502989] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.503080] PPP generic driver version 2.4.2
[    1.503249] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.503268] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.503293] ehci_hcd 0000:00:12.2: setting latency timer to 64
[    1.503297] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    1.503362] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.503527] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.503633] QUIRK: Enable AMD PLL fix
[    1.503637] ehci_hcd 0000:00:12.2: applying AMD SB600/SB700 USB freeze workaround
[    1.503730] ehci_hcd 0000:00:12.2: debug port 15 IN USE
[    1.528051] ehci_hcd 0000:00:12.2: irq 17, io mem 0xd6408500
[    1.528290] ehci_hcd 0000:00:12.2: startup error -19
[    1.528300] ehci_hcd 0000:00:12.2: USB bus 1 deregistered
[    1.528413] ehci_hcd 0000:00:12.2: PCI INT B disabled
[    1.528416] ehci_hcd 0000:00:12.2: init 0000:00:12.2 fail, -19
[    1.528432] ehci_hcd 0000:00:13.2: power state changed by ACPI to D0
[    1.528438] ehci_hcd 0000:00:13.2: power state changed by ACPI to D0
[    1.528445] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.528457] ehci_hcd 0000:00:13.2: setting latency timer to 64
[    1.528461] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.528528] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
[    1.528843] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.529076] ehci_hcd 0000:00:13.2: applying AMD SB600/SB700 USB freeze workaround
[    1.529168] ehci_hcd 0000:00:13.2: debug port 15 IN USE
[    1.556039] ehci_hcd 0000:00:13.2: irq 19, io mem 0xd6408400
[    1.556499] ehci_hcd 0000:00:13.2: startup error -19
[    1.556506] ehci_hcd 0000:00:13.2: USB bus 1 deregistered
[    1.556589] ehci_hcd 0000:00:13.2: PCI INT B disabled
[    1.556592] ehci_hcd 0000:00:13.2: init 0000:00:13.2 fail, -19
[    1.556614] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.556629] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.556641] ohci_hcd 0000:00:12.0: setting latency timer to 64
[    1.556646] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.556705] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 1
[    1.556733] ohci_hcd 0000:00:12.0: irq 16, io mem 0xd6407000
[    1.616182] hub 1-0:1.0: USB hub found
[    1.616194] hub 1-0:1.0: 3 ports detected
[    1.616298] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.616312] ohci_hcd 0000:00:12.1: setting latency timer to 64
[    1.616316] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    1.616382] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 2
[    1.616400] ohci_hcd 0000:00:12.1: irq 16, io mem 0xd6406000
[    1.676160] hub 2-0:1.0: USB hub found
[    1.676171] hub 2-0:1.0: 3 ports detected
[    1.676269] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.676285] ohci_hcd 0000:00:13.0: setting latency timer to 64
[    1.676289] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.676353] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 3
[    1.676381] ohci_hcd 0000:00:13.0: irq 18, io mem 0xd6405000
[    1.736171] hub 3-0:1.0: USB hub found
[    1.736182] hub 3-0:1.0: 3 ports detected
[    1.736265] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.736278] ohci_hcd 0000:00:13.1: setting latency timer to 64
[    1.736282] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    1.736349] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 4
[    1.736370] ohci_hcd 0000:00:13.1: irq 18, io mem 0xd6404000
[    1.796157] hub 4-0:1.0: USB hub found
[    1.796167] hub 4-0:1.0: 3 ports detected
[    1.796266] uhci_hcd: USB Universal Host Controller Interface driver
[    1.796356] usbcore: registered new interface driver libusual
[    1.796416] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.820754] ata1: SATA link down (SStatus 0 SControl 300)
[    1.820819] ata4: SATA link down (SStatus 0 SControl 300)
[    1.823783] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.823792] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.824017] mousedev: PS/2 mouse device common for all mice
[    1.824894] rtc_cmos 00:05: RTC can wake from S4
[    1.825027] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.825057] rtc0: alarms up to one day, 114 bytes nvram, hpet irqs
[    1.825150] device-mapper: uevent: version 1.0.3
[    1.825255] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    1.825297] EISA: Probing bus 0 at eisa.0
[    1.825301] EISA: Cannot allocate resource for mainboard
[    1.825304] Cannot allocate resource for EISA slot 1
[    1.825307] Cannot allocate resource for EISA slot 2
[    1.825310] Cannot allocate resource for EISA slot 3
[    1.825312] Cannot allocate resource for EISA slot 4
[    1.825315] Cannot allocate resource for EISA slot 5
[    1.825318] Cannot allocate resource for EISA slot 6
[    1.825321] Cannot allocate resource for EISA slot 7
[    1.825323] Cannot allocate resource for EISA slot 8
[    1.825326] EISA: Detected 0 cards.
[    1.825342] cpufreq-nforce2: No nForce2 chipset.
[    1.825346] cpuidle: using governor ladder
[    1.825348] cpuidle: using governor menu
[    1.825351] EFI Variables Facility v0.08 2004-May-17
[    1.825635] TCP cubic registered
[    1.825788] NET: Registered protocol family 10
[    1.826426] NET: Registered protocol family 17
[    1.826446] Registering the dns_resolver key type
[    1.826474] Using IPI No-Shortcut mode
[    1.826645] PM: Hibernation image not present or could not be loaded.
[    1.826663] registered taskstats version 1
[    1.845104]   Magic number: 12:333:211
[    1.845241] rtc_cmos 00:05: setting system clock to 2012-05-10 04:14:18 UTC (1336623258)
[    1.845253] powernow-k8: Found 1 AMD Athlon(tm) X2 Dual-Core QL-65 (2 cpu cores) (version 2.20.00)
[    1.845326] powernow-k8:    0 : pstate 0 (2100 MHz)
[    1.845328] powernow-k8:    1 : pstate 1 (1050 MHz)
[    1.845772] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.845777] EDD information not available.
[    1.855077] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.992033] ata3: softreset failed (device not ready)
[    1.992037] ata3: applying PMP SRST workaround and retrying
[    1.992059] ata2: softreset failed (device not ready)
[    1.992063] ata2: applying PMP SRST workaround and retrying
[    2.164039] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.164071] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.177734] ata3.00: ATAPI: TSSTcorp CDDVDW TS-L633P, TO03, max UDMA/100
[    2.191129] ata3.00: configured for UDMA/100
[    2.217089] ata2.00: ATA-8: TOSHIBA MK2555GSX, FG001M, max UDMA/100
[    2.217092] ata2.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.217889] ata2.00: configured for UDMA/100
[    2.218120] scsi 1:0:0:0: Direct-Access     ATA      TOSHIBA MK2555GS FG00 PQ: 0 ANSI: 5
[    2.218308] sd 1:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    2.218328] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    2.218371] sd 1:0:0:0: [sda] Write Protect is off
[    2.218375] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.218402] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.220868] scsi 2:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L633P  TO03 PQ: 0 ANSI: 5
[    2.225418] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.225421] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.225582] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    2.225670] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    2.299863]  sda: sda1 sda2 < sda5 >
[    2.300395] sd 1:0:0:0: [sda] Attached SCSI disk
[    2.300446] Freeing unused kernel memory: 712k freed
[    2.300930] Write protecting the kernel text: 5628k
[    2.300988] Write protecting the kernel read-only data: 2324k
[    2.325326] udevd[92]: starting version 175
[    2.398785] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.398839] r8169 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.398894] r8169 0000:03:00.0: setting latency timer to 64
[    2.398966] r8169 0000:03:00.0: irq 43 for MSI/MSI-X
[    2.399598] r8169 0000:03:00.0: eth0: RTL8102e at 0xf8006000, 00:1e:33:d7:ef:da, XID 04c00000 IRQ 43
[    2.435770] scsi4 : pata_atiixp
[    2.436844] scsi5 : pata_atiixp
[    2.437512] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8000 irq 14
[    2.437516] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8008 irq 15
[    2.437699] ata5: port disabled--ignoring
[    2.864150] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    7.032045] usb 1-3: new low-speed USB device number 2 using ohci_hcd
[    7.172047] usb 1-3: device descriptor read/64, error -62
[    7.416055] usb 1-3: device descriptor read/64, error -62
[    7.570855] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    7.656065] usb 1-3: new low-speed USB device number 3 using ohci_hcd
[    7.796069] usb 1-3: device descriptor read/64, error -62
[    8.016284] Adding 2879484k swap on /dev/sda5.  Priority:-1 extents:1 across:2879484k 
[    8.040055] usb 1-3: device descriptor read/64, error -62
[    8.054644] udevd[404]: starting version 175
[    8.280076] usb 1-3: new low-speed USB device number 4 using ohci_hcd
[    8.688026] usb 1-3: device not accepting address 4, error -62
[    8.824031] usb 1-3: new low-speed USB device number 5 using ohci_hcd
[    9.154650] lp: driver loaded but no devices found
[    9.154922] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    9.232030] usb 1-3: device not accepting address 5, error -62
[    9.232073] hub 1-0:1.0: unable to enumerate USB device on port 3
[   10.206959] wmi: Mapper loaded
[   10.273598] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.328964] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   10.530664] acpi device:03: registered as cooling_device3
[   10.530760] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input4
[   10.530841] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   10.777351] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.19
[   10.779562] input: Toshiba input device as /devices/virtual/input/input5
[   10.788263] Registered led device: toshiba::illumination
[   10.917453] r8187se: module is from the staging directory, the quality is unknown, you have been warned.
[   10.919128] ieee80211_crypt: registered algorithm 'NULL'
[   10.919132] ieee80211_crypt: registered algorithm 'TKIP'
[   10.919134] ieee80211_crypt: registered algorithm 'CCMP'
[   10.919137] ieee80211_crypt: registered algorithm 'WEP'
[   10.919139] 
[   10.919140] Linux kernel driver for RTL8180 / RTL8185 based WLAN cards
[   10.919142] Copyright (c) 2004-2005, Andrea Merello
[   10.919144] r8180: Initializing module
[   10.919146] r8180: Wireless extensions version 22
[   10.919148] r8180: Initializing proc filesystem
[   10.919186] r8180: Configuring chip resources
[   10.919203] r8180 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.919211] r8180 0000:02:00.0: setting latency timer to 64
[   10.921581] rtl8180_init:Error channel plan! Set to default.
[   10.921583] r8180: Channel plan is 0
[   10.921585] 
[   10.921587] Dot11d_Init()
[   10.921592] r8180: MAC controller is a RTL8187SE b/g
[   10.923702] r8180: usValue is 0x104
[   10.923703] 
[   10.966194] r8180: EEPROM version 104
[   10.970453] r8180: WW:**PLEASE** REPORT SUCCESSFUL/UNSUCCESSFUL TO Realtek!
[   10.971051] r8180: IRQ 16
[   10.971712] r8180: Driver probe completed
[   10.971714] 
[   10.981440] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
[   10.981617] SP5100 TCO timer: mmio address 0xfec000f0 already in use
[   11.511049] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   11.511056] Disabling lock debugging due to kernel taint
[   11.704806] [fglrx] Maximum main memory to use for locked dma buffers: 2629 MBytes.
[   11.704928] [fglrx]   vendor: 1002 device: 9613 count: 1
[   11.705653] [fglrx] ioport: bar 1, base 0x7000, size: 0x100
[   11.705671] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   11.705678] pci 0000:01:05.0: setting latency timer to 64
[   11.706317] [fglrx] Kernel PAT support is enabled
[   11.706343] [fglrx] module loaded - fglrx 8.96.4 [Mar 12 2012] with 1 minors
[   12.526787] type=1400 audit(1336623269.175:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=607 comm="apparmor_parser"
[   12.526814] type=1400 audit(1336623269.175:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=631 comm="apparmor_parser"
[   12.527293] type=1400 audit(1336623269.175:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=607 comm="apparmor_parser"
[   12.527328] type=1400 audit(1336623269.175:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=631 comm="apparmor_parser"
[   12.527581] type=1400 audit(1336623269.175:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=607 comm="apparmor_parser"
[   12.527625] type=1400 audit(1336623269.175:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=631 comm="apparmor_parser"
[   12.528488] type=1400 audit(1336623269.179:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=596 comm="apparmor_parser"
[   12.528998] type=1400 audit(1336623269.179:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=596 comm="apparmor_parser"
[   12.529292] type=1400 audit(1336623269.179:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=596 comm="apparmor_parser"
[   12.540498] snd_hda_intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.540551] snd_hda_intel 0000:00:14.2: setting latency timer to 64
[   12.676511] input: HDA ATI SB Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input6
[   12.676784] input: HDA ATI SB Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input7
[   15.365841] init: failsafe main process (697) killed by TERM signal
[   16.692770] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[   16.692776] vesafb: scrolling: redraw
[   16.692780] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[   16.694091] vesafb: framebuffer at 0xc0000000, mapped to 0xf8800000, using 3072k, total 3072k
[   16.694355] Console: switching to colour frame buffer device 128x48
[   16.694386] fb0: VESA VGA frame buffer device
[   18.995388] ppdev: user-space parallel port driver
[   20.179018] Bluetooth: Core ver 2.16
[   20.179054] NET: Registered protocol family 31
[   20.179057] Bluetooth: HCI device and connection manager initialized
[   20.179061] Bluetooth: HCI socket layer initialized
[   20.179065] Bluetooth: L2CAP socket layer initialized
[   20.179072] Bluetooth: SCO socket layer initialized
[   20.211474] Bluetooth: RFCOMM TTY layer initialized
[   20.211483] Bluetooth: RFCOMM socket layer initialized
[   20.211485] Bluetooth: RFCOMM ver 1.11
[   20.387129] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.387134] Bluetooth: BNEP filters: protocol multicast
[   20.474875] type=1400 audit(1336623277.127:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=821 comm="apparmor_parser"
[   20.475475] type=1400 audit(1336623277.127:12): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=821 comm="apparmor_parser"
[   23.148111] r8180: Bringing up iface
[   23.285774] type=1400 audit(1336623279.935:13): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=874 comm="apparmor_parser"
[   23.288074] type=1400 audit(1336623279.939:14): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=874 comm="apparmor_parser"
[   23.288580] type=1400 audit(1336623279.939:15): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=874 comm="apparmor_parser"
[   23.346623] r8180: Card successfully reset
[   23.346948] type=1400 audit(1336623279.995:16): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=873 comm="apparmor_parser"
[   23.484728] type=1400 audit(1336623280.135:17): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=877 comm="apparmor_parser"
[   23.485337] type=1400 audit(1336623280.135:18): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=877 comm="apparmor_parser"
[   23.492104] type=1400 audit(1336623280.143:19): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=878 comm="apparmor_parser"
[   23.492725] type=1400 audit(1336623280.143:20): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=878 comm="apparmor_parser"
[   24.083807] r8180: WIRELESS_MODE_G
[   24.083808] 
[   24.100286] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.100687] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.111546] r8169 0000:03:00.0: eth0: link down
[   24.112190] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   24.112805] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.142657] vboxdrv: Found 2 processor cores.
[   26.143357] vboxdrv: fAsync=1 offMin=0x46c204c offMax=0x46c204c
[   26.143449] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
[   26.143451] vboxdrv: Successfully loaded version 4.1.12_Ubuntu (interface 0x00190000).
[   26.598818] vboxpci: IOMMU not found (not registered)
[   28.844744] [fglrx] GART Table is not in FRAME_BUFFER range 
[   28.845247] [fglrx] Could not enable MSI; System prevented initialization
[   28.846265] [fglrx] Firegl kernel thread PID: 1061
[   28.846362] [fglrx] Firegl kernel thread PID: 1062
[   28.846458] [fglrx] Firegl kernel thread PID: 1063
[   28.846619] [fglrx] IRQ 18 Enabled
[   29.712386] [fglrx] Gart USWC size:868 M.
[   29.712392] [fglrx] Gart cacheable size:342 M.
[   29.712398] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   29.712402] [fglrx] Reserved FB block: Unshared offset:fffb000, size:5000 
[   29.748121] =>>>>>>>>>>=============================>set power:1, 0!
[   38.902388] Linking with Dyer: channel is 1
[   38.942927] Linking with Dyer: channel is 1
[   38.960299] Associated successfully
[   38.960301] Using G rates
[   38.974082] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   39.984511] =>>>>>>>>>>=============================>set power:1, 0!
[   45.576048] usb 1-3: new low-speed USB device number 6 using ohci_hcd
[   45.716048] usb 1-3: device descriptor read/64, error -62
[   45.960059] usb 1-3: device descriptor read/64, error -62
[   46.200104] usb 1-3: new low-speed USB device number 7 using ohci_hcd
[   46.340042] usb 1-3: device descriptor read/64, error -62
[   46.584074] usb 1-3: device descriptor read/64, error -62
[   46.824059] usb 1-3: new low-speed USB device number 8 using ohci_hcd
[   47.232033] usb 1-3: device not accepting address 8, error -62
[   47.368036] usb 1-3: new low-speed USB device number 9 using ohci_hcd
[   47.776037] usb 1-3: device not accepting address 9, error -62
[   47.776107] hub 1-0:1.0: unable to enumerate USB device on port 3
[   49.816032] wlan0: no IPv6 routers present
[ 1022.921290] init: anacron main process (938) killed by TERM signal
[ 1023.108694] =>>>>>>>>>>=============================>set power:0, 0!
[ 1023.108700] Timeout 1
[ 1031.249453] =>>>>>>>>>>=============================>set power:1, 0!
[ 1047.080074] usb 1-3: new low-speed USB device number 10 using ohci_hcd
[ 1047.220060] usb 1-3: device descriptor read/64, error -62
[ 1047.464066] usb 1-3: device descriptor read/64, error -62
[ 1047.704064] usb 1-3: new low-speed USB device number 11 using ohci_hcd
[ 1047.844051] usb 1-3: device descriptor read/64, error -62
[ 1048.088057] usb 1-3: device descriptor read/64, error -62
[ 1048.328050] usb 1-3: new low-speed USB device number 12 using ohci_hcd
[ 1048.736044] usb 1-3: device not accepting address 12, error -62
[ 1048.872055] usb 1-3: new low-speed USB device number 13 using ohci_hcd
[ 1049.280061] usb 1-3: device not accepting address 13, error -62
[ 1049.280079] hub 1-0:1.0: unable to enumerate USB device on port 3
[ 1055.324069] usb 1-3: new low-speed USB device number 14 using ohci_hcd
[ 1055.464079] usb 1-3: device descriptor read/64, error -62
[ 1055.628090] hub 1-0:1.0: unable to enumerate USB device on port 3
[ 1056.992062] usb 1-3: new low-speed USB device number 15 using ohci_hcd
[ 1057.132066] usb 1-3: device descriptor read/64, error -62
[ 1057.376073] usb 1-3: device descriptor read/64, error -62
[ 1057.616066] usb 1-3: new low-speed USB device number 16 using ohci_hcd
[ 1057.756065] usb 1-3: device descriptor read/64, error -62
[ 1058.000059] usb 1-3: device descriptor read/64, error -62
[ 1058.240061] usb 1-3: new low-speed USB device number 17 using ohci_hcd
[ 1058.648050] usb 1-3: device not accepting address 17, error -62
[ 1058.784053] usb 1-3: new low-speed USB device number 18 using ohci_hcd
[ 1059.192036] usb 1-3: device not accepting address 18, error -62
[ 1059.192055] hub 1-0:1.0: unable to enumerate USB device on port 3
[ 1060.472065] usb 1-3: new low-speed USB device number 19 using ohci_hcd
[ 1060.612099] usb 1-3: device descriptor read/64, error -62
[ 1060.856064] usb 1-3: device descriptor read/64, error -62
[ 1061.096067] usb 1-3: new low-speed USB device number 20 using ohci_hcd
[ 1061.236069] usb 1-3: device descriptor read/64, error -62
[ 1061.480069] usb 1-3: device descriptor read/64, error -62
[ 1061.720068] usb 1-3: new low-speed USB device number 21 using ohci_hcd
[ 1062.128052] usb 1-3: device not accepting address 21, error -62
[ 1062.184077] hub 1-0:1.0: unable to enumerate USB device on port 3
[ 1063.352053] usb 1-3: new low-speed USB device number 23 using ohci_hcd
[ 1063.412097] hub 1-0:1.0: unable to enumerate USB device on port 3
[ 1064.852077] usb 1-3: new low-speed USB device number 24 using ohci_hcd
[ 1064.992107] usb 1-3: device descriptor read/64, error -62
[ 1065.236063] usb 1-3: device descriptor read/64, error -62
[ 1065.476079] usb 1-3: new low-speed USB device number 25 using ohci_hcd
[ 1065.616067] usb 1-3: device descriptor read/64, error -62
[ 1065.860089] usb 1-3: device descriptor read/64, error -62
[ 1066.100078] usb 1-3: new low-speed USB device number 26 using ohci_hcd
[ 1066.508068] usb 1-3: device not accepting address 26, error -62
[ 1066.644071] usb 1-3: new low-speed USB device number 27 using ohci_hcd
[ 1067.052062] usb 1-3: device not accepting address 27, error -62
[ 1067.052083] hub 1-0:1.0: unable to enumerate USB device on port 3
[ 1083.504074] usb 1-3: new low-speed USB device number 28 using ohci_hcd
[ 1083.644062] usb 1-3: device descriptor read/64, error -62
[ 1083.888068] usb 1-3: device descriptor read/64, error -62
[ 1084.128061] usb 1-3: new low-speed USB device number 29 using ohci_hcd
[ 1084.268066] usb 1-3: device descriptor read/64, error -62
[ 1084.512060] usb 1-3: device descriptor read/64, error -62
[ 1084.752063] usb 1-3: new low-speed USB device number 30 using ohci_hcd
[ 1085.160048] usb 1-3: device not accepting address 30, error -62
[ 1085.296062] usb 1-3: new low-speed USB device number 31 using ohci_hcd
[ 1085.704058] usb 1-3: device not accepting address 31, error -62
[ 1085.704078] hub 1-0:1.0: unable to enumerate USB device on port 3
[ 1088.968074] usb 1-3: new low-speed USB device number 32 using ohci_hcd
[ 1089.108048] usb 1-3: device descriptor read/64, error -62
[ 1089.352061] usb 1-3: device descriptor read/64, error -62
[ 1089.592065] usb 1-3: new low-speed USB device number 33 using ohci_hcd
[ 1089.732063] usb 1-3: device descriptor read/64, error -62
[ 1089.976063] usb 1-3: device descriptor read/64, error -62
[ 1090.216065] usb 1-3: new low-speed USB device number 34 using ohci_hcd
[ 1090.624059] usb 1-3: device not accepting address 34, error -62
[ 1090.760069] usb 1-3: new low-speed USB device number 35 using ohci_hcd
[ 1091.168063] usb 1-3: device not accepting address 35, error -62
[ 1091.168083] hub 1-0:1.0: unable to enumerate USB device on port 3
[ 1103.680063] usb 1-3: new full-speed USB device number 36 using ohci_hcd
[ 1103.820071] usb 1-3: device descriptor read/64, error -62
[ 1104.064067] usb 1-3: device descriptor read/64, error -62
[ 1104.304068] usb 1-3: new full-speed USB device number 37 using ohci_hcd
[ 1104.444071] usb 1-3: device descriptor read/64, error -62
[ 1104.688085] usb 1-3: device descriptor read/64, error -62
[ 1104.928079] usb 1-3: new full-speed USB device number 38 using ohci_hcd
[ 1105.336066] usb 1-3: device not accepting address 38, error -62
[ 1105.472053] usb 1-3: new full-speed USB device number 39 using ohci_hcd
[ 1105.880055] usb 1-3: device not accepting address 39, error -62
[ 1105.880132] hub 1-0:1.0: unable to enumerate USB device on port 3
[ 1293.140076] usb 1-3: new low-speed USB device number 40 using ohci_hcd
[ 1293.280086] usb 1-3: device descriptor read/64, error -62
[ 1293.524072] usb 1-3: device descriptor read/64, error -62
[ 1293.764059] usb 1-3: new low-speed USB device number 41 using ohci_hcd
[ 1293.904060] usb 1-3: device descriptor read/64, error -62
[ 1294.148078] usb 1-3: device descriptor read/64, error -62
[ 1294.388065] usb 1-3: new low-speed USB device number 42 using ohci_hcd
[ 1294.796071] usb 1-3: device not accepting address 42, error -62
[ 1294.932063] usb 1-3: new low-speed USB device number 43 using ohci_hcd
[ 1295.340067] usb 1-3: device not accepting address 43, error -62
[ 1295.340097] hub 1-0:1.0: unable to enumerate USB device on port 3
[ 1303.580089] usb 1-3: new low-speed USB device number 44 using ohci_hcd
[ 1303.720057] usb 1-3: device descriptor read/64, error -62
[ 1303.964090] usb 1-3: device descriptor read/64, error -62
[ 1304.204060] usb 1-3: new low-speed USB device number 45 using ohci_hcd
[ 1304.288082] hub 1-0:1.0: unable to enumerate USB device on port 3
[ 1306.708062] usb 1-3: new low-speed USB device number 46 using ohci_hcd
[ 1306.848050] usb 1-3: device descriptor read/64, error -62
[ 1307.092047] usb 1-3: device descriptor read/64, error -62
[ 1307.332067] usb 1-3: new low-speed USB device number 47 using ohci_hcd
[ 1307.472069] usb 1-3: device descriptor read/64, error -62
[ 1307.716064] usb 1-3: device descriptor read/64, error -62
[ 1307.956067] usb 1-3: new low-speed USB device number 48 using ohci_hcd
[ 1308.364072] usb 1-3: device not accepting address 48, error -62
[ 1308.500082] usb 1-3: new low-speed USB device number 49 using ohci_hcd
[ 1308.908072] usb 1-3: device not accepting address 49, error -62
[ 1308.908107] hub 1-0:1.0: unable to enumerate USB device on port 3
[ 1323.672084] usb 1-3: new low-speed USB device number 50 using ohci_hcd
[ 1323.812092] usb 1-3: device descriptor read/64, error -62
[ 1324.056076] usb 1-3: device descriptor read/64, error -62
[ 1324.296080] usb 1-3: new low-speed USB device number 51 using ohci_hcd
[ 1324.436080] usb 1-3: device descriptor read/64, error -62
[ 1324.680082] usb 1-3: device descriptor read/64, error -62
[ 1324.920083] usb 1-3: new low-speed USB device number 52 using ohci_hcd
[ 1325.328073] usb 1-3: device not accepting address 52, error -62
[ 1325.464073] usb 1-3: new low-speed USB device number 53 using ohci_hcd
[ 1325.872063] usb 1-3: device not accepting address 53, error -62
[ 1325.872090] hub 1-0:1.0: unable to enumerate USB device on port 3
[ 1329.580085] usb 1-3: new low-speed USB device number 54 using ohci_hcd
[ 1329.720069] usb 1-3: device descriptor read/64, error -62
[ 1329.964095] usb 1-3: device descriptor read/64, error -62
[ 1330.204077] usb 1-3: new low-speed USB device number 55 using ohci_hcd
[ 1330.344077] usb 1-3: device descriptor read/64, error -62
[ 1330.588058] usb 1-3: device descriptor read/64, error -62
[ 1330.828089] usb 1-3: new low-speed USB device number 56 using ohci_hcd
[ 1331.236067] usb 1-3: device not accepting address 56, error -62
[ 1331.372075] usb 1-3: new low-speed USB device number 57 using ohci_hcd
[ 1331.780062] usb 1-3: device not accepting address 57, error -62
[ 1331.780091] hub 1-0:1.0: unable to enumerate USB device on port 3
[ 1355.144076] usb 1-3: new low-speed USB device number 58 using ohci_hcd
[ 1355.284079] usb 1-3: device descriptor read/64, error -62
[ 1355.528074] usb 1-3: device descriptor read/64, error -62
[ 1355.768086] usb 1-3: new low-speed USB device number 59 using ohci_hcd
[ 1355.908064] usb 1-3: device descriptor read/64, error -62
[ 1356.152122] usb 1-3: device descriptor read/64, error -62
[ 1356.392075] usb 1-3: new low-speed USB device number 60 using ohci_hcd
[ 1356.800059] usb 1-3: device not accepting address 60, error -62
[ 1356.936085] usb 1-3: new low-speed USB device number 61 using ohci_hcd
[ 1357.344055] usb 1-3: device not accepting address 61, error -62
[ 1357.344086] hub 1-0:1.0: unable to enumerate USB device on port 3
[ 1696.252072] usb 1-3: new low-speed USB device number 62 using ohci_hcd
[ 1696.392070] usb 1-3: device descriptor read/64, error -62
[ 1696.636063] usb 1-3: device descriptor read/64, error -62
[ 1696.876053] usb 1-3: new low-speed USB device number 63 using ohci_hcd
[ 1697.016067] usb 1-3: device descriptor read/64, error -62
[ 1697.260046] usb 1-3: device descriptor read/64, error -62
[ 1697.500052] usb 1-3: new low-speed USB device number 64 using ohci_hcd
[ 1697.908041] usb 1-3: device not accepting address 64, error -62
[ 1698.044079] usb 1-3: new low-speed USB device number 65 using ohci_hcd
[ 1698.452045] usb 1-3: device not accepting address 65, error -62
[ 1698.452067] hub 1-0:1.0: unable to enumerate USB device on port 3
[ 3168.360074] usb 1-3: new full-speed USB device number 66 using ohci_hcd
[ 3168.500086] usb 1-3: device descriptor read/64, error -62
[ 3168.744061] usb 1-3: device descriptor read/64, error -62
[ 3168.984068] usb 1-3: new full-speed USB device number 67 using ohci_hcd
[ 3169.124062] usb 1-3: device descriptor read/64, error -62
[ 3169.368065] usb 1-3: device descriptor read/64, error -62
[ 3169.608064] usb 1-3: new full-speed USB device number 68 using ohci_hcd
[ 3170.016053] usb 1-3: device not accepting address 68, error -62
[ 3170.152078] usb 1-3: new full-speed USB device number 69 using ohci_hcd
[ 3170.560070] usb 1-3: device not accepting address 69, error -62
[ 3170.560107] hub 1-0:1.0: unable to enumerate USB device on port 3
If someone could please give me at least some advice on what might be happening and where to start (or better yet how to correct it) I would be extremely appreciative. Thank you!

---

### Post by drtheradio on 2012-05-10
If you boot off a live cd do you get the same Problem?

If so you will have to take your laptop to the shop... But first ...you could
check your bios and make sure you have USB turned on.

---

### Post by Nightreaver1986 on 2012-05-10
Sadly, my installation was from a flash drive, so I don't have a live CD handy. I have another PC that I can make one from in the morning, though, so I'm not entirely out of luck there.

In the meantime, I don't understand what the output above is actually saying the issue is. The only thing close to a computer repair shop within a good range is Staples, and they won't touch a computer that doesn't have some sort of Windows operating system on it, sadly, so I don't know what to tell them the problem might be in case it is a hardware issue.

Any advice? And thank you for your timely response, it's most appreciated.

---

### Post by bkratz on 2012-05-10
> **Nightreaver1986 said:**
> Sadly, my installation was from a flash drive, so I don't have a live CD handy. I have another PC that I can make one from in the morning, though, so I'm not entirely out of luck there.

In the meantime, I don't understand what the output above is actually saying the issue is. The only thing close to a computer repair shop within a good range is Staples, and they won't touch a computer that doesn't have some sort of Windows operating system on it, sadly, so I don't know what to tell them the problem might be in case it is a hardware issue.

Any advice? And thank you for your timely response, it's most appreciated.



Saw this interesting thread 

[http://ubuntuforums.org/showthread.php?t=797789&page=2](http://ubuntuforums.org/showthread.php?t=797789&page=2)

It starts kinda old but looks like it might be what you are seeing.  ( I googled one of the errors you showed to find it).

---

### Post by Nightreaver1986 on 2012-05-10
Alright, so I did try this with limited success. Now my devices are consistently getting power to them (except for any usb mouse, which still seems to lose power) but the system still won't let me see them under the file system to view the contents of anything like a hard drive.

Most of the things I've read about the -62 error seem to point to a temporary hardware failure that should be resolved upon rebooting the machine, but this hasn't solved my problem at all. Something about over-current protection, I believe. 

Thank you for the very interesting link though, it seems to have gotten at least some results! Does anyone else have any idea what might be causing this kind of error?

Edit: Would that thread still apply to 12.04? Or has something changed in 12.04 that I need to be aware of to make this work with the new distro?

---

