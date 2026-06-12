---
title: "nVidia MCP 55 SATA and MSI interrupts"
date: 2013-08-13
forum: Hardware
---

### Post by Peter_Saisanas on 2013-08-13
Hi,

    I have installed Ubuntu 13.4 64 bit with latest updates on a HP xw9400 workstation.

This platform uses the nVidia nForce 3600 professional chipset, in a nutshell it basically is an nForce MCP55 chipset based SMP / NUMA AMD Opteron platform. Currently it is configured with dual Opteron 2389 processors and 16GB of RAM (not that this has anything to do with the problem).

    Currently i am trying to optimise the system and i have started setting up all devices where possible to use MSI interrupts. According to lspci, this device suports MSI interrupts.

    So far so good, but when configuring the nVidia MCP55 SATA controller (or more specifically the sata_nv kernel module) to enable MSI interrupts i get a 30 second timeout when booting the system with NCQ issues on the SATA controller. This SATA controller has the bootable SATA HDD attached and errors occur around the 32 second mark.

    After the NCQ issue has occured, the system completes bootup and works fine without any further issues, note that this only occurs when using MSI interrupts and initially booting up. I havent seen the kernel spit out any further errors in the dmesg log after running the system.

    The dmesg log, 

```
[    0.000000] Initializing cgroup subsys cpuset 
[    0.000000] Initializing cgroup subsys cpu 
[    0.000000] Linux version 3.8.0-27-generic (buildd@roseapple) (gcc version 4.7.3 (Ubuntu/Linaro 4.7.3-1ubuntu1) ) #40-Ubuntu SMP Tue Jul 9 00:17:05 UTC 2013 (Ubuntu 3.8.0-27.40-generic 3.8.13.4) 
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-27-generic root=UUID=5f55b8f6-1cbf-4a99-8ee0-fd783613d3d0 ro quiet splash vt.handoff=7 
[    0.000000] KERNEL supported cpus: 
[    0.000000]   Intel GenuineIntel 
[    0.000000]   AMD AuthenticAMD 
[    0.000000]   Centaur CentaurHauls 
[    0.000000] e820: BIOS-provided physical RAM map: 
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009bfff] usable 
[    0.000000] BIOS-e820: [mem 0x000000000009c000-0x000000000009ffff] reserved 
[    0.000000] BIOS-e820: [mem 0x00000000000e8e00-0x00000000000fffff] reserved 
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000dffc60ff] usable 
[    0.000000] BIOS-e820: [mem 0x00000000dffc6100-0x00000000dfffffff] reserved 
[    0.000000] BIOS-e820: [mem 0x00000000f0000000-0x00000000f7ffffff] reserved 
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000ffffffff] reserved 
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000041fffffff] usable 
[    0.000000] NX (Execute Disable) protection: active 
[    0.000000] SMBIOS 2.5 present. 
[    0.000000] DMI: Hewlett-Packard HP xw9400 Workstation/0A1Ch, BIOS 786D6 v04.03 12/10/2009 
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved 
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable 
[    0.000000] No AGP bridge found 
[    0.000000] e820: last_pfn = 0x420000 max_arch_pfn = 0x400000000 
[    0.000000] MTRR default type: uncachable 
[    0.000000] MTRR fixed ranges enabled: 
[    0.000000]   00000-9FFFF write-back 
[    0.000000]   A0000-BFFFF uncachable 
[    0.000000]   C0000-E7FFF write-protect 
[    0.000000]   E8000-EFFFF write-back 
[    0.000000]   F0000-FFFFF write-protect 
[    0.000000] MTRR variable ranges enabled: 
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back 
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back 
[    0.000000]   2 base 0000C0000000 mask FFFFE0000000 write-back 
[    0.000000]   3 disabled 
[    0.000000]   4 disabled 
[    0.000000]   5 disabled 
[    0.000000]   6 disabled 
[    0.000000]   7 disabled 
[    0.000000] TOM2: 0000000420000000 aka 16896M 
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106 
[    0.000000] e820: update [mem 0xe0000000-0xffffffff] usable ==> reserved 
[    0.000000] e820: last_pfn = 0xdffc6 max_arch_pfn = 0x400000000 
[    0.000000] found SMP MP-table at [mem 0x000fe700-0x000fe70f] mapped at [ffff8800000fe700] 
[    0.000000] initial memory mapped: [mem 0x00000000-0x1fffffff] 
[    0.000000] Base memory trampoline at [ffff880000096000] 96000 size 24576 
[    0.000000] Using GB pages for direct mapping 
[    0.000000] init_memory_mapping: [mem 0x00000000-0xdffc5fff] 
[    0.000000]  [mem 0x00000000-0xbfffffff] page 1G 
[    0.000000]  [mem 0xc0000000-0xdfdfffff] page 2M 
[    0.000000]  [mem 0xdfe00000-0xdffc5fff] page 4k 
[    0.000000] kernel direct mapping tables up to 0xdffc5fff @ [mem 0x1fffd000-0x1fffffff] 
[    0.000000] init_memory_mapping: [mem 0x100000000-0x41fffffff] 
[    0.000000]  [mem 0x100000000-0x3ffffffff] page 1G 
[    0.000000]  [mem 0x400000000-0x41fffffff] page 2M 
[    0.000000] kernel direct mapping tables up to 0x41fffffff @ [mem 0xdffc4000-0xdffc5fff] 
[    0.000000] RAMDISK: [mem 0x36766000-0x373aafff] 
[    0.000000] ACPI: RSDP 00000000000e8e10 00024 (v02 HP    ) 
[    0.000000] ACPI: XSDT 00000000dffc99f4 00074 (v01 HPQOEM SLIC-WKS 20091210      00000000) 
[    0.000000] ACPI: FACP 00000000dffc9b9c 000F4 (v03 HP     COBRA    00000001      00000000) 
[    0.000000] ACPI BIOS Bug: Warning: Optional FADT field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20121018/tbfadt-598) 
[    0.000000] ACPI: DSDT 00000000dffca082 02159 (v01 HP         DSDT 00000001 MSFT 0100000E) 
[    0.000000] ACPI: FACS 00000000dffc9700 00040 
[    0.000000] ACPI: SSDT 00000000dffcc1db 08688 (v02 HP      PROJECT 00000001 MSFT 0100000E) 
[    0.000000] ACPI: APIC 00000000dffc9c90 00108 (v01 HP     COBRA    00000001      00000000) 
[    0.000000] ACPI: ASF! 00000000dffc9de4 00063 (v32 HP     COBRA    00000001      00000000) 
[    0.000000] ACPI: WDRT 00000000dffc9e47 00047 (v01 HP     COBRA    00000001      00000000) 
[    0.000000] ACPI: SRAT 00000000dffc97ec 001D0 (v02 HP     COBRA    00000001      00000000) 
[    0.000000] ACPI: HPET 00000000dffc99bc 00038 (v01 HP     COBRA    00000001      00000000) 
[    0.000000] ACPI: MCFG 00000000dffc9e8e 0004C (v01 HP     COBRA    00000001      00000000) 
[    0.000000] ACPI: SLIC 00000000dffc9eda 00176 (v01 HPQOEM SLIC-WKS 00000001      00000000) 
[    0.000000] ACPI: TCPA 00000000dffca050 00032 (v01 HP     COBRA    00000001      00000000) 
[    0.000000] ACPI: Local APIC address 0xfee00000 
[    0.000000] SRAT: PXM 0 -> APIC 0x00 -> Node 0 
[    0.000000] SRAT: PXM 0 -> APIC 0x01 -> Node 0 
[    0.000000] SRAT: PXM 0 -> APIC 0x02 -> Node 0 
[    0.000000] SRAT: PXM 0 -> APIC 0x03 -> Node 0 
[    0.000000] SRAT: PXM 1 -> APIC 0x04 -> Node 1 
[    0.000000] SRAT: PXM 1 -> APIC 0x05 -> Node 1 
[    0.000000] SRAT: PXM 1 -> APIC 0x06 -> Node 1 
[    0.000000] SRAT: PXM 1 -> APIC 0x07 -> Node 1 
[    0.000000] SRAT: Node 0 PXM 0 [mem 0x00000000-0x0009ffff] 
[    0.000000] SRAT: Node 0 PXM 0 [mem 0x000e8000-0xdfffffff] 
[    0.000000] SRAT: Node 0 PXM 0 [mem 0x100000000-0x21fffffff] 
[    0.000000] SRAT: Node 1 PXM 1 [mem 0x220000000-0x41fffffff] 
[    0.000000] NUMA: Node 0 [mem 0x00000000-0x0009ffff] + [mem 0x000e8000-0xdfffffff] -> [mem 0x00000000-0xdfffffff] 
[    0.000000] NUMA: Node 0 [mem 0x00000000-0xdfffffff] + [mem 0x100000000-0x21fffffff] -> [mem 0x00000000-0x21fffffff] 
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x21fffffff] 
[    0.000000]   NODE_DATA [mem 0x21fffb000-0x21fffffff] 
[    0.000000] Initmem setup node 1 [mem 0x220000000-0x41fffffff] 
[    0.000000]   NODE_DATA [mem 0x41fffb000-0x41fffffff] 
[    0.000000]  [ffffea0000000000-ffffea00087fffff] PMD -> [ffff880217e00000-ffff88021fdfffff] on node 0 
[    0.000000]  [ffffea0008800000-ffffea00107fffff] PMD -> [ffff880417600000-ffff88041f5fffff] on node 1 
[    0.000000] Zone ranges: 
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff] 
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff] 
[    0.000000]   Normal   [mem 0x100000000-0x41fffffff] 
[    0.000000] Movable zone start for each node 
[    0.000000] Early memory node ranges 
[    0.000000]   node   0: [mem 0x00010000-0x0009bfff] 
[    0.000000]   node   0: [mem 0x00100000-0xdffc5fff] 
[    0.000000]   node   0: [mem 0x100000000-0x21fffffff] 
[    0.000000]   node   1: [mem 0x220000000-0x41fffffff] 
[    0.000000] On node 0 totalpages: 2096978 
[    0.000000]   DMA zone: 64 pages used for memmap 
[    0.000000]   DMA zone: 6 pages reserved 
[    0.000000]   DMA zone: 3910 pages, LIFO batch:0 
[    0.000000]   DMA32 zone: 14272 pages used for memmap 
[    0.000000]   DMA32 zone: 899078 pages, LIFO batch:31 
[    0.000000]   Normal zone: 18432 pages used for memmap 
[    0.000000]   Normal zone: 1161216 pages, LIFO batch:31 
[    0.000000] On node 1 totalpages: 2097152 
[    0.000000]   Normal zone: 32768 pages used for memmap 
[    0.000000]   Normal zone: 2064384 pages, LIFO batch:31 
[    0.000000] ACPI: PM-Timer IO Port: 0xf808 
[    0.000000] ACPI: Local APIC address 0xfee00000 
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled) 
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x04] enabled) 
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled) 
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x05] enabled) 
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x02] enabled) 
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x06] enabled) 
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x03] enabled) 
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled) 
[    0.000000] ACPI: LAPIC (acpi_id[0x09] lapic_id[0x08] disabled) 
[    0.000000] ACPI: LAPIC (acpi_id[0x0a] lapic_id[0x09] disabled) 
[    0.000000] ACPI: LAPIC (acpi_id[0x0b] lapic_id[0x0a] disabled) 
[    0.000000] ACPI: LAPIC (acpi_id[0x0c] lapic_id[0x0b] disabled) 
[    0.000000] ACPI: LAPIC (acpi_id[0x0d] lapic_id[0x0c] disabled) 
[    0.000000] ACPI: LAPIC (acpi_id[0x0e] lapic_id[0x0d] disabled) 
[    0.000000] ACPI: LAPIC (acpi_id[0x0f] lapic_id[0x0e] disabled) 
[    0.000000] ACPI: LAPIC (acpi_id[0x10] lapic_id[0x0f] disabled) 
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1]) 
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1]) 
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1]) 
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1]) 
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x05] high edge lint[0x1]) 
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x06] high edge lint[0x1]) 
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x07] high edge lint[0x1]) 
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x08] high edge lint[0x1]) 
[    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0]) 
[    0.000000] IOAPIC[0]: apic_id 8, version 17, address 0xfec00000, GSI 0-23 
[    0.000000] ACPI: IOAPIC (id[0x09] address[0xfa400000] gsi_base[24]) 
[    0.000000] IOAPIC[1]: apic_id 9, version 17, address 0xfa400000, GSI 24-47 
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level) 
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge) 
[    0.000000] ACPI: IRQ0 used by override. 
[    0.000000] ACPI: IRQ2 used by override. 
[    0.000000] ACPI: IRQ9 used by override. 
[    0.000000] Using ACPI (MADT) for SMP configuration information 
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000 
[    0.000000] smpboot: Allowing 16 CPUs, 8 hotplug CPUs 
[    0.000000] nr_irqs_gsi: 64 
[    0.000000] PM: Registered nosave memory: 000000000009c000 - 00000000000a0000 
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e9000 
[    0.000000] PM: Registered nosave memory: 00000000000e9000 - 0000000000100000 
[    0.000000] PM: Registered nosave memory: 00000000dffc6000 - 00000000dffc7000 
[    0.000000] PM: Registered nosave memory: 00000000dffc7000 - 00000000e0000000 
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000 
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000f8000000 
[    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fec00000 
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 0000000100000000 
[    0.000000] e820: [mem 0xe0000000-0xefffffff] available for PCI devices 
[    0.000000] Booting paravirtualized kernel on bare hardware 
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:16 nr_node_ids:2 
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff880217c00000 s85056 r8192 d21440 u262144 
[    0.000000] pcpu-alloc: s85056 r8192 d21440 u262144 alloc=1*2097152 
[    0.000000] pcpu-alloc: [0] 00 02 04 06 08 10 12 14 [1] 01 03 05 07 09 11 13 15  
[    0.000000] Built 2 zonelists in Zone order, mobility grouping on.  Total pages: 4128588 
[    0.000000] Policy zone: Normal 
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-27-generic root=UUID=5f55b8f6-1cbf-4a99-8ee0-fd783613d3d0 ro quiet splash vt.handoff=7 
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes) 
[    0.000000] __ex_table already sorted, skipping sort 
[    0.000000] Checking aperture... 
[    0.000000] No AGP bridge found 
[    0.000000] Node 0: aperture @ 0 size 32 MB 
[    0.000000] Your BIOS doesn't leave a aperture memory hole 
[    0.000000] Please enable the IOMMU option in the BIOS setup 
[    0.000000] This costs you 64 MB of RAM 
[    0.000000] Mapping aperture over 65536 KB of RAM @ d4000000 
[    0.000000] PM: Registered nosave memory: 00000000d4000000 - 00000000d8000000 
[    0.000000] Memory: 16352484k/17301504k available (7012k kernel code, 524984k absent, 424036k reserved, 6230k data, 996k init) 
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=16, Nodes=2 
[    0.000000] Hierarchical RCU implementation. 
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled. 
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=16. 
[    0.000000] NR_IRQS:16640 nr_irqs:1216 16 
[    0.000000] Extended CMOS year: 2000 
[    0.000000] spurious 8259A interrupt: IRQ7. 
[    0.000000] Console: colour dummy device 80x25 
[    0.000000] console [tty0] enabled 
[    0.000000] allocated 67108864 bytes of page_cgroup 
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups 
[    0.000000] Enabling automatic NUMA balancing. Configure with numa_balancing= or sysctl 
[    0.000000] hpet clockevent registered 
[    0.000000] tsc: Fast TSC calibration using PIT 
[    0.004000] tsc: Detected 2900.111 MHz processor 
[    0.000007] Calibrating delay loop (skipped), value calculated using timer frequency.. 5800.22 BogoMIPS (lpj=11600444) 
[    0.000010] pid_max: default: 32768 minimum: 301 
[    0.000048] Security Framework initialized 
[    0.000061] AppArmor: AppArmor initialized 
[    0.000062] Yama: becoming mindful. 
[    0.001082] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes) 
[    0.007993] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes) 
[    0.011190] Mount-cache hash table entries: 256 
[    0.011419] Initializing cgroup subsys cpuacct 
[    0.011421] Initializing cgroup subsys memory 
[    0.011446] Initializing cgroup subsys devices 
[    0.011448] Initializing cgroup subsys freezer 
[    0.011449] Initializing cgroup subsys blkio 
[    0.011451] Initializing cgroup subsys perf_event 
[    0.011454] Initializing cgroup subsys hugetlb 
[    0.011481] tseg: 0000000000 
[    0.011497] CPU: Physical Processor ID: 0 
[    0.011498] CPU: Processor Core ID: 0 
[    0.011500] mce: CPU supports 6 MCE banks 
[    0.011506] LVT offset 0 assigned for vector 0xf9 
[    0.011511] process: using AMD E400 aware idle routine 
[    0.011514] Last level iTLB entries: 4KB 512, 2MB 16, 4MB 8 
[    0.011514] Last level dTLB entries: 4KB 512, 2MB 128, 4MB 64 
[    0.011514] tlb_flushall_shift: 4 
[    0.011617] Freeing SMP alternatives: 24k freed 
[    0.013187] ACPI: Core revision 20121018 
[    0.015956] ftrace: allocating 26709 entries in 105 pages 
[    0.027321] Switched APIC routing to physical flat. 
[    0.028117] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1 
[    0.067792] smpboot: CPU0: Quad-Core AMD Opteron(tm) Processor 2389 (fam: 10, model: 04, stepping: 02) 
[    0.173603] Performance Events: AMD PMU driver. 
[    0.173607] ... version:                0 
[    0.173608] ... bit width:              48 
[    0.173609] ... generic registers:      4 
[    0.173610] ... value mask:             0000ffffffffffff 
[    0.173611] ... max period:             00007fffffffffff 
[    0.173612] ... fixed-purpose events:   0 
[    0.173613] ... event mask:             000000000000000f 
[    0.174722] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter. 
[    0.174818] smpboot: Booting Node   1, Processors  #1 OK 
[    0.285773] smpboot: Booting Node   0, Processors  #2 OK 
[    0.298897] smpboot: Booting Node   1, Processors  #3 OK 
[    0.312014] smpboot: Booting Node   0, Processors  #4 OK 
[    0.325135] smpboot: Booting Node   1, Processors  #5 OK 
[    0.338254] smpboot: Booting Node   0, Processors  #6 OK 
[    0.351377] smpboot: Booting Node   1, Processors  #7 
[    0.364413] Brought up 8 CPUs 
[    0.364416] smpboot: Total of 8 processors activated (46401.16 BogoMIPS) 
[    0.375515] devtmpfs: initialized 
[    0.377567] EVM: security.selinux 
[    0.377569] EVM: security.SMACK64 
[    0.377570] EVM: security.capability 
[    0.378667] regulator-dummy: no parameters 
[    0.378728] NET: Registered protocol family 16 
[    0.378834] node 0 link 2: io port [3000, 4fff] 
[    0.378836] node 1 link 0: io port [1000, 2fff] 
[    0.378838] node 1 link 0: io port [e000, efff] 
[    0.378842] TOM: 00000000e0000000 aka 3584M 
[    0.378845] Fam 10h mmconf [mem 0xf0000000-0xf7ffffff] 
[    0.378847] node 0 link 2: mmio [a0000, bffff] 
[    0.378850] node 1 link 0: mmio [f4000000, f7ffffff] ==> none 
[    0.378852] node 0 link 2: mmio [e0000000, efffffff] 
[    0.378854] node 0 link 2: mmio [f8000000, fa2fffff] 
[    0.378856] node 1 link 0: mmio [fa300000, fa4fffff] 
[    0.378858] TOM2: 0000000420000000 aka 16896M 
[    0.378860] bus: [bus 00-3f] on node 0 link 2 
[    0.378861] bus: 00 [io  0x3000-0xdfff] 
[    0.378862] bus: 00 [io  0x0000-0x0fff] 
[    0.378863] bus: 00 [io  0xf000-0xffff] 
[    0.378864] bus: 00 [mem 0x000a0000-0x000bffff] 
[    0.378866] bus: 00 [mem 0xe0000000-0xefffffff] 
[    0.378867] bus: 00 [mem 0xf8000000-0xfa2fffff] 
[    0.378868] bus: 00 [mem 0x420000000-0xfcffffffff] 
[    0.378869] bus: 00 [mem 0xfa500000-0xffffffff] 
[    0.378870] bus: [bus 40-ff] on node 1 link 0 
[    0.378871] bus: 40 [io  0x1000-0x2fff] 
[    0.378872] bus: 40 [io  0xe000-0xefff] 
[    0.378873] bus: 40 [mem 0xfa300000-0xfa4fffff] 
[    0.379000] ACPI: bus type pci registered 
[    0.379067] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf0000000-0xf3ffffff] (base 0xf0000000) 
[    0.379069] PCI: MMCONFIG for domain 0001 [bus 40-7f] at [mem 0xf4000000-0xf7ffffff] (base 0xf0000000) 
[    0.379072] PCI: MMCONFIG at [mem 0xf0000000-0xf3ffffff] reserved in E820 
[    0.379073] PCI: MMCONFIG at [mem 0xf4000000-0xf7ffffff] reserved in E820 
[    0.383850] PCI: Using configuration type 1 for base access 
[    0.384202] mtrr: your CPUs had inconsistent variable MTRR settings 
[    0.384203] mtrr: probably your BIOS does not setup all CPUs. 
[    0.384204] mtrr: corrected configuration. 
[    0.384974] bio: create slab <bio-0> at 0 
[    0.385089] ACPI: Added _OSI(Module Device) 
[    0.385090] ACPI: Added _OSI(Processor Device) 
[    0.385092] ACPI: Added _OSI(3.0 _SCP Extensions) 
[    0.385093] ACPI: Added _OSI(Processor Aggregator Device) 
[    0.385777] ACPI: EC: Look up EC in DSDT 
[    0.388595] ACPI: Interpreter enabled 
[    0.388603] ACPI: (supports S0 S1 S3 S4 S5) 
[    0.388622] ACPI: Using IOAPIC for interrupt routing 
[    0.391586] ACPI: No dock devices found. 
[    0.391591] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug 
[    0.391881] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3f]) 
[    0.391883] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT] 
[    0.392494] PCI host bridge to bus 0000:00 
[    0.392497] pci_bus 0000:00: root bus resource [bus 00-3f] 
[    0.392500] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff] 
[    0.392502] pci_bus 0000:00: root bus resource [io  0x0000-0x03af] 
[    0.392504] pci_bus 0000:00: root bus resource [io  0x03b0-0x03df] 
[    0.392505] pci_bus 0000:00: root bus resource [io  0x03e0-0x0cf7] 
[    0.392507] pci_bus 0000:00: root bus resource [io  0x0d00-0x0fff] 
[    0.392508] pci_bus 0000:00: root bus resource [mem 0xe0000000-0xefffffff] 
[    0.392510] pci_bus 0000:00: root bus resource [mem 0xf8000000-0xfa2fffff] 
[    0.392512] pci_bus 0000:00: root bus resource [io  0x3000-0x4fff] 
[    0.392536] pci 0000:00:00.0: [10de:0369] type 00 class 0x050000 
[    0.392722] pci 0000:00:01.0: [10de:0364] type 00 class 0x060100 
[    0.392763] pci 0000:00:01.1: [10de:0368] type 00 class 0x0c0500 
[    0.392792] pci 0000:00:01.1: reg 20: [io  0x4000-0x403f] 
[    0.392798] pci 0000:00:01.1: reg 24: [io  0x4040-0x407f] 
[    0.392830] pci 0000:00:01.1: PME# supported from D3hot D3cold 
[    0.392851] pci 0000:00:02.0: [10de:036c] type 00 class 0x0c0310 
[    0.392860] pci 0000:00:02.0: reg 10: [mem 0xfa244000-0xfa244fff] 
[    0.392895] pci 0000:00:02.0: supports D1 D2 
[    0.392897] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold 
[    0.392908] pci 0000:00:02.1: [10de:036d] type 00 class 0x0c0320 
[    0.392917] pci 0000:00:02.1: reg 10: [mem 0xfa24a000-0xfa24a0ff] 
[    0.392954] pci 0000:00:02.1: supports D1 D2 
[    0.392956] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold 
[    0.392972] pci 0000:00:04.0: [10de:036e] type 00 class 0x01018a 
[    0.392991] pci 0000:00:04.0: reg 20: [io  0x4080-0x408f] 
[    0.393019] pci 0000:00:05.0: [10de:037f] type 00 class 0x010185 
[    0.393028] pci 0000:00:05.0: reg 10: [io  0x40c0-0x40c7] 
[    0.393033] pci 0000:00:05.0: reg 14: [io  0x4100-0x4103] 
[    0.393038] pci 0000:00:05.0: reg 18: [io  0x40c8-0x40cf] 
[    0.393042] pci 0000:00:05.0: reg 1c: [io  0x4104-0x4107] 
[    0.393047] pci 0000:00:05.0: reg 20: [io  0x4090-0x409f] 
[    0.393051] pci 0000:00:05.0: reg 24: [mem 0xfa245000-0xfa245fff] 
[    0.393084] pci 0000:00:05.1: [10de:037f] type 00 class 0x010185 
[    0.393093] pci 0000:00:05.1: reg 10: [io  0x40d0-0x40d7] 
[    0.393098] pci 0000:00:05.1: reg 14: [io  0x4108-0x410b] 
[    0.393102] pci 0000:00:05.1: reg 18: [io  0x40d8-0x40df] 
[    0.393107] pci 0000:00:05.1: reg 1c: [io  0x410c-0x410f] 
[    0.393111] pci 0000:00:05.1: reg 20: [io  0x40a0-0x40af] 
[    0.393116] pci 0000:00:05.1: reg 24: [mem 0xfa246000-0xfa246fff] 
[    0.393149] pci 0000:00:05.2: [10de:037f] type 00 class 0x010185 
[    0.393158] pci 0000:00:05.2: reg 10: [io  0x40e0-0x40e7] 
[    0.393163] pci 0000:00:05.2: reg 14: [io  0x4110-0x4113] 
[    0.393168] pci 0000:00:05.2: reg 18: [io  0x40e8-0x40ef] 
[    0.393172] pci 0000:00:05.2: reg 1c: [io  0x4114-0x4117] 
[    0.393177] pci 0000:00:05.2: reg 20: [io  0x40b0-0x40bf] 
[    0.393181] pci 0000:00:05.2: reg 24: [mem 0xfa247000-0xfa247fff] 
[    0.393216] pci 0000:00:06.0: [10de:0370] type 01 class 0x060401 
[    0.393253] pci 0000:00:06.1: [10de:0371] type 00 class 0x040300 
[    0.393264] pci 0000:00:06.1: reg 10: [mem 0xfa240000-0xfa243fff] 
[    0.393306] pci 0000:00:06.1: PME# supported from D3hot D3cold 
[    0.393328] pci 0000:00:08.0: [10de:0373] type 00 class 0x068000 
[    0.393340] pci 0000:00:08.0: reg 10: [mem 0xfa248000-0xfa248fff] 
[    0.393345] pci 0000:00:08.0: reg 14: [io  0x40f0-0x40f7] 
[    0.393349] pci 0000:00:08.0: reg 18: [mem 0xfa24a100-0xfa24a1ff] 
[    0.393354] pci 0000:00:08.0: reg 1c: [mem 0xfa24a300-0xfa24a30f] 
[    0.393390] pci 0000:00:08.0: supports D1 D2 
[    0.393392] pci 0000:00:08.0: PME# supported from D0 D1 D2 D3hot D3cold 
[    0.393412] pci 0000:00:09.0: [10de:0373] type 00 class 0x068000 
[    0.393423] pci 0000:00:09.0: reg 10: [mem 0xfa249000-0xfa249fff] 
[    0.393428] pci 0000:00:09.0: reg 14: [io  0x40f8-0x40ff] 
[    0.393432] pci 0000:00:09.0: reg 18: [mem 0xfa24a200-0xfa24a2ff] 
[    0.393437] pci 0000:00:09.0: reg 1c: [mem 0xfa24a310-0xfa24a31f] 
[    0.393473] pci 0000:00:09.0: supports D1 D2 
[    0.393475] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold 
[    0.393495] pci 0000:00:0d.0: [10de:0378] type 01 class 0x060400 
[    0.393528] pci 0000:00:0d.0: PME# supported from D0 D1 D2 D3hot D3cold 
[    0.393550] pci 0000:00:0f.0: [10de:0377] type 01 class 0x060400 
[    0.393582] pci 0000:00:0f.0: PME# supported from D0 D1 D2 D3hot D3cold 
[    0.393601] pci 0000:00:18.0: [1022:1200] type 00 class 0x060000 
[    0.393631] pci 0000:00:18.1: [1022:1201] type 00 class 0x060000 
[    0.393648] pci 0000:00:18.2: [1022:1202] type 00 class 0x060000 
[    0.393666] pci 0000:00:18.3: [1022:1203] type 00 class 0x060000 
[    0.393688] pci 0000:00:18.4: [1022:1204] type 00 class 0x060000 
[    0.393710] pci 0000:00:19.0: [1022:1200] type 00 class 0x060000 
[    0.393743] pci 0000:00:19.1: [1022:1201] type 00 class 0x060000 
[    0.393762] pci 0000:00:19.2: [1022:1202] type 00 class 0x060000 
[    0.393782] pci 0000:00:19.3: [1022:1203] type 00 class 0x060000 
[    0.393807] pci 0000:00:19.4: [1022:1204] type 00 class 0x060000 
[    0.393854] pci 0000:01:05.0: [104c:8023] type 00 class 0x0c0010 
[    0.393866] pci 0000:01:05.0: reg 10: [mem 0xfa104000-0xfa1047ff] 
[    0.393873] pci 0000:01:05.0: reg 14: [mem 0xfa100000-0xfa103fff] 
[    0.393919] pci 0000:01:05.0: supports D1 D2 
[    0.393921] pci 0000:01:05.0: PME# supported from D0 D1 D2 D3hot 
[    0.393948] pci 0000:00:06.0: PCI bridge to [bus 01] (subtractive decode) 
[    0.393951] pci 0000:00:06.0:   bridge window [mem 0xfa100000-0xfa1fffff] 
[    0.393954] pci 0000:00:06.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode) 
[    0.393956] pci 0000:00:06.0:   bridge window [io  0x0000-0x03af] (subtractive decode) 
[    0.393957] pci 0000:00:06.0:   bridge window [io  0x03b0-0x03df] (subtractive decode) 
[    0.393959] pci 0000:00:06.0:   bridge window [io  0x03e0-0x0cf7] (subtractive decode) 
[    0.393960] pci 0000:00:06.0:   bridge window [io  0x0d00-0x0fff] (subtractive decode) 
[    0.393962] pci 0000:00:06.0:   bridge window [mem 0xe0000000-0xefffffff] (subtractive decode) 
[    0.393964] pci 0000:00:06.0:   bridge window [mem 0xf8000000-0xfa2fffff] (subtractive decode) 
[    0.393965] pci 0000:00:06.0:   bridge window [io  0x3000-0x4fff] (subtractive decode) 
[    0.393998] pci 0000:2b:00.0: [1033:0125] type 01 class 0x060400 
[    0.394056] pci 0000:2b:00.0: supports D1 
[    0.394058] pci 0000:2b:00.0: PME# supported from D0 D1 D3hot D3cold 
[    0.394081] pci 0000:2b:00.1: [1033:0125] type 01 class 0x060400 
[    0.394099] pci 0000:2b:00.1: reg 10: [mem 0xfa000000-0xfa00007f 64bit] 
[    0.394167] pci 0000:2b:00.1: supports D1 
[    0.394169] pci 0000:2b:00.1: PME# supported from D0 D1 D3hot D3cold 
[    0.394194] pci 0000:2b:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force' 
[    0.394198] pci 0000:00:0d.0: PCI bridge to [bus 2b-2d] 
[    0.394202] pci 0000:00:0d.0:   bridge window [mem 0xfa000000-0xfa0fffff] 
[    0.394259] pci 0000:2b:00.0: PCI bridge to [bus 2c] 
[    0.394347] pci 0000:2b:00.1: PCI bridge to [bus 2d] 
[    0.394402] pci 0000:18:00.0: [10de:029d] type 00 class 0x030000 
[    0.394410] pci 0000:18:00.0: reg 10: [mem 0xf8000000-0xf8ffffff] 
[    0.394419] pci 0000:18:00.0: reg 14: [mem 0xe0000000-0xefffffff 64bit pref] 
[    0.394427] pci 0000:18:00.0: reg 1c: [mem 0xf9000000-0xf9ffffff 64bit] 
[    0.394433] pci 0000:18:00.0: reg 24: [io  0x3000-0x307f] 
[    0.394440] pci 0000:18:00.0: reg 30: [mem 0x00000000-0x0001ffff pref] 
[    0.394473] pci 0000:18:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force' 
[    0.394478] pci 0000:00:0f.0: PCI bridge to [bus 18] 
[    0.394481] pci 0000:00:0f.0:   bridge window [io  0x3000-0x3fff] 
[    0.394483] pci 0000:00:0f.0:   bridge window [mem 0xf8000000-0xf9ffffff] 
[    0.394487] pci 0000:00:0f.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref] 
[    0.394494] pci_bus 0000:00: on NUMA node 0 (pxm 0) 
[    0.394506] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXPA._PRT] 
[    0.394525] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB_._PRT] 
[    0.394543] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXPC._PRT] 
[    0.394560] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXPC.PCXB._PRT] 
[    0.394614]  pci0000:00: ACPI _OSC support notification failed, disabling PCIe ASPM 
[    0.394616]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x08) 
[    0.395692] ACPI: PCI Root Bridge [PCI1] (domain 0001 [bus 40-ff]) 
[    0.396214] pci_root PNP0A03:00: [Firmware Info]: MMCONFIG for domain 0001 [bus 40-7f] only partially covers this bridge 
[    0.396231] PCI host bridge to bus 0001:40 
[    0.396233] pci_bus 0001:40: root bus resource [bus 40-ff] 
[    0.396235] pci_bus 0001:40: root bus resource [io  0x1000-0x2fff] 
[    0.396236] pci_bus 0001:40: root bus resource [mem 0xfa300000-0xfa4fffff] 
[    0.396256] pci 0001:40:00.0: [10de:0369] type 00 class 0x050000 
[    0.396426] pci 0001:40:01.0: [10de:0361] type 00 class 0x050000 
[    0.396433] pci 0001:40:01.0: reg 14: [mem 0xfa400000-0xfa400fff] 
[    0.396459] pci 0001:40:01.1: [10de:0368] type 00 class 0x0c0500 
[    0.396483] pci 0001:40:01.1: reg 20: [io  0x2000-0x203f] 
[    0.396488] pci 0001:40:01.1: reg 24: [io  0x2040-0x207f] 
[    0.396517] pci 0001:40:01.1: PME# supported from D3hot D3cold 
[    0.396547] pci 0001:40:0d.0: [10de:0378] type 01 class 0x060400 
[    0.396570] pci 0001:40:0d.0: PME# supported from D0 D1 D2 D3hot D3cold 
[    0.396615] pci 0001:6b:00.0: [1000:0058] type 00 class 0x010000 
[    0.396624] pci 0001:6b:00.0: reg 10: [io  0x1000-0x10ff] 
[    0.396633] pci 0001:6b:00.0: reg 14: [mem 0xfa310000-0xfa313fff 64bit] 
[    0.396642] pci 0001:6b:00.0: reg 1c: [mem 0xfa300000-0xfa30ffff 64bit] 
[    0.396652] pci 0001:6b:00.0: reg 30: [mem 0x00000000-0x000fffff pref] 
[    0.396682] pci 0001:6b:00.0: supports D1 D2 
[    0.402800] pci 0001:40:0d.0: PCI bridge to [bus 6b] 
[    0.402805] pci 0001:40:0d.0:   bridge window [io  0x1000-0x1fff] 
[    0.402807] pci 0001:40:0d.0:   bridge window [mem 0xfa300000-0xfa3fffff] 
[    0.402812] pci_bus 0001:40: on NUMA node 1 (pxm 1) 
[    0.402833] ACPI: PCI Interrupt Routing Table [\_SB_.PCI1.EXPC._PRT] 
[    0.402877]  pci0001:40: ACPI _OSC support notification failed, disabling PCIe ASPM 
[    0.402878]  pci0001:40: Unable to request _OSC control (_OSC support mask: 0x08) 
[    0.403067] ACPI: PCI Interrupt Link [LNKA] (IRQs 5 7 *10 16 17 18 19 20 21 22 23) 
[    0.403128] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7 10 16 17 18 19 20 21 22 23) *0, disabled. 
[    0.403184] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 7 10 16 17 18 19 20 21 22 23) *0, disabled. 
[    0.403239] ACPI: PCI Interrupt Link [LNKD] (IRQs *5 7 10 16 17 18 19 20 21 22 23) 
[    0.403292] ACPI: PCI Interrupt Link [LXPA] (IRQs 5 7 10 16 17 18 19 20 21 22 23) *0, disabled. 
[    0.403347] ACPI: PCI Interrupt Link [LXPB] (IRQs *5 7 10 16 17 18 19 20 21 22 23) 
[    0.403402] ACPI: PCI Interrupt Link [LXPC] (IRQs 5 7 10 16 17 18 19 20 21 22 23) *0, disabled. 
[    0.403457] ACPI: PCI Interrupt Link [LXPD] (IRQs 5 7 10 16 17 18 19 20 21 22 23) *0, disabled. 
[    0.403476] ACPI: PCI Interrupt Link [LXA2] (IRQs *40), disabled. 
[    0.403492] ACPI: PCI Interrupt Link [LXB2] (IRQs *41), disabled. 
[    0.403507] ACPI: PCI Interrupt Link [LXC2] (IRQs *42), disabled. 
[    0.403523] ACPI: PCI Interrupt Link [LXD2] (IRQs *43), disabled. 
[    0.403574] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 10 16 17 18 19 20 21 22 23) *11 
[    0.403629] ACPI: PCI Interrupt Link [LSB0] (IRQs *5 7 10 16 17 18 19 20 21 22 23) 
[    0.403683] ACPI: PCI Interrupt Link [LSB2] (IRQs 5 7 *10 16 17 18 19 20 21 22 23) 
[    0.403736] ACPI: PCI Interrupt Link [LMC0] (IRQs *5 7 10 16 17 18 19 20 21 22 23) 
[    0.403790] ACPI: PCI Interrupt Link [LMC1] (IRQs 5 7 *10 16 17 18 19 20 21 22 23) 
[    0.403844] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 10 16 17 18 19 20 21 22 23) *11 
[    0.403899] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 10 16 17 18 19 20 21 22 23) *0, disabled. 
[    0.403959] ACPI: PCI Interrupt Link [LSA0] (IRQs 5 7 10 16 17 18 19 20 21 22 23) *11 
[    0.404017] ACPI: PCI Interrupt Link [LSA1] (IRQs *5 7 10 16 17 18 19 20 21 22 23) 
[    0.404071] ACPI: PCI Interrupt Link [LSA2] (IRQs 5 7 *10 16 17 18 19 20 21 22 23) 
[    0.404188] vgaarb: device added: PCI:0000:18:00.0,decodes=io+mem,owns=io+mem,locks=none 
[    0.404190] vgaarb: loaded 
[    0.404191] vgaarb: bridge control possible 0000:18:00.0 
[    0.404356] SCSI subsystem initialized 
[    0.404358] ACPI: bus type scsi registered 
[    0.404448] libata version 3.00 loaded. 
[    0.404463] ACPI: bus type usb registered 
[    0.404477] usbcore: registered new interface driver usbfs 
[    0.404486] usbcore: registered new interface driver hub 
[    0.404514] usbcore: registered new device driver usb 
[    0.404613] PCI: Using ACPI for IRQ routing 
[    0.405958] PCI: pci_cache_line_size set to 64 bytes 
[    0.406024] e820: reserve RAM buffer [mem 0x0009c000-0x0009ffff] 
[    0.406026] e820: reserve RAM buffer [mem 0xdffc6100-0xdfffffff] 
[    0.406109] NetLabel: Initializing 
[    0.406111] NetLabel:  domain hash size = 128 
[    0.406112] NetLabel:  protocols = UNLABELED CIPSOv4 
[    0.406121] NetLabel:  unlabeled traffic allowed by default 
[    0.406210] HPET: 3 timers in total, 0 timers will be used for per-cpu timer 
[    0.406216] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31 
[    0.406219] hpet0: 3 comparators, 32-bit 25.000000 MHz counter 
[    0.408876] Switching to clocksource hpet 
[    0.414486] AppArmor: AppArmor Filesystem Enabled 
[    0.414533] pnp: PnP ACPI init 
[    0.414553] ACPI: bus type pnp registered 
[    0.414689] pnp 00:00: Plug and Play ACPI device, IDs PNP0c04 (active) 
[    0.414759] pnp 00:01: Plug and Play ACPI device, IDs PNP0103 (active) 
[    0.414768] pnp 00:02: [dma 4] 
[    0.414781] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active) 
[    0.414804] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active) 
[    0.414823] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active) 
[    0.414847] pnp 00:05: Plug and Play ACPI device, IDs PNP0f13 PNP0f0e (active) 
[    0.414872] pnp 00:06: Plug and Play ACPI device, IDs PNP0303 (active) 
[    0.415042] pnp 00:07: Plug and Play ACPI device, IDs PNP0501 PNP0500 (active) 
[    0.415090] pnp 00:08: Plug and Play ACPI device, IDs PNP0700 (disabled) 
[    0.415134] pnp 00:09: Plug and Play ACPI device, IDs PNP0003 (active) 
[    0.415155] pnp 00:0a: Plug and Play ACPI device, IDs IFX0102 PNP0c31 (active) 
[    0.415257] system 00:0b: [io  0x04d0-0x04d1] has been reserved 
[    0.415260] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active) 
[    0.415317] system 00:0c: [io  0x0400-0x047f] has been reserved 
[    0.415319] system 00:0c: [io  0x0480-0x048f] has been reserved 
[    0.415321] system 00:0c: [io  0xe000-0xe07f] has been reserved 
[    0.415323] system 00:0c: [io  0xe080-0xe0ff] has been reserved 
[    0.415325] system 00:0c: [io  0xf200-0xf27f] has been reserved 
[    0.415327] system 00:0c: [io  0xf280-0xf2ff] has been reserved 
[    0.415328] system 00:0c: [io  0xf800-0xf87f] has been reserved 
[    0.415330] system 00:0c: [io  0xf880-0xf8ff] has been reserved 
[    0.415332] system 00:0c: [io  0xf900-0xf97f] has been reserved 
[    0.415333] system 00:0c: [io  0xf980-0xf9ff] has been reserved 
[    0.415335] system 00:0c: [io  0xfa00-0xfa7f] has been reserved 
[    0.415337] system 00:0c: [io  0xfa80-0xfaff] has been reserved 
[    0.415338] system 00:0c: [io  0xfc00-0xfc7f] has been reserved 
[    0.415340] system 00:0c: [io  0xfc80-0xfcff] has been reserved 
[    0.415342] system 00:0c: [io  0xfe00-0xfe7f] has been reserved 
[    0.415343] system 00:0c: [io  0xfe80-0xfeff] has been reserved 
[    0.415346] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active) 
[    0.416076] pnp 00:0d: disabling [mem 0x00000000-0x0009ffff] because it overlaps 0001:6b:00.0 BAR 6 [mem 0x00000000-0x000fffff pref] 
[    0.416083] pnp 00:0d: disabling [mem 0x000e8000-0x000fffff] because it overlaps 0001:6b:00.0 BAR 6 [mem 0x00000000-0x000fffff pref] 
[    0.416086] pnp 00:0d: disabling [mem 0x000d8800-0x000e7fff] because it overlaps 0001:6b:00.0 BAR 6 [mem 0x00000000-0x000fffff pref] 
[    0.416156] system 00:0d: [mem 0x00100000-0xdfffffff] could not be reserved 
[    0.416159] system 00:0d: [mem 0xfec01000-0xffffffff] has been reserved 
[    0.416162] system 00:0d: Plug and Play ACPI device, IDs PNP0c01 (active) 
[    0.416200] system 00:0e: [mem 0xf0000000-0xf7ffffff window] has been reserved 
[    0.416203] system 00:0e: Plug and Play ACPI device, IDs PNP0c02 (active) 
[    0.416213] pnp: PnP ACPI: found 15 devices 
[    0.416214] ACPI: ACPI bus type pnp unregistered 
[    0.422714] pci 0000:00:06.0: PCI bridge to [bus 01] 
[    0.422719] pci 0000:00:06.0:   bridge window [mem 0xfa100000-0xfa1fffff] 
[    0.422725] pci 0000:2b:00.0: PCI bridge to [bus 2c] 
[    0.422735] pci 0000:2b:00.1: PCI bridge to [bus 2d] 
[    0.422749] pci 0000:00:0d.0: PCI bridge to [bus 2b-2d] 
[    0.422752] pci 0000:00:0d.0:   bridge window [mem 0xfa000000-0xfa0fffff] 
[    0.422759] pci 0000:18:00.0: BAR 6: can't assign mem pref (size 0x20000) 
[    0.422762] pci 0000:00:0f.0: PCI bridge to [bus 18] 
[    0.422764] pci 0000:00:0f.0:   bridge window [io  0x3000-0x3fff] 
[    0.422767] pci 0000:00:0f.0:   bridge window [mem 0xf8000000-0xf9ffffff] 
[    0.422770] pci 0000:00:0f.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref] 
[    0.422776] pci 0001:40:0d.0: BAR 15: can't assign mem pref (size 0x100000) 
[    0.422778] pci 0001:6b:00.0: BAR 6: can't assign mem pref (size 0x100000) 
[    0.422780] pci 0001:40:0d.0: PCI bridge to [bus 6b] 
[    0.422782] pci 0001:40:0d.0:   bridge window [io  0x1000-0x1fff] 
[    0.422784] pci 0001:40:0d.0:   bridge window [mem 0xfa300000-0xfa3fffff] 
[    0.422794] pci 0000:00:06.0: setting latency timer to 64 
[    0.422926] ACPI: PCI Interrupt Link [LXPD] enabled at IRQ 23 
[    0.422958] pci_bus 0000:00: resource 4 [mem 0x000a0000-0x000bffff] 
[    0.422960] pci_bus 0000:00: resource 5 [io  0x0000-0x03af] 
[    0.422962] pci_bus 0000:00: resource 6 [io  0x03b0-0x03df] 
[    0.422963] pci_bus 0000:00: resource 7 [io  0x03e0-0x0cf7] 
[    0.422965] pci_bus 0000:00: resource 8 [io  0x0d00-0x0fff] 
[    0.422967] pci_bus 0000:00: resource 9 [mem 0xe0000000-0xefffffff] 
[    0.422968] pci_bus 0000:00: resource 10 [mem 0xf8000000-0xfa2fffff] 
[    0.422970] pci_bus 0000:00: resource 11 [io  0x3000-0x4fff] 
[    0.422972] pci_bus 0000:01: resource 1 [mem 0xfa100000-0xfa1fffff] 
[    0.422974] pci_bus 0000:01: resource 4 [mem 0x000a0000-0x000bffff] 
[    0.422975] pci_bus 0000:01: resource 5 [io  0x0000-0x03af] 
[    0.422977] pci_bus 0000:01: resource 6 [io  0x03b0-0x03df] 
[    0.422979] pci_bus 0000:01: resource 7 [io  0x03e0-0x0cf7] 
[    0.422980] pci_bus 0000:01: resource 8 [io  0x0d00-0x0fff] 
[    0.422982] pci_bus 0000:01: resource 9 [mem 0xe0000000-0xefffffff] 
[    0.422983] pci_bus 0000:01: resource 10 [mem 0xf8000000-0xfa2fffff] 
[    0.422985] pci_bus 0000:01: resource 11 [io  0x3000-0x4fff] 
[    0.422987] pci_bus 0000:2b: resource 1 [mem 0xfa000000-0xfa0fffff] 
[    0.422989] pci_bus 0000:18: resource 0 [io  0x3000-0x3fff] 
[    0.422991] pci_bus 0000:18: resource 1 [mem 0xf8000000-0xf9ffffff] 
[    0.422992] pci_bus 0000:18: resource 2 [mem 0xe0000000-0xefffffff 64bit pref] 
[    0.422995] pci_bus 0001:40: resource 4 [io  0x1000-0x2fff] 
[    0.422996] pci_bus 0001:40: resource 5 [mem 0xfa300000-0xfa4fffff] 
[    0.422998] pci_bus 0001:6b: resource 0 [io  0x1000-0x1fff] 
[    0.423000] pci_bus 0001:6b: resource 1 [mem 0xfa300000-0xfa3fffff] 
[    0.423054] NET: Registered protocol family 2 
[    0.423345] TCP established hash table entries: 131072 (order: 9, 2097152 bytes) 
[    0.424218] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes) 
[    0.424630] TCP: Hash tables configured (established 131072 bind 65536) 
[    0.424680] TCP: reno registered 
[    0.424700] UDP hash table entries: 8192 (order: 6, 262144 bytes) 
[    0.424833] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes) 
[    0.425059] NET: Registered protocol family 1 
[    0.425227] ACPI: PCI Interrupt Link [LSB0] enabled at IRQ 22 
[    0.481138] ACPI: PCI Interrupt Link [LSB2] enabled at IRQ 21 
[    0.481365] pci 0000:00:00.0: Found enabled HT MSI Mapping 
[    0.481416] pci 0000:00:00.0: Found enabled HT MSI Mapping 
[    0.481467] pci 0000:00:00.0: Found enabled HT MSI Mapping 
[    0.481520] pci 0000:00:00.0: Found enabled HT MSI Mapping 
[    0.481574] pci 0000:00:00.0: Found enabled HT MSI Mapping 
[    0.481640] pci 0000:00:00.0: Found enabled HT MSI Mapping 
[    0.481711] pci 0000:00:00.0: Found enabled HT MSI Mapping 
[    0.481787] pci 0000:00:00.0: Found enabled HT MSI Mapping 
[    0.481868] pci 0000:00:00.0: Found enabled HT MSI Mapping 
[    0.481902] pci 0000:18:00.0: Boot video device 
[    0.481974] pci 0001:40:00.0: Found enabled HT MSI Mapping 
[    0.481978] PCI: CLS 64 bytes, default 64 
[    0.482046] Trying to unpack rootfs image as initramfs... 
[    0.689388] Freeing initrd memory: 12564k freed 
[    0.695619] PCI-DMA: Disabling AGP. 
[    0.695744] PCI-DMA: aperture base @ d4000000 size 65536 KB 
[    0.695745] PCI-DMA: using GART IOMMU. 
[    0.695751] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture 
[    0.701250] LVT offset 1 assigned for vector 0x400 
[    0.701265] IBS: LVT offset 1 assigned 
[    0.701310] perf: AMD IBS detected (0x0000001f) 
[    0.701511] Initialise module verification 
[    0.701557] audit: initializing netlink socket (disabled) 
[    0.701571] type=2000 audit(1376469718.572:1): initialized 
[    0.724774] HugeTLB registered 2 MB page size, pre-allocated 0 pages 
[    0.727215] VFS: Disk quotas dquot_6.5.2 
[    0.727263] Dquot-cache hash table entries: 512 (order 0, 4096 bytes) 
[    0.727842] fuse init (API version 7.20) 
[    0.727917] msgmni has been set to 32091 
[    0.728533] Key type asymmetric registered 
[    0.728535] Asymmetric key parser 'x509' registered 
[    0.728563] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252) 
[    0.728602] io scheduler noop registered 
[    0.728604] io scheduler deadline registered (default) 
[    0.728608] io scheduler cfq registered 
[    0.728764] pcieport 0000:00:0d.0: irq 64 for MSI/MSI-X 
[    0.728911] pcieport 0000:00:0f.0: irq 65 for MSI/MSI-X 
[    0.729065] pcieport 0001:40:0d.0: irq 66 for MSI/MSI-X 
[    0.729159] pci_hotplug: PCI Hot Plug PCI Core version: 0.5 
[    0.729171] pciehp: PCI Express Hot Plug Controller Driver version: 0.4 
[    0.729297] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0 
[    0.729303] ACPI: Power Button [PBTN] 
[    0.729336] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1 
[    0.729338] ACPI: Power Button [PWRF] 
[    0.731465] GHES: HEST is not enabled! 
[    0.731572] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled 
[    0.751966] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
[    0.753361] Linux agpgart interface v0.103 
[    0.754604] brd: module loaded 
[    0.755256] loop: module loaded 
[    0.755646] libphy: Fixed MDIO Bus: probed 
[    0.755697] tun: Universal TUN/TAP device driver, 1.6 
[    0.755699] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com> 
[    0.755761] PPP generic driver version 2.4.2 
[    0.755809] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver 
[    0.755811] ehci-pci: EHCI PCI platform driver 
[    0.755878] ehci-pci 0000:00:02.1: setting latency timer to 64 
[    0.755882] ehci-pci 0000:00:02.1: EHCI Host Controller 
[    0.755891] ehci-pci 0000:00:02.1: new USB bus registered, assigned bus number 1 
[    0.755901] ehci-pci 0000:00:02.1: debug port 1 
[    0.755925] ehci-pci 0000:00:02.1: cache line size of 64 is not supported 
[    0.755951] ehci-pci 0000:00:02.1: irq 21, io mem 0xfa24a000 
[    0.764840] ehci-pci 0000:00:02.1: USB 2.0 started, EHCI 1.00 
[    0.764888] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002 
[    0.764890] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1 
[    0.764892] usb usb1: Product: EHCI Host Controller 
[    0.764893] usb usb1: Manufacturer: Linux 3.8.0-27-generic ehci_hcd 
[    0.764895] usb usb1: SerialNumber: 0000:00:02.1 
[    0.765014] hub 1-0:1.0: USB hub found 
[    0.765018] hub 1-0:1.0: 10 ports detected 
[    0.765165] ehci-platform: EHCI generic platform driver 
[    0.765175] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver 
[    0.765212] ohci_hcd 0000:00:02.0: setting latency timer to 64 
[    0.765215] ohci_hcd 0000:00:02.0: OHCI Host Controller 
[    0.765220] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2 
[    0.765248] ohci_hcd 0000:00:02.0: irq 22, io mem 0xfa244000 
[    0.822831] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001 
[    0.822834] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1 
[    0.822836] usb usb2: Product: OHCI Host Controller 
[    0.822837] usb usb2: Manufacturer: Linux 3.8.0-27-generic ohci_hcd 
[    0.822838] usb usb2: SerialNumber: 0000:00:02.0 
[    0.822947] hub 2-0:1.0: USB hub found 
[    0.822952] hub 2-0:1.0: 10 ports detected 
[    0.823094] uhci_hcd: USB Universal Host Controller Interface driver 
[    0.823159] i8042: PNP: PS/2 Controller [PNP0303:KBD,PNP0f0e:PS2M] at 0x60,0x64 irq 1,12 
[    0.825956] serio: i8042 KBD port at 0x60,0x64 irq 1 
[    0.825963] serio: i8042 AUX port at 0x60,0x64 irq 12 
[    0.826111] mousedev: PS/2 mouse device common for all mice 
[    0.826265] rtc_cmos 00:03: RTC can wake from S4 
[    0.826407] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0 
[    0.826443] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs 
[    0.826534] device-mapper: uevent: version 1.0.3 
[    0.826598] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: dm-devel@redhat.com 
[    0.826605] cpuidle: using governor ladder 
[    0.826606] cpuidle: using governor menu 
[    0.826614] ledtrig-cpu: registered to indicate activity on CPUs 
[    0.826616] EFI Variables Facility v0.08 2004-May-17 
[    0.826848] ashmem: initialized 
[    0.826968] TCP: cubic registered 
[    0.827056] NET: Registered protocol family 10 
[    0.827220] NET: Registered protocol family 17 
[    0.827228] Key type dns_resolver registered 
[    0.827595] Loading module verification certificates 
[    0.828547] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: b19078b01b96b975438ce0719f8a7eb15318eb67' 
[    0.828556] registered taskstats version 1 
[    0.831996] Key type trusted registered 
[    0.833803] Key type encrypted registered 
[    0.836098] rtc_cmos 00:03: setting system clock to 2013-08-14 08:41:59 UTC (1376469719) 
[    0.836153] powernow-k8: this CPU is not supported anymore, using acpi-cpufreq instead. 
[    0.837099] acpi-cpufreq: overriding BIOS provided _PSD data 
[    0.837364] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found 
[    0.837365] EDD information not available. 
[    0.838616] Freeing unused kernel memory: 996k freed 
[    0.839058] Write protecting the kernel read-only data: 12288k 
[    0.842049] Freeing unused kernel memory: 1168k freed 
[    0.845239] Freeing unused kernel memory: 1080k freed 
[    0.859659] udevd[132]: starting version 175 
[    0.862906] Disabling lock debugging due to kernel taint 
[    0.863257] microcode: CPU0: patch_level=0x01000086 
[    0.863308] microcode: CPU0: new patch_level=0x010000db 
[    0.863358] microcode: CPU1: patch_level=0x01000086 
[    0.863366] microcode: CPU1: new patch_level=0x010000db 
[    0.863378] microcode: CPU2: patch_level=0x01000086 
[    0.863387] microcode: CPU2: new patch_level=0x010000db 
[    0.863399] microcode: CPU3: patch_level=0x01000086 
[    0.863408] microcode: CPU3: new patch_level=0x010000db 
[    0.863418] microcode: CPU4: patch_level=0x01000086 
[    0.863427] microcode: CPU4: new patch_level=0x010000db 
[    0.863438] microcode: CPU5: patch_level=0x01000086 
[    0.863447] microcode: CPU5: new patch_level=0x010000db 
[    0.863463] microcode: CPU6: patch_level=0x01000086 
[    0.863473] microcode: CPU6: new patch_level=0x010000db 
[    0.863485] microcode: CPU7: patch_level=0x01000086 
[    0.863490] microcode: CPU7: new patch_level=0x010000db 
[    0.863542] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba 
[    0.878615] pata_amd 0000:00:04.0: version 0.4.1 
[    0.878658] pata_amd 0000:00:04.0: setting latency timer to 64 
[    0.879636] scsi0 : pata_amd 
[    0.879757] scsi1 : pata_amd 
[    0.879785] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x4080 irq 14 
[    0.879787] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x4088 irq 15 
[    0.879825] sata_nv 0000:00:05.0: version 3.5 
[    0.879853] ata1: port disabled--ignoring 
[    0.879896] ata2: port disabled--ignoring 
[    0.880044] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 20 
[    0.880063] sata_nv 0000:00:05.0: Using SWNCQ mode 
[    0.880632] sata_nv 0000:00:05.0: Using MSI 
[    0.880654] sata_nv 0000:00:05.0: irq 67 for MSI/MSI-X 
[    0.880667] sata_nv 0000:00:05.0: setting latency timer to 64 
[    0.881906] scsi2 : sata_nv 
[    0.881994] scsi3 : sata_nv 
[    0.882021] ata3: SATA max UDMA/133 cmd 0x40c0 ctl 0x4100 bmdma 0x4090 irq 67 
[    0.882023] ata4: SATA max UDMA/133 cmd 0x40c8 ctl 0x4104 bmdma 0x4098 irq 67 
[    0.882249] ACPI: PCI Interrupt Link [LSA1] enabled at IRQ 19 
[    0.882264] sata_nv 0000:00:05.1: Using SWNCQ mode 
[    0.882300] sata_nv 0000:00:05.1: Using MSI 
[    0.882318] sata_nv 0000:00:05.1: irq 68 for MSI/MSI-X 
[    0.882329] sata_nv 0000:00:05.1: setting latency timer to 64 
[    0.882956] scsi4 : sata_nv 
[    0.883042] scsi5 : sata_nv 
[    0.883070] ata5: SATA max UDMA/133 cmd 0x40d0 ctl 0x4108 bmdma 0x40a0 irq 68 
[    0.883072] ata6: SATA max UDMA/133 cmd 0x40d8 ctl 0x410c bmdma 0x40a8 irq 68 
[    0.883287] ACPI: PCI Interrupt Link [LSA2] enabled at IRQ 18 
[    0.883305] sata_nv 0000:00:05.2: Using SWNCQ mode 
[    0.883338] sata_nv 0000:00:05.2: Using MSI 
[    0.883357] sata_nv 0000:00:05.2: irq 69 for MSI/MSI-X 
[    0.883367] sata_nv 0000:00:05.2: setting latency timer to 64 
[    0.883622] scsi6 : sata_nv 
[    0.883991] scsi7 : sata_nv 
[    0.884033] ata7: SATA max UDMA/133 cmd 0x40e0 ctl 0x4110 bmdma 0x40b0 irq 69 
[    0.884035] ata8: SATA max UDMA/133 cmd 0x40e8 ctl 0x4114 bmdma 0x40b8 irq 69 
[    0.884129] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64. 
[    0.884266] ACPI: PCI Interrupt Link [LMC0] enabled at IRQ 17 
[    0.884281] forcedeth 0000:00:08.0: setting latency timer to 64 
[    0.894021] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 16 
[    0.894870] Fusion MPT base driver 3.04.20 
[    0.894872] Copyright (c) 1999-2008 LSI Corporation 
[    0.895594] Fusion MPT SAS Host driver 3.04.20 
[    0.895742] ACPI: PCI Interrupt Link [LXD2] enabled at IRQ 43 
[    0.896291] mptbase: ioc0: Initiating bringup 
[    0.948833] firewire_ohci 0000:01:05.0: added OHCI v1.10 device as card 0, 4 IR + 8 IT contexts, quirks 0x2 
[    1.076760] usb 1-5: new high-speed USB device number 2 using ehci-pci 
[    1.192734] ata7: SATA link down (SStatus 0 SControl 300) 
[    1.192738] ata5: SATA link down (SStatus 0 SControl 300) 
[    1.209091] usb 1-5: New USB device found, idVendor=0424, idProduct=2512 
[    1.209095] usb 1-5: New USB device strings: Mfr=0, Product=0, SerialNumber=0 
[    1.209360] hub 1-5:1.0: USB hub found 
[    1.209460] hub 1-5:1.0: 2 ports detected 
[    1.348688] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300) 
[    1.356983] ata3.00: ATA-8: WDC WD3200AAKS-75L9A0, 02.03E02, max UDMA/133 
[    1.356987] ata3.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32) 
[    1.373038] ata3.00: configured for UDMA/133 
[    1.373220] scsi 2:0:0:0: Direct-Access     ATA      WDC WD3200AAKS-7 02.0 PQ: 0 ANSI: 5 
[    1.373419] sd 2:0:0:0: Attached scsi generic sg0 type 0 
[    1.373481] sd 2:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB) 
[    1.373669] sd 2:0:0:0: [sda] Write Protect is off 
[    1.373674] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00 
[    1.373719] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[    1.409125] forcedeth 0000:00:08.0: ifname eth0, PHY OUI 0x5043 @ 0, addr 00:1c:c4:17:7e:72 
[    1.409129] forcedeth 0000:00:08.0: highdma csum vlan pwrctl mgmt gbit lnktim msi desc-v3 
[    1.409330] ACPI: PCI Interrupt Link [LMC1] enabled at IRQ 23 
[    1.409336] forcedeth 0000:00:09.0: setting latency timer to 64 
[    1.410452]  sda: sda1 sda2 < sda5 > 
[    1.410976] sd 2:0:0:0: [sda] Attached SCSI disk 
[    1.448730] firewire_core 0000:01:05.0: created device fw0: GUID 0060b000002296d5, S400 
[    1.596593] ioc0: LSISAS1068E B1: Capabilities={Initiator} 
[    1.596643] mptsas 0001:6b:00.0: irq 70 for MSI/MSI-X 
[    1.596655] mptbase: ioc0: PCI-MSI enabled 
[    1.668708] usb 1-5.1: new high-speed USB device number 4 using ehci-pci 
[    1.700568] tsc: Refined TSC clocksource calibration: 2900.000 MHz 
[    1.700574] Switching to clocksource tsc 
[    1.777044] usb 1-5.1: New USB device found, idVendor=0424, idProduct=2602 
[    1.777047] usb 1-5.1: New USB device strings: Mfr=0, Product=0, SerialNumber=0 
[    1.777193] hub 1-5.1:1.0: USB hub found 
[    1.777291] hub 1-5.1:1.0: 4 ports detected 
[    1.840524] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300) 
[    1.848647] ata4.00: ATAPI: TSSTcorpCD/DVDW TS-H653L, HA03, max UDMA/100 
[    1.864643] ata4.00: configured for UDMA/100 
[    1.864645] usb 1-5.2: new low-speed USB device number 5 using ehci-pci 
[    1.865976] scsi 3:0:0:0: CD-ROM            TSSTcorp CD/DVDW TS-H653L HA03 PQ: 0 ANSI: 5 
[    1.871445] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray 
[    1.871448] cdrom: Uniform CD-ROM driver Revision: 3.20 
[    1.871582] sr 3:0:0:0: Attached scsi CD-ROM sr0 
[    1.871669] sr 3:0:0:0: Attached scsi generic sg1 type 5 
[    1.928344] forcedeth 0000:00:09.0: ifname eth1, PHY OUI 0x5043 @ 1, addr 00:1c:c4:17:7e:73 
[    1.928348] forcedeth 0000:00:09.0: highdma csum vlan pwrctl mgmt gbit lnktim msi desc-v3 
[    1.977250] usb 1-5.2: New USB device found, idVendor=045e, idProduct=0040 
[    1.977253] usb 1-5.2: New USB device strings: Mfr=1, Product=3, SerialNumber=0 
[    1.977255] usb 1-5.2: Product: Microsoft 3-Button Mouse with IntelliEye(TM) 
[    1.977257] usb 1-5.2: Manufacturer: Microsoft 
[    1.986183] usbcore: registered new interface driver usbhid 
[    1.986185] usbhid: USB HID core driver 
[    1.988754] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:02.1/usb1/1-5/1-5.2/1-5.2:1.0/input/input2 
[    1.988895] hid-generic 0003:045E:0040.0001: input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:02.1-5.2/input0 
[    2.144896] EXT4-fs (sda1): INFO: recovery required on readonly filesystem 
[    2.144901] EXT4-fs (sda1): write access will be enabled during recovery 
[    2.152427] usb 2-6: new full-speed USB device number 2 using ohci_hcd 
[    2.180423] ata6: SATA link down (SStatus 0 SControl 300) 
[    2.364398] usb 2-6: New USB device found, idVendor=413c, idProduct=1003 
[    2.364402] usb 2-6: New USB device strings: Mfr=1, Product=2, SerialNumber=0 
[    2.364404] usb 2-6: Product: Dell USB Keyboard Hub 
[    2.364406] usb 2-6: Manufacturer: Dell 
[    2.373415] hub 2-6:1.0: USB hub found 
[    2.376394] hub 2-6:1.0: 3 ports detected 
[    2.476464] usb 1-5.1.1: new high-speed USB device number 6 using ehci-pci 
[    2.492325] ata8: SATA link down (SStatus 0 SControl 300) 
[    2.646304] usb 1-5.1.1: New USB device found, idVendor=0424, idProduct=2228 
[    2.646307] usb 1-5.1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3 
[    2.646309] usb 1-5.1.1: Product: Flash Card Reader 
[    2.646310] usb 1-5.1.1: Manufacturer: Generic 
[    2.646312] usb 1-5.1.1: SerialNumber: 080805402737 
[    2.648586] Initializing USB Mass Storage driver... 
[    2.648723] scsi8 : usb-storage 1-5.1.1:1.0 
[    2.648799] usbcore: registered new interface driver usb-storage 
[    2.648800] USB Mass Storage support registered. 
[    2.725289] usb 2-6.1: new full-speed USB device number 3 using ohci_hcd 
[    2.836259] usb 2-6.1: New USB device found, idVendor=413c, idProduct=2010 
[    2.836261] usb 2-6.1: New USB device strings: Mfr=1, Product=3, SerialNumber=0 
[    2.836263] usb 2-6.1: Product: Dell USB Keyboard 
[    2.836264] usb 2-6.1: Manufacturer: Dell 
[    2.851456] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:02.0/usb2/2-6/2-6.1/2-6.1:1.0/input/input3 
[    2.851543] hid-generic 0003:413C:2010.0002: input,hidraw1: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:02.0-6.1/input0 
[    2.865295] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:02.0/usb2/2-6/2-6.1/2-6.1:1.1/input/input4 
[    2.865373] hid-generic 0003:413C:2010.0003: input,hidraw2: USB HID v1.10 Device [Dell Dell USB Keyboard] on usb-0000:00:02.0-6.1/input1 
[    3.658287] scsi 8:0:0:0: Direct-Access     Generic  Flash HS-CF      5.39 PQ: 0 ANSI: 0 
[    3.661396] scsi 8:0:0:1: Direct-Access     Generic  Flash HS-COMBO   5.39 PQ: 0 ANSI: 0 
[    3.661974] sd 8:0:0:0: Attached scsi generic sg2 type 0 
[    3.662113] sd 8:0:0:1: Attached scsi generic sg3 type 0 
[    3.721760] sd 8:0:0:0: [sdb] Attached SCSI removable disk 
[    3.725759] sd 8:0:0:1: [sdc] Attached SCSI removable disk 
[    3.927933] floppy0: no floppy controllers found 
[   11.044939] scsi9 : ioc0: LSISAS1068E B1, FwRev=01120a00h, Ports=1, MaxQ=511, IRQ=70 
[   32.919429] ata3: EH in SWNCQ mode,QC:qc_active 0x7FFFFC01 sactive 0x7FFFFC01 
[   32.919433] ata3: SWNCQ:qc_active 0x1FC00 defer_bits 0x7FFE0001 last_issue_tag 0x10 
[   32.919433]   dhfis 0xFC00 dmafis 0x0 sdbfis 0x0 
[   32.919436] ata3: ATA_REG 0x40 ERR_REG 0x0 
[   32.919438] ata3: tag : dhfis dmafis sdbfis sactive 
[   32.919439] ata3: tag 0xa: 1 0 0 1   
[   32.919441] ata3: tag 0xb: 1 0 0 1   
[   32.919442] ata3: tag 0xc: 1 0 0 1   
[   32.919443] ata3: tag 0xd: 1 0 0 1   
[   32.919444] ata3: tag 0xe: 1 0 0 1   
[   32.919446] ata3: tag 0xf: 1 0 0 1   
[   32.919447] ata3: tag 0x10: 0 0 0 1   
[   32.919460] ata3.00: exception Emask 0x0 SAct 0x7ffffc01 SErr 0x0 action 0x6 frozen 
[   32.919464] ata3.00: failed command: READ FPDMA QUEUED 
[   32.919468] ata3.00: cmd 60/08:00:88:1b:44/00:00:12:00:00/40 tag 0 ncq 4096 in 
[   32.919468]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   32.919471] ata3.00: status: { DRDY } 
[   32.919472] ata3.00: failed command: READ FPDMA QUEUED 
[   32.919476] ata3.00: cmd 60/08:50:e0:1a:44/00:00:12:00:00/40 tag 10 ncq 4096 in 
[   32.919476]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   32.919477] ata3.00: status: { DRDY } 
[   32.919479] ata3.00: failed command: READ FPDMA QUEUED 
[   32.919482] ata3.00: cmd 60/08:58:e8:1a:44/00:00:12:00:00/40 tag 11 ncq 4096 in 
[   32.919482]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   32.919484] ata3.00: status: { DRDY } 
[   32.919485] ata3.00: failed command: READ FPDMA QUEUED 
[   32.919488] ata3.00: cmd 60/08:60:f0:1a:44/00:00:12:00:00/40 tag 12 ncq 4096 in 
[   32.919488]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   32.919490] ata3.00: status: { DRDY } 
[   32.919491] ata3.00: failed command: READ FPDMA QUEUED 
[   32.919494] ata3.00: cmd 60/08:68:f8:1a:44/00:00:12:00:00/40 tag 13 ncq 4096 in 
[   32.919494]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   32.919496] ata3.00: status: { DRDY } 
[   32.919497] ata3.00: failed command: READ FPDMA QUEUED 
[   32.919500] ata3.00: cmd 60/08:70:00:1b:44/00:00:12:00:00/40 tag 14 ncq 4096 in 
[   32.919500]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   32.919502] ata3.00: status: { DRDY } 
[   32.919503] ata3.00: failed command: READ FPDMA QUEUED 
[   32.919506] ata3.00: cmd 60/08:78:08:1b:44/00:00:12:00:00/40 tag 15 ncq 4096 in 
[   32.919506]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   32.919508] ata3.00: status: { DRDY } 
[   32.919509] ata3.00: failed command: READ FPDMA QUEUED 
[   32.919512] ata3.00: cmd 60/08:80:10:1b:44/00:00:12:00:00/40 tag 16 ncq 4096 in 
[   32.919512]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   32.919514] ata3.00: status: { DRDY } 
[   32.919515] ata3.00: failed command: READ FPDMA QUEUED 
[   32.919518] ata3.00: cmd 60/08:88:18:1b:44/00:00:12:00:00/40 tag 17 ncq 4096 in 
[   32.919518]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   32.919520] ata3.00: status: { DRDY } 
[   32.919521] ata3.00: failed command: READ FPDMA QUEUED 
[   32.919524] ata3.00: cmd 60/08:90:20:1b:44/00:00:12:00:00/40 tag 18 ncq 4096 in 
[   32.919524]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   32.919526] ata3.00: status: { DRDY } 
[   32.919527] ata3.00: failed command: READ FPDMA QUEUED 
[   32.919531] ata3.00: cmd 60/08:98:28:1b:44/00:00:12:00:00/40 tag 19 ncq 4096 in 
[   32.919531]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   32.919532] ata3.00: status: { DRDY } 
[   32.919533] ata3.00: failed command: READ FPDMA QUEUED 
[   32.919537] ata3.00: cmd 60/08:a0:30:1b:44/00:00:12:00:00/40 tag 20 ncq 4096 in 
[   32.919537]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   32.919538] ata3.00: status: { DRDY } 
[   32.919539] ata3.00: failed command: READ FPDMA QUEUED 
[   32.919543] ata3.00: cmd 60/08:a8:38:1b:44/00:00:12:00:00/40 tag 21 ncq 4096 in 
[   32.919543]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   32.919544] ata3.00: status: { DRDY } 
[   32.919546] ata3.00: failed command: READ FPDMA QUEUED 
[   32.919549] ata3.00: cmd 60/08:b0:40:1b:44/00:00:12:00:00/40 tag 22 ncq 4096 in 
[   32.919549]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   32.919550] ata3.00: status: { DRDY } 
[   32.919552] ata3.00: failed command: READ FPDMA QUEUED 
[   32.919555] ata3.00: cmd 60/08:b8:48:1b:44/00:00:12:00:00/40 tag 23 ncq 4096 in 
[   32.919555]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   32.919556] ata3.00: status: { DRDY } 
[   32.919558] ata3.00: failed command: READ FPDMA QUEUED 
[   32.919561] ata3.00: cmd 60/08:c0:50:1b:44/00:00:12:00:00/40 tag 24 ncq 4096 in 
[   32.919561]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   32.919562] ata3.00: status: { DRDY } 
[   32.919564] ata3.00: failed command: READ FPDMA QUEUED 
[   32.919567] ata3.00: cmd 60/08:c8:58:1b:44/00:00:12:00:00/40 tag 25 ncq 4096 in 
[   32.919567]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   32.919568] ata3.00: status: { DRDY } 
[   32.919570] ata3.00: failed command: READ FPDMA QUEUED 
[   32.919573] ata3.00: cmd 60/08:d0:60:1b:44/00:00:12:00:00/40 tag 26 ncq 4096 in 
[   32.919573]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   32.919574] ata3.00: status: { DRDY } 
[   32.919576] ata3.00: failed command: READ FPDMA QUEUED 
[   32.919579] ata3.00: cmd 60/08:d8:68:1b:44/00:00:12:00:00/40 tag 27 ncq 4096 in 
[   32.919579]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   32.919580] ata3.00: status: { DRDY } 
[   32.919582] ata3.00: failed command: READ FPDMA QUEUED 
[   32.919585] ata3.00: cmd 60/08:e0:70:1b:44/00:00:12:00:00/40 tag 28 ncq 4096 in 
[   32.919585]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   32.919586] ata3.00: status: { DRDY } 
[   32.919588] ata3.00: failed command: READ FPDMA QUEUED 
[   32.919591] ata3.00: cmd 60/08:e8:78:1b:44/00:00:12:00:00/40 tag 29 ncq 4096 in 
[   32.919591]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   32.919592] ata3.00: status: { DRDY } 
[   32.919594] ata3.00: failed command: READ FPDMA QUEUED 
[   32.919597] ata3.00: cmd 60/08:f0:80:1b:44/00:00:12:00:00/40 tag 30 ncq 4096 in 
[   32.919597]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   32.919598] ata3.00: status: { DRDY } 
[   32.919603] ata3: hard resetting link 
[   32.919605] ata3: nv: skipping hardreset on occupied port 
[   33.387279] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300) 
[   33.404171] ata3.00: configured for UDMA/133 
[   33.404178] ata3.00: device reported invalid CHS sector 0 
[   33.404181] ata3.00: device reported invalid CHS sector 0 
[   33.404183] ata3.00: device reported invalid CHS sector 0 
[   33.404185] ata3.00: device reported invalid CHS sector 0 
[   33.404187] ata3.00: device reported invalid CHS sector 0 
[   33.404189] ata3.00: device reported invalid CHS sector 0 
[   33.404191] ata3.00: device reported invalid CHS sector 0 
[   33.404193] ata3.00: device reported invalid CHS sector 0 
[   33.404195] ata3.00: device reported invalid CHS sector 0 
[   33.404197] ata3.00: device reported invalid CHS sector 0 
[   33.404199] ata3.00: device reported invalid CHS sector 0 
[   33.404201] ata3.00: device reported invalid CHS sector 0 
[   33.404203] ata3.00: device reported invalid CHS sector 0 
[   33.404205] ata3.00: device reported invalid CHS sector 0 
[   33.404207] ata3.00: device reported invalid CHS sector 0 
[   33.404209] ata3.00: device reported invalid CHS sector 0 
[   33.404210] ata3.00: device reported invalid CHS sector 0 
[   33.404212] ata3.00: device reported invalid CHS sector 0 
[   33.404214] ata3.00: device reported invalid CHS sector 0 
[   33.404216] ata3.00: device reported invalid CHS sector 0 
[   33.404218] ata3.00: device reported invalid CHS sector 0 
[   33.404220] ata3.00: device reported invalid CHS sector 0 
[   33.404238] ata3: EH complete 
[   63.950328] ata3: EH in SWNCQ mode,QC:qc_active 0x7800C000 sactive 0x7800C000 
[   63.950332] ata3: SWNCQ:qc_active 0x7800C000 defer_bits 0x0 last_issue_tag 0xe 
[   63.950332]   dhfis 0x7800C000 dmafis 0x0 sdbfis 0x0 
[   63.950335] ata3: ATA_REG 0x40 ERR_REG 0x0 
[   63.950336] ata3: tag : dhfis dmafis sdbfis sactive 
[   63.950338] ata3: tag 0xe: 1 0 0 1   
[   63.950340] ata3: tag 0xf: 1 0 0 1   
[   63.950341] ata3: tag 0x1b: 1 0 0 1   
[   63.950342] ata3: tag 0x1c: 1 0 0 1   
[   63.950343] ata3: tag 0x1d: 1 0 0 1   
[   63.950345] ata3: tag 0x1e: 1 0 0 1   
[   63.950352] ata3.00: exception Emask 0x0 SAct 0x7800c000 SErr 0x0 action 0x6 frozen 
[   63.950355] ata3.00: failed command: READ FPDMA QUEUED 
[   63.950360] ata3.00: cmd 60/10:70:08:1e:44/00:00:12:00:00/40 tag 14 ncq 8192 in 
[   63.950360]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   63.950362] ata3.00: status: { DRDY } 
[   63.950364] ata3.00: failed command: READ FPDMA QUEUED 
[   63.950367] ata3.00: cmd 60/08:78:00:1e:44/00:00:12:00:00/40 tag 15 ncq 4096 in 
[   63.950367]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   63.950369] ata3.00: status: { DRDY } 
[   63.950370] ata3.00: failed command: READ FPDMA QUEUED 
[   63.950373] ata3.00: cmd 60/08:d8:e0:1d:44/00:00:12:00:00/40 tag 27 ncq 4096 in 
[   63.950373]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   63.950375] ata3.00: status: { DRDY } 
[   63.950376] ata3.00: failed command: READ FPDMA QUEUED 
[   63.950379] ata3.00: cmd 60/08:e0:e8:1d:44/00:00:12:00:00/40 tag 28 ncq 4096 in 
[   63.950379]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   63.950381] ata3.00: status: { DRDY } 
[   63.950382] ata3.00: failed command: READ FPDMA QUEUED 
[   63.950386] ata3.00: cmd 60/08:e8:f0:1d:44/00:00:12:00:00/40 tag 29 ncq 4096 in 
[   63.950386]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   63.950387] ata3.00: status: { DRDY } 
[   63.950389] ata3.00: failed command: READ FPDMA QUEUED 
[   63.950392] ata3.00: cmd 60/08:f0:f8:1d:44/00:00:12:00:00/40 tag 30 ncq 4096 in 
[   63.950392]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   63.950393] ata3.00: status: { DRDY } 
[   63.950396] ata3: hard resetting link 
[   63.950398] ata3: nv: skipping hardreset on occupied port 
[   64.418181] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300) 
[   64.434641] ata3.00: configured for UDMA/133 
[   64.434646] ata3.00: device reported invalid CHS sector 0 
[   64.434648] ata3.00: device reported invalid CHS sector 0 
[   64.434650] ata3.00: device reported invalid CHS sector 0 
[   64.434652] ata3.00: device reported invalid CHS sector 0 
[   64.434654] ata3.00: device reported invalid CHS sector 0 
[   64.434656] ata3.00: device reported invalid CHS sector 0 
[   64.434663] ata3: EH complete 
[   94.917268] ata3: EH in SWNCQ mode,QC:qc_active 0x7FFFFFFF sactive 0x7FFFFFFF 
[   94.917271] ata3: SWNCQ:qc_active 0x7E defer_bits 0x7FFFFF81 last_issue_tag 0x6 
[   94.917271]   dhfis 0x3E dmafis 0x0 sdbfis 0x0 
[   94.917274] ata3: ATA_REG 0x40 ERR_REG 0x0 
[   94.917275] ata3: tag : dhfis dmafis sdbfis sactive 
[   94.917276] ata3: tag 0x1: 1 0 0 1   
[   94.917278] ata3: tag 0x2: 1 0 0 1   
[   94.917279] ata3: tag 0x3: 1 0 0 1   
[   94.917280] ata3: tag 0x4: 1 0 0 1   
[   94.917282] ata3: tag 0x5: 1 0 0 1   
[   94.917283] ata3: tag 0x6: 0 0 0 1   
[   94.917290] ata3.00: exception Emask 0x0 SAct 0x7fffffff SErr 0x0 action 0x6 frozen 
[   94.917293] ata3.00: failed command: READ FPDMA QUEUED 
[   94.917297] ata3.00: cmd 60/08:00:18:22:44/00:00:12:00:00/40 tag 0 ncq 4096 in 
[   94.917297]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   94.917299] ata3.00: status: { DRDY } 
[   94.917300] ata3.00: failed command: READ FPDMA QUEUED 
[   94.917303] ata3.00: cmd 60/08:08:70:21:44/00:00:12:00:00/40 tag 1 ncq 4096 in 
[   94.917303]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   94.917305] ata3.00: status: { DRDY } 
[   94.917306] ata3.00: failed command: READ FPDMA QUEUED 
[   94.917310] ata3.00: cmd 60/08:10:78:21:44/00:00:12:00:00/40 tag 2 ncq 4096 in 
[   94.917310]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   94.917311] ata3.00: status: { DRDY } 
[   94.917312] ata3.00: failed command: READ FPDMA QUEUED 
[   94.917316] ata3.00: cmd 60/08:18:80:21:44/00:00:12:00:00/40 tag 3 ncq 4096 in 
[   94.917316]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   94.917317] ata3.00: status: { DRDY } 
[   94.917319] ata3.00: failed command: READ FPDMA QUEUED 
[   94.917322] ata3.00: cmd 60/08:20:88:21:44/00:00:12:00:00/40 tag 4 ncq 4096 in 
[   94.917322]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   94.917323] ata3.00: status: { DRDY } 
[   94.917325] ata3.00: failed command: READ FPDMA QUEUED 
[   94.917328] ata3.00: cmd 60/08:28:90:21:44/00:00:12:00:00/40 tag 5 ncq 4096 in 
[   94.917328]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   94.917329] ata3.00: status: { DRDY } 
[   94.917331] ata3.00: failed command: READ FPDMA QUEUED 
[   94.917334] ata3.00: cmd 60/08:30:98:21:44/00:00:12:00:00/40 tag 6 ncq 4096 in 
[   94.917334]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   94.917335] ata3.00: status: { DRDY } 
[   94.917337] ata3.00: failed command: READ FPDMA QUEUED 
[   94.917340] ata3.00: cmd 60/08:38:a0:21:44/00:00:12:00:00/40 tag 7 ncq 4096 in 
[   94.917340]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   94.917341] ata3.00: status: { DRDY } 
[   94.917343] ata3.00: failed command: READ FPDMA QUEUED 
[   94.917346] ata3.00: cmd 60/08:40:a8:21:44/00:00:12:00:00/40 tag 8 ncq 4096 in 
[   94.917346]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   94.917347] ata3.00: status: { DRDY } 
[   94.917349] ata3.00: failed command: READ FPDMA QUEUED 
[   94.917352] ata3.00: cmd 60/08:48:b0:21:44/00:00:12:00:00/40 tag 9 ncq 4096 in 
[   94.917352]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   94.917353] ata3.00: status: { DRDY } 
[   94.917355] ata3.00: failed command: READ FPDMA QUEUED 
[   94.917358] ata3.00: cmd 60/08:50:b8:21:44/00:00:12:00:00/40 tag 10 ncq 4096 in 
[   94.917358]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   94.917359] ata3.00: status: { DRDY } 
[   94.917361] ata3.00: failed command: READ FPDMA QUEUED 
[   94.917364] ata3.00: cmd 60/08:58:c0:21:44/00:00:12:00:00/40 tag 11 ncq 4096 in 
[   94.917364]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   94.917366] ata3.00: status: { DRDY } 
[   94.917367] ata3.00: failed command: READ FPDMA QUEUED 
[   94.917370] ata3.00: cmd 60/08:60:c8:21:44/00:00:12:00:00/40 tag 12 ncq 4096 in 
[   94.917370]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   94.917372] ata3.00: status: { DRDY } 
[   94.917373] ata3.00: failed command: READ FPDMA QUEUED 
[   94.917376] ata3.00: cmd 60/08:68:d0:21:44/00:00:12:00:00/40 tag 13 ncq 4096 in 
[   94.917376]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   94.917378] ata3.00: status: { DRDY } 
[   94.917379] ata3.00: failed command: READ FPDMA QUEUED 
[   94.917382] ata3.00: cmd 60/08:70:d8:21:44/00:00:12:00:00/40 tag 14 ncq 4096 in 
[   94.917382]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   94.917384] ata3.00: status: { DRDY } 
[   94.917385] ata3.00: failed command: READ FPDMA QUEUED 
[   94.917388] ata3.00: cmd 60/08:78:e0:21:44/00:00:12:00:00/40 tag 15 ncq 4096 in 
[   94.917388]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   94.917390] ata3.00: status: { DRDY } 
[   94.917391] ata3.00: failed command: READ FPDMA QUEUED 
[   94.917394] ata3.00: cmd 60/08:80:e8:21:44/00:00:12:00:00/40 tag 16 ncq 4096 in 
[   94.917394]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   94.917396] ata3.00: status: { DRDY } 
[   94.917397] ata3.00: failed command: READ FPDMA QUEUED 
[   94.917401] ata3.00: cmd 60/08:88:f0:21:44/00:00:12:00:00/40 tag 17 ncq 4096 in 
[   94.917401]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   94.917402] ata3.00: status: { DRDY } 
[   94.917403] ata3.00: failed command: READ FPDMA QUEUED 
[   94.917407] ata3.00: cmd 60/08:90:f8:21:44/00:00:12:00:00/40 tag 18 ncq 4096 in 
[   94.917407]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   94.917408] ata3.00: status: { DRDY } 
[   94.917410] ata3.00: failed command: READ FPDMA QUEUED 
[   94.917413] ata3.00: cmd 60/08:98:00:22:44/00:00:12:00:00/40 tag 19 ncq 4096 in 
[   94.917413]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   94.917414] ata3.00: status: { DRDY } 
[   94.917416] ata3.00: failed command: READ FPDMA QUEUED 
[   94.917419] ata3.00: cmd 60/08:a0:08:22:44/00:00:12:00:00/40 tag 20 ncq 4096 in 
[   94.917419]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   94.917420] ata3.00: status: { DRDY } 
[   94.917422] ata3.00: failed command: READ FPDMA QUEUED 
[   94.917425] ata3.00: cmd 60/08:a8:10:22:44/00:00:12:00:00/40 tag 21 ncq 4096 in 
[   94.917425]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   94.917426] ata3.00: status: { DRDY } 
[   94.917428] ata3.00: failed command: READ FPDMA QUEUED 
[   94.917431] ata3.00: cmd 60/08:b0:20:22:44/00:00:12:00:00/40 tag 22 ncq 4096 in 
[   94.917431]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   94.917432] ata3.00: status: { DRDY } 
[   94.917434] ata3.00: failed command: READ FPDMA QUEUED 
[   94.917437] ata3.00: cmd 60/08:b8:28:22:44/00:00:12:00:00/40 tag 23 ncq 4096 in 
[   94.917437]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   94.917438] ata3.00: status: { DRDY } 
[   94.917440] ata3.00: failed command: READ FPDMA QUEUED 
[   94.917443] ata3.00: cmd 60/08:c0:30:22:44/00:00:12:00:00/40 tag 24 ncq 4096 in 
[   94.917443]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   94.917444] ata3.00: status: { DRDY } 
[   94.917446] ata3.00: failed command: READ FPDMA QUEUED 
[   94.917449] ata3.00: cmd 60/08:c8:38:22:44/00:00:12:00:00/40 tag 25 ncq 4096 in 
[   94.917449]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   94.917450] ata3.00: status: { DRDY } 
[   94.917452] ata3.00: failed command: READ FPDMA QUEUED 
[   94.917455] ata3.00: cmd 60/08:d0:40:22:44/00:00:12:00:00/40 tag 26 ncq 4096 in 
[   94.917455]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   94.917456] ata3.00: status: { DRDY } 
[   94.917458] ata3.00: failed command: READ FPDMA QUEUED 
[   94.917461] ata3.00: cmd 60/08:d8:48:22:44/00:00:12:00:00/40 tag 27 ncq 4096 in 
[   94.917461]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   94.917462] ata3.00: status: { DRDY } 
[   94.917464] ata3.00: failed command: READ FPDMA QUEUED 
[   94.917467] ata3.00: cmd 60/08:e0:50:22:44/00:00:12:00:00/40 tag 28 ncq 4096 in 
[   94.917467]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   94.917469] ata3.00: status: { DRDY } 
[   94.917470] ata3.00: failed command: READ FPDMA QUEUED 
[   94.917473] ata3.00: cmd 60/08:e8:58:22:44/00:00:12:00:00/40 tag 29 ncq 4096 in 
[   94.917473]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   94.917475] ata3.00: status: { DRDY } 
[   94.917476] ata3.00: failed command: READ FPDMA QUEUED 
[   94.917479] ata3.00: cmd 60/08:f0:60:22:44/00:00:12:00:00/40 tag 30 ncq 4096 in 
[   94.917479]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   94.917481] ata3.00: status: { DRDY } 
[   94.917484] ata3: hard resetting link 
[   94.917485] ata3: nv: skipping hardreset on occupied port 
[   95.385105] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300) 
[   95.402024] ata3.00: configured for UDMA/133 
[   95.402028] ata3.00: device reported invalid CHS sector 0 
[   95.402031] ata3.00: device reported invalid CHS sector 0 
[   95.402033] ata3.00: device reported invalid CHS sector 0 
[   95.402034] ata3.00: device reported invalid CHS sector 0 
[   95.402036] ata3.00: device reported invalid CHS sector 0 
[   95.402038] ata3.00: device reported invalid CHS sector 0 
[   95.402040] ata3.00: device reported invalid CHS sector 0 
[   95.402042] ata3.00: device reported invalid CHS sector 0 
[   95.402044] ata3.00: device reported invalid CHS sector 0 
[   95.402046] ata3.00: device reported invalid CHS sector 0 
[   95.402047] ata3.00: device reported invalid CHS sector 0 
[   95.402049] ata3.00: device reported invalid CHS sector 0 
[   95.402051] ata3.00: device reported invalid CHS sector 0 
[   95.402053] ata3.00: device reported invalid CHS sector 0 
[   95.402055] ata3.00: device reported invalid CHS sector 0 
[   95.402057] ata3.00: device reported invalid CHS sector 0 
[   95.402058] ata3.00: device reported invalid CHS sector 0 
[   95.402060] ata3.00: device reported invalid CHS sector 0 
[   95.402062] ata3.00: device reported invalid CHS sector 0 
[   95.402064] ata3.00: device reported invalid CHS sector 0 
[   95.402066] ata3.00: device reported invalid CHS sector 0 
[   95.402068] ata3.00: device reported invalid CHS sector 0 
[   95.402070] ata3.00: device reported invalid CHS sector 0 
[   95.402071] ata3.00: device reported invalid CHS sector 0 
[   95.402073] ata3.00: device reported invalid CHS sector 0 
[   95.402075] ata3.00: device reported invalid CHS sector 0 
[   95.402077] ata3.00: device reported invalid CHS sector 0 
[   95.402079] ata3.00: device reported invalid CHS sector 0 
[   95.402081] ata3.00: device reported invalid CHS sector 0 
[   95.402082] ata3.00: device reported invalid CHS sector 0 
[   95.402084] ata3.00: device reported invalid CHS sector 0 
[   95.402106] ata3: EH complete 
[  125.884187] ata3: EH in SWNCQ mode,QC:qc_active 0x1FFFC000 sactive 0x1FFFC000 
[  125.884190] ata3: SWNCQ:qc_active 0x3FC000 defer_bits 0x1FC00000 last_issue_tag 0x15 
[  125.884190]   dhfis 0x1FC000 dmafis 0x0 sdbfis 0x0 
[  125.884193] ata3: ATA_REG 0x40 ERR_REG 0x0 
[  125.884194] ata3: tag : dhfis dmafis sdbfis sactive 
[  125.884195] ata3: tag 0xe: 1 0 0 1   
[  125.884196] ata3: tag 0xf: 1 0 0 1   
[  125.884198] ata3: tag 0x10: 1 0 0 1   
[  125.884199] ata3: tag 0x11: 1 0 0 1   
[  125.884200] ata3: tag 0x12: 1 0 0 1   
[  125.884202] ata3: tag 0x13: 1 0 0 1   
[  125.884203] ata3: tag 0x14: 1 0 0 1   
[  125.884204] ata3: tag 0x15: 0 0 0 1   
[  125.884210] ata3.00: NCQ disabled due to excessive errors 
[  125.884212] ata3.00: exception Emask 0x0 SAct 0x1fffc000 SErr 0x0 action 0x6 frozen 
[  125.884214] ata3.00: failed command: READ FPDMA QUEUED 
[  125.884218] ata3.00: cmd 60/08:70:58:26:44/00:00:12:00:00/40 tag 14 ncq 4096 in 
[  125.884218]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[  125.884220] ata3.00: status: { DRDY } 
[  125.884221] ata3.00: failed command: READ FPDMA QUEUED 
[  125.884224] ata3.00: cmd 60/08:78:60:26:44/00:00:12:00:00/40 tag 15 ncq 4096 in 
[  125.884224]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[  125.884226] ata3.00: status: { DRDY } 
[  125.884227] ata3.00: failed command: READ FPDMA QUEUED 
[  125.884230] ata3.00: cmd 60/08:80:68:26:44/00:00:12:00:00/40 tag 16 ncq 4096 in 
[  125.884230]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[  125.884232] ata3.00: status: { DRDY } 
[  125.884233] ata3.00: failed command: READ FPDMA QUEUED 
[  125.884237] ata3.00: cmd 60/08:88:70:26:44/00:00:12:00:00/40 tag 17 ncq 4096 in 
[  125.884237]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[  125.884238] ata3.00: status: { DRDY } 
[  125.884240] ata3.00: failed command: READ FPDMA QUEUED 
[  125.884243] ata3.00: cmd 60/08:90:78:26:44/00:00:12:00:00/40 tag 18 ncq 4096 in 
[  125.884243]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[  125.884244] ata3.00: status: { DRDY } 
[  125.884246] ata3.00: failed command: READ FPDMA QUEUED 
[  125.884249] ata3.00: cmd 60/08:98:80:26:44/00:00:12:00:00/40 tag 19 ncq 4096 in 
[  125.884249]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[  125.884250] ata3.00: status: { DRDY } 
[  125.884252] ata3.00: failed command: READ FPDMA QUEUED 
[  125.884255] ata3.00: cmd 60/08:a0:88:26:44/00:00:12:00:00/40 tag 20 ncq 4096 in 
[  125.884255]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[  125.884256] ata3.00: status: { DRDY } 
[  125.884258] ata3.00: failed command: READ FPDMA QUEUED 
[  125.884261] ata3.00: cmd 60/08:a8:90:26:44/00:00:12:00:00/40 tag 21 ncq 4096 in 
[  125.884261]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[  125.884262] ata3.00: status: { DRDY } 
[  125.884264] ata3.00: failed command: READ FPDMA QUEUED 
[  125.884267] ata3.00: cmd 60/08:b0:98:26:44/00:00:12:00:00/40 tag 22 ncq 4096 in 
[  125.884267]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[  125.884269] ata3.00: status: { DRDY } 
[  125.884270] ata3.00: failed command: READ FPDMA QUEUED 
[  125.884273] ata3.00: cmd 60/08:b8:a0:26:44/00:00:12:00:00/40 tag 23 ncq 4096 in 
[  125.884273]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[  125.884275] ata3.00: status: { DRDY } 
[  125.884276] ata3.00: failed command: READ FPDMA QUEUED 
[  125.884279] ata3.00: cmd 60/08:c0:a8:26:44/00:00:12:00:00/40 tag 24 ncq 4096 in 
[  125.884279]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[  125.884281] ata3.00: status: { DRDY } 
[  125.884282] ata3.00: failed command: READ FPDMA QUEUED 
[  125.884285] ata3.00: cmd 60/08:c8:b0:26:44/00:00:12:00:00/40 tag 25 ncq 4096 in 
[  125.884285]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[  125.884287] ata3.00: status: { DRDY } 
[  125.884288] ata3.00: failed command: READ FPDMA QUEUED 
[  125.884291] ata3.00: cmd 60/08:d0:b8:26:44/00:00:12:00:00/40 tag 26 ncq 4096 in 
[  125.884291]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[  125.884293] ata3.00: status: { DRDY } 
[  125.884294] ata3.00: failed command: READ FPDMA QUEUED 
[  125.884297] ata3.00: cmd 60/08:d8:c0:26:44/00:00:12:00:00/40 tag 27 ncq 4096 in 
[  125.884297]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[  125.884299] ata3.00: status: { DRDY } 
[  125.884300] ata3.00: failed command: READ FPDMA QUEUED 
[  125.884303] ata3.00: cmd 60/20:e0:c8:26:44/00:00:12:00:00/40 tag 28 ncq 16384 in 
[  125.884303]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[  125.884305] ata3.00: status: { DRDY } 
[  125.884308] ata3: hard resetting link 
[  125.884309] ata3: nv: skipping hardreset on occupied port 
[  126.352028] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300) 
[  126.376457] ata3.00: configured for UDMA/133 
[  126.376462] ata3.00: device reported invalid CHS sector 0 
[  126.376464] ata3.00: device reported invalid CHS sector 0 
[  126.376466] ata3.00: device reported invalid CHS sector 0 
[  126.376468] ata3.00: device reported invalid CHS sector 0 
[  126.376470] ata3.00: device reported invalid CHS sector 0 
[  126.376472] ata3.00: device reported invalid CHS sector 0 
[  126.376474] ata3.00: device reported invalid CHS sector 0 
[  126.376476] ata3.00: device reported invalid CHS sector 0 
[  126.376478] ata3.00: device reported invalid CHS sector 0 
[  126.376479] ata3.00: device reported invalid CHS sector 0 
[  126.376481] ata3.00: device reported invalid CHS sector 0 
[  126.376483] ata3.00: device reported invalid CHS sector 0 
[  126.376485] ata3.00: device reported invalid CHS sector 0 
[  126.376487] ata3.00: device reported invalid CHS sector 0 
[  126.376490] ata3.00: device reported invalid CHS sector 0 
[  126.376503] ata3: EH complete 
[  127.447589] EXT4-fs (sda1): recovery complete 
[  127.456458] EXT4-fs (sda1): mounted filesystem with writeback data mode. Opts: (null) 
[  142.726705] Adding 4193276k swap on /dev/sda5.  Priority:-1 extents:1 across:4193276k  
[  142.807634] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready 
[  142.807644] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready 
[  142.832736] udevd[445]: starting version 175 
[  143.055183] type=1400 audit(1376433861.759:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=624 comm="apparmor_parser" 
[  143.055205] type=1400 audit(1376433861.759:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=623 comm="apparmor_parser" 
[  143.055587] type=1400 audit(1376433861.759:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=624 comm="apparmor_parser" 
[  143.055617] type=1400 audit(1376433861.759:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=623 comm="apparmor_parser" 
[  143.055811] type=1400 audit(1376433861.759:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=624 comm="apparmor_parser" 
[  143.055846] type=1400 audit(1376433861.759:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=623 comm="apparmor_parser" 
[  143.056490] type=1400 audit(1376433861.759:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=625 comm="apparmor_parser" 
[  143.056896] type=1400 audit(1376433861.759:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=625 comm="apparmor_parser" 
[  143.057123] type=1400 audit(1376433861.759:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=625 comm="apparmor_parser" 
[  143.271238] k10temp 0000:00:18.3: unreliable CPU thermal sensor; monitoring disabled 
[  143.274570] k10temp 0000:00:19.3: unreliable CPU thermal sensor; monitoring disabled 
[  143.276003] lp: driver loaded but no devices found 
[  143.278568] i2c i2c-0: nForce2 SMBus adapter at 0x4000 
[  143.278586] i2c i2c-1: nForce2 SMBus adapter at 0x4040 
[  143.280749] MCE: In-kernel MCE decoding enabled. 
[  143.280789] i2c i2c-2: nForce2 SMBus adapter at 0x2000 
[  143.280817] i2c i2c-3: nForce2 SMBus adapter at 0x2040 
[  143.282872] EDAC MC: Ver: 3.0.0 
[  143.283901] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4 
[  143.286574] nv_tco: NV TCO WatchDog Timer Driver v0.01 
[  143.286821] [drm] Initialized drm 1.1.0 20060810 
[  143.286825] nv_tco: Watchdog reboot detected 
[  143.288844] nv_tco: initialized (0xf940). heartbeat=30 sec (nowayout=0) 
[  143.292887] kvm: Nested Virtualization enabled 
[  143.292894] kvm: Nested Paging enabled 
[  143.293404] AMD64 EDAC driver v3.4.0 
[  143.293460] EDAC amd64: DRAM ECC enabled. 
[  143.293470] EDAC amd64: F10h detected (node 0). 
[  143.293496] EDAC MC: DCT0 chip selects: 
[  143.293497] EDAC amd64: MC: 0:  1024MB 1:  1024MB 
[  143.293499] EDAC amd64: MC: 2:  1024MB 3:  1024MB 
[  143.293500] EDAC amd64: MC: 4:     0MB 5:     0MB 
[  143.293501] EDAC amd64: MC: 6:     0MB 7:     0MB 
[  143.293502] EDAC MC: DCT1 chip selects: 
[  143.293503] EDAC amd64: MC: 0:  1024MB 1:  1024MB 
[  143.293504] EDAC amd64: MC: 2:  1024MB 3:  1024MB 
[  143.293505] EDAC amd64: MC: 4:     0MB 5:     0MB 
[  143.293506] EDAC amd64: MC: 6:     0MB 7:     0MB 
[  143.293508] EDAC amd64: using x4 syndromes. 
[  143.293509] EDAC amd64: MCT channel count: 2 
[  143.293533] EDAC amd64: CS0: Registered DDR2 RAM 
[  143.293534] EDAC amd64: CS1: Registered DDR2 RAM 
[  143.293535] EDAC amd64: CS2: Registered DDR2 RAM 
[  143.293536] EDAC amd64: CS3: Registered DDR2 RAM 
[  143.295273] EDAC MC0: Giving out device to 'amd64_edac' 'F10h': DEV 0000:00:18.2 
[  143.295316] EDAC amd64: DRAM ECC enabled. 
[  143.295338] EDAC amd64: F10h detected (node 1). 
[  143.295364] EDAC MC: DCT0 chip selects: 
[  143.295366] EDAC amd64: MC: 0:  1024MB 1:  1024MB 
[  143.295367] EDAC amd64: MC: 2:  1024MB 3:  1024MB 
[  143.295368] EDAC amd64: MC: 4:     0MB 5:     0MB 
[  143.295369] EDAC amd64: MC: 6:     0MB 7:     0MB 
[  143.295370] EDAC MC: DCT1 chip selects: 
[  143.295371] EDAC amd64: MC: 0:  1024MB 1:  1024MB 
[  143.295372] EDAC amd64: MC: 2:  1024MB 3:  1024MB 
[  143.295373] EDAC amd64: MC: 4:     0MB 5:     0MB 
[  143.295374] EDAC amd64: MC: 6:     0MB 7:     0MB 
[  143.295375] EDAC amd64: using x4 syndromes. 
[  143.295376] EDAC amd64: MCT channel count: 2 
[  143.295399] EDAC amd64: CS0: Registered DDR2 RAM 
[  143.295400] EDAC amd64: CS1: Registered DDR2 RAM 
[  143.295401] EDAC amd64: CS2: Registered DDR2 RAM 
[  143.295402] EDAC amd64: CS3: Registered DDR2 RAM 
[  143.295605] EDAC MC1: Giving out device to 'amd64_edac' 'F10h': DEV 0000:00:19.2 
[  143.295648] EDAC PCI0: Giving out device to module 'amd64_edac' controller 'EDAC PCI controller': DEV '0000:00:18.2' (POLLED) 
[  143.298242] wmi: Mapper loaded 
[  143.313550] ACPI: PCI Interrupt Link [LXPB] enabled at IRQ 22 
[  143.314244] nouveau  [  DEVICE][0000:18:00.0] BOOT0  : 0x049d00a2 
[  143.314247] nouveau  [  DEVICE][0000:18:00.0] Chipset: G71 (NV49) 
[  143.314249] nouveau  [  DEVICE][0000:18:00.0] Family : NV40 
[  143.314873] nouveau  [   VBIOS][0000:18:00.0] checking PRAMIN for image... 
[  143.353200] nouveau  [   VBIOS][0000:18:00.0] ... appears to be valid 
[  143.353202] nouveau  [   VBIOS][0000:18:00.0] using image from PRAMIN 
[  143.353317] nouveau  [   VBIOS][0000:18:00.0] BIT signature found 
[  143.353320] nouveau  [   VBIOS][0000:18:00.0] version 05.71.22.57.06 
[  143.353535] nouveau  [     PFB][0000:18:00.0] RAM type: GDDR3 
[  143.353536] nouveau  [     PFB][0000:18:00.0] RAM size: 256 MiB 
[  143.353538] nouveau  [     PFB][0000:18:00.0]    ZCOMP: 294912 tags 
[  143.367252] tpm_tis: probe of 00:0a failed with error -5 
[  143.368651] tpm_inf_pnp 00:0a: Found TPM with ID IFX0102 
[  143.368701] tpm_inf_pnp 00:0a: TPM found: config base 0x4e, data base 0x4c0, chip version 0x000b, vendor id 0x15d1 (Infineon), product id 0x000b (SLB 9635 TT 1.2) 
[  143.380482] [TTM] Zone  kernel: Available graphics memory: 8217134 kiB 
[  143.380484] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB 
[  143.380485] [TTM] Initializing pool allocator 
[  143.380489] [TTM] Initializing DMA pool allocator 
[  143.390545] nouveau  [     DRM] VRAM: 250 MiB 
[  143.390550] nouveau  [     DRM] GART: 512 MiB 
[  143.390556] nouveau  [     DRM] BIT BIOS found 
[  143.390559] nouveau  [     DRM] Bios version 05.71.22.57 
[  143.390562] nouveau  [     DRM] TMDS table version 1.1 
[  143.390564] nouveau W[     DRM] TMDS table script pointers not stubbed 
[  143.390565] nouveau  [     DRM] DCB version 3.0 
[  143.390568] nouveau  [     DRM] DCB outp 00: 01000300 00000028 
[  143.390570] nouveau  [     DRM] DCB outp 01: 03000302 00000000 
[  143.390571] nouveau  [     DRM] DCB outp 02: 04011310 00000028 
[  143.390573] nouveau  [     DRM] DCB outp 03: 0c011312 00000000 
[  143.390575] nouveau  [     DRM] DCB conn 00: 1030 
[  143.390577] nouveau  [     DRM] DCB conn 01: 2130 
[  143.390578] nouveau  [     DRM] DCB conn 02: 0260 
[  143.392076] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010). 
[  143.392078] [drm] No driver support for vblank timestamp query. 
[  143.392150] nouveau  [     DRM] 0xB8AD: Parsing digital output script table 
[  143.441755] nouveau  [     DRM] 0xB8FD: Parsing digital output script table 
[  143.491709] nouveau  [     DRM] 2 available performance level(s) 
[  143.491713] nouveau  [     DRM] 0: core 470MHz shader 450MHz memory 660MHz voltage 1200mV fanspeed 20% 
[  143.491716] nouveau  [     DRM] 1: core 470MHz shader 450MHz memory 660MHz voltage 1200mV fanspeed 40% 
[  143.491719] nouveau  [     DRM] c: core 450MHz shader 450MHz memory 661MHz voltage 1200mV fanspeed 20% 
[  143.493373] nouveau  [     DRM] MM: using M2MF for buffer copies 
[  143.552342] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21 
[  143.552344] input: HP WMI hotkeys as /devices/virtual/input/input5 
[  143.552400] snd_hda_intel 0000:00:06.1: irq 71 for MSI/MSI-X 
[  143.552430] snd_hda_intel 0000:00:06.1: setting latency timer to 64 
[  143.571487] nouveau  [     DRM] allocated 1920x1200 fb: 0x9000, bo ffff8802146dfc00 
[  143.571554] fbcon: nouveaufb (fb0) is primary device 
[  143.581815] nouveau  [     DRM] 0xB8AD: Parsing digital output script table 
[  143.631539] Console: switching to colour frame buffer device 240x75 
[  143.632447] nouveau 0000:18:00.0: fb0: nouveaufb frame buffer device 
[  143.632449] nouveau 0000:18:00.0: registered panic notifier 
[  143.632454] [drm] Initialized nouveau 1.1.0 20120801 for 0000:18:00.0 on minor 0 
[  144.190794] hda_codec: ALC262: SKU not ready 0x411111f0 
[  144.444143] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro 
[  144.568103] init: failsafe main process (961) killed by TERM signal 
[  144.676714] Bluetooth: Core ver 2.16 
[  144.676746] NET: Registered protocol family 31 
[  144.676748] Bluetooth: HCI device and connection manager initialized 
[  144.676761] Bluetooth: HCI socket layer initialized 
[  144.676763] Bluetooth: L2CAP socket layer initialized 
[  144.676768] Bluetooth: SCO socket layer initialized 
[  144.679636] Bluetooth: BNEP (Ethernet Emulation) ver 1.3 
[  144.679639] Bluetooth: BNEP filters: protocol multicast 
[  144.679645] Bluetooth: BNEP socket layer initialized 
[  144.680014] Bluetooth: RFCOMM TTY layer initialized 
[  144.680031] Bluetooth: RFCOMM socket layer initialized 
[  144.680033] Bluetooth: RFCOMM ver 1.11 
[  144.850153] type=1400 audit(1376433863.551:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1041 comm="apparmor_parser" 
[  145.018894] init: avahi-cups-reload main process (1076) terminated with status 1 
[  145.130893] ppdev: user-space parallel port driver 
[  145.307035] init: alsa-restore main process (1128) terminated with status 19 
[  145.335419] input: HDA NVidia Line as /devices/pci0000:00/0000:00:06.1/sound/card0/input6 
[  145.335523] input: HDA NVidia Front Mic as /devices/pci0000:00/0000:00:06.1/sound/card0/input7 
[  145.335587] input: HDA NVidia Rear Mic as /devices/pci0000:00/0000:00:06.1/sound/card0/input8 
[  145.335750] input: HDA NVidia Front Headphone as /devices/pci0000:00/0000:00:06.1/sound/card0/input9 
[  145.335815] input: HDA NVidia Line Out as /devices/pci0000:00/0000:00:06.1/sound/card0/input10 
[  146.118912] forcedeth 0000:00:08.0: irq 72 for MSI/MSI-X 
[  146.118945] forcedeth 0000:00:08.0 eth0: MSI enabled 
[  146.123429] forcedeth 0000:00:09.0: irq 73 for MSI/MSI-X 
[  146.123449] forcedeth 0000:00:09.0 eth1: MSI enabled 
[  146.123665] forcedeth 0000:00:09.0 eth1: no link during initialization 
[  146.124077] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready 
[  146.124560] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready 
[  146.334228] floppy0: no floppy controllers found
```

