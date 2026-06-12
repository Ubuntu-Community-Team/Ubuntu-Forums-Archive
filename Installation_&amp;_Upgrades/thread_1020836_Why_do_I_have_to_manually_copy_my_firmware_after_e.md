---
title: "Why do I have to manually copy my firmware after every kernel update?"
date: 2008-12-24
forum: Installation &amp; Upgrades
---

### Post by laceration on 2008-12-24
Whenever there is a kernel upgrade the firmware file for my dvb card does not get copied, for instance, from /lib/firmware/2.6.24-22-generic/ to the new /lib/firmware/2.6.24-23-generic/. I have to do it myself.  This is not a major problem but it is mildly irritating. Is there a way within the update mechanism that can do this automatically?

---

### Post by Pumalite on 2008-12-24
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/215624](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/215624)

---

### Post by laceration on 2008-12-24
There is a long thread about this at:
[http://www.gossamer-threads.com/lists/linux/kernel/971985](http://www.gossamer-threads.com/lists/linux/kernel/971985)
I didn't get through half of it.  It says that that Debian systems are about the only Linux systems that put firmware in /lib/firmware/$KERNELRELASE(Someone else said this wasn't true of Debian, only Ubuntu).  So if, like me, you have some firmware that is not a native part of the kernel it will not be available after a kernel upgrade unless you copy it over yourself.
A post said if the firmware file is in /lib/firmware/ it will be found before going to /lib/firmware/$KERNELRELASE to find it.  I will try this and hopefully come back to mark this as solved after the next kernel upgrade:P
edit:reading further on it was settled that this is something Ubuntu does, not Debian.

---

