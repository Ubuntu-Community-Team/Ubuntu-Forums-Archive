---
title: "im seeing two ubuntu 8.04 loader and two safe mood when i have only one \"
date: 2009-01-25
forum: Installation &amp; Upgrades
---

### Post by sookun on 2009-01-25
hi there
i recently updated the Feisty to Hardy well cos i recently reinstalled Feisty and the only upgrade it showed me was Hardy
so now Grub is showing me vmlinux generic 16 and its safe mode
and vmlinuz generic 14 and its safe mode..either boots in the same desktop except in the first one my wireless dont work

any solution?
its running on a vista and linux partions, ACER 5573

---

### Post by x33a on 2009-01-25
grub shows the previous kernel you used along with the updated one. you can disable one by either uninstalling the previous kernel or editing grub.

---

### Post by 73ckn797 on 2009-01-25
> **x33a said:**
> grub shows the previous kernel you used along with the updated one. you can disable one by either uninstalling the previous kernel or editing grub.


Go to Applications/Accessories/Terminal.

Enter the following in terminal:
```
gksudo gedit /boot/grub/menu.lst
```

At the bottom of the file you will see the grub entries. Either insert "#" before the older kernel listings or delete the lines completely. Save then exit and reboot to see changes on boot-up.

---

### Post by sumit.kalra999 on 2009-01-25
enter into root by using "su" or from login screen
enter following code at terminal
```

vi /boot/grub/menu.lst

```

remove the lines which you don't want to show in bootup screen or just comment them using #

you can also change the traditional line by replacing them with some funny line or with your name or anything you want

---

### Post by sookun on 2009-01-25
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=6b1817db-31a4-40cb-afc9-9b86d67befb6 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=6b1817db-31a4-40cb-afc9-9b86d67befb6 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=6b1817db-31a4-40cb-afc9-9b86d67befb6 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=6b1817db-31a4-40cb-afc9-9b86d67befb6 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet


thats what it says...well im greatful to u all im adding the # and restarting but which one is the new and which one is the last 16 or 14-generic??
PS: the 16-generic the wireless dnt work!

---

### Post by ugm6hr on 2009-01-25
2.6.22-14 is a Gutsy kernel
2.6.24-16 is a Hardy kernel

You should leave both for now - and get wifi working in the newer Hardy kernel.

Then # the Gutsy kernel.

---

### Post by sookun on 2009-07-21
thkss mate really helped me out..experienced the same prob when i upgraded 8.10 to Jacalope..take care

---

