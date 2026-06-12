---
title: "Acer 5601 Freezing random"
date: 2008-02-10
forum: Hardware &amp; Laptops
---

### Post by gymmeh on 2008-02-10
I have a Acer Aspire 5601 AWLMi 
Intel Duo Core T2050 1.6Ghz
Intel GMA 950
512MB DDR2
Ubuntu 7.10


The computer functions well on ubuntu, the only problem is random freezing. The mouse and keyboard still work but nothing responds, and some programs turn gray. The problem is completely random. It will work fine for a week, then one day it will freeze 20 times.  

It is not necessarily heat related as it can happen minutes into booting.  Or It may never happen even when the computer is extremely hot. 

I have tried using "top" in terminal to see if anything different happened, nothing happens that catches my eye. 
 
I have also installed gkrellm which tracks performance. When the freezing is going to accrue. 
CPUO and CPU1 both levels off to a low value.
Proc, the blue "bars" level off but the yellow line will step up to the top and then the system will freeze.
Disk, The "bars" will level off at a low value or zero.

THank you for your help.

If you need any information, I am pretty new to this so please use basic terms. 

Long story....back ground... of this was that I have the problem when I got the computer, and acer insisted that the problem was a virus and that I needed to reformat. After doing this 3 or 4 times, I figured is must be something else, but by time I knew acer was completely wrong and there must be something else it was passed the software support.  Since any time I called them is was extremely difficult and timely to get anything useful done,  I tried switching to fedora...which was over my head... then switched to Ubuntu, just recently I got all of the little things worked out and realize the computer still has the same problem...

Moral of the sorry, dont trust acer tech support, and return a computer at the first sign of a problem if its still under warranty... Expensive and Crappy way to learn.

Thanks again for your help!

---

### Post by gymmeh on 2008-02-16
So its been 5 days with no replays....

my computer frooze while booting saying.

