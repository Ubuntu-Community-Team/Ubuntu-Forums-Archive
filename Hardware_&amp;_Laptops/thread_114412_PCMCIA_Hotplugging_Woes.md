---
title: "PCMCIA Hotplugging Woes"
date: 2006-01-08
forum: Hardware &amp; Laptops
---

### Post by bockman on 2006-01-08
Hello,

My wifi card (DWL-G650) works great, but only if inserted at boot time. If it is taken out, and reinserted it doesn't work either. What can I do to ameliorate this situation?

Ubuntu 5.10, 2.6.12-9-686.

---

### Post by Lambert on 2006-01-08
In your /etc/network/interfaces file you'll see something like this.

```
mapping hotplug
        script grep
        map ath0
        map eth0

```

except you won't have the map ath0 line. Add that so it hotplugs.

---

