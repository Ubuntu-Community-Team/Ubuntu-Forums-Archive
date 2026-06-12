---
title: "Mousepad has mind of its own"
date: 2007-07-31
forum: Hardware &amp; Laptops
---

### Post by thebaron2 on 2007-07-31
Just installed Ubuntu (using Wubi) on an old Dell Latitude and the mouse pointer seems to have a mind of its own.

Sometimes I can move it fine and the pointer reacts appropriately.  Other times I'll stop moving it and the pointer will just start heading towards the top/left or bottom/right of the screen.  Sometimes I have to fight it to get it where I want, and then it will suddenly start responding correctly. :confused::(

This is the mousepad on the laptop - no USB mouse or anything.  It all works fine in Windows so I don't know if it's a driver issue or what.

This is literally the first time I've run Ubuntu after its been installed fully.  I had tried to install from a burned ISO but the computer was too slow and hung at install.  This problem also existed when running the desktop from the burned ISO, though.

Suggestions? Recommendations?

---

### Post by WinterWeaver on 2007-07-31
what type of mouse? Optical? Ball-mouse?

I know Opticals do things like that when on certain surfaces.

try another mouse and see if you have the same results

---

### Post by thebaron2 on 2007-07-31
It's the touch pad on the laptop - no external unit.

I'll try to plug some different types of mice in through USB when I get home to see if the problem persists with them.

---

### Post by WinterWeaver on 2007-07-31
oh... ok.. sorry lol... :P

well... on that note.... I know that some touch pads behave in that manner if they are a wee bit wet etc. :P But that's about all I can think of :)

---

### Post by ugm6hr on 2007-07-31
> **thebaron2 said:**
> Suggestions? Recommendations?

Try installing the synaptics driver - this is very informative:
[http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad)

You need to edit xorg.conf to get it to work.  I think that ALPS Touchpads are particularly prone to erratic behaviour unless configured properly...

---

