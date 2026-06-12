---
title: "upgrade from 8.10  to 9.04"
date: 2009-09-03
forum: Installation &amp; Upgrades
---

### Post by lesterness on 2009-09-03
I have Xubuntu 8.10 and Windows XP, dual boot, on my computer.  I would like to upgrade from 8.10 to 9.04 via the Internet.  How?  What are the commands?  Alternatively, I have a Ubuntu 9.04 CD.  How could I  install it on top of the 8.10 partition and replace it?  I don't want to end up with three partitions.

Thanks.

---

### Post by miklcct on 2009-09-03
You can do graphical upgrade by launching the update manager in your system. For command-line upgrade:

```

sudo do-release-upgrade

```

---

### Post by Partyboi2 on 2009-09-03
> **lesterness said:**
> I have Xubuntu 8.10 and Windows XP, dual boot, on my computer.  I would like to upgrade from 8.10 to 9.04 via the Internet.  How?  What are the commands?  Alternatively, I have a Ubuntu 9.04 CD.  How could I  install it on top of the 8.10 partition and replace it?  I don't want to end up with three partitions.

Thanks.
Open a terminal and type
```
sudo update-manager -d
``` this should give you the option to upgrade to 9.04. 
If you want to upgrade using a cd you will need to use the alternate cd as the live cd does not support this function.

---

