---
title: "External hard disk drive doesn't show on fdisk -l or lsusb"
date: 2011-10-30
forum: Hardware
---

### Post by mrblue8 on 2011-10-30
Hello,

I bought an external hdd but KUbuntu 10.04 doesn't recognise it. I have tried all the USB ports as well as typing *fdisk -l* and *lsusb* but none of them show the Samsung drive. The light on the drive is lit and I haven't tested it on a Windows PC yet.

Here are the outputs of *fdisk - l*, *lsusb* and *dmesg*

```
administrador@computador:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6c3c55d4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12166    97723363+  83  Linux
/dev/sda2           12167       13382     9767520   82  Linux swap / Solaris
/dev/sda3           13383       38913   205077757+  83  Linux
administrador@computador:~$ lsusb
Bus 002 Device 005: ID 043d:007b Lexmark International, Inc. InkJet Color Printer
Bus 002 Device 004: ID 043d:007c Lexmark International, Inc. Lexmark X1110/X1130/X1140/X1150/X1170/X1180/X1185
Bus 002 Device 003: ID 043d:007a Lexmark International, Inc. Generic Hub
Bus 002 Device 002: ID 04f2:0719 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
administrador@computador:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-34-generic-pae (buildd@vernadsky) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #77-Ubuntu SMP Tue Sep 13 21:16:18 UTC 2011 (Ubuntu 2.6.32-34.77-generic-pae 2.6.32.44+drm33.19)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e7000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000affb0000 (usable)
[    0.000000]  BIOS-e820: 00000000affb0000 - 00000000affc0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000affc0000 - 00000000afff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000afff0000 - 00000000b0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFE0000000 write-back
[    0.000000]   2 base 0000A0000000 mask FFFFF0000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000140000000 aka 5120M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000b0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e7000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000affb0000 (usable)
[    0.000000]  modified: 00000000affb0000 - 00000000affc0000 (ACPI data)
[    0.000000]  modified: 00000000affc0000 - 00000000afff0000 (ACPI NVS)
[    0.000000]  modified: 00000000afff0000 - 00000000b0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] initial memory mapped : 0 - 00e00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000379fe000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037800000 page 2M
[    0.000000]  0037800000 - 00379fe000 page 4k
[    0.000000] kernel direct mapping tables up to 379fe000 @ 10000-16000
[    0.000000] RAMDISK: 3785a000 - 37fef970
[    0.000000] Allocated new RAMDISK: 00941000 - 010d6970
[    0.000000] Move RAMDISK from 000000003785a000 - 0000000037fef96f to 00941000 - 010d696f
[    0.000000] ACPI: RSDP 000fabf0 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT affb0000 0003C (v01 A_M_I  OEMRSDT  01000908 MSFT 00000097)
[    0.000000] ACPI: FACP affb0200 00084 (v02 A M I  OEMFACP  12000601 MSFT 00000097)
[    0.000000] ACPI: DSDT affb0450 04729 (v01  AS164 AS164133 00000133 INTL 20051117)
[    0.000000] ACPI: FACS affc0000 00040
[    0.000000] ACPI: APIC affb0390 00080 (v01 A_M_I  OEMAPIC  01000908 MSFT 00000097)
[    0.000000] ACPI: MCFG affb0410 0003C (v01 A_M_I  OEMMCFG  01000908 MSFT 00000097)
[    0.000000] ACPI: OEMB affc0040 00060 (v01 A_M_I  AMI_OEM  01000908 MSFT 00000097)
[    0.000000] ACPI: AAFT affb4b80 00027 (v01 A_M_I  OEMAAFT  01000908 MSFT 00000097)
[    0.000000] ACPI: SSDT affb4bb0 003FC (v01 A M I  POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 4230MB HIGHMEM available.
[    0.000000] 889MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 379fe000
[    0.000000]   low ram: 0 - 379fe000
[    0.000000]   node 0 low ram: 00000000 - 379fe000
[    0.000000]   node 0 bootmap 00012000 - 00018f40
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00379fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 0000938818]    TEXT DATA BSS ==> [0000100000 - 0000938818]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [0000939000 - 000094012b]              BRK ==> [0000939000 - 000094012b]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [0000941000 - 00010d6970]      NEW RAMDISK ==> [0000941000 - 00010d6970]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000379fe
[    0.000000]   HighMem  0x000379fe -> 0x00140000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000affb0
[    0.000000]     0: 0x00100000 -> 0x00140000
[    0.000000] On node 0 totalpages: 982847
[    0.000000] free_area_init_node: node 0, pgdat c07d8e00, node_mem_map c10d8200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1748 pages used for memmap
[    0.000000]   Normal zone: 221994 pages, LIFO batch:31
[    0.000000]   HighMem zone: 8461 pages used for memmap
[    0.000000]   HighMem zone: 746661 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x03] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 3, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 1 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e7000
[    0.000000] PM: Registered nosave memory: 00000000000e7000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at b0000000 (gap: b0000000:4ec00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 15 pages/cpu @c3a00000 s39736 r0 d21704 u524288
[    0.000000] pcpu-alloc: s39736 r0 d21704 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 972606
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-34-generic-pae root=UUID=92f1548d-0211-4740-a195-2a51ff02f541 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 26214080 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000379fe:00140000)
[    0.000000] Memory: 3846304k/5242880k available (4832k kernel code, 83908k reserved, 2221k data, 684k init, 3020488k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xffa00000 - 0xffc00000   (2048 kB)
[    0.000000]     vmalloc : 0xf81fe000 - 0xff9fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf79fe000   ( 889 MB)
[    0.000000]       .init : 0xc07e4000 - 0xc088f000   ( 684 kB)
[    0.000000]       .data : 0xc05b815f - 0xc07e3788   (2221 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05b815f   (4832 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:440
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2109.677 MHz processor.
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 4219.35 BogoMIPS (lpj=8438708)
[    0.004020] Security Framework initialized
[    0.004039] AppArmor: AppArmor initialized
[    0.004046] Mount-cache hash table entries: 512
[    0.004157] Initializing cgroup subsys ns
[    0.004161] Initializing cgroup subsys cpuacct
[    0.004165] Initializing cgroup subsys memory
[    0.004172] Initializing cgroup subsys devices
[    0.004174] Initializing cgroup subsys freezer
[    0.004177] Initializing cgroup subsys net_cls
[    0.004194] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004197] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004199] CPU: Physical Processor ID: 0
[    0.004201] CPU: Processor Core ID: 0
[    0.004205] mce: CPU supports 6 MCE banks
[    0.004215] using C1E aware idle routine
[    0.004221] Performance Events: AMD PMU driver.
[    0.004225] ... version:                0
[    0.004227] ... bit width:              48
[    0.004229] ... generic registers:      4
[    0.004231] ... value mask:             0000ffffffffffff
[    0.004233] ... max period:             00007fffffffffff
[    0.004235] ... fixed-purpose events:   0
[    0.004237] ... event mask:             000000000000000f
[    0.004241] Checking 'hlt' instruction... OK.
[    0.022268] ACPI: Core revision 20090903
[    0.030122] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.030127] ftrace: allocating 22362 entries in 44 pages
[    0.032077] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.032542] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.073221] CPU0: AMD Phenom(tm) 8450 Triple-Core Processor stepping 03
[    0.076001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.008000] Initializing CPU#1
[    0.008000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.008000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 1
[    0.160037] CPU1: AMD Phenom(tm) 8450 Triple-Core Processor stepping 03
[    0.160045] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.164070] Booting processor 2 APIC 0x2 ip 0x6000
[    0.008000] Initializing CPU#2
[    0.008000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.008000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 2
[    0.252090] CPU2: AMD Phenom(tm) 8450 Triple-Core Processor stepping 03
[    0.252098] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.256012] Brought up 3 CPUs
[    0.256015] Total of 3 processors activated (12658.50 BogoMIPS).
[    0.257157] CPU0 attaching sched-domain:
[    0.257163]  domain 0: span 0-2 level MC
[    0.257166]   groups: 0 1 2
[    0.257174] CPU1 attaching sched-domain:
[    0.257176]  domain 0: span 0-2 level MC
[    0.257178]   groups: 1 2 0
[    0.257182] CPU2 attaching sched-domain:
[    0.257184]  domain 0: span 0-2 level MC
[    0.257186]   groups: 2 0 1
[    0.257280] devtmpfs: initialized
[    0.257280] regulator: core version 0.5
[    0.257280] Time: 19:10:46  Date: 10/30/11
[    0.257280] NET: Registered protocol family 16
[    0.257280] Trying to unpack rootfs image as initramfs...
[    0.257280] EISA bus registered
[    0.257280] ACPI: bus type pci registered
[    0.257280] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.257280] PCI: Not using MMCONFIG.
[    0.257280] PCI: Using configuration type 1 for base access
[    0.257280] PCI: Using configuration type 1 for extended access
[    0.257844] bio: create slab <bio-0> at 0
[    0.260664] ACPI: EC: Look up EC in DSDT
[    0.263561] ACPI: Executed 1 blocks of module-level executable AML code
[    0.268320] ACPI: Interpreter enabled
[    0.268323] ACPI: (supports S0 S1 S4 S5)
[    0.268342] ACPI: Using IOAPIC for interrupt routing
[    0.268389] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.272391] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.272394] PCI: Using MMCONFIG for extended config space
[    0.279617] ACPI Warning: Incorrect checksum in table [OEMB] - 8E, should be 89 (20090903/tbutils-314)
[    0.279725] ACPI: No dock devices found.
[    0.279841] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.280057] pci 0000:00:01.1: reg 10 io port: [0xec00-0xec3f]
[    0.280068] pci 0000:00:01.1: reg 20 io port: [0x5000-0x503f]
[    0.280073] pci 0000:00:01.1: reg 24 io port: [0x6000-0x603f]
[    0.280093] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.280099] pci 0000:00:01.1: PME# disabled
[    0.280147] pci 0000:00:02.0: reg 10 32bit mmio: [0xdffff000-0xdfffffff]
[    0.280170] pci 0000:00:02.0: supports D1 D2
[    0.280172] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.280175] pci 0000:00:02.0: PME# disabled
[    0.280198] pci 0000:00:02.1: reg 10 32bit mmio: [0xdfffec00-0xdfffecff]
[    0.280224] pci 0000:00:02.1: supports D1 D2
[    0.280227] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.280230] pci 0000:00:02.1: PME# disabled
[    0.280293] pci 0000:00:05.0: reg 10 32bit mmio: [0xdfff8000-0xdfffbfff]
[    0.280320] pci 0000:00:05.0: PME# supported from D3hot D3cold
[    0.280323] pci 0000:00:05.0: PME# disabled
[    0.280356] pci 0000:00:06.0: reg 20 io port: [0xffa0-0xffaf]
[    0.280392] pci 0000:00:07.0: reg 10 32bit mmio: [0xdfffd000-0xdfffdfff]
[    0.280397] pci 0000:00:07.0: reg 14 io port: [0xe480-0xe487]
[    0.280419] pci 0000:00:07.0: supports D1 D2
[    0.280421] pci 0000:00:07.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.280426] pci 0000:00:07.0: PME# disabled
[    0.280447] pci 0000:00:08.0: reg 10 io port: [0xe400-0xe407]
[    0.280451] pci 0000:00:08.0: reg 14 io port: [0xe080-0xe083]
[    0.280455] pci 0000:00:08.0: reg 18 io port: [0xe000-0xe007]
[    0.280459] pci 0000:00:08.0: reg 1c io port: [0xdc00-0xdc03]
[    0.280463] pci 0000:00:08.0: reg 20 io port: [0xd880-0xd88f]
[    0.280467] pci 0000:00:08.0: reg 24 32bit mmio: [0xdfffc000-0xdfffcfff]
[    0.280498] pci 0000:00:08.1: reg 10 io port: [0xd800-0xd807]
[    0.280502] pci 0000:00:08.1: reg 14 io port: [0xd480-0xd483]
[    0.280506] pci 0000:00:08.1: reg 18 io port: [0xd400-0xd407]
[    0.280510] pci 0000:00:08.1: reg 1c io port: [0xd080-0xd083]
[    0.280513] pci 0000:00:08.1: reg 20 io port: [0xd000-0xd00f]
[    0.280518] pci 0000:00:08.1: reg 24 32bit mmio: [0xdfff7000-0xdfff7fff]
[    0.280570] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.280573] pci 0000:00:09.0: PME# disabled
[    0.280610] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.280613] pci 0000:00:0b.0: PME# disabled
[    0.280648] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.280651] pci 0000:00:0c.0: PME# disabled
[    0.280669] pci 0000:00:0d.0: reg 10 32bit mmio: [0xde000000-0xdeffffff]
[    0.280674] pci 0000:00:0d.0: reg 14 64bit mmio pref: [0xc0000000-0xcfffffff]
[    0.280680] pci 0000:00:0d.0: reg 1c 64bit mmio: [0xdd000000-0xddffffff]
[    0.280685] pci 0000:00:0d.0: reg 30 32bit mmio pref: [0xdffc0000-0xdffdffff]
[    0.280813] pci 0000:00:04.0: transparent bridge
[    0.280927] pci_bus 0000:00: on NUMA node 0
[    0.280931] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.281104] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.281187] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR10._PRT]
[    0.281247] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR11._PRT]
[    0.281308] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR12._PRT]
[    0.289203] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
[    0.289398] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.
[    0.289590] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[    0.289782] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
[    0.289973] ACPI: PCI Interrupt Link [LNEA] (IRQs 16 17 18 19) *0, disabled.
[    0.290165] ACPI: PCI Interrupt Link [LNEB] (IRQs 16 17 18 19) *0, disabled.
[    0.290354] ACPI: PCI Interrupt Link [LNEC] (IRQs 16 17 18 19) *0, disabled.
[    0.290545] ACPI: PCI Interrupt Link [LNED] (IRQs 16 17 18 19) *0, disabled.
[    0.290738] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *5
[    0.290929] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *10
[    0.291121] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *5
[    0.291319] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *11
[    0.291510] ACPI: PCI Interrupt Link [LACI] (IRQs 20 21 22 23) *0, disabled.
[    0.291704] ACPI: PCI Interrupt Link [LMC9] (IRQs 20 21 22 23) *10
[    0.291895] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *11
[    0.292100] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *0, disabled.
[    0.292295] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *10
[    0.292486] ACPI: PCI Interrupt Link [LSA1] (IRQs 20 21 22 23) *10
[    0.292716] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[    0.292827] vgaarb: device added: PCI:0000:00:0d.0,decodes=io+mem,owns=io+mem,locks=none
[    0.292832] vgaarb: loaded
[    0.292937] SCSI subsystem initialized
[    0.292959] libata version 3.00 loaded.
[    0.292959] usbcore: registered new interface driver usbfs
[    0.292959] usbcore: registered new interface driver hub
[    0.292959] usbcore: registered new device driver usb
[    0.292959] ACPI: WMI: Mapper loaded
[    0.292959] PCI: Using ACPI for IRQ routing
[    0.292959] NetLabel: Initializing
[    0.292959] NetLabel:  domain hash size = 128
[    0.292959] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.292959] NetLabel:  unlabeled traffic allowed by default
[    0.292959] Switching to clocksource tsc
[    0.293820] AppArmor: AppArmor Filesystem Enabled
[    0.293820] pnp: PnP ACPI init
[    0.293820] ACPI: bus type pnp registered
[    0.298008] pnp: PnP ACPI: found 14 devices
[    0.298010] ACPI: ACPI bus type pnp unregistered
[    0.298013] PnPBIOS: Disabled by ACPI PNP
[    0.298027] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[    0.298030] system 00:06: ioport range 0x800-0x80f has been reserved
[    0.298033] system 00:06: ioport range 0x4000-0x407f has been reserved
[    0.298036] system 00:06: ioport range 0x4080-0x40ff has been reserved
[    0.298039] system 00:06: ioport range 0x4400-0x447f has been reserved
[    0.298042] system 00:06: ioport range 0x4480-0x44ff has been reserved
[    0.298045] system 00:06: ioport range 0x4800-0x487f has been reserved
[    0.298047] system 00:06: ioport range 0x4880-0x48ff has been reserved
[    0.298050] system 00:06: ioport range 0x2000-0x207f has been reserved
[    0.298053] system 00:06: ioport range 0x2080-0x20ff has been reserved
[    0.298057] system 00:06: iomem range 0xfec80000-0x1fd93ffff could not be reserved
[    0.298060] system 00:06: iomem range 0xfefe0000-0xfefe01ff has been reserved
[    0.298064] system 00:06: iomem range 0xfefe1000-0xfefe1fff has been reserved
[    0.298067] system 00:06: iomem range 0xfee01000-0xfeefffff has been reserved
[    0.298072] system 00:07: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.298075] system 00:07: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.298082] system 00:0b: ioport range 0x290-0x29f has been reserved
[    0.298087] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
[    0.298092] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[    0.298095] system 00:0d: iomem range 0xc0000-0xcffff could not be reserved
[    0.298098] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[    0.298101] system 00:0d: iomem range 0x100000-0xbfffffff could not be reserved
[    0.298104] system 00:0d: iomem range 0xff380000-0xffffffff could not be reserved
[    0.332785] pci 0000:00:04.0: PCI bridge, secondary bus 0000:01
[    0.332787] pci 0000:00:04.0:   IO window: disabled
[    0.332790] pci 0000:00:04.0:   MEM window: disabled
[    0.332794] pci 0000:00:04.0:   PREFETCH window: disabled
[    0.332798] pci 0000:00:09.0: PCI bridge, secondary bus 0000:02
[    0.332800] pci 0000:00:09.0:   IO window: disabled
[    0.332803] pci 0000:00:09.0:   MEM window: disabled
[    0.332805] pci 0000:00:09.0:   PREFETCH window: disabled
[    0.332809] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:03
[    0.332811] pci 0000:00:0b.0:   IO window: disabled
[    0.332813] pci 0000:00:0b.0:   MEM window: disabled
[    0.332816] pci 0000:00:0b.0:   PREFETCH window: disabled
[    0.332819] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:04
[    0.332821] pci 0000:00:0c.0:   IO window: disabled
[    0.332824] pci 0000:00:0c.0:   MEM window: disabled
[    0.332826] pci 0000:00:0c.0:   PREFETCH window: disabled
[    0.332835] pci 0000:00:04.0: setting latency timer to 64
[    0.332841] pci 0000:00:09.0: setting latency timer to 64
[    0.332846] pci 0000:00:0b.0: setting latency timer to 64
[    0.332851] pci 0000:00:0c.0: setting latency timer to 64
[    0.332855] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.332858] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.332861] pci_bus 0000:01: resource 3 io:  [0x00-0xffff]
[    0.332863] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.332901] NET: Registered protocol family 2
[    0.332994] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.333300] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.333866] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.334171] TCP: Hash tables configured (established 131072 bind 65536)
[    0.334174] TCP reno registered
[    0.334260] NET: Registered protocol family 1
[    0.390381] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.390430] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.390489] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.390546] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.390604] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.390666] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.390733] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.390804] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.390810] pci 0000:00:0d.0: Boot video device
[    0.391094] cpufreq-nforce2: No nForce2 chipset.
[    0.391118] Scanning for low memory corruption every 60 seconds
[    0.391214] audit: initializing netlink socket (disabled)
[    0.391223] type=2000 audit(1320001845.390:1): initialized
[    0.400276] highmem bounce pool size: 64 pages
[    0.400281] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.401550] VFS: Disk quotas dquot_6.5.2
[    0.401605] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.402121] fuse init (API version 7.13)
[    0.402212] msgmni has been set to 1615
[    0.402483] alg: No test for stdrng (krng)
[    0.402536] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.402539] io scheduler noop registered
[    0.402541] io scheduler anticipatory registered
[    0.402543] io scheduler deadline registered
[    0.402579] io scheduler cfq registered (default)
[    0.402696]   alloc irq_desc for 24 on node -1
[    0.402698]   alloc kstat_irqs on node -1
[    0.402707] pcieport 0000:00:09.0: irq 24 for MSI/MSI-X
[    0.402712] pcieport 0000:00:09.0: setting latency timer to 64
[    0.402779]   alloc irq_desc for 25 on node -1
[    0.402781]   alloc kstat_irqs on node -1
[    0.402786] pcieport 0000:00:0b.0: irq 25 for MSI/MSI-X
[    0.402790] pcieport 0000:00:0b.0: setting latency timer to 64
[    0.402851]   alloc irq_desc for 26 on node -1
[    0.402853]   alloc kstat_irqs on node -1
[    0.402857] pcieport 0000:00:0c.0: irq 26 for MSI/MSI-X
[    0.402861] pcieport 0000:00:0c.0: setting latency timer to 64
[    0.402908] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.402930] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.403026] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.403030] ACPI: Power Button [PWRB]
[    0.403074] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.403077] ACPI: Power Button [PWRF]
[    0.403338] processor LNXCPU:00: registered as cooling_device0
[    0.403369] processor LNXCPU:01: registered as cooling_device1
[    0.403397] processor LNXCPU:02: registered as cooling_device2
[    0.406184] isapnp: Scanning for PnP cards...
[    0.407304] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.407399] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.407701] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.408561] brd: module loaded
[    0.408954] loop: module loaded
[    0.409033] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.409206] pata_acpi 0000:00:06.0: setting latency timer to 64
[    0.409527] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 23
[    0.409532]   alloc irq_desc for 23 on node -1
[    0.409534]   alloc kstat_irqs on node -1
[    0.409544] pata_acpi 0000:00:08.0: PCI INT A -> Link[LSA0] -> GSI 23 (level, low) -> IRQ 23
[    0.409558] pata_acpi 0000:00:08.0: setting latency timer to 64
[    0.409566] pata_acpi 0000:00:08.0: PCI INT A disabled
[    0.409813] ACPI: PCI Interrupt Link [LSA1] enabled at IRQ 22
[    0.409818]   alloc irq_desc for 22 on node -1
[    0.409820]   alloc kstat_irqs on node -1
[    0.409827] pata_acpi 0000:00:08.1: PCI INT B -> Link[LSA1] -> GSI 22 (level, low) -> IRQ 22
[    0.409840] pata_acpi 0000:00:08.1: setting latency timer to 64
[    0.409847] pata_acpi 0000:00:08.1: PCI INT B disabled
[    0.410107] Fixed MDIO Bus: probed
[    0.410136] PPP generic driver version 2.4.2
[    0.410165] tun: Universal TUN/TAP device driver, 1.6
[    0.410166] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.410254] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.410520] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 21
[    0.410523]   alloc irq_desc for 21 on node -1
[    0.410525]   alloc kstat_irqs on node -1
[    0.410532] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUB2] -> GSI 21 (level, low) -> IRQ 21
[    0.410548] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    0.410551] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    0.410584] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    0.410607] ehci_hcd 0000:00:02.1: debug port 1
[    0.410614] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    0.410635] ehci_hcd 0000:00:02.1: irq 21, io mem 0xdfffec00
[    0.422324] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    0.422406] usb usb1: configuration #1 chosen from 1 choice
[    0.422434] hub 1-0:1.0: USB hub found
[    0.422440] hub 1-0:1.0: 9 ports detected
[    0.422498] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.422748] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 20
[    0.422751]   alloc irq_desc for 20 on node -1
[    0.422753]   alloc kstat_irqs on node -1
[    0.422759] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUB0] -> GSI 20 (level, low) -> IRQ 20
[    0.422768] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    0.422770] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    0.422796] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    0.422816] ohci_hcd 0000:00:02.0: irq 20, io mem 0xdffff000
[    0.455716] Freeing initrd memory: 7766k freed
[    0.480374] usb usb2: configuration #1 chosen from 1 choice
[    0.480395] hub 2-0:1.0: USB hub found
[    0.480402] hub 2-0:1.0: 9 ports detected
[    0.480449] uhci_hcd: USB Universal Host Controller Interface driver
[    0.480520] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.483615] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.483624] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.483700] mice: PS/2 mouse device common for all mice
[    0.483799] rtc_cmos 00:02: RTC can wake from S4
[    0.483831] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.483865] rtc0: alarms up to one year, y3k, 114 bytes nvram
[    0.483957] device-mapper: uevent: version 1.0.3
[    0.484135] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.484283] device-mapper: multipath: version 1.1.0 loaded
[    0.484289] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.484425] EISA: Probing bus 0 at eisa.0
[    0.484435] Cannot allocate resource for EISA slot 2
[    0.484439] Cannot allocate resource for EISA slot 4
[    0.484442] Cannot allocate resource for EISA slot 5
[    0.484444] Cannot allocate resource for EISA slot 6
[    0.484451] EISA: Detected 0 cards.
[    0.484605] cpuidle: using governor ladder
[    0.484607] cpuidle: using governor menu
[    0.485008] TCP cubic registered
[    0.485161] NET: Registered protocol family 10
[    0.485901] NET: Registered protocol family 17
[    0.485940] powernow-k8: Found 1 AMD Phenom(tm) 8450 Triple-Core Processor processors (3 cpu cores) (version 2.20.00)
[    0.485979] powernow-k8:    0 : pstate 0 (2100 MHz)
[    0.485981] powernow-k8:    1 : pstate 1 (1050 MHz)
[    0.498594] Using IPI No-Shortcut mode
[    0.498664] PM: Resume from disk failed.
[    0.498676] registered taskstats version 1
[    0.498931]   Magic number: 15:910:193
[    0.499021] rtc_cmos 00:02: setting system clock to 2011-10-30 19:10:46 UTC (1320001846)
[    0.499024] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.499026] EDD information not available.
[    0.503040] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.759079] isapnp: No Plug & Play device found
[    0.759096] Freeing unused kernel memory: 684k freed
[    0.759519] Write protecting the kernel text: 4836k
[    0.759593] Write protecting the kernel read-only data: 1884k
[    0.775118] udev: starting version 151
[    0.801630] sata_nv 0000:00:08.0: version 3.5
[    0.801649] sata_nv 0000:00:08.0: PCI INT A -> Link[LSA0] -> GSI 23 (level, low) -> IRQ 23
[    0.801700] sata_nv 0000:00:08.0: setting latency timer to 64
[    0.821366] scsi0 : sata_nv
[    0.829511] scsi1 : sata_nv
[    0.829941] ata1: SATA max UDMA/133 cmd 0xe400 ctl 0xe080 bmdma 0xd880 irq 23
[    0.829945] ata2: SATA max UDMA/133 cmd 0xe000 ctl 0xdc00 bmdma 0xd888 irq 23
[    0.830009] pata_amd 0000:00:06.0: version 0.4.1
[    0.830058] pata_amd 0000:00:06.0: setting latency timer to 64
[    0.835855] scsi2 : pata_amd
[    0.838973] scsi3 : pata_amd
[    0.839965] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.839969] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.840032] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    0.840351] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 23
[    0.840357] forcedeth 0000:00:07.0: PCI INT A -> Link[LMAC] -> GSI 23 (level, low) -> IRQ 23
[    0.840362] forcedeth 0000:00:07.0: setting latency timer to 64
[    1.098235] usb 2-3: new low speed USB device using ohci_hcd and address 2
[    1.296036] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.305137] ata1.00: ATAPI: HL-DT-STDVD-RAM GH22NS30, 1.01, max UDMA/100
[    1.320161] ata1.00: configured for UDMA/100
[    1.321684] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GH22NS30 1.01 PQ: 0 ANSI: 5
[    1.324382] usb 2-3: configuration #1 chosen from 1 choice
[    1.325154] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.325157] Uniform CD-ROM driver Revision: 3.20
[    1.325263] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.325311] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.365047] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:19:66:a9:d8:2e
[    1.365052] forcedeth 0000:00:07.0: highdma pwrctl mgmt lnktim msi desc-v3
[    1.365087] sata_nv 0000:00:08.1: PCI INT B -> Link[LSA1] -> GSI 22 (level, low) -> IRQ 22
[    1.365134] sata_nv 0000:00:08.1: setting latency timer to 64
[    1.365203] scsi4 : sata_nv
[    1.365293] scsi5 : sata_nv
[    1.365527] ata5: SATA max UDMA/133 cmd 0xd800 ctl 0xd480 bmdma 0xd000 irq 22
[    1.365530] ata6: SATA max UDMA/133 cmd 0xd400 ctl 0xd080 bmdma 0xd008 irq 22
[    1.628019] usb 2-4: new full speed USB device using ohci_hcd and address 3
[    1.686276] ata5: SATA link down (SStatus 0 SControl 300)
[    1.792039] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.800240] ata2.00: ATA-7: SAMSUNG HD322HJ, 1AC01113, max UDMA7
[    1.800243] ata2.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.808254] ata2.00: configured for UDMA/133
[    1.808364] scsi 1:0:0:0: Direct-Access     ATA      SAMSUNG HD322HJ  1AC0 PQ: 0 ANSI: 5
[    1.808500] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    1.808525] sd 1:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.808585] sd 1:0:0:0: [sda] Write Protect is off
[    1.808588] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.808600] ata4: port disabled. ignoring.
[    1.808606] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.808756]  sda: sda1 sda2 sda3
[    1.833225] sd 1:0:0:0: [sda] Attached SCSI disk
[    1.844377] usb 2-4: configuration #1 chosen from 1 choice
[    1.847322] hub 2-4:1.0: USB hub found
[    1.850290] hub 2-4:1.0: 2 ports detected
[    2.087969] kjournald starting.  Commit interval 5 seconds
[    2.087976] EXT3-fs: mounted filesystem with ordered data mode.
[    2.134291] ata6: SATA link down (SStatus 0 SControl 300)
[    2.138394] usbcore: registered new interface driver hiddev
[    2.145281] usb 2-4.1: new full speed USB device using ohci_hcd and address 4
[    2.152452] input: Chicony Chicony wired mouse as /devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.0/input/input4
[    2.152539] generic-usb 0003:04F2:0719.0001: input,hidraw0: USB HID v1.11 Mouse [Chicony Chicony wired mouse] on usb-0000:00:02.0-3/input0
[    2.152560] usbcore: registered new interface driver usbhid
[    2.152563] usbhid: v2.6:USB HID core driver
[    2.256364] usb 2-4.1: configuration #1 chosen from 1 choice
[    2.342277] usb 2-4.2: new full speed USB device using ohci_hcd and address 5
[    2.456359] usb 2-4.2: configuration #1 chosen from 1 choice
[   13.037164] udev: starting version 151
[   13.062786] Adding 9767512k swap on /dev/sda2.  Priority:-1 extents:1 across:9767512k 
[   13.077250] lp: driver loaded but no devices found
[   13.088985] i2c i2c-0: nForce2 SMBus adapter at 0x5000
[   13.089055] i2c i2c-1: nForce2 SMBus adapter at 0x6000
[   13.110500] vga16fb: initializing
[   13.110506] vga16fb: mapped to 0xc00a0000
[   13.110568] fb0: VGA16 VGA frame buffer device
[   13.179181] Linux agpgart interface v0.103
[   13.202199] type=1505 audit(1320001859.201:2):  operation="profile_load" pid=636 name="/sbin/dhclient3"
[   13.202492] type=1505 audit(1320001859.201:3):  operation="profile_load" pid=636 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   13.202660] type=1505 audit(1320001859.201:4):  operation="profile_load" pid=636 name="/usr/lib/connman/scripts/dhclient-script"
[   13.207199] nvidia: module license 'NVIDIA' taints kernel.
[   13.207204] Disabling lock debugging due to kernel taint
[   13.210258] type=1505 audit(1320001859.209:5):  operation="profile_replace" pid=643 name="/sbin/dhclient3"
[   13.210559] type=1505 audit(1320001859.209:6):  operation="profile_replace" pid=643 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   13.210724] type=1505 audit(1320001859.209:7):  operation="profile_replace" pid=643 name="/usr/lib/connman/scripts/dhclient-script"
[   13.331246] EXT3 FS on sda1, internal journal
[   13.675843] kjournald starting.  Commit interval 5 seconds
[   13.676229] EXT3 FS on sda3, internal journal
[   13.676234] EXT3-fs: mounted filesystem with ordered data mode.
[   14.213093] parport_pc 00:05: reported by Plug and Play ACPI
[   14.213146] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   14.225947] usblp0: USB Bidirectional printer dev 5 if 0 alt 0 proto 2 vid 0x043D pid 0x007B
[   14.225965] usbcore: registered new interface driver usblp
[   14.233019] ip_tables: (C) 2000-2006 Netfilter Core Team
[   14.237129] ppdev: user-space parallel port driver
[   14.261318] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   14.262351] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   14.262353] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[   14.262355] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   14.324338] lp0: using parport0 (interrupt-driven).
[   14.363603] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 22
[   14.363610] HDA Intel 0000:00:05.0: PCI INT B -> Link[LAZA] -> GSI 22 (level, low) -> IRQ 22
[   14.363613] hda_intel: Disable MSI for Nvidia chipset
[   14.363641] HDA Intel 0000:00:05.0: setting latency timer to 64
[   14.423060] Console: switching to colour frame buffer device 80x30
[   14.900583] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:05.0/input/input5
[   15.053015] ACPI: PCI Interrupt Link [LMC9] enabled at IRQ 21
[   15.053023] nvidia 0000:00:0d.0: PCI INT A -> Link[LMC9] -> GSI 21 (level, low) -> IRQ 21
[   15.053032] nvidia 0000:00:0d.0: setting latency timer to 64
[   15.053038] vgaarb: device changed decodes: PCI:0000:00:0d.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   15.053293] NVRM: loading NVIDIA UNIX x86 Kernel Module  195.36.24  Thu Apr 22 09:18:20 PDT 2010
[   15.453027] type=1505 audit(1320001861.452:8):  operation="profile_load" pid=884 name="/usr/bin/freshclam"
[   15.454923] type=1505 audit(1320001861.452:9):  operation="profile_load" pid=886 name="/usr/sbin/mysqld-akonadi"
[   15.456294] type=1505 audit(1320001861.456:10):  operation="profile_load" pid=885 name="/usr/lib/cups/backend/cups-pdf"
[   15.456639] type=1505 audit(1320001861.456:11):  operation="profile_load" pid=885 name="/usr/sbin/cupsd"
[   15.463759]   alloc irq_desc for 27 on node -1
[   15.463762]   alloc kstat_irqs on node -1
[   15.463772] forcedeth 0000:00:07.0: irq 27 for MSI/MSI-X
[   15.962156] CPU0 attaching NULL sched-domain.
[   15.962162] CPU1 attaching NULL sched-domain.
[   15.962165] CPU2 attaching NULL sched-domain.
[   16.160595] CPU0 attaching sched-domain:
[   16.160600]  domain 0: span 0-2 level MC
[   16.160603]   groups: 0 1 2
[   16.160609] CPU1 attaching sched-domain:
[   16.160611]  domain 0: span 0-2 level MC
[   16.160613]   groups: 1 2 0
[   16.160616] CPU2 attaching sched-domain:
[   16.160618]  domain 0: span 0-2 level MC
[   16.160619]   groups: 2 0 1
[   16.919095] usb 2-4.2: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[   26.248053] eth0: no IPv6 routers present
[   33.537623] CPUFREQ: Per core ondemand sysfs interface is deprecated - up_threshold
[   33.619433] CPU0 attaching NULL sched-domain.
[   33.619445] CPU1 attaching NULL sched-domain.
[   33.619450] CPU2 attaching NULL sched-domain.
[   33.641131] CPU0 attaching sched-domain:
[   33.641137]  domain 0: span 0-2 level MC
[   33.641143]   groups: 0 1 2
[   33.641154] CPU1 attaching sched-domain:
[   33.641158]  domain 0: span 0-2 level MC
[   33.641162]   groups: 1 2 0
[   33.641174] CPU2 attaching sched-domain:
[   33.641178]  domain 0: span 0-2 level MC
[   33.641185]   groups: 2 0 1
```

