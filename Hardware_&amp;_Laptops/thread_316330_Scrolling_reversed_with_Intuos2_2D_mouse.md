---
title: "Scrolling reversed with Intuos2 2D mouse"
date: 2006-12-10
forum: Hardware &amp; Laptops
---

### Post by rquint on 2006-12-10
I can't find the correct way to change the behaviour of my 2D mouse with an Intuos2 tablet.  I'm running Edgy with the three wacom packages installed through synaptic.  The mouse works fine except for the scroll wheel which sends a scroll up when I scroll down and a scroll down when I scroll down.  I tried adding the lines

Option  "Button4" "5"
Option  "Button5" "4" 

to the cursor section in xorg.conf, but they have no effect.  If I add 

Option  "Button2" "4"

or

Option  "Button2" "5"

I do get scrolling in the correct direction by repeatedly pressing the scroll wheel (which is Button2).  Experimenting I can change the behaviours of Buttons 1, 2 and 3, but no other Buttons are recognized.  Other changes like using absolute or relative mode are recognized.

When I boot into Windows XP, the scrolling with the mouse works as expected.  Scrolling with a USB mouse attached to the system also works correctly.

Any suggestions?  Has anyone successfully removed the ubuntu packages and installed the linuxwacom project's drivers.  When I marked the packages for removal, Synaptic also marked several other packages involving xorg for removal and I wasn't sure if this was safe to do without borking my X server.

---

### Post by nigeltao on 2006-12-26
I filed a bug.
[https://launchpad.net/distros/ubuntu/+source/wacom-tools/+bug/77226](https://launchpad.net/distros/ubuntu/+source/wacom-tools/+bug/77226)

---

