---
title: "Toshiba Satellite touchpad not working with acpi on"
date: 2011-10-17
forum: Hardware
---

### Post by Luoti on 2011-10-17
Hi!

I have Toshiba Satellite L350D-J20. I have tried Fedora 14, Fedora 15, Ubuntu 10.04 and now I have Ubuntu 10.11 installed. My problelm is that when I have acpi on, everything else works fine, but touchpad does nothing. It is recognized by xinput and gives the following info:

```
SynPS/2 Synaptics TouchPad                  id=12    [slave  pointer  (2)]
    Reporting 3 classes:
        Class originated from: 12
        Buttons supported: 12
        Button labels: Button Left Button Middle Button Right Button Wheel Up Button Wheel Down Button Horiz Wheel Left Button Horiz Wheel Right None None None None None
        Button state:
        Class originated from: 12
        Detail for Valuator 0:
          Label: Rel X
          Range: 1472.000000 - 5866.000000
          Resolution: 72000 units/m
          Mode: relative
        Class originated from: 12
        Detail for Valuator 1:
          Label: Rel Y
          Range: 1408.000000 - 5756.000000
          Resolution: 131000 units/m
          Mode: relative

```USB-mouse is working fine all times. When I add acpi=off to kernel parameters, fn-keys stop working with volume control and all that stuff, but then touchpad works just fine. And when acpi is off, my CPUs second core is not recognized. How to debug this more? I have already tried to install synaptiks and "morprobe -r psmouse && modprobe psmouse" with no luck.

