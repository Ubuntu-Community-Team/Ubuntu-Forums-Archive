---
title: "Picture-by-picture not working in 21.04"
date: 2021-05-14
forum: Hardware
---

### Post by ken3412gg on 2021-05-14
I have a wide-screen monitor that can do picture-by-picture (e.g. show output from desktop and laptop side-by-side).  When I do that, my experience is:

**Windows / Mac:**
OS automatically detects the screen width is now 'half' and resizes the desktop to fit the monitor without stretching

**Ubuntu 20.10: **
OS doesn't auto-detect new screen resolution, so desktop image is 'scaled down' by the monitor to be really small (unusable).  On 20.10, running the command xrandr was sufficient to trigger the OS to detect the new monitor resolution and resize the desktop.

So - 20.10 - not great, but workable.

**Ubuntu 21.04:**
OS doesn't detect the new screen resolution and running xrandr doesn't trigger detection of new screen resolution.  So far I've not found a way to trigger the OS to detect the new monitor resolution.

So - 21.04 - not really usable


The ubuntu system is using intel integrated graphics.   Doing ```
cat /sys/class/drm/card0-DP-2/modes
``` gives the original wide-screen monitor resolution not the current 'half-width' resolution.




Any thoughts on how to trigger 21.04 to check the monitor for the new monitor resolution?   I'm guessing it's something about the xrandr in 20.10 that caused the graphics driver to rescan the EDID that doesn't happen in 21.04 (due to Wayland?)

---

### Post by Holger_Gehrke on 2021-05-15
As the name **x**randr implies that tool is for X11. AFAIK there is no direct equivalent on Wayland.

Have you tried to use the graphical '[Display Settings]("https://help.ubuntu.com/stable/ubuntu-help/look-resolution.html.en")' ? That should work with Wayland, but I don't know if it rereads the EDID. AFAIK i2c - the serial bus used for transmitting EDID data and DDC/CI commands - doesn't allow the subordinate device to initiate communication; you'd have to have some program continuously reading the EDID to catch the change of resolution and make the graphics system aware of it.

Holger

---

### Post by ken3412gg on 2021-05-15
Thanks - unfortunately Display Settings isn't working.  Unplugging and re-plugging the monitor cable works, so there must be some path where the display driver triggers a resolution detection.

Time to dig into the driver source, I guess - see if i can figure anything out.

---

### Post by ken3412gg on 2021-05-19
I haven't found a solution yet - but leaving this breadcrumb in case it helps someone else.  Running this command:

echo detect > /sys/class/drm/card0-DP-2/status

Causes the graphics adapter to re-detect monitor resolutions, and the new resolution shows up as the first resolution in the output of this command:

cat /sys/class/drm/card0-DP-2/modes

The resolution still doesn't show up in the the Ubuntu display settings UI, so next step (I guess) is to find out how to have that update with the new resolution.

---

### Post by ajgreeny on 2021-05-19
Does the resolution show in the output of ***xrandr*** if you change to an xorg session?

---

### Post by ken3412gg on 2021-05-21
xrandr wasn't doing much for me.  I found this worked in the end (run as sudo):

```
#! /bin/sh

# Causes the monitor resolution to be re-probed by turning
# the monitor off and on again.

echo off > /sys/class/drm/card0-DP-2/status
echo on > /sys/class/drm/card0-DP-2/status
```


At some point i might figure out a daemon that polls doing a redetect and then simulates monitor off/on when it detects the available resolutions has changed, but for now this is working.

---

