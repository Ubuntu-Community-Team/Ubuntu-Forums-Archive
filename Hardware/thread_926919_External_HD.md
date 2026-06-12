---
title: "External HD"
date: 2008-09-22
forum: Hardware
---

### Post by 4-PackDad on 2008-09-22
Hey;

Newbie Needing More Help.....!

Just bought an SATA 500GB USB External HD.

My system sees the USB device but not the HD. (Can Not Mount)

1. Do not see Gnome Partition Editor under System/Admin.
     -- Is this a "package" I need to download...?

2. Any tricks/tips in working with External HD's with Ubuntu...

Thnx,
Bill

Ubuntu 8.04
Gnome 2.22.3

---

### Post by qstraza on 2008-09-22
plug in the HD and show us whats the output of "dmesg" and "sudo fdisk -l"

---

### Post by 4-PackDad on 2008-09-22
Hey;

Dmesg output is quite long...

[    0.000000] ACPI: FACP 5FFF0030, 0074 (r1 AMIINT SiS735XX     1000 MSFT  100000B)
[    0.000000] ACPI: DSDT 5FFF0100, 33C2 (r1    SiS      735      100 MSFT  100000D)
[    0.000000] ACPI: FACS 5FFF8000, 0040
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] Allocating PCI resources starting at 70000000 (gap: 60000000:9ec00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 390129
[    0.000000] Kernel command line: root=UUID=acc6f814-039a-49d8-8d89-9217b0296ec5 ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffb000 (01c11000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1145.161 MHz processor.
[   22.066636] Console: colour VGA+ 80x25
[   22.066644] console [tty0] enabled
[   22.068133] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   22.071043] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   22.202296] Memory: 1546888k/1572800k available (2177k kernel code, 24700k reserved, 1006k data, 368k init, 655296k highmem)
[   22.202312] virtual kernel memory layout:
[   22.202314]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   22.202316]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   22.202319]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   22.202321]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   22.202323]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   22.202325]       .data : 0xc03204c4 - 0xc041bdc4   (1006 kB)
[   22.202327]       .text : 0xc0100000 - 0xc03204c4   (2177 kB)
[   22.202332] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   22.202432] SLUB: Genslabs=11, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   22.282448] Calibrating delay using timer specific routine.. 2291.85 BogoMIPS (lpj=4583708)
[   22.282522] Security Framework initialized
[   22.282540] SELinux:  Disabled at boot.
[   22.282586] AppArmor: AppArmor initialized
[   22.282596] Failure registering capabilities with primary security module.
[   22.282616] Mount-cache hash table entries: 512
[   22.282921] Initializing cgroup subsys ns
[   22.282930] Initializing cgroup subsys cpuacct
[   22.282952] CPU: After generic identify, caps: 0383f9ff c1c3f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   22.282968] CPU: CLK_CTL MSR was 6003d22f. Reprogramming to 2003d22f
[   22.282975] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   22.282979] CPU: L2 Cache: 256K (64 bytes/line)
[   22.282986] CPU: After all inits, caps: 0383f9ff c1c3f9ff 00000000 00000420 00000000 00000000 00000000 00000000
[   22.283009] Compat vDSO mapped to ffffe000.
[   22.283038] Checking 'hlt' instruction... OK.
[   22.298918] SMP alternatives: switching to UP code
[   22.300918] Freeing SMP alternatives: 11k freed
[   22.301185] Early unpacking initramfs... done
[   22.889342] ACPI: Core revision 20070126
[   22.889499] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   22.891569] ACPI: setting ELCR to 0200 (from 1820)
[   22.897456] CPU0: AMD Athlon(tm) Processor stepping 01
[   22.897468] SMP motherboard not detected.
[   22.897473] Local APIC not detected. Using dummy APIC emulation.
[   22.897586] Brought up 1 CPUs
[   22.897633] CPU0 attaching sched-domain:
[   22.897639]  domain 0: span 01
[   22.897642]   groups: 01
[   22.898068] net_namespace: 64 bytes
[   22.898086] Booting paravirtualized kernel on bare hardware
[   22.898883] Time: 16:13:39  Date: 09/22/08
[   22.898948] NET: Registered protocol family 16
[   22.899363] EISA bus registered
[   22.899382] ACPI: bus type pci registered
[   22.902490] PCI: PCI BIOS revision 2.10 entry at 0xfdb01, last bus=1
[   22.902495] PCI: Using configuration type 1
[   22.902517] Setting up standard PCI resources
[   22.905748] ACPI: EC: Look up EC in DSDT
[   22.911193] ACPI: Interpreter enabled
[   22.911200] ACPI: (supports S0 S1 S4 S5)
[   22.911224] ACPI: Using PIC for interrupt routing
[   22.918855] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   22.919103] Enabling SiS 96x SMBus.
[   22.919810] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   22.922206] ACPI: PCI Interrupt Link [LNKA] (IRQs *11)
[   22.922460] ACPI: PCI Interrupt Link [LNKB] (IRQs *11)
[   22.922607] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 10 12 14 15)
[   22.922752] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 *12 14 15)
[   22.922897] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 12 14 15) *0, disabled.
[   22.923040] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 12 14 15) *0, disabled.
[   22.923184] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 7 10 12 14 15)
[   22.923327] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 *12 14 15)
[   22.923593] ACPI: Power Resource [URP1] (off)
[   22.923639] ACPI: Power Resource [URP2] (off)
[   22.923682] ACPI: Power Resource [FDDP] (off)
[   22.923726] ACPI: Power Resource [LPTP] (off)
[   22.923811] Linux Plug and Play Support v0.97 (c) Adam Belay
[   22.923873] pnp: PnP ACPI init
[   22.923892] ACPI: bus type pnp registered
[   22.929116] pnp: PnP ACPI: found 12 devices
[   22.929122] ACPI: ACPI bus type pnp unregistered
[   22.929131] PnPBIOS: Disabled by ACPI PNP
[   22.929622] PCI: Using ACPI for IRQ routing
[   22.929629] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   22.954337] NET: Registered protocol family 8
[   22.954341] NET: Registered protocol family 20
[   22.954487] AppArmor: AppArmor Filesystem Enabled
[   22.958320] Time: tsc clocksource has been installed.
[   22.997197] PCI: Bridge: 0000:00:01.0
[   22.997201]   IO window: disabled.
[   22.997210]   MEM window: cde00000-cfefffff
[   22.997216]   PREFETCH window: bdc00000-cdcfffff
[   22.997251] NET: Registered protocol family 2
[   23.034490] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   23.035178] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   23.038170] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   23.039670] TCP: Hash tables configured (established 131072 bind 65536)
[   23.039678] TCP reno registered
[   23.050618] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[   23.549262]  it is
[   24.158661] Freeing initrd memory: 7459k freed
[   24.159934] audit: initializing netlink socket (disabled)
[   24.159967] audit(1222100019.960:1): initialized
[   24.160312] highmem bounce pool size: 64 pages
[   24.163964] VFS: Disk quotas dquot_6.5.1
[   24.164107] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   24.164447] io scheduler noop registered
[   24.164452] io scheduler anticipatory registered
[   24.164456] io scheduler deadline registered
[   24.164475] io scheduler cfq registered (default)
[   24.164585] Boot video device is 0000:01:00.0
[   24.165112] isapnp: Scanning for PnP cards...
[   24.518761] isapnp: No Plug & Play device found
[   24.575484] Real Time Clock Driver v1.12ac
[   24.575681] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   24.575888] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   24.576117] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   24.577224] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   24.577829] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   24.579675] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   24.579812] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   24.580008] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   24.580014] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[   24.580212] serio: i8042 KBD port at 0x60,0x64 irq 1
[   24.590041] mice: PS/2 mouse device common for all mice
[   24.590266] EISA: Probing bus 0 at eisa.0
[   24.590313] EISA: Detected 0 cards.
[   24.590320] cpuidle: using governor ladder
[   24.590324] cpuidle: using governor menu
[   24.590610] NET: Registered protocol family 1
[   24.590664] Using IPI No-Shortcut mode
[   24.590735] registered taskstats version 1
[   24.590898]   Magic number: 8:536:237
[   24.590991]   hash matches device ttyv7
[   24.591017]   hash matches device ttysa
[   24.591256] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   24.591260] EDD information not available.
[   24.592140] Freeing unused kernel memory: 368k freed
[   24.621922] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   26.038833] fuse init (API version 7.9)
[   27.289282] usbcore: registered new interface driver usbfs
[   27.289334] usbcore: registered new interface driver hub
[   27.301435] usbcore: registered new device driver usb
[   27.329623] SCSI subsystem initialized
[   27.446607] sis900.c: v1.08.10 Apr. 2 2006
[   27.447035] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 5
[   27.447042] PCI: setting IRQ 5 as level-triggered
[   27.447047] ACPI: PCI Interrupt 0000:00:03.0[A] -> Link [LNKG] -> GSI 5 (level, low) -> IRQ 5
[   27.447986] 0000:00:03.0: Realtek RTL8201 PHY transceiver found at address 1.
[   27.457275] 0000:00:03.0: Using transceiver found at address 1 as default
[   27.461407] eth0: SiS 900 PCI Fast Ethernet at 0xd400, IRQ 5, 00:0a:e6:6b:fb:22
[   27.478733] libata version 3.00 loaded.
[   27.482499] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   27.482921] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 12
[   27.482928] PCI: setting IRQ 12 as level-triggered
[   27.482933] ACPI: PCI Interrupt 0000:00:02.2[D] -> Link [LNKD] -> GSI 12 (level, low) -> IRQ 12
[   27.482964] ohci_hcd 0000:00:02.2: OHCI Host Controller
[   27.483524] ohci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 1
[   27.483559] ohci_hcd 0000:00:02.2: irq 12, io mem 0xcfffe000
[   27.496456] USB Universal Host Controller Interface driver v3.0
[   27.539390] usb usb1: configuration #1 chosen from 1 choice
[   27.539443] hub 1-0:1.0: USB hub found
[   27.539461] hub 1-0:1.0: 3 ports detected
[   27.595456] Floppy drive(s): fd0 is 1.44M
[   27.612874] FDC 0 is a post-1991 82077
[   27.641612] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 12
[   27.641625] ACPI: PCI Interrupt 0000:00:02.3[A] -> Link [LNKH] -> GSI 12 (level, low) -> IRQ 12
[   27.641657] ohci_hcd 0000:00:02.3: OHCI Host Controller
[   27.641720] ohci_hcd 0000:00:02.3: new USB bus registered, assigned bus number 2
[   27.641746] ohci_hcd 0000:00:02.3: irq 12, io mem 0xcffff000
[   27.699257] usb usb2: configuration #1 chosen from 1 choice
[   27.699317] hub 2-0:1.0: USB hub found
[   27.699335] hub 2-0:1.0: 3 ports detected
[   27.801833] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[   27.801845] PCI: setting IRQ 11 as level-triggered
[   27.801850] ACPI: PCI Interrupt 0000:00:13.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   27.801873] uhci_hcd 0000:00:13.0: UHCI Host Controller
[   27.801932] uhci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 3
[   27.801970] uhci_hcd 0000:00:13.0: irq 11, io base 0x0000cc00
[   27.802198] usb usb3: configuration #1 chosen from 1 choice
[   27.802251] hub 3-0:1.0: USB hub found
[   27.802264] hub 3-0:1.0: 2 ports detected
[   27.905586] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[   27.905598] ACPI: PCI Interrupt 0000:00:13.1[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   27.905621] uhci_hcd 0000:00:13.1: UHCI Host Controller
[   27.905674] uhci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 4
[   27.905712] uhci_hcd 0000:00:13.1: irq 11, io base 0x0000d000
[   27.905964] usb usb4: configuration #1 chosen from 1 choice
[   27.906009] hub 4-0:1.0: USB hub found
[   27.906022] hub 4-0:1.0: 2 ports detected
[   28.009454] pata_sis 0000:00:02.5: version 0.5.2
[   28.013371] scsi0 : pata_sis
[   28.015327] scsi1 : pata_sis
[   28.016555] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[   28.016562] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[   28.186343] ata1.00: ATA-5: WDC WD300AB-00BPA1, 18.20D18, max UDMA/100
[   28.186354] ata1.00: 58633344 sectors, multi 16: LBA 
[   28.187756] ata1.01: ATA-6: WDC WD1200JB-00GVA0, 08.02D08, max UDMA/100
[   28.187765] ata1.01: 234441648 sectors, multi 16: LBA48 
[   28.202143] ata1.00: configured for UDMA/100
[   28.218597] ata1.01: configured for UDMA/100
[   28.272960] usb 3-2: new full speed USB device using uhci_hcd and address 2
[   28.447149] usb 3-2: configuration #1 chosen from 1 choice
[   28.692787] usb 4-1: new low speed USB device using uhci_hcd and address 2
[   28.873887] usb 4-1: configuration #1 chosen from 1 choice
[   28.885122] ata2.00: ATAPI: Hewlett-Packard CD-Writer Plus 9300, 1.0c, max UDMA/33
[   28.885163] ata2.01: ATAPI: LITE-ON DVDRW SHW-1635S, YS0R, max UDMA/66
[   29.056954] ata2.00: configured for UDMA/33
[   29.093871] usbcore: registered new interface driver libusual
[   29.112673] Initializing USB Mass Storage driver...
[   29.122892] scsi2 : SCSI emulation for USB Mass Storage devices
[   29.124775] usbcore: registered new interface driver usb-storage
[   29.124790] USB Mass Storage support registered.
[   29.125017] usbcore: registered new interface driver hiddev
[   29.125099] usb-storage: device found at 2
[   29.125103] usb-storage: waiting for device to settle before scanning
[   29.138107] input: Microsoft  Microsoft Basic Optical Mouse v2.0  as /devices/pci0000:00/0000:00:13.1/usb4/4-1/4-1:1.0/input/input2
[   29.152687] input,hidraw0: USB HID v1.11 Mouse [Microsoft  Microsoft Basic Optical Mouse v2.0 ] on usb-0000:00:13.1-1
[   29.152728] usbcore: registered new interface driver usbhid
[   29.152736] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   29.244843] ata2.01: configured for UDMA/66
[   29.245112] scsi 0:0:0:0: Direct-Access     ATA      WDC WD300AB-00BP 18.2 PQ: 0 ANSI: 5
[   29.245993] scsi 0:0:1:0: Direct-Access     ATA      WDC WD1200JB-00G 08.0 PQ: 0 ANSI: 5
[   29.250713] scsi 1:0:0:0: CD-ROM            HP       CD-Writer+ 9300  1.0c PQ: 0 ANSI: 5
[   29.251815] scsi 1:0:1:0: CD-ROM            LITE-ON  DVDRW SHW-1635S  YS0R PQ: 0 ANSI: 5
[   29.256780] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5
[   29.256792] ACPI: PCI Interrupt 0000:00:13.2[C] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[   29.256817] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   29.256906] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 5
[   29.256986] ehci_hcd 0000:00:13.2: irq 5, io mem 0xcfffdf00
[   29.268580] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 0.95, driver 10 Dec 2004
[   29.268855] usb usb5: configuration #1 chosen from 1 choice
[   29.268911] hub 5-0:1.0: USB hub found
[   29.268927] hub 5-0:1.0: 4 ports detected
[   29.292620] usb 3-2: USB disconnect, address 2
[   29.401204] Driver 'sd' needs updating - please use bus_type methods
[   29.402153] sd 0:0:0:0: [sda] 58633344 512-byte hardware sectors (30020 MB)
[   29.402185] sd 0:0:0:0: [sda] Write Protect is off
[   29.402190] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   29.402225] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.402347] sd 0:0:0:0: [sda] 58633344 512-byte hardware sectors (30020 MB)
[   29.402367] sd 0:0:0:0: [sda] Write Protect is off
[   29.402372] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   29.402402] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.402409]  sda: sda1 sda2 <<6>usb 4-1: USB disconnect, address 2
[   29.433862] Driver 'sr' needs updating - please use bus_type methods
[   29.439641]  sda5 >
[   29.439853] sd 0:0:0:0: [sda] Attached SCSI disk
[   29.440009] sd 0:0:1:0: [sdb] 234441648 512-byte hardware sectors (120034 MB)
[   29.440039] sd 0:0:1:0: [sdb] Write Protect is off
[   29.440043] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   29.440079] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.440168] sd 0:0:1:0: [sdb] 234441648 512-byte hardware sectors (120034 MB)
[   29.440187] sd 0:0:1:0: [sdb] Write Protect is off
[   29.440192] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   29.440222] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.440230]  sdb: sdb1 sdb2 < sdb5 >
[   29.643139] sd 0:0:1:0: [sdb] Attached SCSI disk
[   29.662077] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   29.662118] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   29.662153] sr 1:0:0:0: Attached scsi generic sg2 type 5
[   29.662186] scsi 1:0:1:0: Attached scsi generic sg3 type 5
[   29.667013] sr0: scsi3-mmc drive: 32x/32x writer cd/rw xa/form2 cdda tray
[   29.667029] Uniform CD-ROM driver Revision: 3.20
[   29.667154] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   29.673243] sr1: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[   29.673392] sr 1:0:1:0: Attached scsi CD-ROM sr1
[   29.800489] usb 5-2: new high speed USB device using ehci_hcd and address 2
[   29.934320] usb 5-2: configuration #1 chosen from 1 choice
[   29.938520] scsi3 : SCSI emulation for USB Mass Storage devices
[   29.944559] usb-storage: device found at 2
[   29.944570] usb-storage: waiting for device to settle before scanning
[   30.310626] Attempting manual resume
[   30.310636] swsusp: Resume From Partition 8:5
[   30.310639] PM: Checking swsusp image.
[   30.310926] PM: Resume from disk failed.
[   30.368490] kjournald starting.  Commit interval 5 seconds
[   30.368524] EXT3-fs: mounted filesystem with ordered data mode.
[   30.524249] usb 4-1: new low speed USB device using uhci_hcd and address 3
[   30.705526] usb 4-1: configuration #1 chosen from 1 choice
[   30.721759] input: Microsoft  Microsoft Basic Optical Mouse v2.0  as /devices/pci0000:00/0000:00:13.1/usb4/4-1/4-1:1.0/input/input3
[   30.736221] input,hidraw0: USB HID v1.11 Mouse [Microsoft  Microsoft Basic Optical Mouse v2.0 ] on usb-0000:00:13.1-1
[   34.943248] usb-storage: device scan complete
[   39.952035] scsi 3:0:0:0: Direct-Access     WDC WD50 00AAKS-00C8A0    1C02 PQ: 0 ANSI: 2 CCS
[   39.954317] sd 3:0:0:0: [sdc] 976773168 512-byte hardware sectors (500108 MB)
[   39.955093] sd 3:0:0:0: [sdc] Write Protect is off
[   39.955098] sd 3:0:0:0: [sdc] Mode Sense: 00 38 00 00
[   39.955103] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[   39.956219] sd 3:0:0:0: [sdc] 976773168 512-byte hardware sectors (500108 MB)
[   39.956965] sd 3:0:0:0: [sdc] Write Protect is off
[   39.956970] sd 3:0:0:0: [sdc] Mode Sense: 00 38 00 00
[   39.956974] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[   39.956982]  sdc: unknown partition table
[   39.967075] sd 3:0:0:0: [sdc] Attached SCSI disk
[   39.967164] sd 3:0:0:0: Attached scsi generic sg4 type 0
[   46.082970] Linux agpgart interface v0.102
[   46.224058] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x0c00
[   46.284002] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   46.364012] agpgart: Detected SiS chipset - id:1845
[   46.370277] agpgart: AGP aperture is 64M @ 0xd0000000
[   46.432066] sis630_smbus 0000:00:02.0: SIS630 comp. bus not detected, module not inserted.
[   46.500136] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   46.800103] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   47.358526] input: Power Button (FF) as /devices/virtual/input/input5
[   47.367581] ACPI: Power Button (FF) [PWRF]
[   47.367828] input: Sleep Button (CM) as /devices/virtual/input/input6
[   47.383560] ACPI: Sleep Button (CM) [SLPB]
[   48.896562] nvidia: module license 'NVIDIA' taints kernel.
[   51.204216] ACPI: PCI Interrupt 0000:00:02.7[C] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[   51.526399] intel8x0_measure_ac97_clock: measured 55724 usecs
[   51.526409] intel8x0: clocking to 48000
[   51.949247] parport_pc 00:09: reported by Plug and Play ACPI
[   51.949315] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   51.969552] parport0: Printer, Hewlett-Packard HP LaserJet 6MP
[   52.066969] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   52.067890] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.05  Tue Jan 22 19:36:58 PST 2008
[   56.560587] lp0: using parport0 (interrupt-driven).
[   56.662112] Adding 1253028k swap on /dev/sda5.  Priority:-1 extents:1 across:1253028k
[  243.089930] EXT3 FS on sda1, internal journal
[  244.598467] ip_tables: (C) 2000-2006 Netfilter Core Team
[  245.351394] No dock devices found.
[  247.239177] ppdev: user-space parallel port driver
[  247.394466] audit(1222100244.050:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=6912 profile="/usr/sbin/cupsd" namespace="default"
[  247.468574] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  247.468587] apm: overridden by ACPI.
[  249.884850] Bluetooth: Core ver 2.11
[  249.886427] NET: Registered protocol family 31
[  249.886439] Bluetooth: HCI device and connection manager initialized
[  249.886446] Bluetooth: HCI socket layer initialized
[  249.927308] Bluetooth: L2CAP ver 2.9
[  249.927320] Bluetooth: L2CAP socket layer initialized
[  250.015593] Bluetooth: RFCOMM socket layer initialized
[  250.016168] Bluetooth: RFCOMM TTY layer initialized
[  250.016175] Bluetooth: RFCOMM ver 1.8
[  251.715638] eth0: Media Link On 100mbps full-duplex 
[  252.009826] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[  252.010507] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[  252.015345] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[  252.808156] NET: Registered protocol family 17
[  256.049959] NET: Registered protocol family 10
[  256.050889] lo: Disabled Privacy Extensions
[  266.562617] eth0: no IPv6 routers present
[ 3363.745665] ppdev0: registered pardevice
[ 3364.237096] audit(1222103304.969:3): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=8114 profile="/usr/sbin/cupsd" namespace="default"
[ 3365.824842] sysctl table check failed: /dev/parport/parport0/devices/ppdev0/timeslice  Sysctl already exists
[ 3365.824879] Pid: 8123, comm: hpijs Tainted: P        2.6.24-19-generic #1
[ 3365.824923]  [<c01459c5>] set_fail+0x45/0x60
[ 3365.824950]  [<c0145c76>] sysctl_check_table+0x296/0x5b0
[ 3365.824958]  [<c0134228>] sysctl_head_finish+0x18/0x30
[ 3365.824978]  [<c0145c8a>] sysctl_check_table+0x2aa/0x5b0
[ 3365.824984]  [<c0134228>] sysctl_head_finish+0x18/0x30
[ 3365.824998]  [<c0145c8a>] sysctl_check_table+0x2aa/0x5b0
[ 3365.825004]  [<c0134228>] sysctl_head_finish+0x18/0x30
[ 3365.825018]  [<c0145c8a>] sysctl_check_table+0x2aa/0x5b0
[ 3365.825024]  [<c0134228>] sysctl_head_finish+0x18/0x30
[ 3365.825038]  [<c0145c8a>] sysctl_check_table+0x2aa/0x5b0
[ 3365.825045]  [<c0134228>] sysctl_head_finish+0x18/0x30
[ 3365.825058]  [<c0145c8a>] sysctl_check_table+0x2aa/0x5b0
[ 3365.825064]  [<c0132da9>] sysctl_set_parent+0x19/0x30
[ 3365.825078]  [<c01345d0>] register_sysctl_table+0x50/0xa0
[ 3365.825088]  [<f8a9990e>] parport_device_proc_register+0xae/0xe0 [parport]
[ 3365.825116]  [<f8a97e29>] parport_register_device+0x139/0x260 [parport]
[ 3365.825137]  [<f8bd8765>] pp_ioctl+0x445/0x830 [ppdev]
[ 3365.825147]  [<f8bd8240>] pp_irq+0x0/0x50 [ppdev]
[ 3365.825164]  [<c019e048>] do_ioctl+0x78/0x90
[ 3365.825179]  [<c019e28e>] vfs_ioctl+0x22e/0x2b0
[ 3365.825186]  [<c01900ce>] do_sys_open+0xbe/0xe0
[ 3365.825198]  [<c019e366>] sys_ioctl+0x56/0x70
[ 3365.825208]  [<c01043c2>] sysenter_past_esp+0x6b/0xa9
[ 3365.825263]  =======================
[ 3365.825269] ppdev0: registered pardevice
[ 3388.849583] ppdev0: unregistered pardevice
[ 3400.610511] ppdev0: unregistered pardevice
[ 7005.213999] usb 5-2: USB disconnect, address 2
[ 7060.542374] usb 5-2: new high speed USB device using ehci_hcd and address 4
[ 7060.676763] usb 5-2: configuration #1 chosen from 1 choice
[ 7060.732314] scsi4 : SCSI emulation for USB Mass Storage devices
[ 7060.738717] usb-storage: device found at 4
[ 7060.738732] usb-storage: waiting for device to settle before scanning
[ 7066.737144] usb-storage: device scan complete
[ 7072.347105] usb 5-2: reset high speed USB device using ehci_hcd and address 4
[ 7072.459071] usb 5-2: device descriptor read/64, error -71
[ 7072.675048] usb 5-2: device descriptor read/64, error -71
[ 7072.835335] usb 5-2: USB disconnect, address 4
[ 7072.835658] scsi 4:0:0:0: Device offlined - not ready after error recovery
[ 7073.078937] usb 5-2: new high speed USB device using ehci_hcd and address 5
[ 7073.190881] usb 5-2: device descriptor read/64, error -71
[ 7073.406843] usb 5-2: device descriptor read/64, error -71
[ 7073.806745] usb 5-2: new high speed USB device using ehci_hcd and address 7
[ 7073.918677] usb 5-2: device descriptor read/64, error -71
[ 7074.134615] usb 5-2: device descriptor read/64, error -71
[ 7074.534494] usb 5-2: new high speed USB device using ehci_hcd and address 9
[ 7074.646472] usb 5-2: device descriptor read/64, error -71
[ 7074.862434] usb 5-2: device descriptor read/64, error -71
[ 7075.262306] usb 5-2: new high speed USB device using ehci_hcd and address 11
[ 7075.374266] usb 5-2: device descriptor read/64, error -71
[ 7075.590194] usb 5-2: device descriptor read/64, error -71
[ 7075.990102] usb 5-2: new high speed USB device using ehci_hcd and address 13
[ 7076.102064] usb 5-2: device descriptor read/64, error -71
[ 7076.318005] usb 5-2: device descriptor read/64, error -71
[ 7076.717888] usb 5-2: new high speed USB device using ehci_hcd and address 15
[ 7076.829860] usb 5-2: device descriptor read/64, error -71
[ 7077.045798] usb 5-2: device descriptor read/64, error -71
[ 7077.445677] usb 5-2: new high speed USB device using ehci_hcd and address 17
[ 7077.557651] usb 5-2: device descriptor read/64, error -71
[ 7077.795572] usb 5-2: configuration #1 chosen from 1 choice
[ 7077.851838] scsi5 : SCSI emulation for USB Mass Storage devices
[ 7077.857957] usb-storage: device found at 17
[ 7077.857973] usb-storage: waiting for device to settle before scanning
[ 7082.856491] usb-storage: device scan complete
[ 7087.865424] scsi 5:0:0:0: Direct-Access     WDC WD50 00AAKS-00C8A0    1C02 PQ: 0 ANSI: 2 CCS
[ 7087.878884] sd 5:0:0:0: [sdc] 976773168 512-byte hardware sectors (500108 MB)
[ 7087.880210] sd 5:0:0:0: [sdc] Write Protect is off
[ 7087.880219] sd 5:0:0:0: [sdc] Mode Sense: 00 38 00 00
[ 7087.880224] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[ 7087.881458] sd 5:0:0:0: [sdc] 976773168 512-byte hardware sectors (500108 MB)
[ 7087.882207] sd 5:0:0:0: [sdc] Write Protect is off
[ 7087.882214] sd 5:0:0:0: [sdc] Mode Sense: 00 38 00 00
[ 7087.882218] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[ 7087.882232]  sdc: unknown partition table
[ 7087.886976] sd 5:0:0:0: [sdc] Attached SCSI disk
[ 7087.887075] sd 5:0:0:0: Attached scsi generic sg4 type 0
belogg@bill-desktop:~$ 

