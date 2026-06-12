---
title: "IntelHD dosnt works in 16.04.LTS.amd64"
date: 2016-01-16
forum: Hardware
---

### Post by pawe9 on 2016-01-16
Hello

i have 14.04.03 LTS amd64 ubuntu with 3 monitors (2 monitors via ATI HD6450). It works also installation mode 14.04 ;)
 [[IMG]http://obrazki.elektroda.pl/7548702300_1452938546_thumb.jpg[/IMG]]("http://obrazki.elektroda.pl/7548702300_1452938546.png")  

[[IMG]http://obrazki.elektroda.pl/8953001000_1452938804_thumb.jpg[/IMG]]("http://obrazki.elektroda.pl/8953001000_1452938804.png") 

[[IMG]http://obrazki.elektroda.pl/3235529200_1452938876_thumb.jpg[/IMG]]("http://obrazki.elektroda.pl/3235529200_1452938876.png")

dmesg of 14.04.03 :
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.19.0-25-generic (buildd@lgw01-20) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #26~14.04.1-Ubuntu SMP Fri Jul 24 21:16:20 UTC 2015 (Ubuntu 3.19.0-25.26~14.04.1-generic 3.19.8-ckt2)
[    0.000000] Command line: initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- BOOT_IMAGE=/ubnkern 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009dbff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009dc00-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000bee1efff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bee1f000-0x00000000bee20fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bee21000-0x00000000beef5fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000beef6000-0x00000000befe2fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000befe3000-0x00000000befe5fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000befe6000-0x00000000beff1fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000beff2000-0x00000000beff2fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000beff3000-0x00000000beffefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000befff000-0x00000000beffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bf000000-0x00000000bfffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f0000000-0x00000000f7ffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffc00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000023bffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.4 present.
[    0.000000] DMI:                  /DQ35JO, BIOS JOQ3510J.86A.0882.2008.0423.1925 04/23/2008
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] AGP: No AGP bridge found
[    0.000000] e820: last_pfn = 0x23c000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 0BF000000 mask FFF000000 uncachable
[    0.000000]   3 base 100000000 mask F00000000 write-back
[    0.000000]   4 base 200000000 mask F80000000 write-back
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- UC  
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3056MB, range: 16MB, type UC
[    0.000000] reg 3, base: 4GB, range: 4GB, type WB
[    0.000000] reg 4, base: 8GB, range: 2GB, type WB
[    0.000000] total RAM covered: 9200M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 32M     num_reg: 5      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3056MB, range: 16MB, type UC
[    0.000000] reg 3, base: 4GB, range: 4GB, type WB
[    0.000000] reg 4, base: 8GB, range: 2GB, type WB
[    0.000000] e820: update [mem 0xbf000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xbf000 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fe5e0-0x000fe5ef] mapped at [ffff8800000fe5e0]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fd4000, 0x01fd4fff] PGTABLE
[    0.000000] BRK [0x01fd5000, 0x01fd5fff] PGTABLE
[    0.000000] BRK [0x01fd6000, 0x01fd6fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x23be00000-0x23bffffff]
[    0.000000]  [mem 0x23be00000-0x23bffffff] page 2M
[    0.000000] BRK [0x01fd7000, 0x01fd7fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x220000000-0x23bdfffff]
[    0.000000]  [mem 0x220000000-0x23bdfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x200000000-0x21fffffff]
[    0.000000]  [mem 0x200000000-0x21fffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0xbee1efff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0xbedfffff] page 2M
[    0.000000]  [mem 0xbee00000-0xbee1efff] page 4k
[    0.000000] init_memory_mapping: [mem 0xbee21000-0xbeef5fff]
[    0.000000]  [mem 0xbee21000-0xbeef5fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xbefe3000-0xbefe5fff]
[    0.000000]  [mem 0xbefe3000-0xbefe5fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xbeff2000-0xbeff2fff]
[    0.000000]  [mem 0xbeff2000-0xbeff2fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xbefff000-0xbeffffff]
[    0.000000]  [mem 0xbefff000-0xbeffffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x1ffffffff]
[    0.000000]  [mem 0x100000000-0x1ffffffff] page 2M
[    0.000000] BRK [0x01fd8000, 0x01fd8fff] PGTABLE
[    0.000000] BRK [0x01fd9000, 0x01fd9fff] PGTABLE
[    0.000000] RAMDISK: [mem 0x7eb4d000-0x7fffefff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000000FE020 000014 (v00 INTEL )
[    0.000000] ACPI: RSDT 0x00000000BEFFD038 000070 (v01 INTEL  DQ3510J  00000372      01000013)
[    0.000000] ACPI: FACP 0x00000000BEFFC000 000074 (v01 INTEL  DQ3510J  00000372 MSFT 01000013)
[    0.000000] ACPI: DSDT 0x00000000BEFF8000 003D3A (v01 INTEL  DQ3510J  00000372 MSFT 01000013)
[    0.000000] ACPI: FACS 0x00000000BEF82000 000040
[    0.000000] ACPI: APIC 0x00000000BEFF7000 000078 (v01 INTEL  DQ3510J  00000372 MSFT 01000013)
[    0.000000] ACPI: WDDT 0x00000000BEFF6000 000040 (v01 INTEL  DQ3510J  00000372 MSFT 01000013)
[    0.000000] ACPI: MCFG 0x00000000BEFF5000 00003C (v01 INTEL  DQ3510J  00000372 MSFT 01000013)
[    0.000000] ACPI: ASF! 0x00000000BEFF4000 0000A6 (v32 INTEL  DQ3510J  00000372 MSFT 01000013)
[    0.000000] ACPI: HPET 0x00000000BEFF3000 000038 (v01 INTEL  DQ3510J  00000372 MSFT 01000013)
[    0.000000] ACPI: DMAR 0x00000000BEFF1000 000120 (v01 INTEL  DQ3510J  00000372 MSFT 01000013)
[    0.000000] ACPI: ASPT 0x00000000BEFF0000 00002C (v01 INTEL  DQ3510J  00000372 MSFT 01000013)
[    0.000000] ACPI: WDTT 0x00000000BEFEF000 0002CC (v01 INTEL  DQ3510J  00000372 MSFT 01000013)
[    0.000000] ACPI: SSDT 0x00000000BEFEE000 000204 (v01 INTEL  CpuPm    00000372 MSFT 01000013)
[    0.000000] ACPI: SSDT 0x00000000BEFED000 0001F9 (v01 INTEL  Cpu0Ist  00000372 MSFT 01000013)
[    0.000000] ACPI: SSDT 0x00000000BEFEC000 0001F9 (v01 INTEL  Cpu1Ist  00000372 MSFT 01000013)
[    0.000000] ACPI: SSDT 0x00000000BEFEB000 0001F9 (v01 INTEL  Cpu2Ist  00000372 MSFT 01000013)
[    0.000000] ACPI: SSDT 0x00000000BEFEA000 0001F9 (v01 INTEL  Cpu3Ist  00000372 MSFT 01000013)
[    0.000000] ACPI: SSDT 0x00000000BEFE9000 0000DD (v01 INTEL  Cpu0Cst  00000372 MSFT 01000013)
[    0.000000] ACPI: SSDT 0x00000000BEFE8000 0000DD (v01 INTEL  Cpu1Cst  00000372 MSFT 01000013)
[    0.000000] ACPI: SSDT 0x00000000BEFE7000 0000DD (v01 INTEL  Cpu2Cst  00000372 MSFT 01000013)
[    0.000000] ACPI: SSDT 0x00000000BEFE6000 0000DD (v01 INTEL  Cpu3Cst  00000372 MSFT 01000013)
[    0.000000] ACPI: TCPA 0x00000000BEEF7000 000032 (v02 INTEL  TIANO    00000002 MSFT 01000013)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000023bffffff]
[    0.000000] NODE_DATA(0) allocated [mem 0x23bff6000-0x23bffafff]
[    0.000000]  [ffffea0000000000-ffffea0008ffffff] PMD -> [ffff880233600000-ffff88023b5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x23bffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009cfff]
[    0.000000]   node   0: [mem 0x00100000-0xbee1efff]
[    0.000000]   node   0: [mem 0xbee21000-0xbeef5fff]
[    0.000000]   node   0: [mem 0xbefe3000-0xbefe5fff]
[    0.000000]   node   0: [mem 0xbeff2000-0xbeff2fff]
[    0.000000]   node   0: [mem 0xbefff000-0xbeffffff]
[    0.000000]   node   0: [mem 0x100000000-0x23bffffff]
[    0.000000] Initmem setup node 0 [mem 0x00001000-0x23bffffff]
[    0.000000] On node 0 totalpages: 2076309
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3996 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 12156 pages used for memmap
[    0.000000]   DMA32 zone: 777977 pages, LIFO batch:31
[    0.000000]   Normal zone: 20224 pages used for memmap
[    0.000000]   Normal zone: 1294336 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
[    0.000000] smpboot: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009dfff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xbee1f000-0xbee20fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbeef6000-0xbefe2fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbefe6000-0xbeff1fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbeff3000-0xbeffefff]
[    0.000000] PM: Registered nosave memory: [mem 0xbf000000-0xbfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xc0000000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xf7ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xffbfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xffc00000-0xffffffff]
[    0.000000] e820: [mem 0xc0000000-0xefffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 31 pages/cpu @ffff88023bc00000 s86144 r8192 d32640 u524288
[    0.000000] pcpu-alloc: s86144 r8192 d32640 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 2043844
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- BOOT_IMAGE=/ubnkern 
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] AGP: Checking aperture...
[    0.000000] AGP: No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 8069820K/8305236K available (7918K kernel code, 1172K rwdata, 3752K rodata, 1408K init, 1292K bss, 235416K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=4
[    0.000000] NR_IRQS:16640 nr_irqs:456 16
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-3.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 2387.853 MHz processor
[    0.004012] Calibrating delay loop (skipped), value calculated using timer frequency.. 4775.70 BogoMIPS (lpj=9551412)
[    0.004016] pid_max: default: 32768 minimum: 301
[    0.004024] ACPI: Core revision 20141107
[    0.012349] ACPI: All ACPI Tables successfully acquired
[    0.013713] Security Framework initialized
[    0.013737] AppArmor: AppArmor initialized
[    0.013738] Yama: becoming mindful.
[    0.014411] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.018425] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.020466] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.020481] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.020897] Initializing cgroup subsys memory
[    0.020908] Initializing cgroup subsys devices
[    0.020912] Initializing cgroup subsys freezer
[    0.020916] Initializing cgroup subsys net_cls
[    0.020919] Initializing cgroup subsys blkio
[    0.020922] Initializing cgroup subsys perf_event
[    0.020925] Initializing cgroup subsys net_prio
[    0.020928] Initializing cgroup subsys hugetlb
[    0.020957] CPU: Physical Processor ID: 0
[    0.020958] CPU: Processor Core ID: 0
[    0.020961] mce: CPU supports 6 MCE banks
[    0.020969] CPU0: Thermal monitoring enabled (TM2)
[    0.020972] process: using mwait in idle threads
[    0.020978] Last level iTLB entries: 4KB 128, 2MB 4, 4MB 4
[    0.020978] Last level dTLB entries: 4KB 256, 2MB 0, 4MB 32, 1GB 0
[    0.021078] Freeing SMP alternatives memory: 32K (ffffffff81e87000 - ffffffff81e8f000)
[    0.022777] ftrace: allocating 29988 entries in 118 pages
[    0.032105] dmar: Host address width 36
[    0.032109] dmar: DRHD base: 0x000000feb00000 flags: 0x0
[    0.032115] dmar: IOMMU 0: reg_base_addr feb00000 ver 1:0 cap c9008020a30270 ecap 1000
[    0.032117] dmar: DRHD base: 0x000000feb01000 flags: 0x0
[    0.032124] dmar: IOMMU 1: reg_base_addr feb01000 ver 1:0 cap c0000020230270 ecap 1000
[    0.032125] dmar: DRHD base: 0x000000feb02000 flags: 0x0
[    0.032131] dmar: IOMMU 2: reg_base_addr feb02000 ver 1:0 cap c0000020230270 ecap 1000
[    0.032133] dmar: DRHD base: 0x000000feb03000 flags: 0x1
[    0.032137] dmar: IOMMU 3: reg_base_addr feb03000 ver 1:0 cap c9008020230270 ecap 1000
[    0.032139] dmar: RMRR base: 0x000000000e0000 end: 0x000000000effff
[    0.032141] dmar: RMRR base: 0x000000bf600000 end: 0x000000bfffffff
[    0.032588] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.075645] smpboot: CPU0: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz (fam: 06, model: 0f, stepping: 0b)
[    0.076000] Performance Events: PEBS fmt0+, 4-deep LBR, Core2 events, Intel PMU driver.
[    0.076000] perf_event_intel: PEBS disabled due to CPU errata
[    0.076000] ... version:                2
[    0.076000] ... bit width:              40
[    0.076000] ... generic registers:      2
[    0.076000] ... value mask:             000000ffffffffff
[    0.076000] ... max period:             000000007fffffff
[    0.076000] ... fixed-purpose events:   3
[    0.076000] ... event mask:             0000000700000003
[    0.076000] x86: Booting SMP configuration:
[    0.076000] .... node  #0, CPUs:      #1
[    0.086386] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.086516]  #2 #3
[    0.112013] x86: Booted up 1 node, 4 CPUs
[    0.112017] smpboot: Total of 4 processors activated (19102.82 BogoMIPS)
[    0.116175] devtmpfs: initialized
[    0.122320] evm: security.selinux
[    0.122322] evm: security.SMACK64
[    0.122323] evm: security.SMACK64EXEC
[    0.122324] evm: security.SMACK64TRANSMUTE
[    0.122325] evm: security.SMACK64MMAP
[    0.122327] evm: security.ima
[    0.122328] evm: security.capability
[    0.122349] PM: Registering ACPI NVS region [mem 0xbeef6000-0xbefe2fff] (970752 bytes)
[    0.122349] pinctrl core: initialized pinctrl subsystem
[    0.122349] RTC time: 17:44:03, date: 01/15/16
[    0.122349] NET: Registered protocol family 16
[    0.124010] cpuidle: using governor ladder
[    0.128009] cpuidle: using governor menu
[    0.128085] ACPI: bus type PCI registered
[    0.128089] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.128219] PCI: MMCONFIG for domain 0000 [bus 00-7f] at [mem 0xf0000000-0xf7ffffff] (base 0xf0000000)
[    0.128222] PCI: MMCONFIG at [mem 0xf0000000-0xf7ffffff] reserved in E820
[    0.128431] PCI: Using configuration type 1 for base access
[    0.140155] ACPI: Added _OSI(Module Device)
[    0.140158] ACPI: Added _OSI(Processor Device)
[    0.140160] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.140166] ACPI: Added _OSI(Processor Aggregator Device)
[    0.142768] ACPI: Interpreter enabled
[    0.142777] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20141107/hwxface-580)
[    0.142791] ACPI: (supports S0 S1 S3 S4 S5)
[    0.142792] ACPI: Using IOAPIC for interrupt routing
[    0.142817] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.144200] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.144207] acpi PNP0A03:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.144212] acpi PNP0A03:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[    0.145264] acpi PNP0A03:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-7f] only partially covers this bridge
[    0.145437] PCI host bridge to bus 0000:00
[    0.145441] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.145443] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.145445] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.145451] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.145453] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000effff]
[    0.145455] pci_bus 0000:00: root bus resource [mem 0xf8000000-0xfeafffff]
[    0.145457] pci_bus 0000:00: root bus resource [mem 0xc0000000-0xefffffff]
[    0.145467] pci 0000:00:00.0: [8086:29b0] type 00 class 0x060000
[    0.145574] pci 0000:00:01.0: [8086:29b1] type 01 class 0x060400
[    0.145617] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.145659] pci 0000:00:01.0: System wakeup disabled by ACPI
[    0.145707] pci 0000:00:02.0: [8086:29b2] type 00 class 0x038000
[    0.145717] pci 0000:00:02.0: reg 0x10: [mem 0xe0400000-0xe047ffff]
[    0.145723] pci 0000:00:02.0: reg 0x14: [io  0x3430-0x3437]
[    0.145729] pci 0000:00:02.0: reg 0x18: [mem 0xd0000000-0xdfffffff pref]
[    0.145734] pci 0000:00:02.0: reg 0x1c: [mem 0xe0200000-0xe02fffff]
[    0.145838] pci 0000:00:03.0: [8086:29b4] type 00 class 0x078000
[    0.145851] pci 0000:00:03.0: reg 0x10: [mem 0xe04a6100-0xe04a610f 64bit]
[    0.145891] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    0.145999] pci 0000:00:19.0: [8086:10bd] type 00 class 0x020000
[    0.146016] pci 0000:00:19.0: reg 0x10: [mem 0xe0480000-0xe049ffff]
[    0.146024] pci 0000:00:19.0: reg 0x14: [mem 0xe04a4000-0xe04a4fff]
[    0.146032] pci 0000:00:19.0: reg 0x18: [io  0x3400-0x341f]
[    0.146093] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.146137] pci 0000:00:19.0: System wakeup disabled by ACPI
[    0.146185] pci 0000:00:1a.0: [8086:2937] type 00 class 0x0c0300
[    0.146225] pci 0000:00:1a.0: reg 0x20: [io  0x30e0-0x30ff]
[    0.146315] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.146364] pci 0000:00:1a.1: [8086:2938] type 00 class 0x0c0300
[    0.146404] pci 0000:00:1a.1: reg 0x20: [io  0x30c0-0x30df]
[    0.146492] pci 0000:00:1a.1: System wakeup disabled by ACPI
[    0.146544] pci 0000:00:1a.2: [8086:2939] type 00 class 0x0c0300
[    0.146584] pci 0000:00:1a.2: reg 0x20: [io  0x30a0-0x30bf]
[    0.146671] pci 0000:00:1a.2: System wakeup disabled by ACPI
[    0.146729] pci 0000:00:1a.7: [8086:293c] type 00 class 0x0c0320
[    0.146749] pci 0000:00:1a.7: reg 0x10: [mem 0xe04a5c00-0xe04a5fff]
[    0.146836] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.146897] pci 0000:00:1a.7: System wakeup disabled by ACPI
[    0.146951] pci 0000:00:1b.0: [8086:293e] type 00 class 0x040300
[    0.146967] pci 0000:00:1b.0: reg 0x10: [mem 0xe04a0000-0xe04a3fff 64bit]
[    0.147037] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.147101] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.147153] pci 0000:00:1c.0: [8086:2940] type 01 class 0x060400
[    0.147220] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.147265] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.147315] pci 0000:00:1c.1: [8086:2942] type 01 class 0x060400
[    0.147382] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.147427] pci 0000:00:1c.1: System wakeup disabled by ACPI
[    0.147476] pci 0000:00:1c.2: [8086:2944] type 01 class 0x060400
[    0.147548] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.147593] pci 0000:00:1c.2: System wakeup disabled by ACPI
[    0.147644] pci 0000:00:1c.3: [8086:2946] type 01 class 0x060400
[    0.147710] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.147755] pci 0000:00:1c.3: System wakeup disabled by ACPI
[    0.147804] pci 0000:00:1c.4: [8086:2948] type 01 class 0x060400
[    0.147870] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.147916] pci 0000:00:1c.4: System wakeup disabled by ACPI
[    0.147967] pci 0000:00:1d.0: [8086:2934] type 00 class 0x0c0300
[    0.148008] pci 0000:00:1d.0: reg 0x20: [io  0x3080-0x309f]
[    0.148097] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.148148] pci 0000:00:1d.1: [8086:2935] type 00 class 0x0c0300
[    0.148188] pci 0000:00:1d.1: reg 0x20: [io  0x3060-0x307f]
[    0.148277] pci 0000:00:1d.1: System wakeup disabled by ACPI
[    0.148326] pci 0000:00:1d.2: [8086:2936] type 00 class 0x0c0300
[    0.148366] pci 0000:00:1d.2: reg 0x20: [io  0x3040-0x305f]
[    0.148454] pci 0000:00:1d.2: System wakeup disabled by ACPI
[    0.148512] pci 0000:00:1d.7: [8086:293a] type 00 class 0x0c0320
[    0.148533] pci 0000:00:1d.7: reg 0x10: [mem 0xe04a5800-0xe04a5bff]
[    0.148620] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.148681] pci 0000:00:1d.7: System wakeup disabled by ACPI
[    0.148735] pci 0000:00:1e.0: [8086:244e] type 01 class 0x060401
[    0.148818] pci 0000:00:1e.0: System wakeup disabled by ACPI
[    0.148869] pci 0000:00:1f.0: [8086:2914] type 00 class 0x060100
[    0.148945] pci 0000:00:1f.0: can't claim BAR 13 [io  0x0400-0x047f]: address conflict with ACPI PM1a_EVT_BLK [io  0x0400-0x0403]
[    0.148950] pci 0000:00:1f.0: quirk: [io  0x0500-0x053f] claimed by ICH6 GPIO
[    0.148954] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0680 (mask 007f)
[    0.149065] pci 0000:00:1f.2: [8086:2922] type 00 class 0x010601
[    0.149083] pci 0000:00:1f.2: reg 0x10: [io  0x3428-0x342f]
[    0.149091] pci 0000:00:1f.2: reg 0x14: [io  0x343c-0x343f]
[    0.149098] pci 0000:00:1f.2: reg 0x18: [io  0x3420-0x3427]
[    0.149106] pci 0000:00:1f.2: reg 0x1c: [io  0x3438-0x343b]
[    0.149113] pci 0000:00:1f.2: reg 0x20: [io  0x3020-0x303f]
[    0.149121] pci 0000:00:1f.2: reg 0x24: [mem 0xe04a5000-0xe04a57ff]
[    0.149166] pci 0000:00:1f.2: PME# supported from D3hot
[    0.149252] pci 0000:00:1f.3: [8086:2930] type 00 class 0x0c0500
[    0.149266] pci 0000:00:1f.3: reg 0x10: [mem 0xe04a6000-0xe04a60ff 64bit]
[    0.149286] pci 0000:00:1f.3: reg 0x20: [io  0x3000-0x301f]
[    0.149425] pci 0000:01:00.0: [1002:6779] type 00 class 0x030000
[    0.149442] pci 0000:01:00.0: reg 0x10: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.149454] pci 0000:01:00.0: reg 0x18: [mem 0xe0300000-0xe031ffff 64bit]
[    0.149462] pci 0000:01:00.0: reg 0x20: [io  0x2000-0x20ff]
[    0.149487] pci 0000:01:00.0: reg 0x30: [mem 0xfffe0000-0xffffffff pref]
[    0.149529] pci 0000:01:00.0: supports D1 D2
[    0.149585] pci 0000:01:00.1: [1002:aa98] type 00 class 0x040300
[    0.149601] pci 0000:01:00.1: reg 0x10: [mem 0xe0320000-0xe0323fff 64bit]
[    0.149673] pci 0000:01:00.1: supports D1 D2
[    0.149740] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.149744] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    0.149747] pci 0000:00:01.0:   bridge window [mem 0xe0300000-0xe03fffff]
[    0.149751] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.149806] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.149869] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.149949] pci 0000:04:00.0: [11ab:6101] type 00 class 0x01018f
[    0.149968] pci 0000:04:00.0: reg 0x10: [io  0x1018-0x101f]
[    0.149980] pci 0000:04:00.0: reg 0x14: [io  0x1024-0x1027]
[    0.149991] pci 0000:04:00.0: reg 0x18: [io  0x1010-0x1017]
[    0.150003] pci 0000:04:00.0: reg 0x1c: [io  0x1020-0x1023]
[    0.150014] pci 0000:04:00.0: reg 0x20: [io  0x1000-0x100f]
[    0.150026] pci 0000:04:00.0: reg 0x24: [mem 0xe0100000-0xe01001ff]
[    0.150099] pci 0000:04:00.0: supports D1
[    0.150101] pci 0000:04:00.0: PME# supported from D0 D1 D3hot
[    0.150160] pci 0000:04:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.150169] pci 0000:00:1c.2: PCI bridge to [bus 04]
[    0.150172] pci 0000:00:1c.2:   bridge window [io  0x1000-0x1fff]
[    0.150176] pci 0000:00:1c.2:   bridge window [mem 0xe0100000-0xe01fffff]
[    0.150234] pci 0000:00:1c.3: PCI bridge to [bus 05]
[    0.150297] pci 0000:00:1c.4: PCI bridge to [bus 06]
[    0.150354] pci 0000:07:03.0: [11c1:5811] type 00 class 0x0c0010
[    0.150370] pci 0000:07:03.0: reg 0x10: [mem 0xe0000000-0xe0000fff]
[    0.150443] pci 0000:07:03.0: supports D1 D2
[    0.150446] pci 0000:07:03.0: PME# supported from D0 D1 D2 D3hot
[    0.150528] pci 0000:00:1e.0: PCI bridge to [bus 07] (subtractive decode)
[    0.150534] pci 0000:00:1e.0:   bridge window [mem 0xe0000000-0xe00fffff]
[    0.150539] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.150542] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.150544] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.150546] pci 0000:00:1e.0:   bridge window [mem 0x000e0000-0x000effff] (subtractive decode)
[    0.150548] pci 0000:00:1e.0:   bridge window [mem 0xf8000000-0xfeafffff] (subtractive decode)
[    0.150551] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xefffffff] (subtractive decode)
[    0.150649] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    0.150711] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *9 10 11 12)
[    0.150771] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[    0.150833] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[    0.150892] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 *10 11 12)
[    0.150950] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 *9 10 11 12)
[    0.151011] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 *10 11 12)
[    0.151069] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 *11 12)
[    0.151576] ACPI: Enabled 4 GPEs in block 00 to 3F
[    0.152024] vgaarb: setting as boot device: PCI:0000:01:00.0
[    0.152028] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.152031] vgaarb: loaded
[    0.152033] vgaarb: bridge control possible 0000:01:00.0
[    0.152033] SCSI subsystem initialized
[    0.152042] libata version 3.00 loaded.
[    0.152069] ACPI: bus type USB registered
[    0.152094] usbcore: registered new interface driver usbfs
[    0.152105] usbcore: registered new interface driver hub
[    0.152139] usbcore: registered new device driver usb
[    0.152194] PCI: Using ACPI for IRQ routing
[    0.154659] PCI: pci_cache_line_size set to 64 bytes
[    0.154718] e820: reserve RAM buffer [mem 0x0009dc00-0x0009ffff]
[    0.154720] e820: reserve RAM buffer [mem 0xbee1f000-0xbfffffff]
[    0.154722] e820: reserve RAM buffer [mem 0xbeef6000-0xbfffffff]
[    0.154724] e820: reserve RAM buffer [mem 0xbefe6000-0xbfffffff]
[    0.154726] e820: reserve RAM buffer [mem 0xbeff3000-0xbfffffff]
[    0.154727] e820: reserve RAM buffer [mem 0xbf000000-0xbfffffff]
[    0.154868] NetLabel: Initializing
[    0.154870] NetLabel:  domain hash size = 128
[    0.154871] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.154887] NetLabel:  unlabeled traffic allowed by default
[    0.156057] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.156061] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.156066] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.160051] Switched to clocksource hpet
[    0.168441] AppArmor: AppArmor Filesystem Enabled
[    0.168532] pnp: PnP ACPI init
[    0.168653] system 00:00: [mem 0xf0000000-0xf7ffffff] has been reserved
[    0.168656] system 00:00: [mem 0xfeb00000-0xfeb03fff] could not be reserved
[    0.168659] system 00:00: [mem 0xfed13000-0xfed13fff] has been reserved
[    0.168662] system 00:00: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.168664] system 00:00: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.168667] system 00:00: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.168669] system 00:00: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.168672] system 00:00: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.168674] system 00:00: [mem 0xfed45000-0xfed99fff] has been reserved
[    0.168677] system 00:00: [mem 0x000c0000-0x000dffff] could not be reserved
[    0.168679] system 00:00: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.168682] system 00:00: [mem 0xffc00000-0xffffffff] has been reserved
[    0.168686] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.168848] pnp 00:01: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.168911] system 00:02: [io  0x0500-0x053f] has been reserved
[    0.168914] system 00:02: [io  0x0400-0x047f] could not be reserved
[    0.168917] system 00:02: [io  0x0680-0x06ff] has been reserved
[    0.168920] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.168972] pnp 00:03: Plug and Play ACPI device, IDs WEC1000 PNP0c31 (active)
[    0.169038] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.169350] pnp 00:05: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.169437] pnp: PnP ACPI: found 6 devices
[    0.177609] pci 0000:01:00.0: can't claim BAR 6 [mem 0xfffe0000-0xffffffff pref]: no compatible bridge window
[    0.177628] pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 02] add_size 1000
[    0.177632] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 02] add_size 200000
[    0.177635] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff] to [bus 02] add_size 200000
[    0.177642] pci 0000:00:1c.1: bridge window [io  0x1000-0x0fff] to [bus 03] add_size 1000
[    0.177645] pci 0000:00:1c.1: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 03] add_size 200000
[    0.177648] pci 0000:00:1c.1: bridge window [mem 0x00100000-0x000fffff] to [bus 03] add_size 200000
[    0.177656] pci 0000:00:1c.2: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 04] add_size 200000
[    0.177663] pci 0000:00:1c.3: bridge window [io  0x1000-0x0fff] to [bus 05] add_size 1000
[    0.177666] pci 0000:00:1c.3: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 05] add_size 200000
[    0.177669] pci 0000:00:1c.3: bridge window [mem 0x00100000-0x000fffff] to [bus 05] add_size 200000
[    0.177676] pci 0000:00:1c.4: bridge window [io  0x1000-0x0fff] to [bus 06] add_size 1000
[    0.177679] pci 0000:00:1c.4: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 06] add_size 200000
[    0.177682] pci 0000:00:1c.4: bridge window [mem 0x00100000-0x000fffff] to [bus 06] add_size 200000
[    0.177694] pci 0000:00:1f.0: BAR 13: [io  0x0400-0x047f] has bogus alignment
[    0.177700] pci 0000:00:1c.0: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    0.177703] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.177705] pci 0000:00:1c.1: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    0.177708] pci 0000:00:1c.1: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.177710] pci 0000:00:1c.2: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.177713] pci 0000:00:1c.3: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    0.177715] pci 0000:00:1c.3: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.177718] pci 0000:00:1c.4: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    0.177720] pci 0000:00:1c.4: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.177722] pci 0000:00:1c.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.177725] pci 0000:00:1c.1: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.177727] pci 0000:00:1c.3: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.177729] pci 0000:00:1c.4: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.177736] pci 0000:00:1c.0: BAR 14: assigned [mem 0xf8000000-0xf81fffff]
[    0.177741] pci 0000:00:1c.0: BAR 15: assigned [mem 0xf8200000-0xf83fffff 64bit pref]
[    0.177744] pci 0000:00:1c.1: BAR 14: assigned [mem 0xf8400000-0xf85fffff]
[    0.177749] pci 0000:00:1c.1: BAR 15: assigned [mem 0xf8600000-0xf87fffff 64bit pref]
[    0.177753] pci 0000:00:1c.2: BAR 15: assigned [mem 0xf8800000-0xf89fffff 64bit pref]
[    0.177756] pci 0000:00:1c.3: BAR 14: assigned [mem 0xf8a00000-0xf8bfffff]
[    0.177760] pci 0000:00:1c.3: BAR 15: assigned [mem 0xf8c00000-0xf8dfffff 64bit pref]
[    0.177763] pci 0000:00:1c.4: BAR 14: assigned [mem 0xf8e00000-0xf8ffffff]
[    0.177768] pci 0000:00:1c.4: BAR 15: assigned [mem 0xf9000000-0xf91fffff 64bit pref]
[    0.177771] pci 0000:00:1c.0: BAR 13: assigned [io  0x4000-0x4fff]
[    0.177774] pci 0000:00:1c.1: BAR 13: assigned [io  0x5000-0x5fff]
[    0.177777] pci 0000:00:1c.3: BAR 13: assigned [io  0x6000-0x6fff]
[    0.177780] pci 0000:00:1c.4: BAR 13: assigned [io  0x7000-0x7fff]
[    0.177786] pci 0000:01:00.0: BAR 6: assigned [mem 0xe0340000-0xe035ffff pref]
[    0.177789] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.177792] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    0.177795] pci 0000:00:01.0:   bridge window [mem 0xe0300000-0xe03fffff]
[    0.177799] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.177803] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.177806] pci 0000:00:1c.0:   bridge window [io  0x4000-0x4fff]
[    0.177810] pci 0000:00:1c.0:   bridge window [mem 0xf8000000-0xf81fffff]
[    0.177814] pci 0000:00:1c.0:   bridge window [mem 0xf8200000-0xf83fffff 64bit pref]
[    0.177819] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.177822] pci 0000:00:1c.1:   bridge window [io  0x5000-0x5fff]
[    0.177827] pci 0000:00:1c.1:   bridge window [mem 0xf8400000-0xf85fffff]
[    0.177830] pci 0000:00:1c.1:   bridge window [mem 0xf8600000-0xf87fffff 64bit pref]
[    0.177836] pci 0000:00:1c.2: PCI bridge to [bus 04]
[    0.177839] pci 0000:00:1c.2:   bridge window [io  0x1000-0x1fff]
[    0.177843] pci 0000:00:1c.2:   bridge window [mem 0xe0100000-0xe01fffff]
[    0.177847] pci 0000:00:1c.2:   bridge window [mem 0xf8800000-0xf89fffff 64bit pref]
[    0.177852] pci 0000:00:1c.3: PCI bridge to [bus 05]
[    0.177855] pci 0000:00:1c.3:   bridge window [io  0x6000-0x6fff]
[    0.177860] pci 0000:00:1c.3:   bridge window [mem 0xf8a00000-0xf8bfffff]
[    0.177863] pci 0000:00:1c.3:   bridge window [mem 0xf8c00000-0xf8dfffff 64bit pref]
[    0.177869] pci 0000:00:1c.4: PCI bridge to [bus 06]
[    0.177871] pci 0000:00:1c.4:   bridge window [io  0x7000-0x7fff]
[    0.177876] pci 0000:00:1c.4:   bridge window [mem 0xf8e00000-0xf8ffffff]
[    0.177880] pci 0000:00:1c.4:   bridge window [mem 0xf9000000-0xf91fffff 64bit pref]
[    0.177885] pci 0000:00:1e.0: PCI bridge to [bus 07]
[    0.177890] pci 0000:00:1e.0:   bridge window [mem 0xe0000000-0xe00fffff]
[    0.177898] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.177900] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.177902] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.177904] pci_bus 0000:00: resource 7 [mem 0x000e0000-0x000effff]
[    0.177906] pci_bus 0000:00: resource 8 [mem 0xf8000000-0xfeafffff]
[    0.177908] pci_bus 0000:00: resource 9 [mem 0xc0000000-0xefffffff]
[    0.177911] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
[    0.177913] pci_bus 0000:01: resource 1 [mem 0xe0300000-0xe03fffff]
[    0.177915] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.177917] pci_bus 0000:02: resource 0 [io  0x4000-0x4fff]
[    0.177919] pci_bus 0000:02: resource 1 [mem 0xf8000000-0xf81fffff]
[    0.177921] pci_bus 0000:02: resource 2 [mem 0xf8200000-0xf83fffff 64bit pref]
[    0.177924] pci_bus 0000:03: resource 0 [io  0x5000-0x5fff]
[    0.177926] pci_bus 0000:03: resource 1 [mem 0xf8400000-0xf85fffff]
[    0.177928] pci_bus 0000:03: resource 2 [mem 0xf8600000-0xf87fffff 64bit pref]
[    0.177930] pci_bus 0000:04: resource 0 [io  0x1000-0x1fff]
[    0.177932] pci_bus 0000:04: resource 1 [mem 0xe0100000-0xe01fffff]
[    0.177934] pci_bus 0000:04: resource 2 [mem 0xf8800000-0xf89fffff 64bit pref]
[    0.177936] pci_bus 0000:05: resource 0 [io  0x6000-0x6fff]
[    0.177938] pci_bus 0000:05: resource 1 [mem 0xf8a00000-0xf8bfffff]
[    0.177940] pci_bus 0000:05: resource 2 [mem 0xf8c00000-0xf8dfffff 64bit pref]
[    0.177942] pci_bus 0000:06: resource 0 [io  0x7000-0x7fff]
[    0.177944] pci_bus 0000:06: resource 1 [mem 0xf8e00000-0xf8ffffff]
[    0.177947] pci_bus 0000:06: resource 2 [mem 0xf9000000-0xf91fffff 64bit pref]
[    0.177949] pci_bus 0000:07: resource 1 [mem 0xe0000000-0xe00fffff]
[    0.177951] pci_bus 0000:07: resource 4 [io  0x0000-0x0cf7]
[    0.177953] pci_bus 0000:07: resource 5 [io  0x0d00-0xffff]
[    0.177955] pci_bus 0000:07: resource 6 [mem 0x000a0000-0x000bffff]
[    0.177957] pci_bus 0000:07: resource 7 [mem 0x000e0000-0x000effff]
[    0.177959] pci_bus 0000:07: resource 8 [mem 0xf8000000-0xfeafffff]
[    0.177961] pci_bus 0000:07: resource 9 [mem 0xc0000000-0xefffffff]
[    0.177993] NET: Registered protocol family 2
[    0.178258] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
[    0.178521] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.178856] TCP: Hash tables configured (established 65536 bind 65536)
[    0.178896] TCP: reno registered
[    0.178910] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.178968] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.179083] NET: Registered protocol family 1
[    0.181265] pci 0000:01:00.0: Video device with shadowed ROM
[    0.181275] PCI: CLS 64 bytes, default 64
[    0.181356] Trying to unpack rootfs image as initramfs...
[    4.904730] Freeing initrd memory: 21192K (ffff88007eb4d000 - ffff88007ffff000)
[    4.904786] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    4.904789] software IO TLB [mem 0xbae1f000-0xbee1f000] (64MB) mapped at [ffff8800bae1f000-ffff8800bee1efff]
[    4.905113] microcode: CPU0 sig=0x6fb, pf=0x10, revision=0xb6
[    4.905130] microcode: CPU1 sig=0x6fb, pf=0x10, revision=0xb6
[    4.905146] microcode: CPU2 sig=0x6fb, pf=0x10, revision=0xb6
[    4.905160] microcode: CPU3 sig=0x6fb, pf=0x10, revision=0xb6
[    4.905271] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    4.905332] Scanning for low memory corruption every 60 seconds
[    4.905675] futex hash table entries: 1024 (order: 4, 65536 bytes)
[    4.905697] Initialise system trusted keyring
[    4.905719] audit: initializing netlink subsys (disabled)
[    4.905742] audit: type=2000 audit(1452879847.900:1): initialized
[    4.906122] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    4.908241] zpool: loaded
[    4.908244] zbud: loaded
[    4.908477] VFS: Disk quotas dquot_6.5.2
[    4.908543] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    4.909253] fuse init (API version 7.23)
[    4.909501] Key type big_key registered
[    4.910075] Key type asymmetric registered
[    4.910081] Asymmetric key parser 'x509' registered
[    4.910153] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    4.910214] io scheduler noop registered
[    4.910219] io scheduler deadline registered (default)
[    4.910280] io scheduler cfq registered
[    4.910640] pcieport 0000:00:1c.0: enabling device (0000 -> 0003)
[    4.910834] pcieport 0000:00:1c.1: enabling device (0000 -> 0003)
[    4.911210] pcieport 0000:00:1c.3: enabling device (0000 -> 0003)
[    4.911401] pcieport 0000:00:1c.4: enabling device (0000 -> 0003)
[    4.911602] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    4.911623] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    4.911668] intel_idle: does not run on family 6 model 15
[    4.911752] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
[    4.911756] ACPI: Sleep Button [SLPB]
[    4.911815] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    4.911818] ACPI: Power Button [PWRF]
[    4.911952] Monitor-Mwait will be used to enter C-1 state
[    4.912443] GHES: HEST is not enabled!
[    4.912603] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    4.932985] 00:05: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    4.934819] Linux agpgart interface v0.103
[    4.934905] agpgart-intel 0000:00:00.0: Intel Q35 Chipset
[    4.934922] agpgart-intel 0000:00:00.0: detected gtt size: 524288K total, 262144K mappable
[    4.936084] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    4.936218] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    4.936444] tpm_tis 00:03: 1.2 TPM (device-id 0xFE, rev-id 70)
[    5.033693] brd: module loaded
[    5.034509] loop: module loaded
[    5.034800] libphy: Fixed MDIO Bus: probed
[    5.034804] tun: Universal TUN/TAP device driver, 1.6
[    5.034806] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    5.034863] PPP generic driver version 2.4.2
[    5.034955] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    5.034961] ehci-pci: EHCI PCI platform driver
[    5.035131] ehci-pci 0000:00:1a.7: EHCI Host Controller
[    5.035138] ehci-pci 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    5.035151] ehci-pci 0000:00:1a.7: debug port 1
[    5.039052] ehci-pci 0000:00:1a.7: cache line size of 64 is not supported
[    5.039069] ehci-pci 0000:00:1a.7: irq 17, io mem 0xe04a5c00
[    5.048026] ehci-pci 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    5.048088] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    5.048092] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    5.048095] usb usb1: Product: EHCI Host Controller
[    5.048098] usb usb1: Manufacturer: Linux 3.19.0-25-generic ehci_hcd
[    5.048101] usb usb1: SerialNumber: 0000:00:1a.7
[    5.048266] hub 1-0:1.0: USB hub found
[    5.048274] hub 1-0:1.0: 6 ports detected
[    5.048588] ehci-pci 0000:00:1d.7: EHCI Host Controller
[    5.048595] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    5.048606] ehci-pci 0000:00:1d.7: debug port 1
[    5.052510] ehci-pci 0000:00:1d.7: cache line size of 64 is not supported
[    5.052524] ehci-pci 0000:00:1d.7: irq 23, io mem 0xe04a5800
[    5.064026] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    5.064075] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    5.064079] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    5.064082] usb usb2: Product: EHCI Host Controller
[    5.064085] usb usb2: Manufacturer: Linux 3.19.0-25-generic ehci_hcd
[    5.064088] usb usb2: SerialNumber: 0000:00:1d.7
[    5.064242] hub 2-0:1.0: USB hub found
[    5.064249] hub 2-0:1.0: 6 ports detected
[    5.064421] ehci-platform: EHCI generic platform driver
[    5.064433] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    5.064438] ohci-pci: OHCI PCI platform driver
[    5.064453] ohci-platform: OHCI generic platform driver
[    5.064463] uhci_hcd: USB Universal Host Controller Interface driver
[    5.064605] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    5.064611] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    5.064617] uhci_hcd 0000:00:1a.0: detected 2 ports
[    5.064642] uhci_hcd 0000:00:1a.0: irq 18, io base 0x000030e0
[    5.064692] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    5.064695] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    5.064697] usb usb3: Product: UHCI Host Controller
[    5.064699] usb usb3: Manufacturer: Linux 3.19.0-25-generic uhci_hcd
[    5.064701] usb usb3: SerialNumber: 0000:00:1a.0
[    5.064813] hub 3-0:1.0: USB hub found
[    5.064820] hub 3-0:1.0: 2 ports detected
[    5.065047] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    5.065053] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    5.065059] uhci_hcd 0000:00:1a.1: detected 2 ports
[    5.065085] uhci_hcd 0000:00:1a.1: irq 21, io base 0x000030c0
[    5.065130] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    5.065133] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    5.065135] usb usb4: Product: UHCI Host Controller
[    5.065137] usb usb4: Manufacturer: Linux 3.19.0-25-generic uhci_hcd
[    5.065139] usb usb4: SerialNumber: 0000:00:1a.1
[    5.065248] hub 4-0:1.0: USB hub found
[    5.065256] hub 4-0:1.0: 2 ports detected
[    5.065476] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    5.065485] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    5.065491] uhci_hcd 0000:00:1a.2: detected 2 ports
[    5.065508] uhci_hcd 0000:00:1a.2: irq 17, io base 0x000030a0
[    5.065550] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    5.065553] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    5.065555] usb usb5: Product: UHCI Host Controller
[    5.065557] usb usb5: Manufacturer: Linux 3.19.0-25-generic uhci_hcd
[    5.065559] usb usb5: SerialNumber: 0000:00:1a.2
[    5.065669] hub 5-0:1.0: USB hub found
[    5.065676] hub 5-0:1.0: 2 ports detected
[    5.065896] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    5.065902] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    5.065908] uhci_hcd 0000:00:1d.0: detected 2 ports
[    5.065925] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00003080
[    5.065967] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    5.065970] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    5.065972] usb usb6: Product: UHCI Host Controller
[    5.065974] usb usb6: Manufacturer: Linux 3.19.0-25-generic uhci_hcd
[    5.065976] usb usb6: SerialNumber: 0000:00:1d.0
[    5.066086] hub 6-0:1.0: USB hub found
[    5.066093] hub 6-0:1.0: 2 ports detected
[    5.066316] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    5.066323] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    5.066329] uhci_hcd 0000:00:1d.1: detected 2 ports
[    5.066354] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00003060
[    5.066396] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    5.066399] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    5.066401] usb usb7: Product: UHCI Host Controller
[    5.066403] usb usb7: Manufacturer: Linux 3.19.0-25-generic uhci_hcd
[    5.066405] usb usb7: SerialNumber: 0000:00:1d.1
[    5.066525] hub 7-0:1.0: USB hub found
[    5.066532] hub 7-0:1.0: 2 ports detected
[    5.066753] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    5.066761] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    5.066767] uhci_hcd 0000:00:1d.2: detected 2 ports
[    5.066784] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00003040
[    5.066828] usb usb8: New USB device found, idVendor=1d6b, idProduct=0001
[    5.066830] usb usb8: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    5.066832] usb usb8: Product: UHCI Host Controller
[    5.066834] usb usb8: Manufacturer: Linux 3.19.0-25-generic uhci_hcd
[    5.066836] usb usb8: SerialNumber: 0000:00:1d.2
[    5.066945] hub 8-0:1.0: USB hub found
[    5.066952] hub 8-0:1.0: 2 ports detected
[    5.067098] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    5.070269] serio: i8042 KBD port at 0x60,0x64 irq 1
[    5.070279] serio: i8042 AUX port at 0x60,0x64 irq 12
[    5.070490] mousedev: PS/2 mouse device common for all mice
[    5.070734] rtc_cmos 00:01: RTC can wake from S4
[    5.070882] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    5.070914] rtc_cmos 00:01: alarms up to one month, 114 bytes nvram, hpet irqs
[    5.070944] i2c /dev entries driver
[    5.071034] device-mapper: uevent: version 1.0.3
[    5.071136] device-mapper: ioctl: 4.29.0-ioctl (2014-10-28) initialised: dm-devel@redhat.com
[    5.071161] ledtrig-cpu: registered to indicate activity on CPUs
[    5.071349] PCCT header not found.
[    5.071350] ACPI PCC probe failed.
[    5.071498] TCP: cubic registered
[    5.071639] NET: Registered protocol family 10
[    5.071970] NET: Registered protocol family 17
[    5.071981] Key type dns_resolver registered
[    5.072471] Loading compiled-in X.509 certificates
[    5.073662] Loaded X.509 cert 'Magrathea: Glacier signing key: 6aaa11d18c2d3a40b1b4dbe5bf8ad656ddf51838'
[    5.073679] registered taskstats version 1
[    5.075946] Key type trusted registered
[    5.079669] Key type encrypted registered
[    5.079677] AppArmor: AppArmor sha1 policy hashing enabled
[    5.316088] evm: HMAC attrs: 0x1
[    5.316571]   Magic number: 0:583:744
[    5.316699] rtc_cmos 00:01: setting system clock to 2016-01-15 17:44:08 UTC (1452879848)
[    5.317187] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    5.317189] EDD information not available.
[    5.317270] PM: Hibernation image not present or could not be loaded.
[    5.317748] Freeing unused kernel memory: 1408K (ffffffff81d27000 - ffffffff81e87000)
[    5.317750] Write protecting the kernel read-only data: 12288k
[    5.318036] Freeing unused kernel memory: 260K (ffff8800017bf000 - ffff880001800000)
[    5.318196] Freeing unused kernel memory: 344K (ffff880001baa000 - ffff880001c00000)
[    5.333385] systemd-udevd[125]: starting version 204
[    5.358488] [drm] Initialized drm 1.1.0 20060810
[    5.359154] pps_core: LinuxPPS API ver. 1 registered
[    5.359158] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    5.360460] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    5.360704] PTP clock support registered
[    5.365335] e1000e: Intel(R) PRO/1000 Network Driver - 2.3.2-k
[    5.365338] e1000e: Copyright(c) 1999 - 2014 Intel Corporation.
[    5.365612] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    5.369707] scsi host0: pata_marvell
[    5.369911] scsi host1: pata_marvell
[    5.369968] ata1: PATA max UDMA/100 cmd 0x1018 ctl 0x1024 bmdma 0x1000 irq 18
[    5.369970] ata2: DUMMY
[    5.389140] [drm] radeon kernel modesetting enabled.
[    5.391770] AMD IOMMUv2 driver by Joerg Roedel <joerg.roedel@amd.com>
[    5.391773] AMD IOMMUv2 functionality not available on this system
[    5.394509] CRAT table not found
[    5.394512] Finished initializing topology ret=0
[    5.394770] kfd kfd: Initialized module
[    5.396688] [drm] initializing kernel modesetting (CAICOS 0x1002:0x6779 0x174B:0xE164).
[    5.396704] [drm] register mmio base: 0xE0300000
[    5.396706] [drm] register mmio size: 131072
[    5.397628] ATOM BIOS: AMD
[    5.398113] radeon 0000:01:00.0: VRAM: 512M 0x0000000000000000 - 0x000000001FFFFFFF (512M used)
[    5.398116] radeon 0000:01:00.0: GTT: 1024M 0x0000000020000000 - 0x000000005FFFFFFF
[    5.398118] [drm] Detected VRAM RAM=512M, BAR=256M
[    5.398120] [drm] RAM width 64bits DDR
[    5.398370] [TTM] Zone  kernel: Available graphics memory: 4046528 kiB
[    5.398372] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB
[    5.398373] [TTM] Initializing pool allocator
[    5.398379] [TTM] Initializing DMA pool allocator
[    5.398403] [drm] radeon: 512M of VRAM memory ready
[    5.398405] [drm] radeon: 1024M of GTT memory ready.
[    5.398421] [drm] Loading CAICOS Microcode
[    5.398536] [drm] Internal thermal controller without fan control
[    5.402829] [drm] radeon: dpm initialized
[    5.403006] [drm] GART: num cpu pages 262144, num gpu pages 262144
[    5.420272] [drm] PCIE GART of 1024M enabled (table at 0x0000000000274000).
[    5.420407] radeon 0000:01:00.0: WB enabled
[    5.420411] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000020000c00 and cpu addr 0xffff88022e663c00
[    5.420414] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000020000c0c and cpu addr 0xffff88022e663c0c
[    5.421929] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x0000000000072118 and cpu addr 0xffffc90009132118
[    5.421931] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    5.421933] [drm] Driver supports precise vblank timestamp query.
[    5.421935] radeon 0000:01:00.0: radeon: MSI limited to 32-bit
[    5.421969] radeon 0000:01:00.0: radeon: using MSI.
[    5.422001] [drm] radeon: irq initialized.
[    5.432139] usb 2-4: new high-speed USB device number 3 using ehci-pci
[    5.438623] [drm] ring test on 0 succeeded in 2 usecs
[    5.438636] [drm] ring test on 3 succeeded in 7 usecs
[    5.444119] firewire_ohci 0000:07:03.0: added OHCI v1.0 device as card 0, 8 IR + 8 IT contexts, quirks 0x0
[    5.493869] usb 1-1: New USB device found, idVendor=058f, idProduct=6362
[    5.493872] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    5.493874] usb 1-1: Product: Mass Storage Device
[    5.493877] usb 1-1: Manufacturer: Generic
[    5.493879] usb 1-1: SerialNumber: 058F63626376
[    5.508152] usb 7-1: new low-speed USB device number 2 using uhci_hcd
[    5.572329] usb 2-4: New USB device found, idVendor=0424, idProduct=2514
[    5.572332] usb 2-4: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    5.572385] ata1.00: ATAPI: LITE-ON DVDRW SHW-16H5S, LS0N, max UDMA/66
[    5.572637] ata1.01: HPA detected: current 976771055, native 976773168
[    5.572641] ata1.01: ATA-8: WDC WD5000AAKB-00H8A0, 05.04E05, max UDMA/133
[    5.572643] hub 2-4:1.0: USB hub found
[    5.572645] ata1.01: 976771055 sectors, multi 16: LBA48 
[    5.572693] hub 2-4:1.0: 4 ports detected
[    5.604034] usb 1-3: new high-speed USB device number 3 using ehci-pci
[    5.604397] ata1.00: configured for UDMA/66
[    5.614417] [drm] ring test on 5 succeeded in 2 usecs
[    5.614426] [drm] UVD initialized successfully.
[    5.614822] [drm] ib test on ring 0 succeeded in 0 usecs
[    5.614872] [drm] ib test on ring 3 succeeded in 0 usecs
[    5.620612] ata1.01: configured for UDMA/100
[    5.622087] scsi 0:0:0:0: CD-ROM            LITE-ON  DVDRW SHW-16H5S  LS0N PQ: 0 ANSI: 5
[    5.637830] sr 0:0:0:0: [sr0] scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    5.637832] cdrom: Uniform CD-ROM driver Revision: 3.20
[    5.638044] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    5.638141] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    5.638579] scsi 0:0:1:0: Direct-Access     ATA      WDC WD5000AAKB-0 4E05 PQ: 0 ANSI: 5
[    5.638778] sd 0:0:1:0: [sda] 976771055 512-byte logical blocks: (500 GB/465 GiB)
[    5.638818] sd 0:0:1:0: Attached scsi generic sg1 type 0
[    5.638848] sd 0:0:1:0: [sda] Write Protect is off
[    5.638851] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
[    5.638882] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.649928]  sda: sda1
[    5.650184] sd 0:0:1:0: [sda] Attached SCSI disk
[    5.678136] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) 00:1c:c0:81:f9:c7
[    5.678140] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    5.678173] e1000e 0000:00:19.0 eth0: MAC: 7, PHY: 6, PBA No: FFFFFF-0FF
[    5.678202] ahci 0000:00:1f.2: version 3.0
[    5.678484] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    5.678488] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pmp pio slum part ccc ems 
[    5.716828] scsi host2: ahci
[    5.716945] scsi host3: ahci
[    5.717059] scsi host4: ahci
[    5.717172] scsi host5: ahci
[    5.717283] scsi host6: ahci
[    5.717391] scsi host7: ahci
[    5.717458] ata3: SATA max UDMA/133 abar m2048@0xe04a5000 port 0xe04a5100 irq 32
[    5.717461] ata4: SATA max UDMA/133 abar m2048@0xe04a5000 port 0xe04a5180 irq 32
[    5.717463] ata5: SATA max UDMA/133 abar m2048@0xe04a5000 port 0xe04a5200 irq 32
[    5.717465] ata6: SATA max UDMA/133 abar m2048@0xe04a5000 port 0xe04a5280 irq 32
[    5.717467] ata7: SATA max UDMA/133 abar m2048@0xe04a5000 port 0xe04a5300 irq 32
[    5.717469] ata8: SATA max UDMA/133 abar m2048@0xe04a5000 port 0xe04a5380 irq 32
[    5.739742] usb 1-3: New USB device found, idVendor=13fe, idProduct=3600
[    5.739745] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    5.739747] usb 1-3: Product: USB DISK 2.0
[    5.739749] usb 1-3: Manufacturer:         
[    5.739752] usb 1-3: SerialNumber: 07B80408943D02E7
[    5.743688] usb-storage 1-1:1.0: USB Mass Storage device detected
[    5.743810] scsi host8: usb-storage 1-1:1.0
[    5.743907] usb-storage 1-3:1.0: USB Mass Storage device detected
[    5.743976] usb-storage 1-3:1.0: Quirks match for vid 13fe pid 3600: 4000
[    5.744035] scsi host9: usb-storage 1-3:1.0
[    5.744118] usbcore: registered new interface driver usb-storage
[    5.745680] usbcore: registered new interface driver uas
[    5.769051] usb 7-1: New USB device found, idVendor=04d9, idProduct=1603
[    5.769057] usb 7-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    5.769061] usb 7-1: Product: USB Keyboard
[    5.769064] usb 7-1: Manufacturer:  
[    5.780183] hidraw: raw HID events driver (C) Jiri Kosina
[    5.852085] usb 8-2: new low-speed USB device number 2 using uhci_hcd
[    5.898360] usbcore: registered new interface driver usbhid
[    5.898362] usbhid: USB HID core driver
[    5.900271] input:   USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/0003:04D9:1603.0001/input/input5
[    5.904047] tsc: Refined TSC clocksource calibration: 2388.000 MHz
[    5.944239] firewire_core 0000:07:03.0: created device fw0: GUID 00902700022781ba, S400
[    5.956222] hid-generic 0003:04D9:1603.0001: input,hidraw0: USB HID v1.10 Keyboard [  USB Keyboard] on usb-0000:00:1d.1-1/input0
[    5.970145] input:   USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.1/0003:04D9:1603.0002/input/input6
[    6.024198] hid-generic 0003:04D9:1603.0002: input,hidraw1: USB HID v1.10 Device [  USB Keyboard] on usb-0000:00:1d.1-1/input1
[    6.040036] ata8: SATA link down (SStatus 0 SControl 300)
[    6.044042] ata6: SATA link down (SStatus 0 SControl 300)
[    6.044077] ata7: SATA link down (SStatus 0 SControl 300)
[    6.044096] ata5: SATA link down (SStatus 0 SControl 300)
[    6.216053] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    6.220048] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    6.220549] ata3.00: HPA detected: current 78163247, native 78165360
[    6.220619] ata3.00: ATA-7: WDC WD400BD-55MTA1, 10.01E01, max UDMA/133
[    6.220623] ata3.00: 78163247 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    6.221221] ata3.00: configured for UDMA/133
[    6.221327] scsi 2:0:0:0: Direct-Access     ATA      WDC WD400BD-55MT 1E01 PQ: 0 ANSI: 5
[    6.221591] sd 2:0:0:0: [sdb] 78163247 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    6.221593] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    6.221672] sd 2:0:0:0: [sdb] Write Protect is off
[    6.221675] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    6.221711] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.227460]  sdb: sdb1
[    6.227756] sd 2:0:0:0: [sdb] Attached SCSI disk
[    6.232052] usb 8-2: New USB device found, idVendor=413c, idProduct=3012
[    6.232057] usb 8-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    6.232060] usb 8-2: Product: Dell USB Optical Mouse
[    6.232064] usb 8-2: Manufacturer: Dell
[    6.244656] ata4.00: ATA-8: ST3640323AS, SD35, max UDMA/133
[    6.244660] ata4.00: 1250263728 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    6.248507] input: Dell Dell USB Optical Mouse as /devices/pci0000:00/0000:00:1d.2/usb8/8-2/8-2:1.0/0003:413C:3012.0003/input/input7
[    6.248633] hid-generic 0003:413C:3012.0003: input,hidraw2: USB HID v1.11 Mouse [Dell Dell USB Optical Mouse] on usb-0000:00:1d.2-2/input0
[    6.264059] [drm] ib test on ring 5 succeeded
[    6.265023] [drm] Radeon Display Connectors
[    6.265025] [drm] Connector 0:
[    6.265027] [drm]   HDMI-A-1
[    6.265028] [drm]   HPD2
[    6.265030] [drm]   DDC: 0x6440 0x6440 0x6444 0x6444 0x6448 0x6448 0x644c 0x644c
[    6.265031] [drm]   Encoders:
[    6.265032] [drm]     DFP1: INTERNAL_UNIPHY1
[    6.265033] [drm] Connector 1:
[    6.265035] [drm]   DVI-D-1
[    6.265036] [drm]   HPD4
[    6.265037] [drm]   DDC: 0x6460 0x6460 0x6464 0x6464 0x6468 0x6468 0x646c 0x646c
[    6.265038] [drm]   Encoders:
[    6.265040] [drm]     DFP2: INTERNAL_UNIPHY
[    6.265041] [drm] Connector 2:
[    6.265042] [drm]   VGA-1
[    6.265044] [drm]   DDC: 0x6430 0x6430 0x6434 0x6434 0x6438 0x6438 0x643c 0x643c
[    6.265045] [drm]   Encoders:
[    6.265046] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    6.286493] ata4.00: configured for UDMA/133
[    6.286587] scsi 3:0:0:0: Direct-Access     ATA      ST3640323AS      SD35 PQ: 0 ANSI: 5
[    6.286808] sd 3:0:0:0: [sdc] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
[    6.286840] sd 3:0:0:0: Attached scsi generic sg3 type 0
[    6.286860] sd 3:0:0:0: [sdc] Write Protect is off
[    6.286863] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    6.286886] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.337881]  sdc: sdc1 sdc2
[    6.338185] sd 3:0:0:0: [sdc] Attached SCSI disk
[    6.378181] [drm] fb mappable at 0xC0475000
[    6.378184] [drm] vram apper at 0xC0000000
[    6.378185] [drm] size 8294400
[    6.378186] [drm] fb depth is 24
[    6.378188] [drm]    pitch is 7680
[    6.378293] fbcon: radeondrmfb (fb0) is primary device
[    6.539147] random: nonblocking pool is initialized
[    6.544510] Console: switching to colour frame buffer device 160x64
[    6.547920] radeon 0000:01:00.0: fb0: radeondrmfb frame buffer device
[    6.547923] radeon 0000:01:00.0: registered panic notifier
[    6.556092] [drm] Initialized radeon 2.40.0 20080528 for 0000:01:00.0 on minor 0
[    6.556704] [drm] Memory usable by graphics device = 512M
[    6.556708] [drm] Replacing VGA console driver
[    6.580082] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    6.580085] [drm] Driver supports precise vblank timestamp query.
[    6.580156] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    6.581096] [drm] initialized overlay support
[    6.581109] [drm] Initialized i915 1.6.0 20141121 for 0000:00:02.0 on minor 1
[    6.673335] i915 0000:00:02.0: fb1: inteldrmfb frame buffer device
[    6.740772] scsi 8:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[    6.741269] scsi 8:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[    6.741757] scsi 8:0:0:2: Direct-Access     Generic  USB xD/SM Reader 1.02 PQ: 0 ANSI: 0
[    6.742266] scsi 8:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[    6.742631] sd 8:0:0:0: Attached scsi generic sg4 type 0
[    6.742968] sd 8:0:0:1: Attached scsi generic sg5 type 0
[    6.743403] sd 8:0:0:2: Attached scsi generic sg6 type 0
[    6.743739] sd 8:0:0:3: Attached scsi generic sg7 type 0
[    6.745272] scsi 9:0:0:0: Direct-Access              USB DISK 2.0     PMAP PQ: 0 ANSI: 0 CCS
[    6.745597] sd 9:0:0:0: Attached scsi generic sg8 type 0
[    6.746386] sd 9:0:0:0: [sdh] 7831552 512-byte logical blocks: (4.00 GB/3.73 GiB)
[    6.747632] sd 9:0:0:0: [sdh] Write Protect is off
[    6.747636] sd 9:0:0:0: [sdh] Mode Sense: 23 00 00 00
[    6.748754] sd 9:0:0:0: [sdh] No Caching mode page found
[    6.748789] sd 9:0:0:0: [sdh] Assuming drive cache: write through
[    6.754164]  sdh: sdh1
[    6.756882] sd 8:0:0:0: [sdd] Attached SCSI removable disk
[    6.757503] sd 8:0:0:1: [sde] Attached SCSI removable disk
[    6.758121] sd 8:0:0:2: [sdf] Attached SCSI removable disk
[    6.758251] sd 9:0:0:0: [sdh] Attached SCSI removable disk
[    6.758744] sd 8:0:0:3: [sdg] Attached SCSI removable disk
[    6.904129] Switched to clocksource tsc
[    8.372056] floppy0: no floppy controllers found
[    8.909594] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    9.409295] EXT4-fs (sdc1): mounted filesystem with ordered data mode. Opts: (null)
[    9.582742] ISO 9660 Extensions: Microsoft Joliet Level 3
[    9.586115] ISO 9660 Extensions: RRIP_1991A
[   10.654251] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[   17.636040] floppy0: no floppy controllers found
[   21.379995] Adding 5014524k swap on /dev/sdc2.  Priority:-1 extents:1 across:5014524k FS
[   21.554471] systemd-udevd[1306]: starting version 204
[   21.912774] lp: driver loaded but no devices found
[   21.931800] init: cups main process (1349) killed by HUP signal
[   21.931814] init: cups main process ended, respawning
[   21.960707] ppdev: user-space parallel port driver
[   21.988374] Bluetooth: Core ver 2.20
[   21.988408] NET: Registered protocol family 31
[   21.988410] Bluetooth: HCI device and connection manager initialized
[   21.988415] Bluetooth: HCI socket layer initialized
[   21.988419] Bluetooth: L2CAP socket layer initialized
[   21.988427] Bluetooth: SCO socket layer initialized
[   21.999955] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   22.059347] Bluetooth: RFCOMM TTY layer initialized
[   22.059357] Bluetooth: RFCOMM socket layer initialized
[   22.059365] Bluetooth: RFCOMM ver 1.11
[   22.095288] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   22.095292] Bluetooth: BNEP filters: protocol multicast
[   22.095298] Bluetooth: BNEP socket layer initialized
[   22.118078] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052f conflicts with OpRegion 0x000000000000050c-0x000000000000050f (\IGPO) (20141107/utaddress-258)
[   22.118086] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   22.371366] device-mapper: multipath: version 1.7.0 loaded
[   22.381844] coretemp coretemp.0: Using relative temperature scale!
[   22.381870] coretemp coretemp.0: Using relative temperature scale!
[   22.381883] coretemp coretemp.0: Using relative temperature scale!
[   22.381896] coretemp coretemp.0: Using relative temperature scale!
[   22.397880] snd_hda_intel 0000:01:00.1: Handle VGA-switcheroo audio client
[   22.417590] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input8
[   22.442044] sound hdaudioC0D2: autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:line
[   22.442049] sound hdaudioC0D2:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   22.442052] sound hdaudioC0D2:    hp_outs=1 (0x15/0x0/0x0/0x0/0x0)
[   22.442054] sound hdaudioC0D2:    mono: mono_out=0x0
[   22.442056] sound hdaudioC0D2:    inputs:
[   22.442059] sound hdaudioC0D2:      Rear Mic=0x18
[   22.442061] sound hdaudioC0D2:      Front Mic=0x1a
[   22.442064] sound hdaudioC0D2:      Line=0x19
[   22.447449] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   22.447563] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   22.447730] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   22.447986] input: HDA Intel Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   22.448189] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   22.539234] gpio_ich: GPIO from 451 to 511 on gpio_ich
[   22.589513] init: failsafe main process (1601) killed by TERM signal
[   24.193221] init: alsa-restore main process (1966) terminated with status 99
[   24.264206] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.148044] floppy0: no floppy controllers found
[   25.378330] init: plymouth-upstart-bridge main process ended, respawning
[   25.387112] init: plymouth-upstart-bridge main process (2352) terminated with status 1
[   25.387127] init: plymouth-upstart-bridge main process ended, respawning
[   25.660894] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
[   25.661006] e1000e 0000:00:19.0 eth0: 10/100 speed: disabling TSO
[   25.661040] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  164.811002] systemd-hostnamed[3473]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!

