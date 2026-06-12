---
title: "16-bit pcmcia not working after upgrade to Edgy"
date: 2006-11-07
forum: Hardware &amp; Laptops
---

### Post by beatadalhagen on 2006-11-07
I recently updated my Dapper system to Edgy. Now it will not recognise 16-bit pcmcia cards. The kernel mentions "cs: warning: no high memory space available!" 'pccardctl status' shows that I have a 16-bit PC card inserted.

During the install the pcmcia-cs package was removed and the /etc/pcmcia directory is now empty. Previously I had to edit /etc/pcmcia/config.opts to adjust the interrupt list.

any ideas?

---

