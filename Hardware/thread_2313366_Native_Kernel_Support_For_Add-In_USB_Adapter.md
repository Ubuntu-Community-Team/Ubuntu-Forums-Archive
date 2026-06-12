---
title: "Native Kernel Support For Add-In USB Adapter?"
date: 2016-02-11
forum: Hardware
---

### Post by kazz2 on 2016-02-11
I have successfully built an Ubuntu Server 14.04.3 LTS from an EVGA 790i Ultra SLI motherboard with 8GB of RAM and a total of five SATA2-connected hard drives. Four of the hard drives (Hitachi Deskstar 3TBs) are in a zpool RAIDZ array. I installed a Highpoint U1322A USB3 adapter as part of the build. However an lsusb command only lists USB 1.1 and USB 2.0 buses. I've plugged a USB key into one of the USB 3.0 slots and have seen no information through lsusb nor fdisk -l so I don't believe the OS knows it's there at all.

Based on that, I inquired of the mfr about drivers and installation instructions. The reply was, "[COLOR=#000000][FONT=tahoma]The card doesn\'t have extra driver since it is native kernel support."

I'm a Linux/Ubuntu noob so I thought I'd humbly post the issue here and ask if anyone knows how I can get my build to see the adapter.

Thanks!
[/FONT][/COLOR]

---

### Post by alexandari on 2016-02-12
What does **dmesg** say when plugging it in?

---

### Post by kazz2 on 2016-02-12
That is a huge amount of output!

dmesg output no USB key installed:

