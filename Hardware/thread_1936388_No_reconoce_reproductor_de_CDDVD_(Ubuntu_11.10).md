---
title: "No reconoce reproductor de CD/DVD (Ubuntu 11.10)"
date: 2012-03-06
forum: Hardware
---

### Post by nicoletoz on 2012-03-06
Hola! mi nombre es Nicolas, hace apenas un dia que decidi mudarme a ubuntu desde windows, por ahora la experiencia anduvo bien y fui solucionando los pormenores que fueron apareciendo leyendo foros y googleando, pero llegue a un problema que no puedo resolver.  No hay forma de que ubuntu reconozca cds o dvds. actualmente estoy usando gnome classic y cuando inserto un disco en el reproductor, la luz del mismo se prende unos instantes pero luego se apaga, y no ocurre ningun cambio ni aparece en ningun lado que el sistema haya reconocido nada. 
alguna idea de que puede estar pasando o que puedo hacer al respecto??

saludos!

---

### Post by guillermolisi on 2012-03-06
Bienvenido Nico.

Hay varias causas que pueden originar el problema que comentas.
Para tener una idea mas o menos cierta, lo mejor es ver el log del sistema en busca de mensajes que nos den un indicio.

Para eso, en una terminal/consola ingresa ```
dmesg
``` y vas a recibir una buena cantidad de informacion sobre la actividad del sistema. De todo lo que te muestre nos interesa lo referido a /dev/sr0 (suponiendo que tenes solo una unidad optica).

Si queres, pega aqui la salida de ese comando y lo vemos entre todos.

---

### Post by nicoletoz on 2012-03-06
gracias por la bienvenida! 
no encontre nada en el log respecto a sr0. osea que nisiquiera la ve? por las dudas, aclaro que en windows la lectora anda bien  (para ya saber, hay alguna forma de pegar esta clase de logs en un spoiler o algo asi para que no quede tan extenso dentro del thread?) 

 ahi va lo que me devuelve:


