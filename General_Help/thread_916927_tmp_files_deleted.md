---
title: "/tmp files deleted"
date: 2008-09-11
forum: General Help
---

### Post by allinurl on 2008-09-11
Hello, accidentally I deleted all files inside /tmp, and now Im unable to login into my account. it doesnt display any error, it just tries to login and then kick me out to GDM. Does anybody know how can I recover from this? Thanks

---

### Post by kpatz on 2008-09-11
Try rebooting, or restarting gdm.  /tmp is usually cleared on a reboot, so gdm has to start from scratch anyway, so that may do the trick.

To restart gdm, hit Ctrl-Alt-Backspace, or hit Ctrl-Alt-1, then log in to a console, and then enter the command **sudo /etc/init.d/gdm restart**

---

