---
title: "[SOLVED] Updated, Networking Icon Disappears?"
date: 2008-08-01
forum: General Help
---

### Post by Jesdisciple on 2008-08-01
I just updated 75 packages and the networking icon disappeared from my "Notification Area Applet"...  How can I get it back?  (And I don't mean the Network Monitor that goes directly on the panel; when I right-click the one I have in mind, I get the option to Enable/Disable Networking.)

Thanks!

---

### Post by prshah on 2008-08-01
> **Jesdisciple said:**
> the networking icon disappeared from my "Notification Area Applet"...  How can I get it back?

Open a terminal (Applications-Accessories-Terminal) and give the command ```
nm-applet
```

The reason I suggest a terminal is that if there are any errors, we can see those, since nm-applet should not normally disappear by itself.

If there are no errors, and nm-applet works fine, it will disappear again when you close the terminal; in that case, press Alt+f2, and repeat the same command as above again. This time, it will "stick".

---

### Post by Jesdisciple on 2008-08-01
That did it; much thanks!

---

