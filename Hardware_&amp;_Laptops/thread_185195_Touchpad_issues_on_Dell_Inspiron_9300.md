---
title: "Touchpad issues on Dell Inspiron 9300"
date: 2006-05-31
forum: Hardware &amp; Laptops
---

### Post by tbraun on 2006-05-31
Hello!

I have a Dell Inspiron 9300 laptop (Nvidia graphics), on which I recently did a fresh install of Dapper. USB mouse works fine, and the touchpad is also recognized. However, there are a few issues with that touchpad:

1. Its sensitivity is too low. What I mean is: I like the mouse speed, but would like to increase the speed/sensitivity of the touchpad, separately. Yet, I don't seem to be able to find controls specifically for the touchpad. Is there some config file I could tweak?

2. The sideways scroll section on the touchpad does not seem to be recognized. The up-down section works, no problem. However, moving left and right on the sideways section only moves the mouse, but does not perform a sideways scroll of a window.

If anyone could let me know how to address one or both of these issues, that would be greatly appreciated.

Thank you very much!

Tom

---

### Post by David Corrales on 2006-06-01
Same problems here. The touchpad is sloooow and the GUI in synaptics won't allow the adjustment of speed. Is there a way to do this the proper way without horrible configuration file hacks?

---

### Post by emda on 2006-06-06
```
Section "InputDevice"
    Identifier     "Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "ShmConfig" "true"
    Option         "HorizScrollDelta" "0"
    Option         "LeftEdge" "130"
    Option         "RightEdge" "840"
    Option         "TopEdge" "130"
    Option         "BottomEdge" "640"
    Option         "FingerLow" "7"
    Option         "FingerHigh" "8"
    Option     "MinTapTime" "50"
    Option         "MaxTapTime" "180"
    Option         "MaxTapMove" "220"
    Option         "VertScrollDelta" "20"
    Option         "MinSpeed" "0.60"
    Option         "MaxSpeed" "1.10"
    Option         "AccelFactor" "0.03"
EndSection

```

You might have to tweak one of these.. I'd like to make my taping less sensitive so that i dont send mouse clicks when im typing or start moving the mouse but I dont feel like restarting X 50 times (i'm not sure which to change).

---

### Post by sugonaut on 2006-06-06
This can be found in the /etc/X11/xorg.conf file.  When you are ready to make changes to it, just go to your terminal and type ```
sudo gedit /etc/X11/xorg.conf
```.  Edit, save, and close.  You will likely have to reboot before the changes take effect.

---

### Post by sugonaut on 2006-06-06
Also look here: [https://wiki.ubuntu.com/SynapticsTouchpadHowTo](https://wiki.ubuntu.com/SynapticsTouchpadHowTo)

---

