---
title: "Fresh Install problems on multi-HDD PC"
date: 2009-09-04
forum: Installation &amp; Upgrades
---

### Post by Velvet Karuda Leopard on 2009-09-04
Ok.  I just got this computer from a friend and he has had like five different OSes on it in the past.

It currently has two (2) copies of Vista, have no idea why, and about four different Linux flavors, again have no idea.

The box is a Compaq with an AMD Athlon 64 LE-1620, 861 MBs of RAM, and running nVidia onboard graphics.

It has two hard drives and there is at least one OS one each of them.  It has a multi-boot setup.

I am wanting to totally erase every bit of data from the drives and install a fresh install of either Ubuntu 9.04 or Ubuntu Studio 9.04.

I have tried installing using the proper .ISO, but every time it finishes, I have the EXACT same system and setup as before I run the install.  The only change is that now EVERY flavor of Linux on the multi-boot page says Ubuntu 9.04 even though some of the kernels are from years before Ubuntu came to be.

How can I erase both drives and have my machine as if it came with Ubuntu 9.04 on it in the first place?

---

### Post by soloman498 on 2009-09-05
Try downloading  Gparted iso disk and running it at startup and formatting one of the disks and then reloading what you want.

---

### Post by QIII on 2009-09-05
... or

Change the boot order of your drives to have the first one (AFTER your cd/dvd drive!) be the one you want to install Ubuntu on.

When installing, go the easy route and use the drop down to select your desired hdd and select "Use entire disk".

After Ubuntu is installed on that disk, install gparted and repartition the other drive.

---