```
[    0.000000] Initializing cgroup subsys cpuset[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.19.0-49-generic (buildd@lgw01-08) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #55~14.04.1-Ubuntu SMP Fri Jan 22 11:24:31 UTC 2016 (Ubuntu 3.19.0-49.55~14.04.1-generic 3.19.8-ckt12)
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.19.0-49-generic root=/dev/mapper/kazz--u0a1--vg-root ro nomdmonddf nomdmonisw
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009b7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009b800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000bfeeffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bfef0000-0x00000000bfef2fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bfef3000-0x00000000bfefffff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000023fffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.4 present.
[    0.000000] DMI:  EVGA  132-CK-NF79/132-CK-NF79, BIOS   P10  12/30/2009
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] AGP: No AGP bridge found
[    0.000000] e820: last_pfn = 0x240000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CBFFF write-protect
[    0.000000]   CC000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask E00000000 write-back
[    0.000000]   1 base 200000000 mask FC0000000 write-back
[    0.000000]   2 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   3 base 0BFF00000 mask FFFF00000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- UC
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 8GB, type WB
[    0.000000] reg 1, base: 8GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 1GB, type UC
[    0.000000] reg 3, base: 3071MB, range: 1MB, type UC
[    0.000000] total RAM covered: 8191M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K  chunk_size: 2M  num_reg: 5      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3071MB, range: 1MB, type UC
[    0.000000] reg 3, base: 4GB, range: 4GB, type WB
[    0.000000] reg 4, base: 8GB, range: 1GB, type WB
[    0.000000] e820: update [mem 0xbff00000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xbfef0 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000f3fd0-0x000f3fdf] mapped at [ffff8800000f3fd0]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000095000] 95000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fd4000, 0x01fd4fff] PGTABLE
[    0.000000] BRK [0x01fd5000, 0x01fd5fff] PGTABLE
[    0.000000] BRK [0x01fd6000, 0x01fd6fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x23fe00000-0x23fffffff]
[    0.000000]  [mem 0x23fe00000-0x23fffffff] page 2M
[    0.000000] BRK [0x01fd7000, 0x01fd7fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x220000000-0x23fdfffff]
[    0.000000]  [mem 0x220000000-0x23fdfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0xbfeeffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0xbfdfffff] page 2M
[    0.000000]  [mem 0xbfe00000-0xbfeeffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x21fffffff]
[    0.000000]  [mem 0x100000000-0x21fffffff] page 2M
[    0.000000] BRK [0x01fd8000, 0x01fd8fff] PGTABLE
[    0.000000] BRK [0x01fd9000, 0x01fd9fff] PGTABLE
[    0.000000] RAMDISK: [mem 0x34cc8000-0x3665bfff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000000F7FA0 000014 (v00 Nvidia)
[    0.000000] ACPI: RSDT 0x00000000BFEF3040 00003C (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
[    0.000000] ACPI: FACP 0x00000000BFEF30C0 000074 (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
[    0.000000] ACPI: DSDT 0x00000000BFEF3180 005447 (v01 NVIDIA NVDAACPI 00001000 MSFT 03000000)
[    0.000000] ACPI: FACS 0x00000000BFEF0000 000040
[    0.000000] ACPI: HPET 0x00000000BFEF8740 000038 (v01 Nvidia NVDAACPI 42302E31 NVDA 00000098)
[    0.000000] ACPI: WDRT 0x00000000BFEF87C0 000047 (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
[    0.000000] ACPI: MCFG 0x00000000BFEF8880 00003C (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
[    0.000000] ACPI: APIC 0x00000000BFEF8640 000098 (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
[    0.000000] ACPI: OEMN 0x00000000BFEF8900 004AED (v01 NVIDIA NTUNEOEM 20302E31 NVDA 00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000023fffffff]
[    0.000000] NODE_DATA(0) allocated [mem 0x23fff6000-0x23fffafff]
[    0.000000]  [ffffea0000000000-ffffea0008ffffff] PMD -> [ffff880237600000-ffff88023f5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x23fffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009afff]
[    0.000000]   node   0: [mem 0x00100000-0xbfeeffff]
[    0.000000]   node   0: [mem 0x100000000-0x23fffffff]
[    0.000000] Initmem setup node 0 [mem 0x00001000-0x23fffffff]
[    0.000000] On node 0 totalpages: 2096778
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3994 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 12220 pages used for memmap
[    0.000000]   DMA32 zone: 782064 pages, LIFO batch:31
[    0.000000]   Normal zone: 20480 pages used for memmap
[    0.000000]   Normal zone: 1310720 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
[    0.000000] smpboot: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009b000-0x0009bfff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009c000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000effff]
[    0.000000] PM: Registered nosave memory: [mem 0x000f0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xbfef0000-0xbfef2fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbfef3000-0xbfefffff]
[    0.000000] PM: Registered nosave memory: [mem 0xbff00000-0xdfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xffffffff]
[    0.000000] e820: [mem 0xbff00000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 31 pages/cpu @ffff88023fc00000 s86144 r8192 d32640 u524288
[    0.000000] pcpu-alloc: s86144 r8192 d32640 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 2063993
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.19.0-49-generic root=/dev/mapper/kazz--u0a1--vg-root ro nomdmonddf nomdmonisw
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x3, cntxt size 0x240 using standard form
[    0.000000] AGP: Checking aperture...
[    0.000000] AGP: No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 8146696K/8387112K available (7923K kernel code, 1174K rwdata, 3760K rodata, 1408K init, 1292K bss, 240416K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]  RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]  RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=4
[    0.000000] NR_IRQS:16640 nr_irqs:456 16
[    0.000000]  Offload RCU callbacks from all CPUs
[    0.000000]  Offload RCU callbacks from CPUs: 0-3.
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 2999.914 MHz processor
[    0.004009] Calibrating delay loop (skipped), value calculated using timer frequency.. 5999.82 BogoMIPS (lpj=11999656)
[    0.004014] pid_max: default: 32768 minimum: 301
[    0.004021] ACPI: Core revision 20141107
[    0.010117] ACPI: All ACPI Tables successfully acquired
[    0.010140] Security Framework initialized
[    0.010160] AppArmor: AppArmor initialized
[    0.010162] Yama: becoming mindful.
[    0.010684] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.014009] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.015415] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.015428] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.015738] Initializing cgroup subsys memory
[    0.015748] Initializing cgroup subsys devices
[    0.015752] Initializing cgroup subsys freezer
[    0.015756] Initializing cgroup subsys net_cls
[    0.015759] Initializing cgroup subsys blkio
[    0.015762] Initializing cgroup subsys perf_event
[    0.015766] Initializing cgroup subsys net_prio
[    0.015769] Initializing cgroup subsys hugetlb
[    0.015792] CPU: Physical Processor ID: 0
[    0.015794] CPU: Processor Core ID: 0
[    0.015796] mce: CPU supports 6 MCE banks
[    0.015803] CPU0: Thermal monitoring enabled (TM1)
[    0.015807] process: using mwait in idle threads
[    0.015812] Last level iTLB entries: 4KB 128, 2MB 4, 4MB 4
[    0.015812] Last level dTLB entries: 4KB 256, 2MB 0, 4MB 32, 1GB 0
[    0.015899] Freeing SMP alternatives memory: 32K (ffffffff81e87000 - ffffffff81e8f000)
[    0.019413] ftrace: allocating 30034 entries in 118 pages
[    0.028537] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.071795] smpboot: CPU0: Intel(R) Core(TM)2 Quad CPU    Q9650  @ 3.00GHz (fam: 06, model: 17, stepping: 0a)
[    0.072000] Performance Events: PEBS fmt0+, 4-deep LBR, Core2 events, Intel PMU driver.
[    0.072000] ... version:                2
[    0.072000] ... bit width:              40
[    0.072000] ... generic registers:      2
[    0.072000] ... value mask:             000000ffffffffff
[    0.072000] ... max period:             000000007fffffff
[    0.072000] ... fixed-purpose events:   3
[    0.072000] ... event mask:             0000000700000003
[    0.072000] x86: Booting SMP configuration:
[    0.072000] .... node  #0, CPUs:      #1
[    0.082142] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.082251]  #2 #3
[    0.108028] x86: Booted up 1 node, 4 CPUs
[    0.108035] smpboot: Total of 4 processors activated (23999.31 BogoMIPS)
[    0.112137] devtmpfs: initialized
[    0.116739] evm: security.selinux
[    0.116741] evm: security.SMACK64
[    0.116743] evm: security.SMACK64EXEC
[    0.116744] evm: security.SMACK64TRANSMUTE
[    0.116746] evm: security.SMACK64MMAP
[    0.116747] evm: security.ima
[    0.116749] evm: security.capability
[    0.116763] PM: Registering ACPI NVS region [mem 0xbfef0000-0xbfef2fff] (12288 bytes)
[    0.116763] pinctrl core: initialized pinctrl subsystem
[    0.116763] RTC time:  2:09:03, date: 02/12/16
[    0.116763] NET: Registered protocol family 16
[    0.124006] cpuidle: using governor ladder
[    0.128006] cpuidle: using governor menu
[    0.128062] ACPI: bus type PCI registered
[    0.128066] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.128160] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.128171] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.128515] PCI: Using configuration type 1 for base access
[    0.132125] ACPI: Added _OSI(Module Device)
[    0.132128] ACPI: Added _OSI(Processor Device)
[    0.132135] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.132137] ACPI: Added _OSI(Processor Aggregator Device)
[    0.136469] ACPI: Interpreter enabled
[    0.136475] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20141107/hwxface-580)
[    0.136481] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20141107/hwxface-580)
[    0.136493] ACPI: (supports S0 S3 S4 S5)
[    0.136495] ACPI: Using IOAPIC for interrupt routing
[    0.136586] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.136604] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.141446] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.141453] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.141543] acpi PNP0A08:00: _OSC: platform does not support [PCIeHotplug]
[    0.141628] acpi PNP0A08:00: _OSC: OS now controls [PME AER PCIeCapability]
[    0.141875] PCI host bridge to bus 0000:00
[    0.141880] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.141883] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.141886] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.141888] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.141891] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000dffff]
[    0.141893] pci_bus 0000:00: root bus resource [mem 0xbff00000-0xfebfffff]
[    0.141904] pci 0000:00:00.0: [10de:0800] type 00 class 0x060000
[    0.142018] pci 0000:00:00.1: [10de:0808] type 00 class 0x050000
[    0.142129] pci 0000:00:00.2: [10de:0809] type 00 class 0x050000
[    0.142237] pci 0000:00:00.3: [10de:080a] type 00 class 0x050000
[    0.142356] pci 0000:00:00.4: [10de:080b] type 00 class 0x050000
[    0.142475] pci 0000:00:00.5: [10de:080c] type 00 class 0x050000
[    0.142574] pci 0000:00:00.6: [10de:080d] type 00 class 0x050000
[    0.142681] pci 0000:00:00.7: [10de:080e] type 00 class 0x050000
[    0.142788] pci 0000:00:01.0: [10de:080f] type 00 class 0x050000
[    0.142887] pci 0000:00:01.1: [10de:0810] type 00 class 0x050000
[    0.142985] pci 0000:00:01.2: [10de:0811] type 00 class 0x050000
[    0.143083] pci 0000:00:01.3: [10de:0812] type 00 class 0x050000
[    0.143191] pci 0000:00:01.4: [10de:0813] type 00 class 0x050000
[    0.143289] pci 0000:00:01.5: [10de:0814] type 00 class 0x050000
[    0.143387] pci 0000:00:01.6: [10de:081a] type 00 class 0x050000
[    0.143506] pci 0000:00:01.7: [10de:080e] type 00 class 0x050000
[    0.143625] pci 0000:00:02.0: [10de:0815] type 01 class 0x060400
[    0.143708] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.143760] pci 0000:00:02.0: System wakeup disabled by ACPI
[    0.143821] pci 0000:00:04.0: [10de:0817] type 01 class 0x060400
[    0.143898] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.143950] pci 0000:00:04.0: System wakeup disabled by ACPI
[    0.144024] pci 0000:00:09.0: [10de:0369] type 00 class 0x050000
[    0.144271] pci 0000:00:0a.0: [10de:0360] type 00 class 0x060100
[    0.144280] pci 0000:00:0a.0: reg 0x10: [io  0xfc00-0xfc7f]
[    0.144381] pci 0000:00:0a.1: [10de:0368] type 00 class 0x0c0500
[    0.144395] pci 0000:00:0a.1: reg 0x10: [io  0xf800-0xf83f]
[    0.144417] pci 0000:00:0a.1: reg 0x20: [io  0xf400-0xf43f]
[    0.144424] pci 0000:00:0a.1: reg 0x24: [io  0xf000-0xf03f]
[    0.144461] pci 0000:00:0a.1: PME# supported from D3hot D3cold
[    0.144548] pci 0000:00:0b.0: [10de:036c] type 00 class 0x0c0310
[    0.144558] pci 0000:00:0b.0: reg 0x10: [mem 0xdffff000-0xdfffffff]
[    0.144602] pci 0000:00:0b.0: supports D1 D2
[    0.144604] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.144646] pci 0000:00:0b.0: System wakeup disabled by ACPI
[    0.144686] pci 0000:00:0b.1: [10de:036d] type 00 class 0x0c0320
[    0.144697] pci 0000:00:0b.1: reg 0x10: [mem 0xdfffe000-0xdfffe0ff]
[    0.144744] pci 0000:00:0b.1: supports D1 D2
[    0.144745] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.144800] pci 0000:00:0b.1: System wakeup disabled by ACPI
[    0.144849] pci 0000:00:0d.0: [10de:036e] type 00 class 0x01018a
[    0.144873] pci 0000:00:0d.0: reg 0x20: [io  0xec00-0xec0f]
[    0.144883] pci 0000:00:0d.0: legacy IDE quirk: reg 0x10: [io  0x01f0-0x01f7]
[    0.144886] pci 0000:00:0d.0: legacy IDE quirk: reg 0x14: [io  0x03f6]
[    0.144889] pci 0000:00:0d.0: legacy IDE quirk: reg 0x18: [io  0x0170-0x0177]
[    0.144891] pci 0000:00:0d.0: legacy IDE quirk: reg 0x1c: [io  0x0376]
[    0.144978] pci 0000:00:0e.0: [10de:037f] type 00 class 0x010185
[    0.144990] pci 0000:00:0e.0: reg 0x10: [io  0x09f0-0x09f7]
[    0.144995] pci 0000:00:0e.0: reg 0x14: [io  0x0bf0-0x0bf3]
[    0.145001] pci 0000:00:0e.0: reg 0x18: [io  0x0970-0x0977]
[    0.145006] pci 0000:00:0e.0: reg 0x1c: [io  0x0b70-0x0b73]
[    0.145011] pci 0000:00:0e.0: reg 0x20: [io  0xd800-0xd80f]
[    0.145017] pci 0000:00:0e.0: reg 0x24: [mem 0xdfffd000-0xdfffdfff]
[    0.145117] pci 0000:00:0e.1: [10de:037f] type 00 class 0x010185
[    0.145128] pci 0000:00:0e.1: reg 0x10: [io  0x09e0-0x09e7]
[    0.145134] pci 0000:00:0e.1: reg 0x14: [io  0x0be0-0x0be3]
[    0.145139] pci 0000:00:0e.1: reg 0x18: [io  0x0960-0x0967]
[    0.145145] pci 0000:00:0e.1: reg 0x1c: [io  0x0b60-0x0b63]
[    0.145150] pci 0000:00:0e.1: reg 0x20: [io  0xc400-0xc40f]
[    0.145156] pci 0000:00:0e.1: reg 0x24: [mem 0xdfffc000-0xdfffcfff]
[    0.145255] pci 0000:00:0e.2: [10de:037f] type 00 class 0x010185
[    0.145267] pci 0000:00:0e.2: reg 0x10: [io  0xc000-0xc007]
[    0.145272] pci 0000:00:0e.2: reg 0x14: [io  0xbc00-0xbc03]
[    0.145278] pci 0000:00:0e.2: reg 0x18: [io  0xb800-0xb807]
[    0.145283] pci 0000:00:0e.2: reg 0x1c: [io  0xb400-0xb403]
[    0.145288] pci 0000:00:0e.2: reg 0x20: [io  0xb000-0xb00f]
[    0.145294] pci 0000:00:0e.2: reg 0x24: [mem 0xdfffb000-0xdfffbfff]
[    0.145398] pci 0000:00:0f.0: [10de:0370] type 01 class 0x060401
[    0.145469] pci 0000:00:0f.0: System wakeup disabled by ACPI
[    0.145511] pci 0000:00:0f.1: [10de:0371] type 00 class 0x040300
[    0.145523] pci 0000:00:0f.1: reg 0x10: [mem 0xdfff0000-0xdfff3fff]
[    0.145576] pci 0000:00:0f.1: PME# supported from D3hot D3cold
[    0.145620] pci 0000:00:0f.1: System wakeup disabled by ACPI
[    0.145673] pci 0000:00:11.0: [10de:0373] type 00 class 0x068000
[    0.145687] pci 0000:00:11.0: reg 0x10: [mem 0xdfffa000-0xdfffafff]
[    0.145692] pci 0000:00:11.0: reg 0x14: [io  0xac00-0xac07]
[    0.145698] pci 0000:00:11.0: reg 0x18: [mem 0xdfff9000-0xdfff90ff]
[    0.145703] pci 0000:00:11.0: reg 0x1c: [mem 0xdfff8000-0xdfff800f]
[    0.145748] pci 0000:00:11.0: supports D1 D2
[    0.145750] pci 0000:00:11.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.145796] pci 0000:00:11.0: System wakeup disabled by ACPI
[    0.145840] pci 0000:00:12.0: [10de:0373] type 00 class 0x068000
[    0.145863] pci 0000:00:12.0: reg 0x10: [mem 0xdfff7000-0xdfff7fff]
[    0.145869] pci 0000:00:12.0: reg 0x14: [io  0xa800-0xa807]
[    0.145875] pci 0000:00:12.0: reg 0x18: [mem 0xdfff6000-0xdfff60ff]
[    0.145880] pci 0000:00:12.0: reg 0x1c: [mem 0xdfff5000-0xdfff500f]
[    0.145925] pci 0000:00:12.0: supports D1 D2
[    0.145927] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.145974] pci 0000:00:12.0: System wakeup disabled by ACPI
[    0.146019] pci 0000:00:15.0: [10de:0374] type 01 class 0x060400
[    0.146065] pci 0000:00:15.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.146109] pci 0000:00:15.0: System wakeup disabled by ACPI
[    0.146221] pci 0000:01:00.0: [10de:0191] type 00 class 0x030000
[    0.146230] pci 0000:01:00.0: reg 0x10: [mem 0xdc000000-0xdcffffff]
[    0.146238] pci 0000:01:00.0: reg 0x14: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.146247] pci 0000:01:00.0: reg 0x1c: [mem 0xda000000-0xdbffffff 64bit]
[    0.146253] pci 0000:01:00.0: reg 0x24: [io  0x9c00-0x9c7f]
[    0.146259] pci 0000:01:00.0: reg 0x30: [mem 0x00000000-0x0001ffff pref]
[    0.146323] pci 0000:01:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.146332] pci 0000:00:02.0: PCI bridge to [bus 01]
[    0.146338] pci 0000:00:02.0:   bridge window [io  0x9000-0x9fff]
[    0.146341] pci 0000:00:02.0:   bridge window [mem 0xda000000-0xddffffff]
[    0.146347] pci 0000:00:02.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.146408] pci 0000:00:04.0: PCI bridge to [bus 02]
[    0.146477] pci 0000:00:0f.0: PCI bridge to [bus 03] (subtractive decode)
[    0.146483] pci 0000:00:0f.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.146485] pci 0000:00:0f.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.146486] pci 0000:00:0f.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.146488] pci 0000:00:0f.0:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
[    0.146490] pci 0000:00:0f.0:   bridge window [mem 0xbff00000-0xfebfffff] (subtractive decode)
[    0.146545] pci 0000:04:00.0: [197b:2363] type 00 class 0x010601
[    0.146616] pci 0000:04:00.0: reg 0x24: [mem 0xdfefe000-0xdfefffff]
[    0.146672] pci 0000:04:00.0: PME# supported from D3hot
[    0.146728] pci 0000:04:00.1: [197b:2363] type 00 class 0x010185
[    0.146745] pci 0000:04:00.1: reg 0x10: [io  0x8c00-0x8c07]
[    0.146753] pci 0000:04:00.1: reg 0x14: [io  0x8800-0x8803]
[    0.146761] pci 0000:04:00.1: reg 0x18: [io  0x8400-0x8407]
[    0.146769] pci 0000:04:00.1: reg 0x1c: [io  0x8000-0x8003]
[    0.146778] pci 0000:04:00.1: reg 0x20: [io  0x7c00-0x7c0f]
[    0.146867] pci 0000:04:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.146876] pci 0000:00:15.0: PCI bridge to [bus 04]
[    0.146880] pci 0000:00:15.0:   bridge window [io  0x7000-0x8fff]
[    0.146883] pci 0000:00:15.0:   bridge window [mem 0xdfe00000-0xdfefffff]
[    0.147271] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.147317] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.147361] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.147406] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.147451] ACPI: PCI Interrupt Link [LXV5] (IRQs 5 7 9 10 *11 14 15)
[    0.147495] ACPI: PCI Interrupt Link [LXV6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.147540] ACPI: PCI Interrupt Link [LXV7] (IRQs 5 7 9 10 *11 14 15)
[    0.147583] ACPI: PCI Interrupt Link [LXV8] (IRQs 5 7 9 *10 11 14 15)
[    0.147627] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 10 *11 14 15)
[    0.147671] ACPI: PCI Interrupt Link [LMC1] (IRQs *5 7 9 10 11 14 15)
[    0.147715] ACPI: PCI Interrupt Link [LMAC] (IRQs *5 7 9 10 11 14 15)
[    0.147764] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 *10 11 14 15)
[    0.147808] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.147852] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 *10 11 14 15)
[    0.147896] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.147941] ACPI: PCI Interrupt Link [LSA0] (IRQs 5 7 9 10 *11 14 15)
[    0.148002] ACPI: PCI Interrupt Link [LSA1] (IRQs 5 7 9 10 *11 14 15)
[    0.148052] ACPI: PCI Interrupt Link [LSA2] (IRQs 5 7 9 *10 11 14 15)
[    0.148124] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[    0.148191] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[    0.148256] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[    0.148320] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[    0.148384] ACPI: PCI Interrupt Link [AXV5] (IRQs 16) *0, disabled.
[    0.148448] ACPI: PCI Interrupt Link [AXV6] (IRQs 16) *0, disabled.
[    0.148512] ACPI: PCI Interrupt Link [AXV7] (IRQs 16) *0, disabled.
[    0.148576] ACPI: PCI Interrupt Link [AXV8] (IRQs 16) *0, disabled.
[    0.148640] ACPI: PCI Interrupt Link [AUBA] (IRQs 22 23) *0, disabled.
[    0.148705] ACPI: PCI Interrupt Link [AMA1] (IRQs 22 23) *0, disabled.
[    0.148770] ACPI: PCI Interrupt Link [AMAC] (IRQs 22 23) *0, disabled.
[    0.148834] ACPI: PCI Interrupt Link [AAZA] (IRQs 22 23) *0, disabled.
[    0.148899] ACPI: PCI Interrupt Link [AACI] (IRQs 22 23) *0, disabled.
[    0.148963] ACPI: PCI Interrupt Link [AMCI] (IRQs 22 23) *0, disabled.
[    0.149027] ACPI: PCI Interrupt Link [ASMB] (IRQs 22 23) *0, disabled.
[    0.149091] ACPI: PCI Interrupt Link [AUS2] (IRQs 22 23) *0, disabled.
[    0.149156] ACPI: PCI Interrupt Link [AIDE] (IRQs 22 23) *0, disabled.
[    0.149220] ACPI: PCI Interrupt Link [ASA0] (IRQs 20 21) *0, disabled.
[    0.149285] ACPI: PCI Interrupt Link [ASA1] (IRQs 20 21) *0, disabled.
[    0.149349] ACPI: PCI Interrupt Link [ASA2] (IRQs 20 21) *0, disabled.
[    0.149464] vgaarb: setting as boot device: PCI:0000:01:00.0
[    0.149464] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.149464] vgaarb: loaded
[    0.149464] vgaarb: bridge control possible 0000:01:00.0
[    0.149464] SCSI subsystem initialized
[    0.149464] libata version 3.00 loaded.
[    0.149464] ACPI: bus type USB registered
[    0.149464] usbcore: registered new interface driver usbfs
[    0.149464] usbcore: registered new interface driver hub
[    0.149464] usbcore: registered new device driver usb
[    0.149464] PCI: Using ACPI for IRQ routing
[    0.156636] PCI: pci_cache_line_size set to 64 bytes
[    0.156702] e820: reserve RAM buffer [mem 0x0009b800-0x0009ffff]
[    0.156703] e820: reserve RAM buffer [mem 0xbfef0000-0xbfffffff]
[    0.156800] NetLabel: Initializing
[    0.156802] NetLabel:  domain hash size = 128
[    0.156804] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.156816] NetLabel:  unlabeled traffic allowed by default
[    0.156843] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.156843] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
[    0.156843] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.160040] Switched to clocksource hpet
[    0.166391] AppArmor: AppArmor Filesystem Enabled
[    0.166459] pnp: PnP ACPI init
[    0.166551] system 00:00: [io  0x1000-0x107f] could not be reserved
[    0.166555] system 00:00: [io  0x1080-0x10ff] has been reserved
[    0.166558] system 00:00: [io  0x1400-0x147f] has been reserved
[    0.166560] system 00:00: [io  0x1480-0x14ff] has been reserved
[    0.166563] system 00:00: [io  0x1800-0x187f] has been reserved
[    0.166565] system 00:00: [io  0x1880-0x18ff] has been reserved
[    0.166569] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.166676] system 00:01: [io  0x04d0-0x04d1] has been reserved
[    0.166679] system 00:01: [io  0x0295-0x0314] has been reserved
[    0.166682] system 00:01: [io  0x0880-0x088f] has been reserved
[    0.166685] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.166738] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.166898] pnp 00:03: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.167362] system 00:04: [mem 0xe0000000-0xefffffff] has been reserved
[    0.167366] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.167488] system 00:05: [mem 0x000d0000-0x000d3fff] has been reserved
[    0.167492] system 00:05: [mem 0x000d9000-0x000dbfff] has been reserved
[    0.167495] system 00:05: [mem 0x000f0000-0x000fbfff] could not be reserved
[    0.167497] system 00:05: [mem 0x000fc000-0x000fffff] could not be reserved
[    0.167500] system 00:05: [mem 0xbfef0000-0xbfefffff] could not be reserved
[    0.167503] system 00:05: [mem 0xffff0000-0xffffffff] has been reserved
[    0.167506] system 00:05: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.167509] system 00:05: [mem 0x00100000-0xbfeeffff] could not be reserved
[    0.167511] system 00:05: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.167514] system 00:05: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.167517] system 00:05: [mem 0xfeff0000] has been reserved
[    0.167520] system 00:05: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.167528] pnp: PnP ACPI: found 6 devices
[    0.176252] pci 0000:01:00.0: BAR 6: assigned [mem 0xdd000000-0xdd01ffff pref]
[    0.176257] pci 0000:00:02.0: PCI bridge to [bus 01]
[    0.176260] pci 0000:00:02.0:   bridge window [io  0x9000-0x9fff]
[    0.176266] pci 0000:00:02.0:   bridge window [mem 0xda000000-0xddffffff]
[    0.176270] pci 0000:00:02.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.176277] pci 0000:00:04.0: PCI bridge to [bus 02]
[    0.176287] pci 0000:00:0f.0: PCI bridge to [bus 03]
[    0.176294] pci 0000:00:15.0: PCI bridge to [bus 04]
[    0.176297] pci 0000:00:15.0:   bridge window [io  0x7000-0x8fff]
[    0.176301] pci 0000:00:15.0:   bridge window [mem 0xdfe00000-0xdfefffff]
[    0.176307] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.176309] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.176311] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.176312] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000dffff]
[    0.176314] pci_bus 0000:00: resource 8 [mem 0xbff00000-0xfebfffff]
[    0.176316] pci_bus 0000:01: resource 0 [io  0x9000-0x9fff]
[    0.176317] pci_bus 0000:01: resource 1 [mem 0xda000000-0xddffffff]
[    0.176319] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.176321] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.176323] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.176324] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.176326] pci_bus 0000:03: resource 7 [mem 0x000c0000-0x000dffff]
[    0.176328] pci_bus 0000:03: resource 8 [mem 0xbff00000-0xfebfffff]
[    0.176329] pci_bus 0000:04: resource 0 [io  0x7000-0x8fff]
[    0.176331] pci_bus 0000:04: resource 1 [mem 0xdfe00000-0xdfefffff]
[    0.176356] NET: Registered protocol family 2
[    0.176570] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
[    0.176822] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.177169] TCP: Hash tables configured (established 65536 bind 65536)
[    0.177211] TCP: reno registered
[    0.177222] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.177273] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.177352] NET: Registered protocol family 1
[    0.177689] ACPI: PCI Interrupt Link [AUBA] enabled at IRQ 23
[    0.248354] ACPI: PCI Interrupt Link [AUS2] enabled at IRQ 22
[    0.248568] pci 0000:01:00.0: Video device with shadowed ROM
[    0.248571] pci 0000:04:00.0: async suspend disabled to avoid multi-function power-on ordering issue
[    0.248577] pci 0000:04:00.1: async suspend disabled to avoid multi-function power-on ordering issue
[    0.248581] PCI: CLS 64 bytes, default 64
[    0.248632] Trying to unpack rootfs image as initramfs...
[    0.631888] Freeing initrd memory: 26192K (ffff880034cc8000 - ffff88003665c000)
[    0.631930] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.631933] software IO TLB [mem 0xbbef0000-0xbfef0000] (64MB) mapped at [ffff8800bbef0000-ffff8800bfeeffff]
[    0.632246] microcode: CPU0 sig=0x1067a, pf=0x10, revision=0xa07
[    0.632262] microcode: CPU1 sig=0x1067a, pf=0x10, revision=0xa07
[    0.632281] microcode: CPU2 sig=0x1067a, pf=0x10, revision=0xa07
[    0.632298] microcode: CPU3 sig=0x1067a, pf=0x10, revision=0xa07
[    0.632376] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.632427] Scanning for low memory corruption every 60 seconds
[    0.632703] futex hash table entries: 1024 (order: 4, 65536 bytes)
[    0.632721] Initialise system trusted keyring
[    0.632741] audit: initializing netlink subsys (disabled)
[    0.632760] audit: type=2000 audit(1455242943.632:1): initialized
[    0.633071] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.634737] zpool: loaded
[    0.634740] zbud: loaded
[    0.634903] VFS: Disk quotas dquot_6.5.2
[    0.634938] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.635448] fuse init (API version 7.23)
[    0.635592] Key type big_key registered
[    0.636463] Key type asymmetric registered
[    0.636467] Asymmetric key parser 'x509' registered
[    0.636507] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.636585] io scheduler noop registered
[    0.636588] io scheduler deadline registered (default)
[    0.636620] io scheduler cfq registered
[    0.636923] ACPI: PCI Interrupt Link [AXV5] enabled at IRQ 16
[    0.637194] ACPI: PCI Interrupt Link [AXV6] enabled at IRQ 16
[    0.637370] pcieport 0000:00:02.0: Signaling PME through PCIe PME interrupt
[    0.637373] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    0.637378] pcie_pme 0000:00:02.0:pcie01: service driver pcie_pme loaded
[    0.637396] pcieport 0000:00:04.0: Signaling PME through PCIe PME interrupt
[    0.637401] pcie_pme 0000:00:04.0:pcie01: service driver pcie_pme loaded
[    0.637414] pcieport 0000:00:15.0: Signaling PME through PCIe PME interrupt
[    0.637417] pci 0000:04:00.0: Signaling PME through PCIe PME interrupt
[    0.637419] pci 0000:04:00.1: Signaling PME through PCIe PME interrupt
[    0.637423] pcie_pme 0000:00:15.0:pcie01: service driver pcie_pme loaded
[    0.637429] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.637446] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.637479] vesafb: mode is 640x480x32, linelength=2560, pages=0
[    0.637481] vesafb: scrolling: redraw
[    0.637484] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.642259] vesafb: framebuffer at 0xdb000000, mapped to 0xffffc90010e80000, using 1216k, total 1216k
[    0.643550] Console: switching to colour frame buffer device 80x30
[    0.644776] fb0: VESA VGA frame buffer device
[    0.644827] intel_idle: does not run on family 6 model 23
[    0.644902] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.644954] ACPI: Power Button [PWRB]
[    0.645025] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.646626] ACPI: Power Button [PWRF]
[    0.647794] GHES: HEST is not enabled!
[    0.648757] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.652167] Linux agpgart interface v0.103
[    0.654760] brd: module loaded
[    0.656496] loop: module loaded
[    0.657510] libphy: Fixed MDIO Bus: probed
[    0.658314] tun: Universal TUN/TAP device driver, 1.6
[    0.659117] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.660032] PPP generic driver version 2.4.2
[    0.660954] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.661793] ehci-pci: EHCI PCI platform driver
[    0.662762] ehci-pci 0000:00:0b.1: EHCI Host Controller
[    0.663612] ehci-pci 0000:00:0b.1: new USB bus registered, assigned bus number 1
[    0.665321] ehci-pci 0000:00:0b.1: debug port 1
[    0.666210] ehci-pci 0000:00:0b.1: cache line size of 64 is not supported
[    0.666224] ehci-pci 0000:00:0b.1: irq 22, io mem 0xdfffe000
[    0.676018] ehci-pci 0000:00:0b.1: USB 2.0 started, EHCI 1.00
[    0.676898] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.677756] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.679441] usb usb1: Product: EHCI Host Controller
[    0.680293] usb usb1: Manufacturer: Linux 3.19.0-49-generic ehci_hcd
[    0.681135] usb usb1: SerialNumber: 0000:00:0b.1
[    0.682101] hub 1-0:1.0: USB hub found
[    0.682917] hub 1-0:1.0: 10 ports detected
[    0.683885] ehci-platform: EHCI generic platform driver
[    0.684700] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.685497] ohci-pci: OHCI PCI platform driver
[    0.686393] ohci-pci 0000:00:0b.0: OHCI PCI host controller
[    0.687179] ohci-pci 0000:00:0b.0: new USB bus registered, assigned bus number 2
[    0.688772] ohci-pci 0000:00:0b.0: irq 23, io mem 0xdffff000
[    0.746040] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    0.746861] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.748511] usb usb2: Product: OHCI PCI host controller
[    0.749355] usb usb2: Manufacturer: Linux 3.19.0-49-generic ohci_hcd
[    0.750204] usb usb2: SerialNumber: 0000:00:0b.0
[    0.751173] hub 2-0:1.0: USB hub found
[    0.752015] hub 2-0:1.0: 10 ports detected
[    0.753028] ohci-platform: OHCI generic platform driver
[    0.753854] uhci_hcd: USB Universal Host Controller Interface driver
[    0.754744] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.755568] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.757853] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.758825] mousedev: PS/2 mouse device common for all mice
[    0.759809] rtc_cmos 00:02: RTC can wake from S4
[    0.760801] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.761668] rtc_cmos 00:02: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    0.763346] i2c /dev entries driver
[    0.764274] device-mapper: uevent: version 1.0.3
[    0.765203] device-mapper: ioctl: 4.29.0-ioctl (2014-10-28) initialised: dm-devel@redhat.com
[    0.766931] ledtrig-cpu: registered to indicate activity on CPUs
[    0.768042] PCCT header not found.
[    0.769002] TCP: cubic registered
[    0.769967] NET: Registered protocol family 10
[    0.771078] NET: Registered protocol family 17
[    0.771912] Key type dns_resolver registered
[    0.773038] Loading compiled-in X.509 certificates
[    0.774714] Loaded X.509 cert 'Magrathea: Glacier signing key: a932dc237895a44d3959bf91a3566a20ee211f37'
[    0.776386] registered taskstats version 1
[    0.778882] Key type trusted registered
[    0.781504] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.784319] Key type encrypted registered
[    0.785157] AppArmor: AppArmor sha1 policy hashing enabled
[    0.786004] ima: No TPM chip found, activating TPM-bypass!
[    0.786860] evm: HMAC attrs: 0x1
[    0.788084]   Magic number: 4:700:156
[    0.788911] bdi 1:8: hash matches
[    0.789733] acpi device:23: hash matches
[    0.790518] acpi PNP0A08:00: hash matches
[    0.791349] rtc_cmos 00:02: setting system clock to 2016-02-12 02:09:04 UTC (1455242944)
[    0.793039] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.793855] EDD information not available.
[    0.794695] PM: Hibernation image not present or could not be loaded.
[    0.795137] Freeing unused kernel memory: 1408K (ffffffff81d27000 - ffffffff81e87000)
[    0.796781] Write protecting the kernel read-only data: 12288k
[    0.797884] Freeing unused kernel memory: 256K (ffff8800017c0000 - ffff880001800000)
[    0.799694] Freeing unused kernel memory: 336K (ffff880001bac000 - ffff880001c00000)
[    0.814580] systemd-udevd[120]: starting version 204
[    0.838302] pata_amd 0000:00:0d.0: version 0.4.1
[    0.838825] [drm] Initialized drm 1.1.0 20060810
[    0.838968] scsi host0: pata_amd
[    0.840546] scsi host1: pata_amd
[    0.840597] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xec00 irq 14
[    0.840598] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xec08 irq 15
[    0.843281] sata_nv 0000:00:0e.0: version 3.5
[    0.843527] ACPI: PCI Interrupt Link [ASA0] enabled at IRQ 21
[    0.844429] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    0.845836] scsi host2: sata_nv
[    0.847418] pata_jmicron 0000:04:00.1: enabling device (0000 -> 0001)
[    0.847537] scsi host3: sata_nv
[    0.847586] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 21
[    0.847588] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 21
[    0.847796] ACPI: PCI Interrupt Link [ASA1] enabled at IRQ 20
[    0.847805] sata_nv 0000:00:0e.1: Using SWNCQ mode
[    0.850069] scsi host4: sata_nv
[    0.850222] scsi host5: sata_nv
[    0.850265] ata5: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc400 irq 20
[    0.850267] ata6: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc408 irq 20
[    0.850465] ACPI: PCI Interrupt Link [ASA2] enabled at IRQ 21
[    0.850469] sata_nv 0000:00:0e.2: Using SWNCQ mode
[    0.850874] scsi host6: sata_nv
[    0.850985] scsi host7: sata_nv
[    0.851030] ata7: SATA max UDMA/133 cmd 0xc000 ctl 0xbc00 bmdma 0xb000 irq 21
[    0.851031] ata8: SATA max UDMA/133 cmd 0xb800 ctl 0xb400 bmdma 0xb008 irq 21
[    0.851055] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    0.851316] ACPI: PCI Interrupt Link [AMAC] enabled at IRQ 23
[    0.863421] scsi host8: pata_jmicron
[    0.864279] scsi host9: pata_jmicron
[    0.865079] ata9: PATA max UDMA/100 cmd 0x8c00 ctl 0x8800 bmdma 0x7c00 irq 16
[    0.865819] ata10: PATA max UDMA/100 cmd 0x8400 ctl 0x8000 bmdma 0x7c08 irq 16
[    0.867336] ahci 0000:04:00.0: version 3.0
[    0.867548] ACPI: PCI Interrupt Link [AXV8] enabled at IRQ 16
[    0.871911] wmi: Mapper loaded
[    0.884056] ahci 0000:04:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    0.885645] ahci 0000:04:00.0: flags: 64bit ncq led clo pmp pio
[    0.888482] scsi host10: ahci
[    0.890335] scsi host11: ahci
[    0.890541] checking generic (db000000 130000) vs hw (c0000000 10000000)
[    0.890542] checking generic (db000000 130000) vs hw (da000000 2000000)
[    0.890543] fb: switching to nouveaufb from VESA VGA
[    0.891991] Console: switching to colour dummy device 80x25
[    0.892321] ata11: SATA max UDMA/133 abar m8192@0xdfefe000 port 0xdfefe100 irq 16
[    0.892331] ata12: SATA max UDMA/133 abar m8192@0xdfefe000 port 0xdfefe180 irq 16
[    0.892449] nouveau  [  DEVICE][0000:01:00.0] BOOT0  : 0x450100a2
[    0.892456] nouveau  [  DEVICE][0000:01:00.0] Chipset: G80 (NV50)
[    0.892459] nouveau  [  DEVICE][0000:01:00.0] Family : NV50
[    0.999835] nouveau  [   VBIOS][0000:01:00.0] using image from PRAMIN
[    0.999917] nouveau  [   VBIOS][0000:01:00.0] BIT signature found
[    0.999921] nouveau  [   VBIOS][0000:01:00.0] version 60.80.0a.00.00
[    1.007996] ata2: port disabled--ignoring
[    1.020159] nouveau  [     PMC][0000:01:00.0] MSI interrupts enabled
[    1.020183] nouveau  [     PFB][0000:01:00.0] RAM type: GDDR3
[    1.020186] nouveau  [     PFB][0000:01:00.0] RAM size: 768 MiB
[    1.020188] nouveau  [     PFB][0000:01:00.0]    ZCOMP: 3142 tags
[    1.052900] nouveau  [  PTHERM][0000:01:00.0] FAN control: none / external
[    1.052909] nouveau  [  PTHERM][0000:01:00.0] fan management: automatic
[    1.052912] nouveau  [  PTHERM][0000:01:00.0] internal sensor: yes
[    1.072771] nouveau  [     CLK][0000:01:00.0] 20: core 576 MHz shader 1350 MHz memory 900 MHz
[    1.072804] nouveau  [     CLK][0000:01:00.0] --: core 198 MHz shader 1188 MHz memory 396 MHz
[    1.072958] [TTM] Zone  kernel: Available graphics memory: 4087460 kiB
[    1.072961] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB
[    1.072963] [TTM] Initializing pool allocator
[    1.072968] [TTM] Initializing DMA pool allocator
[    1.072977] nouveau  [     DRM] VRAM: 768 MiB
[    1.072979] nouveau  [     DRM] GART: 1048576 MiB
[    1.072982] nouveau  [     DRM] BIT table 'A' not found
[    1.072984] nouveau  [     DRM] TMDS table version 2.0
[    1.072986] nouveau  [     DRM] DCB version 4.0
[    1.072989] nouveau  [     DRM] DCB outp 00: 04000320 00000028
[    1.072991] nouveau  [     DRM] DCB outp 01: 01000322 00000030
[    1.072993] nouveau  [     DRM] DCB outp 02: 02011310 00000028
[    1.072995] nouveau  [     DRM] DCB outp 03: 02011312 00000030
[    1.072997] nouveau  [     DRM] DCB outp 04: 010223f1 00c1c020
[    1.073000] nouveau  [     DRM] DCB conn 00: 1030
[    1.073002] nouveau  [     DRM] DCB conn 01: 2130
[    1.073004] nouveau  [     DRM] DCB conn 02: 0210
[    1.073007] nouveau  [     DRM] DCB conn 03: 0211
[    1.073009] nouveau  [     DRM] DCB conn 04: 0213
[    1.080682] nouveau W[     DRM] failed to create encoder 0/1/0: -19
[    1.080685] nouveau W[     DRM] TV-1 has no encoders, removing
[    1.080712] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    1.080714] [drm] Driver supports precise vblank timestamp query.
[    1.091175] nouveau  [     DRM] MM: using M2MF for buffer copies
[    1.149831] nouveau  [     DRM] allocated 1024x768 fb: 0x70000, bo ffff880232a05c00
[    1.149904] fbcon: nouveaufb (fb0) is primary device
[    1.212057] ata11: SATA link down (SStatus 0 SControl 300)
[    1.212098] ata12: SATA link down (SStatus 0 SControl 300)
[    1.216872] Console: switching to colour frame buffer device 128x48
[    1.217586] nouveau 0000:01:00.0: fb0: nouveaufb frame buffer device
[    1.217612] nouveau 0000:01:00.0: registered panic notifier
[    1.220050] [drm] Initialized nouveau 1.2.1 20120801 for 0000:01:00.0 on minor 0
[    1.312027] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.316026] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.320027] ata7: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.324301] ata5.00: ATA-8: Hitachi HUA723030ALA640, MKAOA580, max UDMA/133
[    1.324313] ata5.00: 5860533168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.328300] ata7.00: ATA-8: Hitachi HUA723030ALA640, MKAOA580, max UDMA/133
[    1.328309] ata7.00: 5860533168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.336207] ata3.00: ATAPI: LITE-ON DVDRW LH-20A1S, 9L05, max UDMA/100
[    1.336352] ata7.00: configured for UDMA/133
[    1.340286] ata5.00: configured for UDMA/133
[    1.368142] ata3.00: configured for UDMA/100
[    1.370028] scsi 2:0:0:0: CD-ROM            LITE-ON  DVDRW LH-20A1S   9L05 PQ: 0 ANSI: 5
[    1.376502] forcedeth 0000:00:11.0: ifname eth0, PHY OUI 0x50ef @ 0, addr 00:04:4b:17:22:9a
[    1.376517] forcedeth 0000:00:11.0: highdma csum vlan pwrctl mgmt gbit lnktim msi desc-v3
[    1.376789] ACPI: PCI Interrupt Link [AMA1] enabled at IRQ 22
[    1.386213] sr 2:0:0:0: [sr0] scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.386225] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.386559] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    1.386622] sr 2:0:0:0: Attached scsi generic sg0 type 5
[    1.632019] tsc: Refined TSC clocksource calibration: 2999.958 MHz
[    1.852024] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.861139] ata4.00: ATA-8: WDC WD5000AAKS-00UU3A0, 01.03B01, max UDMA/133
[    1.861347] ata4.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.877135] ata4.00: configured for UDMA/133
[    1.877418] scsi 3:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-0 3B01 PQ: 0 ANSI: 5
[    1.877786] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    1.877795] sd 3:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.877838] sd 3:0:0:0: [sda] Write Protect is off
[    1.877840] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.877859] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.880529] scsi 4:0:0:0: Direct-Access     ATA      Hitachi HUA72303 A580 PQ: 0 ANSI: 5
[    1.881347] sd 4:0:0:0: [sdb] 5860533168 512-byte logical blocks: (3.00 TB/2.72 TiB)
[    1.881349] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    1.882753] sd 4:0:0:0: [sdb] Write Protect is off
[    1.883515] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.883529] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.900491] forcedeth 0000:00:12.0: ifname eth1, PHY OUI 0x50ef @ 1, addr 00:04:4b:17:22:9b
[    1.900685] forcedeth 0000:00:12.0: highdma csum vlan pwrctl mgmt gbit lnktim msi desc-v3
[    1.911082]  sda: sda1 sda2 < sda5 >
[    1.911673] sd 3:0:0:0: [sda] Attached SCSI disk
[    1.922797]  sdb: sdb1 sdb9
[    1.923186] sd 4:0:0:0: [sdb] Attached SCSI disk
[    2.348034] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.356302] ata6.00: ATA-8: Hitachi HUA723030ALA640, MKAOA580, max UDMA/133
[    2.356575] ata6.00: 5860533168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.372284] ata6.00: configured for UDMA/133
[    2.372619] scsi 5:0:0:0: Direct-Access     ATA      Hitachi HUA72303 A580 PQ: 0 ANSI: 5
[    2.373240] sd 5:0:0:0: Attached scsi generic sg3 type 0
[    2.373946] sd 5:0:0:0: [sdc] 5860533168 512-byte logical blocks: (3.00 TB/2.72 TiB)
[    2.374012] scsi 6:0:0:0: Direct-Access     ATA      Hitachi HUA72303 A580 PQ: 0 ANSI: 5
[    2.374161] sd 6:0:0:0: Attached scsi generic sg4 type 0
[    2.374244] sd 6:0:0:0: [sdd] 5860533168 512-byte logical blocks: (3.00 TB/2.72 TiB)
[    2.374289] sd 6:0:0:0: [sdd] Write Protect is off
[    2.374290] sd 6:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    2.374309] sd 6:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.379204] sd 5:0:0:0: [sdc] Write Protect is off
[    2.380091] sd 5:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    2.380106] sd 5:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.403012]  sdd: sdd1 sdd9
[    2.403461] sd 6:0:0:0: [sdd] Attached SCSI disk
[    2.417129]  sdc: sdc1 sdc9
[    2.417537] sd 5:0:0:0: [sdc] Attached SCSI disk
[    2.632097] Switched to clocksource tsc
[    2.840020] ata8: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.848276] ata8.00: ATA-8: Hitachi HUA723030ALA640, MKAOA580, max UDMA/133
[    2.848573] ata8.00: 5860533168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.864272] ata8.00: configured for UDMA/133
[    2.864615] scsi 7:0:0:0: Direct-Access     ATA      Hitachi HUA72303 A580 PQ: 0 ANSI: 5
[    2.865316] sd 7:0:0:0: Attached scsi generic sg5 type 0
[    2.865857] sd 7:0:0:0: [sde] 5860533168 512-byte logical blocks: (3.00 TB/2.72 TiB)
[    2.865885] sd 7:0:0:0: [sde] Write Protect is off
[    2.865887] sd 7:0:0:0: [sde] Mode Sense: 00 3a 00 00
[    2.865900] sd 7:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.900691]  sde: sde1 sde9
[    2.901134] sd 7:0:0:0: [sde] Attached SCSI disk
[    3.053107] random: nonblocking pool is initialized
[    3.848025] floppy0: no floppy controllers found
[    3.928013] md: linear personality registered for level -1
[    3.930288] md: multipath personality registered for level -4
[    3.932524] md: raid0 personality registered for level 0
[    3.935042] md: raid1 personality registered for level 1
[    4.004023] raid6: sse2x1    4975 MB/s
[    4.072010] raid6: sse2x2    6491 MB/s
[    4.140011] raid6: sse2x4    8789 MB/s
[    4.140020] raid6: using algorithm sse2x4 (8789 MB/s)
[    4.140023] raid6: using ssse3x2 recovery algorithm
[    4.141134] xor: measuring software checksum speed
[    4.180007]    prefetch64-sse: 12530.000 MB/sec
[    4.220007]    generic_sse: 11040.000 MB/sec
[    4.220010] xor: using function: prefetch64-sse (12530.000 MB/sec)
[    4.221068] async_tx: api initialized (async)
[    4.227422] md: raid6 personality registered for level 6
[    4.227427] md: raid5 personality registered for level 5
[    4.227431] md: raid4 personality registered for level 4
[    4.232300] md: raid10 personality registered for level 10
[    9.259436] EXT4-fs (dm-0): INFO: recovery required on readonly filesystem
[    9.259442] EXT4-fs (dm-0): write access will be enabled during recovery
[   10.242345] EXT4-fs (dm-0): recovery complete
[   10.246663] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
[   11.849258] zavl: module license 'CDDL' taints kernel.
[   11.849270] Disabling lock debugging due to kernel taint
[   11.849298] zavl: module verification failed: signature and/or  required key missing - tainting kernel
[   11.874379] SPL: Loaded module v0.6.5.4-1~trusty
[   12.190373] ZFS: Loaded module v0.6.5.4-1~trusty, ZFS pool version 5000, ZFS filesystem version 5
[   17.742515] SPL: using hostid 0x007f0101
[   19.652861] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
[   19.731838] EXT4-fs (sda1): mounting ext2 file system using the ext4 subsystem
[   19.770888] EXT4-fs (sda1): mounted filesystem without journal. Opts: (null)
[   20.476647] systemd-udevd[1904]: starting version 204
[   20.495801] lp: driver loaded but no devices found
[   20.658857] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   20.661329] i2c i2c-4: nForce2 SMBus adapter at 0xf400
[   20.661397] i2c i2c-5: nForce2 SMBus adapter at 0xf000
[   20.692193] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 23
[   20.692202] snd_hda_intel 0000:00:0f.1: Disabling MSI
[   20.798997] audit: type=1400 audit(1455242964.503:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=2012 comm="apparmor_parser"
[   20.799004] audit: type=1400 audit(1455242964.503:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=2012 comm="apparmor_parser"
[   20.799008] audit: type=1400 audit(1455242964.503:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=2012 comm="apparmor_parser"
[   20.799354] audit: type=1400 audit(1455242964.503:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=2012 comm="apparmor_parser"
[   20.799359] audit: type=1400 audit(1455242964.503:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=2012 comm="apparmor_parser"
[   20.799544] audit: type=1400 audit(1455242964.503:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=2012 comm="apparmor_parser"
[   20.801165] audit: type=1400 audit(1455242964.507:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=2035 comm="apparmor_parser"
[   20.801171] audit: type=1400 audit(1455242964.507:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=2035 comm="apparmor_parser"
[   20.801175] audit: type=1400 audit(1455242964.507:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=2035 comm="apparmor_parser"
[   20.801182] audit: type=1400 audit(1455242964.507:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=2013 comm="apparmor_parser"
[   21.057679] forcedeth 0000:00:11.0 eth0: MSI enabled
[   21.440015] sound hdaudioC0D0: autoconfig: line_outs=4 (0x14/0x15/0x16/0x17/0x0) type:line
[   21.440019] sound hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   21.440022] sound hdaudioC0D0:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[   21.440025] sound hdaudioC0D0:    mono: mono_out=0x0
[   21.440027] sound hdaudioC0D0:    dig-out=0x11/0x1e
[   21.440029] sound hdaudioC0D0:    inputs:
[   21.440032] sound hdaudioC0D0:      Front Mic=0x19
[   21.440035] sound hdaudioC0D0:      Rear Mic=0x18
[   21.440038] sound hdaudioC0D0:      Line=0x1a
[   21.440040] sound hdaudioC0D0:    dig-in=0x1f
[   22.327801] init: failsafe main process (2075) killed by TERM signal
[   23.298128] input: HDA NVidia Front Mic as /devices/pci0000:00/0000:00:0f.1/sound/card0/input3
[   23.299028] input: HDA NVidia Rear Mic as /devices/pci0000:00/0000:00:0f.1/sound/card0/input4
[   23.299150] input: HDA NVidia Line as /devices/pci0000:00/0000:00:0f.1/sound/card0/input5
[   23.299260] input: HDA NVidia Line Out Front as /devices/pci0000:00/0000:00:0f.1/sound/card0/input6
[   23.299389] input: HDA NVidia Line Out Surround as /devices/pci0000:00/0000:00:0f.1/sound/card0/input7
[   23.299555] input: HDA NVidia Line Out CLFE as /devices/pci0000:00/0000:00:0f.1/sound/card0/input8
[   23.300168] input: HDA NVidia Line Out Side as /devices/pci0000:00/0000:00:0f.1/sound/card0/input9
[   23.300258] input: HDA NVidia Front Headphone as /devices/pci0000:00/0000:00:0f.1/sound/card0/input10
[   23.550811] init: samba-ad-dc main process (2405) terminated with status 1
[   23.672035] floppy0: no floppy controllers found
[   25.132237] Ebtables v2.0 registered
[   25.185837] ip_tables: (C) 2000-2006 Netfilter Core Team
[   25.192560] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   25.544602] init: plymouth-upstart-bridge main process ended, respawning
[   27.756077] bridge: automatic filtering via arp/ip/ip6tables has been deprecated. Update your scripts to load br_netfilter if you need this.
[   27.877543] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[  107.846011] cgroup: systemd-logind (1957) created nested cgroup for controller "memory" which has incomplete hierarchy support. Nested cgroups may change behavior in the future.
[  107.846014] cgroup: "memory" requires setting use_hierarchy to 1 on the root
[ 1262.958518] usbcore: registered new interface driver usb-storage
```

