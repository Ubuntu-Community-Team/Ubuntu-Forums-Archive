---
title: "changes in an ntfs partition"
date: 2007-08-07
forum: Hardware &amp; Laptops
---

### Post by ramiyyy on 2007-08-07
hi 

i have an ntfs partition on my machine
and i cant do any changes on this partition (read only mode)
how can i modify files there ?

rami

---

### Post by merlinus on 2007-08-07
```

sudo apt-get install ntfs-3g ntfs-config

```

then:

```

sudo ntfs-config

```

Tick the appropriate boxes and restart.

-merlin

---

