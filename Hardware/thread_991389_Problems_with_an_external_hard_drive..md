---
title: "Problems with an external hard drive."
date: 2008-11-23
forum: Hardware
---

### Post by Toadofsky on 2008-11-23
Hi, new to the forums, and new to Ubuntu. So I've needed an external hard drive for some time, and so I bought a simpletech 160 gb usb mini hard drive. And it brings up this message when it tries to load it...
[B]
Unable to mount SignatureMini

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.[/B]


Is there any way to get this to run on linux, and to also be possible to plug up to xp/vista should I ever have to plug it up elsewhere?

---

### Post by Mewshi on 2008-11-23
It's a mounting error.

First, try mounting it manually.

If that doesn't work, do us a favor and post what happens when you put 'dmesg' into a terminal.

These should both be *very* helpful; if not to you, then to those of us who will try to help :)

---

### Post by Toadofsky on 2008-11-23
> **Mewshi said:**
> It's a mounting error.

First, try mounting it manually.

If that doesn't work, do us a favor and post what happens when you put 'dmesg' into a terminal.

These should both be *very* helpful; if not to you, then to those of us who will try to help :)

So, you'll probably laugh, 

how do I mount it manually?

---

### Post by Mewshi on 2008-11-23
Well, how about posting the results from dmesg for us? :)  That will help us.  And no, it's not something I'll laugh at.  Trust me.

I used to be a total noob, too :)

---

