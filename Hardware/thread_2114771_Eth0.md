---
title: "Eth0"
date: 2013-02-11
forum: Hardware
---

### Post by kanjah on 2013-02-11
Hi guyz, i have a hp z800, running ubuntu server 12amg 64, with 2 on board NIC, the system seems to pick one and ignore the other, i have searched it in /etc/networks/interfaces, seems not to be there, ave searched also in /etc/udev/rules.d/70.persistent rule, also it not present, how do i go about this?

---

### Post by papibe on 2013-02-11
Hi kanjah.

Could you post the result of these commands?
```
lspci -nnk | grep -iA2 eth

sudo lshw -C network

```
Regards.

---

### Post by kanjah on 2013-02-11
thanks papibe, from the sudo lshw -C network, i found the other eth interface to be disabled, i enabled it and all is well, thank you again

---

