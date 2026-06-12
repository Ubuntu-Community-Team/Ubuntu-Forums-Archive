---
title: "Razer mouse settings."
date: 2013-01-14
forum: Hardware
---

### Post by Zirts on 2013-01-14
Hi,

So I have a problem with my Razer Diamondback 3g mouse. I was trying to remap it today to get the additional buttons on it working but now I am at the point where my mouse wheel will not work also...

Can anyone lend me a hand on solving this problem? I would still also like to get the 4 additional buttons to work too, like if i press them they type the numbers 4, 5, 6, 7.

Here is my xorg.conf for the mouse currently.
```

Section "InputDevice"
       Identifier "Configured Mouse"
       Driver "mouse"
       Option "Name" "Razer Diamondback Optical Mouse"
       Option "Device" "/dev/input/mice"
       Option "CorePointer"
       Option "Resolution" "1600"
       Option "Buttons" "9"
       Option "Protocol" "ExplorerPS/2"
       Option "ZAxisMapping" "4 5"
       Option "ButtonMapping" "1 2 3 6 7 8 9"
       Option "one page back" "4"
       Option "one page forward" "5"
EndSection


```

Please let me know if any additional info is needed :)

---

