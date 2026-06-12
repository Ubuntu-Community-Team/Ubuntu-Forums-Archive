---
title: "kio_file eating memory"
date: 2009-04-18
forum: Installation &amp; Upgrades
---

### Post by odinb on 2009-04-18
Hi!

Have 2 processes called kio_file. Since last nights Jaunty updates (do not know if related) they are eating memory, and causing my machine to lock up.

Since I run 64bit and have 4GB of RAM, it takes a couple of hours before this happens. Has happened 3 times since late last night.

Any idea on what I can/should do? What can I pull from the system either before this happens, or after it happens to try and figure it out?

Does this process belong with KDE? I run ubuntu, but have ktorrent installed.

Regards,

//Odin

---

### Post by odinb on 2009-04-19
kio-file is indeed a file that is part of KDE. It has to do with IP-traffic.

ktorrents filter function is the culprit here. The filter would not autoupdate, and that caused this enormous leakage of memory. Doing a manual update satisfied the process, and i am no longer experiencing this issue.

Question is though, where do I report this bug?

---

