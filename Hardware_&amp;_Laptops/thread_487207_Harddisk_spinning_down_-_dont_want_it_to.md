---
title: "Harddisk spinning down - dont want it to"
date: 2007-06-28
forum: Hardware &amp; Laptops
---

### Post by Orvil on 2007-06-28
Hi all.

I have an EPIA M1000 running feisty (xubuntu). It has a 2,5 inch harddisk, Seagate Momentus ST94811A.
I use the machine for a printer/file server and for P2P file sharing. 
The thing is, the harddisk keeps spinning down. I don't want it to.

How do I stop the harddisk from spinning down?

---

### Post by brettr on 2007-06-28
First i would check Power management settings, there might be something in there, if not, laptop-mode might be enabled and set to spin down the disk. check out this file to see if laptop mode is enabled

```
/etc/default/acpi-support
```

If it is you can configure it by going
```
/etc/laptop-mode/laptop-mode.conf
```

---

### Post by wieman01 on 2007-08-21
Do this:
> sudo gedit /etc/laptop-mode/laptop-mode.conf
Now set these values to '0':
> CONTROL_HD_IDLE_TIMEOUT=0
> BATT_HD_POWERMGMT=0

---

