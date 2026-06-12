---
title: "[SOLVED] multiple kernels in dual boot"
date: 2009-01-10
forum: Installation &amp; Upgrades
---

### Post by karrank% on 2009-01-10
Apologies if already posted, but I've got multiple kernels showing up in the grub bootscreen menu and it's confusing/ annoying my household. Can I shave it down to just one? Pros and cons anyone? 

Thanks for taking the time to consider this!

XP/Hardy dual boot 
Emachines E1200-01e
Athlon 2650e
2G RAM

Solved!~found it in startup manager (installed from synaptic)

---

### Post by aheckler on 2009-01-10
You can remove older kernels from your machine altogether by searching in Synaptic for "linux-image" and removing the old ones. BE CAREFUL though, removing the current one would be A Bad Thing To Do.

---

### Post by karrank% on 2009-01-11
> **aheckler said:**
> You can remove older kernels from your machine altogether by searching in Synaptic for "linux-image" and removing the old ones. BE CAREFUL though, removing the current one would be A Bad Thing To Do.

Heh, you must have known i was thinking that! I just don't see the reason for keeping all the old kernels around filling up the disk space so will investigate that option. CAREFULLY.

ps. love the Hobbs avatar.

---

