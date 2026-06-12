---
title: "Can't get max widescreen resolution"
date: 2008-11-11
forum: General Help
---

### Post by codeeyez on 2008-11-11
Yo, here's my problem, my max screen resolution should be 1440x900. I've manage to get it to 1360x768, i would be ok with this but of some odd reason it decided to show some of the whole screen and makes it so i have to use my mouse to see the hidden part of the screen. I've tried countless things but the either mess up the xseason or they do nothing at all.

I'm using GeForce 8400 GS Nvidia.

sudo nano /etc/X11/xorg.conf
```
Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
        Disable "dri2"
EndSection

Section "Device"
        Device          "Configured Video Device"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
        Disable "dri2"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Option  "NoLogo"        "True"
        Driver  "nvidia"
EndSection

```

---

### Post by CLomax on 2008-11-11
This might be a silly question but have you tried....

```
Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
   [B][COLOR="Red"]SubSection "Display"
         Modes    "1440 900"
         Virtual   1440 900
   EndSubSection[/COLOR][/B]
EndSection

Section "Module"
        Load    "glx"
        Disable "dri2"
EndSection

Section "Device"
        Device          "Configured Video Device"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
        Disable "dri2"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Option  "NoLogo"        "True"
        Driver  "nvidia"
EndSection
```

?

---

### Post by codeeyez on 2008-11-11
lol, yes that did work. but somehow it changed my theme color. but i'll just live with it.

---

### Post by eternalnewbee on 2008-11-12
Is your graphic card activated? To check, go to **Main Menu > System > Administration > Hardware Drivers**. If it's not activated then you have found the source of your problem. Activate it.

---

### Post by CLomax on 2008-11-12
> **codeeyez said:**
> lol, yes that did work. but somehow it changed my theme color. but i'll just live with it.

You can always change the theme colour again.

---

