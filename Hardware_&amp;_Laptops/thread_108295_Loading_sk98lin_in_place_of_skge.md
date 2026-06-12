---
title: "Loading sk98lin in place of skge"
date: 2005-12-25
forum: Hardware &amp; Laptops
---

### Post by gsdefender on 2005-12-25
I have been experiencing several incompabilities using skge in place of sk98lin to manage my Marvell Yukon Gigabit Ethernet board; while in Slamd64 and Gentoo I could default loading sk98lin in place of skge, I could not figure out how to do that in Ubuntu. I tried putting 

```
sk98lin
``` 

in /etc/modules, and 

```
alias eth0 sk98lin
```

in /etc/modules.d/aliases

but nothing happened. It seems to me that module loading is handled somewhat strangely - as to me - by the hotplug subsystem, and I don't know how to force a change. I would be really glad for any help.

---

