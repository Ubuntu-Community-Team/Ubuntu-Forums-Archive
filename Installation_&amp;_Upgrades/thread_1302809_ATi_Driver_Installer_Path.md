---
title: "ATi Driver Installer Path"
date: 2009-10-27
forum: Installation &amp; Upgrades
---

### Post by rwarner67 on 2009-10-27
Hello all. I have a HP 1155se with an ATI Radeon 3200 graphics card. I am attempting to use the ati-driver-installer for the -9-10-x86.x86_64.run release. 
 
My questions is what is the installation path for the driver? I do not see anything noted in the literature from ATi.
 
Many thanks in advance. 
 
Regardless of the work. Ubuntu is a learning experience and well worth the effort.

---

### Post by martrn on 2009-10-27
The install path for your ATI kernel module (aka driver) would be 

/lib/modules/2.6.xx-xx-generic/kernel/drivers/

where xx would indicate the kernel number you are currently running. you could find out after installing the kernel module by typeing the following at a terminal...

```
sudo find / *.ko | grep ati
```

---

### Post by rwarner67 on 2009-10-27
This box rocks!  Thanks for your assistance.   Problem solved!

---

