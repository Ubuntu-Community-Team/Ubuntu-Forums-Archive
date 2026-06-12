---
title: "Virtual PC, IBM T42: Video Problem"
date: 2007-02-11
forum: Hardware &amp; Laptops
---

### Post by pvravi on 2007-02-11
Hi,

I installed Ubuntu (6.10) on a Virtual PC on Win XP. Out of the box, it works OK. I tried to install XGL and Beryl. Then the problems started:

My T42 comes with a ATI Radeon Mobility 7500. (I understand that this card is a bit dicey for Beryl). However, Ubuntu detected the card as a "S3 Inc. 86c764/765 [Trio32/64/64V+]". I tried replacing this with the generic "radeon" driver in the xorg.conf. No go: X says no devices detected. So also with the generic "ati" driver.

Why does this happen? How can I get video recognized as an ATI device, install appropriate drivers, and get Beryl up and running? 

Thanks much
pvravi

---

### Post by pvravi on 2007-02-11
lspci shows this:


00:08.0 VGA compatible controller: S3 Inc. 86c764/765 [Trio32/64/64V+] (prog-if 00 [VGA])
        Flags: bus master, fast devsel, latency 0
        Memory at f8000000 (32-bit, non-prefetchable) [size=64M]

---

### Post by ltmon on 2007-02-11
Hardware accelerated video does not work at all inside Virtual PC.

The S3 video card detected by Ubuntu is not your real video card, just the generic virtual one that Virtual PC presents to the operating system.  This is why the "radeon" and "ati" drivers are not working for you.

You will have to install directly on the hardware in order to get this kind of stuff working.

---

### Post by pvravi on 2007-02-11
Thanks. That was the conclusion I came to.

---

