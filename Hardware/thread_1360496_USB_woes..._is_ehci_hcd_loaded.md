---
title: "USB woes... is ehci_hcd loaded?"
date: 2009-12-21
forum: Hardware
---

### Post by josarn on 2009-12-21
It seems I can't plug a usb device without a complete system freeze. In fact I have only tried a pen-drive and a sata-2-usb HDD. I am considering reporting this in Launchpad but I realize I can't describe the issue well enough.

When I check the output of dmesg, I can see the usual references to the ehci_hcd modules and other usb drivers but when I check the output of lsmod the only module usb related  that is loaded is the usbhid driver.

I write this in hope of getting your help to get a clearer picture of what is going on in my system before I report a bug in launchpad...

dmesg output:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-16-generic (buildd@crested) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #53-Ubuntu SMP Tue Dec 8 04:02:15 UTC 2009 (Ubuntu 2.6.31-16.53-generic)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-16-generic root=UUID=830ad851-fb14-4b99-bd80-250dac1218da ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ec00 (usable)
[    0.000000]  BIOS-e820: 000000000009ec00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cff80000 (usable)
[    0.000000]  BIOS-e820: 00000000cff80000 - 00000000cff98000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cff98000 - 00000000cffd0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cffd0000 - 00000000d0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff700000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x130000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 base 0000C0000000 mask FFFFF0000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000130000000 aka 4864M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000d0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xcff80 max_arch_pfn = 0x400000000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009ec00 (usable)
[    0.000000]  modified: 000000000009ec00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000cff80000 (usable)
[    0.000000]  modified: 00000000cff80000 - 00000000cff98000 (ACPI data)
[    0.000000]  modified: 00000000cff98000 - 00000000cffd0000 (ACPI NVS)
[    0.000000]  modified: 00000000cffd0000 - 00000000d0000000 (reserved)
[    0.000000]  modified: 00000000ff700000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: 0000000000000000-00000000cff80000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 00c0000000 page 1G
[    0.000000]  00c0000000 - 00cfe00000 page 2M
[    0.000000]  00cfe00000 - 00cff80000 page 4k
[    0.000000] kernel direct mapping tables up to cff80000 @ 10000-13000
[    0.000000] init_memory_mapping: 0000000100000000-0000000130000000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0100000000 - 0130000000 page 2M
[    0.000000] kernel direct mapping tables up to 130000000 @ 12000-14000
[    0.000000] RAMDISK: 3786f000 - 37fefb05
[    0.000000] ACPI: RSDP 00000000000fb870 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 00000000cff80100 0005C (v01 NEC             20090727 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000cff80290 000F4 (v03 072709 FACP1851 20090727 MSFT 00000097)
[    0.000000] ACPI: DSDT 00000000cff805c0 0CCC2 (v01  A1182 A1182001 00000001 INTL 20060113)
[    0.000000] ACPI: FACS 00000000cff98000 00040
[    0.000000] ACPI: APIC 00000000cff80390 0006C (v01 072709 APIC1851 20090727 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000cff80400 0003C (v01 072709 OEMMCFG  20090727 MSFT 00000097)
[    0.000000] ACPI: SLIC 00000000cff80440 00176 (v01 NEC             20090727 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000cff98040 00072 (v01 072709 OEMB1851 20090727 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000cff8f5c0 00038 (v01 072709 OEMHPET  20090727 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000cff8f600 0088C (v01 A M I  POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000130000000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000130000000
[    0.000000]   NODE_DATA [0000000000013000 - 0000000000017fff]
[    0.000000]   bootmap [0000000000018000 -  000000000003dfff] pages 26
[    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0130000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 00019e4ccc]    TEXT DATA BSS ==> [0001000000 - 00019e4ccc]
[    0.000000]   #3 [003786f000 - 0037fefb05]          RAMDISK ==> [003786f000 - 0037fefb05]
[    0.000000]   #4 [000009ec00 - 0000100000]    BIOS reserved ==> [000009ec00 - 0000100000]
[    0.000000]   #5 [00019e5000 - 00019e5358]              BRK ==> [00019e5000 - 00019e5358]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [0000012000 - 0000013000]          PGTABLE ==> [0000012000 - 0000013000]
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000]  [ffffea0000000000-ffffea00043fffff] PMD -> [ffff880028600000-ffff88002bffffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00130000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000cff80
[    0.000000]     0: 0x00100000 -> 0x00130000
[    0.000000] On node 0 totalpages: 1048334
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 103 pages reserved
[    0.000000]   DMA zone: 3823 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 833464 pages, LIFO batch:31
[    0.000000]   Normal zone: 2688 pages used for memmap
[    0.000000]   Normal zone: 193920 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cff80000 - 00000000cff98000
[    0.000000] PM: Registered nosave memory: 00000000cff98000 - 00000000cffd0000
[    0.000000] PM: Registered nosave memory: 00000000cffd0000 - 00000000d0000000
[    0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000ff700000
[    0.000000] PM: Registered nosave memory: 00000000ff700000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at d0000000 (gap: d0000000:2f700000)
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages at ffff880028022000, static data 90720 bytes
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1031207
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-16-generic root=UUID=830ad851-fb14-4b99-bd80-250dac1218da ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ f25e000000 size 32 MB
[    0.000000] Aperture beyond 4GB. Ignoring.
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ 20000000
[    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000024000000
[    0.000000] Memory: 4049872k/4980736k available (5315k kernel code, 787400k absent, 143464k reserved, 3018k data, 660k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] NR_IRQS:4352 nr_irqs:440
[    0.000000] Extended CMOS year: 2000
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 3208.863 MHz processor.
[    0.000015] spurious 8259A interrupt: IRQ7.
[    0.001757] Console: colour VGA+ 80x25
[    0.001759] console [tty0] enabled
[    0.010000] allocated 41943040 bytes of page_cgroup
[    0.010000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.010000] hpet clockevent registered
[    0.010000]   alloc irq_desc for 24 on node 0
[    0.010000]   alloc kstat_irqs on node 0
[    0.010000] HPET: 4 timers in total, 1 timers will be used for per-cpu timer
[    0.010005] Calibrating delay loop (skipped), value calculated using timer frequency.. 6417.71 BogoMIPS (lpj=32088590)
[    0.010021] Security Framework initialized
[    0.010035] AppArmor: AppArmor initialized
[    0.010237] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.011484] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.012058] Mount-cache hash table entries: 256
[    0.012149] Initializing cgroup subsys ns
[    0.012152] Initializing cgroup subsys cpuacct
[    0.012154] Initializing cgroup subsys memory
[    0.012159] Initializing cgroup subsys freezer
[    0.012160] Initializing cgroup subsys net_cls
[    0.012169] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.012170] CPU: L2 Cache: 512K (64 bytes/line)
[    0.012172] CPU 0/0x0 -> Node 0
[    0.012174] tseg: 0000000000
[    0.012184] CPU: Physical Processor ID: 0
[    0.012185] CPU: Processor Core ID: 0
[    0.012187] mce: CPU supports 6 MCE banks
[    0.012193] using C1E aware idle routine
[    0.012195] Performance Counters: AMD PMU driver.
[    0.012198] ... version:                 0
[    0.012199] ... bit width:               48
[    0.012200] ... generic counters:        4
[    0.012201] ... value mask:              0000ffffffffffff
[    0.012202] ... max period:              00007fffffffffff
[    0.012203] ... fixed-purpose counters:  0
[    0.012204] ... counter mask:            000000000000000f
[    0.013321] ACPI: Core revision 20090521
[    0.030045] Setting APIC routing to flat
[    0.030350] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.132581] CPU0: AMD Phenom(tm) II X4 955 Processor stepping 02
[    0.140000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.010000] Initializing CPU#1
[    0.010000] Calibrating delay using timer specific routine.. 6418.39 BogoMIPS (lpj=32091951)
[    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.010000] CPU 1/0x1 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 1
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.290839] CPU1: AMD Phenom(tm) II X4 955 Processor stepping 02
[    0.290845] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.300044] Booting processor 2 APIC 0x2 ip 0x6000
[    0.010000] Initializing CPU#2
[    0.010000] Calibrating delay using timer specific routine.. 6418.37 BogoMIPS (lpj=32091895)
[    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.010000] CPU 2/0x2 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 2
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] x86 PAT enabled: cpu 2, old 0x7040600070406, new 0x7010600070106
[    0.460903] CPU2: AMD Phenom(tm) II X4 955 Processor stepping 02
[    0.460908] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.470044] Booting processor 3 APIC 0x3 ip 0x6000
[    0.010000] Initializing CPU#3
[    0.010000] Calibrating delay using timer specific routine.. 6418.37 BogoMIPS (lpj=32091857)
[    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.010000] CPU 3/0x3 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 3
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] x86 PAT enabled: cpu 3, old 0x7040600070406, new 0x7010600070106
[    0.630859] CPU3: AMD Phenom(tm) II X4 955 Processor stepping 02
[    0.630868] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[    0.640008] Brought up 4 CPUs
[    0.640010] Total of 4 processors activated (25672.85 BogoMIPS).
[    0.640054] CPU0 attaching sched-domain:
[    0.640057]  domain 0: span 0-3 level MC
[    0.640058]   groups: 0 1 2 3
[    0.640062] CPU1 attaching sched-domain:
[    0.640064]  domain 0: span 0-3 level MC
[    0.640065]   groups: 1 2 3 0
[    0.640068] CPU2 attaching sched-domain:
[    0.640069]  domain 0: span 0-3 level MC
[    0.640070]   groups: 2 3 0 1
[    0.640073] CPU3 attaching sched-domain:
[    0.640074]  domain 0: span 0-3 level MC
[    0.640075]   groups: 3 0 1 2
[    0.640134] Booting paravirtualized kernel on bare hardware
[    0.640134] regulator: core version 0.5
[    0.640134] Time:  4:59:34  Date: 12/21/09
[    0.640134] NET: Registered protocol family 16
[    0.640135] node 0 link 0: io port [1000, ffffff]
[    0.640137] TOM: 00000000d0000000 aka 3328M
[    0.640139] Fam 10h mmconf [e0000000, efffffff]
[    0.640141] node 0 link 0: mmio [a0000, bffff]
[    0.640142] node 0 link 0: mmio [d0000000, dfffffff]
[    0.640144] node 0 link 0: mmio [e0000000, efffffff] ==> none
[    0.640146] node 0 link 0: mmio [f0000000, ffefffff]
[    0.640147] TOM2: 0000000130000000 aka 4864M
[    0.640149] bus: [00,07] on node 0 link 0
[    0.640150] bus: 00 index 0 io port: [0, ffff]
[    0.640152] bus: 00 index 1 mmio: [a0000, bffff]
[    0.640153] bus: 00 index 2 mmio: [d0000000, dfffffff]
[    0.640154] bus: 00 index 3 mmio: [f0000000, ffffffff]
[    0.640155] bus: 00 index 4 mmio: [130000000, fcffffffff]
[    0.640163] ACPI: bus type pci registered
[    0.640210] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.640211] PCI: Not using MMCONFIG.
[    0.640213] PCI: Using configuration type 1 for base access
[    0.640214] PCI: Using configuration type 1 for extended access
[    0.640643] bio: create slab <bio-0> at 0
[    0.640643] ACPI: EC: Look up EC in DSDT
[    0.712640] ACPI: Interpreter enabled
[    0.712643] ACPI: (supports S0 S1 S3 S4 S5)
[    0.712659] ACPI: Using IOAPIC for interrupt routing
[    0.712706] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.715600] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.721083] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.725870] ACPI: No dock devices found.
[    0.725988] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.726063] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.726065] pci 0000:00:02.0: PME# disabled
[    0.726092] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.726094] pci 0000:00:06.0: PME# disabled
[    0.726144] pci 0000:00:11.0: reg 10 io port: [0xc000-0xc007]
[    0.726149] pci 0000:00:11.0: reg 14 io port: [0xb000-0xb003]
[    0.726155] pci 0000:00:11.0: reg 18 io port: [0xa000-0xa007]
[    0.726161] pci 0000:00:11.0: reg 1c io port: [0x9000-0x9003]
[    0.726167] pci 0000:00:11.0: reg 20 io port: [0x8000-0x800f]
[    0.726172] pci 0000:00:11.0: reg 24 32bit mmio: [0xf9fffc00-0xf9ffffff]
[    0.726219] pci 0000:00:12.0: reg 10 32bit mmio: [0xf9ffe000-0xf9ffefff]
[    0.726267] pci 0000:00:12.1: reg 10 32bit mmio: [0xf9ffd000-0xf9ffdfff]
[    0.726332] pci 0000:00:12.2: reg 10 32bit mmio: [0xf9fff800-0xf9fff8ff]
[    0.726378] pci 0000:00:12.2: supports D1 D2
[    0.726379] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.726383] pci 0000:00:12.2: PME# disabled
[    0.726410] pci 0000:00:13.0: reg 10 32bit mmio: [0xf9ffc000-0xf9ffcfff]
[    0.726458] pci 0000:00:13.1: reg 10 32bit mmio: [0xf9ffb000-0xf9ffbfff]
[    0.726522] pci 0000:00:13.2: reg 10 32bit mmio: [0xf9fff400-0xf9fff4ff]
[    0.726569] pci 0000:00:13.2: supports D1 D2
[    0.726570] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.726573] pci 0000:00:13.2: PME# disabled
[    0.726676] pci 0000:00:14.1: reg 10 io port: [0x00-0x07]
[    0.726682] pci 0000:00:14.1: reg 14 io port: [0x00-0x03]
[    0.726687] pci 0000:00:14.1: reg 18 io port: [0x00-0x07]
[    0.726693] pci 0000:00:14.1: reg 1c io port: [0x00-0x03]
[    0.726698] pci 0000:00:14.1: reg 20 io port: [0xff00-0xff0f]
[    0.726757] pci 0000:00:14.2: reg 10 64bit mmio: [0xf9ff4000-0xf9ff7fff]
[    0.726795] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.726798] pci 0000:00:14.2: PME# disabled
[    0.726890] pci 0000:00:14.5: reg 10 32bit mmio: [0xf9ffa000-0xf9ffafff]
[    0.727020] pci 0000:01:00.0: reg 10 32bit mmio: [0xfd000000-0xfdffffff]
[    0.727030] pci 0000:01:00.0: reg 14 64bit mmio: [0xd0000000-0xdfffffff]
[    0.727039] pci 0000:01:00.0: reg 1c 64bit mmio: [0xfa000000-0xfbffffff]
[    0.727045] pci 0000:01:00.0: reg 24 io port: [0xdc00-0xdc7f]
[    0.727050] pci 0000:01:00.0: reg 30 32bit mmio: [0xfeae0000-0xfeafffff]
[    0.727127] pci 0000:00:02.0: bridge io port: [0xd000-0xdfff]
[    0.727129] pci 0000:00:02.0: bridge 32bit mmio: [0xfa000000-0xfeafffff]
[    0.727132] pci 0000:00:02.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.727171] pci 0000:02:00.0: reg 10 io port: [0xe800-0xe8ff]
[    0.727186] pci 0000:02:00.0: reg 18 64bit mmio: [0xfebff000-0xfebfffff]
[    0.727201] pci 0000:02:00.0: reg 30 32bit mmio: [0xfebc0000-0xfebdffff]
[    0.727234] pci 0000:02:00.0: supports D1 D2
[    0.727235] pci 0000:02:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.727239] pci 0000:02:00.0: PME# disabled
[    0.727298] pci 0000:00:06.0: bridge io port: [0xe000-0xefff]
[    0.727300] pci 0000:00:06.0: bridge 32bit mmio: [0xfeb00000-0xfebfffff]
[    0.727354] pci 0000:00:14.4: transparent bridge
[    0.727371] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.727518] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[    0.727564] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE6._PRT]
[    0.727626] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[    0.730843] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 *7 10 11 12 14 15)
[    0.730926] ACPI: PCI Interrupt Link [LNKB] (IRQs *4 7 10 11 12 14 15)
[    0.731013] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 *10 11 12 14 15)
[    0.731100] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 *10 11 12 14 15)
[    0.731186] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.731270] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.731351] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 7 10 *11 12 14 15)
[    0.731438] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.731537] SCSI subsystem initialized
[    0.731559] libata version 3.00 loaded.
[    0.731559] usbcore: registered new interface driver usbfs
[    0.731559] usbcore: registered new interface driver hub
[    0.731559] usbcore: registered new device driver usb
[    0.731559] ACPI: WMI: Mapper loaded
[    0.731559] PCI: Using ACPI for IRQ routing
[    0.770010] Bluetooth: Core ver 2.15
[    0.770032] NET: Registered protocol family 31
[    0.770032] Bluetooth: HCI device and connection manager initialized
[    0.770032] Bluetooth: HCI socket layer initialized
[    0.770032] NetLabel: Initializing
[    0.770032] NetLabel:  domain hash size = 128
[    0.770032] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.770032] NetLabel:  unlabeled traffic allowed by default
[    0.770146] PCI-DMA: Disabling AGP.
[    0.770212] PCI-DMA: aperture base @ 20000000 size 65536 KB
[    0.770213] PCI-DMA: using GART IOMMU.
[    0.770215] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    0.771751] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 24, 0
[    0.771756] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.780030] hpet: hpet2 irq 24 for MSI
[    0.800017] Switched to high resolution mode on CPU 0
[    0.800804] Switched to high resolution mode on CPU 1
[    0.800828] Switched to high resolution mode on CPU 3
[    0.800868] Switched to high resolution mode on CPU 2
[    0.820036] pnp: PnP ACPI init
[    0.820052] ACPI: bus type pnp registered
[    0.822359] pnp: PnP ACPI: found 12 devices
[    0.822361] ACPI: ACPI bus type pnp unregistered
[    0.822370] system 00:07: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.822372] system 00:07: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.822376] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.822378] system 00:08: ioport range 0x40b-0x40b has been reserved
[    0.822379] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
[    0.822381] system 00:08: ioport range 0xc00-0xc01 has been reserved
[    0.822382] system 00:08: ioport range 0xc14-0xc14 has been reserved
[    0.822384] system 00:08: ioport range 0xc50-0xc51 has been reserved
[    0.822386] system 00:08: ioport range 0xc52-0xc52 has been reserved
[    0.822387] system 00:08: ioport range 0xc6c-0xc6c has been reserved
[    0.822389] system 00:08: ioport range 0xc6f-0xc6f has been reserved
[    0.822390] system 00:08: ioport range 0xcd0-0xcd1 has been reserved
[    0.822392] system 00:08: ioport range 0xcd2-0xcd3 has been reserved
[    0.822394] system 00:08: ioport range 0xcd4-0xcd5 has been reserved
[    0.822395] system 00:08: ioport range 0xcd6-0xcd7 has been reserved
[    0.822397] system 00:08: ioport range 0xcd8-0xcdf has been reserved
[    0.822398] system 00:08: ioport range 0xb00-0xb3f has been reserved
[    0.822400] system 00:08: ioport range 0x800-0x89f has been reserved
[    0.822402] system 00:08: ioport range 0xb20-0xb3f has been reserved
[    0.822403] system 00:08: ioport range 0x900-0x90f has been reserved
[    0.822405] system 00:08: ioport range 0x910-0x91f has been reserved
[    0.822407] system 00:08: ioport range 0xfe00-0xfefe has been reserved
[    0.822409] system 00:08: iomem range 0xffb80000-0xffbfffff has been reserved
[    0.822411] system 00:08: iomem range 0xfec10000-0xfec1001f has been reserved
[    0.822412] system 00:08: iomem range 0xfed40000-0xfed44fff has been reserved
[    0.822415] system 00:09: ioport range 0x290-0x297 has been reserved
[    0.822417] system 00:09: ioport range 0x2a0-0x2af has been reserved
[    0.822421] system 00:0a: iomem range 0xe0000000-0xefffffff has been reserved
[    0.822424] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[    0.822425] system 00:0b: iomem range 0xc0000-0xcffff has been reserved
[    0.822427] system 00:0b: iomem range 0xe0000-0xfffff could not be reserved
[    0.822429] system 00:0b: iomem range 0x100000-0xcfffffff could not be reserved
[    0.822430] system 00:0b: iomem range 0xfec00000-0xffffffff could not be reserved
[    0.827083] AppArmor: AppArmor Filesystem Enabled
[    0.827103] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
[    0.827105] pci 0000:00:02.0:   IO window: 0xd000-0xdfff
[    0.827107] pci 0000:00:02.0:   MEM window: 0xfa000000-0xfeafffff
[    0.827109] pci 0000:00:02.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.827113] pci 0000:00:06.0: PCI bridge, secondary bus 0000:02
[    0.827114] pci 0000:00:06.0:   IO window: 0xe000-0xefff
[    0.827117] pci 0000:00:06.0:   MEM window: 0xfeb00000-0xfebfffff
[    0.827118] pci 0000:00:06.0:   PREFETCH window: disabled
[    0.827120] pci 0000:00:14.4: PCI bridge, secondary bus 0000:03
[    0.827122] pci 0000:00:14.4:   IO window: disabled
[    0.827126] pci 0000:00:14.4:   MEM window: disabled
[    0.827129] pci 0000:00:14.4:   PREFETCH window: disabled
[    0.827136]   alloc irq_desc for 18 on node 0
[    0.827138]   alloc kstat_irqs on node 0
[    0.827141] pci 0000:00:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.827144] pci 0000:00:02.0: setting latency timer to 64
[    0.827148] pci 0000:00:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.827150] pci 0000:00:06.0: setting latency timer to 64
[    0.827156] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.827158] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.827160] pci_bus 0000:01: resource 0 io:  [0xd000-0xdfff]
[    0.827161] pci_bus 0000:01: resource 1 mem: [0xfa000000-0xfeafffff]
[    0.827163] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.827165] pci_bus 0000:02: resource 0 io:  [0xe000-0xefff]
[    0.827166] pci_bus 0000:02: resource 1 mem: [0xfeb00000-0xfebfffff]
[    0.827168] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.827170] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.827194] NET: Registered protocol family 2
[    0.827294] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.827970] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.830046] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.830349] TCP: Hash tables configured (established 524288 bind 65536)
[    0.830351] TCP reno registered
[    0.830422] NET: Registered protocol family 1
[    0.830466] Trying to unpack rootfs image as initramfs...
[    0.943242] Freeing initrd memory: 7682k freed
[    0.945565] Scanning for low memory corruption every 60 seconds
[    0.945649] audit: initializing netlink socket (disabled)
[    0.945660] type=2000 audit(1261371573.940:1): initialized
[    0.951368] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.952211] VFS: Disk quotas dquot_6.5.2
[    0.952244] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.952597] fuse init (API version 7.12)
[    0.952642] msgmni has been set to 7924
[    0.952818] alg: No test for stdrng (krng)
[    0.952828] io scheduler noop registered
[    0.952829] io scheduler anticipatory registered
[    0.952830] io scheduler deadline registered
[    0.952854] io scheduler cfq registered (default)
[    1.120050] pci 0000:01:00.0: Boot video device
[    1.120158]   alloc irq_desc for 25 on node 0
[    1.120160]   alloc kstat_irqs on node 0
[    1.120165] pcieport-driver 0000:00:02.0: irq 25 for MSI/MSI-X
[    1.120169] pcieport-driver 0000:00:02.0: setting latency timer to 64
[    1.120244]   alloc irq_desc for 26 on node 0
[    1.120246]   alloc kstat_irqs on node 0
[    1.120249] pcieport-driver 0000:00:06.0: irq 26 for MSI/MSI-X
[    1.120252] pcieport-driver 0000:00:06.0: setting latency timer to 64
[    1.120293] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.120307] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.120376] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.120378] ACPI: Power Button [PWRF]
[    1.120415] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.120417] ACPI: Power Button [PWRB]
[    1.120971] processor LNXCPU:00: registered as cooling_device0
[    1.120972] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.121289] processor LNXCPU:01: registered as cooling_device1
[    1.121604] processor LNXCPU:02: registered as cooling_device2
[    1.121919] processor LNXCPU:03: registered as cooling_device3
[    1.124248] Linux agpgart interface v0.103
[    1.124254] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.124892] brd: module loaded
[    1.125127] loop: module loaded
[    1.125166] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.125251] ahci 0000:00:11.0: version 3.0
[    1.125262]   alloc irq_desc for 22 on node 0
[    1.125263]   alloc kstat_irqs on node 0
[    1.125267] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.125384] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    1.125386] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    1.125751] scsi0 : ahci
[    1.125804] scsi1 : ahci
[    1.125836] scsi2 : ahci
[    1.125870] scsi3 : ahci
[    1.125899] scsi4 : ahci
[    1.125933] scsi5 : ahci
[    1.126009] ata1: SATA max UDMA/133 irq_stat 0x00400000 , PHY RDY changed
[    1.126011] ata2: SATA max UDMA/133 abar m1024@0xf9fffc00 port 0xf9fffd80 irq 22
[    1.126014] ata3: SATA max UDMA/133 abar m1024@0xf9fffc00 port 0xf9fffe00 irq 22
[    1.126016] ata4: SATA max UDMA/133 abar m1024@0xf9fffc00 port 0xf9fffe80 irq 22
[    1.126019] ata5: SATA max UDMA/133 abar m1024@0xf9fffc00 port 0xf9ffff00 irq 22
[    1.126022] ata6: SATA max UDMA/133 abar m1024@0xf9fffc00 port 0xf9ffff80 irq 22
[    1.126207]   alloc irq_desc for 16 on node 0
[    1.126208]   alloc kstat_irqs on node 0
[    1.126211] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.126231] pata_atiixp 0000:00:14.1: setting latency timer to 64
[    1.126292] scsi6 : pata_atiixp
[    1.126329] scsi7 : pata_atiixp
[    1.127270] ata7: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    1.127271] ata8: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    1.127625] Fixed MDIO Bus: probed
[    1.127644] PPP generic driver version 2.4.2
[    1.127693] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.127739]   alloc irq_desc for 17 on node 0
[    1.127740]   alloc kstat_irqs on node 0
[    1.127743] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.127757] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    1.127785] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.127806] ehci_hcd 0000:00:12.2: applying AMD SB600/SB700 USB freeze workaround
[    1.127821] ehci_hcd 0000:00:12.2: debug port 1
[    1.127834] ehci_hcd 0000:00:12.2: irq 17, io mem 0xf9fff800
[    1.140025] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.140079] usb usb1: configuration #1 chosen from 1 choice
[    1.140096] hub 1-0:1.0: USB hub found
[    1.140101] hub 1-0:1.0: 6 ports detected
[    1.140181]   alloc irq_desc for 19 on node 0
[    1.140182]   alloc kstat_irqs on node 0
[    1.140185] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.140195] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.140215] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.140230] ehci_hcd 0000:00:13.2: applying AMD SB600/SB700 USB freeze workaround
[    1.140245] ehci_hcd 0000:00:13.2: debug port 1
[    1.140257] ehci_hcd 0000:00:13.2: irq 19, io mem 0xf9fff400
[    1.160025] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.160067] usb usb2: configuration #1 chosen from 1 choice
[    1.160081] hub 2-0:1.0: USB hub found
[    1.160085] hub 2-0:1.0: 6 ports detected
[    1.160137] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.160173] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.160183] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.160200] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.160219] ohci_hcd 0000:00:12.0: irq 16, io mem 0xf9ffe000
[    1.224078] usb usb3: configuration #1 chosen from 1 choice
[    1.224093] hub 3-0:1.0: USB hub found
[    1.224102] hub 3-0:1.0: 3 ports detected
[    1.224171] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.224181] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    1.224202] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    1.224213] ohci_hcd 0000:00:12.1: irq 16, io mem 0xf9ffd000
[    1.284095] usb usb4: configuration #1 chosen from 1 choice
[    1.284109] hub 4-0:1.0: USB hub found
[    1.284116] hub 4-0:1.0: 3 ports detected
[    1.284185] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.284196] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.284214] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.284231] ohci_hcd 0000:00:13.0: irq 18, io mem 0xf9ffc000
[    1.344085] usb usb5: configuration #1 chosen from 1 choice
[    1.344102] hub 5-0:1.0: USB hub found
[    1.344112] hub 5-0:1.0: 3 ports detected
[    1.344177] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.344187] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    1.344204] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    1.344216] ohci_hcd 0000:00:13.1: irq 18, io mem 0xf9ffb000
[    1.404078] usb usb6: configuration #1 chosen from 1 choice
[    1.404092] hub 6-0:1.0: USB hub found
[    1.404099] hub 6-0:1.0: 3 ports detected
[    1.404167] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.404179] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    1.404196] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    1.404208] ohci_hcd 0000:00:14.5: irq 18, io mem 0xf9ffa000
[    1.464078] usb usb7: configuration #1 chosen from 1 choice
[    1.464092] hub 7-0:1.0: USB hub found
[    1.464098] hub 7-0:1.0: 2 ports detected
[    1.464139] uhci_hcd: USB Universal Host Controller Interface driver
[    1.464195] PNP: No PS/2 controller found. Probing ports directly.
[    1.464493] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.464506] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.464564] mice: PS/2 mouse device common for all mice
[    1.464631] rtc_cmos 00:03: RTC can wake from S4
[    1.464651] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.464672] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.464739] device-mapper: uevent: version 1.0.3
[    1.464789] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.464868] device-mapper: multipath: version 1.1.0 loaded
[    1.464870] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.465026] cpuidle: using governor ladder
[    1.465027] cpuidle: using governor menu
[    1.465263] TCP cubic registered
[    1.465333] NET: Registered protocol family 10
[    1.465595] lo: Disabled Privacy Extensions
[    1.465759] NET: Registered protocol family 17
[    1.465770] Bluetooth: L2CAP ver 2.13
[    1.465771] Bluetooth: L2CAP socket layer initialized
[    1.465773] Bluetooth: SCO (Voice Link) ver 0.6
[    1.465774] Bluetooth: SCO socket layer initialized
[    1.465813] Bluetooth: RFCOMM TTY layer initialized
[    1.465815] Bluetooth: RFCOMM socket layer initialized
[    1.465816] Bluetooth: RFCOMM ver 1.11
[    1.465839] powernow-k8: Found 1 AMD Phenom(tm) II X4 955 Processor processors (4 cpu cores) (version 2.20.00)
[    1.465864] powernow-k8:    0 : pstate 0 (3200 MHz)
[    1.465865] powernow-k8:    1 : pstate 1 (2500 MHz)
[    1.465866] powernow-k8:    2 : pstate 2 (2100 MHz)
[    1.465867] powernow-k8:    3 : pstate 3 (800 MHz)
[    1.466385] PM: Resume from disk failed.
[    1.466391] registered taskstats version 1
[    1.466467]   Magic number: 5:479:970
[    1.466523] rtc_cmos 00:03: setting system clock to 2009-12-21 04:59:34 UTC (1261371574)
[    1.466525] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.466526] EDD information not available.
[    1.471290] ata6: SATA link down (SStatus 0 SControl 300)
[    1.471317] ata4: SATA link down (SStatus 0 SControl 300)
[    1.471340] ata2: SATA link down (SStatus 0 SControl 300)
[    1.471382] ata5: SATA link down (SStatus 0 SControl 300)
[    1.650023] ata3: softreset failed (device not ready)
[    1.650026] ata3: applying SB600 PMP SRST workaround and retrying
[    1.650042] usb 4-2: new low speed USB device using ohci_hcd and address 2
[    1.830035] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.833040] ata3.00: ATAPI: HL-DT-ST DVDRAM GH22NS40, NL01, max UDMA/100
[    1.836877] ata3.00: configured for UDMA/100
[    1.856156] usb 4-2: configuration #1 chosen from 1 choice
[    2.050038] ata1: softreset failed (device not ready)
[    2.050041] ata1: applying SB600 PMP SRST workaround and retrying
[    2.150024] usb 4-3: new low speed USB device using ohci_hcd and address 3
[    2.230042] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.273064] ata1.00: ATA-7: MAXTOR STM3320820AS, 3.AAE, max UDMA/133
[    2.273067] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.331376] ata1.00: configured for UDMA/133
[    2.334196] usb 4-3: configuration #1 chosen from 1 choice
[    2.353844] scsi 0:0:0:0: Direct-Access     ATA      MAXTOR STM332082 3.AA PQ: 0 ANSI: 5
[    2.353916] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.353940] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    2.353961] sd 0:0:0:0: [sda] Write Protect is off
[    2.353963] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.353974] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.354036]  sda:
[    2.357412] scsi 2:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH22NS40  NL01 PQ: 0 ANSI: 5
[    2.371070]  sda1 sda2 <sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.378380] Uniform CD-ROM driver Revision: 3.20
[    2.378427] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    2.378451] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    2.394769]  sda5 >
[    2.394920] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.530105] Freeing unused kernel memory: 660k freed
[    2.530226] Write protecting the kernel read-only data: 7584k
[    2.609874] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.609893] r8169 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.609937] r8169 0000:02:00.0: setting latency timer to 64
[    2.609979]   alloc irq_desc for 27 on node 0
[    2.609980]   alloc kstat_irqs on node 0
[    2.609990] r8169 0000:02:00.0: irq 27 for MSI/MSI-X
[    2.610391] eth0: RTL8168b/8111b at 0xffffc90000674000, 00:26:18:df:0c:b4, XID 38000000 IRQ 27
[    2.612693] usbcore: registered new interface driver hiddev
[    2.618354] input: Logitech Trackball as /devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.0/input/input3
[    2.618404] generic-usb 0003:046D:C404.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech Trackball] on usb-0000:00:12.1-2/input0
[    2.623309] input: LITE-ON Technology USB NetVista Full Width Keyboard. as /devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.0/input/input4
[    2.623341] generic-usb 0003:04B3:3025.0002: input,hidraw1: USB HID v1.10 Keyboard [LITE-ON Technology USB NetVista Full Width Keyboard.] on usb-0000:00:12.1-3/input0
[    2.623351] usbcore: registered new interface driver usbhid
[    2.623352] usbhid: v2.6:USB HID core driver
[    4.217694] PM: Starting manual resume from disk
[    4.217696] PM: Resume from partition 8:5
[    4.217697] PM: Checking hibernation image.
[    4.217837] PM: Resume from disk failed.
[    4.240460] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    4.240463] EXT4-fs (sda1): write access will be enabled during recovery
[    4.247257] EXT4-fs (sda1): barriers enabled
[    5.212126] kjournald2 starting: pid 408, dev sda1:8, commit interval 5 seconds
[    5.212138] EXT4-fs (sda1): delayed allocation enabled
[    5.212141] EXT4-fs: file extents enabled
[    5.229369] EXT4-fs: mballoc enabled
[    5.229379] EXT4-fs (sda1): recovery complete
[    5.234320] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    6.258350] type=1505 audit(1261371579.287:2): operation="profile_load" pid=431 name=/usr/share/gdm/guest-session/Xsession
[    6.259842] type=1505 audit(1261371579.287:3): operation="profile_load" pid=432 name=/sbin/dhclient3
[    6.260023] type=1505 audit(1261371579.287:4): operation="profile_load" pid=432 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    6.260124] type=1505 audit(1261371579.287:5): operation="profile_load" pid=432 name=/usr/lib/connman/scripts/dhclient-script
[    6.308510] type=1505 audit(1261371579.337:6): operation="profile_load" pid=433 name=/usr/bin/evince
[    6.311378] type=1505 audit(1261371579.337:7): operation="profile_load" pid=433 name=/usr/bin/evince-previewer
[    6.313104] type=1505 audit(1261371579.337:8): operation="profile_load" pid=433 name=/usr/bin/evince-thumbnailer
[    6.342442] type=1505 audit(1261371579.367:9): operation="profile_load" pid=435 name=/usr/lib/cups/backend/cups-pdf
[    6.342661] type=1505 audit(1261371579.367:10): operation="profile_load" pid=435 name=/usr/sbin/cupsd
[    6.343958] type=1505 audit(1261371579.377:11): operation="profile_load" pid=436 name=/usr/sbin/tcpdump
[   13.073498] udev: starting version 147
[   13.099659] Adding 11888060k swap on /dev/sda5.  Priority:-1 extents:1 across:11888060k 
[   13.101291] nvidia: module license 'NVIDIA' taints kernel.
[   13.101294] Disabling lock debugging due to kernel taint
[   13.131052] EDAC MC: Ver: 2.1.0 Dec  8 2009
[   13.134700] ACPI: I/O resource piix4_smbus [0xb00-0xb07] conflicts with ACPI region SOR1 [0xb00-0xb0f]
[   13.134703] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   13.134720] piix4_smbus: probe of 0000:00:14.0 failed with error -16
[   13.136788] EDAC amd64_edac:  Ver: 3.2.0 Dec  8 2009
[   13.136944] EDAC amd64: This node reports that Memory ECC is currently disabled.
[   13.136947] EDAC amd64: bit 0x400000 in register F3x44 of the MISC_CONTROL device (0000:00:18.3) should be enabled
[   13.136949] EDAC amd64: WARNING: ECC is NOT currently enabled by the BIOS. Module will NOT be loaded.
[   13.136949]     Either Enable ECC in the BIOS, or use the 'ecc_enable_override' parameter.
[   13.136950]     Might be a BIOS bug, if BIOS says ECC is enabled
[   13.136951]     Use of the override can cause unknown side effects.
[   13.136963] amd64_edac: probe of 0000:00:18.2 failed with error -22
[   13.142475] r8169: eth0: link up
[   13.142480] r8169: eth0: link up
[   13.142965] lp: driver loaded but no devices found
[   13.189437] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.209878] ip_tables: (C) 2000-2006 Netfilter Core Team
[   13.314854] hda_codec: Unknown model for ALC887, trying auto-probe from BIOS...
[   13.315147] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input5
[   13.318984] EXT4-fs (sda1): internal journal on sda1:8
[   13.355262] nvidia 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   13.355271] nvidia 0000:01:00.0: setting latency timer to 64
[   13.355393] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  185.18.36  Fri Aug 14 17:35:21 PDT 2009
[   13.380574] type=1505 audit(1261371586.407:12): operation="profile_replace" pid=994 name=/usr/share/gdm/guest-session/Xsession
[   13.381470] type=1505 audit(1261371586.407:13): operation="profile_replace" pid=995 name=/sbin/dhclient3
[   13.381654] type=1505 audit(1261371586.407:14): operation="profile_replace" pid=995 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   13.381757] type=1505 audit(1261371586.407:15): operation="profile_replace" pid=995 name=/usr/lib/connman/scripts/dhclient-script
[   13.383756] type=1505 audit(1261371586.407:16): operation="profile_replace" pid=996 name=/usr/bin/evince
[   13.386661] type=1505 audit(1261371586.417:17): operation="profile_replace" pid=996 name=/usr/bin/evince-previewer
[   13.388393] type=1505 audit(1261371586.417:18): operation="profile_replace" pid=996 name=/usr/bin/evince-thumbnailer
[   13.391563] type=1505 audit(1261371586.417:19): operation="profile_replace" pid=998 name=/usr/lib/cups/backend/cups-pdf
[   13.391784] type=1505 audit(1261371586.417:20): operation="profile_replace" pid=998 name=/usr/sbin/cupsd
[   13.392875] type=1505 audit(1261371586.417:21): operation="profile_replace" pid=999 name=/usr/sbin/tcpdump
[   13.970187] usplash:371 freeing invalid memtype fffffffffb000000-fffffffffbe00000
[   15.893771] device eth0 entered promiscuous mode
[   15.953774] device eth0 left promiscuous mode
[   16.020027] device eth0 entered promiscuous mode
[   16.121658] ppdev: user-space parallel port driver
[   23.422513] eth0: no IPv6 routers present
[  600.950040] Machine check events logged  
```lsmod output:

```
 Module                  Size  Used by
