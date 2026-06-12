---
title: "harddisk  unrecognized"
date: 2006-01-05
forum: Hardware &amp; Laptops
---

### Post by gosh on 2006-01-05
I installed Ubuntu on my kids desktop, because XP was causing all sorts of trouble.

I erased the first harddisk /dev/hda (30Gb) to install Ubuntu.
The other harddisk /dev/hdb (120Gb) contains at least a ntfs partition of 60Gb. However this harddisk is not recognized (says Gparted) and cannot be mount: 
mount: can't find /dev/hdb in /etc/fstab or /etc/mtab
It can be found by System Information however.

How can I mount this disk?

---

### Post by mcduck on 2006-01-05
Here's a nice howt on mounting NTFS drives automaticly:
[http://www.ubuntuguide.org/#automountntfs]("http://www.ubuntuguide.org/#automountntfs")
(the guide is for older version of Ubuntu, but there is no difference in mounting drives. You should also take a look at 'Ubuntu 5.10 Starter Guide' in gnome's help (system/help). It has a lots of useful information and instructions how to do things in ubuntu.

---

### Post by gosh on 2006-01-05
When I mount it this happens:

gosh@sjors:/dev$ sudo mount /dev/hdb /media/windows/ -t ntfs -o nls=utf8,umask=0222
mount: /dev/hdb already mounted or /media/windows/ busy

Disk manager "sees" the disk but says "no know partitions":confused:

---

### Post by Amon_Re on 2006-01-05
[QUOTE=gosh]I installed Ubuntu on my kids desktop, because XP was causing all sorts of trouble.

I erased the first harddisk /dev/hda (30Gb) to install Ubuntu.
The other harddisk /dev/hdb (120Gb) contains at least a ntfs partition of 60Gb. However this harddisk is not recognized (says Gparted) and cannot be mount: 
mount: can't find /dev/hdb in /etc/fstab or /etc/mtab
It can be found by System Information however.

How can I mount this disk?[/QUOTE]

What does **sudo fdisk -l** tell you? It should list all drives & all partitions detected, aswell as their filesystem.

If you find it, that you can mount it like this, ex. given:

sudo mount /dev/hdb1 /mnt/ntfs

Assuming a directory called ntfs exists in /mnt
Also note that this will make the drive owned by root, but it's good for a quick test

---

### Post by gosh on 2006-01-06
[QUOTE=Amon_Re]What does **sudo fdisk -l** tell you? It should list all drives & all partitions detected, aswell as their filesystem.

If you find it, that you can mount it like this, ex. given:

sudo mount /dev/hdb1 /mnt/ntfs

Assuming a directory called ntfs exists in /mnt
Also note that this will make the drive owned by root, but it's good for a quick test[/QUOTE]
output of fdisk -l:

Disk /dev/hda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3497    28089621   83  Linux
/dev/hda2            3498        3649     1220940    5  Extended
/dev/hda5            3498        3649     1220908+  82  Linux swap / Solaris

It doesn't even see hdb

---

### Post by Amon_Re on 2006-01-06
[QUOTE=gosh]output of fdisk -l:

Disk /dev/hda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3497    28089621   83  Linux
/dev/hda2            3498        3649     1220940    5  Extended
/dev/hda5            3498        3649     1220908+  82  Linux swap / Solaris

It doesn't even see hdb[/QUOTE]

Well, that's your problem right there, how is the other drive connected? To the same controller as the primary drive? did you check dmesg for messages related to the hard drive?

---

### Post by gosh on 2006-01-06
[QUOTE=Amon_Re]Well, that's your problem right there, how is the other drive connected? To the same controller as the primary drive? did you check dmesg for messages related to the hard drive?[/QUOTE]

The other drive is connected to the same controller as the primary drive.
I don't know what to look for in dmesg, but here is the output. Maybe you can help.

3000] Cannot allocate resource for EISA slot 8
[4294672.253000] EISA: Detected 0 cards.
[4294672.253000] NET: Registered protocol family 2
[4294672.262000] IP: routing cache hash table of 8192 buckets, 64Kbytes
[4294672.262000] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[4294672.268000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[4294672.269000] TCP: Hash tables configured (established 131072 bind 65536)
[4294672.269000] NET: Registered protocol family 8
[4294672.269000] NET: Registered protocol family 20
[4294672.270000] ACPI wakeup devices:
[4294672.270000] PCI0 USB0 UAR1  KBC MICE
[4294672.270000] ACPI: (supports S0 S1 S5)
[4294672.271000] Freeing unused kernel memory: 224k freed
[4294672.303000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294672.310000] vga16fb: initializing
[4294672.310000] vga16fb: mapped to 0xc00a0000
[4294672.455000] Console: switching to colour frame buffer device 80x30
[4294672.455000] fb0: VGA16 VGA frame buffer device
[4294673.616000] Capability LSM initialized
[4294673.645000] NET: Registered protocol family 1
[4294673.674000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294673.674000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294673.675000] ACPI: bus type ide registered
[4294673.694000] PIIX4: IDE controller at PCI slot 0000:00:07.1
[4294673.694000] PIIX4: chipset revision 1
[4294673.694000] PIIX4: not 100% native mode: will probe irqs later
[4294673.694000]     ide0: BM-DMA at 0x1000-0x1007, BIOS settings: hda:pio, hdb:DMA
[4294673.694000]     ide1: BM-DMA at 0x1008-0x100f, BIOS settings: hdc:pio, hdd:DMA
[4294673.694000] Probing IDE interface ide0...
[4294673.958000] hda: QUANTUM FIREBALLP LM30.0, ATA DISK drive
[4294674.213000] hdb: Maxtor 6Y120L0, ATA DISK drive
[4294674.264000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294674.264000] Probing IDE interface ide1...
[4294674.630000] hdc: CRD-8482B, ATAPI CD/DVD-ROM drive
[4294675.344000] hdd: ATAPI DVD DUAL 8X4X12, ATAPI CD/DVD-ROM drive
[4294675.395000] ide1 at 0x170-0x177,0x376 on irq 15
[4294675.395000] Probing IDE interface ide2...
[4294675.908000] Probing IDE interface ide3...
[4294676.421000] Probing IDE interface ide4...
[4294676.934000] Probing IDE interface ide5...
[4294677.456000] hda: max request size: 128KiB
[4294677.470000] hda: 58633344 sectors (30020 MB) w/1900KiB Cache, CHS=58168/16/63, UDMA(33)
[4294677.470000] hda: cache flushes not supported
[4294677.470000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
[4294677.493000] hdb: max request size: 128KiB
[4294677.493000] hdb: 240121728 sectors (122942 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(33)
[4294677.494000] hdb: cache flushes supported
[4294677.494000]  /dev/ide/host0/bus0/target1/lun0:hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[4294678.827000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=3, sector=0
[4294678.827000] ide: failed opcode was: unknown
[4294678.827000] end_request: I/O error, dev hdb, sector 0
[4294678.827000] Buffer I/O error on device hdb, logical block 0
[4294680.167000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[4294680.167000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=3, sector=0
[4294680.167000] ide: failed opcode was: unknown
[4294680.167000] end_request: I/O error, dev hdb, sector 0
[4294680.167000] Buffer I/O error on device hdb, logical block 0
[4294680.167000]  unable to read partition table
[4294680.181000] hdc: ATAPI 48X CD-ROM drive, 128kB Cache
[4294680.181000] Uniform CD-ROM driver Revision: 3.20
[4294680.183000] hdd: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 8192kB Cache
[4294681.080000] Attempting manual resume
[4294681.080000] swsusp: Suspend partition has wrong signature?
[4294681.176000] usbcore: registered new driver usbfs
[4294681.176000] usbcore: registered new driver hub
[4294681.179000] USB Universal Host Controller Interface driver v2.2
[4294681.180000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 9
[4294681.180000] PCI: setting IRQ 9 as level-triggered
[4294681.180000] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[4294681.180000] uhci_hcd 0000:00:07.2: Intel Corporation 82371AB/EB/MB PIIX4 USB
[4294681.242000] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[4294681.242000] uhci_hcd 0000:00:07.2: irq 9, io base 0x00001020
[4294681.242000] hub 1-0:1.0: USB hub found
[4294681.242000] hub 1-0:1.0: 2 ports detected
[4294681.286000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[4294681.286000] PCI: setting IRQ 11 as level-triggered
[4294681.286000] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4294681.286000] 3c59x: Donald Becker and others. [www.scyld.com/network/vortex.html](www.scyld.com/network/vortex.html)
[4294681.286000] 0000:00:0d.0: 3Com PCI 3c905C Tornado at 0x1080. Vers LK1.1.19
[4294681.363000] ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[4294681.363000] PCI: Enabling device 0000:00:0f.0 (0114 -> 0116)
[4294681.364000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 3
[4294681.364000] PCI: setting IRQ 3 as level-triggered
[4294681.364000] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [LNKC] -> GSI 3 (level, low) -> IRQ 3
[4294681.364000] ohci_hcd 0000:00:0f.0: NEC Corporation USB
[4294681.364000] ohci_hcd 0000:00:0f.0: new USB bus registered, assigned bus number 2
[4294681.364000] ohci_hcd 0000:00:0f.0: irq 3, io mem 0xe8001000
[4294681.444000] usb 1-1: new low speed USB device using uhci_hcd and address 2
[4294681.445000] hub 2-0:1.0: USB hub found
[4294681.445000] hub 2-0:1.0: 2 ports detected
[4294681.476000] PCI: Enabling device 0000:00:0f.1 (0114 -> 0116)
[4294681.476000] ACPI: PCI Interrupt 0000:00:0f.1[B] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[4294681.476000] ohci_hcd 0000:00:0f.1: NEC Corporation USB (#2)
[4294681.476000] ohci_hcd 0000:00:0f.1: new USB bus registered, assigned bus number 3
[4294681.476000] ohci_hcd 0000:00:0f.1: irq 9, io mem 0xe8002000
[4294681.556000] hub 3-0:1.0: USB hub found
[4294681.557000] hub 3-0:1.0: 1 port detected
[4294681.628000] PCI: Enabling device 0000:00:0f.2 (0114 -> 0116)
[4294681.628000] ACPI: PCI Interrupt 0000:00:0f.2[C] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4294681.628000] ehci_hcd 0000:00:0f.2: NEC Corporation USB 2.0
[4294681.649000] ehci_hcd 0000:00:0f.2: new USB bus registered, assigned bus number 4
[4294681.649000] ehci_hcd 0000:00:0f.2: irq 11, io mem 0xe8000400
[4294681.649000] ehci_hcd 0000:00:0f.2: park 0
[4294681.649000] ehci_hcd 0000:00:0f.2: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[4294681.649000] hub 4-0:1.0: USB hub found
[4294681.649000] hub 4-0:1.0: 3 ports detected
[4294682.182000] usb 4-3: new high speed USB device using ehci_hcd and address 3[4294682.599000] usb 3-1: new full speed USB device using ohci_hcd and address 2[4294682.697000] hub 3-1:1.0: USB hub found
[4294682.700000] hub 3-1:1.0: 4 ports detected
[4294683.763000] usbcore: registered new driver hiddev
[4294683.781000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:07.2-1
[4294683.781000] usbcore: registered new driver usbhid
[4294683.781000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
[4294684.896000] ACPI: Fan [FAN1] (on)
[4294684.904000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[4294685.093000] Attempting manual resume
[4294685.094000] swsusp: Suspend partition has wrong signature?
[4294685.135000] kjournald starting.  Commit interval 5 seconds
[4294685.135000] EXT3-fs: mounted filesystem with ordered data mode.
[4294686.239000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294691.299000] Adding 1220900k swap on /dev/hda5.  Priority:-1 extents:1
[4294691.583000] EXT3 FS on hda1, internal journal
[4294699.543000] pnp: Device 00:08 activated.
[4294699.543000] parport: PnPBIOS parport detected.
[4294699.543000] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[4294699.639000] lp0: using parport0 (interrupt-driven).
[4294699.747000] mice: PS/2 mouse device common for all mice
[4294699.922000] ndiswrapper version 1.1 loaded (preempt=no,smp=no)
[4294700.044000] ndiswrapper: driver bcmwl5a (Broadcom,06/25/2004, 3.40.73.0) loaded
[4294700.045000] PCI: Enabling device 0000:00:11.0 (0104 -> 0106)
[4294700.045000] ACPI: PCI Interrupt 0000:00:11.0[A] -> Link [LNKC] -> GSI 3 (level, low) -> IRQ 3
[4294700.055000] ndiswrapper: using irq 3
[4294700.678000] wlan0: ndiswrapper ethernet device 00:11:50:3d:40:c4 using driver bcmwl5a, configuration file 14E4:4320.5.conf
[4294700.679000] wlan0: encryption modes supported: WEP, WPA with TKIP, WPA with AES/CCMP
[4294703.741000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294705.426000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[4294705.426000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=3, sector=0
[4294705.426000] ide: failed opcode was: unknown
[4294705.426000] end_request: I/O error, dev hdb, sector 0
[4294705.426000] Buffer I/O error on device hdb, logical block 0
[4294706.783000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[4294706.783000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=3, sector=0
[4294706.783000] ide: failed opcode was: unknown
[4294706.783000] end_request: I/O error, dev hdb, sector 0
[4294706.783000] Buffer I/O error on device hdb, logical block 0
[4294708.123000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[4294708.123000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=3, sector=0
[4294708.123000] ide: failed opcode was: unknown
[4294708.123000] end_request: I/O error, dev hdb, sector 0
[4294709.706000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[4294709.706000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=3, sector=0
[4294709.706000] ide: failed opcode was: unknown
[4294709.706000] end_request: I/O error, dev hdb, sector 0
[4294710.143000] cdrom: open failed.
[4294710.167000] cdrom: open failed.
[4294713.046000] Linux agpgart interface v0.101 (c) Dave Jones
[4294713.071000] agpgart: Detected an Intel 440BX Chipset.
[4294713.114000] agpgart: AGP aperture is 64M @ 0xec000000
[4294713.337000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294713.351000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294713.351000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294713.981000] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[4294714.367000] Linux video capture interface: v1.00
[4294714.466000] bttv: driver version 0.9.15 loaded
[4294714.466000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[4294714.466000] bttv: Host bridge needs ETBF enabled.
[4294714.476000] bttv: Bt8xx card found (0).
[4294714.476000] PCI: Enabling device 0000:00:0e.0 (0104 -> 0106)
[4294714.477000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[4294714.477000] PCI: setting IRQ 10 as level-triggered
[4294714.477000] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[4294714.477000] bttv0: Bt878 (rev 17) at 0000:00:0e.0, irq: 10, latency: 132, mmio: 0xe8003000
[4294714.477000] bttv0: detected: Leadtek WinFast TV 2000 [card=34], PCI subsystem ID is 107d:6606
[4294714.477000] bttv0: using: Leadtek WinFast 2000/ WinFast 2000 XP [card=34,autodetected]
[4294714.477000] bttv0: enabling ETBF (430FX/VP3 compatibilty)
[4294714.477000] bttv0: gpio: en=00000000, out=00000000 in=00bff707 [init]
[4294714.525000] bttv0: using tuner=5
[4294714.525000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[4294714.528000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[4294714.530000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[4294714.532000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[4294714.572000] tuner 1-0061: chip found @ 0xc2 (bt878 #0 [sw])
[4294714.572000] tuner 1-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[4294714.653000] bttv0: registered device video0
[4294714.655000] bttv0: registered device vbi0
[4294714.658000] bttv0: registered device radio0
[4294714.658000] bttv0: PLL: 28636363 => 35468950 .. ok
[4294714.741000] bttv0: add subdevice "remote0"
[4294715.096000] bt878: AUDIO driver version 0.0.0 loaded
[4294715.106000] bt878: Bt878 AUDIO function found (0).
[4294715.106000] PCI: Enabling device 0000:00:0e.1 (0104 -> 0106)
[4294715.106000] ACPI: PCI Interrupt 0000:00:0e.1[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[4294715.106000] bt878(0): Bt878 (rev 17) at 00:0e.1, irq: 10, latency: 64, memory: 0xe8006000
[4294715.987000] PCI: Enabling device 0000:00:10.0 (0104 -> 0107)
[4294715.987000] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[4294715.987000] Vortex: init.... <6>done.
[4294716.352000] gameport: AU88x0 Gameport is pci0000:00:10.0/gameport0, speed 1807kHz
[4294720.048000] usbcore: registered new driver snd-usb-audio
[4294720.697000] Real Time Clock Driver v1.12
[4294720.905000] input: PC Speaker
[4294721.263000] Floppy drive(s): fd0 is 1.44M
[4294721.277000] FDC 0 is a post-1991 82077
[4294722.264000] ts: Compaq touchscreen protocol output
[4294723.052000] NET: Registered protocol family 17
[4294723.826000] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4294805.865000] ACPI: Power Button (FF) [PWRF]
[4294806.134000] ibm_acpi: ec object not found
[4294814.819000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294814.819000] apm: overridden by ACPI.
[4294818.849000] Bluetooth: Core ver 2.7
[4294818.849000] NET: Registered protocol family 31
[4294818.849000] Bluetooth: HCI device and connection manager initialized
[4294818.849000] Bluetooth: HCI socket layer initialized
[4294818.910000] Bluetooth: L2CAP ver 2.7
[4294818.910000] Bluetooth: L2CAP socket layer initialized
[4294818.958000] Bluetooth: RFCOMM ver 1.5
[4294818.958000] Bluetooth: RFCOMM socket layer initialized
[4294818.958000] Bluetooth: RFCOMM TTY layer initialized
[4294870.870000] NET: Registered protocol family 10
[4294870.871000] Disabled Privacy Extensions on device c02eb280(lo)
[4294870.871000] IPv6 over IPv4 tunneling driver
[4294881.377000] eth0: no IPv6 routers present
[4294881.652000] wlan0: no IPv6 routers present
[4295192.928000] vortex: IRQ fifo error
[4296045.398000] wlan0: no IPv6 routers present
[4297447.619000] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4297458.588000] eth0: no IPv6 routers present
[4297462.294000] wlan0: no IPv6 routers present
[4297495.363000] wlan0: no IPv6 routers present
[4297531.246000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[4297531.246000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=3, sector=0
[4297531.246000] ide: failed opcode was: unknown
[4297531.246000] end_request: I/O error, dev hdb, sector 0
[4297531.246000] Buffer I/O error on device hdb, logical block 0
[4297532.602000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[4297532.602000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=3, sector=0
[4297532.602000] ide: failed opcode was: unknown
[4297532.602000] end_request: I/O error, dev hdb, sector 0
[4297532.602000] Buffer I/O error on device hdb, logical block 0
[4297576.981000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[4297576.981000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=3, sector=0
[4297576.981000] ide: failed opcode was: unknown
[4297576.981000] end_request: I/O error, dev hdb, sector 0
[4297576.981000] Buffer I/O error on device hdb, logical block 0

---

### Post by heftigrat on 2006-01-06
[QUOTE=gosh][4297531.246000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[4297531.246000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=3, sector=0
[4297531.246000] ide: failed opcode was: unknown
[4297531.246000] end_request: I/O error, dev hdb, sector 0
[4297531.246000] Buffer I/O error on device hdb, logical block 0[/QUOTE]

I know there are problems with *NIX reading NTFS.  I don't know all the details, but the part above "error on device hdb, logical block 0" leads me to believe this may be the issue.  The system DOES see hdb, but cannot do anything with it.

Either that, or I would go as far as to say check the jumpers on the hdd's and make sure one is set to master and the other slave.  Otherwise, _shrug_.

---

### Post by gosh on 2006-01-07
[QUOTE=heftigrat]I know there are problems with *NIX reading NTFS.  I don't know all the details, but the part above "error on device hdb, logical block 0" leads me to believe this may be the issue.  The system DOES see hdb, but cannot do anything with it.

Either that, or I would go as far as to say check the jumpers on the hdd's and make sure one is set to master and the other slave.  Otherwise, _shrug_.[/QUOTE]


I did change the jumpers to Master and Slave (they were on CS), but this doesn't make any difference.
Even cfdisk of fdisk dont see them.....](*,)

---

### Post by Amon_Re on 2006-01-07
My friend, i have bad news for you:

```
[4294677.470000] /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
[4294677.493000] hdb: max request size: 128KiB **<< This is the drive**
[4294677.493000] hdb: 240121728 sectors (122942 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(33) **<< Type of the drive & size**
[4294677.494000] hdb: cache flushes supported
[4294677.494000] /dev/ide/host0/bus0/target1/lun0:hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error } **<< This is BAD.**
[4294678.827000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=3, sector=0 **<< More badness**
[4294678.827000] ide: failed opcode was: unknown
[4294678.827000] end_request: I/O error, dev hdb, sector 0
[4294678.827000] Buffer I/O error on device hdb, logical block 0
[4294680.167000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[4294680.167000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=3, sector=0 **<< Second attempt at reading the disk**
[4294680.167000] ide: failed opcode was: unknown
[4294680.167000] end_request: I/O error, dev hdb, sector 0
[4294680.167000] **Buffer I/O error on device hdb, logical block 0**
[4294680.167000] **unable to read partition table**
```

Linux is **unable** to read the partition table and the disk's first logical block, this usually means your drive is dead or dying. Sorry mate

---

### Post by gosh on 2006-01-08
So I even can't format it again?
I will check with the manufacturer Maxtor.

:cry: :cry: :cry: :cry:

---

### Post by Amon_Re on 2006-01-08
[QUOTE=gosh]So I even can't format it again?
I will check with the manufacturer Maxtor.

:cry: :cry: :cry: :cry:[/QUOTE]

It's a maxtor? Then you should download their diagnostics tools and let it analize the hard drive.

Also, installing & running smartmontools might be usefull, aswell as enabling SMART support in the BIOS.

---

### Post by gosh on 2006-01-10
[QUOTE=Amon_Re]It's a maxtor? Then you should download their diagnostics tools and let it analize the hard drive.

Also, installing & running smartmontools might be usefull, aswell as enabling SMART support in the BIOS.[/QUOTE]

Hi, I downloaded Maxtor's tools and burned them on cd on my other desktop, but now I can't mount my cd-rom players :mad: 
I posted another thread on this subject ([http://www.ubuntuforums.org/showthread.php?t=114702)](http://www.ubuntuforums.org/showthread.php?t=114702)).
I first want these to work.
In the meantime I disconnected the maxtor drive from the desktop and I am going to try to install it into my other desktop

---

### Post by gosh on 2006-01-11
I managed to connect the harddisk to my other dualboot (Ubuntu/XP) desktop
I had the same problems in Ubuntu.

In XP however the NTFS partition on that disk was recognized.
I could copy all data to another harddisk.

First Norton PartitionMagic couldn't start because of a error in the ... table.
With Maxtor MaxBlaster I could format the entire disk to a single NTFS partition of 120Mb.
Then I used PartitionMagic to convert it to FAT32.
The disk was then also recognized in Ubuntu

No I only have to reinstall it into the original desktop. 
I expect no trouble there.

So, data saved and harddisk saved:D 

Thanks for thinking with me

---

