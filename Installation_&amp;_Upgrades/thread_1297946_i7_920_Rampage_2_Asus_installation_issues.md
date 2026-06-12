---
title: "i7 920 Rampage 2 Asus installation issues"
date: 2009-10-22
forum: Installation &amp; Upgrades
---

### Post by Tsu on 2009-10-22
I have looked at several of the threads concerning this and serverly confused.

Some people are experiencing issues while others are not.

1> Tried using my SATA dvd/cd rom to install ubuntu 8.04 ltz server edition. It does not see the cd rom after the scan of the cd? What do I do?

2>When loading unbuntu 8.04 lts server edition.(Thats using an IDE cd/dvd rom) I get an issue the second it tries to install or right after it scans the cd. It states that it can't see the CD rom and starts asking me to mount one.

Please save me from this instalation nightmare. I just shilled out £1700 for everything. I don't have the dosh to spen buying another set of components.

Please can someone tell me whats wrong with the DVD/cd rom and why it keeps asking me if I want to use a floppy to load up drivers or then trying a network installation?

I note some threads end with people saying 8.10. How do I get this edition. I can't find where I can download it.

---

### Post by Tsu on 2009-10-22
Windows server 2008 32 bit edition seems to load fine.

So I know this is not a hardware fault. I can only assume that ubuntu 8.04 lts has an issue with SATA installations or does not support my SATA controller/Hard drive controller.

---

### Post by RJARRRPCGP on 2009-10-22
Using 8.04 with a Core i7 setup is asking for trouble, because the hardware is newer than 8.04! 

Don't be surprised if ATA detection fails.

---

### Post by earthpigg on 2009-10-22
hi,

in the future, don't expect a release that came out in the _4_th month of 200_8_ (ie: _8_.0_4_)to support hardware that did not exist at that time :D

Ubuntu 9.04 doesn't quite work properly on my i7 with an Asus mobo system, either, but it works ***okay***.

Hopefully, 9.10 brings better support.

in the meantime, if you must have your server up and running ***right now***:

-Give Ubuntu 9.10 beta a shot. yes, it is beta... but this close to release, 9.10 is *barely* still beta.

-Debian Testing. this is more up-to-date than any version of Ubuntu will ever be, but still pretty damn stable and reliable, and much of your Ubuntu-Fu will carry over.

-failing that, i have been using Arch Linux on my i7 system, and it works fine. rolling release means brand spanking new software... which is more likely to support brand spanking new hardware. Arch is not ideal for a server because it isn't very stable, but if ***any*** distro will work with your just-hit-store-shelves hardware ***today and right now***, it will be a rolling release distro such as Arch or Gentoo.

-combine the above. this is an incredibly unorthodox suggestion, but ill toss it out there anyways. install and configure Arch or Gentoo for hardware support, never update it, then install Ubuntu 8.04 Server ***inside virtual box as a guest OS and configure your server there.*** keep Ubuntu 8.04 up-to-date with security patches and whatnot, but don't touch the host system and risk the instability that comes any time you update a rolling release distro without doing mountains of homework first. when decent Ubuntu support for i7 comes along, migrate your server install from inside virtualbox to a standard install.

---

