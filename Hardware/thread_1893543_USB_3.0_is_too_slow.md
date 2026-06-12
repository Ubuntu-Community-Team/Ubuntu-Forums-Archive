---
title: "USB 3.0 is too slow"
date: 2011-12-10
forum: Hardware
---

### Post by aa-hcl on 2011-12-10
Hi,

I am asking for help to find out how to make USB3.0 working faster than USB2.0. At the moment it is recognised as USB3.0, but only gives me USB2.0 performance and I wonder whether it is possible to make faster!

Hardware:
Dell laptop Latitude E6520, it does not have the built-in USB3.0 port, so I have to buy the PCI Express Card (EC).

The card is Startech ECUSB3S2 USB 3.0 Expresscard ([http://intrl.startech.com/Cards-Adapters/USB-3.0/Cards/2-Port-Flush-Mount-ExpressCard-SuperSpeed-USB-3-Card-Adapter~ECUSB3S254F](http://intrl.startech.com/Cards-Adapters/USB-3.0/Cards/2-Port-Flush-Mount-ExpressCard-SuperSpeed-USB-3-Card-Adapter~ECUSB3S254F))

I am under ubuntu 11.10:

aa@aa-i7:~$ uname -a
Linux aa-i7 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux


1.
The Express card was recognised by the system:

[CODE]  
aa@aa-i7:~$ lspci -v
...
04:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03) (prog-if 30 [XHCI])
	Physical Slot: 1
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at e5b00000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: xhci_hcd
	Kernel modules: xhci-hcd
[\CODE]

But in the kernel it writes two warnings:


Dec 10 13:01:57 aa-i7 kernel: [  154.225740] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:59:45 aa-i7 kernel: [    3.269585] xhci_hcd 0000:04:00.0: WARN: short transfer on control ep


in more details:

[CODE]
Dec 10 01:42:50 aa-i7 kernel: [    1.681437] pci 0000:04:00.0: [1033:0194] type 0 class 0x000c03
Dec 10 01:42:50 aa-i7 kernel: [    1.681484] pci 0000:04:00.0: reg 10: [mem 0xe5b00000-0xe5b01fff 64bit]
Dec 10 01:42:50 aa-i7 kernel: [    1.681660] pci 0000:04:00.0: PME# supported from D0 D3hot
Dec 10 01:42:50 aa-i7 kernel: [    1.681668] pci 0000:04:00.0: PME# disabled
Dec 10 01:42:50 aa-i7 kernel: [    2.400138] xhci_hcd 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Dec 10 01:42:50 aa-i7 kernel: [    2.400158] xhci_hcd 0000:04:00.0: setting latency timer to 64
Dec 10 01:42:50 aa-i7 kernel: [    2.400162] xhci_hcd 0000:04:00.0: xHCI Host Controller
Dec 10 01:42:50 aa-i7 kernel: [    2.400198] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 3
Dec 10 01:42:50 aa-i7 kernel: [    2.400363] xhci_hcd 0000:04:00.0: irq 18, io mem 0xe5b00000
Dec 10 01:42:50 aa-i7 kernel: [    2.400427] xhci_hcd 0000:04:00.0: irq 42 for MSI/MSI-X
Dec 10 01:42:50 aa-i7 kernel: [    2.400433] xhci_hcd 0000:04:00.0: irq 43 for MSI/MSI-X
Dec 10 01:42:50 aa-i7 kernel: [    2.400438] xhci_hcd 0000:04:00.0: irq 44 for MSI/MSI-X
Dec 10 01:42:50 aa-i7 kernel: [    2.400442] xhci_hcd 0000:04:00.0: irq 45 for MSI/MSI-X
Dec 10 01:42:50 aa-i7 kernel: [    2.400446] xhci_hcd 0000:04:00.0: irq 46 for MSI/MSI-X
Dec 10 01:42:50 aa-i7 kernel: [    2.401363] xhci_hcd 0000:04:00.0: xHCI Host Controller
Dec 10 01:42:50 aa-i7 kernel: [    2.401401] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 4
Dec 10 11:10:35 aa-i7 kernel: [    1.681229] pci 0000:04:00.0: [1033:0194] type 0 class 0x000c03
Dec 10 11:10:35 aa-i7 kernel: [    1.681276] pci 0000:04:00.0: reg 10: [mem 0xe5b00000-0xe5b01fff 64bit]
Dec 10 11:10:35 aa-i7 kernel: [    1.681403] pci 0000:04:00.0: PME# supported from D0 D3hot
Dec 10 11:10:35 aa-i7 kernel: [    1.681411] pci 0000:04:00.0: PME# disabled
Dec 10 11:10:35 aa-i7 kernel: [    2.434266] xhci_hcd 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Dec 10 11:10:35 aa-i7 kernel: [    2.434296] xhci_hcd 0000:04:00.0: setting latency timer to 64
Dec 10 11:10:35 aa-i7 kernel: [    2.434302] xhci_hcd 0000:04:00.0: xHCI Host Controller
Dec 10 11:10:35 aa-i7 kernel: [    2.434372] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 3
Dec 10 11:10:35 aa-i7 kernel: [    2.434551] xhci_hcd 0000:04:00.0: irq 18, io mem 0xe5b00000
Dec 10 11:10:35 aa-i7 kernel: [    2.434642] xhci_hcd 0000:04:00.0: irq 42 for MSI/MSI-X
Dec 10 11:10:35 aa-i7 kernel: [    2.434652] xhci_hcd 0000:04:00.0: irq 43 for MSI/MSI-X
Dec 10 11:10:35 aa-i7 kernel: [    2.434660] xhci_hcd 0000:04:00.0: irq 44 for MSI/MSI-X
Dec 10 11:10:35 aa-i7 kernel: [    2.434668] xhci_hcd 0000:04:00.0: irq 45 for MSI/MSI-X
Dec 10 11:10:35 aa-i7 kernel: [    2.434676] xhci_hcd 0000:04:00.0: irq 46 for MSI/MSI-X
Dec 10 11:10:35 aa-i7 kernel: [    2.435020] xhci_hcd 0000:04:00.0: xHCI Host Controller
Dec 10 11:10:35 aa-i7 kernel: [    2.435066] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 4
Dec 10 11:31:11 aa-i7 kernel: [ 1245.661481] xhci_hcd 0000:04:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
Dec 10 11:31:11 aa-i7 kernel: [ 1245.661503] xhci_hcd 0000:04:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xe5b00004)
Dec 10 11:31:11 aa-i7 kernel: [ 1245.661508] xhci_hcd 0000:04:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
Dec 10 11:31:11 aa-i7 kernel: [ 1245.661515] xhci_hcd 0000:04:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100402)
Dec 10 11:31:11 aa-i7 kernel: [ 1245.662161] xhci_hcd 0000:04:00.0: setting latency timer to 64
Dec 10 11:31:11 aa-i7 kernel: [ 1245.662751] xhci_hcd 0000:04:00.0: irq 42 for MSI/MSI-X
Dec 10 11:31:11 aa-i7 kernel: [ 1245.662756] xhci_hcd 0000:04:00.0: irq 43 for MSI/MSI-X
Dec 10 11:31:11 aa-i7 kernel: [ 1245.662761] xhci_hcd 0000:04:00.0: irq 44 for MSI/MSI-X
Dec 10 11:31:11 aa-i7 kernel: [ 1245.662766] xhci_hcd 0000:04:00.0: irq 45 for MSI/MSI-X
Dec 10 11:31:11 aa-i7 kernel: [ 1245.662770] xhci_hcd 0000:04:00.0: irq 46 for MSI/MSI-X
Dec 10 11:36:59 aa-i7 kernel: [ 1379.279271] xhci_hcd 0000:04:00.0: setting latency timer to 64
Dec 10 11:36:59 aa-i7 kernel: [ 1379.294241] xhci_hcd 0000:04:00.0: irq 42 for MSI/MSI-X
Dec 10 11:36:59 aa-i7 kernel: [ 1379.294247] xhci_hcd 0000:04:00.0: irq 43 for MSI/MSI-X
Dec 10 11:36:59 aa-i7 kernel: [ 1379.294253] xhci_hcd 0000:04:00.0: irq 44 for MSI/MSI-X
Dec 10 11:36:59 aa-i7 kernel: [ 1379.294259] xhci_hcd 0000:04:00.0: irq 45 for MSI/MSI-X
Dec 10 11:36:59 aa-i7 kernel: [ 1379.294265] xhci_hcd 0000:04:00.0: irq 46 for MSI/MSI-X
Dec 10 12:01:13 aa-i7 kernel: [    1.681972] pci 0000:04:00.0: [1033:0194] type 0 class 0x000c03
Dec 10 12:01:13 aa-i7 kernel: [    1.682020] pci 0000:04:00.0: reg 10: [mem 0xe5b00000-0xe5b01fff 64bit]
Dec 10 12:01:13 aa-i7 kernel: [    1.682212] pci 0000:04:00.0: PME# supported from D0 D3hot
Dec 10 12:01:13 aa-i7 kernel: [    1.682220] pci 0000:04:00.0: PME# disabled
Dec 10 12:01:13 aa-i7 kernel: [    2.419958] xhci_hcd 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Dec 10 12:01:13 aa-i7 kernel: [    2.419977] xhci_hcd 0000:04:00.0: setting latency timer to 64
Dec 10 12:01:13 aa-i7 kernel: [    2.419982] xhci_hcd 0000:04:00.0: xHCI Host Controller
Dec 10 12:01:13 aa-i7 kernel: [    2.420029] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 3
Dec 10 12:01:13 aa-i7 kernel: [    2.420212] xhci_hcd 0000:04:00.0: irq 18, io mem 0xe5b00000
Dec 10 12:01:13 aa-i7 kernel: [    2.420278] xhci_hcd 0000:04:00.0: irq 43 for MSI/MSI-X
Dec 10 12:01:13 aa-i7 kernel: [    2.420282] xhci_hcd 0000:04:00.0: irq 44 for MSI/MSI-X
Dec 10 12:01:13 aa-i7 kernel: [    2.420287] xhci_hcd 0000:04:00.0: irq 45 for MSI/MSI-X
Dec 10 12:01:13 aa-i7 kernel: [    2.420291] xhci_hcd 0000:04:00.0: irq 46 for MSI/MSI-X
Dec 10 12:01:13 aa-i7 kernel: [    2.420295] xhci_hcd 0000:04:00.0: irq 47 for MSI/MSI-X
Dec 10 12:01:13 aa-i7 kernel: [    2.420506] xhci_hcd 0000:04:00.0: xHCI Host Controller
Dec 10 12:01:13 aa-i7 kernel: [    2.420525] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 4
Dec 10 12:05:27 aa-i7 kernel: [  275.046875] xhci_hcd 0000:04:00.0: remove, state 4
Dec 10 12:05:27 aa-i7 kernel: [  275.115136] xhci_hcd 0000:04:00.0: USB bus 4 deregistered
Dec 10 12:05:27 aa-i7 kernel: [  275.115232] xhci_hcd 0000:04:00.0: remove, state 4
Dec 10 12:05:27 aa-i7 kernel: [  275.135304] xhci_hcd 0000:04:00.0: USB bus 3 deregistered
Dec 10 12:05:27 aa-i7 kernel: [  275.135435] xhci_hcd 0000:04:00.0: PCI INT A disabled
Dec 10 12:05:27 aa-i7 kernel: [  275.136180] pci 0000:04:00.0: [1033:0194] type 0 class 0x000c03
Dec 10 12:05:27 aa-i7 kernel: [  275.136242] pci 0000:04:00.0: reg 10: [mem 0x00000000-0x00001fff 64bit]
Dec 10 12:05:27 aa-i7 kernel: [  275.136472] pci 0000:04:00.0: PME# supported from D0 D3hot
Dec 10 12:05:27 aa-i7 kernel: [  275.136485] pci 0000:04:00.0: PME# disabled
Dec 10 12:05:27 aa-i7 kernel: [  275.136737] pci 0000:04:00.0: BAR 0: assigned [mem 0xe5b00000-0xe5b01fff 64bit]
Dec 10 12:05:27 aa-i7 kernel: [  275.136758] pci 0000:04:00.0: BAR 0: set to [mem 0xe5b00000-0xe5b01fff 64bit] (PCI address [0xe5b00000-0xe5b01fff])
Dec 10 12:05:27 aa-i7 kernel: [  275.136815] pci 0000:04:00.0: no hotplug settings from platform
Dec 10 12:05:27 aa-i7 kernel: [  275.136950] xhci_hcd 0000:04:00.0: enabling device (0000 -> 0002)
Dec 10 12:05:27 aa-i7 kernel: [  275.136965] xhci_hcd 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Dec 10 12:05:27 aa-i7 kernel: [  275.137094] xhci_hcd 0000:04:00.0: setting latency timer to 64
Dec 10 12:05:27 aa-i7 kernel: [  275.137103] xhci_hcd 0000:04:00.0: xHCI Host Controller
Dec 10 12:05:27 aa-i7 kernel: [  275.137223] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 3
Dec 10 12:05:27 aa-i7 kernel: [  275.137439] xhci_hcd 0000:04:00.0: irq 18, io mem 0xe5b00000
Dec 10 12:05:27 aa-i7 kernel: [  275.137575] xhci_hcd 0000:04:00.0: irq 43 for MSI/MSI-X
Dec 10 12:05:27 aa-i7 kernel: [  275.137593] xhci_hcd 0000:04:00.0: irq 44 for MSI/MSI-X
Dec 10 12:05:27 aa-i7 kernel: [  275.137609] xhci_hcd 0000:04:00.0: irq 45 for MSI/MSI-X
Dec 10 12:05:27 aa-i7 kernel: [  275.137624] xhci_hcd 0000:04:00.0: irq 46 for MSI/MSI-X
Dec 10 12:05:27 aa-i7 kernel: [  275.137639] xhci_hcd 0000:04:00.0: irq 47 for MSI/MSI-X
Dec 10 12:05:27 aa-i7 kernel: [  275.138162] xhci_hcd 0000:04:00.0: xHCI Host Controller
Dec 10 12:05:27 aa-i7 kernel: [  275.138239] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 4
Dec 10 12:05:35 aa-i7 kernel: [  283.131839] xhci_hcd 0000:04:00.0: WARN: short transfer on control ep
Dec 10 12:05:35 aa-i7 kernel: [  283.133248] xhci_hcd 0000:04:00.0: WARN: short transfer on control ep
Dec 10 12:05:35 aa-i7 kernel: [  283.134586] xhci_hcd 0000:04:00.0: WARN: short transfer on control ep
Dec 10 12:05:35 aa-i7 kernel: [  283.135835] xhci_hcd 0000:04:00.0: WARN: short transfer on control ep
Dec 10 12:05:35 aa-i7 kernel: [  283.142970] xhci_hcd 0000:04:00.0: WARN: short transfer on control ep
Dec 10 12:05:35 aa-i7 kernel: [  283.144572] xhci_hcd 0000:04:00.0: WARN: short transfer on control ep
Dec 10 12:05:37 aa-i7 kernel: [  284.502718] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:05:37 aa-i7 kernel: [  284.556330] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:05:37 aa-i7 kernel: [  284.609765] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:05:37 aa-i7 kernel: [  284.660849] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:05:37 aa-i7 kernel: [  284.971063] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:05:37 aa-i7 kernel: [  285.161001] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:05:37 aa-i7 kernel: [  285.237899] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:05:37 aa-i7 kernel: [  285.300522] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:05:37 aa-i7 kernel: [  285.339519] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:05:37 aa-i7 kernel: [  285.412277] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:05:38 aa-i7 kernel: [  285.470993] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:05:38 aa-i7 kernel: [  285.543369] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:05:38 aa-i7 kernel: [  285.581544] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:05:38 aa-i7 kernel: [  285.633857] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:05:38 aa-i7 kernel: [  285.658387] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:05:38 aa-i7 kernel: [  285.719691] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:05:38 aa-i7 kernel: [  285.755092] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:05:38 aa-i7 kernel: [  285.937538] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:05:38 aa-i7 kernel: [  285.962205] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:05:38 aa-i7 kernel: [  286.045986] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:05:38 aa-i7 kernel: [  286.070658] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:05:38 aa-i7 kernel: [  286.095671] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:05:38 aa-i7 kernel: [  286.120190] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:05:38 aa-i7 kernel: [  286.194360] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:05:38 aa-i7 kernel: [  286.232472] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:05:38 aa-i7 kernel: [  286.305295] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:05:38 aa-i7 kernel: [  286.333630] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:05:38 aa-i7 kernel: [  286.406732] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:31:39 aa-i7 kernel: [    1.682242] pci 0000:04:00.0: [1033:0194] type 0 class 0x000c03
Dec 10 12:31:39 aa-i7 kernel: [    1.682289] pci 0000:04:00.0: reg 10: [mem 0xe5b00000-0xe5b01fff 64bit]
Dec 10 12:31:39 aa-i7 kernel: [    1.682490] pci 0000:04:00.0: PME# supported from D0 D3hot
Dec 10 12:31:39 aa-i7 kernel: [    1.682498] pci 0000:04:00.0: PME# disabled
Dec 10 12:31:39 aa-i7 kernel: [    2.423831] xhci_hcd 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Dec 10 12:31:39 aa-i7 kernel: [    2.423852] xhci_hcd 0000:04:00.0: setting latency timer to 64
Dec 10 12:31:39 aa-i7 kernel: [    2.423856] xhci_hcd 0000:04:00.0: xHCI Host Controller
Dec 10 12:31:39 aa-i7 kernel: [    2.423895] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 3
Dec 10 12:31:39 aa-i7 kernel: [    2.424065] xhci_hcd 0000:04:00.0: irq 18, io mem 0xe5b00000
Dec 10 12:31:39 aa-i7 kernel: [    2.424131] xhci_hcd 0000:04:00.0: irq 43 for MSI/MSI-X
Dec 10 12:31:39 aa-i7 kernel: [    2.424136] xhci_hcd 0000:04:00.0: irq 44 for MSI/MSI-X
Dec 10 12:31:39 aa-i7 kernel: [    2.424141] xhci_hcd 0000:04:00.0: irq 45 for MSI/MSI-X
Dec 10 12:31:39 aa-i7 kernel: [    2.424145] xhci_hcd 0000:04:00.0: irq 46 for MSI/MSI-X
Dec 10 12:31:39 aa-i7 kernel: [    2.424149] xhci_hcd 0000:04:00.0: irq 47 for MSI/MSI-X
Dec 10 12:31:39 aa-i7 kernel: [    2.424360] xhci_hcd 0000:04:00.0: xHCI Host Controller
Dec 10 12:31:39 aa-i7 kernel: [    2.424379] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 4
Dec 10 12:32:54 aa-i7 kernel: [   95.619204] xhci_hcd 0000:04:00.0: remove, state 4
Dec 10 12:32:54 aa-i7 kernel: [   95.664951] xhci_hcd 0000:04:00.0: USB bus 4 deregistered
Dec 10 12:32:54 aa-i7 kernel: [   95.665046] xhci_hcd 0000:04:00.0: remove, state 4
Dec 10 12:32:54 aa-i7 kernel: [   95.693458] xhci_hcd 0000:04:00.0: USB bus 3 deregistered
Dec 10 12:32:54 aa-i7 kernel: [   95.693604] xhci_hcd 0000:04:00.0: PCI INT A disabled
Dec 10 12:32:54 aa-i7 kernel: [   95.694340] pci 0000:04:00.0: [1033:0194] type 0 class 0x000c03
Dec 10 12:32:54 aa-i7 kernel: [   95.694401] pci 0000:04:00.0: reg 10: [mem 0x00000000-0x00001fff 64bit]
Dec 10 12:32:54 aa-i7 kernel: [   95.694633] pci 0000:04:00.0: PME# supported from D0 D3hot
Dec 10 12:32:54 aa-i7 kernel: [   95.694646] pci 0000:04:00.0: PME# disabled
Dec 10 12:32:54 aa-i7 kernel: [   95.694901] pci 0000:04:00.0: BAR 0: assigned [mem 0xe5b00000-0xe5b01fff 64bit]
Dec 10 12:32:54 aa-i7 kernel: [   95.694922] pci 0000:04:00.0: BAR 0: set to [mem 0xe5b00000-0xe5b01fff 64bit] (PCI address [0xe5b00000-0xe5b01fff])
Dec 10 12:32:54 aa-i7 kernel: [   95.694979] pci 0000:04:00.0: no hotplug settings from platform
Dec 10 12:32:54 aa-i7 kernel: [   95.695109] xhci_hcd 0000:04:00.0: enabling device (0000 -> 0002)
Dec 10 12:32:54 aa-i7 kernel: [   95.695123] xhci_hcd 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Dec 10 12:32:54 aa-i7 kernel: [   95.695235] xhci_hcd 0000:04:00.0: setting latency timer to 64
Dec 10 12:32:54 aa-i7 kernel: [   95.695244] xhci_hcd 0000:04:00.0: xHCI Host Controller
Dec 10 12:32:54 aa-i7 kernel: [   95.695367] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 3
Dec 10 12:32:54 aa-i7 kernel: [   95.695585] xhci_hcd 0000:04:00.0: irq 18, io mem 0xe5b00000
Dec 10 12:32:54 aa-i7 kernel: [   95.695722] xhci_hcd 0000:04:00.0: irq 43 for MSI/MSI-X
Dec 10 12:32:54 aa-i7 kernel: [   95.695739] xhci_hcd 0000:04:00.0: irq 44 for MSI/MSI-X
Dec 10 12:32:54 aa-i7 kernel: [   95.695755] xhci_hcd 0000:04:00.0: irq 45 for MSI/MSI-X
Dec 10 12:32:54 aa-i7 kernel: [   95.695770] xhci_hcd 0000:04:00.0: irq 46 for MSI/MSI-X
Dec 10 12:32:54 aa-i7 kernel: [   95.695785] xhci_hcd 0000:04:00.0: irq 47 for MSI/MSI-X
Dec 10 12:32:54 aa-i7 kernel: [   95.696305] xhci_hcd 0000:04:00.0: xHCI Host Controller
Dec 10 12:32:54 aa-i7 kernel: [   95.696398] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 4
Dec 10 12:33:02 aa-i7 kernel: [  103.636542] xhci_hcd 0000:04:00.0: WARN: short transfer on control ep
Dec 10 12:33:02 aa-i7 kernel: [  103.637803] xhci_hcd 0000:04:00.0: WARN: short transfer on control ep
Dec 10 12:33:02 aa-i7 kernel: [  103.639201] xhci_hcd 0000:04:00.0: WARN: short transfer on control ep
Dec 10 12:33:02 aa-i7 kernel: [  103.640539] xhci_hcd 0000:04:00.0: WARN: short transfer on control ep
Dec 10 12:33:02 aa-i7 kernel: [  103.647938] xhci_hcd 0000:04:00.0: WARN: short transfer on control ep
Dec 10 12:33:02 aa-i7 kernel: [  103.649434] xhci_hcd 0000:04:00.0: WARN: short transfer on control ep
Dec 10 12:33:04 aa-i7 kernel: [  104.925636] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:33:04 aa-i7 kernel: [  104.979532] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:33:04 aa-i7 kernel: [  105.032686] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:33:04 aa-i7 kernel: [  105.083682] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:33:04 aa-i7 kernel: [  105.397136] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:33:04 aa-i7 kernel: [  105.587256] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:33:04 aa-i7 kernel: [  105.664943] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:33:04 aa-i7 kernel: [  105.726957] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:33:05 aa-i7 kernel: [  105.757392] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:33:05 aa-i7 kernel: [  105.830643] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:33:05 aa-i7 kernel: [  105.889122] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:33:05 aa-i7 kernel: [  105.962257] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:33:05 aa-i7 kernel: [  106.148754] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:33:05 aa-i7 kernel: [  106.251087] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:33:05 aa-i7 kernel: [  106.330072] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:33:05 aa-i7 kernel: [  106.391684] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:33:05 aa-i7 kernel: [  106.421105] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:33:05 aa-i7 kernel: [  106.493411] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:33:05 aa-i7 kernel: [  106.526620] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:33:05 aa-i7 kernel: [  106.599022] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:33:06 aa-i7 kernel: [  107.014677] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:33:08 aa-i7 kernel: [  109.012447] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:33:10 aa-i7 kernel: [  111.011257] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:33:12 aa-i7 kernel: [  113.005789] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:33:14 aa-i7 kernel: [  115.004758] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:33:16 aa-i7 kernel: [  117.002761] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:33:18 aa-i7 kernel: [  118.996325] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:33:20 aa-i7 kernel: [  120.997047] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:33:22 aa-i7 kernel: [  122.990186] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:33:24 aa-i7 kernel: [  124.986924] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:33:26 aa-i7 kernel: [  126.988816] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:33:28 aa-i7 kernel: [  128.982333] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:33:30 aa-i7 kernel: [  130.980068] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:33:32 aa-i7 kernel: [  132.976847] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:33:34 aa-i7 kernel: [  134.968040] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:33:36 aa-i7 kernel: [  136.968005] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:33:38 aa-i7 kernel: [  138.966776] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:33:40 aa-i7 kernel: [  140.961016] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:33:42 aa-i7 kernel: [  142.957359] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:33:44 aa-i7 kernel: [  144.954899] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:33:46 aa-i7 kernel: [  146.954596] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:33:48 aa-i7 kernel: [  148.948882] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:33:50 aa-i7 kernel: [  150.945045] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:33:52 aa-i7 kernel: [  152.942452] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:33:54 aa-i7 kernel: [  154.938432] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:33:56 aa-i7 kernel: [  156.938260] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:33:58 aa-i7 kernel: [  158.935451] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:34:00 aa-i7 kernel: [  160.929566] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:34:02 aa-i7 kernel: [  162.929092] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:34:04 aa-i7 kernel: [  164.924980] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:34:06 aa-i7 kernel: [  166.924272] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:34:08 aa-i7 kernel: [  168.916125] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:34:10 aa-i7 kernel: [  170.915792] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:34:12 aa-i7 kernel: [  172.909941] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:34:14 aa-i7 kernel: [  174.906975] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:34:16 aa-i7 kernel: [  176.906020] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:34:18 aa-i7 kernel: [  178.900271] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:34:20 aa-i7 kernel: [  180.899982] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:34:22 aa-i7 kernel: [  182.896744] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:34:24 aa-i7 kernel: [  184.894763] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:34:26 aa-i7 kernel: [  186.889976] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:34:28 aa-i7 kernel: [  188.884111] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:34:30 aa-i7 kernel: [  190.881597] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:34:32 aa-i7 kernel: [  192.877916] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:34:34 aa-i7 kernel: [  194.877710] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:34:36 aa-i7 kernel: [  196.874875] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:34:38 aa-i7 kernel: [  198.871166] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:34:40 aa-i7 kernel: [  200.867810] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:34:42 aa-i7 kernel: [  202.865515] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:34:44 aa-i7 kernel: [  204.859101] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:34:46 aa-i7 kernel: [  206.853503] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:34:48 aa-i7 kernel: [  208.853324] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:34:50 aa-i7 kernel: [  210.852082] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:34:52 aa-i7 kernel: [  212.849212] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:34:54 aa-i7 kernel: [  214.843684] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:34:56 aa-i7 kernel: [  216.843804] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:34:58 aa-i7 kernel: [  218.838903] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:35:00 aa-i7 kernel: [  220.833116] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:35:02 aa-i7 kernel: [  222.833200] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:35:04 aa-i7 kernel: [  224.829944] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:35:06 aa-i7 kernel: [  226.827007] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:35:08 aa-i7 kernel: [  228.822678] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:35:10 aa-i7 kernel: [  230.820588] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:35:12 aa-i7 kernel: [  232.817044] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:35:14 aa-i7 kernel: [  234.813443] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:35:16 aa-i7 kernel: [  236.810109] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:35:18 aa-i7 kernel: [  238.807648] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:35:20 aa-i7 kernel: [  240.804465] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:35:22 aa-i7 kernel: [  242.800233] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:35:24 aa-i7 kernel: [  244.798000] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:35:26 aa-i7 kernel: [  246.794912] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:35:28 aa-i7 kernel: [  248.791642] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:35:30 aa-i7 kernel: [  250.787653] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:35:32 aa-i7 kernel: [  252.784880] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:35:34 aa-i7 kernel: [  254.781682] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:35:36 aa-i7 kernel: [  256.780028] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:35:38 aa-i7 kernel: [  258.772873] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:35:40 aa-i7 kernel: [  260.771789] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:35:42 aa-i7 kernel: [  262.769445] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:35:44 aa-i7 kernel: [  264.766143] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:35:46 aa-i7 kernel: [  266.763011] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:35:48 aa-i7 kernel: [  268.759909] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:35:50 aa-i7 kernel: [  270.756542] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:35:52 aa-i7 kernel: [  272.752648] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:35:54 aa-i7 kernel: [  274.743404] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:35:56 aa-i7 kernel: [  276.742075] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:35:58 aa-i7 kernel: [  278.737177] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:36:00 aa-i7 kernel: [  280.738391] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:36:02 aa-i7 kernel: [  282.737286] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:36:04 aa-i7 kernel: [  284.730012] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:36:06 aa-i7 kernel: [  286.727686] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:36:08 aa-i7 kernel: [  288.724042] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:36:10 aa-i7 kernel: [  290.722399] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:36:12 aa-i7 kernel: [  292.716689] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:36:14 aa-i7 kernel: [  294.716260] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:36:16 aa-i7 kernel: [  296.712630] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:36:18 aa-i7 kernel: [  298.708664] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:36:20 aa-i7 kernel: [  300.705315] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:36:22 aa-i7 kernel: [  302.701003] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:36:24 aa-i7 kernel: [  304.697029] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:36:26 aa-i7 kernel: [  306.693609] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:36:28 aa-i7 kernel: [  308.689948] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:36:30 aa-i7 kernel: [  310.689251] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:36:32 aa-i7 kernel: [  312.685197] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:36:34 aa-i7 kernel: [  314.684743] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:36:36 aa-i7 kernel: [  316.680905] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:36:38 aa-i7 kernel: [  318.677273] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:36:40 aa-i7 kernel: [  320.674117] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:36:42 aa-i7 kernel: [  322.669205] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:36:44 aa-i7 kernel: [  324.668784] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:36:46 aa-i7 kernel: [  326.665083] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:36:48 aa-i7 kernel: [  328.662256] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:36:50 aa-i7 kernel: [  330.657726] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:36:52 aa-i7 kernel: [  332.656401] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:36:54 aa-i7 kernel: [  334.654986] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:36:56 aa-i7 kernel: [  336.645613] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:36:58 aa-i7 kernel: [  338.644473] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:37:00 aa-i7 kernel: [  340.641224] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:37:02 aa-i7 kernel: [  342.639605] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:37:04 aa-i7 kernel: [  344.636295] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:37:06 aa-i7 kernel: [  346.633748] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:37:08 aa-i7 kernel: [  348.626910] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:37:10 aa-i7 kernel: [  350.625465] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:37:12 aa-i7 kernel: [  352.625194] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:37:14 aa-i7 kernel: [  354.621866] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:37:16 aa-i7 kernel: [  356.616099] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:37:18 aa-i7 kernel: [  358.613537] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:37:20 aa-i7 kernel: [  360.612724] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:37:22 aa-i7 kernel: [  362.607888] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:37:24 aa-i7 kernel: [  364.603378] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:37:26 aa-i7 kernel: [  366.600664] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:37:28 aa-i7 kernel: [  368.597364] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:37:30 aa-i7 kernel: [  370.592808] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:37:32 aa-i7 kernel: [  372.591268] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:37:34 aa-i7 kernel: [  374.585948] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:37:36 aa-i7 kernel: [  376.586139] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:37:38 aa-i7 kernel: [  378.582103] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:37:40 aa-i7 kernel: [  380.579917] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:37:42 aa-i7 kernel: [  382.570362] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:37:44 aa-i7 kernel: [  384.570498] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:37:46 aa-i7 kernel: [  386.570806] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:37:48 aa-i7 kernel: [  388.563919] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:37:50 aa-i7 kernel: [  390.559750] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:37:52 aa-i7 kernel: [  392.559335] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:37:54 aa-i7 kernel: [  394.555130] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:37:56 aa-i7 kernel: [  396.553580] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:37:58 aa-i7 kernel: [  398.551198] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:38:00 aa-i7 kernel: [  400.545515] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:38:02 aa-i7 kernel: [  402.545013] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:38:04 aa-i7 kernel: [  404.541894] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:38:06 aa-i7 kernel: [  406.535137] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:38:08 aa-i7 kernel: [  408.535165] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:38:10 aa-i7 kernel: [  410.529485] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:38:12 aa-i7 kernel: [  412.524225] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:38:14 aa-i7 kernel: [  414.522382] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:38:16 aa-i7 kernel: [  416.524935] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:38:18 aa-i7 kernel: [  418.519104] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:38:20 aa-i7 kernel: [  420.516237] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:38:22 aa-i7 kernel: [  422.510917] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:38:24 aa-i7 kernel: [  424.510216] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:38:26 aa-i7 kernel: [  426.506342] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:38:28 aa-i7 kernel: [  428.503903] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:38:30 aa-i7 kernel: [  430.498109] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:38:32 aa-i7 kernel: [  432.495465] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:38:34 aa-i7 kernel: [  434.490690] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:38:36 aa-i7 kernel: [  436.490777] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:38:38 aa-i7 kernel: [  438.488346] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:38:40 aa-i7 kernel: [  440.481566] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:38:42 aa-i7 kernel: [  442.479024] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:38:44 aa-i7 kernel: [  444.474091] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:38:46 aa-i7 kernel: [  446.472790] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:38:48 aa-i7 kernel: [  448.470193] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:38:50 aa-i7 kernel: [  450.468551] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:38:52 aa-i7 kernel: [  452.464774] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:38:54 aa-i7 kernel: [  454.457449] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:38:56 aa-i7 kernel: [  456.455393] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:38:58 aa-i7 kernel: [  458.456992] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:39:00 aa-i7 kernel: [  460.447542] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:39:02 aa-i7 kernel: [  462.445973] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:39:04 aa-i7 kernel: [  464.442585] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:39:06 aa-i7 kernel: [  466.493661] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:39:08 aa-i7 kernel: [  468.438931] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:39:10 aa-i7 kernel: [  470.436461] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:39:12 aa-i7 kernel: [  472.431868] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:39:14 aa-i7 kernel: [  474.425730] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:39:16 aa-i7 kernel: [  476.425430] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:39:18 aa-i7 kernel: [  478.420747] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:39:20 aa-i7 kernel: [  480.420079] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:39:22 aa-i7 kernel: [  482.415628] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:39:24 aa-i7 kernel: [  484.416723] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:39:26 aa-i7 kernel: [  486.411801] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:39:28 aa-i7 kernel: [  488.409869] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:39:30 aa-i7 kernel: [  490.408166] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:39:32 aa-i7 kernel: [  492.407000] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:39:34 aa-i7 kernel: [  494.410780] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:39:36 aa-i7 kernel: [  496.404379] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:39:38 aa-i7 kernel: [  498.398389] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:39:40 aa-i7 kernel: [  500.397992] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:39:42 aa-i7 kernel: [  502.394870] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:39:44 aa-i7 kernel: [  504.391494] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:39:46 aa-i7 kernel: [  506.391331] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:39:48 aa-i7 kernel: [  508.387368] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:39:50 aa-i7 kernel: [  510.386906] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:39:52 aa-i7 kernel: [  512.386039] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:39:54 aa-i7 kernel: [  514.379595] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:39:56 aa-i7 kernel: [  516.377857] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:39:58 aa-i7 kernel: [  518.373831] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:40:00 aa-i7 kernel: [  520.376991] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:40:02 aa-i7 kernel: [  522.373019] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:40:04 aa-i7 kernel: [  524.368246] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:40:06 aa-i7 kernel: [  526.366624] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:40:08 aa-i7 kernel: [  528.365886] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:40:10 aa-i7 kernel: [  530.362659] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:40:12 aa-i7 kernel: [  532.362689] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:40:14 aa-i7 kernel: [  534.358096] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:40:16 aa-i7 kernel: [  536.360081] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:40:18 aa-i7 kernel: [  538.355655] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:40:20 aa-i7 kernel: [  540.356465] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:40:22 aa-i7 kernel: [  542.350553] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:40:24 aa-i7 kernel: [  544.348515] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:40:26 aa-i7 kernel: [  546.346644] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:40:28 aa-i7 kernel: [  548.345594] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:40:30 aa-i7 kernel: [  550.340509] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:40:32 aa-i7 kernel: [  552.345865] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:40:34 aa-i7 kernel: [  554.337643] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:40:36 aa-i7 kernel: [  556.337607] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:40:38 aa-i7 kernel: [  558.333361] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:40:40 aa-i7 kernel: [  560.329456] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:40:42 aa-i7 kernel: [  562.333377] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:40:44 aa-i7 kernel: [  564.328298] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:40:46 aa-i7 kernel: [  566.324824] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:40:48 aa-i7 kernel: [  568.321783] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:40:50 aa-i7 kernel: [  570.320661] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:40:52 aa-i7 kernel: [  572.320480] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:40:54 aa-i7 kernel: [  574.318554] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:40:56 aa-i7 kernel: [  576.315705] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:40:58 aa-i7 kernel: [  578.312159] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:41:00 aa-i7 kernel: [  580.309374] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:41:02 aa-i7 kernel: [  582.310042] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:41:04 aa-i7 kernel: [  584.305745] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:41:06 aa-i7 kernel: [  586.305234] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:41:08 aa-i7 kernel: [  588.303327] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:41:10 aa-i7 kernel: [  590.301449] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:41:12 aa-i7 kernel: [  592.296336] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:41:14 aa-i7 kernel: [  594.291529] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:41:16 aa-i7 kernel: [  596.291552] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:41:18 aa-i7 kernel: [  598.292100] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:41:20 aa-i7 kernel: [  600.290018] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:41:22 aa-i7 kernel: [  602.285343] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:41:24 aa-i7 kernel: [  604.286407] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:41:26 aa-i7 kernel: [  606.283398] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:41:28 aa-i7 kernel: [  608.281340] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:41:30 aa-i7 kernel: [  610.279588] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:41:32 aa-i7 kernel: [  612.276332] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:41:34 aa-i7 kernel: [  614.273522] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:41:36 aa-i7 kernel: [  616.272143] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:41:38 aa-i7 kernel: [  618.269901] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:41:40 aa-i7 kernel: [  620.268582] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:41:42 aa-i7 kernel: [  622.263663] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:41:44 aa-i7 kernel: [  624.264403] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:41:46 aa-i7 kernel: [  626.261742] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:41:48 aa-i7 kernel: [  628.259821] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:41:50 aa-i7 kernel: [  630.257499] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:41:52 aa-i7 kernel: [  632.255164] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:41:54 aa-i7 kernel: [  634.254003] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:41:56 aa-i7 kernel: [  636.250871] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:41:58 aa-i7 kernel: [  638.247941] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:42:00 aa-i7 kernel: [  640.243729] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:42:02 aa-i7 kernel: [  642.238668] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:42:04 aa-i7 kernel: [  644.239408] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:42:06 aa-i7 kernel: [  646.239315] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:42:08 aa-i7 kernel: [  648.237127] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:42:10 aa-i7 kernel: [  650.232757] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:42:12 aa-i7 kernel: [  652.229993] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:42:14 aa-i7 kernel: [  654.230908] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:42:16 aa-i7 kernel: [  656.228584] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:42:18 aa-i7 kernel: [  658.226108] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:42:20 aa-i7 kernel: [  660.219099] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:42:22 aa-i7 kernel: [  662.221575] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:42:24 aa-i7 kernel: [  664.219620] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:42:26 aa-i7 kernel: [  666.217447] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:42:28 aa-i7 kernel: [  668.215761] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:42:30 aa-i7 kernel: [  670.213021] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:42:32 aa-i7 kernel: [  672.210630] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:42:34 aa-i7 kernel: [  674.208635] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:42:36 aa-i7 kernel: [  676.206360] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:42:38 aa-i7 kernel: [  678.204483] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:42:40 aa-i7 kernel: [  680.202317] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:42:42 aa-i7 kernel: [  682.197524] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:42:44 aa-i7 kernel: [  684.198045] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:42:46 aa-i7 kernel: [  686.195577] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:42:48 aa-i7 kernel: [  688.188538] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:42:50 aa-i7 kernel: [  690.193398] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:42:52 aa-i7 kernel: [  692.186650] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:42:54 aa-i7 kernel: [  694.184162] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:42:56 aa-i7 kernel: [  696.184979] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:42:58 aa-i7 kernel: [  698.182584] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:43:00 aa-i7 kernel: [  700.181685] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:43:02 aa-i7 kernel: [  702.178293] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:43:04 aa-i7 kernel: [  704.175541] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:43:06 aa-i7 kernel: [  706.174448] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:43:08 aa-i7 kernel: [  708.171131] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:43:10 aa-i7 kernel: [  710.171089] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:43:12 aa-i7 kernel: [  712.167138] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:43:14 aa-i7 kernel: [  714.164955] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:43:16 aa-i7 kernel: [  716.162764] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:43:18 aa-i7 kernel: [  718.160688] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:43:20 aa-i7 kernel: [  720.160898] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:43:22 aa-i7 kernel: [  722.156543] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:43:24 aa-i7 kernel: [  724.153633] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:43:26 aa-i7 kernel: [  726.151684] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:43:28 aa-i7 kernel: [  728.149589] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:43:30 aa-i7 kernel: [  730.147526] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:43:32 aa-i7 kernel: [  732.145046] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:43:34 aa-i7 kernel: [  734.142608] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:43:36 aa-i7 kernel: [  736.141302] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:43:38 aa-i7 kernel: [  738.139106] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:43:40 aa-i7 kernel: [  740.136912] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:43:42 aa-i7 kernel: [  742.133767] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:43:44 aa-i7 kernel: [  744.132174] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:43:46 aa-i7 kernel: [  746.129775] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:43:48 aa-i7 kernel: [  748.127232] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:43:50 aa-i7 kernel: [  750.125988] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:43:52 aa-i7 kernel: [  752.122891] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:43:54 aa-i7 kernel: [  754.120967] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:43:56 aa-i7 kernel: [  756.118946] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:43:58 aa-i7 kernel: [  758.116624] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:44:00 aa-i7 kernel: [  760.112183] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:44:02 aa-i7 kernel: [  762.111735] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:44:04 aa-i7 kernel: [  764.110405] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:44:06 aa-i7 kernel: [  766.108492] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:44:08 aa-i7 kernel: [  768.105283] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:44:10 aa-i7 kernel: [  770.103422] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:44:12 aa-i7 kernel: [  772.101588] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:44:14 aa-i7 kernel: [  774.099715] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:44:16 aa-i7 kernel: [  776.096703] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:44:18 aa-i7 kernel: [  778.094807] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:44:20 aa-i7 kernel: [  780.093007] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:44:22 aa-i7 kernel: [  782.090038] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:44:24 aa-i7 kernel: [  784.089097] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:44:26 aa-i7 kernel: [  786.085743] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:44:28 aa-i7 kernel: [  788.083452] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:44:30 aa-i7 kernel: [  790.081993] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:44:32 aa-i7 kernel: [  792.079742] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:44:34 aa-i7 kernel: [  794.078815] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:44:36 aa-i7 kernel: [  796.074577] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:44:38 aa-i7 kernel: [  798.073125] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:44:40 aa-i7 kernel: [  800.070798] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:44:42 aa-i7 kernel: [  802.068555] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:44:44 aa-i7 kernel: [  804.068312] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:44:46 aa-i7 kernel: [  806.063506] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:44:48 aa-i7 kernel: [  808.062206] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:44:50 aa-i7 kernel: [  810.059502] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:44:52 aa-i7 kernel: [  812.056229] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:44:54 aa-i7 kernel: [  814.055180] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:44:56 aa-i7 kernel: [  816.052746] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:44:58 aa-i7 kernel: [  818.050502] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:45:00 aa-i7 kernel: [  820.048849] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:45:02 aa-i7 kernel: [  822.046046] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:45:04 aa-i7 kernel: [  824.044580] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:45:06 aa-i7 kernel: [  826.041696] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:45:08 aa-i7 kernel: [  828.039521] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:45:10 aa-i7 kernel: [  830.037459] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:45:12 aa-i7 kernel: [  832.035654] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:45:14 aa-i7 kernel: [  834.033727] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:45:16 aa-i7 kernel: [  836.031277] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:45:18 aa-i7 kernel: [  838.028974] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:45:20 aa-i7 kernel: [  840.026482] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:45:22 aa-i7 kernel: [  842.023959] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:45:24 aa-i7 kernel: [  844.020367] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:45:26 aa-i7 kernel: [  846.020433] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:45:28 aa-i7 kernel: [  848.018055] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:45:30 aa-i7 kernel: [  850.013383] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:45:32 aa-i7 kernel: [  852.012973] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:45:34 aa-i7 kernel: [  854.011723] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:45:36 aa-i7 kernel: [  856.009494] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:45:38 aa-i7 kernel: [  858.006538] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:45:40 aa-i7 kernel: [  860.004954] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:45:42 aa-i7 kernel: [  862.002003] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:45:44 aa-i7 kernel: [  864.000340] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:45:46 aa-i7 kernel: [  865.995179] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:45:48 aa-i7 kernel: [  867.996162] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:45:50 aa-i7 kernel: [  869.994224] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:45:52 aa-i7 kernel: [  871.991515] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:45:54 aa-i7 kernel: [  873.986781] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:45:56 aa-i7 kernel: [  875.986615] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:45:58 aa-i7 kernel: [  877.984490] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:46:00 aa-i7 kernel: [  879.982561] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:46:02 aa-i7 kernel: [  881.980176] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:46:04 aa-i7 kernel: [  883.975709] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:46:06 aa-i7 kernel: [  885.975537] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:46:08 aa-i7 kernel: [  887.973592] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:46:10 aa-i7 kernel: [  889.971802] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:46:12 aa-i7 kernel: [  891.969307] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:46:14 aa-i7 kernel: [  893.967310] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:46:16 aa-i7 kernel: [  895.965039] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:46:18 aa-i7 kernel: [  897.960619] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:46:20 aa-i7 kernel: [  899.961212] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:46:22 aa-i7 kernel: [  901.958527] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:46:24 aa-i7 kernel: [  903.954021] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:46:26 aa-i7 kernel: [  905.951955] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:46:28 aa-i7 kernel: [  907.949214] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:46:30 aa-i7 kernel: [  909.950124] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:46:32 aa-i7 kernel: [  911.948084] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:46:34 aa-i7 kernel: [  913.945755] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:46:36 aa-i7 kernel: [  915.943571] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:46:38 aa-i7 kernel: [  917.940675] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:46:40 aa-i7 kernel: [  919.933926] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:46:42 aa-i7 kernel: [  921.936681] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:46:44 aa-i7 kernel: [  923.936559] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:46:46 aa-i7 kernel: [  925.932306] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:46:48 aa-i7 kernel: [  927.930108] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:46:50 aa-i7 kernel: [  929.925297] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:46:52 aa-i7 kernel: [  931.925975] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:46:54 aa-i7 kernel: [  933.925344] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:46:56 aa-i7 kernel: [  935.918515] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:46:58 aa-i7 kernel: [  937.919012] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:47:00 aa-i7 kernel: [  939.914387] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:47:02 aa-i7 kernel: [  941.915076] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:47:04 aa-i7 kernel: [  943.913871] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:47:06 aa-i7 kernel: [  945.907494] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:47:08 aa-i7 kernel: [  947.903072] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:47:10 aa-i7 kernel: [  949.903549] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:47:12 aa-i7 kernel: [  951.901057] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:47:14 aa-i7 kernel: [  953.901351] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:47:16 aa-i7 kernel: [  955.900015] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:47:18 aa-i7 kernel: [  957.897344] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:47:20 aa-i7 kernel: [  959.893083] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:47:22 aa-i7 kernel: [  961.892794] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:47:24 aa-i7 kernel: [  963.890553] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:47:26 aa-i7 kernel: [  965.888690] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:47:28 aa-i7 kernel: [  967.884078] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:47:30 aa-i7 kernel: [  969.881528] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:47:32 aa-i7 kernel: [  971.878781] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:47:34 aa-i7 kernel: [  973.879411] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:47:36 aa-i7 kernel: [  975.877185] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:47:38 aa-i7 kernel: [  977.875187] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:47:40 aa-i7 kernel: [  979.875215] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:47:42 aa-i7 kernel: [  981.870678] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:47:44 aa-i7 kernel: [  983.868407] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:47:46 aa-i7 kernel: [  985.863804] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:47:48 aa-i7 kernel: [  987.862276] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:47:50 aa-i7 kernel: [  989.863544] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:47:52 aa-i7 kernel: [  991.857642] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:47:54 aa-i7 kernel: [  993.858010] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:47:56 aa-i7 kernel: [  995.855516] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:47:58 aa-i7 kernel: [  997.850157] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:48:00 aa-i7 kernel: [  999.852029] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:48:02 aa-i7 kernel: [ 1001.846036] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:48:04 aa-i7 kernel: [ 1003.844469] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:48:06 aa-i7 kernel: [ 1005.844249] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:48:08 aa-i7 kernel: [ 1007.841812] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:48:10 aa-i7 kernel: [ 1009.840274] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:48:12 aa-i7 kernel: [ 1011.833380] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:48:14 aa-i7 kernel: [ 1013.835770] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:48:16 aa-i7 kernel: [ 1015.832010] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:48:18 aa-i7 kernel: [ 1017.831043] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:48:20 aa-i7 kernel: [ 1019.826465] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:48:22 aa-i7 kernel: [ 1021.823920] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:48:24 aa-i7 kernel: [ 1023.822011] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:48:26 aa-i7 kernel: [ 1025.820075] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:48:28 aa-i7 kernel: [ 1027.820396] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:48:30 aa-i7 kernel: [ 1029.817990] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:48:32 aa-i7 kernel: [ 1031.815907] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:48:34 aa-i7 kernel: [ 1033.813931] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:48:36 aa-i7 kernel: [ 1035.813155] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:48:38 aa-i7 kernel: [ 1037.808699] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:48:40 aa-i7 kernel: [ 1039.804802] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:48:42 aa-i7 kernel: [ 1041.804859] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:48:44 aa-i7 kernel: [ 1043.803024] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:48:46 aa-i7 kernel: [ 1045.802909] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:48:48 aa-i7 kernel: [ 1047.798278] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:48:50 aa-i7 kernel: [ 1049.796058] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:48:52 aa-i7 kernel: [ 1051.794086] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:48:54 aa-i7 kernel: [ 1053.791882] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:48:56 aa-i7 kernel: [ 1055.789807] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:48:58 aa-i7 kernel: [ 1057.787523] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:49:00 aa-i7 kernel: [ 1059.784734] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:49:02 aa-i7 kernel: [ 1061.782718] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:49:04 aa-i7 kernel: [ 1063.780292] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:49:06 aa-i7 kernel: [ 1065.779008] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:49:08 aa-i7 kernel: [ 1067.776023] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:49:10 aa-i7 kernel: [ 1069.774328] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:49:12 aa-i7 kernel: [ 1071.772522] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:49:14 aa-i7 kernel: [ 1073.770069] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:49:16 aa-i7 kernel: [ 1075.765607] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:49:18 aa-i7 kernel: [ 1077.762908] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:49:20 aa-i7 kernel: [ 1079.763024] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:49:22 aa-i7 kernel: [ 1081.758357] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:49:24 aa-i7 kernel: [ 1083.759258] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:49:26 aa-i7 kernel: [ 1085.759295] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:49:28 aa-i7 kernel: [ 1087.752472] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:49:30 aa-i7 kernel: [ 1089.751733] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:49:32 aa-i7 kernel: [ 1091.747076] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:49:34 aa-i7 kernel: [ 1093.745758] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:49:36 aa-i7 kernel: [ 1095.747031] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:49:38 aa-i7 kernel: [ 1097.743624] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:49:40 aa-i7 kernel: [ 1099.741119] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:49:42 aa-i7 kernel: [ 1101.739355] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:49:44 aa-i7 kernel: [ 1103.734608] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:49:46 aa-i7 kernel: [ 1105.733648] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:49:48 aa-i7 kernel: [ 1107.732381] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:49:50 aa-i7 kernel: [ 1109.728290] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:49:52 aa-i7 kernel: [ 1111.725958] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:49:54 aa-i7 kernel: [ 1113.723480] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:49:56 aa-i7 kernel: [ 1115.720748] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:49:58 aa-i7 kernel: [ 1117.718749] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:50:00 aa-i7 kernel: [ 1119.719514] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:50:02 aa-i7 kernel: [ 1121.717309] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:50:04 aa-i7 kernel: [ 1123.714858] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:50:06 aa-i7 kernel: [ 1125.710414] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:50:08 aa-i7 kernel: [ 1127.710639] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:50:10 aa-i7 kernel: [ 1129.708199] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:50:12 aa-i7 kernel: [ 1131.706216] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:50:14 aa-i7 kernel: [ 1133.701577] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:50:16 aa-i7 kernel: [ 1135.701380] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:50:18 aa-i7 kernel: [ 1137.697902] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:50:20 aa-i7 kernel: [ 1139.697660] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:50:22 aa-i7 kernel: [ 1141.697087] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:50:24 aa-i7 kernel: [ 1143.690523] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:50:26 aa-i7 kernel: [ 1145.688201] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:50:28 aa-i7 kernel: [ 1147.689155] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:50:30 aa-i7 kernel: [ 1149.685944] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:50:32 aa-i7 kernel: [ 1151.685389] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:50:34 aa-i7 kernel: [ 1153.682127] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:50:36 aa-i7 kernel: [ 1155.680090] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:50:38 aa-i7 kernel: [ 1157.678122] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:50:40 aa-i7 kernel: [ 1159.675083] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:50:42 aa-i7 kernel: [ 1161.675010] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:50:44 aa-i7 kernel: [ 1163.670418] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:50:46 aa-i7 kernel: [ 1165.669198] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:50:48 aa-i7 kernel: [ 1167.667507] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:50:50 aa-i7 kernel: [ 1169.664216] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:50:52 aa-i7 kernel: [ 1171.662357] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:50:54 aa-i7 kernel: [ 1173.659659] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:50:56 aa-i7 kernel: [ 1175.657515] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:50:58 aa-i7 kernel: [ 1177.653902] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:51:00 aa-i7 kernel: [ 1179.653570] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:51:02 aa-i7 kernel: [ 1181.653473] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:51:04 aa-i7 kernel: [ 1183.649236] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:51:06 aa-i7 kernel: [ 1185.646899] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:51:08 aa-i7 kernel: [ 1187.642614] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:51:10 aa-i7 kernel: [ 1189.639987] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:51:12 aa-i7 kernel: [ 1191.638110] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:51:14 aa-i7 kernel: [ 1193.637676] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:51:16 aa-i7 kernel: [ 1195.635712] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:51:18 aa-i7 kernel: [ 1197.634226] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:51:20 aa-i7 kernel: [ 1199.632009] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:51:22 aa-i7 kernel: [ 1201.631525] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:51:24 aa-i7 kernel: [ 1203.627188] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:51:26 aa-i7 kernel: [ 1205.624781] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:51:28 aa-i7 kernel: [ 1207.623159] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:51:30 aa-i7 kernel: [ 1209.620757] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:51:32 aa-i7 kernel: [ 1211.620856] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:51:34 aa-i7 kernel: [ 1213.616211] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:51:36 aa-i7 kernel: [ 1215.614284] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:51:38 aa-i7 kernel: [ 1217.611831] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:51:40 aa-i7 kernel: [ 1219.609223] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:51:42 aa-i7 kernel: [ 1221.608123] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:51:44 aa-i7 kernel: [ 1223.603427] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:51:46 aa-i7 kernel: [ 1225.603323] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:51:48 aa-i7 kernel: [ 1227.598990] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:51:50 aa-i7 kernel: [ 1229.598976] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:51:52 aa-i7 kernel: [ 1231.598671] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:51:54 aa-i7 kernel: [ 1233.591700] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:51:56 aa-i7 kernel: [ 1235.591932] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:51:58 aa-i7 kernel: [ 1237.587308] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:52:00 aa-i7 kernel: [ 1239.587352] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:52:02 aa-i7 kernel: [ 1241.587011] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:52:04 aa-i7 kernel: [ 1243.580645] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:52:06 aa-i7 kernel: [ 1245.581387] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:52:08 aa-i7 kernel: [ 1247.578768] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:52:10 aa-i7 kernel: [ 1249.576811] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:52:12 aa-i7 kernel: [ 1251.575989] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:52:14 aa-i7 kernel: [ 1253.572349] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:52:16 aa-i7 kernel: [ 1255.568106] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:52:18 aa-i7 kernel: [ 1257.567706] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:52:20 aa-i7 kernel: [ 1259.565408] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:52:22 aa-i7 kernel: [ 1261.564839] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:52:24 aa-i7 kernel: [ 1263.561214] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:52:26 aa-i7 kernel: [ 1265.558737] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:52:28 aa-i7 kernel: [ 1267.557229] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:52:30 aa-i7 kernel: [ 1269.554746] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:52:32 aa-i7 kernel: [ 1271.554453] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:52:34 aa-i7 kernel: [ 1273.549942] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:52:36 aa-i7 kernel: [ 1275.547899] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:52:38 aa-i7 kernel: [ 1277.546533] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:52:40 aa-i7 kernel: [ 1279.543975] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:52:42 aa-i7 kernel: [ 1281.543785] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:52:44 aa-i7 kernel: [ 1283.539007] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:52:46 aa-i7 kernel: [ 1285.536805] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:52:48 aa-i7 kernel: [ 1287.534702] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:52:50 aa-i7 kernel: [ 1289.533102] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:52:52 aa-i7 kernel: [ 1291.530305] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:52:54 aa-i7 kernel: [ 1293.528165] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:52:56 aa-i7 kernel: [ 1295.526197] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:52:58 aa-i7 kernel: [ 1297.524475] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:53:00 aa-i7 kernel: [ 1299.521230] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:53:02 aa-i7 kernel: [ 1301.519243] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:53:04 aa-i7 kernel: [ 1303.517025] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:53:06 aa-i7 kernel: [ 1305.514831] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:53:08 aa-i7 kernel: [ 1307.513428] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:53:10 aa-i7 kernel: [ 1309.510437] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:53:12 aa-i7 kernel: [ 1311.509104] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:53:14 aa-i7 kernel: [ 1313.506643] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:53:16 aa-i7 kernel: [ 1315.546649] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:53:18 aa-i7 kernel: [ 1317.502514] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:53:20 aa-i7 kernel: [ 1319.499616] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:53:22 aa-i7 kernel: [ 1321.497254] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:53:24 aa-i7 kernel: [ 1323.494938] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:53:26 aa-i7 kernel: [ 1325.493417] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:53:28 aa-i7 kernel: [ 1327.490496] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:53:30 aa-i7 kernel: [ 1329.488910] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:53:32 aa-i7 kernel: [ 1331.486794] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:53:34 aa-i7 kernel: [ 1333.484776] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:53:36 aa-i7 kernel: [ 1335.482789] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:53:38 aa-i7 kernel: [ 1337.479623] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:53:40 aa-i7 kernel: [ 1339.478122] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:53:42 aa-i7 kernel: [ 1341.476178] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:53:44 aa-i7 kernel: [ 1343.473169] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:53:46 aa-i7 kernel: [ 1345.472324] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:53:48 aa-i7 kernel: [ 1347.469311] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:53:50 aa-i7 kernel: [ 1349.467292] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:53:52 aa-i7 kernel: [ 1351.465021] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:53:54 aa-i7 kernel: [ 1353.462830] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:53:56 aa-i7 kernel: [ 1355.461859] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:53:58 aa-i7 kernel: [ 1357.457693] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:54:00 aa-i7 kernel: [ 1359.455370] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:54:02 aa-i7 kernel: [ 1361.454366] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:54:04 aa-i7 kernel: [ 1363.451245] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:54:06 aa-i7 kernel: [ 1365.451374] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:54:08 aa-i7 kernel: [ 1367.447345] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:54:10 aa-i7 kernel: [ 1369.444662] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:54:12 aa-i7 kernel: [ 1371.442400] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:54:14 aa-i7 kernel: [ 1373.440244] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:54:16 aa-i7 kernel: [ 1375.438007] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:54:18 aa-i7 kernel: [ 1377.434148] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:54:20 aa-i7 kernel: [ 1379.433722] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:54:22 aa-i7 kernel: [ 1381.431788] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:54:24 aa-i7 kernel: [ 1383.429658] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:54:26 aa-i7 kernel: [ 1385.427347] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:54:28 aa-i7 kernel: [ 1387.425190] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:54:30 aa-i7 kernel: [ 1389.423015] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:54:32 aa-i7 kernel: [ 1391.420874] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:54:34 aa-i7 kernel: [ 1393.418700] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:54:36 aa-i7 kernel: [ 1395.419153] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:54:38 aa-i7 kernel: [ 1397.414099] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:54:40 aa-i7 kernel: [ 1399.412317] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:54:42 aa-i7 kernel: [ 1401.410217] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:54:44 aa-i7 kernel: [ 1403.408026] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:54:46 aa-i7 kernel: [ 1405.405933] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:54:48 aa-i7 kernel: [ 1407.403515] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:54:50 aa-i7 kernel: [ 1409.400925] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:54:52 aa-i7 kernel: [ 1411.398738] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:54:54 aa-i7 kernel: [ 1413.396365] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:54:56 aa-i7 kernel: [ 1415.394408] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:54:58 aa-i7 kernel: [ 1417.391776] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:55:00 aa-i7 kernel: [ 1419.390076] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:55:02 aa-i7 kernel: [ 1421.387762] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:55:04 aa-i7 kernel: [ 1423.385779] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:55:06 aa-i7 kernel: [ 1425.383917] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:55:08 aa-i7 kernel: [ 1427.381714] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:55:10 aa-i7 kernel: [ 1429.379329] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:55:12 aa-i7 kernel: [ 1431.376645] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:55:14 aa-i7 kernel: [ 1433.374693] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:55:16 aa-i7 kernel: [ 1435.373011] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:55:18 aa-i7 kernel: [ 1437.370141] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:55:20 aa-i7 kernel: [ 1439.368902] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:55:22 aa-i7 kernel: [ 1441.365808] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:55:24 aa-i7 kernel: [ 1443.363629] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:55:26 aa-i7 kernel: [ 1445.361288] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:55:28 aa-i7 kernel: [ 1447.359248] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:55:30 aa-i7 kernel: [ 1449.358283] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:55:32 aa-i7 kernel: [ 1451.354991] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:55:34 aa-i7 kernel: [ 1453.352938] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:55:36 aa-i7 kernel: [ 1455.351175] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:55:38 aa-i7 kernel: [ 1457.348690] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:55:40 aa-i7 kernel: [ 1459.347882] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:55:42 aa-i7 kernel: [ 1461.343501] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:55:44 aa-i7 kernel: [ 1463.342062] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:55:46 aa-i7 kernel: [ 1465.339666] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:55:48 aa-i7 kernel: [ 1467.337624] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:55:50 aa-i7 kernel: [ 1469.334983] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:55:52 aa-i7 kernel: [ 1471.332609] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:55:54 aa-i7 kernel: [ 1473.330491] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:55:56 aa-i7 kernel: [ 1475.328295] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:55:58 aa-i7 kernel: [ 1477.325898] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:56:00 aa-i7 kernel: [ 1479.324477] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:56:02 aa-i7 kernel: [ 1481.322252] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:56:04 aa-i7 kernel: [ 1483.319804] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:56:06 aa-i7 kernel: [ 1485.318190] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:56:08 aa-i7 kernel: [ 1487.315090] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:56:10 aa-i7 kernel: [ 1489.313697] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:56:12 aa-i7 kernel: [ 1491.311462] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:56:14 aa-i7 kernel: [ 1493.309130] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:56:16 aa-i7 kernel: [ 1495.306604] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:56:18 aa-i7 kernel: [ 1497.304714] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:56:20 aa-i7 kernel: [ 1499.300271] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:56:22 aa-i7 kernel: [ 1501.297210] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:56:24 aa-i7 kernel: [ 1503.295388] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:56:26 aa-i7 kernel: [ 1505.295587] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:56:28 aa-i7 kernel: [ 1507.293307] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:56:30 aa-i7 kernel: [ 1509.293176] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:56:32 aa-i7 kernel: [ 1511.286776] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:56:34 aa-i7 kernel: [ 1513.286283] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:56:36 aa-i7 kernel: [ 1515.282659] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:56:38 aa-i7 kernel: [ 1517.282107] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:56:40 aa-i7 kernel: [ 1519.276822] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:56:42 aa-i7 kernel: [ 1521.278272] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:56:44 aa-i7 kernel: [ 1523.276077] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:56:46 aa-i7 kernel: [ 1525.273710] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:56:48 aa-i7 kernel: [ 1527.271219] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:56:50 aa-i7 kernel: [ 1529.270057] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:56:52 aa-i7 kernel: [ 1531.265338] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:56:54 aa-i7 kernel: [ 1533.265242] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:56:56 aa-i7 kernel: [ 1535.260482] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:56:58 aa-i7 kernel: [ 1537.255425] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:57:00 aa-i7 kernel: [ 1539.252682] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:57:02 aa-i7 kernel: [ 1541.256877] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:57:04 aa-i7 kernel: [ 1543.253696] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:57:06 aa-i7 kernel: [ 1545.251684] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:57:08 aa-i7 kernel: [ 1547.249198] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:57:10 aa-i7 kernel: [ 1549.247380] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:57:12 aa-i7 kernel: [ 1551.242128] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:57:14 aa-i7 kernel: [ 1553.242662] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:57:16 aa-i7 kernel: [ 1555.235608] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:59:45 aa-i7 kernel: [    1.685955] pci 0000:04:00.0: [1033:0194] type 0 class 0x000c03
Dec 10 12:59:45 aa-i7 kernel: [    1.685988] pci 0000:04:00.0: reg 10: [mem 0xe5b00000-0xe5b01fff 64bit]
Dec 10 12:59:45 aa-i7 kernel: [    1.686165] pci 0000:04:00.0: PME# supported from D0 D3hot
Dec 10 12:59:45 aa-i7 kernel: [    1.686173] pci 0000:04:00.0: PME# disabled
Dec 10 12:59:45 aa-i7 kernel: [    2.447070] xhci_hcd 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Dec 10 12:59:45 aa-i7 kernel: [    2.447087] xhci_hcd 0000:04:00.0: setting latency timer to 64
Dec 10 12:59:45 aa-i7 kernel: [    2.447091] xhci_hcd 0000:04:00.0: xHCI Host Controller
Dec 10 12:59:45 aa-i7 kernel: [    2.447135] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 3
Dec 10 12:59:45 aa-i7 kernel: [    2.447314] xhci_hcd 0000:04:00.0: irq 18, io mem 0xe5b00000
Dec 10 12:59:45 aa-i7 kernel: [    2.447372] xhci_hcd 0000:04:00.0: irq 43 for MSI/MSI-X
Dec 10 12:59:45 aa-i7 kernel: [    2.447376] xhci_hcd 0000:04:00.0: irq 44 for MSI/MSI-X
Dec 10 12:59:45 aa-i7 kernel: [    2.447381] xhci_hcd 0000:04:00.0: irq 45 for MSI/MSI-X
Dec 10 12:59:45 aa-i7 kernel: [    2.447385] xhci_hcd 0000:04:00.0: irq 46 for MSI/MSI-X
Dec 10 12:59:45 aa-i7 kernel: [    2.447390] xhci_hcd 0000:04:00.0: irq 47 for MSI/MSI-X
Dec 10 12:59:45 aa-i7 kernel: [    2.447600] xhci_hcd 0000:04:00.0: xHCI Host Controller
Dec 10 12:59:45 aa-i7 kernel: [    2.447619] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 4
Dec 10 12:59:45 aa-i7 kernel: [    3.269585] xhci_hcd 0000:04:00.0: WARN: short transfer on control ep
Dec 10 12:59:45 aa-i7 kernel: [    3.270867] xhci_hcd 0000:04:00.0: WARN: short transfer on control ep
Dec 10 12:59:45 aa-i7 kernel: [    3.272078] xhci_hcd 0000:04:00.0: WARN: short transfer on control ep
Dec 10 12:59:45 aa-i7 kernel: [    3.273474] xhci_hcd 0000:04:00.0: WARN: short transfer on control ep
Dec 10 12:59:45 aa-i7 kernel: [    3.280723] xhci_hcd 0000:04:00.0: WARN: short transfer on control ep
Dec 10 12:59:45 aa-i7 kernel: [    3.282218] xhci_hcd 0000:04:00.0: WARN: short transfer on control ep
Dec 10 12:59:45 aa-i7 kernel: [    4.411741] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:59:45 aa-i7 kernel: [    4.465438] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:59:45 aa-i7 kernel: [    4.519227] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:59:45 aa-i7 kernel: [   20.128269] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:59:45 aa-i7 kernel: [   20.584277] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:59:45 aa-i7 kernel: [   20.651548] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:59:45 aa-i7 kernel: [   20.676069] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:59:45 aa-i7 kernel: [   20.737666] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:59:45 aa-i7 kernel: [   20.762581] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:59:45 aa-i7 kernel: [   20.834902] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:59:45 aa-i7 kernel: [   20.894451] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:59:45 aa-i7 kernel: [   20.966598] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:59:45 aa-i7 kernel: [   22.078924] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:59:45 aa-i7 kernel: [   22.158144] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 12:59:45 aa-i7 kernel: [   22.459059] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 13:00:43 aa-i7 kernel: [   80.097546] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 13:00:43 aa-i7 kernel: [   80.137318] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 13:00:43 aa-i7 kernel: [   80.250461] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 13:00:43 aa-i7 kernel: [   80.274913] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 13:00:43 aa-i7 kernel: [   80.299116] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 13:00:43 aa-i7 kernel: [   80.323457] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 13:00:43 aa-i7 kernel: [   80.416888] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 13:00:44 aa-i7 kernel: [   81.220052] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 13:00:44 aa-i7 kernel: [   81.333413] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 13:01:57 aa-i7 kernel: [  154.225740] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Dec 10 13:18:28 aa-i7 kernel: [    1.689954] pci 0000:04:00.0: [1033:0194] type 0 class 0x000c03
Dec 10 13:18:28 aa-i7 kernel: [    1.689984] pci 0000:04:00.0: reg 10: [mem 0xe5b00000-0xe5b01fff 64bit]
Dec 10 13:18:28 aa-i7 kernel: [    1.690166] pci 0000:04:00.0: PME# supported from D0 D3hot
Dec 10 13:18:28 aa-i7 kernel: [    1.690174] pci 0000:04:00.0: PME# disabled
Dec 10 13:18:28 aa-i7 kernel: [    2.443813] xhci_hcd 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Dec 10 13:18:28 aa-i7 kernel: [    2.443843] xhci_hcd 0000:04:00.0: setting latency timer to 64
Dec 10 13:18:28 aa-i7 kernel: [    2.443848] xhci_hcd 0000:04:00.0: xHCI Host Controller
Dec 10 13:18:28 aa-i7 kernel: [    2.443902] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 3
Dec 10 13:18:28 aa-i7 kernel: [    2.444076] xhci_hcd 0000:04:00.0: irq 18, io mem 0xe5b00000
Dec 10 13:18:28 aa-i7 kernel: [    2.444143] xhci_hcd 0000:04:00.0: irq 43 for MSI/MSI-X
Dec 10 13:18:28 aa-i7 kernel: [    2.444148] xhci_hcd 0000:04:00.0: irq 44 for MSI/MSI-X
Dec 10 13:18:28 aa-i7 kernel: [    2.444154] xhci_hcd 0000:04:00.0: irq 45 for MSI/MSI-X
Dec 10 13:18:28 aa-i7 kernel: [    2.444158] xhci_hcd 0000:04:00.0: irq 46 for MSI/MSI-X
Dec 10 13:18:28 aa-i7 kernel: [    2.444162] xhci_hcd 0000:04:00.0: irq 47 for MSI/MSI-X
Dec 10 13:18:28 aa-i7 kernel: [    2.444383] xhci_hcd 0000:04:00.0: xHCI Host Controller
Dec 10 13:18:28 aa-i7 kernel: [    2.444410] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 4
aa@aa-i7:~$ 
[\CODE]


