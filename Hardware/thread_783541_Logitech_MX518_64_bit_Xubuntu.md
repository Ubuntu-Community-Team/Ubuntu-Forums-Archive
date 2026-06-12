---
title: "Logitech MX518 64 bit Xubuntu"
date: 2008-05-05
forum: Hardware
---

### Post by dokdoom on 2008-05-05
First I will start off by saying I did my research and checked around on multiple forums. I know there is some heavy documentation out there for Logitech mouses but I am still unable to get my side buttons to work.

When using firefox my side buttons will now move forward and backwards which is nice. But now lets say I have something copied and want to double click (Clicking both Left and Right mouse buttons.) to paste into anything. Before reinstalling with hardy I never ran into any problems.

Basically all I would like to do is be able to have my side buttons functional (outside of firefox) and to be able to click both mouse buttons to paste. I use xterm and refuse to use anything else this is why I can't simply right click and paste. 

Here is the mouse section of my xorg

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection

I thought about running: dpkg-reconfigure -phigh xserver-xorg, hoping this would fix things as I think the 3 mouse button emulation is what I am missing. Before I do this I figured I would ask to see if anyone was having a similar issue.

Thanks in advance for any help you can provide.

---

### Post by dokdoom on 2008-05-07
Does anyone know what I am talking about when I said you can click the Left and Right mouse buttons together to paste? I had a friend test and he was unable to achieve this as well. I could just use the scroll button to get this working but that still doesn't change the fact that my side buttons are only working in firefox. Since my first post I have tried numerous ways of getting this to work, but none have worked and some even prevented X from starting properly. I will keep looking but someone else out there has to know what I am talking about.

---

