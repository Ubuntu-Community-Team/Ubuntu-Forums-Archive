---
title: "Cannot get ubuntu 13.10 to read my Toshiba 1TB external HD"
date: 2014-02-05
forum: Hardware
---

### Post by thedoctor818772 on 2014-02-05
Hi everyone,

I have had a Toshiba external HD for a while now, and recently upon watching several Doctor Who episodes back-to-back, after a while, the episodes beign to "freeze" for a second or two on me. Now, the HD is not even being recognized by my ubuntu box and I am really getting worried. I run 13.10 on my Acer Aspire One netbook, and I could use some help. I am new to this area, but I am posting the results of dmesg and sudo fdisk -l:

**dmesg**

```
[    0.280087] system 00:00: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.280098] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.280141] pnp 00:01: [dma 4]
[    0.280203] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.280325] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.280567] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.280667] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.280751] pnp 00:05: Plug and Play ACPI device, IDs INT0800 (active)
[    0.280886] pnp 00:06: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.281001] pnp 00:07: Plug and Play ACPI device, IDs SYN1b20 SYN1b00 SYN0002 PNP0f13 (active)
[    0.281193] pnp: PnP ACPI: found 8 devices
[    0.281197] ACPI: bus type PNP unregistered
[    0.281205] PnPBIOS: Disabled by ACPI PNP
[    0.323662] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.323675] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.323687] pci 0000:00:1c.0:   bridge window [mem 0x95000000-0x95ffffff]
[    0.323698] pci 0000:00:1c.0:   bridge window [mem 0x90000000-0x90ffffff 64bit pref]
[    0.323712] pci 0000:00:1c.1: PCI bridge to [bus 02]
[    0.323720] pci 0000:00:1c.1:   bridge window [io  0x2000-0x2fff]
[    0.323731] pci 0000:00:1c.1:   bridge window [mem 0x94000000-0x94ffffff]
[    0.323742] pci 0000:00:1c.1:   bridge window [mem 0x91000000-0x91ffffff 64bit pref]
[    0.323754] pci 0000:00:1c.2: PCI bridge to [bus 03]
[    0.323762] pci 0000:00:1c.2:   bridge window [io  0x1000-0x1fff]
[    0.323772] pci 0000:00:1c.2:   bridge window [mem 0x93000000-0x93ffffff]
[    0.323782] pci 0000:00:1c.2:   bridge window [mem 0x92000000-0x92ffffff 64bit pref]
[    0.323794] pci 0000:00:1e.0: PCI bridge to [bus 04]
[    0.324564] pci 0000:00:1e.0: setting latency timer to 64
[    0.324576] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.324582] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.324589] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.324596] pci_bus 0000:00: resource 7 [mem 0x80000000-0xfebfffff]
[    0.324603] pci_bus 0000:01: resource 0 [io  0x3000-0x3fff]
[    0.324609] pci_bus 0000:01: resource 1 [mem 0x95000000-0x95ffffff]
[    0.324616] pci_bus 0000:01: resource 2 [mem 0x90000000-0x90ffffff 64bit pref]
[    0.324623] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    0.324629] pci_bus 0000:02: resource 1 [mem 0x94000000-0x94ffffff]
[    0.324636] pci_bus 0000:02: resource 2 [mem 0x91000000-0x91ffffff 64bit pref]
[    0.324642] pci_bus 0000:03: resource 0 [io  0x1000-0x1fff]
[    0.324649] pci_bus 0000:03: resource 1 [mem 0x93000000-0x93ffffff]
[    0.324655] pci_bus 0000:03: resource 2 [mem 0x92000000-0x92ffffff 64bit pref]
[    0.324662] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
[    0.324669] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
[    0.324675] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    0.324681] pci_bus 0000:04: resource 7 [mem 0x80000000-0xfebfffff]
[    0.324759] NET: Registered protocol family 2
[    0.325113] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.325180] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.325238] TCP: Hash tables configured (established 8192 bind 8192)
[    0.325288] TCP: reno registered
[    0.325296] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.325313] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.325479] NET: Registered protocol family 1
[    0.325517] pci 0000:00:02.0: Boot video device
[    0.340329] PCI: CLS 64 bytes, default 64
[    0.340449] Trying to unpack rootfs image as initramfs...
[    1.480278] Freeing initrd memory: 25132K (f4eda000 - f6765000)
[    1.480414] Simple Boot Flag at 0x44 set to 0x1
[    1.480822] Scanning for low memory corruption every 60 seconds
[    1.481850] Initialise module verification
[    1.482048] audit: initializing netlink socket (disabled)
[    1.482102] type=2000 audit(1391579536.480:1): initialized
[    1.570937] bounce pool size: 64 pages
[    1.570981] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.577072] zbud: loaded
[    1.577285] VFS: Disk quotas dquot_6.5.2
[    1.577490] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.579803] fuse init (API version 7.22)
[    1.580223] msgmni has been set to 1718
[    1.582129] Key type asymmetric registered
[    1.582142] Asymmetric key parser 'x509' registered
[    1.582320] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.582475] io scheduler noop registered
[    1.582488] io scheduler deadline registered (default)
[    1.582616] io scheduler cfq registered
[    1.583080] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    1.583370] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    1.583658] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    1.584049] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    1.584062] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    1.584077] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    1.584154] pcieport 0000:00:1c.1: Signaling PME through PCIe PME interrupt
[    1.584165] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt
[    1.584179] pcie_pme 0000:00:1c.1:pcie01: service driver pcie_pme loaded
[    1.584252] pcieport 0000:00:1c.2: Signaling PME through PCIe PME interrupt
[    1.584262] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
[    1.584277] pcie_pme 0000:00:1c.2:pcie01: service driver pcie_pme loaded
[    1.584349] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.584432] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.584755] intel_idle: MWAIT substates: 0x20220
[    1.584784] intel_idle: v0.4 model 0x1C
[    1.584792] intel_idle: lapic_timer_reliable_states 0x2
[    1.585504] ACPI: AC Adapter [ACAD] (on-line)
[    1.586263] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.586282] ACPI: Power Button [PWRB]
[    1.586453] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    1.586467] ACPI: Sleep Button [SLPB]
[    1.586647] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    1.586751] ACPI: Lid Switch [LID]
[    1.586957] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    1.586971] ACPI: Power Button [PWRF]
[    1.587216] ACPI: Requesting acpi_cpufreq
[    1.594694] thermal LNXTHERM:00: registered as thermal_zone0
[    1.594706] ACPI: Thermal Zone [THRM] (55 C)
[    1.594819] GHES: HEST is not enabled!
[    1.595030] isapnp: Scanning for PnP cards...
[    1.595227] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.596904] ACPI: Battery Slot [BAT1] (battery present)
[    1.602538] Linux agpgart interface v0.103
[    1.602783] agpgart-intel 0000:00:00.0: Intel GMA3150 Chipset
[    1.602985] agpgart-intel 0000:00:00.0: detected gtt size: 524288K total, 262144K mappable
[    1.603282] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    1.603668] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x80000000
[    1.610684] brd: module loaded
[    1.614341] loop: module loaded
[    1.616494] libphy: Fixed MDIO Bus: probed
[    1.617039] tun: Universal TUN/TAP device driver, 1.6
[    1.617047] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.617265] PPP generic driver version 2.4.2
[    1.617489] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.617497] ehci-pci: EHCI PCI platform driver
[    1.618005] ehci-pci 0000:00:1d.7: setting latency timer to 64
[    1.618036] ehci-pci 0000:00:1d.7: EHCI Host Controller
[    1.618061] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.618098] ehci-pci 0000:00:1d.7: debug port 1
[    1.622053] ehci-pci 0000:00:1d.7: cache line size of 64 is not supported
[    1.622124] ehci-pci 0000:00:1d.7: irq 16, io mem 0x96205000
[    1.632075] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.632150] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.632162] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.632172] usb usb1: Product: EHCI Host Controller
[    1.632182] usb usb1: Manufacturer: Linux 3.11.0-15-generic ehci_hcd
[    1.632191] usb usb1: SerialNumber: 0000:00:1d.7
[    1.632671] hub 1-0:1.0: USB hub found
[    1.632693] hub 1-0:1.0: 8 ports detected
[    1.633928] ehci-platform: EHCI generic platform driver
[    1.633978] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.633985] ohci-pci: OHCI PCI platform driver
[    1.634038] ohci-platform: OHCI generic platform driver
[    1.634089] uhci_hcd: USB Universal Host Controller Interface driver
[    1.634538] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.634553] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.634576] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.634646] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00004060
[    1.634780] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    1.634791] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.634801] usb usb2: Product: UHCI Host Controller
[    1.634811] usb usb2: Manufacturer: Linux 3.11.0-15-generic uhci_hcd
[    1.634821] usb usb2: SerialNumber: 0000:00:1d.0
[    1.635290] hub 2-0:1.0: USB hub found
[    1.635311] hub 2-0:1.0: 2 ports detected
[    1.636072] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.636092] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.636117] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.636216] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00004040
[    1.636346] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.636358] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.636368] usb usb3: Product: UHCI Host Controller
[    1.636377] usb usb3: Manufacturer: Linux 3.11.0-15-generic uhci_hcd
[    1.636387] usb usb3: SerialNumber: 0000:00:1d.1
[    1.636805] hub 3-0:1.0: USB hub found
[    1.636825] hub 3-0:1.0: 2 ports detected
[    1.637496] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.637511] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.637533] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    1.637628] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00004020
[    1.637753] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.637765] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.637775] usb usb4: Product: UHCI Host Controller
[    1.637784] usb usb4: Manufacturer: Linux 3.11.0-15-generic uhci_hcd
[    1.637794] usb usb4: SerialNumber: 0000:00:1d.3
[    1.638251] hub 4-0:1.0: USB hub found
[    1.638278] hub 4-0:1.0: 2 ports detected
[    1.638888] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.644808] i8042: Detected active multiplexing controller, rev 1.1
[    1.647693] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.647721] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.647842] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.647950] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.648103] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.648521] mousedev: PS/2 mouse device common for all mice
[    1.649418] rtc_cmos 00:02: RTC can wake from S4
[    1.649742] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.649803] rtc_cmos 00:02: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.650089] device-mapper: uevent: version 1.0.3
[    1.650384] device-mapper: ioctl: 4.25.0-ioctl (2013-06-26) initialised: dm-devel@redhat.com
[    1.650479] platform eisa.0: Probing EISA bus 0
[    1.650562] platform eisa.0: EISA: Detected 0 cards
[    1.650587] cpufreq-nforce2: No nForce2 chipset.
[    1.650914] cpuidle: using governor ladder
[    1.651342] cpuidle: using governor menu
[    1.651399] ledtrig-cpu: registered to indicate activity on CPUs
[    1.651759] TCP: cubic registered
[    1.652331] NET: Registered protocol family 10
[    1.653059] NET: Registered protocol family 17
[    1.653110] Key type dns_resolver registered
[    1.653903] Using IPI No-Shortcut mode
[    1.654432] PM: Hibernation image not present or could not be loaded.
[    1.654451] Loading module verification certificates
[    1.673184] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 5f32dde6ae99ae14b29fb35e935289fb4b6cfb20'
[    1.673233] registered taskstats version 1
[    1.683185] Key type trusted registered
[    1.688098] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.691578] Key type encrypted registered
[    1.701430] AppArmor: AppArmor sha1 policy hashing enabled
[    1.702359]   Magic number: 2:217:870
[    1.702575] rtc_cmos 00:02: setting system clock to 2014-02-05 05:52:17 UTC (1391579537)
[    1.705272] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.705277] EDD information not available.
[    1.944091] usb 1-3: new high-speed USB device number 2 using ehci-pci
[    1.949564] isapnp: No Plug & Play device found
[    1.950328] Freeing unused kernel memory: 880K (c1972000 - c1a4e000)
[    1.950473] Write protecting the kernel text: 6360k
[    1.950639] Write protecting the kernel read-only data: 2700k
[    1.950645] NX-protecting the kernel data: 5928k
[    1.990129] systemd-udevd[110]: starting version 204
[    2.045605] wmi: Mapper loaded
[    2.090695] rtsx_pci 0000:03:00.0: irq 43 for MSI/MSI-X
[    2.090732] rtsx_pci 0000:03:00.0: rtsx_pci_acquire_irq: pcr->msi_en = 1, pci->irq = 43
[    2.113965] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.115165] r8169 0000:01:00.0: irq 44 for MSI/MSI-X
[    2.115693] r8169 0000:01:00.0 eth0: RTL8105e at 0xf8440000, e8:9a:8f:77:bf:68, XID 00a00000 IRQ 44
[    2.124687] ahci 0000:00:1f.2: version 3.0
[    2.124706] [drm] Initialized drm 1.1.0 20060810
[    2.125091] ahci 0000:00:1f.2: irq 45 for MSI/MSI-X
[    2.125174] ahci: SSS flag set, parallel bus scan disabled
[    2.125224] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0x3 impl SATA mode
[    2.125233] ahci 0000:00:1f.2: flags: 64bit ncq ilck stag pm led clo pmp pio slum part 
[    2.125244] ahci 0000:00:1f.2: setting latency timer to 64
[    2.126675] scsi0 : ahci
[    2.126946] scsi1 : ahci
[    2.127202] scsi2 : ahci
[    2.128242] scsi3 : ahci
[    2.128521] ata1: SATA max UDMA/133 abar m1024@0x96204000 port 0x96204100 irq 45
[    2.128530] ata2: SATA max UDMA/133 abar m1024@0x96204000 port 0x96204180 irq 45
[    2.128534] ata3: DUMMY
[    2.128538] ata4: DUMMY
[    2.222345] usb 1-3: New USB device found, idVendor=0402, idProduct=7675
[    2.222357] usb 1-3: New USB device strings: Mfr=3, Product=1, SerialNumber=0
[    2.222366] usb 1-3: Product: WebCam
[    2.222374] usb 1-3: Manufacturer: Y2B6N06TX
[    2.268788] [drm] Memory usable by graphics device = 512M
[    2.268807] i915 0000:00:02.0: setting latency timer to 64
[    2.269314] i915 0000:00:02.0: irq 46 for MSI/MSI-X
[    2.269336] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    2.269341] [drm] Driver supports precise vblank timestamp query.
[    2.269454] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    2.359087] [drm] initialized overlay support
[    2.620194] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.621773] ata1.00: unexpected _GTF length (4)
[    2.622189] ata1.00: ATA-8: ST9320325AS, 0003BSM1, max UDMA/133
[    2.622199] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.624190] ata1.00: unexpected _GTF length (4)
[    2.624577] ata1.00: configured for UDMA/133
[    2.624938] scsi 0:0:0:0: Direct-Access     ATA      ST9320325AS      0003 PQ: 0 ANSI: 5
[    2.625526] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    2.625544] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.625733] sd 0:0:0:0: [sda] Write Protect is off
[    2.625744] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.625826] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.643658]  sda: sda1 sda2 < sda5 >
[    2.644679] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.727482] fbcon: inteldrmfb (fb0) is primary device
[    2.944176] ata2: SATA link down (SStatus 0 SControl 300)
[    3.112145] Console: switching to colour frame buffer device 128x37
[    3.120759] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    3.120765] i915 0000:00:02.0: registered panic notifier
[    3.138068] acpi device:28: registered as cooling_device4
[    3.138548] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    3.138708] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5
[    3.138990] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   15.102000] bio: create slab <bio-1> at 1
[   15.456691] bio: create slab <bio-1> at 1
[   21.907789] EXT4-fs (dm-1): INFO: recovery required on readonly filesystem
[   21.907798] EXT4-fs (dm-1): write access will be enabled during recovery
[   25.448884] EXT4-fs (dm-1): orphan cleanup on readonly fs
[   25.449119] EXT4-fs (dm-1): 1 orphan inode deleted
[   25.449125] EXT4-fs (dm-1): recovery complete
[   25.545156] EXT4-fs (dm-1): mounted filesystem with ordered data mode. Opts: (null)
[   36.079885] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   36.274898] systemd-udevd[388]: starting version 204
[   36.450851] EXT4-fs (dm-1): re-mounted. Opts: errors=remount-ro
[   36.493289] lp: driver loaded but no devices found
[   36.871182] ACPI Warning: 0x00000428-0x0000042f SystemIO conflicts with Region \PMBA 1 (20130517/utaddress-251)
[   36.871206] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   36.871218] ACPI Warning: 0x00000530-0x0000053f SystemIO conflicts with Region \GPIO 1 (20130517/utaddress-251)
[   36.871233] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   36.871240] ACPI Warning: 0x00000500-0x0000052f SystemIO conflicts with Region \GPIO 1 (20130517/utaddress-251)
[   36.871254] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   36.871261] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   36.875821] cfg80211: Calling CRDA to update world regulatory domain
[   36.931015] Intel(R) Wireless WiFi driver for Linux, in-tree:
[   36.931027] Copyright(c) 2003-2013 Intel Corporation
[   36.931571] iwlwifi 0000:02:00.0: irq 47 for MSI/MSI-X
[   37.186125] iwlwifi 0000:02:00.0: loaded firmware version 39.31.5.1 build 32895 op_mode iwldvm
[   37.194607] type=1400 audit(1391579572.987:2): apparmor="STATUS" operation="profile_load" parent=529 profile="unconfined" name="/sbin/dhclient" pid=607 comm="apparmor_parser"
[   37.194635] type=1400 audit(1391579572.987:3): apparmor="STATUS" operation="profile_load" parent=529 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=607 comm="apparmor_parser"
[   37.194656] type=1400 audit(1391579572.987:4): apparmor="STATUS" operation="profile_load" parent=529 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=607 comm="apparmor_parser"
[   37.197330] type=1400 audit(1391579572.991:5): apparmor="STATUS" operation="profile_replace" parent=529 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=607 comm="apparmor_parser"
[   37.197361] type=1400 audit(1391579572.991:6): apparmor="STATUS" operation="profile_replace" parent=529 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=607 comm="apparmor_parser"
[   37.198761] type=1400 audit(1391579572.991:7): apparmor="STATUS" operation="profile_replace" parent=529 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=607 comm="apparmor_parser"
[   37.247051] microcode: CPU0 sig=0x106ca, pf=0x10, revision=0x107
[   37.397309] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   37.397320] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   37.397328] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   37.397336] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_P2P disabled
[   37.397345] iwlwifi 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N 100 BGN, REV=0x6C
[   37.397495] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   37.453849] Linux video capture interface: v2.00
[   37.498550] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   37.610613] uvcvideo: Found UVC 1.00 device WebCam (0402:7675)
[   37.617027] input: WebCam as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3:1.0/input/input6
[   37.617551] usbcore: registered new interface driver uvcvideo
[   37.617560] USB Video Class driver (1.1.1)
[   38.027969] snd_hda_intel 0000:00:1b.0: irq 48 for MSI/MSI-X
[   38.029202] psmouse serio2: synaptics: Touchpad model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04733/0xa40000/0xa0000, board id: 3655, fw id: 528321
[   38.073556] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input7
[   38.093834] hda_codec: ALC269VB: SKU not ready 0x598301f0
[   38.094541] autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[   38.094551]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   38.094559]    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[   38.094565]    mono: mono_out=0x0
[   38.094570]    inputs:
[   38.094578]      Internal Mic=0x1b
[   38.094584]      Mic=0x18
[   38.094591] realtek: No valid SSID, checking pincfg 0x598301f0 for NID 0x1d
[   38.094597] realtek: Enable default setup for auto mode as fallback
[   38.120429] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   38.120744] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   38.372417] microcode: CPU1 sig=0x106ca, pf=0x10, revision=0x107
[   38.380125] acer_wmi: Acer Laptop ACPI-WMI Extras
[   38.380169] acer_wmi: Function bitmap for Communication Button: 0x1
[   38.380184] acer_wmi: Brightness must be controlled by acpi video driver
[   38.382229] input: Acer WMI hotkeys as /devices/virtual/input/input10
[   38.383471] input: Acer BMA150 accelerometer as /devices/virtual/input/input11
[   38.513892] Bluetooth: Core ver 2.16
[   38.513981] NET: Registered protocol family 31
[   38.513988] Bluetooth: HCI device and connection manager initialized
[   38.514013] Bluetooth: HCI socket layer initialized
[   38.514028] Bluetooth: L2CAP socket layer initialized
[   38.514054] Bluetooth: SCO socket layer initialized
[   38.535157] cfg80211: World regulatory domain updated:
[   38.535173] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   38.535182] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   38.535191] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   38.535199] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   38.535207] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   38.535215] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   38.585429] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   38.585442] Bluetooth: BNEP filters: protocol multicast
[   38.585470] Bluetooth: BNEP socket layer initialized
[   38.600248] Bluetooth: RFCOMM TTY layer initialized
[   38.600288] Bluetooth: RFCOMM socket layer initialized
[   38.600296] Bluetooth: RFCOMM ver 1.11
[   38.607770] microcode: CPU2 sig=0x106ca, pf=0x10, revision=0x107
[   38.626055] microcode: CPU3 sig=0x106ca, pf=0x10, revision=0x107
[   38.630501] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   38.772401] kvm: disabled by bios
[   39.405413] init: failsafe main process (1066) killed by TERM signal
[   39.782483] ppdev: user-space parallel port driver
[   40.088894] init: avahi-cups-reload main process (1161) terminated with status 1
[   40.212376] type=1400 audit(1391579576.007:8): apparmor="STATUS" operation="profile_load" parent=1181 profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=1197 comm="apparmor_parser"
[   40.212407] type=1400 audit(1391579576.007:9): apparmor="STATUS" operation="profile_load" parent=1181 profile="unconfined" name="/usr/sbin/cupsd" pid=1197 comm="apparmor_parser"
[   40.215258] type=1400 audit(1391579576.007:10): apparmor="STATUS" operation="profile_replace" parent=1181 profile="unconfined" name="/usr/sbin/cupsd" pid=1197 comm="apparmor_parser"
[   40.377420] type=1400 audit(1391579576.171:11): apparmor="STATUS" operation="profile_replace" parent=1231 profile="unconfined" name="/sbin/dhclient" pid=1239 comm="apparmor_parser"
[   43.575040] r8169 0000:01:00.0 eth2: link down
[   43.575124] IPv6: ADDRCONF(NETDEV_UP): eth2: link is not ready
[   43.576315] IPv6: ADDRCONF(NETDEV_UP): eth2: link is not ready
[   43.583613] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   43.591090] iwlwifi 0000:02:00.0: Radio type=0x0-0x0-0x3
[   43.628947] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   43.636425] iwlwifi 0000:02:00.0: Radio type=0x0-0x0-0x3
[   43.669606] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[   43.670424] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[   44.679827] wlan2: authenticate with ec:1a:59:06:76:58
[   44.693016] wlan2: send auth to ec:1a:59:06:76:58 (try 1/3)
[   44.695953] wlan2: authenticated
[   44.700121] wlan2: associate with ec:1a:59:06:76:58 (try 1/3)
[   44.703436] wlan2: RX AssocResp from ec:1a:59:06:76:58 (capab=0x411 status=0 aid=1)
[   44.705914] wlan2: associated
[   44.707157] IPv6: ADDRCONF(NETDEV_CHANGE): wlan2: link becomes ready
[   58.185419] Adding 2080764k swap on /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:2080764k FS
[   94.216151] usb 1-2: new high-speed USB device number 3 using ehci-pci
[   94.349639] usb 1-2: New USB device found, idVendor=0480, idProduct=a006
[   94.349652] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[   94.349659] usb 1-2: Product: External USB 3.0
[   94.349665] usb 1-2: Manufacturer: Toshiba
[   94.349671] usb 1-2: SerialNumber: 2012122245364
[   94.455317] usb-storage 1-2:1.0: USB Mass Storage device detected
[   94.455631] scsi4 : usb-storage 1-2:1.0
[   94.456000] usbcore: registered new interface driver usb-storage
[  116.944126] usb 1-2: reset high-speed USB device number 3 using ehci-pci
[  117.196132] usb 1-2: reset high-speed USB device number 3 using ehci-pci
[  123.448142] usb 1-2: reset high-speed USB device number 3 using ehci-pci
[  123.696166] usb 1-2: reset high-speed USB device number 3 using ehci-pci
[  123.948206] usb 1-2: reset high-speed USB device number 3 using ehci-pci
[  124.081048] scsi 4:0:0:0: Device offlined - not ready after error recovery
[  167.138418] usb 1-2: USB disconnect, device number 3
[  173.932473] perf samples too long (2532 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[  257.916145] usb 1-1: new high-speed USB device number 4 using ehci-pci
[  258.049748] usb 1-1: New USB device found, idVendor=0480, idProduct=a006
[  258.049761] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  258.049771] usb 1-1: Product: External USB 3.0
[  258.049779] usb 1-1: Manufacturer: Toshiba
[  258.049787] usb 1-1: SerialNumber: 2012122245364
[  258.050365] usb-storage 1-1:1.0: USB Mass Storage device detected
[  258.052847] scsi5 : usb-storage 1-1:1.0
[  279.952152] usb 1-1: reset high-speed USB device number 4 using ehci-pci
[  280.204238] usb 1-1: reset high-speed USB device number 4 using ehci-pci
[  286.456252] usb 1-1: reset high-speed USB device number 4 using ehci-pci
[  286.704163] usb 1-1: reset high-speed USB device number 4 using ehci-pci
[  286.956143] usb 1-1: reset high-speed USB device number 4 using ehci-pci
[  287.089010] scsi 5:0:0:0: Device offlined - not ready after error recovery
[  319.828331] perf samples too long (5019 > 5000), lowering kernel.perf_event_max_sample_rate to 25000
[  431.599998] usb 1-1: USB disconnect, device number 4
[  514.240468] usb 1-2: new high-speed USB device number 5 using ehci-pci
[  514.373823] usb 1-2: New USB device found, idVendor=0480, idProduct=a006
[  514.373840] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  514.373852] usb 1-2: Product: External USB 3.0
[  514.373862] usb 1-2: Manufacturer: Toshiba
[  514.373872] usb 1-2: SerialNumber: 2012122245364
[  514.374729] usb-storage 1-2:1.0: USB Mass Storage device detected
[  514.375534] scsi6 : usb-storage 1-2:1.0
[  533.555064] scsi 6:0:0:0: Direct-Access     TOSHIBA  External USB 3.0 0001 PQ: 1 ANSI: 6
[  533.556165] scsi 6:0:0:0: Attached scsi generic sg1 type 0
[  658.534664] usb 1-2: USB disconnect, device number 5
[  662.976103] usb 1-2: new high-speed USB device number 6 using ehci-pci
[  663.109779] usb 1-2: New USB device found, idVendor=0480, idProduct=a006
[  663.109795] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  663.109806] usb 1-2: Product: External USB 3.0
[  663.109816] usb 1-2: Manufacturer: Toshiba
[  663.109825] usb 1-2: SerialNumber: 2012122245364
[  663.110538] usb-storage 1-2:1.0: USB Mass Storage device detected
[  663.110892] scsi7 : usb-storage 1-2:1.0
[  685.136166] usb 1-2: reset high-speed USB device number 6 using ehci-pci
[  685.388116] usb 1-2: reset high-speed USB device number 6 using ehci-pci
[  691.640147] usb 1-2: reset high-speed USB device number 6 using ehci-pci
[  691.888110] usb 1-2: reset high-speed USB device number 6 using ehci-pci
[  692.140149] usb 1-2: reset high-speed USB device number 6 using ehci-pci
[  692.273039] scsi 7:0:0:0: Device offlined - not ready after error recovery
[  994.251758] usb 1-2: USB disconnect, device number 6
[  997.528148] usb 1-1: new high-speed USB device number 7 using ehci-pci
[  997.661770] usb 1-1: New USB device found, idVendor=0480, idProduct=a006
[  997.661786] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  997.661798] usb 1-1: Product: External USB 3.0
[  997.661808] usb 1-1: Manufacturer: Toshiba
[  997.661817] usb 1-1: SerialNumber: 2012122245364
[  997.662602] usb-storage 1-1:1.0: USB Mass Storage device detected
[  997.663016] scsi8 : usb-storage 1-1:1.0
[ 1020.112087] usb 1-1: reset high-speed USB device number 7 using ehci-pci
[ 1020.368240] usb 1-1: reset high-speed USB device number 7 using ehci-pci
[ 1026.620137] usb 1-1: reset high-speed USB device number 7 using ehci-pci
[ 1026.868175] usb 1-1: reset high-speed USB device number 7 using ehci-pci
[ 1027.120079] usb 1-1: reset high-speed USB device number 7 using ehci-pci
[ 1027.253028] scsi 8:0:0:0: Device offlined - not ready after error recovery


```

