---
title: "Grub anamoly - too many kernels listed."
date: 2009-02-12
forum: Installation &amp; Upgrades
---

### Post by jervin2 on 2009-02-12
I'm, as many are, new to ubuntu 8.10.  WHen I boot my system, grub gives me the following:

Ubuntu 8.10, Kernel 2.6.27-11-generic
Ubuntu 8.10, Kernel 2.6.27-11-generic (recovery mode)
Ubuntu 8.10, Kernel 2.6.27-7-generic
Ubuntu 8.10, Kernel 2.6.27-7-generic (recovery mode)
Ubuntu 8.10, Kernel 2.6.27-3-rt
Ubuntu 8.10, Kernel 2.6.27-3-rt (recovery mode)
etc....

The question is, how to get rid of the kernel listings beyond the 2.6.27-11-generic ones.  I only have two partitions.

---

### Post by panmoto on 2009-02-12
there are two ways, that I know of.
1. graphical way
- go to synaptic package manager
- install startupmanager,
- with this application you can edit how your grub behave. you can limit the number of kernels in boot menu, click on Advanced tab.
- reboot

or you can try
2. direct editing:
- go to terminal, type sudo nautilus
- as a superuser with nautilus, go to /boot/grub/menu.lst,
- to make thing safe, back up this file first.
- open it with text editor, you should find the list of your kernel there near the end of the file. delete what you don't want to appear. but i suggest you keep at least two version of kernels with their respective recovery mode, in case you want to revert back if something is wrong with newer kernel. It looks like this :

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		number-number....
kernel		/boot/vmlinuz-2.6.27-11-generic root=....
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		number-number....
kernel		/boot/vmlinuz-2.6.27-11-generic root=...6 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title           older kernel bla---bla---

- close nautilus, and reboot.


I think way #1 is much safer and simpler.
 
remember :back up first and be careful.

---

### Post by Anger 2 on 2009-02-12
I use Ubuntu 8 10 also and the first four lines of Grub are similar to yours. I have been given to understand that this is normal. If for some reason the first line fails to boot you have the option to boot from the second generic line. I am new to Linux and at first thought that this was a fault. I understand that using the safe mode equivalent can be complicated.

---

