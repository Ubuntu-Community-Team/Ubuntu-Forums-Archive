---
title: "Screen size and resolution"
date: 2011-11-24
forum: Hardware
---

### Post by arshadparvez on 2011-11-24
AoA;

I have upgraded to Ubuntu 11.10 on HP Compaq 6720s notebook. Everything was working fine with 11.04. The widescreen aspect and actual resolution info has somehow been lost either during upgrade or my tweaking.

Supported resolution of the Compaq 6720s is 1280x800.

Some info about the system:

$ sudo lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GME965/GLE960 Integrated Graphics Controller (rev 0c)

$ sudo xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 800 x 600, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
1024x768 61.0*
800x600 61.0

I tried to manually add the resolution (1280x800) but that didn't work. Here is the result:
$ sudo xrandr --newmode "1280x800_60.00" 83.50 1280 1352 1480 1680 800 803 809 831 -hsync +vsync
xrandr: Failed to get size of gamma for output default
$ sudo xrandr --addmode default 1280x800_60.00
xrandr: Failed to get size of gamma for output default
$ sudo xrandr --output default --mode 1280x800_60.00
xrandr: Failed to get size of gamma for output default
xrandr: screen cannot be larger than 1024x768 (desired size 1280x800)

(Note: While max size reported by xrandr above is less than 1280x800,
ddcprobe detects everything correctly)

$ ddcprobe
vbe: VESA 3.0 detected.
oem: Intel(r)GM965/PM965/GL960 Graphics Chip Accelerated VGA BIOS
vendor: Intel Corporation
product: Intel(r)GM965/PM965/GL960 Graphics Controller Hardware Version 0.0
memory: 7616kb
mode: 1280x1024x256
mode: 1280x1024x64k
mode: 1280x1024x16m
mode: 1024x768x256
mode: 1024x768x64k
mode: 1024x768x16m
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 640x480x256
mode: 800x600x256
mode: 640x480x64k
edid:
edid: 1 3
id: 2774
eisa: AUO2774
serial: 00000000
manufacture: 1 2006
input: analog signal.
screensize: 33 21
gamma: 2.200000
dpms: RGB, no active off, no suspend, no standby
dtiming: 1280x800@60
monitorid: AUO
monitorid: B154EW02 V7

Presently I have display in the middle of my wide-screen with black on either side. Also OS detects lower max resolution of 1024x768.

Help is required.

regard

---

