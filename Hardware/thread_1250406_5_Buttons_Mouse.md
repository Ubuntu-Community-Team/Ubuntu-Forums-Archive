---
title: "5 Buttons Mouse"
date: 2009-08-26
forum: Hardware
---

### Post by gtrue on 2009-08-26
Hi there,

I have just installed Ubuntu in my Dekstop and everything is going great, but the scroll function of my mouse. It's a standard 5 Buttons HP optical mouse. 
When I use the wheel to scroll down it works (line-by-line), but when I use the scroll up the screen goes down completely to the bottom. 

Here is my /etc/X11/xorg.conf
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

Ideas??

Thanks,
gtrue

---

