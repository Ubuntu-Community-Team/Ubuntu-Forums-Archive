---
title: "Can't boot without pressing a key"
date: 2009-06-04
forum: Installation &amp; Upgrades
---

### Post by hughc1 on 2009-06-04
I upgraded to jackalope from the a CD downloaded from the Oregon site.  The download was MD5Sum checked OK.  The CD was made at the slowest speed. The install was successful.  But, the system won't boot or shutdown completely without pressing Enter. I get a grub menu, pick Ubuntu, the boot starts, a few lines display(no errors) and the disk lite goes out.  If I press enter or any key the disk lite displays and the boot increments, stops, and waits for me to press another key.  The system eventually boots and works until shutdown.  The desktop goes away, a few lines display, then the disk lite goes out.  I press enter, the disk lite displays and continues as I press enter.  Any ideas?    

The machine is a Compaq Presario F700, 1 gig of ram with 100 gig hard disk. Nvidia, ath5.

The problem is with the CD used to install the software too.

---

### Post by ScottHW on 2009-06-04
You sure you have 1 meg of RAM?

I'm looking at my GRUB menu.lst now, but I don't see any "delay" options, only the "timeout", and that doesn't sound like what you're describing.

---

### Post by hughc1 on 2009-06-04
I downloaded from a new iso from the Purdue site, md5sumed and burned a new CD.  Followed with a new install using the CD.  Same problem.  
BTW, I'm installing 64bit
Linux hughc-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux

---

### Post by DataMatrix on 2009-06-04
A friend of mine have the same issue with HP Pavillion notebook (AMD Athlon64 X2 CPU) but he has that issue with 8.10. He has to keep pressing space in order to reach run level 2 and from there on everything is normal.
Any ideas?

---

### Post by hughc1 on 2009-06-05
Its good to know I'm not the only person with this problem.
Does your friend run 64 bit?
Thank you.

---

### Post by hughc1 on 2009-06-05
I found more info in another thread.
[http://ubuntuforums.org/showthread.php?t=1059545](http://ubuntuforums.org/showthread.php?t=1059545)

Thanks.

---

### Post by 3nd3r on 2009-10-20
add acpi=noirq to your kernel line in your /boot/grub/menu.1st

---

