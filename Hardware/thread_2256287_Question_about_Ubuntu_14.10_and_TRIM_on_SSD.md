---
title: "Question about Ubuntu 14.10 and TRIM on SSD"
date: 2014-12-11
forum: Hardware
---

### Post by leillo1975 on 2014-12-11
Hello 

Recently I buyed a Kingston HyperX Fury SSD. I read in a Blog that we have to schedule a weekly TRIM, but when I tried to edit "/etc/cron.weekly/fstrim", I found by default this:

```
#!/bin/sh
# trim all mounted file systems which support it
/sbin/fstrim &#8211;all || true
```

Does this mean that a weekly check is performed?

I know that in Ubuntu 14.04, TRIM is automatic in Samsung and Intel SSD's, but in 14.10...

---

### Post by kpatz on 2014-12-11
> **leillo1975 said:**
> Does this mean that a weekly check is performed?

I know that in Ubuntu 14.04, TRIM is automatic in Samsung and Intel SSD's, but in 14.10...The TRIM is handled by the cron job you found.  It appears that it's always installed in 14.04 and 14.10.  My 14.04 VMs have it, even though they aren't running on any SSDs.

---