----------------------------------------------------------------------------------

fdsik


Disk /dev/sda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd52f63a7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3493    28057491   83  Linux
/dev/sda2            3494        3649     1253070    5  Extended
/dev/sda5            3494        3649     1253038+  82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1288a812

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2740    22009018+   7  HPFS/NTFS
/dev/sdb2            2741       14593    95209222+   f  W95 Ext'd (LBA)
/dev/sdb5            2741       14593    95209191    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table
belogg@bill-desktop:~$

---

### Post by Nettoyer on 2008-09-22
When I installed Ubuntu originally, I had a USB HDD with a windows partition on it (for my backups, etc..)

mine is located at /media/disk

dunno if this helps?

---

### Post by qstraza on 2008-09-22
well it says that "Disk /dev/sdc doesn't contain a valid partition table"
Whats the type of the partition? NTFS? Probably the best solution is, to format it to FAT, if you dont have anything you dont want to lose on it

---

### Post by 4-PackDad on 2008-09-23
Hey;

It's a Brand New HD...

No partitions or formatting has been done...

Thats what I need to do...

So, since I do not see Gnome Partition Editor under System/Admin
How do I format it as a NTFS...?

Thnx,
Bill

---

### Post by qstraza on 2008-09-23
aha, so
```
sudo cfdisk /dev/sdc
```
And format it into fat.

