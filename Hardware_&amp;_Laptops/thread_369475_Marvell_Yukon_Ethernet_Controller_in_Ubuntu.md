---
title: "Marvell Yukon Ethernet Controller in Ubuntu"
date: 2007-02-24
forum: Hardware &amp; Laptops
---

### Post by poulas on 2007-02-24
Hello,
I have bought ASUS Z84J and on board it has Marvell Yukon Chipset based Ethernet Controller which needs driver to install. For Windows there is driver, but for Ubunt no. Maybe somebody have the same problem and can help me? I can't access the internet without this driver for this LAN card. :(

---

### Post by Daveth on 2007-02-24
have a look at:

[http://www.marvell.com/drivers/](http://www.marvell.com/drivers/)

as they do their own Yukon linux drivers.
May help.

---

### Post by cocoia on 2007-02-25
Kernels from 2.6.18 and up have the sky2 driver, which is a gigabit driver for the Yukon adapter.
So, you could wait for a new kernel release / dist. upgrade or build one yourself, which I am struggling with right now

---

### Post by poulas on 2007-02-25
I have written to Marvell, but they haven't answered to me yet. Later I have downloaded Yukon Linux **Driver Install Package** (Linux Kernel 2.4.20 & Higher,  1/24/07, 10.0.4.3 (install_v10.0.4.3.tar.bz2)) and tried to install it, but there was error:

72: Syntax error: "(" unexpected

Maybe I tried wrong driver to install?  Or everything what I can do it only wait a new driver from Marvell?

---

### Post by Daveth on 2007-02-25
the "installing from Source" section of :

[http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)

is what you should follow. You "tar" that file from Marvell- there should be a readme or somesuch there which might give more info. I have never compiled from source myself, hence pointing you to the guide.

---

