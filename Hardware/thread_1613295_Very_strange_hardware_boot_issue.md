---
title: "Very strange hardware boot issue"
date: 2010-11-04
forum: Hardware
---

### Post by jonamerica on 2010-11-04
I'm running Ubuntu 10.10 as a DVR (MythTV). To save on electric bills I have the computer shutdown between recordings and automatically boot 10 minutes before a show.

If the TV is off when the computer boots, neither the TV or the wireless network adapter will work. It will boot and record TV shows just fine, but I have to manually reboot the machine and let it reboot with the TV on to be able to see anything or connect to the computer remotely.

I have two dmesg files, one from a good boot (when TV was on) and one from a bad boot (TV off), and have been looking for differences (there are many), but I don't know enough to figure out what's wrong.

```
Everything working
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-25-generic (buildd@allspice) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #45-Ubuntu SMP Sat Oct 16 19:52:42 UTC 2010 (Ubuntu 2.6.32-25.45-generic 2.6.32.21+drm33.7)
[    0.000000] Command line: root=/dev/md0 ro ro quiet splash rootflags=data=writeback 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
[    0.000000]  BIOS-e820: 000000003fff0000 - 000000003fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fff3000 - 0000000040000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x3fff0 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FFC0000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003fff0000 (usable)
[    0.000000]  modified: 000000003fff0000 - 000000003fff3000 (ACPI NVS)
[    0.000000]  modified: 000000003fff3000 - 0000000040000000 (ACPI data)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-000000003fff0000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 003fe00000 page 2M
[    0.000000]  003fe00000 - 003fff0000 page 4k
[    0.000000] kernel direct mapping tables up to 3fff0000 @ 10000-13000
[    0.000000] RAMDISK: 377bb000 - 37fefc1b
[    0.000000] ACPI: RSDP 00000000000f7880 00014 (v00 Nvidia)
[    0.000000] ACPI: RSDT 000000003fff3040 00034 (v01 Nvidia AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: FACP 000000003fff30c0 00074 (v01 Nvidia AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: DSDT 000000003fff3180 06360 (v01 NVIDIA AWRDACPI 00001000 MSFT 0100000E)
[    0.000000] ACPI: FACS 000000003fff0000 00040
[    0.000000] ACPI: SRAT 000000003fff9600 00090 (v01 AMD    HAMMER   00000001 AMD  00000001)
[    0.000000] ACPI: MCFG 000000003fff9700 0003C (v01 Nvidia AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: APIC 000000003fff9540 0007C (v01 Nvidia AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] SRAT: PXM 0 -> APIC 0 -> Node 0
[    0.000000] SRAT: Node 0 PXM 0 0-a0000
[    0.000000] SRAT: Node 0 PXM 0 100000-40000000
[    0.000000] NUMA: Allocated memnodemap from 11000 - 11840
[    0.000000] NUMA: Using 20 for the hash shift.
[    0.000000] Bootmem setup node 0 0000000000000000-000000003fff0000
[    0.000000]   NODE_DATA [0000000000011840 - 000000000001683f]
[    0.000000]   bootmap [0000000000017000 -  000000000001efff] pages 8
[    0.000000] (8 early reservations) ==> bootmem [0000000000 - 003fff0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 0001a2ca64]    TEXT DATA BSS ==> [0001000000 - 0001a2ca64]
[    0.000000]   #3 [00377bb000 - 0037fefc1b]          RAMDISK ==> [00377bb000 - 0037fefc1b]
[    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #5 [0001a2d000 - 0001a2d14d]              BRK ==> [0001a2d000 - 0001a2d14d]
[    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #7 [0000011000 - 0000011840]       MEMNODEMAP ==> [0000011000 - 0000011840]
[    0.000000] found SMP MP-table at [ffff8800000f5500] f5500
[    0.000000]  [ffffea0000000000-ffffea0000dfffff] PMD -> [ffff880002000000-ffff880002dfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003fff0
[    0.000000] On node 0 totalpages: 262015
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 100 pages reserved
[    0.000000]   DMA zone: 3827 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 3528 pages used for memmap
[    0.000000]   DMA32 zone: 254504 pages, LIFO batch:31
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:a0000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001c00000 s91544 r8192 d23144 u1048576
[    0.000000] pcpu-alloc: s91544 r8192 d23144 u1048576 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 258331
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=/dev/md0 ro ro quiet splash rootflags=data=writeback 
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ 33fe000000 size 32 MB
[    0.000000] Aperture beyond 4GB. Ignoring.
[    0.000000] Memory: 1014516k/1048512k available (5420k kernel code, 452k absent, 33544k reserved, 2974k data, 872k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:4352 nr_irqs:424
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 10485760 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2216.540 MHz processor.
[    0.010005] Calibrating delay loop (skipped), value calculated using timer frequency.. 4433.08 BogoMIPS (lpj=22165400)
[    0.010033] Security Framework initialized
[    0.010054] AppArmor: AppArmor initialized
[    0.010173] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.020109] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.020423] Mount-cache hash table entries: 256
[    0.020569] Initializing cgroup subsys ns
[    0.020573] Initializing cgroup subsys cpuacct
[    0.020577] Initializing cgroup subsys memory
[    0.020587] Initializing cgroup subsys devices
[    0.020590] Initializing cgroup subsys freezer
[    0.020592] Initializing cgroup subsys net_cls
[    0.020611] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.020613] CPU: L2 Cache: 512K (64 bytes/line)
[    0.020616] CPU 0/0x0 -> Node 0
[    0.020618] tseg: 0000000000
[    0.020635] mce: CPU supports 5 MCE banks
[    0.020647] Performance Events: AMD PMU driver.
[    0.020652] ... version:                0
[    0.020654] ... bit width:              48
[    0.020655] ... generic registers:      4
[    0.020657] ... value mask:             0000ffffffffffff
[    0.020659] ... max period:             00007fffffffffff
[    0.020661] ... fixed-purpose events:   0
[    0.020662] ... event mask:             000000000000000f
[    0.020675] SMP alternatives: switching to UP code
[    0.029738] ACPI: Core revision 20090903
[    0.038976] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.038982] ftrace: allocating 22538 entries in 89 pages
[    0.040092] Setting APIC routing to flat
[    0.040397] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.144763] CPU0: AMD Athlon(tm) 64 Processor 3500+ stepping 02
[    0.150000] Brought up 1 CPUs
[    0.150000] Total of 1 processors activated (4433.08 BogoMIPS).
[    0.150000] CPU0 attaching NULL sched-domain.
[    0.150000] devtmpfs: initialized
[    0.150000] regulator: core version 0.5
[    0.150000] Time: 12:11:40  Date: 11/04/10
[    0.150000] NET: Registered protocol family 16
[    0.150000] node 0 link 0: io port [1000, fffff]
[    0.150000] TOM: 0000000040000000 aka 1024M
[    0.150000] node 0 link 0: mmio [e0000000, efffffff]
[    0.150000] node 0 link 0: mmio [feb00000, fec0ffff]
[    0.150000] node 0 link 0: mmio [a0000, bffff]
[    0.150000] node 0 link 0: mmio [40000000, fed3ffff]
[    0.150000] bus: [00,ff] on node 0 link 0
[    0.150000] bus: 00 index 0 io port: [0, ffff]
[    0.150000] bus: 00 index 1 mmio: [40000000, fcffffffff]
[    0.150000] bus: 00 index 2 mmio: [feb00000, fec0ffff]
[    0.150000] bus: 00 index 3 mmio: [a0000, bffff]
[    0.150000] ACPI: bus type pci registered
[    0.150000] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.150000] PCI: MCFG area at e0000000 reserved in E820
[    0.150000] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.150000] PCI: Using configuration type 1 for base access
[    0.150000] bio: create slab <bio-0> at 0
[    0.150000] ACPI: EC: Look up EC in DSDT
[    0.154744] ACPI: Interpreter enabled
[    0.154747] ACPI: (supports S0 S1 S3 S4 S5)
[    0.154771] ACPI: Using IOAPIC for interrupt routing
[    0.162495] ACPI: No dock devices found.
[    0.162591] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.162693] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.162711] pci 0000:00:01.1: reg 10 io port: [0xe400-0xe41f]
[    0.162719] pci 0000:00:01.1: reg 20 io port: [0x4c00-0x4c3f]
[    0.162723] pci 0000:00:01.1: reg 24 io port: [0x4c40-0x4c7f]
[    0.162732] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.162735] pci 0000:00:01.1: PME# disabled
[    0.162755] pci 0000:00:02.0: reg 10 32bit mmio: [0xdc004000-0xdc004fff]
[    0.162771] pci 0000:00:02.0: supports D1 D2
[    0.162773] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.162775] pci 0000:00:02.0: PME# disabled
[    0.162793] pci 0000:00:02.1: reg 10 32bit mmio: [0xfeb00000-0xfeb000ff]
[    0.162812] pci 0000:00:02.1: supports D1 D2
[    0.162814] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.162817] pci 0000:00:02.1: PME# disabled
[    0.162838] pci 0000:00:04.0: reg 10 io port: [0xdc00-0xdcff]
[    0.162842] pci 0000:00:04.0: reg 14 io port: [0xe000-0xe0ff]
[    0.162846] pci 0000:00:04.0: reg 18 32bit mmio: [0xdc003000-0xdc003fff]
[    0.162859] pci 0000:00:04.0: supports D1 D2
[    0.162879] pci 0000:00:06.0: reg 20 io port: [0xf000-0xf00f]
[    0.162902] pci 0000:00:07.0: reg 10 io port: [0x9f0-0x9f7]
[    0.162905] pci 0000:00:07.0: reg 14 io port: [0xbf0-0xbf3]
[    0.162909] pci 0000:00:07.0: reg 18 io port: [0x970-0x977]
[    0.162912] pci 0000:00:07.0: reg 1c io port: [0xb70-0xb73]
[    0.162916] pci 0000:00:07.0: reg 20 io port: [0xd800-0xd80f]
[    0.162919] pci 0000:00:07.0: reg 24 32bit mmio: [0xdc002000-0xdc002fff]
[    0.162941] pci 0000:00:08.0: reg 10 io port: [0x9e0-0x9e7]
[    0.162944] pci 0000:00:08.0: reg 14 io port: [0xbe0-0xbe3]
[    0.162948] pci 0000:00:08.0: reg 18 io port: [0x960-0x967]
[    0.162951] pci 0000:00:08.0: reg 1c io port: [0xb60-0xb63]
[    0.162955] pci 0000:00:08.0: reg 20 io port: [0xc400-0xc40f]
[    0.162959] pci 0000:00:08.0: reg 24 32bit mmio: [0xdc001000-0xdc001fff]
[    0.162993] pci 0000:00:0a.0: reg 10 32bit mmio: [0xdc000000-0xdc000fff]
[    0.162997] pci 0000:00:0a.0: reg 14 io port: [0xb000-0xb007]
[    0.163011] pci 0000:00:0a.0: supports D1 D2
[    0.163013] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.163016] pci 0000:00:0a.0: PME# disabled
[    0.163045] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.163048] pci 0000:00:0b.0: PME# disabled
[    0.163079] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.163081] pci 0000:00:0c.0: PME# disabled
[    0.163111] pci 0000:00:0d.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.163114] pci 0000:00:0d.0: PME# disabled
[    0.163143] pci 0000:00:0e.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.163146] pci 0000:00:0e.0: PME# disabled
[    0.163248] pci 0000:05:06.0: reg 10 32bit mmio: [0xd3000000-0xd3ffffff]
[    0.163294] pci 0000:05:06.1: reg 10 32bit mmio: [0xd4000000-0xd4ffffff]
[    0.163337] pci 0000:05:06.2: reg 10 32bit mmio: [0xd5000000-0xd5ffffff]
[    0.163381] pci 0000:05:06.4: reg 10 32bit mmio: [0xd6000000-0xd6ffffff]
[    0.163430] pci 0000:05:07.0: reg 10 32bit mmio: [0xd7000000-0xd7ffffff]
[    0.163476] pci 0000:05:07.1: reg 10 32bit mmio: [0xd8000000-0xd8ffffff]
[    0.163519] pci 0000:05:07.2: reg 10 32bit mmio: [0xd9000000-0xd9ffffff]
[    0.163564] pci 0000:05:07.4: reg 10 32bit mmio: [0xda000000-0xdaffffff]
[    0.163613] pci 0000:05:0b.0: reg 10 32bit mmio: [0xdb004000-0xdb0047ff]
[    0.163618] pci 0000:05:0b.0: reg 14 32bit mmio: [0xdb000000-0xdb003fff]
[    0.163644] pci 0000:05:0b.0: supports D1 D2
[    0.163646] pci 0000:05:0b.0: PME# supported from D0 D1 D2 D3hot
[    0.163649] pci 0000:05:0b.0: PME# disabled
[    0.163668] pci 0000:00:09.0: transparent bridge
[    0.163672] pci 0000:00:09.0: bridge 32bit mmio: [0xd3000000-0xdbffffff]
[    0.163780] pci 0000:01:00.0: reg 10 32bit mmio: [0xd0000000-0xd0ffffff]
[    0.163787] pci 0000:01:00.0: reg 14 64bit mmio pref: [0xc0000000-0xcfffffff]
[    0.163793] pci 0000:01:00.0: reg 1c 64bit mmio: [0xd1000000-0xd1ffffff]
[    0.163800] pci 0000:01:00.0: reg 30 32bit mmio pref: [0xd2000000-0xd201ffff]
[    0.163845] pci 0000:00:0e.0: bridge 32bit mmio: [0xd0000000-0xd2ffffff]
[    0.163849] pci 0000:00:0e.0: bridge 64bit mmio pref: [0xc0000000-0xcfffffff]
[    0.163862] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.164087] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.228378] ACPI: PCI Interrupt Link [LNK1] (IRQs *3 4 5 7 9 10 11 12 14 15)
[    0.228513] ACPI: PCI Interrupt Link [LNK2] (IRQs *3 4 5 7 9 10 11 12 14 15)
[    0.228646] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[    0.228778] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.228911] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.229044] ACPI: PCI Interrupt Link [LUBA] (IRQs *3 4 5 7 9 10 11 12 14 15)
[    0.229185] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.229319] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[    0.229452] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 7 9 10 11 *12 14 15)
[    0.229584] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.229719] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 5 7 9 10 11 *12 14 15)
[    0.229855] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.230011] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.230154] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.230299] ACPI: PCI Interrupt Link [LFID] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[    0.230442] ACPI: PCI Interrupt Link [LPCA] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.230597] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0
[    0.230746] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0
[    0.230895] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
[    0.231044] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[    0.231138] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
[    0.231296] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[    0.231453] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[    0.231611] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[    0.231767] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0
[    0.231924] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[    0.232082] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[    0.232239] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[    0.232396] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[    0.232562] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[    0.232727] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
[    0.232897] ACPI: PCI Interrupt Link [APCP] (IRQs 20 21 22 23) *0, disabled.
[    0.233017] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.233019] vgaarb: loaded
[    0.233125] SCSI subsystem initialized
[    0.233203] libata version 3.00 loaded.
[    0.233267] usbcore: registered new interface driver usbfs
[    0.233278] usbcore: registered new interface driver hub
[    0.233299] usbcore: registered new device driver usb
[    0.233408] ACPI: WMI: Mapper loaded
[    0.233410] PCI: Using ACPI for IRQ routing
[    0.233551] NetLabel: Initializing
[    0.233552] NetLabel:  domain hash size = 128
[    0.233554] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.233566] NetLabel:  unlabeled traffic allowed by default
[    0.235145] AppArmor: AppArmor Filesystem Enabled
[    0.235165] pnp: PnP ACPI init
[    0.235186] ACPI: bus type pnp registered
[    0.239948] pnp: PnP ACPI: found 13 devices
[    0.239950] ACPI: ACPI bus type pnp unregistered
[    0.239962] system 00:01: ioport range 0x4000-0x407f has been reserved
[    0.239964] system 00:01: ioport range 0x4080-0x40ff has been reserved
[    0.239967] system 00:01: ioport range 0x4400-0x447f has been reserved
[    0.239970] system 00:01: ioport range 0x4480-0x44ff has been reserved
[    0.239973] system 00:01: ioport range 0x4800-0x487f has been reserved
[    0.239975] system 00:01: ioport range 0x4880-0x48ff has been reserved
[    0.240023] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.240026] system 00:02: ioport range 0x800-0x87f has been reserved
[    0.240029] system 00:02: ioport range 0x290-0x297 has been reserved
[    0.240036] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
[    0.240041] system 00:0c: iomem range 0xf0000-0xf3fff could not be reserved
[    0.240044] system 00:0c: iomem range 0xf4000-0xf7fff could not be reserved
[    0.240047] system 00:0c: iomem range 0xf8000-0xfbfff could not be reserved
[    0.240050] system 00:0c: iomem range 0xfc000-0xfffff could not be reserved
[    0.240053] system 00:0c: iomem range 0x3fff0000-0x3fffffff could not be reserved
[    0.240056] system 00:0c: iomem range 0xffff0000-0xffffffff has been reserved
[    0.240059] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    0.240062] system 00:0c: iomem range 0x100000-0x3ffeffff could not be reserved
[    0.240065] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.240067] system 00:0c: iomem range 0xfee00000-0xfeefffff has been reserved
[    0.240070] system 00:0c: iomem range 0xfefff000-0xfeffffff has been reserved
[    0.240073] system 00:0c: iomem range 0xfff80000-0xfff80fff has been reserved
[    0.240076] system 00:0c: iomem range 0xfff90000-0xfffbffff has been reserved
[    0.240079] system 00:0c: iomem range 0xfffed000-0xfffeffff has been reserved
[    0.244755] Switching to clocksource acpi_pm
[    0.244874] pci 0000:00:09.0: PCI bridge, secondary bus 0000:05
[    0.244876] pci 0000:00:09.0:   IO window: disabled
[    0.244879] pci 0000:00:09.0:   MEM window: 0xd3000000-0xdbffffff
[    0.244881] pci 0000:00:09.0:   PREFETCH window: disabled
[    0.244885] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:04
[    0.244886] pci 0000:00:0b.0:   IO window: disabled
[    0.244889] pci 0000:00:0b.0:   MEM window: disabled
[    0.244891] pci 0000:00:0b.0:   PREFETCH window: disabled
[    0.244895] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:03
[    0.244896] pci 0000:00:0c.0:   IO window: disabled
[    0.244899] pci 0000:00:0c.0:   MEM window: disabled
[    0.244901] pci 0000:00:0c.0:   PREFETCH window: disabled
[    0.244904] pci 0000:00:0d.0: PCI bridge, secondary bus 0000:02
[    0.244906] pci 0000:00:0d.0:   IO window: disabled
[    0.244909] pci 0000:00:0d.0:   MEM window: disabled
[    0.244911] pci 0000:00:0d.0:   PREFETCH window: disabled
[    0.244914] pci 0000:00:0e.0: PCI bridge, secondary bus 0000:01
[    0.244916] pci 0000:00:0e.0:   IO window: disabled
[    0.244919] pci 0000:00:0e.0:   MEM window: 0xd0000000-0xd2ffffff
[    0.244922] pci 0000:00:0e.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff
[    0.244931] pci 0000:00:09.0: setting latency timer to 64
[    0.244936] pci 0000:00:0b.0: setting latency timer to 64
[    0.244941] pci 0000:00:0c.0: setting latency timer to 64
[    0.244945] pci 0000:00:0d.0: setting latency timer to 64
[    0.244950] pci 0000:00:0e.0: setting latency timer to 64
[    0.244954] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.244956] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.244959] pci_bus 0000:05: resource 1 mem: [0xd3000000-0xdbffffff]
[    0.244962] pci_bus 0000:05: resource 3 io:  [0x00-0xffff]
[    0.244964] pci_bus 0000:05: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.244967] pci_bus 0000:01: resource 1 mem: [0xd0000000-0xd2ffffff]
[    0.244970] pci_bus 0000:01: resource 2 pref mem [0xc0000000-0xcfffffff]
[    0.245005] NET: Registered protocol family 2
[    0.245110] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.245658] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[    0.246947] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.247574] TCP: Hash tables configured (established 131072 bind 65536)
[    0.247577] TCP reno registered
[    0.247680] NET: Registered protocol family 1
[    0.260076] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.260082] pci 0000:00:0b.0: Found disabled HT MSI Mapping
[    0.260088] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.260092] pci 0000:00:0b.0: Linking AER extended capability
[    0.260126] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.260131] pci 0000:00:0c.0: Found disabled HT MSI Mapping
[    0.260138] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.260140] pci 0000:00:0c.0: Linking AER extended capability
[    0.260177] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.260182] pci 0000:00:0d.0: Found disabled HT MSI Mapping
[    0.260189] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.260191] pci 0000:00:0d.0: Linking AER extended capability
[    0.260232] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.260237] pci 0000:00:0e.0: Found disabled HT MSI Mapping
[    0.260243] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.260246] pci 0000:00:0e.0: Linking AER extended capability
[    0.260271] pci 0000:01:00.0: Boot video device
[    0.260486] Trying to unpack rootfs image as initramfs...
[    0.300477] Scanning for low memory corruption every 60 seconds
[    0.300608] audit: initializing netlink socket (disabled)
[    0.300621] type=2000 audit(1288872700.300:1): initialized
[    0.320272] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.321597] VFS: Disk quotas dquot_6.5.2
[    0.321650] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.322244] fuse init (API version 7.13)
[    0.322319] msgmni has been set to 1981
[    0.322526] alg: No test for stdrng (krng)
[    0.322578] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.322581] io scheduler noop registered
[    0.322583] io scheduler anticipatory registered
[    0.322585] io scheduler deadline registered
[    0.322628] io scheduler cfq registered (default)
[    0.330152]   alloc irq_desc for 24 on node 0
[    0.330156]   alloc kstat_irqs on node 0
[    0.330166] pcieport 0000:00:0b.0: irq 24 for MSI/MSI-X
[    0.330171] pcieport 0000:00:0b.0: setting latency timer to 64
[    0.330322]   alloc irq_desc for 25 on node 0
[    0.330324]   alloc kstat_irqs on node 0
[    0.330328] pcieport 0000:00:0c.0: irq 25 for MSI/MSI-X
[    0.330332] pcieport 0000:00:0c.0: setting latency timer to 64
[    0.330415]   alloc irq_desc for 26 on node 0
[    0.330417]   alloc kstat_irqs on node 0
[    0.330421] pcieport 0000:00:0d.0: irq 26 for MSI/MSI-X
[    0.330425] pcieport 0000:00:0d.0: setting latency timer to 64
[    0.330508]   alloc irq_desc for 27 on node 0
[    0.330510]   alloc kstat_irqs on node 0
[    0.330514] pcieport 0000:00:0e.0: irq 27 for MSI/MSI-X
[    0.330518] pcieport 0000:00:0e.0: setting latency timer to 64
[    0.330582] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.330605] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.330707] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.330710] ACPI: Power Button [PWRB]
[    0.330766] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.330768] ACPI: Power Button [PWRF]
[    0.330816] fan PNP0C0B:00: registered as cooling_device0
[    0.330822] ACPI: Fan [FAN] (on)
[    0.331339] processor LNXCPU:00: registered as cooling_device1
[    0.335822] thermal LNXTHERM:01: registered as thermal_zone0
[    0.335828] ACPI: Thermal Zone [THRM] (40 C)
[    0.340445] Linux agpgart interface v0.103
[    0.340485] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.340577] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.340841] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.341792] brd: module loaded
[    0.342218] loop: module loaded
[    0.342299] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.350193] pata_acpi 0000:00:06.0: setting latency timer to 64
[    0.350672] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[    0.350677]   alloc irq_desc for 23 on node 0
[    0.350679]   alloc kstat_irqs on node 0
[    0.350689] pata_acpi 0000:00:07.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    0.350704] pata_acpi 0000:00:07.0: setting latency timer to 64
[    0.350710] pata_acpi 0000:00:07.0: PCI INT A disabled
[    0.351086] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 22
[    0.351089]   alloc irq_desc for 22 on node 0
[    0.351090]   alloc kstat_irqs on node 0
[    0.351096] pata_acpi 0000:00:08.0: PCI INT A -> Link[APSJ] -> GSI 22 (level, low) -> IRQ 22
[    0.351110] pata_acpi 0000:00:08.0: setting latency timer to 64
[    0.351116] pata_acpi 0000:00:08.0: PCI INT A disabled
[    0.360382] Fixed MDIO Bus: probed
[    0.360414] PPP generic driver version 2.4.2
[    0.360470] tun: Universal TUN/TAP device driver, 1.6
[    0.360471] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.360565] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.360946] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 21
[    0.360951]   alloc irq_desc for 21 on node 0
[    0.360953]   alloc kstat_irqs on node 0
[    0.360962] ehci_hcd 0000:00:02.1: PCI INT B -> Link[APCL] -> GSI 21 (level, low) -> IRQ 21
[    0.360978] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    0.360981] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    0.361015] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    0.361044] ehci_hcd 0000:00:02.1: debug port 1
[    0.361049] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    0.361069] ehci_hcd 0000:00:02.1: irq 21, io mem 0xfeb00000
[    0.380050] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    0.380182] usb usb1: configuration #1 chosen from 1 choice
[    0.380222] hub 1-0:1.0: USB hub found
[    0.380232] hub 1-0:1.0: 10 ports detected
[    0.380321] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.390425] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 20
[    0.390431]   alloc irq_desc for 20 on node 0
[    0.390433]   alloc kstat_irqs on node 0
[    0.390443] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 20 (level, low) -> IRQ 20
[    0.390463] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    0.390466] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    0.390546] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    0.390576] ohci_hcd 0000:00:02.0: irq 20, io mem 0xdc004000
[    0.452263] usb usb2: configuration #1 chosen from 1 choice
[    0.452298] hub 2-0:1.0: USB hub found
[    0.452309] hub 2-0:1.0: 10 ports detected
[    0.452393] uhci_hcd: USB Universal Host Controller Interface driver
[    0.452481] PNP: No PS/2 controller found. Probing ports directly.
[    0.486530] Freeing initrd memory: 8403k freed
[    0.700522] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.700650] mice: PS/2 mouse device common for all mice
[    0.700759] rtc_cmos 00:04: RTC can wake from S4
[    0.700803] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.700825] rtc0: alarms up to one year, y3k, 242 bytes nvram
[    0.700975] device-mapper: uevent: version 1.0.3
[    0.701152] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.701200] device-mapper: multipath: version 1.1.0 loaded
[    0.701202] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.701331] cpuidle: using governor ladder
[    0.701333] cpuidle: using governor menu
[    0.701690] TCP cubic registered
[    0.701842] NET: Registered protocol family 10
[    0.702315] lo: Disabled Privacy Extensions
[    0.702618] NET: Registered protocol family 17
[    0.702650] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3500+ processors (1 cpu cores) (version 2.20.00)
[    0.706860] [Firmware Bug]: powernow-k8: No PSB or ACPI _PSS objects
[    0.706951] PM: Resume from disk failed.
[    0.706964] registered taskstats version 1
[    0.707268]   Magic number: 2:219:177
[    0.707320] acpi device:0d: hash matches
[    0.707354] rtc_cmos 00:04: setting system clock to 2010-11-04 12:11:40 UTC (1288872700)
[    0.707357] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.707358] EDD information not available.
[    0.707408] Freeing unused kernel memory: 872k freed
[    0.707866] Write protecting the kernel read-only data: 7692k
[    0.727916] udev: starting version 151
[    0.780754] md: linear personality registered for level -1
[    0.820055] usb 1-2: new high speed USB device using ehci_hcd and address 3
[    0.883691] md: multipath personality registered for level -4
[    0.953261] md: raid0 personality registered for level 0
[    0.953754] pata_amd 0000:00:06.0: version 0.4.1
[    0.953799] pata_amd 0000:00:06.0: setting latency timer to 64
[    0.957660] scsi0 : pata_amd
[    0.961049] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[    0.961055]   alloc irq_desc for 16 on node 0
[    0.961057]   alloc kstat_irqs on node 0
[    0.961066] ohci1394 0000:05:0b.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[    0.961283] scsi1 : pata_amd
[    0.961994] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    0.961996] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    0.962320] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    0.962582] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[    0.962587] forcedeth 0000:00:0a.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
[    0.962591] forcedeth 0000:00:0a.0: setting latency timer to 64
[    0.962639] nv_probe: set workaround bit for reversed mac addr
[    0.963230] md: raid1 personality registered for level 1
[    1.020050] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[db004000-db0047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    1.103296] usb 1-2: configuration #1 chosen from 1 choice
[    1.181648] ata1.00: ATA-7: WDC WD2500JB-00REA0, 20.00K20, max UDMA/100
[    1.181652] ata1.00: 488397168 sectors, multi 1: LBA48 
[    1.181681] ata1.01: ATAPI: _NEC DVD_RW ND-3550A, 1.05, max UDMA/33
[    1.181703] ata1: nv_mode_filter: 0x3f39f&0x3f39f->0x3f39f, BIOS=0x3f000 (0xc6c00000) ACPI=0x3f01f (20:60:0x1f)
[    1.181708] ata1: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc6c00000) ACPI=0x701f (20:60:0x1f)
[    1.200345] ata1.00: configured for UDMA/100
[    1.240240] ata1.01: configured for UDMA/33
[    1.240549] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500JB-00R 20.0 PQ: 0 ANSI: 5
[    1.240699] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.242190] scsi 0:0:1:0: CD-ROM            _NEC     DVD_RW ND-3550A  1.05 PQ: 0 ANSI: 5
[    1.242505] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.245182] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    1.245185] Uniform CD-ROM driver Revision: 3.20
[    1.245285] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    1.245338] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    1.245613] sd 0:0:0:0: [sda] Write Protect is off
[    1.245616] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.245649] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.245761]  sda: sda1 sda2 < sda5 >
[    1.272264] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.419520] async_tx: api initialized (async)
[    1.590045] raid6: int64x1   1834 MB/s
[    1.760018] raid6: int64x2   2387 MB/s
[    1.930013] raid6: int64x4   1623 MB/s
[    2.100030] raid6: int64x8   1616 MB/s
[    2.270030] raid6: sse2x1    2687 MB/s
[    2.440025] raid6: sse2x2    3668 MB/s
[    2.610011] raid6: sse2x4    3932 MB/s
[    2.610012] raid6: using algorithm sse2x4 (3932 MB/s)
[    2.615943] xor: automatically using best checksumming function: generic_sse
[    2.660011]    generic_sse:  7103.600 MB/sec
[    2.660013] xor: using function: generic_sse (7103.600 MB/sec)
[    2.660789] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:15:f2:56:a0:17
[    2.660792] forcedeth 0000:00:0a.0: highdma csum gbit lnktim desc-v3
[    2.661247] sata_nv 0000:00:07.0: version 3.5
[    2.661260] sata_nv 0000:00:07.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    2.661307] sata_nv 0000:00:07.0: setting latency timer to 64
[    2.661361] scsi2 : sata_nv
[    2.661472] scsi3 : sata_nv
[    2.661655] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 23
[    2.661658] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 23
[    2.661752] sata_nv 0000:00:08.0: PCI INT A -> Link[APSJ] -> GSI 22 (level, low) -> IRQ 22
[    2.661787] sata_nv 0000:00:08.0: setting latency timer to 64
[    2.661861] scsi4 : sata_nv
[    2.662086] scsi5 : sata_nv
[    2.662373] ata5: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc400 irq 22
[    2.662376] ata6: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc408 irq 22
[    2.670072] usb 2-1: new full speed USB device using ohci_hcd and address 2
[    2.775356] md: bind<sda5>
[    2.777901] md: bind<sda1>
[    2.899228] usb 2-1: configuration #1 chosen from 1 choice
[    2.930115] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d800007bf156]
[    3.150024] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.150142] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.170289] ata3.00: ATA-7: ST3250410AS, 3.AAA, max UDMA/133
[    3.170292] ata3.00: 488397168 sectors, multi 1: LBA48 NCQ (depth 0/32)
[    3.170367] ata5.00: ATA-7: ST3250823AS, 3.03, max UDMA/133
[    3.170370] ata5.00: 488397168 sectors, multi 1: LBA48 NCQ (depth 0/32)
[    3.190295] ata5.00: configured for UDMA/133
[    3.190329] ata3.00: configured for UDMA/133
[    3.190422] scsi 2:0:0:0: Direct-Access     ATA      ST3250410AS      3.AA PQ: 0 ANSI: 5
[    3.190551] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    3.190750] sd 2:0:0:0: [sdb] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    3.190790] sd 2:0:0:0: [sdb] Write Protect is off
[    3.190793] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    3.190813] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.190929]  sdb: sdb1
[    3.206086] sd 2:0:0:0: [sdb] Attached SCSI disk
[    3.240026] usb 2-4: new low speed USB device using ohci_hcd and address 3
[    3.468218] usb 2-4: configuration #1 chosen from 1 choice
[    3.680030] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.700210] ata4.00: ATA-7: ST3250410AS, 3.AAA, max UDMA/133
[    3.700213] ata4.00: 488397168 sectors, multi 1: LBA48 NCQ (depth 0/32)
[    3.740226] ata4.00: configured for UDMA/133
[    3.740323] scsi 3:0:0:0: Direct-Access     ATA      ST3250410AS      3.AA PQ: 0 ANSI: 5
[    3.740457] sd 3:0:0:0: Attached scsi generic sg3 type 0
[    3.740648] scsi 4:0:0:0: Direct-Access     ATA      ST3250823AS      3.03 PQ: 0 ANSI: 5
[    3.740738] sd 4:0:0:0: Attached scsi generic sg4 type 0
[    3.741593] sd 4:0:0:0: [sdd] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    3.741634] sd 4:0:0:0: [sdd] Write Protect is off
[    3.741637] sd 4:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    3.741657] sd 4:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.741743] sd 3:0:0:0: [sdc] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    3.741779] sd 3:0:0:0: [sdc] Write Protect is off
[    3.741782] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    3.741801] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.741920]  sdd:
[    3.742043]  sdc: sdd1 sdd2 < sdc1
[    3.761635] sd 3:0:0:0: [sdc] Attached SCSI disk
[    3.784675]  sdd5 >
[    3.785460] sd 4:0:0:0: [sdd] Attached SCSI disk
[    3.947116] md: bind<sdd1>
[    3.949170] raid1: raid set md0 active with 2 out of 2 mirrors
[    3.949196] md0: detected capacity change from 0 to 246972153856
[    3.950639] md: bind<sdd5>
[    3.951605]  md0:
[    3.952964] raid1: raid set md1 active with 2 out of 2 mirrors
[    3.952993] md1: detected capacity change from 0 to 3084320768
[    3.954061]  unknown partition table
[    3.957482]  md1: unknown partition table
[    4.230033] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.250220] ata6.00: ATA-7: ST3250410AS, 3.AAA, max UDMA/133
[    4.250223] ata6.00: 488397168 sectors, multi 1: LBA48 NCQ (depth 0/32)
[    4.290217] ata6.00: configured for UDMA/133
[    4.290310] scsi 5:0:0:0: Direct-Access     ATA      ST3250410AS      3.AA PQ: 0 ANSI: 5
[    4.290431] sd 5:0:0:0: [sde] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    4.290563] sd 5:0:0:0: [sde] Write Protect is off
[    4.290566] sd 5:0:0:0: [sde] Mode Sense: 00 3a 00 00
[    4.290588] sd 5:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.290744] sd 5:0:0:0: Attached scsi generic sg5 type 0
[    4.290876]  sde: sde1
[    4.306626] sd 5:0:0:0: [sde] Attached SCSI disk
[    4.317846] md: raid6 personality registered for level 6
[    4.317849] md: raid5 personality registered for level 5
[    4.317851] md: raid4 personality registered for level 4
[    4.320691] usbcore: registered new interface driver hiddev
[    4.328511] input: Logitech USB Mouse as /devices/pci0000:00/0000:00:02.0/usb2/2-4/2-4:1.0/input/input3
[    4.328613] generic-usb 0003:046D:C00C.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB Mouse] on usb-0000:00:02.0-4/input0
[    4.328643] usbcore: registered new interface driver usbhid
[    4.328645] usbhid: v2.6:USB HID core driver
[    4.342301] md: raid10 personality registered for level 10
[    4.362656] EXT3-fs: INFO: recovery required on readonly filesystem.
[    4.362660] EXT3-fs: write access will be enabled during recovery.
[    6.765221] kjournald starting.  Commit interval 5 seconds
[    6.765238] EXT3-fs: recovery complete.
[    6.769153] EXT3-fs: mounted filesystem with writeback data mode.
[   28.749023] Adding 3012024k swap on /dev/md1.  Priority:-1 extents:1 across:3012024k 
[   28.781165] udev: starting version 151
[   28.908391] i2c i2c-0: nForce2 SMBus adapter at 0x4c00
[   28.908412] i2c i2c-1: nForce2 SMBus adapter at 0x4c40
[   28.951447] lp: driver loaded but no devices found
[   29.107921] lirc_dev: IR Remote Control driver registered, major 61 
[   29.109645] lirc_mceusb: Windows Media Center Edition USB IR Transceiver driver for LIRC 1.90
[   29.109648] lirc_mceusb: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>, Dan Conti <dconti@acm.wwu.edu>
[   29.127495] parport_pc 00:08: reported by Plug and Play ACPI
[   29.127549] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   29.276429] lp0: using parport0 (interrupt-driven).
[   29.300040] usb 2-1: reset full speed USB device using ohci_hcd and address 2
[   29.365649] cfg80211: Calling CRDA to update world regulatory domain
[   29.417625] cfg80211: World regulatory domain updated:
[   29.417629]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   29.417631]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.417634]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   29.417636]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   29.417639]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.417641]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.434888] vga16fb: initializing
[   29.434893] vga16fb: mapped to 0xffff8800000a0000
[   29.434956] fb0: VGA16 VGA frame buffer device
[   29.447555] EDAC MC: Ver: 2.1.0 Oct 16 2010
[   29.483529] EXT3 FS on md0, internal journal
[   29.520168] lirc_dev: lirc_register_driver: sample_rate: 0
[   29.526155] lirc_mceusb[2]: Philips eHome Infrared Transceiver on usb2:2
[   29.526338] usbcore: registered new interface driver lirc_mceusb
[   29.546441] type=1505 audit(1288872729.332:2):  operation="profile_load" pid=768 name="/sbin/dhclient3"
[   29.546697] type=1505 audit(1288872729.332:3):  operation="profile_load" pid=768 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   29.546840] type=1505 audit(1288872729.332:4):  operation="profile_load" pid=768 name="/usr/lib/connman/scripts/dhclient-script"
[   29.699352] nvidia: module license 'NVIDIA' taints kernel.
[   29.699356] Disabling lock debugging due to kernel taint
[   30.213877] kjournald starting.  Commit interval 5 seconds
[   30.222220] EXT3 FS on sdc1, internal journal
[   30.222227] EXT3-fs: mounted filesystem with writeback data mode.
[   30.270053] kjournald starting.  Commit interval 5 seconds
[   30.270265] EXT3 FS on sdb1, internal journal
[   30.270270] EXT3-fs: mounted filesystem with writeback data mode.
[   30.304954] type=1505 audit(1288872730.092:5):  operation="profile_load" pid=785 name="/usr/sbin/ntpd"
[   30.306380] kjournald starting.  Commit interval 5 seconds
[   30.306645] EXT3 FS on sde1, internal journal
[   30.306650] EXT3-fs: mounted filesystem with writeback data mode.
[   30.549504] type=1505 audit(1288872730.332:6):  operation="profile_load" pid=950 name="/usr/share/gdm/guest-session/Xsession"
[   30.561700] type=1505 audit(1288872730.352:7):  operation="profile_replace" pid=951 name="/sbin/dhclient3"
[   30.561965] type=1505 audit(1288872730.352:8):  operation="profile_replace" pid=951 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   30.562116] type=1505 audit(1288872730.352:9):  operation="profile_replace" pid=951 name="/usr/lib/connman/scripts/dhclient-script"
[   30.569621] type=1505 audit(1288872730.352:10):  operation="profile_load" pid=952 name="/usr/bin/evince"
[   30.596847] type=1505 audit(1288872730.382:11):  operation="profile_load" pid=952 name="/usr/bin/evince-previewer"
[   30.840913] ppdev: user-space parallel port driver
[   31.209949] EDAC amd64_edac:  Ver: 3.2.0 Oct 16 2010
[   31.240080] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).
[   31.240086] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   31.240088]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   31.240089]  (Note that use of the override may cause unknown side effects.)
[   31.240121] amd64_edac: probe of 0000:00:18.2 failed with error -22
[   31.263215] Linux video capture interface: v2.00
[   31.274732] gameport: NS558 PnP Gameport is pnp00:0a/gameport0, io 0x201, speed 901kHz
[   31.327579] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.7 loaded
[   31.335996] cx88[0]: subsystem: 7063:5500, board: pcHDTV HD5500 HDTV [card=47,autodetected], frontend(s): 1
[   31.335999] cx88[0]: TV tuner type 64, Radio tuner type -1
[   31.367855] cx88/0: cx2388x v4l2 driver version 0.0.7 loaded
[   31.412807] cx2388x alsa driver version 0.0.7 loaded
[   31.437339] phy0 -> rt2500usb_init_eeprom: Error - Invalid RT chipset detected.
[   31.437344] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device.
[   31.437398] usbcore: registered new interface driver rt2500usb
[   31.446572] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
[   31.446578] Intel ICH 0000:00:04.0: PCI INT A -> Link[APCJ] -> GSI 22 (level, low) -> IRQ 22
[   31.446608] Intel ICH 0000:00:04.0: setting latency timer to 64
[   31.558055] tuner 2-0043: chip found @ 0x86 (cx88[0])
[   31.575899] tda9887 2-0043: creating new instance
[   31.575901] tda9887 2-0043: tda988[5/6/7] found
[   31.582697] tuner 2-0061: chip found @ 0xc2 (cx88[0])
[   31.631773] Console: switching to colour frame buffer device 80x30
[   31.746283] tuner-simple 2-0061: creating new instance
[   31.746288] tuner-simple 2-0061: type set to 64 (LG TDVS-H06xF)
[   31.749465] input: cx88 IR (pcHDTV HD5500 HDTV) as /devices/pci0000:00/0000:00:09.0/0000:05:06.2/input/input4
[   31.749618] cx88[0]/2: cx2388x 8802 Driver Manager
[   31.749634] cx88-mpeg driver manager 0000:05:06.2: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[   31.749641] cx88[0]/2: found at 0000:05:06.2, rev: 5, irq: 16, latency: 32, mmio: 0xd5000000
[   31.749647] IRQ 16/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   31.754012] cx8800 0000:05:06.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[   31.754020] cx88[0]/0: found at 0000:05:06.0, rev: 5, irq: 16, latency: 32, mmio: 0xd3000000
[   31.754031] IRQ 16/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   31.754643] cx88[0]/0: registered device video0 [v4l2]
[   31.755157] cx88[0]/0: registered device vbi0
[   31.779251] cx88_audio 0000:05:06.1: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[   31.779259] IRQ 16/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   31.779285] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[   31.784563] cx88[1]: subsystem: 7063:5500, board: pcHDTV HD5500 HDTV [card=47,autodetected], frontend(s): 1
[   31.784567] cx88[1]: TV tuner type 64, Radio tuner type -1
[   31.822653] phy1: Selected rate control algorithm 'minstrel'
[   31.823304] Registered led device: rt73usb-phy1::radio
[   31.823319] Registered led device: rt73usb-phy1::assoc
[   31.823334] Registered led device: rt73usb-phy1::quality
[   31.824009] usbcore: registered new interface driver rt73usb
[   31.840085] intel8x0_measure_ac97_clock: measured 59473 usecs (2912 samples)
[   31.840089] intel8x0: clocking to 47055
[   31.876400] rt73usb 1-2:1.0: firmware: requesting rt73.bin

``````
Not Working
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-25-generic (buildd@allspice) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #45-Ubuntu SMP Sat Oct 16 19:52:42 UTC 2010 (Ubuntu 2.6.32-25.45-generic 2.6.32.21+drm33.7)
[    0.000000] Command line: root=/dev/md0 ro ro quiet splash rootflags=data=writeback 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
[    0.000000]  BIOS-e820: 000000003fff0000 - 000000003fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fff3000 - 0000000040000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x3fff0 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FFC0000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003fff0000 (usable)
[    0.000000]  modified: 000000003fff0000 - 000000003fff3000 (ACPI NVS)
[    0.000000]  modified: 000000003fff3000 - 0000000040000000 (ACPI data)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-000000003fff0000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 003fe00000 page 2M
[    0.000000]  003fe00000 - 003fff0000 page 4k
[    0.000000] kernel direct mapping tables up to 3fff0000 @ 10000-13000
[    0.000000] RAMDISK: 377bb000 - 37fefc1b
[    0.000000] ACPI: RSDP 00000000000f7880 00014 (v00 Nvidia)
[    0.000000] ACPI: RSDT 000000003fff3040 00034 (v01 Nvidia AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: FACP 000000003fff30c0 00074 (v01 Nvidia AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: DSDT 000000003fff3180 06360 (v01 NVIDIA AWRDACPI 00001000 MSFT 0100000E)
[    0.000000] ACPI: FACS 000000003fff0000 00040
[    0.000000] ACPI: SRAT 000000003fff9600 00090 (v01 AMD    HAMMER   00000001 AMD  00000001)
[    0.000000] ACPI: MCFG 000000003fff9700 0003C (v01 Nvidia AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: APIC 000000003fff9540 0007C (v01 Nvidia AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] SRAT: PXM 0 -> APIC 0 -> Node 0
[    0.000000] SRAT: Node 0 PXM 0 0-a0000
[    0.000000] SRAT: Node 0 PXM 0 100000-40000000
[    0.000000] NUMA: Allocated memnodemap from 11000 - 11840
[    0.000000] NUMA: Using 20 for the hash shift.
[    0.000000] Bootmem setup node 0 0000000000000000-000000003fff0000
[    0.000000]   NODE_DATA [0000000000011840 - 000000000001683f]
[    0.000000]   bootmap [0000000000017000 -  000000000001efff] pages 8
[    0.000000] (8 early reservations) ==> bootmem [0000000000 - 003fff0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 0001a2ca64]    TEXT DATA BSS ==> [0001000000 - 0001a2ca64]
[    0.000000]   #3 [00377bb000 - 0037fefc1b]          RAMDISK ==> [00377bb000 - 0037fefc1b]
[    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #5 [0001a2d000 - 0001a2d14d]              BRK ==> [0001a2d000 - 0001a2d14d]
[    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #7 [0000011000 - 0000011840]       MEMNODEMAP ==> [0000011000 - 0000011840]
[    0.000000] found SMP MP-table at [ffff8800000f5500] f5500
[    0.000000]  [ffffea0000000000-ffffea0000dfffff] PMD -> [ffff880002000000-ffff880002dfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003fff0
[    0.000000] On node 0 totalpages: 262015
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 100 pages reserved
[    0.000000]   DMA zone: 3827 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 3528 pages used for memmap
[    0.000000]   DMA32 zone: 254504 pages, LIFO batch:31
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:a0000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001c00000 s91544 r8192 d23144 u1048576
[    0.000000] pcpu-alloc: s91544 r8192 d23144 u1048576 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 258331
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=/dev/md0 ro ro quiet splash rootflags=data=writeback 
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ 33fe000000 size 32 MB
[    0.000000] Aperture beyond 4GB. Ignoring.
[    0.000000] Memory: 1014516k/1048512k available (5420k kernel code, 452k absent, 33544k reserved, 2974k data, 872k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:4352 nr_irqs:424
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 10485760 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2216.669 MHz processor.
[    0.010005] Calibrating delay loop (skipped), value calculated using timer frequency.. 4433.33 BogoMIPS (lpj=22166690)
[    0.010032] Security Framework initialized
[    0.010054] AppArmor: AppArmor initialized
[    0.010174] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.010838] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.020212] Mount-cache hash table entries: 256
[    0.020358] Initializing cgroup subsys ns
[    0.020362] Initializing cgroup subsys cpuacct
[    0.020366] Initializing cgroup subsys memory
[    0.020375] Initializing cgroup subsys devices
[    0.020378] Initializing cgroup subsys freezer
[    0.020380] Initializing cgroup subsys net_cls
[    0.020399] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.020402] CPU: L2 Cache: 512K (64 bytes/line)
[    0.020404] CPU 0/0x0 -> Node 0
[    0.020406] tseg: 0000000000
[    0.020424] mce: CPU supports 5 MCE banks
[    0.020436] Performance Events: AMD PMU driver.
[    0.020441] ... version:                0
[    0.020442] ... bit width:              48
[    0.020444] ... generic registers:      4
[    0.020446] ... value mask:             0000ffffffffffff
[    0.020448] ... max period:             00007fffffffffff
[    0.020449] ... fixed-purpose events:   0
[    0.020451] ... event mask:             000000000000000f
[    0.020463] SMP alternatives: switching to UP code
[    0.029525] ACPI: Core revision 20090903
[    0.038775] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.038780] ftrace: allocating 22538 entries in 89 pages
[    0.040091] Setting APIC routing to flat
[    0.040397] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.144566] CPU0: AMD Athlon(tm) 64 Processor 3500+ stepping 02
[    0.150000] Brought up 1 CPUs
[    0.150000] Total of 1 processors activated (4433.33 BogoMIPS).
[    0.150000] CPU0 attaching NULL sched-domain.
[    0.150000] devtmpfs: initialized
[    0.150000] regulator: core version 0.5
[    0.150000] Time: 12:30:30  Date: 11/04/10
[    0.150000] NET: Registered protocol family 16
[    0.150000] node 0 link 0: io port [1000, fffff]
[    0.150000] TOM: 0000000040000000 aka 1024M
[    0.150000] node 0 link 0: mmio [e0000000, efffffff]
[    0.150000] node 0 link 0: mmio [feb00000, fec0ffff]
[    0.150000] node 0 link 0: mmio [a0000, bffff]
[    0.150000] node 0 link 0: mmio [40000000, fed3ffff]
[    0.150000] bus: [00,ff] on node 0 link 0
[    0.150000] bus: 00 index 0 io port: [0, ffff]
[    0.150000] bus: 00 index 1 mmio: [40000000, fcffffffff]
[    0.150000] bus: 00 index 2 mmio: [feb00000, fec0ffff]
[    0.150000] bus: 00 index 3 mmio: [a0000, bffff]
[    0.150000] ACPI: bus type pci registered
[    0.150000] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.150000] PCI: MCFG area at e0000000 reserved in E820
[    0.150000] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.150000] PCI: Using configuration type 1 for base access
[    0.150000] bio: create slab <bio-0> at 0
[    0.150000] ACPI: EC: Look up EC in DSDT
[    0.154745] ACPI: Interpreter enabled
[    0.154747] ACPI: (supports S0 S1 S3 S4 S5)
[    0.154772] ACPI: Using IOAPIC for interrupt routing
[    0.162495] ACPI: No dock devices found.
[    0.162592] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.162694] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.162713] pci 0000:00:01.1: reg 10 io port: [0xe400-0xe41f]
[    0.162720] pci 0000:00:01.1: reg 20 io port: [0x4c00-0x4c3f]
[    0.162724] pci 0000:00:01.1: reg 24 io port: [0x4c40-0x4c7f]
[    0.162734] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.162737] pci 0000:00:01.1: PME# disabled
[    0.162756] pci 0000:00:02.0: reg 10 32bit mmio: [0xdc004000-0xdc004fff]
[    0.162772] pci 0000:00:02.0: supports D1 D2
[    0.162774] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.162776] pci 0000:00:02.0: PME# disabled
[    0.162795] pci 0000:00:02.1: reg 10 32bit mmio: [0xfeb00000-0xfeb000ff]
[    0.162814] pci 0000:00:02.1: supports D1 D2
[    0.162816] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.162819] pci 0000:00:02.1: PME# disabled
[    0.162840] pci 0000:00:04.0: reg 10 io port: [0xdc00-0xdcff]
[    0.162843] pci 0000:00:04.0: reg 14 io port: [0xe000-0xe0ff]
[    0.162847] pci 0000:00:04.0: reg 18 32bit mmio: [0xdc003000-0xdc003fff]
[    0.162860] pci 0000:00:04.0: supports D1 D2
[    0.162880] pci 0000:00:06.0: reg 20 io port: [0xf000-0xf00f]
[    0.162903] pci 0000:00:07.0: reg 10 io port: [0x9f0-0x9f7]
[    0.162907] pci 0000:00:07.0: reg 14 io port: [0xbf0-0xbf3]
[    0.162910] pci 0000:00:07.0: reg 18 io port: [0x970-0x977]
[    0.162914] pci 0000:00:07.0: reg 1c io port: [0xb70-0xb73]
[    0.162917] pci 0000:00:07.0: reg 20 io port: [0xd800-0xd80f]
[    0.162921] pci 0000:00:07.0: reg 24 32bit mmio: [0xdc002000-0xdc002fff]
[    0.162942] pci 0000:00:08.0: reg 10 io port: [0x9e0-0x9e7]
[    0.162946] pci 0000:00:08.0: reg 14 io port: [0xbe0-0xbe3]
[    0.162949] pci 0000:00:08.0: reg 18 io port: [0x960-0x967]
[    0.162953] pci 0000:00:08.0: reg 1c io port: [0xb60-0xb63]
[    0.162956] pci 0000:00:08.0: reg 20 io port: [0xc400-0xc40f]
[    0.162960] pci 0000:00:08.0: reg 24 32bit mmio: [0xdc001000-0xdc001fff]
[    0.162995] pci 0000:00:0a.0: reg 10 32bit mmio: [0xdc000000-0xdc000fff]
[    0.162999] pci 0000:00:0a.0: reg 14 io port: [0xb000-0xb007]
[    0.163013] pci 0000:00:0a.0: supports D1 D2
[    0.163015] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.163018] pci 0000:00:0a.0: PME# disabled
[    0.163047] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.163050] pci 0000:00:0b.0: PME# disabled
[    0.163080] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.163083] pci 0000:00:0c.0: PME# disabled
[    0.163113] pci 0000:00:0d.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.163115] pci 0000:00:0d.0: PME# disabled
[    0.163145] pci 0000:00:0e.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.163148] pci 0000:00:0e.0: PME# disabled
[    0.163250] pci 0000:05:06.0: reg 10 32bit mmio: [0xd3000000-0xd3ffffff]
[    0.163296] pci 0000:05:06.1: reg 10 32bit mmio: [0xd4000000-0xd4ffffff]
[    0.163339] pci 0000:05:06.2: reg 10 32bit mmio: [0xd5000000-0xd5ffffff]
[    0.163383] pci 0000:05:06.4: reg 10 32bit mmio: [0xd6000000-0xd6ffffff]
[    0.163431] pci 0000:05:07.0: reg 10 32bit mmio: [0xd7000000-0xd7ffffff]
[    0.163477] pci 0000:05:07.1: reg 10 32bit mmio: [0xd8000000-0xd8ffffff]
[    0.163520] pci 0000:05:07.2: reg 10 32bit mmio: [0xd9000000-0xd9ffffff]
[    0.163565] pci 0000:05:07.4: reg 10 32bit mmio: [0xda000000-0xdaffffff]
[    0.163615] pci 0000:05:0b.0: reg 10 32bit mmio: [0xdb004000-0xdb0047ff]
[    0.163620] pci 0000:05:0b.0: reg 14 32bit mmio: [0xdb000000-0xdb003fff]
[    0.163645] pci 0000:05:0b.0: supports D1 D2
[    0.163647] pci 0000:05:0b.0: PME# supported from D0 D1 D2 D3hot
[    0.163650] pci 0000:05:0b.0: PME# disabled
[    0.163670] pci 0000:00:09.0: transparent bridge
[    0.163673] pci 0000:00:09.0: bridge 32bit mmio: [0xd3000000-0xdbffffff]
[    0.163782] pci 0000:01:00.0: reg 10 32bit mmio: [0xd0000000-0xd0ffffff]
[    0.163789] pci 0000:01:00.0: reg 14 64bit mmio pref: [0xc0000000-0xcfffffff]
[    0.163795] pci 0000:01:00.0: reg 1c 64bit mmio: [0xd1000000-0xd1ffffff]
[    0.163802] pci 0000:01:00.0: reg 30 32bit mmio pref: [0xd2000000-0xd201ffff]
[    0.163847] pci 0000:00:0e.0: bridge 32bit mmio: [0xd0000000-0xd2ffffff]
[    0.163851] pci 0000:00:0e.0: bridge 64bit mmio pref: [0xc0000000-0xcfffffff]
[    0.163864] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.164089] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.228366] ACPI: PCI Interrupt Link [LNK1] (IRQs *3 4 5 7 9 10 11 12 14 15)
[    0.228500] ACPI: PCI Interrupt Link [LNK2] (IRQs *3 4 5 7 9 10 11 12 14 15)
[    0.228633] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[    0.228765] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.228898] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.229032] ACPI: PCI Interrupt Link [LUBA] (IRQs *3 4 5 7 9 10 11 12 14 15)
[    0.229172] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.229306] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[    0.229439] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 7 9 10 11 *12 14 15)
[    0.229571] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.229705] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 5 7 9 10 11 *12 14 15)
[    0.229842] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.229974] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.230141] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.230286] ACPI: PCI Interrupt Link [LFID] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[    0.230429] ACPI: PCI Interrupt Link [LPCA] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.230583] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0
[    0.230732] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0
[    0.230881] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
[    0.231030] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[    0.231123] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
[    0.231281] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[    0.231438] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[    0.231595] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[    0.231752] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0
[    0.231908] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[    0.232066] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[    0.232222] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[    0.232379] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[    0.232545] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[    0.232710] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
[    0.232879] ACPI: PCI Interrupt Link [APCP] (IRQs 20 21 22 23) *0, disabled.
[    0.232999] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.233001] vgaarb: loaded
[    0.233107] SCSI subsystem initialized
[    0.233185] libata version 3.00 loaded.
[    0.233249] usbcore: registered new interface driver usbfs
[    0.233260] usbcore: registered new interface driver hub
[    0.233281] usbcore: registered new device driver usb
[    0.233391] ACPI: WMI: Mapper loaded
[    0.233393] PCI: Using ACPI for IRQ routing
[    0.233533] NetLabel: Initializing
[    0.233535] NetLabel:  domain hash size = 128
[    0.233536] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.233549] NetLabel:  unlabeled traffic allowed by default
[    0.235127] AppArmor: AppArmor Filesystem Enabled
[    0.235147] pnp: PnP ACPI init
[    0.235169] ACPI: bus type pnp registered
[    0.239930] pnp: PnP ACPI: found 13 devices
[    0.239932] ACPI: ACPI bus type pnp unregistered
[    0.239944] system 00:01: ioport range 0x4000-0x407f has been reserved
[    0.239947] system 00:01: ioport range 0x4080-0x40ff has been reserved
[    0.239950] system 00:01: ioport range 0x4400-0x447f has been reserved
[    0.239952] system 00:01: ioport range 0x4480-0x44ff has been reserved
[    0.239955] system 00:01: ioport range 0x4800-0x487f has been reserved
[    0.239958] system 00:01: ioport range 0x4880-0x48ff has been reserved
[    0.239963] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.239966] system 00:02: ioport range 0x800-0x87f has been reserved
[    0.239969] system 00:02: ioport range 0x290-0x297 has been reserved
[    0.239975] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
[    0.240023] system 00:0c: iomem range 0xf0000-0xf3fff could not be reserved
[    0.240026] system 00:0c: iomem range 0xf4000-0xf7fff could not be reserved
[    0.240029] system 00:0c: iomem range 0xf8000-0xfbfff could not be reserved
[    0.240031] system 00:0c: iomem range 0xfc000-0xfffff could not be reserved
[    0.240034] system 00:0c: iomem range 0x3fff0000-0x3fffffff could not be reserved
[    0.240037] system 00:0c: iomem range 0xffff0000-0xffffffff has been reserved
[    0.240040] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    0.240043] system 00:0c: iomem range 0x100000-0x3ffeffff could not be reserved
[    0.240046] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.240049] system 00:0c: iomem range 0xfee00000-0xfeefffff has been reserved
[    0.240052] system 00:0c: iomem range 0xfefff000-0xfeffffff has been reserved
[    0.240055] system 00:0c: iomem range 0xfff80000-0xfff80fff has been reserved
[    0.240058] system 00:0c: iomem range 0xfff90000-0xfffbffff has been reserved
[    0.240061] system 00:0c: iomem range 0xfffed000-0xfffeffff has been reserved
[    0.244738] Switching to clocksource acpi_pm
[    0.244857] pci 0000:00:09.0: PCI bridge, secondary bus 0000:05
[    0.244859] pci 0000:00:09.0:   IO window: disabled
[    0.244862] pci 0000:00:09.0:   MEM window: 0xd3000000-0xdbffffff
[    0.244864] pci 0000:00:09.0:   PREFETCH window: disabled
[    0.244868] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:04
[    0.244869] pci 0000:00:0b.0:   IO window: disabled
[    0.244872] pci 0000:00:0b.0:   MEM window: disabled
[    0.244874] pci 0000:00:0b.0:   PREFETCH window: disabled
[    0.244878] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:03
[    0.244879] pci 0000:00:0c.0:   IO window: disabled
[    0.244882] pci 0000:00:0c.0:   MEM window: disabled
[    0.244884] pci 0000:00:0c.0:   PREFETCH window: disabled
[    0.244887] pci 0000:00:0d.0: PCI bridge, secondary bus 0000:02
[    0.244889] pci 0000:00:0d.0:   IO window: disabled
[    0.244892] pci 0000:00:0d.0:   MEM window: disabled
[    0.244894] pci 0000:00:0d.0:   PREFETCH window: disabled
[    0.244897] pci 0000:00:0e.0: PCI bridge, secondary bus 0000:01
[    0.244899] pci 0000:00:0e.0:   IO window: disabled
[    0.244902] pci 0000:00:0e.0:   MEM window: 0xd0000000-0xd2ffffff
[    0.244905] pci 0000:00:0e.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff
[    0.244914] pci 0000:00:09.0: setting latency timer to 64
[    0.244919] pci 0000:00:0b.0: setting latency timer to 64
[    0.244923] pci 0000:00:0c.0: setting latency timer to 64
[    0.244928] pci 0000:00:0d.0: setting latency timer to 64
[    0.244933] pci 0000:00:0e.0: setting latency timer to 64
[    0.244937] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.244939] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.244942] pci_bus 0000:05: resource 1 mem: [0xd3000000-0xdbffffff]
[    0.244944] pci_bus 0000:05: resource 3 io:  [0x00-0xffff]
[    0.244947] pci_bus 0000:05: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.244950] pci_bus 0000:01: resource 1 mem: [0xd0000000-0xd2ffffff]
[    0.244953] pci_bus 0000:01: resource 2 pref mem [0xc0000000-0xcfffffff]
[    0.244989] NET: Registered protocol family 2
[    0.245093] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.245640] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[    0.246932] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.247562] TCP: Hash tables configured (established 131072 bind 65536)
[    0.247565] TCP reno registered
[    0.247669] NET: Registered protocol family 1
[    0.260076] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.260082] pci 0000:00:0b.0: Found disabled HT MSI Mapping
[    0.260088] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.260092] pci 0000:00:0b.0: Linking AER extended capability
[    0.260126] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.260131] pci 0000:00:0c.0: Found disabled HT MSI Mapping
[    0.260138] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.260140] pci 0000:00:0c.0: Linking AER extended capability
[    0.260177] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.260182] pci 0000:00:0d.0: Found disabled HT MSI Mapping
[    0.260189] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.260191] pci 0000:00:0d.0: Linking AER extended capability
[    0.260232] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.260237] pci 0000:00:0e.0: Found disabled HT MSI Mapping
[    0.260244] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.260246] pci 0000:00:0e.0: Linking AER extended capability
[    0.260271] pci 0000:01:00.0: Boot video device
[    0.260487] Trying to unpack rootfs image as initramfs...
[    0.300481] Scanning for low memory corruption every 60 seconds
[    0.300610] audit: initializing netlink socket (disabled)
[    0.300623] type=2000 audit(1288873830.300:1): initialized
[    0.320274] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.321599] VFS: Disk quotas dquot_6.5.2
[    0.321651] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.322244] fuse init (API version 7.13)
[    0.322319] msgmni has been set to 1981
[    0.322527] alg: No test for stdrng (krng)
[    0.322579] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.322582] io scheduler noop registered
[    0.322583] io scheduler anticipatory registered
[    0.322585] io scheduler deadline registered
[    0.322628] io scheduler cfq registered (default)
[    0.330154]   alloc irq_desc for 24 on node 0
[    0.330157]   alloc kstat_irqs on node 0
[    0.330168] pcieport 0000:00:0b.0: irq 24 for MSI/MSI-X
[    0.330173] pcieport 0000:00:0b.0: setting latency timer to 64
[    0.330324]   alloc irq_desc for 25 on node 0
[    0.330325]   alloc kstat_irqs on node 0
[    0.330330] pcieport 0000:00:0c.0: irq 25 for MSI/MSI-X
[    0.330334] pcieport 0000:00:0c.0: setting latency timer to 64
[    0.330416]   alloc irq_desc for 26 on node 0
[    0.330418]   alloc kstat_irqs on node 0
[    0.330422] pcieport 0000:00:0d.0: irq 26 for MSI/MSI-X
[    0.330426] pcieport 0000:00:0d.0: setting latency timer to 64
[    0.330510]   alloc irq_desc for 27 on node 0
[    0.330511]   alloc kstat_irqs on node 0
[    0.330515] pcieport 0000:00:0e.0: irq 27 for MSI/MSI-X
[    0.330519] pcieport 0000:00:0e.0: setting latency timer to 64
[    0.330583] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.330607] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.330708] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.330712] ACPI: Power Button [PWRB]
[    0.330767] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.330770] ACPI: Power Button [PWRF]
[    0.330818] fan PNP0C0B:00: registered as cooling_device0
[    0.330824] ACPI: Fan [FAN] (on)
[    0.331341] processor LNXCPU:00: registered as cooling_device1
[    0.335823] thermal LNXTHERM:01: registered as thermal_zone0
[    0.335829] ACPI: Thermal Zone [THRM] (40 C)
[    0.340448] Linux agpgart interface v0.103
[    0.340488] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.340580] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.340844] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.341793] brd: module loaded
[    0.342219] loop: module loaded
[    0.342300] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.350193] pata_acpi 0000:00:06.0: setting latency timer to 64
[    0.350671] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[    0.350676]   alloc irq_desc for 23 on node 0
[    0.350679]   alloc kstat_irqs on node 0
[    0.350688] pata_acpi 0000:00:07.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    0.350703] pata_acpi 0000:00:07.0: setting latency timer to 64
[    0.350709] pata_acpi 0000:00:07.0: PCI INT A disabled
[    0.351085] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 22
[    0.351088]   alloc irq_desc for 22 on node 0
[    0.351089]   alloc kstat_irqs on node 0
[    0.351095] pata_acpi 0000:00:08.0: PCI INT A -> Link[APSJ] -> GSI 22 (level, low) -> IRQ 22
[    0.351109] pata_acpi 0000:00:08.0: setting latency timer to 64
[    0.351115] pata_acpi 0000:00:08.0: PCI INT A disabled
[    0.360384] Fixed MDIO Bus: probed
[    0.360416] PPP generic driver version 2.4.2
[    0.360473] tun: Universal TUN/TAP device driver, 1.6
[    0.360474] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.360568] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.360950] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 21
[    0.360955]   alloc irq_desc for 21 on node 0
[    0.360957]   alloc kstat_irqs on node 0
[    0.360965] ehci_hcd 0000:00:02.1: PCI INT B -> Link[APCL] -> GSI 21 (level, low) -> IRQ 21
[    0.360983] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    0.360985] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    0.361019] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    0.361047] ehci_hcd 0000:00:02.1: debug port 1
[    0.361052] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    0.361072] ehci_hcd 0000:00:02.1: irq 21, io mem 0xfeb00000
[    0.380049] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    0.380181] usb usb1: configuration #1 chosen from 1 choice
[    0.380218] hub 1-0:1.0: USB hub found
[    0.380228] hub 1-0:1.0: 10 ports detected
[    0.380316] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.390403] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 20
[    0.390409]   alloc irq_desc for 20 on node 0
[    0.390411]   alloc kstat_irqs on node 0
[    0.390421] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 20 (level, low) -> IRQ 20
[    0.390441] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    0.390444] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    0.390522] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    0.390552] ohci_hcd 0000:00:02.0: irq 20, io mem 0xdc004000
[    0.452228] usb usb2: configuration #1 chosen from 1 choice
[    0.452262] hub 2-0:1.0: USB hub found
[    0.452272] hub 2-0:1.0: 10 ports detected
[    0.452353] uhci_hcd: USB Universal Host Controller Interface driver
[    0.452441] PNP: No PS/2 controller found. Probing ports directly.
[    0.486485] Freeing initrd memory: 8403k freed
[    0.700522] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.700652] mice: PS/2 mouse device common for all mice
[    0.700761] rtc_cmos 00:04: RTC can wake from S4
[    0.700805] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.700827] rtc0: alarms up to one year, y3k, 242 bytes nvram
[    0.700978] device-mapper: uevent: version 1.0.3
[    0.701152] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.701201] device-mapper: multipath: version 1.1.0 loaded
[    0.701204] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.701332] cpuidle: using governor ladder
[    0.701334] cpuidle: using governor menu
[    0.701691] TCP cubic registered
[    0.701843] NET: Registered protocol family 10
[    0.702317] lo: Disabled Privacy Extensions
[    0.702619] NET: Registered protocol family 17
[    0.702652] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3500+ processors (1 cpu cores) (version 2.20.00)
[    0.706862] [Firmware Bug]: powernow-k8: No PSB or ACPI _PSS objects
[    0.706955] PM: Resume from disk failed.
[    0.706968] registered taskstats version 1
[    0.707273]   Magic number: 2:81:531
[    0.707357] rtc_cmos 00:04: setting system clock to 2010-11-04 12:30:30 UTC (1288873830)
[    0.707360] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.707361] EDD information not available.
[    0.707410] Freeing unused kernel memory: 872k freed
[    0.707867] Write protecting the kernel read-only data: 7692k
[    0.727967] udev: starting version 151
[    0.780804] md: linear personality registered for level -1
[    0.820051] usb 1-2: new high speed USB device using ehci_hcd and address 3
[    0.893609] md: multipath personality registered for level -4
[    0.951882] pata_amd 0000:00:06.0: version 0.4.1
[    0.951930] pata_amd 0000:00:06.0: setting latency timer to 64
[    0.952044] scsi0 : pata_amd
[    0.952248] scsi1 : pata_amd
[    0.953071] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    0.953073] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    0.953366] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    0.953642] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[    0.953647] forcedeth 0000:00:0a.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
[    0.953651] forcedeth 0000:00:0a.0: setting latency timer to 64
[    0.953697] nv_probe: set workaround bit for reversed mac addr
[    0.955008] md: raid0 personality registered for level 0
[    1.103302] usb 1-2: configuration #1 chosen from 1 choice
[    1.171511] ata1.00: ATA-7: WDC WD2500JB-00REA0, 20.00K20, max UDMA/100
[    1.171515] ata1.00: 488397168 sectors, multi 1: LBA48 
[    1.171544] ata1.01: ATAPI: _NEC DVD_RW ND-3550A, 1.05, max UDMA/33
[    1.171566] ata1: nv_mode_filter: 0x3f39f&0x3f39f->0x3f39f, BIOS=0x3f000 (0xc6c00000) ACPI=0x3f01f (20:60:0x1f)
[    1.171572] ata1: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc6c00000) ACPI=0x701f (20:60:0x1f)
[    1.190346] ata1.00: configured for UDMA/100
[    1.230234] ata1.01: configured for UDMA/33
[    1.230583] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500JB-00R 20.0 PQ: 0 ANSI: 5
[    1.230736] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.232082] scsi 0:0:1:0: CD-ROM            _NEC     DVD_RW ND-3550A  1.05 PQ: 0 ANSI: 5
[    1.232390] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.235316] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    1.235319] Uniform CD-ROM driver Revision: 3.20
[    1.235421] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    1.235482] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    1.235765] sd 0:0:0:0: [sda] Write Protect is off
[    1.235768] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.235801] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.235919]  sda: sda1 sda2 < sda5 >
[    1.262128] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.408506] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[    1.408512]   alloc irq_desc for 16 on node 0
[    1.408514]   alloc kstat_irqs on node 0
[    1.408523] ohci1394 0000:05:0b.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[    1.416629] md: raid1 personality registered for level 1
[    1.421651] async_tx: api initialized (async)
[    1.590019] raid6: int64x1   1826 MB/s
[    1.760021] raid6: int64x2   2379 MB/s
[    1.930040] raid6: int64x4   1623 MB/s
[    2.100037] raid6: int64x8   1615 MB/s
[    2.270021] raid6: sse2x1    2643 MB/s
[    2.440022] raid6: sse2x2    3623 MB/s
[    2.610014] raid6: sse2x4    3877 MB/s
[    2.610015] raid6: using algorithm sse2x4 (3877 MB/s)
[    2.610152] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[db004000-db0047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    2.612887] xor: automatically using best checksumming function: generic_sse
[    2.660011]    generic_sse:  7104.000 MB/sec
[    2.660013] xor: using function: generic_sse (7104.000 MB/sec)
[    2.660713] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:15:f2:56:a0:17
[    2.660716] forcedeth 0000:00:0a.0: highdma csum gbit lnktim desc-v3
[    2.661376] sata_nv 0000:00:07.0: version 3.5
[    2.661391] sata_nv 0000:00:07.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    2.661439] sata_nv 0000:00:07.0: setting latency timer to 64
[    2.661500] scsi2 : sata_nv
[    2.661625] scsi3 : sata_nv
[    2.661815] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 23
[    2.661817] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 23
[    2.661915] sata_nv 0000:00:08.0: PCI INT A -> Link[APSJ] -> GSI 22 (level, low) -> IRQ 22
[    2.661952] sata_nv 0000:00:08.0: setting latency timer to 64
[    2.662025] scsi4 : sata_nv
[    2.662258] scsi5 : sata_nv
[    2.662558] ata5: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc400 irq 22
[    2.662560] ata6: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc408 irq 22
[    2.730082] usb 2-1: new full speed USB device using ohci_hcd and address 2
[    2.748403] md: bind<sda5>
[    2.750956] md: bind<sda1>
[    2.959199] usb 2-1: configuration #1 chosen from 1 choice
[    3.150025] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.150145] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.170274] ata3.00: ATA-7: ST3250410AS, 3.AAA, max UDMA/133
[    3.170277] ata3.00: 488397168 sectors, multi 1: LBA48 NCQ (depth 0/32)
[    3.170352] ata5.00: ATA-7: ST3250823AS, 3.03, max UDMA/133
[    3.170355] ata5.00: 488397168 sectors, multi 1: LBA48 NCQ (depth 0/32)
[    3.210285] ata3.00: configured for UDMA/133
[    3.210386] scsi 2:0:0:0: Direct-Access     ATA      ST3250410AS      3.AA PQ: 0 ANSI: 5
[    3.210534] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    3.210743] sd 2:0:0:0: [sdb] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    3.210782] sd 2:0:0:0: [sdb] Write Protect is off
[    3.210784] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    3.210804] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.210882] ata5.00: configured for UDMA/133
[    3.210952]  sdb: sdb1
[    3.229102] sd 2:0:0:0: [sdb] Attached SCSI disk
[    3.300021] usb 2-4: new low speed USB device using ohci_hcd and address 3
[    3.529183] usb 2-4: configuration #1 chosen from 1 choice
[    3.700025] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.720210] ata4.00: ATA-7: ST3250410AS, 3.AAA, max UDMA/133
[    3.720214] ata4.00: 488397168 sectors, multi 1: LBA48 NCQ (depth 0/32)
[    3.760187] ata4.00: configured for UDMA/133
[    3.760276] scsi 3:0:0:0: Direct-Access     ATA      ST3250410AS      3.AA PQ: 0 ANSI: 5
[    3.760413] sd 3:0:0:0: Attached scsi generic sg3 type 0
[    3.760617] scsi 4:0:0:0: Direct-Access     ATA      ST3250823AS      3.03 PQ: 0 ANSI: 5
[    3.760713] sd 4:0:0:0: Attached scsi generic sg4 type 0
[    3.761557] sd 4:0:0:0: [sdd] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    3.761598] sd 4:0:0:0: [sdd] Write Protect is off
[    3.761600] sd 4:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    3.761620] sd 4:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.761703] sd 3:0:0:0: [sdc] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    3.761738] sd 3:0:0:0: [sdc] Write Protect is off
[    3.761740] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    3.761759] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.761887]  sdd:
[    3.762002]  sdc: sdc1
[    3.775304] sd 3:0:0:0: [sdc] Attached SCSI disk
[    3.784757]  sdd1 sdd2 < sdd5 >
[    3.809989] sd 4:0:0:0: [sdd] Attached SCSI disk
[    3.870029] usb 2-9: new low speed USB device using ohci_hcd and address 4
[    3.930183] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d800007bf156]
[    3.971615] md: bind<sdd1>
[    3.973716] raid1: raid set md0 active with 2 out of 2 mirrors
[    3.973742] md0: detected capacity change from 0 to 246972153856
[    3.975171] md: bind<sdd5>
[    3.976169]  md0:
[    3.977563] raid1: raid set md1 active with 2 out of 2 mirrors
[    3.977594] md1: detected capacity change from 0 to 3084320768
[    3.978673]  unknown partition table
[    3.982299]  md1: unknown partition table
[    4.097193] usb 2-9: configuration #1 chosen from 1 choice
[    4.107445] usbcore: registered new interface driver hiddev
[    4.115476] input: Logitech USB Mouse as /devices/pci0000:00/0000:00:02.0/usb2/2-4/2-4:1.0/input/input3
[    4.115648] generic-usb 0003:046D:C00C.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB Mouse] on usb-0000:00:02.0-4/input0
[    4.115914] usbcore: registered new interface driver usbhid
[    4.116011] usbhid: v2.6:USB HID core driver
[    4.250030] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.270204] ata6.00: ATA-7: ST3250410AS, 3.AAA, max UDMA/133
[    4.270207] ata6.00: 488397168 sectors, multi 1: LBA48 NCQ (depth 0/32)
[    4.310221] ata6.00: configured for UDMA/133
[    4.310314] scsi 5:0:0:0: Direct-Access     ATA      ST3250410AS      3.AA PQ: 0 ANSI: 5
[    4.310456] sd 5:0:0:0: Attached scsi generic sg5 type 0
[    4.311320] sd 5:0:0:0: [sde] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    4.311362] sd 5:0:0:0: [sde] Write Protect is off
[    4.311365] sd 5:0:0:0: [sde] Mode Sense: 00 3a 00 00
[    4.311386] sd 5:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.311525]  sde: sde1
[    4.323878] sd 5:0:0:0: [sde] Attached SCSI disk
[    4.329176] md: raid6 personality registered for level 6
[    4.329179] md: raid5 personality registered for level 5
[    4.329181] md: raid4 personality registered for level 4
[    4.341875] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:02.0/usb2/2-9/2-9:1.0/input/input4
[    4.342033] logitech 0003:046D:C517.0002: input,hidraw1: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:02.0-9/input0
[    4.351128] logitech 0003:046D:C517.0003: fixing up Logitech keyboard report descriptor
[    4.352174] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:02.0/usb2/2-9/2-9:1.1/input/input5
[    4.352928] logitech 0003:046D:C517.0003: input,hiddev96,hidraw2: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:02.0-9/input1
[    4.363321] md: raid10 personality registered for level 10
[    4.384083] EXT3-fs: INFO: recovery required on readonly filesystem.
[    4.384087] EXT3-fs: write access will be enabled during recovery.
[    5.783739] kjournald starting.  Commit interval 5 seconds
[    5.783757] EXT3-fs: recovery complete.
[    5.784238] EXT3-fs: mounted filesystem with writeback data mode.
[   27.056200] Adding 3012024k swap on /dev/md1.  Priority:-1 extents:1 across:3012024k 
[   27.091158] udev: starting version 151
[   27.197303] i2c i2c-0: nForce2 SMBus adapter at 0x4c00
[   27.197321] i2c i2c-1: nForce2 SMBus adapter at 0x4c40
[   27.223555] lirc_dev: IR Remote Control driver registered, major 61 
[   27.225230] lirc_mceusb: Windows Media Center Edition USB IR Transceiver driver for LIRC 1.90
[   27.225233] lirc_mceusb: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>, Dan Conti <dconti@acm.wwu.edu>
[   27.241162] lp: driver loaded but no devices found
[   27.440101] usb 2-1: reset full speed USB device using ohci_hcd and address 2
[   27.462864] parport_pc 00:08: reported by Plug and Play ACPI
[   27.462916] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   27.466622] EDAC MC: Ver: 2.1.0 Oct 16 2010
[   27.540783] lp0: using parport0 (interrupt-driven).
[   27.660136] lirc_dev: lirc_register_driver: sample_rate: 0
[   27.666119] lirc_mceusb[2]: Philips eHome Infrared Transceiver on usb2:2
[   27.666168] usbcore: registered new interface driver lirc_mceusb
[   27.754535] vga16fb: initializing
[   27.754539] vga16fb: mapped to 0xffff8800000a0000
[   27.754607] fb0: VGA16 VGA frame buffer device
[   27.763999] cfg80211: Calling CRDA to update world regulatory domain
[   27.799951] cfg80211: World regulatory domain updated:
[   27.799954]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   27.799957]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   27.799959]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   27.799962]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   27.799964]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   27.799966]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   27.807208] type=1505 audit(1288873857.592:2):  operation="profile_load" pid=801 name="/sbin/dhclient3"
[   27.807466] type=1505 audit(1288873857.592:3):  operation="profile_load" pid=801 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   27.807608] type=1505 audit(1288873857.592:4):  operation="profile_load" pid=801 name="/usr/lib/connman/scripts/dhclient-script"
[   27.881519] EXT3 FS on md0, internal journal
[   28.073745] nvidia: module license 'NVIDIA' taints kernel.
[   28.073748] Disabling lock debugging due to kernel taint
[   28.610043] kjournald starting.  Commit interval 5 seconds
[   28.610263] EXT3 FS on sdb1, internal journal
[   28.610268] EXT3-fs: mounted filesystem with writeback data mode.
[   28.664401] kjournald starting.  Commit interval 5 seconds
[   28.664599] EXT3 FS on sdc1, internal journal
[   28.664604] EXT3-fs: mounted filesystem with writeback data mode.
[   28.683066] type=1505 audit(1288873858.472:5):  operation="profile_load" pid=818 name="/usr/sbin/ntpd"
[   28.698143] kjournald starting.  Commit interval 5 seconds
[   28.698639] EXT3 FS on sde1, internal journal
[   28.698645] EXT3-fs: mounted filesystem with writeback data mode.
[   28.919527] type=1505 audit(1288873858.702:6):  operation="profile_load" pid=1029 name="/usr/share/gdm/guest-session/Xsession"
[   28.934238] type=1505 audit(1288873858.722:7):  operation="profile_replace" pid=1030 name="/sbin/dhclient3"
[   28.934504] type=1505 audit(1288873858.722:8):  operation="profile_replace" pid=1030 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   28.934656] type=1505 audit(1288873858.722:9):  operation="profile_replace" pid=1030 name="/usr/lib/connman/scripts/dhclient-script"
[   28.952079] type=1505 audit(1288873858.742:10):  operation="profile_load" pid=1031 name="/usr/bin/evince"
[   28.955495] type=1505 audit(1288873858.742:11):  operation="profile_load" pid=1031 name="/usr/bin/evince-previewer"
[   29.192627] EDAC amd64_edac:  Ver: 3.2.0 Oct 16 2010
[   29.224309] ppdev: user-space parallel port driver
[   29.481831] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).
[   29.481837] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   29.481839]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   29.481840]  (Note that use of the override may cause unknown side effects.)
[   29.481865] amd64_edac: probe of 0000:00:18.2 failed with error -22
[   29.495616] Linux video capture interface: v2.00
[   29.672354] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.7 loaded
[   29.674575] cx88[0]: subsystem: 7063:5500, board: pcHDTV HD5500 HDTV [card=47,autodetected], frontend(s): 1
[   29.674578] cx88[0]: TV tuner type 64, Radio tuner type -1
[   29.677516] gameport: NS558 PnP Gameport is pnp00:0a/gameport0, io 0x201, speed 901kHz
[   29.692070] cx88/0: cx2388x v4l2 driver version 0.0.7 loaded
[   29.763169] cx2388x alsa driver version 0.0.7 loaded
[   29.802799] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
[   29.802805] Intel ICH 0000:00:04.0: PCI INT A -> Link[APCJ] -> GSI 22 (level, low) -> IRQ 22
[   29.802837] Intel ICH 0000:00:04.0: setting latency timer to 64
[   29.807466] phy0 -> rt2500usb_init_eeprom: Error - Invalid RT chipset detected.
[   29.807471] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device.
[   29.807529] usbcore: registered new interface driver rt2500usb
[   29.862903] tuner 2-0043: chip found @ 0x86 (cx88[0])
[   29.924324] tda9887 2-0043: creating new instance
[   29.924327] tda9887 2-0043: tda988[5/6/7] found
[   29.929702] tuner 2-0061: chip found @ 0xc2 (cx88[0])
[   29.994008] Console: switching to colour frame buffer device 80x30
[   30.023415] tuner-simple 2-0061: creating new instance
[   30.023419] tuner-simple 2-0061: type set to 64 (LG TDVS-H06xF)
[   30.026323] input: cx88 IR (pcHDTV HD5500 HDTV) as /devices/pci0000:00/0000:00:09.0/0000:05:06.2/input/input6
[   30.026439] cx88[0]/2: cx2388x 8802 Driver Manager
[   30.026455] cx88-mpeg driver manager 0000:05:06.2: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[   30.026462] cx88[0]/2: found at 0000:05:06.2, rev: 5, irq: 16, latency: 32, mmio: 0xd5000000
[   30.026468] IRQ 16/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   30.028618] cx8800 0000:05:06.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[   30.028626] cx88[0]/0: found at 0000:05:06.0, rev: 5, irq: 16, latency: 32, mmio: 0xd3000000
[   30.028637] IRQ 16/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   30.028848] cx88[0]/0: registered device video0 [v4l2]
[   30.028927] cx88[0]/0: registered device vbi0
[   30.045954] cx88_audio 0000:05:06.1: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[   30.045963] IRQ 16/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   30.045985] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[   30.049653] cx88[1]: subsystem: 7063:5500, board: pcHDTV HD5500 HDTV [card=47,autodetected], frontend(s): 1
[   30.049656] cx88[1]: TV tuner type 64, Radio tuner type -1
[   30.153262] intel8x0_measure_ac97_clock: measured 63499 usecs (3112 samples)
[   30.153266] intel8x0: clocking to 47012
[   30.195997] phy1: Selected rate control algorithm 'minstrel'
[   30.196689] Registered led device: rt73usb-phy1::radio
[   30.196705] Registered led device: rt73usb-phy1::assoc
[   30.196723] Registered led device: rt73usb-phy1::quality
[   30.197513] usbcore: registered new interface driver rt73usb
[   30.207104] tuner 3-0043: chip found @ 0x86 (cx88[1])
[   30.207184] tda9887 3-0043: creating new instance
[   30.207187] tda9887 3-0043: tda988[5/6/7] found
[   30.235513] tuner 3-0061: chip found @ 0xc2 (cx88[1])
[   30.280876] rt73usb 1-2:1.0: firmware: requesting rt73.bin

```

---

