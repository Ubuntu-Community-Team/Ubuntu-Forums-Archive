---
title: "Successful Transfer of  data to new hard drive"
date: 2007-08-01
forum: Hardware &amp; Laptops
---

### Post by adasuper on 2007-08-01
I have Ubuntu dual booted with windows XP on my laptop hard drive, right now i am thinking of buying a larger hard drive and moving the entire Ubuntu installation to the new drive and using the new drive in another laptop. Is it possible to do such a thing without loosing all my settings and documents? If yes, can someone kindly tell me how to go about it?

---

### Post by Malh on 2007-08-01
Maybe using Ghost or something like it to create an image of your HDD then copying the image to an external HDD or some DVDs would work?

---

### Post by ajgreeny on 2007-08-01
Partimage is probably what you need (on the live CD, I think), though bear in mind that you will have problems booting into ubuntu until you have edited various files including the /etc/fstab and /boot/grub/menu.lst and made them point to the new disk and partitions.

---

### Post by pbcartwright on 2007-08-01
I would back up your /home directory to a CD, that way you have almost all settings & files.
/etc has some configuration stuff, but most of your docs and files should be under your /home/LOGIN_NAME folder. If you have another drive or partition you can copy everything from your /home folder. You might look at rsync for that, or just copy everything to a data CD.

---

