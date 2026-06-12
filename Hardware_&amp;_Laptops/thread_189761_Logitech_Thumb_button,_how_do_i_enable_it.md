---
title: "Logitech Thumb button, how do i enable it?"
date: 2006-06-05
forum: Hardware &amp; Laptops
---

### Post by djvishnu on 2006-06-05
I have a "Logitech Cordless Mouse Man Optical" mouse, (logitech cordless desktop pro) but i cant get the thumb button to work. Button 1 through 5 works fine (4-5 is mouse wheel). I have read som post i found googling, but nothing helped me out.

This is probably a question many other have asked, so i hope there is someone that can help me reading this.

Thank you! :)

---

### Post by djvishnu on 2006-06-08
I actually figured it out myself :)

xorg.conf
```
Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ExplorerPS/2"
        Option      "Buttons" "8"
        Option      "ZAxisMapping" "4 5"
EndSection

```

---

