---
title: "Partition/mount problem"
date: 2008-10-07
forum: General Help
---

### Post by niallgrant on 2008-10-07
Hi guys, 

I am new to the Ubuntu forums- and I have looked all over for a solution to this problem before posting. 

Basically I was working away one day, shut it down, it stalled at shut down so I pressed and held the power button to switch the machine off. I then installed a new partition on the same hard disk, which I am using now. The only thing I want is file recovery from the partition (115.1GB) then I will clean the whole disk and start fresh. 

OK. So, when I go to places (GNOME) I can see the 115.1GB media but when i try to access it I get:

> Cannot mount volume.
Unable to mount the volume.
mount: wrong fs type, bad option, bad superblock on /dev/sda1, 
missing code page or helper program or other error. In some cases useful info is found in syslog -try dmesg|tail or so


dmesg|tail outputs

> niall@niall-desktop:~$ dmesg|tail
[ 1162.751771] eth0: PHY reset until link up.
[ 1172.778808] eth0: PHY reset until link up.
[ 1179.480549] EXT2-fs error (device sda1): ext2_check_descriptors: Block bitmap for group 0 not in group (block 2553887680)!
[ 1179.480564] EXT2-fs: group descriptors corrupted!
[ 1182.806851] eth0: PHY reset until link up.
[ 1192.834888] eth0: PHY reset until link up.
[ 1201.555181] EXT2-fs error (device sda1): ext2_check_descriptors: Block bitmap for group 0 not in group (block 2553887680)!
[ 1201.555196] EXT2-fs: group descriptors corrupted!
[ 1202.867726] eth0: PHY reset until link up.
[ 1212.894969] eth0: PHY reset until link up.
 
 
For reference dmesg outputs:

