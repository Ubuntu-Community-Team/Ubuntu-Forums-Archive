---
title: "RAID1 - has a drive failed?"
date: 2006-06-26
forum: Hardware &amp; Laptops
---

### Post by jinx099 on 2006-06-26
I'm considering setting up Ubuntu server on a headless server with a RAID1 setup, using 2 older drives.  The problem I see with this setup is how would I tell if a drive has failed?  If a drive fails and I dont know about it, then the array is no better than a single drive.

So how would I know if a drive has failed?

---

### Post by evilghost on 2006-06-26
cat /proc/mdstat

There used to be an application that would monitor mdstat for changes and report but dang if I can't find it.

---

