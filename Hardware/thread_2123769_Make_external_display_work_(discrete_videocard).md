---
title: "Make external display work (discrete videocard)"
date: 2013-03-08
forum: Hardware
---

### Post by dlazerka on 2013-03-08
I've installed Ubuntu, and external display was not recognized by xrandr, although it showed Ubuntu logo while it was loading.
I've tried to install drivers for NVidia (Bumblebee -- no changes, and those proprietary from NVidia website -- they broke something in my Ubuntu 12.10 window manage, so that it loaded without window borders, taskbar, nothing, so I reinstalled OS).

All what I actually needed is to just change BIOS setting to "Discrete Videocard". And voi-la, external monitor works smoothly! I haven't installed anything extra, just Ubuntu 12.04 out-of-the-box. 

It would be useful to add patch to Ubuntu default nvidia drivers that would use discrete videocard if external monitor plugged in.

My setup was: At first Ubuntu 12.10, after reinstall it's Ubuntu 12.04. Lenovo ThinkPad W530, NVidia K1000M (Optimus).

---

