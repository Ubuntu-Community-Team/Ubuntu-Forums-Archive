---
title: "Error Burning DVD-R"
date: 2010-07-25
forum: Hardware
---

### Post by safetycopy on 2010-07-25
Hi All :-)

I'm having some trouble burning DVD-Rs with Ubuntu 9.10. I've tried Brasero, Gnomebaker and Xfburn, but they all fail. Below is the output from dmesg and Brasero (sorry they're rather long - I wasn't sure what parts would be pertinent).

I'd really appreciate any help - this is driving me bonkers!

dmesg:

```
[    0.195164] pci 0000:00:10.1: reg 20 io port: [0xd000-0xd01f]
[    0.195194] pci 0000:00:10.1: supports D1 D2
[    0.195197] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.195202] pci 0000:00:10.1: PME# disabled
[    0.195257] pci 0000:00:10.2: reg 20 io port: [0xd400-0xd41f]
[    0.195287] pci 0000:00:10.2: supports D1 D2
[    0.195290] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.195295] pci 0000:00:10.2: PME# disabled
[    0.195350] pci 0000:00:10.3: reg 20 io port: [0xd800-0xd81f]
[    0.195381] pci 0000:00:10.3: supports D1 D2
[    0.195383] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.195388] pci 0000:00:10.3: PME# disabled
[    0.195428] pci 0000:00:10.4: reg 10 32bit mmio: [0xde004000-0xde0040ff]
[    0.195478] pci 0000:00:10.4: supports D1 D2
[    0.195480] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.195485] pci 0000:00:10.4: PME# disabled
[    0.195560] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.195624] pci 0000:00:11.5: reg 10 io port: [0xdc00-0xdcff]
[    0.195676] pci 0000:00:11.5: supports D1 D2
[    0.195718] pci 0000:00:12.0: reg 10 io port: [0xe000-0xe0ff]
[    0.195726] pci 0000:00:12.0: reg 14 32bit mmio: [0xde005000-0xde0050ff]
[    0.195771] pci 0000:00:12.0: supports D1 D2
[    0.195774] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.195779] pci 0000:00:12.0: PME# disabled
[    0.195848] pci 0000:01:00.0: reg 10 32bit mmio: [0xd8000000-0xdbffffff]
[    0.195856] pci 0000:01:00.0: reg 14 32bit mmio: [0xdc000000-0xdcffffff]
[    0.195879] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x00ffff]
[    0.195902] pci 0000:01:00.0: supports D1 D2
[    0.195950] pci 0000:00:01.0: bridge 32bit mmio: [0xdc000000-0xddffffff]
[    0.195956] pci 0000:00:01.0: bridge 32bit mmio pref: [0xd8000000-0xdbffffff]
[    0.195966] pci_bus 0000:00: on NUMA node 0
[    0.195973] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.249418] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 10 *11 12)
[    0.249634] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 *10 11 12)
[    0.249854] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 12) *5
[    0.250044] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.250233] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.250415] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.250596] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.250779] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.251067] ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *15, disabled.
[    0.251289] ACPI: PCI Interrupt Link [ALKB] (IRQs *21)
[    0.251507] ACPI: PCI Interrupt Link [ALKC] (IRQs *22)
[    0.251773] ACPI: PCI Interrupt Link [ALKD] (IRQs *23)
[    0.252020] SCSI subsystem initialized
[    0.252041] libata version 3.00 loaded.
[    0.252119] usbcore: registered new interface driver usbfs
[    0.252119] usbcore: registered new interface driver hub
[    0.252119] usbcore: registered new device driver usb
[    0.252119] ACPI: WMI: Mapper loaded
[    0.252119] PCI: Using ACPI for IRQ routing
[    0.264013] Bluetooth: Core ver 2.15
[    0.264034] NET: Registered protocol family 31
[    0.264034] Bluetooth: HCI device and connection manager initialized
[    0.264034] Bluetooth: HCI socket layer initialized
[    0.264034] NetLabel: Initializing
[    0.264034] NetLabel:  domain hash size = 128
[    0.264034] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.264053] NetLabel:  unlabeled traffic allowed by default
[    0.277245] pnp: PnP ACPI init
[    0.277274] ACPI: bus type pnp registered
[    0.281837] pnp: PnP ACPI: found 12 devices
[    0.281840] ACPI: ACPI bus type pnp unregistered
[    0.281845] PnPBIOS: Disabled by ACPI PNP
[    0.281861] system 00:00: iomem range 0xd0000-0xd3fff has been reserved
[    0.281865] system 00:00: iomem range 0xf0000-0xf7fff could not be reserved
[    0.281869] system 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[    0.281872] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
[    0.281876] system 00:00: iomem range 0x1bff0000-0x1bffffff could not be reserved
[    0.281880] system 00:00: iomem range 0xffff0000-0xffffffff has been reserved
[    0.281883] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.281887] system 00:00: iomem range 0x100000-0x1bfeffff could not be reserved
[    0.281890] system 00:00: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.281894] system 00:00: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.281898] system 00:00: iomem range 0xfff80000-0xfffeffff has been reserved
[    0.281907] system 00:02: ioport range 0x400-0x47f has been reserved
[    0.281911] system 00:02: ioport range 0x500-0x50f has been reserved
[    0.281918] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
[    0.281922] system 00:03: ioport range 0x800-0x805 has been reserved
[    0.316650] AppArmor: AppArmor Filesystem Enabled
[    0.316689] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.316692] pci 0000:00:01.0:   IO window: disabled
[    0.316699] pci 0000:00:01.0:   MEM window: 0xdc000000-0xddffffff
[    0.316704] pci 0000:00:01.0:   PREFETCH window: 0xd8000000-0xdbffffff
[    0.316722] pci 0000:00:01.0: setting latency timer to 64
[    0.316729] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.316732] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.316735] pci_bus 0000:01: resource 1 mem: [0xdc000000-0xddffffff]
[    0.316738] pci_bus 0000:01: resource 2 pref mem [0xd8000000-0xdbffffff]
[    0.316789] NET: Registered protocol family 2
[    0.316930] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.317316] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.317462] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.317599] TCP: Hash tables configured (established 16384 bind 16384)
[    0.317603] TCP reno registered
[    0.317692] NET: Registered protocol family 1
[    0.317774] Trying to unpack rootfs image as initramfs...
[    0.546312] Freeing initrd memory: 7463k freed
[    0.556947] cpufreq-nforce2: No nForce2 chipset.
[    0.556991] Scanning for low memory corruption every 60 seconds
[    0.557144] audit: initializing netlink socket (disabled)
[    0.557171] type=2000 audit(1280092873.556:1): initialized
[    0.565509] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.567327] VFS: Disk quotas dquot_6.5.2
[    0.567405] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.568140] fuse init (API version 7.12)
[    0.568246] msgmni has been set to 867
[    0.568542] alg: No test for stdrng (krng)
[    0.568561] io scheduler noop registered
[    0.568565] io scheduler anticipatory registered
[    0.568567] io scheduler deadline registered
[    0.568625] io scheduler cfq registered (default)
[    0.568647] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
[    0.568734] pci 0000:00:11.0: Bypassing VIA 8237 APIC De-Assert Message
[    0.568746] pci 0000:01:00.0: Boot video device
[    0.568867] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.568899] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.569075] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.569080] ACPI: Power Button [PWRF]
[    0.569152] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.569156] ACPI: Power Button [PWRB]
[    0.569216] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.569223] ACPI: Sleep Button [SLPB]
[    0.569298] fan PNP0C0B:00: registered as cooling_device0
[    0.569306] ACPI: Fan [FAN] (on)
[    0.569679] processor LNXCPU:00: registered as cooling_device1
[    0.569733] processor LNXCPU:01: registered as cooling_device2
[    0.573377] thermal LNXTHERM:01: registered as thermal_zone0
[    0.573387] ACPI: Thermal Zone [THRM] (40 C)
[    0.573473] isapnp: Scanning for PnP cards...
[    0.817282] Switched to high resolution mode on CPU 1
[    0.820044] Switched to high resolution mode on CPU 0
[    0.927407] isapnp: No Plug & Play device found
[    0.928876] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.929004] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.929436] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.929546]   alloc irq_desc for 18 on node -1
[    0.929550]   alloc kstat_irqs on node -1
[    0.929559] serial 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.929684] 0000:00:0a.0: ttyS1 at I/O 0xc408 (irq = 18) is a 16450
[    0.929765] 0000:00:0a.0: ttyS2 at I/O 0xc410 (irq = 18) is a 8250
[    0.929842] 0000:00:0a.0: ttyS3 at I/O 0xc418 (irq = 18) is a 16450
[    0.929867] Couldn't register serial port 0000:00:0a.0: -28
[    0.931095] brd: module loaded
[    0.931700] loop: module loaded
[    0.931797] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.932621] pata_via 0000:00:0f.0: version 0.3.4
[    0.932813] ACPI: PCI Interrupt Link [ALKA] disabled and referenced, BIOS bug
[    0.932978] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 15, using IRQ 20
[    0.932982] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[    0.932986]   alloc irq_desc for 20 on node -1
[    0.932988]   alloc kstat_irqs on node -1
[    0.932996] pata_via 0000:00:0f.0: PCI INT A -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    0.933259] scsi0 : pata_via
[    0.933392] scsi1 : pata_via
[    0.935254] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xc800 irq 14
[    0.935258] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xc808 irq 15
[    0.935816] Fixed MDIO Bus: probed
[    0.935863] PPP generic driver version 2.4.2
[    0.935995] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.936296] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[    0.936301]   alloc irq_desc for 21 on node -1
[    0.936303]   alloc kstat_irqs on node -1
[    0.936310] ehci_hcd 0000:00:10.4: PCI INT C -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.936329] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    0.936371] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 1
[    0.936443] ehci_hcd 0000:00:10.4: irq 21, io mem 0xde004000
[    0.948016] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00
[    0.948115] usb usb1: configuration #1 chosen from 1 choice
[    0.948153] hub 1-0:1.0: USB hub found
[    0.948165] hub 1-0:1.0: 8 ports detected
[    0.948249] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.948271] uhci_hcd: USB Universal Host Controller Interface driver
[    0.948314] uhci_hcd 0000:00:10.0: PCI INT A -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.948323] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    0.948371] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[    0.948394] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000cc00
[    0.948498] usb usb2: configuration #1 chosen from 1 choice
[    0.948532] hub 2-0:1.0: USB hub found
[    0.948542] hub 2-0:1.0: 2 ports detected
[    0.948600] uhci_hcd 0000:00:10.1: PCI INT A -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.948607] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    0.948644] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[    0.948667] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000d000
[    0.948770] usb usb3: configuration #1 chosen from 1 choice
[    0.948805] hub 3-0:1.0: USB hub found
[    0.948816] hub 3-0:1.0: 2 ports detected
[    0.948872] uhci_hcd 0000:00:10.2: PCI INT B -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.948879] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    0.948916] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[    0.948939] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000d400
[    0.949042] usb usb4: configuration #1 chosen from 1 choice
[    0.949077] hub 4-0:1.0: USB hub found
[    0.949087] hub 4-0:1.0: 2 ports detected
[    0.949154] uhci_hcd 0000:00:10.3: PCI INT B -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.949161] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    0.949202] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
[    0.949224] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000d800
[    0.949329] usb usb5: configuration #1 chosen from 1 choice
[    0.949363] hub 5-0:1.0: USB hub found
[    0.949374] hub 5-0:1.0: 2 ports detected
[    0.949491] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.949494] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.949621] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.949702] mice: PS/2 mouse device common for all mice
[    0.949840] rtc_cmos 00:05: RTC can wake from S4
[    0.949885] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.949937] rtc0: alarms up to one year, y3k, 242 bytes nvram
[    0.950071] device-mapper: uevent: version 1.0.3
[    0.950222] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.950329] device-mapper: multipath: version 1.1.0 loaded
[    0.950333] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.950491] EISA: Probing bus 0 at eisa.0
[    0.950532] EISA: Detected 0 cards.
[    0.950652] cpuidle: using governor ladder
[    0.950657] cpuidle: using governor menu
[    0.951321] TCP cubic registered
[    0.951483] NET: Registered protocol family 10
[    0.952119] lo: Disabled Privacy Extensions
[    0.952598] NET: Registered protocol family 17
[    0.952624] Bluetooth: L2CAP ver 2.13
[    0.952627] Bluetooth: L2CAP socket layer initialized
[    0.952630] Bluetooth: SCO (Voice Link) ver 0.6
[    0.952632] Bluetooth: SCO socket layer initialized
[    0.952676] Bluetooth: RFCOMM TTY layer initialized
[    0.952680] Bluetooth: RFCOMM socket layer initialized
[    0.952682] Bluetooth: RFCOMM ver 1.11
[    0.952728] Using IPI No-Shortcut mode
[    0.952812] PM: Resume from disk failed.
[    0.952830] registered taskstats version 1
[    0.952977]   Magic number: 2:935:399
[    0.953085] rtc_cmos 00:05: setting system clock to 2010-07-25 21:21:14 UTC (1280092874)
[    0.953089] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.953092] EDD information not available.
[    0.970579] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.104336] ata1.00: HPA unlocked: 378445147 -> 390721968, native 390721968
[    1.104342] ata1.00: ATA-6: WDC WD2000BB-22GUA0, 08.02D08, max UDMA/100
[    1.104346] ata1.00: 390721968 sectors, multi 16: LBA48 
[    1.121511] ata1.00: configured for UDMA/100
[    1.121664] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2000BB-22G 08.0 PQ: 0 ANSI: 5
[    1.121821] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.121993] sd 0:0:0:0: [sda] 390721968 512-byte logical blocks: (200 GB/186 GiB)
[    1.122061] sd 0:0:0:0: [sda] Write Protect is off
[    1.122065] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.122099] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.122285]  sda: sda1 sda2 sda3 < sda5 >
[    1.151602] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.316020] usb 1-2: new high speed USB device using ehci_hcd and address 3
[    1.396800] ata2.00: ATAPI: SONY DVD-ROM DDU1613, 9YS2, max UDMA/33
[    1.396846] ata2.01: ATAPI: SONY    DVD RW DW-D22A, BYS2, max UDMA/66
[    1.397372] ata2.00: configured for UDMA/33
[    1.412257] ata2.01: configured for UDMA/66
[    1.413449] scsi 1:0:0:0: CD-ROM            SONY     DVD-ROM DDU1613  9YS2 PQ: 0 ANSI: 5
[    1.414965] sr0: scsi3-mmc drive: 40x/40x cd/rw xa/form2 cdda tray
[    1.414969] Uniform CD-ROM driver Revision: 3.20
[    1.415082] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.415146] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.415913] scsi 1:0:1:0: CD-ROM            SONY     DVD RW DW-D22A   BYS2 PQ: 0 ANSI: 5
[    1.419504] sr1: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    1.419587] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    1.419642] sr 1:0:1:0: Attached scsi generic sg2 type 5
[    1.419680] Freeing unused kernel memory: 544k freed
[    1.420375] Write protecting the kernel text: 4584k
[    1.420429] Write protecting the kernel read-only data: 1844k
[    1.456875] usb 1-2: configuration #1 chosen from 1 choice
[    1.574015] Linux agpgart interface v0.103
[    1.579382] agpgart: Detected VIA PM800/PN800/PM880/PN880 chipset
[    1.708060] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    1.717561] agpgart-via 0000:00:00.0: AGP aperture is 128M @ 0xd0000000
[    1.750365]   alloc irq_desc for 16 on node -1
[    1.750373]   alloc kstat_irqs on node -1
[    1.750386] ohci1394 0000:00:08.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.759023] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[    1.759034] via-rhine: Broken BIOS detected, avoid_D3 enabled.
[    1.762739] Floppy drive(s): fd0 is 1.44M
[    1.791974] FDC 0 is a post-1991 82077
[    1.810055] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[16]  MMIO=[de000000-de0007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    1.817599] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
[    1.817606]   alloc irq_desc for 23 on node -1
[    1.817609]   alloc kstat_irqs on node -1
[    1.817620] via-rhine 0000:00:12.0: PCI INT A -> Link[ALKD] -> GSI 23 (level, low) -> IRQ 23
[    1.822673] eth0: VIA Rhine II at 0xde005000, 00:11:5b:2b:6d:f8, IRQ 23.
[    1.823385] eth0: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[    1.903455] usb 2-1: configuration #1 chosen from 1 choice
[    1.914953] usbcore: registered new interface driver hiddev
[    1.928685] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:10.0/usb2/2-1/2-1:1.0/input/input5
[    1.928797] generic-usb 0003:046D:C505.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:10.0-1/input0
[    1.961858] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:10.0/usb2/2-1/2-1:1.1/input/input6
[    1.961966] generic-usb 0003:046D:C505.0002: input,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:10.0-1/input1
[    1.961990] usbcore: registered new interface driver usbhid
[    1.961994] usbhid: v2.6:USB HID core driver
[    2.682332] PM: Starting manual resume from disk
[    2.682343] PM: Resume from partition 8:1
[    2.682349] PM: Checking hibernation image.
[    2.682608] PM: Resume from disk failed.
[    2.690052] EXT3-fs: INFO: recovery required on readonly filesystem.
[    2.690060] EXT3-fs: write access will be enabled during recovery.
[    2.916229] kjournald starting.  Commit interval 5 seconds
[    2.916258] EXT3-fs: recovery complete.
[    2.916527] EXT3-fs: mounted filesystem with ordered data mode.
[    3.089236] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0000000000000145]
[    3.665832] type=1505 audit(1280092877.211:2): operation="profile_load" pid=414 name=/usr/share/gdm/guest-session/Xsession
[    3.682421] type=1505 audit(1280092877.227:3): operation="profile_load" pid=415 name=/sbin/dhclient3
[    3.683117] type=1505 audit(1280092877.227:4): operation="profile_load" pid=415 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    3.683496] type=1505 audit(1280092877.227:5): operation="profile_load" pid=415 name=/usr/lib/connman/scripts/dhclient-script
[    3.729412] type=1505 audit(1280092877.275:6): operation="profile_load" pid=416 name=/usr/bin/evince
[    3.740984] type=1505 audit(1280092877.283:7): operation="profile_load" pid=416 name=/usr/bin/evince-previewer
[    3.747796] type=1505 audit(1280092877.291:8): operation="profile_load" pid=416 name=/usr/bin/evince-thumbnailer
[    3.793847] type=1505 audit(1280092877.339:9): operation="profile_load" pid=418 name=/usr/lib/cups/backend/cups-pdf
[    3.794657] type=1505 audit(1280092877.339:10): operation="profile_load" pid=418 name=/usr/sbin/cupsd
[   10.878791] Adding 2000052k swap on /dev/sda1.  Priority:-1 extents:1 across:2000052k 
[   11.412709] udev: starting version 147
[   11.415406] EXT3 FS on sda2, internal journal
[   11.697839] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.776894] lp: driver loaded but no devices found
[   11.843179] parport_pc 00:0a: reported by Plug and Play ACPI
[   11.843252] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   11.945245] lp0: using parport0 (interrupt-driven).
[   11.954944] cfg80211: Calling CRDA to update world regulatory domain
[   12.143683] ppdev: user-space parallel port driver
[   12.174494] cfg80211: World regulatory domain updated:
[   12.174499] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   12.174503] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.174507] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.174510] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.174513] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.174516] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.253038] usb 1-2: reset high speed USB device using ehci_hcd and address 3
[   12.664885] Linux video capture interface: v2.00
[   12.724407] phy0: Selected rate control algorithm 'minstrel'
[   12.725450] zd1211rw 1-2:1.0: phy0
[   12.725490] usbcore: registered new interface driver zd1211rw
[   12.966077] ip_tables: (C) 2000-2006 Netfilter Core Team
[   13.025137] bttv: driver version 0.9.18 loaded
[   13.025143] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   13.025263] bttv: Bt8xx card found (0).
[   13.025295]   alloc irq_desc for 17 on node -1
[   13.025300]   alloc kstat_irqs on node -1
[   13.025314] bttv 0000:00:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.025330] bttv0: Bt878 (rev 17) at 0000:00:09.0, irq: 17, latency: 32, mmio: 0xde001000
[   13.025552] bttv0: detected: Prolink Pixelview PV-BT [card=72], PCI subsystem ID is 1554:4011
[   13.025560] bttv0: using: Prolink Pixelview PV-BT878P+9B (PlayTV Pro rev.9B FM+NICAM) [card=72,autodetected]
[   13.025566] IRQ 17/bttv0: IRQF_DISABLED is not guaranteed on shared IRQs
[   13.025632] bttv0: gpio: en=00000000, out=00000000 in=00afc0ff [init]
[   13.028896] bttv0: tuner type=5
[   13.374270] bttv0: audio absent, no audio device found!
[   13.422465] usb 1-2: firmware: requesting zd1211/zd1211b_ub
[   13.814747] tuner 1-0060: chip found @ 0xc0 (bt878 #0 [sw])
[   13.814851] tea5767 1-0060: type set to Philips TEA5767HN FM Radio
[   13.821969] usb 1-2: firmware: requesting zd1211/zd1211b_uphr
[   13.822817] tuner 1-0061: chip found @ 0xc2 (bt878 #0 [sw])
[   13.905642] zd1211rw 1-2:1.0: firmware version 4725
[   13.950887] zd1211rw 1-2:1.0: zd1211b chip 050d:705c v4810 high 00-1c-df AL2230_RF pa0 g--N-
[   13.953174] cfg80211: Calling CRDA for country: US
[   13.958739] cfg80211: Regulatory domain changed to country: US
[   13.958747] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.958753] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   13.958758] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   13.958765] 	(5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.958770] 	(5490000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.958774] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   13.979666] tuner-simple 1-0061: creating new instance
[   13.979677] tuner-simple 1-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[   13.980504] bttv0: registered device video0
[   13.980568] bttv0: registered device vbi0
[   13.980628] bttv0: registered device radio0
[   13.980652] bttv0: PLL: 28636363 => 35468950 ..
[   14.000861] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.004106] eth0: link down
[   14.004994] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.015587]  ok
[   14.017316] input: bttv IR (card=72) as /devices/pci0000:00/0000:00:09.0/input/input7
[   14.017709] Bt87x 0000:00:09.1: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.018124] bt87x0: Using board 1, analog, digital (rate 32000 Hz)
[   14.022938] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[   14.022948]   alloc irq_desc for 22 on node -1
[   14.022953]   alloc kstat_irqs on node -1
[   14.022968] VIA 82xx Audio 0000:00:11.5: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
[   14.023157] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   14.144082] __ratelimit: 3 callbacks suppressed
[   14.144088] type=1505 audit(1280092887.687:12): operation="profile_replace" pid=1026 name=/usr/share/gdm/guest-session/Xsession
[   14.150714] type=1505 audit(1280092887.695:13): operation="profile_replace" pid=1027 name=/sbin/dhclient3
[   14.151531] type=1505 audit(1280092887.695:14): operation="profile_replace" pid=1027 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   14.151981] type=1505 audit(1280092887.695:15): operation="profile_replace" pid=1027 name=/usr/lib/connman/scripts/dhclient-script
[   14.166381] type=1505 audit(1280092887.711:16): operation="profile_replace" pid=1030 name=/usr/bin/evince
[   14.180467] type=1505 audit(1280092887.723:17): operation="profile_replace" pid=1030 name=/usr/bin/evince-previewer
[   14.189487] type=1505 audit(1280092887.735:18): operation="profile_replace" pid=1030 name=/usr/bin/evince-thumbnailer
[   14.202739] type=1505 audit(1280092887.747:19): operation="profile_replace" pid=1033 name=/usr/lib/cups/backend/cups-pdf
[   14.203730] type=1505 audit(1280092887.747:20): operation="profile_replace" pid=1033 name=/usr/sbin/cupsd
[   14.209646] type=1505 audit(1280092887.755:21): operation="profile_replace" pid=1034 name=/usr/sbin/tcpdump
[   15.456088] CPU0 attaching NULL sched-domain.
[   15.456100] CPU1 attaching NULL sched-domain.
[   15.469100] CPU0 attaching sched-domain:
[   15.469106]  domain 0: span 0-1 level SIBLING
[   15.469111]   groups: 0 1
[   15.469117]   domain 1: span 0-1 level MC
[   15.469120]    groups: 0-1 (__cpu_power = 2048)
[   15.469128] CPU1 attaching sched-domain:
[   15.469131]  domain 0: span 0-1 level SIBLING
[   15.469135]   groups: 1 0
[   15.469141]   domain 1: span 0-1 level MC
[   15.469144]    groups: 0-1 (__cpu_power = 2048)
[   15.967045] [drm] Initialized drm 1.1.0 20060810
[   15.980019] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.980300] [drm] Initialized via 2.11.1 20070202 for 0000:01:00.0 on minor 0
[   15.984756] agpgart-via 0000:00:00.0: AGP 3.5 bridge
[   15.984798] agpgart-via 0000:00:00.0: bridge is in legacy mode, falling back to 2.x
[   15.984811] agpgart-via 0000:00:00.0: putting AGP V2 device into 4x mode
[   15.984955] pci 0000:01:00.0: putting AGP V2 device into 4x mode
[   17.794750] CPU0 attaching NULL sched-domain.
[   17.794759] CPU1 attaching NULL sched-domain.
[   17.808116] CPU0 attaching sched-domain:
[   17.808123]  domain 0: span 0-1 level SIBLING
[   17.808127]   groups: 0 1
[   17.808136] CPU1 attaching sched-domain:
[   17.808138]  domain 0: span 0-1 level SIBLING
[   17.808142]   groups: 1 0
[   61.931953] wlan0: authenticate with AP 00:22:75:63:da:08
[   61.934697] wlan0: authenticated
[   61.934701] wlan0: associate with AP 00:22:75:63:da:08
[   61.937222] wlan0: RX AssocResp from 00:22:75:63:da:08 (capab=0x411 status=0 aid=2)
[   61.937227] wlan0: associated
[   61.937791] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   62.351511] padlock: VIA PadLock not detected.
[   72.648023] wlan0: no IPv6 routers present
[  434.665519] cdrom: This disc doesn't have any tracks I recognize!
[  434.733853] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  434.733861] sr 1:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[  434.733868] sr 1:0:1:0: [sr1] Add. Sense: Logical block address out of range
[  434.733876] end_request: I/O error, dev sr1, sector 0
[  434.733882] Buffer I/O error on device sr1, logical block 0
[  434.735178] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  434.735183] sr 1:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[  434.735188] sr 1:0:1:0: [sr1] Add. Sense: Logical block address out of range
[  434.735194] end_request: I/O error, dev sr1, sector 0
[  434.735197] Buffer I/O error on device sr1, logical block 0
[  523.406789] warning: `growisofs' uses 32-bit capabilities (legacy support in use)
daniel@ubuntu:~$ 

