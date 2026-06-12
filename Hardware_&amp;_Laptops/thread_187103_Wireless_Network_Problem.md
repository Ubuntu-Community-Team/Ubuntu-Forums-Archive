---
title: "Wireless Network Problem"
date: 2006-06-02
forum: Hardware &amp; Laptops
---

### Post by jrattner on 2006-06-02
Could Someone assit me with getting my wireless networking card to work.  Here is the output of lspci -v:

Note: Any help would be appriciated.

0000:00:00.0 Host bridge: Intel Corporation 915G/P/GV/GL/PL/910GL Processor to I/O Controller (rev 04)
        Subsystem: Hewlett-Packard Company: Unknown device 3082
        Flags: bus master, fast devsel, latency 0
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: Intel Corporation 915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00004000-00004fff
        Memory behind bridge: b0100000-b01fffff
        Prefetchable memory behind bridge: c0000000-cfffffff
        Capabilities: <available only to root>

0000:00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Capabilities: <available only to root>

0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company: Unknown device 3082
        Flags: bus master, medium devsel, latency 0, IRQ 225
        I/O ports at 1800 [size=32]

0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company: Unknown device 3082
        Flags: bus master, medium devsel, latency 0, IRQ 233
        I/O ports at 38c0 [size=32]

0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company: Unknown device 3082
        Flags: bus master, medium devsel, latency 0, IRQ 217
        I/O ports at 38e0 [size=32]

0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company: Unknown device 3082
        Flags: bus master, medium devsel, latency 0, IRQ 169
        I/O ports at 3c00 [size=32]

0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company: Unknown device 3082
        Flags: bus master, medium devsel, latency 0, IRQ 225
        Memory at b0000000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <available only to root>

0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0b, subordinate=0f, sec-latency=32
        I/O behind bridge: 00005000-00005fff
        Memory behind bridge: b0200000-b02fffff
        Prefetchable memory behind bridge: 0000000088000000-0000000089f00000
        Capabilities: <available only to root>

0000:00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
        Subsystem: Hewlett-Packard Company: Unknown device 3082
        Flags: bus master, medium devsel, latency 0, IRQ 209
        I/O ports at 3000 [size=256]
        I/O ports at 3880 [size=64]
        Memory at b0000800 (32-bit, non-prefetchable) [size=512]
        Memory at b0000400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03) (prog-if 00 [Generic])
        Subsystem: Hewlett-Packard Company: Unknown device 3082
        Flags: medium devsel, IRQ 209
        I/O ports at 3400 [size=256]
        I/O ports at 3800 [size=128]
        Capabilities: <available only to root>

0000:00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
        Subsystem: Hewlett-Packard Company: Unknown device 3082
        Flags: bus master, medium devsel, latency 0

0000:00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: Hewlett-Packard Company: Unknown device 3082
        Flags: bus master, medium devsel, latency 0, IRQ 217
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at 3c40 [size=16]

0000:00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
        Subsystem: Hewlett-Packard Company: Unknown device 3082
        Flags: medium devsel, IRQ 7
        I/O ports at 3c20 [size=32]

0000:01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600] (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company: Unknown device 3082
        Flags: bus master, fast devsel, latency 0, IRQ 169
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at 4000 [size=256]
        Memory at b0100000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at b0120000 [disabled] [size=128K]
        Capabilities: <available only to root>

0000:0b:00.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
        Subsystem: Hewlett-Packard Company: Unknown device 3082
        Flags: bus master, medium devsel, latency 168, IRQ 169
        Memory at b020a000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=0b, secondary=0c, subordinate=0f, sec-latency=176
        Memory window 0: 88000000-89fff000 (prefetchable)
        Memory window 1: 8a000000-8bfff000
        I/O window 0: 00005400-000054ff
        I/O window 1: 00005800-000058ff
        16-bit legacy interface ports at 0001

0000:0b:00.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company: Unknown device 3082
        Flags: bus master, medium devsel, latency 64, IRQ 209
        Memory at b0208000 (32-bit, non-prefetchable) [size=2K]
        Memory at b0200000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

0000:0b:00.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
        Subsystem: Hewlett-Packard Company: Unknown device 3082
        Flags: medium devsel, IRQ 10
        Memory at b0204000 (32-bit, non-prefetchable) [disabled] [size=8K]
        Capabilities: <available only to root>

0000:0b:00.4 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller
        Subsystem: Hewlett-Packard Company: Unknown device 3082
        Flags: bus master, medium devsel, latency 64, IRQ 169
        Memory at b0209000 (32-bit, non-prefetchable) [size=256]
        Memory at b0208c00 (32-bit, non-prefetchable) [size=256]
        Memory at b0208800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:0b:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Hewlett-Packard Company: Unknown device 3082
        Flags: bus master, medium devsel, latency 64, IRQ 50
        I/O ports at 5000 [size=256]
        Memory at b0209400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:0b:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
        Subsystem: Hewlett-Packard Company: Unknown device 1355
        Flags: bus master, fast devsel, latency 64, IRQ 177
        Memory at b0206000 (32-bit, non-prefetchable) [size=8K]

---

### Post by sadjack on 2006-06-02
Hi

I did a bit of googling on

Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller

which brings back several hits, one of which may help you. Sorry otherwise I cannot help much.

---

### Post by CitizenKane on 2006-06-02
I see that you have a Broadcom Wireless chipset in whatever wireless card you have.  Unfortunately Broadcom has bad linux support and they are also very closed about what they do.  In fact, the linux drivers were made by totally reverse engineering the broadcom drivers for windows.  There is a post to get this going in the HOW-TOs section.

[http://ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://ubuntuforums.org/showthread.php?p=1071920&mode=linear)

---

