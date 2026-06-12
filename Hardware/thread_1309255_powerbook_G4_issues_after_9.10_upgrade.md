---
title: "powerbook G4 issues after 9.10 upgrade"
date: 2009-11-01
forum: Hardware
---

### Post by heliogabalus on 2009-11-01
hey. long time user first time poster. 

I had my powerbook running perfectly on 9.04, but when I upgraded to 9.10 I got the following issues:

1) the fan is now on full throttle all the time! even when the CPU is idle and I'm not using the computer it's like it's been on full activity all day. I tried adding 'acpi_osl=Linux' to the yaboot boot command and tried some of the acpi commands in this forum but nothing works.

2) there is no battery indicator in the power manager. in fact, worse than that, it seems to ignore the fact that there's a battery at all! so there's no warning of low battery whatsoever. it just turns off. no shutdown, nothing. 

regardless to say, these two worked fine on 9.04. any thoughts? thanks!

dmesg output:
```

[    0.000000] Using PowerMac machine description
[    0.000000] Total memory = 2048MB; using 4096kB for hash table (at cfc00000)
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Linux version 2.6.31-14-powerpc (buildd@adare) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu Fri Oct 16 14:11:44 UTC 2009 (Ubuntu 2.6.31-14.48-powerpc)
[    0.000000] Found initrd at 0xc1c00000:0xc2417000
[    0.000000] Found UniNorth memory controller & host bridge @ 0xf8000000 revision: 0xd2
[    0.000000] Mapped at 0xff7c0000
[    0.000000] Found a Intrepid mac-io controller, rev: 0, mapped at 0xff740000
[    0.000000] Processor NAP mode on idle enabled.
[    0.000000] PowerMac motherboard: PowerBook G4 15"
[    0.000000] via-pmu: Server Mode is disabled
[    0.000000] PMU driver v2 initialized for Core99, firmware: 0c
[    0.000000] console [udbg0] enabled
[    0.000000] Found UniNorth PCI host bridge at 0x00000000f0000000. Firmware bus number: 0->1
[    0.000000] PCI host bridge /pci@f0000000  ranges:
[    0.000000]  MEM 0x00000000f1000000..0x00000000f1ffffff -> 0x00000000f1000000
[    0.000000]   IO 0x00000000f0000000..0x00000000f07fffff -> 0x0000000000000000
[    0.000000]  MEM 0x00000000b0000000..0x00000000bfffffff -> 0x00000000b0000000
[    0.000000] Found UniNorth PCI host bridge at 0x00000000f2000000. Firmware bus number: 0->1
[    0.000000] PCI host bridge /pci@f2000000 (primary) ranges:
[    0.000000]  MEM 0x00000000f3000000..0x00000000f3ffffff -> 0x00000000f3000000
[    0.000000]   IO 0x00000000f2000000..0x00000000f27fffff -> 0x0000000000000000
[    0.000000]  MEM 0x0000000080000000..0x00000000afffffff -> 0x0000000080000000
[    0.000000] Found UniNorth PCI host bridge at 0x00000000f4000000. Firmware bus number: 0->1
[    0.000000] PCI host bridge /pci@f4000000  ranges:
[    0.000000]  MEM 0x00000000f5000000..0x00000000f5ffffff -> 0x00000000f5000000
[    0.000000]   IO 0x00000000f4000000..0x00000000f47fffff -> 0x0000000000000000
[    0.000000] nvram: Checking bank 0...
[    0.000000] nvram: gen0=1219, gen1=1220
[    0.000000] nvram: Active bank is: 1
[    0.000000] nvram: OF partition at 0x410
[    0.000000] nvram: XP partition at 0x1020
[    0.000000] nvram: NR partition at 0x1120
[    0.000000] Top of RAM: 0x80000000, Total RAM: 0x80000000
[    0.000000] Memory hole size: 0MB
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00030000
[    0.000000]   Normal   0x00030000 -> 0x00030000
[    0.000000]   HighMem  0x00030000 -> 0x00080000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00080000
[    0.000000] On node 0 totalpages: 524288
[    0.000000] free_area_init_node: node 0, pgdat c05f0ac4, node_mem_map c0685000
[    0.000000]   DMA zone: 1536 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 195072 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2560 pages used for memmap
[    0.000000]   HighMem zone: 325120 pages, LIFO batch:31
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 520192
[    0.000000] Kernel command line: root=/dev/hda3 ro quiet splash acpi_osl=Linux
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] High memory: 1310720k
[    0.000000] Memory: 2059372k/2097152k available (5876k kernel code, 36592k reserved, 224k data, 478k bss, 228k init)
[    0.000000] Kernel virtual memory layout:
[    0.000000]   * 0xfffef000..0xfffff000  : fixmap
[    0.000000]   * 0xff800000..0xffc00000  : highmem PTEs
[    0.000000]   * 0xfdf32000..0xff800000  : early ioremap
[    0.000000]   * 0xf1000000..0xfdf32000  : vmalloc & ioremap
[    0.000000] SLUB: Genslabs=13, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] NR_IRQS:512
[    0.000000] mpic: Setting up MPIC " MPIC 1   " version 1.2 at 80040000, max 4 CPUs
[    0.000000] mpic: ISU size: 64, shift: 6, mask: 3f
[    0.000000] mpic: Initializing for 64 sources
[    0.000000] GMT Delta read from XPRAM: 0 minutes, DST: off
[    0.000000] time_init: decrementer frequency = 18.432000 MHz
[    0.000000] time_init: processor frequency   = 1249.999995 MHz
[    0.000000] clocksource: timebase mult[d9038e4] shift[22] registered
[    0.000000] clockevent: decrementer mult[4b7f5a5] shift[32] cpu[0]
[    0.000129] Console: colour dummy device 80x25
[    0.000141] console handover: boot [udbg0] -> real [tty0]
[    0.000208] Security Framework initialized
[    0.000300] AppArmor: AppArmor initialized
[    0.000321] Mount-cache hash table entries: 512
[    0.000833] device-tree: Duplicate name in /cpus/PowerPC,G4@0, renamed to "l2-cache#1"
[    0.004034] Initializing cgroup subsys ns
[    0.004092] Initializing cgroup subsys devices
[    0.004101] Initializing cgroup subsys freezer
[    0.004108] Initializing cgroup subsys net_cls
[    0.005811] regulator: core version 0.5
[    0.005994] NET: Registered protocol family 16
[    0.006520] MPC7450 family performance monitor hardware support registered
[    0.006590] irq: irq 42 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 42
[    0.006638] KeyWest i2c @0xf8001003 irq 42 /uni-n@f8000000/i2c@f8001000
[    0.006649]  channel 0 bus <multibus>
[    0.006654]  channel 1 bus <multibus>
[    0.006763]  channel 2 bus <multibus>
[    0.006875] irq: irq 25 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 25
[    0.006911] irq: irq 47 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 47
[    0.007569] PCI: Probing PCI hardware
[    0.007781] pci 0000:00:10.0: reg 10 32bit mmio: [0xb8000000-0xbfffffff]
[    0.007793] pci 0000:00:10.0: reg 14 io port: [0x400-0x4ff]
[    0.007805] pci 0000:00:10.0: reg 18 32bit mmio: [0xb0000000-0xb000ffff]
[    0.007827] pci 0000:00:10.0: reg 30 32bit mmio: [0xb0020000-0xb003ffff]
[    0.007856] pci 0000:00:10.0: supports D1 D2
[    0.007924] irq: irq 48 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 48
[    0.008270] pci 0001:10:12.0: reg 10 32bit mmio: [0xa0006000-0xa0007fff]
[    0.008318] pci 0001:10:12.0: supports D1 D2
[    0.008326] pci 0001:10:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.008337] pci 0001:10:12.0: PME# disabled
[    0.008381] pci 0001:10:13.0: reg 10 32bit mmio: [0xa0004000-0xa0004fff]
[    0.008408] pci 0001:10:13.0: supports D1 D2
[    0.008414] pci 0001:10:13.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.008423] pci 0001:10:13.0: PME# disabled
[    0.008459] pci 0001:10:17.0: reg 10 32bit mmio: [0x80000000-0x8007ffff]
[    0.008520] pci 0001:10:18.0: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.008592] pci 0001:10:19.0: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.008656] pci 0001:10:1a.0: reg 10 32bit mmio: [0xa0003000-0xa0003fff]
[    0.008729] pci 0001:10:1b.0: reg 10 32bit mmio: [0xa0002000-0xa0002fff]
[    0.008777] pci 0001:10:1b.0: supports D1 D2
[    0.008784] pci 0001:10:1b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.008793] pci 0001:10:1b.0: PME# disabled
[    0.008835] pci 0001:10:1b.1: reg 10 32bit mmio: [0xa0001000-0xa0001fff]
[    0.008883] pci 0001:10:1b.1: supports D1 D2
[    0.008890] pci 0001:10:1b.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.008899] pci 0001:10:1b.1: PME# disabled
[    0.008941] pci 0001:10:1b.2: reg 10 32bit mmio: [0xa0000000-0xa00000ff]
[    0.008989] pci 0001:10:1b.2: supports D1 D2
[    0.008996] pci 0001:10:1b.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.009005] pci 0001:10:1b.2: PME# disabled
[    0.009066] irq: irq 52 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 52
[    0.009097] irq: irq 53 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 53
[    0.009137] irq: irq 27 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 27
[    0.009174] irq: irq 28 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 28
[    0.009210] irq: irq 29 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 29
[    0.009243] irq: irq 63 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 63
[    0.010035] pci 0002:24:0d.0: reg 10 32bit mmio: [0xf5004000-0xf5007fff]
[    0.010096] pci 0002:24:0e.0: reg 10 32bit mmio: [0xf5000000-0xf5000fff]
[    0.010136] pci 0002:24:0e.0: supports D1 D2
[    0.010143] pci 0002:24:0e.0: PME# supported from D0 D1 D2 D3hot
[    0.010152] pci 0002:24:0e.0: PME# disabled
[    0.010186] pci 0002:24:0f.0: reg 10 32bit mmio: [0xf5200000-0xf53fffff]
[    0.010213] pci 0002:24:0f.0: reg 30 32bit mmio: [0xf5100000-0xf51fffff]
[    0.010281] irq: irq 39 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 39
[    0.010313] irq: irq 40 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 40
[    0.010347] irq: irq 41 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 41
[    0.010722] PCI 0000:00 Cannot reserve Legacy IO [0x802000-0x802fff]
[    0.010755] pci 0001:10:13.0: CardBus bridge, secondary bus 0001:11
[    0.010764] pci 0001:10:13.0:   IO window: 0x001000-0x0010ff
[    0.010774] pci 0001:10:13.0:   IO window: 0x001100-0x0011ff
[    0.010784] pci 0001:10:13.0:   PREFETCH window: 0x84000000-0x87ffffff
[    0.010794] pci 0001:10:13.0:   MEM window: 0x88000000-0x8bffffff
[    0.010824] pci_bus 0000:00: resource 0 io:  [0x802000-0x1001fff]
[    0.010833] pci_bus 0000:00: resource 1 mem: [0xf1000000-0xf1ffffff]
[    0.010841] pci_bus 0000:00: resource 2 mem: [0xb0000000-0xbfffffff]
[    0.010850] pci_bus 0001:10: resource 0 io:  [0x00-0x7fffff]
[    0.010858] pci_bus 0001:10: resource 1 mem: [0xf3000000-0xf3ffffff]
[    0.010867] pci_bus 0001:10: resource 2 mem: [0x80000000-0xafffffff]
[    0.010876] pci_bus 0001:11: resource 0 io:  [0x1000-0x10ff]
[    0.010884] pci_bus 0001:11: resource 1 io:  [0x1100-0x11ff]
[    0.010892] pci_bus 0001:11: resource 2 pref mem [0x84000000-0x87ffffff]
[    0.010901] pci_bus 0001:11: resource 3 mem: [0x88000000-0x8bffffff]
[    0.010910] pci_bus 0002:24: resource 0 io:  [0xff7fe000-0xffffdfff]
[    0.010919] pci_bus 0002:24: resource 1 mem: [0xf5000000-0xf5ffffff]
[    0.015669] bio: create slab <bio-0> at 0
[    0.016481] SCSI subsystem initialized
[    0.016620] libata version 3.00 loaded.
[    0.016848] usbcore: registered new interface driver usbfs
[    0.016884] usbcore: registered new interface driver hub
[    0.016971] usbcore: registered new device driver usb
[    0.020208] Switched to high resolution mode on CPU 0
[    0.024013] AppArmor: AppArmor Filesystem Enabled
[    0.024112] NET: Registered protocol family 2
[    0.024456] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.025482] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.027721] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[    0.028367] TCP: Hash tables configured (established 131072 bind 65536)
[    0.028377] TCP reno registered
[    0.028693] NET: Registered protocol family 1
[    0.028924] Trying to unpack rootfs image as initramfs...
[    0.531038] Freeing initrd memory: 8284k freed
[    0.532240] Thermal assist unit not available
[    0.532535] setup_kcore: restrict size=3fffffff
[    0.532644] Registering PowerMac CPU frequency driver
[    0.532652] Low: 765 Mhz, High: 1249 Mhz, Boot: 765 Mhz
[    0.564381] audit: initializing netlink socket (disabled)
[    0.564411] type=2000 audit(1257075174.564:1): initialized
[    0.577126] highmem bounce pool size: 64 pages
[    0.579939] VFS: Disk quotas dquot_6.5.2
[    0.580055] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.580728] fuse init (API version 7.12)
[    0.580892] msgmni has been set to 1480
[    0.581291] alg: No test for stdrng (krng)
[    0.581314] io scheduler noop registered
[    0.581318] io scheduler anticipatory registered
[    0.581322] io scheduler deadline registered
[    0.581405] io scheduler cfq registered (default)
[    0.581709] radeonfb 0000:00:10.0: enabling device (0006 -> 0007)
[    0.777320] radeonfb 0000:00:10.0: Invalid ROM contents
[    0.777331] radeonfb (0000:00:10.0): Invalid ROM signature 303 should be 0xaa55
[    0.777340] radeonfb: Retrieved PLL infos from Open Firmware
[    0.777346] radeonfb: Reference=27.00 MHz (RefDiv=12) Memory=200.00 Mhz, System=300.00 MHz
[    0.777351] radeonfb: PLL min 12000 max 35000
[    0.873247] i2c-adapter i2c-2: unable to read EDID block.
[    1.025245] i2c-adapter i2c-2: unable to read EDID block.
[    1.177241] i2c-adapter i2c-2: unable to read EDID block.
[    1.533143] radeonfb: Monitor 1 type LCD found
[    1.533146] radeonfb: EDID probed
[    1.533149] radeonfb: Monitor 2 type no found
[    1.533161] radeonfb: Using Firmware dividers 0x0002008e from PPLL 0
[    1.533222] radeonfb: Dynamic Clock Power Management enabled
[    1.565600] Console: switching to colour frame buffer device 160x53
[    1.587030] radeonfb: Backlight initialized (radeonbl0)
[    1.587035] radeonfb (0000:00:10.0): ATI Radeon 4e50 "NP"
[    1.589452] Generic non-volatile memory driver v1.1
[    1.591043] brd: module loaded
[    1.591102] MacIO PCI driver attached to Intrepid chipset
[    1.591387] irq: irq 32 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 32
[    1.591553] irq: irq 24 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 24
[    1.591568] irq: irq 12 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 16
[    1.591626] irq: irq 22 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 22
[    1.591640] irq: irq 5 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 17
[    1.591653] irq: irq 6 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 18
[    1.591728] irq: irq 23 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 23
[    1.591741] irq: irq 7 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 19
[    1.591755] irq: irq 8 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 20
[    1.592024] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.592276] Uniform Multi-Platform E-IDE driver
[    1.592351] adb: starting probe task...
[    1.593633] ide-pmac 0002:24:0d.0: enabling device (0000 -> 0002)
[    1.845193] adb devices: [2]: 2 c4 [3]: 3 1 [7]: 7 1f
[    1.851699] ADB keyboard at 2, handler 1
[    1.851717] Detected ADB keyboard, type ISO, swapping keys.
[    1.851818] input: ADB keyboard as /devices/virtual/input/input1
[    1.851897] input: ADB Powerbook buttons as /devices/virtual/input/input2
[    1.867023] ADB mouse at 3, handler set to 4 (trackpad)
[    1.927082] input: ADB mouse as /devices/virtual/input/input3
[    1.927088] adb: finished probe task...
[    2.612160] ide-pmac: Found Apple UniNorth ATA-6 controller (PCI), bus ID 3, irq 39
[    2.612187] Probing IDE interface ide0...
[    2.900343] hda: FUJITSU MHT2080AT, ATA DISK drive
[    3.572204] hda: host max PIO4 wanted PIO255(auto-tune) selected PIO4
[    3.574532] hda: UDMA/100 mode selected
[    3.576745] ide0 at 0xf1032000-0xf1032070,0xf1032160 on irq 39
[    4.596160] ide-pmac: Found Apple KeyLargo ATA-3 controller (macio), bus ID 0, irq 24
[    4.596179] Probing IDE interface ide1...
[    4.996335] hdc: MATSHITADVD-R UJ-816, ATAPI CD/DVD-ROM drive
[    5.332218] hdc: host max PIO4 wanted PIO255(auto-tune) selected PIO4
[    5.332581] hdc: MWDMA2 mode selected
[    5.333163] ide1 at 0xf1026000-0xf1026070,0xf1026160 on irq 24
[    5.333238] ide-gd driver 1.18
[    5.333274] hda: max request size: 512KiB
[    5.404371] hda: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=16383/255/63
[    5.407386] hda: cache flushes supported
[    5.407470]  hda: [mac] hda1 hda2 hda3 hda4
[    5.412171] ide-cd driver 5.00
[    5.413838] ide-cd: hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
[    5.413850] Uniform CD-ROM driver Revision: 3.20
[    5.424938] Fixed MDIO Bus: probed
[    5.425032] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    5.425072] ehci_hcd 0001:10:1b.2: enabling device (0004 -> 0006)
[    5.425088] ehci_hcd 0001:10:1b.2: EHCI Host Controller
[    5.425156] ehci_hcd 0001:10:1b.2: new USB bus registered, assigned bus number 1
[    5.448191] ehci_hcd 0001:10:1b.2: irq 63, io mem 0xa0000000
[    5.460161] ehci_hcd 0001:10:1b.2: USB 2.0 started, EHCI 1.00
[    5.460313] usb usb1: configuration #1 chosen from 1 choice
[    5.460369] hub 1-0:1.0: USB hub found
[    5.460387] hub 1-0:1.0: 5 ports detected
[    5.460490] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    5.460527] Apple USB OHCI 0001:10:18.0 disabled by firmware
[    5.460544] Apple USB OHCI 0001:10:19.0 disabled by firmware
[    5.460559] ohci_hcd 0001:10:1a.0: enabling device (0000 -> 0002)
[    5.460575] ohci_hcd 0001:10:1a.0: OHCI Host Controller
[    5.460645] ohci_hcd 0001:10:1a.0: new USB bus registered, assigned bus number 2
[    5.460672] ohci_hcd 0001:10:1a.0: irq 29, io mem 0xa0003000
[    5.535810] usb usb2: configuration #1 chosen from 1 choice
[    5.535857] hub 2-0:1.0: USB hub found
[    5.535876] hub 2-0:1.0: 2 ports detected
[    5.535954] ohci_hcd 0001:10:1b.0: enabling device (0000 -> 0002)
[    5.535967] ohci_hcd 0001:10:1b.0: OHCI Host Controller
[    5.536030] ohci_hcd 0001:10:1b.0: new USB bus registered, assigned bus number 3
[    5.536049] ohci_hcd 0001:10:1b.0: irq 63, io mem 0xa0002000
[    5.607790] usb usb3: configuration #1 chosen from 1 choice
[    5.607835] hub 3-0:1.0: USB hub found
[    5.607852] hub 3-0:1.0: 3 ports detected
[    5.607928] ohci_hcd 0001:10:1b.1: enabling device (0000 -> 0002)
[    5.607942] ohci_hcd 0001:10:1b.1: OHCI Host Controller
[    5.607994] ohci_hcd 0001:10:1b.1: new USB bus registered, assigned bus number 4
[    5.608013] ohci_hcd 0001:10:1b.1: irq 63, io mem 0xa0001000
[    5.679784] usb usb4: configuration #1 chosen from 1 choice
[    5.679829] hub 4-0:1.0: USB hub found
[    5.679860] hub 4-0:1.0: 2 ports detected
[    5.679938] uhci_hcd: USB Universal Host Controller Interface driver
[    5.680163] mice: PS/2 mouse device common for all mice
[    5.680249] PowerMac i2c bus pmu 2 registered
[    5.680284] PowerMac i2c bus pmu 1 registered
[    5.680317] PowerMac i2c bus mac-io 0 registered
[    5.680351] PowerMac i2c bus uni-n 1 registered
[    5.680407] PowerMac i2c bus uni-n 0 registered
[    5.681232] TCP cubic registered
[    5.681238] NET: Registered protocol family 17
[    5.681426] registered taskstats version 1
[    5.681715] input: PMU as /devices/virtual/input/input4
[    5.681755] Registered led device: pmu-front-led
[    5.681762] /build/buildd/linux-2.6.31/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[    5.681790] Freeing unused kernel memory: 228k init
[    5.880918] usb 2-1: new full speed USB device using ohci_hcd and address 2
[    6.070388] usb 2-1: configuration #1 chosen from 1 choice
[    6.084284] Linux agpgart interface v0.103
[    6.145382] agpgart-uninorth 0000:00:0b.0: Apple UniNorth 2 chipset
[    6.145528] agpgart-uninorth 0000:00:0b.0: configuring for size idx: 8
[    6.145620] agpgart-uninorth 0000:00:0b.0: AGP aperture is 32M @ 0x0
[    6.258010] b43-pci-bridge 0001:10:12.0: enabling device (0004 -> 0006)
[    6.261410] ssb: Sonics Silicon Backplane found on PCI device 0001:10:12.0
[    6.394820] ohci1394 0002:24:0e.0: enabling device (0000 -> 0002)
[    6.439687] usbcore: registered new interface driver hiddev
[    6.450440] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[40]  MMIO=[f5000000-f50007ff]  Max Packet=[4096]  IR/IT contexts=[8/8]
[    6.469843] input: HID 05ac:1000 as /devices/pci0001:10/0001:10:1a.0/usb2/2-1/2-1:1.0/input/input5
[    6.469960] generic-usb 0003:05AC:1000.0001: input,hidraw0: USB HID v1.11 Keyboard [HID 05ac:1000] on usb-0001:10:1a.0-1/input0
[    6.471008] sungem.c:v0.98 8/24/03 David S. Miller (davem@redhat.com)
[    6.500136] input: HID 05ac:1000 as /devices/pci0001:10/0001:10:1a.0/usb2/2-1/2-1:1.1/input/input6
[    6.500327] generic-usb 0003:05AC:1000.0002: input,hidraw1: USB HID v1.11 Mouse [HID 05ac:1000] on usb-0001:10:1a.0-1/input1
[    6.500365] usbcore: registered new interface driver usbhid
[    6.500371] usbhid: v2.6:USB HID core driver
[    6.540662] PHY ID: 1410cc1, addr: 0
[    6.541500] eth0: Sun GEM (PCI) 10/100/1000BaseT Ethernet 00:0a:95:db:b2:3c
[    6.541506] eth0: Found Marvell 88E1111 PHY
[    6.796073] device-mapper: uevent: version 1.0.3
[    6.796326] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    7.066348] PM: Starting manual resume from disk
[    7.073100] EXT3-fs: INFO: recovery required on readonly filesystem.
[    7.073108] EXT3-fs: write access will be enabled during recovery.
[    7.740908] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000a95fffedbb23c]
[    9.583726] kjournald starting.  Commit interval 5 seconds
[    9.583759] EXT3-fs: recovery complete.
[    9.584091] EXT3-fs: mounted filesystem with writeback data mode.
[   11.246144] type=1505 audit(1257075185.244:2): operation="profile_load" pid=359 name=/usr/share/gdm/guest-session/Xsession
[   11.292830] type=1505 audit(1257075185.292:3): operation="profile_load" pid=360 name=/sbin/dhclient3
[   11.293597] type=1505 audit(1257075185.292:4): operation="profile_load" pid=360 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   11.294014] type=1505 audit(1257075185.292:5): operation="profile_load" pid=360 name=/usr/lib/connman/scripts/dhclient-script
[   11.402806] type=1505 audit(1257075185.400:6): operation="profile_load" pid=361 name=/usr/bin/evince
[   11.415510] type=1505 audit(1257075185.412:7): operation="profile_load" pid=361 name=/usr/bin/evince-previewer
[   11.423016] type=1505 audit(1257075185.420:8): operation="profile_load" pid=361 name=/usr/bin/evince-thumbnailer
[   11.459487] type=1505 audit(1257075185.456:9): operation="profile_load" pid=363 name=/usr/lib/cups/backend/cups-pdf
[   11.460479] type=1505 audit(1257075185.460:10): operation="profile_load" pid=363 name=/usr/sbin/cupsd
[   11.465651] type=1505 audit(1257075185.464:11): operation="profile_load" pid=364 name=/usr/sbin/tcpdump
[   13.269733] Adding 3228828k swap on /dev/hda4.  Priority:-1 extents:1 across:3228828k
[   13.691422] EXT3 FS on hda3, internal journal
[   16.710221] type=1505 audit(1257075190.707:12): operation="profile_replace" pid=481 name=/usr/share/gdm/guest-session/Xsession
[   16.716060] type=1505 audit(1257075190.711:13): operation="profile_replace" pid=482 name=/sbin/dhclient3
[   16.716878] type=1505 audit(1257075190.715:14): operation="profile_replace" pid=482 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   16.717295] type=1505 audit(1257075190.715:15): operation="profile_replace" pid=482 name=/usr/lib/connman/scripts/dhclient-script
[   16.731583] type=1505 audit(1257075190.727:16): operation="profile_replace" pid=483 name=/usr/bin/evince
[   16.745391] type=1505 audit(1257075190.743:17): operation="profile_replace" pid=483 name=/usr/bin/evince-previewer
[   16.753891] type=1505 audit(1257075190.751:18): operation="profile_replace" pid=483 name=/usr/bin/evince-thumbnailer
[   16.768863] type=1505 audit(1257075190.767:19): operation="profile_replace" pid=485 name=/usr/lib/cups/backend/cups-pdf
[   16.769822] type=1505 audit(1257075190.767:20): operation="profile_replace" pid=485 name=/usr/sbin/cupsd
[   16.774792] type=1505 audit(1257075190.771:21): operation="profile_replace" pid=486 name=/usr/sbin/tcpdump
[   23.526350] NET: Registered protocol family 10
[   23.527033] lo: Disabled Privacy Extensions
[   23.527761] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   24.513651] hda: host max PIO4 wanted PIO0 selected PIO0
[   25.964841] udev: starting version 147
[   26.845958] usb 2-1: USB disconnect, address 2
[   26.848029] usb 2-1: usbfs: USBDEVFS_CONTROL failed cmd hid2hci rqt 64 rq 0 len 0 ret -108
[   27.184221] usb 2-1: new full speed USB device using ohci_hcd and address 3
[   27.383389] usb 2-1: configuration #1 chosen from 1 choice
[   33.552704] radeonfb 0000:00:10.0: Invalid ROM contents
[   33.552822] radeonfb 0000:00:10.0: Invalid ROM contents
[   33.651077] ip_tables: (C) 2000-2006 Netfilter Core Team
[   34.180076] cfg80211: Calling CRDA to update world regulatory domain
[   34.212186] Bluetooth: Core ver 2.15
[   34.212294] NET: Registered protocol family 31
[   34.212299] Bluetooth: HCI device and connection manager initialized
[   34.212306] Bluetooth: HCI socket layer initialized
[   34.447712] cfg80211: World regulatory domain updated:
[   34.447723]  (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   34.447729]  (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   34.447735]  (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   34.447741]  (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   34.447746]  (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   34.447752]  (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   34.785729] Bluetooth: Generic Bluetooth USB driver ver 0.5
[   34.785988] usbcore: registered new interface driver btusb
[   34.918685] [drm] Initialized drm 1.1.0 20060810
[   34.920291] rtc-generic rtc-generic: rtc core: registered rtc-generic as rtc0
[   35.106444] [drm] Initialized radeon 1.31.0 20080528 for 0000:00:10.0 on minor 0
[   35.163207] pmac_zilog: 0.6 (Benjamin Herrenschmidt <benh@kernel.crashing.org>)
[   35.163358] ttyPZ0 at MMIO 0x80013020 (irq = 22) is a Z85c30 ESCC - Serial port
[   35.163506] ttyPZ1 at MMIO 0x80013000 (irq = 23) is a Z85c30 ESCC - Serial port
[   35.194862] yenta_cardbus 0001:10:13.0: CardBus bridge found [0000:0000]
[   35.194886] yenta_cardbus 0001:10:13.0: Enabling burst memory read transactions
[   35.194893] yenta_cardbus 0001:10:13.0: Using CSCINT to route CSC interrupts to PCI
[   35.194898] yenta_cardbus 0001:10:13.0: Routing CardBus interrupts to PCI
[   35.194906] yenta_cardbus 0001:10:13.0: TI: mfunc 0x00001002, devctl 0x60
[   35.304202] yenta_cardbus 0001:10:13.0: ISA IRQ mask 0x0000, PCI irq 53
[   35.304211] yenta_cardbus 0001:10:13.0: Socket status: 30000007
[   35.304225] yenta_cardbus 0001:10:13.0: pcmcia: parent PCI bridge I/O window: 0x0 - 0x7fffff
[   35.304233] yenta_cardbus 0001:10:13.0: pcmcia: parent PCI bridge Memory window: 0xf3000000 - 0xf3ffffff
[   35.304239] yenta_cardbus 0001:10:13.0: pcmcia: parent PCI bridge Memory window: 0x80000000 - 0xafffffff
[   35.424287] Bluetooth: L2CAP ver 2.13
[   35.424294] Bluetooth: L2CAP socket layer initialized
[   35.580733] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   35.580741] Bluetooth: BNEP filters: protocol multicast
[   35.800633] Bridge firewalling registered
[   35.844930] Bluetooth: SCO (Voice Link) ver 0.6
[   35.844938] Bluetooth: SCO socket layer initialized
[   35.875682] agpgart-uninorth 0000:00:0b.0: putting AGP V2 device into 4x mode
[   35.875696] radeonfb 0000:00:10.0: putting AGP V2 device into 4x mode
[   36.129620] Bluetooth: RFCOMM TTY layer initialized
[   36.129631] Bluetooth: RFCOMM socket layer initialized
[   36.129636] Bluetooth: RFCOMM ver 1.11
[   36.396927] [drm] Setting GART location based on new memory map
[   36.396945] [drm] Loading R300 Microcode
[   36.396999] [drm] Num pipes: 1
[   36.397012] [drm] writeback test succeeded in 1 usecs
[   36.747527] b43legacy-phy0: Broadcom 4306 WLAN found
[   36.774219] b43legacy-phy0 debug: Found PHY: Analog 1, Type 2, Revision 1
[   36.774249] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[   36.804225] b43legacy-phy0 debug: Radio initialized
[   36.892526] phy0: Selected rate control algorithm 'minstrel'
[   36.893709] Broadcom 43xx-legacy driver loaded [ Features: PLID, Firmware-ID: FW10 ]
[   37.276171] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw
[   37.371801] b43legacy ssb0:0: firmware: requesting b43legacy/pcm4.fw
[   37.468110] b43legacy ssb0:0: firmware: requesting b43legacy/b0g0initvals2.fw
[   37.594582] irq: irq 30 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 30
[   37.594621] irq: irq 1 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 21
[   37.594641] irq: irq 2 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 31
[   37.612180] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[   37.676705] b43legacy-phy0 debug: Chip initialized
[   37.677158] b43legacy-phy0 debug: 30-bit DMA initialized
[   37.677383] Registered led device: b43legacy-phy0::tx
[   37.677427] Registered led device: b43legacy-phy0::rx
[   37.677459] Registered led device: b43legacy-phy0::radio
[   37.677509] b43legacy-phy0 debug: Wireless interface started
[   37.677741] b43legacy-phy0 debug: Adding Interface type 2
[   37.701403] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   37.771640] snd-aoa-fabric-layout: Using direct GPIOs
[   37.771766] irq: irq 61 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 61
[   37.771781] irq: irq 50 on host /pci@f2000000/mac-io@17/interrupt-controller@40000 mapped to virtual irq 50
[   37.996968] snd-aoa-codec-tas: found 'deq' node
[   37.997032] snd-aoa-fabric-layout: can use this codec
[   38.064336] snd-aoa-codec-tas: tas found, addr 0x35 on /pci@f2000000/mac-io@17/i2c@18000/deq@6a
[   38.319412] snd: can't request rsrc  0 (Sound Control: 0x0000000080010000:0000000080010fff)
[   38.533348] apm_emu: PMU APM Emulation initialized.
[   38.780834] adt746x: version 1 (supported)
[   38.780845] adt746x: Thermostat bus: 1, address: 0x2e, limit_adjust: 0, fan_speed: -1
[   38.780851] sensor 0: CPU/INTREPID BOTTOMSIDE
[   38.780856] sensor 1: CPU BOTTOMSIDE
[   38.780859] sensor 2: PWR SUPPLY BOTTOMSIDE
[   38.789212] adt746x: ADT7460 initializing
[   38.799553] adt746x: Lowering max temperatures from 81, 80, 87 to 70, 50, 70
[   39.628393] lp: driver loaded but no devices found
[   39.798453] ppdev: user-space parallel port driver
[   39.919860] input: Mouseemu virtual keyboard as /devices/virtual/input/input7
[   39.925392] input: Mouseemu virtual mouse as /devices/virtual/input/input8
[   89.712231] wlan0: authenticate with AP 00:90:d0:ee:96:63
[   89.713776] wlan0: authenticated
[   89.713781] wlan0: associate with AP 00:90:d0:ee:96:63
[   89.715916] wlan0: RX AssocResp from 00:90:d0:ee:96:63 (capab=0x401 status=0 aid=3)
[   89.715923] wlan0: associated
[   89.725016] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  100.344167] wlan0: no IPv6 routers present
[  106.086171] ondemand governor failed, too long transition latency of HW, fallback to performance governor

```

