---
title: "How to change the location of default installation directory ?"
date: 2008-11-24
forum: General Help
---

### Post by rams123 on 2008-11-24
When I'm trying install any apps using terminal all apps are going to root . Is there any way to change that  to /home ? 

BTW: Why terminal will always install in / ?

---

### Post by CatKiller on 2008-11-24
Not generally. Packages are generally installed to /usr, in keeping with the Filesystem Hierarchy Standard, so that they are usable by all users. Configuration files are kept in /home, since they are per-user.

Programs that you compile yourself can be put in /home, but then they are only usable by that user.

There may be a way to install to ~/usr, but then you'd need to re-install the programs for each user, so I'm not sure why you'd want to. You'd also need to mess about with your $PATH to actually run the programs, or specify ~/usr/bin/programname each time. Since this seems sub-optimal, I don't know how you'd go about using it.

---

