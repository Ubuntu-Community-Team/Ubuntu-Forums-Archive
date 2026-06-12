---
title: "ubuntu 9.10  on hi-grade c2200 - unable to read EDID block."
date: 2009-11-16
forum: Hardware
---

### Post by crofty_boy on 2009-11-16
having problems with my sister laptop , trying too get it too see my lcd monitor and eventually will be hooked up too 28" lcd tv/monitor.

sarah@sarah-laptop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM
Integrated Graphics Device (rev 02)


dmesg

[  395.392302] i2c-adapter i2c-0: unable to read EDID block.
[  395.392306] i915 0000:00:02.0: VGA-1: no EDID data
[  395.461501] [drm] DAC-6: set mode 640x480 0
[  395.886295] i2c-adapter i2c-0: unable to read EDID block.
[  395.886299] i915 0000:00:02.0: VGA-1: no EDID data
[  395.892184] i2c-adapter i2c-1: unable to read EDID block.
[  395.892188] i915 0000:00:02.0: LVDS-1: no EDID data

sarah@sarah-laptop:~$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 2048 x 2048
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y
axis) 0mm x 0mm
  1280x800       60.0*+
  1024x768       85.0     75.0     70.1     60.0
  832x624        74.6
  800x600        85.1     72.2     75.0     60.3     56.2
  640x480        85.0     72.8     75.0     59.9
  720x400        85.0
  640x400        85.1
  640x350        85.1


i have seen lots of messages on the forums about editing the xorg.cfg
file but got a bit lost

any help please?

---

