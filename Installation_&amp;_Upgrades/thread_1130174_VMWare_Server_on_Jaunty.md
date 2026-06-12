---
title: "VMWare Server on Jaunty"
date: 2009-04-19
forum: Installation &amp; Upgrades
---

### Post by ssiegler on 2009-04-19
My VMWare server seems to be working on upgrade from 8.10 to 9.04
by a new install (using the same base) did not

The trick is to regrab all the updated bits:

Using this as a template: [http://geekzine.org/2008/11/20/install-vmware-server-on-ubuntu-intrepid-810/](http://geekzine.org/2008/11/20/install-vmware-server-on-ubuntu-intrepid-810/)

Grab the latest requirements:
apt-get install linux-source-2.6.28 linux-libc-dev xinetd

The latest VMware:
wget [http://download3.vmware.com/software/vmserver/VMware-server-1.0.9-156507.tar.gz](http://download3.vmware.com/software/vmserver/VMware-server-1.0.9-156507.tar.gz)

and the latest patch:
[http://www.insecure.ws/2008/10/20/vmware-specific-specific-55x-and-kernel-2627](http://www.insecure.ws/2008/10/20/vmware-specific-specific-55x-and-kernel-2627)

Stuart

---