the USB3.0 driver is loaded:

aa@aa-i7:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 413c:8187 Dell Computer Corp. DW375 Bluetooth Module
Bus 001 Device 004: ID 05ca:181c Ricoh Co., Ltd 
Bus 002 Device 003: ID 0a5c:5800 Broadcom Corp. BCM5880 Secure Applications Processor
aa@aa-i7:~$ 

and in more details:

[CODE]
aa@aa-i7:~$ lsusb -v -s 004:001

Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
libusb couldn't open USB device /dev/bus/usb/004/001: Permission denied.
libusb requires write access to USB device nodes.
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               3.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         3 
  bMaxPacketSize0         9
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0003 3.0 root hub
  bcdDevice            3.00
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           31
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
        bMaxBurst               0
aa@aa-i7:~$ 
[\CODE]


2. Initially when I was plugging in the USB3.0 HDD (Iomega 1Tb), it was not recognised (it was only recognised on the boot), but I found in https://help.ubuntu.com/community/ExpressCard
that I need to get the module acpiphp  loaded (sudo modprobe acpiphp) and then the HDD is recognised when plugged in.

3. Now I have HDD working, but the speed is only like for USB2.0:  it copies the 10Gb file with about 38Mb/sec speed:

[CODE]
aa@aa-i7:~$ time cp /media/Vbox-disks/WinXP.vdi /media/Iomega_HDD/

