---
title: "Virtual console problem: can't return to desktop"
date: 2008-08-15
forum: General Help
---

### Post by jhsachs on 2008-08-15
I'm trying to use virtual consoles in my new 8.04 system, and am not having luck.

I found many posts by users who report that they can't switch consoles at all.  My problem is different: I can switch, but I can't switch back.

According to the book I'm reading, Ctrl+Alt+F1 through F6 should switch to virtual consoles 1 through 6, which display textual login prompts.  That works.  Ctrl+Alt+F7 should switch back to the desktop, but on my system it does nothing.  Once I've switched consoles, the only way I can escape is to reboot. Any suggestions?

---

### Post by yabbadabbadont on 2008-08-15
Hit Alt+F7 instead of Ctrl+Alt+F7 and see if it works.

---

### Post by jhsachs on 2008-08-16
> **yabbadabbadont said:**
> Hit Alt+F7 instead of Ctrl+Alt+F7 and see if it works.

Yes, it sure does. But only Ctrl_Alt+Fn works for switching to the others. What's the distinction?

---

### Post by yabbadabbadont on 2008-08-16
While in an X session, you have to use Control-Alt-Fn to switch out of X to the desired console tty.  When at a console tty, Alt-Fn is the standard shortcut for switching from one to another.  In this case, tty7 is used by default for the X server.

---

