---
title: "SynPS/2 + Kernel upgrade = left/right mouse click dead"
date: 2006-09-16
forum: Hardware &amp; Laptops
---

### Post by figgles on 2006-09-16
Help. I used the update manager to update my laptop. Now, my left mouse button are not working properly. Sometimes it doesn't work; sometimes I have to click many times. Sometimes, I get a "sticky" click, where its as if I have the left button depressed and I'm moving the widget I'm clicking. 

I can tap to to a left-click, which is what I'm doing to get by.

Help! 

TIA

1 hour later -- the fix appears to have been doing:

sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by figgles on 2006-09-17
oh -- rats -- I spoke to soon -- the reconfigure didn't fix the problem. The left mouse button on the ps/2 synaptics (just below the touchpad) does not work reliably. It goes from "sticky" (mouse always down) to mouse up. No mouse down (i.e., left-click) events. An attached USB mouse works.

Any ideas?

---

### Post by figgles on 2006-09-18
I'm sure this isn't the most exciting question, but I'd sure love some help with this issue. Not having my touchpad is difficult!

---

### Post by klaxian on 2006-09-19
I'm having a similar problem.  It is the same thing that happened many versions ago and I believe it was fixed with a driver update (perhaps it's just a configuration issue).  I think we are stuck waiting for the devs to post an update.  Here is a related bug:

[https://launchpad.net/distros/ubuntu/+source/xserver-xorg-input-synaptics/+bug/60122](https://launchpad.net/distros/ubuntu/+source/xserver-xorg-input-synaptics/+bug/60122)

---

