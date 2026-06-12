---
title: "Ubuntu failed to start"
date: 2008-10-05
forum: General Help
---

### Post by Nabanna on 2008-10-05
After Updating Ubuntu to v8.04.1 yesterday, when i started my PC today just after loading screen it appeared to be freezed, nothing happened for nearly 10 minutes just a black screen, then i had to power off my PC :shock: .
I got this problem two consecutive times but third time PC started normally..????
What could have been wrong.. :confused: ???
It has been working absolutely fine since install but this problem and after this problem my PC seems slower..!!!

---

### Post by tonybaqain on 2008-10-05
please use this and paste results here 
```
tail -200 /var/log/messages
```
and then
```
dmesg | tail
```

---

### Post by Nabanna on 2008-10-05
> **tonybaqain said:**
>  
```
tail -200 /var/log/messages
```


```
Oct  5 17:09:15 illusion-desktop kernel: [   17.482487] system 00:01: ioport range 0x294-0x297 has been reserved
Oct  5 17:09:15 illusion-desktop kernel: [   17.482504] system 00:0b: ioport range 0x400-0x4bf could not be reserved
Oct  5 17:09:15 illusion-desktop kernel: [   17.512988] PCI: Bridge: 0000:00:1e.0
Oct  5 17:09:15 illusion-desktop kernel: [   17.512992]   IO window: c000-cfff
Oct  5 17:09:15 illusion-desktop kernel: [   17.512998]   MEM window: ec000000-edffffff
Oct  5 17:09:15 illusion-desktop kernel: [   17.513002]   PREFETCH window: disabled.
Oct  5 17:09:15 illusion-desktop kernel: [   17.513032] NET: Registered protocol family 2
Oct  5 17:09:15 illusion-desktop kernel: [   17.550387] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
Oct  5 17:09:15 illusion-desktop kernel: [   17.550669] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
Oct  5 17:09:15 illusion-desktop kernel: [   17.550803] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
Oct  5 17:09:15 illusion-desktop kernel: [   17.550935] TCP: Hash tables configured (established 16384 bind 16384)
Oct  5 17:09:15 illusion-desktop kernel: [   17.550938] TCP reno registered
Oct  5 17:09:15 illusion-desktop kernel: [   17.562420] checking if image is initramfs... it is
Oct  5 17:09:15 illusion-desktop kernel: [   18.206733] Freeing initrd memory: 7324k freed
Oct  5 17:09:15 illusion-desktop kernel: [   18.207552] audit: initializing netlink socket (disabled)
Oct  5 17:09:15 illusion-desktop kernel: [   18.207580] audit(1223226531.284:1): initialized
Oct  5 17:09:15 illusion-desktop kernel: [   18.210128] VFS: Disk quotas dquot_6.5.1
Oct  5 17:09:15 illusion-desktop kernel: [   18.210223] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Oct  5 17:09:15 illusion-desktop kernel: [   18.210410] io scheduler noop registered
Oct  5 17:09:15 illusion-desktop kernel: [   18.210412] io scheduler anticipatory registered
Oct  5 17:09:15 illusion-desktop kernel: [   18.210414] io scheduler deadline registered
Oct  5 17:09:15 illusion-desktop kernel: [   18.210429] io scheduler cfq registered (default)
Oct  5 17:09:15 illusion-desktop kernel: [   18.210855] isapnp: Scanning for PnP cards...
Oct  5 17:09:15 illusion-desktop kernel: [   18.564279] isapnp: No Plug & Play device found
Oct  5 17:09:15 illusion-desktop kernel: [   18.599916] Real Time Clock Driver v1.12ac
Oct  5 17:09:15 illusion-desktop kernel: [   18.600067] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Oct  5 17:09:15 illusion-desktop kernel: [   18.600208] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Oct  5 17:09:15 illusion-desktop kernel: [   18.601140] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Oct  5 17:09:15 illusion-desktop kernel: [   18.602153] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Oct  5 17:09:15 illusion-desktop kernel: [   18.602235] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Oct  5 17:09:15 illusion-desktop kernel: [   18.602369] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Oct  5 17:09:15 illusion-desktop kernel: [   18.604794] serio: i8042 KBD port at 0x60,0x64 irq 1
Oct  5 17:09:15 illusion-desktop kernel: [   18.604800] serio: i8042 AUX port at 0x60,0x64 irq 12
Oct  5 17:09:15 illusion-desktop kernel: [   18.608239] mice: PS/2 mouse device common for all mice
Oct  5 17:09:15 illusion-desktop kernel: [   18.608392] EISA: Probing bus 0 at eisa.0
Oct  5 17:09:15 illusion-desktop kernel: [   18.608431] EISA: Detected 0 cards.
Oct  5 17:09:15 illusion-desktop kernel: [   18.608435] cpuidle: using governor ladder
Oct  5 17:09:15 illusion-desktop kernel: [   18.608437] cpuidle: using governor menu
Oct  5 17:09:15 illusion-desktop kernel: [   18.608564] NET: Registered protocol family 1
Oct  5 17:09:15 illusion-desktop kernel: [   18.608602] Using IPI No-Shortcut mode
Oct  5 17:09:15 illusion-desktop kernel: [   18.608643] registered taskstats version 1
Oct  5 17:09:15 illusion-desktop kernel: [   18.608757]   Magic number: 12:267:137
Oct  5 17:09:15 illusion-desktop kernel: [   18.608898] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Oct  5 17:09:15 illusion-desktop kernel: [   18.608900] EDD information not available.
Oct  5 17:09:15 illusion-desktop kernel: [   18.609512] Freeing unused kernel memory: 368k freed
Oct  5 17:09:15 illusion-desktop kernel: [   18.643954] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Oct  5 17:09:15 illusion-desktop kernel: [   18.722472] vesafb: framebuffer at 0xe0000000, mapped to 0xe0080000, using 3750k, total 8000k
Oct  5 17:09:15 illusion-desktop kernel: [   18.722479] vesafb: mode is 800x600x32, linelength=3200, pages=3
Oct  5 17:09:15 illusion-desktop kernel: [   18.722481] vesafb: scrolling: redraw
Oct  5 17:09:15 illusion-desktop kernel: [   18.722484] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
Oct  5 17:09:15 illusion-desktop kernel: [   18.722628] Console: switching to colour frame buffer device 100x37
Oct  5 17:09:15 illusion-desktop kernel: [   18.772390] fb0: VESA VGA frame buffer device
Oct  5 17:09:15 illusion-desktop kernel: [   19.967686] fuse init (API version 7.9)
Oct  5 17:09:15 illusion-desktop kernel: [   19.989545] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Oct  5 17:09:15 illusion-desktop kernel: [   20.583869] usbcore: registered new interface driver usbfs
Oct  5 17:09:15 illusion-desktop kernel: [   20.583904] usbcore: registered new interface driver hub
Oct  5 17:09:15 illusion-desktop kernel: [   20.597730] usbcore: registered new device driver usb
Oct  5 17:09:15 illusion-desktop kernel: [   20.611236] USB Universal Host Controller Interface driver v3.0
Oct  5 17:09:15 illusion-desktop kernel: [   20.611345] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
Oct  5 17:09:15 illusion-desktop kernel: [   20.611365] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Oct  5 17:09:15 illusion-desktop kernel: [   20.611811] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Oct  5 17:09:15 illusion-desktop kernel: [   20.611847] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000d800
Oct  5 17:09:15 illusion-desktop kernel: [   20.612034] usb usb1: configuration #1 chosen from 1 choice
Oct  5 17:09:15 illusion-desktop kernel: [   20.612064] hub 1-0:1.0: USB hub found
Oct  5 17:09:15 illusion-desktop kernel: [   20.612075] hub 1-0:1.0: 2 ports detected
Oct  5 17:09:15 illusion-desktop kernel: [   20.670402] SCSI subsystem initialized
Oct  5 17:09:15 illusion-desktop kernel: [   20.715684] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
Oct  5 17:09:15 illusion-desktop kernel: [   20.715707] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Oct  5 17:09:15 illusion-desktop kernel: [   20.715737] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Oct  5 17:09:15 illusion-desktop kernel: [   20.715768] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000d000
Oct  5 17:09:15 illusion-desktop kernel: [   20.715912] usb usb2: configuration #1 chosen from 1 choice
Oct  5 17:09:15 illusion-desktop kernel: [   20.715939] hub 2-0:1.0: USB hub found
Oct  5 17:09:15 illusion-desktop kernel: [   20.715947] hub 2-0:1.0: 2 ports detected
Oct  5 17:09:15 illusion-desktop kernel: [   20.736664] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Oct  5 17:09:15 illusion-desktop kernel: [   20.819401] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
Oct  5 17:09:15 illusion-desktop kernel: [   20.819424] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Oct  5 17:09:15 illusion-desktop kernel: [   20.819452] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Oct  5 17:09:15 illusion-desktop kernel: [   20.819484] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d400
Oct  5 17:09:15 illusion-desktop kernel: [   20.819635] usb usb3: configuration #1 chosen from 1 choice
Oct  5 17:09:15 illusion-desktop kernel: [   20.819662] hub 3-0:1.0: USB hub found
Oct  5 17:09:15 illusion-desktop kernel: [   20.819670] hub 3-0:1.0: 2 ports detected
Oct  5 17:09:15 illusion-desktop kernel: [   20.867237] Floppy drive(s): fd0 is 2.88M AMI BIOS
Oct  5 17:09:15 illusion-desktop kernel: [   20.886885] FDC 0 is a post-1991 82077
Oct  5 17:09:15 illusion-desktop kernel: [   20.923350] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
Oct  5 17:09:15 illusion-desktop kernel: [   20.923375] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Oct  5 17:09:15 illusion-desktop kernel: [   20.923418] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
Oct  5 17:09:15 illusion-desktop kernel: [   20.927355] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xee080000
Oct  5 17:09:15 illusion-desktop kernel: [   20.942984] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Oct  5 17:09:15 illusion-desktop kernel: [   20.943146] usb usb4: configuration #1 chosen from 1 choice
Oct  5 17:09:15 illusion-desktop kernel: [   20.943178] hub 4-0:1.0: USB hub found
Oct  5 17:09:15 illusion-desktop kernel: [   20.943187] hub 4-0:1.0: 6 ports detected
Oct  5 17:09:15 illusion-desktop kernel: [   21.050655] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
Oct  5 17:09:15 illusion-desktop kernel: [   21.052654] 8139too Fast Ethernet driver 0.9.28
Oct  5 17:09:15 illusion-desktop kernel: [   21.053703] scsi0 : ata_piix
Oct  5 17:09:15 illusion-desktop kernel: [   21.054843] scsi1 : ata_piix
Oct  5 17:09:15 illusion-desktop kernel: [   21.055560] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
Oct  5 17:09:15 illusion-desktop kernel: [   21.055564] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
Oct  5 17:09:15 illusion-desktop kernel: [   21.721591] ata1.00: ATAPI: LITE-ON LTR-48247S, PPB2, max UDMA/33
Oct  5 17:09:15 illusion-desktop kernel: [   21.721620] ata1.01: ATAPI: Optiarc DVD RW AD-7190A, 1.02, max UDMA/66
Oct  5 17:09:15 illusion-desktop kernel: [   21.893168] ata1.00: configured for UDMA/33
Oct  5 17:09:15 illusion-desktop kernel: [   22.080751] ata1.01: configured for UDMA/66
Oct  5 17:09:15 illusion-desktop kernel: [   22.282740] ata2.00: ATA-7: ST3320620A, 3.AAE, max UDMA/100
Oct  5 17:09:15 illusion-desktop kernel: [   22.282745] ata2.00: 625142448 sectors, multi 16: LBA48 
Oct  5 17:09:15 illusion-desktop kernel: [   22.282760] ata2.00: limited to UDMA/33 due to 40-wire cable
Oct  5 17:09:15 illusion-desktop kernel: [   22.349151] ata2.00: configured for UDMA/33
Oct  5 17:09:15 illusion-desktop kernel: [   22.350061] scsi 0:0:0:0: CD-ROM            LITE-ON  LTR-48247S       PPB2 PQ: 0 ANSI: 5
Oct  5 17:09:15 illusion-desktop kernel: [   22.351652] scsi 0:0:1:0: CD-ROM            Optiarc  DVD RW AD-7190A  1.02 PQ: 0 ANSI: 5
Oct  5 17:09:15 illusion-desktop kernel: [   22.352150] scsi 1:0:0:0: Direct-Access     ATA      ST3320620A       3.AA PQ: 0 ANSI: 5
Oct  5 17:09:15 illusion-desktop kernel: [   22.355409] ACPI: PCI Interrupt 0000:01:0d.0[A] -> GSI 23 (level, low) -> IRQ 19
Oct  5 17:09:15 illusion-desktop kernel: [   22.408140] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[19]  MMIO=[ed011000-ed0117ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Oct  5 17:09:15 illusion-desktop kernel: [   22.417974] ACPI: PCI Interrupt 0000:01:0c.0[A] -> GSI 23 (level, low) -> IRQ 19
Oct  5 17:09:15 illusion-desktop kernel: [   22.418698] eth0: RealTek RTL8139 at 0xc400, 00:0c:76:f3:57:e0, IRQ 19
Oct  5 17:09:15 illusion-desktop kernel: [   22.441655] Driver 'sr' needs updating - please use bus_type methods
Oct  5 17:09:15 illusion-desktop kernel: [   22.446933] Driver 'sd' needs updating - please use bus_type methods
Oct  5 17:09:15 illusion-desktop kernel: [   22.448658] sr0: scsi3-mmc drive: 222x/48x writer cd/rw xa/form2 cdda tray
Oct  5 17:09:15 illusion-desktop kernel: [   22.448665] Uniform CD-ROM driver Revision: 3.20
Oct  5 17:09:15 illusion-desktop kernel: [   22.457132] sr1: scsi3-mmc drive: 48x/12x writer dvd-ram cd/rw xa/form2 cdda tray
Oct  5 17:09:15 illusion-desktop kernel: [   22.465727] sd 1:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
Oct  5 17:09:15 illusion-desktop kernel: [   22.465788] sd 1:0:0:0: [sda] Write Protect is off
Oct  5 17:09:15 illusion-desktop kernel: [   22.465816] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct  5 17:09:15 illusion-desktop kernel: [   22.465900] sd 1:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
Oct  5 17:09:15 illusion-desktop kernel: [   22.465914] sd 1:0:0:0: [sda] Write Protect is off
Oct  5 17:09:15 illusion-desktop kernel: [   22.465940] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct  5 17:09:15 illusion-desktop kernel: [   22.465945]  sda:<5>sr 0:0:0:0: Attached scsi generic sg0 type 5
Oct  5 17:09:15 illusion-desktop kernel: [   22.467285] sr 0:0:1:0: Attached scsi generic sg1 type 5
Oct  5 17:09:15 illusion-desktop kernel: [   22.467313] sd 1:0:0:0: Attached scsi generic sg2 type 0
Oct  5 17:09:15 illusion-desktop kernel: [   22.488356]  sda1 sda2 < sda5 sda6 sda7 sda8 sda9 sda10 sda11 >
Oct  5 17:09:15 illusion-desktop kernel: [   22.569392] sd 1:0:0:0: [sda] Attached SCSI disk
Oct  5 17:09:15 illusion-desktop kernel: [   23.105263] Attempting manual resume
Oct  5 17:09:15 illusion-desktop kernel: [   23.133360] kjournald starting.  Commit interval 5 seconds
Oct  5 17:09:15 illusion-desktop kernel: [   23.133381] EXT3-fs: mounted filesystem with ordered data mode.
Oct  5 17:09:15 illusion-desktop kernel: [   31.169086] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Oct  5 17:09:15 illusion-desktop kernel: [   31.216867] iTCO_vendor_support: vendor-support=0
Oct  5 17:09:15 illusion-desktop kernel: [   31.240818] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
Oct  5 17:09:15 illusion-desktop kernel: [   31.241381] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x0460)
Oct  5 17:09:15 illusion-desktop kernel: [   31.241442] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Oct  5 17:09:15 illusion-desktop kernel: [   31.424493] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Oct  5 17:09:15 illusion-desktop kernel: [   31.476504] Linux agpgart interface v0.102
Oct  5 17:09:15 illusion-desktop kernel: [   31.548987] input: PC Speaker as /devices/platform/pcspkr/input/input2
Oct  5 17:09:15 illusion-desktop kernel: [   31.665822] agpgart: Detected an Intel 830M Chipset.
Oct  5 17:09:15 illusion-desktop kernel: [   31.665990] agpgart: Detected 8060K stolen memory.
Oct  5 17:09:15 illusion-desktop kernel: [   31.683640] agpgart: AGP aperture is 128M @ 0xe0000000
Oct  5 17:09:15 illusion-desktop kernel: [   31.798721] i810_smbus 0000:00:02.0: i810/i815 i2c device found.
Oct  5 17:09:15 illusion-desktop kernel: [   31.967460] input: Power Button (FF) as /devices/virtual/input/input3
Oct  5 17:09:15 illusion-desktop kernel: [   31.979232] ACPI: Power Button (FF) [PWRF]
Oct  5 17:09:15 illusion-desktop kernel: [   31.979394] input: Power Button (CM) as /devices/virtual/input/input4
Oct  5 17:09:15 illusion-desktop kernel: [   31.995161] ACPI: Power Button (CM) [PWRB]
Oct  5 17:09:15 illusion-desktop kernel: [   32.732178] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
Oct  5 17:09:15 illusion-desktop kernel: [   32.804683] parport_pc 00:08: reported by Plug and Play ACPI
Oct  5 17:09:15 illusion-desktop kernel: [   32.804784] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
Oct  5 17:09:15 illusion-desktop kernel: [   33.799455] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 20
Oct  5 17:09:15 illusion-desktop kernel: [   34.087747] eth0: link down
Oct  5 17:09:15 illusion-desktop kernel: [   34.122566] intel8x0_measure_ac97_clock: measured 53539 usecs
Oct  5 17:09:15 illusion-desktop kernel: [   34.122572] intel8x0: clocking to 48000
Oct  5 17:09:15 illusion-desktop kernel: [   34.481502] NET: Registered protocol family 10
Oct  5 17:09:15 illusion-desktop kernel: [   34.481812] lo: Disabled Privacy Extensions
Oct  5 17:09:15 illusion-desktop kernel: [   34.482289] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct  5 17:09:15 illusion-desktop kernel: [   36.968663] lp0: using parport0 (interrupt-driven).
Oct  5 17:09:15 illusion-desktop kernel: [   37.063922] Adding 1502036k swap on /dev/sda9.  Priority:-1 extents:1 across:1502036k
Oct  5 17:09:15 illusion-desktop kernel: [   37.627743] EXT3 FS on sda10, internal journal
Oct  5 17:09:15 illusion-desktop kernel: [   38.378644] kjournald starting.  Commit interval 5 seconds
Oct  5 17:09:15 illusion-desktop kernel: [   38.378905] EXT3 FS on sda11, internal journal
Oct  5 17:09:15 illusion-desktop kernel: [   38.378910] EXT3-fs: mounted filesystem with ordered data mode.
Oct  5 17:09:15 illusion-desktop kernel: [   39.757520] ip_tables: (C) 2000-2006 Netfilter Core Team
Oct  5 17:09:15 illusion-desktop kernel: [   40.213771] No dock devices found.
Oct  5 17:09:15 illusion-desktop kernel: [   41.537146] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Oct  5 17:09:15 illusion-desktop kernel: [   41.537155] apm: overridden by ACPI.
Oct  5 17:09:15 illusion-desktop kernel: [   41.680372] ppdev: user-space parallel port driver
Oct  5 17:09:15 illusion-desktop kernel: [   41.815551] audit(1223206755.957:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4883 profile="/usr/sbin/cupsd" namespace="default"
Oct  5 17:09:16 illusion-desktop dhcdbd: Started up.
Oct  5 17:09:17 illusion-desktop kernel: [   43.785324] Bluetooth: Core ver 2.11
Oct  5 17:09:17 illusion-desktop kernel: [   43.786597] NET: Registered protocol family 31
Oct  5 17:09:17 illusion-desktop kernel: [   43.786604] Bluetooth: HCI device and connection manager initialized
Oct  5 17:09:17 illusion-desktop kernel: [   43.786610] Bluetooth: HCI socket layer initialized
Oct  5 17:09:17 illusion-desktop kernel: [   43.827381] Bluetooth: L2CAP ver 2.9
Oct  5 17:09:17 illusion-desktop kernel: [   43.827389] Bluetooth: L2CAP socket layer initialized
Oct  5 17:09:18 illusion-desktop kernel: [   43.932834] Bluetooth: RFCOMM socket layer initialized
Oct  5 17:09:18 illusion-desktop kernel: [   43.932860] Bluetooth: RFCOMM TTY layer initialized
Oct  5 17:09:18 illusion-desktop kernel: [   43.932863] Bluetooth: RFCOMM ver 1.8
Oct  5 17:09:20 illusion-desktop kernel: [   46.614786] [drm] Initialized drm 1.1.0 20060810
Oct  5 17:09:20 illusion-desktop kernel: [   46.620319] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
Oct  5 17:09:20 illusion-desktop kernel: [   46.620456] [drm] Initialized i915 1.6.0 20060119 on minor 0
Oct  5 17:09:57 illusion-desktop kernel: [   83.275414] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Oct  5 17:09:57 illusion-desktop kernel: [   83.281087] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Oct  5 17:11:36 illusion-desktop pppd[5686]: Plugin rp-pppoe.so loaded.
Oct  5 17:11:36 illusion-desktop kernel: [  182.166449] PPP generic driver version 2.4.2
Oct  5 17:11:36 illusion-desktop kernel: [  182.225670] NET: Registered protocol family 17
Oct  5 17:11:36 illusion-desktop pppd[5700]: pppd 2.4.4 started by root, uid 0
Oct  5 17:11:36 illusion-desktop pppd[5700]: PPP session is 6277
Oct  5 17:11:36 illusion-desktop kernel: [  182.284480] NET: Registered protocol family 24
Oct  5 17:11:36 illusion-desktop pppd[5700]: Using interface ppp0
Oct  5 17:11:36 illusion-desktop pppd[5700]: Connect: ppp0 <--> eth0
Oct  5 17:11:39 illusion-desktop pppd[5700]: CHAP authentication succeeded: Authentication success,Welcome!
Oct  5 17:11:39 illusion-desktop pppd[5700]: CHAP authentication succeeded
Oct  5 17:11:39 illusion-desktop pppd[5700]: peer from calling number 00:E0:FC:45:2E:22 authorized
Oct  5 17:11:39 illusion-desktop pppd[5700]: local  IP address 
Oct  5 17:11:39 illusion-desktop pppd[5700]: remote IP address 
Oct  5 17:11:39 illusion-desktop pppd[5700]: primary   DNS address 
Oct  5 17:11:39 illusion-desktop pppd[5700]: secondary DNS address 
Oct  5 17:29:14 illusion-desktop -- MARK --

```


