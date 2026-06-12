---
title: "VERY slow boot times"
date: 2011-07-29
forum: Hardware
---

### Post by horsemanoffaith on 2011-07-29
Hi there, I am having a SERIOUS boot-up problem. I'm running Ubuntu 11.04 on an Dell Inspiron 9300 laptop. I've had Natty installed for quite some time and until now, I've had very little trouble. Just a couple of days ago I tried booting up my laptop and found that my usually fast (around 1 minute) boot times were a thing of the past. It goes through its normal process, then hangs up about 40 seconds into the boot process. When this happens, my hard drive light blinks about once every 8 seconds for almost 2 minutes. Ubuntu finally loads, but this long boot time is driving me CRAZY. Can someone out there help me? Here's the output of dmesg from my last boot:


[    0.253871] pnp 00:05: [io  0x0066]
[    0.253882] pnp 00:05: [irq 1]
[    0.253958] pnp 00:05: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.254001] pnp 00:06: [io  0x0070-0x0071]
[    0.254013] pnp 00:06: [irq 8]
[    0.254019] pnp 00:06: [io  0x0072-0x0077]
[    0.254103] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.254151] pnp 00:07: [io  0x0061]
[    0.254157] pnp 00:07: [io  0x0063]
[    0.254163] pnp 00:07: [io  0x0065]
[    0.254168] pnp 00:07: [io  0x0067]
[    0.254245] pnp 00:07: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.254289] pnp 00:08: [io  0x002e-0x002f]
[    0.254296] pnp 00:08: [io  0x0900-0x090f]
[    0.254301] pnp 00:08: [io  0x0910-0x091f]
[    0.254307] pnp 00:08: [io  0x0920-0x092f]
[    0.254313] pnp 00:08: [io  0x0930-0x093f]
[    0.254319] pnp 00:08: [io  0x0940-0x097f]
[    0.254443] system 00:08: [io  0x0900-0x090f] has been reserved
[    0.254451] system 00:08: [io  0x0910-0x091f] has been reserved
[    0.254459] system 00:08: [io  0x0920-0x092f] has been reserved
[    0.254467] system 00:08: [io  0x0930-0x093f] has been reserved
[    0.254475] system 00:08: [io  0x0940-0x097f] has been reserved
[    0.254483] system 00:08: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.254534] pnp 00:09: [dma 4]
[    0.254540] pnp 00:09: [io  0x0000-0x000f]
[    0.254556] pnp 00:09: [io  0x0080-0x0085]
[    0.254562] pnp 00:09: [io  0x0087-0x008f]
[    0.254568] pnp 00:09: [io  0x00c0-0x00df]
[    0.254574] pnp 00:09: [io  0x0010-0x001f]
[    0.254580] pnp 00:09: [io  0x0090-0x0091]
[    0.254586] pnp 00:09: [io  0x0093-0x009f]
[    0.254666] pnp 00:09: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.254709] pnp 00:0a: [io  0x00f0-0x00ff]
[    0.254722] pnp 00:0a: [irq 13]
[    0.254802] pnp 00:0a: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.255433] pnp: PnP ACPI: found 11 devices
[    0.255438] ACPI: ACPI bus type pnp unregistered
[    0.255446] PnPBIOS: Disabled by ACPI PNP
[    0.295057] pci 0000:00:1e.0: BAR 15: assigned [mem 0x40000000-0x43ffffff pref]
[    0.295069] pci 0000:00:1e.0: BAR 13: assigned [io  0x2000-0x2fff]
[    0.295077] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.295083] pci 0000:00:01.0:   bridge window [io  disabled]
[    0.295092] pci 0000:00:01.0:   bridge window [mem 0xdd000000-0xdfefffff]
[    0.295101] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff pref]
[    0.295116] pci 0000:03:01.0: BAR 15: assigned [mem 0x40000000-0x43ffffff pref]
[    0.295127] pci 0000:03:01.0: BAR 16: assigned [mem 0x44000000-0x47ffffff]
[    0.295135] pci 0000:03:01.0: BAR 0: assigned [mem 0xdcf00000-0xdcf00fff]
[    0.295148] pci 0000:03:01.0: BAR 0: set to [mem 0xdcf00000-0xdcf00fff] (PCI address [0xdcf00000-0xdcf00fff])
[    0.295157] pci 0000:03:01.0: BAR 13: assigned [io  0x2000-0x20ff]
[    0.295164] pci 0000:03:01.0: BAR 14: assigned [io  0x2400-0x24ff]
[    0.295171] pci 0000:03:01.0: CardBus bridge to [bus 04-07]
[    0.295178] pci 0000:03:01.0:   bridge window [io  0x2000-0x20ff]
[    0.295188] pci 0000:03:01.0:   bridge window [io  0x2400-0x24ff]
[    0.295198] pci 0000:03:01.0:   bridge window [mem 0x40000000-0x43ffffff pref]
[    0.295208] pci 0000:03:01.0:   bridge window [mem 0x44000000-0x47ffffff]
[    0.295218] pci 0000:00:1e.0: PCI bridge to [bus 03-04]
[    0.295226] pci 0000:00:1e.0:   bridge window [io  0x2000-0x2fff]
[    0.295237] pci 0000:00:1e.0:   bridge window [mem 0xdcf00000-0xdcffffff]
[    0.295248] pci 0000:00:1e.0:   bridge window [mem 0x40000000-0x43ffffff pref]
[    0.295285] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.295295] pci 0000:00:01.0: setting latency timer to 64
[    0.295308] pci 0000:00:1e.0: setting latency timer to 64
[    0.295321] pci 0000:03:01.0: enabling device (0000 -> 0003)
[    0.295338] pci 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.295351] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.295358] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.295366] pci_bus 0000:01: resource 1 [mem 0xdd000000-0xdfefffff]
[    0.295373] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff pref]
[    0.295380] pci_bus 0000:03: resource 0 [io  0x2000-0x2fff]
[    0.295387] pci_bus 0000:03: resource 1 [mem 0xdcf00000-0xdcffffff]
[    0.295395] pci_bus 0000:03: resource 2 [mem 0x40000000-0x43ffffff pref]
[    0.295402] pci_bus 0000:03: resource 4 [io  0x0000-0xffff]
[    0.295409] pci_bus 0000:03: resource 5 [mem 0x00000000-0xffffffff]
[    0.295416] pci_bus 0000:04: resource 0 [io  0x2000-0x20ff]
[    0.295423] pci_bus 0000:04: resource 1 [io  0x2400-0x24ff]
[    0.295430] pci_bus 0000:04: resource 2 [mem 0x40000000-0x43ffffff pref]
[    0.295437] pci_bus 0000:04: resource 3 [mem 0x44000000-0x47ffffff]
[    0.295519] NET: Registered protocol family 2
[    0.295689] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.296232] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.297744] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.298508] TCP: Hash tables configured (established 131072 bind 65536)
[    0.298514] TCP reno registered
[    0.298522] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.298547] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.298774] NET: Registered protocol family 1
[    0.298964] pci 0000:01:00.0: Boot video device
[    0.298995] PCI: CLS 64 bytes, default 64
[    0.299143] Simple Boot Flag at 0x79 set to 0x1
[    0.299399] cpufreq-nforce2: No nForce2 chipset.
[    0.299751] audit: initializing netlink socket (disabled)
[    0.299774] type=2000 audit(1311891503.292:1): initialized
[    0.325506] Trying to unpack rootfs image as initramfs...
[    0.356887] highmem bounce pool size: 64 pages
[    0.356901] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.372371] VFS: Disk quotas dquot_6.5.2
[    0.372532] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.374424] fuse init (API version 7.16)
[    0.374686] msgmni has been set to 1704
[    0.380694] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.380756] io scheduler noop registered
[    0.380762] io scheduler deadline registered
[    0.380805] io scheduler cfq registered (default)
[    0.381065] pcieport 0000:00:01.0: setting latency timer to 64
[    0.381124] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.381296] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.381361] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.382056] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.382651] ACPI: AC Adapter [AC] (on-line)
[    0.383823] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.384374] ACPI: Lid Switch [LID]
[    0.384506] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.384520] ACPI: Power Button [PBTN]
[    0.384651] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.384660] ACPI: Sleep Button [SBTN]
[    0.384977] ACPI: acpi_idle registered with cpuidle
[    0.385289] Marking TSC unstable due to TSC halts in idle
[    0.395651] thermal LNXTHERM:00: registered as thermal_zone0
[    0.395658] ACPI: Thermal Zone [THM] (53 C)
[    0.400705] ERST: Table is not found!
[    0.400852] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.404114] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.404132] ACPI: Battery Slot [BAT0] (battery absent)
[    0.404204] isapnp: Scanning for PnP cards...
[    0.453419] Linux agpgart interface v0.103
[    0.462149] brd: module loaded
[    0.463853] loop: module loaded
[    0.468107] i2c-core: driver [adp5520] using legacy suspend method
[    0.468114] i2c-core: driver [adp5520] using legacy resume method
[    0.468334] ata_piix 0000:00:1f.2: version 2.13
[    0.468378] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.468390] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    0.636066] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.648391] scsi0 : ata_piix
[    0.652411] scsi1 : ata_piix
[    0.653659] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    0.653667] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    0.654752] Fixed MDIO Bus: probed
[    0.654862] PPP generic driver version 2.4.2
[    0.655008] tun: Universal TUN/TAP device driver, 1.6
[    0.655014] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.655250] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.655291] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.655323] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.655331] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.655431] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.655494] ehci_hcd 0000:00:1d.7: debug port 1
[    0.659394] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.664119] ehci_hcd 0000:00:1d.7: irq 16, io mem 0xffa80800
[    0.676034] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.676407] hub 1-0:1.0: USB hub found
[    0.676419] hub 1-0:1.0: 8 ports detected
[    0.676617] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.676653] uhci_hcd: USB Universal Host Controller Interface driver
[    0.676727] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.676743] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.676751] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.676851] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.676892] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000bf80
[    0.677192] hub 2-0:1.0: USB hub found
[    0.677203] hub 2-0:1.0: 2 ports detected
[    0.677357] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.677370] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.677377] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.677469] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.677529] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000bf60
[    0.677832] hub 3-0:1.0: USB hub found
[    0.677842] hub 3-0:1.0: 2 ports detected
[    0.678015] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.678029] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.678036] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.678132] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.678193] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000bf40
[    0.678494] hub 4-0:1.0: USB hub found
[    0.678505] hub 4-0:1.0: 2 ports detected
[    0.678663] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.678676] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.678684] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.678781] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.678841] uhci_hcd 0000:00:1d.3: irq 19, io base 0x0000bf20
[    0.679145] hub 5-0:1.0: USB hub found
[    0.679156] hub 5-0:1.0: 2 ports detected
[    0.679466] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.732887] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.732904] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.737120] mousedev: PS/2 mouse device common for all mice
[    0.737521] rtc_cmos 00:06: RTC can wake from S4
[    0.737637] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.737681] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.737954] device-mapper: uevent: version 1.0.3
[    0.738161] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: [email]dm-devel@redhat.com[/email]
[    0.738300] device-mapper: multipath: version 1.2.0 loaded
[    0.738307] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.738501] EISA: Probing bus 0 at eisa.0
[    0.738514] Cannot allocate resource for EISA slot 1
[    0.738520] Cannot allocate resource for EISA slot 2
[    0.738555] EISA: Detected 0 cards.
[    0.743710] cpuidle: using governor ladder
[    0.743884] cpuidle: using governor menu
[    0.744570] TCP cubic registered
[    0.744938] NET: Registered protocol family 10
[    0.746320] NET: Registered protocol family 17
[    0.746364] Registering the dns_resolver key type
[    0.747040] Using IPI No-Shortcut mode
[    0.747270] PM: Hibernation image not present or could not be loaded.
[    0.747293] registered taskstats version 1
[    0.747682]   Magic number: 3:716:351
[    0.747826] rtc_cmos 00:06: setting system clock to 2011-07-28 22:18:24 UTC (1311891504)
[    0.747834] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.747838] EDD information not available.
[    0.748151] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.836700] ata2.00: ATAPI: SONY DVD+/-RW DW-D56A, PDS7, max UDMA/33
[    0.852398] ata2.00: configured for UDMA/33
[    0.853559] ata1.00: ATA-6: TOSHIBA MK8026GAX, PA002D, max UDMA/100
[    0.853567] ata1.00: 156301488 sectors, multi 8: LBA 
[    0.853576] ata1.00: applying bridge limits
[    0.903949] ata1.00: configured for UDMA/100
[    1.031888] isapnp: No Plug & Play device found
[    1.032202] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK8026GA PA00 PQ: 0 ANSI: 5
[    1.032654] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.033006] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.033334] sd 0:0:0:0: [sda] Write Protect is off
[    1.033342] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.033406] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.033691] scsi 1:0:0:0: CD-ROM            SONY     DVD+-RW DW-D56A  PDS7 PQ: 0 ANSI: 5
[    1.035716] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.035724] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.035993] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.036166] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.137361]  sda: sda1 sda2 < sda5 sda6 >
[    1.138236] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.384053] usb 4-1: new low speed USB device using uhci_hcd and address 2
[    1.606093] Freeing initrd memory: 12564k freed
[    1.618167] Freeing unused kernel memory: 700k freed
[    1.618913] Write protecting the kernel text: 5192k
[    1.619016] Write protecting the kernel read-only data: 2148k
[    1.702244] <30>udev[79]: starting version 167
[    2.227765] sdhci: Secure Digital Host Controller Interface driver
[    2.227772] sdhci: Copyright(c) Pierre Ossman
[    2.291544] sdhci-pci 0000:03:01.2: SDHCI controller found [1180:0822] (rev 17)
[    2.291572] sdhci-pci 0000:03:01.2: PCI INT C -> GSI 17 (level, low) -> IRQ 17
[    2.292635] mmc0: no vmmc regulator found
[    2.301198] Registered led device: mmc0::
[    2.302464] mmc0: SDHCI controller on PCI [0000:03:01.2] using DMA
[    2.356315] firewire_ohci 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    2.430143] firewire_ohci: Added fw-ohci device 0000:03:01.1, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x1
[    2.432241] b44 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.442418] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input4
[    2.442927] generic-usb 0003:046D:C01D.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.2-1/input0
[    2.443307] usbcore: registered new interface driver usbhid
[    2.443313] usbhid: USB HID core driver
[    2.452185] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[    2.452199] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[    2.452211] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[    2.505407] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[    2.505816] b44: b44.c:v2.0
[    2.514528] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    2.525752] b44 ssb0:0: eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:12:3f:d6:90:54
[    2.936245] firewire_core: created device fw0: GUID 434fc0001564d8e1, S400
[    5.515877] Adding 1663996k swap on /dev/sda6.  Priority:-1 extents:1 across:1663996k 
[    6.635004] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[    6.640390] <30>udev[273]: starting version 167
[    8.192072] lp: driver loaded but no devices found
[    8.476088] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[    8.910092] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input5
[    8.928952] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input6
[    9.107666] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:21/LNXVIDEO:00/input/input7
[    9.107966] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[    9.121538] intel_rng: FWH not detected
[    9.753648] lib80211: common routines for IEEE802.11 drivers
[    9.753657] lib80211_crypt: registered algorithm 'NULL'
[    9.755338] yenta_cardbus 0000:03:01.0: CardBus bridge found [1028:0189]
[    9.880843] yenta_cardbus 0000:03:01.0: ISA IRQ mask 0x0cb8, PCI irq 19
[    9.880853] yenta_cardbus 0000:03:01.0: Socket status: 30000006
[    9.880862] pci_bus 0000:03: Raising subordinate bus# of parent bus (#03) from #04 to #07
[    9.880881] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge window: [io  0x2000-0x2fff]
[    9.880890] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x2000-0x2fff: excluding 0x2000-0x20ff 0x23b0-0x23df 0x2400-0x24ff 0x27b0-0x27df 0x2bb0-0x2bdf 0x2fb0-0x2fdf
[    9.887075] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge window: [mem 0xdcf00000-0xdcffffff]
[    9.887085] pcmcia_socket pcmcia_socket0: cs: memory probe 0xdcf00000-0xdcffffff: excluding 0xdcf00000-0xdcf0ffff 0xdcff0000-0xdcffffff
[    9.887120] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge window: [mem 0x40000000-0x43ffffff pref]
[    9.887129] pcmcia_socket pcmcia_socket0: cs: memory probe 0x40000000-0x43ffffff: excluding 0x40000000-0x43ffffff
[   10.091782] cfg80211: Calling CRDA to update world regulatory domain
[   10.450582] type=1400 audit(1311916714.199:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=460 comm="apparmor_parser"
[   10.452541] type=1400 audit(1311916714.203:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=586 comm="apparmor_parser"
[   10.454598] type=1400 audit(1311916714.203:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=586 comm="apparmor_parser"
[   10.456447] type=1400 audit(1311916714.207:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=460 comm="apparmor_parser"
[   10.457764] type=1400 audit(1311916714.207:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=460 comm="apparmor_parser"
[   10.459521] type=1400 audit(1311916714.207:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=586 comm="apparmor_parser"
[   10.810013] libipw: 802.11 data/management/control stack, git-1.1.13
[   10.810021] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   11.541839] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x370-0x377
[   11.543740] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3f7 0x4d0-0x4d7
[   11.544616] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   11.545331] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   11.546108] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xc7fff 0xf0000-0xfffff
[   11.546256] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   11.546400] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: clean.
[   11.546554] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   11.588194] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   11.588203] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   11.588387] ipw2200 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.588490] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   11.808081] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   11.808092] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   11.808099] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   11.808107] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   11.808114] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   11.808122] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   11.808129] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   11.808137] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   11.808144] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   11.808152] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   11.808158] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   11.808166] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   11.808173] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   11.808181] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   11.808188] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   11.808196] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   11.808203] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   11.808211] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   11.808217] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   11.808225] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   11.808232] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   11.808240] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   11.810349] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   12.301337] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   12.301349] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   12.301356] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   12.301364] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   12.301371] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   12.301379] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   12.301386] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   12.301393] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   12.301400] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   12.301408] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   12.301415] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   12.301423] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   12.301429] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   12.301437] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   12.301444] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   12.301452] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   12.301459] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   12.301467] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   12.301473] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   12.301481] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   12.301488] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   12.301496] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   12.301503] cfg80211: World regulatory domain updated:
[   12.301508] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   12.301516] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.301524] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.301532] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.301539] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.301547] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.530464] nvidia: module license 'NVIDIA' taints kernel.
[   12.530473] Disabling lock debugging due to kernel taint
[   15.876712] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.876730] nvidia 0000:01:00.0: setting latency timer to 64
[   15.876741] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   15.878530] NVRM: loading NVIDIA UNIX x86 Kernel Module  270.41.06  Mon Apr 18 14:54:25 PDT 2011
[   16.726086] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.726139] Intel ICH 0000:00:1e.2: setting latency timer to 64
[   17.556044] intel8x0_measure_ac97_clock: measured 55294 usecs (2664 samples)
[   17.556052] intel8x0: clocking to 48000
[   18.009111] type=1400 audit(1311916721.759:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=720 comm="apparmor_parser"
[   18.016693] type=1400 audit(1311916721.767:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=721 comm="apparmor_parser"
[   18.018782] type=1400 audit(1311916721.767:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=721 comm="apparmor_parser"
[   18.020356] type=1400 audit(1311916721.771:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=721 comm="apparmor_parser"
[   18.735215] type=1400 audit(1311916722.483:12): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=722 comm="apparmor_parser"
[   18.765674] type=1400 audit(1311916722.515:13): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=722 comm="apparmor_parser"
[   18.786670] type=1400 audit(1311916722.535:14): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=722 comm="apparmor_parser"
[   19.787016] type=1400 audit(1311916723.535:15): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=724 comm="apparmor_parser"
[   19.789694] type=1400 audit(1311916723.539:16): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=724 comm="apparmor_parser"
[   20.158151] type=1400 audit(1311916723.907:17): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=726 comm="apparmor_parser"
[   22.841686] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.110172] vboxdrv: Found 1 processor cores.
[   23.118977] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   23.118986] vboxdrv: Successfully loaded version 4.0.4_OSE (interface 0x00160000).
[   25.302713] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   33.840169] eth1: no IPv6 routers present
[  186.970929] vesafb: framebuffer at 0xc0000000, mapped to 0xf8500000, using 5120k, total 5120k
[  186.970939] vesafb: mode is 1280x1024x32, linelength=5120, pages=0
[  186.970944] vesafb: scrolling: redraw
[  186.970952] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[  186.971416] Console: switching to colour frame buffer device 160x64
[  186.971530] fb0: VESA VGA frame buffer device
[  187.046889] ppdev: user-space parallel port driver
[  187.122853] type=1400 audit(1311916890.868:18): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1093 comm="apparmor_parser"
[  187.130497] type=1400 audit(1311916890.876:19): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1093 comm="apparmor_parser"
[  199.472560] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[  231.322911] lib80211_crypt: registered algorithm 'WEP'


I'm not sure what's going on here, but it seems to have something to do with Eth1. I installed bootchart and I have a copy of that as well, but the .png file that it showed doesn't even come close to the 4 1/2 minute boot time... That long of a boot time is unacceptable for me. I was going to re-load 11.04, but unfortunately, my DVD burner isn't working the way that it should either... Sigh. I hope someone out there can give me a hand!

---

### Post by akoskm on 2011-07-29
The timesstamps are looking very weird at the and but anyway...
If your DVD burner is out of order you can always use the [USB Install]("https://help.ubuntu.com/community/Installation/FromUSBStick").

---

### Post by horsemanoffaith on 2011-07-29
Yes that's my next option if I can't get a fix soon. Thanks for the reply!

---