> [   80.215529] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   80.216111] TCP: Hash tables configured (established 131072 bind 65536)
[   80.216116] TCP reno registered
[   80.226474] checking if image is initramfs... it is
[   80.916051] Freeing initrd memory: 7703k freed
[   80.917244] audit: initializing netlink socket (disabled)
[   80.917264] audit(1223411660.540:1): initialized
[   80.917588] highmem bounce pool size: 64 pages
[   80.920472] VFS: Disk quotas dquot_6.5.1
[   80.920578] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   80.920749] io scheduler noop registered
[   80.920751] io scheduler anticipatory registered
[   80.920754] io scheduler deadline registered
[   80.920767] io scheduler cfq registered (default)
[   80.974028] Boot video device is 0000:01:00.0
[   80.974181] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   80.974235] assign_interrupt_mode Found MSI capability
[   80.974289] Allocate Port Service[0000:00:01.0:pcie00]
[   80.974421] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   80.974500] assign_interrupt_mode Found MSI capability
[   80.974549] Allocate Port Service[0000:00:06.0:pcie00]
[   80.974692] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   80.974771] assign_interrupt_mode Found MSI capability
[   80.974820] Allocate Port Service[0000:00:07.0:pcie00]
[   80.975214] isapnp: Scanning for PnP cards...
[   81.326844] isapnp: No Plug & Play device found
[   81.369858] Real Time Clock Driver v1.12ac
[   81.370003] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   81.370141] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   81.371119] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   81.372307] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   81.372400] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   81.372546] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   81.372549] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[   81.372694] serio: i8042 KBD port at 0x60,0x64 irq 1
[   81.390893] mice: PS/2 mouse device common for all mice
[   81.391080] EISA: Probing bus 0 at eisa.0
[   81.391089] Cannot allocate resource for EISA slot 1
[   81.391100] Cannot allocate resource for EISA slot 4
[   81.391119] EISA: Detected 0 cards.
[   81.391123] cpuidle: using governor ladder
[   81.391125] cpuidle: using governor menu
[   81.391224] NET: Registered protocol family 1
[   81.391258] Using IPI No-Shortcut mode
[   81.391300] registered taskstats version 1
[   81.391411]   Magic number: 12:700:598
[   81.391445]   hash matches device ptyd2
[   81.391500] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   81.391502] EDD information not available.
[   81.391893] Freeing unused kernel memory: 368k freed
[   81.433782] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   82.662046] fuse init (API version 7.9)
[   82.682347] ACPI: Fan [FAN] (on)
[   82.689884] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   82.689904] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   82.691595] ACPI: Thermal Zone [THRM] (53 C)
[   83.017621] SCSI subsystem initialized
[   83.072140] libata version 3.00 loaded.
[   83.074457] ACPI: PCI Interrupt 0000:00:02.5[A] -> GSI 16 (level, low) -> IRQ 16
[   83.074528] ACPI: PCI interrupt for device 0000:00:02.5 disabled
[   83.074567] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 17 (level, low) -> IRQ 17
[   83.074596] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   83.074610] ACPI: PCI interrupt for device 0000:00:05.0 disabled
[   83.136027] pata_sis 0000:00:02.5: version 0.5.2
[   83.136069] ACPI: PCI Interrupt 0000:00:02.5[A] -> GSI 16 (level, low) -> IRQ 16
[   83.143506] scsi0 : pata_sis
[   83.145360] scsi1 : pata_sis
[   83.145947] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x4000 irq 14
[   83.145951] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x4008 irq 15
[   83.146152] usbcore: registered new interface driver usbfs
[   83.146183] usbcore: registered new interface driver hub
[   83.146221] usbcore: registered new device driver usb
[   83.158472] USB Universal Host Controller Interface driver v3.0
[   83.159778] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   83.252757] Floppy drive(s): fd0 is 1.44M
[   83.277486] FDC 0 is a post-1991 82077
[   83.474230] ata1.00: ATAPI: Optiarc DVD RW AD-5170A, 1.11, max UDMA/66
[   83.514207] ata1.01: ATA-7: ST3120814A, 3.AAJ, max UDMA/100
[   83.514211] ata1.01: 234441648 sectors, multi 16: LBA48 
[   83.686165] ata1.00: configured for UDMA/66
[   83.731193] ata1.01: configured for UDMA/100
[   83.731252] ata2: port disabled. ignoring.
[   83.732177] scsi 0:0:0:0: CD-ROM            Optiarc  DVD RW AD-5170A  1.11 PQ: 0 ANSI: 5
[   83.732338] scsi 0:0:1:0: Direct-Access     ATA      ST3120814A       3.AA PQ: 0 ANSI: 5
[   83.732474] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 18
[   83.732498] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   83.732503] ohci_hcd 0000:00:03.0: OHCI Host Controller
[   83.732830] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[   83.732852] ohci_hcd 0000:00:03.0: irq 18, io mem 0xfdfff000
[   83.792010] usb usb1: configuration #1 chosen from 1 choice
[   83.792049] hub 1-0:1.0: USB hub found
[   83.792059] hub 1-0:1.0: 4 ports detected
[   83.893918] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 19
[   83.893941] PCI: Setting latency timer of device 0000:00:03.1 to 64
[   83.893946] ohci_hcd 0000:00:03.1: OHCI Host Controller
[   83.893985] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[   83.894007] ohci_hcd 0000:00:03.1: irq 19, io mem 0xfdffe000
[   83.950900] usb usb2: configuration #1 chosen from 1 choice
[   83.950933] hub 2-0:1.0: USB hub found
[   83.950943] hub 2-0:1.0: 4 ports detected
[   84.054086] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 16 (level, low) -> IRQ 16
[   84.054110] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   84.054115] uhci_hcd 0000:00:09.0: UHCI Host Controller
[   84.054169] uhci_hcd 0000:00:09.0: new USB bus registered, assigned bus number 3
[   84.054205] uhci_hcd 0000:00:09.0: irq 16, io base 0x0000f500
[   84.054380] usb usb3: configuration #1 chosen from 1 choice
[   84.054415] hub 3-0:1.0: USB hub found
[   84.054423] hub 3-0:1.0: 2 ports detected
[   84.156839] ACPI: PCI Interrupt 0000:00:09.1[B] -> GSI 17 (level, low) -> IRQ 17
[   84.156858] PCI: Setting latency timer of device 0000:00:09.1 to 64
[   84.156863] uhci_hcd 0000:00:09.1: UHCI Host Controller
[   84.156896] uhci_hcd 0000:00:09.1: new USB bus registered, assigned bus number 4
[   84.156927] uhci_hcd 0000:00:09.1: irq 17, io base 0x0000f400
[   84.157068] usb usb4: configuration #1 chosen from 1 choice
[   84.157100] hub 4-0:1.0: USB hub found
[   84.157108] hub 4-0:1.0: 2 ports detected
[   84.196682] usb 1-4: new low speed USB device using ohci_hcd and address 2
[   84.261318] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level, low) -> IRQ 20
[   84.261338] PCI: Setting latency timer of device 0000:00:03.3 to 64
[   84.261343] ehci_hcd 0000:00:03.3: EHCI Host Controller
[   84.261396] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 5
[   84.261444] PCI: cache line size of 128 is not supported by device 0000:00:03.3
[   84.261457] ehci_hcd 0000:00:03.3: irq 20, io mem 0xfdffd000
[   84.273293] Driver 'sr' needs updating - please use bus_type methods
[   84.274591] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[   84.274596] Uniform CD-ROM driver Revision: 3.20
[   84.274652] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   84.276457] Driver 'sd' needs updating - please use bus_type methods
[   84.276588] sd 0:0:1:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   84.276607] sd 0:0:1:0: [sda] Write Protect is off
[   84.276611] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
[   84.276638] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   84.276712] sd 0:0:1:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   84.276727] sd 0:0:1:0: [sda] Write Protect is off
[   84.276730] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
[   84.276761] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   84.276765]  sda:<5>sr 0:0:0:0: Attached scsi generic sg0 type 5
[   84.292810] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   84.294761]  sda1 sda2 < sda5 sda6 sda7 >
[   84.343149] sd 0:0:1:0: [sda] Attached SCSI disk
[   84.385603] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   84.385799] usb usb5: configuration #1 chosen from 1 choice
[   84.385836] hub 5-0:1.0: USB hub found
[   84.385845] hub 5-0:1.0: 8 ports detected
[   84.491017] ACPI: PCI Interrupt 0000:00:09.2[C] -> GSI 18 (level, low) -> IRQ 21
[   84.491041] PCI: Setting latency timer of device 0000:00:09.2 to 64
[   84.491046] ehci_hcd 0000:00:09.2: EHCI Host Controller
[   84.491082] ehci_hcd 0000:00:09.2: new USB bus registered, assigned bus number 6
[   84.491137] ehci_hcd 0000:00:09.2: irq 21, io mem 0xfdffb000
[   84.501554] ehci_hcd 0000:00:09.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   84.501691] usb usb6: configuration #1 chosen from 1 choice
[   84.501724] hub 6-0:1.0: USB hub found
[   84.501733] hub 6-0:1.0: 4 ports detected
[   84.605765] sata_sis 0000:00:05.0: version 1.0
[   84.605786] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 17 (level, low) -> IRQ 17
[   84.605796] sata_sis 0000:00:05.0: Detected SiS 1183/966/966L/968/680 controller in PATA mode
[   84.606488] scsi2 : sata_sis
[   84.606572] scsi3 : sata_sis
[   84.607092] ata3: PATA max UDMA/133 cmd 0xfb00 ctl 0xfa00 bmdma 0xf700 irq 17
[   84.607096] ata4: PATA max UDMA/133 cmd 0xf900 ctl 0xf800 bmdma 0xf708 irq 17
[   84.764266] Attempting manual resume
[   84.764271] swsusp: Resume From Partition 8:7
[   84.764273] PM: Checking swsusp image.
[   84.764449] PM: Resume from disk failed.
[   84.780541] EXT3-fs: INFO: recovery required on readonly filesystem.
[   84.780547] EXT3-fs: write access will be enabled during recovery.
[   84.781449] usb 1-4: device not accepting address 2, error -62
[   84.806081] kjournald starting.  Commit interval 5 seconds
[   84.806094] EXT3-fs: recovery complete.
[   84.806360] EXT3-fs: mounted filesystem with ordered data mode.
[   85.901005] usb 6-3: new high speed USB device using ehci_hcd and address 2
[   86.172263] usb 6-3: configuration #1 chosen from 1 choice
[   86.476774] usb 1-4: new low speed USB device using ohci_hcd and address 4
[   86.687093] usb 1-4: configuration #1 chosen from 1 choice
[   89.643544] ata3: port is slow to respond, please be patient (Status 0x80)
[   92.949469] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   93.022410] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   93.242430] parport_pc 00:08: reported by Plug and Play ACPI
[   93.242491] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   93.498885] input: Power Button (FF) as /devices/virtual/input/input3
[   93.538192] ACPI: Power Button (FF) [PWRF]
[   93.538281] input: Power Button (CM) as /devices/virtual/input/input4
[   93.602072] ACPI: Power Button (CM) [PWRB]
[   94.227864] usbcore: registered new interface driver hiddev
[   94.235016] input: PS/2+USB Mouse as /devices/pci0000:00/0000:00:03.0/usb1/1-4/1-4:1.0/input/input5
[   94.281800] input,hidraw0: USB HID v1.00 Mouse [PS/2+USB Mouse] on usb-0000:00:03.0-4
[   94.281828] usbcore: registered new interface driver usbhid
[   94.281834] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   94.620569] ata3: device not ready (errno=-16), forcing hardreset
[   94.649042] phy0: Selected rate control algorithm 'simple'
[   94.742045] usbcore: registered new interface driver rt73usb
[   94.762789] usbcore: registered new interface driver rt2500usb
[   94.955029] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   94.955188] sis190 Gigabit Ethernet driver 1.2 loaded.
[   94.955233] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 22
[   94.955253] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   94.955269] 0000:00:04.0: Read MAC address from EEPROM
[   95.041398] 0000:00:04.0: Broadcom PHY AC131 transceiver at address 1.
[   95.088740] Linux agpgart interface v0.102
[   95.553209] 0000:00:04.0: Using transceiver at address 1 as default.
[   95.585611] 0000:00:04.0: SiS 190 PCI Fast Ethernet adapter at f8856000 (IRQ: 22), 00:30:1b:42:60:06
[   95.585617] eth0: GMII mode.
[   95.585625] eth0: Enabling Auto-negotiation.
[   95.617537] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 21
[   95.940044] intel8x0_measure_ac97_clock: measured 53807 usecs
[   95.940049] intel8x0: clocking to 48000
[   97.058013] lp0: using parport0 (interrupt-driven).
[   97.120150] Adding 248968k swap on /dev/sda7.  Priority:-1 extents:1 across:248968k
[   97.692352] EXT3 FS on sda6, internal journal
[   98.794704] ip_tables: (C) 2000-2006 Netfilter Core Team
[   99.185234] No dock devices found.
[  100.377281] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[  100.377288] apm: disabled - APM is not SMP safe.
[  100.523390] ppdev: user-space parallel port driver
[  100.629419] audit(1223411680.701:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5015 profile="/usr/sbin/cupsd" namespace="default"
[  106.982518] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  106.982528] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  106.982535] Info fld=0x20
[  106.982537] sr 0:0:0:0: [sr0] Add. Sense: No seek complete
[  106.982542] end_request: I/O error, dev sr0, sector 128
[  106.982546] Buffer I/O error on device sr0, logical block 16
[  106.982551] Buffer I/O error on device sr0, logical block 17
[  106.982554] Buffer I/O error on device sr0, logical block 18
[  106.982558] Buffer I/O error on device sr0, logical block 19
[  106.982561] Buffer I/O error on device sr0, logical block 20
[  106.982564] Buffer I/O error on device sr0, logical block 21
[  106.982568] Buffer I/O error on device sr0, logical block 22
[  106.982571] Buffer I/O error on device sr0, logical block 23
[  106.982574] Buffer I/O error on device sr0, logical block 24
[  106.982577] Buffer I/O error on device sr0, logical block 25
[  109.466291] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  109.466297] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  109.466302] Info fld=0x50
[  109.466304] sr 0:0:0:0: [sr0] Add. Sense: No seek complete
[  109.466308] end_request: I/O error, dev sr0, sector 320
[  109.745312] Bluetooth: Core ver 2.11
[  109.745657] NET: Registered protocol family 31
[  109.745661] Bluetooth: HCI device and connection manager initialized
[  109.745666] Bluetooth: HCI socket layer initialized
[  109.768012] Bluetooth: L2CAP ver 2.9
[  109.768020] Bluetooth: L2CAP socket layer initialized
[  109.840266] Bluetooth: RFCOMM socket layer initialized
[  109.840293] Bluetooth: RFCOMM TTY layer initialized
[  109.840295] Bluetooth: RFCOMM ver 1.8
[  111.716535] [drm] Initialized drm 1.1.0 20060810
[  111.725103] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[  111.725115] PCI: Setting latency timer of device 0000:01:00.0 to 64
[  111.725231] [drm] Initialized radeon 1.28.0 20060524 on minor 0
[  113.628664] [drm] Setting GART location based on new memory map
[  113.629294] [drm] Loading R300 Microcode
[  113.629352] [drm] writeback test succeeded in 1 usecs
[  119.803615] eth0: PHY reset until link up.
[  129.830657] eth0: PHY reset until link up.
[  138.126807] NET: Registered protocol family 10
[  138.127221] lo: Disabled Privacy Extensions
[  138.128269] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  138.128807] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  139.859706] eth0: PHY reset until link up.
[  149.332535] UDF-fs: No VRS found
[  149.548647] ISO 9660 Extensions: Microsoft Joliet Level 3
[  149.858423] ISO 9660 Extensions: RRIP_1991A
[  149.887734] eth0: PHY reset until link up.
[  153.627889] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  153.627901] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  153.627913] Info fld=0x2a
[  153.627914] sr 0:0:0:0: [sr0] Add. Sense: No seek complete
[  153.627920] end_request: I/O error, dev sr0, sector 168
[  153.628004] ISOFS: unable to read i-node block
[  157.986587] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  157.986599] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  157.986610] Info fld=0x28
[  157.986612] sr 0:0:0:0: [sr0] Add. Sense: No seek complete
[  157.986617] end_request: I/O error, dev sr0, sector 160
[  157.986723] ISOFS: unable to read i-node block
[  159.915774] eth0: PHY reset until link up.
[  160.419119] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  160.419133] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  160.419144] Info fld=0x2e
[  160.419148] sr 0:0:0:0: [sr0] Add. Sense: No seek complete
[  160.419161] end_request: I/O error, dev sr0, sector 184
[  160.419265] ISOFS: unable to read i-node block
[  169.943810] eth0: PHY reset until link up.
[  179.970857] eth0: PHY reset until link up.
[  189.998896] eth0: PHY reset until link up.
[  200.026937] eth0: PHY reset until link up.
[  210.054978] eth0: PHY reset until link up.
[  220.083016] eth0: PHY reset until link up.
[  230.111057] eth0: PHY reset until link up.
[  240.140094] eth0: PHY reset until link up.
[  250.168138] eth0: PHY reset until link up.
[  258.101402] EXT2-fs error (device sda1): ext2_check_descriptors: Block bitmap for group 0 not in group (block 2553887680)!
[  258.101417] EXT2-fs: group descriptors corrupted!
[  260.195178] eth0: PHY reset until link up.
[  270.224225] eth0: PHY reset until link up.
[  280.252258] eth0: PHY reset until link up.
[  282.516350] EXT2-fs error (device sda1): ext2_check_descriptors: Block bitmap for group 0 not in group (block 2553887680)!
[  282.516363] EXT2-fs: group descriptors corrupted!
[  290.280301] eth0: PHY reset until link up.
[  292.179137] NET: Registered protocol family 17
[  293.341418] wlan0: Initial auth_alg=0
[  293.341429] wlan0: authenticate with AP 00:90:96:67:88:57
[  293.342945] wlan0: RX authentication from 00:90:96:67:88:57 (alg=0 transaction=2 status=0)
[  293.342951] wlan0: authenticated
[  293.342954] wlan0: associate with AP 00:90:96:67:88:57
[  293.345205] wlan0: RX AssocResp from 00:90:96:67:88:57 (capab=0x1 status=0 aid=40)
[  293.345212] wlan0: associated
[  293.348231] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  300.307337] eth0: PHY reset until link up.
[  310.215426] wlan0: no IPv6 routers present
[  310.336373] eth0: PHY reset until link up.
[  320.363418] eth0: PHY reset until link up.
[  330.391486] eth0: PHY reset until link up.
[  340.419496] eth0: PHY reset until link up.
[  350.448535] eth0: PHY reset until link up.
[  360.475577] eth0: PHY reset until link up.
[  370.507616] eth0: PHY reset until link up.
[  380.536679] eth0: PHY reset until link up.
[  390.563707] eth0: PHY reset until link up.
[  400.591735] eth0: PHY reset until link up.
[  410.620775] eth0: PHY reset until link up.
[  414.184038] APIC error on CPU0: 00(40)
[  420.648813] eth0: PHY reset until link up.
[  430.675856] eth0: PHY reset until link up.
[  440.704893] eth0: PHY reset until link up.
[  450.731938] eth0: PHY reset until link up.
[  460.761002] eth0: PHY reset until link up.
[  470.789121] eth0: PHY reset until link up.
[  480.817053] eth0: PHY reset until link up.
[  490.844096] eth0: PHY reset until link up.
[  500.872136] eth0: PHY reset until link up.
[  510.900176] eth0: PHY reset until link up.
[  520.935316] eth0: PHY reset until link up.
[  530.961251] eth0: PHY reset until link up.
[  540.989296] eth0: PHY reset until link up.
[  551.016334] eth0: PHY reset until link up.
[  561.045373] eth0: PHY reset until link up.
[  571.078654] eth0: PHY reset until link up.
[  581.105451] eth0: PHY reset until link up.
[  591.133628] eth0: PHY reset until link up.
[  601.161530] eth0: PHY reset until link up.
[  611.189614] eth0: PHY reset until link up.
[  621.216633] eth0: PHY reset until link up.
[  631.244654] eth0: PHY reset until link up.
[  641.273704] eth0: PHY reset until link up.
[  651.301740] eth0: PHY reset until link up.
[  661.328776] eth0: PHY reset until link up.
[  671.356814] eth0: PHY reset until link up.
[  681.384859] eth0: PHY reset until link up.
[  691.412895] eth0: PHY reset until link up.
[  701.440935] eth0: PHY reset until link up.
[  711.469972] eth0: PHY reset until link up.
[  721.498016] eth0: PHY reset until link up.
[  731.525055] eth0: PHY reset until link up.
[  741.553094] eth0: PHY reset until link up.
[  751.582152] eth0: PHY reset until link up.
[  761.610170] eth0: PHY reset until link up.
[  771.638219] eth0: PHY reset until link up.
[  781.665268] eth0: PHY reset until link up.
[  791.693645] eth0: PHY reset until link up.
[  801.725332] eth0: PHY reset until link up.
[  811.754370] eth0: PHY reset until link up.
[  818.671330] APIC error on CPU0: 40(40)
[  821.781413] eth0: PHY reset until link up.
[  827.932640] APIC error on CPU0: 40(40)
[  831.809453] eth0: PHY reset until link up.
[  841.842490] eth0: PHY reset until link up.
[  851.870527] eth0: PHY reset until link up.
[  861.898579] eth0: PHY reset until link up.
[  871.925611] eth0: PHY reset until link up.
[  881.953653] eth0: PHY reset until link up.
[  891.981692] eth0: PHY reset until link up.
[  902.009920] eth0: PHY reset until link up.
[  912.038771] eth0: PHY reset until link up.
[  922.065819] eth0: PHY reset until link up.
[  932.093852] eth0: PHY reset until link up.
[  942.126892] eth0: PHY reset until link up.
[  952.153931] eth0: PHY reset until link up.
[  960.560619] EXT2-fs error (device sda1): ext2_check_descriptors: Block bitmap for group 0 not in group (block 2553887680)!
[  960.560633] EXT2-fs: group descriptors corrupted!
[  962.181971] eth0: PHY reset until link up.
[  972.211006] eth0: PHY reset until link up.
[  974.926324] EXT2-fs error (device sda1): ext2_check_descriptors: Block bitmap for group 0 not in group (block 2553887680)!
[  974.926342] EXT2-fs: group descriptors corrupted!
[  982.238052] eth0: PHY reset until link up.
[  992.267086] eth0: PHY reset until link up.
[ 1002.294131] eth0: PHY reset until link up.
[ 1008.348570] EXT2-fs error (device sda1): ext2_check_descriptors: Block bitmap for group 0 not in group (block 2553887680)!
[ 1008.348583] EXT2-fs: group descriptors corrupted!
[ 1012.322173] eth0: PHY reset until link up.
[ 1022.351208] eth0: PHY reset until link up.
[ 1030.764716] EXT2-fs error (device sda1): ext2_check_descriptors: Block bitmap for group 0 not in group (block 2553887680)!
[ 1030.764731] EXT2-fs: group descriptors corrupted!
[ 1032.379278] eth0: PHY reset until link up.
[ 1042.407297] eth0: PHY reset until link up.
[ 1052.435327] eth0: PHY reset until link up.
[ 1056.976972] EXT2-fs error (device sda1): ext2_check_descriptors: Block bitmap for group 0 not in group (block 2553887680)!
[ 1056.976985] EXT2-fs: group descriptors corrupted!
[ 1062.467508] eth0: PHY reset until link up.
[ 1072.494412] eth0: PHY reset until link up.
[ 1080.924892] EXT2-fs error (device sda1): ext2_check_descriptors: Block bitmap for group 0 not in group (block 2553887680)!
[ 1080.924906] EXT2-fs: group descriptors corrupted!
[ 1082.522450] eth0: PHY reset until link up.
[ 1092.551486] eth0: PHY reset until link up.
[ 1100.977107] EXT2-fs error (device sda1): ext2_check_descriptors: Block bitmap for group 0 not in group (block 2553887680)!
[ 1100.977123] EXT2-fs: group descriptors corrupted!
[ 1102.578537] eth0: PHY reset until link up.
[ 1108.641108] APIC error on CPU0: 40(40)
[ 1112.606571] eth0: PHY reset until link up.
[ 1122.635611] eth0: PHY reset until link up.
[ 1127.397379] EXT2-fs error (device sda1): ext2_check_descriptors: Block bitmap for group 0 not in group (block 2553887680)!
[ 1127.397393] EXT2-fs: group descriptors corrupted!
[ 1132.667667] eth0: PHY reset until link up.
[ 1142.695847] eth0: PHY reset until link up.
[ 1144.754036] EXT2-fs error (device sda1): ext2_check_descriptors: Block bitmap for group 0 not in group (block 2553887680)!
[ 1144.754051] EXT2-fs: group descriptors corrupted!
[ 1152.722728] eth0: PHY reset until link up.
[ 1162.751771] eth0: PHY reset until link up.
[ 1172.778808] eth0: PHY reset until link up.
[ 1179.480549] EXT2-fs error (device sda1): ext2_check_descriptors: Block bitmap for group 0 not in group (block 2553887680)!
[ 1179.480564] EXT2-fs: group descriptors corrupted!
[ 1182.806851] eth0: PHY reset until link up.
[ 1192.834888] eth0: PHY reset until link up.
[ 1201.555181] EXT2-fs error (device sda1): ext2_check_descriptors: Block bitmap for group 0 not in group (block 2553887680)!
[ 1201.555196] EXT2-fs: group descriptors corrupted!
[ 1202.867726] eth0: PHY reset until link up.
[ 1212.894969] eth0: PHY reset until link up.
[ 1222.923009] eth0: PHY reset until link up.
[ 1232.951048] eth0: PHY reset until link up.
[ 1242.984639] eth0: PHY reset until link up.
[ 1253.011127] eth0: PHY reset until link up.
[ 1263.039167] eth0: PHY reset until link up.
[ 1273.068213] eth0: PHY reset until link up.
[ 1283.095247] eth0: PHY reset until link up.
[ 1293.124284] eth0: PHY reset until link up.
[ 1303.152339] eth0: PHY reset until link up.
[ 1313.179368] eth0: PHY reset until link up.


