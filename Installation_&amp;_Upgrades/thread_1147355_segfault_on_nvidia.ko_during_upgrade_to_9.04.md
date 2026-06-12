---
title: "segfault on nvidia.ko during upgrade to 9.04"
date: 2009-05-03
forum: Installation &amp; Upgrades
---

### Post by prosonik on 2009-05-03
Hi!

During the upgrade process to 9.04(RC), my installation died leaving with a rather broken system. I have attached the output below. I haven't been able to finish the RC upgrade to get it up to full..

Setting up module-init-tools (3.7~pre9-2) ...
Running depmod for 2.6.22-14-generic...
WARNING: Couldn't find symtab and strtab in module /lib/modules/2.6.22-14-generic/kernel/drivers/video/nvidia.ko
Segmentation fault
dpkg: error processing module-init-tools (--configure):
 subprocess post-installation script returned error exit status 139
and then installation fails..

Now, to top it off, I don't even have the nvidia card installed anymore. On unrelated matter, it decided to die.. So I'm back to the stock integrated Intel. The board is a P5L-MX

I've tried all the apt-get commands I know. Is there anything I can do to get the upgrade working?

---

