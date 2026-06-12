---
title: "I can play DVD's but cannot get burner to work"
date: 2014-12-11
forum: Hardware
---

### Post by vondalej on 2014-12-11
I got a Toshiba super multi and cannot figure out how to get it working.  Fairly new to ubuntu, but usually google solves my problems.  Can't find a working solution for this one.

---

### Post by carl4926 on 2014-12-11
> **vondalej said:**
> I got a Toshiba super multi and cannot figure out how to get it working.  Fairly new to ubuntu, but usually google solves my problems.  Can't find a working solution for this one.

Lets assume it's Ubuntu
14.04 or 14.10
Either way I use k3b for burning, because it just works.

---

### Post by vondalej on 2014-12-11
> **carl4926 said:**
> Lets assume it's Ubuntu
14.04 or 14.10
Either way I use k3b for burning, because it just works.

12.04.  I've tried 4 or 5 different programs including k3B.  K3B says it can't find any optical devices despite the fact that the DVD icon pops up on the launcher and I can play DVDs.

---

### Post by carl4926 on 2014-12-12
Please make sure all looks OK in the k3b settings
See this clip: [https://dl.dropboxusercontent.com/u/10573557/Ubuntu/k3b_settings.mp4](https://dl.dropboxusercontent.com/u/10573557/Ubuntu/k3b_settings.mp4)

FYI: Optical drives often fail. And you can have the read work and the burner fail. Probably you need a new one.

---

### Post by pqwoerituytrueiwoq on 2014-12-12
```
sudo hwinfo --cdrom >2 /dev/null
```
can we verify via software that it is infant a burner?

---

