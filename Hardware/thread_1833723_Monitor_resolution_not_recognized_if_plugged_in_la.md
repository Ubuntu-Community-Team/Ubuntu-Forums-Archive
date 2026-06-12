---
title: "Monitor resolution not recognized if plugged in later"
date: 2011-08-26
forum: Hardware
---

### Post by aldaris88 on 2011-08-26
Hi,

I suffer from the following problem for a while now:
if I plug in my monitor (Samsung 2343NW) after I'm logged in Ubuntu thinks that the max resolution is 1600x900 (this is the max I can set in the GUI app), but in reality it is 2048x1152. If the monitor is plugged in from the very beginning everything works as expected.
I've tried to use xrandr to add a new 2048x1152_60.00 mode, but when I tried to use that mode I get the following error:
xrandr: screen cannot be larger than 1600x1600 (desired size 2048x1152). Where did the second 1600 come from if it only has 1152 pixels in a column?
Any tip how to solve this? Right now I hit Ctrl + Alt + Backspace to restart the X server, to use my monitor on its native resolution, which is not really userfriendly.

Any help appreciated.

Thanks,
Peter

---

