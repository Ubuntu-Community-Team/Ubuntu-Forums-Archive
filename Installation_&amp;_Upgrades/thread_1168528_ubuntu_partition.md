---
title: "ubuntu partition"
date: 2009-05-24
forum: Installation &amp; Upgrades
---

### Post by salim.madni on 2009-05-24
i create originaly
/ swap
/ root
/var/opt/axigen

later i discover something i did wrong

- if we create partition as /var/opt/axigen, so everything installed axigen here
- but if we take backup under /var/opt/backup
- so will it be part of /root directory or part of /var/opt/axigen
- since we are mounting /var/opt/axigen just to make sure have seperate entire partition of axigen, where backup folder is not part of axigen folders 
- so shell we create partition like
a) /var/opt/

- u suggest if we make mount partition as /var/opt, in this as sub directory /axigen and /backup both can come under single partition
- our purpose target is to put everything inside the /var/opt related to axigen

---