> **tonybaqain said:**
> 
```
dmesg | tail
```

```
[   46.614786] [drm] Initialized drm 1.1.0 20060810
[   46.620319] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   46.620333] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   46.620456] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   83.275414] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   83.281087] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   93.590371] eth0: no IPv6 routers present
[  182.166449] PPP generic driver version 2.4.2
[  182.225670] NET: Registered protocol family 17
[  182.284480] NET: Registered protocol family 24

```

---

### Post by tonybaqain on 2008-10-05
your system seems healthy and running ok, your perephirals seems to be most compatible with the kernel , nothing strange there, it might be a case of sleep and/or powersave situation of one of your perephirals but after some shutdowns and turn-on's it went up, 

please paste the following also :
[list]
[*]sudo ps awux  --sort=rss | tail -30
[*]sudo lspci
[*]sudo lsusb
[*]sudo ethtool eth0
[*]cat /etc/network/interfaces
[/list]

please be patient with me, i need information so we can track some faults, if there are any.

---

### Post by Nabanna on 2008-10-05
> **tonybaqain said:**
> your system seems healthy and running ok, your perephirals seems to be most compatible with the kernel , nothing strange there, it might be a case of sleep and/or powersave situation of one of your perephirals but after some shutdowns and turn-on's it went up, 

