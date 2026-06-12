---
title: "Up arrow taking screenshot"
date: 2008-08-19
forum: Hardware
---

### Post by RicJD on 2008-08-19
Hi Guys

Recently my keyboard has started acting straingly.  When i press the up arrow it takes a screen shot.  Also the down key don't seem to work.  Some of the media keys which used to work aren't working any more.  Below is the set up of my /etc/X11/xorg.conf:

```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "gb"
EndSection

```

The keyboard i'm using is a logitech s510.

If anyone has any ideas or help it would be greatly appreciated.

Thanks

Rick

---

### Post by b-llwyd on 2008-10-07
Same here... using a microsoft wireless keyboard/mouse combo. Intrepid beta. Will investigate. You didn't find  solution, did you?

---

### Post by Shane N on 2008-11-11
I'm having the same issue. Did either of you resolve this?

I use Synergy with the server on a windows machine that has a Microsoft Wireless Comfort Keyboard and Microsoft Wireless Laser Mouse 6000.

---

