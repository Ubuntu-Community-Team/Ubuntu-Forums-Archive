---
title: "hi tv card not work"
date: 2010-04-23
forum: Hardware
---

### Post by ghandon.2110 on 2010-04-23
hi
my tv card not work
lspci
```
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400 GS] (rev a1)
02:01.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)
```and dmesg
```
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
[    0.000000]   #4 [002f8eb000 - 0030033a36]          RAMDISK ==> [002f8eb000 - 0030033a36]
[    0.000000]   #5 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #6 [00008a9000 - 00008ac0f6]              BRK ==> [00008a9000 - 00008ac0f6]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00f4a90] f4a90
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003fff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003fff0
[    0.000000] On node 0 totalpages: 262027
[    0.000000] free_area_init_node: node 0, pgdat c0784900, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 272 pages used for memmap
[    0.000000]   HighMem zone: 34530 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:b0000000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c1805000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259979
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=061f99af-64e7-43fc-9151-50dac67a8965 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 5242560 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0003fff0)
[    0.000000] Memory: 1018044k/1048512k available (4565k kernel code, 29584k reserved, 2143k data, 540k init, 139208k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
[    0.000000]       .data : 0xc0575554 - 0xc078d308   (2143 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0575554   (4565 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 3349.678 MHz processor.
[    0.001617] Console: colour VGA+ 80x25
[    0.001622] console [tty0] enabled
[    0.001739] hpet clockevent registered
[    0.001744] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.001750] Calibrating delay loop (skipped), value calculated using timer frequency.. 6699.35 BogoMIPS (lpj=13398712)
[    0.001770] Security Framework initialized
[    0.001793] AppArmor: AppArmor initialized
[    0.001802] Mount-cache hash table entries: 512
[    0.001953] Initializing cgroup subsys ns
[    0.001959] Initializing cgroup subsys cpuacct
[    0.001964] Initializing cgroup subsys memory
[    0.001971] Initializing cgroup subsys freezer
[    0.001974] Initializing cgroup subsys net_cls
[    0.001995] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.001998] CPU: L2 cache: 512K
[    0.002001] CPU: Hyper-Threading is disabled
[    0.002005] mce: CPU supports 4 MCE banks
[    0.002018] CPU0: Thermal monitoring enabled (TM1)
[    0.002023] using mwait in idle threads.
[    0.002031] Performance Counters: no PMU driver, software counters only.
[    0.002038] Checking 'hlt' instruction... OK.
[    0.016955] SMP alternatives: switching to UP code
[    0.026759] ACPI: Core revision 20090521
[    0.036389] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.078557] CPU0: Intel(R) Celeron(R) D CPU 3.33GHz stepping 05
[    0.080001] Brought up 1 CPUs
[    0.080001] Total of 1 processors activated (6699.35 BogoMIPS).
[    0.080001] CPU0 attaching NULL sched-domain.
[    0.080001] Booting paravirtualized kernel on bare hardware
[    0.080001] regulator: core version 0.5
[    0.080001] Time: 12:57:03  Date: 04/23/10
[    0.080001] NET: Registered protocol family 16
[    0.080001] EISA bus registered
[    0.080001] ACPI: bus type pci registered
[    0.080001] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
[    0.080001] PCI: MCFG area at f0000000 reserved in E820
[    0.080001] PCI: Using MMCONFIG for extended config space
[    0.080001] PCI: Using configuration type 1 for base access
[    0.080001] bio: create slab <bio-0> at 0
[    0.080001] ACPI: EC: Look up EC in DSDT
[    0.084118] ACPI: Interpreter enabled
[    0.084130] ACPI: (supports S0 S1 S4 S5)
[    0.084157] ACPI: Using IOAPIC for interrupt routing
[    0.088893] ACPI: No dock devices found.
[    0.089004] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.089136] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.089140] pci 0000:00:01.0: PME# disabled
[    0.089215] pci 0000:00:1b.0: reg 10 64bit mmio: [0xe6000000-0xe6003fff]
[    0.089265] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.089269] pci 0000:00:1b.0: PME# disabled
[    0.089320] pci 0000:00:1d.0: reg 20 io port: [0xbc00-0xbc1f]
[    0.089377] pci 0000:00:1d.1: reg 20 io port: [0xb000-0xb01f]
[    0.089433] pci 0000:00:1d.2: reg 20 io port: [0xb400-0xb41f]
[    0.089488] pci 0000:00:1d.3: reg 20 io port: [0xb800-0xb81f]
[    0.089542] pci 0000:00:1d.7: reg 10 32bit mmio: [0xe6004000-0xe60043ff]
[    0.089724] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[    0.089729] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.089733] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0800 (mask 000f)
[    0.089737] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0290 (mask 000f)
[    0.089795] pci 0000:00:1f.2: reg 10 io port: [0x00-0x07]
[    0.089802] pci 0000:00:1f.2: reg 14 io port: [0x00-0x03]
[    0.089809] pci 0000:00:1f.2: reg 18 io port: [0x00-0x07]
[    0.089816] pci 0000:00:1f.2: reg 1c io port: [0x00-0x03]
[    0.089822] pci 0000:00:1f.2: reg 20 io port: [0xf000-0xf00f]
[    0.089850] pci 0000:00:1f.2: PME# supported from D3hot
[    0.089855] pci 0000:00:1f.2: PME# disabled
[    0.089905] pci 0000:00:1f.3: reg 20 io port: [0x500-0x51f]
[    0.089969] pci 0000:01:00.0: reg 10 32bit mmio: [0xe2000000-0xe2ffffff]
[    0.089980] pci 0000:01:00.0: reg 14 64bit mmio: [0xd0000000-0xdfffffff]
[    0.089991] pci 0000:01:00.0: reg 1c 64bit mmio: [0xe0000000-0xe1ffffff]
[    0.089998] pci 0000:01:00.0: reg 24 io port: [0x9000-0x907f]
[    0.090004] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.090077] pci 0000:00:01.0: bridge io port: [0x9000-0x9fff]
[    0.090081] pci 0000:00:01.0: bridge 32bit mmio: [0xe0000000-0xe3ffffff]
[    0.090086] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.090131] pci 0000:02:01.0: reg 10 32bit mmio: [0xe5001000-0xe50013ff]
[    0.090185] pci 0000:02:01.0: supports D1 D2
[    0.090227] pci 0000:02:05.0: reg 10 io port: [0xa000-0xa0ff]
[    0.090235] pci 0000:02:05.0: reg 14 32bit mmio: [0xe5000000-0xe50000ff]
[    0.090264] pci 0000:02:05.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.090285] pci 0000:02:05.0: supports D1 D2
[    0.090287] pci 0000:02:05.0: PME# supported from D1 D2 D3hot D3cold
[    0.090292] pci 0000:02:05.0: PME# disabled
[    0.090335] pci 0000:00:1e.0: transparent bridge
[    0.090340] pci 0000:00:1e.0: bridge io port: [0xa000-0xafff]
[    0.090344] pci 0000:00:1e.0: bridge 32bit mmio: [0xe4000000-0xe5ffffff]
[    0.090360] pci_bus 0000:00: on NUMA node 0
[    0.090365] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.090551] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.098460] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.098575] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.098689] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 *6 7 9 10 11 12 14 15)
[    0.098799] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.098910] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.099022] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.099133] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.099245] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.099468] SCSI subsystem initialized
[    0.099547] libata version 3.00 loaded.
[    0.099637] usbcore: registered new interface driver usbfs
[    0.099657] usbcore: registered new interface driver hub
[    0.099684] usbcore: registered new device driver usb
[    0.099835] ACPI: WMI: Mapper loaded
[    0.099837] PCI: Using ACPI for IRQ routing
[    0.100007] Bluetooth: Core ver 2.15
[    0.100046] NET: Registered protocol family 31
[    0.100049] Bluetooth: HCI device and connection manager initialized
[    0.100052] Bluetooth: HCI socket layer initialized
[    0.100054] NetLabel: Initializing
[    0.100056] NetLabel:  domain hash size = 128
[    0.100058] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.100075] NetLabel:  unlabeled traffic allowed by default
[    0.100109] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.100116] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.105595] pnp: PnP ACPI init
[    0.105622] ACPI: bus type pnp registered
[    0.108887] pnp: PnP ACPI: found 15 devices
[    0.108891] ACPI: ACPI bus type pnp unregistered
[    0.108897] PnPBIOS: Disabled by ACPI PNP
[    0.108910] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.108913] system 00:01: ioport range 0x290-0x29f has been reserved
[    0.108916] system 00:01: ioport range 0x800-0x87f has been reserved
[    0.108920] system 00:01: ioport range 0x290-0x294 has been reserved
[    0.108923] system 00:01: ioport range 0x880-0x88f has been reserved
[    0.108932] system 00:0b: ioport range 0x400-0x4bf could not be reserved
[    0.108939] system 00:0c: iomem range 0xf0000000-0xf3ffffff has been reserved
[    0.108947] system 00:0d: iomem range 0xcce00-0xcffff has been reserved
[    0.108951] system 00:0d: iomem range 0xf0000-0xf7fff could not be reserved
[    0.108954] system 00:0d: iomem range 0xf8000-0xfbfff could not be reserved
[    0.108957] system 00:0d: iomem range 0xfc000-0xfffff could not be reserved
[    0.108960] system 00:0d: iomem range 0x3fff0000-0x3fffffff could not be reserved
[    0.108963] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[    0.108966] system 00:0d: iomem range 0x100000-0x3ffeffff could not be reserved
[    0.108970] system 00:0d: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.108973] system 00:0d: iomem range 0xfed13000-0xfed1dfff has been reserved
[    0.108976] system 00:0d: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.108979] system 00:0d: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.108982] system 00:0d: iomem range 0xffb00000-0xffb7ffff has been reserved
[    0.108985] system 00:0d: iomem range 0xfff00000-0xffffffff has been reserved
[    0.108988] system 00:0d: iomem range 0xe0000-0xeffff has been reserved
[    0.143661] AppArmor: AppArmor Filesystem Enabled
[    0.143695] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.143699] pci 0000:00:01.0:   IO window: 0x9000-0x9fff
[    0.143704] pci 0000:00:01.0:   MEM window: 0xe0000000-0xe3ffffff
[    0.143708] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.143714] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.143718] pci 0000:00:1e.0:   IO window: 0xa000-0xafff
[    0.143723] pci 0000:00:1e.0:   MEM window: 0xe4000000-0xe5ffffff
[    0.143728] pci 0000:00:1e.0:   PREFETCH window: 0x40000000-0x400fffff
[    0.143741]   alloc irq_desc for 16 on node -1
[    0.143743]   alloc kstat_irqs on node -1
[    0.143750] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.143755] pci 0000:00:01.0: setting latency timer to 64
[    0.143762] pci 0000:00:1e.0: setting latency timer to 64
[    0.143768] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.143771] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.143774] pci_bus 0000:01: resource 0 io:  [0x9000-0x9fff]
[    0.143776] pci_bus 0000:01: resource 1 mem: [0xe0000000-0xe3ffffff]
[    0.143779] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.143782] pci_bus 0000:02: resource 0 io:  [0xa000-0xafff]
[    0.143785] pci_bus 0000:02: resource 1 mem: [0xe4000000-0xe5ffffff]
[    0.143787] pci_bus 0000:02: resource 2 pref mem [0x40000000-0x400fffff]
[    0.143790] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.143792] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.143836] NET: Registered protocol family 2
[    0.143944] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.144324] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.144959] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.145330] TCP: Hash tables configured (established 131072 bind 65536)
[    0.145335] TCP reno registered
[    0.145470] NET: Registered protocol family 1
[    0.145551] Trying to unpack rootfs image as initramfs...
[    0.355942] Freeing initrd memory: 7458k freed
[    0.361576] cpufreq-nforce2: No nForce2 chipset.
[    0.361610] Scanning for low memory corruption every 60 seconds
[    0.361725] audit: initializing netlink socket (disabled)
[    0.361745] type=2000 audit(1272027422.359:1): initialized
[    0.369629] highmem bounce pool size: 64 pages
[    0.369637] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.371017] VFS: Disk quotas dquot_6.5.2
[    0.371078] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.371683] fuse init (API version 7.12)
[    0.371775] msgmni has been set to 1731
[    0.372025] alg: No test for stdrng (krng)
[    0.372042] io scheduler noop registered
[    0.372045] io scheduler anticipatory registered
[    0.372047] io scheduler deadline registered
[    0.372104] io scheduler cfq registered (default)
[    0.372212] pci 0000:01:00.0: Boot video device
[    0.372328]   alloc irq_desc for 24 on node -1
[    0.372331]   alloc kstat_irqs on node -1
[    0.372342] pcieport-driver 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.372350] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    0.372439] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.372470] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.372612] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.372617] ACPI: Power Button [PWRF]
[    0.372673] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.372676] ACPI: Power Button [PWRB]
[    0.372977] processor LNXCPU:00: registered as cooling_device0
[    0.372982] ACPI: Processor [CPU0] (supports 2 throttling states)
[    0.374840] isapnp: Scanning for PnP cards...
[    0.503964] Switched to high resolution mode on CPU 0
[    0.728091] isapnp: No Plug & Play device found
[    0.729316] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.729428] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.729529] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.729838] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.729974] 00:07: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.731083] brd: module loaded
[    0.731541] loop: module loaded
[    0.731636] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.731753] ata_piix 0000:00:1f.2: version 2.13
[    0.731777]   alloc irq_desc for 19 on node -1
[    0.731780]   alloc kstat_irqs on node -1
[    0.731788] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.731794] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    0.731843] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.731948] scsi0 : ata_piix
[    0.732077] scsi1 : ata_piix
[    0.732954] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    0.732958] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    0.733810] Fixed MDIO Bus: probed
[    0.733852] PPP generic driver version 2.4.2
[    0.733969] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.733995]   alloc irq_desc for 23 on node -1
[    0.733998]   alloc kstat_irqs on node -1
[    0.734005] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.734023] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.734028] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.734097] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.737998] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    0.738388] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xe6004000
[    0.752008] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.752122] usb usb1: configuration #1 chosen from 1 choice
[    0.752157] hub 1-0:1.0: USB hub found
[    0.752168] hub 1-0:1.0: 8 ports detected
[    0.752248] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.752275] uhci_hcd: USB Universal Host Controller Interface driver
[    0.752321] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.752331] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.752335] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.752382] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.752409] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000bc00
[    0.752493] usb usb2: configuration #1 chosen from 1 choice
[    0.752525] hub 2-0:1.0: USB hub found
[    0.752538] hub 2-0:1.0: 2 ports detected
[    0.752588] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.752596] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.752600] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.752634] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.752669] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000b000
[    0.752748] usb usb3: configuration #1 chosen from 1 choice
[    0.752777] hub 3-0:1.0: USB hub found
[    0.752786] hub 3-0:1.0: 2 ports detected
[    0.752837]   alloc irq_desc for 18 on node -1
[    0.752840]   alloc kstat_irqs on node -1
[    0.752846] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.752853] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.752856] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.752891] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.752924] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000b400
[    0.753010] usb usb4: configuration #1 chosen from 1 choice
[    0.753040] hub 4-0:1.0: USB hub found
[    0.753047] hub 4-0:1.0: 2 ports detected
[    0.753100] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.753107] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.753110] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.753143] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.753176] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000b800
[    0.753257] usb usb5: configuration #1 chosen from 1 choice
[    0.753287] hub 5-0:1.0: USB hub found
[    0.753295] hub 5-0:1.0: 2 ports detected
[    0.753410] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.753766] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.753774] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.753846] mice: PS/2 mouse device common for all mice
[    0.753958] rtc_cmos 00:03: RTC can wake from S4
[    0.753997] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.754024] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.754147] device-mapper: uevent: version 1.0.3
[    0.754256] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.754340] device-mapper: multipath: version 1.1.0 loaded
[    0.754344] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.754482] EISA: Probing bus 0 at eisa.0
[    0.754510] EISA: Detected 0 cards.
[    0.754560] cpuidle: using governor ladder
[    0.754564] cpuidle: using governor menu
[    0.755142] TCP cubic registered
[    0.755276] NET: Registered protocol family 10
[    0.755744] lo: Disabled Privacy Extensions
[    0.756108] NET: Registered protocol family 17
[    0.756134] Bluetooth: L2CAP ver 2.13
[    0.756136] Bluetooth: L2CAP socket layer initialized
[    0.756139] Bluetooth: SCO (Voice Link) ver 0.6
[    0.756141] Bluetooth: SCO socket layer initialized
[    0.756185] Bluetooth: RFCOMM TTY layer initialized
[    0.756188] Bluetooth: RFCOMM socket layer initialized
[    0.756190] Bluetooth: RFCOMM ver 1.11
[    0.756229] Using IPI No-Shortcut mode
[    0.756314] PM: Resume from disk failed.
[    0.756332] registered taskstats version 1
[    0.756421]   Magic number: 6:430:987
[    0.756493] rtc_cmos 00:03: setting system clock to 2010-04-23 12:57:03 UTC (1272027423)
[    0.756496] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.756498] EDD information not available.
[    0.771672] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.908208] ata1.00: HPA unlocked: 976771055 -> 976773168, native 976773168
[    0.908214] ata1.00: ATA-8: WDC WD5000AADS-00M2B0, 01.00A01, max UDMA/133
[    0.908217] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.924761] ata1.00: configured for UDMA/133
[    0.924887] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000AADS-0 01.0 PQ: 0 ANSI: 5
[    0.925031] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.925078] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    0.925136] sd 0:0:0:0: [sda] Write Protect is off
[    0.925139] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.925168] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.925318]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 sda10 >
[    1.012693] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.084317] ata2.01: ATAPI: HP Combo 535d, RPK2, max UDMA/33
[    1.116218] ata2.01: configured for UDMA/33
[    1.118080] scsi 1:0:1:0: CD-ROM            HP       Combo 535d       RPK2 PQ: 0 ANSI: 5
[    1.123941] sr0: scsi3-mmc drive: 0x/52x writer cd/rw xa/form2 cdda tray
[    1.123946] Uniform CD-ROM driver Revision: 3.20
[    1.124055] sr 1:0:1:0: Attached scsi CD-ROM sr0
[    1.124119] sr 1:0:1:0: Attached scsi generic sg1 type 5
[    1.124150] Freeing unused kernel memory: 540k freed
[    1.124566] Write protecting the kernel text: 4568k
[    1.124594] Write protecting the kernel read-only data: 1836k
[    1.320708] Linux agpgart interface v0.103
[    1.335549] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.335572]   alloc irq_desc for 21 on node -1
[    1.335575]   alloc kstat_irqs on node -1
[    1.335584] r8169 0000:02:05.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.335612] r8169 0000:02:05.0: no PCI Express capability
[    1.373382] eth0: RTL8169sc/8110sc at 0xf8096000, 00:1a:4d:8d:e1:d8, XID 18000000 IRQ 21
[    1.397515] usb 4-2: new full speed USB device using uhci_hcd and address 2
[    1.579195] usb 4-2: configuration #1 chosen from 1 choice
[    2.982733] PM: Starting manual resume from disk
[    2.982739] PM: Resume from partition 8:10
[    2.982741] PM: Checking hibernation image.
[    2.982968] PM: Resume from disk failed.
[    2.986338] EXT4-fs (sda9): INFO: recovery required on readonly filesystem
[    2.986344] EXT4-fs (sda9): write access will be enabled during recovery
[    2.996479] EXT4-fs (sda9): barriers enabled
[    5.127445] kjournald2 starting: pid 361, dev sda9:8, commit interval 5 seconds
[    5.127470] EXT4-fs (sda9): delayed allocation enabled
[    5.127474] EXT4-fs: file extents enabled
[    5.128064] EXT4-fs: mballoc enabled
[    5.128082] EXT4-fs (sda9): orphan cleanup on readonly fs
[    5.128092] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 12993
[    5.128234] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 12995
[    5.128252] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 12990
[    5.128269] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 12991
[    5.128285] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 12997
[    5.128303] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 85674
[    5.128359] EXT4-fs (sda9): ext4_orphan_cleanup: deleting unreferenced inode 131444
[    5.128368] EXT4-fs (sda9): 7 orphan inodes deleted
[    5.128372] EXT4-fs (sda9): recovery complete
[    5.397705] EXT4-fs (sda9): mounted filesystem with ordered data mode
[    5.783268] type=1505 audit(1272027428.523:2): operation="profile_load" pid=384 name=/usr/share/gdm/guest-session/Xsession
[    5.786140] type=1505 audit(1272027428.527:3): operation="profile_load" pid=385 name=/sbin/dhclient3
[    5.786812] type=1505 audit(1272027428.527:4): operation="profile_load" pid=385 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    5.787175] type=1505 audit(1272027428.527:5): operation="profile_load" pid=385 name=/usr/lib/connman/scripts/dhclient-script
[    5.812058] type=1505 audit(1272027428.555:6): operation="profile_load" pid=386 name=/usr/bin/evince
[    5.823123] type=1505 audit(1272027428.563:7): operation="profile_load" pid=386 name=/usr/bin/evince-previewer
[    5.829634] type=1505 audit(1272027428.571:8): operation="profile_load" pid=386 name=/usr/bin/evince-thumbnailer
[    5.850827] type=1505 audit(1272027428.591:9): operation="profile_load" pid=388 name=/usr/lib/cups/backend/cups-pdf
[    5.851609] type=1505 audit(1272027428.591:10): operation="profile_load" pid=388 name=/usr/sbin/cupsd
[    5.854684] type=1505 audit(1272027428.595:11): operation="profile_load" pid=389 name=/usr/sbin/tcpdump
[    6.602825] Adding 441748k swap on /dev/sda10.  Priority:-1 extents:1 across:441748k 
[    6.970196] udev: starting version 147
[    7.396402] EXT4-fs (sda9): internal journal on sda9:8
[    7.830050] Bluetooth: Generic Bluetooth USB driver ver 0.5
[    7.830170] usbcore: registered new interface driver btusb
[    7.944399] psmouse serio1: ID: 10 00 64
[    8.124851] Linux video capture interface: v2.00
[    8.210991] lp: driver loaded but no devices found
[    8.473062] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input4
[    8.586327] nvidia: module license 'NVIDIA' taints kernel.
[    8.586332] Disabling lock debugging due to kernel taint
[    8.847826] parport_pc 00:08: reported by Plug and Play ACPI
[    8.847876] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    8.849934] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.849946] nvidia 0000:01:00.0: setting latency timer to 64
[    8.850204] NVRM: loading NVIDIA UNIX x86 Kernel Module  185.18.36  Fri Aug 14 17:18:04 PDT 2009
[    8.944185] lp0: using parport0 (interrupt-driven).
[    9.280776] saa7134: `3;tuner=2' invalid for parameter `card'
[    9.295062] saa7134: `3;tuner=2' invalid for parameter `card'
[    9.300463] ppdev: user-space parallel port driver
[    9.307035] intel_rng: FWH not detected
[    9.340585] ip_tables: (C) 2000-2006 Netfilter Core Team
[    9.511188] nf_conntrack version 0.5.0 (16383 buckets, 65532 max)
[    9.511463] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[    9.511466] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[    9.511468] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   10.081042] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.081077] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   10.207476] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   10.217808] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input5
[   12.898936] r8169: eth0: link up
[   13.595216] NET: Registered protocol family 24
[   14.222306] type=1505 audit(1272011236.963:12): operation="profile_replace" pid=1243 name=/usr/share/gdm/guest-session/Xsession
[   14.224633] type=1505 audit(1272011236.967:13): operation="profile_replace" pid=1244 name=/sbin/dhclient3
[   14.225306] type=1505 audit(1272011236.967:14): operation="profile_replace" pid=1244 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   14.225671] type=1505 audit(1272011236.967:15): operation="profile_replace" pid=1244 name=/usr/lib/connman/scripts/dhclient-script
[   14.230556] type=1505 audit(1272011236.971:16): operation="profile_replace" pid=1245 name=/usr/bin/evince
[   14.244242] type=1505 audit(1272011236.987:17): operation="profile_replace" pid=1245 name=/usr/bin/evince-previewer
[   14.250722] type=1505 audit(1272011236.991:18): operation="profile_replace" pid=1245 name=/usr/bin/evince-thumbnailer
[   14.261207] type=1505 audit(1272011237.003:19): operation="profile_replace" pid=1247 name=/usr/lib/cups/backend/cups-pdf
[   14.262053] type=1505 audit(1272011237.003:20): operation="profile_replace" pid=1247 name=/usr/sbin/cupsd
[   14.265302] type=1505 audit(1272011237.007:21): operation="profile_replace" pid=1248 name=/usr/sbin/tcpdump
[   20.981107] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.981111] Bluetooth: BNEP filters: protocol multicast
[   21.008906] Bridge firewalling registered
[   23.212006] eth0: no IPv6 routers present
[ 1068.863127] saa7134: `3;tuner=2' invalid for parameter `card'
[ 2171.362886] Linux video capture interface: v2.00
[ 2171.399719] saa7134: `3;tuner=2' invalid for parameter `card'
[ 4244.477238] Linux video capture interface: v2.00
[ 4244.518271] saa7134: `3;tuner=2' invalid for parameter `card'
[ 4290.256806] saa7134: `3;tuner=2' invalid for parameter `card'
[ 4531.478616] saa7134: `3;tuner=2' invalid for parameter `card'
```

please help me
tanks

---

