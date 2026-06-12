---
title: "How to turn off horizontal scrolling with syntouch?"
date: 2009-10-30
forum: Hardware
---

### Post by jonboy99 on 2009-10-30
Hi folks, am using a slightly older dell laptop - inspiron 640m with syntouch touchpad, and on ibex due to flash player performance with later ubuntu versions.

I hate horizontal scrolling, and can turn it off with the command

 synclient HorizEdgeScroll=0

But on reboot it is activated again.  My xorg.conf sections looks like below, but does not seem to do anything.  What am I doing wrong?

Thanks
Jon

xorg.conf section:

Section "InputDevice"
Identifier "Synaptics touchpad"
Driver "synaptics"
Option "SHMConfig" "true"
Option " HorizEdgeScroll" "0"
EndSection

---

