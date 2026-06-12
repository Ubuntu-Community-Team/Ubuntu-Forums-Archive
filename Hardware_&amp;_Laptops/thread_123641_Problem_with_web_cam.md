---
title: "Problem with web cam"
date: 2006-01-30
forum: Hardware &amp; Laptops
---

### Post by raf-it on 2006-01-30
Hello boys i'm a new Ubuntu user

i've installed my webcam usb (Intel Easy Pc Camera)
Following te instruction find here:

[http://doc.ubuntu-fr.org/materiel/webcam_scpa50x#liste_des_cartes_prises_en_charges](http://doc.ubuntu-fr.org/materiel/webcam_scpa50x#liste_des_cartes_prises_en_charges)


Now i've finished and all that i've do it's good because all the results are ok
but now when i try my cam all go in crash (keyboard, mouse,all) 
Pianto

when i try lsusb from terminal says that
> 
Bus 001 Device 002: ID 8086:0110 Intel Corp. Easy PC Camera
Bus 001 Device 001: ID 0000:0000


and with dmesg it says that
> 
ACPI: RSDP (v000 HP-MCD                                ) @ 0x000f6ed0
[4294667.296000] ACPI: RSDT (v001 HP-MCD CK RSDT  0x07130000 PTL  0x01000000) @ 0x040e5a76
[4294667.296000] ACPI: FADT (v001 HP-MCD CK FACP  0x07130000 HP   0x01000000) @ 0x040efb8c
[4294667.296000] ACPI: DSDT (v001 HP-MCD CK DSDT  0x07130000 MSFT 0x0100000c) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x8008
[4294667.296000] Allocating PCI resources starting at 08000000 (gap: 08000000:f7 ff0c00)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda1 ro quiet splash
[4294667.296000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[4294667.296000] mapped APIC to ffffd000 (01101000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 1024 (order: 10, 16384 bytes)
[4294667.296000] Detected 448.174 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294671.130000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[4294671.130000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[4294671.149000] Memory: 121732k/131072k available (1415k kernel code, 8728k res erved, 763k data, 224k init, 0k highmem)
[4294671.149000] Checking if this processor honours the WP bit even in superviso r mode... Ok.
[4294671.149000] Calibrating delay loop... 888.83 BogoMIPS (lpj=444416)
[4294671.169000] Security Framework v1.0.0 initialized
[4294671.169000] SELinux:  Disabled at boot.
[4294671.169000] Mount-cache hash table entries: 512
[4294671.169000] CPU: After generic identify, caps: 0387f9ff 00000000 00000000 0 0000000 00000000 00000000 00000000
[4294671.169000] CPU: After vendor identify, caps: 0387f9ff 00000000 00000000 00 000000 00000000 00000000 00000000
[4294671.169000] CPU: L1 I cache: 16K, L1 D cache: 16K
[4294671.169000] CPU: L2 cache: 256K
[4294671.169000] CPU serial number disabled.
[4294671.169000] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040  00000000 00000000 00000000
[4294671.169000] CPU: Intel Pentium III (Coppermine) stepping 01
[4294671.169000] Enabling fast FPU save and restore... done.
[4294671.169000] Enabling unmasked SIMD FPU exception support... done.
[4294671.169000] Checking 'hlt' instruction... OK.
[4294671.173000] Checking for popad bug... OK.
[4294671.173000] checking if image is initramfs... it is
[4294672.797000] Freeing initrd memory: 4821k freed
[4294672.800000] ACPI: Looking for DSDT in initrd... not found!
[4294673.062000]  not found!
[4294673.133000] ACPI: setting ELCR to 0200 (from 0400)
[4294673.145000] NET: Registered protocol family 16
[4294673.145000] EISA bus registered
[4294673.145000] ACPI: bus type pci registered
[4294673.146000] PCI: PCI BIOS revision 2.10 entry at 0xfd9cb, last bus=1
[4294673.146000] PCI: Using configuration type 1
[4294673.146000] mtrr: v2.0 (20020519)
[4294673.147000] ACPI: Subsystem revision 20050729
[4294673.236000] ACPI: Interpreter enabled
[4294673.236000] ACPI: Using PIC for interrupt routing
[4294673.238000] ACPI: PCI Interrupt Link [LNKA] (IRQs *10)
[4294673.239000] ACPI: PCI Interrupt Link [LNKB] (IRQs *10)
[4294673.240000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 12 14 1 5) *0, disabled.
[4294673.242000] ACPI: PCI Interrupt Link [LNKD] (IRQs *10)
[4294673.243000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294673.243000] PCI: Probing PCI hardware (bus 00)
[4294673.244000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[4294673.244000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[4294673.262000] Boot video device is 0000:01:00.0
[4294673.279000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294673.286000] ACPI: Power Resource [PFDD] (off)
[4294673.293000] burst-mode-ec-10-Aug
[4294673.293000] ACPI: Embedded Controller [EC0] (gpe 9)
[4294673.306000] ACPI: Power Resource [PIDE] (on)
[4294673.311000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[4294673.313000] ACPI: Power Resource [PFAN] (off)
[4294673.314000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294673.314000] pnp: PnP ACPI init
[4294673.337000] pnp: PnP ACPI: found 13 devices
[4294673.337000] PnPBIOS: Disabled by ACPI PNP
[4294673.337000] PCI: Using ACPI for IRQ routing
[4294673.337000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps , post a report
[4294673.343000] audit: initializing netlink socket (disabled)
[4294673.343000] audit: initialized
[4294673.343000] VFS: Disk quotas dquot_6.5.1
[4294673.343000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294673.343000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294673.343000] devfs: boot_options: 0x0
[4294673.343000] Initializing Cryptographic API
[4294673.343000] Limiting direct PCI/PCI transfers.
[4294673.344000] isapnp: Scanning for PnP cards...
[4294673.697000] isapnp: No Plug & Play device found
[4294673.761000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUE] at 0x60,0x64 ir q 1,12
[4294673.772000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294673.773000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294673.773000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ shari ng enabled
[4294673.773000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294673.781000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294673.781000] io scheduler noop registered
[4294673.781000] io scheduler anticipatory registered
[4294673.781000] io scheduler deadline registered
[4294673.781000] io scheduler cfq registered
[4294673.783000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 bl ocksize
[4294673.784000] EISA: Probing bus 0 at eisa.0
[4294673.784000] Cannot allocate resource for EISA slot 3
[4294673.784000] Cannot allocate resource for EISA slot 8
[4294673.784000] EISA: Detected 0 cards.
[4294673.784000] NET: Registered protocol family 2
[4294673.796000] IP: routing cache hash table of 1024 buckets, 8Kbytes
[4294673.796000] TCP established hash table entries: 8192 (order: 4, 65536 bytes )
[4294673.796000] TCP bind hash table entries: 8192 (order: 3, 32768 bytes)
[4294673.796000] TCP: Hash tables configured (established 8192 bind 8192)
[4294673.797000] NET: Registered protocol family 8
[4294673.797000] NET: Registered protocol family 20
[4294673.797000] ACPI wakeup devices:
[4294673.797000]  LID COM1 BAT1 BAT2 PX42
[4294673.797000] ACPI: (supports S0 S1 S2 S3 S4 S4bios S5)
[4294673.798000] Freeing unused kernel memory: 224k freed
[4294673.818000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294673.855000] vga16fb: initializing
[4294673.855000] vga16fb: mapped to 0xc00a0000
[4294673.978000] Console: switching to colour frame buffer device 80x30
[4294673.978000] fb0: VGA16 VGA frame buffer device
[4294675.187000] Capability LSM initialized
[4294675.233000] NET: Registered protocol family 1
[4294675.286000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294675.286000] ide: Assuming 33MHz system bus speed for PIO modes; override wi th idebus=xx
[4294675.286000] ACPI: bus type ide registered
[4294675.303000] PIIX4: IDE controller at PCI slot 0000:00:07.1
[4294675.303000] PIIX4: chipset revision 1
[4294675.303000] PIIX4: not 100% native mode: will probe irqs later
[4294675.303000]     ide0: BM-DMA at 0xfcf0-0xfcf7, BIOS settings: hda:DMA, hdb: pio
[4294675.304000]     ide1: BM-DMA at 0xfcf8-0xfcff, BIOS settings: hdc:DMA, hdd: pio
[4294675.304000] Probing IDE interface ide0...
[4294675.568000] hda: IBM-DARA-212000, ATA DISK drive
[4294676.181000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294676.181000] Probing IDE interface ide1...
[4294676.547000] hdc: TOSHIBA CD-ROM XM-1902B, ATAPI CD/DVD-ROM drive
[4294676.854000] ide1 at 0x170-0x177,0x376 on irq 15
[4294676.855000] Probing IDE interface ide2...
[4294677.368000] Probing IDE interface ide3...
[4294677.881000] Probing IDE interface ide4...
[4294678.394000] Probing IDE interface ide5...
[4294678.922000] hda: max request size: 128KiB
[4294678.963000] hda: 23579136 sectors (12072 MB) w/418KiB Cache, CHS=23392/16/6 3, UDMA(33)
[4294678.963000] hda: cache flushes not supported
[4294678.963000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
[4294679.079000] hdc: ATAPI 24X CD-ROM drive, 128kB Cache
[4294679.079000] Uniform CD-ROM driver Revision: 3.20
[4294680.062000] Attempting manual resume
[4294680.063000] swsusp: Suspend partition has wrong signature?
[4294680.285000] usbcore: registered new driver usbfs
[4294680.285000] usbcore: registered new driver hub
[4294680.290000] USB Universal Host Controller Interface driver v2.2
[4294680.290000] PCI: Enabling device 0000:00:07.2 (0000 -> 0001)
[4294680.292000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
[4294680.292000] PCI: setting IRQ 10 as level-triggered
[4294680.292000] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 10 (l evel, low) -> IRQ 10
[4294680.292000] uhci_hcd 0000:00:07.2: Intel Corporation 82371AB/EB/MB PIIX4 US B
[4294680.354000] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus num ber 1
[4294680.354000] uhci_hcd 0000:00:07.2: irq 10, io base 0x0000fcc0
[4294680.354000] hub 1-0:1.0: USB hub found
[4294680.354000] hub 1-0:1.0: 2 ports detected
[4294680.523000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[4294683.537000] ACPI: Fan [FAN] (off)
[4294683.550000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[4294683.550000] ACPI: Processor [CPU0] (supports 8 throttling states)
[4294683.565000] ACPI: Thermal Zone [THRM] (41 C)
[4294683.815000] Attempting manual resume
[4294683.836000] swsusp: Suspend partition has wrong signature?
[4294683.891000] kjournald starting.  Commit interval 5 seconds
[4294683.891000] EXT3-fs: mounted filesystem with ordered data mode.
[4294686.644000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294694.118000] Adding 361420k swap on /dev/hda5.  Priority:-1 extents:1
[4294694.564000] EXT3 FS on hda1, internal journal
[4294714.446000] parport: PnPBIOS parport detected.
[4294714.446000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTA TE,COMPAT,ECP,DMA]
[4294714.546000] lp0: using parport0 (interrupt-driven).
[4294714.641000] mice: PS/2 mouse device common for all mice
[4294715.392000] input: ImPS/2 Logitech Wheel Mouse on isa0060/serio1
[4294716.413000] ts: Compaq touchscreen protocol output
[4294719.531000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@r edhat.com
[4294721.304000] hdc: packet command error: status=0x51 { DriveReady SeekComplet e Error }
[4294721.304000] hdc: packet command error: error=0x50 { LastFailedSense=0x05 }
[4294721.304000] ide: failed opcode was: unknown
[4294721.304000] cdrom: open failed.
[4294724.641000] Linux agpgart interface v0.101 (c) Dave Jones
[4294724.675000] agpgart: Detected an Intel 440BX Chipset.
[4294724.739000] agpgart: AGP aperture is 64M @ 0xe0000000
[4294725.060000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294725.082000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294725.082000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294725.436000] Linux Kernel Card Services
[4294725.436000]   options:  [pci] [cardbus] [pm]
[4294725.487000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[4294725.487000] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [LNKA] -> GSI 10 (l evel, low) -> IRQ 10
[4294725.487000] Yenta: CardBus bridge found at 0000:00:04.0 [103c:000a]
[4294725.488000] Yenta: Enabling burst memory read transactions
[4294725.488000] Yenta: Using INTVAL to route CSC interrupts to PCI
[4294725.488000] Yenta: Routing CardBus interrupts to PCI
[4294725.488000] Yenta TI: socket 0000:00:04.0, mfunc 0x01021702, devctl 0x66
[4294725.709000] Yenta: ISA IRQ mask 0x0838, PCI irq 10
[4294725.709000] Socket status: 30000010
[4294725.759000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[4294725.759000] ACPI: PCI Interrupt 0000:00:04.1 -> Link [LNKB] -> GSI 10 (l evel, low) -> IRQ 10
[4294725.759000] Yenta: CardBus bridge found at 0000:00:04.1 [103c:000a]
[4294725.759000] Yenta: Using INTVAL to route CSC interrupts to PCI
[4294725.759000] Yenta: Routing CardBus interrupts to PCI
[4294725.759000] Yenta TI: socket 0000:00:04.1, mfunc 0x01021702, devctl 0x66
[4294725.980000] Yenta: ISA IRQ mask 0x0838, PCI irq 10
[4294725.980000] Socket status: 30000006
[4294728.326000] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[4294729.170000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNKD] -> GSI 10 (l evel, low) -> IRQ 10
[4294729.760000] es1968: clocking to 48000
[4294733.095000] Linux video capture interface: v1.00
[4294733.137000] drivers/usb/media/spca5xx/spca5xx-core.c: USB SPCA5XX camera fo und. Type Intel Easy PC Camera CS110 (SPCA508+PB100)
[4294733.303000] usbcore: registered new driver spca5xx
[4294733.303000] drivers/usb/media/spca5xx/spca5xx-core.c: spca5xx driver 00.57. 02 registered
[4294733.977000] Real Time Clock Driver v1.12
[4294734.326000] input: PC Speaker
[4294735.028000] Floppy drive(s): fd0 is 1.44M
[4294735.042000] FDC 0 is a post-1991 82077
[4294740.176000] ACPI: AC Adapter [ACAD] (on-line)
[4294740.364000] ACPI: Battery Slot [BAT1] (battery present)
[4294740.364000] ACPI: Battery Slot [BAT2] (battery absent)
[4294740.447000] ACPI: Power Button (FF) [PWRF]
[4294740.447000] ACPI: Lid Switch [LID]
[4294740.866000] ibm_acpi: ec object not found
[4294741.331000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[4294765.843000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294765.843000] apm: overridden by ACPI.
[4294769.990000] cs: IO port probe 0x100-0x4ff: excluding 0x4d0-0x4d7
[4294769.991000] cs: IO port probe 0x100-0x4ff: excluding 0x4d0-0x4d7
[4294769.993000] cs: IO port probe 0xc00-0xcf7: clean.
[4294769.993000] cs: IO port probe 0xc00-0xcf7: clean.
[4294769.994000] cs: IO port probe 0xa00-0xaff: clean.
[4294769.995000] cs: IO port probe 0xa00-0xaff: clean.
[4294769.997000] cs: memory probe 0xa0000000-0xa0ffffff: clean.
[4294771.551000] Bluetooth: Core ver 2.7
[4294771.551000] NET: Registered protocol family 31
[4294771.551000] Bluetooth: HCI device and connection manager initialized
[4294771.551000] Bluetooth: HCI socket layer initialized
[4294771.613000] Bluetooth: L2CAP ver 2.7
[4294771.613000] Bluetooth: L2CAP socket layer initialized
[4294771.677000] Bluetooth: RFCOMM ver 1.5
[4294771.677000] Bluetooth: RFCOMM socket layer initialized
[4294771.677000] Bluetooth: RFCOMM TTY layer initialized
[4294773.096000] eth%d: MII link partner: 01e1
[4294773.096000] eth%d: MII selected
[4294773.117000] eth%d: media 100BaseT, silicon revision 5
[4294773.122000] eth0: Xircom: port 0x300, irq 3, hwaddr 00:10:A4:FE:90:C7
[4294773.270000] ttyS3 at I/O 0x2e8 (irq = 3) is a 16550A
[4294776.472000] eth0: MII link partner: 01e1
[4294776.472000] eth0: MII selected
[4294776.493000] eth0: media 100BaseT, silicon revision 5
[4294778.779000] NET: Registered protocol family 10
[4294778.779000] Disabled Privacy Extensions on device c02eb280(lo)
[4294778.780000] IPv6 over IPv4 tunneling driver
[4294789.557000] eth0: no IPv6 routers present
[4294992.782000] atkbd.c: Unknown key released (translated set 2, code 0xaa on i sa0060/serio0).
[4294992.782000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4294992.884000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on is a0060/serio0).
[4294992.884000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295894.857000] usb 1-1: USB disconnect, address 2
[4295919.273000] usb 1-1: new full speed USB device using uhci_hcd and address 3
[4295919.403000] drivers/usb/media/spca5xx/spca5xx-core.c: USB SPCA5XX camera fo und. Type Intel Easy PC Camera CS110 (SPCA508+PB100)


what can i do?

---

