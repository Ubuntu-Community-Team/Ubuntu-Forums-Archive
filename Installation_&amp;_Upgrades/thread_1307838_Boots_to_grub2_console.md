---
title: "Boots to grub2 console"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by smacfarl on 2009-10-31
9.10 is on a secondary partition of the main harddrive.

I have vista on the first partition which I extended from 30gb to 60 gb. I used the Wubi install process to creat an ext4 partition in the 30gb after that, and then created a 4gb swap partition after the ext4 partition. Ubuntu installed onto the ext4 partition.

I rebooted and added an Ubuntu option via easybcd to the windows boot loader. When I select Ubuntu with windows bootloader I now boot into a grub2 console.

ls is not listed as a command when typing help from this console.

Typing ls at the command prompt generates error 32 unrecognized command. 

The wubi identified the ext4 partition as hda5. When I used the advanced option to install grub2 in the wubi it seems to have created a grub.cfg file that I can see when I mount the 40gb ext4 volume from the live CD. When grub launches it seems to be looking for a menu.lst file rather than grub.cfd right before it launches me into the console.

What went wrong? What can I do to fix this?

---

### Post by smacfarl on 2009-11-03
Bump. Still not working.

---

### Post by smacfarl on 2009-11-04
Bump. It's been 4 days any body here have any thoughts?

---

### Post by jkhh07 on 2009-11-04
whats the forum you used to install grub2?

---

### Post by smacfarl on 2009-11-06
Forum? What do you mean forum?

Grub2 is installed by default with 9.10. 9.10 installed it.

---

