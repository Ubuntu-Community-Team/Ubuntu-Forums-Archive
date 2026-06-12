---
title: "Panel crashed, now has disappeared"
date: 2008-09-28
forum: General Help
---

### Post by Robotman on 2008-09-28
While adding an application launcher to my panel, the panel crashed.  Now I can't get it to reappear at all.  Logging out and rebooting don't bring it back, and nothing happens when I try to open the Panel settings in Xfce Settings Manager.
Does anyone know how I can get my panel back?

---

### Post by fooman on 2008-09-28
press alt-f2

if that brings up a run dialog box,  type this into and hit "run":

```
xfce4-panel &
```

if alt-f2 doesn't work...see if you can open a terminal and try that same command there.

---

### Post by Robotman on 2008-09-28
Many thanks! Panel's back and looking good. ;)

---

### Post by miket262 on 2008-12-18
FYI I've encountered this a couple of times, and the solution that is the complete fix in my experience is:
* log out
* log in on a text console (Ctrl-Alt-F1) and "rm -rf .cache"
* Ctrl-Alt-F7 and try the xfce login again
If there are still problems
* log out
* log in on a text console and "rm -rf .cache .config"
* try xfce again
If you remove .config you'll get back to the default panel and have to reapply your changes. To avoid this in the future, after you're done with your tailoring and are logged out, go to the text console and
* tar czvpf config.tgz .config
Then when things go bad you can, while logged out of xfce and from a text console
* rm -rf .cache .config
* tar xzvpf config.tgz
When you next log in your xfce panel should be back to what it was when you created the config.tgz "snapshot"

---

