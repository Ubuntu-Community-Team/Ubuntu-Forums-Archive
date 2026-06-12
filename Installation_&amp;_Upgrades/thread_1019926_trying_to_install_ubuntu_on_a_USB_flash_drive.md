---
title: "trying to install ubuntu on a USB flash drive"
date: 2008-12-23
forum: Installation &amp; Upgrades
---

### Post by hatten on 2008-12-23
I'm trying to install ubuntu to my 1 GB USB flash drive, but the installer says i need about 1.9 GB.

But a LiveCD/LiveUSB is only 700 megabytes, so i wonder whether it is possible to make some kind of (live)USB that you can only boot on, not install from, and that works exactly as a normal install. In under 1 GB.

---

### Post by oilchangeguy on 2008-12-23
> **hatten said:**
> I'm trying to install ubuntu to my 1 GB USB flash drive, but the installer says i need about 1.9 GB.

But a LiveCD/LiveUSB is only 700 megabytes, so i wonder whether it is possible to make some kind of (live)USB that you can only boot on, not install from, and that works exactly as a normal install. In under 1 GB.

i suggest you use puppy linux, or damn small linux. even if you can get it to install on 1gb, what's going to happen when ubuntu wants to update? it's not going to fit. you'll have more problems than it's worth.

---

### Post by hatten on 2008-12-23
but if a liveUSB is at 700 megabytes and you strip off the install stuff you should be able to get it under even that.
What's the other differences between a LiveCD/USB and a real install except for that in the Live you can install linux and in the real you can login and you have a bunch more of programs?

---

### Post by Jose Catre-Vandis on 2008-12-23
hatten, you are quite right! There must be a reason behind why you cannot install to a 1GB drive, If all you want to do is install the live usb version to your flash drive. 

The usb creator (which I will assume you need to be using) should do just as you say and copy over the live cd contents (700mb) and ask you for the size of your user space (in your case from 128mb up to @ 300mb), if you are seeking to go persistent. Don't expect to be able to update or customise too much as installed packages will soon swallow up the user space. Don't try to do anything other than simply create a live usb. Trying to install Ubuntu (like you would on a hard drive) will not work as there is not enough space once all the packages are installed.

If you can, take a screenshot of the usb creator window that shows the problem and post it back here so we can see what is happening.

---

### Post by hatten on 2008-12-23
It seems I'm not clear enough. I can make my USB a LiveUSB perfectly, but i don't want it to be an disk that at startup asks me if i wanna install or try without changes and after that i get immediately logged in as root on my USB. What i want is to when i boot my USB i want it to act like a normal install when at startup it asks for username and password, not if i wanna install anything.

And the question is; how do i do that?


If i do an "installation" like the one when you create a LiveUSB and "remove" the possibility to install from i should have about 300 megs or more left, and "adding" a login screen cannot take that much space

---

### Post by Jose Catre-Vandis on 2008-12-23
Sorry hatten, no. When Ubuntu installs, the 700mb expands significantly to @ 2GB installed on your HD. Normally I would allow 4GB for a fully setup environment. So you need a bigger flash drive.

You can add a user with admin rights if you want to a live usb, and login as that user using gdm (which is there by default, just auto logs in the ubuntu superuser to start with)

---

### Post by hatten on 2008-12-24
So it's not possible to make the LiveUSB skip the installation menu and force you to enter a password?

---

### Post by Jose Catre-Vandis on 2008-12-24
This should be possible with edits to syslinux.cfg on the live usb, certainly there is a timeout of 300 milliseconds in there, but I can't see an obvious call for the language selection screen. Maybe someone else can help here.

I use either the boot cd (or a version of it on my hard drive through grub) from [www.pendrivelinux.com](www.pendrivelinux.com) with a modified initrd.gz file, that loads up the usb drivers to allow boot from usb, you get no language screen or boot menu with this setup

---

### Post by emptythevoid on 2008-12-30
Unfortunately, since it's syslinux and not GRUB doing the bootloading, the package **startupmanager** doesn't help.  That was the first thing that came to my mind.

---

