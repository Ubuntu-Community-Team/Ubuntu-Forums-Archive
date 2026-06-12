---
title: "External screen detected but not working on DisplayPort connection"
date: 2013-05-28
forum: Hardware
---

### Post by rdk on 2013-05-28
I'm running up to date Raring on my Thinkpad X220 and stumbled upon weird problem.

I can connect to an external 24 inch DELL U2312HM external screen using DisplayPort cable.

I tried the same connection at work, with similar, but larger screen - 27 inch DELL U2713HM using the same cable. 

When I check >>Settings >> Displays the display is detected. However I'm looking at dark screen.. Bizarrely - when I hit the PrtScr - I can also see it correctly with Ubuntu walpaper o_O

The monitor is detected and works correctly when using [DisplayPort to DVI-D Adapter Cable (Single Link)] however the resolution on this setup is limited to 1920 x 1200 so I'd really like to take advantage of DVI since the laptop should support it.

How could I fix this issue?

---

### Post by produnis on 2013-05-28
Have you tried it with "disper"?
 (it is in the repositories)
After you installed dipser, open a terminal and type in:

disper -e
(this will expand your Display, so both Laptop as well as Monitor should be used)

To clone the Laptops display to the Monitor, type in:
disper -c

To switch back to your Laptops display only, type in:
disper -s

A list of all recognized Displays gives you the following command:
disper -l


Hope that helps, I solved many Display-Problems with disper....

---

### Post by rdk on 2013-05-28
Thanks for the pointer  produnis.

I gave it a shot. Unfortunately to no avail.

Switching to external just blanks my laptop screen and doesn't wake up the monitor.

---

### Post by rdk on 2013-05-29
bump

---

