---
title: "Best opensource driver for ati."
date: 2010-03-31
forum: Hardware
---

### Post by blackbird307 on 2010-03-31
I am currently using a 5770, but the problem is the drivers ati provided aren't really good. Does anyone know of open source drivers?

Also im fairly new to linux/ubuntu. :D

---

### Post by Dayofswords on 2010-03-31
i dont think the open source ones are any better

---

### Post by n0dix on 2010-03-31
If you install the driver recommend by Ubuntu in System > Administration > Hardware Drivers, you going well.

---

### Post by Mark Phelps on 2010-04-01
> **blackbird307 said:**
> I am currently using a 5770, but the problem is the drivers ati provided aren't really good. Does anyone know of open source drivers?

The open source drivers are installed by default if you don't install the ATI-specific restricted drivers.

If you want to remove the ATI drivers, use the instructions in the link below:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

Do not bother with the xorg.conf stuff. Just reboot after driver removal and Ubuntu should automatically install the open source drivers for you.

However, you will get only basic functions with these drivers.  No CCC will be provided.

---

