---
title: "cannot mount sony usb thumbdrive"
date: 2009-09-18
forum: Hardware
---

### Post by mr.porch on 2009-09-18
I'm getting a "no media in device" error when i try to mount my usb flash drive

I believe it's formatted in fat or fat32
it's set-up to automatically load a tru-crypt directory on it
It does not show up in the fdisk listing
I'm running ubuntu 9.04

here's the output from dmseg

```
[    1.737750] NetLabel:  unlabeled traffic allowed by default
[    1.737750] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    1.737750] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    1.740114] AppArmor: AppArmor Filesystem Enabled
[    1.740123] pnp: PnP ACPI init
[    1.740123] ACPI: bus type pnp registered
[    1.744023] Switched to high resolution mode on CPU 0
[    1.746407] pnp: PnP ACPI: found 11 devices
[    1.746411] ACPI: ACPI bus type pnp unregistered
[    1.746416] PnPBIOS: Disabled by ACPI PNP
[    1.746430] system 00:01: iomem range 0xfec00000-0xfec00fff has been reserved
[    1.746435] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[    1.746447] system 00:08: ioport range 0x1080-0x1080 has been reserved
[    1.746452] system 00:08: ioport range 0x220-0x22f has been reserved
[    1.746456] system 00:08: ioport range 0x40b-0x40b has been reserved
[    1.746461] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    1.746465] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
[    1.746469] system 00:08: ioport range 0x530-0x537 has been reserved
[    1.746474] system 00:08: ioport range 0xc00-0xc01 has been reserved
[    1.746478] system 00:08: ioport range 0xc14-0xc14 has been reserved
[    1.746482] system 00:08: ioport range 0xc50-0xc52 has been reserved
[    1.746487] system 00:08: ioport range 0xc6c-0xc6c has been reserved
[    1.746491] system 00:08: ioport range 0xc6f-0xc6f has been reserved
[    1.746495] system 00:08: ioport range 0xcd0-0xcd1 has been reserved
[    1.746500] system 00:08: ioport range 0xcd2-0xcd3 has been reserved
[    1.746504] system 00:08: ioport range 0xcd4-0xcd5 has been reserved
[    1.746508] system 00:08: ioport range 0xcd6-0xcd7 has been reserved
[    1.746513] system 00:08: ioport range 0xcd8-0xcdf has been reserved
[    1.746517] system 00:08: ioport range 0x8000-0x805f has been reserved
[    1.746522] system 00:08: ioport range 0xf40-0xf47 has been reserved
[    1.746526] system 00:08: ioport range 0x87f-0x87f has been reserved
[    1.746535] system 00:09: iomem range 0xe0000-0xfffff could not be reserved
[    1.746540] system 00:09: iomem range 0xfff00000-0xffffffff has been reserved
[    1.746545] system 00:09: iomem range 0xff800000-0xff80ffff has been reserved
[    1.781372] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    1.781377] pci 0000:00:01.0:   IO window: 0x9000-0x9fff
[    1.781382] pci 0000:00:01.0:   MEM window: 0xf0000000-0xf01fffff
[    1.781387] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    1.781394] pci 0000:00:05.0: PCI bridge, secondary bus 0000:03
[    1.781398] pci 0000:00:05.0:   IO window: 0xa000-0xafff
[    1.781403] pci 0000:00:05.0:   MEM window: 0x88000000-0x880fffff
[    1.781408] pci 0000:00:05.0:   PREFETCH window: 0x000000cfd00000-0x000000cfdfffff
[    1.781414] pci 0000:00:06.0: PCI bridge, secondary bus 0000:04
[    1.781417] pci 0000:00:06.0:   IO window: disabled
[    1.781422] pci 0000:00:06.0:   MEM window: 0xf0200000-0xf02fffff
[    1.781426] pci 0000:00:06.0:   PREFETCH window: disabled
[    1.781432] pci 0000:00:14.4: PCI bridge, secondary bus 0000:09
[    1.781435] pci 0000:00:14.4:   IO window: disabled
[    1.781444] pci 0000:00:14.4:   MEM window: disabled
[    1.781450] pci 0000:00:14.4:   PREFETCH window: disabled
[    1.781469] pci 0000:00:05.0: setting latency timer to 64
[    1.781476] pci 0000:00:06.0: setting latency timer to 64
[    1.781487] bus: 00 index 0 io port: [0x00-0xffff]
[    1.781490] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    1.781494] bus: 01 index 0 io port: [0x9000-0x9fff]
[    1.781497] bus: 01 index 1 mmio: [0xf0000000-0xf01fffff]
[    1.781501] bus: 01 index 2 mmio: [0xd0000000-0xdfffffff]
[    1.781504] bus: 01 index 3 mmio: [0x0-0x0]
[    1.781507] bus: 03 index 0 io port: [0xa000-0xafff]
[    1.781511] bus: 03 index 1 mmio: [0x88000000-0x880fffff]
[    1.781514] bus: 03 index 2 mmio: [0xcfd00000-0xcfdfffff]
[    1.781518] bus: 03 index 3 mmio: [0x0-0x0]
[    1.781521] bus: 04 index 0 mmio: [0x0-0x0]
[    1.781524] bus: 04 index 1 mmio: [0xf0200000-0xf02fffff]
[    1.781527] bus: 04 index 2 mmio: [0x0-0x0]
[    1.781530] bus: 04 index 3 mmio: [0x0-0x0]
[    1.781533] bus: 09 index 0 mmio: [0x0-0x0]
[    1.781536] bus: 09 index 1 mmio: [0x0-0x0]
[    1.781539] bus: 09 index 2 mmio: [0x0-0x0]
[    1.781542] bus: 09 index 3 io port: [0x00-0xffff]
[    1.781545] bus: 09 index 4 mmio: [0x000000-0xffffffff]
[    1.781559] NET: Registered protocol family 2
[    1.783448] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    1.783892] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.784878] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    1.785342] TCP: Hash tables configured (established 131072 bind 65536)
[    1.785346] TCP reno registered
[    1.785497] NET: Registered protocol family 1
[    1.785688] checking if image is initramfs... it is
[    2.745203] Freeing initrd memory: 7389k freed
[    2.745254] Simple Boot Flag at 0x36 set to 0x1
[    2.745356] cpufreq: No nForce2 chipset.
[    2.745545] audit: initializing netlink socket (disabled)
[    2.745565] type=2000 audit(1253303333.744:1): initialized
[    2.769968] highmem bounce pool size: 64 pages
[    2.769977] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    2.771743] VFS: Disk quotas dquot_6.5.1
[    2.771823] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.772680] fuse init (API version 7.10)
[    2.772794] msgmni has been set to 1704
[    2.773039] alg: No test for stdrng (krng)
[    2.773056] io scheduler noop registered
[    2.773059] io scheduler anticipatory registered
[    2.773062] io scheduler deadline registered
[    2.773085] io scheduler cfq registered (default)
[    2.773206] pci 0000:01:05.0: Boot video device
[    2.779414] pcieport-driver 0000:00:05.0: setting latency timer to 64
[    2.779443] pcieport-driver 0000:00:05.0: found MSI capability
[    2.779468] pcieport-driver 0000:00:05.0: irq 2303 for MSI/MSI-X
[    2.779478] pci_express 0000:00:05.0:pcie00: allocate port service
[    2.779500] pci_express 0000:00:05.0:pcie03: allocate port service
[    2.779546] pcieport-driver 0000:00:06.0: setting latency timer to 64
[    2.779571] pcieport-driver 0000:00:06.0: found MSI capability
[    2.779590] pcieport-driver 0000:00:06.0: irq 2302 for MSI/MSI-X
[    2.779600] pci_express 0000:00:06.0:pcie00: allocate port service
[    2.779622] pci_express 0000:00:06.0:pcie03: allocate port service
[    2.779686] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.779703] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.780933] ACPI: AC Adapter [ACAD] (off-line)
[    2.803608] ACPI: Battery Slot [BAT1] (battery present)
[    2.803713] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    2.803717] ACPI: Power Button (FF) [PWRF]
[    2.803777] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    2.803912] ACPI: Lid Switch [LID]
[    2.803972] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    2.803976] ACPI: Sleep Button (CM) [SLPB]
[    2.804048] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[    2.804052] ACPI: Power Button (CM) [PWRB]
[    2.804313] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.804350] processor ACPI_CPU:00: registered as cooling_device0
[    2.804355] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.809220] thermal LNXTHERM:01: registered as thermal_zone0
[    2.811381] ACPI: Thermal Zone [THRM] (54 C)
[    2.811439] isapnp: Scanning for PnP cards...
[    3.168034] isapnp: No Plug & Play device found
[    3.169907] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    3.171230] brd: module loaded
[    3.171658] loop: module loaded
[    3.171754] Fixed MDIO Bus: probed
[    3.171764] PPP generic driver version 2.4.2
[    3.171846] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    3.171886] Driver 'sd' needs updating - please use bus_type methods
[    3.171899] Driver 'sr' needs updating - please use bus_type methods
[    3.171945] ahci 0000:00:12.0: version 3.0
[    3.171971] ahci 0000:00:12.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    3.172024] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
[    3.172173] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    3.172178] ahci 0000:00:12.0: flags: ncq sntf ilck pm led clo pmp pio slum part 
[    3.173239] scsi0 : ahci
[    3.173401] scsi1 : ahci
[    3.173482] scsi2 : ahci
[    3.173553] scsi3 : ahci
[    3.173702] ata1: SATA max UDMA/133 abar m1024@0xf0508000 port 0xf0508100 irq 22
[    3.173708] ata2: SATA max UDMA/133 abar m1024@0xf0508000 port 0xf0508180 irq 22
[    3.173713] ata3: SATA max UDMA/133 abar m1024@0xf0508000 port 0xf0508200 irq 22
[    3.173719] ata4: SATA max UDMA/133 abar m1024@0xf0508000 port 0xf0508280 irq 22
[    3.656012] ata1: softreset failed (device not ready)
[    3.656057] ata1: failed due to HW bug, retry pmp=0
[    3.820029] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.868258] ata1.00: ATA-8: ST9250315AS, 0001SDM1, max UDMA/133
[    3.868263] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    3.868293] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[    3.870452] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[    3.870457] ata1.00: configured for UDMA/133
[    4.204028] ata2: SATA link down (SStatus 0 SControl 300)
[    4.540028] ata3: SATA link down (SStatus 0 SControl 300)
[    4.876028] ata4: SATA link down (SStatus 0 SControl 300)
[    4.892160] scsi 0:0:0:0: Direct-Access     ATA      ST9250315AS      0001 PQ: 0 ANSI: 5
[    4.892295] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[    4.892320] sd 0:0:0:0: [sda] Write Protect is off
[    4.892324] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.892359] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.892455] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[    4.892474] sd 0:0:0:0: [sda] Write Protect is off
[    4.892478] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.892511] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.892518]  sda: sda1 sda2 < sda5 >
[    4.985748] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.985817] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.986186] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.986240] pata_atiixp 0000:00:14.1: setting latency timer to 64
[    4.986343] scsi4 : pata_atiixp
[    4.986418] scsi5 : pata_atiixp
[    4.987658] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8420 irq 14
[    4.987663] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8428 irq 15
[    5.296715] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    5.296744] ehci_hcd 0000:00:13.5: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    5.296772] ehci_hcd 0000:00:13.5: EHCI Host Controller
[    5.296865] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 1
[    5.296913] ehci_hcd 0000:00:13.5: applying AMD SB600/SB700 USB freeze workaround
[    5.296935] ehci_hcd 0000:00:13.5: debug port 1
[    5.296962] ehci_hcd 0000:00:13.5: irq 19, io mem 0xf0508400
[    5.308016] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00
[    5.308125] usb usb1: configuration #1 chosen from 1 choice
[    5.308163] hub 1-0:1.0: USB hub found
[    5.308176] hub 1-0:1.0: 10 ports detected
[    5.308339] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    5.308361] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.308377] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    5.308434] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    5.308464] ohci_hcd 0000:00:13.0: irq 16, io mem 0xf0504000
[    5.364102] usb usb2: configuration #1 chosen from 1 choice
[    5.364135] hub 2-0:1.0: USB hub found
[    5.364152] hub 2-0:1.0: 2 ports detected
[    5.364267] ohci_hcd 0000:00:13.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    5.364283] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    5.364338] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    5.364367] ohci_hcd 0000:00:13.1: irq 17, io mem 0xf0505000
[    5.420103] usb usb3: configuration #1 chosen from 1 choice
[    5.420139] hub 3-0:1.0: USB hub found
[    5.420155] hub 3-0:1.0: 2 ports detected
[    5.420264] ohci_hcd 0000:00:13.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    5.420279] ohci_hcd 0000:00:13.3: OHCI Host Controller
[    5.420339] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 4
[    5.420360] ohci_hcd 0000:00:13.3: irq 17, io mem 0xf0506000
[    5.476106] usb usb4: configuration #1 chosen from 1 choice
[    5.476139] hub 4-0:1.0: USB hub found
[    5.476157] hub 4-0:1.0: 2 ports detected
[    5.476271] ohci_hcd 0000:00:13.4: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    5.476287] ohci_hcd 0000:00:13.4: OHCI Host Controller
[    5.476345] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 5
[    5.476378] ohci_hcd 0000:00:13.4: irq 18, io mem 0xf0507000
[    5.532099] usb usb5: configuration #1 chosen from 1 choice
[    5.532133] hub 5-0:1.0: USB hub found
[    5.532149] hub 5-0:1.0: 2 ports detected
[    5.532283] uhci_hcd: USB Universal Host Controller Interface driver
[    5.532400] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    5.540582] i8042.c: Detected active multiplexing controller, rev 1.1.
[    5.544416] serio: i8042 KBD port at 0x60,0x64 irq 1
[    5.544423] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    5.544427] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    5.544431] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    5.544435] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    5.544656] mice: PS/2 mouse device common for all mice
[    5.544912] rtc_cmos 00:04: RTC can wake from S4
[    5.544961] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    5.544995] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    5.545085] device-mapper: uevent: version 1.0.3
[    5.545233] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    5.545299] device-mapper: multipath: version 1.0.5 loaded
[    5.545304] device-mapper: multipath round-robin: version 1.0.0 loaded
[    5.545408] EISA: Probing bus 0 at eisa.0
[    5.545421] Cannot allocate resource for EISA slot 1
[    5.545451] Cannot allocate resource for EISA slot 8
[    5.545454] EISA: Detected 0 cards.
[    5.545545] cpuidle: using governor ladder
[    5.545625] cpuidle: using governor menu
[    5.546379] TCP cubic registered
[    5.546520] NET: Registered protocol family 10
[    5.547106] lo: Disabled Privacy Extensions
[    5.547570] NET: Registered protocol family 17
[    5.547593] Bluetooth: L2CAP ver 2.11
[    5.547596] Bluetooth: L2CAP socket layer initialized
[    5.547600] Bluetooth: SCO (Voice Link) ver 0.6
[    5.547603] Bluetooth: SCO socket layer initialized
[    5.547638] Bluetooth: RFCOMM socket layer initialized
[    5.547648] Bluetooth: RFCOMM TTY layer initialized
[    5.547651] Bluetooth: RFCOMM ver 1.10
[    5.547683] powernow-k8: Found 1 AMD Athlon(tm) Processor L110 processors (1 cpu cores) (version 2.20.00)
[    5.557560] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
[    5.557625] Using IPI No-Shortcut mode
[    5.557751] registered taskstats version 1
[    5.557920]   Magic number: 9:175:850
[    5.558039] rtc_cmos 00:04: setting system clock to 2009-09-18 19:48:58 UTC (1253303338)
[    5.558044] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    5.558047] EDD information not available.
[    5.558557] Freeing unused kernel memory: 532k freed
[    5.558761] Write protecting the kernel text: 4116k
[    5.558831] Write protecting the kernel read-only data: 1528k
[    5.593693] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    5.732031] usb 1-4: new high speed USB device using ehci_hcd and address 3
[    5.900674] usb 1-4: configuration #1 chosen from 1 choice
[    6.117267] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    6.117290] r8169 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    6.117312] r8169 0000:03:00.0: setting latency timer to 64
[    6.117423] r8169 0000:03:00.0: irq 2301 for MSI/MSI-X
[    6.118303] eth0: RTL8102e at 0xf7d2c000, 00:23:8b:ef:39:f4, XID 24c00000 IRQ 2301
[    6.164438] usb 2-1: new full speed USB device using ohci_hcd and address 2
[    6.333167] usb 2-1: configuration #1 chosen from 1 choice
[    6.609920] Initializing USB Mass Storage driver...
[    6.611995] scsi6 : SCSI emulation for USB Mass Storage devices
[    6.612462] usbcore: registered new interface driver usb-storage
[    6.612468] USB Mass Storage support registered.
[    6.612750] usb-storage: device found at 2
[    6.612752] usb-storage: waiting for device to settle before scanning
[    6.649454] Marking TSC unstable due to TSC halts in idle
[    6.813108] PM: Starting manual resume from disk
[    6.813114] PM: Resume from partition 8:5
[    6.813117] PM: Checking hibernation image.
[    6.813392] PM: Resume from disk failed.
[    6.864110] kjournald starting.  Commit interval 5 seconds
[    6.864126] EXT3-fs: mounted filesystem with ordered data mode.
[   11.613107] usb-storage: device scan complete
[   11.619088] scsi 6:0:0:0: Direct-Access     Novatel  MMC Storage      2.31 PQ: 0 ANSI: 2
[   11.629177] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[   11.629260] sd 6:0:0:0: Attached scsi generic sg1 type 0
[   12.044476] udev: starting version 141
[   12.352380] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.362002] Linux agpgart interface v0.103
[   12.379912] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x8410, revision 0
[   12.509532] acpi device:19: registered as cooling_device1
[   12.635935] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:17/device:18/input/input6
[   12.664249] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   12.795465] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.825912] hda_codec: Unknown model for ALC662, trying auto-probe from BIOS...
[   12.944426] usbcore: registered new interface driver usbserial
[   12.944488] USB Serial support registered for generic
[   12.944595] usbcore: registered new interface driver usbserial_generic
[   12.944599] usbserial: USB Serial Driver core
[   12.948150] cfg80211: Using static regulatory domain info
[   12.948155] cfg80211: Regulatory domain: US
[   12.948159] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   12.948163] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2700 mBm)
[   12.948168] 	(5170000 KHz - 5190000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   12.948172] 	(5190000 KHz - 5210000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   12.948175] 	(5210000 KHz - 5230000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   12.948179] 	(5230000 KHz - 5330000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   12.948183] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 3000 mBm)
[   12.948283] cfg80211: Calling CRDA for country: US
[   12.959466] USB Serial support registered for GSM modem (1-port)
[   12.959566] option 2-1:1.0: GSM modem (1-port) converter detected
[   12.959772] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB0
[   12.959795] option 2-1:1.1: GSM modem (1-port) converter detected
[   12.959940] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB1
[   12.959962] option 2-1:1.2: GSM modem (1-port) converter detected
[   12.960130] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB2
[   12.960151] option 2-1:1.3: GSM modem (1-port) converter detected
[   12.960332] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB3
[   12.960356] usbcore: registered new interface driver option
[   12.960360] option: v0.7.2:USB Driver for GSM modems
[   13.239329] Linux video capture interface: v2.00
[   13.241142] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   13.336469] ath9k 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   13.336483] ath9k 0000:04:00.0: setting latency timer to 64
[   13.400639] uvcvideo: Found UVC 1.00 device CNF9011 (04f2:b175)
[   13.408289] input: CNF9011 as /devices/pci0000:00/0000:00:13.5/usb1/1-4/1-4:1.0/input/input8
[   13.415043] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   13.424292] usbcore: registered new interface driver uvcvideo
[   13.424333] USB Video Class driver (v0.1.0)
[   13.537002] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   13.824417] Registered led device: ath9k-phy0::radio
[   13.824483] Registered led device: ath9k-phy0::assoc
[   13.824543] Registered led device: ath9k-phy0::tx
[   13.824603] Registered led device: ath9k-phy0::rx
[   13.824615] phy0: Atheros AR9285 MAC/BB Rev:2 AR5133 RF Rev:e0: mem=0xf83c0000, irq=18
[   13.908403] PM: Marking nosave pages: 000000000009f000 - 0000000000100000
[   13.908411] PM: Basic memory bitmaps created
[   13.931790] PM: Basic memory bitmaps freed
[   14.327021] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04731/0xa40000
[   14.374893] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input9
[   14.638536] cfg80211: Regulatory domain changed to country: US
[   14.638543] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   14.638548] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   14.638552] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   14.638556] 	(5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.638560] 	(5490000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.638564] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   34.052360] lp: driver loaded but no devices found
[   34.171320] Adding 5277312k swap on /dev/sda5.  Priority:-1 extents:1 across:5277312k
[   34.204504] EXT3 FS on sda1, internal journal
[   34.858221] type=1505 audit(1253303367.797:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3348
[   34.945814] type=1505 audit(1253303367.885:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=3352
[   34.946035] type=1505 audit(1253303367.885:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=3352
[   34.946119] type=1505 audit(1253303367.885:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=3352
[   34.946194] type=1505 audit(1253303367.885:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=3352
[   35.196679] type=1505 audit(1253303368.137:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3357
[   35.197003] type=1505 audit(1253303368.137:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3357
[   35.247566] type=1505 audit(1253303368.185:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=3361
[   38.258152] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   38.258157] Bluetooth: BNEP filters: protocol multicast
[   38.286660] Bridge firewalling registered
[   39.594223] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   39.940170] [drm] Initialized drm 1.1.0 20060810
[   39.986041] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   39.987826] ppdev: user-space parallel port driver
[   40.649828] [drm] Setting GART location based on new memory map
[   40.650844] [drm] Loading RS690/RS740 Microcode
[   40.650868] [drm] Num pipes: 1
[   40.650876] [drm] writeback test succeeded in 1 usecs
[   44.058261] r8169: eth0: link down
[   44.058630] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   44.102827] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   85.864032] usb 1-2: new high speed USB device using ehci_hcd and address 4
[   87.027863] usb 1-2: configuration #1 chosen from 1 choice
[   87.086572] scsi7 : SCSI emulation for USB Mass Storage devices
[   87.091402] usb-storage: device found at 4
[   87.091407] usb-storage: waiting for device to settle before scanning
[   92.088633] usb-storage: device scan complete
[   92.089745] scsi 7:0:0:0: Direct-Access     Sony     Storage Media    0100 PQ: 0 ANSI: 0 CCS
[   92.134892] sd 7:0:0:0: [sdc] 15663104 512-byte hardware sectors: (8.01 GB/7.46 GiB)
[   92.136440] sd 7:0:0:0: [sdc] Write Protect is off
[   92.136447] sd 7:0:0:0: [sdc] Mode Sense: 43 00 00 00
[   92.136451] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[   92.149349] sd 7:0:0:0: [sdc] 15663104 512-byte hardware sectors: (8.01 GB/7.46 GiB)
[   92.150418] sd 7:0:0:0: [sdc] Write Protect is off
[   92.150423] sd 7:0:0:0: [sdc] Mode Sense: 43 00 00 00
[   92.150427] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[   92.150436]  sdc: sdc1
[   92.151673] sd 7:0:0:0: [sdc] Attached SCSI removable disk
[   92.151778] sd 7:0:0:0: Attached scsi generic sg2 type 0
[   92.555112] PPP BSD Compression module registered
[   92.581792] PPP Deflate Compression module registered
[ 1345.059422] usb 1-2: USB disconnect, address 4
[ 1345.063222] sd 7:0:0:0: [sdc] READ CAPACITY failed
[ 1345.063229] sd 7:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1345.063236] sd 7:0:0:0: [sdc] Sense not available.
[ 1345.063292] sd 7:0:0:0: [sdc] Write Protect is off
[ 1345.063296] sd 7:0:0:0: [sdc] Mode Sense: 00 00 00 00
[ 1345.063300] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[ 1345.063974] scsi 7:0:0:0: rejecting I/O to dead device
[ 1345.063983] scsi 7:0:0:0: rejecting I/O to dead device
[ 1345.063991] scsi 7:0:0:0: rejecting I/O to dead device
[ 1345.063996] scsi 7:0:0:0: [sdc] READ CAPACITY failed
[ 1345.064032] scsi 7:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 1345.064037] scsi 7:0:0:0: [sdc] Sense not available.
[ 1345.064045] scsi 7:0:0:0: rejecting I/O to dead device
[ 1345.064050] scsi 7:0:0:0: [sdc] Write Protect is off
[ 1345.064054] scsi 7:0:0:0: [sdc] Mode Sense: 00 00 00 00
[ 1345.064057] scsi 7:0:0:0: [sdc] Assuming drive cache: write through
[ 2357.572055] usb 1-3: new high speed USB device using ehci_hcd and address 5
[ 2358.731785] usb 1-3: configuration #1 chosen from 1 choice
[ 2358.761238] scsi8 : SCSI emulation for USB Mass Storage devices
[ 2358.794161] usb-storage: device found at 5
[ 2358.794166] usb-storage: waiting for device to settle before scanning
[ 2363.792622] usb-storage: device scan complete
[ 2363.793727] scsi 8:0:0:0: Direct-Access     Sony     Storage Media    0100 PQ: 0 ANSI: 0 CCS
[ 2363.801603] sd 8:0:0:0: [sdc] 15663104 512-byte hardware sectors: (8.01 GB/7.46 GiB)
[ 2363.843378] sd 8:0:0:0: [sdc] Write Protect is off
[ 2363.843386] sd 8:0:0:0: [sdc] Mode Sense: 43 00 00 00
[ 2363.843390] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[ 2363.846547] sd 8:0:0:0: [sdc] 15663104 512-byte hardware sectors: (8.01 GB/7.46 GiB)
[ 2363.847710] sd 8:0:0:0: [sdc] Write Protect is off
[ 2363.847715] sd 8:0:0:0: [sdc] Mode Sense: 43 00 00 00
[ 2363.847719] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[ 2363.847728]  sdc: sdc1
[ 2363.849297] sd 8:0:0:0: [sdc] Attached SCSI removable disk
[ 2363.849405] sd 8:0:0:0: Attached scsi generic sg2 type 0
[ 2376.096024] APIC error on CPU0: 00(40)
[ 3402.166427] usb 1-3: USB disconnect, address 5
[ 3408.172034] usb 1-3: new high speed USB device using ehci_hcd and address 6
[ 3409.335401] usb 1-3: configuration #1 chosen from 1 choice
[ 3409.394486] scsi9 : SCSI emulation for USB Mass Storage devices
[ 3409.398926] usb-storage: device found at 6
[ 3409.398931] usb-storage: waiting for device to settle before scanning
[ 3414.396572] usb-storage: device scan complete
[ 3414.397682] scsi 9:0:0:0: Direct-Access     Sony     Storage Media    0100 PQ: 0 ANSI: 0 CCS
[ 3414.403278] sd 9:0:0:0: [sdc] 15663104 512-byte hardware sectors: (8.01 GB/7.46 GiB)
[ 3414.404664] sd 9:0:0:0: [sdc] Write Protect is off
[ 3414.404671] sd 9:0:0:0: [sdc] Mode Sense: 43 00 00 00
[ 3414.404676] sd 9:0:0:0: [sdc] Assuming drive cache: write through
[ 3414.407292] sd 9:0:0:0: [sdc] 15663104 512-byte hardware sectors: (8.01 GB/7.46 GiB)
[ 3414.449119] sd 9:0:0:0: [sdc] Write Protect is off
[ 3414.449127] sd 9:0:0:0: [sdc] Mode Sense: 43 00 00 00
[ 3414.449131] sd 9:0:0:0: [sdc] Assuming drive cache: write through
[ 3414.449140]  sdc: sdc1
[ 3414.450373] sd 9:0:0:0: [sdc] Attached SCSI removable disk
[ 3414.450480] sd 9:0:0:0: Attached scsi generic sg2 type 0
```
please let me know if i left out any important information or if you have any ideas/suggestions for how to make it work

