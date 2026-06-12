---
title: "Crash in the middle of ugprade to 9.04... what to do??!"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by CaptSaltyJack on 2009-04-25
I have a machine running 8.10, and I ran the update manager to upgrade to 9.04.  It grabbed everything fine, and got to the stage where it asks "hey, your /etc/mysql/my.cnf.. use yours, or the distribution package's?"..and the machine locked up on me for some reason.  I'm going to have to hard reset it, BUT I want to know how to get back to that stage where it's going through all the file updates, patching the system, and asking which .conf file to use.

Help?

---

### Post by CaptSaltyJack on 2009-04-26
bump...

---

### Post by CaptSaltyJack on 2009-04-26
Nevermind, got it.  Just rebooted, and did: sudo apt-get dpkg --configure -a

That resumes the package updating process, apparently.

---

