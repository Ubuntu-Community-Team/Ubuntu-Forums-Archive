---
title: "VMware Server 2 install"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by huntz on 2009-11-02
VMware Server 2 installation script is not working on 9.10

Luckily, someone has found a fix (you have to patch some drivers compiled during the installation for kernel 2.6.3x compatibility)

[http://communities.vmware.com/thread/215985](http://communities.vmware.com/thread/215985)

From this blog [http://radu.cotescu.com/2009/10/30/how-to-install-vmware-server-2-0-x-on-ubuntu-9-10-karmic-koala/](http://radu.cotescu.com/2009/10/30/how-to-install-vmware-server-2-0-x-on-ubuntu-9-10-karmic-koala/) you can also download a bash script with all the patches automated.

According to the blog, this workaround works for 32bit and 64bit.

PS: tested with 32bit VMware-server-2.0.2-203138.i386

---

