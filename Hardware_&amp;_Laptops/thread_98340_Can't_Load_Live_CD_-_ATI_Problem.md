---
title: "Can't Load Live CD - ATI Problem?"
date: 2005-12-03
forum: Hardware &amp; Laptops
---

### Post by Georgie-o on 2005-12-03
I purchased a new laptop - WinBook - AMD Sempron with an ATI Radeon Xpress 200M.  During the install I got a screen that said 

"Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the the X server output to diagnose the problem?"

and asks "Yes"  or "No"

 and it would not install.  How can I configure something if it won't even install?  Any help?  I use Ubuntu on my Desktop PC and really want to use it on my laptop.

:???:

---

### Post by skycow on 2005-12-03
lol i have a compaq with the wideview screen and the same graphics card, and i am also having this problem only its after install and try to load it... already tried to reconfig and that didnt work

---

### Post by kook44 on 2005-12-03
Just got a new Dell desktop - same problem 
ATI Radeon X300 SE

stuck in windows hell till I can figure it out! 
:(

---

### Post by migueljacq on 2005-12-03
I got this error message once, but it was because I had been screwing around with the xorg.conf.
I fixed it by running sudo dpkg-reconfigure xserver.xorg

Funny that this happened for you guys straight off the bat, though, considering you hadn't been tampering like me :-/

Good luck

---

### Post by lilrockerboy on 2005-12-06
I'm actually having the same problem. The thing that sucks the most is I haven't used Linux in over 10 years! Now I'm being sucked back in and Ubuntu is perfect! I made my decision from the first screenshots. But whenever I put it in my Laptop with is a Gatway I also get the "*Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the the X server output to diagnose the problem?*" Is there a way around this, or did I get the wrong distro?! Thanks for your time!

---

### Post by Georgie-o on 2005-12-23
I found a way around it (at least sort of).  The Dapper release loads both live and install.  I know it may not be as usable or stable as Breezy, but it will have to do until a final release comes out in 3 months.  I figured I would try it because it seemed that almost no distros would work on this brand new set up.  Well, it looks like Ubuntu is catching up!  Now if I could just figure out this darn USB wireless I'd be golden..

---

