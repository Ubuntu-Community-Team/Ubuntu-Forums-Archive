---
title: "PCMCIA Problem"
date: 2006-07-14
forum: Hardware &amp; Laptops
---

### Post by bigscotty20 on 2006-07-14
:confused: For some reason, my PCMCIA bus is not showing up in Ubuntu. I'm using the original bus in a blue and white PowerMac G3, booted directly (no virtual pc crap.) What do I do to get my cards recognized? ](*,) 

Scott:-k

---

### Post by gratefultux on 2006-07-14
Try installing the pcmcia module for your kernel version.
To figure out what kernel you have type "uname -r" at a command prompt, then search for PCMCIA in aptitude (or whatever you might be using to install programs) and find the module that fits your kernel.

---

### Post by bigscotty20 on 2006-07-14
Thanx! I'll have to try that!

---

