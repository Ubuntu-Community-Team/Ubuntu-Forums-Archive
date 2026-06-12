---
title: "Another sound issue. Please help!"
date: 2007-05-05
forum: Hardware &amp; Laptops
---

### Post by green1152 on 2007-05-05
Hello. I am having another issue with my sound. It's not working completely. 

Here is the output when I input these commands:

dmesg
lspci
lsmod

```
[   10.317055] Total of 1 processors activated (4003.29 BogoMIPS).
[   10.317202] ENABLING IO-APIC IRQs
[   10.317375] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   10.465486] Brought up 1 CPUs
[   10.465690] Booting paravirtualized kernel on bare hardware
[   10.465747] Time: 18:24:12  Date: 04/05/107
[   10.465770] NET: Registered protocol family 16
[   10.465839] EISA bus registered
[   10.465843] ACPI: bus type pci registered
[   10.465904] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=3
[   10.465906] PCI: Using configuration type 1
[   10.465907] Setting up standard PCI resources
[   10.481005] ACPI: Interpreter enabled
[   10.481007] ACPI: Using IOAPIC for interrupt routing
[   10.493813] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   10.493821] PCI: Probing PCI hardware (bus 00)
[   10.494372] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[   10.494375] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[   10.494523] Boot video device is 0000:03:00.0
[   10.494854] PCI: Transparent bridge - 0000:00:1e.0
[   10.494890] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   11.048049] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   11.095547] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[   11.096447] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   11.096654] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   11.096858] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   11.097062] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   11.097268] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   11.097473] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   11.097678] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   11.097883] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   11.097983] Linux Plug and Play Support v0.97 (c) Adam Belay
[   11.097990] pnp: PnP ACPI init
[   11.107943] pnp: PnP ACPI: found 12 devices
[   11.107947] PnPBIOS: Disabled by ACPI PNP
[   11.107984] PCI: Using ACPI for IRQ routing
[   11.107986] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   11.107991] PCI: Cannot allocate resource region 7 of bridge 0000:00:1e.0
[   11.108014] PCI: Cannot allocate resource region 0 of device 0000:01:07.0
[   11.108016] PCI: Cannot allocate resource region 1 of device 0000:01:07.0
[   11.108018] PCI: Cannot allocate resource region 2 of device 0000:01:07.0
[   11.108020] PCI: Cannot allocate resource region 3 of device 0000:01:07.0
[   11.108022] PCI: Cannot allocate resource region 4 of device 0000:01:07.0
[   11.108024] PCI: Cannot allocate resource region 5 of device 0000:01:07.0
[   11.113023] NET: Registered protocol family 8
[   11.113025] NET: Registered protocol family 20
[   11.117625] PCI: Bridge: 0000:00:01.0
[   11.117627]   IO window: disabled.
[   11.117630]   MEM window: faa00000-feafffff
[   11.117633]   PREFETCH window: bfe00000-dfefffff
[   11.117636] PCI: Bridge: 0000:00:1c.0
[   11.117638]   IO window: d000-dfff
[   11.117642]   MEM window: bfc00000-bfcfffff
[   11.117646]   PREFETCH window: bfd00000-bfdfffff
[   11.117665] PCI: Bridge: 0000:00:1e.0
[   11.117668]   IO window: 1000-1fff
[   11.117672]   MEM window: fa900000-fa9fffff
[   11.117675]   PREFETCH window: 50000000-500fffff
[   11.117688] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   11.117692] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   11.117705] PCI: Enabling device 0000:00:1c.0 (0106 -> 0107)
[   11.117708] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   11.117713] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   11.117721] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   11.117738] NET: Registered protocol family 2
[   11.156222] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   11.156313] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   11.157055] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   11.157541] TCP: Hash tables configured (established 131072 bind 65536)
[   11.157544] TCP reno registered
[   11.168294] checking if image is initramfs... it is
[   11.736329] Freeing initrd memory: 7011k freed
[   11.736734] audit: initializing netlink socket (disabled)
[   11.736749] audit(1178389452.780:1): initialized
[   11.736815] highmem bounce pool size: 64 pages
[   11.736872] VFS: Disk quotas dquot_6.5.1
[   11.736890] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   11.736939] io scheduler noop registered
[   11.736942] io scheduler anticipatory registered
[   11.736944] io scheduler deadline registered
[   11.736953] io scheduler cfq registered (default)
[   11.763220] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   11.763247] assign_interrupt_mode Found MSI capability
[   11.763250] Allocate Port Service[0000:00:01.0:pcie00]
[   11.763314] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   11.763346] assign_interrupt_mode Found MSI capability
[   11.763348] Allocate Port Service[0000:00:1c.0:pcie00]
[   11.763371] Allocate Port Service[0000:00:1c.0:pcie02]
[   11.763484] isapnp: Scanning for PnP cards...
[   12.115955] isapnp: No Plug & Play device found
[   12.137441] Real Time Clock Driver v1.12ac
[   12.137494] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   12.138085] mice: PS/2 mouse device common for all mice
[   12.138586] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   12.138777] input: Macintosh mouse button emulation as /class/input/input0
[   12.138804] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   12.138807] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   12.138977] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   12.143837] i8042.c: Detected active multiplexing controller, rev 1.0.
[   12.144707] serio: i8042 KBD port at 0x60,0x64 irq 1
[   12.144710] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   12.144713] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   12.144715] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   12.144717] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   12.144806] EISA: Probing bus 0 at eisa.0
[   12.144813] Cannot allocate resource for EISA slot 1
[   12.144832] EISA: Detected 0 cards.
[   12.174863] TCP cubic registered
[   12.174870] NET: Registered protocol family 1
[   12.174889] Using IPI No-Shortcut mode
[   12.174945] ACPI: (supports S0 S3 S4 S5)
[   12.174984]   Magic number: 7:651:442
[   12.175256] Freeing unused kernel memory: 328k freed
[   12.175706] input: AT Translated Set 2 keyboard as /class/input/input1
[   12.178261] Time: tsc clocksource has been installed.
[   13.360840] Capability LSM initialized
[   13.389907] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   13.389912] ACPI: Processor [CPU1] (supports 8 throttling states)
[   13.392055] ACPI: Thermal Zone [THRM] (24 C)
[   13.687473] usbcore: registered new interface driver usbfs
[   13.687494] usbcore: registered new interface driver hub
[   13.687520] usbcore: registered new device driver usb
[   13.688209] USB Universal Host Controller Interface driver v3.0
[   13.688259] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 17
[   13.688268] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   13.688272] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   13.688407] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   13.688436] uhci_hcd 0000:00:1d.0: irq 17, io base 0x0000e480
[   13.688518] usb usb1: configuration #1 chosen from 1 choice
[   13.688536] hub 1-0:1.0: USB hub found
[   13.688541] hub 1-0:1.0: 2 ports detected
[   13.734994] SCSI subsystem initialized
[   13.739257] libata version 2.20 loaded.
[   13.792043] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 18
[   13.792054] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   13.792057] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   13.792075] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   13.792101] uhci_hcd 0000:00:1d.1: irq 18, io base 0x0000e800
[   13.792174] usb usb2: configuration #1 chosen from 1 choice
[   13.792196] hub 2-0:1.0: USB hub found
[   13.792201] hub 2-0:1.0: 2 ports detected
[   13.852086] ieee1394: Initialized config rom entry `ip1394'
[   13.895259] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
[   13.895271] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   13.895275] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   13.895293] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   13.895320] uhci_hcd 0000:00:1d.2: irq 19, io base 0x0000e880
[   13.895397] usb usb3: configuration #1 chosen from 1 choice
[   13.895418] hub 3-0:1.0: USB hub found
[   13.895423] hub 3-0:1.0: 2 ports detected
[    3.788000] Time: acpi_pm clocksource has been installed.
[    3.852000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[    3.852000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    3.852000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.852000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.852000] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000ec00
[    3.852000] usb usb4: configuration #1 chosen from 1 choice
[    3.852000] hub 4-0:1.0: USB hub found
[    3.852000] hub 4-0:1.0: 2 ports detected
[    3.956000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 17
[    3.956000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    3.956000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.956000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    3.956000] ehci_hcd 0000:00:1d.7: debug port 1
[    3.956000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    3.956000] ehci_hcd 0000:00:1d.7: irq 17, io mem 0xfebffc00
[    3.960000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.960000] usb usb5: configuration #1 chosen from 1 choice
[    3.960000] hub 5-0:1.0: USB hub found
[    3.960000] hub 5-0:1.0: 8 ports detected
[    4.064000] ata_piix 0000:00:1f.1: version 2.10ac1
[    4.064000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 19
[    4.064000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    4.064000] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
[    4.064000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
[    4.064000] scsi0 : ata_piix
[    4.384000] ata1.00: ATAPI, max UDMA/33
[    4.548000] ata1.00: configured for UDMA/33
[    4.548000] scsi1 : ata_piix
[    4.596000] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    4.704000] ATA: abnormal status 0x7F on port 0x00010177
[    4.708000] scsi 0:0:0:0: CD-ROM            Slimtype DVDRW SOSW-833S  VS04 PQ: 0 ANSI: 5
[    4.756000] ACPI: PCI Interrupt 0000:01:04.0[A] -> GSI 18 (level, low) -> IRQ 19
[    4.808000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[fa9ff000-fa9ff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    4.808000] r8169 Gigabit Ethernet driver 2.2LK loaded
[    4.808000] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 19 (level, low) -> IRQ 18
[    4.808000] eth0: RTL8169sb/8110sb at 0xf8856c00, 00:03:0d:36:2e:d7, IRQ 18
[    4.808000] sata_via 0000:01:07.0: version 2.1
[    4.808000] ACPI: PCI Interrupt 0000:01:07.0[A] -> GSI 16 (level, low) -> IRQ 16
[    4.808000] sata_via 0000:01:07.0: routed to hard irq line 10
[    4.808000] ata3: SATA max UDMA/133 cmd 0x00011420 ctl 0x0001142a bmdma 0x00011400 irq 16
[    4.808000] ata4: SATA max UDMA/133 cmd 0x00011430 ctl 0x0001143a bmdma 0x00011408 irq 16
[    4.808000] ata5: PATA max UDMA/133 cmd 0x00011440 ctl 0x0001144a bmdma 0x00011410 irq 16
[    4.808000] scsi2 : sata_via
[    4.816000] usb 3-1: configuration #1 chosen from 1 choice
[    4.820000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    4.820000] Uniform CD-ROM driver Revision: 3.20
[    4.820000] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    4.824000] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    4.832000] usbcore: registered new interface driver hiddev
[    4.852000] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /class/input/input2
[    4.852000] input: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.2-1
[    4.852000] usbcore: registered new interface driver usbhid
[    4.852000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[    5.276000] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[    5.284000] ata3.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    5.284000] ata3.00: ATA-7: FUJITSU MHT2080BH, 0000104A, max UDMA/100
[    5.284000] ata3.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    5.292000] ata3.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    5.292000] ata3.00: configured for UDMA/100
[    5.292000] scsi3 : sata_via
[    5.604000] ata4: SATA link down (SStatus 0 SControl 310)
[    5.604000] ATA: abnormal status 0x7F on port 0x00011437
[    5.608000] scsi4 : sata_via
[    5.764000] ATA: abnormal status 0x8 on port 0x00011447
[    5.768000] scsi 2:0:0:0: Direct-Access     ATA      FUJITSU MHT2080B 0000 PQ: 0 ANSI: 5
[    5.768000] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[    5.776000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    5.776000] sda: Write Protect is off
[    5.776000] sda: Mode Sense: 00 3a 00 00
[    5.776000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.776000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    5.776000] sda: Write Protect is off
[    5.776000] sda: Mode Sense: 00 3a 00 00
[    5.776000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.776000]  sda: sda1 sda2 < sda5 >
[    5.840000] sd 2:0:0:0: Attached scsi disk sda
[    6.056000] Attempting manual resume
[    6.056000] swsusp: Resume From Partition 8:5
[    6.056000] PM: Checking swsusp image.
[    6.056000] PM: Resume from disk failed.
[    6.080000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00030d4971e1e4eb]
[    6.100000] kjournald starting.  Commit interval 5 seconds
[    6.100000] EXT3-fs: mounted filesystem with ordered data mode.
[   15.724000] r8169: eth0: link down
[   16.704000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   16.728000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.840000] Linux agpgart interface v0.102 (c) Dave Jones
[   16.840000] agpgart: Detected an Intel 915GM Chipset.
[   16.860000] agpgart: AGP aperture is 256M @ 0x0
[   17.444000] iTCO_vendor_support: vendor-support=0
[   17.460000] NET: Registered protocol family 17
[   17.744000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   17.764000] ieee80211_crypt: registered algorithm 'NULL'
[   17.764000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   17.764000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   17.820000] nvidia: module license 'NVIDIA' taints kernel.
[   18.096000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   18.096000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   18.096000] NVRM: loading NVIDIA UNIX x86 Kernel Module  1.0-9755  Mon Feb 26 23:21:15 PST 2007
[   18.100000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[   18.100000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   18.100000] ACPI: PCI Interrupt 0000:01:03.0[A] -> GSI 19 (level, low) -> IRQ 18
[   18.100000] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
[   18.324000] ipw2200: Detected geography ZZA (11 802.11bg channels, 13 802.11a channels)
[   18.452000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x6eb1, caps: 0xa04711/0x40a
[   18.492000] ieee80211_crypt: registered algorithm 'WEP'
[   18.492000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   18.516000] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x0860)
[   18.516000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   18.520000] input: PC Speaker as /class/input/input4
[   18.596000] intel_rng: FWH not detected
[   18.680000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   18.680000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   19.264000] fuse init (API version 7.8)
[   19.316000] lp: driver loaded but no devices found
[   19.408000] Adding 3028212k swap on /dev/disk/by-uuid/42166573-07b5-4b82-bc77-010e327b76ba.  Priority:-1 extents:1 across:3028212k
[   19.544000] EXT3 FS on sda1, internal journal
[   23.760000] ibm_acpi: ec object not found
[   23.868000] input: Power Button (FF) as /class/input/input5
[   23.872000] ACPI: Power Button (FF) [PWRF]
[   23.904000] input: Lid Switch as /class/input/input6
[   23.908000] ACPI: Lid Switch [LID]
[   23.940000] input: Sleep Button (CM) as /class/input/input7
[   23.940000] ACPI: Sleep Button (CM) [SLPB]
[   23.976000] input: Power Button (CM) as /class/input/input8
[   23.976000] ACPI: Power Button (CM) [PWRB]
[   24.020000] ACPI: Battery Slot [BAT0] (battery present)
[   24.024000] No dock devices found.
[   24.040000] Using specific hotkey driver
[   24.064000] ACPI Error (utglobal-0125): Unknown exception code: 0xFFFFFFFE [20060707]
[   24.064000] ACPI Exception (acpi_video-1564): UNKNOWN_STATUS_CODE, Cant attach device [20060707]
[   24.064000] ACPI: Video Device [PEG] (multi-head: yes  rom: no  post: no)
[   24.072000] ACPI: AC Adapter [AC0] (on-line)
[   24.116000] wmi_add device=c192ac00
[   24.116000] calling WQBA
[   24.128000] pcc_acpi: loading...
[   28.764000] ppdev: user-space parallel port driver
[   31.312000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   31.312000] apm: overridden by ACPI.
[   31.456000] Bluetooth: Core ver 2.11
[   31.456000] NET: Registered protocol family 31
[   31.456000] Bluetooth: HCI device and connection manager initialized
[   31.456000] Bluetooth: HCI socket layer initialized
[   31.496000] Bluetooth: L2CAP ver 2.8
[   31.496000] Bluetooth: L2CAP socket layer initialized
[   31.612000] Bluetooth: RFCOMM socket layer initialized
[   31.612000] Bluetooth: RFCOMM TTY layer initialized
[   31.612000] Bluetooth: RFCOMM ver 1.8
[   46.344000] NET: Registered protocol family 10
[   46.344000] lo: Disabled Privacy Extensions
[   46.344000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   57.156000] eth1: no IPv6 routers present
chase@chase-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:03.0 Network controller: Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05)
01:04.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
01:07.0 RAID bus controller: VIA Technologies, Inc. VT6421 IDE RAID Controller (rev 50)
03:00.0 VGA compatible controller: nVidia Corporation NV41.8 [GeForce Go 6800] (rev a2)
chase@chase-laptop:~$ lsmod
Module                  Size  Used by
ipv6                  268704  8 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
speedstep_centrino      9920  0 
cpufreq_userspace       5408  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7360  0 
cpufreq_conservative     8200  0 
cpufreq_ondemand        9228  1 
freq_table              5792  3 speedstep_centrino,cpufreq_stats,cpufreq_ondemand
sony_acpi               6284  0 
pcc_acpi               13184  0 
tc1100_wmi              8068  0 
dev_acpi               12292  0 
ac                      6020  0 
video                  16388  0 
asus_acpi              17308  0 
sbs                    15652  0 
i2c_ec                  5888  1 sbs
dock                   10268  0 
battery                10756  0 
button                  8720  0 
container               5248  0 
backlight               7040  1 asus_acpi
sbp2                   23812  0 
parport_pc             36388  0 
lp                     12452  0 
parport                36936  3 ppdev,parport_pc,lp
fuse                   46612  1 
joydev                 10816  0 
snd_hda_intel          21912  1 
snd_hda_codec         205440  1 snd_hda_intel
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
arc4                    2944  2 
ecb                     4480  2 
blkcipher               6784  1 ecb
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
ieee80211_crypt_wep     6144  1 
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ipw2200               148040  0 
nvidia               6837140  22 
pcspkr                  4224  0 
ieee80211              34760  1 ipw2200
ieee80211_crypt         7040  2 ieee80211_crypt_wep,ieee80211
iTCO_wdt               11812  0 
serio_raw               7940  0 
psmouse                38920  0 
snd                    54020  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
af_packet              23816  6 
iTCO_vendor_support     4868  1 iTCO_wdt
i2c_core               22784  2 i2c_ec,nvidia
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
intel_agp              25116  1 
agpgart                35400  2 nvidia,intel_agp
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
evdev                  11008  5 
tsdev                   8768  0 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sd_mod                 23428  3 
usbhid                 26592  0 
hid                    27392  1 usbhid
sg                     36252  0 
sr_mod                 17060  0 
cdrom                  37664  1 sr_mod
generic                 5124  0 [permanent]
ata_generic             9092  0 
sata_via               12548  2 
r8169                  32392  0 
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
ata_piix               15492  0 
libata                125720  3 ata_generic,sata_via,ata_piix
scsi_mod              142348  5 sbp2,sd_mod,sg,sr_mod,libata
ehci_hcd               34188  0 
uhci_hcd               25360  0 
usbcore               134280  4 usbhid,ehci_hcd,uhci_hcd
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability
chase@chase-laptop:~$ 

```

Thank you very much.

---

