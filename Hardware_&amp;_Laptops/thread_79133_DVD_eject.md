---
title: "DVD eject"
date: 2005-10-19
forum: Hardware &amp; Laptops
---

### Post by Jad on 2005-10-19
I have problem in ejecting my DVD/CD
it just ait eject, and I do reboot to eject it 

```

jad@madi:~$ eject -v
eject: using default device `cdrom'
eject: device name is `cdrom'
eject: expanded name is `/dev/cdrom'
eject: `/dev/cdrom' is a link to `/dev/hdc'
eject: `/dev/hdc' is not mounted
eject: `/dev/hdc' is not a mount point
eject: `/dev/hdc' is a multipartition device
eject: trying to eject `/dev/hdc' using CD-ROM eject command
eject: CD-ROM eject command failed
eject: trying to eject `/dev/hdc' using SCSI commands
eject: SCSI eject failed
eject: trying to eject `/dev/hdc' using floppy eject command
eject: floppy eject command failed
eject: trying to eject `/dev/hdc' using tape offline command
eject: tape offline command failed
eject: unable to eject, last error: Invalid argument
```

Please advise

---

### Post by Jad on 2005-10-19
I had to reboot to eject my DVD and I got this error in an infinite loop
jad@madi:~$ uname -a
Linux madi 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686 GNU/Linux

```

failed opcode was: unknown
drive not ready for command
ATAPI reset complete

```