Here is my dmesg:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-12-generic (buildd@crested) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 (Ubuntu 3.0.0-12.20-generic 3.0.4)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=c054aa4b-26e5-437c-a4a1-ec758dc02b49 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000dfdd7000 (usable)
[    0.000000]  BIOS-e820: 00000000dfdd7000 - 00000000dfe3f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000dfe3f000 - 00000000dfe70000 (usable)
[    0.000000]  BIOS-e820: 00000000dfe70000 - 00000000dfebf000 (reserved)
[    0.000000]  BIOS-e820: 00000000dfebf000 - 00000000dfeed000 (usable)
[    0.000000]  BIOS-e820: 00000000dfeed000 - 00000000dfeff000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000dfeff000 - 00000000dff00000 (usable)
[    0.000000]  BIOS-e820: 00000000f7000000 - 00000000f8000000 (reserved)
[    0.000000]  BIOS-e820: 00000000feb00000 - 00000000feb01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000110000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.4 present.
[    0.000000] DMI: TOSHIBA Satellite L350D/Portable PC, BIOS 1.80 09/01/2009
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x110000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 base 0080000000 mask FFC0000000 write-back
[    0.000000]   2 base 00C0000000 mask FFE0000000 write-back
[    0.000000]   3 base 00FFF00000 mask FFFFF00000 write-protect
[    0.000000]   4 base 0100000000 mask FFF0000000 write-back
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 base 00DFE3E000 mask FFFFFFF000 uncachable
[    0.000000] TOM2: 0000000120000000 aka 4608M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] last_pfn = 0xdff00 max_arch_pfn = 0x400000000
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff88000009a000] 9a000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-00000000dff00000
[    0.000000]  0000000000 - 00dfe00000 page 2M
[    0.000000]  00dfe00000 - 00dff00000 page 4k
[    0.000000] kernel direct mapping tables up to dff00000 @ dfee7000-dfeed000
[    0.000000] init_memory_mapping: 0000000100000000-0000000110000000
[    0.000000]  0100000000 - 0110000000 page 2M
[    0.000000] kernel direct mapping tables up to 110000000 @ 10fffa000-110000000
[    0.000000] RAMDISK: 365b8000 - 372d4000
[    0.000000] ACPI: RSDP 00000000000fe020 00024 (v02 TOSINV)
[    0.000000] ACPI: XSDT 00000000dfefe120 0006C (v01 TOSINV TOSINV00 00000003      01000013)
[    0.000000] ACPI: FACP 00000000dfefd000 000F4 (v04 TOSINV TOSINV00 00000003 MSFT 01000013)
[    0.000000] ACPI: DSDT 00000000dfef2000 07CCC (v01 TOSINV TOSINV00 F0000000 MSFT 01000013)
[    0.000000] ACPI: FACS 00000000dfde0000 00040
[    0.000000] ACPI: HPET 00000000dfefc000 00038 (v01 TOSINV TOSINV00 00000001 MSFT 01000013)
[    0.000000] ACPI: APIC 00000000dfefb000 00084 (v02 TOSINV TOSINV00 00000001 MSFT 01000013)
[    0.000000] ACPI: MCFG 00000000dfefa000 0003C (v01 TOSINV TOSINV00 00000001 MSFT 01000013)
[    0.000000] ACPI: SLIC 00000000dfef1000 00176 (v01 TOSINV TOSINV00 00000001 MSFT 01000013)
[    0.000000] ACPI: BOOT 00000000dfef0000 00028 (v01 TOSINV TOSINV00 00000001 MSFT 01000013)
[    0.000000] ACPI: SSDT 00000000dfeef000 002BE (v01 AMD    PowerNow 00000001 AMD  00000001)
[    0.000000] ACPI: SRAT 00000000dfeee000 000A0 (v03 AMD    AMD CRB  00000001 AMD  00000001)
[    0.000000] ACPI: MSCT 00000000dfeed000 0004E (v01 AMD    AMD CRB  00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] SRAT: PXM 0 -> APIC 0x00 -> Node 0
[    0.000000] SRAT: PXM 0 -> APIC 0x01 -> Node 0
[    0.000000] SRAT: Node 0 PXM 0 0-e0000000
[    0.000000] SRAT: Node 0 PXM 0 100000000-120000000
[    0.000000] NUMA: Node 0 [0,e0000000) + [100000000,110000000) -> [0,110000000)
[    0.000000] Initmem setup node 0 0000000000000000-0000000110000000
[    0.000000]   NODE_DATA [000000010fffb000 - 000000010fffffff]
[    0.000000]  [ffffea0000000000-ffffea0003bfffff] PMD -> [ffff88010ba00000-ffff88010effffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00110000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[6] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000dfdd7
[    0.000000]     0: 0x000dfe3f -> 0x000dfe70
[    0.000000]     0: 0x000dfebf -> 0x000dfeed
[    0.000000]     0: 0x000dfeff -> 0x000dff00
[    0.000000]     0: 0x00100000 -> 0x00110000
[    0.000000] On node 0 totalpages: 982470
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3922 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 898671 pages, LIFO batch:31
[    0.000000]   Normal zone: 896 pages used for memmap
[    0.000000]   Normal zone: 64640 pages, LIFO batch:15
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x1002a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000dfdd7000 - 00000000dfe3f000
[    0.000000] PM: Registered nosave memory: 00000000dfe70000 - 00000000dfebf000
[    0.000000] PM: Registered nosave memory: 00000000dfeed000 - 00000000dfeff000
[    0.000000] PM: Registered nosave memory: 00000000dff00000 - 00000000f7000000
[    0.000000] PM: Registered nosave memory: 00000000f7000000 - 00000000f8000000
[    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000feb00000
[    0.000000] PM: Registered nosave memory: 00000000feb00000 - 00000000feb01000
[    0.000000] PM: Registered nosave memory: 00000000feb01000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000fff00000
[    0.000000] PM: Registered nosave memory: 00000000fff00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at dff00000 (gap: dff00000:17100000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88010fc00000 s79616 r8192 d22784 u524288
[    0.000000] pcpu-alloc: s79616 r8192 d22784 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 967233
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=c054aa4b-26e5-437c-a4a1-ec758dc02b49 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3781188k/4456448k available (6104k kernel code, 526568k absent, 148692k reserved, 4880k data, 984k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 31457280 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2098.926 MHz processor.
[    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 4197.85 BogoMIPS (lpj=8395704)
[    0.004011] pid_max: default: 32768 minimum: 301
[    0.004047] Security Framework initialized
[    0.004066] AppArmor: AppArmor initialized
[    0.004068] Yama: becoming mindful.
[    0.004584] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.007475] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.008945] Mount-cache hash table entries: 256
[    0.009136] Initializing cgroup subsys cpuacct
[    0.009144] Initializing cgroup subsys memory
[    0.009156] Initializing cgroup subsys devices
[    0.009159] Initializing cgroup subsys freezer
[    0.009161] Initializing cgroup subsys net_cls
[    0.009164] Initializing cgroup subsys blkio
[    0.009175] Initializing cgroup subsys perf_event
[    0.009212] tseg: 00dff00000
[    0.009215] CPU: Physical Processor ID: 0
[    0.009217] CPU: Processor Core ID: 0
[    0.009220] mce: CPU supports 5 MCE banks
[    0.011769] ACPI: Core revision 20110413
[    0.011775] TOSHIBA Satellite detected - force copy of DSDT to local memory
[    0.011921] ACPI: Forced DSDT copy: length 0x07CCC copied locally, original unmapped
[    0.020028] ftrace: allocating 25651 entries in 101 pages
[    0.024465] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.067551] CPU0: AMD Athlon(tm) X2 Dual-Core QL-64 stepping 01
[    0.068003] Performance Events: AMD PMU driver.
[    0.068003] ... version:                0
[    0.068003] ... bit width:              48
[    0.068003] ... generic registers:      4
[    0.068003] ... value mask:             0000ffffffffffff
[    0.068003] ... max period:             00007fffffffffff
[    0.068003] ... fixed-purpose events:   0
[    0.068003] ... event mask:             000000000000000f
[    0.068003] Booting Node   0, Processors  #1
[    0.068003] smpboot cpu 1: start_ip = 9a000
[    0.156009] TSC synchronization [CPU#0 -> CPU#1]:
[    0.156009] Measured 74892915 cycles TSC warp between CPUs, turning off TSC clock.
[    0.156009] Marking TSC unstable due to check_tsc_sync_source failed
[    0.156023] Brought up 2 CPUs
[    0.156026] Total of 2 processors activated (8387.53 BogoMIPS).
[    0.156526] devtmpfs: initialized
[    0.156526] PM: Registering ACPI NVS region at dfdd7000 (425984 bytes)
[    0.157836] print_constraints: dummy: 
[    0.157866] Time: 17:03:28  Date: 10/17/11
[    0.157925] NET: Registered protocol family 16
[    0.157979] Trying to unpack rootfs image as initramfs...
[    0.158109] TOM: 00000000e0000000 aka 3584M
[    0.158112] Fam 10h mmconf [f7000000, f7ffffff]
[    0.158121] TOM2: 0000000120000000 aka 4608M
[    0.158217] Extended Config Space enabled on 0 nodes
[    0.158235] ACPI: bus type pci registered
[    0.158335] PCI: MMCONFIG for domain 0000 [bus 00-0f] at [mem 0xf7000000-0xf7ffffff] (base 0xf7000000)
[    0.158340] PCI: MMCONFIG at [mem 0xf7000000-0xf7ffffff] reserved in E820
[    0.161855] PCI: Using configuration type 1 for base access
[    0.161887] mtrr: your CPUs had inconsistent variable MTRR settings
[    0.161889] mtrr: probably your BIOS does not setup all CPUs.
[    0.161890] mtrr: corrected configuration.
[    0.162891] bio: create slab <bio-0> at 0
[    0.164750] ACPI: EC: Look up EC in DSDT
[    0.167036] ACPI: Executed 1 blocks of module-level executable AML code
[    0.169946] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.510454] Freeing initrd memory: 13424k freed
[    0.636090] ACPI: Interpreter enabled
[    0.636097] ACPI: (supports S0 S3 S4 S5)
[    0.636136] ACPI: Using IOAPIC for interrupt routing
[    0.647986] ACPI: Power Resource [PFA1] (off)
[    0.648492] ACPI: EC: GPE = 0x7, I/O: command/status = 0x66, data = 0x62
[    0.648758] ACPI: No dock devices found.
[    0.648761] HEST: Table not found.
[    0.648765] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.649444] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.650758] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.650761] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.650764] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.650767] pci_root PNP0A08:00: host bridge window [mem 0x000c0000-0x000c3fff]
[    0.650770] pci_root PNP0A08:00: host bridge window [mem 0x000c4000-0x000c7fff]
[    0.650773] pci_root PNP0A08:00: host bridge window [mem 0x000c8000-0x000cbfff]
[    0.650776] pci_root PNP0A08:00: host bridge window [mem 0x000cc000-0x000cffff]
[    0.650779] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
[    0.650782] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.650785] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.650788] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
[    0.650791] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff]
[    0.650794] pci_root PNP0A08:00: host bridge window [mem 0x000e4000-0x000e7fff]
[    0.650796] pci_root PNP0A08:00: host bridge window [mem 0x000e8000-0x000ebfff]
[    0.650799] pci_root PNP0A08:00: host bridge window [mem 0x000ec000-0x000effff]
[    0.650802] pci_root PNP0A08:00: host bridge window [mem 0xe0000000-0xf6ffffff]
[    0.650805] pci_root PNP0A08:00: host bridge window [mem 0xf8000000-0xffffffff]
[    0.650814] pci_root PNP0A08:00: address space collision: host bridge window [mem 0x000cc000-0x000cffff] conflicts with Video ROM [mem 0x000c0000-0x000cebff]
[    0.650837] pci 0000:00:00.0: [1022:9600] type 0 class 0x000600
[    0.650910] pci 0000:00:01.0: [1022:9602] type 1 class 0x000604
[    0.650965] pci 0000:00:04.0: [1022:9604] type 1 class 0x000604
[    0.651008] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    0.651013] pci 0000:00:04.0: PME# disabled
[    0.651034] pci 0000:00:05.0: [1022:9605] type 1 class 0x000604
[    0.651077] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.651081] pci 0000:00:05.0: PME# disabled
[    0.651102] pci 0000:00:06.0: [1022:9606] type 1 class 0x000604
[    0.651144] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.651148] pci 0000:00:06.0: PME# disabled
[    0.651194] pci 0000:00:11.0: [1002:4391] type 0 class 0x000106
[    0.651218] pci 0000:00:11.0: reg 10: [io  0x7038-0x703f]
[    0.651231] pci 0000:00:11.0: reg 14: [io  0x704c-0x704f]
[    0.651243] pci 0000:00:11.0: reg 18: [io  0x7030-0x7037]
[    0.651256] pci 0000:00:11.0: reg 1c: [io  0x7048-0x704b]
[    0.651268] pci 0000:00:11.0: reg 20: [io  0x7010-0x701f]
[    0.651281] pci 0000:00:11.0: reg 24: [mem 0xf6408000-0xf64083ff]
[    0.651342] pci 0000:00:12.0: [1002:4397] type 0 class 0x000c03
[    0.651359] pci 0000:00:12.0: reg 10: [mem 0xf6407000-0xf6407fff]
[    0.651441] pci 0000:00:12.1: [1002:4398] type 0 class 0x000c03
[    0.651458] pci 0000:00:12.1: reg 10: [mem 0xf6406000-0xf6406fff]
[    0.651547] pci 0000:00:12.2: [1002:4396] type 0 class 0x000c03
[    0.652044] pci 0000:00:12.2: reg 10: [mem 0xf6408500-0xf64085ff]
[    0.657877] pci 0000:00:12.2: supports D1 D2
[    0.657879] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.657884] pci 0000:00:12.2: PME# disabled
[    0.657913] pci 0000:00:13.0: [1002:4397] type 0 class 0x000c03
[    0.657930] pci 0000:00:13.0: reg 10: [mem 0xf6405000-0xf6405fff]
[    0.658012] pci 0000:00:13.1: [1002:4398] type 0 class 0x000c03
[    0.658029] pci 0000:00:13.1: reg 10: [mem 0xf6404000-0xf6404fff]
[    0.658117] pci 0000:00:13.2: [1002:4396] type 0 class 0x000c03
[    0.659038] pci 0000:00:13.2: reg 10: [mem 0xf6408400-0xf64084ff]
[    0.664528] pci 0000:00:13.2: supports D1 D2
[    0.664530] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.664536] pci 0000:00:13.2: PME# disabled
[    0.664568] pci 0000:00:14.0: [1002:4385] type 0 class 0x000c05
[    0.664687] pci 0000:00:14.1: [1002:439c] type 0 class 0x000101
[    0.664709] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
[    0.664721] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
[    0.664734] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
[    0.664746] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
[    0.664759] pci 0000:00:14.1: reg 20: [io  0x7000-0x700f]
[    0.664825] pci 0000:00:14.2: [1002:4383] type 0 class 0x000403
[    0.664854] pci 0000:00:14.2: reg 10: [mem 0xf6400000-0xf6403fff 64bit]
[    0.664927] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.664933] pci 0000:00:14.2: PME# disabled
[    0.664951] pci 0000:00:14.3: [1002:439d] type 0 class 0x000601
[    0.665047] pci 0000:00:14.4: [1002:4384] type 1 class 0x000604
[    0.665107] pci 0000:00:18.0: [1022:1300] type 0 class 0x000600
[    0.665142] pci 0000:00:18.1: [1022:1301] type 0 class 0x000600
[    0.665170] pci 0000:00:18.2: [1022:1302] type 0 class 0x000600
[    0.665200] pci 0000:00:18.3: [1022:1303] type 0 class 0x000600
[    0.665234] pci 0000:00:18.4: [1022:1304] type 0 class 0x000600
[    0.665316] pci 0000:01:05.0: [1002:9613] type 0 class 0x000300
[    0.665330] pci 0000:01:05.0: reg 10: [mem 0xe0000000-0xefffffff pref]
[    0.665338] pci 0000:01:05.0: reg 14: [io  0x6000-0x60ff]
[    0.665345] pci 0000:01:05.0: reg 18: [mem 0xf6300000-0xf630ffff]
[    0.665363] pci 0000:01:05.0: reg 24: [mem 0xf6200000-0xf62fffff]
[    0.665383] pci 0000:01:05.0: supports D1 D2
[    0.665433] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.665439] pci 0000:00:01.0:   bridge window [io  0x6000-0x6fff]
[    0.665443] pci 0000:00:01.0:   bridge window [mem 0xf6200000-0xf63fffff]
[    0.665449] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[    0.665487] pci 0000:00:04.0: PCI bridge to [bus 02-03]
[    0.665492] pci 0000:00:04.0:   bridge window [io  0x5000-0x5fff]
[    0.665496] pci 0000:00:04.0:   bridge window [mem 0xf5200000-0xf61fffff]
[    0.665502] pci 0000:00:04.0:   bridge window [mem 0xf0000000-0xf0ffffff 64bit pref]
[    0.665556] pci 0000:04:00.0: [10ec:8136] type 0 class 0x000200
[    0.665573] pci 0000:04:00.0: reg 10: [io  0x3000-0x30ff]
[    0.665600] pci 0000:04:00.0: reg 18: [mem 0xf1010000-0xf1010fff 64bit pref]
[    0.665617] pci 0000:04:00.0: reg 20: [mem 0xf1000000-0xf100ffff 64bit pref]
[    0.665630] pci 0000:04:00.0: reg 30: [mem 0xfffe0000-0xffffffff pref]
[    0.665666] pci 0000:04:00.0: supports D1 D2
[    0.665669] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.665674] pci 0000:04:00.0: PME# disabled
[    0.672063] pci 0000:00:05.0: PCI bridge to [bus 04-04]
[    0.672069] pci 0000:00:05.0:   bridge window [io  0x3000-0x4fff]
[    0.672073] pci 0000:00:05.0:   bridge window [mem 0xf4200000-0xf51fffff]
[    0.672079] pci 0000:00:05.0:   bridge window [mem 0xf1000000-0xf20fffff 64bit pref]
[    0.672185] pci 0000:05:00.0: [168c:001c] type 0 class 0x000200
[    0.672274] pci 0000:05:00.0: reg 10: [mem 0xf3100000-0xf310ffff 64bit]
[    0.672731] pci 0000:05:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.672754] pci 0000:00:06.0: PCI bridge to [bus 05-05]
[    0.672759] pci 0000:00:06.0:   bridge window [io  0x2000-0x2fff]
[    0.672763] pci 0000:00:06.0:   bridge window [mem 0xf3100000-0xf41fffff]
[    0.672769] pci 0000:00:06.0:   bridge window [mem 0xf2100000-0xf30fffff 64bit pref]
[    0.672847] pci 0000:00:14.4: PCI bridge to [bus 80-8f]
[    0.672852] pci 0000:00:14.4:   bridge window [io  0x1000-0x1fff]
[    0.672858] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.672864] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.672887] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.673114] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.673192] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[    0.673267] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]
[    0.673340] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[    0.673467] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.673530]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.673535]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.673537] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.683838] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.683902] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.683962] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.684024] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.684104] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.684164] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.684226] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.684291] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.684466] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.684471] vgaarb: loaded
[    0.684473] vgaarb: bridge control possible 0000:01:05.0
[    0.684758] SCSI subsystem initialized
[    0.684788] libata version 3.00 loaded.
[    0.684788] usbcore: registered new interface driver usbfs
[    0.684788] usbcore: registered new interface driver hub
[    0.684788] usbcore: registered new device driver usb
[    0.684788] PCI: Using ACPI for IRQ routing
[    0.684788] PCI: pci_cache_line_size set to 64 bytes
[    0.684788] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.684788] reserve RAM buffer: 00000000dfdd7000 - 00000000dfffffff 
[    0.684788] reserve RAM buffer: 00000000dfe70000 - 00000000dfffffff 
[    0.684788] reserve RAM buffer: 00000000dfeed000 - 00000000dfffffff 
[    0.684788] reserve RAM buffer: 00000000dff00000 - 00000000dfffffff 
[    0.684895] NetLabel: Initializing
[    0.684897] NetLabel:  domain hash size = 128
[    0.684899] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.684916] NetLabel:  unlabeled traffic allowed by default
[    0.684989] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.684996] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.687027] Switching to clocksource hpet
[    0.688111] Switched to NOHz mode on CPU #1
[    0.691923] Switched to NOHz mode on CPU #0
[    0.697516] AppArmor: AppArmor Filesystem Enabled
[    0.697564] pnp: PnP ACPI init
[    0.697591] ACPI: bus type pnp registered
[    0.698686] pnp 00:00: [bus 00-ff]
[    0.698690] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.698693] pnp 00:00: [io  0x0d00-0xffff window]
[    0.698696] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.698699] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.698702] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.698705] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.698708] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.698711] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.698713] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.698716] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.698719] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.698722] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.698725] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.698727] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.698730] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.698733] pnp 00:00: [mem 0xe0000000-0xf6ffffff window]
[    0.698736] pnp 00:00: [mem 0xf8000000-0xffffffff window]
[    0.698743] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.698867] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.698946] pnp 00:01: [mem 0xfec00000-0xfec00fff]
[    0.698949] pnp 00:01: [mem 0xfee00000-0xfee00fff]
[    0.699034] system 00:01: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.699038] system 00:01: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.699042] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.699210] pnp 00:02: [irq 0 disabled]
[    0.699225] pnp 00:02: [irq 8]
[    0.699227] pnp 00:02: [mem 0xfed00000-0xfed003ff]
[    0.699266] pnp 00:02: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.699369] pnp 00:03: [io  0x0000-0x000f]
[    0.699372] pnp 00:03: [io  0x0081-0x008f]
[    0.699374] pnp 00:03: [io  0x00c0-0x00df]
[    0.699377] pnp 00:03: [dma 4]
[    0.699422] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.699434] pnp 00:04: [io  0x00f0-0x00fe]
[    0.699444] pnp 00:04: [irq 13]
[    0.699488] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.699536] pnp 00:05: [io  0x0070-0x0071]
[    0.699588] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.699600] pnp 00:06: [io  0x0061]
[    0.699650] pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.699665] pnp 00:07: [io  0x0060]
[    0.699667] pnp 00:07: [io  0x0064]
[    0.699673] pnp 00:07: [irq 1]
[    0.699725] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.699765] pnp 00:08: [irq 12]
[    0.699819] pnp 00:08: Plug and Play ACPI device, IDs SYN1913 SYN0700 SYN0002 PNP0f13 (active)
[    0.699843] pnp 00:09: [io  0x0010-0x001f]
[    0.699845] pnp 00:09: [io  0x002e-0x002f]
[    0.699848] pnp 00:09: [io  0x0068]
[    0.699850] pnp 00:09: [io  0x006c]
[    0.699852] pnp 00:09: [io  0x0072-0x0073]
[    0.699855] pnp 00:09: [io  0x0080]
[    0.699857] pnp 00:09: [io  0x00b0-0x00b1]
[    0.699859] pnp 00:09: [io  0x0092]
[    0.699862] pnp 00:09: [io  0x0400-0x04cf]
[    0.699864] pnp 00:09: [io  0x04d0-0x04d1]
[    0.699867] pnp 00:09: [io  0x04d6]
[    0.699869] pnp 00:09: [io  0x0680-0x06ff]
[    0.699871] pnp 00:09: [io  0x077a]
[    0.699874] pnp 00:09: [io  0x0c00-0x0c01]
[    0.699876] pnp 00:09: [io  0x0c14]
[    0.699878] pnp 00:09: [io  0x0c50-0x0c52]
[    0.699881] pnp 00:09: [io  0x0c6c]
[    0.699883] pnp 00:09: [io  0x0c6f]
[    0.699885] pnp 00:09: [io  0x0cd0-0x0cdb]
[    0.699888] pnp 00:09: [io  0x0022-0x0023]
[    0.699890] pnp 00:09: [io  0x00b8]
[    0.699892] pnp 00:09: [io  0x0800-0x0804]
[    0.699895] pnp 00:09: [io  0x0b00-0x0b3f]
[    0.699897] pnp 00:09: [io  0x0cdc-0x0cdf]
[    0.700049] system 00:09: [io  0x0400-0x04cf] has been reserved
[    0.700053] system 00:09: [io  0x04d0-0x04d1] has been reserved
[    0.700056] system 00:09: [io  0x04d6] has been reserved
[    0.700060] system 00:09: [io  0x0680-0x06ff] has been reserved
[    0.700063] system 00:09: [io  0x077a] has been reserved
[    0.700066] system 00:09: [io  0x0c00-0x0c01] has been reserved
[    0.700070] system 00:09: [io  0x0c14] has been reserved
[    0.700073] system 00:09: [io  0x0c50-0x0c52] has been reserved
[    0.700076] system 00:09: [io  0x0c6c] has been reserved
[    0.700080] system 00:09: [io  0x0c6f] has been reserved
[    0.700083] system 00:09: [io  0x0cd0-0x0cdb] has been reserved
[    0.700087] system 00:09: [io  0x0800-0x0804] has been reserved
[    0.700090] system 00:09: [io  0x0b00-0x0b3f] has been reserved
[    0.700094] system 00:09: [io  0x0cdc-0x0cdf] has been reserved
[    0.700098] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.700179] pnp 00:0a: [mem 0xff800000-0xff80ffff]
[    0.700182] pnp 00:0a: [mem 0x000e0000-0x000fffff]
[    0.700185] pnp 00:0a: [mem 0xfeb00000-0xfeb00fff]
[    0.700187] pnp 00:0a: [mem 0xfff00000-0xffffffff]
[    0.700278] system 00:0a: [mem 0xff800000-0xff80ffff] has been reserved
[    0.700282] system 00:0a: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.700285] system 00:0a: [mem 0xfeb00000-0xfeb00fff] has been reserved
[    0.700289] system 00:0a: [mem 0xfff00000-0xffffffff] has been reserved
[    0.700293] system 00:0a: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.700787] pnp: PnP ACPI: found 11 devices
[    0.700790] ACPI: ACPI bus type pnp unregistered
[    0.707404] pci 0000:04:00.0: no compatible bridge window for [mem 0xfffe0000-0xffffffff pref]
[    0.707413] PCI: max bus depth: 1 pci_try_num: 2
[    0.707455] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.707459] pci 0000:00:01.0:   bridge window [io  0x6000-0x6fff]
[    0.707464] pci 0000:00:01.0:   bridge window [mem 0xf6200000-0xf63fffff]
[    0.707468] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[    0.707474] pci 0000:00:04.0: PCI bridge to [bus 02-03]
[    0.707477] pci 0000:00:04.0:   bridge window [io  0x5000-0x5fff]
[    0.707482] pci 0000:00:04.0:   bridge window [mem 0xf5200000-0xf61fffff]
[    0.707486] pci 0000:00:04.0:   bridge window [mem 0xf0000000-0xf0ffffff 64bit pref]
[    0.707496] pci 0000:04:00.0: BAR 6: assigned [mem 0xf1020000-0xf103ffff pref]
[    0.707500] pci 0000:00:05.0: PCI bridge to [bus 04-04]
[    0.707503] pci 0000:00:05.0:   bridge window [io  0x3000-0x4fff]
[    0.707508] pci 0000:00:05.0:   bridge window [mem 0xf4200000-0xf51fffff]
[    0.707512] pci 0000:00:05.0:   bridge window [mem 0xf1000000-0xf20fffff 64bit pref]
[    0.707518] pci 0000:00:06.0: PCI bridge to [bus 05-05]
[    0.707522] pci 0000:00:06.0:   bridge window [io  0x2000-0x2fff]
[    0.707526] pci 0000:00:06.0:   bridge window [mem 0xf3100000-0xf41fffff]
[    0.707531] pci 0000:00:06.0:   bridge window [mem 0xf2100000-0xf30fffff 64bit pref]
[    0.707536] pci 0000:00:14.4: PCI bridge to [bus 80-8f]
[    0.707544] pci 0000:00:14.4:   bridge window [io  0x1000-0x1fff]
[    0.707551] pci 0000:00:14.4:   bridge window [mem disabled]
[    0.707556] pci 0000:00:14.4:   bridge window [mem pref disabled]
[    0.707573] pci 0000:00:01.0: setting latency timer to 64
[    0.707597] pci 0000:00:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.707601] pci 0000:00:04.0: setting latency timer to 64
[    0.707613] pci 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.707617] pci 0000:00:05.0: setting latency timer to 64
[    0.707627] pci 0000:00:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.707631] pci 0000:00:06.0: setting latency timer to 64
[    0.707642] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.707645] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.707648] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.707651] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.707654] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.707657] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.707660] pci_bus 0000:00: resource 10 [mem 0x000d0000-0x000d3fff]
[    0.707662] pci_bus 0000:00: resource 11 [mem 0x000d4000-0x000d7fff]
[    0.707665] pci_bus 0000:00: resource 12 [mem 0x000d8000-0x000dbfff]
[    0.707668] pci_bus 0000:00: resource 13 [mem 0x000dc000-0x000dffff]
[    0.707671] pci_bus 0000:00: resource 14 [mem 0x000e0000-0x000e3fff]
[    0.707674] pci_bus 0000:00: resource 15 [mem 0x000e4000-0x000e7fff]
[    0.707677] pci_bus 0000:00: resource 16 [mem 0x000e8000-0x000ebfff]
[    0.707680] pci_bus 0000:00: resource 17 [mem 0x000ec000-0x000effff]
[    0.707683] pci_bus 0000:00: resource 18 [mem 0xe0000000-0xf6ffffff]
[    0.707686] pci_bus 0000:00: resource 19 [mem 0xf8000000-0xffffffff]
[    0.707689] pci_bus 0000:01: resource 0 [io  0x6000-0x6fff]
[    0.707692] pci_bus 0000:01: resource 1 [mem 0xf6200000-0xf63fffff]
[    0.707695] pci_bus 0000:01: resource 2 [mem 0xe0000000-0xefffffff 64bit pref]
[    0.707698] pci_bus 0000:02: resource 0 [io  0x5000-0x5fff]
[    0.707701] pci_bus 0000:02: resource 1 [mem 0xf5200000-0xf61fffff]
[    0.707704] pci_bus 0000:02: resource 2 [mem 0xf0000000-0xf0ffffff 64bit pref]
[    0.707707] pci_bus 0000:04: resource 0 [io  0x3000-0x4fff]
[    0.707710] pci_bus 0000:04: resource 1 [mem 0xf4200000-0xf51fffff]
[    0.707713] pci_bus 0000:04: resource 2 [mem 0xf1000000-0xf20fffff 64bit pref]
[    0.707716] pci_bus 0000:05: resource 0 [io  0x2000-0x2fff]
[    0.707719] pci_bus 0000:05: resource 1 [mem 0xf3100000-0xf41fffff]
[    0.707722] pci_bus 0000:05: resource 2 [mem 0xf2100000-0xf30fffff 64bit pref]
[    0.707726] pci_bus 0000:80: resource 0 [io  0x1000-0x1fff]
[    0.707783] NET: Registered protocol family 2
[    0.708049] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.710140] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.715385] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.716055] TCP: Hash tables configured (established 524288 bind 65536)
[    0.716059] TCP reno registered
[    0.716081] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.716137] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.716325] NET: Registered protocol family 1
[    0.716342] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
[    0.892057] pci 0000:01:05.0: Boot video device
[    0.892071] PCI: CLS 64 bytes, default 64
[    0.892074] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.892077] Placing 64MB software IO TLB between ffff8800dbdd7000 - ffff8800dfdd7000
[    0.892080] software IO TLB at phys 0xdbdd7000 - 0xdfdd7000
[    0.892106] Simple Boot Flag at 0x44 set to 0x1
[    0.892545] audit: initializing netlink socket (disabled)
[    0.892559] type=2000 audit(1318871008.888:1): initialized
[    0.934566] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.970998] VFS: Disk quotas dquot_6.5.2
[    0.971077] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.971938] fuse init (API version 7.16)
[    0.972115] msgmni has been set to 7411
[    0.972753] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.972809] io scheduler noop registered
[    0.972812] io scheduler deadline registered
[    0.972869] io scheduler cfq registered (default)
[    0.973043] pcieport 0000:00:04.0: setting latency timer to 64
[    0.973092] pcieport 0000:00:04.0: irq 40 for MSI/MSI-X
[    0.973158] pcieport 0000:00:05.0: setting latency timer to 64
[    0.973194] pcieport 0000:00:05.0: irq 41 for MSI/MSI-X
[    0.973251] pcieport 0000:00:06.0: setting latency timer to 64
[    0.973287] pcieport 0000:00:06.0: irq 42 for MSI/MSI-X
[    0.973381] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.973411] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.973586] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.973676] ACPI: AC Adapter [ADP0] (on-line)
[    0.973871] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.973878] ACPI: Power Button [PWRB]
[    0.973930] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    0.976248] ACPI: Lid Switch [LID]
[    0.976310] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.976314] ACPI: Power Button [PWRF]
[    0.976405] ACPI: Fan [FAN1] (off)
[    0.976413] ACPI: acpi_idle registered with cpuidle
[    0.991131] thermal LNXTHERM:00: registered as thermal_zone0
[    0.991134] ACPI: Thermal Zone [THZN] (64 C)
[    0.991156] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.991188] ERST: Table is not found!
[    0.991312] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.995374] ACPI: Battery Slot [BAT0] (battery present)
[    1.044539] Linux agpgart interface v0.103
[    1.046036] brd: module loaded
[    1.046760] loop: module loaded
[    1.047040] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.047093] pata_acpi 0000:00:14.1: setting latency timer to 64
[    1.047529] Fixed MDIO Bus: probed
[    1.047563] PPP generic driver version 2.4.2
[    1.047624] tun: Universal TUN/TAP device driver, 1.6
[    1.047627] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.047737] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.047760] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.047804] ehci_hcd 0000:00:12.2: setting latency timer to 64
[    1.047809] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    1.047858] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.047871] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.047904] QUIRK: Enable AMD PLL fix
[    1.047908] ehci_hcd 0000:00:12.2: applying AMD SB600/SB700 USB freeze workaround
[    1.047925] ehci_hcd 0000:00:12.2: debug port 1
[    1.047963] ehci_hcd 0000:00:12.2: irq 17, io mem 0xf6408500
[    1.056025] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.056186] hub 1-0:1.0: USB hub found
[    1.056192] hub 1-0:1.0: 6 ports detected
[    1.056388] ehci_hcd 0000:00:13.2: power state changed by ACPI to D0
[    1.056398] ehci_hcd 0000:00:13.2: power state changed by ACPI to D0
[    1.056419] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.056438] ehci_hcd 0000:00:13.2: setting latency timer to 64
[    1.056442] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.056490] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.056504] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.056523] ehci_hcd 0000:00:13.2: applying AMD SB600/SB700 USB freeze workaround
[    1.056539] ehci_hcd 0000:00:13.2: debug port 1
[    1.056567] ehci_hcd 0000:00:13.2: irq 19, io mem 0xf6408400
[    1.068023] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.068165] hub 2-0:1.0: USB hub found
[    1.068170] hub 2-0:1.0: 6 ports detected
[    1.068279] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.068301] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.068321] ohci_hcd 0000:00:12.0: setting latency timer to 64
[    1.068325] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.068374] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.068410] ohci_hcd 0000:00:12.0: irq 16, io mem 0xf6407000
[    1.128138] hub 3-0:1.0: USB hub found
[    1.128150] hub 3-0:1.0: 3 ports detected
[    1.128239] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.128253] ohci_hcd 0000:00:12.1: setting latency timer to 64
[    1.128257] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    1.128305] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    1.128330] ohci_hcd 0000:00:12.1: irq 16, io mem 0xf6406000
[    1.188138] hub 4-0:1.0: USB hub found
[    1.188149] hub 4-0:1.0: 3 ports detected
[    1.188238] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.188252] ohci_hcd 0000:00:13.0: setting latency timer to 64
[    1.188256] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.188311] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.188346] ohci_hcd 0000:00:13.0: irq 18, io mem 0xf6405000
[    1.248137] hub 5-0:1.0: USB hub found
[    1.248149] hub 5-0:1.0: 3 ports detected
[    1.248253] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.248268] ohci_hcd 0000:00:13.1: setting latency timer to 64
[    1.248272] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    1.248318] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    1.248346] ohci_hcd 0000:00:13.1: irq 18, io mem 0xf6404000
[    1.308135] hub 6-0:1.0: USB hub found
[    1.308146] hub 6-0:1.0: 3 ports detected
[    1.308236] uhci_hcd: USB Universal Host Controller Interface driver
[    1.308349] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.333392] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.333399] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.333551] mousedev: PS/2 mouse device common for all mice
[    1.334480] rtc_cmos 00:05: RTC can wake from S4
[    1.334603] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.334636] rtc0: alarms up to one day, 114 bytes nvram, hpet irqs
[    1.334774] device-mapper: uevent: version 1.0.3
[    1.334865] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    1.334880] cpuidle: using governor ladder
[    1.334882] cpuidle: using governor menu
[    1.334885] EFI Variables Facility v0.08 2004-May-17
[    1.335285] TCP cubic registered
[    1.335449] NET: Registered protocol family 10
[    1.336227] NET: Registered protocol family 17
[    1.336255] Registering the dns_resolver key type
[    1.336390] PM: Hibernation image not present or could not be loaded.
[    1.336408] registered taskstats version 1
[    1.363444]   Magic number: 15:617:87
[    1.363518] button LNXPWRBN:00: hash matches
[    1.363592] rtc_cmos 00:05: setting system clock to 2011-10-17 17:03:30 UTC (1318871010)
[    1.363604] powernow-k8: Found 1 AMD Athlon(tm) X2 Dual-Core QL-64 (2 cpu cores) (version 2.20.00)
[    1.363700] powernow-k8:    0 : pstate 0 (2100 MHz)
[    1.363703] powernow-k8:    1 : pstate 1 (1050 MHz)
[    1.364469] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.364471] EDD information not available.
[    1.366679] Freeing unused kernel memory: 984k freed
[    1.367215] Write protecting the kernel read-only data: 10240k
[    1.367478] Freeing unused kernel memory: 20k freed
[    1.372797] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.373777] Freeing unused kernel memory: 1400k freed
[    1.403291] udevd[81]: starting version 173
[    1.424068] usb 2-2: new high speed USB device number 2 using ehci_hcd
[    1.523464] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.523495] r8169 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.523551] r8169 0000:04:00.0: setting latency timer to 64
[    1.523608] r8169 0000:04:00.0: irq 43 for MSI/MSI-X
[    1.538820] ahci 0000:00:11.0: version 3.0
[    1.538860] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.539017] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 6 ports 3 Gbps 0x5 impl SATA mode
[    1.539022] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck led clo pmp pio ccc 
[    1.539490] r8169 0000:04:00.0: eth0: RTL8102e at 0xffffc90000656000, 00:1e:33:d0:35:20, XID 14a00000 IRQ 43
[    1.559398] scsi0 : ahci
[    1.559627] scsi1 : ahci
[    1.559714] scsi2 : ahci
[    1.559799] scsi3 : ahci
[    1.559975] scsi4 : ahci
[    1.560155] scsi5 : ahci
[    1.560380] ata1: SATA max UDMA/133 abar m1024@0xf6408000 port 0xf6408100 irq 22
[    1.560383] ata2: DUMMY
[    1.560386] ata3: SATA max UDMA/133 abar m1024@0xf6408000 port 0xf6408200 irq 22
[    1.560389] ata4: DUMMY
[    1.560391] ata5: DUMMY
[    1.560392] ata6: DUMMY
[    1.560889] scsi6 : pata_atiixp
[    1.560979] scsi7 : pata_atiixp
[    1.561673] ata7: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x7000 irq 14
[    1.561676] ata8: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x7008 irq 15
[    1.860039] usb 3-3: new low speed USB device number 2 using ohci_hcd
[    2.052032] ata1: softreset failed (device not ready)
[    2.052038] ata1: applying SB600 PMP SRST workaround and retrying
[    2.052059] ata3: softreset failed (device not ready)
[    2.052062] ata3: applying SB600 PMP SRST workaround and retrying
[    2.224029] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.224060] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.225832] ata1.00: ATA-8: WDC WD3200BEVT-00A23T0, 01.01A01, max UDMA/133
[    2.225837] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.227065] ata1.00: configured for UDMA/133
[    2.227300] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200BEVT-0 01.0 PQ: 0 ANSI: 5
[    2.227528] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.227735] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    2.227868] sd 0:0:0:0: [sda] Write Protect is off
[    2.227872] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.227924] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.228113] ata3.00: ATAPI: HL-DT-ST DVDRAM GSA-T50N, RT04, max UDMA/133
[    2.232935] ata3.00: configured for UDMA/133
[    2.238415] scsi 2:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T50N  RT04 PQ: 0 ANSI: 5
[    2.243356] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.243360] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.243513] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    2.243596] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    2.300893]  sda: sda1 sda2 < sda5 sda6 >
[    2.301409] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.312480] input: Kingsis Peripherals Evoluent VerticalMouse 2 as /devices/pci0000:00/0000:00:12.0/usb3/3-3/3-3:1.0/input/input4
[    2.312630] generic-usb 0003:2222:3061.0001: input,hidraw0: USB HID v1.10 Mouse [Kingsis Peripherals Evoluent VerticalMouse 2] on usb-0000:00:12.0-3/input0
[    2.312658] usbcore: registered new interface driver usbhid
[    2.312660] usbhid: USB HID core driver
[    2.910375] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   12.276815] udevd[330]: starting version 173
[   12.343526] shpchp 0000:00:01.0: HPC vendor_id 1022 device_id 9602 ss_vid 1022 ss_did 9602
[   12.343534] shpchp 0000:00:01.0: Cannot reserve MMIO region
[   12.343650] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.349628] lp: driver loaded but no devices found
[   12.383093] Adding 3905532k swap on /dev/sda6.  Priority:-1 extents:1 across:3905532k 
[   12.399862] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   12.399870] Disabling lock debugging due to kernel taint
[   12.535012] cfg80211: Calling CRDA to update world regulatory domain
[   12.627703] type=1400 audit(1318871021.757:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=491 comm="apparmor_parser"
[   12.628293] type=1400 audit(1318871021.761:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=491 comm="apparmor_parser"
[   12.628624] type=1400 audit(1318871021.761:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=491 comm="apparmor_parser"
[   12.639654] ath5k 0000:05:00.0: BAR 0: set to [mem 0xf3100000-0xf310ffff 64bit] (PCI address [0xf3100000-0xf310ffff])
[   12.639665] ath5k 0000:05:00.0: enabling device (0000 -> 0002)
[   12.639675] ath5k 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   12.639689] ath5k 0000:05:00.0: setting latency timer to 64
[   12.639779] ath5k 0000:05:00.0: registered as 'phy0'
[   12.649972] [fglrx] Maximum main memory to use for locked dma buffers: 3550 MBytes.
[   12.650058] [fglrx]   vendor: 1002 device: 9613 count: 1
[   12.650637] [fglrx] ioport: bar 1, base 0x6000, size: 0x100
[   12.650657] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   12.650663] pci 0000:01:05.0: setting latency timer to 64
[   12.651187] [fglrx] Kernel PAT support is enabled
[   12.651225] [fglrx] module loaded - fglrx 8.88.7 [Jul 28 2011] with 1 minors
[   12.784802] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   12.785017] acpi device:03: registered as cooling_device3
[   12.785205] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input5
[   12.785368] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   12.799126] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
[   12.800395] SP5100 TCO timer: mmio address 0xfec000f0 already in use
[   12.836055] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   13.145636] ath: EEPROM regdomain: 0x65
[   13.145641] ath: EEPROM indicates we should expect a direct regpair map
[   13.145646] ath: Country alpha2 being used: 00
[   13.145648] ath: Regpair used: 0x65
[   13.150681] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   13.150688] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   13.150691] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   13.150694] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   13.150696] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   13.150699] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   13.150702] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   13.150705] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   13.150707] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   13.150710] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   13.150713] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   13.150715] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   13.150718] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   13.150721] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   13.150723] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   13.150726] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   13.150728] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   13.150731] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   13.150734] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   13.150737] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   13.150739] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   13.150742] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   13.150745] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   13.150748] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   13.150750] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   13.150753] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   13.150755] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   13.150830] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   13.185712] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   13.186725] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   13.214661] Linux video capture interface: v2.00
[   13.215640] uvcvideo: Found UVC 1.00 device CNF7051 (04f2:b070)
[   13.249093] input: CNF7051 as /devices/pci0000:00/0000:00:13.2/usb2/2-2/2-2:1.0/input/input6
[   13.251902] usbcore: registered new interface driver uvcvideo
[   13.251907] USB Video Class driver (v1.1.0)
[   13.362793] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   13.362799] cfg80211: World regulatory domain updated:
[   13.362801] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.362805] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.362808] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.362811] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.362871] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.362874] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.395246] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.395309] HDA Intel 0000:00:14.2: setting latency timer to 64
[   13.445882] hda_codec: ALC268: BIOS auto-probing.
[   13.467779] input: HDA ATI SB Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input7
[   13.467862] input: HDA ATI SB Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input8
[   13.507631] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   13.896485] Synaptics Touchpad, model: 1, fw: 7.0, id: 0x1a0b1, caps: 0xd04711/0xa04000/0x20000
[   13.896494] synaptics: Toshiba Satellite L350D detected, limiting rate to 40pps.
[   13.919830] vesafb: mode is 1152x864x32, linelength=4608, pages=0
[   13.919835] vesafb: scrolling: redraw
[   13.919839] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[   13.921804] vesafb: framebuffer at 0xe0000000, mapped to 0xffffc90002a00000, using 3904k, total 3904k
[   13.922066] Console: switching to colour frame buffer device 144x54
[   13.922096] fb0: VESA VGA frame buffer device
[   13.988947] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   14.095806] type=1400 audit(1318871023.225:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=862 comm="apparmor_parser"
[   14.098289] type=1400 audit(1318871023.229:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=861 comm="apparmor_parser"
[   14.099344] type=1400 audit(1318871023.229:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=862 comm="apparmor_parser"
[   14.099676] type=1400 audit(1318871023.229:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=862 comm="apparmor_parser"
[   14.108785] type=1400 audit(1318871023.241:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=867 comm="apparmor_parser"
[   14.109647] type=1400 audit(1318871023.241:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=867 comm="apparmor_parser"
[   14.129663] type=1400 audit(1318871023.261:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=870 comm="apparmor_parser"
[   14.173659] ppdev: user-space parallel port driver
[   14.355247] init: failsafe main process (806) killed by TERM signal
[   14.367024] init: apport pre-start process (930) terminated with status 1
[   14.388451] init: apport post-stop process (962) terminated with status 1
[   14.517257] r8169 0000:04:00.0: eth0: link down
[   14.517963] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.532356] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.685108] [fglrx] GART Table is not in FRAME_BUFFER range 
[   14.685414] [fglrx] Could not enable MSI; System prevented initialization
[   14.686129] [fglrx] Firegl kernel thread PID: 993
[   14.686197] [fglrx] Firegl kernel thread PID: 994
[   14.686263] [fglrx] Firegl kernel thread PID: 995
[   14.686708] [fglrx] IRQ 18 Enabled
[   14.740341] Bluetooth: Core ver 2.16
[   14.740392] NET: Registered protocol family 31
[   14.740395] Bluetooth: HCI device and connection manager initialized
[   14.740399] Bluetooth: HCI socket layer initialized
[   14.740401] Bluetooth: L2CAP socket layer initialized
[   14.743001] Bluetooth: SCO socket layer initialized
[   14.746794] Bluetooth: RFCOMM TTY layer initialized
[   14.746803] Bluetooth: RFCOMM socket layer initialized
[   14.746806] Bluetooth: RFCOMM ver 1.11
[   14.851017] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   14.851024] Bluetooth: BNEP filters: protocol multicast
[   15.222477] [fglrx] Gart USWC size:1160 M.
[   15.222482] [fglrx] Gart cacheable size:459 M.
[   15.222488] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   15.222491] [fglrx] Reserved FB block: Unshared offset:fffb000, size:5000 
[   15.651913] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   15.656381] EXT4-fs (sda5): re-mounted. Opts: commit=0
[   17.339928] wlan0: authenticate with 50:67:f0:c9:90:54 (try 1)
[   17.341440] wlan0: authenticated
[   17.341856] wlan0: associate with 50:67:f0:c9:90:54 (try 1)
[   17.344173] wlan0: RX AssocResp from 50:67:f0:c9:90:54 (capab=0x411 status=0 aid=1)
[   17.344177] wlan0: associated
[   17.345294] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   17.345424] cfg80211: Calling CRDA for country: AL
[   17.350315] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   17.350322] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.350325] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   17.350328] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.350331] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   17.350334] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.350337] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   17.350340] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.350342] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   17.350345] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.350347] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   17.350350] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.350353] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   17.350355] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.350358] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   17.350361] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.350363] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   17.350366] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.350368] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   17.350371] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.350374] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   17.350377] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.350379] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   17.350382] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.350384] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   17.350387] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   17.350389] cfg80211: Disabling freq 2484 MHz
[   17.350393] cfg80211: Regulatory domain changed to country: AL
[   17.350396] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   17.350399] cfg80211:     (2402000 KHz - 2482000 KHz @ 20000 KHz), (N/A, 2000 mBm)
[   20.374457] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   20.754020] EXT4-fs (sda5): re-mounted. Opts: commit=0
[   27.832023] wlan0: no IPv6 routers present
```What should I do next?

Thanks.

---

