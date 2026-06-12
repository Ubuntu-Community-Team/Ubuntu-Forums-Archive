---
title: "nVidia drivers make thinks look big?"
date: 2007-12-19
forum: Hardware &amp; Laptops
---

### Post by jstanczak on 2007-12-19
I have a:
01:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7900 GS (rev a1)

When I install the nvidia drivers thinks get bigger. The nv drivers look just fine. xvidtune and the nvidia-settings both show the correct resolution (1920x1200). I'm on a Dell Inspiron 9400. Anyone else have this issue? I'm running Xubuntu 7.10.

---

### Post by jstanczak on 2007-12-19
I think it's fixed. I just remover the default xorg.conf and ran nvidia-xconfig. Looks like it just set new refresh rates. It looks better.

---

