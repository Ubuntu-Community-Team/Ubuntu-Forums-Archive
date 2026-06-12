---
title: "Yamaha PCI Sound card problem"
date: 2009-12-06
forum: Hardware
---

### Post by mahadevan on 2009-12-06
Hi guys,

I'm a newbie in Linux. I installed Karmic yesterday. There is some problem detecting my Yamaha PCI sound card. 

Heres the output of lspci -v

06:05.0 Multimedia audio controller: Yamaha Corporation DS1L Audio
    Subsystem: Yamaha Corporation DS-XG PCI Audio CODEC
    Flags: medium devsel, IRQ 17
    Memory at 92000000 (32-bit, non-prefetchable) [size=32K]
    Capabilities: [50] Power Management version 1
    Kernel modules: snd-ymfpci


I went to the alsa site, downloaded ymfpci source, compiled it. Then downloaded ymfpci lib, compiled it. Then downloaded ymfpci utils, compiled it also. It all seemed to compile well. Then I type 

modprobe snd-ymfpci.

This gives me no output. In fact I try 

aplay -l and the output is

aplay: device_list:223: no soundcards found...

**When I run alsaconf, it is showing my soundcard, When I choose it, it says the card is configured and ready for use, but its not.**

Hope it makes some sense.

Thanks

---

### Post by mahadevan on 2009-12-06
anyone ??? :)

---

