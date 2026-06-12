---
title: "ATI Radeon X550 pci driver for ubuntu 5.10"
date: 2006-02-08
forum: Installation &amp; Upgrades
---

### Post by x-ph on 2006-02-08
When I installed ubuntu on my AMD Opteron 64bit PC the x server couldn't start because of error. I reconfigured it and using VESA display driver it started, but I can't make the resolution of the screen higher than 1024x768@75Hz (on 19" CRT monitor)... My video card is ATI Radeon X550 pci and I need some help to install a proper driver. Thanks in advance.

---

### Post by x-ph on 2006-02-10
Well, I surrender. I'll change the linux distribution...

---

### Post by Teroedni on 2006-02-10
hello
i think you only need to edit your vert and horinz to get hiigher resolutions:)

Could you paste your xorg.conf file

In Terminal

write
```
sudo gedit /etc/X11/xorg.conf
```

---

