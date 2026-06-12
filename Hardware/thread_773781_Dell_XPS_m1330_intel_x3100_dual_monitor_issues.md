---
title: "Dell XPS m1330 intel x3100 dual monitor issues"
date: 2008-04-29
forum: Hardware
---

### Post by fat_kanickel on 2008-04-29
Heya, been trying to figure out this problem for quite a while now. I am running an Ubuntu on the dell xps 1330 with the onboard intel x3100 graphics card and haven't figured out how to get an external monitor working. The gui interface isn't much of a help and according to xrandr, a 2nd monitor isn't even detected on the VGA output. I haven't tried the hdmi output yet, due to lack of the hardware. I am running a Kubuntu Gutsy 32bit.

Help is much appreciated.

---

### Post by matheeny on 2009-01-03
Did you ever figure this out?  I'm having the same problem using 8.04.

If I go into System->Preferences->screen resolution, the other monitor is listed and the resolution can be changed but it looks like its only capable of cloned display and not extended.  The x3100 also doesn't seem to support very high resolutions and as a result, it looks pretty shitty on my 22" monitor.

---

### Post by jpreston84 on 2009-01-05
I had a similar situation on my Inspiron 1318 (which has the same X3100 aka GM965 graphics). I wanted to use the built-in 1280x800 display, as well as an external 14.1" slim profile 1280x800 display I bought. However, trying to set them up side by side in KDE with KRandR failed -- it would only let me clone them.

Running xrandr from the terminal showed me why -- the virtual desktop was set for a max of 2048x2048 pixels. To fix it, I had to add a subsection to my /etc/X11/xorg.conf file (just search for how to increase virtual desktop size and you should find it). I told it to make the virtual desktop size 2560x800 (the combined resolution of my two LCDs when placed side by side).

After that, and a reboot, I was able to set up the second display via the terminal something like this:

```
xrandr --output LVDS --mode 1280x800 --pos 0x0 --output VGA --mode 1280x800 --pos 1280x0
```

This works. I recommend avoiding using the KDE GUI (KRandR). It seems to be buggy at the moment.

It should be noted however, that I am having a problem as the result of this setup. For whatever reason, my internal LCD (LVDS for xrandr) has 3D issues now. When I use compiz, and move windows, or use expo, etc, I end up with artifacts covering what should be the wallpaper area of my desktop. On my external monitor, which seems to be defined as the primary for whatever reason, everything displays fine, *including* wallpaper, etc.

This doesn't stop me from running dual displays, but I would like to know how to fix this, if possible.


[B][I]Edit: To fix the 3D glitches, you need the 2.5.x Intel drivers. These are apparently slated for release with Ubuntu 9.04, but there are backports that I'm now running, which seem to work just fine.

Get them at [https://launchpad.net/~intel-gfx-testing/+archive](https://launchpad.net/~intel-gfx-testing/+archive)

Note that I'm running Intrepid (8.10) and these drivers may or may not work for you.[/I][/B]

---

