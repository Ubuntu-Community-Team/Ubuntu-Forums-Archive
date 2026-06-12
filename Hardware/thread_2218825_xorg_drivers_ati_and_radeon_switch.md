---
title: "xorg drivers ati and radeon switch?"
date: 2014-04-22
forum: Hardware
---

### Post by jhay2 on 2014-04-22
hi , i found out that xorg-ati and xorg-radeon are two different drivers of xorg 
when i try to boot puppylinux on my ram , puppylinux has an ability to switch graphic drivers from ati to radeon or radeon to ati at first run
so i thought that this 2 drivers of x.org are different. 
and i want to test if it has a difference in performance. 

can i switch radeon to ati x.org drivers in ubuntu like puppylinux? if yes , how ? 

sorry for my bad english ..

---

### Post by Yellow Pasque on 2014-04-22
Are you talking about fglrx/Catalyst?

xorg-ati is not a different driver. It is just a wrapper that selects xorg-radeon for Radeon cards (or a different xorg driver, such as mach64, for older cards).

---

### Post by jhay2 on 2014-04-22
thanks for your reply .. 

but in puppylinux .. it has an option that i can choose what xorg driver should i use , the ati and radeon xorg drivers were seperated on the choices .. when i look on lsmod , radeon is loaded (if radeon was chosen) and ati is loaded when i chose ati ,


so i thought that these two are different driver

---

### Post by Yellow Pasque on 2014-04-22
> **jhay2 said:**
> so i thought that these two are different driver

No. xorg-ati is just a wrapper and not a different driver:
> 
This package provides the 'ati' driver for the AMD/ATI Mach64, Rage128,
Radeon, FireGL, FireMV, FirePro and FireStream series. [B]This driver is
actually a wrapper that loads one of the 'mach64', 'r128' or 'radeon'
sub-drivers depending on the hardware.[/B]

---

