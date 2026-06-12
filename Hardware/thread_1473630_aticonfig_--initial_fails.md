---
title: "aticonfig --initial fails"
date: 2010-05-05
forum: Hardware
---

### Post by privateabstract on 2010-05-05
I'm running Ubuntu Lucid Lynx 32-bit with an ATI HD 4870 (512mb version) and for some reason I cannot get the command **aticonfig --initial** to work. I've had it working before but now I get the following error:
```

$ aticonfig --initial
Found fglrx primary device section
 Unable to find any supported Screen sections

```I have absolutely no clue how I got it running last time. Here is my /etc/X11/xorg.conf file:
```

Section "Files"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "ServerFlags"
    Option        "Xinerama" "off"
EndSection

Section "Device"
    Identifier  "Default Device"
    Driver      "fglrx"
EndSection

Section "Screen"
    Identifier "Default Screen"
    DefaultDepth     24
EndSection

```Thanks in advance for any assistance you can provide. :)

Edit: Damn damn damn. Sorry! *slaps self for not using the search function.*

```

$ sudo aticonfig --initial -f

```seems to work fine.

---

