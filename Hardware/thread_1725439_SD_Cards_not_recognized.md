---
title: "SD Cards not recognized"
date: 2011-04-09
forum: Hardware
---

### Post by qkzoo on 2011-04-09
Ok, my USB memory stick functions just fine, but for some reason, my SD card is not being recognized.  Windows XP (on another machine) detects the card as normal.  I also plugged the SD card into a portable USB card reader, and ran a command I found on the forums here, and it generated this information:

```


andrew@andrew-HP-Mini-110-3000:~$ sudo lsusb
[sudo] password for andrew: 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0421:00ab Nokia Mobile Phones E71 (PC Suite mode)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 022: ID 05dc:b023 Lexar Media, Inc. 
Bus 001 Device 002: ID 1fea:0047  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
andrew@andrew-HP-Mini-110-3000:~$ 

```

As you can see, the operating system detects the portable card reader, but not the card.  It also does this with a mini SD card for my Nokia Phone, where it's not detected in Ubuntu, but it is in Windows.  Any thoughts into what I need to do to get these detected and mounted properly?

Thanks,

Q

---

### Post by qkzoo on 2011-04-10
Sorry, the card reader above is the one labeled "Lexar Media, Inc".

---

### Post by qkzoo on 2011-04-10
Here's the output of my dmesg in case it helps:

