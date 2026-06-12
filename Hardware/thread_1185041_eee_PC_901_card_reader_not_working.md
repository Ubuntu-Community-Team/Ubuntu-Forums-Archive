---
title: "eee PC 901 card reader not working"
date: 2009-06-11
forum: Hardware
---

### Post by rdjse on 2009-06-11
Today I tried to use the internal card reader on my EEE 901 with Jaunty but my SDcard did not get mounted. When I insert the card into the reader nothing happens. 
The only thing I've found is this flood in dmesg whenever I insert a card into the reader;
> 
[  568.880168] hub 3-0:1.0: unable to enumerate USB device on port 1
[  569.380148] hub 5-0:1.0: unable to enumerate USB device on port 5
[  570.672194] hub 5-0:1.0: unable to enumerate USB device on port 5
[  576.992151] hub 5-0:1.0: unable to enumerate USB device on port 5
[  577.340176] hub 5-0:1.0: unable to enumerate USB device on port 5
[  577.780156] hub 5-0:1.0: unable to enumerate USB device on port 5


This is my lspci output:
```

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Network controller: RaLink RT2860
04:00.0 Ethernet controller: Attansic Technology Corp. L1e Gigabit Ethernet Adapter (rev b0)

```

And here's my lsusb:
```

Bus 005 Device 003: ID 05e3:0505 Genesys Logic, Inc. 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0b05:b700 ASUSTek Computer, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Any ideas? Thanks in advance!

---

### Post by dranoweb on 2010-06-17
The fix is quite simple,

reboot, 

press f2 for bios menu

change os status to "complete" instead of "start"

---

### Post by bolle2000 on 2011-03-16
Hello,
i have a similar problem with my eeepc 901 running ubuntu 10.10: the cardreader does not work at all, when i insert a card that is working on a windows computer nothing happens.

with an sd card inserted dmesg gives me this output:
```
[    0.231828] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0290 (mask 0007)
[    0.231838] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0068 (mask 0003)
[    0.231931] pci 0000:00:1f.2: reg 10: [io  0x0000-0x0007]
[    0.231946] pci 0000:00:1f.2: reg 14: [io  0x0000-0x0003]
[    0.231962] pci 0000:00:1f.2: reg 18: [io  0x0000-0x0007]
[    0.231977] pci 0000:00:1f.2: reg 1c: [io  0x0000-0x0003]
[    0.232011] pci 0000:00:1f.2: reg 20: [io  0xffa0-0xffaf]
[    0.232066] pci 0000:00:1f.2: PME# supported from D3hot
[    0.232077] pci 0000:00:1f.2: PME# disabled
[    0.232160] pci 0000:00:1f.3: reg 20: [io  0x0400-0x041f]
[    0.232293] pci 0000:00:1c.0: PCI bridge to [bus 05-05]
[    0.232306] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.232321] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.232338] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.232516] pci 0000:04:00.0: reg 10: [mem 0xfbfc0000-0xfbffffff 64bit]
[    0.232537] pci 0000:04:00.0: reg 18: [io  0xec80-0xecff]
[    0.232644] pci 0000:04:00.0: PME# supported from D3hot D3cold
[    0.232656] pci 0000:04:00.0: PME# disabled
[    0.232699] pci 0000:04:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.232725] pci 0000:00:1c.1: PCI bridge to [bus 04-04]
[    0.232737] pci 0000:00:1c.1:   bridge window [io  0xe000-0xefff]
[    0.232749] pci 0000:00:1c.1:   bridge window [mem 0xfbf00000-0xfbffffff]
[    0.232765] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.232857] pci 0000:00:1c.2: PCI bridge to [bus 03-03]
[    0.232869] pci 0000:00:1c.2:   bridge window [io  0xf000-0x0000] (disabled)
[    0.232881] pci 0000:00:1c.2:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.232898] pci 0000:00:1c.2:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.233037] pci 0000:01:00.0: reg 10: [mem 0xfbef0000-0xfbefffff]
[    0.233154] pci 0000:01:00.0: PME# supported from D0 D3hot
[    0.233166] pci 0000:01:00.0: PME# disabled
[    0.240089] pci 0000:00:1c.3: PCI bridge to [bus 01-02]
[    0.240105] pci 0000:00:1c.3:   bridge window [io  0xf000-0x0000] (disabled)
[    0.240120] pci 0000:00:1c.3:   bridge window [mem 0xf8000000-0xfbefffff]
[    0.240138] pci 0000:00:1c.3:   bridge window [mem 0xf0000000-0xf6ffffff 64bit pref]
[    0.240269] pci 0000:00:1e.0: PCI bridge to [bus 06-06] (subtractive decode)
[    0.240282] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.240295] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.240311] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.240322] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.240331] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.240340] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.240350] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.240360] pci 0000:00:1e.0:   bridge window [mem 0x3f800000-0xffffffff] (subtractive decode)
[    0.240413] pci_bus 0000:00: on NUMA node 0
[    0.240441] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.240982] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.241190] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]
[    0.241377] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[    0.241712] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[    0.279466] ACPI: PCI Interrupt Link [LNKA] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.279812] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.280164] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.280498] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.280833] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.281159] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.281505] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.281833] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.281995] HEST: Table is not found!
[    0.282286] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.282321] vgaarb: loaded
[    0.282916] SCSI subsystem initialized
[    0.283174] libata version 3.00 loaded.
[    0.283409] usbcore: registered new interface driver usbfs
[    0.283486] usbcore: registered new interface driver hub
[    0.283597] usbcore: registered new device driver usb
[    0.284149] ACPI: WMI: Mapper loaded
[    0.284156] PCI: Using ACPI for IRQ routing
[    0.284239] PCI: pci_cache_line_size set to 64 bytes
[    0.284403] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.284413] reserve RAM buffer: 000000003f7a0000 - 000000003fffffff 
[    0.284765] NetLabel: Initializing
[    0.284775] NetLabel:  domain hash size = 128
[    0.284780] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.284817] NetLabel:  unlabeled traffic allowed by default
[    0.284949] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.284964] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.284979] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.292107] Switching to clocksource tsc
[    0.321928] AppArmor: AppArmor Filesystem Enabled
[    0.321977] pnp: PnP ACPI init
[    0.322030] ACPI: bus type pnp registered
[    0.327930] pnp: PnP ACPI: found 13 devices
[    0.327940] ACPI: ACPI bus type pnp unregistered
[    0.327953] PnPBIOS: Disabled by ACPI PNP
[    0.328004] system 00:01: [mem 0xfed13000-0xfed19fff] has been reserved
[    0.328034] system 00:08: [io  0x025c-0x025f] has been reserved
[    0.328044] system 00:08: [io  0x0380-0x0383] has been reserved
[    0.328054] system 00:08: [io  0x0400-0x041f] has been reserved
[    0.328063] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.328073] system 00:08: [io  0x0800-0x087f] has been reserved
[    0.328083] system 00:08: [io  0x0480-0x04bf] has been reserved
[    0.328095] system 00:08: [mem 0x8c000000-0x8c01ffff] has been reserved
[    0.328105] system 00:08: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.328116] system 00:08: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.328126] system 00:08: [mem 0xfed50000-0xfed8ffff] has been reserved
[    0.328136] system 00:08: [mem 0xffb00000-0xffbfffff] has been reserved
[    0.328149] system 00:08: [mem 0xfff00000-0xffffffff] could not be reserved
[    0.328171] system 00:0a: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.328181] system 00:0a: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.328199] system 00:0b: [mem 0xe0000000-0xe3ffffff] has been reserved
[    0.328218] system 00:0c: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.328229] system 00:0c: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.328239] system 00:0c: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.328249] system 00:0c: [mem 0x00100000-0x3f7fffff] could not be reserved
[    0.369034] pci 0000:00:1c.0: BAR 14: assigned [mem 0x3f800000-0x3f9fffff]
[    0.369050] pci 0000:00:1c.0: BAR 15: assigned [mem 0x3fa00000-0x3fbfffff 64bit pref]
[    0.369062] pci 0000:00:1c.1: BAR 15: assigned [mem 0x3fc00000-0x3fdfffff 64bit pref]
[    0.369073] pci 0000:00:1c.2: BAR 14: assigned [mem 0x3fe00000-0x3fffffff]
[    0.369085] pci 0000:00:1c.2: BAR 15: assigned [mem 0x40000000-0x401fffff 64bit pref]
[    0.369097] pci 0000:00:1c.0: BAR 13: assigned [io  0x1000-0x1fff]
[    0.369108] pci 0000:00:1c.2: BAR 13: assigned [io  0x2000-0x2fff]
[    0.369118] pci 0000:00:1c.3: BAR 13: assigned [io  0x3000-0x3fff]
[    0.369127] pci 0000:00:1c.0: PCI bridge to [bus 05-05]
[    0.369137] pci 0000:00:1c.0:   bridge window [io  0x1000-0x1fff]
[    0.369151] pci 0000:00:1c.0:   bridge window [mem 0x3f800000-0x3f9fffff]
[    0.369164] pci 0000:00:1c.0:   bridge window [mem 0x3fa00000-0x3fbfffff 64bit pref]
[    0.369181] pci 0000:00:1c.1: PCI bridge to [bus 04-04]
[    0.369190] pci 0000:00:1c.1:   bridge window [io  0xe000-0xefff]
[    0.369204] pci 0000:00:1c.1:   bridge window [mem 0xfbf00000-0xfbffffff]
[    0.369216] pci 0000:00:1c.1:   bridge window [mem 0x3fc00000-0x3fdfffff 64bit pref]
[    0.369233] pci 0000:00:1c.2: PCI bridge to [bus 03-03]
[    0.369243] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff]
[    0.369258] pci 0000:00:1c.2:   bridge window [mem 0x3fe00000-0x3fffffff]
[    0.369272] pci 0000:00:1c.2:   bridge window [mem 0x40000000-0x401fffff 64bit pref]
[    0.369290] pci 0000:00:1c.3: PCI bridge to [bus 01-02]
[    0.369301] pci 0000:00:1c.3:   bridge window [io  0x3000-0x3fff]
[    0.369315] pci 0000:00:1c.3:   bridge window [mem 0xf8000000-0xfbefffff]
[    0.369330] pci 0000:00:1c.3:   bridge window [mem 0xf0000000-0xf6ffffff 64bit pref]
[    0.369347] pci 0000:00:1e.0: PCI bridge to [bus 06-06]
[    0.369354] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.369367] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.369378] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.369416] pci 0000:00:1c.0: enabling device (0104 -> 0107)
[    0.369446]   alloc irq_desc for 16 on node -1
[    0.369453]   alloc kstat_irqs on node -1
[    0.369475] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.369492] pci 0000:00:1c.0: setting latency timer to 64
[    0.369514]   alloc irq_desc for 17 on node -1
[    0.369521]   alloc kstat_irqs on node -1
[    0.369533] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.369547] pci 0000:00:1c.1: setting latency timer to 64
[    0.369568] pci 0000:00:1c.2: enabling device (0104 -> 0107)
[    0.369579]   alloc irq_desc for 18 on node -1
[    0.369585]   alloc kstat_irqs on node -1
[    0.369597] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.369609] pci 0000:00:1c.2: setting latency timer to 64
[    0.369629] pci 0000:00:1c.3: enabling device (0106 -> 0107)
[    0.369640]   alloc irq_desc for 19 on node -1
[    0.369646]   alloc kstat_irqs on node -1
[    0.369658] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.369670] pci 0000:00:1c.3: setting latency timer to 64
[    0.369689] pci 0000:00:1e.0: setting latency timer to 64
[    0.369701] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.369709] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.369718] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.369726] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.369735] pci_bus 0000:00: resource 8 [mem 0x3f800000-0xffffffff]
[    0.369744] pci_bus 0000:05: resource 0 [io  0x1000-0x1fff]
[    0.369752] pci_bus 0000:05: resource 1 [mem 0x3f800000-0x3f9fffff]
[    0.369761] pci_bus 0000:05: resource 2 [mem 0x3fa00000-0x3fbfffff 64bit pref]
[    0.369770] pci_bus 0000:04: resource 0 [io  0xe000-0xefff]
[    0.369778] pci_bus 0000:04: resource 1 [mem 0xfbf00000-0xfbffffff]
[    0.369787] pci_bus 0000:04: resource 2 [mem 0x3fc00000-0x3fdfffff 64bit pref]
[    0.369797] pci_bus 0000:03: resource 0 [io  0x2000-0x2fff]
[    0.369805] pci_bus 0000:03: resource 1 [mem 0x3fe00000-0x3fffffff]
[    0.369814] pci_bus 0000:03: resource 2 [mem 0x40000000-0x401fffff 64bit pref]
[    0.369823] pci_bus 0000:01: resource 0 [io  0x3000-0x3fff]
[    0.369832] pci_bus 0000:01: resource 1 [mem 0xf8000000-0xfbefffff]
[    0.369841] pci_bus 0000:01: resource 2 [mem 0xf0000000-0xf6ffffff 64bit pref]
[    0.369850] pci_bus 0000:06: resource 4 [io  0x0000-0x0cf7]
[    0.369858] pci_bus 0000:06: resource 5 [io  0x0d00-0xffff]
[    0.369867] pci_bus 0000:06: resource 6 [mem 0x000a0000-0x000bffff]
[    0.369875] pci_bus 0000:06: resource 7 [mem 0x000d0000-0x000dffff]
[    0.369884] pci_bus 0000:06: resource 8 [mem 0x3f800000-0xffffffff]
[    0.370000] NET: Registered protocol family 2
[    0.370216] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.371121] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.372425] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.373049] TCP: Hash tables configured (established 131072 bind 65536)
[    0.373059] TCP reno registered
[    0.373072] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.373100] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.373454] NET: Registered protocol family 1
[    0.373531] pci 0000:00:02.0: Boot video device
[    0.373769] PCI: CLS 32 bytes, default 64
[    0.374467] cpufreq-nforce2: No nForce2 chipset.
[    0.374577] Scanning for low memory corruption every 60 seconds
[    0.374963] audit: initializing netlink socket (disabled)
[    0.374993] type=2000 audit(1300291771.368:1): initialized
[    0.398913] highmem bounce pool size: 64 pages
[    0.398932] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.404491] VFS: Disk quotas dquot_6.5.2
[    0.404722] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.407006] fuse init (API version 7.14)
[    0.407391] msgmni has been set to 1707
[    0.408674] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.408688] io scheduler noop registered
[    0.408694] io scheduler deadline registered
[    0.408752] io scheduler cfq registered (default)
[    0.409136] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.409212]   alloc irq_desc for 40 on node -1
[    0.409219]   alloc kstat_irqs on node -1
[    0.409244] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.409507] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.409575]   alloc irq_desc for 41 on node -1
[    0.409581]   alloc kstat_irqs on node -1
[    0.409600] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.409856] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.409925]   alloc irq_desc for 42 on node -1
[    0.409932]   alloc kstat_irqs on node -1
[    0.409950] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    0.410196] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.410262]   alloc irq_desc for 43 on node -1
[    0.410268]   alloc kstat_irqs on node -1
[    0.410298] pcieport 0000:00:1c.3: irq 43 for MSI/MSI-X
[    0.410660] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.411037] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.411414] intel_idle: MWAIT substates: 0x20220
[    0.411421] intel_idle: v0.4 model 0x1C
[    0.411427] intel_idle: lapic_timer_reliable_states 0x6
[    0.411447] Marking TSC unstable due to TSC halts in idle states deeper than C2
[    0.411935] ACPI: AC Adapter [AC0] (on-line)
[    0.412190] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.412407] Switching to clocksource hpet
[    0.417304] ACPI: Lid Switch [LID]
[    0.417516] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.417534] ACPI: Sleep Button [SLPB]
[    0.417720] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input2
[    0.417735] ACPI: Power Button [PWRB]
[    0.417912] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.417925] ACPI: Power Button [PWRF]
[    0.418753] ACPI: acpi_idle yielding to intel_idle
[    0.437090] thermal LNXTHERM:01: registered as thermal_zone0
[    0.437124] ACPI: Thermal Zone [TZ00] (55 C)
[    0.437410] ERST: Table is not found!
[    0.438192] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.443365] brd: module loaded
[    0.445571] loop: module loaded
[    0.446275] ata_piix 0000:00:1f.2: version 2.13
[    0.446327] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.446342] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    0.446448] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.446717] isapnp: Scanning for PnP cards...
[    0.452255] scsi0 : ata_piix
[    0.496205] scsi1 : ata_piix
[    0.555093] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.555104] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.556473] Fixed MDIO Bus: probed
[    0.556607] PPP generic driver version 2.4.2
[    0.556784] tun: Universal TUN/TAP device driver, 1.6
[    0.556791] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.557059] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.557118]   alloc irq_desc for 23 on node -1
[    0.557124]   alloc kstat_irqs on node -1
[    0.557144] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.557189] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.557199] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.557461] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.557514] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.557536] ehci_hcd 0000:00:1d.7: debug port 1
[    0.561421] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.568364] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf7eb7c00
[    0.584875] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.585337] hub 1-0:1.0: USB hub found
[    0.585352] hub 1-0:1.0: 8 ports detected
[    0.585565] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.585621] uhci_hcd: USB Universal Host Controller Interface driver
[    0.585718] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.585741] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.585751] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.585889] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.585950] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d480
[    0.586401] hub 2-0:1.0: USB hub found
[    0.586419] hub 2-0:1.0: 2 ports detected
[    0.586612] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.586632] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.586641] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.586792] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.586869] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d800
[    0.587255] hub 3-0:1.0: USB hub found
[    0.587269] hub 3-0:1.0: 2 ports detected
[    0.587423] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.587440] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.587449] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.587571] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.587637] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d880
[    0.588047] hub 4-0:1.0: USB hub found
[    0.588061] hub 4-0:1.0: 2 ports detected
[    0.588212] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.588230] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.588240] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.588357] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.588487] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000dc00
[    0.588860] hub 5-0:1.0: USB hub found
[    0.588873] hub 5-0:1.0: 2 ports detected
[    0.589242] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.643559] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.643589] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.644071] mice: PS/2 mouse device common for all mice
[    0.645944] rtc_cmos 00:03: RTC can wake from S4
[    0.646066] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.646119] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    0.646493] device-mapper: uevent: version 1.0.3
[    0.653967] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    0.671188] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.728597] device-mapper: multipath: version 1.1.1 loaded
[    0.728610] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.729128] EISA: Probing bus 0 at eisa.0
[    0.729138] EISA: Cannot allocate resource for mainboard
[    0.729147] Cannot allocate resource for EISA slot 1
[    0.729155] Cannot allocate resource for EISA slot 2
[    0.729163] Cannot allocate resource for EISA slot 3
[    0.729171] Cannot allocate resource for EISA slot 4
[    0.729178] Cannot allocate resource for EISA slot 5
[    0.729186] Cannot allocate resource for EISA slot 6
[    0.729194] Cannot allocate resource for EISA slot 7
[    0.729202] Cannot allocate resource for EISA slot 8
[    0.729208] EISA: Detected 0 cards.
[    0.745084] cpuidle: using governor ladder
[    0.745485] cpuidle: using governor menu
[    0.746461] TCP cubic registered
[    0.746925] NET: Registered protocol family 10
[    0.747958] lo: Disabled Privacy Extensions
[    0.748686] NET: Registered protocol family 17
[    0.750067] Using IPI No-Shortcut mode
[    0.750381] PM: Resume from disk failed.
[    0.750412] registered taskstats version 1
[    0.750952]   Magic number: 3:496:186
[    0.751111] rtc_cmos 00:03: setting system clock to 2011-03-16 16:09:32 UTC (1300291772)
[    0.751120] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.751126] EDD information not available.
[    0.805652] isapnp: No Plug & Play device found
[    0.825405] ACPI: Battery Slot [BAT0] (battery present)
[    0.845515] ata2.00: CFA: ASUS-PHISON SSD, TST2.04U, max UDMA/66
[    0.845528] ata2.00: 7880544 sectors, multi 0: LBA 
[    0.845617] ata2.01: CFA: ASUS-PHISON SSD, TST2.04P, max UDMA/66
[    0.845626] ata2.01: 31522176 sectors, multi 0: LBA 
[    0.853446] ata2.00: configured for UDMA/66
[    0.861438] ata2.01: configured for UDMA/66
[    0.861824] scsi 1:0:0:0: Direct-Access     ATA      ASUS-PHISON SSD  TST2 PQ: 0 ANSI: 5
[    0.862357] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    0.862798] sd 1:0:0:0: [sda] 7880544 512-byte logical blocks: (4.03 GB/3.75 GiB)
[    0.863031] sd 1:0:0:0: [sda] Write Protect is off
[    0.863042] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.863141] sd 1:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    0.863760]  sda: sda1
[    0.865510] scsi 1:0:1:0: Direct-Access     ATA      ASUS-PHISON SSD  TST2 PQ: 0 ANSI: 5
[    0.866008] sd 1:0:1:0: Attached scsi generic sg1 type 0
[    0.866590] sd 1:0:1:0: [sdb] 31522176 512-byte logical blocks: (16.1 GB/15.0 GiB)
[    0.866834] sd 1:0:0:0: [sda] Attached SCSI disk
[    0.866945] sd 1:0:1:0: [sdb] Write Protect is off
[    0.866956] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    0.867052] sd 1:0:1:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    0.867638]  sdb: sdb1
[    0.869904] sd 1:0:1:0: [sdb] Attached SCSI disk
[    0.897148] hub 1-0:1.0: unable to enumerate USB device on port 7
[    0.902594] Freeing initrd memory: 10512k freed
[    0.915015] Freeing unused kernel memory: 684k freed
[    0.915894] Write protecting the kernel text: 4932k
[    0.915971] Write protecting the kernel read-only data: 1976k
[    0.959534] udev[81]: starting version 163
[    1.009111] usb 1-8: new high speed USB device using ehci_hcd and address 3
[    1.380947] ATL1E 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.380979] ATL1E 0000:04:00.0: setting latency timer to 64
[    1.395827] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    6.088505] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    6.197975] udev[336]: starting version 163
[    6.321324] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[    6.335261] lp: driver loaded but no devices found
[    6.696477] intel_rng: FWH not detected
[    6.777830] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input5
[    6.778031] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    6.905872] leds_ss4200: no LED devices found
[    6.990864] Linux agpgart interface v0.103
[    7.134930] Linux video capture interface: v2.00
[    7.160768] eeepc_laptop: Eee PC Hotkey Driver
[    7.160794] eeepc_laptop: Hotkey init flags 0x41
[    7.261925] agpgart-intel 0000:00:00.0: Intel 945GME Chipset
[    7.262465] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[    7.291903] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (05e3:0505)
[    7.316631] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    7.468991] cfg80211: Calling CRDA to update world regulatory domain
[    7.501207] usbcore: registered new interface driver uvcvideo
[    7.501216] USB Video Class driver (v0.1.0)
[    7.523275] psmouse serio1: ID: 10 00 64
[    7.617928] type=1400 audit(1300291779.362:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=632 comm="apparmor_parser"
[    7.618807] type=1400 audit(1300291779.362:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=632 comm="apparmor_parser"
[    7.619330] type=1400 audit(1300291779.362:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=632 comm="apparmor_parser"
[    7.663313] cfg80211: World regulatory domain updated:
[    7.663324]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    7.663338]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    7.663348]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    7.663357]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    7.663366]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    7.663376]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    7.756989] elantech: assuming hardware version 2, firmware version 2.0.48
[    7.794468] [drm] Initialized drm 1.1.0 20060810
[    7.829609] elantech: Synaptics capabilities query result 0x00, 0x02, 0x64.
[    8.081209] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio1/input/input6
[    8.121452] rt2800pci 0000:01:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    8.121471] rt2800pci 0000:01:00.0: setting latency timer to 64
[    8.293848] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.293866] i915 0000:00:02.0: setting latency timer to 64
[    8.375045]   alloc irq_desc for 44 on node -1
[    8.375058]   alloc kstat_irqs on node -1
[    8.375090] ATL1E 0000:04:00.0: irq 44 for MSI/MSI-X
[    8.375978] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    8.393648] phy0: Selected rate control algorithm 'minstrel'
[    8.395890] Registered led device: rt2800pci-phy0::radio
[    8.395973] Registered led device: rt2800pci-phy0::assoc
[    8.399658] Registered led device: rt2800pci-phy0::quality
[    8.405218] rt2860sta: module is from the staging directory, the quality is unknown, you have been warned.
[    8.455622] [drm] set up 7M of stolen space
[    8.596598] type=1400 audit(1300291780.342:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=774 comm="apparmor_parser"
[    8.602189] type=1400 audit(1300291780.346:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=775 comm="apparmor_parser"
[    8.603081] type=1400 audit(1300291780.346:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=775 comm="apparmor_parser"
[    8.603632] type=1400 audit(1300291780.346:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=775 comm="apparmor_parser"
[    8.607091] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    8.607738] [drm] initialized overlay support
[    8.632787] type=1400 audit(1300291780.378:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=778 comm="apparmor_parser"
[    8.633772] type=1400 audit(1300291780.378:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=778 comm="apparmor_parser"
[    8.654234] type=1400 audit(1300291780.398:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=779 comm="apparmor_parser"
[    8.921842] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    8.961744] Skipping EDID probe due to cached edid
[    9.367386] eeepc_laptop: TYPE (2000000) not reported by BIOS, enabling anyway
[    9.373413] eeepc_laptop: PANELPOWER (4000000) not reported by BIOS, enabling anyway
[    9.373423] eeepc_laptop: Get control methods supported: 0x6101713
[    9.505921] Console: switching to colour frame buffer device 128x37
[    9.514869] fb0: inteldrmfb frame buffer device
[    9.514875] drm: registered panic notifier
[    9.514886] Slow work thread pool: Starting up
[    9.515492] Slow work thread pool: Ready
[    9.515492] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    9.515492] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.518270]   alloc irq_desc for 45 on node -1
[    9.518277]   alloc kstat_irqs on node -1
[    9.518301] HDA Intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[    9.518366] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    9.519389] input: Asus EeePC extra buttons as /devices/platform/eeepc/input/input7
[    9.657086] Skipping EDID probe due to cached edid
[   10.873604] ppdev: user-space parallel port driver
[   11.093198] Skipping EDID probe due to cached edid
[   11.291726] Skipping EDID probe due to cached edid
[   12.420523] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   12.433712] EXT4-fs (sdb1): re-mounted. Opts: commit=0
[   13.584086] Skipping EDID probe due to cached edid
[   13.620094] Skipping EDID probe due to cached edid
[   13.656097] Skipping EDID probe due to cached edid
[   13.692094] Skipping EDID probe due to cached edid
[   18.025538] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   18.038374] EXT4-fs (sdb1): re-mounted. Opts: commit=0
[   26.942242] Skipping EDID probe due to cached edid
[   26.983194] Skipping EDID probe due to cached edid
[   27.024124] Skipping EDID probe due to cached edid
[   27.064084] Skipping EDID probe due to cached edid
[   31.769153] Skipping EDID probe due to cached edid
[   33.246128] Skipping EDID probe due to cached edid
[   33.458436] wlan0: authenticate with 00:23:08:eb:77:58 (try 1)
[   33.460175] wlan0: authenticated
[   33.460268] wlan0: associate with 00:23:08:eb:77:58 (try 1)
[   33.472448] wlan0: RX AssocResp from 00:23:08:eb:77:58 (capab=0x411 status=0 aid=2)
[   33.472457] wlan0: associated
[   33.481508] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   33.482086] cfg80211: Calling CRDA for country: DE
[   33.526084] cfg80211: Received country IE:
[   33.526096] cfg80211: Regulatory domain: DE
[   33.526102]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   33.526113]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (10000 mBi, 1600 mBm)
[   33.526120] cfg80211: CRDA thinks this should applied:
[   33.526126] cfg80211: Regulatory domain: DE
[   33.526131]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   33.526140]     (2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   33.526149]     (5150000 KHz - 5350000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   33.526158]     (5470000 KHz - 5725000 KHz @ 40000 KHz), (N/A, 2698 mBm)
[   33.526165] cfg80211: We intersect both of these and get:
[   33.526171] cfg80211: Regulatory domain: 98
[   33.526176]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   33.526185]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 1600 mBm)
[   33.526202] cfg80211: Disabling channel 2484 MHz on phy0 due to Country IE
[   33.526214] cfg80211: Current regulatory domain updated by AP to: DE
[   33.526220]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   33.526229]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 1600 mBm)
[   33.785842] padlock: VIA PadLock not detected.
[   43.888029] wlan0: no IPv6 routers present
[ 1145.276162] usb 1-3: new high speed USB device using ehci_hcd and address 4
[ 1145.473207] Initializing USB Mass Storage driver...
[ 1145.473598] scsi2 : usb-storage 1-3:1.0
[ 1145.473955] usbcore: registered new interface driver usb-storage
[ 1145.473963] USB Mass Storage support registered.
[ 1146.479393] scsi 2:0:0:0: Direct-Access                  CCR-70       9412 PQ: 0 ANSI: 0
[ 1146.487801] sd 2:0:0:0: Attached scsi generic sg2 type 0
[ 1148.578101] sd 2:0:0:0: [sdc] 3995648 512-byte logical blocks: (2.04 GB/1.90 GiB)
[ 1148.579460] sd 2:0:0:0: [sdc] Write Protect is off
[ 1148.579483] sd 2:0:0:0: [sdc] Mode Sense: 03 00 00 00
[ 1148.579500] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[ 1148.585727] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[ 1148.585788]  sdc: sdc1
[ 1148.596413] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[ 1148.596413] sd 2:0:0:0: [sdc] Attached SCSI removable disk
[ 1169.273956] usb 1-3: USB disconnect, address 4

