---
title: "Grub installation problem"
date: 2008-10-08
forum: General Help
---

### Post by ichundu on 2008-10-08
hi,
i have tried twice installing ubuntu on a HP Pavilion Laptop, but after doing 96% of the installation it fails to install grub and says: "this is a fatal error".
this laptop has vista 64 bit on it. i have also failed to install windows xp (wanted to remove vista), but it didn't detect the HDD, but i think it was probably because i had to install sata drivers at the F6 prompt of the xp setup.

as you can see i'm trying to make a dual boot of vista and ubuntu. can anyone help with this grub issue?

thanks!

---

### Post by spiderbatdad on 2008-10-08
I believe a common problem with grub on sata is grub improperly maps to hdb,1. Try google grub on sata...something like this:[http://ubuntuforums.org/showthread.php?t=75385](http://ubuntuforums.org/showthread.php?t=75385)

[https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/32357](https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/32357)

editing from the grub menu should get you booted...then fix the device map in /boot/grub/menu.lst

---

### Post by Kevbert on 2008-10-08
You need to completely format the hard disk.  It Vista was supplied with a repair partition, it means you'll completely loose Vista.  You've suggested that you wanted to install XP instead. You can probably do this from the XP install CD.

---

### Post by ichundu on 2008-10-08
> **spiderbatdad said:**
> I believe a common problem with grub on sata is grub improperly maps to hdb,1. Try google grub on sata...something like this:[http://ubuntuforums.org/showthread.php?t=75385](http://ubuntuforums.org/showthread.php?t=75385)

[https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/32357](https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/32357)

editing from the grub menu should get you booted...then fix the device map in /boot/grub/menu.lst

thanks for the links, although my problem seems to be a bit different. grub fails to install, which breaks the ubuntu installation before it completes.

> **Kevbert said:**
> You need to completely format the hard disk.  It Vista was supplied with a repair partition, it means you'll completely loose Vista.  You've suggested that you wanted to install XP instead. You can probably do this from the XP install CD.

that's exactly what i did: booted from the xp install cd, but it didn't detect the HDD, so i couldn't continue with the setup and couldn't remove vista and replace it with xp. or did you mean i can install sata drivers from the xp install cd?

---

### Post by spiderbatdad on 2008-10-08
sorry for misunderstanding. Sometimes the sata can be configured in ide mode with the parameter all_generic_ide added to the kernel line in /boot/grub/menu.lst....after the installation. However, to boot for first time installation:
Use the F6 more options from the startup screen and delete "quiet splash--" from the end of the boot line. replace with "all_generic_ide"

If that fails try again with "irqpoll" to replace "quiet splash."

---

### Post by ichundu on 2008-10-09
> **spiderbatdad said:**
> sorry for misunderstanding. Sometimes the sata can be configured in ide mode with the parameter all_generic_ide added to the kernel line in /boot/grub/menu.lst....after the installation. However, to boot for first time installation:
Use the F6 more options from the startup screen and delete "quiet splash--" from the end of the boot line. replace with "all_generic_ide"

If that fails try again with "irqpoll" to replace "quiet splash."

spiderbatdad, thank you so much man. i replaced "quiet splash" with "all_generic_ide" and it worked greatly, now i have ubuntu installed. :guitar:

---

