---
title: "Loading a module at startup with options specified in /etc/modprobe.conf"
date: 2005-03-17
forum: Hardware &amp; Laptops
---

### Post by Pierre Mazoyer on 2005-03-17
I have a module "pcan" that is loaded with options specified in /etc/modprobe.conf. These options consist actually of another command that creates additional devices.

My /etc/modprobe.conf file contains :

install pcan /sbin/modprobe --ignore-install pcan; /usr/local/bin/pcan_make_devices 2

If I use "modprobe pcan", everything works well: my module is loaded and my devices are created.

But if I add a line with "pcan" to /etc/modules, only the loading happens at startup, not the device creation.

It seems that modprobe (called by module-init-tools) ignores options in /etc/modprobe.conf at startup!  :( 

Does anybody have an idea about this issue?

Thank you.

---

