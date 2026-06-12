---
title: "Kernel Panic caused by PC Card Use?"
date: 2007-01-11
forum: Hardware &amp; Laptops
---

### Post by Slodeine on 2007-01-11
I've recently been experimenting with dual-booting Edgy Eft and Windows. I first tried it on my Desktop with Windows 2000 and was impressed with the out-of-the-box compatibility I experienced with my admittedly disparate setup. However, I share that computer with family members and dislike restarting whenever they need to use Windows. So I shrunk the WinXP partition on my personal laptop and installed Ubuntu. Again, I was impressed that Ubuntu recognized my wireless PCI card (Linksys WPC54G v1.2) out of the box, but I experience what I am told is called "kernel panic" whenever I attempt to use the card, or even configure it. Additionally, Edgy Eft's drivers do not seem to provide full functionality.

Believing my difficulties were driver-related, I spent several days on the forums, attempting to find alternate drivers. I attempted to use ndiswrapper as well as bcm43xx to no avail. Ultimately, I completely reinstalled Edgy Eft and attempted a solution detailed in another thread. The bcm43xx driver seems to provide better functionality, but kernel panic still occurs. In fact, it occurred in every solution I attempted.

I've even tried another wireless card, the Belkin F5D7010, and that causes kernel panic right at the login screen, before I can even try to do *anything*.  I'm beginning to think that the problem has nothing to do with drivers or networking, but perhaps the manner in which Ubuntu deals with the PC Card slots themselves.  Unfortunately, I have no other PC Card devices to test this theory with.

Can anybody offer a solution to this problem?  Or at least a way of finding out if this indeed *is* the problem?

For reference, my laptop is a Toshiba Satellite A45-S120.

---

### Post by Slodeine on 2007-01-11
I hate to bump, but I could really use some help with this.  This issue is the deal-breaker for Ubuntu and I.  :(

---

