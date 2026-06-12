---
title: "Auto disable synaptic trackpad"
date: 2008-08-09
forum: Hardware
---

### Post by m9365428 on 2008-08-09
I love to use my track pad on the go and my usb mouse at my desk but I can't figure out how to have the system auto disable the trackpad when I plug in my usb mouse. I think it is a synaptic track pad. I am running 8.04 in a Toshiba Satellite P200. Any help would be greatly appreciated.

M

---

### Post by linux_tech on 2008-08-21
This won't auto disable the touchpad upon plugging in the usb mouse but it should allow you to disable and re-enable the touchpad.

Verify that in the /etc/X11/xorg.conf file, (cat /etc/X11/xorg.conf) you have something like this:

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "Device"                "/dev/psaux"
        Option          "SHMConfig"             "on"
EndSection

If you can see the last line- “SHMConfig” “on” — this is the one that you really need to have. This allows you to change some configuration parameters for the synaptics touchpad without having to restart Xserver.


From terminal
To disable the synaptics touchpad-
```
 synclient TouchpadOff=1 
``` 

To turn it back on-
```
 synclient TouchpadOff=0  
```

---