---

### Post by jward3010 on 2009-09-18
Have you a Windows machine to try it on? And for the hell of it post what you get from
```
sudo fdisk -l
```
And also do
```
sudo lsusb
```

---

### Post by mr.porch on 2009-09-19
It works fine on my windows XP box

```
sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0601dbd6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29744   238918648+  83  Linux
/dev/sda2           29745       30401     5277352+   5  Extended
/dev/sda5           29745       30401     5277321   82  Linux swap / Solaris

```

```
lsusb
Bus 001 Device 003: ID 054c:0243 Sony Corp. MicroVault Flash Drive
Bus 001 Device 002: ID 04f2:b175 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

---

### Post by earthpigg on 2009-09-19
> **mr.porch said:**
> It works fine on my windows XP box


does this thumb drive, by chance, have any silly pre-installed software or anything else that shows up in Windows that does not show up on a generic thumb drive?

this could be another case of this: [http://en.wikipedia.org/wiki/U3#Criticisms](http://en.wikipedia.org/wiki/U3#Criticisms)

i'm looking here: [http://www.sony.net/Products/Media/Microvault/products/usm-l/index.html#caution](http://www.sony.net/Products/Media/Microvault/products/usm-l/index.html#caution)

> Sony Micro Vault is formatted with an exclusive software to best perform the High-Speed USB's high transfer rate. If formatted using any other software, it is possible that the performance deteriorates or that a data error happens depending on the computers or on the OS. Should any of such conditions happen, it is highly recommended to download and format the device again using Sony Micro Vault Format Software’. (Be sure to backup your files before re-formatting)

[http://www.sony.net/Products/Media/Microvault/support/index.html#support02](http://www.sony.net/Products/Media/Microvault/support/index.html#support02)

> You cannot use the Micro Vault with unsupported operating systems. Please check the OS compatibility chart.

> Before Use
	
What PCs can I use?
You can use PCs that have Windows XP, Windows 2000 or Windows Me installed. Please apply the latest service packs. 

and, of course: [http://www.sony.net/Products/Media/Microvault/products/usm-l/index.html#caution](http://www.sony.net/Products/Media/Microvault/products/usm-l/index.html#caution)

---

### Post by jward3010 on 2009-09-19
In Disk Management under Windows what type of filesystem does it come up as out of interest?

What you can do is format it as FAT32 within Windows, and go back to the U3 system at any time with Sony's tool.

---