### Post by Toadofsky on 2008-11-23
[    0.568758] TCP reno registered
[    0.572347] NET: Registered protocol family 1
[    0.572488] checking if image is initramfs... it is
[    1.016286] Switched to high resolution mode on CPU 1
[    1.020066] Switched to high resolution mode on CPU 0
[    1.231498] Freeing initrd memory: 7979k freed
[    1.232929] audit: initializing netlink socket (disabled)
[    1.232951] type=2000 audit(1227453232.229:1): initialized
[    1.237606] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.241612] VFS: Disk quotas dquot_6.5.1
[    1.241763] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.241921] msgmni has been set to 1003
[    1.242139] io scheduler noop registered
[    1.242143] io scheduler anticipatory registered
[    1.242146] io scheduler deadline registered
[    1.242168] io scheduler cfq registered (default)
[    9.240013] pci 0000:00:1d.7: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[    9.240158] pci 0000:01:00.0: Boot video device
[    9.240845] isapnp: Scanning for PnP cards...
[    9.594444] isapnp: No Plug & Play device found
[    9.663612] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    9.663786] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    9.664965] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    9.668469] brd: module loaded
[    9.668591] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    9.668956] PNP: No PS/2 controller found. Probing ports directly.
[    9.672022] serio: i8042 KBD port at 0x60,0x64 irq 1
[    9.672033] serio: i8042 AUX port at 0x60,0x64 irq 12
[    9.680234] mice: PS/2 mouse device common for all mice
[    9.680531] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    9.680558] rtc0: alarms up to one month, hpet irqs
[    9.680817] EISA: Probing bus 0 at eisa.0
[    9.680860] EISA: Detected 0 cards.
[    9.680864] cpuidle: using governor ladder
[    9.680867] cpuidle: using governor menu
[    9.681634] TCP cubic registered
[    9.681679] Using IPI No-Shortcut mode
[    9.682071] registered taskstats version 1
[    9.682227]   Magic number: 0:518:235
[    9.682264] tty ttyv5: hash matches
[    9.682376] rtc_cmos 00:02: setting system clock to 2008-11-23 15:14:01 UTC (1227453241)
[    9.682381] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    9.682383] EDD information not available.
[    9.682768] Freeing unused kernel memory: 424k freed
[    9.682824] Write protecting the kernel text: 2576k
[    9.682860] Write protecting the kernel read-only data: 936k
[    9.849995] fuse init (API version 7.9)
[    9.893812] processor ACPI0007:00: registered as cooling_device0
[    9.893989] processor ACPI0007:01: registered as cooling_device1
[   10.172722] usbcore: registered new interface driver usbfs
[   10.172768] usbcore: registered new interface driver hub
[   10.196107] usbcore: registered new device driver usb
[   10.205555] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[   10.205576] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[   10.205583] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   10.205675] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[   10.209614] ehci_hcd 0000:00:1d.7: debug port 1
[   10.209624] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[   10.209647] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfebffc00
[   10.213721] USB Universal Host Controller Interface driver v3.0
[   10.239267] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   10.239532] usb usb1: configuration #1 chosen from 1 choice
[   10.239585] hub 1-0:1.0: USB hub found
[   10.239602] hub 1-0:1.0: 8 ports detected
[   10.448661] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.448679] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[   10.448687] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   10.448770] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[   10.448820] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000e000
[   10.449081] usb usb2: configuration #1 chosen from 1 choice
[   10.449152] hub 2-0:1.0: USB hub found
[   10.449173] hub 2-0:1.0: 2 ports detected
[   10.513747] No dock devices found.
[   10.521071] 8139too Fast Ethernet driver 0.9.28
[   10.561894] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   10.561916] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[   10.561923] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   10.561993] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[   10.562039] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e400
[   10.562388] usb usb3: configuration #1 chosen from 1 choice
[   10.562454] hub 3-0:1.0: USB hub found
[   10.562476] hub 3-0:1.0: 2 ports detected
[   10.582576] SCSI subsystem initialized
[   10.620081] libata version 3.00 loaded.
[   10.772692] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   10.772710] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[   10.772717] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   10.772789] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[   10.772838] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e800
[   10.773138] usb usb4: configuration #1 chosen from 1 choice
[   10.773210] hub 4-0:1.0: USB hub found
[   10.773235] hub 4-0:1.0: 2 ports detected
[   10.887302] usb 3-2: new low speed USB device using uhci_hcd and address 2
[   10.984708] uhci_hcd 0000:00:1d.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.984730] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[   10.984739] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   10.984823] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[   10.984866] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000ec00
[   10.985186] usb usb5: configuration #1 chosen from 1 choice
[   10.985259] hub 5-0:1.0: USB hub found
[   10.985279] hub 5-0:1.0: 2 ports detected
[   11.077387] usb 3-2: configuration #1 chosen from 1 choice
[   11.197778] ata_piix 0000:00:1f.1: version 2.12
[   11.197801] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[   11.197815] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   11.197900] ata_piix 0000:00:1f.1: setting latency timer to 64
[   11.198092] scsi0 : ata_piix
[   11.198365] scsi1 : ata_piix
[   11.202198] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[   11.202206] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[   11.204605] usb 4-1: new low speed USB device using uhci_hcd and address 2
[   11.368588] ata1.00: ATA-7: Maxtor 6Y160P0, YAR41BW0, max UDMA/133
[   11.368597] ata1.00: 320173056 sectors, multi 16: LBA48 
[   11.375039] usb 4-1: configuration #1 chosen from 1 choice
[   11.384475] ata1.00: configured for UDMA/100
[   11.488019] usb 5-1: new low speed USB device using uhci_hcd and address 2
[   11.553306] ata2.00: ATAPI: RICOH   DVD+RW MP5240A, 1.11, max UDMA/33
[   11.553328] ata2.01: ATAPI: IDE-DVD ROM 16x, HD09, max UDMA/33
[   11.568222] ata2.00: configured for UDMA/33
[   11.584262] ata2.01: configured for UDMA/33
[   11.584430] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6Y160P0   YAR4 PQ: 0 ANSI: 5
[   11.586557] scsi 1:0:0:0: CD-ROM            RICOH    DVD+RW MP5240A   1.11 PQ: 0 ANSI: 5
[   11.587011] scsi 1:0:1:0: CD-ROM            IDE-DVD  ROM 16x          HD09 PQ: 0 ANSI: 5
[   11.587291] ata_piix 0000:00:1f.2: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   11.587302] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[   11.587380] ata_piix 0000:00:1f.2: setting latency timer to 64
[   11.587525] scsi2 : ata_piix
[   11.587676] scsi3 : ata_piix
[   11.587785] ata3: SATA max UDMA/133 cmd 0xd400 ctl 0xd000 bmdma 0xc400 irq 18
[   11.587790] ata4: SATA max UDMA/133 cmd 0xcc00 ctl 0xc800 bmdma 0xc408 irq 18
[   11.660459] usb 5-1: configuration #1 chosen from 1 choice
[   11.772022] usb 5-2: new full speed USB device using uhci_hcd and address 3
[   11.918802] 8139too 0000:02:0f.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   11.919830] eth0: RealTek RTL8139 at 0xb400, 00:0e:a6:1b:be:20, IRQ 19
[   11.919833] eth0:  Identified 8139 chip type 'RTL-8101'
[   11.919932] ohci1394 0000:02:0e.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   11.969788] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[feaff000-feaff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   11.969958] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   12.005148] usb 5-2: configuration #1 chosen from 1 choice
[   12.006020] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[   12.006139] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[   12.006237] scsi 1:0:1:0: Attached scsi generic sg2 type 5
[   12.008483] usbcore: registered new interface driver hiddev
[   12.023604] input: BTC USB Multimedia Cordless Kit   as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input1
[   12.053474] input,hidraw0: USB HID v1.00 Keyboard [BTC USB Multimedia Cordless Kit  ] on usb-0000:00:1d.1-2
[   12.053806] Driver 'sd' needs updating - please use bus_type methods
[   12.054005] sd 0:0:0:0: [sda] 320173056 512-byte hardware sectors (163929 MB)
[   12.054056] sd 0:0:0:0: [sda] Write Protect is off
[   12.054062] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   12.054142] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   12.054280] sd 0:0:0:0: [sda] 320173056 512-byte hardware sectors (163929 MB)
[   12.054314] sd 0:0:0:0: [sda] Write Protect is off
[   12.054319] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   12.054392] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   12.054402]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   12.069212]  sda1 sda2 sda3 < sda5 sda6 >
[   12.097513] sd 0:0:0:0: [sda] Attached SCSI disk
[   12.102099] input: BTC USB Multimedia Cordless Kit   as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.1/input/input2
[   12.107716] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   12.107725] Uniform CD-ROM driver Revision: 3.20
[   12.107901] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   12.112277] sr1: scsi3-mmc drive: 0x/40x cd/rw xa/form2 cdda tray
[   12.112462] sr 1:0:1:0: Attached scsi CD-ROM sr1
[   12.151805] input,hiddev96,hidraw1: USB HID v1.00 Mouse [BTC USB Multimedia Cordless Kit  ] on usb-0000:00:1d.1-2
[   12.313960] input: USB Mouse as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input3
[   12.314480] input,hidraw2: USB HID v1.10 Mouse [USB Mouse] on usb-0000:00:1d.2-1
[   12.338866] input: HP EverestFBB as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/input/input4
[   12.339373] input,hiddev97,hidraw3: USB HID v1.10 Device [HP EverestFBB] on usb-0000:00:1d.3-1
[   12.340143] usbcore: registered new interface driver usbhid
[   12.340147] usbcore: registered new interface driver libusual
[   12.340156] usbhid: v2.6:USB HID core driver
[   12.385890] Initializing USB Mass Storage driver...
[   12.386623] scsi4 : SCSI emulation for USB Mass Storage devices
[   12.387565] usbcore: registered new interface driver usb-storage
[   12.387573] USB Mass Storage support registered.
[   12.388223] usb-storage: device found at 3
[   12.388231] usb-storage: waiting for device to settle before scanning
[   12.428372] PM: Starting manual resume from disk
[   12.428378] PM: Resume from partition 8:5
[   12.428381] PM: Checking hibernation image.
[   12.428579] PM: Resume from disk failed.
[   12.487232] kjournald starting.  Commit interval 5 seconds
[   12.487256] EXT3-fs: mounted filesystem with ordered data mode.
[   13.240275] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e01800004b7e15]
[   17.389967] usb-storage: device scan complete
[   17.392929] scsi 4:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[   17.395920] scsi 4:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[   17.398922] scsi 4:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[   17.401922] scsi 4:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   17.447010] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[   17.447177] sd 4:0:0:0: Attached scsi generic sg3 type 0
[   17.490995] sd 4:0:0:1: [sdc] Attached SCSI removable disk
[   17.491097] sd 4:0:0:1: Attached scsi generic sg4 type 0
[   17.535095] sd 4:0:0:2: [sdd] Attached SCSI removable disk
[   17.535265] sd 4:0:0:2: Attached scsi generic sg5 type 0
[   17.579019] sd 4:0:0:3: [sde] Attached SCSI removable disk
[   17.579189] sd 4:0:0:3: Attached scsi generic sg6 type 0
[   17.651111] udevd version 124 started
[   18.114855] Linux agpgart interface v0.103
[   18.138055] agpgart-intel 0000:00:00.0: Intel 865 Chipset
[   18.149588] agpgart-intel 0000:00:00.0: AGP aperture is 64M @ 0xf8000000
[   18.174334] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   18.204123] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   18.679728] intel_rng: FWH not detected
[   18.846731] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input5
[   18.861272] iTCO_vendor_support: vendor-support=0
[   18.869880] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   18.870329] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   18.870366] iTCO_wdt: No card detected
[   18.873059] ACPI: Power Button (FF) [PWRF]
[   18.873295] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input6
[   18.905080] ACPI: Power Button (CM) [PWRB]
[   19.462393] nvidia: module license 'NVIDIA' taints kernel.
[   19.868740] parport_pc 00:07: reported by Plug and Play ACPI
[   19.868794] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   19.885408] Linux video capture interface: v2.00
[   19.909401] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.909740] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.12  Thu Jul 17 18:11:36 PDT 2008
[   19.987714] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[   19.987800] cx8800 0000:02:0a.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   19.987813] cx88[0]/0: Can't get MMIO memory @ 0x0, subsystem: 1043:4803
[   19.987831] cx8800: probe of 0000:02:0a.0 failed with error -22
[   21.311143] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   21.999117] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   21.999147] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   22.325052] intel8x0_measure_ac97_clock: measured 56361 usecs
[   22.325059] intel8x0: clocking to 48000
[   24.639032] lp0: using parport0 (interrupt-driven).
[   24.847503] Adding 1950440k swap on /dev/sda5.  Priority:-1 extents:1 across:1950440k
[   25.421894] EXT3 FS on sda2, internal journal
[   26.301974] kjournald starting.  Commit interval 5 seconds
[   26.302400] EXT3 FS on sda6, internal journal
[   26.302408] EXT3-fs: mounted filesystem with ordered data mode.
[   26.681218] type=1505 audit(1227474858.185:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4193
[   26.867535] type=1505 audit(1227474858.369:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4198
[   26.867853] type=1505 audit(1227474858.369:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4198
[   26.933797] type=1505 audit(1227474858.437:5): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=4202
[   26.975151] type=1505 audit(1227474858.477:6): operation="profile_load" name="/usr/sbin/mysqld-akonadi" name2="default" pid=4206
[   27.333323] ip_tables: (C) 2000-2006 Netfilter Core Team
[   27.953893] ACPI: WMI: Mapper loaded
[   28.990816] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   29.118195] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   29.118208] apm: disabled - APM is not SMP safe.
[   29.272041] ppdev: user-space parallel port driver
[   32.513425] Bluetooth: Core ver 2.13
[   32.514462] NET: Registered protocol family 31
[   32.514477] Bluetooth: HCI device and connection manager initialized
[   32.514484] Bluetooth: HCI socket layer initialized
[   32.553931] Bluetooth: L2CAP ver 2.11
[   32.553939] Bluetooth: L2CAP socket layer initialized
[   32.569411] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   32.569418] Bluetooth: BNEP filters: protocol multicast
[   32.600643] Bridge firewalling registered
[   32.601092] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   32.614357] Bluetooth: RFCOMM socket layer initialized
[   32.616026] Bluetooth: RFCOMM TTY layer initialized
[   32.616041] Bluetooth: RFCOMM ver 1.10
[   32.622667] Bluetooth: SCO (Voice Link) ver 0.6
[   32.622687] Bluetooth: SCO socket layer initialized
[   34.986305] agpgart-intel 0000:00:00.0: AGP 3.0 bridge
[   34.986326] agpgart-intel 0000:00:00.0: putting AGP V3 device into 8x mode
[   34.986373] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
[   36.757519] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   37.187869] NET: Registered protocol family 17
[   71.676282] NET: Registered protocol family 10
[   71.677503] lo: Disabled Privacy Extensions
[   82.132015] eth0: no IPv6 routers present
[  132.760199] ppdev0: registered pardevice
[  132.808099] ppdev0: unregistered pardevice
[  132.972455] ppdev0: registered pardevice
[  133.020382] ppdev0: unregistered pardevice
[  133.552450] ppdev0: registered pardevice
[  133.603108] ppdev0: unregistered pardevice
[ 5477.087042] PM: Syncing filesystems ... done.
[ 5477.087132] PM: Preparing system for mem sleep
[ 5477.087138] Freezing user space processes ... (elapsed 0.00 seconds) done.
[ 5477.088810] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[ 5477.088925] PM: Entering mem sleep
[ 5477.088929] Suspending console(s) (use no_console_suspend to debug)
[ 5477.124028] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[ 5477.248262] sd 0:0:0:0: [sda] Stopping disk
[ 5477.384995] parport_pc 00:07: disabled
[ 5477.385361] serial 00:05: disabled
[ 5477.385455] ACPI handle has no context!
[ 5477.400086] ACPI handle has no context!
[ 5477.400101] NVRM: RmPowerManagement: 4
[ 5477.483189] Intel ICH 0000:00:1f.5: PCI INT B disabled
[ 5477.483363] ata_piix 0000:00:1f.2: PCI INT A disabled
[ 5477.483476] ata_piix 0000:00:1f.1: PCI INT A disabled
[ 5477.483576] ehci_hcd 0000:00:1d.7: PCI INT D disabled
[ 5477.496057] uhci_hcd 0000:00:1d.3: PCI INT A disabled
[ 5477.496088] uhci_hcd 0000:00:1d.2: PCI INT C disabled
[ 5477.496118] uhci_hcd 0000:00:1d.1: PCI INT B disabled
[ 5477.496149] uhci_hcd 0000:00:1d.0: PCI INT A disabled
[ 5477.496237] PM: suspend devices took 0.408 seconds
[ 5477.496286] ACPI: Preparing to enter system sleep state S3
[ 5477.496819] Disabling non-boot CPUs ...
[ 5477.600033] CPU 1 is now offline
[ 5477.600037] SMP alternatives: switching to UP code
[ 5477.611652] CPU0 attaching NULL sched-domain.
[ 5477.611656] CPU1 attaching NULL sched-domain.
[ 5477.611698] CPU0 attaching sched-domain:
[ 5477.611701]  domain 0: span 0 level CPU
[ 5477.611704]   groups: 0
[ 5477.611939] CPU1 is down
[ 5477.611939] Back to C!
[ 5477.611939] Force enabled HPET at resume
[ 5477.612250] Enabling non-boot CPUs ...
[ 5477.612496] SMP alternatives: switching to SMP code
[ 5477.624176] Booting processor 1/1 ip 6000
[ 5477.500972] Initializing CPU#1
[ 5477.500972] Calibrating delay using timer specific routine.. 6000.23 BogoMIPS (lpj=12000478)
[ 5477.500972] CPU: Trace cache: 12K uops, L1 D cache: 8K
[ 5477.500972] CPU: L2 cache: 512K
[ 5477.500972] CPU: Physical Processor ID: 0
[ 5477.712277] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 09
[ 5477.712298] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[ 5477.732384] CPU0 attaching NULL sched-domain.
[ 5477.736013] Switched to high resolution mode on CPU 1
[ 5477.740019] CPU0 attaching sched-domain:
[ 5477.740023]  domain 0: span 0-1 level SIBLING
[ 5477.740025]   groups: 0 1
[ 5477.740030]   domain 1: span 0-1 level CPU
[ 5477.740032]    groups: 0-1
[ 5477.740037] CPU1 attaching sched-domain:
[ 5477.740039]  domain 0: span 0-1 level SIBLING
[ 5477.740041]   groups: 1 0
[ 5477.740044]   domain 1: span 0-1 level CPU
[ 5477.740046]    groups: 0-1
[ 5477.740529] CPU1 is up
[ 5477.740534] ACPI: Waking up from system sleep state S3
[ 5477.741137] pm_op(): pci_pm_resume+0x0/0x80 returns -16
[ 5477.741147] PM: Device 0000:00:00.0 failed to resume: error -16
[ 5477.741180] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 5477.741186] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[ 5477.741227] usb usb2: root hub lost power or was reset
[ 5477.741243] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[ 5477.741248] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[ 5477.741287] usb usb3: root hub lost power or was reset
[ 5477.741313] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[ 5477.741318] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[ 5477.741358] usb usb4: root hub lost power or was reset
[ 5477.741381] uhci_hcd 0000:00:1d.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 5477.741386] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[ 5477.741426] usb usb5: root hub lost power or was reset
[ 5477.756017] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[ 5477.756023] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[ 5477.756084] pci 0000:00:1e.0: restoring config space at offset 0x7 (was 0xa280b0b0, writing 0x8280b0b0)
[ 5477.756103] pci 0000:00:1e.0: setting latency timer to 64
[ 5477.756142] ata_piix 0000:00:1f.1: restoring config space at offset 0x9 (was 0x0, writing 0x30000000)
[ 5477.756156] ata_piix 0000:00:1f.1: restoring config space at offset 0x1 (was 0x2880005, writing 0x2880007)
[ 5477.756167] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 5477.756171] ata_piix 0000:00:1f.1: setting latency timer to 64
[ 5477.756233] ata_piix 0000:00:1f.2: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 5477.756241] ata_piix 0000:00:1f.2: setting latency timer to 64
[ 5477.756467] Intel ICH 0000:00:1f.5: restoring config space at offset 0x1 (was 0x2900007, writing 0x2900003)
[ 5477.756485] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[ 5477.756493] Intel ICH 0000:00:1f.5: setting latency timer to 64
[ 5477.766169] NVRM: RmPowerManagement: 5
[ 5477.934355] ata2.01: ACPI cmd ef/03:42:00:00:00:b0 filtered out
[ 5477.934361] ata2.01: ACPI cmd ef/03:0c:00:00:00:b0 filtered out
[ 5478.077368] ata2.00: ACPI cmd ef/03:42:00:00:00:a0 filtered out
[ 5478.077373] ata2.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[ 5478.093299] ata2.00: configured for UDMA/33
[ 5478.109291] ata2.01: configured for UDMA/33
[ 5478.736385] pci 0000:02:0a.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[ 5478.752025] ohci1394 0000:02:0e.0: restoring config space at offset 0xf (was 0x4030100, writing 0x403010a)
[ 5478.752043] ohci1394 0000:02:0e.0: restoring config space at offset 0x5 (was 0x0, writing 0xfeaf8000)
[ 5478.752049] ohci1394 0000:02:0e.0: restoring config space at offset 0x4 (was 0x0, writing 0xfeaff000)
[ 5478.752055] ohci1394 0000:02:0e.0: restoring config space at offset 0x3 (was 0x0, writing 0x4004)
[ 5478.752062] ohci1394 0000:02:0e.0: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100116)
[ 5478.801696] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[feaff000-feaff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[ 5478.803195] serial 00:05: activated
[ 5478.804655] parport_pc 00:07: activated
[ 5479.876018] usb 3-2: reset low speed USB device using uhci_hcd and address 2
[ 5480.452015] usb 4-1: reset low speed USB device using uhci_hcd and address 2
[ 5480.761779] sd 0:0:0:0: [sda] Starting disk
[ 5482.812019] ata1: link is slow to respond, please be patient (ready=0)
[ 5483.704294] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
[ 5483.704297] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[ 5483.704444] ata1.00: ACPI cmd c6/00:10:00:00:00:a0 succeeded
[ 5483.729414] ata1.00: configured for UDMA/100
[ 5483.753407] ata1.00: configured for UDMA/100
[ 5483.753411] ata1: EH complete
[ 5483.773129] sd 0:0:0:0: [sda] 320173056 512-byte hardware sectors (163929 MB)
[ 5483.773196] sd 0:0:0:0: [sda] Write Protect is off
[ 5483.773200] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 5483.773262] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 5483.773323] sd 0:0:0:0: [sda] 320173056 512-byte hardware sectors (163929 MB)
[ 5483.773355] sd 0:0:0:0: [sda] Write Protect is off
[ 5483.773360] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 5483.773420] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 5484.032016] usb 5-1: reset low speed USB device using uhci_hcd and address 2
[ 5484.456014] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 5484.615845] PM: resume devices took 6.872 seconds
[ 5484.615855] ------------[ cut here ]------------
[ 5484.615858] WARNING: at /build/buildd/linux-2.6.27/kernel/power/main.c:176 suspend_test_finish+0x74/0x80()
[ 5484.615862] Modules linked in: ipv6 af_packet binfmt_misc sco rfcomm bridge stp bnep l2cap bluetooth ppdev speedstep_lib cpufreq_powersave cpufreq_ondemand cpufreq_stats freq_table cpufreq_conservative cpufreq_userspace sbs sbshc container wmi pci_slot video output battery iptable_filter ip_tables x_tables ac sbp2 lp snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi psmouse snd_seq_midi_event serio_raw snd_seq snd_timer snd_seq_device snd pcspkr soundcore snd_page_alloc joydev evdev cx8800 cx88xx ir_common i2c_algo_bit tveeprom videodev parport_pc parport v4l1_compat compat_ioctl32 v4l2_common videobuf_dma_sg videobuf_core btcx_risc nvidia(P) i2c_core iTCO_wdt iTCO_vendor_support button shpchp pci_hotplug intel_agp agpgart ext3 jbd mbcache usb_storage libusual sr_mod sd_mod crc_t10dif cdrom sg pata_acpi ata_generic 8139cp usbhid hid ata_piix libata scsi_mod ohci1394 8139too mii dock ieee1394 uhci_hcd ehci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[ 5484.615948] Pid: 6250, comm: pm-suspend Tainted: P          2.6.27-7-generic #1
[ 5484.615952]  [<c037c406>] ? printk+0x1d/0x1f
[ 5484.615959]  [<c0131de9>] warn_on_slowpath+0x59/0x90
[ 5484.615967]  [<c014d255>] ? sched_clock_cpu+0xd5/0x170
[ 5484.615972]  [<c014c0af>] ? down_trylock+0x2f/0x40
[ 5484.615977]  [<c01324c2>] ? try_acquire_console_sem+0x12/0x40
[ 5484.615982]  [<c024e580>] ? kobject_put+0x20/0x50
[ 5484.615987]  [<c015d204>] suspend_test_finish+0x74/0x80
[ 5484.615991]  [<c015d2f6>] suspend_devices_and_enter+0xe6/0x190
[ 5484.615995]  [<c015d571>] enter_state+0xd1/0x100
[ 5484.615999]  [<c015d625>] state_store+0x85/0xd0
[ 5484.616034]  [<c015d5a0>] ? state_store+0x0/0xd0
[ 5484.616040]  [<c024e444>] kobj_attr_store+0x24/0x30
[ 5484.616043]  [<c01ff4c7>] sysfs_write_file+0x97/0x100
[ 5484.616048]  [<c01b24c0>] vfs_write+0xa0/0x110
[ 5484.616052]  [<c01ff430>] ? sysfs_write_file+0x0/0x100
[ 5484.616056]  [<c01b2602>] sys_write+0x42/0x70
[ 5484.616060]  [<c0103f7b>] sysenter_do_call+0x12/0x2f
[ 5484.616064]  [<c0370000>] ? default_device_exit+0x60/0xb0
[ 5484.616069]  =======================
[ 5484.616071] ---[ end trace 4b04122a5d120792 ]---
[ 5484.616202] PM: Finishing wakeup.
[ 5484.616205] Restarting tasks ... done.
[ 5485.614760] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 5495.924014] eth0: no IPv6 routers present
[ 6007.548027] usb 1-1: new high speed USB device using ehci_hcd and address 6
[ 6007.695386] usb 1-1: configuration #1 chosen from 1 choice
[ 6007.696631] scsi5 : SCSI emulation for USB Mass Storage devices
[ 6007.699112] usb-storage: device found at 6
[ 6007.699130] usb-storage: waiting for device to settle before scanning
[ 6012.696201] usb-storage: device scan complete
[ 6012.696678] scsi 5:0:0:0: Direct-Access     WDC WD16 00BEVS-00RST0    04.0 PQ: 0 ANSI: 0
[ 6012.708037] sd 5:0:0:0: [sdf] 312581808 512-byte hardware sectors (160042 MB)
[ 6012.709435] sd 5:0:0:0: [sdf] Write Protect is off
[ 6012.709449] sd 5:0:0:0: [sdf] Mode Sense: 03 00 00 00
[ 6012.709455] sd 5:0:0:0: [sdf] Assuming drive cache: write through
[ 6012.732292] sd 5:0:0:0: [sdf] 312581808 512-byte hardware sectors (160042 MB)
[ 6012.735544] sd 5:0:0:0: [sdf] Write Protect is off
[ 6012.735557] sd 5:0:0:0: [sdf] Mode Sense: 03 00 00 00
[ 6012.735563] sd 5:0:0:0: [sdf] Assuming drive cache: write through
[ 6012.740595]  sdf: sdf1
[ 6012.797347] sd 5:0:0:0: [sdf] Attached SCSI disk
[ 6012.797626] sd 5:0:0:0: Attached scsi generic sg7 type 0





