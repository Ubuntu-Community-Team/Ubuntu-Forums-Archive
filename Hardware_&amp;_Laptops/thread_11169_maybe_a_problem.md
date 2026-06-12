---
title: "maybe a problem"
date: 2005-01-14
forum: Hardware &amp; Laptops
---

### Post by gpredrag on 2005-01-14
My Ubuntu is actually working perfectly, but I am receiving error messages during boot time while starting PCI hot plug subsitem. Two modules pciehp and shpchp cannot be loaded. Modinfo tells me that those two modules are related to PCI hot plug controlers. Machine I am working on is beige box P4 with Intel chipset, not some dedicated server machine, I don't even suppose it supports hot plug.
Can I safely ignore this or are those two modules important for this new (for me) 2.6 sysfs udef thing. Am I losing some funtionality?
I work mostly with Debian Woody, and I wonder is handling of modules different in Ubuntu than in Woody. For instance, I commented out IPv6 in /etc/aliases, run update-modules, still lsmod shows me IPv6 module loaded. I have instaled kernel(linux)-package 686 from ubuntu - is IPv6 built in kernel?
Pointing me to some HOWTO (udev,sysfs, Ubuntu+modules) would be helpfull.

---

### Post by nemin on 2005-01-14
[QUOTE=gpredrag]My Ubuntu is actually working perfectly, but I am receiving error messages during boot time while starting PCI hot plug subsitem. [/QUOTE]
[http://www.ubuntulinux.org/wiki/FrequentlyAskedQuestions#booterrors](http://www.ubuntulinux.org/wiki/FrequentlyAskedQuestions#booterrors)

---