```


[    0.556399] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.556963] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[    0.557404] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.557722] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    0.558460] ACPI Warning for \_SB_.PCI0._OSC: Parameter count mismatch - ASL declared 5, ACPI requires 4 (20100428/nspredef-352)
[    0.558492] \_SB_.PCI0:_OSC evaluation returned wrong type
[    0.558498] _OSC request data:1 1f 1f 
[    0.569108] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    0.569480] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 *10 11 12)
[    0.569873] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[    0.570246] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[    0.570646] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.571024] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.571400] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.571799] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.572006] HEST: Table is not found!
[    0.572252] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.572283] vgaarb: loaded
[    0.572853] SCSI subsystem initialized
[    0.573072] libata version 3.00 loaded.
[    0.573265] usbcore: registered new interface driver usbfs
[    0.573328] usbcore: registered new interface driver hub
[    0.573429] usbcore: registered new device driver usb
[    0.574332] ACPI: WMI: Mapper loaded
[    0.574339] PCI: Using ACPI for IRQ routing
[    0.574349] PCI: pci_cache_line_size set to 64 bytes
[    0.574512] reserve RAM buffer: 0000000000002000 - 000000000000ffff 
[    0.574521] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.574529] reserve RAM buffer: 000000003f43f000 - 000000003fffffff 
[    0.574539] reserve RAM buffer: 000000003f600000 - 000000003fffffff 
[    0.574839] NetLabel: Initializing
[    0.574847] NetLabel:  domain hash size = 128
[    0.574852] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.574893] NetLabel:  unlabeled traffic allowed by default
[    0.575013] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.575028] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.575042] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.584084] Switching to clocksource tsc
[    0.612201] AppArmor: AppArmor Filesystem Enabled
[    0.612237] pnp: PnP ACPI init
[    0.612282] ACPI: bus type pnp registered
[    0.618480] pnp: PnP ACPI: found 9 devices
[    0.618489] ACPI: ACPI bus type pnp unregistered
[    0.618499] PnPBIOS: Disabled by ACPI PNP
[    0.618537] system 00:01: [io  0x0600-0x060f] has been reserved
[    0.618548] system 00:01: [io  0x0610] has been reserved
[    0.618558] system 00:01: [io  0x0800-0x080f] has been reserved
[    0.618568] system 00:01: [io  0x0810-0x0817] has been reserved
[    0.618578] system 00:01: [io  0x0400-0x047f] has been reserved
[    0.618589] system 00:01: [io  0x0500-0x053f] has been reserved
[    0.618602] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.618612] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.618622] system 00:01: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.618632] system 00:01: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.618642] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.618652] system 00:01: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.618662] system 00:01: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.659064] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.659079] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.659094] pci 0000:00:1c.0:   bridge window [mem 0x53000000-0x53ffffff]
[    0.659107] pci 0000:00:1c.0:   bridge window [mem 0x50000000-0x50ffffff 64bit pref]
[    0.659125] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    0.659135] pci 0000:00:1c.1:   bridge window [io  0x1000-0x1fff]
[    0.659150] pci 0000:00:1c.1:   bridge window [mem 0x52000000-0x52ffffff]
[    0.659163] pci 0000:00:1c.1:   bridge window [mem 0x51000000-0x51ffffff 64bit pref]
[    0.659181] pci 0000:00:1e.0: PCI bridge to [bus 03-03]
[    0.659188] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.659201] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.659212] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.659251]   alloc irq_desc for 16 on node -1
[    0.659258]   alloc kstat_irqs on node -1
[    0.659277] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.659290] pci 0000:00:1c.0: setting latency timer to 64
[    0.659312]   alloc irq_desc for 17 on node -1
[    0.659318]   alloc kstat_irqs on node -1
[    0.659330] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.659341] pci 0000:00:1c.1: setting latency timer to 64
[    0.659358] pci 0000:00:1e.0: setting latency timer to 64
[    0.659370] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.659378] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.659386] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.659394] pci_bus 0000:00: resource 7 [mem 0x40000000-0xfebfffff]
[    0.659403] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
[    0.659411] pci_bus 0000:01: resource 1 [mem 0x53000000-0x53ffffff]
[    0.659420] pci_bus 0000:01: resource 2 [mem 0x50000000-0x50ffffff 64bit pref]
[    0.659429] pci_bus 0000:02: resource 0 [io  0x1000-0x1fff]
[    0.659437] pci_bus 0000:02: resource 1 [mem 0x52000000-0x52ffffff]
[    0.659445] pci_bus 0000:02: resource 2 [mem 0x51000000-0x51ffffff 64bit pref]
[    0.659454] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.659462] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.659470] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.659479] pci_bus 0000:03: resource 7 [mem 0x40000000-0xfebfffff]
[    0.659584] NET: Registered protocol family 2
[    0.659773] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.660606] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.661676] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.662262] TCP: Hash tables configured (established 131072 bind 65536)
[    0.662274] TCP reno registered
[    0.662291] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.662319] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.662635] NET: Registered protocol family 1
[    0.662680] pci 0000:00:02.0: Boot video device
[    0.675931] PCI: CLS 64 bytes, default 64
[    0.676001] Simple Boot Flag at 0x44 set to 0x1
[    0.676552] cpufreq-nforce2: No nForce2 chipset.
[    0.676666] Scanning for low memory corruption every 60 seconds
[    0.677091] audit: initializing netlink socket (disabled)
[    0.677118] type=2000 audit(1302490621.672:1): initialized
[    0.700010] highmem bounce pool size: 64 pages
[    0.700027] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.705233] VFS: Disk quotas dquot_6.5.2
[    0.705429] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.707513] fuse init (API version 7.14)
[    0.707871] msgmni has been set to 1709
[    0.738672] Freeing initrd memory: 10516k freed
[    0.751899] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.751908] io scheduler noop registered
[    0.751913] io scheduler deadline registered
[    0.751954] io scheduler cfq registered (default)
[    0.752187] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.752251]   alloc irq_desc for 40 on node -1
[    0.752256]   alloc kstat_irqs on node -1
[    0.752276] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.752467] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.752524]   alloc irq_desc for 41 on node -1
[    0.752529]   alloc kstat_irqs on node -1
[    0.752544] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.752774] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.753046] ACPI Warning for \_SB_.PCI0._OSC: Parameter count mismatch - ASL declared 5, ACPI requires 4 (20100428/nspredef-352)
[    0.753070] \_SB_.PCI0:_OSC evaluation returned wrong type
[    0.753074] _OSC request data:1 0 1f 
[    0.753331] ACPI Warning for \_SB_.PCI0._OSC: Parameter count mismatch - ASL declared 5, ACPI requires 4 (20100428/nspredef-352)
[    0.753353] \_SB_.PCI0:_OSC evaluation returned wrong type
[    0.753357] _OSC request data:1 0 1f 
[    0.753648] ACPI Warning for \_SB_.PCI0._OSC: Parameter count mismatch - ASL declared 5, ACPI requires 4 (20100428/nspredef-352)
[    0.753669] \_SB_.PCI0:_OSC evaluation returned wrong type
[    0.753674] _OSC request data:1 0 1f 
[    0.753924] ACPI Warning for \_SB_.PCI0._OSC: Parameter count mismatch - ASL declared 5, ACPI requires 4 (20100428/nspredef-352)
[    0.753946] \_SB_.PCI0:_OSC evaluation returned wrong type
[    0.753950] _OSC request data:1 0 1f 
[    0.754003] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.754221] intel_idle: MWAIT substates: 0x20220
[    0.754226] intel_idle: v0.4 model 0x1C
[    0.754230] intel_idle: lapic_timer_reliable_states 0x2
[    0.754244] Marking TSC unstable due to TSC halts in idle states deeper than C2
[    0.754343] Switching to clocksource hpet
[    0.755965] ACPI: AC Adapter [AC] (on-line)
[    0.756174] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.756188] ACPI: Power Button [PWRB]
[    0.756292] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    0.757337] ACPI: Lid Switch [LID0]
[    0.757474] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.757484] ACPI: Power Button [PWRF]
[    0.758028] ACPI: acpi_idle yielding to intel_idleACPI Warning for \_TZ_.THRM._AL0: Return Package has no elements (empty) (20100428/nspredef-456)
[    0.771945] ACPI: [Package] has zero elements (f689d3c0)
[    0.771951] ACPI: Invalid active0 threshold
[    0.775224] thermal LNXTHERM:01: registered as thermal_zone0
[    0.775243] ACPI: Thermal Zone [THRM] (56 C)
[    0.775443] ERST: Table is not found!
[    0.775583] isapnp: Scanning for PnP cards...
[    0.776143] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.780550] brd: module loaded
[    0.782437] loop: module loaded
[    0.784284] Fixed MDIO Bus: probed
[    0.784410] PPP generic driver version 2.4.2
[    0.784529] tun: Universal TUN/TAP device driver, 1.6
[    0.784536] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.784772] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.784822] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.784863] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.784873] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.784973] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.785023] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.785044] ehci_hcd 0000:00:1d.7: debug port 1
[    0.788940] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.788988] ehci_hcd 0000:00:1d.7: irq 16, io mem 0x54204400
[    0.804044] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.804444] hub 1-0:1.0: USB hub found
[    0.804486] hub 1-0:1.0: 8 ports detected
[    0.804799] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.804848] uhci_hcd: USB Universal Host Controller Interface driver
[    0.804920] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.804962] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.804972] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.805116] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.805163] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00003080
[    0.805836] hub 2-0:1.0: USB hub found
[    0.805851] hub 2-0:1.0: 2 ports detected
[    0.805996]   alloc irq_desc for 18 on node -1
[    0.806003]   alloc kstat_irqs on node -1
[    0.806019] uhci_hcd 0000:00:1d.1: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.806093] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.806124] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.806233] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.806331] uhci_hcd 0000:00:1d.1: irq 18, io base 0x00003060
[    0.806776] hub 3-0:1.0: USB hub found
[    0.806811] hub 3-0:1.0: 2 ports detected
[    0.806963] uhci_hcd 0000:00:1d.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.807039] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.807069] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.807175] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.807468] uhci_hcd 0000:00:1d.2: irq 17, io base 0x00003040
[    0.807825] hub 4-0:1.0: USB hub found
[    0.807838] hub 4-0:1.0: 2 ports detected
[    0.807983]   alloc irq_desc for 19 on node -1
[    0.807990]   alloc kstat_irqs on node -1
[    0.808047] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.808076] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.808085] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.808203] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.808353] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00003020
[    0.808825] hub 5-0:1.0: USB hub found
[    0.808839] hub 5-0:1.0: 2 ports detected
[    0.809187] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUE] at 0x60,0x64 irq 1,12
[    0.816311] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.816329] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.816546] mice: PS/2 mouse device common for all mice
[    0.816991] rtc_cmos 00:03: RTC can wake from S4
[    0.817104] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.817148] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.817581] device-mapper: uevent: version 1.0.3
[    0.817947] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    0.818303] device-mapper: multipath: version 1.1.1 loaded
[    0.818311] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.818691] EISA: Probing bus 0 at eisa.0
[    0.818699] EISA: Cannot allocate resource for mainboard
[    0.818708] Cannot allocate resource for EISA slot 1
[    0.818716] Cannot allocate resource for EISA slot 2
[    0.818723] Cannot allocate resource for EISA slot 3
[    0.818731] Cannot allocate resource for EISA slot 4
[    0.818738] Cannot allocate resource for EISA slot 5
[    0.818746] Cannot allocate resource for EISA slot 6
[    0.818753] Cannot allocate resource for EISA slot 7
[    0.818761] Cannot allocate resource for EISA slot 8
[    0.818767] EISA: Detected 0 cards.
[    0.819201] cpuidle: using governor ladder
[    0.819645] cpuidle: using governor menu
[    0.820517] TCP cubic registered
[    0.820937] NET: Registered protocol family 10
[    0.821941] lo: Disabled Privacy Extensions
[    0.822529] NET: Registered protocol family 17
[    0.824039] Using IPI No-Shortcut mode
[    0.824316] PM: Resume from disk failed.
[    0.824345] registered taskstats version 1
[    0.825032]   Magic number: 7:464:965
[    0.825159] rtc_cmos 00:03: setting system clock to 2011-04-11 02:57:02 UTC (1302490622)
[    0.825167] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.825173] EDD information not available.
[    0.956418] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.976829] ACPI: Battery Slot [BAT0] (battery present)
[    1.130535] isapnp: No Plug & Play device found
[    1.130604] Freeing unused kernel memory: 688k freed
[    1.131163] Write protecting the kernel text: 4936k
[    1.131238] Write protecting the kernel read-only data: 1980k
[    1.169665] udev[76]: starting version 163
[    1.284163] usb 1-8: new high speed USB device using ehci_hcd and address 4
[    1.469275] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.469352] r8169 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.469480] r8169 0000:01:00.0: setting latency timer to 64
[    1.469502] r8169 0000:01:00.0: (unregistered net_device): unknown MAC, using family default
[    1.469675]   alloc irq_desc for 42 on node -1
[    1.469683]   alloc kstat_irqs on node -1
[    1.469730] r8169 0000:01:00.0: irq 42 for MSI/MSI-X
[    1.471262] r8169 0000:01:00.0: eth0: RTL8101e at 0xf8034000, 00:21:cc:47:89:e1, XID 04000000 IRQ 42
[    1.531263] ahci 0000:00:1f.2: version 3.0
[    1.531302] ahci 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.531384]   alloc irq_desc for 43 on node -1
[    1.531392]   alloc kstat_irqs on node -1
[    1.531416] ahci 0000:00:1f.2: irq 43 for MSI/MSI-X
[    1.531506] ahci: SSS flag set, parallel bus scan disabled
[    1.531565] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0x3 impl SATA mode
[    1.531576] ahci 0000:00:1f.2: flags: 64bit ncq ilck stag pm led clo pmp pio slum part 
[    1.531590] ahci 0000:00:1f.2: setting latency timer to 64
[    1.533414] scsi0 : ahci
[    1.533801] scsi1 : ahci
[    1.534063] scsi2 : ahci
[    1.534330] scsi3 : ahci
[    1.535177] ata1: SATA max UDMA/133 abar m1024@0x54204000 port 0x54204100 irq 43
[    1.535191] ata2: SATA max UDMA/133 abar m1024@0x54204000 port 0x54204180 irq 43
[    1.535199] ata3: DUMMY
[    1.535205] ata4: DUMMY
[    1.692125] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    2.024142] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.025756] ata1.00: unexpected _GTF length (4)
[    2.026136] ata1.00: ATA-8: ST9160314AS, 0001SDM1, max UDMA/133
[    2.026148] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.028152] ata1.00: unexpected _GTF length (4)
[    2.028588] ata1.00: configured for UDMA/133
[    2.044402] scsi 0:0:0:0: Direct-Access     ATA      ST9160314AS      0001 PQ: 0 ANSI: 5
[    2.044938] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.045254] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    2.045412] sd 0:0:0:0: [sda] Write Protect is off
[    2.045420] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.045486] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.046098]  sda: sda1 sda2 < sda5 >
[    2.093151] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.112625] usb 2-2: new full speed USB device using uhci_hcd and address 3
[    2.293495] hub 2-2:1.0: USB hub found
[    2.295360] hub 2-2:1.0: 3 ports detected
[    2.364140] ata2: SATA link down (SStatus 0 SControl 300)
[    2.397456] usbcore: registered new interface driver hiddev
[    2.452249] input: Microsoft Microsoft Wireless Optical Mouse® 1.00 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input4
[    2.452695] generic-usb 0003:045E:00E1.0001: input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse® 1.00] on usb-0000:00:1d.0-1/input0
[    2.452764] usbcore: registered new interface driver usbhid
[    2.452772] usbhid: USB HID core driver
[    2.577359] usb 2-2.1: new full speed USB device using uhci_hcd and address 4
[    2.705428] input: HID 0a5c:4502 as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2.1/2-2.1:1.0/input/input5
[    2.705702] generic-usb 0003:0A5C:4502.0002: input,hidraw1: USB HID v1.11 Keyboard [HID 0a5c:4502] on usb-0000:00:1d.0-2.1/input0
[    2.765340] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    2.778347] usb 2-2.2: new full speed USB device using uhci_hcd and address 5
[    2.904978] input: HID 0a5c:4503 as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2.2/2-2.2:1.0/input/input6
[    2.905217] generic-usb 0003:0A5C:4503.0003: input,hidraw2: USB HID v1.11 Mouse [HID 0a5c:4503] on usb-0000:00:1d.0-2.2/input0
[    2.977364] usb 2-2.3: new full speed USB device using uhci_hcd and address 6
[   15.561797] Adding 3068924k swap on /dev/sda5.  Priority:-1 extents:1 across:3068924k 
[   15.707502] udev[336]: starting version 163
[   15.757730] lp: driver loaded but no devices found
[   16.292859] Linux agpgart interface v0.103
[   16.439463] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   16.528746] Linux video capture interface: v2.00
[   16.535797] agpgart-intel 0000:00:00.0: Intel GMA3150 Chipset
[   16.536623] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
[   16.616448] uvcvideo: Found UVC 1.00 device HP Webcam (1fea:0047)
[   16.707493] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x40000000
[   16.710160] input: HP Webcam as /devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/input/input7
[   16.710355] usbcore: registered new interface driver uvcvideo
[   16.710361] USB Video Class driver (v0.1.0)
[   16.740674] cfg80211: Calling CRDA to update world regulatory domain
[   16.746707] Bluetooth: Core ver 2.15
[   16.746772] NET: Registered protocol family 31
[   16.746777] Bluetooth: HCI device and connection manager initialized
[   16.746784] Bluetooth: HCI socket layer initialized
[   16.885376] [drm] Initialized drm 1.1.0 20060810
[   16.896415] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   16.899027] input: HP WMI hotkeys as /devices/virtual/input/input8
[   16.950053] cfg80211: World regulatory domain updated:
[   16.950065]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   16.950077]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.950086]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.950096]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.950105]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.950114]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.115368] type=1400 audit(1302490638.786:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=633 comm="apparmor_parser"
[   17.116184] type=1400 audit(1302490638.790:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=633 comm="apparmor_parser"
[   17.116736] type=1400 audit(1302490638.790:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=633 comm="apparmor_parser"
[   17.186222] usbcore: registered new interface driver btusb
[   17.290727] i915 0000:00:02.0: power state changed by ACPI to D0
[   17.290765] i915 0000:00:02.0: power state changed by ACPI to D0
[   17.290783] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.290796] i915 0000:00:02.0: setting latency timer to 64
[   17.360566] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.360594] ath9k 0000:02:00.0: setting latency timer to 64
[   17.413383] ath: EEPROM regdomain: 0x60
[   17.413391] ath: EEPROM indicates we should expect a direct regpair map
[   17.413403] ath: Country alpha2 being used: 00
[   17.413409] ath: Regpair used: 0x60
[   17.432547]   alloc irq_desc for 44 on node -1
[   17.432557]   alloc kstat_irqs on node -1
[   17.432579] i915 0000:00:02.0: irq 44 for MSI/MSI-X
[   17.432604] [drm] set up 7M of stolen space
[   17.589195] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   17.590384] [drm] initialized overlay support
[   17.901297] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   17.903259] Registered led device: ath9k-phy0::radio
[   17.903329] Registered led device: ath9k-phy0::assoc
[   17.903399] Registered led device: ath9k-phy0::tx
[   17.903468] Registered led device: ath9k-phy0::rx
[   17.903490] phy0: Atheros AR9285 Rev:2 mem=0xf8280000, irq=17
[   17.904937] Skipping EDID probe due to cached edid
[   18.013289] type=1400 audit(1302490639.686:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=811 comm="apparmor_parser"
[   18.019278] type=1400 audit(1302490639.690:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=812 comm="apparmor_parser"
[   18.019937] type=1400 audit(1302490639.690:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=812 comm="apparmor_parser"
[   18.020331] type=1400 audit(1302490639.694:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=812 comm="apparmor_parser"
[   18.047528] type=1400 audit(1302490639.718:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=815 comm="apparmor_parser"
[   18.048435] type=1400 audit(1302490639.722:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=815 comm="apparmor_parser"
[   18.052845] type=1400 audit(1302490639.726:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=813 comm="apparmor_parser"
[   18.116399] r8169 0000:01:00.0: eth0: link down
[   18.117001] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.359837] Console: switching to colour frame buffer device 128x37
[   18.369180] fb0: inteldrmfb frame buffer device
[   18.369187] drm: registered panic notifier
[   18.371115] Slow work thread pool: Starting up
[   18.390146] Slow work thread pool: Ready
[   18.400290] acpi device:20: registered as cooling_device2
[   18.402808] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input9
[   18.413135] ACPI: Video Device [OVGA] (multi-head: yes  rom: no  post: no)
[   18.414284] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   18.414390] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.414494]   alloc irq_desc for 45 on node -1
[   18.414501]   alloc kstat_irqs on node -1
[   18.414528] HDA Intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   18.414591] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   18.487129] Synaptics Touchpad, model: 1, fw: 7.4, id: 0x1e0b1, caps: 0xd04771/0xa40000/0xa0400
[   18.533564] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input10
[   18.548922] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   18.549465] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   18.553549] Skipping EDID probe due to cached edid
[   18.780961] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   18.780974] vboxdrv: Warning: 2.6.31+ kernel detected. Most likely the hardware performance
[   18.780979] vboxdrv: counter framework which can generate NMIs is active. You have to prevent
[   18.780983] vboxdrv: the usage of hardware performance counters by
[   18.780987] vboxdrv:   echo 2 > /proc/sys/kernel/perf_counter_paranoid
[   18.781677] vboxdrv: Found 2 processor cores.
[   18.781895] vboxdrv: fAsync=0 offMin=0x258 offMax=0x30fc
[   18.782049] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   18.782057] vboxdrv: Successfully loaded version 3.2.8_OSE (interface 0x00140001).
[   19.004685] ppdev: user-space parallel port driver
[   19.069601] Bluetooth: L2CAP ver 2.14
[   19.069610] Bluetooth: L2CAP socket layer initialized
[   19.204797] Skipping EDID probe due to cached edid
[   19.228081] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.228091] Bluetooth: BNEP filters: protocol multicast
[   19.236793] Skipping EDID probe due to cached edid
[   19.274864] Bluetooth: SCO (Voice Link) ver 0.6
[   19.274872] Bluetooth: SCO socket layer initialized
[   19.543525] Bluetooth: RFCOMM TTY layer initialized
[   19.543542] Bluetooth: RFCOMM socket layer initialized
[   19.543549] Bluetooth: RFCOMM ver 1.11
[   20.478700] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   20.732644] Skipping EDID probe due to cached edid
[   20.768125] Skipping EDID probe due to cached edid
[   20.812118] Skipping EDID probe due to cached edid
[   20.852099] Skipping EDID probe due to cached edid
[   22.987477] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   36.884632] Skipping EDID probe due to cached edid
[   36.920647] Skipping EDID probe due to cached edid
[   36.956639] Skipping EDID probe due to cached edid
[   36.992130] Skipping EDID probe due to cached edid
[   37.604102] Skipping EDID probe due to cached edid
[   38.101138] lo: Disabled Privacy Extensions
[   39.016130] Skipping EDID probe due to cached edid
[   39.048213] Skipping EDID probe due to cached edid
[   74.188450] PPP BSD Compression module registered
[   74.198062] PPP Deflate Compression module registered
[  124.141207] lo: Disabled Privacy Extensions
andrew@andrew-HP-Mini-110-3000:~$ 

```

