---
title: "Install errors.... how do I fix??"
date: 2008-01-03
forum: Hardware &amp; Laptops
---

### Post by whos2know on 2008-01-03
hi,

I get the following errors every time I install something.  I know it's from installing my printer ( that still don't work ) but... I would like to have these errors fixed.... any help would be great!! Thank you!!

[PHP]E: cupsys: subprocess post-installation script returned error exit status 2
E: cups-pdf: dependency problems - leaving unconfigured
E: hplip: dependency problems - leaving unconfigured
E: bluez-cups: dependency problems - leaving unconfigured
E: cupsys-driver-gutenprint: dependency problems - leaving unconfigured
E: hal-cups-utils: dependency problems - leaving unconfigured
E: hplip-gui: dependency problems - leaving unconfigured

[/PHP]

---

### Post by pietjanjaap on 2008-01-03
Example of wrong install of vmware.
Alway's errors with install of programs.
**See the directories with you can clean out, only look for your program name.**


Problem is:
/var/cache/apt/archives/vmware-player_1.0.2-2_i386.deb: subprocess new pre-removal script returned error exit status 1.
And map     /var/lib/dpkg/info

vmware problem, all deb removed in cache(map) en alle pre install(inst) van vmware remove.


** /var/cache/apt/archives** all deb remove.
And here **/var/lib/dpkg/info** all inst(install) removed, only removed of a program that has problems.

Check if you have fived it.

---

### Post by whos2know on 2008-01-09
i'm sorry for the late reply... I want to thank you for your help and all other help you can give... i'm not quite understanding what you are telling me.... i just started to use Ubuntu about 3 months ago.... can you explain more.... thank you very very much!!

Bobby

---

### Post by whos2know on 2008-02-08
fixed... i cloned and reinstalled ubuntu!!  thank you!!

---

