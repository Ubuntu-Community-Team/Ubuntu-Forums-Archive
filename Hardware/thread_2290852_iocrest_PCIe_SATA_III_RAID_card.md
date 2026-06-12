---
title: "iocrest PCIe SATA III RAID card"
date: 2015-08-16
forum: Hardware
---

### Post by asb3 on 2015-08-16
I want to install a RAID in my machine. My motherboard contains the Intel c210 chipset.  I'm running ubuntu 14.04.3 LTS. The system has 3 SATA ports, two of which are connected to FLASH drives.  I recently lost some data when my hard drive failed, so I want to install a RAID.  I installed an iocrest PCI-Epress Sata III raid card and two 2T hard drives.  When I try to boot the system, I see screen which says

Asmedia 106x SATA Controller Ver 0.61 ALTCI mode.
Copyright (c) Asmedia Technologies, Inc all rights reserved
S.M.A.R.T. supported
Using PCIE Gen 2


Press 'Ctrl-r' to enter RAID menu


Nothing happens when I press 'Clrl-r'; in fact, the machine doesn't boot and is completely unresponsive.  In fact, if I reboot and press "del", the machine will not enter the BIOS.  The only way I can get the machine to boot is to disconnect the hard drives from the RAID controller.

What do I have to do to get the RAID card to work?  I did install the drivers that came with the card.

---

### Post by dino99 on 2015-08-16
a few things to check:
- bios/uefi raid settings
- hdd jumper config
- pci card doc

then you need to know if there is some warning/error related to that raid card: see dmesg

---

### Post by asb3 on 2015-08-16
How do I check the bios/uefi settings?  I rebooted and went into bios and didn't see anything about uefi or RAID.
jumper on what device?
The card came with almost no documentation.

I looked in /var/log/dmesg.  I could not look for messages after a failed boot, since then the  computer was completely frozen and I had to turn off the power and remove some cables to get the machine to boot.



The only lines in /var/log/dmesg that mention RAID or pci are:

