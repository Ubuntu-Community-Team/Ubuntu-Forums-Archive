---
title: "[SOLVED] Trayer Always On Top"
date: 2008-09-20
forum: General Help
---

### Post by Mark76 on 2008-09-20
I'm running trayer as part of an openbox set up and I noticed that when I drag windows over it it appears on top of them.

I looked in the manual for trayer, but I couldn't see anything that might modify this behaviour.

---

### Post by Predator106 on 2008-09-20
I have no idea what Trayer is, but with any window you can right click it's titlebar or taskbar object and check/uncheck Always On Top. Not sure if this will help permanently

---

### Post by Mark76 on 2008-09-20
It's a system tray application.

---

### Post by Predator106 on 2008-09-20
Oh, lol, I thought you were talking about it being in a window form. Welp, that just made me look stupid :)

---

### Post by Mark76 on 2008-09-23
I found the solution. You just have to set SetDockType to false in the start up configuration :D

---

