---
title: "SSD error on boot"
date: 2014-07-09
forum: Hardware
---

### Post by leonixyz on 2014-07-09
My laptop is a Sony Vaio vpcyb15al with an AMD E-350 Processor × 2.
I substituted my disk with an Samsung SSD 840 EVO 120GB (EXT0BB6Q).

I run a fresh Ubuntu 14.04 Trusty Tahr installation, done with the newest iso.
When my system boots the screen is full of error messages.
This is the output of dmesg. Any help is appreciated.

First error seems to be at [COLOR=#000000][FONT=Ubuntu Mono]3.308356[/FONT][/COLOR]

```
[    0.000000] Initializing cgroup subsys cpuset[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-30-generic (buildd@kissel) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #55-Ubuntu SMP Fri Jul 4 21:40:53 UTC 2014 (Ubuntu 3.13.0-30.55-generic 3.13.11.2)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-30-generic root=UUID=293807a0-018c-454f-ae3a-f195b67cf838 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000006567ffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000065680000-0x000000006587ffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x0000000065880000-0x0000000066d3efff] usable
[    0.000000] BIOS-e820: [mem 0x0000000066d3f000-0x0000000066dbefff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000066dbf000-0x0000000066ebefff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x0000000066ebf000-0x0000000066ef5fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x0000000066ef6000-0x0000000066efffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000066f00000-0x000000007effffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec10000-0x00000000fec10fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffe00000-0x00000000ffffffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: Sony Corporation VPCYB15AL/VAIO, BIOS R0162Z7 09/13/2011
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x66f00 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-through
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FC0000000 write-back
[    0.000000]   1 base 040000000 mask FE0000000 write-back
[    0.000000]   2 base 060000000 mask FF8000000 write-back
[    0.000000]   3 base 066EBD000 mask FFFFFF000 uncachable
[    0.000000]   4 base 0FFE00000 mask FFFE00000 write-protect
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [mem 0x000fe1b0-0x000fe1bf] mapped at [ffff8800000fe1b0]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fde000, 0x01fdefff] PGTABLE
[    0.000000] BRK [0x01fdf000, 0x01fdffff] PGTABLE
[    0.000000] BRK [0x01fe0000, 0x01fe0fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x66a00000-0x66bfffff]
[    0.000000]  [mem 0x66a00000-0x66bfffff] page 2M
[    0.000000] BRK [0x01fe1000, 0x01fe1fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x64000000-0x6567ffff]
[    0.000000]  [mem 0x64000000-0x655fffff] page 2M
[    0.000000]  [mem 0x65600000-0x6567ffff] page 4k
[    0.000000] BRK [0x01fe2000, 0x01fe2fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x65880000-0x669fffff]
[    0.000000]  [mem 0x65880000-0x659fffff] page 4k
[    0.000000]  [mem 0x65a00000-0x669fffff] page 2M
[    0.000000] BRK [0x01fe3000, 0x01fe3fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x00100000-0x63ffffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x63ffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x66c00000-0x66d3efff]
[    0.000000]  [mem 0x66c00000-0x66d3efff] page 4k
[    0.000000] init_memory_mapping: [mem 0x66ef6000-0x66efffff]
[    0.000000]  [mem 0x66ef6000-0x66efffff] page 4k
[    0.000000] RAMDISK: [mem 0x35b68000-0x36dabfff]
[    0.000000] ACPI: RSDP 00000000000fe020 000024 (v02   Sony)
[    0.000000] ACPI: XSDT 0000000066ef5120 000064 (v01   Sony     VAIO 20110913      01000013)
[    0.000000] ACPI: FACP 0000000066ef4000 0000F4 (v04   Sony     VAIO 20110913 ACPI 00040000)
[    0.000000] ACPI: DSDT 0000000066ee8000 00802A (v01   Sony     VAIO 20110913 ACPI 00040000)
[    0.000000] ACPI: FACS 0000000066e97000 000040
[    0.000000] ACPI: HPET 0000000066ef3000 000038 (v01   Sony     VAIO 20110913 ACPI 00040000)
[    0.000000] ACPI: APIC 0000000066ef2000 000084 (v02   Sony     VAIO 20110913 ACPI 00040000)
[    0.000000] ACPI: MCFG 0000000066ef1000 00003C (v01   Sony     VAIO 20110913 ACPI 00040000)
[    0.000000] ACPI: BOOT 0000000066ee7000 000028 (v01   Sony     VAIO 20110913 ACPI 00040000)
[    0.000000] ACPI: SLIC 0000000066ee6000 000176 (v01   Sony     VAIO 20110913 ACPI 00040000)
[    0.000000] ACPI: SSDT 0000000066ee5000 0003DE (v01 AMD    POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: SSDT 0000000066ee3000 0012FA (v02    AMD     ALIB 00000001 MSFT 04000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x0000000066efffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x66efffff]
[    0.000000]   NODE_DATA [mem 0x66efb000-0x66efffff]
[    0.000000]  [ffffea0000000000-ffffea00019fffff] PMD -> [ffff880063c00000-ffff8800655fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   empty
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0x6567ffff]
[    0.000000]   node   0: [mem 0x65880000-0x66d3efff]
[    0.000000]   node   0: [mem 0x66ef6000-0x66efffff]
[    0.000000] On node 0 totalpages: 420583
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3998 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 6524 pages used for memmap
[    0.000000]   DMA32 zone: 416585 pages, LIFO batch:31
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
[    0.000000] smpboot: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x65680000-0x6587ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x66d3f000-0x66dbefff]
[    0.000000] PM: Registered nosave memory: [mem 0x66dbf000-0x66ebefff]
[    0.000000] PM: Registered nosave memory: [mem 0x66ebf000-0x66ef5fff]
[    0.000000] e820: [mem 0x7f000000-0xf7ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff880066800000 s86336 r8192 d24256 u524288
[    0.000000] pcpu-alloc: s86336 r8192 d24256 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 413974
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-30-generic root=UUID=293807a0-018c-454f-ae3a-f195b67cf838 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 1619904K/1682332K available (7356K kernel code, 1142K rwdata, 3396K rodata, 1332K init, 1440K bss, 62428K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-3.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 6815744 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 1595.987 MHz processor
[    0.000007] Calibrating delay loop (skipped), value calculated using timer frequency.. 3191.97 BogoMIPS (lpj=6383948)
[    0.000014] pid_max: default: 32768 minimum: 301
[    0.000071] Security Framework initialized
[    0.000118] AppArmor: AppArmor initialized
[    0.000121] Yama: becoming mindful.
[    0.000513] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.002041] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.002783] Mount-cache hash table entries: 4096 (order: 3, 32768 bytes)
[    0.002795] Mountpoint-cache hash table entries: 4096 (order: 3, 32768 bytes)
[    0.003319] Initializing cgroup subsys memory
[    0.003341] Initializing cgroup subsys devices
[    0.003345] Initializing cgroup subsys freezer
[    0.003349] Initializing cgroup subsys blkio
[    0.003352] Initializing cgroup subsys perf_event
[    0.003358] Initializing cgroup subsys hugetlb
[    0.003404] tseg: 0066f00000
[    0.003409] CPU: Physical Processor ID: 0
[    0.003411] CPU: Processor Core ID: 0
[    0.003415] mce: CPU supports 6 MCE banks
[    0.003434] Last level iTLB entries: 4KB 512, 2MB 8, 4MB 4
[    0.003434] Last level dTLB entries: 4KB 512, 2MB 8, 4MB 4
[    0.003434] tlb_flushall_shift: 5
[    0.003654] Freeing SMP alternatives memory: 32K (ffffffff81e6c000 - ffffffff81e74000)
[    0.006357] ACPI: Core revision 20131115
[    0.014536] ACPI: All ACPI Tables successfully acquired
[    0.015188] ftrace: allocating 28465 entries in 112 pages
[    0.043181] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.082922] smpboot: CPU0: AMD E-350 Processor (fam: 14, model: 01, stepping: 00)
[    0.190550] Performance Events: AMD PMU driver.
[    0.190560] ... version:                0
[    0.190563] ... bit width:              48
[    0.190566] ... generic registers:      4
[    0.190569] ... value mask:             0000ffffffffffff
[    0.190571] ... max period:             00007fffffffffff
[    0.190574] ... fixed-purpose events:   0
[    0.190576] ... event mask:             000000000000000f
[    0.194246] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.194466] x86: Booting SMP configuration:
[    0.194472] .... node  #0, CPUs:      #1
[    0.207572] x86: Booted up 1 node, 2 CPUs
[    0.207578] smpboot: Total of 2 processors activated (6383.94 BogoMIPS)
[    0.208883] devtmpfs: initialized
[    0.217103] EVM: security.selinux
[    0.217107] EVM: security.SMACK64
[    0.217110] EVM: security.ima
[    0.217113] EVM: security.capability
[    0.217313] PM: Registering ACPI NVS region [mem 0x65680000-0x6587ffff] (2097152 bytes)
[    0.217402] PM: Registering ACPI NVS region [mem 0x66dbf000-0x66ebefff] (1048576 bytes)
[    0.219524] pinctrl core: initialized pinctrl subsystem
[    0.219706] regulator-dummy: no parameters
[    0.219751] RTC time: 23:37:55, date: 07/09/14
[    0.219847] NET: Registered protocol family 16
[    0.220099] cpuidle: using governor ladder
[    0.220104] cpuidle: using governor menu
[    0.220286] ACPI: bus type PCI registered
[    0.220292] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.220429] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.220435] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.225478] PCI: Using configuration type 1 for base access
[    0.225699] mtrr: your CPUs had inconsistent variable MTRR settings
[    0.225703] mtrr: probably your BIOS does not setup all CPUs.
[    0.225705] mtrr: corrected configuration.
[    0.227570] bio: create slab <bio-0> at 0
[    0.228419] ACPI: Added _OSI(Module Device)
[    0.228429] ACPI: Added _OSI(Processor Device)
[    0.228432] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.228435] ACPI: Added _OSI(Processor Aggregator Device)
[    0.233144] ACPI: Executed 1 blocks of module-level executable AML code
[    0.237020] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.257507] ACPI: Interpreter enabled
[    0.257532] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
[    0.257542] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.257575] ACPI: (supports S0 S3 S4 S5)
[    0.257579] ACPI: Using IOAPIC for interrupt routing
[    0.257889] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.258156] ACPI: No dock devices found.
[    0.277484] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.277499] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.277992] acpi PNP0A08:00: _OSC: OS now controls [PCIeHotplug PME AER PCIeCapability]
[    0.278251] acpi PNP0A08:00: ignoring host bridge window [mem 0x000cc000-0x000cffff] (conflicts with Video ROM [mem 0x000c0000-0x000ce1ff])
[    0.278261] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[    0.278648] PCI host bridge to bus 0000:00
[    0.278655] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.278660] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.278664] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.278669] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.278673] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000c3fff]
[    0.278677] pci_bus 0000:00: root bus resource [mem 0x000c4000-0x000c7fff]
[    0.278681] pci_bus 0000:00: root bus resource [mem 0x000c8000-0x000cbfff]
[    0.278685] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    0.278689] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    0.278693] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    0.278697] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    0.278701] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
[    0.278709] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff]
[    0.278713] pci_bus 0000:00: root bus resource [mem 0x000e8000-0x000ebfff]
[    0.278717] pci_bus 0000:00: root bus resource [mem 0x000ec000-0x000effff]
[    0.278721] pci_bus 0000:00: root bus resource [mem 0x7f000000-0xf7ffffff]
[    0.278725] pci_bus 0000:00: root bus resource [mem 0xfc000000-0xffffffff]
[    0.278740] pci 0000:00:00.0: [1022:1510] type 00 class 0x060000
[    0.278915] pci 0000:00:01.0: [1002:9802] type 00 class 0x030000
[    0.278933] pci 0000:00:01.0: reg 0x10: [mem 0x80000000-0x8fffffff pref]
[    0.278944] pci 0000:00:01.0: reg 0x14: [io  0x3000-0x30ff]
[    0.278955] pci 0000:00:01.0: reg 0x18: [mem 0x90200000-0x9023ffff]
[    0.279020] pci 0000:00:01.0: supports D1 D2
[    0.279157] pci 0000:00:01.1: [1002:1314] type 00 class 0x040300
[    0.279173] pci 0000:00:01.1: reg 0x10: [mem 0x90244000-0x90247fff]
[    0.279248] pci 0000:00:01.1: supports D1 D2
[    0.279390] pci 0000:00:04.0: [1022:1512] type 01 class 0x060400
[    0.279472] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    0.279567] pci 0000:00:04.0: System wakeup disabled by ACPI
[    0.279655] pci 0000:00:06.0: [1022:1514] type 01 class 0x060400
[    0.279735] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.279908] pci 0000:00:11.0: [1002:4391] type 00 class 0x010601
[    0.279936] pci 0000:00:11.0: reg 0x10: [io  0x3118-0x311f]
[    0.279951] pci 0000:00:11.0: reg 0x14: [io  0x3124-0x3127]
[    0.279966] pci 0000:00:11.0: reg 0x18: [io  0x3110-0x3117]
[    0.279980] pci 0000:00:11.0: reg 0x1c: [io  0x3120-0x3123]
[    0.279995] pci 0000:00:11.0: reg 0x20: [io  0x3100-0x310f]
[    0.280010] pci 0000:00:11.0: reg 0x24: [mem 0x9024c000-0x9024c3ff]
[    0.280211] pci 0000:00:12.0: [1002:4397] type 00 class 0x0c0310
[    0.280232] pci 0000:00:12.0: reg 0x10: [mem 0x9024b000-0x9024bfff]
[    0.280388] pci 0000:00:12.0: System wakeup disabled by ACPI
[    0.280455] pci 0000:00:12.2: [1002:4396] type 00 class 0x0c0320
[    0.280966] pci 0000:00:12.2: reg 0x10: [mem 0x9024a000-0x9024a0ff]
[    0.283608] pci 0000:00:12.2: supports D1 D2
[    0.283612] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.283705] pci 0000:00:12.2: System wakeup disabled by ACPI
[    0.283778] pci 0000:00:13.0: [1002:4397] type 00 class 0x0c0310
[    0.283799] pci 0000:00:13.0: reg 0x10: [mem 0x90249000-0x90249fff]
[    0.283955] pci 0000:00:13.0: System wakeup disabled by ACPI
[    0.284022] pci 0000:00:13.2: [1002:4396] type 00 class 0x0c0320
[    0.284512] pci 0000:00:13.2: reg 0x10: [mem 0x90248000-0x902480ff]
[    0.287108] pci 0000:00:13.2: supports D1 D2
[    0.287112] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.287202] pci 0000:00:13.2: System wakeup disabled by ACPI
[    0.287271] pci 0000:00:14.0: [1002:4385] type 00 class 0x0c0500
[    0.287486] pci 0000:00:14.2: [1002:4383] type 00 class 0x040300
[    0.287518] pci 0000:00:14.2: reg 0x10: [mem 0x90240000-0x90243fff 64bit]
[    0.287617] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.287759] pci 0000:00:14.3: [1002:439d] type 00 class 0x060100
[    0.287973] pci 0000:00:14.4: [1002:4384] type 01 class 0x060401
[    0.288100] pci 0000:00:14.4: System wakeup disabled by ACPI
[    0.288169] pci 0000:00:18.0: [1022:1700] type 00 class 0x060000
[    0.288325] pci 0000:00:18.1: [1022:1701] type 00 class 0x060000
[    0.288477] pci 0000:00:18.2: [1022:1702] type 00 class 0x060000
[    0.288629] pci 0000:00:18.3: [1022:1703] type 00 class 0x060000
[    0.288794] pci 0000:00:18.4: [1022:1704] type 00 class 0x060000
[    0.288940] pci 0000:00:18.5: [1022:1718] type 00 class 0x060000
[    0.289091] pci 0000:00:18.6: [1022:1716] type 00 class 0x060000
[    0.289240] pci 0000:00:18.7: [1022:1719] type 00 class 0x060000
[    0.289594] pci 0000:01:00.0: [1969:1063] type 00 class 0x020000
[    0.289624] pci 0000:01:00.0: reg 0x10: [mem 0x90100000-0x9013ffff 64bit]
[    0.289641] pci 0000:01:00.0: reg 0x18: [io  0x2000-0x207f]
[    0.289755] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.295859] pci 0000:00:04.0: PCI bridge to [bus 01]
[    0.295886] pci 0000:00:04.0:   bridge window [io  0x2000-0x2fff]
[    0.295895] pci 0000:00:04.0:   bridge window [mem 0x90100000-0x901fffff]
[    0.296056] pci 0000:02:00.0: [168c:002b] type 00 class 0x028000
[    0.296089] pci 0000:02:00.0: reg 0x10: [mem 0x90000000-0x9000ffff 64bit]
[    0.296207] pci 0000:02:00.0: supports D1
[    0.296211] pci 0000:02:00.0: PME# supported from D0 D1 D3hot D3cold
[    0.303861] pci 0000:00:06.0: PCI bridge to [bus 02]
[    0.303892] pci 0000:00:06.0:   bridge window [mem 0x90000000-0x900fffff]
[    0.304050] pci 0000:00:14.4: PCI bridge to [bus 03] (subtractive decode)
[    0.304066] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.304070] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.304075] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.304080] pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000c3fff] (subtractive decode)
[    0.304084] pci 0000:00:14.4:   bridge window [mem 0x000c4000-0x000c7fff] (subtractive decode)
[    0.304088] pci 0000:00:14.4:   bridge window [mem 0x000c8000-0x000cbfff] (subtractive decode)
[    0.304092] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.304097] pci 0000:00:14.4:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.304101] pci 0000:00:14.4:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.304105] pci 0000:00:14.4:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.304109] pci 0000:00:14.4:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    0.304113] pci 0000:00:14.4:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
[    0.304117] pci 0000:00:14.4:   bridge window [mem 0x000e8000-0x000ebfff] (subtractive decode)
[    0.304122] pci 0000:00:14.4:   bridge window [mem 0x000ec000-0x000effff] (subtractive decode)
[    0.304126] pci 0000:00:14.4:   bridge window [mem 0x7f000000-0xf7ffffff] (subtractive decode)
[    0.304130] pci 0000:00:14.4:   bridge window [mem 0xfc000000-0xffffffff] (subtractive decode)
[    0.305158] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.305300] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.305441] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.305580] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.305696] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.305791] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.305886] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.305980] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.306254] ACPI: \_SB_.PCI0: notify handler is installed
[    0.306350] Found 1 acpi root devices
[    0.306427] ACPI : EC: GPE = 0x3, I/O: command/status = 0x66, data = 0x62
[    0.306859] vgaarb: device added: PCI:0000:00:01.0,decodes=io+mem,owns=io+mem,locks=none
[    0.306876] vgaarb: loaded
[    0.306879] vgaarb: bridge control possible 0000:00:01.0
[    0.307319] SCSI subsystem initialized
[    0.307561] libata version 3.00 loaded.
[    0.307654] ACPI: bus type USB registered
[    0.307708] usbcore: registered new interface driver usbfs
[    0.307725] usbcore: registered new interface driver hub
[    0.308046] usbcore: registered new device driver usb
[    0.308503] PCI: Using ACPI for IRQ routing
[    0.311127] PCI: pci_cache_line_size set to 64 bytes
[    0.311219] e820: reserve RAM buffer [mem 0x0009f800-0x0009ffff]
[    0.311225] e820: reserve RAM buffer [mem 0x65680000-0x67ffffff]
[    0.311229] e820: reserve RAM buffer [mem 0x66d3f000-0x67ffffff]
[    0.311232] e820: reserve RAM buffer [mem 0x66f00000-0x67ffffff]
[    0.311458] NetLabel: Initializing
[    0.311461] NetLabel:  domain hash size = 128
[    0.311464] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.311491] NetLabel:  unlabeled traffic allowed by default
[    0.311845] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.311859] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    0.313994] Switched to clocksource hpet
[    0.324835] AppArmor: AppArmor Filesystem Enabled
[    0.324908] pnp: PnP ACPI init
[    0.324939] ACPI: bus type PNP registered
[    0.325245] system 00:00: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.325251] system 00:00: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.325260] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.325512] pnp 00:01: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.325597] pnp 00:02: [dma 4]
[    0.325640] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.325696] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.325801] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.325850] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.325946] system 00:06: [io  0x0400-0x04cf] could not be reserved
[    0.325952] system 00:06: [io  0x04d0-0x04d1] has been reserved
[    0.325956] system 00:06: [io  0x04d6] has been reserved
[    0.325961] system 00:06: [io  0x0680-0x06ff] has been reserved
[    0.325966] system 00:06: [io  0x077a] has been reserved
[    0.325971] system 00:06: [io  0x0c00-0x0c01] has been reserved
[    0.325975] system 00:06: [io  0x0c14] has been reserved
[    0.325980] system 00:06: [io  0x0c50-0x0c52] has been reserved
[    0.325984] system 00:06: [io  0x0c6c] has been reserved
[    0.325989] system 00:06: [io  0x0c6f] has been reserved
[    0.325993] system 00:06: [io  0x0cd0-0x0cdb] has been reserved
[    0.326042] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.326194] system 00:07: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.326200] system 00:07: [mem 0xffe00000-0xffffffff] has been reserved
[    0.326206] system 00:07: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.326336] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.326406] pnp 00:09: Plug and Play ACPI device, IDs SYN0300 SYN0002 PNP0f13 (active)
[    0.326622] pnp: PnP ACPI: found 10 devices
[    0.326625] ACPI: bus type PNP unregistered
[    0.340960] pci 0000:00:04.0: PCI bridge to [bus 01]
[    0.340973] pci 0000:00:04.0:   bridge window [io  0x2000-0x2fff]
[    0.340982] pci 0000:00:04.0:   bridge window [mem 0x90100000-0x901fffff]
[    0.340993] pci 0000:00:06.0: PCI bridge to [bus 02]
[    0.341000] pci 0000:00:06.0:   bridge window [mem 0x90000000-0x900fffff]
[    0.341010] pci 0000:00:14.4: PCI bridge to [bus 03]
[    0.341030] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.341034] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.341038] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.341042] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.341046] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.341050] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.341055] pci_bus 0000:00: resource 10 [mem 0x000d0000-0x000d3fff]
[    0.341059] pci_bus 0000:00: resource 11 [mem 0x000d4000-0x000d7fff]
[    0.341063] pci_bus 0000:00: resource 12 [mem 0x000d8000-0x000dbfff]
[    0.341067] pci_bus 0000:00: resource 13 [mem 0x000dc000-0x000dffff]
[    0.341071] pci_bus 0000:00: resource 14 [mem 0x000e0000-0x000e3fff]
[    0.341075] pci_bus 0000:00: resource 15 [mem 0x000e4000-0x000e7fff]
[    0.341079] pci_bus 0000:00: resource 16 [mem 0x000e8000-0x000ebfff]
[    0.341083] pci_bus 0000:00: resource 17 [mem 0x000ec000-0x000effff]
[    0.341087] pci_bus 0000:00: resource 18 [mem 0x7f000000-0xf7ffffff]
[    0.341091] pci_bus 0000:00: resource 19 [mem 0xfc000000-0xffffffff]
[    0.341096] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
[    0.341100] pci_bus 0000:01: resource 1 [mem 0x90100000-0x901fffff]
[    0.341104] pci_bus 0000:02: resource 1 [mem 0x90000000-0x900fffff]
[    0.341109] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.341113] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.341117] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.341122] pci_bus 0000:03: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.341126] pci_bus 0000:03: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.341130] pci_bus 0000:03: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.341134] pci_bus 0000:03: resource 10 [mem 0x000d0000-0x000d3fff]
[    0.341138] pci_bus 0000:03: resource 11 [mem 0x000d4000-0x000d7fff]
[    0.341142] pci_bus 0000:03: resource 12 [mem 0x000d8000-0x000dbfff]
[    0.341146] pci_bus 0000:03: resource 13 [mem 0x000dc000-0x000dffff]
[    0.341150] pci_bus 0000:03: resource 14 [mem 0x000e0000-0x000e3fff]
[    0.341154] pci_bus 0000:03: resource 15 [mem 0x000e4000-0x000e7fff]
[    0.341157] pci_bus 0000:03: resource 16 [mem 0x000e8000-0x000ebfff]
[    0.341161] pci_bus 0000:03: resource 17 [mem 0x000ec000-0x000effff]
[    0.341166] pci_bus 0000:03: resource 18 [mem 0x7f000000-0xf7ffffff]
[    0.341170] pci_bus 0000:03: resource 19 [mem 0xfc000000-0xffffffff]
[    0.341241] NET: Registered protocol family 2
[    0.341570] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.341675] TCP bind hash table entries: 16384 (order: 6, 262144 bytes)
[    0.341811] TCP: Hash tables configured (established 16384 bind 16384)
[    0.341905] TCP: reno registered
[    0.341922] UDP hash table entries: 1024 (order: 3, 32768 bytes)
[    0.341954] UDP-Lite hash table entries: 1024 (order: 3, 32768 bytes)
[    0.342213] NET: Registered protocol family 1
[    0.342249] pci 0000:00:01.0: Boot video device
[    0.518601] PCI: CLS 64 bytes, default 64
[    0.518742] Trying to unpack rootfs image as initramfs...
[    1.134439] Freeing initrd memory: 18704K (ffff880035b68000 - ffff880036dac000)
[    1.134647] Simple Boot Flag at 0x44 set to 0x1
[    1.134905] LVT offset 0 assigned for vector 0x400
[    1.134984] perf: AMD IBS detected (0x000000ff)
[    1.135122] microcode: CPU0: patch_level=0x05000028
[    1.135140] microcode: CPU1: patch_level=0x05000028
[    1.135378] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.135389] Scanning for low memory corruption every 60 seconds
[    1.136076] Initialise system trusted keyring
[    1.136193] audit: initializing netlink socket (disabled)
[    1.136222] type=2000 audit(1404949076.020:1): initialized
[    1.189150] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.192050] zbud: loaded
[    1.192624] VFS: Disk quotas dquot_6.5.2
[    1.192739] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.194129] fuse init (API version 7.22)
[    1.194569] msgmni has been set to 3200
[    1.194731] Key type big_key registered
[    1.196768] Key type asymmetric registered
[    1.196779] Asymmetric key parser 'x509' registered
[    1.196892] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.196964] io scheduler noop registered
[    1.196968] io scheduler deadline registered (default)
[    1.197024] io scheduler cfq registered
[    1.197407] pcieport 0000:00:04.0: irq 40 for MSI/MSI-X
[    1.197629] pcieport 0000:00:06.0: irq 41 for MSI/MSI-X
[    1.197757] pcieport 0000:00:04.0: Signaling PME through PCIe PME interrupt
[    1.197763] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    1.197770] pcie_pme 0000:00:04.0:pcie01: service driver pcie_pme loaded
[    1.197803] pcieport 0000:00:06.0: Signaling PME through PCIe PME interrupt
[    1.197807] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt
[    1.197814] pcie_pme 0000:00:06.0:pcie01: service driver pcie_pme loaded
[    1.197843] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.197874] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.197957] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[    1.197960] vesafb: scrolling: redraw
[    1.197964] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[    1.198239] vesafb: framebuffer at 0x80000000, mapped to 0xffffc90004400000, using 3072k, total 3072k
[    1.257047] Console: switching to colour frame buffer device 128x48
[    1.315525] fb0: VESA VGA frame buffer device
[    1.315580] ipmi message handler version 39.2
[    1.317007] ACPI: AC Adapter [ADP1] (off-line)
[    1.317231] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.317240] ACPI: Power Button [PWRB]
[    1.317337] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    1.319649] ACPI: Lid Switch [LID0]
[    1.319792] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.319801] ACPI: Sleep Button [SLPB]
[    1.319869] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    1.319874] ACPI: Power Button [PWRF]
[    1.320107] ACPI: acpi_idle registered with cpuidle
[    1.356965] thermal LNXTHERM:00: registered as thermal_zone0
[    1.356975] ACPI: Thermal Zone [TZS0] (69 C)
[    1.378918] thermal LNXTHERM:01: registered as thermal_zone1
[    1.378928] ACPI: Thermal Zone [TZS1] (29 C)
[    1.379007] GHES: HEST is not enabled!
[    1.379289] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.385910] Linux agpgart interface v0.103
[    1.392092] brd: module loaded
[    1.393935] loop: module loaded
[    1.394767] libphy: Fixed MDIO Bus: probed
[    1.394954] tun: Universal TUN/TAP device driver, 1.6
[    1.394957] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.395300] PPP generic driver version 2.4.2
[    1.395597] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.395623] ehci-pci: EHCI PCI platform driver
[    1.395827] QUIRK: Enable AMD PLL fix
[    1.395872] ehci-pci 0000:00:12.2: EHCI Host Controller
[    1.395886] ehci-pci 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.395898] ehci-pci 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.395914] ehci-pci 0000:00:12.2: debug port 1
[    1.396008] ehci-pci 0000:00:12.2: irq 17, io mem 0x9024a000
[    1.406927] ehci-pci 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.407115] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.407121] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.407125] usb usb1: Product: EHCI Host Controller
[    1.407130] usb usb1: Manufacturer: Linux 3.13.0-30-generic ehci_hcd
[    1.407133] usb usb1: SerialNumber: 0000:00:12.2
[    1.407572] hub 1-0:1.0: USB hub found
[    1.407597] hub 1-0:1.0: 5 ports detected
[    1.408050] ehci-pci 0000:00:13.2: EHCI Host Controller
[    1.408063] ehci-pci 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.408073] ehci-pci 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.408089] ehci-pci 0000:00:13.2: debug port 1
[    1.408144] ehci-pci 0000:00:13.2: irq 17, io mem 0x90248000
[    1.418929] ehci-pci 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.419101] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.419107] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.419112] usb usb2: Product: EHCI Host Controller
[    1.419116] usb usb2: Manufacturer: Linux 3.13.0-30-generic ehci_hcd
[    1.419120] usb usb2: SerialNumber: 0000:00:13.2
[    1.419630] hub 2-0:1.0: USB hub found
[    1.419654] hub 2-0:1.0: 5 ports detected
[    1.420045] ehci-platform: EHCI generic platform driver
[    1.420069] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.420073] ohci-pci: OHCI PCI platform driver
[    1.420268] ohci-pci 0000:00:12.0: OHCI PCI host controller
[    1.420280] ohci-pci 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.420331] ohci-pci 0000:00:12.0: irq 18, io mem 0x9024b000
[    1.479079] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.479089] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.479094] usb usb3: Product: OHCI PCI host controller
[    1.479098] usb usb3: Manufacturer: Linux 3.13.0-30-generic ohci_hcd
[    1.479102] usb usb3: SerialNumber: 0000:00:12.0
[    1.479565] hub 3-0:1.0: USB hub found
[    1.479592] hub 3-0:1.0: 5 ports detected
[    1.480029] ohci-pci 0000:00:13.0: OHCI PCI host controller
[    1.480042] ohci-pci 0000:00:13.0: new USB bus registered, assigned bus number 4
[    1.480074] ohci-pci 0000:00:13.0: irq 18, io mem 0x90249000
[    1.539085] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.539095] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.539100] usb usb4: Product: OHCI PCI host controller
[    1.539104] usb usb4: Manufacturer: Linux 3.13.0-30-generic ohci_hcd
[    1.539109] usb usb4: SerialNumber: 0000:00:13.0
[    1.539544] hub 4-0:1.0: USB hub found
[    1.539571] hub 4-0:1.0: 5 ports detected
[    1.539970] ohci-platform: OHCI generic platform driver
[    1.539994] uhci_hcd: USB Universal Host Controller Interface driver
[    1.540122] i8042: PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.563978] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.563990] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.564544] mousedev: PS/2 mouse device common for all mice
[    1.565580] rtc_cmos 00:04: RTC can wake from S4
[    1.565965] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.566014] rtc_cmos 00:04: alarms up to one day, 114 bytes nvram, hpet irqs
[    1.566174] device-mapper: uevent: version 1.0.3
[    1.566499] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    1.566520] ledtrig-cpu: registered to indicate activity on CPUs
[    1.566736] TCP: cubic registered
[    1.566977] NET: Registered protocol family 10
[    1.567327] NET: Registered protocol family 17
[    1.567347] Key type dns_resolver registered
[    1.568651] Loading compiled-in X.509 certificates
[    1.571099] Loaded X.509 cert 'Magrathea: Glacier signing key: 094b30964ee6ceb2c567d252226b47712cfd8af6'
[    1.571129] registered taskstats version 1
[    1.578049] Key type trusted registered
[    1.584683] Key type encrypted registered
[    1.591348] AppArmor: AppArmor sha1 policy hashing enabled
[    1.591361] IMA: No TPM chip found, activating TPM-bypass!
[    1.591764] regulator-dummy: disabling
[    1.592103]   Magic number: 6:703:655
[    1.592305] rtc_cmos 00:04: setting system clock to 2014-07-09 23:37:57 UTC (1404949077)
[    1.592630] acpi-cpufreq: overriding BIOS provided _PSD data
[    1.592809] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.592812] EDD information not available.
[    1.592890] PM: Hibernation image not present or could not be loaded.
[    1.602219] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.671341] ACPI: Battery Slot [BAT0] (battery present)
[    1.674339] Freeing unused kernel memory: 1332K (ffffffff81d1f000 - ffffffff81e6c000)
[    1.674350] Write protecting the kernel read-only data: 12288k
[    1.679760] Freeing unused kernel memory: 824K (ffff880001732000 - ffff880001800000)
[    1.684087] Freeing unused kernel memory: 700K (ffff880001b51000 - ffff880001c00000)
[    1.724287] systemd-udevd[103]: starting version 204
[    1.735023] usb 2-3: new high-speed USB device number 2 using ehci-pci
[    1.809182] ahci 0000:00:11.0: version 3.0
[    1.809467] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 1 ports 6 Gbps 0x1 impl SATA mode
[    1.809475] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    1.809944] scsi0 : ahci
[    1.810091] ata1: SATA max UDMA/133 abar m1024@0x9024c000 port 0x9024c100 irq 19
[    1.827540] atl1c 0000:01:00.0: version 1.0.1.1-NAPI
[    1.892363] usb 2-3: New USB device found, idVendor=04f2, idProduct=b211
[    1.892374] usb 2-3: New USB device strings: Mfr=2, Product=1, SerialNumber=0
[    1.892379] usb 2-3: Product: Sony Visual Communication Camera
[    1.892384] usb 2-3: Manufacturer: Sonix Technology Co., Ltd.
[    2.135646] tsc: Refined TSC clocksource calibration: 1596.003 MHz
[    2.267604] usb 2-5: new high-speed USB device number 4 using ehci-pci
[    2.299504] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    2.301649] ata1.00: supports DRM functions and may not be fully accessible
[    2.301743] ata1.00: failed to get NCQ Send/Recv Log Emask 0x1
[    2.301748] ata1.00: ATA-9: Samsung SSD 840 EVO 120GB, EXT0BB6Q, max UDMA/133
[    2.301753] ata1.00: 234441648 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
[    2.302197] ata1.00: supports DRM functions and may not be fully accessible
[    2.302286] ata1.00: failed to get NCQ Send/Recv Log Emask 0x1
[    2.302295] ata1.00: configured for UDMA/133
[    2.302835] scsi 0:0:0:0: Direct-Access     ATA      Samsung SSD 840  EXT0 PQ: 0 ANSI: 5
[    2.303314] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.303352] sd 0:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    2.303595] sd 0:0:0:0: [sda] Write Protect is off
[    2.303601] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.303797] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.305547]  sda: sda1 sda2 < sda5 >
[    2.306875] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.376504] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    2.661344] usb 2-5: New USB device found, idVendor=0bda, idProduct=0186
[    2.661355] usb 2-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.661359] usb 2-5: Product: USB 2.0 Reader
[    2.661363] usb 2-5: Manufacturer: Generic
[    2.661368] usb 2-5: SerialNumber: 00000001
[    2.811912] random: init urandom read with 42 bits of entropy available
[    2.838438] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.5, id: 0x1e0b1, caps: 0xd00073/0x240000/0xa0400, board id: 1571, fw id: 698215
[    2.882090] init: plymouth-upstart-bridge main process (155) terminated with status 1
[    2.882189] init: plymouth-upstart-bridge main process ended, respawning
[    2.905862] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[    2.911411] init: plymouth-upstart-bridge main process (165) terminated with status 1
[    2.911448] init: plymouth-upstart-bridge main process ended, respawning
[    2.931167] init: plymouth-upstart-bridge main process (169) terminated with status 1
[    2.931207] init: plymouth-upstart-bridge main process ended, respawning
[    2.939721] usb 4-4: new full-speed USB device number 2 using ohci-pci
[    3.115039] usb 4-4: New USB device found, idVendor=0489, idProduct=e00f
[    3.115051] usb 4-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    3.115056] usb 4-4: Product: Broadcom Bluetooth Device
[    3.115060] usb 4-4: Manufacturer: Broadcom Corp
[    3.115064] usb 4-4: SerialNumber: 90004EF7955A
[    3.139944] Switched to clocksource tsc
[    3.218261] Adding 1680380k swap on /dev/sda5.  Priority:-1 extents:1 across:1680380k SSFS
[    3.237769] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    3.308356] ata1.00: exception Emask 0x10 SAct 0x1 SErr 0x400000 action 0x6 frozen
[    3.308366] ata1.00: irq_stat 0x08000000, interface fatal error
[    3.308371] ata1: SError: { Handshk }
[    3.308378] ata1.00: failed command: WRITE FPDMA QUEUED
[    3.308389] ata1.00: cmd 61/08:00:e0:3e:84/00:00:0b:00:00/40 tag 0 ncq 4096 out
[    3.308389]          res 40/00:00:e0:3e:84/00:00:0b:00:00/40 Emask 0x10 (ATA bus error)
[    3.308394] ata1.00: status: { DRDY }
[    3.308404] ata1: hard resetting link
[    3.800427] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    3.802565] ata1.00: supports DRM functions and may not be fully accessible
[    3.802647] ata1.00: failed to get NCQ Send/Recv Log Emask 0x1
[    3.803191] ata1.00: supports DRM functions and may not be fully accessible
[    3.803271] ata1.00: failed to get NCQ Send/Recv Log Emask 0x1
[    3.803280] ata1.00: configured for UDMA/133
[    3.803319] ata1: EH complete
[    3.815088] ata1.00: exception Emask 0x10 SAct 0x1 SErr 0x400000 action 0x6 frozen
[    3.815098] ata1.00: irq_stat 0x08000000, interface fatal error
[    3.815104] ata1: SError: { Handshk }
[    3.815110] ata1.00: failed command: WRITE FPDMA QUEUED
[    3.815121] ata1.00: cmd 61/08:00:08:45:84/00:00:0b:00:00/40 tag 0 ncq 4096 out
[    3.815121]          res 40/00:00:08:45:84/00:00:0b:00:00/40 Emask 0x10 (ATA bus error)
[    3.815126] ata1.00: status: { DRDY }
[    3.815135] ata1: hard resetting link
[    4.304745] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    4.306898] ata1.00: supports DRM functions and may not be fully accessible
[    4.306980] ata1.00: failed to get NCQ Send/Recv Log Emask 0x1
[    4.307680] ata1.00: supports DRM functions and may not be fully accessible
[    4.307899] ata1.00: failed to get NCQ Send/Recv Log Emask 0x1
[    4.307914] ata1.00: configured for UDMA/133
[    4.307963] ata1: EH complete
[    4.309564] ata1.00: exception Emask 0x10 SAct 0x8 SErr 0x400000 action 0x6 frozen
[    4.309574] ata1.00: irq_stat 0x08000000, interface fatal error
[    4.309580] ata1: SError: { Handshk }
[    4.309587] ata1.00: failed command: WRITE FPDMA QUEUED
[    4.309597] ata1.00: cmd 61/08:18:a0:0a:84/00:00:0b:00:00/40 tag 3 ncq 4096 out
[    4.309597]          res 40/00:18:a0:0a:84/00:00:0b:00:00/40 Emask 0x10 (ATA bus error)
[    4.309602] ata1.00: status: { DRDY }
[    4.309612] ata1: hard resetting link
[    4.801051] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    4.803170] ata1.00: supports DRM functions and may not be fully accessible
[    4.803253] ata1.00: failed to get NCQ Send/Recv Log Emask 0x1
[    4.803795] ata1.00: supports DRM functions and may not be fully accessible
[    4.803876] ata1.00: failed to get NCQ Send/Recv Log Emask 0x1
[    4.803885] ata1.00: configured for UDMA/133
[    4.803925] ata1: EH complete
[    4.850402] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    5.093050] systemd-udevd[308]: starting version 204
[    5.296063] lp: driver loaded but no devices found
[    5.331815] ppdev: user-space parallel port driver
[    5.365301] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    5.376466] random: nonblocking pool is initialized
[    5.460138] acpi device:01: registered as cooling_device2
[    5.460782] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input7
[    5.461045] ACPI: Video Device [VGA1] (multi-head: yes  rom: no  post: no)
[    5.461512] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:04/LNXVIDEO:01/input/input8
[    5.683071] sony_laptop: Sony Notebook Control Driver v0.6
[    5.684895] input: Sony Vaio Keys as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:25/SNY5001:00/input/input9
[    5.685290] input: Sony Vaio Jogdial as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:25/SNY5001:00/input/input10
[    5.784556] wmi: Mapper loaded
[    5.821222] sony_laptop: brightness ignored, must be controlled by ACPI video driver
[    5.947959] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[    5.948112] piix4_smbus 0000:00:14.0: Auxiliary SMBus Host Controller at 0xb20
[    5.958978] sp5100_tco: SP5100/SB800 TCO WatchDog Timer Driver v0.05
[    5.961797] sp5100_tco: PCI Revision ID: 0x42
[    5.961858] sp5100_tco: Using 0xfed80b00 for watchdog MMIO address
[    5.961873] sp5100_tco: Last reboot was not triggered by watchdog.
[    6.068271] Bluetooth: Core ver 2.17
[    6.068305] NET: Registered protocol family 31
[    6.068306] Bluetooth: HCI device and connection manager initialized
[    6.068321] Bluetooth: HCI socket layer initialized
[    6.068326] Bluetooth: L2CAP socket layer initialized
[    6.068333] Bluetooth: SCO socket layer initialized
[    6.069393] sp5100_tco: initialized (0xffffc900043d6b00). heartbeat=60 sec (nowayout=0)
[    6.101721] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    6.101729] Bluetooth: BNEP filters: protocol multicast
[    6.101748] Bluetooth: BNEP socket layer initialized
[    6.109851] Bluetooth: RFCOMM TTY layer initialized
[    6.109880] Bluetooth: RFCOMM socket layer initialized
[    6.109910] Bluetooth: RFCOMM ver 1.11
[    6.114810] cfg80211: Calling CRDA to update world regulatory domain
[    6.114907] usbcore: registered new interface driver btusb
[    6.115004] [drm] Initialized drm 1.1.0 20060810
[    6.190763] ata1: limiting SATA link speed to 3.0 Gbps
[    6.190776] ata1.00: exception Emask 0x10 SAct 0x1 SErr 0x400001 action 0x6 frozen
[    6.191635] ata1.00: irq_stat 0x08000000, interface fatal error
[    6.192296] ata1: SError: { RecovData Handshk }
[    6.192806] ata1.00: failed command: WRITE FPDMA QUEUED
[    6.193397] ata1.00: cmd 61/f8:00:10:08:c4/00:00:06:00:00/40 tag 0 ncq 126976 out
[    6.193397]          res 40/00:00:10:08:c4/00:00:06:00:00/40 Emask 0x10 (ATA bus error)
[    6.195130] ata1.00: status: { DRDY }
[    6.195548] ata1: hard resetting link
[    6.686051] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
[    6.688079] ata1.00: supports DRM functions and may not be fully accessible
[    6.688162] ata1.00: failed to get NCQ Send/Recv Log Emask 0x1
[    6.688485] ata1.00: supports DRM functions and may not be fully accessible
[    6.688568] ata1.00: failed to get NCQ Send/Recv Log Emask 0x1
[    6.688577] ata1.00: configured for UDMA/133
[    6.688621] ata1: EH complete
[    6.731230] type=1400 audit(1404949082.630:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=474 comm="apparmor_parser"
[    6.731248] type=1400 audit(1404949082.630:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=474 comm="apparmor_parser"
[    6.731258] type=1400 audit(1404949082.630:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=474 comm="apparmor_parser"
[    6.732102] type=1400 audit(1404949082.630:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=474 comm="apparmor_parser"
[    6.732115] type=1400 audit(1404949082.630:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=474 comm="apparmor_parser"
[    6.732558] type=1400 audit(1404949082.630:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=474 comm="apparmor_parser"
[    6.759785] type=1400 audit(1404949082.658:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=473 comm="apparmor_parser"
[    6.759806] type=1400 audit(1404949082.658:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=473 comm="apparmor_parser"
[    6.760640] type=1400 audit(1404949082.658:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=473 comm="apparmor_parser"
[    6.911116] Linux video capture interface: v2.00
[    7.086558] usb-storage 2-5:1.0: USB Mass Storage device detected
[    7.102230] scsi1 : usb-storage 2-5:1.0
[    7.102478] usbcore: registered new interface driver usb-storage
[    7.250576] uvcvideo: Found UVC 1.00 device Sony Visual Communication Camera (04f2:b211)
[    7.256782] [drm] radeon kernel modesetting enabled.
[    7.256888] checking generic (80000000 300000) vs hw (80000000 10000000)
[    7.256892] fb: conflicting fb hw usage radeondrmfb vs VESA VGA - removing generic driver
[    7.256987] Console: switching to colour dummy device 80x25
[    7.311209] ath: phy0: Enable LNA combining
[    7.314819] input: Sony Visual Communication Camer as /devices/pci0000:00/0000:00:13.2/usb2/2-3/2-3:1.0/input/input11
[    7.316582] usbcore: registered new interface driver uvcvideo
[    7.316590] USB Video Class driver (1.1.1)
[    7.320224] [drm] initializing kernel modesetting (PALM 0x1002:0x9802 0x104D:0x9082).
[    7.320284] [drm] register mmio base: 0x90200000
[    7.320287] [drm] register mmio size: 262144
[    7.323654] ath: phy0: ASPM enabled: 0x42
[    7.323660] ath: EEPROM regdomain: 0x65
[    7.323662] ath: EEPROM indicates we should expect a direct regpair map
[    7.323668] ath: Country alpha2 being used: 00
[    7.323671] ath: Regpair used: 0x65
[    7.324473] ATOM BIOS: Sony
[    7.324564] radeon 0000:00:01.0: VRAM: 384M 0x0000000000000000 - 0x0000000017FFFFFF (384M used)
[    7.324570] radeon 0000:00:01.0: GTT: 1024M 0x0000000018000000 - 0x0000000057FFFFFF
[    7.324575] [drm] Detected VRAM RAM=384M, BAR=256M
[    7.324578] [drm] RAM width 32bits DDR
[    7.327875] [TTM] Zone  kernel: Available graphics memory: 820748 kiB
[    7.327883] [TTM] Initializing pool allocator
[    7.327896] [TTM] Initializing DMA pool allocator
[    7.327958] [drm] radeon: 384M of VRAM memory ready
[    7.327961] [drm] radeon: 1024M of GTT memory ready.
[    7.327992] [drm] Loading PALM Microcode
[    7.342958] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[    7.344456] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xffffc90004720000, irq=18
[    7.346739] type=1400 audit(1404949083.246:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cups-browsed" pid=530 comm="apparmor_parser"
[    7.354630] [drm] GART: num cpu pages 262144, num gpu pages 262144
[    7.420167] [drm] PCIE GART of 1024M enabled (table at 0x0000000000273000).
[    7.421015] radeon 0000:00:01.0: WB enabled
[    7.421026] radeon 0000:00:01.0: fence driver on ring 0 use gpu addr 0x0000000018000c00 and cpu addr 0xffff880062f09c00
[    7.421032] radeon 0000:00:01.0: fence driver on ring 3 use gpu addr 0x0000000018000c0c and cpu addr 0xffff880062f09c0c
[    7.421833] radeon 0000:00:01.0: fence driver on ring 5 use gpu addr 0x0000000000072118 and cpu addr 0xffffc900044b2118
[    7.421840] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    7.421843] [drm] Driver supports precise vblank timestamp query.
[    7.421889] radeon 0000:00:01.0: irq 42 for MSI/MSI-X
[    7.421917] radeon 0000:00:01.0: radeon: using MSI.
[    7.421964] [drm] radeon: irq initialized.
[    7.439661] [drm] ring test on 0 succeeded in 1 usecs
[    7.439794] [drm] ring test on 3 succeeded in 1 usecs
[    7.447092] kvm: disabled by bios
[    7.497813] [drm] ring test on 5 succeeded in 1 usecs
[    7.519971] [drm] UVD initialized successfully.
[    7.524401] [drm] Enabling audio 0 support
[    7.524457] [drm] ib test on ring 0 succeeded in 0 usecs
[    7.524496] [drm] ib test on ring 3 succeeded in 0 usecs
[    7.554144] [drm] ib test on ring 5 succeeded
[    7.636034] [drm] radeon atom DIG backlight initialized
[    7.636050] [drm] Radeon Display Connectors
[    7.636054] [drm] Connector 0:
[    7.636059] [drm]   LVDS-1
[    7.636062] [drm]   HPD1
[    7.636067] [drm]   DDC: 0x6430 0x6430 0x6434 0x6434 0x6438 0x6438 0x643c 0x643c
[    7.636069] [drm]   Encoders:
[    7.636072] [drm]     LCD1: INTERNAL_UNIPHY
[    7.636075] [drm] Connector 1:
[    7.636078] [drm]   HDMI-A-1
[    7.636080] [drm]   HPD2
[    7.636084] [drm]   DDC: 0x6440 0x6440 0x6444 0x6444 0x6448 0x6448 0x644c 0x644c
[    7.636086] [drm]   Encoders:
[    7.636088] [drm]     DFP1: INTERNAL_UNIPHY
[    7.636091] [drm] Connector 2:
[    7.636093] [drm]   VGA-1
[    7.636097] [drm]   DDC: 0x64d8 0x64d8 0x64dc 0x64dc 0x64e0 0x64e0 0x64e4 0x64e4
[    7.636099] [drm]   Encoders:
[    7.636102] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    7.636170] [drm] Internal thermal controller without fan control
[    7.636369] [drm] Found smc ucode version: 0x00010200
[    7.636649] [drm] radeon: dpm initialized
[    8.125295] [drm] fb mappable at 0x80477000
[    8.125306] [drm] vram apper at 0x80000000
[    8.125309] [drm] size 4325376
[    8.125312] [drm] fb depth is 24
[    8.125315] [drm]    pitch is 5632
[    8.132973] init: failsafe main process (566) killed by TERM signal
[    8.136795] fbcon: radeondrmfb (fb0) is primary device
[    8.188802] scsi 1:0:0:0: Direct-Access     Generic  2.0 Reader   -SD 1.00 PQ: 0 ANSI: 0 CCS
[    8.210600] acer_wmi: Acer Laptop ACPI-WMI Extras
[    8.210642] acer_wmi: Unable to detect available WMID devices
[    8.227033] acer_wmi: Acer Laptop ACPI-WMI Extras
[    8.235614] acer_wmi: Unable to detect available WMID devices
[    8.274463] scsi 1:0:0:1: Direct-Access     Generic  2.0 Reader   -MS 1.00 PQ: 0 ANSI: 0 CCS
[    8.275113] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    8.275977] sd 1:0:0:1: Attached scsi generic sg2 type 0
[    8.284926] sd 1:0:0:1: [sdc] Attached SCSI removable disk
[    8.287204] sd 1:0:0:0: [sdb] Attached SCSI removable disk
[    8.517468] cfg80211: World regulatory domain updated:
[    8.517470] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    8.517476] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.517478] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.517480] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    8.517482] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.517484] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.627649] Console: switching to colour frame buffer device 170x48
[    8.634496] radeon 0000:00:01.0: fb0: radeondrmfb frame buffer device
[    8.634498] radeon 0000:00:01.0: registered panic notifier
[    8.637955] [drm] Initialized radeon 2.36.0 20080528 for 0000:00:01.0 on minor 0
[    8.638448] hda-intel 0000:00:01.1: Using LPIB position fix
[    8.638526] snd_hda_intel 0000:00:01.1: irq 43 for MSI/MSI-X
[    8.657974] hda-intel 0000:00:01.1: Enable sync_write for stable communication
[    8.690652] HDMI ATI/AMD: no speaker allocation for ELD
[    8.690984] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.1/sound/card0/input12
[    8.692776] hda-intel 0000:00:14.2: Using LPIB position fix
[    8.711555] hda-intel 0000:00:14.2: Enable sync_write for stable communication
[    8.798841] SKU: Nid=0x1d sku_cfg=0x40179a2d
[    8.798856] SKU: port_connectivity=0x1
[    8.798859] SKU: enable_pcbeep=0x1
[    8.798862] SKU: check_sum=0x00000007
[    8.798865] SKU: customization=0x0000009a
[    8.798867] SKU: external_amp=0x5
[    8.798869] SKU: platform_type=0x1
[    8.798872] SKU: swap=0x0
[    8.798874] SKU: override=0x1
[    8.799649] autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[    8.799653]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    8.799662]    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[    8.799664]    mono: mono_out=0x0
[    8.799666]    inputs:
[    8.799670]      Mic=0x18
[    8.799674]      Internal Mic=0x12
[    8.799677] realtek: No valid SSID, checking pincfg 0x40179a2d for NID 0x1d
[    8.799680] realtek: Enabling init ASM_ID=0x9a2d CODEC_ID=10ec0269
[    8.911004] input: HDA ATI SB Headphone as /devices/pci0000:00/0000:00:14.2/sound/card1/input14
[    8.911605] input: HDA ATI SB Mic as /devices/pci0000:00/0000:00:14.2/sound/card1/input13
[    9.063478] atl1c 0000:01:00.0: irq 44 for MSI/MSI-X
[    9.080374] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    9.082348] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    9.174101] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    9.177503] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   10.281536] wlan0: authenticate with 00:22:3f:61:e4:c0
[   10.306054] wlan0: send auth to 00:22:3f:61:e4:c0 (try 1/3)
[   10.309516] wlan0: authenticated
[   10.318904] wlan0: AP has invalid WMM params (AIFSN=1 for ACI 2), disabling WMM
[   10.318920] ath9k 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   10.320545] wlan0: associate with 00:22:3f:61:e4:c0 (try 1/3)
[   10.324921] wlan0: RX AssocResp from 00:22:3f:61:e4:c0 (capab=0x431 status=0 aid=4)
[   10.325262] wlan0: associated
[   10.325315] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   12.320211] init: plymouth-upstart-bridge main process ended, respawning
[   14.954485] init: anacron main process (949) killed by TERM signal
[   25.101673] HDMI ATI/AMD: no speaker allocation for ELD
[   25.400738] HDMI ATI/AMD: no speaker allocation for ELD
[   25.701105] HDMI ATI/AMD: no speaker allocation for ELD
[   26.001424] HDMI ATI/AMD: no speaker allocation for ELD
[   26.301759] HDMI ATI/AMD: no speaker allocation for ELD
[   26.602091] HDMI ATI/AMD: no speaker allocation for ELD
[   26.902433] HDMI ATI/AMD: no speaker allocation for ELD
[   27.202824] HDMI ATI/AMD: no speaker allocation for ELD
[   27.503094] HDMI ATI/AMD: no speaker allocation for ELD
```

---

### Post by oldfred on 2014-07-09
I have seen this before. Not sure if frozen is the issue or the result of issues.
AT 3.81
 ata1.00: exception Emask 0x10 SAct 0x1 SErr 0x400000 action 0x6[COLOR=#ff0000] frozen[/COLOR]


 Hard drive info - will show locked frozen status or not, change sdd to your drive:
sudo hdparm -I /dev/sdd
sudo lshw -class disk
udisks --dump

see this for some info on reset under freeze.  
man hdparm 

> The --dco-freeze option will freeze/lock the current drive  configuration,
              thereby  preventing  software (or malware) from changing any DCO
              settings until after the next power-on reset.


---

### Post by leonixyz on 2014-07-10
```
/dev/sda:

ATA device, with non-removable media
	Model Number:       Samsung SSD 840 EVO 120GB               
	Serial Number:      S1D5NSAF397185R     
	Firmware Revision:  EXT0BB6Q
	Transport:          Serial, ATA8-AST, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6, SATA Rev 3.0
Standards:
	Used: unknown (minor revision code 0x0039) 
	Supported: 9 8 7 6 5 
	Likely used: 9
Configuration:
	Logical		max	current
	cylinders	16383	16383
	heads		16	16
	sectors/track	63	63
	--
	CHS current addressable sectors:   16514064
	LBA    user addressable sectors:  234441648
	LBA48  user addressable sectors:  234441648
	Logical  Sector size:                   512 bytes
	Physical Sector size:                   512 bytes
	Logical Sector-0 offset:                  0 bytes
	device size with M = 1024*1024:      114473 MBytes
	device size with M = 1000*1000:      120034 MBytes (120 GB)
	cache/buffer size  = unknown
	Nominal Media Rotation Rate: Solid State Device
Capabilities:
	LBA, IORDY(can be disabled)
	Queue depth: 32
	Standby timer values: spec'd by Standard, no device specific minimum
	R/W multiple sector transfer: Max = 1	Current = 1
	DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
	Enabled	Supported:
	   *	SMART feature set
	    	Security Mode feature set
	   *	Power Management feature set
	   *	Write cache
	   *	Look-ahead
	   *	Host Protected Area feature set
	   *	WRITE_BUFFER command
	   *	READ_BUFFER command
	   *	NOP cmd
	   *	DOWNLOAD_MICROCODE
	    	SET_MAX security extension
	   *	48-bit Address feature set
	   *	Device Configuration Overlay feature set
	   *	Mandatory FLUSH_CACHE
	   *	FLUSH_CACHE_EXT
	   *	SMART error logging
	   *	SMART self-test
	   *	General Purpose Logging feature set
	   *	WRITE_{DMA|MULTIPLE}_FUA_EXT
	   *	64-bit World wide name
	    	Write-Read-Verify feature set
	   *	WRITE_UNCORRECTABLE_EXT command
	   *	{READ,WRITE}_DMA_EXT_GPL commands
	   *	Segmented DOWNLOAD_MICROCODE
	   *	Gen1 signaling speed (1.5Gb/s)
	   *	Gen2 signaling speed (3.0Gb/s)
	   *	Gen3 signaling speed (6.0Gb/s)
	   *	Native Command Queueing (NCQ)
	   *	Phy event counters
	   *	READ_LOG_DMA_EXT equivalent to READ_LOG_EXT
	   *	DMA Setup Auto-Activate optimization
	    	Device-initiated interface power management
	   *	Asynchronous notification (eg. media change)
	   *	Software settings preservation
	   *	SMART Command Transport (SCT) feature set
	   *	SCT Write Same (AC2)
	   *	SCT Error Recovery Control (AC3)
	   *	SCT Features Control (AC4)
	   *	SCT Data Tables (AC5)
	   *	reserved 69[4]
	   *	DOWNLOAD MICROCODE DMA command
	   *	SET MAX SETPASSWORD/UNLOCK DMA commands
	   *	WRITE BUFFER DMA command
	   *	READ BUFFER DMA command
	   *	Data Set Management TRIM supported (limit 8 blocks)
Security: 
	Master password revision code = 65534
		supported
	not	enabled
	not	locked
	not	frozen
	not	expired: security count
		supported: enhanced erase
	2min for SECURITY ERASE UNIT. 8min for ENHANCED SECURITY ERASE UNIT. 
Logical Unit WWN Device Identifier: 50025388a02c56bf
	NAA		: 5
	IEEE OUI	: 002538
	Unique ID	: 8a02c56bf
Checksum: correct
```


```
  *-disk
       description: ATA Disk
       product: Samsung SSD 840
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: EXT0
       serial: S1D5NSAF397185R
       size: 111GiB (120GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 sectorsize=512 signature=00051044
  *-disk:0
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/sdb
       configuration: sectorsize=512
  *-disk:1
       description: SCSI Disk
       physical id: 0.0.1
       bus info: scsi@1:0.0.1
       logical name: /dev/sdc
       configuration: sectorsize=512
```



```
========================================================================
Showing information for /org/freedesktop/UDisks/devices/sda
  native-path:                 /sys/devices/pci0000:00/0000:00:11.0/ata1/host0/target0:0:0/0:0:0:0/block/sda
  device:                      8:0
  device-file:                 /dev/sda
    presentation:              /dev/sda
    by-id:                     /dev/disk/by-id/ata-Samsung_SSD_840_EVO_120GB_S1D5NSAF397185R
    by-id:                     /dev/disk/by-id/wwn-0x50025388a02c56bf
  detected at:                 ven 11 lug 2014 01:57:39 CEST
  system internal:             1
  removable:                   0
  has media:                   1 (detected at ven 11 lug 2014 01:57:39 CEST)
    detects change:            0
    detection by polling:      0
    detection inhibitable:     0
    detection inhibited:       0
  is read only:                0
  is mounted:                  0
  mount paths:             
  mounted by uid:              0
  presentation hide:           0
  presentation nopolicy:       0
  presentation name:           
  presentation icon:           
  automount hint:              
  size:                        120034123776
  block size:                  512
  job underway:                no
  usage:                       
  type:                        
  version:                     
  uuid:                        
  label:                       
  partition table:
    scheme:                    mbr
    count:                     3
  drive:
    vendor:                    ATA
    model:                     Samsung SSD 840 EVO 120GB
    revision:                  EXT0BB6Q
    serial:                    S1D5NSAF397185R
    WWN:                       50025388a02c56bf
    detachable:                0
    can spindown:              1
    rotational media:          No
    write-cache:               enabled
    ejectable:                 0
    adapter:                   Unknown
    ports:
    similar devices:
    media:                     
      compat:                 
    interface:                 ata
    if speed:                  (unknown)
    ATA SMART:                 Data not collected

========================================================================
Showing information for /org/freedesktop/UDisks/devices/sda1
  native-path:                 /sys/devices/pci0000:00/0000:00:11.0/ata1/host0/target0:0:0/0:0:0:0/block/sda/sda1
  device:                      8:1
  device-file:                 /dev/sda1
    presentation:              /dev/sda1
    by-id:                     /dev/disk/by-id/ata-Samsung_SSD_840_EVO_120GB_S1D5NSAF397185R-part1
    by-id:                     /dev/disk/by-id/wwn-0x50025388a02c56bf-part1
    by-id:                     /dev/disk/by-uuid/293807a0-018c-454f-ae3a-f195b67cf838
  detected at:                 ven 11 lug 2014 01:57:39 CEST
  system internal:             1
  removable:                   0
  has media:                   1 (detected at ven 11 lug 2014 01:57:39 CEST)
    detects change:            0
    detection by polling:      0
    detection inhibitable:     0
    detection inhibited:       0
  is read only:                0
  is mounted:                  1
  mount paths:             /
  mounted by uid:              0
  presentation hide:           0
  presentation nopolicy:       0
  presentation name:           
  presentation icon:           
  automount hint:              
  size:                        118310830080
  block size:                  512
  job underway:                no
  usage:                       filesystem
  type:                        ext4
  version:                     1.0
  uuid:                        293807a0-018c-454f-ae3a-f195b67cf838
  label:                       
  partition:
    part of:                   /org/freedesktop/UDisks/devices/sda
    scheme:                    mbr
    number:                    1
    type:                      0x83
    flags:                     boot
    offset:                    1048576
    alignment offset:          0
    size:                      118310830080
    label:                     
    uuid:                      

========================================================================
Showing information for /org/freedesktop/UDisks/devices/sda2
  native-path:                 /sys/devices/pci0000:00/0000:00:11.0/ata1/host0/target0:0:0/0:0:0:0/block/sda/sda2
  device:                      8:2
  device-file:                 /dev/sda2
    presentation:              /dev/sda2
    by-id:                     /dev/disk/by-id/ata-Samsung_SSD_840_EVO_120GB_S1D5NSAF397185R-part2
    by-id:                     /dev/disk/by-id/wwn-0x50025388a02c56bf-part2
  detected at:                 ven 11 lug 2014 01:57:39 CEST
  system internal:             1
  removable:                   0
  has media:                   1 (detected at ven 11 lug 2014 01:57:39 CEST)
    detects change:            0
    detection by polling:      0
    detection inhibitable:     0
    detection inhibited:       0
  is read only:                0
  is mounted:                  0
  mount paths:             
  mounted by uid:              0
  presentation hide:           0
  presentation nopolicy:       0
  presentation name:           
  presentation icon:           
  automount hint:              
  size:                        1024
  block size:                  512
  job underway:                no
  usage:                       
  type:                        
  version:                     
  uuid:                        
  label:                       
  partition:
    part of:                   /org/freedesktop/UDisks/devices/sda
    scheme:                    mbr
    number:                    2
    type:                      0x05
    flags:                    
    offset:                    118312926208
    alignment offset:          0
    size:                      1720714240
    label:                     
    uuid:                      

========================================================================
Showing information for /org/freedesktop/UDisks/devices/sda5
  native-path:                 /sys/devices/pci0000:00/0000:00:11.0/ata1/host0/target0:0:0/0:0:0:0/block/sda/sda5
  device:                      8:5
  device-file:                 /dev/sda5
    presentation:              /dev/sda5
    by-id:                     /dev/disk/by-id/ata-Samsung_SSD_840_EVO_120GB_S1D5NSAF397185R-part5
    by-id:                     /dev/disk/by-id/wwn-0x50025388a02c56bf-part5
    by-id:                     /dev/disk/by-uuid/2b81bfaa-b12d-4e3d-bd4f-784db5168e06
  detected at:                 ven 11 lug 2014 01:57:39 CEST
  system internal:             1
  removable:                   0
  has media:                   1 (detected at ven 11 lug 2014 01:57:39 CEST)
    detects change:            0
    detection by polling:      0
    detection inhibitable:     0
    detection inhibited:       0
  is read only:                0
  is mounted:                  0
  mount paths:             
  mounted by uid:              0
  presentation hide:           0
  presentation nopolicy:       0
  presentation name:           
  presentation icon:           
  automount hint:              
  size:                        1720713216
  block size:                  512
  job underway:                no
  usage:                       other
  type:                        swap
  version:                     2
  uuid:                        2b81bfaa-b12d-4e3d-bd4f-784db5168e06
  label:                       
  partition:
    part of:                   /org/freedesktop/UDisks/devices/sda
    scheme:                    mbr
    number:                    5
    type:                      0x82
    flags:                    
    offset:                    118312927232
    alignment offset:          0
    size:                      1720713216
    label:                     
    uuid:                      

========================================================================
Showing information for /org/freedesktop/UDisks/devices/sdb
  native-path:                 /sys/devices/pci0000:00/0000:00:13.2/usb2/2-5/2-5:1.0/host1/target1:0:0/1:0:0:0/block/sdb
  device:                      8:16
  device-file:                 /dev/sdb
    presentation:              /dev/sdb
    by-id:                     /dev/disk/by-id/usb-Generic_2.0_Reader_-SD_00000001-0:0
    by-path:                   /dev/disk/by-path/pci-0000:00:13.2-usb-0:5:1.0-scsi-0:0:0:0
  detected at:                 ven 11 lug 2014 01:57:39 CEST
  system internal:             0
  removable:                   1
  has media:                   0
    detects change:            1
    detection by polling:      1
    detection inhibitable:     1
    detection inhibited:       0
  is read only:                0
  is mounted:                  0
  mount paths:             
  mounted by uid:              0
  presentation hide:           0
  presentation nopolicy:       0
  presentation name:           
  presentation icon:           
  automount hint:              
  size:                        0
  block size:                  0
  job underway:                no
  usage:                       
  type:                        
  version:                     
  uuid:                        
  label:                       
  drive:
    vendor:                    Generic
    model:                     2.0 Reader   -SD
    revision:                  1.00
    serial:                    00000001
    WWN:                       
    detachable:                1
    can spindown:              0
    rotational media:          Yes, unknown rate
    write-cache:               unknown
    ejectable:                 0
    adapter:                   Unknown
    ports:
    similar devices:
    media:                     
      compat:                  flash_sd
    interface:                 usb
    if speed:                  480000000 bits/s
    ATA SMART:                 not available

========================================================================
Showing information for /org/freedesktop/UDisks/devices/sdc
  native-path:                 /sys/devices/pci0000:00/0000:00:13.2/usb2/2-5/2-5:1.0/host1/target1:0:0/1:0:0:1/block/sdc
  device:                      8:32
  device-file:                 /dev/sdc
    presentation:              /dev/sdc
    by-id:                     /dev/disk/by-id/usb-Generic_2.0_Reader_-MS_00000001-0:1
    by-path:                   /dev/disk/by-path/pci-0000:00:13.2-usb-0:5:1.0-scsi-0:0:0:1
  detected at:                 ven 11 lug 2014 01:57:39 CEST
  system internal:             0
  removable:                   1
  has media:                   0
    detects change:            1
    detection by polling:      1
    detection inhibitable:     1
    detection inhibited:       0
  is read only:                0
  is mounted:                  0
  mount paths:             
  mounted by uid:              0
  presentation hide:           0
  presentation nopolicy:       0
  presentation name:           
  presentation icon:           
  automount hint:              
  size:                        0
  block size:                  0
  job underway:                no
  usage:                       
  type:                        
  version:                     
  uuid:                        
  label:                       
  drive:
    vendor:                    Generic
    model:                     2.0 Reader   -MS
    revision:                  1.00
    serial:                    00000001
    WWN:                       
    detachable:                1
    can spindown:              0
    rotational media:          Yes, unknown rate
    write-cache:               unknown
    ejectable:                 0
    adapter:                   Unknown
    ports:
    similar devices:
    media:                     
      compat:                 
    interface:                 usb
    if speed:                  480000000 bits/s
    ATA SMART:                 not available

========================================================================
```

---

### Post by oldfred on 2014-07-10
The only setting I know is that is does not now say frozen.
Any difference in booting?

Is Sony UEFI based but you are booting with BIOS and MBR(msdos) partitions?

---

### Post by leonixyz on 2014-07-12
> **oldfred said:**
> The only setting I know is that is does not now say frozen.
Any difference in booting?

Is Sony UEFI based but you are booting with BIOS and MBR(msdos) partitions?

I don't know, how do I check that?

---

### Post by oldfred on 2014-07-12
From live installer run BootInfo report and post link:

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

