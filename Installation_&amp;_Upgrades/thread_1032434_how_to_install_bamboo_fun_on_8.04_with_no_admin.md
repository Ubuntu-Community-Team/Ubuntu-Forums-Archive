---
title: "how to install bamboo fun on 8.04 with no admin?"
date: 2009-01-06
forum: Installation &amp; Upgrades
---

### Post by johnny linux on 2009-01-06
is it possible to get my bamboo fun to work without using admin?

---

### Post by Rithmarin on 2009-01-06
The drivers are already loaded, but I needed to uncomment some lines in xorg.conf to get ubuntu to use mine as more than just a mouse.

The command I used was "sudo vi /etc/X11/xorg.conf" which is a bit of admin with a normal user, so not sure how that falls in with your question.

I also had to start ubuntu with the tablet plugged in as I never managed to get hotplug to work...

---

