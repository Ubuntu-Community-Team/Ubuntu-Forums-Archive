---
title: "Ubuntu 9.10 (64bit) &#8211; Laptop external monitor &#8211; mouse problem"
date: 2009-11-10
forum: Hardware
---

### Post by damienbfn on 2009-11-10
All works fine until I move the mouse cursor on the monitor to either the bottom of the screen or to the right of the screen. It then disappears from the monitor and re-appears onto my laptop screen. There is no way I can then get control back onto the monitor screen.

This happens whether or not I use the laptop touchpad mouse or the Wireless USB mouse and whether or not the USB adaptor is connected. My laptop has nvidia graphics and the drivers are installed. Tried it with two different monitors. When I dual boot my laptop onto Windows XP and connect to the external monitor the mouse works perfect. I am hoping that one of you 'boffins' please can help!

My /etc/X11/xorg.conf file contains the following entry at the mouse part..

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection****

---

