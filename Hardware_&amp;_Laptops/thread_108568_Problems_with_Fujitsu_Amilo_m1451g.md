---
title: "Problems with Fujitsu Amilo m1451g"
date: 2005-12-26
forum: Hardware &amp; Laptops
---

### Post by ethan29 on 2005-12-26
Hi,

I have installed Ubuntu Linux 5.10 with kernel 2.6.15-6-686. I have achieved sound works but only if I plug headphones, not in integrated loudspeakers. ACPI works badly, because battery status sometimes shows 0% charge and a warning appears. The mainly problem is that DVD drive isn't available for kernel. /dev/cdrom doesn't exits. Dmesg shows this:
```

570.092000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179570.092000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 *7 10 11 12 14 1 5)
[17179570.092000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15 ) *0, disabled.
[17179570.092000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11 12 14 1 5)
[17179570.092000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.092000] pnp: PnP ACPI init
[17179570.100000] pnp: PnP ACPI: found 12 devices
[17179570.100000] PnPBIOS: Disabled by ACPI PNP
[17179570.100000] PCI: Using ACPI for IRQ routing
[17179570.100000] PCI: If a device doesn't work, try "pci=routeirq".  If it help s, post a report
[17179570.100000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[17179570.104000] PCI: Bridge: 0000:00:01.0
[17179570.104000]   IO window: d000-dfff
[17179570.104000]   MEM window: ffd00000-ffdfffff
[17179570.104000]   PREFETCH window: cff00000-dfefffff
[17179570.104000] PCI: Bridge: 0000:00:1c.0
[17179570.104000]   IO window: disabled.
[17179570.104000]   MEM window: bfc00000-bfcfffff
[17179570.104000]   PREFETCH window: bfd00000-bfdfffff
[17179570.104000] PCI: Bridge: 0000:00:1e.0
[17179570.104000]   IO window: c000-cfff
[17179570.104000]   MEM window: ffc00000-ffcfffff
[17179570.104000]   PREFETCH window: disabled.
[17179570.104000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179570.104000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179570.104000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179570.104000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179570.104000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179570.104000] audit: initializing netlink socket (disabled)
[17179570.104000] audit(1135618545.100:1): initialized
[17179570.104000] highmem bounce pool size: 64 pages
[17179570.104000] VFS: Disk quotas dquot_6.5.1
[17179570.104000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.104000] Initializing Cryptographic API
[17179570.104000] io scheduler noop registered
[17179570.104000] io scheduler anticipatory registered
[17179570.104000] io scheduler deadline registered
[17179570.104000] io scheduler cfq registered
[17179570.104000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179570.104000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179570.104000] assign_interrupt_mode Found MSI capability
[17179570.104000] Allocate Port Service[pcie00]
[17179570.104000] Allocate Port Service[pcie03]
[17179570.104000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179570.104000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179570.104000] assign_interrupt_mode Found MSI capability
[17179570.104000] Allocate Port Service[pcie00]
[17179570.104000] Allocate Port Service[pcie02]
[17179570.104000] Allocate Port Service[pcie03]
[17179570.104000] isapnp: Scanning for PnP cards...
[17179570.460000] isapnp: No Plug & Play device found
[17179570.472000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179570.476000] i8042.c: Detected active multiplexing controller, rev 1.0.
[17179570.476000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[17179570.476000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[17179570.476000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[17179570.476000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[17179570.476000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179570.476000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ shari ng enabled
[17179570.476000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 b locksize
[17179570.476000] EISA: Probing bus 0 at eisa.0
[17179570.476000] EISA: Detected 0 cards.
[17179570.476000] NET: Registered protocol family 2
[17179570.484000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179570.516000] IP route cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179570.516000] TCP established hash table entries: 262144 (order: 9, 2097152 bytes)
[17179570.516000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[17179570.516000] TCP: Hash tables configured (established 262144 bind 65536)
[17179570.516000] TCP reno registered
[17179570.516000] TCP bic registered
[17179570.516000] NET: Registered protocol family 8
[17179570.516000] NET: Registered protocol family 20
[17179570.516000] Using IPI No-Shortcut mode
[17179570.516000] ACPI wakeup devices: 
[17179570.516000] P0P1  LAN MC97  AZC P0P5 P0P6 P0P7 P0P3 P0P2 
[17179570.516000] ACPI: (supports S0 S3 S4 S5)
[17179570.516000] Freeing unused kernel memory: 308k freed
[17179570.544000] bitblit: Unknown symbol soft_cursor
[17179570.544000] fbcon: Unknown symbol fbcon_set_bitops
[17179570.548000] vesafb: framebuffer at 0xd0000000, mapped to 0xf8880000, using 3072k, total 32768k
[17179570.548000] vesafb: mode is 1024x768x16, linelength=2048, pages=20
[17179570.548000] vesafb: protected mode interface info at c000:584c
[17179570.548000] vesafb: scrolling: redraw
[17179570.548000] vesafb: Truecolor: size=0:5:6:5, shift=0:11:5:0
[17179570.548000] vesafb: Mode is VGA compatible
[17179570.548000] fb0: VESA VGA frame buffer device
[17179571.628000] Capability LSM initialized
[17179571.632000] Console: switching to colour frame buffer device 128x48
[17179571.636000] NET: Registered protocol family 1
[17179571.644000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[17179571.644000] ACPI: Processor [CPU1] (supports 8 throttling states)
[17179571.660000] ACPI: Thermal Zone [THRM] (71 C)
[17179572.336000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179572.336000] 8139cp: pci dev 0000:01:0c.0 (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[17179572.336000] 8139cp: Try the "8139too" driver instead.
[17179572.340000] 8139too Fast Ethernet driver 0.9.27
[17179572.340000] ACPI: PCI Interrupt 0000:01:0c.0[A] -> GSI 19 (level, low) -> IRQ 201
[17179572.340000] eth0: RealTek RTL8139 at 0xc800, 00:03:0d:30:6f:09, IRQ 201
[17179572.340000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[17179572.348000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179572.348000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179572.348000] ACPI: bus type ide registered
[17179572.348000] SCSI subsystem initialized
[17179572.360000] libata version 1.20 loaded.
[17179572.364000] ahci 0000:00:1f.2: version 1.2
[17179572.364000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 201
[17179572.364000] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[17179572.364000] ahci: probe of 0000:00:1f.2 failed with error -12
[17179572.368000] ata_piix 0000:00:1f.2: version 1.05
[17179572.368000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 201
[17179572.368000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179572.368000] ata1: SATA max UDMA/133 cmd 0x1F0 ctl 0x3F6 bmdma 0xFFA0 irq 14
[17179572.532000] ata1: dev 0 cfg 49:0f00 82:746b 83:7f69 84:4063 85:f469 86:3c49 87:4063 88:203f
[17179572.532000] ata1: dev 0 ATA-7, max UDMA/100, 195371568 sectors: LBA48
[17179572.532000] ata1: dev 0 configured for UDMA/100
[17179572.532000] scsi0 : ata_piix
[17179572.532000]   Vendor: ATA       Model: HTS541010G9SA00   Rev: MBZO
[17179572.532000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179572.532000] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xFFA8 irq 15
[17179572.852000] ata2: dev 0 cfg 49:0b00 82:0000 83:0000 84:0000 85:0000 86:0000 87:0000 88:0407
[17179572.852000] ata2: dev 0 ATAPI, max UDMA/33
[17179572.852000] ata2: dev 0 configured for UDMA/33
[17179572.852000] scsi1 : ata_piix
[17179572.860000] SCSI device sda: 195371568 512-byte hdwr sectors (100030 MB)
[17179572.860000] SCSI device sda: drive cache: write back
[17179572.864000] SCSI device sda: 195371568 512-byte hdwr sectors (100030 MB)
[17179572.864000] SCSI device sda: drive cache: write back
[17179572.864000]  sda: sda1 sda2 sda3 < sda5 >
[17179573.260000] sd 0:0:0:0: Attached scsi disk sda
[17179573.484000] ide0: I/O resource 0x1F0-0x1F7 not free.
[17179573.484000] ide0: ports already in use, skipping probe
[17179573.484000] ide1: I/O resource 0x170-0x177 not free.
[17179573.484000] ide1: ports already in use, skipping probe
[17179573.556000] Attempting manual resume
[17179573.584000] kjournald starting.  Commit interval 5 seconds
[17179573.584000] EXT3-fs: mounted filesystem with ordered data mode.
[17179574.692000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179574.692000] md: bitmap version 4.39
[17179575.832000] Adding 827308k swap on /dev/sda5.  Priority:-1 extents:1 across:827308k
[17179576.076000] EXT3 FS on sda2, internal journal
[17179577.580000] usbcore: registered new driver usbfs
[17179577.580000] usbcore: registered new driver hub
[17179577.588000] Linux agpgart interface v0.101 (c) Dave Jones
[17179577.592000] USB Universal Host Controller Interface driver v2.3
[17179577.592000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 209
[17179577.592000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179577.592000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179577.592000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179577.592000] uhci_hcd 0000:00:1d.0: irq 209, io base 0x0000e480
[17179577.592000] hub 1-0:1.0: USB hub found
[17179577.592000] hub 1-0:1.0: 2 ports detected
[17179577.612000] agpgart: Detected an Intel 915GM Chipset.
[17179577.628000] agpgart: AGP aperture is 256M @ 0x0
[17179577.696000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 201
[17179577.696000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179577.696000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179577.696000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179577.696000] uhci_hcd 0000:00:1d.1: irq 201, io base 0x0000e800
[17179577.696000] hub 2-0:1.0: USB hub found
[17179577.696000] hub 2-0:1.0: 2 ports detected
[17179577.800000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 217
[17179577.800000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179577.800000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179577.800000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179577.800000] uhci_hcd 0000:00:1d.2: irq 217, io base 0x0000e880
[17179577.800000] hub 3-0:1.0: USB hub found
[17179577.800000] hub 3-0:1.0: 2 ports detected
[17179577.876000] hw_random: RNG not detected
[17179577.916000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 169
[17179577.916000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17179577.916000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[17179577.916000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[17179577.916000] uhci_hcd 0000:00:1d.3: irq 169, io base 0x0000ec00
[17179577.916000] hub 4-0:1.0: USB hub found
[17179577.916000] hub 4-0:1.0: 2 ports detected
[17179577.984000] input: PC Speaker as /class/input/input1
[17179577.992000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179577.992000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[17179578.020000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 209
[17179578.020000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179578.020000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179578.020000] ehci_hcd 0000:00:1d.7: debug port 1
[17179578.020000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[17179578.020000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[17179578.020000] ehci_hcd 0000:00:1d.7: irq 209, io mem 0xffeffc00
[17179578.024000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179578.024000] hub 5-0:1.0: USB hub found
[17179578.024000] hub 5-0:1.0: 8 ports detected
[17179578.080000] Real Time Clock Driver v1.12
[17179578.120000] hda_codec: Unknown model for ALC880, trying auto-probe from BIOS...
[17179578.144000] ieee80211_crypt: registered algorithm 'NULL'
[17179578.144000] ieee80211: 802.11 data/management/control stack, git-1.1.7
[17179578.144000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179578.192000] ieee1394: Initialized config rom entry `ip1394'
[17179578.232000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, git-1.0.8
[17179578.232000] ipw2200: Copyright(c) 2003-2005 Intel Corporation
[17179578.232000] Warning: PCI driver ipw2200 has a struct device_driver shutdown method, please update!
[17179578.312000] Synaptics Touchpad, model: 1, fw: 5.10, id: 0x258eb1, caps: 0xa04713/0x0
[17179578.348000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[17179578.360000] ts: Compaq touchscreen protocol output
[17179578.396000] mice: PS/2 mouse device common for all mice
[17179578.680000] ACPI: PCI Interrupt 0000:01:0a.0[A] -> GSI 18 (level, low) -> IRQ 217
[17179578.728000] ACPI: PCI Interrupt 0000:01:03.0[A] -> GSI 21 (level, low) -> IRQ 225
[17179578.728000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[17179578.728000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[217]  MMIO=[ffcff000-ffcff7ff]  Max Packet=[2048]
[17179579.876000] lp: driver loaded but no devices found
[17179579.924000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179579.924000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179580.040000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00030d4950e00fab]
[17179583.068000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[17179586.276000] NET: Registered protocol family 17
[17179588.908000] NET: Registered protocol family 10
[17179588.912000] Disabled Privacy Extensions on device c033efa0(lo)
[17179588.912000] IPv6 over IPv4 tunneling driver
[17179589.868000] ACPI: AC Adapter [AC0] (on-line)
[17179590.016000] ACPI: Battery Slot [BAT0] (battery present)
[17179590.028000] ACPI: Power Button (FF) [PWRF]
[17179590.028000] ACPI: Lid Switch [LID]
[17179590.028000] ACPI: Sleep Button (CM) [SLPB]
[17179590.028000] ACPI: Power Button (CM) [PWRB]
[17179590.060000] ibm_acpi: ec object not found
[17179590.136000] ACPI: Video Device [PEG] (multi-head: yes  rom: no  post: no)
[17179596.624000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179596.624000] apm: overridden by ACPI.
[17179596.864000] Intel ISA PCIC probe: not found.
[17179599.444000] eth0: no IPv6 routers present
[17179711.080000]     ACPI-0412: *** Error: Handler for [EmbeddedControl] returned AE_TIME
[17179711.080000]     ACPI-0508: *** Error: Method execution failed [\_SB_.PCI0.AC0_._PSR] (Node dffe8ba0), AE_TIME
[17179711.180000]     ACPI-0412: *** Error: Handler for [EmbeddedControl] returned AE_TIME
......

```

---

### Post by el_Salmon on 2005-12-29
If DVD drive doesn't appear is very strange. &#191;Have you looking for information in [http://tuxmobil.org/mylaptops.html]("http://tuxmobil.org/mylaptops.html") or [http://ubuntuforums.org/showthread.php?t=88639]("http://ubuntuforums.org/showthread.php?t=88639")?

---

