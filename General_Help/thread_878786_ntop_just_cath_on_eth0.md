---
title: "ntop just cath on eth0"
date: 2008-08-03
forum: General Help
---

### Post by dapim on 2008-08-03
how do i put for eth1 ???
can't file the conf file in /etc/ntop

---

### Post by alej0 on 2008-08-12
Hi

To change the interface you have to change INTERFACES in 

/var/lib/ntop/init.cfg 

```

USER="ntop"
INTERFACES="eth1"

```

thats all.

---

