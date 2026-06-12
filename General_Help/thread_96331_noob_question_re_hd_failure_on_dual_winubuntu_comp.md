---
title: "noob question re: hd failure on dual win/ubuntu comp"
date: 2005-11-28
forum: General Help
---

### Post by ubuntunooboob on 2005-11-28
ok well blah...total noob issue..flame away.  Anyway, I decided to give ubuntu a shot on my windows laptop so I installed it and had it partition off about half of the drive for itself.  Everything was going great and I was really enjoying ubuntu but I still need to use windows for my law school exam software.  So yea, I have an exam tomorrow and sure enough 2 days ago windows freaks out for no apparent reason and now if I try to boot into win i get the blue screen of death with a stop 0x24 (corrupt ntsf filesystem) message.  Oddly enough, I can go into ubuntu fine and I can access my windows drive through there.  Do i need to give up and just assume the drive was corrupted due to the partition or is there hope??  Thanks.

---

### Post by IdolizingStewie on 2005-11-28
Have you run checkdisk off a Windows recovery CD? That would be my first step. You could also try some of the diagnostics here [http://www.ubcd4win.com/](http://www.ubcd4win.com/) (the Ultimate Boot CD for Windows) if you don't have a Windows CD handy. 

I'm not really sure what else to do other than if you have the software handy just back up any important files and flatten and reinstall the Windows partition. I suspect that would overwrite Grub though, and you'll need someone more knowledgeable than me to fix the MBR, so my recommendation is running checkdisk.

---

### Post by akiro.yamamoto on 2005-11-29
If you re-install Win and need to repair GRUB try the process mentioned in this post:
[http://ubuntuforums.org/showthread.php?p=529262](http://ubuntuforums.org/showthread.php?p=529262)
Regards

---

