---
title: "Scanner doesn't work"
date: 2007-05-19
forum: Hardware &amp; Laptops
---

### Post by foerdi on 2007-05-19
Hi,

i installed HP Scanjet 6100


[http://www.sane-project.org/sane-mfgs.html](http://www.sane-project.org/sane-mfgs.html) -> support: complete

but xsane doesn't find any devices

dmesg:
```
susi@dahle:~$ dmesg
[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 0000000033ef0000 end: 0000000033ff0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 0000000033ff0000 size: 0000000000003000 end: 0000000033ff3000 type: 4
[    0.000000] copy_e820_map() start: 0000000033ff3000 size: 000000000000d000 end: 0000000034000000 type: 3
[    0.000000] copy_e820_map() start: 00000000ffff0000 size: 0000000000010000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000033ff0000 (usable)
[    0.000000]  BIOS-e820: 0000000033ff0000 - 0000000033ff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000033ff3000 - 0000000034000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 831MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 212976) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   212976
[    0.000000]   HighMem    212976 ->   212976
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   212976
[    0.000000] On node 0 totalpages: 212976
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1631 pages used for memmap
[    0.000000]   Normal zone: 207249 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI not present or invalid.
[    0.000000] ACPI: RSDP (v000 VIA694                                ) @ 0x000f77d0
[    0.000000] ACPI: RSDT (v001 VIA694 AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x33ff3000
[    0.000000] ACPI: FADT (v001 VIA694 AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x33ff3040
[    0.000000] ACPI: DSDT (v001 VIA694 AWRDACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
[    0.000000] ACPI: Disabling ACPI support
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 34000000:cbff0000)
[    0.000000] Detected 1002.354 MHz processor.
[   26.736428] Built 1 zonelists.  Total pages: 211313
[   26.736437] Kernel command line: root=UUID=8da55e5a-f30d-4b9b-87cb-300be1d71db3 ro quiet splash locale=de_DE
[   26.736789] Local APIC disabled by BIOS -- you can enable it with "lapic"
[   26.736813] mapped APIC to ffffd000 (0168c000)
[   26.736822] Enabling fast FPU save and restore... done.
[   26.736848] Initializing CPU#0
[   26.737007] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   26.738302] Console: colour VGA+ 80x25
[   26.740326] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   26.743403] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   26.801650] Memory: 833344k/851904k available (1992k kernel code, 17932k reserved, 893k data, 328k init, 0k highmem)
[   26.801673] virtual kernel memory layout:
[   26.801676]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   26.801679]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   26.801681]     vmalloc : 0xf4800000 - 0xff7fe000   ( 175 MB)
[   26.801684]     lowmem  : 0xc0000000 - 0xf3ff0000   ( 831 MB)
[   26.801687]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   26.801689]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   26.801692]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   26.801699] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   26.880926] Calibrating delay using timer specific routine.. 2006.95 BogoMIPS (lpj=4013919)
[   26.881021] Security Framework v1.0.0 initialized
[   26.881037] SELinux:  Disabled at boot.
[   26.881075] Mount-cache hash table entries: 512
[   26.881391] CPU: After generic identify, caps: 0183f9ff c1c7f9ff 00000000 00000000 00000000 00000000 00000000
[   26.881409] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   26.881414] CPU: L2 Cache: 256K (64 bytes/line)
[   26.881420] CPU: After all inits, caps: 0183f9ff c1c7f9ff 00000000 00000420 00000000 00000000 00000000
[   26.881442] Compat vDSO mapped to ffffe000.
[   26.881454] Remapping vsyscall page to ffffe000
[   26.881473] Checking 'hlt' instruction... OK.
[   26.896991] SMP alternatives: switching to UP code
[   26.897507] Freeing SMP alternatives: 11k freed
[   26.898025] Early unpacking initramfs... done
[   27.531498] CPU0: AMD Athlon(tm) Processor stepping 02
[   27.531513] SMP motherboard not detected.
[   27.531519] Local APIC not detected. Using dummy APIC emulation.
[   27.531623] Brought up 1 CPUs
[   27.532228] Booting paravirtualized kernel on bare hardware
[   27.532406] Time: 17:50:15  Date: 04/19/107
[   27.532488] NET: Registered protocol family 16
[   27.532764] EISA bus registered
[   27.568620] PCI: PCI BIOS revision 2.10 entry at 0xfb3f0, last bus=1
[   27.568625] PCI: Using configuration type 1
[   27.568629] Setting up standard PCI resources
[   27.576141] ACPI: Interpreter disabled.
[   27.576151] Linux Plug and Play Support v0.97 (c) Adam Belay
[   27.576173] pnp: PnP ACPI: disabled
[   27.576180] PnPBIOS: Scanning system for PnP BIOS support...
[   27.576816] PnPBIOS: Found PnP BIOS installation structure at 0xc00fbed0
[   27.576831] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xbf00, dseg 0xf0000
[   27.578933] PnPBIOS: 16 nodes reported by PnP BIOS; 16 recorded by driver
[   27.579028] PCI: Probing PCI hardware
[   27.579036] PCI: Probing PCI hardware (bus 00)
[   27.579200] Disabling VIA memory write queue (PCI ID 0305, rev 03): [55] 89 & 1f -> 09
[   27.579469] PCI quirk: region 6000-607f claimed by vt82c686 HW-mon
[   27.579476] PCI quirk: region 5000-500f claimed by vt82c686 SMB
[   27.579880] Boot video device is 0000:01:00.0
[   27.582025] PCI: Using IRQ router VIA [1106/0686] at 0000:00:07.0
[   27.616171] NET: Registered protocol family 8
[   27.616176] NET: Registered protocol family 20
[   27.616330] pnp: 00:0b: ioport range 0x260-0x267 has been reserved
[   27.616938] PCI: Bridge: 0000:00:01.0
[   27.616945]   IO window: a000-afff
[   27.616952]   MEM window: e2000000-e3ffffff
[   27.616958]   PREFETCH window: d0000000-dfffffff
[   27.616981] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   27.617040] NET: Registered protocol family 2
[   27.652693] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   27.653296] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   27.659109] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   27.662098] TCP: Hash tables configured (established 131072 bind 65536)
[   27.662107] TCP reno registered
[   27.672788] checking if image is initramfs... it is
[   28.868248] Freeing initrd memory: 6783k freed
[   28.869357] audit: initializing netlink socket (disabled)
[   28.869396] audit(1179597016.316:1): initialized
[   28.869643] VFS: Disk quotas dquot_6.5.1
[   28.869683] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   28.869821] io scheduler noop registered
[   28.869828] io scheduler anticipatory registered
[   28.869833] io scheduler deadline registered
[   28.869855] io scheduler cfq registered (default)
[   28.869882] Applying VIA southbridge workaround.
[   28.869892] PCI: Disabling Via external APIC routing
[   28.870443] isapnp: Scanning for PnP cards...
[   28.957164] isapnp: Card 'SYM 53C416'
[   28.957169] isapnp: 1 Plug & Play card detected total
[   29.015975] Real Time Clock Driver v1.12ac
[   29.016161] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   29.016394] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   29.016810] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   29.018114] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   29.018715] 00:0e: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   29.019278] mice: PS/2 mouse device common for all mice
[   29.020652] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   29.021266] input: Macintosh mouse button emulation as /class/input/input0
[   29.021344] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   29.021354] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   29.021816] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   29.022231] serio: i8042 KBD port at 0x60,0x64 irq 1
[   29.022241] serio: i8042 AUX port at 0x60,0x64 irq 12
[   29.022517] EISA: Probing bus 0 at eisa.0
[   29.022561] Cannot allocate resource for EISA slot 5
[   29.022566] Cannot allocate resource for EISA slot 6
[   29.022581] EISA: Detected 0 cards.
[   29.023043] TCP cubic registered
[   29.023057] NET: Registered protocol family 1
[   29.023103] Using IPI No-Shortcut mode
[   29.023146]   Magic number: 7:13:846
[   29.023405]   hash matches device ptyrf
[   29.023632] Time: tsc clocksource has been installed.
[   29.024631] Freeing unused kernel memory: 328k freed
[   29.041624] input: AT Translated Set 2 keyboard as /class/input/input1
[   30.570166] Capability LSM initialized
[   30.671902] thermal: Unknown symbol acpi_processor_set_thermal_limit
[   31.743345] SCSI subsystem initialized
[   31.753608] libata version 2.20 loaded.
[   31.759284] VP_IDE: IDE controller at PCI slot 0000:00:07.1
[   31.759324] VP_IDE: chipset revision 6
[   31.759328] VP_IDE: not 100% native mode: will probe irqs later
[   31.759347] VP_IDE: VIA vt82c686b (rev 40) IDE UDMA100 controller on pci0000:00:07.1
[   31.759363]     ide0: BM-DMA at 0xb000-0xb007, BIOS settings: hda:DMA, hdb:DMA
[   31.759384]     ide1: BM-DMA at 0xb008-0xb00f, BIOS settings: hdc:DMA, hdd:DMA
[   31.759401] Probing IDE interface ide0...
[   31.793737] usbcore: registered new interface driver usbfs
[   31.793821] usbcore: registered new interface driver hub
[   31.793879] usbcore: registered new device driver usb
[   31.796071] USB Universal Host Controller Interface driver v3.0
[   32.315296] FDC 0 is a post-1991 82077
[   32.657624] hda: TSSTcorpDVD-ROM TS-H352A, ATAPI CD/DVD-ROM drive
[   33.441146] hdb: CR-48XATE, ATAPI CD/DVD-ROM drive
[   33.497572] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   33.498427] Probing IDE interface ide1...
[   33.912915] hdc: ExcelStor Technology CT210, ATA DISK drive
[   34.192705] hdd: ST34321A, ATA DISK drive
[   34.249495] ide1 at 0x170-0x177,0x376 on irq 15
[   34.252528] PCI: setting IRQ 11 as level-triggered
[   34.252537] PCI: Found IRQ 11 for device 0000:00:07.2
[   34.252559] PCI: Sharing IRQ 11 with 0000:00:07.3
[   34.252606] uhci_hcd 0000:00:07.2: UHCI Host Controller
[   34.253167] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[   34.253210] uhci_hcd 0000:00:07.2: irq 11, io base 0x0000b400
[   34.254518] usb usb1: configuration #1 chosen from 1 choice
[   34.254952] hub 1-0:1.0: USB hub found
[   34.254983] hub 1-0:1.0: 2 ports detected
[   34.357665] PCI: Found IRQ 11 for device 0000:00:07.3
[   34.357686] PCI: Sharing IRQ 11 with 0000:00:07.2
[   34.357740] uhci_hcd 0000:00:07.3: UHCI Host Controller
[   34.357806] uhci_hcd 0000:00:07.3: new USB bus registered, assigned bus number 2
[   34.357847] uhci_hcd 0000:00:07.3: irq 11, io base 0x0000b800
[   34.358100] usb usb2: configuration #1 chosen from 1 choice
[   34.358158] hub 2-0:1.0: USB hub found
[   34.358181] hub 2-0:1.0: 2 ports detected
[   34.461570] PCI: setting IRQ 10 as level-triggered
[   34.461581] PCI: Found IRQ 10 for device 0000:00:08.0
[   34.461646] uhci_hcd 0000:00:08.0: UHCI Host Controller
[   34.461705] uhci_hcd 0000:00:08.0: new USB bus registered, assigned bus number 3
[   34.461749] uhci_hcd 0000:00:08.0: irq 10, io base 0x0000c800
[   34.461998] usb usb3: configuration #1 chosen from 1 choice
[   34.462060] hub 3-0:1.0: USB hub found
[   34.462091] hub 3-0:1.0: 2 ports detected
[   34.565615] PCI: Found IRQ 11 for device 0000:00:08.1
[   34.565657] PCI: Sharing IRQ 11 with 0000:00:09.0
[   34.565667] PCI: Sharing IRQ 11 with 0000:00:0e.0
[   34.565694] uhci_hcd 0000:00:08.1: UHCI Host Controller
[   34.565752] uhci_hcd 0000:00:08.1: new USB bus registered, assigned bus number 4
[   34.565792] uhci_hcd 0000:00:08.1: irq 11, io base 0x0000cc00
[   34.566051] usb usb4: configuration #1 chosen from 1 choice
[   34.566114] hub 4-0:1.0: USB hub found
[   34.566140] hub 4-0:1.0: 2 ports detected
[   34.670221] PCI: setting IRQ 9 as level-triggered
[   34.670233] PCI: Found IRQ 9 for device 0000:00:08.2
[   34.670266] PCI: Sharing IRQ 9 with 0000:00:07.5
[   34.670306] ehci_hcd 0000:00:08.2: EHCI Host Controller
[   34.670590] ehci_hcd 0000:00:08.2: new USB bus registered, assigned bus number 5
[   34.670696] ehci_hcd 0000:00:08.2: irq 9, io mem 0xe5001000
[   34.670706] ehci_hcd 0000:00:08.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   34.671955] usb usb5: configuration #1 chosen from 1 choice
[   34.672665] hub 5-0:1.0: USB hub found
[   34.672700] hub 5-0:1.0: 4 ports detected
[   34.776714] HPT370A: IDE controller at PCI slot 0000:00:0e.0
[   34.776753] PCI: Found IRQ 11 for device 0000:00:0e.0
[   34.776780] PCI: Sharing IRQ 11 with 0000:00:08.1
[   34.776795] PCI: Sharing IRQ 11 with 0000:00:09.0
[   34.776826] HPT370A: chipset revision 4
[   34.776839] HPT370A: 100% native mode on irq 11
[   34.776857] HPT37X: no clock data saved by BIOS
[   34.904033] HPT37X: using 33MHz PCI clock
[   34.904146]     ide2: BM-DMA at 0xe400-0xe407, BIOS settings: hde:pio, hdf:pio
[   34.904582]     ide3: BM-DMA at 0xe408-0xe40f, BIOS settings: hdg:pio, hdh:pio
[   34.904606] Probing IDE interface ide2...
[   35.471755] Probing IDE interface ide3...
[   36.039719] PCI: Found IRQ 11 for device 0000:00:09.0
[   36.039750] PCI: Sharing IRQ 11 with 0000:00:08.1
[   36.039770] PCI: Sharing IRQ 11 with 0000:00:0e.0
[   36.039788] 3c59x: Donald Becker and others. www.scyld.com/network/vortex.html
[   36.039805] 0000:00:09.0: 3Com PCI 3c905B Cyclone 100baseTx at f482a000.
[   36.116657] hda: ATAPI 48X DVD-ROM drive, 512kB Cache, UDMA(33)
[   36.116681] Uniform CD-ROM driver Revision: 3.20
[   36.127908] hdb: ATAPI 40X CD-ROM CD-R/RW drive, 16384kB Cache, UDMA(33)
[   36.152169] hdc: max request size: 128KiB
[   36.152184] hdc: 20040450 sectors (10260 MB) w/512KiB Cache, CHS=19881/16/63, UDMA(66)
[   36.152196] hdc: cache flushes not supported
[   36.152303]  hdc: hdc1
[   36.175555] hdd: max request size: 128KiB
[   36.175564] hdd: 8404830 sectors (4303 MB) w/128KiB Cache, CHS=8894/15/63, UDMA(33)
[   36.175575] hdd: cache flushes not supported
[   36.175640]  hdd:hdd: set_multmode: status=0x51 { DriveReady SeekComplete Error }
[   36.311837] hdd: set_multmode: error=0x04 { DriveStatusError }
[   36.311845] ide: failed opcode was: unknown
[   36.324446]  hdd1 hdd2 < hdd5 >
[   37.183993] Attempting manual resume
[   37.184002] swsusp: Resume From Partition 22:69
[   37.184006] PM: Checking swsusp image.
[   37.208814] PM: Resume from disk failed.
[   37.281561] EXT3-fs: INFO: recovery required on readonly filesystem.
[   37.281571] EXT3-fs: write access will be enabled during recovery.
[   39.526977] kjournald starting.  Commit interval 5 seconds
[   39.527025] EXT3-fs: recovery complete.
[   39.560834] EXT3-fs: mounted filesystem with ordered data mode.
[   63.892895] eth0:  setting half-duplex.
[   65.666845] NET: Registered protocol family 17
[   68.563570] parport_pc: VIA 686A/8231 detected
[   68.563580] parport_pc: probing current configuration
[   68.563605] parport_pc: Current parallel port base: 0x378
[   68.563785] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[   68.611478] Linux agpgart interface v0.102 (c) Dave Jones
[   68.827119] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   68.843019] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   68.904670] parport0: Printer, EPSON Stylus Photo EX
[   68.904768] parport_pc: VIA parallel port: io=0x378, irq=7
[   69.045772] agpgart: Detected VIA Twister-K/KT133x/KM133 chipset
[   69.049519] agpgart: AGP aperture is 32M @ 0xe0000000
[   69.091596] input: PC Speaker as /class/input/input2
[   69.845878] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   70.929881] PCI: Found IRQ 9 for device 0000:00:07.5
[   70.929922] PCI: Sharing IRQ 9 with 0000:00:08.2
[   70.930090] PCI: Setting latency timer of device 0000:00:07.5 to 64
[   71.754400] fuse init (API version 7.8)
[   71.796559] lp0: using parport0 (interrupt-driven).
[   71.872933] Adding 240932k swap on /dev/disk/by-uuid/429ec4d0-959d-40fe-9a4d-795d2b4c5189.  Priority:-1 extents:1 across:240932k
[   72.060778] EXT3 FS on hdd1, internal journal
[   72.703063] kjournald starting.  Commit interval 5 seconds
[   72.703301] EXT3 FS on hdc1, internal journal
[   72.703313] EXT3-fs: mounted filesystem with ordered data mode.
[   78.728154] PPP generic driver version 2.4.2
[   78.817426] NET: Registered protocol family 10
[   78.817653] lo: Disabled Privacy Extensions
[   78.817783] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   79.887114] powernow_k7: Unknown symbol acpi_processor_notify_smm
[   79.887189] powernow_k7: Unknown symbol acpi_processor_unregister_performance
[   79.887341] powernow_k7: Unknown symbol acpi_processor_register_performance
[   79.939352] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[   79.939429] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[   79.939602] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[   79.939691] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[   84.396531] [drm] Initialized drm 1.1.0 20060810
[   84.445555] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[   84.787866] ppdev: user-space parallel port driver
[   85.961782] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   85.962031] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[   85.962265] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[   86.334454] [drm] Setting GART location based on new memory map
[   86.334478] [drm] Loading R200 Microcode
[   86.334528] [drm] writeback test succeeded in 1 usecs
[   87.595105] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   88.114587] Bluetooth: Core ver 2.11
[   88.115968] NET: Registered protocol family 31
[   88.115981] Bluetooth: HCI device and connection manager initialized
[   88.115990] Bluetooth: HCI socket layer initialized
[   88.178445] Bluetooth: L2CAP ver 2.8
[   88.178456] Bluetooth: L2CAP socket layer initialized
[   88.367906] Bluetooth: RFCOMM socket layer initialized
[   88.368134] Bluetooth: RFCOMM TTY layer initialized
[   88.368140] Bluetooth: RFCOMM ver 1.8
[  236.802039] eth0:  setting full-duplex.
[  236.803996] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  247.291173] eth0: no IPv6 routers present
[  274.192317] NET: Registered protocol family 24
[  276.156401] ip_tables: (C) 2000-2006 Netfilter Core Team
[  460.562241] ppdev0: registered pardevice
[  460.613148] ppdev0: negotiated back to compatibility mode because user-space forgot
[  460.614665] ppdev0: unregistered pardevice
```

---

