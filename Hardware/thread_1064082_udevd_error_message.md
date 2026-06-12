---
title: "udevd error message"
date: 2009-02-08
forum: Hardware
---

### Post by FrostDust on 2009-02-08
I installed cdemu (helps you mount disc images) a while ago, and then uninstalled it. However, whenever I boot Ubuntu, a message appears saying something like "udevd[2825]: cdemu not found." I'm pretty sure this is because cdemu worked by installing a fake cd-rom drive, or something along those lines.

Reading the man page, udev seems to be in control of loading devices during the boot process. I looked around in /dev, but I couldn't find any "cdemu" file. I also checked synaptic, and nothing comes up for "cdemu" either.

If anyone has any advice on how to completely uninstall the program, or at least suppress the error message, I'd appreciate it.

---

