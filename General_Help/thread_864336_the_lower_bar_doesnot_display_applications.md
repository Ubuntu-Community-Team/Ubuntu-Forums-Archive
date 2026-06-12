---
title: "the lower bar doesnot display applications"
date: 2008-07-19
forum: General Help
---

### Post by Newbi on 2008-07-19
hi..

i got a problem here.. i was surfing the net and unexpectedly the lower bar of gnome has stopped displaying all the application windows. This is causing a lot of problems.

For example , in the screen shot , firefox is running but it is not being displayed on the lower bar

Can any one help me to fix it. Thanks

---

### Post by aashay on 2008-07-19
Right click the lower panel, click 'Add to panel' In the window that pops up, Select "window list" and "add" it

---

### Post by Newbi on 2008-07-19
yup.. got it... thanks mate :)

any idea how o move it?? mine is stuck somewhere near the middle..

also a big thanks to this post: 

[http://ubuntuforums.org/showthread.php?t=65005&page=2](http://ubuntuforums.org/showthread.php?t=65005&page=2)

---

### Post by briwood on 2008-07-19
Haven't seen this before...

To fix I would try

   killall gnome-panel 

from a terminal.  You shouldn't need to sudo for that. 

The panel will disappear and the reappear after a few seconds.

If it doesn't reappear, in a terminal type

   gnome-panel

Hope that helps.  This treats the symptom, but not the problem.  Does this only happen with Firefox?  If so, make sure you have the latest FF and disable your FF Add-ons for a while to see if that fixes it

---

### Post by Newbi on 2008-07-19
just tried it.. we do need sudo for it

---

### Post by Newbi on 2008-07-19
but this problem is for a a single user only and not other users

---

