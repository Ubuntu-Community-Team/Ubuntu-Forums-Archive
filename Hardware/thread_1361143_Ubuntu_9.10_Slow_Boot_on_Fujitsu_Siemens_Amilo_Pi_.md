---
title: "Ubuntu 9.10 Slow Boot on Fujitsu Siemens Amilo Pi 1505"
date: 2009-12-21
forum: Hardware
---

### Post by thycpt737 on 2009-12-21
Hello all,
I've just installed Ubuntu 9.10 onto my FujitsuSiemens Amilo Pi1505 laptop.Totally Formatted the drive into one partition for ubuntu and made install with the usb key. &#304;nstall went fine and system is working great except for the slow boot. Actually after the grub loading text computer stands for about 42 seconds with a blinking cursor top left side, at this moment there is actually no activity at the hdd because there is no blinking leds or a hdd noise. After that ubuntu boots as usual and perfectly usable with every hardware working. I'll put my dmesg output and bootchart graph. I think there is a problem with the Cd-rom drive at the boot. And i've read in an another forum that Fujitsu Comp. has DSDT problems but i dont know if its the case so i'll just pass it. Here is the cd-rom out put of dmesg code,

[    1.740616] sd 0:0:0:0: [sda] Attached SCSI disk
[   21.691573] scsi scan: 96 byte inquiry failed.  Consider BLIST_INQUIRY_36 for this device
[   21.694051] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T10N  PR03 PQ: 0 ANSI: 5

and below is the whole dmesg output,

