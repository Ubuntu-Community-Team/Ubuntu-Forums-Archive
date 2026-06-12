---
title: "Not detected: SONY CDROM CRX880A on mobile IDE controller"
date: 2007-07-11
forum: Hardware &amp; Laptops
---

### Post by jjfraney on 2007-07-11
This cdrom was accessible during the install, but now it isn't detected.  Now, after booting into multi-user mode and successful access of other hardware on the laptop (apci, wireless), inserting a new cd into the cdrom does not activate automount, and eject command gives a failure of being unable to open device.

System is a Dell Latitude laptop, D830, intel chipset through and through.

The cdrom does not show up in the 'device manager' under Mobile IDE Controller.   Windows device manager can see the cdrom on the controller. 

This is lspci output wrt the controller:
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)

How may I proceed?   I've searched ubuntu forum for the cdrom model and the controller model.  Nobody has has had (and solved) this same problem.

Regards,
John

---

