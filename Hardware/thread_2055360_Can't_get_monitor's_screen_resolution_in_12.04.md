---
title: "Can't get monitor's screen resolution in 12.04"
date: 2012-09-09
forum: Hardware
---

### Post by andrewkirk on 2012-09-09
Hello. I just upgraded from 10.04 to 12.04.
After a few initial obstacles it's now going well, except I can't get the 'Settings>Displays' dialog to offer me the screen resolution native to my monitor, which is 1280 x 1024

I have tried putting it in the xorg.conf file but it gets ignored.
I have also tried via xrandr and have executed the following commands without error messages. But still no luck.

cvt 1280 1024 60
[this gave output # 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
]

Then the following commands:

xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
xrandr --addmode  VGA-0 1280x1024@60

Monitor is LG L1811S
Graphics Card is Radeon HD 4350, and driver from AMD site for it has been installed (amd-driver-installer-12.6-legacy-x86.x86_64.run) without any reported errors.
xorg.conf file is attached.

I hope somebody can help. :-)

---

