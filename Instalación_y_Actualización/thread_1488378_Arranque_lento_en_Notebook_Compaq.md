---
title: "Arranque lento en Notebook Compaq"
date: 2010-05-20
forum: Instalación y Actualización
---

### Post by renzo.martinez.friz on 2010-05-20
Buenas.

Al intalar la ultima version de Ubuntu 10.04, mi notebook Compaq demora 52 segundos en iniciar desde que lo enciendo hasta que aparece la pantalla de los usuarios.

De acuerdo a lo indicado por Carlos C, utilizando el comando "dmesg", la información que aparece es la siguiente:
> 
[    0.620917] pci 0000:00:1c.5:   PREFETCH window: 0x00000095400000-0x000000963fffff
[    0.620925] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:09
[    0.620927] pci 0000:00:1e.0:   IO window: disabled
[    0.620932] pci 0000:00:1e.0:   MEM window: disabled
[    0.620937] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.620955]   alloc irq_desc for 16 on node -1
[    0.620957]   alloc kstat_irqs on node -1
[    0.620962] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.620968] pci 0000:00:1c.0: setting latency timer to 64
[    0.620977]   alloc irq_desc for 17 on node -1
[    0.620979]   alloc kstat_irqs on node -1
[    0.620985] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.620990] pci 0000:00:1c.1: setting latency timer to 64
[    0.620999]   alloc irq_desc for 18 on node -1
[    0.621001]   alloc kstat_irqs on node -1
[    0.621004] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.621009] pci 0000:00:1c.2: setting latency timer to 64
[    0.621018]   alloc irq_desc for 19 on node -1
[    0.621019]   alloc kstat_irqs on node -1
[    0.621023] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.621028] pci 0000:00:1c.3: setting latency timer to 64
[    0.621037] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.621042] pci 0000:00:1c.4: setting latency timer to 64
[    0.621052] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.621056] pci 0000:00:1c.5: setting latency timer to 64
[    0.621064] pci 0000:00:1e.0: setting latency timer to 64
[    0.621069] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.621072] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.621074] pci_bus 0000:01: resource 0 io:  [0x6000-0x6fff]
[    0.621076] pci_bus 0000:01: resource 1 mem: [0x9b500000-0x9c4fffff]
[    0.621079] pci_bus 0000:01: resource 2 pref mem [0x90400000-0x913fffff]
[    0.621081] pci_bus 0000:02: resource 0 io:  [0x5000-0x5fff]
[    0.621083] pci_bus 0000:02: resource 1 mem: [0x9a500000-0x9b4fffff]
[    0.621086] pci_bus 0000:02: resource 2 pref mem [0x91400000-0x923fffff]
[    0.621088] pci_bus 0000:03: resource 0 io:  [0x4000-0x4fff]
[    0.621090] pci_bus 0000:03: resource 1 mem: [0x99500000-0x9a4fffff]
[    0.621093] pci_bus 0000:03: resource 2 pref mem [0x92400000-0x933fffff]
[    0.621095] pci_bus 0000:04: resource 0 io:  [0x3000-0x3fff]
[    0.621097] pci_bus 0000:04: resource 1 mem: [0x98500000-0x994fffff]
[    0.621100] pci_bus 0000:04: resource 2 pref mem [0x93400000-0x943fffff]
[    0.621102] pci_bus 0000:05: resource 0 io:  [0x2000-0x2fff]
[    0.621104] pci_bus 0000:05: resource 1 mem: [0x97500000-0x984fffff]
[    0.621106] pci_bus 0000:05: resource 2 pref mem [0x94400000-0x953fffff]
[    0.621109] pci_bus 0000:06: resource 0 io:  [0x1000-0x1fff]
[    0.621111] pci_bus 0000:06: resource 1 mem: [0x96500000-0x974fffff]
[    0.621113] pci_bus 0000:06: resource 2 pref mem [0x95400000-0x963fffff]
[    0.621116] pci_bus 0000:09: resource 3 io:  [0x00-0xffff]
[    0.621118] pci_bus 0000:09: resource 4 mem: [0x000000-0xffffffff]
[    0.621149] NET: Registered protocol family 2
[    0.621232] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.621501] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.622005] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.622335] TCP: Hash tables configured (established 131072 bind 65536)
[    0.622338] TCP reno registered
[    0.622471] NET: Registered protocol family 1
[    0.622494] pci 0000:00:02.0: Boot video device
[    2.220008] pci 0000:00:1a.7: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[    3.820006] pci 0000:00:1d.7: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[    3.820198] Simple Boot Flag value 0x5 read from CMOS RAM was invalid
[    3.820200] Simple Boot Flag at 0x44 set to 0x1
[    3.820315] cpufreq-nforce2: No nForce2 chipset.
[    3.820338] Scanning for low memory corruption every 60 seconds
[    3.820435] audit: initializing netlink socket (disabled)
[    3.820446] type=2000 audit(1274326151.820:1): initialized
[    3.829615] Trying to unpack rootfs image as initramfs...
[    3.840469] highmem bounce pool size: 64 pages
[    3.840475] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    3.848040] VFS: Disk quotas dquot_6.5.2
[    3.848117] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    3.848626] fuse init (API version 7.13)
[    3.848698] msgmni has been set to 1690
[    3.848874] alg: No test for stdrng (krng)
[    3.848922] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    3.848925] io scheduler noop registered
[    3.848927] io scheduler anticipatory registered
[    3.848928] io scheduler deadline registered
[    3.848962] io scheduler cfq registered (default)
[    3.849120]   alloc irq_desc for 24 on node -1
[    3.849123]   alloc kstat_irqs on node -1
[    3.849135] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
[    3.849146] pcieport 0000:00:1c.0: setting latency timer to 64
[    3.849296]   alloc irq_desc for 25 on node -1
[    3.849298]   alloc kstat_irqs on node -1
[    3.849306] pcieport 0000:00:1c.1: irq 25 for MSI/MSI-X
[    3.849317] pcieport 0000:00:1c.1: setting latency timer to 64
[    3.849459]   alloc irq_desc for 26 on node -1
[    3.849460]   alloc kstat_irqs on node -1
[    3.849469] pcieport 0000:00:1c.2: irq 26 for MSI/MSI-X
[    3.849479] pcieport 0000:00:1c.2: setting latency timer to 64
[    3.849626]   alloc irq_desc for 27 on node -1
[    3.849628]   alloc kstat_irqs on node -1
[    3.849636] pcieport 0000:00:1c.3: irq 27 for MSI/MSI-X
[    3.849647] pcieport 0000:00:1c.3: setting latency timer to 64
[    3.849799]   alloc irq_desc for 28 on node -1
[    3.849801]   alloc kstat_irqs on node -1
[    3.849809] pcieport 0000:00:1c.4: irq 28 for MSI/MSI-X
[    3.849820] pcieport 0000:00:1c.4: setting latency timer to 64
[    3.849968]   alloc irq_desc for 29 on node -1
[    3.849970]   alloc kstat_irqs on node -1
[    3.849978] pcieport 0000:00:1c.5: irq 29 for MSI/MSI-X
[    3.849988] pcieport 0000:00:1c.5: setting latency timer to 64
[    3.850082] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    3.850299] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    3.976402] ACPI: AC Adapter [AC] (on-line)
[    3.976487] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    3.976491] ACPI: Power Button [PWRB]
[    3.976526] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    3.976596] ACPI: Lid Switch [LID0]
[    3.976635] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    3.976643] ACPI: Sleep Button [SLPB]
[    3.976690] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    3.976693] ACPI: Power Button [PWRF]
[    3.991484] fan PNP0C0B:00: registered as cooling_device0
[    3.991495] ACPI: Fan [FAN] (on)
[    3.996236] Monitor-Mwait will be used to enter C-1 state
[    3.996280] Monitor-Mwait will be used to enter C-2 state
[    3.996300] Monitor-Mwait will be used to enter C-3 state
[    3.996306] Marking TSC unstable due to TSC halts in idle
[    3.996356] processor LNXCPU:00: registered as cooling_device1
[    4.000279] Switching to clocksource hpet
[    4.017193] Freeing initrd memory: 7784k freed
[    4.123248] thermal LNXTHERM:01: registered as thermal_zone0
[    4.123256] ACPI: Thermal Zone [THRM] (24 C)
[    4.124649] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    4.125916] brd: module loaded
[    4.126294] loop: module loaded
[    4.126368] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    4.126712] Fixed MDIO Bus: probed
[    4.126741] PPP generic driver version 2.4.2
[    4.126773] tun: Universal TUN/TAP device driver, 1.6
[    4.126775] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    4.127028] isapnp: Scanning for PnP cards...
[    4.132552] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.132577] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.132591] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    4.132595] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    4.132622] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    4.132653] ehci_hcd 0000:00:1a.7: debug port 1
[    4.136535] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    4.180179] ehci_hcd 0000:00:1a.7: irq 18, io mem 0x9c504c00
[    4.227607] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    4.227678] usb usb1: configuration #1 chosen from 1 choice
[    4.227704] hub 1-0:1.0: USB hub found
[    4.227711] hub 1-0:1.0: 4 ports detected
[    4.227759]   alloc irq_desc for 20 on node -1
[    4.227761]   alloc kstat_irqs on node -1
[    4.227766] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    4.227778] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    4.227781] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.227812] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    4.227838] ehci_hcd 0000:00:1d.7: debug port 1
[    4.231716] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    4.231732] ehci_hcd 0000:00:1d.7: irq 20, io mem 0x9c504800
[    4.279261] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    4.279336] usb usb2: configuration #1 chosen from 1 choice
[    4.279358] hub 2-0:1.0: USB hub found
[    4.279364] hub 2-0:1.0: 8 ports detected
[    4.279419] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.279431] uhci_hcd: USB Universal Host Controller Interface driver
[    4.279455] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.279462] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    4.279466] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    4.279491] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    4.279528] uhci_hcd 0000:00:1a.0: irq 16, io base 0x000070e0
[    4.279603] usb usb3: configuration #1 chosen from 1 choice
[    4.279628] hub 3-0:1.0: USB hub found
[    4.279635] hub 3-0:1.0: 2 ports detected
[    4.279674] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    4.279680] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    4.279684] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    4.279708] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    4.279743] uhci_hcd 0000:00:1a.1: irq 17, io base 0x000070c0
[    4.279823] usb usb4: configuration #1 chosen from 1 choice
[    4.279844] hub 4-0:1.0: USB hub found
[    4.279850] hub 4-0:1.0: 2 ports detected
[    4.279888] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    4.279896] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    4.279899] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    4.279925] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    4.279953] uhci_hcd 0000:00:1d.0: irq 20, io base 0x000070a0
[    4.280048] usb usb5: configuration #1 chosen from 1 choice
[    4.280069] hub 5-0:1.0: USB hub found
[    4.280076] hub 5-0:1.0: 2 ports detected
[    4.280114]   alloc irq_desc for 22 on node -1
[    4.280116]   alloc kstat_irqs on node -1
[    4.280120] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    4.280127] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    4.280130] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    4.280156] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    4.280191] uhci_hcd 0000:00:1d.1: irq 22, io base 0x00007080
[    4.280404] usb usb6: configuration #1 chosen from 1 choice
[    4.280424] hub 6-0:1.0: USB hub found
[    4.280430] hub 6-0:1.0: 2 ports detected
[    4.280470] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.280476] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    4.280479] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    4.280503] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    4.280531] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00007060
[    4.280603] usb usb7: configuration #1 chosen from 1 choice
[    4.280624] hub 7-0:1.0: USB hub found
[    4.280629] hub 7-0:1.0: 2 ports detected
[    4.280668] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    4.280674] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    4.280677] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    4.280783] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 8
[    4.280895] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00007040
[    4.280970] usb usb8: configuration #1 chosen from 1 choice
[    4.280990] hub 8-0:1.0: USB hub found
[    4.280996] hub 8-0:1.0: 2 ports detected
[    4.281078] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUE] at 0x60,0x64 irq 1,12
[    4.321350] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.321359] serio: i8042 AUX port at 0x60,0x64 irq 12
[    4.321457] mice: PS/2 mouse device common for all mice
[    4.324387] rtc_cmos 00:03: RTC can wake from S4
[    4.324421] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    4.324453] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    4.324587] device-mapper: uevent: version 1.0.3
[    4.324807] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    4.368533] device-mapper: multipath: version 1.1.0 loaded
[    4.368535] device-mapper: multipath round-robin: version 1.0.0 loaded
[    4.368634] EISA: Probing bus 0 at eisa.0
[    4.368640] Cannot allocate resource for EISA slot 1
[    4.368642] Cannot allocate resource for EISA slot 2
[    4.368643] Cannot allocate resource for EISA slot 3
[    4.368645] Cannot allocate resource for EISA slot 4
[    4.368647] Cannot allocate resource for EISA slot 5
[    4.368648] Cannot allocate resource for EISA slot 6
[    4.368650] Cannot allocate resource for EISA slot 7
[    4.368657] EISA: Detected 0 cards.
[    4.368729] cpuidle: using governor ladder
[    4.368777] cpuidle: using governor menu
[    4.369112] TCP cubic registered
[    4.369242] NET: Registered protocol family 10
[    4.369599] lo: Disabled Privacy Extensions
[    4.369831] NET: Registered protocol family 17
[    4.369878] Using IPI No-Shortcut mode
[    4.369943] PM: Resume from disk failed.
[    4.369952] registered taskstats version 1
[    4.370834]   Magic number: 10:736:462
[    4.370870] pci 0000:05:00.0: hash matches
[    4.370923] rtc_cmos 00:03: setting system clock to 2010-05-20 03:29:13 UTC (1274326153)
[    4.370926] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.370927] EDD information not available.
[    4.545330] isapnp: No Plug & Play device found
[    4.545365] Freeing unused kernel memory: 656k freed
[    4.545652] Write protecting the kernel text: 4676k
[    4.545674] Write protecting the kernel read-only data: 1840k
[    4.548178] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    4.571843] udev: starting version 151
[    4.656045] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    4.774053] ACPI: Battery Slot [BAT0] (battery present)
[    4.789366] usb 2-1: configuration #1 chosen from 1 choice
[    4.789698] hub 2-1:1.0: USB hub found
[    4.790038] hub 2-1:1.0: 4 ports detected
[    4.800068] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    4.800108] r8169 0000:04:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    4.800225] r8169 0000:04:00.0: setting latency timer to 64
[    4.800371]   alloc irq_desc for 30 on node -1
[    4.800373]   alloc kstat_irqs on node -1
[    4.800418] r8169 0000:04:00.0: irq 30 for MSI/MSI-X
[    4.800917] eth0: RTL8102e at 0xf8098000, 00:23:5a:1e:92:e9, XID 04a00000 IRQ 30
[    4.805962] ahci 0000:00:1f.2: version 3.0
[    4.805982]   alloc irq_desc for 21 on node -1
[    4.805984]   alloc kstat_irqs on node -1
[    4.805991] ahci 0000:00:1f.2: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    4.806035]   alloc irq_desc for 31 on node -1
[    4.806037]   alloc kstat_irqs on node -1
[    4.806046] ahci 0000:00:1f.2: irq 31 for MSI/MSI-X
[    4.806106] ahci: SSS flag set, parallel bus scan disabled
[    4.806146] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    4.806149] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck stag pm led clo pmp pio slum part ccc ems 
[    4.806155] ahci 0000:00:1f.2: setting latency timer to 64
[    4.828091] scsi0 : ahci
[    4.828283] scsi1 : ahci
[    4.828374] scsi2 : ahci
[    4.828468] scsi3 : ahci
[    4.828556] scsi4 : ahci
[    4.828644] scsi5 : ahci
[    4.828916] ata1: SATA max UDMA/133 abar m2048@0x9c504000 port 0x9c504100 irq 31
[    4.828920] ata2: SATA max UDMA/133 abar m2048@0x9c504000 port 0x9c504180 irq 31
[    4.828922] ata3: DUMMY
[    4.828923] ata4: DUMMY
[    4.828926] ata5: SATA max UDMA/133 abar m2048@0x9c504000 port 0x9c504300 irq 31
[    4.828929] ata6: SATA max UDMA/133 abar m2048@0x9c504000 port 0x9c504380 irq 31
[    4.956039] usb 2-5: new high speed USB device using ehci_hcd and address 4
[    5.180635] usb 2-5: configuration #1 chosen from 1 choice
[    5.312046] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.315042] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    5.315248] ata1.00: ACPI cmd ef/10:01:00:00:00:a0 (SET FEATURES) rejected by device (Stat=0x51 Err=0x04)
[    5.315349] ata1.00: ACPI cmd ef/10:02:00:00:00:a0 (SET FEATURES) succeeded
[    5.315352] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    5.315560] ata1.00: ACPI cmd ef/10:04:00:00:00:a0 (SET FEATURES) rejected by device (Stat=0x51 Err=0x04)
[    5.315769] ata1.00: ACPI cmd ef/10:05:00:00:00:a0 (SET FEATURES) rejected by device (Stat=0x51 Err=0x04)
[    5.318326] ata1.00: ATA-8: SAMSUNG HM160HI, HH100-12, max UDMA/100
[    5.318328] ata1.00: 312581808 sectors, multi 0: LBA48 
[    5.321477] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    5.321683] ata1.00: ACPI cmd ef/10:01:00:00:00:a0 (SET FEATURES) rejected by device (Stat=0x51 Err=0x04)
[    5.321779] ata1.00: ACPI cmd ef/10:02:00:00:00:a0 (SET FEATURES) succeeded
[    5.321782] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    5.321989] ata1.00: ACPI cmd ef/10:04:00:00:00:a0 (SET FEATURES) rejected by device (Stat=0x51 Err=0x04)
[    5.322198] ata1.00: ACPI cmd ef/10:05:00:00:00:a0 (SET FEATURES) rejected by device (Stat=0x51 Err=0x04)
[    5.324775] ata1.00: configured for UDMA/100
[    5.340144] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HM160HI  HH10 PQ: 0 ANSI: 5
[    5.340287] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.340509] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    5.340548] sd 0:0:0:0: [sda] Write Protect is off
[    5.340551] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.340571] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.340692]  sda: sda1 sda2 < sda5 >
[    5.388136] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.424036] usb 6-1: new low speed USB device using uhci_hcd and address 2
[    5.597310] usb 6-1: configuration #1 chosen from 1 choice
[    5.660047] ata2: SATA link down (SStatus 0 SControl 300)
[    6.564040] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    6.577385] ata5.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    6.577733] ata5.00: ACPI cmd ef/10:01:00:00:00:a0 (SET FEATURES) rejected by device (Stat=0x51 Err=0x04)
[    6.578082] ata5.00: ACPI cmd ef/10:02:00:00:00:a0 (SET FEATURES) rejected by device (Stat=0x51 Err=0x04)
[    6.578085] ata5.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    6.578420] ata5.00: ACPI cmd ef/10:04:00:00:00:a0 (SET FEATURES) rejected by device (Stat=0x51 Err=0x04)
[    6.578765] ata5.00: ACPI cmd ef/10:05:00:00:00:a0 (SET FEATURES) rejected by device (Stat=0x51 Err=0x04)
[    6.578770] ata5.00: ATAPI: Optiarc DVD RW AD-7561S, AH03, max UDMA/100
[    6.592961] ata5.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    6.593314] ata5.00: ACPI cmd ef/10:01:00:00:00:a0 (SET FEATURES) rejected by device (Stat=0x51 Err=0x04)
[    6.593666] ata5.00: ACPI cmd ef/10:02:00:00:00:a0 (SET FEATURES) rejected by device (Stat=0x51 Err=0x04)
[    6.593669] ata5.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    6.594015] ata5.00: ACPI cmd ef/10:04:00:00:00:a0 (SET FEATURES) rejected by device (Stat=0x51 Err=0x04)
[    6.594365] ata5.00: ACPI cmd ef/10:05:00:00:00:a0 (SET FEATURES) rejected by device (Stat=0x51 Err=0x04)
[    6.594389] ata5.00: configured for UDMA/100
[    6.609076] scsi 4:0:0:0: CD-ROM            Optiarc  DVD RW AD-7561S  AH03 PQ: 0 ANSI: 5
[    6.614379] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    6.614382] Uniform CD-ROM driver Revision: 3.20
[    6.614480] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    6.614535] sr 4:0:0:0: Attached scsi generic sg1 type 5
[    6.932044] ata6: SATA link down (SStatus 0 SControl 300)
[    6.955820] usbcore: registered new interface driver hiddev
[    6.969472] input: USB KB USB KB as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0/input/input6
[    6.969544] generic-usb 0003:1241:1503.0001: input,hidraw0: USB HID v1.10 Keyboard [USB KB USB KB] on usb-0000:00:1d.1-1/input0
[    6.969566] usbcore: registered new interface driver usbhid
[    6.969568] usbhid: v2.6:USB HID core driver
[    7.190640] kjournald starting.  Commit interval 5 seconds
[    7.190650] EXT3-fs: mounted filesystem with ordered data mode.
[   35.067265] udev: starting version 151
[   35.145858] lp: driver loaded but no devices found
[   35.175330] Adding 5927944k swap on /dev/sda5.  Priority:-1 extents:1 across:5927944k 
[   35.182299] lirc_dev: IR Remote Control driver registered, major 61 
[   35.194233] lirc_dev: lirc_register_driver: sample_rate: 0
[   35.222211] enecir: KB3926C detected, driver support is not complete!
[   35.222215] enecir: chip is 0x3926 - 0x00, 0xc0
[   35.222224] enecir: hardware features:
[   35.222225] enecir: learning and tx off, gpio40_learn off, fan_in off
[   35.222227] enecir: driver has been succesfully loaded
[   35.501091] lib80211: common routines for IEEE802.11 drivers
[   35.501095] lib80211_crypt: registered algorithm 'NULL'
[   35.502307] Linux agpgart interface v0.103
[   35.512881] sdhci: Secure Digital Host Controller Interface driver
[   35.512885] sdhci: Copyright(c) Pierre Ossman
[   35.512936] agpgart-intel 0000:00:00.0: Intel Mobile Intel® GM45 Express Chipset
[   35.513182] agpgart-intel 0000:00:00.0: detected 32764K stolen memory
[   35.648279] EXT3 FS on sda1, internal journal
[   35.668452] Linux video capture interface: v2.00
[   35.672736] [drm] Initialized drm 1.1.0 20060810
[   35.680697] wl: module license 'MIXED/Proprietary' taints kernel.
[   35.680700] Disabling lock debugging due to kernel taint
[   35.699139] sdhci-pci 0000:05:00.0: SDHCI controller found [197b:2382] (rev 0)
[   35.699165] sdhci-pci 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   35.699208] sdhci-pci 0000:05:00.0: setting latency timer to 64
[   35.699244] Registered led device: mmc0::
[   35.699276] mmc0: SDHCI controller on PCI [0000:05:00.0] using ADMA
[   35.699288] sdhci-pci 0000:05:00.2: SDHCI controller found [197b:2381] (rev 0)
[   35.699307] sdhci-pci 0000:05:00.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   35.699312] sdhci-pci 0000:05:00.2: Refusing to bind to secondary interface.
[   35.699320] sdhci-pci 0000:05:00.2: PCI INT A disabled
[   35.701396] jmb38x_ms 0000:05:00.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   35.701405] jmb38x_ms 0000:05:00.3: setting latency timer to 64
[   35.710502] wl 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   35.710516] wl 0000:03:00.0: setting latency timer to 64
[   35.750530] uvcvideo: Found UVC 1.00 device Webcam-101 (064e:c108)
[   35.755121] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x80000000
[   35.763791] input: Webcam-101 as /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/input/input7
[   35.763848] usbcore: registered new interface driver uvcvideo
[   35.763851] USB Video Class driver (v0.1.0)
[   35.811994] type=1505 audit(1274326184.937:2):  operation="profile_load" pid=645 name="/sbin/dhclient3"
[   35.812678] type=1505 audit(1274326184.941:3):  operation="profile_load" pid=645 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   35.813017] type=1505 audit(1274326184.941:4):  operation="profile_load" pid=645 name="/usr/lib/connman/scripts/dhclient-script"
[   35.820575] type=1505 audit(1274326184.949:5):  operation="profile_load" pid=658 name="/usr/sbin/ntpd"
[   35.849344] lib80211_crypt: registered algorithm 'TKIP'
[   35.849495] eth1: Broadcom BCM4315 802.11 Hybrid Wireless Controller 5.60.48.36 
[   35.918268] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   35.918274] i915 0000:00:02.0: setting latency timer to 64
[   35.932821]   alloc irq_desc for 32 on node -1
[   35.932825]   alloc kstat_irqs on node -1
[   35.932834] i915 0000:00:02.0: irq 32 for MSI/MSI-X
[   35.932840] [drm] set up 31M of stolen space
[   36.659492] type=1505 audit(1274326185.785:6):  operation="profile_load" pid=784 name="/usr/share/gdm/guest-session/Xsession"
[   36.661145] type=1505 audit(1274326185.789:7):  operation="profile_replace" pid=785 name="/sbin/dhclient3"
[   36.661790] type=1505 audit(1274326185.789:8):  operation="profile_replace" pid=785 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   36.662135] type=1505 audit(1274326185.789:9):  operation="profile_replace" pid=785 name="/usr/lib/connman/scripts/dhclient-script"
[   36.665614] type=1505 audit(1274326185.793:10):  operation="profile_load" pid=786 name="/usr/bin/evince"
[   36.676729] type=1505 audit(1274326185.805:11):  operation="profile_load" pid=786 name="/usr/bin/evince-previewer"
[   36.716854] fb0: inteldrmfb frame buffer device
[   36.716857] registered panic notifier
[   36.717942] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[   36.727616] acpi device:02: registered as cooling_device2
[   36.728866] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input8
[   36.729005] ACPI: Video Device [OVGA] (multi-head: yes  rom: no  post: no)
[   36.729646] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   36.735986] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   36.736024] HDA Intel 0000:00:1b.0: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[   36.736028] hda_intel: msi for device 103c:3607 set to 1
[   36.736090]   alloc irq_desc for 33 on node -1
[   36.736092]   alloc kstat_irqs on node -1
[   36.736104] HDA Intel 0000:00:1b.0: irq 33 for MSI/MSI-X
[   36.736139] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   36.760528] vga16fb: initializing
[   36.760532] vga16fb: mapped to 0xc00a0000
[   36.760536] vga16fb: not registering due to another framebuffer present
[   37.092606] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input9
[   37.121403] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input10
[   37.144205] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input11
[   37.150159] Console: switching to colour frame buffer device 160x50
[   37.177519] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   37.177734] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   37.461698] apm: BIOS not found.
[   37.554316] r8169: eth0: link down
[   37.554527] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   37.905460] ppdev: user-space parallel port driver
[   48.460021] eth1: no IPv6 routers present
[   54.572530] Bridge firewalling registered
[   65.396043] pan1: no IPv6 routers present

Qué podemos quitar para hacer el ingreso más rápido, pues ahora demora más que cuando tenía alguna de las versiones 9.X.  El cierre no demora 5 segundos.

Saludos.

---

