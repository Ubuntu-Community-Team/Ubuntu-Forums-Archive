---
title: "[SOLVED] Updating grub for multiple OS."
date: 2008-10-09
forum: General Help
---

### Post by Kevbert on 2008-10-09
I'm running Ubuntu 8.04, 8.10, Kubuntu 8.10 and XP.  If I run 
sudo update-grub
it updates only Ubuntu 8.10, my currently running OS and last OS installed. Is there a way of updating all OS at the same time from the command line ?  If I update the software in 8.04 and the kernel is changed I want to be able to update all grub entries at once.

---

### Post by caljohnsmith on 2008-10-09
> **Kevbert said:**
> I'm running Ubuntu 8.04, 8.10, Kubuntu 8.10 and XP.  If I run 
sudo update-grub
it updates only Ubuntu 8.10, my currently running OS and last OS installed. Is there a way of updating all OS at the same time from the command line ?  If I update the software in 8.04 and the kernel is changed I want to be able to update all grub entries at once.
Yes, the update-grub command will only update the menu.lst of the Linux distro you are currently in. If you don't want to boot into your other Ubuntu versions to update their menu.lst, you can do it like follows from the distro you are in:
```
sudo mount /dev/sdX /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt /bin/bash
update-grub
exit
```
And replace sdX with the partition of the Ubuntu version you want to update; also you can change the mount point above if you like. That's the only way I know of to use "update-grub" to update their menu.lst without booting into them.

---

### Post by Kevbert on 2008-10-09
Thanks for the useful information. I'll use that in future.
Cheers
Kevin.

---

