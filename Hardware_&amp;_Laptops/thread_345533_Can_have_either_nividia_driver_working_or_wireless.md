---
title: "Can have either nividia driver working or wireless working, but not both."
date: 2007-01-24
forum: Hardware &amp; Laptops
---

### Post by Yerknutz on 2007-01-24
I'm really curious what is different about Edgy 6.10 then Dapper 6.06.  In 6.06 I could have the latest nvidia driver installed as well as having my Intel Pro Wireless 3945abg card working perfectly.  With Edgy, I can only have one or the other. Here is what I have figured out:

Clean install of Edgy 6.10. Video works using the standard "nv" driver in xorg.conf and the wireless radio is not active so network manager does not detect eth1 (wireless card).

Newest nvidia driver is installed, xorg.conf is changed from "nv" to "nvidia".  Edgy starts fine, gives the Nvidia splash screen indicating that the new driver is working properly. Wireless radio still not active.

linux-restricted-modules for my kernel are installed, madwifi is included and I am assuming this is what is activating my wireless radio.  It also installed nvidia-kernel-common.  Result - wireless radio is active and can set network settings and utilize my wireless connection.  Upon reboot, X crashes. The only way for me to get back to a graphical interface is to change the "nvidia" back to "nv" and then /etc/init.d/gdm restart

I can only guess that the nvidia-kernel-common that I am forced to install with the "linux-restricted-modules" is what is breaking X.  I am therefore stuck with my video drivers working correctly but with no wireless or with working wireless but my video drivers not working correctly.

Is there a way for me to get the modules that are in the linux-restricted-modules seperately, or to get the nvidia-kernel-common to not break X?

---

### Post by gmc1200 on 2007-03-21
Hi, i'm experiencing this same problem.  Does anyone know the solution?

---

