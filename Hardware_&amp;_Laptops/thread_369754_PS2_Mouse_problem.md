---
title: "PS2 Mouse problem"
date: 2007-02-24
forum: Hardware &amp; Laptops
---

### Post by IMageCrafter on 2007-02-24
I was trying to install Ubuntu in my PC but during the LiveCD boot, I noticed that my optical mouse (a ps2 VCOM Optical Mouse) light didn't turn on, even after the GNOME interface ended loading. My mouse didn't work, each time I loaded Ubuntu through the LiveCD.
The Ubuntu version to install is 6.06 LTS and my motherboard is Asus A7V8X-X.
It seems all mouse modules are well loaded and I even tried to reconfigure Xorg with no success. This mouse works fine under Windows in this same PC and there is a friend of mine who has a similar ps2 optical mouse working ok with the same model of motherboard and Ubuntu.
Any ideias on what the problem may be?
I thank every help.

---

### Post by Stemp on 2007-02-25
Could you please post the mouse section of you /etc/X11/xorg.conf file ?

---

### Post by IMageCrafter on 2007-02-25
Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
End Section

---

### Post by IMageCrafter on 2007-02-25
Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
End Section

sorry... this one it the right one

---

### Post by Stemp on 2007-02-25
Maybe be you should try to add the protocol :
```
Option          "Protocol"              "ExplorerPS/2"
```
or
```
Option          "Protocol"              "auto"
```

If it's not working try to change the device to :
```
/dev/input/mouse0
```
or
```
/dev/psaux
```

---

