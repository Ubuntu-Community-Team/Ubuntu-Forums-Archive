---
title: "graphicalinterface install problem?"
date: 2006-09-18
forum: Hardware &amp; Laptops
---

### Post by mstrat on 2006-09-18
During the initial boot from the CD, I cannot get Ubuntu to load. I get the message:

Failed to start the X Server (your graphical interface) It is likely that it is not set up correctly. Would you like to view the X-Server to diagnose the problem?

Then I can do nothing but shut down. I put Ubuntu on another laptop computer without any problems, and am using it 100% on that computer (It fits my uses perfectly), so I think it is something other than my error. I am attempting to install it on a Toshiba Satellite notebook with Intel Centrino Duo Core processor and a 17" widescreen display...is that a problem? 

Any suggestions?

---

### Post by bigken on 2006-09-18
try this boot into safe mode and type sudo dpkg-reconfigure xserver-xorg and select your grapics driver and screen resolution sizes using the space bar ;)

sorry missread your error you could try the alternate cd

---

