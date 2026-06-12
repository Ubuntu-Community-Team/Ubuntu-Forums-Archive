---
title: "Problem with serial port on ThinkPad T22"
date: 2008-02-12
forum: Hardware &amp; Laptops
---

### Post by VOVEEE on 2008-02-12
Hi !
I'm having a problem with my laptop IBM ThinkPad T22. I've tried several dists (Ubuntu, Fedora) but I can't make my serial port working. At the moment  I use Ubuntu 6.10 (Edgy) and gtkterm and minicom but there is no result. When I type dmesg | grep serial the following appears:

[17179596.448000] piix4_smbus 0000:00:07.3: IBM Laptop detected; this module may corrupt your serial eeprom! Refusing to load module!


The result of dmesg| grep tty is :

[17179596.448000] piix4_smbus 0000:00:07.3: IBM Laptop detected; this module may corrupt your serial eeprom! Refusing to load module!


In Windows I have no problems so the problem is not in the hardware. Does anyone know how to fix this? 
May be the problem is that Ubuntu doesn't load some module.

Thanks in advance.

---

### Post by VOVEEE on 2008-02-15
Isn´t there a person with a similar problem ?

:confused::confused::confused:

---

