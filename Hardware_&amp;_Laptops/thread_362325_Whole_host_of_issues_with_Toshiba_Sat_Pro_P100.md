---
title: "Whole host of issues with Toshiba Sat Pro P100"
date: 2007-02-15
forum: Hardware &amp; Laptops
---

### Post by paddyS on 2007-02-15
Not doing well and a complete newbie (to Linux anyway - I did know my way around unix servers but that was over 10 yrs ago ;) )

Installed Dapper on reccomendation of one of my colleagues who wanted my machine to run same as him for cross compatability.....  seemed to go ok but then issues with installing packages... Installed the Nvidia driver (even tho not strictly supported for geforce Go 7600) and things improved (upto a point) Did some investigation and found the following....

patrick@patrick-laptop:~$ lspci -v
0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03 )
        Subsystem: Toshiba America Info Systems: Unknown device ff31
        Flags: bus master, fast devsel, latency 0
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Graphics Port (rev  03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: d0000000-d1ffffff
        Prefetchable memory behind bridge: 00000000c0000000-00000000cff00000
        Capabilities: <available only to root>

0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Toshiba America Info Systems: Unknown device ff31
        Flags: bus master, fast devsel, latency 0, IRQ 58
        Memory at d2500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port  1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: 6a000000-6a0fffff
        Capabilities: <available only to root>

0000:00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port  2 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Memory behind bridge: 6a100000-6a1fffff
        Capabilities: <available only to root>

0000:00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port  3 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        Capabilities: <available only to root>

0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems: Unknown device ff31
        Flags: bus master, medium devsel, latency 0, IRQ 50
        I/O ports at 1800 [size=32]

0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems: Unknown device ff31
        Flags: bus master, medium devsel, latency 0, IRQ 233
        I/O ports at 1820 [size=32]

0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems: Unknown device ff31
        Flags: bus master, medium devsel, latency 0, IRQ 185
        I/O ports at 1840 [size=32]

0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems: Unknown device ff31
        Flags: bus master, medium devsel, latency 0, IRQ 169
        I/O ports at 1860 [size=32]

0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Co ntroller (rev 02) (prog-if 20 [EHCI])
        Subsystem: Toshiba America Info Systems: Unknown device ff31
        Flags: bus master, medium devsel, latency 0, IRQ 50
        Memory at d2504000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <available only to root>

0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (pro g-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0a, subordinate=0e, sec-latency=32
        I/O behind bridge: 00004000-00004fff
        Memory behind bridge: d2100000-d21fffff
        Prefetchable memory behind bridge: 0000000068000000-0000000069f00000
        Capabilities: <available only to root>

0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridg e (rev 02)
        Subsystem: Toshiba America Info Systems: Unknown device ff31
        Flags: bus master, medium devsel, latency 0
        Capabilities: <available only to root>

0000:00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 02) (prog-if 80 [Master])
        Subsystem: Toshiba America Info Systems: Unknown device ff31
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 233
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at 18b0 [size=16]
        Capabilities: <available only to root>

0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev  02)
        Subsystem: Toshiba America Info Systems: Unknown device ff31
        Flags: medium devsel, IRQ 11
        I/O ports at 18c0 [size=32]

0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0398 (rev a1) (prog-if 00 [VGA])
        Subsystem: Toshiba America Info Systems: Unknown device ff31
        Flags: bus master, fast devsel, latency 0, IRQ 169
        Memory at d1000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at d0000000 (64-bit, non-prefetchable) [size=16M]
        I/O ports at 2000 [size=128]
        Capabilities: <available only to root>

0000:02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Cont roller
        Subsystem: Toshiba America Info Systems: Unknown device ff31
        Flags: bus master, fast devsel, latency 0, IRQ 66
        Memory at 6a000000 (32-bit, non-prefetchable) [size=128K]
        I/O ports at 3000 [size=32]
        Capabilities: <available only to root>

0000:03:00.0 Network controller: Intel Corporation: Unknown device 4222 (rev 02)
        Subsystem: Intel Corporation: Unknown device 1041
        Flags: bus master, fast devsel, latency 0, IRQ 177
        Memory at 6a100000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:0a:04.0 CardBus bridge: Texas Instruments: Unknown device 8039
        Subsystem: Toshiba America Info Systems: Unknown device ff31
        Flags: bus master, medium devsel, latency 168, IRQ 177
        Memory at d2100000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=0a, secondary=0b, subordinate=0e, sec-latency=176
        Memory window 0: 68000000-69fff000 (prefetchable)
        Memory window 1: 6c000000-6dfff000
        I/O window 0: 00004000-000040ff
        I/O window 1: 00004400-000044ff
        16-bit legacy interface ports at 0001

0000:0a:04.1 FireWire (IEEE 1394): Texas Instruments: Unknown device 803a (prog- if 10 [OHCI])
        Subsystem: Toshiba America Info Systems: Unknown device ff31
        Flags: bus master, medium devsel, latency 64, IRQ 177
        Memory at d2102000 (32-bit, non-prefetchable) [size=2K]
        Memory at d2104000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

0000:0a:04.2 Mass storage controller: Texas Instruments: Unknown device 803b
        Subsystem: Toshiba America Info Systems: Unknown device ff31
        Flags: medium devsel, IRQ 11
        Memory at d2101000 (32-bit, non-prefetchable) [disabled] [size=4K]
        Capabilities: <available only to root>

0000:0a:04.3 0805: Texas Instruments: Unknown device 803c (prog-if 01)
        Subsystem: Toshiba America Info Systems: Unknown device ff31
        Flags: bus master, medium devsel, latency 64, IRQ 177
        Memory at d2102800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

Suggestions of help appreciated (In simple words (maybe crayon with my level of knowledge)) ;)

Paddy

---

### Post by louis_nichols on 2007-02-15
Hi! the lspci output is helpful, but one needs to know more in order to help.

what errors do you get when you try installing packages? what other problems do you have?

---

### Post by paddyS on 2007-02-15
until I got the nvidia driver sorted out it wouldn't let me install most packages (just said not compatible with my hardware in an error box) - thats sorted now; but no sound - issues mounting drives (windows drive or external HD).  Graphics still not right but that i presume is that nvidia are not supporting this card in their driver at the moment.

Also issues with wireless - tho that is more wep vs wpa related (is there decent wpa support in any wireless app under dapper - most references I've seen are for edgy)

P

P

---