real	4m30.100s
user	0m0.248s
sys	0m27.646s
aa@aa-i7:~$ ls -all /media/Vbox-disks/WinXP.vdi
-rw------- 1 aa aa 10277134848 2011-12-06 12:14 /media/Vbox-disks/WinXP.vdi
[\CODE]

The read time is also like for USB2.0:

[CODE]
aa@aa-i7:~$ sudo hdparm -t /dev/sdb1
[sudo] password for aa: 

/dev/sdb1:
 Timing buffered disk reads: 104 MB in  3.03 seconds =  34.38 MB/sec
[\CODE]


4. I found in http://ubuntuforums.org/showthread.php?t=1680278  that I need to add pci=nomsi in the grub configuration:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=nomsi"

I tried this, but it did not help, so I changed it back.



I am now out of ideas about how to make this USB3.0 working at least a bit fast than USB2.0.

Can you please help?

---

### Post by Mark Phelps on 2011-12-12
I have a Sony USB 3.0 port on the motherboard on my PC, and at first, it only operated at USB 2.0 speeds.  Even worse, it would disconnect part way through a file transfer -- making it effectively even slower than USB 1.0 speeds!

I was able to fix the problem by flashing the firmware on the USB controller.  But I had to do that in Win7, as there was no Linux-based app I could use.  I also had to update the Sony Renesas USB 3.0 driver.

