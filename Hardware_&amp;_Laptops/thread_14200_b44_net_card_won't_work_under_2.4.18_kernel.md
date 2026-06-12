---
title: "b44 net card won't work under 2.4.18 kernel"
date: 2005-02-05
forum: Hardware &amp; Laptops
---

### Post by drasko on 2005-02-05
I have a problem there - my b44 broadcom sis net card don't work under 2.4.18 kernel - this kernel is old and it don't have support for this card, but I have to use this exact kernel version for my project. I have installed 2.6.9 kernel, and there my b44 work quite well. How can I make it work under 2.4.18 kernel - can I just copy b44.ko file from /lib/modules/kernel/2.6.9/drivers/net/b44.ko to some location in 2.4.18 kernel and where, and after that run modprobe. How to do that? 
I also downloaded the sources for that module. Do I have to compile that source while running in 2.4.18 kernel? What file will I get after compiling and what to do with it? If possible I would rather compile this source running  2.6.9 kernel because I am afraid of all the build-deps that my needed (and I cannot download them from 2.4.18 kernel), but what to do with file I'll get afer this?

Thanks for any help....
Drasko

---

