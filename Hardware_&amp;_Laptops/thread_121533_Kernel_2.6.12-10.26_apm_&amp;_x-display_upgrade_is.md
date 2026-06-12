---
title: "Kernel 2.6.12-10.26 apm &amp; x-display upgrade issues"
date: 2006-01-25
forum: Hardware &amp; Laptops
---

### Post by olddog55 on 2006-01-25
Greetings:-

After recently doing an apt-get upgrade from 10.25 to linux-image-2.6.12-10-386 2.6.12-10.26, I found the following:

1.  It appears apm support has been removed.  It worked before, but now I'm getting
  tru:~$ apm
  No APM support in kernel

2.  After booting up, I get the normal X-Display login screen, login, but then it just hangs on a brown screen of death with a cursor arrow.

3.  The bootup process seems to take longer then ususal and noticably hangs for ~45 seconds at the 'Configuring Network Interfaces' stage

Adding the boot kernel option 'irqpoll' seems to solve problems 2 and 3, but ???

This is on a IBM ThinkPad 600x, using breezy with all current upgrades.  (Should a bug report be filed?) 

/d

---

### Post by olddog55 on 2006-01-28
bump

---

