---
title: "How to use madwifi instead of madwifi-deprecated?"
date: 2006-07-01
forum: Hardware &amp; Laptops
---

### Post by A.Skwar on 2006-07-01
Hello!

I'm using kernel 2.6.15-25-686 on Dapper. This kernel ships both madwifi-deprecated (as madwifi, with ath_pci) and madwifi (as madwifi-ng, with new_ath_pci). 

What would I need to modify, so that madwifi is used instead of madwifi-deprecated?

Thanks,

Alexander

---

### Post by stanwebber on 2006-08-06
assuming this bug is ever fixed,

[https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/54619](https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/54619)

you would need to edit /etc/default/linux-restricted-modules-common to disable ath_pci (madwifi-old) in favor of new_ath_pci```
DISABLED_MODULES="ath_hal"
```
if you don't need any of the other modules disable them as well```
DISABLED_MODULES="ath_hal fc fglrx ltm nv"
```

---

