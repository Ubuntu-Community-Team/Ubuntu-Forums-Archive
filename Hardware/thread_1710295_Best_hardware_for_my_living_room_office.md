---
title: "Best hardware for my living room office"
date: 2011-03-19
forum: Hardware
---

### Post by mlissner on 2011-03-19
I currently have a desktop computer in my living room office that I can't turn off. I've asked on many forums about how to get suspend or hibernate to work, and nobody can figure it out. 

So, given that it's in my living room office making noise and being generally annoying, it's time to upgrade the hardware in order to fix the problem. I figure I need at least a new mother board and probably a new case and CPU. 

Here's what I'm looking for:
 - Popularity. I want something a lot of linux people would choose, that's well supported in the community.
 - Supports my current hardware. I have two IDE hard drives, a wireless card and a video card that need to get in there. I don't have an ethernet card or sound card, so if those are integrated in the mother board, that would be great. If not, so be it - I'll buy cards for these.
 - The case should be quiet, and the smaller the better (but nothing weird just to be small)
 - I figure I'll need a new CPU to go with this, and I'm OK putting up some money for the motherboard.

Here's my current hardware:
```
% lspci -v
00:00.0 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
    Subsystem: Elitegroup Computer Systems Device 1b47
    Flags: bus master, medium devsel, latency 8
    Memory at f0000000 (32-bit, prefetchable) [size=128M]
    Capabilities: <access denied>
    Kernel driver in use: agpgart-via
    Kernel modules: via-agp

00:00.1 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
    Subsystem: Elitegroup Computer Systems Device 1b47
    Flags: bus master, medium devsel, latency 0

00:00.2 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
    Subsystem: Elitegroup Computer Systems Device 1b47
    Flags: bus master, medium devsel, latency 0

00:00.3 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
    Subsystem: Elitegroup Computer Systems Device 1b47
    Flags: bus master, medium devsel, latency 0

00:00.4 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
    Subsystem: Elitegroup Computer Systems Device 1b47
    Flags: bus master, medium devsel, latency 0

00:00.5 PIC: VIA Technologies, Inc. CN896/VN896/P4M900 I/O APIC Interrupt Controller (prog-if 20 [IO(X)-APIC])
    Flags: bus master, fast devsel, latency 0

00:00.6 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Security Device
    Flags: bus master, fast devsel, latency 0

00:00.7 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
    Flags: bus master, medium devsel, latency 0

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge (prog-if 00 [Normal decode])
    Flags: bus master, 66MHz, medium devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    Capabilities: <access denied>
    Kernel modules: shpchp

00:02.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000a000-0000cfff
    Memory behind bridge: ff300000-ff3fffff
    Prefetchable memory behind bridge: 00000000bff00000-00000000dfefffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:03.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: 80000000-801fffff
    Prefetchable memory behind bridge: 0000000080200000-00000000803fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:0f.0 IDE interface: VIA Technologies, Inc. Device 5337 (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Elitegroup Computer Systems Device 1b47
    Flags: bus master, medium devsel, latency 64, IRQ 21
    I/O ports at ec00 [size=8]
    I/O ports at e880 [size=4]
    I/O ports at e800 [size=8]
    I/O ports at e480 [size=4]
    I/O ports at e400 [size=16]
    I/O ports at e000 [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sata_via
    Kernel modules: sata_via

00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07) (prog-if 8a [Master SecP PriP])
    Subsystem: Elitegroup Computer Systems Device 1b47
    Flags: bus master, medium devsel, latency 32
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
    I/O ports at fc00 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_via
    Kernel modules: pata_via

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) (prog-if 00 [UHCI])
    Subsystem: Elitegroup Computer Systems Device 1b47
    Flags: bus master, medium devsel, latency 64, IRQ 20
    I/O ports at dc00 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) (prog-if 00 [UHCI])
    Subsystem: Elitegroup Computer Systems Device 1b47
    Flags: bus master, medium devsel, latency 64, IRQ 22
    I/O ports at d880 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) (prog-if 00 [UHCI])
    Subsystem: Elitegroup Computer Systems Device 1b47
    Flags: bus master, medium devsel, latency 64, IRQ 21
    I/O ports at d800 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) (prog-if 00 [UHCI])
    Subsystem: Elitegroup Computer Systems Device 1b47
    Flags: bus master, medium devsel, latency 64, IRQ 23
    I/O ports at d480 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20 [EHCI])
    Subsystem: Elitegroup Computer Systems Device 1b47
    Flags: bus master, medium devsel, latency 64, IRQ 21
    Memory at ff6ffc00 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
    Subsystem: Elitegroup Computer Systems Device 1b47
    Flags: medium devsel
    Capabilities: <access denied>
    Kernel modules: i2c-viapro

00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
    Subsystem: VIA Technologies, Inc. Device 337e
    Flags: bus master, medium devsel, latency 128
    Capabilities: <access denied>

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
    Subsystem: Elitegroup Computer Systems Device 0102
    Flags: bus master, medium devsel, latency 64, IRQ 23
    I/O ports at d000 [size=256]
    Memory at ff6ff800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: via-rhine
    Kernel modules: via-rhine

00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    Memory behind bridge: ff400000-ff4fffff
    Capabilities: <access denied>
    Kernel modules: shpchp

00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    Memory behind bridge: ff500000-ff5fffff
    Capabilities: <access denied>

02:00.0 VGA compatible controller: ATI Technologies Inc RV610 video device [Radeon HD 2400 PRO] (prog-if 00 [VGA controller])
    Subsystem: Diamond Multimedia Systems Device 3490
    Flags: bus master, fast devsel, latency 0, IRQ 24
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at ff3f0000 (64-bit, non-prefetchable) [size=64K]
    I/O ports at c000 [size=256]
    Expansion ROM at ff3c0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon

02:00.1 Audio device: ATI Technologies Inc RV610 audio device [Radeon HD 2400 PRO]
    Subsystem: Diamond Multimedia Systems Device aa10
    Flags: bus master, fast devsel, latency 0, IRQ 25
    Memory at ff3ec000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

04:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)
    Subsystem: Elitegroup Computer Systems Device 1b47
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at ff4fc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

05:04.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
    Subsystem: Belkin Device 700c
    Flags: bus master, medium devsel, latency 168, IRQ 17
    Memory at ff5f0000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath5k
    Kernel modules: ath5k

```Let me know if I've left out any important pieces of information!

---

