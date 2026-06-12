---
title: "Software Raid For Ubuntu Desktop, md modules and mdstat not found."
date: 2009-01-28
forum: Installation &amp; Upgrades
---

### Post by Cyborg28 on 2009-01-28
Hi,

I have an ubuntu x86 desktop machine that I want to add a pair of HDDs to in a software Raid1 config.

The problems is that I can't find the mdstat file in /proc thus indicating that my kernel does not have raid support.

Is this the case for the generic ubuntu desktop install?  Can md-modules be added?  I don't want to have to reinstall my entire system.

BTW: I don't need or want the system areas to be "raided", just a couple drives for user data that I can not afford to lose.

What should I do?

Thanks,

Cyborg

---

### Post by lha on 2009-02-03
Hi,

I set up my raid a few years ago, so I have forgotten the exact steps that I took to get it working. Nevertheless, since noone else has responded, I'll try to help you a bit.

First of all, md-modules can be added - no need to reinstall. You could take a look at [http://www.linuxconfig.org/Linux_Software_Raid_1_Setup]("http://www.linuxconfig.org/Linux_Software_Raid_1_Setup"). It contains some stuff that won't be useful to you, but it hopefully shows you how to get started. Probably loading modules md_mod and raid1 (or some other raid module) will give you a /proc/mdstat. Another useful resource comes with the package mdadm: /usr/share/doc/mdadm/rootraiddoc.97.html. (Make sure you have mdadm installed.)

---

