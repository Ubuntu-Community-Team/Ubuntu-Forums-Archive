---
title: "Blacklisting module aic7xxx doesn't work"
date: 2007-10-21
forum: Hardware &amp; Laptops
---

### Post by ianw1974 on 2007-10-21
I'm trying to stop the aic7xxx module loading on my system, so I blacklisted it in /etc/modprobe.d/blacklist as follows:

```
blacklist aic7xxx
```

I rebooted the system, and yet found that the module had loaded.  Why didn't the blacklist stop it?

---

