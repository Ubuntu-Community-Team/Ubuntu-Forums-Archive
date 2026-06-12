---
title: "Installing"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by JohnnyWhite2007 on 2009-10-29
Hello Everyone. 

I am about to install Ubuntu 9.10 on a 1TB Hard Drive that is partitioned into two 500GB partitions. After I install Ubuntu 9.10 on one partition I will be installing Windows 7 on the other partition. My question is if I install Ubuntu first and then install Windows will I still be able to use Grub or will Windows install its own boot loader, which I hate? And will I still be able to get into Ubuntu?

---

### Post by Rocket2DMn on 2009-10-29
It is usually best to install Windows first so that when you install Ubuntu, Grub will take over the MBR and you won't have to go back and reinstall it after Windows does its thing.  Also, just FYI, fresh installing Karmic will give you the new Grub2, which is a bit different from the old Grub you're used to.  You shouldn't have any problems with it, I'm just giving you a heads up in case you get confused.

---

### Post by sickly on 2009-10-29
Yes install windows first then boot from the Ubuntu cd and the Ubuntu installer will let you resize the windows partition to whatever size you want, installing them side by side so you can choose wich one to boot on startup. That would be the easiest way.

---

### Post by sickly on 2009-10-29
Sorry forgot to mention that when you install windows, you can erase both partitions and make it so its just one partition, then you can resize in Ubuntu installer.

---

