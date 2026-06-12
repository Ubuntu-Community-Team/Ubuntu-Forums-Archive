---
title: "fglrx; default powerstate setting..."
date: 2006-11-16
forum: Hardware &amp; Laptops
---

### Post by hardyn on 2006-11-16
the following xorg.conf setting for the fglrx driver is not implemented in the current driver (8.30.3)

Option "PowerState" "#"  (allows me to crack back the performance of the video)

but the command line switch does work:

aticonfig --set-powerstate=#

how / where would somebody locate such a command to force a default power state upon boot-up?

thanks.

---

