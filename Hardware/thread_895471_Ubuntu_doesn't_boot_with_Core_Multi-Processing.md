---
title: "Ubuntu doesn't boot with Core Multi-Processing"
date: 2008-08-20
forum: Hardware
---

### Post by Teiseii on 2008-08-20
Hello !

I'm having problems with my Lenovo Thinkpad T60 and Ubuntu. I get kernel panic or CPU failure whenever I try to boot to Ubuntu in normal mode. Sometimes I get the same errors in recovery mode. Live CD's (7.04, 7.10, 8.04) refuse to boot as well. If I enter Ubuntu in recovery mode successfully and launch GDM from there, I will encounter HAL problems, applications will crash etc. so it isn't usable that way.

I have located the problem by playing with BIOS. If I disable "Core Multi-Processing" option in BIOS, I can boot normally to Ubuntu and Live CD's without any problems. However, when I enable it, the symptoms I mentioned will appear again.

The problem is that I can't utilize the full power of my CPU in Ubuntu because only one core is in use. I'd like to be able to use the "Core Multi-Processing" option without problems.

I have both i386 and Generic kernels installed, but none of them work with "Core Multi-Processing" enabled. I'm running Ubuntu 8.10 at the moment, but I've had this problem since Ubuntu 7.10.

Thank you for any solutions you come up with.

---

