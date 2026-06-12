---
title: "USB Gamepad, device not accepting address"
date: 2006-09-27
forum: Hardware &amp; Laptops
---

### Post by magelus on 2006-09-27
I've been attempting to install Step Mania for the past 2 weeks... nothing is working, fix one issue, come up agaist another. Finally the game is installed and working properly, now I need to get the gamepad working.

I bought a dance pad, it's a Gamesis MPM300 (StepMania.com lists it as a "Genesis Multi-platform" [Dance Pad Page]("http://www.stepmania.com/wiki/Dance_Pads")) it is a triple tailed dance pad with conections for Playstaion 2, XBox, and USB. It says it requires no drivers and comes with none. I have confirmed it as functioning. I plugged it into my Windows XP SP2 Box, and played a little with no issues at all. Furthermore, I've played extesively on my Modded Playsation 1 (Kickin' it old school!).  The Pad is good. For more information on the pad you can check the [Gamesis Product Page]("http://www.gamesis.com/product/MPM-3000.htm")

I'm trying get this working with my laptop so I can play step mania anywhere. 

The Laptop is a Dell Latitude C610, with Ubuntu Dapper on it (Just installed a earlier this wee). It has one USB port that is functioning (My mouse uses it, when I'm not using another device).

When I plugged in the dance pad I ran dmesg to see if all was going well. Well, all was not well. Here is what I got...

```
[17179571.972000] Checking 'hlt' instruction... OK.
[17179571.988000] checking if image is initramfs... it is
[17179573.272000] Freeing initrd memory: 6840k freed
[17179573.292000] ACPI: Looking for DSDT ... not found!
[17179573.296000] ACPI: setting ELCR to 0200 (from 0800)
[17179574.336000] NET: Registered protocol family 16
[17179574.336000] EISA bus registered
[17179574.336000] ACPI: bus type pci registered
[17179574.348000] PCI: PCI BIOS revision 2.10 entry at 0xfbfee, last bus=2
[17179574.348000] PCI: Using configuration type 1
[17179574.348000] ACPI: Subsystem revision 20051216
[17179574.360000] ACPI: Interpreter enabled
[17179574.360000] ACPI: Using PIC for interrupt routing
[17179574.360000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179574.360000] PCI: Probing PCI hardware (bus 00)
[17179574.360000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179574.384000] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[17179574.384000] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
[17179574.384000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179574.384000] Boot video device is 0000:01:00.0
[17179574.384000] PCI: Transparent bridge - 0000:00:1e.0
[17179574.384000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179574.428000] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[17179574.428000] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *11
[17179574.428000] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
[17179574.428000] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 *11)
[17179574.432000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[17179574.432000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[17179574.432000] ACPI: Power Resource [PADA] (on)
[17179574.432000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179574.432000] pnp: PnP ACPI init
[17179574.488000] pnp: PnP ACPI: found 16 devices
[17179574.488000] PnPBIOS: Disabled by ACPI PNP
[17179574.488000] PCI: Using ACPI for IRQ routing
[17179574.488000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179574.500000] pnp: 00:01: ioport range 0x4d0-0x4d1 has been reserved
[17179574.500000] pnp: 00:01: ioport range 0x800-0x805 could not be reserved
[17179574.500000] pnp: 00:01: ioport range 0x808-0x80f could not be reserved
[17179574.500000] pnp: 00:02: ioport range 0x806-0x807 has been reserved
[17179574.500000] pnp: 00:02: ioport range 0x810-0x85f could not be reserved
[17179574.500000] pnp: 00:02: ioport range 0x860-0x87f has been reserved
[17179574.500000] pnp: 00:02: ioport range 0x880-0x8bf has been reserved
[17179574.500000] pnp: 00:02: ioport range 0x8c0-0x8df has been reserved
[17179574.500000] pnp: 00:02: ioport range 0x8e0-0x8ff has been reserved
[17179574.500000] pnp: 00:03: ioport range 0xf000-0xf0fe has been reserved
[17179574.500000] pnp: 00:03: ioport range 0xf100-0xf1fe has been reserved
[17179574.500000] pnp: 00:03: ioport range 0xf200-0xf2fe has been reserved
[17179574.500000] pnp: 00:03: ioport range 0xf400-0xf4fe has been reserved
[17179574.500000] pnp: 00:03: ioport range 0xf500-0xf5fe has been reserved
[17179574.500000] pnp: 00:03: ioport range 0xf600-0xf6fe has been reserved
[17179574.500000] pnp: 00:03: ioport range 0xf800-0xf8fe has been reserved
[17179574.500000] pnp: 00:03: ioport range 0xf900-0xf9fe has been reserved
[17179574.500000] pnp: 00:08: ioport range 0x900-0x91f has been reserved
[17179574.500000] pnp: 00:08: ioport range 0x3f0-0x3f1 has been reserved
[17179574.500000] pnp: 00:0e: ioport range 0xbf40-0xbf5f has been reserved
[17179574.500000] pnp: 00:0e: ioport range 0xbf20-0xbf3f has been reserved
[17179574.504000] PCI: Bridge: 0000:00:01.0
[17179574.504000]   IO window: c000-cfff
[17179574.504000]   MEM window: fc000000-fdffffff
[17179574.504000]   PREFETCH window: e0000000-e7ffffff
[17179574.504000] PCI: Bus 3, cardbus bridge: 0000:02:01.0
[17179574.504000]   IO window: 0000e000-0000e0ff
[17179574.504000]   IO window: 0000e400-0000e4ff
[17179574.504000]   PREFETCH window: 30000000-31ffffff
[17179574.504000]   MEM window: f4000000-f5ffffff
[17179574.504000] PCI: Bus 7, cardbus bridge: 0000:02:01.1
[17179574.504000]   IO window: 0000e800-0000e8ff
[17179574.504000]   IO window: 00001000-000010ff
[17179574.504000]   PREFETCH window: 32000000-33ffffff
[17179574.504000]   MEM window: f6000000-f7ffffff
[17179574.504000] PCI: Bus 11, cardbus bridge: 0000:02:03.0
[17179574.504000]   IO window: 00001400-000014ff
[17179574.504000]   IO window: 00001800-000018ff
[17179574.504000]   PREFETCH window: 34000000-35ffffff
[17179574.504000]   MEM window: fa000000-fbffffff
[17179574.504000] PCI: Bridge: 0000:00:1e.0
[17179574.504000]   IO window: e000-ffff
[17179574.504000]   MEM window: f4000000-fbffffff
[17179574.504000]   PREFETCH window: 30000000-36ffffff
[17179574.504000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179574.504000] PCI: Enabling device 0000:02:01.0 (0000 -> 0003)
[17179574.504000] **** SET: Misaligned resource pointer: dff4a3e2 Type 07 Len 0
[17179574.504000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[17179574.504000] PCI: setting IRQ 11 as level-triggered
[17179574.504000] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179574.504000] PCI: Enabling device 0000:02:01.1 (0000 -> 0003)
[17179574.504000] ACPI: PCI Interrupt 0000:02:01.1[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179574.504000] **** SET: Misaligned resource pointer: dff4a3e2 Type 07 Len 0
[17179574.504000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[17179574.504000] PCI: setting IRQ 5 as level-triggered
[17179574.504000] ACPI: PCI Interrupt 0000:02:03.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[17179574.504000] audit: initializing netlink socket (disabled)
[17179574.504000] audit(1159406422.504:1): initialized
[17179574.504000] VFS: Disk quotas dquot_6.5.1
[17179574.504000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179574.504000] Initializing Cryptographic API
[17179574.504000] io scheduler noop registered
[17179574.504000] io scheduler anticipatory registered
[17179574.504000] io scheduler deadline registered
[17179574.504000] io scheduler cfq registered
[17179574.504000] isapnp: Scanning for PnP cards...
[17179574.856000] isapnp: No Plug & Play device found
[17179574.880000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179574.884000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179574.884000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179574.884000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179574.884000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179574.888000] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179574.888000] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[17179574.888000] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[17179574.888000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179574.892000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179574.892000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179574.892000] mice: PS/2 mouse device common for all mice
[17179574.892000] EISA: Probing bus 0 at eisa.0
[17179574.892000] Cannot allocate resource for EISA slot 1
[17179574.892000] EISA: Detected 0 cards.
[17179574.892000] NET: Registered protocol family 2
[17179574.932000] IP route cache hash table entries: 8192 (order: 3, 32768 bytes)
[17179574.932000] TCP established hash table entries: 32768 (order: 5, 131072 bytes)
[17179574.932000] TCP bind hash table entries: 32768 (order: 5, 131072 bytes)
[17179574.932000] TCP: Hash tables configured (established 32768 bind 32768)
[17179574.932000] TCP reno registered
[17179574.932000] TCP bic registered
[17179574.932000] NET: Registered protocol family 1
[17179574.932000] NET: Registered protocol family 8
[17179574.932000] NET: Registered protocol family 20
[17179574.932000] Using IPI Shortcut mode
[17179574.932000] ACPI wakeup devices:
[17179574.932000]  LID PBTN PCI0 UAR1 USB0 USB1 USB2 MODM PCIE MPCI
[17179574.932000] ACPI: (supports S0 S1 S3 S4 S5)
[17179574.932000] Freeing unused kernel memory: 288k freed
[17179575.004000] vga16fb: initializing
[17179575.004000] vga16fb: mapped to 0xc00a0000
[17179575.120000] Console: switching to colour frame buffer device 80x25
[17179575.120000] fb0: VGA16 VGA frame buffer device
[17179575.296000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179576.192000] Capability LSM initialized
[17179576.316000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179576.328000] ACPI: Thermal Zone [THM] (47 C)
[17179576.876000] ICH3M: IDE controller at PCI slot 0000:00:1f.1
[17179576.876000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[17179576.876000] **** SET: Misaligned resource pointer: de9adee2 Type 07 Len 0
[17179576.876000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[17179576.876000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179576.876000] ICH3M: chipset revision 2
[17179576.876000] ICH3M: not 100% native mode: will probe irqs later
[17179576.876000]     ide0: BM-DMA at 0xbfa0-0xbfa7, BIOS settings: hda:DMA, hdb:pio
[17179576.876000]     ide1: BM-DMA at 0xbfa8-0xbfaf, BIOS settings: hdc:DMA, hdd:pio
[17179576.876000] Probing IDE interface ide0...
[17179577.168000] hda: IC25N020ATCS04-0, ATA DISK drive
[17179577.840000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179577.860000] Probing IDE interface ide1...
[17179578.596000] hdc: LG DVD-ROM DRN-8080B, ATAPI CD/DVD-ROM drive
[17179579.268000] ide1 at 0x170-0x177,0x376 on irq 15
[17179579.276000] hda: max request size: 128KiB
[17179579.288000] hda: 39070080 sectors (20003 MB) w/1768KiB Cache, CHS=38760/16/63, UDMA(100)
[17179579.288000] hda: cache flushes not supported
[17179579.288000]  hda: hda1 hda2 < hda5 >
[17179579.348000] hdc: ATAPI 24X DVD-ROM drive, 512kB Cache, DMA
[17179579.348000] Uniform CD-ROM driver Revision: 3.20
[17179579.596000] usbcore: registered new driver usbfs
[17179579.596000] usbcore: registered new driver hub
[17179579.600000] USB Universal Host Controller Interface driver v2.3
[17179579.600000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179579.600000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179579.600000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179579.600000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179579.600000] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000bf80
[17179579.604000] hub 1-0:1.0: USB hub found
[17179579.604000] hub 1-0:1.0: 2 ports detected
[17179579.768000] Attempting manual resume
[17179579.820000] EXT3-fs: mounted filesystem with ordered data mode.
[17179579.824000] kjournald starting.  Commit interval 5 seconds
[17179580.076000] usb 1-1: new low speed USB device using uhci_hcd and address 2[17179580.196000] usb 1-1: device descriptor read/64, error -71
[17179580.420000] usb 1-1: device descriptor read/64, error -71
[17179580.636000] usb 1-1: new low speed USB device using uhci_hcd and address 3[17179580.756000] usb 1-1: device descriptor read/64, error -71
[17179580.980000] usb 1-1: device descriptor read/64, error -71
[17179581.196000] usb 1-1: new low speed USB device using uhci_hcd and address 4[17179581.604000] usb 1-1: device not accepting address 4, error -71
[17179581.716000] usb 1-1: new low speed USB device using uhci_hcd and address 5[17179582.132000] usb 1-1: device not accepting address 5, error -71
[17179596.784000] Linux agpgart interface v0.101 (c) Dave Jones
[17179596.788000] agpgart: Detected an Intel 830M Chipset.
[17179596.804000] agpgart: AGP aperture is 256M @ 0xd0000000
[17179596.852000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179596.872000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179596.916000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[17179596.916000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[17179597.484000] intel8x0_measure_ac97_clock: measured 55568 usecs
[17179597.484000] intel8x0: clocking to 48000
[17179597.700000] hw_random: RNG not detected
[17179597.724000] input: PC Speaker as /class/input/input1
[17179597.816000] Floppy drive(s): fd0 is 1.44M
[17179597.832000] FDC 0 is a post-1991 82077
[17179598.056000] Real Time Clock Driver v1.12
[17179598.188000] parport: PnPBIOS parport detected.
[17179598.188000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[17179598.392000] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179598.392000] Yenta: CardBus bridge found at 0000:02:01.0 [1028:00e3]
[17179598.392000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179598.392000] Yenta: Routing CardBus interrupts to PCI
[17179598.392000] Yenta TI: socket 0000:02:01.0, mfunc 0x01261222, devctl 0x64
[17179598.624000] Yenta: ISA IRQ mask 0x0418, PCI irq 11
[17179598.624000] Socket status: 30000006
[17179598.624000] pcmcia: parent PCI bridge I/O window: 0xe000 - 0xffff
[17179598.624000] cs: IO port probe 0xe000-0xffff: clean.
[17179598.624000] pcmcia: parent PCI bridge Memory window: 0xf4000000 - 0xfbffffff
[17179598.624000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x36ffffff
[17179598.624000] ACPI: PCI Interrupt 0000:02:01.1[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179598.624000] Yenta: CardBus bridge found at 0000:02:01.1 [1028:00e3]
[17179598.624000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179598.624000] Yenta: Routing CardBus interrupts to PCI
[17179598.624000] Yenta TI: socket 0000:02:01.1, mfunc 0x01261222, devctl 0x64
[17179598.856000] Yenta: ISA IRQ mask 0x0418, PCI irq 11
[17179598.856000] Socket status: 30000006
[17179598.856000] pcmcia: parent PCI bridge I/O window: 0xe000 - 0xffff
[17179598.856000] cs: IO port probe 0xe000-0xffff: clean.
[17179598.856000] pcmcia: parent PCI bridge Memory window: 0xf4000000 - 0xfbffffff
[17179598.856000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x36ffffff
[17179598.856000] ACPI: PCI Interrupt 0000:02:03.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[17179598.856000] Yenta: CardBus bridge found at 0000:02:03.0 [12a3:ab01]
[17179598.856000] Yenta: Enabling burst memory read transactions
[17179598.856000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179598.856000] Yenta: Routing CardBus interrupts to PCI
[17179598.856000] Yenta TI: socket 0000:02:03.0, mfunc 0x01000002, devctl 0x60
[17179598.944000] **** SET: Misaligned resource pointer: dafbd5a2 Type 07 Len 0
[17179598.948000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[17179598.948000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179598.948000] 3c59x: Donald Becker and others. www.scyld.com/network/vortex.html
[17179598.948000] 0000:02:00.0: 3Com PCI 3c905C Tornado at e0a20c00. Vers LK1.1.19
[17179599.096000] Yenta: ISA IRQ mask 0x0000, PCI irq 5
[17179599.096000] Socket status: 30000010
[17179599.096000] pcmcia: parent PCI bridge I/O window: 0xe000 - 0xffff
[17179599.096000] cs: IO port probe 0xe000-0xffff: clean.
[17179599.096000] pcmcia: parent PCI bridge Memory window: 0xf4000000 - 0xfbffffff
[17179599.096000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x36ffffff
[17179599.284000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179599.800000] pccard: PCMCIA card inserted into slot 2
[17179599.904000] cs: memory probe 0xf4000000-0xfbffffff: excluding 0xf4000000-0xf8ffffff 0xfa000000-0xfbffffff
[17179599.904000] pcmcia: registering new device pcmcia2.0
[17179599.964000] cs: IO port probe 0x100-0x3af: clean.
[17179599.968000] cs: IO port probe 0x3e0-0x4ff: clean.
[17179599.968000] cs: IO port probe 0x820-0x8ff: clean.
[17179599.968000] cs: IO port probe 0xc00-0xcf7: clean.
[17179599.968000] cs: IO port probe 0xa00-0xaff: clean.
[17179599.968000] cs: IO port probe 0x100-0x3af: clean.
[17179599.968000] cs: IO port probe 0x3e0-0x4ff: clean.
[17179599.968000] cs: IO port probe 0x820-0x8ff: clean.
[17179599.968000] cs: IO port probe 0xc00-0xcf7: clean.
[17179599.968000] cs: IO port probe 0xa00-0xaff: clean.
[17179599.996000] cs: IO port probe 0x100-0x3af: clean.
[17179599.996000] cs: IO port probe 0x3e0-0x4ff: clean.
[17179599.996000] cs: IO port probe 0x820-0x8ff: clean.
[17179599.996000] cs: IO port probe 0xc00-0xcf7: clean.
[17179599.996000] cs: IO port probe 0xa00-0xaff: clean.
[17179600.060000] orinoco 0.15rc3 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[17179600.064000] orinoco_cs 0.15rc3 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[17179600.148000] eth1: Hardware identity 0005:0004:0005:0000
[17179600.148000] eth1: Station identity  001f:0001:0008:000a
[17179600.148000] eth1: Firmware determined as Lucent/Agere 8.10
[17179600.148000] eth1: Ad-hoc demo mode supported
[17179600.148000] eth1: IEEE standard IBSS ad-hoc mode supported
[17179600.148000] eth1: WEP supported, 104-bit key
[17179600.148000] eth1: MAC address 00:02:2D:6D:A4:C4
[17179600.148000] eth1: Station name "HERMES I"
[17179600.148000] eth1: ready
[17179600.148000] eth1: index 0x01: Vcc 3.3, irq 5, io 0xe100-0xe13f
[17179600.220000] ieee80211_crypt: registered algorithm 'NULL'
[17179600.260000] hostap_cs: 0.4.4-kernel (Jouni Malinen <jkmaline@cc.hut.fi>)
[17179600.336000] NET: Registered protocol family 17
[17179600.644000] lp0: using parport0 (interrupt-driven).
[17179600.728000] Adding 827308k swap on /dev/hda5.  Priority:-1 extents:1 across:827308k
[17179600.744000] eth1: New link status: Connected (0001)
[17179600.872000] EXT3 FS on hda1, internal journal
[17179601.112000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179601.112000] md: bitmap version 4.39
[17179602.032000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[17179602.876000] eth1: New link status: AP Changed (0003)
[17179608.588000] ACPI: AC Adapter [AC] (on-line)
[17179609.004000] ACPI: Battery Slot [BAT0] (battery present)
[17179609.004000] ACPI: Battery Slot [BAT1] (battery absent)
[17179609.104000] ACPI: Lid Switch [LID]
[17179609.104000] ACPI: Power Button (CM) [PBTN]
[17179609.104000] ACPI: Sleep Button (CM) [SBTN]
[17179609.272000] ibm_acpi: ec object not found
[17179609.316000] pcc_acpi: loading...
[17179609.460000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[17179609.776000] NET: Registered protocol family 10
[17179609.776000] lo: Disabled Privacy Extensions
[17179609.776000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179609.776000] IPv6 over IPv4 tunneling driver
[17179615.196000] [drm] Initialized drm 1.0.1 20051102
[17179615.288000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179615.292000] [drm] Initialized radeon 1.24.0 20060225 on minor 0
[17179616.892000] ppdev: user-space parallel port driver
[17179617.388000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179617.388000] apm: overridden by ACPI.
[17179617.632000] [drm] Setting GART location based on new memory map
[17179617.632000] [drm] writeback test succeeded in 1 usecs
[17179620.764000] eth1: no IPv6 routers present
[17179625.552000] Bluetooth: Core ver 2.8
[17179625.552000] NET: Registered protocol family 31
[17179625.552000] Bluetooth: HCI device and connection manager initialized
[17179625.552000] Bluetooth: HCI socket layer initialized
[17179625.608000] Bluetooth: L2CAP ver 2.8
[17179625.608000] Bluetooth: L2CAP socket layer initialized
[17179625.616000] Bluetooth: RFCOMM socket layer initialized
[17179625.616000] Bluetooth: RFCOMM TTY layer initialized
[17179625.616000] Bluetooth: RFCOMM ver 1.7
[17179645.136000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17179645.244000] ISOFS: changing to secondary root
[17179728.052000] usb 1-1: new low speed USB device using uhci_hcd and address 6[17179728.420000] usbcore: registered new driver hiddev
[17179728.440000] input: Logitech USB Receiver as /class/input/input2
[17179728.440000] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-1
[17179728.440000] usbcore: registered new driver usbhid
[17179728.440000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179728.612000] ts: Compaq touchscreen protocol output
[17179773.644000] usb 1-1: USB disconnect, address 6
[17179789.272000] usb 1-1: new low speed USB device using uhci_hcd and address 7[17179789.392000] usb 1-1: device descriptor read/64, error -71
[17179789.616000] usb 1-1: device descriptor read/64, error -71
[17179789.832000] usb 1-1: new low speed USB device using uhci_hcd and address 8[17179789.952000] usb 1-1: device descriptor read/64, error -71
[17179790.180000] usb 1-1: device descriptor read/64, error -71
[17179790.396000] usb 1-1: new low speed USB device using uhci_hcd and address 9[17179790.804000] usb 1-1: device not accepting address 9, error -71
[17179790.916000] usb 1-1: new low speed USB device using uhci_hcd and address 10
[17179791.324000] usb 1-1: device not accepting address 10, error -71
[17180507.676000] eth1: New link status: Disconnected (0002)
[17180511.116000] eth1: New link status: Connected (0001)
[17180519.532000] usb 1-1: new low speed USB device using uhci_hcd and address 11
[17180519.724000] input: Logitech USB Receiver as /class/input/input3
[17180519.724000] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-1
[17180991.760000] usb 1-1: USB disconnect, address 11
[17181004.276000] usb 1-1: new low speed USB device using uhci_hcd and address 12
[17181004.684000] usb 1-1: device not accepting address 12, error -71
[17181004.796000] usb 1-1: new low speed USB device using uhci_hcd and address 13
[17181005.204000] usb 1-1: device not accepting address 13, error -71
[17181005.316000] usb 1-1: new low speed USB device using uhci_hcd and address 14
[17181005.436000] usb 1-1: device descriptor read/64, error -71
[17181005.660000] usb 1-1: device descriptor read/64, error -71
[17181005.876000] usb 1-1: new low speed USB device using uhci_hcd and address 15
[17181005.996000] usb 1-1: device descriptor read/64, error -71
[17181006.220000] usb 1-1: device descriptor read/64, error -71
[17181063.620000] uhci_hcd 0000:00:1d.0: remove, state 1
[17181063.620000] usb usb1: USB disconnect, address 1
[17181063.620000] uhci_hcd 0000:00:1d.0: USB bus 1 deregistered
[17181063.624000] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
[17181255.856000] USB Universal Host Controller Interface driver v2.3
[17181255.856000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17181255.856000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17181255.856000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17181255.860000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17181255.860000] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000bf80
[17181255.880000] hub 1-0:1.0: USB hub found
[17181255.880000] hub 1-0:1.0: 2 ports detected
[17181256.224000] usb 1-1: new low speed USB device using uhci_hcd and address 2[17181256.304000] input: Logitech USB Receiver as /class/input/input4
[17181256.304000] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-1
[17181439.944000] usb 1-1: USB disconnect, address 2
[17181462.884000] usb 1-1: new low speed USB device using uhci_hcd and address 3[17181463.296000] usb 1-1: device not accepting address 3, error -71
[17181463.408000] usb 1-1: new low speed USB device using uhci_hcd and address 4[17181463.816000] usb 1-1: device not accepting address 4, error -71
[17181463.928000] usb 1-1: new low speed USB device using uhci_hcd and address 5[17181464.048000] usb 1-1: device descriptor read/64, error -71
[17181464.272000] usb 1-1: device descriptor read/64, error -71
[17181464.488000] usb 1-1: new low speed USB device using uhci_hcd and address 6[17181464.608000] usb 1-1: device descriptor read/64, error -71
[17181464.832000] usb 1-1: device descriptor read/64, error -71
[17181628.228000] eth1: New link status: Disconnected (0002)
[17181629.468000] eth1: New link status: Connected (0001)
[17182468.640000] eth1: New link status: Disconnected (0002)
[17182469.920000] eth1: New link status: Connected (0001)
[17183309.056000] eth1: New link status: Disconnected (0002)
[17183310.376000] eth1: New link status: Connected (0001)
[17184149.468000] eth1: New link status: Disconnected (0002)
[17184150.624000] eth1: New link status: Connected (0001)
[17184506.048000] uhci_hcd 0000:00:1d.0: remove, state 1
[17184506.048000] usb usb1: USB disconnect, address 1
[17184506.048000] uhci_hcd 0000:00:1d.0: USB bus 1 deregistered
[17184506.052000] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
[17184526.100000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17184711.212000] USB Universal Host Controller Interface driver v2.3
[17184711.212000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17184711.212000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17184711.212000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17184711.216000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17184711.216000] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000bf80
[17184711.216000] hub 1-0:1.0: USB hub found
[17184711.216000] hub 1-0:1.0: 2 ports detected
[17184811.152000] usb 1-1: new low speed USB device using uhci_hcd and address 2[17184811.344000] input: Logitech USB Receiver as /class/input/input5
[17184811.344000] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-1
[17184919.240000] usb 1-1: USB disconnect, address 2
[17184926.876000] usb 1-1: new low speed USB device using uhci_hcd and address 3[17184927.000000] usb 1-1: device descriptor read/64, error -71
[17184927.224000] usb 1-1: device descriptor read/64, error -71
[17184927.440000] usb 1-1: new low speed USB device using uhci_hcd and address 4[17184927.560000] usb 1-1: device descriptor read/64, error -71
[17184927.784000] usb 1-1: device descriptor read/64, error -71
[17184928.000000] usb 1-1: new low speed USB device using uhci_hcd and address 5[17184928.408000] usb 1-1: device not accepting address 5, error -71
[17184928.520000] usb 1-1: new low speed USB device using uhci_hcd and address 6[17184928.928000] usb 1-1: device not accepting address 6, error -71
[17185232.668000] eth1: New link status: Disconnected (0002)
[17185233.956000] eth1: New link status: Connected (0001)
[17185260.104000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17185298.788000] usb 1-1: new low speed USB device using uhci_hcd and address 7[17185298.908000] usb 1-1: device descriptor read/64, error -71
[17185299.132000] usb 1-1: device descriptor read/64, error -71
[17185299.348000] usb 1-1: new low speed USB device using uhci_hcd and address 8[17185299.468000] usb 1-1: device descriptor read/64, error -71
[17185299.692000] usb 1-1: device descriptor read/64, error -71
[17185299.908000] usb 1-1: new low speed USB device using uhci_hcd and address 9[17185300.320000] usb 1-1: device not accepting address 9, error -71
[17185300.432000] usb 1-1: new low speed USB device using uhci_hcd and address 10
[17185300.840000] usb 1-1: device not accepting address 10, error -71
[17186073.080000] eth1: New link status: Disconnected (0002)
[17186074.204000] eth1: New link status: Connected (0001)
[17186436.176000] usb 1-1: new low speed USB device using uhci_hcd and address 11
[17186436.368000] input: Logitech USB Receiver as /class/input/input6
[17186436.368000] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-1
[17187809.836000] usb 1-1: USB disconnect, address 11
[17187822.760000] usb 1-1: new low speed USB device using uhci_hcd and address 12
[17187822.880000] usb 1-1: device descriptor read/64, error -71
[17187823.104000] usb 1-1: device descriptor read/64, error -71
[17187823.320000] usb 1-1: new low speed USB device using uhci_hcd and address 13
[17187823.440000] usb 1-1: device descriptor read/64, error -71
[17187823.664000] usb 1-1: device descriptor read/64, error -71
[17187823.880000] usb 1-1: new low speed USB device using uhci_hcd and address 14
[17187824.288000] usb 1-1: device not accepting address 14, error -71
[17187824.400000] usb 1-1: new low speed USB device using uhci_hcd and address 15
[17187824.808000] usb 1-1: device not accepting address 15, error -71

```

This is the output of lsmod
```
root@Lust:/dev/bus/usb/001# lsmod
Module                  Size  Used by
analog                 12320  0
gameport               15496  1 analog
ohci_hcd               21892  0
uhci_hcd               33680  0
tsdev                   8000  0
usbhid                 39904  0
nls_cp437               5888  1
isofs                  37688  1
udf                    88452  0
binfmt_misc            12296  1
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
ppdev                   9220  0
radeon                116000  1
drm                    73236  2 radeon
speedstep_ich           5260  0
speedstep_lib           4484  1 speedstep_ich
cpufreq_userspace       4696  1
cpufreq_stats           5636  0
freq_table              4740  2 speedstep_ich,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
ipv6                  265728  8
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
i2c_core               21904  1 i2c_acpi_ec
ac                      5252  1 acpi_sbs
dm_mod                 58936  1
md_mod                 72532  0
lp                     11844  0
af_packet              22920  4
hostap_cs              64536  0
hostap                119428  1 hostap_cs
ieee80211_crypt         6272  1 hostap
orinoco_cs             17928  1
orinoco                43156  1 orinoco_cs
hermes                  7808  2 orinoco_cs,orinoco
pcmcia                 40508  2 hostap_cs,orinoco_cs
3c59x                  45608  0
mii                     5888  1 3c59x
yenta_socket           28428  5
rsrc_nonstatic         13440  1 yenta_socket
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
rtc                    13492  0
floppy                 62148  0
pcspkr                  2180  0
serio_raw               7300  0
psmouse                36100  0
snd_intel8x0           33692  1
snd_ac97_codec         93088  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
intel_agp              22940  1
agpgart                34888  2 drm,intel_agp
snd_pcm                89864  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
evdev                   9856  1
ext3                  135688  1
jbd                    58772  1 ext3
ide_generic             1536  0
usbcore               130692  4 ohci_hcd,uhci_hcd,usbhid
ide_cd                 33028  1
cdrom                  38560  1 ide_cd
ide_disk               17664  3
piix                   11012  1
generic                 5124  0
thermal                13576  0
processor              23360  1 thermal
fan                     4868  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit

```

I'm at a loss of what to do next. I've researched a number similar issues many refering to a device /dev/input/js0, which I do not have.

I check /dev/input to make sure.

```
root@Lust:/dev/bus/usb/001# ls /dev/input
event0  event1  mice

```

Does anyone have any ideas, as to what to do next?

---

### Post by jISh on 2006-09-27
Try typing this in console:
```
rmmod ehci-hcd
```
Then trying your pad again.

---

### Post by magelus on 2006-09-28
The module wasn't loaded in the first place
```
adam@Lust:~$ sudo rmmod ehci_hcd
Password:
ERROR: Module ehci_hcd does not exist in /proc/modules
adam@Lust:~$

```

This is what I have as far as usb goes

```
adam@Lust:~$ lsmod|grep usb
usbhid                 39904  0
usbcore               130692  3 usbhid,uhci_hcd

```

---

### Post by magelus on 2006-09-28
I've made some attempts at fixing this problem...

I attempted to disable acpi an apic in /boot/grub/menu.lst, as such...
```
title           Ubuntu, kernel 2.6.15-26-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash noapic acpi=off
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.15-26-386
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
boot

```

though, still I get the following errors in dmesg

```
[  206.382923] usb 1-1: new low speed USB device using uhci_hcd and address 3
[  206.502908] usb 1-1: device descriptor read/64, error -71
[  206.726869] usb 1-1: device descriptor read/64, error -71
[  206.942838] usb 1-1: new low speed USB device using uhci_hcd and address 4
[  207.062829] usb 1-1: device descriptor read/64, error -71
[  207.286785] usb 1-1: device descriptor read/64, error -71
[  207.502753] usb 1-1: new low speed USB device using uhci_hcd and address 5
[  207.910689] usb 1-1: device not accepting address 5, error -71
[  208.022674] usb 1-1: new low speed USB device using uhci_hcd and address 6
[  208.430611] usb 1-1: device not accepting address 6, error -71
[  248.992589] usb 1-1: new low speed USB device using uhci_hcd and address 7

```

---

### Post by magelus on 2006-09-28
If anyone can at least tell me what "device descriptor read/64" that would even be helpful.

---

### Post by magelus on 2006-09-29
PROBELM SOLVED

Turns out error -71  is a low level hardware error, and usually signifies a problem with the device or the chord.  The device and the usb port are know to work so...

I ended up buying a usb hub (a standard 1.1, considering this laptop doesn't have a high speed port) and it recognized my device. Considering I only had one usb port, I needed it anyway.


Hope this help someone down the line.

---

