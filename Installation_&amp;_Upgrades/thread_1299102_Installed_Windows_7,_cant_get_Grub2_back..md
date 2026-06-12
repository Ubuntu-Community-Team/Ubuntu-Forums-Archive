---
title: "Installed Windows 7, cant get Grub2 back."
date: 2009-10-23
forum: Installation &amp; Upgrades
---

### Post by tjeremiah on 2009-10-23
And yes I searched before I post. Almost every solution tells me to boot up LIVE CD, sudo grub, hd 0,0, etc and that doesnt work. While in LIVE CD, it doesnt find directory or I get an error. I really dont know what to do.

---

### Post by drs305 on 2009-10-23
Did you try the chroot method from the LiveCD? And of course you cannot use any of the "find /boot/grub/stage1" posts, which apply only to Grub and not to GRUB 2.

If you didn't try instructions specific to G2, try using the instructions in section "Reinstalling Grub 2 from the LiveCD" in [Grub 2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275").

If you already did use this method, how did it fail?

---

### Post by tjeremiah on 2009-10-23
> **drs305 said:**
> Did you try the chroot method from the LiveCD? And of course you cannot use any of the "find /boot/grub/stage1" posts, which apply only to Grub and not to GRUB 2.

If you didn't try instructions specific to G2, try using the instructions in section "Reinstalling Grub 2 from the LiveCD" in [Grub 2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275").

If you already did use this method, how did it fail?

Silly me for assuming what I did :( Thanks, what you suggested works.

---

