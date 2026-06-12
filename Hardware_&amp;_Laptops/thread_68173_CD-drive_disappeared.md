---
title: "CD-drive disappeared"
date: 2005-09-22
forum: Hardware &amp; Laptops
---

### Post by perkeleet on 2005-09-22
Hi.

Soon after installing Ubuntu, my CD-drive decided to stop working. It used to locate at /dev/hdd, but now it won't show up even in BIOS setup. There should be no physical damage.

I've tried the following commands with absolutely no effect

modprobe ide_cd
sudo mount /media/cdrom0 -o unhide

fstab:
```

#/etc/fstab: static file system information.
#
      <file system> <mount point> <type> <options> <dump> <pass>
      proc /proc proc defaults 0 0
      /dev/hda1 / ext3 defaults,errors=remount-ro 0 1
      /dev/hda5 none swap sw 0 0
      /dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0

```

dmesg doesn't say anything about the CD drive and it just seems to skip over the phase, where it should appear.

I'd really appreciate your help. Getting really desperate here...  ](*,)

---

### Post by perkeleet on 2005-09-22
Here's the full dmesg info:

```
[4294669.657000] PCI: setting IRQ 11 as level-triggered
[4294669.657000] ACPI: PCI Interrupt 0000:00:10.3[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4294669.657000] ehci_hcd 0000:00:10.3: VIA Technologies, Inc. USB 2.0
[4294669.657000] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 3
[4294669.657000] ehci_hcd 0000:00:10.3: irq 11, io mem 0xf0000000
[4294669.657000] ehci_hcd 0000:00:10.3: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[4294669.657000] hub 3-0:1.0: USB hub found
[4294669.658000] hub 3-0:1.0: 4 ports detected
[4294669.706000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294669.706000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294669.706000] ACPI: bus type ide registered
[4294669.747000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[4294669.747000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[4294669.752000] eth0: VIA Rhine II at 0x1e300, 00:40:d0:59:b7:e2, IRQ 10.
[4294669.752000] eth0: MII PHY found at address 1, status 0x7869 advertising 05e1 Link 4061.
[4294671.806000] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[4294671.807000] ACPI: PCI Interrupt 0000:00:11.1[A]: no GSI
[4294671.807000] VP_IDE: chipset revision 6
[4294671.807000] VP_IDE: not 100% native mode: will probe irqs later
[4294671.807000] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
[4294671.807000]     ide0: BM-DMA at 0x1100-0x1107, BIOS settings: hda:DMA, hdb:pio
[4294671.807000]     ide1: BM-DMA at 0x1108-0x110f, BIOS settings: hdc:pio, hdd:pio
[4294671.807000] Probing IDE interface ide0...
[4294672.190000] hda: TOSHIBA MK3021GAS, ATA DISK drive
[4294672.802000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294672.802000] Probing IDE interface ide1...
[4294673.321000] Probing IDE interface ide1...
[4294673.839000] Probing IDE interface ide2...
[4294674.351000] Probing IDE interface ide3...
[4294674.863000] Probing IDE interface ide4...
[4294675.375000] Probing IDE interface ide5...
[4294675.892000] hda: max request size: 128KiB
[4294675.957000] hda: 58605120 sectors (30005 MB), CHS=58140/16/63, UDMA(100)
[4294675.957000] hda: cache flushes supported
[4294675.957000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
[4294676.249000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[4294676.259000] vga16fb: initializing
[4294676.259000] vga16fb: mapped to 0xc00a0000
[4294676.418000] Console: switching to colour frame buffer device 80x30
[4294676.418000] fb0: VGA16 VGA frame buffer device
[4294676.642000] Attempting manual resume
[4294676.674000] swsusp: Suspend partition has wrong signature?
[4294676.748000] kjournald starting.  Commit interval 5 seconds
[4294676.748000] EXT3-fs: mounted filesystem with ordered data mode.
[4294678.670000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294682.809000] Adding 658624k swap on /dev/hda5.  Priority:-1 extents:1
[4294683.168000] EXT3 FS on hda1, internal journal
[4294693.958000] lp: driver loaded but no devices found
[4294693.981000] mice: PS/2 mouse device common for all mice
[4294694.797000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x254ab1, caps: 0x804713/0x0
[4294694.799000] input: SynPS/2 Synaptics TouchPad on isa0060/serio1
[4294697.339000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294701.111000] Linux agpgart interface v0.101 (c) Dave Jones
[4294701.128000] agpgart: Detected VIA Apollo Pro266 chipset
[4294701.168000] agpgart: AGP aperture is 64M @ 0xa0000000
[4294701.309000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294701.320000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294701.320000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294701.467000] Linux Kernel Card Services
[4294701.467000]   options:  [pci] [cardbus] [pm]
[4294701.494000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKB] -> GSI 7 (level, low) -> IRQ 7
[4294701.494000] Yenta: CardBus bridge found at 0000:00:09.0 [1734:1054]
[4294701.615000] Yenta: ISA IRQ mask 0x0000, PCI irq 7
[4294701.615000] Socket status: 30000006
[4294702.020000] irda_init()
[4294702.020000] NET: Registered protocol family 23
[4294702.608000] via82xx: Assuming DXS channels with 48k fixed sample rate.
[4294702.608000]          Please try dxs_support=5 option
[4294702.608000]          and report if it works on your machine.
[4294702.608000]          For more details, read ALSA-Configuration.txt.
[4294702.609000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5
[4294702.609000] PCI: setting IRQ 5 as level-triggered
[4294702.609000] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[4294702.609000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[4294704.046000] ACPI: PCI Interrupt 0000:00:11.6[C] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[4294704.047000] PCI: Setting latency timer of device 0000:00:11.6 to 64
[4294706.463000] Real Time Clock Driver v1.12
[4294706.585000] input: PC Speaker
[4294707.310000] ts: Compaq touchscreen protocol output
[4294709.723000] eth0: link up, 10Mbps, full-duplex, lpa 0x4061
[4294709.743000] NET: Registered protocol family 17
[4294710.896000] ACPI: AC Adapter [AC] (off-line)
[4294710.969000] ACPI: Battery Slot [BAT0] (battery present)
[4294711.004000] ACPI: Power Button (FF) [PWRF]
[4294711.004000] ACPI: Sleep Button (CM) [SBTN]
[4294711.004000] ACPI: Lid Switch [LID]
[4294711.145000] Using specific hotkey driver
[4294711.197000] ibm_acpi: ec object not found
[4294724.107000] apm: BIOS not found.
[4294724.796000] cs: IO port probe 0x100-0x4ff: excluding 0x170-0x177 0x370-0x377
[4294724.801000] cs: IO port probe 0xc00-0xcff: clean.
[4294724.802000] cs: IO port probe 0xa00-0xaff: clean.
[4294725.184000] powernow: PowerNOW! Technology present. Can scale: frequency and voltage.
[4294725.189000] Detected 1997.114 MHz processor.
[4294725.194000] powernow: SGTC: 13333
[4294725.194000] powernow: Minimum speed 665 MHz. Maximum speed 1997 MHz.
[4294725.398000] Bluetooth: Core ver 2.7
[4294725.398000] NET: Registered protocol family 31
[4294725.398000] Bluetooth: HCI device and connection manager initialized
[4294725.399000] Bluetooth: HCI socket layer initialized
[4294725.423000] Bluetooth: L2CAP ver 2.7
[4294725.423000] Bluetooth: L2CAP socket layer initialized
[4294725.502000] Bluetooth: RFCOMM ver 1.5
[4294725.502000] Bluetooth: RFCOMM socket layer initialized
[4294725.502000] Bluetooth: RFCOMM TTY layer initialized
[4294743.709000] NET: Registered protocol family 10
[4294743.710000] Disabled Privacy Extensions on device c02eb280(lo)
[4294743.710000] IPv6 over IPv4 tunneling driver
[4294753.951000] eth0: no IPv6 routers present

```

And to be more specific, the CD-drive shows up as 'DISABLED' in bios setup. (Contrary to 'NONE' as with floppy drive)

---

