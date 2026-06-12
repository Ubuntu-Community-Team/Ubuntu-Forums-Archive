---
title: "Ubuntu Resolutions"
date: 2005-06-12
forum: Hardware &amp; Laptops
---

### Post by kdupuy9 on 2005-06-12
I Have Ubuntu 5.04 with a Sony CPD-100ES monitor, and with Ubuntu the resolution of the system is 640x480 instead of 1040x840 or something like that. I went to change the resolutions, but the only option was 640x480! How can I change the resolution?

---

### Post by bored2k on 2005-06-12
[QUOTE=kdupuy9]I Have Ubuntu 5.04 with a Sony CPD-100ES monitor, and with Ubuntu the resolution of the system is 640x480 instead of 1040x840 or something like that. I went to change the resolutions, but the only option was 640x480! How can I change the resolution?[/QUOTE]
 From your upper pannel try:
Applications > System tools > terminal
Run
```
sudo dpkg-reconfigure xserver-xorg
``` to select the correct resolutions (Eventually). After you're done, reboot and try to catch any difference.

---

