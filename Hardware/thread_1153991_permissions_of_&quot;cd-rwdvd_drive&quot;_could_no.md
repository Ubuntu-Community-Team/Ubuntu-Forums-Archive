---
title: "permissions of &quot;cd-rw/dvd drive&quot; could not be determined"
date: 2009-05-09
forum: Hardware
---

### Post by Scott_74 on 2009-05-09
I'm having issues mounting my cd and dvd drives. Neither drive will read a disk but can I burn cd/dvds. Also usb connection to zen creative mp3 player & ipod are not reconised. 

Below is my out from fdisk -l & fstab 

[B]fdisk -l
[/B]
Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008db6f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6079    48829536   83  Linux
/dev/sda2            6080       20023   112005180    5  Extended
/dev/sda5           19836       20023     1510078+  82  Linux swap / Solaris
/dev/sda6            6080       19835   110495007   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbce0bce0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1530    12289693+   b  W95 FAT32
Partition 1 does not end on cylinder boundary.
/dev/sdb2            1531       14853   107016997+  83  Linux
/dev/sdb3           14854       14946      747022+   5  Extended

**fstab**

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a70405b9-be3b-4685-8428-504a190e616b /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/sda6
UUID=13f7c54a-e900-4d98-9946-5d061c309c8d /home           ext3    defaults,relatime        0       2
# /dev/sda5
UUID=30c157a6-7c58-4b77-b420-bb311ac79f8b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 auto ro,noauto,user,exec 0 0
/dev/scd1       /media/cdrom1   udf,iso9660 auto ro,noauto,user,exec 0 0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sdc1    /media/data2    ext3    defaults,relatime    0    0

---

### Post by cybergypsy on 2009-05-09
could you post the output from dmesg after connecting the USB devices and / or putting in a CD/DVD , thanks.

---

### Post by Scott_74 on 2009-05-09
it's long 