the lspci output 

```
0000:00:00.0 RAM memory: NVIDIA Corporation MCP55 Memory Controller (rev a2) 
    Subsystem: Hewlett-Packard Company Device 12fe 
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx- 
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
    Latency: 0 
    Capabilities: [44] HyperTransport: Slave or Primary Interface 
        Command: BaseUnitID=0 UnitCnt=15 MastHost- DefDir- DUL- 
        Link Control 0: CFlE+ CST- CFE- <LkFail- Init+ EOC- TXO- <CRCErr=0 IsocEn- LSEn+ ExtCTL- 64b- 
        Link Config 0: MLWI=16bit DwFcIn- MLWO=16bit DwFcOut- LWI=16bit DwFcInEn- LWO=16bit DwFcOutEn- 
        Link Control 1: CFlE- CST- CFE- <LkFail+ Init- EOC+ TXO+ <CRCErr=0 IsocEn- LSEn- ExtCTL- 64b- 
        Link Config 1: MLWI=8bit DwFcIn- MLWO=8bit DwFcOut- LWI=8bit DwFcInEn- LWO=8bit DwFcOutEn- 
        Revision ID: 1.03 
        Link Frequency 0: 1.0GHz 
        Link Error 0: <Prot- <Ovfl- <EOC- CTLTm- 
        Link Frequency Capability 0: 200MHz+ 300MHz+ 400MHz+ 500MHz+ 600MHz+ 800MHz+ 1.0GHz+ 1.2GHz- 1.4GHz- 1.6GHz- Vend- 
        Feature Capability: IsocFC+ LDTSTOP+ CRCTM- ECTLT- 64bA- UIDRD- 
        Link Frequency 1: 200MHz 
        Link Error 1: <Prot- <Ovfl- <EOC- CTLTm- 
        Link Frequency Capability 1: 200MHz- 300MHz- 400MHz- 500MHz- 600MHz- 800MHz- 1.0GHz- 1.2GHz- 1.4GHz- 1.6GHz- Vend- 
        Error Handling: PFlE+ OFlE+ PFE- OFE- EOCFE- RFE- CRCFE- SERRFE- CF- RE- PNFE- ONFE- EOCNFE- RNFE- CRCNFE- SERRNFE- 
        Prefetchable memory behind bridge Upper: 00-00 
        Bus Number: 00 
    Capabilities: [dc] HyperTransport: MSI Mapping Enable+ Fixed- 
        Mapping Address Base: 00000000fee00000 
 
0000:00:01.0 ISA bridge: NVIDIA Corporation MCP55 LPC Bridge (rev a3) 
    Subsystem: Hewlett-Packard Company Device 12fe 
    Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx- 
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
    Latency: 0 
 
0000:00:01.1 SMBus: NVIDIA Corporation MCP55 SMBus (rev a3) 
    Subsystem: Hewlett-Packard Company Device 12fe 
    Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx- 
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
    Interrupt: pin A routed to IRQ 11 
    Region 4: I/O ports at 4000 [size=64] 
    Region 5: I/O ports at 4040 [size=64] 
    Capabilities: [44] Power Management version 2 
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold+) 
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME- 
    Kernel driver in use: nForce2_smbus 
 
0000:00:02.0 USB controller: NVIDIA Corporation MCP55 USB Controller (rev a1) (prog-if 10 [OHCI]) 
    Subsystem: Hewlett-Packard Company Device 12fe 
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx- 
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
    Latency: 0 (750ns min, 250ns max) 
    Interrupt: pin A routed to IRQ 22 
    Region 0: Memory at fa244000 (32-bit, non-prefetchable) [size=4K] 
    Capabilities: [44] Power Management version 2 
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+) 
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME- 
    Kernel driver in use: ohci_hcd 
 
0000:00:02.1 USB controller: NVIDIA Corporation MCP55 USB Controller (rev a2) (prog-if 20 [EHCI]) 
    Subsystem: Hewlett-Packard Company Device 12fe 
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx- 
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
    Latency: 0 (750ns min, 250ns max) 
    Interrupt: pin B routed to IRQ 21 
    Region 0: Memory at fa24a000 (32-bit, non-prefetchable) [size=256] 
    Capabilities: [44] Debug port: BAR=1 offset=0098 
    Capabilities: [80] Power Management version 2 
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+) 
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME- 
    Kernel driver in use: ehci-pci 
 
0000:00:04.0 IDE interface: NVIDIA Corporation MCP55 IDE (rev a1) (prog-if 8a [Master SecP PriP]) 
    Subsystem: Hewlett-Packard Company Device 12fe 
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx- 
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
    Latency: 0 (750ns min, 250ns max) 
    Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8] 
    Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1] 
    Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8] 
    Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1] 
    Region 4: I/O ports at 4080 [size=16] 
    Capabilities: [44] Power Management version 2 
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-) 
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME- 
    Kernel driver in use: pata_amd 
 
0000:00:05.0 IDE interface: NVIDIA Corporation MCP55 SATA Controller (rev a3) (prog-if 85 [Master SecO PriO]) 
    Subsystem: Hewlett-Packard Company Device 12fe 
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+ 
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
    Latency: 0 (750ns min, 250ns max) 
    Interrupt: pin A routed to IRQ 67 
    Region 0: I/O ports at 40c0 [size=8] 
    Region 1: I/O ports at 4100 [size=4] 
    Region 2: I/O ports at 40c8 [size=8] 
    Region 3: I/O ports at 4104 [size=4] 
    Region 4: I/O ports at 4090 [size=16] 
    Region 5: Memory at fa245000 (32-bit, non-prefetchable) [size=4K] 
    Capabilities: [44] Power Management version 2 
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-) 
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME- 
    Capabilities: [b0] MSI: Enable+ Count=1/4 Maskable- 64bit+ 
        Address: 00000000fee00000  Data: 40b6 
    Capabilities: [cc] HyperTransport: MSI Mapping Enable- Fixed+ 
    Kernel driver in use: sata_nv 
 
0000:00:05.1 IDE interface: NVIDIA Corporation MCP55 SATA Controller (rev a3) (prog-if 85 [Master SecO PriO]) 
    Subsystem: Hewlett-Packard Company Device 12fe 
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+ 
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
    Latency: 0 (750ns min, 250ns max) 
    Interrupt: pin B routed to IRQ 68 
    Region 0: I/O ports at 40d0 [size=8] 
    Region 1: I/O ports at 4108 [size=4] 
    Region 2: I/O ports at 40d8 [size=8] 
    Region 3: I/O ports at 410c [size=4] 
    Region 4: I/O ports at 40a0 [size=16] 
    Region 5: Memory at fa246000 (32-bit, non-prefetchable) [size=4K] 
    Capabilities: [44] Power Management version 2 
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-) 
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME- 
    Capabilities: [b0] MSI: Enable+ Count=1/4 Maskable- 64bit+ 
        Address: 00000000fee00000  Data: 40d1 
    Capabilities: [cc] HyperTransport: MSI Mapping Enable- Fixed+ 
    Kernel driver in use: sata_nv 
 
0000:00:05.2 IDE interface: NVIDIA Corporation MCP55 SATA Controller (rev a3) (prog-if 85 [Master SecO PriO]) 
    Subsystem: Hewlett-Packard Company Device 12fe 
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+ 
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
    Latency: 0 (750ns min, 250ns max) 
    Interrupt: pin C routed to IRQ 69 
    Region 0: I/O ports at 40e0 [size=8] 
    Region 1: I/O ports at 4110 [size=4] 
    Region 2: I/O ports at 40e8 [size=8] 
    Region 3: I/O ports at 4114 [size=4] 
    Region 4: I/O ports at 40b0 [size=16] 
    Region 5: Memory at fa247000 (32-bit, non-prefetchable) [size=4K] 
    Capabilities: [44] Power Management version 2 
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-) 
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME- 
    Capabilities: [b0] MSI: Enable+ Count=1/4 Maskable- 64bit+ 
        Address: 00000000fee00000  Data: 4022 
    Capabilities: [cc] HyperTransport: MSI Mapping Enable- Fixed+ 
    Kernel driver in use: sata_nv 
 
0000:00:06.0 PCI bridge: NVIDIA Corporation MCP55 PCI bridge (rev a2) (prog-if 01 [Subtractive decode]) 
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx- 
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
    Latency: 0 
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=32 
    I/O behind bridge: 0000f000-00000fff 
    Memory behind bridge: fa100000-fa1fffff 
    Prefetchable memory behind bridge: fff00000-000fffff 
    Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- <SERR- <PERR- 
    BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B- 
        PriDiscTmr- SecDiscTmr+ DiscTmrStat- DiscTmrSERREn+ 
    Capabilities: [b8] Subsystem: NVIDIA Corporation Device cb84 
    Capabilities: [8c] HyperTransport: MSI Mapping Enable- Fixed- 
        Mapping Address Base: 00000000fee00000 
 
0000:00:06.1 Audio device: NVIDIA Corporation MCP55 High Definition Audio (rev a2) 
    Subsystem: Hewlett-Packard Company Device 12fe 
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+ 
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
    Latency: 0 (500ns min, 1250ns max) 
    Interrupt: pin B routed to IRQ 71 
    Region 0: Memory at fa240000 (32-bit, non-prefetchable) [size=16K] 
    Capabilities: [44] Power Management version 2 
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold+) 
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME- 
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable+ 64bit+ 
        Address: 00000000fee00000  Data: 4092 
        Masking: 00000000  Pending: 00000000 
    Capabilities: [6c] HyperTransport: MSI Mapping Enable- Fixed+ 
    Kernel driver in use: snd_hda_intel 
 
0000:00:08.0 Bridge: NVIDIA Corporation MCP55 Ethernet (rev a3) 
    Subsystem: Hewlett-Packard Company Device 12fe 
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+ 
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
    Latency: 0 (250ns min, 5000ns max) 
    Interrupt: pin A routed to IRQ 72 
    Region 0: Memory at fa248000 (32-bit, non-prefetchable) [size=4K] 
    Region 1: I/O ports at 40f0 [size=8] 
    Region 2: Memory at fa24a100 (32-bit, non-prefetchable) [size=256] 
    Region 3: Memory at fa24a300 (32-bit, non-prefetchable) [size=16] 
    Capabilities: [44] Power Management version 2 
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+) 
        Status: D0 NoSoftRst- PME-Enable+ DSel=0 DScale=0 PME- 
    Capabilities: [70] MSI-X: Enable- Count=8 Masked- 
        Vector table: BAR=2 offset=00000000 
        PBA: BAR=3 offset=00000000 
    Capabilities: [50] MSI: Enable+ Count=1/8 Maskable+ 64bit+ 
        Address: 00000000fee01000  Data: 40a6 
        Masking: 000000fe  Pending: 00000000 
    Capabilities: [6c] HyperTransport: MSI Mapping Enable- Fixed+ 
    Kernel driver in use: forcedeth 
 
0000:00:09.0 Bridge: NVIDIA Corporation MCP55 Ethernet (rev a3) 
    Subsystem: Hewlett-Packard Company Device 12fe 
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+ 
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
    Latency: 0 (250ns min, 5000ns max) 
    Interrupt: pin A routed to IRQ 73 
    Region 0: Memory at fa249000 (32-bit, non-prefetchable) [size=4K] 
    Region 1: I/O ports at 40f8 [size=8] 
    Region 2: Memory at fa24a200 (32-bit, non-prefetchable) [size=256] 
    Region 3: Memory at fa24a310 (32-bit, non-prefetchable) [size=16] 
    Capabilities: [44] Power Management version 2 
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+) 
        Status: D0 NoSoftRst- PME-Enable+ DSel=0 DScale=0 PME- 
    Capabilities: [70] MSI-X: Enable- Count=8 Masked- 
        Vector table: BAR=2 offset=00000000 
        PBA: BAR=3 offset=00000000 
    Capabilities: [50] MSI: Enable+ Count=1/8 Maskable+ 64bit+ 
        Address: 00000000fee00000  Data: 40b2 
        Masking: 000000fe  Pending: 00000000 
    Capabilities: [6c] HyperTransport: MSI Mapping Enable- Fixed+ 
    Kernel driver in use: forcedeth 
 
0000:00:0d.0 PCI bridge: NVIDIA Corporation MCP55 PCI Express bridge (rev a3) (prog-if 00 [Normal decode]) 
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+ 
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
    Latency: 0, Cache Line Size: 64 bytes 
    Bus: primary=00, secondary=2b, subordinate=2d, sec-latency=0 
    I/O behind bridge: 0000f000-00000fff 
    Memory behind bridge: fa000000-fa0fffff 
    Prefetchable memory behind bridge: 00000000fff00000-00000000000fffff 
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR- 
    BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B- 
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn- 
    Capabilities: [40] Subsystem: NVIDIA Corporation Device 0000 
    Capabilities: [48] Power Management version 2 
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+) 
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME- 
    Capabilities: [50] MSI: Enable+ Count=1/2 Maskable- 64bit+ 
        Address: 00000000fee00000  Data: 4071 
    Capabilities: [60] HyperTransport: MSI Mapping Enable- Fixed- 
        Mapping Address Base: 00000000fee00000 
    Capabilities: [80] Express (v1) Root Port (Slot+), MSI 00 
        DevCap:    MaxPayload 256 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us 
            ExtTag- RBE+ FLReset- 
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported- 
            RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+ 
            MaxPayload 128 bytes, MaxReadReq 512 bytes 
        DevSta:    CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend- 
        LnkCap:    Port #2, Speed 2.5GT/s, Width x4, ASPM L0s L1, Latency L0 <512ns, L1 <4us 
            ClockPM- Surprise- LLActRep+ BwNot- 
        LnkCtl:    ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk- 
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt- 
        LnkSta:    Speed 2.5GT/s, Width x4, TrErr- Train- SlotClk+ DLActive+ BWMgmt- ABWMgmt- 
        SltCap:    AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug- Surprise- 
            Slot #0, PowerLimit 0.000W; Interlock- NoCompl- 
        SltCtl:    Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg- 
            Control: AttnInd Off, PwrInd On, Power- Interlock- 
        SltSta:    Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet+ Interlock- 
            Changed: MRL- PresDet+ LinkState+ 
        RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal+ PMEIntEna- CRSVisible- 
        RootCap: CRSVisible- 
        RootSta: PME ReqID 0000, PMEStatus- PMEPending- 
    Capabilities: [100 v1] Virtual Channel 
        Caps:    LPEVC=0 RefClk=100ns PATEntryBits=1 
        Arb:    Fixed- WRR32- WRR64- WRR128- 
        Ctrl:    ArbSelect=WRR32 
        Status:    InProgress- 
        VC0:    Caps:    PATOffset=00 MaxTimeSlots=1 RejSnoopTrans- 
            Arb:    Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256- 
            Ctrl:    Enable+ ID=0 ArbSelect=Fixed TC/VC=01 
            Status:    NegoPending- InProgress- 
    Capabilities: [160 v1] Advanced Error Reporting 
        UESta:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol- 
        UEMsk:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol- 
        UESvrt:    DLP+ SDES- TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt+ RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol- 
        CESta:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr- 
        CEMsk:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+ 
        AERCap:    First Error Pointer: 00, GenCap+ CGenEn- ChkCap+ ChkEn- 
    Kernel driver in use: pcieport 
 
0000:00:0f.0 PCI bridge: NVIDIA Corporation MCP55 PCI Express bridge (rev a3) (prog-if 00 [Normal decode]) 
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+ 
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
    Latency: 0, Cache Line Size: 64 bytes 
    Bus: primary=00, secondary=18, subordinate=18, sec-latency=0 
    I/O behind bridge: 00003000-00003fff 
    Memory behind bridge: f8000000-f9ffffff 
    Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff 
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR- 
    BridgeCtl: Parity- SERR+ NoISA- VGA+ MAbort- >Reset- FastB2B- 
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn- 
    Capabilities: [40] Subsystem: NVIDIA Corporation Device 0000 
    Capabilities: [48] Power Management version 2 
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+) 
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME- 
    Capabilities: [50] MSI: Enable+ Count=1/2 Maskable- 64bit+ 
        Address: 00000000fee00000  Data: 4081 
    Capabilities: [60] HyperTransport: MSI Mapping Enable- Fixed- 
        Mapping Address Base: 00000000fee00000 
    Capabilities: [80] Express (v1) Root Port (Slot+), MSI 00 
        DevCap:    MaxPayload 256 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us 
            ExtTag- RBE+ FLReset- 
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported- 
            RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+ 
            MaxPayload 128 bytes, MaxReadReq 512 bytes 
        DevSta:    CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend- 
        LnkCap:    Port #0, Speed 2.5GT/s, Width x16, ASPM L0s L1, Latency L0 <512ns, L1 <4us 
            ClockPM- Surprise- LLActRep+ BwNot- 
        LnkCtl:    ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk- 
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt- 
        LnkSta:    Speed 2.5GT/s, Width x16, TrErr- Train- SlotClk+ DLActive+ BWMgmt- ABWMgmt- 
        SltCap:    AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug- Surprise- 
            Slot #0, PowerLimit 0.000W; Interlock- NoCompl- 
        SltCtl:    Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg- 
            Control: AttnInd Off, PwrInd On, Power- Interlock- 
        SltSta:    Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet+ Interlock- 
            Changed: MRL- PresDet+ LinkState+ 
        RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal+ PMEIntEna- CRSVisible- 
        RootCap: CRSVisible- 
        RootSta: PME ReqID 0000, PMEStatus- PMEPending- 
    Capabilities: [100 v1] Virtual Channel 
        Caps:    LPEVC=0 RefClk=100ns PATEntryBits=1 
        Arb:    Fixed- WRR32- WRR64- WRR128- 
        Ctrl:    ArbSelect=WRR32 
        Status:    InProgress- 
        VC0:    Caps:    PATOffset=00 MaxTimeSlots=1 RejSnoopTrans- 
            Arb:    Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256- 
            Ctrl:    Enable+ ID=0 ArbSelect=Fixed TC/VC=01 
            Status:    NegoPending- InProgress- 
    Capabilities: [160 v1] Advanced Error Reporting 
        UESta:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol- 
        UEMsk:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol- 
        UESvrt:    DLP+ SDES- TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt+ RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol- 
        CESta:    RxErr- BadTLP- BadDLLP- Rollover- Timeout+ NonFatalErr- 
        CEMsk:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+ 
        AERCap:    First Error Pointer: 00, GenCap+ CGenEn- ChkCap+ ChkEn- 
    Kernel driver in use: pcieport 
 
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration 
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx- 
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
    Capabilities: [80] HyperTransport: Host or Secondary Interface 
        Command: WarmRst+ DblEnd- DevNum=0 ChainSide- HostHide+ Slave- <EOCErr- DUL- 
        Link Control: CFlE- CST- CFE- <LkFail- Init+ EOC- TXO- <CRCErr=0 IsocEn- LSEn+ ExtCTL- 64b- 
        Link Config: MLWI=16bit DwFcIn- MLWO=16bit DwFcOut- LWI=16bit DwFcInEn- LWO=16bit DwFcOutEn- 
        Revision ID: 3.00 
        Link Frequency: 1.6GHz 
        Link Error: <Prot- <Ovfl- <EOC- CTLTm- 
        Link Frequency Capability: 200MHz+ 300MHz- 400MHz+ 500MHz- 600MHz+ 800MHz+ 1.0GHz+ 1.2GHz+ 1.4GHz- 1.6GHz- Vend- 
        Feature Capability: IsocFC+ LDTSTOP+ CRCTM- ECTLT- 64bA+ UIDRD- ExtRS- UCnfE- 
    Capabilities: [a0] HyperTransport: Host or Secondary Interface 
        Command: WarmRst+ DblEnd- DevNum=0 ChainSide- HostHide+ Slave- <EOCErr- DUL- 
        Link Control: CFlE- CST- CFE- <LkFail- Init+ EOC- TXO- <CRCErr=0 IsocEn- LSEn+ ExtCTL- 64b- 
        Link Config: MLWI=16bit DwFcIn- MLWO=16bit DwFcOut- LWI=16bit DwFcInEn- LWO=16bit DwFcOutEn- 
        Revision ID: 3.00 
        Link Frequency: 1.6GHz 
        Link Error: <Prot- <Ovfl- <EOC- CTLTm- 
        Link Frequency Capability: 200MHz+ 300MHz- 400MHz+ 500MHz- 600MHz+ 800MHz+ 1.0GHz+ 1.2GHz+ 1.4GHz- 1.6GHz- Vend- 
        Feature Capability: IsocFC+ LDTSTOP+ CRCTM- ECTLT- 64bA+ UIDRD- ExtRS- UCnfE- 
    Capabilities: [c0] HyperTransport: Host or Secondary Interface 
        Command: WarmRst+ DblEnd- DevNum=0 ChainSide- HostHide+ Slave- <EOCErr- DUL- 
        Link Control: CFlE- CST- CFE- <LkFail- Init+ EOC- TXO- <CRCErr=0 IsocEn- LSEn+ ExtCTL- 64b- 
        Link Config: MLWI=16bit DwFcIn- MLWO=16bit DwFcOut- LWI=16bit DwFcInEn- LWO=16bit DwFcOutEn- 
        Revision ID: 3.00 
        Link Frequency: 1.0GHz 
        Link Error: <Prot- <Ovfl- <EOC- CTLTm- 
        Link Frequency Capability: 200MHz+ 300MHz- 400MHz+ 500MHz- 600MHz+ 800MHz+ 1.0GHz+ 1.2GHz+ 1.4GHz- 1.6GHz- Vend- 
        Feature Capability: IsocFC+ LDTSTOP+ CRCTM- ECTLT- 64bA+ UIDRD- ExtRS- UCnfE- 
 
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map 
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx- 
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
 
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller 
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx- 
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
    Kernel driver in use: amd64_edac 
 
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control 
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx- 
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
    Capabilities: [f0] Secure device <?> 
 
0000:00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control 
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx- 
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
 
0000:00:19.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration 
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx- 
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
    Capabilities: [80] HyperTransport: Host or Secondary Interface 
        Command: WarmRst+ DblEnd- DevNum=0 ChainSide- HostHide+ Slave- <EOCErr- DUL- 
        Link Control: CFlE- CST- CFE- <LkFail- Init+ EOC- TXO- <CRCErr=0 IsocEn- LSEn+ ExtCTL- 64b- 
        Link Config: MLWI=16bit DwFcIn- MLWO=16bit DwFcOut- LWI=16bit DwFcInEn- LWO=16bit DwFcOutEn- 
        Revision ID: 3.00 
        Link Frequency: 1.0GHz 
        Link Error: <Prot- <Ovfl- <EOC- CTLTm- 
        Link Frequency Capability: 200MHz+ 300MHz- 400MHz+ 500MHz- 600MHz+ 800MHz+ 1.0GHz+ 1.2GHz+ 1.4GHz- 1.6GHz- Vend- 
        Feature Capability: IsocFC+ LDTSTOP+ CRCTM- ECTLT- 64bA+ UIDRD- ExtRS- UCnfE- 
    Capabilities: [a0] HyperTransport: Host or Secondary Interface 
        Command: WarmRst+ DblEnd- DevNum=0 ChainSide- HostHide+ Slave- <EOCErr- DUL- 
        Link Control: CFlE- CST- CFE- <LkFail- Init+ EOC- TXO- <CRCErr=0 IsocEn- LSEn+ ExtCTL- 64b- 
        Link Config: MLWI=16bit DwFcIn- MLWO=16bit DwFcOut- LWI=16bit DwFcInEn- LWO=16bit DwFcOutEn- 
        Revision ID: 3.00 
        Link Frequency: 1.6GHz 
        Link Error: <Prot- <Ovfl- <EOC- CTLTm- 
        Link Frequency Capability: 200MHz+ 300MHz- 400MHz+ 500MHz- 600MHz+ 800MHz+ 1.0GHz+ 1.2GHz+ 1.4GHz- 1.6GHz- Vend- 
        Feature Capability: IsocFC+ LDTSTOP+ CRCTM- ECTLT- 64bA+ UIDRD- ExtRS- UCnfE- 
    Capabilities: [c0] HyperTransport: Host or Secondary Interface 
        Command: WarmRst+ DblEnd- DevNum=0 ChainSide- HostHide+ Slave- <EOCErr- DUL- 
        Link Control: CFlE- CST- CFE- <LkFail- Init+ EOC- TXO- <CRCErr=0 IsocEn- LSEn+ ExtCTL- 64b- 
        Link Config: MLWI=16bit DwFcIn- MLWO=16bit DwFcOut- LWI=16bit DwFcInEn- LWO=16bit DwFcOutEn- 
        Revision ID: 3.00 
        Link Frequency: 1.6GHz 
        Link Error: <Prot- <Ovfl- <EOC- CTLTm- 
        Link Frequency Capability: 200MHz+ 300MHz- 400MHz+ 500MHz- 600MHz+ 800MHz+ 1.0GHz+ 1.2GHz+ 1.4GHz- 1.6GHz- Vend- 
        Feature Capability: IsocFC+ LDTSTOP+ CRCTM- ECTLT- 64bA+ UIDRD- ExtRS- UCnfE- 
 
0000:00:19.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map 
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx- 
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
 
0000:00:19.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller 
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx- 
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
    Kernel driver in use: amd64_edac 
 
0000:00:19.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control 
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx- 
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
    Capabilities: [f0] Secure device <?> 
 
0000:00:19.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control 
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx- 
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
 
0000:01:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx] (prog-if 10 [OHCI]) 
    Subsystem: Hewlett-Packard Company Device 12fe 
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx- 
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
    Latency: 32 (500ns min, 1000ns max), Cache Line Size: 64 bytes 
    Interrupt: pin A routed to IRQ 16 
    Region 0: Memory at fa104000 (32-bit, non-prefetchable) [size=2K] 
    Region 1: Memory at fa100000 (32-bit, non-prefetchable) [size=16K] 
    Capabilities: [44] Power Management version 2 
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-) 
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME+ 
    Kernel driver in use: firewire_ohci 
 
0000:18:00.0 VGA compatible controller: NVIDIA Corporation G71GL [Quadro FX 3500] (rev a1) (prog-if 00 [VGA controller]) 
    Subsystem: NVIDIA Corporation Device 032b 
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx- 
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
    Latency: 0, Cache Line Size: 64 bytes 
    Interrupt: pin A routed to IRQ 22 
    Region 0: Memory at f8000000 (32-bit, non-prefetchable) [size=16M] 
    Region 1: Memory at e0000000 (64-bit, prefetchable) [size=256M] 
    Region 3: Memory at f9000000 (64-bit, non-prefetchable) [size=16M] 
    Region 5: I/O ports at 3000 [size=128] 
    Expansion ROM at <unassigned> [disabled] 
    Capabilities: [60] Power Management version 2 
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-) 
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME- 
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+ 
        Address: 0000000000000000  Data: 0000 
    Capabilities: [78] Express (v1) Endpoint, MSI 00 
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <1us, L1 <4us 
            ExtTag- AttnBtn- AttnInd- PwrInd- RBE- FLReset- 
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal+ Unsupported- 
            RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+ 
            MaxPayload 128 bytes, MaxReadReq 512 bytes 
        DevSta:    CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend- 
        LnkCap:    Port #0, Speed 2.5GT/s, Width x16, ASPM L0s L1, Latency L0 <1us, L1 <4us 
            ClockPM- Surprise- LLActRep- BwNot- 
        LnkCtl:    ASPM Disabled; RCB 128 bytes Disabled- Retrain- CommClk- 
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt- 
        LnkSta:    Speed 2.5GT/s, Width x16, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt- 
    Capabilities: [100 v1] Virtual Channel 
        Caps:    LPEVC=0 RefClk=100ns PATEntryBits=1 
        Arb:    Fixed- WRR32- WRR64- WRR128- 
        Ctrl:    ArbSelect=Fixed 
        Status:    InProgress- 
        VC0:    Caps:    PATOffset=00 MaxTimeSlots=1 RejSnoopTrans- 
            Arb:    Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256- 
            Ctrl:    Enable+ ID=0 ArbSelect=Fixed TC/VC=01 
            Status:    NegoPending- InProgress- 
    Capabilities: [128 v1] Power Budgeting <?> 
    Kernel driver in use: nouveau 
 
0000:2b:00.0 PCI bridge: NEC Corporation uPD720400 PCI Express - PCI/PCI-X Bridge (rev 06) (prog-if 00 [Normal decode]) 
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx- 
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
    Latency: 0, Cache Line Size: 64 bytes 
    Bus: primary=2b, secondary=2c, subordinate=2c, sec-latency=32 
    I/O behind bridge: 0000f000-00000fff 
    Memory behind bridge: fff00000-000fffff 
    Prefetchable memory behind bridge: 00000000fff00000-00000000000fffff 
    Secondary status: 66MHz+ FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort+ <SERR- <PERR- 
    BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B- 
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn- 
    Capabilities: [40] Express (v1) PCI/PCI-X Bridge, MSI 00 
        DevCap:    MaxPayload 256 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us 
            ExtTag- AttnBtn- AttnInd- PwrInd- RBE- FLReset- 
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal+ Unsupported- 
            RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop- BrConfRtry- 
            MaxPayload 128 bytes, MaxReadReq 512 bytes 
        DevSta:    CorrErr- UncorrErr+ FatalErr- UnsuppReq+ AuxPwr- TransPend- 
        LnkCap:    Port #0, Speed 2.5GT/s, Width x8, ASPM L0s L1, Latency L0 <4us, L1 <16us 
            ClockPM- Surprise- LLActRep- BwNot- 
        LnkCtl:    ASPM Disabled; Disabled- Retrain- CommClk- 
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt- 
        LnkSta:    Speed 2.5GT/s, Width x4, TrErr- Train- SlotClk- DLActive- BWMgmt- ABWMgmt- 
    Capabilities: [54] PCI-X bridge device 
        Secondary Status: 64bit+ 133MHz+ SCD- USC- SCO- SRD- Freq=133MHz 
        Status: Dev=2b:00.0 64bit- 133MHz- SCD- USC- SCO- SRD- 
        Upstream: Capacity=32 CommitmentLimit=32 
        Downstream: Capacity=16 CommitmentLimit=16 
    Capabilities: [64] Power Management version 2 
        Flags: PMEClk- DSI- D1+ D2- AuxCurrent=55mA PME(D0+,D1+,D2-,D3hot+,D3cold+) 
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME- 
        Bridge: PM- B3+ 
    Capabilities: [100 v1] Advanced Error Reporting 
        UESta:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq+ ACSViol- 
        UEMsk:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol- 
        UESvrt:    DLP+ SDES- TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol- 
        CESta:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr- 
        CEMsk:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr- 
        AERCap:    First Error Pointer: 14, GenCap+ CGenEn- ChkCap+ ChkEn- 
 
0000:2b:00.1 PCI bridge: NEC Corporation uPD720400 PCI Express - PCI/PCI-X Bridge (rev 06) (prog-if 00 [Normal decode]) 
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx- 
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
    Latency: 0, Cache Line Size: 64 bytes 
    Region 0: Memory at fa000000 (64-bit, non-prefetchable) [size=128] 
    Bus: primary=2b, secondary=2d, subordinate=2d, sec-latency=32 
    I/O behind bridge: 0000f000-00000fff 
    Memory behind bridge: fff00000-000fffff 
    Prefetchable memory behind bridge: 00000000fff00000-00000000000fffff 
    Secondary status: 66MHz+ FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort+ <SERR- <PERR- 
    BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B- 
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn- 
    Capabilities: [40] Express (v1) PCI/PCI-X Bridge, MSI 00 
        DevCap:    MaxPayload 256 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us 
            ExtTag- AttnBtn- AttnInd- PwrInd- RBE- FLReset- 
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal+ Unsupported- 
            RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop- BrConfRtry- 
            MaxPayload 128 bytes, MaxReadReq 512 bytes 
        DevSta:    CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend- 
        LnkCap:    Port #0, Speed 2.5GT/s, Width x8, ASPM L0s L1, Latency L0 <4us, L1 <16us 
            ClockPM- Surprise- LLActRep- BwNot- 
        LnkCtl:    ASPM Disabled; Disabled- Retrain- CommClk- 
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt- 
        LnkSta:    Speed 2.5GT/s, Width x4, TrErr- Train- SlotClk- DLActive- BWMgmt- ABWMgmt- 
    Capabilities: [54] PCI-X bridge device 
        Secondary Status: 64bit+ 133MHz+ SCD- USC- SCO- SRD- Freq=conv 
        Status: Dev=2b:00.1 64bit- 133MHz- SCD- USC- SCO- SRD- 
        Upstream: Capacity=32 CommitmentLimit=32 
        Downstream: Capacity=16 CommitmentLimit=16 
    Capabilities: [64] Power Management version 2 
        Flags: PMEClk- DSI- D1+ D2- AuxCurrent=55mA PME(D0+,D1+,D2-,D3hot+,D3cold+) 
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME- 
        Bridge: PM- B3+ 
    Capabilities: [6c] MSI: Enable- Count=1/1 Maskable- 64bit+ 
        Address: 0000000000000000  Data: 0000 
    Capabilities: [7c] Hot-plug capable 
    Capabilities: [100 v1] Advanced Error Reporting 
        UESta:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol- 
        UEMsk:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol- 
        UESvrt:    DLP+ SDES- TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol- 
        CESta:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr- 
        CEMsk:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr- 
        AERCap:    First Error Pointer: 00, GenCap+ CGenEn- ChkCap+ ChkEn- 
 
0001:40:00.0 RAM memory: NVIDIA Corporation MCP55 Memory Controller (rev a2) 
    Subsystem: Hewlett-Packard Company Device 12fe 
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx- 
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
    Latency: 0 
    Capabilities: [44] HyperTransport: Slave or Primary Interface 
        Command: BaseUnitID=0 UnitCnt=15 MastHost- DefDir- DUL- 
        Link Control 0: CFlE+ CST- CFE- <LkFail- Init+ EOC- TXO- <CRCErr=0 IsocEn- LSEn- ExtCTL- 64b- 
        Link Config 0: MLWI=16bit DwFcIn- MLWO=16bit DwFcOut- LWI=16bit DwFcInEn- LWO=16bit DwFcOutEn- 
        Link Control 1: CFlE- CST- CFE- <LkFail+ Init- EOC+ TXO+ <CRCErr=0 IsocEn- LSEn- ExtCTL- 64b- 
        Link Config 1: MLWI=8bit DwFcIn- MLWO=8bit DwFcOut- LWI=8bit DwFcInEn- LWO=8bit DwFcOutEn- 
        Revision ID: 1.03 
        Link Frequency 0: 1.0GHz 
        Link Error 0: <Prot- <Ovfl- <EOC- CTLTm- 
        Link Frequency Capability 0: 200MHz+ 300MHz+ 400MHz+ 500MHz+ 600MHz+ 800MHz+ 1.0GHz+ 1.2GHz- 1.4GHz- 1.6GHz- Vend- 
        Feature Capability: IsocFC+ LDTSTOP+ CRCTM- ECTLT- 64bA- UIDRD- 
        Link Frequency 1: 200MHz 
        Link Error 1: <Prot- <Ovfl- <EOC- CTLTm- 
        Link Frequency Capability 1: 200MHz- 300MHz- 400MHz- 500MHz- 600MHz- 800MHz- 1.0GHz- 1.2GHz- 1.4GHz- 1.6GHz- Vend- 
        Error Handling: PFlE+ OFlE+ PFE- OFE- EOCFE- RFE- CRCFE- SERRFE- CF- RE- PNFE- ONFE- EOCNFE- RNFE- CRCNFE- SERRNFE- 
        Prefetchable memory behind bridge Upper: 00-00 
        Bus Number: 00 
    Capabilities: [dc] HyperTransport: MSI Mapping Enable+ Fixed- 
        Mapping Address Base: 00000000fee00000 
 
0001:40:01.0 RAM memory: NVIDIA Corporation MCP55 LPC Bridge (rev a3) 
    Subsystem: Hewlett-Packard Company Device 12fe 
    Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx- 
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
    Latency: 0 
    Region 1: Memory at fa400000 (32-bit, non-prefetchable) [size=4K] 
 
0001:40:01.1 SMBus: NVIDIA Corporation MCP55 SMBus (rev a3) 
    Subsystem: Hewlett-Packard Company Device 12fe 
    Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx- 
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
    Interrupt: pin A routed to IRQ 255 
    Region 4: I/O ports at 2000 [size=64] 
    Region 5: I/O ports at 2040 [size=64] 
    Capabilities: [44] Power Management version 2 
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold+) 
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME- 
    Kernel driver in use: nForce2_smbus 
 
0001:40:0d.0 PCI bridge: NVIDIA Corporation MCP55 PCI Express bridge (rev a3) (prog-if 00 [Normal decode]) 
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+ 
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
    Latency: 0, Cache Line Size: 64 bytes 
    Bus: primary=40, secondary=6b, subordinate=6b, sec-latency=0 
    I/O behind bridge: 00001000-00001fff 
    Memory behind bridge: fa300000-fa3fffff 
    Prefetchable memory behind bridge: 00000000fff00000-00000000000fffff 
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR- 
    BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B- 
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn- 
    Capabilities: [40] Subsystem: NVIDIA Corporation Device 0000 
    Capabilities: [48] Power Management version 2 
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+) 
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME- 
    Capabilities: [50] MSI: Enable+ Count=1/2 Maskable- 64bit+ 
        Address: 00000000fee00000  Data: 4091 
    Capabilities: [60] HyperTransport: MSI Mapping Enable- Fixed- 
        Mapping Address Base: 00000000fee00000 
    Capabilities: [80] Express (v1) Root Port (Slot+), MSI 00 
        DevCap:    MaxPayload 256 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us 
            ExtTag- RBE+ FLReset- 
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported- 
            RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+ 
            MaxPayload 128 bytes, MaxReadReq 512 bytes 
        DevSta:    CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend- 
        LnkCap:    Port #2, Speed 2.5GT/s, Width x4, ASPM L0s L1, Latency L0 <512ns, L1 <4us 
            ClockPM- Surprise- LLActRep+ BwNot- 
        LnkCtl:    ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk- 
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt- 
        LnkSta:    Speed 2.5GT/s, Width x4, TrErr- Train- SlotClk+ DLActive+ BWMgmt- ABWMgmt- 
        SltCap:    AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug- Surprise- 
            Slot #0, PowerLimit 0.000W; Interlock- NoCompl- 
        SltCtl:    Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg- 
            Control: AttnInd Off, PwrInd On, Power- Interlock- 
        SltSta:    Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet+ Interlock- 
            Changed: MRL- PresDet+ LinkState+ 
        RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal+ PMEIntEna- CRSVisible- 
        RootCap: CRSVisible- 
        RootSta: PME ReqID 0000, PMEStatus- PMEPending- 
    Capabilities: [100 v1] Virtual Channel 
        Caps:    LPEVC=0 RefClk=100ns PATEntryBits=1 
        Arb:    Fixed- WRR32- WRR64- WRR128- 
        Ctrl:    ArbSelect=WRR32 
        Status:    InProgress- 
        VC0:    Caps:    PATOffset=00 MaxTimeSlots=1 RejSnoopTrans- 
            Arb:    Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256- 
            Ctrl:    Enable+ ID=0 ArbSelect=Fixed TC/VC=01 
            Status:    NegoPending- InProgress- 
    Capabilities: [160 v1] Advanced Error Reporting 
        UESta:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol- 
        UEMsk:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol- 
        UESvrt:    DLP+ SDES- TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt+ RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol- 
        CESta:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr- 
        CEMsk:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+ 
        AERCap:    First Error Pointer: 00, GenCap+ CGenEn- ChkCap+ ChkEn- 
    Kernel driver in use: pcieport 
 
0001:6b:00.0 SCSI storage controller: LSI Logic / Symbios Logic SAS1068E PCI-Express Fusion-MPT SAS (rev 02) 
    Subsystem: Hewlett-Packard Company Device 12fe 
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+ 
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
    Latency: 0, Cache Line Size: 64 bytes 
    Interrupt: pin A routed to IRQ 70 
    Region 0: I/O ports at 1000 [size=256] 
    Region 1: Memory at fa310000 (64-bit, non-prefetchable) [size=16K] 
    Region 3: Memory at fa300000 (64-bit, non-prefetchable) [size=64K] 
    Capabilities: [50] Power Management version 2 
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-) 
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME- 
    Capabilities: [68] Express (v1) Endpoint, MSI 00 
        DevCap:    MaxPayload 4096 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us 
            ExtTag+ AttnBtn- AttnInd- PwrInd- RBE- FLReset- 
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal+ Unsupported- 
            RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+ 
            MaxPayload 128 bytes, MaxReadReq 512 bytes 
        DevSta:    CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend- 
        LnkCap:    Port #0, Speed 2.5GT/s, Width x8, ASPM L0s L1, Latency L0 <64ns, L1 <1us 
            ClockPM- Surprise- LLActRep- BwNot- 
        LnkCtl:    ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk- 
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt- 
        LnkSta:    Speed 2.5GT/s, Width x4, TrErr- Train- SlotClk- DLActive- BWMgmt- ABWMgmt- 
    Capabilities: [98] MSI: Enable+ Count=1/1 Maskable- 64bit+ 
        Address: 00000000fee04000  Data: 4082 
    Capabilities: [b0] MSI-X: Enable- Count=1 Masked- 
        Vector table: BAR=1 offset=00002000 
        PBA: BAR=1 offset=00003000 
    Capabilities: [100 v1] Advanced Error Reporting 
        UESta:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol- 
        UEMsk:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol- 
        UESvrt:    DLP+ SDES- TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol- 
        CESta:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr- 
        CEMsk:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr- 
        AERCap:    First Error Pointer: 00, GenCap+ CGenEn- ChkCap+ ChkEn- 
    Kernel driver in use: mptsas 


```

