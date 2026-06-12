---
title: "resetting your ip?"
date: 2008-07-11
forum: General Help
---

### Post by WinterMadness on 2008-07-11
how would i go about doing this?

---

### Post by iaculallad on 2008-07-11
> **WinterMadness said:**
> how would i go about doing this?

If you're speaking on resetting DHCP assigned IP addresses:

:Release
```
sudo dhclient -r
```
:Obtain:
```
sudo dhclient
```
:Restart network daemon
```
sudo /etc/init.d/networking restart
```

---

