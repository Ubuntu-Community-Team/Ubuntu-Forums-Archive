---
title: "Internal speaker"
date: 2009-10-31
forum: Hardware
---

### Post by mitsios on 2009-10-31
Hi,
I have recently upgraded to 9.10, and I have a problem. Instead of beeping through the internal speaker, Ubuntu beeps through the normal speakers. What should I do?

---

### Post by Grumbel on 2009-10-31
The file /etc/modprobe.d/blacklist.conf contains the line

blacklist pcspkr

Removing that might be a first step to get the speaker back, but there might be more that needs to be done.

See [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/421250](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/421250)

---

