---
title: "Grub Loader issues"
date: 2005-05-27
forum: Hardware &amp; Laptops
---

### Post by sidarian on 2005-05-27
I installed Ubuntu onto the Primary Slave, a second Hard Drive. Installation was fine, but the drivers for my vid card and NIC didn't work. So I tried to reformat and repartition my Hard Drive. After rebooting the computer, I was greeted with a Grub Loader Error 17. If I disconnect the Hard Drive, I get grub loader error 21. How can I delete the grub loader without formatting the main harddrive?

---

### Post by spd106 on 2005-05-27
Hi, by changing the partition structure, grub now can't find the partition it's looking for.

Grub stage 1 lives in the master boot record of the primary hard drive and there are lot's of ways to edit it without affecting the rest of the drive. 

If you have a live cd you can edit the /boot/grub/menu.lst file to point to the correct partition.

If you know which partition you want to boot from you can use the command line in grub, look at the grub website [http://www.gnu.org/software/grub](http://www.gnu.org/software/grub) for information. Then edit as above.

It might also be possible to overwrite grub with the installation cd, you don't need to install the whole thing again just skip to the grub installation.

Hope this helps

---