Since then, I can get USB 3.0 speeds and I don't get disconnects anymore.

---

### Post by aa-hcl on 2011-12-13
Hi,

many thanks - I will try to contact the manufacture and ask them about the firmware update.
On their website only the dirver is available for download, so I had to contact their support.


I have dual boot Win7 / ubuntu 11.10, and I must add that I have the same problems (slow USB3.0) in Windows 7 64 bit as well. 

In Win7 it is even worse - I still did not manage to figure out how to make Win7 to  recognize that the HDD was plugged in the USB3.0 - hot plug does not work, only when plugged in on boot. I did not try to fix that yet since I do not use Win7 - only very occasionally. I always use ubuntu.

---

### Post by fmjrey on 2012-02-28
So did you manage to update the firmware of the USB controler on your Dell latitude E6520 and get USB 3.0 speed?

---

### Post by aa-hcl on 2012-02-28
Hi,

no, I did not manage to update the controller - I contacted the manufacturer and they said it is not available.

For Win7 (I have a dual boot) after updates it suddenly started to give me the USB3.0 speed (OK, not quite - it is now about 2 times faster than USB 2.0 - probably limited by my HDD speed or something else), which means it is not the hardware to blame.


Do you have any idea what to try next?

Many thanks!

---

### Post by jonnyboysmithy on 2012-05-05
Bump, same problem here on ubuntu 12.04. The usb3 ports worked out of the box but I'm getting usb2 speeds.