```

Brasero:

```
Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1848)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI burn:// URI found burn:///test.txt
BraseroBurnURI called brasero_job_set_current_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI Information retrieval for burn:///test.txt
BraseroBurnURI Added file /home/daniel/Documents/test.txt at /test.txt
BraseroBurnURI called brasero_job_add_track
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI Finished track successfully
BraseroBurnURI stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_set_output_size_for_current_track
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack no remote URIs
BraseroLocalTrack stopping
BraseroChecksumFiles called brasero_job_get_output_type
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_set_output_size_for_current_track
BraseroChecksumFiles stopping
BraseroChecksumFiles called brasero_job_get_output_type
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_session_output_size
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_set_current_action
BraseroChecksumFiles called brasero_job_get_flags
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles Adding graft for checksum file /.checksum.md5 file:///tmp/brasero_tmp_NI0YFV.md5
BraseroChecksumFiles called brasero_job_add_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles Finished track successfully
BraseroChecksumFiles stopping
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs getting varg
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_flags
BraseroGrowisofs called brasero_job_get_speed
BraseroGrowisofs called brasero_job_get_device
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_session_output_size
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_fd_in
BraseroGrowisofs Using genisoimage
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_tmp_dir
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs got varg:
	growisofs
	-use-the-force-luke=notray
	-use-the-force-luke=4gms
	-dvd-compat
	-speed=4
	-use-the-force-luke=tty
	-Z
	/dev/sr1
	-dry-run
	-r
	-J
	-input-charset
	utf8
	-graft-points
	-path-list
	/tmp/brasero_tmp_FY5YFV
	-exclude-list
	/tmp/brasero_tmp_JX5YFV
	-print-size
