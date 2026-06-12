---
title: "Terminal won't start (yup, It think I messed up)"
date: 2008-11-04
forum: General Help
---

### Post by Gonz_91 on 2008-11-04
So, here I am, playing around with the terminal settings, in a newly-created terminal, so the default wouldn't suffer. I set the option "Run a custom command instead of my shell" on, and then messed up real time: set that profile as the default. Result: I click "Terminal" on my panel, the taskbar shows an item called "Starting Terminal", which rapidly vanishes and nothing happens.


Help please! :(

---

### Post by bogdan.veringioiu on 2008-11-04
Hi.

Try to do this:

Alt+F2 (this is opening Run Application window)

Type:

gnome-terminal --window-with-profile=Default

In this way you open the terminal with the default profile.

Hope it works.

Bogdan

---

### Post by Gonz_91 on 2008-11-04
Thanks a lot! :)

---