Hope this is enough information to help...

Thank you.

---

### Post by Patb on 2008-10-07
Niall, I assume you created the new partition without changing the (115.1GB) partition in question. If you tinkered with your partitions after forcing a shutdown and without trying to restart normally, please please don't do that again :). 

Could you please open a terminal and post the output of the following command:
```
sudo fdisk -l
```
That might give useful information to help get you restarted.  

Cheers, Pat.

---

### Post by caljohnsmith on 2008-10-07
Use the fdisk command that Patb gave to find which is your 115 GB partition in question, and then run an fsck on it to try and fix the file system:
```
sudo fsck -y /dev/sdaX
```
And replace sdaX with your 115 GB partition. Please post the output of that command, along with the fdisk command that Patb asked for.

---

### Post by niallgrant on 2008-10-08
thanks guys that seems to have made some good progress.

basically the fsck sda1 worked, cleaned up the partition 

I can now access the 115.1GB media but there is only one folder- 

> lost+found

When i try to access it, it says:

> 
The folder contents could not be displayed
You do not have the permissions necessary to view the contents of "lost+found".


any ideas?

---

### Post by drs305 on 2008-10-08
Since you want to look inside the 'lost+found' folder but we don't know the mountpoint, the easiest way to do this would be to open nautilus with sudo and navigate to the applicable folder:
```
gksudo nautilus
```

---

### Post by niallgrant on 2008-10-08
funny that, did 

> gksudo nautilus

and nothing is in that folder... 

does this look like a file recovery project now??

:(:(

---

### Post by geirha on 2008-10-08
Sounds like that partition has been removed and recreated. If that is the case, you might have luck getting the previous partition back with testdisk. Boot the ubuntu CD, install testdisk with ```
sudo aptitude install testdisk
``` Then see what it finds. You'll find testdisk's documentation at [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by Patb on 2008-10-09
> **niallgrant said:**
> ... and nothing is in that folder... 
does this look like a file recovery project now??
Niall, the "lost+found" folder is a common feature in Linux. It is created by the system and is readable only by root, hence the need to use sudo.  I'm not sure of the details but the idea is that the system will use it to house any "orphan" files it finds if it has nowhere else to put them.  Prof Google will give you lots more details. 

It does look like a recovery project and Geirha's information should be useful. 

Cheers, Pat

---

