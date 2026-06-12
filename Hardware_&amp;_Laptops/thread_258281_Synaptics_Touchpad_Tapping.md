---
title: "Synaptics Touchpad Tapping"
date: 2006-09-15
forum: Hardware &amp; Laptops
---

### Post by pelagic on 2006-09-15
Hello all,

yes I'm also one of those with a touchpad and I can't stand the "tapping feature" and I can't disable it (not the pad, only the tapping).

So I'd appreciate any help.
Here is my xorg.conf:
```
...
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"            "on"
        Option          "MaxTapTime"            "0"
EndSection
... ... ...
        InputDevice     "Synaptics Touchpad"
...
```

and a maybe interesting line from Xorg.0.log:
```
...
(II) LoadModule: "synaptics"
(WW) Warning, couldn't open module synaptics
(II) UnloadModule: "synaptics"
(EE) Failed to load module "synaptics" (module does not exist, 0)
... ...
(**) Configured Mouse: Buttons: 9
(EE) No Input driver matching `synaptics'
...
```
Any idea?

---

### Post by Henry Rayker on 2006-09-16
I would backup your xorg.conf file and run

dpkg-reconfigure xserver-xorg

and make sure that, when it asks about your mouse, you set it to ExplorerPS/2. I had ALL SORTS of problems with it before I did that, and now it sets up just fine. After that, open the xorg.conf file (the new one) and set the MaxTapTime = 0 and see if it works.

I'm not sure when/how the tapping annoys you, but if it is only when you're typing (i.e. you accidentally tap the pad and it changes your position or something, you can add

syndaemon -i 0.5 -d

to your sessions startup programs. This will disable the touchpad for half a second after you do any typing on the keyboard. You can change the time by changing the 0.5 to whatever you want, in seconds.

I hope that helped.

---

