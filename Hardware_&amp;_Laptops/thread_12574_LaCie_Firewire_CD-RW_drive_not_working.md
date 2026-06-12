---
title: "LaCie Firewire CD-RW drive not working"
date: 2005-01-25
forum: Hardware &amp; Laptops
---

### Post by mgalvin on 2005-01-25
Hi All,

This is my first post, as this forum has SO much great info already on it, i haven't had to ask a single question thus far. I have been able to get just about everything working (following how-tos,  and a little bit of manual digging, etc...), ati drivers, music, dvds, 3d, games, ... you name it. The ONLY problem i have not gotten worked out and have not found here is...

my external LaCie Firewire CD-RW drive is not seen by Ubuntu. I cannot use it at all.

It's the 52x one designed by Porsche something or other. I am running i386, 3.2GHz P4, 1GB RAM, 2 IDE HD's, on a Abit IC7-G Max Advance II Motherboard. I am using the 2.6.8-686-smp kernel. This is all under warty. I also tried upgrading to hoary(which is what i am running now) and again, i got everything working except this dang firewire cd-rw drive, argh!!!

Does anyone know how to fix this? Thanks a million in advance!!!

Best Forum Ever!!!
Ubuntu Rocks!!!

Thanks

mg

---

### Post by kafton on 2005-01-26
Are you sure you have the 1394 modules loaded? Run lsmod to see if ohci1394 and ieee1394 are listed. If not, modprobe those modules and try your drive again. If it works add the modules to your /etc/modules file. 
Kafton

---

