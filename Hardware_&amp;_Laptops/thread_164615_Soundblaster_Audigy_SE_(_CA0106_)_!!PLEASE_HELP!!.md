---
title: "Soundblaster Audigy SE ( CA0106 ) !!PLEASE HELP!!"
date: 2006-04-23
forum: Hardware &amp; Laptops
---

### Post by darkwarrior0404 on 2006-04-23
Okay, I have everything done right... *i think* so, i plugged the speakers into the subwoofer (blue) port on the soundcard, and I get sound from there but its really scratchy, BECAUSE if i plug them into the normal green port like its supposed to be, it doesnt give me any sound, but I booted up into windows, and installed drivers, and  plugged it into green port on sound card and have great sound, why wont linux give me any sound other than out the subwoofer port? and why is it so scratchy? my last soundcard only worked on 2.4 kernel and ugh never had any luck, and now its the same thing all over again.. please help:confused:

---

### Post by ragingpenguin on 2006-04-23
I have the 2 cards in my machine:
Audigy gamer (emu10k1)
Onboard Audigy SE (CA0106)

I had been trying to get sound out to headset through CA0106 on dsp1 for skype, with no luck. The Gamer Card works great on dsp

I had been trying to figure out if it was an issue with the alsa module, or alsa support for this particular onboard sound card as I have never been able to get it to work.

Had you any luck with the SE at all on linux?

---

### Post by darkwarrior0404 on 2006-04-23
yeah, if i plug the speakers up into the subwoofer port it gives me sound, but its really scratchy, but thats about all the luck I have had..](*,)

---