cat /proc/interrupt otuput.

```
            CPU0       CPU1       CPU2       CPU3       CPU4       CPU5       CPU6       CPU7        
   0:         45          0          0          0          0          0          0          0   IO-APIC-edge      timer 
   1:          3          0          0          0          0          0          0          0   IO-APIC-edge      i8042 
   7:          1          0          0          0          0          0          0          0   IO-APIC-edge     
   8:          1          0          0          0          0          0          0          0   IO-APIC-edge      rtc0 
   9:          0          0          0          0          0          0          0          0   IO-APIC-fasteoi   acpi 
  12:          5          0          0          0          0          0          0          0   IO-APIC-edge      i8042 
  14:          0          0          0          0          0          0          0          0   IO-APIC-edge      pata_amd 
  15:          0          0          0          0          0          0          0          0   IO-APIC-edge      pata_amd 
  16:          2          0          0          0          0          0          0          0   IO-APIC-fasteoi   firewire_ohci 
  21:       1398          0       1269          0       1555          0        977          0   IO-APIC-fasteoi   ehci_hcd:usb1 
  22:       2100          0       6911          0          0          0          0          0   IO-APIC-fasteoi   ohci_hcd:usb2, nouveau 
  67:      11638          0          0          0        486          0       1219          0   PCI-MSI-edge      sata_nv 
  68:          0          0          0          0          0          0          0          0   PCI-MSI-edge      sata_nv 
  69:          0          0          0          0          0          0          0          0   PCI-MSI-edge      sata_nv 
  70:          0         66          0          0          0          0          0          0   PCI-MSI-edge      ioc0 
  71:        324          0          0          0          0          0          0          0   PCI-MSI-edge      snd_hda_intel 
  72:        128          0          0          0          0          0        117          0   PCI-MSI-edge      eth0 
  73:          0          0          0          0          0          0          0          0   PCI-MSI-edge      eth1 
 NMI:          0          0          0          0          0          0          0          0   Non-maskable interrupts 
 LOC:       7461       3763       6621       3488       7273       3111       8092       2854   Local timer interrupts 
 SPU:          0          0          0          0          0          0          0          0   Spurious interrupts 
 PMI:          0          0          0          0          0          0          0          0   Performance monitoring interrupts 
 IWI:          0          0          0          0          0          0          0          0   IRQ work interrupts 
 RTR:          0          0          0          0          0          0          0          0   APIC ICR read retries 
 RES:      17796      12837      17127      11819      15543      17683      14362      12445   Rescheduling interrupts 
 CAL:        560       4877        536       2975        542       1113        485        916   Function call interrupts 
 TLB:        397        288        839        803        578        548        497        461   TLB shootdowns 
 TRM:          0          0          0          0          0          0          0          0   Thermal event interrupts 
 THR:          0          0          0          0          0          0          0          0   Threshold APIC interrupts 
 MCE:          0          0          0          0          0          0          0          0   Machine check exceptions 
 MCP:          2          2          2          2          2          2          2          2   Machine check polls 
 ERR:          1 
 MIS:          0
```

    Does anyone know if the sata_nv module and the mcp55 SATA controller have issues working with MSI interrupts or is there something wrong with my hardware or config? Or is there a problem with the sata_nv driver itself?

    Regards,
    Peter

