---
title: "locked on boot::asking for root password"
date: 2005-11-12
forum: General Help
---

### Post by {{corona}} on 2005-11-12
hi after my last reboot the boot sequence ends up in a file system check on root and asks for root password! now my sudo password does not work as root. and therefore the only other option is to press ctrl-d which reboots the system and the same thing happens again. earlier a ctrl-d would carry on and kubuntu would startup. can someone help?

I tried the recovery mode too and the same thing happens- the filecheck asking for root password without which it reboots again!

can someone help?

---

### Post by {{corona}} on 2005-11-12
solved:

you will have to gain root access by following one of these methods.

[http://ubuntuguide.org/#gainrootwithoutlogin](http://ubuntuguide.org/#gainrootwithoutlogin)

and after that run fsck on your root after you have umounted it.

this guide is really useful

---

