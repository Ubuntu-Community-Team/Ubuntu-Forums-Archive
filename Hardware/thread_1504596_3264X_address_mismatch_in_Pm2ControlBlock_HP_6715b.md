---
title: "32/64X address mismatch in Pm2ControlBlock HP 6715b"
date: 2010-06-08
forum: Hardware
---

### Post by Beebock on 2010-06-08
Hi,

Been seeing a strange issue with a clean install of 10.04.

The machine seems to be running fine, but it does not seem to be running in the x64 mode.

Does anyone know about this?

Dmesg:

[PHP][    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-22-generic (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 (Ubuntu 2.6.32-22.36-generic 2.6.32.11+drm33.2)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=76239851-930b-4cdc-ab79-000c0f992057 ro quiet splash acpi=force
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000077fb0000 (usable)
[    0.000000]  BIOS-e820: 0000000077fb0000 - 0000000077fc8000 (reserved)
[    0.000000]  BIOS-e820: 0000000077fc8000 - 0000000077fe7fb8 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000077fe7fb8 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec02000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffbc0000 - 00000000ffcc0000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0x77fb0 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C0FFF write-protect
[    0.000000]   C1000-C3FFF write-back
[    0.000000]   C4000-C4FFF write-protect
[    0.000000]   C5000-C7FFF write-back
[    0.000000]   C8000-C8FFF write-protect
[    0.000000]   C9000-CBFFF write-back
[    0.000000]   CC000-CCFFF write-protect
[    0.000000]   CD000-CFFFF write-back
[    0.000000]   D0000-D0FFF write-protect
[    0.000000]   D1000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FFC0000000 write-back
[    0.000000]   1 base 0040000000 mask FFE0000000 write-back
[    0.000000]   2 base 0060000000 mask FFF0000000 write-back
[    0.000000]   3 base 0070000000 mask FFF8000000 write-back
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000001000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
[    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 0000000077fb0000 (usable)
[    0.000000]  modified: 0000000077fb0000 - 0000000077fc8000 (reserved)
[    0.000000]  modified: 0000000077fc8000 - 0000000077fe7fb8 (ACPI NVS)
[    0.000000]  modified: 0000000077fe7fb8 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec02000 (reserved)
[    0.000000]  modified: 00000000ffbc0000 - 00000000ffcc0000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-0000000077fb0000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 0077e00000 page 2M
[    0.000000]  0077e00000 - 0077fb0000 page 4k
[    0.000000] kernel direct mapping tables up to 77fb0000 @ 8000-c000
[    0.000000] RAMDISK: 377fe000 - 37fef69f
[    0.000000] ACPI: RSDP 00000000000fe0b0 00024 (v02 HP    )
[    0.000000] ACPI: XSDT 0000000077fc81bc 00064 (v01 HPQOEM SLIC-MPC 00000001 HP   00000001)
[    0.000000] ACPI: FACP 0000000077fc8084 000F4 (v04 HP     0944     00000003 HP   00000001)
[    0.000000] ACPI Error: 32/64X address mismatch in Pm2ControlBlock: 00008800/0000000000008100, using 32 (20090903/tbfadt-427)
[    0.000000] ACPI: DSDT 0000000077fc84a4 1193C (v01 HP        SB400 00010000 MSFT 03000001)
[    0.000000] ACPI: FACS 0000000077fe7d80 00040
[    0.000000] ACPI: SLIC 0000000077fc8220 00176 (v01 HPQOEM SLIC-MPC 00000001 HP   00000001)
[    0.000000] ACPI: EPTH 0000000077fc8398 00038 (v01 HP     0944     00000001 HP   00000001)
[    0.000000] ACPI: APIC 0000000077fc83d0 00062 (v01 HP     0944     00000001 HP   00000001)
[    0.000000] ACPI: MCFG 0000000077fc8434 0003C (v01 HP     0944     00000001 HP   00000001)
[    0.000000] ACPI: TCPA 0000000077fc8470 00032 (v02 HP     0944     00000001 HP   00000001)
[    0.000000] ACPI: SSDT 0000000077fd9de0 00059 (v01 HP       HPQNLP 00000001 MSFT 03000001)
[    0.000000] ACPI: SSDT 0000000077fd9e39 00206 (v01 HP     PSSTBLID 00000001 HP   00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000077fb0000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000077fb0000
[    0.000000]   NODE_DATA [000000000000a000 - 000000000000efff]
[    0.000000]   bootmap [000000000000f000 -  000000000001dff7] pages f
[    0.000000] (7 early reservations) ==> bootmem [0000000000 - 0077fb0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 0001a29e64]    TEXT DATA BSS ==> [0001000000 - 0001a29e64]
[    0.000000]   #3 [00377fe000 - 0037fef69f]          RAMDISK ==> [00377fe000 - 0037fef69f]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [0001a2a000 - 0001a2a190]              BRK ==> [0001a2a000 - 0001a2a190]
[    0.000000]   #6 [0000008000 - 000000a000]          PGTABLE ==> [0000008000 - 000000a000]
[    0.000000]  [ffffea0000000000-ffffea0001bfffff] PMD -> [ffff880002000000-ffff880003bfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000001
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x00077fb0
[    0.000000] On node 0 totalpages: 491338
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 101 pages reserved
[    0.000000]   DMA zone: 3837 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 6663 pages used for memmap
[    0.000000]   DMA32 zone: 480681 pages, LIFO batch:31
[    0.000000] SB600 revision 0x13
[    0.000000] Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:60000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001c00000 s91544 r8192 d23144 u1048576
[    0.000000] pcpu-alloc: s91544 r8192 d23144 u1048576 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 484518
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=76239851-930b-4cdc-ab79-000c0f992057 ro quiet splash acpi=force
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ 0 size 32 MB
[    0.000000] Memory: 1917716k/1965760k available (5409k kernel code, 408k absent, 47636k reserved, 2976k data, 876k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:4352 nr_irqs:424
[    0.000000] Extended CMOS year: 2000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 19660800 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1994.927 MHz processor.
[    0.010005] Calibrating delay loop (skipped), value calculated using timer frequency.. 3989.85 BogoMIPS (lpj=19949270)
[    0.010035] Security Framework initialized
[    0.010057] AppArmor: AppArmor initialized
[    0.010266] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.011370] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.011883] Mount-cache hash table entries: 256
[    0.012037] Initializing cgroup subsys ns
[    0.012042] Initializing cgroup subsys cpuacct
[    0.012046] Initializing cgroup subsys memory
[    0.012055] Initializing cgroup subsys devices
[    0.012058] Initializing cgroup subsys freezer
[    0.012060] Initializing cgroup subsys net_cls
[    0.012082] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.012085] CPU: L2 Cache: 512K (64 bytes/line)
[    0.012088] CPU 0/0x0 -> Node 0
[    0.012090] tseg: 0000000000
[    0.012107] CPU: Physical Processor ID: 0
[    0.012109] CPU: Processor Core ID: 0
[    0.012112] mce: CPU supports 5 MCE banks
[    0.012125] using C1E aware idle routine
[    0.012127] Performance Events: AMD PMU driver.
[    0.012133] ... version:                0
[    0.012135] ... bit width:              48
[    0.012137] ... generic registers:      4
[    0.012139] ... value mask:             0000ffffffffffff
[    0.012141] ... max period:             00007fffffffffff
[    0.012143] ... fixed-purpose events:   0
[    0.012145] ... event mask:             000000000000000f
[    0.014003] ACPI: Core revision 20090903
[    0.040025] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.040038] ftrace: allocating 22518 entries in 89 pages
[    0.050099] Setting APIC routing to flat
[    0.050422] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.152899] CPU0: AMD Turion(tm) 64 X2 Mobile Technology TL-60 stepping 02
[    0.160000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.020000] Initializing CPU#1
[    0.020000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.020000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.020000] CPU 1/0x1 -> Node 0
[    0.020000] CPU: Physical Processor ID: 0
[    0.020000] CPU: Processor Core ID: 1
[    0.020000] System has AMD C1E enabled
[    0.020000] Switch to broadcast mode on CPU1
[    0.310059] CPU1: AMD Turion(tm) 64 X2 Mobile Technology TL-60 stepping 02
[    0.310079] Brought up 2 CPUs
[    0.310082] Total of 2 processors activated (7979.96 BogoMIPS).
[    0.310258] CPU0 attaching sched-domain:
[    0.310261]  domain 0: span 0-1 level MC
[    0.310264]   groups: 0 1
[    0.310270] CPU1 attaching sched-domain:
[    0.310272]  domain 0: span 0-1 level MC
[    0.310275]   groups: 1 0
[    0.310366] Switch to broadcast mode on CPU0
[    0.310366] devtmpfs: initialized
[    0.310366] regulator: core version 0.5
[    0.310366] Time: 10:42:40  Date: 06/08/10
[    0.310366] NET: Registered protocol family 16
[    0.310366] Trying to unpack rootfs image as initramfs...
[    0.310366] node 0 link 0: io port [1000, fffff]
[    0.310366] TOM: 0000000080000000 aka 2048M
[    0.310366] node 0 link 0: mmio [e0000000, efffffff]
[    0.310366] node 0 link 0: mmio [f0000000, ffffffff]
[    0.310366] node 0 link 0: mmio [c8000000, dfffffff]
[    0.310366] node 0 link 0: mmio [c0000000, c7ffffff]
[    0.310366] node 0 link 0: mmio [a0000, bffff]
[    0.310366] node 0 link 0: mmio [80000000, bfffffff]
[    0.310366] bus: [00,ff] on node 0 link 0
[    0.310366] bus: 00 index 0 io port: [0, ffff]
[    0.310366] bus: 00 index 1 mmio: [80000000, fcffffffff]
[    0.310366] bus: 00 index 2 mmio: [a0000, bffff]
[    0.310366] ACPI: bus type pci registered
[    0.310381] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.310384] PCI: MCFG area at e0000000 reserved in E820
[    0.316806] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.316810] PCI: Using configuration type 1 for base access
[    0.320162] bio: create slab <bio-0> at 0
[    0.321067] ACPI: EC: Look up EC in DSDT
[    0.514320] Freeing initrd memory: 8133k freed
[    0.570225] ACPI: Interpreter enabled
[    0.570225] ACPI: (supports S0 S3 S4 S5)
[    0.570225] ACPI: Using IOAPIC for interrupt routing
[    0.590853] ACPI: EC: GPE = 0x11, I/O: command/status = 0x66, data = 0x62
[    0.590942] ACPI: Power Resource [C171] (off)
[    0.591121] ACPI: Power Resource [C224] (on)
[    0.591286] ACPI: Power Resource [C231] (on)
[    0.591330] ACPI: Power Resource [C24D] (on)
[    0.591425] ACPI: Power Resource [C397] (off)
[    0.591511] ACPI: Power Resource [C398] (off)
[    0.591594] ACPI: Power Resource [C399] (off)
[    0.591676] ACPI: Power Resource [C39A] (off)
[    0.592062] ACPI: No dock devices found.
[    0.597947] ACPI: PCI Root Bridge [C08B] (0000:00)
[    0.598080] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    0.598083] pci 0000:00:04.0: PME# disabled
[    0.598121] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.598124] pci 0000:00:05.0: PME# disabled
[    0.598162] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.598165] pci 0000:00:06.0: PME# disabled
[    0.598224] pci 0000:00:12.0: reg 10 io port: [0x9000-0x9007]
[    0.598232] pci 0000:00:12.0: reg 14 io port: [0x9008-0x900b]
[    0.598240] pci 0000:00:12.0: reg 18 io port: [0x9010-0x9017]
[    0.598248] pci 0000:00:12.0: reg 1c io port: [0x5018-0x501b]
[    0.598256] pci 0000:00:12.0: reg 20 io port: [0x5020-0x502f]
[    0.598264] pci 0000:00:12.0: reg 24 32bit mmio: [0xd0609000-0xd06093ff]
[    0.598283] pci 0000:00:12.0: set SATA to AHCI mode
[    0.598327] pci 0000:00:13.0: reg 10 32bit mmio: [0xd0601000-0xd0601fff]
[    0.598388] pci 0000:00:13.1: reg 10 32bit mmio: [0xd0602000-0xd0602fff]
[    0.598452] pci 0000:00:13.2: reg 10 32bit mmio: [0xd0603000-0xd0603fff]
[    0.598513] pci 0000:00:13.3: reg 10 32bit mmio: [0xd0604000-0xd0604fff]
[    0.598574] pci 0000:00:13.4: reg 10 32bit mmio: [0xd0605000-0xd0605fff]
[    0.598654] pci 0000:00:13.5: reg 10 32bit mmio: [0xd0606000-0xd06060ff]
[    0.598711] pci 0000:00:13.5: supports D1 D2
[    0.598713] pci 0000:00:13.5: PME# supported from D0 D1 D2 D3hot
[    0.598718] pci 0000:00:13.5: PME# disabled
[    0.598767] pci 0000:00:14.0: reg 10 io port: [0x8200-0x820f]
[    0.598842] pci 0000:00:14.1: reg 10 io port: [0x00-0x07]
[    0.598850] pci 0000:00:14.1: reg 14 io port: [0x00-0x03]
[    0.598857] pci 0000:00:14.1: reg 18 io port: [0x00-0x07]
[    0.598865] pci 0000:00:14.1: reg 1c io port: [0x00-0x03]
[    0.598873] pci 0000:00:14.1: reg 20 io port: [0x5040-0x504f]
[    0.598931] pci 0000:00:14.2: reg 10 64bit mmio: [0xd0608000-0xd060bfff]
[    0.598978] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.598983] pci 0000:00:14.2: PME# disabled
[    0.599201] pci 0000:01:05.0: reg 10 64bit mmio pref: [0xc0000000-0xc7ffffff]
[    0.599207] pci 0000:01:05.0: reg 18 64bit mmio: [0xd0400000-0xd040ffff]
[    0.599212] pci 0000:01:05.0: reg 20 io port: [0x4000-0x40ff]
[    0.599216] pci 0000:01:05.0: reg 24 32bit mmio: [0xd0500000-0xd05fffff]
[    0.599229] pci 0000:01:05.0: supports D1 D2
[    0.599250] pci 0000:00:01.0: bridge io port: [0x4000-0x4fff]
[    0.599254] pci 0000:00:01.0: bridge 32bit mmio: [0xd0400000-0xd05fffff]
[    0.599258] pci 0000:00:01.0: bridge 64bit mmio pref: [0xc0000000-0xc7ffffff]
[    0.599350] pci 0000:10:00.0: reg 10 64bit mmio: [0xd0000000-0xd000ffff]
[    0.599409] pci 0000:10:00.0: PME# supported from D3hot D3cold
[    0.599414] pci 0000:10:00.0: PME# disabled
[    0.599480] pci 0000:00:04.0: bridge 32bit mmio: [0xd0000000-0xd00fffff]
[    0.599532] pci 0000:00:05.0: bridge io port: [0x2000-0x3fff]
[    0.599535] pci 0000:00:05.0: bridge 32bit mmio: [0xcc000000-0xcfffffff]
[    0.599585] pci 0000:30:00.0: reg 10 64bit mmio: [0xc8000000-0xc8003fff]
[    0.599641] pci 0000:30:00.0: supports D1 D2
[    0.599712] pci 0000:00:06.0: bridge 32bit mmio: [0xc8000000-0xc80fffff]
[    0.599769] pci 0000:02:04.0: reg 10 32bit mmio: [0xd0100000-0xd0100fff]
[    0.599795] pci 0000:02:04.0: supports D1 D2
[    0.599797] pci 0000:02:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.599803] pci 0000:02:04.0: PME# disabled
[    0.599849] pci 0000:02:04.1: reg 10 32bit mmio: [0xd0101000-0xd01017ff]
[    0.599912] pci 0000:02:04.1: supports D1 D2
[    0.599914] pci 0000:02:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.599920] pci 0000:02:04.1: PME# disabled
[    0.600003] pci 0000:00:14.4: transparent bridge
[    0.600011] pci 0000:00:14.4: bridge 32bit mmio: [0xd0100000-0xd03fffff]
[    0.600053] ACPI: PCI Interrupt Routing Table [\_SB_.C08B._PRT]
[    0.600312] ACPI: PCI Interrupt Routing Table [\_SB_.C08B.C08C._PRT]
[    0.600392] ACPI: PCI Interrupt Routing Table [\_SB_.C08B.C0FC._PRT]
[    0.623826] ACPI: PCI Interrupt Link [C145] (IRQs 10 11) *0, disabled.
[    0.623990] ACPI: PCI Interrupt Link [C146] (IRQs 10 11) *0, disabled.
[    0.624154] ACPI: PCI Interrupt Link [C147] (IRQs 10 11) *0, disabled.
[    0.624317] ACPI: PCI Interrupt Link [C148] (IRQs 10 11) *0, disabled.
[    0.624484] ACPI: PCI Interrupt Link [C149] (IRQs 10 11) *0, disabled.
[    0.624647] ACPI: PCI Interrupt Link [C14A] (IRQs 9) *0, disabled.
[    0.624809] ACPI: PCI Interrupt Link [C14B] (IRQs 10 11) *0, disabled.
[    0.624976] ACPI: PCI Interrupt Link [C14C] (IRQs 10 11) *0, disabled.
[    0.625126] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.625132] vgaarb: loaded
[    0.625254] SCSI subsystem initialized
[    0.625319] libata version 3.00 loaded.
[    0.625319] usbcore: registered new interface driver usbfs
[    0.625319] usbcore: registered new interface driver hub
[    0.625319] usbcore: registered new device driver usb
[    0.625319] ACPI: WMI: Mapper loaded
[    0.625319] PCI: Using ACPI for IRQ routing
[    0.625319] pci 0000:00:14.2: BAR 0: address space collision on of device [0xd0608000-0xd060bfff]
[    0.625319] pci 0000:00:14.2: BAR 0: can't allocate resource
[    0.625319] NetLabel: Initializing
[    0.625319] NetLabel:  domain hash size = 128
[    0.625319] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.625319] NetLabel:  unlabeled traffic allowed by default
[    0.625319] AppArmor: AppArmor Filesystem Enabled
[    0.625319] pnp: PnP ACPI init
[    0.625319] ACPI: bus type pnp registered
[    0.638405]   alloc irq_desc for 22 on node 0
[    0.638408]   alloc kstat_irqs on node 0
[    0.640906] pnp: PnP ACPI: found 15 devices
[    0.640909] ACPI: ACPI bus type pnp unregistered
[    0.640922] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.640925] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[    0.640928] system 00:00: iomem range 0x100000-0xffffffff could not be reserved
[    0.640939] system 00:0b: ioport range 0x40b-0x40b has been reserved
[    0.640942] system 00:0b: ioport range 0x4d0-0x4d1 has been reserved
[    0.640944] system 00:0b: ioport range 0x4d6-0x4d6 has been reserved
[    0.640948] system 00:0b: ioport range 0x500-0x51f has been reserved
[    0.640951] system 00:0b: ioport range 0xc00-0xc01 has been reserved
[    0.640953] system 00:0b: ioport range 0xc14-0xc14 has been reserved
[    0.640956] system 00:0b: ioport range 0xc50-0xc51 has been reserved
[    0.640959] system 00:0b: ioport range 0xc52-0xc52 has been reserved
[    0.640962] system 00:0b: ioport range 0xc6c-0xc6c has been reserved
[    0.640970] system 00:0b: ioport range 0xc6f-0xc6f has been reserved
[    0.640973] system 00:0b: ioport range 0xcd0-0xcdf has been reserved
[    0.640976] system 00:0b: iomem range 0xffb00000-0xffbfffff could not be reserved
[    0.640980] system 00:0b: iomem range 0xfff00000-0xffffffff has been reserved
[    0.640986] system 00:0d: ioport range 0x8000-0x802f has been reserved
[    0.640989] system 00:0d: ioport range 0x8100-0x811f has been reserved
[    0.640992] system 00:0d: iomem range 0xe0000000-0xefffffff has been reserved
[    0.640995] system 00:0d: iomem range 0xfec00000-0xfec000ff could not be reserved
[    0.640999] system 00:0d: iomem range 0xfed45000-0xfed8ffff has been reserved
[    0.641004] system 00:0e: iomem range 0xcd400-0xcffff has been reserved
[    0.641007] system 00:0e: iomem range 0xd2a00-0xd2fff has been reserved
[    0.641010] system 00:0e: iomem range 0x0-0x7ffffff could not be reserved
[    0.641013] system 00:0e: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.645764] Switching to clocksource acpi_pm
[    0.645820] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.645820] pci 0000:00:01.0:   IO window: 0x4000-0x4fff
[    0.645820] pci 0000:00:01.0:   MEM window: 0xd0400000-0xd05fffff
[    0.645820] pci 0000:00:01.0:   PREFETCH window: 0x000000c0000000-0x000000c7ffffff
[    0.645820] pci 0000:00:04.0: PCI bridge, secondary bus 0000:10
[    0.645820] pci 0000:00:04.0:   IO window: disabled
[    0.645820] pci 0000:00:04.0:   MEM window: 0xd0000000-0xd00fffff
[    0.645820] pci 0000:00:04.0:   PREFETCH window: disabled
[    0.645820] pci 0000:00:05.0: PCI bridge, secondary bus 0000:20
[    0.645820] pci 0000:00:05.0:   IO window: 0x2000-0x3fff
[    0.645820] pci 0000:00:05.0:   MEM window: 0xcc000000-0xcfffffff
[    0.645820] pci 0000:00:05.0:   PREFETCH window: disabled
[    0.645820] pci 0000:00:06.0: PCI bridge, secondary bus 0000:30
[    0.645820] pci 0000:00:06.0:   IO window: disabled
[    0.645820] pci 0000:00:06.0:   MEM window: 0xc8000000-0xc80fffff
[    0.645820] pci 0000:00:06.0:   PREFETCH window: disabled
[    0.645820] pci 0000:02:04.0: CardBus bridge, secondary bus 0000:03
[    0.645820] pci 0000:02:04.0:   IO window: 0x001000-0x0010ff
[    0.645820] pci 0000:02:04.0:   IO window: 0x001400-0x0014ff
[    0.645820] pci 0000:02:04.0:   PREFETCH window: 0x80000000-0x83ffffff
[    0.645820] pci 0000:02:04.0:   MEM window: 0x88000000-0x8bffffff
[    0.645820] pci 0000:00:14.4: PCI bridge, secondary bus 0000:02
[    0.645820] pci 0000:00:14.4:   IO window: 0x1000-0x1fff
[    0.645820] pci 0000:00:14.4:   MEM window: 0xd0100000-0xd03fffff
[    0.645820] pci 0000:00:14.4:   PREFETCH window: 0x80000000-0x83ffffff
[    0.645820] pci 0000:00:04.0: setting latency timer to 64
[    0.645820] pci 0000:00:05.0: setting latency timer to 64
[    0.645820] pci 0000:00:06.0: setting latency timer to 64
[    0.645820]   alloc irq_desc for 20 on node 0
[    0.645820]   alloc kstat_irqs on node 0
[    0.645820] pci 0000:02:04.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.645820] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.645820] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.645820] pci_bus 0000:01: resource 0 io:  [0x4000-0x4fff]
[    0.645820] pci_bus 0000:01: resource 1 mem: [0xd0400000-0xd05fffff]
[    0.645820] pci_bus 0000:01: resource 2 pref mem [0xc0000000-0xc7ffffff]
[    0.645820] pci_bus 0000:10: resource 1 mem: [0xd0000000-0xd00fffff]
[    0.645820] pci_bus 0000:20: resource 0 io:  [0x2000-0x3fff]
[    0.645820] pci_bus 0000:20: resource 1 mem: [0xcc000000-0xcfffffff]
[    0.645820] pci_bus 0000:30: resource 1 mem: [0xc8000000-0xc80fffff]
[    0.645820] pci_bus 0000:02: resource 0 io:  [0x1000-0x1fff]
[    0.645820] pci_bus 0000:02: resource 1 mem: [0xd0100000-0xd03fffff]
[    0.645820] pci_bus 0000:02: resource 2 pref mem [0x80000000-0x83ffffff]
[    0.645820] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.645820] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.645820] pci_bus 0000:03: resource 0 io:  [0x1000-0x10ff]
[    0.645820] pci_bus 0000:03: resource 1 io:  [0x1400-0x14ff]
[    0.645820] pci_bus 0000:03: resource 2 pref mem [0x80000000-0x83ffffff]
[    0.645820] pci_bus 0000:03: resource 3 mem: [0x88000000-0x8bffffff]
[    0.645820] NET: Registered protocol family 2
[    0.645820] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.645820] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.645820] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.645820] TCP: Hash tables configured (established 262144 bind 65536)
[    0.645820] TCP reno registered
[    0.645820] NET: Registered protocol family 1
[    0.645820] pci 0000:01:05.0: Boot video device
[    0.645820] Scanning for low memory corruption every 60 seconds
[    0.645820] audit: initializing netlink socket (disabled)
[    0.645820] type=2000 audit(1275993759.644:1): initialized
[    0.654824] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.656674] VFS: Disk quotas dquot_6.5.2
[    0.656740] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.657575] fuse init (API version 7.13)
[    0.657679] msgmni has been set to 3761
[    0.658039] alg: No test for stdrng (krng)
[    0.658113] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.658117] io scheduler noop registered
[    0.658119] io scheduler anticipatory registered
[    0.658122] io scheduler deadline registered
[    0.658169] io scheduler cfq registered (default)
[    0.658469]   alloc irq_desc for 24 on node 0
[    0.658472]   alloc kstat_irqs on node 0
[    0.658482] pcieport 0000:00:04.0: irq 24 for MSI/MSI-X
[    0.658489] pcieport 0000:00:04.0: setting latency timer to 64
[    0.658633]   alloc irq_desc for 25 on node 0
[    0.658635]   alloc kstat_irqs on node 0
[    0.658640] pcieport 0000:00:05.0: irq 25 for MSI/MSI-X
[    0.658646] pcieport 0000:00:05.0: setting latency timer to 64
[    0.658779]   alloc irq_desc for 26 on node 0
[    0.658781]   alloc kstat_irqs on node 0
[    0.658787] pcieport 0000:00:06.0: irq 26 for MSI/MSI-X
[    0.658793] pcieport 0000:00:06.0: setting latency timer to 64
[    0.658868] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.658897] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.662945] ACPI: AC Adapter [C1EB] (on-line)
[    0.663059] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
[    0.663063] ACPI: Sleep Button [C28D]
[    0.663118] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    0.663192] ACPI: Lid Switch [C1F0]
[    0.663248] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.663251] ACPI: Power Button [PWRF]
[    0.663488] fan PNP0C0B:00: registered as cooling_device0
[    0.663495] ACPI: Fan [C39B] (off)
[    0.663669] fan PNP0C0B:01: registered as cooling_device1
[    0.663676] ACPI: Fan [C39C] (off)
[    0.663852] fan PNP0C0B:02: registered as cooling_device2
[    0.663858] ACPI: Fan [C39D] (off)
[    0.664037] fan PNP0C0B:03: registered as cooling_device3
[    0.664043] ACPI: Fan [C39E] (off)
[    0.664369] ACPI: processor limited to max C-state 1
[    0.664391] processor LNXCPU:00: registered as cooling_device4
[    0.664507] processor LNXCPU:01: registered as cooling_device5
[    0.680897] thermal LNXTHERM:01: registered as thermal_zone0
[    0.680906] ACPI: Thermal Zone [TZ1] (79 C)
[    0.681773] ACPI: Battery Slot [C1EC] (battery absent)
[    0.683262] Linux agpgart interface v0.103
[    0.683305] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.683435] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.683761] 00:02: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.684998] brd: module loaded
[    0.685540] loop: module loaded
[    0.685654] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.685980]   alloc irq_desc for 16 on node 0
[    0.685982]   alloc kstat_irqs on node 0
[    0.685989] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.686457] Fixed MDIO Bus: probed
[    0.686497] PPP generic driver version 2.4.2
[    0.686544] tun: Universal TUN/TAP device driver, 1.6
[    0.686546] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.686681] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.686746]   alloc irq_desc for 23 on node 0
[    0.686748]   alloc kstat_irqs on node 0
[    0.686753] ehci_hcd 0000:00:13.5: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.686776] ehci_hcd 0000:00:13.5: EHCI Host Controller
[    0.686851] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 1
[    0.686887] ehci_hcd 0000:00:13.5: applying AMD SB600/SB700 USB freeze workaround
[    0.686902] ehci_hcd 0000:00:13.5: debug port 1
[    0.686929] ehci_hcd 0000:00:13.5: irq 23, io mem 0xd0606000
[    0.710045] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00
[    0.710171] usb usb1: configuration #1 chosen from 1 choice
[    0.710206] hub 1-0:1.0: USB hub found
[    0.710215] hub 1-0:1.0: 10 ports detected
[    0.710311] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.710381] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.710398] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    0.710443] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    0.710470] ohci_hcd 0000:00:13.0: irq 23, io mem 0xd0601000
[    0.724636] ACPI: Battery Slot [C1ED] (battery present)
[    0.764128] usb usb2: configuration #1 chosen from 1 choice
[    0.764158] hub 2-0:1.0: USB hub found
[    0.764171] hub 2-0:1.0: 2 ports detected
[    0.764289]   alloc irq_desc for 17 on node 0
[    0.764291]   alloc kstat_irqs on node 0
[    0.764298] ohci_hcd 0000:00:13.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.764311] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    0.764352] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    0.764381] ohci_hcd 0000:00:13.1: irq 17, io mem 0xd0602000
[    0.824127] usb usb3: configuration #1 chosen from 1 choice
[    0.824153] hub 3-0:1.0: USB hub found
[    0.824166] hub 3-0:1.0: 2 ports detected
[    0.824282] ohci_hcd 0000:00:13.2: PCI INT C -> GSI 17 (level, low) -> IRQ 17
[    0.824294] ohci_hcd 0000:00:13.2: OHCI Host Controller
[    0.824340] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 4
[    0.824359] ohci_hcd 0000:00:13.2: irq 17, io mem 0xd0603000
[    0.884125] usb usb4: configuration #1 chosen from 1 choice
[    0.884153] hub 4-0:1.0: USB hub found
[    0.884166] hub 4-0:1.0: 2 ports detected
[    0.884273] ohci_hcd 0000:00:13.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.884284] ohci_hcd 0000:00:13.3: OHCI Host Controller
[    0.884324] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 5
[    0.884342] ohci_hcd 0000:00:13.3: irq 17, io mem 0xd0604000
[    0.944120] usb usb5: configuration #1 chosen from 1 choice
[    0.944152] hub 5-0:1.0: USB hub found
[    0.944165] hub 5-0:1.0: 2 ports detected
[    0.944271] ohci_hcd 0000:00:13.4: PCI INT C -> GSI 17 (level, low) -> IRQ 17
[    0.944283] ohci_hcd 0000:00:13.4: OHCI Host Controller
[    0.944320] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 6
[    0.944339] ohci_hcd 0000:00:13.4: irq 17, io mem 0xd0605000
[    1.004129] usb usb6: configuration #1 chosen from 1 choice
[    1.004159] hub 6-0:1.0: USB hub found
[    1.004172] hub 6-0:1.0: 2 ports detected
[    1.004235] uhci_hcd: USB Universal Host Controller Interface driver
[    1.004315] PNP: PS/2 Controller [PNP0303:C24A,PNP0f13:C24B] at 0x60,0x64 irq 1,12
[    1.005995] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.006782] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.006788] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.006817] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.006844] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.006869] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.006998] mice: PS/2 mouse device common for all mice
[    1.007151] rtc_cmos 00:08: RTC can wake from S4
[    1.007205] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    1.007234] rtc0: alarms up to one month, y3k, 114 bytes nvram
[    1.007386] device-mapper: uevent: version 1.0.3
[    1.007512] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.007632] device-mapper: multipath: version 1.1.0 loaded
[    1.007635] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.007893] cpuidle: using governor ladder
[    1.007895] cpuidle: using governor menu
[    1.008328] TCP cubic registered
[    1.008483] NET: Registered protocol family 10
[    1.008970] lo: Disabled Privacy Extensions
[    1.009269] NET: Registered protocol family 17
[    1.009314] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-60 processors (2 cpu cores) (version 2.20.00)
[    1.009376] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x12
[    1.009379] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x13
[    1.009381] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x14
[    1.009384] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x1e
[    1.009456] powernow-k8: ph2 null fid transition 0xc
[    1.009585] PM: Resume from disk failed.
[    1.009606] registered taskstats version 1
[    1.010029]   Magic number: 14:343:729
[    1.010069] pci_express 0000:00:04.0:pcie08: hash matches
[    1.010148] rtc_cmos 00:08: setting system clock to 2010-06-08 10:42:41 UTC (1275993761)
[    1.010151] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.010153] EDD information not available.
[    1.010234] Freeing unused kernel memory: 876k freed
[    1.010681] Write protecting the kernel read-only data: 7680k
[    1.028798] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.033961] udev: starting version 151
[    1.206499]   alloc irq_desc for 18 on node 0
[    1.206503]   alloc kstat_irqs on node 0
[    1.206514] b43-pci-bridge 0000:30:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.206523] b43-pci-bridge 0000:30:00.0: setting latency timer to 64
[    1.209328] ahci 0000:00:12.0: version 3.0
[    1.209355] ahci 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.209403] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
[    1.209485] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0x1 impl SATA mode
[    1.209490] ahci 0000:00:12.0: flags: ncq sntf ilck pm led clo pio slum part ccc 
[    1.209677] tg3.c:v3.102 (September 1, 2009)
[    1.209727] tg3 0000:10:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.209734] tg3 0000:10:00.0: setting latency timer to 64
[    1.226321] scsi0 : ahci
[    1.226512] scsi1 : ahci
[    1.226740] scsi2 : ahci
[    1.227394] scsi3 : ahci
[    1.227510] ata1: SATA max UDMA/133 abar m1024@0xd0609000 port 0xd0609100 irq 16
[    1.227513] ata2: DUMMY
[    1.227515] ata3: DUMMY
[    1.227516] ata4: DUMMY
[    1.227965] scsi4 : pata_atiixp
[    1.228099] scsi5 : pata_atiixp
[    1.228580] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x5040 irq 14
[    1.228584] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x5048 irq 15
[    1.230043]   alloc irq_desc for 21 on node 0
[    1.230046]   alloc kstat_irqs on node 0
[    1.230054] ohci1394 0000:02:04.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.262553] usb 1-6: new high speed USB device using ehci_hcd and address 4
[    1.292118] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[d0101000-d01017ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    1.320127] ssb: Sonics Silicon Backplane found on PCI device 0000:30:00.0
[    1.410532] usb 1-6: configuration #1 chosen from 1 choice
[    1.410737] hub 1-6:1.0: USB hub found
[    1.410803] hub 1-6:1.0: 4 ports detected
[    1.420585] ata5.00: ATAPI: TSSTcorpCD/DVDW TS-L632D, HH17, max MWDMA2
[    1.480513] ata5.00: configured for MWDMA2
[    1.570068] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.570554] ata1.00: ATA-8: FUJITSU MHZ2160BH G2, 8909, max UDMA/100
[    1.570557] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.570578] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[    1.571178] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[    1.571180] ata1.00: configured for UDMA/100
[    1.590151] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHZ2160B 8909 PQ: 0 ANSI: 5
[    1.590335] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.590702] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.590752] sd 0:0:0:0: [sda] Write Protect is off
[    1.590755] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.590782] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.590935]  sda:
[    1.610426] scsi 4:0:0:0: CD-ROM            TSSTcorp CD/DVDW TS-L632D HH17 PQ: 0 ANSI: 5
[    1.629342]  sda1 sda2 < sda5 sda6 >
[    1.661773] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.740085] usb 2-2: new full speed USB device using ohci_hcd and address 2
[    1.760842] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.760846] Uniform CD-ROM driver Revision: 3.20
[    1.760953] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    1.761019] sr 4:0:0:0: Attached scsi generic sg1 type 5
[    1.947188] usb 2-2: configuration #1 chosen from 1 choice
[    2.280050] usb 4-1: new full speed USB device using ohci_hcd and address 2
[    2.453310] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    2.474203] usb 4-1: configuration #1 chosen from 1 choice
[    2.550219] usb 1-6.2: new low speed USB device using ehci_hcd and address 5
[    2.610202] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f99295d2c0e]
[    2.666946] usb 1-6.2: configuration #1 chosen from 1 choice
[    3.261342] eth0: Tigon3 [partno(none) rev b002] (PCI Express) MAC address 00:25:b3:5e:a5:0b
[    3.261348] eth0: attached PHY is 5787 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    3.261351] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    3.261354] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   11.707417] Adding 979924k swap on /dev/sda5.  Priority:-1 extents:1 across:979924k 
[   11.728405] udev: starting version 151
[   11.816326] lp: driver loaded but no devices found
[   11.874439] lis3lv02d: hardware type NC6715x found.
[   11.875309] lis3lv02d: 2-byte sensor found
[   11.886172] EDAC MC: Ver: 2.1.0 Jun  3 2010
[   11.886348] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x8200, revision 0
[   11.982444] cfg80211: Calling CRDA to update world regulatory domain
[   11.988668] type=1505 audit(1275993772.472:2):  operation="profile_load" pid=593 name="/sbin/dhclient3"
[   11.988961] type=1505 audit(1275993772.472:3):  operation="profile_load" pid=593 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   11.989121] type=1505 audit(1275993772.472:4):  operation="profile_load" pid=593 name="/usr/lib/connman/scripts/dhclient-script"
[   11.997853] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   11.997982] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.086759] EDAC amd64_edac:  Ver: 3.2.0 Jun  3 2010
[   12.092760] parport_pc 00:03: reported by Plug and Play ACPI
[   12.092843] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   12.142073] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input5
[   12.142194] Registered led device: hp::hddprotect
[   12.142222] lis3lv02d driver loaded.
[   12.142403] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).
[   12.142414] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   12.142415]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   12.142417]  (Note that use of the override may cause unknown side effects.)
[   12.142450] amd64_edac: probe of 0000:00:18.2 failed with error -22
[   12.146596] Bluetooth: Core ver 2.15
[   12.155648] NET: Registered protocol family 31
[   12.155651] Bluetooth: HCI device and connection manager initialized
[   12.155655] Bluetooth: HCI socket layer initialized
[   12.157532] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   12.157673] usbcore: registered new interface driver btusb
[   12.172801] lp0: using parport0 (interrupt-driven).
[   12.173393] tpm_inf_pnp 00:04: Found C232 with ID IFX0102
[   12.173445] tpm_inf_pnp 00:04: TPM found: config base 0x520, data base 0x530, chip version 0x000b, vendor id 0x15d1 (Infineon), product id 0x000b (SLB 9635 TT 1.2)
[   12.289598] cfg80211: World regulatory domain updated:
[   12.289603] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   12.289606] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.289609] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.289612] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.289614] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.289617] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.312116] ppdev: user-space parallel port driver
[   12.315910] acpi device:01: registered as cooling_device6
[   12.316822] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:00/LNXVIDEO:00/input/input6
[   12.316960] ACPI: Video Device [C08D] (multi-head: yes  rom: no  post: no)
[   12.344128] [drm] Initialized drm 1.1.0 20060810
[   12.371148] yenta_cardbus 0000:02:04.0: CardBus bridge found [103c:30c2]
[   12.411913] [drm] radeon defaulting to kernel modesetting.
[   12.411917] [drm] radeon kernel modesetting enabled.
[   12.412052]   alloc irq_desc for 19 on node 0
[   12.412055]   alloc kstat_irqs on node 0
[   12.412064] radeon 0000:01:05.0: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   12.415076] [drm] radeon: Initializing kernel modesetting.
[   12.415172] [drm] register mmio base: 0xD0400000
[   12.415174] [drm] register mmio size: 65536
[   12.415262] ATOM BIOS: ATI
[   12.415484] [drm] GPU reset succeed (RBBM_STATUS=0x10000140)
[   12.415498] [drm] radeon: VRAM 128M
[   12.415500] [drm] radeon: VRAM from 0x78000000 to 0x7FFFFFFF
[   12.415502] [drm] radeon: GTT 512M
[   12.415504] [drm] radeon: GTT from 0x80000000 to 0x9FFFFFFF
[   12.415541]   alloc irq_desc for 27 on node 0
[   12.415544]   alloc kstat_irqs on node 0
[   12.415554] radeon 0000:01:05.0: irq 27 for MSI/MSI-X
[   12.415558] [drm] radeon: using MSI.
[   12.415582] [drm] radeon: irq initialized.
[   12.415787] [drm] Detected VRAM RAM=128M, BAR=128M
[   12.415793] [drm] RAM width 128bits DDR
[   12.415902] [TTM] Zone  kernel: Available graphics memory: 963364 kiB.
[   12.415924] [drm] radeon: 128M of VRAM memory ready
[   12.415926] [drm] radeon: 512M of GTT memory ready.
[   12.415949] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   12.420188] [drm] radeon: 1 quad pipes, 1 z pipes initialized.
[   12.420211] [drm] radeon: cp idle (0x10000C03)
[   12.420333] [drm] Loading RS690/RS740 Microcode
[   12.420684] platform radeon_cp.0: firmware: requesting radeon/RS690_cp.bin
[   12.423260] [drm] radeon: ring at 0x0000000080000000
[   12.423281] [drm] ring test succeeded in 1 usecs
[   12.423448] [drm] radeon: ib pool ready.
[   12.423528] [drm] ib test succeeded in 0 usecs
[   12.423684] [drm] Default TV standard: NTSC
[   12.423712] [drm] Radeon Display Connectors
[   12.423714] [drm] Connector 0:
[   12.423715] [drm]   VGA
[   12.423718] [drm]   DDC: 0x7e50 0x7e40 0x7e54 0x7e44 0x7e58 0x7e48 0x7e5c 0x7e4c
[   12.423720] [drm]   Encoders:
[   12.423722] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   12.423724] [drm] Connector 1:
[   12.423725] [drm]   LVDS
[   12.423728] [drm]   DDC: 0x7e40 0x7e50 0x7e44 0x7e54 0x7e48 0x7e58 0x7e4c 0x7e5c
[   12.423729] [drm]   Encoders:
[   12.423731] [drm]     LCD1: INTERNAL_LVTM1
[   12.423733] [drm] Connector 2:
[   12.423734] [drm]   S-video
[   12.423735] [drm]   Encoders:
[   12.423737] [drm]     TV1: INTERNAL_KLDSCP_DAC1
[   12.433188] b43-phy0: Broadcom 4311 WLAN found (core revision 13)
[   12.433285] usbcore: registered new interface driver hiddev
[   12.436824] input: Microsoft Basic Optical Mouse as /devices/pci0000:00/0000:00:13.5/usb1/1-6/1-6.2/1-6.2:1.0/input/input7
[   12.436958] generic-usb 0003:045E:0084.0001: input,hidraw0: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0000:00:13.5-6.2/input0
[   12.436992] usbcore: registered new interface driver usbhid
[   12.436996] usbhid: v2.6:USB HID core driver
[   12.520746] yenta_cardbus 0000:02:04.0: ISA IRQ mask 0x0c38, PCI irq 20
[   12.520752] yenta_cardbus 0000:02:04.0: Socket status: 30000006
[   12.520756] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #03 to #06
[   12.520766] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge I/O window: 0x1000 - 0x1fff
[   12.520770] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge Memory window: 0xd0100000 - 0xd03fffff
[   12.520774] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge Memory window: 0x80000000 - 0x83ffffff
[   12.544974] HDA Intel 0000:00:14.2: power state changed by ACPI to D0
[   12.544991] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.651420] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x2580b1, caps: 0xa04793/0x300000
[   12.651426] serio: Synaptics pass-through port at isa0060/serio4/input0
[   12.688483] phy0: Selected rate control algorithm 'minstrel'
[   12.689276] Registered led device: b43-phy0::tx
[   12.689298] Registered led device: b43-phy0::rx
[   12.689318] Registered led device: b43-phy0::radio
[   12.689403] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
[   12.692241] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
[   12.738525] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input9
[   13.155839] [drm] fb mappable at 0xC0040000
[   13.155843] [drm] vram apper at 0xC0000000
[   13.155845] [drm] size 7257600
[   13.155846] [drm] fb depth is 24
[   13.155848] [drm]    pitch is 6912
[   13.156082] fb0: radeondrmfb frame buffer device
[   13.156084] registered panic notifier
[   13.156090] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:05.0 on minor 0
[   13.158308] vga16fb: initializing
[   13.158314] vga16fb: mapped to 0xffff8800000a0000
[   13.158321] vga16fb: not registering due to another framebuffer present
[   13.543387] Console: switching to colour frame buffer device 210x65
[   14.006497] EXT4-fs (sda6): mounted filesystem with ordered data mode
[   14.516897] type=1505 audit(1275993774.999:5):  operation="profile_load" pid=952 name="/usr/share/gdm/guest-session/Xsession"
[   14.519644] type=1505 audit(1275993774.999:6):  operation="profile_replace" pid=953 name="/sbin/dhclient3"
[   14.519950] type=1505 audit(1275993774.999:7):  operation="profile_replace" pid=953 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   14.520206] type=1505 audit(1275993775.009:8):  operation="profile_replace" pid=953 name="/usr/lib/connman/scripts/dhclient-script"
[   14.524853] type=1505 audit(1275993775.009:9):  operation="profile_load" pid=955 name="/usr/bin/evince"
[   14.529133] type=1505 audit(1275993775.009:10):  operation="profile_load" pid=955 name="/usr/bin/evince-previewer"
[   14.531843] type=1505 audit(1275993775.019:11):  operation="profile_load" pid=955 name="/usr/bin/evince-thumbnailer"
[   14.627244]   alloc irq_desc for 28 on node 0
[   14.627249]   alloc kstat_irqs on node 0
[   14.627303] tg3 0000:10:00.0: irq 28 for MSI/MSI-X
[   14.656877] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.762773] Bluetooth: L2CAP ver 2.14
[   14.762778] Bluetooth: L2CAP socket layer initialized
[   14.772813] b43 ssb0:0: firmware: requesting b43/ucode13.fw
[   14.774006] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   14.774010] Bluetooth: BNEP filters: protocol multicast
[   14.786782] Bridge firewalling registered
[   14.923712] b43 ssb0:0: firmware: requesting b43/b0g0initvals13.fw
[   15.092580] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   15.280594] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.307054] Bluetooth: SCO (Voice Link) ver 0.6
[   15.307058] Bluetooth: SCO socket layer initialized
[   15.390281] Bluetooth: RFCOMM TTY layer initialized
[   15.390288] Bluetooth: RFCOMM socket layer initialized
[   15.390290] Bluetooth: RFCOMM ver 1.11
[   17.781626] tg3: eth0: Link is up at 1000 Mbps, full duplex.
[   17.781631] tg3: eth0: Flow control is off for TX and off for RX.
[   17.782052] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   27.972525] eth0: no IPv6 routers present
[   29.050337] wlan0: deauthenticating from 00:01:e6:ff:f4:c9 by local choice (reason=3)
[   29.050454] wlan0: direct probe to AP 00:01:e6:ff:f4:c9 (try 1)
[   29.053449] wlan0: direct probe responded
[   29.053456] wlan0: authenticate with AP 00:01:e6:ff:f4:c9 (try 1)
[   29.056061] wlan0: authenticated
[   29.056094] wlan0: associate with AP 00:01:e6:ff:f4:c9 (try 1)
[   29.059740] wlan0: RX AssocResp from 00:01:e6:ff:f4:c9 (capab=0x411 status=0 aid=9)
[   29.059743] wlan0: associated
[   29.060816] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   29.060910] cfg80211: Calling CRDA for country: GB
[   29.064309] cfg80211: Received country IE:
[   29.064314] cfg80211: Regulatory domain: GB
[   29.064316] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   29.064319] 	(2402000 KHz - 2494000 KHz @ 40000 KHz), (10000 mBi, 10000 mBm)
[   29.064322] cfg80211: CRDA thinks this should applied:
[   29.064323] cfg80211: Regulatory domain: GB
[   29.064325] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   29.064327] 	(2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   29.064329] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   29.064332] 	(5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   29.064334] 	(5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[   29.064336] cfg80211: We intersect both of these and get:
[   29.064338] cfg80211: Regulatory domain: 98
[   29.064339] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   29.064342] 	(2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   29.064348] cfg80211: Disabling channel 2484 MHz on phy0 due to Country IE
[   29.064351] cfg80211: Current regulatory domain updated by AP to: GB
[   29.064353] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   29.064356] 	(2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   39.090052] wlan0: deauthenticating from 00:01:e6:ff:f4:c9 by local choice (reason=3)
[   39.300648] wlan0: deauthenticating from 00:01:e6:ff:f4:c9 by local choice (reason=3)
[   39.490170] wlan0: direct probe to AP 00:01:e6:ff:f4:c9 (try 1)
[   39.492880] wlan0: direct probe responded
[   39.492889] wlan0: authenticate with AP 00:01:e6:ff:f4:c9 (try 1)
[   39.496289] wlan0: authenticated
[   39.496326] wlan0: associate with AP 00:01:e6:ff:f4:c9 (try 1)
[   39.500967] wlan0: RX AssocResp from 00:01:e6:ff:f4:c9 (capab=0x411 status=0 aid=9)
[   39.500970] wlan0: associated
[   39.720027] wlan0: no IPv6 routers present
[   77.810063] Clocksource tsc unstable (delta = -161226812 ns)
[   87.540160] wlan0: deauthenticating from 00:01:e6:ff:f4:c9 by local choice (reason=3)
[   97.610331] wlan0: deauthenticating from 00:01:e6:ff:f4:c9 by local choice (reason=3)
[   97.800198] wlan0: direct probe to AP 00:0d:9d:f6:53:af (try 1)
[   97.802628] wlan0: direct probe responded
[   97.802644] wlan0: authenticate with AP 00:0d:9d:f6:53:af (try 1)
[   97.805005] wlan0: authenticated
[   97.805072] wlan0: associate with AP 00:0d:9d:f6:53:af (try 1)
[   97.808368] wlan0: RX AssocResp from 00:0d:9d:f6:53:af (capab=0x11 status=0 aid=9)
[   97.808375] wlan0: associated
[  380.706513] __ratelimit: 9 callbacks suppressed
[  380.706520] npviewer.bin[2047]: segfault at ff999ea8 ip 00000000ff999ea8 sp 00000000ffaf785c error 14[/PHP]

---

### Post by easydiver on 2010-06-09
I have a related issue:
 
I'm running 10.04 64 bit Ubuntu in VMWare workstation, the image is from thoughtpolice.
 
Installing jre1.6.0_16 gives:
ERROR: The 64 bit JRE cannot be installed on a 32 bit Linux.
 
"uname - a" gives:
 
Linux <hostname> 2.6.32.21-server #32-Ubuntu SMP <date/time> x86_64 GNU/Linux
 
Any sugestions are welcome !
 
---- found the problem uname -i gives "unknown" apparrently a bug in uname... I changed the install script to bypass system checks... this is also a bug in a fresh 10.04 install form the official ubuntu image.

---

### Post by Beebock on 2010-06-10
Linux xy01l731 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux


Same here. 

Does anyone have any idea? Tis rather irritating that I can't use the 64bit ability of my CPUs...

---

### Post by Beebock on 2010-06-12
bump.... anyone?

---

