---
title: "Laptop audio controllers"
date: 2012-02-13
forum: Hardware
---

### Post by didiandrade on 2012-02-13
Hi, just started using lubuntu and I'd like to make the make the sound controllers button (like the mute button) of the laptop work.

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
    Subsystem: Hewlett-Packard Company Device 3091
    Flags: bus master, 66MHz, medium devsel, latency 64
    Kernel modules: ati-agp

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
    I/O behind bridge: 00009000-00009fff
    Memory behind bridge: c0100000-c01fffff
    Prefetchable memory behind bridge: 00000000c8000000-00000000cfffffff
    Capabilities: <access denied>
    Kernel modules: shpchp

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (prog-if 10 [OHCI])
    Subsystem: Hewlett-Packard Company Device 3091
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at c0000000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (prog-if 10 [OHCI])
    Subsystem: Hewlett-Packard Company Device 3091
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at c0001000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (prog-if 20 [EHCI])
    Subsystem: Hewlett-Packard Company Device 3091
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at c0002000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
    Subsystem: Hewlett-Packard Company Device 3091
    Flags: 66MHz, medium devsel
    I/O ports at 8400 [size=16]
    Memory at c0003000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (prog-if 8a [Master SecP PriP])
    Subsystem: Hewlett-Packard Company Device 3091
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 8410 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_atiixp
    Kernel modules: pata_atiixp

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
    Subsystem: Hewlett-Packard Company Device 3091
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (prog-if 01 [Subtractive decode])
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=05, subordinate=09, sec-latency=64
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: c0200000-c02fffff
    Prefetchable memory behind bridge: 20000000-23ffffff

00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 3091
    Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 17
    Memory at c0003400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ATI IXP AC97 controller
    Kernel modules: snd-atiixp

00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02) (prog-if 00 [Generic])
    Subsystem: Hewlett-Packard Company Device 3091
    Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 17
    Memory at c0003800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ATI IXP MC97 controller
    Kernel modules: snd-atiixp-modem

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
    Flags: fast devsel
    Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
    Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
    Flags: fast devsel
    Kernel driver in use: k8temp
    Kernel modules: k8temp

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE) (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Device 3091
    Flags: bus master, 66MHz, medium devsel, latency 66, IRQ 17
    Memory at c8000000 (32-bit, prefetchable) [size=128M]
    I/O ports at 9000 [size=256]
    Memory at c0100000 (32-bit, non-prefetchable) [size=64K]
    [virtual] Expansion ROM at c0120000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel modules: radeon, radeonfb

05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    Subsystem: Hewlett-Packard Company Device 3091
    Flags: bus master, medium devsel, latency 64, IRQ 18
    I/O ports at a000 [size=256]
    Memory at c0208000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: 8139too
    Kernel modules: 8139too, 8139cp

05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
    Subsystem: Hewlett-Packard Company Broadcom 802.11b/g WLAN
    Flags: bus master, fast devsel, latency 64, IRQ 20
    Memory at c0204000 (32-bit, non-prefetchable) [size=8K]
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb

05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
    Subsystem: Hewlett-Packard Company Device 3091
    Flags: bus master, medium devsel, latency 168, IRQ 17
    Memory at c0200000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=05, secondary=06, subordinate=09, sec-latency=176
    Memory window 0: 20000000-23fff000 (prefetchable)
    Memory window 1: 24000000-27fff000
    I/O window 0: 0000a400-0000a4ff
    I/O window 1: 0000a800-0000a8ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

---

### Post by Rodney9 on 2012-02-13
Try this , but make sure you backup the file first.

[http://wiki.lxde.org/en/LXDE:Questions#How_do_I_make_my_keyboard_volume_buttons_work.3F](http://wiki.lxde.org/en/LXDE:Questions#How_do_I_make_my_keyboard_volume_buttons_work.3F)


For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