---

### Post by qkzoo on 2011-04-10
Ok, well, here's some more information that may or may not be relevent.  I saw in another forum, somebody said to type this command and post the output, so here's mine:

```


andrew@andrew-HP-Mini-110-3000:~$ lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 04)
01:00.1 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5288 (rev 01)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
andrew@andrew-HP-Mini-110-3000:~$ 

```

...I'm not sure what I'm supposed to do with this information, so perhaps somebody could point me in the right direction?

Thanks,

Q

---

### Post by qkzoo on 2011-04-12
Anybody?

---

### Post by dandnsmith on 2011-04-12
You could consider the possibility that it might be the particular card which is the problem - have you tried others?

Note: some cards are not accepted/recognized by certain readers - it's usually the higher capacity cards which are to a higher spec (I've forgotten the key words for this), and I did buy another card reader to cope with these.

---

### Post by coffeecat on 2011-04-12
> **dandnsmith said:**
> 
Note: some cards are not accepted/recognized by certain readers - it's usually the higher capacity cards which are to a higher spec (I've forgotten the key words for this), and I did buy another card reader to cope with these.

That's what I found. It's the SDHC cards which can be the problem in some, but not all, card readers. With an 8GB SDHC card I found that it read OK in my inbuilt card reader in my laptop and in one of those cheap SD card USB devices, but not in another USB device and in the (old-ish) card reader I built into my desktop. Whereas Windows 7 was fine with all. Presumably a deficiency in some, but not all, of the Linux drivers. I'm surprised that the legacy XP is OK. Perhaps Microsoft shipped updated drivers in SP3 or an update.