binfmt_misc            10220  1 
ppdev                   8232  0 
snd_hda_codec_realtek   277860  1 
iptable_filter          3872  0 
ip_tables              21200  1 iptable_filter
x_tables               25832  1 ip_tables
snd_hda_intel          31880  2 
snd_hda_codec          87584  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
snd_rawmidi            27360  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    77096  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lp                     11908  0 
parport                40528  2 ppdev,lp
amd64_edac_mod         26688  0 
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
edac_core              48876  1 amd64_edac_mod
asus_atk0110            9472  0 
psmouse                57124  0 
i2c_piix4              11728  0 
serio_raw               6596  0 
nvidia              10316904  36 
usbhid                 43968  0 
r8169                  38884  0 
mii                     6368  1 r8169 
```

---

### Post by josarn on 2009-12-29
This issue has been reported for quite some time now:

[http://bugs.launchpad.net/ubuntu/+source/linux/+bug/483483]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/483483")

There has been no new developments since then.

---

### Post by josarn on 2010-01-05
[LEFT]New kernel...
[/LEFT]
 
output of "uname -r"
```
2.6.31-17-generic
```Still getting the system freeze when a usb storage device is plugged in.

I have been googlin' on and off on the subject and there seems to be a lot of freezes going on in AMD64 systems. I get the distinct impression there is a firm believe that the privative Nvidia driver is the cause. 
Just for the sake of it (can't do much about solving the issue) I removed the driver and its tainting of the kernel but didn't change the situation.

---

### Post by josarn on 2010-01-10
I have the AMD64 system (an Asus M4A78-VM motherboard) and a netbook (Acer Aspire One A150). The USB subsystem seems to work fine in the netbook (32 bit) but not in the desktop.
Another thing worth mentioning is that I gave a try to the latest stable Debian release "Lenny" (64 bit) and the problem was gone but reappeared when I installed the unstable release "Sid" . 

I hope this information proves to be helpful in some way...

*EDIT: the difference in the modules loaded in my two systems is that the "usbstorage" modules isn't loaded in the desktop.

---

### Post by josarn on 2010-01-10
Problem solved....

the "sudo modprobe usb_sotarge" command does the trick...

---

### Post by josarn on 2010-01-11
New kernel update: 2.6.31-18-generic . No use including the "usb_storage" in "/etc/modules", the problem is still there. Issues should have the decency of not working if they are not fixed. :)

---

### Post by josarn on 2010-01-11
Booted with the previous kernel image and the issue persisted. It is as if I had dreamt that yesterday I was able to plug a USB storage device without the system freezing...

---

### Post by josarn on 2010-01-14
Found this bug report about USB ehci_hcd mode not working on a system with my same chipset AMD SB700 as my system has. Tried the solution of including the ehci module in "/etc/initramfs-tools/modules" and run the "sudo update-initramfs -u" command. 
System freezes still there... 

The link to the bug reported I was talking about:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/313603](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/313603)

***Edit: Forgot to mention the bug report on reply #2 was made on a system with a nForce4 chipset and I have the same problem on an AMD 780g Chipset.

---

### Post by josarn on 2010-01-14
Used Ubuntu's installation CD as found in main homepage to boot into a LiveCD and was able to plug a USB storage device without the freezing issue...

---

### Post by josarn on 2010-01-16
This should be my last comment on the subject. I have enjoyed myself looking into this  although it has always been clear to me that there wasn't much I could do to help solve the issue.
I don't have a clear picture of what the problem might be but I did end up with the feeling that I had made a mistake by acquiring a mobo with an  AMD chipset because of the line in dmesg about having to apply a workaround to prevent a USB freeze (SB600 & SB700).
So I rounded up the little money I could and got one with a nvidia chipset (Geforce 8300).
When it comes to the USB subsytem the new mobo does have the freezing issue from the moment the new Ubuntu install upgraded the kernel (I could have sticked to a working LTS release so I am not complainig).

For the curious here is the output of dmesg with the new mobo:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-18-generic (buildd@yellow) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #55-Ubuntu SMP Fri Jan 8 14:54:52 UTC 2010 (Ubuntu 2.6.31-18.55-generic)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-18-generic root=UUID=dec5a773-d8b2-4a4d-a852-359e53fa6d7e ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e000 (usable)
[    0.000000]  BIOS-e820: 000000000009e000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e3000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cff90000 (usable)
[    0.000000]  BIOS-e820: 00000000cff90000 - 00000000cffa8000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cffa8000 - 00000000cffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cffe0000 - 00000000d0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x130000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 base 0000C0000000 mask FFFFF0000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000130000000 aka 4864M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000d0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xcff90 max_arch_pfn = 0x400000000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009e000 (usable)
[    0.000000]  modified: 000000000009e000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e3000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000cff90000 (usable)
[    0.000000]  modified: 00000000cff90000 - 00000000cffa8000 (ACPI data)
[    0.000000]  modified: 00000000cffa8000 - 00000000cffe0000 (ACPI NVS)
[    0.000000]  modified: 00000000cffe0000 - 00000000d0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: 0000000000000000-00000000cff90000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 00c0000000 page 1G
[    0.000000]  00c0000000 - 00cfe00000 page 2M
[    0.000000]  00cfe00000 - 00cff90000 page 4k
[    0.000000] kernel direct mapping tables up to cff90000 @ 10000-13000
[    0.000000] init_memory_mapping: 0000000100000000-0000000130000000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0100000000 - 0130000000 page 2M
[    0.000000] kernel direct mapping tables up to 130000000 @ 12000-14000
[    0.000000] RAMDISK: 3786c000 - 37fef1f1
[    0.000000] ACPI: RSDP 00000000000fbbb0 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 00000000cff90100 00064 (v01 090209 XSDT1127 20090902 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000cff90290 000F4 (v03 090209 FACP1127 20090902 MSFT 00000097)
[    0.000000] ACPI: DSDT 00000000cff90450 0BF1B (v01  A1191 A1191001 00000001 INTL 20060113)
[    0.000000] ACPI: FACS 00000000cffa8000 00040
[    0.000000] ACPI: APIC 00000000cff90390 00080 (v01 090209 APIC1127 20090902 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000cff90410 0003C (v01 090209 OEMMCFG  20090902 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000cffa8040 00073 (v01 090209 OEMB1127 20090902 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000cff9c370 00038 (v01 090209 OEMHPET0 20090902 MSFT 00000097)
[    0.000000] ACPI: INFO 00000000cffa80c0 00124 (v01 090209 AMDINFO  20090902 MSFT 00000097)
[    0.000000] ACPI: NVHD 00000000cffa81f0 00284 (v01 090209  NVHDCP  20090902 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000cff9c3b0 0088C (v01 A M I  POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000130000000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000130000000
[    0.000000]   NODE_DATA [0000000000013000 - 0000000000017fff]
[    0.000000]   bootmap [0000000000018000 -  000000000003dfff] pages 26
[    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0130000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 00019e7c8c]    TEXT DATA BSS ==> [0001000000 - 00019e7c8c]
[    0.000000]   #3 [003786c000 - 0037fef1f1]          RAMDISK ==> [003786c000 - 0037fef1f1]
[    0.000000]   #4 [000009e000 - 0000100000]    BIOS reserved ==> [000009e000 - 0000100000]
[    0.000000]   #5 [00019e8000 - 00019e8290]              BRK ==> [00019e8000 - 00019e8290]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [0000012000 - 0000013000]          PGTABLE ==> [0000012000 - 0000013000]
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000]  [ffffea0000000000-ffffea00043fffff] PMD -> [ffff880028600000-ffff88002bffffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00130000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000cff90
[    0.000000]     0: 0x00100000 -> 0x00130000
[    0.000000] On node 0 totalpages: 1048350
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 104 pages reserved
[    0.000000]   DMA zone: 3822 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 833480 pages, LIFO batch:31
[    0.000000]   Normal zone: 2688 pages used for memmap
[    0.000000]   Normal zone: 193920 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x2008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e3000
[    0.000000] PM: Registered nosave memory: 00000000000e3000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cff90000 - 00000000cffa8000
[    0.000000] PM: Registered nosave memory: 00000000cffa8000 - 00000000cffe0000
[    0.000000] PM: Registered nosave memory: 00000000cffe0000 - 00000000d0000000
[    0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fef00000
[    0.000000] PM: Registered nosave memory: 00000000fef00000 - 00000000fff00000
[    0.000000] PM: Registered nosave memory: 00000000fff00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at d0000000 (gap: d0000000:2ec00000)
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages at ffff880028022000, static data 90720 bytes
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1031222
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-18-generic root=UUID=dec5a773-d8b2-4a4d-a852-359e53fa6d7e ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ 20000000 size 32 MB
[    0.000000] Aperture pointing to e820 RAM. Ignoring.
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ 20000000
[    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000024000000
[    0.000000] Memory: 4049912k/4980736k available (5328k kernel code, 787336k absent, 143488k reserved, 3013k data, 660k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] NR_IRQS:4352 nr_irqs:440
[    0.000000] Extended CMOS year: 2000
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 3200.410 MHz processor.
[    0.000012] spurious 8259A interrupt: IRQ7.
[    0.001695] Console: colour VGA+ 80x25
[    0.001697] console [tty0] enabled
[    0.010000] allocated 41943040 bytes of page_cgroup
[    0.010000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.010000] hpet clockevent registered
[    0.010000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.010000] Calibrating delay loop (skipped), value calculated using timer frequency.. 6400.81 BogoMIPS (lpj=32004060)
[    0.010000] Security Framework initialized
[    0.010000] AppArmor: AppArmor initialized
[    0.010000] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.010000] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.010000] Mount-cache hash table entries: 256
[    0.010000] Initializing cgroup subsys ns
[    0.010000] Initializing cgroup subsys cpuacct
[    0.010000] Initializing cgroup subsys memory
[    0.010000] Initializing cgroup subsys freezer
[    0.010000] Initializing cgroup subsys net_cls
[    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.010000] CPU 0/0x0 -> Node 0
[    0.010000] tseg: 0000000000
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 0
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] using C1E aware idle routine
[    0.010000] Performance Counters: AMD PMU driver.
[    0.010000] ... version:                 0
[    0.010000] ... bit width:               48
[    0.010000] ... generic counters:        4
[    0.010000] ... value mask:              0000ffffffffffff
[    0.010000] ... max period:              00007fffffffffff
[    0.010000] ... fixed-purpose counters:  0
[    0.010000] ... counter mask:            000000000000000f
[    0.010000] ACPI: Core revision 20090521
[    0.017386] Setting APIC routing to flat
[    0.017840] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.117875] CPU0: AMD Phenom(tm) II X4 955 Processor stepping 02
[    0.120000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.010000] Initializing CPU#1
[    0.010000] Calibrating delay using timer specific routine.. 6399.99 BogoMIPS (lpj=31999970)
[    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.010000] CPU 1/0x1 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 1
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.270871] CPU1: AMD Phenom(tm) II X4 955 Processor stepping 02
[    0.270881] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.280044] Booting processor 2 APIC 0x2 ip 0x6000
[    0.010000] Initializing CPU#2
[    0.010000] Calibrating delay using timer specific routine.. 6399.98 BogoMIPS (lpj=31999946)
[    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.010000] CPU 2/0x2 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 2
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] x86 PAT enabled: cpu 2, old 0x7040600070406, new 0x7010600070106
[    0.440883] CPU2: AMD Phenom(tm) II X4 955 Processor stepping 02
[    0.440892] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.450044] Booting processor 3 APIC 0x3 ip 0x6000
[    0.010000] Initializing CPU#3
[    0.010000] Calibrating delay using timer specific routine.. 6399.98 BogoMIPS (lpj=31999917)
[    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.010000] CPU 3/0x3 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 3
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] x86 PAT enabled: cpu 3, old 0x7040600070406, new 0x7010600070106
[    0.610892] CPU3: AMD Phenom(tm) II X4 955 Processor stepping 02
[    0.610901] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[    0.620013] Brought up 4 CPUs
[    0.620014] Total of 4 processors activated (25600.77 BogoMIPS).
[    0.620099] CPU0 attaching sched-domain:
[    0.620101]  domain 0: span 0-3 level MC
[    0.620102]   groups: 0 1 2 3
[    0.620106] CPU1 attaching sched-domain:
[    0.620107]  domain 0: span 0-3 level MC
[    0.620109]   groups: 1 2 3 0
[    0.620111] CPU2 attaching sched-domain:
[    0.620113]  domain 0: span 0-3 level MC
[    0.620114]   groups: 2 3 0 1
[    0.620116] CPU3 attaching sched-domain:
[    0.620117]  domain 0: span 0-3 level MC
[    0.620119]   groups: 3 0 1 2
[    0.620176] Booting paravirtualized kernel on bare hardware
[    0.620176] regulator: core version 0.5
[    0.620176] Time:  5:23:46  Date: 01/16/10
[    0.620176] NET: Registered protocol family 16
[    0.620176] node 0 link 0: io port [1000, ffffff]
[    0.620176] node 0 link 0: io port [2000, 2fff]
[    0.620176] TOM: 00000000d0000000 aka 3328M
[    0.620176] Fam 10h mmconf [e0000000, efffffff]
[    0.620176] node 0 link 0: mmio [e0000000, efffffff] ==> none
[    0.620176] node 0 link 0: mmio [a0000, bffff]
[    0.620178] node 0 link 0: mmio [d0000000, fe0bffff] ==> [d0000000, dfffffff] and [f0000000, fe0bffff]
[    0.620181] TOM2: 0000000130000000 aka 4864M
[    0.620182] bus: [00,07] on node 0 link 0
[    0.620183] bus: 00 index 0 io port: [0, ffff]
[    0.620185] bus: 00 index 1 mmio: [a0000, bffff]
[    0.620186] bus: 00 index 2 mmio: [d0000000, dfffffff]
[    0.620187] bus: 00 index 3 mmio: [f0000000, ffffffff]
[    0.620188] bus: 00 index 4 mmio: [130000000, fcffffffff]
[    0.620199] ACPI: bus type pci registered
[    0.620250] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.620251] PCI: Not using MMCONFIG.
[    0.620253] PCI: Using configuration type 1 for base access
[    0.620254] PCI: Using configuration type 1 for extended access
[    0.620674] bio: create slab <bio-0> at 0
[    0.620681] ACPI: EC: Look up EC in DSDT
[    0.763858] ACPI: Interpreter enabled
[    0.763861] ACPI: (supports S0 S1 S3 S4 S5)
[    0.763875] ACPI: Using IOAPIC for interrupt routing
[    0.763925] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.769455] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.774827] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.785600] ACPI Warning: Incorrect checksum in table [OEMB] - 79, should be 71 20090521 tbutils-246
[    0.785787] ACPI: No dock devices found.
[    0.786121] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.786363] pci 0000:00:01.0: reg 10 io port: [0x2f00-0x2fff]
[    0.786398] pci 0000:00:01.1: reg 10 io port: [0x2900-0x293f]
[    0.786407] pci 0000:00:01.1: reg 20 io port: [0x2d00-0x2d3f]
[    0.786410] pci 0000:00:01.1: reg 24 io port: [0x2e00-0x2e3f]
[    0.786427] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.786432] pci 0000:00:01.1: PME# disabled
[    0.786483] pci 0000:00:01.3: reg 10 32bit mmio: [0xf7f80000-0xf7ffffff]
[    0.786601] pci 0000:00:02.0: reg 10 32bit mmio: [0xf7f7e000-0xf7f7efff]
[    0.786620] pci 0000:00:02.0: supports D1 D2
[    0.786622] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.786624] pci 0000:00:02.0: PME# disabled
[    0.786643] pci 0000:00:02.1: reg 10 32bit mmio: [0xf7f7fc00-0xf7f7fcff]
[    0.786667] pci 0000:00:02.1: supports D1 D2
[    0.786669] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.786671] pci 0000:00:02.1: PME# disabled
[    0.786695] pci 0000:00:04.0: reg 10 32bit mmio: [0xf7f7d000-0xf7f7dfff]
[    0.786715] pci 0000:00:04.0: supports D1 D2
[    0.786716] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.786718] pci 0000:00:04.0: PME# disabled
[    0.786737] pci 0000:00:04.1: reg 10 32bit mmio: [0xf7f7f800-0xf7f7f8ff]
[    0.786761] pci 0000:00:04.1: supports D1 D2
[    0.786762] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.786765] pci 0000:00:04.1: PME# disabled
[    0.786794] pci 0000:00:06.0: reg 20 io port: [0xffa0-0xffaf]
[    0.786820] pci 0000:00:07.0: reg 10 32bit mmio: [0xf7f78000-0xf7f7bfff]
[    0.786840] pci 0000:00:07.0: PME# supported from D3hot D3cold
[    0.786842] pci 0000:00:07.0: PME# disabled
[    0.786885] pci 0000:00:09.0: reg 10 io port: [0xd480-0xd487]
[    0.786888] pci 0000:00:09.0: reg 14 io port: [0xd400-0xd403]
[    0.786890] pci 0000:00:09.0: reg 18 io port: [0xd080-0xd087]
[    0.786893] pci 0000:00:09.0: reg 1c io port: [0xd000-0xd003]
[    0.786896] pci 0000:00:09.0: reg 20 io port: [0xcc00-0xcc0f]
[    0.786898] pci 0000:00:09.0: reg 24 32bit mmio: [0xf7f76000-0xf7f77fff]
[    0.786929] pci 0000:00:0a.0: reg 10 32bit mmio: [0xf7f7c000-0xf7f7cfff]
[    0.786932] pci 0000:00:0a.0: reg 14 io port: [0xc880-0xc887]
[    0.786935] pci 0000:00:0a.0: reg 18 32bit mmio: [0xf7f7f400-0xf7f7f4ff]
[    0.786938] pci 0000:00:0a.0: reg 1c 32bit mmio: [0xf7f7f000-0xf7f7f00f]
[    0.786955] pci 0000:00:0a.0: supports D1 D2
[    0.786956] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.786959] pci 0000:00:0a.0: PME# disabled
[    0.787164] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.787170] pci 0000:00:10.0: PME# disabled
[    0.787401] pci 0000:00:13.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.787408] pci 0000:00:13.0: PME# disabled
[    0.787638] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.787645] pci 0000:00:14.0: PME# disabled
[    0.787764] pci 0000:00:08.0: transparent bridge
[    0.787803] pci 0000:02:00.0: reg 10 32bit mmio: [0xfb000000-0xfbffffff]
[    0.787811] pci 0000:02:00.0: reg 14 64bit mmio: [0xd0000000-0xdfffffff]
[    0.787820] pci 0000:02:00.0: reg 1c 64bit mmio: [0xf8000000-0xf9ffffff]
[    0.787825] pci 0000:02:00.0: reg 24 io port: [0xec00-0xec7f]
[    0.787830] pci 0000:02:00.0: reg 30 32bit mmio: [0xfafe0000-0xfaffffff]
[    0.787903] pci 0000:00:10.0: bridge io port: [0xe000-0xefff]
[    0.787910] pci 0000:00:10.0: bridge 32bit mmio: [0xf8000000-0xfbffffff]
[    0.787923] pci 0000:00:10.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.788096] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.788294] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.788404] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.MXR0._PRT]
[    0.788458] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR13._PRT]
[    0.788507] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR14._PRT]
[    0.801335] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
[    0.801539] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.
[    0.801740] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[    0.801941] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
[    0.802144] ACPI: PCI Interrupt Link [LN0A] (IRQs 16 17 18 19) *10
[    0.802345] ACPI: PCI Interrupt Link [LN0B] (IRQs 16 17 18 19) *0, disabled.
[    0.802545] ACPI: PCI Interrupt Link [LN0C] (IRQs 16 17 18 19) *0, disabled.
[    0.802745] ACPI: PCI Interrupt Link [LN0D] (IRQs 16 17 18 19) *0, disabled.
[    0.802946] ACPI: PCI Interrupt Link [LN1A] (IRQs 16 17 18 19) *0, disabled.
[    0.803146] ACPI: PCI Interrupt Link [LN1B] (IRQs 16 17 18 19) *0, disabled.
[    0.803347] ACPI: PCI Interrupt Link [LN1C] (IRQs 16 17 18 19) *0, disabled.
[    0.803547] ACPI: PCI Interrupt Link [LN1D] (IRQs 16 17 18 19) *0, disabled.
[    0.803747] ACPI: PCI Interrupt Link [LN2A] (IRQs 16 17 18 19) *0, disabled.
[    0.803948] ACPI: PCI Interrupt Link [LN2B] (IRQs 16 17 18 19) *0, disabled.
[    0.804148] ACPI: PCI Interrupt Link [LN2C] (IRQs 16 17 18 19) *0, disabled.
[    0.804349] ACPI: PCI Interrupt Link [LN2D] (IRQs 16 17 18 19) *0, disabled.
[    0.804554] ACPI: PCI Interrupt Link [LN3A] (IRQs 16 17 18 19) *11
[    0.804754] ACPI: PCI Interrupt Link [LN3B] (IRQs 16 17 18 19) *0, disabled.
[    0.804954] ACPI: PCI Interrupt Link [LN3C] (IRQs 16 17 18 19) *0, disabled.
[    0.805154] ACPI: PCI Interrupt Link [LN3D] (IRQs 16 17 18 19) *0, disabled.
[    0.805358] ACPI: PCI Interrupt Link [LN4A] (IRQs 16 17 18 19) *15
[    0.805557] ACPI: PCI Interrupt Link [LN4B] (IRQs 16 17 18 19) *0, disabled.
[    0.805758] ACPI: PCI Interrupt Link [LN4C] (IRQs 16 17 18 19) *0, disabled.
[    0.805958] ACPI: PCI Interrupt Link [LN4D] (IRQs 16 17 18 19) *0, disabled.
[    0.806158] ACPI: PCI Interrupt Link [LN5A] (IRQs 16 17 18 19) *0, disabled.
[    0.806358] ACPI: PCI Interrupt Link [LN5B] (IRQs 16 17 18 19) *0, disabled.
[    0.806558] ACPI: PCI Interrupt Link [LN5C] (IRQs 16 17 18 19) *0, disabled.
[    0.806758] ACPI: PCI Interrupt Link [LN5D] (IRQs 16 17 18 19) *0, disabled.
[    0.806959] ACPI: PCI Interrupt Link [LN6A] (IRQs 16 17 18 19) *0, disabled.
[    0.807159] ACPI: PCI Interrupt Link [LN6B] (IRQs 16 17 18 19) *0, disabled.
[    0.807359] ACPI: PCI Interrupt Link [LN6C] (IRQs 16 17 18 19) *0, disabled.
[    0.807560] ACPI: PCI Interrupt Link [LN6D] (IRQs 16 17 18 19) *0, disabled.
[    0.807760] ACPI: PCI Interrupt Link [LN7A] (IRQs 16 17 18 19) *0, disabled.
[    0.807961] ACPI: PCI Interrupt Link [LN7B] (IRQs 16 17 18 19) *0, disabled.
[    0.808161] ACPI: PCI Interrupt Link [LN7C] (IRQs 16 17 18 19) *0, disabled.
[    0.808362] ACPI: PCI Interrupt Link [LN7D] (IRQs 16 17 18 19) *0, disabled.
[    0.808566] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *15
[    0.808770] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *11
[    0.808974] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *15
[    0.809178] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *11
[    0.809378] ACPI: PCI Interrupt Link [SGRU] (IRQs 20 21 22 23) *0, disabled.
[    0.809584] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *10
[    0.809788] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *7
[    0.810025] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *5
[    0.810260] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[    0.810464] ACPI: PCI Interrupt Link [UB11] (IRQs 20 21 22 23) *10
[    0.810667] ACPI: PCI Interrupt Link [UB12] (IRQs 20 21 22 23) *10
[    0.810777] SCSI subsystem initialized
[    0.810798] libata version 3.00 loaded.
[    0.810798] usbcore: registered new interface driver usbfs
[    0.810798] usbcore: registered new interface driver hub
[    0.810798] usbcore: registered new device driver usb
[    0.810798] ACPI: WMI: Mapper loaded
[    0.810798] PCI: Using ACPI for IRQ routing
[    0.850010] Bluetooth: Core ver 2.15
[    0.850031] NET: Registered protocol family 31
[    0.850031] Bluetooth: HCI device and connection manager initialized
[    0.850031] Bluetooth: HCI socket layer initialized
[    0.850031] NetLabel: Initializing
[    0.850031] NetLabel:  domain hash size = 128
[    0.850031] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.850031] NetLabel:  unlabeled traffic allowed by default
[    0.850232] PCI-DMA: Disabling AGP.
[    0.850299] PCI-DMA: aperture base @ 20000000 size 65536 KB
[    0.850300] PCI-DMA: using GART IOMMU.
[    0.850302] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    0.851840] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.851845] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.890011] Switched to high resolution mode on CPU 0
[    0.890906] Switched to high resolution mode on CPU 1
[    0.890928] Switched to high resolution mode on CPU 2
[    0.890932] Switched to high resolution mode on CPU 3
[    0.910026] pnp: PnP ACPI init
[    0.910041] ACPI: bus type pnp registered
[    0.915686] pnp: PnP ACPI: found 12 devices
[    0.915687] ACPI: ACPI bus type pnp unregistered
[    0.915695] system 00:05: ioport range 0x4d0-0x4d1 has been reserved
[    0.915697] system 00:05: ioport range 0x800-0x80f has been reserved
[    0.915699] system 00:05: ioport range 0x2000-0x207f has been reserved
[    0.915701] system 00:05: ioport range 0x2080-0x20ff has been reserved
[    0.915702] system 00:05: ioport range 0x2400-0x247f has been reserved
[    0.915704] system 00:05: ioport range 0x2480-0x24ff has been reserved
[    0.915705] system 00:05: ioport range 0x2800-0x287f has been reserved
[    0.915707] system 00:05: ioport range 0x2880-0x28ff has been reserved
[    0.915709] system 00:05: iomem range 0xfed04000-0xfed04fff has been reserved
[    0.915711] system 00:05: iomem range 0xfee01000-0xfeefffff has been reserved
[    0.915715] system 00:08: ioport range 0xc00-0xc0f has been reserved
[    0.915716] system 00:08: ioport range 0xd00-0xd0f has been reserved
[    0.915718] system 00:08: ioport range 0xa20-0xa2f has been reserved
[    0.915719] system 00:08: ioport range 0xa30-0xa3f has been reserved
[    0.915722] system 00:09: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.915724] system 00:09: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.915727] system 00:0a: iomem range 0xe0000000-0xefffffff has been reserved
[    0.915730] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[    0.915731] system 00:0b: iomem range 0xc0000-0xcffff has been reserved
[    0.915733] system 00:0b: iomem range 0xe0000-0xfffff could not be reserved
[    0.915735] system 00:0b: iomem range 0x100000-0xcfffffff could not be reserved
[    0.915736] system 00:0b: iomem range 0xfec00000-0xffffffff could not be reserved
[    0.920370] AppArmor: AppArmor Filesystem Enabled
[    0.920433] pci 0000:00:08.0: PCI bridge, secondary bus 0000:01
[    0.920434] pci 0000:00:08.0:   IO window: disabled
[    0.920437] pci 0000:00:08.0:   MEM window: disabled
[    0.920438] pci 0000:00:08.0:   PREFETCH window: disabled
[    0.920441] pci 0000:00:10.0: PCI bridge, secondary bus 0000:02
[    0.920445] pci 0000:00:10.0:   IO window: 0xe000-0xefff
[    0.920454] pci 0000:00:10.0:   MEM window: 0xf8000000-0xfbffffff
[    0.920460] pci 0000:00:10.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.920472] pci 0000:00:13.0: PCI bridge, secondary bus 0000:03
[    0.920473] pci 0000:00:13.0:   IO window: disabled
[    0.920481] pci 0000:00:13.0:   MEM window: disabled
[    0.920487] pci 0000:00:13.0:   PREFETCH window: disabled
[    0.920494] pci 0000:00:14.0: PCI bridge, secondary bus 0000:04
[    0.920495] pci 0000:00:14.0:   IO window: disabled
[    0.920503] pci 0000:00:14.0:   MEM window: disabled
[    0.920509] pci 0000:00:14.0:   PREFETCH window: disabled
[    0.920519] pci 0000:00:08.0: setting latency timer to 64
[    0.920821] ACPI: PCI Interrupt Link [LN0A] enabled at IRQ 19
[    0.920823]   alloc irq_desc for 19 on node 0
[    0.920824]   alloc kstat_irqs on node 0
[    0.920831] pci 0000:00:10.0: PCI INT A -> Link[LN0A] -> GSI 19 (level, low) -> IRQ 19
[    0.920838] pci 0000:00:10.0: setting latency timer to 64
[    0.921131] ACPI: PCI Interrupt Link [LN3A] enabled at IRQ 18
[    0.921133]   alloc irq_desc for 18 on node 0
[    0.921134]   alloc kstat_irqs on node 0
[    0.921139] pci 0000:00:13.0: PCI INT A -> Link[LN3A] -> GSI 18 (level, low) -> IRQ 18
[    0.921146] pci 0000:00:13.0: setting latency timer to 64
[    0.921438] ACPI: PCI Interrupt Link [LN4A] enabled at IRQ 17
[    0.921439]   alloc irq_desc for 17 on node 0
[    0.921440]   alloc kstat_irqs on node 0
[    0.921445] pci 0000:00:14.0: PCI INT A -> Link[LN4A] -> GSI 17 (level, low) -> IRQ 17
[    0.921452] pci 0000:00:14.0: setting latency timer to 64
[    0.921457] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.921459] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.921461] pci_bus 0000:01: resource 3 io:  [0x00-0xffff]
[    0.921462] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.921464] pci_bus 0000:02: resource 0 io:  [0xe000-0xefff]
[    0.921465] pci_bus 0000:02: resource 1 mem: [0xf8000000-0xfbffffff]
[    0.921467] pci_bus 0000:02: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.921492] NET: Registered protocol family 2
[    0.921597] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.922277] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.924346] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.924644] TCP: Hash tables configured (established 524288 bind 65536)
[    0.924646] TCP reno registered
[    0.924713] NET: Registered protocol family 1
[    0.924755] Trying to unpack rootfs image as initramfs...
[    1.038715] Freeing initrd memory: 7692k freed
[    1.041080] Scanning for low memory corruption every 60 seconds
[    1.041165] audit: initializing netlink socket (disabled)
[    1.041177] type=2000 audit(1263619426.040:1): initialized
[    1.046667] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.047528] VFS: Disk quotas dquot_6.5.2
[    1.047559] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.047920] fuse init (API version 7.12)
[    1.047966] msgmni has been set to 7925
[    1.048144] alg: No test for stdrng (krng)
[    1.048154] io scheduler noop registered
[    1.048155] io scheduler anticipatory registered
[    1.048157] io scheduler deadline registered
[    1.048180] io scheduler cfq registered (default)
[    1.100154] pci 0000:00:08.0: Enabling HT MSI Mapping
[    1.100251] pci 0000:00:09.0: Enabling HT MSI Mapping
[    1.100352] pci 0000:00:0a.0: Enabling HT MSI Mapping
[    1.100527] pci 0000:02:00.0: Boot video device
[    1.100823]   alloc irq_desc for 24 on node 0
[    1.100824]   alloc kstat_irqs on node 0
[    1.100841] pcieport-driver 0000:00:10.0: irq 24 for MSI/MSI-X
[    1.100859] pcieport-driver 0000:00:10.0: setting latency timer to 64
[    1.101242]   alloc irq_desc for 25 on node 0
[    1.101243]   alloc kstat_irqs on node 0
[    1.101259] pcieport-driver 0000:00:13.0: irq 25 for MSI/MSI-X
[    1.101276] pcieport-driver 0000:00:13.0: setting latency timer to 64
[    1.101635]   alloc irq_desc for 26 on node 0
[    1.101636]   alloc kstat_irqs on node 0
[    1.101651] pcieport-driver 0000:00:14.0: irq 26 for MSI/MSI-X
[    1.101668] pcieport-driver 0000:00:14.0: setting latency timer to 64
[    1.101812] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.101825] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.101901] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.101904] ACPI: Power Button [PWRF]
[    1.101938] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.101940] ACPI: Power Button [PWRB]
[    1.102509] processor LNXCPU:00: registered as cooling_device0
[    1.102835] processor LNXCPU:01: registered as cooling_device1
[    1.103159] processor LNXCPU:02: registered as cooling_device2
[    1.103489] processor LNXCPU:03: registered as cooling_device3
[    1.108786] Linux agpgart interface v0.103
[    1.108792] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.109398] brd: module loaded
[    1.109625] loop: module loaded
[    1.109661] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.109771] ahci 0000:00:09.0: version 3.0
[    1.110098] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 23
[    1.110100]   alloc irq_desc for 23 on node 0
[    1.110101]   alloc kstat_irqs on node 0
[    1.110108] ahci 0000:00:09.0: PCI INT A -> Link[LSA0] -> GSI 23 (level, low) -> IRQ 23
[    1.110130]   alloc irq_desc for 27 on node 0
[    1.110131]   alloc kstat_irqs on node 0
[    1.110135] ahci 0000:00:09.0: irq 27 for MSI/MSI-X
[    1.110182] ahci 0000:00:09.0: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    1.110184] ahci 0000:00:09.0: flags: 64bit ncq sntf led clo pmp pio 
[    1.110186] ahci 0000:00:09.0: setting latency timer to 64
[    1.110555] scsi0 : ahci
[    1.110612] scsi1 : ahci
[    1.110644] scsi2 : ahci
[    1.110675] scsi3 : ahci
[    1.110704] scsi4 : ahci
[    1.110736] scsi5 : ahci
[    1.110806] ata1: SATA max UDMA/133 abar m8192@0xf7f76000 port 0xf7f76100 irq 27
[    1.110808] ata2: SATA max UDMA/133 abar m8192@0xf7f76000 port 0xf7f76180 irq 27
[    1.110809] ata3: SATA max UDMA/133 abar m8192@0xf7f76000 port 0xf7f76200 irq 27
[    1.110811] ata4: SATA max UDMA/133 abar m8192@0xf7f76000 port 0xf7f76280 irq 27
[    1.110813] ata5: SATA max UDMA/133 abar m8192@0xf7f76000 port 0xf7f76300 irq 27
[    1.110814] ata6: SATA max UDMA/133 abar m8192@0xf7f76000 port 0xf7f76380 irq 27
[    1.110978] pata_amd 0000:00:06.0: version 0.4.1
[    1.111001] pata_amd 0000:00:06.0: setting latency timer to 64
[    1.111067] scsi6 : pata_amd
[    1.111107] scsi7 : pata_amd
[    1.111812] ata7: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    1.111813] ata8: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    1.112174] Fixed MDIO Bus: probed
[    1.112193] PPP generic driver version 2.4.2
[    1.112242] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.112591] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 22
[    1.112593]   alloc irq_desc for 22 on node 0
[    1.112594]   alloc kstat_irqs on node 0
[    1.112600] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUB2] -> GSI 22 (level, low) -> IRQ 22
[    1.112608] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    1.112609] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    1.112626] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    1.112647] ehci_hcd 0000:00:02.1: debug port 1
[    1.112650] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    1.112663] ehci_hcd 0000:00:02.1: irq 22, io mem 0xf7f7fc00
[    1.130016] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    1.130067] usb usb1: configuration #1 chosen from 1 choice
[    1.130083] hub 1-0:1.0: USB hub found
[    1.130087] hub 1-0:1.0: 6 ports detected
[    1.130443] ACPI: PCI Interrupt Link [UB12] enabled at IRQ 21
[    1.130445]   alloc irq_desc for 21 on node 0
[    1.130446]   alloc kstat_irqs on node 0
[    1.130452] ehci_hcd 0000:00:04.1: PCI INT B -> Link[UB12] -> GSI 21 (level, low) -> IRQ 21
[    1.130459] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    1.130461] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    1.130481] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 2
[    1.130499] ehci_hcd 0000:00:04.1: debug port 1
[    1.130502] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
[    1.130516] ehci_hcd 0000:00:04.1: irq 21, io mem 0xf7f7f800
[    1.150023] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    1.150063] usb usb2: configuration #1 chosen from 1 choice
[    1.150077] hub 2-0:1.0: USB hub found
[    1.150081] hub 2-0:1.0: 6 ports detected
[    1.150119] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.150440] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 20
[    1.150442]   alloc irq_desc for 20 on node 0
[    1.150443]   alloc kstat_irqs on node 0
[    1.150449] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUB0] -> GSI 20 (level, low) -> IRQ 20
[    1.150457] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    1.150459] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    1.150477] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 3
[    1.150495] ohci_hcd 0000:00:02.0: irq 20, io mem 0xf7f7e000
[    1.212054] usb usb3: configuration #1 chosen from 1 choice
[    1.212068] hub 3-0:1.0: USB hub found
[    1.212074] hub 3-0:1.0: 6 ports detected
[    1.212426] ACPI: PCI Interrupt Link [UB11] enabled at IRQ 23
[    1.212428] ohci_hcd 0000:00:04.0: PCI INT A -> Link[UB11] -> GSI 23 (level, low) -> IRQ 23
[    1.212436] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    1.212438] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    1.212455] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 4
[    1.212474] ohci_hcd 0000:00:04.0: irq 23, io mem 0xf7f7d000
[    1.272051] usb usb4: configuration #1 chosen from 1 choice
[    1.272067] hub 4-0:1.0: USB hub found
[    1.272074] hub 4-0:1.0: 6 ports detected
[    1.272109] uhci_hcd: USB Universal Host Controller Interface driver
[    1.272165] PNP: No PS/2 controller found. Probing ports directly.
[    1.272550] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.272563] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.272622] mice: PS/2 mouse device common for all mice
[    1.272683] rtc_cmos 00:07: RTC can wake from S4
[    1.272703] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    1.272754] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    1.272837] device-mapper: uevent: version 1.0.3
[    1.272899] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.272975] device-mapper: multipath: version 1.1.0 loaded
[    1.272977] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.273138] cpuidle: using governor ladder
[    1.273139] cpuidle: using governor menu
[    1.273375] TCP cubic registered
[    1.273445] NET: Registered protocol family 10
[    1.273710] lo: Disabled Privacy Extensions
[    1.273883] NET: Registered protocol family 17
[    1.273893] Bluetooth: L2CAP ver 2.13
[    1.273895] Bluetooth: L2CAP socket layer initialized
[    1.273896] Bluetooth: SCO (Voice Link) ver 0.6
[    1.273897] Bluetooth: SCO socket layer initialized
[    1.273937] Bluetooth: RFCOMM TTY layer initialized
[    1.273939] Bluetooth: RFCOMM socket layer initialized
[    1.273940] Bluetooth: RFCOMM ver 1.11
[    1.281066] powernow-k8: Found 1 AMD Phenom(tm) II X4 955 Processor processors (4 cpu cores) (version 2.20.00)
[    1.281100] powernow-k8:    0 : pstate 0 (3200 MHz)
[    1.281101] powernow-k8:    1 : pstate 1 (2500 MHz)
[    1.281103] powernow-k8:    2 : pstate 2 (2100 MHz)
[    1.281104] powernow-k8:    3 : pstate 3 (800 MHz)
[    1.281679] PM: Resume from disk failed.
[    1.281685] registered taskstats version 1
[    1.281761]   Magic number: 10:520:365
[    1.281848] rtc_cmos 00:07: setting system clock to 2010-01-16 05:23:47 UTC (1263619427)
[    1.281850] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.281851] EDD information not available.
[    1.460024] ata6: SATA link down (SStatus 0 SControl 300)
[    1.460035] ata5: SATA link down (SStatus 0 SControl 300)
[    1.460048] ata2: SATA link down (SStatus 0 SControl 300)
[    1.460061] ata4: SATA link down (SStatus 0 SControl 300)
[    1.640015] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.640025] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.643469] ata3.00: ATAPI: HL-DT-ST DVDRAM GH22NS40, NL01, max UDMA/100
[    1.647305] ata3.00: configured for UDMA/100
[    1.681719] ata1.00: ATA-7: MAXTOR STM3320820AS, 3.AAE, max UDMA/133
[    1.681722] ata1.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    1.730012] usb 3-2: new low speed USB device using ohci_hcd and address 2
[    1.740029] ata1.00: configured for UDMA/133
[    1.740105] scsi 0:0:0:0: Direct-Access     ATA      MAXTOR STM332082 3.AA PQ: 0 ANSI: 5
[    1.740174] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.740199] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.740220] sd 0:0:0:0: [sda] Write Protect is off
[    1.740221] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.740232] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.740295]  sda:
[    1.743659] scsi 2:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH22NS40  NL01 PQ: 0 ANSI: 5
[    1.764625] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.764628] Uniform CD-ROM driver Revision: 3.20
[    1.764672] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    1.764695] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    1.764758] ata8: port disabled. ignoring.
[    1.779706]  sda1 sda2 < sda5 >
[    1.803554] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.803562] Freeing unused kernel memory: 660k freed
[    1.803688] Write protecting the kernel read-only data: 7596k
[    1.884338] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.884700] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 22
[    1.884704] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 22 (level, low) -> IRQ 22
[    1.884708] forcedeth 0000:00:0a.0: setting latency timer to 64
[    1.907717] FDC 0 is a post-1991 82077
[    1.960992] usb 3-2: configuration #1 chosen from 1 choice
[    1.966859] usbcore: registered new interface driver hiddev
[    1.974103] input: Logitech Trackball as /devices/pci0000:00/0000:00:02.0/usb3/3-2/3-2:1.0/input/input3
[    1.974142] generic-usb 0003:046D:C404.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech Trackball] on usb-0000:00:02.0-2/input0
[    1.974151] usbcore: registered new interface driver usbhid
[    1.974152] usbhid: v2.6:USB HID core driver
[    2.360012] usb 4-2: new low speed USB device using ohci_hcd and address 2
[    2.410573] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 90:e6:ba:3f:9d:79
[    2.410575] forcedeth 0000:00:0a.0: highdma csum pwrctl mgmt gbit lnktim msi desc-v3
[    2.592908] usb 4-2: configuration #1 chosen from 1 choice
[    2.609003] input: LITE-ON Technology USB NetVista Full Width Keyboard. as /devices/pci0000:00/0000:00:04.0/usb4/4-2/4-2:1.0/input/input4
[    2.609036] generic-usb 0003:04B3:3025.0002: input,hidraw1: USB HID v1.10 Keyboard [LITE-ON Technology USB NetVista Full Width Keyboard.] on usb-0000:00:04.0-2/input0
[    3.800587] PM: Starting manual resume from disk
[    3.800589] PM: Resume from partition 8:5
[    3.800591] PM: Checking hibernation image.
[    3.800710] PM: Resume from disk failed.
[    3.830463] EXT4-fs (sda1): barriers enabled
[    3.847265] kjournald2 starting: pid 436, dev sda1:8, commit interval 5 seconds
[    3.847331] EXT4-fs (sda1): delayed allocation enabled
[    3.847333] EXT4-fs: file extents enabled
[    3.864582] EXT4-fs: mballoc enabled
[    3.864590] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    4.431642] type=1505 audit(1263619430.641:2): operation="profile_load" pid=463 name=/usr/share/gdm/guest-session/Xsession
[    4.433121] type=1505 audit(1263619430.650:3): operation="profile_load" pid=464 name=/sbin/dhclient3
[    4.433300] type=1505 audit(1263619430.650:4): operation="profile_load" pid=464 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    4.433400] type=1505 audit(1263619430.650:5): operation="profile_load" pid=464 name=/usr/lib/connman/scripts/dhclient-script
[    4.475429] type=1505 audit(1263619430.689:6): operation="profile_load" pid=465 name=/usr/bin/evince
[    4.478280] type=1505 audit(1263619430.689:7): operation="profile_load" pid=465 name=/usr/bin/evince-previewer
[    4.479992] type=1505 audit(1263619430.689:8): operation="profile_load" pid=465 name=/usr/bin/evince-thumbnailer
[    4.492675] type=1505 audit(1263619430.701:9): operation="profile_load" pid=467 name=/usr/lib/cups/backend/cups-pdf
[    4.492890] type=1505 audit(1263619430.701:10): operation="profile_load" pid=467 name=/usr/sbin/cupsd
[    5.622476] Adding 11888060k swap on /dev/sda5.  Priority:-1 extents:1 across:11888060k 
[    5.959014] EXT4-fs (sda1): internal journal on sda1:8
[    6.549790] udev: starting version 147
[    8.597039] nvidia: module license 'NVIDIA' taints kernel.
[    8.597043] Disabling lock debugging due to kernel taint
[    8.615081] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x2d00
[    8.615084] ACPI: I/O resource nForce2_smbus [0x2e00-0x2e3f] conflicts with ACPI region SM00 [0x2e00-0x2e3f]
[    8.615087] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.615088] nForce2_smbus 0000:00:01.1: Error probing SMB2.
[    8.623529] EDAC MC: Ver: 2.1.0 Jan  8 2010
[    8.638985] EDAC amd64_edac:  Ver: 3.2.0 Jan  8 2010
[    8.639131] EDAC amd64: This node reports that Memory ECC is currently disabled.
[    8.639134] EDAC amd64: bit 0x400000 in register F3x44 of the MISC_CONTROL device (0000:00:18.3) should be enabled
[    8.639136] EDAC amd64: WARNING: ECC is NOT currently enabled by the BIOS. Module will NOT be loaded.
[    8.639137]     Either Enable ECC in the BIOS, or use the 'ecc_enable_override' parameter.
[    8.639137]     Might be a BIOS bug, if BIOS says ECC is enabled
[    8.639138]     Use of the override can cause unknown side effects.
[    8.639147] amd64_edac: probe of 0000:00:18.2 failed with error -22
[    8.712795] lp: driver loaded but no devices found
[    8.738387] ip_tables: (C) 2000-2006 Netfilter Core Team
[    8.849998] nvidia 0000:02:00.0: PCI INT A -> Link[LN0A] -> GSI 19 (level, low) -> IRQ 19
[    8.850011] nvidia 0000:02:00.0: setting latency timer to 64
[    8.850163] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  185.18.36  Fri Aug 14 17:35:21 PDT 2009
[    9.122340] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[    9.122490] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[    9.122490] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[    9.122490] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[    9.572429] HDA Intel 0000:00:07.0: power state changed by ACPI to D0
[    9.572728] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[    9.572732] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
[    9.572768] HDA Intel 0000:00:07.0: setting latency timer to 64
[   10.836537] __ratelimit: 3 callbacks suppressed
[   10.836539] type=1505 audit(1263619437.051:12): operation="profile_replace" pid=901 name=/usr/share/gdm/guest-session/Xsession
[   10.837432] type=1505 audit(1263619437.051:13): operation="profile_replace" pid=902 name=/sbin/dhclient3
[   10.837611] type=1505 audit(1263619437.051:14): operation="profile_replace" pid=902 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   10.837713] type=1505 audit(1263619437.051:15): operation="profile_replace" pid=902 name=/usr/lib/connman/scripts/dhclient-script
[   10.839661] type=1505 audit(1263619437.051:16): operation="profile_replace" pid=903 name=/usr/bin/evince
[   10.842525] type=1505 audit(1263619437.051:17): operation="profile_replace" pid=903 name=/usr/bin/evince-previewer
[   10.844230] type=1505 audit(1263619437.061:18): operation="profile_replace" pid=903 name=/usr/bin/evince-thumbnailer
[   10.847297] type=1505 audit(1263619437.061:19): operation="profile_replace" pid=905 name=/usr/lib/cups/backend/cups-pdf
[   10.847513] type=1505 audit(1263619437.061:20): operation="profile_replace" pid=905 name=/usr/sbin/cupsd
[   10.848480] type=1505 audit(1263619437.061:21): operation="profile_replace" pid=906 name=/usr/sbin/tcpdump
[   12.969418]   alloc irq_desc for 28 on node 0
[   12.969421]   alloc kstat_irqs on node 0
[   12.969427] forcedeth 0000:00:0a.0: irq 28 for MSI/MSI-X
 
```

---

