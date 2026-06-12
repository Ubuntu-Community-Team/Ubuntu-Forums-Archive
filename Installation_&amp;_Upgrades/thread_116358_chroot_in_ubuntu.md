---
title: "chroot in ubuntu"
date: 2006-01-12
forum: Installation &amp; Upgrades
---

### Post by 0x001A4 on 2006-01-12
I dont know if this is the right place to ask this. Its sort of an Ubuntu question and a Gentoo question in one.

I am in mid process of a Gentoo install through Ubuntu and the last step before I go into the Gentoo environment to finish it off is to chroot into Gentoo. I'm not sure how to do this from Ubuntu.

When I type
```

$ sudo chroot /mnt/gentoo /bin/bash

```
It gives me this error:
```

chroot: cannot run command `/bin/bash': Exec format error

```

Does anyone know how I can accomplish this?

SOLVED - I am going from 32bit Ubuntu to 64bit Gentoo. I need to chroot from a 64bit environment for it to work :)

---

