---
title: "Monitor Resolution"
date: 2010-06-24
forum: Hardware
---

### Post by laialexander on 2010-06-24
I have Ubuntu 10.4 LTS installed on a DELL desktp with a DELL W1909 monitor.  Default resolution of the DELL W1909 should be 1440x900, however, only 1360x768 is available under [System] -> [Preferences] -> [Monitors].  The monitor was detected as "Unknown".

I do not have hope the Ubuntu to detect this DELL Monitor properly, but I would like to see the monitor could use correct resolution.  It would be much appreciated if anyone could help.

Please forgive me if this post is being posted on a wrong place.

Have a good day to all of you.

Alexander Lai

---

### Post by efflandt on 2010-06-24
Sounds like you are probably using VGA which does not seem to be able to determine your native video mode and assumes generic modes.  If you were using DVI or HDMI it would likely automatically recognize your native resolution (DVI worked automatically for for me with an older 1280x720 HDTV and for 1080p HDTV).

See what **xrandr** in an X terminal shows for your video device and modes.  You can use **cvt 1440 900 60** or **gtf 1440 900 60** to find possibly suitable modelines and **xrandr** to try them out (see **man xrandr**).

See [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by laialexander on 2010-06-24
I created a new mode using the commands as the following:

cvt 1440 900 60
# 1440x900 59.89 Hz (CVT 1.30MA) hsync: 55.93 kHz; pclk: 106.50 MHz
Modeline "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
xrandr --newmode "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
xrandr --addmode VGA-0 "1440x900_60.00"

I could setup using the new 1440x900 (16:10) resolution in Monitors.  However, after the system is being restarted, I have to do all over again.  Is it possible to permanently add this new mode to the system?
On the other hand, is it possible to use this resolution mode as the mode to be used on login screen?

I am very new to Ubuntu, my questions may be too stupid too most of you I know, your help is much appreciated.

Alexander Lai

---

### Post by dino99 on 2010-06-24
note that kernels now directly deals with X, and old xorg.conf often push up troubles

so try without xorg.conf

sudo rm -f /etc/X11/xorg.conf

---

