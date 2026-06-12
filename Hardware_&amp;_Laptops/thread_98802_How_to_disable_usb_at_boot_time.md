---
title: "How to disable usb at boot time?"
date: 2005-12-04
forum: Hardware &amp; Laptops
---

### Post by coaxx on 2005-12-04
Hi all,

For debugging reasons I am trying to disable usb at start time. But I have not managed to prevent usbcore from loading. Maybe anyone can help here...

what I tried allready:

- disable hotplug (chmod -x /etc/init.d/hotplug)
- disable all usb things in /etc/discover.conf
- bootoption "nousb" (no effect)
- bootoption "nopci" (no effect)

**-->still USB modules are loaded at boot time :(**

here is a bootlog and there You can see usb automatically loading each boot time:

```

Dec  4 14:20:39 localhost kernel: Inspecting /boot/System.map-2.6.12-9-386
Dec  4 14:20:39 localhost kernel: Loaded 29002 symbols from /boot/System.map-2.6.12-9-386.
Dec  4 14:20:39 localhost kernel: Symbols match kernel version 2.6.12.
Dec  4 14:20:39 localhost kernel: No module symbols loaded - kernel modules not enabled.
Dec  4 14:20:39 localhost kernel: sing pmtmr for high-res timesource
Dec  4 14:20:39 localhost kernel: [4294667.296000] Console: colour dummy device 80x25
Dec  4 14:20:39 localhost kernel: [4294669.231000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Dec  4 14:20:39 localhost kernel: [4294669.232000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Dec  4 14:20:39 localhost kernel: [4294669.246000] Memory: 511108k/524080k available (1415k kernel code, 12396k reserved, 763k data, 224k init, 0k highmem)
Dec  4 14:20:39 localhost kernel: [4294669.246000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Dec  4 14:20:39 localhost kernel: [4294669.268000] Security Framework v1.0.0 initialized
Dec  4 14:20:39 localhost kernel: [4294669.268000] SELinux:  Disabled at boot.
Dec  4 14:20:39 localhost kernel: [4294669.268000] Mount-cache hash table entries: 512
Dec  4 14:20:39 localhost kernel: [4294669.268000] CPU: Trace cache: 12K uops, L1 D cache: 8K
Dec  4 14:20:39 localhost kernel: [4294669.268000] CPU: L2 cache: 512K
Dec  4 14:20:39 localhost kernel: [4294669.268000] CPU: Intel Mobile Intel(R) Pentium(R) 4 - M CPU 2.00GHz stepping 07
Dec  4 14:20:39 localhost kernel: [4294669.268000] Enabling fast FPU save and restore... done.
Dec  4 14:20:39 localhost kernel: [4294669.268000] Enabling unmasked SIMD FPU exception support... done.
Dec  4 14:20:39 localhost kernel: [4294669.268000] Checking 'hlt' instruction... OK.
Dec  4 14:20:39 localhost kernel: [4294669.272000] Checking for popad bug... OK.
Dec  4 14:20:39 localhost kernel: [4294669.272000] checking if image is initramfs... it is
Dec  4 14:20:39 localhost kernel: [4294669.789000] Freeing initrd memory: 4824k freed
Dec  4 14:20:39 localhost kernel: [4294669.789000] ACPI: Looking for DSDT in initrd... not found!
Dec  4 14:20:39 localhost kernel: [4294669.845000]  not found!
Dec  4 14:20:39 localhost kernel: [4294669.856000] ACPI: setting ELCR to 0200 (from 0ae0)
Dec  4 14:20:39 localhost kernel: [4294669.857000] NET: Registered protocol family 16
Dec  4 14:20:39 localhost kernel: [4294669.857000] EISA bus registered
Dec  4 14:20:39 localhost kernel: [4294669.857000] ACPI: bus type pci registered
Dec  4 14:20:39 localhost kernel: [4294669.857000] PCI: PCI BIOS revision 2.10 entry at 0xfcebc, last bus=4
Dec  4 14:20:39 localhost kernel: [4294669.857000] PCI: Using configuration type 1
Dec  4 14:20:39 localhost kernel: [4294669.857000] mtrr: v2.0 (20020519)
Dec  4 14:20:39 localhost kernel: [4294669.858000] ACPI: Subsystem revision 20050729
Dec  4 14:20:39 localhost kernel: [4294669.862000] ACPI: Interpreter enabled
Dec  4 14:20:39 localhost kernel: [4294669.862000] ACPI: Using PIC for interrupt routing
Dec  4 14:20:39 localhost kernel: [4294669.862000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Dec  4 14:20:39 localhost kernel: [4294669.863000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Dec  4 14:20:39 localhost kernel: [4294669.863000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 *11 12)
Dec  4 14:20:39 localhost kernel: [4294669.864000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *6 7 10 11 12)
Dec  4 14:20:39 localhost kernel: [4294669.864000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *5
Dec  4 14:20:39 localhost kernel: [4294669.865000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Dec  4 14:20:39 localhost kernel: [4294669.865000] ACPI: PCI Interrupt Link [LNKG] (IRQs *5)
Dec  4 14:20:39 localhost kernel: [4294669.865000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Dec  4 14:20:39 localhost kernel: [4294669.866000] ACPI: PCI Root Bridge [PCI0] (0000:00)
Dec  4 14:20:39 localhost kernel: [4294669.866000] PCI: Probing PCI hardware (bus 00)
Dec  4 14:20:39 localhost kernel: [4294669.866000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
Dec  4 14:20:39 localhost kernel: [4294669.866000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
Dec  4 14:20:39 localhost kernel: [4294669.868000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
Dec  4 14:20:39 localhost kernel: [4294669.868000] PCI: Transparent bridge - 0000:00:1e.0
Dec  4 14:20:39 localhost kernel: [4294669.874000] ACPI: Power Resource [PFN0] (off)
Dec  4 14:20:39 localhost kernel: [4294669.874000] ACPI: Power Resource [PFN1] (off)
Dec  4 14:20:39 localhost kernel: [4294669.874000] Linux Plug and Play Support v0.97 (c) Adam Belay
Dec  4 14:20:39 localhost kernel: [4294669.874000] pnp: PnP ACPI init
Dec  4 14:20:39 localhost kernel: [4294669.876000] pnp: PnP ACPI: found 12 devices
Dec  4 14:20:39 localhost kernel: [4294669.876000] PnPBIOS: Disabled by ACPI PNP
Dec  4 14:20:39 localhost kernel: [4294669.876000] PCI: Using ACPI for IRQ routing
Dec  4 14:20:39 localhost kernel: [4294669.876000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Dec  4 14:20:39 localhost kernel: [4294669.883000] Simple Boot Flag at 0x7c set to 0x1
Dec  4 14:20:39 localhost kernel: [4294669.883000] audit: initializing netlink socket (disabled)
Dec  4 14:20:39 localhost kernel: [4294669.883000] audit: initialized
Dec  4 14:20:39 localhost kernel: [4294669.883000] VFS: Disk quotas dquot_6.5.1
Dec  4 14:20:39 localhost kernel: [4294669.883000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Dec  4 14:20:39 localhost kernel: [4294669.883000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
Dec  4 14:20:39 localhost kernel: [4294669.883000] devfs: boot_options: 0x0
Dec  4 14:20:39 localhost kernel: [4294669.883000] Initializing Cryptographic API
Dec  4 14:20:39 localhost kernel: [4294669.883000] isapnp: Scanning for PnP cards...
Dec  4 14:20:39 localhost kernel: [4294670.237000] isapnp: No Plug & Play device found
Dec  4 14:20:39 localhost kernel: [4294670.258000] PNP: PS/2 controller doesn't have AUX irq; using default 0xc
Dec  4 14:20:39 localhost kernel: [4294670.258000] PNP: PS/2 Controller [PNP0303:KBC] at 0x60,0x64 irq 112
Dec  4 14:20:39 localhost kernel: [4294670.262000] serio: i8042 AUX port at 0x60,0x64 irq 12
Dec  4 14:20:39 localhost kernel: [4294670.263000] serio: i8042 KBD port at 0x60,0x64 irq 1
Dec  4 14:20:39 localhost kernel: [4294670.263000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
Dec  4 14:20:39 localhost kernel: [4294670.265000] PCI: Enabling device 0000:00:1f.6 (0000 -> 0001)
Dec  4 14:20:39 localhost kernel: [4294670.266000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
Dec  4 14:20:39 localhost kernel: [4294670.266000] PCI: setting IRQ 11 as level-triggered
Dec  4 14:20:39 localhost kernel: [4294670.266000] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
Dec  4 14:20:39 localhost kernel: [4294670.266000] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
Dec  4 14:20:39 localhost kernel: [4294670.266000] io scheduler noop registered
Dec  4 14:20:39 localhost kernel: [4294670.266000] io scheduler anticipatory registered
Dec  4 14:20:39 localhost kernel: [4294670.266000] io scheduler deadline registered
Dec  4 14:20:39 localhost kernel: [4294670.266000] io scheduler cfq registered
Dec  4 14:20:39 localhost kernel: [4294670.266000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Dec  4 14:20:39 localhost kernel: [4294670.267000] EISA: Probing bus 0 at eisa.0
Dec  4 14:20:39 localhost kernel: [4294670.267000] Cannot allocate resource for EISA slot 1
Dec  4 14:20:39 localhost kernel: [4294670.267000] EISA: Detected 0 cards.
Dec  4 14:20:39 localhost kernel: [4294670.267000] NET: Registered protocol family 2
Dec  4 14:20:39 localhost kernel: [4294670.277000] IP: routing cache hash table of 4096 buckets, 32Kbytes
Dec  4 14:20:39 localhost kernel: [4294670.277000] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
Dec  4 14:20:39 localhost kernel: [4294670.277000] TCP bind hash table entries: 32768 (order: 5, 131072 bytes)
Dec  4 14:20:39 localhost kernel: [4294670.277000] TCP: Hash tables configured (established 32768 bind 32768)
Dec  4 14:20:39 localhost kernel: [4294670.277000] NET: Registered protocol family 8
Dec  4 14:20:39 localhost kernel: [4294670.277000] NET: Registered protocol family 20
Dec  4 14:20:39 localhost kernel: [4294670.277000] ACPI wakeup devices:
Dec  4 14:20:39 localhost kernel: [4294670.277000]  LAN CBC0 USB2 USB3 USB4 AMDM  LID
Dec  4 14:20:39 localhost kernel: [4294670.278000] ACPI: (supports S0 S3 S4 S5)
Dec  4 14:20:39 localhost kernel: [4294670.278000] Freeing unused kernel memory: 224k freed
Dec  4 14:20:39 localhost kernel: [4294670.318000] input: AT Translated Set 2 keyboard on isa0060/serio0
Dec  4 14:20:39 localhost kernel: [4294670.324000] Capability LSM initialized
Dec  4 14:20:39 localhost kernel: [4294670.330000] vesafb: framebuffer at 0xd8000000, mapped to 0xe0880000, using 10240k, total 65536k
Dec  4 14:20:39 localhost kernel: [4294670.330000] vesafb: mode is 1280x1024x32, linelength=5120, pages=10
Dec  4 14:20:39 localhost kernel: [4294670.330000] vesafb: protected mode interface info at c000:f410
Dec  4 14:20:39 localhost kernel: [4294670.330000] vesafb: scrolling: redraw
Dec  4 14:20:39 localhost kernel: [4294670.330000] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
Dec  4 14:20:39 localhost kernel: [4294670.330000] fb0: VESA VGA frame buffer device
Dec  4 14:20:39 localhost kernel: [4294670.368000] Console: switching to colour frame buffer device 160x64
Dec  4 14:20:39 localhost kernel: [4294670.373000] NET: Registered protocol family 1
Dec  4 14:20:39 localhost kernel: [4294670.389000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Dec  4 14:20:39 localhost kernel: [4294670.389000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Dec  4 14:20:39 localhost kernel: [4294670.389000] ACPI: bus type ide registered
Dec  4 14:20:39 localhost kernel: [4294670.399000] ICH3M: IDE controller at PCI slot 0000:00:1f.1
Dec  4 14:20:39 localhost kernel: [4294670.400000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
Dec  4 14:20:39 localhost kernel: [4294670.400000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Dec  4 14:20:39 localhost kernel: [4294670.401000] ICH3M: chipset revision 2
Dec  4 14:20:39 localhost kernel: [4294670.401000] ICH3M: not 100%% native mode: will probe irqs later
Dec  4 14:20:39 localhost kernel: [4294670.401000]     ide0: BM-DMA at 0xcfa0-0xcfa7, BIOS settings: hda:DMA, hdb:DMA
Dec  4 14:20:39 localhost kernel: [4294670.401000]     ide1: BM-DMA at 0xcfa8-0xcfaf, BIOS settings: hdc:pio, hdd:pio
Dec  4 14:20:39 localhost kernel: [4294670.665000] hda: HITACHI_DK23EA-60, ATA DISK drive
Dec  4 14:20:39 localhost kernel: [4294671.073000] hdb: TOSHIBA DVD-ROM SD-R6012, ATAPI CD/DVD-ROM drive
Dec  4 14:20:39 localhost kernel: [4294671.124000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Dec  4 14:20:39 localhost kernel: [4294674.220000] hda: max request size: 128KiB
Dec  4 14:20:39 localhost kernel: [4294674.222000] hda: 117210240 sectors (60011 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
Dec  4 14:20:39 localhost kernel: [4294674.222000] hda: cache flushes supported
Dec  4 14:20:39 localhost kernel: [4294674.222000]  /dev/ide/host0/bus0/target0/lun0: p1 p3 < p5 p6 p7 >
Dec  4 14:20:39 localhost kernel: [4294674.320000] hdb: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
Dec  4 14:20:39 localhost kernel: [4294674.320000] Uniform CD-ROM driver Revision: 3.20
Dec  4 14:20:39 localhost kernel: [4294674.682000] Attempting manual resume
Dec  4 14:20:39 localhost kernel: [4294674.702000] swsusp: Suspend partition has wrong signature?
Dec  4 14:20:39 localhost kernel: [4294674.730000] usbcore: registered new driver usbfs
Dec  4 14:20:39 localhost kernel: [4294674.730000] usbcore: registered new driver hub
Dec  4 14:20:39 localhost kernel: [4294674.732000] USB Universal Host Controller Interface driver v2.2
Dec  4 14:20:39 localhost kernel: [4294674.732000] PCI: Enabling device 0000:00:1d.0 (0000 -> 0001)
Dec  4 14:20:39 localhost kernel: [4294674.732000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
Dec  4 14:20:39 localhost kernel: [4294674.733000] PCI: setting IRQ 10 as level-triggered
Dec  4 14:20:39 localhost kernel: [4294674.733000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
Dec  4 14:20:39 localhost kernel: [4294674.733000] uhci_hcd 0000:00:1d.0: Intel Corporation 82801CA/CAM USB (Hub #1)
Dec  4 14:20:39 localhost kernel: [4294674.796000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Dec  4 14:20:39 localhost kernel: [4294674.796000] uhci_hcd 0000:00:1d.0: irq 10, io base 0x00001000
Dec  4 14:20:39 localhost kernel: [4294674.796000] hub 1-0:1.0: USB hub found
Dec  4 14:20:39 localhost kernel: [4294674.797000] hub 1-0:1.0: 2 ports detected
Dec  4 14:20:39 localhost kernel: [4294674.861000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 6
Dec  4 14:20:39 localhost kernel: [4294674.861000] PCI: setting IRQ 6 as level-triggered
Dec  4 14:20:39 localhost kernel: [4294674.861000] ACPI: PCI Interrupt 0000:02:06.0[A] -> Link [LNKD] -> GSI 6 (level, low) -> IRQ 6
Dec  4 14:20:39 localhost kernel: [4294674.862000] ohci_hcd 0000:02:06.0: NEC Corporation USB
Dec  4 14:20:39 localhost kernel: [4294674.873000] ohci_hcd 0000:02:06.0: new USB bus registered, assigned bus number 2
Dec  4 14:20:39 localhost kernel: [4294674.884000] ohci_hcd 0000:02:06.0: irq 6, io mem 0xfceff000
Dec  4 14:20:39 localhost kernel: [4294674.948000] hub 2-0:1.0: USB hub found
Dec  4 14:20:39 localhost kernel: [4294674.959000] hub 2-0:1.0: 3 ports detected
Dec  4 14:20:39 localhost kernel: [4294674.973000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 10
Dec  4 14:20:39 localhost kernel: [4294674.984000] ACPI: PCI Interrupt 0000:02:06.1[B] -> Link [LNKE] -> GSI 10 (level, low) -> IRQ 10
Dec  4 14:20:39 localhost kernel: [4294674.995000] ohci_hcd 0000:02:06.1: NEC Corporation USB (#2)
Dec  4 14:20:39 localhost kernel: [4294675.017000] ohci_hcd 0000:02:06.1: new USB bus registered, assigned bus number 3
Dec  4 14:20:39 localhost kernel: [4294675.028000] ohci_hcd 0000:02:06.1: irq 10, io mem 0xfcefe000
Dec  4 14:20:39 localhost kernel: [4294675.092000] hub 3-0:1.0: USB hub found
Dec  4 14:20:39 localhost kernel: [4294675.103000] hub 3-0:1.0: 2 ports detected
Dec  4 14:20:39 localhost kernel: [4294675.135000] PCI: Enabling device 0000:02:06.2 (0000 -> 0002)
Dec  4 14:20:39 localhost kernel: [4294675.147000] ACPI: PCI Interrupt 0000:02:06.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Dec  4 14:20:39 localhost kernel: [4294675.158000] ehci_hcd 0000:02:06.2: NEC Corporation USB 2.0
Dec  4 14:20:39 localhost kernel: [4294675.191000] ehci_hcd 0000:02:06.2: new USB bus registered, assigned bus number 4
Dec  4 14:20:39 localhost kernel: [4294675.202000] ehci_hcd 0000:02:06.2: irq 11, io mem 0x20000400
Dec  4 14:20:39 localhost kernel: [4294675.214000] ehci_hcd 0000:02:06.2: USB 2.0 initialized, EHCI 0.95, driver 10 Dec 2004
Dec  4 14:20:39 localhost kernel: [4294675.225000] usb 2-1: new full speed USB device using ohci_hcd and address 2
Dec  4 14:20:39 localhost kernel: [4294675.237000] hub 4-0:1.0: USB hub found
Dec  4 14:20:39 localhost kernel: [4294675.248000] hub 4-0:1.0: 5 ports detected
Dec  4 14:20:39 localhost kernel: [4294675.300000] e100: Intel(R) PRO/100 Network Driver, 3.4.8-k2-NAPI
Dec  4 14:20:39 localhost kernel: [4294675.311000] e100: Copyright(c) 1999-2005 Intel Corporation
Dec  4 14:20:39 localhost kernel: [4294675.323000] ACPI: PCI Interrupt 0000:02:08.0[A] -> Link [LNKE] -> GSI 10 (level, low) -> IRQ 10
Dec  4 14:20:39 localhost kernel: [4294675.358000] e100: eth0: e100_probe: addr 0xfcefd000, irq 10, MAC addr 00:08:0D:3A:F5:14
Dec  4 14:20:39 localhost kernel: [4294675.810000] usb 4-1: new high speed USB device using ehci_hcd and address 2
Dec  4 14:20:39 localhost kernel: [4294675.898000] hub 4-1:1.0: USB hub found
Dec  4 14:20:39 localhost kernel: [4294675.910000] hub 4-1:1.0: 4 ports detected
Dec  4 14:20:39 localhost kernel: [4294676.473000] usb 4-1.3: new high speed USB device using ehci_hcd and address 5
Dec  4 14:20:39 localhost kernel: [4294676.710000] usb 2-2: new low speed USB device using ohci_hcd and address 3
Dec  4 14:20:39 localhost kernel: [4294677.007000] usb 2-3: new full speed USB device using ohci_hcd and address 4
Dec  4 14:20:39 localhost kernel: [4294677.418000] usbcore: registered new driver hiddev
Dec  4 14:20:39 localhost kernel: [4294677.438000] input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:02:06.0-2
Dec  4 14:20:39 localhost kernel: [4294677.462000] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:02:06.0-2
Dec  4 14:20:39 localhost kernel: [4294677.474000] usbhid: probe of 2-3:1.0 failed with error -5
Dec  4 14:20:39 localhost kernel: [4294677.485000] usbcore: registered new driver usbhid
Dec  4 14:20:39 localhost kernel: [4294677.497000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
Dec  4 14:20:39 localhost kernel: [4294677.556000] SCSI subsystem initialized
Dec  4 14:20:39 localhost kernel: [4294677.569000] Initializing USB Mass Storage driver...
Dec  4 14:20:39 localhost kernel: [4294677.581000] scsi0 : SCSI emulation for USB Mass Storage devices
Dec  4 14:20:39 localhost kernel: [4294677.593000] usbcore: registered new driver usb-storage
Dec  4 14:20:39 localhost kernel: [4294677.604000] USB Mass Storage support registered.

.
.
.


```

---

### Post by gsjarvis on 2007-02-15
Hello All,

I'm new here and new to ubuntu too.
I hope someone will publish some kind of answer to this question because I'm trying to install ubuntu server (ubuntu-6.06.1-server-i386) onto an old PIII machine in Morocco.
Of course this machine doesn't have any usb ports so when it boots it says:
[INDENT]***uhci_hcd Found HC with no IRQ check BIOS/PCI 000: Setup!***[/INDENT]
and whenever I press numlock or the numeric pad numbers or scroll lock it crashes the machine :confused: 

I found this link via google:
[INDENT][http://support.cristie.com/cgi-bin/kb.cgi?do=read&id=86&lang=en](http://support.cristie.com/cgi-bin/kb.cgi?do=read&id=86&lang=en)[/INDENT]
that says the usb devices should be disabled in the kernel if there are non in the machine.

Any suggetions - I can't get another machine ;-) 

GsJ

---

### Post by Gabbegubben on 2008-02-11
OK, very late reply but maybe it will be of help to someone.

This will disable all USB modules and prevent them from loading:

sudo sh -c 'echo blacklist ehci_hcd > /etc/modprobe.d/blacklist-ehci'
sudo sh -c 'echo blacklist uhci_hcd > /etc/modprobe.d/blacklist-uhci'
sudo sh -c 'echo blacklist ohci_hcd > /etc/modprobe.d/blacklist-ohci'
sudo update-initramfs -u
or
sudo update-initramfs -u -k `uname -r`
if you want to update the kernel you are running - and it is not the latest available.

I had to do this to get around [bug #155278]("https://bugs.launchpad.net/linux/+bug/155278") on an old IBM Aptiva.

---

