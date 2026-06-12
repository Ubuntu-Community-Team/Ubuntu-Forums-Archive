---
title: "Maxtor 300GB not mounting"
date: 2007-12-10
forum: Hardware &amp; Laptops
---

### Post by atentik on 2007-12-10
I have a 300GB maxter external harddrive that use to store extra stuff on. It used to auto mount when I had ubuntu 7.04 then I switched to Mandriva, which I did not find great. Then I moved back to Ubuntu when I plugs the hard drive in the USB port, it does not automout. In fact it does not mount.... Is their a way around this... that is to auto mount larger hard drives? Thanks

---

### Post by petterth on 2007-12-10
Hi!
I got 2 external maxtor drives working in ubuntu so it should not be a problem.
what is your output of dmesg ?

What filesystem do you use ? ntfs or ext3 ?

---

### Post by atentik on 2007-12-13
Not sure what format it is in, don't know whether it is ntfs or ext3. Here is the output when I typed dmesg:
> [    3.556000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[    3.556000] ehci_hcd 0000:00:1d.7: debug port 1
[    3.556000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    3.556000] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xc0000000
[    3.560000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.560000] usb usb4: configuration #1 chosen from 1 choice
[    3.560000] hub 4-0:1.0: USB hub found
[    3.560000] hub 4-0:1.0: 6 ports detected
[    3.664000] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[    3.916000] e1000: 0000:02:01.0: e1000_probe: (PCI:33MHz:32-bit) 00:11:25:11:a7:a1
[    3.952000] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[    3.952000] ata_piix 0000:00:1f.1: version 2.11
[    3.952000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[    3.952000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[    3.952000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    3.956000] scsi0 : ata_piix
[    3.956000] scsi1 : ata_piix
[    3.956000] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011860 irq 14
[    3.956000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011868 irq 15
[    4.120000] ata1.00: ATA-6: TOSHIBA MK4026GAX, PA106E, max UDMA/100
[    4.120000] ata1.00: 78140160 sectors, multi 16: LBA 
[    4.128000] ata1.00: configured for UDMA/100
[    4.448000] ata2.00: ATAPI: HL-DT-STCD-RW/DVD DRIVE GCC-4242N, 0201, max UDMA/33
[    4.620000] ata2.00: configured for UDMA/33
[    4.620000] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK4026GA PA10 PQ: 0 ANSI: 5
[    4.624000] scsi 1:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4242N 0201 PQ: 0 ANSI: 5
[    4.636000] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[    4.636000] sd 0:0:0:0: [sda] Write Protect is off
[    4.636000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.636000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.636000] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[    4.636000] sd 0:0:0:0: [sda] Write Protect is off
[    4.636000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.636000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.636000]  sda: sda1 sda2 < sda5 >
[    4.712000] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.716000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.716000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    4.744000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    4.744000] Uniform CD-ROM driver Revision: 3.20
[    4.744000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.768000] usb 3-1: new full speed USB device using uhci_hcd and address 2
[    4.856000] Attempting manual resume
[    4.856000] swsusp: Resume From Partition 8:5
[    4.856000] PM: Checking swsusp image.
[    4.856000] PM: Resume from disk failed.
[    4.892000] kjournald starting.  Commit interval 5 seconds
[    4.892000] EXT3-fs: mounted filesystem with ordered data mode.
[    5.028000] usb 3-1: configuration #1 chosen from 1 choice
[    5.272000] usb 3-2: new full speed USB device using uhci_hcd and address 3
[    5.448000] usb 3-2: configuration #1 chosen from 1 choice
[   13.608000] Linux agpgart interface v0.102 (c) Dave Jones
[   13.780000] agpgart: Detected an Intel 855PM Chipset.
[   13.792000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   13.796000] agpgart: AGP aperture is 256M @ 0xd0000000
[   13.796000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.000000] iTCO_vendor_support: vendor-support=0
[   14.140000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   14.140000] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x1060)
[   14.140000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   15.048000] intel_rng: FWH not detected
[   15.052000] Yenta: CardBus bridge found at 0000:02:00.0 [1014:0552]
[   15.052000] Yenta: Using INTVAL to route CSC interrupts to PCI
[   15.052000] Yenta: Routing CardBus interrupts to PCI
[   15.052000] Yenta TI: socket 0000:02:00.0, mfunc 0x01d21b22, devctl 0x64
[   15.060000] Bluetooth: Core ver 2.11
[   15.060000] NET: Registered protocol family 31
[   15.060000] Bluetooth: HCI device and connection manager initialized
[   15.060000] Bluetooth: HCI socket layer initialized
[   15.072000] ieee80211_crypt: registered algorithm 'NULL'
[   15.072000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   15.072000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   15.092000] Bluetooth: HCI USB driver ver 2.9
[   15.092000] usbcore: registered new interface driver hci_usb
[   15.148000] input: PC Speaker as /class/input/input2
[   15.188000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[   15.188000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   15.284000] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
[   15.284000] Socket status: 30000086
[   15.284000] pcmcia: parent PCI bridge I/O window: 0x4000 - 0x8fff
[   15.284000] cs: IO port probe 0x4000-0x8fff: clean.
[   15.284000] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xcfffffff
[   15.284000] pcmcia: parent PCI bridge Memory window: 0xe8000000 - 0xefffffff
[   15.284000] Yenta: CardBus bridge found at 0000:02:00.1 [1014:0552]
[   15.284000] Yenta: Using INTVAL to route CSC interrupts to PCI
[   15.284000] Yenta: Routing CardBus interrupts to PCI
[   15.284000] Yenta TI: socket 0000:02:00.1, mfunc 0x01d21b22, devctl 0x64
[   15.424000] irda_init()
[   15.424000] NET: Registered protocol family 23
[   15.516000] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
[   15.516000] Socket status: 30000086
[   15.516000] pcmcia: parent PCI bridge I/O window: 0x4000 - 0x8fff
[   15.516000] cs: IO port probe 0x4000-0x8fff: clean.
[   15.516000] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xcfffffff
[   15.516000] pcmcia: parent PCI bridge Memory window: 0xe8000000 - 0xefffffff
[   15.520000] ACPI: PCI Interrupt 0000:02:02.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   15.520000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   15.744000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   15.768000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   15.768000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   15.796000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x2c6ab1, caps: 0x884793/0x0
[   15.796000] serio: Synaptics pass-through port at isa0060/serio1/input0
[   15.836000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   15.840000] parport_pc 00:0b: reported by Plug and Play ACPI
[   15.840000] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
[   15.936000] pnp: Device 00:0c activated.
[   15.936000] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[   15.936000] nsc-ircc, chip->init
[   15.936000] nsc-ircc, Found chip at base=0x02e
[   15.936000] nsc-ircc, driver loaded (Dag Brattli)
[   15.936000] IrDA: Registered device irda0
[   15.936000] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500
[   16.108000] cs: IO port probe 0x100-0x3af: clean.
[   16.108000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   16.108000] cs: IO port probe 0x820-0x8ff: clean.
[   16.108000] cs: IO port probe 0xc00-0xcf7: clean.
[   16.108000] cs: IO port probe 0xa00-0xaff: clean.
[   16.112000] cs: IO port probe 0x100-0x3af: clean.
[   16.112000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   16.112000] cs: IO port probe 0x820-0x8ff: clean.
[   16.112000] cs: IO port probe 0xc00-0xcf7: clean.
[   16.112000] cs: IO port probe 0xa00-0xaff: clean.
[   16.692000] intel8x0_measure_ac97_clock: measured 55337 usecs
[   16.692000] intel8x0: clocking to 48000
[   17.296000] lp0: using parport0 (interrupt-driven).
[   17.340000] Adding 1646620k swap on /dev/sda5.  Priority:-1 extents:1 across:1646620k
[   17.632000] EXT3 FS on sda1, internal journal
[   18.896000] input: Power Button (FF) as /class/input/input4
[   18.900000] ACPI: Power Button (FF) [PWRF]
[   18.944000] input: Lid Switch as /class/input/input5
[   18.948000] ACPI: Lid Switch [LID]
[   18.996000] input: Sleep Button (CM) as /class/input/input6
[   19.000000] ACPI: Sleep Button (CM) [SLPB]
[   19.020000] ACPI: Battery Slot [BAT0] (battery present)
[   19.052000] ACPI: AC Adapter [AC] (on-line)
[   19.088000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   19.108000] ACPI: ACPI Dock Station Driver 
[   19.148000] ACPI: \_SB_.PCI0.IDE0.SCND.MSTR: found ejectable bay
[   19.148000] ACPI: \_SB_.PCI0.IDE0.SCND.MSTR: Adding notify handler
[   19.148000] ACPI: Error installing bay notify handler
[   19.148000] ACPI: Bay [\_SB_.PCI0.IDE0.SCND.MSTR] Added
[   20.520000] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   20.520000] PCI: Setting latency timer of device 0000:00:1f.6 to 64
[   20.632000] MC'97 1 converters and GPIO not ready (0xff00)
[   21.164000] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   21.392000] input: TPPS/2 IBM TrackPoint as /class/input/input7
[   22.372000] [drm] Initialized drm 1.1.0 20060810
[   22.392000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   22.396000] [drm] Initialized radeon 1.27.0 20060524 on minor 0
[   22.832000] ppdev: user-space parallel port driver
[   23.168000] audit(1197499432.851:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4779 profile="/usr/sbin/cupsd"
[   23.224000] IBM machine detected. Enabling interrupts during APM calls.
[   23.224000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   23.224000] apm: overridden by ACPI.
[   23.460000] thinkpad_acpi: ThinkPad ACPI Extras v0.14
[   23.460000] thinkpad_acpi: [http://ibm-acpi.sf.net/](http://ibm-acpi.sf.net/)
[   23.460000] thinkpad_acpi: ThinkPad EC firmware 1RHT71WW-3.04
[   23.464000] thinkpad_acpi: another device driver is already handling bay events
[   23.464000] thinkpad_acpi: disabling subdriver bay
[   23.616000] Failure registering capabilities with primary security module.
[   23.812000] Bluetooth: L2CAP ver 2.8
[   23.812000] Bluetooth: L2CAP socket layer initialized
[   23.904000] Bluetooth: RFCOMM socket layer initialized
[   23.904000] Bluetooth: RFCOMM TTY layer initialized
[   23.904000] Bluetooth: RFCOMM ver 1.8
[   24.020000] Clocksource tsc unstable (delta = -84026061 ns)
[   24.760000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   24.760000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   24.760000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   26.068000] [drm] Setting GART location based on new memory map
[   26.068000] [drm] writeback test succeeded in 2 usecs
[   68.624000] NET: Registered protocol family 17
[   79.144000] NET: Registered protocol family 10
[   79.144000] lo: Disabled Privacy Extensions
[   79.144000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   89.760000] eth1: no IPv6 routers present
[26267.452000] ACPI: PCI interrupt for device 0000:02:01.0 disabled
[26268.016000] ACPI: PCI interrupt for device 0000:02:02.0 disabled
[26268.140000] ieee80211_crypt: unregistered algorithm 'NULL'
[26271.048000] PM: suspend-to-disk mode set to 'shutdown'
[26271.048000] swsusp: Basic memory bitmaps created
[26271.048000] Stopping tasks ... done.
[26271.228000] Shrinking memory... done (376472 pages freed)
[26277.768000] Freed 1505888 kbytes in 6.54 seconds (230.25 MB/s)
[26277.768000] Suspending console(s)
[26278.212000] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[26278.212000] usb_device usbdev4.1: PM: suspend 0->1, parent usb4 already 2
[26278.212000] usb_endpoint usbdev4.1_ep81: PM: suspend 0->1, parent 4-0:1.0 already 2
[26278.212000] hub 4-0:1.0: PM: suspend 2->1, parent usb4 already 2
[26278.212000] usb_endpoint usbdev4.1_ep00: PM: suspend 0->1, parent usb4 already 2
[26278.212000] usb_device usbdev2.1: PM: suspend 0->1, parent usb2 already 2
[26278.212000] usb_endpoint usbdev2.1_ep81: PM: suspend 0->1, parent 2-0:1.0 already 2
[26278.212000] hub 2-0:1.0: PM: suspend 2->1, parent usb2 already 2
[26278.212000] usb_endpoint usbdev2.1_ep00: PM: suspend 0->1, parent usb2 already 2
[26278.212000] usb_device usbdev1.1: PM: suspend 0->1, parent usb1 already 2
[26278.212000] usb_endpoint usbdev1.1_ep81: PM: suspend 0->1, parent 1-0:1.0 already 2
[26278.212000] hub 1-0:1.0: PM: suspend 2->1, parent usb1 already 2
[26278.212000] usb_endpoint usbdev1.1_ep00: PM: suspend 0->1, parent usb1 already 2
[26278.212000] pnp: Device 00:0c disabled.
[26278.212000] pnp: Device 00:0b disabled.
[26278.212000] pnp: Device 00:0a disabled.
[26278.212000] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[26278.228000] ACPI: PCI interrupt for device 0000:00:1f.5 disabled
[26278.228000] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[26278.228000] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
[26278.244000] ACPI: PCI interrupt for device 0000:00:1d.2 disabled
[26278.244000] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
[26278.244000] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
[26278.244000] Disabling non-boot CPUs ...
[26278.244000] PM: snapshotting memory.
[26278.244000] swsusp: critical section: 
[26278.244000] swsusp: Need to copy 126054 pages
[26278.244000] swsusp: Normal pages needed: 26919 + 1024 + 40, available pages: 202453
[26278.244000] PM: Image restored successfully.
[26278.244000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[26278.244000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[26278.244000] usb usb1: root hub lost power or was reset
[26278.244000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[26278.244000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[26278.244000] usb usb2: root hub lost power or was reset
[26278.244000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[26278.244000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[26278.244000] usb usb3: root hub lost power or was reset
[26278.260000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
[26278.260000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[26278.260000] usb usb4: root hub lost power or was reset
[26278.260000] ehci_hcd 0000:00:1d.7: debug port 1
[26278.260000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[26278.264000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[26278.264000] PM: Writing back config space on device 0000:00:1f.1 at offset 1 (was 2800003, writing 2800007)
[26278.264000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[26278.264000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[26278.264000] PM: Writing back config space on device 0000:00:1f.5 at offset 1 (was 2900007, writing 2900003)
[26278.268000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[26278.268000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[26278.444000] ata1.00: configured for UDMA/100
[26278.444000] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[26278.444000] sd 0:0:0:0: [sda] Write Protect is off
[26278.444000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[26278.444000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[26278.928000] ata2.00: configured for UDMA/33
[26279.296000] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[26279.296000] PCI: Setting latency timer of device 0000:00:1f.6 to 64
[26280.300000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[26280.300000] PM: Writing back config space on device 0000:02:00.0 at offset f (was 3c0010b, writing 5c0010b)
[26280.300000] PM: Writing back config space on device 0000:02:00.0 at offset 3 (was 824008, writing 82a820)
[26280.300000] PM: Writing back config space on device 0000:02:00.0 at offset 1 (was 2100107, writing 2100007)
[26280.300000] PM: Writing back config space on device 0000:02:00.1 at offset f (was 3c0020b, writing 5c0020b)
[26280.300000] PM: Writing back config space on device 0000:02:00.1 at offset 3 (was 824008, writing 82a820)
[26280.300000] PM: Writing back config space on device 0000:02:00.1 at offset 1 (was 2100107, writing 2100007)
[26280.300000] PM: Writing back config space on device 0000:02:01.0 at offset 1 (was 2300110, writing 2300113)
[26280.300000] PM: Writing back config space on device 0000:02:02.0 at offset 1 (was 2900116, writing 2900102)
[26280.300000] pnp: Device 00:0a activated.
[26280.300000] pnp: Device 00:0b activated.
[26280.304000] pnp: Device 00:0c activated.
[26281.024000] sd 0:0:0:0: [sda] Starting disk
[26281.076000] usb_endpoint usbdev3.2_ep00: PM: resume from 0, parent 3-1 still 1
[26281.076000] hci_usb 3-1:1.0: PM: resume from 1, parent 3-1 still 1
[26281.076000] usb_endpoint usbdev3.2_ep81: PM: resume from 0, parent 3-1:1.0 still 1
[26281.076000] usb_endpoint usbdev3.2_ep02: PM: resume from 0, parent 3-1:1.0 still 1
[26281.076000] usb_endpoint usbdev3.2_ep82: PM: resume from 0, parent 3-1:1.0 still 1
[26281.076000] hci_usb 3-1:1.1: PM: resume from 1, parent 3-1 still 1
[26281.076000] usb 3-1:1.2: PM: resume from 1, parent 3-1 still 1
[26281.076000] usb_device usbdev3.2: PM: resume from 0, parent 3-1 still 1
[26281.076000] usb_endpoint usbdev3.3_ep00: PM: resume from 0, parent 3-2 still 1
[26281.076000] usb 3-2:1.0: PM: resume from 1, parent 3-2 still 1
[26281.076000] usb_endpoint usbdev3.3_ep81: PM: resume from 0, parent 3-2:1.0 still 1
[26281.076000] usb_endpoint usbdev3.3_ep02: PM: resume from 0, parent 3-2:1.0 still 1
[26281.076000] usb_endpoint usbdev3.3_ep83: PM: resume from 0, parent 3-2:1.0 still 1
[26281.076000] usb_device usbdev3.3: PM: resume from 0, parent 3-2 still 1
[26281.076000] usb_endpoint usbdev3.2_ep03: PM: resume from 0, parent 3-1:1.1 still 1
[26281.076000] usb_endpoint usbdev3.2_ep83: PM: resume from 0, parent 3-1:1.1 still 1
[26281.076000] bluetooth hci0: PM: resume from 0, parent 3-1:1.0 still 1
[26283.484000] Restarting tasks ... done.
[26283.512000] swsusp: Basic memory bitmaps freed
[26283.516000] usb 3-1: USB disconnect, address 2
[26283.912000] usb 3-2: USB disconnect, address 3
[26284.760000] usb 3-1: new full speed USB device using uhci_hcd and address 4
[26285.016000] usb 3-1: configuration #1 chosen from 1 choice
[26285.264000] usb 3-2: new full speed USB device using uhci_hcd and address 5
[26285.440000] usb 3-2: configuration #1 chosen from 1 choice
[26303.724000] Intel(R) PRO/1000 Network Driver - version 7.3.20-k2-NAPI
[26303.724000] Copyright (c) 1999-2006 Intel Corporation.
[26303.728000] PCI: Enabling device 0000:02:01.0 (0000 -> 0003)
[26303.728000] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[26303.728000] PCI: Setting latency timer of device 0000:02:01.0 to 64
[26303.980000] e1000: 0000:02:01.0: e1000_probe: (PCI:33MHz:32-bit) 00:11:25:11:a7:a1
[26304.060000] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[26304.292000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[26304.320000] ieee80211_crypt: registered algorithm 'NULL'
[26304.328000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[26304.328000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[26304.352000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[26304.352000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[26304.352000] ACPI: PCI Interrupt 0000:02:02.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[26304.352000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[26304.716000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[26308.244000] input: Power Button (FF) as /class/input/input8
[26308.244000] ACPI: Power Button (FF) [PWRF]
[26308.244000] input: Lid Switch as /class/input/input9
[26308.244000] ACPI: Lid Switch [LID]
[26308.244000] input: Sleep Button (CM) as /class/input/input10
[26308.244000] ACPI: Sleep Button (CM) [SLPB]
[26308.616000] ACPI: Thermal Zone [THM0] (30 C)
[26308.760000] thinkpad_acpi: ThinkPad ACPI Extras v0.14
[26308.760000] thinkpad_acpi: [http://ibm-acpi.sf.net/](http://ibm-acpi.sf.net/)
[26308.760000] thinkpad_acpi: ThinkPad EC firmware 1RHT71WW-3.04
[26308.764000] thinkpad_acpi: another device driver is already handling bay events
[26308.764000] thinkpad_acpi: disabling subdriver bay
[26308.832000] ACPI: AC Adapter [AC] (on-line)
[26308.864000] ACPI: Battery Slot [BAT0] (battery present)
[26309.364000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[26309.364000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[26309.364000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[26317.688000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[26337.996000] eth1: no IPv6 routers present
[30059.340000] usb 4-4: new high speed USB device using ehci_hcd and address 11
[30059.828000] usb 4-4: new high speed USB device using ehci_hcd and address 13
[30060.088000] ehci_hcd 0000:00:1d.7: port 4 reset error -110
[30060.088000] hub 4-0:1.0: hub_port_status failed (err = -32)
[30062.244000] usb 4-4: new high speed USB device using ehci_hcd and address 22
[30062.732000] usb 4-4: new high speed USB device using ehci_hcd and address 24
[30066.228000] usb 4-4: new high speed USB device using ehci_hcd and address 42
[30066.716000] usb 4-4: new high speed USB device using ehci_hcd and address 44
[30068.332000] usb 4-4: new high speed USB device using ehci_hcd and address 52
[30068.592000] ehci_hcd 0000:00:1d.7: port 4 reset error -110
[30068.592000] hub 4-0:1.0: hub_port_status failed (err = -32)
[30070.372000] usb 4-4: new high speed USB device using ehci_hcd and address 59
[30071.424000] usb 4-4: new high speed USB device using ehci_hcd and address 64
[30072.852000] usb 4-4: new high speed USB device using ehci_hcd and address 71
[30074.468000] usb 4-4: new high speed USB device using ehci_hcd and address 79
[30076.648000] usb 4-4: new high speed USB device using ehci_hcd and address 90
[30082.776000] usb 4-4: new high speed USB device using ehci_hcd and address 122
[30087.212000] usb 4-4: new high speed USB device using ehci_hcd and address 19
[30088.640000] usb 4-4: new high speed USB device using ehci_hcd and address 26
[30092.324000] usb 4-4: new high speed USB device using ehci_hcd and address 45
[30092.584000] ehci_hcd 0000:00:1d.7: port 4 reset error -110
[30092.584000] hub 4-0:1.0: hub_port_status failed (err = -32)
[30094.176000] usb 4-4: new high speed USB device using ehci_hcd and address 51
[30097.672000] usb 4-4: new high speed USB device using ehci_hcd and address 69
[30098.724000] usb 4-4: new high speed USB device using ehci_hcd and address 74
[30100.340000] usb 4-4: new high speed USB device using ehci_hcd and address 82
[30101.016000] usb 4-4: new high speed USB device using ehci_hcd and address 85
[30101.692000] usb 4-4: new high speed USB device using ehci_hcd and address 88
[30102.180000] usb 4-4: new high speed USB device using ehci_hcd and address 90
[30103.232000] usb 4-4: new high speed USB device using ehci_hcd and address 95
[30103.492000] ehci_hcd 0000:00:1d.7: port 4 reset error -110
[30103.492000] hub 4-0:1.0: hub_port_status failed (err = -32)
[30105.084000] usb 4-4: new high speed USB device using ehci_hcd and address 101
[30111.964000] usb 4-4: new high speed USB device using ehci_hcd and address 11
[30112.828000] usb 4-4: new high speed USB device using ehci_hcd and address 15
[30113.088000] ehci_hcd 0000:00:1d.7: port 4 reset error -110
[30113.088000] hub 4-0:1.0: hub_port_status failed (err = -32)
[30117.500000] usb 4-4: new high speed USB device using ehci_hcd and address 36
[30117.760000] ehci_hcd 0000:00:1d.7: port 4 reset error -110
[30117.760000] hub 4-0:1.0: hub_port_status failed (err = -32)
[30118.372000] ehci_hcd 0000:00:1d.7: port 4 reset error -110
[30118.372000] hub 4-0:1.0: hub_port_status failed (err = -32)
[30118.372000] hub 4-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[30118.876000] usb 4-4: new high speed USB device using ehci_hcd and address 38
[30120.116000] usb 4-4: new high speed USB device using ehci_hcd and address 44
[30121.544000] usb 4-4: new high speed USB device using ehci_hcd and address 51
[30123.348000] usb 4-4: new high speed USB device using ehci_hcd and address 60
[30124.212000] usb 4-4: new high speed USB device using ehci_hcd and address 64
[30125.076000] usb 4-4: new high speed USB device using ehci_hcd and address 68
[30125.940000] usb 4-4: new high speed USB device using ehci_hcd and address 72
[30126.240000] usb 4-4: new high speed USB device using ehci_hcd and address 73
[30127.668000] usb 4-4: new high speed USB device using ehci_hcd and address 80
[30128.532000] usb 4-4: new high speed USB device using ehci_hcd and address 84
[30129.772000] usb 4-4: new high speed USB device using ehci_hcd and address 90
[30130.072000] usb 4-4: new high speed USB device using ehci_hcd and address 91
[30131.500000] usb 4-4: new high speed USB device using ehci_hcd and address 98
[30131.800000] usb 4-4: new high speed USB device using ehci_hcd and address 99
[30132.288000] usb 4-4: new high speed USB device using ehci_hcd and address 101
[30132.548000] ehci_hcd 0000:00:1d.7: port 4 reset error -110
[30132.548000] hub 4-0:1.0: hub_port_status failed (err = -32)
[30134.704000] usb 4-4: new high speed USB device using ehci_hcd and address 110
[30135.944000] usb 4-4: new high speed USB device using ehci_hcd and address 116
[30139.628000] usb 4-4: new high speed USB device using ehci_hcd and address 9
[30140.868000] usb 4-4: new high speed USB device using ehci_hcd and address 15
[30142.860000] usb 4-4: new high speed USB device using ehci_hcd and address 25
[30143.120000] ehci_hcd 0000:00:1d.7: port 4 reset error -110
[30143.120000] hub 4-0:1.0: hub_port_status failed (err = -32)
[30147.908000] usb 4-4: new high speed USB device using ehci_hcd and address 48
[30148.208000] usb 4-4: new high speed USB device using ehci_hcd and address 49
[30150.764000] usb 4-4: new high speed USB device using ehci_hcd and address 62
[30151.024000] ehci_hcd 0000:00:1d.7: port 4 reset error -110
[30151.024000] hub 4-0:1.0: hub_port_status failed (err = -32)
[30151.676000] usb 4-4: new high speed USB device using ehci_hcd and address 63
[30153.480000] usb 4-4: new high speed USB device using ehci_hcd and address 72
[30156.788000] usb 4-4: new high speed USB device using ehci_hcd and address 89
[30157.652000] usb 4-4: new high speed USB device using ehci_hcd and address 93
[30164.908000] usb 4-4: new high speed USB device using ehci_hcd and address 5
[30165.168000] ehci_hcd 0000:00:1d.7: port 4 reset error -110
[30165.168000] hub 4-0:1.0: hub_port_status failed (err = -32)
[30168.264000] usb 4-4: new high speed USB device using ehci_hcd and address 19
[30181.348000] usb 4-4: new high speed USB device using ehci_hcd and address 88
[30181.648000] usb 4-4: new high speed USB device using ehci_hcd and address 89
[30185.144000] usb 4-4: new high speed USB device using ehci_hcd and address 107
[30187.324000] usb 4-4: new high speed USB device using ehci_hcd and address 118
[30187.584000] ehci_hcd 0000:00:1d.7: port 4 reset error -110
[30187.584000] hub 4-0:1.0: hub_port_status failed (err = -32)
[30188.196000] ehci_hcd 0000:00:1d.7: port 4 reset error -110
[30188.196000] hub 4-0:1.0: hub_port_status failed (err = -32)
[30188.196000] hub 4-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[30188.888000] usb 4-4: new high speed USB device using ehci_hcd and address 121
[30189.188000] usb 4-4: new high speed USB device using ehci_hcd and address 122
[30194.000000] usb 4-4: new high speed USB device using ehci_hcd and address 21
[30195.052000] usb 4-4: new high speed USB device using ehci_hcd and address 26
[30195.312000] ehci_hcd 0000:00:1d.7: port 4 reset error -110
[30195.312000] hub 4-0:1.0: hub_port_status failed (err = -32)
[30195.964000] usb 4-4: new high speed USB device using ehci_hcd and address 27
[30197.392000] usb 4-4: new high speed USB device using ehci_hcd and address 34
[30204.460000] usb 4-4: new high speed USB device using ehci_hcd and address 71
[30204.760000] usb 4-4: new high speed USB device using ehci_hcd and address 72
[30205.812000] usb 4-4: new high speed USB device using ehci_hcd and address 77
[30206.072000] ehci_hcd 0000:00:1d.7: port 4 reset error -110
[30206.072000] hub 4-0:1.0: hub_port_status failed (err = -32)
[30206.724000] usb 4-4: new high speed USB device using ehci_hcd and address 78
[30208.340000] usb 4-4: new high speed USB device using ehci_hcd and address 86
[30210.332000] usb 4-4: new high speed USB device using ehci_hcd and address 96
[30211.008000] usb 4-4: new high speed USB device using ehci_hcd and address 99
[30212.624000] usb 4-4: new high speed USB device using ehci_hcd and address 107
[30213.112000] usb 4-4: new high speed USB device using ehci_hcd and address 109
[30213.600000] usb 4-4: new high speed USB device using ehci_hcd and address 111
[30215.404000] usb 4-4: new high speed USB device using ehci_hcd and address 120
[30216.080000] usb 4-4: new high speed USB device using ehci_hcd and address 123
[30216.944000] usb 4-4: new high speed USB device using ehci_hcd and address 127
[30220.816000] usb 4-4: new high speed USB device using ehci_hcd and address 21  

---

