---
title: "[SOLVED] Major problems with X-org and Nvidia 9600gt"
date: 2008-04-13
forum: Hardware &amp; Laptops
---

### Post by |UMN|Mike on 2008-04-13
My graphics card on my desktop recently died and I replaced it with the Nvidia 9600gt and since then I haven't been able to get it to work.  I have tried installing the 171.something driver from nvidia but still can't get it to work.  When I looked in the Xorg log file it says that my graphics chipset is not supported by that driver and I have had no luck going to the vesa drivers.

System: Gusty 64bit
              XfX 9600gt
              AMD 4200
              Asus M2n-sli deluxe


[ATTACH]65823[/ATTACH]

---

### Post by CarVac on 2008-04-13
How did you install it?
I'm assuming you downloaded the right one (64-bit linux).
You have to have to boot in failsafe mode by selecting it in grub.
Then, type in the terminal 'apt-get install build-essential' (no sudo is necessary because you're in a root terminal)
After it installs, type 'runlevel --set=3' (the driver wants this).
'cd' to the directory where you downloaded the driver to.
Run your installer: sh NVIDIA-Linux-[filename].run
It'll ask you if you want to download a precompiled kernel interface for the driver, and don't.

---

### Post by |UMN|Mike on 2008-04-13
I tried that and the log still had the same error at then end.  How long should it take to compile the kernal module?  It seemed to take only a few seconds and that seems to be a little to short.

---

### Post by Neo0351 on 2008-04-14
try this, this is how i got mine working.
[http://ubuntuforums.org/showpost.php?p=4558708&postcount=37](http://ubuntuforums.org/showpost.php?p=4558708&postcount=37)

---

### Post by Neo0351 on 2008-04-14
oh, and it doesnt take long to compile to kernel.

---

### Post by |UMN|Mike on 2008-04-14
Thanks, that got it working.:):):):)

---

### Post by Neo0351 on 2008-04-14
You're welcome

---

### Post by slick_nick on 2008-04-28
Just thought I'd put in my $.02...just built a new computer today with a 9600GT, and a fresh install of Hardy works fine with it. Haven't gotten dual monitors working yet though...

---

### Post by Neo0351 on 2008-04-30
> **slick_nick said:**
> Just thought I'd put in my $.02...just built a new computer today with a 9600GT, and a fresh install of Hardy works fine with it. Haven't gotten dual monitors working yet though...

you're right, it works out of the box for Hardy, but i tried getting compiz to work and nothing.  so i had to install the 173.08 drivers.  at least we got our splash screen back, yay

---

