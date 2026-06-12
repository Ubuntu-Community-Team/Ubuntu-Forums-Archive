---
title: "Error 15 file not found by upgrading 8.04 to 8.10"
date: 2009-03-29
forum: Installation &amp; Upgrades
---

### Post by corinnespi on 2009-03-29
Hello,
I know there are some other thread in different forum about this theme,but I don't understand how to change the menu.lst for me.
I hope somebody can help me.
thanks a lot !

I have the error 15 file not found be reboot after upgrading. (normal mode or recovery mode)

from the cd-live ubuntu "sudo fdisk -l" I have that :
Device Boot Start End Blocks Id System
/dev/sda1 1 1020 8193118+ 12 Compaq diagnostics
/dev/sda2 * 1021 6119 40957717+ 7 HPFS/NTFS
/dev/sda3 6120 6152 265072+ 83 Linux
/dev/sda4 6153 19457 106872412+ 5 Extended
/dev/sda5 6153 6336 1477948+ 82 Linux swap / Solaris
/dev/sda6 6337 19457 105394401 83 Linux

In "menu.lst" (without the comment) :
# menu.lst - See: grub(8), info grub, update-grub(8)

default 0
timeout 3

title Ubuntu 8.04.2, kernel 2.6.24-23-generic
root (hd0,2)
kernel /vmlinuz-2.6.24-23-generic root=UUID=4038bffc-47be-46f7-983f-0133c1aa8ab6 ro quiet splash
initrd /initrd.img-2.6.24-23-generic
quiet

title Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root (hd0,2)
kernel /vmlinuz-2.6.24-23-generic root=UUID=4038bffc-47be-46f7-983f-0133c1aa8ab6 ro single
initrd /initrd.img-2.6.24-23-generic

title Ubuntu 8.04.2, memtest86+
root (hd0,2)
kernel /memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows NT/2000/XP
root (hd0,0)
savedefault
makeactive
chainloader +1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Windows Vista/Longhorn (loader)
root (hd0,1)
savedefault
makeactive
chainloader +1

ls /boot :
abi-2.6.27-7-generic System.map-2.6.27-7-generic
config-2.6.27-7-generic vmcoreinfo-2.6.27-7-generic
memtest86+.bin

  ls /boot/grub
ls: cannot access /boot/grub: No such file or directory

Thanks for your help !

---

### Post by Pumalite on 2009-03-29
[http://users.bigpond.net.au/hermanzone/p15.htm#15](http://users.bigpond.net.au/hermanzone/p15.htm#15)

---

### Post by ronparent on 2009-03-29
Your boot menu directs grub to find 8.04. If you change menu.lst from the live cd to find the operative files for 8.10, that should fix your problem.

---

### Post by corinnespi on 2009-03-29
Yes, of course, but it fact, it seems, some files are missing, like linuz and initrp ?
So I'm not sure it is enough !

---

### Post by ronparent on 2009-03-29
The files you are looking for should be /boot/vmlinuz-2.6.27-7-generic and /boot/initrd.img-2.6.27-7-generic on first install of 8.10.

---

### Post by corinnespi on 2009-03-29
Yes, but I don't know if it is enough to copy then on the /boot from an other user or from the cd-live ?

---

### Post by ronparent on 2009-03-29
If the files are missing it may not be enough to copy them from somewhere else. The install may be incomplete. At this point it may not hurt to try.

---