### Post by darkwarrior0404 on 2006-04-23
> darkwarrior0404@ubuntu:~$ lspci
0000:00:00.0 Memory controller: nVidia Corporation: Unknown device 005e (rev a2)0000:00:01.0 ISA bridge: nVidia Corporation: Unknown device 0050 (rev a2)
0000:00:01.1 SMBus: nVidia Corporation: Unknown device 0052 (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation: Unknown device 005a (rev a2)
0000:00:02.1 USB Controller: nVidia Corporation: Unknown device 005b (rev a2)
0000:00:06.0 IDE interface: nVidia Corporation: Unknown device 0053 (rev f2)
0000:00:07.0 IDE interface: nVidia Corporation: Unknown device 0054 (rev f2)
0000:00:08.0 IDE interface: nVidia Corporation: Unknown device 0055 (rev f2)
0000:00:09.0 PCI bridge: nVidia Corporation: Unknown device 005c (rev a2)
0000:00:0a.0 Bridge: nVidia Corporation: Unknown device 0057 (rev a2)
0000:00:0b.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a2)
0000:00:0c.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a2)
0000:00:0d.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a2)
0000:00:0e.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a2)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:07.0 VGA compatible controller: nVidia Corporation: Unknown device 0326 (rev a1)
0000:01:09.0 Multimedia audio controller: Creative Labs SB Audigy LS
darkwarrior0404@ubuntu:~$ dmesg | grep 01:09.0
[   48.662356] ACPI: PCI Interrupt 0000:01:09.0[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 19
darkwarrior0404@ubuntu:~$ dmesg
er 0, 4096 bytes)
[   23.137974] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[   23.137978] devfs: boot_options: 0x0
[   23.138003] Initializing Cryptographic API
[   23.138103] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   23.138106] pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vendor BIOS
[   23.138123] assign_interrupt_mode Found MSI capability
[   23.138126] Allocate Port Service[pcie00]
[   23.138158] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   23.138162] pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vendor BIOS
[   23.138177] assign_interrupt_mode Found MSI capability
[   23.138180] Allocate Port Service[pcie00]
[   23.138213] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   23.138216] pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vendor BIOS
[   23.138232] assign_interrupt_mode Found MSI capability
[   23.138234] Allocate Port Service[pcie00]
[   23.138261] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   23.138265] pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vendor BIOS
[   23.138280] assign_interrupt_mode Found MSI capability
[   23.138283] Allocate Port Service[pcie00]
[   23.153577] Linux agpgart interface v0.101 (c) Dave Jones
[   23.153647] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   23.170623] serio: i8042 KBD port at 0x60,0x64 irq 1
[   23.170629] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[   23.170747] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   23.170840] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   23.172348] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   23.172463] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   23.172542] io scheduler noop registered
[   23.172557] io scheduler anticipatory registered
[   23.172563] io scheduler deadline registered
[   23.172570] io scheduler cfq registered
[   23.172861] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   23.172923] NET: Registered protocol family 2
[   23.183573] IP: routing cache hash table of 8192 buckets, 64Kbytes
[   23.183762] TCP established hash table entries: 262144 (order: 9, 2097152 bytes)
[   23.186499] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   23.187047] TCP: Hash tables configured (established 262144 bind 65536)
[   23.187124] NET: Registered protocol family 8
[   23.187127] NET: Registered protocol family 20
[   23.208064] input: AT Translated Set 2 keyboard on isa0060/serio0
[   23.208108] ACPI wakeup devices:
[   23.208110] HUB0 XVR0 XVR1 XVR2 XVR3 USB0 USB2 MMAC MMCI UAR1
[   23.208116] ACPI: (supports S0 S1 S4 S5)
[   23.208334] Freeing unused kernel memory: 136k freed
[   23.222357] vga16fb: initializing
[   23.222361] vga16fb: mapped to 0xffff8100000a0000
[   23.386482] Console: switching to colour frame buffer device 80x30
[   23.386488] fb0: VGA16 VGA frame buffer device
[   24.523862] Capability LSM initialized
[   24.532814] NET: Registered protocol family 1
[   24.541937] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   24.541950] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   24.541953] ACPI: bus type ide registered
[   24.545516] SCSI subsystem initialized
[   24.546658] libata version 1.11 loaded.
[   24.547796] sata_nv version 0.6
[   24.548551] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[   24.548559] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [APSI] -> GSI 23 (level, low) -> IRQ 23
[   24.548579] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   24.548625] ata1: SATA max UDMA/133 cmd 0x9F0 ctl 0xBF2 bmdma 0xF600 irq 23
[   24.548643] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xB72 bmdma 0xF608 irq 23
[   24.749358] ata1: no device found (phy stat 00000000)
[   24.749361] scsi0 : sata_nv
[   24.950336] ata2: no device found (phy stat 00000000)
[   24.950338] scsi1 : sata_nv
[   24.951765] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 22
[   24.951770] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSJ] -> GSI 22 (level, low) -> IRQ 22
[   24.951780] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   24.951802] ata3: SATA max UDMA/133 cmd 0x9E0 ctl 0xBE2 bmdma 0xF100 irq 22
[   24.951820] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xB62 bmdma 0xF108 irq 22
[   25.306389] ata3: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4003 85:3469 86:3c01 87:4003 88:407f
[   25.306394] ata3: dev 0 ATA, max UDMA/133, 312581808 sectors: lba48
[   25.306671] nv_sata: Primary device added
[   25.306673] nv_sata: Primary device removed
[   25.306675] nv_sata: Secondary device added
[   25.306677] nv_sata: Secondary device removed
[   25.306681] ata3: dev 0 configured for UDMA/133
[   25.306683] scsi2 : sata_nv
[   25.507278] ata4: no device found (phy stat 00000000)
[   25.507281] scsi3 : sata_nv
[   25.507332]   Vendor: ATA       Model: ST3160827AS       Rev: 3.42
[   25.507339]   Type:   Direct-Access                      ANSI SCSI revision: 05
[   25.525581] NFORCE-CK804: IDE controller at PCI slot 0000:00:06.0
[   25.525603] NFORCE-CK804: chipset revision 242
[   25.525606] NFORCE-CK804: not 100% native mode: will probe irqs later
[   25.525612] NFORCE-CK804: 0000:00:06.0 (rev f2) UDMA133 controller
[   25.525622]     ide0: BM-DMA at 0xfb00-0xfb07, BIOS settings: hda:DMA, hdb:DMA
[   25.525633]     ide1: BM-DMA at 0xfb08-0xfb0f, BIOS settings: hdc:DMA, hdd:DMA
[   25.525641] Probing IDE interface ide0...
[   26.452251] hdb: MAD DOG MD-52XCDR, ATAPI CD/DVD-ROM drive
[   26.503622] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   26.503670] Probing IDE interface ide1...
[   27.022150] Probing IDE interface ide1...
[   27.540061] Probing IDE interface ide2...
[   28.052006] Probing IDE interface ide3...
[   28.563951] Probing IDE interface ide4...
[   29.075896] Probing IDE interface ide5...
[   29.596800] hdb: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache
[   29.596807] Uniform CD-ROM driver Revision: 3.20
[   29.610303] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[   29.610314] SCSI device sda: drive cache: write back
[   29.610378] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[   29.610386] SCSI device sda: drive cache: write back
[   29.610389]  /dev/scsi/host2/bus0/target0/lun0: p1 p2 p3
[   29.638709] Attached scsi disk sda at scsi2, channel 0, id 0, lun 0
[   29.866896] Attempting manual resume
[   29.867161] swsusp: Suspend partition has wrong signature?
[   29.884652] ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[   29.885288] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
[   29.885296] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 21 (level, low) -> IRQ 21
[   29.885315] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   29.885319] ohci_hcd 0000:00:02.0: nVidia Corporation CK804 USB Controller
[   29.898945] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   29.898956] ohci_hcd 0000:00:02.0: irq 21, io mem 0xfebff000
[   29.951875] hub 1-0:1.0: USB hub found
[   29.951885] hub 1-0:1.0: 10 ports detected
[   29.960717] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20
[   29.960727] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCL] -> GSI 20 (level, low) -> IRQ 20
[   29.960744] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   29.960748] ehci_hcd 0000:00:02.1: nVidia Corporation CK804 USB Controller
[   29.960755] ehci_hcd 0000:00:02.1: debug port 1
[   29.960794] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[   29.960812] ehci_hcd 0000:00:02.1: irq 20, io mem 0xfeb00000
[   29.960840] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[   29.960844] ehci_hcd 0000:00:02.1: park 0
[   29.960850] ehci_hcd 0000:00:02.1: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[   29.960926] hub 2-0:1.0: USB hub found
[   29.960934] hub 2-0:1.0: 10 ports detected
[   30.006402] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.41.
[   30.007045] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[   30.007050] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [APCH] -> GSI 23 (level, low) -> IRQ 23
[   30.007057] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   30.518918] eth0: forcedeth.c: subsystem: 01462:7135 bound to 0000:00:0a.0
[   30.855711] usb 2-2: new high speed USB device using ehci_hcd and address 3
[   31.096682] usb 2-6: new high speed USB device using ehci_hcd and address 4
[   31.659622] usb 1-1: new full speed USB device using ohci_hcd and address 2
[   31.955590] usb 1-7: new low speed USB device using ohci_hcd and address 3
[   32.239560] usb 1-8: new low speed USB device using ohci_hcd and address 4
[   32.576127] usbcore: registered new driver hiddev
[   32.584959] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:02.0-7
[   32.621960] input: USB HID v1.10 Joystick [Saitek PLC Cyborg Force Rumble Pad] on usb-0000:00:02.0-8
[   32.621968] usbcore: registered new driver usbhid
[   32.621971] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
[   32.636408] Initializing USB Mass Storage driver...
[   32.636744] scsi4 : SCSI emulation for USB Mass Storage devices
[   32.636794] usb-storage: device found at 3
[   32.636797] usb-storage: waiting for device to settle before scanning
[   32.637112] scsi5 : SCSI emulation for USB Mass Storage devices
[   32.637146] usb-storage: device found at 4
[   32.637149] usb-storage: waiting for device to settle before scanning
[   32.637156] usbcore: registered new driver usb-storage
[   32.637159] USB Mass Storage support registered.
[   33.053589] ACPI: Fan [FAN] (on)
[   33.055993] ACPI: CPU0 (power states: C1[C1])
[   33.057221] ACPI: Thermal Zone [THRM] (22 C)
[   33.221286] Attempting manual resume
[   33.221479] swsusp: Suspend partition has wrong signature?
[   33.238332] kjournald starting.  Commit interval 5 seconds
[   33.238344] EXT3-fs: mounted filesystem with ordered data mode.
[   33.985922] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[   36.761562] Adding 1566328k swap on /dev/sda3.  Priority:-1 extents:1
[   36.988439] EXT3 FS on sda2, internal journal
[   37.637601]   Vendor: FUJITSU   Model: MPD3064AT         Rev: 0811
[   37.637610]   Type:   Direct-Access                      ANSI SCSI revision: 00
[   37.638713]   Vendor: LEXAR     Model: JUMPDRIVE SECURE  Rev: 3000
[   37.638722]   Type:   Direct-Access                      ANSI SCSI revision: 00
[   37.642643] SCSI device sdb: 12672450 512-byte hdwr sectors (6488 MB)
[   37.642649] sdb: assuming drive cache: write through
[   37.645717] SCSI device sdb: 12672450 512-byte hdwr sectors (6488 MB)
[   37.645722] sdb: assuming drive cache: write through
[   37.645729]  /dev/scsi/host4/bus0/target0/lun0:
[   37.650013] Attached scsi disk sdb at scsi4, channel 0, id 0, lun 0
[   37.651232] usb-storage: device scan complete
[   37.652460] SCSI device sdc: 506880 512-byte hdwr sectors (260 MB)
[   37.653834] sdc: Write Protect is off
[   37.653837] sdc: Mode Sense: 43 00 00 00
[   37.653841] sdc: assuming drive cache: write through
[   37.659710] SCSI device sdc: 506880 512-byte hdwr sectors (260 MB)
[   37.660843] sdc: Write Protect is off
[   37.660846] sdc: Mode Sense: 43 00 00 00
[   37.660849] sdc: assuming drive cache: write through
[   37.660853]  /dev/scsi/host5/bus0/target0/lun0: p1
[   37.663055] Attached scsi removable disk sdc at scsi5, channel 0, id 0, lun 0[   37.664560] usb-storage: device scan complete
[   42.148014] parport: PnPBIOS parport detected.
[   42.148060] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   42.234199] lp0: using parport0 (interrupt-driven).
[   42.279953] mice: PS/2 mouse device common for all mice
[   42.307284] Real Time Clock Driver v1.12
[   45.052402] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[   45.678882] hdb: packet command error: status=0x51 { DriveReady SeekComplete Error }
[   45.678889] hdb: packet command error: error=0x50 { LastFailedSense=0x05 }
[   45.678893] ide: failed opcode was: unknown
[   45.679490] cdrom: failed setting lba address space
[   46.503424] NTFS driver 2.1.22 [Flags: R/O MODULE].
[   46.557213] NTFS volume version 3.1.
[   47.826521] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x4c00
[   47.839389] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x4c40
[   48.208861] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   48.219417] shpchp: Address64 -------- Resource unparsed
[   48.219423] shpchp: Address64 -------- Resource unparsed
[   48.219426] shpchp: Address64 -------- Resource unparsed
[   48.229068] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   48.662346] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[   48.662356] ACPI: PCI Interrupt 0000:01:09.0[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 19
[   48.662386] Model 100a Rev 00000000 Serial 100a1102
[   50.549738] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x03F0 pid 0x7604
[   50.554778] usbcore: registered new driver usblp
[   50.554784] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver[   51.012258] input: PC Speaker
[   51.068081] Floppy drive(s): fd0 is 1.44M
[   51.100551] FDC 0 is a post-1991 82077
[   51.966016] ts: Compaq touchscreen protocol output
[   53.469539] NET: Registered protocol family 17
[   59.245716] NET: Registered protocol family 10
[   59.245828] Disabled Privacy Extensions on device ffffffff8035a5a0(lo)
[   59.246197] IPv6 over IPv4 tunneling driver
[   61.893625] ACPI: Power Button (FF) [PWRF]
[   61.893639] ACPI: Power Button (CM) [PWRB]
[   61.977336] ibm_acpi: ec object not found
[   69.206214] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.40.4)
[   69.210956] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
[   69.581768] Bluetooth: Core ver 2.7
[   69.581776] NET: Registered protocol family 31
[   69.581779] Bluetooth: HCI device and connection manager initialized
[   69.581790] Bluetooth: HCI socket layer initialized
[   69.892522] eth0: no IPv6 routers present
[   70.006377] Bluetooth: L2CAP ver 2.7
[   70.006382] Bluetooth: L2CAP socket layer initialized
[   70.071567] Bluetooth: RFCOMM ver 1.5
[   70.071577] Bluetooth: RFCOMM socket layer initialized
[   70.071592] Bluetooth: RFCOMM TTY layer initialized
[   83.423977] hdb: packet command error: status=0x51 { DriveReady SeekComplete Error }
[   83.423985] hdb: packet command error: error=0x50 { LastFailedSense=0x05 }
[   83.423990] ide: failed opcode was: unknown
[   83.424585] cdrom: failed setting lba address space
[   83.461311] hdb: packet command error: status=0x51 { DriveReady SeekComplete Error }
[   83.461319] hdb: packet command error: error=0x50 { LastFailedSense=0x05 }
[   83.461323] ide: failed opcode was: unknown
[   83.461918] cdrom: failed setting lba address space
[   83.502220] ISO 9660 Extensions: Microsoft Joliet Level 3
[   83.503407] ISOFS: changing to secondary root
[  890.613019] usb 1-1: USB disconnect, address 2
[  890.614373] drivers/usb/class/usblp.c: usblp0: removed
[  891.289928] usb 1-1: new full speed USB device using ohci_hcd and address 5
[  891.417273] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 5 if 0 alt 0 proto 2 vid 0x03F0 pid 0x7604
[ 3661.701320] ibm_acpi: ec object not found
[ 3666.647294] hdb: packet command error: status=0x51 { DriveReady SeekComplete Error }
[ 3666.647302] hdb: packet command error: error=0x50 { LastFailedSense=0x05 }
[ 3666.647306] ide: failed opcode was: unknown
[ 3666.647890] cdrom: failed setting lba address space
darkwarrior0404@ubuntu:~$


