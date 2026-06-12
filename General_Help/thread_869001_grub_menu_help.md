---
title: "grub menu help"
date: 2008-07-24
forum: General Help
---

### Post by chris.c on 2008-07-24
I have loaded Ubuntu and Linux Mint on seperate occasions dual booted with XP.  I am having troubles with GRUB.  Linux 'sees' my SATA drive as HD0 and my boot drive containing operating systems as HD1.  My system boots from HD1 and the sata drive is storage.  

The problem with this is, when my pc boots, the system sees the sata drive last, and my ide drives first, meaning the boot drive is HD0.  When grub loads and i try to start my an OS (either one) it gives an error saying partition invalid or something like that.  How do I remap GRUB so it will load correctly?

---

### Post by Potatoj316 on 2008-07-24
Did you add one of the hard drives after installing?  Did grub ever work for you?  If grub used to work what did you do to make it stop?

---

### Post by chris.c on 2008-07-24
Grub has never worked for me.  All the drives were in and running at the time I install ubuntu.

My motherboard sees IDE drives first and SATA drives last, but Ubuntu is seeing the opposite, and I think that is what is causing the conflicts.

---

### Post by Potatoj316 on 2008-07-24
Could you paste the bottom portion of your /boot/grub/menu.lst here (where it starts listing the possible OSs to boot for the grub menu)

---

### Post by sandysandy on 2008-07-24
have a look here for dual booting

[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

and here for how to restore Grub from a live Ubuntu cd.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

regards

---

### Post by chris.c on 2008-07-24
title		Linux Mint, kernel 2.6.24-16-generic
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sdb3 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic

title		Linux Mint, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sdb3 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Linux Mint, kernel memtest86+
root		(hd1,2)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

### Post by Potatoj316 on 2008-07-24
If it is IDing the drives wrong then this should fix it, if it dosent than I have no idea.  I really dont think this is the problem though.  What do the partitions look like on the HD that you want to boot from?  How do you boot anyway, or are you retrieving this with a live CD?

title Linux Mint, kernel 2.6.24-16-generic
root (hd**0**,2)
kernel /boot/vmlinuz-2.6.24-16-generic root=/dev/sdb3 ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic

title Linux Mint, kernel 2.6.24-16-generic (recovery mode)
root (hd**0**,2)
kernel /boot/vmlinuz-2.6.24-16-generic root=/dev/sdb3 ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Linux Mint, kernel memtest86+
root (hd**0**,2)
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Microsoft Windows XP Professional
root (hd**0**,0)
savedefault
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

---

### Post by jimmywu013 on 2008-07-24
EDIT: never mind - I reread your first post and it seems you currently have Linux Mint dual booting with XP

where are the grub entries for ubuntu?

---

### Post by jimmywu013 on 2008-07-24
it might help if you told us what changes in terms of installing/uninstalling hd's or os's you made since the last time your system was working

your grub entries seem to indicate that linux mint is on the third partition of your second HD, which you say is the sata one, while xp is on the first partition of your first (ide) drive.  Is that the case?

---

