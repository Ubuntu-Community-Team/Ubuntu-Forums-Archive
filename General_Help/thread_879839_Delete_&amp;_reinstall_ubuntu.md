---
title: "Delete &amp; reinstall ubuntu"
date: 2008-08-04
forum: General Help
---

### Post by Vasilisgr on 2008-08-04
Good evening, i am a newbie and i manage to mess up my dual boot (vista - ubuntu hardy), i posted few threats here at the forum and everybody was very helpful, thank you a lot for that. But i couldn't fix it. I have vista pre-installed on my laptop (HP Pavilion DV 60xx) and then i install ubuntu hardy with wubi. Everything was fine until i got a magazine with the Ultimate Gamers Edition of hardy and install it as well on my external hard drive... and then everything started. GRAB 21 error when my usb is not plugged ! when usb is present no problem i can boot anything i like.... now i uninstall ubuntu from my windows, the one i got installed with wubi, and i want to delete also ubuntu from my external drive as well. If i do so i will still get Grub 21 ? because if i delete everything then i will not be able to boot at all.... :confused::confused::confused:

---

### Post by Elfy on 2008-08-04
If you want to delete everything then without fixing the windows boot then yes you will have problems - it can be dealt with though.

If you are going to reinstall buntu - I would do a clean install on the laptop so you are running a dual boot, the install will share the drive for you.

But make sure you have defragged windows a couple of times before you start.

---

### Post by geirha on 2008-08-04
Grub is most likely installed on the internal drive. When you installed on the external drive, the best thing to do would have been to install grub on the external drive. Of course, you usually don't know these kinds of things before you've used and messed up linux a few years. 

Anyway, the easiest way to fix your current problem is to let Vista overwrite the grub bootloader with its own bootloader. I don't have vista myself, but earlier windows versions you could boot the windows CD and select something like "Repair MBR". There's probably something like this for Vista too. 

Another option may be to download and burn the SuperGrubCD, boot it, and have it change grub to only boot Vista on the internal drive.

---

### Post by Vasilisgr on 2008-08-04
ok i did get it working with out the grub error but i did a mess again ](*,)

i manage to overwrite ubuntu at the backup partition of vista :shock:

i downloaded the paragon disk manager which have its own boot manager so you overdrive grub :)  :guitar:

thanks for the help :KS


p.s i dont know how to mark it as solved...:lolflag:

---

### Post by Elfy on 2008-08-04
Thread tools at the top - glad you're done.

---