irq conflict maybe? :( but it works in windows just fine, and has really good sound, anyone got any ideas?:confused:

---

### Post by darkwarrior0404 on 2006-04-23
> darkwarrior0404@ubuntu:~$ lspci
0000:00:00.0 Memory controller: nVidia Corporation: Unknown device 005e (rev a2)0000:00:01.0 ISA bridge: nVidia Corporation: Unknown device 0050 (rev a2)
0000:00:01.1 SMBus: nVidia Corporation: Unknown device 0052 (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation: Unknown device 005a (rev a2)
0000:00:02.1 USB Controller: nVidia Corporation: Unknown device 005b (rev a2)
0000:00:06.0 IDE interface: nVidia Corporation: Unknown device 0053 (rev f2)
0000:00:07.0 IDE interface: nVidia Corporation: Unknown device 0054 (rev f2)
0000:00:08.0 IDE interface: nVidia Corporation: Unknown device 0055 (rev f2)
0000:00:09.0 PCI bridge: nVidia Corporation: Unknown device 005c (rev a2)
0000:00:0a.0 Bridge: nVidia Corporation: Unknown device 0057 (rev a2)
0000:00:0b.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a2)
0000:00:0c.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a2)
0000:00:0d.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a2)
0000:00:0e.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a2)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:07.0 VGA compatible controller: nVidia Corporation: Unknown device 0326 (rev a1)
0000:01:09.0 Multimedia audio controller: Creative Labs SB Audigy LS
darkwarrior0404@ubuntu:~$ dmesg | grep 01:09.0
[   48.662356] ACPI: PCI Interrupt 0000:01:09.0[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 19
darkwarrior0404@ubuntu:~$ dmesg
er 0, 4096 bytes)
[   23.137974] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[   23.137978] devfs: boot_options: 0x0
[   23.138003] Initializing Cryptographic API
[   23.138103] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   23.138106] pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vendor BIOS
[   23.138123] assign_interrupt_mode Found MSI capability
[   23.138126] Allocate Port Service[pcie00]
[   23.138158] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   23.138162] pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vendor BIOS
[   23.138177] assign_interrupt_mode Found MSI capability
[   23.138180] Allocate Port Service[pcie00]
[   23.138213] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   23.138216] pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vendor BIOS
[   23.138232] assign_interrupt_mode Found MSI capability
[   23.138234] Allocate Port Service[pcie00]
[   23.138261] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   23.138265] pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vendor BIOS
[   23.138280] assign_interrupt_mode Found MSI capability
[   23.138283] Allocate Port Service[pcie00]
[   23.153577] Linux agpgart interface v0.101 (c) Dave Jones
[   23.153647] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   23.170623] serio: i8042 KBD port at 0x60,0x64 irq 1
[   23.170629] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[   23.170747] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   23.170840] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   23.172348] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   23.172463] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   23.172542] io scheduler noop registered
[   23.172557] io scheduler anticipatory registered
[   23.172563] io scheduler deadline registered
[   23.172570] io scheduler cfq registered
[   23.172861] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   23.172923] NET: Registered protocol family 2
[   23.183573] IP: routing cache hash table of 8192 buckets, 64Kbytes
[   23.183762] TCP established hash table entries: 262144 (order: 9, 2097152 bytes)
[   23.186499] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   23.187047] TCP: Hash tables configured (established 262144 bind 65536)
[   23.187124] NET: Registered protocol family 8
[   23.187127] NET: Registered protocol family 20
[   23.208064] input: AT Translated Set 2 keyboard on isa0060/serio0
[   23.208108] ACPI wakeup devices:
[   23.208110] HUB0 XVR0 XVR1 XVR2 XVR3 USB0 USB2 MMAC MMCI UAR1
[   23.208116] ACPI: (supports S0 S1 S4 S5)
[   23.208334] Freeing unused kernel memory: 136k freed
[   23.222357] vga16fb: initializing
[   23.222361] vga16fb: mapped to 0xffff8100000a0000
[   23.386482] Console: switching to colour frame buffer device 80x30
[   23.386488] fb0: VGA16 VGA frame buffer device
[   24.523862] Capability LSM initialized
[   24.532814] NET: Registered protocol family 1
[   24.541937] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   24.541950] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   24.541953] ACPI: bus type ide registered
[   24.545516] SCSI subsystem initialized
[   24.546658] libata version 1.11 loaded.
[   24.547796] sata_nv version 0.6
[   24.548551] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[   24.548559] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [APSI] -> GSI 23 (level, low) -> IRQ 23
[   24.548579] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   24.548625] ata1: SATA max UDMA/133 cmd 0x9F0 ctl 0xBF2 bmdma 0xF600 irq 23
[   24.548643] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xB72 bmdma 0xF608 irq 23
[   24.749358] ata1: no device found (phy stat 00000000)
[   24.749361] scsi0 : sata_nv
[   24.950336] ata2: no device found (phy stat 00000000)
[   24.950338] scsi1 : sata_nv
[   24.951765] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 22
[   24.951770] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSJ] -> GSI 22 (level, low) -> IRQ 22
[   24.951780] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   24.951802] ata3: SATA max UDMA/133 cmd 0x9E0 ctl 0xBE2 bmdma 0xF100 irq 22
[   24.951820] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xB62 bmdma 0xF108 irq 22
[   25.306389] ata3: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4003 85:3469 86:3c01 87:4003 88:407f
[   25.306394] ata3: dev 0 ATA, max UDMA/133, 312581808 sectors: lba48
[   25.306671] nv_sata: Primary device added
[   25.306673] nv_sata: Primary device removed
[   25.306675] nv_sata: Secondary device added
[   25.306677] nv_sata: Secondary device removed
[   25.306681] ata3: dev 0 configured for UDMA/133
[   25.306683] scsi2 : sata_nv
[   25.507278] ata4: no device found (phy stat 00000000)
[   25.507281] scsi3 : sata_nv
[   25.507332]   Vendor: ATA       Model: ST3160827AS       Rev: 3.42
[   25.507339]   Type:   Direct-Access                      ANSI SCSI revision: 05
[   25.525581] NFORCE-CK804: IDE controller at PCI slot 0000:00:06.0
[   25.525603] NFORCE-CK804: chipset revision 242
[   25.525606] NFORCE-CK804: not 100% native mode: will probe irqs later
[   25.525612] NFORCE-CK804: 0000:00:06.0 (rev f2) UDMA133 controller
[   25.525622]     ide0: BM-DMA at 0xfb00-0xfb07, BIOS settings: hda:DMA, hdb:DMA
[   25.525633]     ide1: BM-DMA at 0xfb08-0xfb0f, BIOS settings: hdc:DMA, hdd:DMA
[   25.525641] Probing IDE interface ide0...
[   26.452251] hdb: MAD DOG MD-52XCDR, ATAPI CD/DVD-ROM drive
[   26.503622] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   26.503670] Probing IDE interface ide1...
[   27.022150] Probing IDE interface ide1...
[   27.540061] Probing IDE interface ide2...
[   28.052006] Probing IDE interface ide3...
[   28.563951] Probing IDE interface ide4...
[   29.075896] Probing IDE interface ide5...
[   29.596800] hdb: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache
[   29.596807] Uniform CD-ROM driver Revision: 3.20
[   29.610303] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[   29.610314] SCSI device sda: drive cache: write back
[   29.610378] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[   29.610386] SCSI device sda: drive cache: write back
[   29.610389]  /dev/scsi/host2/bus0/target0/lun0: p1 p2 p3
[   29.638709] Attached scsi disk sda at scsi2, channel 0, id 0, lun 0
[   29.866896] Attempting manual resume
[   29.867161] swsusp: Suspend partition has wrong signature?
[   29.884652] ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[   29.885288] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
[   29.885296] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 21 (level, low) -> IRQ 21
[   29.885315] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   29.885319] ohci_hcd 0000:00:02.0: nVidia Corporation CK804 USB Controller
[   29.898945] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   29.898956] ohci_hcd 0000:00:02.0: irq 21, io mem 0xfebff000
[   29.951875] hub 1-0:1.0: USB hub found
[   29.951885] hub 1-0:1.0: 10 ports detected
[   29.960717] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20
[   29.960727] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCL] -> GSI 20 (level, low) -> IRQ 20
[   29.960744] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   29.960748] ehci_hcd 0000:00:02.1: nVidia Corporation CK804 USB Controller
[   29.960755] ehci_hcd 0000:00:02.1: debug port 1
[   29.960794] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[   29.960812] ehci_hcd 0000:00:02.1: irq 20, io mem 0xfeb00000
[   29.960840] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[   29.960844] ehci_hcd 0000:00:02.1: park 0
[   29.960850] ehci_hcd 0000:00:02.1: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[   29.960926] hub 2-0:1.0: USB hub found
[   29.960934] hub 2-0:1.0: 10 ports detected
[   30.006402] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.41.
[   30.007045] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[   30.007050] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [APCH] -> GSI 23 (level, low) -> IRQ 23
[   30.007057] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   30.518918] eth0: forcedeth.c: subsystem: 01462:7135 bound to 0000:00:0a.0
[   30.855711] usb 2-2: new high speed USB device using ehci_hcd and address 3
[   31.096682] usb 2-6: new high speed USB device using ehci_hcd and address 4
[   31.659622] usb 1-1: new full speed USB device using ohci_hcd and address 2
[   31.955590] usb 1-7: new low speed USB device using ohci_hcd and address 3
[   32.239560] usb 1-8: new low speed USB device using ohci_hcd and address 4
[   32.576127] usbcore: registered new driver hiddev
[   32.584959] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:02.0-7
[   32.621960] input: USB HID v1.10 Joystick [Saitek PLC Cyborg Force Rumble Pad] on usb-0000:00:02.0-8
[   32.621968] usbcore: registered new driver usbhid
[   32.621971] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
[   32.636408] Initializing USB Mass Storage driver...
[   32.636744] scsi4 : SCSI emulation for USB Mass Storage devices
[   32.636794] usb-storage: device found at 3
[   32.636797] usb-storage: waiting for device to settle before scanning
[   32.637112] scsi5 : SCSI emulation for USB Mass Storage devices
[   32.637146] usb-storage: device found at 4
[   32.637149] usb-storage: waiting for device to settle before scanning
[   32.637156] usbcore: registered new driver usb-storage
[   32.637159] USB Mass Storage support registered.
[   33.053589] ACPI: Fan [FAN] (on)
[   33.055993] ACPI: CPU0 (power states: C1[C1])
[   33.057221] ACPI: Thermal Zone [THRM] (22 C)
[   33.221286] Attempting manual resume
[   33.221479] swsusp: Suspend partition has wrong signature?
[   33.238332] kjournald starting.  Commit interval 5 seconds
[   33.238344] EXT3-fs: mounted filesystem with ordered data mode.
[   33.985922] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[   36.761562] Adding 1566328k swap on /dev/sda3.  Priority:-1 extents:1
[   36.988439] EXT3 FS on sda2, internal journal
[   37.637601]   Vendor: FUJITSU   Model: MPD3064AT         Rev: 0811
[   37.637610]   Type:   Direct-Access                      ANSI SCSI revision: 00
[   37.638713]   Vendor: LEXAR     Model: JUMPDRIVE SECURE  Rev: 3000
[   37.638722]   Type:   Direct-Access                      ANSI SCSI revision: 00
[   37.642643] SCSI device sdb: 12672450 512-byte hdwr sectors (6488 MB)
[   37.642649] sdb: assuming drive cache: write through
[   37.645717] SCSI device sdb: 12672450 512-byte hdwr sectors (6488 MB)
[   37.645722] sdb: assuming drive cache: write through
[   37.645729]  /dev/scsi/host4/bus0/target0/lun0:
[   37.650013] Attached scsi disk sdb at scsi4, channel 0, id 0, lun 0
[   37.651232] usb-storage: device scan complete
[   37.652460] SCSI device sdc: 506880 512-byte hdwr sectors (260 MB)
[   37.653834] sdc: Write Protect is off
[   37.653837] sdc: Mode Sense: 43 00 00 00
[   37.653841] sdc: assuming drive cache: write through
[   37.659710] SCSI device sdc: 506880 512-byte hdwr sectors (260 MB)
[   37.660843] sdc: Write Protect is off
[   37.660846] sdc: Mode Sense: 43 00 00 00
[   37.660849] sdc: assuming drive cache: write through
[   37.660853]  /dev/scsi/host5/bus0/target0/lun0: p1
[   37.663055] Attached scsi removable disk sdc at scsi5, channel 0, id 0, lun 0[   37.664560] usb-storage: device scan complete
[   42.148014] parport: PnPBIOS parport detected.
[   42.148060] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   42.234199] lp0: using parport0 (interrupt-driven).
[   42.279953] mice: PS/2 mouse device common for all mice
[   42.307284] Real Time Clock Driver v1.12
[   45.052402] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[   45.678882] hdb: packet command error: status=0x51 { DriveReady SeekComplete Error }
[   45.678889] hdb: packet command error: error=0x50 { LastFailedSense=0x05 }
[   45.678893] ide: failed opcode was: unknown
[   45.679490] cdrom: failed setting lba address space
[   46.503424] NTFS driver 2.1.22 [Flags: R/O MODULE].
[   46.557213] NTFS volume version 3.1.
[   47.826521] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x4c00
[   47.839389] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x4c40
[   48.208861] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   48.219417] shpchp: Address64 -------- Resource unparsed
[   48.219423] shpchp: Address64 -------- Resource unparsed
[   48.219426] shpchp: Address64 -------- Resource unparsed
[   48.229068] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   48.662346] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[   48.662356] ACPI: PCI Interrupt 0000:01:09.0[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 19
[   48.662386] Model 100a Rev 00000000 Serial 100a1102
[   50.549738] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x03F0 pid 0x7604
[   50.554778] usbcore: registered new driver usblp
[   50.554784] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver[   51.012258] input: PC Speaker
[   51.068081] Floppy drive(s): fd0 is 1.44M
[   51.100551] FDC 0 is a post-1991 82077
[   51.966016] ts: Compaq touchscreen protocol output
[   53.469539] NET: Registered protocol family 17
[   59.245716] NET: Registered protocol family 10
[   59.245828] Disabled Privacy Extensions on device ffffffff8035a5a0(lo)
[   59.246197] IPv6 over IPv4 tunneling driver
[   61.893625] ACPI: Power Button (FF) [PWRF]
[   61.893639] ACPI: Power Button (CM) [PWRB]
[   61.977336] ibm_acpi: ec object not found
[   69.206214] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.40.4)
[   69.210956] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
[   69.581768] Bluetooth: Core ver 2.7
[   69.581776] NET: Registered protocol family 31
[   69.581779] Bluetooth: HCI device and connection manager initialized
[   69.581790] Bluetooth: HCI socket layer initialized
[   69.892522] eth0: no IPv6 routers present
[   70.006377] Bluetooth: L2CAP ver 2.7
[   70.006382] Bluetooth: L2CAP socket layer initialized
[   70.071567] Bluetooth: RFCOMM ver 1.5
[   70.071577] Bluetooth: RFCOMM socket layer initialized
[   70.071592] Bluetooth: RFCOMM TTY layer initialized
[   83.423977] hdb: packet command error: status=0x51 { DriveReady SeekComplete Error }
[   83.423985] hdb: packet command error: error=0x50 { LastFailedSense=0x05 }
[   83.423990] ide: failed opcode was: unknown
[   83.424585] cdrom: failed setting lba address space
[   83.461311] hdb: packet command error: status=0x51 { DriveReady SeekComplete Error }
[   83.461319] hdb: packet command error: error=0x50 { LastFailedSense=0x05 }
[   83.461323] ide: failed opcode was: unknown
[   83.461918] cdrom: failed setting lba address space
[   83.502220] ISO 9660 Extensions: Microsoft Joliet Level 3
[   83.503407] ISOFS: changing to secondary root
[  890.613019] usb 1-1: USB disconnect, address 2
[  890.614373] drivers/usb/class/usblp.c: usblp0: removed
[  891.289928] usb 1-1: new full speed USB device using ohci_hcd and address 5
[  891.417273] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 5 if 0 alt 0 proto 2 vid 0x03F0 pid 0x7604
[ 3661.701320] ibm_acpi: ec object not found
[ 3666.647294] hdb: packet command error: status=0x51 { DriveReady SeekComplete Error }
[ 3666.647302] hdb: packet command error: error=0x50 { LastFailedSense=0x05 }
[ 3666.647306] ide: failed opcode was: unknown
[ 3666.647890] cdrom: failed setting lba address space
darkwarrior0404@ubuntu:~$