Yeah, that's ALOT of info.

---

### Post by Mewshi on 2008-11-23
Now, do you see, third line up from the bottom, where it says 'sdf1'?  That's your device file :)  (Odd concept, I know)

So, what you'll want to do is use "sudo mount /dev/sdf1 /path/to/mount"

If that doesn't work, let us know :)

---

### Post by Toadofsky on 2008-11-23
keenan@TheExecutor:~$ sudo mount/dev/sdf1/path/to/mount
[sudo] password for keenan: 
sudo: mount/dev/sdf1/path/to/mount: command not found

I guessed I missed something somewhere. I'm getting close right?:rolleyes:

---

### Post by Mewshi on 2008-11-23
mount and /dev need a space.
you need to have "sudo mount /dev..." understand? :)

---

### Post by Toadofsky on 2008-11-23
> **Mewshi said:**
> mount and /dev need a space.
you need to have "sudo mount /dev..." understand? :)

Oh, duh, sorry.

So I fixed that, and here's what I get...

mount: can't find /dev/sdf1/path/to/mount in /etc/fstab or /etc/mtab
:-s

---

### Post by Mewshi on 2008-11-23
Also, um... dude, the /path/to/mount is where you want to mount it -_-

So, if you want to mount it in, say, your home folder, do this

"mkdir ~/drive" This will make a folder in your home directory called "drive"

