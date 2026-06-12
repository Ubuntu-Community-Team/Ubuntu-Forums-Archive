---
title: "Cardbus problems on Cinet SmartBook 440"
date: 2005-09-23
forum: Hardware &amp; Laptops
---

### Post by pepzi on 2005-09-23
Hello fellow human beings!

First of all, Ubuntu is great! I've been running Slackware since 1998, but when I recently bought this laptop I thought I'd try something new, and I totally love it :)

Tonight has been a long night though, trying to get my D-Link DWL-G650+ cardbus adapter to work. First I thought it was a wlan-driver problem, trying everything I could read about this and similar cards on this forum. After a while I figured it must probably be a cardbus problem instead.

I am not experienced with PCMCIA/CardBus, and I'm not even 100% sure my laptop (an AMD XP 1900+) has CardBus anymore? It has two sockets, which the adapter only fits in one of them. I believe the upper card is 16bit-PCMCIA, and the lower is 32bit-CardBus though. Here is what lspci -v has to say about it:

0000:00:0a.0 CardBus bridge: O2 Micro, Inc. OZ6912 Cardbus Controller
        Subsystem: QUANTA Computer Inc: Unknown device 9905
        Flags: bus master, stepping, slow devsel, latency 168, IRQ 11
        Memory at 0c000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
        Memory window 0: 10000000-103ff000 (prefetchable)
        Memory window 1: 10400000-107ff000
        I/O window 0: 00004000-000040ff
        I/O window 1: 00004400-000044ff
        16-bit legacy interface ports at 0001

This is what's in dmesg that has to do with this:

Linux Kernel Card Services
  options:  [pci] [cardbus] [pm]
<snip>
Yenta: CardBus bridge found at 0000:00:0a.0 [152d:9905]
Yenta O2: res at 0x94/0xD4: 00/ea
Yenta O2: enabling read prefetch/write burst
Yenta: ISA IRQ mask 0x0000, PCI irq 11
Socket status: ffffffff

cardctl status outputs:
Socket 0:
  no card

Telling me it only found one socket :(

I've now compiled and recompiled my own kernel numerous times. When I only select  32bit-CardBus, it doesnt find anything PCMCIA/CardBus at all. :/ Does anyone have any clue at all what might be wrong? I've looked at my BIOS-settings, but it's very limited, with no options whatsoever that has anything with PCMCIA/CardBus to do. This is extremely frustrating :/

When searching Google I've found people talking about patching the Yenta-driver but I'm currently to tired to dig in to it any furter than that right now. I doubt that it would help anyways. This is my last shot for the night, hopefully someone can give me some tips here :)

For the record: I'm running linux 2.6.10 right now.

---

