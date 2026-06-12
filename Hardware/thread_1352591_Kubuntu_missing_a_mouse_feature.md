---
title: "Kubuntu missing a mouse feature?"
date: 2009-12-11
forum: Hardware
---

### Post by jessiebrownjr on 2009-12-11
I just switched from gnome 32bit to KDE 64 bit 9.04, and I have a problem now. My touchpad on the laptop is very sensitive.. I have to disable clicking with the actual pad (not the buttons but the pad you touch to move the mouse around)... if I don't disable this, it ports my cursor around from random "mouse clicks" from the palm of my hand. Does anybody know the RIGHT way to disable the keybad from clicking? Gnome had it under the mouse preferances, KDE doesn't.. Lost... This is going to be a 100% deal breaker if I can't disable it.. help!

---

### Post by Zorael on 2009-12-12
Yes, there's currently no touchpad section anywhere in System Settings on a default installation. [It exists](http://www.kde-apps.org/content/show.php/kcm_touchpad?content=113335), but it's not part of KDE 4.3. Not sure if it will officially be in 4.4.

You can either compile it and install it yourself, or add a PPA that has it and install it from there.

The developer himself has it on his PPA (**[ppa:mishaaq/ppa](https://launchpad.net/~mishaaq/+archive/ppa/)**), and when doing a [PPA search for kcmtouchpad](https://launchpad.net/ubuntu/+ppas?name_filter=kcmtouchpad) two more show up. I'd try the developer's.

Another alternative would be to make a script that disables tapping and put it in your **~/.kde/Autostart** directory. (Assuming you have a Synaptics pad.)
```
#!/bin/bash

xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Tap Action" 8 0 0 0 0 0 0 0
```

---

