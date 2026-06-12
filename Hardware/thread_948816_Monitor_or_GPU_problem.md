---
title: "Monitor or GPU problem?"
date: 2008-10-15
forum: Hardware
---

### Post by hiacynt on 2008-10-15
Hi, I'm experiencing a strange problem, namely when I install the drivers for my GPU (GeForce 7600 Go), I loose all but the native (1680x1050) screen resolution options, get wrong refresh rate (50Hz instead of 60) and the fullscreen support is messed as well. I tested it by running an app that goes fullscreen by default, and it did in a way (didn't run in a window), just that the resolution remained 1680x1050, and the app run in a part of it. In the rest of the screen the desktop was fully visible.
If I don't use the drivers, I've got plenty of resolutions to chose from and they work properly. Sometimes, when I turn the drivers on, and later turn them off, I am returned to some failsafe screen drivers/options, and am left with 800x600, which can only be fixed by running in the recovery mode and fixing the xorg server through it.

I looked around for answers, and tried some of them, like reconfiguring the xorg, but to no avail (all I got were some keyboard questions instead of graphics-related ones). I tried the latest drivers from Nvidia, Nvidia xsserver config, also some drivers through EnvyNG, but got the same effect, which makes me think that it's more of a problem with the monitor rather than with the GPU. The Nvidia xserver settings identifies it as 'Seiko', and although I do not know for sure about that, I couldn't find any related monitor drivers.

Specs:
Ubuntu 8.04 (installed through Wubi, with all current updates)
Intel Core Duo 2x1.66Ghz, 1024 RAM, GeForce 7600 Go. If needed I can provide with some more detailed specs from lshw or something.
My laptop is a California Access M158, if that's of any help.
Thanks a lot for any help :)

---

