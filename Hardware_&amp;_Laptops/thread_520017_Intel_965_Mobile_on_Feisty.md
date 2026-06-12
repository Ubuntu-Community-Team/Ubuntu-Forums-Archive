---
title: "Intel 965 Mobile on Feisty"
date: 2007-08-07
forum: Hardware &amp; Laptops
---

### Post by kooseefoo on 2007-08-07
Okay, I've found about a thousand threads on this forum talking about the 965 chipset, but there's one slight problem: everybody seems to be having resolution problems.

I can't even get the xserver to start. I've played around with dpkg-reconfigure xserver-xorg a bit, but I really don't know squat about X, so it's not doing any good.

This is a completely untouched install of Ubuntu Feisty (used the Alternate install CD). It has the 2.6.20 kernel (I read about needing the 2.6.18 or more for kernel support). I've tried the i810 driver in the dpkg-reconfigure, but still the same thing. I get a message about the xserver failing to start and end up at a terminal.


Any help?

---

### Post by Syke on 2007-08-07
Give Gutsy a try just to see if the new video drivers work on your system. It's probably not stable for serious work, but it'll give you hope that your system is compatible.

Hopefully fully supported drivers will be available in Feisty soon.

---

