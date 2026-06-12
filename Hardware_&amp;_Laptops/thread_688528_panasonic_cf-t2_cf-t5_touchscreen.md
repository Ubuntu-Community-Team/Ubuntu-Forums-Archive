---
title: "panasonic cf-t2 cf-t5 touchscreen"
date: 2008-02-05
forum: Hardware &amp; Laptops
---

### Post by svlachos on 2008-02-05
Here is a working config to have the touchscreen work on a panasonic cf-t2 or cf-t5

Section "InputDevice"
    Identifier "touchscreen"
    Driver "evtouch"
    Option "Device" "/dev/input/event4"
    Option "DeviceName" "touchscreen"
        Option          "MinX"                  "200"
        Option          "MinY"                  "15800"
        Option          "MaxX"                  "15455"
        Option          "MaxY"                  "1500"
Option "ReportingMode" "Raw"
Option "Emulate3Buttons"
Option "Emulate3Timeout" "50"
Option "SendCoreEvents" "On"
Option "SwapX" "0"
Option "Swapy" "1"
#Option "Calibrate" "1"
EndSection

---

### Post by jasonhaley on 2008-02-06
I have a CF-t2 and the touchpad worked out of the box...it worked even better than it does with Windows XP

---

