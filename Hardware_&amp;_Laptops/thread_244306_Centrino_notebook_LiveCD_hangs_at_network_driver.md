---
title: "Centrino notebook: LiveCD hangs at network driver"
date: 2006-08-26
forum: Hardware &amp; Laptops
---

### Post by el3ktro on 2006-08-26
I'm trying to boot the LiveCD on my new Averatec 2460, it's a Centrino notebook. The boot hangs when it tries to load the network module for eth0. It first loads the "8139cp" driver for the RealTek 8139 chipset, but the module says that it's not an 8139 compatible chip and that the "8139too" driver should be loaded. The LiveCD loads this other module, but then the boot hangs and nothing happens.

It seems that the LiveCD loads the wrong network module. Is there any way to tell the LiveCD which network module to load, or to turn off networking at all during boot?

Tom

---

### Post by el3ktro on 2006-08-26
Hmm the preinstalled Windows XP tells me that it is an "RealTek RTL 8139/810x Family Fast Ethernet" network card. How can I find out which is the right kernel module for this network card?

Tom

---

### Post by el3ktro on 2006-08-26
Ok kind of talking to myself here. It seems the 8139 modules are making problems. In fact it seems that BOTH are being load , the 8139cp and the 8139too. How can I Tell the LiveCD / Desktop CD to only load one of these drivers?

Tom

---

