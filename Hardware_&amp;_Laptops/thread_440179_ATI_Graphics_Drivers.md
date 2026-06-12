---
title: "ATI Graphics Drivers"
date: 2007-05-11
forum: Hardware &amp; Laptops
---

### Post by a.ranic on 2007-05-11
I recently installed Fawn on a second HD in my rig and everything works properly but I'm wondering if I should bother with ATI drivers because the machine works fine as is.  I've read that there's very poor support for ATI cards from ATI.  The ATI proprietary drivers don't have my Radeon 7000 listed as being supported.  Long story short, should I just leave as is or wrestle with the drivers?  Thanks for your help.

---

### Post by kelvin spratt on 2007-05-11
If its working and your satisfied i would leave it I use an ATI card with no problems straight from the box after I gave up with my Nvidia

---

### Post by Ken_Lewis81 on 2007-05-11
"As is" will use the free software that ATI helped to write which fully supports your Radeon 7000.  Check that you're using the "radeon" X.org driver: type "cat /etc/X11/xorg.conf | grep radeon" in a terminal window. (In the terminal, "man cat" and "man grep" will tell you what each of these commands do; the '|' is the pipe that puts one command's output to another.)

take care.
Ken.

---

