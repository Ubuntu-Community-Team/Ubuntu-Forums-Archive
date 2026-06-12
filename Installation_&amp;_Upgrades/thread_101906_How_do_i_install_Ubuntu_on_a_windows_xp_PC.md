---
title: "How do i install Ubuntu on a windows xp PC?"
date: 2005-12-10
forum: Installation &amp; Upgrades
---

### Post by Atrio05 on 2005-12-10
Hey i feel really dumb asking this but how do i go about installing Ubuntu along with windows xp? i already had another distro installed on it before and that worked out ok. i was wondering if i could just install ubuntu on the ext2 partition that already exists from the old distro? because i tryed to do that already and i could not figure out what was going on. some one please help!!

---

### Post by kairu0 on 2005-12-10
You could very well install from the ext2 partition, but I recommend that you use reiserfs.

Boot off of the Ubuntu CD, choose the custom partition option, delete your ext2 partition and create a reiserfs partition in its place. Ubuntu will install the GRUB bootloader in place of Windows XP's, but Ubuntu will also add Windows XP to the bootloader menu.

---

### Post by Atrio05 on 2005-12-10
is that all i have to do? theres no other options i need to mess with? i really need a newb walkthrough cause i have no idea how to set this puppy up. the last distro was as simple as hell to install a few clicks and i was done. thanx for the help!!

---

### Post by ardz on 2005-12-10
good day... i had tried installing the ubuntu 5.04 before in my other pc with winxp pack2, and it went well. Now am installing it in my other pc also with winxp but it did'nt went well. it has a message " your processor is not capable in 32 bit distribution" something like that... your problem might be different but maybe you know how to solve mine. I am new to this linux system. thanks

---

### Post by kairu0 on 2005-12-10
Here are two relevant HOWTOs that you should take a look at about installing Ubuntu on a system that already has Windows installed:

[http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/](http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/)
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

The second is better in terms of being an easy read and having lots of pictures.

And your situation will be a little different at the partitioning stage because you already have an ext2 partition that you can wipe and use. So, when you get to the partitioning part, do a custom partition job, delete ext2 and create a reiserfs where it was.

---

