---
title: "Radeon X1300 Worked, then it didn't"
date: 2015-01-07
forum: Hardware
---

### Post by sbarrow47 on 2015-01-07
I've been running an X1300 for months now. Earlier today I tried to enable Compiz, which wound up screwing up Gnome in a big way, deleted my config and uninstalled Unity which seemed to fix it. But now I'm stuck in software rendering.

Relevant files attached. I have the xserver-xorg-video-radeon and xserver-xorg-video-ati packages installed. I also reinstalled unity. I do not nor have I ever (as far as I can remember) had fglrx installed.

```
[    0.000000] Initializing cgroup subsys cpuset[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-43-generic (buildd@tipua) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #72-Ubuntu SMP Mon Dec 8 19:35:06 UTC 2014 (Ubuntu 3.13.0-43.72-generic 3.13.11.11)
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.13.0-43-generic root=UUID=af35895a-fc9e-4d61-b4f4-d24e6c2b3acf ro quiet splash nomdmonddf nomdmonisw nomdmonddf nomdmonisw vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009efff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009f000-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e4000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000cfe7ffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000cfe80000-0x00000000cfe97fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000cfe98000-0x00000000cfebffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000cfec0000-0x00000000cfefffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffe00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000042effffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.5 present.
[    0.000000] DMI: System manufacturer System Product Name/M5A78L-M LX PLUS, BIOS 1302    11/14/2012
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x42f000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 base 0000C0000000 mask FFFFF0000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 000000042f000000 aka 17136M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820: update [mem 0xd0000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xcfe80 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000ff780-0x000ff78f] mapped at [ffff8800000ff780]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fe1000, 0x01fe1fff] PGTABLE
[    0.000000] BRK [0x01fe2000, 0x01fe2fff] PGTABLE
[    0.000000] BRK [0x01fe3000, 0x01fe3fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x42ee00000-0x42effffff]
[    0.000000]  [mem 0x42ee00000-0x42effffff] page 2M
[    0.000000] BRK [0x01fe4000, 0x01fe4fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x42c000000-0x42edfffff]
[    0.000000]  [mem 0x42c000000-0x42edfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x400000000-0x42bffffff]
[    0.000000]  [mem 0x400000000-0x42bffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0xcfe7ffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
[    0.000000]  [mem 0x40000000-0xbfffffff] page 1G
[    0.000000]  [mem 0xc0000000-0xcfdfffff] page 2M
[    0.000000]  [mem 0xcfe00000-0xcfe7ffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x3ffffffff]
[    0.000000]  [mem 0x100000000-0x3ffffffff] page 1G
[    0.000000] RAMDISK: [mem 0x34a52000-0x36520fff]
[    0.000000] ACPI: RSDP 00000000000fb490 000024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 00000000cfe80100 000054 (v01 111412 XSDT1100 20121114 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000cfe80290 0000F4 (v03 111412 FACP1100 20121114 MSFT 00000097)
[    0.000000] ACPI BIOS Warning (bug): Optional FADT field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20131115/tbfadt-603)
[    0.000000] ACPI: DSDT 00000000cfe80460 00D86A (v01  A1969 A1969001 00000001 INTL 20060113)
[    0.000000] ACPI: FACS 00000000cfe98000 000040
[    0.000000] ACPI: APIC 00000000cfe80390 00008C (v01 111412 APIC1100 20121114 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000cfe80420 00003C (v01 111412 OEMMCFG  20121114 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000cfe98040 000072 (v01 111412 OEMB1100 20121114 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000cfe8f460 000038 (v01 111412 OEMHPET  20121114 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000cfe8f4a0 001158 (v01 A M I  POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000042effffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x42effffff]
[    0.000000]   NODE_DATA [mem 0x42eff9000-0x42effdfff]
[    0.000000]  [ffffea0000000000-ffffea0010bfffff] PMD -> [ffff88041e600000-ffff88042e5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x42effffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0xcfe7ffff]
[    0.000000]   node   0: [mem 0x100000000-0x42effffff]
[    0.000000] On node 0 totalpages: 4189726
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3998 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 13242 pages used for memmap
[    0.000000]   DMA32 zone: 847488 pages, LIFO batch:31
[    0.000000]   Normal zone: 52160 pages used for memmap
[    0.000000]   Normal zone: 3338240 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x10] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x11] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x12] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x13] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x14] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x15] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x86] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x87] disabled)
[    0.000000] ACPI: IOAPIC (id[0x16] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 22, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000e3fff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e4000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xcfe80000-0xcfe97fff]
[    0.000000] PM: Registered nosave memory: [mem 0xcfe98000-0xcfebffff]
[    0.000000] PM: Registered nosave memory: [mem 0xcfec0000-0xcfefffff]
[    0.000000] PM: Registered nosave memory: [mem 0xcff00000-0xffdfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xffe00000-0xffffffff]
[    0.000000] e820: [mem 0xcff00000-0xffdfffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88042ec00000 s82304 r8192 d24192 u262144
[    0.000000] pcpu-alloc: s82304 r8192 d24192 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 4124239
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.13.0-43-generic root=UUID=af35895a-fc9e-4d61-b4f4-d24e6c2b3acf ro quiet splash nomdmonddf nomdmonisw nomdmonddf nomdmonisw vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ 0 size 32 MB
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ c4000000
[    0.000000] PM: Registered nosave memory: [mem 0xc4000000-0xc7ffffff]
[    0.000000] Memory: 16320176K/16758904K available (7383K kernel code, 1144K rwdata, 3408K rodata, 1336K init, 1444K bss, 438728K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-7.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 67108864 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration failed
[    0.008000] tsc: PIT calibration matches HPET. 1 loops
[    0.008000] tsc: Detected 3515.763 MHz processor
[    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 7031.52 BogoMIPS (lpj=14063052)
[    0.000005] pid_max: default: 32768 minimum: 301
[    0.000031] Security Framework initialized
[    0.000050] AppArmor: AppArmor initialized
[    0.000052] Yama: becoming mindful.
[    0.001143] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes)
[    0.004859] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.006488] Mount-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.006507] Mountpoint-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.006754] Initializing cgroup subsys memory
[    0.006759] Initializing cgroup subsys devices
[    0.006760] Initializing cgroup subsys freezer
[    0.006762] Initializing cgroup subsys blkio
[    0.006763] Initializing cgroup subsys perf_event
[    0.006765] Initializing cgroup subsys hugetlb
[    0.006781] tseg: 0000000000
[    0.006786] CPU: Physical Processor ID: 0
[    0.006787] CPU: Processor Core ID: 0
[    0.006788] mce: CPU supports 7 MCE banks
[    0.006794] LVT offset 1 assigned for vector 0xf9
[    0.006799] Last level iTLB entries: 4KB 512, 2MB 1024, 4MB 512
[    0.006799] Last level dTLB entries: 4KB 1024, 2MB 1024, 4MB 512
[    0.006799] tlb_flushall_shift: 5
[    0.006877] Freeing SMP alternatives memory: 32K (ffffffff81e6e000 - ffffffff81e76000)
[    0.007623] ACPI: Core revision 20131115
[    0.010955] ACPI: All ACPI Tables successfully acquired
[    0.020197] ftrace: allocating 28552 entries in 112 pages
[    0.028925] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.068576] smpboot: CPU0: AMD FX(tm)-6300 Six-Core Processor (fam: 15, model: 02, stepping: 00)
[    0.175578] Performance Events: Fam15h core perfctr, AMD PMU driver.
[    0.175583] ... version:                0
[    0.175584] ... bit width:              48
[    0.175585] ... generic registers:      6
[    0.175586] ... value mask:             0000ffffffffffff
[    0.175587] ... max period:             00007fffffffffff
[    0.175588] ... fixed-purpose events:   0
[    0.175589] ... event mask:             000000000000003f
[    0.177144] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.177212] x86: Booting SMP configuration:
[    0.177214] .... node  #0, CPUs:      #1 #2 #3 #4 #5
[    0.243168] x86: Booted up 1 node, 6 CPUs
[    0.243171] smpboot: Total of 6 processors activated (42189.15 BogoMIPS)
[    0.250849] devtmpfs: initialized
[    0.254613] EVM: security.selinux
[    0.254614] EVM: security.SMACK64
[    0.254615] EVM: security.ima
[    0.254616] EVM: security.capability
[    0.254689] PM: Registering ACPI NVS region [mem 0xcfe98000-0xcfebffff] (163840 bytes)
[    0.255437] pinctrl core: initialized pinctrl subsystem
[    0.255491] regulator-dummy: no parameters
[    0.255521] RTC time:  3:24:21, date: 01/08/15
[    0.255552] NET: Registered protocol family 16
[    0.255674] cpuidle: using governor ladder
[    0.255675] cpuidle: using governor menu
[    0.255750] ACPI: bus type PCI registered
[    0.255752] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.255803] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.255805] PCI: not using MMCONFIG
[    0.255806] PCI: Using configuration type 1 for base access
[    0.255807] PCI: Using configuration type 1 for extended access
[    0.256116] mtrr: your CPUs had inconsistent variable MTRR settings
[    0.256117] mtrr: probably your BIOS does not setup all CPUs.
[    0.256117] mtrr: corrected configuration.
[    0.256941] bio: create slab <bio-0> at 0
[    0.257104] ACPI: Added _OSI(Module Device)
[    0.257106] ACPI: Added _OSI(Processor Device)
[    0.257107] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.257108] ACPI: Added _OSI(Processor Aggregator Device)
[    0.260584] ACPI: Executed 3 blocks of module-level executable AML code
[    0.368024] ACPI: Interpreter enabled
[    0.368035] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.368052] ACPI: (supports S0 S1 S3 S4 S5)
[    0.368054] ACPI: Using IOAPIC for interrupt routing
[    0.368074] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.369793] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.379464] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.379574] ACPI: No dock devices found.
[    0.428585] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.428590] acpi PNP0A03:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.428594] acpi PNP0A03:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[    0.428960] PCI host bridge to bus 0000:00
[    0.428963] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.428964] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.428966] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.428968] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.428970] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000dffff]
[    0.428971] pci_bus 0000:00: root bus resource [mem 0xcff00000-0xdfffffff]
[    0.428973] pci_bus 0000:00: root bus resource [mem 0xf0000000-0xfebfffff]
[    0.428982] pci 0000:00:00.0: [1022:9600] type 00 class 0x060000
[    0.429088] pci 0000:00:02.0: [1022:9603] type 01 class 0x060400
[    0.429123] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.429173] pci 0000:00:02.0: System wakeup disabled by ACPI
[    0.429199] pci 0000:00:04.0: [1022:9604] type 01 class 0x060400
[    0.429233] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    0.429281] pci 0000:00:04.0: System wakeup disabled by ACPI
[    0.429313] pci 0000:00:09.0: [1022:9608] type 01 class 0x060400
[    0.429347] pci 0000:00:09.0: PME# supported from D0 D3hot D3cold
[    0.429396] pci 0000:00:09.0: System wakeup disabled by ACPI
[    0.429437] pci 0000:00:11.0: [1002:4390] type 00 class 0x01018f
[    0.429456] pci 0000:00:11.0: reg 0x10: [io  0xc000-0xc007]
[    0.429466] pci 0000:00:11.0: reg 0x14: [io  0xb000-0xb003]
[    0.429475] pci 0000:00:11.0: reg 0x18: [io  0xa000-0xa007]
[    0.429485] pci 0000:00:11.0: reg 0x1c: [io  0x9000-0x9003]
[    0.429494] pci 0000:00:11.0: reg 0x20: [io  0x8000-0x800f]
[    0.429504] pci 0000:00:11.0: reg 0x24: [mem 0xfe9ffc00-0xfe9fffff]
[    0.429524] pci 0000:00:11.0: set SATA to AHCI mode
[    0.429625] pci 0000:00:12.0: [1002:4397] type 00 class 0x0c0310
[    0.429638] pci 0000:00:12.0: reg 0x10: [mem 0xfe9fe000-0xfe9fefff]
[    0.429737] pci 0000:00:12.0: System wakeup disabled by ACPI
[    0.429762] pci 0000:00:12.1: [1002:4398] type 00 class 0x0c0310
[    0.429776] pci 0000:00:12.1: reg 0x10: [mem 0xfe9fd000-0xfe9fdfff]
[    0.429875] pci 0000:00:12.1: System wakeup disabled by ACPI
[    0.429909] pci 0000:00:12.2: [1002:4396] type 00 class 0x0c0320
[    0.429928] pci 0000:00:12.2: reg 0x10: [mem 0xfe9ff800-0xfe9ff8ff]
[    0.430012] pci 0000:00:12.2: supports D1 D2
[    0.430013] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.430064] pci 0000:00:12.2: System wakeup disabled by ACPI
[    0.430095] pci 0000:00:13.0: [1002:4397] type 00 class 0x0c0310
[    0.430108] pci 0000:00:13.0: reg 0x10: [mem 0xfe9fc000-0xfe9fcfff]
[    0.430207] pci 0000:00:13.0: System wakeup disabled by ACPI
[    0.430232] pci 0000:00:13.1: [1002:4398] type 00 class 0x0c0310
[    0.430245] pci 0000:00:13.1: reg 0x10: [mem 0xfe9fb000-0xfe9fbfff]
[    0.430345] pci 0000:00:13.1: System wakeup disabled by ACPI
[    0.430376] pci 0000:00:13.2: [1002:4396] type 00 class 0x0c0320
[    0.430395] pci 0000:00:13.2: reg 0x10: [mem 0xfe9ff400-0xfe9ff4ff]
[    0.430479] pci 0000:00:13.2: supports D1 D2
[    0.430480] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.430530] pci 0000:00:13.2: System wakeup disabled by ACPI
[    0.430567] pci 0000:00:14.0: [1002:4385] type 00 class 0x0c0500
[    0.430721] pci 0000:00:14.1: [1002:439c] type 00 class 0x01018a
[    0.430738] pci 0000:00:14.1: reg 0x10: [io  0x0000-0x0007]
[    0.430747] pci 0000:00:14.1: reg 0x14: [io  0x0000-0x0003]
[    0.430756] pci 0000:00:14.1: reg 0x18: [io  0x0000-0x0007]
[    0.430765] pci 0000:00:14.1: reg 0x1c: [io  0x0000-0x0003]
[    0.430775] pci 0000:00:14.1: reg 0x20: [io  0xff00-0xff0f]
[    0.430887] pci 0000:00:14.2: [1002:4383] type 00 class 0x040300
[    0.430909] pci 0000:00:14.2: reg 0x10: [mem 0xfe9f4000-0xfe9f7fff 64bit]
[    0.430976] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.431025] pci 0000:00:14.2: System wakeup disabled by ACPI
[    0.431052] pci 0000:00:14.3: [1002:439d] type 00 class 0x060100
[    0.431182] pci 0000:00:14.4: [1002:4384] type 01 class 0x060401
[    0.431258] pci 0000:00:14.4: System wakeup disabled by ACPI
[    0.431287] pci 0000:00:14.5: [1002:4399] type 00 class 0x0c0310
[    0.431301] pci 0000:00:14.5: reg 0x10: [mem 0xfe9fa000-0xfe9fafff]
[    0.431403] pci 0000:00:14.5: System wakeup disabled by ACPI
[    0.431434] pci 0000:00:18.0: [1022:1600] type 00 class 0x060000
[    0.431506] pci 0000:00:18.1: [1022:1601] type 00 class 0x060000
[    0.431571] pci 0000:00:18.2: [1022:1602] type 00 class 0x060000
[    0.431638] pci 0000:00:18.3: [1022:1603] type 00 class 0x060000
[    0.431709] pci 0000:00:18.4: [1022:1604] type 00 class 0x060000
[    0.431775] pci 0000:00:18.5: [1022:1605] type 00 class 0x060000
[    0.431887] pci 0000:01:00.0: [1002:7146] type 00 class 0x030000
[    0.431899] pci 0000:01:00.0: reg 0x10: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.431909] pci 0000:01:00.0: reg 0x18: [mem 0xfeae0000-0xfeaeffff 64bit]
[    0.431915] pci 0000:01:00.0: reg 0x20: [io  0xd000-0xd0ff]
[    0.431927] pci 0000:01:00.0: reg 0x30: [mem 0xfeac0000-0xfeadffff pref]
[    0.431955] pci 0000:01:00.0: supports D1 D2
[    0.431986] pci 0000:01:00.1: [1002:7166] type 00 class 0x038000
[    0.431997] pci 0000:01:00.1: reg 0x10: [mem 0xfeab0000-0xfeabffff 64bit]
[    0.432045] pci 0000:01:00.1: supports D1 D2
[    0.432072] pci 0000:01:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.432080] pci 0000:00:02.0: PCI bridge to [bus 01]
[    0.432083] pci 0000:00:02.0:   bridge window [io  0xd000-0xdfff]
[    0.432085] pci 0000:00:02.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.432089] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.432143] pci 0000:02:00.0: [10ec:8168] type 00 class 0x020000
[    0.432155] pci 0000:02:00.0: reg 0x10: [io  0xe800-0xe8ff]
[    0.432176] pci 0000:02:00.0: reg 0x18: [mem 0xfdfff000-0xfdffffff 64bit pref]
[    0.432189] pci 0000:02:00.0: reg 0x20: [mem 0xfdff8000-0xfdffbfff 64bit pref]
[    0.432243] pci 0000:02:00.0: supports D1 D2
[    0.432244] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.432271] pci 0000:02:00.0: System wakeup disabled by ACPI
[    0.439350] pci 0000:00:04.0: PCI bridge to [bus 02]
[    0.439354] pci 0000:00:04.0:   bridge window [io  0xe000-0xefff]
[    0.439358] pci 0000:00:04.0:   bridge window [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.439408] pci 0000:03:00.0: [168c:002e] type 00 class 0x028000
[    0.439425] pci 0000:03:00.0: reg 0x10: [mem 0xfebf0000-0xfebfffff 64bit]
[    0.439501] pci 0000:03:00.0: supports D1
[    0.439502] pci 0000:03:00.0: PME# supported from D0 D1 D3hot
[    0.447340] pci 0000:00:09.0: PCI bridge to [bus 03]
[    0.447345] pci 0000:00:09.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.447419] pci 0000:00:14.4: PCI bridge to [bus 04] (subtractive decode)
[    0.447428] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.447430] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.447431] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.447433] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.447434] pci 0000:00:14.4:   bridge window [mem 0xcff00000-0xdfffffff] (subtractive decode)
[    0.447436] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
[    0.463401] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 7 *10 12 14 15)
[    0.463451] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 10 *11 12 14 15)
[    0.463500] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 *10 11 12 14 15)
[    0.463547] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 10 *11 12 14 15)
[    0.463595] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.463644] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.463691] ACPI: PCI Interrupt Link [LNKG] (IRQs *11)
[    0.463737] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.463942] ACPI: Enabled 1 GPEs in block 00 to 1F
[    0.463948] ACPI: \_SB_.PCI0: notify handler is installed
[    0.463984] Found 1 acpi root devices
[    0.464067] vgaarb: setting as boot device: PCI:0000:01:00.0
[    0.464068] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.464070] vgaarb: loaded
[    0.464071] vgaarb: bridge control possible 0000:01:00.0
[    0.464218] SCSI subsystem initialized
[    0.464270] libata version 3.00 loaded.
[    0.464288] ACPI: bus type USB registered
[    0.464301] usbcore: registered new interface driver usbfs
[    0.464315] usbcore: registered new interface driver hub
[    0.464337] usbcore: registered new device driver usb
[    0.464438] PCI: Using ACPI for IRQ routing
[    0.473133] PCI: pci_cache_line_size set to 64 bytes
[    0.473187] e820: reserve RAM buffer [mem 0x0009f000-0x0009ffff]
[    0.473189] e820: reserve RAM buffer [mem 0xcfe80000-0xcfffffff]
[    0.473190] e820: reserve RAM buffer [mem 0x42f000000-0x42fffffff]
[    0.473254] NetLabel: Initializing
[    0.473255] NetLabel:  domain hash size = 128
[    0.473256] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.473266] NetLabel:  unlabeled traffic allowed by default
[    0.473329] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.473333] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.475398] Switched to clocksource hpet
[    0.481003] AppArmor: AppArmor Filesystem Enabled
[    0.481018] pnp: PnP ACPI init
[    0.481026] ACPI: bus type PNP registered
[    0.481152] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.481187] pnp 00:01: [dma 4]
[    0.481203] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.481232] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.481251] pnp 00:03: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.481277] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.481942] pnp 00:05: [dma 0 disabled]
[    0.482166] pnp 00:05: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.482214] pnp 00:06: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.482716] pnp 00:07: [dma 0 disabled]
[    0.482777] pnp 00:07: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.482883] system 00:08: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.482885] system 00:08: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.482888] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.483137] system 00:09: [io  0x04d0-0x04d1] has been reserved
[    0.483139] system 00:09: [io  0x040b] has been reserved
[    0.483141] system 00:09: [io  0x04d6] has been reserved
[    0.483143] system 00:09: [io  0x0c00-0x0c01] has been reserved
[    0.483145] system 00:09: [io  0x0c14] has been reserved
[    0.483146] system 00:09: [io  0x0c50-0x0c51] has been reserved
[    0.483148] system 00:09: [io  0x0c52] has been reserved
[    0.483149] system 00:09: [io  0x0c6c] has been reserved
[    0.483151] system 00:09: [io  0x0c6f] has been reserved
[    0.483153] system 00:09: [io  0x0cd0-0x0cd1] has been reserved
[    0.483154] system 00:09: [io  0x0cd2-0x0cd3] has been reserved
[    0.483156] system 00:09: [io  0x0cd4-0x0cd5] has been reserved
[    0.483157] system 00:09: [io  0x0cd6-0x0cd7] has been reserved
[    0.483159] system 00:09: [io  0x0cd8-0x0cdf] has been reserved
[    0.483161] system 00:09: [io  0x0b00-0x0b3f] has been reserved
[    0.483162] system 00:09: [io  0x0800-0x089f] could not be reserved
[    0.483164] system 00:09: [io  0x0b00-0x0b0f] has been reserved
[    0.483166] system 00:09: [io  0x0b20-0x0b3f] has been reserved
[    0.483167] system 00:09: [io  0x0900-0x090f] has been reserved
[    0.483169] system 00:09: [io  0x0910-0x091f] has been reserved
[    0.483171] system 00:09: [io  0xfe00-0xfefe] has been reserved
[    0.483173] system 00:09: [mem 0xcff00000-0xcfffffff] has been reserved
[    0.483175] system 00:09: [mem 0xffb80000-0xffbfffff] has been reserved
[    0.483176] system 00:09: [mem 0xfec10000-0xfec1001f] has been reserved
[    0.483178] system 00:09: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.483180] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.483399] system 00:0a: [io  0x0230-0x023f] has been reserved
[    0.483401] system 00:0a: [io  0x0290-0x029f] has been reserved
[    0.483402] system 00:0a: [io  0x0300-0x030f] has been reserved
[    0.483404] system 00:0a: [io  0x0a30-0x0a3f] has been reserved
[    0.483406] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.483461] system 00:0b: [mem 0xe0000000-0xefffffff] has been reserved
[    0.483463] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.499564] system 00:0c: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.499567] system 00:0c: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.499569] system 00:0c: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.499571] system 00:0c: [mem 0x00100000-0xcfefffff] could not be reserved
[    0.499573] system 00:0c: [mem 0xfec00000-0xffffffff] could not be reserved
[    0.499575] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.499679] pnp: PnP ACPI: found 13 devices
[    0.499680] ACPI: bus type PNP unregistered
[    0.505996] pci 0000:00:02.0: PCI bridge to [bus 01]
[    0.505998] pci 0000:00:02.0:   bridge window [io  0xd000-0xdfff]
[    0.506001] pci 0000:00:02.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.506004] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.506007] pci 0000:00:04.0: PCI bridge to [bus 02]
[    0.506009] pci 0000:00:04.0:   bridge window [io  0xe000-0xefff]
[    0.506012] pci 0000:00:04.0:   bridge window [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.506015] pci 0000:00:09.0: PCI bridge to [bus 03]
[    0.506018] pci 0000:00:09.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.506022] pci 0000:00:14.4: PCI bridge to [bus 04]
[    0.506034] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.506035] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.506037] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.506039] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.506040] pci_bus 0000:00: resource 8 [mem 0xcff00000-0xdfffffff]
[    0.506041] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.506043] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.506044] pci_bus 0000:01: resource 1 [mem 0xfea00000-0xfeafffff]
[    0.506046] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.506047] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.506049] pci_bus 0000:02: resource 2 [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.506051] pci_bus 0000:03: resource 1 [mem 0xfeb00000-0xfebfffff]
[    0.506052] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
[    0.506054] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
[    0.506055] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    0.506056] pci_bus 0000:04: resource 7 [mem 0x000d0000-0x000dffff]
[    0.506058] pci_bus 0000:04: resource 8 [mem 0xcff00000-0xdfffffff]
[    0.506059] pci_bus 0000:04: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.506081] NET: Registered protocol family 2
[    0.506310] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.506574] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.506751] TCP: Hash tables configured (established 131072 bind 65536)
[    0.506777] TCP: reno registered
[    0.506799] UDP hash table entries: 8192 (order: 6, 262144 bytes)
[    0.506866] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes)
[    0.506965] NET: Registered protocol family 1
[    0.931135] pci 0000:01:00.0: Video device with shadowed ROM
[    0.931143] PCI: CLS 64 bytes, default 64
[    0.931191] Trying to unpack rootfs image as initramfs...
[    1.301494] Freeing initrd memory: 27452K (ffff880034a52000 - ffff880036521000)
[    1.301751] PCI-DMA: Disabling AGP.
[    1.301822] PCI-DMA: aperture base @ c4000000 size 65536 KB
[    1.301824] PCI-DMA: using GART IOMMU.
[    1.301827] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    1.306303] perf: AMD NB counters detected
[    1.306328] LVT offset 0 assigned for vector 0x400
[    1.306353] perf: AMD IBS detected (0x000000ff)
[    1.306391] microcode: CPU0: patch_level=0x0600081c
[    1.306397] microcode: CPU1: patch_level=0x0600081c
[    1.306406] microcode: CPU2: patch_level=0x0600081c
[    1.306415] microcode: CPU3: patch_level=0x0600081c
[    1.306423] microcode: CPU4: patch_level=0x0600081c
[    1.306432] microcode: CPU5: patch_level=0x0600081c
[    1.306513] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.306515] Scanning for low memory corruption every 60 seconds
[    1.306813] Initialise system trusted keyring
[    1.306848] audit: initializing netlink socket (disabled)
[    1.306856] type=2000 audit(1420687462.192:1): initialized
[    1.328872] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.330138] zbud: loaded
[    1.330247] VFS: Disk quotas dquot_6.5.2
[    1.330281] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.330702] fuse init (API version 7.22)
[    1.330766] msgmni has been set to 32057
[    1.330812] Key type big_key registered
[    1.331304] Key type asymmetric registered
[    1.331306] Asymmetric key parser 'x509' registered
[    1.331330] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.331373] io scheduler noop registered
[    1.331374] io scheduler deadline registered (default)
[    1.331394] io scheduler cfq registered
[    1.331607] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    1.331756] pcieport 0000:00:04.0: irq 41 for MSI/MSI-X
[    1.331903] pcieport 0000:00:09.0: irq 42 for MSI/MSI-X
[    1.331950] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.331962] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.331993] vesafb: mode is 1280x1024x32, linelength=5120, pages=0
[    1.331994] vesafb: scrolling: redraw
[    1.331996] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[    1.332219] vesafb: framebuffer at 0xd0000000, mapped to 0xffffc90011c00000, using 5120k, total 5120k
[    1.353707] Console: switching to colour frame buffer device 160x64
[    1.375108] fb0: VESA VGA frame buffer device
[    1.375124] ipmi message handler version 39.2
[    1.375174] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.375177] ACPI: Power Button [PWRB]
[    1.375206] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.375208] ACPI: Power Button [PWRF]
[    1.375442] ACPI: acpi_idle registered with cpuidle
[    1.376715] GHES: HEST is not enabled!
[    1.376791] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.397237] 00:07: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    1.398559] Linux agpgart interface v0.103
[    1.399793] brd: module loaded
[    1.400418] loop: module loaded
[    1.400738] libphy: Fixed MDIO Bus: probed
[    1.400815] tun: Universal TUN/TAP device driver, 1.6
[    1.400816] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.400859] PPP generic driver version 2.4.2
[    1.400899] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.400902] ehci-pci: EHCI PCI platform driver
[    1.401037] ehci-pci 0000:00:12.2: EHCI Host Controller
[    1.401041] ehci-pci 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.401045] ehci-pci 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.401056] ehci-pci 0000:00:12.2: debug port 1
[    1.401092] ehci-pci 0000:00:12.2: irq 17, io mem 0xfe9ff800
[    1.410595] ehci-pci 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.410641] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.410643] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.410645] usb usb1: Product: EHCI Host Controller
[    1.410646] usb usb1: Manufacturer: Linux 3.13.0-43-generic ehci_hcd
[    1.410648] usb usb1: SerialNumber: 0000:00:12.2
[    1.410749] hub 1-0:1.0: USB hub found
[    1.410754] hub 1-0:1.0: 6 ports detected
[    1.410995] ehci-pci 0000:00:13.2: EHCI Host Controller
[    1.410999] ehci-pci 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.411001] ehci-pci 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.411012] ehci-pci 0000:00:13.2: debug port 1
[    1.411045] ehci-pci 0000:00:13.2: irq 19, io mem 0xfe9ff400
[    1.422578] ehci-pci 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.422609] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.422611] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.422612] usb usb2: Product: EHCI Host Controller
[    1.422613] usb usb2: Manufacturer: Linux 3.13.0-43-generic ehci_hcd
[    1.422615] usb usb2: SerialNumber: 0000:00:13.2
[    1.422724] hub 2-0:1.0: USB hub found
[    1.422738] hub 2-0:1.0: 6 ports detected
[    1.422849] ehci-platform: EHCI generic platform driver
[    1.422855] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.422856] ohci-pci: OHCI PCI platform driver
[    1.422987] ohci-pci 0000:00:12.0: OHCI PCI host controller
[    1.422990] ohci-pci 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.423008] ohci-pci 0000:00:12.0: irq 16, io mem 0xfe9fe000
[    1.482582] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.482584] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.482586] usb usb3: Product: OHCI PCI host controller
[    1.482588] usb usb3: Manufacturer: Linux 3.13.0-43-generic ohci_hcd
[    1.482589] usb usb3: SerialNumber: 0000:00:12.0
[    1.482702] hub 3-0:1.0: USB hub found
[    1.482717] hub 3-0:1.0: 3 ports detected
[    1.482910] ohci-pci 0000:00:12.1: OHCI PCI host controller
[    1.482915] ohci-pci 0000:00:12.1: new USB bus registered, assigned bus number 4
[    1.482927] ohci-pci 0000:00:12.1: irq 16, io mem 0xfe9fd000
[    1.542527] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.542530] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.542531] usb usb4: Product: OHCI PCI host controller
[    1.542533] usb usb4: Manufacturer: Linux 3.13.0-43-generic ohci_hcd
[    1.542534] usb usb4: SerialNumber: 0000:00:12.1
[    1.542654] hub 4-0:1.0: USB hub found
[    1.542665] hub 4-0:1.0: 3 ports detected
[    1.542859] ohci-pci 0000:00:13.0: OHCI PCI host controller
[    1.542863] ohci-pci 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.542883] ohci-pci 0000:00:13.0: irq 18, io mem 0xfe9fc000
[    1.602474] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.602477] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.602479] usb usb5: Product: OHCI PCI host controller
[    1.602480] usb usb5: Manufacturer: Linux 3.13.0-43-generic ohci_hcd
[    1.602481] usb usb5: SerialNumber: 0000:00:13.0
[    1.602594] hub 5-0:1.0: USB hub found
[    1.602607] hub 5-0:1.0: 3 ports detected
[    1.602801] ohci-pci 0000:00:13.1: OHCI PCI host controller
[    1.602805] ohci-pci 0000:00:13.1: new USB bus registered, assigned bus number 6
[    1.602816] ohci-pci 0000:00:13.1: irq 18, io mem 0xfe9fb000
[    1.662423] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    1.662425] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.662427] usb usb6: Product: OHCI PCI host controller
[    1.662428] usb usb6: Manufacturer: Linux 3.13.0-43-generic ohci_hcd
[    1.662430] usb usb6: SerialNumber: 0000:00:13.1
[    1.662550] hub 6-0:1.0: USB hub found
[    1.662564] hub 6-0:1.0: 3 ports detected
[    1.662768] ohci-pci 0000:00:14.5: OHCI PCI host controller
[    1.662772] ohci-pci 0000:00:14.5: new USB bus registered, assigned bus number 7
[    1.662784] ohci-pci 0000:00:14.5: irq 18, io mem 0xfe9fa000
[    1.722382] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    1.722384] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.722386] usb usb7: Product: OHCI PCI host controller
[    1.722387] usb usb7: Manufacturer: Linux 3.13.0-43-generic ohci_hcd
[    1.722389] usb usb7: SerialNumber: 0000:00:14.5
[    1.722558] hub 7-0:1.0: USB hub found
[    1.722572] hub 7-0:1.0: 2 ports detected
[    1.722632] ohci-platform: OHCI generic platform driver
[    1.722640] uhci_hcd: USB Universal Host Controller Interface driver
[    1.722687] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.723063] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.723069] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.723213] mousedev: PS/2 mouse device common for all mice
[    1.723330] rtc_cmos 00:02: RTC can wake from S4
[    1.723438] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.723462] rtc_cmos 00:02: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.723515] device-mapper: uevent: version 1.0.3
[    1.723576] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    1.723582] ledtrig-cpu: registered to indicate activity on CPUs
[    1.723658] TCP: cubic registered
[    1.723734] NET: Registered protocol family 10
[    1.723885] NET: Registered protocol family 17
[    1.723890] Key type dns_resolver registered
[    1.724400] Loading compiled-in X.509 certificates
[    1.725180] Loaded X.509 cert 'Magrathea: Glacier signing key: 55ab2fe28ed5c60df9587150d1734c920ea7b818'
[    1.725187] registered taskstats version 1
[    1.727372] Key type trusted registered
[    1.729042] Key type encrypted registered
[    1.730648] AppArmor: AppArmor sha1 policy hashing enabled
[    1.730651] IMA: No TPM chip found, activating TPM-bypass!
[    1.730884] regulator-dummy: disabling
[    1.730960]   Magic number: 15:258:411
[    1.730977] pci 0000:00:18.3: hash matches
[    1.731043] rtc_cmos 00:02: setting system clock to 2015-01-08 03:24:23 UTC (1420687463)
[    1.731169] acpi-cpufreq: overriding BIOS provided _PSD data
[    1.731783] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.731784] EDD information not available.
[    1.731807] PM: Hibernation image not present or could not be loaded.
[    1.732959] Freeing unused kernel memory: 1336K (ffffffff81d20000 - ffffffff81e6e000)
[    1.732960] Write protecting the kernel read-only data: 12288k
[    1.735679] Freeing unused kernel memory: 796K (ffff880001739000 - ffff880001800000)
[    1.737911] Freeing unused kernel memory: 688K (ffff880001b54000 - ffff880001c00000)
[    1.750024] systemd-udevd[135]: starting version 204
[    1.761425] wmi: Mapper loaded
[    1.768214] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.768225] r8169 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[    1.768461] r8169 0000:02:00.0: irq 43 for MSI/MSI-X
[    1.768645] r8169 0000:02:00.0 eth0: RTL8168f/8111f at 0xffffc9000189c000, 60:a4:4c:ab:77:77, XID 08000800 IRQ 43
[    1.768649] r8169 0000:02:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    1.770102] [drm] Initialized drm 1.1.0 20060810
[    1.770208] scsi0 : pata_atiixp
[    1.770459] scsi1 : pata_atiixp
[    1.770498] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    1.770500] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    1.770543] ahci 0000:00:11.0: version 3.0
[    1.770880] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.770883] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
[    1.771419] scsi2 : ahci
[    1.771514] scsi3 : ahci
[    1.771582] scsi4 : ahci
[    1.771670] scsi5 : ahci
[    1.771729] ata3: SATA max UDMA/133 abar m1024@0xfe9ffc00 port 0xfe9ffd00 irq 22
[    1.771732] ata4: SATA max UDMA/133 abar m1024@0xfe9ffc00 port 0xfe9ffd80 irq 22
[    1.771734] ata5: SATA max UDMA/133 abar m1024@0xfe9ffc00 port 0xfe9ffe00 irq 22
[    1.771737] ata6: SATA max UDMA/133 abar m1024@0xfe9ffc00 port 0xfe9ffe80 irq 22
[    1.792878] [drm] radeon userspace modesetting enabled.
[    1.793507] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    1.793508] [drm] No driver support for vblank timestamp query.
[    1.793510] [drm] Initialized radeon 1.34.0 20080528 for 0000:01:00.0 on minor 0
[    2.090076] ata6: SATA link down (SStatus 0 SControl 300)
[    2.261914] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.261949] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.262562] ata5.00: ATA-8: ST2000DM001-1CH164, CC24, max UDMA/133
[    2.262564] ata5.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.262669] ata4.00: ATA-8: ST2000DM001-1CH164, CC24, max UDMA/133
[    2.262673] ata4.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.263256] ata5.00: configured for UDMA/133
[    2.263362] ata4.00: configured for UDMA/133
[    2.265906] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.266644] ata3.00: failed to get NCQ Send/Recv Log Emask 0x1
[    2.266646] ata3.00: ATA-9: Samsung SSD 840 Series, DXT06B0Q, max UDMA/133
[    2.266648] ata3.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.266685] ata3.00: failed to get Identify Device Data, Emask 0x1
[    2.266999] ata3.00: failed to get NCQ Send/Recv Log Emask 0x1
[    2.267039] ata3.00: failed to get Identify Device Data, Emask 0x1
[    2.267042] ata3.00: configured for UDMA/133
[    2.267177] scsi 2:0:0:0: Direct-Access     ATA      Samsung SSD 840  DXT0 PQ: 0 ANSI: 5
[    2.267319] sd 2:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    2.267330] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    2.267473] sd 2:0:0:0: [sda] Write Protect is off
[    2.267476] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.267493] scsi 3:0:0:0: Direct-Access     ATA      ST2000DM001-1CH1 CC24 PQ: 0 ANSI: 5
[    2.267514] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.267666] sd 3:0:0:0: [sdb] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    2.267667] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    2.267671] sd 3:0:0:0: [sdb] 4096-byte physical blocks
[    2.267738] sd 3:0:0:0: [sdb] Write Protect is off
[    2.267740] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.267781] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.267813] scsi 4:0:0:0: Direct-Access     ATA      ST2000DM001-1CH1 CC24 PQ: 0 ANSI: 5
[    2.267971]  sda: sda1 sda2
[    2.267989] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    2.268007] sd 4:0:0:0: [sdc] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    2.268009] sd 4:0:0:0: [sdc] 4096-byte physical blocks
[    2.268103] sd 4:0:0:0: [sdc] Write Protect is off
[    2.268105] sd 4:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    2.268144] sd 4:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.268367] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.286682]  sdb: sdb1
[    2.286990] sd 3:0:0:0: [sdb] Attached SCSI disk
[    2.287210]  sdc: sdc1
[    2.287466] sd 4:0:0:0: [sdc] Attached SCSI disk
[    2.301813] tsc: Refined TSC clocksource calibration: 3515.779 MHz
[    2.371555] md: bind<sdc1>
[    2.373148] md: bind<sdb1>
[    2.441713] raid6: sse2x1    7299 MB/s
[    2.477744] usb 4-1: new full-speed USB device number 2 using ohci-pci
[    2.509653] raid6: sse2x2   10916 MB/s
[    2.577592] raid6: sse2x4   13486 MB/s
[    2.577593] raid6: using algorithm sse2x4 (13486 MB/s)
[    2.577594] raid6: using ssse3x2 recovery algorithm
[    2.578765] xor: automatically using best checksumming function:
[    2.617556]    avx       :  5091.000 MB/sec
[    2.618662] async_tx: api initialized (async)
[    2.624681] md: raid6 personality registered for level 6
[    2.624683] md: raid5 personality registered for level 5
[    2.624684] md: raid4 personality registered for level 4
[    2.624909] md/raid:md127: device sdb1 operational as raid disk 0
[    2.624912] md/raid:md127: device sdc1 operational as raid disk 1
[    2.625151] md/raid:md127: allocated 0kB
[    2.625190] md/raid:md127: raid level 5 active with 2 out of 2 devices, algorithm 2
[    2.625191] RAID conf printout:
[    2.625192]  --- level:5 rd:2 wd:2
[    2.625193]  disk 0, o:1, dev:sdb1
[    2.625194]  disk 1, o:1, dev:sdc1
[    2.625209] md127: detected capacity change from 0 to 2000263053312
[    2.631113]  md127: unknown partition table
[    2.660595] usb 4-1: New USB device found, idVendor=0a5c, idProduct=2198
[    2.660603] usb 4-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.660609] usb 4-1: Product: Broadcom Bluetooth 3.0 Device
[    2.660615] usb 4-1: Manufacturer: Broadcom Corp
[    2.660620] usb 4-1: SerialNumber: 000272DDD0CC
[    2.953154] md: linear personality registered for level -1
[    2.955280] md: multipath personality registered for level -4
[    2.957381] md: raid0 personality registered for level 0
[    2.959761] md: raid1 personality registered for level 1
[    2.965493] md: raid10 personality registered for level 10
[    2.981203] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[    3.081078] random: init urandom read with 90 bits of entropy available
[    3.189035] usb 3-1: new full-speed USB device number 2 using ohci-pci
[    3.301094] Switched to clocksource tsc
[    3.361899] usb 3-1: New USB device found, idVendor=046d, idProduct=c52b
[    3.361903] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.361904] usb 3-1: Product: USB Receiver
[    3.361906] usb 3-1: Manufacturer: Logitech
[    3.439424] random: nonblocking pool is initialized
[    3.632615] usb 3-3: new low-speed USB device number 3 using ohci-pci
[    3.784847] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
[    3.803496] usb 3-3: New USB device found, idVendor=258a, idProduct=0001
[    3.803499] usb 3-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.803501] usb 3-3: Product: USB KEYBOARD
[    3.803502] usb 3-3: Manufacturer: SINO WEALTH
[    3.879389] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    3.972810] EXT4-fs (md127): mounted filesystem with ordered data mode. Opts: (null)
[    4.459482] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    4.518813] systemd-udevd[499]: starting version 204
[    4.565352] lp: driver loaded but no devices found
[    4.571609] ppdev: user-space parallel port driver
[    4.574052] parport_pc 00:05: reported by Plug and Play ACPI
[    4.574109] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    4.667815] lp0: using parport0 (interrupt-driven).
[    4.677266] Bluetooth: Core ver 2.17
[    4.677284] NET: Registered protocol family 31
[    4.677286] Bluetooth: HCI device and connection manager initialized
[    4.677293] Bluetooth: HCI socket layer initialized
[    4.677296] Bluetooth: L2CAP socket layer initialized
[    4.677300] Bluetooth: SCO socket layer initialized
[    4.679881] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    4.679884] Bluetooth: BNEP filters: protocol multicast
[    4.679890] Bluetooth: BNEP socket layer initialized
[    4.680317] Bluetooth: RFCOMM TTY layer initialized
[    4.680324] Bluetooth: RFCOMM socket layer initialized
[    4.680329] Bluetooth: RFCOMM ver 1.11
[    4.696947] init: cups main process (567) killed by HUP signal
[    4.696955] init: cups main process ended, respawning
[    4.733017] cfg80211: Calling CRDA to update world regulatory domain
[    4.735741] ATK0110 ATK0110:00: Overriding interface detection
[    4.761593] ACPI Warning: 0x0000000000000b00-0x0000000000000b07 SystemIO conflicts with Region \SOR1 1 (20131115/utaddress-251)
[    4.761598] ACPI Warning: 0x0000000000000b00-0x0000000000000b07 SystemIO conflicts with Region \SMRG 2 (20131115/utaddress-251)
[    4.761602] ACPI Warning: 0x0000000000000b00-0x0000000000000b07 SystemIO conflicts with Region \_SB_.PCI0.SBRG.ASOC.SMRG 3 (20131115/utaddress-251)
[    4.761605] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    4.762696] sp5100_tco: SP5100/SB800 TCO WatchDog Timer Driver v0.05
[    4.762777] sp5100_tco: PCI Revision ID: 0x3c
[    4.762798] sp5100_tco: failed to find MMIO address, giving up.
[    4.775444] MCE: In-kernel MCE decoding enabled.
[    4.777660] EDAC MC: Ver: 3.0.0
[    4.784378] AMD64 EDAC driver v3.4.0
[    4.784396] EDAC amd64: DRAM ECC disabled.
[    4.784405] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[    4.784405]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[    4.784405]  (Note that use of the override may cause unknown side effects.)
[    4.789181] usbcore: registered new interface driver btusb
[    4.844968] ath: EEPROM regdomain: 0x809c
[    4.844972] ath: EEPROM indicates we should expect a country code
[    4.844973] ath: doing EEPROM country->regdmn map search
[    4.844975] ath: country maps to regdmn code: 0x52
[    4.844976] ath: Country alpha2 being used: CN
[    4.844977] ath: Regpair used: 0x52
[    4.852202] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[    4.852538] ieee80211 phy0: Atheros AR9287 Rev:2 mem=0xffffc90011bc0000, irq=17
[    4.867312] kvm: Nested Virtualization enabled
[    4.867318] kvm: Nested Paging enabled
[    4.900830] hda-intel 0000:00:14.2: Using LPIB position fix
[    4.904683] hda-intel 0000:00:14.2: Enable sync_write for stable communication
[    4.917282] SKU: Nid=0x1d sku_cfg=0x4004c601
[    4.917285] SKU: port_connectivity=0x1
[    4.917286] SKU: enable_pcbeep=0x0
[    4.917288] SKU: check_sum=0x00000004
[    4.917290] SKU: customization=0x000000c6
[    4.917291] SKU: external_amp=0x0
[    4.917292] SKU: platform_type=0x0
[    4.917293] SKU: swap=0x0
[    4.917294] SKU: override=0x1
[    4.917763] autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:line
[    4.917765]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    4.917767]    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[    4.917768]    mono: mono_out=0x0
[    4.917769]    dig-out=0x11/0x0
[    4.917769]    inputs:
[    4.917771]      Front Mic=0x19
[    4.917772]      Rear Mic=0x18
[    4.917773]      Line=0x1a
[    4.917775] realtek: No valid SSID, checking pincfg 0x4004c601 for NID 0x1d
[    4.917776] realtek: Enabling init ASM_ID=0xc601 CODEC_ID=10ec0887
[    4.927914] hidraw: raw HID events driver (C) Jiri Kosina
[    4.933226] input: HDA ATI SB Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input9
[    4.933295] input: HDA ATI SB Line Out as /devices/pci0000:00/0000:00:14.2/sound/card0/input8
[    4.933388] input: HDA ATI SB Line as /devices/pci0000:00/0000:00:14.2/sound/card0/input7
[    4.933451] input: HDA ATI SB Rear Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input6
[    4.933537] input: HDA ATI SB Front Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input5
[    4.935696] systemd-udevd[607]: renamed network interface wlan0 to wlan2
[    4.935735] cfg80211: World regulatory domain updated:
[    4.935739] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    4.935741] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    4.935743] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    4.935744] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    4.935746] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    4.935747] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    4.935759] cfg80211: Calling CRDA for country: CN
[    4.943691] cfg80211: Regulatory domain changed to country: CN
[    4.943694] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    4.943697] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[    4.943698] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A, 3000 mBm)
[    4.943700] cfg80211:   (57240000 KHz - 59400000 KHz @ 2160000 KHz), (N/A, 2800 mBm)
[    4.943702] cfg80211:   (59400000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4400 mBm)
[    4.943704] cfg80211:   (63720000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 2800 mBm)
[    4.955585] logitech-djreceiver 0003:046D:C52B.0003: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:12.0-1/input2
[    4.960636] input: Logitech Unifying Device. Wireless PID:101b as /devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1:1.2/0003:046D:C52B.0003/input/input10
[    4.960786] logitech-djdevice 0003:046D:C52B.0004: input,hidraw1: USB HID v1.11 Mouse [Logitech Unifying Device. Wireless PID:101b] on usb-0000:00:12.0-1:1
[    4.972641] usbcore: registered new interface driver usbhid
[    4.972643] usbhid: USB HID core driver
[    4.975867] input: SINO WEALTH USB KEYBOARD as /devices/pci0000:00/0000:00:12.0/usb3/3-3/3-3:1.0/input/input11
[    4.976020] hid-generic 0003:258A:0001.0005: input,hidraw2: USB HID v1.10 Keyboard [SINO WEALTH USB KEYBOARD] on usb-0000:00:12.0-3/input0
[    4.979782] input: SINO WEALTH USB KEYBOARD as /devices/pci0000:00/0000:00:12.0/usb3/3-3/3-3:1.1/input/input12
[    4.980254] hid-generic 0003:258A:0001.0006: input,hiddev0,hidraw3: USB HID v1.10 Device [SINO WEALTH USB KEYBOARD] on usb-0000:00:12.0-3/input1
[    5.051606] init: failsafe main process (783) killed by TERM signal
[    5.465869] r8169 0000:02:00.0 eth0: link down
[    5.465910] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    5.466438] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    5.484734] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[    5.488900] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[    5.489847] init: gdm main process (1152) killed by TERM signal
[    5.566054] NET: Registered protocol family 15
[    5.677816] vboxdrv: module verification failed: signature and/or  required key missing - tainting kernel
[    5.681669] vboxdrv: Found 6 processor cores.
[    5.681939] vboxdrv: fAsync=0 offMin=0x389 offMax=0x3d3c
[    5.682025] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[    5.682026] vboxdrv: Successfully loaded version 4.3.10_Ubuntu (interface 0x001a0007).
[    5.695925] vboxpci: IOMMU not found (not registered)
[    5.925904] init: plymouth-upstart-bridge main process ended, respawning
[    5.930284] init: plymouth-upstart-bridge main process (1562) terminated with status 1
[    5.930293] init: plymouth-upstart-bridge main process ended, respawning
[    6.298702] wlan2: authenticate with 20:aa:4b:16:02:0d
[    6.317744] wlan2: send auth to 20:aa:4b:16:02:0d (try 1/3)
[    6.319725] wlan2: authenticated
[    6.322315] wlan2: associate with 20:aa:4b:16:02:0d (try 1/3)
[    6.325864] wlan2: RX AssocResp from 20:aa:4b:16:02:0d (capab=0x411 status=0 aid=4)
[    6.325903] wlan2: associated
[    6.325909] IPv6: ADDRCONF(NETDEV_CHANGE): wlan2: link becomes ready
[    6.920032] init: plymouth-stop pre-start process (2034) terminated with status 1
```

