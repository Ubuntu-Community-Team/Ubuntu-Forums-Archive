---
title: "Dual boot with windows no grub menu to boot linux."
date: 2009-02-03
forum: Installation &amp; Upgrades
---

### Post by mihlub on 2009-02-03
in the last several days i've been stuckedfailed/unsuccessfully in trying to dual boot windows xp, vista, or windows 7 beta with ububuntu. here's what i did.
1. boot with live dvd, use partition tool to split the small 32gb ssd drive into two primary partions 16gb each.
2. install any of the windows mentioned above on partition 1.
3. install ubuntu 8.10 desktop on partition 2. it goes ok. the last few screens of
the installation process detects the existing ofwindows os and was intalling grub accordingly. it then  ejected the live intstallation dvd and proceed to restart the system.

the problem is when the system reboot. it automatically load windows that was insrall on partition 1. it gives no grub menu option to boot any other thing as would be expected on a fully functional grub and dual-boot setup of this type.

i have tried to use the installation cd to use the rescue option without any success.

please help and thanks.

---

### Post by 2hot6ft2 on 2009-02-03
Sounds like you just need to restore Grub to your MBR, so if you boot your Live CD, open a terminal (Applications > Accessories > Terminal) and do:

```
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```

And that's all it should take.

---

### Post by photoikon on 2009-03-28
OK -- just installed Ubuntu 9.04 onto a Vista SP1 machine.  800 gigs for Vista, 200 gig partition for Ubuntu, with 4 gig set aside for a swap.  Reboot the machine, no GRUB at all -- goes straight to Vista. No grub "splash" screen or anything.

Tried the sudo grub as above, (with hd0 and hd1, just to cover all the bases) but get "unable to mount partition" message.

Is this something that's unique, do you think, to 9.04?

Should I just blow away the partitions and start over with 8.xx?

Thanks

m2

---

### Post by brayden13 on 2009-03-28
i would suggest you use the 8.xx ubuntus but if you want to use ubuntu 9 here is what i think i see is the problem.
in 2hot6ft2 post he/she mentioned the command line for loading GRUB into the MBR (master boot record) but it looks like the command is incorrect. the root drive might not be the hd0,0 drive. but then again i'm not exactly a wiz at linux so i'm not sure.

---

