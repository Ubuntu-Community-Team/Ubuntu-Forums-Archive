---
title: "Big desktop using DVI, VGA and LVDS"
date: 2011-06-01
forum: Hardware
---

### Post by biofoder on 2011-06-01
I have an old Radeon X1600 graphics card in my laptop, and have it running with dual monitors using the VGA and DVI port. As far as I've been told, Radeon cards (with a few exception in the later 5000 series) only support dual monitors. However, I am almost certain that I once had a configuration with LVDS, VGA and DVI with my current setup. Am I just hallucinating or is it possible to activate LVDS and use three monitors (two external, laptop internal) with a single graphics card in Ubuntu/Linux?

All displays are detected using xrandr. Running Ubuntu 11.04.

biofoder@mymobo:~$ xrandr | grep connected
VGA-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
LVDS connected (normal left inverted right x axis y axis)
S-video disconnected (normal left inverted right x axis y axis)
DVI-0 connected 1280x1024+1280+0 (normal left inverted right x axis y axis) 338mm x 271mm

---

