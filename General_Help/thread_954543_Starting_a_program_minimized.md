---
title: "Starting a program minimized"
date: 2008-10-21
forum: General Help
---

### Post by Kevbert on 2008-10-21
I'm trying to autorun a program so that it's either minimized or a certain window size when I boot into Ubuntu. What's the best way to do this ? (preferably when started under sessions).

---

### Post by RequinB4 on 2008-10-21
Assuming you have compiz, I'd suggest modifying this tutorial to meet your needs:

[http://maketecheasier.com/terminal-as-transparent-wallpaper-in-ubuntu/2008/05/21](http://maketecheasier.com/terminal-as-transparent-wallpaper-in-ubuntu/2008/05/21)

Worked wonders for me

---

### Post by Kevbert on 2008-10-21
Thanks for the link.

---

### Post by sethvath on 2008-10-21
That compiz link is not what you're looking for. In sessions, just add "--start-hidden" ie. /path/to/program --start-hidden

---

### Post by Kevbert on 2008-10-21
> **sethvath said:**
> That compiz link is not what you're looking for. In sessions, just add "--start-hidden" ie. /path/to/program --start-hidden

Unfortunately that didn't work. When I tried it the program ran in a window. I also tried it via terminal and got the following:
```
$ liferea --start-hidden
Liferea encountered an unknown argument: --start-hidden

```
Also tried it with different spacing between arguments and that made no difference.
I've found a new way of doing this.  With Liferea minimized (only the top menu icon showing) and just clicked on Remember Current-Running Applications button under Session Options Tab, closed Sessions and rebooted. It initially shows a window when the Desktop is first shown, but this then disappears immediately.  Where is this information saved ?

---

### Post by Kevbert on 2008-11-03
bump

---

