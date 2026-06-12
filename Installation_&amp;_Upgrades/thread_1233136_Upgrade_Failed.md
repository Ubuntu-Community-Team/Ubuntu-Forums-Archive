---
title: "Upgrade Failed"
date: 2009-08-06
forum: Installation &amp; Upgrades
---

### Post by helmsdb on 2009-08-06
I'm trying to install an upgrade to Ubuntu - the error message says  E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open()failed, please report

I don't know how to run this command manually - how do I get into manual mode?

---

### Post by Partyboi2 on 2009-08-06
Hi, do as it says, open a terminal (Applications>Accessories>Terminal) and type
```
sudo dpkg --configure -a
```

---

### Post by helmsdb on 2009-08-06
Thanks - I'll see if that helps!:)

---

### Post by Partyboi2 on 2009-08-06
> **helmsdb said:**
> Thanks - I'll see if that helps!:)
If it does not fix it, post the output to the 'sudo dpkg --configure -a' command so we can see what the problem could be.

---

