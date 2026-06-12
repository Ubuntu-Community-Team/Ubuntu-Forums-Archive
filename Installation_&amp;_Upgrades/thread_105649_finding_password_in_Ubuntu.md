---
title: "finding password in Ubuntu"
date: 2005-12-18
forum: Installation &amp; Upgrades
---

### Post by ngant17 on 2005-12-18
I just installed Ubuntu from iso file as a CD copy.  I completely install, but I forgot the username and password.  How can I access this again?

---

### Post by g-a-c on 2005-12-19
Boot into single user mode (I think Ubuntu comes with some "recovery mode" boot time options which may send you into this). In single user mode, you get a single root shell, with no password prompt, and then you can do "passwd yourusernamehere" to reset the password for your user.

If you can't even remember the username, then you'll need to look in the file /etc/passwd to find it.

---

