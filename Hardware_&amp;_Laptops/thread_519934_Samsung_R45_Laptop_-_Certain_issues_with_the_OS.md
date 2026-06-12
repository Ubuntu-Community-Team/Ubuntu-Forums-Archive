---
title: "Samsung R45 Laptop - Certain issues with the OS"
date: 2007-08-07
forum: Hardware &amp; Laptops
---

### Post by Xelviar on 2007-08-07
I've just installed the current Ubuntu onto my **Samsung R45**, but I already seem to be having problems...

First of all, I need to understand how to install an official ATi card from the ATi site and make it install on the Ubuntu desktop.  The card is a ATi Radeon Xpress 200M.  However, as the computer is a WXGA widescreen laptop (resolution 1280x800) I may need help on compiling the installer and then resizing it to the resolution above.

I also require some help for the soundcard, which is a Realtek HD Audio driver on the x86 platform.  Could anyone give me some tips of installing it?

I'm sorry if this has been done a couple of times, but as I want an alternative for Windows, I'm rather new to the Ubuntu environment.  PM or reply below to recommendations to help me out on this problem! :)

---

### Post by syahya on 2007-09-27
Same problem with SAMSUNG R40.

Sound card was working properly with Ubuntu 6.04 & 6.10

Now with 7.04 I am facing strange permission problems with sound card

Here is an output for the command lspci -v


00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
        Subsystem: Samsung Electronics Co Ltd Unknown device c02b
        Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: c0000000-c00fffff
        Prefetchable memory behind bridge: d0000000-dfffffff
        Capabilities: <access denied>

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Samsung Electronics Co Ltd Unknown device c02b
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        Memory at c0404000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Samsung Electronics Co Ltd Unknown device c02b
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        Memory at c0405000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) (prog-if 20 [EHCI])
        Subsystem: Samsung Electronics Co Ltd Unknown device c02b
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        Memory at c0406000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
        Subsystem: Samsung Electronics Co Ltd Unknown device c02b
        Flags: 66MHz, medium devsel
        I/O ports at 8400 [size=16]
        Memory at c0407000 (32-bit, non-prefetchable) [size=1K]

00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80) (prog-if 8a [Master SecP PriP])
        Subsystem: Samsung Electronics Co Ltd Unknown device c02b
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 8410 [size=16]
        Capabilities: <access denied>

00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
        Subsystem: Samsung Electronics Co Ltd Unknown device c02b
        Flags: bus master, slow devsel, latency 64, IRQ 18
        Memory at c0400000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
        Subsystem: Samsung Electronics Co Ltd Unknown device c02b
        Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=02, subordinate=05, sec-latency=64
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: f0200000-f02fffff
        Prefetchable memory behind bridge: f0300000-f03fffff

01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M] (prog-if 00 [VGA])
        Subsystem: Samsung Electronics Co Ltd Unknown device c02b
        Flags: bus master, 66MHz, medium devsel, latency 255, IRQ 22
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at 9000 [size=256]
        Memory at c0000000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at c0020000 [disabled] [size=128K]
        Capabilities: <access denied>

02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Samsung Electronics Co Ltd Unknown device c02b
        Flags: bus master, medium devsel, latency 64, IRQ 19
        I/O ports at a000 [size=256]
        Memory at c0100000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

02:07.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
        Subsystem: Askey Computer Corp. Unknown device 7101
        Flags: bus master, medium devsel, latency 168, IRQ 18
        Memory at c0110000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

02:09.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b4)
        Subsystem: Samsung Electronics Co Ltd Unknown device c02b
        Flags: bus master, medium devsel, latency 168, IRQ 16
        Memory at c0101000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=04, sec-latency=176
        Memory window 0: 40000000-43fff000 (prefetchable)
        Memory window 1: 44000000-47fff000
        I/O window 0: 0000a400-0000a4ff
        I/O window 1: 0000a800-0000a8ff
        16-bit legacy interface ports at 0001

02:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 18)
        Subsystem: Samsung Electronics Co Ltd Unknown device c02b
        Flags: bus master, medium devsel, latency 64, IRQ 20
        Memory at c0100400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

02:09.2 System peripheral: Ricoh Co Ltd Unknown device 0843
        Subsystem: Samsung Electronics Co Ltd Unknown device c02b
        Flags: bus master, medium devsel, latency 0, IRQ 255
        Memory at c0100800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

02:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 09)
        Subsystem: Samsung Electronics Co Ltd Unknown device c02b
        Flags: medium devsel, IRQ 255
        Memory at c0100c00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

02:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 04)
        Subsystem: Samsung Electronics Co Ltd Unknown device c02b
        Flags: medium devsel, IRQ 255
        Memory at c0102000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>


:confused::confused::confused::confused:

---

