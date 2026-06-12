---
title: "Cannot Mount External Hard Drive"
date: 2008-12-22
forum: Hardware
---

### Post by Slugzzz on 2008-12-22
Hi! When I try to mount my external hard drive it gives me the following error: 

Unable to mount (Name of hard drive)
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

Any help is greatly appreciated!

            Slugzzz

---

### Post by Mewshi on 2008-12-22
Is it making a clicking noise?

I know that some hard drives, like mine, won't function properly on certain computers due to a lack of power.

---

### Post by Slugzzz on 2008-12-22
No.. it will mount on a mac and a windows machine... but not Ubuntu.

---

### Post by Mewshi on 2008-12-22
But, are they all the same machine?

---

### Post by Slugzzz on 2008-12-22
No... three different machines. It mounts on the mac and the Windows but not on Ubuntu.

---

### Post by nordmichael29 on 2008-12-22
I had this problem as well, does it also display a notification about the HDD being improperly shut down, ("hard drive name" indicates unclean shutdown...etc.)? if so you can force the HD to mount, or plug it into the mac and then ctrl(right) click and say unmount. that should work...

---

### Post by Mewshi on 2008-12-22
That's what I'm saying.  The Ubuntu machine may not be providing proper voltage to the drive.  It's not an Ubuntu issue, it's a hardware issue, if that's the case.

---

### Post by Silentzor on 2008-12-22
Hey, the only time i had this problem was when windows did not shutdown properly, like i forced it to shutdown by the button or pulled a plug. You have to run windows or any other OS you were running previously that was using this HDD and shut it down properly.

---

### Post by Mewshi on 2008-12-22
It's *very* much dependent on the hard drive.  Some don't act like this.  Mine, a WD drive, does this horribly, and only reliably runs on some hardware...

---

### Post by Slugzzz on 2008-12-22
Okay... so I plugged it into the mac, ejected it properly... and plugged it back into Ubuntu... and the same problem. It might be worth noting that the Windows system that the hard drive worked on, I deleted and then installed Ubuntu over.

---

### Post by Mewshi on 2008-12-22
You said it was three separate machines -_-

Anyway...
try running dmesg *immediately* after you plug the device in, and give it to us.  That might help.

---

