---
title: "VMware Workstation 6.5.0 issue on Ubuntu 9.10 beta"
date: 2009-10-16
forum: Installation &amp; Upgrades
---

### Post by kalyogi on 2009-10-16
Hi All,

I have installed VMware Workstation 6.5.0 and the installation was successful. 

When I tried to open application, it is asking to install/compile some modules, when I click install button then it gives error "Unable to build kernal module"

and the log file shows:

```
Oct 16 15:36:57.869: app| Log for VMware Workstation pid=5235 version=6.5.0 build=build-118166 option=Release
Oct 16 15:36:57.869: app| Host codepage=UTF-8 encoding=UTF-8
Oct 16 15:36:57.869: app| Logging to /tmp/vmware-root/setup-5235.log
Oct 16 15:36:59.152: app| Extracting the sources of the vmmon module.
Oct 16 15:36:59.168: app| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.31-14-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.1

```


Is someone having the solution?

Thanks in advance.

---

### Post by dabl on 2009-10-16
Yes.

[http://communities.vmware.com/thread/221724;jsessionid=BC3D091ABA48DA73B0F42DCAFAD7CEE7?tstart=75](http://communities.vmware.com/thread/221724;jsessionid=BC3D091ABA48DA73B0F42DCAFAD7CEE7?tstart=75)

:)

---

### Post by kalyogi on 2009-10-17
This article shows how to install VMWare Workstation version 6.5.2. But I have installed 6.5.0 version. 

Is there any solution for this version or I need to install new VMWare version?

Thanks in advance.

---

