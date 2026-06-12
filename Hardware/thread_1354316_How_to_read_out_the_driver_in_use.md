---
title: "How to read out the driver in use?"
date: 2009-12-13
forum: Hardware
---

### Post by shade5 on 2009-12-13
hi,
I want to read out which Wifi driver I am using. I know it is the Broadcom STA wireless driver but I need to know the exact name to add it to /etc/network/interfaces.

Thanks.

---

### Post by IcarusR on 2009-12-14
Why do you want to do this? 
As far as I know you should not need to put the network module (driver) name in /etc/network/interfaces

This is my /etc/network/interfaces

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
```


There is no mention of my wifi interface

---

