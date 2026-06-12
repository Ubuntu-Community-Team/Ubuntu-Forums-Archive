---
title: "Resume upon suspend of m1210 with Intel gma"
date: 2007-08-06
forum: Hardware &amp; Laptops
---

### Post by Mega_slayer on 2007-08-06
I was wondering if other people had problems suspending with the Dell m1210? I am using Feisty, have an Intel chipset and I beleive that it may be the Intel 945G with an intel gma (950?) video card.

I can suspend fine, however, upon resuming, the screen becomes all scrambled, or more precisely, what I see on my screen is shifted up and to the left, and the portion that is no longer on my screen comes out on the bottom right corner. It's hard to explain, has anyone else experienced this? Thanks in advance.

- Scott

---

### Post by Mega_slayer on 2007-08-08
I should maybe note that I am using Feisty 32bit. Suspend does not work properly however Hibernate does.

When I was using Feisty 64bit, it was the opposite, Hibernate did not work and Suspend did (if I remember correctly). I did however get some updates, maybe something changed my video settings?
Is anyone else using a intel gma 950 with Feisty 32bit and able to Suspend?

Thanks again.

---

### Post by Mega_slayer on 2007-08-09
I guess that no one else is having any problems. After searching around a bit, I realized that I have an "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller" (according to my xorg.conf file). As well, I was using the i810 driver (suspend didn't work, hibernate did).

Now I uninstalled that driver, installed the xserver-xorg-video-intel driver and my resolution works (1280x800, which actually looks different from the i810 with 915resolution 1280x800!?), as well as resuming from suspend, however Hibernate does not work.

This is not a problem to me but I hope that this little topic helps others, good luck.

---

### Post by Mach1US on 2007-08-09
Another How-to that fixed my problem 100%
[http://ubuntuforums.org/showthread.php?t=471855](http://ubuntuforums.org/showthread.php?t=471855)

---

### Post by Mega_slayer on 2007-08-10
> **Mach1US said:**
> Another How-to that fixed my problem 100%
[http://ubuntuforums.org/showthread.php?t=471855](http://ubuntuforums.org/showthread.php?t=471855)

Thanks a lot Mach1US for the info. I was looking at that and tried the commands, suspend works but it's the resuming that was the problem. I will take another look at it.

---

