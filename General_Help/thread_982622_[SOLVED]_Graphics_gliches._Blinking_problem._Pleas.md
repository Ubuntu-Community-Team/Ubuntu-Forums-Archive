---
title: "[SOLVED] Graphics gliches. Blinking problem. Please help."
date: 2008-11-14
forum: General Help
---

### Post by Marius Derekus on 2008-11-14
hello,
I have Ubuntu 8.04 on an acer extensa with an **Ati radeon Xpress 1250 **graphics card, my graphics card seems to be working perfectly because **glxgears** worked and when i types this command
** glxinfo | grep direct** which tests to see if you have 3d acceleration, it said yes. The only problem i have is that when glxgears or 3d chess runs(these are the only 3d programs i have tested on ubuntu so far), the 3d animation blinks. you will see the 3d gears running, and then they will frequently blink. On 3d chess the graphics will show for about 2 seconds, then go black, then show again. Is there anything I can do to fix this?

---

### Post by ztrange on 2008-11-15
Are you using compiz? Its known that it has issues with opengl acceletation. Try to disable it and see if you still ahve the same issue.

---

### Post by Marius Derekus on 2008-11-15
Thanx, you were right!. Compiz was cuasing the issue. I got a program called compiz-switch so i can temporarily disable it when i need to.
THANK YOU VERY MUCH!

---

