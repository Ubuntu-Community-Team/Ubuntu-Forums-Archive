---
title: "Running Ubuntu on a MacBook/MacBook Pro"
date: 2006-10-28
forum: Hardware &amp; Laptops
---

### Post by aktiv on 2006-10-28
Hi

I am wondering if anyone has any experiences, comments or general info on running Ubuntu on a MacBook/MacBook Pro. 

I need a laptop for cross-platform developing, with C# (VS2005) and QT4 for GUIs. Compiling C# will be done with mono in linux and osx.

So I figured I could get a MacBook. I know it's possible to run WinXP in windowed mode in OSX, what about Ubuntu?

I am currently running Ubuntu on my Desktop PC, while running VS2005 in WinXP with VMware, and it's working flawlessly.

The way I see it, the alternatives are:
1. Running OSX and Ubuntu dual-boot, and running XP through VMware in the Ubuntu partition. Any comments/tips/experiences?

2. Ideally, I want to avoid dualbooting, so if I could run both WinXP and Ubuntu windowed on OSX that would be the best solution. Comments/tips/experiences?

What works "best" for XP, running with vmware in ubuntu or with 'whatever equivalent' in OSX? (Haven't gotten around to researching this properly yet, thought I'd ask around here first, surely I can't be the first to try to do this? :) )

tx
Aktiv

---

### Post by Unicast on 2006-10-28
There's a thread here: [MacBook Pro Linux](http://www.ubuntuforums.org/showthread.php?t=198453) :mrgreen:

---

### Post by idn on 2006-10-28
Works good for me, the only problem is that grub doesnt install, which means updating lilo is always a hassle.

---

### Post by rdwtux on 2006-10-28
> **aktiv said:**
> Hi

2. Ideally, I want to avoid dualbooting, so if I could run both WinXP and Ubuntu windowed on OSX that would be the best solution. Comments/tips/experiences?


Running Ubuntu (or any linux distro) natively in dual or single boot on the Macbook isn't quite there yet.  It works but your going to either have to jump through a lot of hoops to get all the hardware working properly. 


Windows XP runs in dual-boot mode using Bootcamp very well on the Macbook with good driver support.  Linux needs a little while to get the drivers and EFI boot support into distro's.

Your #2 option will work fine though.  I have a 120gb hard drive in my Macbook with 2gb of RAM, running OS X natively with Ubuntu Edgy and a few other distro's running in Paralells ([http://www.parallels.com](http://www.parallels.com)) and they run flawlessly and fast. 

That will allow you to use Mac OSX natively and Windows XP and Linux in Parallels without rebooting.

---

