---
title: "Toshiba Laptop ACPI"
date: 2010-08-13
forum: Hardware
---

### Post by cravenc on 2010-08-13
Hey all,

I found a fix to my problem and decided to document it here for others.  I own a Toshiba Satellite L505D-LS5010 which I bought off Newegg for $400 (deal of the week).  I tried to install 10.04 on it but ran into problems with ACPI.  To install I had to turn ACPI off by pressing F6 to get to the Live CD menu and then F6 again to turn off ACPI.

That part was documented already.  However, once installed I could not see any information about the battery, making it essentially worthless as a Laptop.  I found my solution in installing the 2.6.35 Kernel from this location.

[http://www.ramoonus.nl/2010/08/linux-kernel-2-6-35-installation-guide-for-ubuntu-linux/](http://www.ramoonus.nl/2010/08/linux-kernel-2-6-35-installation-guide-for-ubuntu-linux/)

After following his directions and installing the new kernel I could use most function keys and see my battery state.  

Hopefully this helps someone.

---

