---
title: "How to install HP LaserJet MFP130nw network printer?"
date: 2024-06-11
forum: Hardware
---

### Post by trancephorm on 2024-06-11
Network printer used to work with hp-lip drivers (but not the ones from Ubuntu repository), but you can only install USB, not the network printer. I don't know what I've didn't try by now, this is hell.

Anyone has the same trouble an found a solution?

---

### Post by Xian on 2024-06-12
Are you able to install the hplip-gui package?

$ sudo apt-get install hplip-gui


Then launch the hp-setup wizard to configure.

---

### Post by trancephorm on 2024-06-12
Yes, I've tried that with repository packages, network printers are losing connection, only USB printing is working (although I don't know if it works with repository packages - I'm sure it works with hplip drivers downloaded from HP website).

---

