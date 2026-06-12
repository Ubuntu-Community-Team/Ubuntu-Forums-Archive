---
title: "Grub boot from Partition, not MBR"
date: 2009-09-13
forum: Installation &amp; Upgrades
---

### Post by creiss on 2009-09-13
Hey all!  I am dual booting on my notebook (Vista and Ubuntu). The former is for play, the later for work. Now, being paranoid I encrypted the linux root part with luks and the windows part with truecrypt. Now, truecrypt wants/ must sit on the MBR, shoving Grub back to its /boot partition. A grub-install /dev/sda2 worked wonders.  Now I get the TrueCrypt boot screen on power on, and when I hit ESC I get grub.   My question: How can I prevent Ubuntu from doing a grub-install which would overwrite my MBR? Or even better: Is there a config file in which I can specify where to write Grub? /dev/sda2 instead of /dev/sda and I am all good :)  Thanks! -Chris

---

