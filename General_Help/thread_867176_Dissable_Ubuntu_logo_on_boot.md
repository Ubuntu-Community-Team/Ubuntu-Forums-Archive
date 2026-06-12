---
title: "Dissable Ubuntu logo on boot"
date: 2008-07-22
forum: General Help
---

### Post by Tlingit on 2008-07-22
Does anyone know what I need to know to be able to disable the Ubuntu logo on boot? I would like to see everything it is doing?

I like to watch it load drivers and processes. its cool

---

### Post by Tlingit on 2008-07-22
sudo gedit /boot/grub/menu.lst

that has "splash=silent" to "splash=verbose" 

Save and reboot

---

### Post by BryanFRitt on 2008-07-22
or edit it so that it says nosplash
sudo kate /boot/grub/menu.lst
(or choose your own text editor, like gedit)
change the line that looks like
*/boot/vmlinuz-2.6.24-19-generic root=UUID=5d69eb91-48e6-443c-ba78-3b46f0d9a663 ro quiet splash*
to one that looks like this
*/boot/vmlinuz-2.6.24-19-generic root=UUID=5d69eb91-48e6-443c-ba78-3b46f0d9a663 ro quiet nosplash*
If you just want to view it one time, choose edit at the boot menu
If you want to make it a choice, leave the original and copy that boot option to another section above or below itself

---

