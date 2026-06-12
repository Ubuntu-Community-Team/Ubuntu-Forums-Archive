---
title: "Lenovo T61, no display on external screen, when docked"
date: 2011-12-30
forum: Hardware
---

### Post by venturax on 2011-12-30
Hi,
I installed Ubuntu 11.10 on a Lenovo T61 and everything went fine, during the install.

When i dock the machine and turn on, my external monitor (Dell 2001FP) does turn on and i see console+ initial Ubuntu boot. When Ubuntu opens the login manager, the monitor turns black and says no screen input. If i open the laptop lid, i see the login manager on the internal display.

I can see, that the proprietary Nvidia driver (Quatro 140) does detect the Dell monitor on DFP-1 and the internal LCD on DFP-0, but in have only the Screen-0 device listed in the nvidia graphics manager.

xrandr also only reports one display (the internal LCD).

Just for fun I tried to uninstall the nvidia driver and replace it with the MESA one. I checked with glxinfo to verify the driver was replaced.

Using the MESA driver does work both docked and undocked, but the hardware acceleration is missing, thus unity becomes too sluggish for everyday use.

I really want the nvdia driver to behave, properly, but right now I'm out of ideas :(

---

### Post by yaco8 on 2012-02-07
Hi
Did you find a solution to this problem? I have the exact same issue
cheers
Yannick

---

### Post by venturax on 2012-02-15
Sadly not. Are not closer to a solution currently :(

---

