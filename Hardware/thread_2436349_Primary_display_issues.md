---
title: "Primary display issues"
date: 2020-02-04
forum: Hardware
---

### Post by steve60901 on 2020-02-04
I got a 3 monitor set up running on the GTX1060Ti. The center (main) is HDMI TV. The left is DVI-I the right is DVI-D (with dvi to vga adapter). I cannot for the life of me get ubuntu to open things on the monitor i have set as main. Everything wants to open on the left monitor. Even the login screen comes up on the left side. Games open on the left side, new windows open on the left side everything does... How can I get everything to open on the center screen... again already set it as main... and is it possible to get proprietary nvidia drivers?

---

### Post by CelticWarrior on 2020-02-04
Yes, you should install Nvidia drivers. Just open Additional settings, everything should be intuitive from there.

---

### Post by steve60901 on 2020-02-04
It would appear they were already installed, so everything was opening on the left monitor while center was set as main and the nvidia drivers and nvidia xserver settings application was also installed. navigated that a bit but didn't see anything that looked like a fix.

---

### Post by CatKiller on 2020-02-04
> **steve60901 said:**
> Everything wants to open on the left monitor. Even the login screen comes up on the left side. Games open on the left side, new windows open on the left side everything does... How can I get everything to open on the center screen.

It depends on how fortunate you are, how you've set things up, and how much you want to get your hands dirty.

If you're very fortunate, your UEFI will have an option for which output should be initialised first. That's where the boot information would be displayed and, in the absence of any other configuration, will be used as a hint by the autoconfiguration routines for which display is the primary display. Set that, it cascades through the autoconfiguration, job done. If you're lucky.

If you're quite fortunate, you already set up your multimonitor by manually creating an xorg.conf. If you did that, there's an option setting for which display is the primary, which should be then used by the display manager and window manager for determining where windows should open.

If you're a bit fortunate, since it relies on your window manager being friendly, your display options have a nice "Primary display" setting. KDE, which I use, has this, but I have no idea if Gnome does.

If you're relying entirely on autoconfiguration without any available tunables, things get a bit trickier. You may be able to use something like ```
xrandr --output XXXX --primary
``` to set one of your displays as the primary display. If you aren't sure what the name of the display is for the XXXX, you can use ```
xrandr --current
``` To the best of my knowledge, that setting wouldn't persist over reboots, but you could automate it in a script that gets run when you log in, or before the display manager starts, or whenever.

Otherwise you could recreate your multimonitor setup in an xorg.conf just so that you can add the Primary option to it. Which would be a pain, but is doable.

Window managers differ in where they open new windows. Some will try to remember where the window was the last time that you used it, some will default to the primary display, some will default to where the mouse pointer is, and so on. In some window managers this behaviour will be a configurable option; Gnome devs don't like users having configurable options in general.

---

### Post by him610 on 2020-02-05
Simple brute force method: physically reposition the monitors.

---

### Post by mastablasta on 2020-02-06
> **him610 said:**
> Simple brute force method: physically reposition the monitors.
:lolflag:

 good one.

i have similar issue, but one is large TV (DVI-D to HDMI) and the other one is small VGA monitor (VGA to VGA). nvidia pushes picture first to TV (doesn't matter if TV is connected or not), then to monitor. however i was able to set it up in KDE. so now on boot TV is used, then the output switches to monitor (and it turns off TV). however, it would occasionally move back to TV exclusively when running some full screen games. then i figured out that if i switch the full screen resolution it drops automatically to the smaller monitor.

AMD never had these issues, but my old radeon died.

---

