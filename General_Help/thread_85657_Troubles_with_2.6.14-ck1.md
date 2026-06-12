---
title: "Troubles with 2.6.14-ck1"
date: 2005-11-03
forum: General Help
---

### Post by drolyk on 2005-11-03
Hi All!
I`ve got isuues with new kernel.
1) I can`t mount my second hard drive.
---
root@c3po:~ # mount /dev/hdb1 /mnt/share2
mount: /dev/hdb1 already mounted or /mnt/share2 busy
---
2) I see a lot of error and warnings on boot up
---
device-mapper: error adding target to table
device-mapper: dm-linear: Device lookup failed
---

I compile kernel (make-kpkg -initrd --revision=ck1 kernel_image) with slightly changed .config from ubuntu kernel package(default codepages, processor type).


Here is my dmesg`s output:
---
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294670.690000] Initializing Cryptographic API
[4294670.690000] vesafb: unrecognized option mtrr
[4294670.694000] vesafb: NVidia Corporation, NV17 () Board, Chip Rev A2 (OEM: NVidia)
[4294670.694000] vesafb: VBE version: 3.0
[4294670.701000] vesafb: protected mode interface info at c000:f310
[4294670.701000] vesafb: pmi: set display start = b00cf355, set palette = b00cf3da
[4294670.701000] vesafb: pmi: ports = b4c3 b503 ba03 c003 c103 c403 c503 c603 c703 c803 c903 cc03 ce03 cf03 d003 d103 d203 d303 d403 d503 da03 ff03 
[4294670.765000] vesafb: VBIOS/hardware supports DDC2 transfers
[4294670.840000]       Display is GTF capable
[4294670.840000] vesafb: monitor limits: vf = 160 Hz, hf = 96 kHz, clk = 250 MHz
[4294670.840000] vesafb: scrolling: ypan using protected mode interface, yres_virtual=1875
[4294670.841000] vesafb: framebuffer at 0xd0000000, mapped to 0xd0880000, using 7500k, total 65536k
[4294670.841000] fb0: VESA VGA frame buffer device
[4294670.869000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[4294670.870000] PNP: PS/2 controller doesn't have AUX irq; using default 12
[4294670.871000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294670.872000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294670.872000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[4294670.872000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294670.872000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294670.873000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294670.873000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294670.873000] io scheduler noop registered
[4294670.873000] io scheduler anticipatory registered
[4294670.873000] io scheduler deadline registered
[4294670.873000] io scheduler cfq registered (default)
[4294670.874000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294670.874000] mice: PS/2 mouse device common for all mice
[4294670.875000] NET: Registered protocol family 2
[4294670.884000] IP route cache hash table entries: 8192 (order: 3, 32768 bytes)
[4294670.884000] TCP established hash table entries: 32768 (order: 5, 131072 bytes)
[4294670.884000] TCP bind hash table entries: 32768 (order: 5, 131072 bytes)
[4294670.885000] TCP: Hash tables configured (established 32768 bind 32768)
[4294670.885000] TCP reno registered
[4294670.885000] TCP bic registered
[4294670.885000] NET: Registered protocol family 8
[4294670.885000] NET: Registered protocol family 20
[4294670.885000] Using IPI Shortcut mode
[4294670.885000] ACPI wakeup devices: 
[4294670.885000] SLPB PCI0 HUB0 USB0 USB1 AC97 UAR1 UAR2 
[4294670.885000] ACPI: (supports S0 S1 S4 S5)
[4294670.886000] Freeing unused kernel memory: 176k freed
[4294670.911000] fbcon: Unknown symbol crc32_le
[4294670.920000] vga16fb: initializing
[4294670.920000] vga16fb: mapped to 0xb00a0000
[4294670.920000] fb1: VGA16 VGA frame buffer device
[4294671.195000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294672.002000] NET: Registered protocol family 1
[4294672.028000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294672.028000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294672.031000] ICH2: IDE controller at PCI slot 0000:00:1f.1
[4294672.031000] ICH2: chipset revision 5
[4294672.031000] ICH2: not 100% native mode: will probe irqs later
[4294672.031000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[4294672.031000]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:pio
[4294672.031000] Probing IDE interface ide0...
[4294672.295000] hda: Maxtor 6Y080P0, ATA DISK drive
[4294672.550000] hdb: WDC WD2000JB-00GVA0, ATA DISK drive
[4294672.602000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294672.602000] Probing IDE interface ide1...
[4294673.274000] hdc: PIONEER DVD-RW DVR-109, ATAPI CD/DVD-ROM drive
[4294673.886000] ide1 at 0x170-0x177,0x376 on irq 15
[4294673.907000] hda: max request size: 128KiB
[4294673.923000] hda: 160086528 sectors (81964 MB) w/7936KiB Cache, CHS=65535/16/63, UDMA(100)
[4294673.923000] hda: cache flushes supported
[4294673.923000]  hda: hda1 hda2 hda3 < hda5 hda6 hda7 hda8 hda9 hda10 >
[4294673.996000] hdb: max request size: 1024KiB
[4294674.180000] hdb: 390721968 sectors (200049 MB) w/8192KiB Cache, CHS=24321/255/63, UDMA(100)
[4294674.182000] hdb: cache flushes supported
[4294674.182000]  hdb: hdb1
[4294674.203000] hdc: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2000kB Cache
[4294674.203000] Uniform CD-ROM driver Revision: 3.20
[4294674.899000] usbcore: registered new driver usbfs
[4294674.900000] usbcore: registered new driver hub
[4294674.902000] USB Universal Host Controller Interface driver v2.3
[4294674.903000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 5
[4294674.903000] PCI: setting IRQ 5 as level-triggered
[4294674.903000] ACPI: PCI Interrupt 0000:00:1f.2[D] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[4294674.903000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[4294674.903000] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[4294674.903000] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[4294674.903000] uhci_hcd 0000:00:1f.2: irq 5, io base 0x0000d000
[4294674.903000] hub 1-0:1.0: USB hub found
[4294674.903000] hub 1-0:1.0: 2 ports detected
[4294675.004000] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 11
[4294675.004000] PCI: setting IRQ 11 as level-triggered
[4294675.004000] ACPI: PCI Interrupt 0000:00:1f.4[C] -> Link [LNK1] -> GSI 11 (level, low) -> IRQ 11
[4294675.004000] PCI: Setting latency timer of device 0000:00:1f.4 to 64
[4294675.004000] uhci_hcd 0000:00:1f.4: UHCI Host Controller
[4294675.004000] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2
[4294675.004000] uhci_hcd 0000:00:1f.4: irq 11, io base 0x0000d400
[4294675.004000] hub 2-0:1.0: USB hub found
[4294675.004000] hub 2-0:1.0: 2 ports detected
[4294675.210000] usb 1-2: new low speed USB device using uhci_hcd and address 2
[4294675.211000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 12
[4294675.211000] PCI: setting IRQ 12 as level-triggered
[4294675.211000] ACPI: PCI Interrupt 0000:02:05.0[A] -> Link [LNKA] -> GSI 12 (level, low) -> IRQ 12
[4294675.211000] 3c59x: Donald Becker and others. [www.scyld.com/network/vortex.html](www.scyld.com/network/vortex.html)
[4294675.211000] 0000:02:05.0: 3Com PCI 3c905C Tornado at 0xc800. Vers LK1.1.19
[4294675.251000] 8139too Fast Ethernet driver 0.9.27
[4294675.252000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[4294675.252000] ACPI: PCI Interrupt 0000:02:06.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[4294675.252000] eth1: RealTek RTL8139 at 0xcc00, 00:40:f4:6d:be:62, IRQ 11
[4294675.252000] eth1:  Identified 8139 chip type 'RTL-8100B/8139D'
[4294675.257000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[4294675.580000] usb 2-1: new full speed USB device using uhci_hcd and address 2
[4294677.293000] usbcore: registered new driver hiddev
[4294677.311000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1f.2-2
[4294677.311000] usbcore: registered new driver usbhid
[4294677.311000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[4294677.995000] ACPI: Fan [FAN] (on)
[4294678.001000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[4294678.001000] ACPI: Processor [CPU0] (supports 2 throttling states)
[4294678.004000] ACPI: Thermal Zone [THRM] (40 C)
[4294678.213000] ReiserFS: hda8: found reiserfs format "3.6" with standard journal
[4294678.650000] ReiserFS: hda8: using ordered data mode
[4294678.664000] ReiserFS: hda8: journal params: device hda8, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[4294678.669000] ReiserFS: hda8: checking transaction log (hda8)
[4294678.697000] ReiserFS: hda8: Using r5 hash to sort names
[4294680.389000] md: md driver 0.90.2 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294680.389000] md: bitmap version 3.39
[4294685.233000] Adding 489972k swap on /dev/hda2.  Priority:-1 extents:1 across:489972k
[4294687.682000] parport: PnPBIOS parport detected.
[4294687.682000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[4294687.784000] lp0: using parport0 (interrupt-driven).
[4294688.287000] it87: Found IT8712F chip at 0x290, revision 5
[4294688.314000] it87-isa 9191-0290: Detected broken BIOS defaults, disabling PWM interface
[4294690.761000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294691.622000] cdrom: open failed.
[4294691.953000] device-mapper: dm-linear: Device lookup failed
[4294691.953000] device-mapper: error adding target to table
[4294691.971000] device-mapper: dm-linear: Device lookup failed
[4294691.971000] device-mapper: error adding target to table
[4294691.976000] device-mapper: dm-linear: Device lookup failed
[4294691.976000] device-mapper: error adding target to table
[4294691.981000] device-mapper: dm-linear: Device lookup failed
[4294691.981000] device-mapper: error adding target to table
[4294691.986000] device-mapper: dm-linear: Device lookup failed
[4294691.986000] device-mapper: error adding target to table
[4294691.991000] device-mapper: dm-linear: Device lookup failed
[4294691.991000] device-mapper: error adding target to table
[4294691.996000] device-mapper: dm-linear: Device lookup failed
[4294691.996000] device-mapper: error adding target to table
[4294692.000000] device-mapper: dm-linear: Device lookup failed
[4294692.001000] device-mapper: error adding target to table
[4294692.015000] device-mapper: dm-linear: Device lookup failed
[4294692.015000] device-mapper: error adding target to table
[4294692.020000] device-mapper: dm-linear: Device lookup failed
[4294692.020000] device-mapper: error adding target to table
[4294692.025000] device-mapper: dm-linear: Device lookup failed
[4294692.025000] device-mapper: error adding target to table
[4294692.030000] device-mapper: dm-linear: Device lookup failed
[4294692.030000] device-mapper: error adding target to table
[4294692.035000] device-mapper: dm-linear: Device lookup failed
[4294692.035000] device-mapper: error adding target to table
[4294692.040000] device-mapper: dm-linear: Device lookup failed
[4294692.040000] device-mapper: error adding target to table
[4294692.045000] device-mapper: dm-linear: Device lookup failed
[4294692.045000] device-mapper: error adding target to table
[4294692.050000] device-mapper: dm-linear: Device lookup failed
[4294692.050000] device-mapper: error adding target to table
[4294692.055000] device-mapper: dm-linear: Device lookup failed
[4294692.055000] device-mapper: error adding target to table
[4294692.060000] device-mapper: dm-linear: Device lookup failed
[4294692.060000] device-mapper: error adding target to table
[4294692.065000] device-mapper: dm-linear: Device lookup failed
[4294692.065000] device-mapper: error adding target to table
[4294692.070000] device-mapper: dm-linear: Device lookup failed
[4294692.070000] device-mapper: error adding target to table
[4294692.075000] device-mapper: dm-linear: Device lookup failed
[4294692.075000] device-mapper: error adding target to table
[4294692.080000] device-mapper: dm-linear: Device lookup failed
[4294692.080000] device-mapper: error adding target to table
[4294692.085000] device-mapper: dm-linear: Device lookup failed
[4294692.085000] device-mapper: error adding target to table
[4294692.090000] device-mapper: dm-linear: Device lookup failed
[4294692.090000] device-mapper: error adding target to table
[4294692.095000] device-mapper: dm-linear: Device lookup failed
[4294692.095000] device-mapper: error adding target to table
[4294692.100000] device-mapper: dm-linear: Device lookup failed
[4294692.100000] device-mapper: error adding target to table
[4294692.105000] device-mapper: dm-linear: Device lookup failed
[4294692.105000] device-mapper: error adding target to table
[4294692.110000] device-mapper: dm-linear: Device lookup failed
[4294692.110000] device-mapper: error adding target to table
[4294692.115000] device-mapper: dm-linear: Device lookup failed
[4294692.115000] device-mapper: error adding target to table
[4294692.120000] device-mapper: dm-linear: Device lookup failed
[4294692.120000] device-mapper: error adding target to table
[4294692.125000] device-mapper: dm-linear: Device lookup failed
[4294692.125000] device-mapper: error adding target to table
[4294692.130000] device-mapper: dm-linear: Device lookup failed
[4294692.130000] device-mapper: error adding target to table
[4294692.507000] ReiserFS: hda10: found reiserfs format "3.6" with standard journal
[4294699.464000] ReiserFS: hda10: using ordered data mode
[4294699.482000] ReiserFS: hda10: journal params: device hda10, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[4294699.486000] ReiserFS: hda10: checking transaction log (hda10)
[4294699.520000] ReiserFS: hda10: Using r5 hash to sort names
[4294701.926000] Linux agpgart interface v0.101 (c) Dave Jones
[4294702.052000] agpgart: Detected an Intel i815 Chipset.
[4294702.090000] agpgart: AGP aperture is 64M @ 0xe0000000
[4294702.386000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294702.507000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294702.507000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294702.699000] hw_random: RNG not detected
[4294702.801000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294702.801000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294704.459000] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[4294705.308000] gameport: EMU10K1 is pci0000:02:01.1/gameport0, io 0xc400, speed 1147kHz
[4294705.470000] Linux video capture interface: v1.00
[4294705.597000] saa7130/34: v4l2 driver version 0.2.14 loaded
[4294705.600000] ACPI: PCI Interrupt 0000:02:03.0[A] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[4294705.600000] saa7134[0]: found at 0000:02:03.0, rev: 1, irq: 5, latency: 32, mmio: 0xe7001000
[4294705.600000] saa7134[0]: subsystem: 1461:9715, board: Avermedia AVerTV Studio 307 [card=45,autodetected]
[4294705.600000] saa7134[0]: board init: gpio is 5e8
[4294705.603000] saa7134[0]: registered input device for IR
[4294705.760000] saa7134[0]: i2c eeprom 00: 61 14 15 97 ff ff ff ff ff ff ff ff ff ff ff ff
[4294705.760000] saa7134[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4294705.760000] saa7134[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4294705.760000] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4294705.776000] tuner 0-0061: chip found @ 0xc2 (saa7134[0])
[4294705.777000] tuner 0-0061: type set to 51 (Philips PAL/SECAM_D (FM 1256 I-H3))
[4294705.798000] tda9885/6/7: chip found @ 0x86
[4294705.815000] saa7134[0]: registered device video0 [v4l2]
[4294705.818000] saa7134[0]: registered device vbi0
[4294705.821000] saa7134[0]: registered device radio0
[4294707.637000] Bluetooth: Core ver 2.7
[4294707.637000] NET: Registered protocol family 31
[4294707.637000] Bluetooth: HCI device and connection manager initialized
[4294707.637000] Bluetooth: HCI socket layer initialized
[4294707.659000] Bluetooth: HCI USB driver ver 2.9
[4294707.679000] usbcore: registered new driver hci_usb
[4294708.837000] Real Time Clock Driver v1.12
[4294708.943000] input: PC Speaker
[4294709.055000] Floppy drive(s): fd0 is 1.44M
[4294709.070000] FDC 0 is a post-1991 82077
[4294710.168000] ts: Compaq touchscreen protocol output
[4294711.619000] ACPI: PCI Interrupt 0000:02:05.0[A] -> Link [LNKA] -> GSI 12 (level, low) -> IRQ 12
---

Is there any solution ?  
:confused:

---

### Post by manuska on 2005-11-03
A solution (three actually) can be found at [http://evms.sourceforge.net/faq.html]("http://evms.sourceforge.net/faq.html")

I used the last one and disabled everyhing -> All partitions mount correctly :-)

---

