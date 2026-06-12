---
title: "Mouse scroll wheel / extra buttons not working"
date: 2006-04-09
forum: Hardware &amp; Laptops
---

### Post by olsonar on 2006-04-09
I have a logitech mx310 mouse, and i want to be able to use the extra buttns and scroll wheel. When i first started using it the wheel worked fine, but the extra vuttons did not. so i looked around the forums a bit and tried some stuff and now the scroll wheel does what i was trying to make the side buttons do. the side buttons do nothing. Here's it's entry in xorg.conf:

```

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ExplorerPS/2"
    Option        "Buttons"        "7"
    Option        "ZAxisMapping"        "6 7"
    Option        "Resolution"        "800"
EndSection

```

Any ideas? At the least I would like the scroll wheel back, but I can't remember the origional entry.

---

### Post by nanotube on 2006-04-10
your zaxismapping is supposed to be "4 5". 
check the link in my sig, and go to the "five button mouse" section, to see how i have configured it (everything works for me).

---

### Post by olsonar on 2006-04-12
Thanks. Now it works perfectly, although I had to install imwheel to get the side buttons working.

---

