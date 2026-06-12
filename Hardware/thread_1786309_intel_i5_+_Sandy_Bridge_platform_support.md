---
title: "intel i5 + Sandy Bridge platform support"
date: 2011-06-19
forum: Hardware
---

### Post by lblum on 2011-06-19
Hi all,

I recently bought a laptop built on Sandy Bridge Platform B2 and iCore5 intel CPU. 
Windows 7 is working fine on it but I would like to install Ubuntu on it too...however given some bad feedback on Ubuntu support for this recent platform I am not sure whether it is a good thing I try or not.

So can anyone either, tell me whether this platform is supported by last Ubuntu version 11, whether what are the (hardware) risks if I try to install it anyway!!

Thanks a lot for your help and have a nice end of week end,

Lionel

---

### Post by Artemis3 on 2011-06-19
Bad feedback? Anyway if you are using a discrete graphics card (ie nvidia) it should work fine ^^

Not real hardware risks short of seeing some graphic glitches because the intel video drivers are not so good. You can always just boot the CD to give it a test drive. I suggest you don't use 3d (ie. Gnome Classic without desktop effects, or Xubuntu with compositing disabled).

It seems mesa 7.11 is needed for better support but ubuntu ships with 7.10. There appears to be a [PPA to upgrade mesa, X, and the intel driver](https://launchpad.net/~xorg-edgers/+archive/ppa).

---

