---
title: "Lost touchpad settings after docking til sleep or restart."
date: 2012-04-09
forum: Hardware
---

### Post by T3kG33k on 2012-04-09
've been having a strange issue since I've began using Ubuntu on my Dell Latitude D630 and 610. The touchpad settings are apparently lost upon docking. If I restart, shutdown, or sleep the system then the settings are back to normal. The same thing happens after undocking.

This has been occuring since using Ubuntu 9.x and I'm currently using 10.10. I would be using 12.x but it ran like crap on my D630

I read that if I run
```
sudo modprobe -r psmouse; sleep 5; sudo modprobe psmouse
```
that the issue should be resolved but I have no clue as to create a udev rule.

This isn't a major problem but more of an annoyance that has persisted for a long time.

---

