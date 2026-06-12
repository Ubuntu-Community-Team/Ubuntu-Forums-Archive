---
title: "Ubuntu 13.10 Laptop Does not Suspend or Resume"
date: 2013-12-28
forum: Hardware
---

### Post by 7-webmaster on 2013-12-28
I could understand a couple of years ago when my laptop was brand new that Linux might not support it completely, but a couple of years have gone by and the support is getting worse, not better.

Frequently I close the laptop and the system keeps running.  Obviously this means that it quickly runs the battery down, but it also means that the system overheats if I have put it into a backpack or a briefcase without noticing that the system has ignored the fact that it was supposed to shut down!  The following is the dmesg output from such a case:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.11.0-14-generic (buildd@allspice) (gcc version 4.8.1 (Ubuntu/Linaro 4.8.1-10ubuntu8) ) #21-Ubuntu SMP Tue Nov 12 17:04:55 UTC 2013 (Ubuntu 3.11.0-14.21-generic 3.11.7)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-14-generic root=UUID=5850bfca-8269-4a92-8fda-798e6557b0bd ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009d3ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009d400-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000008f5d0fff] usable
[    0.000000] BIOS-e820: [mem 0x000000008f5d1000-0x000000008f619fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000008f61a000-0x000000008f627fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000008f628000-0x000000008f62bfff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000008f62c000-0x000000008f62cfff] usable
[    0.000000] BIOS-e820: [mem 0x000000008f62d000-0x000000008f887fff] reserved
[    0.000000] BIOS-e820: [mem 0x000000008f888000-0x000000008f888fff] usable
[    0.000000] BIOS-e820: [mem 0x000000008f889000-0x000000008f899fff] reserved
[    0.000000] BIOS-e820: [mem 0x000000008f89a000-0x000000008f89ffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000008f8a0000-0x000000008f8a1fff] reserved
[    0.000000] BIOS-e820: [mem 0x000000008f8a2000-0x000000008f8a6fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000008f8a7000-0x000000008f8cafff] reserved
[    0.000000] BIOS-e820: [mem 0x000000008f8cb000-0x000000008facdfff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000008face000-0x000000008fd47fff] usable
[    0.000000] BIOS-e820: [mem 0x000000008fd48000-0x000000008fef3fff] reserved
[    0.000000] BIOS-e820: [mem 0x000000008fef4000-0x000000008fefffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fe800000-0x00000000fe800fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec10000-0x00000000fec10fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed61000-0x00000000fed70fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed80000-0x00000000fed8ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff800000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100001000-0x00000001ceffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: Dell Inc. Vostro 3555/0K89MF, BIOS A04 10/24/2011
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x1cf000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF write-through
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 base 0080000000 mask FFF0000000 write-back
[    0.000000]   2 base 008FF00000 mask FFFFF00000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 00000001cf000000 aka 7408M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 256MB, type WB
[    0.000000] reg 2, base: 2303MB, range: 1MB, type UC
[    0.000000] total RAM covered: 2303M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 2M     num_reg: 3      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 256MB, type WB
[    0.000000] reg 2, base: 2303MB, range: 1MB, type UC
[    0.000000] e820: update [mem 0x8ff00000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0x8ff00 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fd2f0-0x000fd2ff] mapped at [ffff8800000fd2f0]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fd1000, 0x01fd1fff] PGTABLE
[    0.000000] BRK [0x01fd2000, 0x01fd2fff] PGTABLE
[    0.000000] BRK [0x01fd3000, 0x01fd3fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x1cee00000-0x1ceffffff]
[    0.000000]  [mem 0x1cee00000-0x1ceffffff] page 2M
[    0.000000] BRK [0x01fd4000, 0x01fd4fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x1cc000000-0x1cedfffff]
[    0.000000]  [mem 0x1cc000000-0x1cedfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x180000000-0x1cbffffff]
[    0.000000]  [mem 0x180000000-0x1bfffffff] page 1G
[    0.000000]  [mem 0x1c0000000-0x1cbffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0x8f5d0fff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
[    0.000000]  [mem 0x40000000-0x7fffffff] page 1G
[    0.000000]  [mem 0x80000000-0x8f3fffff] page 2M
[    0.000000]  [mem 0x8f400000-0x8f5d0fff] page 4k
[    0.000000] init_memory_mapping: [mem 0x8f62c000-0x8f62cfff]
[    0.000000]  [mem 0x8f62c000-0x8f62cfff] page 4k
[    0.000000] BRK [0x01fd5000, 0x01fd5fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x8f888000-0x8f888fff]
[    0.000000]  [mem 0x8f888000-0x8f888fff] page 4k
[    0.000000] BRK [0x01fd6000, 0x01fd6fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x8face000-0x8fd47fff]
[    0.000000]  [mem 0x8face000-0x8fd47fff] page 4k
[    0.000000] init_memory_mapping: [mem 0x8fef4000-0x8fefffff]
[    0.000000]  [mem 0x8fef4000-0x8fefffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100001000-0x17fffffff]
[    0.000000]  [mem 0x100001000-0x1001fffff] page 4k
[    0.000000]  [mem 0x100200000-0x13fffffff] page 2M
[    0.000000]  [mem 0x140000000-0x17fffffff] page 1G
[    0.000000] RAMDISK: [mem 0x35eea000-0x36f6cfff]
[    0.000000] ACPI: RSDP 00000000000f0440 00024 (v02   DELL)
[    0.000000] ACPI: XSDT 000000008f61a070 00064 (v01 DELL    WN09    01072009 AMI  00010013)
[    0.000000] ACPI: FACP 000000008f6244d8 000F4 (v04   DELL     WN09 01072009 AMI  00010013)
[    0.000000] ACPI BIOS Warning (bug): Optional FADT field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20130517/tbfadt-603)
[    0.000000] ACPI: DSDT 000000008f61a168 0A369 (v02   DELL     WN09 00000015 INTL 20051117)
[    0.000000] ACPI: FACS 000000008f8a2f80 00040
[    0.000000] ACPI: APIC 000000008f6245d0 00072 (v03   DELL     WN09 01072009 AMI  00010013)
[    0.000000] ACPI: MCFG 000000008f624648 0003C (v01 A M I  GMCH945. 01072009 MSFT 00000097)
[    0.000000] ACPI: SLIC 000000008f624688 00176 (v01 DELL    WN09    01072009 AMI  00010013)
[    0.000000] ACPI: HPET 000000008f624800 00038 (v01   DELL     WN09 01072009 AMI  00000004)
[    0.000000] ACPI: SSDT 000000008f624838 00E34 (v01 AMD    POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: SSDT 000000008f625670 0193D (v02    AMD     ALIB 00000001 MSFT 04000000)
[    0.000000] ACPI: OSFR 000000008f626fb0 00086 (v01 DELL    M08     07DB0A18 ASL  00000061)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x00000001ceffffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x1ceffffff]
[    0.000000]   NODE_DATA [mem 0x1ceff4000-0x1ceff8fff]
[    0.000000]  [ffffea0000000000-ffffea00073fffff] PMD -> [ffff8801c8e00000-ffff8801ce5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x1ceffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009cfff]
[    0.000000]   node   0: [mem 0x00100000-0x8f5d0fff]
[    0.000000]   node   0: [mem 0x8f62c000-0x8f62cfff]
[    0.000000]   node   0: [mem 0x8f888000-0x8f888fff]
[    0.000000]   node   0: [mem 0x8face000-0x8fd47fff]
[    0.000000]   node   0: [mem 0x8fef4000-0x8fefffff]
[    0.000000]   node   0: [mem 0x100001000-0x1ceffffff]
[    0.000000] On node 0 totalpages: 1435636
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3996 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 9122 pages used for memmap
[    0.000000]   DMA32 zone: 583769 pages, LIFO batch:31
[    0.000000]   Normal zone: 13248 pages used for memmap
[    0.000000]   Normal zone: 847871 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x05] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 5, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
[    0.000000] smpboot: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009dfff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x8f5d1000-0x8f619fff]
[    0.000000] PM: Registered nosave memory: [mem 0x8f61a000-0x8f627fff]
[    0.000000] PM: Registered nosave memory: [mem 0x8f628000-0x8f62bfff]
[    0.000000] PM: Registered nosave memory: [mem 0x8f62d000-0x8f887fff]
[    0.000000] PM: Registered nosave memory: [mem 0x8f889000-0x8f899fff]
[    0.000000] PM: Registered nosave memory: [mem 0x8f89a000-0x8f89ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x8f8a0000-0x8f8a1fff]
[    0.000000] PM: Registered nosave memory: [mem 0x8f8a2000-0x8f8a6fff]
[    0.000000] PM: Registered nosave memory: [mem 0x8f8a7000-0x8f8cafff]
[    0.000000] PM: Registered nosave memory: [mem 0x8f8cb000-0x8facdfff]
[    0.000000] PM: Registered nosave memory: [mem 0x8fd48000-0x8fef3fff]
[    0.000000] PM: Registered nosave memory: [mem 0x8ff00000-0xdfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfe7fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfe800000-0xfe800fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfe801000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfec0ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec10000-0xfec10fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec11000-0xfecfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfed00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed01000-0xfed60fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed61000-0xfed70fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed71000-0xfed7ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed80000-0xfed8ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed90000-0xff7fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xff800000-0xffffffff]
[    0.000000] PM: Registered nosave memory: [mem 0x100000000-0x100000fff]
[    0.000000] e820: [mem 0x8ff00000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff8801cec00000 s86720 r8192 d23872 u524288
[    0.000000] pcpu-alloc: s86720 r8192 d23872 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1413181
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-14-generic root=UUID=5850bfca-8269-4a92-8fda-798e6557b0bd ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 5552404K/5742544K available (7143K kernel code, 1082K rwdata, 3260K rodata, 1364K init, 1420K bss, 190140K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-255.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 23068672 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 1596.975 MHz processor
[    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 3193.95 BogoMIPS (lpj=6387900)
[    0.000007] pid_max: default: 32768 minimum: 301
[    0.000032] Security Framework initialized
[    0.000052] AppArmor: AppArmor initialized
[    0.000053] Yama: becoming mindful.
[    0.000576] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.003045] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.004427] Mount-cache hash table entries: 256
[    0.004640] Initializing cgroup subsys memory
[    0.004654] Initializing cgroup subsys devices
[    0.004656] Initializing cgroup subsys freezer
[    0.004658] Initializing cgroup subsys blkio
[    0.004659] Initializing cgroup subsys perf_event
[    0.004662] Initializing cgroup subsys hugetlb
[    0.004686] tseg: 008ff00000
[    0.004689] CPU: Physical Processor ID: 0
[    0.004690] CPU: Processor Core ID: 0
[    0.004692] mce: CPU supports 6 MCE banks
[    0.004702] Last level iTLB entries: 4KB 512, 2MB 16, 4MB 8
[    0.004702] Last level dTLB entries: 4KB 1024, 2MB 128, 4MB 64
[    0.004702] tlb_flushall_shift: 5
[    0.004823] Freeing SMP alternatives memory: 28K (ffffffff81e65000 - ffffffff81e6c000)
[    0.007544] ACPI: Core revision 20130517
[    0.012175] ACPI: All ACPI Tables successfully acquired
[    0.042660] ftrace: allocating 27804 entries in 109 pages
[    0.062680] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.102356] smpboot: CPU0: AMD A8-3520M APU with Radeon(tm) HD Graphics (fam: 12, model: 01, stepping: 00)
[    0.208881] Performance Events: AMD PMU driver.
[    0.208886] ... version:                0
[    0.208887] ... bit width:              48
[    0.208888] ... generic registers:      4
[    0.208889] ... value mask:             0000ffffffffffff
[    0.208890] ... max period:             00007fffffffffff
[    0.208891] ... fixed-purpose events:   0
[    0.208892] ... event mask:             000000000000000f
[    0.210747] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.210830] smpboot: Booting Node   0, Processors  #1 #2 #3 OK
[    0.250402] Brought up 4 CPUs
[    0.250404] smpboot: Total of 4 processors activated (12775.80 BogoMIPS)
[    0.251905] devtmpfs: initialized
[    0.253593] EVM: security.selinux
[    0.253594] EVM: security.SMACK64
[    0.253595] EVM: security.capability
[    0.253775] PM: Registering ACPI NVS region [mem 0x8f5d1000-0x8f619fff] (299008 bytes)
[    0.253781] PM: Registering ACPI NVS region [mem 0x8f628000-0x8f62bfff] (16384 bytes)
[    0.253783] PM: Registering ACPI NVS region [mem 0x8f89a000-0x8f89ffff] (24576 bytes)
[    0.253784] PM: Registering ACPI NVS region [mem 0x8f8a2000-0x8f8a6fff] (20480 bytes)
[    0.253786] PM: Registering ACPI NVS region [mem 0x8f8cb000-0x8facdfff] (2109440 bytes)
[    0.255062] regulator-dummy: no parameters
[    0.255142] RTC time: 13:09:38, date: 12/27/13
[    0.255202] NET: Registered protocol family 16
[    0.255566] ACPI: bus type PCI registered
[    0.255568] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.255652] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.255655] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.276670] PCI: Using configuration type 1 for base access
[    0.278136] bio: create slab <bio-0> at 0
[    0.278728] ACPI: Added _OSI(Module Device)
[    0.278735] ACPI: Added _OSI(Processor Device)
[    0.278736] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.278738] ACPI: Added _OSI(Processor Aggregator Device)
[    0.280419] ACPI: EC: Look up EC in DSDT
[    0.282411] ACPI: Executed 2 blocks of module-level executable AML code
[    0.287090] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.291244] ACPI: Interpreter enabled
[    0.291252] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20130517/hwxface-571)
[    0.291259] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20130517/hwxface-571)
[    0.291280] ACPI: (supports S0 S3 S4 S5)
[    0.291283] ACPI: Using IOAPIC for interrupt routing
[    0.291513] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.291686] ACPI: No dock devices found.
[    0.293427] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.293438] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.341362] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.341379] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.341552] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.341571] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.358850] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.359176] acpi PNP0A03:00: Requesting ACPI _OSC control (0x1d)
[    0.359630] acpi PNP0A03:00: ACPI _OSC control (0x19) granted
[    0.360093] PCI host bridge to bus 0000:00
[    0.360098] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.360101] pci_bus 0000:00: root bus resource [io  0x0000-0x03af]
[    0.360104] pci_bus 0000:00: root bus resource [io  0x03e0-0x0cf7]
[    0.360107] pci_bus 0000:00: root bus resource [io  0x03b0-0x03df]
[    0.360110] pci_bus 0000:00: root bus resource [io  0x1778-0xffff]
[    0.360113] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.360116] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000dffff]
[    0.360118] pci_bus 0000:00: root bus resource [mem 0xb0000000-0xffffffff]
[    0.360131] pci 0000:00:00.0: [1022:1705] type 00 class 0x060000
[    0.360259] pci 0000:00:01.0: [1002:9641] type 00 class 0x030000
[    0.360272] pci 0000:00:01.0: reg 0x10: [mem 0xb0000000-0xbfffffff pref]
[    0.360281] pci 0000:00:01.0: reg 0x14: [io  0xf000-0xf0ff]
[    0.360289] pci 0000:00:01.0: reg 0x18: [mem 0xff700000-0xff73ffff]
[    0.360343] pci 0000:00:01.0: supports D1 D2
[    0.360411] pci 0000:00:01.1: [1002:1714] type 00 class 0x040300
[    0.360420] pci 0000:00:01.1: reg 0x10: [mem 0xff744000-0xff747fff]
[    0.360474] pci 0000:00:01.1: supports D1 D2
[    0.360547] pci 0000:00:04.0: [1022:1709] type 01 class 0x060400
[    0.360606] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    0.360680] pci 0000:00:04.0: System wakeup disabled by ACPI
[    0.360772] pci 0000:00:06.0: [1022:170b] type 01 class 0x060400
[    0.360843] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.361026] pci 0000:00:10.0: [1022:7812] type 00 class 0x0c0330
[    0.361051] pci 0000:00:10.0: reg 0x10: [mem 0xff74a000-0xff74bfff 64bit]
[    0.361174] pci 0000:00:10.0: PME# supported from D0 D3hot D3cold
[    0.361254] pci 0000:00:10.0: System wakeup disabled by ACPI
[    0.361360] pci 0000:00:10.1: [1022:7812] type 00 class 0x0c0330
[    0.361382] pci 0000:00:10.1: reg 0x10: [mem 0xff748000-0xff749fff 64bit]
[    0.361497] pci 0000:00:10.1: PME# supported from D0 D3hot D3cold
[    0.361556] pci 0000:00:10.1: System wakeup disabled by ACPI
[    0.361616] pci 0000:00:11.0: [1022:7804] type 00 class 0x010601
[    0.361637] pci 0000:00:11.0: reg 0x10: [io  0xf190-0xf197]
[    0.361647] pci 0000:00:11.0: reg 0x14: [io  0xf180-0xf183]
[    0.361658] pci 0000:00:11.0: reg 0x18: [io  0xf170-0xf177]
[    0.361668] pci 0000:00:11.0: reg 0x1c: [io  0xf160-0xf163]
[    0.361679] pci 0000:00:11.0: reg 0x20: [io  0xf150-0xf15f]
[    0.361690] pci 0000:00:11.0: reg 0x24: [mem 0xff752000-0xff7527ff]
[    0.361850] pci 0000:00:12.0: [1022:7807] type 00 class 0x0c0310
[    0.361867] pci 0000:00:12.0: reg 0x10: [mem 0xff751000-0xff751fff]
[    0.362007] pci 0000:00:12.0: System wakeup disabled by ACPI
[    0.362104] pci 0000:00:12.2: [1022:7808] type 00 class 0x0c0320
[    0.362127] pci 0000:00:12.2: reg 0x10: [mem 0xff750000-0xff7500ff]
[    0.362226] pci 0000:00:12.2: supports D1 D2
[    0.362229] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.362310] pci 0000:00:12.2: System wakeup disabled by ACPI
[    0.362407] pci 0000:00:13.0: [1022:7807] type 00 class 0x0c0310
[    0.362423] pci 0000:00:13.0: reg 0x10: [mem 0xff74f000-0xff74ffff]
[    0.362535] pci 0000:00:13.0: System wakeup disabled by ACPI
[    0.362598] pci 0000:00:13.2: [1022:7808] type 00 class 0x0c0320
[    0.362619] pci 0000:00:13.2: reg 0x10: [mem 0xff74e000-0xff74e0ff]
[    0.362711] pci 0000:00:13.2: supports D1 D2
[    0.362712] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.362776] pci 0000:00:13.2: System wakeup disabled by ACPI
[    0.362828] pci 0000:00:14.0: [1022:780b] type 00 class 0x0c0500
[    0.363042] pci 0000:00:14.1: [1022:780c] type 00 class 0x01018a
[    0.363059] pci 0000:00:14.1: reg 0x10: [io  0xf140-0xf147]
[    0.363071] pci 0000:00:14.1: reg 0x14: [io  0xf130-0xf133]
[    0.363083] pci 0000:00:14.1: reg 0x18: [io  0xf120-0xf127]
[    0.363095] pci 0000:00:14.1: reg 0x1c: [io  0xf110-0xf113]
[    0.363107] pci 0000:00:14.1: reg 0x20: [io  0xf100-0xf10f]
[    0.363278] pci 0000:00:14.2: [1022:780d] type 00 class 0x040300
[    0.363305] pci 0000:00:14.2: reg 0x10: [mem 0xff740000-0xff743fff 64bit]
[    0.363384] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.363453] pci 0000:00:14.2: System wakeup disabled by ACPI
[    0.363494] pci 0000:00:14.3: [1022:780e] type 00 class 0x060100
[    0.363635] pci 0000:00:14.4: [1022:780f] type 01 class 0x060401
[    0.363714] pci 0000:00:14.4: System wakeup disabled by ACPI
[    0.363758] pci 0000:00:14.5: [1022:7809] type 00 class 0x0c0310
[    0.363773] pci 0000:00:14.5: reg 0x10: [mem 0xff74d000-0xff74dfff]
[    0.363977] pci 0000:00:14.7: [1022:7806] type 00 class 0x080501
[    0.364000] pci 0000:00:14.7: reg 0x10: [mem 0xff74c000-0xff74c0ff 64bit]
[    0.364196] pci 0000:00:15.0: [1022:43a0] type 01 class 0x060400
[    0.364291] pci 0000:00:15.0: supports D1 D2
[    0.364365] pci 0000:00:15.0: System wakeup disabled by ACPI
[    0.364457] pci 0000:00:15.1: [1022:43a1] type 01 class 0x060400
[    0.364550] pci 0000:00:15.1: supports D1 D2
[    0.364605] pci 0000:00:15.1: System wakeup disabled by ACPI
[    0.364643] pci 0000:00:18.0: [1022:1700] type 00 class 0x060000
[    0.364729] pci 0000:00:18.1: [1022:1701] type 00 class 0x060000
[    0.364837] pci 0000:00:18.2: [1022:1702] type 00 class 0x060000
[    0.364950] pci 0000:00:18.3: [1022:1703] type 00 class 0x060000
[    0.365072] pci 0000:00:18.4: [1022:1704] type 00 class 0x060000
[    0.365183] pci 0000:00:18.5: [1022:1718] type 00 class 0x060000
[    0.365294] pci 0000:00:18.6: [1022:1716] type 00 class 0x060000
[    0.365406] pci 0000:00:18.7: [1022:1719] type 00 class 0x060000
[    0.365600] pci 0000:01:00.0: [10ec:8168] type 00 class 0x020000
[    0.365617] pci 0000:01:00.0: reg 0x10: [io  0xe000-0xe0ff]
[    0.365645] pci 0000:01:00.0: reg 0x18: [mem 0xd0004000-0xd0004fff 64bit pref]
[    0.365663] pci 0000:01:00.0: reg 0x20: [mem 0xd0000000-0xd0003fff 64bit pref]
[    0.365732] pci 0000:01:00.0: supports D1 D2
[    0.365733] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.373031] pci 0000:00:04.0: PCI bridge to [bus 01]
[    0.373051] pci 0000:00:04.0:   bridge window [io  0xe000-0xefff]
[    0.373065] pci 0000:00:04.0:   bridge window [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.373195] pci 0000:02:00.0: [14e4:4727] type 00 class 0x028000
[    0.373219] pci 0000:02:00.0: reg 0x10: [mem 0xff600000-0xff603fff 64bit]
[    0.373329] pci 0000:02:00.0: supports D1 D2
[    0.373331] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    0.381045] pci 0000:00:06.0: PCI bridge to [bus 02]
[    0.381066] pci 0000:00:06.0:   bridge window [mem 0xff600000-0xff6fffff]
[    0.381224] pci 0000:00:14.4: PCI bridge to [bus 03] (subtractive decode)
[    0.381234] pci 0000:00:14.4:   bridge window [io  0x0000-0x03af] (subtractive decode)
[    0.381236] pci 0000:00:14.4:   bridge window [io  0x03e0-0x0cf7] (subtractive decode)
[    0.381238] pci 0000:00:14.4:   bridge window [io  0x03b0-0x03df] (subtractive decode)
[    0.381240] pci 0000:00:14.4:   bridge window [io  0x1778-0xffff] (subtractive decode)
[    0.381242] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.381244] pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
[    0.381246] pci 0000:00:14.4:   bridge window [mem 0xb0000000-0xffffffff] (subtractive decode)
[    0.381323] pci 0000:00:15.0: PCI bridge to [bus 04]
[    0.381401] pci 0000:00:15.1: PCI bridge to [bus 05-07]
[    0.381407] pci 0000:00:15.1:   bridge window [io  0xd000-0xdfff]
[    0.381411] pci 0000:00:15.1:   bridge window [mem 0xff500000-0xff5fffff]
[    0.381418] pci 0000:00:15.1:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.385916] ACPI: PCI Interrupt Link [LN24] (IRQs *24)
[    0.385948] ACPI: PCI Interrupt Link [LN25] (IRQs *25)
[    0.385992] ACPI: PCI Interrupt Link [LN26] (IRQs *26)
[    0.386039] ACPI: PCI Interrupt Link [LN27] (IRQs *27)
[    0.386085] ACPI: PCI Interrupt Link [LN28] (IRQs *28)
[    0.386132] ACPI: PCI Interrupt Link [LN29] (IRQs *29)
[    0.386178] ACPI: PCI Interrupt Link [LN30] (IRQs *30)
[    0.386225] ACPI: PCI Interrupt Link [LN31] (IRQs *31)
[    0.386272] ACPI: PCI Interrupt Link [LN32] (IRQs *32)
[    0.386318] ACPI: PCI Interrupt Link [LN33] (IRQs *33)
[    0.386365] ACPI: PCI Interrupt Link [LN34] (IRQs *34)
[    0.386411] ACPI: PCI Interrupt Link [LN35] (IRQs *35)
[    0.386458] ACPI: PCI Interrupt Link [LN36] (IRQs *36)
[    0.386504] ACPI: PCI Interrupt Link [LN37] (IRQs *37)
[    0.386551] ACPI: PCI Interrupt Link [LN38] (IRQs *38)
[    0.386598] ACPI: PCI Interrupt Link [LN39] (IRQs *39)
[    0.386645] ACPI: PCI Interrupt Link [LN40] (IRQs *40)
[    0.386691] ACPI: PCI Interrupt Link [LN41] (IRQs *41)
[    0.386738] ACPI: PCI Interrupt Link [LN42] (IRQs *42)
[    0.386785] ACPI: PCI Interrupt Link [LN43] (IRQs *43)
[    0.386831] ACPI: PCI Interrupt Link [LN44] (IRQs *44)
[    0.386877] ACPI: PCI Interrupt Link [LN45] (IRQs *45)
[    0.386924] ACPI: PCI Interrupt Link [LN46] (IRQs *46)
[    0.386971] ACPI: PCI Interrupt Link [LN47] (IRQs *47)
[    0.387017] ACPI: PCI Interrupt Link [LN48] (IRQs *48)
[    0.387063] ACPI: PCI Interrupt Link [LN49] (IRQs *49)
[    0.387115] ACPI: PCI Interrupt Link [LN50] (IRQs *50)
[    0.387162] ACPI: PCI Interrupt Link [LN51] (IRQs *51)
[    0.387208] ACPI: PCI Interrupt Link [LN52] (IRQs *52)
[    0.387252] ACPI: PCI Interrupt Link [LN53] (IRQs *53)
[    0.387282] ACPI: PCI Interrupt Link [LN54] (IRQs *54)
[    0.387312] ACPI: PCI Interrupt Link [LN55] (IRQs *55)
[    0.387412] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 5 7 10 11 14 15) *0
[    0.387480] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 5 7 10 11 14 15) *0
[    0.387570] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 5 7 10 11 14 15) *0
[    0.387661] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 5 7 10 11 14 15) *0
[    0.387736] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 5 7 10 11 14 15) *0
[    0.387798] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 5 7 10 11 14 15) *0
[    0.387860] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 5 7 10 11 14 15) *0
[    0.387923] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 5 7 10 11 14 15) *0
[    0.388331] ACPI: Enabled 3 GPEs in block 00 to 1F
[    0.388341] ACPI: \_SB_.PCI0: notify handler is installed
[    0.388437] Found 1 acpi root devices
[    0.388660] vgaarb: device added: PCI:0000:00:01.0,decodes=io+mem,owns=io+mem,locks=none
[    0.388670] vgaarb: loaded
[    0.388672] vgaarb: bridge control possible 0000:00:01.0
[    0.388879] SCSI subsystem initialized
[    0.388882] ACPI: bus type ATA registered
[    0.389017] libata version 3.00 loaded.
[    0.389040] ACPI: bus type USB registered
[    0.389063] usbcore: registered new interface driver usbfs
[    0.389075] usbcore: registered new interface driver hub
[    0.389191] usbcore: registered new device driver usb
[    0.389464] PCI: Using ACPI for IRQ routing
[    0.399154] PCI: pci_cache_line_size set to 64 bytes
[    0.399256] e820: reserve RAM buffer [mem 0x0009d400-0x0009ffff]
[    0.399258] e820: reserve RAM buffer [mem 0x8f5d1000-0x8fffffff]
[    0.399260] e820: reserve RAM buffer [mem 0x8f62d000-0x8fffffff]
[    0.399262] e820: reserve RAM buffer [mem 0x8f889000-0x8fffffff]
[    0.399264] e820: reserve RAM buffer [mem 0x8fd48000-0x8fffffff]
[    0.399265] e820: reserve RAM buffer [mem 0x8ff00000-0x8fffffff]
[    0.399267] e820: reserve RAM buffer [mem 0x1cf000000-0x1cfffffff]
[    0.399413] NetLabel: Initializing
[    0.399415] NetLabel:  domain hash size = 128
[    0.399416] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.399431] NetLabel:  unlabeled traffic allowed by default
[    0.399631] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.399639] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    0.401749] Switched to clocksource hpet
[    0.408437] AppArmor: AppArmor Filesystem Enabled
[    0.408484] pnp: PnP ACPI init
[    0.408503] ACPI: bus type PNP registered
[    0.408653] system 00:00: [mem 0xe0000000-0xefffffff] has been reserved
[    0.408657] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.409471] system 00:01: [io  0x04d0-0x04d1] has been reserved
[    0.409475] system 00:01: [io  0x040b] has been reserved
[    0.409478] system 00:01: [io  0x04d6] has been reserved
[    0.409482] system 00:01: [io  0x0c00-0x0c01] has been reserved
[    0.409485] system 00:01: [io  0x0c14] has been reserved
[    0.409488] system 00:01: [io  0x0c50-0x0c51] has been reserved
[    0.409491] system 00:01: [io  0x0c52] has been reserved
[    0.409495] system 00:01: [io  0x0c6c] has been reserved
[    0.409498] system 00:01: [io  0x0c6f] has been reserved
[    0.409501] system 00:01: [io  0x0cd0-0x0cd1] has been reserved
[    0.409504] system 00:01: [io  0x0cd2-0x0cd3] has been reserved
[    0.409508] system 00:01: [io  0x0cd4-0x0cd5] has been reserved
[    0.409511] system 00:01: [io  0x0cd6-0x0cd7] has been reserved
[    0.409517] system 00:01: [io  0x0cd8-0x0cdf] has been reserved
[    0.409520] system 00:01: [io  0x0800-0x089f] could not be reserved
[    0.409524] system 00:01: [io  0x0b20-0x0b3f] has been reserved
[    0.409528] system 00:01: [io  0x0900-0x090f] has been reserved
[    0.409531] system 00:01: [io  0x0910-0x091f] has been reserved
[    0.409535] system 00:01: [io  0xfe00-0xfefe] has been reserved
[    0.409539] system 00:01: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.409543] system 00:01: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.409546] system 00:01: [mem 0xfed80000-0xfed8ffff] has been reserved
[    0.409550] system 00:01: [mem 0xfed61000-0xfed70fff] has been reserved
[    0.409554] system 00:01: [mem 0xfec10000-0xfec10fff] has been reserved
[    0.409557] system 00:01: [mem 0xfed00000-0xfed00fff] has been reserved
[    0.409561] system 00:01: [mem 0xff800000-0xffffffff] has been reserved
[    0.409565] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.409582] pnp 00:02: [dma 4]
[    0.409606] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.409649] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.409679] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.409776] system 00:05: [io  0x04d0-0x04d1] has been reserved
[    0.409780] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.409817] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.409876] system 00:07: [io  0x1770-0x1777] has been reserved
[    0.409879] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.409950] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.409974] pnp 00:09: Plug and Play ACPI device, IDs DLL0513 SYN0002 SYN0600 SYN0602 PNP0f13 (active)
[    0.410012] system 00:0a: [mem 0xff800000-0xff801fff] has been reserved
[    0.410014] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.410172] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.414599] pnp 00:0c: Plug and Play ACPI device, IDs SMO8800 (active)
[    0.415091] pnp 00:0d: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.415096] pnp: PnP ACPI: found 14 devices
[    0.415098] ACPI: bus type PNP unregistered
[    0.423110] pci 0000:00:04.0: PCI bridge to [bus 01]
[    0.423118] pci 0000:00:04.0:   bridge window [io  0xe000-0xefff]
[    0.423126] pci 0000:00:04.0:   bridge window [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.423132] pci 0000:00:06.0: PCI bridge to [bus 02]
[    0.423137] pci 0000:00:06.0:   bridge window [mem 0xff600000-0xff6fffff]
[    0.423145] pci 0000:00:14.4: PCI bridge to [bus 03]
[    0.423206] pci 0000:00:15.0: PCI bridge to [bus 04]
[    0.423219] pci 0000:00:15.1: PCI bridge to [bus 05-07]
[    0.423223] pci 0000:00:15.1:   bridge window [io  0xd000-0xdfff]
[    0.423229] pci 0000:00:15.1:   bridge window [mem 0xff500000-0xff5fffff]
[    0.423235] pci 0000:00:15.1:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.423625] pci 0000:00:15.1: enabling device (0006 -> 0007)
[    0.423746] pci_bus 0000:00: resource 4 [io  0x0000-0x03af]
[    0.423748] pci_bus 0000:00: resource 5 [io  0x03e0-0x0cf7]
[    0.423750] pci_bus 0000:00: resource 6 [io  0x03b0-0x03df]
[    0.423752] pci_bus 0000:00: resource 7 [io  0x1778-0xffff]
[    0.423754] pci_bus 0000:00: resource 8 [mem 0x000a0000-0x000bffff]
[    0.423756] pci_bus 0000:00: resource 9 [mem 0x000c0000-0x000dffff]
[    0.423758] pci_bus 0000:00: resource 10 [mem 0xb0000000-0xffffffff]
[    0.423760] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.423762] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.423765] pci_bus 0000:02: resource 1 [mem 0xff600000-0xff6fffff]
[    0.423767] pci_bus 0000:03: resource 4 [io  0x0000-0x03af]
[    0.423769] pci_bus 0000:03: resource 5 [io  0x03e0-0x0cf7]
[    0.423771] pci_bus 0000:03: resource 6 [io  0x03b0-0x03df]
[    0.423772] pci_bus 0000:03: resource 7 [io  0x1778-0xffff]
[    0.423778] pci_bus 0000:03: resource 8 [mem 0x000a0000-0x000bffff]
[    0.423781] pci_bus 0000:03: resource 9 [mem 0x000c0000-0x000dffff]
[    0.423784] pci_bus 0000:03: resource 10 [mem 0xb0000000-0xffffffff]
[    0.423787] pci_bus 0000:05: resource 0 [io  0xd000-0xdfff]
[    0.423790] pci_bus 0000:05: resource 1 [mem 0xff500000-0xff5fffff]
[    0.423793] pci_bus 0000:05: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.423844] NET: Registered protocol family 2
[    0.424122] TCP established hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.424607] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.425023] TCP: Hash tables configured (established 65536 bind 65536)
[    0.425082] TCP: reno registered
[    0.425095] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.425157] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.425316] NET: Registered protocol family 1
[    0.425338] pci 0000:00:01.0: Boot video device
[    1.213915] PCI: CLS 64 bytes, default 64
[    1.213975] Trying to unpack rootfs image as initramfs...
[    1.583535] Freeing initrd memory: 16908K (ffff880035eea000 - ffff880036f6d000)
[    1.583543] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.583546] software IO TLB [mem 0x8b5d1000-0x8f5d1000] (64MB) mapped at [ffff88008b5d1000-ffff88008f5d0fff]
[    1.583886] LVT offset 0 assigned for vector 0x400
[    1.583952] perf: AMD IBS detected (0x000000ff)
[    1.583993] Scanning for low memory corruption every 60 seconds
[    1.584463] Initialise module verification
[    1.584511] audit: initializing netlink socket (disabled)
[    1.584525] type=2000 audit(1388149778.444:1): initialized
[    1.621040] bounce pool size: 64 pages
[    1.621055] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.623026] zbud: loaded
[    1.623376] VFS: Disk quotas dquot_6.5.2
[    1.623443] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.624418] fuse init (API version 7.22)
[    1.624696] msgmni has been set to 10877
[    1.625827] Key type asymmetric registered
[    1.625833] Asymmetric key parser 'x509' registered
[    1.625906] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.626002] io scheduler noop registered
[    1.626005] io scheduler deadline registered (default)
[    1.626027] io scheduler cfq registered
[    1.626301] pcieport 0000:00:15.1: irq 40 for MSI/MSI-X
[    1.626385] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.626413] pciehp 0000:00:15.1:pcie04: HPC vendor_id 1022 device_id 43a1 ss_vid 1022 ss_did 0
[    1.626469] pciehp 0000:00:15.1:pcie04: service driver pciehp loaded
[    1.626473] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.626625] ACPI: AC Adapter [AC] (on-line)
[    1.626690] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.626695] ACPI: Power Button [PWRB]
[    1.626768] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    1.627988] ACPI: Lid Switch [LID]
[    1.628019] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.628022] ACPI: Sleep Button [SBTN]
[    1.628048] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    1.628050] ACPI: Power Button [PWRF]
[    1.628211] ACPI: acpi_idle registered with cpuidle
[    1.645821] thermal LNXTHERM:00: registered as thermal_zone0
[    1.645828] ACPI: Thermal Zone [THM] (64 C)
[    1.645867] GHES: HEST is not enabled!
[    1.646115] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.670026] Linux agpgart interface v0.103
[    1.672982] brd: module loaded
[    1.674010] loop: module loaded
[    1.674347] libphy: Fixed MDIO Bus: probed
[    1.674419] tun: Universal TUN/TAP device driver, 1.6
[    1.674421] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.674544] PPP generic driver version 2.4.2
[    1.674606] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.674608] ehci-pci: EHCI PCI platform driver
[    1.674810] ehci-pci 0000:00:12.2: EHCI Host Controller
[    1.674816] ehci-pci 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.674827] QUIRK: Enable AMD PLL fix
[    1.674829] ehci-pci 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.674842] ehci-pci 0000:00:12.2: debug port 1
[    1.674885] ehci-pci 0000:00:12.2: irq 17, io mem 0xff750000
[    1.685678] ehci-pci 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.685730] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.685732] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.685735] usb usb1: Product: EHCI Host Controller
[    1.685736] usb usb1: Manufacturer: Linux 3.11.0-14-generic ehci_hcd
[    1.685738] usb usb1: SerialNumber: 0000:00:12.2
[    1.698358] hub 1-0:1.0: USB hub found
[    1.698366] hub 1-0:1.0: 5 ports detected
[    1.698742] ehci-pci 0000:00:13.2: EHCI Host Controller
[    1.698749] ehci-pci 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.698753] ehci-pci 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.698766] ehci-pci 0000:00:13.2: debug port 1
[    1.698797] ehci-pci 0000:00:13.2: irq 17, io mem 0xff74e000
[    1.702062] ACPI: Battery Slot [BAT0] (battery present)
[    1.709669] ehci-pci 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.709708] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.709711] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.709714] usb usb2: Product: EHCI Host Controller
[    1.709719] usb usb2: Manufacturer: Linux 3.11.0-14-generic ehci_hcd
[    1.709721] usb usb2: SerialNumber: 0000:00:13.2
[    1.710061] hub 2-0:1.0: USB hub found
[    1.710070] hub 2-0:1.0: 5 ports detected
[    1.710279] ehci-platform: EHCI generic platform driver
[    1.710291] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.710292] ohci-platform: OHCI generic platform driver
[    1.710297] uhci_hcd: USB Universal Host Controller Interface driver
[    1.710543] xhci_hcd 0000:00:10.0: xHCI Host Controller
[    1.710549] xhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 3
[    1.710770] xhci_hcd 0000:00:10.0: irq 41 for MSI/MSI-X
[    1.710777] xhci_hcd 0000:00:10.0: irq 42 for MSI/MSI-X
[    1.710783] xhci_hcd 0000:00:10.0: irq 43 for MSI/MSI-X
[    1.710789] xhci_hcd 0000:00:10.0: irq 44 for MSI/MSI-X
[    1.710795] xhci_hcd 0000:00:10.0: irq 45 for MSI/MSI-X
[    1.710885] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    1.710887] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.710889] usb usb3: Product: xHCI Host Controller
[    1.710891] usb usb3: Manufacturer: Linux 3.11.0-14-generic xhci_hcd
[    1.710892] usb usb3: SerialNumber: 0000:00:10.0
[    1.711137] xHCI xhci_add_endpoint called for root hub
[    1.711141] xHCI xhci_check_bandwidth called for root hub
[    1.711169] hub 3-0:1.0: USB hub found
[    1.711221] hub 3-0:1.0: 2 ports detected
[    1.711288] xhci_hcd 0000:00:10.0: xHCI Host Controller
[    1.711291] xhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 4
[    1.714156] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    1.714157] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.714159] usb usb4: Product: xHCI Host Controller
[    1.714161] usb usb4: Manufacturer: Linux 3.11.0-14-generic xhci_hcd
[    1.714162] usb usb4: SerialNumber: 0000:00:10.0
[    1.714408] xHCI xhci_add_endpoint called for root hub
[    1.714412] xHCI xhci_check_bandwidth called for root hub
[    1.714443] hub 4-0:1.0: USB hub found
[    1.714497] hub 4-0:1.0: 2 ports detected
[    1.721989] xhci_hcd 0000:00:10.1: xHCI Host Controller
[    1.722000] xhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 5
[    1.722232] xhci_hcd 0000:00:10.1: irq 46 for MSI/MSI-X
[    1.722239] xhci_hcd 0000:00:10.1: irq 47 for MSI/MSI-X
[    1.722246] xhci_hcd 0000:00:10.1: irq 48 for MSI/MSI-X
[    1.722252] xhci_hcd 0000:00:10.1: irq 49 for MSI/MSI-X
[    1.722258] xhci_hcd 0000:00:10.1: irq 50 for MSI/MSI-X
[    1.722359] usb usb5: New USB device found, idVendor=1d6b, idProduct=0002
[    1.722361] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.722363] usb usb5: Product: xHCI Host Controller
[    1.722365] usb usb5: Manufacturer: Linux 3.11.0-14-generic xhci_hcd
[    1.722366] usb usb5: SerialNumber: 0000:00:10.1
[    1.722649] xHCI xhci_add_endpoint called for root hub
[    1.722653] xHCI xhci_check_bandwidth called for root hub
[    1.722686] hub 5-0:1.0: USB hub found
[    1.722739] hub 5-0:1.0: 2 ports detected
[    1.722812] xhci_hcd 0000:00:10.1: xHCI Host Controller
[    1.722816] xhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 6
[    1.725612] usb usb6: New USB device found, idVendor=1d6b, idProduct=0003
[    1.725614] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.725616] usb usb6: Product: xHCI Host Controller
[    1.725618] usb usb6: Manufacturer: Linux 3.11.0-14-generic xhci_hcd
[    1.725619] usb usb6: SerialNumber: 0000:00:10.1
[    1.725874] xHCI xhci_add_endpoint called for root hub
[    1.725878] xHCI xhci_check_bandwidth called for root hub
[    1.725909] hub 6-0:1.0: USB hub found
[    1.725962] hub 6-0:1.0: 2 ports detected
[    1.733945] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.737298] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.737310] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.737758] mousedev: PS/2 mouse device common for all mice
[    1.738650] rtc_cmos 00:03: RTC can wake from S4
[    1.738774] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.738802] rtc_cmos 00:03: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.738866] device-mapper: uevent: version 1.0.3
[    1.738980] device-mapper: ioctl: 4.25.0-ioctl (2013-06-26) initialised: dm-devel@redhat.com
[    1.739027] cpuidle: using governor ladder
[    1.739138] cpuidle: using governor menu
[    1.739150] ledtrig-cpu: registered to indicate activity on CPUs
[    1.739234] TCP: cubic registered
[    1.739313] NET: Registered protocol family 10
[    1.739495] NET: Registered protocol family 17
[    1.739504] Key type dns_resolver registered
[    1.739895] PM: Hibernation image not present or could not be loaded.
[    1.739900] Loading module verification certificates
[    1.741020] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 4f57df1a3429640d83ffde722907e1377213486f'
[    1.741034] registered taskstats version 1
[    1.744377] Key type trusted registered
[    1.746912] Key type encrypted registered
[    1.749157] AppArmor: AppArmor sha1 policy hashing enabled
[    1.749732]   Magic number: 9:62:181
[    1.749888] rtc_cmos 00:03: setting system clock to 2013-12-27 13:09:39 UTC (1388149779)
[    1.750047] acpi-cpufreq: overriding BIOS provided _PSD data
[    1.750438] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.750440] EDD information not available.
[    1.752047] Freeing unused kernel memory: 1364K (ffffffff81d10000 - ffffffff81e65000)
[    1.752053] Write protecting the kernel read-only data: 12288k
[    1.755646] Freeing unused kernel memory: 1036K (ffff8800016fd000 - ffff880001800000)
[    1.758369] Freeing unused kernel memory: 836K (ffff880001b2f000 - ffff880001c00000)
[    1.758432] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.776928] systemd-udevd[112]: starting version 204
[    1.805313] mii: module verification failed: signature and/or required key missing - tainting kernel
[    1.806853] ahci 0000:00:11.0: version 3.0
[    1.807115] ahci 0000:00:11.0: irq 51 for MSI/MSI-X
[    1.807186] ahci 0000:00:11.0: AHCI 0001.0300 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[    1.807190] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part sxs 
[    1.807795] scsi0 : ahci
[    1.807981] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.808322] r8169 0000:01:00.0: irq 52 for MSI/MSI-X
[    1.808393] scsi1 : ahci
[    1.808503] r8169 0000:01:00.0 eth0: RTL8168e/8111e at 0xffffc90000c72000, 24:b6:fd:25:7e:39, XID 0c200000 IRQ 52
[    1.808508] r8169 0000:01:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    1.808521] scsi2 : ahci
[    1.808702] ata1: SATA max UDMA/133 abar m2048@0xff752000 port 0xff752100 irq 51
[    1.808706] ata2: SATA max UDMA/133 abar m2048@0xff752000 port 0xff752180 irq 51
[    1.808710] ata3: SATA max UDMA/133 abar m2048@0xff752000 port 0xff752200 irq 51
[    1.809799] ohci-pci: OHCI PCI platform driver
[    1.809963] ohci-pci 0000:00:12.0: OHCI PCI host controller
[    1.809970] ohci-pci 0000:00:12.0: new USB bus registered, assigned bus number 7
[    1.810001] ohci-pci 0000:00:12.0: irq 18, io mem 0xff751000
[    1.813094] sdhci: Secure Digital Host Controller Interface driver
[    1.813098] sdhci: Copyright(c) Pierre Ossman
[    1.869655] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    1.869661] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.869663] usb usb7: Product: OHCI PCI host controller
[    1.869665] usb usb7: Manufacturer: Linux 3.11.0-14-generic ohci_hcd
[    1.869666] usb usb7: SerialNumber: 0000:00:12.0
[    1.870062] hub 7-0:1.0: USB hub found
[    1.870072] hub 7-0:1.0: 5 ports detected
[    1.870412] ohci-pci 0000:00:13.0: OHCI PCI host controller
[    1.870417] ohci-pci 0000:00:13.0: new USB bus registered, assigned bus number 8
[    1.870435] ohci-pci 0000:00:13.0: irq 18, io mem 0xff74f000
[    1.929650] usb usb8: New USB device found, idVendor=1d6b, idProduct=0001
[    1.929656] usb usb8: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.929658] usb usb8: Product: OHCI PCI host controller
[    1.929659] usb usb8: Manufacturer: Linux 3.11.0-14-generic ohci_hcd
[    1.929661] usb usb8: SerialNumber: 0000:00:13.0
[    1.930047] hub 8-0:1.0: USB hub found
[    1.930057] hub 8-0:1.0: 5 ports detected
[    1.930401] ohci-pci 0000:00:14.5: OHCI PCI host controller
[    1.930407] ohci-pci 0000:00:14.5: new USB bus registered, assigned bus number 9
[    1.930426] ohci-pci 0000:00:14.5: irq 18, io mem 0xff74d000
[    1.989625] usb usb9: New USB device found, idVendor=1d6b, idProduct=0001
[    1.989630] usb usb9: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.989633] usb usb9: Product: OHCI PCI host controller
[    1.989634] usb usb9: Manufacturer: Linux 3.11.0-14-generic ohci_hcd
[    1.989636] usb usb9: SerialNumber: 0000:00:14.5
[    1.990015] hub 9-0:1.0: USB hub found
[    1.990026] hub 9-0:1.0: 2 ports detected
[    1.990762] scsi3 : pata_atiixp
[    1.991099] scsi4 : pata_atiixp
[    1.991337] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf100 irq 14
[    1.991339] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf108 irq 15
[    1.991410] sdhci-pci 0000:00:14.7: SDHCI controller found [1022:7806] (rev 0)
[    1.991584] mmc0: no vqmmc regulator found
[    1.991586] mmc0: no vmmc regulator found
[    1.991724] mmc0: SDHCI controller on PCI [0000:00:14.7] using ADMA
[    2.125620] ata3: SATA link down (SStatus 0 SControl 300)
[    2.297529] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.297570] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.298397] ata2.00: ATAPI: PLDS DVD+/-RW DS-8A8SH, KD11, max UDMA/100
[    2.299927] ata2.00: configured for UDMA/100
[    2.353840] ata1.00: ATA-8: ST9500325AS, D005DEM1, max UDMA/133
[    2.353848] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.356748] ata1.00: configured for UDMA/133
[    2.357284] scsi 0:0:0:0: Direct-Access     ATA      ST9500325AS      D005 PQ: 0 ANSI: 5
[    2.357565] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    2.357567] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.357604] sd 0:0:0:0: [sda] Write Protect is off
[    2.357607] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.357621] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.359755] scsi 1:0:0:0: CD-ROM            PLDS     DVD+-RW DS-8A8SH KD11 PQ: 0 ANSI: 5
[    2.363248] sr0: scsi3-mmc drive: 16x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.363260] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.363613] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.363774] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.394714]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    2.396218] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.537367] usb 2-3: new high-speed USB device number 2 using ehci-pci
[    2.581447] tsc: Refined TSC clocksource calibration: 1597.094 MHz
[    2.676960] usb 2-3: New USB device found, idVendor=05ca, idProduct=181d
[    2.676973] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.676979] usb 2-3: Product: Laptop_Integrated_Webcam_FHD
[    2.676984] usb 2-3: Manufacturer: CKFA228h475010006CQ0
[    2.789238] usb 2-5: new high-speed USB device number 3 using ehci-pci
[    2.934791] usb 2-5: New USB device found, idVendor=0bda, idProduct=0138
[    2.934803] usb 2-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.934810] usb 2-5: Product: USB2.0-CRW
[    2.934817] usb 2-5: Manufacturer: Generic
[    2.934819] usb 2-5: SerialNumber: 20090516388200000
[    2.943105] usbcore: registered new interface driver usb-storage
[    2.944538] ums-realtek 2-5:1.0: USB Mass Storage device detected
[    2.968605] scsi5 : usb-storage 2-5:1.0
[    2.968728] usbcore: registered new interface driver ums-realtek
[    3.053342] usb 3-2: new low-speed USB device number 2 using xhci_hcd
[    3.110213] usb 3-2: New USB device found, idVendor=045e, idProduct=0040
[    3.110220] usb 3-2: New USB device strings: Mfr=1, Product=3, SerialNumber=0
[    3.110224] usb 3-2: Product: Microsoft 3-Button Mouse with IntelliEye(TM)
[    3.110226] usb 3-2: Manufacturer: Microsoft
[    3.110492] usb 3-2: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    3.115832] hidraw: raw HID events driver (C) Jiri Kosina
[    3.131305] usbcore: registered new interface driver usbhid
[    3.131309] usbhid: USB HID core driver
[    3.133542] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:10.0/usb3/3-2/3-2:1.0/input/input5
[    3.134057] hid-generic 0003:045E:0040.0001: input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:10.0-2/input0
[    3.501221] usb 7-2: new full-speed USB device number 2 using ohci-pci
[    3.581421] Switched to clocksource tsc
[    3.676212] usb 7-2: New USB device found, idVendor=0a5c, idProduct=21bc
[    3.676224] usb 7-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    3.676231] usb 7-2: Product: Dell Wireless 1701 Bluetooth
[    3.676236] usb 7-2: Manufacturer: Broadcom Corp
[    3.676240] usb 7-2: SerialNumber: 7CE9D3D40916
[    3.791468] EXT4-fs (sda6): INFO: recovery required on readonly filesystem
[    3.791474] EXT4-fs (sda6): write access will be enabled during recovery
[    3.941005] usb 7-3: new full-speed USB device number 3 using ohci-pci
[    4.106105] usb 7-3: New USB device found, idVendor=138a, idProduct=0011
[    4.106117] usb 7-3: New USB device strings: Mfr=0, Product=0, SerialNumber=1
[    4.106124] usb 7-3: SerialNumber: 17d34241c140
[    4.153052] usb 2-5: USB disconnect, device number 3
[    7.216931] EXT4-fs (sda6): orphan cleanup on readonly fs
[    7.254344] EXT4-fs (sda6): 17 orphan inodes deleted
[    7.254351] EXT4-fs (sda6): recovery complete
[    7.442635] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   22.878182] Adding 5740540k swap on /dev/sda5.  Priority:-1 extents:1 across:5740540k FS
[   23.019348] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.104804] systemd-udevd[295]: starting version 204
[   23.252074] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[   23.279153] acpi device:30: registered as cooling_device4
[   23.279174] ACPI: Video Device [VGA1] (multi-head: yes  rom: no  post: no)
[   23.279253] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input6
[   23.285625] lp: driver loaded but no devices found
[   23.290529] wmi: Mapper loaded
[   23.290974] AMD IOMMUv2 driver by Joerg Roedel <joerg.roedel@amd.com>
[   23.290980] AMD IOMMUv2 functionality not available on this system
[   23.294914] bcma: bus0: Found chip with id 0x4313, rev 0x01 and package 0x08
[   23.294938] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x24, class 0x0)
[   23.294955] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x18, class 0x0)
[   23.294987] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x11, class 0x0)
[   23.301773] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   23.301781] Disabling lock debugging due to kernel taint
[   23.314160] bcma: bus0: Bus registered
[   23.320939] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   23.341230] Bluetooth: Core ver 2.16
[   23.341254] NET: Registered protocol family 31
[   23.341256] Bluetooth: HCI device and connection manager initialized
[   23.341270] Bluetooth: HCI socket layer initialized
[   23.341274] Bluetooth: L2CAP socket layer initialized
[   23.341281] Bluetooth: SCO socket layer initialized
[   23.352061] usbcore: registered new interface driver btusb
[   23.352140] hda-intel 0000:00:01.1: Using LPIB position fix
[   23.352185] snd_hda_intel 0000:00:01.1: irq 53 for MSI/MSI-X
[   23.352552] <6>[fglrx] Maximum main memory to use for locked dma buffers: 5253 MBytes.
[   23.352691] <6>[fglrx]   vendor: 1002 device: 9641 count: 1
[   23.353243] <6>[fglrx] ioport: bar 1, base 0xf000, size: 0x100
[   23.353950] <6>[fglrx] Kernel PAT support is enabled
[   23.353978] <6>[fglrx] module loaded - fglrx 13.10.10 [May 23 2013] with 1 minors
[   23.357043] hda-intel 0000:00:01.1: Enable sync_write for stable communication
[   23.363781] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.1/sound/card0/input7
[   23.371494] hda-intel 0000:00:14.2: Using LPIB position fix
[   23.374993] hda-intel 0000:00:14.2: Enable sync_write for stable communication
[   23.376275] microcode: CPU0: patch_level=0x03000025
[   23.383493] autoconfig: line_outs=1 (0xd/0x0/0x0/0x0/0x0) type:speaker
[   23.383500]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   23.383508]    hp_outs=1 (0xb/0x0/0x0/0x0/0x0)
[   23.383510]    mono: mono_out=0x0
[   23.383511]    inputs:
[   23.383514]      Internal Mic=0x11
[   23.383516]      Mic=0xa
[   23.390614] type=1400 audit(1388149801.143:2): apparmor="STATUS" operation="profile_load" parent=334 profile="unconfined" name="/sbin/dhclient" pid=365 comm="apparmor_parser"
[   23.390627] type=1400 audit(1388149801.143:3): apparmor="STATUS" operation="profile_load" parent=334 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=365 comm="apparmor_parser"
[   23.390634] type=1400 audit(1388149801.143:4): apparmor="STATUS" operation="profile_load" parent=334 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=365 comm="apparmor_parser"
[   23.391523] type=1400 audit(1388149801.143:5): apparmor="STATUS" operation="profile_replace" parent=334 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=365 comm="apparmor_parser"
[   23.391531] type=1400 audit(1388149801.143:6): apparmor="STATUS" operation="profile_replace" parent=334 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=365 comm="apparmor_parser"
[   23.392057] type=1400 audit(1388149801.147:7): apparmor="STATUS" operation="profile_replace" parent=334 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=365 comm="apparmor_parser"
[   23.395663] type=1400 audit(1388149801.147:8): apparmor="STATUS" operation="profile_load" parent=334 profile="unconfined" name="/usr/sbin/ntpd" pid=367 comm="apparmor_parser"
[   23.396042] input: HD-Audio Generic Headphone as /devices/pci0000:00/0000:00:14.2/sound/card1/input8
[   23.396184] input: HD-Audio Generic Mic as /devices/pci0000:00/0000:00:14.2/sound/card1/input9
[   23.448326] microcode: CPU0: new patch_level=0x03000027
[   23.448380] microcode: CPU1: patch_level=0x03000025
[   23.448403] microcode: CPU1: new patch_level=0x03000027
[   23.448417] microcode: CPU2: patch_level=0x03000025
[   23.448436] microcode: CPU2: new patch_level=0x03000027
[   23.448446] microcode: CPU3: patch_level=0x03000025
[   23.448464] microcode: CPU3: new patch_level=0x03000027
[   23.448598] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   23.454936] kvm: Nested Virtualization enabled
[   23.454944] kvm: Nested Paging enabled
[   23.469700] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   23.543057] input: Dell WMI hotkeys as /devices/virtual/input/input10
[   23.558966] cfg80211: Calling CRDA to update world regulatory domain
[   23.586877] Support for cores revisions 0x17 and 0x18 disabled by module param allhwsupport=0. Try b43.allhwsupport=1
[   23.586891] b43: probe of bcma0:0 failed with error -524
[   23.586929] Broadcom 43xx driver loaded [ Features: PNL ]
[   23.601098] brcmsmac bcma0:0: mfg 4bf core 812 rev 24 class 0 irq 18
[   23.607415] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   23.607838] ieee80211 phy0: registered radio enabled led device: brcmsmac-phy0:radio gpio: 243
[   23.813688] Linux video capture interface: v2.00
[   23.822779] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_FHD (05ca:181d)
[   23.824439] input: Laptop_Integrated_Webcam_FHD as /devices/pci0000:00/0000:00:13.2/usb2/2-3/2-3:1.0/input/input11
[   23.824561] usbcore: registered new interface driver uvcvideo
[   23.824564] USB Video Class driver (1.1.1)
[   24.005918] cfg80211: World regulatory domain updated:
[   24.005923] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   24.005926] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.005928] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.005929] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   24.005931] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.005932] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.527377] input: DualPoint Stick as /devices/platform/i8042/serio1/input/input12
[   24.541431] input: AlpsPS/2 ALPS DualPoint TouchPad as /devices/platform/i8042/serio1/input/input13
[   25.582015] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   26.099310] init: failsafe main process (579) killed by TERM signal
[   26.537776] type=1400 audit(1388149804.291:9): apparmor="STATUS" operation="profile_load" parent=677 profile="unconfined" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper" pid=684 comm="apparmor_parser"
[   26.537790] type=1400 audit(1388149804.291:10): apparmor="STATUS" operation="profile_load" parent=677 profile="unconfined" name="chromium_browser" pid=684 comm="apparmor_parser"
[   26.538121] type=1400 audit(1388149804.291:11): apparmor="STATUS" operation="profile_load" parent=677 profile="unconfined" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=683 comm="apparmor_parser"
[   26.561197] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   26.561204] Bluetooth: BNEP filters: protocol multicast
[   26.561218] Bluetooth: BNEP socket layer initialized
[   26.562531] Bluetooth: RFCOMM TTY layer initialized
[   26.562550] Bluetooth: RFCOMM socket layer initialized
[   26.562553] Bluetooth: RFCOMM ver 1.11
[   26.999436] init: avahi-cups-reload main process (734) terminated with status 1
[   27.178636] ppdev: user-space parallel port driver
[   27.278319] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[   27.278326] vesafb: scrolling: redraw
[   27.278330] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[   27.279788] vesafb: framebuffer at 0xb0000000, mapped to 0xffffc90011280000, using 3072k, total 3072k
[   27.281389] Console: switching to colour frame buffer device 128x48
[   27.285790] fb0: VESA VGA frame buffer device
[   29.194046] r8169 0000:01:00.0 eth0: link down
[   29.194105] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   29.194471] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   29.560718] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   29.560782] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[   29.560956] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.561329] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   31.353474] fglrx_pci 0000:00:01.0: irq 54 for MSI/MSI-X
[   31.354463] <6>[fglrx] Firegl kernel thread PID: 1210
[   31.354758] <6>[fglrx] Firegl kernel thread PID: 1211
[   31.355045] <6>[fglrx] Firegl kernel thread PID: 1212
[   31.355166] <6>[fglrx] IRQ 54 Enabled
[   31.359331] <6>[fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   31.359334] <6>[fglrx] Reserved FB block: Unshared offset:fb7c000, size:484000 
[   31.359336] <6>[fglrx] Reserved FB block: Unshared offset:1fff4000, size:c000 
[   31.469762] <6>[fglrx] ATIF platform detected with notification ID: 0x81
[   32.699003] ACPI Error: Needed [Integer/String/Buffer], found [Reference] ffff8801b46f5000 (20130517/exresop-422)
[   32.699012] ACPI Exception: AE_AML_OPERAND_TYPE, While resolving operands for [OpcodeName unavailable] (20130517/dswexec-461)
[   32.699016] ACPI Error: Method parse/execution failed [\_SB_.PCI0.VGA_.AF03] (Node ffff8801c6684640), AE_AML_OPERAND_TYPE (20130517/psparse-536)
[   32.699024] ACPI Error: Method parse/execution failed [\_SB_.PCI0.VGA_.ATIF] (Node ffff8801c66843c0), AE_AML_OPERAND_TYPE (20130517/psparse-536)
[   68.677053] ISO 9660 Extensions: Microsoft Joliet Level 3
[   68.830039] ISO 9660 Extensions: RRIP_1991A
[   92.352686] systemd-hostnamed[2556]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[ 2108.326399] audit_printk_skb: 174 callbacks suppressed
[ 2108.326410] type=1400 audit(1388151886.588:70): apparmor="STATUS" operation="profile_replace" parent=3077 profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=3081 comm="apparmor_parser"
[ 2108.326437] type=1400 audit(1388151886.588:71): apparmor="STATUS" operation="profile_replace" parent=3077 profile="unconfined" name="/usr/sbin/cupsd" pid=3081 comm="apparmor_parser"
[ 2108.328655] type=1400 audit(1388151886.592:72): apparmor="STATUS" operation="profile_replace" parent=3077 profile="unconfined" name="/usr/sbin/cupsd" pid=3081 comm="apparmor_parser"
[ 7363.177787] PM: Syncing filesystems ... done.
[ 7363.345175] PM: Preparing system for mem sleep
[ 7363.345530] Freezing user space processes ... (elapsed 0.001 seconds) done.
[ 7363.347160] Freezing remaining freezable tasks ... (elapsed 0.001 seconds) done.
[ 7363.348493] PM: Entering mem sleep
[ 7363.348602] Suspending console(s) (use no_console_suspend to debug)
[ 7363.349066] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[ 7363.349390] sd 0:0:0:0: [sda] Stopping disk
[ 7363.366772] <6>[fglrx] IRQ 54 Disabled
[ 7363.366883] <6>[fglrx] Preparing suspend fglrx in kernel.
[ 7363.582606] <6>[fglrx] Suspending fglrx in kernel completed.
[ 7363.582607] <6>[fglrx] Power down the ASIC .
[ 7363.729278] PM: suspend of devices complete after 380.601 msecs
[ 7363.729500] PM: late suspend of devices complete after 0.219 msecs
[ 7363.745161] pcieport 0000:00:04.0: System wakeup enabled by ACPI
[ 7363.761508] ehci-pci 0000:00:13.2: System wakeup enabled by ACPI
[ 7363.777197] ohci-pci 0000:00:13.0: System wakeup enabled by ACPI
[ 7363.777301] ehci-pci 0000:00:12.2: System wakeup enabled by ACPI
[ 7363.793179] ohci-pci 0000:00:12.0: System wakeup enabled by ACPI
[ 7363.793298] xhci_hcd 0000:00:10.1: System wakeup enabled by ACPI
[ 7363.809183] xhci_hcd 0000:00:10.0: System wakeup enabled by ACPI
[ 7363.825250] PM: noirq suspend of devices complete after 95.767 msecs
[ 7363.825322] ACPI: Preparing to enter system sleep state S3
[ 7363.949385] PM: Saving platform NVS memory
[ 7363.951872] Disabling non-boot CPUs ...
[ 7363.953771] smpboot: CPU 1 is now offline
[ 7363.954489] Broke affinity for irq 18
[ 7364.056841] smpboot: CPU 2 is now offline
[ 7364.057684] Broke affinity for irq 41
[ 7364.057708] Broke affinity for irq 51
[ 7364.160820] smpboot: CPU 3 is now offline
[ 7364.161528] ACPI: Low-level resume complete
[ 7364.161567] PM: Restoring platform NVS memory
[ 7364.163121] microcode: CPU0: new patch_level=0x03000027
[ 7364.163174] Enabling non-boot CPUs ...
[ 7364.163215] smpboot: Booting Node 0 Processor 1 APIC 0x1
[ 7364.174217] LVT offset 0 assigned for vector 0x400
[ 7364.176664] microcode: CPU1: new patch_level=0x03000027
[ 7364.176667] CPU1 is up
[ 7364.176684] smpboot: Booting Node 0 Processor 2 APIC 0x2
[ 7364.190012] microcode: CPU2: new patch_level=0x03000027
[ 7364.190015] CPU2 is up
[ 7364.190030] smpboot: Booting Node 0 Processor 3 APIC 0x3
[ 7364.203353] microcode: CPU3: new patch_level=0x03000027
[ 7364.203357] CPU3 is up
[ 7364.204644] ACPI: Waking up from system sleep state S3
[ 7364.258964] xhci_hcd 0000:00:10.0: System wakeup disabled by ACPI
[ 7364.274928] xhci_hcd 0000:00:10.1: System wakeup disabled by ACPI
[ 7364.275032] ohci-pci 0000:00:12.0: System wakeup disabled by ACPI
[ 7364.290943] ehci-pci 0000:00:12.2: System wakeup disabled by ACPI
[ 7364.291027] ohci-pci 0000:00:13.0: System wakeup disabled by ACPI
[ 7364.306940] ehci-pci 0000:00:13.2: System wakeup disabled by ACPI
[ 7364.354982] PM: noirq resume of devices complete after 125.166 msecs
[ 7364.355185] PM: early resume of devices complete after 0.110 msecs
[ 7364.356671] snd_hda_intel 0000:00:01.1: irq 53 for MSI/MSI-X
[ 7364.357710] pciehp 0000:00:15.1:pcie04: No adapter on slot(0)
[ 7364.357736] pcieport 0000:00:04.0: System wakeup disabled by ACPI
[ 7364.362411] <6>[fglrx] Power up the ASIC
[ 7364.367475] <6>[fglrx] Preparing resume fglrx in kernel.
[ 7364.372629] <6>[fglrx] Resuming fglrx in kernel completed.
[ 7364.372671] <6>[fglrx] IRQ 54 Enabled
[ 7364.676782] usb 3-2: reset low-speed USB device number 2 using xhci_hcd
[ 7364.709936] xhci_hcd 0000:00:10.0: xHCI xhci_drop_endpoint called with disabled ep ffff8801c20e5f00
[ 7364.709951] usb 3-2: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[ 7364.810720] ata3: SATA link down (SStatus 0 SControl 300)
[ 7364.894710] usb 7-2: reset full-speed USB device number 2 using ohci-pci
[ 7364.994670] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 7364.996624] ata2.00: configured for UDMA/100
[ 7365.051677] usb 7-2: device firmware changed
[ 7365.186747] usb 7-3: reset full-speed USB device number 3 using ohci-pci
[ 7366.778271] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 7367.034070] ata1.00: configured for UDMA/133
[ 7367.050497] sd 0:0:0:0: [sda] Starting disk
[ 7367.077456] PM: resume of devices complete after 2722.933 msecs
[ 7367.077690] PM: Finishing wakeup.
[ 7367.077691] Restarting tasks ... done.
[ 7367.079416] usb 2-3: USB disconnect, device number 2
[ 7367.114494] video LNXVIDEO:01: Restoring backlight state
[ 7367.350137] usb 2-3: new high-speed USB device number 4 using ehci-pci
[ 7367.633684] usb 2-3: New USB device found, idVendor=05ca, idProduct=181d
[ 7367.633690] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 7367.633692] usb 2-3: Product: Laptop_Integrated_Webcam_FHD
[ 7367.633694] usb 2-3: Manufacturer: CKFA228h475010006CQ0
[ 7367.634751] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_FHD (05ca:181d)
[ 7367.636220] input: Laptop_Integrated_Webcam_FHD as /devices/pci0000:00/0000:00:13.2/usb2/2-3/2-3:1.0/input/input14
[ 7367.745859] usb 2-5: new high-speed USB device number 5 using ehci-pci
[ 7367.891090] usb 2-5: New USB device found, idVendor=0bda, idProduct=0138
[ 7367.891103] usb 2-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 7367.891110] usb 2-5: Product: USB2.0-CRW
[ 7367.891115] usb 2-5: Manufacturer: Generic
[ 7367.891120] usb 2-5: SerialNumber: 20090516388200000
[ 7367.897231] ums-realtek 2-5:1.0: USB Mass Storage device detected
[ 7367.921324] scsi6 : usb-storage 2-5:1.0
[ 7367.921535] usb 7-2: USB disconnect, device number 2
[ 7368.057783] usb 7-2: new full-speed USB device number 4 using ohci-pci
[ 7368.232983] usb 7-2: New USB device found, idVendor=0a5c, idProduct=21bc
[ 7368.232997] usb 7-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 7368.233004] usb 7-2: Product: Dell Wireless 1701 Bluetooth
[ 7368.233009] usb 7-2: Manufacturer: Broadcom Corp
[ 7368.233014] usb 7-2: SerialNumber: 7CE9D3D40916
[ 7368.236131] usb 2-5: USB disconnect, device number 5
[ 7368.697353] r8169 0000:01:00.0 eth0: link down
[ 7368.697408] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 7368.746070] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 7368.746079] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[ 7368.746217] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7368.866286] atkbd serio0: Unknown key pressed (translated set 2, code 0x8d on isa0060/serio0).
[ 7368.866299] atkbd serio0: Use 'setkeycodes e00d <keycode>' to make it known.
[ 7371.616056] VFS: busy inodes on changed media or resized disk sr0
[ 9365.256910] PM: Syncing filesystems ... done.
[ 9365.394626] PM: Preparing system for mem sleep
[ 9365.394962] Freezing user space processes ... (elapsed 0.001 seconds) done.
[ 9365.396638] Freezing remaining freezable tasks ... (elapsed 0.001 seconds) done.
[ 9365.397981] PM: Entering mem sleep
[ 9365.398096] Suspending console(s) (use no_console_suspend to debug)
[ 9365.398586] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[ 9365.398943] sd 0:0:0:0: [sda] Stopping disk
[ 9365.411348] <6>[fglrx] IRQ 54 Disabled
[ 9365.411472] <6>[fglrx] Preparing suspend fglrx in kernel.
[ 9365.631249] <6>[fglrx] Suspending fglrx in kernel completed.
[ 9365.631251] <6>[fglrx] Power down the ASIC .
[ 9365.773644] PM: suspend of devices complete after 375.474 msecs
[ 9365.773866] PM: late suspend of devices complete after 0.219 msecs
[ 9365.787308] pcieport 0000:00:04.0: System wakeup enabled by ACPI
[ 9365.803688] ehci-pci 0000:00:13.2: System wakeup enabled by ACPI
[ 9365.819333] ohci-pci 0000:00:13.0: System wakeup enabled by ACPI
[ 9365.819434] ehci-pci 0000:00:12.2: System wakeup enabled by ACPI
[ 9365.835328] ohci-pci 0000:00:12.0: System wakeup enabled by ACPI
[ 9365.835447] xhci_hcd 0000:00:10.1: System wakeup enabled by ACPI
[ 9365.851322] xhci_hcd 0000:00:10.0: System wakeup enabled by ACPI
[ 9365.867420] PM: noirq suspend of devices complete after 93.571 msecs
[ 9365.867496] ACPI: Preparing to enter system sleep state S3
[ 9365.879449] PM: Saving platform NVS memory
[ 9365.881742] Disabling non-boot CPUs ...
[ 9365.882505] Broke affinity for irq 51
[ 9365.883570] smpboot: CPU 1 is now offline
[ 9365.885172] smpboot: CPU 2 is now offline
[ 9365.885857] Broke affinity for irq 17
[ 9365.885869] Broke affinity for irq 41
[ 9365.987001] smpboot: CPU 3 is now offline
[ 9365.987697] ACPI: Low-level resume complete
[ 9365.987735] PM: Restoring platform NVS memory
[ 9365.989142] microcode: CPU0: new patch_level=0x03000027
[ 9365.989194] Enabling non-boot CPUs ...
[ 9365.989233] smpboot: Booting Node 0 Processor 1 APIC 0x1
[ 9366.000236] LVT offset 0 assigned for vector 0x400
[ 9366.002676] microcode: CPU1: new patch_level=0x03000027
[ 9366.002681] CPU1 is up
[ 9366.002697] smpboot: Booting Node 0 Processor 2 APIC 0x2
[ 9366.016019] microcode: CPU2: new patch_level=0x03000027
[ 9366.016022] CPU2 is up
[ 9366.016037] smpboot: Booting Node 0 Processor 3 APIC 0x3
[ 9366.029365] microcode: CPU3: new patch_level=0x03000027
[ 9366.029369] CPU3 is up
[ 9366.030678] ACPI: Waking up from system sleep state S3
[ 9366.084892] xhci_hcd 0000:00:10.0: System wakeup disabled by ACPI
[ 9366.100886] xhci_hcd 0000:00:10.1: System wakeup disabled by ACPI
[ 9366.100992] ohci-pci 0000:00:12.0: System wakeup disabled by ACPI
[ 9366.116873] ehci-pci 0000:00:12.2: System wakeup disabled by ACPI
[ 9366.116959] ohci-pci 0000:00:13.0: System wakeup disabled by ACPI
[ 9366.132869] ehci-pci 0000:00:13.2: System wakeup disabled by ACPI
[ 9366.180911] PM: noirq resume of devices complete after 124.697 msecs
[ 9366.181114] PM: early resume of devices complete after 0.110 msecs
[ 9366.183098] snd_hda_intel 0000:00:01.1: irq 53 for MSI/MSI-X
[ 9366.183363] pciehp 0000:00:15.1:pcie04: No adapter on slot(0)
[ 9366.183369] pcieport 0000:00:04.0: System wakeup disabled by ACPI
[ 9366.188676] <6>[fglrx] Power up the ASIC
[ 9366.193838] <6>[fglrx] Preparing resume fglrx in kernel.
[ 9366.199113] <6>[fglrx] Resuming fglrx in kernel completed.
[ 9366.199167] <6>[fglrx] IRQ 54 Enabled
[ 9366.506031] usb 3-2: reset low-speed USB device number 2 using xhci_hcd
[ 9366.535271] xhci_hcd 0000:00:10.0: xHCI xhci_drop_endpoint called with disabled ep ffff8801c20e5f00
[ 9366.535286] usb 3-2: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[ 9366.640801] ata3: SATA link down (SStatus 0 SControl 300)
[ 9366.716731] usb 7-2: reset full-speed USB device number 4 using ohci-pci
[ 9366.812731] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 9366.815026] ata2.00: configured for UDMA/100
[ 9366.875643] usb 7-2: device firmware changed
[ 9367.008651] usb 7-3: reset full-speed USB device number 3 using ohci-pci
[ 9368.664293] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 9368.749263] ata1.00: configured for UDMA/133
[ 9368.764323] sd 0:0:0:0: [sda] Starting disk
[ 9368.812256] PM: resume of devices complete after 2631.781 msecs
[ 9368.812488] PM: Finishing wakeup.
[ 9368.812490] Restarting tasks ... done.
[ 9368.813250] usb 2-3: USB disconnect, device number 4
[ 9368.864577] video LNXVIDEO:01: Restoring backlight state
[ 9369.100053] usb 2-3: new high-speed USB device number 6 using ehci-pci
[ 9369.382394] usb 2-3: New USB device found, idVendor=05ca, idProduct=181d
[ 9369.382402] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 9369.382406] usb 2-3: Product: Laptop_Integrated_Webcam_FHD
[ 9369.382409] usb 2-3: Manufacturer: CKFA228h475010006CQ0
[ 9369.383213] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_FHD (05ca:181d)
[ 9369.385087] input: Laptop_Integrated_Webcam_FHD as /devices/pci0000:00/0000:00:13.2/usb2/2-3/2-3:1.0/input/input15
[ 9369.495931] usb 2-5: new high-speed USB device number 7 using ehci-pci
[ 9369.640473] usb 2-5: New USB device found, idVendor=0bda, idProduct=0138
[ 9369.640487] usb 2-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 9369.640494] usb 2-5: Product: USB2.0-CRW
[ 9369.640499] usb 2-5: Manufacturer: Generic
[ 9369.640503] usb 2-5: SerialNumber: 20090516388200000
[ 9369.647306] ums-realtek 2-5:1.0: USB Mass Storage device detected
[ 9369.670679] scsi7 : usb-storage 2-5:1.0
[ 9369.671045] usb 7-2: USB disconnect, device number 4
[ 9369.807874] usb 7-2: new full-speed USB device number 5 using ohci-pci
[ 9369.982956] usb 7-2: New USB device found, idVendor=0a5c, idProduct=21bc
[ 9369.982969] usb 7-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 9369.982976] usb 7-2: Product: Dell Wireless 1701 Bluetooth
[ 9369.982981] usb 7-2: Manufacturer: Broadcom Corp
[ 9369.982986] usb 7-2: SerialNumber: 7CE9D3D40916
[ 9369.986289] usb 2-5: USB disconnect, device number 7
[ 9370.139627] r8169 0000:01:00.0 eth0: link down
[ 9370.139911] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 9370.189091] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 9370.189107] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[ 9370.189336] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9370.344372] atkbd serio0: Unknown key pressed (translated set 2, code 0x8d on isa0060/serio0).
[ 9370.344385] atkbd serio0: Use 'setkeycodes e00d <keycode>' to make it known.
[ 9373.046463] VFS: busy inodes on changed media or resized disk sr0
[10429.340156] PM: Syncing filesystems ... done.
[10429.566720] PM: Preparing system for mem sleep
[10429.567090] Freezing user space processes ... (elapsed 0.001 seconds) done.
[10429.568668] Freezing remaining freezable tasks ... (elapsed 0.001 seconds) done.
[10429.570001] PM: Entering mem sleep
[10429.570112] Suspending console(s) (use no_console_suspend to debug)
[10429.570517] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[10429.583496] <6>[fglrx] IRQ 54 Disabled
[10429.583620] <6>[fglrx] Preparing suspend fglrx in kernel.
[10429.585840] sd 0:0:0:0: [sda] Stopping disk
[10429.801304] <6>[fglrx] Suspending fglrx in kernel completed.
[10429.801305] <6>[fglrx] Power down the ASIC .
[10429.968987] PM: suspend of devices complete after 398.794 msecs
[10429.969227] PM: late suspend of devices complete after 0.237 msecs
[10429.983644] pcieport 0000:00:04.0: System wakeup enabled by ACPI
[10429.999990] ehci-pci 0000:00:13.2: System wakeup enabled by ACPI
[10430.015664] ohci-pci 0000:00:13.0: System wakeup enabled by ACPI
[10430.015766] ehci-pci 0000:00:12.2: System wakeup enabled by ACPI
[10430.031663] ohci-pci 0000:00:12.0: System wakeup enabled by ACPI
[10430.031781] xhci_hcd 0000:00:10.1: System wakeup enabled by ACPI
[10430.047664] xhci_hcd 0000:00:10.0: System wakeup enabled by ACPI
[10430.063731] PM: noirq suspend of devices complete after 94.520 msecs
[10430.063807] ACPI: Preparing to enter system sleep state S3
[10430.068757] PM: Saving platform NVS memory
[10430.071136] Disabling non-boot CPUs ...
[10430.175339] smpboot: CPU 1 is now offline
[10430.176976] smpboot: CPU 2 is now offline
[10430.177740] Broke affinity for irq 17
[10430.279311] smpboot: CPU 3 is now offline
[10430.280017] ACPI: Low-level resume complete
[10430.280056] PM: Restoring platform NVS memory
[10430.281452] microcode: CPU0: new patch_level=0x03000027
[10430.281491] Enabling non-boot CPUs ...
[10430.281531] smpboot: Booting Node 0 Processor 1 APIC 0x1
[10430.292534] LVT offset 0 assigned for vector 0x400
[10430.294973] microcode: CPU1: new patch_level=0x03000027
[10430.294977] CPU1 is up
[10430.294994] smpboot: Booting Node 0 Processor 2 APIC 0x2
[10430.308319] microcode: CPU2: new patch_level=0x03000027
[10430.308323] CPU2 is up
[10430.308338] smpboot: Booting Node 0 Processor 3 APIC 0x3
[10430.321666] microcode: CPU3: new patch_level=0x03000027
[10430.321670] CPU3 is up
[10430.322985] ACPI: Waking up from system sleep state S3
[10430.377216] xhci_hcd 0000:00:10.0: System wakeup disabled by ACPI
[10430.393210] xhci_hcd 0000:00:10.1: System wakeup disabled by ACPI
[10430.393313] ohci-pci 0000:00:12.0: System wakeup disabled by ACPI
[10430.409197] ehci-pci 0000:00:12.2: System wakeup disabled by ACPI
[10430.409283] ohci-pci 0000:00:13.0: System wakeup disabled by ACPI
[10430.425192] ehci-pci 0000:00:13.2: System wakeup disabled by ACPI
[10430.473233] PM: noirq resume of devices complete after 124.772 msecs
[10430.473436] PM: early resume of devices complete after 0.110 msecs
[10430.475379] snd_hda_intel 0000:00:01.1: irq 53 for MSI/MSI-X
[10430.477293] pciehp 0000:00:15.1:pcie04: No adapter on slot(0)
[10430.477318] pcieport 0000:00:04.0: System wakeup disabled by ACPI
[10430.481699] <6>[fglrx] Power up the ASIC
[10430.486945] <6>[fglrx] Preparing resume fglrx in kernel.
[10430.492175] <6>[fglrx] Resuming fglrx in kernel completed.
[10430.492216] <6>[fglrx] IRQ 54 Enabled
[10430.798407] usb 3-2: reset low-speed USB device number 2 using xhci_hcd
[10430.827590] xhci_hcd 0000:00:10.0: xHCI xhci_drop_endpoint called with disabled ep ffff8801c20e5f00
[10430.827600] usb 3-2: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[10430.933111] ata3: SATA link down (SStatus 0 SControl 300)
[10431.009072] usb 7-2: reset full-speed USB device number 5 using ohci-pci
[10431.105038] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[10431.107440] ata2.00: configured for UDMA/100
[10431.167238] usb 7-2: device firmware changed
[10431.301004] usb 7-3: reset full-speed USB device number 3 using ohci-pci
[10432.952616] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[10433.183134] ata1.00: configured for UDMA/133
[10433.196851] sd 0:0:0:0: [sda] Starting disk
[10433.226560] PM: resume of devices complete after 2753.794 msecs
[10433.226793] PM: Finishing wakeup.
[10433.226795] Restarting tasks ... done.
[10433.227693] usb 2-3: USB disconnect, device number 6
[10433.256899] video LNXVIDEO:01: Restoring backlight state
[10433.508481] usb 2-3: new high-speed USB device number 8 using ehci-pci
[10433.790892] usb 2-3: New USB device found, idVendor=05ca, idProduct=181d
[10433.790898] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[10433.790900] usb 2-3: Product: Laptop_Integrated_Webcam_FHD
[10433.790902] usb 2-3: Manufacturer: CKFA228h475010006CQ0
[10433.791797] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_FHD (05ca:181d)
[10433.794344] input: Laptop_Integrated_Webcam_FHD as /devices/pci0000:00/0000:00:13.2/usb2/2-3/2-3:1.0/input/input16
[10433.904397] usb 2-5: new high-speed USB device number 9 using ehci-pci
[10434.048619] usb 2-5: New USB device found, idVendor=0bda, idProduct=0138
[10434.048632] usb 2-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[10434.048639] usb 2-5: Product: USB2.0-CRW
[10434.048644] usb 2-5: Manufacturer: Generic
[10434.048649] usb 2-5: SerialNumber: 20090516388200000
[10434.054746] ums-realtek 2-5:1.0: USB Mass Storage device detected
[10434.079056] scsi8 : usb-storage 2-5:1.0
[10434.079463] usb 7-2: USB disconnect, device number 5
[10434.224209] usb 7-2: new full-speed USB device number 6 using ohci-pci
[10434.399330] usb 7-2: New USB device found, idVendor=0a5c, idProduct=21bc
[10434.399344] usb 7-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[10434.399351] usb 7-2: Product: Dell Wireless 1701 Bluetooth
[10434.399357] usb 7-2: Manufacturer: Broadcom Corp
[10434.399362] usb 7-2: SerialNumber: 7CE9D3D40916
[10434.402349] usb 2-5: USB disconnect, device number 9
[10434.607781] r8169 0000:01:00.0 eth0: link down
[10434.607832] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[10434.656183] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[10434.656193] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[10434.656341] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[10434.846208] atkbd serio0: Unknown key pressed (translated set 2, code 0x8d on isa0060/serio0).
[10434.846223] atkbd serio0: Use 'setkeycodes e00d <keycode>' to make it known.
[10437.746024] VFS: busy inodes on changed media or resized disk sr0
[12037.656091] usb 3-2: USB disconnect, device number 2
[12039.523234] PM: Syncing filesystems ... done.
[12039.782176] PM: Preparing system for mem sleep
[12039.782712] Freezing user space processes ... (elapsed 0.001 seconds) done.
[12039.784380] Freezing remaining freezable tasks ... (elapsed 0.001 seconds) done.
[12039.785781] PM: Entering mem sleep
[12039.785923] Suspending console(s) (use no_console_suspend to debug)
[12039.802849] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[12039.803233] sd 0:0:0:0: [sda] Stopping disk
[12039.815488] <6>[fglrx] IRQ 54 Disabled
[12039.815628] <6>[fglrx] Preparing suspend fglrx in kernel.
[12040.038749] <6>[fglrx] Suspending fglrx in kernel completed.
[12040.038751] <6>[fglrx] Power down the ASIC .
[12040.179686] PM: suspend of devices complete after 377.715 msecs
[12040.179902] PM: late suspend of devices complete after 0.213 msecs
[12040.210221] ehci-pci 0000:00:13.2: System wakeup enabled by ACPI
[12040.225901] ohci-pci 0000:00:13.0: System wakeup enabled by ACPI
[12040.226003] ehci-pci 0000:00:12.2: System wakeup enabled by ACPI
[12040.241898] ohci-pci 0000:00:12.0: System wakeup enabled by ACPI
[12040.242017] xhci_hcd 0000:00:10.1: System wakeup enabled by ACPI
[12040.257902] xhci_hcd 0000:00:10.0: System wakeup enabled by ACPI
[12040.273968] PM: noirq suspend of devices complete after 94.083 msecs
[12040.274040] ACPI: Preparing to enter system sleep state S3
[12040.286877] PM: Saving platform NVS memory
[12040.289362] Disabling non-boot CPUs ...
[12040.289945] Broke affinity for irq 51
[12040.393573] smpboot: CPU 1 is now offline
[12040.497548] smpboot: CPU 2 is now offline
[12040.601520] smpboot: CPU 3 is now offline
[12040.602241] ACPI: Low-level resume complete
[12040.602278] PM: Restoring platform NVS memory
[12040.603651] microcode: CPU0: new patch_level=0x03000027
[12040.603686] Enabling non-boot CPUs ...
[12040.603727] smpboot: Booting Node 0 Processor 1 APIC 0x1
[12040.614730] LVT offset 0 assigned for vector 0x400
[12040.617171] microcode: CPU1: new patch_level=0x03000027
[12040.617175] CPU1 is up
[12040.617190] smpboot: Booting Node 0 Processor 2 APIC 0x2
[12040.630514] microcode: CPU2: new patch_level=0x03000027
[12040.630517] CPU2 is up
[12040.630532] smpboot: Booting Node 0 Processor 3 APIC 0x3
[12040.643875] microcode: CPU3: new patch_level=0x03000027
[12040.643878] CPU3 is up
[12040.645234] ACPI: Waking up from system sleep state S3
[12040.699489] xhci_hcd 0000:00:10.0: System wakeup disabled by ACPI
[12040.715484] xhci_hcd 0000:00:10.1: System wakeup disabled by ACPI
[12040.715589] ohci-pci 0000:00:12.0: System wakeup disabled by ACPI
[12040.731470] ehci-pci 0000:00:12.2: System wakeup disabled by ACPI
[12040.731556] ohci-pci 0000:00:13.0: System wakeup disabled by ACPI
[12040.747465] ehci-pci 0000:00:13.2: System wakeup disabled by ACPI
[12040.795501] PM: noirq resume of devices complete after 124.788 msecs
[12040.795704] PM: early resume of devices complete after 0.110 msecs
[12040.797582] pciehp 0000:00:15.1:pcie04: No adapter on slot(0)
[12040.800853] snd_hda_intel 0000:00:01.1: irq 53 for MSI/MSI-X
[12040.803569] <6>[fglrx] Power up the ASIC
[12040.808812] <6>[fglrx] Preparing resume fglrx in kernel.
[12040.813997] <6>[fglrx] Resuming fglrx in kernel completed.
[12040.814040] <6>[fglrx] IRQ 54 Enabled
[12041.187277] usb 7-2: reset full-speed USB device number 6 using ohci-pci
[12041.247251] ata3: SATA link down (SStatus 0 SControl 300)
[12041.344442] usb 7-2: device firmware changed
[12041.419266] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[12041.421699] ata2.00: configured for UDMA/100
[12041.479201] usb 7-3: reset full-speed USB device number 3 using ohci-pci
[12043.222799] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[12043.462737] ata1.00: configured for UDMA/133
[12043.478876] sd 0:0:0:0: [sda] Starting disk
[12043.506331] PM: resume of devices complete after 2711.286 msecs
[12043.506584] PM: Finishing wakeup.
[12043.506586] Restarting tasks ... done.
[12043.507606] usb 2-3: USB disconnect, device number 8
[12043.547993] video LNXVIDEO:01: Restoring backlight state
[12043.798652] usb 2-3: new high-speed USB device number 10 using ehci-pci
[12044.081095] usb 2-3: New USB device found, idVendor=05ca, idProduct=181d
[12044.081101] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[12044.081104] usb 2-3: Product: Laptop_Integrated_Webcam_FHD
[12044.081105] usb 2-3: Manufacturer: CKFA228h475010006CQ0
[12044.081903] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_FHD (05ca:181d)
[12044.083447] input: Laptop_Integrated_Webcam_FHD as /devices/pci0000:00/0000:00:13.2/usb2/2-3/2-3:1.0/input/input17
[12044.194365] usb 2-5: new high-speed USB device number 11 using ehci-pci
[12044.584429] usb 2-5: New USB device found, idVendor=0bda, idProduct=0138
[12044.584442] usb 2-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[12044.584449] usb 2-5: Product: USB2.0-CRW
[12044.584454] usb 2-5: Manufacturer: Generic
[12044.584459] usb 2-5: SerialNumber: 20090516388200000
[12044.591520] ums-realtek 2-5:1.0: USB Mass Storage device detected
[12044.620044] scsi9 : usb-storage 2-5:1.0
[12044.620431] usb 7-2: USB disconnect, device number 6
[12044.730260] r8169 0000:01:00.0 eth0: link down
[12044.730434] r8169 0000:01:00.0 eth0: link down
[12044.730498] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[12044.758356] usb 7-2: new full-speed USB device number 7 using ohci-pci
[12044.781161] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[12044.781182] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[12044.781460] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[12044.933421] usb 7-2: New USB device found, idVendor=0a5c, idProduct=21bc
[12044.933435] usb 7-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[12044.933442] usb 7-2: Product: Dell Wireless 1701 Bluetooth
[12044.933447] usb 7-2: Manufacturer: Broadcom Corp
[12044.933451] usb 7-2: SerialNumber: 7CE9D3D40916
[12044.937012] usb 2-5: USB disconnect, device number 11
[12045.662590] atkbd serio0: Unknown key pressed (translated set 2, code 0x8d on isa0060/serio0).
[12045.662603] atkbd serio0: Use 'setkeycodes e00d <keycode>' to make it known.
[12046.568190] wlan0: authenticate with d8:6c:e9:2d:0f:31
[12046.568376] wlan0: send auth to d8:6c:e9:2d:0f:31 (try 1/3)
[12046.569947] wlan0: authenticated
[12046.573864] wlan0: associate with d8:6c:e9:2d:0f:31 (try 1/3)
[12046.578281] wlan0: RX AssocResp from d8:6c:e9:2d:0f:31 (capab=0xc11 status=0 aid=1)
[12046.578737] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[12046.578747] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[12046.578772] wlan0: associated
[12046.578861] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[12046.579022] cfg80211: Calling CRDA for country: CA
[12046.585853] cfg80211: Regulatory domain changed to country: CA
[12046.585863] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[12046.585870] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[12046.585876] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[12046.585881] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[12046.585885] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[12046.585890] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[12047.925638] r8169 0000:01:00.0 eth0: link up
[12047.925662] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[12049.647831] VFS: busy inodes on changed media or resized disk sr0
[12049.952219] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[12061.014476] usb 3-2: new low-speed USB device number 3 using xhci_hcd
[12061.070720] usb 3-2: New USB device found, idVendor=045e, idProduct=0040
[12061.070733] usb 3-2: New USB device strings: Mfr=1, Product=3, SerialNumber=0
[12061.070740] usb 3-2: Product: Microsoft 3-Button Mouse with IntelliEye(TM)
[12061.070745] usb 3-2: Manufacturer: Microsoft
[12061.071049] usb 3-2: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[12061.086683] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:10.0/usb3/3-2/3-2:1.0/input/input18
[12061.087405] hid-generic 0003:045E:0040.0002: input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:10.0-2/input0
[12130.533406] usb 5-2: new high-speed USB device number 2 using xhci_hcd
[12130.564690] usb 5-2: New USB device found, idVendor=1949, idProduct=0004
[12130.564703] usb 5-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[12130.564709] usb 5-2: Product: Amazon Kindle
[12130.564714] usb 5-2: Manufacturer: Amazon
[12130.564719] usb 5-2: SerialNumber: B008A0A003530035
[12130.569742] usb-storage 5-2:1.0: USB Mass Storage device detected
[12130.570215] scsi10 : usb-storage 5-2:1.0
[12131.571502] scsi 10:0:0:0: Direct-Access     Kindle   Internal Storage 0100 PQ: 0 ANSI: 2
[12131.572381] sd 10:0:0:0: Attached scsi generic sg2 type 0
[12131.577295] sd 10:0:0:0: [sdb] 6410688 512-byte logical blocks: (3.28 GB/3.05 GiB)
[12131.680525] sd 10:0:0:0: [sdb] Write Protect is off
[12131.680541] sd 10:0:0:0: [sdb] Mode Sense: 0f 00 00 00
[12131.790468] sd 10:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[12132.011370]  sdb: sdb1
[12132.280349] sd 10:0:0:0: [sdb] Attached SCSI removable disk
[12132.873596] FAT-fs (sdb1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
[12144.221725] sdb: detected capacity change from 3282272256 to 0
[13921.879830] type=1400 audit(1388253722.456:73): apparmor="STATUS" operation="profile_replace" parent=8281 profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=8285 comm="apparmor_parser"
[13921.879863] type=1400 audit(1388253722.456:74): apparmor="STATUS" operation="profile_replace" parent=8281 profile="unconfined" name="/usr/sbin/cupsd" pid=8285 comm="apparmor_parser"
[13921.882122] type=1400 audit(1388253722.460:75): apparmor="STATUS" operation="profile_replace" parent=8281 profile="unconfined" name="/usr/sbin/cupsd" pid=8285 comm="apparmor_parser"
[16501.746046] wlan0: deauthenticating from d8:6c:e9:2d:0f:31 by local choice (reason=3)
[16501.748325] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[16501.748345] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[16501.748351] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[16501.749421] cfg80211: Calling CRDA to update world regulatory domain
[16501.757161] cfg80211: World regulatory domain updated:
[16501.757172] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[16501.757179] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[16501.757185] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[16501.757190] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[16501.757195] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[16501.757199] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[16503.863127] PM: Syncing filesystems ... done.
[16504.155041] PM: Preparing system for mem sleep
[16504.155445] Freezing user space processes ... (elapsed 0.001 seconds) done.
[16504.156885] Freezing remaining freezable tasks ... (elapsed 0.001 seconds) done.
[16504.158135] PM: Entering mem sleep
[16504.158263] Suspending console(s) (use no_console_suspend to debug)
[16504.158531] sd 10:0:0:0: [sdb] Synchronizing SCSI cache
[16504.159046] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[16504.165828] sd 10:0:0:0: [sdb]  
[16504.165832] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[16504.165836] sd 10:0:0:0: [sdb]  
[16504.165840] Sense Key : Not Ready [current] 
[16504.165842] sd 10:0:0:0: [sdb]  
[16504.165848] Add. Sense: Medium not present
[16504.165872] dpm_run_callback(): scsi_bus_suspend+0x0/0x40 returns -5
[16504.165886] PM: Device 10:0:0:0 failed to suspend async: error -5
[16504.185635] sd 0:0:0:0: [sda] Stopping disk
[16504.561592] PM: Some devices failed to suspend, or early wake event detected
[16504.564234] sd 0:0:0:0: [sda] Starting disk
[16504.564914] hub 2-0:1.0: hub_port_status failed (err = -113)
[16504.564918] hub 2-0:1.0: cannot disable port 3 (err = -113)
[16504.564926] dpm_run_callback(): usb_dev_resume+0x0/0x20 returns -113
[16504.564929] PM: Device 2-3 failed to resume async: error -113
[16504.784274] usb 7-3: reset full-speed USB device number 3 using ohci-pci
[16504.884243] ata3: SATA link down (SStatus 0 SControl 300)
[16505.052234] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[16505.062045] ata2.00: configured for UDMA/100
[16505.084144] usb 7-2: reset full-speed USB device number 7 using ohci-pci
[16505.488921] PM: resume of devices complete after 927.546 msecs
[16505.489146] PM: Finishing wakeup.
[16505.489269] usb 2-3: USB disconnect, device number 10
[16505.489147] Restarting tasks ... done.
[16505.508458] video LNXVIDEO:01: Restoring backlight state
[16505.635846] usb 2-3: new high-speed USB device number 12 using ehci-pci
[16505.775563] usb 2-3: New USB device found, idVendor=05ca, idProduct=181d
[16505.775569] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[16505.775571] usb 2-3: Product: Laptop_Integrated_Webcam_FHD
[16505.775573] usb 2-3: Manufacturer: CKFA228h475010006CQ0
[16505.776534] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_FHD (05ca:181d)
[16505.778273] input: Laptop_Integrated_Webcam_FHD as /devices/pci0000:00/0000:00:13.2/usb2/2-3/2-3:1.0/input/input19
[16506.715230] r8169 0000:01:00.0 eth0: link down
[16506.715259] r8169 0000:01:00.0 eth0: link down
[16506.715361] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[16506.760129] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[16506.760138] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[16506.760267] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[16508.528618] wlan0: authenticate with d8:6c:e9:2d:0f:31
[16508.529112] wlan0: send auth to d8:6c:e9:2d:0f:31 (try 1/3)
[16508.531399] wlan0: authenticated
[16508.535282] wlan0: associate with d8:6c:e9:2d:0f:31 (try 1/3)
[16508.539801] wlan0: RX AssocResp from d8:6c:e9:2d:0f:31 (capab=0xc11 status=0 aid=1)
[16508.540281] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[16508.540291] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[16508.540323] wlan0: associated
[16508.540402] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[16508.540621] cfg80211: Calling CRDA for country: CA
[16508.547322] cfg80211: Regulatory domain changed to country: CA
[16508.547332] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[16508.547339] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[16508.547345] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[16508.547350] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[16508.547354] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[16508.547359] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[16508.848249] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[16509.059599] r8169 0000:01:00.0 eth0: link up
[16509.059622] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[16540.357140] usb 5-2: USB disconnect, device number 2
[16540.358384] sd 10:0:0:0: [sdb] Synchronizing SCSI cache
[16540.358595] sd 10:0:0:0: [sdb]  
[16540.358609] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK

```

Even more frequently when the system has suspended it won't resume!  The blank screen just sits there because the drivers, both the lousy one from AMD and the open code one, just cannot seem to figure out how to make the display come one when the laptop opens.  And I am left with the only option to reboot the operating system and losing everything I was working on.  I am one frustrated puppy!:mad:

```
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] BeaverCreek [Radeon HD 6620G]
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] BeaverCreek HDMI Audio [Radeon HD 6500D and 6400G-6600G series]
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 12h Processor Root Port
00:06.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 12h Processor Root Port
00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 03)
00:10.1 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 03)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 13)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD] FCH IDE Controller
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] FCH PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:14.7 SD Host controller: Advanced Micro Devices, Inc. [AMD] FCH SD Flash Controller
00:15.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Hudson PCI to PCI bridge (PCIE port 0)
00:15.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Hudson PCI to PCI bridge (PCIE port 1)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 7
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter (rev 01)

