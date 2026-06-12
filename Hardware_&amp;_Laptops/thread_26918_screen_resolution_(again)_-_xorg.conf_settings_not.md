---
title: "screen resolution (again) - xorg.conf settings not taking effect"
date: 2005-04-14
forum: Hardware &amp; Laptops
---

### Post by filcro on 2005-04-14
Hi gang

I'm writing about the age-old problem of screen resolution.  I've just jumped ship from suse 9.2 after having video problems, only to have some (although not as bad) with Hoary - at least it loads the nvidia drivers on every boot!

I've installed the nvidia-glx drivers but I don't seem to be able to achieve a screen res. of 1280x1024.  I've tried using the following command:

sudo dpkg-reconfigure xserver-xorg

and then set the screen resolution but it simply ignores my choice of 1280x1024 and gives me a 1024x768 res. instead.

So, I manually altered the xorg.conf file, but now it gives me a screen resolution of 1280x768.  I'm still learning about manually editing the various config files, so I'm by no means an expert.  I've included a copy of the section which deals with the display from my xorg.conf file below - can anyone help at all?

```
Section "Device"
        Identifier      "NVIDIA Corporation NV34 [GeForce FX 5200]"
        Driver          "nvidia"
        BusID           "PCI:2:0:0"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-49
        VertRefresh     43-72
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV34 [GeForce FX 5200]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection
```

I noticed in passing that KDE's display manager is set to 1280x768 (without a 1280x1024 setting) - could this be a KDE issue?

Thanks for taking the time to read this!

Phil

---

### Post by filcro on 2005-04-14
Hi gang

Solved my own problem - I looked up my monitor's specs (AOC LM919) and altered the following settings:

HorizSync       28-49
VertRefresh    43-72

to those listed by the manufacturer and it worked a treat -1280x1024.

HorizSync       24-83
VertRefresh     55-85

---

