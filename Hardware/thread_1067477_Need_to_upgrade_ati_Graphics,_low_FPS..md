---
title: "Need to upgrade ati Graphics, low FPS."
date: 2009-02-11
forum: Hardware
---

### Post by AllRadioisDead on 2009-02-11
Hi, I just installed halo on ubuntu, but I'm only getting about 15-20 fps. I've checked, catalyst cp, and My version is from 2 years ago. I went to the ati website, I downloaded the latest .run file, I ran the file, I think I installed it, but my catalyst version is still the same, and I still get the same low fps. Did I do something wrong? (I'm running an ati radeon 4850)

---

### Post by nixscripter on 2009-02-14
The first thing I would check is to see if you're getting direct rendering from the card.

Open a terminal and type: ```
glxinfo | grep direct
``` It should say: direct rendering yes.

---

### Post by AllRadioisDead on 2009-02-16
I rebooted and my FPS shot up back to normal, thanks.

---

