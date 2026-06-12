---
title: "USB delay to being found: new high-speed USB device number 116 using ehci-pci"
date: 2015-04-30
forum: Hardware
---

### Post by samuelsimon on 2015-04-30
On startup the computer is very slow to recognise attached USB devices, specifically a Zyxel G-202 USB dongle. I am running ubuntu 15.04 64bit (although the problem existed before the upgrade) on a lenovo ThinkCentre. Any suggestions would be greatly appreciated.

dmseg shows the following message but repeated many times:

```
[  371.960052] usb 2-2: new high-speed USB device number 89 using ehci-pci
[  372.732071] usb 2-2: new high-speed USB device number 92 using ehci-pci
[  373.936036] usb 2-2: new high-speed USB device number 97 using ehci-pci
```

This continues for some time until the following is show:
```
[  387.396032] usb 2-2: new high-speed USB device number 27 using ehci-pci
[  387.764060] usb 6-2: new full-speed USB device number 3 using uhci_hcd
[  387.909860] usb 6-2: not running at top speed; connect to a high speed hub
[  387.937859] usb 6-2: New USB device found, idVendor=0586, idProduct=3410
[  387.937865] usb 6-2: New USB device strings: Mfr=16, Product=32, SerialNumber=0
[  387.937871] usb 6-2: Product: ZyXEL G-202
[  387.937875] usb 6-2: Manufacturer: ZyDAS

```

During this process I have control of the system and can attempt running lsusb or usb-devices in the terminal, both of which hang until the USB device is recognised.

The full output of dmseg is as follows:

