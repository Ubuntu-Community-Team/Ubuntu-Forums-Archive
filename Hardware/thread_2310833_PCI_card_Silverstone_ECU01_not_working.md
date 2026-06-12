---
title: "PCI card Silverstone ECU01 not working"
date: 2016-01-22
forum: Hardware
---

### Post by fraiddo on 2016-01-22
Hello,

i have a problem with my PCI card Silverstone ECU01, so

this is my setup :
[FONT=Arial]- motherboard MSI z97 PC MATE
- a only usb3 card reader (who works good on the usb3 of the motherboard)
- PCI card SILVERSTONE ecu01 : [/FONT][http://www.silverstonetek.com/product.php?pid=498](http://www.silverstonetek.com/product.php?pid=498)

after installation i have this

```

[COLOR=#FFFFFF]ordi@ordi-MS-7850:~$ dmesg[/COLOR][    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 4.2.0-25-generic (buildd@lcy01-02) (gcc version 5.2.1 20151010 (Ubuntu 5.2.1-22ubuntu2) ) #30-Ubuntu SMP Mon Jan 18 12:31:50 UTC 2016 (Ubuntu 4.2.0-25.30-generic 4.2.6)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-25-generic root=UUID=43bb30ed-20bf-40e4-a850-1e0973a7c57e ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] x86/fpu: xstate_offset[2]: 0240, xstate_sizes[2]: 0100
[    0.000000] x86/fpu: Supporting XSAVE feature 0x01: 'x87 floating point registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x02: 'SSE registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x04: 'AVX registers'
[    0.000000] x86/fpu: Enabled xstate features 0x7, context size is 0x340 bytes, using 'standard' format.
[    0.000000] x86/fpu: Using 'eager' FPU context switches.
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009d7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009d800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000c82ddfff] usable
[    0.000000] BIOS-e820: [mem 0x00000000c82de000-0x00000000c82e4fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000c82e5000-0x00000000c8731fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000c8732000-0x00000000c8d42fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000c8d43000-0x00000000d960cfff] usable
[    0.000000] BIOS-e820: [mem 0x00000000d960d000-0x00000000d9677fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000d9678000-0x00000000d96c3fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000d96c4000-0x00000000d97fcfff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000d97fd000-0x00000000d9ffefff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000d9fff000-0x00000000d9ffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000db000000-0x00000000df1fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000021fdfffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.8 present.
[    0.000000] DMI: MSI MS-7850/Z97 PC Mate(MS-7850), BIOS V4.7 12/23/2014
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x21fe00 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask 7E00000000 write-back
[    0.000000]   1 base 0200000000 mask 7FE0000000 write-back
[    0.000000]   2 base 00E0000000 mask 7FE0000000 uncachable
[    0.000000]   3 base 00DC000000 mask 7FFC000000 uncachable
[    0.000000]   4 base 00DB000000 mask 7FFF000000 uncachable
[    0.000000]   5 base 021FE00000 mask 7FFFE00000 uncachable
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- WT  
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 8GB, type WB
[    0.000000] reg 1, base: 8GB, range: 512MB, type WB
[    0.000000] reg 2, base: 3584MB, range: 512MB, type UC
[    0.000000] reg 3, base: 3520MB, range: 64MB, type UC
[    0.000000] reg 4, base: 3504MB, range: 16MB, type UC
[    0.000000] reg 5, base: 8702MB, range: 2MB, type UC
[    0.000000] total RAM covered: 8110M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 128M     num_reg: 8      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 512MB, type WB
[    0.000000] reg 3, base: 3504MB, range: 16MB, type UC
[    0.000000] reg 4, base: 3520MB, range: 64MB, type UC
[    0.000000] reg 5, base: 4GB, range: 4GB, type WB
[    0.000000] reg 6, base: 8GB, range: 512MB, type WB
[    0.000000] reg 7, base: 8702MB, range: 2MB, type UC
[    0.000000] e820: update [mem 0xdb000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xda000 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fd7b0-0x000fd7bf] mapped at [ffff8800000fd7b0]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01ff0000, 0x01ff0fff] PGTABLE
[    0.000000] BRK [0x01ff1000, 0x01ff1fff] PGTABLE
[    0.000000] BRK [0x01ff2000, 0x01ff2fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x21fc00000-0x21fdfffff]
[    0.000000]  [mem 0x21fc00000-0x21fdfffff] page 2M
[    0.000000] BRK [0x01ff3000, 0x01ff3fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x200000000-0x21fbfffff]
[    0.000000]  [mem 0x200000000-0x21fbfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x1e0000000-0x1ffffffff]
[    0.000000]  [mem 0x1e0000000-0x1ffffffff] page 1G
[    0.000000] init_memory_mapping: [mem 0x00100000-0xc82ddfff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
[    0.000000]  [mem 0x40000000-0xbfffffff] page 1G
[    0.000000]  [mem 0xc0000000-0xc81fffff] page 2M
[    0.000000]  [mem 0xc8200000-0xc82ddfff] page 4k
[    0.000000] init_memory_mapping: [mem 0xc82e5000-0xc8731fff]
[    0.000000]  [mem 0xc82e5000-0xc83fffff] page 4k
[    0.000000]  [mem 0xc8400000-0xc85fffff] page 2M
[    0.000000]  [mem 0xc8600000-0xc8731fff] page 4k
[    0.000000] BRK [0x01ff4000, 0x01ff4fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0xc8d43000-0xd960cfff]
[    0.000000]  [mem 0xc8d43000-0xc8dfffff] page 4k
[    0.000000]  [mem 0xc8e00000-0xd95fffff] page 2M
[    0.000000]  [mem 0xd9600000-0xd960cfff] page 4k
[    0.000000] BRK [0x01ff5000, 0x01ff5fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0xd9678000-0xd96c3fff]
[    0.000000]  [mem 0xd9678000-0xd96c3fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xd9fff000-0xd9ffffff]
[    0.000000]  [mem 0xd9fff000-0xd9ffffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x1dfffffff]
[    0.000000]  [mem 0x100000000-0x1dfffffff] page 1G
[    0.000000] RAMDISK: [mem 0x33fda000-0x35fe4fff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000000F04A0 000024 (v02 ALASKA)
[    0.000000] ACPI: XSDT 0x00000000D97C8088 000094 (v01 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: FACP 0x00000000D97D94B0 00010C (v05 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 0x00000000D97C81B8 0112F5 (v02 ALASKA A M I    00000015 INTL 20120711)
[    0.000000] ACPI: FACS 0x00000000D97FCF80 000040
[    0.000000] ACPI: APIC 0x00000000D97D95C0 000072 (v03 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: FPDT 0x00000000D97D9638 000044 (v01 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: FIDT 0x00000000D97D9680 00009C (v01 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: ASF! 0x00000000D97D9720 0000A5 (v32 INTEL   HCG     00000001 TFSM 000F4240)
[    0.000000] ACPI: SSDT 0x00000000D97D97C8 000C7D (v02 Ther_R Ther_Rvp 00001000 INTL 20120711)
[    0.000000] ACPI: SSDT 0x00000000D97DA448 000539 (v02 PmRef  Cpu0Ist  00003000 INTL 20051117)
[    0.000000] ACPI: SSDT 0x00000000D97DA988 000B74 (v02 CpuRef CpuSsdt  00003000 INTL 20051117)
[    0.000000] ACPI: MCFG 0x00000000D97DB500 00003C (v01 ALASKA A M I    01072009 MSFT 00000097)
[    0.000000] ACPI: HPET 0x00000000D97DB540 000038 (v01 ALASKA A M I    01072009 AMI. 00000005)
[    0.000000] ACPI: SSDT 0x00000000D97DB578 00036D (v01 SataRe SataTabl 00001000 INTL 20120711)
[    0.000000] ACPI: SSDT 0x00000000D97DB8E8 005B5D (v02 SaSsdt SaSsdt   00003000 INTL 20120711)
[    0.000000] ACPI: UEFI 0x00000000D97E1448 000042 (v01 ALASKA A M I    01072009      00000000)
[    0.000000] ACPI: SSDT 0x00000000D97E1490 0005AC (v02 Intel_ IsctTabl 00001000 INTL 20120711)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000021fdfffff]
[    0.000000] NODE_DATA(0) allocated [mem 0x21fdf7000-0x21fdfbfff]
[    0.000000]  [ffffea0000000000-ffffea00087fffff] PMD -> [ffff880217400000-ffff88021f3fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.000000]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
[    0.000000]   Normal   [mem 0x0000000100000000-0x000000021fdfffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x0000000000001000-0x000000000009cfff]
[    0.000000]   node   0: [mem 0x0000000000100000-0x00000000c82ddfff]
[    0.000000]   node   0: [mem 0x00000000c82e5000-0x00000000c8731fff]
[    0.000000]   node   0: [mem 0x00000000c8d43000-0x00000000d960cfff]
[    0.000000]   node   0: [mem 0x00000000d9678000-0x00000000d96c3fff]
[    0.000000]   node   0: [mem 0x00000000d9fff000-0x00000000d9ffffff]
[    0.000000]   node   0: [mem 0x0000000100000000-0x000000021fdfffff]
[    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x000000021fdfffff]
[    0.000000] On node 0 totalpages: 2067934
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3996 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 13826 pages used for memmap
[    0.000000]   DMA32 zone: 884802 pages, LIFO batch:31
[    0.000000]   Normal zone: 18424 pages used for memmap
[    0.000000]   Normal zone: 1179136 pages, LIFO batch:31
[    0.000000] Reserving Intel graphics stolen memory at 0xdb200000-0xdf1fffff
[    0.000000] ACPI: PM-Timer IO Port: 0x1808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] smpboot: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009dfff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xc82de000-0xc82e4fff]
[    0.000000] PM: Registered nosave memory: [mem 0xc8732000-0xc8d42fff]
[    0.000000] PM: Registered nosave memory: [mem 0xd960d000-0xd9677fff]
[    0.000000] PM: Registered nosave memory: [mem 0xd96c4000-0xd97fcfff]
[    0.000000] PM: Registered nosave memory: [mem 0xd97fd000-0xd9ffefff]
[    0.000000] PM: Registered nosave memory: [mem 0xda000000-0xdaffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xdb000000-0xdf1fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xdf200000-0xf7ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfbffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfc000000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfecfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfed03fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed04000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xfeffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
[    0.000000] e820: [mem 0xdf200000-0xf7ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 33 pages/cpu @ffff88021fa00000 s96728 r8192 d30248 u524288
[    0.000000] pcpu-alloc: s96728 r8192 d30248 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 2035599
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-25-generic root=UUID=43bb30ed-20bf-40e4-a850-1e0973a7c57e ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 8024556K/8271736K available (8148K kernel code, 1237K rwdata, 3800K rodata, 1460K init, 1292K bss, 247180K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     Build-time adjustment of leaf fanout to 64.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=64, nr_cpu_ids=4
[    0.000000] NR_IRQS:16640 nr_irqs:456 16
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-3.
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 133484882848 ns
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 3600.273 MHz processor
[    0.000019] Calibrating delay loop (skipped), value calculated using timer frequency.. 7200.54 BogoMIPS (lpj=14401092)
[    0.000020] pid_max: default: 32768 minimum: 301
[    0.000024] ACPI: Core revision 20150619
[    0.010856] ACPI: All ACPI Tables successfully acquired
[    0.010868] Security Framework initialized
[    0.010874] AppArmor: AppArmor initialized
[    0.010875] Yama: becoming mindful.
[    0.011218] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.012225] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.012663] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.012670] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.012809] Initializing cgroup subsys blkio
[    0.012811] Initializing cgroup subsys memory
[    0.012816] Initializing cgroup subsys devices
[    0.012817] Initializing cgroup subsys freezer
[    0.012819] Initializing cgroup subsys net_cls
[    0.012820] Initializing cgroup subsys perf_event
[    0.012821] Initializing cgroup subsys net_prio
[    0.012823] Initializing cgroup subsys hugetlb
[    0.012838] CPU: Physical Processor ID: 0
[    0.012838] CPU: Processor Core ID: 0
[    0.013549] mce: CPU supports 7 MCE banks
[    0.013557] CPU0: Thermal monitoring enabled (TM1)
[    0.013562] process: using mwait in idle threads
[    0.013564] Last level iTLB entries: 4KB 1024, 2MB 1024, 4MB 1024
[    0.013565] Last level dTLB entries: 4KB 1024, 2MB 1024, 4MB 1024, 1GB 4
[    0.013784] Freeing SMP alternatives memory: 28K (ffffffff81ea4000 - ffffffff81eab000)
[    0.023620] ftrace: allocating 30910 entries in 121 pages
[    0.032183] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
[    0.071810] TSC deadline timer enabled
[    0.071813] smpboot: CPU0: Intel(R) Core(TM) i3-4160 CPU @ 3.60GHz (fam: 06, model: 3c, stepping: 03)
[    0.071831] Performance Events: PEBS fmt2+, 16-deep LBR, Haswell events, full-width counters, Intel PMU driver.
[    0.071844] ... version:                3
[    0.071845] ... bit width:              48
[    0.071846] ... generic registers:      4
[    0.071846] ... value mask:             0000ffffffffffff
[    0.071847] ... max period:             0000ffffffffffff
[    0.071847] ... fixed-purpose events:   3
[    0.071848] ... event mask:             000000070000000f
[    0.072348] x86: Booting SMP configuration:
[    0.072349] .... node  #0, CPUs:      #1
[    0.076199] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.076252]  #2 #3
[    0.083928] x86: Booted up 1 node, 4 CPUs
[    0.083930] smpboot: Total of 4 processors activated (28802.18 BogoMIPS)
[    0.086427] devtmpfs: initialized
[    0.087801] evm: security.selinux
[    0.087802] evm: security.SMACK64
[    0.087803] evm: security.SMACK64EXEC
[    0.087803] evm: security.SMACK64TRANSMUTE
[    0.087804] evm: security.SMACK64MMAP
[    0.087804] evm: security.ima
[    0.087805] evm: security.capability
[    0.087836] PM: Registering ACPI NVS region [mem 0xc82de000-0xc82e4fff] (28672 bytes)
[    0.087837] PM: Registering ACPI NVS region [mem 0xd96c4000-0xd97fcfff] (1282048 bytes)
[    0.087892] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    0.087942] pinctrl core: initialized pinctrl subsystem
[    0.088011] RTC time: 16:41:41, date: 01/21/16
[    0.088080] NET: Registered protocol family 16
[    0.094303] cpuidle: using governor ladder
[    0.098297] cpuidle: using governor menu
[    0.098339] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.098340] ACPI: bus type PCI registered
[    0.098341] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.098382] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.098383] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.098389] PCI: Using configuration type 1 for base access
[    0.098529] perf_event_intel: PMU erratum BJ122, BV98, HSD29 worked around, HT is on
[    0.102491] ACPI: Added _OSI(Module Device)
[    0.102493] ACPI: Added _OSI(Processor Device)
[    0.102493] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.102494] ACPI: Added _OSI(Processor Aggregator Device)
[    0.105432] ACPI: Executed 6 blocks of module-level executable AML code
[    0.107411] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.107937] ACPI: Dynamic OEM Table Load:
[    0.107941] ACPI: SSDT 0xFFFF880215D12400 0003D3 (v02 PmRef  Cpu0Cst  00003001 INTL 20051117)
[    0.108402] ACPI: Dynamic OEM Table Load:
[    0.108405] ACPI: SSDT 0xFFFF880215CFA000 0005AA (v02 PmRef  ApIst    00003000 INTL 20051117)
[    0.108896] ACPI: Dynamic OEM Table Load:
[    0.108899] ACPI: SSDT 0xFFFF880215D33A00 000119 (v02 PmRef  ApCst    00003000 INTL 20051117)
[    0.109652] ACPI: Interpreter enabled
[    0.109657] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20150619/hwxface-580)
[    0.109661] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20150619/hwxface-580)
[    0.109675] ACPI: (supports S0 S3 S4 S5)
[    0.109676] ACPI: Using IOAPIC for interrupt routing
[    0.109694] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.109981] ACPI: Power Resource [PG00] (on)
[    0.110152] ACPI: Power Resource [PG01] (on)
[    0.110319] ACPI: Power Resource [PG02] (on)
[    0.115241] ACPI: Power Resource [FN00] (off)
[    0.115286] ACPI: Power Resource [FN01] (off)
[    0.115328] ACPI: Power Resource [FN02] (off)
[    0.115370] ACPI: Power Resource [FN03] (off)
[    0.115412] ACPI: Power Resource [FN04] (off)
[    0.115930] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    0.115933] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.116062] acpi PNP0A08:00: _OSC: platform does not support [PCIeHotplug PME]
[    0.116137] acpi PNP0A08:00: _OSC: OS now controls [AER PCIeCapability]
[    0.116138] acpi PNP0A08:00: FADT indicates ASPM is unsupported, using BIOS configuration
[    0.116390] PCI host bridge to bus 0000:00
[    0.116392] pci_bus 0000:00: root bus resource [bus 00-3e]
[    0.116393] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
[    0.116394] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
[    0.116395] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
[    0.116396] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff window]
[    0.116397] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff window]
[    0.116398] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff window]
[    0.116399] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff window]
[    0.116400] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff window]
[    0.116400] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff window]
[    0.116401] pci_bus 0000:00: root bus resource [mem 0xdf200000-0xfeafffff window]
[    0.116406] pci 0000:00:00.0: [8086:0c00] type 00 class 0x060000
[    0.116461] pci 0000:00:02.0: [8086:041e] type 00 class 0x030000
[    0.116469] pci 0000:00:02.0: reg 0x10: [mem 0xf7800000-0xf7bfffff 64bit]
[    0.116473] pci 0000:00:02.0: reg 0x18: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.116476] pci 0000:00:02.0: reg 0x20: [io  0xf000-0xf03f]
[    0.116522] pci 0000:00:03.0: [8086:0c0c] type 00 class 0x040300
[    0.116529] pci 0000:00:03.0: reg 0x10: [mem 0xf7d14000-0xf7d17fff 64bit]
[    0.116595] pci 0000:00:14.0: [8086:8cb1] type 00 class 0x0c0330
[    0.116616] pci 0000:00:14.0: reg 0x10: [mem 0xf7d00000-0xf7d0ffff 64bit]
[    0.116655] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.116684] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.116709] pci 0000:00:16.0: [8086:8cba] type 00 class 0x078000
[    0.116731] pci 0000:00:16.0: reg 0x10: [mem 0xf7d1d000-0xf7d1d00f 64bit]
[    0.116773] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.116834] pci 0000:00:1a.0: [8086:8cad] type 00 class 0x0c0320
[    0.116857] pci 0000:00:1a.0: reg 0x10: [mem 0xf7d1b000-0xf7d1b3ff]
[    0.116914] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.116945] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.116969] pci 0000:00:1b.0: [8086:8ca0] type 00 class 0x040300
[    0.116990] pci 0000:00:1b.0: reg 0x10: [mem 0xf7d10000-0xf7d13fff 64bit]
[    0.117035] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.117069] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.117092] pci 0000:00:1c.0: [8086:8c90] type 01 class 0x060400
[    0.117140] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.117182] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.117208] pci 0000:00:1c.5: [8086:8c9a] type 01 class 0x060400
[    0.117257] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.117297] pci 0000:00:1c.5: System wakeup disabled by ACPI
[    0.117320] pci 0000:00:1c.6: [8086:244e] type 01 class 0x060401
[    0.117368] pci 0000:00:1c.6: PME# supported from D0 D3hot D3cold
[    0.117407] pci 0000:00:1c.6: System wakeup disabled by ACPI
[    0.117432] pci 0000:00:1d.0: [8086:8ca6] type 00 class 0x0c0320
[    0.117456] pci 0000:00:1d.0: reg 0x10: [mem 0xf7d1a000-0xf7d1a3ff]
[    0.117513] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.117543] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.117569] pci 0000:00:1f.0: [8086:8cc4] type 00 class 0x060100
[    0.117692] pci 0000:00:1f.2: [8086:8c82] type 00 class 0x010601
[    0.117709] pci 0000:00:1f.2: reg 0x10: [io  0xf0b0-0xf0b7]
[    0.117715] pci 0000:00:1f.2: reg 0x14: [io  0xf0a0-0xf0a3]
[    0.117720] pci 0000:00:1f.2: reg 0x18: [io  0xf090-0xf097]
[    0.117726] pci 0000:00:1f.2: reg 0x1c: [io  0xf080-0xf083]
[    0.117732] pci 0000:00:1f.2: reg 0x20: [io  0xf060-0xf07f]
[    0.117738] pci 0000:00:1f.2: reg 0x24: [mem 0xf7d19000-0xf7d197ff]
[    0.117757] pci 0000:00:1f.2: PME# supported from D3hot
[    0.117798] pci 0000:00:1f.3: [8086:8ca2] type 00 class 0x0c0500
[    0.117811] pci 0000:00:1f.3: reg 0x10: [mem 0xf7d18000-0xf7d180ff 64bit]
[    0.117827] pci 0000:00:1f.3: reg 0x20: [io  0xf040-0xf05f]
[    0.117924] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.117988] pci 0000:02:00.0: [10ec:8168] type 00 class 0x020000
[    0.118024] pci 0000:02:00.0: reg 0x10: [io  0xe000-0xe0ff]
[    0.118050] pci 0000:02:00.0: reg 0x18: [mem 0xf7c00000-0xf7c00fff 64bit]
[    0.118066] pci 0000:02:00.0: reg 0x20: [mem 0xf0000000-0xf0003fff 64bit pref]
[    0.118120] pci 0000:02:00.0: supports D1 D2
[    0.118121] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.118153] pci 0000:02:00.0: System wakeup disabled by ACPI
[    0.122281] pci 0000:00:1c.5: PCI bridge to [bus 02]
[    0.122284] pci 0000:00:1c.5:   bridge window [io  0xe000-0xefff]
[    0.122287] pci 0000:00:1c.5:   bridge window [mem 0xf7c00000-0xf7cfffff]
[    0.122291] pci 0000:00:1c.5:   bridge window [mem 0xf0000000-0xf00fffff 64bit pref]
[    0.122355] pci 0000:03:00.0: [1b21:1080] type 01 class 0x060400
[    0.122463] pci 0000:03:00.0: supports D1 D2
[    0.122463] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.122493] pci 0000:03:00.0: System wakeup disabled by ACPI
[    0.130267] pci 0000:00:1c.6: PCI bridge to [bus 03-04] (subtractive decode)
[    0.130274] pci 0000:00:1c.6:   bridge window [io  0x0000-0x0cf7 window] (subtractive decode)
[    0.130275] pci 0000:00:1c.6:   bridge window [io  0x0d00-0xffff window] (subtractive decode)
[    0.130276] pci 0000:00:1c.6:   bridge window [mem 0x000a0000-0x000bffff window] (subtractive decode)
[    0.130277] pci 0000:00:1c.6:   bridge window [mem 0x000d0000-0x000d3fff window] (subtractive decode)
[    0.130277] pci 0000:00:1c.6:   bridge window [mem 0x000d4000-0x000d7fff window] (subtractive decode)
[    0.130278] pci 0000:00:1c.6:   bridge window [mem 0x000d8000-0x000dbfff window] (subtractive decode)
[    0.130279] pci 0000:00:1c.6:   bridge window [mem 0x000dc000-0x000dffff window] (subtractive decode)
[    0.130280] pci 0000:00:1c.6:   bridge window [mem 0x000e0000-0x000e3fff window] (subtractive decode)
[    0.130281] pci 0000:00:1c.6:   bridge window [mem 0x000e4000-0x000e7fff window] (subtractive decode)
[    0.130282] pci 0000:00:1c.6:   bridge window [mem 0xdf200000-0xfeafffff window] (subtractive decode)
[    0.130388] pci 0000:03:00.0: PCI bridge to [bus 04]
[    0.130902] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.130935] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.130964] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.130993] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.131022] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.131051] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.131080] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 6 10 11 12 14 15)
[    0.131108] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 10 11 12 14 15)
[    0.131291] ACPI: Enabled 6 GPEs in block 00 to 3F
[    0.131355] vgaarb: setting as boot device: PCI:0000:00:02.0
[    0.131356] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.131358] vgaarb: loaded
[    0.131359] vgaarb: bridge control possible 0000:00:02.0
[    0.131510] SCSI subsystem initialized
[    0.131537] libata version 3.00 loaded.
[    0.131552] ACPI: bus type USB registered
[    0.131561] usbcore: registered new interface driver usbfs
[    0.131566] usbcore: registered new interface driver hub
[    0.131575] usbcore: registered new device driver usb
[    0.131662] PCI: Using ACPI for IRQ routing
[    0.132820] PCI: pci_cache_line_size set to 64 bytes
[    0.132852] e820: reserve RAM buffer [mem 0x0009d800-0x0009ffff]
[    0.132853] e820: reserve RAM buffer [mem 0xc82de000-0xcbffffff]
[    0.132854] e820: reserve RAM buffer [mem 0xc8732000-0xcbffffff]
[    0.132855] e820: reserve RAM buffer [mem 0xd960d000-0xdbffffff]
[    0.132855] e820: reserve RAM buffer [mem 0xd96c4000-0xdbffffff]
[    0.132856] e820: reserve RAM buffer [mem 0xda000000-0xdbffffff]
[    0.132857] e820: reserve RAM buffer [mem 0x21fe00000-0x21fffffff]
[    0.132921] NetLabel: Initializing
[    0.132922] NetLabel:  domain hash size = 128
[    0.132923] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.132930] NetLabel:  unlabeled traffic allowed by default
[    0.132972] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.132975] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.134991] clocksource: Switched to clocksource hpet
[    0.138528] AppArmor: AppArmor Filesystem Enabled
[    0.138574] pnp: PnP ACPI init
[    0.138667] system 00:00: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.138670] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.138746] system 00:01: [io  0x0800-0x087f] has been reserved
[    0.138747] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.138763] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.138786] system 00:03: [io  0x1854-0x1857] has been reserved
[    0.138788] system 00:03: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.138857] system 00:04: [io  0x0a00-0x0a0f] has been reserved
[    0.138858] system 00:04: [io  0x0a10-0x0a1f] has been reserved
[    0.138859] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.138954] pnp 00:05: [dma 0 disabled]
[    0.138995] pnp 00:05: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.139140] pnp 00:06: [dma 0 disabled]
[    0.139195] pnp 00:06: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.139224] system 00:07: [io  0x04d0-0x04d1] has been reserved
[    0.139225] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.139459] system 00:08: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.139460] system 00:08: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.139461] system 00:08: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.139463] system 00:08: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.139464] system 00:08: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.139465] system 00:08: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.139466] system 00:08: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.139467] system 00:08: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.139469] system 00:08: [mem 0xff000000-0xffffffff] has been reserved
[    0.139470] system 00:08: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.139471] system 00:08: [mem 0xf7fe0000-0xf7feffff] has been reserved
[    0.139472] system 00:08: [mem 0xf7ff0000-0xf7ffffff] has been reserved
[    0.139474] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.139591] pnp: PnP ACPI: found 9 devices
[    0.145266] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    0.145297] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.145306] pci 0000:00:1c.5: PCI bridge to [bus 02]
[    0.145308] pci 0000:00:1c.5:   bridge window [io  0xe000-0xefff]
[    0.145312] pci 0000:00:1c.5:   bridge window [mem 0xf7c00000-0xf7cfffff]
[    0.145315] pci 0000:00:1c.5:   bridge window [mem 0xf0000000-0xf00fffff 64bit pref]
[    0.145319] pci 0000:03:00.0: PCI bridge to [bus 04]
[    0.145335] pci 0000:00:1c.6: PCI bridge to [bus 03-04]
[    0.145344] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7 window]
[    0.145345] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff window]
[    0.145346] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.145347] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff window]
[    0.145347] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff window]
[    0.145348] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff window]
[    0.145349] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff window]
[    0.145350] pci_bus 0000:00: resource 11 [mem 0x000e0000-0x000e3fff window]
[    0.145351] pci_bus 0000:00: resource 12 [mem 0x000e4000-0x000e7fff window]
[    0.145352] pci_bus 0000:00: resource 13 [mem 0xdf200000-0xfeafffff window]
[    0.145353] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.145354] pci_bus 0000:02: resource 1 [mem 0xf7c00000-0xf7cfffff]
[    0.145355] pci_bus 0000:02: resource 2 [mem 0xf0000000-0xf00fffff 64bit pref]
[    0.145356] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7 window]
[    0.145357] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff window]
[    0.145357] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.145358] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000d3fff window]
[    0.145359] pci_bus 0000:03: resource 8 [mem 0x000d4000-0x000d7fff window]
[    0.145360] pci_bus 0000:03: resource 9 [mem 0x000d8000-0x000dbfff window]
[    0.145361] pci_bus 0000:03: resource 10 [mem 0x000dc000-0x000dffff window]
[    0.145362] pci_bus 0000:03: resource 11 [mem 0x000e0000-0x000e3fff window]
[    0.145363] pci_bus 0000:03: resource 12 [mem 0x000e4000-0x000e7fff window]
[    0.145363] pci_bus 0000:03: resource 13 [mem 0xdf200000-0xfeafffff window]
[    0.145383] NET: Registered protocol family 2
[    0.145484] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
[    0.145571] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.145671] TCP: Hash tables configured (established 65536 bind 65536)
[    0.145688] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.145707] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.145741] NET: Registered protocol family 1
[    0.145752] pci 0000:00:02.0: Video device with shadowed ROM
[    0.146038] PCI: CLS 64 bytes, default 64
[    0.146076] Trying to unpack rootfs image as initramfs...
[    0.461454] Freeing initrd memory: 32812K (ffff880033fda000 - ffff880035fe5000)
[    0.461461] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.461463] software IO TLB [mem 0xd560d000-0xd960d000] (64MB) mapped at [ffff8800d560d000-ffff8800d960cfff]
[    0.461508] RAPL PMU detected, API unit is 2^-32 Joules, 4 fixed counters 655360 ms ovfl timer
[    0.461509] hw unit of domain pp0-core 2^-14 Joules
[    0.461509] hw unit of domain package 2^-14 Joules
[    0.461510] hw unit of domain dram 2^-14 Joules
[    0.461510] hw unit of domain pp1-gpu 2^-14 Joules
[    0.461588] microcode: CPU0 sig=0x306c3, pf=0x2, revision=0x1c
[    0.461594] microcode: CPU1 sig=0x306c3, pf=0x2, revision=0x1c
[    0.461597] microcode: CPU2 sig=0x306c3, pf=0x2, revision=0x1c
[    0.461602] microcode: CPU3 sig=0x306c3, pf=0x2, revision=0x1c
[    0.461632] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.461685] Scanning for low memory corruption every 60 seconds
[    0.461877] futex hash table entries: 1024 (order: 4, 65536 bytes)
[    0.461890] Initialise system trusted keyring
[    0.461904] audit: initializing netlink subsys (disabled)
[    0.461915] audit: type=2000 audit(1453394501.452:1): initialized
[    0.462126] HugeTLB registered 1 GB page size, pre-allocated 0 pages
[    0.462126] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.463017] zpool: loaded
[    0.463019] zbud: loaded
[    0.463130] VFS: Disk quotas dquot_6.6.0
[    0.463150] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.463425] fuse init (API version 7.23)
[    0.463508] Key type big_key registered
[    0.463749] Key type asymmetric registered
[    0.463751] Asymmetric key parser 'x509' registered
[    0.463760] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 249)
[    0.463787] io scheduler noop registered
[    0.463789] io scheduler deadline registered (default)
[    0.463807] io scheduler cfq registered
[    0.464034] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.464038] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.464058] vesafb: mode is 1920x1080x32, linelength=7680, pages=0
[    0.464059] vesafb: scrolling: redraw
[    0.464060] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.464068] vesafb: framebuffer at 0xe0000000, mapped to 0xffffc90001000000, using 8128k, total 8128k
[    0.464131] Console: switching to colour frame buffer device 240x67
[    0.464145] fb0: VESA VGA frame buffer device
[    0.464156] intel_idle: MWAIT substates: 0x42120
[    0.464156] intel_idle: v0.4 model 0x3C
[    0.464157] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.464310] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.464312] ACPI: Power Button [PWRB]
[    0.464334] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.464335] ACPI: Sleep Button [SLPB]
[    0.464357] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.464358] ACPI: Power Button [PWRF]
[    0.464813] thermal LNXTHERM:00: registered as thermal_zone0
[    0.464814] ACPI: Thermal Zone [TZ00] (28 C)
[    0.464927] thermal LNXTHERM:01: registered as thermal_zone1
[    0.464928] ACPI: Thermal Zone [TZ01] (30 C)
[    0.464965] GHES: HEST is not enabled!
[    0.465019] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.485344] 00:05: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    0.486413] Linux agpgart interface v0.103
[    0.487651] brd: module loaded
[    0.488166] loop: module loaded
[    0.488290] libphy: Fixed MDIO Bus: probed
[    0.488291] tun: Universal TUN/TAP device driver, 1.6
[    0.488292] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.488319] PPP generic driver version 2.4.2
[    0.488417] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.488420] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
[    0.489477] xhci_hcd 0000:00:14.0: hcc params 0x200077c1 hci version 0x100 quirks 0x00009810
[    0.489482] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.489538] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.489539] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.489540] usb usb1: Product: xHCI Host Controller
[    0.489541] usb usb1: Manufacturer: Linux 4.2.0-25-generic xhci-hcd
[    0.489542] usb usb1: SerialNumber: 0000:00:14.0
[    0.489609] hub 1-0:1.0: USB hub found
[    0.489623] hub 1-0:1.0: 14 ports detected
[    0.492460] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.492462] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    0.492488] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
[    0.492488] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.492489] usb usb2: Product: xHCI Host Controller
[    0.492490] usb usb2: Manufacturer: Linux 4.2.0-25-generic xhci-hcd
[    0.492491] usb usb2: SerialNumber: 0000:00:14.0
[    0.492550] hub 2-0:1.0: USB hub found
[    0.492560] hub 2-0:1.0: 6 ports detected
[    0.493741] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.493744] ehci-pci: EHCI PCI platform driver
[    0.493802] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    0.493805] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.493814] ehci-pci 0000:00:1a.0: debug port 2
[    0.497704] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    0.497710] ehci-pci 0000:00:1a.0: irq 16, io mem 0xf7d1b000
[    0.506419] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.506441] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    0.506441] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.506442] usb usb3: Product: EHCI Host Controller
[    0.506443] usb usb3: Manufacturer: Linux 4.2.0-25-generic ehci_hcd
[    0.506444] usb usb3: SerialNumber: 0000:00:1a.0
[    0.506521] hub 3-0:1.0: USB hub found
[    0.506524] hub 3-0:1.0: 2 ports detected
[    0.506637] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    0.506640] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 4
[    0.506648] ehci-pci 0000:00:1d.0: debug port 2
[    0.510532] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    0.510538] ehci-pci 0000:00:1d.0: irq 23, io mem 0xf7d1a000
[    0.522394] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.522414] usb usb4: New USB device found, idVendor=1d6b, idProduct=0002
[    0.522415] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.522416] usb usb4: Product: EHCI Host Controller
[    0.522416] usb usb4: Manufacturer: Linux 4.2.0-25-generic ehci_hcd
[    0.522417] usb usb4: SerialNumber: 0000:00:1d.0
[    0.522496] hub 4-0:1.0: USB hub found
[    0.522498] hub 4-0:1.0: 2 ports detected
[    0.522562] ehci-platform: EHCI generic platform driver
[    0.522568] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.522571] ohci-pci: OHCI PCI platform driver
[    0.522576] ohci-platform: OHCI generic platform driver
[    0.522581] uhci_hcd: USB Universal Host Controller Interface driver
[    0.522611] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.525140] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.525143] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.525358] mousedev: PS/2 mouse device common for all mice
[    0.525669] rtc_cmos 00:02: RTC can wake from S4
[    0.525780] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.525802] rtc_cmos 00:02: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.525807] i2c /dev entries driver
[    0.525852] device-mapper: uevent: version 1.0.3
[    0.525898] device-mapper: ioctl: 4.33.0-ioctl (2015-8-18) initialised: dm-devel@redhat.com
[    0.525909] Intel P-state driver initializing.
[    0.526013] ledtrig-cpu: registered to indicate activity on CPUs
[    0.526287] PCCT header not found.
[    0.526810] NET: Registered protocol family 10
[    0.527243] NET: Registered protocol family 17
[    0.527299] Key type dns_resolver registered
[    0.528239] Loading compiled-in X.509 certificates
[    0.530430] Loaded X.509 cert 'Build time autogenerated kernel key: a41030fbdf1dc962b4bb7d1644c3337ec416db86'
[    0.530441] registered taskstats version 1
[    0.530453] zswap: loading zswap
[    0.530454] zswap: using zbud pool
[    0.530457] zswap: using lzo compressor
[    0.531631] Key type trusted registered
[    0.533648] Key type encrypted registered
[    0.533653] AppArmor: AppArmor sha1 policy hashing enabled
[    0.533656] ima: No TPM chip found, activating TPM-bypass!
[    0.533668] evm: HMAC attrs: 0x1
[    0.533971]   Magic number: 0:377:692
[    0.534060] rtc_cmos 00:02: setting system clock to 2016-01-21 16:41:42 UTC (1453394502)
[    0.534107] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.534107] EDD information not available.
[    0.534156] PM: Hibernation image not present or could not be loaded.
[    0.534341] Freeing unused kernel memory: 1460K (ffffffff81d37000 - ffffffff81ea4000)
[    0.534342] Write protecting the kernel read-only data: 12288k
[    0.534437] Freeing unused kernel memory: 32K (ffff8800017f8000 - ffff880001800000)
[    0.534490] Freeing unused kernel memory: 296K (ffff880001bb6000 - ffff880001c00000)
[    0.540566] random: systemd-udevd urandom read with 2 bits of entropy available
[    0.558407] wmi: Mapper loaded
[    0.568750] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.568756] r8169 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[    0.571238] [drm] Initialized drm 1.1.0 20060810
[    0.571645] ahci 0000:00:1f.2: version 3.0
[    0.571779] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x3 impl SATA mode
[    0.571781] ahci 0000:00:1f.2: flags: 64bit ncq led clo pio slum part ems apst 
[    0.576041] r8169 0000:02:00.0 eth0: RTL8168g/8111g at 0xffffc90000ea6000, d8:cb:8a:56:f7:51, XID 0c000800 IRQ 26
[    0.576043] r8169 0000:02:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    0.578969] scsi host0: ahci
[    0.579065] scsi host1: ahci
[    0.579143] scsi host2: ahci
[    0.579214] scsi host3: ahci
[    0.579329] scsi host4: ahci
[    0.579400] scsi host5: ahci
[    0.579441] ata1: SATA max UDMA/133 abar m2048@0xf7d19000 port 0xf7d19100 irq 25
[    0.579444] ata2: SATA max UDMA/133 abar m2048@0xf7d19000 port 0xf7d19180 irq 25
[    0.579445] ata3: DUMMY
[    0.579446] ata4: DUMMY
[    0.579447] ata5: DUMMY
[    0.579448] ata6: DUMMY
[    0.591530] [drm] Memory usable by graphics device = 2048M
[    0.591533] checking generic (e0000000 7f0000) vs hw (e0000000 10000000)
[    0.591535] fb: switching to inteldrmfb from VESA VGA
[    0.591558] Console: switching to colour dummy device 80x25
[    0.591611] [drm] Replacing VGA console driver
[    0.594665] r8169 0000:02:00.0 enp2s0: renamed from eth0
[    0.598195] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    0.598196] [drm] Driver supports precise vblank timestamp query.
[    0.598250] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    0.676239] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    0.676568] acpi device:16: registered as cooling_device9
[    0.676625] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input4
[    0.676704] [drm] Initialized i915 1.6.0 20150522 for 0000:00:02.0 on minor 0
[    0.712860] fbcon: inteldrmfb (fb0) is primary device
[    0.712905] Console: switching to colour frame buffer device 240x67
[    0.712920] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    0.712921] i915 0000:00:02.0: registered panic notifier
[    0.805975] usb 1-5: new low-speed USB device number 2 using xhci_hcd
[    0.806231] usb 2-6: new SuperSpeed USB device number 2 using xhci_hcd
[    0.817955] usb 3-1: new high-speed USB device number 2 using ehci-pci
[    0.824605] usb 2-6: New USB device found, idVendor=05e3, idProduct=0732
[    0.824607] usb 2-6: New USB device strings: Mfr=3, Product=4, SerialNumber=5
[    0.824608] usb 2-6: Product: USB Reader
[    0.824609] usb 2-6: Manufacturer: Genesys
[    0.824610] usb 2-6: SerialNumber: 000000000696
[    0.828768] usb-storage 2-6:1.0: USB Mass Storage device detected
[    0.828855] scsi host6: usb-storage 2-6:1.0
[    0.830012] usbcore: registered new interface driver usb-storage
[    0.830819] usbcore: registered new interface driver uas
[    0.833907] usb 4-1: new high-speed USB device number 2 using ehci-pci
[    0.897813] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    0.897846] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    0.898512] ata2.00: ATA-9: ST1000DM003-1ER162, CC45, max UDMA/133
[    0.898514] ata2.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    0.898642] ata1.00: ATA-9: SanDisk SDSSDHII120G, X31200RL, max UDMA/133
[    0.898643] ata1.00: 234441648 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
[    0.899179] ata2.00: configured for UDMA/133
[    0.900205] ata1.00: configured for UDMA/133
[    0.900288] scsi 0:0:0:0: Direct-Access     ATA      SanDisk SDSSDHII 00RL PQ: 0 ANSI: 5
[    0.900412] sd 0:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    0.900424] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.900457] sd 0:0:0:0: [sda] Write Protect is off
[    0.900459] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.900472] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.900502] scsi 1:0:0:0: Direct-Access     ATA      ST1000DM003-1ER1 CC45 PQ: 0 ANSI: 5
[    0.900638] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    0.900648] sd 1:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    0.900650] sd 1:0:0:0: [sdb] 4096-byte physical blocks
[    0.900681] sd 1:0:0:0: [sdb] Write Protect is off
[    0.900683] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    0.900700] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.900859]  sda: sda1 sda2 < sda5 >
[    0.901105] sd 0:0:0:0: [sda] Attached SCSI disk
[    0.929932]  sdb: sdb1
[    0.930105] sd 1:0:0:0: [sdb] Attached SCSI disk
[    0.950066] usb 3-1: New USB device found, idVendor=8087, idProduct=8009
[    0.950068] usb 3-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    0.950322] hub 3-1:1.0: USB hub found
[    0.950439] hub 3-1:1.0: 6 ports detected
[    0.966028] usb 4-1: New USB device found, idVendor=8087, idProduct=8001
[    0.966030] usb 4-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    0.966178] hub 4-1:1.0: USB hub found
[    0.966278] hub 4-1:1.0: 8 ports detected
[    1.047975] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    1.125844] systemd[1]: Failed to insert module 'kdbus': Function not implemented
[    1.135768] systemd[1]: systemd 225 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ -LZ4 +SECCOMP +BLKID -ELFUTILS +KMOD -IDN)
[    1.135849] systemd[1]: Detected architecture x86-64.
[    1.135979] systemd[1]: Set hostname to <ordi-MS-7850>.
[    1.191836] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[    1.191871] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[    1.191880] systemd[1]: Reached target Encrypted Volumes.
[    1.191899] systemd[1]: Created slice Root Slice.
[    1.191919] systemd[1]: Listening on /dev/initctl Compatibility Named Pipe.
[    1.191939] systemd[1]: Listening on Journal Socket (/dev/log).
[    1.191959] systemd[1]: Listening on udev Control Socket.
[    1.191967] systemd[1]: Reached target Remote File Systems (Pre).
[    1.191988] systemd[1]: Listening on Journal Socket.
[    1.192040] systemd[1]: Listening on Journal Audit Socket.
[    1.192089] systemd[1]: Created slice User and Session Slice.
[    1.192105] systemd[1]: Listening on udev Kernel Socket.
[    1.192113] systemd[1]: Reached target User and Group Name Lookups.
[    1.192127] systemd[1]: Listening on fsck to fsckd communication Socket.
[    1.192170] systemd[1]: Created slice System Slice.
[    1.192435] systemd[1]: Starting Increase datagram queue length...
[    1.192452] systemd[1]: Reached target Slices.
[    1.193212] systemd[1]: Starting Load Kernel Modules...
[    1.193604] systemd[1]: Started Braille Device Support.
[    1.193809] systemd[1]: Created slice system-getty.slice.
[    1.194110] systemd[1]: Starting Create list of required static device nodes for the current kernel...
[    1.194370] systemd[1]: Starting Setup Virtual Console...
[    1.194659] systemd[1]: Starting Uncomplicated firewall...
[    1.194740] systemd[1]: Created slice system-systemd\x2dfsck.slice.
[    1.195032] systemd[1]: Started Read required files in advance.
[    1.195360] systemd[1]: Mounting POSIX Message Queue File System...
[    1.195661] systemd[1]: Mounting Debug File System...
[    1.196091] systemd[1]: Starting udev Coldplug all Devices...
[    1.196543] systemd[1]: Mounting Huge Pages File System...
[    1.201534] systemd[1]: Started Setup Virtual Console.
[    1.202573] systemd[1]: Started Create list of required static device nodes for the current kernel.
[    1.203037] systemd[1]: Starting Create Static Device Nodes in /dev...
[    1.204082] systemd[1]: Mounted Debug File System.
[    1.204103] systemd[1]: Mounted Huge Pages File System.
[    1.204112] systemd[1]: Mounted POSIX Message Queue File System.
[    1.204230] systemd[1]: Started Increase datagram queue length.
[    1.204355] systemd[1]: Started Uncomplicated firewall.
[    1.204549] systemd[1]: Listening on Syslog Socket.
[    1.204823] systemd[1]: Starting Journal Service...
[    1.219366] lp: driver loaded but no devices found
[    1.223552] ppdev: user-space parallel port driver
[    1.225547] parport_pc 00:06: reported by Plug and Play ACPI
[    1.225611] parport0: PC-style at 0x378, irq 5 [PCSPP]
[    1.231268] systemd[1]: Started Create Static Device Nodes in /dev.
[    1.231696] systemd[1]: Starting udev Kernel Device Manager...
[    1.240776] systemd[1]: Started udev Coldplug all Devices.
[    1.248082] systemd[1]: Started Journal Service.
[    1.266556] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    1.272226] systemd-journald[247]: Received request to flush runtime journal from PID 1
[    1.321251] lp0: using parport0 (interrupt-driven).
[    1.332237] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    1.389947] snd_hda_intel 0000:00:03.0: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[    1.397672] AVX2 version of gcm_enc/dec engaged.
[    1.397674] AES CTR mode by8 optimization enabled
[    1.410661] input: HDA Intel HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/sound/card0/input7
[    1.411466] snd_hda_codec_realtek hdaudioC1D0: autoconfig for ALC887-VD: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:line
[    1.411467] snd_hda_codec_realtek hdaudioC1D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    1.411469] snd_hda_codec_realtek hdaudioC1D0:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[    1.411469] snd_hda_codec_realtek hdaudioC1D0:    mono: mono_out=0x0
[    1.411470] snd_hda_codec_realtek hdaudioC1D0:    inputs:
[    1.411471] snd_hda_codec_realtek hdaudioC1D0:      Front Mic=0x19
[    1.411472] snd_hda_codec_realtek hdaudioC1D0:      Rear Mic=0x18
[    1.411473] snd_hda_codec_realtek hdaudioC1D0:      Line=0x1a
[    1.415958] input: HDA Intel HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:03.0/sound/card0/input8
[    1.416269] input: HDA Intel HDMI HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:03.0/sound/card0/input9
[    1.427184] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input10
[    1.427241] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input11
[    1.427368] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card1/input12
[    1.427430] input: HDA Intel PCH Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card1/input13
[    1.427485] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card1/input14
[    1.428659] Adding 4914172k swap on /dev/sda5.  Priority:-1 extents:1 across:4914172k SSFS
[    1.437866] intel_rapl: Found RAPL domain package
[    1.437869] intel_rapl: Found RAPL domain core
[    1.437873] intel_rapl: Found RAPL domain uncore
[    1.437874] intel_rapl: Found RAPL domain dram
[    1.456996] tsc: Refined TSC clocksource calibration: 3599.998 MHz
[    1.457001] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x33e451ab1a6, max_idle_ns: 440795278720 ns
[    1.628927] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[    1.690755] audit: type=1400 audit(1453394503.656:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=522 comm="apparmor_parser"
[    1.690760] audit: type=1400 audit(1453394503.656:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=522 comm="apparmor_parser"
[    1.692882] audit: type=1400 audit(1453394503.660:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=522 comm="apparmor_parser"
[    1.692886] audit: type=1400 audit(1453394503.660:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=522 comm="apparmor_parser"
[    1.692890] audit: type=1400 audit(1453394503.660:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=522 comm="apparmor_parser"
[    1.692894] audit: type=1400 audit(1453394503.660:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=522 comm="apparmor_parser"
[    1.702657] audit: type=1400 audit(1453394503.668:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince" pid=522 comm="apparmor_parser"
[    1.702662] audit: type=1400 audit(1453394503.668:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=522 comm="apparmor_parser"
[    1.702665] audit: type=1400 audit(1453394503.668:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-previewer" pid=522 comm="apparmor_parser"
[    1.763512] cgroup: new mount options do not match the existing superblock, will be ignored
[    1.770616] random: nonblocking pool is initialized
[    1.825385] scsi 6:0:0:0: Direct-Access     Generic  STORAGE DEVICE   0551 PQ: 0 ANSI: 5
[    1.825732] scsi 6:0:0:1: Direct-Access     Generic  STORAGE DEVICE   0551 PQ: 0 ANSI: 5
[    1.826067] scsi 6:0:0:2: Direct-Access     Generic  STORAGE DEVICE   0551 PQ: 0 ANSI: 5
[    1.826406] scsi 6:0:0:3: Direct-Access     Generic  STORAGE DEVICE   0551 PQ: 0 ANSI: 5
[    1.826741] scsi 6:0:0:4: Direct-Access     Generic  STORAGE DEVICE   0551 PQ: 0 ANSI: 5
[    1.827534] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    1.827673] sd 6:0:0:1: Attached scsi generic sg3 type 0
[    1.827783] sd 6:0:0:2: Attached scsi generic sg4 type 0
[    1.827881] sd 6:0:0:3: Attached scsi generic sg5 type 0
[    1.827975] sd 6:0:0:4: Attached scsi generic sg6 type 0
[    1.828075] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[    1.846084] sd 6:0:0:2: [sde] Attached SCSI removable disk
[    1.846507] sd 6:0:0:1: [sdd] Attached SCSI removable disk
[    1.846921] sd 6:0:0:3: [sdf] Attached SCSI removable disk
[    1.847346] sd 6:0:0:4: [sdg] Attached SCSI removable disk
[    1.908029] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[    1.950697] r8169 0000:02:00.0 enp2s0: link down
[    1.950716] r8169 0000:02:00.0 enp2s0: link down
[    1.950741] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[    2.455495] clocksource: Switched to clocksource tsc
[    4.590823] r8169 0000:02:00.0 enp2s0: link up
[    4.590830] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s0: link becomes ready
[   11.006015] usb 1-5: device descriptor read/64, error -110
[   11.247446] usb 1-5: New USB device found, idVendor=1c4f, idProduct=0002
[   11.247448] usb 1-5: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[   11.247449] usb 1-5: Product: USB Keykoard
[   11.247450] usb 1-5: Manufacturer: USB
[   11.247588] usb 1-5: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[   11.247591] usb 1-5: ep 0x82 - rounding interval to 64 microframes, ep desc says 80 microframes
[   11.413341] usb 1-6: new low-speed USB device number 3 using xhci_hcd
[   11.601791] usb 1-6: New USB device found, idVendor=1267, idProduct=0210
[   11.601793] usb 1-6: New USB device strings: Mfr=0, Product=2, SerialNumber=0
[   11.601794] usb 1-6: Product: PS/2+USB Mouse
[   11.601920] usb 1-6: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[   11.612647] hidraw: raw HID events driver (C) Jiri Kosina
[   11.621573] usbcore: registered new interface driver usbhid
[   11.621575] usbhid: USB HID core driver
[   11.623643] input: USB USB Keykoard as /devices/pci0000:00/0000:00:14.0/usb1/1-5/1-5:1.0/0003:1C4F:0002.0001/input/input15
[   11.677026] hid-generic 0003:1C4F:0002.0001: input,hidraw0: USB HID v1.10 Keyboard [USB USB Keykoard] on usb-0000:00:14.0-5/input0
[   11.677144] input: USB USB Keykoard as /devices/pci0000:00/0000:00:14.0/usb1/1-5/1-5:1.1/0003:1C4F:0002.0002/input/input16
[   11.732951] hid-generic 0003:1C4F:0002.0002: input,hidraw1: USB HID v1.10 Device [USB USB Keykoard] on usb-0000:00:14.0-5/input1
[   11.733040] input: PS/2+USB Mouse as /devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.0/0003:1267:0210.0003/input/input17
[   11.792880] hid-generic 0003:1267:0210.0003: input,hidraw2: USB HID v1.00 Mouse [PS/2+USB Mouse] on usb-0000:00:14.0-6/input0
[   34.877312] usb 1-5: USB disconnect, device number 2
[   38.400173] usb 1-5: new low-speed USB device number 4 using xhci_hcd
[   38.539251] usb 1-5: New USB device found, idVendor=1c4f, idProduct=0002
[   38.539253] usb 1-5: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[   38.539254] usb 1-5: Product: USB Keykoard
[   38.539255] usb 1-5: Manufacturer: USB
[   38.539393] usb 1-5: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[   38.539397] usb 1-5: ep 0x82 - rounding interval to 64 microframes, ep desc says 80 microframes
[   38.542001] input: USB USB Keykoard as /devices/pci0000:00/0000:00:14.0/usb1/1-5/1-5:1.0/0003:1C4F:0002.0004/input/input18
[   38.598881] hid-generic 0003:1C4F:0002.0004: input,hidraw0: USB HID v1.10 Keyboard [USB USB Keykoard] on usb-0000:00:14.0-5/input0
[   38.601060] input: USB USB Keykoard as /devices/pci0000:00/0000:00:14.0/usb1/1-5/1-5:1.1/0003:1C4F:0002.0005/input/input19
[   38.655505] hid-generic 0003:1C4F:0002.0005: input,hidraw1: USB HID v1.10 Device [USB USB Keykoard] on usb-0000:00:14.0-5/input1
[   39.037338] usb 1-6: USB disconnect, device number 3
[   51.730280] usb 1-6: new low-speed USB device number 5 using xhci_hcd
[   51.863478] usb 1-6: New USB device found, idVendor=1267, idProduct=0210
[   51.863480] usb 1-6: New USB device strings: Mfr=0, Product=2, SerialNumber=0
[   51.863481] usb 1-6: Product: PS/2+USB Mouse
[   51.863619] usb 1-6: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[   51.867151] input: PS/2+USB Mouse as /devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.0/0003:1267:0210.0006/input/input20
[   51.867305] hid-generic 0003:1267:0210.0006: input,hidraw2: USB HID v1.00 Mouse [PS/2+USB Mouse] on usb-0000:00:14.0-6/input0
[   53.113331] usb 1-6: USB disconnect, device number 5
[   71.422318] usb 1-6: new low-speed USB device number 6 using xhci_hcd
[   71.610909] usb 1-6: New USB device found, idVendor=1267, idProduct=0210
[   71.610916] usb 1-6: New USB device strings: Mfr=0, Product=2, SerialNumber=0
[   71.610920] usb 1-6: Product: PS/2+USB Mouse
[   71.611125] usb 1-6: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[   71.615111] input: PS/2+USB Mouse as /devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.0/0003:1267:0210.0007/input/input21 [COLOR=#FFFFFF][   71.615429] hid-generic 0003:1267:0210.0007: input,hidraw2: USB HID v1.00 Mouse [PS/2+USB Mouse] on usb-0000:00:14.0-6/input0[/COLOR]
```

and this part give my attention

```


[    0.115933] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.116062] acpi PNP0A08:00: _OSC: platform does not support [PCIeHotplug PME]
[    0.116137] acpi PNP0A08:00: _OSC: OS now controls [AER PCIeCapability]
[    0.116138] acpi PNP0A08:00: FADT indicates ASPM is unsupported, using BIOS configuration
```

the card is not working (usb3 devices works good when i put on the usb3 of motherboard), i really need more usb3 inside computer

so, what's wrong ?

---

### Post by fraiddo on 2016-01-22
links to screens of my bios :

- [http://imgur.com/a/uvvz1](http://imgur.com/a/uvvz1)
- [http://imgur.com/a/USaWW/](http://imgur.com/a/USaWW/)

---

### Post by fraiddo on 2016-01-25
nobody ? :(

---

