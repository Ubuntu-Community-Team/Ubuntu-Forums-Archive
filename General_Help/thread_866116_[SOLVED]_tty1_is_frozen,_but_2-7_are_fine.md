---
title: "[SOLVED] tty1 is frozen, but 2-7 are fine"
date: 2008-07-21
forum: General Help
---

### Post by TeeAhr1 on 2008-07-21
I'm not entirely sure how this happened (it's on my server, and I haven't had any reason to look at it in a while, but tty1 seems to be frozen. 2-7 are fine, I can switch back and forth between them and even back and forth to tty1, but tty1 won't take any other input. I tried killing the processes that were running on it, didn't help. Any guidance would be appreciated, I've got a house record for uptime going, and I really don't want to reboot ;)

thx-
p.

---

### Post by TeeAhr1 on 2008-07-21
Solved (how do I always do that thirty seconds after posting?). I ran "ps -A|grep tty1" and saw that bash was still running there. Killed it, problem solved. We now return you to your regularly scheduled programming.

---