```
name of display: :0.0display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_make_current_read
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_fbconfig_float, 
    GLX_ARB_framebuffer_sRGB, GLX_ARB_get_proc_address, GLX_ARB_multisample, 
    GLX_EXT_buffer_age, GLX_EXT_create_context_es2_profile, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_INTEL_swap_event, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync
GLX version: 1.4
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_multithread_makecurrent, 
    GLX_MESA_query_renderer, GLX_OML_swap_method, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGI_make_current_read
OpenGL vendor string: VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.5, 128 bits)
OpenGL version string: 3.0 Mesa 10.5.0-devel
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:
    GL_AMD_conservative_depth, GL_AMD_draw_buffers_blend, 
    GL_AMD_seamless_cubemap_per_texture, GL_AMD_shader_trinary_minmax, 
    GL_ANGLE_texture_compression_dxt3, GL_ANGLE_texture_compression_dxt5, 
    GL_APPLE_packed_pixels, GL_APPLE_vertex_array_object, 
    GL_ARB_ES2_compatibility, GL_ARB_ES3_compatibility, GL_ARB_base_instance, 
    GL_ARB_blend_func_extended, GL_ARB_clear_buffer_object, 
    GL_ARB_clip_control, GL_ARB_color_buffer_float, 
    GL_ARB_compressed_texture_pixel_storage, 
    GL_ARB_conditional_render_inverted, GL_ARB_conservative_depth, 
    GL_ARB_copy_buffer, GL_ARB_debug_output, GL_ARB_depth_buffer_float, 
    GL_ARB_depth_clamp, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_draw_buffers_blend, GL_ARB_draw_elements_base_vertex, 
    GL_ARB_draw_instanced, GL_ARB_explicit_attrib_location, 
    GL_ARB_explicit_uniform_location, GL_ARB_fragment_coord_conventions, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_framebuffer_object, 
    GL_ARB_framebuffer_sRGB, GL_ARB_get_program_binary, 
    GL_ARB_half_float_pixel, GL_ARB_half_float_vertex, 
    GL_ARB_instanced_arrays, GL_ARB_internalformat_query, 
    GL_ARB_invalidate_subdata, GL_ARB_map_buffer_alignment, 
    GL_ARB_map_buffer_range, GL_ARB_multi_bind, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_occlusion_query2, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_provoking_vertex, GL_ARB_robustness, GL_ARB_sampler_objects, 
    GL_ARB_seamless_cube_map, GL_ARB_seamless_cubemap_per_texture, 
    GL_ARB_separate_shader_objects, GL_ARB_shader_bit_encoding, 
    GL_ARB_shader_objects, GL_ARB_shader_texture_lod, 
    GL_ARB_shading_language_100, GL_ARB_shading_language_420pack, 
    GL_ARB_shading_language_packing, GL_ARB_shadow, GL_ARB_stencil_texturing, 
    GL_ARB_sync, GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_compression_rgtc, GL_ARB_texture_cube_map, 
    GL_ARB_texture_cube_map_array, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_float, 
    GL_ARB_texture_mirror_clamp_to_edge, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_multisample, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_query_levels, GL_ARB_texture_rectangle, GL_ARB_texture_rg, 
    GL_ARB_texture_rgb10_a2ui, GL_ARB_texture_storage, 
    GL_ARB_texture_storage_multisample, GL_ARB_texture_swizzle, 
    GL_ARB_timer_query, GL_ARB_transform_feedback2, 
    GL_ARB_transform_feedback3, GL_ARB_transform_feedback_instanced, 
    GL_ARB_transpose_matrix, GL_ARB_uniform_buffer_object, 
    GL_ARB_vertex_array_bgra, GL_ARB_vertex_array_object, 
    GL_ARB_vertex_attrib_binding, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_vertex_type_10f_11f_11f_rev, GL_ARB_vertex_type_2_10_10_10_rev, 
    GL_ARB_window_pos, GL_ATI_blend_equation_separate, GL_ATI_draw_buffers, 
    GL_ATI_separate_stencil, GL_ATI_texture_compression_3dc, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_float, 
    GL_ATI_texture_mirror_once, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_copy_texture, GL_EXT_draw_buffers2, GL_EXT_draw_instanced, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_blit, 
    GL_EXT_framebuffer_multisample, GL_EXT_framebuffer_multisample_blit_scaled, 
    GL_EXT_framebuffer_object, GL_EXT_framebuffer_sRGB, 
    GL_EXT_gpu_program_parameters, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_float, GL_EXT_packed_pixels, 
    GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_provoking_vertex, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_shader_integer_mix, GL_EXT_shadow_funcs, GL_EXT_stencil_two_side, 
    GL_EXT_stencil_wrap, GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_array, GL_EXT_texture_compression_dxt1, 
    GL_EXT_texture_compression_latc, GL_EXT_texture_compression_rgtc, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_integer, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, GL_EXT_texture_sRGB_decode, 
    GL_EXT_texture_shared_exponent, GL_EXT_texture_snorm, 
    GL_EXT_texture_swizzle, GL_EXT_timer_query, GL_EXT_transform_feedback, 
    GL_EXT_vertex_array, GL_EXT_vertex_array_bgra, 
    GL_IBM_multimode_draw_arrays, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_KHR_context_flush_control, GL_KHR_debug, GL_MESA_pack_invert, 
    GL_MESA_texture_signed_rgba, GL_MESA_window_pos, GL_MESA_ycbcr_texture, 
    GL_NV_blend_square, GL_NV_conditional_render, GL_NV_depth_clamp, 
    GL_NV_fog_distance, GL_NV_light_max_exponent, GL_NV_packed_depth_stencil, 
    GL_NV_primitive_restart, GL_NV_texgen_reflection, 
    GL_NV_texture_env_combine4, GL_NV_texture_rectangle, GL_OES_EGL_image, 
    GL_OES_read_format, GL_S3_s3tc, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays


120 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0f6 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0f7 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0f8 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0f9 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0fa 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0fb 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0fc 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x0fd 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x0fe 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x0ff 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x100 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x101 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x102 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x103 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x104 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x105 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x106 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x107 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x108 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x109 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x10a 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x10b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x10c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x10d 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x10e 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x10f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x110 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x111 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x112 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x113 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x114 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x115 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x116 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x117 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x118 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x119 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x11a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x11b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x11c 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x11d 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x11e 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x11f 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x120 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x121 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x122 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x123 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x124 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x125 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x126 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x127 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x128 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x129 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x12a 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x12b 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x12c 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x12d 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x12e 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x12f 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x130 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x131 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x132 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x133 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x134 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x135 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x136 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x137 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x138 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x139 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x13a 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x13b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x13c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x13d 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x13e 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x13f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x140 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x141 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x142 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x143 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x144 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x145 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x146 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x147 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x148 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x149 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x14a 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x14b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x14c 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x14d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x14e 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x14f 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x150 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x151 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x152 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x153 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x154 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x155 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x156 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x157 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x158 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x159 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x15a 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x15b 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x15c 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x15d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x15e 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x15f 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x160 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x161 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x162 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x163 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x164 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x165 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x166 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x167 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x168 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x169 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x16a 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x16b 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x041 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None


180 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x042 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x043 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x044 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x045 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x046 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x047 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x048 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x049 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x04a 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x04b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x04c 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x04d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x04e 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x04f 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x050 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x051 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x052 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x053 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x054 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x055 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x056 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x057 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x058 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x059 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x05a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x05b 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x05c 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x05d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x05e 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x05f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x060 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x061 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x062 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x063 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x064 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x065 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x066 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x067 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x068 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x069 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x06a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x06b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x06c 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x06d 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x06e 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x06f 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x070 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x071 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x072 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x073 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x074 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x075 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x076 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x077 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x078 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x079 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x07a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x07b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x07c 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x07d 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x07e  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07f  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x080  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x081  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x082  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x083  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x084  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x085  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x086  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x087  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x088  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x089  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x08a  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x08b  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x08c  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x08d  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x08e  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x08f  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x090  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x091  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x092  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x093  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x094  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x095  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x096  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 32  0  0  0  0  0  0 0 None
0x097  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x098  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 32  0  0  0  0  0  0 0 None
0x099  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x09a  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 32  0  0  0  0  0  0 0 None
0x09b  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x09c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x09d 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x09e 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x09f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0a0 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a1 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0a2 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x0a3 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x0a4 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x0a5 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x0a6 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x0a7 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x0a8 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0a9 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0aa 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0ab 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0ac 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0ad 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0ae 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0af 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0b0 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0b1 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0b2 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0b3 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0b4 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x0b5 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x0b6 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x0b7 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x0b8 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x0b9 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x0ba 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0bb 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0bc 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0bd 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0be 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0bf 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0c0 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0c1 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0c2 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0c3 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0c4 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0c5 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0c6 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0c7 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0c8 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0c9 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0ca 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0cb 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0cc 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0cd 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0ce 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0cf 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0d0 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0d1 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0d2 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x0d3 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x0d4 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x0d5 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x0d6 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x0d7 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x0d8  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0d9  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0da  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0db  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0dc  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0dd  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0de  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0df  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0e0  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0e1  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0e2  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0e3  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0e4  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0e5  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0e6  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0e7  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0e8  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0e9  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0ea  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0eb  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0ec  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0ed  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0ee  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0ef  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0f0  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 32  0  0  0  0  0  0 0 None
0x0f1  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x0f2  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 32  0  0  0  0  0  0 0 None
0x0f3  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x0f4  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 32  0  0  0  0  0  0 0 None
0x0f5  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 32  0 16 16 16  0  0 0 Slow



```

