---
title: "Ubuntu 8.10, IrDa not working"
date: 2008-11-09
forum: Hardware
---

### Post by RazTaz on 2008-11-09
Hello.

I have a Fujistu-Siemens Lifebook C 1020 on which I recently moved from Xubuntu Hardy to Ubuntu 8.10.

Previously my IrDa was working perfectly after using these settings: [https://help.ubuntu.com/community/IrdaHowto](https://help.ubuntu.com/community/IrdaHowto)

Now, I simply can't make it work. 

Yes, the IR port is enabled in BIOS and yes, it's assigned COM2 (2F8)

After I followed exactly the steps in the link above, dmesg gives me the following result:

...
[   19.501953] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[   19.501993] nsc-ircc, chip->init
[   19.502004] nsc-ircc, Found chip at base=0x02e
[   19.502030] nsc-ircc, driver loaded (Dag Brattli)
[   19.502047] nsc_ircc_open(), can't get iobase of 0x2f8
[   19.502076] nsc-ircc, Found chip at base=0x02e
[   19.502101] nsc-ircc, driver loaded (Dag Brattli)
[   19.502104] nsc_ircc_open(), can't get iobase of 0x2f8
[   19.502505] nsc-ircc 00:0c: disabled
[   20.326096] ttySHSF0 at I/O 0xe200 (irq = 10) is a Conexant HSF softmodem (PCI-1106:3068-10cf:118e)
[   20.831028] VIA 82xx Audio 0000:00:11.5: power state changed by ACPI to D0
[   20.831048] VIA 82xx Audio 0000:00:11.5: PCI INT C -> Link[LNKC] -> GSI 10 (level, low) -> IRQ 10
[   20.831204] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   22.852732] cs: IO port probe 0x100-0x3af: clean.
[   22.854598] cs: IO port probe 0x3e0-0x4ff: clean.
[   22.855395] cs: IO port probe 0x820-0x8ff: clean.
[   22.856193] cs: IO port probe 0xc00-0xcf7: clean.
[   22.857087] cs: IO port probe 0xa00-0xaff: clean.
[   22.887855] cs: IO port probe 0x100-0x3af: clean.
[   22.889776] cs: IO port probe 0x3e0-0x4ff: clean.
[   22.890572] cs: IO port probe 0x820-0x8ff: clean.
[   22.891253] cs: IO port probe 0xc00-0xcf7: clean.
[   22.892168] cs: IO port probe 0xa00-0xaff: clean.
[   23.759901] lp0: using parport0 (interrupt-driven).
[   23.867061] IrCOMM protocol (Dag Brattli)
[   24.187813] Adding 1646620k swap on /dev/sda5.  Priority:-1 extents:1 across:1646620k
[   24.984520] EXT3 FS on sda1, internal journal
[   26.418657] type=1505 audit(1226213042.884:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4093
[   26.668215] type=1505 audit(1226213043.132:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4098
[   26.668760] type=1505 audit(1226213043.136:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4098
[   26.933676] ip_tables: (C) 2000-2006 Netfilter Core Team
[   27.157928] ttyS1: LSR safety check engaged!
[   27.159162] ttyS1: LSR safety check engaged!
[   27.231707] pnp 00:0c: activated
[   27.235029] serial8250: too much work for irq3
[   27.257834] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[   27.257874] nsc-ircc, chip->init
[   27.257885] nsc-ircc, Found chip at base=0x02e
[   27.257911] nsc-ircc, driver loaded (Dag Brattli)
[   27.258408] IrDA: Registered device irda0
[   27.258411] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500
[   28.796276] ACPI: WMI: Mapper loaded
[   30.231320] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   30.742145] /dev/vmmon[4761]: Module vmmon: registered with major=10 minor=165
[   30.742171] /dev/vmmon[4761]: Initial HV check: anyNotCapable=1 anyUnlocked=0 anyEnabled=0 anyDisabled=0
[   30.742176] /dev/vmmon[4761]: Module vmmon: initialized
[   30.793675] /dev/vmci[4772]: VMCI: Driver initialized.
[   30.794454] /dev/vmci[4772]: Module vmci: registered with major=10 minor=60
[   30.794463] /dev/vmci[4772]: Module vmci: initialized
[   42.759740] /dev/vmnet: open called by PID 5329 (vmnet-dhcpd)
[   42.759763] /dev/vmnet: hub 1 does not exist, allocating memory.
[   42.759780] /dev/vmnet: port on hub 1 successfully opened
[   42.890276] /dev/vmnet: open called by PID 5333 (vmnet-netifup)
[   42.890311] /dev/vmnet: port on hub 1 successfully opened
[   42.935314] /dev/vmnet: open called by PID 5336 (vmnet-dhcpd)
[   42.935339] /dev/vmnet: hub 8 does not exist, allocating memory.
[   42.935358] /dev/vmnet: port on hub 8 successfully opened
[   43.039645] /dev/vmnet: open called by PID 5338 (vmnet-natd)
[   43.039680] /dev/vmnet: port on hub 8 successfully opened
[   43.111713] /dev/vmnet: open called by PID 5342 (vmnet-netifup)
[   43.111766] /dev/vmnet: port on hub 8 successfully opened
[   43.680990] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   43.681001] apm: overridden by ACPI.
[   43.927215] ppdev: user-space parallel port driver
[   44.856626] irlap_change_speed(), setting speed to 9600

...

More, cat /proc/net/irda/discovery is not able to detect anything, despite putting my Nokia 6610i with infrared reception activated in the range.

irdaping is not returning any response, either.

Lastly, I have to say that IrDA worked fine with Xubuntu Hardy, and I was able to use gnokii to access my phone. So I suspect it's an issue of Ubuntu 8.10.

Can anybody give me some help on what can I do to get my infrared port to work again?

Thank you kindly,
Razvan

---

### Post by bat12 on 2009-01-05
The same happens with my laptop (Clevo).As I switched to 8.10, irda stoped working. I tried the HOW TO above again I have:

```
sudo irdadump
15:10:53.671549 xid:cmd e089689d > ffffffff S=6 s=0 (14) 
15:10:53.759488 xid:cmd e089689d > ffffffff S=6 s=1 (14) 
15:10:53.847487 xid:cmd e089689d > ffffffff S=6 s=2 (14) 
15:10:53.935486 xid:cmd e089689d > ffffffff S=6 s=3 (14) 
15:10:54.023486 xid:cmd e089689d > ffffffff S=6 s=4 (14) 
15:10:54.111487 xid:cmd e089689d > ffffffff S=6 s=5 (14) 
15:10:54.199487 xid:cmd e089689d > ffffffff S=6 s=* ben-laptop hint=0400 [ Computer ] (27)
```

and when I put my phone near nothing changes.

Also:

```
cat /proc/net/irda/discovery
IrLMP: Discovery log:             
```

Here's my dmesg:

```
[    0.028026] Freeing SMP alternatives: 11k freed
[    0.028032] ACPI: Core revision 20080609
[    0.030489] ACPI: Checking initramfs for custom DSDT
[    0.368532] ACPI: setting ELCR to 0800 (from 0a20)
[    0.369913] weird, boot CPU (#0) not listedby the BIOS.
[    0.369916] SMP motherboard not detected.
[    0.369920] Local APIC not detected. Using dummy APIC emulation.
[    0.369922] SMP disabled
[    0.370000] Brought up 1 CPUs
[    0.370003] Total of 1 processors activated (5600.18 BogoMIPS).
[    0.370016] CPU0 attaching NULL sched-domain.
[    0.370292] net_namespace: 840 bytes
[    0.370304] Booting paravirtualized kernel on bare hardware
[    0.370541] Time: 16:14:38  Date: 01/05/09
[    0.370581] NET: Registered protocol family 16
[    0.370987] EISA bus registered
[    0.371014] ACPI: bus type pci registered
[    0.372538] PCI: PCI BIOS revision 2.10 entry at 0xfd9d8, last bus=1
[    0.372542] PCI: Using configuration type 1 for base access
[    0.374284] ACPI: EC: Look up EC in DSDT
[    0.378907] ACPI: Interpreter enabled
[    0.378915] ACPI: (supports S0 S3 S4 S5)
[    0.378929] ACPI: Using PIC for interrupt routing
[    0.385966] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.388158] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.388162] ACPI: EC: driver started in interrupt mode
[    0.388227] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.388320] PCI: 0000:00:00.0 reg 10 32bit mmio: [e8000000, ebffffff]
[    0.388448] pci 0000:00:02.0: Enabling SiS 96x SMBus
[    0.388489] PCI: 0000:00:02.1 reg 20 io port: [8100, 811f]
[    0.388535] PCI: 0000:00:02.3 reg 10 32bit mmio: [ec000000, ec000fff]
[    0.388568] PCI: 0000:00:02.3 reg 30 32bit mmio: [0, 1ffff]
[    0.388583] pci 0000:00:02.3: supports D1
[    0.388585] pci 0000:00:02.3: supports D2
[    0.388588] pci 0000:00:02.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.388593] pci 0000:00:02.3: PME# disabled
[    0.388612] PCI: 0000:00:02.5 reg 10 io port: [1f0, 1f7]
[    0.388618] PCI: 0000:00:02.5 reg 14 io port: [3f4, 3f7]
[    0.388625] PCI: 0000:00:02.5 reg 18 io port: [170, 177]
[    0.388632] PCI: 0000:00:02.5 reg 1c io port: [374, 377]
[    0.388639] PCI: 0000:00:02.5 reg 20 io port: [1000, 100f]
[    0.388684] PCI: 0000:00:02.6 reg 10 io port: [1400, 14ff]
[    0.388691] PCI: 0000:00:02.6 reg 14 io port: [1080, 10ff]
[    0.388730] pci 0000:00:02.6: supports D1
[    0.388731] pci 0000:00:02.6: supports D2
[    0.388734] pci 0000:00:02.6: PME# supported from D3hot D3cold
[    0.388738] pci 0000:00:02.6: PME# disabled
[    0.388770] PCI: 0000:00:02.7 reg 10 io port: [1c00, 1cff]
[    0.388777] PCI: 0000:00:02.7 reg 14 io port: [1800, 187f]
[    0.388816] pci 0000:00:02.7: supports D1
[    0.388818] pci 0000:00:02.7: supports D2
[    0.388820] pci 0000:00:02.7: PME# supported from D3hot D3cold
[    0.388824] pci 0000:00:02.7: PME# disabled
[    0.388842] PCI: 0000:00:03.0 reg 10 32bit mmio: [ec001000, ec001fff]
[    0.388892] PCI: 0000:00:03.1 reg 10 32bit mmio: [ec002000, ec002fff]
[    0.388942] PCI: 0000:00:03.2 reg 10 32bit mmio: [ec003000, ec003fff]
[    0.389003] PCI: 0000:00:03.3 reg 10 32bit mmio: [ec004000, ec004fff]
[    0.389045] pci 0000:00:03.3: PME# supported from D0 D3hot D3cold
[    0.389049] pci 0000:00:03.3: PME# disabled
[    0.389091] PCI: 0000:00:0a.0 reg 10 io port: [2000, 20ff]
[    0.389099] PCI: 0000:00:0a.0 reg 14 32bit mmio: [ec005000, ec0050ff]
[    0.389137] pci 0000:00:0a.0: supports D1
[    0.389139] pci 0000:00:0a.0: supports D2
[    0.389141] pci 0000:00:0a.0: PME# supported from D1 D2 D3hot D3cold
[    0.389146] pci 0000:00:0a.0: PME# disabled
[    0.389177] PCI: 0000:00:0c.0 reg 10 32bit mmio: [38020000, 38020fff]
[    0.389192] pci 0000:00:0c.0: supports D1
[    0.389194] pci 0000:00:0c.0: supports D2
[    0.389196] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.389201] pci 0000:00:0c.0: PME# disabled
[    0.389261] PCI: 0000:01:00.0 reg 10 32bit mmio: [f0000000, f7ffffff]
[    0.389268] PCI: 0000:01:00.0 reg 14 io port: [9000, 90ff]
[    0.389274] PCI: 0000:01:00.0 reg 18 32bit mmio: [ec100000, ec10ffff]
[    0.389292] PCI: 0000:01:00.0 reg 30 32bit mmio: [0, 1ffff]
[    0.389308] pci 0000:01:00.0: supports D1
[    0.389310] pci 0000:01:00.0: supports D2
[    0.389345] PCI: bridge 0000:00:01.0 io port: [9000, 9fff]
[    0.389350] PCI: bridge 0000:00:01.0 32bit mmio: [ec100000, ec1fffff]
[    0.389355] PCI: bridge 0000:00:01.0 32bit mmio pref: [f0000000, f7ffffff]
[    0.389380] bus 00 -> node 0
[    0.389390] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.399038] ACPI: PCI Interrupt Link [LNKA] (IRQs *11)
[    0.399180] ACPI: PCI Interrupt Link [LNKB] (IRQs *9)
[    0.399315] ACPI: PCI Interrupt Link [LNKC] (IRQs 5) *0, disabled.
[    0.399450] ACPI: PCI Interrupt Link [LNKD] (IRQs *11)
[    0.399616] ACPI: PCI Interrupt Link [LNKE] (IRQs *11)
[    0.399753] ACPI: PCI Interrupt Link [LNKF] (IRQs *9)
[    0.399887] ACPI: PCI Interrupt Link [LNKG] (IRQs *9)
[    0.400046] ACPI: PCI Interrupt Link [LNKH] (IRQs 9) *0, disabled.
[    0.400267] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.400318] pnp: PnP ACPI init
[    0.400331] ACPI: bus type pnp registered
[    0.407206] pnp: PnP ACPI: found 12 devices
[    0.407206] ACPI: ACPI bus type pnp unregistered
[    0.407206] PnPBIOS: Disabled by ACPI PNP
[    0.408182] PCI: Using ACPI for IRQ routing
[    0.408324] NET: Registered protocol family 8
[    0.408324] NET: Registered protocol family 20
[    0.408324] NetLabel: Initializing
[    0.408324] NetLabel:  domain hash size = 128
[    0.408324] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.408324] NetLabel:  unlabeled traffic allowed by default
[    0.408427] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.408430]    actual entries 65620
[    0.408589] AppArmor: AppArmor Filesystem Enabled
[    0.408622] system 00:04: ioport range 0x8000-0x808f has been reserved
[    0.408622] system 00:04: ioport range 0x8090-0x80ff has been reserved
[    0.408622] system 00:04: ioport range 0x8100-0x811f has been reserved
[    0.408622] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[    0.408622] system 00:04: ioport range 0xfe00-0xfe00 has been reserved
[    0.408622] system 00:04: iomem range 0xfec00000-0xfecfffff could not be reserved
[    0.408622] system 00:04: iomem range 0xfee00000-0xfeefffff could not be reserved
[    0.408622] system 00:04: iomem range 0xffc00000-0xffc00fff has been reserved
[    0.408622] system 00:04: iomem range 0xffe00000-0xffe00fff has been reserved
[    0.408622] system 00:04: iomem range 0xffe80000-0xffefffff has been reserved
[    0.444299] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.444304] pci 0000:00:01.0:   IO window: 0x9000-0x9fff
[    0.444310] pci 0000:00:01.0:   MEM window: 0xec100000-0xec1fffff
[    0.444316] pci 0000:00:01.0:   PREFETCH window: 0x000000f0000000-0x000000f7ffffff
[    0.444324] pci 0000:00:0c.0: CardBus bridge, secondary bus 0000:02
[    0.444326] pci 0000:00:0c.0:   IO window: 0x002400-0x0024ff
[    0.444331] pci 0000:00:0c.0:   IO window: 0x002800-0x0028ff
[    0.444336] pci 0000:00:0c.0:   PREFETCH window: 0x30000000-0x33ffffff
[    0.444341] pci 0000:00:0c.0:   MEM window: 0x34000000-0x37ffffff
[    0.444629] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5
[    0.444633] PCI: setting IRQ 5 as level-triggered
[    0.444638] pci 0000:00:0c.0: PCI INT A -> Link[LNKC] -> GSI 5 (level, low) -> IRQ 5
[    0.444644] bus: 00 index 0 io port: [0, ffff]
[    0.444647] bus: 00 index 1 mmio: [0, ffffffff]
[    0.444649] bus: 01 index 0 io port: [9000, 9fff]
[    0.444652] bus: 01 index 1 mmio: [ec100000, ec1fffff]
[    0.444654] bus: 01 index 2 mmio: [f0000000, f7ffffff]
[    0.444656] bus: 01 index 3 mmio: [0, 0]
[    0.444659] bus: 02 index 0 io port: [2400, 24ff]
[    0.444661] bus: 02 index 1 io port: [2800, 28ff]
[    0.444664] bus: 02 index 2 mmio: [30000000, 33ffffff]
[    0.444666] bus: 02 index 3 mmio: [34000000, 37ffffff]
[    0.444682] NET: Registered protocol family 2
[    0.444862] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.445140] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.445225] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.445305] TCP: Hash tables configured (established 16384 bind 16384)
[    0.445308] TCP reno registered
[    0.445412] NET: Registered protocol family 1
[    0.445567] checking if image is initramfs... it is
[    0.948081] Switched to high resolution mode on CPU 0
[    1.151484] Freeing initrd memory: 7950k freed
[    1.152292] audit: initializing netlink socket (disabled)
[    1.152316] type=2000 audit(1231172079.152:1): initialized
[    1.156954] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.159601] VFS: Disk quotas dquot_6.5.1
[    1.159725] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.159858] msgmni has been set to 999
[    1.160052] io scheduler noop registered
[    1.160056] io scheduler anticipatory registered
[    1.160059] io scheduler deadline registered
[    1.160077] io scheduler cfq registered (default)
[    1.592037] pci 0000:01:00.0: Boot video device
[    1.592485] isapnp: Scanning for PnP cards...
[    1.945969] isapnp: No Plug & Play device found
[    2.006135] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.006274] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.006471] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 8250
[    2.007454] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.007731] serial 0000:00:02.6: enabling device (0000 -> 0001)
[    2.007741] serial 0000:00:02.6: PCI INT C -> Link[LNKC] -> GSI 5 (level, low) -> IRQ 5
[    2.007748] serial 0000:00:02.6: PCI INT C disabled
[    2.009954] brd: module loaded
[    2.010044] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    2.010205] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.012445] i8042.c: Detected active multiplexing controller, rev 1.1.
[    2.013815] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.013821] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    2.013825] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    2.013827] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    2.013830] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    2.014501] mice: PS/2 mouse device common for all mice
[    2.014700] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    2.014722] rtc0: alarms up to one year, y3k
[    2.014889] EISA: Probing bus 0 at eisa.0
[    2.014898] Cannot allocate resource for EISA slot 1
[    2.014900] Cannot allocate resource for EISA slot 2
[    2.014920] Cannot allocate resource for EISA slot 8
[    2.014922] EISA: Detected 0 cards.
[    2.014926] cpuidle: using governor ladder
[    2.014929] cpuidle: using governor menu
[    2.015550] TCP cubic registered
[    2.015590] Using IPI No-Shortcut mode
[    2.015943] registered taskstats version 1
[    2.016099]   Magic number: 9:208:236
[    2.016143] tty ttyv6: hash matches
[    2.016271] rtc_cmos 00:02: setting system clock to 2009-01-05 16:14:40 UTC (1231172080)
[    2.016275] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.016277] EDD information not available.
[    2.016584] Freeing unused kernel memory: 424k freed
[    2.016643] Write protecting the kernel text: 2580k
[    2.016677] Write protecting the kernel read-only data: 940k
[    2.042193] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.272061] fuse init (API version 7.9)
[    2.540083] processor ACPI0007:00: registered as cooling_device0
[    2.540090] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.548197] thermal LNXTHERM:01: registered as thermal_zone0
[    2.551206] ACPI: Thermal Zone [THM0] (58 C)
[    3.261821] No dock devices found.
[    3.319916] SCSI subsystem initialized
[    3.320358] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 9
[    3.320363] PCI: setting IRQ 9 as level-triggered
[    3.320368] ohci1394 0000:00:02.3: PCI INT B -> Link[LNKB] -> GSI 9 (level, low) -> IRQ 9
[    3.372123] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[9]  MMIO=[ec000000-ec0007ff]  Max Packet=[2048]  IR/IT contexts=[4/6]
[    3.430738] usbcore: registered new interface driver usbfs
[    3.430779] usbcore: registered new interface driver hub
[    3.444117] usbcore: registered new device driver usb
[    3.520115] libata version 3.00 loaded.
[    3.552205] ehci_hcd 0000:00:03.3: enabling device (0000 -> 0002)
[    3.552475] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 9
[    3.552481] ehci_hcd 0000:00:03.3: PCI INT D -> Link[LNKH] -> GSI 9 (level, low) -> IRQ 9
[    3.552502] ehci_hcd 0000:00:03.3: EHCI Host Controller
[    3.552581] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 1
[    3.552619] ehci_hcd 0000:00:03.3: cache line size of 128 is not supported
[    3.552629] ehci_hcd 0000:00:03.3: irq 9, io mem 0xec004000
[    3.553641] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.564067] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.564310] usb usb1: configuration #1 chosen from 1 choice
[    3.564346] hub 1-0:1.0: USB hub found
[    3.564360] hub 1-0:1.0: 6 ports detected
[    3.772361] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.772381] r8169 0000:00:0a.0: enabling device (0015 -> 0017)
[    3.772651] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    3.772655] PCI: setting IRQ 11 as level-triggered
[    3.772659] r8169 0000:00:0a.0: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    3.773004] eth0: RTL8110s at 0xe082a000, 00:90:f5:28:75:70, XID 04000000 IRQ 11
[    3.776970] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[    3.776976] ohci_hcd 0000:00:03.0: PCI INT A -> Link[LNKE] -> GSI 11 (level, low) -> IRQ 11
[    3.776992] ohci_hcd 0000:00:03.0: OHCI Host Controller
[    3.777043] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 2
[    3.777068] ohci_hcd 0000:00:03.0: irq 11, io mem 0xec001000
[    3.834339] usb usb2: configuration #1 chosen from 1 choice
[    3.834378] hub 2-0:1.0: USB hub found
[    3.834392] hub 2-0:1.0: 2 ports detected
[    3.936702] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 9
[    3.936709] ohci_hcd 0000:00:03.1: PCI INT B -> Link[LNKF] -> GSI 9 (level, low) -> IRQ 9
[    3.936727] ohci_hcd 0000:00:03.1: OHCI Host Controller
[    3.936765] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 3
[    3.936788] ohci_hcd 0000:00:03.1: irq 9, io mem 0xec002000
[    3.994259] usb usb3: configuration #1 chosen from 1 choice
[    3.994298] hub 3-0:1.0: USB hub found
[    3.994314] hub 3-0:1.0: 2 ports detected
[    4.096456] ohci_hcd 0000:00:03.2: enabling device (0010 -> 0012)
[    4.096725] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 9
[    4.096731] ohci_hcd 0000:00:03.2: PCI INT C -> Link[LNKG] -> GSI 9 (level, low) -> IRQ 9
[    4.096752] ohci_hcd 0000:00:03.2: OHCI Host Controller
[    4.096790] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 4
[    4.096812] ohci_hcd 0000:00:03.2: irq 9, io mem 0xec003000
[    4.154263] usb usb4: configuration #1 chosen from 1 choice
[    4.154303] hub 4-0:1.0: USB hub found
[    4.154318] hub 4-0:1.0: 2 ports detected
[    4.304048] usb 2-2: new full speed USB device using ohci_hcd and address 2
[    4.363577] pata_sis 0000:00:02.5: version 0.5.2
[    4.363890] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    4.363895] pata_sis 0000:00:02.5: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    4.365328] scsi0 : pata_sis
[    4.366402] scsi1 : pata_sis
[    4.367233] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x1000 irq 14
[    4.367237] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x1008 irq 15
[    4.517263] usb 2-2: configuration #1 chosen from 1 choice
[    4.528413] ata1.00: ATA-6: IC25N040ATMR04-0, MO2OAD4A, max UDMA/100
[    4.528418] ata1.00: 78140160 sectors, multi 16: LBA48 
[    4.544410] ata1.00: configured for UDMA/100
[    4.696039] usb 4-1: new full speed USB device using ohci_hcd and address 2
[    4.724297] ata2.00: ATAPI: DV-W22E, R.0A, max UDMA/33
[    4.780294] ata2.00: configured for UDMA/33
[    4.780433] scsi 0:0:0:0: Direct-Access     ATA      IC25N040ATMR04-0 MO2O PQ: 0 ANSI: 5
[    4.825035] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0090f50000707528]
[    4.828050] scsi 1:0:0:0: CD-ROM            TEAC     DV-W22E          R.0A PQ: 0 ANSI: 5
[    4.846618] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    4.846670] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    4.882504] Driver 'sd' needs updating - please use bus_type methods
[    4.882657] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[    4.882680] sd 0:0:0:0: [sda] Write Protect is off
[    4.882683] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.882719] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.882814] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[    4.882834] sd 0:0:0:0: [sda] Write Protect is off
[    4.882837] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.882871] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.882876]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    4.900949] usb 4-1: not running at top speed; connect to a high speed hub
[    4.912468]  sda1 sda2 <<6>usb 4-1: configuration #1 chosen from 1 choice
[    4.939557] usbcore: registered new interface driver libusual
[    4.945553]  sda5 >
[    4.945778] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.952366] Initializing USB Mass Storage driver...
[    4.964935] scsi2 : SCSI emulation for USB Mass Storage devices
[    4.969538] usbcore: registered new interface driver usb-storage
[    4.969544] USB Mass Storage support registered.
[    4.969677] usb-storage: device found at 2
[    4.969680] usb-storage: waiting for device to settle before scanning
[    5.262157] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    5.262164] Uniform CD-ROM driver Revision: 3.20
[    5.262302] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    6.020645] PM: Starting manual resume from disk
[    6.020651] PM: Resume from partition 8:5
[    6.020653] PM: Checking hibernation image.
[    6.020836] PM: Resume from disk failed.
[    6.082553] kjournald starting.  Commit interval 5 seconds
[    6.082574] EXT3-fs: mounted filesystem with ordered data mode.
[    9.969177] usb-storage: device scan complete
[    9.976148] scsi 2:0:0:0: Direct-Access     Generic  STORAGE DEVICE   1125 PQ: 0 ANSI: 0
[    9.983141] scsi 2:0:0:1: Direct-Access     Generic  STORAGE DEVICE   1125 PQ: 0 ANSI: 0
[    9.990138] scsi 2:0:0:2: Direct-Access     Generic  STORAGE DEVICE   1125 PQ: 0 ANSI: 0
[    9.997137] scsi 2:0:0:3: Direct-Access     Generic  STORAGE DEVICE   1125 PQ: 0 ANSI: 0
[   10.008228] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   10.008405] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   10.019224] sd 2:0:0:1: [sdc] Attached SCSI removable disk
[   10.019366] sd 2:0:0:1: Attached scsi generic sg3 type 0
[   10.030204] sd 2:0:0:2: [sdd] Attached SCSI removable disk
[   10.030316] sd 2:0:0:2: Attached scsi generic sg4 type 0
[   10.041196] sd 2:0:0:3: [sde] Attached SCSI removable disk
[   10.041287] sd 2:0:0:3: Attached scsi generic sg5 type 0
[   17.688367] udevd version 124 started
[   19.008211] Linux agpgart interface v0.103
[   19.240213] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   19.288284] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   19.388227] agpgart-sis 0000:00:00.0: SiS chipset [1039/0648]
[   19.397945] agpgart-sis 0000:00:00.0: AGP aperture is 64M @ 0xe8000000
[   19.478015] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   19.488064] ACPI: Power Button (FF) [PWRF]
[   19.488253] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[   19.504059] ACPI: Power Button (CM) [PWRB]
[   19.504223] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
[   19.520040] ACPI: Sleep Button (CM) [SLPB]
[   19.520194] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input5
[   19.520533] ACPI: Lid Switch [LID]
[   19.536066] ACPI: AC Adapter [ADP0] (on-line)
[   19.544751] ACPI: Battery Slot [BAT0] (battery present)
[   19.577899] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   19.657835] Yenta: CardBus bridge found at 0000:00:0c.0 [1558:0480]
[   19.657857] Yenta: Using CSCINT to route CSC interrupts to PCI
[   19.657860] Yenta: Routing CardBus interrupts to PCI
[   19.657865] Yenta TI: socket 0000:00:0c.0, mfunc 0x01001002, devctl 0x44
[   19.888590] Yenta: ISA IRQ mask 0x0490, PCI irq 5
[   19.888595] Socket status: 30000006
[   19.987388] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x8100
[   20.737610] input: PS/2 Generic Mouse as /devices/platform/i8042/serio2/input/input7
[   20.851406] Intel ICH 0000:00:02.7: enabling device (0000 -> 0001)
[   20.851418] Intel ICH 0000:00:02.7: PCI INT C -> Link[LNKC] -> GSI 5 (level, low) -> IRQ 5
[   21.065731] input: PS/2 Mouse as /devices/platform/i8042/serio4/input/input8
[   21.116159] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input9
[   21.289776] parport_pc 00:0b: reported by Plug and Play ACPI
[   21.289828] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   21.436796] irda_init()
[   21.436816] NET: Registered protocol family 23
[   21.556345] Linux video capture interface: v2.00
[   21.570248] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 0.
[   21.570285] nsc-ircc, chip->init
[   21.570295] nsc-ircc, Found chip at base=0x02e
[   21.570321] nsc-ircc, driver loaded (Dag Brattli)
[   21.570329] nsc_ircc_open(), can't get iobase of 0x2f8
[   21.570359] nsc-ircc, Found chip at base=0x02e
[   21.570385] nsc-ircc, driver loaded (Dag Brattli)
[   21.570388] nsc_ircc_open(), can't get iobase of 0x2f8
[   21.570574] nsc-ircc 00:09: disabled
[   21.624530] gspca: main v2.2.0 registered
[   21.640994] gspca: probing 0ac8:301b
[   21.676067] intel8x0_measure_ac97_clock: measured 55472 usecs
[   21.676072] intel8x0: clocking to 48000
[   23.536258] zc3xx: probe 2wr ov vga 0x0000
[   23.704897] zc3xx: probe 3wr vga 1 0xc000
[   24.011887] zc3xx: probe 3wr vga 2 0x0000
[   24.079839] zc3xx: Sensor UNKNOW_0 force Tas5130
[   24.095081] gspca: probe ok
[   24.095113] usbcore: registered new interface driver zc3xx
[   24.095134] zc3xx: registered
[   24.278028] cs: IO port probe 0x100-0x3af: clean.
[   24.279691] cs: IO port probe 0x3e0-0x4ff: excluding 0x480-0x48f
[   24.280404] cs: IO port probe 0x820-0x8ff: clean.
[   24.281008] cs: IO port probe 0xc00-0xcf7: clean.
[   24.281799] cs: IO port probe 0xa00-0xaff: clean.
[   24.624463] lp0: using parport0 (interrupt-driven).
[   24.698651] IrCOMM protocol (Dag Brattli)
[   24.726914] nsc-ircc 00:09: activated
[   24.726921] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 0.
[   24.726957] nsc-ircc, chip->init
[   24.726968] nsc-ircc, Found chip at base=0x02e
[   24.727189] nsc-ircc 00:09: disabled
[   25.032435] Adding 1502036k swap on /dev/sda5.  Priority:-1 extents:1 across:1502036k
[   25.589982] EXT3 FS on sda1, internal journal
[   26.738384] type=1505 audit(1231172105.264:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4095
[   26.939837] type=1505 audit(1231172105.464:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4100
[   26.940201] type=1505 audit(1231172105.468:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4100
[   27.108836] ip_tables: (C) 2000-2006 Netfilter Core Team
[   27.258923] pnp 00:09: activated
[   27.277233] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 0.
[   27.277269] __ratelimit: 5 callbacks suppressed
[   27.277271] nsc-ircc, chip->init
[   27.277281] nsc-ircc, Found chip at base=0x02e
[   27.277307] nsc-ircc, driver loaded (Dag Brattli)
[   27.277317] nsc_ircc_open(), can't get iobase of 0x2f8
[   27.277346] nsc-ircc, Found chip at base=0x02e
[   27.277373] nsc-ircc, driver loaded (Dag Brattli)
[   27.277376] nsc_ircc_open(), can't get iobase of 0x2f8
[   27.277561] nsc-ircc 00:09: disabled
[   27.289100] pnp 00:09: activated
[   28.037134] ACPI: WMI: Mapper loaded
[   29.782895] Intel ICH Modem 0000:00:02.6: PCI INT C -> Link[LNKC] -> GSI 5 (level, low) -> IRQ 5
[   30.107666] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   30.280369] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   30.280377] apm: overridden by ACPI.
[   30.624437] ppdev: user-space parallel port driver
[   33.962705] serial8250: too much work for irq3
[   34.173023] Bluetooth: Core ver 2.13
[   34.175261] NET: Registered protocol family 31
[   34.175268] Bluetooth: HCI device and connection manager initialized
[   34.175274] Bluetooth: HCI socket layer initialized
[   34.234679] Bluetooth: L2CAP ver 2.11
[   34.234689] Bluetooth: L2CAP socket layer initialized
[   34.256677] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   34.256684] Bluetooth: BNEP filters: protocol multicast
[   34.312040] Bridge firewalling registered
[   34.335491] Bluetooth: SCO (Voice Link) ver 0.6
[   34.335498] Bluetooth: SCO socket layer initialized
[   34.347834] Bluetooth: RFCOMM socket layer initialized
[   34.348112] Bluetooth: RFCOMM TTY layer initialized
[   34.348118] Bluetooth: RFCOMM ver 1.10
[   37.069327] pci 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   37.435818] [drm] Initialized drm 1.1.0 20060810
[   37.460957] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   37.703405] agpgart-sis 0000:00:00.0: AGP 3.5 bridge
[   37.703438] agpgart-sis 0000:00:00.0: putting AGP V3 device at 0000:00:00.0 into 8x mode
[   37.703443] agpgart-sis 0000:00:00.0: SiS delay workaround: giving bridge time to recover
[   37.716099] agpgart-sis 0000:00:00.0: putting AGP V3 device at 0000:01:00.0 into 8x mode
[   37.987714] [drm] Setting GART location based on new memory map
[   37.987726] [drm] Loading R300 Microcode
[   37.987766] [drm] Num pipes: 1
[   37.987774] [drm] writeback test succeeded in 1 usecs
[   38.584816] r8169: eth0: link down
[  121.526616] r8169: eth0: link up
[  121.681203] NET: Registered protocol family 17
[  127.212434] NET: Registered protocol family 10
[  127.214855] lo: Disabled Privacy Extensions
[  137.512019] eth0: no IPv6 routers present
[  168.716358] ppdev0: registered pardevice
[  168.764466] ppdev0: unregistered pardevice
[  170.293693] ppdev0: registered pardevice
[  170.340187] ppdev0: unregistered pardevice
[  171.793445] ppdev0: registered pardevice
[  171.840071] ppdev0: unregistered pardevice
[  344.078164] sirdev_get_instance - ttyS1
[  344.080122] irtty_open - ttyS1: irda line discipline opened
[  345.083940] irlap_change_speed(), setting speed to 9600
[ 1077.328559] r8169: eth0: link down
[ 1096.966030] r8169: eth0: link up
[ 2023.633211] sirdev_put_instance
[ 2023.636534] irtty_close - ttyS1: irda line discipline closed
[ 2051.873088] sirdev_get_instance - ttyS1
[ 2051.876818] irtty_open - ttyS1: irda line discipline opened
[ 2052.880231] irlap_change_speed(), setting speed to 9600

```

---

