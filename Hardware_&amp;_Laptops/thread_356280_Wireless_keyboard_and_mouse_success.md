---
title: "Wireless keyboard and mouse success"
date: 2007-02-08
forum: Hardware &amp; Laptops
---

### Post by peterthewolf on 2007-02-08
Have recently purchased a Keysonic ACK-540 RF mini keyboard, has built in touch pad mouse and usb wireless stick. It worked straight out of the box. Ideal for HPTC remote use.:)

---

### Post by stedevil on 2007-11-11
I also have the Keysonic ACK-540 RF, and while it did work just fine auto magically in Ubuntu 7.04, it doesnt in 7.10. The keys still work, but the touch pad & mouse buttons are dead.

Do you have the same experience or is your keyboard still working fine in 7.10?

---

### Post by stedevil on 2007-11-12
Ok, did some tinkering around and got the touchpad up and working again by adding the following to /etc/X11/xorg.conf
```

#Vendor=05af Product=0408 Version=0110
Section "InputDevice"
#       Identifier      "Touchpad - Keysonic ACK-540RF Wireless Mini Keyboard"
        Identifier      "Touchpad"
        Driver          "evdev"
        Option          "SendCoreEvents" "1"
# cat /proc/bus/input/devices
        Option          "Name" "2.4G USB RF KeyBoard"
        Option          "Phys" "*/input1"
EndSection

```
and in Section "ServerLayout" adding 
```

InputDevice    "Touchpad" "SendCoreEvents"

```

Then I just logged out and restarted the x-server (simplest by alt+ctrl+bksp) and it was up and running.

PS cat /proc/bus/input/devices showed me 3 different entries for 2.4G USB RF KeyBoard, but 2 of them seemed to only be about keyboard things (which was already working) so I didnt bother with adding those.

PPS I am using a stationary mouse as well as keyboard as the CorePointer/CoreKeyboard, if somebody was wondering why Im using Option          "SendCoreEvents" "1" instead of Option "Core...".

---

### Post by peterthewolf on 2007-12-12
I am using 7.10 have just plugged keysonic in and everything just works.

---