### Post by Slugzzz on 2008-12-22
err... what is the prompt for that? IS n00b :-(
Never mind... I figured it out.

---

### Post by Slugzzz on 2008-12-22
[    0.420026] Total of 1 processors activated (3832.04 BogoMIPS).
[    0.420026] CPU0 attaching sched-domain:
[    0.420026]  domain 0: span 0 level CPU
[    0.420026]   groups: 0
[    0.420026] net_namespace: 840 bytes
[    0.420026] Booting paravirtualized kernel on bare hardware
[    0.420026] Time: 23:30:30  Date: 12/22/08
[    0.420026] NET: Registered protocol family 16
[    0.420026] EISA bus registered
[    0.420026] ACPI: bus type pci registered
[    0.420482] PCI: PCI BIOS revision 2.10 entry at 0xfda71, last bus=1
[    0.420486] PCI: Using configuration type 1 for base access
[    0.422374] ACPI: EC: Look up EC in DSDT
[    0.429550] ACPI: Interpreter enabled
[    0.429555] ACPI: (supports S0 S1 S4 S5)
[    0.429572] ACPI: Using IOAPIC for interrupt routing
[    0.436896] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.436994] PCI: 0000:00:00.0 reg 10 32bit mmio: [e0000000, e3ffffff]
[    0.437063] pci 0000:00:01.0: supports D1
[    0.437097] PCI: 0000:00:09.0 reg 10 32bit mmio: [de000000, dfffffff]
[    0.437104] PCI: 0000:00:09.0 reg 14 32bit mmio: [d8000000, d9ffffff]
[    0.437111] PCI: 0000:00:09.0 reg 18 io port: [ec00, ecff]
[    0.437129] PCI: 0000:00:09.0 reg 30 32bit mmio: [ddff0000, ddffffff]
[    0.437164] PCI: 0000:00:0a.0 reg 10 io port: [d000, d01f]
[    0.437198] pci 0000:00:0a.0: supports D1
[    0.437200] pci 0000:00:0a.0: supports D2
[    0.437225] PCI: 0000:00:0b.0 reg 10 32bit mmio: [ddfeb800, ddfebfff]
[    0.437232] PCI: 0000:00:0b.0 reg 14 io port: [cc00, cc7f]
[    0.437265] pci 0000:00:0b.0: supports D2
[    0.437268] pci 0000:00:0b.0: PME# supported from D2 D3hot D3cold
[    0.437273] pci 0000:00:0b.0: PME# disabled
[    0.437298] PCI: 0000:00:0c.0 reg 10 io port: [c800, c8ff]
[    0.437305] PCI: 0000:00:0c.0 reg 14 32bit mmio: [ddfeb400, ddfeb7ff]
[    0.437327] PCI: 0000:00:0c.0 reg 30 32bit mmio: [fffe0000, ffffffff]
[    0.437339] pci 0000:00:0c.0: supports D1
[    0.437341] pci 0000:00:0c.0: supports D2
[    0.437344] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.437348] pci 0000:00:0c.0: PME# disabled
[    0.437376] PCI: 0000:00:0f.0 reg 10 io port: [e800, e807]
[    0.437382] PCI: 0000:00:0f.0 reg 14 io port: [e400, e403]
[    0.437389] PCI: 0000:00:0f.0 reg 18 io port: [e000, e007]
[    0.437396] PCI: 0000:00:0f.0 reg 1c io port: [dc00, dc03]
[    0.437402] PCI: 0000:00:0f.0 reg 20 io port: [d800, d80f]
[    0.437409] PCI: 0000:00:0f.0 reg 24 io port: [d400, d4ff]
[    0.437465] PCI: 0000:00:0f.1 reg 20 io port: [fc00, fc0f]
[    0.437529] PCI: 0000:00:10.0 reg 20 io port: [b800, b81f]
[    0.437549] pci 0000:00:10.0: supports D1
[    0.437551] pci 0000:00:10.0: supports D2
[    0.437554] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.437558] pci 0000:00:10.0: PME# disabled
[    0.437596] PCI: 0000:00:10.1 reg 20 io port: [bc00, bc1f]
[    0.437616] pci 0000:00:10.1: supports D1
[    0.437618] pci 0000:00:10.1: supports D2
[    0.437620] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.437625] pci 0000:00:10.1: PME# disabled
[    0.437665] PCI: 0000:00:10.2 reg 20 io port: [c000, c01f]
[    0.437684] pci 0000:00:10.2: supports D1
[    0.437687] pci 0000:00:10.2: supports D2
[    0.437689] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.437693] pci 0000:00:10.2: PME# disabled
[    0.437732] PCI: 0000:00:10.3 reg 20 io port: [c400, c41f]
[    0.437752] pci 0000:00:10.3: supports D1
[    0.437754] pci 0000:00:10.3: supports D2
[    0.437756] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.437761] pci 0000:00:10.3: PME# disabled
[    0.437785] PCI: 0000:00:10.4 reg 10 32bit mmio: [ddfeb200, ddfeb2ff]
[    0.437819] pci 0000:00:10.4: supports D1
[    0.437821] pci 0000:00:10.4: supports D2
[    0.437824] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.437828] pci 0000:00:10.4: PME# disabled
[    0.437885] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.437924] PCI: 0000:00:12.0 reg 10 io port: [b400, b4ff]
[    0.437931] PCI: 0000:00:12.0 reg 14 32bit mmio: [ddfeb100, ddfeb1ff]
[    0.437963] pci 0000:00:12.0: supports D1
[    0.437965] pci 0000:00:12.0: supports D2
[    0.437967] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.437972] pci 0000:00:12.0: PME# disabled
[    0.438027] bus 00 -> node 0
[    0.438035] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.461704] ACPI: PCI Interrupt Link [LNKA] (IRQs *3 4 5 7 10 11 12 14 15)
[    0.461864] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 *11 12 14 15)
[    0.462022] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *10 11 12 14 15)
[    0.462184] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 7 10 11 12 14 15)
[    0.462341] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.462498] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.462655] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.462812] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.462967] ACPI: Power Resource [URP1] (off)
[    0.463015] ACPI: Power Resource [URP2] (off)
[    0.463063] ACPI: Power Resource [FDDP] (off)
[    0.463111] ACPI: Power Resource [LPTP] (off)
[    0.463220] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.463276] pnp: PnP ACPI init
[    0.463286] ACPI: bus type pnp registered
[    0.467726] pnp: PnP ACPI: found 12 devices
[    0.467730] ACPI: ACPI bus type pnp unregistered
[    0.467734] PnPBIOS: Disabled by ACPI PNP
[    0.468294] PCI: Using ACPI for IRQ routing
[    0.468450] NET: Registered protocol family 8
[    0.468450] NET: Registered protocol family 20
[    0.468450] NetLabel: Initializing
[    0.468450] NetLabel:  domain hash size = 128
[    0.468450] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.468450] NetLabel:  unlabeled traffic allowed by default
[    0.468460] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.468464]    actual entries 65620
[    0.468776] AppArmor: AppArmor Filesystem Enabled
[    0.468797] ACPI: RTC can wake from S4
[    0.468808] system 00:05: ioport range 0x295-0x296 has been reserved
[    0.468808] system 00:05: ioport range 0x3f0-0x3f1 has been reserved
[    0.468808] system 00:05: ioport range 0x4d0-0x4d1 has been reserved
[    0.468808] system 00:05: ioport range 0x400-0x40f has been reserved
[    0.468808] system 00:05: ioport range 0x800-0x87f has been reserved
[    0.468808] system 00:05: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.468808] system 00:05: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.504585] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.504588] pci 0000:00:01.0:   IO window: disabled
[    0.504594] pci 0000:00:01.0:   MEM window: disabled
[    0.504598] pci 0000:00:01.0:   PREFETCH window: disabled
[    0.504615] pci 0000:00:01.0: setting latency timer to 64
[    0.504619] bus: 00 index 0 io port: [0, ffff]
[    0.504622] bus: 00 index 1 mmio: [0, ffffffff]
[    0.504624] bus: 01 index 0 mmio: [0, 0]
[    0.504627] bus: 01 index 1 mmio: [0, 0]
[    0.504629] bus: 01 index 2 mmio: [0, 0]
[    0.504631] bus: 01 index 3 mmio: [0, 0]
[    0.504644] NET: Registered protocol family 2
[    0.504800] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.505081] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.505205] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.505334] TCP: Hash tables configured (established 8192 bind 8192)
[    0.505338] TCP reno registered
[    0.505425] NET: Registered protocol family 1
[    0.505572] checking if image is initramfs... it is
[    1.008083] Switched to high resolution mode on CPU 0
[    1.270448] Freeing initrd memory: 8007k freed
[    1.271669] audit: initializing netlink socket (disabled)
[    1.271696] type=2000 audit(1229988630.268:1): initialized
[    1.277820] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.281027] VFS: Disk quotas dquot_6.5.1
[    1.281154] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.281301] msgmni has been set to 496
[    1.281470] io scheduler noop registered
[    1.281474] io scheduler anticipatory registered
[    1.281477] io scheduler deadline registered
[    1.281491] io scheduler cfq registered (default)
[    1.281506] PCI: VIA PCI bridge detected.Disabling DAC.
[    1.281515] pci 0000:00:09.0: Boot video device
[    1.281592] pci 0000:00:11.0: Bypassing VIA 8237 APIC De-Assert Message
[    1.282080] isapnp: Scanning for PnP cards...
[    1.635668] isapnp: No Plug & Play device found
[    1.691379] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.691532] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.692487] 00:02: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.695101] brd: module loaded
[    1.695209] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.695389] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.695860] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.695869] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.696621] mice: PS/2 mouse device common for all mice
[    1.696832] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    1.696871] rtc0: alarms up to one year, y3k
[    1.697049] EISA: Probing bus 0 at eisa.0
[    1.697087] EISA: Detected 0 cards.
[    1.697093] cpuidle: using governor ladder
[    1.697095] cpuidle: using governor menu
[    1.697753] TCP cubic registered
[    1.697792] Using IPI No-Shortcut mode
[    1.698060] registered taskstats version 1
[    1.698215]   Magic number: 4:609:555
[    1.698353] tty ptya1: hash matches
[    1.698453] pci_link PNP0C0F:06: hash matches
[    1.698516] rtc_cmos 00:07: setting system clock to 2008-12-22 23:30:31 UTC (1229988631)
[    1.698521] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.698523] EDD information not available.
[    1.699196] Freeing unused kernel memory: 424k freed
[    1.699260] Write protecting the kernel text: 2576k
[    1.699300] Write protecting the kernel read-only data: 936k
[    1.718261] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.979125] fuse init (API version 7.9)
[    2.090881] processor ACPI0007:00: registered as cooling_device0
[    2.829902] Linux Tulip driver version 1.1.15 (Feb 27, 2007)
[    2.829964] tulip 0000:00:0c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.830375] tulip0:  MII transceiver #1 config 1000 status 787d advertising 05e1.
[    2.836679] eth0: ADMtek Comet rev 17 at Port 0xc800, 00:12:17:57:b5:d6, IRQ 16.
[    2.836878] No dock devices found.
[    2.840273] ohci1394 0000:00:0b.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.893035] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[19]  MMIO=[ddfeb800-ddfebfff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    3.007817] usbcore: registered new interface driver usbfs
[    3.007854] usbcore: registered new interface driver hub
[    3.016576] usbcore: registered new device driver usb
[    3.032462] SCSI subsystem initialized
[    3.038846] USB Universal Host Controller Interface driver v3.0
[    3.119898] uhci_hcd 0000:00:10.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    3.119916] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    3.120026] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[    3.120070] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000b800
[    3.120328] usb usb1: configuration #1 chosen from 1 choice
[    3.120366] hub 1-0:1.0: USB hub found
[    3.120382] hub 1-0:1.0: 2 ports detected
[    3.125089] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[    3.130776] libata version 3.00 loaded.
[    3.328457] uhci_hcd 0000:00:10.1: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    3.328473] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    3.328507] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[    3.328536] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000bc00
[    3.328666] usb usb2: configuration #1 chosen from 1 choice
[    3.328699] hub 2-0:1.0: USB hub found
[    3.328712] hub 2-0:1.0: 2 ports detected
[    3.536754] uhci_hcd 0000:00:10.2: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    3.536771] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    3.536806] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[    3.536836] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000c000
[    3.536989] usb usb3: configuration #1 chosen from 1 choice
[    3.537023] hub 3-0:1.0: USB hub found
[    3.537037] hub 3-0:1.0: 2 ports detected
[    3.648166] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    3.744388] uhci_hcd 0000:00:10.3: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    3.744405] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    3.744455] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[    3.744484] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000c400
[    3.744622] usb usb4: configuration #1 chosen from 1 choice
[    3.744657] hub 4-0:1.0: USB hub found
[    3.744672] hub 4-0:1.0: 2 ports detected
[    3.836015] usb 2-1: configuration #1 chosen from 1 choice
[    3.948017] usb 2-2: new low speed USB device using uhci_hcd and address 3
[    3.952307] ehci_hcd 0000:00:10.4: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    3.952328] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    3.952362] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[    3.952407] ehci_hcd 0000:00:10.4: irq 21, io mem 0xddfeb200
[    3.964015] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.964146] usb usb5: configuration #1 chosen from 1 choice
[    3.964182] hub 5-0:1.0: USB hub found
[    3.964197] hub 5-0:1.0: 8 ports detected
[    4.020038] hub 2-0:1.0: unable to enumerate USB device on port 2
[    4.120042] usb 2-1: USB disconnect, address 2
[    4.172361] sata_via 0000:00:0f.0: version 2.3
[    4.172393] sata_via 0000:00:0f.0: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    4.172468] sata_via 0000:00:0f.0: routed to hard irq line 11
[    4.174104] scsi0 : sata_via
[    4.174331] scsi1 : sata_via
[    4.174385] ata1: SATA max UDMA/133 cmd 0xe800 ctl 0xe400 bmdma 0xd800 irq 20
[    4.174389] ata2: SATA max UDMA/133 cmd 0xe000 ctl 0xdc00 bmdma 0xd808 irq 20
[    4.376414] ata1: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    4.388177] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011060000005f76]
[    4.580015] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    4.580079] pata_via 0000:00:0f.1: version 0.3.3
[    4.580105] pata_via 0000:00:0f.1: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    4.580293] scsi2 : pata_via
[    4.580810] scsi3 : pata_via
[    4.583401] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[    4.583406] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[    4.656416] usb 2-1: new full speed USB device using uhci_hcd and address 4
[    4.744534] ata3.00: ATA-7: Maxtor 6Y080L0, YAR41BW0, max UDMA/133
[    4.744539] ata3.00: 160086528 sectors, multi 16: LBA 
[    4.760380] ata3.00: configured for UDMA/133
[    4.848665] usb 2-1: configuration #1 chosen from 1 choice
[    4.932363] ata4.00: ATAPI: LITE-ON LTR-52327S, QS57, max UDMA/33
[    4.932383] ata4.01: ATAPI: DVD-ROM DDU1621, VER S2.7, max UDMA/33
[    4.948226] ata4.00: configured for UDMA/33
[    4.964223] ata4.01: configured for UDMA/33
[    4.964393] scsi 2:0:0:0: Direct-Access     ATA      Maxtor 6Y080L0   YAR4 PQ: 0 ANSI: 5
[    4.965326] scsi 3:0:0:0: CD-ROM            LITE-ON  LTR-52327S       QS57 PQ: 0 ANSI: 5
[    4.965889] scsi 3:0:1:0: CD-ROM            SONY     DVD-ROM DDU1621  S2.7 PQ: 0 ANSI: 5
[    4.966085] via-rhine 0000:00:12.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    4.966457] eth1: VIA Rhine II at 0xddfeb100, 00:0b:6a:c5:48:8b, IRQ 23.
[    4.967168] eth1: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[    4.996746] scsi 2:0:0:0: Attached scsi generic sg0 type 0
[    4.996813] scsi 3:0:0:0: Attached scsi generic sg1 type 5
[    4.996867] scsi 3:0:1:0: Attached scsi generic sg2 type 5
[    5.036422] Driver 'sd' needs updating - please use bus_type methods
[    5.036604] sd 2:0:0:0: [sda] 160086528 512-byte hardware sectors (81964 MB)
[    5.036632] sd 2:0:0:0: [sda] Write Protect is off
[    5.036636] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.036674] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.036772] sd 2:0:0:0: [sda] 160086528 512-byte hardware sectors (81964 MB)
[    5.036794] sd 2:0:0:0: [sda] Write Protect is off
[    5.036797] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.039695] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.039706]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    5.053871]  sda1 sda2 < sda5 >
[    5.070870] sd 2:0:0:0: [sda] Attached SCSI disk
[    5.078138] sr0: scsi3-mmc drive: 247x/52x writer cd/rw xa/form2 cdda tray
[    5.078147] Uniform CD-ROM driver Revision: 3.20
[    5.078290] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    5.079812] sr1: scsi3-mmc drive: 6x/40x cd/rw xa/form2 cdda tray
[    5.079942] sr 3:0:1:0: Attached scsi CD-ROM sr1
[    5.088922] usb 2-2: new low speed USB device using uhci_hcd and address 5
[    5.289523] usb 2-2: configuration #1 chosen from 1 choice
[    5.318049] usbcore: registered new interface driver hiddev
[    5.708446] hiddev96hidraw0: USB HID v1.10 Device [APC Back-UPS ES 350 FW:823.B1a.D USB FW:B1a] on usb-0000:00:10.1-2
[    5.708480] usbcore: registered new interface driver usbhid
[    5.708485] usbhid: v2.6:USB HID core driver
[    5.765820] PM: Starting manual resume from disk
[    5.765826] PM: Resume from partition 8:5
[    5.765828] PM: Checking hibernation image.
[    5.766156] PM: Resume from disk failed.
[    5.825296] kjournald starting.  Commit interval 5 seconds
[    5.825320] EXT3-fs: mounted filesystem with ordered data mode.
[   11.934750] udevd version 124 started
[   12.623493] Linux agpgart interface v0.103
[   12.678633] agpgart: Detected VIA KT400/KT400A/KT600 chipset
[   12.682881] agpgart-via 0000:00:00.0: AGP aperture is 64M @ 0xe0000000
[   12.755291] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   12.896379] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.223605] voodoo3_smbus 0000:00:09.0: Using Banshee/Voodoo3 I2C device at d0880000
[   13.356140] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   13.369657] ACPI: Power Button (FF) [PWRF]
[   13.369841] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[   13.391076] ACPI: Power Button (CM) [PWRB]
[   13.391309] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
[   13.404040] ACPI: Sleep Button (CM) [SLPB]
[   14.151259] parport_pc 00:03: reported by Plug and Play ACPI
[   14.151349] parport0: PC-style at 0x378 (0x778), irq 7, dma 0 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   15.003003] CA0106 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   15.003050] snd-ca0106: Model 1006 Rev 00000000 Serial 10061102
[   15.182986] Linux video capture interface: v2.00
[   15.230243] gspca: main v2.2.0 registered
[   15.270711] gspca: probing 046d:08ad
[   15.938431] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   16.719947] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input6
[   16.891399] zc3xx: probe 2wr ov vga 0x0000
[   16.935410] zc3xx: probe sensor -> 11
[   16.935417] zc3xx: Find Sensor HV7131R(c)
[   16.940735] gspca: probe ok
[   16.940757] gspca: probing 046d:08ad
[   16.940771] gspca: probing 046d:08ad
[   16.940804] usbcore: registered new interface driver zc3xx
[   16.940828] zc3xx: registered
[   17.027257] usbcore: registered new interface driver snd-usb-audio
[   18.957271] lp0: using parport0 (interrupt-driven).
[   19.126375] Adding 738948k swap on /dev/sda5.  Priority:-1 extents:1 across:738948k
[   19.707892] EXT3 FS on sda1, internal journal
[   20.774539] type=1505 audit(1229988650.968:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3985
[   21.036149] type=1505 audit(1229988651.232:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3990
[   21.036600] type=1505 audit(1229988651.232:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3990
[   21.230545] ip_tables: (C) 2000-2006 Netfilter Core Team
[   21.810865] ACPI: WMI: Mapper loaded
[   23.007076] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   23.084265] apm: BIOS not found.
[   23.267314] ppdev: user-space parallel port driver
[   24.792199] Bluetooth: Core ver 2.13
[   24.795239] NET: Registered protocol family 31
[   24.795248] Bluetooth: HCI device and connection manager initialized
[   24.795254] Bluetooth: HCI socket layer initialized
[   24.828653] Bluetooth: L2CAP ver 2.11
[   24.828663] Bluetooth: L2CAP socket layer initialized
[   24.850779] Bluetooth: SCO (Voice Link) ver 0.6
[   24.850788] Bluetooth: SCO socket layer initialized
[   24.896872] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   24.896882] Bluetooth: BNEP filters: protocol multicast
[   24.942831] Bridge firewalling registered
[   24.943856] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   24.972137] Bluetooth: RFCOMM socket layer initialized
[   24.972499] Bluetooth: RFCOMM TTY layer initialized
[   24.972507] Bluetooth: RFCOMM ver 1.10
[   26.501000] [drm] Initialized drm 1.1.0 20060810
[   26.527869] voodoo3_smbus 0000:00:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   26.527885] voodoo3_smbus 0000:00:09.0: setting latency timer to 64
[   26.530450] [drm] Initialized tdfx 1.0.0 20010216 on minor 0
[   29.118824] eth1: link down
[   29.445413] NET: Registered protocol family 17
[   32.121623] 0000:00:0c.0: tulip_stop_rxtx() failed (CSR5 0xfc664010 CSR6 0xff972113)
[   32.121642] eth0: Setting full-duplex based on MII#1 link partner capability of edb5.
[  117.488252] ppdev0: registered pardevice
[  117.582414] ppdev0: unregistered pardevice
[  117.721320] ppdev0: registered pardevice
[  117.768042] ppdev0: unregistered pardevice
[  120.564389] ppdev0: registered pardevice
[  120.612193] ppdev0: unregistered pardevice
[  208.784014] usb 5-6: new high speed USB device using ehci_hcd and address 4
[  208.934598] usb 5-6: configuration #1 chosen from 1 choice
[  209.107121] usbcore: registered new interface driver libusual
[  209.145035] Initializing USB Mass Storage driver...
[  209.147691] scsi4 : SCSI emulation for USB Mass Storage devices
[  209.148966] usbcore: registered new interface driver usb-storage
[  209.149148] USB Mass Storage support registered.
[  209.149466] usb-storage: device found at 4
[  209.149472] usb-storage: waiting for device to settle before scanning
[  214.148224] usb-storage: device scan complete
[  219.760020] usb 5-6: reset high speed USB device using ehci_hcd and address 4
[  219.898907] scsi 4:0:0:0: Direct-Access     Maxtor   OneTouch III     0344 PQ: 0 ANSI: 4
[  219.908267] sd 4:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[  219.909508] sd 4:0:0:0: [sdb] Write Protect is off
[  219.909514] sd 4:0:0:0: [sdb] Mode Sense: 17 00 00 00
[  219.909518] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  219.910879] sd 4:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[  219.912018] sd 4:0:0:0: [sdb] Write Protect is off
[  219.912025] sd 4:0:0:0: [sdb] Mode Sense: 17 00 00 00
[  219.912027] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  219.912580]  sdb:<6>usb 5-6: reset high speed USB device using ehci_hcd and address 4
[  250.233536]  sdb1
[  250.237080] sd 4:0:0:0: [sdb] Attached SCSI disk
[  250.237681] sd 4:0:0:0: Attached scsi generic sg3 type 0
[  311.076436] NET: Registered protocol family 10
[  311.079136] lo: Disabled Privacy Extensions
[  311.081063] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  321.196008] eth0: no IPv6 routers present
[ 1647.892112] usb 5-6: USB disconnect, address 4
[ 1729.496015] usb 5-2: new high speed USB device using ehci_hcd and address 5
[ 1729.645844] usb 5-2: configuration #1 chosen from 1 choice
[ 1729.649605] scsi5 : SCSI emulation for USB Mass Storage devices
[ 1729.650485] usb-storage: device found at 5
[ 1729.650492] usb-storage: waiting for device to settle before scanning
[ 1734.648296] usb-storage: device scan complete
[ 1735.391117] scsi 5:0:0:0: Direct-Access     Maxtor   OneTouch III     0344 PQ: 0 ANSI: 4
[ 1735.397053] sd 5:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[ 1735.398471] sd 5:0:0:0: [sdb] Write Protect is off
[ 1735.398480] sd 5:0:0:0: [sdb] Mode Sense: 17 00 00 00
[ 1735.398483] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1735.399832] sd 5:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[ 1735.401956] sd 5:0:0:0: [sdb] Write Protect is off
[ 1735.401962] sd 5:0:0:0: [sdb] Mode Sense: 17 00 00 00
[ 1735.401965] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1735.404388]  sdb: sdb1
[ 1735.426448] sd 5:0:0:0: [sdb] Attached SCSI disk
[ 1735.427504] sd 5:0:0:0: Attached scsi generic sg3 type 0
[ 2778.155802] usb 5-2: USB disconnect, address 5
[ 2780.264015] usb 5-2: new high speed USB device using ehci_hcd and address 6
[ 2780.413802] usb 5-2: configuration #1 chosen from 1 choice
[ 2780.417596] scsi6 : SCSI emulation for USB Mass Storage devices
[ 2780.418474] usb-storage: device found at 6
[ 2780.418480] usb-storage: waiting for device to settle before scanning
[ 2785.416250] usb-storage: device scan complete
[ 2786.152723] scsi 6:0:0:0: Direct-Access     Maxtor   OneTouch III     0344 PQ: 0 ANSI: 4
[ 2786.180238] sd 6:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[ 2786.185851] sd 6:0:0:0: [sdb] Write Protect is off
[ 2786.185864] sd 6:0:0:0: [sdb] Mode Sense: 17 00 00 00
[ 2786.185869] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 2786.187555] sd 6:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[ 2786.189400] sd 6:0:0:0: [sdb] Write Protect is off
[ 2786.189413] sd 6:0:0:0: [sdb] Mode Sense: 17 00 00 00
[ 2786.189417] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 2786.190027]  sdb: sdb1
[ 2786.213312] sd 6:0:0:0: [sdb] Attached SCSI disk
[ 2786.213726] sd 6:0:0:0: Attached scsi generic sg3 type 0
[ 7912.565153] usb 5-2: USB disconnect, address 6
[ 7972.776016] usb 5-2: new high speed USB device using ehci_hcd and address 7
[ 7972.925768] usb 5-2: configuration #1 chosen from 1 choice
[ 7972.929617] scsi7 : SCSI emulation for USB Mass Storage devices
[ 7972.931599] usb-storage: device found at 7
[ 7972.931610] usb-storage: waiting for device to settle before scanning
[ 7977.928250] usb-storage: device scan complete
[ 7983.540019] usb 5-2: reset high speed USB device using ehci_hcd and address 7
[ 7983.678956] scsi 7:0:0:0: Direct-Access     Maxtor   OneTouch III     0344 PQ: 0 ANSI: 4
[ 7983.693212] sd 7:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[ 7983.694610] sd 7:0:0:0: [sdb] Write Protect is off
[ 7983.694619] sd 7:0:0:0: [sdb] Mode Sense: 17 00 00 00
[ 7983.694623] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 7983.698179] sd 7:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[ 7983.712064] sd 7:0:0:0: [sdb] Write Protect is off
[ 7983.712077] sd 7:0:0:0: [sdb] Mode Sense: 17 00 00 00
[ 7983.712081] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 7983.712815]  sdb:<6>usb 5-2: reset high speed USB device using ehci_hcd and address 7
[ 8014.039834]  sdb1
[ 8014.043335] sd 7:0:0:0: [sdb] Attached SCSI disk
[ 8014.043935] sd 7:0:0:0: Attached scsi generic sg3 type 0
[ 9614.979035] usb 5-2: USB disconnect, address 7
[ 9642.044016] usb 5-2: new high speed USB device using ehci_hcd and address 8
[ 9642.205437] usb 5-2: configuration #1 chosen from 1 choice
[ 9642.225170] scsi8 : SCSI emulation for USB Mass Storage devices
[ 9642.235131] usb-storage: device found at 8
[ 9642.235146] usb-storage: waiting for device to settle before scanning

