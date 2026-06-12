---
title: "Grub error 22"
date: 2009-08-12
forum: Installation &amp; Upgrades
---

### Post by Fuith on 2009-08-12
Hi guys, I installed Mint KDE on top of Mint Gnome and I can't boot. Grub error 22 keeps popping up.
Here's the device.map
> (hd0)    /dev/sda
(hd1)    /dev/sdbAnd the menu.lst
title        Linux Mint 7 Gloria, kernel 2.6.28-14-generic
root        (hd1,4)
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=f5e5b0bc-08e3-46b7-be18-53b9e4e25d77 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

title        Linux Mint 7 Gloria, kernel 2.6.28-14-generic (recovery mode)
root        (hd1,4)
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=f5e5b0bc-08e3-46b7-be18-53b9e4e25d77 ro single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Linux Mint 7 Gloria, kernel 2.6.28-13-generic
root        (hd1,4)
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=f5e5b0bc-08e3-46b7-be18-53b9e4e25d77 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Linux Mint 7 Gloria, kernel 2.6.28-13-generic (recovery mode)
root        (hd1,4)
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=f5e5b0bc-08e3-46b7-be18-53b9e4e25d77 ro single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Linux Mint 7 Gloria, kernel 2.6.28-11-generic
root        (hd1,4)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=f5e5b0bc-08e3-46b7-be18-53b9e4e25d77 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Linux Mint 7 Gloria, kernel 2.6.28-11-generic (recovery mode)
root        (hd1,4)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=f5e5b0bc-08e3-46b7-be18-53b9e4e25d77 ro single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Linux Mint 7 Gloria, memtest86+
root        (hd1,4)
kernel        /boot/memtest86+.bin
quiet

title        Linux Mint 7 Gloria KDE, kernel 2.6.28-11-generic
root        (hd1,5)
kernel        /boot/vmlinuz-2.6.28-11-generic root=/dev/sdb6 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Linux Mint 7 Gloria KDE, kernel 2.6.28-11-generic (recovery mode)
root        (hd1,5)
kernel        /boot/vmlinuz-2.6.28-11-generic root=/dev/sdb6 ro single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Linux Mint 7 Gloria KDE, memtest86+
root        (hd1,5)
kernel        /boot/memtest86+.bin
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
#title        Windows Vista (loader)
#rootnoverify    (hd0,0)
#savedefault
#makeactive
#chainloader    +1

title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

Windows boots fine. How do I fix the Linux parts?

---

### Post by zvacet on 2009-08-12
If you installed Mint KDE on top of Mint Gnome entries in menu list should be the same (hd1,4).Read [this.]("http://members.iinet.net.au/~herman546/p15.html#22")

---

### Post by Fuith on 2009-08-12
I'll try that.

---

### Post by Fuith on 2009-08-12
Tried it, set it up with grub, no joy.

---

### Post by stlsaint on 2009-08-12
ok how many times did you install mint gnome...also whats with the xp mbr at bottom?!

---

### Post by stlsaint on 2009-08-12
maybe you should clean up kernels?

---

