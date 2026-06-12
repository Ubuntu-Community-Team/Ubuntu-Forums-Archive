---
title: "Damaged Grub"
date: 2010-02-02
forum: Hardware
---

### Post by Mat11 on 2010-02-02
Hi i've tried to repair my boot up problem whereby i had to press the power on switch 3 times to get the O/S to work, so i took a chance with a suggestion on the forum.
Deleted pc grub and grub common using sudo then tried to reinstall them with only the pc grub installing properly.
My laptop is a i386 how do i start to fix the problem ?
All i see at the moment is a question mark after Grub recovery.Think i'm in the **** !
Ran the 9.10 boot CD and it indicated i had 3 missing files. 
How can i use my CD to recover ?
 
Need help 
 
Matt

---

### Post by zwaardmeester on 2010-02-02
Hi Matt, taking the advice about reinstalling packages was not a good idea. When your problem would indeed come from Grub, then updating the configuration file would have been enough, probably. Hopefully the packages are still present on the system, in which case you can follow the steps from [this guide]("http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7") (try option 2 or 3). Keep us posted on how that went. 

Worst case the grub package is missing or broken, which means we have to re-install it by chroot. With this i have no experience, so I hope somebody else can come to the rescue. 

Good luck!

---

