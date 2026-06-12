---
title: "Bluetooth Mouse Scrollwheel problem"
date: 2007-09-15
forum: Hardware &amp; Laptops
---

### Post by novusopiate on 2007-09-15
Hello all!

This seems to be a recurring issue in Ubuntu but I have not yet found a resolution that works for me. I am using a Bluetooth optical mouse and it works well. I can use all of the buttons (including the wheel, but only for pasting and such in terminal etc)  but I cannot use it to scroll in web pages and documents.
Here is my xorg info:
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5 6 7"
    Option         "Emulate3Buttons" "true"
    Option         "Buttons" "3"
EndSection


I have been browsing fairly constantly looking for something that will resolve this but have had no luck yet. Any help would be appreciated...


Mike

btw, Im using Feisty....

---

### Post by rivalarrival on 2007-09-15
I would first try changing the line:
```

Option "ZAxisMapping" "4 5 6 7"

```
to read:
```

Option "ZAxisMapping" "4 5"

```

And maybe changing
```

Options "Buttons" "3"

```
to 
```

Options "Buttons" "5"

```

---

### Post by novusopiate on 2007-09-15
No luck....... but thanks.

 any other ideas?

---

### Post by novusopiate on 2007-09-15
bumpiness?

---

### Post by novusopiate on 2007-09-15
bump once more? any body......it's a fairly annoying thing...:confused:

---

