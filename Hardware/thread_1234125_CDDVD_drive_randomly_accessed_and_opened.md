---
title: "CD/DVD drive randomly accessed and opened"
date: 2009-08-07
forum: Hardware
---

### Post by BlueElk on 2009-08-07
Every once in a while Ubuntu attempts to access my (empty) CD/DVD drive. It happens completely at random, and once it starts it doesn't stop until the tray is ejected. If I leave it trying long enough it will eventually manage to eject the tray by itself. Usually I just do it myself manually to stop it from making all that irritating noise (and it can't be healthy for the drive either). Once the tray is ejected I can push it back in and everything is fine. I never have another problem with the drive until the next time I start up the laptop. Or the next-next time, or the time after that, there is no way to tell. 

I've checked the logs via System - Administration - Log File Viewer, but I can't find anything in there while this is happening. 

This has happened before, but the behavior disappeared with some update or another.

I have a HP Pavilion dv5-1190eo running an up-to-date Jaunty. 

Someone had a similar question and they asked him to try (a) "eject" and (b) "eject -t". For me, (a) ejects the tray, (b) just prints "eject: CD-ROM tray close command failed: Input/output error"

---

### Post by BlueElk on 2009-08-11
It happened again. This time the tray just popped open without any previous attempt to access the drive, i.e. there was no preceding noise. It just opened. 

I am not sure if it's significant, but I found this in the message log:

[FONT="Courier New"]golem kernel: [  793.134536] CE: hpet increasing min_delta_ns to 15000 nsec[/FONT]

It seems to have occured at the same time as the tray opened.

Anyone?

---

### Post by BlueElk on 2009-08-13
Scratch the previous post. It keeps happening and no such message appears in the logs. 

Someone?

---

### Post by brookie on 2009-08-13
I am running intrepid 8.10 and my cdrom/dvd randomly opens/ejects every day with no disc in it. It seems to happen after startup in the morning. This never happened in WinXp on the same machine, (Inspiron 600m). It would be cool if we could figure this one out.

---

### Post by BlueElk on 2009-08-14
Sorry to hear you have the same problem, but at the same time I'm kind of relieved to hear that I am not alone. :)

I have windows vista on the same machine and it never happens when I boot into that operating... system... for me either.

---

### Post by BlueElk on 2009-08-19
*bump*

Tray popped out again; this time while browsing the web in firefox. 

Anyone?

---

### Post by brookie on 2009-08-29
just happened again! browsing the forums with firefox. not easily reproducible but i ran dmesg right after it happened. it sure would be nice to troubleshoot this properly and find a fix. 

here's the output of dmesg, maybe it's something in the end but i don't know, and i have googled my *** off trying to figure out a way to troubleshoot this.

anybody else having this issue or able to find a fix? any troubleshooting help will be appreciated. 

