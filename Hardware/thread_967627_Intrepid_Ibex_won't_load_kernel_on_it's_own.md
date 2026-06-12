---
title: "Intrepid Ibex won't load kernel on it's own"
date: 2008-11-02
forum: Hardware
---

### Post by Ozzi on 2008-11-02
Hi,

I have an HP Pavilion DV 9500 (DV 9645 ED more precisely) laptop.

Whenever I try to boot the new Intrepid Ibex the kernel won't load unless I keep a key (any key) pressed on my keyboard. It seems to be getting stuck on each component discovery.

This happens both when booting the CD and loading up the newly installed system with both ubuntu 32 and 64 bit edition.

I've had some serious trouble with this laptop when I first bought it (on almost all systems including a 2.6.22 kernel). I had to recompile the kernel without hardware IRQ support but this was fixed from version 2.6.23 onward.

Did anybody else experience these problems and/or knows any way to fix it?

Thanks

PS: I've attached the output of lspci and the kernel log from the Live CD

---