@qkzoo, is the card you are having difficulty with an SDHC, rather than SD.

---

### Post by qkzoo on 2011-04-12
No, the card is an SD 1 gigabyte Sandisk card, that works fine with my Windows XP machine.  As above in those commands I posted the output of, I'm pretty sure that both the external USB card reader, and the internal card reader are being detected, but the card isn't.  

I also have a 4 gb micro sd card, not sure what brand or anything off the top of my head, but it isn't being read as well.  I have a generic USB flash drive, that works fine however.  Does it maybe have something to do with the file system on the card?

**NOTE:** the 1 gigabyte card I'm trying to read is from my digital camera, so I'm not sure that I can go messing with the file system of it, since it may have been written by the camera.  Also, when Windows 7 was on this pc, it read the card without a hitch.

---

### Post by coffeecat on 2011-04-12
> **qkzoo said:**
>   Does it maybe have something to do with the file system on the card?

It shouldn't do if the filesystem is FAT16 or FAT32. Ubuntu is fine with those. Clutching at straws here, but you sometimes get a situation where a filesystem corruption is tolerated by Windows but prevents the device being mounted by Linux. Try copying anything you need off the SD card and then reformatting it, either in Windows or in a digital camera. See if it works then.

---

### Post by qkzoo on 2011-04-13
Ok, so I formatted the card in the camera, stuck it back in Ubuntu, and nothing.  Next, I formatted the card in Windows XP via our desktop.  XP appeared to format the card, and then at the very end, said that it could not finish formatting the card, with no real explanation of why.  Is there a way to make Ubuntu more "lenient" as you stated Windows, and apparently my camera are?

Also, I have a micro SD card, 4 gigabyte that isn't reading as well, neither in the internal USB card slot (via sd adapter), nor in an external USB card reader (via sd adapter).  What's the solution you've found for SDHC cards that works?  My goal is to not be dependent on a Windows machine if at all possible, as I'd like to convert our desktop over to Ubuntu exclusively, but little things like this are holding me back...

---

### Post by dandnsmith on 2011-04-14
How about a sanity check now?
Boot from a liveCD, preferably from Ubuntu 10.04 or earlier - I suggest this as there have been some oddities thrown up with 10.10.
If the cards load with this, then you'll have a clue where to look.

---

### Post by qkzoo on 2011-04-17
You're on to something there.  I didn't install 10.04, but jumped up to the 11.04 beta, and it appears to detect the card, something must have changed.

---

