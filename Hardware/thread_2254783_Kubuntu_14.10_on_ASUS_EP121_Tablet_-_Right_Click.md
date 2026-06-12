---
title: "Kubuntu 14.10 on ASUS EP121 Tablet - Right Click?"
date: 2014-11-29
forum: Hardware
---

### Post by m.lp.ql.m on 2014-11-29
Just installed Kubuntu 14.10 on my ASUS EP121 tablet. Was running Ubuntu 14.10, but for some reason, the WiFi and Bluetooth works better in Kubuntu. :)

All I'm trying to do is to eek out some sort of right click capability from the touchscreen--2 finger click, click-and-hold, CTRL-click--at this point, I don't care.

System Settings -> Input Devices -> Touchpad -> Taps tab has all options greyed out. A red banner at the top reads "Synaptics driver is not installed (or is not used)". The Enable/Disable Touchpad tab is also all greyed out. 

Trying to install xserver-xorg-input-synaptics reveals that it's already at the newest version. The few Google hits I got seemed to imply that the synaptics driver just doesn't work in Kubuntu.

I was able to enable click-and-hold as a right click in Ubuntu using dconf-editor, where it's just an option to select.

Any ideas?

Thanks!

---

### Post by ajgreeny on 2014-11-30
See if command **synclient -l** gives you any clues.  It might not, as I think that is the list of synaptics driver settings, but it may lead to more information about what is going on, and will at least prove that you need to search out the touchpad make installed.

---

### Post by m.lp.ql.m on 2014-12-03
```
mark@fieval:~$ synclient -l
Couldn't find synaptics properties. No synaptics driver loaded?
```

xserver-xorg-input-synaptics package IS installed, however. Reinstalling did nothing new.

Attempted installing the 3 packages listed at [http://linuxwacom.sourceforge.net/wiki/index.php/Downloads](http://linuxwacom.sourceforge.net/wiki/index.php/Downloads), but I ended up in a dependency hell: I couldn't compile one of the dependencies because "x11" wasn't installed-- which package exactly is that?

My touchscreen is correctly identified as a Wacom. System Settings->Input Devices has a "Wacom Tablet Settings" tab, but offers right-click and middle-click options for the wrong stylus. My stylus, the one that came with the ASUS EP121, has no buttons on it.

---