```

lsusb shows this:

```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05e3:0505 Genesys Logic, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

and lspci this:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Network controller: RaLink RT2860
04:00.0 Ethernet controller: Atheros Communications AR8121/AR8113/AR8114 Gigabit or Fast Ethernet (rev b0)
```

unfortunately i don't have any option in my bios to toggle my OS status to complete.....

any ideas? or is the card reader just broken, which would be a shame?

thank you in advance!!!

---

### Post by RichardM90 on 2011-06-18
The solution dranoweb outlined also worked for me.

When you reboot, press F2 to enter the bios setup utility. 
Then move to the advanced tab. 
The last option on the page is OS Installation, mine was set to Start and I changed this to Finished. 
Exited and saved settings and now SD cards are recognised in the built in card reader.

This was on an eeepc 4g.

Richard

---

### Post by medevacs on 2012-01-12
FYI: this will not work for eee 901 with the newest version of BIOS which currently is 2103 as... there is no such option.

---

### Post by Ledif on 2012-04-12
Same problem with "Oneiric Ocelot" :(

-- 
Ledif

---

### Post by FBMinis on 2012-11-06
I had the same problem using an 8gb Kingston MicroSDHC on my eee 901 with Lubuntu.

The mentioned "F2+bios.." solution did not work, as my Bios didnt show that option.

I just put the Sd card on my other machine running Lubuntu and it immediately detected it. The I formatted it using Gparted following this tutorial:

[http://www.youtube.com/watch?v=xlbjtyMusf8](http://www.youtube.com/watch?v=xlbjtyMusf8)

Tried the card again on the EEE and it worked. :guitar:

---

