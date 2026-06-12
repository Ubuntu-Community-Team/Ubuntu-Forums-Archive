---
title: "heavy network load on via VT6105 [Rhine-III] freezes system"
date: 2007-04-16
forum: Hardware &amp; Laptops
---

### Post by b52_ on 2007-04-16
Hi folks,

I discovered that my system freezes under heavy network load with my VIA Rhine VT6105 network controller. Well it doesn't really freeze, its just not mouse or keyboard interactive anymore.

On the remote host I still see my laptop sending and receiving packages. There is no log output about something is going wrong, but I think its caused by too many interrupts. Under medium network load I can see about 20 percent hardware interrupts and 20 percent software interrupts in top.

I use a selfcompiled kernel 2.6.17.14-ubuntu1 #1 PREEMPT from ubuntu kernel sources and it doesn't make any difference if I compile via_rhine as module or not. The strange thing is that I used gentoo before, with exactly the same kernel configuration and it worked perfectly.

I attached the lshw output and the kernel configuration.

Thank you for any help.

---

