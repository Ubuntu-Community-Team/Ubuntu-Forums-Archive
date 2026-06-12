---
title: "convert xrandr to xorg.conf settings"
date: 2008-10-07
forum: General Help
---

### Post by kirkilj on 2008-10-07
Migrating from MS-Windows...

I configured my desired display settings with the following xrandr commands:

# xrandr --output LVDS --off
# xrandr --output VGA --mode 1920x1200

This turns of my laptop's display and sets up the proper resolution of my external monitor.

What would be the equivalent xorg.conf settings OR would it just be easier to throw the xrandr commands into a login script of some type?

John

---

### Post by ajmorris on 2008-10-08
> **kirkilj said:**
> Migrating from MS-Windows...

I configured my desired display settings with the following xrandr commands:

# xrandr --output LVDS --off
# xrandr --output VGA --mode 1920x1200

This turns of my laptop's display and sets up the proper resolution of my external monitor.

What would be the equivalent xorg.conf settings OR would it just be easier to throw the xrandr commands into a login script of some type?

John

hi there,
you could do some sort of twin view, to mirror your laptop's display to the external monitor... i.e. an xorg.conf device section like:

```
Section "Device"
    Identifier     "Some Identifier"
    Driver         "your xorg driver"
    Option "TwinView" "Yes"
    Option "TwinViewOrientation" "Clone"
    Option "MetaModes" "1920x1200"
EndSection


```
that way your laptop monitor could be shut, with the display still 
mirrored onto your external display.

You could alternatively create a bash script and add it to boot, to run
your xrandr commands...

there is also the option of having 2 X sessions running, with one (say TTY7
for your laptop's monitor display) and a second one for your external monitor,
with a second xorg.conf for your external display, with the above device secion,
which could then be referenced by:
```
Xorg :2 -ac -config /etc/X11/xorg.conf.alternate

```

I think the twinview option could be the best option though :)


AJ

---

