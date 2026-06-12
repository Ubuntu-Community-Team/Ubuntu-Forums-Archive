---
title: "open source ATI driver + touchpad interaction causing system resets?"
date: 2008-02-24
forum: Hardware &amp; Laptops
---

### Post by mr-zap on 2008-02-24
Hi, I'm getting system crashes on my HP ZT3000 laptop that seem to be linked to both the display driver and the mouse / touchpad. I'm running a fresh install of 7.10.

- when I enable the open source ati driver for the Mobility Radeon 9200 (RV250 / FireGL 9000) and reboot or restart X -  straight system reset, no messages. Switching back to the basic vesa driver gives a completely stable system.

- however, everything is fine as soon as I plug in a USB mouse. With the external mouse, the system is stable and works perfectly under any stress, compiz is fine, can't find anything wrong with it.

The standard input device is a Synaptics touchpad - listed as SynPS/2 Synaptics Touchpad,

I reckon this could be a hardware thing since an XP installation has a similar problem (only works with 'safe mode' display driver without external mouse, everything functional with mouse plugged in). Plus it's persisted through more than one complete blank slate install. But the fact that it showed up hours after installing ubuntu and around the time I was tinkering with the synaptics SHMConfig parameters makes me think there has to be a solution somewhere in software or firmware...??

Any ideas or diagnostics are welcome as I just don't know where to start... Thanks a lot for your time and thanks to the forum regulars, you've helped me loads to iron out some of the ubuntu creases!

---

