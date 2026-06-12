---
title: "Having to re-load compiz on each login (using emerald too)"
date: 2008-08-07
forum: General Help
---

### Post by dougmmms on 2008-08-07
I recently installed 8.04 from scratch.  Everything was working fine.  I decided to install emerald and the compiz-fusion icon.  I customized the window decorations via emerald and set it so that emerald was used rather than gtk.  Now whenever I login, I have to reset compiz (the window borders are missing).  Once reset, all is fine.  It's annoying to have to do so, though.  Any suggestions?  Thank you.

---

### Post by 00arthuryu on 2008-08-07
have you tried putting 
```
fusion-icon
```
in session startup?

---

### Post by dougmmms on 2008-08-07
I certainly have.  Oddly enough, it never loads.  I don't think that it loading would make a difference; the issue is with compiz or emerald.  I made sure emerald theme manager is loaded each session as well.

---

### Post by raven_keii on 2009-05-06
Daaaa! it was pretty obvious jajaja what worked for me is to deactivate metacity compositing manager! how? well alt+f2, type "gconf-editor" without quotes then go to apps>metacity>general and uncheck compositing_manager, now close session when you came back it should be done !!!

---