```
[    0.718127] pnp: PnP ACPI: found 11 devices
[    0.718130] ACPI: ACPI bus type pnp unregistered
[    0.718135] PnPBIOS: Disabled by ACPI PNP
[    0.718146] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    0.718149] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.718152] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.718158] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.718161] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.718165] system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.718168] system 00:01: iomem range 0xfed40000-0xfed44fff has been reserved
[    0.718171] system 00:01: iomem range 0xfed45000-0xfed8ffff has been reserved
[    0.718179] system 00:04: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.718186] system 00:06: ioport range 0x200-0x20f has been reserved
[    0.718189] system 00:06: ioport range 0x680-0x69f has been reserved
[    0.718192] system 00:06: ioport range 0x800-0x80f has been reserved
[    0.718196] system 00:06: ioport range 0x1000-0x107f has been reserved
[    0.718199] system 00:06: ioport range 0x1180-0x11bf has been reserved
[    0.718202] system 00:06: ioport range 0x1640-0x164f has been reserved
[    0.718208] system 00:07: ioport range 0x6a0-0x6af has been reserved
[    0.718211] system 00:07: ioport range 0x6b0-0x6ff has been reserved
[    0.752895] AppArmor: AppArmor Filesystem Enabled
[    0.752984] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.752988] pci 0000:00:1c.0:   IO window: 0xf000-0xffff
[    0.752996] pci 0000:00:1c.0:   MEM window: 0xfac00000-0xfebfffff
[    0.753001] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.753006] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:04
[    0.753009] pci 0000:00:1c.1:   IO window: disabled
[    0.753015] pci 0000:00:1c.1:   MEM window: disabled
[    0.753020] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.753038] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:05
[    0.753040] pci 0000:00:1c.2:   IO window: disabled
[    0.753047] pci 0000:00:1c.2:   MEM window: 0xf7000000-0xf70fffff
[    0.753052] pci 0000:00:1c.2:   PREFETCH window: disabled
[    0.753062] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:06
[    0.753066] pci 0000:00:1e.0:   IO window: 0x2000-0x2fff
[    0.753073] pci 0000:00:1e.0:   MEM window: 0xf0200000-0xf02fffff
[    0.753078] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.753091] pci 0000:00:1c.0: enabling device (0000 -> 0003)
[    0.753096]   alloc irq_desc for 17 on node -1
[    0.753099]   alloc kstat_irqs on node -1
[    0.753104] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.753112] pci 0000:00:1c.0: setting latency timer to 64
[    0.753121]   alloc irq_desc for 16 on node -1
[    0.753122]   alloc kstat_irqs on node -1
[    0.753126] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.753133] pci 0000:00:1c.1: setting latency timer to 64
[    0.753142] pci 0000:00:1c.2: enabling device (0000 -> 0002)
[    0.753146]   alloc irq_desc for 18 on node -1
[    0.753148]   alloc kstat_irqs on node -1
[    0.753152] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.753159] pci 0000:00:1c.2: setting latency timer to 64
[    0.753168] pci 0000:00:1e.0: setting latency timer to 64
[    0.753173] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.753176] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.753179] pci_bus 0000:02: resource 0 io:  [0xf000-0xffff]
[    0.753182] pci_bus 0000:02: resource 1 mem: [0xfac00000-0xfebfffff]
[    0.753185] pci_bus 0000:05: resource 1 mem: [0xf7000000-0xf70fffff]
[    0.753188] pci_bus 0000:06: resource 0 io:  [0x2000-0x2fff]
[    0.753190] pci_bus 0000:06: resource 1 mem: [0xf0200000-0xf02fffff]
[    0.753193] pci_bus 0000:06: resource 3 io:  [0x00-0xffff]
[    0.753196] pci_bus 0000:06: resource 4 mem: [0x000000-0xffffffff]
[    0.753231] NET: Registered protocol family 2
[    0.753334] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.753681] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.754247] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.754519] TCP: Hash tables configured (established 131072 bind 65536)
[    0.754522] TCP reno registered
[    0.754601] NET: Registered protocol family 1
[    0.754669] Trying to unpack rootfs image as initramfs...
[    0.961648] Freeing initrd memory: 7474k freed
[    0.966074] Simple Boot Flag at 0x35 set to 0x1
[    0.966283] cpufreq-nforce2: No nForce2 chipset.
[    0.966314] Scanning for low memory corruption every 60 seconds
[    0.966437] audit: initializing netlink socket (disabled)
[    0.966458] type=2000 audit(1261432653.964:1): initialized
[    0.975879] highmem bounce pool size: 64 pages
[    0.975885] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.977528] VFS: Disk quotas dquot_6.5.2
[    0.977599] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.978211] fuse init (API version 7.12)
[    0.978302] msgmni has been set to 1706
[    0.978551] alg: No test for stdrng (krng)
[    0.978567] io scheduler noop registered
[    0.978570] io scheduler anticipatory registered
[    0.978572] io scheduler deadline registered
[    0.978620] io scheduler cfq registered (default)
[    0.978634] pci 0000:00:02.0: Boot video device
[    0.978899]   alloc irq_desc for 24 on node -1
[    0.978902]   alloc kstat_irqs on node -1
[    0.978915] pcieport-driver 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.978927] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.979093]   alloc irq_desc for 25 on node -1
[    0.979096]   alloc kstat_irqs on node -1
[    0.979105] pcieport-driver 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.979117] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    0.979284]   alloc irq_desc for 26 on node -1
[    0.979286]   alloc kstat_irqs on node -1
[    0.979295] pcieport-driver 0000:00:1c.2: irq 26 for MSI/MSI-X
[    0.979307] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    0.979425] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.979545] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.979978] ACPI: AC Adapter [AC0] (off-line)
[    0.980102] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.980106] ACPI: Power Button [PWRF]
[    0.980169] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    0.980206] ACPI: Lid Switch [LID0]
[    0.980254] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
[    0.980257] ACPI: Power Button [PWRB]
[    0.980305] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input3
[    0.980308] ACPI: Sleep Button [SLPB]
[    0.981035] ACPI: SSDT 7f697f42 001A8 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.981427] ACPI: SSDT 7f697cf7 001C6 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.981747] Marking TSC unstable due to TSC halts in idle
[    0.981767] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    0.981796] processor LNXCPU:00: registered as cooling_device0
[    0.981800] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.982183] ACPI: SSDT 7f6980ea 00089 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.982520] ACPI: SSDT 7f697ebd 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.982928] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    0.982955] processor LNXCPU:01: registered as cooling_device1
[    0.982960] ACPI: Processor [CPU1] (supports 8 throttling states)
[    0.985286] thermal LNXTHERM:01: registered as thermal_zone0
[    0.985295] ACPI: Thermal Zone [THRM] (41 C)
[    0.985369] isapnp: Scanning for PnP cards...
[    1.042448] ACPI: Battery Slot [BAT0] (battery present)
[    1.339685] isapnp: No Plug & Play device found
[    1.340967] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.342432] brd: module loaded
[    1.342924] loop: module loaded
[    1.343001] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    1.343078] ahci 0000:00:1f.2: version 3.0
[    1.343093]   alloc irq_desc for 19 on node -1
[    1.343095]   alloc kstat_irqs on node -1
[    1.343101] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.343134]   alloc irq_desc for 27 on node -1
[    1.343136]   alloc kstat_irqs on node -1
[    1.343147] ahci 0000:00:1f.2: irq 27 for MSI/MSI-X
[    1.343227] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0x5 impl SATA mode
[    1.343230] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[    1.343236] ahci 0000:00:1f.2: setting latency timer to 64
[    1.343425] scsi0 : ahci
[    1.343523] scsi1 : ahci
[    1.343590] scsi2 : ahci
[    1.343666] scsi3 : ahci
[    1.343774] ata1: SATA max UDMA/133 abar m1024@0xf0004400 port 0xf0004500 irq 27
[    1.343777] ata2: DUMMY
[    1.343780] ata3: SATA max UDMA/133 abar m1024@0xf0004400 port 0xf0004600 irq 27
[    1.343782] ata4: DUMMY
[    1.343837] ata_piix 0000:00:1f.1: version 2.13
[    1.343847] ata_piix 0000:00:1f.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.343883] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.343964] scsi4 : ata_piix
[    1.344050] scsi5 : ata_piix
[    1.344603] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    1.344607] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    1.345604] Fixed MDIO Bus: probed
[    1.345641] PPP generic driver version 2.4.2
[    1.345733] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.345752]   alloc irq_desc for 23 on node -1
[    1.345754]   alloc kstat_irqs on node -1
[    1.345759] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.345771] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.345775] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.345838] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.349059] ata6: port disabled. ignoring.
[    1.349749] ehci_hcd 0000:00:1d.7: debug port 1
[    1.349757] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.349771] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf0004000
[    1.364019] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.364096] usb usb1: configuration #1 chosen from 1 choice
[    1.364128] hub 1-0:1.0: USB hub found
[    1.364138] hub 1-0:1.0: 8 ports detected
[    1.364219] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.364236] uhci_hcd: USB Universal Host Controller Interface driver
[    1.364261] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.364268] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.364272] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.364305] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.364334] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[    1.364420] usb usb2: configuration #1 chosen from 1 choice
[    1.364451] hub 2-0:1.0: USB hub found
[    1.364458] hub 2-0:1.0: 2 ports detected
[    1.364510] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.364517] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.364521] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.364556] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.364594] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[    1.364677] usb usb3: configuration #1 chosen from 1 choice
[    1.364708] hub 3-0:1.0: USB hub found
[    1.364715] hub 3-0:1.0: 2 ports detected
[    1.364765] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.364772] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.364775] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.364807] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.364845] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    1.364929] usb usb4: configuration #1 chosen from 1 choice
[    1.364957] hub 4-0:1.0: USB hub found
[    1.364964] hub 4-0:1.0: 2 ports detected
[    1.365014] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    1.365020] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.365024] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.365056] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.365092] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
[    1.365179] usb usb5: configuration #1 chosen from 1 choice
[    1.365207] hub 5-0:1.0: USB hub found
[    1.365214] hub 5-0:1.0: 2 ports detected
[    1.365327] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.367598] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.368826] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.368833] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.368836] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.368841] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.368844] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.368914] mice: PS/2 mouse device common for all mice
[    1.369124] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    1.369157] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.369256] device-mapper: uevent: version 1.0.3
[    1.369358] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    1.369461] device-mapper: multipath: version 1.1.0 loaded
[    1.369464] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.369590] EISA: Probing bus 0 at eisa.0
[    1.369597] Cannot allocate resource for EISA slot 1
[    1.369599] Cannot allocate resource for EISA slot 2
[    1.369626] EISA: Detected 0 cards.
[    1.369831] cpuidle: using governor ladder
[    1.369967] cpuidle: using governor menu
[    1.370502] TCP cubic registered
[    1.370668] NET: Registered protocol family 10
[    1.371167] lo: Disabled Privacy Extensions
[    1.371537] NET: Registered protocol family 17
[    1.371556] Bluetooth: L2CAP ver 2.13
[    1.371558] Bluetooth: L2CAP socket layer initialized
[    1.371561] Bluetooth: SCO (Voice Link) ver 0.6
[    1.371563] Bluetooth: SCO socket layer initialized
[    1.371608] Bluetooth: RFCOMM TTY layer initialized
[    1.371611] Bluetooth: RFCOMM socket layer initialized
[    1.371613] Bluetooth: RFCOMM ver 1.11
[    1.371916] Using IPI No-Shortcut mode
[    1.371978] PM: Resume from disk failed.
[    1.371993] registered taskstats version 1
[    1.372130]   Magic number: 5:287:1006
[    1.372155] input input3: hash matches
[    1.372161] rtc_cmos 00:08: hash matches
[    1.372228] rtc_cmos 00:08: setting system clock to 2009-12-21 21:57:35 UTC (1261432655)
[    1.372231] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.372233] EDD information not available.
[    1.401225] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    1.500096] Clocksource tsc unstable (delta = -97272270 ns)
[    1.516493] ata5.00: ATAPI: HL-DT-ST DVDRAM GSA-T10N, PR03, max UDMA/33
[    1.532443] ata5.00: configured for UDMA/33
[    1.660136] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.661185] ata1.00: ACPI cmd ef/90:03:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    1.665081] ata3: SATA link down (SStatus 0 SControl 300)
[    1.689799] ata1.00: ATA-7: WDC WD1200BEVS-07LAT0, 01.06M01, max UDMA/133
[    1.689802] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 1)
[    1.690971] ata1.00: ACPI cmd ef/90:03:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    1.691132] ata1.00: configured for UDMA/133
[    1.704343] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1200BEVS-0 01.0 PQ: 0 ANSI: 5
[    1.704518] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.704561] sd 0:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    1.704613] sd 0:0:0:0: [sda] Write Protect is off
[    1.704616] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.704642] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.704784]  sda: sda1 sda2 < sda5 >
[    1.740616] sd 0:0:0:0: [sda] Attached SCSI disk
[   21.691573] scsi scan: 96 byte inquiry failed.  Consider BLIST_INQUIRY_36 for this device
[   21.694051] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T10N  PR03 PQ: 0 ANSI: 5
[   41.688531] sr0: scsi-1 drive
[   41.688537] Uniform CD-ROM driver Revision: 3.20
[   41.688677] sr 4:0:0:0: Attached scsi CD-ROM sr0
[   41.688754] sr 4:0:0:0: Attached scsi generic sg1 type 5
[   41.688857] Freeing unused kernel memory: 540k freed
[   41.689222] Write protecting the kernel text: 4568k
[   41.689281] Write protecting the kernel read-only data: 1836k
[   41.833805] Linux agpgart interface v0.103
[   41.836908] agpgart-intel 0000:00:00.0: Intel 945GM Chipset
[   41.838865] acpi device:0a: registered as cooling_device2
[   41.838991] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:07/input/input6
[   41.839038] ACPI: Video Device [IGD] (multi-head: yes  rom: no  post: no)
[   41.861061] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[   41.864155] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[   41.910675] <6>8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   41.910709] 8139cp 0000:06:05.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[   41.913302] 8139too Fast Ethernet driver 0.9.28
[   41.913339] 8139too 0000:06:05.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   41.914791] eth0: RealTek RTL8139 at 0x2000, 00:03:0d:4f:ea:b1, IRQ 16
[   41.930901] ohci1394 0000:06:04.0: enabling device (0195 -> 0197)
[   41.930911] ohci1394 0000:06:04.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   41.954205] [drm] Initialized drm 1.1.0 20060810
[   41.965939] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   41.965945] i915 0000:00:02.0: setting latency timer to 64
[   41.998056] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[f0200000-f02007ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[   42.480388] [drm] TV-14: set mode NTSC 480i 0
[   42.606489] [drm] fb0: inteldrmfb frame buffer device
[   42.606500] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   42.673501] [drm] LVDS-8: set mode 1280x800 17
[   42.890714] Console: switching to colour frame buffer device 160x50
[   43.272414] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00030d005003a224]
[   49.804079] ata5: lost interrupt (Status 0x58)
[   49.808066] ata5: drained 32768 bytes to clear DRQ.
[   49.914762] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   49.914773] ata5.00: cmd a0/01:00:00:fe:00/00:00:00:00:00/a0 tag 0 dma 16640 in
[   49.914774]          cdb 12 00 00 00 fe 00 00 00  00 00 00 00 00 00 00 00
[   49.914775]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[   49.914778] ata5.00: status: { DRDY }
[   49.914819] ata5: soft resetting link
[   50.092446] ata5.00: configured for UDMA/33
[   50.094808] ata5: EH complete
[   50.360235] PM: Starting manual resume from disk
[   50.360239] PM: Resume from partition 8:5
[   50.360242] PM: Checking hibernation image.
[   50.360365] PM: Resume from disk failed.
[   50.421885] EXT4-fs (sda1): barriers enabled
[   50.445165] kjournald2 starting: pid 384, dev sda1:8, commit interval 5 seconds
[   50.445175] EXT4-fs (sda1): delayed allocation enabled
[   50.445179] EXT4-fs: file extents enabled
[   50.452906] EXT4-fs: mballoc enabled
[   50.452921] EXT4-fs (sda1): mounted filesystem with ordered data mode
[   51.254352] type=1505 audit(1261432705.381:2): operation="profile_load" pid=407 name=/usr/share/gdm/guest-session/Xsession
[   51.257031] type=1505 audit(1261432705.383:3): operation="profile_load" pid=408 name=/sbin/dhclient3
[   51.257832] type=1505 audit(1261432705.383:4): operation="profile_load" pid=408 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   51.258264] type=1505 audit(1261432705.383:5): operation="profile_load" pid=408 name=/usr/lib/connman/scripts/dhclient-script
[   51.339148] type=1505 audit(1261432705.464:6): operation="profile_load" pid=409 name=/usr/bin/evince
[   51.352113] type=1505 audit(1261432705.479:7): operation="profile_load" pid=409 name=/usr/bin/evince-previewer
[   51.359667] type=1505 audit(1261432705.483:8): operation="profile_load" pid=409 name=/usr/bin/evince-thumbnailer
[   51.391347] type=1505 audit(1261432705.515:9): operation="profile_load" pid=411 name=/usr/lib/cups/backend/cups-pdf
[   51.392301] type=1505 audit(1261432705.519:10): operation="profile_load" pid=411 name=/usr/sbin/cupsd
[   51.430860] type=1505 audit(1261432705.555:11): operation="profile_load" pid=412 name=/usr/sbin/mysqld-akonadi
[   68.303858] EXT4-fs (sda1): warning: maximal mount count reached, running e2fsck is recommended
[   68.304060] EXT4-fs (sda1): internal journal on sda1:8
[   68.328563] udev: starting version 147
[   68.492000] intel_rng: FWH not detected
[   68.511219] Adding 4803392k swap on /dev/sda5.  Priority:-1 extents:1 across:4803392k 
[   68.538150] sdhci: Secure Digital Host Controller Interface driver
[   68.538154] sdhci: Copyright(c) Pierre Ossman
[   68.539535] sdhci-pci 0000:06:04.2: SDHCI controller found [1217:7120] (rev 1)
[   68.539558] sdhci-pci 0000:06:04.2: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   68.539583] mmc0: Unknown controller version (16). You may experience problems.
[   68.539622] Registered led device: mmc0::
[   68.539659] mmc0: SDHCI controller on PCI [0000:06:04.2] using PIO
[   68.572950] lp: driver loaded but no devices found
[   68.576086] cfg80211: Calling CRDA to update world regulatory domain
[   68.589392] cfg80211: World regulatory domain updated:
[   68.589396]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   68.589399]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   68.589402]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   68.589405]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   68.589408]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   68.589410]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   68.629514] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   68.629518] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[   68.629611] iwl3945 0000:05:00.0: enabling device (0000 -> 0002)
[   68.629624] iwl3945 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   68.629644] iwl3945 0000:05:00.0: setting latency timer to 64
[   68.649733] ip_tables: (C) 2000-2006 Netfilter Core Team
[   68.711513] iwl3945 0000:05:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   68.711518] iwl3945 0000:05:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   68.711637]   alloc irq_desc for 28 on node -1
[   68.711639]   alloc kstat_irqs on node -1
[   68.711675] iwl3945 0000:05:00.0: irq 28 for MSI/MSI-X
[   68.758553]   alloc irq_desc for 22 on node -1
[   68.758559]   alloc kstat_irqs on node -1
[   68.758569] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   68.758613] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   68.791751] eth0: link down
[   68.792037] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   68.826567] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   68.835357] psmouse serio4: ID: 10 00 64
[   68.848975] iwl3945 0000:05:00.0: firmware: requesting iwlwifi-3945-2.ucode
[   68.904812] hda_codec: Unknown model for ALC861, trying auto-probe from BIOS...
[   68.904889] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input7
[   68.934527] __ratelimit: 3 callbacks suppressed
[   68.934531] type=1505 audit(1261432723.059:13): operation="profile_replace" pid=933 name=/usr/share/gdm/guest-session/Xsession
[   68.936642] type=1505 audit(1261432723.063:14): operation="profile_replace" pid=935 name=/sbin/dhclient3
[   68.937468] type=1505 audit(1261432723.063:15): operation="profile_replace" pid=935 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   68.937907] type=1505 audit(1261432723.063:16): operation="profile_replace" pid=935 name=/usr/lib/connman/scripts/dhclient-script
[   68.953762] type=1505 audit(1261432723.079:17): operation="profile_replace" pid=939 name=/usr/bin/evince
[   68.967336] type=1505 audit(1261432723.091:18): operation="profile_replace" pid=939 name=/usr/bin/evince-previewer
[   68.974911] type=1505 audit(1261432723.099:19): operation="profile_replace" pid=939 name=/usr/bin/evince-thumbnailer
[   68.985930] type=1505 audit(1261432723.111:20): operation="profile_replace" pid=942 name=/usr/lib/cups/backend/cups-pdf
[   68.986877] type=1505 audit(1261432723.111:21): operation="profile_replace" pid=942 name=/usr/sbin/cupsd
[   68.989705] type=1505 audit(1261432723.115:22): operation="profile_replace" pid=943 name=/usr/sbin/mysqld-akonadi
[   69.203345] iwl3945 0000:05:00.0: loaded firmware version 15.32.2.9
[   69.203490] iwl3945 0000:05:00.0: Radio disabled by HW RF Kill switch
[   69.228448] iwl3945 0000:05:00.0: Radio disabled by HW RF Kill switch
[   69.489500] input: PS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio4/input/input8
[   69.941992] [drm] TV-14: set mode NTSC 480i 0
[   69.987808] ppdev: user-space parallel port driver
[   70.082188] [drm] TV-14: set mode NTSC 480i 0
[   70.359053] [drm] TV-14: set mode NTSC 480i 0
[   70.501055] [drm] TV-14: set mode NTSC 480i 0
[   72.732760] [drm] TV-14: set mode NTSC 480i 0
[   72.874186] [drm] TV-14: set mode NTSC 480i 0
[   73.151938] [drm] TV-14: set mode NTSC 480i 0
[   73.292710] [drm] TV-14: set mode NTSC 480i 0
[   73.579991] [drm] TV-14: set mode NTSC 480i 0
[   73.721733] [drm] TV-14: set mode NTSC 480i 0
[   74.686895] [drm] TV-14: set mode NTSC 480i 0
[   74.827039] [drm] TV-14: set mode NTSC 480i 0
[   74.978324] Registered led device: iwl-phy0::radio
[   74.978349] Registered led device: iwl-phy0::assoc
[   74.978407] Registered led device: iwl-phy0::RX
[   74.978427] Registered led device: iwl-phy0::TX
[   75.001143] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   75.824031] ata5: lost interrupt (Status 0x58)
[   75.905767] ata5: drained 32768 bytes to clear DRQ.
[   75.935410] ata5.00: limiting speed to UDMA/25:PIO4
[   75.935415] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   75.935427] ata5.00: cmd a0/01:00:00:fe:00/00:00:00:00:00/a0 tag 0 dma 16640 in
[   75.935429]          cdb 12 00 00 00 fe 00 00 00  00 00 00 00 00 00 00 00
[   75.935430]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[   75.935434] ata5.00: status: { DRDY }
[   75.935471] ata5: soft resetting link
[   76.124335] ata5.00: configured for UDMA/25
[   76.126655] ata5: EH complete
[   91.551824] wlan0: authenticate with AP 00:1a:2a:86:34:77
[   91.553815] wlan0: authenticated
[   91.553820] wlan0: associate with AP 00:1a:2a:86:34:77
[   91.556986] wlan0: RX AssocResp from 00:1a:2a:86:34:77 (capab=0x451 status=0 aid=1)
[   91.556993] wlan0: associated
[   91.559091] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  101.660029] wlan0: no IPv6 routers present
[  212.290149] wlan0: disassociating by local choice (reason=3)
[  222.658079] wlan0: authenticate with AP 00:1a:2a:86:34:77
[  222.668775] wlan0: authenticated
[  222.668783] wlan0: associate with AP 00:1a:2a:86:34:77
[  222.671970] wlan0: RX AssocResp from 00:1a:2a:86:34:77 (capab=0x451 status=0 aid=1)
[  222.671977] wlan0: associated
[  458.947219] CE: hpet increasing min_delta_ns to 15000 nsec
[  754.427290] CE: hpet increasing min_delta_ns to 22500 nsec
[ 1468.868163] usb 2-1: new low speed USB device using uhci_hcd and address 2
[ 1469.072312] usb 2-1: configuration #1 chosen from 1 choice
[ 1469.138992] usbcore: registered new interface driver hiddev
[ 1469.177786] input: HID 04d9:0499 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input9
[ 1469.177964] generic-usb 0003:04D9:0499.0001: input,hidraw0: USB HID v1.10 Mouse [HID 04d9:0499] on usb-0000:00:1d.0-1/input0
[ 1469.178001] usbcore: registered new interface driver usbhid
[ 1469.178007] usbhid: v2.6:USB HID core driver
[ 2385.216734] cfg80211: Found new beacon on frequency: 2467 MHz (Ch 12) on phy0

```Here is the link for the bootchart graph,

[http://i48.tinypic.com/2eyfhvd.png](http://i48.tinypic.com/2eyfhvd.png)

Waiting for your help, Thanx in Advance.

---

### Post by fanxiong on 2010-01-02
WOW! It's the most slow system what I heard.
Is there any driver have not installed apposite?

---

### Post by fanxiong on 2010-01-02
WOW! It's the most slow system what I heard.
Is there any driver have not installed apposite?

---

### Post by syncmasterpt on 2010-01-07
I have the exact same problem, with my desktop PC, and it's related to apparmor.

Removing it, or disabling it, solve the issue.

I have no idea what are the side effects off this, but I think there only related to security.

---

