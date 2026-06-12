---
title: "Can't install Vista?"
date: 2009-07-30
forum: Installation &amp; Upgrades
---

### Post by CastilleV on 2009-07-30
Hey everyone, I want to use both Ubuntu and vista, but I want to use Ubuntu through VMware on Windows Vista (So to say I want to completely remove Ubuntu from my PC), but when I get to the install screen, its says that my partitions aren't NTFS anymore, when I was able to install XP on my PC.

---

### Post by running_rabbit07 on 2009-07-30
Boot up with the Ubuntu LiveCD and open System>Administration>Partition Editor. You can then delete the partitions if you want everything gone and create an NTFS Primary partition. After that, try loading Windows. 

If you have any problems after you have started your formatting, boot with the LiveCD and come this forum or go to the Microsoft forum.

 Edit: In the future if you decide to install Linux again, leave your Windows installed on a small partition. It is much easier to tell grub to hide the Windows boot loader and have Windows there later if you want it.

---

### Post by Dullstar on 2009-07-30
If Microsoft has a forum, it's probably forbidden to give useful advice. :)

---

