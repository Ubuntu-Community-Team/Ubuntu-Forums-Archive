---
title: "Screens connected though docking station not detected. Latitude E6430. Intel. 13.04."
date: 2013-05-13
forum: Hardware
---

### Post by inlimbo on 2013-05-13
Hi guys,

I have two displays connected to a docking station though DVI. But xrandr is not able to find them. 
I'm using ubuntu 13.04, the intel driver i915 is used. Network and USB works fine through the docking. 

lspci:
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)

xrandr:
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 309mm x 174mm
VGA1 disconnected (normal left inverted right x axis y axis)

I have been googling for an hour now, but can't find anyone with the same problem.

---

### Post by inlimbo on 2013-05-13
I found a guide about this on: 
[https://github.com/Bumblebee-Project/Bumblebee/wiki/Multi-monitor-setup](https://github.com/Bumblebee-Project/Bumblebee/wiki/Multi-monitor-setup)

It seems that the DVI is connected to the nvidia chip, not the intel chip. Causing some problems.

---

