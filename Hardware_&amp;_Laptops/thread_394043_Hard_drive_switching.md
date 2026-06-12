---
title: "Hard drive switching"
date: 2007-03-26
forum: Hardware &amp; Laptops
---

### Post by carlosjoan91 on 2007-03-26
Hi, when i installed ubuntu, i was just trying it, so i installed on the secondary master, or on the primary slave, i don't recall, and Win XP was in primary master, the thing is i don't need windows in this computer anymore, and i want that HDD for anothercomputer, so i want to know how to switch the ubuntu hard drive to primary master, and take away the Win XP disk without damaging my ubuntu installation, is this possible? thank you

---

### Post by s0cket on 2007-03-26
It can be done easily.  You'll need to play around with your grub configuration and install grub to the MBR of that hard disk.  I would recommend moving the HDD to the proper configuration, booting to the Ubuntu Live CD and fixing everything from there.  In fact you could look at the gentoo handbook for infromation on how to setup GRUB by hand.  Most of what they say in there will apply to Ubuntu.

---

### Post by carlosjoan91 on 2007-03-26
i'm sorry if i sound too dumb, but i'm too much of a newbie here... i don't know to what  handbook you refer... and from the ubuntu live cd, what exactly would i have to do?, sorry and thanks

---

