---
title: "Change resolution after suspend"
date: 2006-07-27
forum: Hardware &amp; Laptops
---

### Post by garethj on 2006-07-27
Hi,

I have an IBM T42p ThinkPad and on first loading X can change resolution quite happily. However, if I suspend (sleep, not hibernate) and then resume, the resolution switcher application (System->Preferences->Screen Resolution) acts as if it is changing resolution but the resolution does not actually change. Restarting X solves the problem.

Anyone have any ideas or advice?

Thanks,

Gareth

---

### Post by goanga on 2008-04-21
Hello,

I have the same problem on a Dell Inspiron 6400. I use a script that calls xrandr to turn on/off SVHS output, and it only works after I restart X. Switching back to the original resolution works flawlessly.

Any ideas/solutions?

Edit: Forgot to mention I'm using hardy beta

---

