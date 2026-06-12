---
title: "Fan control on ROG Maximus Hero VII in 15.04"
date: 2015-04-25
forum: Hardware
---

### Post by DreamKing on 2015-04-25
Hi

In windows I have an app for my Asus ROG  Maximus Hero VII where I have 4 options for fan speed,
Silent, standard, fast and full.

But in 15.04 fans always run at full speed.

How would I get the same options as with the windows app?
Or just be able to set the cooling profile to silent? 

Thanks!

---

### Post by DreamKing on 2015-04-25
I ended up just configuring fan speed in the BIOS and then using lm-sensors to view fan speed.

However I needed to add "acpi_enforce_resources=lax" to grub boot options in /etc/default/grub ([http://askubuntu.com/questions/19486/how-do-i-add-a-kernel-boot-parameter](http://askubuntu.com/questions/19486/how-do-i-add-a-kernel-boot-parameter))

To get a better readout from sensors I used a custom config
([http://lists.lm-sensors.org/pipermail/lm-sensors/2014-November/042908.html](http://lists.lm-sensors.org/pipermail/lm-sensors/2014-November/042908.html))

---

