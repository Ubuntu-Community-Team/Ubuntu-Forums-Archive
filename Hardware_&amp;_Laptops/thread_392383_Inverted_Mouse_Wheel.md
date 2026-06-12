---
title: "Inverted Mouse Wheel"
date: 2007-03-24
forum: Hardware &amp; Laptops
---

### Post by ReverendJ1 on 2007-03-24
Hello all. I have one small problem with my mouse. The scroll wheel is inverted. i.e. when I scroll up it goes down, when I scroll down it goes up. This isn't a critical problem, but annoying none the less. Anyone got any ideas of how to fix it?

---

### Post by Wally68 on 2007-03-24
Rev,
Take a look at your /etc/X11/xorg.conf, look for the following:

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection


check the ZAxisMapping line, if it is "4 5" try reversing the order to "5 4"


Tom

---

### Post by ReverendJ1 on 2007-03-24
Hmm. No that didn't seem to work. Any other ideas?

---

### Post by willdeed on 2008-02-25
If you're using KDE try this: KMenu -> System Settings -> Keyboard & Mouse -> Reverse scroll direction

---

