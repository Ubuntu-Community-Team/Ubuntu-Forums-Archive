---
title: "32bit PCI hardware SATA RAID controller"
date: 2005-02-04
forum: Hardware &amp; Laptops
---

### Post by Gorf on 2005-02-04
I am looking for a hardware based (NOT driver based like Promise) SATA RAID controller that fits into a 32bit PCI bus.  I need it to have at least 4 SATA ports, and needs to do RAID 5.

Of course I also need it to run nicely under Ubuntu :D 

Anyone seen/use something like this?  I have having a hell of a time finding one.  Everything seems to be PCI-X or 64bit PCI.  Will a 64bit PCI device run in a 32bit slot? Is there hardware compatability for that?

Thanks guys...

---

### Post by deppingh on 2005-02-07
Try one from 3Ware ([http://3ware.com/](http://3ware.com/)).  Their PCI raid controllers are natively supported by kernel 2.4 and up.  They're not cheap, but in my experience they're very reliable and completely hassle-free.  I have two 7000 series IDE controllers that work just fine with every distro I've tried, including Ubuntu.

---