[B]sudo fdisk -l


[/B][CODE]
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009def2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   625141759   312320001    5  Extended
/dev/sda5          501760   625141759   312320000   83  Linux

Disk /dev/mapper/sda5_crypt: 319.8 GB, 319813582848 bytes
255 heads, 63 sectors/track, 38881 cylinders, total 624635904 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/sda5_crypt doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--vg-root: 317.7 GB, 317664002048 bytes
255 heads, 63 sectors/track, 38620 cylinders, total 620437504 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--vg-swap_1: 2130 MB, 2130706432 bytes
255 heads, 63 sectors/track, 259 cylinders, total 4161536 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-swap_1 doesn't contain a valid partition table

Disk /dev/mapper/cryptswap1: 2130 MB, 2130706432 bytes
255 heads, 63 sectors/track, 259 cylinders, total 4161536 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8f97666f

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table
[CODE]

I wouls appreciate any help that anyone could be in this matter as I have nearly 85% of the HD full of movies at this point and would really hate to be looinsg all of that.........

-Michael Dykes

---

### Post by fdrake on 2014-02-05
try this enter recovery mode from the grub menu (by pressing "shift" if it doesn't show up) and enter the root selectio and run this command:
fsck -Vy /dev/sda5

---

### Post by thedoctor818772 on 2014-02-08
> **fdrake said:**
> try this enter recovery mode from the grub menu (by pressing "shift" if it doesn't show up) and enter the root selectio and run this command:
fsck -Vy /dev/sda5

I am still new to this so please bear with me. This is an external hard drive I am having trouble with so how do I do what you are asking/advising me to do, I mean when do I enter that command? I tried but to no avail. Sometimes the external HD allow my machine to read it, but even then it acts rather odd and I cannot ,e.g., delete things from the drive and while watching movies from it they often freeze in the middle. Help please! Thanks.

---

