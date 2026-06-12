---
title: "Tri-Boot (XP, PCLinuxOS,Ubuntu)"
date: 2005-11-29
forum: General Help
---

### Post by silverjim on 2005-11-29
Afternoon. I'd like to install Ubuntu to my hard drive. I already have XP and PCLinuxOS 09.2 on there, and I boot up in LILO to switch. I'll either use Acronis or Partition Magic to re-size the partitions, giving myself 2-3 more. I have 3 for XP, 3 for PCLinuxOS, and will probably go for 3 for Ubuntu. I'm looking at a 5gb for /, 1gb for swap (system has 1.2gb memory) and 4gb for /home.

I'm not sure just how to install Ubuntu so that everything gets recognized in LILO. I can't seem to find any info in your Wiki or the forums to do this. 

Since PCLinuxOS finds and runs all of my hardware fine, I'm not anticipating any problems there. My system is a Dell Inspiron 9200 1.6gHz Pentium M, with 1.2gb memory, 80gb disk, 160gb USB2.0 external disk, a Broadcom 440x Ethernet, and an ATI 128mb Radeon 9700.

Anyway, advice would be welcome. I'm pretty cautious, as this is my only system and I just wouldn't want to really screw it up.

---

### Post by aysiu on 2005-11-30
Any reason you want to keep Lilo?
If you install Ubuntu and put Grub on the MBR, Ubuntu will add PCLinuxOS and XP to the Grub boot menu.

---

### Post by silverjim on 2005-11-30
I'll use whatever works. I have no particular prejudice towards either one. Thanks for the advice, aysiu. I'll look into it.

---

