---
title: "Black screen when booting. Hardware problem?"
date: 2009-05-25
forum: Hardware
---

### Post by Loopk1n on 2009-05-25
So, I have this Fujitsu-Siemens Amilo L 6825 laptop. Most of the time when booting I end up with black screen instead of login screen/desktop, everything works but after the loading bar screen just seems to shut down. This behavior makes the laptop unusable although everything seems to work just fine the rare times I get past the loading screen. This happens with 8.10 and 9.04, and with plain Debian too. I know that people have lot of trouble with the same integrated video card that I have.

lspci grep | VGA
```
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
```

Below is my dmesg output if someone cares to look, I can make out these lines from the bottom but have no idea what they're about:
```

[   29.806731] [drm:i915_setparam] *ERROR* unknown parameter 4
[   29.806818] [drm:i915_getparam] *ERROR* Unknown parameter 6

[   30.996631] [drm:i915_getparam] *ERROR* Unknown parameter 6
```dmesg output:
```

[    0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 (Ubuntu 2.6.28-11.42-generic)
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
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001f7d0000 (usable)
[    0.000000]  BIOS-e820: 000000001f7d0000 - 000000001f7df000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001f7df000 - 000000001f800000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x1f7d0 max_arch_pfn = 0x100000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000001f7d0000 (usable)
[    0.000000]  modified: 000000001f7d0000 - 000000001f7df000 (ACPI data)
[    0.000000]  modified: 000000001f7df000 - 000000001f800000 (ACPI NVS)
[    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 1f7d0000 @ 10000-16000
[    0.000000] RAMDISK: 1f08d000 - 1f7bfcbd
[    0.000000] ACPI: RSDP 000F5540, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 1F7D0000, 0030 (r1 A M I  OEMRSDT   6000418 MSFT       97)
[    0.000000] ACPI: FACP 1F7D0200, 0081 (r2 A M I  OEMFACP   6000418 MSFT       97)
[    0.000000] ACPI: DSDT 1F7D03F0, 38D2 (r1 UW____ 755II5__       16 INTL  2002026)
[    0.000000] ACPI: FACS 1F7DF000, 0040
[    0.000000] ACPI: APIC 1F7D0390, 005C (r1 A M I  OEMAPIC   6000418 MSFT       97)
[    0.000000] ACPI: OEMB 1F7DF040, 0108 (r1 A M I  AMI_OEM   6000418 MSFT       97)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 503MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 1f7d0000
[    0.000000]   low ram: 00000000 - 1f7d0000
[    0.000000]   bootmap 00012000 - 00015efc
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 001f7d0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 000087c52c]    TEXT DATA BSS ==> [0000100000 - 000087c52c]
[    0.000000]   #4 [001f08d000 - 001f7bfcbd]          RAMDISK ==> [001f08d000 - 001f7bfcbd]
[    0.000000]   #5 [000087d000 - 0000881000]    INIT_PG_TABLE ==> [000087d000 - 0000881000]
[    0.000000]   #6 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #7 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #8 [0000012000 - 0000016000]          BOOTMAP ==> [0000012000 - 0000016000]
[    0.000000] found SMP MP-table at [c00ff780] 000ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0001f7d0
[    0.000000]   HighMem  0x0001f7d0 -> 0x0001f7d0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0001f7d0
[    0.000000] On node 0 totalpages: 128863
[    0.000000] free_area_init_node: node 0, pgdat c06d0f80, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 976 pages used for memmap
[    0.000000]   Normal zone: 123904 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1f800000:e0780000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 127855
[    0.000000] Kernel command line: root=UUID=68532498-3525-48a2-8c24-58c960e727f8 ro vga=792 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] TSC: PIT calibration matches PMTIMER. 1 loops
[    0.000000] Detected 2800.103 MHz processor.
[    0.004000] Console: colour dummy device 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.004000] allocated 2579200 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 493084k/515904k available (4126k kernel code, 22136k reserved, 2208k data, 532k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xdffd0000 - 0xff3fe000   ( 500 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xdf7d0000   ( 503 MB)
[    0.004000]       .init : 0xc0737000 - 0xc07bc000   ( 532 kB)
[    0.004000]       .data : 0xc0507a6f - 0xc072fe60   (2208 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0507a6f   (4126 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=128, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004016] Calibrating delay loop (skipped), value calculated using timer frequency.. 5600.20 BogoMIPS (lpj=11200412)
[    0.004064] Security Framework initialized
[    0.004080] SELinux:  Disabled at boot.
[    0.004115] AppArmor: AppArmor initialized
[    0.004140] Mount-cache hash table entries: 512
[    0.004422] Initializing cgroup subsys ns
[    0.004448] Initializing cgroup subsys cpuacct
[    0.004457] Initializing cgroup subsys memory
[    0.004472] Initializing cgroup subsys freezer
[    0.004508] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    0.004520] CPU: L2 cache: 128K
[    0.004528] CPU: Hyper-Threading is disabled
[    0.004562] Checking 'hlt' instruction... OK.
[    0.020863] SMP alternatives: switching to UP code
[    0.192045] ACPI: Core revision 20080926
[    0.196482] ACPI: Checking initramfs for custom DSDT
[    0.504854] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.546597] CPU0: Intel(R) Celeron(R) CPU 2.80GHz stepping 09
[    0.548002] Brought up 1 CPUs
[    0.548002] Total of 1 processors activated (5600.20 BogoMIPS).
[    0.548002] CPU0 attaching NULL sched-domain.
[    0.548002] net_namespace: 776 bytes
[    0.548002] Booting paravirtualized kernel on bare hardware
[    0.548002] Time: 18:08:03  Date: 05/25/09
[    0.548002] regulator: core version 0.5
[    0.548002] NET: Registered protocol family 16
[    0.548002] EISA bus registered
[    0.548002] ACPI: bus type pci registered
[    0.548373] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[    0.548385] PCI: Using configuration type 1 for base access
[    0.551634] ACPI: EC: Look up EC in DSDT
[    0.560064] ACPI: Interpreter enabled
[    0.560083] ACPI: (supports S0 S3 S4 S5)
[    0.560114] ACPI: Using IOAPIC for interrupt routing
[    0.570960] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.572368] ACPI: EC: GPE storm detected, transactions will use polling mode
[    0.577895] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    0.577909] ACPI: EC: driver started in poll mode
[    0.578064] ACPI: No dock devices found.
[    0.578105] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.578210] pci 0000:00:00.0: reg 10 32bit mmio: [0xc0000000-0xcfffffff]
[    0.578286] pci 0000:00:02.0: reg 10 32bit mmio: [0xd0000000-0xd7ffffff]
[    0.578294] pci 0000:00:02.0: reg 14 32bit mmio: [0xdff80000-0xdfffffff]
[    0.578403] pci 0000:00:1d.0: reg 20 io port: [0xdf20-0xdf3f]
[    0.578457] pci 0000:00:1d.1: reg 20 io port: [0xdf40-0xdf5f]
[    0.578521] pci 0000:00:1d.2: reg 20 io port: [0xdf80-0xdf9f]
[    0.578585] pci 0000:00:1d.7: reg 10 32bit mmio: [0xdff7bc00-0xdff7bfff]
[    0.578632] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.578644] pci 0000:00:1d.7: PME# disabled
[    0.578696] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[    0.578698] * this clock source is slow. If you are sure your timer does not have
[    0.578699] * this bug, please use "acpi_pm_good" to disable the workaround
[    0.578750] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.578761] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[    0.578768] pci 0000:00:1f.0: quirk: region 0500-053f claimed by ICH4 GPIO
[    0.578793] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.578802] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.578809] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.578816] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.578824] pci 0000:00:1f.1: reg 20 io port: [0xffa0-0xffaf]
[    0.578831] pci 0000:00:1f.1: reg 24 32bit mmio: [0x000000-0x0003ff]
[    0.578884] pci 0000:00:1f.3: reg 20 io port: [0x540-0x55f]
[    0.578929] pci 0000:00:1f.5: reg 10 io port: [0xe000-0xe0ff]
[    0.578935] pci 0000:00:1f.5: reg 14 io port: [0xe100-0xe13f]
[    0.578942] pci 0000:00:1f.5: reg 18 32bit mmio: [0x000000-0x0001ff]
[    0.578949] pci 0000:00:1f.5: reg 1c 32bit mmio: [0x000000-0x0000ff]
[    0.578973] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.578982] pci 0000:00:1f.5: PME# disabled
[    0.579016] pci 0000:00:1f.6: reg 10 io port: [0xe200-0xe2ff]
[    0.579022] pci 0000:00:1f.6: reg 14 io port: [0xe300-0xe37f]
[    0.579055] pci 0000:00:1f.6: PME# supported from D0 D3hot D3cold
[    0.579062] pci 0000:00:1f.6: PME# disabled
[    0.579114] pci 0000:01:03.0: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.579125] pci 0000:01:03.0: supports D1 D2
[    0.579127] pci 0000:01:03.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.579135] pci 0000:01:03.0: PME# disabled
[    0.579179] pci 0000:01:0a.0: reg 10 32bit mmio: [0xdfdff800-0xdfdfffff]
[    0.579187] pci 0000:01:0a.0: reg 14 io port: [0xcc00-0xcc7f]
[    0.579221] pci 0000:01:0a.0: supports D2
[    0.579223] pci 0000:01:0a.0: PME# supported from D2 D3hot D3cold
[    0.579230] pci 0000:01:0a.0: PME# disabled
[    0.579267] pci 0000:01:0c.0: reg 10 io port: [0xc800-0xc8ff]
[    0.579274] pci 0000:01:0c.0: reg 14 32bit mmio: [0xdfdfe000-0xdfdfefff]
[    0.579300] pci 0000:01:0c.0: reg 30 32bit mmio: [0xdfde0000-0xdfdeffff]
[    0.579310] pci 0000:01:0c.0: supports D1 D2
[    0.579312] pci 0000:01:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.579319] pci 0000:01:0c.0: PME# disabled
[    0.579351] pci 0000:00:1e.0: transparent bridge
[    0.579358] pci 0000:00:1e.0: bridge io port: [0xc000-0xcfff]
[    0.579363] pci 0000:00:1e.0: bridge 32bit mmio: [0xdfd00000-0xdfdfffff]
[    0.579393] bus 00 -> node 0
[    0.579414] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.579636] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    0.635810] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.636115] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[    0.636380] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.636639] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.636891] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.637142] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.637392] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.637646] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.637882] ACPI: Power Resource [URP1] (off)
[    0.637972] ACPI: Power Resource [URP2] (off)
[    0.638059] ACPI: Power Resource [FDDP] (off)
[    0.638157] ACPI: Power Resource [LPTP] (off)
[    0.638340] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - B0, should be AB [20080926]
[    0.638408] ACPI: WMI: Mapper loaded
[    0.638857] SCSI subsystem initialized
[    0.639020] libata version 3.00 loaded.
[    0.639176] usbcore: registered new interface driver usbfs
[    0.639233] usbcore: registered new interface driver hub
[    0.639354] usbcore: registered new device driver usb
[    0.639757] PCI: Using ACPI for IRQ routing
[    0.639943] Bluetooth: Core ver 2.13
[    0.640193] NET: Registered protocol family 31
[    0.640204] Bluetooth: HCI device and connection manager initialized
[    0.640211] Bluetooth: HCI socket layer initialized
[    0.640216] NET: Registered protocol family 8
[    0.640220] NET: Registered protocol family 20
[    0.640256] NetLabel: Initializing
[    0.640262] NetLabel:  domain hash size = 128
[    0.640265] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.640305] NetLabel:  unlabeled traffic allowed by default
[    0.640475] AppArmor: AppArmor Filesystem Enabled
[    0.640532] pnp: PnP ACPI init
[    0.640532] ACPI: bus type pnp registered
[    0.648785] pnp: PnP ACPI: found 10 devices
[    0.648801] ACPI: ACPI bus type pnp unregistered
[    0.648810] PnPBIOS: Disabled by ACPI PNP
[    0.648844] system 00:05: ioport range 0x4d0-0x4d1 has been reserved
[    0.648852] system 00:05: ioport range 0x400-0x47f has been reserved
[    0.648857] system 00:05: ioport range 0x500-0x53f has been reserved
[    0.648864] system 00:05: iomem range 0xffe80000-0xffefffff has been reserved
[    0.648870] system 00:05: iomem range 0xfff80000-0xffffffff has been reserved
[    0.648875] system 00:05: iomem range 0xfee00400-0xffbfffff has been reserved
[    0.648891] system 00:06: ioport range 0x1100-0x113f has been reserved
[    0.648897] system 00:06: ioport range 0x1254-0x1254 has been reserved
[    0.648901] system 00:06: ioport range 0x12d4-0x12d4 has been reserved
[    0.648906] system 00:06: ioport range 0x1300-0x1375 has been reserved
[    0.648911] system 00:06: ioport range 0x1377-0x137f has been reserved
[    0.648926] system 00:09: iomem range 0x0-0x9ffff could not be reserved
[    0.648933] system 00:09: iomem range 0xe0000-0xfffff could not be reserved
[    0.648938] system 00:09: iomem range 0x100000-0x1f7fffff could not be reserved
[    0.683949] pci 0000:01:03.0: CardBus bridge, secondary bus 0000:02
[    0.683962] pci 0000:01:03.0:   IO window: 0x00c000-0x00c0ff
[    0.683969] pci 0000:01:03.0:   IO window: 0x00c400-0x00c4ff
[    0.683976] pci 0000:01:03.0:   PREFETCH window: 0x20000000-0x23ffffff
[    0.683983] pci 0000:01:03.0:   MEM window: 0x28000000-0x2bffffff
[    0.684007] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
[    0.684014] pci 0000:00:1e.0:   IO window: 0xc000-0xcfff
[    0.684022] pci 0000:00:1e.0:   MEM window: 0xdfd00000-0xdfdfffff
[    0.684029] pci 0000:00:1e.0:   PREFETCH window: 0x00000020000000-0x00000025ffffff
[    0.684055] pci 0000:00:1e.0: setting latency timer to 64
[    0.684079] pci 0000:01:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.684090] pci 0000:01:03.0: setting latency timer to 64
[    0.684096] bus: 00 index 0 io port: [0x00-0xffff]
[    0.684100] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.684104] bus: 01 index 0 io port: [0xc000-0xcfff]
[    0.684108] bus: 01 index 1 mmio: [0xdfd00000-0xdfdfffff]
[    0.684112] bus: 01 index 2 mmio: [0x20000000-0x25ffffff]
[    0.684116] bus: 01 index 3 io port: [0x00-0xffff]
[    0.684120] bus: 01 index 4 mmio: [0x000000-0xffffffff]
[    0.684124] bus: 02 index 0 io port: [0xc000-0xc0ff]
[    0.684128] bus: 02 index 1 io port: [0xc400-0xc4ff]
[    0.684132] bus: 02 index 2 mmio: [0x20000000-0x23ffffff]
[    0.684136] bus: 02 index 3 mmio: [0x28000000-0x2bffffff]
[    0.684161] NET: Registered protocol family 2
[    0.684376] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.684765] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.684927] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.685178] TCP: Hash tables configured (established 16384 bind 16384)
[    0.685197] TCP reno registered
[    0.685474] NET: Registered protocol family 1
[    0.685690] checking if image is initramfs... it is
[    1.184064] Switched to high resolution mode on CPU 0
[    1.380173] Freeing initrd memory: 7371k freed
[    1.380314] cpufreq: No nForce2 chipset.
[    1.380631] audit: initializing netlink socket (disabled)
[    1.380672] type=2000 audit(1243274883.380:1): initialized
[    1.387816] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.389678] VFS: Disk quotas dquot_6.5.1
[    1.389815] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.391082] fuse init (API version 7.10)
[    1.391309] msgmni has been set to 977
[    1.391775] alg: No test for stdrng (krng)
[    1.391843] io scheduler noop registered
[    1.391853] io scheduler anticipatory registered
[    1.391857] io scheduler deadline registered
[    1.391919] io scheduler cfq registered (default)
[    1.391949] pci 0000:00:02.0: Boot video device
[    1.403490] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.403522] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.407765] ACPI: AC Adapter [AC0] (on-line)
[    1.410168] ACPI: Battery Slot [BAT0] (battery absent)
[    1.410338] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.410352] ACPI: Power Button (FF) [PWRF]
[    1.410458] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:0f/PNP0C0D:00/input/input1
[    1.410548] ACPI: Lid Switch [LID]
[    1.410665] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.410676] ACPI: Sleep Button (CM) [SLPB]
[    1.410758] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[    1.410776] ACPI: Power Button (CM) [PWRB]
[    1.411131] processor ACPI_CPU:00: registered as cooling_device0
[    1.411150] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.418832] thermal LNXTHERM:01: registered as thermal_zone0
[    1.419044] ACPI: Thermal Zone [THRM] (75 C)
[    1.419179] isapnp: Scanning for PnP cards...
[    1.773117] isapnp: No Plug & Play device found
[    1.776544] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.777113] serial 0000:00:1f.6: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.777131] serial 0000:00:1f.6: PCI INT B disabled
[    1.778787] brd: module loaded
[    1.779705] loop: module loaded
[    1.779960] Fixed MDIO Bus: probed
[    1.779980] PPP generic driver version 2.4.2
[    1.780208] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    1.780300] Driver 'sd' needs updating - please use bus_type methods
[    1.780330] Driver 'sr' needs updating - please use bus_type methods
[    1.780487] ata_piix 0000:00:1f.1: version 2.12
[    1.780507] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    1.780535] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.780623] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.780847] scsi0 : ata_piix
[    1.781115] scsi1 : ata_piix
[    1.783043] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    1.783056] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    1.944477] ata1.00: ATA-6: ST9402112A, 3.04, max UDMA/100
[    1.944490] ata1.00: 78140160 sectors, multi 16: LBA48 
[    1.960483] ata1.00: configured for UDMA/100
[    2.124334] ata2.00: ATAPI:         DVD+RW RW8165, 1.03, max UDMA/33
[    2.140282] ata2.00: configured for UDMA/33
[    2.142280] scsi 0:0:0:0: Direct-Access     ATA      ST9402112A       3.04 PQ: 0 ANSI: 5
[    2.142588] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors: (40.0 GB/37.2 GiB)
[    2.142677] sd 0:0:0:0: [sda] Write Protect is off
[    2.142688] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.142806] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.143045] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors: (40.0 GB/37.2 GiB)
[    2.143130] sd 0:0:0:0: [sda] Write Protect is off
[    2.143141] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.143262] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.143282]  sda: sda1 sda2 < sda5 >
[    2.181790] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.181939] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.184623] scsi 1:0:0:0: CD-ROM                     DVD+RW RW8165    1.03 PQ: 0 ANSI: 5
[    2.191622] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    2.191641] Uniform CD-ROM driver Revision: 3.20
[    2.191863] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.191978] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.193379] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.193459] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    2.193519] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.193525] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.193703] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    2.197650] ehci_hcd 0000:00:1d.7: debug port 1
[    2.197665] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    2.197694] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xdff7bc00
[    2.212023] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.212202] usb usb1: configuration #1 chosen from 1 choice
[    2.212274] hub 1-0:1.0: USB hub found
[    2.212307] hub 1-0:1.0: 6 ports detected
[    2.212600] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.212661] uhci_hcd: USB Universal Host Controller Interface driver
[    2.212776] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.212802] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.212808] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.212948] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.213005] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000df20
[    2.213190] usb usb2: configuration #1 chosen from 1 choice
[    2.213270] hub 2-0:1.0: USB hub found
[    2.213301] hub 2-0:1.0: 2 ports detected
[    2.213553] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.213576] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.213581] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.213731] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    2.213786] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000df40
[    2.213980] usb usb3: configuration #1 chosen from 1 choice
[    2.214061] hub 3-0:1.0: USB hub found
[    2.214092] hub 3-0:1.0: 2 ports detected
[    2.214360] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.214384] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.214389] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.214530] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    2.214589] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000df80
[    2.214771] usb usb4: configuration #1 chosen from 1 choice
[    2.214845] hub 4-0:1.0: USB hub found
[    2.214875] hub 4-0:1.0: 2 ports detected
[    2.215210] usbcore: registered new interface driver libusual
[    2.215316] usbcore: registered new interface driver usbserial
[    2.215350] USB Serial support registered for generic
[    2.215388] usbcore: registered new interface driver usbserial_generic
[    2.215397] usbserial: USB Serial Driver core
[    2.215502] PNP: PS/2 Controller [PNP030b:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    2.223387] i8042.c: Detected active multiplexing controller, rev 1.0.
[    2.225927] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.225950] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    2.225956] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    2.225961] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    2.225965] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    2.226425] mice: PS/2 mouse device common for all mice
[    2.227098] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    2.227148] rtc0: alarms up to one month, 114 bytes nvram
[    2.227311] device-mapper: uevent: version 1.0.3
[    2.227666] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    2.227879] device-mapper: multipath: version 1.0.5 loaded
[    2.227896] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.228204] EISA: Probing bus 0 at eisa.0
[    2.228256] EISA: Detected 0 cards.
[    2.228371] cpuidle: using governor ladder
[    2.228383] cpuidle: using governor menu
[    2.229123] TCP cubic registered
[    2.229330] NET: Registered protocol family 10
[    2.229998] lo: Disabled Privacy Extensions
[    2.230401] NET: Registered protocol family 17
[    2.230475] Bluetooth: L2CAP ver 2.11
[    2.230485] Bluetooth: L2CAP socket layer initialized
[    2.230493] Bluetooth: SCO (Voice Link) ver 0.6
[    2.230498] Bluetooth: SCO socket layer initialized
[    2.230614] Bluetooth: RFCOMM socket layer initialized
[    2.230655] Bluetooth: RFCOMM TTY layer initialized
[    2.230660] Bluetooth: RFCOMM ver 1.10
[    2.230801] Using IPI No-Shortcut mode
[    2.231062] registered taskstats version 1
[    2.231243]   Magic number: 9:845:140
[    2.231284] block ram5: hash matches
[    2.231325] acpi device:11: hash matches
[    2.231377] rtc_cmos 00:02: setting system clock to 2009-05-25 18:08:04 UTC (1243274884)
[    2.231387] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.231391] EDD information not available.
[    2.232495] Freeing unused kernel memory: 532k freed
[    2.232708] Write protecting the kernel text: 4128k
[    2.232758] Write protecting the kernel read-only data: 1532k
[    2.268170] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    2.377092] vesafb: framebuffer at 0xd0000000, mapped to 0xe0080000, using 6144k, total 8000k
[    2.377110] vesafb: mode is 1024x768x32, linelength=4096, pages=1
[    2.377115] vesafb: scrolling: redraw
[    2.377120] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    2.377321] Console: switching to colour frame buffer device 128x48
[    2.433850] fb0: VESA VGA frame buffer device
[    2.748083] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    2.933112] ohci1394 0000:01:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.986803] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[dfdff800-dfdfffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    2.995570] natsemi dp8381x driver, version 2.1, Sept 11, 2006
[    2.995575]   originally by Donald Becker <becker@scyld.com>
[    2.995576]   2.4.x kernel port by Jeff Garzik, Tjeerd Mulder
[    3.003466] usb 2-1: configuration #1 chosen from 1 choice
[    3.018379] natsemi 0000:01:0c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.021764] natsemi eth0: NatSemi DP8381[56] at 0xdfdfe000 (0000:01:0c.0), 00:03:0d:13:f9:7e, IRQ 17, port TP.
[    3.751145] usbcore: registered new interface driver hiddev
[    3.765758] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input6
[    3.767886] generic-usb 0003:046D:C00E.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-1/input0
[    3.796361] usbcore: registered new interface driver usbhid
[    3.823394] usbhid: v2.6:USB HID core driver
[    4.195730] PM: Starting manual resume from disk
[    4.222708] PM: Resume from partition 8:5
[    4.222711] PM: Checking hibernation image.
[    4.223075] PM: Resume from disk failed.
[    4.313526] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00030d49755c9592]
[    4.337395] kjournald starting.  Commit interval 5 seconds
[    4.364172] EXT3-fs: mounted filesystem with ordered data mode.
[   12.274911] udev: starting version 141
[   12.588240] Linux agpgart interface v0.103
[   12.678462] agpgart-intel 0000:00:00.0: Intel 830M Chipset
[   12.720544] agpgart-intel 0000:00:00.0: detected 8060K stolen memory
[   12.764219] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xd0000000
[   13.019510] intel_rng: FWH not detected
[   13.065909] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.179484] iTCO_vendor_support: vendor-support=0
[   13.480313] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   13.538181] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x0460)
[   13.664553] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   13.745721] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   13.904854] yenta_cardbus 0000:01:03.0: CardBus bridge found [1734:103c]
[   13.929317] yenta_cardbus 0000:01:03.0: O2: res at 0x94/0xD4: 00/ea
[   13.953577] yenta_cardbus 0000:01:03.0: O2: enabling read prefetch/write burst
[   14.161997] yenta_cardbus 0000:01:03.0: ISA IRQ mask 0x0cb8, PCI irq 17
[   14.186259] yenta_cardbus 0000:01:03.0: Socket status: 30000821
[   14.210092] pci_bus 0000:01: Raising subordinate bus# of parent bus (#01) from #01 to #05
[   14.273434] yenta_cardbus 0000:01:03.0: pcmcia: parent PCI bridge I/O window: 0xc000 - 0xcfff
[   14.314188] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   14.365278] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc000-0xcfff: clean.
[   14.389401] yenta_cardbus 0000:01:03.0: pcmcia: parent PCI bridge Memory window: 0xdfd00000 - 0xdfdfffff
[   14.459149] yenta_cardbus 0000:01:03.0: pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x25ffffff
[   14.696691] Intel ICH 0000:00:1f.5: enabling device (0005 -> 0007)
[   14.719549] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   14.754976] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   15.136024] pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted into slot 0
[   15.159339] pci 0000:02:00.0: reg 10 32bit mmio: [0x000000-0x001fff]
[   15.213640] b43-pci-bridge 0000:02:00.0: enabling device (0000 -> 0002)
[   15.237229] b43-pci-bridge 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.260866] b43-pci-bridge 0000:02:00.0: setting latency timer to 64
[   15.304372] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   15.336345] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   15.360470] ssb: Sonics Silicon Backplane found on PCI device 0000:02:00.0
[   15.387259] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   15.419260] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   15.445193] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   15.530062] cfg80211: Calling CRDA to update world regulatory domain
[   15.562257] Synaptics Touchpad, model: 1, fw: 4.1, id: 0x848a1, caps: 0x0/0x0
[   15.585348] intel8x0_measure_ac97_clock: measured 60449 usecs
[   15.608250] intel8x0: clocking to 48000
[   15.704758] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input8
[   15.841138] cfg80211: World regulatory domain updated:
[   15.865217]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   15.889784]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.914546]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.939167]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.963609]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.987892]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.039741] b43-phy0: Broadcom 4318 WLAN found
[   16.134080] phy0: Selected rate control algorithm 'pid'
[   16.206398] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]
[   16.529179] lp: driver loaded but no devices found
[   16.860260] Adding 1469908k swap on /dev/sda5.  Priority:-1 extents:1 across:1469908k
[   17.423907] EXT3 FS on sda1, internal journal
[   18.636240] type=1505 audit(1243274900.904:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1947
[   18.714004] type=1505 audit(1243274900.980:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1951
[   18.714400] type=1505 audit(1243274900.980:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1951
[   18.714647] type=1505 audit(1243274900.980:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1951
[   18.714865] type=1505 audit(1243274900.980:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1951
[   18.914029] type=1505 audit(1243274901.180:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1956
[   18.914595] type=1505 audit(1243274901.180:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1956
[   18.965934] type=1505 audit(1243274901.232:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1960
[   25.594626] input: b43-phy0 as /devices/virtual/input/input9
[   25.696116] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   25.772356] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   25.796648] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   25.812664] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   25.959249] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   26.001266] Registered led device: b43-phy0::tx
[   26.001302] Registered led device: b43-phy0::rx
[   26.001343] Registered led device: b43-phy0::radio
[   26.024129] b43-phy0: Radio turned on by software
[   26.024818] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.814964] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   26.814971] Bluetooth: BNEP filters: protocol multicast
[   26.866586] Bridge firewalling registered
[   27.689366] ppdev: user-space parallel port driver
[   28.107506] eth0: DSPCFG accepted after 0 usec.
[   28.107724] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   29.419488] [drm] Initialized drm 1.1.0 20060810
[   29.441839] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   29.441848] pci 0000:00:02.0: setting latency timer to 64
[   29.442177] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   29.563751] [drm:i915_setparam] *ERROR* unknown parameter 4
[   29.563837] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   30.484231] input: b43-phy0 as /devices/virtual/input/input10
[   30.720136] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   30.748154] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   30.773318] Registered led device: b43-phy0::tx
[   30.773362] Registered led device: b43-phy0::rx
[   30.773403] Registered led device: b43-phy0::radio
[   30.805388] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   31.536685] wlan0: authenticate with AP 00:16:01:fb:44:89
[   31.538207] wlan0: authenticated
[   31.538214] wlan0: associate with AP 00:16:01:fb:44:89
[   31.541074] wlan0: RX AssocResp from 00:16:01:fb:44:89 (capab=0x411 status=0 aid=1)
[   31.541081] wlan0: associated
[   31.541800] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   31.557245] wlan0: authenticate with AP 00:16:01:fb:44:89
[   31.560515] wlan0: authenticated
[   31.560523] wlan0: associate with AP 00:16:01:fb:44:89
[   31.562881] wlan0: RX ReassocResp from 00:16:01:fb:44:89 (capab=0x411 status=0 aid=1)
[   31.562887] wlan0: associated
[   31.700438] padlock: VIA PadLock not detected.
[   41.704612] wlan0: disassociating by local choice (reason=3)
[   42.036022] wlan0: no IPv6 routers present
[   43.232726] wlan0: authenticate with AP 00:16:01:fb:44:89
[   43.240252] wlan0: authenticate with AP 00:16:01:fb:44:89
[   43.241772] wlan0: authenticated
[   43.241779] wlan0: associate with AP 00:16:01:fb:44:89
[   43.244982] wlan0: RX ReassocResp from 00:16:01:fb:44:89 (capab=0x411 status=0 aid=1)
[   43.244987] wlan0: associated
[   53.151138] CPU0 attaching NULL sched-domain.
[   53.151295] CPU0 attaching NULL sched-domain.
```
What goes wrong during boot?
Any help will be appreciated.

---

