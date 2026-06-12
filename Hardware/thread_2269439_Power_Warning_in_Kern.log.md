---
title: "Power Warning in Kern.log"
date: 2015-03-15
forum: Hardware
---

### Post by marseille2 on 2015-03-15
Should I be worried? I keep getting this warning at every boot.

```
WARNING! power/level is deprecated; use power/control instead
```

Output of dmesg:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-46-lowlatency (buildd@orlo) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #79-Ubuntu SMP PREEMPT Tue Mar 10 20:23:54 UTC 2015 (Ubuntu 3.13.0-46.79-lowlatency 3.13.11-ckt15)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-46-lowlatency root=UUID=c5172c50-9eb0-4a08-bc83-9dfc55829d7b ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009fbff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009fc00-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000be33ffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000be340000-0x00000000be4e6fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000be4e7000-0x00000000be8d9fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000be8da000-0x00000000bee2cfff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bee2d000-0x00000000bee2dfff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bee2e000-0x00000000bf033fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bf034000-0x00000000bf451fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bf452000-0x00000000bf7f2fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bf7f3000-0x00000000bf7fffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec10000-0x00000000fec10fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec20000-0x00000000fec20fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed61000-0x00000000fed70fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed80000-0x00000000fed8ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fef00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100001000-0x000000023effffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: To Be Filled By O.E.M. To Be Filled By O.E.M./970 Extreme4, BIOS P2.60 11/11/2013
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x23f000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF write-through
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EAFFF uncachable
[    0.000000]   EB000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 base 0000BF800000 mask FFFFFF800000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 000000023f000000 aka 9200M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3064MB, range: 8MB, type UC
[    0.000000] total RAM covered: 3064M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 16M     num_reg: 3      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3064MB, range: 8MB, type UC
[    0.000000] e820: update [mem 0xbf800000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xbf800 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fd9a0-0x000fd9af] mapped at [ffff8800000fd9a0]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fd9000, 0x01fd9fff] PGTABLE
[    0.000000] BRK [0x01fda000, 0x01fdafff] PGTABLE
[    0.000000] BRK [0x01fdb000, 0x01fdbfff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x23ee00000-0x23effffff]
[    0.000000]  [mem 0x23ee00000-0x23effffff] page 2M
[    0.000000] BRK [0x01fdc000, 0x01fdcfff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x23c000000-0x23edfffff]
[    0.000000]  [mem 0x23c000000-0x23edfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x200000000-0x23bffffff]
[    0.000000]  [mem 0x200000000-0x23bffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0xbe33ffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
[    0.000000]  [mem 0x40000000-0x7fffffff] page 1G
[    0.000000]  [mem 0x80000000-0xbe1fffff] page 2M
[    0.000000]  [mem 0xbe200000-0xbe33ffff] page 4k
[    0.000000] init_memory_mapping: [mem 0xbee2d000-0xbee2dfff]
[    0.000000]  [mem 0xbee2d000-0xbee2dfff] page 4k
[    0.000000] BRK [0x01fdd000, 0x01fddfff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0xbf034000-0xbf451fff]
[    0.000000]  [mem 0xbf034000-0xbf1fffff] page 4k
[    0.000000]  [mem 0xbf200000-0xbf3fffff] page 2M
[    0.000000]  [mem 0xbf400000-0xbf451fff] page 4k
[    0.000000] BRK [0x01fde000, 0x01fdefff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0xbf7f3000-0xbf7fffff]
[    0.000000]  [mem 0xbf7f3000-0xbf7fffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100001000-0x1ffffffff]
[    0.000000]  [mem 0x100001000-0x1001fffff] page 4k
[    0.000000]  [mem 0x100200000-0x13fffffff] page 2M
[    0.000000]  [mem 0x140000000-0x1ffffffff] page 1G
[    0.000000] RAMDISK: [mem 0x35b64000-0x36da9fff]
[    0.000000] ACPI: RSDP 00000000000f0490 000024 (v02 ALASKA)
[    0.000000] ACPI: XSDT 00000000be8c7078 00006C (v01 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: FACP 00000000be8d0098 00010C (v05 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI BIOS Warning (bug): Optional FADT field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20131115/tbfadt-603)
[    0.000000] ACPI: DSDT 00000000be8c7178 008F1C (v02 ALASKA    A M I 00000000 INTL 20051117)
[    0.000000] ACPI: FACS 00000000be8d3080 000040
[    0.000000] ACPI: APIC 00000000be8d01a8 00009E (v03 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: FPDT 00000000be8d0248 000044 (v01 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: MCFG 00000000be8d0290 00003C (v01 ALASKA    A M I 01072009 MSFT 00010013)
[    0.000000] ACPI: AAFT 00000000be8d02d0 000062 (v01 ALASKA OEMAAFT  01072009 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000be8d0338 000038 (v01 ALASKA    A M I 01072009 AMI  00000005)
[    0.000000] ACPI: SSDT 00000000be8d0370 001714 (v01 AMD    POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: IVRS 00000000be8d1a88 0000D0 (v01  AMD     RD890S 00202031 AMD  00000000)
[    0.000000] ACPI: BGRT 00000000be8d1b58 000038 (v00 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000023effffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x23effffff]
[    0.000000]   NODE_DATA [mem 0x23eff5000-0x23eff9fff]
[    0.000000]  [ffffea0000000000-ffffea0008ffffff] PMD -> [ffff880236600000-ffff88023e5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x23effffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0xbe33ffff]
[    0.000000]   node   0: [mem 0xbee2d000-0xbee2dfff]
[    0.000000]   node   0: [mem 0xbf034000-0xbf451fff]
[    0.000000]   node   0: [mem 0xbf7f3000-0xbf7fffff]
[    0.000000]   node   0: [mem 0x100001000-0x23effffff]
[    0.000000] On node 0 totalpages: 2086665
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3998 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 12126 pages used for memmap
[    0.000000]   DMA32 zone: 776044 pages, LIFO batch:31
[    0.000000]   Normal zone: 20416 pages used for memmap
[    0.000000]   Normal zone: 1306623 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x10] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x11] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x12] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x13] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x14] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x15] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x16] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x17] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x09] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 9, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IOAPIC (id[0x0a] address[0xfec20000] gsi_base[24])
[    0.000000] IOAPIC[1]: apic_id 10, version 33, address 0xfec20000, GSI 24-55
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x43538210 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 72
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xbe340000-0xbe4e6fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbe4e7000-0xbe8d9fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbe8da000-0xbee2cfff]
[    0.000000] PM: Registered nosave memory: [mem 0xbee2e000-0xbf033fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbf452000-0xbf7f2fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbf800000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfec0ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec10000-0xfec10fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec11000-0xfec1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec20000-0xfec20fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec21000-0xfecfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfed00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed01000-0xfed60fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed61000-0xfed70fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed71000-0xfed7ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed80000-0xfed8ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed90000-0xfeefffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfef00000-0xffffffff]
[    0.000000] PM: Registered nosave memory: [mem 0x100000000-0x100000fff]
[    0.000000] e820: [mem 0xbf800000-0xfebfffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88023ec00000 s82816 r8192 d23680 u262144
[    0.000000] pcpu-alloc: s82816 r8192 d23680 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2054038
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-46-lowlatency root=UUID=c5172c50-9eb0-4a08-bc83-9dfc55829d7b ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ ab2c000000 size 32 MB
[    0.000000] Aperture beyond 4GB. Ignoring.
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ b4000000
[    0.000000] PM: Registered nosave memory: [mem 0xb4000000-0xb7ffffff]
[    0.000000] Memory: 8047760K/8346660K available (7400K kernel code, 1134K rwdata, 3408K rodata, 1324K init, 1444K bss, 298900K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Preemptible hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     Dump stacks of tasks blocking RCU-preempt GP.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-7.
[    0.000000] NR_IRQS:16640 nr_irqs:1288 16
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.001000] tsc: Detected 3991.309 MHz processor
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 7982.61 BogoMIPS (lpj=3991309)
[    0.000005] pid_max: default: 32768 minimum: 301
[    0.000029] Security Framework initialized
[    0.000045] AppArmor: AppArmor initialized
[    0.000046] Yama: becoming mindful.
[    0.000566] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.002357] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.003150] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.003160] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.003347] Initializing cgroup subsys memory
[    0.003353] Initializing cgroup subsys devices
[    0.003354] Initializing cgroup subsys freezer
[    0.003355] Initializing cgroup subsys blkio
[    0.003356] Initializing cgroup subsys perf_event
[    0.003358] Initializing cgroup subsys hugetlb
[    0.003375] tseg: 00bf800000
[    0.003377] CPU: Physical Processor ID: 0
[    0.003378] CPU: Processor Core ID: 0
[    0.003379] mce: CPU supports 7 MCE banks
[    0.003385] LVT offset 1 assigned for vector 0xf9
[    0.003390] Last level iTLB entries: 4KB 512, 2MB 1024, 4MB 512
[    0.003390] Last level dTLB entries: 4KB 1024, 2MB 1024, 4MB 512
[    0.003390] tlb_flushall_shift: 5
[    0.003458] Freeing SMP alternatives memory: 24K (ffffffff81e68000 - ffffffff81e6e000)
[    0.004027] ACPI: Core revision 20131115
[    0.006239] ACPI: All ACPI Tables successfully acquired
[    0.018113] ftrace: allocating 28565 entries in 112 pages
[    0.104813] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.114833] smpboot: CPU0: AMD FX(tm)-8350 Eight-Core Processor (fam: 15, model: 02, stepping: 00)
[    0.216269] Performance Events: Fam15h core perfctr, AMD PMU driver.
[    0.216273] ... version:                0
[    0.216274] ... bit width:              48
[    0.216274] ... generic registers:      6
[    0.216275] ... value mask:             0000ffffffffffff
[    0.216276] ... max period:             00007fffffffffff
[    0.216277] ... fixed-purpose events:   0
[    0.216278] ... event mask:             000000000000003f
[    0.223336] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.225336] x86: Booting SMP configuration:
[    0.225338] .... node  #0, CPUs:      #1 #2 #3 #4 #5 #6 #7
[    0.328643] x86: Booted up 1 node, 8 CPUs
[    0.328646] smpboot: Total of 8 processors activated (63860.94 BogoMIPS)
[    0.338618] devtmpfs: initialized
[    0.341193] EVM: security.selinux
[    0.341194] EVM: security.SMACK64
[    0.341195] EVM: security.ima
[    0.341196] EVM: security.capability
[    0.341260] PM: Registering ACPI NVS region [mem 0xbe4e7000-0xbe8d9fff] (4141056 bytes)
[    0.341315] PM: Registering ACPI NVS region [mem 0xbee2e000-0xbf033fff] (2121728 bytes)
[    0.342033] pinctrl core: initialized pinctrl subsystem
[    0.342083] regulator-dummy: no parameters
[    0.342105] RTC time: 22:31:49, date: 03/15/15
[    0.342136] NET: Registered protocol family 16
[    0.342231] cpuidle: using governor ladder
[    0.342232] cpuidle: using governor menu
[    0.342300] ACPI: bus type PCI registered
[    0.342301] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.342348] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.342350] PCI: not using MMCONFIG
[    0.342351] PCI: Using configuration type 1 for base access
[    0.342352] PCI: Using configuration type 1 for extended access
[    0.343359] bio: create slab <bio-0> at 0
[    0.343532] ACPI: Added _OSI(Module Device)
[    0.343533] ACPI: Added _OSI(Processor Device)
[    0.343535] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.343536] ACPI: Added _OSI(Processor Aggregator Device)
[    0.345732] ACPI: Executed 3 blocks of module-level executable AML code
[    0.355917] ACPI: Interpreter enabled
[    0.355923] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
[    0.355926] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.355941] ACPI: (supports S0 S3 S4 S5)
[    0.355942] ACPI: Using IOAPIC for interrupt routing
[    0.356073] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.356109] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.369240] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.369343] ACPI: No dock devices found.
[    0.401246] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.401251] acpi PNP0A03:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.401255] acpi PNP0A03:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[    0.401689] PCI host bridge to bus 0000:00
[    0.401691] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.401693] pci_bus 0000:00: root bus resource [io  0x0000-0x03af]
[    0.401694] pci_bus 0000:00: root bus resource [io  0x03e0-0x0cf7]
[    0.401696] pci_bus 0000:00: root bus resource [io  0x03b0-0x03df]
[    0.401697] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.401699] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.401700] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000dffff]
[    0.401701] pci_bus 0000:00: root bus resource [mem 0xc0000000-0xffffffff]
[    0.401711] pci 0000:00:00.0: [1002:5a14] type 00 class 0x060000
[    0.401826] pci 0000:00:00.2: [1002:5a23] type 00 class 0x080600
[    0.401924] pci 0000:00:02.0: [1002:5a16] type 01 class 0x060400
[    0.401957] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.402010] pci 0000:00:02.0: System wakeup disabled by ACPI
[    0.402038] pci 0000:00:09.0: [1002:5a1c] type 01 class 0x060400
[    0.402069] pci 0000:00:09.0: PME# supported from D0 D3hot D3cold
[    0.402120] pci 0000:00:09.0: System wakeup disabled by ACPI
[    0.402154] pci 0000:00:11.0: [1002:4390] type 00 class 0x01018f
[    0.402170] pci 0000:00:11.0: reg 0x10: [io  0xf090-0xf097]
[    0.402177] pci 0000:00:11.0: reg 0x14: [io  0xf080-0xf083]
[    0.402184] pci 0000:00:11.0: reg 0x18: [io  0xf070-0xf077]
[    0.402191] pci 0000:00:11.0: reg 0x1c: [io  0xf060-0xf063]
[    0.402198] pci 0000:00:11.0: reg 0x20: [io  0xf050-0xf05f]
[    0.402205] pci 0000:00:11.0: reg 0x24: [mem 0xfeb07000-0xfeb073ff]
[    0.402220] pci 0000:00:11.0: set SATA to AHCI mode
[    0.402310] pci 0000:00:12.0: [1002:4397] type 00 class 0x0c0310
[    0.402320] pci 0000:00:12.0: reg 0x10: [mem 0xfeb06000-0xfeb06fff]
[    0.402406] pci 0000:00:12.0: System wakeup disabled by ACPI
[    0.402433] pci 0000:00:12.2: [1002:4396] type 00 class 0x0c0320
[    0.402448] pci 0000:00:12.2: reg 0x10: [mem 0xfeb05000-0xfeb050ff]
[    0.402510] pci 0000:00:12.2: supports D1 D2
[    0.402511] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.402563] pci 0000:00:12.2: System wakeup disabled by ACPI
[    0.402593] pci 0000:00:13.0: [1002:4397] type 00 class 0x0c0310
[    0.402603] pci 0000:00:13.0: reg 0x10: [mem 0xfeb04000-0xfeb04fff]
[    0.402689] pci 0000:00:13.0: System wakeup disabled by ACPI
[    0.402717] pci 0000:00:13.2: [1002:4396] type 00 class 0x0c0320
[    0.402731] pci 0000:00:13.2: reg 0x10: [mem 0xfeb03000-0xfeb030ff]
[    0.402794] pci 0000:00:13.2: supports D1 D2
[    0.402795] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.402850] pci 0000:00:13.2: System wakeup disabled by ACPI
[    0.402876] pci 0000:00:14.0: [1002:4385] type 00 class 0x0c0500
[    0.402985] pci 0000:00:14.1: [1002:439c] type 00 class 0x01018a
[    0.402995] pci 0000:00:14.1: reg 0x10: [io  0xf040-0xf047]
[    0.403002] pci 0000:00:14.1: reg 0x14: [io  0xf030-0xf033]
[    0.403009] pci 0000:00:14.1: reg 0x18: [io  0xf020-0xf027]
[    0.403017] pci 0000:00:14.1: reg 0x1c: [io  0xf010-0xf013]
[    0.403024] pci 0000:00:14.1: reg 0x20: [io  0xf000-0xf00f]
[    0.403126] pci 0000:00:14.3: [1002:439d] type 00 class 0x060100
[    0.403239] pci 0000:00:14.4: [1002:4384] type 01 class 0x060401
[    0.403308] pci 0000:00:14.4: System wakeup disabled by ACPI
[    0.403330] pci 0000:00:14.5: [1002:4399] type 00 class 0x0c0310
[    0.403340] pci 0000:00:14.5: reg 0x10: [mem 0xfeb02000-0xfeb02fff]
[    0.403424] pci 0000:00:14.5: System wakeup disabled by ACPI
[    0.403451] pci 0000:00:15.0: [1002:43a0] type 01 class 0x060400
[    0.403505] pci 0000:00:15.0: supports D1 D2
[    0.403559] pci 0000:00:15.0: System wakeup disabled by ACPI
[    0.403589] pci 0000:00:15.2: [1002:43a2] type 01 class 0x060400
[    0.403643] pci 0000:00:15.2: supports D1 D2
[    0.403694] pci 0000:00:15.2: System wakeup disabled by ACPI
[    0.403720] pci 0000:00:15.3: [1002:43a3] type 01 class 0x060400
[    0.403774] pci 0000:00:15.3: supports D1 D2
[    0.403826] pci 0000:00:15.3: System wakeup disabled by ACPI
[    0.403852] pci 0000:00:16.0: [1002:4397] type 00 class 0x0c0310
[    0.403862] pci 0000:00:16.0: reg 0x10: [mem 0xfeb01000-0xfeb01fff]
[    0.403948] pci 0000:00:16.0: System wakeup disabled by ACPI
[    0.403975] pci 0000:00:16.2: [1002:4396] type 00 class 0x0c0320
[    0.403990] pci 0000:00:16.2: reg 0x10: [mem 0xfeb00000-0xfeb000ff]
[    0.404052] pci 0000:00:16.2: supports D1 D2
[    0.404053] pci 0000:00:16.2: PME# supported from D0 D1 D2 D3hot
[    0.404103] pci 0000:00:16.2: System wakeup disabled by ACPI
[    0.404130] pci 0000:00:18.0: [1022:1600] type 00 class 0x060000
[    0.404202] pci 0000:00:18.1: [1022:1601] type 00 class 0x060000
[    0.404269] pci 0000:00:18.2: [1022:1602] type 00 class 0x060000
[    0.404335] pci 0000:00:18.3: [1022:1603] type 00 class 0x060000
[    0.404404] pci 0000:00:18.4: [1022:1604] type 00 class 0x060000
[    0.404469] pci 0000:00:18.5: [1022:1605] type 00 class 0x060000
[    0.404583] pci 0000:01:00.0: [1002:6779] type 00 class 0x030000
[    0.404597] pci 0000:01:00.0: reg 0x10: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.404608] pci 0000:01:00.0: reg 0x18: [mem 0xfea20000-0xfea3ffff 64bit]
[    0.404615] pci 0000:01:00.0: reg 0x20: [io  0xe000-0xe0ff]
[    0.404628] pci 0000:01:00.0: reg 0x30: [mem 0xfea00000-0xfea1ffff pref]
[    0.404661] pci 0000:01:00.0: supports D1 D2
[    0.404700] pci 0000:01:00.1: [1002:aa98] type 00 class 0x040300
[    0.404713] pci 0000:01:00.1: reg 0x10: [mem 0xfea40000-0xfea43fff 64bit]
[    0.404773] pci 0000:01:00.1: supports D1 D2
[    0.406605] pci 0000:00:02.0: PCI bridge to [bus 01]
[    0.406610] pci 0000:00:02.0:   bridge window [io  0xe000-0xefff]
[    0.406612] pci 0000:00:02.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.406616] pci 0000:00:02.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.406677] pci 0000:02:00.0: [1b21:1042] type 00 class 0x0c0330
[    0.406695] pci 0000:02:00.0: reg 0x10: [mem 0xfe900000-0xfe907fff 64bit]
[    0.406813] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    0.408783] pci 0000:00:09.0: PCI bridge to [bus 02]
[    0.408788] pci 0000:00:09.0:   bridge window [mem 0xfe900000-0xfe9fffff]
[    0.408829] pci 0000:03:06.0: [1814:3062] type 00 class 0x028000
[    0.408847] pci 0000:03:06.0: reg 0x10: [mem 0xfe800000-0xfe80ffff]
[    0.408977] pci 0000:00:14.4: PCI bridge to [bus 03] (subtractive decode)
[    0.408982] pci 0000:00:14.4:   bridge window [mem 0xfe800000-0xfe8fffff]
[    0.408985] pci 0000:00:14.4:   bridge window [io  0x0000-0x03af] (subtractive decode)
[    0.408987] pci 0000:00:14.4:   bridge window [io  0x03e0-0x0cf7] (subtractive decode)
[    0.408988] pci 0000:00:14.4:   bridge window [io  0x03b0-0x03df] (subtractive decode)
[    0.408989] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.408991] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.408992] pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
[    0.408994] pci 0000:00:14.4:   bridge window [mem 0xc0000000-0xffffffff] (subtractive decode)
[    0.409035] pci 0000:00:15.0: PCI bridge to [bus 04]
[    0.409101] pci 0000:05:00.0: [1106:3403] type 00 class 0x0c0010
[    0.409122] pci 0000:05:00.0: reg 0x10: [mem 0xfe700000-0xfe7007ff 64bit]
[    0.409133] pci 0000:05:00.0: reg 0x18: [io  0xd000-0xd0ff]
[    0.409247] pci 0000:05:00.0: supports D2
[    0.409248] pci 0000:05:00.0: PME# supported from D2 D3hot D3cold
[    0.410613] pci 0000:00:15.2: PCI bridge to [bus 05]
[    0.410618] pci 0000:00:15.2:   bridge window [io  0xd000-0xdfff]
[    0.410621] pci 0000:00:15.2:   bridge window [mem 0xfe700000-0xfe7fffff]
[    0.410688] pci 0000:06:00.0: [10ec:8168] type 00 class 0x020000
[    0.410704] pci 0000:06:00.0: reg 0x10: [io  0xc000-0xc0ff]
[    0.410730] pci 0000:06:00.0: reg 0x18: [mem 0xd0004000-0xd0004fff 64bit pref]
[    0.410747] pci 0000:06:00.0: reg 0x20: [mem 0xd0000000-0xd0003fff 64bit pref]
[    0.410828] pci 0000:06:00.0: supports D1 D2
[    0.410829] pci 0000:06:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.412792] pci 0000:00:15.3: PCI bridge to [bus 06]
[    0.412797] pci 0000:00:15.3:   bridge window [io  0xc000-0xcfff]
[    0.412802] pci 0000:00:15.3:   bridge window [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.424701] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11 14 15) *0
[    0.424766] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11 14 15) *0
[    0.424830] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11 14 15) *0
[    0.424894] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11 14 15) *0
[    0.424946] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11 14 15) *0
[    0.424988] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11 14 15) *0
[    0.425030] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11 14 15) *0
[    0.425071] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11 14 15) *0
[    0.425254] ACPI: \_SB_.PCI0: notify handler is installed
[    0.425290] Found 1 acpi root devices
[    0.425372] vgaarb: setting as boot device: PCI:0000:01:00.0
[    0.425374] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.425375] vgaarb: loaded
[    0.425376] vgaarb: bridge control possible 0000:01:00.0
[    0.425515] SCSI subsystem initialized
[    0.425570] libata version 3.00 loaded.
[    0.425586] ACPI: bus type USB registered
[    0.425599] usbcore: registered new interface driver usbfs
[    0.425606] usbcore: registered new interface driver hub
[    0.425626] usbcore: registered new device driver usb
[    0.425736] PCI: Using ACPI for IRQ routing
[    0.432048] PCI: pci_cache_line_size set to 64 bytes
[    0.432105] e820: reserve RAM buffer [mem 0x0009fc00-0x0009ffff]
[    0.432106] e820: reserve RAM buffer [mem 0xbe340000-0xbfffffff]
[    0.432108] e820: reserve RAM buffer [mem 0xbee2e000-0xbfffffff]
[    0.432109] e820: reserve RAM buffer [mem 0xbf452000-0xbfffffff]
[    0.432110] e820: reserve RAM buffer [mem 0xbf800000-0xbfffffff]
[    0.432111] e820: reserve RAM buffer [mem 0x23f000000-0x23fffffff]
[    0.432171] NetLabel: Initializing
[    0.432172] NetLabel:  domain hash size = 128
[    0.432173] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.432183] NetLabel:  unlabeled traffic allowed by default
[    0.432230] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.432232] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    0.434313] Switched to clocksource hpet
[    0.439548] AppArmor: AppArmor Filesystem Enabled
[    0.439561] pnp: PnP ACPI init
[    0.439570] ACPI: bus type PNP registered
[    0.439648] system 00:00: [mem 0xe0000000-0xefffffff] has been reserved
[    0.439650] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.439751] system 00:01: [mem 0xfec20000-0xfec200ff] could not be reserved
[    0.439753] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.439817] system 00:02: [mem 0xfeb20000-0xfeb23fff] could not be reserved
[    0.439819] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.440080] system 00:03: [io  0x040b] has been reserved
[    0.440082] system 00:03: [io  0x04d6] has been reserved
[    0.440084] system 00:03: [io  0x0c00-0x0c01] has been reserved
[    0.440086] system 00:03: [io  0x0c14] has been reserved
[    0.440087] system 00:03: [io  0x0c50-0x0c51] has been reserved
[    0.440089] system 00:03: [io  0x0c52] has been reserved
[    0.440090] system 00:03: [io  0x0c6c] has been reserved
[    0.440091] system 00:03: [io  0x0c6f] has been reserved
[    0.440093] system 00:03: [io  0x0cd0-0x0cd1] has been reserved
[    0.440094] system 00:03: [io  0x0cd2-0x0cd3] has been reserved
[    0.440096] system 00:03: [io  0x0cd4-0x0cd5] has been reserved
[    0.440097] system 00:03: [io  0x0cd6-0x0cd7] has been reserved
[    0.440099] system 00:03: [io  0x0cd8-0x0cdf] has been reserved
[    0.440100] system 00:03: [io  0x0800-0x089f] could not be reserved
[    0.440102] system 00:03: [io  0x0b20-0x0b3f] has been reserved
[    0.440104] system 00:03: [io  0x0900-0x090f] has been reserved
[    0.440105] system 00:03: [io  0x0910-0x091f] has been reserved
[    0.440107] system 00:03: [io  0xfe00-0xfefe] has been reserved
[    0.440109] system 00:03: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.440110] system 00:03: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.440112] system 00:03: [mem 0xfed80000-0xfed8ffff] has been reserved
[    0.440114] system 00:03: [mem 0xfed61000-0xfed70fff] has been reserved
[    0.440116] system 00:03: [mem 0xfec10000-0xfec10fff] has been reserved
[    0.440117] system 00:03: [mem 0xfed00000-0xfed00fff] has been reserved
[    0.440119] system 00:03: [mem 0xffc00000-0xffffffff] has been reserved
[    0.440121] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.440198] system 00:04: [io  0x0290-0x029f] has been reserved
[    0.440200] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.440374] pnp 00:05: [dma 4]
[    0.440388] pnp 00:05: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.440419] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.440437] pnp 00:07: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.440485] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.440487] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.440509] pnp 00:09: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.440541] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.440583] pnp 00:0b: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.440630] pnp 00:0c: Plug and Play ACPI device, IDs PNP0f03 PNP0f13 (active)
[    0.440755] pnp 00:0d: [dma 0 disabled]
[    0.440790] pnp 00:0d: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.452514] pnp 00:0e: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.452521] pnp: PnP ACPI: found 15 devices
[    0.452522] ACPI: bus type PNP unregistered
[    0.458748] pci 0000:00:02.0: PCI bridge to [bus 01]
[    0.458751] pci 0000:00:02.0:   bridge window [io  0xe000-0xefff]
[    0.458754] pci 0000:00:02.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.458756] pci 0000:00:02.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.458759] pci 0000:00:09.0: PCI bridge to [bus 02]
[    0.458762] pci 0000:00:09.0:   bridge window [mem 0xfe900000-0xfe9fffff]
[    0.458765] pci 0000:00:14.4: PCI bridge to [bus 03]
[    0.458769] pci 0000:00:14.4:   bridge window [mem 0xfe800000-0xfe8fffff]
[    0.458775] pci 0000:00:15.0: PCI bridge to [bus 04]
[    0.458782] pci 0000:00:15.2: PCI bridge to [bus 05]
[    0.458784] pci 0000:00:15.2:   bridge window [io  0xd000-0xdfff]
[    0.458788] pci 0000:00:15.2:   bridge window [mem 0xfe700000-0xfe7fffff]
[    0.458793] pci 0000:00:15.3: PCI bridge to [bus 06]
[    0.458795] pci 0000:00:15.3:   bridge window [io  0xc000-0xcfff]
[    0.458799] pci 0000:00:15.3:   bridge window [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.458804] pci_bus 0000:00: resource 4 [io  0x0000-0x03af]
[    0.458805] pci_bus 0000:00: resource 5 [io  0x03e0-0x0cf7]
[    0.458806] pci_bus 0000:00: resource 6 [io  0x03b0-0x03df]
[    0.458808] pci_bus 0000:00: resource 7 [io  0x0d00-0xffff]
[    0.458809] pci_bus 0000:00: resource 8 [mem 0x000a0000-0x000bffff]
[    0.458811] pci_bus 0000:00: resource 9 [mem 0x000c0000-0x000dffff]
[    0.458812] pci_bus 0000:00: resource 10 [mem 0xc0000000-0xffffffff]
[    0.458813] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.458815] pci_bus 0000:01: resource 1 [mem 0xfea00000-0xfeafffff]
[    0.458816] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.458818] pci_bus 0000:02: resource 1 [mem 0xfe900000-0xfe9fffff]
[    0.458819] pci_bus 0000:03: resource 1 [mem 0xfe800000-0xfe8fffff]
[    0.458821] pci_bus 0000:03: resource 4 [io  0x0000-0x03af]
[    0.458822] pci_bus 0000:03: resource 5 [io  0x03e0-0x0cf7]
[    0.458823] pci_bus 0000:03: resource 6 [io  0x03b0-0x03df]
[    0.458825] pci_bus 0000:03: resource 7 [io  0x0d00-0xffff]
[    0.458826] pci_bus 0000:03: resource 8 [mem 0x000a0000-0x000bffff]
[    0.458827] pci_bus 0000:03: resource 9 [mem 0x000c0000-0x000dffff]
[    0.458829] pci_bus 0000:03: resource 10 [mem 0xc0000000-0xffffffff]
[    0.458830] pci_bus 0000:05: resource 0 [io  0xd000-0xdfff]
[    0.458831] pci_bus 0000:05: resource 1 [mem 0xfe700000-0xfe7fffff]
[    0.458833] pci_bus 0000:06: resource 0 [io  0xc000-0xcfff]
[    0.458834] pci_bus 0000:06: resource 2 [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.458856] NET: Registered protocol family 2
[    0.459041] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
[    0.459196] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.459375] TCP: Hash tables configured (established 65536 bind 65536)
[    0.459401] TCP: reno registered
[    0.459412] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.459445] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.459514] NET: Registered protocol family 1
[    0.719155] pci 0000:01:00.0: Video device with shadowed ROM
[    0.719331] PCI: CLS 64 bytes, default 64
[    0.719378] Trying to unpack rootfs image as initramfs...
[    0.947627] Freeing initrd memory: 18712K (ffff880035b64000 - ffff880036daa000)
[    0.948076] AMD-Vi: Found IOMMU at 0000:00:00.2 cap 0x40
[    0.948077] AMD-Vi: Interrupt remapping enabled
[    0.948090] pci 0000:00:00.2: irq 72 for MSI/MSI-X
[    0.957091] AMD-Vi: Lazy IO/TLB flushing enabled
[    1.035522] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.035524] software IO TLB [mem 0xba340000-0xbe340000] (64MB) mapped at [ffff8800ba340000-ffff8800be33ffff]
[    1.035783] perf: AMD NB counters detected
[    1.035811] LVT offset 0 assigned for vector 0x400
[    1.035835] perf: AMD IBS detected (0x000000ff)
[    1.035868] microcode: CPU0: patch_level=0x06000817
[    1.035873] microcode: CPU1: patch_level=0x06000817
[    1.035881] microcode: CPU2: patch_level=0x06000817
[    1.035886] microcode: CPU3: patch_level=0x06000817
[    1.035893] microcode: CPU4: patch_level=0x06000817
[    1.035899] microcode: CPU5: patch_level=0x06000817
[    1.035906] microcode: CPU6: patch_level=0x06000817
[    1.035913] microcode: CPU7: patch_level=0x06000817
[    1.035963] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.035965] Scanning for low memory corruption every 60 seconds
[    1.036232] Initialise system trusted keyring
[    1.036267] audit: initializing netlink socket (disabled)
[    1.036280] type=2000 audit(1426458708.825:1): initialized
[    1.051843] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.052895] zbud: loaded
[    1.053000] VFS: Disk quotas dquot_6.5.2
[    1.053031] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.053404] fuse init (API version 7.22)
[    1.053461] msgmni has been set to 15754
[    1.053504] Key type big_key registered
[    1.053965] Key type asymmetric registered
[    1.053967] Asymmetric key parser 'x509' registered
[    1.054018] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.054064] io scheduler noop registered
[    1.054065] io scheduler deadline registered (default)
[    1.054086] io scheduler cfq registered
[    1.054719] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.054730] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.054762] vesafb: mode is 1400x1050x32, linelength=5632, pages=0
[    1.054763] vesafb: scrolling: redraw
[    1.054765] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[    1.055071] vesafb: framebuffer at 0xc0000000, mapped to 0xffffc90010e80000, using 5824k, total 5824k
[    1.085281] Console: switching to colour frame buffer device 175x65
[    1.115268] fb0: VESA VGA frame buffer device
[    1.115283] ipmi message handler version 39.2
[    1.115334] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.115336] ACPI: Power Button [PWRB]
[    1.115361] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.115363] ACPI: Power Button [PWRF]
[    1.115414] ACPI: acpi_idle registered with cpuidle
[    1.115879] GHES: HEST is not enabled!
[    1.115946] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.136547] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    1.137835] Linux agpgart interface v0.103
[    1.138968] brd: module loaded
[    1.139573] loop: module loaded
[    1.139884] libphy: Fixed MDIO Bus: probed
[    1.139959] tun: Universal TUN/TAP device driver, 1.6
[    1.139960] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.139995] PPP generic driver version 2.4.2
[    1.140031] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.140034] ehci-pci: EHCI PCI platform driver
[    1.140160] QUIRK: Enable AMD PLL fix
[    1.140177] ehci-pci 0000:00:12.2: EHCI Host Controller
[    1.140181] ehci-pci 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.140184] ehci-pci 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.140192] ehci-pci 0000:00:12.2: debug port 1
[    1.140255] ehci-pci 0000:00:12.2: irq 17, io mem 0xfeb05000
[    1.145666] ehci-pci 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.145713] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.145715] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.145717] usb usb1: Product: EHCI Host Controller
[    1.145718] usb usb1: Manufacturer: Linux 3.13.0-46-lowlatency ehci_hcd
[    1.145719] usb usb1: SerialNumber: 0000:00:12.2
[    1.145826] hub 1-0:1.0: USB hub found
[    1.145832] hub 1-0:1.0: 5 ports detected
[    1.146038] ehci-pci 0000:00:13.2: EHCI Host Controller
[    1.146042] ehci-pci 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.146045] ehci-pci 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.146053] ehci-pci 0000:00:13.2: debug port 1
[    1.146111] ehci-pci 0000:00:13.2: irq 17, io mem 0xfeb03000
[    1.151689] ehci-pci 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.151720] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.151722] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.151723] usb usb2: Product: EHCI Host Controller
[    1.151724] usb usb2: Manufacturer: Linux 3.13.0-46-lowlatency ehci_hcd
[    1.151725] usb usb2: SerialNumber: 0000:00:13.2
[    1.151816] hub 2-0:1.0: USB hub found
[    1.151821] hub 2-0:1.0: 5 ports detected
[    1.152040] ehci-pci 0000:00:16.2: EHCI Host Controller
[    1.152043] ehci-pci 0000:00:16.2: new USB bus registered, assigned bus number 3
[    1.152046] ehci-pci 0000:00:16.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.152054] ehci-pci 0000:00:16.2: debug port 1
[    1.152112] ehci-pci 0000:00:16.2: irq 17, io mem 0xfeb00000
[    1.157713] ehci-pci 0000:00:16.2: USB 2.0 started, EHCI 1.00
[    1.157752] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    1.157754] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.157755] usb usb3: Product: EHCI Host Controller
[    1.157757] usb usb3: Manufacturer: Linux 3.13.0-46-lowlatency ehci_hcd
[    1.157758] usb usb3: SerialNumber: 0000:00:16.2
[    1.157900] hub 3-0:1.0: USB hub found
[    1.157904] hub 3-0:1.0: 4 ports detected
[    1.157987] ehci-platform: EHCI generic platform driver
[    1.157993] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.157995] ohci-pci: OHCI PCI platform driver
[    1.158120] ohci-pci 0000:00:12.0: OHCI PCI host controller
[    1.158123] ohci-pci 0000:00:12.0: new USB bus registered, assigned bus number 4
[    1.158185] ohci-pci 0000:00:12.0: irq 18, io mem 0xfeb06000
[    1.212801] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.212804] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.212805] usb usb4: Product: OHCI PCI host controller
[    1.212807] usb usb4: Manufacturer: Linux 3.13.0-46-lowlatency ohci_hcd
[    1.212808] usb usb4: SerialNumber: 0000:00:12.0
[    1.213003] hub 4-0:1.0: USB hub found
[    1.213010] hub 4-0:1.0: 5 ports detected
[    1.213212] ohci-pci 0000:00:13.0: OHCI PCI host controller
[    1.213215] ohci-pci 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.213264] ohci-pci 0000:00:13.0: irq 18, io mem 0xfeb04000
[    1.267942] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.267945] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.267946] usb usb5: Product: OHCI PCI host controller
[    1.267948] usb usb5: Manufacturer: Linux 3.13.0-46-lowlatency ohci_hcd
[    1.267949] usb usb5: SerialNumber: 0000:00:13.0
[    1.268133] hub 5-0:1.0: USB hub found
[    1.268139] hub 5-0:1.0: 5 ports detected
[    1.268345] ohci-pci 0000:00:14.5: OHCI PCI host controller
[    1.268349] ohci-pci 0000:00:14.5: new USB bus registered, assigned bus number 6
[    1.268398] ohci-pci 0000:00:14.5: irq 18, io mem 0xfeb02000
[    1.323039] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    1.323041] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.323043] usb usb6: Product: OHCI PCI host controller
[    1.323044] usb usb6: Manufacturer: Linux 3.13.0-46-lowlatency ohci_hcd
[    1.323046] usb usb6: SerialNumber: 0000:00:14.5
[    1.323210] hub 6-0:1.0: USB hub found
[    1.323219] hub 6-0:1.0: 2 ports detected
[    1.323397] ohci-pci 0000:00:16.0: OHCI PCI host controller
[    1.323402] ohci-pci 0000:00:16.0: new USB bus registered, assigned bus number 7
[    1.323507] ohci-pci 0000:00:16.0: irq 18, io mem 0xfeb01000
[    1.378136] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    1.378138] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.378140] usb usb7: Product: OHCI PCI host controller
[    1.378141] usb usb7: Manufacturer: Linux 3.13.0-46-lowlatency ohci_hcd
[    1.378143] usb usb7: SerialNumber: 0000:00:16.0
[    1.378384] hub 7-0:1.0: USB hub found
[    1.378391] hub 7-0:1.0: 4 ports detected
[    1.378468] ohci-platform: OHCI generic platform driver
[    1.378474] uhci_hcd: USB Universal Host Controller Interface driver
[    1.378535] xhci_hcd 0000:02:00.0: xHCI Host Controller
[    1.378539] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 8
[    1.382939] xhci_hcd 0000:02:00.0: irq 73 for MSI/MSI-X
[    1.382947] xhci_hcd 0000:02:00.0: irq 74 for MSI/MSI-X
[    1.382953] xhci_hcd 0000:02:00.0: irq 75 for MSI/MSI-X
[    1.382960] xhci_hcd 0000:02:00.0: irq 76 for MSI/MSI-X
[    1.382973] xhci_hcd 0000:02:00.0: irq 77 for MSI/MSI-X
[    1.382980] xhci_hcd 0000:02:00.0: irq 78 for MSI/MSI-X
[    1.382986] xhci_hcd 0000:02:00.0: irq 79 for MSI/MSI-X
[    1.382993] xhci_hcd 0000:02:00.0: irq 80 for MSI/MSI-X
[    1.383499] usb usb8: New USB device found, idVendor=1d6b, idProduct=0002
[    1.383501] usb usb8: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.383503] usb usb8: Product: xHCI Host Controller
[    1.383504] usb usb8: Manufacturer: Linux 3.13.0-46-lowlatency xhci_hcd
[    1.383505] usb usb8: SerialNumber: 0000:02:00.0
[    1.383595] hub 8-0:1.0: USB hub found
[    1.383603] hub 8-0:1.0: 2 ports detected
[    1.383656] xhci_hcd 0000:02:00.0: xHCI Host Controller
[    1.383658] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 9
[    1.383695] usb usb9: New USB device found, idVendor=1d6b, idProduct=0003
[    1.383697] usb usb9: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.383698] usb usb9: Product: xHCI Host Controller
[    1.383699] usb usb9: Manufacturer: Linux 3.13.0-46-lowlatency xhci_hcd
[    1.383700] usb usb9: SerialNumber: 0000:02:00.0
[    1.383766] hub 9-0:1.0: USB hub found
[    1.383772] hub 9-0:1.0: 2 ports detected
[    1.389314] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.391977] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.392011] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.392099] mousedev: PS/2 mouse device common for all mice
[    1.392239] rtc_cmos 00:06: RTC can wake from S4
[    1.392325] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.392439] rtc_cmos 00:06: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.392490] device-mapper: uevent: version 1.0.3
[    1.392545] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    1.392551] ledtrig-cpu: registered to indicate activity on CPUs
[    1.392630] TCP: cubic registered
[    1.392698] NET: Registered protocol family 10
[    1.392824] NET: Registered protocol family 17
[    1.392829] Key type dns_resolver registered
[    1.393501] Loading compiled-in X.509 certificates
[    1.394239] Loaded X.509 cert 'Magrathea: Glacier signing key: 5bf75c2f0447f99b533de364c848f704cbb48760'
[    1.394247] registered taskstats version 1
[    1.396569] Key type trusted registered
[    1.399746] Key type encrypted registered
[    1.399750] AppArmor: AppArmor sha1 policy hashing enabled
[    1.399752] IMA: No TPM chip found, activating TPM-bypass!
[    1.400031] regulator-dummy: disabling
[    1.400090]   Magic number: 7:919:552
[    1.400100] tty ttyS28: hash matches
[    1.400104] clockevents clockevent3: hash matches
[    1.400114] acpi PNP0C0F:03: hash matches
[    1.400167] rtc_cmos 00:06: setting system clock to 2015-03-15 22:31:50 UTC (1426458710)
[    1.400284] acpi-cpufreq: overriding BIOS provided _PSD data
[    1.400599] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.400600] EDD information not available.
[    1.400634] PM: Hibernation image not present or could not be loaded.
[    1.401637] Freeing unused kernel memory: 1324K (ffffffff81d1d000 - ffffffff81e68000)
[    1.401639] Write protecting the kernel read-only data: 12288k
[    1.404166] Freeing unused kernel memory: 780K (ffff88000173d000 - ffff880001800000)
[    1.406264] Freeing unused kernel memory: 688K (ffff880001b54000 - ffff880001c00000)
[    1.413645] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.417729] systemd-udevd[176]: starting version 204
[    1.435089] scsi0 : pata_atiixp
[    1.435192] scsi1 : pata_atiixp
[    1.435222] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    1.435224] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    1.435245] ahci 0000:00:11.0: version 3.0
[    1.435459] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 4 ports 6 Gbps 0xf impl SATA mode
[    1.435462] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    1.435951] scsi2 : ahci
[    1.436017] scsi3 : ahci
[    1.436121] scsi4 : ahci
[    1.436208] scsi5 : ahci
[    1.436284] ata3: SATA max UDMA/133 abar m1024@0xfeb07000 port 0xfeb07100 irq 19
[    1.436286] ata4: SATA max UDMA/133 abar m1024@0xfeb07000 port 0xfeb07180 irq 19
[    1.436288] ata5: SATA max UDMA/133 abar m1024@0xfeb07000 port 0xfeb07200 irq 19
[    1.436292] ata6: SATA max UDMA/133 abar m1024@0xfeb07000 port 0xfeb07280 irq 19
[    1.438032] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.438042] r8169 0000:06:00.0: can't disable ASPM; OS doesn't have ASPM control
[    1.438284] r8169 0000:06:00.0: irq 81 for MSI/MSI-X
[    1.438457] r8169 0000:06:00.0 eth0: RTL8168evl/8111evl at 0xffffc90010c82000, bc:5f:f4:0b:8e:65, XID 0c900800 IRQ 81
[    1.438460] r8169 0000:06:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    1.490348] firewire_ohci 0000:05:00.0: added OHCI v1.10 device as card 0, 4 IR + 8 IT contexts, quirks 0x11
[    1.700749] usb 1-2: new high-speed USB device number 3 using ehci-pci
[    1.741711] ata5: SATA link down (SStatus 0 SControl 300)
[    1.741768] ata4: SATA link down (SStatus 0 SControl 300)
[    1.741803] ata6: SATA link down (SStatus 0 SControl 300)
[    1.817213] usb 1-2: New USB device found, idVendor=05e3, idProduct=0608
[    1.817216] usb 1-2: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[    1.817218] usb 1-2: Product: USB2.0 Hub
[    1.817544] hub 1-2:1.0: USB hub found
[    1.817898] hub 1-2:1.0: 4 ports detected
[    1.853277] psmouse serio1: alps: Unknown ALPS touchpad: E7=10 00 64, EC=10 00 64
[    1.896982] ata3: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.898340] ata3.00: ATA-8: ST500DM002-1BD142, KC48, max UDMA/133
[    1.898343] ata3.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.899980] ata3.00: configured for UDMA/133
[    1.900111] scsi 2:0:0:0: Direct-Access     ATA      ST500DM002-1BD14 KC48 PQ: 0 ANSI: 5
[    1.900252] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    1.900263] sd 2:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.900265] sd 2:0:0:0: [sda] 4096-byte physical blocks
[    1.900395] sd 2:0:0:0: [sda] Write Protect is off
[    1.900397] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.900438] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.930659]  sda: sda1 < sda5 sda6 sda7 > sda2
[    1.931175] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.992200] firewire_core 0000:05:00.0: created device fw0: GUID 008f13008fe51300, S400
[    2.039134] tsc: Refined TSC clocksource calibration: 3991.500 MHz
[    2.299733] usb 5-2: new full-speed USB device number 2 using ohci-pci
[    2.365738] random: nonblocking pool is initialized
[    2.457093] usb 5-2: New USB device found, idVendor=0b05, idProduct=17cb
[    2.457100] usb 5-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.457104] usb 5-2: Product: BCM20702A0
[    2.457108] usb 5-2: Manufacturer: Broadcom Corp
[    2.457112] usb 5-2: SerialNumber: 5CF37064503A
[    2.654550] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input4
[    2.686326] usb 4-1: new full-speed USB device number 2 using ohci-pci
[    2.836553] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    2.845702] usb 4-1: New USB device found, idVendor=0582, idProduct=002c
[    2.845704] usb 4-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.845706] usb 4-1: Product: EDIROL UA-700
[    2.845708] usb 4-1: Manufacturer: Roland
[    3.000952] usb 8-2: new high-speed USB device number 2 using xhci_hcd
[    3.041192] Switched to clocksource tsc
[    3.168583] usb 8-2: New USB device found, idVendor=0bda, idProduct=58bb
[    3.168592] usb 8-2: New USB device strings: Mfr=3, Product=1, SerialNumber=2
[    3.168598] usb 8-2: Product: FULL HD 1080P Webcam
[    3.168602] usb 8-2: Manufacturer: Generic
[    3.168606] usb 8-2: SerialNumber: 200901010001
[    3.342804] usb 1-2.3: new full-speed USB device number 4 using ehci-pci
[    3.424650] usb 1-2.3: New USB device found, idVendor=056a, idProduct=00d4
[    3.424657] usb 1-2.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.424662] usb 1-2.3: Product: CTL-460
[    3.424666] usb 1-2.3: Manufacturer: Wacom Co.,Ltd.
[    3.487982] usb 1-2.4: new high-speed USB device number 5 using ehci-pci
[    3.567608] usb 1-2.4: New USB device found, idVendor=04a9, idProduct=1741
[    3.567611] usb 1-2.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    3.567613] usb 1-2.4: Product: MX340 series
[    3.567614] usb 1-2.4: Manufacturer: Canon
[    3.567615] usb 1-2.4: SerialNumber: 32EF1D
[   14.542157] Adding 2559996k swap on /dev/sda6.  Priority:-1 extents:1 across:2559996k FS
[   14.583084] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.620611] systemd-udevd[369]: starting version 204
[   14.660762] lp: driver loaded but no devices found
[   14.667535] [drm] Initialized drm 1.1.0 20060810
[   14.667601] vboxvideo: module verification failed: signature and/or  required key missing - tainting kernel
[   14.670976] Linux video capture interface: v2.00
[   14.672266] v4l2loopback driver version 0.6.1-droidcam loaded
[   14.675942] ppdev: user-space parallel port driver
[   14.816296] wmi: Mapper loaded
[   14.828782] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.831165] ACPI Warning: 0x0000000000000b00-0x0000000000000b07 SystemIO conflicts with Region \SOR1 1 (20131115/utaddress-251)
[   14.831172] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.834311] sp5100_tco: SP5100/SB800 TCO WatchDog Timer Driver v0.05
[   14.834406] sp5100_tco: PCI Revision ID: 0x42
[   14.834438] sp5100_tco: Using 0xfed80b00 for watchdog MMIO address
[   14.834448] sp5100_tco: Last reboot was not triggered by watchdog.
[   14.834491] sp5100_tco: initialized (0xffffc90000c7cb00). heartbeat=60 sec (nowayout=0)
[   14.844976] MCE: In-kernel MCE decoding enabled.
[   14.850092] cfg80211: Calling CRDA to update world regulatory domain
[   14.850887] EDAC MC: Ver: 3.0.0
[   14.853210] AMD64 EDAC driver v3.4.0
[   14.853232] EDAC amd64: DRAM ECC disabled.
[   14.853240] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   14.853240]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   14.853240]  (Note that use of the override may cause unknown side effects.)
[   14.865447] WARNING! power/level is deprecated; use power/control instead
[   14.869060] type=1400 audit(1426458723.944:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=512 comm="apparmor_parser"
[   14.869066] type=1400 audit(1426458723.944:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=512 comm="apparmor_parser"
[   14.869071] type=1400 audit(1426458723.944:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=512 comm="apparmor_parser"
[   14.869392] type=1400 audit(1426458723.944:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=512 comm="apparmor_parser"
[   14.869397] type=1400 audit(1426458723.944:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=512 comm="apparmor_parser"
[   14.869562] type=1400 audit(1426458723.944:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=512 comm="apparmor_parser"
[   14.872574] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3572, rev 0223 detected
[   14.875577] [drm] radeon kernel modesetting enabled.
[   14.875645] checking generic (c0000000 5b0000) vs hw (c0000000 10000000)
[   14.875647] fb: conflicting fb hw usage radeondrmfb vs VESA VGA - removing generic driver
[   14.875667] Console: switching to colour dummy device 80x25
[   14.877107] [drm] initializing kernel modesetting (CAICOS 0x1002:0x6779 0x1043:0x0461).
[   14.877124] [drm] register mmio base: 0xFEA20000
[   14.877125] [drm] register mmio size: 131072
[   14.877171] radeon 0000:01:00.0: Invalid ROM contents
[   14.877208] ATOM BIOS: 6779HB.13.12.0.48.AS05
[   14.878355] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 0008 detected
[   14.878463] radeon 0000:01:00.0: VRAM: 2048M 0x0000000000000000 - 0x000000007FFFFFFF (2048M used)
[   14.878465] radeon 0000:01:00.0: GTT: 1024M 0x0000000080000000 - 0x00000000BFFFFFFF
[   14.878467] [drm] Detected VRAM RAM=2048M, BAR=256M
[   14.878468] [drm] RAM width 64bits DDR
[   14.878528] [TTM] Zone  kernel: Available graphics memory: 4034644 kiB
[   14.878529] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB
[   14.878531] [TTM] Initializing pool allocator
[   14.878535] [TTM] Initializing DMA pool allocator
[   14.878548] [drm] radeon: 2048M of VRAM memory ready
[   14.878549] [drm] radeon: 1024M of GTT memory ready.
[   14.878563] [drm] Loading CAICOS Microcode
[   14.886718] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   14.892918] kvm: Nested Virtualization enabled
[   14.892924] kvm: Nested Paging enabled
[   15.011812] cfg80211: World regulatory domain updated:
[   15.011819] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   15.011820] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.011822] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.011823] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.011824] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.011825] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.044776] [drm] GART: num cpu pages 262144, num gpu pages 262144
[   15.045814] [drm] enabling PCIE gen 2 link speeds, disable with radeon.pcie_gen2=0
[   15.060885] [drm] PCIE GART of 1024M enabled (table at 0x0000000000273000).
[   15.060990] radeon 0000:01:00.0: WB enabled
[   15.060993] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000080000c00 and cpu addr 0xffff88022febcc00
[   15.060995] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000080000c0c and cpu addr 0xffff88022febcc0c
[   15.062467] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x0000000000072118 and cpu addr 0xffffc90011c32118
[   15.062469] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   15.062470] [drm] Driver supports precise vblank timestamp query.
[   15.062471] radeon 0000:01:00.0: radeon: MSI limited to 32-bit
[   15.062494] radeon 0000:01:00.0: irq 82 for MSI/MSI-X
[   15.062504] radeon 0000:01:00.0: radeon: using MSI.
[   15.062558] [drm] radeon: irq initialized.
[   15.079247] [drm] ring test on 0 succeeded in 3 usecs
[   15.079259] [drm] ring test on 3 succeeded in 6 usecs
[   15.094417] ip_tables: (C) 2000-2006 Netfilter Core Team
[   15.100031] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   15.109479] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   15.196313] Bluetooth: Core ver 2.17
[   15.196332] NET: Registered protocol family 31
[   15.196334] Bluetooth: HCI device and connection manager initialized
[   15.196342] Bluetooth: HCI socket layer initialized
[   15.196344] Bluetooth: L2CAP socket layer initialized
[   15.196354] Bluetooth: SCO socket layer initialized
[   15.198146] input: Wacom Bamboo Pen Pen as /devices/pci0000:00/0000:00:12.2/usb1/1-2/1-2.3/1-2.3:1.0/input/input5
[   15.199088] usbcore: registered new interface driver btusb
[   15.201098] input: Wacom Bamboo Pen Finger as /devices/pci0000:00/0000:00:12.2/usb1/1-2/1-2.3/1-2.3:1.1/input/input6
[   15.201197] usbcore: registered new interface driver wacom
[   15.204071] hidraw: raw HID events driver (C) Jiri Kosina
[   15.205198] uvcvideo: Found UVC 1.00 device FULL HD 1080P Webcam (0bda:58bb)
[   15.205815] usbcore: registered new interface driver usbhid
[   15.205817] usbhid: USB HID core driver
[   15.216880] input: FULL HD 1080P Webcam as /devices/pci0000:00/0000:00:09.0/0000:02:00.0/usb8/8-2/8-2:1.0/input/input7
[   15.216959] usbcore: registered new interface driver uvcvideo
[   15.216961] USB Video Class driver (1.1.1)
[   15.266737] [drm] ring test on 5 succeeded in 2 usecs
[   15.266744] [drm] UVD initialized successfully.
[   15.267054] [drm] Enabling audio 0 support
[   15.267104] [drm] ib test on ring 0 succeeded in 0 usecs
[   15.267150] [drm] ib test on ring 3 succeeded in 0 usecs
[   15.419886] [drm] ib test on ring 5 succeeded
[   15.420306] [drm] Radeon Display Connectors
[   15.420308] [drm] Connector 0:
[   15.420309] [drm]   HDMI-A-1
[   15.420310] [drm]   HPD1
[   15.420311] [drm]   DDC: 0x6460 0x6460 0x6464 0x6464 0x6468 0x6468 0x646c 0x646c
[   15.420312] [drm]   Encoders:
[   15.420313] [drm]     DFP1: INTERNAL_UNIPHY1
[   15.420314] [drm] Connector 1:
[   15.420315] [drm]   DVI-D-1
[   15.420315] [drm]   HPD4
[   15.420316] [drm]   DDC: 0x6450 0x6450 0x6454 0x6454 0x6458 0x6458 0x645c 0x645c
[   15.420317] [drm]   Encoders:
[   15.420318] [drm]     DFP2: INTERNAL_UNIPHY
[   15.420318] [drm] Connector 2:
[   15.420319] [drm]   VGA-1
[   15.420320] [drm]   DDC: 0x6430 0x6430 0x6434 0x6434 0x6438 0x6438 0x643c 0x643c
[   15.420321] [drm]   Encoders:
[   15.420322] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   15.420427] [drm] Internal thermal controller without fan control
[   15.429373] [drm] radeon: dpm initialized
[   15.470947] [drm] fb mappable at 0xC0474000
[   15.470949] [drm] vram apper at 0xC0000000
[   15.470950] [drm] size 7299072
[   15.470951] [drm] fb depth is 24
[   15.470952] [drm]    pitch is 6912
[   15.471069] fbcon: radeondrmfb (fb0) is primary device
[   15.475891] Console: switching to colour frame buffer device 210x65
[   15.478909] radeon 0000:01:00.0: fb0: radeondrmfb frame buffer device
[   15.478910] radeon 0000:01:00.0: registered panic notifier
[   15.478914] [drm] Initialized radeon 2.36.0 20080528 for 0000:01:00.0 on minor 0
[   15.479053] hda-intel 0000:01:00.1: Handle VGA-switcheroo audio client
[   15.479055] hda-intel 0000:01:00.1: Using LPIB position fix
[   15.479097] snd_hda_intel 0000:01:00.1: irq 83 for MSI/MSI-X
[   15.481311] hda-intel 0000:01:00.1: Enable sync_write for stable communication
[   15.484495] HDMI ATI/AMD: no speaker allocation for ELD
[   15.484545] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card2/input8
[   16.340835] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   16.618903] init: failsafe main process (905) killed by TERM signal
[   16.879890] type=1400 audit(1426458725.951:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/tcpdump" pid=1009 comm="apparmor_parser"
[   16.880165] type=1400 audit(1426458725.951:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=1003 comm="apparmor_parser"
[   16.880172] type=1400 audit(1426458725.951:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1003 comm="apparmor_parser"
[   16.880176] type=1400 audit(1426458725.951:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1003 comm="apparmor_parser"
[   16.968885] Bluetooth: RFCOMM TTY layer initialized
[   16.968893] Bluetooth: RFCOMM socket layer initialized
[   16.968897] Bluetooth: RFCOMM ver 1.11
[   17.051523] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.051525] Bluetooth: BNEP filters: protocol multicast
[   17.051532] Bluetooth: BNEP socket layer initialized
[   17.198323] init: cups main process (1016) killed by HUP signal
[   17.198332] init: cups main process ended, respawning
[   18.049896] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2860.bin'
[   18.130354] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.34
[   18.167928] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.168221] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.330994] r8169 0000:06:00.0 eth0: link down
[   18.331049] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.331312] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.657429] init: samba-ad-dc main process (1242) terminated with status 1
[   19.469186] wlan0: authenticate with 00:23:69:b3:4d:e9
[   19.473078] wlan0: send auth to 00:23:69:b3:4d:e9 (try 1/3)
[   19.477417] wlan0: authenticated
[   19.477562] rt2800pci 0000:03:06.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   19.477565] rt2800pci 0000:03:06.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   19.477965] wlan0: associate with 00:23:69:b3:4d:e9 (try 1/3)
[   19.480031] wlan0: RX AssocResp from 00:23:69:b3:4d:e9 (capab=0x411 status=0 aid=4)
[   19.480187] wlan0: associated
[   19.480205] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   19.544704] vboxdrv: Found 8 processor cores.
[   19.544979] vboxdrv: fAsync=0 offMin=0x26e offMax=0x47ca
[   19.545063] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   19.545065] vboxdrv: Successfully loaded version 4.3.22 (interface 0x001a0009).
[   19.752463] vboxpci: IOMMU found
[   20.901621] init: plymouth-upstart-bridge main process ended, respawning
[   22.920569] usbcore: registered new interface driver snd-usb-audio
[   23.968371] usblp 1-2.4:1.1: usblp0: USB Bidirectional printer dev 5 if 1 alt 0 proto 2 vid 0x04A9 pid 0x1741
[   23.971255] usblp 1-2.4:1.2: usblp1: USB Bidirectional printer dev 5 if 2 alt 0 proto 2 vid 0x04A9 pid 0x1741
[   23.971272] usbcore: registered new interface driver usblp
[   31.024412] nf_conntrack: automatic helper assignment is deprecated and it will be removed soon. Use the iptables CT target to attach helpers instead.
[   47.072697] audit_printk_skb: 105 callbacks suppressed
[   47.072701] type=1400 audit(1426458756.090:47): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2690 comm="apparmor_parser"
[   47.072706] type=1400 audit(1426458756.090:48): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2690 comm="apparmor_parser"
[   47.073047] type=1400 audit(1426458756.091:49): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2690 comm="apparmor_parser"
[  305.097556] input: 0C:A6:94:B4:F9:F9 as /devices/virtual/input/input9
```

---

### Post by tgalati4 on 2015-03-15
The kernel expects perfect hardware and when things are not perfect it complains.  Such is life.  A google search shows:

[https://wiki.archlinux.org/index.php/sane](https://wiki.archlinux.org/index.php/sane)

[http://stackoverflow.com/questions/4702216/controlling-a-usb-power-supply-on-off-with-linux](http://stackoverflow.com/questions/4702216/controlling-a-usb-power-supply-on-off-with-linux)

[https://lists.launchpad.net/kernel-packages/msg14768.html](https://lists.launchpad.net/kernel-packages/msg14768.html)

Seems to be related to USB power when suspending.  Does the system leave power to the USB port when asleep so you can charge your phone?  Yes, no?  

Unplug all your USB devices and see if the message goes away.

---

### Post by marseille2 on 2015-03-16
Ok, I'll test it. Thank-you!

---