---

### Post by aa-hcl on 2012-05-07
After installation of 12.04 LTS on the same system (through the upgrade)

It looks now that USB3.0 works similar as with Windows 7 on the same machine:

reading test speed: 72MB/sec  ~ 2 times faster than USB2.0

copying from laptop's HDD is faster than with USB2.0, but not than much faster - it is apparently limited to reading limitation on laptops HDD. 

aa@aa-i7:~$ sudo hdparm -t /dev/sdb1
/dev/sdb1:
 Timing buffered disk reads: 218 MB in  3.01 seconds =  72.38 MB/sec
aa@aa-i7:~$ 

aa@aa-i7:~$ time cp /media/Vbox-disks/WinXP.vdi /media/Iomega_HDD/usb3/

real    3m56.709s
user    0m0.160s
sys    0m27.062s
aa@aa-i7:~$ ls -all /media/Vbox-disks/WinXP.vdi 
-rw------- 1 aa aa 10277134848 Apr 30 16:44 /media/Vbox-disks/WinXP.vdi

this is 10277/236 = 43.54 MB/sec

---

### Post by aa-hcl on 2012-05-07
> **jonnyboysmithy said:**
> Bump, same problem here on ubuntu 12.04. The usb3 ports worked out of the box but I'm getting usb2 speeds.