Here is my dmesg
```

.296000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 767MB LOWMEM available.
[4294667.296000] On node 0 totalpages: 196592
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:1
[4294667.296000]   Normal zone: 192496 pages, LIFO batch:31
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:1
[4294667.296000] DMI 2.3 present.
[4294667.296000] ACPI: RSDP (v000 JETWAY                                ) @ 0x000f7210
[4294667.296000] ACPI: RSDT (v001 JETWAY AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x2fff3000
[4294667.296000] ACPI: FADT (v001 JETWAY AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x2fff3040
[4294667.296000] ACPI: DSDT (v001 JETWAY AWRDACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x1008
[4294667.296000] Allocating PCI resources starting at 30000000 (gap: 30000000:cec00000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda1 ro quiet splash
[4294667.296000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[4294667.296000] mapped APIC to ffffd000 (01603000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[4294667.296000] Detected 2013.833 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294670.158000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[4294670.160000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294670.183000] Memory: 770948k/786368k available (1415k kernel code, 14832k reserved, 763k data, 224k init, 0k highmem)
[4294670.183000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294670.183000] Calibrating delay loop... 3997.69 BogoMIPS (lpj=1998848)
[4294670.205000] Security Framework v1.0.0 initialized
[4294670.205000] SELinux:  Disabled at boot.
[4294670.205000] Mount-cache hash table entries: 512
[4294670.205000] CPU: After generic identify, caps: bfebf9ff 00000000 00000000 00000000 00004400 00000000 00000000
[4294670.205000] CPU: After vendor identify, caps: bfebf9ff 00000000 00000000 00000000 00004400 00000000 00000000
[4294670.205000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[4294670.205000] CPU: L2 cache: 512K
[4294670.205000] CPU: After all inits, caps: bfebf9ff 00000000 00000000 00000080 00004400 00000000 00000000
[4294670.205000] CPU: Intel(R) Pentium(R) 4 CPU 2.66GHz stepping 09
[4294670.205000] Enabling fast FPU save and restore... done.
[4294670.205000] Enabling unmasked SIMD FPU exception support... done.
[4294670.205000] Checking 'hlt' instruction... OK.
[4294670.209000] Checking for popad bug... OK.
[4294670.209000] checking if image is initramfs... it is
[4294670.771000] Freeing initrd memory: 5173k freed
[4294670.777000] ACPI: Looking for DSDT in initrd... not found!
[4294670.836000]  not found!
[4294670.845000] ACPI: setting ELCR to 0200 (from 0e20)
[4294670.849000] NET: Registered protocol family 16
[4294670.849000] EISA bus registered
[4294670.849000] ACPI: bus type pci registered
[4294670.855000] PCI: PCI BIOS revision 2.10 entry at 0xfb3c0, last bus=1
[4294670.855000] PCI: Using configuration type 1
[4294670.855000] mtrr: v2.0 (20020519)
[4294670.855000] ACPI: Subsystem revision 20050729
[4294670.869000] ACPI: Interpreter enabled
[4294670.869000] ACPI: Using PIC for interrupt routing
[4294670.869000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294670.869000] PCI: Probing PCI hardware (bus 00)
[4294670.869000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[4294670.869000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[4294670.872000] Uncovering SIS961 that hid as a SIS503 (compatible=1)
[4294670.872000] Enabling SiS 96x SMBus.
[4294670.873000] Boot video device is 0000:01:00.0
[4294670.902000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294670.904000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *9 10 11 14 15)
[4294670.904000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 14 15)
[4294670.904000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11 14 15)
[4294670.905000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 14 15)
[4294670.905000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 9 10 11 14 15)
[4294670.905000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 9 10 11 14 15)
[4294670.906000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
[4294670.906000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 *10 11 14 15)
[4294670.910000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294670.910000] pnp: PnP ACPI init
[4294670.915000] pnp: PnP ACPI: found 13 devices
[4294670.915000] PnPBIOS: Disabled by ACPI PNP
[4294670.915000] PCI: Using ACPI for IRQ routing
[4294670.915000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294670.952000] audit: initializing netlink socket (disabled)
[4294670.952000] audit: initialized
[4294670.952000] VFS: Disk quotas dquot_6.5.1
[4294670.952000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294670.952000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294670.952000] devfs: boot_options: 0x0
[4294670.952000] Initializing Cryptographic API
[4294670.952000] isapnp: Scanning for PnP cards...
[4294671.306000] isapnp: No Plug & Play device found
[4294671.327000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[4294671.327000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294671.327000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294671.327000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
[4294671.327000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294671.327000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294671.329000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294671.330000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294671.330000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[4294671.330000] PCI: setting IRQ 11 as level-triggered
[4294671.330000] ACPI: PCI Interrupt 0000:00:11.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[4294671.331000] io scheduler noop registered
[4294671.331000] io scheduler anticipatory registered
[4294671.331000] io scheduler deadline registered
[4294671.331000] io scheduler cfq registered
[4294671.331000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294671.332000] EISA: Probing bus 0 at eisa.0
[4294671.332000] Cannot allocate resource for EISA slot 1
[4294671.332000] EISA: Detected 0 cards.
[4294671.332000] NET: Registered protocol family 2
[4294671.342000] IP: routing cache hash table of 8192 buckets, 64Kbytes
[4294671.342000] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[4294671.344000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[4294671.345000] TCP: Hash tables configured (established 131072 bind 65536)
[4294671.345000] NET: Registered protocol family 8
[4294671.345000] NET: Registered protocol family 20
[4294671.345000] ACPI wakeup devices: 
[4294671.345000] PCI0 USB0 USB1 AMR0 UAR1 UAR2 PS2M PS2K 
[4294671.345000] ACPI: (supports S0 S1 S4 S5)
[4294671.346000] Freeing unused kernel memory: 224k freed
[4294671.366000] vga16fb: initializing
[4294671.366000] vga16fb: mapped to 0xc00a0000
[4294671.499000] Console: switching to colour frame buffer device 80x30
[4294671.499000] fb0: VGA16 VGA frame buffer device
[4294671.510000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294672.631000] Capability LSM initialized
[4294672.646000] NET: Registered protocol family 1
[4294672.662000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294672.662000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294672.662000] ACPI: bus type ide registered
[4294672.669000] SIS5513: IDE controller at PCI slot 0000:00:02.5
[4294672.669000] SIS5513: chipset revision 208
[4294672.669000] SIS5513: not 100% native mode: will probe irqs later
[4294672.669000] SIS5513: SiS 961 MuTIOL IDE UDMA100 controller
[4294672.669000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[4294672.669000]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:pio
[4294672.669000] Probing IDE interface ide0...
[4294672.933000] hda: ST340014A, ATA DISK drive
[4294673.188000] hdb: QUANTUM FIREBALLlct20 20, ATA DISK drive
[4294673.239000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294673.239000] Probing IDE interface ide1...
[4294673.911000] hdc: SONY DVD RW DRU-810A, ATAPI CD/DVD-ROM drive
[4294674.523000] ide1 at 0x170-0x177,0x376 on irq 15
[4294674.523000] Probing IDE interface ide2...
[4294675.036000] Probing IDE interface ide3...
[4294675.548000] Probing IDE interface ide4...
[4294676.060000] Probing IDE interface ide5...
[4294676.577000] hda: max request size: 1024KiB
[4294676.578000] hda: 78165360 sectors (40020 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[4294676.578000] hda: cache flushes supported
[4294676.578000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
[4294676.615000] hdb: max request size: 128KiB
[4294676.617000] hdb: 39876480 sectors (20416 MB) w/418KiB Cache, CHS=39560/16/63, UDMA(33)
[4294676.617000] hdb: cache flushes not supported
[4294676.617000]  /dev/ide/host0/bus0/target1/lun0: p1
[4294676.629000] hdc: ATAPI 94X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
[4294676.629000] Uniform CD-ROM driver Revision: 3.20
[4294677.030000] Attempting manual resume
[4294677.030000] swsusp: Suspend partition has wrong signature?
[4294677.076000] usbcore: registered new driver usbfs
[4294677.076000] usbcore: registered new driver hub
[4294677.077000] ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[4294677.077000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 5
[4294677.077000] PCI: setting IRQ 5 as level-triggered
[4294677.077000] ACPI: PCI Interrupt 0000:00:02.2[D] -> Link [LNKE] -> GSI 5 (level, low) -> IRQ 5
[4294677.077000] ohci_hcd 0000:00:02.2: Silicon Integrated Systems [SiS] USB 1.0 Controller
[4294677.078000] ohci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 1
[4294677.078000] ohci_hcd 0000:00:02.2: irq 5, io mem 0xe7002000
[4294677.131000] hub 1-0:1.0: USB hub found
[4294677.131000] hub 1-0:1.0: 3 ports detected
[4294677.134000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
[4294677.134000] PCI: setting IRQ 10 as level-triggered
[4294677.134000] ACPI: PCI Interrupt 0000:00:02.3[A] -> Link [LNKH] -> GSI 10 (level, low) -> IRQ 10
[4294677.134000] ohci_hcd 0000:00:02.3: Silicon Integrated Systems [SiS] USB 1.0 Controller (#2)
[4294677.134000] ohci_hcd 0000:00:02.3: new USB bus registered, assigned bus number 2
[4294677.134000] ohci_hcd 0000:00:02.3: irq 10, io mem 0xe7000000
[4294677.187000] hub 2-0:1.0: USB hub found
[4294677.187000] hub 2-0:1.0: 3 ports detected
[4294677.227000] fealnx.c:v2.51 Nov-17-2001
[4294677.228000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[4294677.228000] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[4294677.228000] eth0: 100/10M Ethernet PCI Adapter at 0001e000, 00:e0:50:01:da:6e, IRQ 11.
[4294677.239000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[4294677.239000] 8139cp: pci dev 0000:00:0f.0 (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[4294677.239000] 8139cp: Try the "8139too" driver instead.
[4294677.241000] 8139too Fast Ethernet driver 0.9.27
[4294677.241000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
[4294677.241000] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[4294677.242000] eth1: RealTek RTL8139 at 0xe400, 00:a1:b0:0a:6b:55, IRQ 10
[4294677.242000] eth1:  Identified 8139 chip type 'RTL-8100'
[4294677.377000] usb 2-1: new full speed USB device using ohci_hcd and address 2
[4294679.765000] ACPI: Fan [FAN] (on)
[4294679.770000] ACPI: CPU0 (power states: C1[C1])
[4294679.771000] ACPI: Thermal Zone [THRM] (40 C)
[4294679.963000] Attempting manual resume
[4294679.988000] swsusp: Suspend partition has wrong signature?
[4294679.998000] EXT3-fs: INFO: recovery required on readonly filesystem.
[4294679.998000] EXT3-fs: write access will be enabled during recovery.
[4294681.300000] kjournald starting.  Commit interval 5 seconds
[4294681.301000] EXT3-fs: hda1: orphan cleanup on readonly fs
[4294681.301000] ext3_orphan_cleanup: deleting unreferenced inode 4660422
[4294681.301000] ext3_orphan_cleanup: deleting unreferenced inode 4660418
[4294681.404000] ext3_orphan_cleanup: deleting unreferenced inode 4660396
[4294681.404000] EXT3-fs: hda1: 3 orphan inodes deleted
[4294681.404000] EXT3-fs: recovery complete.
[4294681.412000] EXT3-fs: mounted filesystem with ordered data mode.
[4294682.511000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294686.676000] Adding 746980k swap on /dev/hda5.  Priority:-1 extents:1
[4294686.983000] EXT3 FS on hda1, internal journal
[4294692.584000] parport: PnPBIOS parport detected.
[4294692.584000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[4294692.674000] lp0: using parport0 (interrupt-driven).
[4294692.711000] mice: PS/2 mouse device common for all mice
[4294693.087000] input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
[4294693.511000] ts: Compaq touchscreen protocol output
[4294696.231000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294698.421000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4294700.395000] Linux agpgart interface v0.101 (c) Dave Jones
[4294700.409000] agpgart: Detected SiS 645 chipset
[4294700.434000] agpgart: AGP aperture is 64M @ 0xe0000000
[4294700.550000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294700.558000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294700.558000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294700.751000] i2c-sis96x version 1.0.0
[4294700.757000] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x1080
[4294701.218000] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 5
[4294701.218000] ACPI: PCI Interrupt 0000:00:02.7[C] -> Link [LNKF] -> GSI 5 (level, low) -> IRQ 5
[4294701.527000] intel8x0_measure_ac97_clock: measured 49926 usecs
[4294701.527000] intel8x0: clocking to 48000
[4294704.217000] Real Time Clock Driver v1.12
[4294704.331000] input: PC Speaker
[4294704.476000] Floppy drive(s): fd0 is 1.44M
[4294704.491000] FDC 0 is a post-1991 82077
[4294707.414000] NET: Registered protocol family 10
[4294707.414000] Disabled Privacy Extensions on device c02eb280(lo)
[4294707.420000] IPv6 over IPv4 tunneling driver
[4294709.537000] ACPI: Power Button (FF) [PWRF]
[4294709.537000] ACPI: Power Button (CM) [PWRB]
[4294709.676000] ibm_acpi: ec object not found
[4294717.010000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[4294717.010000] apm: overridden by ACPI.
[4294718.299000] eth0: no IPv6 routers present
[4294721.406000] Bluetooth: Core ver 2.7
[4294721.406000] NET: Registered protocol family 31
[4294721.406000] Bluetooth: HCI device and connection manager initialized
[4294721.406000] Bluetooth: HCI socket layer initialized
[4294721.550000] Bluetooth: L2CAP ver 2.7
[4294721.550000] Bluetooth: L2CAP socket layer initialized
[4294721.603000] Bluetooth: RFCOMM ver 1.5
[4294721.603000] Bluetooth: RFCOMM socket layer initialized
[4294721.603000] Bluetooth: RFCOMM TTY layer initialized
[4294735.476000] UDF-fs: No VRS found
[4294735.690000] ISO 9660 Extensions: Microsoft Joliet Level 3
[4294735.811000] ISO 9660 Extensions: RRIP_1991A
[4294832.185000] cdrom: This disc doesn't have any tracks I recognize!

```

---

### Post by notanatheist on 2005-10-21
Have you tried "eject /media/cdrom"? Does "mount" show the drive mounted? Have you tried to "umount /dev/hd?" and manually eject the drive?

---

### Post by jvictor on 2005-11-04
Looks like a DMA related prob ..have u enabled DMA for the drive ?

---

