---
title: "nVidia 8600GS drivers not installing correctly"
date: 2008-08-29
forum: General Help
---

### Post by asenine on 2008-08-29
Hey guys,

I installed xubuntu today to replace my old OS, as it has stopped working and I am getting massively frustrated with window$. I have been fruitlessly trying to get drivers for my 8600GS, but they seem to not install correctly.

I did sudo apt-get nvidia-glx, and it appeared to install, but there is no line in /etc/X11/xorg.conf referring to the driver, or any driver for that matter.

Here is what my config looks like before and after I try and put nvidia in:

Before:

```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "gb"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection
```

After:

```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "gb"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "nvidia"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection
```

It boots fine before, but after, I get this: [http://img365.imageshack.us/img365/6001/dsc00127af1.jpg]("http://img365.imageshack.us/img365/6001/dsc00127af1.jpg")

It appears in synaptics as selected, but the dev package is not. Any ideas?

---

### Post by Ms_Angel_D on 2008-08-29
Try installing your driver using EnvyNG [http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

---

### Post by asenine on 2008-08-29
> **MetalHellsAngel said:**
> Try installing your driver using EnvyNG [http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")
No cigar, doesn't detect my card.

Also, I should mention, I did do a direct download and ran it with X terminated, but it couldn't find my libc headers (I have v2.7).

---

### Post by Ms_Angel_D on 2008-08-29
Take a look at their F.A.Q. I noticed it says something about if your using Xubuntu

[http://albertomilone.com/envyngfaq.html#A]("http://albertomilone.com/envyngfaq.html#A")

P.S. You may to un-enable the driver you previously enabled.

---

### Post by asenine on 2008-08-29
Thanks a lot for trying to help. Turns out all I needed to get the apt-get installer going was build-essential. :)

---

