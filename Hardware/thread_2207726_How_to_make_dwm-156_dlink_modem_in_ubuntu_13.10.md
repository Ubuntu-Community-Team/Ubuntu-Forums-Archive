---
title: "How to make dwm-156 dlink modem in ubuntu 13.10?"
date: 2014-02-24
forum: Hardware
---

### Post by rubankumars on 2014-02-24
I use ubuntu 13.10 64 bit.I used ethernet before.But,I am now using wireless internet using D link dwm-156 modem (hsupa usb adapter).How to make it work in ubuntu 13.10? my service provider is vodafone.

---

### Post by varunendra on 2014-02-25
Please unplug the modem > wait about 10 seconds > replug > wait about 30 seconds > open a terminal (Ctrl-Alt-T) and run the following commands in it -
```
lsusb
dmesg | tail -20
```
Post back the outputs from the terminal.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by rubankumars on 2014-02-26
```
  Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 04ca:0061 Lite-On Technology Corp. 
Bus 003 Device 003: ID 2001:7d01 D-Link Corp. 
Bus 003 Device 002: ID 0e8f:0022 GreenAsia Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

  
```
```
  [    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.11.0-17-generic (buildd@toyol) (gcc version 4.8.1 (Ubuntu/Linaro 4.8.1-10ubuntu8) ) #31-Ubuntu SMP Mon Feb 3 21:52:43 UTC 2014 (Ubuntu 3.11.0-17.31-generic 3.11.10.3)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-17-generic root=UUID=56195e25-3e7c-4c02-9670-ce1d1a9bc448 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009d7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009d800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000b8c77fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000b8c78000-0x00000000b8c7efff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000b8c7f000-0x00000000b9a8cfff] usable
[    0.000000] BIOS-e820: [mem 0x00000000b9a8d000-0x00000000ba053fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ba054000-0x00000000cb354fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000cb355000-0x00000000cb3defff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000cb3df000-0x00000000cb3f3fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000cb3f4000-0x00000000cb563fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000cb564000-0x00000000cbffefff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000cbfff000-0x00000000cbffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000d7000000-0x00000000df1fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000011fdfffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI:                  /DH87RL, BIOS RLH8710H.86A.0320.2013.0606.1802 06/06/2013
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x11fe00 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask 7F00000000 write-back
[    0.000000]   1 base 0100000000 mask 7FE0000000 write-back
[    0.000000]   2 base 00E0000000 mask 7FE0000000 uncachable
[    0.000000]   3 base 00D8000000 mask 7FF8000000 uncachable
[    0.000000]   4 base 00D7000000 mask 7FFF000000 uncachable
[    0.000000]   5 base 011FE00000 mask 7FFFE00000 uncachable
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 4GB, type WB
[    0.000000] reg 1, base: 4GB, range: 512MB, type WB
[    0.000000] reg 2, base: 3584MB, range: 512MB, type UC
[    0.000000] reg 3, base: 3456MB, range: 128MB, type UC
[    0.000000] reg 4, base: 3440MB, range: 16MB, type UC
[    0.000000] reg 5, base: 4606MB, range: 2MB, type UC
[    0.000000] total RAM covered: 3950M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K      chunk_size: 32M   num_reg: 7        lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 256MB, type WB
[    0.000000] reg 3, base: 3328MB, range: 128MB, type WB
[    0.000000] reg 4, base: 3440MB, range: 16MB, type UC
[    0.000000] reg 5, base: 4GB, range: 512MB, type WB
[    0.000000] reg 6, base: 4606MB, range: 2MB, type UC
[    0.000000] e820: update [mem 0xd7000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xcc000 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fd680-0x000fd68f] mapped at [ffff8800000fd680]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fd1000, 0x01fd1fff] PGTABLE
[    0.000000] BRK [0x01fd2000, 0x01fd2fff] PGTABLE
[    0.000000] BRK [0x01fd3000, 0x01fd3fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x11fc00000-0x11fdfffff]
[    0.000000]  [mem 0x11fc00000-0x11fdfffff] page 2M
[    0.000000] BRK [0x01fd4000, 0x01fd4fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x11c000000-0x11fbfffff]
[    0.000000]  [mem 0x11c000000-0x11fbfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x100000000-0x11bffffff]
[    0.000000]  [mem 0x100000000-0x11bffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0xb8c77fff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
[    0.000000]  [mem 0x40000000-0x7fffffff] page 1G
[    0.000000]  [mem 0x80000000-0xb8bfffff] page 2M
[    0.000000]  [mem 0xb8c00000-0xb8c77fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xb8c7f000-0xb9a8cfff]
[    0.000000]  [mem 0xb8c7f000-0xb8dfffff] page 4k
[    0.000000]  [mem 0xb8e00000-0xb99fffff] page 2M
[    0.000000]  [mem 0xb9a00000-0xb9a8cfff] page 4k
[    0.000000] BRK [0x01fd5000, 0x01fd5fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0xba054000-0xcb354fff]
[    0.000000]  [mem 0xba054000-0xba1fffff] page 4k
[    0.000000]  [mem 0xba200000-0xcb1fffff] page 2M
[    0.000000]  [mem 0xcb200000-0xcb354fff] page 4k
[    0.000000] BRK [0x01fd6000, 0x01fd6fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0xcbfff000-0xcbffffff]
[    0.000000]  [mem 0xcbfff000-0xcbffffff] page 4k
[    0.000000] RAMDISK: [mem 0x34e06000-0x366fafff]
[    0.000000] ACPI: RSDP 00000000000f0490 00024 (v02  INTEL)
[    0.000000] ACPI: XSDT 00000000cb3e3080 0007C (v01 INTEL  DH87RL   00000140 AMI  00010013)
[    0.000000] ACPI: FACP 00000000cb3ee8f8 0010C (v05 INTEL  DH87RL   00000140 AMI  00010013)
[    0.000000] ACPI: DSDT 00000000cb3e3188 0B76D (v02 INTEL  DH87RL   00000140 INTL 20120711)
[    0.000000] ACPI: FACS 00000000cb562080 00040
[    0.000000] ACPI: APIC 00000000cb3eea08 00092 (v03 INTEL  DH87RL   00000140 AMI  00010013)
[    0.000000] ACPI: FPDT 00000000cb3eeaa0 00044 (v01 INTEL  DH87RL   00000140 AMI  00010013)
[    0.000000] ACPI: SSDT 00000000cb3eeae8 00539 (v01 INTEL  DH87RL   00000140 INTL 20051117)
[    0.000000] ACPI: SSDT 00000000cb3ef028 00AD8 (v01 INTEL  DH87RL   00000140 INTL 20051117)
[    0.000000] ACPI: SSDT 00000000cb3efb00 001C7 (v01 INTEL  DH87RL   00000140 INTL 20051117)
[    0.000000] ACPI: MCFG 00000000cb3efcc8 0003C (v01 INTEL  DH87RL   00000140 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000cb3efd08 00038 (v01 INTEL  DH87RL   00000140 AMI. 00000005)
[    0.000000] ACPI: SSDT 00000000cb3efd40 0036D (v01 INTEL  DH87RL   00000140 INTL 20091112)
[    0.000000] ACPI: SSDT 00000000cb3f00b0 02EDB (v01 INTEL  DH87RL   00000140 INTL 20091112)
[    0.000000] ACPI: DMAR 00000000cb3f2f90 000B8 (v01 INTEL  DH87RL   00000140 INTL 00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000011fdfffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x11fdfffff]
[    0.000000]   NODE_DATA [mem 0x11fdf6000-0x11fdfafff]
[    0.000000]  [ffffea0000000000-ffffea00047fffff] PMD -> [ffff88011b800000-ffff88011f3fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x11fdfffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009cfff]
[    0.000000]   node   0: [mem 0x00100000-0xb8c77fff]
[    0.000000]   node   0: [mem 0xb8c7f000-0xb9a8cfff]
[    0.000000]   node   0: [mem 0xba054000-0xcb354fff]
[    0.000000]   node   0: [mem 0xcbfff000-0xcbffffff]
[    0.000000]   node   0: [mem 0x100000000-0x11fdfffff]
[    0.000000] On node 0 totalpages: 961316
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3996 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 12919 pages used for memmap
[    0.000000]   DMA32 zone: 826760 pages, LIFO batch:31
[    0.000000]   Normal zone: 2040 pages used for memmap
[    0.000000]   Normal zone: 130560 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009dfff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xb8c78000-0xb8c7efff]
[    0.000000] PM: Registered nosave memory: [mem 0xb9a8d000-0xba053fff]
[    0.000000] PM: Registered nosave memory: [mem 0xcb355000-0xcb3defff]
[    0.000000] PM: Registered nosave memory: [mem 0xcb3df000-0xcb3f3fff]
[    0.000000] PM: Registered nosave memory: [mem 0xcb3f4000-0xcb563fff]
[    0.000000] PM: Registered nosave memory: [mem 0xcb564000-0xcbffefff]
[    0.000000] PM: Registered nosave memory: [mem 0xcc000000-0xd6ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xd7000000-0xdf1fffff]
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
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff88011fa00000 s86720 r8192 d23872 u262144
[    0.000000] pcpu-alloc: s86720 r8192 d23872 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 946272
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-17-generic root=UUID=56195e25-3e7c-4c02-9670-ce1d1a9bc448 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3674692K/3845264K available (7150K kernel code, 1083K rwdata, 3312K rodata, 1364K init, 1420K bss, 170572K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]    RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]    RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000]    Offload RCU callbacks from all CPUs
[    0.000000]    Offload RCU callbacks from CPUs: 0-255.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 15728640 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 2993.239 MHz processor
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 5986.47 BogoMIPS (lpj=11972956)
[    0.000004] pid_max: default: 32768 minimum: 301
[    0.000022] Security Framework initialized
[    0.000037] AppArmor: AppArmor initialized
[    0.000038] Yama: becoming mindful.
[    0.000235] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.001262] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.001734] Mount-cache hash table entries: 256
[    0.001871] Initializing cgroup subsys memory
[    0.001879] Initializing cgroup subsys devices
[    0.001880] Initializing cgroup subsys freezer
[    0.001881] Initializing cgroup subsys blkio
[    0.001882] Initializing cgroup subsys perf_event
[    0.001884] Initializing cgroup subsys hugetlb
[    0.001900] CPU: Physical Processor ID: 0
[    0.001901] CPU: Processor Core ID: 0
[    0.001904] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.001904] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.002689] mce: CPU supports 9 MCE banks
[    0.002701] CPU0: Thermal monitoring enabled (TM1)
[    0.002711] Last level iTLB entries: 4KB 0, 2MB 0, 4MB 0
[    0.002711] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 0
[    0.002711] tlb_flushall_shift: 6
[    0.002799] Freeing SMP alternatives memory: 28K (ffffffff81e65000 - ffffffff81e6c000)
[    0.004196] ACPI: Core revision 20130517
[    0.009926] ACPI: All ACPI Tables successfully acquired
[    0.010575] ftrace: allocating 27846 entries in 109 pages
[    0.019732] dmar: Host address width 39
[    0.019734] dmar: DRHD base: 0x000000fed90000 flags: 0x0
[    0.019738] dmar: IOMMU 0: reg_base_addr fed90000 ver 1:0 cap c0000020660462 ecap f0101a
[    0.019739] dmar: DRHD base: 0x000000fed91000 flags: 0x1
[    0.019743] dmar: IOMMU 1: reg_base_addr fed91000 ver 1:0 cap d2008020660462 ecap f010da
[    0.019744] dmar: RMRR base: 0x000000cbeb9000 end: 0x000000cbec7fff
[    0.019744] dmar: RMRR base: 0x000000d7000000 end: 0x000000df1fffff
[    0.019814] IOAPIC id 2 under DRHD base  0xfed91000 IOMMU 1
[    0.019814] HPET id 0 under DRHD base 0xfed91000
[    0.020001] Enabled IRQ remapping in x2apic mode
[    0.020002] Enabling x2apic
[    0.020003] Enabled x2apic
[    0.020011] Switched APIC routing to cluster x2apic.
[    0.020437] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.060108] smpboot: CPU0: Intel(R) Core(TM) i7-4770 CPU @ 3.40GHz (fam: 06, model: 3c, stepping: 03)
[    0.060119] TSC deadline timer enabled
[    0.060125] Performance Events: PEBS fmt2+, 16-deep LBR, Haswell events, full-width counters, Intel PMU driver.
[    0.060130] ... version:                3
[    0.060130] ... bit width:              48
[    0.060131] ... generic registers:      4
[    0.060132] ... value mask:             0000ffffffffffff
[    0.060132] ... max period:             0000ffffffffffff
[    0.060133] ... fixed-purpose events:   3
[    0.060134] ... event mask:             000000070000000f
[    0.075127] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.061237] smpboot: Booting Node   0, Processors  #1 #2 #3 #4 #5 #6 #7 OK
[    0.158514] Brought up 8 CPUs
[    0.158517] smpboot: Total of 8 processors activated (47891.82 BogoMIPS)
[    0.166160] devtmpfs: initialized
[    0.166752] EVM: security.selinux
[    0.166753] EVM: security.SMACK64
[    0.166754] EVM: security.capability
[    0.166784] PM: Registering ACPI NVS region [mem 0xb8c78000-0xb8c7efff] (28672 bytes)
[    0.166785] PM: Registering ACPI NVS region [mem 0xcb3f4000-0xcb563fff] (1507328 bytes)
[    0.167339] regulator-dummy: no parameters
[    0.167369] RTC time: 13:00:05, date: 02/26/14
[    0.167392] NET: Registered protocol family 16
[    0.167479] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.167480] ACPI: bus type PCI registered
[    0.167482] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.167519] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.167521] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.172205] PCI: Using configuration type 1 for base access
[    0.172806] bio: create slab <bio-0> at 0
[    0.172914] ACPI: Added _OSI(Module Device)
[    0.172915] ACPI: Added _OSI(Processor Device)
[    0.172916] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.172917] ACPI: Added _OSI(Processor Aggregator Device)
[    0.174224] ACPI: EC: Look up EC in DSDT
[    0.175662] ACPI: Executed 1 blocks of module-level executable AML code
[    0.177426] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.178062] ACPI: SSDT 00000000cb3d4c18 003D3 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.178390] ACPI: Dynamic OEM Table Load:
[    0.178391] ACPI: SSDT           (null) 003D3 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.182174] ACPI: SSDT 00000000cb3d4618 005AA (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.182555] ACPI: Dynamic OEM Table Load:
[    0.182556] ACPI: SSDT           (null) 005AA (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.198055] ACPI: SSDT 00000000cb3d3d98 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.198380] ACPI: Dynamic OEM Table Load:
[    0.198381] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.206832] ACPI: Interpreter enabled
[    0.206837] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20130517/hwxface-571)
[    0.206841] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20130517/hwxface-571)
[    0.206852] ACPI: (supports S0 S3 S4 S5)
[    0.206853] ACPI: Using IOAPIC for interrupt routing
[    0.206872] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.206973] ACPI: No dock devices found.
[    0.212380] ACPI: Power Resource [FN00] (off)
[    0.212430] ACPI: Power Resource [FN01] (off)
[    0.212476] ACPI: Power Resource [FN02] (off)
[    0.212522] ACPI: Power Resource [FN03] (off)
[    0.212567] ACPI: Power Resource [FN04] (off)
[    0.213097] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    0.213247] acpi PNP0A08:00: Requesting ACPI _OSC control (0x1d)
[    0.213376] acpi PNP0A08:00: ACPI _OSC control (0x18) granted
[    0.213699] PCI host bridge to bus 0000:00
[    0.213700] pci_bus 0000:00: root bus resource [bus 00-3e]
[    0.213702] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.213703] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.213704] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.213705] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    0.213706] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    0.213707] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    0.213708] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    0.213709] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
[    0.213710] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff]
[    0.213711] pci_bus 0000:00: root bus resource [mem 0xdf200000-0xfeafffff]
[    0.213717] pci 0000:00:00.0: [8086:0c00] type 00 class 0x060000
[    0.213786] pci 0000:00:02.0: [8086:0412] type 00 class 0x030000
[    0.213795] pci 0000:00:02.0: reg 0x10: [mem 0xf7800000-0xf7bfffff 64bit]
[    0.213800] pci 0000:00:02.0: reg 0x18: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.213804] pci 0000:00:02.0: reg 0x20: [io  0xf000-0xf03f]
[    0.213857] pci 0000:00:03.0: [8086:0c0c] type 00 class 0x040300
[    0.213863] pci 0000:00:03.0: reg 0x10: [mem 0xf7c34000-0xf7c37fff 64bit]
[    0.213946] pci 0000:00:14.0: [8086:8c31] type 00 class 0x0c0330
[    0.213962] pci 0000:00:14.0: reg 0x10: [mem 0xf7c20000-0xf7c2ffff 64bit]
[    0.214019] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.214049] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.214076] pci 0000:00:16.0: [8086:8c3a] type 00 class 0x078000
[    0.214093] pci 0000:00:16.0: reg 0x10: [mem 0xf7c3f000-0xf7c3f00f 64bit]
[    0.214149] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.214208] pci 0000:00:19.0: [8086:153b] type 00 class 0x020000
[    0.214223] pci 0000:00:19.0: reg 0x10: [mem 0xf7c00000-0xf7c1ffff]
[    0.214230] pci 0000:00:19.0: reg 0x14: [mem 0xf7c3d000-0xf7c3dfff]
[    0.214237] pci 0000:00:19.0: reg 0x18: [io  0xf080-0xf09f]
[    0.214289] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.214319] pci 0000:00:19.0: System wakeup disabled by ACPI
[    0.214350] pci 0000:00:1a.0: [8086:8c2d] type 00 class 0x0c0320
[    0.214368] pci 0000:00:1a.0: reg 0x10: [mem 0xf7c3c000-0xf7c3c3ff]
[    0.214447] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.214494] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.214520] pci 0000:00:1b.0: [8086:8c20] type 00 class 0x040300
[    0.214532] pci 0000:00:1b.0: reg 0x10: [mem 0xf7c30000-0xf7c33fff 64bit]
[    0.214589] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.214620] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.214647] pci 0000:00:1d.0: [8086:8c26] type 00 class 0x0c0320
[    0.214665] pci 0000:00:1d.0: reg 0x10: [mem 0xf7c3b000-0xf7c3b3ff]
[    0.214744] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.214787] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.214814] pci 0000:00:1f.0: [8086:8c4a] type 00 class 0x060100
[    0.214955] pci 0000:00:1f.2: [8086:8c02] type 00 class 0x010601
[    0.214968] pci 0000:00:1f.2: reg 0x10: [io  0xf0d0-0xf0d7]
[    0.214975] pci 0000:00:1f.2: reg 0x14: [io  0xf0c0-0xf0c3]
[    0.214981] pci 0000:00:1f.2: reg 0x18: [io  0xf0b0-0xf0b7]
[    0.214987] pci 0000:00:1f.2: reg 0x1c: [io  0xf0a0-0xf0a3]
[    0.214993] pci 0000:00:1f.2: reg 0x20: [io  0xf060-0xf07f]
[    0.215000] pci 0000:00:1f.2: reg 0x24: [mem 0xf7c3a000-0xf7c3a7ff]
[    0.215033] pci 0000:00:1f.2: PME# supported from D3hot
[    0.215081] pci 0000:00:1f.3: [8086:8c22] type 00 class 0x0c0500
[    0.215093] pci 0000:00:1f.3: reg 0x10: [mem 0xf7c39000-0xf7c390ff 64bit]
[    0.215111] pci 0000:00:1f.3: reg 0x20: [io  0xf040-0xf05f]
[    0.215167] acpi PNP0A08:00: Disabling ASPM (FADT indicates it is unsupported)
[    0.215714] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.215763] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.215807] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.215855] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.215904] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 10 11 12 14 15)
[    0.215951] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.215995] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 6 10 11 12 14 15)
[    0.216042] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 *4 5 6 10 11 12 14 15)
[    0.216313] ACPI: Enabled 5 GPEs in block 00 to 3F
[    0.216318] ACPI: \_SB_.PCI0: notify handler is installed
[    0.216363] Found 1 acpi root devices
[    0.216426] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.216428] vgaarb: loaded
[    0.216428] vgaarb: bridge control possible 0000:00:02.0
[    0.216523] SCSI subsystem initialized
[    0.216525] ACPI: bus type ATA registered
[    0.216554] libata version 3.00 loaded.
[    0.216563] ACPI: bus type USB registered
[    0.216573] usbcore: registered new interface driver usbfs
[    0.216577] usbcore: registered new interface driver hub
[    0.216600] usbcore: registered new device driver usb
[    0.216666] PCI: Using ACPI for IRQ routing
[    0.217954] PCI: pci_cache_line_size set to 64 bytes
[    0.217986] e820: reserve RAM buffer [mem 0x0009d800-0x0009ffff]
[    0.217987] e820: reserve RAM buffer [mem 0xb8c78000-0xbbffffff]
[    0.217988] e820: reserve RAM buffer [mem 0xb9a8d000-0xbbffffff]
[    0.217989] e820: reserve RAM buffer [mem 0xcb355000-0xcbffffff]
[    0.217990] e820: reserve RAM buffer [mem 0x11fe00000-0x11fffffff]
[    0.218044] NetLabel: Initializing
[    0.218045] NetLabel:  domain hash size = 128
[    0.218046] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.218053] NetLabel:  unlabeled traffic allowed by default
[    0.218092] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.218095] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.220122] Switched to clocksource hpet
[    0.223185] AppArmor: AppArmor Filesystem Enabled
[    0.223195] pnp: PnP ACPI init
[    0.223201] ACPI: bus type PNP registered
[    0.223240] system 00:00: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.223242] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.223248] pnp 00:01: [dma 4]
[    0.223257] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.223267] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    0.223352] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.223390] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.223457] system 00:05: [io  0x0680-0x069f] has been reserved
[    0.223458] system 00:05: [io  0xffff] has been reserved
[    0.223460] system 00:05: [io  0xffff] has been reserved
[    0.223461] system 00:05: [io  0xffff] has been reserved
[    0.223462] system 00:05: [io  0x1c00-0x1cfe] has been reserved
[    0.223463] system 00:05: [io  0x1d00-0x1dfe] has been reserved
[    0.223464] system 00:05: [io  0x1e00-0x1efe] has been reserved
[    0.223465] system 00:05: [io  0x1f00-0x1ffe] has been reserved
[    0.223467] system 00:05: [io  0x1800-0x18fe] could not be reserved
[    0.223468] system 00:05: [io  0x164e-0x164f] has been reserved
[    0.223469] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.223491] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.223514] system 00:07: [io  0x1854-0x1857] has been reserved
[    0.223516] system 00:07: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.223576] system 00:08: [io  0x0a00-0x0a1f] has been reserved
[    0.223578] system 00:08: [io  0x0a20-0x0a23] has been reserved
[    0.223579] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.223643] system 00:09: [io  0x04d0-0x04d1] has been reserved
[    0.223645] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.223980] system 00:0a: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.223982] system 00:0a: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.223983] system 00:0a: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.223984] system 00:0a: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.223987] system 00:0a: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.223988] system 00:0a: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.223989] system 00:0a: [mem 0xfed90000-0xfed93fff] could not be reserved
[    0.223990] system 00:0a: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.223992] system 00:0a: [mem 0xff000000-0xffffffff] has been reserved
[    0.223993] system 00:0a: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.223994] system 00:0a: [mem 0xf7fef000-0xf7feffff] has been reserved
[    0.223995] system 00:0a: [mem 0xf7ff0000-0xf7ff0fff] has been reserved
[    0.223997] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.224184] pnp: PnP ACPI: found 11 devices
[    0.224185] ACPI: bus type PNP unregistered
[    0.230221] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.230223] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.230224] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.230225] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.230226] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.230227] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.230229] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    0.230230] pci_bus 0000:00: resource 11 [mem 0x000e0000-0x000e3fff]
[    0.230231] pci_bus 0000:00: resource 12 [mem 0x000e4000-0x000e7fff]
[    0.230232] pci_bus 0000:00: resource 13 [mem 0xdf200000-0xfeafffff]
[    0.230250] NET: Registered protocol family 2
[    0.230351] TCP established hash table entries: 32768 (order: 7, 524288 bytes)
[    0.230478] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
[    0.230582] TCP: Hash tables configured (established 32768 bind 32768)
[    0.230599] TCP: reno registered
[    0.230605] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.230622] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.230670] NET: Registered protocol family 1
[    0.230677] pci 0000:00:02.0: Boot video device
[    0.268190] PCI: CLS 64 bytes, default 64
[    0.268214] Trying to unpack rootfs image as initramfs...
[    0.568762] Freeing initrd memory: 25556K (ffff880034e06000 - ffff8800366fb000)
[    0.568770] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.568772] software IO TLB [mem 0xc7355000-0xcb355000] (64MB) mapped at [ffff8800c7355000-ffff8800cb354fff]
[    0.568986] Scanning for low memory corruption every 60 seconds
[    0.569209] Initialise module verification
[    0.569239] audit: initializing netlink socket (disabled)
[    0.569247] type=2000 audit(1393419604.556:1): initialized
[    0.588307] bounce pool size: 64 pages
[    0.588314] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.589019] zbud: loaded
[    0.589115] VFS: Disk quotas dquot_6.5.2
[    0.589139] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.589438] fuse init (API version 7.22)
[    0.589486] msgmni has been set to 7227
[    0.589890] Key type asymmetric registered
[    0.589891] Asymmetric key parser 'x509' registered
[    0.589908] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.589949] io scheduler noop registered
[    0.589950] io scheduler deadline registered (default)
[    0.589963] io scheduler cfq registered
[    0.590011] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.590019] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.590052] intel_idle: MWAIT substates: 0x42120
[    0.590053] intel_idle: v0.4 model 0x3C
[    0.590054] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.590141] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.590145] ACPI: Power Button [PWRB]
[    0.590166] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.590167] ACPI: Power Button [PWRF]
[    0.590222] ACPI: Fan [FAN0] (off)
[    0.590239] ACPI: Fan [FAN1] (off)
[    0.590251] ACPI: Fan [FAN2] (off)
[    0.590264] ACPI: Fan [FAN3] (off)
[    0.590277] ACPI: Fan [FAN4] (off)
[    0.590313] ACPI: Requesting acpi_cpufreq
[    0.590766] thermal LNXTHERM:00: registered as thermal_zone0
[    0.590767] ACPI: Thermal Zone [TZ00] (28 C)
[    0.590912] thermal LNXTHERM:01: registered as thermal_zone1
[    0.590913] ACPI: Thermal Zone [TZ01] (30 C)
[    0.590931] GHES: HEST is not enabled!
[    0.590983] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.592064] Linux agpgart interface v0.103
[    0.592875] brd: module loaded
[    0.593286] loop: module loaded
[    0.593484] libphy: Fixed MDIO Bus: probed
[    0.593530] tun: Universal TUN/TAP device driver, 1.6
[    0.593530] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.593565] PPP generic driver version 2.4.2
[    0.593595] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.593597] ehci-pci: EHCI PCI platform driver
[    0.593678] ehci-pci 0000:00:1a.0: setting latency timer to 64
[    0.593683] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    0.593687] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.593702] ehci-pci 0000:00:1a.0: debug port 2
[    0.597604] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    0.597618] ehci-pci 0000:00:1a.0: irq 16, io mem 0xf7c3c000
[    0.607995] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.608007] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.608008] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.608010] usb usb1: Product: EHCI Host Controller
[    0.608011] usb usb1: Manufacturer: Linux 3.11.0-17-generic ehci_hcd
[    0.608012] usb usb1: SerialNumber: 0000:00:1a.0
[    0.608082] hub 1-0:1.0: USB hub found
[    0.608085] hub 1-0:1.0: 2 ports detected
[    0.608215] ehci-pci 0000:00:1d.0: setting latency timer to 64
[    0.608218] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    0.608221] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.608235] ehci-pci 0000:00:1d.0: debug port 2
[    0.612127] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    0.612138] ehci-pci 0000:00:1d.0: irq 23, io mem 0xf7c3b000
[    0.623991] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.623998] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.623999] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.624000] usb usb2: Product: EHCI Host Controller
[    0.624001] usb usb2: Manufacturer: Linux 3.11.0-17-generic ehci_hcd
[    0.624002] usb usb2: SerialNumber: 0000:00:1d.0
[    0.624053] hub 2-0:1.0: USB hub found
[    0.624056] hub 2-0:1.0: 2 ports detected
[    0.624121] ehci-platform: EHCI generic platform driver
[    0.624125] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.624126] ohci-pci: OHCI PCI platform driver
[    0.624132] ohci-platform: OHCI generic platform driver
[    0.624135] uhci_hcd: USB Universal Host Controller Interface driver
[    0.624215] xhci_hcd 0000:00:14.0: setting latency timer to 64
[    0.624218] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.624221] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    0.624313] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.624338] xhci_hcd 0000:00:14.0: irq 42 for MSI/MSI-X
[    0.624367] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    0.624368] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.624369] usb usb3: Product: xHCI Host Controller
[    0.624370] usb usb3: Manufacturer: Linux 3.11.0-17-generic xhci_hcd
[    0.624371] usb usb3: SerialNumber: 0000:00:14.0
[    0.624416] xHCI xhci_add_endpoint called for root hub
[    0.624417] xHCI xhci_check_bandwidth called for root hub
[    0.624428] hub 3-0:1.0: USB hub found
[    0.624447] hub 3-0:1.0: 14 ports detected
[    0.626744] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.626746] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    0.626768] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    0.626769] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.626770] usb usb4: Product: xHCI Host Controller
[    0.626771] usb usb4: Manufacturer: Linux 3.11.0-17-generic xhci_hcd
[    0.626772] usb usb4: SerialNumber: 0000:00:14.0
[    0.626823] xHCI xhci_add_endpoint called for root hub
[    0.626824] xHCI xhci_check_bandwidth called for root hub
[    0.626835] hub 4-0:1.0: USB hub found
[    0.626849] hub 4-0:1.0: 6 ports detected
[    0.632015] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.634321] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.634324] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.634407] mousedev: PS/2 mouse device common for all mice
[    0.634509] rtc_cmos 00:06: RTC can wake from S4
[    0.634625] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.634654] rtc_cmos 00:06: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.634689] device-mapper: uevent: version 1.0.3
[    0.634735] device-mapper: ioctl: 4.25.0-ioctl (2013-06-26) initialised: dm-devel@redhat.com
[    0.634831] cpuidle: using governor ladder
[    0.634968] cpuidle: using governor menu
[    0.634974] ledtrig-cpu: registered to indicate activity on CPUs
[    0.635039] TCP: cubic registered
[    0.635089] NET: Registered protocol family 10
[    0.635203] NET: Registered protocol family 17
[    0.635208] Key type dns_resolver registered
[    0.635402] PM: Hibernation image not present or could not be loaded.
[    0.635405] Loading module verification certificates
[    0.635995] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 2a3861a17986e2fcfa4fcad981cb7e6fd9516274'
[    0.636001] registered taskstats version 1
[    0.637270] Key type trusted registered
[    0.638387] Key type encrypted registered
[    0.639665] AppArmor: AppArmor sha1 policy hashing enabled
[    0.639875]   Magic number: 2:269:29
[    0.639982] rtc_cmos 00:06: setting system clock to 2014-02-26 13:00:05 UTC (1393419605)
[    0.640993] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.640994] EDD information not available.
[    0.641713] Freeing unused kernel memory: 1364K (ffffffff81d10000 - ffffffff81e65000)
[    0.641714] Write protecting the kernel read-only data: 12288k
[    0.643458] Freeing unused kernel memory: 1032K (ffff8800016fe000 - ffff880001800000)
[    0.644691] Freeing unused kernel memory: 784K (ffff880001b3c000 - ffff880001c00000)
[    0.653797] systemd-udevd[146]: starting version 204
[    0.665863] pps_core: LinuxPPS API ver. 1 registered
[    0.665866] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    0.666712] PTP clock support registered
[    0.668076] [drm] Initialized drm 1.1.0 20060810
[    0.670279] e1000e: Intel(R) PRO/1000 Network Driver - 2.3.2-k
[    0.670281] e1000e: Copyright(c) 1999 - 2013 Intel Corporation.
[    0.670473] e1000e 0000:00:19.0: setting latency timer to 64
[    0.670544] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    0.670572] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[    0.919910] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    0.950972] e1000e 0000:00:19.0 eth0: registered PHC clock
[    0.950975] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) 00:22:4d:ae:21:68
[    0.950977] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    0.951023] e1000e 0000:00:19.0 eth0: MAC: 11, PHY: 12, PBA No: FFFFFF-0FF
[    0.951061] ahci 0000:00:1f.2: version 3.0
[    0.951184] ahci 0000:00:1f.2: irq 44 for MSI/MSI-X
[    0.951235] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 5 ports 6 Gbps 0xb impl SATA mode
[    0.951237] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part ems apst 
[    0.951241] ahci 0000:00:1f.2: setting latency timer to 64
[    0.964205] scsi0 : ahci
[    0.964323] scsi1 : ahci
[    0.964716] scsi2 : ahci
[    0.964810] scsi3 : ahci
[    0.964924] scsi4 : ahci
[    0.965002] ata1: SATA max UDMA/133 abar m2048@0xf7c3a000 port 0xf7c3a100 irq 44
[    0.965005] ata2: SATA max UDMA/133 abar m2048@0xf7c3a000 port 0xf7c3a180 irq 44
[    0.965006] ata3: DUMMY
[    0.965008] ata4: SATA max UDMA/133 abar m2048@0xf7c3a000 port 0xf7c3a280 irq 44
[    0.965009] ata5: DUMMY
[    0.965694] [drm] Memory usable by graphics device = 2048M
[    0.965698] i915 0000:00:02.0: setting latency timer to 64
[    0.987404] i915 0000:00:02.0: irq 45 for MSI/MSI-X
[    0.987410] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    0.987410] [drm] Driver supports precise vblank timestamp query.
[    0.987464] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    1.033669] fbcon: inteldrmfb (fb0) is primary device
[    1.052250] usb 1-1: New USB device found, idVendor=8087, idProduct=8008
[    1.052251] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.052394] hub 1-1:1.0: USB hub found
[    1.052490] hub 1-1:1.0: 6 ports detected
[    1.163796] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.239805] Console: switching to colour frame buffer device 128x48
[    1.241267] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    1.241269] i915 0000:00:02.0: registered panic notifier
[    1.245144] acpi device:50: registered as cooling_device13
[    1.245167] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    1.245194] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input2
[    1.245247] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    1.283804] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.283820] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.284677] ata1.00: ATA-8: WDC WD2500AAJS-07M0A0, 01.03E01, max UDMA/133
[    1.284679] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.284978] ata2.00: ATA-8: ST3500413AS, JC4B, max UDMA/133
[    1.284980] ata2.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.286335] ata2.00: configured for UDMA/133
[    1.286404] ata1.00: configured for UDMA/133
[    1.286542] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500AAJS-0 01.0 PQ: 0 ANSI: 5
[    1.286642] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.286666] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.286667] sd 0:0:0:0: [sda] Write Protect is off
[    1.286670] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.286680] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.286827] scsi 1:0:0:0: Direct-Access     ATA      ST3500413AS      JC4B PQ: 0 ANSI: 5
[    1.286938] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    1.286949] sd 1:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.287059] sd 1:0:0:0: [sdb] Write Protect is off
[    1.287061] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.287094] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.287755] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.289684] ata4.00: ATAPI: HL-DT-ST DVDRAM GH24NSB0, LN00, max UDMA/133
[    1.291775] ata4.00: configured for UDMA/133
[    1.296202] usb 2-1: New USB device found, idVendor=8087, idProduct=8000
[    1.296204] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.296440] hub 2-1:1.0: USB hub found
[    1.296533] hub 2-1:1.0: 8 ports detected
[    1.296970] scsi 3:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH24NSB0  LN00 PQ: 0 ANSI: 5
[    1.300360] sr0: scsi3-mmc drive: 48x/12x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.300362] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.300447] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    1.300494] sr 3:0:0:0: Attached scsi generic sg2 type 5
[    1.305313]  sdb: sdb1
[    1.305704] sd 1:0:0:0: [sdb] Attached SCSI disk
[    1.358127]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 >
[    1.358618] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.467731] usb 3-6: new low-speed USB device number 2 using xhci_hcd
[    1.488584] usb 3-6: New USB device found, idVendor=0e8f, idProduct=0022
[    1.488587] usb 3-6: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.488588] usb 3-6: Product: USB KB V11
[    1.488590] usb 3-6: Manufacturer: GASIA
[    1.488655] usb 3-6: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    1.488658] usb 3-6: ep 0x82 - rounding interval to 64 microframes, ep desc says 80 microframes
[    1.491537] hidraw: raw HID events driver (C) Jiri Kosina
[    1.496955] usbcore: registered new interface driver usbhid
[    1.496957] usbhid: USB HID core driver
[    1.497965] input: GASIA USB KB V11 as /devices/pci0000:00/0000:00:14.0/usb3/3-6/3-6:1.0/input/input3
[    1.498035] hid-generic 0003:0E8F:0022.0001: input,hidraw0: USB HID v1.10 Keyboard [GASIA USB KB V11] on usb-0000:00:14.0-6/input0
[    1.498966] input: GASIA USB KB V11 as /devices/pci0000:00/0000:00:14.0/usb3/3-6/3-6:1.1/input/input4
[    1.499031] hid-generic 0003:0E8F:0022.0002: input,hidraw1: USB HID v1.10 Device [GASIA USB KB V11] on usb-0000:00:14.0-6/input1
[    1.567673] tsc: Refined TSC clocksource calibration: 2993.068 MHz
[    1.655668] usb 3-7: new high-speed USB device number 3 using xhci_hcd
[    1.672420] usb 3-7: New USB device found, idVendor=2001, idProduct=7d01
[    1.672423] usb 3-7: New USB device strings: Mfr=9, Product=10, SerialNumber=0
[    1.672424] usb 3-7: Product: D-Link DWM-156
[    1.672425] usb 3-7: Manufacturer: D-Link,Inc  
[    1.675476] usb-storage 3-7:1.6: USB Mass Storage device detected
[    1.675559] scsi5 : usb-storage 3-7:1.6
[    1.675605] usbcore: registered new interface driver usb-storage
[    1.839587] usb 3-8: new low-speed USB device number 4 using xhci_hcd
[    1.859384] usb 3-8: New USB device found, idVendor=04ca, idProduct=0061
[    1.859386] usb 3-8: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.859387] usb 3-8: Product: USB Optical Mouse
[    1.859388] usb 3-8: Manufacturer: PixArt
[    1.859470] usb 3-8: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    1.861234] input: PixArt USB Optical Mouse as /devices/pci0000:00/0000:00:14.0/usb3/3-8/3-8:1.0/input/input5
[    1.861405] hid-generic 0003:04CA:0061.0003: input,hidraw2: USB HID v1.11 Mouse [PixArt USB Optical Mouse] on usb-0000:00:14.0-8/input0
[    2.567362] Switched to clocksource tsc
[    2.671750] scsi 5:0:0:0: Direct-Access     HSPA USB SCSI CD-ROM      6225 PQ: 0 ANSI: 0 CCS
[    2.671959] sd 5:0:0:0: Attached scsi generic sg3 type 0
[    2.672964] sd 5:0:0:0: [sdc] Attached SCSI removable disk
[    2.827325] [drm] Enabling RC6 states: RC6 on, RC6p off, RC6pp off
[    7.033497] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   11.400464] Adding 10238972k swap on /dev/sda7.  Priority:-1 extents:1 across:10238972k FS
[   11.448588] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   11.461978] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   11.489047] systemd-udevd[379]: starting version 204
[   11.554243] mei_me 0000:00:16.0: setting latency timer to 64
[   11.554292] mei_me 0000:00:16.0: irq 46 for MSI/MSI-X
[   11.557438] ACPI Warning: 0x0000000000001828-0x000000000000182f SystemIO conflicts with Region \PMIO 1 (20130517/utaddress-251)
[   11.557444] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   11.557453] ACPI Warning: 0x0000000000001c30-0x0000000000001c3f SystemIO conflicts with Region \GPRL 1 (20130517/utaddress-251)
[   11.557456] ACPI Warning: 0x0000000000001c30-0x0000000000001c3f SystemIO conflicts with Region \GPR_ 2 (20130517/utaddress-251)
[   11.557459] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   11.557461] ACPI Warning: 0x0000000000001c00-0x0000000000001c2f SystemIO conflicts with Region \GPRL 1 (20130517/utaddress-251)
[   11.557463] ACPI Warning: 0x0000000000001c00-0x0000000000001c2f SystemIO conflicts with Region \GPR_ 2 (20130517/utaddress-251)
[   11.557466] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   11.557467] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   11.566485] microcode: CPU0 sig=0x306c3, pf=0x2, revision=0x9
[   11.612372] lp: driver loaded but no devices found
[   11.631516] HDA driver get symbol successfully from i915 module
[   11.631545] snd_hda_intel 0000:00:03.0: irq 47 for MSI/MSI-X
[   11.631639] snd_hda_intel 0000:00:1b.0: irq 48 for MSI/MSI-X
[   11.641975] SKU: Nid=0x1d sku_cfg=0x4016f601
[   11.641977] SKU: port_connectivity=0x1
[   11.641978] SKU: enable_pcbeep=0x1
[   11.641979] SKU: check_sum=0x00000006
[   11.641979] SKU: customization=0x000000f6
[   11.641980] SKU: external_amp=0x0
[   11.641981] SKU: platform_type=0x0
[   11.641981] SKU: swap=0x0
[   11.641982] SKU: override=0x1
[   11.642409] hda_codec: invalid CONNECT_LIST verb 6[1]:0
[   11.642435] autoconfig: line_outs=4 (0x14/0x15/0x16/0x18/0x0) type:line
[   11.642436]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   11.642437]    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[   11.642438]    mono: mono_out=0x0
[   11.642438]    dig-out=0x11/0x1e
[   11.642439]    inputs:
[   11.642440]      Mic=0x19
[   11.642441]      Line=0x1a
[   11.642441] realtek: No valid SSID, checking pincfg 0x4016f601 for NID 0x1d
[   11.642442] realtek: Enabling init ASM_ID=0xf601 CODEC_ID=10ec0892
[   11.642464] hda_codec: invalid CONNECT_LIST verb 7[1]:0
[   11.642665] input: HDA Intel MID HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:03.0/sound/card0/input6
[   11.642722] input: HDA Intel MID HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/sound/card0/input7
[   11.654237] input: HDA Intel PCH Line Out Side as /devices/pci0000:00/0000:00:1b.0/sound/card1/input8
[   11.654275] input: HDA Intel PCH Line Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card1/input9
[   11.654306] input: HDA Intel PCH Line Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card1/input10
[   11.654340] input: HDA Intel PCH Line Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card1/input11
[   11.654371] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card1/input12
[   11.661358] microcode: CPU1 sig=0x306c3, pf=0x2, revision=0x9
[   11.661644] microcode: CPU2 sig=0x306c3, pf=0x2, revision=0x9
[   11.661927] microcode: CPU3 sig=0x306c3, pf=0x2, revision=0x9
[   11.662206] microcode: CPU4 sig=0x306c3, pf=0x2, revision=0x9
[   11.662481] microcode: CPU5 sig=0x306c3, pf=0x2, revision=0x9
[   11.662749] microcode: CPU6 sig=0x306c3, pf=0x2, revision=0x9
[   11.663015] microcode: CPU7 sig=0x306c3, pf=0x2, revision=0x9
[   11.663312] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   11.803256] type=1400 audit(1393419616.660:2): apparmor="STATUS" operation="profile_load" parent=455 profile="unconfined" name="/sbin/dhclient" pid=542 comm="apparmor_parser"
[   11.803262] type=1400 audit(1393419616.660:3): apparmor="STATUS" operation="profile_load" parent=455 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=542 comm="apparmor_parser"
[   11.803266] type=1400 audit(1393419616.660:4): apparmor="STATUS" operation="profile_load" parent=455 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=542 comm="apparmor_parser"
[   11.803272] type=1400 audit(1393419616.660:5): apparmor="STATUS" operation="profile_replace" parent=466 profile="unconfined" name="/sbin/dhclient" pid=543 comm="apparmor_parser"
[   11.803278] type=1400 audit(1393419616.660:6): apparmor="STATUS" operation="profile_replace" parent=466 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=543 comm="apparmor_parser"
[   11.803282] type=1400 audit(1393419616.660:7): apparmor="STATUS" operation="profile_replace" parent=466 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=543 comm="apparmor_parser"
[   11.803801] type=1400 audit(1393419616.660:8): apparmor="STATUS" operation="profile_replace" parent=455 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=542 comm="apparmor_parser"
[   11.803806] type=1400 audit(1393419616.660:9): apparmor="STATUS" operation="profile_replace" parent=455 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=542 comm="apparmor_parser"
[   11.803816] type=1400 audit(1393419616.660:10): apparmor="STATUS" operation="profile_replace" parent=466 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=543 comm="apparmor_parser"
[   11.803820] type=1400 audit(1393419616.660:11): apparmor="STATUS" operation="profile_replace" parent=466 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=543 comm="apparmor_parser"
[   11.897742] usbcore: registered new interface driver usbserial
[   11.897750] usbcore: registered new interface driver usbserial_generic
[   11.897756] usbserial: USB Serial support registered for generic
[   12.081582] usbcore: registered new interface driver cdc_wdm
[   12.111046] usbcore: registered new interface driver cdc_ncm
[   12.151144] usbcore: registered new interface driver option
[   12.151153] usbserial: USB Serial support registered for GSM modem (1-port)
[   12.151222] option 3-7:1.2: GSM modem (1-port) converter detected
[   12.151300] usb 3-7: GSM modem (1-port) converter now attached to ttyUSB0
[   12.151345] option 3-7:1.3: GSM modem (1-port) converter detected
[   12.151411] usb 3-7: GSM modem (1-port) converter now attached to ttyUSB1
[   12.151450] option 3-7:1.4: GSM modem (1-port) converter detected
[   12.151496] usb 3-7: GSM modem (1-port) converter now attached to ttyUSB2
[   12.151529] option 3-7:1.5: GSM modem (1-port) converter detected
[   12.151563] usb 3-7: GSM modem (1-port) converter now attached to ttyUSB3
[   12.162445] cdc_mbim 3-7:1.0: cdc-wdm0: USB WDM device
[   12.162558] cdc_mbim 3-7:1.0 wwan0: register 'cdc_mbim' at usb-0000:00:14.0-7, CDC MBIM, 36:56:70:dd:8f:24
[   12.162573] usbcore: registered new interface driver cdc_mbim
[   12.354257] init: failsafe main process (702) killed by TERM signal
[   12.734684] Bluetooth: Core ver 2.16
[   12.734705] NET: Registered protocol family 31
[   12.734707] Bluetooth: HCI device and connection manager initialized
[   12.734715] Bluetooth: HCI socket layer initialized
[   12.734717] Bluetooth: L2CAP socket layer initialized
[   12.734721] Bluetooth: SCO socket layer initialized
[   12.736496] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   12.736498] Bluetooth: BNEP filters: protocol multicast
[   12.736502] Bluetooth: BNEP socket layer initialized
[   12.737458] Bluetooth: RFCOMM TTY layer initialized
[   12.737464] Bluetooth: RFCOMM socket layer initialized
[   12.737465] Bluetooth: RFCOMM ver 1.11
[   12.925181] ppdev: user-space parallel port driver
[   12.998185] init: avahi-cups-reload main process (864) terminated with status 1
[   14.309790] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[   14.411078] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[   14.411176] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.411365] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   94.325788] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)

  
```

