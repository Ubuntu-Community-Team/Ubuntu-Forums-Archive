---
title: "USB 3.0 External drive not transfering data at superspeed."
date: 2013-01-15
forum: Hardware
---

### Post by TonyLudwick on 2013-01-15
Good Morning,
I am having trouble getting our  external USB 3.0 Drive to operate at superspeed. The box has the  following specs:
ASRock 890FX Deluxe 5 Motherboard
AMD Athlon II X4 630 Processor 2800 MHz
10 Gig of Ram
Ubuntu Server / Kernel 3.2.0-35-generic
Silverstone PCI Express USB 3.0 card wi NEC Chip
Vantec  External Hard Drive cabinet - NexStar-HX4R capable of holding 4 sata  drives. Currently only have one Seagate 3TB Drive inside it.

It takes 3 minutes and 24 seconds to copy a 3.7 GB file from the box to the external.

I takes only 42 seconds to copy that same file from another box running Kubuntu 12.04 64 bit / Kernel 3.2.0-35-generic using the same Silverstone PCI Express USB 3.0 card, but in a Dell precision T3400.

i  will attach the dmesg output below but I am not sure what I am looking  for.  I did see where the drive was detected as a superspeed device. 

Any help would be appreciated.  Thank You in advance.

Tony

```

[    0.400078] pci 0000:00:05.0: PME# disabled
[    0.400089] pci 0000:00:06.0: [1002:5a1a] type 1 class 0x000604
[    0.400117] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.400119] pci 0000:00:06.0: PME# disabled
[    0.400132] pci 0000:00:09.0: [1002:5a1c] type 1 class 0x000604
[    0.400159] pci 0000:00:09.0: PME# supported from D0 D3hot D3cold
[    0.400161] pci 0000:00:09.0: PME# disabled
[    0.400185] pci 0000:00:11.0: [1002:4391] type 0 class 0x000106
[    0.400201] pci 0000:00:11.0: reg 10: [io  0xf040-0xf047]
[    0.400209] pci 0000:00:11.0: reg 14: [io  0xf030-0xf033]
[    0.400217] pci 0000:00:11.0: reg 18: [io  0xf020-0xf027]
[    0.400225] pci 0000:00:11.0: reg 1c: [io  0xf010-0xf013]
[    0.400233] pci 0000:00:11.0: reg 20: [io  0xf000-0xf00f]
[    0.400241] pci 0000:00:11.0: reg 24: [mem 0xfe704000-0xfe7043ff]
[    0.400293] pci 0000:00:14.0: [1002:4385] type 0 class 0x000c05
[    0.400359] pci 0000:00:14.2: [1002:4383] type 0 class 0x000403
[    0.400377] pci 0000:00:14.2: reg 10: [mem 0xfe700000-0xfe703fff 64bit]
[    0.400431] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.400435] pci 0000:00:14.2: PME# disabled
[    0.400448] pci 0000:00:14.3: [1002:439d] type 0 class 0x000601
[    0.400512] pci 0000:00:14.4: [1002:4384] type 1 class 0x000604
[    0.400554] pci 0000:00:15.0: [1002:43a0] type 1 class 0x000604
[    0.400615] pci 0000:00:15.0: supports D1 D2
[    0.400638] pci 0000:00:18.0: [1022:1200] type 0 class 0x000600
[    0.400653] pci 0000:00:18.1: [1022:1201] type 0 class 0x000600
[    0.400664] pci 0000:00:18.2: [1022:1202] type 0 class 0x000600
[    0.400676] pci 0000:00:18.3: [1022:1203] type 0 class 0x000600
[    0.400691] pci 0000:00:18.4: [1022:1204] type 0 class 0x000600
[    0.400735] pci 0000:01:00.0: [10de:10c3] type 0 class 0x000300
[    0.400744] pci 0000:01:00.0: reg 10: [mem 0xfd000000-0xfdffffff]
[    0.400753] pci 0000:01:00.0: reg 14: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.400762] pci 0000:01:00.0: reg 1c: [mem 0xd0000000-0xd1ffffff 64bit pref]
[    0.400768] pci 0000:01:00.0: reg 24: [io  0xe000-0xe07f]
[    0.400774] pci 0000:01:00.0: reg 30: [mem 0xfe000000-0xfe07ffff pref]
[    0.400822] pci 0000:01:00.1: [10de:0be3] type 0 class 0x000403
[    0.400830] pci 0000:01:00.1: reg 10: [mem 0xfe080000-0xfe083fff]
[    0.408053] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    0.408112] pci 0000:00:02.0:   bridge window [io  0xe000-0xefff]
[    0.408115] pci 0000:00:02.0:   bridge window [mem 0xfd000000-0xfe0fffff]
[    0.408119] pci 0000:00:02.0:   bridge window [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.408154] pci 0000:02:00.0: [1b4b:9120] type 0 class 0x000106
[    0.408164] pci 0000:02:00.0: reg 10: [io  0xd090-0xd097]
[    0.408171] pci 0000:02:00.0: reg 14: [io  0xd080-0xd083]
[    0.408177] pci 0000:02:00.0: reg 18: [io  0xd070-0xd077]
[    0.408183] pci 0000:02:00.0: reg 1c: [io  0xd060-0xd063]
[    0.408189] pci 0000:02:00.0: reg 20: [io  0xd050-0xd05f]
[    0.408195] pci 0000:02:00.0: reg 24: [mem 0xfe615000-0xfe6157ff]
[    0.408202] pci 0000:02:00.0: reg 30: [mem 0xfe600000-0xfe60ffff pref]
[    0.408231] pci 0000:02:00.0: PME# supported from D3hot
[    0.408234] pci 0000:02:00.0: PME# disabled
[    0.416055] pci 0000:00:04.0: PCI bridge to [bus 02-02]
[    0.416113] pci 0000:00:04.0:   bridge window [io  0xd000-0xdfff]
[    0.416116] pci 0000:00:04.0:   bridge window [mem 0xfe600000-0xfe6fffff]
[    0.416155] pci 0000:03:00.0: [1033:0194] type 0 class 0x000c03
[    0.416170] pci 0000:03:00.0: reg 10: [mem 0xfe500000-0xfe501fff 64bit]
[    0.416240] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.416244] pci 0000:03:00.0: PME# disabled
[    0.424052] pci 0000:00:05.0: PCI bridge to [bus 03-03]
[    0.424113] pci 0000:00:05.0:   bridge window [mem 0xfe500000-0xfe5fffff]
[    0.424152] pci 0000:04:00.0: [1033:0194] type 0 class 0x000c03
[    0.424168] pci 0000:04:00.0: reg 10: [mem 0xfe400000-0xfe401fff 64bit]
[    0.424238] pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
[    0.424241] pci 0000:04:00.0: PME# disabled
[    0.432057] pci 0000:00:06.0: PCI bridge to [bus 04-04]
[    0.432117] pci 0000:00:06.0:   bridge window [mem 0xfe400000-0xfe4fffff]
[    0.432156] pci 0000:05:00.0: [1106:3403] type 0 class 0x000c00
[    0.432173] pci 0000:05:00.0: reg 10: [mem 0xfe310000-0xfe3107ff 64bit]
[    0.432181] pci 0000:05:00.0: reg 18: [io  0xc000-0xc0ff]
[    0.432248] pci 0000:05:00.0: supports D2
[    0.432249] pci 0000:05:00.0: PME# supported from D2 D3hot D3cold
[    0.432253] pci 0000:05:00.0: PME# disabled
[    0.432280] pci 0000:05:00.1: [1106:0415] type 0 class 0x000101
[    0.432292] pci 0000:05:00.1: reg 10: [io  0xc140-0xc147]
[    0.432300] pci 0000:05:00.1: reg 14: [io  0xc130-0xc133]
[    0.432308] pci 0000:05:00.1: reg 18: [io  0xc120-0xc127]
[    0.432317] pci 0000:05:00.1: reg 1c: [io  0xc110-0xc113]
[    0.432325] pci 0000:05:00.1: reg 20: [io  0xc100-0xc10f]
[    0.432340] pci 0000:05:00.1: reg 30: [mem 0xfe300000-0xfe30ffff pref]
[    0.432378] pci 0000:05:00.1: supports D2
[    0.432380] pci 0000:05:00.1: PME# supported from D2 D3hot D3cold
[    0.432383] pci 0000:05:00.1: PME# disabled
[    0.440057] pci 0000:00:09.0: PCI bridge to [bus 05-05]
[    0.440116] pci 0000:00:09.0:   bridge window [io  0xc000-0xcfff]
[    0.440119] pci 0000:00:09.0:   bridge window [mem 0xfe300000-0xfe3fffff]
[    0.440164] pci 0000:06:05.0: [14e4:1644] type 0 class 0x000200
[    0.440190] pci 0000:06:05.0: reg 10: [mem 0xfe200000-0xfe20ffff 64bit]
[    0.440301] pci 0000:06:05.0: PME# supported from D3hot D3cold
[    0.440306] pci 0000:06:05.0: PME# disabled
[    0.440352] pci 0000:00:14.4: PCI bridge to [bus 06-06] (subtractive decode)
[    0.440411] pci 0000:00:14.4:   bridge window [mem 0xfe200000-0xfe2fffff]
[    0.440415] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.440417] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.440419] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.440421] pci 0000:00:14.4:   bridge window [mem 0x000c8000-0x000dffff] (subtractive decode)
[    0.440423] pci 0000:00:14.4:   bridge window [mem 0xc0000000-0xffffffff] (subtractive decode)
[    0.440497] pci 0000:07:00.0: [1912:0014] type 0 class 0x000c03
[    0.440527] pci 0000:07:00.0: reg 10: [mem 0xfe100000-0xfe101fff 64bit]
[    0.440677] pci 0000:07:00.0: PME# supported from D0 D3hot D3cold
[    0.440683] pci 0000:07:00.0: PME# disabled
[    0.448062] pci 0000:00:15.0: PCI bridge to [bus 07-07]
[    0.448133] pci 0000:00:15.0:   bridge window [mem 0xfe100000-0xfe1fffff]
[    0.448159] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.448306] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PC02._PRT]
[    0.448327] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PC04._PRT]
[    0.448347] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PC05._PRT]
[    0.448364] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PC06._PRT]
[    0.448382] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PC09._PRT]
[    0.448418] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[    0.448454] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PE20._PRT]
[    0.448473]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.448528]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.448592] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.451421] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11 14 15) *0
[    0.451778] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11 14 15) *0
[    0.452124] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11 14 15) *0
[    0.452478] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11 14 15) *0
[    0.452821] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11 14 15) *0
[    0.453157] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11 14 15) *0
[    0.453495] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11 14 15) *0
[    0.453831] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11 14 15) *0
[    0.454241] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.454241] vgaarb: loaded
[    0.454241] vgaarb: bridge control possible 0000:01:00.0
[    0.454241] i2c-core: driver [aat2870] using legacy suspend method
[    0.454241] i2c-core: driver [aat2870] using legacy resume method
[    0.454241] SCSI subsystem initialized
[    0.454241] libata version 3.00 loaded.
[    0.454241] usbcore: registered new interface driver usbfs
[    0.454241] usbcore: registered new interface driver hub
[    0.454241] usbcore: registered new device driver usb
[    0.454241] PCI: Using ACPI for IRQ routing
[    0.462333] PCI: pci_cache_line_size set to 64 bytes
[    0.462401] reserve RAM buffer: 0000000000099400 - 000000000009ffff 
[    0.462403] reserve RAM buffer: 00000000bfa85000 - 00000000bfffffff 
[    0.462405] reserve RAM buffer: 00000000bff00000 - 00000000bfffffff 
[    0.462491] NetLabel: Initializing
[    0.462542] NetLabel:  domain hash size = 128
[    0.462593] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.462651] NetLabel:  unlabeled traffic allowed by default
[    0.462746] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.462746] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    0.465057] Switching to clocksource hpet
[    0.469453] AppArmor: AppArmor Filesystem Enabled
[    0.469533] pnp: PnP ACPI init
[    0.469596] ACPI: bus type pnp registered
[    0.469771] pnp 00:00: [bus 00-ff]
[    0.469773] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.469775] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.469777] pnp 00:00: [io  0x0d00-0xffff window]
[    0.469781] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.469783] pnp 00:00: [mem 0x000c8000-0x000dffff window]
[    0.469784] pnp 00:00: [mem 0xc0000000-0xffffffff window]
[    0.469786] pnp 00:00: [mem 0x00000000 window]
[    0.469839] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.469864] pnp 00:01: [mem 0xe0000000-0xefffffff]
[    0.469910] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.469966] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.470028] pnp 00:02: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.470030] pnp 00:02: [mem 0xfec20000-0xfec200ff]
[    0.470060] system 00:02: [mem 0xfec20000-0xfec200ff] could not be reserved
[    0.470115] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.470147] pnp 00:03: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.470177] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.470349] pnp 00:04: [io  0x040b]
[    0.470351] pnp 00:04: [io  0x04d6]
[    0.470352] pnp 00:04: [io  0x0c00-0x0c01]
[    0.470354] pnp 00:04: [io  0x0c14]
[    0.470355] pnp 00:04: [io  0x0c50-0x0c51]
[    0.470357] pnp 00:04: [io  0x0c52]
[    0.470358] pnp 00:04: [io  0x0c6c]
[    0.470359] pnp 00:04: [io  0x0c6f]
[    0.470360] pnp 00:04: [io  0x0cd0-0x0cd1]
[    0.470362] pnp 00:04: [io  0x0cd2-0x0cd3]
[    0.470363] pnp 00:04: [io  0x0cd4-0x0cd5]
[    0.470365] pnp 00:04: [io  0x0cd6-0x0cd7]
[    0.470366] pnp 00:04: [io  0x0cd8-0x0cdf]
[    0.470367] pnp 00:04: [io  0x0800-0x089f]
[    0.470369] pnp 00:04: [io  0x0000-0xffffffffffffffff disabled]
[    0.470371] pnp 00:04: [io  0x0000-0x000f]
[    0.470372] pnp 00:04: [io  0x0b20-0x0b3f]
[    0.470373] pnp 00:04: [io  0x0900-0x090f]
[    0.470375] pnp 00:04: [io  0x0910-0x091f]
[    0.470376] pnp 00:04: [io  0xfe00-0xfefe]
[    0.470378] pnp 00:04: [io  0x0060-0x005f disabled]
[    0.470379] pnp 00:04: [io  0x0064-0x0063 disabled]
[    0.470381] pnp 00:04: [mem 0xfec00000-0xfec00fff]
[    0.470382] pnp 00:04: [mem 0xfee00000-0xfee00fff]
[    0.470384] pnp 00:04: [mem 0xfed80000-0xfed8ffff]
[    0.470385] pnp 00:04: [mem 0xfed61000-0xfed70fff]
[    0.470387] pnp 00:04: [mem 0xfec10000-0xfec10fff]
[    0.470389] pnp 00:04: [mem 0xfed00000-0xfed00fff]
[    0.470390] pnp 00:04: [mem 0xffc00000-0xffffffff]
[    0.470448] system 00:04: [io  0x040b] has been reserved
[    0.470501] system 00:04: [io  0x04d6] has been reserved
[    0.470554] system 00:04: [io  0x0c00-0x0c01] has been reserved
[    0.470608] system 00:04: [io  0x0c14] has been reserved
[    0.470660] system 00:04: [io  0x0c50-0x0c51] has been reserved
[    0.470714] system 00:04: [io  0x0c52] has been reserved
[    0.470769] system 00:04: [io  0x0c6c] has been reserved
[    0.470821] system 00:04: [io  0x0c6f] has been reserved
[    0.470874] system 00:04: [io  0x0cd0-0x0cd1] has been reserved
[    0.470927] system 00:04: [io  0x0cd2-0x0cd3] has been reserved
[    0.470981] system 00:04: [io  0x0cd4-0x0cd5] has been reserved
[    0.471034] system 00:04: [io  0x0cd6-0x0cd7] has been reserved
[    0.471088] system 00:04: [io  0x0cd8-0x0cdf] has been reserved
[    0.471141] system 00:04: [io  0x0800-0x089f] has been reserved
[    0.471195] system 00:04: [io  0x0b20-0x0b3f] has been reserved
[    0.471248] system 00:04: [io  0x0900-0x090f] has been reserved
[    0.471302] system 00:04: [io  0x0910-0x091f] has been reserved
[    0.471355] system 00:04: [io  0xfe00-0xfefe] has been reserved
[    0.471409] system 00:04: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.471464] system 00:04: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.471519] system 00:04: [mem 0xfed80000-0xfed8ffff] has been reserved
[    0.471573] system 00:04: [mem 0xfed61000-0xfed70fff] has been reserved
[    0.471627] system 00:04: [mem 0xfec10000-0xfec10fff] has been reserved
[    0.471682] system 00:04: [mem 0xfed00000-0xfed00fff] has been reserved
[    0.471736] system 00:04: [mem 0xffc00000-0xffffffff] has been reserved
[    0.471791] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.471830] pnp 00:05: [io  0x0000-0xffffffffffffffff disabled]
[    0.471832] pnp 00:05: [io  0x0290-0x029f]
[    0.471834] pnp 00:05: [io  0x0000-0xffffffffffffffff disabled]
[    0.471868] system 00:05: [io  0x0290-0x029f] has been reserved
[    0.471923] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.472140] pnp 00:06: [io  0x03f0-0x03f5]
[    0.472143] pnp 00:06: [io  0x03f7]
[    0.472152] pnp 00:06: [irq 6]
[    0.472153] pnp 00:06: [dma 2]
[    0.472196] pnp 00:06: Plug and Play ACPI device, IDs PNP0700 (active)
[    0.472283] pnp 00:07: [dma 4]
[    0.472284] pnp 00:07: [io  0x0000-0x000f]
[    0.472286] pnp 00:07: [io  0x0081-0x0083]
[    0.472287] pnp 00:07: [io  0x0087]
[    0.472289] pnp 00:07: [io  0x0089-0x008b]
[    0.472290] pnp 00:07: [io  0x008f]
[    0.472291] pnp 00:07: [io  0x00c0-0x00df]
[    0.472316] pnp 00:07: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.472323] pnp 00:08: [io  0x0070-0x0071]
[    0.472326] pnp 00:08: [irq 8]
[    0.472349] pnp 00:08: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.472355] pnp 00:09: [io  0x0061]
[    0.472376] pnp 00:09: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.472389] pnp 00:0a: [io  0x0010-0x001f]
[    0.472391] pnp 00:0a: [io  0x0022-0x003f]
[    0.472392] pnp 00:0a: [io  0x0044-0x005f]
[    0.472394] pnp 00:0a: [io  0x0062-0x0063]
[    0.472395] pnp 00:0a: [io  0x0065-0x006f]
[    0.472396] pnp 00:0a: [io  0x0072-0x007f]
[    0.472398] pnp 00:0a: [io  0x0080]
[    0.472399] pnp 00:0a: [io  0x0084-0x0086]
[    0.472401] pnp 00:0a: [io  0x0088]
[    0.472402] pnp 00:0a: [io  0x008c-0x008e]
[    0.472403] pnp 00:0a: [io  0x0090-0x009f]
[    0.472405] pnp 00:0a: [io  0x00a2-0x00bf]
[    0.472406] pnp 00:0a: [io  0x00e0-0x00ef]
[    0.472408] pnp 00:0a: [io  0x04d0-0x04d1]
[    0.472450] system 00:0a: [io  0x04d0-0x04d1] has been reserved
[    0.472504] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.472510] pnp 00:0b: [io  0x00f0-0x00ff]
[    0.472514] pnp 00:0b: [irq 13]
[    0.472538] pnp 00:0b: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.472580] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.472595] pnp 00:0d: [io  0x0060]
[    0.472596] pnp 00:0d: [io  0x0064]
[    0.472601] pnp 00:0d: [irq 1]
[    0.472631] pnp 00:0d: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.472654] pnp 00:0e: [irq 12]
[    0.472684] pnp 00:0e: Plug and Play ACPI device, IDs PNP0f03 PNP0f13 (active)
[    0.472832] pnp 00:0f: [io  0x03f8-0x03ff]
[    0.472835] pnp 00:0f: [irq 4]
[    0.472837] pnp 00:0f: [dma 0 disabled]
[    0.472886] pnp 00:0f: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.472977] pnp 00:10: [mem 0xfed00000-0xfed003ff]
[    0.473007] pnp 00:10: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.473011] pnp: PnP ACPI: found 17 devices
[    0.473062] ACPI: ACPI bus type pnp unregistered
[    0.479751] PCI: max bus depth: 1 pci_try_num: 2
[    0.479782] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    0.479837] pci 0000:00:02.0:   bridge window [io  0xe000-0xefff]
[    0.479891] pci 0000:00:02.0:   bridge window [mem 0xfd000000-0xfe0fffff]
[    0.479947] pci 0000:00:02.0:   bridge window [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.480024] pci 0000:00:04.0: PCI bridge to [bus 02-02]
[    0.480077] pci 0000:00:04.0:   bridge window [io  0xd000-0xdfff]
[    0.480131] pci 0000:00:04.0:   bridge window [mem 0xfe600000-0xfe6fffff]
[    0.480187] pci 0000:00:05.0: PCI bridge to [bus 03-03]
[    0.480240] pci 0000:00:05.0:   bridge window [mem 0xfe500000-0xfe5fffff]
[    0.480297] pci 0000:00:06.0: PCI bridge to [bus 04-04]
[    0.480350] pci 0000:00:06.0:   bridge window [mem 0xfe400000-0xfe4fffff]
[    0.480406] pci 0000:00:09.0: PCI bridge to [bus 05-05]
[    0.480459] pci 0000:00:09.0:   bridge window [io  0xc000-0xcfff]
[    0.480513] pci 0000:00:09.0:   bridge window [mem 0xfe300000-0xfe3fffff]
[    0.480569] pci 0000:00:14.4: PCI bridge to [bus 06-06]
[    0.480624] pci 0000:00:14.4:   bridge window [mem 0xfe200000-0xfe2fffff]
[    0.480684] pci 0000:00:15.0: PCI bridge to [bus 07-07]
[    0.480739] pci 0000:00:15.0:   bridge window [mem 0xfe100000-0xfe1fffff]
[    0.480811] pci 0000:00:02.0: PCI INT A -> GSI 52 (level, low) -> IRQ 52
[    0.480867] pci 0000:00:02.0: setting latency timer to 64
[    0.480871] pci 0000:00:04.0: PCI INT A -> GSI 52 (level, low) -> IRQ 52
[    0.480926] pci 0000:00:04.0: setting latency timer to 64
[    0.480930] pci 0000:00:05.0: PCI INT A -> GSI 52 (level, low) -> IRQ 52
[    0.480985] pci 0000:00:05.0: setting latency timer to 64
[    0.480992] pci 0000:00:06.0: PCI INT A -> GSI 53 (level, low) -> IRQ 53
[    0.481046] pci 0000:00:06.0: setting latency timer to 64
[    0.481050] pci 0000:00:09.0: PCI INT A -> GSI 53 (level, low) -> IRQ 53
[    0.481105] pci 0000:00:09.0: setting latency timer to 64
[    0.481115] pci 0000:00:15.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.481171] pci 0000:00:15.0: setting latency timer to 64
[    0.481174] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.481176] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.481178] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.481180] pci_bus 0000:00: resource 7 [mem 0x000c8000-0x000dffff]
[    0.481182] pci_bus 0000:00: resource 8 [mem 0xc0000000-0xffffffff]
[    0.481184] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.481186] pci_bus 0000:01: resource 1 [mem 0xfd000000-0xfe0fffff]
[    0.481188] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.481190] pci_bus 0000:02: resource 0 [io  0xd000-0xdfff]
[    0.481192] pci_bus 0000:02: resource 1 [mem 0xfe600000-0xfe6fffff]
[    0.481194] pci_bus 0000:03: resource 1 [mem 0xfe500000-0xfe5fffff]
[    0.481196] pci_bus 0000:04: resource 1 [mem 0xfe400000-0xfe4fffff]
[    0.481199] pci_bus 0000:05: resource 0 [io  0xc000-0xcfff]
[    0.481201] pci_bus 0000:05: resource 1 [mem 0xfe300000-0xfe3fffff]
[    0.481203] pci_bus 0000:06: resource 1 [mem 0xfe200000-0xfe2fffff]
[    0.481205] pci_bus 0000:06: resource 4 [io  0x0000-0x0cf7]
[    0.481207] pci_bus 0000:06: resource 5 [io  0x0d00-0xffff]
[    0.481209] pci_bus 0000:06: resource 6 [mem 0x000a0000-0x000bffff]
[    0.481211] pci_bus 0000:06: resource 7 [mem 0x000c8000-0x000dffff]
[    0.481213] pci_bus 0000:06: resource 8 [mem 0xc0000000-0xffffffff]
[    0.481215] pci_bus 0000:07: resource 1 [mem 0xfe100000-0xfe1fffff]
[    0.481253] NET: Registered protocol family 2
[    0.481585] IP route cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.483565] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.486685] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.487115] TCP: Hash tables configured (established 524288 bind 65536)
[    0.487171] TCP reno registered
[    0.487245] UDP hash table entries: 8192 (order: 6, 262144 bytes)
[    0.487415] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes)
[    0.487665] NET: Registered protocol family 1
[    0.487765] pci 0000:01:00.0: Boot video device
[    0.487793] pci 0000:03:00.0: PCI INT A -> GSI 46 (level, low) -> IRQ 46
[    0.487875] pci 0000:03:00.0: PCI INT A disabled
[    0.487935] pci 0000:04:00.0: PCI INT A -> GSI 51 (level, low) -> IRQ 51
[    0.488042] pci 0000:04:00.0: PCI INT A disabled
[    0.488110] pci 0000:07:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.488210] pci 0000:07:00.0: PCI INT A disabled
[    0.488264] PCI: CLS 64 bytes, default 64
[    0.488572] PCI-DMA: Disabling AGP.
[    0.491165] PCI-DMA: aperture base @ b4000000 size 65536 KB
[    0.491218] PCI-DMA: using GART IOMMU.
[    0.491270] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    0.494202] IBS: LVT offset 1 assigned
[    0.494282] perf: AMD IBS detected (0x0000001f)
[    0.494501] audit: initializing netlink socket (disabled)
[    0.494563] type=2000 audit(1358124549.488:1): initialized
[    0.513824] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.516391] VFS: Disk quotas dquot_6.5.2
[    0.516492] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.517075] fuse init (API version 7.17)
[    0.517237] msgmni has been set to 19962
[    0.517795] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.517969] io scheduler noop registered
[    0.518024] io scheduler deadline registered
[    0.518132] io scheduler cfq registered (default)
[    0.518423] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.518493] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.518654] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.518722] ACPI: Power Button [PWRB]
[    0.518806] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.519884] ACPI: Power Button [PWRF]
[    0.521141] ERST: Table is not found!
[    0.521195] GHES: HEST is not enabled!
[    0.521347] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.541803] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.571366] Freeing initrd memory: 14260k freed
[    0.680540] 00:0f: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.700337] Linux agpgart interface v0.103
[    0.701892] brd: module loaded
[    0.702814] loop: module loaded
[    0.703014] ahci 0000:00:11.0: version 3.0
[    0.703037] ahci 0000:00:11.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.703232] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 6 ports 6 Gbps 0x3f impl SATA mode
[    0.703299] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck led clo pmp pio slum part 
[    0.704174] scsi0 : ahci
[    0.704382] scsi1 : ahci
[    0.704575] scsi2 : ahci
[    0.704781] scsi3 : ahci
[    0.705003] scsi4 : ahci
[    0.705215] scsi5 : ahci
[    0.705336] ata1: SATA max UDMA/133 abar m1024@0xfe704000 port 0xfe704100 irq 19
[    0.705402] ata2: SATA max UDMA/133 abar m1024@0xfe704000 port 0xfe704180 irq 19
[    0.705467] ata3: SATA max UDMA/133 abar m1024@0xfe704000 port 0xfe704200 irq 19
[    0.705532] ata4: SATA max UDMA/133 abar m1024@0xfe704000 port 0xfe704280 irq 19
[    0.705597] ata5: SATA max UDMA/133 abar m1024@0xfe704000 port 0xfe704300 irq 19
[    0.705661] ata6: SATA max UDMA/133 abar m1024@0xfe704000 port 0xfe704380 irq 19
[    0.705833] ahci 0000:02:00.0: PCI INT A -> GSI 44 (level, low) -> IRQ 44
[    0.705961] ahci 0000:02:00.0: irq 72 for MSI/MSI-X
[    0.706012] ahci 0000:02:00.0: AHCI 0001.0000 32 slots 2 ports 6 Gbps 0x3 impl SATA mode
[    0.706110] ahci 0000:02:00.0: flags: 64bit ncq sntf led only pmp fbs pio slum part sxs 
[    0.706189] ahci 0000:02:00.0: setting latency timer to 64
[    0.706498] scsi6 : ahci
[    0.706646] scsi7 : ahci
[    0.706741] ata7: SATA max UDMA/133 abar m2048@0xfe615000 port 0xfe615100 irq 72
[    0.706806] ata8: SATA max UDMA/133 abar m2048@0xfe615000 port 0xfe615180 irq 72
[    0.707095] pata_acpi 0000:05:00.1: PCI INT A -> GSI 48 (level, low) -> IRQ 48
[    0.707204] pata_acpi 0000:05:00.1: setting latency timer to 64
[    0.707218] pata_acpi 0000:05:00.1: PCI INT A disabled
[    0.707592] Fixed MDIO Bus: probed
[    0.707659] tun: Universal TUN/TAP device driver, 1.6
[    0.707711] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.707840] PPP generic driver version 2.4.2
[    0.708049] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.708119] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.708182] uhci_hcd: USB Universal Host Controller Interface driver
[    0.708291] xhci_hcd 0000:03:00.0: PCI INT A -> GSI 46 (level, low) -> IRQ 46
[    0.708370] xhci_hcd 0000:03:00.0: setting latency timer to 64
[    0.708373] xhci_hcd 0000:03:00.0: xHCI Host Controller
[    0.708516] xhci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 1
[    0.708701] xhci_hcd 0000:03:00.0: irq 46, io mem 0xfe500000
[    0.708793] xhci_hcd 0000:03:00.0: irq 73 for MSI/MSI-X
[    0.708798] xhci_hcd 0000:03:00.0: irq 74 for MSI/MSI-X
[    0.708802] xhci_hcd 0000:03:00.0: irq 75 for MSI/MSI-X
[    0.708805] xhci_hcd 0000:03:00.0: irq 76 for MSI/MSI-X
[    0.708809] xhci_hcd 0000:03:00.0: irq 77 for MSI/MSI-X
[    0.708962] xHCI xhci_add_endpoint called for root hub
[    0.708963] xHCI xhci_check_bandwidth called for root hub
[    0.708986] hub 1-0:1.0: USB hub found
[    0.709040] hub 1-0:1.0: 2 ports detected
[    0.709138] xhci_hcd 0000:03:00.0: xHCI Host Controller
[    0.709250] xhci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 2
[    0.712115] xHCI xhci_add_endpoint called for root hub
[    0.712117] xHCI xhci_check_bandwidth called for root hub
[    0.712135] hub 2-0:1.0: USB hub found
[    0.712193] hub 2-0:1.0: 2 ports detected
[    0.776093] xhci_hcd 0000:04:00.0: PCI INT A -> GSI 51 (level, low) -> IRQ 51
[    0.776172] xhci_hcd 0000:04:00.0: setting latency timer to 64
[    0.776174] xhci_hcd 0000:04:00.0: xHCI Host Controller
[    0.776324] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 3
[    0.776504] xhci_hcd 0000:04:00.0: irq 51, io mem 0xfe400000
[    0.776595] xhci_hcd 0000:04:00.0: irq 78 for MSI/MSI-X
[    0.776598] xhci_hcd 0000:04:00.0: irq 79 for MSI/MSI-X
[    0.776601] xhci_hcd 0000:04:00.0: irq 80 for MSI/MSI-X
[    0.776604] xhci_hcd 0000:04:00.0: irq 81 for MSI/MSI-X
[    0.776607] xhci_hcd 0000:04:00.0: irq 82 for MSI/MSI-X
[    0.776763] xHCI xhci_add_endpoint called for root hub
[    0.776765] xHCI xhci_check_bandwidth called for root hub
[    0.776786] hub 3-0:1.0: USB hub found
[    0.776841] hub 3-0:1.0: 2 ports detected
[    0.776938] xhci_hcd 0000:04:00.0: xHCI Host Controller
[    0.777048] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 4
[    0.779953] xHCI xhci_add_endpoint called for root hub
[    0.779954] xHCI xhci_check_bandwidth called for root hub
[    0.779973] hub 4-0:1.0: USB hub found
[    0.780043] hub 4-0:1.0: 2 ports detected
[    0.816113] xhci_hcd 0000:07:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.816196] xhci_hcd 0000:07:00.0: setting latency timer to 64
[    0.816200] xhci_hcd 0000:07:00.0: xHCI Host Controller
[    0.816340] xhci_hcd 0000:07:00.0: new USB bus registered, assigned bus number 5
[    1.097810] xhci_hcd 0000:07:00.0: irq 16, io mem 0xfe100000
[    1.097913] xhci_hcd 0000:07:00.0: irq 83 for MSI/MSI-X
[    1.097916] xhci_hcd 0000:07:00.0: irq 84 for MSI/MSI-X
[    1.097920] xhci_hcd 0000:07:00.0: irq 85 for MSI/MSI-X
[    1.097924] xhci_hcd 0000:07:00.0: irq 86 for MSI/MSI-X
[    1.097929] xhci_hcd 0000:07:00.0: irq 87 for MSI/MSI-X
[    1.098116] xHCI xhci_add_endpoint called for root hub
[    1.098118] xHCI xhci_check_bandwidth called for root hub
[    1.098141] hub 5-0:1.0: USB hub found
[    1.098199] hub 5-0:1.0: 4 ports detected
[    1.098307] xhci_hcd 0000:07:00.0: xHCI Host Controller
[    1.098417] xhci_hcd 0000:07:00.0: new USB bus registered, assigned bus number 6
[    1.101450] xHCI xhci_add_endpoint called for root hub
[    1.101452] xHCI xhci_check_bandwidth called for root hub
[    1.101470] hub 6-0:1.0: USB hub found
[    1.101529] hub 6-0:1.0: 4 ports detected
[    1.168121] usbcore: registered new interface driver libusual
[    1.168213] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.171141] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.171202] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.171447] mousedev: PS/2 mouse device common for all mice
[    1.171659] rtc_cmos 00:08: RTC can wake from S4
[    1.171823] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    1.171900] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.172041] device-mapper: uevent: version 1.0.3
[    1.172178] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.172248] cpuidle: using governor ladder
[    1.172300] cpuidle: using governor menu
[    1.172351] EFI Variables Facility v0.08 2004-May-17
[    1.172569] TCP cubic registered
[    1.172698] NET: Registered protocol family 10
[    1.173122] NET: Registered protocol family 17
[    1.173176] Registering the dns_resolver key type
[    1.173372] PM: Hibernation image not present or could not be loaded.
[    1.173382] registered taskstats version 1
[    1.180063]   Magic number: 13:802:809
[    1.180230] rtc_cmos 00:08: setting system clock to 2013-01-14 00:49:10 UTC (1358124550)
[    1.180333] powernow-k8: Found 1 AMD Athlon(tm) II X4 630 Processor (4 cpu cores) (version 2.20.00)
[    1.180434] powernow-k8:    0 : pstate 0 (2800 MHz)
[    1.180486] powernow-k8:    1 : pstate 1 (2100 MHz)
[    1.180538] powernow-k8:    2 : pstate 2 (1600 MHz)
[    1.180590] powernow-k8:    3 : pstate 3 (800 MHz)
[    1.181242] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.181299] EDD information not available.
[    1.196082] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.196165] ata6: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.196168] ata7: SATA link up 3.0 Gbps (SStatus 123 SControl 330)
[    1.196192] ata8: SATA link up 1.5 Gbps (SStatus 113 SControl 330)
[    1.196358] ata4: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.196441] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.196516] ata5: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.196637] ata7.00: ATA-7: WDC WD400BD-75LRA0, 09.01D09, max UDMA/133
[    1.196702] ata7.00: 78125000 sectors, multi 0: LBA48 
[    1.196771] ata8.00: ATAPI: TSSTcorp CDDVDW SH-222AB, SB00, max UDMA/100
[    1.197302] ata7.00: configured for UDMA/133
[    1.197579] ata8.00: configured for UDMA/100
[    1.200418] ata2.00: ATA-8: WDC WD2002FAEX-007BA0, 05.01D05, max UDMA/133
[    1.200485] ata2.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.200623] ata1.00: ATA-8: WDC WD2002FAEX-007BA0, 05.01D05, max UDMA/133
[    1.200682] ata1.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.200830] ata4.00: ATA-8: WDC WD2002FAEX-007BA0, 05.01D05, max UDMA/133
[    1.200892] ata4.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.200974] ata6.00: ATA-8: WDC WD2002FAEX-007BA0, 05.01D05, max UDMA/133
[    1.201037] ata6.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.201179] ata5.00: ATA-8: WDC WD2002FAEX-007BA0, 05.01D05, max UDMA/133
[    1.201235] ata5.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.204427] ata2.00: configured for UDMA/133
[    1.205575] ata6.00: configured for UDMA/133
[    1.205730] ata1.00: configured for UDMA/133
[    1.205827] ata4.00: configured for UDMA/133
[    1.205987] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2002FAEX-0 05.0 PQ: 0 ANSI: 5
[    1.206158] ata5.00: configured for UDMA/133
[    1.206265] sd 0:0:0:0: [sda] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    1.206267] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.206581] scsi 1:0:0:0: Direct-Access     ATA      WDC WD2002FAEX-0 05.0 PQ: 0 ANSI: 5
[    1.206706] sd 0:0:0:0: [sda] Write Protect is off
[    1.206764] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.206846] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.206852] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    1.206857] sd 1:0:0:0: [sdb] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    1.206965] sd 1:0:0:0: [sdb] Write Protect is off
[    1.206968] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.207005] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.212951]  sda:
[    1.213598] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.227433]  sdb: unknown partition table
[    1.228098] sd 1:0:0:0: [sdb] Attached SCSI disk
[    1.230296] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.412766] usb 6-4: new SuperSpeed USB device number 2 using xhci_hcd
[    1.434879] Initializing USB Mass Storage driver...
[    1.435177] scsi8 : usb-storage 6-4:1.0
[    1.435305] usbcore: registered new interface driver usb-storage
[    1.435359] USB Mass Storage support registered.
[    1.492055] Refined TSC clocksource calibration: 2812.383 MHz.
[    1.492114] Switching to clocksource tsc
[    1.588045] ata3: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.592603] ata3.00: ATA-8: WDC WD2002FAEX-007BA0, 05.01D05, max UDMA/133
[    1.592661] ata3.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.596604] ata3.00: configured for UDMA/133
[    1.596852] scsi 2:0:0:0: Direct-Access     ATA      WDC WD2002FAEX-0 05.0 PQ: 0 ANSI: 5
[    1.597104] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    1.597144] sd 2:0:0:0: [sdc] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    1.597330] sd 2:0:0:0: [sdc] Write Protect is off
[    1.597387] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    1.597420] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.597429] scsi 3:0:0:0: Direct-Access     ATA      WDC WD2002FAEX-0 05.0 PQ: 0 ANSI: 5
[    1.597637] sd 3:0:0:0: [sdd] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    1.597644] sd 3:0:0:0: Attached scsi generic sg3 type 0
[    1.597764] scsi 4:0:0:0: Direct-Access     ATA      WDC WD2002FAEX-0 05.0 PQ: 0 ANSI: 5
[    1.597835] sd 3:0:0:0: [sdd] Write Protect is off
[    1.597889] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    1.597957] sd 4:0:0:0: Attached scsi generic sg4 type 0
[    1.597964] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.598110] sd 4:0:0:0: [sde] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    1.598247] scsi 5:0:0:0: Direct-Access     ATA      WDC WD2002FAEX-0 05.0 PQ: 0 ANSI: 5
[    1.598301] sd 4:0:0:0: [sde] Write Protect is off
[    1.598304] sd 4:0:0:0: [sde] Mode Sense: 00 3a 00 00
[    1.598330] sd 4:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.598565] sd 5:0:0:0: [sdf] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    1.598569] sd 5:0:0:0: Attached scsi generic sg5 type 0
[    1.598805] scsi 6:0:0:0: Direct-Access     ATA      WDC WD400BD-75LR 09.0 PQ: 0 ANSI: 5
[    1.598984] sd 5:0:0:0: [sdf] Write Protect is off
[    1.599041] sd 5:0:0:0: [sdf] Mode Sense: 00 3a 00 00
[    1.599077] sd 6:0:0:0: [sdg] 78125000 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    1.599085] sd 6:0:0:0: Attached scsi generic sg6 type 0
[    1.599100] sd 5:0:0:0: [sdf] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.599557] sd 6:0:0:0: [sdg] Write Protect is off
[    1.599616] sd 6:0:0:0: [sdg] Mode Sense: 00 3a 00 00
[    1.599724] sd 6:0:0:0: [sdg] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.599900] scsi 7:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-222AB  SB00 PQ: 0 ANSI: 5
[    1.602542] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.602610] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.602802] sr 7:0:0:0: Attached scsi CD-ROM sr0
[    1.602890] sr 7:0:0:0: Attached scsi generic sg7 type 5
[    1.606403]  sdd: unknown partition table
[    1.607046] sd 3:0:0:0: [sdd] Attached SCSI disk
[    1.615809]  sde: unknown partition table
[    1.616462] sd 4:0:0:0: [sde] Attached SCSI disk
[    1.617779]  sdc: unknown partition table
[    1.618420] sd 2:0:0:0: [sdc] Attached SCSI disk
[    1.622624]  sdf:
[    1.623227] sd 5:0:0:0: [sdf] Attached SCSI disk
[    1.649600]  sdg: sdg1 sdg2 < sdg5 >
[    1.650368] sd 6:0:0:0: [sdg] Attached SCSI disk
[    1.651637] Freeing unused kernel memory: 924k freed
[    1.651891] Write protecting the kernel read-only data: 12288k
[    1.656294] Freeing unused kernel memory: 1604k freed
[    1.659930] Freeing unused kernel memory: 1196k freed
[    1.679733] udevd[115]: starting version 175
[    1.686246] md: linear personality registered for level -1
[    1.692184] md: multipath personality registered for level -4
[    1.695186] md: raid0 personality registered for level 0
[    1.703790] md: raid1 personality registered for level 1
[    1.710072] async_tx: api initialized (async)
[    1.716586] firewire_ohci 0000:05:00.0: PCI INT A -> GSI 48 (level, low) -> IRQ 48
[    1.716658] firewire_ohci 0000:05:00.0: setting latency timer to 64
[    1.742812] tg3.c:v3.121 (November 2, 2011)
[    1.742895] tg3 0000:06:05.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.746993] md: bind<sda>
[    1.758126] FDC 0 is a post-1991 82077
[    1.760507] md: bind<sdb>
[    1.762796] md: bind<sdd>
[    1.765217] md: bind<sde>
[    1.767624] md: bind<sdf>
[    1.772570] md: bind<sdc>
[    1.776019] raid6: int64x1   2415 MB/s
[    1.780092] firewire_ohci: Added fw-ohci device 0000:05:00.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x11
[    1.780244] pata_via 0000:05:00.1: version 0.3.4
[    1.780261] pata_via 0000:05:00.1: PCI INT A -> GSI 48 (level, low) -> IRQ 48
[    1.780364] pata_via 0000:05:00.1: setting latency timer to 64
[    1.780674] scsi9 : pata_via
[    1.781052] scsi10 : pata_via
[    1.781268] ata9: PATA max UDMA/133 cmd 0xc140 ctl 0xc130 bmdma 0xc100 irq 48
[    1.781324] ata10: PATA max UDMA/133 cmd 0xc120 ctl 0xc110 bmdma 0xc108 irq 48
[    1.844019] raid6: int64x2   3486 MB/s
[    1.912039] raid6: int64x4   2547 MB/s
[    1.980020] raid6: int64x8   2230 MB/s
[    2.048023] raid6: sse2x1    3855 MB/s
[    2.116017] raid6: sse2x2    6382 MB/s
[    2.184030] raid6: sse2x4    7045 MB/s
[    2.184081] raid6: using algorithm sse2x4 (7045 MB/s)
[    2.184639] xor: automatically using best checksumming function: generic_sse
[    2.204022]    generic_sse: 11447.000 MB/sec
[    2.204075] xor: using function: generic_sse (11447.000 MB/sec)
[    2.204999] md: raid6 personality registered for level 6
[    2.205055] md: raid5 personality registered for level 5
[    2.205107] md: raid4 personality registered for level 4
[    2.209987] md: raid10 personality registered for level 10
[    2.275553] bio: create slab <bio-1> at 1
[    2.275637] md/raid:md0: device sdc operational as raid disk 2
[    2.275690] md/raid:md0: device sde operational as raid disk 4
[    2.275744] md/raid:md0: device sdd operational as raid disk 3
[    2.275797] md/raid:md0: device sdb operational as raid disk 1
[    2.275850] md/raid:md0: device sda operational as raid disk 0
[    2.276300] md/raid:md0: allocated 6384kB
[    2.276432] md/raid:md0: raid level 5 active with 5 out of 6 devices, algorithm 2
[    2.276502] RAID conf printout:
[    2.276504]  --- level:5 rd:6 wd:5
[    2.276508]  disk 0, o:1, dev:sda
[    2.276511]  disk 1, o:1, dev:sdb
[    2.276514]  disk 2, o:1, dev:sdc
[    2.276517]  disk 3, o:1, dev:sdd
[    2.276519]  disk 4, o:1, dev:sde
[    2.276521]  disk 5, o:1, dev:sdf
[    2.276582] md0: detected capacity change from 0 to 10001322803200
[    2.276677] RAID conf printout:
[    2.276681]  --- level:5 rd:6 wd:5
[    2.276683]  disk 0, o:1, dev:sda
[    2.276685]  disk 1, o:1, dev:sdb
[    2.276686]  disk 2, o:1, dev:sdc
[    2.276688]  disk 3, o:1, dev:sdd
[    2.276689]  disk 4, o:1, dev:sde
[    2.276690]  disk 5, o:1, dev:sdf
[    2.276691] RAID conf printout:
[    2.276693]  --- level:5 rd:6 wd:5
[    2.276694]  disk 0, o:1, dev:sda
[    2.276695]  disk 1, o:1, dev:sdb
[    2.276696]  disk 2, o:1, dev:sdc
[    2.276697]  disk 3, o:1, dev:sdd
[    2.276698]  disk 4, o:1, dev:sde
[    2.276699]  disk 5, o:1, dev:sdf
[    2.276765] md: recovery of RAID array md0
[    2.276822] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
[    2.276876] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for recovery.
[    2.276961] md: using 128k window, over a total of 1953383360k.
[    2.277015] md: resuming recovery of md0 from checkpoint.
[    2.280112] firewire_core: created device fw0: GUID 008f13003be30d00, S400
[    2.328579]  md0: unknown partition table
[    2.433862] scsi 8:0:0:0: Direct-Access     ST3000DM 001-9YN166            PQ: 0 ANSI: 5
[    2.434526] sd 8:0:0:0: Attached scsi generic sg8 type 0
[    2.434755] sd 8:0:0:0: [sdh] Very big device. Trying to use READ CAPACITY(16).
[    2.435466] sd 8:0:0:0: [sdh] 5860533168 512-byte logical blocks: (3.00 TB/2.72 TiB)
[    2.437425] sd 8:0:0:0: [sdh] Write Protect is off
[    2.437485] sd 8:0:0:0: [sdh] Mode Sense: 28 00 00 00
[    2.438823] sd 8:0:0:0: [sdh] No Caching mode page present
[    2.438881] sd 8:0:0:0: [sdh] Assuming drive cache: write through
[    2.439408] sd 8:0:0:0: [sdh] Very big device. Trying to use READ CAPACITY(16).
[    2.442543] sd 8:0:0:0: [sdh] No Caching mode page present
[    2.442600] sd 8:0:0:0: [sdh] Assuming drive cache: write through
[    2.468069]  sdh: sdh1 sdh2
[    2.468711] sd 8:0:0:0: [sdh] Very big device. Trying to use READ CAPACITY(16).
[    2.472202] sd 8:0:0:0: [sdh] No Caching mode page present
[    2.472263] sd 8:0:0:0: [sdh] Assuming drive cache: write through
[    2.472317] sd 8:0:0:0: [sdh] Attached SCSI disk
[    3.236873] tg3 0000:06:05.0: eth0: Tigon3 [partno(BCM95700A6) rev 7102] (PCI:33MHz:32-bit) MAC address 00:04:76:aa:a7:3d
[    3.236945] tg3 0000:06:05.0: eth0: attached PHY is 5401 (10/100/1000Base-T Ethernet) (WireSpeed[0], EEE[0])
[    3.237012] tg3 0000:06:05.0: eth0: RXcsums[1] LinkChgREG[1] MIirq[1] ASF[0] TSOcap[0]
[    3.237077] tg3 0000:06:05.0: eth0: dma_rwctrl[76ff000f] dma_mask[64-bit]
[    3.611154] ata6.00: exception Emask 0x10 SAct 0xff SErr 0x400000 action 0x6 frozen
[    3.611300] ata6.00: irq_stat 0x08000000, interface fatal error
[    3.611390] ata6: SError: { Handshk }
[    3.611485] ata6.00: failed command: WRITE FPDMA QUEUED
[    3.611579] ata6.00: cmd 61/08:00:c8:2a:ba/00:00:c9:00:00/40 tag 0 ncq 4096 out
[    3.611580]          res 40/00:1c:c0:2a:ba/00:00:c9:00:00/40 Emask 0x10 (ATA bus error)
[    3.611768] ata6.00: status: { DRDY }
[    3.611894] ata6.00: failed command: WRITE FPDMA QUEUED
[    3.611973] ata6.00: cmd 61/08:08:b0:28:ba/02:00:c9:00:00/40 tag 1 ncq 266240 out
[    3.611974]          res 40/00:1c:c0:2a:ba/00:00:c9:00:00/40 Emask 0x10 (ATA bus error)
[    3.612215] ata6.00: status: { DRDY }
[    3.612327] ata6.00: failed command: WRITE FPDMA QUEUED
[    3.612426] ata6.00: cmd 61/08:10:b8:2a:ba/00:00:c9:00:00/40 tag 2 ncq 4096 out
[    3.612427]          res 40/00:1c:c0:2a:ba/00:00:c9:00:00/40 Emask 0x10 (ATA bus error)
[    3.612744] ata6.00: status: { DRDY }
[    3.612829] ata6.00: failed command: WRITE FPDMA QUEUED
[    3.612968] ata6.00: cmd 61/08:18:c0:2a:ba/00:00:c9:00:00/40 tag 3 ncq 4096 out
[    3.612969]          res 40/00:1c:c0:2a:ba/00:00:c9:00:00/40 Emask 0x10 (ATA bus error)
[    3.613228] ata6.00: status: { DRDY }
[    3.613307] ata6.00: failed command: WRITE FPDMA QUEUED
[    3.613417] ata6.00: cmd 61/08:20:d0:2a:ba/00:00:c9:00:00/40 tag 4 ncq 4096 out
[    3.613418]          res 40/00:1c:c0:2a:ba/00:00:c9:00:00/40 Emask 0x10 (ATA bus error)
[    3.613613] ata6.00: status: { DRDY }
[    3.613750] ata6.00: failed command: WRITE FPDMA QUEUED
[    3.613924] ata6.00: cmd 61/08:28:d8:2a:ba/00:00:c9:00:00/40 tag 5 ncq 4096 out
[    3.613925]          res 40/00:1c:c0:2a:ba/00:00:c9:00:00/40 Emask 0x10 (ATA bus error)
[    3.614251] ata6.00: status: { DRDY }
[    3.614378] ata6.00: failed command: WRITE FPDMA QUEUED
[    3.614506] ata6.00: cmd 61/08:30:e0:2a:ba/00:00:c9:00:00/40 tag 6 ncq 4096 out
[    3.614507]          res 40/00:1c:c0:2a:ba/00:00:c9:00:00/40 Emask 0x10 (ATA bus error)
[    3.614755] ata6.00: status: { DRDY }
[    3.614864] ata6.00: failed command: WRITE FPDMA QUEUED
[    3.614946] ata6.00: cmd 61/08:38:e8:2a:ba/00:00:c9:00:00/40 tag 7 ncq 4096 out
[    3.614947]          res 40/00:1c:c0:2a:ba/00:00:c9:00:00/40 Emask 0x10 (ATA bus error)
[    3.615136] ata6.00: status: { DRDY }
[    3.615210] ata6: hard resetting link
[    4.104041] ata6: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    4.114387] ata6.00: configured for UDMA/133
[    4.114456] ata6: EH complete
[    8.443460] ata6.00: exception Emask 0x10 SAct 0x3 SErr 0x400000 action 0x6 frozen
[    8.443543] ata6.00: irq_stat 0x08000000, interface fatal error
[    8.443614] ata6: SError: { Handshk }
[    8.443689] ata6.00: failed command: WRITE FPDMA QUEUED
[    8.443759] ata6.00: cmd 61/d8:00:f0:65:c3/00:00:c9:00:00/40 tag 0 ncq 110592 out
[    8.443760]          res 40/00:04:f0:65:c3/00:00:c9:00:00/40 Emask 0x10 (ATA bus error)
[    8.443933] ata6.00: status: { DRDY }
[    8.443999] ata6.00: failed command: WRITE FPDMA QUEUED
[    8.444089] ata6.00: cmd 61/a8:08:c8:66:c3/00:00:c9:00:00/40 tag 1 ncq 86016 out
[    8.444090]          res 40/00:04:f0:65:c3/00:00:c9:00:00/40 Emask 0x10 (ATA bus error)
[    8.444279] ata6.00: status: { DRDY }
[    8.444360] ata6: hard resetting link
[    9.048040] ata6: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    9.057846] ata6.00: configured for UDMA/133
[    9.057911] ata6: EH complete
[   10.366684] ata6.00: exception Emask 0x10 SAct 0x7ff SErr 0x400000 action 0x6 frozen
[   10.366752] ata6.00: irq_stat 0x08000000, interface fatal error
[   10.366806] ata6: SError: { Handshk }
[   10.366858] ata6.00: failed command: WRITE FPDMA QUEUED
[   10.366913] ata6.00: cmd 61/f8:00:88:ac:c5/02:00:c9:00:00/40 tag 0 ncq 389120 out
[   10.366914]          res 40/00:44:b8:af:c5/00:00:c9:00:00/40 Emask 0x10 (ATA bus error)
[   10.367041] ata6.00: status: { DRDY }
[   10.367092] ata6.00: failed command: WRITE FPDMA QUEUED
[   10.367147] ata6.00: cmd 61/08:08:80:af:c5/00:00:c9:00:00/40 tag 1 ncq 4096 out
[   10.367147]          res 40/00:44:b8:af:c5/00:00:c9:00:00/40 Emask 0x10 (ATA bus error)
[   10.367274] ata6.00: status: { DRDY }
[   10.367325] ata6.00: failed command: WRITE FPDMA QUEUED
[   10.367379] ata6.00: cmd 61/08:10:88:af:c5/00:00:c9:00:00/40 tag 2 ncq 4096 out
[   10.367380]          res 40/00:44:b8:af:c5/00:00:c9:00:00/40 Emask 0x10 (ATA bus error)
[   10.367507] ata6.00: status: { DRDY }
[   10.367557] ata6.00: failed command: WRITE FPDMA QUEUED
[   10.367612] ata6.00: cmd 61/08:18:90:af:c5/00:00:c9:00:00/40 tag 3 ncq 4096 out
[   10.367613]          res 40/00:44:b8:af:c5/00:00:c9:00:00/40 Emask 0x10 (ATA bus error)
[   10.367739] ata6.00: status: { DRDY }
[   10.367790] ata6.00: failed command: WRITE FPDMA QUEUED
[   10.367845] ata6.00: cmd 61/08:20:98:af:c5/00:00:c9:00:00/40 tag 4 ncq 4096 out
[   10.367845]          res 40/00:44:b8:af:c5/00:00:c9:00:00/40 Emask 0x10 (ATA bus error)
[   10.367972] ata6.00: status: { DRDY }
[   10.368033] ata6.00: failed command: WRITE FPDMA QUEUED
[   10.368088] ata6.00: cmd 61/08:28:a0:af:c5/00:00:c9:00:00/40 tag 5 ncq 4096 out
[   10.368089]          res 40/00:44:b8:af:c5/00:00:c9:00:00/40 Emask 0x10 (ATA bus error)
[   10.368215] ata6.00: status: { DRDY }
[   10.368266] ata6.00: failed command: WRITE FPDMA QUEUED
[   10.368320] ata6.00: cmd 61/08:30:a8:af:c5/00:00:c9:00:00/40 tag 6 ncq 4096 out
[   10.368321]          res 40/00:44:b8:af:c5/00:00:c9:00:00/40 Emask 0x10 (ATA bus error)
[   10.368448] ata6.00: status: { DRDY }
[   10.368499] ata6.00: failed command: WRITE FPDMA QUEUED
[   10.368553] ata6.00: cmd 61/08:38:b0:af:c5/00:00:c9:00:00/40 tag 7 ncq 4096 out
[   10.368554]          res 40/00:44:b8:af:c5/00:00:c9:00:00/40 Emask 0x10 (ATA bus error)
[   10.368680] ata6.00: status: { DRDY }
[   10.368731] ata6.00: failed command: WRITE FPDMA QUEUED
[   10.368786] ata6.00: cmd 61/08:40:b8:af:c5/00:00:c9:00:00/40 tag 8 ncq 4096 out
[   10.368787]          res 40/00:44:b8:af:c5/00:00:c9:00:00/40 Emask 0x10 (ATA bus error)
[   10.368913] ata6.00: status: { DRDY }
[   10.368964] ata6.00: failed command: WRITE FPDMA QUEUED
[   10.369018] ata6.00: cmd 61/00:48:c0:af:c5/04:00:c9:00:00/40 tag 9 ncq 524288 out
[   10.369019]          res 40/00:44:b8:af:c5/00:00:c9:00:00/40 Emask 0x10 (ATA bus error)
[   10.369146] ata6.00: status: { DRDY }
[   10.369197] ata6.00: failed command: WRITE FPDMA QUEUED
[   10.369251] ata6.00: cmd 61/a0:50:c0:b3:c5/00:00:c9:00:00/40 tag 10 ncq 81920 out
[   10.369252]          res 40/00:44:b8:af:c5/00:00:c9:00:00/40 Emask 0x10 (ATA bus error)
[   10.369378] ata6.00: status: { DRDY }
[   10.369431] ata6: hard resetting link
[   10.860055] ata6: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[   10.870226] ata6.00: configured for UDMA/133
[   10.870298] ata6: EH complete
[   12.793540] ata6: limiting SATA link speed to 3.0 Gbps
[   12.793604] ata6.00: exception Emask 0x10 SAct 0x1f SErr 0x400000 action 0x6 frozen
[   12.793674] ata6.00: irq_stat 0x08000000, interface fatal error
[   12.793731] ata6: SError: { Handshk }
[   12.793785] ata6.00: failed command: WRITE FPDMA QUEUED
[   12.793843] ata6.00: cmd 61/30:00:80:fe:c7/01:00:c9:00:00/40 tag 0 ncq 155648 out
[   12.793844]          res 40/00:0c:b0:ff:c7/00:00:c9:00:00/40 Emask 0x10 (ATA bus error)
[   12.793977] ata6.00: status: { DRDY }
[   12.794031] ata6.00: failed command: WRITE FPDMA QUEUED
[   12.794089] ata6.00: cmd 61/88:08:b0:ff:c7/00:00:c9:00:00/40 tag 1 ncq 69632 out
[   12.794090]          res 40/00:0c:b0:ff:c7/00:00:c9:00:00/40 Emask 0x10 (ATA bus error)
[   12.794228] ata6.00: status: { DRDY }
[   12.794280] ata6.00: failed command: WRITE FPDMA QUEUED
[   12.794338] ata6.00: cmd 61/f8:10:38:00:c8/00:00:c9:00:00/40 tag 2 ncq 126976 out
[   12.794339]          res 40/00:0c:b0:ff:c7/00:00:c9:00:00/40 Emask 0x10 (ATA bus error)
[   12.794472] ata6.00: status: { DRDY }
[   12.794524] ata6.00: failed command: WRITE FPDMA QUEUED
[   12.794581] ata6.00: cmd 61/08:18:30:01:c8/00:00:c9:00:00/40 tag 3 ncq 4096 out
[   12.794582]          res 40/00:0c:b0:ff:c7/00:00:c9:00:00/40 Emask 0x10 (ATA bus error)
[   12.794713] ata6.00: status: { DRDY }
[   12.795781] ata6.00: failed command: WRITE FPDMA QUEUED
[   12.795836] ata6.00: cmd 61/08:20:38:01:c8/00:00:c9:00:00/40 tag 4 ncq 4096 out
[   12.795837]          res 40/00:0c:b0:ff:c7/00:00:c9:00:00/40 Emask 0x10 (ATA bus error)
[   12.795964] ata6.00: status: { DRDY }
[   12.796036] ata6: hard resetting link
[   13.288041] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
[   13.297684] ata6.00: configured for UDMA/133
[   13.297752] ata6: EH complete
[  145.595922] EXT4-fs (sdg1): mounted filesystem with ordered data mode. Opts: (null)
[  148.666934] Adding 10479612k swap on /dev/sdg5.  Priority:-1 extents:1 across:10479612k 
[  149.098192] EXT4-fs (sdg1): re-mounted. Opts: errors=remount-ro
[  150.146431] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  150.469699] udevd[458]: starting version 175
[  152.513788] lp: driver loaded but no devices found
[  152.585348] MCE: In-kernel MCE decoding enabled.
[  153.255848] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[  153.671022] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input3
[  153.776821] type=1400 audit(1358124703.094:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=628 comm="apparmor_parser"
[  153.777303] type=1400 audit(1358124703.094:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=628 comm="apparmor_parser"
[  153.777640] type=1400 audit(1358124703.094:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=628 comm="apparmor_parser"
[  153.854913] EDAC MC: Ver: 2.1.0
[  153.871084] AMD64 EDAC driver v3.4.0
[  153.871183] EDAC amd64: DRAM ECC disabled.
[  153.871207] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[  153.871208]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[  153.871209]  (Note that use of the override may cause unknown side effects.)
[  153.993264] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
[  153.993426] SP5100 TCO timer: mmio address 0xbafe00 already in use
[  154.005494] wmi: Mapper loaded
[  155.019710] [drm] Initialized drm 1.1.0 20060810
[  155.123187] snd_hda_intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  155.545636] input: HDA ATI SB Line as /devices/pci0000:00/0000:00:14.2/sound/card0/input4
[  155.545740] input: HDA ATI SB Front Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input5
[  155.545812] input: HDA ATI SB Rear Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input6
[  155.545884] input: HDA ATI SB Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input7
[  155.545957] input: HDA ATI SB Line-Out Side as /devices/pci0000:00/0000:00:14.2/sound/card0/input8
[  155.546026] input: HDA ATI SB Line-Out CLFE as /devices/pci0000:00/0000:00:14.2/sound/card0/input9
[  155.546096] input: HDA ATI SB Line-Out Surround as /devices/pci0000:00/0000:00:14.2/sound/card0/input10
[  155.546174] input: HDA ATI SB Line-Out Front as /devices/pci0000:00/0000:00:14.2/sound/card0/input11
[  155.546452] snd_hda_intel 0000:01:00.1: PCI INT B -> GSI 25 (level, low) -> IRQ 25
[  155.546458] hda_intel: Disabling MSI
[  155.546536] snd_hda_intel 0000:01:00.1: setting latency timer to 64
[  156.388045] HDMI status: Codec=0 Pin=5 Presence_Detect=0 ELD_Valid=0
[  156.412038] HDMI status: Codec=1 Pin=5 Presence_Detect=0 ELD_Valid=0
[  156.436037] HDMI status: Codec=2 Pin=5 Presence_Detect=0 ELD_Valid=0
[  156.460039] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
[  156.460129] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input12
[  156.460305] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input13
[  156.460402] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input14
[  156.460481] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input15
[  156.695463] nouveau 0000:01:00.0: PCI INT A -> GSI 24 (level, low) -> IRQ 24
[  156.695470] nouveau 0000:01:00.0: setting latency timer to 64
[  156.696843] [drm] nouveau 0000:01:00.0: Detected an NV50 generation card (0x0a8180b1)
[  156.699774] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PRAMIN
[  156.777641] [drm] nouveau 0000:01:00.0: ... appears to be valid
[  156.777644] [drm] nouveau 0000:01:00.0: BIT BIOS found
[  156.777647] [drm] nouveau 0000:01:00.0: Bios version 70.18.76.00
[  156.777650] [drm] nouveau 0000:01:00.0: TMDS table version 2.0
[  156.777652] [drm] nouveau 0000:01:00.0: Found Display Configuration Block version 4.0
[  156.777655] [drm] nouveau 0000:01:00.0: Raw DCB entry 0: 01000302 00020030
[  156.777657] [drm] nouveau 0000:01:00.0: Raw DCB entry 1: 02000300 00000000
[  156.777659] [drm] nouveau 0000:01:00.0: Raw DCB entry 2: 02011362 00020010
[  156.777661] [drm] nouveau 0000:01:00.0: Raw DCB entry 3: 01022310 00000000
[  156.777663] [drm] nouveau 0000:01:00.0: DCB connector table: VHER 0x40 5 16 4
[  156.777665] [drm] nouveau 0000:01:00.0:   0: 0x00001030: type 0x30 idx 0 tag 0x07
[  156.777667] [drm] nouveau 0000:01:00.0:   1: 0x00002161: type 0x61 idx 1 tag 0x08
[  156.777669] [drm] nouveau 0000:01:00.0:   2: 0x00000200: type 0x00 idx 2 tag 0xff
[  156.777674] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 0 at offset 0x6B0E
[  156.838209] [drm] nouveau 0000:01:00.0: 0x6DE3: Condition still not met after 20ms, skipping following opcodes
[  156.858057] [drm] nouveau 0000:01:00.0: 0x6DE7: Condition still not met after 20ms, skipping following opcodes
[  156.858090] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 1 at offset 0x6FC1
[  156.865824] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 2 at offset 0x7E8C
[  156.865831] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 3 at offset 0x7EA5
[  156.908353] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 4 at offset 0x7F8C
[  156.908355] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table at offset 0x7FF1
[  156.928201] [drm] nouveau 0000:01:00.0: 0x6982: Condition still not met after 20ms, skipping following opcodes
[  157.408048] [drm] nouveau 0000:01:00.0: 3 available performance level(s)
[  157.408052] [drm] nouveau 0000:01:00.0: 0: core 135MHz shader 270MHz memory 135MHz timing 0 voltage 1050mV
[  157.408055] [drm] nouveau 0000:01:00.0: 1: core 405MHz shader 810MHz memory 405MHz timing 1 voltage 1050mV
[  157.408059] [drm] nouveau 0000:01:00.0: 3: core 520MHz shader 1238MHz memory 600MHz timing 4 voltage 1050mV
[  157.408082] [drm] nouveau 0000:01:00.0: c: core 405MHz shader 810MHz memory 405MHz voltage 1050mV
[  157.408131] [drm] nouveau 0000:01:00.0: memory controller reports 512MiB VRAM
[  157.408133] [drm] nouveau 0000:01:00.0: we calculated 1024MiB VRAM
[  157.409376] [TTM] Zone  kernel: Available graphics memory: 5119372 kiB.
[  157.409378] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB.
[  157.409379] [TTM] Initializing pool allocator.
[  157.409391] [drm] nouveau 0000:01:00.0: Detected 512MiB VRAM
[  157.410226] [drm] nouveau 0000:01:00.0: 512 MiB GART (aperture)
[  157.447620] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[  157.447623] [drm] No driver support for vblank timestamp query.
[  157.561062] [drm] nouveau 0000:01:00.0: allocated 1024x768 fb: 0x310000, bo ffff8802a9e3dc00
[  157.561155] fbcon: nouveaufb (fb0) is primary device
[  157.618942] Console: switching to colour frame buffer device 128x48
[  157.620118] fb0: nouveaufb frame buffer device
[  157.620119] drm: registered panic notifier
[  157.620125] [drm] Initialized nouveau 0.0.16 20090420 for 0000:01:00.0 on minor 0
[  157.856442] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  160.192758] init: udev-fallback-graphics main process (809) terminated with status 1
[  161.852973] tg3 0000:06:05.0: eth0: Link is up at 1000 Mbps, full duplex
[  161.852977] tg3 0000:06:05.0: eth0: Flow control is off for TX and off for RX
[  161.854908] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  163.521092] init: failsafe main process (746) killed by TERM signal
[  164.416945] type=1400 audit(1358124713.734:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=963 comm="apparmor_parser"
[  164.417387] type=1400 audit(1358124713.734:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=963 comm="apparmor_parser"
[  164.417611] type=1400 audit(1358124713.734:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=963 comm="apparmor_parser"
[  164.611688] type=1400 audit(1358124713.926:8): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=965 comm="apparmor_parser"
[  172.280023] eth0: no IPv6 routers present
[  928.320947] md: md0: recovery done.
[  928.377815] md0: detected capacity change from 10001322803200 to 0
[  928.377828] md: md0 stopped.
[  928.377840] md: unbind<sdc>
[  928.400173] md: export_rdev(sdc)
[  928.400357] md: unbind<sdf>
[  928.436131] md: export_rdev(sdf)
[  928.436219] md: unbind<sde>
[  928.472144] md: export_rdev(sde)
[  928.472324] md: unbind<sdd>
[  928.472433] md: export_rdev(sdd)
[  928.472637] md: unbind<sdb>
[  928.480136] md: export_rdev(sdb)
[  928.480313] md: unbind<sda>
[  928.488139] md: export_rdev(sda)
[ 2427.034206] init: tty1 main process ended, respawning
[12272.697616] md: bind<sda1>
[12272.697925] md: bind<sdb1>
[12272.698132] md: bind<sdc1>
[12272.698324] md: bind<sdd1>
[12272.698492] md: bind<sde1>
[12272.698666] md: bind<sdf1>
[12272.705344] md/raid:md0: device sde1 operational as raid disk 4
[12272.705354] md/raid:md0: device sdd1 operational as raid disk 3
[12272.705360] md/raid:md0: device sdc1 operational as raid disk 2
[12272.705366] md/raid:md0: device sdb1 operational as raid disk 1
[12272.705372] md/raid:md0: device sda1 operational as raid disk 0
[12272.706511] md/raid:md0: allocated 6384kB
[12272.706750] md/raid:md0: raid level 5 active with 5 out of 6 devices, algorithm 2
[12272.706791] RAID conf printout:
[12272.706795]  --- level:5 rd:6 wd:5
[12272.706801]  disk 0, o:1, dev:sda1
[12272.706805]  disk 1, o:1, dev:sdb1
[12272.706810]  disk 2, o:1, dev:sdc1
[12272.706814]  disk 3, o:1, dev:sdd1
[12272.706818]  disk 4, o:1, dev:sde1
[12272.706912] md0: detected capacity change from 0 to 10001316904960
[12272.706983] RAID conf printout:
[12272.706994]  --- level:5 rd:6 wd:5
[12272.707002]  disk 0, o:1, dev:sda1
[12272.707008]  disk 1, o:1, dev:sdb1
[12272.707013]  disk 2, o:1, dev:sdc1
[12272.707018]  disk 3, o:1, dev:sdd1
[12272.707022]  disk 4, o:1, dev:sde1
[12272.707026]  disk 5, o:1, dev:sdf1
[12272.707577] md: recovery of RAID array md0
[12272.707585] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
[12272.707592] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for recovery.
[12272.707612] md: using 128k window, over a total of 1953382208k.
[12272.724309]  md0: unknown partition table
[18960.216727] init: smbd main process (771) killed by TERM signal
[55096.694568] md: md0: recovery done.
[55096.743151] RAID conf printout:
[55096.743157]  --- level:5 rd:6 wd:6
[55096.743160]  disk 0, o:1, dev:sda1
[55096.743163]  disk 1, o:1, dev:sdb1
[55096.743166]  disk 2, o:1, dev:sdc1
[55096.743168]  disk 3, o:1, dev:sdd1
[55096.743170]  disk 4, o:1, dev:sde1
[55096.743172]  disk 5, o:1, dev:sdf1
[67070.359951] EXT4-fs (md0): mounted filesystem with ordered data mode. Opts: errors=continue
[71584.532851] init: smbd main process (25266) killed by TERM signal
[73012.152460] init: smbd main process (1005) killed by TERM signal
[75022.878220] init: smbd main process (1301) killed by TERM signal
[75560.444314] init: smbd main process (1674) killed by TERM signal
[76405.772690] init: smbd main process (1842) killed by TERM signal
[76633.022605] init: smbd main process (2082) killed by TERM signal
[77098.286325] init: smbd main process (2205) killed by TERM signal
[77658.152868] init: smbd main process (2335) killed by TERM signal
[77982.917061] init: smbd main process (2526) killed by TERM signal
[89578.148743] init: smbd main process (2699) killed by TERM signal
[91092.297113] init: smbd main process (4701) killed by TERM signal
[94124.923728] init: smbd main process (5341) killed by TERM signal
[94448.947205] init: smbd main process (5821) killed by TERM signal
[95555.744484] init: smbd main process (5936) killed by TERM signal
[100002.391961] ip_tables: (C) 2000-2006 Netfilter Core Team

```

---

