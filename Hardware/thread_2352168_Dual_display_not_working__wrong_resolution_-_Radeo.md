---
title: "Dual display not working / wrong resolution - Radeon/Lubuntu16.04"
date: 2017-02-10
forum: Hardware
---

### Post by ecapoe on 2017-02-10
Hello,

I try to install a second monitor (Samsung SF35, 22") on my laptop Asus F552E.
When connected, the main laptop monitor remains black and the external monitor (VGA connection) has the wrong resolution (1368x1080, same as laptop screen) instead of its own (1920x1080). The edges are cut and the whole display slightly blurred, and no way to have both monitors.

Graphic card is Radeon:

> 00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Kabini [Radeon HD 8330] [1002:9832] (prog-if 00 [VGA controller])

LXRandR sees only the laptop's resolution and offers no option to change.

xrand -q returns this

> xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1366 x 768, current 1366 x 768, maximum 1366 x 768
default connected 1366x768+0+0 0mm x 0mm
   1366x768      76.00*

There is no xorg.conf
Any help is welcome ! Thanks.

---