```
[    0.000000] CPU0 microcode updated early to revision 0xa4, date = 2010-10-02
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.19.0-15-generic (buildd@komainu) (gcc version 4.9.2 (Ubuntu 4.9.2-10ubuntu13) ) #15-Ubuntu SMP Thu Apr 16 23:32:37 UTC 2015 (Ubuntu 3.19.0-15.15-generic 3.19.3)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-15-generic root=UUID=3f7841df-59ca-4d21-90a9-3f6404a53584 ro
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009dfff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009e000-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000bf5affff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bf5b0000-0x00000000bf5c8fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000bf5c9000-0x00000000bf5cbfff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bf5cc000-0x00000000bf7fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec0ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000022fffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.5 present.
[    0.000000] DMI: LENOVO 6072WRW/LENOVO, BIOS 2RKT38AUS 02/15/2008
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] AGP: No AGP bridge found
[    0.000000] e820: last_pfn = 0x230000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-E3FFF uncachable
[    0.000000]   E4000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 100000000 mask F00000000 write-back
[    0.000000]   3 base 200000000 mask FE0000000 write-back
[    0.000000]   4 base 220000000 mask FF0000000 write-back
[    0.000000]   5 base 0BF600000 mask FFFE00000 uncachable
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- UC  
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 4GB, range: 4GB, type WB
[    0.000000] reg 3, base: 8GB, range: 512MB, type WB
[    0.000000] reg 4, base: 8704MB, range: 256MB, type WB
[    0.000000] reg 5, base: 3062MB, range: 2MB, type UC
[    0.000000] total RAM covered: 7934M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 16M     num_reg: 6      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3062MB, range: 2MB, type UC
[    0.000000] reg 3, base: 4GB, range: 4GB, type WB
[    0.000000] reg 4, base: 8GB, range: 512MB, type WB
[    0.000000] reg 5, base: 8704MB, range: 256MB, type WB
[    0.000000] e820: update [mem 0xbf600000-0xbf7fffff] usable ==> reserved
[    0.000000] e820: update [mem 0xc0000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xbf5b0 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000f6030-0x000f603f] mapped at [ffff8800000f6030]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fe5000, 0x01fe5fff] PGTABLE
[    0.000000] BRK [0x01fe6000, 0x01fe6fff] PGTABLE
[    0.000000] BRK [0x01fe7000, 0x01fe7fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x22fe00000-0x22fffffff]
[    0.000000]  [mem 0x22fe00000-0x22fffffff] page 2M
[    0.000000] BRK [0x01fe8000, 0x01fe8fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x220000000-0x22fdfffff]
[    0.000000]  [mem 0x220000000-0x22fdfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x200000000-0x21fffffff]
[    0.000000]  [mem 0x200000000-0x21fffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0xbf5affff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0xbf3fffff] page 2M
[    0.000000]  [mem 0xbf400000-0xbf5affff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x1ffffffff]
[    0.000000]  [mem 0x100000000-0x1ffffffff] page 2M
[    0.000000] BRK [0x01fe9000, 0x01fe9fff] PGTABLE
[    0.000000] BRK [0x01fea000, 0x01feafff] PGTABLE
[    0.000000] RAMDISK: [mem 0x3583c000-0x36c15fff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000000F5E20 000024 (v02 PTLTD )
[    0.000000] ACPI: XSDT 0x00000000BF5BD89C 0000B4 (v01 LENOVO TC-2R    060400D0  LTP 00000000)
[    0.000000] ACPI: TCPA 0x00000000BF5C8BB9 000032 (v02 LENOVO TC-2R    060400D0 PTL  00000000)
[    0.000000] ACPI: FACP 0x00000000BF5C8BEB 0000F4 (v03 INTEL           060400D0 PTL  00000003)
[    0.000000] ACPI: DSDT 0x00000000BF5C1019 007B2C (v01 INTEL  BEARLAKE 060400D0 MSFT 0100000E)
[    0.000000] ACPI: FACS 0x00000000BF5CBFC0 000040
[    0.000000] ACPI: _MAR 0x00000000BF5C8CDF 000030 (v01 Intel  OEMDMAR  060400D0 LOHR 00000001)
[    0.000000] ACPI: SLIC 0x00000000BF5C8D0F 000176 (v01 LENOVO TC-2R    060400D0  LTP 00000000)
[    0.000000] ACPI: MCFG 0x00000000BF5C8E85 00003C (v01 PTLTD    MCFG   060400D0  LTP 00000000)
[    0.000000] ACPI: HPET 0x00000000BF5C8EC1 000038 (v01 PTLTD  HPETTBL  060400D0  LTP 00000001)
[    0.000000] ACPI: APIC 0x00000000BF5C8EF9 000068 (v01 PTLTD  ? APIC   060400D0  LTP 00000000)
[    0.000000] ACPI: BOOT 0x00000000BF5C8F61 000028 (v01 PTLTD  $SBFTBL$ 060400D0  LTP 00000001)
[    0.000000] ACPI: ASF! 0x00000000BF5C8F89 000077 (v16   CETP     CETP 060400D0 PTL  00000001)
[    0.000000] ACPI: SSDT 0x00000000BF5BF1DF 00025F (v01 PmRef  Cpu0Tst  00003000 INTL 20050228)
[    0.000000] ACPI: SSDT 0x00000000BF5BF139 0000A6 (v01 PmRef  Cpu7Tst  00003000 INTL 20050228)
[    0.000000] ACPI: SSDT 0x00000000BF5BF093 0000A6 (v01 PmRef  Cpu6Tst  00003000 INTL 20050228)
[    0.000000] ACPI: SSDT 0x00000000BF5BEFED 0000A6 (v01 PmRef  Cpu5Tst  00003000 INTL 20050228)
[    0.000000] ACPI: SSDT 0x00000000BF5BEF47 0000A6 (v01 PmRef  Cpu4Tst  00003000 INTL 20050228)
[    0.000000] ACPI: SSDT 0x00000000BF5BEEA1 0000A6 (v01 PmRef  Cpu3Tst  00003000 INTL 20050228)
[    0.000000] ACPI: SSDT 0x00000000BF5BEDFB 0000A6 (v01 PmRef  Cpu2Tst  00003000 INTL 20050228)
[    0.000000] ACPI: SSDT 0x00000000BF5BED55 0000A6 (v01 PmRef  Cpu1Tst  00003000 INTL 20050228)
[    0.000000] ACPI: SSDT 0x00000000BF5BD950 001405 (v01 PmRef  CpuPm    00003000 INTL 20050228)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000022fffffff]
[    0.000000] NODE_DATA(0) allocated [mem 0x22fff6000-0x22fffafff]
[    0.000000]  [ffffea0000000000-ffffea0008bfffff] PMD -> [ffff880227a00000-ffff88022f5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x22fffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009dfff]
[    0.000000]   node   0: [mem 0x00100000-0xbf5affff]
[    0.000000]   node   0: [mem 0x100000000-0x22fffffff]
[    0.000000] Initmem setup node 0 [mem 0x00001000-0x22fffffff]
[    0.000000] On node 0 totalpages: 2028877
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3997 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 12183 pages used for memmap
[    0.000000]   DMA32 zone: 779696 pages, LIFO batch:31
[    0.000000]   Normal zone: 19456 pages used for memmap
[    0.000000]   Normal zone: 1245184 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
[    0.000000] smpboot: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xbf5b0000-0xbf5c8fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbf5c9000-0xbf5cbfff]
[    0.000000] PM: Registered nosave memory: [mem 0xbf5cc000-0xbf7fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xbf800000-0xdfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec0ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec10000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xfeffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
[    0.000000] e820: [mem 0xbf800000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 31 pages/cpu @ffff88022fc00000 s87040 r8192 d31744 u1048576
[    0.000000] pcpu-alloc: s87040 r8192 d31744 u1048576 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1997153
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-15-generic root=UUID=3f7841df-59ca-4d21-90a9-3f6404a53584 ro
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] AGP: Checking aperture...
[    0.000000] AGP: No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 7885232K/8115508K available (7993K kernel code, 1232K rwdata, 3752K rodata, 1408K init, 1300K bss, 230276K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=2.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=2
[    0.000000] NR_IRQS:16640 nr_irqs:440 16
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-1.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 2194.593 MHz processor
[    0.004014] Calibrating delay loop (skipped), value calculated using timer frequency.. 4389.18 BogoMIPS (lpj=8778372)
[    0.004105] pid_max: default: 32768 minimum: 301
[    0.004157] ACPI: Core revision 20141107
[    0.011240] ACPI: All ACPI Tables successfully acquired
[    0.012033] Security Framework initialized
[    0.012099] AppArmor: AppArmor initialized
[    0.012143] Yama: becoming mindful.
[    0.012978] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.018112] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.020269] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.020337] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.020823] Initializing cgroup subsys memory
[    0.020876] Initializing cgroup subsys devices
[    0.020924] Initializing cgroup subsys freezer
[    0.020970] Initializing cgroup subsys net_cls
[    0.021017] Initializing cgroup subsys blkio
[    0.021063] Initializing cgroup subsys perf_event
[    0.021109] Initializing cgroup subsys net_prio
[    0.021156] Initializing cgroup subsys hugetlb
[    0.021230] CPU: Physical Processor ID: 0
[    0.021274] CPU: Processor Core ID: 0
[    0.021319] mce: CPU supports 6 MCE banks
[    0.021369] CPU0: Thermal monitoring handled by SMI
[    0.021378] Last level iTLB entries: 4KB 128, 2MB 4, 4MB 4
Last level dTLB entries: 4KB 256, 2MB 0, 4MB 32, 1GB 0
[    0.021549] Freeing SMP alternatives memory: 32K (ffffffff81e96000 - ffffffff81e9e000)
[    0.023090] ftrace: allocating 30078 entries in 118 pages
[    0.032506] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.075656] smpboot: CPU0: Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz (fam: 06, model: 0f, stepping: 0d)
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
[    0.008000] CPU1 microcode updated early to revision 0xa4, date = 2010-10-02
[    0.008000] CPU1: Thermal monitoring handled by SMI
[    0.087241] x86: Booted up 1 node, 2 CPUs
[    0.087376] smpboot: Total of 2 processors activated (8778.37 BogoMIPS)
[    0.088052] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.089439] devtmpfs: initialized
[    0.091175] evm: security.selinux
[    0.091220] evm: security.SMACK64
[    0.091262] evm: security.SMACK64EXEC
[    0.091305] evm: security.SMACK64TRANSMUTE
[    0.091349] evm: security.SMACK64MMAP
[    0.091392] evm: security.ima
[    0.091434] evm: security.capability
[    0.092026] PM: Registering ACPI NVS region [mem 0xbf5c9000-0xbf5cbfff] (12288 bytes)
[    0.092213] pinctrl core: initialized pinctrl subsystem
[    0.092225] RTC time:  6:44:28, date: 04/30/15
[    0.092225] NET: Registered protocol family 16
[    0.100011] cpuidle: using governor ladder
[    0.104011] cpuidle: using governor menu
[    0.104130] ACPI: bus type PCI registered
[    0.104183] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.104321] PCI: MMCONFIG for domain 0000 [bus 00-10] at [mem 0xe0000000-0xe10fffff] (base 0xe0000000)
[    0.104381] PCI: MMCONFIG at [mem 0xe0000000-0xe10fffff] reserved in E820
[    0.104467] PCI: Using configuration type 1 for base access
[    0.108120] ACPI: Added _OSI(Module Device)
[    0.108167] ACPI: Added _OSI(Processor Device)
[    0.108212] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.108256] ACPI: Added _OSI(Processor Aggregator Device)
[    0.112306] ACPI: Dynamic OEM Table Load:
[    0.112418] ACPI: SSDT 0xFFFF880226775C00 00021F (v01 PmRef  Cpu0Ist  00003000 INTL 20050228)
[    0.113063] ACPI: Dynamic OEM Table Load:
[    0.113173] ACPI: SSDT 0xFFFF880226773600 0001B0 (v01 PmRef  Cpu1Ist  00003000 INTL 20050228)
[    0.113740] ACPI: Interpreter enabled
[    0.113789] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20141107/hwxface-580)
[    0.113909] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20141107/hwxface-580)
[    0.114038] ACPI: (supports S0 S3 S4 S5)
[    0.114083] ACPI: Using IOAPIC for interrupt routing
[    0.114153] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.121223] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3f])
[    0.121276] acpi PNP0A03:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.121387] ACPI Error: [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS (20141107/dsfield-211)
[    0.121538] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node ffff88022749a708), AE_ALREADY_EXISTS (20141107/psparse-536)
[    0.121726] acpi PNP0A03:00: _OSC failed (AE_ALREADY_EXISTS); disabling ASPM
[    0.122715] acpi PNP0A03:00: host bridge window expanded to [mem 0xc0000000-0xfffffffe]; [mem 0xc0000000-0xfffffffe] ignored
[    0.122783] acpi PNP0A03:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-10] only partially covers this bridge
[    0.123073] PCI host bridge to bus 0000:00
[    0.123120] pci_bus 0000:00: root bus resource [bus 00-3f]
[    0.123166] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.123213] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.123260] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    0.123308] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    0.123355] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    0.123402] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    0.123450] pci_bus 0000:00: root bus resource [io  0x0d00-0xfdff]
[    0.123496] pci_bus 0000:00: root bus resource [mem 0xc0000000-0xfffffffe]
[    0.123552] pci 0000:00:00.0: [8086:29b0] type 00 class 0x060000
[    0.123685] pci 0000:00:01.0: [8086:29b1] type 01 class 0x060400
[    0.123736] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.123847] pci 0000:00:03.0: [8086:29b4] type 00 class 0x078000
[    0.123865] pci 0000:00:03.0: reg 0x10: [mem 0xd3326000-0xd332600f 64bit]
[    0.123916] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    0.124021] pci 0000:00:03.2: [8086:29b6] type 00 class 0x010185
[    0.124033] pci 0000:00:03.2: reg 0x10: [io  0x1c80-0x1c87]
[    0.124039] pci 0000:00:03.2: reg 0x14: [io  0x1c74-0x1c77]
[    0.124045] pci 0000:00:03.2: reg 0x18: [io  0x1c78-0x1c7f]
[    0.124051] pci 0000:00:03.2: reg 0x1c: [io  0x1c70-0x1c73]
[    0.124057] pci 0000:00:03.2: reg 0x20: [io  0x1c20-0x1c2f]
[    0.124184] pci 0000:00:03.3: [8086:29b7] type 00 class 0x070002
[    0.124197] pci 0000:00:03.3: reg 0x10: [io  0x1c88-0x1c8f]
[    0.124205] pci 0000:00:03.3: reg 0x14: [mem 0xd3324000-0xd3324fff]
[    0.124375] pci 0000:00:19.0: [8086:10bd] type 00 class 0x020000
[    0.124395] pci 0000:00:19.0: reg 0x10: [mem 0xd3300000-0xd331ffff]
[    0.124404] pci 0000:00:19.0: reg 0x14: [mem 0xd3325000-0xd3325fff]
[    0.124413] pci 0000:00:19.0: reg 0x18: [io  0x1820-0x183f]
[    0.124482] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.124539] pci 0000:00:19.0: System wakeup disabled by ACPI
[    0.124639] pci 0000:00:1a.0: [8086:2937] type 00 class 0x0c0300
[    0.124685] pci 0000:00:1a.0: reg 0x20: [io  0x1840-0x185f]
[    0.124791] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.124895] pci 0000:00:1a.1: [8086:2938] type 00 class 0x0c0300
[    0.124940] pci 0000:00:1a.1: reg 0x20: [io  0x1860-0x187f]
[    0.125046] pci 0000:00:1a.1: System wakeup disabled by ACPI
[    0.125148] pci 0000:00:1a.2: [8086:2939] type 00 class 0x0c0300
[    0.125193] pci 0000:00:1a.2: reg 0x20: [io  0x1880-0x189f]
[    0.125299] pci 0000:00:1a.2: System wakeup disabled by ACPI
[    0.125409] pci 0000:00:1a.7: [8086:293c] type 00 class 0x0c0320
[    0.125432] pci 0000:00:1a.7: reg 0x10: [mem 0xd3326800-0xd3326bff]
[    0.125530] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.125589] pci 0000:00:1a.7: System wakeup disabled by ACPI
[    0.125696] pci 0000:00:1b.0: [8086:293e] type 00 class 0x040300
[    0.125715] pci 0000:00:1b.0: reg 0x10: [mem 0xd3320000-0xd3323fff 64bit]
[    0.125794] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.125903] pci 0000:00:1d.0: [8086:2934] type 00 class 0x0c0300
[    0.125958] pci 0000:00:1d.0: reg 0x20: [io  0x18a0-0x18bf]
[    0.126074] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.126177] pci 0000:00:1d.1: [8086:2935] type 00 class 0x0c0300
[    0.126233] pci 0000:00:1d.1: reg 0x20: [io  0x18c0-0x18df]
[    0.126349] pci 0000:00:1d.1: System wakeup disabled by ACPI
[    0.126451] pci 0000:00:1d.2: [8086:2936] type 00 class 0x0c0300
[    0.126496] pci 0000:00:1d.2: reg 0x20: [io  0x18e0-0x18ff]
[    0.126605] pci 0000:00:1d.2: System wakeup disabled by ACPI
[    0.126715] pci 0000:00:1d.7: [8086:293a] type 00 class 0x0c0320
[    0.126738] pci 0000:00:1d.7: reg 0x10: [mem 0xd3326c00-0xd3326fff]
[    0.126835] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.126895] pci 0000:00:1d.7: System wakeup disabled by ACPI
[    0.126995] pci 0000:00:1e.0: [8086:244e] type 01 class 0x060401
[    0.127096] pci 0000:00:1e.0: System wakeup disabled by ACPI
[    0.127199] pci 0000:00:1f.0: [8086:2914] type 00 class 0x060100
[    0.127283] pci 0000:00:1f.0: can't claim BAR 13 [io  0x1000-0x107f]: address conflict with ACPI CPU throttle [io  0x1010-0x1015]
[    0.127349] pci 0000:00:1f.0: quirk: [io  0x1180-0x11bf] claimed by ICH6 GPIO
[    0.127398] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0500 (mask 007f)
[    0.127584] pci 0000:00:1f.2: [8086:2920] type 00 class 0x01018a
[    0.127601] pci 0000:00:1f.2: reg 0x10: [io  0x0000-0x0007]
[    0.127610] pci 0000:00:1f.2: reg 0x14: [io  0x0000-0x0003]
[    0.127619] pci 0000:00:1f.2: reg 0x18: [io  0x0000-0x0007]
[    0.127627] pci 0000:00:1f.2: reg 0x1c: [io  0x0000-0x0003]
[    0.127636] pci 0000:00:1f.2: reg 0x20: [io  0x1c40-0x1c4f]
[    0.127645] pci 0000:00:1f.2: reg 0x24: [io  0x1c30-0x1c3f]
[    0.127657] pci 0000:00:1f.2: legacy IDE quirk: reg 0x10: [io  0x01f0-0x01f7]
[    0.127705] pci 0000:00:1f.2: legacy IDE quirk: reg 0x14: [io  0x03f6]
[    0.127752] pci 0000:00:1f.2: legacy IDE quirk: reg 0x18: [io  0x0170-0x0177]
[    0.127800] pci 0000:00:1f.2: legacy IDE quirk: reg 0x1c: [io  0x0376]
[    0.127967] pci 0000:00:1f.3: [8086:2930] type 00 class 0x0c0500
[    0.127983] pci 0000:00:1f.3: reg 0x10: [mem 0xd3327000-0xd33270ff 64bit]
[    0.128006] pci 0000:00:1f.3: reg 0x20: [io  0x1c00-0x1c1f]
[    0.128122] pci 0000:00:1f.5: [8086:2926] type 00 class 0x010185
[    0.128139] pci 0000:00:1f.5: reg 0x10: [io  0x1cb8-0x1cbf]
[    0.128148] pci 0000:00:1f.5: reg 0x14: [io  0x1cac-0x1caf]
[    0.128157] pci 0000:00:1f.5: reg 0x18: [io  0x1cb0-0x1cb7]
[    0.128166] pci 0000:00:1f.5: reg 0x1c: [io  0x1ca8-0x1cab]
[    0.128174] pci 0000:00:1f.5: reg 0x20: [io  0x1c60-0x1c6f]
[    0.128183] pci 0000:00:1f.5: reg 0x24: [io  0x1c50-0x1c5f]
[    0.128366] pci 0000:01:00.0: [10de:0a65] type 00 class 0x030000
[    0.128379] pci 0000:01:00.0: reg 0x10: [mem 0xd2000000-0xd2ffffff]
[    0.128391] pci 0000:01:00.0: reg 0x14: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.128403] pci 0000:01:00.0: reg 0x1c: [mem 0xd0000000-0xd1ffffff 64bit pref]
[    0.128411] pci 0000:01:00.0: reg 0x24: [io  0x2000-0x207f]
[    0.128420] pci 0000:01:00.0: reg 0x30: [mem 0x00000000-0x0007ffff pref]
[    0.128526] pci 0000:01:00.1: [10de:0be3] type 00 class 0x040300
[    0.128538] pci 0000:01:00.1: reg 0x10: [mem 0xd3000000-0xd3003fff]
[    0.128684] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.128732] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    0.128735] pci 0000:00:01.0:   bridge window [mem 0xd2000000-0xd30fffff]
[    0.128740] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.128829] pci 0000:00:1e.0: PCI bridge to [bus 11] (subtractive decode)
[    0.128885] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.128888] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.128891] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.128893] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.128895] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.128898] pci 0000:00:1e.0:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.128900] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xfdff] (subtractive decode)
[    0.128903] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xfffffffe] (subtractive decode)
[    0.129271] ACPI: PCI Interrupt Link [LNKA] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.129729] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.130185] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.130641] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.131099] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.131627] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.132124] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.132651] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.133152] platform INT0800:00: failed to claim resource 0
[    0.133201] acpi INT0800:00: platform device creation failed: -16
[    0.133897] ACPI: Enabled 3 GPEs in block 00 to 3F
[    0.134126] vgaarb: setting as boot device: PCI:0000:01:00.0
[    0.134126] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.134126] vgaarb: loaded
[    0.134126] vgaarb: bridge control possible 0000:01:00.0
[    0.134126] SCSI subsystem initialized
[    0.134126] libata version 3.00 loaded.
[    0.134126] ACPI: bus type USB registered
[    0.134126] usbcore: registered new interface driver usbfs
[    0.134126] usbcore: registered new interface driver hub
[    0.134126] usbcore: registered new device driver usb
[    0.134126] PCI: Using ACPI for IRQ routing
[    0.134126] PCI: pci_cache_line_size set to 64 bytes
[    0.134126] Expanded resource reserved due to conflict with PCI Bus 0000:00
[    0.134126] e820: reserve RAM buffer [mem 0x0009e000-0x0009ffff]
[    0.134126] e820: reserve RAM buffer [mem 0xbf5b0000-0xbfffffff]
[    0.134126] NetLabel: Initializing
[    0.134126] NetLabel:  domain hash size = 128
[    0.136003] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.136066] NetLabel:  unlabeled traffic allowed by default
[    0.136138] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.136138] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.136284] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.138347] Switched to clocksource hpet
[    0.145969] AppArmor: AppArmor Filesystem Enabled
[    0.146131] pnp: PnP ACPI init
[    0.146498] system 00:00: [io  0x0110-0x0117] has been reserved
[    0.146547] system 00:00: [io  0x0500-0x057f] has been reserved
[    0.146594] system 00:00: [io  0x0800-0x080f] has been reserved
[    0.146641] system 00:00: [io  0x1000-0x107f] could not be reserved
[    0.146688] system 00:00: [io  0x1180-0x11bf] has been reserved
[    0.146735] system 00:00: [io  0x04d0-0x04d1] has been reserved
[    0.146782] system 00:00: [io  0xfe00] has been reserved
[    0.146832] system 00:00: [mem 0xfed11000-0xfed11fff] has been reserved
[    0.146880] system 00:00: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.146928] system 00:00: [mem 0xfed18000-0xfed1ffff] has been reserved
[    0.146975] system 00:00: [mem 0xe0000000-0xefffffff] has been reserved
[    0.147023] system 00:00: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.147071] system 00:00: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.147118] system 00:00: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.147166] system 00:00: [mem 0xfef00000-0xfeffffff] has been reserved
[    0.147215] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.147287] pnp 00:01: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.147972] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.148028] pnp 00:03: Plug and Play ACPI device, IDs WEC1000 PNP0c31 (active)
[    0.148073] pnp: PnP ACPI: found 4 devices
[    0.155371] pci 0000:00:1f.0: BAR 13: [io  0x1000-0x107f] has bogus alignment
[    0.155427] pci 0000:01:00.0: BAR 6: assigned [mem 0xd3080000-0xd30fffff pref]
[    0.155485] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.155531] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    0.155580] pci 0000:00:01.0:   bridge window [mem 0xd2000000-0xd30fffff]
[    0.155629] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.155689] pci 0000:00:1e.0: PCI bridge to [bus 11]
[    0.155743] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.155746] pci_bus 0000:00: resource 5 [mem 0x000a0000-0x000bffff]
[    0.155748] pci_bus 0000:00: resource 6 [mem 0x000d0000-0x000d3fff]
[    0.155750] pci_bus 0000:00: resource 7 [mem 0x000d4000-0x000d7fff]
[    0.155753] pci_bus 0000:00: resource 8 [mem 0x000d8000-0x000dbfff]
[    0.155755] pci_bus 0000:00: resource 9 [mem 0x000dc000-0x000dffff]
[    0.155757] pci_bus 0000:00: resource 10 [io  0x0d00-0xfdff]
[    0.155760] pci_bus 0000:00: resource 11 [mem 0xc0000000-0xfffffffe]
[    0.155762] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
[    0.155764] pci_bus 0000:01: resource 1 [mem 0xd2000000-0xd30fffff]
[    0.155767] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.155769] pci_bus 0000:11: resource 4 [io  0x0000-0x0cf7]
[    0.155772] pci_bus 0000:11: resource 5 [mem 0x000a0000-0x000bffff]
[    0.155774] pci_bus 0000:11: resource 6 [mem 0x000d0000-0x000d3fff]
[    0.155776] pci_bus 0000:11: resource 7 [mem 0x000d4000-0x000d7fff]
[    0.155778] pci_bus 0000:11: resource 8 [mem 0x000d8000-0x000dbfff]
[    0.155781] pci_bus 0000:11: resource 9 [mem 0x000dc000-0x000dffff]
[    0.155783] pci_bus 0000:11: resource 10 [io  0x0d00-0xfdff]
[    0.155785] pci_bus 0000:11: resource 11 [mem 0xc0000000-0xfffffffe]
[    0.155820] NET: Registered protocol family 2
[    0.156142] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
[    0.156506] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.156925] TCP: Hash tables configured (established 65536 bind 65536)
[    0.157025] TCP: reno registered
[    0.157082] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.157187] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.157380] NET: Registered protocol family 1
[    0.159409] pci 0000:01:00.0: Video device with shadowed ROM
[    0.159421] PCI: CLS 32 bytes, default 64
[    0.159547] Trying to unpack rootfs image as initramfs...
[    0.563770] Freeing initrd memory: 20328K (ffff88003583c000 - ffff880036c16000)
[    0.563876] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.563924] software IO TLB [mem 0xbb5b0000-0xbf5b0000] (64MB) mapped at [ffff8800bb5b0000-ffff8800bf5affff]
[    0.564056] Simple Boot Flag at 0x44 set to 0x1
[    0.564302] microcode: CPU0 sig=0x6fd, pf=0x1, revision=0xa4
[    0.564354] microcode: CPU1 sig=0x6fd, pf=0x1, revision=0xa4
[    0.564494] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.564586] Scanning for low memory corruption every 60 seconds
[    0.564994] futex hash table entries: 512 (order: 3, 32768 bytes)
[    0.565066] Initialise system trusted keyring
[    0.565137] audit: initializing netlink subsys (disabled)
[    0.565209] audit: type=2000 audit(1430376268.564:1): initialized
[    0.565647] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.568055] zpool: loaded
[    0.568098] zbud: loaded
[    0.568314] VFS: Disk quotas dquot_6.5.2
[    0.568408] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.569157] fuse init (API version 7.23)
[    0.569401] Key type big_key registered
[    0.569848] Key type asymmetric registered
[    0.570860] Asymmetric key parser 'x509' registered
[    0.570956] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.571051] io scheduler noop registered
[    0.571096] io scheduler deadline registered (default)
[    0.571185] io scheduler cfq registered
[    0.571578] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.571643] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.571743] intel_idle: does not run on family 6 model 15
[    0.571867] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/PNP0C0C:00/input/input0
[    0.571929] ACPI: Power Button [PWRB]
[    0.572043] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.572099] ACPI: Power Button [PWRF]
[    0.573715] GHES: HEST is not enabled!
[    0.573881] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.596042] 0000:00:03.3: ttyS4 at I/O 0x1c88 (irq = 17, base_baud = 115200) is a 16550A
[    0.596413] Linux agpgart interface v0.103
[    0.608038] tpm_tis 00:03: 1.2 TPM (device-id 0xFE, rev-id 70)
[    0.704049] tpm_tis 00:03: TPM is disabled/deactivated (0x6)
[    0.705899] brd: module loaded
[    0.706849] loop: module loaded
[    0.707077] ata_piix 0000:00:1f.2: version 2.13
[    0.707208] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.861022] scsi host0: ata_piix
[    0.861227] scsi host1: ata_piix
[    0.861336] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x1c40 irq 14
[    0.861385] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x1c48 irq 15
[    0.861594] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    1.016817] scsi host2: ata_piix
[    1.016977] scsi host3: ata_piix
[    1.017078] ata3: SATA max UDMA/133 cmd 0x1cb8 ctl 0x1cac bmdma 0x1c60 irq 18
[    1.017126] ata4: SATA max UDMA/133 cmd 0x1cb0 ctl 0x1ca8 bmdma 0x1c68 irq 18
[    1.017349] libphy: Fixed MDIO Bus: probed
[    1.017394] tun: Universal TUN/TAP device driver, 1.6
[    1.017438] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.017550] PPP generic driver version 2.4.2
[    1.017698] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.017748] ehci-pci: EHCI PCI platform driver
[    1.017957] ehci-pci 0000:00:1a.7: EHCI Host Controller
[    1.018009] ehci-pci 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    1.018077] ehci-pci 0000:00:1a.7: debug port 1
[    1.022017] ehci-pci 0000:00:1a.7: cache line size of 32 is not supported
[    1.022025] ehci-pci 0000:00:1a.7: irq 18, io mem 0xd3326800
[    1.032032] ehci-pci 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    1.032166] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.032220] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.032275] usb usb1: Product: EHCI Host Controller
[    1.032319] usb usb1: Manufacturer: Linux 3.19.0-15-generic ehci_hcd
[    1.032364] usb usb1: SerialNumber: 0000:00:1a.7
[    1.032554] hub 1-0:1.0: USB hub found
[    1.032605] hub 1-0:1.0: 6 ports detected
[    1.032978] ehci-pci 0000:00:1d.7: EHCI Host Controller
[    1.033028] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    1.033093] ehci-pci 0000:00:1d.7: debug port 1
[    1.037030] ehci-pci 0000:00:1d.7: cache line size of 32 is not supported
[    1.037045] ehci-pci 0000:00:1d.7: irq 16, io mem 0xd3326c00
[    1.048034] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.048167] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.048222] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.048277] usb usb2: Product: EHCI Host Controller
[    1.048321] usb usb2: Manufacturer: Linux 3.19.0-15-generic ehci_hcd
[    1.048366] usb usb2: SerialNumber: 0000:00:1d.7
[    1.048540] hub 2-0:1.0: USB hub found
[    1.048590] hub 2-0:1.0: 6 ports detected
[    1.048825] ehci-platform: EHCI generic platform driver
[    1.048881] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.048929] ohci-pci: OHCI PCI platform driver
[    1.048986] ohci-platform: OHCI generic platform driver
[    1.049039] uhci_hcd: USB Universal Host Controller Interface driver
[    1.049223] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.049273] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    1.049333] uhci_hcd 0000:00:1a.0: detected 2 ports
[    1.049394] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001840
[    1.049487] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.049534] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.049589] usb usb3: Product: UHCI Host Controller
[    1.049633] usb usb3: Manufacturer: Linux 3.19.0-15-generic uhci_hcd
[    1.049678] usb usb3: SerialNumber: 0000:00:1a.0
[    1.049852] hub 3-0:1.0: USB hub found
[    1.049903] hub 3-0:1.0: 2 ports detected
[    1.050178] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.050228] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    1.050290] uhci_hcd 0000:00:1a.1: detected 2 ports
[    1.050359] uhci_hcd 0000:00:1a.1: irq 17, io base 0x00001860
[    1.050451] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.050498] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.050553] usb usb4: Product: UHCI Host Controller
[    1.050597] usb usb4: Manufacturer: Linux 3.19.0-15-generic uhci_hcd
[    1.050642] usb usb4: SerialNumber: 0000:00:1a.1
[    1.050808] hub 4-0:1.0: USB hub found
[    1.050857] hub 4-0:1.0: 2 ports detected
[    1.051128] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    1.051177] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    1.051237] uhci_hcd 0000:00:1a.2: detected 2 ports
[    1.051297] uhci_hcd 0000:00:1a.2: irq 18, io base 0x00001880
[    1.051391] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.051438] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.051493] usb usb5: Product: UHCI Host Controller
[    1.051537] usb usb5: Manufacturer: Linux 3.19.0-15-generic uhci_hcd
[    1.051582] usb usb5: SerialNumber: 0000:00:1a.2
[    1.051755] hub 5-0:1.0: USB hub found
[    1.051804] hub 5-0:1.0: 2 ports detected
[    1.052086] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.052136] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    1.052196] uhci_hcd 0000:00:1d.0: detected 2 ports
[    1.052256] uhci_hcd 0000:00:1d.0: irq 16, io base 0x000018a0
[    1.052350] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    1.052397] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.052452] usb usb6: Product: UHCI Host Controller
[    1.052496] usb usb6: Manufacturer: Linux 3.19.0-15-generic uhci_hcd
[    1.052542] usb usb6: SerialNumber: 0000:00:1d.0
[    1.052705] hub 6-0:1.0: USB hub found
[    1.052754] hub 6-0:1.0: 2 ports detected
[    1.053027] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.053078] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    1.053137] uhci_hcd 0000:00:1d.1: detected 2 ports
[    1.053196] uhci_hcd 0000:00:1d.1: irq 17, io base 0x000018c0
[    1.053289] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    1.053336] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.053391] usb usb7: Product: UHCI Host Controller
[    1.053435] usb usb7: Manufacturer: Linux 3.19.0-15-generic uhci_hcd
[    1.053481] usb usb7: SerialNumber: 0000:00:1d.1
[    1.053647] hub 7-0:1.0: USB hub found
[    1.053696] hub 7-0:1.0: 2 ports detected
[    1.053971] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.054021] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    1.054080] uhci_hcd 0000:00:1d.2: detected 2 ports
[    1.054140] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018e0
[    1.054232] usb usb8: New USB device found, idVendor=1d6b, idProduct=0001
[    1.054280] usb usb8: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.054335] usb usb8: Product: UHCI Host Controller
[    1.054379] usb usb8: Manufacturer: Linux 3.19.0-15-generic uhci_hcd
[    1.054424] usb usb8: SerialNumber: 0000:00:1d.2
[    1.054590] hub 8-0:1.0: USB hub found
[    1.054640] hub 8-0:1.0: 2 ports detected
[    1.054838] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.057710] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.057758] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.057960] mousedev: PS/2 mouse device common for all mice
[    1.058180] rtc_cmos 00:01: RTC can wake from S4
[    1.058352] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    1.058421] rtc_cmos 00:01: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.058494] i2c /dev entries driver
[    1.058634] device-mapper: uevent: version 1.0.3
[    1.058767] device-mapper: ioctl: 4.29.0-ioctl (2014-10-28) initialised: dm-devel@redhat.com
[    1.058842] ledtrig-cpu: registered to indicate activity on CPUs
[    1.059010] PCCT header not found.
[    1.059053] ACPI PCC probe failed.
[    1.059217] TCP: cubic registered
[    1.059416] NET: Registered protocol family 10
[    1.059738] NET: Registered protocol family 17
[    1.059795] Key type dns_resolver registered
[    1.060188] Loading compiled-in X.509 certificates
[    1.061515] Loaded X.509 cert 'Magrathea: Glacier signing key: 9e64807092f3a6a8f66f3b7ea4cb3767fdfae08a'
[    1.061592] registered taskstats version 1
[    1.064341] Key type trusted registered
[    1.069052] Key type encrypted registered
[    1.069105] AppArmor: AppArmor sha1 policy hashing enabled
[    1.092063] tpm_tis 00:03: A TPM error (6) occurred attempting to read a pcr value
[    1.092124] ima: No TPM chip found, activating TPM-bypass!
[    1.092211] evm: HMAC attrs: 0x1
[    1.093569]   Magic number: 11:560:722
[    1.093645] block loop2: hash matches
[    1.093798] rtc_cmos 00:01: setting system clock to 2015-04-30 06:44:29 UTC (1430376269)
[    1.094338] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.094384] EDD information not available.
[    1.094505] PM: Hibernation image not present or could not be loaded.
[    1.346673] ata3: SATA link down (SStatus 0 SControl 300)
[    1.544038] usb 6-1: new full-speed USB device number 2 using uhci_hcd
[    1.564295] tsc: Refined TSC clocksource calibration: 2194.516 MHz
[    1.705079] usb 6-1: New USB device found, idVendor=0c45, idProduct=612c
[    1.705132] usb 6-1: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[    1.705185] usb 6-1: Product: USB camera
[    1.804044] usb 7-1: new low-speed USB device number 2 using uhci_hcd
[    1.986049] usb 7-1: New USB device found, idVendor=045e, idProduct=0040
[    1.986102] usb 7-1: New USB device strings: Mfr=1, Product=3, SerialNumber=0
[    1.986154] usb 7-1: Product: Microsoft 3-Button Mouse with IntelliEye(TM)
[    1.986208] usb 7-1: Manufacturer: Microsoft
[    2.044029] ata4: failed to resume link (SControl 0)
[    2.054683] ata4: SATA link down (SStatus 0 SControl 0)
[    2.054750] usb 2-2: new high-speed USB device number 6 using ehci-pci
[    2.208028] ata1.01: failed to resume link (SControl 0)
[    2.208149] ata2.01: failed to resume link (SControl 0)
[    2.228036] usb 7-2: new low-speed USB device number 3 using uhci_hcd
[    2.364095] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.364157] ata1.01: SATA link down (SStatus 0 SControl 0)
[    2.364317] ata2.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.364373] ata2.01: SATA link down (SStatus 0 SControl 0)
[    2.372343] ata2.00: ATA-8: Hitachi HDP725050GLA360, GM4OA52A, max UDMA/133
[    2.372396] ata2.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.388350] ata2.00: configured for UDMA/133
[    2.391083] ata1.00: ATA-8: KINGSTON SV300S37A120G, 521ABBF0, max UDMA/133
[    2.391136] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.413051] usb 7-2: New USB device found, idVendor=04df, idProduct=0032
[    2.413104] usb 7-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.413156] usb 7-2: Product: USB RF Combo Device 
[    2.413208] usb 7-2: Manufacturer: Interlink Electronics, Inc. 
[    2.422946] ata1.00: configured for UDMA/133
[    2.423132] scsi 0:0:0:0: Direct-Access     ATA      KINGSTON SV300S3 BBF0 PQ: 0 ANSI: 5
[    2.423385] sd 0:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    2.423419] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.423528] scsi 1:0:0:0: Direct-Access     ATA      Hitachi HDP72505 A52A PQ: 0 ANSI: 5
[    2.423563] sd 0:0:0:0: [sda] Write Protect is off
[    2.423565] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.423590] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.423908] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    2.423911] sd 1:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    2.423966] sd 1:0:0:0: [sdb] Write Protect is off
[    2.423968] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.423992] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.424544]  sda: sda1 sda2 < sda5 >
[    2.424968] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.461243]  sdb: sdb1 sdb2 < sdb5 >
[    2.461670] sd 1:0:0:0: [sdb] Attached SCSI disk
[    2.462272] Freeing unused kernel memory: 1408K (ffffffff81d36000 - ffffffff81e96000)
[    2.462330] Write protecting the kernel read-only data: 12288k
[    2.462620] Freeing unused kernel memory: 188K (ffff8800017d1000 - ffff880001800000)
[    2.462846] Freeing unused kernel memory: 344K (ffff880001baa000 - ffff880001c00000)
[    2.476828] random: systemd-udevd urandom read with 17 bits of entropy available
[    2.499449] pata_acpi 0000:00:03.2: enabling device (0004 -> 0005)
[    2.505533] pps_core: LinuxPPS API ver. 1 registered
[    2.505584] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    2.507405] PTP clock support registered
[    2.512663] e1000e: Intel(R) PRO/1000 Network Driver - 2.3.2-k
[    2.512715] e1000e: Copyright(c) 1999 - 2014 Intel Corporation.
[    2.513003] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    2.532515] hidraw: raw HID events driver (C) Jiri Kosina
[    2.568081] Switched to clocksource tsc
[    2.594492] usbcore: registered new interface driver usbhid
[    2.594542] usbhid: USB HID core driver
[    2.609174] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/0003:045E:0040.0001/input/input5
[    2.609403] hid-generic 0003:045E:0040.0001: input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.1-1/input0
[    2.609807] input: Interlink Electronics, Inc.  USB RF Combo Device  as /devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.0/0003:04DF:0032.0002/input/input6
[    2.616047] usb 2-2: new high-speed USB device number 7 using ehci-pci
[    2.622609] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    2.668087] hid-generic 0003:04DF:0032.0002: input,hidraw1: USB HID v1.00 Keyboard [Interlink Electronics, Inc.  USB RF Combo Device ] on usb-0000:00:1d.1-2/input0
[    2.668603] input: Interlink Electronics, Inc.  USB RF Combo Device  as /devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.1/0003:04DF:0032.0003/input/input7
[    2.724241] hid-generic 0003:04DF:0032.0003: input,hidraw2: USB HID v1.00 Mouse [Interlink Electronics, Inc.  USB RF Combo Device ] on usb-0000:00:1d.1-2/input1
[    2.824303] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) 00:1d:7d:b6:65:8c
[    2.824363] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    2.824431] e1000e 0000:00:19.0 eth0: MAC: 7, PHY: 6, PBA No: FFFFFF-0FF
[    3.172036] usb 2-2: new high-speed USB device number 9 using ehci-pci
[    5.540109] floppy0: no floppy controllers found
[    5.888035] usb 2-2: new high-speed USB device number 21 using ehci-pci
[    8.820033] usb 2-2: new high-speed USB device number 34 using ehci-pci
[   11.104031] usb 2-2: new high-speed USB device number 44 using ehci-pci
[   12.092033] usb 2-2: new high-speed USB device number 48 using ehci-pci
[   14.808032] usb 2-2: new high-speed USB device number 60 using ehci-pci
[   15.580033] usb 2-2: new high-speed USB device number 63 using ehci-pci
[   16.568032] usb 2-2: new high-speed USB device number 67 using ehci-pci
[   17.772032] usb 2-2: new high-speed USB device number 72 using ehci-pci
[   18.544032] usb 2-2: new high-speed USB device number 75 using ehci-pci
[   18.884026] usb 2-2: new high-speed USB device number 76 using ehci-pci
[   19.224026] usb 2-2: new high-speed USB device number 77 using ehci-pci
[   19.780031] usb 2-2: new high-speed USB device number 79 using ehci-pci
[   20.768032] usb 2-2: new high-speed USB device number 83 using ehci-pci
[   21.756032] usb 2-2: new high-speed USB device number 87 using ehci-pci
[   22.960026] usb 2-2: new high-speed USB device number 92 using ehci-pci
[   23.300026] usb 2-2: new high-speed USB device number 93 using ehci-pci
[   24.504031] usb 2-2: new high-speed USB device number 98 using ehci-pci
[   25.492031] usb 2-2: new high-speed USB device number 102 using ehci-pci
[   26.480032] usb 2-2: new high-speed USB device number 106 using ehci-pci
[   27.468032] usb 2-2: new high-speed USB device number 110 using ehci-pci
[   28.456032] usb 2-2: new high-speed USB device number 114 using ehci-pci
[   31.388027] usb 2-2: new high-speed USB device number 127 using ehci-pci
[   32.376026] usb 2-2: new high-speed USB device number 5 using ehci-pci
[   33.364026] usb 2-2: new high-speed USB device number 9 using ehci-pci
[   34.352027] usb 2-2: new high-speed USB device number 13 using ehci-pci
[   35.340027] usb 2-2: new high-speed USB device number 17 using ehci-pci
[   35.710721] systemd[1]: Inserted module 'autofs4'
[   35.720451] systemd[1]: systemd 219 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT -GNUTLS +ACL +XZ -LZ4 -SECCOMP +BLKID -ELFUTILS +KMOD -IDN)
[   35.720688] systemd[1]: Detected architecture x86-64.
[   35.721738] systemd[1]: Set hostname to <lenovo>.
[   35.906632] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[   35.906704] systemd[1]: Starting Forward Password Requests to Wall Directory Watch.
[   35.907046] systemd[1]: Created slice Root Slice.
[   35.907100] systemd[1]: Starting Root Slice.
[   35.907394] systemd[1]: Listening on Journal Audit Socket.
[   35.907447] systemd[1]: Starting Journal Audit Socket.
[   35.907726] systemd[1]: Listening on Delayed Shutdown Socket.
[   35.907780] systemd[1]: Starting Delayed Shutdown Socket.
[   35.908102] systemd[1]: Listening on Journal Socket (/dev/log).
[   35.908157] systemd[1]: Starting Journal Socket (/dev/log).
[   35.908445] systemd[1]: Listening on /dev/initctl Compatibility Named Pipe.
[   35.908500] systemd[1]: Starting /dev/initctl Compatibility Named Pipe.
[   35.908872] systemd[1]: Created slice System Slice.
[   35.908932] systemd[1]: Starting System Slice.
[   35.909750] systemd[1]: Starting Increase datagram queue length...
[   35.910262] systemd[1]: Listening on udev Control Socket.
[   35.910333] systemd[1]: Starting udev Control Socket.
[   35.910703] systemd[1]: Listening on Journal Socket.
[   35.910773] systemd[1]: Starting Journal Socket.
[   35.911644] systemd[1]: Starting Setup Virtual Console...
[   35.913830] systemd[1]: Starting Nameserver information manager...
[   35.915048] systemd[1]: Mounting Huge Pages File System...
[   35.916687] systemd[1]: Started Braille Device Support.
[   35.917669] systemd[1]: Starting Braille Device Support...
[   35.919378] systemd[1]: Mounting Debug File System...
[   35.921105] systemd[1]: Starting Create list of required static device nodes for the current kernel...
[   35.922044] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[   35.922139] systemd[1]: Starting Arbitrary Executable File Formats File System Automount Point.
[   35.925370] systemd[1]: Started Set Up Additional Binary Formats.
[   35.925757] systemd[1]: Listening on fsck to fsckd communication Socket.
[   35.925818] systemd[1]: Starting fsck to fsckd communication Socket.
[   35.931896] systemd[1]: Starting Load Kernel Modules...
[   35.932948] systemd[1]: Mounting POSIX Message Queue File System...
[   35.938244] systemd[1]: Starting Uncomplicated firewall...
[   35.939047] systemd[1]: Created slice system-getty.slice.
[   35.939111] systemd[1]: Starting system-getty.slice.
[   35.939557] systemd[1]: Created slice User and Session Slice.
[   35.939619] systemd[1]: Starting User and Session Slice.
[   35.939910] systemd[1]: Reached target Slices.
[   35.939966] systemd[1]: Starting Slices.
[   35.940277] systemd[1]: Reached target Encrypted Volumes.
[   35.940338] systemd[1]: Starting Encrypted Volumes.
[   35.941690] systemd[1]: Started Read required files in advance.
[   35.941918] systemd[1]: Starting Read required files in advance...
[   35.942429] systemd[1]: Listening on udev Kernel Socket.
[   35.942486] systemd[1]: Starting udev Kernel Socket.
[   35.943387] systemd[1]: Starting udev Coldplug all Devices...
[   35.943848] systemd[1]: Reached target Remote File Systems (Pre).
[   35.943920] systemd[1]: Starting Remote File Systems (Pre).
[   35.946704] systemd[1]: Mounted Huge Pages File System.
[   35.947042] systemd[1]: Mounted Debug File System.
[   35.947397] systemd[1]: Mounted POSIX Message Queue File System.
[   35.948719] systemd[1]: Started Increase datagram queue length.
[   35.949455] systemd[1]: Started Setup Virtual Console.
[   35.953485] systemd[1]: Started Create list of required static device nodes for the current kernel.
[   35.955028] systemd[1]: Started Uncomplicated firewall.
[   35.958009] systemd[1]: Started Nameserver information manager.
[   35.967808] lp: driver loaded but no devices found
[   35.977587] ppdev: user-space parallel port driver
[   35.983788] systemd[1]: Started udev Coldplug all Devices.
[   35.998184] coretemp coretemp.0: Using relative temperature scale!
[   35.998249] coretemp coretemp.0: Using relative temperature scale!
[   35.999698] systemd[1]: Started Load Kernel Modules.
[   36.007828] systemd[1]: Starting Apply Kernel Variables...
[   36.009042] systemd[1]: Mounting FUSE Control File System...
[   36.009379] systemd[1]: Mounted Configuration File System.
[   36.010318] systemd[1]: Starting udev Wait for Complete Device Initialization...
[   36.012259] systemd[1]: Starting Create Static Device Nodes in /dev...
[   36.014564] systemd[1]: Listening on Syslog Socket.
[   36.014700] systemd[1]: Starting Syslog Socket.
[   36.015995] systemd[1]: Starting Journal Service...
[   36.018754] systemd[1]: Mounted FUSE Control File System.
[   36.067435] systemd[1]: Started Apply Kernel Variables.
[   36.068653] systemd[1]: Started Create Static Device Nodes in /dev.
[   36.074111] systemd[1]: Starting udev Kernel Device Manager...
[   36.085827] systemd[1]: Started Journal Service.
[   36.120061] usb 2-2: new high-speed USB device number 20 using ehci-pci
[   36.218341] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   36.271070] [drm] Initialized drm 1.1.0 20060810
[   36.272426] ACPI Warning: SystemIO range 0x0000000000001028-0x000000000000102f conflicts with OpRegion 0x0000000000001028-0x0000000000001047 (\_SB_.PCI0.IEIT.EITR) (20141107/utaddress-258)
[   36.272437] ACPI Warning: SystemIO range 0x0000000000001028-0x000000000000102f conflicts with OpRegion 0x0000000000001000-0x000000000000102f (\_SB_.PCI0.LPC0.PMIO) (20141107/utaddress-258)
[   36.272442] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   36.272446] ACPI Warning: SystemIO range 0x0000000000001180-0x00000000000011af conflicts with OpRegion 0x0000000000001180-0x00000000000011af (\_SB_.PCI0.LPC0.GPOX) (20141107/utaddress-258)
[   36.272451] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   36.272498] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   36.297062] random: nonblocking pool is initialized
[   36.402070] snd_hda_intel 0000:01:00.1: Disabling MSI
[   36.402085] snd_hda_intel 0000:01:00.1: Handle VGA-switcheroo audio client
[   36.536961] gpio_ich: GPIO from 451 to 511 on gpio_ich
[   36.752558] nvidia: module license 'NVIDIA' taints kernel.
[   36.752563] Disabling lock debugging due to kernel taint
[   36.767251] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
[   36.777484] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   36.784077] [drm] Initialized nvidia-drm 0.0.0 20150116 for 0000:01:00.0 on minor 0
[   36.784096] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  340.76  Thu Jan 22 12:11:08 PST 2015
[   36.785024] sound hdaudioC0D2: autoconfig: line_outs=1 (0x12/0x0/0x0/0x0/0x0) type:line
[   36.785030] sound hdaudioC0D2:    speaker_outs=1 (0x13/0x0/0x0/0x0/0x0)
[   36.785033] sound hdaudioC0D2:    hp_outs=1 (0x11/0x0/0x0/0x0/0x0)
[   36.785035] sound hdaudioC0D2:    mono: mono_out=0x0
[   36.785037] sound hdaudioC0D2:    inputs:
[   36.785040] sound hdaudioC0D2:      Front Mic=0x14
[   36.785043] sound hdaudioC0D2:      Rear Mic=0x17
[   36.785046] sound hdaudioC0D2:      Line=0x15
[   36.785048] sound hdaudioC0D2:      CD=0x18
[   36.793780] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   36.793881] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   36.793969] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   36.794057] input: HDA Intel Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   36.794144] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   36.937409] Adding 8080380k swap on /dev/sda5.  Priority:-1 extents:1 across:8080380k SSFS
[   37.194247] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input13
[   37.196051] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input14
[   37.196241] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input15
[   37.196464] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input16
[   37.452024] media: Linux media interface: v0.10
[   37.457340] Linux video capture interface: v2.00
[   37.459680] gspca_main: v2.14.0 registered
[   37.461754] gspca_main: sonixj-2.14.0 probing 0c45:612c
[   37.467965] input: sonixj as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/input/input17
[   37.468184] usbcore: registered new interface driver sonixj
[   38.624044] usb 2-2: new high-speed USB device number 31 using ehci-pci
[   39.260051] floppy0: no floppy controllers found
[   39.396033] usb 2-2: new high-speed USB device number 34 using ehci-pci
[   40.384027] usb 2-2: new high-speed USB device number 38 using ehci-pci
[   41.372028] usb 2-2: new high-speed USB device number 42 using ehci-pci
[   42.576034] usb 2-2: new high-speed USB device number 47 using ehci-pci
[   43.564033] usb 2-2: new high-speed USB device number 51 using ehci-pci
[   43.904027] usb 2-2: new high-speed USB device number 52 using ehci-pci
[   44.244028] usb 2-2: new high-speed USB device number 53 using ehci-pci
[   44.584035] usb 2-2: new high-speed USB device number 54 using ehci-pci
[   45.140038] usb 2-2: new high-speed USB device number 56 using ehci-pci
[   45.480028] usb 2-2: new high-speed USB device number 57 using ehci-pci
[   46.036033] usb 2-2: new high-speed USB device number 59 using ehci-pci
[   46.376029] usb 2-2: new high-speed USB device number 60 using ehci-pci
[   47.148035] usb 2-2: new high-speed USB device number 63 using ehci-pci
[   47.704028] usb 2-2: new high-speed USB device number 65 using ehci-pci
[   48.260042] usb 2-2: new high-speed USB device number 67 using ehci-pci
[   48.600034] usb 2-2: new high-speed USB device number 68 using ehci-pci
[   49.588034] usb 2-2: new high-speed USB device number 72 using ehci-pci
[   49.928028] usb 2-2: new high-speed USB device number 73 using ehci-pci
[   50.700027] usb 2-2: new high-speed USB device number 76 using ehci-pci
[   51.040033] usb 2-2: new high-speed USB device number 77 using ehci-pci
[   51.812032] usb 2-2: new high-speed USB device number 80 using ehci-pci
[   52.584033] usb 2-2: new high-speed USB device number 83 using ehci-pci
[   52.924027] usb 2-2: new high-speed USB device number 84 using ehci-pci
[   53.912038] usb 2-2: new high-speed USB device number 88 using ehci-pci
[   55.548027] usb 2-2: new high-speed USB device number 95 using ehci-pci
[   56.104034] usb 2-2: new high-speed USB device number 97 using ehci-pci
[   57.524028] usb 2-2: new high-speed USB device number 103 using ehci-pci
[   57.864033] usb 2-2: new high-speed USB device number 104 using ehci-pci
[   58.420038] usb 2-2: new high-speed USB device number 106 using ehci-pci
[   58.760027] usb 2-2: new high-speed USB device number 107 using ehci-pci
[   59.316038] usb 2-2: new high-speed USB device number 109 using ehci-pci
[   60.092034] usb 2-2: new high-speed USB device number 112 using ehci-pci
[   61.080033] usb 2-2: new high-speed USB device number 116 using ehci-pci
[   61.636028] usb 2-2: new high-speed USB device number 118 using ehci-pci
[   61.976028] usb 2-2: new high-speed USB device number 119 using ehci-pci
[   62.532028] usb 2-2: new high-speed USB device number 121 using ehci-pci
[   62.872027] usb 2-2: new high-speed USB device number 122 using ehci-pci
[   64.508028] usb 2-2: new high-speed USB device number 3 using ehci-pci
[   65.064029] usb 2-2: new high-speed USB device number 5 using ehci-pci
[   65.836033] usb 2-2: new high-speed USB device number 8 using ehci-pci
[   66.392038] usb 2-2: new high-speed USB device number 10 using ehci-pci
[   67.164035] usb 2-2: new high-speed USB device number 13 using ehci-pci
[   67.720027] usb 2-2: new high-speed USB device number 15 using ehci-pci
[   70.868034] usb 2-2: new high-speed USB device number 29 using ehci-pci
[   71.208029] usb 2-2: new high-speed USB device number 30 using ehci-pci
[   72.844033] usb 2-2: new high-speed USB device number 37 using ehci-pci
[   73.184035] usb 2-2: new high-speed USB device number 38 using ehci-pci
[   73.956028] usb 2-2: new high-speed USB device number 41 using ehci-pci
[   76.240028] usb 2-2: new high-speed USB device number 51 using ehci-pci
[   76.796032] usb 2-2: new high-speed USB device number 53 using ehci-pci
[   79.944028] usb 2-2: new high-speed USB device number 67 using ehci-pci
[   80.284033] usb 2-2: new high-speed USB device number 68 using ehci-pci
[   80.624028] usb 2-2: new high-speed USB device number 69 using ehci-pci
[   80.964028] usb 2-2: new high-speed USB device number 70 using ehci-pci
[   81.520033] usb 2-2: new high-speed USB device number 72 using ehci-pci
[   82.292028] usb 2-2: new high-speed USB device number 75 using ehci-pci
[   82.632028] usb 2-2: new high-speed USB device number 76 using ehci-pci
[   82.972028] usb 2-2: new high-speed USB device number 77 using ehci-pci
[   83.528033] usb 2-2: new high-speed USB device number 79 using ehci-pci
[   84.516033] usb 2-2: new high-speed USB device number 83 using ehci-pci
[   85.072033] usb 2-2: new high-speed USB device number 85 using ehci-pci
[   86.276027] usb 2-2: new high-speed USB device number 90 using ehci-pci
[   86.832033] usb 2-2: new high-speed USB device number 92 using ehci-pci
[   87.172028] usb 2-2: new high-speed USB device number 93 using ehci-pci
[   87.728032] usb 2-2: new high-speed USB device number 95 using ehci-pci
[   88.500028] usb 2-2: new high-speed USB device number 98 using ehci-pci
[   89.704033] usb 2-2: new high-speed USB device number 103 using ehci-pci
[   90.692033] usb 2-2: new high-speed USB device number 107 using ehci-pci
[   91.032028] usb 2-2: new high-speed USB device number 108 using ehci-pci
[   91.804027] usb 2-2: new high-speed USB device number 111 using ehci-pci
[   92.364027] usb 2-2: new high-speed USB device number 113 using ehci-pci
[   92.704032] usb 2-2: new high-speed USB device number 114 using ehci-pci
[   94.340027] usb 2-2: new high-speed USB device number 121 using ehci-pci
[   96.840034] usb 2-2: new high-speed USB device number 6 using ehci-pci
[   97.396049] usb 2-2: new high-speed USB device number 8 using ehci-pci
[   97.952028] usb 2-2: new high-speed USB device number 10 using ehci-pci
[   98.292028] usb 2-2: new high-speed USB device number 11 using ehci-pci
[   98.848033] usb 2-2: new high-speed USB device number 13 using ehci-pci
[   99.836034] usb 2-2: new high-speed USB device number 17 using ehci-pci
[  100.176028] usb 2-2: new high-speed USB device number 18 using ehci-pci
[  100.948028] usb 2-2: new high-speed USB device number 21 using ehci-pci
[  101.504028] usb 2-2: new high-speed USB device number 23 using ehci-pci
[  102.060027] usb 2-2: new high-speed USB device number 25 using ehci-pci
[  102.400039] usb 2-2: new high-speed USB device number 26 using ehci-pci
[  103.388038] usb 2-2: new high-speed USB device number 30 using ehci-pci
[  104.160028] usb 2-2: new high-speed USB device number 33 using ehci-pci
[  104.500028] usb 2-2: new high-speed USB device number 34 using ehci-pci
[  105.056034] usb 2-2: new high-speed USB device number 36 using ehci-pci
[  105.396040] usb 2-2: new high-speed USB device number 37 using ehci-pci
[  105.736027] usb 2-2: new high-speed USB device number 38 using ehci-pci
[  106.508028] usb 2-2: new high-speed USB device number 41 using ehci-pci
[  106.848032] usb 2-2: new high-speed USB device number 42 using ehci-pci
[  107.620029] usb 2-2: new high-speed USB device number 45 using ehci-pci
[  108.176027] usb 2-2: new high-speed USB device number 47 using ehci-pci
[  109.164028] usb 2-2: new high-speed USB device number 51 using ehci-pci
[  109.504028] usb 2-2: new high-speed USB device number 52 using ehci-pci
[  110.924037] usb 2-2: new high-speed USB device number 58 using ehci-pci
[  111.480029] usb 2-2: new high-speed USB device number 60 using ehci-pci
[  111.820033] usb 2-2: new high-speed USB device number 61 using ehci-pci
[  112.376027] usb 2-2: new high-speed USB device number 63 using ehci-pci
[  112.716028] usb 2-2: new high-speed USB device number 64 using ehci-pci
[  113.272032] usb 2-2: new high-speed USB device number 66 using ehci-pci
[  113.828033] usb 2-2: new high-speed USB device number 68 using ehci-pci
[  114.384039] usb 2-2: new high-speed USB device number 70 using ehci-pci
[  115.372027] usb 2-2: new high-speed USB device number 74 using ehci-pci
[  117.444040] usb 2-2: new high-speed USB device number 83 using ehci-pci
[  119.080032] usb 2-2: new high-speed USB device number 90 using ehci-pci
[  119.636028] usb 2-2: new high-speed USB device number 92 using ehci-pci
[  119.976033] usb 2-2: new high-speed USB device number 93 using ehci-pci
[  120.316027] usb 2-2: new high-speed USB device number 94 using ehci-pci
[  120.656028] usb 2-2: new high-speed USB device number 95 using ehci-pci
[  121.212032] usb 2-2: new high-speed USB device number 97 using ehci-pci
[  121.768027] usb 2-2: new high-speed USB device number 99 using ehci-pci
[  122.540028] usb 2-2: new high-speed USB device number 102 using ehci-pci
[  122.880038] usb 2-2: new high-speed USB device number 103 using ehci-pci
[  123.436034] usb 2-2: new high-speed USB device number 105 using ehci-pci
[  123.992028] usb 2-2: new high-speed USB device number 107 using ehci-pci
[  124.548028] usb 2-2: new high-speed USB device number 109 using ehci-pci
[  124.888038] usb 2-2: new high-speed USB device number 110 using ehci-pci
[  125.228035] usb 2-2: new high-speed USB device number 111 using ehci-pci
[  125.568034] usb 2-2: new high-speed USB device number 112 using ehci-pci
[  126.124028] usb 2-2: new high-speed USB device number 114 using ehci-pci
[  126.896038] usb 2-2: new high-speed USB device number 117 using ehci-pci
[  127.884037] usb 2-2: new high-speed USB device number 121 using ehci-pci
[  128.224034] usb 2-2: new high-speed USB device number 122 using ehci-pci
[  128.564028] usb 2-2: new high-speed USB device number 123 using ehci-pci
[  128.904038] usb 2-2: new high-speed USB device number 124 using ehci-pci
[  129.892038] usb 2-2: new high-speed USB device number 2 using ehci-pci
[  130.232034] usb 2-2: new high-speed USB device number 3 using ehci-pci
[  131.868033] usb 2-2: new high-speed USB device number 10 using ehci-pci
[  132.208028] usb 2-2: new high-speed USB device number 11 using ehci-pci
[  133.196027] usb 2-2: new high-speed USB device number 15 using ehci-pci
[  133.752027] usb 2-2: new high-speed USB device number 17 using ehci-pci
[  134.308027] usb 2-2: new high-speed USB device number 19 using ehci-pci
[  134.864033] usb 2-2: new high-speed USB device number 21 using ehci-pci
[  135.204027] usb 2-2: new high-speed USB device number 22 using ehci-pci
[  136.840033] usb 2-2: new high-speed USB device number 29 using ehci-pci
[  137.180028] usb 2-2: new high-speed USB device number 30 using ehci-pci
[  138.816033] usb 2-2: new high-speed USB device number 37 using ehci-pci
[  140.020043] usb 2-2: new high-speed USB device number 42 using ehci-pci
[  141.012047] usb 2-2: new high-speed USB device number 46 using ehci-pci
[  141.784032] usb 2-2: new high-speed USB device number 49 using ehci-pci
[  142.556028] usb 2-2: new high-speed USB device number 52 using ehci-pci
[  143.112032] usb 2-2: new high-speed USB device number 54 using ehci-pci
[  143.452028] usb 2-2: new high-speed USB device number 55 using ehci-pci
[  143.792032] usb 2-2: new high-speed USB device number 56 using ehci-pci
[  144.132034] usb 2-2: new high-speed USB device number 57 using ehci-pci
[  145.768032] usb 2-2: new high-speed USB device number 64 using ehci-pci
[  146.972033] usb 2-2: new high-speed USB device number 69 using ehci-pci
[  147.312027] usb 2-2: new high-speed USB device number 70 using ehci-pci
[  148.084033] usb 2-2: new high-speed USB device number 73 using ehci-pci
[  148.424038] usb 2-2: new high-speed USB device number 74 using ehci-pci
[  150.708033] usb 2-2: new high-speed USB device number 84 using ehci-pci
[  151.048028] usb 2-2: new high-speed USB device number 85 using ehci-pci
[  151.388038] usb 2-2: new high-speed USB device number 86 using ehci-pci
[  151.728032] usb 2-2: new high-speed USB device number 87 using ehci-pci
[  152.716032] usb 2-2: new high-speed USB device number 91 using ehci-pci
[  153.488029] usb 2-2: new high-speed USB device number 94 using ehci-pci
[  154.692032] usb 2-2: new high-speed USB device number 99 using ehci-pci
[  156.328027] usb 2-2: new high-speed USB device number 106 using ehci-pci
[  157.100033] usb 2-2: new high-speed USB device number 109 using ehci-pci
[  157.440030] usb 2-2: new high-speed USB device number 110 using ehci-pci
[  158.212027] usb 2-2: new high-speed USB device number 113 using ehci-pci
[  159.200028] usb 2-2: new high-speed USB device number 117 using ehci-pci
[  160.188035] usb 2-2: new high-speed USB device number 121 using ehci-pci
[  161.176037] usb 2-2: new high-speed USB device number 125 using ehci-pci
[  161.732028] usb 2-2: new high-speed USB device number 127 using ehci-pci
[  162.072032] usb 2-2: new high-speed USB device number 2 using ehci-pci
[  162.412028] usb 2-2: new high-speed USB device number 3 using ehci-pci
[  163.175692] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[  163.208363] systemd-journald[240]: Received request to flush runtime journal from PID 1
[  163.272890] audit: type=1400 audit(1430376431.674:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=451 comm="apparmor_parser"
[  163.272899] audit: type=1400 audit(1430376431.674:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=451 comm="apparmor_parser"
[  163.276492] audit: type=1400 audit(1430376431.678:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=451 comm="apparmor_parser"
[  163.276505] audit: type=1400 audit(1430376431.678:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=451 comm="apparmor_parser"
[  163.279627] audit: type=1400 audit(1430376431.678:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper" pid=451 comm="apparmor_parser"
[  163.279640] audit: type=1400 audit(1430376431.678:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=451 comm="apparmor_parser"
[  163.282246] audit: type=1400 audit(1430376431.682:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=451 comm="apparmor_parser"
[  163.282257] audit: type=1400 audit(1430376431.682:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=451 comm="apparmor_parser"
[  163.282265] audit: type=1400 audit(1430376431.682:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=451 comm="apparmor_parser"
[  163.282272] audit: type=1400 audit(1430376431.682:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=451 comm="apparmor_parser"
[  163.571443] cfg80211: Calling CRDA to update world regulatory domain
[  163.576369] cfg80211: World regulatory domain updated:
[  163.576374] cfg80211:  DFS Master region: unset
[  163.576377] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[  163.576381] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[  163.576383] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[  163.576386] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[  163.576389] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[  163.576391] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[  163.620045] usb 2-2: new high-speed USB device number 8 using ehci-pci
[  165.976058] usb 2-2: new high-speed USB device number 17 using ehci-pci
[  166.316056] usb 2-2: new high-speed USB device number 18 using ehci-pci
[  167.768098] usb 2-2: new high-speed USB device number 24 using ehci-pci
[  168.108056] usb 2-2: new high-speed USB device number 25 using ehci-pci
[  168.664071] usb 2-2: new high-speed USB device number 27 using ehci-pci
[  169.004055] usb 2-2: new high-speed USB device number 28 using ehci-pci
[  169.344073] usb 2-2: new high-speed USB device number 29 using ehci-pci
[  169.900111] usb 2-2: new high-speed USB device number 31 using ehci-pci
[  170.092373] ata2.00: configured for UDMA/133
[  170.092384] ata2: EH complete
[  170.149678]  sdb: sdb1 sdb2 < sdb5 >
[  170.672071] usb 2-2: new high-speed USB device number 34 using ehci-pci
[  171.016080] usb 2-2: new high-speed USB device number 35 using ehci-pci
[  172.656064] usb 2-2: new high-speed USB device number 42 using ehci-pci
[  172.996870] usb 2-2: new high-speed USB device number 43 using ehci-pci
[  173.768068] usb 2-2: new high-speed USB device number 46 using ehci-pci
[  174.540051] usb 2-2: new high-speed USB device number 49 using ehci-pci
[  175.532074] usb 2-2: new high-speed USB device number 53 using ehci-pci
[  176.520067] usb 2-2: new high-speed USB device number 57 using ehci-pci
[  177.076055] usb 2-2: new high-speed USB device number 59 using ehci-pci
[  177.416056] usb 2-2: new high-speed USB device number 60 using ehci-pci
[  179.484064] usb 2-2: new high-speed USB device number 69 using ehci-pci
[  180.040048] usb 2-2: new high-speed USB device number 71 using ehci-pci
[  181.244055] usb 2-2: new high-speed USB device number 76 using ehci-pci
[  181.584055] usb 2-2: new high-speed USB device number 77 using ehci-pci
[  182.356047] usb 2-2: new high-speed USB device number 80 using ehci-pci
[  183.344074] usb 2-2: new high-speed USB device number 84 using ehci-pci
[  184.980047] usb 2-2: new high-speed USB device number 91 using ehci-pci
[  186.184056] usb 2-2: new high-speed USB device number 96 using ehci-pci
[  186.740064] usb 2-2: new high-speed USB device number 98 using ehci-pci
[  187.296070] usb 2-2: new high-speed USB device number 100 using ehci-pci
[  188.716056] usb 2-2: new high-speed USB device number 106 using ehci-pci
[  191.864046] usb 2-2: new high-speed USB device number 120 using ehci-pci
[  192.636077] usb 2-2: new high-speed USB device number 123 using ehci-pci
[  193.624073] usb 2-2: new high-speed USB device number 127 using ehci-pci
[  194.180045] usb 2-2: new high-speed USB device number 3 using ehci-pci
[  194.520050] usb 2-2: new high-speed USB device number 4 using ehci-pci
[  194.860082] usb 2-2: new high-speed USB device number 5 using ehci-pci
[  195.848077] usb 2-2: new high-speed USB device number 9 using ehci-pci
[  197.052042] usb 2-2: new high-speed USB device number 14 using ehci-pci
[  197.608056] usb 2-2: new high-speed USB device number 16 using ehci-pci
[  197.948067] usb 2-2: new high-speed USB device number 17 using ehci-pci
[  198.936080] usb 2-2: new high-speed USB device number 21 using ehci-pci
[  199.276061] usb 2-2: new high-speed USB device number 22 using ehci-pci
[  199.832061] usb 2-2: new high-speed USB device number 24 using ehci-pci
[  200.400061] usb 2-2: new high-speed USB device number 26 using ehci-pci
[  201.388045] usb 2-2: new high-speed USB device number 30 using ehci-pci
[  202.160056] usb 2-2: new high-speed USB device number 33 using ehci-pci
[  202.716062] usb 2-2: new high-speed USB device number 35 using ehci-pci
[  203.056086] usb 2-2: new high-speed USB device number 36 using ehci-pci
[  205.128077] usb 2-2: new high-speed USB device number 45 using ehci-pci
[  207.196047] usb 2-2: new high-speed USB device number 54 using ehci-pci
[  207.968049] usb 2-2: new high-speed USB device number 57 using ehci-pci
[  208.308037] usb 2-2: new high-speed USB device number 58 using ehci-pci
[  209.296075] usb 2-2: new high-speed USB device number 62 using ehci-pci
[  209.636058] usb 2-2: new high-speed USB device number 63 using ehci-pci
[  209.976066] usb 2-2: new high-speed USB device number 64 using ehci-pci
[  210.532040] usb 2-2: new high-speed USB device number 66 using ehci-pci
[  211.520074] usb 2-2: new high-speed USB device number 70 using ehci-pci
[  211.860041] usb 2-2: new high-speed USB device number 71 using ehci-pci
[  212.848049] usb 2-2: new high-speed USB device number 75 using ehci-pci
[  213.188055] usb 2-2: new high-speed USB device number 76 using ehci-pci
[  213.528078] usb 2-2: new high-speed USB device number 77 using ehci-pci
[  214.084051] usb 2-2: new high-speed USB device number 79 using ehci-pci
[  214.640075] usb 2-2: new high-speed USB device number 81 using ehci-pci
[  215.196064] usb 2-2: new high-speed USB device number 83 using ehci-pci
[  216.400060] usb 2-2: new high-speed USB device number 88 using ehci-pci
[  217.404085] usb 2-2: new high-speed USB device number 92 using ehci-pci
[  219.040045] usb 2-2: new high-speed USB device number 99 using ehci-pci
[  219.380047] usb 2-2: new high-speed USB device number 100 using ehci-pci
[  219.720044] usb 2-2: new high-speed USB device number 101 using ehci-pci
[  220.276035] usb 2-2: new high-speed USB device number 103 using ehci-pci
[  222.344050] usb 2-2: new high-speed USB device number 112 using ehci-pci
[  222.684061] usb 2-2: new high-speed USB device number 113 using ehci-pci
[  223.240063] usb 2-2: new high-speed USB device number 115 using ehci-pci
[  224.444035] usb 2-2: new high-speed USB device number 120 using ehci-pci
[  224.784070] usb 2-2: new high-speed USB device number 121 using ehci-pci
[  225.556052] usb 2-2: new high-speed USB device number 124 using ehci-pci
[  226.112066] usb 2-2: new high-speed USB device number 126 using ehci-pci
[  227.100046] usb 2-2: new high-speed USB device number 4 using ehci-pci
[  228.520050] usb 2-2: new high-speed USB device number 10 using ehci-pci
[  229.724039] usb 2-2: new high-speed USB device number 15 using ehci-pci
[  230.064057] usb 2-2: new high-speed USB device number 16 using ehci-pci
[  230.620080] usb 2-2: new high-speed USB device number 18 using ehci-pci
[  231.392108] usb 2-2: new high-speed USB device number 21 using ehci-pci
[  231.948061] usb 2-2: new high-speed USB device number 23 using ehci-pci
[  237.688057] usb 2-2: new high-speed USB device number 49 using ehci-pci
[  238.244066] usb 2-2: new high-speed USB device number 51 using ehci-pci
[  239.880060] usb 2-2: new high-speed USB device number 58 using ehci-pci
[  240.652059] usb 2-2: new high-speed USB device number 61 using ehci-pci
[  241.208035] usb 2-2: new high-speed USB device number 63 using ehci-pci
[  242.628069] usb 2-2: new high-speed USB device number 69 using ehci-pci
[  243.200060] usb 2-2: new high-speed USB device number 71 using ehci-pci
[  245.052046] usb 2-2: new high-speed USB device number 79 using ehci-pci
[  245.608035] usb 2-2: new high-speed USB device number 81 using ehci-pci
[  246.380065] usb 2-2: new high-speed USB device number 84 using ehci-pci
[  247.152037] usb 2-2: new high-speed USB device number 87 using ehci-pci
[  247.492069] usb 2-2: new high-speed USB device number 88 using ehci-pci
[  249.344053] usb 2-2: new high-speed USB device number 96 using ehci-pci
[  250.548069] usb 2-2: new high-speed USB device number 101 using ehci-pci
[  250.888047] usb 2-2: new high-speed USB device number 102 using ehci-pci
[  251.444064] usb 2-2: new high-speed USB device number 104 using ehci-pci
[  252.648065] usb 2-2: new high-speed USB device number 109 using ehci-pci
[  254.932041] usb 2-2: new high-speed USB device number 119 using ehci-pci
[  255.920037] usb 2-2: new high-speed USB device number 123 using ehci-pci
[  256.476044] usb 2-2: new high-speed USB device number 125 using ehci-pci
[  256.816113] usb 2-2: new high-speed USB device number 126 using ehci-pci
[  257.372033] usb 2-2: new high-speed USB device number 2 using ehci-pci
[  257.712038] usb 2-2: new high-speed USB device number 3 using ehci-pci
[  258.268035] usb 2-2: new high-speed USB device number 5 using ehci-pci
[  261.416036] usb 2-2: new high-speed USB device number 19 using ehci-pci
[  263.700047] usb 2-2: new high-speed USB device number 29 using ehci-pci
[  264.904051] usb 2-2: new high-speed USB device number 34 using ehci-pci
[  266.108048] usb 2-2: new high-speed USB device number 39 using ehci-pci
[  267.528076] usb 2-2: new high-speed USB device number 45 using ehci-pci
[  267.868092] usb 2-2: new high-speed USB device number 46 using ehci-pci
[  268.208032] usb 2-2: new high-speed USB device number 47 using ehci-pci
[  270.492038] usb 2-2: new high-speed USB device number 57 using ehci-pci
[  270.832050] usb 2-2: new high-speed USB device number 58 using ehci-pci
[  271.824041] usb 2-2: new high-speed USB device number 62 using ehci-pci
[  273.676073] usb 2-2: new high-speed USB device number 70 using ehci-pci
[  275.312036] usb 2-2: new high-speed USB device number 77 using ehci-pci
[  278.028050] usb 2-2: new high-speed USB device number 89 using ehci-pci
[  278.584040] usb 2-2: new high-speed USB device number 91 using ehci-pci
[  280.004050] usb 2-2: new high-speed USB device number 97 using ehci-pci
[  280.560060] usb 2-2: new high-speed USB device number 99 using ehci-pci
[  280.900040] usb 2-2: new high-speed USB device number 100 using ehci-pci
[  282.104059] usb 2-2: new high-speed USB device number 105 using ehci-pci
[  282.660068] usb 2-2: new high-speed USB device number 107 using ehci-pci
[  283.000039] usb 2-2: new high-speed USB device number 108 using ehci-pci
[  284.852092] usb 2-2: new high-speed USB device number 116 using ehci-pci
[  285.192056] usb 2-2: new high-speed USB device number 117 using ehci-pci
[  287.908037] usb 2-2: new high-speed USB device number 3 using ehci-pci
[  288.248038] usb 2-2: new high-speed USB device number 4 using ehci-pci
[  290.316034] usb 2-2: new high-speed USB device number 13 using ehci-pci
[  291.520036] usb 2-2: new high-speed USB device number 18 using ehci-pci
[  291.860038] usb 2-2: new high-speed USB device number 19 using ehci-pci
[  292.848054] usb 2-2: new high-speed USB device number 23 using ehci-pci
[  293.188041] usb 2-2: new high-speed USB device number 24 using ehci-pci
[  293.744099] usb 2-2: new high-speed USB device number 26 using ehci-pci
[  295.812113] usb 2-2: new high-speed USB device number 35 using ehci-pci
[  296.584039] usb 2-2: new high-speed USB device number 38 using ehci-pci
[  296.924063] usb 2-2: new high-speed USB device number 39 using ehci-pci
[  297.696043] usb 2-2: new high-speed USB device number 42 using ehci-pci
[  298.252037] usb 2-2: new high-speed USB device number 44 using ehci-pci
[  298.808069] usb 2-2: new high-speed USB device number 46 using ehci-pci
[  299.580040] usb 2-2: new high-speed USB device number 49 using ehci-pci
[  300.568071] usb 2-2: new high-speed USB device number 53 using ehci-pci
[  301.340037] usb 2-2: new high-speed USB device number 56 using ehci-pci
[  301.680779] usb 2-2: new high-speed USB device number 57 using ehci-pci
[  302.020098] usb 2-2: new high-speed USB device number 58 using ehci-pci
[  302.576039] usb 2-2: new high-speed USB device number 60 using ehci-pci
[  303.132036] usb 2-2: new high-speed USB device number 62 using ehci-pci
[  303.692062] usb 2-2: new high-speed USB device number 64 using ehci-pci
[  307.704039] usb 2-2: new high-speed USB device number 82 using ehci-pci
[  308.044049] usb 2-2: new high-speed USB device number 83 using ehci-pci
[  309.248038] usb 2-2: new high-speed USB device number 88 using ehci-pci
[  310.236037] usb 2-2: new high-speed USB device number 92 using ehci-pci
[  311.224035] usb 2-2: new high-speed USB device number 96 using ehci-pci
[  313.076034] usb 2-2: new high-speed USB device number 104 using ehci-pci
[  314.496035] usb 2-2: new high-speed USB device number 110 using ehci-pci
[  315.268036] usb 2-2: new high-speed USB device number 113 using ehci-pci
[  315.824049] usb 2-2: new high-speed USB device number 115 using ehci-pci
[  316.380034] usb 2-2: new high-speed USB device number 117 using ehci-pci
[  316.720040] usb 2-2: new high-speed USB device number 118 using ehci-pci
[  317.276036] usb 2-2: new high-speed USB device number 120 using ehci-pci
[  318.048035] usb 2-2: new high-speed USB device number 123 using ehci-pci
[  322.492039] usb 2-2: new high-speed USB device number 17 using ehci-pci
[  323.696072] usb 2-2: new high-speed USB device number 22 using ehci-pci
[  324.468034] usb 2-2: new high-speed USB device number 25 using ehci-pci
[  325.024064] usb 2-2: new high-speed USB device number 27 using ehci-pci
[  326.228078] usb 2-2: new high-speed USB device number 32 using ehci-pci
[  327.000072] usb 2-2: new high-speed USB device number 35 using ehci-pci
[  327.772069] usb 2-2: new high-speed USB device number 38 using ehci-pci
[  328.328033] usb 2-2: new high-speed USB device number 40 using ehci-pci
[  330.184049] usb 2-2: new high-speed USB device number 48 using ehci-pci
[  330.740071] usb 2-2: new high-speed USB device number 50 using ehci-pci
[  331.728047] usb 2-2: new high-speed USB device number 54 using ehci-pci
[  332.068039] usb 2-2: new high-speed USB device number 55 using ehci-pci
[  332.624066] usb 2-2: new high-speed USB device number 57 using ehci-pci
[  332.964078] usb 2-2: new high-speed USB device number 58 using ehci-pci
[  333.304036] usb 2-2: new high-speed USB device number 59 using ehci-pci
[  334.076048] usb 2-2: new high-speed USB device number 62 using ehci-pci
[  334.416109] usb 2-2: new high-speed USB device number 63 using ehci-pci
[  334.972032] usb 2-2: new high-speed USB device number 65 using ehci-pci
[  335.744057] usb 2-2: new high-speed USB device number 68 using ehci-pci
[  336.084038] usb 2-2: new high-speed USB device number 69 using ehci-pci
[  337.504052] usb 2-2: new high-speed USB device number 75 using ehci-pci
[  338.492039] usb 2-2: new high-speed USB device number 79 using ehci-pci
[  339.480061] usb 2-2: new high-speed USB device number 83 using ehci-pci
[  339.820075] usb 2-2: new high-speed USB device number 84 using ehci-pci
[  340.376066] usb 2-2: new high-speed USB device number 86 using ehci-pci
[  340.716041] usb 2-2: new high-speed USB device number 87 using ehci-pci
[  341.272048] usb 2-2: new high-speed USB device number 89 using ehci-pci
[  342.908049] usb 2-2: new high-speed USB device number 96 using ehci-pci
[  344.760083] usb 2-2: new high-speed USB device number 104 using ehci-pci
[  346.180037] usb 2-2: new high-speed USB device number 110 using ehci-pci
[  346.520039] usb 2-2: new high-speed USB device number 111 using ehci-pci
[  347.508038] usb 2-2: new high-speed USB device number 115 using ehci-pci
[  347.848045] usb 2-2: new high-speed USB device number 116 using ehci-pci
[  348.836073] usb 2-2: new high-speed USB device number 120 using ehci-pci
[  349.176034] usb 2-2: new high-speed USB device number 121 using ehci-pci
[  349.732081] usb 2-2: new high-speed USB device number 123 using ehci-pci
[  350.288040] usb 2-2: new high-speed USB device number 125 using ehci-pci
[  351.276039] usb 2-2: new high-speed USB device number 3 using ehci-pci
[  351.616037] usb 2-2: new high-speed USB device number 4 using ehci-pci
[  353.468033] usb 2-2: new high-speed USB device number 12 using ehci-pci
[  355.104045] usb 2-2: new high-speed USB device number 19 using ehci-pci
[  356.308039] usb 2-2: new high-speed USB device number 24 using ehci-pci
[  357.296035] usb 2-2: new high-speed USB device number 28 using ehci-pci
[  358.932037] usb 2-2: new high-speed USB device number 35 using ehci-pci
[  359.704053] usb 2-2: new high-speed USB device number 38 using ehci-pci
[  360.104062] INFO: task colord-sane:2078 blocked for more than 120 seconds.
[  360.104071]       Tainted: P           OE  3.19.0-15-generic #15-Ubuntu
[  360.104074] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[  360.104078] colord-sane     D ffff880206f4bd88     0  2078   2074 0x00000000
[  360.104085]  ffff880206f4bd88 ffff880206c4e220 0000000000014200 ffff880206f4bfd8
[  360.104092]  0000000000014200 ffff88020a78d850 ffff880206c4e220 0000000006f4be08
[  360.104097]  ffff88022666f8f0 ffff88022666f8f4 ffff880206c4e220 00000000ffffffff
[  360.104103] Call Trace:
[  360.104117]  [<ffffffff817c4f19>] schedule_preempt_disabled+0x29/0x70
[  360.104124]  [<ffffffff817c6dd5>] __mutex_lock_slowpath+0x95/0x100
[  360.104129]  [<ffffffff817c6e63>] mutex_lock+0x23/0x40
[  360.104136]  [<ffffffff815c6240>] read_descriptors+0x40/0x110
[  360.104143]  [<ffffffff8126db77>] sysfs_kf_bin_read+0x47/0x70
[  360.104148]  [<ffffffff8126ced0>] kernfs_fop_read+0xa0/0x170
[  360.104155]  [<ffffffff811f3df8>] __vfs_read+0x18/0x50
[  360.104160]  [<ffffffff811f3eba>] vfs_read+0x8a/0x140
[  360.104165]  [<ffffffff811f3fb6>] SyS_read+0x46/0xb0
[  360.104171]  [<ffffffff817c934d>] system_call_fastpath+0x16/0x1b
[  361.124081] usb 2-2: new high-speed USB device number 44 using ehci-pci
[  361.680112] usb 2-2: new high-speed USB device number 46 using ehci-pci
[  362.452062] usb 2-2: new high-speed USB device number 49 using ehci-pci
[  362.792085] usb 2-2: new high-speed USB device number 50 using ehci-pci
[  367.452042] usb 2-2: new high-speed USB device number 71 using ehci-pci
[  368.008067] usb 2-2: new high-speed USB device number 73 using ehci-pci
[  368.348031] usb 2-2: new high-speed USB device number 74 using ehci-pci
[  371.064046] usb 2-2: new high-speed USB device number 86 using ehci-pci
[  371.404047] usb 2-2: new high-speed USB device number 87 using ehci-pci
[  371.960052] usb 2-2: new high-speed USB device number 89 using ehci-pci
[  372.732071] usb 2-2: new high-speed USB device number 92 using ehci-pci
[  373.936036] usb 2-2: new high-speed USB device number 97 using ehci-pci
[  374.276037] usb 2-2: new high-speed USB device number 98 using ehci-pci
[  375.264046] usb 2-2: new high-speed USB device number 102 using ehci-pci
[  376.036040] usb 2-2: new high-speed USB device number 105 using ehci-pci
[  377.888037] usb 2-2: new high-speed USB device number 113 using ehci-pci
[  378.228029] usb 2-2: new high-speed USB device number 114 using ehci-pci
[  379.216041] usb 2-2: new high-speed USB device number 118 using ehci-pci
[  379.772065] usb 2-2: new high-speed USB device number 120 using ehci-pci
[  380.112033] usb 2-2: new high-speed USB device number 121 using ehci-pci
[  382.180037] usb 2-2: new high-speed USB device number 4 using ehci-pci
[  387.056037] usb 2-2: new high-speed USB device number 26 using ehci-pci
[  387.396032] usb 2-2: new high-speed USB device number 27 using ehci-pci
[  387.764060] usb 6-2: new full-speed USB device number 3 using uhci_hcd
[  387.909860] usb 6-2: not running at top speed; connect to a high speed hub
[  387.937859] usb 6-2: New USB device found, idVendor=0586, idProduct=3410
[  387.937865] usb 6-2: New USB device strings: Mfr=16, Product=32, SerialNumber=0
[  387.937871] usb 6-2: Product: ZyXEL G-202
[  387.937875] usb 6-2: Manufacturer: ZyDAS
[  389.108046] usb 6-2: reset full-speed USB device number 3 using uhci_hcd
[  389.269567] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[  389.270036] zd1211rw 6-2:1.0: phy0
[  389.270088] usbcore: registered new interface driver zd1211rw
[  389.368870] zd1211rw 6-2:1.0: firmware version 4725
[  389.428871] zd1211rw 6-2:1.0: zd1211b chip 0586:3410 v4810 full 00-13-49 AL2230_RF pa0 g---S
[  389.489588] cfg80211: Calling CRDA for country: DE
[  389.498700] cfg80211: Regulatory domain changed to country: DE
[  389.498708] cfg80211:  DFS Master region: ETSI
[  389.498711] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[  389.498717] cfg80211:   (2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[  389.498721] cfg80211:   (5150000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[  389.498726] cfg80211:   (5250000 KHz - 5350000 KHz @ 40000 KHz), (N/A, 2000 mBm), (0 s)
[  389.498730] cfg80211:   (5470000 KHz - 5725000 KHz @ 40000 KHz), (N/A, 2698 mBm), (0 s)
[  389.498735] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm), (N/A)
[  390.587315] wlan0: authenticate with 5c:7d:5e:cc:0a:c6
[  390.628943] wlan0: send auth to 5c:7d:5e:cc:0a:c6 (try 1/3)
[  390.631902] wlan0: authenticated
[  390.636060] wlan0: associate with 5c:7d:5e:cc:0a:c6 (try 1/3)
[  390.649939] wlan0: RX AssocResp from 5c:7d:5e:cc:0a:c6 (capab=0x411 status=0 aid=3)
[  390.650887] wlan0: associated
[  940.646218] perf interrupt took too long (2505 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
```

