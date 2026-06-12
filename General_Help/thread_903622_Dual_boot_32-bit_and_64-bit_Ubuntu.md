---
title: "Dual boot 32-bit and 64-bit Ubuntu"
date: 2008-08-28
forum: General Help
---

### Post by driordan1 on 2008-08-28
Hello all,

I'm trying to set up a system which can boot 32-bit or 64-bit Ubuntu (as well as a Vista partition). I have all the Operating Systems installed but I'm unable to boot the 64-bit Ubuntu.

My grub menu.lst is contained in the 32-bit Ubuntu and has an entry for loading the 64-bit partition using both the initrd and chainloader methods.

When loaded via initrd I get a message 'Kernel Alive' at the start of the boot process and then the booting doesn't get past Ubuntu splash screen. I'd guess that grub is loading my 32-bit kernel and then trying to load the 64-bit OS on top of that which is obviously going to fail.

When I try the chainloading method I get the 'Error 12: Invalid device required'.

I would imagine that I need to tweak my grub to load the 64-bit kernel or tweak my 64-bit installation to make is usable with the chainloader.

Anybody have any suggestions to get this set up working?

Thanks,
Donal

My menu.lst options:

title		Windows Vista (32-bit)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title		Ubuntu 8.04.1 (32-bit)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=6432fb0a-3d7d-4f4d-8ad4-760eaf5dbb44 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1 (64-bit)
root		(hd0,7)
makeactive
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=c22f0755-6e07-4eec-9b6f-d37529c9991a  ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1 (64-bit) chainloader
rootnoverify	(hd0,7)
makeactive
chainloader	+1

---

