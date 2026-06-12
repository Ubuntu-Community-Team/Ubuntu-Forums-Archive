---
title: "Problems moving root partition!"
date: 2005-12-03
forum: General Help
---

### Post by SirKillalot on 2005-12-03
Hi,
I had my root partition on /dev/hda8 and an old windows partition on /dev/hda1.
I use grub to load a dualboot system.
Now, I decided to remove windows and just to use linux, I deleted the partition on /dev/hda1 and copied/pasted /dev/hda8 to /dev/hda1 using GParted.
Then I removed the bootflag on hda8 and enabled it on hda1.
After that, I loaded ubuntu LiveCD and chrooted to /dev/hda1 and made "grub-install hd0" and "grub-install /dev/hda"

But now, I got the problem that I see "Loading grub stage 2" when I boot, but then grub stucks somehow.

Hope anyone can help, thanks.

---

### Post by Xen2oo6 on 2005-12-03
have you edit the /etc/fstab and /boot/grub/menu.lst, too? if not, please make this and reinstall grub.

---

### Post by SirKillalot on 2005-12-03
[QUOTE=Xen2oo6]have you edit the /etc/fstab and /boot/grub/menu.lst, too? if not, please make this and reinstall grub.[/QUOTE]
yep, I did that before, but that shouldn't have anything to do with grub itself :-/

---

