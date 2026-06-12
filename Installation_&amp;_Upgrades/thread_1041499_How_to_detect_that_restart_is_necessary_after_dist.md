---
title: "How to detect that restart is necessary after dist-upgrade"
date: 2009-01-16
forum: Installation &amp; Upgrades
---

### Post by glenroe on 2009-01-16
I have searched for this using what I thought were the obvious search terms, but can't come up with the answer.

How can I tell from a script that a restart is necessary after an upgrade?

I have a couple of machines I access remotely that do an automatic apt-get update and apt-get dist-upgrade every night, and I want to be able to log in and find out if a restart is necessary and reboot when it is convenient.

---

### Post by cariboo on 2009-01-16
Generally speaking the only time you have to reboot after an upgrade is if there is a new kernel, and only then, if the upgraded kernel has something you really need.

Jim

---

