---
title: "Web Cam video is very dark."
date: 2009-08-15
forum: Hardware
---

### Post by Julita on 2009-08-15
Hello! I have just bought new Lyromedia camera. Skype recognizes it, but the image is very dark. Is there a way to fix it? It appears that there are no drivers for it, and can work only with module LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

UPD 

```
$v4l-conf
v4l-conf: using X11 display :0.0
dga: version 2.0
WARNING: No DGA direct video mode for this display.
mode: 1152x864, depth=24, bpp=32, bpl=4608, base=unknown
/dev/video0 [v4l2]: no overlay support
```

---

### Post by Julita on 2009-08-15
The camera via lsusb is recognized as Microdia PC Camera, and the appropriate driver is loaded to kernel via modprobe, but to no avail. Camorama without LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so wouldn't capture video. Even with preloded module, the video is still very dark, and adjusting brightness, etc doesn't improve the image much. I have no idea what to do else...

---

### Post by Julita on 2009-08-15
dmesg

```
[    0.000000] BIOS EBDA/lowmem at: 00000000/000a0000
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-15-generic (buildd@rothera) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #48-Ubuntu SMP Wed Jul 29 08:54:56 UTC 2009 (Ubuntu 2.6.28-15.48-generic)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000fff0000 (usable)
[    0.000000]  BIOS-e820: 000000000fff0000 - 000000000fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000000fff3000 - 0000000010000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.2 present.
[    0.000000] last_pfn = 0xfff0 max_arch_pfn = 0x100000
[    0.000000] Scanning 2 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)
[    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000093000 (usable)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000000fff0000 (usable)
[    0.000000]  modified: 000000000fff0000 - 000000000fff3000 (ACPI NVS)
[    0.000000]  modified: 000000000fff3000 - 0000000010000000 (ACPI data)
[    0.000000]  modified: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to fff0000 @ 10000-16000
[    0.000000] RAMDISK: 0f8a3000 - 0ffdfff6
[    0.000000] ACPI: RSDP 000F7100, 0014 (r0 JETWAY)
[    0.000000] ACPI: RSDT 0FFF3000, 0028 (r1 JETWAY AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 0FFF3040, 0074 (r1 JETWAY AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 0FFF30C0, 2554 (r1 JETWAY AWRDACPI     1000 MSFT  100000C)
[    0.000000] ACPI: FACS 0FFF0000, 0040
[    0.000000] ACPI: DMI BIOS year==0, assuming ACPI-capable machine
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 255MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 0fff0000
[    0.000000]   low ram: 00000000 - 0fff0000
[    0.000000]   bootmap 00012000 - 00014000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 000fff0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008780ac]    TEXT DATA BSS ==> [0000100000 - 00008780ac]
[    0.000000]   #4 [000f8a3000 - 000ffdfff6]          RAMDISK ==> [000f8a3000 - 000ffdfff6]
[    0.000000]   #5 [0000879000 - 000087d000]    INIT_PG_TABLE ==> [0000879000 - 000087d000]
[    0.000000]   #6 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #7 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #8 [0000012000 - 0000014000]          BOOTMAP ==> [0000012000 - 0000014000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0000fff0
[    0.000000]   HighMem  0x0000fff0 -> 0x0000fff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x00000007
[    0.000000]     0: 0x00000010 -> 0x00000093
[    0.000000]     0: 0x00000100 -> 0x0000fff0
[    0.000000] On node 0 totalpages: 65398
[    0.000000] free_area_init_node: node 0, pgdat c06cb500, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3942 pages, LIFO batch:0
[    0.000000]   Normal zone: 480 pages used for memmap
[    0.000000]   Normal zone: 60944 pages, LIFO batch:15
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 0000000000093000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 10000000:efff0000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 64886
[    0.000000] Kernel command line: root=UUID=8f4c45ff-534f-4bd2-9ad6-ad82c9050365 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 999.980 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.004000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[    0.004000] allocated 1310400 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 242684k/262080k available (4115k kernel code, 18704k reserved, 2199k data, 532k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xd07f0000 - 0xff3fe000   ( 748 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xcfff0000   ( 255 MB)
[    0.004000]       .init : 0xc0733000 - 0xc07b8000   ( 532 kB)
[    0.004000]       .data : 0xc0504f5f - 0xc072ae60   (2199 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0504f5f   (4115 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004030] Calibrating delay loop (skipped), value calculated using timer frequency.. 1999.96 BogoMIPS (lpj=3999920)
[    0.004089] Security Framework initialized
[    0.004125] SELinux:  Disabled at boot.
[    0.004189] AppArmor: AppArmor initialized
[    0.004214] Mount-cache hash table entries: 512
[    0.004645] Initializing cgroup subsys ns
[    0.004657] Initializing cgroup subsys cpuacct
[    0.004663] Initializing cgroup subsys memory
[    0.004674] Initializing cgroup subsys freezer
[    0.004720] CPU: L1 I cache: 16K, L1 D cache: 16K
[    0.004727] CPU: L2 cache: 256K
[    0.004736] CPU serial number disabled.
[    0.004788] Checking 'hlt' instruction... OK.
[    0.021028] SMP alternatives: switching to UP code
[    0.262015] Freeing SMP alternatives: 18k freed
[    0.262037] ACPI: Core revision 20080926
[    0.264309] ACPI: Checking initramfs for custom DSDT
[    0.892601] ACPI: setting ELCR to 0200 (from 1e20)
[    0.894671] weird, boot CPU (#0) not listedby the BIOS.
[    0.894677] SMP motherboard not detected.
[    0.894685] Local APIC not detected. Using dummy APIC emulation.
[    0.894690] SMP disabled
[    0.895700] Brought up 1 CPUs
[    0.895717] Total of 1 processors activated (1999.96 BogoMIPS).
[    0.895769] CPU0 attaching NULL sched-domain.
[    0.897155] net_namespace: 776 bytes
[    0.897201] Booting paravirtualized kernel on bare hardware
[    0.897950] Time: 14:22:22  Date: 08/15/09
[    0.897970] regulator: core version 0.5
[    0.898128] NET: Registered protocol family 16
[    0.898566] EISA bus registered
[    0.898623] ACPI: bus type pci registered
[    0.929871] PCI: PCI BIOS revision 2.10 entry at 0xfb0d0, last bus=1
[    0.929878] PCI: Using configuration type 1 for base access
[    0.933227] ACPI: EC: Look up EC in DSDT
[    0.941285] ACPI: Interpreter enabled
[    0.941301] ACPI: (supports S0 S1 S5)
[    0.941339] ACPI: Using PIC for interrupt routing
[    0.950861] ACPI: No dock devices found.
[    0.950891] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.951012] pci 0000:00:00.0: reg 10 32bit mmio: [0xe0000000-0xe3ffffff]
[    0.951089] pci 0000:00:01.0: supports D1
[    0.951187] pci 0000:00:07.1: reg 20 io port: [0xe000-0xe00f]
[    0.951252] pci 0000:00:07.2: reg 20 io port: [0xe400-0xe41f]
[    0.951352] pci 0000:00:0b.0: reg 10 io port: [0xe800-0xe8ff]
[    0.951362] pci 0000:00:0b.0: reg 14 32bit mmio: [0xe6000000-0xe60000ff]
[    0.951393] pci 0000:00:0b.0: supports D1 D2
[    0.951399] pci 0000:00:0b.0: PME# supported from D1 D2 D3hot
[    0.951407] pci 0000:00:0b.0: PME# disabled
[    0.951444] pci 0000:00:0f.0: reg 10 io port: [0xec00-0xec3f]
[    0.951479] pci 0000:00:0f.0: supports D2
[    0.951548] pci 0000:01:00.0: reg 10 32bit mmio: [0xd0000000-0xd7ffffff]
[    0.951559] pci 0000:01:00.0: reg 14 io port: [0xd000-0xd0ff]
[    0.951568] pci 0000:01:00.0: reg 18 32bit mmio: [0xe5000000-0xe500ffff]
[    0.951589] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.951603] pci 0000:01:00.0: supports D1 D2
[    0.952037] pci 0000:01:00.1: reg 10 32bit mmio: [0xd8000000-0xdfffffff]
[    0.952047] pci 0000:01:00.1: reg 14 32bit mmio: [0xe5010000-0xe501ffff]
[    0.952078] pci 0000:01:00.1: supports D1 D2
[    0.952125] pci 0000:00:01.0: bridge io port: [0xd000-0xdfff]
[    0.952133] pci 0000:00:01.0: bridge 32bit mmio: [0xe4000000-0xe5ffffff]
[    0.952141] pci 0000:00:01.0: bridge 32bit mmio pref: [0xd0000000-0xdfffffff]
[    0.952153] bus 00 -> node 0
[    0.952173] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.989462] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[    0.989945] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 10 11 *12 14 15)
[    0.990422] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 *5 6 7 10 11 12 14 15)
[    0.990910] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *10 11 12 14 15)
[    0.991303] ACPI: WMI: Mapper loaded
[    0.992220] SCSI subsystem initialized
[    0.992384] libata version 3.00 loaded.
[    0.992547] usbcore: registered new interface driver usbfs
[    0.992621] usbcore: registered new interface driver hub
[    0.992717] usbcore: registered new device driver usb
[    0.993060] PCI: Using ACPI for IRQ routing
[    0.993284] Bluetooth: Core ver 2.13
[    0.993284] NET: Registered protocol family 31
[    0.993284] Bluetooth: HCI device and connection manager initialized
[    0.993284] Bluetooth: HCI socket layer initialized
[    0.993284] NET: Registered protocol family 8
[    0.993284] NET: Registered protocol family 20
[    0.993284] NetLabel: Initializing
[    0.993284] NetLabel:  domain hash size = 128
[    0.993284] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.993284] NetLabel:  unlabeled traffic allowed by default
[    0.993284] AppArmor: AppArmor Filesystem Enabled
[    0.993284] pnp: PnP ACPI init
[    0.993284] ACPI: bus type pnp registered
[    1.003773] pnp: PnP ACPI: found 12 devices
[    1.003780] ACPI: ACPI bus type pnp unregistered
[    1.003792] PnPBIOS: Disabled by ACPI PNP
[    1.003849] system 00:00: iomem range 0xf0000-0xf3fff could not be reserved
[    1.003857] system 00:00: iomem range 0xf4000-0xf7fff could not be reserved
[    1.003863] system 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[    1.003870] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
[    1.003877] system 00:00: iomem range 0xfff0000-0xfffffff could not be reserved
[    1.003884] system 00:00: iomem range 0xffff0000-0xffffffff has been reserved
[    1.003891] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    1.003897] system 00:00: iomem range 0x100000-0xffeffff could not be reserved
[    1.003917] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    1.038993] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    1.039001] pci 0000:00:01.0:   IO window: 0xd000-0xdfff
[    1.039012] pci 0000:00:01.0:   MEM window: 0xe4000000-0xe5ffffff
[    1.039020] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    1.039051] pci 0000:00:01.0: setting latency timer to 64
[    1.039061] bus: 00 index 0 io port: [0x00-0xffff]
[    1.039067] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    1.039072] bus: 01 index 0 io port: [0xd000-0xdfff]
[    1.039078] bus: 01 index 1 mmio: [0xe4000000-0xe5ffffff]
[    1.039083] bus: 01 index 2 mmio: [0xd0000000-0xdfffffff]
[    1.039088] bus: 01 index 3 mmio: [0x0-0x0]
[    1.039131] NET: Registered protocol family 2
[    1.039551] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[    1.040289] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    1.040672] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    1.041041] TCP: Hash tables configured (established 8192 bind 8192)
[    1.041048] TCP reno registered
[    1.041403] NET: Registered protocol family 1
[    1.041881] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[    1.663990]  it is
[    2.556889] Freeing initrd memory: 7411k freed
[    2.557150] cpufreq: No nForce2 chipset.
[    2.557710] audit: initializing netlink socket (disabled)
[    2.557792] type=2000 audit(1250346143.556:1): initialized
[    2.575540] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    2.579289] VFS: Disk quotas dquot_6.5.1
[    2.579499] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.581544] fuse init (API version 7.10)
[    2.581800] msgmni has been set to 488
[    2.582549] alg: No test for stdrng (krng)
[    2.582595] io scheduler noop registered
[    2.582601] io scheduler anticipatory registered
[    2.582606] io scheduler deadline registered
[    2.582686] io scheduler cfq registered (default)
[    2.582744] PCI: VIA PCI bridge detected.Disabling DAC.
[    2.582755] pci 0000:00:07.0: Activating ISA DMA hang workarounds
[    2.582802] pci 0000:01:00.0: Boot video device
[    2.592276] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.592301] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.592631] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    2.592640] ACPI: Power Button (FF) [PWRF]
[    2.592748] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    2.592755] ACPI: Power Button (CM) [PWRB]
[    2.592863] fan PNP0C0B:00: registered as cooling_device0
[    2.592886] ACPI: Fan [FAN] (on)
[    2.593297] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    2.593358] processor ACPI_CPU:00: registered as cooling_device1
[    2.593368] ACPI: Processor [CPU0] (supports 2 throttling states)
[    2.598867] thermal LNXTHERM:01: registered as thermal_zone0
[    2.599040] ACPI: Thermal Zone [THRM] (22 C)
[    2.599134] isapnp: Scanning for PnP cards...
[    2.953140] isapnp: No Plug & Play device found
[    2.956400] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.956574] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.956718] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    2.957437] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.957664] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    2.959652] brd: module loaded
[    2.960695] loop: module loaded
[    2.960996] Fixed MDIO Bus: probed
[    2.961017] PPP generic driver version 2.4.2
[    2.961209] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    2.961329] Driver 'sd' needs updating - please use bus_type methods
[    2.961354] Driver 'sr' needs updating - please use bus_type methods
[    2.962766] pata_via 0000:00:07.1: version 0.3.3
[    2.963483] scsi0 : pata_via
[    2.963972] scsi1 : pata_via
[    2.964148] ata1: PATA max UDMA/66 cmd 0x1f0 ctl 0x3f6 bmdma 0xe000 irq 14
[    2.964155] ata2: PATA max UDMA/66 cmd 0x170 ctl 0x376 bmdma 0xe008 irq 15
[    3.155122] ata1.00: ATA-5: IBM-DTLA-307020, TX3OA60A, max UDMA/100
[    3.155130] ata1.00: 40188960 sectors, multi 16: LBA 
[    3.196538] ata1.00: configured for UDMA/66
[    3.368305] ata2.00: ATAPI: PLEXTOR CD-R   PX-W5224A, 1.01, max UDMA/33
[    3.368382] ata2.01: ATAPI: NEC CD-ROM DRIVE:282, 4.A2, max UDMA/33
[    3.384293] ata2.00: configured for UDMA/33
[    3.400298] ata2.01: configured for UDMA/33
[    3.402533] scsi 0:0:0:0: Direct-Access     ATA      IBM-DTLA-307020  TX3O PQ: 0 ANSI: 5
[    3.402866] sd 0:0:0:0: [sda] 40188960 512-byte hardware sectors: (20.5 GB/19.1 GiB)
[    3.402919] sd 0:0:0:0: [sda] Write Protect is off
[    3.402926] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.403000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.403235] sd 0:0:0:0: [sda] 40188960 512-byte hardware sectors: (20.5 GB/19.1 GiB)
[    3.403274] sd 0:0:0:0: [sda] Write Protect is off
[    3.403280] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.403350] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.403363]  sda: sda1 sda2 < sda5 >
[    3.438725] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.438897] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.440101] scsi 1:0:0:0: CD-ROM            PLEXTOR  CD-R   PX-W5224A 1.01 PQ: 0 ANSI: 5
[    3.442705] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    3.442716] Uniform CD-ROM driver Revision: 3.20
[    3.443060] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.443217] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    3.445518] scsi 1:0:1:0: CD-ROM            NEC      CD-ROM DRIVE:282 4.A2 PQ: 0 ANSI: 5
[    3.450037] sr1: scsi3-mmc drive: 17x/40x cd/rw xa/form2 cdda tray
[    3.450238] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    3.450353] sr 1:0:1:0: Attached scsi generic sg2 type 5
[    3.450795] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.450867] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.450905] uhci_hcd: USB Universal Host Controller Interface driver
[    3.452132] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
[    3.452142] PCI: setting IRQ 10 as level-triggered
[    3.452153] uhci_hcd 0000:00:07.2: PCI INT D -> Link[LNKD] -> GSI 10 (level, low) -> IRQ 10
[    3.452178] uhci_hcd 0000:00:07.2: UHCI Host Controller
[    3.452438] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[    3.452492] uhci_hcd 0000:00:07.2: irq 10, io base 0x0000e400
[    3.452788] usb usb1: configuration #1 chosen from 1 choice
[    3.452868] hub 1-0:1.0: USB hub found
[    3.452903] hub 1-0:1.0: 2 ports detected
[    3.453308] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    3.453317] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    3.453477] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.453830] mice: PS/2 mouse device common for all mice
[    3.454295] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    3.454339] rtc0: alarms up to one year, y3k, 242 bytes nvram
[    3.454597] device-mapper: uevent: version 1.0.3
[    3.455044] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    3.455232] device-mapper: multipath: version 1.0.5 loaded
[    3.455242] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.455554] EISA: Probing bus 0 at eisa.0
[    3.455590] Cannot allocate resource for EISA slot 4
[    3.455616] EISA: Detected 0 cards.
[    3.455795] cpuidle: using governor ladder
[    3.455903] cpuidle: using governor menu
[    3.457515] TCP cubic registered
[    3.457805] NET: Registered protocol family 10
[    3.459011] lo: Disabled Privacy Extensions
[    3.459866] NET: Registered protocol family 17
[    3.459941] Bluetooth: L2CAP ver 2.11
[    3.459946] Bluetooth: L2CAP socket layer initialized
[    3.459954] Bluetooth: SCO (Voice Link) ver 0.6
[    3.459959] Bluetooth: SCO socket layer initialized
[    3.460239] Bluetooth: RFCOMM socket layer initialized
[    3.460272] Bluetooth: RFCOMM TTY layer initialized
[    3.460276] Bluetooth: RFCOMM ver 1.10
[    3.460489] IO APIC resources could be not be allocated.
[    3.460558] Using IPI No-Shortcut mode
[    3.460883] registered taskstats version 1
[    3.461141]   Magic number: 5:446:384
[    3.461347] rtc_cmos 00:04: setting system clock to 2009-08-15 14:22:24 UTC (1250346144)
[    3.461355] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.461360] EDD information not available.
[    3.463869] Freeing unused kernel memory: 532k freed
[    3.464423] Write protecting the kernel text: 4116k
[    3.464526] Write protecting the kernel read-only data: 1528k
[    3.480703] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    3.764931] usb 1-1: new low speed USB device using uhci_hcd and address 2
[    3.958909] usb 1-1: configuration #1 chosen from 1 choice
[    4.072193] usb 1-2: new full speed USB device using uhci_hcd and address 3
[    4.244915] usb 1-2: configuration #1 chosen from 1 choice
[    4.375957] Floppy drive(s): fd0 is 1.44M
[    4.396171] FDC 0 is a post-1991 82077
[    4.805069] usbcore: registered new interface driver hiddev
[    4.819570] input: USB Mouse as /devices/pci0000:00/0000:00:07.2/usb1/1-1/1-1:1.0/input/input4
[    4.853564] generic-usb 0003:15D9:0A37.0001: input,hidraw0: USB HID v1.10 Mouse [USB Mouse] on usb-0000:00:07.2-1/input0
[    4.853757] usbcore: registered new interface driver usbhid
[    4.853775] usbhid: v2.6:USB HID core driver
[    4.935957] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    4.936173] 8139cp 0000:00:0b.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    4.961833] 8139too Fast Ethernet driver 0.9.28
[    4.963057] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 12
[    4.963067] PCI: setting IRQ 12 as level-triggered
[    4.963078] 8139too 0000:00:0b.0: PCI INT A -> Link[LNKB] -> GSI 12 (level, low) -> IRQ 12
[    4.965112] eth0: RealTek RTL8139 at 0xe800, 4c:00:10:60:86:f2, IRQ 12
[    4.965119] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    6.220023] Marking TSC unstable due to TSC halts in idle
[    6.302775] PM: Starting manual resume from disk
[    6.302794] PM: Resume from partition 8:5
[    6.302798] PM: Checking hibernation image.
[    6.303309] PM: Resume from disk failed.
[    6.345273] kjournald starting.  Commit interval 5 seconds
[    6.345336] EXT3-fs: mounted filesystem with ordered data mode.
[    8.949537] udev: starting version 141
[    9.360835] Linux agpgart interface v0.103
[    9.382934] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    9.401747] agpgart: Detected VIA Apollo Pro 133 chipset
[    9.435191] agpgart-via 0000:00:00.0: AGP aperture is 64M @ 0xe0000000
[    9.694034] parport_pc 00:0a: reported by Plug and Play ACPI
[    9.694110] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   10.268366] Linux video capture interface: v2.00
[   10.333287] ACPI: I/O resource vt596_smbus [0x5000-0x5007] conflicts with ACPI region SM06 [0x5006-0x5006]
[   10.333302] ACPI: Device needs an ACPI driver
[   10.404933] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   10.429046] gspca: main v2.3.0 registered
[   10.462279] gspca: probing 0c45:612a
[   10.468759] sonixj: Sonix chip id: 12
[   10.473818] gspca: probe ok
[   10.474086] usbcore: registered new interface driver sonixj
[   10.474246] sonixj: registered
[   11.333722] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5
[   11.333737] PCI: setting IRQ 5 as level-triggered
[   11.333748] ENS1371 0000:00:0f.0: PCI INT A -> Link[LNKC] -> GSI 5 (level, low) -> IRQ 5
[   11.905434] ppdev: user-space parallel port driver
[   12.634278] Control name 'Sigmatel Surround Phase Inversion Playback Switch' truncated to 'Sigmatel Surround Phase Inversion Playback '
[   13.234750] lp0: using parport0 (interrupt-driven).
[   13.783532] Adding 730916k swap on /dev/sda5.  Priority:-1 extents:1 across:730916k
[   14.577417] EXT3 FS on sda1, internal journal
[   24.334465] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[   24.334483] PCI: setting IRQ 11 as level-triggered
[   24.334494] pci 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   24.859690] [drm] Initialized drm 1.1.0 20060810
[   25.118543] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   26.362062] agpgart-via 0000:00:00.0: AGP 1.0 bridge
[   26.362110] agpgart-via 0000:00:00.0: putting AGP V2 device into 2x mode
[   26.362151] pci 0000:01:00.0: putting AGP V2 device into 2x mode
[   26.673407] [drm] Setting GART location based on new memory map
[   26.673441] [drm] Loading R200 Microcode
[   26.673556] [drm] writeback test succeeded in 1 usecs
[   28.966025] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   38.972057] eth0: no IPv6 routers present
[ 2498.520197] usb 1-2: USB disconnect, address 3
[ 2498.521097] gspca: disconnect complete
[ 2516.120335] usb 1-2: new full speed USB device using uhci_hcd and address 4
[ 2516.321053] usb 1-2: configuration #1 chosen from 1 choice
[ 2517.026865] Initializing USB Mass Storage driver...
[ 2517.046519] scsi2 : SCSI emulation for USB Mass Storage devices
[ 2517.061427] usbcore: registered new interface driver usb-storage
[ 2517.061442] USB Mass Storage support registered.
[ 2517.074235] usb-storage: device found at 4
[ 2517.074249] usb-storage: waiting for device to settle before scanning
[ 2522.099733] usb-storage: device scan complete
[ 2522.109669] scsi 2:0:0:0: Direct-Access     CREATIVE NOMAD MuVo TX    1223 PQ: 0 ANSI: 4
[ 2522.134139] sd 2:0:0:0: [sdb] 117824 2048-byte hardware sectors: (241 MB/230 MiB)
[ 2522.142387] sd 2:0:0:0: [sdb] Write Protect is off
[ 2522.142433] sd 2:0:0:0: [sdb] Mode Sense: 38 00 00 00
[ 2522.142443] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 2522.163515] sd 2:0:0:0: [sdb] 117824 2048-byte hardware sectors: (241 MB/230 MiB)
[ 2522.176431] sd 2:0:0:0: [sdb] Write Protect is off
[ 2522.176485] sd 2:0:0:0: [sdb] Mode Sense: 38 00 00 00
[ 2522.176498] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 2522.176594]  sdb: sdb1
[ 2522.195977] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[ 2522.202738] sd 2:0:0:0: Attached scsi generic sg3 type 0
[ 2616.072179] usb 1-2: USB disconnect, address 4
[ 2644.344149] usb 1-1: USB disconnect, address 2
[ 2646.552200] usb 1-2: new low speed USB device using uhci_hcd and address 5
[ 2646.726651] usb 1-2: configuration #1 chosen from 1 choice
[ 2646.755583] input: USB Mouse as /devices/pci0000:00/0000:00:07.2/usb1/1-2/1-2:1.0/input/input6
[ 2646.780422] generic-usb 0003:15D9:0A37.0002: input,hidraw0: USB HID v1.10 Mouse [USB Mouse] on usb-0000:00:07.2-2/input0
[ 2650.312804] usb 1-1: new full speed USB device using uhci_hcd and address 6
[ 2650.522400] usb 1-1: configuration #1 chosen from 1 choice
[ 2650.526716] gspca: probing 0c45:612a
[ 2650.539226] sonixj: Sonix chip id: 12
[ 2650.549941] gspca: probe ok
[11692.053700] Thunar[10357]: segfault at c ip b7ee9fa2 sp bf986b60 error 4 in libexo-0.3.so.0.5.0[b7ecb000+39000]
[14262.648272] usb 1-1: USB disconnect, address 6
[14262.653877] gspca: disconnect complete
[16710.152075] usb 1-1: new full speed USB device using uhci_hcd and address 7
[16710.310824] usb 1-1: configuration #1 chosen from 1 choice
[16710.313113] gspca: probing 0c45:612a
[16710.318151] sonixj: Sonix chip id: 12
[16710.322158] gspca: probe ok
 
```

---

### Post by dovael on 2009-11-04
Did you find a solution, because I have a similar webcam?

---

### Post by Julita on 2009-11-04
dovael, no I haven't... I guess it will remain the same... there is a Google group microdia [http://groups.google.mv/group/microdia](http://groups.google.mv/group/microdia) maybe they will be able to fix your problem.

---

