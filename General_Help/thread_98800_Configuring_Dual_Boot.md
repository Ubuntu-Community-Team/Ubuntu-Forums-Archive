---
title: "Configuring Dual Boot"
date: 2005-12-04
forum: General Help
---

### Post by ubuntuubuntu on 2005-12-04
How can I configure Grub so that the option "Microsoft Windows" appears on top?

---

### Post by UbuntuJohan on 2005-12-04
The boot order for GRUB is determined by the file.
/boot/grub/menu.lst

In the ubuntuguide.org its described how to change it.
[http://www.ubuntuguide.org/#changedefaultosgrub](http://www.ubuntuguide.org/#changedefaultosgrub)

Good luck

---

### Post by LittleReinhart on 2005-12-04
Hey,

I don't have a dual boot with M$ Windows, but if I want to change my boot-order, I edit the /boot/grub/menu.lst file.

Scroll down to 
```
## ## End Default Options ##
```
Below that line you find a list of your boot-stuff.

Put your windows startup at the top of this list.

Here is mine:
```
## ## End Default Options ##

title           Ubuntu5.10 hd 1,1 (sda2), kernel 2.6.12-9-amd64-generic Default
root            (hd1,1)
kernel          /boot/vmlinuz root=/dev/sda2 ro quiet splash
initrd          /boot/initrd.img
savedefault
boot

title           Ubuntu 5.04 hd 2,1 (sdb2)
root            (hd2,1)
kernel          /boot/vmlinuz-2.6.10-5-amd64-generic root=/dev/sdb2 ro console=tty0 quiet splash
initrd          /boot/initrd.img-2.6.10-5-amd64-generic
savedefault
boot

title           Ubuntu, kernel memtest86+
root            (hd2,1)
kernel          /boot/memtest86+.bin
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
```
So, if I would like Ubuntu 5.04 to be my default boot, I just have to switch the first and second item in this list.

Here is some info about the grub:
[http://ubuntuguide.org/#addwindowsentrygrubmenu](http://ubuntuguide.org/#addwindowsentrygrubmenu)

Greetings,
Reinhart

P.S. Make a backup from the /boot/grub/menu.lst befor you begin ;-)

---

