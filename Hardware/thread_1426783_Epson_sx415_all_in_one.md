---
title: "Epson sx415 all in one"
date: 2010-03-10
forum: Hardware
---

### Post by chuggly on 2010-03-10
Hello all

I have a problem.
I run an Acer Aspire 9301AWSMI with nvidia graphics.

I also run an old home built desktop
Athlon 800mhz
ATI 32mb graphics
256mb ram
80g ide hdd
old scsi card not used
old hauppauge card not used
old soundblaster card not used
Belkin 7 port usb hub plugged into newish Belkin usb2 card.

On both machines, the printer works fine.
I am running gutenprint on both machines.
I am running Ubuntu 9.10 32 bit on both machines


The scanner of the sx415 works fine on the laptop but is not recognised by the desktop. Both run 

The only other thing is the unit is plugged into a usb hub on the desktop and direct on the laptop. I haven't tried plugging directly into the desktop as it is a bugger to get to and is sort of built in to the desk I made.

I know it is a bit of a dinosaur, but it never crashes, except when running a MS product and has been faultless since I built it about 8 years ago.
It is basically used as a word basher by my wife.

Result of DMESG on the dinosaur is:-

 Freeing initrd memory: 7466k freed
[    0.823353] cpufreq-nforce2: No nForce2 chipset.
[    0.823431] Scanning for low memory corruption every 60 seconds
[    0.823803] audit: initializing netlink socket (disabled)
[    0.823860] type=2000 audit(1268258294.820:1): initialized
[    0.849144] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.853844] VFS: Disk quotas dquot_6.5.2
[    0.854046] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.855843] fuse init (API version 7.12)
[    0.856188] msgmni has been set to 488
[    0.857021] alg: No test for stdrng (krng)
[    0.857089] io scheduler noop registered
[    0.857097] io scheduler anticipatory registered
[    0.857104] io scheduler deadline registered
[    0.857274] io scheduler cfq registered (default)
[    0.857436] pci 0000:01:05.0: Boot video device
[    0.857670] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.857743] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.858116] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.858132] ACPI: Power Button [PWRF]
[    0.858277] input: Sleep Button as /devices/LNXSYSTM:00/LNXSLPBN:00/input/input1
[    0.858286] ACPI: Sleep Button [SLPF]
[    0.858444] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
[    0.858453] ACPI: Power Button [PWRB]
[    0.858830] processor LNXCPU:00: registered as cooling_device0
[    0.864608] thermal LNXTHERM:01: registered as thermal_zone0
[    0.864637] ACPI: Thermal Zone [THRM] (29 C)
[    0.864791] isapnp: Scanning for PnP cards...
[    1.219451] isapnp: No Plug & Play device found
[    1.223120] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.223342] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.223552] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.224234] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.224485] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.227629] brd: module loaded
[    1.229128] loop: module loaded
[    1.229443] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.230259] pata_amd 0000:00:07.1: version 0.4.1
[    1.230758] scsi0 : pata_amd
[    1.231168] scsi1 : pata_amd
[    1.231277] ata1: PATA max UDMA/66 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    1.231287] ata2: PATA max UDMA/66 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    1.233253] Fixed MDIO Bus: probed
[    1.233363] PPP generic driver version 2.4.2
[    1.233689] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.234258] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[    1.234269] PCI: setting IRQ 11 as level-triggered
[    1.234282] ehci_hcd 0000:00:0b.2: PCI INT C -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    1.234330] ehci_hcd 0000:00:0b.2: EHCI Host Controller
[    1.234491] ehci_hcd 0000:00:0b.2: new USB bus registered, assigned bus number 1
[    1.234610] ehci_hcd 0000:00:0b.2: irq 11, io mem 0xefffff00
[    1.244040] ehci_hcd 0000:00:0b.2: USB 2.0 started, EHCI 1.00
[    1.244316] usb usb1: configuration #1 chosen from 1 choice
[    1.244409] hub 1-0:1.0: USB hub found
[    1.244449] hub 1-0:1.0: 4 ports detected
[    1.244620] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.245133] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 12
[    1.245144] PCI: setting IRQ 12 as level-triggered
[    1.245156] ohci_hcd 0000:00:07.4: PCI INT D -> Link[LNKD] -> GSI 12 (level, low) -> IRQ 12
[    1.245193] ohci_hcd 0000:00:07.4: OHCI Host Controller
[    1.245355] ohci_hcd 0000:00:07.4: new USB bus registered, assigned bus number 2
[    1.245413] ohci_hcd 0000:00:07.4: irq 12, io mem 0xefffd000
[    1.300278] usb usb2: configuration #1 chosen from 1 choice
[    1.300362] hub 2-0:1.0: USB hub found
[    1.300396] hub 2-0:1.0: 4 ports detected
[    1.300557] uhci_hcd: USB Universal Host Controller Interface driver
[    1.300717] uhci_hcd 0000:00:0b.0: PCI INT A -> Link[LNKD] -> GSI 12 (level, low) -> IRQ 12
[    1.300738] uhci_hcd 0000:00:0b.0: UHCI Host Controller
[    1.300853] uhci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 3
[    1.300896] uhci_hcd 0000:00:0b.0: irq 12, io base 0x0000da00
[    1.301156] usb usb3: configuration #1 chosen from 1 choice
[    1.301253] hub 3-0:1.0: USB hub found
[    1.301286] hub 3-0:1.0: 2 ports detected
[    1.301828] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[    1.301838] PCI: setting IRQ 10 as level-triggered
[    1.301851] uhci_hcd 0000:00:0b.1: PCI INT B -> Link[LNKA] -> GSI 10 (level, low) -> IRQ 10
[    1.301872] uhci_hcd 0000:00:0b.1: UHCI Host Controller
[    1.302003] uhci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 4
[    1.302048] uhci_hcd 0000:00:0b.1: irq 10, io base 0x0000dc00
[    1.302364] usb usb4: configuration #1 chosen from 1 choice
[    1.302465] hub 4-0:1.0: USB hub found
[    1.302508] hub 4-0:1.0: 2 ports detected
[    1.302754] PNP: PS/2 Controller [PNP030b:PS2K] at 0x60,0x64 irq 1
[    1.302763] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.303268] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.303512] mice: PS/2 mouse device common for all mice
[    1.303950] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.303990] rtc0: alarms up to one year, y3k, 114 bytes nvram
[    1.304363] device-mapper: uevent: version 1.0.3
[    1.304766] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    1.305103] device-mapper: multipath: version 1.1.0 loaded
[    1.305113] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.305595] EISA: Probing bus 0 at eisa.0
[    1.305632] Cannot allocate resource for EISA slot 5
[    1.305655] EISA: Detected 0 cards.
[    1.305860] cpuidle: using governor ladder
[    1.305868] cpuidle: using governor menu
[    1.307461] TCP cubic registered
[    1.307966] NET: Registered protocol family 10
[    1.309440] lo: Disabled Privacy Extensions
[    1.310425] NET: Registered protocol family 17
[    1.310506] Bluetooth: L2CAP ver 2.13
[    1.310512] Bluetooth: L2CAP socket layer initialized
[    1.310521] Bluetooth: SCO (Voice Link) ver 0.6
[    1.310527] Bluetooth: SCO socket layer initialized
[    1.310713] Bluetooth: RFCOMM TTY layer initialized
[    1.310724] Bluetooth: RFCOMM socket layer initialized
[    1.310730] Bluetooth: RFCOMM ver 1.11
[    1.310777] powernow-k8: Processor cpuid 622 not supported
[    1.310840] Using IPI No-Shortcut mode
[    1.311091] PM: Resume from disk failed.
[    1.311137] registered taskstats version 1
[    1.311455]   Magic number: 2:403:1005
[    1.311573] input input2: hash matches
[    1.311592] pnp 00:07: hash matches
[    1.311694] rtc_cmos 00:03: setting system clock to 2010-03-10 21:58:15 UTC (1268258295)
[    1.311704] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.311710] EDD information not available.
[    1.323923] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.396447] ata1.00: ATA-7: SAMSUNG SP0802N, TK200-04, max UDMA/100
[    1.396457] ata1.00: 156368016 sectors, multi 16: LBA48 
[    1.404366] ata1.00: configured for UDMA/66
[    1.404817] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG SP0802N  TK20 PQ: 0 ANSI: 5
[    1.405233] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.405434] sd 0:0:0:0: [sda] 156368016 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.405636] sd 0:0:0:0: [sda] Write Protect is off
[    1.405647] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.405750] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.406271]  sda: sda1 sda2 < sda5 >
[    1.441163] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.556048] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.689079] usb 1-1: configuration #1 chosen from 1 choice
[    1.800438] ata2.00: ATAPI: HL-DT-STDVD-RAM GH22LP20, 1.02, max UDMA/66
[    1.800521] ata2.01: ATAPI: SONY    CD-RW  CRX215E1, SYS2, max UDMA/33
[    1.800581] ata2.00: limited to UDMA/33 due to 40-wire cable
[    1.816335] ata2.00: configured for UDMA/33
[    1.832267] ata2.01: configured for UDMA/33
[    1.854768] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GH22LP20 1.02 PQ: 0 ANSI: 5
[    1.858570] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.858582] Uniform CD-ROM driver Revision: 3.20
[    1.858881] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.859055] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.863933] scsi 1:0:1:0: CD-ROM            SONY     CD-RW  CRX215E1  SYS2 PQ: 0 ANSI: 5
[    1.913816] sr1: scsi3-mmc drive: 63x/40x writer cd/rw xa/form2 cdda tray
[    1.914098] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    1.914247] sr 1:0:1:0: Attached scsi generic sg2 type 5
[    1.914336] Freeing unused kernel memory: 540k freed
[    1.916441] Write protecting the kernel text: 4580k
[    1.916538] Write protecting the kernel read-only data: 1840k
[    2.144118] usb 4-2: new full speed USB device using uhci_hcd and address 2
[    2.329585] usb 4-2: configuration #1 chosen from 1 choice
[    2.340298] hub 4-2:1.0: USB hub found
[    2.347072] hub 4-2:1.0: 7 ports detected
[    2.511316] Linux agpgart interface v0.103
[    2.578978] agpgart-amdk7 0000:00:00.0: AMD Irongate chipset
[    2.656917] Floppy drive(s): fd0 is 1.44M
[    2.772349] <6>8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    2.778436] FDC 0 is a post-1991 82077
[    2.803611] agpgart-amdk7 0000:00:00.0: AGP aperture is 64M @ 0xe8000000
[    2.804501] 8139cp 0000:00:09.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    2.861306] usb 4-2.1: new low speed USB device using uhci_hcd and address 3
[    2.937701] 8139too Fast Ethernet driver 0.9.28
[    2.937854] 8139too 0000:00:09.0: PCI INT A -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    2.939980] eth0: RealTek RTL8139 at 0xd800, 00:00:21:ee:06:c2, IRQ 11
[    3.079589] usb 4-2.1: configuration #1 chosen from 1 choice
[    3.108328] usbcore: registered new interface driver hiddev
[    3.125336] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:0b.1/usb4/4-2/4-2.1/4-2.1:1.0/input/input5
[    3.125655] generic-usb 0003:045E:0040.0001: input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:0b.1-2.1/input0
[    3.125722] usbcore: registered new interface driver usbhid
[    3.125733] usbhid: v2.6:USB HID core driver
[    3.177288] usb 4-2.6: new full speed USB device using uhci_hcd and address 4
[    3.392401] usb 4-2.6: configuration #1 chosen from 1 choice
[    4.028161] PM: Starting manual resume from disk
[    4.028180] PM: Resume from partition 8:5
[    4.028186] PM: Checking hibernation image.
[    4.028591] PM: Resume from disk failed.
[    4.074702] kjournald starting.  Commit interval 5 seconds
[    4.074751] EXT3-fs: mounted filesystem with writeback data mode.
[    5.082294] type=1505 audit(1268258299.268:2): operation="profile_load" pid=329 name=/usr/share/gdm/guest-session/Xsession
[    5.123842] type=1505 audit(1268258299.308:3): operation="profile_load" pid=330 name=/sbin/dhclient3
[    5.124887] type=1505 audit(1268258299.312:4): operation="profile_load" pid=330 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    5.125403] type=1505 audit(1268258299.312:5): operation="profile_load" pid=330 name=/usr/lib/connman/scripts/dhclient-script
[    5.166490] type=1505 audit(1268258299.352:6): operation="profile_load" pid=331 name=/usr/bin/evince
[    5.184602] type=1505 audit(1268258299.372:7): operation="profile_load" pid=331 name=/usr/bin/evince-previewer
[    5.195122] type=1505 audit(1268258299.380:8): operation="profile_load" pid=331 name=/usr/bin/evince-thumbnailer
[    5.219594] type=1505 audit(1268258299.404:9): operation="profile_load" pid=333 name=/usr/bin/freshclam
[    5.234538] type=1505 audit(1268258299.420:10): operation="profile_load" pid=334 name=/usr/lib/cups/backend/cups-pdf
[   17.207911] Adding 730916k swap on /dev/sda5.  Priority:-1 extents:1 across:730916k 
[   17.377015] EXT3 FS on sda1, internal journal
[   17.731081] udev: starting version 147
[   19.394917] lp: driver loaded but no devices found
[   19.445907] cfg80211: Calling CRDA to update world regulatory domain
[   19.959734] Linux video capture interface: v2.00
[   19.989382] shpchp 0000:00:01.0: HPC vendor_id 1022 device_id 7007 ss_vid 0 ss_did 0
[   19.989402] shpchp 0000:00:01.0: Cannot reserve MMIO region
[   19.989531] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   19.992417] parport_pc 00:0a: reported by Plug and Play ACPI
[   19.992484] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   20.077446] lp0: using parport0 (interrupt-driven).
[   20.181708] cfg80211: World regulatory domain updated:
[   20.181725] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   20.181736] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.181745] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.181754] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.181762] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.181771] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.308992] ACPI: I/O resource amd756_smbus [0x50e0-0x50ef] conflicts with ACPI region SBS_ [0x50e0-0x50e8]
[   20.309010] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   20.428395] gspca: main v2.6.0 registered
[   20.444847] usb 1-1: reset high speed USB device using ehci_hcd and address 2
[   20.466837] ppdev: user-space parallel port driver
[   20.516572] ip_tables: (C) 2000-2006 Netfilter Core Team
[   20.538292] gspca: probing 093a:2460
[   20.551739] pac207: Pixart Sensor ID 0x27 Chips ID 0x09
[   20.551752] pac207: Pixart PAC207BCA Image Processor and Control Chip detected (vid/pid 0x093A:0x2460)
[   20.584482] gspca: probe ok
[   20.584564] usbcore: registered new interface driver pac207
[   20.584574] pac207: registered
[   21.060700] bttv: driver version 0.9.18 loaded
[   21.060713] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   21.060882] bttv: Bt8xx card found (0).
[   21.061432] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 9
[   21.061444] PCI: setting IRQ 9 as level-triggered
[   21.061458] bttv 0000:00:0a.0: PCI INT A -> Link[LNKC] -> GSI 9 (level, low) -> IRQ 9
[   21.061483] bttv0: Bt878 (rev 2) at 0000:00:0a.0, irq: 9, latency: 64, mmio: 0xefdfe000
[   21.081722] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb
[   21.081736] bttv0: using: Hauppauge (bt878) [card=10,autodetected]
[   21.081746] IRQ 9/bttv0: IRQF_DISABLED is not guaranteed on shared IRQs
[   21.081825] bttv0: gpio: en=00000000, out=00000000 in=00fffffb [init]
[   21.084321] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]
[   21.117142] tveeprom 0-0050: Hauppauge model 61205, rev BM  , serial# 3033755
[   21.117153] tveeprom 0-0050: tuner model is Philips FI1246 MK2 (idx 11, type 1)
[   21.117165] tveeprom 0-0050: TV standards PAL(I) (eeprom 0x10)
[   21.117174] tveeprom 0-0050: audio processor is None (idx 0)
[   21.117181] tveeprom 0-0050: has no radio
[   21.117187] bttv0: Hauppauge eeprom indicates model#61205
[   21.117194] bttv0: tuner type=1
[   21.338594] phy0: Selected rate control algorithm 'minstrel'
[   21.340908] zd1211rw 1-1:1.0: phy0
[   21.341049] usbcore: registered new interface driver zd1211rw
[   21.813429] bttv0: audio absent, no audio device found!
[   21.879273] tuner 0-0061: chip found @ 0xc2 (bt878 #0 [sw])
[   22.439495] tuner-simple 0-0061: creating new instance
[   22.439512] tuner-simple 0-0061: type set to 1 (Philips PAL_I (FI1246 and compatibles))
[   22.440405] bttv0: registered device video1
[   22.440500] bttv0: registered device vbi0
[   22.440547] bttv0: PLL: 28636363 => 35468950 .. ok
[   22.476847] Bt87x 0000:00:0a.1: PCI INT A -> Link[LNKC] -> GSI 9 (level, low) -> IRQ 9
[   22.477923] bt87x0: Using board 1, analog, digital (rate 32000 Hz)
[   22.484819] ENS1371 0000:00:0c.0: PCI INT A -> Link[LNKA] -> GSI 10 (level, low) -> IRQ 10
[   24.471527] eth0: link down
[   24.497530] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   24.589623] usb 1-1: firmware: requesting zd1211/zd1211b_ub
[   24.774647] usb 1-1: firmware: requesting zd1211/zd1211b_uphr
[   25.192228] zd1211rw 1-1:1.0: firmware version 4725
[   25.242243] zd1211rw 1-1:1.0: zd1211b chip 050d:705c v4810 high 00-17-3f AL2230_RF pa0 g--NS
[   25.245384] cfg80211: Calling CRDA for country: US
[   25.261080] cfg80211: Regulatory domain changed to country: US
[   25.261098] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   25.261110] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   25.261119] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   25.261128] 	(5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.261137] 	(5490000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.261145] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   25.285666] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.375140] __ratelimit: 6 callbacks suppressed
[   25.375154] type=1505 audit(1268258319.560:13): operation="profile_replace" pid=902 name=/usr/share/gdm/guest-session/Xsession
[   25.395172] type=1505 audit(1268258319.580:14): operation="profile_replace" pid=903 name=/sbin/dhclient3
[   25.412383] type=1505 audit(1268258319.600:15): operation="profile_replace" pid=903 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   25.413014] type=1505 audit(1268258319.600:16): operation="profile_replace" pid=903 name=/usr/lib/connman/scripts/dhclient-script
[   25.459872] type=1505 audit(1268258319.644:17): operation="profile_replace" pid=904 name=/usr/bin/evince
[   25.510934] type=1505 audit(1268258319.696:18): operation="profile_replace" pid=904 name=/usr/bin/evince-previewer
[   25.541338] type=1505 audit(1268258319.728:19): operation="profile_replace" pid=904 name=/usr/bin/evince-thumbnailer
[   25.581564] type=1505 audit(1268258319.768:20): operation="profile_replace" pid=906 name=/usr/bin/freshclam
[   25.615144] type=1505 audit(1268258319.800:21): operation="profile_replace" pid=907 name=/usr/lib/cups/backend/cups-pdf
[   25.632654] type=1505 audit(1268258319.820:22): operation="profile_replace" pid=907 name=/usr/sbin/cupsd
[   28.698380] mtrr: no MTRR for e0000000,2000000 found
[   29.120569] [drm] Initialized drm 1.1.0 20060810
[   29.270797] pci 0000:01:05.0: PCI INT A -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[   29.271848] [drm] Initialized r128 2.5.0 20030725 for 0000:01:05.0 on minor 0
[   29.298480] agpgart-amdk7 0000:00:00.0: AGP 1.0 bridge
[   29.298531] agpgart-amdk7 0000:00:00.0: putting AGP V2 device into 1x mode
[   29.298594] pci 0000:01:05.0: putting AGP V2 device into 1x mode
[   43.924141] glxinfo:1640 freeing invalid memtype e8102000-e8106000
[   43.924170] glxinfo:1640 freeing invalid memtype e8106000-e810a000
[   43.924189] glxinfo:1640 freeing invalid memtype e810a000-e810e000
[   43.924206] glxinfo:1640 freeing invalid memtype e810e000-e8112000
[   43.924223] glxinfo:1640 freeing invalid memtype e8112000-e8116000
[   43.924240] glxinfo:1640 freeing invalid memtype e8116000-e811a000
[   43.924257] glxinfo:1640 freeing invalid memtype e811a000-e811e000
[   43.924273] glxinfo:1640 freeing invalid memtype e811e000-e8122000
[   43.924290] glxinfo:1640 freeing invalid memtype e8122000-e8126000
[   43.924306] glxinfo:1640 freeing invalid memtype e8126000-e812a000
[   43.924323] glxinfo:1640 freeing invalid memtype e812a000-e812e000
[   43.924339] glxinfo:1640 freeing invalid memtype e812e000-e8132000
[   43.924356] glxinfo:1640 freeing invalid memtype e8132000-e8136000
[   43.924373] glxinfo:1640 freeing invalid memtype e8136000-e813a000
[   43.924389] glxinfo:1640 freeing invalid memtype e813a000-e813e000
[   43.924406] glxinfo:1640 freeing invalid memtype e813e000-e8142000
[   43.924422] glxinfo:1640 freeing invalid memtype e8142000-e8146000
[   43.924439] glxinfo:1640 freeing invalid memtype e8146000-e814a000
[   43.924455] glxinfo:1640 freeing invalid memtype e814a000-e814e000
[   43.924472] glxinfo:1640 freeing invalid memtype e814e000-e8152000
[   43.924489] glxinfo:1640 freeing invalid memtype e8152000-e8156000
[   43.924505] glxinfo:1640 freeing invalid memtype e8156000-e815a000
[   43.924522] glxinfo:1640 freeing invalid memtype e815a000-e815e000
[   43.924539] glxinfo:1640 freeing invalid memtype e815e000-e8162000
[   43.924555] glxinfo:1640 freeing invalid memtype e8162000-e8166000
[   43.924572] glxinfo:1640 freeing invalid memtype e8166000-e816a000
[   43.924588] glxinfo:1640 freeing invalid memtype e816a000-e816e000
[   43.924605] glxinfo:1640 freeing invalid memtype e816e000-e8172000
[   43.924621] glxinfo:1640 freeing invalid memtype e8172000-e8176000
[   43.924638] glxinfo:1640 freeing invalid memtype e8176000-e817a000
[   43.924654] glxinfo:1640 freeing invalid memtype e817a000-e817e000
[   43.924671] glxinfo:1640 freeing invalid memtype e817e000-e8182000
[   43.924687] glxinfo:1640 freeing invalid memtype e8182000-e8186000
[   43.924704] glxinfo:1640 freeing invalid memtype e8186000-e818a000
[   43.924721] glxinfo:1640 freeing invalid memtype e818a000-e818e000
[   43.924737] glxinfo:1640 freeing invalid memtype e818e000-e8192000
[   43.924754] glxinfo:1640 freeing invalid memtype e8192000-e8196000
[   43.924770] glxinfo:1640 freeing invalid memtype e8196000-e819a000
[   43.924787] glxinfo:1640 freeing invalid memtype e819a000-e819e000
[   43.924804] glxinfo:1640 freeing invalid memtype e819e000-e81a2000
[   43.924820] glxinfo:1640 freeing invalid memtype e81a2000-e81a6000
[   43.924837] glxinfo:1640 freeing invalid memtype e81a6000-e81aa000
[   43.924853] glxinfo:1640 freeing invalid memtype e81aa000-e81ae000
[   43.924870] glxinfo:1640 freeing invalid memtype e81ae000-e81b2000
[   43.924886] glxinfo:1640 freeing invalid memtype e81b2000-e81b6000
[   43.924903] glxinfo:1640 freeing invalid memtype e81b6000-e81ba000
[   43.924920] glxinfo:1640 freeing invalid memtype e81ba000-e81be000
[   43.924937] glxinfo:1640 freeing invalid memtype e81be000-e81c2000
[   43.924954] glxinfo:1640 freeing invalid memtype e81c2000-e81c6000
[   43.924970] glxinfo:1640 freeing invalid memtype e81c6000-e81ca000
[   43.924987] glxinfo:1640 freeing invalid memtype e81ca000-e81ce000
[   43.925004] glxinfo:1640 freeing invalid memtype e81ce000-e81d2000
[   43.925020] glxinfo:1640 freeing invalid memtype e81d2000-e81d6000
[   43.925036] glxinfo:1640 freeing invalid memtype e81d6000-e81da000
[   43.925053] glxinfo:1640 freeing invalid memtype e81da000-e81de000
[   43.925070] glxinfo:1640 freeing invalid memtype e81de000-e81e2000
[   43.925086] glxinfo:1640 freeing invalid memtype e81e2000-e81e6000
[   43.925103] glxinfo:1640 freeing invalid memtype e81e6000-e81ea000
[   43.925119] glxinfo:1640 freeing invalid memtype e81ea000-e81ee000
[   43.925136] glxinfo:1640 freeing invalid memtype e81ee000-e81f2000
[   43.925152] glxinfo:1640 freeing invalid memtype e81f2000-e81f6000
[   43.925169] glxinfo:1640 freeing invalid memtype e81f6000-e81fa000
[   43.925186] glxinfo:1640 freeing invalid memtype e81fa000-e81fe000
[   43.925203] glxinfo:1640 freeing invalid memtype e81fe000-e8202000
[   43.925219] glxinfo:1640 freeing invalid memtype e8202000-e8206000
[   43.925235] glxinfo:1640 freeing invalid memtype e8206000-e820a000
[   43.925252] glxinfo:1640 freeing invalid memtype e820a000-e820e000
[   43.925269] glxinfo:1640 freeing invalid memtype e820e000-e8212000
[   43.925285] glxinfo:1640 freeing invalid memtype e8212000-e8216000
[   43.925302] glxinfo:1640 freeing invalid memtype e8216000-e821a000
[   43.925318] glxinfo:1640 freeing invalid memtype e821a000-e821e000
[   43.925342] glxinfo:1640 freeing invalid memtype e821e000-e8222000
[   43.925359] glxinfo:1640 freeing invalid memtype e8222000-e8226000
[   43.925375] glxinfo:1640 freeing invalid memtype e8226000-e822a000
[   43.925392] glxinfo:1640 freeing invalid memtype e822a000-e822e000
[   43.925408] glxinfo:1640 freeing invalid memtype e822e000-e8232000
[   43.925425] glxinfo:1640 freeing invalid memtype e8232000-e8236000
[   43.925441] glxinfo:1640 freeing invalid memtype e8236000-e823a000
[   43.925458] glxinfo:1640 freeing invalid memtype e823a000-e823e000
[   43.925475] glxinfo:1640 freeing invalid memtype e823e000-e8242000
[   43.925491] glxinfo:1640 freeing invalid memtype e8242000-e8246000
[   43.925507] glxinfo:1640 freeing invalid memtype e8246000-e824a000
[   43.925524] glxinfo:1640 freeing invalid memtype e824a000-e824e000
[   43.925541] glxinfo:1640 freeing invalid memtype e824e000-e8252000
[   43.925557] glxinfo:1640 freeing invalid memtype e8252000-e8256000
[   43.925574] glxinfo:1640 freeing invalid memtype e8256000-e825a000
[   43.925590] glxinfo:1640 freeing invalid memtype e825a000-e825e000
[   43.925607] glxinfo:1640 freeing invalid memtype e825e000-e8262000
[   43.925623] glxinfo:1640 freeing invalid memtype e8262000-e8266000
[   43.925640] glxinfo:1640 freeing invalid memtype e8266000-e826a000
[   43.925656] glxinfo:1640 freeing invalid memtype e826a000-e826e000
[   43.925673] glxinfo:1640 freeing invalid memtype e826e000-e8272000
[   43.925689] glxinfo:1640 freeing invalid memtype e8272000-e8276000
[   43.925706] glxinfo:1640 freeing invalid memtype e8276000-e827a000
[   43.925722] glxinfo:1640 freeing invalid memtype e827a000-e827e000
[   43.925739] glxinfo:1640 freeing invalid memtype e827e000-e8282000
[   43.925755] glxinfo:1640 freeing invalid memtype e8282000-e8286000
[   43.925772] glxinfo:1640 freeing invalid memtype e8286000-e828a000
[   43.925789] glxinfo:1640 freeing invalid memtype e828a000-e828e000
[   43.925805] glxinfo:1640 freeing invalid memtype e828e000-e8292000
[   43.925822] glxinfo:1640 freeing invalid memtype e8292000-e8296000
[   43.925838] glxinfo:1640 freeing invalid memtype e8296000-e829a000
[   43.925855] glxinfo:1640 freeing invalid memtype e829a000-e829e000
[   43.925871] glxinfo:1640 freeing invalid memtype e829e000-e82a2000
[   43.925888] glxinfo:1640 freeing invalid memtype e82a2000-e82a6000
[   43.925904] glxinfo:1640 freeing invalid memtype e82a6000-e82aa000
[   43.925921] glxinfo:1640 freeing invalid memtype e82aa000-e82ae000
[   43.925938] glxinfo:1640 freeing invalid memtype e82ae000-e82b2000
[   43.925954] glxinfo:1640 freeing invalid memtype e82b2000-e82b6000
[   43.925970] glxinfo:1640 freeing invalid memtype e82b6000-e82ba000
[   43.925987] glxinfo:1640 freeing invalid memtype e82ba000-e82be000
[   43.926004] glxinfo:1640 freeing invalid memtype e82be000-e82c2000
[   43.926020] glxinfo:1640 freeing invalid memtype e82c2000-e82c6000
[   43.926037] glxinfo:1640 freeing invalid memtype e82c6000-e82ca000
[   43.926053] glxinfo:1640 freeing invalid memtype e82ca000-e82ce000
[   43.926070] glxinfo:1640 freeing invalid memtype e82ce000-e82d2000
[   43.926086] glxinfo:1640 freeing invalid memtype e82d2000-e82d6000
[   43.926102] glxinfo:1640 freeing invalid memtype e82d6000-e82da000
[   43.926119] glxinfo:1640 freeing invalid memtype e82da000-e82de000
[   43.926136] glxinfo:1640 freeing invalid memtype e82de000-e82e2000
[   43.926152] glxinfo:1640 freeing invalid memtype e82e2000-e82e6000
[   43.926169] glxinfo:1640 freeing invalid memtype e82e6000-e82ea000
[   43.926185] glxinfo:1640 freeing invalid memtype e82ea000-e82ee000
[   43.926202] glxinfo:1640 freeing invalid memtype e82ee000-e82f2000
[   43.926218] glxinfo:1640 freeing invalid memtype e82f2000-e82f6000
[   43.926235] glxinfo:1640 freeing invalid memtype e82f6000-e82fa000
[   43.926251] glxinfo:1640 freeing invalid memtype e82fa000-e82fe000
[   43.926267] glxinfo:1640 freeing invalid memtype e82fe000-e8302000
[  233.465367] wlan0: authenticate with AP 00:11:50:85:0d:86
[  233.533648] wlan0: authenticated
[  233.533662] wlan0: associate with AP 00:11:50:85:0d:86
[  233.539885] wlan0: RX AssocResp from 00:11:50:85:0d:86 (capab=0x471 status=0 aid=1)
[  233.539901] wlan0: associated
[  233.542039] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  238.773577] padlock: VIA PadLock not detected.
[  243.988037] wlan0: no IPv6 routers present
[ 2123.198014] usb 4-2.3: new full speed USB device using uhci_hcd and address 5
[ 2123.300016] usb 4-2.3: not running at top speed; connect to a high speed hub
[ 2123.328394] usb 4-2.3: configuration #1 chosen from 1 choice
[ 2124.327597] Initializing USB Mass Storage driver...
[ 2124.331084] scsi2 : SCSI emulation for USB Mass Storage devices
[ 2124.331804] usbcore: registered new interface driver usb-storage
[ 2124.331816] USB Mass Storage support registered.
[ 2124.333283] usb-storage: device found at 5
[ 2124.333291] usb-storage: waiting for device to settle before scanning
[ 2124.532838] usblp0: USB Bidirectional printer dev 5 if 1 alt 0 proto 2 vid 0x04B8 pid 0x0851
[ 2124.532928] usbcore: registered new interface driver usblp
[ 2126.131957] usb 4-2.3: usbfs: interface 1 claimed by usblp while 'usb' sets config #1
[ 2129.333527] usb-storage: device scan complete
[ 2129.336755] scsi 2:0:0:0: Direct-Access     EPSON    Stylus Storage   1.00 PQ: 0 ANSI: 2
[ 2129.338385] sd 2:0:0:0: Attached scsi generic sg3 type 0
[ 2129.370064] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[ 2145.261551] usblp0: removed
[ 2145.261628] usb 4-2.3: usbfs: interface 2 claimed by usb-storage while 'xsane' sets config #1
[ 2145.279586] usblp0: USB Bidirectional printer dev 5 if 1 alt 0 proto 2 vid 0x04B8 pid 0x0851
[ 2153.232597] usblp0: removed
[ 2153.232676] usb 4-2.3: usbfs: interface 2 claimed by usb-storage while 'xsane' sets config #1
[ 2190.124273] usblp0: USB Bidirectional printer dev 5 if 1 alt 0 proto 2 vid 0x04B8 pid 0x0851
laura@laura-desktop:~$ 


Many thanks and regards to all
Tim

---

### Post by chuggly on 2010-03-10
Where did the smilies come from I didn't put them there?

Tim

---

### Post by ajgreeny on 2010-03-10
Those smilies can be a bit of a pain, I agree, but you can disable them from your post by clicking the Disable smilies box in the Additional Options section below the entry box, just below the first of the two "Submit reply" buttons that are available.

I think it's colons (:) that cause them to appear, and I assume it's asci  entries equivalent to smilies that are automatically changed to the appropriate smiley.

EDIT: Yes it does, my (:) in the example has just turned into a smiley, as I did not click on the disable box, and shows that a colon followed by a ) without a space between will do exactly that.

Sorry to say after that I have no idea about your main scanner problem, other than to suggest that there is not enough power getting to the scanner through the hub; maybe a powered hub would help get more power to the machine.

---

