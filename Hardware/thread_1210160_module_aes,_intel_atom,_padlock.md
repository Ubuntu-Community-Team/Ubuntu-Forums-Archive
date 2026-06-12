---
title: "module aes, intel atom, padlock"
date: 2009-07-11
forum: Hardware
---

### Post by metalfan_ on 2009-07-11
Hi,

just wanted to try ecryptfs, but trying to load the aes module results in:

```

sudo modprobe aes
WARNING: Error inserting padlock_aes (/lib/modules/2.6.27-11-generic/kernel/drivers/crypto/padlock-aes.ko): No such device

```


Any ideas?


SOLUTION:
i tend to find the right google search term after i posted the initial question...

/etc/modprobe.d/blacklist
blacklist padlock_aes

---

