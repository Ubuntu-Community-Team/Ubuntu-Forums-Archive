---
title: "Ms Wireless Mouse 3500 and Ubuntu"
date: 2013-08-12
forum: Hardware
---

### Post by Hewjr100 on 2013-08-12
Simple question, I think? why is it when I run ubuntu 12.04, 13.04 and 13.10 that only 12.04 has pointer speed control/slide for this mouse in settings->mouse and 13.04, 13.10 don't.  I would think that newer versions of ubuntu would support ms wireless mouse 3500 and perhaps not the older versions, but it seems the opposite is true.  Any particular reason?

Henry

---

### Post by varunendra on 2013-08-12
There are many user controls that have been removed or hidden in 13.04 and later. Extended pointer control is one of them as far as I know.

However, you can try "gpointing-device-settings" which is a gui tool that offers quite an extensive set of controls over pointing devices. To install it -
```
sudo apt-get install gpointing-device-settings
```

You may have to run it from terminal or Alt+F2 shortcut after installation, since it does not add a gui launcher by default in Unity dash.

---

### Post by Hewjr100 on 2013-08-12
Tried it, but have the same issue, only shows touchpad controls nothing for the mouse or pointer.

Henry

---

### Post by varunendra on 2013-08-12
Does the mouse work on the system? Is it even detected?

Wireless mice work on bluetooth signals, and if it doesn't work at all, it is most probably a problem with the bluetooth functionality, not the mouse or related controls.

To see if it is detected -
```
xinput
cat /proc/bus/input/devices
hcitool scan
```

---

### Post by Hewjr100 on 2013-08-12
Under that command I do see the synaptics touchpad but not the mouse, however the mouse does work, just no settings available in system settings.  At least I do not see slider to adjust mouse pointer speed.  Btw no bluetooh on this laptop.

Henry

---

### Post by varunendra on 2013-08-12
Did any of the latter two commands ("cat /proc...." and "hcitool scan") show the mouse or its hardware ID? Please post their outputs if not sure.

Also, any wireless device obviously requires a medium to connect. So far, I have only seen that medium to be bluetooth signals for pointing devices. But I'm not expert in this field and it would be interesting for me to see what medium your mouse is using. :)

---

