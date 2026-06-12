---
title: "GRUB - Triple boot &gt; going to double"
date: 2009-08-20
forum: Installation &amp; Upgrades
---

### Post by ^_Pepe_^ on 2009-08-20
Hi everyone.

I have 3 partitions on my HDD. 

1. NTFS with XP (boot)
2. Ext4 with Ubuntu 9.04
3. Ext4 with Jolicloud 

I've installed them in that order, so now, I can get a GRUB menu placed into /boot/grub/ directory of 3rd partition. 

I want to get rid of Jolicloud, and I'm thinking on doing following:

1. Start with Ubuntu
2. Gparted > Delete partition 3
3. Start with LiveCD and reinstall GRUB with one of those HowTo's that I have found here.

Please advice. Is that right?

Thanks, 
^_Pepe_^

---

### Post by Mark Phelps on 2009-08-20
Yes, that's right.  Just make sure that the partition for JoliCloud is not mounted when you try to remove it in GParted.

---

### Post by ^_Pepe_^ on 2009-08-21
Smooooth!

It worked perfectly!

Thanks!

---

