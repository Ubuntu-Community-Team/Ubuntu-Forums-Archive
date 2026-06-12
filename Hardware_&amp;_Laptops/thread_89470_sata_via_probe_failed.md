---
title: "sata_via probe failed"
date: 2005-11-12
forum: Hardware &amp; Laptops
---

### Post by yveskurz on 2005-11-12
Hello,
I'm trying to install breezy on my new PC (Asus Pundit p2-ae2). It has only one (sata) harddisk on a via VT6420 sata-controller. Now when I want to install breezy it doesn't find the harddisk. It says something like:

libata version 1.11 loaded
sata_via version 1.1
sata_via(0000:00:0f.0): SATA master/slave not supported (0xa2)
sata_via: probe of 0000:00:0f.0 failed with error -5
....

this happens with the x86 and the amd64 version of breezy. Even debian etch beta1 installer says the same. 

What can i do? I tried already acpi=off noacpi noapic pci=noacpi. There is no such thing like compatibility mode in the bios and there is also no bios update available.

Anything I can do? 
thanks

---

### Post by bluevoodoo1 on 2005-12-05
I'm thinking about getting an ASUS Pundit-R... I was wondering if you had solved your  problem with the HD, or if the SATA is still giving you problems. Thanks!

---