[    0.195737] pnp 00:0a: [io  0x0400-0x041f]
[    0.195740] pnp 00:0a: [io  0x0000-0xffffffff disabled]
[    0.195816] system 00:0a: [io  0x03e0-0x03e7] has been reserved
[    0.195820] system 00:0a: [io  0x04d0-0x04d1] has been reserved
[    0.195823] system 00:0a: [io  0x0800-0x087f] has been reserved
[    0.195827] system 00:0a: [io  0x0400-0x041f] has been reserved
[    0.195831] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.195893] pnp 00:0b: [mem 0xfec00000-0xfec00fff]
[    0.195896] pnp 00:0b: [mem 0xfee00000-0xfee00fff]
[    0.195957] system 00:0b: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.195960] system 00:0b: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.195965] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.196755] pnp 00:0c: [io  0x03f8-0x03ff]
[    0.196769] pnp 00:0c: [irq 4]
[    0.196772] pnp 00:0c: [dma 0 disabled]
[    0.196871] pnp 00:0c: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.197124] pnp 00:0d: [mem 0x00000000-0x0009ffff]
[    0.197128] pnp 00:0d: [mem 0x000c0000-0x000cffff]
[    0.197131] pnp 00:0d: [mem 0x000e0000-0x000fffff]
[    0.197134] pnp 00:0d: [mem 0x00100000-0x3fffffff]
[    0.197137] pnp 00:0d: [mem 0xff380000-0xffffffff]
[    0.197240] system 00:0d: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.197244] system 00:0d: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.197248] system 00:0d: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.197252] system 00:0d: [mem 0x00100000-0x3fffffff] could not be reserved
[    0.197256] system 00:0d: [mem 0xff380000-0xffffffff] has been reserved
[    0.197260] system 00:0d: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.197436] pnp: PnP ACPI: found 14 devices
[    0.197438] ACPI: ACPI bus type pnp unregistered
[    0.197444] PnPBIOS: Disabled by ACPI PNP
[    0.234210] Switching to clocksource acpi_pm
[    0.234319] PCI: max bus depth: 1 pci_try_num: 2
[    0.234356] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.234359] pci 0000:00:01.0:   bridge window [io  disabled]
[    0.234367] pci 0000:00:01.0:   bridge window [mem 0xfca00000-0xfeafffff]
[    0.234372] pci 0000:00:01.0:   bridge window [mem 0xe7f00000-0xf7efffff pref]
[    0.234396] pci 0000:00:01.0: setting latency timer to 64
[    0.234402] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.234406] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.234409] pci_bus 0000:01: resource 1 [mem 0xfca00000-0xfeafffff]
[    0.234412] pci_bus 0000:01: resource 2 [mem 0xe7f00000-0xf7efffff pref]
[    0.234485] NET: Registered protocol family 2
[    0.234607] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.234991] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.234991] Switched to NOHz mode on CPU #0
[    0.234225] Switched to NOHz mode on CPU #1
[    0.234991] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.235314] TCP: Hash tables configured (established 131072 bind 65536)
[    0.235318] TCP reno registered
[    0.235324] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.235355] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.235603] NET: Registered protocol family 1
[    0.235647] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
[    0.235755] pci 0000:00:11.0: Bypassing VIA 8237 APIC De-Assert Message
[    0.235778] pci 0000:01:00.0: Boot video device
[    0.235782] PCI: CLS 32 bytes, default 64
[    0.236342] audit: initializing netlink socket (disabled)
[    0.236360] type=2000 audit(1330916783.232:1): initialized
[    0.265484] highmem bounce pool size: 64 pages
[    0.265492] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.275714] VFS: Disk quotas dquot_6.5.2
[    0.275810] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.276782] fuse init (API version 7.16)
[    0.276909] msgmni has been set to 1704
[    0.277393] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.277443] io scheduler noop registered
[    0.277445] io scheduler deadline registered
[    0.277464] io scheduler cfq registered (default)
[    0.277660] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.277691] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.277786] intel_idle: MWAIT substates: 0x220
[    0.277789] intel_idle: does not run on family 6 model 15
[    0.277913] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0
[    0.277923] ACPI: Sleep Button [SLPB]
[    0.277979] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.277984] ACPI: Power Button [PWRB]
[    0.278039] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.278043] ACPI: Power Button [PWRF]
[    0.278079] ACPI: acpi_idle registered with cpuidle
[    0.283344] ERST: Table is not found!
[    0.283517] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.292237] isapnp: Scanning for PnP cards...
[    0.303927] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.530040] Freeing initrd memory: 13320k freed
[    0.646191] isapnp: No Plug & Play device found
[    0.677956] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.678270] Linux agpgart interface v0.103
[    0.678369] agpgart: Detected VIA VT3314 chipset
[    0.681554] agpgart-via 0000:00:00.0: AGP aperture is 64M @ 0xf8000000
[    0.683146] brd: module loaded
[    0.683910] loop: module loaded
[    0.684199] pata_acpi 0000:00:0f.0: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    0.684255] pata_acpi 0000:00:0f.0: PCI INT B disabled
[    0.684273] pata_acpi 0000:00:0f.1: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.684299] pata_acpi 0000:00:0f.1: PCI INT A disabled
[    0.684725] Fixed MDIO Bus: probed
[    0.684756] PPP generic driver version 2.4.2
[    0.684821] tun: Universal TUN/TAP device driver, 1.6
[    0.684823] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.684933] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.684960] ehci_hcd 0000:00:10.4: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    0.684979] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    0.685031] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 1
[    0.685100] ehci_hcd 0000:00:10.4: irq 21, io mem 0xfebffc00
[    0.696021] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00
[    0.696179] hub 1-0:1.0: USB hub found
[    0.696185] hub 1-0:1.0: 8 ports detected
[    0.696286] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.696304] uhci_hcd: USB Universal Host Controller Interface driver
[    0.696345] uhci_hcd 0000:00:10.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    0.696353] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    0.696408] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[    0.696433] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000dc00
[    0.696582] hub 2-0:1.0: USB hub found
[    0.696587] hub 2-0:1.0: 2 ports detected
[    0.696674] uhci_hcd 0000:00:10.1: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    0.696681] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    0.696726] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[    0.696749] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000d880
[    0.696894] hub 3-0:1.0: USB hub found
[    0.696899] hub 3-0:1.0: 2 ports detected
[    0.696972] uhci_hcd 0000:00:10.2: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.696979] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    0.697023] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[    0.697046] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000d800
[    0.697189] hub 4-0:1.0: USB hub found
[    0.697194] hub 4-0:1.0: 2 ports detected
[    0.697272] uhci_hcd 0000:00:10.3: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.697281] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    0.697326] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
[    0.697349] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000d480
[    0.697493] hub 5-0:1.0: USB hub found
[    0.697497] hub 5-0:1.0: 2 ports detected
[    0.697653] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.698157] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.698168] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.698336] mousedev: PS/2 mouse device common for all mice
[    0.698522] rtc_cmos 00:02: RTC can wake from S4
[    0.698683] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.698737] rtc0: alarms up to one year, y3k, 114 bytes nvram
[    0.698865] device-mapper: uevent: version 1.0.3
[    0.698967] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: [email]dm-devel@redhat.com[/email]
[    0.699010] EISA: Probing bus 0 at eisa.0
[    0.699052] EISA: Detected 0 cards.
[    0.699065] cpufreq-nforce2: No nForce2 chipset.
[    0.699069] cpuidle: using governor ladder
[    0.699071] cpuidle: using governor menu
[    0.699074] EFI Variables Facility v0.08 2004-May-17
[    0.699473] TCP cubic registered
[    0.699650] NET: Registered protocol family 10
[    0.700494] NET: Registered protocol family 17
[    0.700529] Registering the dns_resolver key type
[    0.700559] Using IPI No-Shortcut mode
[    0.700672] PM: Hibernation image not present or could not be loaded.
[    0.700689] registered taskstats version 1
[    0.712383]   Magic number: 4:734:107
[    0.712398] usbmon usbmon3: hash matches
[    0.712527] rtc_cmos 00:02: setting system clock to 2012-03-05 03:06:24 UTC (1330916784)
[    0.712556] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.712558] EDD information not available.
[    0.712696] Freeing unused kernel memory: 696k freed
[    0.712963] Write protecting the kernel text: 5340k
[    0.713024] Write protecting the kernel read-only data: 2192k
[    0.714739] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.737160] udevd[80]: starting version 173
[    0.840233] Floppy drive(s): fd0 is 1.44M
[    0.843326] sata_via 0000:00:0f.0: version 2.6
[    0.843356] sata_via 0000:00:0f.0: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    0.843409] sata_via 0000:00:0f.0: routed to hard irq line 11
[    0.853876] scsi0 : sata_via
[    0.857400] scsi1 : sata_via
[    0.859257] ata1: SATA max UDMA/133 cmd 0xec00 ctl 0xe880 bmdma 0xe400 irq 20
[    0.859264] ata2: SATA max UDMA/133 cmd 0xe800 ctl 0xe480 bmdma 0xe408 irq 20
[    0.861416] FDC 0 is a post-1991 82077
[    0.866781] pata_via 0000:00:0f.1: version 0.3.4
[    0.866813] pata_via 0000:00:0f.1: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.870929] scsi2 : pata_via
[    0.873032] via_rhine: v1.10-LK1.5.0 2010-10-09 Written by Donald Becker
[    0.874099] scsi3 : pata_via
[    0.875888] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[    0.875894] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[    0.881712] via-rhine 0000:00:12.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.886430] via-rhine 0000:00:12.0: eth0: VIA Rhine II at 0xfebff800, 00:16:ec:fa:e7:d0, IRQ 23
[    0.887142] via-rhine 0000:00:12.0: eth0: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000
[    1.008029] usb 1-2: new high speed USB device number 2 using ehci_hcd
[    1.060021] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.236022] Refined TSC clocksource calibration: 1800.000 MHz.
[    1.236029] Switching to clocksource tsc
[    1.242439] ata1.00: ATA-7: WDC WD1600AABS-00PRA0, 05.06H05, max UDMA/133
[    1.242443] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.248989] ata1.00: configured for UDMA/133
[    1.249141] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600AABS-0 05.0 PQ: 0 ANSI: 5
[    1.249410] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.249442] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.249520] sd 0:0:0:0: [sda] Write Protect is off
[    1.249524] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.249573] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.280300]  sda: sda1 sda2 < sda5 sda6 >
[    1.280756] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.452015] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    2.130020] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   14.836892] udevd[281]: starting version 173
[   14.889708] lp: driver loaded but no devices found
[   14.911400] Adding 1046524k swap on /dev/sda6.  Priority:-1 extents:1 across:1046524k 
[   14.976852] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.084181] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   15.108918] type=1400 audit(1330927598.892:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=452 comm="apparmor_parser"
[   15.109534] type=1400 audit(1330927598.892:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=452 comm="apparmor_parser"
[   15.109903] type=1400 audit(1330927598.892:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=452 comm="apparmor_parser"
[   15.223969] nvidia: module license 'NVIDIA' taints kernel.
[   15.223976] Disabling lock debugging due to kernel taint
[   15.254546] parport_pc 00:08: reported by Plug and Play ACPI
[   15.254651] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   15.500307] lp0: using parport0 (interrupt-driven).
[   15.507639] psmouse serio1: ID: 10 00 64
[   15.680867] ppdev: user-space parallel port driver
[   15.681362] cfg80211: Calling CRDA to update world regulatory domain
[   15.751663] cfg80211: World regulatory domain updated:
[   15.751667] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   15.751671] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.751675] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.751678] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.751681] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.751685] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.829273] VIA 82xx Audio 0000:00:11.5: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[   15.829594] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   15.854318] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.854332] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   15.855136] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.30  Thu Apr 14 08:47:14 PDT 2011
[   15.866046] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   15.866053] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.866056] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   15.866060] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.866063] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   15.866066] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.866069] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   15.866073] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.866075] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   15.866079] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.866082] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   15.866085] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.866088] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   15.866092] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.866095] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   15.866098] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.866101] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   15.866105] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.866108] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   15.866111] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.866114] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   15.866118] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.866121] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   15.866124] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.866127] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   15.866131] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.866134] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   15.866137] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.920193] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   15.921170] Registered led device: rt2800usb-phy0::radio
[   15.921201] Registered led device: rt2800usb-phy0::assoc
[   15.921226] Registered led device: rt2800usb-phy0::quality
[   15.923240] usbcore: registered new interface driver rt2800usb
[   16.026457] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input4
[   16.045732] init: failsafe main process (718) killed by TERM signal
[   16.119991] type=1400 audit(1330927599.900:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=783 comm="apparmor_parser"
[   16.123340] type=1400 audit(1330927599.904:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=783 comm="apparmor_parser"
[   16.123681] type=1400 audit(1330927599.904:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=783 comm="apparmor_parser"
[   16.141148] type=1400 audit(1330927599.924:8): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=789 comm="apparmor_parser"
[   16.152811] type=1400 audit(1330927599.936:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=789 comm="apparmor_parser"
[   16.157508] type=1400 audit(1330927599.940:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=782 comm="apparmor_parser"
[   16.160096] type=1400 audit(1330927599.944:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=789 comm="apparmor_parser"
[   16.320981] init: apport pre-start process (834) terminated with status 1
[   16.321845] init: alsa-restore main process (842) terminated with status 19
[   16.358335] init: apport post-stop process (862) terminated with status 1
[   16.503702] Bluetooth: Core ver 2.16
[   16.503745] NET: Registered protocol family 31
[   16.503747] Bluetooth: HCI device and connection manager initialized
[   16.503751] Bluetooth: HCI socket layer initialized
[   16.503754] Bluetooth: L2CAP socket layer initialized
[   16.503924] Bluetooth: SCO socket layer initialized
[   16.507301] Bluetooth: RFCOMM TTY layer initialized
[   16.507309] Bluetooth: RFCOMM socket layer initialized
[   16.507311] Bluetooth: RFCOMM ver 1.11
[   16.515024] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.515029] Bluetooth: BNEP filters: protocol multicast
[   16.572297] vesafb: mode is 1280x1024x32, linelength=5120, pages=0
[   16.572302] vesafb: scrolling: redraw
[   16.572306] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   16.573423] vesafb: framebuffer at 0xe8000000, mapped to 0xf9000000, using 5120k, total 5120k
[   16.573557] fbcon: VESA VGA (fb0) is primary device
[   16.573792] Console: switching to colour frame buffer device 160x64
[   16.573836] fb0: VESA VGA frame buffer device
[   16.893185] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.906496] via-rhine 0000:00:12.0: eth0: link down
[   16.906813] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.068658] agpgart-via 0000:00:00.0: AGP 3.5 bridge
[   17.068687] agpgart-via 0000:00:00.0: putting AGP V3 device into 8x mode
[   17.068838] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
[   18.289372] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   18.668461] init: plymouth-stop pre-start process (1137) terminated with status 1
[   20.297123] wlan0: authenticate with 00:02:cf:bd:a3:67 (try 1)
[   20.298536] wlan0: authenticated
[   20.316147] wlan0: associate with 00:02:cf:bd:a3:67 (try 1)
[   20.320410] wlan0: RX AssocResp from 00:02:cf:bd:a3:67 (capab=0x431 status=0 aid=3)
[   20.320417] wlan0: associated
[   20.328433] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   21.017316] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   31.064026] wlan0: no IPv6 routers present
[  299.988020] [Hardware Error]: Machine check events logged
[ 2322.732022] usb 2-1: new full speed USB device number 2 using uhci_hcd
[ 2326.357731] cdc_acm 2-1:2.3: ttyACM0: USB ACM device
[ 2326.360543] usbcore: registered new interface driver cdc_acm
[ 2326.360549] cdc_acm: USB Abstract Control Model driver for USB modems and ISDN adapters
[ 2326.381182] usbcore: registered new interface driver cdc_ether
[ 2326.387115] usb 2-1: bad CDC descriptors
[ 2326.387168] usbcore: registered new interface driver rndis_host
[ 2326.419980] usb 2-1: bad CDC descriptors
[ 2326.420067] usbcore: registered new interface driver rndis_wlan
[ 2326.479303] usbcore: registered new interface driver uas
[ 2326.496331] Initializing USB Mass Storage driver...
[ 2326.496567] scsi4 : usb-storage 2-1:2.5
[ 2326.496741] usbcore: registered new interface driver usb-storage
[ 2326.496744] USB Mass Storage support registered.
[ 2327.500066] scsi 4:0:0:0: Direct-Access     Agere    MMCSD Storage    2.01 PQ: 0 ANSI: 0
[ 2327.604378] sd 4:0:0:0: Attached scsi generic sg1 type 0
[ 2327.614049] sd 4:0:0:0: [sdb] 3842048 512-byte logical blocks: (1.96 GB/1.83 GiB)
[ 2327.621045] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2327.628044] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 2327.628049] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 2327.642042] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2327.649057] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 2327.649063] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 2327.659119]  sdb: sdb1
[ 2327.675082] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2327.682193] sd 4:0:0:0: [sdb] Asking for cache data failed
[ 2327.682205] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 2327.682217] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[ 2327.732046] agpgart-via 0000:00:00.0: AGP 3.5 bridge
[ 2327.732070] agpgart-via 0000:00:00.0: putting AGP V3 device into 8x mode
[ 2327.732160] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
[ 2776.531489] agpgart-via 0000:00:00.0: AGP 3.5 bridge
[ 2776.531513] agpgart-via 0000:00:00.0: putting AGP V3 device into 8x mode
[ 2776.531603] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
[34338.744060] usb 2-1: USB disconnect, device number 2
[40254.531240] agpgart-via 0000:00:00.0: AGP 3.5 bridge
[40254.531264] agpgart-via 0000:00:00.0: putting AGP V3 device into 8x mode
[40254.531352] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
[40309.869734] agpgart-via 0000:00:00.0: AGP 3.5 bridge
[40309.869757] agpgart-via 0000:00:00.0: putting AGP V3 device into 8x mode
[40309.869845] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
[41672.833911] agpgart-via 0000:00:00.0: AGP 3.5 bridge
[41672.833934] agpgart-via 0000:00:00.0: putting AGP V3 device into 8x mode
[41672.834022] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
[43369.257942] agpgart-via 0000:00:00.0: AGP 3.5 bridge
[43369.257968] agpgart-via 0000:00:00.0: putting AGP V3 device into 8x mode
[43369.258057] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
[45838.414785] agpgart-via 0000:00:00.0: AGP 3.5 bridge
[45838.414809] agpgart-via 0000:00:00.0: putting AGP V3 device into 8x mode
[45838.414898] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
[45873.435626] show_signal_msg: 21 callbacks suppressed
[45873.435632] gnome-shell[12506]: segfault at 10 ip 01280217 sp bfb7cf3c error 6 in libcogl.so.5.0.0[122e000+74000]
[45882.988894] agpgart-via 0000:00:00.0: AGP 3.5 bridge
[45882.988918] agpgart-via 0000:00:00.0: putting AGP V3 device into 8x mode
[45882.989007] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
[45911.475133] gnome-shell[12794]: segfault at 10 ip 03216217 sp bfee8e1c error 6 in libcogl.so.5.0.0[31c4000+74000]
[45920.448537] gnome-shell[12875]: segfault at 10 ip 00dab217 sp bf941eec error 6 in libcogl.so.5.0.0[d59000+74000]
[46118.404782] agpgart-via 0000:00:00.0: AGP 3.5 bridge
[46118.404806] agpgart-via 0000:00:00.0: putting AGP V3 device into 8x mode
[46118.404894] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
[57454.550871] agpgart-via 0000:00:00.0: AGP 3.5 bridge
[57454.550894] agpgart-via 0000:00:00.0: putting AGP V3 device into 8x mode
[57454.550983] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
[57487.651922] gnome-shell[15025]: segfault at 10 ip 036c6217 sp bfebfd9c error 6 in libcogl.so.5.0.0[3674000+74000]
[57760.679472] agpgart-via 0000:00:00.0: AGP 3.5 bridge
[57760.679496] agpgart-via 0000:00:00.0: putting AGP V3 device into 8x mode
[57760.679584] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
[58504.108043] end_request: I/O error, dev fd0, sector 0
[58521.076079] end_request: I/O error, dev fd0, sector 0
[80073.204059] end_request: I/O error, dev fd0, sector 0
[80323.744039] end_request: I/O error, dev fd0, sector 0
[80902.512038] usb 2-1: new full speed USB device number 3 using uhci_hcd
[80902.727180] usb 2-1: bad CDC descriptors
[80902.727261] usb 2-1: bad CDC descriptors
[80902.730173] cdc_acm 2-1:2.3: ttyACM0: USB ACM device
[80902.736278] scsi5 : usb-storage 2-1:2.5
[80903.740159] scsi 5:0:0:0: Direct-Access     Agere    MMCSD Storage    2.01 PQ: 0 ANSI: 0
[80903.800752] sd 5:0:0:0: Attached scsi generic sg1 type 0
[80903.810131] sd 5:0:0:0: [sdb] 3842048 512-byte logical blocks: (1.96 GB/1.83 GiB)
[80903.817139] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[80903.824132] sd 5:0:0:0: [sdb] Asking for cache data failed
[80903.824138] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[80903.838120] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[80903.845124] sd 5:0:0:0: [sdb] Asking for cache data failed
[80903.845128] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[80903.855230]  sdb: sdb1
[80903.871121] sd 5:0:0:0: [sdb] Test WP failed, assume Write Enabled
[80903.878150] sd 5:0:0:0: [sdb] Asking for cache data failed
[80903.878156] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[80903.878161] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[80942.904044] usb 2-1: USB disconnect, device number 3
[80945.168025] usb 2-1: new full speed USB device number 4 using uhci_hcd
[80945.382294] usb 2-1: bad CDC descriptors
[80945.382372] usb 2-1: bad CDC descriptors
[80945.386305] cdc_acm 2-1:2.3: ttyACM0: USB ACM device
[80945.392375] scsi6 : usb-storage 2-1:2.5
[80946.396399] scsi 6:0:0:0: Direct-Access     Agere    MMCSD Storage    2.01 PQ: 0 ANSI: 0
[80946.434092] sd 6:0:0:0: Attached scsi generic sg1 type 0
[80946.446272] sd 6:0:0:0: [sdb] 3842048 512-byte logical blocks: (1.96 GB/1.83 GiB)
[80946.453289] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[80946.460274] sd 6:0:0:0: [sdb] Asking for cache data failed
[80946.460278] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[80946.474285] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[80946.481268] sd 6:0:0:0: [sdb] Asking for cache data failed
[80946.481273] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[80946.491361]  sdb: sdb1
[80946.510315] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[80946.519336] sd 6:0:0:0: [sdb] Asking for cache data failed
[80946.519345] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[80946.519350] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[83689.038205] agpgart-via 0000:00:00.0: AGP 3.5 bridge
[83689.038230] agpgart-via 0000:00:00.0: putting AGP V3 device into 8x mode
[83689.038317] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
[83755.225570] agpgart-via 0000:00:00.0: AGP 3.5 bridge
[83755.225594] agpgart-via 0000:00:00.0: putting AGP V3 device into 8x mode
[83755.225682] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
[85733.469912] agpgart-via 0000:00:00.0: AGP 3.5 bridge
[85733.469936] agpgart-via 0000:00:00.0: putting AGP V3 device into 8x mode
[85733.470023] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
[108789.540039] usb 2-1: USB disconnect, device number 4
[108789.740048] hub 2-0:1.0: unable to enumerate USB device on port 1
[108789.984106] hub 1-0:1.0: unable to enumerate USB device on port 1
[108790.308038] hub 2-0:1.0: unable to enumerate USB device on port 1

---

### Post by guillermolisi on 2012-03-07
Podrias mostrar la salida del comando en consola/terminal ```
sudo lshw
``` por favor ? En el log que pasaste no menciona la unidad optica, si el resto, asi que algun problem de reconocimiento de hardware me parece que podria ser la razon.

Me paso con unas unidades Lite-On IDE y opte por el camino mas rapido: Las cambie por unidades SATA y se acabo el problema.

---

### Post by nicoletoz on 2012-03-14
perdon el cuelgue, aparentemente tuve algun problema mas grave por el cual directamente linux dejo de arrancar cuando lo selecciono desde el GRUB.  despues de hablar con un amigo, me recomendo pasarme a xubuntu. actualmente estoy en eso, pero estoy teniendo problemas en la instalacion... voy a hacer otro  thread al respecto. de todas formas, gracias por la colaboracion!

---

