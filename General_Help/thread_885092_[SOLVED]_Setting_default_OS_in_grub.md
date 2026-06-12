---
title: "[SOLVED] Setting default OS in grub"
date: 2008-08-09
forum: General Help
---

### Post by peterjakey on 2008-08-09
Hi, Could someone please tell how to set the default OS in GRUB boot loader? I have set up a dual boot with XP and Kubuntu and would like to set XP as the default.

---

### Post by Victormd on 2008-08-09
open a terminal and type
```
sudo kate /boot/grub/menu.lst
```
This will allow you to edit your boot list. Scroll to the line that reads
> # You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0
and change the "0" to match your windows boot (if windows is the 3rd line, then set this number to 2)

Another option is to enable the savedefault option. This will make it so the boot menu remembers the last OS loaded and always loads the last OS (i.e., if you boot into kubuntu, upon reboot, it will load kubuntu, if you boot into windows, upon reboot it will load windows until the next time you choose to load kubuntu...)
To do this, instead of a number, write "saved" so it will look like this
> default saved
Then, scroll to the block that reads (I use ubuntu so there may be differences with kubuntu, but you get the gist...):
> title		Ubuntu 8.04.1, kernel 2.6.24-20-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-20-generic root=UUID=32a8891a-e732-43d3-9334-418c63daaf0a ro quiet splash
initrd		/boot/initrd.img-2.6.24-20-generic
quiet
and add "savedefault" to the end so it looks like this:
> title		Ubuntu 8.04.1, kernel 2.6.24-20-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-20-generic root=UUID=32a8891a-e732-43d3-9334-418c63daaf0a ro quiet splash
initrd		/boot/initrd.img-2.6.24-20-generic
quiet
savedefault

Furthermore, scroll down to:
> ### END DEBIAN AUTOMAGIC KERNELS LIST
and make sure you have "savedefault" after your windows block as well (it should be there by default).

---

### Post by peterjakey on 2008-08-09
Thankyou! =)

---

