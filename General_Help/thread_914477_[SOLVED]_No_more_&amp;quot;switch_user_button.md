---
title: "[SOLVED] No more &amp;quot;switch user button"
date: 2008-09-08
forum: General Help
---

### Post by pi.boy.travis on 2008-09-08
Just curious. . . I have noticed that the dialog displayed during system wake up no longer has a "switch user" button.  I only have one user, but it was useful to be able to get back to the login screen if I needed to.  Is this the result of an update?  Can I turn it back on?

Thanks!

---

### Post by pi.boy.travis on 2008-09-09
Bump

---

### Post by pi.boy.travis on 2008-09-10
I just tested this with a virtual machine, and with all updates installed it still had a switch user button.  Any way to get this back on my host system?

EDIT:  OK, even if I add another user, the button isn't there. . .

---

### Post by etnlIcarus on 2008-09-10
Right-click on an empty part of the panel and there should be an option to add items/applets/plugins to the panel. Clicking on that will bring up a list of icons you can drag-and-drop onto your panels. One of them will be the applet you're looking for.

Sorry I couldn't be more specific but I don't use Gnome.

---

### Post by Nepherte on 2008-09-10
To enable it, open up gconf-editor:
```
gconf-editor
```

Navigate to apps/gnome-screensaver and check user_switch_enabled.

---

### Post by pi.boy.travis on 2008-09-10
Thanks!  That fixed it!

Wonder how that happened in the first place. . .

---

