---
title: "How to stop screen lock on close"
date: 2006-06-04
forum: Hardware &amp; Laptops
---

### Post by .t. on 2006-06-04
I asked this before during development, but no one seemed to know. So, I'll ask it again:

About a month ago, I received an update which meant that when I closed my screen, the desktop locked. I do not know which update that was, nor which file changed, but I can see the change in behaviour. I'd like to reverse that change, so I plea: how can I stop the desktop locking when I close the screen?

---

### Post by mscman on 2006-06-04
I'm not currently on my laptop, so I can't test this theory, but in gconf-editor Apps > gnome-power-manager, there is an option to "lock on blank screen".  If you disable this, it should prevent the computer from locking

---

### Post by .t. on 2006-06-04
Thank you very much - that did the job perfectly. It should be made available in the gnome-power-manager preferences, though.

---

