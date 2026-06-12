---
title: "screen locked after suspend"
date: 2009-04-29
forum: Hardware
---

### Post by arod0405 on 2009-04-29
xubuntu 9.04, fresh install.
after suspend to ram and resume screen is locked (gnome-screensaver fault I guess) even if "lock screen when screensaver is active" is not checked.
I'd like not to enter any password upon resume. is that possible?
Thanks!

---

### Post by blackSP on 2009-05-12
Bump!

I have the same issue, #LOCK_SCREEN=true does not disable it anymore, it did in 8.10!

---

### Post by James Keating on 2009-05-13
At least in the standard Ubuntu Gnome session, you can bypass the requirement for entering a password on suspend/resume this way:

1. run gconf-editor (NOT as root -- this sets per-user settings)
2. navigate to apps / gnome-power-manager / lock
3. uncheck the locks for suspend and hibernate, and everything else

---

### Post by m4lte on 2009-05-15
> **James Keating said:**
> At least in the standard Ubuntu Gnome session, you can bypass the requirement for entering a password on suspend/resume this way:

1. run gconf-editor (NOT as root -- this sets per-user settings)
2. navigate to apps / gnome-power-manager / lock
3. uncheck the locks for suspend and hibernate, and everything else

Works for me in Ubuntu 9.04. Thanks!

---

### Post by Rogerborg on 2009-09-18
\\:D/ Confirmed; this works in 9.04.  Great advice, many thanks.  Strange that it's not in the GUI.

---

