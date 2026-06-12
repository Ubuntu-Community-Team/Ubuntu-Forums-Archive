---
title: "PC shuts down after 10m; screen not fully displayed"
date: 2010-05-17
forum: Hardware
---

### Post by florian107 on 2010-05-17
Hi,

I have had graphic problems for some time now. My screen is not displayed correctly. There is a black area at the bottom of the screen (full width and ca. 3cm wide, task bar is visible) and the desktop image and any programme I run is not visible in it. Although it's active as e.g. the cursor recognizes links in Firefox. Strangely, the full screen mode, e.g. for Firefox and movie player works fine.

The other problem, which I'm sure is related, is that the Computer shuts down without warning after being idle for about 10 minutes. The same is true when I watch a DVD on movie player or a stream on the web. It doesn't shut down completely but goes in some sort of sleep mode. I can't figure out what it is as the screen goes blank and the monitor displays the message "Input not supported".

Any idea what the problem could be? My google and forum searches have been unsuccessful.

Thanks a lot,

Florian

Ubuntu 9.10 (Karmic)
Kernel Linux 2.6.31-21-generic
Gnome 2.28.1
Memory 2GB
Mesh Core2Quad CPU Q8300@2.5GHz

flo@flo-desktop:~$ dmesg
[    0.377115] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    0.377118] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.377121] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0280 (mask 00ff)
[    0.377124] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0300 (mask 003f)
[    0.377160] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.377166] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.377171] pci 0000:00:1f.1: reg 18 io port: [0x8f0-0x8f7]
[    0.377177] pci 0000:00:1f.1: reg 1c io port: [0x8f8-0x8fb]
[    0.377182] pci 0000:00:1f.1: reg 20 io port: [0xffa0-0xffaf]
[    0.377217] pci 0000:00:1f.2: reg 10 io port: [0xd080-0xd087]
[    0.377222] pci 0000:00:1f.2: reg 14 io port: [0xd000-0xd003]
[    0.377227] pci 0000:00:1f.2: reg 18 io port: [0xcc00-0xcc07]
[    0.377232] pci 0000:00:1f.2: reg 1c io port: [0xc880-0xc883]
[    0.377237] pci 0000:00:1f.2: reg 20 io port: [0xc800-0xc80f]
[    0.377257] pci 0000:00:1f.2: PME# supported from D3hot
[    0.377260] pci 0000:00:1f.2: PME# disabled
[    0.377299] pci 0000:00:1f.3: reg 20 io port: [0x400-0x41f]
[    0.377357] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xfdf00000-0xfdffffff]
[    0.377398] pci 0000:01:00.0: reg 10 io port: [0xe800-0xe8ff]
[    0.377416] pci 0000:01:00.0: reg 18 64bit mmio: [0xfdeff000-0xfdefffff]
[    0.377429] pci 0000:01:00.0: reg 20 64bit mmio: [0xfdee0000-0xfdeeffff]
[    0.377436] pci 0000:01:00.0: reg 30 32bit mmio: [0xfebe0000-0xfebfffff]
[    0.377472] pci 0000:01:00.0: supports D1 D2
[    0.377474] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.377478] pci 0000:01:00.0: PME# disabled
[    0.377528] pci 0000:00:1c.1: bridge io port: [0xe000-0xefff]
[    0.377531] pci 0000:00:1c.1: bridge 32bit mmio: [0xfeb00000-0xfebfffff]
[    0.377536] pci 0000:00:1c.1: bridge 64bit mmio pref: [0xfde00000-0xfdefffff]
[    0.377578] pci 0000:00:1e.0: transparent bridge
[    0.377596] pci_bus 0000:00: on NUMA node 0
[    0.377600] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.377713] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.377811] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.377858] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[    0.380179] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.380271] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.380363] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.380453] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.380543] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.380633] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.380724] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.380817] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.380963] SCSI subsystem initialized
[    0.380980] libata version 3.00 loaded.
[    0.380980] usbcore: registered new interface driver usbfs
[    0.380980] usbcore: registered new interface driver hub
[    0.380980] usbcore: registered new device driver usb
[    0.380980] ACPI: WMI: Mapper loaded
[    0.380980] PCI: Using ACPI for IRQ routing
[    0.392007] Bluetooth: Core ver 2.15
[    0.392019] NET: Registered protocol family 31
[    0.392019] Bluetooth: HCI device and connection manager initialized
[    0.392019] Bluetooth: HCI socket layer initialized
[    0.392019] NetLabel: Initializing
[    0.392019] NetLabel:  domain hash size = 128
[    0.392019] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.392028] NetLabel:  unlabeled traffic allowed by default
[    0.392142] hpet clockevent registered
[    0.392144] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.392148] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.392152] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.412006] pnp: PnP ACPI init
[    0.412014] ACPI: bus type pnp registered
[    0.415123] pnp: PnP ACPI: found 16 devices
[    0.415125] ACPI: ACPI bus type pnp unregistered
[    0.415127] PnPBIOS: Disabled by ACPI PNP
[    0.415136] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[    0.415143] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[    0.415145] system 00:07: ioport range 0x800-0x87f has been reserved
[    0.415148] system 00:07: ioport range 0x480-0x4bf has been reserved
[    0.415150] system 00:07: ioport range 0x900-0x90f has been reserved
[    0.415152] system 00:07: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.415155] system 00:07: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.415159] system 00:09: iomem range 0xffc00000-0xfff7ffff has been reserved
[    0.415163] system 00:0a: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.415166] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.415171] system 00:0d: ioport range 0x280-0x28f has been reserved
[    0.415173] system 00:0d: ioport range 0x290-0x29f has been reserved
[    0.415177] system 00:0e: iomem range 0xe0000000-0xefffffff has been reserved
[    0.415181] system 00:0f: iomem range 0x0-0x9ffff could not be reserved
[    0.415184] system 00:0f: iomem range 0xc0000-0xcffff could not be reserved
[    0.415186] system 00:0f: iomem range 0xe0000-0xfffff could not be reserved
[    0.415188] system 00:0f: iomem range 0x100000-0x7f6fffff could not be reserved
[    0.449800] AppArmor: AppArmor Filesystem Enabled
[    0.449830] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.449832] pci 0000:00:1c.0:   IO window: disabled
[    0.449836] pci 0000:00:1c.0:   MEM window: disabled
[    0.449839] pci 0000:00:1c.0:   PREFETCH window: 0x000000fdf00000-0x000000fdffffff
[    0.449844] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:01
[    0.449847] pci 0000:00:1c.1:   IO window: 0xe000-0xefff
[    0.449851] pci 0000:00:1c.1:   MEM window: 0xfeb00000-0xfebfffff
[    0.449855] pci 0000:00:1c.1:   PREFETCH window: 0x000000fde00000-0x000000fdefffff
[    0.449860] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.449861] pci 0000:00:1e.0:   IO window: disabled
[    0.449865] pci 0000:00:1e.0:   MEM window: disabled
[    0.449868] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.449878]   alloc irq_desc for 16 on node -1
[    0.449880]   alloc kstat_irqs on node -1
[    0.449884] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.449888] pci 0000:00:1c.0: setting latency timer to 64
[    0.449894]   alloc irq_desc for 17 on node -1
[    0.449895]   alloc kstat_irqs on node -1
[    0.449898] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.449901] pci 0000:00:1c.1: setting latency timer to 64
[    0.449906] pci 0000:00:1e.0: setting latency timer to 64
[    0.449910] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.449912] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.449914] pci_bus 0000:02: resource 2 pref mem [0xfdf00000-0xfdffffff]
[    0.449916] pci_bus 0000:01: resource 0 io:  [0xe000-0xefff]
[    0.449918] pci_bus 0000:01: resource 1 mem: [0xfeb00000-0xfebfffff]
[    0.449920] pci_bus 0000:01: resource 2 pref mem [0xfde00000-0xfdefffff]
[    0.449922] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.449924] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffff]
[    0.449950] NET: Registered protocol family 2
[    0.450027] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.450274] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.450758] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.450973] TCP: Hash tables configured (established 131072 bind 65536)
[    0.450975] TCP reno registered
[    0.451038] NET: Registered protocol family 1
[    0.451087] Trying to unpack rootfs image as initramfs...
[    0.617787] Freeing initrd memory: 8258k freed
[    0.621897] cpufreq-nforce2: No nForce2 chipset.
[    0.621920] Scanning for low memory corruption every 60 seconds
[    0.622011] audit: initializing netlink socket (disabled)
[    0.622029] type=2000 audit(1274130029.619:1): initialized
[    0.628956] highmem bounce pool size: 64 pages
[    0.628960] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.630151] VFS: Disk quotas dquot_6.5.2
[    0.630197] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.630641] fuse init (API version 7.12)
[    0.630707] msgmni has been set to 1705
[    0.630936] alg: No test for stdrng (krng)
[    0.630945] io scheduler noop registered
[    0.630947] io scheduler anticipatory registered
[    0.630948] io scheduler deadline registered
[    0.630980] io scheduler cfq registered (default)
[    0.630989] pci 0000:00:02.0: Boot video device
[    0.631147]   alloc irq_desc for 24 on node -1
[    0.631149]   alloc kstat_irqs on node -1
[    0.631158] pcieport-driver 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.631165] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.631260]   alloc irq_desc for 25 on node -1
[    0.631262]   alloc kstat_irqs on node -1
[    0.631267] pcieport-driver 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.631274] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    0.631343] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.631357] Firmware did not grant requested _OSC control
[    0.631371] Firmware did not grant requested _OSC control
[    0.631392] Firmware did not grant requested _OSC control
[    0.631402] Firmware did not grant requested _OSC control
[    0.631413] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.631518] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.631523] ACPI: Power Button [PWRF]
[    0.631569] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.631571] ACPI: Power Button [PWRB]
[    0.632106] ACPI: SSDT 7f6c20f0 001F3 (v01 DpgPmm  P001Ist 00000011 INTL 20051117)
[    0.632349] processor LNXCPU:00: registered as cooling_device0
[    0.632671] ACPI: SSDT 7f6c2580 001F3 (v01 DpgPmm  P002Ist 00000012 INTL 20051117)
[    0.632900] processor LNXCPU:01: registered as cooling_device1
[    0.633220] ACPI: SSDT 7f6c2a10 001F3 (v01 DpgPmm  P003Ist 00000012 INTL 20051117)
[    0.633450] processor LNXCPU:02: registered as cooling_device2
[    0.633770] ACPI: SSDT 7f6c2ea0 001F3 (v01 DpgPmm  P004Ist 00000012 INTL 20051117)
[    0.634002] processor LNXCPU:03: registered as cooling_device3
[    0.635530] isapnp: Scanning for PnP cards...
[    0.893337] Switched to high resolution mode on CPU 3
[    0.893385] Switched to high resolution mode on CPU 1
[    0.893425] Switched to high resolution mode on CPU 2
[    0.895929] Switched to high resolution mode on CPU 0
[    0.989167] isapnp: No Plug & Play device found
[    0.989989] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.990082] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.990448] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.991237] brd: module loaded
[    0.991590] loop: module loaded
[    0.991642] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.991722] ata_piix 0000:00:1f.1: version 2.13
[    0.991733]   alloc irq_desc for 18 on node -1
[    0.991734]   alloc kstat_irqs on node -1
[    0.991739] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.991766] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.991830] scsi0 : ata_piix
[    0.991896] scsi1 : ata_piix
[    0.992833] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.992836] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.992855]   alloc irq_desc for 19 on node -1
[    0.992856]   alloc kstat_irqs on node -1
[    0.992860] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.992867] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.992900] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.992952] scsi2 : ata_piix
[    0.993006] scsi3 : ata_piix
[    0.994086] ata3: SATA max UDMA/133 cmd 0xd080 ctl 0xd000 bmdma 0xc800 irq 19
[    0.994088] ata4: SATA max UDMA/133 cmd 0xcc00 ctl 0xc880 bmdma 0xc808 irq 19
[    0.994733] Fixed MDIO Bus: probed
[    0.994759] PPP generic driver version 2.4.2
[    0.994822] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.994834]   alloc irq_desc for 23 on node -1
[    0.994836]   alloc kstat_irqs on node -1
[    0.994840] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.994851] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.994854] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.994877] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.994880] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.998777] ehci_hcd 0000:00:1d.7: debug port 1
[    0.998782] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.998792] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfea77c00
[    1.012006] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.012067] usb usb1: configuration #1 chosen from 1 choice
[    1.012090] hub 1-0:1.0: USB hub found
[    1.012096] hub 1-0:1.0: 8 ports detected
[    1.012142] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.012154] uhci_hcd: USB Universal Host Controller Interface driver
[    1.012171] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.012176] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.012178] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.012200] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.012219] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d400
[    1.012278] usb usb2: configuration #1 chosen from 1 choice
[    1.012298] hub 2-0:1.0: USB hub found
[    1.012303] hub 2-0:1.0: 2 ports detected
[    1.012335] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.012339] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.012342] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.012367] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.012386] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d480
[    1.012440] usb usb3: configuration #1 chosen from 1 choice
[    1.012459] hub 3-0:1.0: USB hub found
[    1.012464] hub 3-0:1.0: 2 ports detected
[    1.012495] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.012502] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.012504] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.012527] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.012552] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d800
[    1.012608] usb usb4: configuration #1 chosen from 1 choice
[    1.012628] hub 4-0:1.0: USB hub found
[    1.012632] hub 4-0:1.0: 2 ports detected
[    1.012665] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    1.012670] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.012672] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.012696] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.012720] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d880
[    1.012775] usb usb5: configuration #1 chosen from 1 choice
[    1.012794] hub 5-0:1.0: USB hub found
[    1.012800] hub 5-0:1.0: 2 ports detected
[    1.012875] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.012877] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.013364] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.013418] mice: PS/2 mouse device common for all mice
[    1.013505] rtc_cmos 00:03: RTC can wake from S4
[    1.013530] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.013550] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.013629] device-mapper: uevent: version 1.0.3
[    1.013697] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    1.013775] device-mapper: multipath: version 1.1.0 loaded
[    1.013777] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.013863] EISA: Probing bus 0 at eisa.0
[    1.013885] EISA: Detected 0 cards.
[    1.013997] cpuidle: using governor ladder
[    1.013999] cpuidle: using governor menu
[    1.014376] TCP cubic registered
[    1.014498] NET: Registered protocol family 10
[    1.014856] lo: Disabled Privacy Extensions
[    1.015116] NET: Registered protocol family 17
[    1.015129] Bluetooth: L2CAP ver 2.13
[    1.015130] Bluetooth: L2CAP socket layer initialized
[    1.015132] Bluetooth: SCO (Voice Link) ver 0.6
[    1.015134] Bluetooth: SCO socket layer initialized
[    1.015155] Bluetooth: RFCOMM TTY layer initialized
[    1.015158] Bluetooth: RFCOMM socket layer initialized
[    1.015159] Bluetooth: RFCOMM ver 1.11
[    1.015904] Using IPI No-Shortcut mode
[    1.015956] PM: Resume from disk failed.
[    1.015966] registered taskstats version 1
[    1.016058]   Magic number: 10:460:45
[    1.016112] rtc_cmos 00:03: setting system clock to 2010-05-17 21:00:30 UTC (1274130030)
[    1.016114] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.016116] EDD information not available.
[    1.041230] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.164179] ata4.01: NODEV after polling detection
[    1.164421] ata3.00: ATA-7: SAMSUNG HD502HI, 1AG01118, max UDMA7
[    1.164424] ata3.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.172297] ata4.00: ATAPI: TSSTcorp CDDVDW SH-S223C, SB02, max UDMA/100
[    1.172420] ata3.00: configured for UDMA/133
[    1.172518] scsi 2:0:0:0: Direct-Access     ATA      SAMSUNG HD502HI  1AG0 PQ: 0 ANSI: 5
[    1.172609] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    1.172638] sd 2:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.172673] sd 2:0:0:0: [sda] Write Protect is off
[    1.172675] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.172693] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.172793]  sda: sda1 sda2 <
[    1.188216] ata4.00: configured for UDMA/100
[    1.192294] scsi 3:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S223C  SB02 PQ: 0 ANSI: 5
[    1.199477] sr0: scsi3-mmc drive: 52x/52x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.199480] Uniform CD-ROM driver Revision: 3.20
[    1.199554] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    1.199589] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    1.202111]  sda5 >
[    1.202329] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.202347] Freeing unused kernel memory: 544k freed
[    1.202598] Write protecting the kernel text: 4584k
[    1.202633] Write protecting the kernel read-only data: 1840k
[    1.291392] Linux agpgart interface v0.103
[    1.295837] agpgart-intel 0000:00:00.0: Intel G33 Chipset
[    1.296768] agpgart-intel 0000:00:00.0: detected 7164K stolen memory
[    1.298183] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.298200] r8169 0000:01:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.298235] r8169 0000:01:00.0: setting latency timer to 64
[    1.298280]   alloc irq_desc for 26 on node -1
[    1.298282]   alloc kstat_irqs on node -1
[    1.298295] r8169 0000:01:00.0: irq 26 for MSI/MSI-X
[    1.298829] eth0: RTL8102e at 0xf8012000, 00:25:22:19:a0:20, XID 24a00000 IRQ 26
[    1.299617] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    1.409717] [drm] Initialized drm 1.1.0 20060810
[    1.418339] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.418344] i915 0000:00:02.0: setting latency timer to 64
[    1.421197]   alloc irq_desc for 27 on node -1
[    1.421200]   alloc kstat_irqs on node -1
[    1.421211] i915 0000:00:02.0: irq 27 for MSI/MSI-X
[    1.509510] usb 3-2: new low speed USB device using uhci_hcd and address 2
[    1.536642] integrated sync not supported
[    1.542505] [drm] fb0: inteldrmfb frame buffer device
[    1.542551] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    1.607776] [drm] DAC-6: set mode 1280x1024 18
[    1.631844] Console: switching to colour frame buffer device 160x64
[    1.689327] usb 3-2: configuration #1 chosen from 1 choice
[    1.696295] usbcore: registered new interface driver hiddev
[    1.709426] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input4
[    1.709486] generic-usb 0003:046D:C03F.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.1-2/input0
[    1.709496] usbcore: registered new interface driver usbhid
[    1.709498] usbhid: v2.6:USB HID core driver
[    1.929294] PM: Starting manual resume from disk
[    1.929297] PM: Resume from partition 8:5
[    1.929299] PM: Checking hibernation image.
[    1.930006] PM: Resume from disk failed.
[    1.933123] PM: Marking nosave pages: 000000000009f000 - 0000000000100000
[    1.933127] PM: Basic memory bitmaps created
[    1.939609] PM: Basic memory bitmaps freed
[    1.947857] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    1.947860] EXT4-fs (sda1): write access will be enabled during recovery
[    1.971422] EXT4-fs (sda1): barriers enabled
[    5.847838] kjournald2 starting: pid 420, dev sda1:8, commit interval 5 seconds
[    5.847945] EXT4-fs (sda1): delayed allocation enabled
[    5.847948] EXT4-fs: file extents enabled
[    5.872908] EXT4-fs: mballoc enabled
[    5.872921] EXT4-fs (sda1): orphan cleanup on readonly fs
[    5.872928] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 10315
[    5.872988] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 4244
[    5.873025] EXT4-fs (sda1): 2 orphan inodes deleted
[    5.873028] EXT4-fs (sda1): recovery complete
[    6.272043] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    6.707579] type=1505 audit(1274130036.188:2): operation="profile_load" pid=447 name=/usr/share/gdm/guest-session/Xsession
[    6.721236] type=1505 audit(1274130036.204:3): operation="profile_load" pid=448 name=/sbin/dhclient3
[    6.721821] type=1505 audit(1274130036.204:4): operation="profile_load" pid=448 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    6.722134] type=1505 audit(1274130036.204:5): operation="profile_load" pid=448 name=/usr/lib/connman/scripts/dhclient-script
[    6.755440] type=1505 audit(1274130036.236:6): operation="profile_load" pid=449 name=/usr/bin/evince
[    6.764806] type=1505 audit(1274130036.245:7): operation="profile_load" pid=449 name=/usr/bin/evince-previewer
[    6.770304] type=1505 audit(1274130036.253:8): operation="profile_load" pid=449 name=/usr/bin/evince-thumbnailer
[    6.787914] type=1505 audit(1274130036.269:9): operation="profile_load" pid=451 name=/usr/lib/cups/backend/cups-pdf
[    6.788592] type=1505 audit(1274130036.269:10): operation="profile_load" pid=451 name=/usr/sbin/cupsd
[    6.795717] type=1505 audit(1274130036.277:11): operation="profile_load" pid=452 name=/usr/sbin/ntpd
[   13.477990] Adding 6008268k swap on /dev/sda5.  Priority:-1 extents:1 across:6008268k 
[   13.490409] udev: starting version 147
[   13.499217] lp: driver loaded but no devices found
[   13.503112] coretemp coretemp.0: Using relative temperature scale!
[   13.503153] coretemp coretemp.1: Using relative temperature scale!
[   13.503182] coretemp coretemp.2: Using relative temperature scale!
[   13.503215] coretemp coretemp.3: Using relative temperature scale!
[   13.519623] intel_rng: FWH not detected
[   13.548747] parport_pc 00:06: reported by Plug and Play ACPI
[   13.548797] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   13.571176] ip_tables: (C) 2000-2006 Netfilter Core Team
[   13.576541] ppdev: user-space parallel port driver
[   13.584938] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   13.585127] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   13.585129] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[   13.585131] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   13.614159] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   13.625514] EXT4-fs (sda1): internal journal on sda1:8
[   13.644185] lp0: using parport0 (interrupt-driven).
[   13.644339] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.644361] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   13.728016] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input5
[   13.750772] __ratelimit: 3 callbacks suppressed
[   13.750776] type=1505 audit(1274130043.231:13): operation="profile_replace" pid=993 name=/usr/share/gdm/guest-session/Xsession
[   13.752602] type=1505 audit(1274130043.235:14): operation="profile_replace" pid=998 name=/sbin/dhclient3
[   13.753189] type=1505 audit(1274130043.235:15): operation="profile_replace" pid=998 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   13.753524] type=1505 audit(1274130043.235:16): operation="profile_replace" pid=998 name=/usr/lib/connman/scripts/dhclient-script
[   13.757997] type=1505 audit(1274130043.239:17): operation="profile_replace" pid=1003 name=/usr/bin/evince
[   13.768142] type=1505 audit(1274130043.251:18): operation="profile_replace" pid=1003 name=/usr/bin/evince-previewer
[   13.773646] type=1505 audit(1274130043.255:19): operation="profile_replace" pid=1003 name=/usr/bin/evince-thumbnailer
[   13.785604] type=1505 audit(1274130043.267:20): operation="profile_replace" pid=1105 name=/usr/lib/cups/backend/cups-pdf
[   13.786293] type=1505 audit(1274130043.267:21): operation="profile_replace" pid=1105 name=/usr/sbin/cupsd
[   13.788391] type=1505 audit(1274130043.271:22): operation="profile_replace" pid=1109 name=/usr/sbin/ntpd
[   13.949487] r8169: eth0: link up
[   13.949497] r8169: eth0: link up
[   14.780926] integrated sync not supported
[   14.901214] integrated sync not supported
[   15.902003] integrated sync not supported
[   16.009833] integrated sync not supported
[   16.132353] integrated sync not supported
[   24.544006] eth0: no IPv6 routers present
[   28.045857] integrated sync not supported
[   28.221418] integrated sync not supported
[   28.337462] integrated sync not supported
[  800.968023] usb 1-8: new high speed USB device using ehci_hcd and address 3
[  801.101531] usb 1-8: configuration #1 chosen from 1 choice
[  801.142888] Initializing USB Mass Storage driver...
[  801.143084] scsi4 : SCSI emulation for USB Mass Storage devices
[  801.143566] usb-storage: device found at 3
[  801.143569] usb-storage: waiting for device to settle before scanning
[  801.143582] usbcore: registered new interface driver usb-storage
[  801.143586] USB Mass Storage support registered.
[  806.140291] usb-storage: device scan complete
[  806.141648] scsi 4:0:0:0: Direct-Access     WDC WD80 0UE-00HCT0       0811 PQ: 0 ANSI: 0
[  806.142080] sd 4:0:0:0: Attached scsi generic sg2 type 0
[  806.142879] sd 4:0:0:0: [sdb] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[  806.144123] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  806.144126] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  806.146245] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  806.146247] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  806.146251]  sdb: sdb1
[  806.202067] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  806.202071] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  806.202075] sd 4:0:0:0: [sdb] Attached SCSI disk
[  859.149516] usb 1-7: new high speed USB device using ehci_hcd and address 4
[  859.282521] usb 1-7: configuration #1 chosen from 1 choice
[  859.282892] scsi5 : SCSI emulation for USB Mass Storage devices
[  859.283038] usb-storage: device found at 4
[  859.283041] usb-storage: waiting for device to settle before scanning
[  864.280164] usb-storage: device scan complete
[  864.280893] scsi 5:0:0:0: Direct-Access     USB2.0   CardReader CF    0100 PQ: 0 ANSI: 0
[  864.281364] sd 5:0:0:0: Attached scsi generic sg3 type 0
[  869.482436] sd 5:0:0:0: [sdc] 8027712 512-byte logical blocks: (4.11 GB/3.82 GiB)
[  869.482804] sd 5:0:0:0: [sdc] 8027712 512-byte logical blocks: (4.11 GB/3.82 GiB)
[  869.483303] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[  869.483307] sd 5:0:0:0: [sdc] Attached SCSI removable disk
[  869.483799] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[  869.486175] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[  869.486179]  sdc: sdc1
[ 2942.568423] usb 1-7: USB disconnect, address 4

---

### Post by florian107 on 2010-05-25
Come on guys, surely I'm not the only one with this problem. If any information is missing, please let me know.

---

