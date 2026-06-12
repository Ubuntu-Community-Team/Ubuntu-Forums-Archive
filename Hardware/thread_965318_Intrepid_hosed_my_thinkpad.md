---
title: "Intrepid hosed my thinkpad"
date: 2008-10-31
forum: Hardware
---

### Post by velozoom on 2008-10-31
Have a Thinkpad T500, just a couple weeks old.  I had installed Hardy 64b with little problem.  Video worked smashingly.  Had great resolution even during the OS install!  THe only real issue was that 8.04 refused to see my WiFi card.  I decided to wait for 8.10 to see if that improved anything.  

I upgraded through Synaptic and never got X to run again.  I kept getting a "No Screens Found" error.  I tried the fglrx driver, updating xserver files, playing with xorg.conf, nothing.  Not even the vesa driver would get x to run.

I gave up and re-installed 8.04, on which the video is working swimmmingly.  Still have the wireless issue but that's for another thread.  The vidcard is an ATI Mobility Radeon HD 3650.  

Any thoughts on the 8.10 issue and why this would work with generic drivers in an old version of Ubuntu but not the latest?

---

### Post by bswilson on 2008-10-31
This is a known issue, I'm afraid.  Take a look at [this part of the 8.10 Release Notes]("http://www.ubuntu.com/getubuntu/releasenotes/810#ATI%20%22fglrx%22%20video%20support").  The bug notes make it look like there's a workaround, so you may be able to try upgrading again.

---

### Post by velozoom on 2008-10-31
Thanks for the link.  Hadn't seen that.  I'll see what I can use.

---

