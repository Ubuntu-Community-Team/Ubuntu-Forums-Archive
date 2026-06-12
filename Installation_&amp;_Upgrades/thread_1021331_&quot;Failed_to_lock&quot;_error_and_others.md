---
title: "&quot;Failed to lock&quot; error and others"
date: 2008-12-25
forum: Installation &amp; Upgrades
---

### Post by bchecca1 on 2008-12-25
I'm trying to upgrade to 8.10 from 8.04 using the update manager and keep getting errors.
It comes up with "failed to lock /var/cache/apt/archives/lock". 

I've also noticed that this error:

 E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

occurs when I try to get updates.

Any ideas?
Bruce C.

---

### Post by damis648 on 2008-12-25
You have more than one package manager open (either apt or synaptic). Close one.

---

