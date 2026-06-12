---
title: "lmsensors and MSI K8N Neo2"
date: 2005-09-08
forum: Hardware &amp; Laptops
---

### Post by yesplease on 2005-09-08
Will lm-sensors work with nforce3 chipset? Does anyone have a configuration  file or method for the MSI K8N Neo2 plat? I ask this because this motherboard is quite common and because it would be dangerous to enter the wrong range of cpu voltages and temps. (CPU voltage is already regulated by powernowd) Oh, and I use 32 bit Hoary Hedgehog 504.


There is a howto for lm-sensors and nforce2 chipsets

[http://ubuntuforums.org/showthread.php?t=2780&page=2&pp=10&highlight=lm-sensors](http://ubuntuforums.org/showthread.php?t=2780&page=2&pp=10&highlight=lm-sensors)

but perhaps lm-sensors is more uptodate now.


Edit: lm-sensors has a home-page: [http://www.lm-sensors.nu](http://www.lm-sensors.nu) You see that when you search in synaptic (offically supported packages). The homepage says that nforce3 is supported, but you need to install i2c-nforce2 version 2.9.0 first. Synaptic does not provide ic2, but the description of lm-sensors says it is in kernel 2.6 (that must be version 2.8.0). So, I did not find a  way to install version 2.9.0 before lm-sensors, but it needs a version of lm-sensors that is not newbie-proof anyway.

---

