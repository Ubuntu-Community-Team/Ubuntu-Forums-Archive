---
title: "Dual booting unbuntu with Mepis"
date: 2005-12-31
forum: Installation &amp; Upgrades
---

### Post by jmc012 on 2005-12-31
I setup unbuntu to dual boot with Mepis and my question has to do with the menu.lst file for grub.
I let Mepis overwrite grub on the mbr. I was able to get it working by changing the unbuntu entry to look like the mepis entry. Like this:

title MEPIS at hdb1, kernel 2.4.29
kernel (hd1,0)/boot/vmlinuz-2.4.29 root=/dev/hdb1 nomce quiet splash=verbose vga=791 hdc=ide-scsi 
initrd (hd1,0)/boot/initrd.splash 

title Ubuntu, kernel 2.6.12-10-386
kernel (hd0,0)/boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro quiet splash
initrd (hd0,0)/boot/initrd.img-2.6.12-10-386

The old unbuntu entry I put in mepis menu.lst that didn't work looked like this :

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

Is this just because the mepis grub is a different version than unbuntu ? I want to install more distro's and I want to make sure I understand whats going on. By the way, I can't believe I just discovered how great Linux is a few weeks ago, I didn't realize how much I hated Windows.
Thanks
JC

---

