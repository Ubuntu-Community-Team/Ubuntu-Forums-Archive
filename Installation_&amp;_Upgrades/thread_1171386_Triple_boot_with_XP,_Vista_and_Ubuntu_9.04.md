---
title: "Triple boot with XP, Vista and Ubuntu 9.04"
date: 2009-05-27
forum: Installation &amp; Upgrades
---

### Post by Posessor on 2009-05-27
So I decided to give Ubuntu 9.04 a try and installed it next to my already existing dualboot of Xp and Vista. Now the problem I'm having is that GRUB made all the right entries for Ubuntu to boot correctly but for my already existing dualboot it made a new entry that just refers to the vista bootloader. So when I pick the new entry, I get the Vista boot screen where I can choose between Xp and Vista.

What I would like to do is make grub the only loader I need. Could you guys please help me on how to do this?

---

### Post by argail1980 on 2009-05-27
first you have to add the entry for XP to grub, if I got you right. the config-file to edit is /boot/grub/menu.lst.

```
sudo gedit /boot/grub/menu.lst
```

with a little experience you can modify the file to include you XP partition. If you have no experience, post the content of the file.

then you need to turn off the bootloader in Vista. The file you need to edit is boot.ini (somewhere in the depths of Windoze). But I can't tell you exactly how. in any case you can reduce the time the win-bootloader waits before booting the default system.

---

### Post by unix1adm on 2009-05-27
i have the same issue i can see the fedora/redhat boot but when i try to boot xp it wont load. 

i also lost my wireless networking

---

### Post by Mark Phelps on 2009-05-27
> **Posessor said:**
> What I would like to do is make grub the only loader I need. Could you guys please help me on how to do this?
I don't believe that is possible because, for non-Linux OSs, all GRUB does is hand off loading to another loader. 

If what you want is to only have one menu (which is what I think you're asking), that is a LOT of work because of the new structure of the Vista boot loader.  

All GRUB will be able to do is point to a specific partition.  You will have to hand-edit the Vista BCD file, and that can only be done in Vista.  You can download a tool to do that (known as easyBCD) from the NeoSoft forums. Suggest you go there and check their forums regarding the details of what you want to do.

---

### Post by Posessor on 2009-05-27
> **Mark Phelps said:**
> I don't believe that is possible because, for non-Linux OSs, all GRUB does is hand off loading to another loader. 

If what you want is to only have one menu (which is what I think you're asking), that is a LOT of work because of the new structure of the Vista boot loader.  

All GRUB will be able to do is point to a specific partition.  You will have to hand-edit the Vista BCD file, and that can only be done in Vista.  You can download a tool to do that (known as easyBCD) from the NeoSoft forums. Suggest you go there and check their forums regarding the details of what you want to do.

Ok, then is it possible to just use the vista bootloader for everything and disable grub?

---

### Post by argail1980 on 2009-05-28
Most probably not. Windows is known to only recognize their own stuff and ignore non-NTFS/FAT/whatsoever partitions. (At least up to XP, correct me f that has changed)

---

### Post by raymondh on 2009-05-28
[QUOTE=Mark Phelps;7355249]I don't believe that is possible because, for non-Linux OSs, all GRUB does is hand off loading to another loader. 

If what you want is to only have one menu (which is what I think you're asking), that is a LOT of work because of the new structure of the Vista boot loader.  
/QUOTE]

I agree ...

in my case, I have darwin and grub talking to one another depending on which OS I choose (OSX, XP or Ubuntu)

---

### Post by Mark Phelps on 2009-05-28
> **Posessor said:**
> Ok, then is it possible to just use the vista bootloader for everything and disable grub?

Yes, it is.  Once again, use the EasyBCD app from NeoSoft to edit the Vista boot menu to add an entry for Ubuntu.  Check their forums for details.  They have how-tos and guides for doing this.

---

