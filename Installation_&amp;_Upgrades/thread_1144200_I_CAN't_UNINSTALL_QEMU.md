---
title: "I CAN't UNINSTALL QEMU"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by yildiz.a on 2009-04-30
Hi, I installed "QEMU" using command line interface, - ./configure, make, make install - not from the Synaptic Package Manager. But now I want to fully remove it, but couldn't find a way. 

"sudo apt-get remove qemu" doesn't work. It says no application called qemu installed.

Thanks...

---

### Post by Partyboi2 on 2009-04-30
Hi, you normally uninstalled programs by entering the source directory and typing[FONT=monospace]
[/FONT]```
sudo make uninstall
```

---

