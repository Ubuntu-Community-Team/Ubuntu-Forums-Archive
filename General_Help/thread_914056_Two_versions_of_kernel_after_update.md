---
title: "Two versions of kernel after update"
date: 2008-09-08
forum: General Help
---

### Post by dennisejames on 2008-09-08
I have just installed Ubuntu 8.04 and love it. After it did an auto update I now have two kernel versions in the boot menu. Is this normal and can I remove the older version so that it doesn't show up in the grub menu? I also had trouble with the dual boot for Win XP but I figured it out by reading the forums.

---

### Post by Oldsoldier2003 on 2008-09-08
you can remove the older kernel version, but it is prudent to keep at least one older kernel version in case you run into problems.

To remove unwanted kernels, open synaptic and search for linux-image. find the kernel image you want removed and mark it "for complete removal" this will remove the kernel and also automatically remove the grub menu option for the kernel as well.

---

### Post by anaconda on 2008-09-08
that is normal, and if everything works well with the new kernel you can safely remove the old kernel with eg. synaptic.

or you could just comment the extra lines from grub (boot loader) edit with this command:
sudo gedit /boot/grub/menu.lst

---

