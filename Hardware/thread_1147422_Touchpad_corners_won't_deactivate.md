---
title: "Touchpad corners won't deactivate"
date: 2009-05-03
forum: Hardware
---

### Post by theinfiniteadam on 2009-05-03
I have a synaptics touchpad, and whenever I use it,the corners of the touchpad perform actions that I don't want.

Whenever I tap the bottom right part of the touchpad, the menu comes up. When I tap the top right part of my touchpad, it acts as a middle click. I have tried editing some .fdi files to make this stop, but I'm not sure the necessary options to put in an .fdi file to stop this. I would post my xorg.conf, but its commented out by hal. 

Can anyone just post an .fdi file that will stop the corners of my mousepad from performing actions?

---

### Post by theinfiniteadam on 2009-05-05
Bump

---

### Post by xMarine73 on 2009-05-14
Try this...

```

synclient TouchpadOff=0 MaxTapTime=150 ClickFinger1=1 ClickFinger2=2 ClickFinger3=3 **RTCornerButton**=0 **RBCornerButton**=0;

```

It's been a while since I've read what each of those do but google it and you should be golden.  I believe a value of zero for the corner buttons is in fact what you want.

Hope it helps!

---

