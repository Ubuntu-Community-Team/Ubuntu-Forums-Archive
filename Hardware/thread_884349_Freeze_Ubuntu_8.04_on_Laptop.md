---
title: "Freeze Ubuntu 8.04 on Laptop"
date: 2008-08-08
forum: Hardware
---

### Post by chanfle on 2008-08-08
Hello all,
some times it's freeze my laptop Acer 5150 with ubuntu 8.04 hardy...example if I use firefox, the browser take gray color and i need to restart tha unit or quit force the firefox....
anybody know if exist any trick...or any update???
thanks
I waiting your response...

---

### Post by vandorjw on 2008-08-08
sudo apt-get remove firefox
sudo apt-get install opera

sudo apt-get autoremove

This will remove firefox, and install Opera Web Browser, and clean up some files no longer needed.

PS: to check for an update, 
sudo apt-get update

To install updates, (after checking for and update)
sudo apt-get upgrade

-----------------------
I do not know how new you are to Ubuntu, so if you do not know what I mean with sudo....etc please post "I don't understand", and I will explain in more detail.

---

### Post by chanfle on 2008-08-08
thanks for response...but when I mention Firefox it was example, it's happend with others applications....

---

### Post by chanfle on 2008-08-09
any update/comments..???

---

### Post by ultimatsz on 2008-08-09
check your error mesage log. or type dmesg at the terminal after it hangs. it should show some forms of errors. my guess is something which goes on the line ata1: soft resetting port and eh complete.

---

