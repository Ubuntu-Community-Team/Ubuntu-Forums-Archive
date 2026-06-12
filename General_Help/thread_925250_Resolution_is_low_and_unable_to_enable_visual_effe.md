---
title: "Resolution is low and unable to enable visual effects."
date: 2008-09-20
forum: General Help
---

### Post by Poindexter on 2008-09-20
Resolution is low and unable to enable visual effects. It happen after I was trying to Disable Synaptics Touchpad for my laptop. 
This is what I did:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_synbackup

gksu gedit /etc/X11/xorg.conf

Scroll down the page until you see something like this:

Section “InputDevice”
Identifier “Synaptics Touchpad”
Driver “synaptics”
Option “SendCoreEvents” “true”
Option “Device” “/dev/psaux”
Option “Protocol” “auto-dev”
Option “HorizEdgeScroll” “0&#8243;
EndSection

Insert the following line just before the EndSection

Option “SHMConfig” “on”

Save the file and exit.

Press Ctrl + Alt + Backspace to restart X11.

After the restart I got a message that my screen resolution is now on low and when I try to enable visual effects got message unable to enable visual effects. Please help.



Dexx

---

### Post by Interpreter on 2008-09-20
Try this one to change the resolution 

```
sudo displayconfig-gtk
```

---

