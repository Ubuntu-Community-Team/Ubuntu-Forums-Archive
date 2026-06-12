---
title: "Can't find hard drive"
date: 2008-11-13
forum: General Help
---

### Post by Burningice95 on 2008-11-13
I'll start off by saying that my computer is a gateway 6860 fx, and that it came with a main partition and a recovery partition. I installed Ubuntu with Wubi, and now it only sees the recovery partition. I have not been able to get ubuntu to see the C:/ main partition. anyone have any ideas on how i can fix this?

---

### Post by prshah on 2008-11-13
> **Burningice95 said:**
> it came with a main partition and a recovery partition. I installed Ubuntu with Wubi, and now it only sees the recovery partition. I have not been able to get ubuntu to see the C:/ main partition. 

The main partition serves as a "host" for the wubi-installed ubuntu. You cannot then mount the "host" partition in wubi ubuntu. 

Workarounds? 
a) install ubuntu to a separate, dedicated partition.
b) create a separate windows "D:" drive to host your wubi-ubuntu files. Or install wubi-ubuntu to the recovery partition if space and permissions permit.

---

