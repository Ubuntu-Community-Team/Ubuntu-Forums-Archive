---
title: "Severe problems following distro upgrade"
date: 2009-05-19
forum: Installation &amp; Upgrades
---

### Post by strm on 2009-05-19
I've run a distribution upgrade (8.04 -> 8.10) on two machines in my lab. One had a fresh install of 8.04 and upgraded without problems. The 2nd machine had been in use for about 6 months running 8.04 without problems. I upgraded using the usual command *update-manager -d*.

Since the upgrade the machine has become extremely unresponsive taking several minutes to boot up. Once the Gnome Display Manager starts, logging in takes another 3-5 minutes after typing in my password. After logging in, running any command requiring superuser privileges also takes a long time.

The machine does not get an IP after booting up anymore (despite having no issues prior to update), it calls itself "localhost.localdomain" despite having a name and being on a domain.

Dropping to a text first terminal (ctrl+alt+f[1-6]) and attempting to login also takes a significant amount of time. Sometimes, dropping to a terminal causes the keyboard to not work.

During the boot process the following things fail:
```

binding to YP server ...
starting hardware abstraction layer hald ...

```

Failure to bind the yellow pages (NIS) can probably be attributed to the machine's lack of IP address, I suspect the rest of the problems are due to the failure of HALD.

Any tips would be appreciated, I will attempt to post any logs I can dig up from the machine. Thanks.

---