### Post by Random Bob on 2008-09-04
[   10.989696] Booting paravirtualized kernel on bare hardware
[   10.990147] Time: 16:32:49  Date: 09/04/08
[   10.990170] NET: Registered protocol family 16
[   10.990353] EISA bus registered
[   10.990378] ACPI: bus type pci registered
[   11.008042] PCI: PCI BIOS revision 2.10 entry at 0xfd70e, last bus=7
[   11.008044] PCI: Using configuration type 1
[   11.008051] Setting up standard PCI resources
[   11.015699] ACPI: EC: Look up EC in DSDT
[   11.017119] ACPI: Interpreter enabled
[   11.017121] ACPI: (supports S0 S3 S4 S5)
[   11.017134] ACPI: Using IOAPIC for interrupt routing
[   11.045528] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[   11.045530] ACPI: EC: driver started in poll mode
[   11.045567] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   11.046222] Force enabled HPET at base address 0xfed00000
[   11.046228] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   11.046232] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   11.046737] PCI: Transparent bridge - 0000:00:1e.0
[   11.046813] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   11.047140] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   11.051735] ACPI: PCI Interrupt Link [LNKA] (IRQs *10 11)
[   11.051819] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 *11)
[   11.051901] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 *11)
[   11.051983] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 *11)
[   11.052064] ACPI: PCI Interrupt Link [LNKE] (IRQs *10 11)
[   11.052146] ACPI: PCI Interrupt Link [LNKF] (IRQs *10 11)
[   11.052227] ACPI: PCI Interrupt Link [LNKG] (IRQs *10 11)
[   11.052308] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 *11)
[   11.052420] Linux Plug and Play Support v0.97 (c) Adam Belay
[   11.052451] pnp: PnP ACPI init
[   11.052457] ACPI: bus type pnp registered
[   11.062880] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   11.063423] pnp: PnP ACPI: found 8 devices
[   11.063425] ACPI: ACPI bus type pnp unregistered
[   11.063429] PnPBIOS: Disabled by ACPI PNP
[   11.063624] PCI: Using ACPI for IRQ routing
[   11.063626] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   11.093435] NET: Registered protocol family 8
[   11.093437] NET: Registered protocol family 20
[   11.093592] hpet clockevent registered
[   11.093598] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   11.093602] hpet0: 3 64-bit timers, 14318180 Hz
[   11.094637] AppArmor: AppArmor Filesystem Enabled
[   11.097427] Time: tsc clocksource has been installed.
[   11.105460] system 00:04: ioport range 0x800-0x80f has been reserved
[   11.105463] system 00:04: ioport range 0x1000-0x107f has been reserved
[   11.105466] system 00:04: ioport range 0x1180-0x11bf has been reserved
[   11.105469] system 00:04: ioport range 0x1200-0x1200 has been reserved
[   11.105471] system 00:04: ioport range 0x1204-0x1204 has been reserved
[   11.105475] system 00:04: iomem range 0xe0000000-0xefffffff could not be reserved
[   11.105478] system 00:04: iomem range 0xf0000000-0xf0003fff could not be reserved
[   11.105481] system 00:04: iomem range 0xf0004000-0xf0004fff could not be reserved
[   11.105484] system 00:04: iomem range 0xf0005000-0xf0005fff could not be reserved
[   11.105487] system 00:04: iomem range 0xf0008000-0xf000bfff could not be reserved
[   11.105490] system 00:04: iomem range 0xfec18000-0xfec180ff has been reserved
[   11.105493] system 00:04: iomem range 0xfed20000-0xfed8ffff could not be reserved
[   11.135875] PCI: Bridge: 0000:00:1c.0
[   11.135878]   IO window: 2000-2fff
[   11.135884]   MEM window: b4000000-b7ffffff
[   11.135889]   PREFETCH window: d0000000-d3ffffff
[   11.135897] PCI: Bus 7, cardbus bridge: 0000:06:09.0
[   11.135899]   IO window: 00003400-000034ff
[   11.135904]   IO window: 00003800-000038ff
[   11.135910]   PREFETCH window: 8c000000-8fffffff
[   11.135915]   MEM window: 90000000-93ffffff
[   11.135920] PCI: Bridge: 0000:00:1e.0
[   11.135923]   IO window: 3000-3fff
[   11.135928]   MEM window: b8000000-b80fffff
[   11.135933]   PREFETCH window: disabled.
[   11.135959] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
[   11.135965] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   11.135978] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   11.135994] ACPI: PCI Interrupt 0000:06:09.0[A] -> GSI 22 (level, low) -> IRQ 17
[   11.136007] NET: Registered protocol family 2
[   11.173466] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   11.173692] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   11.174457] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   11.174890] TCP: Hash tables configured (established 131072 bind 65536)
[   11.174893] TCP reno registered
[   11.185554] checking if image is initramfs... it is
[   11.597304] Switched to high resolution mode on CPU 0
[   11.874005] Freeing initrd memory: 7283k freed
[   11.874217] Simple Boot Flag at 0x37 set to 0x1
[   11.874619] audit: initializing netlink socket (disabled)
[   11.874636] audit(1220545969.388:1): initialized
[   11.874852] highmem bounce pool size: 64 pages
[   11.876710] VFS: Disk quotas dquot_6.5.1
[   11.876786] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   11.876928] io scheduler noop registered
[   11.876930] io scheduler anticipatory registered
[   11.876932] io scheduler deadline registered
[   11.876943] io scheduler cfq registered (default)
[   11.876955] Boot video device is 0000:00:02.0
[   11.877141] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   11.877211] assign_interrupt_mode Found MSI capability
[   11.877256] Allocate Port Service[0000:00:1c.0:pcie00]
[   11.877294] Allocate Port Service[0000:00:1c.0:pcie02]
[   11.877543] isapnp: Scanning for PnP cards...
[   12.231636] isapnp: No Plug & Play device found
[   12.257696] Real Time Clock Driver v1.12ac
[   12.257802] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   12.258935] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   12.259006] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   12.259097] PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   12.259408] i8042.c: Detected active multiplexing controller, rev 1.1.
[   12.259475] serio: i8042 KBD port at 0x60,0x64 irq 1
[   12.259479] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   12.259481] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   12.259484] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   12.259486] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   12.261287] mice: PS/2 mouse device common for all mice
[   12.261394] EISA: Probing bus 0 at eisa.0
[   12.261402] Cannot allocate resource for EISA slot 1
[   12.261404] Cannot allocate resource for EISA slot 2
[   12.261407] Cannot allocate resource for EISA slot 3
[   12.261427] EISA: Detected 0 cards.
[   12.261430] cpuidle: using governor ladder
[   12.261432] cpuidle: using governor menu
[   12.261523] NET: Registered protocol family 1
[   12.261548] Using IPI No-Shortcut mode
[   12.261580] registered taskstats version 1
[   12.261678]   Magic number: 8:492:539
[   12.261775] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   12.261777] EDD information not available.
[   12.261976] Freeing unused kernel memory: 368k freed
[   12.264222] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   13.463178] fuse init (API version 7.9)
[   13.486107] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   13.486112] ACPI: Processor [CPU0] (supports 8 throttling states)
[   13.486125] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   13.491905] ACPI: Thermal Zone [TZS0] (53 C)
[   13.493786] ACPI: Thermal Zone [TZS1] (53 C)
[   14.069100] usbcore: registered new interface driver usbfs
[   14.069124] usbcore: registered new interface driver hub
[   14.084477] usbcore: registered new device driver usb
[   14.088940] USB Universal Host Controller Interface driver v3.0
[   14.089054] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 18
[   14.089065] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   14.089070] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   14.089394] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   14.089426] uhci_hcd 0000:00:1d.0: irq 18, io base 0x00001820
[   14.089555] usb usb1: configuration #1 chosen from 1 choice
[   14.089579] hub 1-0:1.0: USB hub found
[   14.089584] hub 1-0:1.0: 2 ports detected
[   14.180631] SCSI subsystem initialized
[   14.192525] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 16
[   14.192538] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   14.192543] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   14.192566] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   14.192597] uhci_hcd 0000:00:1d.1: irq 16, io base 0x00001840
[   14.192706] usb usb2: configuration #1 chosen from 1 choice
[   14.192729] hub 2-0:1.0: USB hub found
[   14.192734] hub 2-0:1.0: 2 ports detected
[   14.244768] libata version 3.00 loaded.
[   14.254780] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   14.296480] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
[   14.296492] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   14.296497] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   14.296523] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   14.296553] uhci_hcd 0000:00:1d.2: irq 19, io base 0x00001860
[   14.296663] usb usb3: configuration #1 chosen from 1 choice
[   14.296687] hub 3-0:1.0: USB hub found
[   14.296692] hub 3-0:1.0: 2 ports detected
[   14.400446] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 20
[   14.400459] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   14.400464] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   14.400488] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   14.400520] uhci_hcd 0000:00:1d.3: irq 20, io base 0x00001880
[   14.400626] usb usb4: configuration #1 chosen from 1 choice
[   14.400649] hub 4-0:1.0: USB hub found
[   14.400655] hub 4-0:1.0: 2 ports detected
[   14.504522] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 18
[   14.504537] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   14.504541] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   14.504563] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   14.508466] ehci_hcd 0000:00:1d.7: debug port 1
[   14.508472] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   14.508479] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xb0004000
[   14.524304] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   14.524423] usb usb5: configuration #1 chosen from 1 choice
[   14.524447] hub 5-0:1.0: USB hub found
[   14.524452] hub 5-0:1.0: 8 ports detected
[   14.628421] 8139cp 0000:06:07.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   14.628427] 8139cp 0000:06:07.0: Try the "8139too" driver instead.
[   14.631935] 8139too Fast Ethernet driver 0.9.28
[   14.631989] ACPI: PCI Interrupt 0000:06:07.0[A] -> GSI 20 (level, low) -> IRQ 21
[   14.632849] eth0: RealTek RTL8139 at 0x3000, 00:0a:e4:fc:14:cf, IRQ 21
[   14.632852] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   14.636935] ahci 0000:00:1f.2: version 3.0
[   14.636957] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 16
[   14.636966] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[   14.636971] ahci: probe of 0000:00:1f.2 failed with error -22
[   14.640122] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 16
[   14.640155] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   14.640167] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[   14.643842] ata_piix 0000:00:1f.2: version 2.12
[   14.643848] ata_piix 0000:00:1f.2: MAP [ IDE IDE P1 P3 ]
[   14.643863] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 16
[   14.643887] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   14.644395] scsi0 : ata_piix
[   14.644858] scsi1 : ata_piix
[   14.645707] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[   14.645710] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[   14.972725] ata1.00: ATA-7: HTS421212H9AT00, HA4OA70G, max UDMA/100
[   14.972729] ata1.00: 234441648 sectors, multi 16: LBA48 
[   14.972754] ata1.01: ATAPI: TSSTcorpCD/DVDW TS-L632D, ac00, max UDMA/33
[   14.988652] ata1.00: configured for UDMA/100
[   15.092120] Clocksource tsc unstable (delta = -1648683520 ns)
[   15.092130] usb 4-1: new low speed USB device using uhci_hcd and address 2
[   15.096117] Time: hpet clocksource has been installed.
[   15.110131] ata1.01: configured for UDMA/33
[   15.129182] usb 4-1: configuration #1 chosen from 1 choice
[   15.145367] usbcore: registered new interface driver hiddev
[   15.151444] input: Logitech USB RECEIVER as /devices/pci0000:00/0000:00:1d.3/usb4/4-1/4-1:1.0/input/input2
[   15.153248] input,hidraw0: USB HID v1.11 Mouse [Logitech USB RECEIVER] on usb-0000:00:1d.3-1
[   15.153260] usbcore: registered new interface driver usbhid
[   15.153263] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   15.178845] scsi 0:0:0:0: Direct-Access     ATA      HTS421212H9AT00  HA4O PQ: 0 ANSI: 5
[   15.180629] scsi 0:0:1:0: CD-ROM            TSSTcorp CD/DVDW TS-L632D ac00 PQ: 0 ANSI: 5
[   15.189229] Driver 'sd' needs updating - please use bus_type methods
[   15.189297] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   15.189309] sd 0:0:0:0: [sda] Write Protect is off
[   15.189312] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   15.189327] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   15.189371] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   15.189381] sd 0:0:0:0: [sda] Write Protect is off
[   15.189383] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   15.189398] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   15.189402]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   15.216130]  sda1 sda2 sda3 < sda5 sda6 sda7 > sda4
[   15.257071] sd 0:0:0:0: [sda] Attached SCSI disk
[   15.262441] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   15.262459] sr 0:0:1:0: Attached scsi generic sg1 type 5
[   15.289089] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   15.289094] Uniform CD-ROM driver Revision: 3.20
[   15.289140] sr 0:0:1:0: Attached scsi CD-ROM sr0
[   29.545269] ACPI: WMI-Acer: Mapper loaded
[   29.877506] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   29.937499] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   30.013433] iTCO_vendor_support: vendor-support=0
[   30.077407] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   30.077488] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x1060)
[   30.077521] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   30.154543] Linux agpgart interface v0.102
[   30.329383] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   30.417783] acer_acpi: Acer Laptop ACPI Extras version 0.11.1
[   30.417790] acer_acpi: Detected Acer AMW0 version 2 interface
[   30.429761] Registered led device: acer_acpi:mail
[   30.609202] intel_rng: FWH not detected
[   30.632077] agpgart: Detected an Intel 915GM Chipset.
[   30.632646] agpgart: Detected 7932K stolen memory.
[   30.650890] agpgart: AGP aperture is 256M @ 0xc0000000
[   30.693274] input: Power Button (FF) as /devices/virtual/input/input4
[   30.725171] ACPI: Power Button (FF) [PWRF]
[   30.725228] input: Lid Switch as /devices/virtual/input/input5
[   30.744224] ACPI: Lid Switch [LID0]
[   30.744278] input: Sleep Button (CM) as /devices/virtual/input/input6
[   30.769152] ACPI: Sleep Button (CM) [SLPB]
[   30.793931] ieee80211_crypt: registered algorithm 'NULL'
[   30.969122] Yenta: CardBus bridge found at 0000:06:09.0 [1025:0100]
[   30.969149] Yenta: Using CSCINT to route CSC interrupts to PCI
[   30.969151] Yenta: Routing CardBus interrupts to PCI
[   30.969157] Yenta TI: socket 0000:06:09.0, mfunc 0x00001022, devctl 0x44
[   31.201771] Yenta: ISA IRQ mask 0x0cf8, PCI irq 17
[   31.201776] Socket status: 30000006
[   31.201779] Yenta: Raising subordinate bus# of parent bus (#06) from #07 to #0a
[   31.201784] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   31.201787] cs: IO port probe 0x3000-0x3fff: clean.
[   31.202016] pcmcia: parent PCI bridge Memory window: 0xb8000000 - 0xb80fffff
[   31.381984] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   31.381989] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   31.668806] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   31.668810] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   31.668897] ACPI: PCI Interrupt 0000:06:05.0[A] -> GSI 21 (level, low) -> IRQ 22
[   31.716775] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   31.737064] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input7
[   31.764765] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   31.764997] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input8
[   31.792767] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   32.069026] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x12a0b1, caps: 0xa04713/0x204000
[   32.099313] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input9
[   32.720485] ACPI: AC Adapter [ADP1] (on-line)
[   32.838498] usbcore: registered new interface driver lmpcm_usb
[   32.838503] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/misc/lmpcm_usb.c: v0.5.5:USB Logitech MediaPlay Cordless Mouse driver
[   32.956968] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 23
[   32.956996] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   33.083838] ACPI: Battery Slot [BAT0] (battery present)
[   34.156991] cs: IO port probe 0x100-0x3af: clean.
[   34.158713] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   34.159434] cs: IO port probe 0x820-0x8ff: clean.
[   34.160045] cs: IO port probe 0xc00-0xcf7: clean.
[   34.160793] cs: IO port probe 0xa00-0xaff: clean.
[   34.175044] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   34.230196] udev: renamed network interface eth1 to eth0
[   34.269647] udev: renamed network interface eth0_rename to eth1
[   34.391750] loop: module loaded
[   34.485599] lp: driver loaded but no devices found
[   39.686541] kjournald starting.  Commit interval 5 seconds
[   39.686995] EXT3 FS on sda7, internal journal
[   39.686999] EXT3-fs: mounted filesystem with ordered data mode.
[   39.767869] ReiserFS: sda6: found reiserfs format "3.6" with standard journal
[   39.767877] ReiserFS: sda6: using ordered data mode
[   39.774623] ReiserFS: sda6: journal params: device sda6, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   39.774947] ReiserFS: sda6: checking transaction log (sda6)
[   39.814907] ReiserFS: sda6: Using r5 hash to sort names
[   40.442924] ip_tables: (C) 2000-2006 Netfilter Core Team
[   40.880870] No dock devices found.
[   42.162790] apm: BIOS not found.
[   42.318678] ppdev: user-space parallel port driver
[   42.547795] audit(1220560406.366:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5008 profile="/usr/sbin/cupsd" namespace="default"
[   92.479936] Marking TSC unstable due to: cpufreq changes.
[   95.423795] eth1: link down
[   95.764207] Bluetooth: Core ver 2.11
[   95.766639] NET: Registered protocol family 31
[   95.766646] Bluetooth: HCI device and connection manager initialized
[   95.766653] Bluetooth: HCI socket layer initialized
[   44.234368] Bluetooth: L2CAP ver 2.9
[   44.234372] Bluetooth: L2CAP socket layer initialized
[   44.277577] Bluetooth: RFCOMM socket layer initialized
[   44.277590] Bluetooth: RFCOMM TTY layer initialized
[   44.277592] Bluetooth: RFCOMM ver 1.8
[   46.601132] [drm] Initialized drm 1.1.0 20060810
[   46.604329] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 23
[   46.604336] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   46.604398] [drm] Initialized i915 1.6.0 20060119 on minor 0
[  120.917898] NET: Registered protocol family 10
[  120.918627] lo: Disabled Privacy Extensions
[  120.919598] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   62.067129] eth0: no IPv6 routers present
[  390.452068] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  390.452093] ata1.01: cmd a0/00:00:00:0c:00/00:00:00:00:00/b0 tag 0 pio 12 in
[  390.452096]          cdb 43 00 00 00 00 00 00 00  0c 00 00 00 00 00 00 00
[  390.452099]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[  390.452107] ata1.01: status: { DRDY }
[  392.314257] ata1: port is slow to respond, please be patient (Status 0xd0)
[  394.181750] ata1: device not ready (errno=-16), forcing hardreset
[  394.181760] ata1: soft resetting link
[  394.314328] ata1.00: configured for UDMA/100
[  394.388289] ata1.01: configured for UDMA/33
[  394.388309] ata1: EH complete
[  394.394367] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[  394.397317] sd 0:0:0:0: [sda] Write Protect is off
[  394.397324] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  394.407180] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  394.413149] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[  394.418898] sd 0:0:0:0: [sda] Write Protect is off
[  394.418905] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  409.854935] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  409.854960] ata1.01: cmd a0/00:00:00:0c:00/00:00:00:00:00/b0 tag 0 pio 12 in
[  409.854963]          cdb 43 00 00 00 00 00 00 00  0c 00 00 00 00 00 00 00
[  409.854966]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[  409.854974] ata1.01: status: { DRDY }
[  411.804954] ata1: port is slow to respond, please be patient (Status 0xd0)
[  413.633335] ata1: device not ready (errno=-16), forcing hardreset
[  413.633345] ata1: soft resetting link
[  413.764180] ata1.00: configured for UDMA/100
[  413.845045] ata1.01: configured for UDMA/33
[  413.845066] ata1: EH complete
[  413.845463] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  413.860026] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[  413.863313] sd 0:0:0:0: [sda] Write Protect is off
[  413.863321] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  413.871982] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  633.138201] NET: Registered protocol family 17
[  633.424440] ieee80211_crypt: registered algorithm 'WEP'
[  643.889196] eth0: no IPv6 routers present
[  652.986931] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  652.986954] ata1.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
[  652.986958]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[  652.986961]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[  652.986968] ata1.01: status: { DRDY }
[  654.777302] ata1: port is slow to respond, please be patient (Status 0xd0)
[  656.475484] ata1: device not ready (errno=-16), forcing hardreset
[  656.475495] ata1: soft resetting link
[  656.604763] ata1.00: configured for UDMA/100
[  656.666777] ata1.01: configured for UDMA/33
[  656.666794] ata1: EH complete
[  656.672696] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[  656.673336] sd 0:0:0:0: [sda] Write Protect is off
[  656.673344] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  656.684710] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  656.696659] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[  656.699673] sd 0:0:0:0: [sda] Write Protect is off
[  656.699680] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  656.705746] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  871.291899] ata1.01: qc timeout (cmd 0xa0)
[  871.291922] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  871.291941] ata1.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
[  871.291944]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[  871.291947]          res 51/20:03:00:00:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
[  871.291954] ata1.01: status: { DRDY ERR }
[  873.025995] ata1: port is slow to respond, please be patient (Status 0xd0)
[  874.758508] ata1: device not ready (errno=-16), forcing hardreset
[  874.758519] ata1: soft resetting link
[  874.882392] ata1.00: configured for UDMA/100
[  874.948327] ata1.01: configured for UDMA/33
[  874.948358] ata1: EH complete
[  874.955352] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[  874.956031] sd 0:0:0:0: [sda] Write Protect is off
[  874.956039] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  875.386372] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  875.394935] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[  875.398094] sd 0:0:0:0: [sda] Write Protect is off
[  875.398102] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  875.402379] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1247.469550] ata1.01: qc timeout (cmd 0xa0)
[ 1247.469572] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 1247.469591] ata1.01: cmd a0/00:00:00:08:00/00:00:00:00:00/b0 tag 0 pio 8 in
[ 1247.469595]          cdb 25 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 1247.469598]          res 51/20:03:00:00:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
[ 1247.469605] ata1.01: status: { DRDY ERR }
[ 1249.291743] ata1: port is slow to respond, please be patient (Status 0xd0)
[ 1251.002713] ata1: device not ready (errno=-16), forcing hardreset
[ 1251.002723] ata1: soft resetting link
[ 1251.130524] ata1.00: configured for UDMA/100
[ 1251.191996] ata1.01: configured for UDMA/33
[ 1251.192024] ata1: EH complete
[ 1251.198216] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[ 1251.203706] sd 0:0:0:0: [sda] Write Protect is off
[ 1251.203714] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1251.209509] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1251.648484] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[ 1251.654095] sd 0:0:0:0: [sda] Write Protect is off
[ 1251.654103] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1251.660154] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA


having the exact same problem
no idea what to do about it!
here's the dmesg output

As a future reference, where can I find the error log?

---

### Post by luckyuser on 2008-09-05
Hardy has been freezing on me too, and with similar symptons. Also the mouse and keyboard inputs cease to work so I am left to push&hold the power button.

---

### Post by mempman on 2008-09-08
> **chanfle said:**
> Hello all,
some times it's freeze my laptop Acer 5150 with ubuntu 8.04 hardy...example if I use firefox, the browser take gray color and i need to restart tha unit or quit force the firefox....
anybody know if exist any trick...or any update???
thanks
I waiting your response...

I have the same problem....I'm guessing that every time the freezing occurs you are running your laptop on battery power?

---

### Post by ewinslow on 2008-09-10
I'll add to the chorus. The system has practically become useless on battery power.

---

### Post by ewinslow on 2008-09-10
From some other threads I found the suggestion to back off to an older kernel. 
I booted with the  2.6.24-16 kernel and am not having the freezing issue.

In another thread the -17 kernel was also suggested.

---

### Post by alcatraz on 2008-10-04
I have the same problem. It seem to be a kernel problem. Because I bought a new harddrive and it did not work properly. It has always problems when I read more stuff from the harddrive...

But in the Beta 1 of Ubuntu 8.10 Intrepid Ibex, the problem is NOT there anymore. I tested to run 6 movies simulteanously and watch my high resoluted holiday pictures. It worked fine. I guess in the newest kernel, they finally fixed the problem :)

So... I would suggest to wait until the 30th October until the stable version of Ubuntu 8.10 will be released

---