```
OpenGL vendor string:   VMware, Inc.OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.5, 128 bits)
OpenGL version string:  3.0 Mesa 10.5.0-devel


Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes


Unity 3D supported:       no



```

```
[     5.714] X.Org X Server 1.15.1
Release Date: 2014-04-13
[     5.714] X Protocol Version 11, Revision 0
[     5.714] Build Operating System: Linux 3.2.0-70-generic x86_64 Ubuntu
[     5.714] Current Operating System: Linux desktop 3.13.0-43-generic #72-Ubuntu SMP Mon Dec 8 19:35:06 UTC 2014 x86_64
[     5.714] Kernel command line: BOOT_IMAGE=/vmlinuz-3.13.0-43-generic root=UUID=af35895a-fc9e-4d61-b4f4-d24e6c2b3acf ro quiet splash nomdmonddf nomdmonisw nomdmonddf nomdmonisw vt.handoff=7
[     5.714] Build Date: 10 December 2014  06:15:52PM
[     5.714] xorg-server 2:1.15.1-0ubuntu2.6 (For technical support please see http://www.ubuntu.com/support) 
[     5.714] Current version of pixman: 0.30.2
[     5.714]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[     5.714] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     5.714] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Jan  7 22:24:27 2015
[     5.715] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     5.715] (==) No Layout section.  Using the first Screen section.
[     5.715] (==) No screen section available. Using defaults.
[     5.715] (**) |-->Screen "Default Screen Section" (0)
[     5.715] (**) |   |-->Monitor "<default monitor>"
[     5.715] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[     5.715] (==) Automatically adding devices
[     5.715] (==) Automatically enabling devices
[     5.715] (==) Automatically adding GPU devices
[     5.715] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     5.715]     Entry deleted from font path.
[     5.715] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     5.715]     Entry deleted from font path.
[     5.715] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     5.715]     Entry deleted from font path.
[     5.715] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     5.715]     Entry deleted from font path.
[     5.715] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     5.715]     Entry deleted from font path.
[     5.715] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[     5.715] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     5.715] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[     5.715] (II) Loader magic: 0x7f5b1cf85d40
[     5.715] (II) Module ABI versions:
[     5.715]     X.Org ANSI C Emulation: 0.4
[     5.715]     X.Org Video Driver: 15.0
[     5.715]     X.Org XInput driver : 20.0
[     5.715]     X.Org Server Extension : 8.0
[     5.715] (II) xfree86: Adding drm device (/dev/dri/card0)
[     5.717] (--) PCI:*(0:1:0:0) 1002:7146:107b:3a11 rev 0, Mem @ 0xd0000000/268435456, 0xfeae0000/65536, I/O @ 0x0000d000/256, BIOS @ 0x????????/131072
[     5.717] (--) PCI: (0:1:0:1) 1002:7166:107b:3a10 rev 0, Mem @ 0xfeab0000/65536
[     5.717] Initializing built-in extension Generic Event Extension
[     5.717] Initializing built-in extension SHAPE
[     5.717] Initializing built-in extension MIT-SHM
[     5.717] Initializing built-in extension XInputExtension
[     5.717] Initializing built-in extension XTEST
[     5.717] Initializing built-in extension BIG-REQUESTS
[     5.717] Initializing built-in extension SYNC
[     5.717] Initializing built-in extension XKEYBOARD
[     5.717] Initializing built-in extension XC-MISC
[     5.717] Initializing built-in extension SECURITY
[     5.717] Initializing built-in extension XINERAMA
[     5.717] Initializing built-in extension XFIXES
[     5.717] Initializing built-in extension RENDER
[     5.717] Initializing built-in extension RANDR
[     5.717] Initializing built-in extension COMPOSITE
[     5.717] Initializing built-in extension DAMAGE
[     5.717] Initializing built-in extension MIT-SCREEN-SAVER
[     5.717] Initializing built-in extension DOUBLE-BUFFER
[     5.717] Initializing built-in extension RECORD
[     5.717] Initializing built-in extension DPMS
[     5.717] Initializing built-in extension Present
[     5.717] Initializing built-in extension DRI3
[     5.717] Initializing built-in extension X-Resource
[     5.717] Initializing built-in extension XVideo
[     5.717] Initializing built-in extension XVideo-MotionCompensation
[     5.717] Initializing built-in extension SELinux
[     5.717] Initializing built-in extension XFree86-VidModeExtension
[     5.717] Initializing built-in extension XFree86-DGA
[     5.717] Initializing built-in extension XFree86-DRI
[     5.717] Initializing built-in extension DRI2
[     5.717] (II) LoadModule: "glx"
[     5.719] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[     5.733] (II) Module glx: vendor="X.Org Foundation"
[     5.733]     compiled for 1.15.1, module version = 1.0.0
[     5.733]     ABI class: X.Org Server Extension, version 8.0
[     5.733] (==) AIGLX enabled
[     5.733] Loading extension GLX
[     5.733] (==) Matched fglrx as autoconfigured driver 0
[     5.733] (==) Matched ati as autoconfigured driver 1
[     5.733] (==) Matched fglrx as autoconfigured driver 2
[     5.733] (==) Matched ati as autoconfigured driver 3
[     5.733] (==) Matched modesetting as autoconfigured driver 4
[     5.733] (==) Matched fbdev as autoconfigured driver 5
[     5.733] (==) Matched vesa as autoconfigured driver 6
[     5.733] (==) Assigned the driver to the xf86ConfigLayout
[     5.733] (II) LoadModule: "fglrx"
[     5.733] (WW) Warning, couldn't open module fglrx
[     5.733] (II) UnloadModule: "fglrx"
[     5.733] (II) Unloading fglrx
[     5.733] (EE) Failed to load module "fglrx" (module does not exist, 0)
[     5.733] (II) LoadModule: "ati"
[     5.733] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[     5.733] (II) Module ati: vendor="X.Org Foundation"
[     5.733]     compiled for 1.15.1, module version = 7.4.99
[     5.733]     Module class: X.Org Video Driver
[     5.733]     ABI class: X.Org Video Driver, version 15.0
[     5.733] (II) LoadModule: "radeon"
[     5.734] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[     5.735] (II) Module radeon: vendor="X.Org Foundation"
[     5.735]     compiled for 1.15.1, module version = 7.4.99
[     5.735]     Module class: X.Org Video Driver
[     5.735]     ABI class: X.Org Video Driver, version 15.0
[     5.735] (II) LoadModule: "modesetting"
[     5.735] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     5.735] (II) Module modesetting: vendor="X.Org Foundation"
[     5.735]     compiled for 1.15.0, module version = 0.8.1
[     5.735]     Module class: X.Org Video Driver
[     5.735]     ABI class: X.Org Video Driver, version 15.0
[     5.735] (II) LoadModule: "fbdev"
[     5.736] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     5.736] (II) Module fbdev: vendor="X.Org Foundation"
[     5.736]     compiled for 1.15.0, module version = 0.4.4
[     5.736]     Module class: X.Org Video Driver
[     5.736]     ABI class: X.Org Video Driver, version 15.0
[     5.736] (II) LoadModule: "vesa"
[     5.736] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     5.736] (II) Module vesa: vendor="X.Org Foundation"
[     5.736]     compiled for 1.15.0, module version = 2.3.3
[     5.736]     Module class: X.Org Video Driver
[     5.736]     ABI class: X.Org Video Driver, version 15.0
[     5.736] (==) Matched fglrx as autoconfigured driver 0
[     5.736] (==) Matched ati as autoconfigured driver 1
[     5.736] (==) Matched fglrx as autoconfigured driver 2
[     5.736] (==) Matched ati as autoconfigured driver 3
[     5.736] (==) Matched modesetting as autoconfigured driver 4
[     5.736] (==) Matched fbdev as autoconfigured driver 5
[     5.736] (==) Matched vesa as autoconfigured driver 6
[     5.736] (==) Assigned the driver to the xf86ConfigLayout
[     5.736] (II) LoadModule: "fglrx"
[     5.736] (WW) Warning, couldn't open module fglrx
[     5.736] (II) UnloadModule: "fglrx"
[     5.736] (II) Unloading fglrx
[     5.736] (EE) Failed to load module "fglrx" (module does not exist, 0)
[     5.736] (II) LoadModule: "ati"
[     5.737] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[     5.737] (II) Module ati: vendor="X.Org Foundation"
[     5.737]     compiled for 1.15.1, module version = 7.4.99
[     5.737]     Module class: X.Org Video Driver
[     5.737]     ABI class: X.Org Video Driver, version 15.0
[     5.737] (II) LoadModule: "modesetting"
[     5.737] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     5.737] (II) Module modesetting: vendor="X.Org Foundation"
[     5.737]     compiled for 1.15.0, module version = 0.8.1
[     5.737]     Module class: X.Org Video Driver
[     5.737]     ABI class: X.Org Video Driver, version 15.0
[     5.737] (II) UnloadModule: "modesetting"
[     5.737] (II) Unloading modesetting
[     5.737] (II) Failed to load module "modesetting" (already loaded, 0)
[     5.737] (II) LoadModule: "fbdev"
[     5.737] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     5.737] (II) Module fbdev: vendor="X.Org Foundation"
[     5.737]     compiled for 1.15.0, module version = 0.4.4
[     5.737]     Module class: X.Org Video Driver
[     5.737]     ABI class: X.Org Video Driver, version 15.0
[     5.737] (II) UnloadModule: "fbdev"
[     5.737] (II) Unloading fbdev
[     5.737] (II) Failed to load module "fbdev" (already loaded, 0)
[     5.737] (II) LoadModule: "vesa"
[     5.737] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     5.737] (II) Module vesa: vendor="X.Org Foundation"
[     5.737]     compiled for 1.15.0, module version = 2.3.3
[     5.737]     Module class: X.Org Video Driver
[     5.737]     ABI class: X.Org Video Driver, version 15.0
[     5.737] (II) UnloadModule: "vesa"
[     5.737] (II) Unloading vesa
[     5.737] (II) Failed to load module "vesa" (already loaded, 0)
[     5.737] (II) RADEON: Driver for ATI Radeon chipsets:
    ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
    ATI Radeon Mobility X300 (M24) 3152 (PCIE),
    ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
    ATI Radeon X600 (RV380) 3E50 (PCIE),
    ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
    ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
    ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
    ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
    ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
    ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
    ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
    ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
    ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
    ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
    ATI Radeon IGP330M/340M/350M (U2) 4337,
    ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
    ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
    ATI Radeon X800PRO (R420) JI (AGP),
    ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
    ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
    ATI Radeon Mobility 9800 (M18) JN (AGP),
    ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
    ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
    ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
    ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
    ATI Radeon Mobility M7 LW (AGP),
    ATI Mobility FireGL 7800 M7 LX (AGP),
    ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
    ATI FireGL Mobility 9000 (M9) Ld (AGP),
    ATI Radeon Mobility 9000 (M9) Lf (AGP),
    ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI FireMV 2400 PCI,
    ATI Radeon 9700 Pro ND (AGP), ATI Radeon 9700/9500Pro NE (AGP),
    ATI Radeon 9600TX NF (AGP), ATI FireGL X1 NG (AGP),
    ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
    ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
    ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
    ATI Radeon Mobility 9600 (M10) NQ (AGP),
    ATI Radeon Mobility 9600 (M11) NR (AGP),
    ATI Radeon Mobility 9600 (M10) NS (AGP),
    ATI FireGL Mobility T2 (M10) NT (AGP),
    ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
    ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
    ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
    ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
    ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
    ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
    ATI Radeon Mobility X300 (M22) 5460 (PCIE),
    ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
    ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
    ATI Radeon X800PRO (R423) UI (PCIE),
    ATI Radeon X800LE (R423) UJ (PCIE),
    ATI Radeon X800SE (R423) UK (PCIE),
    ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
    ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
    ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
    ATI FireGL unknown (R423) UR (PCIE),
    ATI FireGL unknown (R423) UT (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility Radeon X700 XL (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
    ATI Radeon Mobility 9100 IGP (U3) 5835,
    ATI Radeon XPRESS 200 5954 (PCIE),
    ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
    ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
    ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
    ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
    ATI Radeon XPRESS 200M 5975 (PCIE),
    ATI Radeon XPRESS 200 5A41 (PCIE),
    ATI Radeon XPRESS 200M 5A42 (PCIE),
    ATI Radeon XPRESS 200 5A61 (PCIE),
    ATI Radeon XPRESS 200M 5A62 (PCIE),
    ATI Radeon X300 (RV370) 5B60 (PCIE),
    ATI Radeon X600 (RV370) 5B62 (PCIE),
    ATI Radeon X550 (RV370) 5B63 (PCIE),
    ATI FireGL V3100 (RV370) 5B64 (PCIE),
    ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
    ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
    ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
    ATI Mobility Radeon X800 XT (M28) (PCIE),
    ATI Mobility FireGL V5100 (M28) (PCIE),
    ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
    ATI Radeon X850 XT PE (R480) (PCIE),
    ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
    ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
    ATI Radeon X850 XT (R480) (PCIE),
    ATI Radeon X800XT (R423) 5D57 (PCIE),
    ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
    ATI Radeon X700 PRO (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
    ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
    ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
    ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
    ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
    ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
    ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
    ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
    ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
    ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
    ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
    ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
    ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
    ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
    ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
    ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
    ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
    ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
    ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
    ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
    ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
    ATI Mobility Radeon X1700, ATI Radeon X2300HD,
    ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
    ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
    ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
    ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
    ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
    ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
    ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
    ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
    ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
    ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
    ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
    ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
    ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
    ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
    ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
    ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
    AMD FireStream 9250, ATI FirePro V8700 (FireGL),
    ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
    ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
    ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
    ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
    ATI Mobility Radeon HD 4670, ATI FirePro M5750,
    ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
    ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
    ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
    ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
    ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
    ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
    ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
    ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
    ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
    ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
    ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
    ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
    ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
    ATI Mobility Radeon HD 3850 X2, ATI RV670,
    ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
    ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
    ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
    ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
    ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
    ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
    ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
    ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
    ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
    ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
    ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
    ATI FireGL V3600, ATI Radeon HD 2600 LE,
    ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
    ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
    ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
    ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
    ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
    ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
    ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
    ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
    ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
    ATI Radeon 3000 Graphics, SUMO, SUMO, SUMO2, SUMO2, SUMO2, SUMO2,
    SUMO, SUMO, SUMO2, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
    ATI Radeon 4100, ATI Mobility Radeon HD 4200,
    ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
    AMD Radeon HD 6310 Graphics, AMD Radeon HD 6310 Graphics,
    AMD Radeon HD 6250 Graphics, AMD Radeon HD 6250 Graphics,
    AMD Radeon HD 6300 Series Graphics,
    AMD Radeon HD 6200 Series Graphics, PALM, PALM, PALM, CYPRESS,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
    AMD Firestream 9350, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5900 Series,
    ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
    ATI Mobility Radeon HD 5800 Series,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
    ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
    ATI Mobility Radeon Graphics, CEDAR,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
    ATI Radeon HD 5450, CEDAR, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
    CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
    AMD Radeon HD 6900 Series, AMD Radeon HD 6900 Series, CAYMAN, CAYMAN,
    CAYMAN, AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series,
    BARTS, BARTS, Mobility Radeon HD 6000 Series,
    Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
    AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
    AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, TAHITI, TAHITI, TAHITI, TAHITI,
    TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI,
    TAHITI, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
    PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
    VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
    VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
    VERDE, VERDE, VERDE, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND,
    OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, HAINAN, HAINAN, HAINAN,
    HAINAN, HAINAN, HAINAN, BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE,
    BONAIRE, BONAIRE, BONAIRE, KABINI, KABINI, KABINI, KABINI, KABINI,
    KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI,
    KABINI, KABINI, KABINI, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS,
    MULLINS, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS,
    MULLINS, MULLINS, MULLINS, MULLINS, KAVERI, KAVERI, KAVERI, KAVERI,
    KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    KAVERI, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII,
    HAWAII, HAWAII, HAWAII, HAWAII, HAWAII
[     5.746] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     5.747] (II) FBDEV: driver for framebuffer: fbdev
[     5.747] (II) VESA: driver for VESA chipsets: vesa
[     5.747] (++) using VT number 7


[     5.747] (II) [KMS] drm report modesetting isn't supported.
[     5.747] (II) [KMS] drm report modesetting isn't supported.
[     5.747] (II) [KMS] drm report modesetting isn't supported.
[     5.747] (II) [KMS] drm report modesetting isn't supported.
[     5.747] (II) [KMS] drm report modesetting isn't supported.
[     5.747] (WW) Falling back to old probe method for modesetting
[     5.747] (II) Loading sub module "fbdevhw"
[     5.747] (II) LoadModule: "fbdevhw"
[     5.747] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     5.747] (II) Module fbdevhw: vendor="X.Org Foundation"
[     5.747]     compiled for 1.15.1, module version = 0.0.2
[     5.747]     ABI class: X.Org Video Driver, version 15.0
[     5.747] (**) FBDEV(6): claimed PCI slot 1@0:0:0
[     5.747] (II) FBDEV(6): using default device
[     5.747] (WW) Falling back to old probe method for vesa
[     5.748] (EE) Screen 0 deleted because of no matching config section.
[     5.748] (II) UnloadModule: "radeon"
[     5.748] (EE) Screen 0 deleted because of no matching config section.
[     5.748] (II) UnloadModule: "radeon"
[     5.748] (EE) Screen 0 deleted because of no matching config section.
[     5.748] (II) UnloadModule: "radeon"
[     5.748] (EE) Screen 0 deleted because of no matching config section.
[     5.748] (II) UnloadModule: "radeon"
[     5.748] (EE) Screen 0 deleted because of no matching config section.
[     5.748] (II) UnloadModule: "modesetting"
[     5.748] (EE) Screen 0 deleted because of no matching config section.
[     5.748] (II) UnloadModule: "modesetting"
[     5.748] (II) FBDEV(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[     5.748] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[     5.748] (==) FBDEV(0): RGB weight 888
[     5.748] (==) FBDEV(0): Default visual is TrueColor
[     5.748] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[     5.748] (II) FBDEV(0): hardware: VESA VGA (video memory: 5120kB)
[     5.748] (II) FBDEV(0): checking modes against framebuffer device...
[     5.748] (II) FBDEV(0): checking modes against monitor...
[     5.748] (--) FBDEV(0): Virtual size is 1280x1024 (pitch 1280)
[     5.748] (**) FBDEV(0):  Built-in mode "current": 131.1 MHz, 80.3 kHz, 76.6 Hz
[     5.748] (II) FBDEV(0): Modeline "current"x0.0  131.09  1280 1312 1472 1632  1024 1028 1032 1048 -hsync -vsync -csync (80.3 kHz b)
[     5.748] (==) FBDEV(0): DPI set to (96, 96)
[     5.748] (II) Loading sub module "fb"
[     5.748] (II) LoadModule: "fb"
[     5.748] (II) Loading /usr/lib/xorg/modules/libfb.so
[     5.748] (II) Module fb: vendor="X.Org Foundation"
[     5.748]     compiled for 1.15.1, module version = 1.0.0
[     5.748]     ABI class: X.Org ANSI C Emulation, version 0.4
[     5.748] (**) FBDEV(0): using shadow framebuffer
[     5.748] (II) Loading sub module "shadow"
[     5.748] (II) LoadModule: "shadow"
[     5.748] (II) Loading /usr/lib/xorg/modules/libshadow.so
[     5.749] (II) Module shadow: vendor="X.Org Foundation"
[     5.749]     compiled for 1.15.1, module version = 1.1.0
[     5.749]     ABI class: X.Org ANSI C Emulation, version 0.4
[     5.749] (II) UnloadModule: "radeon"
[     5.749] (II) UnloadModule: "vesa"
[     5.749] (II) Unloading vesa
[     5.749] (==) Depth 24 pixmap format is 32 bpp
[     5.749] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[     5.749] (==) FBDEV(0): Backing store enabled
[     5.749] (==) FBDEV(0): DPMS enabled
[     5.749] (==) RandR enabled
[     5.754] (II) SELinux: Disabled on system
[     5.755] (II) AIGLX: Screen 0 is not DRI2 capable
[     5.755] (EE) AIGLX: reverting to software rendering
[     5.770] (II) AIGLX: Loaded and initialized swrast
[     5.770] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[     5.779] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     5.781] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     5.781] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     5.781] (II) LoadModule: "evdev"
[     5.782] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     5.786] (II) Module evdev: vendor="X.Org Foundation"
[     5.786]     compiled for 1.15.0, module version = 2.8.2
[     5.786]     Module class: X.Org XInput Driver
[     5.786]     ABI class: X.Org XInput driver, version 20.0
[     5.786] (II) Using input driver 'evdev' for 'Power Button'
[     5.786] (**) Power Button: always reports core events
[     5.786] (**) evdev: Power Button: Device: "/dev/input/event1"
[     5.786] (--) evdev: Power Button: Vendor 0 Product 0x1
[     5.786] (--) evdev: Power Button: Found keys
[     5.786] (II) evdev: Power Button: Configuring as keyboard
[     5.786] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[     5.786] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     5.786] (**) Option "xkb_rules" "evdev"
[     5.786] (**) Option "xkb_model" "pc105"
[     5.786] (**) Option "xkb_layout" "us"
[     5.786] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     5.786] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     5.786] (II) Using input driver 'evdev' for 'Power Button'
[     5.786] (**) Power Button: always reports core events
[     5.786] (**) evdev: Power Button: Device: "/dev/input/event0"
[     5.786] (--) evdev: Power Button: Vendor 0 Product 0x1
[     5.786] (--) evdev: Power Button: Found keys
[     5.786] (II) evdev: Power Button: Configuring as keyboard
[     5.786] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[     5.786] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[     5.786] (**) Option "xkb_rules" "evdev"
[     5.786] (**) Option "xkb_model" "pc105"
[     5.786] (**) Option "xkb_layout" "us"
[     5.787] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:02.0/0000:01:00.0/drm/card0
[     5.787] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[     5.787] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:101b (/dev/input/event7)
[     5.787] (**) Logitech Unifying Device. Wireless PID:101b: Applying InputClass "evdev pointer catchall"
[     5.787] (II) Using input driver 'evdev' for 'Logitech Unifying Device. Wireless PID:101b'
[     5.787] (**) Logitech Unifying Device. Wireless PID:101b: always reports core events
[     5.787] (**) evdev: Logitech Unifying Device. Wireless PID:101b: Device: "/dev/input/event7"
[     5.787] (--) evdev: Logitech Unifying Device. Wireless PID:101b: Vendor 0x46d Product 0xc52b
[     5.787] (--) evdev: Logitech Unifying Device. Wireless PID:101b: Found 20 mouse buttons
[     5.787] (--) evdev: Logitech Unifying Device. Wireless PID:101b: Found scroll wheel(s)
[     5.787] (--) evdev: Logitech Unifying Device. Wireless PID:101b: Found relative axes
[     5.787] (--) evdev: Logitech Unifying Device. Wireless PID:101b: Found x and y relative axes
[     5.787] (II) evdev: Logitech Unifying Device. Wireless PID:101b: Configuring as mouse
[     5.787] (II) evdev: Logitech Unifying Device. Wireless PID:101b: Adding scrollwheel support
[     5.787] (**) evdev: Logitech Unifying Device. Wireless PID:101b: YAxisMapping: buttons 4 and 5
[     5.787] (**) evdev: Logitech Unifying Device. Wireless PID:101b: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     5.787] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1:1.2/0003:046D:C52B.0003/input/input10/event7"
[     5.787] (II) XINPUT: Adding extended input device "Logitech Unifying Device. Wireless PID:101b" (type: MOUSE, id 8)
[     5.787] (II) evdev: Logitech Unifying Device. Wireless PID:101b: initialized for relative axes.
[     5.787] (**) Logitech Unifying Device. Wireless PID:101b: (accel) keeping acceleration scheme 1
[     5.787] (**) Logitech Unifying Device. Wireless PID:101b: (accel) acceleration profile 0
[     5.787] (**) Logitech Unifying Device. Wireless PID:101b: (accel) acceleration factor: 2.000
[     5.787] (**) Logitech Unifying Device. Wireless PID:101b: (accel) acceleration threshold: 4
[     5.787] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:101b (/dev/input/mouse0)
[     5.787] (II) No input driver specified, ignoring this device.
[     5.787] (II) This device may have been added with another device file.
[     5.788] (II) config/udev: Adding input device SINO WEALTH USB KEYBOARD (/dev/input/event8)
[     5.788] (**) SINO WEALTH USB KEYBOARD: Applying InputClass "evdev keyboard catchall"
[     5.788] (II) Using input driver 'evdev' for 'SINO WEALTH USB KEYBOARD'
[     5.788] (**) SINO WEALTH USB KEYBOARD: always reports core events
[     5.788] (**) evdev: SINO WEALTH USB KEYBOARD: Device: "/dev/input/event8"
[     5.788] (--) evdev: SINO WEALTH USB KEYBOARD: Vendor 0x258a Product 0x1
[     5.788] (--) evdev: SINO WEALTH USB KEYBOARD: Found keys
[     5.788] (II) evdev: SINO WEALTH USB KEYBOARD: Configuring as keyboard
[     5.788] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb3/3-3/3-3:1.0/input/input11/event8"
[     5.788] (II) XINPUT: Adding extended input device "SINO WEALTH USB KEYBOARD" (type: KEYBOARD, id 9)
[     5.788] (**) Option "xkb_rules" "evdev"
[     5.788] (**) Option "xkb_model" "pc105"
[     5.788] (**) Option "xkb_layout" "us"
[     5.788] (II) config/udev: Adding input device SINO WEALTH USB KEYBOARD (/dev/input/event9)
[     5.788] (**) SINO WEALTH USB KEYBOARD: Applying InputClass "evdev keyboard catchall"
[     5.788] (II) Using input driver 'evdev' for 'SINO WEALTH USB KEYBOARD'
[     5.788] (**) SINO WEALTH USB KEYBOARD: always reports core events
[     5.788] (**) evdev: SINO WEALTH USB KEYBOARD: Device: "/dev/input/event9"
[     5.788] (--) evdev: SINO WEALTH USB KEYBOARD: Vendor 0x258a Product 0x1
[     5.788] (--) evdev: SINO WEALTH USB KEYBOARD: Found keys
[     5.788] (II) evdev: SINO WEALTH USB KEYBOARD: Configuring as keyboard
[     5.788] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb3/3-3/3-3:1.1/input/input12/event9"
[     5.788] (II) XINPUT: Adding extended input device "SINO WEALTH USB KEYBOARD" (type: KEYBOARD, id 10)
[     5.788] (**) Option "xkb_rules" "evdev"
[     5.788] (**) Option "xkb_model" "pc105"
[     5.788] (**) Option "xkb_layout" "us"
[     5.789] (II) config/udev: Adding input device HDA ATI SB Front Mic (/dev/input/event6)
[     5.789] (II) No input driver specified, ignoring this device.
[     5.789] (II) This device may have been added with another device file.
[     5.789] (II) config/udev: Adding input device HDA ATI SB Rear Mic (/dev/input/event5)
[     5.789] (II) No input driver specified, ignoring this device.
[     5.789] (II) This device may have been added with another device file.
[     5.789] (II) config/udev: Adding input device HDA ATI SB Line (/dev/input/event4)
[     5.789] (II) No input driver specified, ignoring this device.
[     5.789] (II) This device may have been added with another device file.
[     5.789] (II) config/udev: Adding input device HDA ATI SB Line Out (/dev/input/event3)
[     5.789] (II) No input driver specified, ignoring this device.
[     5.789] (II) This device may have been added with another device file.
[     5.789] (II) config/udev: Adding input device HDA ATI SB Front Headphone (/dev/input/event2)
[     5.789] (II) No input driver specified, ignoring this device.
[     5.789] (II) This device may have been added with another device file.
[     5.793] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[    13.339] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    13.652] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[    13.682] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    13.685] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[    13.688] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[    13.690] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[    13.693] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[    13.693] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    13.699] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[    13.702] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[    13.704] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[    13.707] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[    13.709] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[    13.711] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[    13.713] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[    13.715] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
```

---