dmesg output with USB key installed and server reboot:

```
[    0.000000] Initializing cgroup subsys cpuset[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.19.0-49-generic (buildd@lgw01-08) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #55~14.04.1-Ubuntu SMP Fri Jan 22 11:24:31 UTC 2016 (Ubuntu 3.19.0-49.55~14.04.1-generic 3.19.8-ckt12)
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.19.0-49-generic root=/dev/mapper/kazz--u0a1--vg-root ro nomdmonddf nomdmonisw
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009b7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009b800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000bfeeffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bfef0000-0x00000000bfef2fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bfef3000-0x00000000bfefffff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000023fffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.4 present.
[    0.000000] DMI:  EVGA  132-CK-NF79/132-CK-NF79, BIOS   P10  12/30/2009
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] AGP: No AGP bridge found
[    0.000000] e820: last_pfn = 0x240000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CBFFF write-protect
[    0.000000]   CC000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask E00000000 write-back
[    0.000000]   1 base 200000000 mask FC0000000 write-back
[    0.000000]   2 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   3 base 0BFF00000 mask FFFF00000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- UC
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 8GB, type WB
[    0.000000] reg 1, base: 8GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 1GB, type UC
[    0.000000] reg 3, base: 3071MB, range: 1MB, type UC
[    0.000000] total RAM covered: 8191M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K  chunk_size: 2M  num_reg: 5      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3071MB, range: 1MB, type UC
[    0.000000] reg 3, base: 4GB, range: 4GB, type WB
[    0.000000] reg 4, base: 8GB, range: 1GB, type WB
[    0.000000] e820: update [mem 0xbff00000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xbfef0 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000f3fd0-0x000f3fdf] mapped at [ffff8800000f3fd0]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000095000] 95000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fd4000, 0x01fd4fff] PGTABLE
[    0.000000] BRK [0x01fd5000, 0x01fd5fff] PGTABLE
[    0.000000] BRK [0x01fd6000, 0x01fd6fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x23fe00000-0x23fffffff]
[    0.000000]  [mem 0x23fe00000-0x23fffffff] page 2M
[    0.000000] BRK [0x01fd7000, 0x01fd7fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x220000000-0x23fdfffff]
[    0.000000]  [mem 0x220000000-0x23fdfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0xbfeeffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0xbfdfffff] page 2M
[    0.000000]  [mem 0xbfe00000-0xbfeeffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x21fffffff]
[    0.000000]  [mem 0x100000000-0x21fffffff] page 2M
[    0.000000] BRK [0x01fd8000, 0x01fd8fff] PGTABLE
[    0.000000] BRK [0x01fd9000, 0x01fd9fff] PGTABLE
[    0.000000] RAMDISK: [mem 0x34cc8000-0x3665bfff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000000F7FA0 000014 (v00 Nvidia)
[    0.000000] ACPI: RSDT 0x00000000BFEF3040 00003C (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
[    0.000000] ACPI: FACP 0x00000000BFEF30C0 000074 (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
[    0.000000] ACPI: DSDT 0x00000000BFEF3180 005447 (v01 NVIDIA NVDAACPI 00001000 MSFT 03000000)
[    0.000000] ACPI: FACS 0x00000000BFEF0000 000040
[    0.000000] ACPI: HPET 0x00000000BFEF8740 000038 (v01 Nvidia NVDAACPI 42302E31 NVDA 00000098)
[    0.000000] ACPI: WDRT 0x00000000BFEF87C0 000047 (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
[    0.000000] ACPI: MCFG 0x00000000BFEF8880 00003C (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
[    0.000000] ACPI: APIC 0x00000000BFEF8640 000098 (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
[    0.000000] ACPI: OEMN 0x00000000BFEF8900 004AED (v01 NVIDIA NTUNEOEM 20302E31 NVDA 00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000023fffffff]
[    0.000000] NODE_DATA(0) allocated [mem 0x23fff6000-0x23fffafff]
[    0.000000]  [ffffea0000000000-ffffea0008ffffff] PMD -> [ffff880237600000-ffff88023f5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x23fffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009afff]
[    0.000000]   node   0: [mem 0x00100000-0xbfeeffff]
[    0.000000]   node   0: [mem 0x100000000-0x23fffffff]
[    0.000000] Initmem setup node 0 [mem 0x00001000-0x23fffffff]
[    0.000000] On node 0 totalpages: 2096778
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3994 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 12220 pages used for memmap
[    0.000000]   DMA32 zone: 782064 pages, LIFO batch:31
[    0.000000]   Normal zone: 20480 pages used for memmap
[    0.000000]   Normal zone: 1310720 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
[    0.000000] smpboot: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009b000-0x0009bfff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009c000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000effff]
[    0.000000] PM: Registered nosave memory: [mem 0x000f0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xbfef0000-0xbfef2fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbfef3000-0xbfefffff]
[    0.000000] PM: Registered nosave memory: [mem 0xbff00000-0xdfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xffffffff]
[    0.000000] e820: [mem 0xbff00000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 31 pages/cpu @ffff88023fc00000 s86144 r8192 d32640 u524288
[    0.000000] pcpu-alloc: s86144 r8192 d32640 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 2063993
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.19.0-49-generic root=/dev/mapper/kazz--u0a1--vg-root ro nomdmonddf nomdmonisw
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x3, cntxt size 0x240 using standard form
[    0.000000] AGP: Checking aperture...
[    0.000000] AGP: No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 8146696K/8387112K available (7923K kernel code, 1174K rwdata, 3760K rodata, 1408K init, 1292K bss, 240416K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]  RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]  RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=4
[    0.000000] NR_IRQS:16640 nr_irqs:456 16
[    0.000000]  Offload RCU callbacks from all CPUs
[    0.000000]  Offload RCU callbacks from CPUs: 0-3.
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 2999.807 MHz processor
[    0.004010] Calibrating delay loop (skipped), value calculated using timer frequency.. 5999.61 BogoMIPS (lpj=11999228)
[    0.004014] pid_max: default: 32768 minimum: 301
[    0.004021] ACPI: Core revision 20141107
[    0.010322] ACPI: All ACPI Tables successfully acquired
[    0.010345] Security Framework initialized
[    0.010365] AppArmor: AppArmor initialized
[    0.010367] Yama: becoming mindful.
[    0.010889] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.014212] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.015622] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.015634] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.015943] Initializing cgroup subsys memory
[    0.015953] Initializing cgroup subsys devices
[    0.015957] Initializing cgroup subsys freezer
[    0.015961] Initializing cgroup subsys net_cls
[    0.015964] Initializing cgroup subsys blkio
[    0.015967] Initializing cgroup subsys perf_event
[    0.015971] Initializing cgroup subsys net_prio
[    0.015974] Initializing cgroup subsys hugetlb
[    0.016017] CPU: Physical Processor ID: 0
[    0.016019] CPU: Processor Core ID: 0
[    0.016021] mce: CPU supports 6 MCE banks
[    0.016028] CPU0: Thermal monitoring enabled (TM1)
[    0.016032] process: using mwait in idle threads
[    0.016037] Last level iTLB entries: 4KB 128, 2MB 4, 4MB 4
[    0.016037] Last level dTLB entries: 4KB 256, 2MB 0, 4MB 32, 1GB 0
[    0.016125] Freeing SMP alternatives memory: 32K (ffffffff81e87000 - ffffffff81e8f000)
[    0.019616] ftrace: allocating 30034 entries in 118 pages
[    0.032315] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.072009] smpboot: CPU0: Intel(R) Core(TM)2 Quad CPU    Q9650  @ 3.00GHz (fam: 06, model: 17, stepping: 0a)
[    0.076000] Performance Events: PEBS fmt0+, 4-deep LBR, Core2 events, Intel PMU driver.
[    0.076000] ... version:                2
[    0.076000] ... bit width:              40
[    0.076000] ... generic registers:      2
[    0.076000] ... value mask:             000000ffffffffff
[    0.076000] ... max period:             000000007fffffff
[    0.076000] ... fixed-purpose events:   3
[    0.076000] ... event mask:             0000000700000003
[    0.076000] x86: Booting SMP configuration:
[    0.076000] .... node  #0, CPUs:      #1
[    0.086146] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.086255]  #2 #3
[    0.112027] x86: Booted up 1 node, 4 CPUs
[    0.112035] smpboot: Total of 4 processors activated (23998.45 BogoMIPS)
[    0.116138] devtmpfs: initialized
[    0.120741] evm: security.selinux
[    0.120744] evm: security.SMACK64
[    0.120745] evm: security.SMACK64EXEC
[    0.120747] evm: security.SMACK64TRANSMUTE
[    0.120748] evm: security.SMACK64MMAP
[    0.120750] evm: security.ima
[    0.120751] evm: security.capability
[    0.120765] PM: Registering ACPI NVS region [mem 0xbfef0000-0xbfef2fff] (12288 bytes)
[    0.120765] pinctrl core: initialized pinctrl subsystem
[    0.120765] RTC time: 16:19:23, date: 02/12/16
[    0.120765] NET: Registered protocol family 16
[    0.128006] cpuidle: using governor ladder
[    0.132006] cpuidle: using governor menu
[    0.132062] ACPI: bus type PCI registered
[    0.132066] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.132160] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.132171] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.132515] PCI: Using configuration type 1 for base access
[    0.136126] ACPI: Added _OSI(Module Device)
[    0.136129] ACPI: Added _OSI(Processor Device)
[    0.136136] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.136137] ACPI: Added _OSI(Processor Aggregator Device)
[    0.140468] ACPI: Interpreter enabled
[    0.140474] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20141107/hwxface-580)
[    0.140480] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20141107/hwxface-580)
[    0.140492] ACPI: (supports S0 S3 S4 S5)
[    0.140494] ACPI: Using IOAPIC for interrupt routing
[    0.140585] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.140602] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.145437] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.145443] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.145533] acpi PNP0A08:00: _OSC: platform does not support [PCIeHotplug]
[    0.145619] acpi PNP0A08:00: _OSC: OS now controls [PME AER PCIeCapability]
[    0.145867] PCI host bridge to bus 0000:00
[    0.145874] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.145876] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.145883] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.145886] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.145888] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000dffff]
[    0.145891] pci_bus 0000:00: root bus resource [mem 0xbff00000-0xfebfffff]
[    0.145902] pci 0000:00:00.0: [10de:0800] type 00 class 0x060000
[    0.146016] pci 0000:00:00.1: [10de:0808] type 00 class 0x050000
[    0.146127] pci 0000:00:00.2: [10de:0809] type 00 class 0x050000
[    0.146234] pci 0000:00:00.3: [10de:080a] type 00 class 0x050000
[    0.146353] pci 0000:00:00.4: [10de:080b] type 00 class 0x050000
[    0.146472] pci 0000:00:00.5: [10de:080c] type 00 class 0x050000
[    0.146571] pci 0000:00:00.6: [10de:080d] type 00 class 0x050000
[    0.146678] pci 0000:00:00.7: [10de:080e] type 00 class 0x050000
[    0.146786] pci 0000:00:01.0: [10de:080f] type 00 class 0x050000
[    0.146884] pci 0000:00:01.1: [10de:0810] type 00 class 0x050000
[    0.146982] pci 0000:00:01.2: [10de:0811] type 00 class 0x050000
[    0.147080] pci 0000:00:01.3: [10de:0812] type 00 class 0x050000
[    0.147188] pci 0000:00:01.4: [10de:0813] type 00 class 0x050000
[    0.147286] pci 0000:00:01.5: [10de:0814] type 00 class 0x050000
[    0.147384] pci 0000:00:01.6: [10de:081a] type 00 class 0x050000
[    0.147503] pci 0000:00:01.7: [10de:080e] type 00 class 0x050000
[    0.147622] pci 0000:00:02.0: [10de:0815] type 01 class 0x060400
[    0.147704] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.147756] pci 0000:00:02.0: System wakeup disabled by ACPI
[    0.147817] pci 0000:00:04.0: [10de:0817] type 01 class 0x060400
[    0.147894] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.147946] pci 0000:00:04.0: System wakeup disabled by ACPI
[    0.148024] pci 0000:00:09.0: [10de:0369] type 00 class 0x050000
[    0.148270] pci 0000:00:0a.0: [10de:0360] type 00 class 0x060100
[    0.148279] pci 0000:00:0a.0: reg 0x10: [io  0xfc00-0xfc7f]
[    0.148380] pci 0000:00:0a.1: [10de:0368] type 00 class 0x0c0500
[    0.148394] pci 0000:00:0a.1: reg 0x10: [io  0xf800-0xf83f]
[    0.148416] pci 0000:00:0a.1: reg 0x20: [io  0xf400-0xf43f]
[    0.148422] pci 0000:00:0a.1: reg 0x24: [io  0xf000-0xf03f]
[    0.148459] pci 0000:00:0a.1: PME# supported from D3hot D3cold
[    0.148546] pci 0000:00:0b.0: [10de:036c] type 00 class 0x0c0310
[    0.148557] pci 0000:00:0b.0: reg 0x10: [mem 0xdffff000-0xdfffffff]
[    0.148601] pci 0000:00:0b.0: supports D1 D2
[    0.148602] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.148644] pci 0000:00:0b.0: System wakeup disabled by ACPI
[    0.148684] pci 0000:00:0b.1: [10de:036d] type 00 class 0x0c0320
[    0.148695] pci 0000:00:0b.1: reg 0x10: [mem 0xdfffe000-0xdfffe0ff]
[    0.148742] pci 0000:00:0b.1: supports D1 D2
[    0.148743] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.148798] pci 0000:00:0b.1: System wakeup disabled by ACPI
[    0.148847] pci 0000:00:0d.0: [10de:036e] type 00 class 0x01018a
[    0.148871] pci 0000:00:0d.0: reg 0x20: [io  0xec00-0xec0f]
[    0.148881] pci 0000:00:0d.0: legacy IDE quirk: reg 0x10: [io  0x01f0-0x01f7]
[    0.148884] pci 0000:00:0d.0: legacy IDE quirk: reg 0x14: [io  0x03f6]
[    0.148887] pci 0000:00:0d.0: legacy IDE quirk: reg 0x18: [io  0x0170-0x0177]
[    0.148889] pci 0000:00:0d.0: legacy IDE quirk: reg 0x1c: [io  0x0376]
[    0.148976] pci 0000:00:0e.0: [10de:037f] type 00 class 0x010185
[    0.148987] pci 0000:00:0e.0: reg 0x10: [io  0x09f0-0x09f7]
[    0.148993] pci 0000:00:0e.0: reg 0x14: [io  0x0bf0-0x0bf3]
[    0.148998] pci 0000:00:0e.0: reg 0x18: [io  0x0970-0x0977]
[    0.149004] pci 0000:00:0e.0: reg 0x1c: [io  0x0b70-0x0b73]
[    0.149009] pci 0000:00:0e.0: reg 0x20: [io  0xd800-0xd80f]
[    0.149015] pci 0000:00:0e.0: reg 0x24: [mem 0xdfffd000-0xdfffdfff]
[    0.149114] pci 0000:00:0e.1: [10de:037f] type 00 class 0x010185
[    0.149126] pci 0000:00:0e.1: reg 0x10: [io  0x09e0-0x09e7]
[    0.149131] pci 0000:00:0e.1: reg 0x14: [io  0x0be0-0x0be3]
[    0.149137] pci 0000:00:0e.1: reg 0x18: [io  0x0960-0x0967]
[    0.149142] pci 0000:00:0e.1: reg 0x1c: [io  0x0b60-0x0b63]
[    0.149147] pci 0000:00:0e.1: reg 0x20: [io  0xc400-0xc40f]
[    0.149153] pci 0000:00:0e.1: reg 0x24: [mem 0xdfffc000-0xdfffcfff]
[    0.149252] pci 0000:00:0e.2: [10de:037f] type 00 class 0x010185
[    0.149264] pci 0000:00:0e.2: reg 0x10: [io  0xc000-0xc007]
[    0.149269] pci 0000:00:0e.2: reg 0x14: [io  0xbc00-0xbc03]
[    0.149275] pci 0000:00:0e.2: reg 0x18: [io  0xb800-0xb807]
[    0.149280] pci 0000:00:0e.2: reg 0x1c: [io  0xb400-0xb403]
[    0.149285] pci 0000:00:0e.2: reg 0x20: [io  0xb000-0xb00f]
[    0.149291] pci 0000:00:0e.2: reg 0x24: [mem 0xdfffb000-0xdfffbfff]
[    0.149395] pci 0000:00:0f.0: [10de:0370] type 01 class 0x060401
[    0.149465] pci 0000:00:0f.0: System wakeup disabled by ACPI
[    0.149507] pci 0000:00:0f.1: [10de:0371] type 00 class 0x040300
[    0.149520] pci 0000:00:0f.1: reg 0x10: [mem 0xdfff0000-0xdfff3fff]
[    0.149572] pci 0000:00:0f.1: PME# supported from D3hot D3cold
[    0.149616] pci 0000:00:0f.1: System wakeup disabled by ACPI
[    0.149669] pci 0000:00:11.0: [10de:0373] type 00 class 0x068000
[    0.149683] pci 0000:00:11.0: reg 0x10: [mem 0xdfffa000-0xdfffafff]
[    0.149689] pci 0000:00:11.0: reg 0x14: [io  0xac00-0xac07]
[    0.149694] pci 0000:00:11.0: reg 0x18: [mem 0xdfff9000-0xdfff90ff]
[    0.149700] pci 0000:00:11.0: reg 0x1c: [mem 0xdfff8000-0xdfff800f]
[    0.149744] pci 0000:00:11.0: supports D1 D2
[    0.149746] pci 0000:00:11.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.149792] pci 0000:00:11.0: System wakeup disabled by ACPI
[    0.149836] pci 0000:00:12.0: [10de:0373] type 00 class 0x068000
[    0.149850] pci 0000:00:12.0: reg 0x10: [mem 0xdfff7000-0xdfff7fff]
[    0.149860] pci 0000:00:12.0: reg 0x14: [io  0xa800-0xa807]
[    0.149870] pci 0000:00:12.0: reg 0x18: [mem 0xdfff6000-0xdfff60ff]
[    0.149876] pci 0000:00:12.0: reg 0x1c: [mem 0xdfff5000-0xdfff500f]
[    0.149920] pci 0000:00:12.0: supports D1 D2
[    0.149922] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.149970] pci 0000:00:12.0: System wakeup disabled by ACPI
[    0.150015] pci 0000:00:15.0: [10de:0374] type 01 class 0x060400
[    0.150060] pci 0000:00:15.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.150104] pci 0000:00:15.0: System wakeup disabled by ACPI
[    0.150216] pci 0000:01:00.0: [10de:0191] type 00 class 0x030000
[    0.150225] pci 0000:01:00.0: reg 0x10: [mem 0xdc000000-0xdcffffff]
[    0.150233] pci 0000:01:00.0: reg 0x14: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.150241] pci 0000:01:00.0: reg 0x1c: [mem 0xda000000-0xdbffffff 64bit]
[    0.150247] pci 0000:01:00.0: reg 0x24: [io  0x9c00-0x9c7f]
[    0.150253] pci 0000:01:00.0: reg 0x30: [mem 0x00000000-0x0001ffff pref]
[    0.150318] pci 0000:01:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.150327] pci 0000:00:02.0: PCI bridge to [bus 01]
[    0.150333] pci 0000:00:02.0:   bridge window [io  0x9000-0x9fff]
[    0.150336] pci 0000:00:02.0:   bridge window [mem 0xda000000-0xddffffff]
[    0.150342] pci 0000:00:02.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.150402] pci 0000:00:04.0: PCI bridge to [bus 02]
[    0.150471] pci 0000:00:0f.0: PCI bridge to [bus 03] (subtractive decode)
[    0.150477] pci 0000:00:0f.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.150479] pci 0000:00:0f.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.150481] pci 0000:00:0f.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.150482] pci 0000:00:0f.0:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
[    0.150484] pci 0000:00:0f.0:   bridge window [mem 0xbff00000-0xfebfffff] (subtractive decode)
[    0.150539] pci 0000:04:00.0: [197b:2363] type 00 class 0x010601
[    0.150610] pci 0000:04:00.0: reg 0x24: [mem 0xdfefe000-0xdfefffff]
[    0.150666] pci 0000:04:00.0: PME# supported from D3hot
[    0.150722] pci 0000:04:00.1: [197b:2363] type 00 class 0x010185
[    0.150739] pci 0000:04:00.1: reg 0x10: [io  0x8c00-0x8c07]
[    0.150748] pci 0000:04:00.1: reg 0x14: [io  0x8800-0x8803]
[    0.150756] pci 0000:04:00.1: reg 0x18: [io  0x8400-0x8407]
[    0.150764] pci 0000:04:00.1: reg 0x1c: [io  0x8000-0x8003]
[    0.150772] pci 0000:04:00.1: reg 0x20: [io  0x7c00-0x7c0f]
[    0.150862] pci 0000:04:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.150871] pci 0000:00:15.0: PCI bridge to [bus 04]
[    0.150875] pci 0000:00:15.0:   bridge window [io  0x7000-0x8fff]
[    0.150878] pci 0000:00:15.0:   bridge window [mem 0xdfe00000-0xdfefffff]
[    0.151263] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.151309] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.151354] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.151398] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.151443] ACPI: PCI Interrupt Link [LXV5] (IRQs 5 7 9 10 *11 14 15)
[    0.151487] ACPI: PCI Interrupt Link [LXV6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.151532] ACPI: PCI Interrupt Link [LXV7] (IRQs 5 7 9 10 *11 14 15)
[    0.151575] ACPI: PCI Interrupt Link [LXV8] (IRQs 5 7 9 *10 11 14 15)
[    0.151619] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 10 *11 14 15)
[    0.151663] ACPI: PCI Interrupt Link [LMC1] (IRQs *5 7 9 10 11 14 15)
[    0.151707] ACPI: PCI Interrupt Link [LMAC] (IRQs *5 7 9 10 11 14 15)
[    0.151756] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 *10 11 14 15)
[    0.151800] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.151844] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 *10 11 14 15)
[    0.151888] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.151933] ACPI: PCI Interrupt Link [LSA0] (IRQs 5 7 9 10 *11 14 15)
[    0.151977] ACPI: PCI Interrupt Link [LSA1] (IRQs 5 7 9 10 *11 14 15)
[    0.152039] ACPI: PCI Interrupt Link [LSA2] (IRQs 5 7 9 *10 11 14 15)
[    0.152112] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[    0.152178] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[    0.152243] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[    0.152307] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[    0.152372] ACPI: PCI Interrupt Link [AXV5] (IRQs 16) *0, disabled.
[    0.152436] ACPI: PCI Interrupt Link [AXV6] (IRQs 16) *0, disabled.
[    0.152500] ACPI: PCI Interrupt Link [AXV7] (IRQs 16) *0, disabled.
[    0.152564] ACPI: PCI Interrupt Link [AXV8] (IRQs 16) *0, disabled.
[    0.152628] ACPI: PCI Interrupt Link [AUBA] (IRQs 22 23) *0, disabled.
[    0.152693] ACPI: PCI Interrupt Link [AMA1] (IRQs 22 23) *0, disabled.
[    0.152758] ACPI: PCI Interrupt Link [AMAC] (IRQs 22 23) *0, disabled.
[    0.152822] ACPI: PCI Interrupt Link [AAZA] (IRQs 22 23) *0, disabled.
[    0.152887] ACPI: PCI Interrupt Link [AACI] (IRQs 22 23) *0, disabled.
[    0.152951] ACPI: PCI Interrupt Link [AMCI] (IRQs 22 23) *0, disabled.
[    0.153016] ACPI: PCI Interrupt Link [ASMB] (IRQs 22 23) *0, disabled.
[    0.153080] ACPI: PCI Interrupt Link [AUS2] (IRQs 22 23) *0, disabled.
[    0.153144] ACPI: PCI Interrupt Link [AIDE] (IRQs 22 23) *0, disabled.
[    0.153209] ACPI: PCI Interrupt Link [ASA0] (IRQs 20 21) *0, disabled.
[    0.153273] ACPI: PCI Interrupt Link [ASA1] (IRQs 20 21) *0, disabled.
[    0.153338] ACPI: PCI Interrupt Link [ASA2] (IRQs 20 21) *0, disabled.
[    0.153452] vgaarb: setting as boot device: PCI:0000:01:00.0
[    0.153452] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.153452] vgaarb: loaded
[    0.153452] vgaarb: bridge control possible 0000:01:00.0
[    0.153452] SCSI subsystem initialized
[    0.153452] libata version 3.00 loaded.
[    0.153452] ACPI: bus type USB registered
[    0.153452] usbcore: registered new interface driver usbfs
[    0.153452] usbcore: registered new interface driver hub
[    0.153452] usbcore: registered new device driver usb
[    0.153452] PCI: Using ACPI for IRQ routing
[    0.160622] PCI: pci_cache_line_size set to 64 bytes
[    0.160687] e820: reserve RAM buffer [mem 0x0009b800-0x0009ffff]
[    0.160688] e820: reserve RAM buffer [mem 0xbfef0000-0xbfffffff]
[    0.160784] NetLabel: Initializing
[    0.160787] NetLabel:  domain hash size = 128
[    0.160788] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.160801] NetLabel:  unlabeled traffic allowed by default
[    0.160828] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.160828] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
[    0.160828] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.162072] Switched to clocksource hpet
[    0.166388] AppArmor: AppArmor Filesystem Enabled
[    0.166455] pnp: PnP ACPI init
[    0.166545] system 00:00: [io  0x1000-0x107f] could not be reserved
[    0.166548] system 00:00: [io  0x1080-0x10ff] has been reserved
[    0.166551] system 00:00: [io  0x1400-0x147f] has been reserved
[    0.166554] system 00:00: [io  0x1480-0x14ff] has been reserved
[    0.166556] system 00:00: [io  0x1800-0x187f] has been reserved
[    0.166559] system 00:00: [io  0x1880-0x18ff] has been reserved
[    0.166563] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.166668] system 00:01: [io  0x04d0-0x04d1] has been reserved
[    0.166672] system 00:01: [io  0x0295-0x0314] has been reserved
[    0.166674] system 00:01: [io  0x0880-0x088f] has been reserved
[    0.166677] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.166731] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.166890] pnp 00:03: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.167354] system 00:04: [mem 0xe0000000-0xefffffff] has been reserved
[    0.167358] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.167481] system 00:05: [mem 0x000d0000-0x000d3fff] has been reserved
[    0.167485] system 00:05: [mem 0x000d9000-0x000dbfff] has been reserved
[    0.167488] system 00:05: [mem 0x000f0000-0x000fbfff] could not be reserved
[    0.167491] system 00:05: [mem 0x000fc000-0x000fffff] could not be reserved
[    0.167494] system 00:05: [mem 0xbfef0000-0xbfefffff] could not be reserved
[    0.167496] system 00:05: [mem 0xffff0000-0xffffffff] has been reserved
[    0.167499] system 00:05: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.167502] system 00:05: [mem 0x00100000-0xbfeeffff] could not be reserved
[    0.167505] system 00:05: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.167508] system 00:05: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.167510] system 00:05: [mem 0xfeff0000] has been reserved
[    0.167514] system 00:05: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.167521] pnp: PnP ACPI: found 6 devices
[    0.176246] pci 0000:01:00.0: BAR 6: assigned [mem 0xdd000000-0xdd01ffff pref]
[    0.176251] pci 0000:00:02.0: PCI bridge to [bus 01]
[    0.176254] pci 0000:00:02.0:   bridge window [io  0x9000-0x9fff]
[    0.176260] pci 0000:00:02.0:   bridge window [mem 0xda000000-0xddffffff]
[    0.176264] pci 0000:00:02.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.176271] pci 0000:00:04.0: PCI bridge to [bus 02]
[    0.176281] pci 0000:00:0f.0: PCI bridge to [bus 03]
[    0.176288] pci 0000:00:15.0: PCI bridge to [bus 04]
[    0.176291] pci 0000:00:15.0:   bridge window [io  0x7000-0x8fff]
[    0.176295] pci 0000:00:15.0:   bridge window [mem 0xdfe00000-0xdfefffff]
[    0.176301] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.176303] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.176304] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.176306] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000dffff]
[    0.176308] pci_bus 0000:00: resource 8 [mem 0xbff00000-0xfebfffff]
[    0.176310] pci_bus 0000:01: resource 0 [io  0x9000-0x9fff]
[    0.176311] pci_bus 0000:01: resource 1 [mem 0xda000000-0xddffffff]
[    0.176313] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.176315] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.176317] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.176318] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.176320] pci_bus 0000:03: resource 7 [mem 0x000c0000-0x000dffff]
[    0.176322] pci_bus 0000:03: resource 8 [mem 0xbff00000-0xfebfffff]
[    0.176323] pci_bus 0000:04: resource 0 [io  0x7000-0x8fff]
[    0.176325] pci_bus 0000:04: resource 1 [mem 0xdfe00000-0xdfefffff]
[    0.176350] NET: Registered protocol family 2
[    0.176562] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
[    0.176811] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.177161] TCP: Hash tables configured (established 65536 bind 65536)
[    0.177202] TCP: reno registered
[    0.177213] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.177264] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.177341] NET: Registered protocol family 1
[    0.177678] ACPI: PCI Interrupt Link [AUBA] enabled at IRQ 23
[    0.248354] ACPI: PCI Interrupt Link [AUS2] enabled at IRQ 22
[    0.248567] pci 0000:01:00.0: Video device with shadowed ROM
[    0.248571] pci 0000:04:00.0: async suspend disabled to avoid multi-function power-on ordering issue
[    0.248576] pci 0000:04:00.1: async suspend disabled to avoid multi-function power-on ordering issue
[    0.248581] PCI: CLS 64 bytes, default 64
[    0.248631] Trying to unpack rootfs image as initramfs...
[    0.631848] Freeing initrd memory: 26192K (ffff880034cc8000 - ffff88003665c000)
[    0.631894] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.631900] software IO TLB [mem 0xbbef0000-0xbfef0000] (64MB) mapped at [ffff8800bbef0000-ffff8800bfeeffff]
[    0.632212] microcode: CPU0 sig=0x1067a, pf=0x10, revision=0xa07
[    0.632228] microcode: CPU1 sig=0x1067a, pf=0x10, revision=0xa07
[    0.632248] microcode: CPU2 sig=0x1067a, pf=0x10, revision=0xa07
[    0.632267] microcode: CPU3 sig=0x1067a, pf=0x10, revision=0xa07
[    0.632342] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.632393] Scanning for low memory corruption every 60 seconds
[    0.632671] futex hash table entries: 1024 (order: 4, 65536 bytes)
[    0.632689] Initialise system trusted keyring
[    0.632707] audit: initializing netlink subsys (disabled)
[    0.632727] audit: type=2000 audit(1455293963.632:1): initialized
[    0.633034] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.634704] zpool: loaded
[    0.634706] zbud: loaded
[    0.634864] VFS: Disk quotas dquot_6.5.2
[    0.634900] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.635405] fuse init (API version 7.23)
[    0.635550] Key type big_key registered
[    0.636371] Key type asymmetric registered
[    0.636375] Asymmetric key parser 'x509' registered
[    0.636415] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.636490] io scheduler noop registered
[    0.636494] io scheduler deadline registered (default)
[    0.636526] io scheduler cfq registered
[    0.636829] ACPI: PCI Interrupt Link [AXV5] enabled at IRQ 16
[    0.637100] ACPI: PCI Interrupt Link [AXV6] enabled at IRQ 16
[    0.637274] pcieport 0000:00:02.0: Signaling PME through PCIe PME interrupt
[    0.637278] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    0.637282] pcie_pme 0000:00:02.0:pcie01: service driver pcie_pme loaded
[    0.637301] pcieport 0000:00:04.0: Signaling PME through PCIe PME interrupt
[    0.637306] pcie_pme 0000:00:04.0:pcie01: service driver pcie_pme loaded
[    0.637319] pcieport 0000:00:15.0: Signaling PME through PCIe PME interrupt
[    0.637322] pci 0000:04:00.0: Signaling PME through PCIe PME interrupt
[    0.637324] pci 0000:04:00.1: Signaling PME through PCIe PME interrupt
[    0.637327] pcie_pme 0000:00:15.0:pcie01: service driver pcie_pme loaded
[    0.637334] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.637350] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.637384] vesafb: mode is 640x480x32, linelength=2560, pages=0
[    0.637386] vesafb: scrolling: redraw
[    0.637388] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.642158] vesafb: framebuffer at 0xdb000000, mapped to 0xffffc90010e80000, using 1216k, total 1216k
[    0.643449] Console: switching to colour frame buffer device 80x30
[    0.644676] fb0: VESA VGA frame buffer device
[    0.644725] intel_idle: does not run on family 6 model 23
[    0.644800] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.644853] ACPI: Power Button [PWRB]
[    0.644923] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.646518] ACPI: Power Button [PWRF]
[    0.647674] GHES: HEST is not enabled!
[    0.648635] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.652034] Linux agpgart interface v0.103
[    0.654613] brd: module loaded
[    0.656347] loop: module loaded
[    0.657358] libphy: Fixed MDIO Bus: probed
[    0.658159] tun: Universal TUN/TAP device driver, 1.6
[    0.658960] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.659862] PPP generic driver version 2.4.2
[    0.660785] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.661621] ehci-pci: EHCI PCI platform driver
[    0.662589] ehci-pci 0000:00:0b.1: EHCI Host Controller
[    0.663437] ehci-pci 0000:00:0b.1: new USB bus registered, assigned bus number 1
[    0.665142] ehci-pci 0000:00:0b.1: debug port 1
[    0.666029] ehci-pci 0000:00:0b.1: cache line size of 64 is not supported
[    0.666044] ehci-pci 0000:00:0b.1: irq 22, io mem 0xdfffe000
[    0.676018] ehci-pci 0000:00:0b.1: USB 2.0 started, EHCI 1.00
[    0.676898] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.677754] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.679439] usb usb1: Product: EHCI Host Controller
[    0.680291] usb usb1: Manufacturer: Linux 3.19.0-49-generic ehci_hcd
[    0.681132] usb usb1: SerialNumber: 0000:00:0b.1
[    0.682097] hub 1-0:1.0: USB hub found
[    0.682913] hub 1-0:1.0: 10 ports detected
[    0.683881] ehci-platform: EHCI generic platform driver
[    0.684695] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.685494] ohci-pci: OHCI PCI platform driver
[    0.686390] ohci-pci 0000:00:0b.0: OHCI PCI host controller
[    0.687177] ohci-pci 0000:00:0b.0: new USB bus registered, assigned bus number 2
[    0.688777] ohci-pci 0000:00:0b.0: irq 23, io mem 0xdffff000
[    0.746040] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    0.746861] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.748514] usb usb2: Product: OHCI PCI host controller
[    0.749358] usb usb2: Manufacturer: Linux 3.19.0-49-generic ohci_hcd
[    0.750210] usb usb2: SerialNumber: 0000:00:0b.0
[    0.751178] hub 2-0:1.0: USB hub found
[    0.752020] hub 2-0:1.0: 10 ports detected
[    0.753033] ohci-platform: OHCI generic platform driver
[    0.753861] uhci_hcd: USB Universal Host Controller Interface driver
[    0.754751] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.755575] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.758061] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.759033] mousedev: PS/2 mouse device common for all mice
[    0.760028] rtc_cmos 00:02: RTC can wake from S4
[    0.761013] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.761881] rtc_cmos 00:02: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    0.763559] i2c /dev entries driver
[    0.764486] device-mapper: uevent: version 1.0.3
[    0.765415] device-mapper: ioctl: 4.29.0-ioctl (2014-10-28) initialised: dm-devel@redhat.com
[    0.767143] ledtrig-cpu: registered to indicate activity on CPUs
[    0.768261] PCCT header not found.
[    0.769221] TCP: cubic registered
[    0.770183] NET: Registered protocol family 10
[    0.771303] NET: Registered protocol family 17
[    0.772166] Key type dns_resolver registered
[    0.773300] Loading compiled-in X.509 certificates
[    0.774972] Loaded X.509 cert 'Magrathea: Glacier signing key: a932dc237895a44d3959bf91a3566a20ee211f37'
[    0.776651] registered taskstats version 1
[    0.779171] Key type trusted registered
[    0.781776] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.784644] Key type encrypted registered
[    0.785482] AppArmor: AppArmor sha1 policy hashing enabled
[    0.786329] ima: No TPM chip found, activating TPM-bypass!
[    0.787185] evm: HMAC attrs: 0x1
[    0.788405]   Magic number: 4:843:337
[    0.789248] tty tty58: hash matches
[    0.790123] rtc_cmos 00:02: setting system clock to 2016-02-12 16:19:23 UTC (1455293963)
[    0.791843] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.792689] EDD information not available.
[    0.793559] PM: Hibernation image not present or could not be loaded.
[    0.794002] Freeing unused kernel memory: 1408K (ffffffff81d27000 - ffffffff81e87000)
[    0.795672] Write protecting the kernel read-only data: 12288k
[    0.796815] Freeing unused kernel memory: 256K (ffff8800017c0000 - ffff880001800000)
[    0.798700] Freeing unused kernel memory: 336K (ffff880001bac000 - ffff880001c00000)
[    0.813670] systemd-udevd[120]: starting version 204
[    0.839182] [drm] Initialized drm 1.1.0 20060810
[    0.840191] pata_amd 0000:00:0d.0: version 0.4.1
[    0.843559] pata_jmicron 0000:04:00.1: enabling device (0000 -> 0001)
[    0.846833] scsi host1: pata_jmicron
[    0.848039] scsi host0: pata_amd
[    0.848804] scsi host2: pata_jmicron
[    0.848856] ata3: PATA max UDMA/100 cmd 0x8c00 ctl 0x8800 bmdma 0x7c00 irq 16
[    0.848857] ata4: PATA max UDMA/100 cmd 0x8400 ctl 0x8000 bmdma 0x7c08 irq 16
[    0.849626] ahci 0000:04:00.0: version 3.0
[    0.849925] ACPI: PCI Interrupt Link [AXV8] enabled at IRQ 16
[    0.855944] scsi host3: pata_amd
[    0.856989] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xec00 irq 14
[    0.857910] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xec08 irq 15
[    0.858515] wmi: Mapper loaded
[    0.859651] sata_nv 0000:00:0e.0: version 3.5
[    0.859854] ACPI: PCI Interrupt Link [ASA0] enabled at IRQ 21
[    0.860746] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    0.862153] scsi host4: sata_nv
[    0.863188] scsi host5: sata_nv
[    0.864092] ata5: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 21
[    0.864961] ata6: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 21
[    0.866020] ACPI: PCI Interrupt Link [ASA1] enabled at IRQ 20
[    0.866860] sata_nv 0000:00:0e.1: Using SWNCQ mode
[    0.873709] scsi host6: sata_nv
[    0.873768] ahci 0000:04:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    0.873770] ahci 0000:04:00.0: flags: 64bit ncq led clo pmp pio
[    0.877567] scsi host7: ahci
[    0.878488] scsi host8: sata_nv
[    0.879345] ata7: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc400 irq 20
[    0.879569] checking generic (db000000 130000) vs hw (c0000000 10000000)
[    0.879570] checking generic (db000000 130000) vs hw (da000000 2000000)
[    0.879571] fb: switching to nouveaufb from VESA VGA
[    0.880119] scsi host9: ahci
[    0.880193] ata9: SATA max UDMA/133 abar m8192@0xdfefe000 port 0xdfefe100 irq 16
[    0.880196] ata10: SATA max UDMA/133 abar m8192@0xdfefe000 port 0xdfefe180 irq 16
[    0.884966] ata8: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc408 irq 20
[    0.884993] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    0.885232] ACPI: PCI Interrupt Link [AMAC] enabled at IRQ 23
[    0.887217] Console: switching to colour dummy device 80x25
[    0.887706] nouveau  [  DEVICE][0000:01:00.0] BOOT0  : 0x450100a2
[    0.887710] nouveau  [  DEVICE][0000:01:00.0] Chipset: G80 (NV50)
[    0.887712] nouveau  [  DEVICE][0000:01:00.0] Family : NV50
[    0.994466] nouveau  [   VBIOS][0000:01:00.0] using image from PRAMIN
[    0.994549] nouveau  [   VBIOS][0000:01:00.0] BIT signature found
[    0.994552] nouveau  [   VBIOS][0000:01:00.0] version 60.80.0a.00.00
[    1.014752] nouveau  [     PMC][0000:01:00.0] MSI interrupts enabled
[    1.014778] nouveau  [     PFB][0000:01:00.0] RAM type: GDDR3
[    1.014781] nouveau  [     PFB][0000:01:00.0] RAM size: 768 MiB
[    1.014783] nouveau  [     PFB][0000:01:00.0]    ZCOMP: 3142 tags
[    1.049254] nouveau  [  PTHERM][0000:01:00.0] FAN control: none / external
[    1.049263] nouveau  [  PTHERM][0000:01:00.0] fan management: automatic
[    1.049266] nouveau  [  PTHERM][0000:01:00.0] internal sensor: yes
[    1.069124] nouveau  [     CLK][0000:01:00.0] 20: core 576 MHz shader 1350 MHz memory 900 MHz
[    1.069158] nouveau  [     CLK][0000:01:00.0] --: core 198 MHz shader 1188 MHz memory 396 MHz
[    1.069327] [TTM] Zone  kernel: Available graphics memory: 4087460 kiB
[    1.069329] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB
[    1.069331] [TTM] Initializing pool allocator
[    1.069337] [TTM] Initializing DMA pool allocator
[    1.069347] nouveau  [     DRM] VRAM: 768 MiB
[    1.069349] nouveau  [     DRM] GART: 1048576 MiB
[    1.069352] nouveau  [     DRM] BIT table 'A' not found
[    1.069355] nouveau  [     DRM] TMDS table version 2.0
[    1.069357] nouveau  [     DRM] DCB version 4.0
[    1.069360] nouveau  [     DRM] DCB outp 00: 04000320 00000028
[    1.069362] nouveau  [     DRM] DCB outp 01: 01000322 00000030
[    1.069364] nouveau  [     DRM] DCB outp 02: 02011310 00000028
[    1.069367] nouveau  [     DRM] DCB outp 03: 02011312 00000030
[    1.069369] nouveau  [     DRM] DCB outp 04: 010223f1 00c1c020
[    1.069371] nouveau  [     DRM] DCB conn 00: 1030
[    1.069373] nouveau  [     DRM] DCB conn 01: 2130
[    1.069376] nouveau  [     DRM] DCB conn 02: 0210
[    1.069378] nouveau  [     DRM] DCB conn 03: 0211
[    1.069380] nouveau  [     DRM] DCB conn 04: 0213
[    1.077070] nouveau W[     DRM] failed to create encoder 0/1/0: -19
[    1.077073] nouveau W[     DRM] TV-1 has no encoders, removing
[    1.077100] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    1.077102] [drm] Driver supports precise vblank timestamp query.
[    1.087593] nouveau  [     DRM] MM: using M2MF for buffer copies
[    1.147230] nouveau  [     DRM] allocated 1024x768 fb: 0x70000, bo ffff880232a04000
[    1.147305] fbcon: nouveaufb (fb0) is primary device
[    1.175356] ata2: port disabled--ignoring
[    1.200042] ata9: SATA link down (SStatus 0 SControl 300)
[    1.204046] ata10: SATA link down (SStatus 0 SControl 300)
[    1.214282] Console: switching to colour frame buffer device 128x48
[    1.214996] nouveau 0000:01:00.0: fb0: nouveaufb frame buffer device
[    1.215022] nouveau 0000:01:00.0: registered panic notifier
[    1.216041] [drm] Initialized nouveau 1.2.1 20120801 for 0000:01:00.0 on minor 0
[    1.332029] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.352026] ata7: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.356146] ata5.00: ATAPI: LITE-ON DVDRW LH-20A1S, 9L05, max UDMA/100
[    1.360305] ata7.00: ATA-8: Hitachi HUA723030ALA640, MKAOA580, max UDMA/133
[    1.360317] ata7.00: 5860533168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.376296] ata7.00: configured for UDMA/133
[    1.388145] ata5.00: configured for UDMA/100
[    1.390033] scsi 4:0:0:0: CD-ROM            LITE-ON  DVDRW LH-20A1S   9L05 PQ: 0 ANSI: 5
[    1.406206] sr 4:0:0:0: [sr0] scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.406216] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.406394] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    1.406476] sr 4:0:0:0: Attached scsi generic sg0 type 5
[    1.408508] forcedeth 0000:00:11.0: ifname eth0, PHY OUI 0x50ef @ 0, addr 00:04:4b:17:22:9a
[    1.408516] forcedeth 0000:00:11.0: highdma csum vlan pwrctl mgmt gbit lnktim msi desc-v3
[    1.408742] ACPI: PCI Interrupt Link [AMA1] enabled at IRQ 22
[    1.628018] tsc: Refined TSC clocksource calibration: 2999.958 MHz
[    1.872025] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.892810] ata6.00: ATA-8: WDC WD5000AAKS-00UU3A0, 01.03B01, max UDMA/133
[    1.893022] ata6.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.908837] ata6.00: configured for UDMA/133
[    1.909119] scsi 5:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-0 3B01 PQ: 0 ANSI: 5
[    1.909479] sd 5:0:0:0: Attached scsi generic sg1 type 0
[    1.909482] sd 5:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.909525] sd 5:0:0:0: [sda] Write Protect is off
[    1.909526] sd 5:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.909545] sd 5:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.912233] scsi 6:0:0:0: Direct-Access     ATA      Hitachi HUA72303 A580 PQ: 0 ANSI: 5
[    1.913018] sd 6:0:0:0: [sdb] 5860533168 512-byte logical blocks: (3.00 TB/2.72 TiB)
[    1.913060] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    1.914420] sd 6:0:0:0: [sdb] Write Protect is off
[    1.915116] sd 6:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.915151] sd 6:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.932461] forcedeth 0000:00:12.0: ifname eth1, PHY OUI 0x50ef @ 1, addr 00:04:4b:17:22:9b
[    1.932683] forcedeth 0000:00:12.0: highdma csum vlan pwrctl mgmt gbit lnktim msi desc-v3
[    1.932689]  sda: sda1 sda2 < sda5 >
[    1.932929] sd 5:0:0:0: [sda] Attached SCSI disk
[    1.935105] ACPI: PCI Interrupt Link [ASA2] enabled at IRQ 21
[    1.935771] sata_nv 0000:00:0e.2: Using SWNCQ mode
[    1.937082] scsi host10: sata_nv
[    1.937606] scsi host11: sata_nv
[    1.938418] ata11: SATA max UDMA/133 cmd 0xc000 ctl 0xbc00 bmdma 0xb000 irq 21
[    1.939209] ata12: SATA max UDMA/133 cmd 0xb800 ctl 0xb400 bmdma 0xb008 irq 21
[    1.954446]  sdb: sdb1 sdb9
[    1.954959] sd 6:0:0:0: [sdb] Attached SCSI disk
[    2.380026] ata8: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.388284] ata8.00: ATA-8: Hitachi HUA723030ALA640, MKAOA580, max UDMA/133
[    2.388544] ata8.00: 5860533168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.404270] ata8.00: configured for UDMA/133
[    2.404601] scsi 8:0:0:0: Direct-Access     ATA      Hitachi HUA72303 A580 PQ: 0 ANSI: 5
[    2.405224] sd 8:0:0:0: [sdc] 5860533168 512-byte logical blocks: (3.00 TB/2.72 TiB)
[    2.405255] sd 8:0:0:0: Attached scsi generic sg3 type 0
[    2.406817] sd 8:0:0:0: [sdc] Write Protect is off
[    2.407596] sd 8:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    2.407612] sd 8:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.408043] ata11: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.416279] ata11.00: ATA-8: Hitachi HUA723030ALA640, MKAOA580, max UDMA/133
[    2.416564] ata11.00: 5860533168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.432292] ata11.00: configured for UDMA/133
[    2.432648] scsi 10:0:0:0: Direct-Access     ATA      Hitachi HUA72303 A580 PQ: 0 ANSI: 5
[    2.433327] sd 10:0:0:0: Attached scsi generic sg4 type 0
[    2.433335] sd 10:0:0:0: [sdd] 5860533168 512-byte logical blocks: (3.00 TB/2.72 TiB)
[    2.433377] sd 10:0:0:0: [sdd] Write Protect is off
[    2.433379] sd 10:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    2.433398] sd 10:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.450608]  sdc: sdc1 sdc9
[    2.451060] sd 8:0:0:0: [sdc] Attached SCSI disk
[    2.469193]  sdd: sdd1 sdd9
[    2.469704] sd 10:0:0:0: [sdd] Attached SCSI disk
[    2.628091] Switched to clocksource tsc
[    2.904020] ata12: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.912273] ata12.00: ATA-8: Hitachi HUA723030ALA640, MKAOA580, max UDMA/133
[    2.912552] ata12.00: 5860533168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.928266] ata12.00: configured for UDMA/133
[    2.928596] scsi 11:0:0:0: Direct-Access     ATA      Hitachi HUA72303 A580 PQ: 0 ANSI: 5
[    2.929208] sd 11:0:0:0: Attached scsi generic sg5 type 0
[    2.929210] sd 11:0:0:0: [sde] 5860533168 512-byte logical blocks: (3.00 TB/2.72 TiB)
[    2.929243] sd 11:0:0:0: [sde] Write Protect is off
[    2.929244] sd 11:0:0:0: [sde] Mode Sense: 00 3a 00 00
[    2.929259] sd 11:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.960087]  sde: sde1 sde9
[    2.960516] sd 11:0:0:0: [sde] Attached SCSI disk
[    3.062522] random: nonblocking pool is initialized
[    3.844028] floppy0: no floppy controllers found
[    3.923844] md: linear personality registered for level -1
[    3.926146] md: multipath personality registered for level -4
[    3.928372] md: raid0 personality registered for level 0
[    3.930918] md: raid1 personality registered for level 1
[    4.000007] raid6: sse2x1    4986 MB/s
[    4.068004] raid6: sse2x2    5284 MB/s
[    4.136009] raid6: sse2x4    8749 MB/s
[    4.136017] raid6: using algorithm sse2x4 (8749 MB/s)
[    4.136020] raid6: using ssse3x2 recovery algorithm
[    4.137181] xor: measuring software checksum speed
[    4.176007]    prefetch64-sse: 12514.000 MB/sec
[    4.216007]    generic_sse: 11040.000 MB/sec
[    4.216016] xor: using function: prefetch64-sse (12514.000 MB/sec)
[    4.217075] async_tx: api initialized (async)
[    4.223413] md: raid6 personality registered for level 6
[    4.223419] md: raid5 personality registered for level 5
[    4.223423] md: raid4 personality registered for level 4
[    4.228417] md: raid10 personality registered for level 10
[    9.259390] EXT4-fs (dm-0): INFO: recovery required on readonly filesystem
[    9.259397] EXT4-fs (dm-0): write access will be enabled during recovery
[   10.772139] EXT4-fs (dm-0): recovery complete
[   10.776440] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
[   12.304067] zavl: module license 'CDDL' taints kernel.
[   12.304080] Disabling lock debugging due to kernel taint
[   12.304107] zavl: module verification failed: signature and/or  required key missing - tainting kernel
[   12.329378] SPL: Loaded module v0.6.5.4-1~trusty
[   12.645498] ZFS: Loaded module v0.6.5.4-1~trusty, ZFS pool version 5000, ZFS filesystem version 5
[   19.397074] SPL: using hostid 0x007f0101
[   21.115959] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
[   21.194828] EXT4-fs (sda1): mounting ext2 file system using the ext4 subsystem
[   21.233991] EXT4-fs (sda1): mounted filesystem without journal. Opts: (null)
[   21.906406] systemd-udevd[1900]: starting version 204
[   21.926628] lp: driver loaded but no devices found
[   22.083169] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   22.085308] i2c i2c-4: nForce2 SMBus adapter at 0xf400
[   22.085674] i2c i2c-5: nForce2 SMBus adapter at 0xf000
[   22.141854] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 23
[   22.141866] snd_hda_intel 0000:00:0f.1: Disabling MSI
[   22.278800] audit: type=1400 audit(1455293984.982:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=2040 comm="apparmor_parser"
[   22.278807] audit: type=1400 audit(1455293984.982:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=2040 comm="apparmor_parser"
[   22.278811] audit: type=1400 audit(1455293984.982:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=2040 comm="apparmor_parser"
[   22.278819] audit: type=1400 audit(1455293984.982:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=2041 comm="apparmor_parser"
[   22.278835] audit: type=1400 audit(1455293984.982:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=2041 comm="apparmor_parser"
[   22.278839] audit: type=1400 audit(1455293984.982:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=2041 comm="apparmor_parser"
[   22.279168] audit: type=1400 audit(1455293984.982:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=2040 comm="apparmor_parser"
[   22.279173] audit: type=1400 audit(1455293984.982:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=2040 comm="apparmor_parser"
[   22.279233] audit: type=1400 audit(1455293984.982:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=2041 comm="apparmor_parser"
[   22.279237] audit: type=1400 audit(1455293984.982:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=2041 comm="apparmor_parser"
[   22.533529] forcedeth 0000:00:11.0 eth0: MSI enabled
[   22.876016] sound hdaudioC0D0: autoconfig: line_outs=4 (0x14/0x15/0x16/0x17/0x0) type:line
[   22.876021] sound hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   22.876024] sound hdaudioC0D0:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[   22.876026] sound hdaudioC0D0:    mono: mono_out=0x0
[   22.876029] sound hdaudioC0D0:    dig-out=0x11/0x1e
[   22.876031] sound hdaudioC0D0:    inputs:
[   22.876034] sound hdaudioC0D0:      Front Mic=0x19
[   22.876037] sound hdaudioC0D0:      Rear Mic=0x18
[   22.876039] sound hdaudioC0D0:      Line=0x1a
[   22.876041] sound hdaudioC0D0:    dig-in=0x1f
[   23.714804] init: failsafe main process (2105) killed by TERM signal
[   24.733717] input: HDA NVidia Front Mic as /devices/pci0000:00/0000:00:0f.1/sound/card0/input3
[   24.733801] input: HDA NVidia Rear Mic as /devices/pci0000:00/0000:00:0f.1/sound/card0/input4
[   24.733880] input: HDA NVidia Line as /devices/pci0000:00/0000:00:0f.1/sound/card0/input5
[   24.737403] input: HDA NVidia Line Out Front as /devices/pci0000:00/0000:00:0f.1/sound/card0/input6
[   24.737714] input: HDA NVidia Line Out Surround as /devices/pci0000:00/0000:00:0f.1/sound/card0/input7
[   24.738273] input: HDA NVidia Line Out CLFE as /devices/pci0000:00/0000:00:0f.1/sound/card0/input8
[   24.738853] input: HDA NVidia Line Out Side as /devices/pci0000:00/0000:00:0f.1/sound/card0/input9
[   24.738950] input: HDA NVidia Front Headphone as /devices/pci0000:00/0000:00:0f.1/sound/card0/input10
[   24.997438] init: samba-ad-dc main process (2415) terminated with status 1
[   25.100034] floppy0: no floppy controllers found
[   26.984188] Ebtables v2.0 registered
[   27.057725] ip_tables: (C) 2000-2006 Netfilter Core Team
[   27.064876] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   27.432679] init: plymouth-upstart-bridge main process ended, respawning
[   29.236095] bridge: automatic filtering via arp/ip/ip6tables has been deprecated. Update your scripts to load br_netfilter if you need this.
[   29.352225] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   45.316492] cgroup: systemd-logind (1958) created nested cgroup for controller "memory" which has incomplete hierarchy support. Nested cgroups may change behavior in the future.
[   45.316495] cgroup: "memory" requires setting use_hierarchy to 1 on the root
[  109.571207] init: tty1 main process ended, respawning
```

