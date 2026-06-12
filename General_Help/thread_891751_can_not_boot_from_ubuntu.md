---
title: "can not boot from ubuntu"
date: 2008-08-16
forum: General Help
---

### Post by thomaskprakash on 2008-08-16
dear friends,
i have successfully installed ubuntu on a hard disk which already had windows Xp, but was unable to boot. after installing ubuntu i am not able to get the boot screen. so the system does not boot into ubuntu linux. what could be the problem ? can anybody help ?

---

### Post by Naatan on 2008-08-16
Do you get into GRUB (the screen that asks you what to boot) and what happens when you try to boot? Just a black screen or do you get any errors?

---

### Post by thomaskprakash on 2008-08-17
i dont get the GRUB screen. in the process of installation, no GRUB configuration was prompted for. i have two hard disks. one a 20 gb and the other a newer 80 gb disk. i have windows98 and redhat linux on the 20 gb disk(ide0), but both i am unable to boot from both. in the 80 gb disk(ide1) there is windows xp and windows 2000 installed. windows2000 had been corrupted long ago. So i had been using windows Xp for sometime now. At present even windows XP too became unusable. So i tried to install ubuntu. the installation was successful. but i get only the windows98 and redhat linux boot screen of the old 20 gb hard disk when i try to boot. the ubuntu boot option is nowhere to be seen.

---

### Post by Naatan on 2008-08-17
Odd, GRUB is installed by default.. you'd have to manually disable it during installation for it not to get installed..

Either way, try following the steps given at the following url;

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

Nevermind the title.

---

