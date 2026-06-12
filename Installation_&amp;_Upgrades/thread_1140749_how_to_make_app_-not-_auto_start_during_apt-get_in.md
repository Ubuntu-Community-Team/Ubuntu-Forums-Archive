---
title: "how to make app -not- auto start during apt-get install?"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by sirpelidor on 2009-04-27
hi,  I've installed a few apps which starts as soon as i turn on my computer (vmware, mysql, wine, cisco vpn etc).

i dunno how these daemons impacted my laptop's performance, but i would prefer to start them up manually.

should i just go ahead and delete them off /etc/init.d directory, or is there is a more elegant way to handle it?

thank you

---

### Post by tommcd on 2009-04-28
What version of Ubuntu are you running?

On Ubuntu 9.04 (and 8.10 also) you can click: system > preferences > startup_applications, and uncheck the things that you don't want to start automatically when the computer boots up.

---

### Post by sirpelidor on 2009-04-28
hi tommcd

i'm running 8.04 Hardy, and I don't see that option available.  can that be done via other means?

thank you

---

