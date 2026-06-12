---
title: "install 3512 Sata Controler"
date: 2008-09-18
forum: Hardware
---

### Post by rascalli on 2008-09-18
I have bought an silicone Sata Controller 3512, wich I would like to use with just 1x Sata HDD

Ubuntu sees the controler , but does not see the HDD.

ANy idea's what I need to do from here ?

OS : Ubuntu server 6.06.2 LTS
Kernel : 2.6.15.26-server

---

### Post by prshah on 2008-09-18
> **rascalli said:**
> Ubuntu sees the controler , but does not see the HDD.
OS : Ubuntu server 6.06.2 LTS
Kernel : 2.6.15.26-server

Prior to 8.04, ubuntu did not include "out-of-box" SATA drivers, which meant switching SATA to an IDE compatible mode in the BIOS until it was fully installed and upgraded. Unfortunately I don't know how to change the compatibility mode in an add-on card.

Can I suggest: Try the 8.04.1 CD, and if it still fails to see your hard disk drive, maybe we can troubleshoot further? (There's no need to complete the installation of 8.04.1, you can just try it as a test to see if your HDD is recognized or not.)

---

### Post by rascalli on 2008-09-19
will that also work with the controller ?

As I do not have a SATA slot on my MB , that's why I am going for a PCI Sata Controller , so I cannot plug the HDD onto the MB

---

### Post by prshah on 2008-09-19
> **rascalli said:**
> will that also work with the controller ?
As I do not have a SATA slot on my MB , that's why I am going for a PCI Sata Controller , so I cannot plug the HDD onto the MB

Yes, it should work with the controller as well. You'll have to try it.

---

