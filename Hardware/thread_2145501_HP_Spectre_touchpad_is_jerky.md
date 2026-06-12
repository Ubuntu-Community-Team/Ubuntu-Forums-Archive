---
title: "HP Spectre touchpad is jerky"
date: 2013-05-15
forum: Hardware
---

### Post by dargaud on 2013-05-15
Hello all,
just install Kubuntu on a new HP Spectre Ultrabook. Win8 never even had a chance and screamed while being aborted. The only issue I've had was to disable UEFI (press ESC while booting, then disable Intel rapid start and enable Legacy support in the boot options). All hardware seems to be operational out of the box with 13.04.

The only issue I've noticed is the touchpad which is VERY jerky vertically. Trying to clik moves the cursor by one or two lines. Trying to double clik easily crosses 1/4 of the screen. I've tried playing with the settings of the SynPS/2 Synaptics touchpad manager without success so far (min speed ? Max speed ?)

I just noticed something. If i leave a finger on the touchpad, the pointer jerks around vertically. If i use another finger to touch ANY part of the base of the laptop: it stops !?!

Any advice on that ?
Thanks.

---

### Post by andreyvo2 on 2013-10-08
Had similar problem with jerky touchpad on Hp Spectre XT 15-4000ea.

Played around with synclient command:
```
synclient FingerHigh=40
synclient FingerLow=35

```
and then put these values in so settings saved permanently /etc/X11/xorg.conf 

[HTML]Section "InputClass"
    Identifier "touchpad"
    Driver "synaptics"
    MatchIsTouchpad "on"
    Option "FingerHigh" "40"
    Option "FingerLow" "35"
EndSection
[/HTML]
[http://askubuntu.com/questions/127829/synaptics-touchpad-cursor-moves-around-when-just-tapped-after-ubuntu-12-04-](http://askubuntu.com/questions/127829/synaptics-touchpad-cursor-moves-around-when-just-tapped-after-ubuntu-12-04-)

---