Just to add that when I firstly installed the Express card with USB3.0 port on my dell 6520, the card did not work on Windows 7 at all (I have dual-boot machine). Then Win7 did some updates and after a couple of weeks it fixed itself somehow. May be Win 7 also did some firmware updates - I do not know for sure (however, it is probably unlikely), but eventually it started to work on ubuntu as well (at that time 11.10). And only after upgrade to 12.04 I got the same speed on USB3.0 in ubuntu 12.04 as in Win7.

I also noticed that under 12.04 the backup (dejadup or rsync-based) seems to be much faster than before on USB3.0 drive, but I did not have time to measure it.

---

### Post by Zelphir on 2012-05-10
I read about this issue before and it seems that the speed also depends on how your express card port is connected in your computer. It can be connected to the USB 2.0 Controler or the PCIe Controler internally. So I would like to ask: What terminal commands can I use to find out how my express card port is connected internally?

---

### Post by aa-hcl on 2012-05-10
> **Zelphir said:**
> I read about this issue before and it seems that the speed also depends on how your express card port is connected in your computer. It can be connected to the USB 2.0 Controler or the PCIe Controler internally. So I would like to ask: What terminal commands can I use to find out how my express card port is connected internally?


Hi,

I guess that when you type lspci (or lsusb) you get the list of all devices.

