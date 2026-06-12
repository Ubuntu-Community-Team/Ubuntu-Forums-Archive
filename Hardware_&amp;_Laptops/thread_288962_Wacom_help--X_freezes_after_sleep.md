---
title: "Wacom help--X freezes after sleep"
date: 2006-10-30
forum: Hardware &amp; Laptops
---

### Post by quietphoks on 2006-10-30
I have a Wacom Cintiq 21UX on Ubuntu 6.06.  After installing wacom-tools and following the instructions on [https://help.ubuntu.com/community/Wacom]("https://help.ubuntu.com/community/Wacom") everything works fine, except that I can't wake the computer from sleep, using mouse, keyboard, or the Wacom.  I have ssh'ed to the computer in this state, and found that the process Xorg is taking a lot or all of the CPU (45% one time, 99.9% today).  

Killing Xorg remotely wakes the computer, and I'm back at the login screen.  

Under System>Preferences>Power Management I've set both "Put display to sleep when computer is inactive for" and "Put computer to sleep when it is inactive for" to "Never," but that hasn't helped.

Anyone have advice?  I would post a log file, but I'm not sure which is applicable to this problem.  Thanks,

---

