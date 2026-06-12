---
title: "[SOLVED] How do you get the control alt escape/backspace keys?"
date: 2008-09-01
forum: General Help
---

### Post by ronnielsen1 on 2008-09-01
I'm used to using kde but I decided to see what the new ubuntu was like and it's sucking me in (which is amazing for me - never went with gnome before) so excuse me if this is a kde specific thing. How do you get control alt escape and control alt backspace working? They do nothing on my box.

---

### Post by meindian523 on 2008-09-01
Ctrl+Alt+Backspace is not a DE-specific thing.It kills the Xserver regardless of which DE you are running.I wouldn't know anything about Ctrl+Alt+Esc.What's that used for?

---

### Post by ronnielsen1 on 2008-09-01
Ok, the control-alt-backspace thing did work and after a little googling it appears that control-alt-escape belongs to kwin

Control-alt-escape brings up a x that you can click on an unresponsive window and kill it. It works great.

---

### Post by meindian523 on 2008-09-01
The corresponding command in GNOME is ```
xkill
```This and the following commands can be run in the Run Application dialog box(Alt+F2) and also,you can use ```
pkill <app_name>
``` or to kill all instances of an app```
killall <app_name>
```

---

### Post by ronnielsen1 on 2008-09-01
That's great! Thank you

---

### Post by meindian523 on 2008-09-01
You are welcome.Please mark the thread solved.

---

