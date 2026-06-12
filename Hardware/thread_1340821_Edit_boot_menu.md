---
title: "Edit boot menu"
date: 2009-11-29
forum: Hardware
---

### Post by rmadams1 on 2009-11-29
Hi there, I've got a quick question that I've looked for an answer on and am apparently too blind to find. I've made a change to my boot menu to solve an issue I was having with an initramfs error. The change has worked, but I want to make it permanent and I'm not able to find the boot/grub/menu.lst file. I find the boot/grub/grub.cfg file which is kindly marked *do not edit*, and the referring files don't appear to have the actual boot menu. 
 
I'm running a dual boot with Vista and 9.10. Thank you for your patience and assistance with a ubuntu noobie.
 
P.S. Original issue was related to the hdd, hence the post on this forum. If the wrong place, I apologize. Tell me and I'll repost elsehwere.

---

### Post by SteveDee on 2009-11-29
> ...I'm not able to find the boot/grub/menu.lst file....

The menu.lst file only applies to the old version of Grub used in 'buntu versions before 9.10.

Now they are using Grub 2, so it looks like you have to edit the /etc/default/grub file, save it, then open a terminal and type: sudo update-grub

Hope this helps.

---

### Post by coffeecat on 2009-11-29
A couple of useful links for you for grub 2:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Grub 2 configuration is quite different from grub 1. Those two links have helped me a lot.

---

### Post by rmadams1 on 2009-11-29
Thanks to both for the info and the links. Issue solved!

---

