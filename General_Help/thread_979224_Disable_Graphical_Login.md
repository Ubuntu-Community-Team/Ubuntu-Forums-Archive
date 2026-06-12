---
title: "Disable Graphical Login"
date: 2008-11-11
forum: General Help
---

### Post by WaddleDee on 2008-11-11
Heyy

How do I set my OS to tty1 every time I boot up?

Thanks, Waddle

---

### Post by Sam on 2008-11-11
System > Administration > Services


Uncheck "Graphical login manager (gdm)"

---

### Post by wx1gdave on 2010-02-13
I'm running the pre-release Lucid distro and want to disable the graphical login.  GDM is not started in services, nor is there a gdm script in /etc/rc2.d, or any of the rc#.d scripts.  I want to do this to get around a bug that prevents me from loging in without crashing the x session and having a system with keyboard locked.  Now, when I hear the login prompt, I go to another console, type "sudo gdm-stop", open another console, login, and type "startx".

Any suggestions?

---

### Post by flippo on 2010-02-13
Did you check /etc/init.d/ for gdm?  Thats where it usually sits.

---

### Post by wx1gdave on 2010-02-13
I found "gdm" in "/etc/init.d/".  If I just move it out of there, will I get a console login?

---

### Post by flippo on 2010-02-13
I think you should, you could alternatively 'chmod -x' it.

---