Fatal:Error Inserting snd_seq_dummy, see dmesg, 

 so this is what that said

 ```
[   15.658791] assign_interrupt_mode Found MSI capability
[   15.658793] Allocate Port Service[0000:00:1c.1:pcie00]
[   15.658826] Allocate Port Service[0000:00:1c.1:pcie02]
[   15.658931] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   15.658990] assign_interrupt_mode Found MSI capability
[   15.658993] Allocate Port Service[0000:00:1c.2:pcie00]
[   15.659029] Allocate Port Service[0000:00:1c.2:pcie02]
[   15.659132] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   15.659191] assign_interrupt_mode Found MSI capability
[   15.659194] Allocate Port Service[0000:00:1c.3:pcie00]
[   15.659226] Allocate Port Service[0000:00:1c.3:pcie02]
[   15.659396] isapnp: Scanning for PnP cards...
[   16.012947] isapnp: No Plug & Play device found
[   16.038820] Real Time Clock Driver v1.12ac
[   16.039071] hpet_resources: 0xfed00000 is busy
[   16.039107] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   16.040323] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   16.040459] input: Macintosh mouse button emulation as /class/input/input0
[   16.040542] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   16.043613] i8042.c: Detected active multiplexing controller, rev 1.1.
[   16.044609] serio: i8042 KBD port at 0x60,0x64 irq 1
[   16.044615] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   16.044619] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   16.044622] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   16.044625] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   16.044777] mice: PS/2 mouse device common for all mice
[   16.044915] EISA: Probing bus 0 at eisa.0
[   16.044923] Cannot allocate resource for EISA slot 1
[   16.044927] Cannot allocate resource for EISA slot 2
[   16.044954] EISA: Detected 0 cards.
[   16.045150] TCP cubic registered
[   16.045168] NET: Registered protocol family 1
[   16.045192] Using IPI No-Shortcut mode
[   16.045362]   Magic number: 12:148:239
[   16.045391]   hash matches device ttyv9
[   16.045402]   hash matches device ttysc
[   16.045512]   hash matches device thermal:00
[   16.045732] Freeing unused kernel memory: 364k freed
[   16.084035] input: AT Translated Set 2 keyboard as /class/input/input1
[   17.254528] AppArmor: AppArmor initialized<5>audit(1203182097.884:2):  type=1505 info="AppArmor initialized" pid=1232
[   17.262795] fuse init (API version 7.8)
[   17.268404] Failure registering capabilities with primary security module.
[   17.306359] ACPI: SSDT 1F693C78, 01EA (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[   17.306596] ACPI: SSDT 1F693A23, 01D0 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[   17.306892] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   17.306897] ACPI: Processor [CPU0] (supports 8 throttling states)
[   17.307149] ACPI: SSDT 1F693E62, 0089 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[   17.307364] ACPI: SSDT 1F693BF3, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[   17.307691] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   17.307696] ACPI: Processor [CPU1] (supports 8 throttling states)
[   17.311494] ACPI: Thermal Zone [THRM] (54 C)
[    3.356000] Marking TSC unstable due to: possible TSC halt in C2.
[    3.360000] Time: hpet clocksource has been installed.
[    3.828000] usbcore: registered new interface driver usbfs
[    3.828000] usbcore: registered new interface driver hub
[    3.828000] usbcore: registered new device driver usb
[    3.828000] USB Universal Host Controller Interface driver v3.0
[    3.828000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 21
[    3.828000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    3.828000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.828000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.828000] uhci_hcd 0000:00:1d.0: irq 21, io base 0x00001820
[    3.828000] usb usb1: configuration #1 chosen from 1 choice
[    3.828000] hub 1-0:1.0: USB hub found
[    3.828000] hub 1-0:1.0: 2 ports detected
[    3.836000] SCSI subsystem initialized
[    3.860000] libata version 2.21 loaded.
[    3.884000] 8139too Fast Ethernet driver 0.9.28
[    3.932000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[    3.932000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.932000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.932000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.932000] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[    3.932000] usb usb2: configuration #1 chosen from 1 choice
[    3.932000] hub 2-0:1.0: USB hub found
[    3.932000] hub 2-0:1.0: 2 ports detected
[    4.000000] Clocksource tsc unstable (delta = -68591776 ns)
[    4.036000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[    4.036000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    4.036000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    4.036000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    4.036000] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    4.036000] usb usb3: configuration #1 chosen from 1 choice
[    4.036000] hub 3-0:1.0: USB hub found
[    4.036000] hub 3-0:1.0: 2 ports detected
[    4.140000] ata_piix 0000:00:1f.1: version 2.11
[    4.140000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[    4.140000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    4.140000] scsi0 : ata_piix
[    4.140000] scsi1 : ata_piix
[    4.140000] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011810 irq 14
[    4.140000] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011818 irq 15
[    4.504000] ata1.00: ATA-6: HTS541010G9AT00, MBZOA60A, max UDMA/100
[    4.504000] ata1.00: 195371568 sectors, multi 16: LBA48 
[    4.504000] ata1.01: ATAPI: TSSTcorpCD/DVDW TS-L632D, ac00, max UDMA/33
[    4.504000] ata1.00: limited to UDMA/33 due to 40-wire cable
[    4.520000] ata1.00: configured for UDMA/33
[    4.708000] ata1.01: configured for UDMA/33
[    4.904000] scsi 0:0:0:0: Direct-Access     ATA      HTS541010G9AT00  MBZO PQ: 0 ANSI: 5
[    4.916000] scsi 0:0:1:0: CD-ROM            TSSTcorp CD/DVDW TS-L632D ac00 PQ: 0 ANSI: 5
[    4.916000] ACPI: PCI Interrupt 0000:0a:00.0[A] -> GSI 17 (level, low) -> IRQ 16
[    4.916000] eth0: RealTek RTL8139 at 0xe0072000, 00:16:36:63:fa:98, IRQ 16
[    4.916000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    4.916000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 21
[    4.916000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    4.916000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.916000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[    4.916000] ehci_hcd 0000:00:1d.7: debug port 1
[    4.916000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    4.916000] ehci_hcd 0000:00:1d.7: irq 21, io mem 0xb0004000
[    4.920000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.920000] usb usb4: configuration #1 chosen from 1 choice
[    4.920000] hub 4-0:1.0: USB hub found
[    4.920000] hub 4-0:1.0: 8 ports detected
[    4.920000] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    5.024000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 17
[    5.024000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    5.024000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    5.024000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    5.024000] uhci_hcd 0000:00:1d.3: irq 17, io base 0x00001880
[    5.024000] usb usb5: configuration #1 chosen from 1 choice
[    5.024000] hub 5-0:1.0: USB hub found
[    5.024000] hub 5-0:1.0: 2 ports detected
[    5.148000] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
[    5.148000] sd 0:0:0:0: [sda] Write Protect is off
[    5.148000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.148000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.148000] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
[    5.148000] sd 0:0:0:0: [sda] Write Protect is off
[    5.148000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.148000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.148000]  sda: sda1 sda2 < sda5 >
[    5.192000] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.200000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.200000] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    5.272000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.272000] Uniform CD-ROM driver Revision: 3.20
[    5.272000] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    5.448000] usb 5-2: new low speed USB device using uhci_hcd and address 2
[    5.552000] Attempting manual resume
[    5.552000] swsusp: Resume From Partition 8:5
[    5.552000] PM: Checking swsusp image.
[    5.552000] PM: Resume from disk failed.
[    5.600000] kjournald starting.  Commit interval 5 seconds
[    5.600000] EXT3-fs: mounted filesystem with ordered data mode.
[    5.628000] usb 5-2: configuration #1 chosen from 1 choice
[   15.272000] ip_tables: (C) 2000-2006 Netfilter Core Team
[   15.324000] Netfilter messages via NETLINK v0.30.
[   15.344000] nf_conntrack version 0.5.0 (4020 buckets, 32160 max)
[   16.512000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   16.528000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.752000] Linux agpgart interface v0.102 (c) Dave Jones
[   16.820000] agpgart: Detected an Intel 945GM Chipset.
[   16.820000] agpgart: Detected 7932K stolen memory.
[   16.836000] agpgart: AGP aperture is 256M @ 0xc0000000
[   17.256000] Yenta: CardBus bridge found at 0000:0a:09.0 [1025:0102]
[   17.256000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   17.256000] Yenta: Routing CardBus interrupts to PCI
[   17.256000] Yenta TI: socket 0000:0a:09.0, mfunc 0x01321b22, devctl 0x66
[   17.272000] ieee80211_crypt: registered algorithm 'NULL'
[   17.272000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   17.272000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   17.400000] iTCO_vendor_support: vendor-support=0
[   17.488000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 20
[   17.488000] Socket status: 30000006
[   17.488000] Yenta: Raising subordinate bus# of parent bus (#0a) from #0b to #0e
[   17.488000] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   17.488000] cs: IO port probe 0x2000-0x2fff: clean.
[   17.488000] pcmcia: parent PCI bridge Memory window: 0xb0300000 - 0xb03fffff
[   17.488000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[   17.512000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.2mp.ubuntu1
[   17.512000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   17.512000] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
[   17.512000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 17
[   17.512000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   17.520000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   17.520000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   17.628000] sdhci: Secure Digital Host Controller Interface driver
[   17.628000] sdhci: Copyright(c) Pierre Ossman
[   17.628000] sdhci: SDHCI controller found at 0000:0a:09.3 [104c:803c] (rev 0)
[   17.628000] ACPI: PCI Interrupt 0000:0a:09.3[A] -> GSI 20 (level, low) -> IRQ 20
[   17.628000] mmc0: SDHCI at 0xb0300400 irq 20 DMA
[   17.644000] ACPI: PCI Interrupt 0000:0a:09.2[A] -> GSI 20 (level, low) -> IRQ 20
[   17.824000] usbcore: registered new interface driver hiddev
[   17.836000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input2
[   17.836000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.3-2
[   17.836000] usbcore: registered new interface driver usbhid
[   17.836000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   17.884000] snd_rawmidi: disagrees about version of symbol snd_info_register
[   17.884000] snd_rawmidi: Unknown symbol snd_info_register
[   17.884000] snd_rawmidi: disagrees about version of symbol snd_seq_device_new
[   17.884000] snd_rawmidi: Unknown symbol snd_seq_device_new
[   17.884000] snd_rawmidi: disagrees about version of symbol snd_info_free_entry
[   17.884000] snd_rawmidi: Unknown symbol snd_info_free_entry
[   17.884000] snd_rawmidi: disagrees about version of symbol snd_unregister_oss_device
[   17.884000] snd_rawmidi: Unknown symbol snd_unregister_oss_device
[   17.884000] snd_rawmidi: disagrees about version of symbol snd_register_oss_device
[   17.884000] snd_rawmidi: Unknown symbol snd_register_oss_device
[   17.884000] snd_rawmidi: disagrees about version of symbol snd_ctl_register_ioctl
[   17.884000] snd_rawmidi: Unknown symbol snd_ctl_register_ioctl
[   17.884000] snd_rawmidi: disagrees about version of symbol snd_card_file_add
[   17.884000] snd_rawmidi: Unknown symbol snd_card_file_add
[   17.884000] snd_rawmidi: disagrees about version of symbol snd_unregister_device
[   17.884000] snd_rawmidi: Unknown symbol snd_unregister_device
[   17.884000] snd_rawmidi: disagrees about version of symbol snd_device_new
[   17.884000] snd_rawmidi: Unknown symbol snd_device_new
[   17.884000] snd_rawmidi: disagrees about version of symbol snd_ctl_unregister_ioctl
[   17.884000] snd_rawmidi: Unknown symbol snd_ctl_unregister_ioctl
[   17.884000] snd_rawmidi: disagrees about version of symbol snd_info_create_card_entry
[   17.884000] snd_rawmidi: Unknown symbol snd_info_create_card_entry
[   17.884000] snd_rawmidi: disagrees about version of symbol snd_card_file_remove
[   17.884000] snd_rawmidi: Unknown symbol snd_card_file_remove
[   17.884000] snd_rawmidi: disagrees about version of symbol snd_register_device_for_dev
[   17.884000] snd_rawmidi: Unknown symbol snd_register_device_for_dev
[   17.884000] snd_rawmidi: disagrees about version of symbol snd_device_register
[   17.884000] snd_rawmidi: Unknown symbol snd_device_register
[   17.944000] snd_seq_midi: Unknown symbol snd_rawmidi_info_select
[   17.948000] snd_seq_midi: Unknown symbol snd_rawmidi_output_params
[   17.948000] snd_seq_midi: Unknown symbol snd_rawmidi_kernel_read
[   17.948000] snd_seq_midi: disagrees about version of symbol snd_seq_device_register_driver
[   17.948000] snd_seq_midi: Unknown symbol snd_seq_device_register_driver
[   17.948000] snd_seq_midi: Unknown symbol snd_rawmidi_kernel_write
[   17.948000] snd_seq_midi: Unknown symbol snd_rawmidi_drain_output
[   17.948000] snd_seq_midi: Unknown symbol snd_rawmidi_input_params
[   17.948000] snd_seq_midi: Unknown symbol snd_rawmidi_kernel_open
[   17.948000] snd_seq_midi: disagrees about version of symbol snd_seq_create_kernel_client
[   17.948000] snd_seq_midi: Unknown symbol snd_seq_create_kernel_client
[   17.948000] snd_seq_midi: Unknown symbol snd_rawmidi_kernel_release
[   18.076000] cs: IO port probe 0x100-0x3af: clean.
[   18.080000] cs: IO port probe 0x3e0-0x4ff:snd_seq_dummy: disagrees about version of symbol snd_seq_create_kernel_client
[   18.080000] snd_seq_dummy: Unknown symbol snd_seq_create_kernel_client
[   18.080000]  excluding 0x4d0-0x4d7
[   18.080000] cs: IO port probe 0x820-0x8ff: clean.
[   18.080000] cs: IO port probe 0xc00-0xcf7: clean.
[   18.080000] cs: IO port probe 0xa00-0xaff: clean.
[   18.084000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x12a0b1, caps: 0xa04713/0x204000
[   18.124000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   18.128000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   18.128000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   18.340000] intel_rng: FWH not detected
[   18.528000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   18.528000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   19.524000] ipw3945: Radio Frequency Kill Switch is On:
[   19.524000] Kill switch must be turned off for wireless networking to work.
[   19.544000] lp: driver loaded but no devices found
[   19.604000] Adding 1477940k swap on /dev/sda5.  Priority:-1 extents:1 across:1477940k
[  270.616000] EXT3 FS on sda1, internal journal
[  273.624000] ACPI: Battery Slot [BAT1] (battery present)
[  273.880000] No dock devices found.
[  274.032000] input: Power Button (FF) as /class/input/input4
[  274.032000] ACPI: Power Button (FF) [PWRF]
[  274.032000] input: Lid Switch as /class/input/input5
[  274.032000] ACPI: Lid Switch [LID]
[  274.048000] input: Power Button (CM) as /class/input/input6
[  274.052000] ACPI: Power Button (CM) [PWRB]
[  274.052000] input: Sleep Button (CM) as /class/input/input7
[  274.052000] ACPI: Sleep Button (CM) [SLPB]
[  274.148000] ACPI: AC Adapter [ACAD] (on-line)
[  274.160000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[  278.732000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  278.936000] ppdev: user-space parallel port driver
[  280.940000] audit(1203182375.826:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5124 profile="/usr/sbin/cupsd"
[  281.304000] [drm] Initialized drm 1.1.0 20060810
[  281.352000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[  281.352000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[  281.404000] apm: BIOS not found.
[  282.392000] Failure registering capabilities with primary security module.
[  282.992000] Bluetooth: Core ver 2.11
[  282.992000] NET: Registered protocol family 31
[  282.992000] Bluetooth: HCI device and connection manager initialized
[  282.992000] Bluetooth: HCI socket layer initialized
[  283.080000] Bluetooth: L2CAP ver 2.8
[  283.080000] Bluetooth: L2CAP socket layer initialized
[  283.224000] Bluetooth: RFCOMM socket layer initialized
[  283.224000] Bluetooth: RFCOMM TTY layer initialized
[  283.224000] Bluetooth: RFCOMM ver 1.8
[  288.052000] NET: Registered protocol family 17
[  291.260000] NET: Registered protocol family 10
[  291.260000] lo: Disabled Privacy Extensions
[  294.308000] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:01:5c:22:55:82:08:00 SRC=10.245.128.1 DST=255.255.255.255 LEN=387 TOS=0x00 PREC=0x00 TTL=64 ID=19910 PROTO=UDP SPT=67 DPT=68 LEN=367 

```

---

### Post by gymmeh on 2008-03-07
So the one thing that does not freeze is Tremulous?

Any Ideas

---

