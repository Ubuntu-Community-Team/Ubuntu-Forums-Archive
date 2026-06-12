---
title: "S-Video Problems"
date: 2009-07-28
forum: Hardware
---

### Post by JoeShmo397 on 2009-07-28
Im running the latest edition of Xubuntu on my Dell Inspiron Laptop.  After installing Sysinfo I determined that my graphics card is Intel 945GM.  I want to use my S-video out, but have been unable to.  After googling the problem the only solutions I can find revolve around editing xorg.conf file, but mine really doesnt have anything....

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection


I'm still a general newb here, but I was really hoping to be able to use my S-video out like I could on...dare i say it...windows

any help is appreciated, thanks in advance

---

