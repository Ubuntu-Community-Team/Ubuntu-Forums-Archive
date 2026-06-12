---
title: "CPU frequency does not change on ASUS UL20A"
date: 2010-08-22
forum: Hardware
---

### Post by ksmigrod on 2010-08-22
On Ubuntu 10.4 and 10.4.1 x86_32 CPU frequency does not change.
According to cpu frequency panel applet, this system does not support frequency changing (which is false, frequency changes under Win7).

Laptop: Asus UL20A-2X055V 1,2 GHz CPU, 4GB RAM
Kernel options in /etc/defaults/grub:

```
GRUB_CMDLINE_LINUX_DEFAULT="acpi_backlight=vendor quiet splash"
```

I've already tried using generic and generic-pae without success.
For your information, same problem shows up if I use Fedora 13 live CD.

---

### Post by jongkind on 2010-08-22
Not sure whether it will work in Ubuntu, but you can try to edit the rc.local file and add: 
*cpufreq-set -g ondemand*

The last line in rc.local must be:
*exit 0*

The rc.local file can be found in the /etc folder.

---

