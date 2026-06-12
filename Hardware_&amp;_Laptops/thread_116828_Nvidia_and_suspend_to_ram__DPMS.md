---
title: "Nvidia and suspend to ram / DPMS"
date: 2006-01-13
forum: Hardware &amp; Laptops
---

### Post by glacierre on 2006-01-13
I'm using the deb-packaged propietary drivers for nvidia on a Toshiba Tecra M4 (nvidia geforce go 6200/6600)

My problem is that, although I can hibernate (suspend to disk) seamlessly, I can't properly suspend to ram (after activating it on /etc/default/acpi-support).

More precisely, I can suspend  but the screen won't wake up from that state.

I've also tried to turn off the screen manually using DPMS and xset (since I have the option on xorg.conf, but doesn't get activated itself and have to force it), with the same results, I cannot turn it on back.

Anyone knows how to get at least DPMS working? (or a way to turn off the screen without shutting down the whole laptop) Thanks.

---

