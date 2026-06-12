---
title: "How could I make my multimedia reader work?"
date: 2006-03-08
forum: Hardware &amp; Laptops
---

### Post by gohanUbuntu on 2006-03-08
Hello everyone:

I have a **HP Pavilion dv1000** working perfectly except for the **multimedia reader**. I've looking for an answer in google, but I've not found anything helpful...

gohan$ lspci -v

...
0000:06:09.3 Unknown mass storage controller: Texas Instruments: Unknown device 8033
        Subsystem: Hewlett-Packard Company: Unknown device 3080
        Flags: bus master, medium devsel, latency 57, IRQ 11
        Memory at b0104000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: [44] Power Management version 2

0000:06:09.4 0805: Texas Instruments: Unknown device 8034
        Subsystem: Hewlett-Packard Company: Unknown device 3080
        Flags: bus master, medium devsel, latency 57, IRQ 11
        Memory at b0108400 (32-bit, non-prefetchable) [size=256]
        Memory at b0108000 (32-bit, non-prefetchable) [size=256]
        Memory at b0106400 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

I have no idea what to do and how...could someone give me a clue please.

gohanUbuntu
Mexico.

---

### Post by Whoopie on 2006-03-10
Hi,

have a look at [http://mmc.drzeus.cx/wiki/Linux/Drivers/sdhci](http://mmc.drzeus.cx/wiki/Linux/Drivers/sdhci)

But you have to patch and build your own kernel.

Best regards,
Whoopie

---

### Post by mjg59 on 2006-03-12
Should work out of the box in Dapper.

---