```

the lspci (14.04.03) :

```

00:00.0 Host bridge: Intel Corporation 82Q35 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82Q35 Express PCI Express Root Port (rev 02)
00:02.0 Display controller: Intel Corporation 82Q35 Express Integrated Graphics Controller (rev 02)
00:03.0 Communication controller: Intel Corporation 82Q35 Express MEI Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DM-2 Gigabit Network Connection (rev 02)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IO (ICH9DO) LPC Interface Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 6 port SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Caicos [Radeon HD 6450/7450/8450 / R5 230 OEM]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Caicos HDMI Audio [Radeon HD 6400 Series]
04:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6101/6102 single-port PATA133 interface (rev b2)
07:03.0 FireWire (IEEE 1394): LSI Corporation FW322/323 [TrueFire] 1394a Controller (rev 70)

```

but the same hardware configuration dosnt works on 16.04.LTS (alpha from 14.01.2016) amd64.

it looks ok in screenshots :

[[img]http://obrazki.elektroda.pl/4509210000_1452939956_thumb.jpg[/img]](http://obrazki.elektroda.pl/4509210000_1452939956.png) [[img]http://obrazki.elektroda.pl/4704859500_1452939957_thumb.jpg[/img]](http://obrazki.elektroda.pl/4704859500_1452939957.png) 

but the monitor from Intel HD (builtin motherboard) dosnt work - it is black ... 

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 4.3.0-5-generic (buildd@lgw01-10) (gcc version 5.3.1 20151216 (Ubuntu 5.3.1-3ubuntu3) ) #16-Ubuntu SMP Wed Dec 16 23:33:25 UTC 2015 (Ubuntu 4.3.0-5.16-generic 4.3.3)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.3.0-5-generic root=UUID=62f8a354-b923-4733-9a28-976899d688e1 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] x86/fpu: Legacy x87 FPU detected.
[    0.000000] x86/fpu: Using 'lazy' FPU context switches.
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009dbff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009dc00-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000bee1efff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bee1f000-0x00000000bee20fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bee21000-0x00000000beef5fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000beef6000-0x00000000befe2fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000befe3000-0x00000000befe5fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000befe6000-0x00000000beff1fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000beff2000-0x00000000beff2fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000beff3000-0x00000000beffefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000befff000-0x00000000beffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bf000000-0x00000000bfffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f0000000-0x00000000f7ffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffc00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000023bffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.4 present.
[    0.000000] DMI:                  /DQ35JO, BIOS JOQ3510J.86A.0882.2008.0423.1925 04/23/2008
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x23c000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 0BF000000 mask FFF000000 uncachable
[    0.000000]   3 base 100000000 mask F00000000 write-back
[    0.000000]   4 base 200000000 mask F80000000 write-back
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- WT  
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3056MB, range: 16MB, type UC
[    0.000000] reg 3, base: 4GB, range: 4GB, type WB
[    0.000000] reg 4, base: 8GB, range: 2GB, type WB
[    0.000000] total RAM covered: 9200M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 32M 	num_reg: 5  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3056MB, range: 16MB, type UC
[    0.000000] reg 3, base: 4GB, range: 4GB, type WB
[    0.000000] reg 4, base: 8GB, range: 2GB, type WB
[    0.000000] e820: update [mem 0xbf000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xbf000 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fe5e0-0x000fe5ef] mapped at [ffff8800000fe5e0]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x021f6000, 0x021f6fff] PGTABLE
[    0.000000] BRK [0x021f7000, 0x021f7fff] PGTABLE
[    0.000000] BRK [0x021f8000, 0x021f8fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x23be00000-0x23bffffff]
[    0.000000]  [mem 0x23be00000-0x23bffffff] page 2M
[    0.000000] BRK [0x021f9000, 0x021f9fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x220000000-0x23bdfffff]
[    0.000000]  [mem 0x220000000-0x23bdfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x200000000-0x21fffffff]
[    0.000000]  [mem 0x200000000-0x21fffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0xbee1efff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0xbedfffff] page 2M
[    0.000000]  [mem 0xbee00000-0xbee1efff] page 4k
[    0.000000] init_memory_mapping: [mem 0xbee21000-0xbeef5fff]
[    0.000000]  [mem 0xbee21000-0xbeef5fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xbefe3000-0xbefe5fff]
[    0.000000]  [mem 0xbefe3000-0xbefe5fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xbeff2000-0xbeff2fff]
[    0.000000]  [mem 0xbeff2000-0xbeff2fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xbefff000-0xbeffffff]
[    0.000000]  [mem 0xbefff000-0xbeffffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x1ffffffff]
[    0.000000]  [mem 0x100000000-0x1ffffffff] page 2M
[    0.000000] BRK [0x021fa000, 0x021fafff] PGTABLE
[    0.000000] BRK [0x021fb000, 0x021fbfff] PGTABLE
[    0.000000] RAMDISK: [mem 0x33dc4000-0x35ed9fff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000000FE020 000014 (v00 INTEL )
[    0.000000] ACPI: RSDT 0x00000000BEFFD038 000070 (v01 INTEL  DQ3510J  00000372      01000013)
[    0.000000] ACPI: FACP 0x00000000BEFFC000 000074 (v01 INTEL  DQ3510J  00000372 MSFT 01000013)
[    0.000000] ACPI: DSDT 0x00000000BEFF8000 003D3A (v01 INTEL  DQ3510J  00000372 MSFT 01000013)
[    0.000000] ACPI: FACS 0x00000000BEF82000 000040
[    0.000000] ACPI: APIC 0x00000000BEFF7000 000078 (v01 INTEL  DQ3510J  00000372 MSFT 01000013)
[    0.000000] ACPI: WDDT 0x00000000BEFF6000 000040 (v01 INTEL  DQ3510J  00000372 MSFT 01000013)
[    0.000000] ACPI: MCFG 0x00000000BEFF5000 00003C (v01 INTEL  DQ3510J  00000372 MSFT 01000013)
[    0.000000] ACPI: ASF! 0x00000000BEFF4000 0000A6 (v32 INTEL  DQ3510J  00000372 MSFT 01000013)
[    0.000000] ACPI: HPET 0x00000000BEFF3000 000038 (v01 INTEL  DQ3510J  00000372 MSFT 01000013)
[    0.000000] ACPI: DMAR 0x00000000BEFF1000 000120 (v01 INTEL  DQ3510J  00000372 MSFT 01000013)
[    0.000000] ACPI: ASPT 0x00000000BEFF0000 00002C (v01 INTEL  DQ3510J  00000372 MSFT 01000013)
[    0.000000] ACPI: WDTT 0x00000000BEFEF000 0002CC (v01 INTEL  DQ3510J  00000372 MSFT 01000013)
[    0.000000] ACPI: SSDT 0x00000000BEFEE000 000204 (v01 INTEL  CpuPm    00000372 MSFT 01000013)
[    0.000000] ACPI: SSDT 0x00000000BEFED000 0001F9 (v01 INTEL  Cpu0Ist  00000372 MSFT 01000013)
[    0.000000] ACPI: SSDT 0x00000000BEFEC000 0001F9 (v01 INTEL  Cpu1Ist  00000372 MSFT 01000013)
[    0.000000] ACPI: SSDT 0x00000000BEFEB000 0001F9 (v01 INTEL  Cpu2Ist  00000372 MSFT 01000013)
[    0.000000] ACPI: SSDT 0x00000000BEFEA000 0001F9 (v01 INTEL  Cpu3Ist  00000372 MSFT 01000013)
[    0.000000] ACPI: SSDT 0x00000000BEFE9000 0000DD (v01 INTEL  Cpu0Cst  00000372 MSFT 01000013)
[    0.000000] ACPI: SSDT 0x00000000BEFE8000 0000DD (v01 INTEL  Cpu1Cst  00000372 MSFT 01000013)
[    0.000000] ACPI: SSDT 0x00000000BEFE7000 0000DD (v01 INTEL  Cpu2Cst  00000372 MSFT 01000013)
[    0.000000] ACPI: SSDT 0x00000000BEFE6000 0000DD (v01 INTEL  Cpu3Cst  00000372 MSFT 01000013)
[    0.000000] ACPI: TCPA 0x00000000BEEF7000 000032 (v02 INTEL  TIANO    00000002 MSFT 01000013)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000023bffffff]
[    0.000000] NODE_DATA(0) allocated [mem 0x23bff6000-0x23bffafff]
[    0.000000]  [ffffea0000000000-ffffea0008ffffff] PMD -> [ffff880233600000-ffff88023b5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.000000]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
[    0.000000]   Normal   [mem 0x0000000100000000-0x000000023bffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x0000000000001000-0x000000000009cfff]
[    0.000000]   node   0: [mem 0x0000000000100000-0x00000000bee1efff]
[    0.000000]   node   0: [mem 0x00000000bee21000-0x00000000beef5fff]
[    0.000000]   node   0: [mem 0x00000000befe3000-0x00000000befe5fff]
[    0.000000]   node   0: [mem 0x00000000beff2000-0x00000000beff2fff]
[    0.000000]   node   0: [mem 0x00000000befff000-0x00000000beffffff]
[    0.000000]   node   0: [mem 0x0000000100000000-0x000000023bffffff]
[    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x000000023bffffff]
[    0.000000] On node 0 totalpages: 2076309
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3996 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 12156 pages used for memmap
[    0.000000]   DMA32 zone: 777977 pages, LIFO batch:31
[    0.000000]   Normal zone: 20224 pages used for memmap
[    0.000000]   Normal zone: 1294336 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
[    0.000000] smpboot: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009dfff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xbee1f000-0xbee20fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbeef6000-0xbefe2fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbefe6000-0xbeff1fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbeff3000-0xbeffefff]
[    0.000000] PM: Registered nosave memory: [mem 0xbf000000-0xbfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xc0000000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xf7ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xffbfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xffc00000-0xffffffff]
[    0.000000] e820: [mem 0xc0000000-0xefffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 33 pages/cpu @ffff88023bc00000 s97304 r8192 d29672 u524288
[    0.000000] pcpu-alloc: s97304 r8192 d29672 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 2043844
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.3.0-5-generic root=UUID=62f8a354-b923-4733-9a28-976899d688e1 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 8054916K/8305236K available (8194K kernel code, 1251K rwdata, 3852K rodata, 1464K init, 1300K bss, 250320K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	Build-time adjustment of leaf fanout to 64.
[    0.000000] 	RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=64, nr_cpu_ids=4
[    0.000000] NR_IRQS:16640 nr_irqs:456 16
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 133484882848 ns
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 2387.929 MHz processor
[    0.004012] Calibrating delay loop (skipped), value calculated using timer frequency.. 4775.85 BogoMIPS (lpj=9551716)
[    0.004016] pid_max: default: 32768 minimum: 301
[    0.004024] ACPI: Core revision 20150818
[    0.012558] ACPI: 10 ACPI AML tables successfully acquired and loaded
[    0.012585] Security Framework initialized
[    0.012588] Yama: becoming mindful.
[    0.012606] AppArmor: AppArmor initialized
[    0.013293] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.017374] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.019387] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.019402] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.019807] Initializing cgroup subsys io
[    0.019816] Initializing cgroup subsys memory
[    0.019828] Initializing cgroup subsys devices
[    0.019831] Initializing cgroup subsys freezer
[    0.019835] Initializing cgroup subsys net_cls
[    0.019839] Initializing cgroup subsys perf_event
[    0.019842] Initializing cgroup subsys net_prio
[    0.019845] Initializing cgroup subsys hugetlb
[    0.019851] Initializing cgroup subsys pids
[    0.019878] CPU: Physical Processor ID: 0
[    0.019879] CPU: Processor Core ID: 0
[    0.019882] mce: CPU supports 6 MCE banks
[    0.019890] CPU0: Thermal monitoring enabled (TM2)
[    0.019895] process: using mwait in idle threads
[    0.019901] Last level iTLB entries: 4KB 128, 2MB 4, 4MB 4
[    0.019902] Last level dTLB entries: 4KB 256, 2MB 0, 4MB 32, 1GB 0
[    0.020268] Freeing SMP alternatives memory: 28K (ffffffff820a8000 - ffffffff820af000)
[    0.023599] ftrace: allocating 31344 entries in 123 pages
[    0.032107] DMAR: Host address width 36
[    0.032111] DMAR: DRHD base: 0x000000feb00000 flags: 0x0
[    0.032118] DMAR: dmar0: reg_base_addr feb00000 ver 1:0 cap c9008020a30270 ecap 1000
[    0.032120] DMAR: DRHD base: 0x000000feb01000 flags: 0x0
[    0.032127] DMAR: dmar1: reg_base_addr feb01000 ver 1:0 cap c0000020230270 ecap 1000
[    0.032128] DMAR: DRHD base: 0x000000feb02000 flags: 0x0
[    0.032135] DMAR: dmar2: reg_base_addr feb02000 ver 1:0 cap c0000020230270 ecap 1000
[    0.032136] DMAR: DRHD base: 0x000000feb03000 flags: 0x1
[    0.032141] DMAR: dmar3: reg_base_addr feb03000 ver 1:0 cap c9008020230270 ecap 1000
[    0.032143] DMAR: RMRR base: 0x000000000e0000 end: 0x000000000effff
[    0.032145] DMAR: RMRR base: 0x000000bf600000 end: 0x000000bfffffff
[    0.032509] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.076000] smpboot: CPU0: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz (family: 0x6, model: 0xf, stepping: 0xb)
[    0.076000] Performance Events: PEBS fmt0+, 4-deep LBR, Core2 events, Intel PMU driver.
[    0.076000] perf_event_intel: PEBS disabled due to CPU errata
[    0.076000] ... version:                2
[    0.076000] ... bit width:              40
[    0.076000] ... generic registers:      2
[    0.076000] ... value mask:             000000ffffffffff
[    0.076000] ... max period:             000000007fffffff
[    0.076000] ... fixed-purpose events:   3
[    0.076000] ... event mask:             0000000700000003
[    0.076000] x86: Booting SMP configuration:
[    0.076000] .... node  #0, CPUs:      #1
[    0.086198] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.086307]  #2 #3
[    0.112021] x86: Booted up 1 node, 4 CPUs
[    0.112026] smpboot: Total of 4 processors activated (19103.43 BogoMIPS)
[    0.116017] devtmpfs: initialized
[    0.120190] evm: security.selinux
[    0.120192] evm: security.SMACK64
[    0.120194] evm: security.SMACK64EXEC
[    0.120195] evm: security.SMACK64TRANSMUTE
[    0.120196] evm: security.SMACK64MMAP
[    0.120197] evm: security.ima
[    0.120198] evm: security.capability
[    0.120220] PM: Registering ACPI NVS region [mem 0xbeef6000-0xbefe2fff] (970752 bytes)
[    0.120220] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    0.120243] pinctrl core: initialized pinctrl subsystem
[    0.120243] RTC time: 11:11:42, date: 01/16/16
[    0.120334] NET: Registered protocol family 16
[    0.132008] cpuidle: using governor ladder
[    0.144004] cpuidle: using governor menu
[    0.144015] PCCT header not found.
[    0.144135] ACPI: bus type PCI registered
[    0.144139] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.144260] PCI: MMCONFIG for domain 0000 [bus 00-7f] at [mem 0xf0000000-0xf7ffffff] (base 0xf0000000)
[    0.144263] PCI: MMCONFIG at [mem 0xf0000000-0xf7ffffff] reserved in E820
[    0.144272] PCI: Using configuration type 1 for base access
[    0.152130] ACPI: Added _OSI(Module Device)
[    0.152137] ACPI: Added _OSI(Processor Device)
[    0.152139] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.152140] ACPI: Added _OSI(Processor Aggregator Device)
[    0.154821] ACPI: Interpreter enabled
[    0.154830] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20150818/hwxface-580)
[    0.154844] ACPI: (supports S0 S1 S3 S4 S5)
[    0.154846] ACPI: Using IOAPIC for interrupt routing
[    0.154869] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.160438] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.160445] acpi PNP0A03:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.160450] acpi PNP0A03:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[    0.160989] acpi PNP0A03:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-7f] only partially covers this bridge
[    0.161178] PCI host bridge to bus 0000:00
[    0.161181] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.161184] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
[    0.161186] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
[    0.161189] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
[    0.161191] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000effff window]
[    0.161193] pci_bus 0000:00: root bus resource [mem 0xf8000000-0xfeafffff window]
[    0.161195] pci_bus 0000:00: root bus resource [mem 0xc0000000-0xefffffff window]
[    0.161204] pci 0000:00:00.0: [8086:29b0] type 00 class 0x060000
[    0.161313] pci 0000:00:01.0: [8086:29b1] type 01 class 0x060400
[    0.161359] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.161407] pci 0000:00:01.0: System wakeup disabled by ACPI
[    0.161454] pci 0000:00:02.0: [8086:29b2] type 00 class 0x038000
[    0.161468] pci 0000:00:02.0: reg 0x10: [mem 0xe0400000-0xe047ffff]
[    0.161473] pci 0000:00:02.0: reg 0x14: [io  0x3430-0x3437]
[    0.161479] pci 0000:00:02.0: reg 0x18: [mem 0xd0000000-0xdfffffff pref]
[    0.161485] pci 0000:00:02.0: reg 0x1c: [mem 0xe0200000-0xe02fffff]
[    0.161583] pci 0000:00:03.0: [8086:29b4] type 00 class 0x078000
[    0.161600] pci 0000:00:03.0: reg 0x10: [mem 0xe04a6100-0xe04a610f 64bit]
[    0.161631] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    0.161738] pci 0000:00:19.0: [8086:10bd] type 00 class 0x020000
[    0.161762] pci 0000:00:19.0: reg 0x10: [mem 0xe0480000-0xe049ffff]
[    0.161770] pci 0000:00:19.0: reg 0x14: [mem 0xe04a4000-0xe04a4fff]
[    0.161779] pci 0000:00:19.0: reg 0x18: [io  0x3400-0x341f]
[    0.161821] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.161867] pci 0000:00:19.0: System wakeup disabled by ACPI
[    0.161919] pci 0000:00:1a.0: [8086:2937] type 00 class 0x0c0300
[    0.161963] pci 0000:00:1a.0: reg 0x20: [io  0x30e0-0x30ff]
[    0.162051] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.162101] pci 0000:00:1a.1: [8086:2938] type 00 class 0x0c0300
[    0.162145] pci 0000:00:1a.1: reg 0x20: [io  0x30c0-0x30df]
[    0.162230] pci 0000:00:1a.1: System wakeup disabled by ACPI
[    0.162280] pci 0000:00:1a.2: [8086:2939] type 00 class 0x0c0300
[    0.162324] pci 0000:00:1a.2: reg 0x20: [io  0x30a0-0x30bf]
[    0.162409] pci 0000:00:1a.2: System wakeup disabled by ACPI
[    0.162466] pci 0000:00:1a.7: [8086:293c] type 00 class 0x0c0320
[    0.162494] pci 0000:00:1a.7: reg 0x10: [mem 0xe04a5c00-0xe04a5fff]
[    0.162558] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.162624] pci 0000:00:1a.7: System wakeup disabled by ACPI
[    0.162676] pci 0000:00:1b.0: [8086:293e] type 00 class 0x040300
[    0.162701] pci 0000:00:1b.0: reg 0x10: [mem 0xe04a0000-0xe04a3fff 64bit]
[    0.162755] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.162819] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.162870] pci 0000:00:1c.0: [8086:2940] type 01 class 0x060400
[    0.162926] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.162975] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.163026] pci 0000:00:1c.1: [8086:2942] type 01 class 0x060400
[    0.163082] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.163135] pci 0000:00:1c.1: System wakeup disabled by ACPI
[    0.163186] pci 0000:00:1c.2: [8086:2944] type 01 class 0x060400
[    0.163246] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.163294] pci 0000:00:1c.2: System wakeup disabled by ACPI
[    0.163346] pci 0000:00:1c.3: [8086:2946] type 01 class 0x060400
[    0.163401] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.163450] pci 0000:00:1c.3: System wakeup disabled by ACPI
[    0.163499] pci 0000:00:1c.4: [8086:2948] type 01 class 0x060400
[    0.163554] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.163605] pci 0000:00:1c.4: System wakeup disabled by ACPI
[    0.163657] pci 0000:00:1d.0: [8086:2934] type 00 class 0x0c0300
[    0.163701] pci 0000:00:1d.0: reg 0x20: [io  0x3080-0x309f]
[    0.163786] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.163837] pci 0000:00:1d.1: [8086:2935] type 00 class 0x0c0300
[    0.163881] pci 0000:00:1d.1: reg 0x20: [io  0x3060-0x307f]
[    0.163966] pci 0000:00:1d.1: System wakeup disabled by ACPI
[    0.164019] pci 0000:00:1d.2: [8086:2936] type 00 class 0x0c0300
[    0.164063] pci 0000:00:1d.2: reg 0x20: [io  0x3040-0x305f]
[    0.164151] pci 0000:00:1d.2: System wakeup disabled by ACPI
[    0.164208] pci 0000:00:1d.7: [8086:293a] type 00 class 0x0c0320
[    0.164236] pci 0000:00:1d.7: reg 0x10: [mem 0xe04a5800-0xe04a5bff]
[    0.164300] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.164366] pci 0000:00:1d.7: System wakeup disabled by ACPI
[    0.164416] pci 0000:00:1e.0: [8086:244e] type 01 class 0x060401
[    0.164499] pci 0000:00:1e.0: System wakeup disabled by ACPI
[    0.164550] pci 0000:00:1f.0: [8086:2914] type 00 class 0x060100
[    0.164632] pci 0000:00:1f.0: can't claim BAR 13 [io  0x0400-0x047f]: address conflict with ACPI CPU throttle [io  0x0410-0x0415]
[    0.164637] pci 0000:00:1f.0: quirk: [io  0x0500-0x053f] claimed by ICH6 GPIO
[    0.164641] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0680 (mask 007f)
[    0.164743] pci 0000:00:1f.2: [8086:2922] type 00 class 0x010601
[    0.164766] pci 0000:00:1f.2: reg 0x10: [io  0x3428-0x342f]
[    0.164774] pci 0000:00:1f.2: reg 0x14: [io  0x343c-0x343f]
[    0.164782] pci 0000:00:1f.2: reg 0x18: [io  0x3420-0x3427]
[    0.164789] pci 0000:00:1f.2: reg 0x1c: [io  0x3438-0x343b]
[    0.164797] pci 0000:00:1f.2: reg 0x20: [io  0x3020-0x303f]
[    0.164805] pci 0000:00:1f.2: reg 0x24: [mem 0xe04a5000-0xe04a57ff]
[    0.164831] pci 0000:00:1f.2: PME# supported from D3hot
[    0.164927] pci 0000:00:1f.3: [8086:2930] type 00 class 0x0c0500
[    0.164943] pci 0000:00:1f.3: reg 0x10: [mem 0xe04a6000-0xe04a60ff 64bit]
[    0.164963] pci 0000:00:1f.3: reg 0x20: [io  0x3000-0x301f]
[    0.165098] pci 0000:01:00.0: [1002:6779] type 00 class 0x030000
[    0.165126] pci 0000:01:00.0: reg 0x10: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.165137] pci 0000:01:00.0: reg 0x18: [mem 0xe0300000-0xe031ffff 64bit]
[    0.165146] pci 0000:01:00.0: reg 0x20: [io  0x2000-0x20ff]
[    0.165160] pci 0000:01:00.0: reg 0x30: [mem 0xfffe0000-0xffffffff pref]
[    0.165186] pci 0000:01:00.0: supports D1 D2
[    0.165240] pci 0000:01:00.1: [1002:aa98] type 00 class 0x040300
[    0.165267] pci 0000:01:00.1: reg 0x10: [mem 0xe0320000-0xe0323fff 64bit]
[    0.165321] pci 0000:01:00.1: supports D1 D2
[    0.165398] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.165401] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    0.165404] pci 0000:00:01.0:   bridge window [mem 0xe0300000-0xe03fffff]
[    0.165408] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.165456] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.165510] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.165575] pci 0000:04:00.0: [11ab:6101] type 00 class 0x01018f
[    0.165608] pci 0000:04:00.0: reg 0x10: [io  0x1018-0x101f]
[    0.165620] pci 0000:04:00.0: reg 0x14: [io  0x1024-0x1027]
[    0.165632] pci 0000:04:00.0: reg 0x18: [io  0x1010-0x1017]
[    0.165643] pci 0000:04:00.0: reg 0x1c: [io  0x1020-0x1023]
[    0.165655] pci 0000:04:00.0: reg 0x20: [io  0x1000-0x100f]
[    0.165667] pci 0000:04:00.0: reg 0x24: [mem 0xe0100000-0xe01001ff]
[    0.165712] pci 0000:04:00.0: supports D1
[    0.165714] pci 0000:04:00.0: PME# supported from D0 D1 D3hot
[    0.165770] pci 0000:04:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.165779] pci 0000:00:1c.2: PCI bridge to [bus 04]
[    0.165783] pci 0000:00:1c.2:   bridge window [io  0x1000-0x1fff]
[    0.165787] pci 0000:00:1c.2:   bridge window [mem 0xe0100000-0xe01fffff]
[    0.165838] pci 0000:00:1c.3: PCI bridge to [bus 05]
[    0.165890] pci 0000:00:1c.4: PCI bridge to [bus 06]
[    0.165943] pci 0000:07:03.0: [11c1:5811] type 00 class 0x0c0010
[    0.165965] pci 0000:07:03.0: reg 0x10: [mem 0xe0000000-0xe0000fff]
[    0.166028] pci 0000:07:03.0: supports D1 D2
[    0.166030] pci 0000:07:03.0: PME# supported from D0 D1 D2 D3hot
[    0.166111] pci 0000:00:1e.0: PCI bridge to [bus 07] (subtractive decode)
[    0.166117] pci 0000:00:1e.0:   bridge window [mem 0xe0000000-0xe00fffff]
[    0.166123] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7 window] (subtractive decode)
[    0.166125] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff window] (subtractive decode)
[    0.166127] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff window] (subtractive decode)
[    0.166130] pci 0000:00:1e.0:   bridge window [mem 0x000e0000-0x000effff window] (subtractive decode)
[    0.166132] pci 0000:00:1e.0:   bridge window [mem 0xf8000000-0xfeafffff window] (subtractive decode)
[    0.166135] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xefffffff window] (subtractive decode)
[    0.166235] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    0.166301] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *9 10 11 12)
[    0.166365] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[    0.166428] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[    0.166494] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 *10 11 12)
[    0.166557] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 *9 10 11 12)
[    0.166622] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 *10 11 12)
[    0.166685] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 *11 12)
[    0.167211] ACPI: Enabled 4 GPEs in block 00 to 3F
[    0.168024] vgaarb: setting as boot device: PCI:0000:01:00.0
[    0.168028] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.168032] vgaarb: loaded
[    0.168034] vgaarb: bridge control possible 0000:01:00.0
[    0.168335] SCSI subsystem initialized
[    0.168360] libata version 3.00 loaded.
[    0.168360] ACPI: bus type USB registered
[    0.168360] usbcore: registered new interface driver usbfs
[    0.168360] usbcore: registered new interface driver hub
[    0.168360] usbcore: registered new device driver usb
[    0.168360] PCI: Using ACPI for IRQ routing
[    0.170672] PCI: pci_cache_line_size set to 64 bytes
[    0.170731] e820: reserve RAM buffer [mem 0x0009dc00-0x0009ffff]
[    0.170733] e820: reserve RAM buffer [mem 0xbee1f000-0xbfffffff]
[    0.170735] e820: reserve RAM buffer [mem 0xbeef6000-0xbfffffff]
[    0.170737] e820: reserve RAM buffer [mem 0xbefe6000-0xbfffffff]
[    0.170738] e820: reserve RAM buffer [mem 0xbeff3000-0xbfffffff]
[    0.170740] e820: reserve RAM buffer [mem 0xbf000000-0xbfffffff]
[    0.170877] NetLabel: Initializing
[    0.170878] NetLabel:  domain hash size = 128
[    0.170880] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.170896] NetLabel:  unlabeled traffic allowed by default
[    0.172068] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.172073] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.172077] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.176040] clocksource: Switched to clocksource hpet
[    0.185178] AppArmor: AppArmor Filesystem Enabled
[    0.185273] pnp: PnP ACPI init
[    0.185401] system 00:00: [mem 0xf0000000-0xf7ffffff] has been reserved
[    0.185407] system 00:00: [mem 0xfeb00000-0xfeb03fff] could not be reserved
[    0.185410] system 00:00: [mem 0xfed13000-0xfed13fff] has been reserved
[    0.185412] system 00:00: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.185415] system 00:00: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.185417] system 00:00: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.185420] system 00:00: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.185422] system 00:00: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.185425] system 00:00: [mem 0xfed45000-0xfed99fff] has been reserved
[    0.185428] system 00:00: [mem 0x000c0000-0x000dffff] could not be reserved
[    0.185430] system 00:00: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.185433] system 00:00: [mem 0xffc00000-0xffffffff] has been reserved
[    0.185438] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.185611] pnp 00:01: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.185674] system 00:02: [io  0x0500-0x053f] has been reserved
[    0.185677] system 00:02: [io  0x0400-0x047f] could not be reserved
[    0.185680] system 00:02: [io  0x0680-0x06ff] has been reserved
[    0.185684] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.185741] pnp 00:03: Plug and Play ACPI device, IDs WEC1000 PNP0c31 (active)
[    0.185808] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.186137] pnp 00:05: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.186217] pnp: PnP ACPI: found 6 devices
[    0.194541] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    0.194549] pci 0000:01:00.0: can't claim BAR 6 [mem 0xfffe0000-0xffffffff pref]: no compatible bridge window
[    0.194565] pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 02] add_size 1000
[    0.194569] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 02] add_size 200000 add_align 100000
[    0.194574] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff] to [bus 02] add_size 200000 add_align 100000
[    0.194582] pci 0000:00:1c.1: bridge window [io  0x1000-0x0fff] to [bus 03] add_size 1000
[    0.194585] pci 0000:00:1c.1: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 03] add_size 200000 add_align 100000
[    0.194589] pci 0000:00:1c.1: bridge window [mem 0x00100000-0x000fffff] to [bus 03] add_size 200000 add_align 100000
[    0.194597] pci 0000:00:1c.2: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 04] add_size 200000 add_align 100000
[    0.194605] pci 0000:00:1c.3: bridge window [io  0x1000-0x0fff] to [bus 05] add_size 1000
[    0.194608] pci 0000:00:1c.3: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 05] add_size 200000 add_align 100000
[    0.194611] pci 0000:00:1c.3: bridge window [mem 0x00100000-0x000fffff] to [bus 05] add_size 200000 add_align 100000
[    0.194618] pci 0000:00:1c.4: bridge window [io  0x1000-0x0fff] to [bus 06] add_size 1000
[    0.194621] pci 0000:00:1c.4: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 06] add_size 200000 add_align 100000
[    0.194624] pci 0000:00:1c.4: bridge window [mem 0x00100000-0x000fffff] to [bus 06] add_size 200000 add_align 100000
[    0.194637] pci 0000:00:1f.0: BAR 13: [io  size 0x0080] has bogus alignment
[    0.194641] pci 0000:00:1c.0: res[14]=[mem 0x00100000-0x000fffff] res_to_dev_res add_size 200000 min_align 100000
[    0.194644] pci 0000:00:1c.0: res[14]=[mem 0x00100000-0x002fffff] res_to_dev_res add_size 200000 min_align 100000
[    0.194646] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.194649] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x002fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.194652] pci 0000:00:1c.1: res[14]=[mem 0x00100000-0x000fffff] res_to_dev_res add_size 200000 min_align 100000
[    0.194654] pci 0000:00:1c.1: res[14]=[mem 0x00100000-0x002fffff] res_to_dev_res add_size 200000 min_align 100000
[    0.194657] pci 0000:00:1c.1: res[15]=[mem 0x00100000-0x000fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.194660] pci 0000:00:1c.1: res[15]=[mem 0x00100000-0x002fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.194662] pci 0000:00:1c.2: res[15]=[mem 0x00100000-0x000fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.194665] pci 0000:00:1c.2: res[15]=[mem 0x00100000-0x002fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.194668] pci 0000:00:1c.3: res[14]=[mem 0x00100000-0x000fffff] res_to_dev_res add_size 200000 min_align 100000
[    0.194670] pci 0000:00:1c.3: res[14]=[mem 0x00100000-0x002fffff] res_to_dev_res add_size 200000 min_align 100000
[    0.194673] pci 0000:00:1c.3: res[15]=[mem 0x00100000-0x000fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.194676] pci 0000:00:1c.3: res[15]=[mem 0x00100000-0x002fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.194678] pci 0000:00:1c.4: res[14]=[mem 0x00100000-0x000fffff] res_to_dev_res add_size 200000 min_align 100000
[    0.194681] pci 0000:00:1c.4: res[14]=[mem 0x00100000-0x002fffff] res_to_dev_res add_size 200000 min_align 100000
[    0.194683] pci 0000:00:1c.4: res[15]=[mem 0x00100000-0x000fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.194686] pci 0000:00:1c.4: res[15]=[mem 0x00100000-0x002fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.194689] pci 0000:00:1c.0: res[13]=[io  0x1000-0x0fff] res_to_dev_res add_size 1000 min_align 1000
[    0.194691] pci 0000:00:1c.0: res[13]=[io  0x1000-0x1fff] res_to_dev_res add_size 1000 min_align 1000
[    0.194694] pci 0000:00:1c.1: res[13]=[io  0x1000-0x0fff] res_to_dev_res add_size 1000 min_align 1000
[    0.194696] pci 0000:00:1c.1: res[13]=[io  0x1000-0x1fff] res_to_dev_res add_size 1000 min_align 1000
[    0.194699] pci 0000:00:1c.3: res[13]=[io  0x1000-0x0fff] res_to_dev_res add_size 1000 min_align 1000
[    0.194701] pci 0000:00:1c.3: res[13]=[io  0x1000-0x1fff] res_to_dev_res add_size 1000 min_align 1000
[    0.194704] pci 0000:00:1c.4: res[13]=[io  0x1000-0x0fff] res_to_dev_res add_size 1000 min_align 1000
[    0.194706] pci 0000:00:1c.4: res[13]=[io  0x1000-0x1fff] res_to_dev_res add_size 1000 min_align 1000
[    0.194712] pci 0000:00:1c.0: BAR 14: assigned [mem 0xf8000000-0xf81fffff]
[    0.194717] pci 0000:00:1c.0: BAR 15: assigned [mem 0xf8200000-0xf83fffff 64bit pref]
[    0.194720] pci 0000:00:1c.1: BAR 14: assigned [mem 0xf8400000-0xf85fffff]
[    0.194725] pci 0000:00:1c.1: BAR 15: assigned [mem 0xf8600000-0xf87fffff 64bit pref]
[    0.194729] pci 0000:00:1c.2: BAR 15: assigned [mem 0xf8800000-0xf89fffff 64bit pref]
[    0.194732] pci 0000:00:1c.3: BAR 14: assigned [mem 0xf8a00000-0xf8bfffff]
[    0.194737] pci 0000:00:1c.3: BAR 15: assigned [mem 0xf8c00000-0xf8dfffff 64bit pref]
[    0.194740] pci 0000:00:1c.4: BAR 14: assigned [mem 0xf8e00000-0xf8ffffff]
[    0.194744] pci 0000:00:1c.4: BAR 15: assigned [mem 0xf9000000-0xf91fffff 64bit pref]
[    0.194748] pci 0000:00:1c.0: BAR 13: assigned [io  0x4000-0x4fff]
[    0.194751] pci 0000:00:1c.1: BAR 13: assigned [io  0x5000-0x5fff]
[    0.194754] pci 0000:00:1c.3: BAR 13: assigned [io  0x6000-0x6fff]
[    0.194756] pci 0000:00:1c.4: BAR 13: assigned [io  0x7000-0x7fff]
[    0.194762] pci 0000:01:00.0: BAR 6: assigned [mem 0xe0340000-0xe035ffff pref]
[    0.194764] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.194767] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    0.194771] pci 0000:00:01.0:   bridge window [mem 0xe0300000-0xe03fffff]
[    0.194774] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.194778] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.194781] pci 0000:00:1c.0:   bridge window [io  0x4000-0x4fff]
[    0.194786] pci 0000:00:1c.0:   bridge window [mem 0xf8000000-0xf81fffff]
[    0.194790] pci 0000:00:1c.0:   bridge window [mem 0xf8200000-0xf83fffff 64bit pref]
[    0.194795] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.194798] pci 0000:00:1c.1:   bridge window [io  0x5000-0x5fff]
[    0.194803] pci 0000:00:1c.1:   bridge window [mem 0xf8400000-0xf85fffff]
[    0.194807] pci 0000:00:1c.1:   bridge window [mem 0xf8600000-0xf87fffff 64bit pref]
[    0.194812] pci 0000:00:1c.2: PCI bridge to [bus 04]
[    0.194815] pci 0000:00:1c.2:   bridge window [io  0x1000-0x1fff]
[    0.194820] pci 0000:00:1c.2:   bridge window [mem 0xe0100000-0xe01fffff]
[    0.194824] pci 0000:00:1c.2:   bridge window [mem 0xf8800000-0xf89fffff 64bit pref]
[    0.194829] pci 0000:00:1c.3: PCI bridge to [bus 05]
[    0.194832] pci 0000:00:1c.3:   bridge window [io  0x6000-0x6fff]
[    0.194837] pci 0000:00:1c.3:   bridge window [mem 0xf8a00000-0xf8bfffff]
[    0.194840] pci 0000:00:1c.3:   bridge window [mem 0xf8c00000-0xf8dfffff 64bit pref]
[    0.194846] pci 0000:00:1c.4: PCI bridge to [bus 06]
[    0.194849] pci 0000:00:1c.4:   bridge window [io  0x7000-0x7fff]
[    0.194853] pci 0000:00:1c.4:   bridge window [mem 0xf8e00000-0xf8ffffff]
[    0.194857] pci 0000:00:1c.4:   bridge window [mem 0xf9000000-0xf91fffff 64bit pref]
[    0.194863] pci 0000:00:1e.0: PCI bridge to [bus 07]
[    0.194867] pci 0000:00:1e.0:   bridge window [mem 0xe0000000-0xe00fffff]
[    0.194875] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7 window]
[    0.194877] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff window]
[    0.194880] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.194882] pci_bus 0000:00: resource 7 [mem 0x000e0000-0x000effff window]
[    0.194884] pci_bus 0000:00: resource 8 [mem 0xf8000000-0xfeafffff window]
[    0.194886] pci_bus 0000:00: resource 9 [mem 0xc0000000-0xefffffff window]
[    0.194889] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
[    0.194891] pci_bus 0000:01: resource 1 [mem 0xe0300000-0xe03fffff]
[    0.194893] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.194895] pci_bus 0000:02: resource 0 [io  0x4000-0x4fff]
[    0.194898] pci_bus 0000:02: resource 1 [mem 0xf8000000-0xf81fffff]
[    0.194900] pci_bus 0000:02: resource 2 [mem 0xf8200000-0xf83fffff 64bit pref]
[    0.194902] pci_bus 0000:03: resource 0 [io  0x5000-0x5fff]
[    0.194904] pci_bus 0000:03: resource 1 [mem 0xf8400000-0xf85fffff]
[    0.194906] pci_bus 0000:03: resource 2 [mem 0xf8600000-0xf87fffff 64bit pref]
[    0.194908] pci_bus 0000:04: resource 0 [io  0x1000-0x1fff]
[    0.194911] pci_bus 0000:04: resource 1 [mem 0xe0100000-0xe01fffff]
[    0.194913] pci_bus 0000:04: resource 2 [mem 0xf8800000-0xf89fffff 64bit pref]
[    0.194915] pci_bus 0000:05: resource 0 [io  0x6000-0x6fff]
[    0.194917] pci_bus 0000:05: resource 1 [mem 0xf8a00000-0xf8bfffff]
[    0.194919] pci_bus 0000:05: resource 2 [mem 0xf8c00000-0xf8dfffff 64bit pref]
[    0.194922] pci_bus 0000:06: resource 0 [io  0x7000-0x7fff]
[    0.194924] pci_bus 0000:06: resource 1 [mem 0xf8e00000-0xf8ffffff]
[    0.194926] pci_bus 0000:06: resource 2 [mem 0xf9000000-0xf91fffff 64bit pref]
[    0.194928] pci_bus 0000:07: resource 1 [mem 0xe0000000-0xe00fffff]
[    0.194931] pci_bus 0000:07: resource 4 [io  0x0000-0x0cf7 window]
[    0.194933] pci_bus 0000:07: resource 5 [io  0x0d00-0xffff window]
[    0.194935] pci_bus 0000:07: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.194937] pci_bus 0000:07: resource 7 [mem 0x000e0000-0x000effff window]
[    0.194939] pci_bus 0000:07: resource 8 [mem 0xf8000000-0xfeafffff window]
[    0.194942] pci_bus 0000:07: resource 9 [mem 0xc0000000-0xefffffff window]
[    0.194981] NET: Registered protocol family 2
[    0.195251] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
[    0.195506] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.195828] TCP: Hash tables configured (established 65536 bind 65536)
[    0.195883] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.195937] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.196072] NET: Registered protocol family 1
[    0.196485] pci 0000:01:00.0: Video device with shadowed ROM
[    0.196495] PCI: CLS 64 bytes, default 64
[    0.196565] Trying to unpack rootfs image as initramfs...
[    0.806698] Freeing initrd memory: 33880K (ffff880033dc4000 - ffff880035eda000)
[    0.806796] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.806799] software IO TLB [mem 0xbae1f000-0xbee1f000] (64MB) mapped at [ffff8800bae1f000-ffff8800bee1efff]
[    0.807004] microcode: CPU0 sig=0x6fb, pf=0x10, revision=0xb6
[    0.807018] microcode: CPU1 sig=0x6fb, pf=0x10, revision=0xb6
[    0.807033] microcode: CPU2 sig=0x6fb, pf=0x10, revision=0xb6
[    0.807047] microcode: CPU3 sig=0x6fb, pf=0x10, revision=0xb6
[    0.807140] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.807223] Scanning for low memory corruption every 60 seconds
[    0.807563] futex hash table entries: 1024 (order: 4, 65536 bytes)
[    0.807599] audit: initializing netlink subsys (disabled)
[    0.807623] audit: type=2000 audit(1452942702.804:1): initialized
[    0.807928] Initialise system trusted keyring
[    0.808072] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.810339] zbud: loaded
[    0.810636] VFS: Disk quotas dquot_6.6.0
[    0.810704] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.811417] fuse init (API version 7.23)
[    0.811672] Key type big_key registered
[    0.812336] Key type asymmetric registered
[    0.812341] Asymmetric key parser 'x509' registered
[    0.812368] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 249)
[    0.812422] io scheduler noop registered
[    0.812427] io scheduler deadline registered (default)
[    0.812489] io scheduler cfq registered
[    0.813136] pcieport 0000:00:1c.0: enabling device (0000 -> 0003)
[    0.813430] pcieport 0000:00:1c.1: enabling device (0000 -> 0003)
[    0.814008] pcieport 0000:00:1c.3: enabling device (0000 -> 0003)
[    0.814298] pcieport 0000:00:1c.4: enabling device (0000 -> 0003)
[    0.814500] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.814509] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.814552] vesafb: mode is 1400x1050x32, linelength=5632, pages=0
[    0.814553] vesafb: scrolling: redraw
[    0.814556] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[    0.814572] vesafb: framebuffer at 0xc0000000, mapped to 0xffffc90001000000, using 5824k, total 5824k
[    0.814685] Console: switching to colour frame buffer device 175x65
[    0.814722] fb0: VESA VGA frame buffer device
[    0.814741] intel_idle: does not run on family 6 model 15
[    0.814828] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
[    0.814832] ACPI: Sleep Button [SLPB]
[    0.814891] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.814894] ACPI: Power Button [PWRF]
[    0.814981] Monitor-Mwait will be used to enter C-1 state
[    0.815678] GHES: HEST is not enabled!
[    0.815785] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.836155] 00:05: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    0.837923] Linux agpgart interface v0.103
[    0.838012] agpgart-intel 0000:00:00.0: Intel Q35 Chipset
[    0.838030] agpgart-intel 0000:00:00.0: detected gtt size: 524288K total, 262144K mappable
[    0.839184] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    0.839335] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    0.860059] tpm_tis 00:03: 1.2 TPM (device-id 0xFE, rev-id 70)
[    0.959967] brd: module loaded
[    0.961798] loop: module loaded
[    0.962319] libphy: Fixed MDIO Bus: probed
[    0.962323] tun: Universal TUN/TAP device driver, 1.6
[    0.962325] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.962373] PPP generic driver version 2.4.2
[    0.962457] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.962462] ehci-pci: EHCI PCI platform driver
[    0.962625] ehci-pci 0000:00:1a.7: EHCI Host Controller
[    0.962633] ehci-pci 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.962645] ehci-pci 0000:00:1a.7: debug port 1
[    0.966557] ehci-pci 0000:00:1a.7: cache line size of 64 is not supported
[    0.966571] ehci-pci 0000:00:1a.7: irq 17, io mem 0xe04a5c00
[    0.976031] ehci-pci 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.976096] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.976100] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.976104] usb usb1: Product: EHCI Host Controller
[    0.976107] usb usb1: Manufacturer: Linux 4.3.0-5-generic ehci_hcd
[    0.976110] usb usb1: SerialNumber: 0000:00:1a.7
[    0.976280] hub 1-0:1.0: USB hub found
[    0.976287] hub 1-0:1.0: 6 ports detected
[    0.976605] ehci-pci 0000:00:1d.7: EHCI Host Controller
[    0.976611] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.976622] ehci-pci 0000:00:1d.7: debug port 1
[    0.980533] ehci-pci 0000:00:1d.7: cache line size of 64 is not supported
[    0.980544] ehci-pci 0000:00:1d.7: irq 23, io mem 0xe04a5800
[    0.992044] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.992109] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.992113] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.992116] usb usb2: Product: EHCI Host Controller
[    0.992119] usb usb2: Manufacturer: Linux 4.3.0-5-generic ehci_hcd
[    0.992123] usb usb2: SerialNumber: 0000:00:1d.7
[    0.992273] hub 2-0:1.0: USB hub found
[    0.992281] hub 2-0:1.0: 6 ports detected
[    0.992452] ehci-platform: EHCI generic platform driver
[    0.992464] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.992468] ohci-pci: OHCI PCI platform driver
[    0.992483] ohci-platform: OHCI generic platform driver
[    0.992495] uhci_hcd: USB Universal Host Controller Interface driver
[    0.992636] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.992642] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.992649] uhci_hcd 0000:00:1a.0: detected 2 ports
[    0.992671] uhci_hcd 0000:00:1a.0: irq 18, io base 0x000030e0
[    0.992717] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    0.992719] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.992721] usb usb3: Product: UHCI Host Controller
[    0.992724] usb usb3: Manufacturer: Linux 4.3.0-5-generic uhci_hcd
[    0.992726] usb usb3: SerialNumber: 0000:00:1a.0
[    0.992840] hub 3-0:1.0: USB hub found
[    0.992848] hub 3-0:1.0: 2 ports detected
[    0.993072] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.993079] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.993085] uhci_hcd 0000:00:1a.1: detected 2 ports
[    0.993109] uhci_hcd 0000:00:1a.1: irq 21, io base 0x000030c0
[    0.993154] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    0.993157] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.993159] usb usb4: Product: UHCI Host Controller
[    0.993161] usb usb4: Manufacturer: Linux 4.3.0-5-generic uhci_hcd
[    0.993163] usb usb4: SerialNumber: 0000:00:1a.1
[    0.993277] hub 4-0:1.0: USB hub found
[    0.993284] hub 4-0:1.0: 2 ports detected
[    0.993510] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.993517] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.993523] uhci_hcd 0000:00:1a.2: detected 2 ports
[    0.993540] uhci_hcd 0000:00:1a.2: irq 17, io base 0x000030a0
[    0.993584] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    0.993586] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.993589] usb usb5: Product: UHCI Host Controller
[    0.993591] usb usb5: Manufacturer: Linux 4.3.0-5-generic uhci_hcd
[    0.993593] usb usb5: SerialNumber: 0000:00:1a.2
[    0.993707] hub 5-0:1.0: USB hub found
[    0.993714] hub 5-0:1.0: 2 ports detected
[    0.993936] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.993943] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.993949] uhci_hcd 0000:00:1d.0: detected 2 ports
[    0.993966] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00003080
[    0.994009] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    0.994012] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.994014] usb usb6: Product: UHCI Host Controller
[    0.994016] usb usb6: Manufacturer: Linux 4.3.0-5-generic uhci_hcd
[    0.994018] usb usb6: SerialNumber: 0000:00:1d.0
[    0.994133] hub 6-0:1.0: USB hub found
[    0.994140] hub 6-0:1.0: 2 ports detected
[    0.994367] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.994375] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.994382] uhci_hcd 0000:00:1d.1: detected 2 ports
[    0.994404] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00003060
[    0.994454] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    0.994457] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.994459] usb usb7: Product: UHCI Host Controller
[    0.994461] usb usb7: Manufacturer: Linux 4.3.0-5-generic uhci_hcd
[    0.994463] usb usb7: SerialNumber: 0000:00:1d.1
[    0.994577] hub 7-0:1.0: USB hub found
[    0.994585] hub 7-0:1.0: 2 ports detected
[    0.994805] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.994811] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.994819] uhci_hcd 0000:00:1d.2: detected 2 ports
[    0.994836] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00003040
[    0.994881] usb usb8: New USB device found, idVendor=1d6b, idProduct=0001
[    0.994883] usb usb8: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.994886] usb usb8: Product: UHCI Host Controller
[    0.994888] usb usb8: Manufacturer: Linux 4.3.0-5-generic uhci_hcd
[    0.994890] usb usb8: SerialNumber: 0000:00:1d.2
[    0.995007] hub 8-0:1.0: USB hub found
[    0.995015] hub 8-0:1.0: 2 ports detected
[    0.995163] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.998363] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.998368] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.998530] mousedev: PS/2 mouse device common for all mice
[    0.998680] rtc_cmos 00:01: RTC can wake from S4
[    0.998800] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    0.998822] rtc_cmos 00:01: alarms up to one month, 114 bytes nvram, hpet irqs
[    0.998831] i2c /dev entries driver
[    0.998900] device-mapper: uevent: version 1.0.3
[    0.998981] device-mapper: ioctl: 4.33.0-ioctl (2015-8-18) initialised: dm-devel@redhat.com
[    0.999002] ledtrig-cpu: registered to indicate activity on CPUs
[    0.999425] NET: Registered protocol family 10
[    0.999644] NET: Registered protocol family 17
[    0.999658] Key type dns_resolver registered
[    1.000067] registered taskstats version 1
[    1.000082] Loading compiled-in X.509 certificates
[    1.001226] Loaded X.509 cert 'Build time autogenerated kernel key: 7c724264be95f5251ba6dcfc79faa85dca02c8a4'
[    1.001248] zswap: loaded using pool lzo/zbud
[    1.003758] Key type trusted registered
[    1.007998] Key type encrypted registered
[    1.008005] AppArmor: AppArmor sha1 policy hashing enabled
[    1.244082] evm: HMAC attrs: 0x1
[    1.244484]   Magic number: 0:951:175
[    1.244492] misc network_throughput: hash matches
[    1.244563] acpi device:0b: hash matches
[    1.244625] rtc_cmos 00:01: setting system clock to 2016-01-16 11:11:44 UTC (1452942704)
[    1.245140] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.245142] EDD information not available.
[    1.245227] PM: Hibernation image not present or could not be loaded.
[    1.245747] Freeing unused kernel memory: 1464K (ffffffff81f3a000 - ffffffff820a8000)
[    1.245749] Write protecting the kernel read-only data: 14336k
[    1.246619] Freeing unused kernel memory: 2032K (ffff880001804000 - ffff880001a00000)
[    1.246758] Freeing unused kernel memory: 244K (ffff880001dc3000 - ffff880001e00000)
[    1.261334] random: systemd-udevd urandom read with 5 bits of entropy available
[    1.288030] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.300622] FUJITSU Extended Socket Network Device Driver - version 1.0 - Copyright (c) 2015 FUJITSU LIMITED
[    1.315831] [drm] Initialized drm 1.1.0 20060810
[    1.316982] pps_core: LinuxPPS API ver. 1 registered
[    1.316985] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    1.318600] PTP clock support registered
[    1.327143] e1000e: Intel(R) PRO/1000 Network Driver - 3.2.6-k
[    1.327145] e1000e: Copyright(c) 1999 - 2015 Intel Corporation.
[    1.327352] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    1.327715] scsi host0: pata_marvell
[    1.327918] scsi host1: pata_marvell
[    1.327985] ata1: PATA max UDMA/100 cmd 0x1018 ctl 0x1024 bmdma 0x1000 irq 18
[    1.327987] ata2: DUMMY
[    1.351834] [drm] radeon kernel modesetting enabled.
[    1.354562] AMD IOMMUv2 driver by Joerg Roedel <jroedel@suse.de>
[    1.354566] AMD IOMMUv2 functionality not available on this system
[    1.357943] CRAT table not found
[    1.357945] Finished initializing topology ret=0
[    1.358010] kfd kfd: Initialized module
[    1.358406] checking generic (c0000000 5b0000) vs hw (c0000000 10000000)
[    1.358409] fb: switching to radeondrmfb from VESA VGA
[    1.358443] Console: switching to colour dummy device 80x25
[    1.358736] [drm] initializing kernel modesetting (CAICOS 0x1002:0x6779 0x174B:0xE164).
[    1.358749] [drm] register mmio base: 0xE0300000
[    1.358750] [drm] register mmio size: 131072
[    1.359503] ATOM BIOS: AMD
[    1.359969] radeon 0000:01:00.0: VRAM: 512M 0x0000000000000000 - 0x000000001FFFFFFF (512M used)
[    1.359972] radeon 0000:01:00.0: GTT: 1024M 0x0000000020000000 - 0x000000005FFFFFFF
[    1.359974] [drm] Detected VRAM RAM=512M, BAR=256M
[    1.359980] [drm] RAM width 64bits DDR
[    1.360022] usb 2-4: new high-speed USB device number 3 using ehci-pci
[    1.360217] [TTM] Zone  kernel: Available graphics memory: 4046282 kiB
[    1.360219] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB
[    1.360220] [TTM] Initializing pool allocator
[    1.360226] [TTM] Initializing DMA pool allocator
[    1.360252] [drm] radeon: 512M of VRAM memory ready
[    1.360253] [drm] radeon: 1024M of GTT memory ready.
[    1.360266] [drm] Loading CAICOS Microcode
[    1.360388] [drm] Internal thermal controller without fan control
[    1.364660] [drm] radeon: dpm initialized
[    1.364815] [drm] GART: num cpu pages 262144, num gpu pages 262144
[    1.382039] [drm] PCIE GART of 1024M enabled (table at 0x0000000000274000).
[    1.382163] radeon 0000:01:00.0: WB enabled
[    1.382167] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000020000c00 and cpu addr 0xffff880035b98c00
[    1.382169] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000020000c0c and cpu addr 0xffff880035b98c0c
[    1.383639] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x0000000000072118 and cpu addr 0xffffc90001832118
[    1.383644] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    1.383645] [drm] Driver supports precise vblank timestamp query.
[    1.383647] radeon 0000:01:00.0: radeon: MSI limited to 32-bit
[    1.383824] radeon 0000:01:00.0: radeon: using MSI.
[    1.383861] [drm] radeon: irq initialized.
[    1.400077] firewire_ohci 0000:07:03.0: added OHCI v1.0 device as card 0, 8 IR + 8 IT contexts, quirks 0x0
[    1.400513] [drm] ring test on 0 succeeded in 2 usecs
[    1.400525] [drm] ring test on 3 succeeded in 6 usecs
[    1.425994] usb 1-1: New USB device found, idVendor=058f, idProduct=6362
[    1.425998] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.426000] usb 1-1: Product: Mass Storage Device
[    1.426003] usb 1-1: Manufacturer: Generic
[    1.426005] usb 1-1: SerialNumber: 058F63626376
[    1.430170] usb-storage 1-1:1.0: USB Mass Storage device detected
[    1.430351] scsi host2: usb-storage 1-1:1.0
[    1.430436] usbcore: registered new interface driver usb-storage
[    1.432017] usbcore: registered new interface driver uas
[    1.432051] usb 7-1: new low-speed USB device number 2 using uhci_hcd
[    1.492335] usb 2-4: New USB device found, idVendor=0424, idProduct=2514
[    1.492338] usb 2-4: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.492501] hub 2-4:1.0: USB hub found
[    1.492588] hub 2-4:1.0: 4 ports detected
[    1.524362] ata1.00: ATAPI: LITE-ON DVDRW SHW-16H5S, LS0N, max UDMA/66
[    1.524618] ata1.01: HPA detected: current 976771055, native 976773168
[    1.524622] ata1.01: ATA-8: WDC WD5000AAKB-00H8A0, 05.04E05, max UDMA/133
[    1.524624] ata1.01: 976771055 sectors, multi 16: LBA48 
[    1.568361] ata1.00: configured for UDMA/66
[    1.576302] [drm] ring test on 5 succeeded in 2 usecs
[    1.576311] [drm] UVD initialized successfully.
[    1.576759] [drm] ib test on ring 0 succeeded in 0 usecs
[    1.576808] [drm] ib test on ring 3 succeeded in 0 usecs
[    1.592675] ata1.01: configured for UDMA/100
[    1.594187] scsi 0:0:0:0: CD-ROM            LITE-ON  DVDRW SHW-16H5S  LS0N PQ: 0 ANSI: 5
[    1.609962] sr 0:0:0:0: [sr0] scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    1.609965] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.610109] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.610186] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.610816] scsi 0:0:1:0: Direct-Access     ATA      WDC WD5000AAKB-0 4E05 PQ: 0 ANSI: 5
[    1.610993] sd 0:0:1:0: [sda] 976771055 512-byte logical blocks: (500 GB/465 GiB)
[    1.611023] sd 0:0:1:0: Attached scsi generic sg1 type 0
[    1.611047] sd 0:0:1:0: [sda] Write Protect is off
[    1.611050] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
[    1.611086] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.622220]  sda: sda1
[    1.622448] sd 0:0:1:0: [sda] Attached SCSI disk
[    1.650722] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) 00:1c:c0:81:f9:c7
[    1.650727] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    1.650759] e1000e 0000:00:19.0 eth0: MAC: 7, PHY: 6, PBA No: FFFFFF-0FF
[    1.650938] ahci 0000:00:1f.2: version 3.0
[    1.651171] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    1.651175] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pmp pio slum part ccc ems 
[    1.651576] e1000e 0000:00:19.0 enp0s25: renamed from eth0
[    1.689008] scsi host3: ahci
[    1.689130] scsi host4: ahci
[    1.689305] scsi host5: ahci
[    1.689417] scsi host6: ahci
[    1.689585] scsi host7: ahci
[    1.689692] scsi host8: ahci
[    1.689759] ata3: SATA max UDMA/133 abar m2048@0xe04a5000 port 0xe04a5100 irq 32
[    1.689762] ata4: SATA max UDMA/133 abar m2048@0xe04a5000 port 0xe04a5180 irq 32
[    1.689765] ata5: SATA max UDMA/133 abar m2048@0xe04a5000 port 0xe04a5200 irq 32
[    1.689767] ata6: SATA max UDMA/133 abar m2048@0xe04a5000 port 0xe04a5280 irq 32
[    1.689769] ata7: SATA max UDMA/133 abar m2048@0xe04a5000 port 0xe04a5300 irq 32
[    1.689771] ata8: SATA max UDMA/133 abar m2048@0xe04a5000 port 0xe04a5380 irq 32
[    1.692051] usb 7-1: New USB device found, idVendor=04d9, idProduct=1603
[    1.692055] usb 7-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.692058] usb 7-1: Product: USB Keyboard
[    1.692060] usb 7-1: Manufacturer:  
[    1.703463] hidraw: raw HID events driver (C) Jiri Kosina
[    1.744042] usb 8-2: new low-speed USB device number 2 using uhci_hcd
[    1.808038] tsc: Refined TSC clocksource calibration: 2388.000 MHz
[    1.808043] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x226bef96e18, max_idle_ns: 440795310092 ns
[    1.821370] usbcore: registered new interface driver usbhid
[    1.821373] usbhid: USB HID core driver
[    1.823423] input:   USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/0003:04D9:1603.0001/input/input5
[    1.876306] hid-generic 0003:04D9:1603.0001: input,hidraw0: USB HID v1.10 Keyboard [  USB Keyboard] on usb-0000:00:1d.1-1/input0
[    1.890147] input:   USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.1/0003:04D9:1603.0002/input/input6
[    1.904158] firewire_core 0000:07:03.0: created device fw0: GUID 00902700022781ba, S400
[    1.928045] usb 8-2: New USB device found, idVendor=413c, idProduct=3012
[    1.928051] usb 8-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.928054] usb 8-2: Product: Dell USB Optical Mouse
[    1.928058] usb 8-2: Manufacturer: Dell
[    1.944211] hid-generic 0003:04D9:1603.0002: input,hidraw1: USB HID v1.10 Device [  USB Keyboard] on usb-0000:00:1d.1-1/input1
[    1.944524] input: Dell Dell USB Optical Mouse as /devices/pci0000:00/0000:00:1d.2/usb8/8-2/8-2:1.0/0003:413C:3012.0003/input/input7
[    1.944668] hid-generic 0003:413C:3012.0003: input,hidraw2: USB HID v1.11 Mouse [Dell Dell USB Optical Mouse] on usb-0000:00:1d.2-2/input0
[    2.012042] ata8: SATA link down (SStatus 0 SControl 300)
[    2.012070] ata6: SATA link down (SStatus 0 SControl 300)
[    2.012105] ata7: SATA link down (SStatus 0 SControl 300)
[    2.016034] ata5: SATA link down (SStatus 0 SControl 300)
[    2.188032] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.188050] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.188537] ata3.00: HPA detected: current 78163247, native 78165360
[    2.188605] ata3.00: ATA-7: WDC WD400BD-55MTA1, 10.01E01, max UDMA/133
[    2.188609] ata3.00: 78163247 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    2.189202] ata3.00: configured for UDMA/133
[    2.189390] scsi 3:0:0:0: Direct-Access     ATA      WDC WD400BD-55MT 1E01 PQ: 0 ANSI: 5
[    2.189598] sd 3:0:0:0: [sdb] 78163247 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    2.189654] sd 3:0:0:0: Attached scsi generic sg2 type 0
[    2.189658] sd 3:0:0:0: [sdb] Write Protect is off
[    2.189662] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.189686] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.210330]  sdb: sdb1
[    2.210656] sd 3:0:0:0: [sdb] Attached SCSI disk
[    2.216652] ata4.00: ATA-8: ST3640323AS, SD35, max UDMA/133
[    2.216657] ata4.00: 1250263728 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    2.224065] [drm] ib test on ring 5 succeeded
[    2.225331] [drm] Radeon Display Connectors
[    2.225333] [drm] Connector 0:
[    2.225335] [drm]   HDMI-A-1
[    2.225336] [drm]   HPD2
[    2.225338] [drm]   DDC: 0x6440 0x6440 0x6444 0x6444 0x6448 0x6448 0x644c 0x644c
[    2.225339] [drm]   Encoders:
[    2.225341] [drm]     DFP1: INTERNAL_UNIPHY1
[    2.225342] [drm] Connector 1:
[    2.225343] [drm]   DVI-D-1
[    2.225344] [drm]   HPD4
[    2.225346] [drm]   DDC: 0x6460 0x6460 0x6464 0x6464 0x6468 0x6468 0x646c 0x646c
[    2.225347] [drm]   Encoders:
[    2.225349] [drm]     DFP2: INTERNAL_UNIPHY
[    2.225350] [drm] Connector 2:
[    2.225351] [drm]   VGA-1
[    2.225353] [drm]   DDC: 0x6430 0x6430 0x6434 0x6434 0x6438 0x6438 0x643c 0x643c
[    2.225354] [drm]   Encoders:
[    2.225355] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    2.258504] ata4.00: configured for UDMA/133
[    2.258619] scsi 4:0:0:0: Direct-Access     ATA      ST3640323AS      SD35 PQ: 0 ANSI: 5
[    2.258860] sd 4:0:0:0: Attached scsi generic sg3 type 0
[    2.258863] sd 4:0:0:0: [sdc] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
[    2.258916] sd 4:0:0:0: [sdc] Write Protect is off
[    2.258922] sd 4:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    2.258952] sd 4:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.304737]  sdc: sdc1 sdc2
[    2.304998] sd 4:0:0:0: [sdc] Attached SCSI disk
[    2.338102] [drm] fb mappable at 0xC0475000
[    2.338104] [drm] vram apper at 0xC0000000
[    2.338105] [drm] size 8294400
[    2.338107] [drm] fb depth is 24
[    2.338108] [drm]    pitch is 7680
[    2.338178] fbcon: radeondrmfb (fb0) is primary device
[    2.338268] Console: switching to colour frame buffer device 160x64
[    2.338304] radeon 0000:01:00.0: fb0: radeondrmfb frame buffer device
[    2.348115] [drm] Initialized radeon 2.43.0 20080528 for 0000:01:00.0 on minor 0
[    2.349144] [drm] Memory usable by graphics device = 512M
[    2.349146] [drm] Replacing VGA console driver
[    2.356246] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    2.356249] [drm] Driver supports precise vblank timestamp query.
[    2.356307] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    2.357287] [drm] initialized overlay support
[    2.357304] [drm] Initialized i915 1.6.0 20150731 for 0000:00:02.0 on minor 1
[    2.428889] scsi 2:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[    2.429508] scsi 2:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[    2.430137] scsi 2:0:0:2: Direct-Access     Generic  USB xD/SM Reader 1.02 PQ: 0 ANSI: 0
[    2.430760] scsi 2:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[    2.431234] sd 2:0:0:0: Attached scsi generic sg4 type 0
[    2.431694] sd 2:0:0:1: Attached scsi generic sg5 type 0
[    2.431911] sd 2:0:0:2: Attached scsi generic sg6 type 0
[    2.432125] sd 2:0:0:3: Attached scsi generic sg7 type 0
[    2.439589] i915 0000:00:02.0: fb1: inteldrmfb frame buffer device
[    2.449507] sd 2:0:0:1: [sde] Attached SCSI removable disk
[    2.461376] sd 2:0:0:0: [sdd] Attached SCSI removable disk
[    2.461997] sd 2:0:0:2: [sdf] Attached SCSI removable disk
[    2.463254] sd 2:0:0:3: [sdg] Attached SCSI removable disk
[    2.808098] clocksource: Switched to clocksource tsc
[    4.324042] floppy0: no floppy controllers found
[    4.366969] random: nonblocking pool is initialized
[    4.540505] EXT4-fs (sdc1): mounted filesystem with ordered data mode. Opts: (null)
[    5.198803] systemd[1]: RTC configured in localtime, applying delta of 60 minutes to system time.
[    5.432622] systemd[1]: Failed to insert module 'kdbus': Function not implemented
[    5.596181] systemd[1]: systemd 228 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ -LZ4 +SECCOMP +BLKID +ELFUTILS +KMOD -IDN)
[    5.596368] systemd[1]: Detected architecture x86-64.
[    5.596849] systemd[1]: Set hostname to <mainframe>.
[    6.425520] systemd[1]: Listening on Journal Audit Socket.
[    6.425725] systemd[1]: Created slice System Slice.
[    6.425744] systemd[1]: Reached target User and Group Name Lookups.
[    6.425785] systemd[1]: Listening on udev Control Socket.
[    6.425924] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[    6.426058] systemd[1]: Created slice system-getty.slice.
[    6.426170] systemd[1]: Created slice User and Session Slice.
[    6.426182] systemd[1]: Reached target Slices.
[    6.426192] systemd[1]: Reached target Encrypted Volumes.
[    6.426235] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[    6.426283] systemd[1]: Listening on Journal Socket.
[    6.427008] systemd[1]: Starting Create list of required static device nodes for the current kernel...
[    6.427889] systemd[1]: Mounting POSIX Message Queue File System...
[    6.428727] systemd[1]: Started Read required files in advance.
[    6.429829] systemd[1]: Starting Braille Device Support...
[    6.429919] systemd[1]: Listening on Journal Socket (/dev/log).
[    6.429974] systemd[1]: Listening on Syslog Socket.
[    6.430818] systemd[1]: Starting Journal Service...
[    6.457622] systemd[1]: Listening on /dev/initctl Compatibility Named Pipe.
[    6.457662] systemd[1]: Reached target Remote File Systems (Pre).
[    6.457689] systemd[1]: Reached target Remote File Systems.
[    6.458482] systemd[1]: Mounting Huge Pages File System...
[    6.458560] systemd[1]: Listening on udev Kernel Socket.
[    6.700830] systemd[1]: Starting Uncomplicated firewall...
[    6.700893] systemd[1]: Listening on fsck to fsckd communication Socket.
[    6.704525] systemd[1]: Starting Load Kernel Modules...
[    6.705262] systemd[1]: Mounting Debug File System...
[    6.708151] systemd[1]: Started Create list of required static device nodes for the current kernel.
[    6.710164] systemd[1]: Starting Create Static Device Nodes in /dev...
[    6.808942] systemd[1]: Started Uncomplicated firewall.
[    6.877514] systemd[1]: Mounted Debug File System.
[    6.877557] systemd[1]: Mounted Huge Pages File System.
[    6.877578] systemd[1]: Mounted POSIX Message Queue File System.
[    7.030772] systemd[1]: Started Load Kernel Modules.
[    7.031728] systemd[1]: Mounting FUSE Control File System...
[    7.032535] systemd[1]: Starting Apply Kernel Variables...
[    7.037335] systemd[1]: Mounted FUSE Control File System.
[    7.066191] systemd[1]: Started Journal Service.
[    9.237788] EXT4-fs (sdc1): re-mounted. Opts: errors=remount-ro
[    9.396172] systemd-journald[277]: Received request to flush runtime journal from PID 1
[   10.340372] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.497677] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x000000000000050C-0x000000000000050F (\IGPO) (20150818/utaddress-254)
[   10.497685] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   10.697255] snd_hda_intel 0000:01:00.1: Handle VGA-switcheroo audio client
[   10.714801] snd_hda_codec_hdmi hdaudioC1D0: HDMI ATI/AMD: no speaker allocation for ELD
[   10.715441] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input8
[   10.728667] snd_hda_codec_realtek hdaudioC0D2: autoconfig for ALC268: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:line
[   10.728672] snd_hda_codec_realtek hdaudioC0D2:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   10.728675] snd_hda_codec_realtek hdaudioC0D2:    hp_outs=1 (0x15/0x0/0x0/0x0/0x0)
[   10.728677] snd_hda_codec_realtek hdaudioC0D2:    mono: mono_out=0x0
[   10.728680] snd_hda_codec_realtek hdaudioC0D2:    inputs:
[   10.728682] snd_hda_codec_realtek hdaudioC0D2:      Rear Mic=0x18
[   10.728685] snd_hda_codec_realtek hdaudioC0D2:      Front Mic=0x1a
[   10.728687] snd_hda_codec_realtek hdaudioC0D2:      Line=0x19
[   10.735202] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   10.735286] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   10.735362] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   10.735439] input: HDA Intel Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   10.735518] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   10.816201] snd_hda_codec_hdmi hdaudioC1D0: HDMI ATI/AMD: no speaker allocation for ELD
[   11.116098] snd_hda_codec_hdmi hdaudioC1D0: HDMI ATI/AMD: no speaker allocation for ELD
[   11.159253] coretemp coretemp.0: Using relative temperature scale!
[   11.159272] coretemp coretemp.0: Using relative temperature scale!
[   11.159284] coretemp coretemp.0: Using relative temperature scale!
[   11.159298] coretemp coretemp.0: Using relative temperature scale!
[   11.420048] snd_hda_codec_hdmi hdaudioC1D0: HDMI ATI/AMD: no speaker allocation for ELD
[   11.462660] ppdev: user-space parallel port driver
[   11.470180] gpio_ich: GPIO from 451 to 511 on gpio_ich
[   11.720089] snd_hda_codec_hdmi hdaudioC1D0: HDMI ATI/AMD: no speaker allocation for ELD
[   12.020110] snd_hda_codec_hdmi hdaudioC1D0: HDMI ATI/AMD: no speaker allocation for ELD
[   12.320111] snd_hda_codec_hdmi hdaudioC1D0: HDMI ATI/AMD: no speaker allocation for ELD
[   12.620272] snd_hda_codec_hdmi hdaudioC1D0: HDMI ATI/AMD: no speaker allocation for ELD
[   12.728712] Adding 5990396k swap on /dev/sdc2.  Priority:-1 extents:1 across:5990396k FS
[   12.920059] snd_hda_codec_hdmi hdaudioC1D0: HDMI ATI/AMD: no speaker allocation for ELD
[   13.220046] snd_hda_codec_hdmi hdaudioC1D0: HDMI ATI/AMD: no speaker allocation for ELD
[   13.372040] floppy0: no floppy controllers found
[   13.531368] audit: type=1400 audit(1452939116.782:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=591 comm="apparmor_parser"
[   13.531379] audit: type=1400 audit(1452939116.782:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=591 comm="apparmor_parser"
[   13.583879] audit: type=1400 audit(1452939116.834:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=591 comm="apparmor_parser"
[   13.583888] audit: type=1400 audit(1452939116.834:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=591 comm="apparmor_parser"
[   13.583895] audit: type=1400 audit(1452939116.834:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=591 comm="apparmor_parser"
[   13.583901] audit: type=1400 audit(1452939116.834:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=591 comm="apparmor_parser"
[   13.689054] audit: type=1400 audit(1452939116.942:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince" pid=591 comm="apparmor_parser"
[   13.689065] audit: type=1400 audit(1452939116.942:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=591 comm="apparmor_parser"
[   13.689072] audit: type=1400 audit(1452939116.942:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-previewer" pid=591 comm="apparmor_parser"
[   13.689079] audit: type=1400 audit(1452939116.942:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=591 comm="apparmor_parser"
[   14.389799] cgroup: new mount options do not match the existing superblock, will be ignored
[   16.694762] IPv6: ADDRCONF(NETDEV_UP): enp0s25: link is not ready
[   17.156458] IPv6: ADDRCONF(NETDEV_UP): enp0s25: link is not ready
[   18.508883] e1000e: enp0s25 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
[   18.508993] e1000e 0000:00:19.0 enp0s25: 10/100 speed: disabling TSO
[   18.509025] IPv6: ADDRCONF(NETDEV_CHANGE): enp0s25: link becomes ready
[  227.445341] show_signal_msg: 18 callbacks suppressed
[  227.445348] gvfsd-network[2689]: segfault at 6c00000001 ip 00007f4e5c047a75 sp 00007ffd1f039ce0 error 4 in libgvfsdaemon.so[7f4e5c038000+24000]
[  289.624042] usb 1-4: new high-speed USB device number 3 using ehci-pci
[  289.757509] usb 1-4: New USB device found, idVendor=04e8, idProduct=6860
[  289.757515] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  289.757519] usb 1-4: Product: SAMSUNG_Android
[  289.757522] usb 1-4: Manufacturer: SAMSUNG
[  289.757525] usb 1-4: SerialNumber: 5a9b2cbd
[  349.964022] usb 1-4: reset high-speed USB device number 3 using ehci-pci
[  365.879065] usb 1-4: USB disconnect, device number 3
[  366.256016] usb 1-4: new high-speed USB device number 4 using ehci-pci
[  366.401505] usb 1-4: New USB device found, idVendor=04e8, idProduct=6860
[  366.401512] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  366.401516] usb 1-4: Product: SAMSUNG_Android
[  366.401519] usb 1-4: Manufacturer: SAMSUNG
[  366.401522] usb 1-4: SerialNumber: 5a9b2cbd
[  470.430660] perf interrupt took too long (2511 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[  558.172261] usb 1-4: USB disconnect, device number 4
[  664.824038] usb 1-4: new high-speed USB device number 5 using ehci-pci
[  664.957857] usb 1-4: New USB device found, idVendor=04e8, idProduct=6860
[  664.957862] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  664.957866] usb 1-4: Product: SAMSUNG_Android
[  664.957869] usb 1-4: Manufacturer: SAMSUNG
[  664.957871] usb 1-4: SerialNumber: 5a9b2cbd
[  725.152082] usb 1-4: reset high-speed USB device number 5 using ehci-pci

```

