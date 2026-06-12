---
title: "Help - Is is possible to downgrade the kernel in 9.04?"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by Alteranous on 2009-05-05
Hi,

Hopefully this makes sense, im still kind of new to linux:

I upgraded my ubuntu from 8.10 to 9.04 yesterday, however, the new kernel 2.6.28 seems to have issues with some hardware I need to use (Msp430 Jtag Programmer).  However, this hardware works flawlessly under ubuntu 8.10 with the 2.6.27 kernel.  Rather than reinstall Ubuntu 8.10, I was wondering if it is possible to install/downgrade the 2.6.27 kernel into ubuntu 9.04?
I tried searching for linux-image in apt-get but I only found the 2.6.28 kernel.

Thanks
Anthony

---

### Post by snowpine on 2009-05-05
The old kernel should be in your Grub boot menu when you first turn on the computer.

---

