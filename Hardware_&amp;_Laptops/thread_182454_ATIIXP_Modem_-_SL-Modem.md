---
title: "ATIIXP Modem - SL-Modem"
date: 2006-05-26
forum: Hardware &amp; Laptops
---

### Post by erothoff on 2006-05-26
Hello,
  I have a Compaq v2552us notebook that uses the ATIIXP Sound and Modem.  I have read that other also have the problem of being able to install the sl-modem package, and everything works except that the modem will not detect a dialtone. I tried using the mixer to take the modem manually off hook, but that didn't solve the problem.
  I also read that it is a conflict between the sound and modem drivers, and if I could put the sound driver in the kernal that this might solve the problem. But I was unable to install the kernal tree to try and compile a new kernel with the sound build in. (I am using kernel 2.6.15-23-386.)  And I can not install the new sl-modem, slmodem-2.9.11-20051101 also because I can not install the kernel tree.
  Does anyone have another suggestion? I am also trying to install a hardware PCMCIA modem, but that also isn't working. (See other post.)
  Thank you for your time,
Eric
P.S. my lspci -v is:
> 0000:00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
        Subsystem: Hewlett-Packard Company: Unknown device 3091
        Flags: bus master, 66MHz, medium devsel, latency 64

0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5a3f (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: d0100000-d01fffff
        Prefetchable memory behind bridge: 00000000d4000000-00000000d7f00000
        Capabilities: <available only to root>

0000:00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company: Unknown device 3091
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 201
        Memory at d0000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company: Unknown device 3091
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 201
        Memory at d0001000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company: Unknown device 3091
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 201
        Memory at d0002000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
        Subsystem: Hewlett-Packard Company: Unknown device 3091
        Flags: 66MHz, medium devsel
        I/O ports at 8400 [size=16]
        Memory at d0003000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <available only to root>

0000:00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80) (prog-if 8a [Master SecP PriP])
        Subsystem: Hewlett-Packard Company: Unknown device 3091
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 193
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at 8410 [size=16]
        Capabilities: <available only to root>

0000:00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
        Subsystem: Hewlett-Packard Company: Unknown device 3091
        Flags: bus master, 66MHz, medium devsel, latency 0

0000:00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=05, subordinate=09, sec-latency=64
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: d0200000-d02fffff
        Prefetchable memory behind bridge: 20000000-21ffffff

0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 80)
        Subsystem: Hewlett-Packard Company: Unknown device 3091
        Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 185
        Memory at d0003400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 80) (prog-if 00 [Generic])
        Subsystem: Hewlett-Packard Company: Unknown device 3091
        Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 185
        Memory at d0003800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <available only to root>

0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel

0000:01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE) (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company: Unknown device 3091
        Flags: bus master, 66MHz, medium devsel, latency 66, IRQ 10
        Memory at d4000000 (32-bit, prefetchable) [size=64M]
        I/O ports at 9000 [size=256]
        Memory at d0100000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at d0120000 [disabled] [size=128K]
        Capabilities: <available only to root>

0000:05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Hewlett-Packard Company: Unknown device 3091
        Flags: bus master, medium devsel, latency 64, IRQ 209
        I/O ports at a000 [size=256]
        Memory at d0208000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
        Subsystem: Hewlett-Packard Company: Unknown device 1355
        Flags: bus master, fast devsel, latency 64, IRQ 217
        Memory at d0204000 (32-bit, non-prefetchable) [size=8K]

0000:05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
        Subsystem: Hewlett-Packard Company: Unknown device 3091
        Flags: bus master, medium devsel, latency 168, IRQ 185
        Memory at d0200000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=05, secondary=06, subordinate=09, sec-latency=176
        Memory window 0: 20000000-21fff000 (prefetchable)
        Memory window 1: 22000000-23fff000
        I/O window 0: 0000a400-0000a4ff
        I/O window 1: 0000a800-0000a8ff
        16-bit legacy interface ports at 0001
 

---