In my case the USB3.0 card is sitting on PCI as it should be:

aa@aa-i7:~$ lspci | grep "USB 3"
04:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)

---

### Post by Zelphir on 2012-05-10
> **aa-hcl said:**
> Hi,

I guess that when you type lspci (or lsusb) you get the list of all devices.

In my case the USB3.0 card is sitting on PCI as it should be:

aa@aa-i7:~$ lspci | grep &quot;USB 3&quot;
04:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)

 Worked like a charm for me, thanks!

---

### Post by jcoles on 2012-06-16
I had exactly the same issue in 12.04. 

According to lsusb (and lsusb -t), the PCI express card was recognized as USB 3.0:
```
Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 08.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/2p, 5000M
```

But the Seagate USB 3.0 drive connected to that card ran as USB 2.0:
```
Bus 007 Device 007: ID 0bc2:5031 Seagate RSS LLC FreeAgent GoFlex USB 3.0
/:  Bus 07.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/2p, 480M
    |__ Port 2: Dev 7, If 0, Class=stor., Driver=usb-storage, 480M
```

Note that the drive is shown as connected to USB 2.0 Bus 007, not USB 3.0 Bus 008. 

I tried substituting a different cable that came with a RocketFish USB 3.0 enclosure. This cable has a second connector to get additional power from another USB port. The GoFlex drive was correctly recognized as USB 3.0. Then I retried without the extra power connection -- success again. Lastly, I retried with the original cable -- success. Nice to succeed, but I still don't know what the problem was.

Addenda: 

Copying a 2GB file to the GoFlex in 3.0 mode is no faster than in 2.0 mode. Same file. Same source. Same destination. 3.0 may be supported, but 3.0 performance just isn't there. 

Tried my RocketFish enclosure and found it is not detected at all on the 3.0 ports. Will try again with another card. This one's a cheapie and only one of the two ports works at all.

---

### Post by aa-hcl on 2012-06-17
Hi,

Do you have a dual boot machine?  when I first got the USB3.0 EC card into  the laptop the USB3.0 did not work at all and when it started to work, it was as slow as USB2.0

Only after sometime it started to work on Win7 and only on ubuntu 12.04 it started to be USB3.0. This may me thinking that it was a kernel problem.

Another good idea is to check - are there any hardware updates from the manufacturer?

By the way, now I have another problem with USB3.0 EC card:  when I insert now the USB3.0 HDD it is NOT recognized by the laptop - i.e. hot-plug is NOT working!!!!

Previously in 12.04 it was working! If I reboot, then the HDD recognized during boot and everything works.

Can you please check what module are running on your machine and what they are writing to log files when the dirve is plugged into the port?

Many thanks!

---

