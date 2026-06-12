---
title: "How should I partition my drive?"
date: 2009-09-04
forum: Installation &amp; Upgrades
---

### Post by sblunix on 2009-09-04
Hey everybody, I've got a 250GB HDD, and I've never made a "/home" partition before, but I heard it was really useful for reinstalling (etc, etc) so, I want to partition this 250GB HDD to 1 "home" partition, 1 "system" partition, and 1 "swap" partition? How much should each partition get allocated?

---

### Post by pastalavista on 2009-09-04
> **sblunix said:**
> Hey everybody, I've got a 250GB HDD, and I've never made a "/home" partition before, but I heard it was really useful for reinstalling (etc, etc) so, I want to partition this 250GB HDD to 1 "home" partition, 1 "system" partition, and 1 "swap" partition? How much should each partition get allocated?

Just me, but I would create a / partition of about 50 GB, a swap partition with as much space as you have RAM (more if you plan to suspend or hibernate with several apps running) and all the rest, /home

You might want to make those 'logical' partitions inside one larger 'extended' (primary) partition in case you want to leave some room for other storage or a multi-OS system. You're only allowed 4 primary partitions max.

---

### Post by Vaphell on 2009-09-04
imo 50GB for / is way too much, i got 20GB and it's 50% used after ~2 years. I don't install millions of packages for the sake of it though.

---

