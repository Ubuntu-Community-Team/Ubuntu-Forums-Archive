---
title: "PCMCIA Slot not working in Flight 7"
date: 2006-05-26
forum: Hardware &amp; Laptops
---

### Post by erothoff on 2006-05-26
Hello,
  I am trying to get my PCMCIA Slot working, so that I can use my 3Com 3CCM756 modem. (Yes it is a hardware modem, and both the modem and PCMCIA Slot works under SUSE 10.0 kernel 2.6.13-15-default)
  When I first tried "lspci -v | grep subordinate" I got:
>         Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        Bus: primary=00, secondary=05, subordinate=09, sec-latency=64
        Bus: primary=05, secondary=06, subordinate=09, sec-latency=176

Then I added "pci=assign-busses" to the boot parameters and got:

>         Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        Bus: primary=00, secondary=02, subordinate=06, sec-latency=64
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=176

And the PCMCIA Card still didn't work. Also, lspci -v without providing the boot switch provided:

0000:00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
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



And with the switch



0000:00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
        Subsystem: Hewlett-Packard Company: Unknown device 3091
        Flags: bus master, 66MHz, medium devsel, latency 64

0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5a3f (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: d0100000-d01fffff
        Prefetchable memory behind bridge: 00000000d4000000-00000000d7f00000
        Capabilities: [44] #08 [a803]
        Capabilities: [b0] #0d [0000]

0000:00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company: Unknown device 3091
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 201
        Memory at d0000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [d0] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-

0000:00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company: Unknown device 3091
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 201
        Memory at d0001000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [d0] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-

0000:00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company: Unknown device 3091
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 201
        Memory at d0002000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [dc] Power Management version 2
        Capabilities: [d0] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-

0000:00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
        Subsystem: Hewlett-Packard Company: Unknown device 3091
        Flags: 66MHz, medium devsel
        I/O ports at 8400 [size=16]
        Memory at d0003000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [b0] #08 [a802]

0000:00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80) (prog-if 8a [Master SecP PriP])
        Subsystem: Hewlett-Packard Company: Unknown device 3091
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 193
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at 8410 [size=16]
        Capabilities: [70] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-

0000:00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
        Subsystem: Hewlett-Packard Company: Unknown device 3091
        Flags: bus master, 66MHz, medium devsel, latency 0

0000:00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=02, subordinate=06, sec-latency=64
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: d0200000-d02fffff
        Prefetchable memory behind bridge: 20000000-21ffffff

0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 80)
        Subsystem: Hewlett-Packard Company: Unknown device 3091
        Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 185
        Memory at d0003400 (32-bit, non-prefetchable) [size=256]
        Capabilities: [40] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-

0000:00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 80) (prog-if 00 [Generic])
        Subsystem: Hewlett-Packard Company: Unknown device 3091
        Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 185
        Memory at d0003800 (32-bit, non-prefetchable) [size=256]
        Capabilities: [40] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-

0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: [80] #08 [2101]

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
        Capabilities: [50] Power Management version 2

0000:02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Hewlett-Packard Company: Unknown device 3091
        Flags: bus master, medium devsel, latency 64, IRQ 209
        I/O ports at a000 [size=256]
        Memory at d0208000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2

0000:02:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
        Subsystem: Hewlett-Packard Company: Unknown device 1355
        Flags: bus master, fast devsel, latency 64, IRQ 217
        Memory at d0204000 (32-bit, non-prefetchable) [size=8K]

0000:02:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
        Subsystem: Hewlett-Packard Company: Unknown device 3091
        Flags: bus master, medium devsel, latency 168, IRQ 185
        Memory at d0200000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
        Memory window 0: 20000000-21fff000 (prefetchable)
        Memory window 1: 22000000-23fff000
        I/O window 0: 0000a400-0000a4ff
        I/O window 1: 0000a800-0000a8ff
        16-bit legacy interface ports at 0001

  Any suggestions in getting the PCMCIA Slot working would be greatly appreciated. Once 6.06 final comes out, I will put my experience on laptop ubuntu.  I was going to do it with 5.10, but it freezes on boot.
  My notebook is a Compaq v2552US, and I have Kubuntu Flight 7 with all the updates, (From my Ethernet connection to a friends broadband connection.)  It is a Sempron, (I do not believe it is a 64) and I have SUSE 10.0 installed also, and the PCMCIA card and modem both work on it. (But the battery stats, and other things don't work there.)
  Thank you for your time,
Eric

---

