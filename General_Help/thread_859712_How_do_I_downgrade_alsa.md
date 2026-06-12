---
title: "How do I downgrade alsa?"
date: 2008-07-14
forum: General Help
---

### Post by ryanrad on 2008-07-14
Hello Everyone.  I have a Panasonic CF-74 with a problem that is common to many laptops, sound issues.  My variation is that I get sound out of the headphone jack, but not the speakers.

I'm lucky enough to have several hard drives at my disposal.  One of those hard drives has Ubuntu 7.04 installed on it.  When I install the 7.04 hard drive, my sound works perfectly.

My question to the forum is, "What is the best way to downgrade to alsa-base_1.0.13-3ubuntu1_all?"  More specifically, how do I remove the current version 1.0.16 and install 1.0.13?

Please help,
Ryan

---

### Post by ghost_ryder35 on 2008-07-14
```

sudo aptitude remove alsa-base_1.0.16 && sudo aptitude install alsa-base_1.0.13-3ubuntu1_all

```

---

