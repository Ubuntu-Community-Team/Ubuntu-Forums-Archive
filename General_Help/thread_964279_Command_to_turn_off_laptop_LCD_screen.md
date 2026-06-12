---
title: "Command to turn off laptop LCD screen?"
date: 2008-10-30
forum: General Help
---

### Post by riahc3 on 2008-10-30
Is there a command to turn off laptop LCD screens? Then when I press a keyboard key/move the mouse it turns back on.

In my situation, a turn off display timeout is not possible as I want to instantly be able to turn it off/on. Anyway possible?

---

### Post by riahc3 on 2008-10-31
Or is it at least possible to somehow run this program under Ubunutu (WINE doesn't seem to work)

---

### Post by PsychedelicReaction on 2008-10-31
mmh i don't know about shutting down the screen, but you can make it black with the ctrl+alt+L combination

---

### Post by PsychedelicReaction on 2008-10-31
nevermind, run 

```
xset dpms force off
```

---

### Post by riahc3 on 2008-11-01
Thanks

---

### Post by hogancool on 2008-12-09
I was also looking for some solution of this problem, couse "xset dpms force off" doesn't work for me (Lenovo ThinkPad R61i) and i found that command:
```
 xset dpms force standby 
```

---

