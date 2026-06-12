---
title: "weird behavior of the mouse after updating to 9.04"
date: 2009-05-01
forum: Hardware
---

### Post by Yoqtan on 2009-05-01
Hello,

I just updated ubuntu to 9.04, and my mouse has caught a bug in the process. It seems to stuck on some toolbars.

Two examples : 
I have a shortcut to firefox in my top bar. if I click on it, firefox opens, but I won't be able to click on anything in the new window. I won't be able to change windows. In fact, the only thing i can do is click on the shortcut again and open a new firefox window. If I right click on anything, on my desktop, it will open the contextual menu of the shortcut, and then free my mouse. I can the use it normally.

Into firefox, If I want to change tabs, I have to right click anywhere on my desktop, this will open the contextual menu of my page, and then click on the tab I want. Then, I have to right click on the tab bar before I can click on anything on the web page.

I tried to stop compiz, I still have the same problem.
My xorg.conf is almost empty : 

```
Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

```Thank you for your help !

---

