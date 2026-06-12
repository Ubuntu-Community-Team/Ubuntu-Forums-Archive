---
title: "Easy way to turn on/off wireless?"
date: 2005-06-15
forum: Hardware &amp; Laptops
---

### Post by hagan on 2005-06-15
Hi,
I am looking for an easy way to turn on / off my internal wireless networkcard in my IBM X40. Up to now I do Sytem -> Administration -> Networking -> enter password -> activate ath0. There has to be some easier way. I am thinking of a one buton approach. Does anyone have a good approach to this.

Thanks
Marcus

---

### Post by luca_linux on 2005-06-15
I'm using this script on my Asus M6N:
```

#!/bin/bash

if `/sbin/ifconfig eth1 |grep -q UP`; then
    /sbin/ifdown eth1
    echo 0 > /proc/acpi/asus/wled || \
    logger -t acpid "Unable to bring down wireless"
else
    /sbin/ifup eth1
    echo 1 > /proc/acpi/asus/wled || \
    logger -t acpid "Unable to bring up wireless"
fi

```
It's related to acpi events...

---

