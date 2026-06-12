---
title: "Issues with Ubuntu Server on HP Laptop"
date: 2007-01-19
forum: Hardware &amp; Laptops
---

### Post by nextgengames on 2007-01-19
Hey Guys,

This week I installed a LAMP server on my few years old HP Laptop (NX9005) to use as a local development environment rather than running it on my mac which is kinda slowing down with age ;). The idea is to close it up and hide it away in a closet with some other machines

Theres 2 issues I seem to be having; firstly the screen doesn't power down when I close the lid and secondly the fans on the machine seem to constantly be going at full speed which makes it kinda noisy ;)

Any suggestions ?

Thanks Kevin

---

### Post by az on 2007-01-19
Are you using Dapper?


If it doesn't work as it should, there are workarounds.  I assume you are not running the desktop packages, just the base system which is console-only?  The power-saving functionality can probably be installed using the individual packages.

Also, are you using the server kernel or the desktop kernel.  The server kernel will not work well with a lot of desktop hardware, so I would suggest you start by installing the linux-image-386 (for Dapper) or the linux-image-generic (for Edgy or more recent).  That will install the desktop kernel.

---

### Post by nextgengames on 2007-01-19
Yeah Im doing it from the terminal or shell depending on what ever os your used too. The reason I used server was due to the 15 min to LAMP feature which is basically what I need :).

I'll download the desktop kernal version shortly and hopefully it will work a little better. I just need to fiqure out how to reinstall it ;)

Thanks Again.

---

### Post by az on 2007-01-19
> **nextgengames said:**
> 
I'll download the desktop kernal version shortly and hopefully it will work a little better. I just need to fiqure out how to reinstall it ;)

Thanks Again.

Don't reinstall the whole OS.  Just install the kernel.

sudo apt-get install linux-image-386

Then, reboot into your new kernel.

---

### Post by nextgengames on 2007-01-19
Alright cool, Ill go and find that now!

[Edit: That command doesnt seem to work via ssh, as also now my keyboard on the laptop dont work after boot. Its fine on bootmanager though :/]

---

### Post by az on 2007-01-19
Boot the live cd or any installer cd.  Chroot into your system and do it from there.

---

### Post by nextgengames on 2007-01-20
Maybe ive been a mac user to long or something but, i dont see how i get to chroot from the cd , It justs gives me intall options, and boot from hard disk :/

Sorry for all the hassle!

Kevin

---

