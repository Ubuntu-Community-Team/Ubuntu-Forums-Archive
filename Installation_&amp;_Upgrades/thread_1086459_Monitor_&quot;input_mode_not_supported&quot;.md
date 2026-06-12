---
title: "Monitor &quot;input mode not supported&quot;"
date: 2009-03-04
forum: Installation &amp; Upgrades
---

### Post by Stormblazer on 2009-03-04
Alright, I've used Linux in the past, but I've never used Ubuntu before now. I'm dropping it on an older system for my younger brother, and for the most part things went very smoothly. I was about 5s from manually installing the nvidia driver when I noticed the notification about restricted drivers, and used that instead. However, upon reboot the monitor refused to accept the input signal. It's an older LCD monitor, VGA input only, 1280x1024, video card is an old GeForce Ti4200 AGP card.

Oddly enough, if I put the same output to a newer, 1680x1050 LCD monitor, it worked fine. Even more bizarre, if I use the other monitor to change the resolution down to 1280x1024, and switch the cable to the other monitor, it works fine - until I reboot/restart X.

Now, on other Linux installations this would have been very simple, I would've just edited xorg.conf. Unfortunately, Ubuntu seems to use a completely different system as most of the normal entries in xorg.conf are flat out missing, and editing it directly did not function as I would have expected at all.

Does anyone have any idea what I can do?

---

