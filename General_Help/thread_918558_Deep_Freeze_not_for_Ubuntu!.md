---
title: "Deep Freeze not for Ubuntu!"
date: 2008-09-13
forum: General Help
---

### Post by branko.savic on 2008-09-13
I need a program like Faronics Deep Freeze in ubuntu, but the progrgam they have on their site does not seem to be working in ubuntu!

Is there an alternative or can someone please create a program like that?

Thanks in advance!

---

### Post by eentonig on 2008-09-13
You don't need a program to achieve that.

System wide settings are protected by default, unless you specifically enable root privileges for yourself to change something.

All a regular user (or potentionally a virus activated by a user) could do, is change settings in his personal home folder. And this can be protected via two simple things:

1. Change the permissions on the configuration files (.somtehing), so you can't overwrite them by accident.
2. Save a copy of all needed .something files and folders and have a script save that copy back when the user logs out.

---