---

### Post by varunendra on 2014-02-26
> **rubankumars said:**
> ```

[   12.151144] usbcore: registered new interface driver option
[   12.151153] usbserial: USB Serial support registered for GSM modem (1-port)
[   12.151222] option 3-7:1.2: GSM modem (1-port) converter detected
[   12.151300] usb 3-7: GSM modem (1-port) converter now attached to ttyUSB0
[   12.151345] option 3-7:1.3: GSM modem (1-port) converter detected
[   12.151411] usb 3-7: GSM modem (1-port) converter now attached to ttyUSB1
[   12.151450] option 3-7:1.4: GSM modem (1-port) converter detected
[   12.151496] usb 3-7: GSM modem (1-port) converter now attached to ttyUSB2
[   12.151529] option 3-7:1.5: GSM modem (1-port) converter detected
[   12.151563] usb 3-7: GSM modem (1-port) converter now attached to ttyUSB3
[   12.162445] cdc_mbim 3-7:1.0: cdc-wdm0: USB WDM device
[   12.162558] cdc_mbim 3-7:1.0 wwan0: register 'cdc_mbim' at usb-0000:00:14.0-7, CDC MBIM, 36:56:70:dd:8f:24
[   12.162573] usbcore: registered new interface driver cdc_mbim
  
```

