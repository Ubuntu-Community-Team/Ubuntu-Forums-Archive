---
title: "Intel(R) PRO/1000 driver question !~"
date: 2009-09-26
forum: Installation &amp; Upgrades
---

### Post by moneybox123 on 2009-09-26
**[COLOR=blue]Intel(R) PRO/1000 EB Network Connection[/COLOR]**
 
Does anyone know this netcard drivers ,I can not driver it :(

---

### Post by tommcd on 2009-09-26
Can you post the output of:
```
lspci
```
This will list your ethernet card near the end of the output. Post that here.
The **ethtool** command is included in Ubuntu, at least I have it on my system anyway. To see what driver your ethernet card uses, run:
```
ethtool -i eth0
```
If your ethernet device is not eth0, change that as necessary (eth1, eth2, etc).
Assuming ethtool reports a driver, then run **lsmod** in the terminal to see if the driver is listed there.
Can you post the results of: lspci, ethtool -i eth0, and lsmod here.

EDIT: Also post the output of: **ifconfig**.

---

