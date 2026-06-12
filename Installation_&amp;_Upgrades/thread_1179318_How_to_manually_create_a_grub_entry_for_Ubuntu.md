---
title: "How to manually create a grub entry for Ubuntu?"
date: 2009-06-05
forum: Installation &amp; Upgrades
---

### Post by bunty on 2009-06-05
Hi,

I just went through the installation process and installed ubuntu onto a spare partition. I did not want it to dump on my carefully setup multiboot grub.conf so I selected "don't install boot loader" option and let it put the kernel stuff in it's own /boot directory rather than giving it my separate /boot partition to play with.

This seems fine but I not have to reconstruct a grub entry with no clear information of what ubuntu requires to start.

I have a fair bit of linux experience but I'm not too familiar with ubuntu's way of setting up so I just looked at the kernel and initrd files and set up a simple grub.conf entry.

title bunty
root (hd0,7)
kernel /boot/vmlinuz-2.6.28-11-generic  root=/dev/hda8  splash=silent vga=788
initrd /boot/initrd.img-2.6.28-11-generic


When I boot this, the kernel loads OK and initrd starts but then the screen goes blank.

I found a howto that seemed to suggest I was doing the right sort of thing but clearly not .

This is a common problem with several distros. If you need to a manual set up they just leave in the dark. For example I dont even know if it's expecting to see this IDE drive as a hda or sda device, whether it relies on UUID or whatever.

Using sda8 it just flashed up a little Ubuntu logo before going blank. with hda8 popped a reboot !

Where is this documented?

TIA.

---

### Post by merlinus on 2009-06-05
FWIW, here is mine:

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        8268d051-ae3a-4d8b-9c21-ddf82d782734
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=8268d051-ae3a-4d8b-9c21-ddf82d782734 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

---

### Post by jbruced on 2009-06-05
Supergrub website has lots of detailed, current documentation. 

GL
Bruce

---

