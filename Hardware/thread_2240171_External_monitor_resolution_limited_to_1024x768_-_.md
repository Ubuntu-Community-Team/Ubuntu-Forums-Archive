---
title: "External monitor resolution limited to 1024x768 - Intel Graphics"
date: 2014-08-18
forum: Hardware
---

### Post by rcasha on 2014-08-18
I have an HP Probook 450 G1 laptop, with Intel graphics, connected to an external HP S2231a monitor. The monitor should be able to go up to 1920x1080x60Hz but I can't get it to go beyond 1024x768. It is shown as "Unknown display" in the displays control panel.

I tried using xrandr as follows:
$ gtf 1920 1080 60

  # 1920x1080 @ 60.00 Hz (GTF) hsync: 67.08 kHz; pclk: 172.80 MHz
  Modeline "1920x1080_60.00"  172.80  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync

$ xrandr --newmode  "1920x1080_60.00"  172.80  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync
$ xrandr --addmode VGA1 1920x1080_60.00
$ xrandr --output VGA1 --mode 1920x1080_60.00
xrandr: Configure crtc 1 failed

The XOrg.0.log file contains:
[  2052.888] (II) intel(0): switch to mode 1920x1080@60.0 on VGA1 using pipe 1, position (0, 0), rotation normal, reflection none
[  2053.080] (EE) intel(0): failed to set mode: Invalid argument
[  2053.413] (II) intel(0): resizing framebuffer to 2390x768
[  2053.419] (II) intel(0): switch to mode 1366x768@60.0 on eDP1 using pipe 0, position (1024, 0), rotation normal, reflection none
[  2054.138] (II) intel(0): switch to mode 1024x768@60.0 on VGA1 using pipe 1, position (0, 0), rotation normal, reflection none

more info: 
inxi -G
Graphics:  Card: Intel 4th Gen Core Processor Integrated Graphics Controller 
           X.Org: 1.15.1 drivers: intel (unloaded: fbdev,vesa) Resolution: 1366x768@60.0hz, 1024x768@60.0hz 
           GLX Renderer: Mesa DRI Intel Haswell Mobile GLX Version: 3.0 Mesa 10.2.2

Any suggestions please?

---