please paste the following also :
[list]
[*]sudo ps awux  --sort=rss | tail -30
[*]sudo lspci
[*]sudo lsusb
[*]sudo ethtool eth0
[*]cat /etc/network/interfaces
[/list]

please be patient with me, i need information so we can track some faults, if there are any.

ok...

---

### Post by xrea on 2008-10-05
hey!

i have the some problem that Nabanna has, unlike my PC does not want to start after login screen. Just like Nabanna worte it appeares to be freeze, nothing happens (this problem started after updating ubuntu to version 8.04.1) . I ve tried to restart the system several times but with no success. 


what can i do?

---

### Post by tonybaqain on 2008-10-05
im really curious about the results of the commands for you both, i hope you could send them to me, at least the **lspci** and **cat /etc/network/interfaces** commands, help me so i can help you.

have fun :)

---

### Post by Nabanna on 2008-10-06
> **tonybaqain said:**
> im really curious about the results of the commands for you both, i hope you could send them to me, at least the **lspci** and **cat /etc/network/interfaces** commands, help me so i can help you.

have fun :)

@tonybaqain,

after my last post, i wasn't able to start Ubuntu as i said in my earlier post, so after trying 2-3 times i reinstalled Ubuntu(this time 8.04.1)...lets see what happens now....(fingers crossed)..
i appreciate your help...thank you.... :)

---

