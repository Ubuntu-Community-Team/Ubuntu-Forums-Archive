---
title: "External USB keyboard - how to disable it behaving like a keyboard?"
date: 2007-10-03
forum: Hardware &amp; Laptops
---

### Post by mr.proxxxy on 2007-10-03
This is a strange topic, I know.

Here is the rundown:

I have a laptop (Acer Aspire 4470z).
I have a project that I am working on where I would like to have access to both an external human interface device as well as the laptop keyboard.
I bought a cheap usb keyboard.
I found the device in the filesystem, but (as expected), the kernel recognized the device and decided "hey, this should function like the primary keyboard, just like the external mouse does!"
I don't want it to do this.

Ideal solution:

Configure X to ignore the external keyboard, but still allow it to behave as a device.
There is probably something in Xorg.conf to do this, but the only section I see in my xorg conf is:

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection


Any thoughts?

---