and lspci from 16.04 : 

```

00:00.0 Host bridge: Intel Corporation 82Q35 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82Q35 Express PCI Express Root Port (rev 02)
00:02.0 Display controller: Intel Corporation 82Q35 Express Integrated Graphics Controller (rev 02)
00:03.0 Communication controller: Intel Corporation 82Q35 Express MEI Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DM-2 Gigabit Network Connection (rev 02)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IO (ICH9DO) LPC Interface Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 6 port SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Caicos [Radeon HD 6450/7450/8450 / R5 230 OEM]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Caicos HDMI Audio [Radeon HD 6400 Series]
04:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6101/6102 single-port PATA133 interface (rev b2)
07:03.0 FireWire (IEEE 1394): LSI Corporation FW322/323 [TrueFire] 1394a Controller (rev 70)

```

what is wrong.

Both ubuntu (16.04 and 14.04.3) are fresh now.



Regards
Pawel

its no problem with Intel HD driver - but with ubuntu but IMO with ubuntu - if I change 1st graphics Card to Intel HD in BIOS the monitor with Intel HD works, but the 2 other monitors (with ATI) dosnt.

[[img]http://obrazki.elektroda.pl/3174947300_1452941017_thumb.jpg[/img]](http://obrazki.elektroda.pl/3174947300_1452941017.png) 

dmesg after change bios (1st card as builtin (intel HD))

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 4.3.0-5-generic (buildd@lgw01-10) (gcc version 5.3.1 20151216 (Ubuntu 5.3.1-3ubuntu3) ) #16-Ubuntu SMP Wed Dec 16 23:33:25 UTC 2015 (Ubuntu 4.3.0-5.16-generic 4.3.3)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.3.0-5-generic root=UUID=62f8a354-b923-4733-9a28-976899d688e1 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] x86/fpu: Legacy x87 FPU detected.
[    0.000000] x86/fpu: Using 'lazy' FPU context switches.
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009dbff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009dc00-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000bee1efff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bee1f000-0x00000000bee20fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bee21000-0x00000000beedcfff] usable
[    0.000000] BIOS-e820: [mem 0x00000000beedd000-0x00000000befe2fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000befe3000-0x00000000befe5fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000befe6000-0x00000000beff1fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000beff2000-0x00000000beff2fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000beff3000-0x00000000beffefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000befff000-0x00000000beffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bf000000-0x00000000bfffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f0000000-0x00000000f7ffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffc00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000023bffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.4 present.
[    0.000000] DMI:                  /DQ35JO, BIOS JOQ3510J.86A.0882.2008.0423.1925 04/23/2008
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x23c000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 0BF000000 mask FFF000000 uncachable
[    0.000000]   3 base 100000000 mask F00000000 write-back
[    0.000000]   4 base 200000000 mask F80000000 write-back
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- WT  
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3056MB, range: 16MB, type UC
[    0.000000] reg 3, base: 4GB, range: 4GB, type WB
[    0.000000] reg 4, base: 8GB, range: 2GB, type WB
[    0.000000] total RAM covered: 9200M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 32M 	num_reg: 5  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3056MB, range: 16MB, type UC
[    0.000000] reg 3, base: 4GB, range: 4GB, type WB
[    0.000000] reg 4, base: 8GB, range: 2GB, type WB
[    0.000000] e820: update [mem 0xbf000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xbf000 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fe5e0-0x000fe5ef] mapped at [ffff8800000fe5e0]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x021f6000, 0x021f6fff] PGTABLE
[    0.000000] BRK [0x021f7000, 0x021f7fff] PGTABLE
[    0.000000] BRK [0x021f8000, 0x021f8fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x23be00000-0x23bffffff]
[    0.000000]  [mem 0x23be00000-0x23bffffff] page 2M
[    0.000000] BRK [0x021f9000, 0x021f9fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x220000000-0x23bdfffff]
[    0.000000]  [mem 0x220000000-0x23bdfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x200000000-0x21fffffff]
[    0.000000]  [mem 0x200000000-0x21fffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0xbee1efff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0xbedfffff] page 2M
[    0.000000]  [mem 0xbee00000-0xbee1efff] page 4k
[    0.000000] init_memory_mapping: [mem 0xbee21000-0xbeedcfff]
[    0.000000]  [mem 0xbee21000-0xbeedcfff] page 4k
[    0.000000] init_memory_mapping: [mem 0xbefe3000-0xbefe5fff]
[    0.000000]  [mem 0xbefe3000-0xbefe5fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xbeff2000-0xbeff2fff]
[    0.000000]  [mem 0xbeff2000-0xbeff2fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xbefff000-0xbeffffff]
[    0.000000]  [mem 0xbefff000-0xbeffffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x1ffffffff]
[    0.000000]  [mem 0x100000000-0x1ffffffff] page 2M
[    0.000000] BRK [0x021fa000, 0x021fafff] PGTABLE
[    0.000000] BRK [0x021fb000, 0x021fbfff] PGTABLE
[    0.000000] RAMDISK: [mem 0x33dc4000-0x35ed9fff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000000FE020 000014 (v00 INTEL )
[    0.000000] ACPI: RSDT 0x00000000BEFFD038 000070 (v01 INTEL  DQ3510J  00000372      01000013)
[    0.000000] ACPI: FACP 0x00000000BEFFC000 000074 (v01 INTEL  DQ3510J  00000372 MSFT 01000013)
[    0.000000] ACPI: DSDT 0x00000000BEFF8000 003D3A (v01 INTEL  DQ3510J  00000372 MSFT 01000013)
[    0.000000] ACPI: FACS 0x00000000BEF82000 000040
[    0.000000] ACPI: APIC 0x00000000BEFF7000 000078 (v01 INTEL  DQ3510J  00000372 MSFT 01000013)
[    0.000000] ACPI: WDDT 0x00000000BEFF6000 000040 (v01 INTEL  DQ3510J  00000372 MSFT 01000013)
[    0.000000] ACPI: MCFG 0x00000000BEFF5000 00003C (v01 INTEL  DQ3510J  00000372 MSFT 01000013)
[    0.000000] ACPI: ASF! 0x00000000BEFF4000 0000A6 (v32 INTEL  DQ3510J  00000372 MSFT 01000013)
[    0.000000] ACPI: HPET 0x00000000BEFF3000 000038 (v01 INTEL  DQ3510J  00000372 MSFT 01000013)
[    0.000000] ACPI: DMAR 0x00000000BEFF1000 000120 (v01 INTEL  DQ3510J  00000372 MSFT 01000013)
[    0.000000] ACPI: ASPT 0x00000000BEFF0000 00002C (v01 INTEL  DQ3510J  00000372 MSFT 01000013)
[    0.000000] ACPI: WDTT 0x00000000BEFEF000 0002CC (v01 INTEL  DQ3510J  00000372 MSFT 01000013)
[    0.000000] ACPI: SSDT 0x00000000BEFEE000 000204 (v01 INTEL  CpuPm    00000372 MSFT 01000013)
[    0.000000] ACPI: SSDT 0x00000000BEFED000 0001F9 (v01 INTEL  Cpu0Ist  00000372 MSFT 01000013)
[    0.000000] ACPI: SSDT 0x00000000BEFEC000 0001F9 (v01 INTEL  Cpu1Ist  00000372 MSFT 01000013)
[    0.000000] ACPI: SSDT 0x00000000BEFEB000 0001F9 (v01 INTEL  Cpu2Ist  00000372 MSFT 01000013)
[    0.000000] ACPI: SSDT 0x00000000BEFEA000 0001F9 (v01 INTEL  Cpu3Ist  00000372 MSFT 01000013)
[    0.000000] ACPI: SSDT 0x00000000BEFE9000 0000DD (v01 INTEL  Cpu0Cst  00000372 MSFT 01000013)
[    0.000000] ACPI: SSDT 0x00000000BEFE8000 0000DD (v01 INTEL  Cpu1Cst  00000372 MSFT 01000013)
[    0.000000] ACPI: SSDT 0x00000000BEFE7000 0000DD (v01 INTEL  Cpu2Cst  00000372 MSFT 01000013)
[    0.000000] ACPI: SSDT 0x00000000BEFE6000 0000DD (v01 INTEL  Cpu3Cst  00000372 MSFT 01000013)
[    0.000000] ACPI: TCPA 0x00000000BEEDE000 000032 (v02 INTEL  TIANO    00000002 MSFT 01000013)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000023bffffff]
[    0.000000] NODE_DATA(0) allocated [mem 0x23bff6000-0x23bffafff]
[    0.000000]  [ffffea0000000000-ffffea0008ffffff] PMD -> [ffff880233600000-ffff88023b5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.000000]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
[    0.000000]   Normal   [mem 0x0000000100000000-0x000000023bffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x0000000000001000-0x000000000009cfff]
[    0.000000]   node   0: [mem 0x0000000000100000-0x00000000bee1efff]
[    0.000000]   node   0: [mem 0x00000000bee21000-0x00000000beedcfff]
[    0.000000]   node   0: [mem 0x00000000befe3000-0x00000000befe5fff]
[    0.000000]   node   0: [mem 0x00000000beff2000-0x00000000beff2fff]
[    0.000000]   node   0: [mem 0x00000000befff000-0x00000000beffffff]
[    0.000000]   node   0: [mem 0x0000000100000000-0x000000023bffffff]
[    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x000000023bffffff]
[    0.000000] On node 0 totalpages: 2076284
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3996 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 12156 pages used for memmap
[    0.000000]   DMA32 zone: 777952 pages, LIFO batch:31
[    0.000000]   Normal zone: 20224 pages used for memmap
[    0.000000]   Normal zone: 1294336 pages, LIFO batch:31
[    0.000000] Reserving Intel graphics stolen memory at 0xbf800000-0xbfffffff
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
[    0.000000] smpboot: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009dfff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xbee1f000-0xbee20fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbeedd000-0xbefe2fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbefe6000-0xbeff1fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbeff3000-0xbeffefff]
[    0.000000] PM: Registered nosave memory: [mem 0xbf000000-0xbfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xc0000000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xf7ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xffbfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xffc00000-0xffffffff]
[    0.000000] e820: [mem 0xc0000000-0xefffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 33 pages/cpu @ffff88023bc00000 s97304 r8192 d29672 u524288
[    0.000000] pcpu-alloc: s97304 r8192 d29672 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 2043819
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.3.0-5-generic root=UUID=62f8a354-b923-4733-9a28-976899d688e1 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 8054816K/8305136K available (8194K kernel code, 1251K rwdata, 3852K rodata, 1464K init, 1300K bss, 250320K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	Build-time adjustment of leaf fanout to 64.
[    0.000000] 	RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=64, nr_cpu_ids=4
[    0.000000] NR_IRQS:16640 nr_irqs:456 16
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 133484882848 ns
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 2387.990 MHz processor
[    0.004012] Calibrating delay loop (skipped), value calculated using timer frequency.. 4775.98 BogoMIPS (lpj=9551960)
[    0.004015] pid_max: default: 32768 minimum: 301
[    0.004024] ACPI: Core revision 20150818
[    0.012340] ACPI: 10 ACPI AML tables successfully acquired and loaded
[    0.012367] Security Framework initialized
[    0.012371] Yama: becoming mindful.
[    0.012389] AppArmor: AppArmor initialized
[    0.013073] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.017185] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.019198] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.019212] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.019618] Initializing cgroup subsys io
[    0.019627] Initializing cgroup subsys memory
[    0.019639] Initializing cgroup subsys devices
[    0.019642] Initializing cgroup subsys freezer
[    0.019646] Initializing cgroup subsys net_cls
[    0.019649] Initializing cgroup subsys perf_event
[    0.019652] Initializing cgroup subsys net_prio
[    0.019656] Initializing cgroup subsys hugetlb
[    0.019662] Initializing cgroup subsys pids
[    0.019688] CPU: Physical Processor ID: 0
[    0.019690] CPU: Processor Core ID: 0
[    0.019692] mce: CPU supports 6 MCE banks
[    0.019702] CPU0: Thermal monitoring enabled (TM2)
[    0.019706] process: using mwait in idle threads
[    0.019711] Last level iTLB entries: 4KB 128, 2MB 4, 4MB 4
[    0.019713] Last level dTLB entries: 4KB 256, 2MB 0, 4MB 32, 1GB 0
[    0.020080] Freeing SMP alternatives memory: 28K (ffffffff820a8000 - ffffffff820af000)
[    0.023431] ftrace: allocating 31344 entries in 123 pages
[    0.032107] DMAR: Host address width 36
[    0.032110] DMAR: DRHD base: 0x000000feb00000 flags: 0x0
[    0.032118] DMAR: dmar0: reg_base_addr feb00000 ver 1:0 cap c9008020a30270 ecap 1000
[    0.032120] DMAR: DRHD base: 0x000000feb01000 flags: 0x0
[    0.032126] DMAR: dmar1: reg_base_addr feb01000 ver 1:0 cap c0000020230270 ecap 1000
[    0.032128] DMAR: DRHD base: 0x000000feb02000 flags: 0x0
[    0.032134] DMAR: dmar2: reg_base_addr feb02000 ver 1:0 cap c0000020230270 ecap 1000
[    0.032136] DMAR: DRHD base: 0x000000feb03000 flags: 0x1
[    0.032141] DMAR: dmar3: reg_base_addr feb03000 ver 1:0 cap c9008020230270 ecap 1000
[    0.032142] DMAR: RMRR base: 0x000000000e0000 end: 0x000000000effff
[    0.032144] DMAR: RMRR base: 0x000000bf600000 end: 0x000000bfffffff
[    0.032505] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.076000] smpboot: CPU0: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz (family: 0x6, model: 0xf, stepping: 0xb)
[    0.076000] Performance Events: PEBS fmt0+, 4-deep LBR, Core2 events, Intel PMU driver.
[    0.076000] perf_event_intel: PEBS disabled due to CPU errata
[    0.076000] ... version:                2
[    0.076000] ... bit width:              40
[    0.076000] ... generic registers:      2
[    0.076000] ... value mask:             000000ffffffffff
[    0.076000] ... max period:             000000007fffffff
[    0.076000] ... fixed-purpose events:   3
[    0.076000] ... event mask:             0000000700000003
[    0.076000] x86: Booting SMP configuration:
[    0.076000] .... node  #0, CPUs:      #1
[    0.086199] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.086304]  #2 #3
[    0.112022] x86: Booted up 1 node, 4 CPUs
[    0.112026] smpboot: Total of 4 processors activated (19103.92 BogoMIPS)
[    0.116015] devtmpfs: initialized
[    0.120115] evm: security.selinux
[    0.120117] evm: security.SMACK64
[    0.120119] evm: security.SMACK64EXEC
[    0.120120] evm: security.SMACK64TRANSMUTE
[    0.120121] evm: security.SMACK64MMAP
[    0.120122] evm: security.ima
[    0.120124] evm: security.capability
[    0.120145] PM: Registering ACPI NVS region [mem 0xbeedd000-0xbefe2fff] (1073152 bytes)
[    0.120192] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    0.120245] pinctrl core: initialized pinctrl subsystem
[    0.120245] RTC time: 11:35:40, date: 01/16/16
[    0.120338] NET: Registered protocol family 16
[    0.132008] cpuidle: using governor ladder
[    0.144006] cpuidle: using governor menu
[    0.144012] PCCT header not found.
[    0.144107] ACPI: bus type PCI registered
[    0.144111] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.144233] PCI: MMCONFIG for domain 0000 [bus 00-7f] at [mem 0xf0000000-0xf7ffffff] (base 0xf0000000)
[    0.144237] PCI: MMCONFIG at [mem 0xf0000000-0xf7ffffff] reserved in E820
[    0.144245] PCI: Using configuration type 1 for base access
[    0.156159] ACPI: Added _OSI(Module Device)
[    0.156161] ACPI: Added _OSI(Processor Device)
[    0.156167] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.156168] ACPI: Added _OSI(Processor Aggregator Device)
[    0.158834] ACPI: Interpreter enabled
[    0.158843] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20150818/hwxface-580)
[    0.158857] ACPI: (supports S0 S1 S3 S4 S5)
[    0.158859] ACPI: Using IOAPIC for interrupt routing
[    0.158884] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.164470] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.164476] acpi PNP0A03:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.164484] acpi PNP0A03:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[    0.165023] acpi PNP0A03:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-7f] only partially covers this bridge
[    0.165209] PCI host bridge to bus 0000:00
[    0.165213] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.165216] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
[    0.165221] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
[    0.165224] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
[    0.165226] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000effff window]
[    0.165228] pci_bus 0000:00: root bus resource [mem 0xf8000000-0xfeafffff window]
[    0.165230] pci_bus 0000:00: root bus resource [mem 0xc0000000-0xefffffff window]
[    0.165239] pci 0000:00:00.0: [8086:29b0] type 00 class 0x060000
[    0.165350] pci 0000:00:01.0: [8086:29b1] type 01 class 0x060400
[    0.165387] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.165435] pci 0000:00:01.0: System wakeup disabled by ACPI
[    0.165482] pci 0000:00:02.0: [8086:29b2] type 00 class 0x030000
[    0.165496] pci 0000:00:02.0: reg 0x10: [mem 0xe0400000-0xe047ffff]
[    0.165502] pci 0000:00:02.0: reg 0x14: [io  0x3430-0x3437]
[    0.165508] pci 0000:00:02.0: reg 0x18: [mem 0xd0000000-0xdfffffff pref]
[    0.165513] pci 0000:00:02.0: reg 0x1c: [mem 0xe0200000-0xe02fffff]
[    0.165612] pci 0000:00:03.0: [8086:29b4] type 00 class 0x078000
[    0.165629] pci 0000:00:03.0: reg 0x10: [mem 0xe04a6100-0xe04a610f 64bit]
[    0.165660] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    0.165767] pci 0000:00:19.0: [8086:10bd] type 00 class 0x020000
[    0.165791] pci 0000:00:19.0: reg 0x10: [mem 0xe0480000-0xe049ffff]
[    0.165800] pci 0000:00:19.0: reg 0x14: [mem 0xe04a4000-0xe04a4fff]
[    0.165808] pci 0000:00:19.0: reg 0x18: [io  0x3400-0x341f]
[    0.165850] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.165896] pci 0000:00:19.0: System wakeup disabled by ACPI
[    0.165945] pci 0000:00:1a.0: [8086:2937] type 00 class 0x0c0300
[    0.165989] pci 0000:00:1a.0: reg 0x20: [io  0x30e0-0x30ff]
[    0.166076] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.166126] pci 0000:00:1a.1: [8086:2938] type 00 class 0x0c0300
[    0.166170] pci 0000:00:1a.1: reg 0x20: [io  0x30c0-0x30df]
[    0.166255] pci 0000:00:1a.1: System wakeup disabled by ACPI
[    0.166306] pci 0000:00:1a.2: [8086:2939] type 00 class 0x0c0300
[    0.166361] pci 0000:00:1a.2: reg 0x20: [io  0x30a0-0x30bf]
[    0.166445] pci 0000:00:1a.2: System wakeup disabled by ACPI
[    0.166501] pci 0000:00:1a.7: [8086:293c] type 00 class 0x0c0320
[    0.166528] pci 0000:00:1a.7: reg 0x10: [mem 0xe04a5c00-0xe04a5fff]
[    0.166593] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.166658] pci 0000:00:1a.7: System wakeup disabled by ACPI
[    0.166712] pci 0000:00:1b.0: [8086:293e] type 00 class 0x040300
[    0.166737] pci 0000:00:1b.0: reg 0x10: [mem 0xe04a0000-0xe04a3fff 64bit]
[    0.166791] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.166857] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.166907] pci 0000:00:1c.0: [8086:2940] type 01 class 0x060400
[    0.166963] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.167011] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.167061] pci 0000:00:1c.1: [8086:2942] type 01 class 0x060400
[    0.167116] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.167166] pci 0000:00:1c.1: System wakeup disabled by ACPI
[    0.167219] pci 0000:00:1c.2: [8086:2944] type 01 class 0x060400
[    0.167279] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.167328] pci 0000:00:1c.2: System wakeup disabled by ACPI
[    0.167378] pci 0000:00:1c.3: [8086:2946] type 01 class 0x060400
[    0.167433] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.167481] pci 0000:00:1c.3: System wakeup disabled by ACPI
[    0.167531] pci 0000:00:1c.4: [8086:2948] type 01 class 0x060400
[    0.167587] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.167635] pci 0000:00:1c.4: System wakeup disabled by ACPI
[    0.167690] pci 0000:00:1d.0: [8086:2934] type 00 class 0x0c0300
[    0.167734] pci 0000:00:1d.0: reg 0x20: [io  0x3080-0x309f]
[    0.167819] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.167870] pci 0000:00:1d.1: [8086:2935] type 00 class 0x0c0300
[    0.167915] pci 0000:00:1d.1: reg 0x20: [io  0x3060-0x307f]
[    0.167999] pci 0000:00:1d.1: System wakeup disabled by ACPI
[    0.168053] pci 0000:00:1d.2: [8086:2936] type 00 class 0x0c0300
[    0.168097] pci 0000:00:1d.2: reg 0x20: [io  0x3040-0x305f]
[    0.168181] pci 0000:00:1d.2: System wakeup disabled by ACPI
[    0.168240] pci 0000:00:1d.7: [8086:293a] type 00 class 0x0c0320
[    0.168267] pci 0000:00:1d.7: reg 0x10: [mem 0xe04a5800-0xe04a5bff]
[    0.168332] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.168397] pci 0000:00:1d.7: System wakeup disabled by ACPI
[    0.168447] pci 0000:00:1e.0: [8086:244e] type 01 class 0x060401
[    0.168530] pci 0000:00:1e.0: System wakeup disabled by ACPI
[    0.168582] pci 0000:00:1f.0: [8086:2914] type 00 class 0x060100
[    0.168674] pci 0000:00:1f.0: can't claim BAR 13 [io  0x0400-0x047f]: address conflict with ACPI CPU throttle [io  0x0410-0x0415]
[    0.168679] pci 0000:00:1f.0: quirk: [io  0x0500-0x053f] claimed by ICH6 GPIO
[    0.168683] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0680 (mask 007f)
[    0.168783] pci 0000:00:1f.2: [8086:2922] type 00 class 0x010601
[    0.168806] pci 0000:00:1f.2: reg 0x10: [io  0x3428-0x342f]
[    0.168814] pci 0000:00:1f.2: reg 0x14: [io  0x343c-0x343f]
[    0.168821] pci 0000:00:1f.2: reg 0x18: [io  0x3420-0x3427]
[    0.168829] pci 0000:00:1f.2: reg 0x1c: [io  0x3438-0x343b]
[    0.168836] pci 0000:00:1f.2: reg 0x20: [io  0x3020-0x303f]
[    0.168844] pci 0000:00:1f.2: reg 0x24: [mem 0xe04a5000-0xe04a57ff]
[    0.168871] pci 0000:00:1f.2: PME# supported from D3hot
[    0.168963] pci 0000:00:1f.3: [8086:2930] type 00 class 0x0c0500
[    0.168980] pci 0000:00:1f.3: reg 0x10: [mem 0xe04a6000-0xe04a60ff 64bit]
[    0.168999] pci 0000:00:1f.3: reg 0x20: [io  0x3000-0x301f]
[    0.169135] pci 0000:01:00.0: [1002:6779] type 00 class 0x030000
[    0.169160] pci 0000:01:00.0: reg 0x10: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.169171] pci 0000:01:00.0: reg 0x18: [mem 0xe0300000-0xe031ffff 64bit]
[    0.169177] pci 0000:01:00.0: reg 0x20: [io  0x2000-0x20ff]
[    0.169188] pci 0000:01:00.0: reg 0x30: [mem 0xfffe0000-0xffffffff pref]
[    0.169214] pci 0000:01:00.0: supports D1 D2
[    0.169268] pci 0000:01:00.1: [1002:aa98] type 00 class 0x040300
[    0.169295] pci 0000:01:00.1: reg 0x10: [mem 0xe0320000-0xe0323fff 64bit]
[    0.169350] pci 0000:01:00.1: supports D1 D2
[    0.169417] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.169420] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    0.169423] pci 0000:00:01.0:   bridge window [mem 0xe0300000-0xe03fffff]
[    0.169427] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.169475] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.169526] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.169593] pci 0000:04:00.0: [11ab:6101] type 00 class 0x01018f
[    0.169626] pci 0000:04:00.0: reg 0x10: [io  0x1018-0x101f]
[    0.169638] pci 0000:04:00.0: reg 0x14: [io  0x1024-0x1027]
[    0.169650] pci 0000:04:00.0: reg 0x18: [io  0x1010-0x1017]
[    0.169661] pci 0000:04:00.0: reg 0x1c: [io  0x1020-0x1023]
[    0.169673] pci 0000:04:00.0: reg 0x20: [io  0x1000-0x100f]
[    0.169685] pci 0000:04:00.0: reg 0x24: [mem 0xe0100000-0xe01001ff]
[    0.169729] pci 0000:04:00.0: supports D1
[    0.169732] pci 0000:04:00.0: PME# supported from D0 D1 D3hot
[    0.169789] pci 0000:04:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.169798] pci 0000:00:1c.2: PCI bridge to [bus 04]
[    0.169802] pci 0000:00:1c.2:   bridge window [io  0x1000-0x1fff]
[    0.169806] pci 0000:00:1c.2:   bridge window [mem 0xe0100000-0xe01fffff]
[    0.169856] pci 0000:00:1c.3: PCI bridge to [bus 05]
[    0.169909] pci 0000:00:1c.4: PCI bridge to [bus 06]
[    0.169963] pci 0000:07:03.0: [11c1:5811] type 00 class 0x0c0010
[    0.169985] pci 0000:07:03.0: reg 0x10: [mem 0xe0000000-0xe0000fff]
[    0.170047] pci 0000:07:03.0: supports D1 D2
[    0.170049] pci 0000:07:03.0: PME# supported from D0 D1 D2 D3hot
[    0.170130] pci 0000:00:1e.0: PCI bridge to [bus 07] (subtractive decode)
[    0.170136] pci 0000:00:1e.0:   bridge window [mem 0xe0000000-0xe00fffff]
[    0.170141] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7 window] (subtractive decode)
[    0.170144] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff window] (subtractive decode)
[    0.170146] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff window] (subtractive decode)
[    0.170149] pci 0000:00:1e.0:   bridge window [mem 0x000e0000-0x000effff window] (subtractive decode)
[    0.170151] pci 0000:00:1e.0:   bridge window [mem 0xf8000000-0xfeafffff window] (subtractive decode)
[    0.170154] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xefffffff window] (subtractive decode)
[    0.170254] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    0.170321] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *9 10 11 12)
[    0.170385] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[    0.170449] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[    0.170515] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 *10 11 12)
[    0.170579] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 *9 10 11 12)
[    0.170642] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 *10 11 12)
[    0.170704] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 *11 12)
[    0.171228] ACPI: Enabled 4 GPEs in block 00 to 3F
[    0.171335] vgaarb: setting as boot device: PCI:0000:00:02.0
[    0.171335] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.171335] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=none,locks=none
[    0.171335] vgaarb: loaded
[    0.171335] vgaarb: bridge control possible 0000:01:00.0
[    0.171335] vgaarb: no bridge control possible 0000:00:02.0
[    0.171335] SCSI subsystem initialized
[    0.171335] libata version 3.00 loaded.
[    0.171335] ACPI: bus type USB registered
[    0.171335] usbcore: registered new interface driver usbfs
[    0.171335] usbcore: registered new interface driver hub
[    0.171335] usbcore: registered new device driver usb
[    0.172063] PCI: Using ACPI for IRQ routing
[    0.174683] PCI: pci_cache_line_size set to 64 bytes
[    0.174742] e820: reserve RAM buffer [mem 0x0009dc00-0x0009ffff]
[    0.174744] e820: reserve RAM buffer [mem 0xbee1f000-0xbfffffff]
[    0.174746] e820: reserve RAM buffer [mem 0xbeedd000-0xbfffffff]
[    0.174748] e820: reserve RAM buffer [mem 0xbefe6000-0xbfffffff]
[    0.174750] e820: reserve RAM buffer [mem 0xbeff3000-0xbfffffff]
[    0.174752] e820: reserve RAM buffer [mem 0xbf000000-0xbfffffff]
[    0.174892] NetLabel: Initializing
[    0.174894] NetLabel:  domain hash size = 128
[    0.174895] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.174914] NetLabel:  unlabeled traffic allowed by default
[    0.174947] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.174947] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.174947] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.177014] clocksource: Switched to clocksource hpet
[    0.185140] AppArmor: AppArmor Filesystem Enabled
[    0.185237] pnp: PnP ACPI init
[    0.185362] system 00:00: [mem 0xf0000000-0xf7ffffff] has been reserved
[    0.185366] system 00:00: [mem 0xfeb00000-0xfeb03fff] could not be reserved
[    0.185369] system 00:00: [mem 0xfed13000-0xfed13fff] has been reserved
[    0.185371] system 00:00: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.185374] system 00:00: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.185376] system 00:00: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.185379] system 00:00: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.185381] system 00:00: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.185383] system 00:00: [mem 0xfed45000-0xfed99fff] has been reserved
[    0.185386] system 00:00: [mem 0x000c0000-0x000dffff] could not be reserved
[    0.185389] system 00:00: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.185391] system 00:00: [mem 0xffc00000-0xffffffff] has been reserved
[    0.185396] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.185561] pnp 00:01: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.185624] system 00:02: [io  0x0500-0x053f] has been reserved
[    0.185627] system 00:02: [io  0x0400-0x047f] could not be reserved
[    0.185630] system 00:02: [io  0x0680-0x06ff] has been reserved
[    0.185634] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.185689] pnp 00:03: Plug and Play ACPI device, IDs WEC1000 PNP0c31 (active)
[    0.185758] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.186090] pnp 00:05: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.186169] pnp: PnP ACPI: found 6 devices
[    0.194472] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    0.194480] pci 0000:01:00.0: can't claim BAR 6 [mem 0xfffe0000-0xffffffff pref]: no compatible bridge window
[    0.194497] pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 02] add_size 1000
[    0.194501] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 02] add_size 200000 add_align 100000
[    0.194504] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff] to [bus 02] add_size 200000 add_align 100000
[    0.194512] pci 0000:00:1c.1: bridge window [io  0x1000-0x0fff] to [bus 03] add_size 1000
[    0.194515] pci 0000:00:1c.1: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 03] add_size 200000 add_align 100000
[    0.194518] pci 0000:00:1c.1: bridge window [mem 0x00100000-0x000fffff] to [bus 03] add_size 200000 add_align 100000
[    0.194526] pci 0000:00:1c.2: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 04] add_size 200000 add_align 100000
[    0.194534] pci 0000:00:1c.3: bridge window [io  0x1000-0x0fff] to [bus 05] add_size 1000
[    0.194537] pci 0000:00:1c.3: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 05] add_size 200000 add_align 100000
[    0.194540] pci 0000:00:1c.3: bridge window [mem 0x00100000-0x000fffff] to [bus 05] add_size 200000 add_align 100000
[    0.194548] pci 0000:00:1c.4: bridge window [io  0x1000-0x0fff] to [bus 06] add_size 1000
[    0.194551] pci 0000:00:1c.4: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 06] add_size 200000 add_align 100000
[    0.194554] pci 0000:00:1c.4: bridge window [mem 0x00100000-0x000fffff] to [bus 06] add_size 200000 add_align 100000
[    0.194568] pci 0000:00:1f.0: BAR 13: [io  size 0x0080] has bogus alignment
[    0.194573] pci 0000:00:1c.0: res[14]=[mem 0x00100000-0x000fffff] res_to_dev_res add_size 200000 min_align 100000
[    0.194575] pci 0000:00:1c.0: res[14]=[mem 0x00100000-0x002fffff] res_to_dev_res add_size 200000 min_align 100000
[    0.194578] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.194581] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x002fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.194583] pci 0000:00:1c.1: res[14]=[mem 0x00100000-0x000fffff] res_to_dev_res add_size 200000 min_align 100000
[    0.194586] pci 0000:00:1c.1: res[14]=[mem 0x00100000-0x002fffff] res_to_dev_res add_size 200000 min_align 100000
[    0.194589] pci 0000:00:1c.1: res[15]=[mem 0x00100000-0x000fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.194591] pci 0000:00:1c.1: res[15]=[mem 0x00100000-0x002fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.194594] pci 0000:00:1c.2: res[15]=[mem 0x00100000-0x000fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.194597] pci 0000:00:1c.2: res[15]=[mem 0x00100000-0x002fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.194599] pci 0000:00:1c.3: res[14]=[mem 0x00100000-0x000fffff] res_to_dev_res add_size 200000 min_align 100000
[    0.194602] pci 0000:00:1c.3: res[14]=[mem 0x00100000-0x002fffff] res_to_dev_res add_size 200000 min_align 100000
[    0.194604] pci 0000:00:1c.3: res[15]=[mem 0x00100000-0x000fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.194607] pci 0000:00:1c.3: res[15]=[mem 0x00100000-0x002fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.194610] pci 0000:00:1c.4: res[14]=[mem 0x00100000-0x000fffff] res_to_dev_res add_size 200000 min_align 100000
[    0.194612] pci 0000:00:1c.4: res[14]=[mem 0x00100000-0x002fffff] res_to_dev_res add_size 200000 min_align 100000
[    0.194615] pci 0000:00:1c.4: res[15]=[mem 0x00100000-0x000fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.194618] pci 0000:00:1c.4: res[15]=[mem 0x00100000-0x002fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.194620] pci 0000:00:1c.0: res[13]=[io  0x1000-0x0fff] res_to_dev_res add_size 1000 min_align 1000
[    0.194623] pci 0000:00:1c.0: res[13]=[io  0x1000-0x1fff] res_to_dev_res add_size 1000 min_align 1000
[    0.194625] pci 0000:00:1c.1: res[13]=[io  0x1000-0x0fff] res_to_dev_res add_size 1000 min_align 1000
[    0.194628] pci 0000:00:1c.1: res[13]=[io  0x1000-0x1fff] res_to_dev_res add_size 1000 min_align 1000
[    0.194630] pci 0000:00:1c.3: res[13]=[io  0x1000-0x0fff] res_to_dev_res add_size 1000 min_align 1000
[    0.194633] pci 0000:00:1c.3: res[13]=[io  0x1000-0x1fff] res_to_dev_res add_size 1000 min_align 1000
[    0.194635] pci 0000:00:1c.4: res[13]=[io  0x1000-0x0fff] res_to_dev_res add_size 1000 min_align 1000
[    0.194637] pci 0000:00:1c.4: res[13]=[io  0x1000-0x1fff] res_to_dev_res add_size 1000 min_align 1000
[    0.194644] pci 0000:00:1c.0: BAR 14: assigned [mem 0xf8000000-0xf81fffff]
[    0.194649] pci 0000:00:1c.0: BAR 15: assigned [mem 0xf8200000-0xf83fffff 64bit pref]
[    0.194652] pci 0000:00:1c.1: BAR 14: assigned [mem 0xf8400000-0xf85fffff]
[    0.194656] pci 0000:00:1c.1: BAR 15: assigned [mem 0xf8600000-0xf87fffff 64bit pref]
[    0.194661] pci 0000:00:1c.2: BAR 15: assigned [mem 0xf8800000-0xf89fffff 64bit pref]
[    0.194664] pci 0000:00:1c.3: BAR 14: assigned [mem 0xf8a00000-0xf8bfffff]
[    0.194668] pci 0000:00:1c.3: BAR 15: assigned [mem 0xf8c00000-0xf8dfffff 64bit pref]
[    0.194671] pci 0000:00:1c.4: BAR 14: assigned [mem 0xf8e00000-0xf8ffffff]
[    0.194676] pci 0000:00:1c.4: BAR 15: assigned [mem 0xf9000000-0xf91fffff 64bit pref]
[    0.194679] pci 0000:00:1c.0: BAR 13: assigned [io  0x4000-0x4fff]
[    0.194682] pci 0000:00:1c.1: BAR 13: assigned [io  0x5000-0x5fff]
[    0.194685] pci 0000:00:1c.3: BAR 13: assigned [io  0x6000-0x6fff]
[    0.194688] pci 0000:00:1c.4: BAR 13: assigned [io  0x7000-0x7fff]
[    0.194694] pci 0000:01:00.0: BAR 6: assigned [mem 0xe0340000-0xe035ffff pref]
[    0.194696] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.194699] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    0.194703] pci 0000:00:01.0:   bridge window [mem 0xe0300000-0xe03fffff]
[    0.194706] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.194710] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.194713] pci 0000:00:1c.0:   bridge window [io  0x4000-0x4fff]
[    0.194718] pci 0000:00:1c.0:   bridge window [mem 0xf8000000-0xf81fffff]
[    0.194722] pci 0000:00:1c.0:   bridge window [mem 0xf8200000-0xf83fffff 64bit pref]
[    0.194727] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.194730] pci 0000:00:1c.1:   bridge window [io  0x5000-0x5fff]
[    0.194735] pci 0000:00:1c.1:   bridge window [mem 0xf8400000-0xf85fffff]
[    0.194738] pci 0000:00:1c.1:   bridge window [mem 0xf8600000-0xf87fffff 64bit pref]
[    0.194744] pci 0000:00:1c.2: PCI bridge to [bus 04]
[    0.194747] pci 0000:00:1c.2:   bridge window [io  0x1000-0x1fff]
[    0.194751] pci 0000:00:1c.2:   bridge window [mem 0xe0100000-0xe01fffff]
[    0.194755] pci 0000:00:1c.2:   bridge window [mem 0xf8800000-0xf89fffff 64bit pref]
[    0.194760] pci 0000:00:1c.3: PCI bridge to [bus 05]
[    0.194763] pci 0000:00:1c.3:   bridge window [io  0x6000-0x6fff]
[    0.194768] pci 0000:00:1c.3:   bridge window [mem 0xf8a00000-0xf8bfffff]
[    0.194772] pci 0000:00:1c.3:   bridge window [mem 0xf8c00000-0xf8dfffff 64bit pref]
[    0.194777] pci 0000:00:1c.4: PCI bridge to [bus 06]
[    0.194780] pci 0000:00:1c.4:   bridge window [io  0x7000-0x7fff]
[    0.194784] pci 0000:00:1c.4:   bridge window [mem 0xf8e00000-0xf8ffffff]
[    0.194788] pci 0000:00:1c.4:   bridge window [mem 0xf9000000-0xf91fffff 64bit pref]
[    0.194794] pci 0000:00:1e.0: PCI bridge to [bus 07]
[    0.194798] pci 0000:00:1e.0:   bridge window [mem 0xe0000000-0xe00fffff]
[    0.194806] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7 window]
[    0.194808] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff window]
[    0.194811] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.194813] pci_bus 0000:00: resource 7 [mem 0x000e0000-0x000effff window]
[    0.194815] pci_bus 0000:00: resource 8 [mem 0xf8000000-0xfeafffff window]
[    0.194817] pci_bus 0000:00: resource 9 [mem 0xc0000000-0xefffffff window]
[    0.194820] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
[    0.194822] pci_bus 0000:01: resource 1 [mem 0xe0300000-0xe03fffff]
[    0.194824] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.194826] pci_bus 0000:02: resource 0 [io  0x4000-0x4fff]
[    0.194829] pci_bus 0000:02: resource 1 [mem 0xf8000000-0xf81fffff]
[    0.194831] pci_bus 0000:02: resource 2 [mem 0xf8200000-0xf83fffff 64bit pref]
[    0.194833] pci_bus 0000:03: resource 0 [io  0x5000-0x5fff]
[    0.194835] pci_bus 0000:03: resource 1 [mem 0xf8400000-0xf85fffff]
[    0.194837] pci_bus 0000:03: resource 2 [mem 0xf8600000-0xf87fffff 64bit pref]
[    0.194840] pci_bus 0000:04: resource 0 [io  0x1000-0x1fff]
[    0.194842] pci_bus 0000:04: resource 1 [mem 0xe0100000-0xe01fffff]
[    0.194844] pci_bus 0000:04: resource 2 [mem 0xf8800000-0xf89fffff 64bit pref]
[    0.194846] pci_bus 0000:05: resource 0 [io  0x6000-0x6fff]
[    0.194849] pci_bus 0000:05: resource 1 [mem 0xf8a00000-0xf8bfffff]
[    0.194851] pci_bus 0000:05: resource 2 [mem 0xf8c00000-0xf8dfffff 64bit pref]
[    0.194853] pci_bus 0000:06: resource 0 [io  0x7000-0x7fff]
[    0.194855] pci_bus 0000:06: resource 1 [mem 0xf8e00000-0xf8ffffff]
[    0.194857] pci_bus 0000:06: resource 2 [mem 0xf9000000-0xf91fffff 64bit pref]
[    0.194860] pci_bus 0000:07: resource 1 [mem 0xe0000000-0xe00fffff]
[    0.194862] pci_bus 0000:07: resource 4 [io  0x0000-0x0cf7 window]
[    0.194864] pci_bus 0000:07: resource 5 [io  0x0d00-0xffff window]
[    0.194866] pci_bus 0000:07: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.194869] pci_bus 0000:07: resource 7 [mem 0x000e0000-0x000effff window]
[    0.194871] pci_bus 0000:07: resource 8 [mem 0xf8000000-0xfeafffff window]
[    0.194873] pci_bus 0000:07: resource 9 [mem 0xc0000000-0xefffffff window]
[    0.194912] NET: Registered protocol family 2
[    0.195178] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
[    0.195430] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.195755] TCP: Hash tables configured (established 65536 bind 65536)
[    0.195811] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.195866] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.195984] NET: Registered protocol family 1
[    0.196024] pci 0000:00:02.0: Video device with shadowed ROM
[    0.196424] PCI: CLS 64 bytes, default 64
[    0.196496] Trying to unpack rootfs image as initramfs...
[    0.806840] Freeing initrd memory: 33880K (ffff880033dc4000 - ffff880035eda000)
[    0.806939] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.806942] software IO TLB [mem 0xbae1f000-0xbee1f000] (64MB) mapped at [ffff8800bae1f000-ffff8800bee1efff]
[    0.807146] microcode: CPU0 sig=0x6fb, pf=0x10, revision=0xb6
[    0.807160] microcode: CPU1 sig=0x6fb, pf=0x10, revision=0xb6
[    0.807174] microcode: CPU2 sig=0x6fb, pf=0x10, revision=0xb6
[    0.807188] microcode: CPU3 sig=0x6fb, pf=0x10, revision=0xb6
[    0.807279] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.807363] Scanning for low memory corruption every 60 seconds
[    0.807705] futex hash table entries: 1024 (order: 4, 65536 bytes)
[    0.807742] audit: initializing netlink subsys (disabled)
[    0.807766] audit: type=2000 audit(1452944140.804:1): initialized
[    0.808091] Initialise system trusted keyring
[    0.808247] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.810614] zbud: loaded
[    0.810915] VFS: Disk quotas dquot_6.6.0
[    0.810985] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.811690] fuse init (API version 7.23)
[    0.811939] Key type big_key registered
[    0.812572] Key type asymmetric registered
[    0.812577] Asymmetric key parser 'x509' registered
[    0.812600] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 249)
[    0.812664] io scheduler noop registered
[    0.812669] io scheduler deadline registered (default)
[    0.812735] io scheduler cfq registered
[    0.813405] pcieport 0000:00:1c.0: enabling device (0000 -> 0003)
[    0.813699] pcieport 0000:00:1c.1: enabling device (0000 -> 0003)
[    0.814275] pcieport 0000:00:1c.3: enabling device (0000 -> 0003)
[    0.814563] pcieport 0000:00:1c.4: enabling device (0000 -> 0003)
[    0.814766] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.814775] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.814817] vesafb: mode is 1280x1024x32, linelength=5120, pages=0
[    0.814818] vesafb: scrolling: redraw
[    0.814820] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.814836] vesafb: framebuffer at 0xd0000000, mapped to 0xffffc90001000000, using 5120k, total 5120k
[    0.814955] Console: switching to colour frame buffer device 160x64
[    0.814989] fb0: VESA VGA frame buffer device
[    0.815008] intel_idle: does not run on family 6 model 15
[    0.815094] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
[    0.815099] ACPI: Sleep Button [SLPB]
[    0.815157] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.815160] ACPI: Power Button [PWRF]
[    0.815247] Monitor-Mwait will be used to enter C-1 state
[    0.815960] GHES: HEST is not enabled!
[    0.816086] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.836447] 00:05: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    0.838227] Linux agpgart interface v0.103
[    0.838318] agpgart-intel 0000:00:00.0: Intel Q35 Chipset
[    0.838337] agpgart-intel 0000:00:00.0: detected gtt size: 524288K total, 262144K mappable
[    0.839496] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    0.839638] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    0.864052] tpm_tis 00:03: 1.2 TPM (device-id 0xFE, rev-id 70)
[    0.963881] brd: module loaded
[    0.965723] loop: module loaded
[    0.966238] libphy: Fixed MDIO Bus: probed
[    0.966242] tun: Universal TUN/TAP device driver, 1.6
[    0.966244] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.966292] PPP generic driver version 2.4.2
[    0.966377] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.966383] ehci-pci: EHCI PCI platform driver
[    0.966545] ehci-pci 0000:00:1a.7: EHCI Host Controller
[    0.966553] ehci-pci 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.966565] ehci-pci 0000:00:1a.7: debug port 1
[    0.970484] ehci-pci 0000:00:1a.7: cache line size of 64 is not supported
[    0.970498] ehci-pci 0000:00:1a.7: irq 17, io mem 0xe04a5c00
[    0.980045] ehci-pci 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.980110] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.980114] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.980117] usb usb1: Product: EHCI Host Controller
[    0.980121] usb usb1: Manufacturer: Linux 4.3.0-5-generic ehci_hcd
[    0.980124] usb usb1: SerialNumber: 0000:00:1a.7
[    0.980287] hub 1-0:1.0: USB hub found
[    0.980295] hub 1-0:1.0: 6 ports detected
[    0.980608] ehci-pci 0000:00:1d.7: EHCI Host Controller
[    0.980615] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.980625] ehci-pci 0000:00:1d.7: debug port 1
[    0.984521] ehci-pci 0000:00:1d.7: cache line size of 64 is not supported
[    0.984532] ehci-pci 0000:00:1d.7: irq 23, io mem 0xe04a5800
[    0.996045] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.996111] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.996115] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.996119] usb usb2: Product: EHCI Host Controller
[    0.996122] usb usb2: Manufacturer: Linux 4.3.0-5-generic ehci_hcd
[    0.996125] usb usb2: SerialNumber: 0000:00:1d.7
[    0.996272] hub 2-0:1.0: USB hub found
[    0.996281] hub 2-0:1.0: 6 ports detected
[    0.996451] ehci-platform: EHCI generic platform driver
[    0.996463] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.996468] ohci-pci: OHCI PCI platform driver
[    0.996482] ohci-platform: OHCI generic platform driver
[    0.996493] uhci_hcd: USB Universal Host Controller Interface driver
[    0.996638] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.996644] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.996650] uhci_hcd 0000:00:1a.0: detected 2 ports
[    0.996675] uhci_hcd 0000:00:1a.0: irq 18, io base 0x000030e0
[    0.996720] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    0.996723] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.996725] usb usb3: Product: UHCI Host Controller
[    0.996727] usb usb3: Manufacturer: Linux 4.3.0-5-generic uhci_hcd
[    0.996729] usb usb3: SerialNumber: 0000:00:1a.0
[    0.996844] hub 3-0:1.0: USB hub found
[    0.996851] hub 3-0:1.0: 2 ports detected
[    0.997079] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.997085] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.997091] uhci_hcd 0000:00:1a.1: detected 2 ports
[    0.997114] uhci_hcd 0000:00:1a.1: irq 21, io base 0x000030c0
[    0.997159] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    0.997162] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.997164] usb usb4: Product: UHCI Host Controller
[    0.997166] usb usb4: Manufacturer: Linux 4.3.0-5-generic uhci_hcd
[    0.997169] usb usb4: SerialNumber: 0000:00:1a.1
[    0.997284] hub 4-0:1.0: USB hub found
[    0.997291] hub 4-0:1.0: 2 ports detected
[    0.997513] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.997521] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.997529] uhci_hcd 0000:00:1a.2: detected 2 ports
[    0.997546] uhci_hcd 0000:00:1a.2: irq 17, io base 0x000030a0
[    0.997591] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    0.997594] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.997596] usb usb5: Product: UHCI Host Controller
[    0.997598] usb usb5: Manufacturer: Linux 4.3.0-5-generic uhci_hcd
[    0.997600] usb usb5: SerialNumber: 0000:00:1a.2
[    0.997715] hub 5-0:1.0: USB hub found
[    0.997722] hub 5-0:1.0: 2 ports detected
[    0.997946] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.997952] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.997958] uhci_hcd 0000:00:1d.0: detected 2 ports
[    0.997975] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00003080
[    0.998020] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    0.998023] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.998025] usb usb6: Product: UHCI Host Controller
[    0.998027] usb usb6: Manufacturer: Linux 4.3.0-5-generic uhci_hcd
[    0.998030] usb usb6: SerialNumber: 0000:00:1d.0
[    0.998142] hub 6-0:1.0: USB hub found
[    0.998149] hub 6-0:1.0: 2 ports detected
[    0.998374] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.998382] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.998389] uhci_hcd 0000:00:1d.1: detected 2 ports
[    0.998412] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00003060
[    0.998462] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    0.998464] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.998467] usb usb7: Product: UHCI Host Controller
[    0.998469] usb usb7: Manufacturer: Linux 4.3.0-5-generic uhci_hcd
[    0.998471] usb usb7: SerialNumber: 0000:00:1d.1
[    0.998591] hub 7-0:1.0: USB hub found
[    0.998599] hub 7-0:1.0: 2 ports detected
[    0.998818] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.998825] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.998831] uhci_hcd 0000:00:1d.2: detected 2 ports
[    0.998848] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00003040
[    0.998893] usb usb8: New USB device found, idVendor=1d6b, idProduct=0001
[    0.998896] usb usb8: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.998898] usb usb8: Product: UHCI Host Controller
[    0.998900] usb usb8: Manufacturer: Linux 4.3.0-5-generic uhci_hcd
[    0.998902] usb usb8: SerialNumber: 0000:00:1d.2
[    0.999014] hub 8-0:1.0: USB hub found
[    0.999021] hub 8-0:1.0: 2 ports detected
[    0.999171] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.002372] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.002377] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.002535] mousedev: PS/2 mouse device common for all mice
[    1.002685] rtc_cmos 00:01: RTC can wake from S4
[    1.002804] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    1.002826] rtc_cmos 00:01: alarms up to one month, 114 bytes nvram, hpet irqs
[    1.002835] i2c /dev entries driver
[    1.002903] device-mapper: uevent: version 1.0.3
[    1.002987] device-mapper: ioctl: 4.33.0-ioctl (2015-8-18) initialised: dm-devel@redhat.com
[    1.003008] ledtrig-cpu: registered to indicate activity on CPUs
[    1.003423] NET: Registered protocol family 10
[    1.003702] NET: Registered protocol family 17
[    1.003723] Key type dns_resolver registered
[    1.004200] registered taskstats version 1
[    1.004215] Loading compiled-in X.509 certificates
[    1.005349] Loaded X.509 cert 'Build time autogenerated kernel key: 7c724264be95f5251ba6dcfc79faa85dca02c8a4'
[    1.005372] zswap: loaded using pool lzo/zbud
[    1.007590] Key type trusted registered
[    1.012055] Key type encrypted registered
[    1.012070] AppArmor: AppArmor sha1 policy hashing enabled
[    1.252093] evm: HMAC attrs: 0x1
[    1.252520]   Magic number: 0:366:580
[    1.252583] pci_bus 0000:01: hash matches
[    1.252655] rtc_cmos 00:01: setting system clock to 2016-01-16 11:35:41 UTC (1452944141)
[    1.253169] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.253171] EDD information not available.
[    1.253258] PM: Hibernation image not present or could not be loaded.
[    1.253772] Freeing unused kernel memory: 1464K (ffffffff81f3a000 - ffffffff820a8000)
[    1.253775] Write protecting the kernel read-only data: 14336k
[    1.254643] Freeing unused kernel memory: 2032K (ffff880001804000 - ffff880001a00000)
[    1.254780] Freeing unused kernel memory: 244K (ffff880001dc3000 - ffff880001e00000)
[    1.269101] random: systemd-udevd urandom read with 5 bits of entropy available
[    1.292029] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.308707] FUJITSU Extended Socket Network Device Driver - version 1.0 - Copyright (c) 2015 FUJITSU LIMITED
[    1.322628] pps_core: LinuxPPS API ver. 1 registered
[    1.322632] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    1.323727] [drm] Initialized drm 1.1.0 20060810
[    1.324255] PTP clock support registered
[    1.329000] e1000e: Intel(R) PRO/1000 Network Driver - 3.2.6-k
[    1.329002] e1000e: Copyright(c) 1999 - 2015 Intel Corporation.
[    1.329270] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    1.329400] scsi host0: pata_marvell
[    1.329529] scsi host1: pata_marvell
[    1.329614] ata1: PATA max UDMA/100 cmd 0x1018 ctl 0x1024 bmdma 0x1000 irq 18
[    1.329616] ata2: DUMMY
[    1.364031] usb 2-4: new high-speed USB device number 3 using ehci-pci
[    1.365462] [drm] radeon kernel modesetting enabled.
[    1.368123] AMD IOMMUv2 driver by Joerg Roedel <jroedel@suse.de>
[    1.368127] AMD IOMMUv2 functionality not available on this system
[    1.371593] CRAT table not found
[    1.371596] Finished initializing topology ret=0
[    1.371683] kfd kfd: Initialized module
[    1.372103] checking generic (d0000000 500000) vs hw (c0000000 10000000)
[    1.372222] radeon 0000:01:00.0: enabling device (0000 -> 0003)
[    1.372459] [drm] initializing kernel modesetting (CAICOS 0x1002:0x6779 0x174B:0xE164).
[    1.372475] [drm] register mmio base: 0xE0300000
[    1.372476] [drm] register mmio size: 131072
[    1.404896] firewire_ohci 0000:07:03.0: added OHCI v1.0 device as card 0, 8 IR + 8 IT contexts, quirks 0x0
[    1.426502] usb 1-1: New USB device found, idVendor=058f, idProduct=6362
[    1.426506] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.426508] usb 1-1: Product: Mass Storage Device
[    1.426511] usb 1-1: Manufacturer: Generic
[    1.426513] usb 1-1: SerialNumber: 058F63626376
[    1.436028] usb 7-1: new low-speed USB device number 2 using uhci_hcd
[    1.491704] ATOM BIOS: AMD
[    1.491758] [drm] GPU not posted. posting now...
[    1.495032] radeon 0000:01:00.0: VRAM: 512M 0x0000000000000000 - 0x000000001FFFFFFF (512M used)
[    1.495035] radeon 0000:01:00.0: GTT: 1024M 0x0000000020000000 - 0x000000005FFFFFFF
[    1.495037] [drm] Detected VRAM RAM=512M, BAR=256M
[    1.495039] [drm] RAM width 64bits DDR
[    1.495129] [TTM] Zone  kernel: Available graphics memory: 4046232 kiB
[    1.495131] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB
[    1.495132] [TTM] Initializing pool allocator
[    1.495139] [TTM] Initializing DMA pool allocator
[    1.495160] [drm] radeon: 512M of VRAM memory ready
[    1.495162] [drm] radeon: 1024M of GTT memory ready.
[    1.495185] [drm] Loading CAICOS Microcode
[    1.495290] [drm] Internal thermal controller without fan control
[    1.497141] usb 2-4: New USB device found, idVendor=0424, idProduct=2514
[    1.497144] usb 2-4: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.497366] hub 2-4:1.0: USB hub found
[    1.497449] hub 2-4:1.0: 4 ports detected
[    1.499569] [drm] radeon: dpm initialized
[    1.499700] [drm] GART: num cpu pages 262144, num gpu pages 262144
[    1.503514] [drm] PCIE GART of 1024M enabled (table at 0x0000000000274000).
[    1.503635] radeon 0000:01:00.0: WB enabled
[    1.503639] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000020000c00 and cpu addr 0xffff88022d775c00
[    1.503641] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000020000c0c and cpu addr 0xffff88022d775c0c
[    1.505115] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x0000000000072118 and cpu addr 0xffffc90001832118
[    1.505120] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    1.505122] [drm] Driver supports precise vblank timestamp query.
[    1.505124] radeon 0000:01:00.0: radeon: MSI limited to 32-bit
[    1.505319] radeon 0000:01:00.0: radeon: using MSI.
[    1.505368] [drm] radeon: irq initialized.
[    1.522099] [drm] ring test on 0 succeeded in 2 usecs
[    1.522111] [drm] ring test on 3 succeeded in 6 usecs
[    1.532394] ata1.00: ATAPI: LITE-ON DVDRW SHW-16H5S, LS0N, max UDMA/66
[    1.536021] usb 1-4: new high-speed USB device number 3 using ehci-pci
[    1.537588] ata1.01: HPA detected: current 976771055, native 976773168
[    1.537591] ata1.01: ATA-8: WDC WD5000AAKB-00H8A0, 05.04E05, max UDMA/133
[    1.537594] ata1.01: 976771055 sectors, multi 16: LBA48 
[    1.568368] ata1.00: configured for UDMA/66
[    1.584615] ata1.01: configured for UDMA/100
[    1.586056] scsi 0:0:0:0: CD-ROM            LITE-ON  DVDRW SHW-16H5S  LS0N PQ: 0 ANSI: 5
[    1.609828] sr 0:0:0:0: [sr0] scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    1.609830] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.610077] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.610228] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.610638] scsi 0:0:1:0: Direct-Access     ATA      WDC WD5000AAKB-0 4E05 PQ: 0 ANSI: 5
[    1.610874] sd 0:0:1:0: [sda] 976771055 512-byte logical blocks: (500 GB/465 GiB)
[    1.610926] sd 0:0:1:0: [sda] Write Protect is off
[    1.610930] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
[    1.610953] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.610979] sd 0:0:1:0: Attached scsi generic sg1 type 0
[    1.617154]  sda: sda1
[    1.617374] sd 0:0:1:0: [sda] Attached SCSI disk
[    1.666138] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) 00:1c:c0:81:f9:c7
[    1.666141] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    1.666168] e1000e 0000:00:19.0 eth0: MAC: 7, PHY: 6, PBA No: FFFFFF-0FF
[    1.666354] ahci 0000:00:1f.2: version 3.0
[    1.666587] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    1.666591] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pmp pio slum part ccc ems 
[    1.667499] e1000e 0000:00:19.0 enp0s25: renamed from eth0
[    1.669421] usb 1-4: New USB device found, idVendor=04e8, idProduct=6860
[    1.669424] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.669427] usb 1-4: Product: SAMSUNG_Android
[    1.669429] usb 1-4: Manufacturer: SAMSUNG
[    1.669431] usb 1-4: SerialNumber: 5a9b2cbd
[    1.674268] usb-storage 1-1:1.0: USB Mass Storage device detected
[    1.674679] scsi host2: usb-storage 1-1:1.0
[    1.674978] usbcore: registered new interface driver usb-storage
[    1.677037] usbcore: registered new interface driver uas
[    1.696044] usb 7-1: New USB device found, idVendor=04d9, idProduct=1603
[    1.696048] usb 7-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.696051] usb 7-1: Product: USB Keyboard
[    1.696053] usb 7-1: Manufacturer:  
[    1.697916] [drm] ring test on 5 succeeded in 2 usecs
[    1.697926] [drm] UVD initialized successfully.
[    1.698402] [drm] ib test on ring 0 succeeded in 0 usecs
[    1.698477] [drm] ib test on ring 3 succeeded in 0 usecs
[    1.707651] hidraw: raw HID events driver (C) Jiri Kosina
[    1.725685] scsi host3: ahci
[    1.725934] scsi host4: ahci
[    1.726181] scsi host5: ahci
[    1.726419] scsi host6: ahci
[    1.726662] scsi host7: ahci
[    1.726896] scsi host8: ahci
[    1.726971] ata3: SATA max UDMA/133 abar m2048@0xe04a5000 port 0xe04a5100 irq 32
[    1.726974] ata4: SATA max UDMA/133 abar m2048@0xe04a5000 port 0xe04a5180 irq 32
[    1.726976] ata5: SATA max UDMA/133 abar m2048@0xe04a5000 port 0xe04a5200 irq 32
[    1.726978] ata6: SATA max UDMA/133 abar m2048@0xe04a5000 port 0xe04a5280 irq 32
[    1.726981] ata7: SATA max UDMA/133 abar m2048@0xe04a5000 port 0xe04a5300 irq 32
[    1.726983] ata8: SATA max UDMA/133 abar m2048@0xe04a5000 port 0xe04a5380 irq 32
[    1.736046] usb 8-2: new low-speed USB device number 2 using uhci_hcd
[    1.804059] tsc: Refined TSC clocksource calibration: 2388.000 MHz
[    1.804064] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x226bef96e18, max_idle_ns: 440795310092 ns
[    1.825318] usbcore: registered new interface driver usbhid
[    1.825321] usbhid: USB HID core driver
[    1.827254] input:   USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/0003:04D9:1603.0001/input/input5
[    1.880186] hid-generic 0003:04D9:1603.0001: input,hidraw0: USB HID v1.10 Keyboard [  USB Keyboard] on usb-0000:00:1d.1-1/input0
[    1.894153] input:   USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.1/0003:04D9:1603.0002/input/input6
[    1.904164] firewire_core 0000:07:03.0: created device fw0: GUID 00902700022781ba, S400
[    1.912050] usb 8-2: New USB device found, idVendor=413c, idProduct=3012
[    1.912055] usb 8-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.912059] usb 8-2: Product: Dell USB Optical Mouse
[    1.912062] usb 8-2: Manufacturer: Dell
[    1.928531] input: Dell Dell USB Optical Mouse as /devices/pci0000:00/0000:00:1d.2/usb8/8-2/8-2:1.0/0003:413C:3012.0003/input/input7
[    1.948216] hid-generic 0003:04D9:1603.0002: input,hidraw1: USB HID v1.10 Device [  USB Keyboard] on usb-0000:00:1d.1-1/input1
[    1.948288] hid-generic 0003:413C:3012.0003: input,hidraw2: USB HID v1.11 Mouse [Dell Dell USB Optical Mouse] on usb-0000:00:1d.2-2/input0
[    2.048040] ata8: SATA link down (SStatus 0 SControl 300)
[    2.048067] ata6: SATA link down (SStatus 0 SControl 300)
[    2.048091] ata5: SATA link down (SStatus 0 SControl 300)
[    2.048113] ata7: SATA link down (SStatus 0 SControl 300)
[    2.212030] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.216031] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.216520] ata3.00: HPA detected: current 78163247, native 78165360
[    2.216585] ata3.00: ATA-7: WDC WD400BD-55MTA1, 10.01E01, max UDMA/133
[    2.216589] ata3.00: 78163247 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    2.217196] ata3.00: configured for UDMA/133
[    2.217406] scsi 3:0:0:0: Direct-Access     ATA      WDC WD400BD-55MT 1E01 PQ: 0 ANSI: 5
[    2.217698] sd 3:0:0:0: [sdb] 78163247 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    2.217769] sd 3:0:0:0: [sdb] Write Protect is off
[    2.217772] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.217775] sd 3:0:0:0: Attached scsi generic sg2 type 0
[    2.217797] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.221819]  sdb: sdb1
[    2.222104] sd 3:0:0:0: [sdb] Attached SCSI disk
[    2.240607] ata4.00: ATA-8: ST3640323AS, SD35, max UDMA/133
[    2.240612] ata4.00: 1250263728 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    2.282409] ata4.00: configured for UDMA/133
[    2.282548] scsi 4:0:0:0: Direct-Access     ATA      ST3640323AS      SD35 PQ: 0 ANSI: 5
[    2.282739] sd 4:0:0:0: [sdc] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
[    2.282779] sd 4:0:0:0: Attached scsi generic sg3 type 0
[    2.282787] sd 4:0:0:0: [sdc] Write Protect is off
[    2.282790] sd 4:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    2.282812] sd 4:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.330021]  sdc: sdc1 sdc2
[    2.330376] sd 4:0:0:0: [sdc] Attached SCSI disk
[    2.348106] [drm] ib test on ring 5 succeeded
[    2.349027] [drm] Radeon Display Connectors
[    2.349030] [drm] Connector 0:
[    2.349031] [drm]   HDMI-A-1
[    2.349032] [drm]   HPD2
[    2.349035] [drm]   DDC: 0x6440 0x6440 0x6444 0x6444 0x6448 0x6448 0x644c 0x644c
[    2.349036] [drm]   Encoders:
[    2.349037] [drm]     DFP1: INTERNAL_UNIPHY1
[    2.349038] [drm] Connector 1:
[    2.349040] [drm]   DVI-D-1
[    2.349041] [drm]   HPD4
[    2.349043] [drm]   DDC: 0x6460 0x6460 0x6464 0x6464 0x6468 0x6468 0x646c 0x646c
[    2.349044] [drm]   Encoders:
[    2.349045] [drm]     DFP2: INTERNAL_UNIPHY
[    2.349046] [drm] Connector 2:
[    2.349047] [drm]   VGA-1
[    2.349049] [drm]   DDC: 0x6430 0x6430 0x6434 0x6434 0x6438 0x6438 0x643c 0x643c
[    2.349050] [drm]   Encoders:
[    2.349052] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    2.468958] [drm] fb mappable at 0xC0475000
[    2.468961] [drm] vram apper at 0xC0000000
[    2.468963] [drm] size 8294400
[    2.468964] [drm] fb depth is 24
[    2.468966] [drm]    pitch is 7680
[    2.468969] checking generic (d0000000 500000) vs hw (c0000000 10000000)
[    2.469085] radeon 0000:01:00.0: fb1: radeondrmfb frame buffer device
[    2.484101] [drm] Initialized radeon 2.43.0 20080528 for 0000:01:00.0 on minor 0
[    2.484623] [drm] Memory usable by graphics device = 512M
[    2.484626] checking generic (d0000000 500000) vs hw (d0000000 10000000)
[    2.484628] fb: switching to inteldrmfb from VESA VGA
[    2.484665] Console: switching to colour dummy device 80x25
[    2.484732] [drm] Replacing VGA console driver
[    2.491753] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    2.491756] [drm] Driver supports precise vblank timestamp query.
[    2.491818] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none
[    2.491822] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=none:owns=io+mem
[    2.492826] [drm] initialized overlay support
[    2.492896] [drm] Initialized i915 1.6.0 20150731 for 0000:00:02.0 on minor 1
[    2.582956] fbcon: inteldrmfb (fb0) is primary device
[    2.583025] Console: switching to colour frame buffer device 160x64
[    2.583064] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    2.672820] scsi 2:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[    2.673439] scsi 2:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[    2.674062] scsi 2:0:0:2: Direct-Access     Generic  USB xD/SM Reader 1.02 PQ: 0 ANSI: 0
[    2.674685] scsi 2:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[    2.675223] sd 2:0:0:0: Attached scsi generic sg4 type 0
[    2.675673] sd 2:0:0:1: Attached scsi generic sg5 type 0
[    2.676146] sd 2:0:0:2: Attached scsi generic sg6 type 0
[    2.676452] sd 2:0:0:3: Attached scsi generic sg7 type 0
[    2.706053] sd 2:0:0:0: [sdd] Attached SCSI removable disk
[    2.706678] sd 2:0:0:1: [sde] Attached SCSI removable disk
[    2.707306] sd 2:0:0:2: [sdf] Attached SCSI removable disk
[    2.707930] sd 2:0:0:3: [sdg] Attached SCSI removable disk
[    2.804083] clocksource: Switched to clocksource tsc
[    4.328052] floppy0: no floppy controllers found
[    4.390928] random: nonblocking pool is initialized
[    4.615652] EXT4-fs (sdc1): mounted filesystem with ordered data mode. Opts: (null)
[    5.274078] systemd[1]: RTC configured in localtime, applying delta of 60 minutes to system time.
[    5.507858] systemd[1]: Failed to insert module 'kdbus': Function not implemented
[    5.688058] systemd[1]: systemd 228 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ -LZ4 +SECCOMP +BLKID +ELFUTILS +KMOD -IDN)
[    5.688246] systemd[1]: Detected architecture x86-64.
[    5.688745] systemd[1]: Set hostname to <mainframe>.
[    6.433105] systemd[1]: Listening on fsck to fsckd communication Socket.
[    6.433186] systemd[1]: Listening on /dev/initctl Compatibility Named Pipe.
[    6.433199] systemd[1]: Reached target Remote File Systems (Pre).
[    6.433210] systemd[1]: Reached target User and Group Name Lookups.
[    6.433221] systemd[1]: Reached target Encrypted Volumes.
[    6.433252] systemd[1]: Listening on Syslog Socket.
[    6.433263] systemd[1]: Reached target Remote File Systems.
[    6.433345] systemd[1]: Listening on Journal Audit Socket.
[    6.433498] systemd[1]: Created slice User and Session Slice.
[    6.433545] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[    6.433667] systemd[1]: Created slice System Slice.
[    6.433799] systemd[1]: Created slice system-getty.slice.
[    6.433811] systemd[1]: Reached target Slices.
[    6.433852] systemd[1]: Listening on udev Control Socket.
[    6.433990] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[    6.434025] systemd[1]: Listening on Journal Socket (/dev/log).
[    6.434066] systemd[1]: Listening on Journal Socket.
[    6.452230] systemd[1]: Starting Load Kernel Modules...
[    6.499759] systemd[1]: Mounting Debug File System...
[    6.500740] systemd[1]: Mounting POSIX Message Queue File System...
[    6.501580] systemd[1]: Starting Uncomplicated firewall...
[    6.502436] systemd[1]: Starting Create list of required static device nodes for the current kernel...
[    6.503254] systemd[1]: Started Read required files in advance.
[    6.504301] systemd[1]: Starting Journal Service...
[    6.505172] systemd[1]: Mounting Huge Pages File System...
[    6.505999] systemd[1]: Starting Braille Device Support...
[    6.506062] systemd[1]: Listening on udev Kernel Socket.
[    6.591154] systemd[1]: Started Uncomplicated firewall.
[    6.602438] systemd[1]: Started Create list of required static device nodes for the current kernel.
[    6.603316] systemd[1]: Starting Create Static Device Nodes in /dev...
[    6.841842] systemd[1]: Mounted Debug File System.
[    6.841888] systemd[1]: Mounted Huge Pages File System.
[    6.841908] systemd[1]: Mounted POSIX Message Queue File System.
[    6.988934] systemd[1]: Started Load Kernel Modules.
[    6.989798] systemd[1]: Mounting FUSE Control File System...
[    6.990511] systemd[1]: Starting Apply Kernel Variables...
[    6.994989] systemd[1]: Mounted FUSE Control File System.
[    7.096720] systemd[1]: Started Apply Kernel Variables.
[    7.233750] systemd[1]: Started Journal Service.
[    9.646914] EXT4-fs (sdc1): re-mounted. Opts: errors=remount-ro
[    9.904588] systemd-journald[277]: Received request to flush runtime journal from PID 1
[   10.658283] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.807532] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x000000000000050C-0x000000000000050F (\IGPO) (20150818/utaddress-254)
[   10.807540] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   11.380076] coretemp coretemp.0: Using relative temperature scale!
[   11.380099] coretemp coretemp.0: Using relative temperature scale!
[   11.380114] coretemp coretemp.0: Using relative temperature scale!
[   11.380129] coretemp coretemp.0: Using relative temperature scale!
[   11.403535] snd_hda_intel 0000:01:00.1: Handle VGA-switcheroo audio client
[   11.411707] ppdev: user-space parallel port driver
[   11.412166] gpio_ich: GPIO from 451 to 511 on gpio_ich
[   11.422971] snd_hda_codec_hdmi hdaudioC1D0: HDMI ATI/AMD: no speaker allocation for ELD
[   11.423606] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input8
[   11.624701] snd_hda_codec_realtek hdaudioC0D2: autoconfig for ALC268: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:line
[   11.624706] snd_hda_codec_realtek hdaudioC0D2:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   11.624709] snd_hda_codec_realtek hdaudioC0D2:    hp_outs=1 (0x15/0x0/0x0/0x0/0x0)
[   11.624711] snd_hda_codec_realtek hdaudioC0D2:    mono: mono_out=0x0
[   11.624713] snd_hda_codec_realtek hdaudioC0D2:    inputs:
[   11.624716] snd_hda_codec_realtek hdaudioC0D2:      Rear Mic=0x18
[   11.624719] snd_hda_codec_realtek hdaudioC0D2:      Front Mic=0x1a
[   11.624721] snd_hda_codec_realtek hdaudioC0D2:      Line=0x19
[   11.630918] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   11.631031] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   11.631122] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   11.631207] input: HDA Intel Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   11.631285] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   13.137239] Adding 5990396k swap on /dev/sdc2.  Priority:-1 extents:1 across:5990396k FS
[   13.673433] audit: type=1400 audit(1452940553.917:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=570 comm="apparmor_parser"
[   13.673443] audit: type=1400 audit(1452940553.917:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=570 comm="apparmor_parser"
[   13.699037] audit: type=1400 audit(1452940553.941:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=570 comm="apparmor_parser"
[   13.699045] audit: type=1400 audit(1452940553.941:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=570 comm="apparmor_parser"
[   13.699052] audit: type=1400 audit(1452940553.941:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=570 comm="apparmor_parser"
[   13.699057] audit: type=1400 audit(1452940553.941:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=570 comm="apparmor_parser"
[   13.704060] floppy0: no floppy controllers found
[   13.797634] audit: type=1400 audit(1452940554.041:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince" pid=570 comm="apparmor_parser"
[   13.797646] audit: type=1400 audit(1452940554.041:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=570 comm="apparmor_parser"
[   13.797653] audit: type=1400 audit(1452940554.041:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-previewer" pid=570 comm="apparmor_parser"
[   13.797660] audit: type=1400 audit(1452940554.041:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=570 comm="apparmor_parser"
[   15.710252] cgroup: new mount options do not match the existing superblock, will be ignored
[   21.005628] IPv6: ADDRCONF(NETDEV_UP): enp0s25: link is not ready
[   21.472421] IPv6: ADDRCONF(NETDEV_UP): enp0s25: link is not ready
[   22.868875] e1000e: enp0s25 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
[   22.868984] e1000e 0000:00:19.0 enp0s25: 10/100 speed: disabling TSO
[   22.869015] IPv6: ADDRCONF(NETDEV_CHANGE): enp0s25: link becomes ready
[   59.098932] usb 1-4: USB disconnect, device number 3
[   59.476332] usb 1-4: new high-speed USB device number 4 using ehci-pci
[   59.609504] usb 1-4: New USB device found, idVendor=04e8, idProduct=6860
[   59.609510] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[   59.609514] usb 1-4: Product: SAMSUNG_Android
[   59.609517] usb 1-4: Manufacturer: SAMSUNG
[   59.609521] usb 1-4: SerialNumber: 5a9b2cbd
[  390.430377] show_signal_msg: 18 callbacks suppressed
[  390.430383] gvfsd-network[1756]: segfault at 6c00000001 ip 00007f773138ba75 sp 00007ffd398ca000 error 4 in libgvfsdaemon.so[7f773137c000+24000]
[  390.431010] gvfsd-network[1738]: segfault at 6c00000001 ip 00007fd514040a75 sp 00007ffe064b10c0 error 4 in libgvfsdaemon.so[7fd514031000+24000]
[  536.120039] perf interrupt took too long (2505 > 2500), lowering kernel.perf_event_max_sample_rate to 50000

```

and lspci 

```

00:00.0 Host bridge: Intel Corporation 82Q35 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82Q35 Express PCI Express Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82Q35 Express Integrated Graphics Controller (rev 02)
00:03.0 Communication controller: Intel Corporation 82Q35 Express MEI Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DM-2 Gigabit Network Connection (rev 02)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IO (ICH9DO) LPC Interface Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 6 port SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Caicos [Radeon HD 6450/7450/8450 / R5 230 OEM]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Caicos HDMI Audio [Radeon HD 6400 Series]
04:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6101/6102 single-port PATA133 interface (rev b2)
07:03.0 FireWire (IEEE 1394): LSI Corporation FW322/323 [TrueFire] 1394a Controller (rev 70)

```

please looks into ubuntu`s code and mechanism of multiple graphics cards / monitors 

Regards
Pawel

---

### Post by geomcd1949 on 2016-01-20
I have a similar problem.

---

### Post by Vladlenin5000 on 2016-01-21
Not really a problem, it's by design.
Most boards do NOT support using integrated and discrete graphics simultaneously.

---

### Post by pawe9 on 2016-02-08
Hello,
but the on Ubuntu 14.04.03 64bit it works.

P.

---

