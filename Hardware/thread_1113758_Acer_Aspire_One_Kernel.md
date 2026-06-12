---
title: "Acer Aspire One Kernel"
date: 2009-04-02
forum: Hardware
---

### Post by kev000 on 2009-04-02
Trying out several kernels from around the web (eeebuntu, kuki's sickboy kernel), I decided to compile my own.

The reason for this is that eeebuntu's is too old (2.6.27) and has ALSA issues.  Kuki's is slightly newer/faster (2.6.28), but lacks prolific pl2303 support which I need for my GPS receiver.

I started with Kuki's config and added prolific usb/serial support with the 2.6.29 vanilla kernel source.  This boots fast and works great except for compiz/gfx accelleration.  Compiz runs noticeably slower and I get a good 20fps less when running glxcube.

Anyone have any suggestions on things I can try to improve DRI performance in my kernel?

Attached is the config for my kernel if anyone wants to try it out.

---

### Post by Harani on 2009-05-06
am fairly new to ubuntu and am running sickboy/kuki kernel on my acer aspire one (much faster boot times !) however i have the same problem that i need the prolific serial USB driver for my GPS unit.

Would be grateful for any tips on how to install this

Thanks

Glen

---