This is a USB2 key and the adapter is a USB3. But I don't think that matters.

lsusb output before and after hasn't changed:

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

I'll start comparing the two large outputs above. At first glance they're the same.

Thanks!

I see no pertinent difference. But Ubuntu and Linux are new to me.

Here's the output of a print all in parted:

```
GNU Parted 2.3Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print all
Model: ATA WDC WD5000AAKS-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size   Type      File system  Flags
 1      1049kB  256MB  255MB  primary   ext2         boot
 2      257MB   500GB  500GB  extended
 5      257MB   500GB  500GB  logical                lvm




Model: ATA Hitachi HUA72303 (scsi)
Disk /dev/sdb: 3001GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start   End     Size    File system  Name  Flags
 1      1049kB  3001GB  3001GB  zfs          zfs
 9      3001GB  3001GB  8389kB




Model: ATA Hitachi HUA72303 (scsi)
Disk /dev/sdc: 3001GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start   End     Size    File system  Name  Flags
 1      1049kB  3001GB  3001GB  zfs          zfs
 9      3001GB  3001GB  8389kB




Model: ATA Hitachi HUA72303 (scsi)
Disk /dev/sdd: 3001GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start   End     Size    File system  Name  Flags
 1      1049kB  3001GB  3001GB  zfs          zfs
 9      3001GB  3001GB  8389kB




Model: ATA Hitachi HUA72303 (scsi)
Disk /dev/sde: 3001GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start   End     Size    File system  Name  Flags
 1      1049kB  3001GB  3001GB  zfs          zfs
 9      3001GB  3001GB  8389kB




Error: /dev/mapper/kazz--u0a1--vg-swap_1: unrecognised disk label


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/kazz--u0a1--vg-root: 241GB
Sector size (logical/physical): 512B/512B
Partition Table: loop


Number  Start  End    Size   File system  Flags
 1      0.00B  241GB  241GB  ext4

```

