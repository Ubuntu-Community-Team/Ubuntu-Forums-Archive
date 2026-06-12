---
title: "Panels all closed, how to reopen one?"
date: 2008-09-14
forum: General Help
---

### Post by pwaugh on 2008-09-14
I tried adding the contacts search app to a panel on Hardy, and it froze the panels.  I tried killing the X-Server and then logging in again, but the panels were then gone.

So, I opened a virtual terminal and halted the system, rebooting.

However, after logging in, they are still all gone.  How can I open one from the terminal?

Patrick

---

### Post by mb_webguy on 2008-09-14
Try "killall gnome-panel".

---

### Post by pwaugh on 2008-09-14
Found the answer here:

[http://ubuntuforums.org/showthread.php?t=913530&highlight=open+panel+terminal](http://ubuntuforums.org/showthread.php?t=913530&highlight=open+panel+terminal)

Basically typed "gnome-panel&" at the terminal, and used gconf-editor too.

Thanks

---

