---
title: "a few mouse configs needed please"
date: 2007-05-07
forum: Hardware &amp; Laptops
---

### Post by Bashed on 2007-05-07
I have Microsoft Wireless Laser Mouse 6000 and I enabled the 5 button settings with the below:

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice" 
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
    Option         "Buttons" "7" 
    Option         "ButtonMapping" "1 2 3 6 7"
EndSection


I'm hoping someone can help me to get the horizontal scroll to work.  Also, I would like the back button to work when browsing the file system (under places > computer for example). That would be great.

Thanks

---

### Post by Bashed on 2007-05-08
I hope someone can please help me out

---

