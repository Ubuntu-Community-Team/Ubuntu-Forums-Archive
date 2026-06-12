---
title: "restricted drivers manager + new nvidia driver?"
date: 2007-12-21
forum: Hardware &amp; Laptops
---

### Post by jimmy the saint on 2007-12-21
The new stable Nvidia driver fixes a lot of issues with thinkpad *61s, including brightness issues.  I have the driver that comes standard with Gutsy through the restricted driver manager.  Will the Ubuntu team be enabling the new driver through the restricted drivers manager does this only happen with new OS releases? 
 I have heard that installing video drivers manually is not for the faint of heart, or for newbies like me, but the fixes for my laptop are numerous and I would love to benefit from them.

---

### Post by igknighted on 2007-12-21
> **jimmy the saint said:**
> The new stable Nvidia driver fixes a lot of issues with thinkpad *61s, including brightness issues.  I have the driver that comes standard with Gutsy through the restricted driver manager.  Will the Ubuntu team be enabling the new driver through the restricted drivers manager does this only happen with new OS releases? 
 I have heard that installing video drivers manually is not for the faint of heart, or for newbies like me, but the fixes for my laptop are numerous and I would love to benefit from them.

If you really don't want to get too involved, download Envy (search for it on google, I forget the website).  It has an option to "manually install", and it should download the latest driver from nvidia.

If you want to do it yourself, it's actually quite easy.  Simply install the kernel-headers package and the build-essential package, download the driver from nvidia's site, then hit ctrl-alt-f1 to get to a text terminal.  Type 'sudo /etc/init.d/gdm stop' to kill the xserver.  Then type ```
sudo apt-get remove --purge nvidia-glx-new
```
now cd to the directory of the driver and type:
```
sudo sh NVID*
```

Just hit enter (ok) to everything and let it do it's thing.  When it is done, reboot and the new driver should be working.

---

### Post by jimmy the saint on 2007-12-21
Every tutorial I have seen about manually installing nvidia drivers is well over a page long and includes steps like disabling gdm.  I will check out envy again, but i have a few other restricted drivers and I would probably have to go through and install them manually as well since envy requires you to get rid of the restricted drivers manager.  It would be easier if the new driver just appeared in the manager.

---