---

### Post by Slugzzz on 2008-12-22
Here is my system info by the way:

Ubuntu 
Release 8.10 (intrepid)
Kernel Linux 2.6.27-9-generic
GNOME 2.24.1

Hardware
Memory 248.7 MiB
Processor: AMD Athlon(tm) XP 2600+

System Status
Available disk space: 68.0 GiB

---

### Post by newtolinuxhardy on 2008-12-22
heres what you should do:

1.  check the power cable.  use a voltmeter to check the voltage.  use an ammeter to check the amperes.  check where the cable plugs into the hard drive.  inspect the cable itself.

2.  check the data cable.  check where the cable plugs into the hard drive.  inspect the cable itself.  check where the cable connects to the motherboard.

3.  plug the drive in and go to the bios.  most bios offer a hard disk self check.  run this.

if everything checks out then someone else will have to help you.  i have a hardware oriented mind, not a software oriented mind (i don't understand much about software).

---

### Post by Slugzzz on 2008-12-23
How do you go to the BIOS?  Sorry... :confused:

---

### Post by newtolinuxhardy on 2008-12-23
it varies from computer to computer.  wait until you see a screen with the name of either your computer manufacturer (sony for example) or the name of your motherboard manufacturer.  you will then have to press either escape, F1, or F10(mostly restricted to laptops).

---

### Post by muxpux on 2008-12-23
Hey guys i had a thread very similar and i had read your posts about being not enough power and remembered reading about a jumper setting on the motherboard for ps2_usb_PWR1 power, i just switched this from +5VSB to +5V and the drive mounted instantly, thanks hope this helps!

---

