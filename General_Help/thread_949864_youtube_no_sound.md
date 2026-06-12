---
title: "youtube no sound"
date: 2008-10-16
forum: General Help
---

### Post by LidanJericho on 2008-10-16
I install Adobe Flash 10 and every clip i try to see i don't hear any sound..
what's the problem?

---

### Post by scouser73 on 2008-10-17
Open terminal and enter

[B]sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
ln -s /tmp/.esd-1000 /tmp/.esd[/B]

---