then you would use "sudo mount /dev/sdf1 /home/(your user name here)/drive"  :)

---

### Post by Toadofsky on 2008-11-23
Okay so here's what I did.

keenan@TheExecutor:~$ mkdir ~/drive
keenan@TheExecutor:~$ sudo mount /dev/sdf1/home/keenan/drive
mount: can't find /dev/sdf1/home/keenan/drive in /etc/fstab or /etc/mtab
keenan@TheExecutor:~$ sudo mount /dev/sdf1/home/keenan/signaturedrive
mount: can't find /dev/sdf1/home/keenan/signaturedrive in /etc/fstab or /etc/mtab
keenan@TheExecutor:~$ sudo mount /dev/sdf1/home/keenan/signaturemini
mount: can't find /dev/sdf1/home/keenan/signaturemini in /etc/fstab or /etc/mtab


I tried to see what would happen with typing the name of the drive, but nothing.

(I'm sorry, I know this sounds so noob, but, well, that's what I am with this right now)

---

### Post by Mewshi on 2008-11-23
You need to have a space between /dev/sdf1 and /home...

It's two separate locations

Here's how the mount command works:

mount (command name) (any options you want) /dev/sdf1 (device you want to mount) /home/keenan/drive (location you want to mount it.

---

### Post by Toadofsky on 2008-11-23
Okay, I'm starting to understand this now... I think...

Here's what I typed, here's what I've got so far...

keenan@TheExecutor:~$ sudo mount / dev/ sdf1/ home/keenan
[sudo] password for keenan: 
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

I know I'm probably getting on your nerves here on something so simple.

---

### Post by Mewshi on 2008-11-23
Just copy and paste everything I have in quotations -_-

"sudo mount /dev/sdf1 /home/keenan/drive"

---

### Post by Toadofsky on 2008-11-23
I'm so sorry, I know this is annoying.

keenan@TheExecutor:~$ sudo mount /dev/sdf1 /home/keenan/drive
$LogFile indicates unclean shutdown (0, 1)
Failed to mount '/dev/sdf1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdf1 /home/keenan/drive -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdf1 /home/keenan/drive ntfs-3g force 0 0
keenan@TheExecutor:~$ mount -t ntfs-3g /dev/sdf1 /home/keenan/drive -o force
mount: only root can do that

It says it had an unclean shutdown, so I tried to force it to close it. and well, you see what I got from that...

:(

---

### Post by Mewshi on 2008-11-23
try your command again, but put sudo in front

---

### Post by Toadofsky on 2008-11-23
$LogFile indicates unclean shutdown (0, 1)
WARNING: Forced mount, reset $LogFile.
keenan@TheExecutor:~$ sudo mount /dev/sdf1 /home/keenan/drive
fuse: mount failed: Device or resource busy

So you see what I tried doing... What does LogFile mean?

---

### Post by Toadofsky on 2008-11-23
Never mind! It's working NOW!!! WOOOT! Thank you sir!!

---

### Post by Mewshi on 2008-11-23
Glad to hear it :)

---