---

### Post by 4-PackDad on 2008-09-24
Hey;

I gave it a shot...

Here's the out-put...

Still doesn't look like it formatted because my PC still can't see the HD

I like to format NTFS so my Vista Laptop can use it too.

What am I doing wrong...?

Thnx


cfdisk (util-linux-ng 2.13.1)

                              Disk Drive: /dev/sdc
                       Size: 500107862016 bytes, 500.1 GB
             Heads: 255   Sectors per Track: 63   Cylinders: 60801

    Name        Flags      Part Type  FS Type          [Label]        Size (MB)
 ------------------------------------------------------------------------------
    sdc1        Boot        Primary   NTFS                            500105.25











     [Bootable]  [ Delete ]  [  Help  ]  [Maximize]  [ Print  ]
s    [  Quit  ]  [  Type  ]  [ Units  ]  [ Write  ]
                         Wrote partition table to disk
                 Toggle bootable flag of the current partition

---

### Post by qstraza on 2008-09-24
does this work:
```
sudo mkdir /mnt/hdd
sudo mount /dev/sdc1 /mnt/hdd
``` ?

can you see files in /mnt/hdd?

---

### Post by 4-PackDad on 2008-09-24
Ok;

Here the output from those commands...

belogg@bill-desktop:~$ sudo mkdir /mnt/hdd
[sudo] password for belogg: 
belogg@bill-desktop:~$ sudo mount /dev/sdc1 /mnt/hdd
mount: you must specify the filesystem type

Now What...?

---

