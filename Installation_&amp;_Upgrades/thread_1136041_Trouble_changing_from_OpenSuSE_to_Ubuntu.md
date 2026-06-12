---
title: "Trouble changing from OpenSuSE to Ubuntu"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by evil-noxx on 2009-04-24
hi,

I'm having trouble getting my Ubuntu 9.04 to work. The problem is that after i install it and reboot my PC grub says something like "Loading, please wait... error 15" and then just hangs there.

I really don't know if it matters but i installed ubuntu on 2 partitions (one / and the other /home), both reiserfs.
Once i tried installing MacOS and i couldn't boot because of something called jmicron that my motherboard has. Don't know  if it's relevant or not.

I've tried reinstalling grub using 2 methods: grub-install /dev/sdc (gives some error about the BIOS) and grub -> root (hd2,4) -> setup (hd0) which seems to install just fine but gives the same error.

I tryed both those methods to install grub on 2 of my 3 hard drives and used install-mbr to clean their MBRs.

Does anyone have any ideias??

---

### Post by zvacet on 2009-04-24
[Here]("http://users.bigpond.net.au/hermanzone/p15.htm#15") is explanation what error 15. means and how to fix it.

---

### Post by evil-noxx on 2009-04-26
thank you for the help. Turns out it was a corrupt stage1.5 or something that couldn't be fixed with a simple install. I had to remove /boot/grub/* in order for the new installation to work.

---

