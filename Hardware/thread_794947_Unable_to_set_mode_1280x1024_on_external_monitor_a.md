---
title: "Unable to set mode 1280x1024 on external monitor after X restart"
date: 2008-05-15
forum: Hardware
---

### Post by mojones on 2008-05-15
I'm running Hardy on a thinkpad x61t and use an external monitor while at work.  If the monitor was connected when I started the xserver, this works perfectly:

xrandr --output VGA --mode 1280x1024 --output LVDS --off

However, if the external monitor wasn't connected when I started up (e.g. I booted up at home, went into suspend, then came to work) I get:

xrandr: cannot find mode 1280x1024

Restarting X solves the problem.  I assume that this is because xserver detects external display at startup and dynamically generates a list of supported modes.  Is there any way I can get X to regenerate the list of modes without restarting?

---

