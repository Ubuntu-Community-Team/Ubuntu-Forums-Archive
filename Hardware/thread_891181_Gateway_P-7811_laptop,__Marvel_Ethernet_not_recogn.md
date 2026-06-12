---
title: "Gateway P-7811 laptop,  Marvel Ethernet not recognized."
date: 2008-08-15
forum: Hardware
---

### Post by Der_Idiot on 2008-08-15
I have a Gateway P-7811 and it has a Marvel Yukon 88E8057 gigabit PCI-E port, at least according to windows. It was not recognized by Ubuntu 8.04 during install, but the wireless works 8-[. lspci finds a Marvel Yukon device, but doesn't know what to do with it, and states it as 'unknown'.

Any ideas? This is a new chipset, apparently.

---

### Post by Der_Idiot on 2008-08-16
Nothing yet? :confused:

---

### Post by jhelmer on 2008-08-27
There is kernel support for that card as of 2.6.27-rc3 ([http://www.linuxhq.com/kernel/v2.6/27-rc3/drivers/net/sky2.c](http://www.linuxhq.com/kernel/v2.6/27-rc3/drivers/net/sky2.c)).  I manually downloaded the kernel and got it compiled.  It seems to be working out OK.

---

### Post by Der_Idiot on 2008-09-06
Well, that's good to hear. Now I just need to learn how to install a new kernel :confused:

I wonder if I'll be able to raid0 this machine and still dual-boot with no trouble, heh :lolflag:

---

