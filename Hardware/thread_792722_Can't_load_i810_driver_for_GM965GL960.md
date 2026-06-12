---
title: "Can't load i810 driver for GM965/GL960"
date: 2008-05-13
forum: Hardware
---

### Post by Nano on 2008-05-13
I'm running an Acer Extensa 5620 and I still cannot load Intel i810 driver.
Doesn't matter what I choose it keeps VESA driver.

Weird thing is that I can use compiz pretty decently.
From glxinfo:
```

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2

```

and from xorg.conf
```

Section "Device"
	Identifier	"Configured Video Device"
EndSection

```

Any tips?

---

### Post by hermes0710 on 2008-05-13
Can you post your dmesg output? How do you know the driver is not in use?
Post you lsmod output too if you can.

---