It seems the device was correctly detected and recognized as a modem by the system. Don't you get a "New Mobile Broadband Connection.." option in Network Manager's drop-down menu (nm-applet in the top-right corner)?

What does this show -
```
ifconfig -a
```

---

### Post by rubankumars on 2014-02-26
```
  eth0      Link encap:Ethernet  HWaddr 00:22:4d:ae:21:68  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:f7c00000-f7c20000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:543 errors:0 dropped:0 overruns:0 frame:0
          TX packets:543 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:45927 (45.9 KB)  TX bytes:45927 (45.9 KB)

wwan0     Link encap:Ethernet  HWaddr ca:e9:a8:35:cb:60  
          BROADCAST NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

  
```

---

### Post by varunendra on 2014-02-26
This looks interesting -
> **rubankumars said:**
> ```

**[COLOR="#006400"]wwan0[/COLOR]**     Link encap:Ethernet  HWaddr ca:e9:a8:35:cb:60  
          BROADCAST NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

  
```

Please show -
```
sed -n '7,$ p' /etc/udev/rules.d/70-persistent-net.rules
```

And you didn't answer my previous question - Do you see any new option in Network Manager's menu when you plug in the modem?

How are you supposed to use that modem? Just plug and use or do you have to save some settings (id, password etc.) to be able to connect? Ask your ISP customer care.

