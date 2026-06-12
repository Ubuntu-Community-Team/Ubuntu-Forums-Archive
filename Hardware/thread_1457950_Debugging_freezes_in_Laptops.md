---
title: "Debugging freezes in Laptops"
date: 2010-04-19
forum: Hardware
---

### Post by CrazyGuy123 on 2010-04-19
Hi,

I have a laptop that from time to time (ie. every few hours) will freeze.

The problem results in an entirely frozen screen (including mouse), and caps lock etc. lights stuck.  Even the sys-rq key combinations do nothing.

I've noticed that when in the frozen state the laptop cools down significantly, so I suspect the CPU is stuck in some suspend-like state. (maybe some driver disabled interrupts and didn't re-enable them)

To debug this on a desktop PC I'd plug in a serial cable, set the kernel loglevel to 9 and watch for the last message before a freeze.  This is a laptop with no serial port, so what do you guys recommend?

I'd prefer to stay away from solutions like "*try noacpi*" or "*remove hardware one device at a time*", because I'd rather track down the exact source code line number that causes this rather than find a work-around.

This is an untainted amd64 kernel with default ubuntu 10.04 b2 fresh install config on an HP nx6125.

Thanks
Oliver

---

