---
title: "required files for compiling a new kernel driver?"
date: 2010-07-01
forum: Hardware
---

### Post by stevfletchcom on 2010-07-01
Could someone tell me what I need to install using apt-get so that I'll have the necessary kernel headers/files for compiling a network card driver against my current kernel?

I am running ubuntu 10.04 server edition and I need to get my Zonet ZEN3301E working, but it requires that I compile the driver against my kernel.  I am still not that familiar with compiling kernel modules but am hoping that I am just missing certain development files.

I have already installed a package called linux-headers-2.6.32-21-generic-pae but I would like to know if I am missing anything else?

Thanks

Steven F.

---

### Post by Yellow Pasque on 2010-07-02
Make sure you have build-essential package installed and you should be good.

---

