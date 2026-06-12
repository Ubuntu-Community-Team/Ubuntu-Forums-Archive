---
title: "how i can use my 2 cpu?"
date: 2005-12-23
forum: Installation &amp; Upgrades
---

### Post by oceanstar on 2005-12-23
I just installed ubuntu-server on the ibm e-server 8835-31x.
I have a dual processor amd64 server with 2 AMD Opterons .
The default kernel is linux-amd64-k8.
So I can only use 1 cpu.
But when I use  linux-amd64-k8-smp,it doesn't work

I mean when i reboot the system,and start up with linux-amd64-k8-smp kernel.
The system can not start and work .
Looks like having the memory test.
Maybe i'd better to take a photo of it :)

Who can help me ?
Why the smp kernel doesn't work?

---

### Post by randy on 2005-12-24
You can try building an smp enabled kernel using make-kpkg. It'll build your kernel source directory into a debian package and then you can use it to install it.

---

