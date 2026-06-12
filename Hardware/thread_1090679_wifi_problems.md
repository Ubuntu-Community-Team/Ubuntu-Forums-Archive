---
title: "wifi problems"
date: 2009-03-08
forum: Hardware
---

### Post by lyratzis on 2009-03-08
Hey

My laptop just stopped detecting wireless internet at some point (I am not sure exactly how long ago it was) and I really don't understand why. 

"sudo pccardctl ident" doesn't return anything
 
and the relevant parts of "lspci -v | less" are

09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
        Subsystem: Dell Unknown device 022f
        Flags: bus master, fast devsel, latency 0, IRQ 219
        Memory at fe8fc000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at de00 [size=256]
        Capabilities: <access denied>

0b:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
        Subsystem: Intel Corporation Unknown device 1120
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at fe7fe000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>

The thing is, it used to work fine. I had a similar problem with my webcam; one day, it just stopped working. Maybe I am just unlucky with hardware or something, but to me it seems more like detection issues. I don't understand why ubuntu does this to me. Does anyone have any suggestions for getting my wifi working again?

---

