---
title: "right click problem"
date: 2008-10-18
forum: General Help
---

### Post by krishna1650 on 2008-10-18
trying to set video as wallpaper i made some changes in gconf-editor.
now when i click right mouse button nothing is shown.
how to show it?

---

### Post by Genius314 on 2008-10-18
You probably disabled Nautilus from drawing the desktop. (You need to in order to see the animated desktop, I think...)
Go back into Gconf-Editor, go to /apps/nautilus/preferences, and check the box for "show_desktop." That should work. :)

---

### Post by krishna1650 on 2008-10-18
> **Genius314 said:**
> You probably disabled Nautilus from drawing the desktop. (You need to in order to see the animated desktop, I think...)
Go back into Gconf-Editor, go to /apps/nautilus/preferences, and check the box for "show_desktop." That should work. :)

thanks it worked.

---

