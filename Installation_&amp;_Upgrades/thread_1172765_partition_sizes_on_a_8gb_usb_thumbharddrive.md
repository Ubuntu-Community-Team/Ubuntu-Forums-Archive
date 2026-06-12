---
title: "partition sizes on a 8gb usb thumbharddrive?"
date: 2009-05-28
forum: Installation &amp; Upgrades
---

### Post by linux000019 on 2009-05-28
im installing a ubuntu remix onto a 8gb hard drive; not flash, and was wondering how to make the 3 partition sizes? 3 partionions i mean swap, home, root. maybe i can combine root and home together since i dont have much space.

---

### Post by linux000019 on 2009-05-28
im in the setup screen "prepare disk space" and clicked manual so maybe you can just tell me where to go next.

---

### Post by orange-wedge on 2009-05-28
Yes the minimum number of partitions that you need are 2:
swap and /

I think Ubuntu requires that you have about 2.5 GB for / 

You can play around with that value to see the minimum during the installation.

I generally like to create my swap partitions twice the size of my available RAM.  This is probably over kill, but you definitely want to create the swap partition the size of your available RAM.

Then I make a partition of about 100 MB for /boot

You don't need a partition for /home but I like to create one even if I'm cramped for space because you can always use that partition to backup files if somehow your OS goes belly up and you have to do a fresh install on your / partition.  Trust me... this has come in handy in the past.

---

### Post by linux000019 on 2009-05-28
alright im doing the install exactly like what yo said.

also, if i make the / size 2500 is that going to be enough when i want to upgrade the system and add new programs?

---

### Post by linux000019 on 2009-05-28
****, it installed, except when i did choose ubuntu in grub, i see a "error 17: cannot mount selected partition press any key to continue..."

---

### Post by orange-wedge on 2009-05-29
seems that somehow your grub menu list is wrong.  you may need to edit your /boot/grub/menu.lst file to point to the right partition.

---