---

### Post by rubankumars on 2014-02-26
Yes,I found the problem.The problem is "you should not install the modem driver which is supplied by manufacturer".
After uninstalling it,the modem showed up in the list.And I connected to internet successfully.Thanks for your help very much.

---

### Post by varunendra on 2014-02-26
Awesome!

And I like what you said :P -
> **rubankumars said:**
> Yes,I found the problem.The problem is "**you should not install the modem driver which is supplied by manufacturer**".
..or **keep it as the Last Option**, when it is confirmed that there are no native drivers available to support it.

The reason is, most often these are outdated drivers meant for older kernels, while linux kernels keep upgrading every month or so. One critical change in the kernel code and the older driver is trash.

Please mark the thread as [SOLVED] using the "Thread Tools" link above the top post to make it useful for others having similar problem.

---

### Post by rubankumars on 2014-02-27
Now the internet is not connecting .It connected in the afternoon.When I connected in evening it is not connecting.What to do? Also,the modem is not showing up in the system.

---

### Post by varunendra on 2014-02-27
Does it show up in lsusb? And what does the dmesg say?

Please post the same outputs as asked before. :)

Also worth checking - Open "Disk Utility" and see if the modem show up as a CDRom device there. If it does, 'Eject' it using Disk Utility and see if Network Manager detects it as modem again.

**PS:**
When the signal/connectivity is not good, it is easy for the modemmanager to get confused and not handle the device properly. In such a case, it usually takes more than one cycles of - unplug > wait 8-10 seconds > replug > wait another 28-30 seconds.

---

