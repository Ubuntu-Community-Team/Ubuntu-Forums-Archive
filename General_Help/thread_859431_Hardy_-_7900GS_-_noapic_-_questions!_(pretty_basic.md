---
title: "Hardy - 7900GS - noapic - questions! (pretty basic)"
date: 2008-07-14
forum: General Help
---

### Post by blackbinary on 2008-07-14
Hello everyone!

I first tried Ubuntu with the earlier release Gutsy, and I had a few problems. I use an nVidia 7900GS, and could never get the drivers working properly. Also, to boot I had to use a noapic flag. I have found that the 7900GS is under nVidia's supported-product list as far as linux drivers go (from what I understand), which makes me think it wouldn't be hard to install said drivers. Could someone point me to a tutorial on how to install the drivers in hardy properly? Secondly, is there anything I can do about the noapic thing? Finally one of the stranger problems that stopped me from using Ubuntu; if I left my computer alone for a few minutes (10-15) the mouse and keyboard input would freeze. I know this because if I pressed the power button on my tower, the log off / shutdown screen would pop up promptly, though my keyboard nor mouse worked. 

I am hoping these issues will clear up with Hardy Heron. If anyone has got a 7900GS working with full compiz support it'd be nice if you could post here what you did.

As for my hardware:

Motherboard: ASUS M2N32-SLI-Deluxe (most recent bios)
Video Card: nVidia 7900GS
RAM: 2GB 667Ghz OCZ DDR2 (and a 1GB stick of value ram im thinking of taking out, lol)
CPU: Amd Athalon64X2 5200+
HDD: 320GB SATA, 80GB SATA, 1TB e-SATA
O/S: Right now I have XP on the 80GB. Thats all that is on it.

Hopefully you don't need to know much else, though if you do let me know. 

As a side-question, if I put ubuntu on the external drive (on its own partition) would there be a way to get it work(boot would be lovely) on multiple hardware configurations? 
(I would have maybe 3 different hardware-configs. Could I get it to automatically choose the correct configuration, or at least let me choose at a boot loader (e.g. Ubuntu Comp-1 , Comp-2 , Comp-3) which would tell it which configuration to use. Or do I even have to do that? I'm coming from XP and I know you could manage doing it using their hardware profiles service that was aimed at laptops)


Thanks for any and all help :)

---

### Post by hal8000 on 2008-07-14
Here you are:

[http://ubuntuguide.org/wiki/Ubuntu:Hardy](http://ubuntuguide.org/wiki/Ubuntu:Hardy)

Section 1.7.1 on installing the Nvidia OpenGL drivers.

You are better off installing Ubuntu on its own partition, booting different OS's is only a matter of modifying lines in grub/menu.lst

---

### Post by blackbinary on 2008-07-14
> **hal8000 said:**
> Here you are:

[http://ubuntuguide.org/wiki/Ubuntu:Hardy](http://ubuntuguide.org/wiki/Ubuntu:Hardy)

Section 1.7.1 on installing the Nvidia OpenGL drivers.

--- And i'm assuming this will work properly? I followed a similar guide for gutsy and it did not work :(. 

You are better off installing Ubuntu on its own partition, booting different OS's is only a matter of modifying lines in grub/menu.lst

----Um what? I don't recall saying Ubuntu wouldn't be on its own partition. And yes, i understand how to boot different OS's(didn't think i asked that question lol!), what I wanted to know is if I could boot with different hardware. In windows this means you have a hardware profile that has all the drivers you need attached, and another profile with different drivers. Then you have to select which profile to use and it will work on 2 different computers :)



^

---