---

### Post by mrblue8 on 2011-10-31
I have tried to use the external hdd with Windows and it mounted as read-only. I formatted it (ntfs) and was then able to write on it. I came back to Ubuntu but neither *lsusb* nor *fdisk -l* can recognize it.

New dmesg output (lusb and fdisk -l remain the same as before):

```
administrador@computador:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-34-generic-pae (buildd@vernadsky) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #77-Ubuntu SMP Tue Sep 13 21:16:18 UTC 2011 (Ubuntu 2.6.32-34.77-generic-pae 2.6.32.44+drm33.19)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e7000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000affb0000 (usable)
[    0.000000]  BIOS-e820: 00000000affb0000 - 00000000affc0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000affc0000 - 00000000afff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000afff0000 - 00000000b0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFE0000000 write-back
[    0.000000]   2 base 0000A0000000 mask FFFFF0000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000140000000 aka 5120M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000b0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e7000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000affb0000 (usable)
[    0.000000]  modified: 00000000affb0000 - 00000000affc0000 (ACPI data)
[    0.000000]  modified: 00000000affc0000 - 00000000afff0000 (ACPI NVS)
[    0.000000]  modified: 00000000afff0000 - 00000000b0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] initial memory mapped : 0 - 00e00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000379fe000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037800000 page 2M
[    0.000000]  0037800000 - 00379fe000 page 4k
[    0.000000] kernel direct mapping tables up to 379fe000 @ 10000-16000
[    0.000000] RAMDISK: 3785a000 - 37fef970
[    0.000000] Allocated new RAMDISK: 00941000 - 010d6970
[    0.000000] Move RAMDISK from 000000003785a000 - 0000000037fef96f to 00941000 - 010d696f
[    0.000000] ACPI: RSDP 000fabf0 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT affb0000 0003C (v01 A_M_I  OEMRSDT  01000908 MSFT 00000097)
[    0.000000] ACPI: FACP affb0200 00084 (v02 A M I  OEMFACP  12000601 MSFT 00000097)
[    0.000000] ACPI: DSDT affb0450 04729 (v01  AS164 AS164133 00000133 INTL 20051117)
[    0.000000] ACPI: FACS affc0000 00040
[    0.000000] ACPI: APIC affb0390 00080 (v01 A_M_I  OEMAPIC  01000908 MSFT 00000097)
[    0.000000] ACPI: MCFG affb0410 0003C (v01 A_M_I  OEMMCFG  01000908 MSFT 00000097)
[    0.000000] ACPI: OEMB affc0040 00060 (v01 A_M_I  AMI_OEM  01000908 MSFT 00000097)
[    0.000000] ACPI: AAFT affb4b80 00027 (v01 A_M_I  OEMAAFT  01000908 MSFT 00000097)
[    0.000000] ACPI: SSDT affb4bb0 003FC (v01 A M I  POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 4230MB HIGHMEM available.
[    0.000000] 889MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 379fe000
[    0.000000]   low ram: 0 - 379fe000
[    0.000000]   node 0 low ram: 00000000 - 379fe000
[    0.000000]   node 0 bootmap 00012000 - 00018f40
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00379fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 0000938818]    TEXT DATA BSS ==> [0000100000 - 0000938818]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [0000939000 - 000094012b]              BRK ==> [0000939000 - 000094012b]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [0000941000 - 00010d6970]      NEW RAMDISK ==> [0000941000 - 00010d6970]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000379fe
[    0.000000]   HighMem  0x000379fe -> 0x00140000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000affb0
[    0.000000]     0: 0x00100000 -> 0x00140000
[    0.000000] On node 0 totalpages: 982847
[    0.000000] free_area_init_node: node 0, pgdat c07d8e00, node_mem_map c10d8200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1748 pages used for memmap
[    0.000000]   Normal zone: 221994 pages, LIFO batch:31
[    0.000000]   HighMem zone: 8461 pages used for memmap
[    0.000000]   HighMem zone: 746661 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x03] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 3, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 1 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e7000
[    0.000000] PM: Registered nosave memory: 00000000000e7000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at b0000000 (gap: b0000000:4ec00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 15 pages/cpu @c3a00000 s39736 r0 d21704 u524288
[    0.000000] pcpu-alloc: s39736 r0 d21704 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 972606
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-34-generic-pae root=UUID=92f1548d-0211-4740-a195-2a51ff02f541 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 26214080 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000379fe:00140000)
[    0.000000] Memory: 3846304k/5242880k available (4832k kernel code, 83908k reserved, 2221k data, 684k init, 3020488k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xffa00000 - 0xffc00000   (2048 kB)
[    0.000000]     vmalloc : 0xf81fe000 - 0xff9fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf79fe000   ( 889 MB)
[    0.000000]       .init : 0xc07e4000 - 0xc088f000   ( 684 kB)
[    0.000000]       .data : 0xc05b815f - 0xc07e3788   (2221 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05b815f   (4832 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:440
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2109.662 MHz processor.
[    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 4219.32 BogoMIPS (lpj=8438648)
[    0.004020] Security Framework initialized
[    0.004039] AppArmor: AppArmor initialized
[    0.004046] Mount-cache hash table entries: 512
[    0.004157] Initializing cgroup subsys ns
[    0.004161] Initializing cgroup subsys cpuacct
[    0.004165] Initializing cgroup subsys memory
[    0.004171] Initializing cgroup subsys devices
[    0.004174] Initializing cgroup subsys freezer
[    0.004176] Initializing cgroup subsys net_cls
[    0.004193] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004196] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004199] CPU: Physical Processor ID: 0
[    0.004200] CPU: Processor Core ID: 0
[    0.004204] mce: CPU supports 6 MCE banks
[    0.004215] using C1E aware idle routine
[    0.004221] Performance Events: AMD PMU driver.
[    0.004225] ... version:                0
[    0.004227] ... bit width:              48
[    0.004229] ... generic registers:      4
[    0.004231] ... value mask:             0000ffffffffffff
[    0.004233] ... max period:             00007fffffffffff
[    0.004235] ... fixed-purpose events:   0
[    0.004237] ... event mask:             000000000000000f
[    0.004241] Checking 'hlt' instruction... OK.
[    0.022262] ACPI: Core revision 20090903
[    0.030008] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.030013] ftrace: allocating 22362 entries in 44 pages
[    0.032076] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.032541] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.073077] CPU0: AMD Phenom(tm) 8450 Triple-Core Processor stepping 03
[    0.076001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.008000] Initializing CPU#1
[    0.008000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.008000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 1
[    0.160037] CPU1: AMD Phenom(tm) 8450 Triple-Core Processor stepping 03
[    0.160045] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.164071] Booting processor 2 APIC 0x2 ip 0x6000
[    0.008000] Initializing CPU#2
[    0.008000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.008000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 2
[    0.252090] CPU2: AMD Phenom(tm) 8450 Triple-Core Processor stepping 03
[    0.252098] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.256012] Brought up 3 CPUs
[    0.256015] Total of 3 processors activated (12658.49 BogoMIPS).
[    0.257155] CPU0 attaching sched-domain:
[    0.257161]  domain 0: span 0-2 level MC
[    0.257163]   groups: 0 1 2
[    0.257171] CPU1 attaching sched-domain:
[    0.257173]  domain 0: span 0-2 level MC
[    0.257175]   groups: 1 2 0
[    0.257182] CPU2 attaching sched-domain:
[    0.257183]  domain 0: span 0-2 level MC
[    0.257185]   groups: 2 0 1
[    0.257279] devtmpfs: initialized
[    0.257279] regulator: core version 0.5
[    0.257279] Time: 14:30:10  Date: 10/31/11
[    0.257279] NET: Registered protocol family 16
[    0.257279] Trying to unpack rootfs image as initramfs...
[    0.257279] EISA bus registered
[    0.257279] ACPI: bus type pci registered
[    0.257279] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.257279] PCI: Not using MMCONFIG.
[    0.257279] PCI: Using configuration type 1 for base access
[    0.257279] PCI: Using configuration type 1 for extended access
[    0.257840] bio: create slab <bio-0> at 0
[    0.260662] ACPI: EC: Look up EC in DSDT
[    0.263548] ACPI: Executed 1 blocks of module-level executable AML code
[    0.268276] ACPI: Interpreter enabled
[    0.268279] ACPI: (supports S0 S1 S4 S5)
[    0.268297] ACPI: Using IOAPIC for interrupt routing
[    0.268344] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.272333] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.272336] PCI: Using MMCONFIG for extended config space
[    0.279549] ACPI Warning: Incorrect checksum in table [OEMB] - 8E, should be 89 (20090903/tbutils-314)
[    0.279657] ACPI: No dock devices found.
[    0.279773] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.279983] pci 0000:00:01.1: reg 10 io port: [0xec00-0xec3f]
[    0.279994] pci 0000:00:01.1: reg 20 io port: [0x5000-0x503f]
[    0.280004] pci 0000:00:01.1: reg 24 io port: [0x6000-0x603f]
[    0.280024] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.280030] pci 0000:00:01.1: PME# disabled
[    0.280079] pci 0000:00:02.0: reg 10 32bit mmio: [0xdffff000-0xdfffffff]
[    0.280101] pci 0000:00:02.0: supports D1 D2
[    0.280103] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.280107] pci 0000:00:02.0: PME# disabled
[    0.280129] pci 0000:00:02.1: reg 10 32bit mmio: [0xdfffec00-0xdfffecff]
[    0.280155] pci 0000:00:02.1: supports D1 D2
[    0.280158] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.280161] pci 0000:00:02.1: PME# disabled
[    0.280224] pci 0000:00:05.0: reg 10 32bit mmio: [0xdfff8000-0xdfffbfff]
[    0.280251] pci 0000:00:05.0: PME# supported from D3hot D3cold
[    0.280254] pci 0000:00:05.0: PME# disabled
[    0.280287] pci 0000:00:06.0: reg 20 io port: [0xffa0-0xffaf]
[    0.280323] pci 0000:00:07.0: reg 10 32bit mmio: [0xdfffd000-0xdfffdfff]
[    0.280327] pci 0000:00:07.0: reg 14 io port: [0xe480-0xe487]
[    0.280349] pci 0000:00:07.0: supports D1 D2
[    0.280351] pci 0000:00:07.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.280355] pci 0000:00:07.0: PME# disabled
[    0.280377] pci 0000:00:08.0: reg 10 io port: [0xe400-0xe407]
[    0.280381] pci 0000:00:08.0: reg 14 io port: [0xe080-0xe083]
[    0.280384] pci 0000:00:08.0: reg 18 io port: [0xe000-0xe007]
[    0.280388] pci 0000:00:08.0: reg 1c io port: [0xdc00-0xdc03]
[    0.280392] pci 0000:00:08.0: reg 20 io port: [0xd880-0xd88f]
[    0.280396] pci 0000:00:08.0: reg 24 32bit mmio: [0xdfffc000-0xdfffcfff]
[    0.280427] pci 0000:00:08.1: reg 10 io port: [0xd800-0xd807]
[    0.280431] pci 0000:00:08.1: reg 14 io port: [0xd480-0xd483]
[    0.280435] pci 0000:00:08.1: reg 18 io port: [0xd400-0xd407]
[    0.280439] pci 0000:00:08.1: reg 1c io port: [0xd080-0xd083]
[    0.280443] pci 0000:00:08.1: reg 20 io port: [0xd000-0xd00f]
[    0.280447] pci 0000:00:08.1: reg 24 32bit mmio: [0xdfff7000-0xdfff7fff]
[    0.280500] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.280503] pci 0000:00:09.0: PME# disabled
[    0.280540] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.280543] pci 0000:00:0b.0: PME# disabled
[    0.280578] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.280581] pci 0000:00:0c.0: PME# disabled
[    0.280598] pci 0000:00:0d.0: reg 10 32bit mmio: [0xde000000-0xdeffffff]
[    0.280604] pci 0000:00:0d.0: reg 14 64bit mmio pref: [0xc0000000-0xcfffffff]
[    0.280610] pci 0000:00:0d.0: reg 1c 64bit mmio: [0xdd000000-0xddffffff]
[    0.280615] pci 0000:00:0d.0: reg 30 32bit mmio pref: [0xdffc0000-0xdffdffff]
[    0.280743] pci 0000:00:04.0: transparent bridge
[    0.280857] pci_bus 0000:00: on NUMA node 0
[    0.280861] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.281033] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.281116] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR10._PRT]
[    0.281177] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR11._PRT]
[    0.281237] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR12._PRT]
[    0.289142] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
[    0.289336] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.
[    0.289529] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[    0.289719] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
[    0.289910] ACPI: PCI Interrupt Link [LNEA] (IRQs 16 17 18 19) *0, disabled.
[    0.290099] ACPI: PCI Interrupt Link [LNEB] (IRQs 16 17 18 19) *0, disabled.
[    0.290290] ACPI: PCI Interrupt Link [LNEC] (IRQs 16 17 18 19) *0, disabled.
[    0.290480] ACPI: PCI Interrupt Link [LNED] (IRQs 16 17 18 19) *0, disabled.
[    0.290671] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *5
[    0.290862] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *10
[    0.291053] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *5
[    0.291250] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *11
[    0.291441] ACPI: PCI Interrupt Link [LACI] (IRQs 20 21 22 23) *0, disabled.
[    0.291633] ACPI: PCI Interrupt Link [LMC9] (IRQs 20 21 22 23) *10
[    0.291823] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *11
[    0.292024] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *0, disabled.
[    0.292205] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *10
[    0.292390] ACPI: PCI Interrupt Link [LSA1] (IRQs 20 21 22 23) *10
[    0.292613] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[    0.292723] vgaarb: device added: PCI:0000:00:0d.0,decodes=io+mem,owns=io+mem,locks=none
[    0.292728] vgaarb: loaded
[    0.292832] SCSI subsystem initialized
[    0.292852] libata version 3.00 loaded.
[    0.292852] usbcore: registered new interface driver usbfs
[    0.292852] usbcore: registered new interface driver hub
[    0.292852] usbcore: registered new device driver usb
[    0.292852] ACPI: WMI: Mapper loaded
[    0.292852] PCI: Using ACPI for IRQ routing
[    0.292852] NetLabel: Initializing
[    0.292852] NetLabel:  domain hash size = 128
[    0.292852] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.292852] NetLabel:  unlabeled traffic allowed by default
[    0.292852] Switching to clocksource tsc
[    0.293781] AppArmor: AppArmor Filesystem Enabled
[    0.293781] pnp: PnP ACPI init
[    0.293781] ACPI: bus type pnp registered
[    0.297977] pnp: PnP ACPI: found 14 devices
[    0.297979] ACPI: ACPI bus type pnp unregistered
[    0.297983] PnPBIOS: Disabled by ACPI PNP
[    0.297997] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[    0.298000] system 00:06: ioport range 0x800-0x80f has been reserved
[    0.298004] system 00:06: ioport range 0x4000-0x407f has been reserved
[    0.298006] system 00:06: ioport range 0x4080-0x40ff has been reserved
[    0.298009] system 00:06: ioport range 0x4400-0x447f has been reserved
[    0.298012] system 00:06: ioport range 0x4480-0x44ff has been reserved
[    0.298015] system 00:06: ioport range 0x4800-0x487f has been reserved
[    0.298018] system 00:06: ioport range 0x4880-0x48ff has been reserved
[    0.298021] system 00:06: ioport range 0x2000-0x207f has been reserved
[    0.298023] system 00:06: ioport range 0x2080-0x20ff has been reserved
[    0.298027] system 00:06: iomem range 0xfec80000-0x1fd93ffff could not be reserved
[    0.298031] system 00:06: iomem range 0xfefe0000-0xfefe01ff has been reserved
[    0.298034] system 00:06: iomem range 0xfefe1000-0xfefe1fff has been reserved
[    0.298037] system 00:06: iomem range 0xfee01000-0xfeefffff has been reserved
[    0.298043] system 00:07: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.298046] system 00:07: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.298052] system 00:0b: ioport range 0x290-0x29f has been reserved
[    0.298057] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
[    0.298062] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[    0.298066] system 00:0d: iomem range 0xc0000-0xcffff could not be reserved
[    0.298069] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[    0.298072] system 00:0d: iomem range 0x100000-0xbfffffff could not be reserved
[    0.298075] system 00:0d: iomem range 0xff380000-0xffffffff could not be reserved
[    0.332755] pci 0000:00:04.0: PCI bridge, secondary bus 0000:01
[    0.332757] pci 0000:00:04.0:   IO window: disabled
[    0.332760] pci 0000:00:04.0:   MEM window: disabled
[    0.332763] pci 0000:00:04.0:   PREFETCH window: disabled
[    0.332768] pci 0000:00:09.0: PCI bridge, secondary bus 0000:02
[    0.332770] pci 0000:00:09.0:   IO window: disabled
[    0.332773] pci 0000:00:09.0:   MEM window: disabled
[    0.332775] pci 0000:00:09.0:   PREFETCH window: disabled
[    0.332779] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:03
[    0.332780] pci 0000:00:0b.0:   IO window: disabled
[    0.332783] pci 0000:00:0b.0:   MEM window: disabled
[    0.332786] pci 0000:00:0b.0:   PREFETCH window: disabled
[    0.332789] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:04
[    0.332791] pci 0000:00:0c.0:   IO window: disabled
[    0.332794] pci 0000:00:0c.0:   MEM window: disabled
[    0.332796] pci 0000:00:0c.0:   PREFETCH window: disabled
[    0.332805] pci 0000:00:04.0: setting latency timer to 64
[    0.332811] pci 0000:00:09.0: setting latency timer to 64
[    0.332815] pci 0000:00:0b.0: setting latency timer to 64
[    0.332820] pci 0000:00:0c.0: setting latency timer to 64
[    0.332824] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.332827] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.332831] pci_bus 0000:01: resource 3 io:  [0x00-0xffff]
[    0.332833] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.332871] NET: Registered protocol family 2
[    0.332964] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.333270] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.333837] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.334139] TCP: Hash tables configured (established 131072 bind 65536)
[    0.334141] TCP reno registered
[    0.334228] NET: Registered protocol family 1
[    0.390422] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.390471] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.390530] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.390587] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.390644] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.390707] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.390773] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.390844] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.390850] pci 0000:00:0d.0: Boot video device
[    0.391135] cpufreq-nforce2: No nForce2 chipset.
[    0.391159] Scanning for low memory corruption every 60 seconds
[    0.391250] audit: initializing netlink socket (disabled)
[    0.391259] type=2000 audit(1320071409.390:1): initialized
[    0.400298] highmem bounce pool size: 64 pages
[    0.400303] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.401562] VFS: Disk quotas dquot_6.5.2
[    0.401636] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.402158] fuse init (API version 7.13)
[    0.402240] msgmni has been set to 1615
[    0.402515] alg: No test for stdrng (krng)
[    0.402574] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.402577] io scheduler noop registered
[    0.402579] io scheduler anticipatory registered
[    0.402581] io scheduler deadline registered
[    0.402616] io scheduler cfq registered (default)
[    0.402732]   alloc irq_desc for 24 on node -1
[    0.402735]   alloc kstat_irqs on node -1
[    0.402743] pcieport 0000:00:09.0: irq 24 for MSI/MSI-X
[    0.402748] pcieport 0000:00:09.0: setting latency timer to 64
[    0.402816]   alloc irq_desc for 25 on node -1
[    0.402818]   alloc kstat_irqs on node -1
[    0.402823] pcieport 0000:00:0b.0: irq 25 for MSI/MSI-X
[    0.402827] pcieport 0000:00:0b.0: setting latency timer to 64
[    0.402890]   alloc irq_desc for 26 on node -1
[    0.402891]   alloc kstat_irqs on node -1
[    0.402896] pcieport 0000:00:0c.0: irq 26 for MSI/MSI-X
[    0.402899] pcieport 0000:00:0c.0: setting latency timer to 64
[    0.402950] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.402972] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.403067] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.403071] ACPI: Power Button [PWRB]
[    0.403115] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.403117] ACPI: Power Button [PWRF]
[    0.403377] processor LNXCPU:00: registered as cooling_device0
[    0.403405] processor LNXCPU:01: registered as cooling_device1
[    0.403433] processor LNXCPU:02: registered as cooling_device2
[    0.406215] isapnp: Scanning for PnP cards...
[    0.407328] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.407423] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.407724] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.408594] brd: module loaded
[    0.408980] loop: module loaded
[    0.409062] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.409231] pata_acpi 0000:00:06.0: setting latency timer to 64
[    0.409544] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 23
[    0.409548]   alloc irq_desc for 23 on node -1
[    0.409550]   alloc kstat_irqs on node -1
[    0.409560] pata_acpi 0000:00:08.0: PCI INT A -> Link[LSA0] -> GSI 23 (level, low) -> IRQ 23
[    0.409575] pata_acpi 0000:00:08.0: setting latency timer to 64
[    0.409583] pata_acpi 0000:00:08.0: PCI INT A disabled
[    0.409831] ACPI: PCI Interrupt Link [LSA1] enabled at IRQ 22
[    0.409834]   alloc irq_desc for 22 on node -1
[    0.409835]   alloc kstat_irqs on node -1
[    0.409842] pata_acpi 0000:00:08.1: PCI INT B -> Link[LSA1] -> GSI 22 (level, low) -> IRQ 22
[    0.409855] pata_acpi 0000:00:08.1: setting latency timer to 64
[    0.409862] pata_acpi 0000:00:08.1: PCI INT B disabled
[    0.410128] Fixed MDIO Bus: probed
[    0.410159] PPP generic driver version 2.4.2
[    0.410189] tun: Universal TUN/TAP device driver, 1.6
[    0.410191] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.410271] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.410533] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 21
[    0.410536]   alloc irq_desc for 21 on node -1
[    0.410538]   alloc kstat_irqs on node -1
[    0.410545] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUB2] -> GSI 21 (level, low) -> IRQ 21
[    0.410561] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    0.410564] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    0.410592] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    0.410618] ehci_hcd 0000:00:02.1: debug port 1
[    0.410625] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    0.410645] ehci_hcd 0000:00:02.1: irq 21, io mem 0xdfffec00
[    0.422365] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    0.422452] usb usb1: configuration #1 chosen from 1 choice
[    0.422479] hub 1-0:1.0: USB hub found
[    0.422487] hub 1-0:1.0: 9 ports detected
[    0.422549] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.422794] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 20
[    0.422797]   alloc irq_desc for 20 on node -1
[    0.422798]   alloc kstat_irqs on node -1
[    0.422805] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUB0] -> GSI 20 (level, low) -> IRQ 20
[    0.422814] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    0.422816] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    0.422842] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    0.422865] ohci_hcd 0000:00:02.0: irq 20, io mem 0xdffff000
[    0.455607] Freeing initrd memory: 7766k freed
[    0.480415] usb usb2: configuration #1 chosen from 1 choice
[    0.480441] hub 2-0:1.0: USB hub found
[    0.480448] hub 2-0:1.0: 9 ports detected
[    0.480495] uhci_hcd: USB Universal Host Controller Interface driver
[    0.480565] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.483656] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.483665] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.483738] mice: PS/2 mouse device common for all mice
[    0.483840] rtc_cmos 00:02: RTC can wake from S4
[    0.483874] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.483908] rtc0: alarms up to one year, y3k, 114 bytes nvram
[    0.483998] device-mapper: uevent: version 1.0.3
[    0.484175] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.484320] device-mapper: multipath: version 1.1.0 loaded
[    0.484323] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.484445] EISA: Probing bus 0 at eisa.0
[    0.484454] Cannot allocate resource for EISA slot 2
[    0.484459] Cannot allocate resource for EISA slot 4
[    0.484461] Cannot allocate resource for EISA slot 5
[    0.484463] Cannot allocate resource for EISA slot 6
[    0.484470] EISA: Detected 0 cards.
[    0.484626] cpuidle: using governor ladder
[    0.484628] cpuidle: using governor menu
[    0.485027] TCP cubic registered
[    0.485169] NET: Registered protocol family 10
[    0.485910] NET: Registered protocol family 17
[    0.485949] powernow-k8: Found 1 AMD Phenom(tm) 8450 Triple-Core Processor processors (3 cpu cores) (version 2.20.00)
[    0.485989] powernow-k8:    0 : pstate 0 (2100 MHz)
[    0.485991] powernow-k8:    1 : pstate 1 (1050 MHz)
[    0.498622] Using IPI No-Shortcut mode
[    0.498691] PM: Resume from disk failed.
[    0.498702] registered taskstats version 1
[    0.498955]   Magic number: 15:317:537
[    0.498964] bdi 1:15: hash matches
[    0.499049] rtc_cmos 00:02: setting system clock to 2011-10-31 14:30:10 UTC (1320071410)
[    0.499052] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.499054] EDD information not available.
[    0.502967] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.759110] isapnp: No Plug & Play device found
[    0.759127] Freeing unused kernel memory: 684k freed
[    0.759545] Write protecting the kernel text: 4836k
[    0.759618] Write protecting the kernel read-only data: 1884k
[    0.775099] udev: starting version 151
[    0.805624] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    0.805944] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 23
[    0.805951] forcedeth 0000:00:07.0: PCI INT A -> Link[LMAC] -> GSI 23 (level, low) -> IRQ 23
[    0.805956] forcedeth 0000:00:07.0: setting latency timer to 64
[    1.098279] usb 2-3: new low speed USB device using ohci_hcd and address 2
[    1.324450] usb 2-3: configuration #1 chosen from 1 choice
[    1.329524] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:19:66:a9:d8:2e
[    1.329529] forcedeth 0000:00:07.0: highdma pwrctl mgmt lnktim msi desc-v3
[    1.329550] sata_nv 0000:00:08.0: version 3.5
[    1.329564] sata_nv 0000:00:08.0: PCI INT A -> Link[LSA0] -> GSI 23 (level, low) -> IRQ 23
[    1.329612] sata_nv 0000:00:08.0: setting latency timer to 64
[    1.329673] scsi0 : sata_nv
[    1.329825] scsi1 : sata_nv
[    1.330218] ata1: SATA max UDMA/133 cmd 0xe400 ctl 0xe080 bmdma 0xd880 irq 23
[    1.330221] ata2: SATA max UDMA/133 cmd 0xe000 ctl 0xdc00 bmdma 0xd888 irq 23
[    1.330247] pata_amd 0000:00:06.0: version 0.4.1
[    1.330273] pata_amd 0000:00:06.0: setting latency timer to 64
[    1.330346] scsi2 : pata_amd
[    1.330410] scsi3 : pata_amd
[    1.331392] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    1.331396] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    1.331443] sata_nv 0000:00:08.1: PCI INT B -> Link[LSA1] -> GSI 22 (level, low) -> IRQ 22
[    1.331473] sata_nv 0000:00:08.1: setting latency timer to 64
[    1.331514] scsi4 : sata_nv
[    1.331567] scsi5 : sata_nv
[    1.331766] ata5: SATA max UDMA/133 cmd 0xd800 ctl 0xd480 bmdma 0xd000 irq 22
[    1.331769] ata6: SATA max UDMA/133 cmd 0xd400 ctl 0xd080 bmdma 0xd008 irq 22
[    1.628017] usb 2-4: new full speed USB device using ohci_hcd and address 3
[    1.650293] ata5: SATA link down (SStatus 0 SControl 300)
[    1.804042] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.812140] ata1.00: ATAPI: HL-DT-STDVD-RAM GH22NS30, 1.01, max UDMA/100
[    1.828161] ata1.00: configured for UDMA/100
[    1.828420] usb 2-4: configuration #1 chosen from 1 choice
[    1.829663] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GH22NS30 1.01 PQ: 0 ANSI: 5
[    1.831373] hub 2-4:1.0: USB hub found
[    1.833146] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.833150] Uniform CD-ROM driver Revision: 3.20
[    1.833251] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.833307] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.834342] hub 2-4:1.0: 2 ports detected
[    2.129333] usb 2-4.1: new full speed USB device using ohci_hcd and address 4
[    2.243381] usb 2-4.1: configuration #1 chosen from 1 choice
[    2.300538] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.308240] ata2.00: ATA-7: SAMSUNG HD322HJ, 1AC01113, max UDMA7
[    2.308243] ata2.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.316260] ata2.00: configured for UDMA/133
[    2.316372] scsi 1:0:0:0: Direct-Access     ATA      SAMSUNG HD322HJ  1AC0 PQ: 0 ANSI: 5
[    2.316522] sd 1:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    2.316545] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    2.316575] sd 1:0:0:0: [sda] Write Protect is off
[    2.316578] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.316604] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.316653] ata4: port disabled. ignoring.
[    2.316804]  sda: sda1 sda2 sda3
[    2.329327] usb 2-4.2: new full speed USB device using ohci_hcd and address 5
[    2.339998] sd 1:0:0:0: [sda] Attached SCSI disk
[    2.443384] usb 2-4.2: configuration #1 chosen from 1 choice
[    2.638268] ata6: SATA link down (SStatus 0 SControl 300)
[    2.642223] usbcore: registered new interface driver hiddev
[    2.656514] input: Chicony Chicony wired mouse as /devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.0/input/input4
[    2.656610] generic-usb 0003:04F2:0719.0001: input,hidraw0: USB HID v1.11 Mouse [Chicony Chicony wired mouse] on usb-0000:00:02.0-3/input0
[    2.656636] usbcore: registered new interface driver usbhid
[    2.656639] usbhid: v2.6:USB HID core driver
[    2.868328] kjournald starting.  Commit interval 5 seconds
[    2.868335] EXT3-fs: mounted filesystem with ordered data mode.
[   13.834076] udev: starting version 151
[   13.858449] i2c i2c-0: nForce2 SMBus adapter at 0x5000
[   13.858508] i2c i2c-1: nForce2 SMBus adapter at 0x6000
[   13.859374] lp: driver loaded but no devices found
[   13.878357] vga16fb: initializing
[   13.878362] vga16fb: mapped to 0xc00a0000
[   13.878477] fb0: VGA16 VGA frame buffer device
[   13.888493] Adding 9767512k swap on /dev/sda2.  Priority:-1 extents:1 across:9767512k 
[   13.942642] Linux agpgart interface v0.103
[   13.996612] type=1505 audit(1320071423.993:2):  operation="profile_load" pid=623 name="/sbin/dhclient3"
[   13.996906] type=1505 audit(1320071423.993:3):  operation="profile_load" pid=623 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   13.997069] type=1505 audit(1320071423.997:4):  operation="profile_load" pid=623 name="/usr/lib/connman/scripts/dhclient-script"
[   14.005169] type=1505 audit(1320071424.005:5):  operation="profile_replace" pid=649 name="/sbin/dhclient3"
[   14.005485] type=1505 audit(1320071424.005:6):  operation="profile_replace" pid=649 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   14.005663] type=1505 audit(1320071424.005:7):  operation="profile_replace" pid=649 name="/usr/lib/connman/scripts/dhclient-script"
[   14.007051] nvidia: module license 'NVIDIA' taints kernel.
[   14.007055] Disabling lock debugging due to kernel taint
[   15.019650] parport_pc 00:05: reported by Plug and Play ACPI
[   15.019703] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   15.032866] ppdev: user-space parallel port driver
[   15.041011] usblp0: USB Bidirectional printer dev 5 if 0 alt 0 proto 2 vid 0x043D pid 0x007B
[   15.041030] usbcore: registered new interface driver usblp
[   15.072245] ip_tables: (C) 2000-2006 Netfilter Core Team
[   15.127099] lp0: using parport0 (interrupt-driven).
[   15.135306] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 22
[   15.135312] HDA Intel 0000:00:05.0: PCI INT B -> Link[LAZA] -> GSI 22 (level, low) -> IRQ 22
[   15.135315] hda_intel: Disable MSI for Nvidia chipset
[   15.135340] HDA Intel 0000:00:05.0: setting latency timer to 64
[   15.167851] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   15.168903] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   15.168906] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[   15.168908] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   15.234660] Console: switching to colour frame buffer device 80x30
[   15.684572] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:05.0/input/input5
[   15.836502] ACPI: PCI Interrupt Link [LMC9] enabled at IRQ 21
[   15.836511] nvidia 0000:00:0d.0: PCI INT A -> Link[LMC9] -> GSI 21 (level, low) -> IRQ 21
[   15.836520] nvidia 0000:00:0d.0: setting latency timer to 64
[   15.836526] vgaarb: device changed decodes: PCI:0000:00:0d.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   15.836754] NVRM: loading NVIDIA UNIX x86 Kernel Module  195.36.24  Thu Apr 22 09:18:20 PDT 2010
[  110.313066] EXT3 FS on sda1, internal journal
[  110.413833] kjournald starting.  Commit interval 5 seconds
[  110.414040] EXT3 FS on sda3, internal journal
[  110.414047] EXT3-fs: mounted filesystem with ordered data mode.
[  112.043430] type=1505 audit(1320071522.040:8):  operation="profile_load" pid=896 name="/usr/bin/freshclam"
[  112.045261] type=1505 audit(1320071522.044:9):  operation="profile_replace" pid=894 name="/sbin/dhclient3"
[  112.045545] type=1505 audit(1320071522.044:10):  operation="profile_replace" pid=894 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[  112.045709] type=1505 audit(1320071522.044:11):  operation="profile_replace" pid=894 name="/usr/lib/connman/scripts/dhclient-script"
[  112.048288] type=1505 audit(1320071522.048:12):  operation="profile_load" pid=897 name="/usr/lib/cups/backend/cups-pdf"
[  112.048398] type=1505 audit(1320071522.048:13):  operation="profile_load" pid=898 name="/usr/sbin/mysqld-akonadi"
[  112.050138] type=1505 audit(1320071522.048:14):  operation="profile_load" pid=897 name="/usr/sbin/cupsd"
[  112.051181] type=1505 audit(1320071522.048:15):  operation="profile_load" pid=899 name="/usr/sbin/tcpdump"
[  112.108279]   alloc irq_desc for 27 on node -1
[  112.108283]   alloc kstat_irqs on node -1
[  112.108294] forcedeth 0000:00:07.0: irq 27 for MSI/MSI-X
[  112.728112] CPU0 attaching NULL sched-domain.
[  112.728119] CPU1 attaching NULL sched-domain.
[  112.728122] CPU2 attaching NULL sched-domain.
[  112.896097] CPU0 attaching sched-domain:
[  112.896102]  domain 0: span 0-2 level MC
[  112.896106]   groups: 0 1 2
[  112.896113] CPU1 attaching sched-domain:
[  112.896115]  domain 0: span 0-2 level MC
[  112.896117]   groups: 1 2 0
[  112.896122] CPU2 attaching sched-domain:
[  112.896124]  domain 0: span 0-2 level MC
[  112.896126]   groups: 2 0 1
[  113.459870] usb 2-4.2: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[  122.972087] eth0: no IPv6 routers present
[  217.373740] CPUFREQ: Per core ondemand sysfs interface is deprecated - up_threshold
[  217.454573] CPU0 attaching NULL sched-domain.
[  217.454585] CPU1 attaching NULL sched-domain.
[  217.454591] CPU2 attaching NULL sched-domain.
[  217.480136] CPU0 attaching sched-domain:
[  217.480143]  domain 0: span 0-2 level MC
[  217.480149]   groups: 0 1 2
[  217.480160] CPU1 attaching sched-domain:
[  217.480165]  domain 0: span 0-2 level MC
[  217.480169]   groups: 1 2 0
[  217.480181] CPU2 attaching sched-domain:
[  217.480185]  domain 0: span 0-2 level MC
[  217.480189]   groups: 2 0 1
[  334.995810] CPU0 attaching NULL sched-domain.
[  334.995821] CPU1 attaching NULL sched-domain.
[  334.995827] CPU2 attaching NULL sched-domain.
[  335.021130] CPU0 attaching sched-domain:
[  335.021137]  domain 0: span 0-2 level MC
[  335.021143]   groups: 0 1 2
[  335.021154] CPU1 attaching sched-domain:
[  335.021158]  domain 0: span 0-2 level MC
[  335.021164]   groups: 1 2 0
[  335.021177] CPU2 attaching sched-domain:
[  335.021180]  domain 0: span 0-2 level MC
[  335.021187]   groups: 2 0 1
```

---

