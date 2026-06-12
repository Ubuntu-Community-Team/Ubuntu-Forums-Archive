---
title: "Intel Core Duo: constantly at ~50% high CPU load"
date: 2006-09-08
forum: Hardware &amp; Laptops
---

### Post by el3ktro on 2006-09-08
Hello,
I just installed Dapper on my Averatec 2460 with Intel Core Duo and Intel 945GM chipset. I've installed the linux-image-686-smp kernel. The gnome-system-monitor shows me a constant CPU load of 20-60% on both CPUs, but neither in gnome-system-monitor or top I see any processes taking so much CPU. Can anybody confirm this or does somebody have a solution?

Tom

---

### Post by el3ktro on 2006-09-08
Ok after messing around with my system I can definitely say that /etc/init.d/powernowd is the bad guy. When I stop powernowd and powernowd.early CPU load suddenly drops to around 7% on both cores - which I still think is a little high, but definitely much better than 50%.

The question now is, are there any known _working_ alternatives for an Intel Core Duo CPU?

Tom

---