---

### Post by Peter_Saisanas on 2013-08-15
Well i done some more investigations.

The sata_nv module by default has swncq enabled and msi interrupts disabled by default.

It seems that swncq mode seems to work perfectly well when running with io-apic interrupts but when switched over to enable the use of msi interrupts, swncq mode has all sorts of issues.

So in other words, to use msi interrupts, you must disable swncq and vice versa. Therefore i assume SATA hotplug is disabled if no ncq? Am i correct?

Could this possibly be an issue with the sata_nv driver or libata? Some sort of incompatibility with msi interrupts and swncq enabled together?

Either way for me, it isnt really a problem. In terms of performance, the hdd benches pactically the same in either mode... But i don't like the sounds of missing out on hotplug!

---

### Post by Yellow Pasque on 2013-08-15
I think nvidia chipsets struggle with MSI (the ALSA devs automatically disable MSI for the sound codec if they detect an nvidia chipset).

Some interesting links/ideas here: [http://plone.lucidsolutions.co.nz/linux/io/ssd-on-nvidia-sata-port-generates-error-eh-in-swncq-mode-and-failed-command-read-fpdma-queued](http://plone.lucidsolutions.co.nz/linux/io/ssd-on-nvidia-sata-port-generates-error-eh-in-swncq-mode-and-failed-command-read-fpdma-queued)

---

### Post by Peter_Saisanas on 2013-08-15
Thanks for the reply.

It seems to me regarding the HDA audio, it uses the snd-hda-intel driver and it seems to be working fine on my machine with MSI interrupts so far...

Also, using when the SATA controller is in MSI interrupt mode, it seems stable as well when running under heavy iozone benchmarks.

In general, it seems that msi interrupts seem to work fine for me.. just msi and swncq together cause problems.

I found something else i think that is quite interesting, one of the freebsd devs claims that when accessing one of the PCI BARS of the MCP55 SATA controller, it requires some sort of delay. I dont know exactly what is occuring, but i guess switching into swncq mode would require writing to one of the pci config space registers. Perhaps it needs some sort of delay after writing?

I'll attach the link below.

[http://mailing.freebsd.current.narkive.com/VfoZfXG9/mcp55-sata-solution-to-test](http://mailing.freebsd.current.narkive.com/VfoZfXG9/mcp55-sata-solution-to-test)

---

### Post by Yellow Pasque on 2013-08-16
Just because MSI is enabled on the storage controller, I don't think it's necessarily enabled for audio:
> HD-audio driver uses MSI as default (if available) since 2.6.33
kernel as MSI works better on some machines, and in general, it's
better for performance.  However, Nvidia controllers showed bad
regressions with MSI (especially in a combination with AMD chipset),
thus we disabled MSI for them.


---

### Post by Peter_Saisanas on 2013-08-16
Agreed,

But i have also specifically enabled MSI for the audio interface, i.e. the snd-hda-intel module.
I also enabled MSI for the SAS controller (which i will be using soon).
I have the output of the /proc/interrupts in the first msg in this thread.

Unfortunately, i cannot do it with the Quadro FX3500 (NV49) as it seems the nouveau driver doesnt support msi for this model yet.

---

