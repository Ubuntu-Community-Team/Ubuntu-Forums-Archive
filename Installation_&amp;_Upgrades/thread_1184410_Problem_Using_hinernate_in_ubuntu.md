---
title: "Problem Using hinernate in ubuntu"
date: 2009-06-11
forum: Installation &amp; Upgrades
---

### Post by gkgm on 2009-06-11
I user installed hibernate package yesterday by using sudo apt-get hibernate. But when I run sudo hibernate it gives the following error msg... pls help me ..


egyaan@gBuntu:~$ sudo hibernate
[sudo] password for egyaan: 
hibernate:Warning: Tuxonice binary signature file not found.
Some modules failed to unload: nvidia
hibernate: Aborting suspend due to errors in ModulesUnloadBlacklist (use --force to override).

---

### Post by Mighty_Joe on 2009-06-11
That sounds like [this bug]("https://bugs.launchpad.net/ubuntu/+source/hibernate/+bug/94051").  You may want to search Launchpad and this forum for people who have the same hardware you are using.  Perhaps someone has a workaround.

---

