---
title: "hp elitebook 8730w"
date: 2009-05-07
forum: Hardware
---

### Post by xender69 on 2009-05-07
Hi,

Just installed ubuntu 9.0.4 on the hp elitebook 8730w and was wanting to enable the extra visual effects so that I can use AWN but I can't seem to enable it.

I'm pretty sure it has to do with my graphics driver but can't seem to find a driver out there for the ati mobility firegl v5725.

any help would be really appreciated.

---

### Post by sharpone on 2009-05-23
The latest fglrx drivers from ati work fine. Follow the instructions here ([http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)) if you want to install the latest, otherwise install the ones from the 'restricted driver list'.

After you install, you may notice upon reboot that your screen goes completely blank. Boot into rescue mode, drop to a root shell and run
```
aticonfig --acpi-services=off
``` and reboot. This should fix the blank screen issue.

I still have an issue where I can't get the laptop to auto poweroff, I think it might be due to disabling the acpi stuff, but at least the fglrx drivers work now :0

The opensource ati drivers do not support the V5725 FireGL card for 3d, so fglrx is your only option to utilize the card.

---

### Post by xender69 on 2009-06-15
> **sharpone said:**
> The latest fglrx drivers from ati work fine. Follow the instructions here ([http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)) if you want to install the latest, otherwise install the ones from the 'restricted driver list'.

After you install, you may notice upon reboot that your screen goes completely blank. Boot into rescue mode, drop to a root shell and run
```
aticonfig --acpi-services=off
``` and reboot. This should fix the blank screen issue.

I still have an issue where I can't get the laptop to auto poweroff, I think it might be due to disabling the acpi stuff, but at least the fglrx drivers work now :0

The opensource ati drivers do not support the V5725 FireGL card for 3d, so fglrx is your only option to utilize the card.

Hi,
Thanks forthe advice but can I can't seem to get into rescue mode using the live CD, how do I get into rescue move so that I can try your suggestion?
Thanks.

---

