---
title: "Logitec MX518 Button Capabilities?"
date: 2007-11-08
forum: Hardware &amp; Laptops
---

### Post by SkippyIsForYou on 2007-11-08
Is there a simple walkthrough that has the MX518 mouse installing guide for it?

THANKS! 
~Skippy

---

### Post by spoilerhead on 2007-11-08
```
Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "evdev"
        Option      "SendCoreEvents" "true"
        Option      "Name" "Logitech USB-PS/2 Optical Mouse"
        Option      "Emulate3Buttons" "true"
        Option      "ZAxisMapping" "4 5 6 7"
        Option      "Buttons"   "12"
        Option      "Resolution"    "400"
        Option "AllowMouseOpenFail" "true"

EndSection

```

be sure to remove the CorePointer option from all input devices

works for me here with the same mouse, tested on edgy, feisty and gutsy
you need the xserver-xorg-input-evdev package installed

---

### Post by madestro on 2007-11-18
Awesome !!! Thanxs a lot **spoilerhead** you saved my surfing life !!! Now do you happen to know how I can use the back and forward buttons in Nautilus ??
Again thanxs a lot keep up the good work !!!!! =D>

---

### Post by i0h on 2007-12-20
Thanks alot spoilerhead,   tried 3-4 other "howtos"  and they just f***ed up my system.. and easy cut and paste and it all works.. you tha maen

---

### Post by ShadowBlade on 2007-12-31
Awesome, it works!

---

### Post by harold4 on 2008-01-09
About to pull my hair out...  I config similiar to this worked in Dapper, but is failing to work in Gusty.

---

### Post by dg88 on 2008-03-29
whoa! ive been tring a few variations too. seems like i should have tried one more :)

thanks alot!

---