```
[    0.551638] pnp 00:03: io resource (0x860-0x87f) overlaps 0000:00:1f.0 BAR 7 (0x800-0x87f), disabling
[    0.574897] pnp: PnP ACPI: found 13 devices
[    0.574901] ACPI: ACPI bus type pnp unregistered
[    0.574906] PnPBIOS: Disabled by ACPI PNP
[    0.575283] PCI: Using ACPI for IRQ routing
[    0.575402] NET: Registered protocol family 8
[    0.575402] NET: Registered protocol family 20
[    0.575402] NetLabel: Initializing
[    0.575402] NetLabel:  domain hash size = 128
[    0.575402] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.575402] NetLabel:  unlabeled traffic allowed by default
[    0.575402] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.575402]    actual entries 65620
[    0.575402] AppArmor: AppArmor Filesystem Enabled
[    0.575402] system 00:00: iomem range 0x0-0x9fbff could not be reserved
[    0.575402] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
[    0.575402] system 00:00: iomem range 0xc0000-0xcffff could not be reserved
[    0.575402] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[    0.575402] system 00:00: iomem range 0x100000-0x7ffeffff could not be reserved
[    0.575402] system 00:00: iomem range 0x7fff0000-0x7fffffff could not be reserved
[    0.575402] system 00:00: iomem range 0xfeda0000-0xfedfffff could not be reserved
[    0.576037] system 00:00: iomem range 0xffb00000-0xffbfffff could not be reserved
[    0.576045] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.576052] system 00:03: ioport range 0xf400-0xf4fe has been reserved
[    0.576056] system 00:03: ioport range 0x880-0x8bf has been reserved
[    0.576060] system 00:03: ioport range 0x8c0-0x8df has been reserved
[    0.576063] system 00:03: ioport range 0x8e0-0x8ff has been reserved
[    0.576073] system 00:08: ioport range 0x900-0x97f has been reserved
[    0.611194] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.611199] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
[    0.611204] pci 0000:00:01.0:   MEM window: 0xfc000000-0xfdffffff
[    0.611208] pci 0000:00:01.0:   PREFETCH window: 0x000000e8000000-0x000000efffffff
[    0.611223] pci 0000:02:01.0: CardBus bridge, secondary bus 0000:03
[    0.611226] pci 0000:02:01.0:   IO window: 0x00d000-0x00d0ff
[    0.611231] pci 0000:02:01.0:   IO window: 0x00d400-0x00d4ff
[    0.611236] pci 0000:02:01.0:   PREFETCH window: 0x88000000-0x8bffffff
[    0.611241] pci 0000:02:01.0:   MEM window: 0x94000000-0x97ffffff
[    0.611246] pci 0000:02:01.1: CardBus bridge, secondary bus 0000:07
[    0.611249] pci 0000:02:01.1:   IO window: 0x00d800-0x00d8ff
[    0.611254] pci 0000:02:01.1:   IO window: 0x00dc00-0x00dcff
[    0.611259] pci 0000:02:01.1:   PREFETCH window: 0x8c000000-0x8fffffff
[    0.611264] pci 0000:02:01.1:   MEM window: 0x98000000-0x9bffffff
[    0.611269] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.611273] pci 0000:00:1e.0:   IO window: 0xd000-0xefff
[    0.611279] pci 0000:00:1e.0:   MEM window: 0xf6000000-0xfbffffff
[    0.611284] pci 0000:00:1e.0:   PREFETCH window: 0x00000088000000-0x0000008fffffff
[    0.611302] pci 0000:00:1e.0: setting latency timer to 64
[    0.611311] pci 0000:02:01.0: enabling device (0000 -> 0003)
[    0.611537] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    0.611540] PCI: setting IRQ 11 as level-triggered
[    0.611545] pci 0000:02:01.0: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.611557] pci 0000:02:01.1: enabling device (0000 -> 0003)
[    0.611562] pci 0000:02:01.1: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.611570] bus: 00 index 0 io port: [0, ffff]
[    0.611573] bus: 00 index 1 mmio: [0, ffffffff]
[    0.611575] bus: 01 index 0 io port: [c000, cfff]
[    0.611578] bus: 01 index 1 mmio: [fc000000, fdffffff]
[    0.611581] bus: 01 index 2 mmio: [e8000000, efffffff]
[    0.611583] bus: 01 index 3 mmio: [0, 0]
[    0.611586] bus: 02 index 0 io port: [d000, efff]
[    0.611589] bus: 02 index 1 mmio: [f6000000, fbffffff]
[    0.611591] bus: 02 index 2 mmio: [88000000, 8fffffff]
[    0.611594] bus: 02 index 3 io port: [0, ffff]
[    0.611597] bus: 02 index 4 mmio: [0, ffffffff]
[    0.611599] bus: 03 index 0 io port: [d000, d0ff]
[    0.611602] bus: 03 index 1 io port: [d400, d4ff]
[    0.611604] bus: 03 index 2 mmio: [88000000, 8bffffff]
[    0.611607] bus: 03 index 3 mmio: [94000000, 97ffffff]
[    0.611610] bus: 07 index 0 io port: [d800, d8ff]
[    0.611613] bus: 07 index 1 io port: [dc00, dcff]
[    0.611615] bus: 07 index 2 mmio: [8c000000, 8fffffff]
[    0.611618] bus: 07 index 3 mmio: [98000000, 9bffffff]
[    0.611628] NET: Registered protocol family 2
[    0.611767] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.612086] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.613101] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.613811] TCP: Hash tables configured (established 131072 bind 65536)
[    0.613815] TCP reno registered
[    0.613983] NET: Registered protocol family 1
[    0.614155] checking if image is initramfs... it is
[    1.112084] Switched to high resolution mode on CPU 0
[    1.483954] Freeing initrd memory: 8005k freed
[    1.484795] audit: initializing netlink socket (disabled)
[    1.484822] type=2000 audit(1251565231.484:1): initialized
[    1.491466] highmem bounce pool size: 64 pages
[    1.491476] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.494250] VFS: Disk quotas dquot_6.5.1
[    1.494356] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.494495] msgmni has been set to 1743
[    1.494653] io scheduler noop registered
[    1.494656] io scheduler anticipatory registered
[    1.494659] io scheduler deadline registered
[    1.494674] io scheduler cfq registered (default)
[    1.494768] pci 0000:01:00.0: Boot video device
[    1.495168] isapnp: Scanning for PnP cards...
[    1.848063] isapnp: No Plug & Play device found
[    1.888168] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.888307] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.889099] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.889571] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[    1.889576] PCI: setting IRQ 5 as level-triggered
[    1.889581] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[    1.889591] serial 0000:00:1f.6: PCI INT B disabled
[    1.891414] brd: module loaded
[    1.891505] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.891649] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.896573] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.896580] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.896903] mice: PS/2 mouse device common for all mice
[    1.897062] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.897082] rtc0: alarms up to one day
[    1.897218] EISA: Probing bus 0 at eisa.0
[    1.897245] EISA: Detected 0 cards.
[    1.897249] cpuidle: using governor ladder
[    1.897252] cpuidle: using governor menu
[    1.897880] TCP cubic registered
[    1.897917] Using IPI No-Shortcut mode
[    1.898137] registered taskstats version 1
[    1.898268]   Magic number: 5:955:37
[    1.898437] rtc_cmos 00:06: setting system clock to 2009-08-29 17:00:33 UTC (1251565233)
[    1.898441] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.898444] EDD information not available.
[    1.898810] Freeing unused kernel memory: 428k freed
[    1.898867] Write protecting the kernel text: 2584k
[    1.898904] Write protecting the kernel read-only data: 940k
[    1.902358] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.972865] vesafb: framebuffer at 0xe8000000, mapped to 0xf8880000, using 4608k, total 65472k
[    1.972870] vesafb: mode is 1024x768x24, linelength=3072, pages=27
[    1.972873] vesafb: protected mode interface info at c000:57f3
[    1.972876] vesafb: pmi: set display start = c00c5861, set palette = c00c589b
[    1.972879] vesafb: pmi: ports = c010 c016 c054 c038 c03c c05c c000 c004 c0b0 c0b2 c0b4 
[    1.972888] vesafb: scrolling: redraw
[    1.972892] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[    1.973157] Console: switching to colour frame buffer device 128x48
[    2.018120] fb0: VESA VGA frame buffer device
[    2.213869] fuse init (API version 7.9)
[    2.235483] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[    2.235551] processor ACPI0007:00: registered as cooling_device0
[    2.235557] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.241356] thermal LNXTHERM:01: registered as thermal_zone0
[    2.244414] ACPI: Thermal Zone [THM] (40 C)
[    3.104099] usbcore: registered new interface driver usbfs
[    3.104133] usbcore: registered new interface driver hub
[    3.104173] usbcore: registered new device driver usb
[    3.110812] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[    3.110819] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 11 (level, low) -> IRQ 11
[    3.110836] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.110840] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.110905] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    3.114825] ehci_hcd 0000:00:1d.7: debug port 1
[    3.114833] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.114844] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xf4fffc00
[    3.118779] USB Universal Host Controller Interface driver v3.0
[    3.146762] ACPI: ACPI Dock Station Driver
[    3.167541] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.167792] usb usb1: configuration #1 chosen from 1 choice
[    3.167826] hub 1-0:1.0: USB hub found
[    3.167838] hub 1-0:1.0: 6 ports detected
[    3.195419] SCSI subsystem initialized
[    3.232741] libata version 3.00 loaded.
[    3.372644] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    3.372652] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    3.372664] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.372668] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.372703] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    3.372732] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000bf80
[    3.372853] usb usb2: configuration #1 chosen from 1 choice
[    3.372886] hub 2-0:1.0: USB hub found
[    3.372896] hub 2-0:1.0: 2 ports detected
[    3.484090] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    3.580435] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    3.580449] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.580454] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.580483] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    3.580511] uhci_hcd 0000:00:1d.1: irq 11, io base 0x0000bf40
[    3.580632] usb usb3: configuration #1 chosen from 1 choice
[    3.580664] hub 3-0:1.0: USB hub found
[    3.580673] hub 3-0:1.0: 2 ports detected
[    3.616579] usb 1-1: configuration #1 chosen from 1 choice
[    3.616715] hub 1-1:1.0: USB hub found
[    3.616805] hub 1-1:1.0: 7 ports detected
[    3.765432] Marking TSC unstable due to TSC halts in idle
[    3.788632] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    3.788638] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    3.788650] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.788654] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.788687] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    3.788716] uhci_hcd 0000:00:1d.2: irq 11, io base 0x0000bf20
[    3.788839] usb usb4: configuration #1 chosen from 1 choice
[    3.788872] hub 4-0:1.0: USB hub found
[    3.788882] hub 4-0:1.0: 2 ports detected
[    3.893003] pata_acpi 0000:00:1f.1: enabling device (0005 -> 0007)
[    3.893011] pata_acpi 0000:00:1f.1: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    3.893045] pata_acpi 0000:00:1f.1: setting latency timer to 64
[    3.893062] pata_acpi 0000:00:1f.1: PCI INT A disabled
[    3.893093] tg3.c:v3.94 (August 14, 2008)
[    3.893104] tg3 0000:02:00.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    3.945496] eth0: Tigon3 [partno(BCM95705A50) rev 3001 PHY(5705)] (PCI:33MHz:32-bit) 10/100/1000Base-T Ethernet 00:11:43:43:c9:14
[    3.945502] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[    3.945506] eth0: dma_rwctrl[763f0000] dma_mask[64-bit]
[    3.950657] ata_piix 0000:00:1f.1: version 2.12
[    3.950673] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    3.950724] ata_piix 0000:00:1f.1: setting latency timer to 64
[    3.951012] scsi0 : ata_piix
[    3.951279] scsi1 : ata_piix
[    3.952349] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    3.952353] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    4.012135] usb 1-1.4: new low speed USB device using ehci_hcd and address 4
[    4.109953] usb 1-1.4: configuration #1 chosen from 1 choice
[    4.168244] ata1.00: ATA-8: WDC WD2500BEVE-00WZT0, 01.01A01, max UDMA/100
[    4.168249] ata1.00: 488397168 sectors, multi 8: LBA48 
[    4.185104] ata1.00: configured for UDMA/100
[    4.348335] ata2.00: ATAPI: SAMSUNG CDRW/DVD SN-324S, U306, max UDMA/33
[    4.360031] usb 3-1: new full speed USB device using uhci_hcd and address 2
[    4.364273] ata2.00: configured for UDMA/33
[    4.364413] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500BEVE-0 01.0 PQ: 0 ANSI: 5
[    4.365292] scsi 1:0:0:0: CD-ROM            SAMSUNG  CDRW/DVD SN-324S U306 PQ: 0 ANSI: 5
[    4.383266] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    4.383311] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    4.409827] Driver 'sd' needs updating - please use bus_type methods
[    4.409964] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[    4.409984] sd 0:0:0:0: [sda] Write Protect is off
[    4.409988] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.410016] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.410095] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[    4.410112] sd 0:0:0:0: [sda] Write Protect is off
[    4.410115] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.410143] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.410148]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    4.421077]  sda1 sda2 < sda5 >
[    4.445501] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.452575] sr0: scsi3-mmc drive: 5x/24x writer cd/rw xa/form2 cdda tray
[    4.452580] Uniform CD-ROM driver Revision: 3.20
[    4.452686] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.548264] usb 3-1: configuration #1 chosen from 1 choice
[    4.550700] usbcore: registered new interface driver hiddev
[    4.553287] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.7/usb1/1-1/1-1.4/1-1.4:1.0/input/input2
[    4.568193] input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.7-1.4
[    4.573027] Fixing up Logitech keyboard report descriptor
[    4.574661] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.7/usb1/1-1/1-1.4/1-1.4:1.1/input/input3
[    4.593344] input,hiddev96,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.7-1.4
[    4.593378] usbcore: registered new interface driver usbhid
[    4.593382] usbhid: v2.6:USB HID core driver
[    4.793168] PM: Starting manual resume from disk
[    4.793173] PM: Resume from partition 8:5
[    4.793175] PM: Checking hibernation image.
[    4.793425] PM: Resume from disk failed.
[    4.867760] kjournald starting.  Commit interval 5 seconds
[    4.867774] EXT3-fs: mounted filesystem with ordered data mode.
[    5.364160] usb 1-1.7: new high speed USB device using ehci_hcd and address 5
[    5.458497] usb 1-1.7: configuration #1 chosen from 1 choice
[    6.132158] usb 1-1.1: new high speed USB device using ehci_hcd and address 6
[    6.240962] usb 1-1.1: configuration #1 chosen from 1 choice
[   12.828304] udevd version 124 started
[   13.720191] Linux agpgart interface v0.103
[   13.777119] agpgart-intel 0000:00:00.0: Intel 855PM Chipset
[   13.784240] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe0000000
[   13.902443] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   13.960241] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.030857] intel_rng: FWH not detected
[   14.196158] iTCO_vendor_support: vendor-support=0
[   14.272176] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   14.272303] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x0860)
[   14.272490] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   14.353190] ACPI: AC Adapter [AC] (on-line)
[   14.961046] ACPI: Battery Slot [BAT0] (battery present)
[   14.961120] ACPI: Battery Slot [BAT1] (battery absent)
[   14.961206] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input4
[   14.961640] ACPI: Lid Switch [LID]
[   14.961716] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input5
[   14.972025] ACPI: Power Button (CM) [PBTN]
[   14.972159] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input6
[   14.984047] ACPI: Sleep Button (CM) [SBTN]
[   15.836475] parport_pc 00:0c: reported by Plug and Play ACPI
[   15.836525] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   16.003415] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:1e/device:1f/input/input7
[   16.012036] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   16.373770] Yenta: CardBus bridge found at 0000:02:01.0 [1028:011e]
[   16.373793] Yenta O2: res at 0x94/0xD4: 00/ea
[   16.373796] Yenta O2: enabling read prefetch/write burst
[   16.433771] ieee80211_crypt: registered algorithm 'NULL'
[   16.476176] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   16.476181] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   16.501297] Yenta: ISA IRQ mask 0x0418, PCI irq 11
[   16.501302] Socket status: 30000820
[   16.501307] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   16.501315] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xefff
[   16.501319] cs: IO port probe 0xd000-0xefff: clean.
[   16.501880] pcmcia: parent PCI bridge Memory window: 0xf6000000 - 0xfbffffff
[   16.501884] pcmcia: parent PCI bridge Memory window: 0x88000000 - 0x8fffffff
[   16.521911] Yenta: CardBus bridge found at 0000:02:01.1 [1028:011e]
[   16.652784] Yenta: ISA IRQ mask 0x0418, PCI irq 11
[   16.652789] Socket status: 30000410
[   16.652794] Yenta: Raising subordinate bus# of parent bus (#02) from #06 to #0a
[   16.652802] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xefff
[   16.652806] cs: IO port probe 0xd000-0xefff: clean.
[   16.653366] pcmcia: parent PCI bridge Memory window: 0xf6000000 - 0xfbffffff
[   16.653370] pcmcia: parent PCI bridge Memory window: 0x88000000 - 0x8fffffff
[   16.717658] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   16.717663] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   16.717759] ipw2200 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[   16.729673] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   16.729728] firmware: requesting ipw2200-bss.fw
[   16.808131] Linux video capture interface: v2.00
[   16.892172] gspca: main v2.2.0 registered
[   16.928186] gspca: probing 046d:08da
[   17.168032] pccard: CardBus card inserted into slot 0
[   17.168080] PCI: 0000:03:00.0 reg 10 io port: [0, 3f]
[   17.168152] pci 0000:03:00.0: supports D1
[   17.168154] pci 0000:03:00.0: supports D2
[   17.312164] pccard: PCMCIA card inserted into slot 1
[   17.508599] input: PC Speaker as /devices/platform/pcspkr/input/input8
[   17.965551] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input9
[   18.012003] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input10
[   18.032511] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   18.572071] zc3xx: probe 2wr ov vga 0x0000
[   18.616160] zc3xx: probe sensor -> 11
[   18.616164] zc3xx: Find Sensor HV7131R(c)
[   18.621322] gspca: probe ok
[   18.621348] gspca: probing 046d:08da
[   18.621374] gspca: probing 046d:08da
[   18.621465] usbcore: registered new interface driver zc3xx
[   18.621484] zc3xx: registered
[   18.621918] usbcore: registered new interface driver libusual
[   18.689338] Initializing USB Mass Storage driver...
[   18.705105] scsi2 : SCSI emulation for USB Mass Storage devices
[   18.705266] usb-storage: device found at 5
[   18.705269] usb-storage: waiting for device to settle before scanning
[   18.705296] scsi3 : SCSI emulation for USB Mass Storage devices
[   18.705407] usbcore: registered new interface driver usb-storage
[   18.705412] USB Mass Storage support registered.
[   18.705428] usb-storage: device found at 6
[   18.705431] usb-storage: waiting for device to settle before scanning
[   18.853619] usbcore: registered new interface driver snd-usb-audio
[   19.556151] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   19.556210] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[   19.556241] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   19.768038] cs: memory probe 0xf6000000-0xfbffffff: excluding 0xf6000000-0xf65fffff 0xf6c00000-0xf71fffff 0xf7e00000-0xf83fffff 0xf9c00000-0xfa1fffff 0xfae00000-0xfb3fffff
[   19.781234] pcmcia: registering new device pcmcia1.0
[   19.908841] cs: IO port probe 0x100-0x3af: clean.
[   19.909842] cs: IO port probe 0x3e0-0x4ff: clean.
[   19.910270] cs: IO port probe 0x820-0x8ff: clean.
[   19.910325] cs: IO port probe 0xc00-0xcf7: clean.
[   19.910849] cs: IO port probe 0xa00-0xaff: clean.
[   19.912048] cs: IO port probe 0x100-0x3af: clean.
[   19.913046] cs: IO port probe 0x3e0-0x4ff: clean.
[   19.913475] cs: IO port probe 0x820-0x8ff: clean.
[   19.913529] cs: IO port probe 0xc00-0xcf7: clean.
[   19.914050] cs: IO port probe 0xa00-0xaff: clean.
[   20.384030] intel8x0_measure_ac97_clock: measured 55423 usecs
[   20.384034] intel8x0: clocking to 48000
[   20.386747] EMU10K1_Audigy 0000:03:00.0: enabling device (0000 -> 0001)
[   20.386761] EMU10K1_Audigy 0000:03:00.0: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[   20.386858] EMU10K1_Audigy 0000:03:00.0: setting latency timer to 64
[   20.592731] Audigy2 value: Special config.
[   20.604935] Writing to ADC failed!
[   20.604940] status=0x634, reg=23, value=0
[   20.614913] Writing to ADC failed!
[   20.614915] status=0x634, reg=7, value=0
[   20.624889] Writing to ADC failed!
[   20.624891] status=0x634, reg=11, value=34
[   20.634864] Writing to ADC failed!
[   20.634866] status=0x634, reg=12, value=34
[   20.644840] Writing to ADC failed!
[   20.644842] status=0x634, reg=13, value=8
[   20.654815] Writing to ADC failed!
[   20.654817] status=0x634, reg=14, value=207
[   20.664791] Writing to ADC failed!
[   20.664793] status=0x634, reg=15, value=207
[   20.674766] Writing to ADC failed!
[   20.674768] status=0x634, reg=16, value=123
[   21.798293] lp0: using parport0 (interrupt-driven).
[   21.805629] i8k: unable to get SMM BIOS version
[   21.805640] Dell laptop SMM driver v1.14 21/02/2005 Massimo Dal Zotto (dz@debian.org)
[   21.914361] Adding 6064496k swap on /dev/sda5.  Priority:-1 extents:1 across:6064496k
[   22.459584] EXT3 FS on sda1, internal journal
[   23.540375] type=1505 audit(1251565254.886:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4113
[   23.704331] usb-storage: device scan complete
[   23.705028] scsi 2:0:0:0: Direct-Access     FUJITSU  MHV2040AT        0083 PQ: 0 ANSI: 0
[   23.726596] usb-storage: device scan complete
[   23.727235] sd 2:0:0:0: [sdb] 78140160 512-byte hardware sectors (40008 MB)
[   23.728032] scsi 3:0:0:0: Direct-Access     Seagate  FreeAgent Go     100F PQ: 0 ANSI: 4
[   23.728353] sd 2:0:0:0: [sdb] Write Protect is off
[   23.728357] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   23.728360] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   23.732477] sd 2:0:0:0: [sdb] 78140160 512-byte hardware sectors (40008 MB)
[   23.733352] sd 2:0:0:0: [sdb] Write Protect is off
[   23.733355] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   23.733358] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   23.733363]  sdb: sdb1
[   23.820400] sd 2:0:0:0: [sdb] Attached SCSI disk
[   23.820610] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   23.828040] sd 3:0:0:0: [sdc] 312581808 512-byte hardware sectors (160042 MB)
[   23.832662] sd 3:0:0:0: [sdc] Write Protect is off
[   23.832666] sd 3:0:0:0: [sdc] Mode Sense: 1c 00 00 00
[   23.832670] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[   23.841500] sd 3:0:0:0: [sdc] 312581808 512-byte hardware sectors (160042 MB)
[   23.842834] sd 3:0:0:0: [sdc] Write Protect is off
[   23.842838] sd 3:0:0:0: [sdc] Mode Sense: 1c 00 00 00
[   23.842841] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[   23.842847]  sdc: sdc1
[   23.864388] sd 3:0:0:0: [sdc] Attached SCSI disk
[   23.864584] sd 3:0:0:0: Attached scsi generic sg3 type 0
[   23.975143] type=1505 audit(1251565255.318:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4118
[   23.975430] type=1505 audit(1251565255.318:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4118
[   24.285430] ip_tables: (C) 2000-2006 Netfilter Core Team
[   24.392390] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   24.392581] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Plase use
[   24.392585] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
[   24.392588] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   24.625083] NET: Registered protocol family 10
[   24.625754] lo: Disabled Privacy Extensions
[   24.719014] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   26.085533] ACPI: WMI: Mapper loaded
[   27.303531] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   27.452399] apm: BIOS not found.
[   27.620438] ppdev: user-space parallel port driver
[   29.108043] Clocksource tsc unstable (delta = -198507883 ns)
[   33.794584] pci 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   34.144951] [drm] Initialized drm 1.1.0 20060810
[   34.215542] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   34.337749] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[   34.337788] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
[   34.337851] pci 0000:01:00.0: putting AGP V2 device into 4x mode
[   34.572691] [drm] Setting GART location based on new memory map
[   34.572706] [drm] Loading R200 Microcode
[   34.572764] [drm] writeback test succeeded in 2 usecs
[   36.121678] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   36.201281] NET: Registered protocol family 17
[   46.952037] eth1: no IPv6 routers present
[   62.185600] ieee80211_crypt: registered algorithm 'CCMP'
[   62.637627] padlock: VIA PadLock not detected.
[  128.184218] ppdev0: registered pardevice
[  128.232067] ppdev0: unregistered pardevice
[  129.785978] [UFW BLOCK INPUT]: IN=eth1 OUT= MAC=00:0e:35:ec:07:04:00:80:77:0a:56:83:08:00 SRC=192.168.1.132 DST=192.168.1.4 LEN=83 TOS=0x00 PREC=0x00 TTL=64 ID=13170 PROTO=UDP SPT=161 DPT=50634 LEN=63 
[  130.836952] ppdev0: registered pardevice
[  130.884451] ppdev0: unregistered pardevice
[  131.564415] ppdev0: registered pardevice
[  131.612911] ppdev0: unregistered pardevice
[ 1411.351447] [UFW BLOCK INPUT]: IN=eth1 OUT= MAC=00:0e:35:ec:07:04:00:13:10:8e:c9:55:08:00 SRC=190.173.5.46 DST=192.168.1.4 LEN=90 TOS=0x00 PREC=0x20 TTL=109 ID=12842 PROTO=UDP SPT=13262 DPT=60921 LEN=70 
```

thanks, 
brook

---

### Post by BlueElk on 2009-09-05
This time it happened while I was playing freeciv, and I wasn't even touching the keyboard or the touchpad at the time. The lappy had been running for, say, 20 minutes. 

Suggestions?

---

### Post by BlueElk on 2009-09-11
... and again. Sorry for all the *bumps* but I don't know what to do. 

Are there other forums where I cuold post this query?

---

### Post by rkh on 2009-12-04
This is happening to me on 9.10. Did you ever figure it out?

---

### Post by BlueElk on 2009-12-06
Nah, I never figured it out. But some update or another - dare I say it? - must've fixed it. Last time it happened was ~ 6 weeks ago ago. 

I'm still using 9.04. (I am not upgrading until this: [https://bugs.launchpad.net/ubuntu/+bug/464591](https://bugs.launchpad.net/ubuntu/+bug/464591) is fixed)

---

### Post by rkh on 2009-12-07
Ah well. My workaround (leaving a dvd in the drive) works okay for now.

---

