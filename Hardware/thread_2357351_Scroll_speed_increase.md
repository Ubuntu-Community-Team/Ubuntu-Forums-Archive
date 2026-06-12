---
title: "Scroll speed increase"
date: 2017-04-01
forum: Hardware
---

### Post by cyril-auburtin on 2017-04-01
This is crazily complex to increase the default scroll speed (too slow)

In xinput '[COLOR=#111111][FONT=Ubuntu]Evdev Scrolling Distance' can't be set lower than 1:[/FONT][/COLOR]
I tried xinput set-prop 10 275 --type=float  0.5 0.5 0.5

It's possible to use imwheel, but the experience is bad in the console (scroll disabled, it scrolls on the last commands instead), and buggy

There are methods with libinput and MOUSE_WHEEL_CLICK_ANGLE, but it disabled touchpad tap and other things, without making scroll faster


refs: 

[http://askubuntu.com/questions/285689/increase-mouse-wheel-scroll-speed](http://askubuntu.com/questions/285689/increase-mouse-wheel-scroll-speed)
[http://unix.stackexchange.com/questions/307663/change-scroll-speed-with-libinput](http://unix.stackexchange.com/questions/307663/change-scroll-speed-with-libinput)

---

