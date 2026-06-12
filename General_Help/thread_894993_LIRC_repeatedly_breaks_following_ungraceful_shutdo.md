---
title: "LIRC repeatedly breaks following ungraceful shutdown"
date: 2008-08-19
forum: General Help
---

### Post by kaput on 2008-08-19
I'm running 8.04 with a Hauppauge PVR-150 and for the second time, a power outage has broken LIRC (0.8.3~pre1-0ubuntu7.1). Both times, the exact same issue occurred following boot: /dev/lirc0 fails to be created. Despite reading dozens of bug reports and forum threads, the only way I managed to fix the issue (not much of a fix) was by re-installing.

I've changed no config files. Everything remains as it was following the initial mythbuntu-control-centre configuration. Both drivers as defined by 'hardware.conf' are loaded (lirc_dev/lirc_i2c).

Anybody have any ideas? I've attached some necessary info.

---

