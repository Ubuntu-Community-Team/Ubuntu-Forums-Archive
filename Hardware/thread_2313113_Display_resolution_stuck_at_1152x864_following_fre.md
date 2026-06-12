---
title: "Display resolution stuck at 1152x864 following fresh 14.04 desktop install"
date: 2016-02-09
forum: Hardware
---

### Post by wdweisman on 2016-02-09
Lots of similar issues out there, but a whole bunch of different solutions - not sure which if any applies to my situation.  I did a fresh 14.04 desktop install yesterday, during which I had to set "nomodeset" to keep the video from going haywire during the install.

After the install finished, I went into System Settings -> Displays.  The only available resolution for the built-in display is 1152x864, and most of the menu choices are grayed out.  The max resolution for the Radeon HD is 2560x1600.  How do I get more resolution choices?

HP Pavillion Model #p7-1258
AMD A8-3820 APU w/ Radeon HD Graphics
8G DDR3 1333Mhz dual-channel memory

Display is an HP s2031 LCD monitor, 1600x900, DVI-D

# xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1152 x 864, current 1152 x 864, maximum 1152 x 864
default connected primary 1152x864+0+0 0mm x 0mm
   1152x864       76.0* 
#

SOLVED:  used additional drivers, did install-update of proprietary driver

---

