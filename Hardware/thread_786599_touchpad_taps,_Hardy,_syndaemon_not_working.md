---
title: "touchpad taps, Hardy, syndaemon not working"
date: 2008-05-08
forum: Hardware
---

### Post by raequin on 2008-05-08
Hi. I have an Acer laptop. When I type, the touchpad will often cause a click where the pointer is, so the cursor ends up jumping around.

I have tried many things, the only solution so far is to use the touchpad on/off button (fn+f7) on my laptop. Even System+Preferences+Mouse+Touchpad->disable mouse clicks with touchpad has no effect.

I have edited xorg.conf and run syndaemon without result. Here is the touchpad section of that file.

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizEdgeScroll" "0"
Option "SHMConfig" "on"
# Option "MaxTapTime" "0"
EndSection

I commented out the maxtaptime, because it had no effect.

I have run syndaemon both with and without options --- no effect.

Thanks for helping me get this working.

One other option would be a keyboard shortcut that I can access from the home position (Emacs has spoiled me).

 ps --- Vertical scrolling is not working either. That would be nice.

---

### Post by kpkeerthi on 2008-05-08
Did you restart X after making changes to xorg.conf?

---

### Post by raequin on 2008-05-09
Yes, I have restarted X (Ctrl+Alt+backspace), and also restarted the computer.

---

### Post by raequin on 2008-05-09
I can even go in System->Preferences->Mouse and uncheck the box that says "Enable touchpad," and nothing changes.

---

