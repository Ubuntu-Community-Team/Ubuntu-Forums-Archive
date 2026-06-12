---
title: "Feisty Fawn and the Geforce 8"
date: 2007-03-26
forum: Hardware &amp; Laptops
---

### Post by ravalox on 2007-03-26
Hey, I have a new machine and I'm trying to get 3d support in Feisty Fawn, the nvidia-glx drivers don't seem to support the geforce8.  Can I get 3d support out of Ubuntu or do I need to try to force the nvidia drivers from their website?

---

### Post by s0cket on 2007-03-26
> **ravalox said:**
> Hey, I have a new machine and I'm trying to get 3d support in Feisty Fawn, the nvidia-glx drivers don't seem to support the geforce8.  Can I get 3d support out of Ubuntu or do I need to try to force the nvidia drivers from their website?

You want a 9xxx series driver.  You can get them from the nvidia website.  Remember to apt-get build essentials and kernel headers before you try to install them.

---

### Post by ravalox on 2007-03-27
This is all good advice, here's the catch;  Feisty Fawn will NOT let me stop X!  I've tried init 1, ctrl+alt+backspace, /etc/init.d/gdm stop, I even tried kill -9 on Xorg.  All of these things forced me to reboot, none of them would give me an X-less terminal!  So I could install the nvidia driver, if I could stop X.

---

### Post by Motoxrdude on 2007-03-27
> **ravalox said:**
> This is all good advice, here's the catch;  Feisty Fawn will NOT let me stop X!  I've tried init 1, ctrl+alt+backspace, /etc/init.d/gdm stop, I even tried kill -9 on Xorg.  All of these things forced me to reboot, none of them would give me an X-less terminal!  So I could install the nvidia driver, if I could stop X.

Reboot your computer and select the failsafe mode in grub. Just remember that you are root when you boot the failsafe mode and think before you type ;-)

---