Does this imply that the PC is not recognizing the adapter?

Again, thanks!

---

### Post by Yellow Pasque on 2016-02-12
Let's start with something simpler. See if lspci recognizes the device:
```
sudo update-pciids
sudo lspci -k | grep -iA 3 usb
```

---

### Post by kazz2 on 2016-02-12
sudo update-pciids:

```
Downloaded daily snapshot dated 2016-02-06 03:15:02
```

sudo lspci -k | grep -iA 3 usb:

```
00:0b.0 USB controller: NVIDIA Corporation MCP55 USB Controller (rev a1)        Subsystem: NVIDIA Corporation Device c73e
        Kernel driver in use: ohci-pci
00:0b.1 USB controller: NVIDIA Corporation MCP55 USB Controller (rev a2)
        Subsystem: NVIDIA Corporation Device c73e
        Kernel driver in use: ehci-pci
00:0d.0 IDE interface: NVIDIA Corporation MCP55 IDE (rev a1)
```

I assume this means Ubuntu's only seeing the onboard USB hardware.

Question: If I rearrange adapters in slots, in this case GPU & add-in USB3 adapter, will the current installation adapt to it OK or do I need to make changes before shutdown? I'd like to move the add-in adapter closest to the CPU and the GPU another x16 slot further away as a test.

