---
title: "Is Netbook remix good with SSD drives?"
date: 2010-07-06
forum: Hardware
---

### Post by Julian David Pitt on 2010-07-06
Hi
I have an MSI Wind U115 netbook that is fitted with an 8GB SSD drive, together with a conventional 160GB hard drive. It came supplied with XP Home but I would like to install Netbook remix and was wondering if the trim command is supported by this operating system. I would love to get rid of Windoze and any advice would be appreciated.

---

### Post by AltomineUK on 2010-07-09
> **Julian David Pitt said:**
> Hi
I have an MSI Wind U115 netbook that is fitted with an 8GB SSD drive, together with a conventional 160GB hard drive. It came supplied with XP Home but I would like to install Netbook remix and was wondering if the trim command is supported by this operating system. I would love to get rid of Windoze and any advice would be appreciated.

Hello mate,

Hmm...so let me get this straight. You have a MSI Wind that comes with BOTH an 8GB SSD and a 160GB Hard Disk Drive and you want Linux only machine?

---

### Post by ks07 on 2010-07-09
> **Julian David Pitt said:**
> Hi
I have an MSI Wind U115 netbook that is fitted with an 8GB SSD drive, together with a conventional 160GB hard drive. It came supplied with XP Home but I would like to install Netbook remix and was wondering if the trim command is supported by this operating system. I would love to get rid of Windoze and any advice would be appreciated.
From [http://en.wikipedia.org/wiki/TRIM#Operating_system_support](http://en.wikipedia.org/wiki/TRIM#Operating_system_support) , TRIM is supported in linux kernel 2.6.33. However, the current Ubuntu version of the kernel is 2.6.32. So, afaik, for now TRIM is not supported, unless you manually install the 2.6.33 kernel.

If I were you, I'd wait until it is updated rather than installign manually, but you may have a long wait. Possibly until 10.10 ;)

---

### Post by cascade9 on 2010-07-09
You dont have to have trim support from the kernel. Its the easy, fast way but it is possible to setup trim via hdparm- 

[http://forums.clubrsx.com/showthread.php?p=33429489#post33429489](http://forums.clubrsx.com/showthread.php?p=33429489#post33429489)

---

