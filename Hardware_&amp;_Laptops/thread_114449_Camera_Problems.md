---
title: "Camera Problems"
date: 2006-01-08
forum: Hardware &amp; Laptops
---

### Post by Pedricko on 2006-01-08
Hey I just bought a new digital camera - A Premier DS-5080 from Tesco (a british supermarket), it was only £40 and its 5.0 megapixels so I thought I might as well get it.

It has inbuilt memory (14MB, I think - enough for 26 pictures), and also takes up to 1GB of secure digital.

When I plug into my ubuntu (and only) computer, it doesnt mount. I believe I need some help. I'm plugging in via USB and have even tried using different USB ports.

My other idea (to solve the problem) is to buy a USB card reader and an SD card, but I'm out of the money game at the moment.

How can I get my camera to mount?!

Thanks in advance - the Pedro

---

### Post by Amon_Re on 2006-01-08
[QUOTE=Pedricko]Hey I just bought a new digital camera - A Premier DS-5080 from Tesco (a british supermarket), it was only £40 and its 5.0 megapixels so I thought I might as well get it.

It has inbuilt memory (14MB, I think - enough for 26 pictures), and also takes up to 1GB of secure digital.

When I plug into my ubuntu (and only) computer, it doesnt mount. I believe I need some help. I'm plugging in via USB and have even tried using different USB ports.

My other idea (to solve the problem) is to buy a USB card reader and an SD card, but I'm out of the money game at the moment.

How can I get my camera to mount?!

Thanks in advance - the Pedro[/QUOTE]

When plugging it in, you should get entries in dmesg, what does dmesg tell you?

---

### Post by Pedricko on 2006-01-08
I had a terminal open when I plugged in, but nothing happened, I just tried Dmesg and (brace yourself) this is what came up.

