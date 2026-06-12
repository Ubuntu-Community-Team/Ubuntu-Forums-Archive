---
title: "Usb ports not working after update"
date: 2011-09-14
forum: Hardware
---

### Post by devilunix on 2011-09-14
hi folks.i installed ubuntu via wubi installer everything was ok till i update it.After update to latest version (around 232 updates)usb ports dont work.They are working no problem with win7.i tried 3 times same process .installed and updated.result is same not working after updates.my wireless card is ralink RT73 USB card.i cannot use internet.i can use ubuntu with no usb  but cant use it witouth internet.Help pls.some logs i saved like this .my knowledge about linux is nothing im newbie.

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-11-generic (buildd@allspice) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) ) #48-Ubuntu SMP Fri Jul 29 19:02:55 UTC 2011 (Ubuntu 2.6.38-11.48-generic 2.6.38.8)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-11-generic root=UUID=C43EB5173EB50388 loop=/ubuntu/disks/root.disk ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfdf0000 (usable)
[    0.000000]  BIOS-e820: 00000000cfdf0000 - 00000000cfdf3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cfdf3000 - 00000000cfe00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cfe00000 - 00000000cff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.4 present.
[    0.000000] DMI: Gigabyte Technology Co., Ltd. GA-MA785GM-US2H/GA-MA785GM-US2H, BIOS F11 05/17/2010
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x130000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 base 0000C0000000 mask FFFFF0000000 write-back
[    0.000000]   3 base 0000CFE00000 mask FFFFFFE00000 uncachable
[    0.000000]   4 base 000100000000 mask FFFFE0000000 write-back
[    0.000000]   5 base 000120000000 mask FFFFF0000000 write-back
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000130000000 aka 4864M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000cfe00000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xcfdf0 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000f5670] f5670
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: 0000000000000000-00000000cfdf0000
[    0.000000]  0000000000 - 00c0000000 page 1G
[    0.000000]  00c0000000 - 00cfc00000 page 2M
[    0.000000]  00cfc00000 - 00cfdf0000 page 4k
[    0.000000] kernel direct mapping tables up to cfdf0000 @ 1fffd000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-0000000130000000
[    0.000000]  0100000000 - 0130000000 page 2M
[    0.000000] kernel direct mapping tables up to 130000000 @ cfdee000-cfdf0000
[    0.000000] RAMDISK: 366ce000 - 3735f000
[    0.000000] ACPI: RSDP 00000000000f7030 00014 (v00 GBT   )
[    0.000000] ACPI: RSDT 00000000cfdf3000 00040 (v01 GBT    GBTUACPI 42302E31 MSFT 01010101)
[    0.000000] ACPI: FACP 00000000cfdf3040 00074 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: DSDT 00000000cfdf30c0 07492 (v01 GBT    GBTUACPI 00001000 MSFT 03000000)
[    0.000000] ACPI: FACS 00000000cfdf0000 00040
[    0.000000] ACPI: SSDT 00000000cfdfa640 0095E (v01 PTLTD  POWERNOW 00000001  LTP 00000001)
[    0.000000] ACPI: HPET 00000000cfdfafc0 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 00000098)
[    0.000000] ACPI: MCFG 00000000cfdfb000 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: TAMG 00000000cfdfb040 0032A (v01 GBT    GBT   B0 5455312E BG?? 53450101)
[    0.000000] ACPI: APIC 00000000cfdfa580 000BC (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: SLIC 00000000cfdf0040 00176 (v01 GBT    GBTUACPI 00000001 MSFT 000F4240)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000130000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000130000000
[    0.000000]   NODE_DATA [000000012fffb000 - 000000012fffffff]
[    0.000000]  [ffffea0000000000-ffffea00043fffff] PMD -> [ffff88012be00000-ffff88012f7fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00130000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000cfdf0
[    0.000000]     0: 0x00100000 -> 0x00130000
[    0.000000] On node 0 totalpages: 1047935
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 6 pages reserved
[    0.000000]   DMA zone: 3921 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 833064 pages, LIFO batch:31
[    0.000000]   Normal zone: 2688 pages used for memmap
[    0.000000]   Normal zone: 193920 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x04] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x05] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x06] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x07] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x05] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x06] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x07] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfed00000
[    0.000000] SMP: Allowing 8 CPUs, 6 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cfdf0000 - 00000000cfdf3000
[    0.000000] PM: Registered nosave memory: 00000000cfdf3000 - 00000000cfe00000
[    0.000000] PM: Registered nosave memory: 00000000cfe00000 - 00000000cff00000
[    0.000000] PM: Registered nosave memory: 00000000cff00000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at cff00000 (gap: cff00000:10100000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff8800cfa00000 s84416 r8192 d22080 u262144
[    0.000000] pcpu-alloc: s84416 r8192 d22080 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1030905
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-11-generic root=UUID=C43EB5173EB50388 loop=/ubuntu/disks/root.disk ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ c4000000 size 32 MB
[    0.000000] Aperture pointing to e820 RAM. Ignoring.
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ c4000000
[    0.000000] PM: Registered nosave memory: 00000000c4000000 - 00000000c8000000
[    0.000000] Memory: 3973552k/4980736k available (5942k kernel code, 788996k absent, 218188k reserved, 5016k data, 956k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 41943040 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration failed
[    0.000000] TSC: Unable to calibrate against PIT
[    0.000000] TSC: using HPET reference calibration
[    0.000000] Detected 3114.029 MHz processor.
[    0.040004] Calibrating delay loop (skipped), value calculated using timer frequency.. 6228.05 BogoMIPS (lpj=31140290)
[    0.040008] pid_max: default: 32768 minimum: 301
[    0.040034] Security Framework initialized
[    0.040048] AppArmor: AppArmor initialized
[    0.040049] Yama: becoming mindful.
[    0.040353] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.041228] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.041607] Mount-cache hash table entries: 256
[    0.041698] Initializing cgroup subsys ns
[    0.041701] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.041703] Initializing cgroup subsys cpuacct
[    0.041706] Initializing cgroup subsys memory
[    0.041712] Initializing cgroup subsys devices
[    0.041714] Initializing cgroup subsys freezer
[    0.041715] Initializing cgroup subsys net_cls
[    0.041717] Initializing cgroup subsys blkio
[    0.041739] tseg: 00cff00000
[    0.041740] CPU: Physical Processor ID: 0
[    0.041742] CPU: Processor Core ID: 0
[    0.041743] mce: CPU supports 6 MCE banks
[    0.041750] using C1E aware idle routine
[    0.044555] ACPI: Core revision 20110112
[    0.060032] ftrace: allocating 24325 entries in 96 pages
[    0.070062] Setting APIC routing to flat
[    0.080450] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.204709] CPU0: AMD Phenom(tm) II X2 550 Processor stepping 03
[    0.210000] Performance Events: AMD PMU driver.
[    0.210000] ... version:                0
[    0.210000] ... bit width:              48
[    0.210000] ... generic registers:      4
[    0.210000] ... value mask:             0000ffffffffffff
[    0.210000] ... max period:             00007fffffffffff
[    0.210000] ... fixed-purpose events:   0
[    0.210000] ... event mask:             000000000000000f
[    0.210000] Booting Node   0, Processors  #1
[    6.943409] CPU1: Not responding.
[    6.943467] Brought up 1 CPUs
[    6.943469] Total of 1 processors activated (6228.05 BogoMIPS).
[    6.945676] devtmpfs: initialized
[    6.946389] print_constraints: dummy: 
[    6.946411] Time: 14:45:46  Date: 09/14/11
[    6.946437] NET: Registered protocol family 16
[    6.946499] node 0 link 0: io port [c000, ffff]
[    6.946501] TOM: 00000000d0000000 aka 3328M
[    6.946503] Fam 10h mmconf [e0000000, e00fffff]
[    6.946504] node 0 link 0: mmio [a0000, bffff]
[    6.946506] node 0 link 0: mmio [d0000000, dfffffff]
[    6.946509] node 0 link 0: mmio [f0000000, fe02ffff]
[    6.946510] node 0 link 0: mmio [e0000000, e03fffff] ==> [e0100000, e03fffff]
[    6.946513] TOM2: 0000000130000000 aka 4864M
[    6.946515] bus: [00, 03] on node 0 link 0
[    6.946517] bus: 00 index 0 [io  0x0000-0xffff]
[    6.946518] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
[    6.946520] bus: 00 index 2 [mem 0xd0000000-0xdfffffff]
[    6.946521] bus: 00 index 3 [mem 0xe0400000-0xffffffff]
[    6.946522] bus: 00 index 4 [mem 0xe0100000-0xe03fffff]
[    6.946524] bus: 00 index 5 [mem 0x130000000-0xfcffffffff]
[    6.946533] Extended Config Space enabled on 1 nodes
[    6.946545] ACPI: bus type pci registered
[    6.946593] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    6.946595] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    6.969873] PCI: Using configuration type 1 for base access
[    6.970384] bio: create slab <bio-0> at 0
[    6.972500] ACPI: EC: Look up EC in DSDT
[    6.976969] ACPI Warning: Incorrect checksum in table [TAMG] - 0xC3, should be 0xC2 (20110112/tbutils-314)
[    6.977076] ACPI: Interpreter enabled
[    6.977079] ACPI: (supports S0 S3 S4 S5)
[    6.977094] ACPI: Using IOAPIC for interrupt routing
[    6.979787] ACPI: No dock devices found.
[    6.979789] HEST: Table not found.
[    6.979792] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    6.979835] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    6.979913] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    6.979915] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    6.979917] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    6.979919] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000dffff]
[    6.979920] pci_root PNP0A03:00: host bridge window [mem 0xd0000000-0xfebfffff]
[    6.979932] pci 0000:00:00.0: [1022:9601] type 0 class 0x000600
[    6.979942] pci 0000:00:00.0: reg 1c: [mem 0xe0000000-0xffffffff 64bit]
[    6.979971] pci 0000:00:02.0: [1022:9603] type 1 class 0x000604
[    6.979993] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    6.979995] pci 0000:00:02.0: PME# disabled
[    6.980000] pci 0000:00:0a.0: [1022:9609] type 1 class 0x000604
[    6.980000] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
[    6.980000] pci 0000:00:0a.0: PME# disabled
[    6.980032] pci 0000:00:11.0: [1002:4390] type 0 class 0x000101
[    6.980050] pci 0000:00:11.0: reg 10: [io  0xff00-0xff07]
[    6.980058] pci 0000:00:11.0: reg 14: [io  0xfe00-0xfe03]
[    6.980067] pci 0000:00:11.0: reg 18: [io  0xfd00-0xfd07]
[    6.980076] pci 0000:00:11.0: reg 1c: [io  0xfc00-0xfc03]
[    6.980085] pci 0000:00:11.0: reg 20: [io  0xfb00-0xfb0f]
[    6.980094] pci 0000:00:11.0: reg 24: [mem 0xfe02f000-0xfe02f3ff]
[    6.980113] pci 0000:00:11.0: set SATA to AHCI mode
[    6.980144] pci 0000:00:12.0: [1002:4397] type 0 class 0x000c03
[    6.980157] pci 0000:00:12.0: reg 10: [mem 0xfe02e000-0xfe02efff]
[    6.980216] pci 0000:00:12.1: [1002:4398] type 0 class 0x000c03
[    6.980228] pci 0000:00:12.1: reg 10: [mem 0xfe02d000-0xfe02dfff]
[    6.980293] pci 0000:00:12.2: [1002:4396] type 0 class 0x000c03
[    6.980310] pci 0000:00:12.2: reg 10: [mem 0xfe02c000-0xfe02c0ff]
[    6.980376] pci 0000:00:12.2: supports D1 D2
[    6.980377] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    6.980381] pci 0000:00:12.2: PME# disabled
[    6.980402] pci 0000:00:13.0: [1002:4397] type 0 class 0x000c03
[    6.980414] pci 0000:00:13.0: reg 10: [mem 0xfe02b000-0xfe02bfff]
[    6.980473] pci 0000:00:13.1: [1002:4398] type 0 class 0x000c03
[    6.981967] pci 0000:00:13.1: reg 10: [mem 0xfe02a000-0xfe02afff]
[    6.982042] pci 0000:00:13.2: [1002:4396] type 0 class 0x000c03
[    6.982061] pci 0000:00:13.2: reg 10: [mem 0xfe029000-0xfe0290ff]
[    6.982126] pci 0000:00:13.2: supports D1 D2
[    6.982128] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    6.982132] pci 0000:00:13.2: PME# disabled
[    6.982155] pci 0000:00:14.0: [1002:4385] type 0 class 0x000c05
[    6.982241] pci 0000:00:14.1: [1002:439c] type 0 class 0x000101
[    6.982256] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
[    6.982265] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
[    6.982273] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
[    6.982282] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
[    6.982291] pci 0000:00:14.1: reg 20: [io  0xfa00-0xfa0f]
[    6.982336] pci 0000:00:14.2: [1002:4383] type 0 class 0x000403
[    6.982356] pci 0000:00:14.2: reg 10: [mem 0xfe024000-0xfe027fff 64bit]
[    6.982410] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    6.982413] pci 0000:00:14.2: PME# disabled
[    6.982425] pci 0000:00:14.3: [1002:439d] type 0 class 0x000601
[    6.982494] pci 0000:00:14.4: [1002:4384] type 1 class 0x000604
[    6.982538] pci 0000:00:14.5: [1002:4399] type 0 class 0x000c03
[    6.982550] pci 0000:00:14.5: reg 10: [mem 0xfe028000-0xfe028fff]
[    6.982611] pci 0000:00:18.0: [1022:1200] type 0 class 0x000600
[    6.982624] pci 0000:00:18.1: [1022:1201] type 0 class 0x000600
[    6.982634] pci 0000:00:18.2: [1022:1202] type 0 class 0x000600
[    6.982645] pci 0000:00:18.3: [1022:1203] type 0 class 0x000600
[    6.982656] pci 0000:00:18.4: [1022:1204] type 0 class 0x000600
[    6.982699] pci 0000:01:00.0: [1002:6719] type 0 class 0x000300
[    6.982711] pci 0000:01:00.0: reg 10: [mem 0xd0000000-0xdfffffff 64bit pref]
[    6.982720] pci 0000:01:00.0: reg 18: [mem 0xfdfc0000-0xfdfdffff 64bit]
[    6.982726] pci 0000:01:00.0: reg 20: [io  0xee00-0xeeff]
[    6.982737] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    6.982753] pci 0000:01:00.0: supports D1 D2
[    6.982770] pci 0000:01:00.1: [1002:aa80] type 0 class 0x000403
[    6.982782] pci 0000:01:00.1: reg 10: [mem 0xfdffc000-0xfdffffff 64bit]
[    6.982820] pci 0000:01:00.1: supports D1 D2
[    6.982853] System has AMD C1E enabled
[    6.982867] Switch to broadcast mode on CPU0
[    7.000027] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    7.000032] pci 0000:00:02.0:   bridge window [io  0xe000-0xefff]
[    7.000035] pci 0000:00:02.0:   bridge window [mem 0xfdf00000-0xfdffffff]
[    7.000038] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    7.000080] pci 0000:02:00.0: [10ec:8168] type 0 class 0x000200
[    7.000094] pci 0000:02:00.0: reg 10: [io  0xde00-0xdeff]
[    7.000113] pci 0000:02:00.0: reg 18: [mem 0xfdbff000-0xfdbfffff 64bit pref]
[    7.000125] pci 0000:02:00.0: reg 20: [mem 0xfdbe0000-0xfdbeffff 64bit pref]
[    7.000134] pci 0000:02:00.0: reg 30: [mem 0x00000000-0x0000ffff pref]
[    7.000163] pci 0000:02:00.0: supports D1 D2
[    7.000165] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    7.000168] pci 0000:02:00.0: PME# disabled
[    7.020029] pci 0000:00:0a.0: PCI bridge to [bus 02-02]
[    7.020034] pci 0000:00:0a.0:   bridge window [io  0xd000-0xdfff]
[    7.020036] pci 0000:00:0a.0:   bridge window [mem 0xfde00000-0xfdefffff]
[    7.020039] pci 0000:00:0a.0:   bridge window [mem 0xfdb00000-0xfdbfffff 64bit pref]
[    7.020096] pci 0000:03:0e.0: [104c:8024] type 0 class 0x000c00
[    7.020119] pci 0000:03:0e.0: reg 10: [mem 0xfddff000-0xfddff7ff]
[    7.020131] pci 0000:03:0e.0: reg 14: [mem 0xfddf8000-0xfddfbfff]
[    7.020210] pci 0000:03:0e.0: supports D1 D2
[    7.020212] pci 0000:03:0e.0: PME# supported from D0 D1 D2 D3hot
[    7.020216] pci 0000:03:0e.0: PME# disabled
[    7.020249] pci 0000:00:14.4: PCI bridge to [bus 03-03] (subtractive decode)
[    7.020253] pci 0000:00:14.4:   bridge window [io  0xc000-0xcfff]
[    7.020257] pci 0000:00:14.4:   bridge window [mem 0xfdd00000-0xfddfffff]
[    7.020260] pci 0000:00:14.4:   bridge window [mem 0xfdc00000-0xfdcfffff pref]
[    7.020263] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    7.020264] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    7.020266] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    7.020268] pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
[    7.020270] pci 0000:00:14.4:   bridge window [mem 0xd0000000-0xfebfffff] (subtractive decode)
[    7.020284] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    7.020463] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    7.020504] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[    7.020531] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCEA._PRT]
[    7.020554]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    7.033985] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    7.034017] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    7.034045] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    7.034072] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    7.034099] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    7.034125] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    7.034152] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    7.034178] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    7.034262] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    7.034265] vgaarb: loaded
[    7.034381] SCSI subsystem initialized
[    7.034427] libata version 3.00 loaded.
[    7.034458] usbcore: registered new interface driver usbfs
[    7.034466] usbcore: registered new interface driver hub
[    7.034480] usbcore: registered new device driver usb
[    7.034603] wmi: Mapper loaded
[    7.034604] PCI: Using ACPI for IRQ routing
[    7.034606] PCI: pci_cache_line_size set to 64 bytes
[    7.034612] pci 0000:00:00.0: no compatible bridge window for [mem 0xe0000000-0xffffffff 64bit]
[    7.034677] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    7.034679] reserve RAM buffer: 00000000cfdf0000 - 00000000cfffffff 
[    7.034747] NetLabel: Initializing
[    7.034748] NetLabel:  domain hash size = 128
[    7.034749] NetLabel:  protocols = UNLABELED CIPSOv4
[    7.034757] NetLabel:  unlabeled traffic allowed by default
[    7.034784] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    7.034788] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    7.038099] Switching to clocksource hpet
[    7.038116] Switched to NOHz mode on CPU #0
[    7.038116] AppArmor: AppArmor Filesystem Enabled
[    7.038116] pnp: PnP ACPI init
[    7.038116] ACPI: bus type pnp registered
[    7.038116] pnp 00:00: [bus 00-ff]
[    7.038116] pnp 00:00: [io  0x0cf8-0x0cff]
[    7.038116] pnp 00:00: [io  0x0000-0x0cf7 window]
[    7.038116] pnp 00:00: [io  0x0d00-0xffff window]
[    7.038116] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    7.038116] pnp 00:00: [mem 0x000c0000-0x000dffff window]
[    7.038116] pnp 00:00: [mem 0xd0000000-0xfebfffff window]
[    7.038116] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    7.038116] pnp 00:01: [io  0x0010-0x001f]
[    7.038116] pnp 00:01: [io  0x0022-0x003f]
[    7.038116] pnp 00:01: [io  0x0044-0x005f]
[    7.038116] pnp 00:01: [io  0x0062-0x0063]
[    7.038116] pnp 00:01: [io  0x0065-0x006f]
[    7.038116] pnp 00:01: [io  0x0074-0x007f]
[    7.038116] pnp 00:01: [io  0x0091-0x0093]
[    7.038116] pnp 00:01: [io  0x00a2-0x00bf]
[    7.038116] pnp 00:01: [io  0x00e0-0x00ef]
[    7.038116] pnp 00:01: [io  0x04d0-0x04d1]
[    7.038116] pnp 00:01: [io  0x0220-0x0225]
[    7.038116] pnp 00:01: [io  0x0290-0x0294]
[    7.038116] system 00:01: [io  0x04d0-0x04d1] has been reserved
[    7.038116] system 00:01: [io  0x0220-0x0225] has been reserved
[    7.038116] system 00:01: [io  0x0290-0x0294] has been reserved
[    7.038116] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    7.038116] pnp 00:02: [io  0x4100-0x411f]
[    7.038116] pnp 00:02: [io  0x0228-0x022f]
[    7.038116] pnp 00:02: [io  0x040b]
[    7.038116] pnp 00:02: [io  0x04d6]
[    7.038116] pnp 00:02: [io  0x0c00-0x0c01]
[    7.038116] pnp 00:02: [io  0x0c14]
[    7.038116] pnp 00:02: [io  0x0c50-0x0c52]
[    7.038116] pnp 00:02: [io  0x0c6c-0x0c6d]
[    7.038116] pnp 00:02: [io  0x0c6f]
[    7.038116] pnp 00:02: [io  0x0cd0-0x0cd1]
[    7.038116] pnp 00:02: [io  0x0cd2-0x0cd3]
[    7.038116] pnp 00:02: [io  0x0cd4-0x0cdf]
[    7.038116] pnp 00:02: [io  0x4000-0x40fe]
[    7.038116] pnp 00:02: [io  0x4210-0x4217]
[    7.038116] pnp 00:02: [io  0x0b00-0x0b0f]
[    7.038116] pnp 00:02: [io  0x0b10-0x0b1f]
[    7.038116] pnp 00:02: [io  0x0b20-0x0b3f]
[    7.038116] pnp 00:02: [mem 0x00000000-0x00000fff window]
[    7.038116] pnp 00:02: [mem 0xfee00400-0xfee00fff window]
[    7.038116] pnp 00:02: disabling [mem 0x00000000-0x00000fff window] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    7.038116] pnp 00:02: disabling [mem 0x00000000-0x00000fff window disabled] because it overlaps 0000:01:00.0 BAR 6 [mem 0x00000000-0x0001ffff pref]
[    7.038116] pnp 00:02: disabling [mem 0x00000000-0x00000fff window disabled] because it overlaps 0000:02:00.0 BAR 6 [mem 0x00000000-0x0000ffff pref]
[    7.038116] system 00:02: [io  0x4100-0x411f] has been reserved
[    7.038116] system 00:02: [io  0x0228-0x022f] has been reserved
[    7.038116] system 00:02: [io  0x040b] has been reserved
[    7.038116] system 00:02: [io  0x04d6] has been reserved
[    7.038116] system 00:02: [io  0x0c00-0x0c01] has been reserved
[    7.038116] system 00:02: [io  0x0c14] has been reserved
[    7.038116] system 00:02: [io  0x0c50-0x0c52] has been reserved
[    7.038116] system 00:02: [io  0x0c6c-0x0c6d] has been reserved
[    7.038116] system 00:02: [io  0x0c6f] has been reserved
[    7.038116] system 00:02: [io  0x0cd0-0x0cd1] has been reserved
[    7.038116] system 00:02: [io  0x0cd2-0x0cd3] has been reserved
[    7.038116] system 00:02: [io  0x0cd4-0x0cdf] has been reserved
[    7.038116] system 00:02: [io  0x4000-0x40fe] has been reserved
[    7.038116] system 00:02: [io  0x4210-0x4217] has been reserved
[    7.038116] system 00:02: [io  0x0b00-0x0b0f] has been reserved
[    7.038116] system 00:02: [io  0x0b10-0x0b1f] has been reserved
[    7.038116] system 00:02: [io  0x0b20-0x0b3f] has been reserved
[    7.038116] system 00:02: [mem 0xfee00400-0xfee00fff window] has been reserved
[    7.038116] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    7.038116] pnp 00:03: [dma 4]
[    7.038116] pnp 00:03: [io  0x0000-0x000f]
[    7.038116] pnp 00:03: [io  0x0080-0x0090]
[    7.038116] pnp 00:03: [io  0x0094-0x009f]
[    7.038116] pnp 00:03: [io  0x00c0-0x00df]
[    7.038116] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
[    7.038116] pnp 00:04: [irq 0 disabled]
[    7.038116] pnp 00:04: [irq 8]
[    7.038116] pnp 00:04: [mem 0xfed00000-0xfed003ff]
[    7.038116] pnp 00:04: Plug and Play ACPI device, IDs PNP0103 (active)
[    7.038116] pnp 00:05: [io  0x0070-0x0073]
[    7.038116] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    7.038116] pnp 00:06: [io  0x0061]
[    7.038116] pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
[    7.038116] pnp 00:07: [io  0x00f0-0x00ff]
[    7.038116] pnp 00:07: [irq 13]
[    7.038116] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
[    7.038116] pnp 00:08: [io  0x03f8-0x03ff]
[    7.038116] pnp 00:08: [irq 4]
[    7.038116] pnp 00:08: Plug and Play ACPI device, IDs PNP0501 (active)
[    7.038116] pnp 00:09: [io  0x0378-0x037f]
[    7.038116] pnp 00:09: [irq 7]
[    7.038116] pnp 00:09: Plug and Play ACPI device, IDs PNP0400 (active)
[    7.038116] pnp 00:0a: [mem 0xe0000000-0xefffffff]
[    7.038116] system 00:0a: [mem 0xe0000000-0xefffffff] has been reserved
[    7.038116] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    7.038116] pnp 00:0b: [mem 0x000cfa00-0x000cffff]
[    7.038116] pnp 00:0b: [mem 0x000f0000-0x000f7fff]
[    7.038116] pnp 00:0b: [mem 0x000f8000-0x000fbfff]
[    7.038116] pnp 00:0b: [mem 0x000fc000-0x000fffff]
[    7.038116] pnp 00:0b: [mem 0xcfdf0000-0xcfdfffff]
[    7.038116] pnp 00:0b: [mem 0xffff0000-0xffffffff]
[    7.038116] pnp 00:0b: [mem 0x00000000-0x0009ffff]
[    7.038116] pnp 00:0b: [mem 0x00100000-0xcfdeffff]
[    7.038116] pnp 00:0b: [mem 0xcfe00000-0xcfefffff]
[    7.038116] pnp 00:0b: [mem 0xcff00000-0xcfffffff]
[    7.038116] pnp 00:0b: [mem 0x00000000-0xffffffffffffffff disabled]
[    7.038116] pnp 00:0b: [mem 0xfec00000-0xfec00fff]
[    7.038116] pnp 00:0b: [mem 0xfee00000-0xfee00fff]
[    7.038116] pnp 00:0b: [mem 0xfff80000-0xfffeffff]
[    7.038116] pnp 00:0b: disabling [mem 0x000cfa00-0x000cffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    7.038116] pnp 00:0b: disabling [mem 0x000f0000-0x000f7fff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    7.038116] pnp 00:0b: disabling [mem 0x000f8000-0x000fbfff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    7.038116] pnp 00:0b: disabling [mem 0x000fc000-0x000fffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    7.038116] pnp 00:0b: disabling [mem 0x00000000-0x0009ffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    7.038116] pnp 00:0b: disabling [mem 0x00100000-0xcfdeffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    7.038116] system 00:0b: [mem 0xcfdf0000-0xcfdfffff] could not be reserved
[    7.038116] system 00:0b: [mem 0xffff0000-0xffffffff] has been reserved
[    7.038116] system 00:0b: [mem 0xcfe00000-0xcfefffff] has been reserved
[    7.038116] system 00:0b: [mem 0xcff00000-0xcfffffff] could not be reserved
[    7.038116] system 00:0b: [mem 0xfec00000-0xfec00fff] could not be reserved
[    7.038116] system 00:0b: [mem 0xfee00000-0xfee00fff] could not be reserved
[    7.038116] system 00:0b: [mem 0xfff80000-0xfffeffff] has been reserved
[    7.038116] system 00:0b: Plug and Play ACPI device, IDs PNP0c01 (active)
[    7.038116] pnp: PnP ACPI: found 12 devices
[    7.038116] ACPI: ACPI bus type pnp unregistered
[    7.044409] pci 0000:01:00.0: BAR 6: assigned [mem 0xfdf00000-0xfdf1ffff pref]
[    7.044413] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    7.044416] pci 0000:00:02.0:   bridge window [io  0xe000-0xefff]
[    7.044418] pci 0000:00:02.0:   bridge window [mem 0xfdf00000-0xfdffffff]
[    7.044420] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    7.044424] pci 0000:02:00.0: BAR 6: assigned [mem 0xfdb00000-0xfdb0ffff pref]
[    7.044426] pci 0000:00:0a.0: PCI bridge to [bus 02-02]
[    7.044428] pci 0000:00:0a.0:   bridge window [io  0xd000-0xdfff]
[    7.044430] pci 0000:00:0a.0:   bridge window [mem 0xfde00000-0xfdefffff]
[    7.044432] pci 0000:00:0a.0:   bridge window [mem 0xfdb00000-0xfdbfffff 64bit pref]
[    7.044435] pci 0000:00:14.4: PCI bridge to [bus 03-03]
[    7.044437] pci 0000:00:14.4:   bridge window [io  0xc000-0xcfff]
[    7.044442] pci 0000:00:14.4:   bridge window [mem 0xfdd00000-0xfddfffff]
[    7.044445] pci 0000:00:14.4:   bridge window [mem 0xfdc00000-0xfdcfffff pref]
[    7.044469] pci 0000:00:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    7.044472] pci 0000:00:02.0: setting latency timer to 64
[    7.044476] pci 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    7.044478] pci 0000:00:0a.0: setting latency timer to 64
[    7.044485] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    7.044486] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    7.044488] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    7.044489] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000dffff]
[    7.044491] pci_bus 0000:00: resource 8 [mem 0xd0000000-0xfebfffff]
[    7.044493] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    7.044494] pci_bus 0000:01: resource 1 [mem 0xfdf00000-0xfdffffff]
[    7.044496] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    7.044497] pci_bus 0000:02: resource 0 [io  0xd000-0xdfff]
[    7.044499] pci_bus 0000:02: resource 1 [mem 0xfde00000-0xfdefffff]
[    7.044500] pci_bus 0000:02: resource 2 [mem 0xfdb00000-0xfdbfffff 64bit pref]
[    7.044502] pci_bus 0000:03: resource 0 [io  0xc000-0xcfff]
[    7.044503] pci_bus 0000:03: resource 1 [mem 0xfdd00000-0xfddfffff]
[    7.044505] pci_bus 0000:03: resource 2 [mem 0xfdc00000-0xfdcfffff pref]
[    7.044506] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    7.044508] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    7.044509] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    7.044511] pci_bus 0000:03: resource 7 [mem 0x000c0000-0x000dffff]
[    7.044512] pci_bus 0000:03: resource 8 [mem 0xd0000000-0xfebfffff]
[    7.044543] NET: Registered protocol family 2
[    7.044652] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    7.045436] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    7.048823] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    7.049141] TCP: Hash tables configured (established 524288 bind 65536)
[    7.049143] TCP reno registered
[    7.049150] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    7.049180] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    7.049299] NET: Registered protocol family 1
[    7.150067] pci 0000:01:00.0: Boot video device
[    7.150078] PCI: CLS 4 bytes, default 64
[    7.150222] Trying to unpack rootfs image as initramfs...
[    7.190331] PCI-DMA: Disabling AGP.
[    7.190407] PCI-DMA: aperture base @ c4000000 size 65536 KB
[    7.190408] PCI-DMA: using GART IOMMU.
[    7.190410] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    7.193760] audit: initializing netlink socket (disabled)
[    7.193769] type=2000 audit(1316011546.190:1): initialized
[    7.220294] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    7.221462] VFS: Disk quotas dquot_6.5.2
[    7.221499] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    7.221917] fuse init (API version 7.16)
[    7.221973] msgmni has been set to 7889
[    7.230248] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    7.230265] io scheduler noop registered
[    7.230266] io scheduler deadline registered
[    7.230294] io scheduler cfq registered (default)
[    7.230386] pcieport 0000:00:02.0: setting latency timer to 64
[    7.230411] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    7.230461] pcieport 0000:00:0a.0: setting latency timer to 64
[    7.230479] pcieport 0000:00:0a.0: irq 41 for MSI/MSI-X
[    7.230524] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    7.230539] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    7.230636] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    7.230640] ACPI: Power Button [PWRB]
[    7.230674] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    7.230676] ACPI: Power Button [PWRF]
[    7.230788] ACPI: acpi_idle registered with cpuidle
[    7.230801] ACPI: processor limited to max C-state 1
[    7.231735] ERST: Table is not found!
[    7.231781] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    7.252395] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    7.301376] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    7.320480] Linux agpgart interface v0.103
[    7.321201] brd: module loaded
[    7.321533] loop: module loaded
[    7.321598] i2c-core: driver [adp5520] using legacy suspend method
[    7.321600] i2c-core: driver [adp5520] using legacy resume method
[    7.321738] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.321987] Fixed MDIO Bus: probed
[    7.322006] PPP generic driver version 2.4.2
[    7.322031] tun: Universal TUN/TAP device driver, 1.6
[    7.322033] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    7.322086] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    7.322115] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    7.322126] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    7.322151] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    7.322162] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    7.322184] ehci_hcd 0000:00:12.2: debug port 1
[    7.322210] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe02c000
[    7.340094] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    7.340211] hub 1-0:1.0: USB hub found
[    7.340214] hub 1-0:1.0: 6 ports detected
[    7.350167] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    7.350188] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    7.350234] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    7.350245] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    7.350265] ehci_hcd 0000:00:13.2: debug port 1
[    7.350292] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe029000
[    7.370137] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    7.370258] hub 2-0:1.0: USB hub found
[    7.370262] hub 2-0:1.0: 6 ports detected
[    7.370347] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    7.380252] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.380275] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    7.380320] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    7.380355] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfe02e000
[    7.391821] Freeing initrd memory: 12868k freed
[    7.444194] hub 3-0:1.0: USB hub found
[    7.444200] hub 3-0:1.0: 3 ports detected
[    7.444302] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.444322] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    7.444352] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    7.444372] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfe02d000
[    7.504119] hub 4-0:1.0: USB hub found
[    7.504125] hub 4-0:1.0: 3 ports detected
[    7.504203] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    7.504216] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    7.504243] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    7.504274] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe02b000
[    7.564114] hub 5-0:1.0: USB hub found
[    7.564120] hub 5-0:1.0: 3 ports detected
[    7.564192] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    7.564204] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    7.564233] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    7.564248] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfe02a000
[    7.624114] hub 6-0:1.0: USB hub found
[    7.624120] hub 6-0:1.0: 3 ports detected
[    7.624192] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    7.624207] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    7.624232] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    7.624246] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfe028000
[    7.660045] usb 1-3: new high speed USB device using ehci_hcd and address 2
[    7.684118] hub 7-0:1.0: USB hub found
[    7.684124] hub 7-0:1.0: 2 ports detected
[    7.684178] uhci_hcd: USB Universal Host Controller Interface driver
[    7.684260] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    7.717210] i8042: Failed to disable AUX port, but continuing anyway... Is this a SiS?
[    7.717211] i8042: If AUX port is really absent please use the 'i8042.noaux' option
[    7.930037] usb 1-4: new high speed USB device using ehci_hcd and address 3
[    7.960127] serio: i8042 KBD port at 0x60,0x64 irq 1
[    7.960206] mousedev: PS/2 mouse device common for all mice
[    7.960292] rtc_cmos 00:05: RTC can wake from S4
[    7.960326] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    7.960356] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    7.960423] device-mapper: uevent: version 1.0.3
[    7.960471] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    7.960505] device-mapper: multipath: version 1.2.0 loaded
[    7.960507] device-mapper: multipath round-robin: version 1.0.0 loaded
[    7.960575] cpuidle: using governor ladder
[    7.960576] cpuidle: using governor menu
[    7.960729] TCP cubic registered
[    7.960799] NET: Registered protocol family 10
[    7.961146] NET: Registered protocol family 17
[    7.961156] Registering the dns_resolver key type
[    7.961169] powernow-k8: Found 1 AMD Phenom(tm) II X2 550 Processor (1 cpu cores) (version 2.20.00)
[    7.961199] powernow-k8:    0 : pstate 0 (3100 MHz)
[    7.961200] powernow-k8:    1 : pstate 1 (2400 MHz)
[    7.961202] powernow-k8:    2 : pstate 2 (1900 MHz)
[    7.961203] powernow-k8:    3 : pstate 3 (800 MHz)
[    7.961281] PM: Hibernation image not present or could not be loaded.
[    7.961290] registered taskstats version 1
[    7.961489]   Magic number: 11:789:788
[    7.961564] rtc_cmos 00:05: setting system clock to 2011-09-14 14:45:47 UTC (1316011547)
[    7.961566] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    7.961567] EDD information not available.
[    7.962759] Freeing unused kernel memory: 956k freed
[    7.963048] Write protecting the kernel read-only data: 10240k
[    7.963574] Freeing unused kernel memory: 184k freed
[    7.967131] Freeing unused kernel memory: 1440k freed
[    7.979188] <30>udev[98]: starting version 167
[    8.111524] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    8.111543] r8169 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    8.111576] r8169 0000:02:00.0: setting latency timer to 64
[    8.111616] r8169 0000:02:00.0: irq 42 for MSI/MSI-X
[    8.111926] r8169 0000:02:00.0: eth0: RTL8168c/8111c at 0xffffc90000668000, 00:24:1d:d9:7d:7b, XID 1c4000c0 IRQ 42
[    8.114436] ahci 0000:00:11.0: version 3.0
[    8.114455] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    8.114547] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    8.114550] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
[    8.115084] firewire_ohci 0000:03:0e.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    8.115129] scsi0 : ahci
[    8.115229] scsi1 : ahci
[    8.115284] scsi2 : ahci
[    8.115338] scsi3 : ahci
[    8.115412] ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 22
[    8.115414] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 22
[    8.115417] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 22
[    8.115420] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 22
[    8.115961] scsi4 : pata_atiixp
[    8.116036] scsi5 : pata_atiixp
[    8.116427] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfa00 irq 14
[    8.116429] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfa08 irq 15
[    8.170102] firewire_ohci: Added fw-ohci device 0000:03:0e.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
[    8.190031] Refined TSC clocksource calibration: 3114.072 MHz.
[    8.190036] Switching to clocksource tsc
[    8.460074] ata4: SATA link down (SStatus 0 SControl 300)
[    8.660084] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    8.660106] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    8.660123] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    8.660878] ata2.00: ATA-8: WDC WD6400AARS-00Y5B1, 80.00A80, max UDMA/133
[    8.660880] ata2.00: 1250263728 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    8.662327] ata2.00: configured for UDMA/133
[    8.663077] ata3.00: ATAPI: HL-DT-ST DVDRAM GH22NS50, TN02, max UDMA/100
[    8.665834] ata1.00: ATA-8: SAMSUNG HD103SJ, 1AJ10001, max UDMA/133
[    8.665837] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    8.666899] ata3.00: configured for UDMA/100
[    8.670063] firewire_core: created device fw0: GUID 00e148170000241d, S400
[    8.671609] ata1.00: configured for UDMA/133
[    8.671678] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HD103SJ  1AJ1 PQ: 0 ANSI: 5
[    8.671775] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    8.671846] scsi 1:0:0:0: Direct-Access     ATA      WDC WD6400AARS-0 80.0 PQ: 0 ANSI: 5
[    8.671917] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    8.672061] sd 1:0:0:0: [sdb] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
[    8.672089] sd 1:0:0:0: [sdb] Write Protect is off
[    8.672091] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    8.672103] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.672280] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    8.672306] sd 0:0:0:0: [sda] Write Protect is off
[    8.672308] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    8.672330] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.675488] scsi 2:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH22NS50  TN02 PQ: 0 ANSI: 5
[    8.683886] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    8.683888] cdrom: Uniform CD-ROM driver Revision: 3.20
[    8.683955] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    8.683990] sr 2:0:0:0: Attached scsi generic sg2 type 5
[    8.702039]  sda: sda1 sda2 < sda5 >
[    8.702212] sd 0:0:0:0: [sda] Attached SCSI disk
[    8.770023] usb 4-3: new full speed USB device using ohci_hcd and address 2
[    8.982347] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.0/input/input2
[    8.982442] generic-usb 0003:046D:C52E.0001: input,hidraw0: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:12.1-3/input0
[    8.987476] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.1/input/input3
[    8.987719] generic-usb 0003:046D:C52E.0002: input,hiddev0,hidraw1: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:12.1-3/input1
[    8.987806] usbcore: registered new interface driver usbhid
[    8.987807] usbhid: USB HID core driver
[    9.159535]  sdb: sdb1
[    9.159701] sd 1:0:0:0: [sdb] Attached SCSI disk
[    9.180004] ata2.00: exception Emask 0x50 SAct 0x0 SErr 0x280900 action 0x6 frozen
[    9.180004] ata2.00: irq_stat 0x08000000, interface fatal error
[    9.180004] ata2: SError: { UnrecovData HostInt 10B8B BadCRC }
[    9.180004] ata2.00: failed command: IDENTIFY DEVICE
[    9.180004] ata2.00: cmd ec/00:01:00:00:00/00:00:00:00:00/00 tag 0 pio 512 in
[    9.180004]          res 40/00:04:00:00:00/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
[    9.180004] ata2.00: status: { DRDY }
[    9.180004] ata2: hard resetting link
[    9.300023] usb 6-2: new full speed USB device using ohci_hcd and address 2
[    9.720036] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    9.723595] ata2.00: configured for UDMA/133
[    9.723605] ata2: EH complete
[    9.731046] EXT4-fs (loop0): INFO: recovery required on readonly filesystem
[    9.731048] EXT4-fs (loop0): write access will be enabled during recovery
[    9.735389] ata2.00: exception Emask 0x50 SAct 0x1 SErr 0x280900 action 0x6 frozen
[    9.735391] ata2.00: irq_stat 0x08000000, interface fatal error
[    9.735393] ata2: SError: { UnrecovData HostInt 10B8B BadCRC }
[    9.735396] ata2.00: failed command: READ FPDMA QUEUED
[    9.735400] ata2.00: cmd 60/08:00:00:00:00/00:00:00:00:00/40 tag 0 ncq 4096 in
[    9.735401]          res 40/00:04:00:00:00/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
[    9.735403] ata2.00: status: { DRDY }
[    9.735406] ata2: hard resetting link
[   10.280030] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   10.283131] ata2.00: configured for UDMA/133
[   10.283140] ata2: EH complete
[   10.326568] ata2.00: exception Emask 0x50 SAct 0x1 SErr 0x280900 action 0x6 frozen
[   10.326571] ata2.00: irq_stat 0x08000000, interface fatal error
[   10.326574] ata2: SError: { UnrecovData HostInt 10B8B BadCRC }
[   10.326576] ata2.00: failed command: READ FPDMA QUEUED
[   10.326580] ata2.00: cmd 60/08:00:a8:81:85/00:00:4a:00:00/40 tag 0 ncq 4096 in
[   10.326581]          res 40/00:04:a8:81:85/00:00:4a:00:00/40 Emask 0x50 (ATA bus error)
[   10.326583] ata2.00: status: { DRDY }
[   10.326586] ata2: hard resetting link
[   10.715903] EXT4-fs (loop0): orphan cleanup on readonly fs
[   10.715910] EXT4-fs (loop0): ext4_orphan_cleanup: deleting unreferenced inode 266358
[   10.715963] EXT4-fs (loop0): 1 orphan inode deleted
[   10.715965] EXT4-fs (loop0): recovery complete
[   10.716486] EXT4-fs (loop0): mounted filesystem with ordered data mode. Opts: (null)
[   10.870036] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   10.872750] ata2.00: configured for UDMA/133
[   10.872758] ata2: EH complete
[   10.893309] ata2: limiting SATA link speed to 1.5 Gbps
[   10.893311] ata2.00: exception Emask 0x50 SAct 0x1 SErr 0x280900 action 0x6 frozen
[   10.893314] ata2.00: irq_stat 0x08000000, interface fatal error
[   10.893316] ata2: SError: { UnrecovData HostInt 10B8B BadCRC }
[   10.893318] ata2.00: failed command: READ FPDMA QUEUED
[   10.893322] ata2.00: cmd 60/08:00:a8:81:85/00:00:4a:00:00/40 tag 0 ncq 4096 in
[   10.893323]          res 40/00:04:a8:81:85/00:00:4a:00:00/40 Emask 0x50 (ATA bus error)
[   10.893325] ata2.00: status: { DRDY }
[   10.893328] ata2: hard resetting link
[   11.440037] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   11.441140] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[   11.441142] ata2.00: revalidation failed (errno=-5)
[   12.968229] <30>udev[427]: starting version 167
[   13.527596] parport_pc 00:09: reported by Plug and Play ACPI
[   13.527648] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   13.647714] lp0: using parport0 (interrupt-driven).
[   13.652430] ppdev: user-space parallel port driver
[   13.907132] Linux video capture interface: v2.00
[   13.918599] ACPI: resource piix4_smbus [io  0x0b00-0x0b07] conflicts with ACPI region SOR1 [io 0xb00-0xb0f]
[   13.918601] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   13.930799] MCE: In-kernel MCE decoding enabled.
[   14.018908] EDAC MC: Ver: 2.1.0 Jul 29 2011
[   14.047489] cfg80211: Calling CRDA to update world regulatory domain
[   14.059587] Bluetooth: Core ver 2.15
[   14.059620] NET: Registered protocol family 31
[   14.059622] Bluetooth: HCI device and connection manager initialized
[   14.059624] Bluetooth: HCI socket layer initialized
[   14.071680] uvcvideo: Found UVC 1.00 device USB Video Camera (0471:0334)
[   14.073746] input: USB Video Camera as /devices/pci0000:00/0000:00:12.2/usb1/1-3/1-3:1.0/input/input4
[   14.074151] usbcore: registered new interface driver uvcvideo
[   14.074153] USB Video Class driver (v1.0.0)
[   14.108858] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
[   14.109762] SP5100 TCO timer: mmio address 0xfec000f0 already in use
[   14.114973] EDAC amd64_edac: v3.3.0
[   14.115017] EDAC amd64: DRAM ECC disabled.
[   14.115020] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   14.115021]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   14.115022]  (Note that use of the override may cause unknown side effects.)
[   14.229384] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   14.229933] usbcore: registered new interface driver btusb
[   14.644568] usbcore: registered new interface driver snd-usb-audio
[   14.713262] phy0 -> rt2500usb_init_eeprom: Error - Invalid RT chipset detected.
[   14.713305] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device.
[   14.713403] usbcore: registered new interface driver rt2500usb
[   14.771226] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.834701] cfg80211: World regulatory domain updated:
[   14.834703] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   14.834706] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.834708] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.834709] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.834711] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.834712] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.850102] hda-intel: Enable sync_write for AMD chipset
[   15.018885] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   15.018943] HDA Intel 0000:01:00.1: irq 43 for MSI/MSI-X
[   15.018962] HDA Intel 0000:01:00.1: setting latency timer to 64
[   15.020142] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   15.020145] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.020147] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   15.020148] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.020150] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   15.020152] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.020153] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   15.020155] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.020156] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   15.020158] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.020176] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   15.020178] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.020179] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   15.020181] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.020182] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   15.020184] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.020185] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   15.020187] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.020189] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   15.020190] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.020192] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   15.020193] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.020195] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   15.020197] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.020198] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   15.020200] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.020201] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   15.020203] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.052078] hda-intel: Enable sync_write for AMD chipset
[   15.116546] ieee80211 phy1: Selected rate control algorithm 'minstrel_ht'
[   15.116939] Registered led device: rt73usb-phy1::radio
[   15.116953] Registered led device: rt73usb-phy1::assoc
[   15.116966] Registered led device: rt73usb-phy1::quality
[   15.117503] usbcore: registered new interface driver rt73usb
[   16.249803] Adding 262136k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:262136k 
[   16.299144] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro
[   16.440022] ata2: hard resetting link
[   16.923360] type=1400 audit(1316000756.458:2): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=879 comm="apparmor_parser"
[   16.990236] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   16.991314] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[   16.991316] ata2.00: revalidation failed (errno=-5)
[   17.261284] type=1400 audit(1316000756.798:3): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=880 comm="apparmor_parser"
[   17.261362] type=1400 audit(1316000756.798:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=880 comm="apparmor_parser"
[   17.261414] type=1400 audit(1316000756.798:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=880 comm="apparmor_parser"
[   17.617574] r8169 0000:02:00.0: eth0: link down
[   17.620495] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.734556] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.990089] ata2: hard resetting link
[   22.540100] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   22.543325] ata2.00: configured for UDMA/133
[   22.543334] ata2: EH complete
[   22.560794] ata2.00: exception Emask 0x50 SAct 0x1 SErr 0x280901 action 0x6 frozen
[   22.560836] ata2.00: irq_stat 0x08000000, interface fatal error
[   22.560876] ata2: SError: { RecovData UnrecovData HostInt 10B8B BadCRC }
[   22.560915] ata2.00: failed command: READ FPDMA QUEUED
[   22.560956] ata2.00: cmd 60/08:00:a8:81:85/00:00:4a:00:00/40 tag 0 ncq 4096 in
[   22.560957]          res 40/00:04:a8:81:85/00:00:4a:00:00/40 Emask 0x50 (ATA bus error)
[   22.561034] ata2.00: status: { DRDY }
[   22.561073] ata2: hard resetting link
[   22.599833] type=1400 audit(1316000762.128:6): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=893 comm="apparmor_parser"
[   22.600843] type=1400 audit(1316000762.138:7): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=893 comm="apparmor_parser"
[   22.601426] type=1400 audit(1316000762.138:8): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=893 comm="apparmor_parser"
[   23.110101] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   23.111163] type=1400 audit(1316000762.648:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=910 comm="apparmor_parser"
[   23.111210] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[   23.111212] ata2.00: revalidation failed (errno=-5)
[   23.111470] type=1400 audit(1316000762.648:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=910 comm="apparmor_parser"
[   23.121094] type=1400 audit(1316000762.658:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=911 comm="apparmor_parser"
[   23.396835] Bluetooth: L2CAP ver 2.15
[   23.396837] Bluetooth: L2CAP socket layer initialized


[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-8-generic (buildd@allspice) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 (Ubuntu 2.6.38-8.42-generic 2.6.38.2)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=C43EB5173EB50388 loop=/ubuntu/disks/root.disk ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfdf0000 (usable)
[    0.000000]  BIOS-e820: 00000000cfdf0000 - 00000000cfdf3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cfdf3000 - 00000000cfe00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cfe00000 - 00000000cff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.4 present.
[    0.000000] DMI: Gigabyte Technology Co., Ltd. GA-MA785GM-US2H/GA-MA785GM-US2H, BIOS F11 05/17/2010
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x130000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 base 0000C0000000 mask FFFFF0000000 write-back
[    0.000000]   3 base 0000CFE00000 mask FFFFFFE00000 uncachable
[    0.000000]   4 base 000100000000 mask FFFFE0000000 write-back
[    0.000000]   5 base 000120000000 mask FFFFF0000000 write-back
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000130000000 aka 4864M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000cfe00000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xcfdf0 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000f5670] f5670
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: 0000000000000000-00000000cfdf0000
[    0.000000]  0000000000 - 00c0000000 page 1G
[    0.000000]  00c0000000 - 00cfc00000 page 2M
[    0.000000]  00cfc00000 - 00cfdf0000 page 4k
[    0.000000] kernel direct mapping tables up to cfdf0000 @ 1fffd000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-0000000130000000
[    0.000000]  0100000000 - 0130000000 page 2M
[    0.000000] kernel direct mapping tables up to 130000000 @ cfdee000-cfdf0000
[    0.000000] RAMDISK: 366e2000 - 37369000
[    0.000000] ACPI: RSDP 00000000000f7030 00014 (v00 GBT   )
[    0.000000] ACPI: RSDT 00000000cfdf3000 00040 (v01 GBT    GBTUACPI 42302E31 MSFT 01010101)
[    0.000000] ACPI: FACP 00000000cfdf3040 00074 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: DSDT 00000000cfdf30c0 07492 (v01 GBT    GBTUACPI 00001000 MSFT 03000000)
[    0.000000] ACPI: FACS 00000000cfdf0000 00040
[    0.000000] ACPI: SSDT 00000000cfdfa640 0095E (v01 PTLTD  POWERNOW 00000001  LTP 00000001)
[    0.000000] ACPI: HPET 00000000cfdfafc0 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 00000098)
[    0.000000] ACPI: MCFG 00000000cfdfb000 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: TAMG 00000000cfdfb040 0032A (v01 GBT    GBT   B0 5455312E BG?? 53450101)
[    0.000000] ACPI: APIC 00000000cfdfa580 000BC (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: SLIC 00000000cfdf0040 00176 (v01 GBT    GBTUACPI 00000001 MSFT 000F4240)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000130000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000130000000
[    0.000000]   NODE_DATA [000000012fffb000 - 000000012fffffff]
[    0.000000]  [ffffea0000000000-ffffea00043fffff] PMD -> [ffff88012be00000-ffff88012f7fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00130000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000cfdf0
[    0.000000]     0: 0x00100000 -> 0x00130000
[    0.000000] On node 0 totalpages: 1047935
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 6 pages reserved
[    0.000000]   DMA zone: 3921 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 833064 pages, LIFO batch:31
[    0.000000]   Normal zone: 2688 pages used for memmap
[    0.000000]   Normal zone: 193920 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x04] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x05] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x06] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x07] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x05] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x06] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x07] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfed00000
[    0.000000] SMP: Allowing 8 CPUs, 6 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cfdf0000 - 00000000cfdf3000
[    0.000000] PM: Registered nosave memory: 00000000cfdf3000 - 00000000cfe00000
[    0.000000] PM: Registered nosave memory: 00000000cfe00000 - 00000000cff00000
[    0.000000] PM: Registered nosave memory: 00000000cff00000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at cff00000 (gap: cff00000:10100000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff8800cfa00000 s84416 r8192 d22080 u262144
[    0.000000] pcpu-alloc: s84416 r8192 d22080 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1030905
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=C43EB5173EB50388 loop=/ubuntu/disks/root.disk ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ c4000000 size 32 MB
[    0.000000] Aperture pointing to e820 RAM. Ignoring.
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ c4000000
[    0.000000] PM: Registered nosave memory: 00000000c4000000 - 00000000c8000000
[    0.000000] Memory: 3973592k/4980736k available (5940k kernel code, 788996k absent, 218148k reserved, 5017k data, 956k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 41943040 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 3114.424 MHz processor.
[    0.020004] Calibrating delay loop (skipped), value calculated using timer frequency.. 6228.84 BogoMIPS (lpj=31144240)
[    0.020007] pid_max: default: 32768 minimum: 301
[    0.020028] Security Framework initialized
[    0.020040] AppArmor: AppArmor initialized
[    0.020041] Yama: becoming mindful.
[    0.020348] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.021663] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.022235] Mount-cache hash table entries: 256
[    0.022340] Initializing cgroup subsys ns
[    0.022342] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.022345] Initializing cgroup subsys cpuacct
[    0.022348] Initializing cgroup subsys memory
[    0.022355] Initializing cgroup subsys devices
[    0.022357] Initializing cgroup subsys freezer
[    0.022358] Initializing cgroup subsys net_cls
[    0.022360] Initializing cgroup subsys blkio
[    0.022385] tseg: 00cff00000
[    0.022386] CPU: Physical Processor ID: 0
[    0.022387] CPU: Processor Core ID: 0
[    0.022389] mce: CPU supports 6 MCE banks
[    0.022397] using C1E aware idle routine
[    0.023611] ACPI: Core revision 20110112
[    0.030032] ftrace: allocating 24314 entries in 96 pages
[    0.040074] Setting APIC routing to flat
[    0.040552] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.140907] CPU0: AMD Phenom(tm) II X2 550 Processor stepping 03
[    0.150000] Performance Events: AMD PMU driver.
[    0.150000] ... version:                0
[    0.150000] ... bit width:              48
[    0.150000] ... generic registers:      4
[    0.150000] ... value mask:             0000ffffffffffff
[    0.150000] ... max period:             00007fffffffffff
[    0.150000] ... fixed-purpose events:   0
[    0.150000] ... event mask:             000000000000000f
[    0.150000] Booting Node   0, Processors  #1
[    0.310008] Brought up 2 CPUs
[    0.310010] Total of 2 processors activated (12457.01 BogoMIPS).
[    0.310012] System has AMD C1E enabled
[    0.310037] Switch to broadcast mode on CPU1
[    0.310705] Switch to broadcast mode on CPU0
[    0.310705] devtmpfs: initialized
[    0.310705] print_constraints: dummy: 
[    0.310705] Time: 16:48:49  Date: 09/14/11
[    0.310705] NET: Registered protocol family 16
[    0.310782] node 0 link 0: io port [c000, ffff]
[    0.310784] TOM: 00000000d0000000 aka 3328M
[    0.310785] Fam 10h mmconf [e0000000, e00fffff]
[    0.310787] node 0 link 0: mmio [a0000, bffff]
[    0.310789] node 0 link 0: mmio [d0000000, dfffffff]
[    0.310735] Trying to unpack rootfs image as initramfs...
[    0.310793] 
[    0.310795] node 0 link 0: mmio [f0000000, fe02ffff]
[    0.310797] node 0 link 0: mmio [e0000000, e03fffff] ==> [e0100000, e03fffff]
[    0.310799] TOM2: 0000000130000000 aka 4864M
[    0.310801] bus: [00, 03] on node 0 link 0
[    0.310803] bus: 00 index 0 [io  0x0000-0xffff]
[    0.310804] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
[    0.310806] bus: 00 index 2 [mem 0xd0000000-0xdfffffff]
[    0.310807] bus: 00 index 3 [mem 0xe0400000-0xffffffff]
[    0.310809] bus: 00 index 4 [mem 0xe0100000-0xe03fffff]
[    0.310810] bus: 00 index 5 [mem 0x130000000-0xfcffffffff]
[    0.310819] Extended Config Space enabled on 1 nodes
[    0.310833] ACPI: bus type pci registered
[    0.310881] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.310884] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.328746] PCI: Using configuration type 1 for base access
[    0.329262] bio: create slab <bio-0> at 0
[    0.329941] ACPI: EC: Look up EC in DSDT
[    0.334268] ACPI Warning: Incorrect checksum in table [TAMG] - 0xC3, should be 0xC2 (20110112/tbutils-314)
[    0.334379] ACPI: Interpreter enabled
[    0.334382] ACPI: (supports S0 S3 S4 S5)
[    0.334397] ACPI: Using IOAPIC for interrupt routing
[    0.481133] Freeing initrd memory: 12828k freed
[    0.551680] ACPI: No dock devices found.
[    0.551682] HEST: Table not found.
[    0.551685] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.551728] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.551809] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.551811] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.551813] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.551814] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000dffff]
[    0.551816] pci_root PNP0A03:00: host bridge window [mem 0xd0000000-0xfebfffff]
[    0.551828] pci 0000:00:00.0: [1022:9601] type 0 class 0x000600
[    0.551838] pci 0000:00:00.0: reg 1c: [mem 0xe0000000-0xffffffff 64bit]
[    0.551866] pci 0000:00:02.0: [1022:9603] type 1 class 0x000604
[    0.551888] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.551891] pci 0000:00:02.0: PME# disabled
[    0.551909] pci 0000:00:0a.0: [1022:9609] type 1 class 0x000604
[    0.551930] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
[    0.551932] pci 0000:00:0a.0: PME# disabled
[    0.551956] pci 0000:00:11.0: [1002:4390] type 0 class 0x000101
[    0.551973] pci 0000:00:11.0: reg 10: [io  0xff00-0xff07]
[    0.551982] pci 0000:00:11.0: reg 14: [io  0xfe00-0xfe03]
[    0.551991] pci 0000:00:11.0: reg 18: [io  0xfd00-0xfd07]
[    0.552000] pci 0000:00:11.0: reg 1c: [io  0xfc00-0xfc03]
[    0.552009] pci 0000:00:11.0: reg 20: [io  0xfb00-0xfb0f]
[    0.552017] pci 0000:00:11.0: reg 24: [mem 0xfe02f000-0xfe02f3ff]
[    0.552036] pci 0000:00:11.0: set SATA to AHCI mode
[    0.552067] pci 0000:00:12.0: [1002:4397] type 0 class 0x000c03
[    0.552080] pci 0000:00:12.0: reg 10: [mem 0xfe02e000-0xfe02efff]
[    0.552138] pci 0000:00:12.1: [1002:4398] type 0 class 0x000c03
[    0.552151] pci 0000:00:12.1: reg 10: [mem 0xfe02d000-0xfe02dfff]
[    0.552215] pci 0000:00:12.2: [1002:4396] type 0 class 0x000c03
[    0.552233] pci 0000:00:12.2: reg 10: [mem 0xfe02c000-0xfe02c0ff]
[    0.552298] pci 0000:00:12.2: supports D1 D2
[    0.552300] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.552303] pci 0000:00:12.2: PME# disabled
[    0.552324] pci 0000:00:13.0: [1002:4397] type 0 class 0x000c03
[    0.552336] pci 0000:00:13.0: reg 10: [mem 0xfe02b000-0xfe02bfff]
[    0.552394] pci 0000:00:13.1: [1002:4398] type 0 class 0x000c03
[    0.552407] pci 0000:00:13.1: reg 10: [mem 0xfe02a000-0xfe02afff]
[    0.552471] pci 0000:00:13.2: [1002:4396] type 0 class 0x000c03
[    0.552489] pci 0000:00:13.2: reg 10: [mem 0xfe029000-0xfe0290ff]
[    0.552554] pci 0000:00:13.2: supports D1 D2
[    0.552556] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.552559] pci 0000:00:13.2: PME# disabled
[    0.552581] pci 0000:00:14.0: [1002:4385] type 0 class 0x000c05
[    0.552667] pci 0000:00:14.1: [1002:439c] type 0 class 0x000101
[    0.552682] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
[    0.552691] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
[    0.552700] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
[    0.552708] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
[    0.552717] pci 0000:00:14.1: reg 20: [io  0xfa00-0xfa0f]
[    0.552762] pci 0000:00:14.2: [1002:4383] type 0 class 0x000403
[    0.552782] pci 0000:00:14.2: reg 10: [mem 0xfe024000-0xfe027fff 64bit]
[    0.552836] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.552840] pci 0000:00:14.2: PME# disabled
[    0.552851] pci 0000:00:14.3: [1002:439d] type 0 class 0x000601
[    0.552921] pci 0000:00:14.4: [1002:4384] type 1 class 0x000604
[    0.552959] pci 0000:00:14.5: [1002:4399] type 0 class 0x000c03
[    0.552971] pci 0000:00:14.5: reg 10: [mem 0xfe028000-0xfe028fff]
[    0.553032] pci 0000:00:18.0: [1022:1200] type 0 class 0x000600
[    0.553044] pci 0000:00:18.1: [1022:1201] type 0 class 0x000600
[    0.553054] pci 0000:00:18.2: [1022:1202] type 0 class 0x000600
[    0.553064] pci 0000:00:18.3: [1022:1203] type 0 class 0x000600
[    0.553076] pci 0000:00:18.4: [1022:1204] type 0 class 0x000600
[    0.553117] pci 0000:01:00.0: [1002:6719] type 0 class 0x000300
[    0.553129] pci 0000:01:00.0: reg 10: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.553138] pci 0000:01:00.0: reg 18: [mem 0xfdfc0000-0xfdfdffff 64bit]
[    0.553145] pci 0000:01:00.0: reg 20: [io  0xee00-0xeeff]
[    0.553156] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.553171] pci 0000:01:00.0: supports D1 D2
[    0.553188] pci 0000:01:00.1: [1002:aa80] type 0 class 0x000403
[    0.553199] pci 0000:01:00.1: reg 10: [mem 0xfdffc000-0xfdffffff 64bit]
[    0.553238] pci 0000:01:00.1: supports D1 D2
[    0.570019] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    0.570024] pci 0000:00:02.0:   bridge window [io  0xe000-0xefff]
[    0.570026] pci 0000:00:02.0:   bridge window [mem 0xfdf00000-0xfdffffff]
[    0.570029] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.570067] pci 0000:02:00.0: [10ec:8168] type 0 class 0x000200
[    0.570080] pci 0000:02:00.0: reg 10: [io  0xde00-0xdeff]
[    0.570099] pci 0000:02:00.0: reg 18: [mem 0xfdbff000-0xfdbfffff 64bit pref]
[    0.570111] pci 0000:02:00.0: reg 20: [mem 0xfdbe0000-0xfdbeffff 64bit pref]
[    0.570120] pci 0000:02:00.0: reg 30: [mem 0x00000000-0x0000ffff pref]
[    0.570147] pci 0000:02:00.0: supports D1 D2
[    0.570149] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.570152] pci 0000:02:00.0: PME# disabled
[    0.590020] pci 0000:00:0a.0: PCI bridge to [bus 02-02]
[    0.590024] pci 0000:00:0a.0:   bridge window [io  0xd000-0xdfff]
[    0.590026] pci 0000:00:0a.0:   bridge window [mem 0xfde00000-0xfdefffff]
[    0.590029] pci 0000:00:0a.0:   bridge window [mem 0xfdb00000-0xfdbfffff 64bit pref]
[    0.590080] pci 0000:03:0e.0: [104c:8024] type 0 class 0x000c00
[    0.590102] pci 0000:03:0e.0: reg 10: [mem 0xfddff000-0xfddff7ff]
[    0.590114] pci 0000:03:0e.0: reg 14: [mem 0xfddf8000-0xfddfbfff]
[    0.590192] pci 0000:03:0e.0: supports D1 D2
[    0.590193] pci 0000:03:0e.0: PME# supported from D0 D1 D2 D3hot
[    0.590198] pci 0000:03:0e.0: PME# disabled
[    0.590230] pci 0000:00:14.4: PCI bridge to [bus 03-03] (subtractive decode)
[    0.590234] pci 0000:00:14.4:   bridge window [io  0xc000-0xcfff]
[    0.590238] pci 0000:00:14.4:   bridge window [mem 0xfdd00000-0xfddfffff]
[    0.590241] pci 0000:00:14.4:   bridge window [mem 0xfdc00000-0xfdcfffff pref]
[    0.590243] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.590245] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.590247] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.590248] pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
[    0.590250] pci 0000:00:14.4:   bridge window [mem 0xd0000000-0xfebfffff] (subtractive decode)
[    0.590262] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.590420] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.590459] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[    0.590485] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCEA._PRT]
[    0.590507]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.599074] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.599103] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.599130] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.599156] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.599182] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.599208] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.599234] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.599260] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.599340] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.599343] vgaarb: loaded
[    0.599456] SCSI subsystem initialized
[    0.599474] libata version 3.00 loaded.
[    0.599474] usbcore: registered new interface driver usbfs
[    0.599474] usbcore: registered new interface driver hub
[    0.599474] usbcore: registered new device driver usb
[    0.599474] wmi: Mapper loaded
[    0.599474] PCI: Using ACPI for IRQ routing
[    0.599474] PCI: pci_cache_line_size set to 64 bytes
[    0.599474] pci 0000:00:00.0: no compatible bridge window for [mem 0xe0000000-0xffffffff 64bit]
[    0.599474] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.599474] reserve RAM buffer: 00000000cfdf0000 - 00000000cfffffff 
[    0.599474] NetLabel: Initializing
[    0.599474] NetLabel:  domain hash size = 128
[    0.599474] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.599474] NetLabel:  unlabeled traffic allowed by default
[    0.599474] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.599474] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.601019] Switching to clocksource hpet
[    0.605477] AppArmor: AppArmor Filesystem Enabled
[    0.605492] pnp: PnP ACPI init
[    0.605503] ACPI: bus type pnp registered
[    0.605564] pnp 00:00: [bus 00-ff]
[    0.605566] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.605568] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.605569] pnp 00:00: [io  0x0d00-0xffff window]
[    0.605571] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.605573] pnp 00:00: [mem 0x000c0000-0x000dffff window]
[    0.605574] pnp 00:00: [mem 0xd0000000-0xfebfffff window]
[    0.605606] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.605613] pnp 00:01: [io  0x0010-0x001f]
[    0.605614] pnp 00:01: [io  0x0022-0x003f]
[    0.605615] pnp 00:01: [io  0x0044-0x005f]
[    0.605617] pnp 00:01: [io  0x0062-0x0063]
[    0.605618] pnp 00:01: [io  0x0065-0x006f]
[    0.605619] pnp 00:01: [io  0x0074-0x007f]
[    0.605621] pnp 00:01: [io  0x0091-0x0093]
[    0.605622] pnp 00:01: [io  0x00a2-0x00bf]
[    0.605623] pnp 00:01: [io  0x00e0-0x00ef]
[    0.605624] pnp 00:01: [io  0x04d0-0x04d1]
[    0.605626] pnp 00:01: [io  0x0220-0x0225]
[    0.605627] pnp 00:01: [io  0x0290-0x0294]
[    0.605662] system 00:01: [io  0x04d0-0x04d1] has been reserved
[    0.605664] system 00:01: [io  0x0220-0x0225] has been reserved
[    0.605666] system 00:01: [io  0x0290-0x0294] has been reserved
[    0.605668] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.608022] Switched to NOHz mode on CPU #1
[    0.608024] Switched to NOHz mode on CPU #0
[    0.610342] pnp 00:02: [io  0x4100-0x411f]
[    0.610344] pnp 00:02: [io  0x0228-0x022f]
[    0.610346] pnp 00:02: [io  0x040b]
[    0.610347] pnp 00:02: [io  0x04d6]
[    0.610348] pnp 00:02: [io  0x0c00-0x0c01]
[    0.610349] pnp 00:02: [io  0x0c14]
[    0.610350] pnp 00:02: [io  0x0c50-0x0c52]
[    0.610352] pnp 00:02: [io  0x0c6c-0x0c6d]
[    0.610353] pnp 00:02: [io  0x0c6f]
[    0.610354] pnp 00:02: [io  0x0cd0-0x0cd1]
[    0.610355] pnp 00:02: [io  0x0cd2-0x0cd3]
[    0.610356] pnp 00:02: [io  0x0cd4-0x0cdf]
[    0.610357] pnp 00:02: [io  0x4000-0x40fe]
[    0.610358] pnp 00:02: [io  0x4210-0x4217]
[    0.610360] pnp 00:02: [io  0x0b00-0x0b0f]
[    0.610361] pnp 00:02: [io  0x0b10-0x0b1f]
[    0.610365] pnp 00:02: [io  0x0b20-0x0b3f]
[    0.610367] pnp 00:02: [mem 0x00000000-0x00000fff window]
[    0.610368] pnp 00:02: [mem 0xfee00400-0xfee00fff window]
[    0.610373] pnp 00:02: disabling [mem 0x00000000-0x00000fff window] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.610393] pnp 00:02: disabling [mem 0x00000000-0x00000fff window disabled] because it overlaps 0000:01:00.0 BAR 6 [mem 0x00000000-0x0001ffff pref]
[    0.610398] pnp 00:02: disabling [mem 0x00000000-0x00000fff window disabled] because it overlaps 0000:02:00.0 BAR 6 [mem 0x00000000-0x0000ffff pref]
[    0.610424] system 00:02: [io  0x4100-0x411f] has been reserved
[    0.610427] system 00:02: [io  0x0228-0x022f] has been reserved
[    0.610428] system 00:02: [io  0x040b] has been reserved
[    0.610430] system 00:02: [io  0x04d6] has been reserved
[    0.610432] system 00:02: [io  0x0c00-0x0c01] has been reserved
[    0.610434] system 00:02: [io  0x0c14] has been reserved
[    0.610435] system 00:02: [io  0x0c50-0x0c52] has been reserved
[    0.610437] system 00:02: [io  0x0c6c-0x0c6d] has been reserved
[    0.610439] system 00:02: [io  0x0c6f] has been reserved
[    0.610440] system 00:02: [io  0x0cd0-0x0cd1] has been reserved
[    0.610442] system 00:02: [io  0x0cd2-0x0cd3] has been reserved
[    0.610444] system 00:02: [io  0x0cd4-0x0cdf] has been reserved
[    0.610446] system 00:02: [io  0x4000-0x40fe] has been reserved
[    0.610447] system 00:02: [io  0x4210-0x4217] has been reserved
[    0.610449] system 00:02: [io  0x0b00-0x0b0f] has been reserved
[    0.610451] system 00:02: [io  0x0b10-0x0b1f] has been reserved
[    0.610453] system 00:02: [io  0x0b20-0x0b3f] has been reserved
[    0.610455] system 00:02: [mem 0xfee00400-0xfee00fff window] has been reserved
[    0.610458] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.610525] pnp 00:03: [dma 4]
[    0.610527] pnp 00:03: [io  0x0000-0x000f]
[    0.610528] pnp 00:03: [io  0x0080-0x0090]
[    0.610529] pnp 00:03: [io  0x0094-0x009f]
[    0.610530] pnp 00:03: [io  0x00c0-0x00df]
[    0.610549] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.610582] pnp 00:04: [irq 0 disabled]
[    0.610594] pnp 00:04: [irq 8]
[    0.610595] pnp 00:04: [mem 0xfed00000-0xfed003ff]
[    0.610614] pnp 00:04: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.610631] pnp 00:05: [io  0x0070-0x0073]
[    0.610649] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.610654] pnp 00:06: [io  0x0061]
[    0.610675] pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.610680] pnp 00:07: [io  0x00f0-0x00ff]
[    0.610687] pnp 00:07: [irq 13]
[    0.610705] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.610897] pnp 00:08: [io  0x03f8-0x03ff]
[    0.610904] pnp 00:08: [irq 4]
[    0.610943] pnp 00:08: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.611076] pnp 00:09: [io  0x0378-0x037f]
[    0.611083] pnp 00:09: [irq 7]
[    0.611115] pnp 00:09: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.611192] pnp 00:0a: [mem 0xe0000000-0xefffffff]
[    0.611228] system 00:0a: [mem 0xe0000000-0xefffffff] has been reserved
[    0.611230] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.611336] pnp 00:0b: [mem 0x000cfa00-0x000cffff]
[    0.611338] pnp 00:0b: [mem 0x000f0000-0x000f7fff]
[    0.611339] pnp 00:0b: [mem 0x000f8000-0x000fbfff]
[    0.611340] pnp 00:0b: [mem 0x000fc000-0x000fffff]
[    0.611342] pnp 00:0b: [mem 0xcfdf0000-0xcfdfffff]
[    0.611343] pnp 00:0b: [mem 0xffff0000-0xffffffff]
[    0.611345] pnp 00:0b: [mem 0x00000000-0x0009ffff]
[    0.611346] pnp 00:0b: [mem 0x00100000-0xcfdeffff]
[    0.611349] pnp 00:0b: [mem 0xcfe00000-0xcfefffff]
[    0.611350] pnp 00:0b: [mem 0xcff00000-0xcfffffff]
[    0.611352] pnp 00:0b: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.611353] pnp 00:0b: [mem 0xfec00000-0xfec00fff]
[    0.611355] pnp 00:0b: [mem 0xfee00000-0xfee00fff]
[    0.611356] pnp 00:0b: [mem 0xfff80000-0xfffeffff]
[    0.611359] pnp 00:0b: disabling [mem 0x000cfa00-0x000cffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.611362] pnp 00:0b: disabling [mem 0x000f0000-0x000f7fff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.611365] pnp 00:0b: disabling [mem 0x000f8000-0x000fbfff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.611367] pnp 00:0b: disabling [mem 0x000fc000-0x000fffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.611370] pnp 00:0b: disabling [mem 0x00000000-0x0009ffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.611373] pnp 00:0b: disabling [mem 0x00100000-0xcfdeffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.611416] system 00:0b: [mem 0xcfdf0000-0xcfdfffff] could not be reserved
[    0.611418] system 00:0b: [mem 0xffff0000-0xffffffff] has been reserved
[    0.611420] system 00:0b: [mem 0xcfe00000-0xcfefffff] has been reserved
[    0.611422] system 00:0b: [mem 0xcff00000-0xcfffffff] could not be reserved
[    0.611424] system 00:0b: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.611426] system 00:0b: [mem 0xfee00000-0xfee00fff] could not be reserved
[    0.611428] system 00:0b: [mem 0xfff80000-0xfffeffff] has been reserved
[    0.611430] system 00:0b: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.611445] pnp: PnP ACPI: found 12 devices
[    0.611446] ACPI: ACPI bus type pnp unregistered
[    0.617009] pci 0000:01:00.0: BAR 6: assigned [mem 0xfdf00000-0xfdf1ffff pref]
[    0.617012] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    0.617014] pci 0000:00:02.0:   bridge window [io  0xe000-0xefff]
[    0.617016] pci 0000:00:02.0:   bridge window [mem 0xfdf00000-0xfdffffff]
[    0.617018] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.617022] pci 0000:02:00.0: BAR 6: assigned [mem 0xfdb00000-0xfdb0ffff pref]
[    0.617023] pci 0000:00:0a.0: PCI bridge to [bus 02-02]
[    0.617025] pci 0000:00:0a.0:   bridge window [io  0xd000-0xdfff]
[    0.617027] pci 0000:00:0a.0:   bridge window [mem 0xfde00000-0xfdefffff]
[    0.617030] pci 0000:00:0a.0:   bridge window [mem 0xfdb00000-0xfdbfffff 64bit pref]
[    0.617033] pci 0000:00:14.4: PCI bridge to [bus 03-03]
[    0.617035] pci 0000:00:14.4:   bridge window [io  0xc000-0xcfff]
[    0.617039] pci 0000:00:14.4:   bridge window [mem 0xfdd00000-0xfddfffff]
[    0.617043] pci 0000:00:14.4:   bridge window [mem 0xfdc00000-0xfdcfffff pref]
[    0.617060] pci 0000:00:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.617063] pci 0000:00:02.0: setting latency timer to 64
[    0.617067] pci 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.617069] pci 0000:00:0a.0: setting latency timer to 64
[    0.617075] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.617077] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.617078] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.617080] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000dffff]
[    0.617081] pci_bus 0000:00: resource 8 [mem 0xd0000000-0xfebfffff]
[    0.617083] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.617085] pci_bus 0000:01: resource 1 [mem 0xfdf00000-0xfdffffff]
[    0.617086] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.617088] pci_bus 0000:02: resource 0 [io  0xd000-0xdfff]
[    0.617090] pci_bus 0000:02: resource 1 [mem 0xfde00000-0xfdefffff]
[    0.617091] pci_bus 0000:02: resource 2 [mem 0xfdb00000-0xfdbfffff 64bit pref]
[    0.617093] pci_bus 0000:03: resource 0 [io  0xc000-0xcfff]
[    0.617095] pci_bus 0000:03: resource 1 [mem 0xfdd00000-0xfddfffff]
[    0.617096] pci_bus 0000:03: resource 2 [mem 0xfdc00000-0xfdcfffff pref]
[    0.617098] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.617099] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.617101] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.617102] pci_bus 0000:03: resource 7 [mem 0x000c0000-0x000dffff]
[    0.617104] pci_bus 0000:03: resource 8 [mem 0xd0000000-0xfebfffff]
[    0.617125] NET: Registered protocol family 2
[    0.617234] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.618105] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.620570] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.620870] TCP: Hash tables configured (established 524288 bind 65536)
[    0.620872] TCP reno registered
[    0.620882] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.620909] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.621017] NET: Registered protocol family 1
[    0.720097] pci 0000:01:00.0: Boot video device
[    0.720107] PCI: CLS 4 bytes, default 64
[    0.721218] PCI-DMA: Disabling AGP.
[    0.721297] PCI-DMA: aperture base @ c4000000 size 65536 KB
[    0.721298] PCI-DMA: using GART IOMMU.
[    0.721301] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    0.724547] audit: initializing netlink socket (disabled)
[    0.724561] type=2000 audit(1316018928.720:1): initialized
[    0.733788] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.735048] VFS: Disk quotas dquot_6.5.2
[    0.735088] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.735571] fuse init (API version 7.16)
[    0.735654] msgmni has been set to 7914
[    0.735899] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.735933] io scheduler noop registered
[    0.735934] io scheduler deadline registered
[    0.735964] io scheduler cfq registered (default)
[    0.736071] pcieport 0000:00:02.0: setting latency timer to 64
[    0.736095] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    0.736166] pcieport 0000:00:0a.0: setting latency timer to 64
[    0.736184] pcieport 0000:00:0a.0: irq 41 for MSI/MSI-X
[    0.736244] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.736260] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.736356] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.736360] ACPI: Power Button [PWRB]
[    0.736393] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.736395] ACPI: Power Button [PWRF]
[    0.736502] ACPI: acpi_idle registered with cpuidle
[    0.736514] ACPI: processor limited to max C-state 1
[    0.850683] ERST: Table is not found!
[    0.850738] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.871352] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.500754] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.500979] Linux agpgart interface v0.103
[    1.501671] brd: module loaded
[    1.501982] loop: module loaded
[    1.502042] i2c-core: driver [adp5520] using legacy suspend method
[    1.502043] i2c-core: driver [adp5520] using legacy resume method
[    1.502181] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.502454] Fixed MDIO Bus: probed
[    1.502474] PPP generic driver version 2.4.2
[    1.502514] tun: Universal TUN/TAP device driver, 1.6
[    1.502515] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.502571] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.502616] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.502632] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    1.502663] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.530079] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.530101] ehci_hcd 0000:00:12.2: debug port 1
[    1.530127] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe02c000
[    1.550066] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.550152] hub 1-0:1.0: USB hub found
[    1.550155] hub 1-0:1.0: 6 ports detected
[    1.550264] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.550274] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.550300] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.550325] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.550343] ehci_hcd 0000:00:13.2: debug port 1
[    1.550368] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe029000
[    1.570065] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.570140] hub 2-0:1.0: USB hub found
[    1.570142] hub 2-0:1.0: 6 ports detected
[    1.570217] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.570261] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.570273] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.570297] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.570341] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfe02e000
[    1.634193] hub 3-0:1.0: USB hub found
[    1.634198] hub 3-0:1.0: 3 ports detected
[    1.634312] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.634323] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    1.634347] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    1.634377] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfe02d000
[    1.694145] hub 4-0:1.0: USB hub found
[    1.694150] hub 4-0:1.0: 3 ports detected
[    1.694261] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.694275] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.694298] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.694341] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe02b000
[    1.720061] Refined TSC clocksource calibration: 3114.071 MHz.
[    1.720065] Switching to clocksource tsc
[    1.754135] hub 5-0:1.0: USB hub found
[    1.754140] hub 5-0:1.0: 3 ports detected
[    1.754235] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.754246] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    1.754269] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    1.754296] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfe02a000
[    1.814137] hub 6-0:1.0: USB hub found
[    1.814143] hub 6-0:1.0: 3 ports detected
[    1.814239] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.814251] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    1.814278] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    1.814305] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfe028000
[    1.870056] usb 1-3: new high speed USB device using ehci_hcd and address 2
[    1.874132] hub 7-0:1.0: USB hub found
[    1.874137] hub 7-0:1.0: 2 ports detected
[    1.874212] uhci_hcd: USB Universal Host Controller Interface driver
[    1.874279] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.906992] i8042: Failed to disable AUX port, but continuing anyway... Is this a SiS?
[    1.906993] i8042: If AUX port is really absent please use the 'i8042.noaux' option
[    2.150136] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.150208] mousedev: PS/2 mouse device common for all mice
[    2.150291] rtc_cmos 00:05: RTC can wake from S4
[    2.160101] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    2.160133] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    2.160201] device-mapper: uevent: version 1.0.3
[    2.160249] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    2.160309] device-mapper: multipath: version 1.2.0 loaded
[    2.160311] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.160393] cpuidle: using governor ladder
[    2.160394] cpuidle: using governor menu
[    2.160545] TCP cubic registered
[    2.160618] NET: Registered protocol family 10
[    2.160966] NET: Registered protocol family 17
[    2.160976] Registering the dns_resolver key type
[    2.160997] powernow-k8: Found 1 AMD Phenom(tm) II X2 550 Processor (2 cpu cores) (version 2.20.00)
[    2.161021] powernow-k8:    0 : pstate 0 (3100 MHz)
[    2.161023] powernow-k8:    1 : pstate 1 (2400 MHz)
[    2.161024] powernow-k8:    2 : pstate 2 (1900 MHz)
[    2.161025] powernow-k8:    3 : pstate 3 (800 MHz)
[    2.161156] PM: Hibernation image not present or could not be loaded.
[    2.161162] registered taskstats version 1
[    2.161352]   Magic number: 11:554:843
[    2.161406] rtc_cmos 00:05: setting system clock to 2011-09-14 16:48:51 UTC (1316018931)
[    2.161409] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.161410] EDD information not available.
[    2.162605] Freeing unused kernel memory: 956k freed
[    2.162790] Write protecting the kernel read-only data: 10240k
[    2.163337] Freeing unused kernel memory: 184k freed
[    2.166892] Freeing unused kernel memory: 1444k freed
[    2.180063] <30>udev[98]: starting version 167
[    2.219141] scsi0 : pata_atiixp
[    2.220332] scsi1 : pata_atiixp
[    2.220748] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfa00 irq 14
[    2.220750] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfa08 irq 15
[    2.226119] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.226139] r8169 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.226173] r8169 0000:02:00.0: setting latency timer to 64
[    2.226213] r8169 0000:02:00.0: irq 42 for MSI/MSI-X
[    2.226527] r8169 0000:02:00.0: eth0: RTL8168c/8111c at 0xffffc90000668000, 00:24:1d:d9:7d:7b, XID 1c4000c0 IRQ 42
[    2.244901] ahci 0000:00:11.0: version 3.0
[    2.244926] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    2.245025] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    2.245028] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
[    2.245596] scsi2 : ahci
[    2.245664] scsi3 : ahci
[    2.245710] scsi4 : ahci
[    2.245755] scsi5 : ahci
[    2.245839] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 22
[    2.245841] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 22
[    2.245844] ata5: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 22
[    2.245847] ata6: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 22
[    2.490052] usb 4-3: new full speed USB device using ohci_hcd and address 2
[    2.590123] ata6: SATA link down (SStatus 0 SControl 300)
[    2.730098] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.0/input/input2
[    2.730167] generic-usb 0003:046D:C52E.0001: input,hidraw0: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:12.1-3/input0
[    2.734449] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.1/input/input3
[    2.734553] generic-usb 0003:046D:C52E.0002: input,hiddev0,hidraw1: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:12.1-3/input1
[    2.734563] usbcore: registered new interface driver usbhid
[    2.734565] usbhid: USB HID core driver
[    2.790101] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.790123] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.790142] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.790878] ata4.00: ATA-8: WDC WD6400AARS-00Y5B1, 80.00A80, max UDMA/133
[    2.790880] ata4.00: 1250263728 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.791694] ata4.00: configured for UDMA/133
[    2.793134] ata5.00: ATAPI: HL-DT-ST DVDRAM GH22NS50, TN02, max UDMA/100
[    2.795892] ata3.00: ATA-8: SAMSUNG HD103SJ, 1AJ10001, max UDMA/133
[    2.795895] ata3.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.796960] ata5.00: configured for UDMA/100
[    2.801685] ata3.00: configured for UDMA/133
[    2.801800] scsi 2:0:0:0: Direct-Access     ATA      SAMSUNG HD103SJ  1AJ1 PQ: 0 ANSI: 5
[    2.801889] sd 2:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.801915] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    2.801919] sd 2:0:0:0: [sda] Write Protect is off
[    2.801921] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.801933] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.802007] scsi 3:0:0:0: Direct-Access     ATA      WDC WD6400AARS-0 80.0 PQ: 0 ANSI: 5
[    2.802081] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    2.802123] sd 3:0:0:0: [sdb] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
[    2.802152] sd 3:0:0:0: [sdb] Write Protect is off
[    2.802154] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.802167] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.805564] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH22NS50  TN02 PQ: 0 ANSI: 5
[    2.813974] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.813977] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.814061] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    2.814100] sr 4:0:0:0: Attached scsi generic sg2 type 5
[    2.827482]  sda: sda1 sda2 < sda5 >
[    2.827685] sd 2:0:0:0: [sda] Attached SCSI disk
[    3.277972]  sdb: sdb1
[    3.278156] sd 3:0:0:0: [sdb] Attached SCSI disk
[    3.286527] firewire_ohci 0000:03:0e.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    3.337873] ata4.00: exception Emask 0x50 SAct 0x1 SErr 0x280900 action 0x6 frozen
[    3.337876] ata4.00: irq_stat 0x08000000, interface fatal error
[    3.337878] ata4: SError: { UnrecovData HostInt 10B8B BadCRC }
[    3.337881] ata4.00: failed command: READ FPDMA QUEUED
[    3.337885] ata4.00: cmd 60/08:00:a8:82:85/00:00:4a:00:00/40 tag 0 ncq 4096 in
[    3.337885]          res 40/00:04:a8:82:85/00:00:4a:00:00/40 Emask 0x50 (ATA bus error)
[    3.337887] ata4.00: status: { DRDY }
[    3.337890] ata4: hard resetting link
[    3.340096] firewire_ohci: Added fw-ohci device 0000:03:0e.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
[    3.766342] EXT4-fs (loop0): mounted filesystem with ordered data mode. Opts: (null)
[    3.840078] firewire_core: created device fw0: GUID 00e148170000241d, S400
[    3.900094] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.903407] ata4.00: configured for UDMA/133
[    3.903417] ata4: EH complete
[    3.937303] ata4.00: exception Emask 0x50 SAct 0x1 SErr 0x280900 action 0x6 frozen
[    3.937306] ata4.00: irq_stat 0x08000000, interface fatal error
[    3.937309] ata4: SError: { UnrecovData HostInt 10B8B BadCRC }
[    3.937311] ata4.00: failed command: READ FPDMA QUEUED
[    3.937315] ata4.00: cmd 60/08:00:70:82:85/00:00:4a:00:00/40 tag 0 ncq 4096 in
[    3.937316]          res 40/00:04:70:82:85/00:00:4a:00:00/40 Emask 0x50 (ATA bus error)
[    3.937317] ata4.00: status: { DRDY }
[    3.937321] ata4: hard resetting link
[    4.480064] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.483006] ata4.00: configured for UDMA/133
[    4.483015] ata4: EH complete
[    4.504019] ata4.00: exception Emask 0x50 SAct 0x1 SErr 0x280900 action 0x6 frozen
[    4.504022] ata4.00: irq_stat 0x08000000, interface fatal error
[    4.504025] ata4: SError: { UnrecovData HostInt 10B8B BadCRC }
[    4.504027] ata4.00: failed command: READ FPDMA QUEUED
[    4.504031] ata4.00: cmd 60/08:00:70:82:85/00:00:4a:00:00/40 tag 0 ncq 4096 in
[    4.504032]          res 40/00:04:70:82:85/00:00:4a:00:00/40 Emask 0x50 (ATA bus error)
[    4.504034] ata4.00: status: { DRDY }
[    4.504037] ata4: hard resetting link
[    5.050066] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.053764] ata4.00: configured for UDMA/133
[    5.053775] ata4: EH complete
[    5.080462] ata4: limiting SATA link speed to 1.5 Gbps
[    5.080466] ata4.00: exception Emask 0x50 SAct 0x1 SErr 0x280900 action 0x6 frozen
[    5.080468] ata4.00: irq_stat 0x08000000, interface fatal error
[    5.080470] ata4: SError: { UnrecovData HostInt 10B8B BadCRC }
[    5.080473] ata4.00: failed command: READ FPDMA QUEUED
[    5.080476] ata4.00: cmd 60/08:00:b0:81:85/00:00:4a:00:00/40 tag 0 ncq 4096 in
[    5.080477]          res 40/00:04:b0:81:85/00:00:4a:00:00/40 Emask 0x50 (ATA bus error)
[    5.080479] ata4.00: status: { DRDY }
[    5.080483] ata4: hard resetting link
[    5.630085] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[    5.631214] ata4.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[    5.631217] ata4.00: revalidation failed (errno=-5)
[    5.868155] <30>udev[402]: starting version 167
[    6.617504] MCE: In-kernel MCE decoding enabled.
[    6.663245] parport_pc 00:09: reported by Plug and Play ACPI
[    6.663296] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    6.688955] EDAC MC: Ver: 2.1.0 Apr 11 2011
[    6.726779] ACPI: resource piix4_smbus [io  0x0b00-0x0b07] conflicts with ACPI region SOR1 [io 0xb00-0xb0f]
[    6.726781] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    6.760800] lp0: using parport0 (interrupt-driven).
[    6.771366] ppdev: user-space parallel port driver
[    6.792066] EDAC amd64_edac: v3.3.0
[    6.792311] EDAC amd64: DRAM ECC disabled.
[    6.792316] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[    6.792317]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[    6.792318]  (Note that use of the override may cause unknown side effects.)
[    6.809399] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
[    6.809494] SP5100 TCO timer: mmio address 0xfec000f0 already in use
[    6.821646] Linux video capture interface: v2.00
[    6.914682] uvcvideo: Found UVC 1.00 device USB Video Camera (0471:0334)
[    6.916702] input: USB Video Camera as /devices/pci0000:00/0000:00:12.2/usb1/1-3/1-3:1.0/input/input4
[    6.916780] usbcore: registered new interface driver uvcvideo
[    6.916782] USB Video Class driver (v1.0.0)
[    6.997735] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.094437] usbcore: registered new interface driver snd-usb-audio
[    7.189460] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    7.189522] HDA Intel 0000:01:00.1: irq 43 for MSI/MSI-X
[    7.189541] HDA Intel 0000:01:00.1: setting latency timer to 64
[    7.404850] type=1400 audit(1316008136.734:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=580 comm="apparmor_parser"
[    7.404864] type=1400 audit(1316008136.734:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=579 comm="apparmor_parser"
[    7.405100] type=1400 audit(1316008136.734:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=580 comm="apparmor_parser"
[    7.405119] type=1400 audit(1316008136.734:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=579 comm="apparmor_parser"
[    7.405262] type=1400 audit(1316008136.734:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=580 comm="apparmor_parser"
[    7.405289] type=1400 audit(1316008136.734:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=579 comm="apparmor_parser"
[    8.919504] Adding 262136k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:262136k 
[    8.966118] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro
[    9.424005] type=1400 audit(1316008138.754:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=799 comm="apparmor_parser"
[    9.424267] type=1400 audit(1316008138.754:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=799 comm="apparmor_parser"
[    9.424432] type=1400 audit(1316008138.754:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=799 comm="apparmor_parser"
[    9.447214] type=1400 audit(1316008138.774:11): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=798 comm="apparmor_parser"



```

---

### Post by diasf on 2011-09-14
My guess is apparmor. Everything seems fine, you even got the webcam recognized.

Try to disable apparmor. Check this link to find out exactly how:

[https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)

---

### Post by devilunix on 2011-09-15
thanks for reply .but i cant do it.i tried to uninstall apparmor completely .it didnt work anyway.

---

