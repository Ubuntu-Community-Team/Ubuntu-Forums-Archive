---
title: "whats wrong with my comp?"
date: 2008-08-24
forum: General Help
---

### Post by IrunoHatake on 2008-08-24
w/e i put in a command to download something it says could not get a lock on /var/lib/dpkg/lock  - open (resource temporarily unavailable) it also says something about is another process using it? and now that i read it would me using update manager while doing this be the problem?

---

### Post by cariboo on 2008-08-24
Your problem is you have either synaptic or update manager open, close it and then your command line install should work.

Jim

---

### Post by Yellow Pasque on 2008-08-24
As noted above, close synaptic or update manager. If they're not open and you're still getting this message, it means synaptic or another package manager crashed before removing its lock and you have to remove it manually.
```
sudo rm -f /var/lib/dpkg/lock
```

---