BraseroGrowisofs Launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'genisoimage -r -J -input-charset utf8 -graft-points -path-list /tmp/brasero_tmp_FY5YFV -exclude-list /tmp/brasero_tmp_JX5YFV -print-size | builtin_dd of=/dev/sr1 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: Total extents scheduled to be written = 183
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_output_size_for_current_track
BraseroGrowisofs Finished successfully session
BraseroGrowisofs stopping
BraseroGrowisofs got killed
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs getting varg
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_flags
BraseroGrowisofs called brasero_job_get_speed
BraseroGrowisofs called brasero_job_get_device
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_session_output_size
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_fd_in
BraseroGrowisofs Using genisoimage
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_tmp_dir
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_data_label
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs got varg:
	growisofs
	-use-the-force-luke=notray
	-use-the-force-luke=4gms
	-dvd-compat
	-speed=4
	-use-the-force-luke=tracksize:183
	-use-the-force-luke=tty
	-Z
	/dev/sr1
	-r
	-J
	-input-charset
	utf8
	-graft-points
	-path-list
	/tmp/brasero_tmp_759ZFV
	-exclude-list
	/tmp/brasero_tmp_749ZFV
	-A
	Brasero-2.28.2
	-sysid
	LINUX
	-v
BraseroGrowisofs Launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'genisoimage -r -J -input-charset utf8 -graft-points -path-list /tmp/brasero_tmp_759ZFV -exclude-list /tmp/brasero_tmp_749ZFV -A Brasero-2.28.2 -sysid LINUX -v | builtin_dd of=/dev/sr1 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: genisoimage 1.1.9 (Linux)
BraseroGrowisofs stderr: Writing:   Initial Padblock                        Start Block 0
BraseroGrowisofs stderr: Done with: Initial Padblock                        Block(s)    16
BraseroGrowisofs stderr: Writing:   Primary Volume Descriptor               Start Block 16
BraseroGrowisofs stderr: Done with: Primary Volume Descriptor               Block(s)    1
BraseroGrowisofs stderr: Writing:   Joliet Volume Descriptor                Start Block 17
BraseroGrowisofs stderr: Done with: Joliet Volume Descriptor                Block(s)    1
BraseroGrowisofs stderr: Writing:   End Volume Descriptor                   Start Block 18
BraseroGrowisofs stderr: Done with: End Volume Descriptor                   Block(s)    1
BraseroGrowisofs stderr: Writing:   Version block                           Start Block 19
BraseroGrowisofs stderr: Done with: Version block                           Block(s)    1
BraseroGrowisofs stderr: Writing:   Path table                              Start Block 20
BraseroGrowisofs stderr: Done with: Path table                              Block(s)    4
BraseroGrowisofs stderr: Writing:   Joliet path table                       Start Block 24
BraseroGrowisofs stderr: Done with: Joliet path table                       Block(s)    4
BraseroGrowisofs stderr: Writing:   Directory tree                          Start Block 28
BraseroGrowisofs stderr: Done with: Directory tree                          Block(s)    1
BraseroGrowisofs stderr: Writing:   Joliet directory tree                   Start Block 29
BraseroGrowisofs stderr: Done with: Joliet directory tree                   Block(s)    1
BraseroGrowisofs stderr: Writing:   Directory tree cleanup                  Start Block 30
BraseroGrowisofs stderr: Done with: Directory tree cleanup                  Block(s)    0
BraseroGrowisofs stderr: Writing:   Extension record                        Start Block 30
BraseroGrowisofs stderr: Done with: Extension record                        Block(s)    1
BraseroGrowisofs stderr: Writing:   The File(s)                             Start Block 31
BraseroGrowisofs stderr: Total translation table size: 0
BraseroGrowisofs stderr: Total rockridge attributes bytes: 334
BraseroGrowisofs stderr: Total directory bytes: 0
BraseroGrowisofs stderr: Path table size(bytes): 10
BraseroGrowisofs stderr: Done with: The File(s)                             Block(s)    2
BraseroGrowisofs stderr: Writing:   Ending Padblock                         Start Block 33
BraseroGrowisofs stderr: Done with: Ending Padblock                         Block(s)    150
BraseroGrowisofs stderr: Max brk space used 0
BraseroGrowisofs stderr: 183 extents written (0 MB)
BraseroGrowisofs stderr: :-[ PERFORM OPC failed with SK=2h/CANNOT WRITE MEDIUM - INCOMPATIBLE FORMAT]: Wrong medium type
BraseroGrowisofs stderr: /dev/sr1: "Current Write Speed" is 4.1x1352KBps.
BraseroGrowisofs stderr: :-[ WRITE@LBA=0h failed with SK=2h/CANNOT WRITE MEDIUM - INCOMPATIBLE FORMAT]: Wrong medium type
BraseroGrowisofs stderr: :-( media is not formatted or unsupported.
BraseroGrowisofs stdout: HUP
BraseroGrowisofs stderr: :-( write failed: Wrong medium type
BraseroGrowisofs stderr: HUP
BraseroGrowisofs process finished with status 124
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
	error		= 0
	message	= "no message"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
Session error : unknown (brasero_burn_record brasero-burn.c:2811)
```

---

### Post by RyanRebirth on 2010-08-20
software center =DeVeDe    to convert to iso's
If you are using brasero make sure to go into Brasero>edit>plugins  and turn off image checksum plugins...

---

