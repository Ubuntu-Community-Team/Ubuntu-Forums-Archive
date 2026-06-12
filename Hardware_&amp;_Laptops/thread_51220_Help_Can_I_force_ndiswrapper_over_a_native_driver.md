---
title: "Help: Can I force ndiswrapper over a native driver?"
date: 2005-07-23
forum: Hardware &amp; Laptops
---

### Post by gmc on 2005-07-23
Hello Folks,

I'm in need of a little assistance here. I've got a SMC 2635W wireless pcmcia card that uses the adm8211 chipset (rev 20). To my complete suprise, Ubuntu thoughtfully includes the native driver for this chipset. Unfortunately the driver is proving to be very unreliable. If the card is put under any sort of extended load, for example downloading the kernel source, it will generate an "FBE" error and stop working. The only solution to this is to reboot the machine or use cardctl to reset the pcmcia ports.

I decided to try the ndiswrapper and native windows drivers and see if that is any more reliable. Does anyone know how I can force the system to ignore the adm8211 driver and use the ndiswrapper drivers?

G.

---

### Post by elsewhere on 2005-07-23
Try adding **adm8211** to your hotplug blacklist (*/etc/hotplug/blacklist*).  This should prevent the system from automatically loading the driver when it recognizes your card.

I had to do the same thing to get ndiswrapper working with my wifi card, the system was automatically loading an incompatible driver thus preventing ndiswrapper from controlling it.

Hope this helps...

Cheers,
KV

---

### Post by gmc on 2005-07-24
Perfect! works like a charm.

Thanks

G.

---

### Post by elsewhere on 2005-07-24
Glad to hear it worked !

Cheers,
KV

---

