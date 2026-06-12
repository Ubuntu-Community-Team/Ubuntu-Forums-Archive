---
title: "Why not autorun?"
date: 2009-08-06
forum: Installation &amp; Upgrades
---

### Post by ThomasHu on 2009-08-06
Followed "[SIZE=2]Preparing Files for USB Memory Stick Booting", [/SIZE]I create a flash disk installer for ubuntu 9.04. 
My syslinux.cfg:
default vmlinuz
append initrd=initrd.gz

But it hint "boot:" after I boot from usb stick.
If I type " vmlinuz initrd=initrd.gz", it will start to install.

I want to run it automatically, how can I fix it?

---

### Post by ThomasHu on 2009-08-07
> **ThomasHu said:**
> Followed "[SIZE=2]Preparing Files for USB Memory Stick Booting", [/SIZE]I create a flash disk installer for ubuntu 9.04. 
My syslinux.cfg:
default vmlinuz
append initrd=initrd.gz

But it hint "boot:" after I boot from usb stick.
If I type " vmlinuz initrd=initrd.gz", it will start to install.

I want to run it automatically, how can I fix it?


I fix it.
sysconfig.cfg:
[SIZE=2]TIMEOUT 1
[/SIZE][SIZE=2]PROMPT 0
[/SIZE][SIZE=2]NOESCAPE 1[/SIZE]
DEFAULT vmlinuz
  APPEND initrd=initrd.gz

---

