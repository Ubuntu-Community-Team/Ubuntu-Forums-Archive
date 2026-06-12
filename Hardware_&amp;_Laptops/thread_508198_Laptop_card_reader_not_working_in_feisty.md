---
title: "Laptop card reader not working in feisty"
date: 2007-07-23
forum: Hardware &amp; Laptops
---

### Post by arrenlex on 2007-07-23
I have recently installed kubuntu on my toshiba laptop and I have been overwhemled by the experience. It's beautiful, polished, easy to use and full-featured. The only things that don't work are suspend to ram, the card reader, tablet pen right-clicking and changing pen orientation with screen orientation (it's a tablet PC).

I was hoping one of you could help me get the card reader working; that's the most important for me. This is what sudo lspci -v says about it:

> 03:0b.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
        Subsystem: Toshiba America Info Systems Unknown device 0001
        Flags: bus master, medium devsel, latency 168, IRQ 18
        Memory at 58004000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=03, secondary=04, subordinate=07, sec-latency=176
        Memory window 0: 50000000-53fff000 (prefetchable)
        Memory window 1: 54000000-57fff000
        I/O window 0: 00001000-000010ff
        I/O window 1: 00001400-000014ff
        16-bit legacy interface ports at 0001

03:0b.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
        Subsystem: Toshiba America Info Systems Unknown device 0001
        Flags: bus master, medium devsel, latency 64, IRQ 19
        Memory at 58005000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2

03:0b.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller (prog-if 01)
        Subsystem: Toshiba America Info Systems Unknown device 0001
        Flags: bus master, medium devsel, latency 64, IRQ 19
        Memory at 58006800 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2


All I need is SD card support. dmesg doesn't print ANYTHING when a card is inserted or removed.

Thanks for the help in advance, and thanks for creating such a fantastic Linux distribution!

---

