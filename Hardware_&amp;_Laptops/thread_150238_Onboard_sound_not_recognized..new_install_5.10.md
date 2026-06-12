---
title: "Onboard sound not recognized..new install 5.10"
date: 2006-03-25
forum: Hardware &amp; Laptops
---

### Post by gordong11 on 2006-03-25
I just built a new pc, everything works great except no sound. It's a Gigabyte GA-K8N51GMF with onboard nvidia graphics and realtek AC97, alc850 sound. the install does not see the onboard sound, in the device manager nothing listed for default sound card.

0000:00:10.2 Multimedia audio controller: nVidia Corporation: Unknown device 026b (rev a2)
        Subsystem: Giga-byte Technology: Unknown device ae01
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
        I/O ports at c400 [size=256]
        I/O ports at c800 [size=256]
        Memory at f5102000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

linux@ubuntu:~$ dmesg
294671.372000] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 *10 11 14 15)
[4294671.372000] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 *11 14 15)
[4294671.372000] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[4294671.373000] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[4294671.373000] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[4294671.374000] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[4294671.374000] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[4294671.375000] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[4294671.375000] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[4294671.376000] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[4294671.376000] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[4294671.377000] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[4294671.377000] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[4294671.378000] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0, disabled.
[4294671.378000] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[4294671.379000] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0, disabled.
[4294671.379000] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
[4294671.380000] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[4294671.380000] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0, disabled.
[4294671.381000] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[4294671.381000] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0, disabled.
[4294671.382000] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0, disabled.
[4294671.382000] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[4294671.383000] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[4294671.383000] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0, disabled.
[4294671.384000] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
[4294671.387000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294671.387000] pnp: PnP ACPI init
[4294671.394000] pnp: PnP ACPI: found 12 devices
[4294671.394000] PnPBIOS: Disabled by ACPI PNP
[4294671.394000] PCI: Using ACPI for IRQ routing
[4294671.394000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294671.449000] pnp: 00:00: ioport range 0x1000-0x107f could not be reserved
[4294671.449000] pnp: 00:00: ioport range 0x1080-0x10ff has been reserved
[4294671.449000] pnp: 00:00: ioport range 0x1400-0x147f has been reserved
[4294671.449000] pnp: 00:00: ioport range 0x1480-0x14ff could not be reserved
[4294671.449000] pnp: 00:00: ioport range 0x1800-0x187f has been reserved
[4294671.449000] pnp: 00:00: ioport range 0x1880-0x18ff has been reserved
[4294671.449000] pnp: 00:00: ioport range 0x2000-0x207f has been reserved
[4294671.449000] pnp: 00:00: ioport range 0x2080-0x20ff has been reserved
[4294671.449000] audit: initializing netlink socket (disabled)
[4294671.449000] audit: initialized
[4294671.449000] VFS: Disk quotas dquot_6.5.1
[4294671.449000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294671.449000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294671.449000] devfs: boot_options: 0x0
[4294671.449000] Initializing Cryptographic API
[4294671.450000] isapnp: Scanning for PnP cards...
[4294671.801000] isapnp: No Plug & Play device found
[4294671.818000] PNP: PS/2 controller doesn't have AUX irq; using default 0xc
[4294671.818000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 112
[4294671.820000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294671.820000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294671.820000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
[4294671.821000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294671.821000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294671.823000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294671.823000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294671.823000] io scheduler noop registered
[4294671.823000] io scheduler anticipatory registered
[4294671.823000] io scheduler deadline registered
[4294671.823000] io scheduler cfq registered
[4294671.823000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294671.824000] EISA: Probing bus 0 at eisa.0
[4294671.824000] Cannot allocate resource for EISA slot 1
[4294671.824000] Cannot allocate resource for EISA slot 2
[4294671.824000] EISA: Detected 0 cards.
[4294671.824000] NET: Registered protocol family 2
[4294671.833000] IP: routing cache hash table of 4096 buckets, 32Kbytes
[4294671.833000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[4294671.833000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[4294671.833000] TCP: Hash tables configured (established 16384 bind 16384)
[4294671.833000] NET: Registered protocol family 8
[4294671.833000] NET: Registered protocol family 20
[4294671.833000] ACPI wakeup devices:
[4294671.833000] HUB0 XVRA XVRB XVRC USB0 USB2 AZAD MMAC MMCI UAR1
[4294671.833000] ACPI: (supports S0 S1 S4 S5)
[4294671.833000] Freeing unused kernel memory: 224k freed
[4294671.846000] vga16fb: initializing
[4294671.846000] vga16fb: mapped to 0xc00a0000
[4294672.035000] Console: switching to colour frame buffer device 80x30
[4294672.035000] fb0: VGA16 VGA frame buffer device
[4294672.103000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294673.164000] Capability LSM initialized
[4294673.174000] NET: Registered protocol family 1
[4294673.189000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294673.189000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294673.189000] ACPI: bus type ide registered
[4294673.192000] SCSI subsystem initialized
[4294673.193000] libata version 1.11 loaded.
[4294673.194000] sata_nv version 0.6
[4294673.194000] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[4294673.194000] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [APSI] -> GSI 23 (level, low) -> IRQ 23
[4294673.194000] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[4294673.195000] ata1: SATA max UDMA/133 cmd 0x9F0 ctl 0xBF2 bmdma 0xDC00 irq 23[4294673.195000] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xB72 bmdma 0xDC08 irq 23[4294673.550000] ata1: dev 0 cfg 49:2f00 82:706b 83:7e01 84:4023 85:7068 86:3c01 87:4023 88:407f
[4294673.550000] ata1: dev 0 ATA, max UDMA/133, 156312576 sectors: lba48
[4294673.550000] ata1: dev 0 configured for UDMA/133
[4294673.550000] scsi0 : sata_nv
[4294673.751000] ata2: no device found (phy stat 00000000)
[4294673.751000] scsi1 : sata_nv
[4294673.751000]   Vendor: ATA       Model: WDC WD800JD-08LS  Rev: 09.0
[4294673.751000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[4294673.764000] NFORCE-MCP51: IDE controller at PCI slot 0000:00:0d.0
[4294673.764000] NFORCE-MCP51: chipset revision 161
[4294673.764000] NFORCE-MCP51: not 100% native mode: will probe irqs later
[4294673.764000] NFORCE-MCP51: 0000:00:0d.0 (rev a1) UDMA133 controller
[4294673.764000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[4294673.764000]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
[4294673.764000] Probing IDE interface ide0...
[4294674.436000] hda: LITE-ON DVDRW SHW-160P6S, ATAPI CD/DVD-ROM drive
[4294675.048000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294675.048000] Probing IDE interface ide1...
[4294675.567000] Probing IDE interface ide1...
[4294676.085000] Probing IDE interface ide2...
[4294676.597000] Probing IDE interface ide3...
[4294677.109000] Probing IDE interface ide4...
[4294677.621000] Probing IDE interface ide5...
[4294678.138000] hda: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
[4294678.138000] Uniform CD-ROM driver Revision: 3.20
[4294678.144000] SCSI device sda: 156312576 512-byte hdwr sectors (80032 MB)
[4294678.144000] SCSI device sda: drive cache: write back
[4294678.144000] SCSI device sda: 156312576 512-byte hdwr sectors (80032 MB)
[4294678.144000] SCSI device sda: drive cache: write back
[4294678.144000]  /dev/scsi/host0/bus0/target0/lun0: p1 p2 < p5 >
[4294678.175000] Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
[4294678.409000] Attempting manual resume
[4294678.409000] swsusp: Suspend partition has wrong signature?
[4294678.508000] usbcore: registered new driver usbfs
[4294678.508000] usbcore: registered new driver hub
[4294678.509000] ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[4294678.509000] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
[4294678.509000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [APCF] -> GSI 22 (level, low) -> IRQ 22
[4294678.509000] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[4294678.509000] ohci_hcd 0000:00:0b.0: nVidia Corporation MCP51 USB Controller
[4294678.509000] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[4294678.509000] ohci_hcd 0000:00:0b.0: irq 22, io mem 0xf5104000
[4294678.562000] hub 1-0:1.0: USB hub found
[4294678.562000] hub 1-0:1.0: 8 ports detected
[4294678.573000] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 21
[4294678.573000] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [APCL] -> GSI 21 (level, low) -> IRQ 21
[4294678.573000] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[4294678.573000] ehci_hcd 0000:00:0b.1: nVidia Corporation MCP51 USB Controller
[4294678.573000] ehci_hcd 0000:00:0b.1: debug port 1
[4294678.573000] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[4294678.573000] ehci_hcd 0000:00:0b.1: irq 21, io mem 0xf5100000
[4294678.573000] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
[4294678.573000] ehci_hcd 0000:00:0b.1: park 0
[4294678.573000] ehci_hcd 0000:00:0b.1: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[4294678.573000] hub 2-0:1.0: USB hub found
[4294678.573000] hub 2-0:1.0: 8 ports detected
[4294678.631000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.41.
[4294678.632000] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 20
[4294678.632000] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [APCH] -> GSI 20 (level, low) -> IRQ 20
[4294678.632000] PCI: Setting latency timer of device 0000:00:14.0 to 64
[4294679.027000] usb 1-5: new low speed USB device using ohci_hcd and address 2
[4294679.144000] eth0: forcedeth.c: subsystem: 01458:e000 bound to 0000:00:14.0
[4294681.195000] usbcore: registered new driver hiddev
[4294681.207000] input: USB HID v1.00 Mouse [Microsoft Microsoft Trackball Explorer\uffff] on usb-0000:00:0b.0-5
[4294681.207000] usbcore: registered new driver usbhid
[4294681.207000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
[4294681.585000] ACPI: CPU0 (power states: C1[C1])
[4294681.762000] Attempting manual resume
[4294681.763000] swsusp: Suspend partition has wrong signature?
[4294681.775000] kjournald starting.  Commit interval 5 seconds
[4294681.775000] EXT3-fs: mounted filesystem with ordered data mode.
[4294682.590000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294684.869000] Adding 1132540k swap on /dev/sda5.  Priority:-1 extents:1
[4294685.117000] EXT3 FS on sda1, internal journal
[4294689.632000] parport: PnPBIOS parport detected.
[4294689.632000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[4294689.718000] lp0: using parport0 (interrupt-driven).
[4294689.746000] mice: PS/2 mouse device common for all mice
[4294689.796000] ieee1394: Initialized config rom entry `ip1394'
[4294689.800000] sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
[4294692.634000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294694.731000] ohci1394: $Rev: 1250 $ Ben Collins <bcollins@debian.org>
[4294694.732000] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[4294694.732000] ACPI: PCI Interrupt 0000:01:0e.0[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 19
[4294694.732000] PCI: Via IRQ fixup for 0000:01:0e.0, from 10 to 3
[4294694.789000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[19]  MMIO=[f5000000-f50007ff]  Max Packet=[2048]
[4294696.056000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0000148500e4e635][4294696.196000] Real Time Clock Driver v1.12
[4294696.257000] input: PC Speaker
[4294696.377000] Floppy drive(s): fd0 is 1.44M
[4294696.392000] FDC 0 is a post-1991 82077
[4294696.671000] ts: Compaq touchscreen protocol output
[4294697.319000] NET: Registered protocol family 17
[4294701.801000] NET: Registered protocol family 10
[4294701.801000] Disabled Privacy Extensions on device c02eb280(lo)
[4294701.801000] IPv6 over IPv4 tunneling driver
[4294702.710000] ACPI: Power Button (FF) [PWRF]
[4294702.710000] ACPI: Power Button (CM) [PWRB]
[4294702.813000] ibm_acpi: ec object not found
[4294712.279000] eth0: no IPv6 routers present
[4294932.139000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[4294932.139000] apm: overridden by ACPI.
[4294932.157000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[4294932.157000] apm: disabled on user request.
[4294951.872000] Bluetooth: Core ver 2.7
[4294951.872000] NET: Registered protocol family 31
[4294951.872000] Bluetooth: HCI device and connection manager initialized
[4294951.872000] Bluetooth: HCI socket layer initialized
[4294951.911000] Bluetooth: L2CAP ver 2.7
[4294951.912000] Bluetooth: L2CAP socket layer initialized
[4294951.921000] Bluetooth: RFCOMM ver 1.5
[4294951.921000] Bluetooth: RFCOMM socket layer initialized
[4294951.921000] Bluetooth: RFCOMM TTY layer initialized
[4295001.815000] powernow-k8: Power state transitions not supported
[4295019.449000] ibm_acpi: ec object not found
[4295226.341000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[4295226.341000] apm: disabled on user request.
[4295234.846000] ppdev: user-space parallel port driver
[4295234.847000] ppdev0: registered pardevice
[4295234.888000] ppdev0: unregistered pardevice
[4295234.888000] ppdev1: claim the port first
[4295234.888000] ppdev2: claim the port first
[4295349.077000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[4295349.077000] apm: disabled on user request.
[4295353.933000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[4295353.933000] apm: disabled on user request.
[4295358.205000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[4295358.205000] apm: disabled on user request.
[4295460.156000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295460.156000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295460.376000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295460.376000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295465.144000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295465.144000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295466.340000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295466.340000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295475.320000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295475.320000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295475.454000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295475.454000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295487.188000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[4295487.188000] apm: disabled on user request.
[4295772.023000] ibm_acpi: ec object not found
[4295782.466000] cdrom: open failed.
linux@ubuntu:~$



Can anyone point me in the right direction? or need any other info(plz tell me console commands)? Thanks

Gordo

---

