---
title: "IBM R40e lucent/agere modem &amp; wireless won't work"
date: 2008-07-24
forum: Hardware
---

### Post by charonred on 2008-07-24
I just installed Ubuntu 8.04 on my old r40e thinkpad (2003 model), and it's running a treat.

I have the Ethernet working fine; but not the inbuilt Lucent/Agere dialup modem, nor my **Minitar wireless PCMCIA card**.

Is there a driver to get the dialup modem working - so I can still take it on the road as such.

I'm thinking the Minitar wireless card maybe a bit dated to get a suitable Linux driver; if so, then maybe a wireless USB dongle would be better - I can then use my 3 port USB 2.0 PCMCIA card and plug into that- can anyone recommend a wireless USB dongle that works with Ubuntu?

---

### Post by charonred on 2008-07-28
After reading a few other threads from the forum, I went to package manager and installed 'ndiswrapper'.

Once installed I just fired it up; then selected 'add a new driver', browsed my Minitar carbus driver CD (card must be plugged in first) and selected the Windows '.ini' file.

Once that was done, I went into configuration and applied my WLAN settings and closed it.

works a treat, good signal strength and reception.

Still need some advice on **inbuilt Modem  - Lucent/Agere AC'97**

---

