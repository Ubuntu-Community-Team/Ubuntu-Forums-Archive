---
title: "Cannot switch to external monitor on Laptop"
date: 2008-11-07
forum: General Help
---

### Post by Peter09 on 2008-11-07
Argg... just preparing my laptop for a presentation this afternoon and find that I cannot switch to external monitor.... the function keys are not working

---

### Post by daleus on 2008-11-07
Ubuntu may be able to detect a monitor plugged in, when plugged in try go to System then screens (or something similar) and you may have the option to enable it.

Sorry I can't be more specific I am not at my machine at the moment!

---

### Post by Peter09 on 2008-11-07
Nope - discovered that none of my function keys work

---

### Post by soro2005 on 2008-11-07
Look under System --> Preferences for Screen Resolution. You can switch it from there. If you don't have it, type gnome-display-properties at a terminal.

If you have an Nvidia card, you may have to use the Nvidia XServer Settings tool, which you might find in System Administration.

---

### Post by Peter09 on 2008-11-07
Nothing under screen resolution because there is no additional screen recognized.

---

### Post by soro2005 on 2008-11-07
But the additional screen is plugged in and switched on? Have you hit "detect displays"? It should be plug'n'play.

---

### Post by Peter09 on 2008-11-07
No, nothing. This is really to do with the function keys, they enable the output port at the back of the`laptop.

---

### Post by soro2005 on 2008-11-07
Depending on your laptop model, the function keys may not work at all, or they may require additional set-up. In any case, they should not interfer with the X server detecting additional displays.

Have you tried pluging in your external screen and logging out/in of gnome?

---

