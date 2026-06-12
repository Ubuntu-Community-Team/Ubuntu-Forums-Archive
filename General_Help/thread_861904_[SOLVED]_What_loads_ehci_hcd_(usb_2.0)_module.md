---
title: "[SOLVED] What loads ehci_hcd (usb 2.0) module?"
date: 2008-07-17
forum: General Help
---

### Post by mempman on 2008-07-17
During the boot process what exactly is responsible for loading the ehci_hcd module.  Is it modprobe, then y cannot I find any references at all in /etc/modprobe.d/ folder for ehci_hcd?

---

### Post by mempman on 2008-07-17
Never mind...found answer in modprobe manpage...

> 
 modprobe looks in the module directory /lib/modules/&#8216;uname -r&#8216; for all the modules and other files,  except  for  the  optional  /etc/mod&#8208;
       probe.conf configuration file and /etc/modprobe.d directory (see modprobe.conf(5)).  All files in the /etc/modprobe.d/arch/ directory are ignored.



---