usb-devices shows:

```
T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.19
S:  Manufacturer=Linux 3.19.0-15-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1a.7
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.19
S:  Manufacturer=Linux 3.19.0-15-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.7
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.19
S:  Manufacturer=Linux 3.19.0-15-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1a.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.19
S:  Manufacturer=Linux 3.19.0-15-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1a.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.19
S:  Manufacturer=Linux 3.19.0-15-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1a.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=06 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.19
S:  Manufacturer=Linux 3.19.0-15-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=06 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0c45 ProdID=612c Rev=01.01
S:  Product=USB camera
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=sonixj

T:  Bus=06 Lev=01 Prnt=01 Port=01 Cnt=02 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=ff(vend.) Sub=ff Prot=ff MxPS=64 #Cfgs=  1
P:  Vendor=0586 ProdID=3410 Rev=48.10
S:  Manufacturer=ZyDAS
S:  Product=ZyXEL G-202
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 4 Cls=ff(vend.) Sub=00 Prot=00 Driver=(none)

T:  Bus=07 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.19
S:  Manufacturer=Linux 3.19.0-15-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=07 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=045e ProdID=0040 Rev=03.00
S:  Manufacturer=Microsoft
S:  Product=Microsoft 3-Button Mouse with IntelliEye(TM)
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid

T:  Bus=07 Lev=01 Prnt=01 Port=01 Cnt=02 Dev#=  3 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=04df ProdID=0032 Rev=03.00
S:  Manufacturer=Interlink Electronics, Inc. 
S:  Product=USB RF Combo Device 
C:  #Ifs= 2 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid
I:  If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid

T:  Bus=08 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.19
S:  Manufacturer=Linux 3.19.0-15-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


```

---

### Post by samuelsimon on 2015-06-11
I'm also having trouble starting up with 'A start job is running for udev wait for Complete Device Initialization' delaying startup by around 3 minutes. Any idea if this is related or how to fix it?

---

### Post by Bucky Ball on 2015-06-11
Just a thought. Your BIOS is not set to boot from the USB is it? Might seem a silly question but never hurts to ask.

This problem can happen with an upgrade, but you mention it was like this prior to the upgrade. Is that why you upgraded? Not probably the best move. 

[This]("http://osdir.com/ml/general/2015-05/msg35884.html") might give a few clues to move things along.

---

### Post by samuelsimon on 2015-06-11
Thanks for the suggestion. I had set to boot from USB in the startup which I have now turned off. Neither error occurred on the latest startup but I will continue to check as the issue was intermittent. 

I thought that the BIOS options happened before ubuntu got 'control' and hence would make no difference given startup was happening from the hard disk (no USB). Have I misunderstood?

---

### Post by samuelsimon on 2015-06-12
Removing USB startup from the BIOS list has not fixed this.

The USB problem occurred prior to the upgrade. The 3 minute wait for udev coincided with the upgrade but this was around the same time I installed a Nvidia graphics card.

---

