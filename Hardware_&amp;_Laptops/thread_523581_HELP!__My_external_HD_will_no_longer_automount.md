---
title: "HELP!  My external HD will no longer automount"
date: 2007-08-12
forum: Hardware &amp; Laptops
---

### Post by rockmanac on 2007-08-12
Kubuntu 7.04... It's able to see that I had plugged the drive in, and I was able to manually mount by typing

```
adam@willow:/media$ sudo mount /dev/sdb1 /media/sdb1
```

but up until we lost power while I was at work, it auto mounted when I plugged it in.

Any suggestions?

The drive still auto mounts just fine on my OSX laptop.

-Adam

---

### Post by chewearn on 2007-08-12
Try this:
Unmount the harddisk and unplug it.
Delete the directory /media/sdb1.
Plug back the harddisk.  Does it automount now?

---

