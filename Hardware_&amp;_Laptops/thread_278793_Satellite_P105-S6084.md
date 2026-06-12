---
title: "Satellite P105-S6084"
date: 2006-10-16
forum: Hardware &amp; Laptops
---

### Post by dafut on 2006-10-16
First off, I'm new to the Ubuntu forum community, reasonably new to linux-based workstations, and have fair experience with linux-based servers (LAMP).

Being another that's fed up with "the other guys", I want to migrate almost entirely to a new system (I say almost because I've still got to support people on the WinX platform).  

My install of Ubuntu Dapper Drake on my Toshiba Satellite P105-6084 went very well: wired, wireless, sound (with acpi off), usb, networked printers, wireless keyboard and mouse all work.  

Where I'm running into problems is with my need to run a second monitor (dual head) and that I can't record sound (capture), so Skype only works for chat-based communications.

Any thoughts, suggestions, ideas or *solutions* are greatly appreciated.  My lspci is below.

[SIZE="2"]```
root@shibatop:/proc# lspci -v
0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
        Subsystem: Toshiba America Info Systems: Unknown device ff31
        Flags: bus master, fast devsel, latency 0
        Capabilities: [e0] #09 [5109]

0000:00:02.0 VGA compatible controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: Toshiba America Info Systems: Unknown device ff31
        Flags: bus master, fast devsel, latency 0, IRQ 153
        Memory at d0200000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Memory at d0300000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: [90] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-
        Capabilities: [d0] Power Management version 2

0000:00:02.1 Display controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
        Subsystem: Toshiba America Info Systems: Unknown device ff31
        Flags: bus master, fast devsel, latency 0
        Memory at d0280000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: [d0] Power Management version 2

0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Toshiba America Info Systems: Unknown device ff31
        Flags: bus master, fast devsel, latency 0, IRQ 193
        Memory at d0340000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
        Capabilities: [70] #10 [0091]

0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Capabilities: [40] #10 [0141]
        Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable+
        Capabilities: [90] #0d [0000]
        Capabilities: [a0] Power Management version 2

0000:00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Memory behind bridge: d0100000-d01fffff
        Capabilities: [40] #10 [0141]
        Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable+
        Capabilities: [90] #0d [0000]
        Capabilities: [a0] Power Management version 2

0000:00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        Capabilities: [40] #10 [0141]
        Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable+
        Capabilities: [90] #0d [0000]
        Capabilities: [a0] Power Management version 2

0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems: Unknown device ff31
        Flags: bus master, medium devsel, latency 0, IRQ 201
        I/O ports at 1820 [size=32]

0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems: Unknown device ff31
        Flags: bus master, medium devsel, latency 0, IRQ 177
        I/O ports at 1840 [size=32]

0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems: Unknown device ff31
        Flags: bus master, medium devsel, latency 0, IRQ 169
        I/O ports at 1860 [size=32]

0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems: Unknown device ff31
        Flags: bus master, medium devsel, latency 0, IRQ 153
        I/O ports at 1880 [size=32]

0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: Toshiba America Info Systems: Unknown device ff31
        Flags: bus master, medium devsel, latency 0, IRQ 201
        Memory at d0544000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] #0a [20a0]

0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0a, subordinate=0e, sec-latency=32
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: d0000000-d00fffff
        Prefetchable memory behind bridge: 0000000088000000-0000000089f00000
        Capabilities: [50] #0d [0000]

0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
        Subsystem: Toshiba America Info Systems: Unknown device ff31
        Flags: bus master, medium devsel, latency 0
        Capabilities: [e0] #09 [100c]

0000:00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 02) (prog-if 80 [Master])
        Subsystem: Toshiba America Info Systems: Unknown device ff31
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 177
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at 18b0 [size=16]
        Capabilities: [70] Power Management version 2

0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
        Subsystem: Toshiba America Info Systems: Unknown device ff31
        Flags: medium devsel, IRQ 177
        I/O ports at 18c0 [size=32]

0000:03:00.0 Network controller: Intel Corporation: Unknown device 4222 (rev 02)
        Subsystem: Intel Corporation: Unknown device 1040
        Flags: bus master, fast devsel, latency 0, IRQ 161
        Memory at d0100000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [c8] Power Management version 2
        Capabilities: [d0] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
        Capabilities: [e0] #10 [0011]

0000:0a:04.0 CardBus bridge: Texas Instruments: Unknown device 8039
        Subsystem: Toshiba America Info Systems: Unknown device ff31
        Flags: bus master, medium devsel, latency 168, IRQ 161
        Memory at d0004000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=0a, secondary=0b, subordinate=0e, sec-latency=176
        Memory window 0: 88000000-89fff000 (prefetchable)
        Memory window 1: 8a000000-8bfff000
        I/O window 0: 00002400-000024ff
        I/O window 1: 00002800-000028ff
        16-bit legacy interface ports at 0001

0000:0a:04.1 FireWire (IEEE 1394): Texas Instruments: Unknown device 803a (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems: Unknown device ff31
        Flags: bus master, medium devsel, latency 64, IRQ 161
        Memory at d0007000 (32-bit, non-prefetchable) [size=2K]
        Memory at d0000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 2

0000:0a:04.2 Mass storage controller: Texas Instruments: Unknown device 803b
        Subsystem: Toshiba America Info Systems: Unknown device ff31
        Flags: medium devsel, IRQ 161
        Memory at d0005000 (32-bit, non-prefetchable) [disabled] [size=4K]
        Capabilities: [44] Power Management version 2

0000:0a:04.3 0805: Texas Instruments: Unknown device 803c (prog-if 01)
        Subsystem: Toshiba America Info Systems: Unknown device ff31
        Flags: bus master, medium devsel, latency 64, IRQ 161
        Memory at d0007800 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

0000:0a:08.0 Ethernet controller: Intel Corporation: Unknown device 1092 (rev 02)
        Subsystem: Toshiba America Info Systems: Unknown device ff31
        Flags: bus master, medium devsel, latency 64, IRQ 185
        Memory at d0006000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 2000 [size=64]
        Capabilities: [dc] Power Management version 2


```[/SIZE]

---

