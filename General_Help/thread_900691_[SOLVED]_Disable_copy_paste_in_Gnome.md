---
title: "[SOLVED] Disable copy paste in Gnome"
date: 2008-08-25
forum: General Help
---

### Post by lsutiger on 2008-08-25
There is a reg setting in windows that can accomplish this. Is there an equivalent in Gnome?

---

### Post by lsutiger on 2008-08-25
OK - What I am trying to do is disable copying from an nx server to the client. 
I came across [this feature request]("http://www.nomachine.com/fr/view.php?id=FR03D01323") that states that it is possible, but I have no idea where to set this setting.
Anybody familiar with Nomachine NX??

---

### Post by lsutiger on 2008-08-25
OK - I figured it out!
According to []("http://www.nomachine.com/documentation/admin-guide.php") for Nomachine NX, in section 10.9, there is a config file locate at /usr/NX/etc/server.cfg.
Find the EnableClipboard option, remove the comment #, and set to "none".

I FREAKING LOVE LINUX!!!! Anything is possible!!

---

