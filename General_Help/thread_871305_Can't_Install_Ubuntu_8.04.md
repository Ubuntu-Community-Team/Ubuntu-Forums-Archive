---
title: "Can't Install Ubuntu 8.04"
date: 2008-07-26
forum: General Help
---

### Post by statman88 on 2008-07-26
Hello,

I am having some problems installing 8.04 on a desktop machine.  It is a compaq presario 80g hard drive. 256 ram and intel celeron processor.

When I try and install 8.04 on the machine using the largest free continious space I get an error message window 

"the configuration could not be loaded.  You are not allowed to access the system configuration"

???  Not sure why.....XP runs fine on the same machine.

Any help would be greatly appreciated.

Thanks in advance,

Statman88

---

### Post by CatKiller on 2008-07-26
I wouldn't install Ubuntu on a computer with that amount of RAM. Try Xubuntu or one of the other lighter-weight distributions.

Lack of memory in the live cd environment can cause peculiar behaviour.

---

### Post by statman88 on 2008-07-26
> **CatKiller said:**
> I wouldn't install Ubuntu on a computer with that amount of RAM. Try Xubuntu or one of the other lighter-weight distributions.

Lack of memory in the live cd environment can cause peculiar behaviour.

Thanks for the replay!

But, According to the System Requirements

[https://help.ubuntu.com/community/Installation/SystemRequirements]("https://help.ubuntu.com/community/Installation/SystemRequirements")

The computer I am trying to install it on will more than suffice.

Statman88

---

### Post by CatKiller on 2008-07-26
> **statman88 said:**
> Thanks for the replay!

But, According to the System Requirements

[https://help.ubuntu.com/community/Installation/SystemRequirements]("https://help.ubuntu.com/community/Installation/SystemRequirements")

The computer I am trying to install it on will more than suffice.

> It should be possible to get Ubuntu running on a system with the following minimum hardware specification, although it is unlikely that the system would run well. You should use the Alternate install CD to attempt such an installation.

That's for a really bare installation - no graphical interface at all. The live cd will not run properly with less than 384MiB of RAM. You can install with 256MiB of RAM without using the live cd with the text-mode installer. This will let you use a full install without the extra overhead of running the live environment at the same time.

More RAM will help enormously, and using a lighter distribution, like Xubuntu, will also help performance.

---

### Post by statman88 on 2008-07-27
Thank you for your information.  I will try the text-mode installer.

---