```
[4294670.268000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294670.271000] audit: initializing netlink socket (disabled)
[4294670.271000] audit: initialized
[4294670.271000] VFS: Disk quotas dquot_6.5.1
[4294670.271000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294670.271000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294670.272000] devfs: boot_options: 0x0
[4294670.272000] Initializing Cryptographic API
[4294670.272000] isapnp: Scanning for PnP cards...
[4294670.626000] isapnp: No Plug & Play device found
[4294670.655000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[4294670.655000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294670.655000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294670.655000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
[4294670.655000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294670.659000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294670.659000] io scheduler noop registered
[4294670.659000] io scheduler anticipatory registered
[4294670.659000] io scheduler deadline registered
[4294670.659000] io scheduler cfq registered
[4294670.660000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294670.660000] EISA: Probing bus 0 at eisa.0
[4294670.660000] Cannot allocate resource for EISA slot 5
[4294670.660000] EISA: Detected 0 cards.
[4294670.660000] NET: Registered protocol family 2
[4294670.670000] IP: routing cache hash table of 512 buckets, 4Kbytes
[4294670.670000] TCP established hash table entries: 4096 (order: 3, 32768 bytes)
[4294670.670000] TCP bind hash table entries: 4096 (order: 2, 16384 bytes)
[4294670.670000] TCP: Hash tables configured (established 4096 bind 4096)
[4294670.670000] NET: Registered protocol family 8
[4294670.670000] NET: Registered protocol family 20
[4294670.670000] ACPI wakeup devices:
[4294670.671000] PCI0 PS2M PS2K UAR1 USB1 USB2  LAN  MDM  AUD SLPB
[4294670.671000] ACPI: (supports S0 S1 S4 S5)
[4294670.672000] Freeing unused kernel memory: 224k freed
[4294670.694000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294670.699000] vga16fb: initializing
[4294670.699000] vga16fb: mapped to 0xc00a0000
[4294670.799000] Console: switching to colour frame buffer device 80x30
[4294670.799000] fb0: VGA16 VGA frame buffer device
[4294671.919000] Capability LSM initialized
[4294671.941000] NET: Registered protocol family 1
[4294671.961000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294671.961000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294671.961000] ACPI: bus type ide registered
[4294671.972000] SIS5513: IDE controller at PCI slot 0000:00:00.1
[4294671.972000] SIS5513: chipset revision 208
[4294671.972000] SIS5513: not 100% native mode: will probe irqs later
[4294671.972000] SIS5513: SiS730 ATA 100 (1st gen) controller
[4294671.972000]     ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:DMA, hdb:DMA
[4294671.972000]     ide1: BM-DMA at 0xff08-0xff0f, BIOS settings: hdc:DMA, hdd:DMA
[4294671.973000] Probing IDE interface ide0...
[4294672.236000] hda: Maxtor 6Y080P0, ATA DISK drive
[4294672.848000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294672.848000] Probing IDE interface ide1...
[4294673.520000] hdc: TSST CDW/DVD TS-H492A, ATAPI CD/DVD-ROM drive
[4294674.132000] ide1 at 0x170-0x177,0x376 on irq 15
[4294674.132000] Probing IDE interface ide2...
[4294674.645000] Probing IDE interface ide3...
[4294675.157000] Probing IDE interface ide4...
[4294675.669000] Probing IDE interface ide5...
[4294676.187000] hda: max request size: 128KiB
[4294676.189000] hda: 160086528 sectors (81964 MB) w/7936KiB Cache, CHS=65535/16/63, UDMA(100)
[4294676.189000] hda: cache flushes supported
[4294676.190000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
[4294676.209000] hdc: ATAPI 40X DVD-ROM CD-R/RW drive, 2048kB Cache
[4294676.209000] Uniform CD-ROM driver Revision: 3.20
[4294676.734000] sis900.c: v1.08.08 Jan. 22 2005
[4294676.735000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[4294676.735000] PCI: setting IRQ 11 as level-triggered
[4294676.735000] ACPI: PCI Interrupt 0000:00:01.1[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[4294676.736000] 0000:00:01.1: VIA 6103 PHY transceiver found at address 1.
[4294676.744000] 0000:00:01.1: Using transceiver found at address 1 as default
[4294676.745000] eth0: SiS 900 PCI Fast Ethernet at 0xd000, IRQ 11, 00:07:95:30:f7:2c.
[4294676.763000] usbcore: registered new driver usbfs
[4294676.763000] usbcore: registered new driver hub
[4294676.765000] ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[4294676.765000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 3
[4294676.765000] PCI: setting IRQ 3 as level-triggered
[4294676.765000] ACPI: PCI Interrupt 0000:00:01.2[D] -> Link [LNKD] -> GSI 3 (level, low) -> IRQ 3
[4294676.765000] ohci_hcd 0000:00:01.2: Silicon Integrated Systems [SiS] USB 1.0 Controller
[4294676.766000] ohci_hcd 0000:00:01.2: new USB bus registered, assigned bus number 1
[4294676.766000] ohci_hcd 0000:00:01.2: irq 3, io mem 0xcfffc000
[4294676.819000] hub 1-0:1.0: USB hub found
[4294676.819000] hub 1-0:1.0: 3 ports detected
[4294676.822000] ACPI: PCI Interrupt 0000:00:01.3[D] -> Link [LNKD] -> GSI 3 (level, low) -> IRQ 3
[4294676.822000] ohci_hcd 0000:00:01.3: Silicon Integrated Systems [SiS] USB 1.0 Controller (#2)
[4294676.822000] ohci_hcd 0000:00:01.3: new USB bus registered, assigned bus number 2
[4294676.822000] ohci_hcd 0000:00:01.3: irq 3, io mem 0xcfffd000
[4294676.875000] hub 2-0:1.0: USB hub found
[4294676.875000] hub 2-0:1.0: 3 ports detected
[4294677.055000] usb 2-1: new full speed USB device using ohci_hcd and address 2[4294679.515000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[4294679.515000] ACPI: Processor [CPU1] (supports 8 throttling states)
[4294679.645000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294688.239000] hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
[4294688.239000] hdc: media error (bad sector): error=0x30 { LastFailedSense=0x03 }
[4294688.239000] ide: failed opcode was: unknown
[4294688.239000] end_request: I/O error, dev hdc, sector 47488
[4294688.239000] Buffer I/O error on device hdc, logical block 5936
[4294698.611000] hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
[4294698.611000] hdc: media error (bad sector): error=0x30 { LastFailedSense=0x03 }
[4294698.611000] ide: failed opcode was: unknown
[4294698.611000] end_request: I/O error, dev hdc, sector 47488
[4294698.611000] Buffer I/O error on device hdc, logical block 5936
[4294703.562000] Attempting manual resume
[4294703.580000] swsusp: Suspend partition has wrong signature?
[4294703.595000] EXT3-fs: INFO: recovery required on readonly filesystem.
[4294703.595000] EXT3-fs: write access will be enabled during recovery.
[4294708.744000] kjournald starting.  Commit interval 5 seconds
[4294708.744000] EXT3-fs: recovery complete.
[4294708.745000] EXT3-fs: mounted filesystem with ordered data mode.
[4294710.202000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294715.129000] Adding 327672k swap on /dev/mapper/Ubuntu-swap_1.  Priority:-1 extents:1
[4294715.344000] EXT3 FS on dm-0, internal journal
[4294721.176000] parport: PnPBIOS parport detected.
[4294721.176000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[4294721.271000] lp0: using parport0 (interrupt-driven).
[4294721.335000] mice: PS/2 mouse device common for all mice
[4294721.727000] input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
[4294722.331000] ts: Compaq touchscreen protocol output
[4294726.289000] cdrom: hdc: mrw address space DMA selected
[4294727.029000] kjournald starting.  Commit interval 5 seconds
[4294727.030000] EXT3 FS on hda1, internal journal
[4294727.030000] EXT3-fs: mounted filesystem with ordered data mode.
[4294728.436000] Linux agpgart interface v0.101 (c) Dave Jones
[4294728.457000] agpgart: Detected SiS 730 chipset
[4294728.502000] agpgart: AGP aperture is 64M @ 0xd0000000
[4294729.691000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[4294729.691000] ACPI: PCI Interrupt 0000:00:01.4[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[4294731.498000] MC'97 1 converters and GPIO not ready (0x1)
[4294731.549000] gameport: Trident 4DWave is pci0000:00:01.4/gameport0, speed 2130kHz
[4294732.304000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294732.330000] shpchp: shpc_init : shpc_cap_offset == 0
[4294732.330000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294732.502000] ac97 codec read TIMEOUT [0x54/0x1c0d4]!!!
[4294732.531000] ac97 codec read TIMEOUT [0x54/0x1c0d4]!!!
[4294732.631000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 5
[4294732.631000] PCI: setting IRQ 5 as level-triggered
[4294732.631000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKA] -> GSI 5 (level, low) -> IRQ 5
[4294734.652000] Linux video capture interface: v1.00
[4294734.680000] drivers/usb/media/spca5xx/spca5xx-core.c: USB SPCA5XX camera found.Labtec WebCam Elch 2(SPCA561A)
[4294734.708000] usbcore: registered new driver spca5xx
[4294734.708000] drivers/usb/media/spca5xx/spca5xx-core.c: spca5xx driver 00.57.02 registered
[4294734.957000] Real Time Clock Driver v1.12
[4294735.169000] input: PC Speaker
[4294735.570000] Floppy drive(s): fd0 is 1.44M
[4294735.585000] FDC 0 is a post-1991 82077
[4294737.306000] NET: Registered protocol family 17
[4294740.285000] eth0: Media Link On 100mbps full-duplex
[4294759.835000] ac97 codec read TIMEOUT [0x54/0x1c0d4]!!!
[4294759.865000] ac97 codec read TIMEOUT [0x54/0x1c0d4]!!!
[4294760.695000] NET: Registered protocol family 10
[4294760.695000] Disabled Privacy Extensions on device c02eb280(lo)
[4294760.695000] IPv6 over IPv4 tunneling driver
[4294762.001000] ACPI: Power Button (FF) [PWRF]
[4294762.001000] ACPI: Power Button (CM) [PWBX]
[4294762.001000] ACPI: Sleep Button (CM) [SLPB]
[4294762.232000] ibm_acpi: ec object not found
[4294770.440000] [drm] Initialized drm 1.0.0 20040925
[4294770.487000] [drm] Initialized sis 1.1.0 20030826 on minor 0: Silicon Integrated Systems [SiS] 630/730 PCI/AGP VGA Display Adapter
[4294770.489000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[4294770.489000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 2x mode
[4294770.489000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 2x mode
[4294770.747000] eth0: no IPv6 routers present
[4294774.127000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294774.127000] apm: overridden by ACPI.
[4294776.459000] Bluetooth: Core ver 2.7
[4294776.459000] NET: Registered protocol family 31
[4294776.459000] Bluetooth: HCI device and connection manager initialized
[4294776.459000] Bluetooth: HCI socket layer initialized
[4294776.531000] Bluetooth: L2CAP ver 2.7
[4294776.531000] Bluetooth: L2CAP socket layer initialized
[4294776.629000] Bluetooth: RFCOMM ver 1.5
[4294776.629000] Bluetooth: RFCOMM socket layer initialized
[4294776.629000] Bluetooth: RFCOMM TTY layer initialized
[4294817.927000] ac97 codec read TIMEOUT [0x54/0x1c0d4]!!!
[4294817.960000] ac97 codec read TIMEOUT [0x54/0x1c0d4]!!!
[4294826.898000] cdrom: hdc: mrw address space DMA selected
[4294827.506000] cdrom: hdc: mrw address space DMA selected
[4294827.558000] ISO 9660 Extensions: Microsoft Joliet Level 3
[4294827.644000] ISO 9660 Extensions: RRIP_1991A
[4295000.490000] atkbd.c: Keyboard on isa0060/serio0 reports too many keys pressed.
[4295089.418000] ibm_acpi: ec object not found
[4295334.572000] usb 1-3: new full speed USB device using ohci_hcd and address 2[4295412.571000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295412.571000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295412.638000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295412.638000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295448.895000] usb 1-3: USB disconnect, address 2
[4295473.825000] usb 1-3: new full speed USB device using ohci_hcd and address 3[4295887.290000] atkbd.c: Keyboard on isa0060/serio0 reports too many keys pressed.
[4295888.153000] atkbd.c: Keyboard on isa0060/serio0 reports too many keys pressed.
[4296907.939000] atkbd.c: Keyboard on isa0060/serio0 reports too many keys pressed.
[4296981.777000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296981.777000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296981.975000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296981.975000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297940.650000] atkbd.c: Keyboard on isa0060/serio0 reports too many keys pressed.
[4298255.975000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4298255.975000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298256.045000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4298256.045000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298283.988000] atkbd.c: Keyboard on isa0060/serio0 reports too many keys pressed.
[4298518.733000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4298518.733000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298518.881000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4298518.881000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298519.353000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4298519.353000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298519.432000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4298519.432000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298519.726000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4298519.726000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298519.802000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4298519.802000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298519.923000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4298519.923000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298520.014000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4298520.014000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298520.126000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4298520.126000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298520.220000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4298520.220000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298520.597000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4298520.597000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298520.732000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4298520.732000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298520.844000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4298520.844000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298520.941000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4298520.941000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
```

I dont know what most of that means.

---

### Post by Pedricko on 2006-01-08
Problem solved!

I was choosing the 'PC Cam' Feature on the device, thinking it would link to the comp.

Choosing the 'disk drive' option turned it into a mass storage device, which ubuntu recognizes!

Voila!

Thanks anyway for looking.

---

### Post by barkham hobbey on 2006-07-05
I found your advice very helpful as I lost the manual to the camera!  However, I wonder if you could help me.  I've got the same camera as you. I've put the extra memory card in, but it still says that the memory is full!!  How do I get the camera to access the extra memory and recognise it.

Thanks for your help.

---

