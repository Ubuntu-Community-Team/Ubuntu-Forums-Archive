---
title: "Ubuntu 17.10 + Logitech Marble Mouse"
date: 2017-11-12
forum: Hardware
---

### Post by Albertus on 2017-11-12
I have a Lenovo ThinkPad T500 and a Logitech Marble Mouse.

The laptop has a trackpad with two buttons and a trackpoint with three buttons.

The Marble Mouse has four buttons (two big ones and two small ones) and a ball, obviously.

I have a pretty specific way in which I want to set this up... The trackpad and trackpoint buttons I would like to keep default (left as primary click, right as secondary click, and middle (of the trackpoint) as middle click and scroll button). But on the Marble Mouse I would like to switch the left and right buttons, set the left small button as middle-click and scroll activator (instead of default action: Back) and the right small button as a back button (instead of default action: Forward).

The problem is that xinput doesn't individually list the devices - it only lists an "xwayland-pointer:14" and an "xwayland-relative-pointer:14".

If I use xinput to swap buttons around on the xwayland-pointer:14, that does have the desired effect on the Marble Mouse - but it also swaps the left and right button of the trackpad and trackpoint... (buttonmap 3 2 1 4 5 6 7 2 8 10)

And I have yet to find a way to set up scrolling on the Marble Mouse. [http://www.russet.org.uk/blog/3181?kblog-transclude=2](http://www.russet.org.uk/blog/3181?kblog-transclude=2) does give me a pointer, but this doesn't work because xinput doesn't identify the Marble Mouse as such, only gives me the xwayland pointer devices.

Help? :D

---

### Post by Albertus on 2017-11-19
Nobody? :(

I find it rather disappointing that something relatively simple as customizing mouse buttons isn't possible in Ubuntu 17.10 out of the box. I'm probably going to have to ditch Wayland and return to X.org in order to be able to use my mouse /somewhat/ like what I would like to have, but even previously under X.org it didn't allow me to set it up exactly like I want it...

---

