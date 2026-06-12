---
title: "[SOLVED] Speed of autohide animations"
date: 2008-10-18
forum: General Help
---

### Post by aero528 on 2008-10-18
Hey, all.  I'm running Ubuntu 8.10 beta on my desktop.  I have my task bars set to auto hide, and I like how it looks.  My only problem is that when it I bring my mouse up to them, it takes them a full second or second and a half to pop out.  Is there a way I can make that almost instant? If I run gconf-editor then go to >apps>panel>global I can change a couple of those settings, but they don't seem to change anything, even after a restart.  Any ideas?  Thanks.

---

### Post by loell on 2008-10-18
even changing **/apps/panel/toplevels/** panel_*'s delay in gconf? from 500 to shorter?

---

### Post by aero528 on 2008-10-18
Yep, that did the trick.  I was working in global, and changing it from 500 to about 200, but I ended up just changing it to 0, which works great.  Thanks!

---

### Post by loell on 2008-10-18
no problem. :)

---

