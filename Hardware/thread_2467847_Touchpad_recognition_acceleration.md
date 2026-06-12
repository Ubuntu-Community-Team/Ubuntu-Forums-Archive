---
title: "Touchpad recognition/ acceleration"
date: 2021-10-09
forum: Hardware
---

### Post by thomasg62 on 2021-10-09
Hi - firstly apologies if this is in the wrong place. It seems 'hardware' to me because it is about my touchpad, but I appreciate that it might actually be software. I can shift it if thats what you think.

I am keen to install Ubuntu on my HP Elite X2 1012 G2, and have done so many time successfully on other laptops/ Pc's. However, when I do I cannot seem to get it to recognise my touchpad (this model has a detachable keyboard, if that's relevant). I get the setting for mouse, but not touchpad. Problem is that the touchpad works but is painfully slow to move the cursor across the screen. Adjusting the mouse settings does nothing to the touchpad speed. I need to accelerate it somehow, and have tried searching this but with no real success. I wouldn't have come on to ask this if I was really experienced and it was easy to find, so sorry if it is obvious to others. 
I have tried other Distros to see if this was a characteristic of main Ubuntu, but POP_OS, Zorin etc., all derivatives of course, were the same. Then I tried Elementary OS and the touchpad setting were there and worked great. I might have settled for that but it is as buggy as hell. Odin I think it is called. So many broken dependencies I cannot fix etc. 

Given that Elementary OS is again a derivative of Ubuntu it seemed plausible that I should be able to get proper Ubuntu to work. The touchpad is a deal-breaker for me. Can anyone assist?

---

### Post by axelmasok on 2021-10-13
This won't be too hard.

[B]sudo dmesg |grep -i input

sudo dmesg |grep -i touch[/B]

Many laptops will result in :

**input: PS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6**

Luckily you have found a distro that works so you'd be running these command there and furthering your knowledge on the touchpad type and required driver for your HP (from HP site and web search).  I have read recently that some touch pads are improving over the older style (better resolution?) and therefore I'm not surprised they will require some mucking around to get working.

---