```

---

### Post by Toz on 2013-12-28
From your dmesg:
> [    0.000000] ACPI BIOS Warning (bug): Optional FADT field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20130517/tbfadt-603)
FADT is an ACPI table structure that contains info about system power management. It may be related to the problem you are experiencing. 

> [    0.000000] DMI: Dell Inc. Vostro 3555/0K89MF, BIOS A04 10/24/2011
First, I would look to see if a bios update is available for your laptop that might fix this issue.

If one does not exist or if it doesn't fix the problem, I would look at trying kernel boot parameters like:
- acpi_osi=
- acpi_osi=Linux
- acpi_osi=\"!Windows 2012\"
...to see if they will load an alternate set of tables.

---

### Post by 7-webmaster on 2014-01-08
> **Toz said:**
> From your dmesg:

FADT is an ACPI table structure that contains info about system power management. It may be related to the problem you are experiencing. 


First, I would look to see if a bios update is available for your laptop that might fix this issue.

If one does not exist or if it doesn't fix the problem, I would look at trying kernel boot parameters like:
- acpi_osi=
- acpi_osi=Linux
- acpi_osi=\"!Windows 2012\"
...to see if they will load an alternate set of tables.

Thank you for looking at this problem.

I cannot find a BIOS fix on the Dell site.  I haven't the foggiest idea of what a kernel boot parameter is or how to change it even after reading the various web pages on the subject.  I have grep'ed /boot/*, /boot/grub/*, and /etc/default/grub and cannot find any occurrence of the string "acpi_osi".

---

### Post by Toz on 2014-01-08
> **7-webmaster said:**
> I haven't the foggiest idea of what a kernel boot parameter is or how to change it even after reading the various web pages on the subject.  I have grep'ed /boot/*, /boot/grub/*, and /etc/default/grub and cannot find any occurrence of the string "acpi_osi".

Follow the "Temporarily Add a Kernel Boot Parameter for Testing" instructions at the [Kernel Boot Parameters wiki]("https://wiki.ubuntu.com/Kernel/KernelBootParameters") to temporarily test out each parameter.

---

### Post by Bucky Ball on 2014-11-02
Thread closed.

See here: [http://ubuntuforums.org/showthread.php?t=2251048](http://ubuntuforums.org/showthread.php?t=2251048)

---

