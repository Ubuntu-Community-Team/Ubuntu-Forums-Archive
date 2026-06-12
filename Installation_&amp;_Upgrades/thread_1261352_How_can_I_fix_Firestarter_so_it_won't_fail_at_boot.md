---
title: "How can I fix Firestarter so it won't fail at boot?"
date: 2009-09-08
forum: Installation &amp; Upgrades
---

### Post by Ubu4moi on 2009-09-08
I installed Firestarter on Ubuntu Ultimate Edition 64bit and it fails during boot. Is there anything I have to configure?
 Also, how can I allow or not allow programs to connect to the Internet? Is there a more complete interface for newbee's?

---

### Post by imbjr on 2009-09-08
Firestarter is merely the interface to the in-built firewall, so it did its job when you started it, changed what you wanted and quitted.

Everytime you reboot, the rules that you set via firestarter are re-instated without actually needing to run the program.

Edit: as for stopping particular programs, that is not supported by most builds of iptables (the in-built firewall), which is a shame as that was a feature of MS firewalls that was useful.

---

### Post by Ubu4moi on 2009-09-08
Thanks. During boot it says that Firestarter fail to start, in red. Does it still run?

---

### Post by Penguin Guy on 2009-09-08
> **Ubu4moi said:**
> Thanks. During boot it says that Firestarter fail to start, in red. Does it still run?
Firestarter is not a firewall, it just sets up the firewall (a.k.a. it starts the fire). It only needs to be ran once and you're set for life.

---

