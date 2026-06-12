---
title: "How to mount partition as HOME after clean install?"
date: 2009-05-12
forum: Installation &amp; Upgrades
---

### Post by ToshibaLaptoplinux on 2009-05-12
Against my better instincts I "upgraded" to Jaunty and as a result the problems were so many that my laptop essentially was not usable. I decided to do a clean install.

My question is this. I had my HOME directory on a separate partition and did a clean install of Jaunty on the partition previously used for Hardy/Ibex. Now Jaunty only sees that partition as a "disk". How can I mount this as my HOME directory from now on. I already changed my HOME location to that disk in my Users and Groups control panel but that only does exactly what it says.

Thanks for the help.

---

### Post by Lampi on 2009-05-12
you can mount this home partition using /etc/fstab

Let's say this home partition is sda3, sitting on a ext3 formatted filesystem, the entry in fstab could look like this:

```
/dev/sda3 /home ext3 defaults,errors=remount-ro 0 1
```

Maybe you should first move the content of the current home directory in use, so you can kind of combine the old stuff with the new stuff

---

