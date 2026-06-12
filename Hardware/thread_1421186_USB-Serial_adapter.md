---
title: "USB-Serial adapter"
date: 2010-03-03
forum: Hardware
---

### Post by K8JWT on 2010-03-03
How can I tell if my USB to serial adapter is working properly in Ubuntu 9.10?

---

### Post by iponeverything on 2010-03-04
> **K8JWT said:**
> How can I tell if my USB to serial adapter is working properly in Ubuntu 9.10?

1) try it

2) open a terminal and run ```
sudo tail -f /var/log/messages
``` and plug in the adapter.

---