Thanks!

---

### Post by Yellow Pasque on 2016-02-12
> I assume this means Ubuntu's only seeing the onboard USB hardware.

It certainly looks that way. The adapter uses the asmedia 1062 chipset from what I can tell, which has been supported in Linux kernel for a while (should work out of the box on any Ubuntu version that has a 3.x kernel, including Ubuntu 12.04).

> Question: If I rearrange adapters in slots, in this case GPU & add-in USB3 adapter, will the current installation adapt to it OK or do I need to make changes before shutdown? I'd like to move the add-in adapter closest to the CPU and the GPU another x16 slot further away as a test.

It should work (and no, you shouldn't have to change anything in the OS). The mobo you have has three PCI-e x16 slots. Only the top two slots are PCI-e 2.0, so if you have the USB adapter plugged into the bottom slot, move it into one of the other two slots. As long as you have your GPU and USB adapter plugged into the top two slots, it should work regardless of which one is in the top and middle. Just don't use the bottom slot unless you have a device that only needs PCI-e 1.0.

One last note: the USB adapter has a supplemental power connector (looks like a SATA power connector to me). Did you connect it? I think it'll be needed if you intend to charge devices the use "USB Power Delivery 2.0" since it requires up to 100W and the PCIe slot can only support 75W maximum according to specification.

---

### Post by kazz2 on 2016-02-12
I'm used to some old server OSs that would require uninstalling drivers, shutdown, move hardware, re-install drivers. Good to know Linux is smarter than that!

And that's why I was asking. I believe it to be a slot issue. The GPU is supported in any of the three PCI-e x16 slots for SLI (I was running SLI in Windows on this motherboard and this GPU at one time successfully) so that's flexible. I have the USB adapter in the smaller PCI slot and it requires PCI-e 2.0. So I'm going to move the GPU down a x16 slot and use the now-free x16 slot for the adapter. With any luck she'll immediately show up upon reboot.

I don't intend to power anything by USB. This adapter will serve external, USB3 hard drives for backup. With that antique GPU, an optical drive, the motherboard, and five hard drives I don't want to spread anymore power out if I don't have to!

Thanks!

---

### Post by Yellow Pasque on 2016-02-12
> **kazz2 said:**
> I have the USB adapter in the smaller PCI slot

Huh? How did you manage that? It's an x4 card and won't physically fit in the x1 slot(s) on your mobo (unless they're open-ended, but the card won't work that way). The only other "smaller" slots on your mobo are PCI (non-express) slots. If you crammed it into a regular PCI slot, it won't work for obvious reasons. [https://en.wikipedia.org/wiki/PCI_Express](https://en.wikipedia.org/wiki/PCI_Express)

---

### Post by kazz2 on 2016-02-12
I understand the headscratching! Many errors and bad assumptions on my part.

First, the USB3 adapter was in the third x16 slot. Also, in a single-GPU configuration the GPU MUST be installed in the first x16 slot.

So first I moved the USB3 adapter to the 2nd x16 slot. No joy. Then added power to that adapter. Still no joy.

At this point I'm going to have to remove the adapter, put it in another (Windows) PC and see if it works at all.

Thanks.

---

### Post by kazz2 on 2016-02-12
The adapter is not identified when installed in an EVGA X58 SLI motherboard under Win10-64 or Win7-64, either. I've asked the mfr for a replacement. We'll see how that goes.

In the meantime, does anyone have a 3rd-party USB 3.0 adapter they would recommend for my server?

Thank you!

---

### Post by Yellow Pasque on 2016-02-12
> In the meantime, does anyone have a 3rd-party USB 3.0 adapter they would recommend for my server?


You got a DOA card/device. It happens... If the card wasn't defective, it should have worked just fine under Linux. I don't see that as a reason to buy something different. Hopefully, you'll get a replacement card at no charge, slap it in the (correct) slot, and can focus on the next obstacle life throws your way. Good luck.

---

### Post by kazz2 on 2016-02-12
Yep, I know. It just sucks when a $25 part stops your whole build. I'd be burning backups, etc. all weekend and be live Monday.

Patience.

Thanks for all your time and help!

---

### Post by kazz2 on 2016-02-18
Still arguing with Highpoint. Went to Best Buy. I just installed the Insignia 2-port USB 3.0 adapter (without connecting power) and Ubuntu immediately identified it.  Now to craft a backup script and get it cron'd.

Thanks again to all.

---

