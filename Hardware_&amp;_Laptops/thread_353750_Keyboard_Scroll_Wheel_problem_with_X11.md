---
title: "Keyboard Scroll Wheel problem with X11"
date: 2007-02-05
forum: Hardware &amp; Laptops
---

### Post by Magicdead on 2007-02-05
I'm using a Trust DS-4500X Wireless Laser Deskset keyboard on my ubuntu dapper and the scroll wheel on the keyboard isn't working.

It doesn't give any event when using xev, either.

here's my current xorg.conf:

```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "logicink" #"pc105"
        Option          "XkbLayout"     "de_ch"
EndSection

```

the logicink was my last attemp to solve the problem, it didn't work with pc105 either. (I googled a little and somewhere, with another keyboard, the logicink model worked... )

I see the light blinking on the wireless receiver when I use the mouse wheel, so the keyboard is sending an event, but it's not registered by xev or the os.

all the other multimedia keys work flawless, only other thing that doesn't work is the battery gauge, but that would be another problem to solve, first of i'd like to have the scroll wheel working.

best regards,

Magicdead

[Edit] 
The keyboard is connected to the PS/2 slot on my mainboard, using the USB <-> PS/2 Adapter that came with the keyboard

---

