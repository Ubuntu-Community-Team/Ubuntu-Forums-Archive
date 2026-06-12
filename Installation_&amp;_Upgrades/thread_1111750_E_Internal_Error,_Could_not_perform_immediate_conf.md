---
title: "E: Internal Error, Could not perform immediate configuration (2) on libc6"
date: 2009-03-31
forum: Installation &amp; Upgrades
---

### Post by atulgoyal52 on 2009-03-31
Hi,
I'm trying to install packages with apt-get in my ubuntu 7.04. But after the whole downloading I got the following message:

E: Internal Error, Could not perform immediate configuration (2) on libc6

Any help?

---

### Post by atulgoyal52 on 2009-03-31
please suggest some way to overcome this error. I'm stuck just because of this error.

---

### Post by byramm on 2009-04-09
I hit the same error after updating /etc/apt/sources.list to use jaunty packages instead of feisty packages and performing a

[INDENT]apt-get update; apt-get dist-upgrade[/INDENT]

A simple work-around is to make a smaller leap. For example upgrade to hardy first, then upgrade to jaunty.

---

