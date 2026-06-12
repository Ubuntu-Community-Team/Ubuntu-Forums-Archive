---
title: "ThinkPad 770E, serial port and pnp problems..."
date: 2006-03-07
forum: Hardware &amp; Laptops
---

### Post by k616 on 2006-03-07
Yesterday i installed ubuntu lite to old IBM ThinkPad 770E laptop. All went well except some serial port problems.. I was able to install tpctl and set port addresses, irq:s etc.. but i can not set 'power management' -bit on. It needs ThinkPads own windows configuration centre (and i don't have it) to do that - except that you should also be able to do it with setpnp. When i try to use setpnp (or lspnp) only answer i got was "lspnp: /proc/bus/pnp not available". A quick search in the web offered as a solution to put pnp support on in the kernel. Well, it's already on...

Right now i'm quite tired (as one might guess from my english), 'cause it's 6pm and i didn't sleep at all last night, but i have to get that port working today. Does anyone have any idea what might be wrong? Installation is ubuntu server installation with some ligthweight x packages, and kernel is 2.6.12-9-686 from ubuntu repositories.

---

