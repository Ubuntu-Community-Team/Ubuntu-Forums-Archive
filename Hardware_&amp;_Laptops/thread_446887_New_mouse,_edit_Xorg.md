---
title: "New mouse, edit Xorg?"
date: 2007-05-17
forum: Hardware &amp; Laptops
---

### Post by _simon_ on 2007-05-17
My new mouse should be here by Monday, what do I need to do when it arrives?

For reference I am replacing my Logitech MX700 with a Razor Copperhead.

---

### Post by newlinux on 2007-05-17
You may not need to do anything. Plug it in first and see how it works. Most mice I've used have just "worked" in ubuntu.

---

### Post by _simon_ on 2007-05-17
Will it auto update Xorg?

Currently my mouse section looks like this:

```

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Dev Name" "Logitech USB Receiver"
    Option         "Dev Phys" "0000:00:02.0-1/input0"
    Option         "Device" "/dev/input/mice"
    Option         "Buttons" "10"
    Option         "ZAxisMapping" "4 5"
    Option         "ButtonMapping" "1 2 3 6 7 "
    Option         "Resolution" "800"
EndSection

```

---

