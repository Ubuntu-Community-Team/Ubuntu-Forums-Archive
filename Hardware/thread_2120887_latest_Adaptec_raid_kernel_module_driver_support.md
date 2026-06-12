---
title: "latest Adaptec raid kernel module driver support"
date: 2013-02-27
forum: Hardware
---

### Post by burgundy on 2013-02-27
Recently I attempted to use both of the binary packages provided by Adaptec on their website:
[http://www.adaptec.com/en-us/downloads/ubuntu/ubuntu_12lts/productid=sas-7805&dn=adaptec+raid+7805.html](http://www.adaptec.com/en-us/downloads/ubuntu/ubuntu_12lts/productid=sas-7805&dn=adaptec+raid+7805.html)

Neither .deb package would load against the kernel the system was using (3.2.0-38-generic).

As a result I began to explore their source RPMs.  Not surprisingly these RPMs contained source code and Makefiles setup for a Red Hat environment.

From $/usr/src/aacraid-1.2.1.29900 I attempted to use their Makefile, but it failed to find DKMS_KERNEL_SOURCE_DIR and DKMS_SUBDIRS.

After a little more digging into how to compile a kernel module on a current Ubuntu system I found that

DKMS_KERNEL_SOURCE_DIR=/lib/modules/3.2.0-32-generic/build
DKMS_SUBDIRS=$(PWD)

filled in the missing parameters this Red Hat Makefile was expecting.

From there everything went much more smoothly.  $insmod aacraid.ko was happy and Ubuntu found the RAID controller and accessed/mounted my hard drives.

Today was a good day.

---