irq conflict maybe? :( but it works in windows just fine, and has really good sound, anyone got any ideas?:confused:

---

### Post by darkwarrior0404 on 2006-04-23
> darkwarrior0404@ubuntu:~$ lspci
0000:00:00.0 Memory controller: nVidia Corporation: Unknown device 005e (rev a2)0000:00:01.0 ISA bridge: nVidia Corporation: Unknown device 0050 (rev a2)
0000:00:01.1 SMBus: nVidia Corporation: Unknown device 0052 (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation: Unknown device 005a (rev a2)
0000:00:02.1 USB Controller: nVidia Corporation: Unknown device 005b (rev a2)
0000:00:06.0 IDE interface: nVidia Corporation: Unknown device 0053 (rev f2)
0000:00:07.0 IDE interface: nVidia Corporation: Unknown device 0054 (rev f2)
0000:00:08.0 IDE interface: nVidia Corporation: Unknown device 0055 (rev f2)
0000:00:09.0 PCI bridge: nVidia Corporation: Unknown device 005c (rev a2)
0000:00:0a.0 Bridge: nVidia Corporation: Unknown device 0057 (rev a2)
0000:00:0b.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a2)
0000:00:0c.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a2)
0000:00:0d.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a2)
0000:00:0e.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a2)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:07.0 VGA compatible controller: nVidia Corporation: Unknown device 0326 (rev a1)
0000:01:09.0 Multimedia audio controller: Creative Labs SB Audigy LS
darkwarrior0404@ubuntu:~$ dmesg | grep 01:09.0
[   48.662356] ACPI: PCI Interrupt 0000:01:09.0[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 19
darkwarrior0404@ubuntu:~$ dmesg
er 0, 4096 bytes)
[   23.137974] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[   23.137978] devfs: boot_options: 0x0
[   23.138003] Initializing Cryptographic API
[   23.138103] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   23.138106] pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vendor BIOS
[   23.138123] assign_interrupt_mode Found MSI capability
[   23.138126] Allocate Port Service[pcie00]
[   23.138158] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   23.138162] pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vendor BIOS
[   23.138177] assign_interrupt_mode Found MSI capability
[   23.138180] Allocate Port Service[pcie00]
[   23.138213] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   23.138216] pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vendor BIOS
[   23.138232] assign_interrupt_mode Found MSI capability
[   23.138234] Allocate Port Service[pcie00]
[   23.138261] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   23.138265] pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vendor BIOS
[   23.138280] assign_interrupt_mode Found MSI capability
[   23.138283] Allocate Port Service[pcie00]
[   23.153577] Linux agpgart interface v0.101 (c) Dave Jones
[   23.153647] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   23.170623] serio: i8042 KBD port at 0x60,0x64 irq 1
[   23.170629] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[   23.170747] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   23.170840] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   23.172348] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   23.172463] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   23.172542] io scheduler noop registered
[   23.172557] io scheduler anticipatory registered
[   23.172563] io scheduler deadline registered
[   23.172570] io scheduler cfq registered
[   23.172861] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   23.172923] NET: Registered protocol family 2
[   23.183573] IP: routing cache hash table of 8192 buckets, 64Kbytes
[   23.183762] TCP established hash table entries: 262144 (order: 9, 2097152 bytes)
[   23.186499] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   23.187047] TCP: Hash tables configured (established 262144 bind 65536)
[   23.187124] NET: Registered protocol family 8
[   23.187127] NET: Registered protocol family 20
[   23.208064] input: AT Translated Set 2 keyboard on isa0060/serio0
[   23.208108] ACPI wakeup devices:
[   23.208110] HUB0 XVR0 XVR1 XVR2 XVR3 USB0 USB2 MMAC MMCI UAR1
[   23.208116] ACPI: (supports S0 S1 S4 S5)
[   23.208334] Freeing unused kernel memory: 136k freed
[   23.222357] vga16fb: initializing
[   23.222361] vga16fb: mapped to 0xffff8100000a0000
[   23.386482] Console: switching to colour frame buffer device 80x30
[   23.386488] fb0: VGA16 VGA frame buffer device
[   24.523862] Capability LSM initialized
[   24.532814] NET: Registered protocol family 1
[   24.541937] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   24.541950] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   24.541953] ACPI: bus type ide registered
[   24.545516] SCSI subsystem initialized
[   24.546658] libata version 1.11 loaded.
[   24.547796] sata_nv version 0.6
[   24.548551] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[   24.548559] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [APSI] -> GSI 23 (level, low) -> IRQ 23
[   24.548579] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   24.548625] ata1: SATA max UDMA/133 cmd 0x9F0 ctl 0xBF2 bmdma 0xF600 irq 23
[   24.548643] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xB72 bmdma 0xF608 irq 23
[   24.749358] ata1: no device found (phy stat 00000000)
[   24.749361] scsi0 : sata_nv
[   24.950336] ata2: no device found (phy stat 00000000)
[   24.950338] scsi1 : sata_nv
[   24.951765] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 22
[   24.951770] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSJ] -> GSI 22 (level, low) -> IRQ 22
[   24.951780] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   24.951802] ata3: SATA max UDMA/133 cmd 0x9E0 ctl 0xBE2 bmdma 0xF100 irq 22
[   24.951820] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xB62 bmdma 0xF108 irq 22
[   25.306389] ata3: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4003 85:3469 86:3c01 87:4003 88:407f
[   25.306394] ata3: dev 0 ATA, max UDMA/133, 312581808 sectors: lba48
[   25.306671] nv_sata: Primary device added
[   25.306673] nv_sata: Primary device removed
[   25.306675] nv_sata: Secondary device added
[   25.306677] nv_sata: Secondary device removed
[   25.306681] ata3: dev 0 configured for UDMA/133
[   25.306683] scsi2 : sata_nv
[   25.507278] ata4: no device found (phy stat 00000000)
[   25.507281] scsi3 : sata_nv
[   25.507332]   Vendor: ATA       Model: ST3160827AS       Rev: 3.42
[   25.507339]   Type:   Direct-Access                      ANSI SCSI revision: 05
[   25.525581] NFORCE-CK804: IDE controller at PCI slot 0000:00:06.0
[   25.525603] NFORCE-CK804: chipset revision 242
[   25.525606] NFORCE-CK804: not 100% native mode: will probe irqs later
[   25.525612] NFORCE-CK804: 0000:00:06.0 (rev f2) UDMA133 controller
[   25.525622]     ide0: BM-DMA at 0xfb00-0xfb07, BIOS settings: hda:DMA, hdb:DMA
[   25.525633]     ide1: BM-DMA at 0xfb08-0xfb0f, BIOS settings: hdc:DMA, hdd:DMA
[   25.525641] Probing IDE interface ide0...
[   26.452251] hdb: MAD DOG MD-52XCDR, ATAPI CD/DVD-ROM drive
[   26.503622] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   26.503670] Probing IDE interface ide1...
[   27.022150] Probing IDE interface ide1...
[   27.540061] Probing IDE interface ide2...
[   28.052006] Probing IDE interface ide3...
[   28.563951] Probing IDE interface ide4...
[   29.075896] Probing IDE interface ide5...
[   29.596800] hdb: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache
[   29.596807] Uniform CD-ROM driver Revision: 3.20
[   29.610303] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[   29.610314] SCSI device sda: drive cache: write back
[   29.610378] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[   29.610386] SCSI device sda: drive cache: write back
[   29.610389]  /dev/scsi/host2/bus0/target0/lun0: p1 p2 p3
[   29.638709] Attached scsi disk sda at scsi2, channel 0, id 0, lun 0
[   29.866896] Attempting manual resume
[   29.867161] swsusp: Suspend partition has wrong signature?
[   29.884652] ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[   29.885288] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
[   29.885296] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 21 (level, low) -> IRQ 21
[   29.885315] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   29.885319] ohci_hcd 0000:00:02.0: nVidia Corporation CK804 USB Controller
[   29.898945] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   29.898956] ohci_hcd 0000:00:02.0: irq 21, io mem 0xfebff000
[   29.951875] hub 1-0:1.0: USB hub found
[   29.951885] hub 1-0:1.0: 10 ports detected
[   29.960717] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20
[   29.960727] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCL] -> GSI 20 (level, low) -> IRQ 20
[   29.960744] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   29.960748] ehci_hcd 0000:00:02.1: nVidia Corporation CK804 USB Controller
[   29.960755] ehci_hcd 0000:00:02.1: debug port 1
[   29.960794] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[   29.960812] ehci_hcd 0000:00:02.1: irq 20, io mem 0xfeb00000
[   29.960840] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[   29.960844] ehci_hcd 0000:00:02.1: park 0
[   29.960850] ehci_hcd 0000:00:02.1: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[   29.960926] hub 2-0:1.0: USB hub found
[   29.960934] hub 2-0:1.0: 10 ports detected
[   30.006402] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.41.
[   30.007045] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[   30.007050] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [APCH] -> GSI 23 (level, low) -> IRQ 23
[   30.007057] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   30.518918] eth0: forcedeth.c: subsystem: 01462:7135 bound to 0000:00:0a.0
[   30.855711] usb 2-2: new high speed USB device using ehci_hcd and address 3
[   31.096682] usb 2-6: new high speed USB device using ehci_hcd and address 4
[   31.659622] usb 1-1: new full speed USB device using ohci_hcd and address 2
[   31.955590] usb 1-7: new low speed USB device using ohci_hcd and address 3
[   32.239560] usb 1-8: new low speed USB device using ohci_hcd and address 4
[   32.576127] usbcore: registered new driver hiddev
[   32.584959] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:02.0-7
[   32.621960] input: USB HID v1.10 Joystick [Saitek PLC Cyborg Force Rumble Pad] on usb-0000:00:02.0-8
[   32.621968] usbcore: registered new driver usbhid
[   32.621971] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
[   32.636408] Initializing USB Mass Storage driver...
[   32.636744] scsi4 : SCSI emulation for USB Mass Storage devices
[   32.636794] usb-storage: device found at 3
[   32.636797] usb-storage: waiting for device to settle before scanning
[   32.637112] scsi5 : SCSI emulation for USB Mass Storage devices
[   32.637146] usb-storage: device found at 4
[   32.637149] usb-storage: waiting for device to settle before scanning
[   32.637156] usbcore: registered new driver usb-storage
[   32.637159] USB Mass Storage support registered.
[   33.053589] ACPI: Fan [FAN] (on)
[   33.055993] ACPI: CPU0 (power states: C1[C1])
[   33.057221] ACPI: Thermal Zone [THRM] (22 C)
[   33.221286] Attempting manual resume
[   33.221479] swsusp: Suspend partition has wrong signature?
[   33.238332] kjournald starting.  Commit interval 5 seconds
[   33.238344] EXT3-fs: mounted filesystem with ordered data mode.
[   33.985922] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[   36.761562] Adding 1566328k swap on /dev/sda3.  Priority:-1 extents:1
[   36.988439] EXT3 FS on sda2, internal journal
[   37.637601]   Vendor: FUJITSU   Model: MPD3064AT         Rev: 0811
[   37.637610]   Type:   Direct-Access                      ANSI SCSI revision: 00
[   37.638713]   Vendor: LEXAR     Model: JUMPDRIVE SECURE  Rev: 3000
[   37.638722]   Type:   Direct-Access                      ANSI SCSI revision: 00
[   37.642643] SCSI device sdb: 12672450 512-byte hdwr sectors (6488 MB)
[   37.642649] sdb: assuming drive cache: write through
[   37.645717] SCSI device sdb: 12672450 512-byte hdwr sectors (6488 MB)
[   37.645722] sdb: assuming drive cache: write through
[   37.645729]  /dev/scsi/host4/bus0/target0/lun0:
[   37.650013] Attached scsi disk sdb at scsi4, channel 0, id 0, lun 0
[   37.651232] usb-storage: device scan complete
[   37.652460] SCSI device sdc: 506880 512-byte hdwr sectors (260 MB)
[   37.653834] sdc: Write Protect is off
[   37.653837] sdc: Mode Sense: 43 00 00 00
[   37.653841] sdc: assuming drive cache: write through
[   37.659710] SCSI device sdc: 506880 512-byte hdwr sectors (260 MB)
[   37.660843] sdc: Write Protect is off
[   37.660846] sdc: Mode Sense: 43 00 00 00
[   37.660849] sdc: assuming drive cache: write through
[   37.660853]  /dev/scsi/host5/bus0/target0/lun0: p1
[   37.663055] Attached scsi removable disk sdc at scsi5, channel 0, id 0, lun 0[   37.664560] usb-storage: device scan complete
[   42.148014] parport: PnPBIOS parport detected.
[   42.148060] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   42.234199] lp0: using parport0 (interrupt-driven).
[   42.279953] mice: PS/2 mouse device common for all mice
[   42.307284] Real Time Clock Driver v1.12
[   45.052402] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[   45.678882] hdb: packet command error: status=0x51 { DriveReady SeekComplete Error }
[   45.678889] hdb: packet command error: error=0x50 { LastFailedSense=0x05 }
[   45.678893] ide: failed opcode was: unknown
[   45.679490] cdrom: failed setting lba address space
[   46.503424] NTFS driver 2.1.22 [Flags: R/O MODULE].
[   46.557213] NTFS volume version 3.1.
[   47.826521] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x4c00
[   47.839389] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x4c40
[   48.208861] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   48.219417] shpchp: Address64 -------- Resource unparsed
[   48.219423] shpchp: Address64 -------- Resource unparsed
[   48.219426] shpchp: Address64 -------- Resource unparsed
[   48.229068] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   48.662346] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[   48.662356] ACPI: PCI Interrupt 0000:01:09.0[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 19
[   48.662386] Model 100a Rev 00000000 Serial 100a1102
[   50.549738] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x03F0 pid 0x7604
[   50.554778] usbcore: registered new driver usblp
[   50.554784] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver[   51.012258] input: PC Speaker
[   51.068081] Floppy drive(s): fd0 is 1.44M
[   51.100551] FDC 0 is a post-1991 82077
[   51.966016] ts: Compaq touchscreen protocol output
[   53.469539] NET: Registered protocol family 17
[   59.245716] NET: Registered protocol family 10
[   59.245828] Disabled Privacy Extensions on device ffffffff8035a5a0(lo)
[   59.246197] IPv6 over IPv4 tunneling driver
[   61.893625] ACPI: Power Button (FF) [PWRF]
[   61.893639] ACPI: Power Button (CM) [PWRB]
[   61.977336] ibm_acpi: ec object not found
[   69.206214] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.40.4)
[   69.210956] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
[   69.581768] Bluetooth: Core ver 2.7
[   69.581776] NET: Registered protocol family 31
[   69.581779] Bluetooth: HCI device and connection manager initialized
[   69.581790] Bluetooth: HCI socket layer initialized
[   69.892522] eth0: no IPv6 routers present
[   70.006377] Bluetooth: L2CAP ver 2.7
[   70.006382] Bluetooth: L2CAP socket layer initialized
[   70.071567] Bluetooth: RFCOMM ver 1.5
[   70.071577] Bluetooth: RFCOMM socket layer initialized
[   70.071592] Bluetooth: RFCOMM TTY layer initialized
[   83.423977] hdb: packet command error: status=0x51 { DriveReady SeekComplete Error }
[   83.423985] hdb: packet command error: error=0x50 { LastFailedSense=0x05 }
[   83.423990] ide: failed opcode was: unknown
[   83.424585] cdrom: failed setting lba address space
[   83.461311] hdb: packet command error: status=0x51 { DriveReady SeekComplete Error }
[   83.461319] hdb: packet command error: error=0x50 { LastFailedSense=0x05 }
[   83.461323] ide: failed opcode was: unknown
[   83.461918] cdrom: failed setting lba address space
[   83.502220] ISO 9660 Extensions: Microsoft Joliet Level 3
[   83.503407] ISOFS: changing to secondary root
[  890.613019] usb 1-1: USB disconnect, address 2
[  890.614373] drivers/usb/class/usblp.c: usblp0: removed
[  891.289928] usb 1-1: new full speed USB device using ohci_hcd and address 5
[  891.417273] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 5 if 0 alt 0 proto 2 vid 0x03F0 pid 0x7604
[ 3661.701320] ibm_acpi: ec object not found
[ 3666.647294] hdb: packet command error: status=0x51 { DriveReady SeekComplete Error }
[ 3666.647302] hdb: packet command error: error=0x50 { LastFailedSense=0x05 }
[ 3666.647306] ide: failed opcode was: unknown
[ 3666.647890] cdrom: failed setting lba address space
darkwarrior0404@ubuntu:~$


irq conflict maybe? :( but it works in windows just fine, and has really good sound, anyone got any ideas?:confused:

---

