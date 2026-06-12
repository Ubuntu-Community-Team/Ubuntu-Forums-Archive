---
title: "No option to boot Ubuntu"
date: 2008-10-03
forum: General Help
---

### Post by bgdre12 on 2008-10-03
Okay, a few days ago i installed Ubuntu via wubi.  I just recently purchased a new 320gb hd.  Made a complete carbon copy of my disk.  My Leopard partition works find, and windows still boots, however i don't get the option to choose Ubuntu or Vista anymore while booting windows.  Anyone know how to re enable this?

---

### Post by bgdre12 on 2008-10-03
Ok, after some research, i downloaded EasyBCD and there is no ubuntu boot option in the boot manager.  Can i just add it from EasyBCD in the menu?

---

### Post by utsuprainfra on 2008-10-03
Grub would maybe make this easier.

---

### Post by jf812 on 2008-10-04
Grub will be a much easier option.

---

### Post by ago on 2008-10-06
Well probably menu.lst, kernel and initrd are on an ntfs partition and grub cannot access that. Also if people use wubi probably they do not have a compatible partition to install grub onto. Grub2 works, but is not officially supported yet. 

But yes you can use EasyBCD to load wubildr.mbr

---

