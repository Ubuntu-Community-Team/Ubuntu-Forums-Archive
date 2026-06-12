---
title: "ventrilo problems in wine"
date: 2008-09-12
forum: General Help
---

### Post by codenamepenryn on 2008-09-12
hi, just installed ubuntu, and i have wine working. but their is a problem.

i installed ventrilo inside wine, worked fine at first. at first the chat worked, when i pressed the chat button, the chat came up fine. but then i decided to close vent. now when i go to vent, my name will have a "C" in front of it which means it thinks my chat box is already open, but it is not. is there anyway to fix this. Thx.

---

### Post by Predator106 on 2008-09-12
When you "go to vent"? What do you mean by this, is Vent running in a virtual window? This can cause problems sometimes. But yeah, the "C" does mean that you are supposedly in chat.

---

### Post by Thanoulis on 2008-09-12
Maybe wine refuses to close any connection. 
Try a:
```
killall wine
```
or a:
```
kilall wineserver
```

---

### Post by Predator106 on 2008-09-13
Oh okay, yeah, it probably didn't actually close, also doesn't Vent minimize to tray when you close it? In which case if it wasn't in a virtual window (probably isn't) then it will be in the notification area.

The guy above me is probably right, but that could also mean that it is still minimized to tray, so you could probably just right click vent and go to close.

Also, Thanoulis has a typo in his latter command, it's actually:
 
killall wineserver

Just to let you know.

---

