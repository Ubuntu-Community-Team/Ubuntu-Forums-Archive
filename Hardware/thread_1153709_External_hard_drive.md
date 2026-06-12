---
title: "External hard drive"
date: 2009-05-09
forum: Hardware
---

### Post by noelc on 2009-05-09
I,m running Ubuntu 8.1 and for some reason my PC is not seeing my external hardrive.
It sees the USB drives but when I open I get the unable to mount location no media in drive. " but there is ?


Can anyone help?

---

### Post by x33a on 2009-05-09
please, post a screenshot of the error.

and, post the output of
```
sudo fdisk -l
```

---

### Post by Ber P on 2009-05-09
A screen dump of *dmesg* and *lsusb* might also give some useful information

---

### Post by noelc on 2009-05-10
OK Thanks dumps below

f disk report

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6589b897

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18701   150215751   83  Linux
/dev/sda2           18702       19457     6072570    5  Extended
/dev/sda5           18702       19457     6072538+  82  Linux swap / Solaris




dmesg report 

[    0.000000] Kernel command line: root=UUID=df8c5718-dcba-4af2-9914-38b8e07afae6 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PMTIMER calibration value
[    0.000000] Detected 2999.609 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 2062740k/2096384k available (2576k kernel code, 32364k reserved, 1164k data, 424k init, 1178880k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ad000 - 0xc0517000   ( 424 kB)
[    0.004000]       .data : 0xc03843ea - 0xc04a7680   (1164 kB)
[    0.004000]       .text : 0xc0100000 - 0xc03843ea   (2576 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=128, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004016] Calibrating delay loop (skipped), value calculated using timer frequency.. 5999.21 BogoMIPS (lpj=11998436)
[    0.004040] Security Framework initialized
[    0.004050] SELinux:  Disabled at boot.
[    0.004078] AppArmor: AppArmor initialized
[    0.004094] Mount-cache hash table entries: 512
[    0.004325] Initializing cgroup subsys ns
[    0.004331] Initializing cgroup subsys cpuacct
[    0.004335] Initializing cgroup subsys memory
[    0.004359] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.004363] CPU: L2 cache: 1024K
[    0.004366] CPU: Physical Processor ID: 0
[    0.004371] using mwait in idle threads.
[    0.004385] Checking 'hlt' instruction... OK.
[    0.022645] ACPI: Core revision 20080609
[    0.025224] ACPI: Checking initramfs for custom DSDT
[    0.348580] ENABLING IO-APIC IRQs
[    0.348756] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.388448] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 01
[    0.392024] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 5999.74 BogoMIPS (lpj=11999495)
[    0.004000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.004000] CPU: L2 cache: 1024K
[    0.004000] CPU: Physical Processor ID: 0
[    0.476429] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 01
[    0.476456] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.480063] Brought up 2 CPUs
[    0.480069] Total of 2 processors activated (11998.96 BogoMIPS).
[    0.480093] CPU0 attaching sched-domain:
[    0.480097]  domain 0: span 0-1 level SIBLING
[    0.480100]   groups: 0 1
[    0.480109] CPU1 attaching sched-domain:
[    0.480111]  domain 0: span 0-1 level SIBLING
[    0.480114]   groups: 1 0
[    0.480216] net_namespace: 840 bytes
[    0.480216] Booting paravirtualized kernel on bare hardware
[    0.480401] Time: 10:17:51  Date: 05/10/09
[    0.480440] NET: Registered protocol family 16
[    0.480473] EISA bus registered
[    0.480473] ACPI: bus type pci registered
[    0.480473] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=2
[    0.480473] PCI: Using configuration type 1 for base access
[    0.484631] ACPI: EC: Look up EC in DSDT
[    0.494708] ACPI: Interpreter enabled
[    0.494714] ACPI: (supports S0 S1 S3 S4 S5)
[    0.494741] ACPI: Using IOAPIC for interrupt routing
[    0.504229] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.504229] PCI: 0000:00:00.0 reg 10 32bit mmio: [f8000000, fbffffff]
[    0.504229] PCI: 0000:00:1d.0 reg 20 io port: [e000, e01f]
[    0.504272] PCI: 0000:00:1d.1 reg 20 io port: [e400, e41f]
[    0.504327] PCI: 0000:00:1d.2 reg 20 io port: [e800, e81f]
[    0.504381] PCI: 0000:00:1d.3 reg 20 io port: [ec00, ec1f]
[    0.504444] PCI: 0000:00:1d.7 reg 10 32bit mmio: [ff27fc00, ff27ffff]
[    0.504501] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.504507] pci 0000:00:1d.7: PME# disabled
[    0.504591] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.504598] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[    0.504603] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH4 GPIO
[    0.504624] PCI: 0000:00:1f.1 reg 10 io port: [0, 7]
[    0.504632] PCI: 0000:00:1f.1 reg 14 io port: [0, 3]
[    0.504639] PCI: 0000:00:1f.1 reg 18 io port: [0, 7]
[    0.504647] PCI: 0000:00:1f.1 reg 1c io port: [0, 3]
[    0.504654] PCI: 0000:00:1f.1 reg 20 io port: [fc00, fc0f]
[    0.504662] PCI: 0000:00:1f.1 reg 24 32bit mmio: [0, 3ff]
[    0.504714] PCI: 0000:00:1f.3 reg 20 io port: [400, 41f]
[    0.504763] PCI: 0000:00:1f.5 reg 10 io port: [d800, d8ff]
[    0.504770] PCI: 0000:00:1f.5 reg 14 io port: [dc00, dc3f]
[    0.504778] PCI: 0000:00:1f.5 reg 18 32bit mmio: [ff27f800, ff27f9ff]
[    0.504785] PCI: 0000:00:1f.5 reg 1c 32bit mmio: [ff27f400, ff27f4ff]
[    0.504814] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.504819] pci 0000:00:1f.5: PME# disabled
[    0.504858] PCI: 0000:01:00.0 reg 10 32bit mmio: [e0000000, efffffff]
[    0.504867] PCI: 0000:01:00.0 reg 14 io port: [a800, a8ff]
[    0.504874] PCI: 0000:01:00.0 reg 18 32bit mmio: [ff0f0000, ff0fffff]
[    0.504892] PCI: 0000:01:00.0 reg 30 32bit mmio: [ff0c0000, ff0dffff]
[    0.504910] pci 0000:01:00.0: supports D1
[    0.504912] pci 0000:01:00.0: supports D2
[    0.504937] PCI: 0000:01:00.1 reg 10 32bit mmio: [d0000000, dfffffff]
[    0.504944] PCI: 0000:01:00.1 reg 14 32bit mmio: [ff0e0000, ff0effff]
[    0.504976] pci 0000:01:00.1: supports D1
[    0.504978] pci 0000:01:00.1: supports D2
[    0.505021] PCI: bridge 0000:00:01.0 io port: [a000, afff]
[    0.505025] PCI: bridge 0000:00:01.0 32bit mmio: [ff000000, ff0fffff]
[    0.505030] PCI: bridge 0000:00:01.0 32bit mmio pref: [b7f00000, f7efffff]
[    0.505073] PCI: 0000:02:05.0 reg 10 io port: [b800, b8ff]
[    0.505081] PCI: 0000:02:05.0 reg 14 32bit mmio: [ff1ffc00, ff1ffcff]
[    0.505119] pci 0000:02:05.0: supports D1
[    0.505122] pci 0000:02:05.0: supports D2
[    0.505124] pci 0000:02:05.0: PME# supported from D1 D2 D3hot D3cold
[    0.505129] pci 0000:02:05.0: PME# disabled
[    0.505164] pci 0000:00:1e.0: transparent bridge
[    0.505169] PCI: bridge 0000:00:1e.0 io port: [b000, bfff]
[    0.505174] PCI: bridge 0000:00:1e.0 32bit mmio: [ff100000, ff1fffff]
[    0.505191] bus 00 -> node 0
[    0.505201] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.505443] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.508392] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.508392] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.508560] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.508737] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.508911] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.512126] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.512302] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.512477] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.512563] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - D5, should be C8 [20080609]
[    0.512563] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.512563] pnp: PnP ACPI init
[    0.512563] ACPI: bus type pnp registered
[    0.520624] pnp: PnP ACPI: found 14 devices
[    0.520624] ACPI: ACPI bus type pnp unregistered
[    0.520624] PnPBIOS: Disabled by ACPI PNP
[    0.520624] PCI: Using ACPI for IRQ routing
[    0.528047] NET: Registered protocol family 8
[    0.528051] NET: Registered protocol family 20
[    0.528076] NetLabel: Initializing
[    0.528076] NetLabel:  domain hash size = 128
[    0.528076] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.528084] NetLabel:  unlabeled traffic allowed by default
[    0.528168] hpet clockevent registered
[    0.528174] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.528181] hpet0: 3 64-bit timers, 14318180 Hz
[    0.530533] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.530536]    actual entries 65620
[    0.530694] AppArmor: AppArmor Filesystem Enabled
[    0.530714] ACPI: RTC can wake from S4
[    0.536074] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[    0.536079] system 00:07: ioport range 0x800-0x87f has been reserved
[    0.536082] system 00:07: ioport range 0x480-0x4bf has been reserved
[    0.536086] system 00:07: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.536091] system 00:07: iomem range 0xff380000-0xffefffff could not be reserved
[    0.536099] system 00:08: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.536103] system 00:08: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.536114] system 00:0c: ioport range 0x680-0x6ff has been reserved
[    0.536118] system 00:0c: ioport range 0x295-0x296 has been reserved
[    0.536126] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[    0.536130] system 00:0d: iomem range 0xc0000-0xdffff could not be reserved
[    0.536133] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[    0.536137] system 00:0d: iomem range 0x100000-0x7fffffff could not be reserved
[    0.536140] system 00:0d: iomem range 0xfff00000-0xffffffff could not be reserved
[    0.571691] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.571696] pci 0000:00:01.0:   IO window: 0xa000-0xafff
[    0.571702] pci 0000:00:01.0:   MEM window: 0xff000000-0xff0fffff
[    0.571707] pci 0000:00:01.0:   PREFETCH window: 0x000000b7f00000-0x000000f7efffff
[    0.571714] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.571718] pci 0000:00:1e.0:   IO window: 0xb000-0xbfff
[    0.571725] pci 0000:00:1e.0:   MEM window: 0xff100000-0xff1fffff
[    0.571730] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.571751] pci 0000:00:1e.0: setting latency timer to 64
[    0.571757] bus: 00 index 0 io port: [0, ffff]
[    0.571760] bus: 00 index 1 mmio: [0, ffffffff]
[    0.571762] bus: 01 index 0 io port: [a000, afff]
[    0.571765] bus: 01 index 1 mmio: [ff000000, ff0fffff]
[    0.571767] bus: 01 index 2 mmio: [b7f00000, f7efffff]
[    0.571770] bus: 01 index 3 mmio: [0, 0]
[    0.571773] bus: 02 index 0 io port: [b000, bfff]
[    0.571775] bus: 02 index 1 mmio: [ff100000, ff1fffff]
[    0.571777] bus: 02 index 2 mmio: [0, 0]
[    0.571780] bus: 02 index 3 io port: [0, ffff]
[    0.571782] bus: 02 index 4 mmio: [0, ffffffff]
[    0.571796] NET: Registered protocol family 2
[    0.584121] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.584505] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.585006] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.585317] TCP: Hash tables configured (established 131072 bind 65536)
[    0.585321] TCP reno registered
[    0.592176] NET: Registered protocol family 1
[    0.592349] checking if image is initramfs... it is
[    1.028525] Switched to high resolution mode on CPU 1
[    1.032072] Switched to high resolution mode on CPU 0
[    1.268734] Freeing initrd memory: 8015k freed
[    1.270520] audit: initializing netlink socket (disabled)
[    1.270545] type=2000 audit(1241950671.268:1): initialized
[    1.276370] highmem bounce pool size: 64 pages
[    1.276380] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.280323] VFS: Disk quotas dquot_6.5.1
[    1.280456] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.280615] msgmni has been set to 1743
[    1.280800] io scheduler noop registered
[    1.280803] io scheduler anticipatory registered
[    1.280806] io scheduler deadline registered
[    1.280823] io scheduler cfq registered (default)
[    1.280928] pci 0000:01:00.0: Boot video device
[    1.281516] isapnp: Scanning for PnP cards...
[    1.633222] isapnp: No Plug & Play device found
[    1.694086] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.694240] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.695350] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.698495] brd: module loaded
[    1.698612] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.698816] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.701361] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.701371] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.704207] mice: PS/2 mouse device common for all mice
[    1.704442] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.704470] rtc0: alarms up to one month, hpet irqs
[    1.704711] EISA: Probing bus 0 at eisa.0
[    1.704751] EISA: Detected 0 cards.
[    1.704755] cpuidle: using governor ladder
[    1.704758] cpuidle: using governor menu
[    1.705524] TCP cubic registered
[    1.705562] Using IPI No-Shortcut mode
[    1.705905] registered taskstats version 1
[    1.706057]   Magic number: 9:522:274
[    1.706084] tty ttyy2: hash matches
[    1.706161] tty tty11: hash matches
[    1.706208] rtc_cmos 00:02: setting system clock to 2009-05-10 10:17:53 UTC (1241950673)
[    1.706213] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.706215] EDD information not available.
[    1.706540] Freeing unused kernel memory: 424k freed
[    1.706602] Write protecting the kernel text: 2580k
[    1.706641] Write protecting the kernel read-only data: 940k
[    1.723884] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.900179] fuse init (API version 7.9)
[    2.024069] processor ACPI0007:00: registered as cooling_device0
[    2.024086] ACPI: Processor [CPU1] (supports 8 throttling states)
[    2.028043] processor ACPI0007:01: registered as cooling_device1
[    2.305737] usbcore: registered new interface driver usbfs
[    2.305777] usbcore: registered new interface driver hub
[    2.317639] usbcore: registered new device driver usb
[    2.322781] USB Universal Host Controller Interface driver v3.0
[    2.322852] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.322865] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.322871] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.322938] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    2.322975] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000e000
[    2.323229] usb usb1: configuration #1 chosen from 1 choice
[    2.323278] hub 1-0:1.0: USB hub found
[    2.323290] hub 1-0:1.0: 2 ports detected
[    2.407766] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
[    2.532422] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.532439] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.532446] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.532511] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    2.532554] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e400
[    2.532738] usb usb2: configuration #1 chosen from 1 choice
[    2.532796] hub 2-0:1.0: USB hub found
[    2.532811] hub 2-0:1.0: 2 ports detected
[    2.640424] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.640441] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.640448] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.640497] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    2.640542] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e800
[    2.640722] usb usb3: configuration #1 chosen from 1 choice
[    2.640774] hub 3-0:1.0: USB hub found
[    2.640787] hub 3-0:1.0: 2 ports detected
[    2.648050] usb 1-2: new full speed USB device using uhci_hcd and address 2
[    2.748082] No dock devices found.
[    2.748487] uhci_hcd 0000:00:1d.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.748504] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    2.748511] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    2.748562] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    2.748597] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000ec00
[    2.748796] usb usb4: configuration #1 chosen from 1 choice
[    2.748858] hub 4-0:1.0: USB hub found
[    2.748875] hub 4-0:1.0: 2 ports detected
[    2.781684] SCSI subsystem initialized
[    2.816632] libata version 3.00 loaded.
[    2.852236] usb 1-2: configuration #1 chosen from 1 choice
[    2.948645] 8139too Fast Ethernet driver 0.9.28
[    2.960553] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    2.960586] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.960594] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.960661] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    2.964593] ehci_hcd 0000:00:1d.7: debug port 1
[    2.964606] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    2.964641] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xff27fc00
[    3.072042] usb 4-1: new full speed USB device using uhci_hcd and address 2
[    3.080540] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.080850] usb usb5: configuration #1 chosen from 1 choice
[    3.080919] hub 5-0:1.0: USB hub found
[    3.080937] hub 5-0:1.0: 8 ports detected
[    3.140446] hub 4-0:1.0: unable to enumerate USB device on port 1
[    3.140523] usb 1-2: USB disconnect, address 2
[    3.299109] 8139too 0000:02:05.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    3.300154] eth0: RealTek RTL8139 at 0xb800, 00:19:66:2c:88:07, IRQ 22
[    3.300160] eth0:  Identified 8139 chip type 'RTL-8101'
[    3.306951] ata_piix 0000:00:1f.1: version 2.12
[    3.306976] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.307061] ata_piix 0000:00:1f.1: setting latency timer to 64
[    3.307227] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    3.308012] scsi0 : ata_piix
[    3.308265] scsi1 : ata_piix
[    3.312781] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[    3.312789] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[    3.412540] usb 5-2: new high speed USB device using ehci_hcd and address 2
[    3.478217] ata1.00: ATA-6: WDC WD1600BB-00GUA0, 08.02D08, max UDMA/100
[    3.478225] ata1.00: 312581808 sectors, multi 16: LBA48 
[    3.494134] ata1.00: configured for UDMA/100
[    3.545802] usb 5-2: configuration #1 chosen from 1 choice
[    3.656670] usb 5-7: new high speed USB device using ehci_hcd and address 3
[    3.798632] usb 5-7: configuration #1 chosen from 1 choice
[    3.800260] usbcore: registered new interface driver libusual
[    3.817091] Initializing USB Mass Storage driver...
[    3.818223] scsi2 : SCSI emulation for USB Mass Storage devices
[    3.820104] scsi3 : SCSI emulation for USB Mass Storage devices
[    3.820268] usb-storage: device found at 2
[    3.820274] usb-storage: waiting for device to settle before scanning
[    3.820327] usbcore: registered new interface driver usb-storage
[    3.820335] USB Mass Storage support registered.
[    3.820505] usb-storage: device found at 3
[    3.820510] usb-storage: waiting for device to settle before scanning
[    4.448314] ata2.00: ATAPI: HL-DT-ST DVDRAM GSA-4163B, A102, max UDMA/33
[    4.448349] ata2.01: ATAPI: ATAPI 16X DVDROM, OM   VA1, max UDMA/33
[    4.464243] ata2.00: configured for UDMA/33
[    4.480239] ata2.01: configured for UDMA/33
[    4.480410] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600BB-00G 08.0 PQ: 0 ANSI: 5
[    4.480667] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    4.484140] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-4163B A102 PQ: 0 ANSI: 5
[    4.484295] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    4.485187] scsi 1:0:1:0: CD-ROM            ATAPI 16 X DVDROM   VA100 A100 PQ: 0 ANSI: 5
[    4.485340] scsi 1:0:1:0: Attached scsi generic sg2 type 5
[    4.524990] Driver 'sd' needs updating - please use bus_type methods
[    4.528573] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    4.528639] sd 0:0:0:0: [sda] Write Protect is off
[    4.528645] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.528707] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.528851] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    4.528887] sd 0:0:0:0: [sda] Write Protect is off
[    4.528894] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.528955] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.528966]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    4.550650]  sda1 sda2 < sda5 >
[    4.569128] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.579209] sr0: scsi3-mmc drive: 78x/78x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.579218] Uniform CD-ROM driver Revision: 3.20
[    4.579400] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.582906] sr1: scsi3-mmc drive: 12x/48x cd/rw xa/form2 cdda tray
[    4.583078] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    4.857472] PM: Starting manual resume from disk
[    4.857477] PM: Resume from partition 8:5
[    4.857480] PM: Checking hibernation image.
[    4.857652] PM: Resume from disk failed.
[    4.921026] kjournald starting.  Commit interval 5 seconds
[    4.921038] EXT3-fs: mounted filesystem with ordered data mode.
[    8.820263] usb-storage: device scan complete
[    8.820282] usb-storage: device scan complete
[    8.820724] scsi 2:0:0:0: Direct-Access     HP       Photosmart C3180 1.00 PQ: 0 ANSI: 2
[    8.822215] scsi 3:0:0:0: Direct-Access     USB2.0   CF Card       CF 1.6E PQ: 0 ANSI: 0 CCS
[    8.823962] scsi 3:0:0:1: Direct-Access     USB2.0   MULTI Card    MS 1.6E PQ: 0 ANSI: 0 CCS
[    8.825691] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[    8.825879] sd 3:0:0:0: Attached scsi generic sg3 type 0
[    8.826903] sd 3:0:0:1: [sdc] Attached SCSI removable disk
[    8.826977] sd 3:0:0:1: Attached scsi generic sg4 type 0
[    8.827780] sd 2:0:0:0: [sdd] Attached SCSI removable disk
[    8.827858] sd 2:0:0:0: Attached scsi generic sg5 type 0
[   10.882076] udevd version 124 started
[   11.506718] Linux agpgart interface v0.103
[   11.611782] agpgart-intel 0000:00:00.0: Intel 865 Chipset
[   11.615469] agpgart-intel 0000:00:00.0: AGP aperture is 64M @ 0xf8000000
[   11.736675] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   11.829734] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.938189] intel_rng: FWH not detected
[   12.072941] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   12.169856] iTCO_vendor_support: vendor-support=0
[   12.380693] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   12.380826] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x0860)
[   12.381009] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   12.435085] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   12.468556] ACPI: Power Button (FF) [PWRF]
[   12.468750] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
[   12.484538] ACPI: Power Button (CM) [PWRB]
[   13.960077] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   13.984272] usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x03F0 pid 0x5611
[   13.984317] usbcore: registered new interface driver usblp
[   13.994935] parport_pc 00:06: reported by Plug and Play ACPI
[   13.995039] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   14.684853] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   14.684889] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   15.008554] intel8x0_measure_ac97_clock: measured 55639 usecs
[   15.008560] intel8x0: clocking to 48000
[   17.790369] lp0: using parport0 (interrupt-driven).
[   17.988300] Adding 6072528k swap on /dev/sda5.  Priority:-1 extents:1 across:6072528k
[   18.559948] EXT3 FS on sda1, internal journal
[   19.832307] type=1505 audit(1241950691.174:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4136
[   20.026711] type=1505 audit(1241950691.366:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4141
[   20.026973] type=1505 audit(1241950691.366:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4141
[   20.223933] ip_tables: (C) 2000-2006 Netfilter Core Team
[   20.980191] ACPI: WMI: Mapper loaded
[   22.035755] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   22.114972] apm: BIOS version 1.2 Flags 0x02 (Driver version 1.16ac)
[   22.114980] apm: disabled - APM is not SMP safe.
[   22.394892] ppdev: user-space parallel port driver
[   26.030791] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   26.030799] vboxdrv: Successfully done.
[   26.030803] vboxdrv: Found 2 processor cores.
[   26.031052] vboxdrv: fAsync=0 offMin=0x599 offMax=0x300c
[   26.031144] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   26.031150] vboxdrv: Successfully loaded version 2.2.2 (interface 0x000a0009).
[   28.647319] Bluetooth: Core ver 2.13
[   28.648553] NET: Registered protocol family 31
[   28.648562] Bluetooth: HCI device and connection manager initialized
[   28.648571] Bluetooth: HCI socket layer initialized
[   28.769649] Bluetooth: L2CAP ver 2.11
[   28.769657] Bluetooth: L2CAP socket layer initialized
[   28.808174] Bluetooth: SCO (Voice Link) ver 0.6
[   28.808181] Bluetooth: SCO socket layer initialized
[   28.824224] Bluetooth: RFCOMM socket layer initialized
[   28.824251] Bluetooth: RFCOMM TTY layer initialized
[   28.824256] Bluetooth: RFCOMM ver 1.10
[   28.907105] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   28.907113] Bluetooth: BNEP filters: protocol multicast
[   29.035865] Bridge firewalling registered
[   32.159838] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   32.216628] [fglrx] Maximum main memory to use for locked dma buffers: 1896 MBytes.
[   32.217129] [fglrx]   vendor: 1002 device: 4153 count: 1
[   32.218662] [fglrx] ioport: bar 1, base 0xa800, size: 0x100
[   32.218686] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   32.220473] [fglrx] Driver built-in PAT support is enabled successfully
[   32.220554] [fglrx] module loaded - fglrx 8.59.2 [Mar 13 2009] with 1 minors
[   32.238673] [fglrx] AGP detected, AgpState   = 0x1f004a1b (hardware caps of chipset)
[   32.238690] [fglrx] [agp] enabling AGP with mode=0x1f004b1a
[   32.238697] agpgart-intel 0000:00:00.0: AGP 3.0 bridge
[   32.238724] agpgart-intel 0000:00:00.0: putting AGP V3 device into 8x mode
[   32.238772] fglrx_pci 0000:01:00.0: putting AGP V3 device into 8x mode
[   32.238797] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[   33.013154] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   33.306851] NET: Registered protocol family 17
[   35.434058] [fglrx] Setup AGP aperture
[   35.434659] [fglrx] GART Table is not in FRAME_BUFFER range 
[   35.443356] [fglrx] Firegl kernel thread PID: 5538
[   35.445923] [fglrx] Reserved FB block: Shared offset:0, size:40000 
[   35.445938] [fglrx] Reserved FB block: Unshared offset:ffff000, size:1000 
[   37.079346] NET: Registered protocol family 10
[   37.081999] lo: Disabled Privacy Extensions
[   47.908014] eth0: no IPv6 routers present
[   58.370864] UDF-fs: Partition marked readonly; forcing readonly mount
[   58.403790] UDF-fs INFO UDF: Mounting volume 'WARLU_WAY', timestamp 2007/11/15 20:19 (1258)
[  139.153857] ppdev0: registered pardevice
[  139.192270] ppdev0: unregistered pardevice
[  141.535646] ppdev0: registered pardevice
[  141.584381] ppdev0: unregistered pardevice
[  141.652160] ppdev0: registered pardevice
[  141.700048] ppdev0: unregistered pardevice

isusb report

Bus 005 Device 003: ID 0dda:2005 Integrated Circuit Solution, Inc. Datalux DLX-1611 16in1 Card Reader
Bus 005 Device 002: ID 03f0:5611 Hewlett-Packard PhotoSmart C3180
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