[    0.020874] SMP alternatives: switching to UP code
[    0.513407] Freeing SMP alternatives: 18k freed
[    0.513419] ACPI: Core revision 20080926
[    0.518327] ACPI: Checking initramfs for custom DSDT
[    1.007079] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    1.046776] CPU0: AMD Duron(tm)  stepping 01
[    1.048003] Brought up 1 CPUs
[    1.048003] Total of 1 processors activated (2400.06 BogoMIPS).
[    1.048003] CPU0 attaching NULL sched-domain.
[    1.048003] net_namespace: 776 bytes
[    1.048003] Booting paravirtualized kernel on bare hardware
[    1.048003] Time:  8:07:14  Date: 05/09/09
[    1.048003] regulator: core version 0.5
[    1.048003] NET: Registered protocol family 16
[    1.048003] EISA bus registered
[    1.048003] ACPI: bus type pci registered
[    1.048573] PCI: PCI BIOS revision 2.10 entry at 0xfdb01, last bus=2
[    1.048579] PCI: Using configuration type 1 for base access
[    1.051299] ACPI: EC: Look up EC in DSDT
[    1.061440] ACPI: Interpreter enabled
[    1.061457] ACPI: (supports S0 S1 S4 S5)
[    1.061493] ACPI: Using IOAPIC for interrupt routing
[    1.069824] ACPI: No dock devices found.
[    1.069850] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    1.069954] pci 0000:00:00.0: reg 10 32bit mmio: [0xd0000000-0xd7ffffff]
[    1.070112] pci 0000:00:02.0: Enabling SiS 96x SMBus
[    1.070168] pci 0000:00:02.1: reg 20 io port: [0xc00-0xc1f]
[    1.070237] pci 0000:00:02.5: reg 20 io port: [0xff00-0xff0f]
[    1.070306] pci 0000:00:02.7: reg 10 io port: [0xdc00-0xdcff]
[    1.070317] pci 0000:00:02.7: reg 14 io port: [0xd800-0xd87f]
[    1.070360] pci 0000:00:02.7: supports D1 D2
[    1.070365] pci 0000:00:02.7: PME# supported from D3hot D3cold
[    1.070373] pci 0000:00:02.7: PME# disabled
[    1.070403] pci 0000:00:03.0: reg 10 32bit mmio: [0xcefdd000-0xcefddfff]
[    1.070468] pci 0000:00:03.1: reg 10 32bit mmio: [0xcefde000-0xcefdefff]
[    1.070546] pci 0000:00:03.2: reg 10 32bit mmio: [0xcefdf000-0xcefdffff]
[    1.070593] pci 0000:00:03.2: PME# supported from D0 D3hot D3cold
[    1.070600] pci 0000:00:03.2: PME# disabled
[    1.070651] pci 0000:00:04.0: reg 10 io port: [0xd400-0xd4ff]
[    1.070661] pci 0000:00:04.0: reg 14 32bit mmio: [0xcefdc000-0xcefdcfff]
[    1.070695] pci 0000:00:04.0: reg 30 32bit mmio: [0xcefa0000-0xcefbffff]
[    1.070708] pci 0000:00:04.0: supports D1 D2
[    1.070712] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.070718] pci 0000:00:04.0: PME# disabled
[    1.070767] pci 0000:00:09.0: reg 10 32bit mmio: [0xcf000000-0xcfffffff]
[    1.070777] pci 0000:00:09.0: reg 14 32bit mmio: [0xc0000000-0xc7ffffff]
[    1.070787] pci 0000:00:09.0: reg 18 32bit mmio: [0xcdc80000-0xcdcfffff]
[    1.070814] pci 0000:00:09.0: reg 30 32bit mmio: [0xcefe0000-0xceffffff]
[    1.070924] pci 0000:00:01.0: bridge 32bit mmio: [0xcdd00000-0xcdefffff]
[    1.070932] pci 0000:00:01.0: bridge 32bit mmio pref: [0xbd900000-0xbdafffff]
[    1.070945] bus 00 -> node 0
[    1.070958] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.073344] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    1.073588] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 *11 12 14 15)
[    1.073819] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *10 11 12 14 15)
[    1.074059] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 *11 12 14 15)
[    1.074289] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 7 10 11 12 14 15)
[    1.074518] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 *11 12 14 15)
[    1.074750] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    1.074980] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 7 10 11 12 14 15)
[    1.075161] ACPI: Power Resource [URP1] (off)
[    1.075228] ACPI: Power Resource [URP2] (off)
[    1.075304] ACPI: Power Resource [FDDP] (off)
[    1.075368] ACPI: Power Resource [LPTP] (off)
[    1.075525] ACPI: WMI: Mapper loaded
[    1.076109] SCSI subsystem initialized
[    1.076262] libata version 3.00 loaded.
[    1.076392] usbcore: registered new interface driver usbfs
[    1.076435] usbcore: registered new interface driver hub
[    1.076505] usbcore: registered new device driver usb
[    1.076769] PCI: Using ACPI for IRQ routing
[    1.076976] Bluetooth: Core ver 2.13
[    1.076976] NET: Registered protocol family 31
[    1.076976] Bluetooth: HCI device and connection manager initialized
[    1.076976] Bluetooth: HCI socket layer initialized
[    1.076976] NET: Registered protocol family 8
[    1.076976] NET: Registered protocol family 20
[    1.076976] NetLabel: Initializing
[    1.076976] NetLabel:  domain hash size = 128
[    1.076976] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.076976] NetLabel:  unlabeled traffic allowed by default
[    1.076976] AppArmor: AppArmor Filesystem Enabled
[    1.076976] pnp: PnP ACPI init
[    1.076976] ACPI: bus type pnp registered
[    1.084365] pnp: PnP ACPI: found 11 devices
[    1.084373] ACPI: ACPI bus type pnp unregistered
[    1.084382] PnPBIOS: Disabled by ACPI PNP
[    1.084416] system 00:01: ioport range 0x290-0x297 has been reserved
[    1.084422] system 00:01: ioport range 0x480-0x48f has been reserved
[    1.084426] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    1.084431] system 00:01: ioport range 0xc00-0xc1f has been reserved
[    1.084436] system 00:01: ioport range 0x3f0-0x3f1 has been reserved
[    1.084444] system 00:01: iomem range 0xfee00000-0xfeefffff could not be reserved
[    1.119373] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    1.119379] pci 0000:00:01.0:   IO window: disabled
[    1.119389] pci 0000:00:01.0:   MEM window: 0xcdd00000-0xcdefffff
[    1.119396] pci 0000:00:01.0:   PREFETCH window: 0x000000bd900000-0x000000bdafffff
[    1.119422] bus: 00 index 0 io port: [0x00-0xffff]
[    1.119426] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    1.119430] bus: 01 index 0 mmio: [0x0-0x0]
[    1.119433] bus: 01 index 1 mmio: [0xcdd00000-0xcdefffff]
[    1.119437] bus: 01 index 2 mmio: [0xbd900000-0xbdafffff]
[    1.119441] bus: 01 index 3 mmio: [0x0-0x0]
[    1.119475] NET: Registered protocol family 2
[    1.119750] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    1.120278] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    1.120689] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    1.121155] TCP: Hash tables configured (established 16384 bind 16384)
[    1.121162] TCP reno registered
[    1.121444] NET: Registered protocol family 1
[    1.121730] checking if image is initramfs... it is
[    1.620083] Switched to high resolution mode on CPU 0
[    2.221845] Freeing initrd memory: 7382k freed
[    2.222115] cpufreq: No nForce2 chipset.
[    2.222406] audit: initializing netlink socket (disabled)
[    2.222455] type=2000 audit(1241856435.220:1): initialized
[    2.235541] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    2.238277] VFS: Disk quotas dquot_6.5.1
[    2.238442] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.239769] fuse init (API version 7.10)
[    2.239963] msgmni has been set to 994
[    2.240565] alg: No test for stdrng (krng)
[    2.240602] io scheduler noop registered
[    2.240606] io scheduler anticipatory registered
[    2.240610] io scheduler deadline registered
[    2.240689] io scheduler cfq registered (default)
[    2.272064] pci 0000:00:09.0: Boot video device
[    2.278683] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.278704] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.278968] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    2.278975] ACPI: Power Button (FF) [PWRF]
[    2.279072] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    2.279077] ACPI: Power Button (CM) [PWRB]
[    2.279166] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    2.279178] ACPI: Sleep Button (CM) [SLPB]
[    2.279494] processor ACPI_CPU:00: registered as cooling_device0
[    2.283902] isapnp: Scanning for PnP cards...
[    2.637776] isapnp: No Plug & Play device found
[    2.640201] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.640368] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.640936] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.642451] brd: module loaded
[    2.643097] loop: module loaded
[    2.643354] Fixed MDIO Bus: probed
[    2.643368] PPP generic driver version 2.4.2
[    2.643527] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    2.643603] Driver 'sd' needs updating - please use bus_type methods
[    2.643621] Driver 'sr' needs updating - please use bus_type methods
[    2.644623] pata_sis 0000:00:02.5: version 0.5.2
[    2.645089] scsi0 : pata_sis
[    2.645397] scsi1 : pata_sis
[    2.646873] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    2.646881] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    2.816449] ata1.00: ATA-7: Hitachi HDS721616PLAT80, P22OA8BA, max UDMA/133
[    2.816456] ata1.00: 321672960 sectors, multi 16: LBA48 
[    2.816695] ata1.01: ATA-7: Maxtor 6Y120P0, YAR41BW0, max UDMA/133
[    2.816700] ata1.01: 240121728 sectors, multi 16: LBA 
[    2.816735] ata1.00: limited to UDMA/33 due to 40-wire cable
[    2.816741] ata1.01: limited to UDMA/33 due to 40-wire cable
[    2.832448] ata1.00: configured for UDMA/33
[    2.848428] ata1.01: configured for UDMA/33
[    3.020264] ata2.00: ATAPI: DVD-RW IDE1108, VER B029, max UDMA/66
[    3.020311] ata2.01: ATAPI: ATAPI   CD-RW 52XMax, 170D, max UDMA/33
[    3.036288] ata2.00: configured for UDMA/66
[    3.052290] ata2.01: configured for UDMA/33
[    3.053528] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HDS72161 P22O PQ: 0 ANSI: 5
[    3.053813] sd 0:0:0:0: [sda] 321672960 512-byte hardware sectors: (164 GB/153 GiB)
[    3.053852] sd 0:0:0:0: [sda] Write Protect is off
[    3.053856] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.053907] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.054084] sd 0:0:0:0: [sda] 321672960 512-byte hardware sectors: (164 GB/153 GiB)
[    3.054115] sd 0:0:0:0: [sda] Write Protect is off
[    3.054119] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.054166] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.054176]  sda: sda1 sda2 < sda5 sda6 >
[    3.080512] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.080657] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.080936] scsi 0:0:1:0: Direct-Access     ATA      Maxtor 6Y120P0   YAR4 PQ: 0 ANSI: 5
[    3.081200] sd 0:0:1:0: [sdb] 240121728 512-byte hardware sectors: (122 GB/114 GiB)
[    3.081239] sd 0:0:1:0: [sdb] Write Protect is off
[    3.081243] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    3.081294] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.081470] sd 0:0:1:0: [sdb] 240121728 512-byte hardware sectors: (122 GB/114 GiB)
[    3.081501] sd 0:0:1:0: [sdb] Write Protect is off
[    3.081505] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    3.081551] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.081561]  sdb: sdb1 sdb2 sdb3 < >
[    3.103163] sd 0:0:1:0: [sdb] Attached SCSI disk
[    3.103289] sd 0:0:1:0: Attached scsi generic sg1 type 0
[    3.103833] scsi 1:0:0:0: CD-ROM            DVDRW    IDE1108          B029 PQ: 0 ANSI: 5
[    3.107059] sr0: scsi3-mmc drive: 1x/40x writer cd/rw xa/form2 cdda tray
[    3.107071] Uniform CD-ROM driver Revision: 3.20
[    3.107368] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.107508] sr 1:0:0:0: Attached scsi generic sg2 type 5
[    3.108604] scsi 1:0:1:0: CD-ROM            ATAPI    CD-RW 52XMax     170D PQ: 0 ANSI: 5
[    3.111472] sr1: scsi3-mmc drive: 52x/52x writer cd/rw xa/form2 cdda tray
[    3.111740] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    3.111853] sr 1:0:1:0: Attached scsi generic sg3 type 5
[    3.112200] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.112267] ehci_hcd 0000:00:03.2: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    3.112338] ehci_hcd 0000:00:03.2: EHCI Host Controller
[    3.112514] ehci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 1
[    3.112590] ehci_hcd 0000:00:03.2: cache line size of 64 is not supported
[    3.112627] ehci_hcd 0000:00:03.2: irq 23, io mem 0xcefdf000
[    3.124015] ehci_hcd 0000:00:03.2: USB 2.0 started, EHCI 1.00
[    3.124191] usb usb1: configuration #1 chosen from 1 choice
[    3.124246] hub 1-0:1.0: USB hub found
[    3.124279] hub 1-0:1.0: 6 ports detected
[    3.124553] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.124640] ohci_hcd 0000:00:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    3.124698] ohci_hcd 0000:00:03.0: OHCI Host Controller
[    3.124826] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 2
[    3.124891] ohci_hcd 0000:00:03.0: irq 20, io mem 0xcefdd000
[    3.182191] usb usb2: configuration #1 chosen from 1 choice
[    3.182257] hub 2-0:1.0: USB hub found
[    3.182284] hub 2-0:1.0: 3 ports detected
[    3.182483] ohci_hcd 0000:00:03.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    3.182536] ohci_hcd 0000:00:03.1: OHCI Host Controller
[    3.182647] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 3
[    3.182704] ohci_hcd 0000:00:03.1: irq 21, io mem 0xcefde000
[    3.238178] usb usb3: configuration #1 chosen from 1 choice
[    3.238232] hub 3-0:1.0: USB hub found
[    3.238259] hub 3-0:1.0: 3 ports detected
[    3.238468] uhci_hcd: USB Universal Host Controller Interface driver
[    3.238693] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    3.239048] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.239067] serio: i8042 AUX port at 0x60,0x64 irq 12
[    3.239371] mice: PS/2 mouse device common for all mice
[    3.239640] rtc_cmos 00:03: RTC can wake from S4
[    3.239725] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    3.239766] rtc0: alarms up to one month, 114 bytes nvram
[    3.239953] device-mapper: uevent: version 1.0.3
[    3.240368] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[    3.240542] device-mapper: multipath: version 1.0.5 loaded
[    3.240549] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.240799] EISA: Probing bus 0 at eisa.0
[    3.240852] EISA: Detected 0 cards.
[    3.240942] cpuidle: using governor ladder
[    3.240946] cpuidle: using governor menu
[    3.242029] TCP cubic registered
[    3.242208] NET: Registered protocol family 10
[    3.243041] lo: Disabled Privacy Extensions
[    3.243630] NET: Registered protocol family 17
[    3.243710] Bluetooth: L2CAP ver 2.11
[    3.243713] Bluetooth: L2CAP socket layer initialized
[    3.243720] Bluetooth: SCO (Voice Link) ver 0.6
[    3.243723] Bluetooth: SCO socket layer initialized
[    3.243873] Bluetooth: RFCOMM socket layer initialized
[    3.243898] Bluetooth: RFCOMM TTY layer initialized
[    3.243903] Bluetooth: RFCOMM ver 1.10
[    3.244066] powernow-k8: Processor cpuid 681 not supported
[    3.244126] Using IPI No-Shortcut mode
[    3.244427] registered taskstats version 1
[    3.244651]   Magic number: 9:579:118
[    3.244867] rtc_cmos 00:03: setting system clock to 2009-05-09 08:07:16 UTC (1241856436)
[    3.244875] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.244879] EDD information not available.
[    3.246480] Freeing unused kernel memory: 532k freed
[    3.246708] Write protecting the kernel text: 4112k
[    3.246778] Write protecting the kernel read-only data: 1524k
[    3.265246] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    4.136360] Floppy drive(s): fd0 is 1.44M
[    4.157680] FDC 0 is a post-1991 82077
[    4.681764] sis900.c: v1.08.10 Apr. 2 2006
[    4.681883] sis900 0000:00:04.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    4.683289] 0000:00:04.0: VIA 6103 PHY transceiver found at address 1.
[    4.694502] 0000:00:04.0: Using transceiver found at address 1 as default
[    4.705387] eth0: SiS 900 PCI Fast Ethernet at 0xd400, IRQ 19, 00:0d:87:37:4f:b7
[    5.598269] PM: Starting manual resume from disk
[    5.598285] PM: Resume from partition 8:5
[    5.598288] PM: Checking hibernation image.
[    5.598721] PM: Resume from disk failed.
[    5.626156] kjournald starting.  Commit interval 5 seconds
[    5.626201] EXT3-fs: mounted filesystem with ordered data mode.
[   12.383217] udev: starting version 141
[   12.621065] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.635003] Linux agpgart interface v0.103
[   12.642378] agpgart-sis 0000:00:00.0: SiS chipset [1039/0746]
[   12.678208] parport_pc 00:0a: reported by Plug and Play ACPI
[   12.678330] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   12.690211] agpgart-sis 0000:00:00.0: AGP aperture is 128M @ 0xd0000000
[   12.814490] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x0c00
[   12.814506] ACPI: I/O resource 0000:00:02.1 [0xc00-0xc1f] conflicts with ACPI region SMRG [0xc00-0xc1f]
[   12.814511] ACPI: Device needs an ACPI driver
[   13.783094] nvidia: module license 'NVIDIA' taints kernel.
[   14.119582] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   14.263535] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   14.512640] Intel ICH 0000:00:02.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   14.745419] psmouse serio1: ID: 10 00 64<4>logips2pp: Detected unknown logitech mouse model 89
[   14.840139] intel8x0_measure_ac97_clock: measured 55269 usecs (2659 samples)
[   14.840150] intel8x0: clocking to 48000
[   14.844012] nvidia 0000:00:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.845809] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.10  Sat Jan 24 19:49:38 PST 2009
[   15.061048] ppdev: user-space parallel port driver
[   15.352892] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input6
[   15.544820] lp0: using parport0 (interrupt-driven).
[   15.955684] Adding 1510068k swap on /dev/sda5.  Priority:-1 extents:1 across:1510068k
[  140.311395] EXT3 FS on sda1, internal journal
[  141.674740] kjournald starting.  Commit interval 5 seconds
[  141.675214] EXT3 FS on sda6, internal journal
[  141.675228] EXT3-fs: mounted filesystem with ordered data mode.
[  142.487582] type=1505 audit(1241856575.739:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2806
[  142.633643] type=1505 audit(1241856575.887:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2810
[  142.634215] type=1505 audit(1241856575.887:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2810
[  142.634479] type=1505 audit(1241856575.887:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2810
[  142.634663] type=1505 audit(1241856575.887:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2810
[  143.006567] type=1505 audit(1241856576.259:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2815
[  143.007391] type=1505 audit(1241856576.259:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2815
[  143.096613] type=1505 audit(1241856576.351:9): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=2819
[  143.176455] type=1505 audit(1241856576.431:10): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2823
[  157.465503] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  157.465512] Bluetooth: BNEP filters: protocol multicast
[  157.494973] Bridge firewalling registered
[  166.748791] eth0: Media Link On 100mbps full-duplex 
[  174.572072] eth0: no IPv6 routers present
[ 2727.521732] UDP: bad checksum. From 67.166.178.220:28524 to 192.168.0.171:51413 ulen 75
[ 4799.865084] UDP: bad checksum. From 67.166.178.220:28524 to 192.168.0.171:51413 ulen 75
[19146.304148] usb 1-3: new high speed USB device using ehci_hcd and address 2
[19146.442242] usb 1-3: configuration #1 chosen from 1 choice
[19319.203922] usb 1-3: USB disconnect, address 2
[20236.798322] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[20236.798338] sr 1:0:0:0: [sr0] Sense Key : Hardware Error [current] 
[20236.798348] sr 1:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[20236.798359] end_request: I/O error, dev sr0, sector 80
[20236.798375] Buffer I/O error on device sr0, logical block 10
[20246.468151] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[20246.468165] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
[20246.468175] sr 1:0:0:0: [sr0] Add. Sense: No seek complete
[20246.468184] end_request: I/O error, dev sr0, sector 80
[20246.468199] Buffer I/O error on device sr0, logical block 10
[20253.525925] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[20253.525941] sr 1:0:0:0: [sr0] Sense Key : Hardware Error [current] 
[20253.525951] sr 1:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[20253.525962] end_request: I/O error, dev sr0, sector 88
[20253.525978] Buffer I/O error on device sr0, logical block 11
[20253.525989] Buffer I/O error on device sr0, logical block 12
[20253.525995] Buffer I/O error on device sr0, logical block 13
[20253.526001] Buffer I/O error on device sr0, logical block 14
[20253.526007] Buffer I/O error on device sr0, logical block 15
[20253.526012] Buffer I/O error on device sr0, logical block 16
[20253.526018] Buffer I/O error on device sr0, logical block 17
[20262.407538] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[20262.407552] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
[20262.407561] sr 1:0:0:0: [sr0] Add. Sense: No seek complete
[20262.407570] end_request: I/O error, dev sr0, sector 80
[20262.407586] Buffer I/O error on device sr0, logical block 10
[20271.120562] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[20271.120577] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
[20271.120587] sr 1:0:0:0: [sr0] Add. Sense: No seek complete
[20271.120595] end_request: I/O error, dev sr0, sector 80
[20271.120611] Buffer I/O error on device sr0, logical block 10
[20279.879730] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[20279.879744] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
[20279.879754] sr 1:0:0:0: [sr0] Add. Sense: No seek complete
[20279.879762] end_request: I/O error, dev sr0, sector 80
[20279.879778] Buffer I/O error on device sr0, logical block 10
[20288.562122] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[20288.562137] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
[20288.562147] sr 1:0:0:0: [sr0] Add. Sense: No seek complete
[20288.562155] end_request: I/O error, dev sr0, sector 80
[20288.562170] Buffer I/O error on device sr0, logical block 10
[20297.927378] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[20297.927394] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
[20297.927403] sr 1:0:0:0: [sr0] Add. Sense: No seek complete
[20297.927412] end_request: I/O error, dev sr0, sector 80
[20297.927428] Buffer I/O error on device sr0, logical block 10
[20306.220652] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[20306.220669] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
[20306.220679] sr 1:0:0:0: [sr0] Add. Sense: No seek complete
[20306.220687] end_request: I/O error, dev sr0, sector 80
[20306.220704] Buffer I/O error on device sr0, logical block 10
[20314.397081] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[20314.397097] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
[20314.397106] sr 1:0:0:0: [sr0] Add. Sense: No seek complete
[20314.397115] end_request: I/O error, dev sr0, sector 80
[20314.397131] Buffer I/O error on device sr0, logical block 10
[20322.798852] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[20322.798869] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
[20322.798879] sr 1:0:0:0: [sr0] Add. Sense: No seek complete
[20322.798887] end_request: I/O error, dev sr0, sector 80
[20322.798902] Buffer I/O error on device sr0, logical block 10
[20911.764696] kjournald starting.  Commit interval 5 seconds
[20911.764742] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[20911.765345] EXT3 FS on sdb2, internal journal
[20911.765359] EXT3-fs: mounted filesystem with ordered data mode.
[21896.534860] ppdev0: registered pardevice
[21896.576791] ppdev0: unregistered pardevice
[21899.544740] ppdev0: registered pardevice
[21899.599698] ppdev0: unregistered pardevice
[21900.828335] ppdev0: registered pardevice
[21900.872658] ppdev0: unregistered pardevice
[26561.531716] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[26561.531732] sr 1:0:0:0: [sr0] Sense Key : Hardware Error [current] 
[26561.531742] sr 1:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[26561.531753] end_request: I/O error, dev sr0, sector 40
[26561.531769] Buffer I/O error on device sr0, logical block 5
[26561.531796] Buffer I/O error on device sr0, logical block 6
[26561.531802] Buffer I/O error on device sr0, logical block 7
[26561.531808] Buffer I/O error on device sr0, logical block 8
[26561.531813] Buffer I/O error on device sr0, logical block 9
[26561.531819] Buffer I/O error on device sr0, logical block 10
[26561.531824] Buffer I/O error on device sr0, logical block 11
[26561.531830] Buffer I/O error on device sr0, logical block 12
[26561.531835] Buffer I/O error on device sr0, logical block 13
[26561.531841] Buffer I/O error on device sr0, logical block 14
[26561.662359] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[26561.662374] sr 1:0:0:0: [sr0] Sense Key : Hardware Error [current] 
[26561.662384] sr 1:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[26561.662395] end_request: I/O error, dev sr0, sector 80
[26561.695888] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[26561.695903] sr 1:0:0:0: [sr0] Sense Key : Hardware Error [current] 
[26561.695913] sr 1:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[26561.695924] end_request: I/O error, dev sr0, sector 80
[26561.767426] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[26561.767441] sr 1:0:0:0: [sr0] Sense Key : Hardware Error [current] 
[26561.767451] sr 1:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[26561.767462] end_request: I/O error, dev sr0, sector 88
[26561.770175] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[26561.770191] sr 1:0:0:0: [sr0] Sense Key : Hardware Error [current] 
[26561.770201] sr 1:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[26561.770211] end_request: I/O error, dev sr0, sector 120
[26561.798035] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[26561.798051] sr 1:0:0:0: [sr0] Sense Key : Hardware Error [current] 
[26561.798061] sr 1:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[26561.798072] end_request: I/O error, dev sr0, sector 80
[26561.830496] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[26561.830512] sr 1:0:0:0: [sr0] Sense Key : Hardware Error [current] 
[26561.830521] sr 1:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[26561.830532] end_request: I/O error, dev sr0, sector 80
[26561.864231] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[26561.864248] sr 1:0:0:0: [sr0] Sense Key : Hardware Error [current] 
[26561.864257] sr 1:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[26561.864268] end_request: I/O error, dev sr0, sector 80
root@sah-desktop:/home/sah#

---

### Post by Scott_74 on 2009-05-09
I get this message when inserting a dvd 

DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)

---

### Post by Scott_74 on 2009-05-09
abit more information on fstab

[mntent]: line 11 in etc/fstab is bad
[mntent]: line 12 in etc/fstab is bad
mount: can't find /media/cdrom0 in /etc/fstab or /etc/mtab

---

### Post by cybergypsy on 2009-05-09
well , /dev/sr0 is being mounted and looks like your DVD drive but is not described in /etc/fstab , it also shows a lot of errors , is the hardware working OK ?

paste in the output from the mount command when you have a DVD in the drive.

---

### Post by Scott_74 on 2009-05-09
mount 

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/sda6 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/sah/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=sah)
/dev/sdb2 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)

---

### Post by cybergypsy on 2009-05-09
as a test I would remove the two entries for /dev/scd0 and /dev/scd1
and then replace then with just one entry of /dev/sr0 for now

perhaps disconnect one drive altogether and concentrate on the remaining drive first.

---

### Post by Scott_74 on 2009-05-10
cdrom mounts and read disk after making the adjustment above. The dvd/rw drive still has the same problem, my be I should disconnect the cd rom drive and just test the dvd drive?

---

### Post by cybergypsy on 2009-05-10
the second optical drive is probably being mounted as /dev/sr1 , check dmes output and adjust /etc/fstab to match.

---

### Post by Scott_74 on 2009-05-10
if the first line is for the dvd 
:/dev/sr0       /media/dvd0   udf,iso9660 auto ro,noauto,user,exec 0 0
should the second line  for the cdrom be
:/dev/sr1       /media/cdrom0   udf,iso9660 auto ro,noauto,user,exec 0 0

---

