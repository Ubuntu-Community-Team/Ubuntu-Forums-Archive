---
title: "tasksel question"
date: 2008-12-15
forum: Installation &amp; Upgrades
---

### Post by dittonamed on 2008-12-15
[**This image**]("https://help.ubuntu.com/community/Tasksel#Task descriptions") shows all the many software groups that can be installed via "tasksel". However, my newly installed system ONLY shows "SSH server" (which is checked). Yes, the list is one item long.

... but /usr/share/tasksel/ubuntu-tasks.desc has everything as expected.

I installed via the alternate install iso, and the system is a meant to be a server with no graphical interface.

Why is this list shorter than it should be?

Thanks!

---

### Post by dittonamed on 2008-12-15
also

```
sudo tasksel install lamp-server 
```

does nothing. no errors, no message

---

### Post by maybeway36 on 2008-12-15
If you used the alternate CD to install a CLI system, then you shouldn't have many of those tasks.
As for installing new tasks, I usually do that with aptitude.

---

### Post by dittonamed on 2008-12-16
running ```
apt-get update
``` fixed the problem

---

