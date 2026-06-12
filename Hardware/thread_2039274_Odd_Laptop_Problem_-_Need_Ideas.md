---
title: "Odd Laptop Problem - Need Ideas"
date: 2012-08-08
forum: Hardware
---

### Post by pauldemet on 2012-08-08
Am trying to solve a strange problem. Have a laptop that works just fine when booting Windows or DOS. When I boot Ubuntu Linux and turn the system off, then the laptop will not even get through the BIOS. It turns itself off after a few seconds. If I boot up to the Grub selection screen and then turn the system off, the laptop still boots correctly. Once I let the kernel load and power off, it will never boot again. When I remove all power sources to the laptop, it will then boot correctly one time and then the problem returns.
 
So what is the Linux kernel doing to my system that is causing it not to boot? Could the kernel be changing my system configuration?
 
I have compared the CMOS under DOS and Linux and there are four bytes that are different but I don't have the CMOS map for the device.
 
Any guidance would be appreciated.

---

### Post by TheFu on 2012-08-08
Sorry, I don't have any clue what could be happening.  I'd think the issue would be in the MBR, not the CMOS.  This script [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) will pull information about your system drives and boot "stuff." It might shed some light on an issue for you.

---