[    0.000000] e820: [mem 0xdf200000-0xf7ffffff] available for PCI devices
[    0.237123] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.237124] ACPI: bus type PCI registered
[    0.237125] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.237162] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.237164] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.242030] PCI: Using configuration type 1 for base access
[    0.262354] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.266834] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    0.266968] acpi PNP0A08:00: _OSC: platform does not support [PCIeHotplug PME]
[    0.267045] acpi PNP0A08:00: _OSC: OS now controls [AER PCIeCapability]
[    0.267422] PCI host bridge to bus 0000:00
[    0.267424] pci_bus 0000:00: root bus resource [bus 00-3e]
[    0.267425] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.267426] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.267427] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.267428] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    0.267429] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    0.267430] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    0.267431] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    0.267432] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
[    0.267433] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff]
[    0.267434] pci_bus 0000:00: root bus resource [mem 0xdf200000-0xfeafffff]
[    0.267440] pci 0000:00:00.0: [8086:0150] type 00 class 0x060000
[    0.267499] pci 0000:00:01.0: [8086:0151] type 01 class 0x060400
[    0.267520] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.267550] pci 0000:00:01.0: System wakeup disabled by ACPI
[    0.267571] pci 0000:00:02.0: [8086:0162] type 00 class 0x030000
[    0.267578] pci 0000:00:02.0: reg 0x10: [mem 0xf7800000-0xf7bfffff 64bit]
[    0.267583] pci 0000:00:02.0: reg 0x18: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.267586] pci 0000:00:02.0: reg 0x20: [io  0xf000-0xf03f]
[    0.267656] pci 0000:00:14.0: [8086:1e31] type 00 class 0x0c0330
[    0.267676] pci 0000:00:14.0: reg 0x10: [mem 0xf7e00000-0xf7e0ffff 64bit]
[    0.267741] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.267774] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.267796] pci 0000:00:16.0: [8086:1e3a] type 00 class 0x078000
[    0.267816] pci 0000:00:16.0: reg 0x10: [mem 0xf7e1a000-0xf7e1a00f 64bit]
[    0.267885] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.267946] pci 0000:00:1a.0: [8086:1e2d] type 00 class 0x0c0320
[    0.267965] pci 0000:00:1a.0: reg 0x10: [mem 0xf7e18000-0xf7e183ff]
[    0.268048] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.268091] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.268114] pci 0000:00:1b.0: [8086:1e20] type 00 class 0x040300
[    0.268127] pci 0000:00:1b.0: reg 0x10: [mem 0xf7e10000-0xf7e13fff 64bit]
[    0.268188] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.268224] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.268251] pci 0000:00:1c.0: [8086:1e10] type 01 class 0x060400
[    0.268378] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.268424] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.268446] pci 0000:00:1c.4: [8086:1e18] type 01 class 0x060400
[    0.268516] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.268553] pci 0000:00:1c.4: System wakeup disabled by ACPI
[    0.268572] pci 0000:00:1c.5: [8086:244e] type 01 class 0x060401
[    0.268643] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.268680] pci 0000:00:1c.5: System wakeup disabled by ACPI
[    0.268700] pci 0000:00:1c.6: [8086:1e1c] type 01 class 0x060400
[    0.268771] pci 0000:00:1c.6: PME# supported from D0 D3hot D3cold
[    0.268808] pci 0000:00:1c.6: System wakeup disabled by ACPI
[    0.268827] pci 0000:00:1c.7: [8086:1e1e] type 01 class 0x060400
[    0.268898] pci 0000:00:1c.7: PME# supported from D0 D3hot D3cold
[    0.268935] pci 0000:00:1c.7: System wakeup disabled by ACPI
[    0.268958] pci 0000:00:1d.0: [8086:1e26] type 00 class 0x0c0320
[    0.268977] pci 0000:00:1d.0: reg 0x10: [mem 0xf7e17000-0xf7e173ff]
[    0.269060] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.269103] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.269125] pci 0000:00:1f.0: [8086:1e44] type 00 class 0x060100
[    0.269270] pci 0000:00:1f.2: [8086:1e02] type 00 class 0x010601
[    0.269286] pci 0000:00:1f.2: reg 0x10: [io  0xf0b0-0xf0b7]
[    0.269292] pci 0000:00:1f.2: reg 0x14: [io  0xf0a0-0xf0a3]
[    0.269298] pci 0000:00:1f.2: reg 0x18: [io  0xf090-0xf097]
[    0.269305] pci 0000:00:1f.2: reg 0x1c: [io  0xf080-0xf083]
[    0.269311] pci 0000:00:1f.2: reg 0x20: [io  0xf060-0xf07f]
[    0.269317] pci 0000:00:1f.2: reg 0x24: [mem 0xf7e16000-0xf7e167ff]
[    0.269357] pci 0000:00:1f.2: PME# supported from D3hot
[    0.269405] pci 0000:00:1f.3: [8086:1e22] type 00 class 0x0c0500
[    0.269418] pci 0000:00:1f.3: reg 0x10: [mem 0xf7e15000-0xf7e150ff 64bit]
[    0.269436] pci 0000:00:1f.3: reg 0x20: [io  0xf040-0xf05f]
[    0.269515] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.269595] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.269679] pci 0000:03:00.0: [10ec:8168] type 00 class 0x020000
[    0.269697] pci 0000:03:00.0: reg 0x10: [io  0xe000-0xe0ff]
[    0.269729] pci 0000:03:00.0: reg 0x18: [mem 0xf0004000-0xf0004fff 64bit pref]
[    0.269749] pci 0000:03:00.0: reg 0x20: [mem 0xf0000000-0xf0003fff 64bit pref]
[    0.269838] pci 0000:03:00.0: supports D1 D2
[    0.269839] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.269873] pci 0000:03:00.0: System wakeup disabled by ACPI
[    0.277595] pci 0000:00:1c.4: PCI bridge to [bus 03]
[    0.277600] pci 0000:00:1c.4:   bridge window [io  0xe000-0xefff]
[    0.277610] pci 0000:00:1c.4:   bridge window [mem 0xf0000000-0xf00fffff 64bit pref]
[    0.277698] pci 0000:04:00.0: [1b21:1080] type 01 class 0x060401
[    0.277814] pci 0000:04:00.0: System wakeup disabled by ACPI
[    0.277828] pci 0000:00:1c.5: PCI bridge to [bus 04-05] (subtractive decode)
[    0.277837] pci 0000:00:1c.5:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.277838] pci 0000:00:1c.5:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.277840] pci 0000:00:1c.5:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.277841] pci 0000:00:1c.5:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.277842] pci 0000:00:1c.5:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.277843] pci 0000:00:1c.5:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.277844] pci 0000:00:1c.5:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.277845] pci 0000:00:1c.5:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    0.277846] pci 0000:00:1c.5:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
[    0.277847] pci 0000:00:1c.5:   bridge window [mem 0xdf200000-0xfeafffff] (subtractive decode)
[    0.277954] pci 0000:04:00.0: PCI bridge to [bus 05] (subtractive decode)
[    0.277974] pci 0000:04:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.277975] pci 0000:04:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.277978] pci 0000:04:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.277979] pci 0000:04:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.277980] pci 0000:04:00.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.277981] pci 0000:04:00.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.277982] pci 0000:04:00.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.277983] pci 0000:04:00.0:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.277984] pci 0000:04:00.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.277985] pci 0000:04:00.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.277986] pci 0000:04:00.0:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.277987] pci 0000:04:00.0:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    0.277988] pci 0000:04:00.0:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
[    0.277989] pci 0000:04:00.0:   bridge window [mem 0xdf200000-0xfeafffff] (subtractive decode)
[    0.278064] pci 0000:06:00.0: [1b21:0622] type 00 class 0x010601
[    0.278138] pci 0000:06:00.0: reg 0x24: [mem 0xf7d80000-0xf7d81fff]
[    0.278150] pci 0000:06:00.0: reg 0x30: [mem 0xf7d00000-0xf7d7ffff pref]
[    0.278214] pci 0000:06:00.0: System wakeup disabled by ACPI
[    0.285602] pci 0000:00:1c.6: PCI bridge to [bus 06]
[    0.285610] pci 0000:00:1c.6:   bridge window [mem 0xf7d00000-0xf7dfffff]
[    0.285712] pci 0000:07:00.0: [1b21:1042] type 00 class 0x0c0330
[    0.285739] pci 0000:07:00.0: reg 0x10: [mem 0xf7c00000-0xf7c07fff 64bit]
[    0.285881] pci 0000:07:00.0: PME# supported from D3hot D3cold
[    0.285911] pci 0000:07:00.0: System wakeup disabled by ACPI
[    0.293614] pci 0000:00:1c.7: PCI bridge to [bus 07]
[    0.293622] pci 0000:00:1c.7:   bridge window [mem 0xf7c00000-0xf7cfffff]
[    0.293990] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.294022] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 10 11 12 *14 15)
[    0.294053] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 *6 10 11 12 14 15)
[    0.294084] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 10 11 12 14 *15)
[    0.294114] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.294145] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.294175] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 6 10 11 12 14 15)
[    0.294205] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 10 11 12 14 15)
[    0.294359] ACPI: \_SB_.PCI0: notify handler is installed
[    0.294449] vgaarb: setting as boot device: PCI:0000:00:02.0
[    0.294451] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.294679] PCI: Using ACPI for IRQ routing
[    0.296007] PCI: pci_cache_line_size set to 64 bytes
[    0.307084] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.307088] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.307104] pci 0000:00:1c.4: PCI bridge to [bus 03]
[    0.307107] pci 0000:00:1c.4:   bridge window [io  0xe000-0xefff]
[    0.307112] pci 0000:00:1c.4:   bridge window [mem 0xf0000000-0xf00fffff 64bit pref]
[    0.307117] pci 0000:04:00.0: PCI bridge to [bus 05]
[    0.307136] pci 0000:00:1c.5: PCI bridge to [bus 04-05]
[    0.307145] pci 0000:00:1c.6: PCI bridge to [bus 06]
[    0.307149] pci 0000:00:1c.6:   bridge window [mem 0xf7d00000-0xf7dfffff]
[    0.307156] pci 0000:00:1c.7: PCI bridge to [bus 07]
[    0.307160] pci 0000:00:1c.7:   bridge window [mem 0xf7c00000-0xf7cfffff]
[    0.307167] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.307168] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.307169] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.307170] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.307171] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.307172] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.307174] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    0.307175] pci_bus 0000:00: resource 11 [mem 0x000e0000-0x000e3fff]
[    0.307176] pci_bus 0000:00: resource 12 [mem 0x000e4000-0x000e7fff]
[    0.307177] pci_bus 0000:00: resource 13 [mem 0xdf200000-0xfeafffff]
[    0.307178] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
[    0.307179] pci_bus 0000:03: resource 2 [mem 0xf0000000-0xf00fffff 64bit pref]
[    0.307180] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
[    0.307181] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
[    0.307182] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    0.307183] pci_bus 0000:04: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.307184] pci_bus 0000:04: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.307185] pci_bus 0000:04: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.307186] pci_bus 0000:04: resource 10 [mem 0x000dc000-0x000dffff]
[    0.307187] pci_bus 0000:04: resource 11 [mem 0x000e0000-0x000e3fff]
[    0.307188] pci_bus 0000:04: resource 12 [mem 0x000e4000-0x000e7fff]
[    0.307190] pci_bus 0000:04: resource 13 [mem 0xdf200000-0xfeafffff]
[    0.307191] pci_bus 0000:05: resource 8 [io  0x0000-0x0cf7]
[    0.307192] pci_bus 0000:05: resource 9 [io  0x0d00-0xffff]
[    0.307193] pci_bus 0000:05: resource 10 [mem 0x000a0000-0x000bffff]
[    0.307194] pci_bus 0000:05: resource 11 [mem 0x000d0000-0x000d3fff]
[    0.307195] pci_bus 0000:05: resource 12 [mem 0x000d4000-0x000d7fff]
[    0.307196] pci_bus 0000:05: resource 13 [mem 0x000d8000-0x000dbfff]
[    0.307197] pci_bus 0000:05: resource 14 [mem 0x000dc000-0x000dffff]
[    0.307198] pci_bus 0000:05: resource 15 [mem 0x000e0000-0x000e3fff]
[    0.307199] pci_bus 0000:05: resource 16 [mem 0x000e4000-0x000e7fff]
[    0.307200] pci_bus 0000:05: resource 17 [mem 0xdf200000-0xfeafffff]
[    0.307201] pci_bus 0000:06: resource 1 [mem 0xf7d00000-0xf7dfffff]
[    0.307202] pci_bus 0000:07: resource 1 [mem 0xf7c00000-0xf7cfffff]
[    0.307979] pci 0000:00:02.0: Video device with shadowed ROM
[    0.346445] PCI: CLS 64 bytes, default 64
[    0.554711] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.575312] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.575645] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.575652] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.609511] ehci-pci: EHCI PCI platform driver
[    0.609589] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    0.609593] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.609604] ehci-pci 0000:00:1a.0: debug port 2
[    0.613511] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    0.613523] ehci-pci 0000:00:1a.0: irq 23, io mem 0xf7e18000
[    0.622517] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.622738] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    0.622741] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.622751] ehci-pci 0000:00:1d.0: debug port 2
[    0.626645] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    0.626651] ehci-pci 0000:00:1d.0: irq 23, io mem 0xf7e17000
[    0.638529] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.638677] ohci-pci: OHCI PCI platform driver
[    0.934840] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.107529] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT0._GTF] (Node ffff8807f40d4208), AE_NOT_FOUND (20131115/psparse-536)
[    1.107560] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT4._GTF] (Node ffff8807f40d43e8), AE_NOT_FOUND (20131115/psparse-536)
[    1.107594] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT3._GTF] (Node ffff8807f40d4370), AE_NOT_FOUND (20131115/psparse-536)
[    1.108444] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT4._GTF] (Node ffff8807f40d43e8), AE_NOT_FOUND (20131115/psparse-536)
[    1.108603] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT0._GTF] (Node ffff8807f40d4208), AE_NOT_FOUND (20131115/psparse-536)
[    1.117636] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT3._GTF] (Node ffff8807f40d4370), AE_NOT_FOUND (20131115/psparse-536)
[    1.179167] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.506055] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.0/input/input5
[    1.695017] input: Microsoft Microsoft\xffffffc2\xffffffae Digital Media Pro Keyboard as /devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.0/input/input6
[    1.700425] input: Microsoft Microsoft\xffffffc2\xffffffae Digital Media Pro Keyboard as /devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.1/input/input7
[    4.361071] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    4.422432] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    4.910268] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input19
[    4.910332] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input18
[    4.910396] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input17
[    4.910457] input: HDA Intel PCH Line Out Side as /devices/pci0000:00/0000:00:1b.0/sound/card0/input16
[    4.910518] input: HDA Intel PCH Line Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[    4.910579] input: HDA Intel PCH Line Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[    4.910631] input: HDA Intel PCH Line Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[    4.910659] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[    4.910691] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[    4.910719] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10

[    0.752910] md: raid0 personality registered for level 0
[    0.754596] md: raid1 personality registered for level 1
[    0.822708] raid6: sse2x1   10006 MB/s
[    0.890773] raid6: sse2x2   12615 MB/s
[    0.958841] raid6: sse2x4   15085 MB/s
[    0.958842] raid6: using algorithm sse2x4 (15085 MB/s)
[    0.958843] raid6: using ssse3x2 recovery algorithm
[    1.003755] md: raid6 personality registered for level 6
[    1.003756] md: raid5 personality registered for level 5
[    1.003757] md: raid4 personality registered for level 4
[    1.006855] md: raid10 personality registered for level 10

---

### Post by asb3 on 2015-09-25
The failure was caused by a bad hard drive.  I now have the card installed and attached to two good hard drives.  When I boot the machine, I still get the message "Press Ctrl-r to configure RAID", but pressing ctrl-r does nothing, and the machine boots normally.  with the gnome disk utility I can see the two new unformatted drives, but I don't know how to configure a RAID1.  Can I just use mdadm?  (It seems odd to use softward RAID with a RAID card).

---

