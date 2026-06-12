---
title: "Wubi and Windows 7"
date: 2009-09-25
forum: Installation &amp; Upgrades
---

### Post by crazyfrog1234 on 2009-09-25
Hi ! Does Wubi 9.04 works correctly with  Windows 7 ?

---

### Post by clonne4crw on 2009-09-25
Eh. I wouldn't try it. All of the machines I've tried Wubi on have had both the Linux and Windows installs completely hosed. 

I'll give it a try in a VM using the RC and tell you how it goes. :popcorn: I'm curious myself.

---

### Post by Mark Phelps on 2009-09-26
The Wubi guide does not list Seven as compatible.  Some folks have been able to get it to work, but requires some hacking to make tht happen.

---

### Post by clonne4crw on 2009-09-26
Windows 7 and Vista use completely different boot loaders, which may or may not make using Wubi any easier. I don't fully understand how the new ones work, but with XP and 2000, you could just edit the boot.ini file and make an entry pointing to a Linux bootloader image.

---

### Post by Mark Phelps on 2009-10-01
I don't think the "new" bootloader introduced in Vista is the problem because folks have reported installing using Wubi in Vista and it works fine.

There is the situation that is new to Seven in that, if you install to an unformatted drive, it creates a separate 100MB "boot" partition.  If folks are attempting to install in that environment, it could be that Wubi is either unaware of that partitioning scheme, or is simply unable to handle it.

However, you can also create an empty NTFS partition and install Seven to that.  Using that approach, Seven does NOT create the 100MB boot partition -- in which case, a Wubi install then should act just like a Wubi install in Vista.

---