---

### Post by Vaflejens on 2009-11-01
Hi, I just installed 9.10 on my PowerBook G4 as well. I experience the same problems. However I managed to fix the fan issue by activating the therm_adt746x module. Just modprobe it to see if it works. If it does, you can add it to /etc/modules. 

I'm currently looking in to the other problem. The problem has to do with Power Manager, it seems. Because "cat /proc/pmu/battery_0" lists various information about the battery just fine.

edit: it seems that the problem has to do with devicekit-power. "devkit-power -d" in the terminal reports that the computer is not running on battery power.

---

### Post by heliogabalus on 2009-11-01
thanks for the tips. I did modprobe that one but the fan is still in overdrive. 
as for the rest about the battery, I confirm absolutely what you said, and get the same results!

edit: after some testing, I realized the module was being loaded already, so I tried out some options and found a way of quieting the fan. I replaced the line
```
therm_adt746x
```
with 
```
therm_adt746x limit_adjust=-15
```
in /etc/modules. thanks for that tip!

thing is, not sure if this is going to heat it up too much. so far so good! I'll report if the chip burns out!

edit2: yup, I confirm. the best is just to suck it up! I messed around with the fan speeds only to get my CPU to overheat. not sure how to get it back to the old days (silent but would speed up when it's too hot). now it seems to be more nervous (multiple speeds and very variable all the time) and never goes back to being completely silent. maybe it's good old lint. anyway, these two remain unsolved.

---

### Post by cpthuk on 2009-12-12
This has been recognized as a serious bug and fixed. I hope kernel module will be updated ASAP.

[http://www.gossamer-threads.com/lists/linux/kernel/1160406](http://www.gossamer-threads.com/lists/linux/kernel/1160406)

Bye,
Diego

---

### Post by heliogabalus on 2009-12-12
good news! thanks for that info!

---

### Post by 0graham0 on 2009-12-30
Hi,

I think if you add pmu_battery to /etc/modules you will get the battery status.

---

### Post by heliogabalus on 2009-12-30
yup, worked! still no luck with the fan though.

---

### Post by WindChild on 2010-02-09
The fan speed issue is a bug in the therm_adt746x module. For details See:
[http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.31.y.git;a=commit;h=0b1b72ba20a7d73136f57bb57ff8e2f3f79e62ad](http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.31.y.git;a=commit;h=0b1b72ba20a7d73136f57bb57ff8e2f3f79e62ad)

On my system, compiling a new therm_adt746x from the fixed source resolved all my issues with the fan speed.  Kernels newer than 2.6.31.9 have the fix already included.

---

### Post by PBG4 on 2010-03-02
Hi,
Complete newbie here insofar as Linux is concerned. I just installed Ubuntu 9.10 onto my 1Ghz PowerBook G4 - just out of curiosity and to see if I could get a faster user experience.
Everything seems to be working fine except the fan, which is running at full speed.
As I installed only yesterday, I would have expected the fix mentioned in the previous post to have been included in that install, however, not so.
How do I implement the fix? As I say, I'm a newbie, so please be gentle.
I don't mind breaking stuff. I have all the original install discs for Mac OS so can always go back to that.
Cheers
Allen

---

### Post by rocheleaud on 2010-03-14
Same thing for me ... ( just installed 9.10 on my old 12 inch ) . Fan run 100% all the time . Will try to download and compile new version of the module . Thanks . I have the  kernel 2.6.31.19 . wich is way newer than 2.6.31.9 .

---

### Post by spedl on 2010-04-01
Same problem here as well.  My fan is on overdrive and the wireless device claims to not be ready.  Just getting started so I'm not even sure how to try that thermal moderator trick but crashing the whole computer isn't a big issue.

Thanks in advance,

Jacob

---

