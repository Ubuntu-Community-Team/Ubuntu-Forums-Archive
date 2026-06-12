---
title: "Wireless drivers?"
date: 2008-05-22
forum: Hardware
---

### Post by Caram on 2008-05-22
Ubuntu works with my network card right out of the box and I'm looking to have this for another Linux system. Network information shows ath_pci as my driver, I'm just not sure where it's located.

---

### Post by hal10000 on 2008-05-22
The kernel modules for your wireless card is located under
> 
/lib/modules/2.6.24.3/kernel/drivers/net/wireless/

Note: The version Number here (2.6.24.3) will probably differ on your system,
maybe 2.6.24-17-generic or something similar. 
The kernel-Version number of the currently running kernel can be obtained by

uname -r


In this directory you should find the module which is probably named ath_pci.ko
If you use the command [COLOR="Red"]modinfo ath_pci[/COLOR] you can find out some more info about this driver. With the command
[COLOR="Red"]lsmod | grep ath_pci[/COLOR] you can find out if it is already loaded and if it is not you can load it manually with the command
[COLOR="Red"]sudo modprobe ath_pci[/COLOR]

---

### Post by Caram on 2008-05-24
thanks :D

---

