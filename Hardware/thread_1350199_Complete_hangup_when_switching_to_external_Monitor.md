---
title: "Complete hangup when switching to external Monitor after Hibernation"
date: 2009-12-09
forum: Hardware
---

### Post by ManDay on 2009-12-09
Usually I can change between monitors with Fn+F8 without problems. Only when I put the computer into hibernation, bring it back and then try to activate the external mnitoor I get a 100% freeze and need to hard reset. When I press Fn+F8 then, the monitor activates, both screens turn black with only the mousepointer on them. On the laptop LCD the mousepointer is then frozen to the center of the right edge of the screen and on the monitor its frozen to the very center.

Any idea?

PS: The graphics set is Intel GMA950

---

### Post by ManDay on 2009-12-12
Dec 12 12:35:21 fly kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
Dec 12 12:35:21 fly rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="760" x-info="http://www.rsyslog.com"] (re)start
Dec 12 12:35:22 fly rsyslogd: rsyslogd's groupid changed to 102
Dec 12 12:35:22 fly rsyslogd: rsyslogd's userid changed to 101
Dec 12 12:35:22 fly kernel: [    0.000000] Initializing cgroup subsys cpuset
Dec 12 12:35:22 fly kernel: [    0.000000] Initializing cgroup subsys cpu
Dec 12 12:35:22 fly kernel: [    0.000000] Linux version 2.6.31-16-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 (Ubuntu 2.6.31-16.53-generic)
Dec 12 12:35:22 fly kernel: [    0.000000] KERNEL supported cpus:
Dec 12 12:35:22 fly kernel: [    0.000000]   Intel GenuineIntel
Dec 12 12:35:22 fly kernel: [    0.000000]   AMD AuthenticAMD
Dec 12 12:35:22 fly kernel: [    0.000000]   NSC Geode by NSC
Dec 12 12:35:22 fly kernel: [    0.000000]   Cyrix CyrixInstead
Dec 12 12:35:22 fly kernel: [    0.000000]   Centaur CentaurHauls
Dec 12 12:35:22 fly kernel: [    0.000000]   Transmeta GenuineTMx86
Dec 12 12:35:22 fly kernel: [    0.000000]   Transmeta TransmetaCPU
Dec 12 12:35:22 fly kernel: [    0.000000]   UMC UMC UMC UMC
Dec 12 12:35:22 fly kernel: [    0.000000] BIOS-provided physical RAM map:
Dec 12 12:35:22 fly kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Dec 12 12:35:22 fly kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Dec 12 12:35:22 fly kernel: [    0.000000]  BIOS-e820: 00000000000e2000 - 0000000000100000 (reserved)
Dec 12 12:35:22 fly kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003f7a0000 (usable)
Dec 12 12:35:22 fly kernel: [    0.000000]  BIOS-e820: 000000003f7a0000 - 000000003f7ae000 (ACPI data)
Dec 12 12:35:22 fly kernel: [    0.000000]  BIOS-e820: 000000003f7ae000 - 000000003f7f0000 (ACPI NVS)
Dec 12 12:35:22 fly kernel: [    0.000000]  BIOS-e820: 000000003f7f0000 - 000000003f800000 (reserved)
Dec 12 12:35:22 fly kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Dec 12 12:35:22 fly kernel: [    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
Dec 12 12:35:22 fly kernel: [    0.000000] DMI present.
Dec 12 12:35:22 fly kernel: [    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
Dec 12 12:35:22 fly kernel: [    0.000000] last_pfn = 0x3f7a0 max_arch_pfn = 0x100000
Dec 12 12:35:22 fly kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Dec 12 12:35:22 fly kernel: [    0.000000] Scanning 0 areas for low memory corruption
Dec 12 12:35:22 fly kernel: [    0.000000] modified physical RAM map:
Dec 12 12:35:22 fly kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Dec 12 12:35:22 fly kernel: [    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
Dec 12 12:35:22 fly kernel: [    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
Dec 12 12:35:22 fly kernel: [    0.000000]  modified: 00000000000e2000 - 0000000000100000 (reserved)
Dec 12 12:35:22 fly kernel: [    0.000000]  modified: 0000000000100000 - 000000003f7a0000 (usable)
Dec 12 12:35:22 fly kernel: [    0.000000]  modified: 000000003f7a0000 - 000000003f7ae000 (ACPI data)
Dec 12 12:35:22 fly kernel: [    0.000000]  modified: 000000003f7ae000 - 000000003f7f0000 (ACPI NVS)
Dec 12 12:35:22 fly kernel: [    0.000000]  modified: 000000003f7f0000 - 000000003f800000 (reserved)
Dec 12 12:35:22 fly kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
Dec 12 12:35:22 fly kernel: [    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
Dec 12 12:35:22 fly kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Dec 12 12:35:22 fly kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Dec 12 12:35:22 fly kernel: [    0.000000] RAMDISK: 2f799000 - 2f9f74de
Dec 12 12:35:22 fly kernel: [    0.000000] ACPI: RSDP 000fb9e0 00014 (v00 ACPIAM)
Dec 12 12:35:22 fly kernel: [    0.000000] ACPI: RSDT 3f7a0000 0003C (v01 A_M_I_ OEMRSDT  07000921 MSFT 00000097)
Dec 12 12:35:22 fly kernel: [    0.000000] ACPI: FACP 3f7a0200 00084 (v02 A_M_I_ OEMFACP  07000921 MSFT 00000097)
Dec 12 12:35:22 fly kernel: [    0.000000] ACPI: DSDT 3f7a0430 05342 (v01  A1028 A1028000 00000000 INTL 20051117)
Dec 12 12:35:22 fly kernel: [    0.000000] ACPI: FACS 3f7ae000 00040
Dec 12 12:35:22 fly kernel: [    0.000000] ACPI: APIC 3f7a0390 0005C (v01 A_M_I_ OEMAPIC  07000921 MSFT 00000097)
Dec 12 12:35:22 fly kernel: [    0.000000] ACPI: MCFG 3f7a03f0 0003C (v01 A_M_I_ OEMMCFG  07000921 MSFT 00000097)
Dec 12 12:35:22 fly kernel: [    0.000000] ACPI: OEMB 3f7ae040 00061 (v01 A_M_I_ AMI_OEM  07000921 MSFT 00000097)
Dec 12 12:35:22 fly kernel: [    0.000000] ACPI: HPET 3f7a5780 00038 (v01 A_M_I_ OEMHPET  07000921 MSFT 00000097)
Dec 12 12:35:22 fly kernel: [    0.000000] ACPI: SSDT 3f7aeb80 004F0 (v01  PmRef    CpuPm 00003000 INTL 20051117)
Dec 12 12:35:22 fly kernel: [    0.000000] 127MB HIGHMEM available.
Dec 12 12:35:22 fly kernel: [    0.000000] 887MB LOWMEM available.
Dec 12 12:35:22 fly kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Dec 12 12:35:22 fly kernel: [    0.000000]   low ram: 0 - 377fe000
Dec 12 12:35:22 fly kernel: [    0.000000]   node 0 low ram: 00000000 - 377fe000
Dec 12 12:35:22 fly kernel: [    0.000000]   node 0 bootmap 00011000 - 00017f00
Dec 12 12:35:22 fly kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
Dec 12 12:35:22 fly kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Dec 12 12:35:22 fly kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Dec 12 12:35:22 fly kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Dec 12 12:35:22 fly kernel: [    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
Dec 12 12:35:22 fly kernel: [    0.000000]   #4 [002f799000 - 002f9f74de]          RAMDISK ==> [002f799000 - 002f9f74de]
Dec 12 12:35:22 fly kernel: [    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
Dec 12 12:35:22 fly kernel: [    0.000000]   #6 [00008a9000 - 00008ac1f8]              BRK ==> [00008a9000 - 00008ac1f8]
Dec 12 12:35:22 fly kernel: [    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
Dec 12 12:35:22 fly kernel: [    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
Dec 12 12:35:22 fly kernel: [    0.000000] found SMP MP-table at [c00ff780] ff780
Dec 12 12:35:22 fly kernel: [    0.000000] Zone PFN ranges:
Dec 12 12:35:22 fly kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Dec 12 12:35:22 fly kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Dec 12 12:35:22 fly kernel: [    0.000000]   HighMem  0x000377fe -> 0x0003f7a0
Dec 12 12:35:22 fly kernel: [    0.000000] Movable zone start PFN for each node
Dec 12 12:35:22 fly kernel: [    0.000000] early_node_map[2] active PFN ranges
Dec 12 12:35:22 fly kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Dec 12 12:35:22 fly kernel: [    0.000000]     0: 0x00000100 -> 0x0003f7a0
Dec 12 12:35:22 fly kernel: [    0.000000] Using APIC driver default
Dec 12 12:35:22 fly kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Dec 12 12:35:22 fly kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Dec 12 12:35:22 fly kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Dec 12 12:35:22 fly kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Dec 12 12:35:22 fly kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Dec 12 12:35:22 fly kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Dec 12 12:35:22 fly kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Dec 12 12:35:22 fly kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Dec 12 12:35:22 fly kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Dec 12 12:35:22 fly kernel: [    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
Dec 12 12:35:22 fly kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Dec 12 12:35:22 fly kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Dec 12 12:35:22 fly kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e2000
Dec 12 12:35:22 fly kernel: [    0.000000] PM: Registered nosave memory: 00000000000e2000 - 0000000000100000
Dec 12 12:35:22 fly kernel: [    0.000000] Allocating PCI resources starting at 3f800000 (gap: 3f800000:bf600000)
Dec 12 12:35:22 fly kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
Dec 12 12:35:22 fly kernel: [    0.000000] PERCPU: Embedded 14 pages at c17f4000, static data 35612 bytes
Dec 12 12:35:22 fly kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257855
Dec 12 12:35:22 fly kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.31-16-generic root=UUID=117575d0-8466-46f5-8bcf-15d8e85e1bff ro quiet splash
Dec 12 12:35:22 fly kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Dec 12 12:35:22 fly kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Dec 12 12:35:22 fly kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Dec 12 12:35:22 fly kernel: [    0.000000] Enabling fast FPU save and restore... done.
Dec 12 12:35:22 fly kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Dec 12 12:35:22 fly kernel: [    0.000000] Initializing CPU#0
Dec 12 12:35:22 fly kernel: [    0.000000] allocated 5199680 bytes of page_cgroup
Dec 12 12:35:22 fly kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Dec 12 12:35:22 fly kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:0003f7a0)
Dec 12 12:35:22 fly kernel: [    0.000000] Memory: 1014616k/1040000k available (4566k kernel code, 24436k reserved, 2142k data, 540k init, 130696k highmem)
Dec 12 12:35:22 fly kernel: [    0.000000] virtual kernel memory layout:
Dec 12 12:35:22 fly kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Dec 12 12:35:22 fly kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Dec 12 12:35:22 fly kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Dec 12 12:35:22 fly kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Dec 12 12:35:22 fly kernel: [    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
Dec 12 12:35:22 fly kernel: [    0.000000]       .data : 0xc0575bb4 - 0xc078d3c8   (2142 kB)
Dec 12 12:35:22 fly kernel: [    0.000000]       .text : 0xc0100000 - 0xc0575bb4   (4566 kB)
Dec 12 12:35:22 fly kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Dec 12 12:35:22 fly kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Dec 12 12:35:22 fly kernel: [    0.000000] NR_IRQS:2304 nr_irqs:424
Dec 12 12:35:22 fly kernel: [    0.000000] Fast TSC calibration using PIT
Dec 12 12:35:22 fly kernel: [    0.000000] Detected 1595.924 MHz processor.
Dec 12 12:35:22 fly kernel: [    0.001812] Console: colour VGA+ 80x25
Dec 12 12:35:22 fly kernel: [    0.001819] console [tty0] enabled
Dec 12 12:35:22 fly kernel: [    0.002072] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Dec 12 12:35:22 fly kernel: [    0.002084] Calibrating delay loop (skipped), value calculated using timer frequency.. 3191.84 BogoMIPS (lpj=6383696)
Dec 12 12:35:22 fly kernel: [    0.002121] Security Framework initialized
Dec 12 12:35:22 fly kernel: [    0.002160] AppArmor: AppArmor initialized
Dec 12 12:35:22 fly kernel: [    0.002175] Mount-cache hash table entries: 512
Dec 12 12:35:22 fly kernel: [    0.002401] Initializing cgroup subsys ns
Dec 12 12:35:22 fly kernel: [    0.002412] Initializing cgroup subsys cpuacct
Dec 12 12:35:22 fly kernel: [    0.002420] Initializing cgroup subsys memory
Dec 12 12:35:22 fly kernel: [    0.002432] Initializing cgroup subsys freezer
Dec 12 12:35:22 fly kernel: [    0.002437] Initializing cgroup subsys net_cls
Dec 12 12:35:22 fly kernel: [    0.002462] CPU: L1 I cache: 32K, L1 D cache: 24K
Dec 12 12:35:22 fly kernel: [    0.002468] CPU: L2 cache: 512K
Dec 12 12:35:22 fly kernel: [    0.002473] CPU: Physical Processor ID: 0
Dec 12 12:35:22 fly kernel: [    0.002477] CPU: Processor Core ID: 0
Dec 12 12:35:22 fly kernel: [    0.002484] mce: CPU supports 5 MCE banks
Dec 12 12:35:22 fly kernel: [    0.002497] CPU0: Thermal monitoring enabled (TM2)
Dec 12 12:35:22 fly kernel: [    0.002505] using mwait in idle threads.
Dec 12 12:35:22 fly kernel: [    0.002516] Performance Counters: Atom events, Intel PMU driver.
Dec 12 12:35:22 fly kernel: [    0.002531] ... version:                 3
Dec 12 12:35:22 fly kernel: [    0.002535] ... bit width:               40
Dec 12 12:35:22 fly kernel: [    0.002539] ... generic counters:        2
Dec 12 12:35:22 fly kernel: [    0.002544] ... value mask:              000000ffffffffff
Dec 12 12:35:22 fly kernel: [    0.002548] ... max period:              000000007fffffff
Dec 12 12:35:22 fly kernel: [    0.002553] ... fixed-purpose counters:  3
Dec 12 12:35:22 fly kernel: [    0.002557] ... counter mask:            0000000700000003
Dec 12 12:35:22 fly kernel: [    0.002566] Checking 'hlt' instruction... OK.
Dec 12 12:35:22 fly kernel: [    0.020014] ACPI: Core revision 20090521
Dec 12 12:35:22 fly kernel: [    0.036506] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Dec 12 12:35:22 fly kernel: [    0.083004] CPU0: Intel(R) Atom(TM) CPU N270   @ 1.60GHz stepping 02
Dec 12 12:35:22 fly kernel: [    0.084001] Booting processor 1 APIC 0x1 ip 0x6000
Dec 12 12:35:22 fly kernel: [    0.004000] Initializing CPU#1
Dec 12 12:35:22 fly kernel: [    0.004000] Calibrating delay using timer specific routine.. 3191.93 BogoMIPS (lpj=6383862)
Dec 12 12:35:22 fly kernel: [    0.004000] CPU: L1 I cache: 32K, L1 D cache: 24K
Dec 12 12:35:22 fly kernel: [    0.004000] CPU: L2 cache: 512K
Dec 12 12:35:22 fly kernel: [    0.004000] CPU: Physical Processor ID: 0
Dec 12 12:35:22 fly kernel: [    0.004000] CPU: Processor Core ID: 0
Dec 12 12:35:22 fly kernel: [    0.004000] mce: CPU supports 5 MCE banks
Dec 12 12:35:22 fly kernel: [    0.004000] CPU1: Thermal monitoring enabled (TM2)
Dec 12 12:35:22 fly kernel: [    0.004000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
Dec 12 12:35:22 fly kernel: [    0.169002] CPU1: Intel(R) Atom(TM) CPU N270   @ 1.60GHz stepping 02
Dec 12 12:35:22 fly kernel: [    0.169037] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Dec 12 12:35:22 fly kernel: [    0.172050] Brought up 2 CPUs
Dec 12 12:35:22 fly kernel: [    0.172057] Total of 2 processors activated (6383.77 BogoMIPS).
Dec 12 12:35:22 fly kernel: [    0.172312] Booting paravirtualized kernel on bare hardware
Dec 12 12:35:22 fly kernel: [    0.172481] regulator: core version 0.5
Dec 12 12:35:22 fly kernel: [    0.172481] Time: 11:35:11  Date: 12/12/09
Dec 12 12:35:22 fly kernel: [    0.172481] NET: Registered protocol family 16
Dec 12 12:35:22 fly kernel: [    0.172481] EISA bus registered
Dec 12 12:35:22 fly kernel: [    0.172481] ACPI: bus type pci registered
Dec 12 12:35:22 fly kernel: [    0.172594] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 63
Dec 12 12:35:22 fly kernel: [    0.172601] PCI: Not using MMCONFIG.
Dec 12 12:35:22 fly kernel: [    0.172914] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
Dec 12 12:35:22 fly kernel: [    0.172919] PCI: Using configuration type 1 for base access
Dec 12 12:35:22 fly kernel: [    0.177319] bio: create slab <bio-0> at 0
Dec 12 12:35:22 fly kernel: [    0.189939] ACPI: Interpreter enabled
Dec 12 12:35:22 fly kernel: [    0.189954] ACPI: (supports S0 S1 S3 S4 S5)
Dec 12 12:35:22 fly kernel: [    0.190007] ACPI: Using IOAPIC for interrupt routing
Dec 12 12:35:22 fly kernel: [    0.190105] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 63
Dec 12 12:35:22 fly kernel: [    0.193457] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
Dec 12 12:35:22 fly kernel: [    0.193464] PCI: Using MMCONFIG for extended config space
Dec 12 12:35:22 fly kernel: [    0.203709] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
Dec 12 12:35:22 fly kernel: [    0.203716] ACPI: EC: driver started in poll mode
Dec 12 12:35:22 fly kernel: [    0.204107] ACPI: No dock devices found.
Dec 12 12:35:22 fly kernel: [    0.204352] ACPI: PCI Root Bridge [PCI0] (0000:00)
Dec 12 12:35:22 fly kernel: [    0.204826] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Dec 12 12:35:22 fly kernel: [    0.204835] pci 0000:00:1b.0: PME# disabled
Dec 12 12:35:22 fly kernel: [    0.204944] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Dec 12 12:35:22 fly kernel: [    0.204953] pci 0000:00:1c.0: PME# disabled
Dec 12 12:35:22 fly kernel: [    0.205065] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Dec 12 12:35:22 fly kernel: [    0.205073] pci 0000:00:1c.1: PME# disabled
Dec 12 12:35:22 fly kernel: [    0.205187] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Dec 12 12:35:22 fly kernel: [    0.205196] pci 0000:00:1c.3: PME# disabled
Dec 12 12:35:22 fly kernel: [    0.205701] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Dec 12 12:35:22 fly kernel: [    0.205710] pci 0000:00:1d.7: PME# disabled
Dec 12 12:35:22 fly kernel: [    0.205905] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
Dec 12 12:35:22 fly kernel: [    0.205914] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
Dec 12 12:35:22 fly kernel: [    0.205922] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0380 (mask 0003)
Dec 12 12:35:22 fly kernel: [    0.205930] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0290 (mask 0007)
Dec 12 12:35:22 fly kernel: [    0.205939] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0068 (mask 0003)
Dec 12 12:35:22 fly kernel: [    0.206117] pci 0000:00:1f.2: PME# supported from D3hot
Dec 12 12:35:22 fly kernel: [    0.206125] pci 0000:00:1f.2: PME# disabled
Dec 12 12:35:22 fly kernel: [    0.206419] pci 0000:03:00.0: PME# supported from D3hot D3cold
Dec 12 12:35:22 fly kernel: [    0.206428] pci 0000:03:00.0: PME# disabled
Dec 12 12:35:22 fly kernel: [    0.206723] pci 0000:01:00.0: PME# supported from D0 D3hot
Dec 12 12:35:22 fly kernel: [    0.206732] pci 0000:01:00.0: PME# disabled
Dec 12 12:35:22 fly kernel: [    0.206908] pci 0000:00:1e.0: transparent bridge
Dec 12 12:35:22 fly kernel: [    0.226436] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Dec 12 12:35:22 fly kernel: [    0.226658] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Dec 12 12:35:22 fly kernel: [    0.226877] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 *7 10 11 12 14 15)
Dec 12 12:35:22 fly kernel: [    0.227103] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Dec 12 12:35:22 fly kernel: [    0.227321] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Dec 12 12:35:22 fly kernel: [    0.227547] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Dec 12 12:35:22 fly kernel: [    0.227766] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Dec 12 12:35:22 fly kernel: [    0.227986] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 10 11 12 14 15)
Dec 12 12:35:22 fly kernel: [    0.228407] SCSI subsystem initialized
Dec 12 12:35:22 fly kernel: [    0.228446] usbcore: registered new interface driver usbfs
Dec 12 12:35:22 fly kernel: [    0.228446] usbcore: registered new interface driver hub
Dec 12 12:35:22 fly kernel: [    0.228446] usbcore: registered new device driver usb
Dec 12 12:35:22 fly kernel: [    0.228446] ACPI: WMI: Mapper loaded
Dec 12 12:35:22 fly kernel: [    0.228446] PCI: Using ACPI for IRQ routing
Dec 12 12:35:22 fly kernel: [    0.240021] Bluetooth: Core ver 2.15
Dec 12 12:35:22 fly kernel: [    0.240067] NET: Registered protocol family 31
Dec 12 12:35:22 fly kernel: [    0.240067] Bluetooth: HCI device and connection manager initialized
Dec 12 12:35:22 fly kernel: [    0.240067] Bluetooth: HCI socket layer initialized
Dec 12 12:35:22 fly kernel: [    0.240067] NetLabel: Initializing
Dec 12 12:35:22 fly kernel: [    0.240067] NetLabel:  domain hash size = 128
Dec 12 12:35:22 fly kernel: [    0.240067] NetLabel:  protocols = UNLABELED CIPSOv4
Dec 12 12:35:22 fly kernel: [    0.240081] NetLabel:  unlabeled traffic allowed by default
Dec 12 12:35:22 fly kernel: [    0.240169] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Dec 12 12:35:22 fly kernel: [    0.240180] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
Dec 12 12:35:22 fly kernel: [    0.257085] pnp: PnP ACPI init
Dec 12 12:35:22 fly kernel: [    0.257125] ACPI: bus type pnp registered
Dec 12 12:35:22 fly kernel: [    0.260750] pnp: PnP ACPI: found 13 devices
Dec 12 12:35:22 fly kernel: [    0.260756] ACPI: ACPI bus type pnp unregistered
Dec 12 12:35:22 fly kernel: [    0.260764] PnPBIOS: Disabled by ACPI PNP
Dec 12 12:35:22 fly kernel: [    0.260790] system 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
Dec 12 12:35:22 fly kernel: [    0.260810] system 00:08: ioport range 0x25c-0x25f has been reserved
Dec 12 12:35:22 fly kernel: [    0.260817] system 00:08: ioport range 0x380-0x383 has been reserved
Dec 12 12:35:22 fly kernel: [    0.260824] system 00:08: ioport range 0x400-0x41f has been reserved
Dec 12 12:35:22 fly kernel: [    0.260831] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
Dec 12 12:35:22 fly kernel: [    0.260838] system 00:08: ioport range 0x800-0x87f has been reserved
Dec 12 12:35:22 fly kernel: [    0.260845] system 00:08: ioport range 0x480-0x4bf has been reserved
Dec 12 12:35:22 fly kernel: [    0.260853] system 00:08: iomem range 0x8c000000-0x8c01ffff has been reserved
Dec 12 12:35:22 fly kernel: [    0.260861] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
Dec 12 12:35:22 fly kernel: [    0.260868] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
Dec 12 12:35:22 fly kernel: [    0.260876] system 00:08: iomem range 0xfed50000-0xfed8ffff has been reserved
Dec 12 12:35:22 fly kernel: [    0.260883] system 00:08: iomem range 0xffb00000-0xffbfffff has been reserved
Dec 12 12:35:22 fly kernel: [    0.260891] system 00:08: iomem range 0xfff00000-0xffffffff could not be reserved
Dec 12 12:35:22 fly kernel: [    0.260905] system 00:0a: iomem range 0xfec00000-0xfec00fff could not be reserved
Dec 12 12:35:22 fly kernel: [    0.260912] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
Dec 12 12:35:22 fly kernel: [    0.260925] system 00:0b: iomem range 0xe0000000-0xe3ffffff has been reserved
Dec 12 12:35:22 fly kernel: [    0.260938] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
Dec 12 12:35:22 fly kernel: [    0.260945] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
Dec 12 12:35:22 fly kernel: [    0.260952] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
Dec 12 12:35:22 fly kernel: [    0.260959] system 00:0c: iomem range 0x100000-0x3f7fffff could not be reserved
Dec 12 12:35:22 fly kernel: [    0.295852] AppArmor: AppArmor Filesystem Enabled
Dec 12 12:35:22 fly kernel: [    0.295934] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:04
Dec 12 12:35:22 fly kernel: [    0.295939] pci 0000:00:1c.0:   IO window: disabled
Dec 12 12:35:22 fly kernel: [    0.295949] pci 0000:00:1c.0:   MEM window: disabled
Dec 12 12:35:22 fly kernel: [    0.295957] pci 0000:00:1c.0:   PREFETCH window: disabled
Dec 12 12:35:22 fly kernel: [    0.295966] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
Dec 12 12:35:22 fly kernel: [    0.295973] pci 0000:00:1c.1:   IO window: 0xe000-0xefff
Dec 12 12:35:22 fly kernel: [    0.295987] pci 0000:00:1c.1:   MEM window: 0xfbf00000-0xfbffffff
Dec 12 12:35:22 fly kernel: [    0.295996] pci 0000:00:1c.1:   PREFETCH window: disabled
Dec 12 12:35:22 fly kernel: [    0.296005] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:01
Dec 12 12:35:22 fly kernel: [    0.296009] pci 0000:00:1c.3:   IO window: disabled
Dec 12 12:35:22 fly kernel: [    0.296020] pci 0000:00:1c.3:   MEM window: 0xf8000000-0xfbefffff
Dec 12 12:35:22 fly kernel: [    0.296029] pci 0000:00:1c.3:   PREFETCH window: 0x000000f0000000-0x000000f6ffffff
Dec 12 12:35:22 fly kernel: [    0.296042] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
Dec 12 12:35:22 fly kernel: [    0.296047] pci 0000:00:1e.0:   IO window: disabled
Dec 12 12:35:22 fly kernel: [    0.296056] pci 0000:00:1e.0:   MEM window: disabled
Dec 12 12:35:22 fly kernel: [    0.296064] pci 0000:00:1e.0:   PREFETCH window: disabled
Dec 12 12:35:22 fly kernel: [    0.296107] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 12 12:35:22 fly kernel: [    0.296146] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Dec 12 12:35:22 fly kernel: [    0.296182] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Dec 12 12:35:22 fly kernel: [    0.296335] NET: Registered protocol family 2
Dec 12 12:35:22 fly kernel: [    0.296551] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Dec 12 12:35:22 fly kernel: [    0.297235] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Dec 12 12:35:22 fly kernel: [    0.298206] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Dec 12 12:35:22 fly kernel: [    0.298710] TCP: Hash tables configured (established 131072 bind 65536)
Dec 12 12:35:22 fly kernel: [    0.298716] TCP reno registered
Dec 12 12:35:22 fly kernel: [    0.298935] NET: Registered protocol family 1
Dec 12 12:35:22 fly kernel: [    0.299094] Trying to unpack rootfs image as initramfs...
Dec 12 12:35:22 fly kernel: [    0.404853] Freeing initrd memory: 2425k freed
Dec 12 12:35:22 fly kernel: [    0.407677] cpufreq-nforce2: No nForce2 chipset.
Dec 12 12:35:22 fly kernel: [    0.407746] Scanning for low memory corruption every 60 seconds
Dec 12 12:35:22 fly kernel: [    0.407971] audit: initializing netlink socket (disabled)
Dec 12 12:35:22 fly kernel: [    0.408013] type=2000 audit(1260617710.407:1): initialized
Dec 12 12:35:22 fly kernel: [    0.426238] highmem bounce pool size: 64 pages
Dec 12 12:35:22 fly kernel: [    0.426251] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Dec 12 12:35:22 fly kernel: [    0.429479] VFS: Disk quotas dquot_6.5.2
Dec 12 12:35:22 fly kernel: [    0.429613] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Dec 12 12:35:22 fly kernel: [    0.430897] fuse init (API version 7.12)
Dec 12 12:35:22 fly kernel: [    0.431096] msgmni has been set to 1732
Dec 12 12:35:22 fly kernel: [    0.431592] alg: No test for stdrng (krng)
Dec 12 12:35:22 fly kernel: [    0.431627] io scheduler noop registered
Dec 12 12:35:22 fly kernel: [    0.431632] io scheduler anticipatory registered
Dec 12 12:35:22 fly kernel: [    0.431637] io scheduler deadline registered
Dec 12 12:35:22 fly kernel: [    0.431742] io scheduler cfq registered (default)
Dec 12 12:35:22 fly kernel: [    0.432854] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Dec 12 12:35:22 fly kernel: [    0.433084] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Dec 12 12:35:22 fly kernel: [    0.433348] ACPI: AC Adapter [AC0] (off-line)
Dec 12 12:35:22 fly kernel: [    0.433491] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
Dec 12 12:35:22 fly kernel: [    0.433499] ACPI: Power Button [PWRF]
Dec 12 12:35:22 fly kernel: [    0.433618] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
Dec 12 12:35:22 fly kernel: [    0.434844] ACPI: EC: non-query interrupt received, switching to interrupt mode
Dec 12 12:35:22 fly kernel: [    0.447966] ACPI: Lid Switch [LID]
Dec 12 12:35:22 fly kernel: [    0.448091] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
Dec 12 12:35:22 fly kernel: [    0.448098] ACPI: Sleep Button [SLPB]
Dec 12 12:35:22 fly kernel: [    0.448195] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
Dec 12 12:35:22 fly kernel: [    0.448202] ACPI: Power Button [PWRB]
Dec 12 12:35:22 fly kernel: [    0.449523] ACPI: SSDT 3f7ae180 0023C (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
Dec 12 12:35:22 fly kernel: [    0.450499] ACPI: SSDT 3f7ae450 00724 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
Dec 12 12:35:22 fly kernel: [    0.451378] Marking TSC unstable due to TSC halts in idle
Dec 12 12:35:22 fly kernel: [    0.451465] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Dec 12 12:35:22 fly kernel: [    0.451526] processor LNXCPU:00: registered as cooling_device0
Dec 12 12:35:22 fly kernel: [    0.451535] ACPI: Processor [CPU0] (supports 8 throttling states)
Dec 12 12:35:22 fly kernel: [    0.452281] ACPI: SSDT 3f7ae0b0 000CC (v01  PmRef  Cpu1Ist 00003000 INTL 20051117)
Dec 12 12:35:22 fly kernel: [    0.452902] ACPI: SSDT 3f7ae3c0 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20051117)
Dec 12 12:35:22 fly kernel: [    0.453903] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
Dec 12 12:35:22 fly kernel: [    0.453954] processor LNXCPU:01: registered as cooling_device1
Dec 12 12:35:22 fly kernel: [    0.453963] ACPI: Processor [CPU1] (supports 8 throttling states)
Dec 12 12:35:22 fly kernel: [    0.477151] thermal LNXTHERM:01: registered as thermal_zone0
Dec 12 12:35:22 fly kernel: [    0.477170] ACPI: Thermal Zone [TZ00] (49 C)
Dec 12 12:35:22 fly kernel: [    0.477311] isapnp: Scanning for PnP cards...
Dec 12 12:35:22 fly kernel: [    0.740748] ACPI: Battery Slot [BAT0] (battery present)
Dec 12 12:35:22 fly kernel: [    0.831986] isapnp: No Plug & Play device found
Dec 12 12:35:22 fly kernel: [    0.834781] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Dec 12 12:35:22 fly kernel: [    0.837504] brd: module loaded
Dec 12 12:35:22 fly kernel: [    0.838510] loop: module loaded
Dec 12 12:35:22 fly kernel: [    0.838684] input: Macintosh mouse button emulation as /devices/virtual/input/input4
Dec 12 12:35:22 fly kernel: [    0.838951] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Dec 12 12:35:22 fly kernel: [    0.838962] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
Dec 12 12:35:22 fly kernel: [    0.839206] scsi0 : ata_piix
Dec 12 12:35:22 fly kernel: [    0.839415] scsi1 : ata_piix
Dec 12 12:35:22 fly kernel: [    0.842291] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
Dec 12 12:35:22 fly kernel: [    0.842299] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
Dec 12 12:35:22 fly kernel: [    0.844226] Fixed MDIO Bus: probed
Dec 12 12:35:22 fly kernel: [    0.844315] PPP generic driver version 2.4.2
Dec 12 12:35:22 fly kernel: [    0.844531] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Dec 12 12:35:22 fly kernel: [    0.844597] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Dec 12 12:35:22 fly kernel: [    0.844635] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Dec 12 12:35:22 fly kernel: [    0.844737] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
Dec 12 12:35:22 fly kernel: [    0.848662] ehci_hcd 0000:00:1d.7: debug port 1
Dec 12 12:35:22 fly kernel: [    0.848702] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf7eb7c00
Dec 12 12:35:22 fly kernel: [    0.864033] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Dec 12 12:35:22 fly kernel: [    0.864205] usb usb1: configuration #1 chosen from 1 choice
Dec 12 12:35:22 fly kernel: [    0.864278] hub 1-0:1.0: USB hub found
Dec 12 12:35:22 fly kernel: [    0.864295] hub 1-0:1.0: 8 ports detected
Dec 12 12:35:22 fly kernel: [    0.864452] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Dec 12 12:35:22 fly kernel: [    0.864498] uhci_hcd: USB Universal Host Controller Interface driver
Dec 12 12:35:22 fly kernel: [    0.864583] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Dec 12 12:35:22 fly kernel: [    0.864605] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Dec 12 12:35:22 fly kernel: [    0.864679] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Dec 12 12:35:22 fly kernel: [    0.864721] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d400
Dec 12 12:35:22 fly kernel: [    0.864908] usb usb2: configuration #1 chosen from 1 choice
Dec 12 12:35:22 fly kernel: [    0.864969] hub 2-0:1.0: USB hub found
Dec 12 12:35:22 fly kernel: [    0.864985] hub 2-0:1.0: 2 ports detected
Dec 12 12:35:22 fly kernel: [    0.865080] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Dec 12 12:35:22 fly kernel: [    0.865100] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Dec 12 12:35:22 fly kernel: [    0.865165] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
Dec 12 12:35:22 fly kernel: [    0.865217] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d480
Dec 12 12:35:22 fly kernel: [    0.865386] usb usb3: configuration #1 chosen from 1 choice
Dec 12 12:35:22 fly kernel: [    0.865446] hub 3-0:1.0: USB hub found
Dec 12 12:35:22 fly kernel: [    0.865461] hub 3-0:1.0: 2 ports detected
Dec 12 12:35:22 fly kernel: [    0.865571] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Dec 12 12:35:22 fly kernel: [    0.865590] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Dec 12 12:35:22 fly kernel: [    0.865658] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
Dec 12 12:35:22 fly kernel: [    0.865710] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d800
Dec 12 12:35:22 fly kernel: [    0.865882] usb usb4: configuration #1 chosen from 1 choice
Dec 12 12:35:22 fly kernel: [    0.865942] hub 4-0:1.0: USB hub found
Dec 12 12:35:22 fly kernel: [    0.865957] hub 4-0:1.0: 2 ports detected
Dec 12 12:35:22 fly kernel: [    0.866047] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
Dec 12 12:35:22 fly kernel: [    0.866067] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Dec 12 12:35:22 fly kernel: [    0.866139] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
Dec 12 12:35:22 fly kernel: [    0.866188] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d880
Dec 12 12:35:22 fly kernel: [    0.866360] usb usb5: configuration #1 chosen from 1 choice
Dec 12 12:35:22 fly kernel: [    0.866422] hub 5-0:1.0: USB hub found
Dec 12 12:35:22 fly kernel: [    0.866436] hub 5-0:1.0: 2 ports detected
Dec 12 12:35:22 fly kernel: [    0.866635] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Dec 12 12:35:22 fly kernel: [    0.898349] serio: i8042 KBD port at 0x60,0x64 irq 1
Dec 12 12:35:22 fly kernel: [    0.898364] serio: i8042 AUX port at 0x60,0x64 irq 12
Dec 12 12:35:22 fly kernel: [    0.898492] mice: PS/2 mouse device common for all mice
Dec 12 12:35:22 fly kernel: [    0.898774] rtc_cmos 00:03: RTC can wake from S4
Dec 12 12:35:22 fly kernel: [    0.898845] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Dec 12 12:35:22 fly kernel: [    0.898889] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
Dec 12 12:35:22 fly kernel: [    0.899146] device-mapper: uevent: version 1.0.3
Dec 12 12:35:22 fly kernel: [    0.900775] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
Dec 12 12:35:22 fly kernel: [    0.900972] device-mapper: multipath: version 1.1.0 loaded
Dec 12 12:35:22 fly kernel: [    0.900979] device-mapper: multipath round-robin: version 1.0.0 loaded
Dec 12 12:35:22 fly kernel: [    0.901283] EISA: Probing bus 0 at eisa.0
Dec 12 12:35:22 fly kernel: [    0.901326] EISA: Detected 0 cards.
Dec 12 12:35:22 fly kernel: [    0.901728] cpuidle: using governor ladder
Dec 12 12:35:22 fly kernel: [    0.901985] cpuidle: using governor menu
Dec 12 12:35:22 fly kernel: [    0.903112] TCP cubic registered
Dec 12 12:35:22 fly kernel: [    0.903491] NET: Registered protocol family 10
Dec 12 12:35:22 fly kernel: [    0.904499] lo: Disabled Privacy Extensions
Dec 12 12:35:22 fly kernel: [    0.905229] NET: Registered protocol family 17
Dec 12 12:35:22 fly kernel: [    0.905275] Bluetooth: L2CAP ver 2.13
Dec 12 12:35:22 fly kernel: [    0.905279] Bluetooth: L2CAP socket layer initialized
Dec 12 12:35:22 fly kernel: [    0.905285] Bluetooth: SCO (Voice Link) ver 0.6
Dec 12 12:35:22 fly kernel: [    0.905289] Bluetooth: SCO socket layer initialized
Dec 12 12:35:22 fly kernel: [    0.905397] Bluetooth: RFCOMM TTY layer initialized
Dec 12 12:35:22 fly kernel: [    0.905404] Bluetooth: RFCOMM socket layer initialized
Dec 12 12:35:22 fly kernel: [    0.905408] Bluetooth: RFCOMM ver 1.11
Dec 12 12:35:22 fly kernel: [    0.906252] Using IPI No-Shortcut mode
Dec 12 12:35:22 fly kernel: [    0.906448] registered taskstats version 1
Dec 12 12:35:22 fly kernel: [    0.906662]   Magic number: 5:134:580
Dec 12 12:35:22 fly kernel: [    0.906721] pci_bus 0000:01: hash matches
Dec 12 12:35:22 fly kernel: [    0.906802] rtc_cmos 00:03: setting system clock to 2009-12-12 11:35:12 UTC (1260617712)
Dec 12 12:35:22 fly kernel: [    0.906811] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Dec 12 12:35:22 fly kernel: [    0.906815] EDD information not available.
Dec 12 12:35:22 fly kernel: [    0.925494] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
Dec 12 12:35:22 fly kernel: [    1.001133] Clocksource tsc unstable (delta = -79935226 ns)
Dec 12 12:35:22 fly kernel: [    1.005596] ata1.00: ATA-8: ST9160827AS, 3.AAA, max UDMA/133
Dec 12 12:35:22 fly kernel: [    1.005605] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
Dec 12 12:35:22 fly kernel: [    1.020627] ata1.00: configured for UDMA/133
Dec 12 12:35:22 fly kernel: [    1.020864] scsi 0:0:0:0: Direct-Access     ATA      ST9160827AS      3.AA PQ: 0 ANSI: 5
Dec 12 12:35:22 fly kernel: [    1.021172] sd 0:0:0:0: Attached scsi generic sg0 type 0
Dec 12 12:35:22 fly kernel: [    1.021286] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
Dec 12 12:35:22 fly kernel: [    1.021420] sd 0:0:0:0: [sda] Write Protect is off
Dec 12 12:35:22 fly kernel: [    1.021498] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 12 12:35:22 fly kernel: [    1.021846]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 >
Dec 12 12:35:22 fly kernel: [    1.114193] sd 0:0:0:0: [sda] Attached SCSI disk
Dec 12 12:35:22 fly kernel: [    1.114251] Freeing unused kernel memory: 540k freed
Dec 12 12:35:22 fly kernel: [    1.114739] Write protecting the kernel text: 4568k
Dec 12 12:35:22 fly kernel: [    1.114820] Write protecting the kernel read-only data: 1836k
Dec 12 12:35:22 fly kernel: [    1.232102] usb 1-5: new high speed USB device using ehci_hcd and address 3
Dec 12 12:35:22 fly kernel: [    1.369864] usb 1-5: configuration #1 chosen from 1 choice
Dec 12 12:35:22 fly kernel: [    1.608115] usb 1-8: new high speed USB device using ehci_hcd and address 5
Dec 12 12:35:22 fly kernel: [    1.799009] usb 1-8: configuration #1 chosen from 1 choice
Dec 12 12:35:22 fly kernel: [    2.040141] usb 3-1: new low speed USB device using uhci_hcd and address 2
Dec 12 12:35:22 fly kernel: [    2.110619] PM: Starting manual resume from disk
Dec 12 12:35:22 fly kernel: [    2.223559] usb 3-1: configuration #1 chosen from 1 choice
Dec 12 12:35:22 fly kernel: [    2.484140] usb 5-1: new full speed USB device using uhci_hcd and address 2
Dec 12 12:35:22 fly kernel: [    2.652495] usb 5-1: configuration #1 chosen from 1 choice
Dec 12 12:35:22 fly kernel: [    2.809922] type=1505 audit(1260617714.401:2): operation="profile_load" pid=368 name=/sbin/dhclient3
Dec 12 12:35:22 fly kernel: [    2.810528] type=1505 audit(1260617714.401:3): operation="profile_load" pid=368 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Dec 12 12:35:22 fly kernel: [    2.810870] type=1505 audit(1260617714.401:4): operation="profile_load" pid=368 name=/usr/lib/connman/scripts/dhclient-script
Dec 12 12:35:22 fly kernel: [    2.843089] type=1505 audit(1260617714.433:5): operation="profile_load" pid=369 name=/usr/bin/evince
Dec 12 12:35:22 fly kernel: [    2.852449] type=1505 audit(1260617714.445:6): operation="profile_load" pid=369 name=/usr/bin/evince-previewer
Dec 12 12:35:22 fly kernel: [    2.858149] type=1505 audit(1260617714.449:7): operation="profile_load" pid=369 name=/usr/bin/evince-thumbnailer
Dec 12 12:35:22 fly kernel: [    2.874574] type=1505 audit(1260617714.465:8): operation="profile_load" pid=371 name=/usr/sbin/tcpdump
Dec 12 12:35:22 fly kernel: [    3.573546] Adding 996020k swap on /dev/sda2.  Priority:-1 extents:1 across:996020k 
Dec 12 12:35:22 fly kernel: [    4.219265] udev: starting version 147
Dec 12 12:35:22 fly kernel: [    4.928121] Linux video capture interface: v2.00
Dec 12 12:35:22 fly kernel: [    4.952133] uvcvideo: Found UVC 1.00 device CNF7129 (04f2:b071)
Dec 12 12:35:22 fly kernel: [    4.969283] input: CNF7129 as /devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/input/input6
Dec 12 12:35:22 fly kernel: [    4.969510] usbcore: registered new interface driver uvcvideo
Dec 12 12:35:22 fly kernel: [    4.969525] USB Video Class driver (v0.1.0)
Dec 12 12:35:22 fly kernel: [    5.383979] usbcore: registered new interface driver hiddev
Dec 12 12:35:22 fly kernel: [    5.402273] input: Genius 4D Scroll Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input7
Dec 12 12:35:22 fly kernel: [    5.402661] generic-usb 0003:0458:0056.0001: input,hidraw0: USB HID v1.10 Mouse [Genius 4D Scroll Mouse] on usb-0000:00:1d.1-1/input0
Dec 12 12:35:22 fly kernel: [    5.402722] usbcore: registered new interface driver usbhid
Dec 12 12:35:22 fly kernel: [    5.402736] usbhid: v2.6:USB HID core driver
Dec 12 12:35:22 fly kernel: [    5.658850] ip_tables: (C) 2000-2006 Netfilter Core Team
Dec 12 12:35:22 fly kernel: [    5.934803] eeepc_laptop: Eee PC Hotkey Driver
Dec 12 12:35:22 fly kernel: [    5.936292] eeepc_laptop: Hotkey init flags 0x41
Dec 12 12:35:22 fly kernel: [    5.936997] eeepc_laptop: TYPE (2000000) not reported by BIOS, enabling anyway
Dec 12 12:35:22 fly kernel: [    5.946812] eeepc_laptop: PANELPOWER (4000000) not reported by BIOS, enabling anyway
Dec 12 12:35:22 fly kernel: [    5.946830] eeepc_laptop: Get control methods supported: 0x6101713
Dec 12 12:35:22 fly kernel: [    5.947010] input: Asus EeePC extra buttons as /devices/virtual/input/input8
Dec 12 12:35:22 fly kernel: [    5.970957] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 12 12:35:22 fly kernel: [    6.124114] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:19/input/input9
Dec 12 12:35:22 fly kernel: [    6.124201] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Dec 12 12:35:22 fly kernel: [    6.182827] Linux agpgart interface v0.103
Dec 12 12:35:22 fly kernel: [    6.300776] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input10
Dec 12 12:35:22 fly kernel: [    6.419585] intel_rng: FWH not detected
Dec 12 12:35:22 fly kernel: [    6.471189] Initializing USB Mass Storage driver...
Dec 12 12:35:22 fly kernel: [    6.471613] scsi2 : SCSI emulation for USB Mass Storage devices
Dec 12 12:35:22 fly kernel: [    6.481633] agpgart-intel 0000:00:00.0: Intel 945GME Chipset
Dec 12 12:35:22 fly kernel: [    6.482259] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
Dec 12 12:35:22 fly kernel: [    6.483707] usbcore: registered new interface driver usb-storage
Dec 12 12:35:22 fly kernel: [    6.483719] USB Mass Storage support registered.
Dec 12 12:35:22 fly kernel: [    6.485455] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
Dec 12 12:35:22 fly kernel: [    6.663015] rt2860sta: module is from the staging directory, the quality is unknown, you have been warned.
Dec 12 12:35:22 fly kernel: [    6.671308] rt2860 0000:01:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Dec 12 12:35:22 fly kernel: [    6.671793] 
Dec 12 12:35:22 fly kernel: [    6.671797] 
Dec 12 12:35:22 fly kernel: [    6.671799] === pAd = f861e000, size = 580808 ===
Dec 12 12:35:22 fly kernel: [    6.671802] 
Dec 12 12:35:22 fly kernel: [    6.671810] <-- RTMPAllocAdapterBlock, Status=0
Dec 12 12:35:22 fly kernel: [    6.695706] Bluetooth: Generic Bluetooth USB driver ver 0.5
Dec 12 12:35:22 fly kernel: [    6.848632] [drm] Initialized drm 1.1.0 20060810
Dec 12 12:35:22 fly kernel: [    6.931262] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 12 12:35:22 fly kernel: [    7.173000] lp: driver loaded but no devices found
Dec 12 12:35:22 fly kernel: [    7.190601] ATL1E 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Dec 12 12:35:22 fly kernel: [    7.276308] [drm] fb0: inteldrmfb frame buffer device
Dec 12 12:35:22 fly kernel: [    7.276330] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Dec 12 12:35:22 fly kernel: [    7.285674] elantech.c: assuming hardware version 2, firmware version 2.48
Dec 12 12:35:22 fly kernel: [    7.360976] elantech.c: Synaptics capabilities query result 0x00, 0x02, 0x64.
Dec 12 12:35:22 fly kernel: [    7.486775] [drm] DAC-6: set mode 1280x1024 1d
Dec 12 12:35:22 fly kernel: [    7.571939] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio1/input/input11
Dec 12 12:35:22 fly kernel: [    7.798373] [drm] LVDS-8: set mode 1024x600 1e
Dec 12 12:35:22 fly kernel: [    8.155156] Console: switching to colour frame buffer device 128x37
Dec 12 12:35:22 fly kernel: [    8.412397] kjournald starting.  Commit interval 5 seconds
Dec 12 12:35:22 fly kernel: [    8.412785] EXT3 FS on sda5, internal journal
Dec 12 12:35:22 fly kernel: [    8.412805] EXT3-fs: mounted filesystem with writeback data mode.
Dec 12 12:35:22 fly kernel: [    8.658272] usbcore: registered new interface driver btusb
Dec 12 12:35:22 fly kernel: [    9.026940] REISERFS (device sda7): found reiserfs format "3.6" with standard journal
Dec 12 12:35:22 fly kernel: [    9.026987] REISERFS (device sda7): using ordered data mode
Dec 12 12:35:22 fly kernel: [    9.038220] REISERFS (device sda7): journal params: device sda7, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
Dec 12 12:35:22 fly kernel: [    9.038929] REISERFS (device sda7): checking transaction log (sda7)
Dec 12 12:35:22 fly kernel: [    9.064111] REISERFS (device sda7): Using r5 hash to sort names
Dec 12 12:35:22 fly kernel: [    9.131137] REISERFS (device sda7): Removing [299 2508 0x0 SD]..done
Dec 12 12:35:22 fly kernel: [    9.131821] REISERFS (device sda7): Removing [299 2171 0x0 SD]..done
Dec 12 12:35:22 fly kernel: [    9.131941] REISERFS (device sda7): There were 2 uncompleted unlinks/truncates. Completed
Dec 12 12:35:22 fly kernel: [   11.276447] RX DESC f6791000  size = 2048
Dec 12 12:35:22 fly kernel: [   11.276936] <-- RTMPAllocTxRxRingMemory, Status=0
Dec 12 12:35:22 fly kernel: [   11.280823] --> Error 2 opening /etc/Wireless/RT2860STA/RT2860STA.dat
Dec 12 12:35:22 fly kernel: [   11.280834] 1. Phy Mode = 0
Dec 12 12:35:22 fly kernel: [   11.280840] 2. Phy Mode = 0
Dec 12 12:35:22 fly kernel: [   11.301312] RTMPSetPhyMode: channel is out of range, use first channel=1 
Dec 12 12:35:22 fly kernel: [   11.307611] 3. Phy Mode = 0
Dec 12 12:35:22 fly kernel: [   11.330410] MCS Set = 00 00 00 00 00
Dec 12 12:35:22 fly kernel: [   11.332051] <==== RTMPInitialize, Status=0
Dec 12 12:35:22 fly kernel: [   11.332128] 0x1300 = 00073200
Dec 12 12:35:23 fly kernel: [   11.481263] scsi 2:0:0:0: Direct-Access     Single   Flash Reader     1.00 PQ: 0 ANSI: 0
Dec 12 12:35:23 fly kernel: [   11.482697] sd 2:0:0:0: Attached scsi generic sg1 type 0
Dec 12 12:35:23 fly kernel: [   12.134827] sd 2:0:0:0: [sdb] 3935232 512-byte logical blocks: (2.01 GB/1.87 GiB)
Dec 12 12:35:23 fly kernel: [   12.136001] sd 2:0:0:0: [sdb] Write Protect is off
Dec 12 12:35:23 fly kernel: [   12.145455]  sdb: sdb1
Dec 12 12:35:23 fly kernel: [   12.165885] sd 2:0:0:0: [sdb] Attached SCSI removable disk
Dec 12 12:35:24 fly kernel: [   12.408155] type=1505 audit(1260617724.001:9): operation="profile_replace" pid=909 name=/sbin/dhclient3
Dec 12 12:35:24 fly kernel: [   12.409083] type=1505 audit(1260617724.001:10): operation="profile_replace" pid=909 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Dec 12 12:35:24 fly kernel: [   12.409467] type=1505 audit(1260617724.001:11): operation="profile_replace" pid=909 name=/usr/lib/connman/scripts/dhclient-script
Dec 12 12:35:24 fly kernel: [   12.419300] type=1505 audit(1260617724.009:12): operation="profile_replace" pid=910 name=/usr/bin/evince
Dec 12 12:35:24 fly kernel: [   12.436658] type=1505 audit(1260617724.029:13): operation="profile_replace" pid=910 name=/usr/bin/evince-previewer
Dec 12 12:35:24 fly kernel: [   12.445145] type=1505 audit(1260617724.037:14): operation="profile_replace" pid=910 name=/usr/bin/evince-thumbnailer
Dec 12 12:35:24 fly kernel: [   12.460137] type=1505 audit(1260617724.053:15): operation="profile_replace" pid=912 name=/usr/sbin/tcpdump
Dec 12 12:35:26 fly kernel: [   14.827269] [drm] DAC-6: set mode 800x600 21
Dec 12 12:35:27 fly kernel: [   15.140089] [drm] LVDS-8: set mode 800x600 22
Dec 12 12:35:29 fly kernel: [   17.437150] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1069
Dec 12 12:35:33 fly kernel: [   22.356043] ERROR!!! RTMPCancelTimer failed, Timer hasn't been initialize!
Dec 12 12:35:45 fly kernel: [   33.385683] [drm] DAC-6: set mode 1280x1024 1d
Dec 12 12:35:45 fly kernel: [   33.697303] [drm] LVDS-8: set mode 1024x600 1e
Dec 12 12:35:49 fly kernel: [   37.420141] ===>rt_ioctl_giwscan. 8(8) BSS returned, data->length = 977

---

