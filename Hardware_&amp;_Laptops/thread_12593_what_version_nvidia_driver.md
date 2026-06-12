---
title: "what version nvidia driver"
date: 2005-01-25
forum: Hardware &amp; Laptops
---

### Post by sharkzf6 on 2005-01-25
I just installed this ubuntu thing on an old P3 rig with an nVidia GeForce 2 graphics card. How do I know which nvidia driver version the desktop is using? It looks great on my NEC LCD1765. I'm not sure if X is using the nv driver or the nvidia one. I'm a Linux newb.

BTW - I stuck this thing in the CD, booted it, waited for about 20 minutes, and everything came up and is working!!!!

I am totally stunned. It took me over a week to get my Debian Woody system up and it's still not where this is as far as hardware, funtionallity, and just plain beauty. Whoever made this is awesome!!!

---

### Post by martyr on 2005-01-25
You can find out about the currently used driver by looking at /etc/X11/XF86Config-4

You should find something similar to the following:

```
Section "Device"
        Identifier      "00e6"
        Driver          "[COLOR=Red]nvidia[/COLOR]"
        BusID           "PCI:1:0:0"
EndSection
```

At the place which I highlighted, there should be either "nv" or "nvidia". "nvidia" are then closed source nvidia drivers.
If it's "nv", change it to "nvidia" if you have installed the nvidia drivers.

---

